# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #1 выполнил(а):
- Сапкалова Кристина Сергеевна
- РИ210934
Отметка о выполнении заданий (заполняется студентом):

| Задание | Выполнение | Баллы |
| ------ | ------ | ------ |
| Задание 1 | * | 60 |
| Задание 2 | * | 20 |
| Задание 3 | * | 20 |

знак "*" - задание выполнено; знак "#" - задание не выполнено;

Работу проверили:
- к.т.н., доцент Денисов Д.В.
- к.э.н., доцент Панов М.А.
- ст. преп., Фадеев В.О.

[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

## Задание 1
### Реализовать систему машинного обучения в Python - Google-Sheets – Unity.
- В проект Unity добавим два пакета:
![image](https://user-images.githubusercontent.com/104152574/197794915-9d99d8de-9498-42a9-b697-0229d04deeb9.png)
- Добавила mlagents и torch:
![image](https://user-images.githubusercontent.com/104152574/197803728-0ae4f695-6b6e-431d-9527-75e46de9b9df.png)
- Создала куб, плоскость, шар:
![image](https://user-images.githubusercontent.com/104152574/197807995-35f757c5-ac1a-4b05-a828-2557f1c642b4.png)
- В скрипт-файл RollerAgent добавила следующий код:
~~~using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
    Rigidbody rBody;
    void Start()
    {
        rBody = GetComponent<Rigidbody>();
    }
    public Transform Target;
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
        {
            this.rBody.angularVelocity = Vector3.zero;
            this.rBody.velocity = Vector3.zero;
            this.transform.localPosition = new Vector3(0, 0.5f, 0);
        }
        Target.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
    }
    public override void CollectObservations(VectorSensor sensor)
    {
        sensor.AddObservation(Target.localPosition);
        sensor.AddObservation(this.transform.localPosition);
        sensor.AddObservation(rBody.velocity.x);
        sensor.AddObservation(rBody.velocity.z);
    }
    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {
        Vector3 controlSignal = Vector3.zero;
        controlSignal.x = actionBuffers.ContinuousActions[0];
        controlSignal.z = actionBuffers.ContinuousActions[1];
        rBody.AddForce(controlSignal * forceMultiplier);
        float distanceToTarget = Vector3.Distance(this.transform.localPosition, Target.localPosition);
        if(distanceToTarget < 1.42f)
        {
            SetReward(1.0f);
            EndEpisode();
        }
        else if (this.transform.localPosition.y < 0)
        {
            EndEpisode();
        }
    }
}
~~~
- Запустила работу ml-агента:
![image](https://user-images.githubusercontent.com/104152574/197826352-2d2a9cf7-aa59-4c14-bcfe-d2675801c5dc.png)
- Сделала несколько копий модели и обучила их:
![image](https://user-images.githubusercontent.com/104152574/197832539-26c4562a-9120-41f6-bba6-921f51186163.png)
- Работа модели:
https://user-images.githubusercontent.com/104152574/197833503-aa7b15a8-de0e-486d-abae-2d63ab107423.mp4

                                            
## Задание 2
### Подробно описать каждую строку файла конфигурации нейронной сети. Самостоятельно найти информацию о компонентах Decision Requester, Behavior Parameters, добавленных сфере.
Decision Requester - запрашивает решение через регулярные промежутки времени.
Behavior Parameters - определяет принятие объектом решений, в него указывается какой тип поведения будет использоваться: уже обученная модель или удалённый процесс обучения.
~~~
behaviors:
  RollerBall:                        #id агента
    trainer_type: ppo                #Устанавливаем режим обучения (Proximal Policy Optimization).
    hyperparameters:                 #Задаются гиперпараметры.
      batch_size: 10                 #Количество опытов на каждой итерации.
      buffer_size: 100               #Количество опыта, которое нужно набрать перед обновлением модели.
      learning_rate: 3.0e-4          #Начальная скорость.
      beta: 5.0e-4                   #Увеличивает случайность действий.
      epsilon: 0.2                   #Порог расхождений между старой и новой политиками при обновлении.
      lambd: 0.99                    #Параметр регуляции, насколько сильно агент полагается на value estimate.
      num_epoch: 3                   #Количество проходов через буфер опыта, при выполнении оптимизации.
      learning_rate_schedule: linear #Определяет, как скорость обучения изменяется с течением времени и линейно уменьшает скорость.
    network_settings:                #Определяет сетевые настройки.
      normalize: false               #Отключаем нормализацию входных данных.
      hidden_units: 128              #Количество нейронов в скрытых слоях сети.
      num_layers: 2                  #Количество скрытых слоев для размещения нейронов.
    reward_signals:                  #Задает сигналы о вознаграждении.
      extrinsic:
        gamma: 0.99                  #Коэффициент скидки для будущих вознаграждений.
        strength: 1.0                #Коэффициент на который умножается вознаграждение.
    max_steps: 500000                #Количество шагов, которые должны быть выполнены в среде до завершения обучения.
    time_horizon: 64                 #Количество циклов ML агента, хранящихся в буфере до ввода в модель.
    summary_freq: 10000              #Количество опыта, который необходимо собрать перед созданием и отображением статистики.
~~~
## Задание 3
### Доработайте сцену и обучите ML-Agent таким образом, чтобы шар перемещался между двумя кубами разного цвета. Кубы должны, как и впервом задании, случайно изменять кооринаты на плоскости.
- Добавила второй кубик:
![image](https://user-images.githubusercontent.com/104152574/197834522-3e5a5b00-235e-4a4e-8746-d81f8fa39723.png)
- Изменила код для двух кубиков:
~~~
using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using Unity.MLAgents;
using Unity.MLAgents.Sensors;
using Unity.MLAgents.Actuators;

public class RollerAgent : Agent
{
    Rigidbody rBody;
    void Start()
    {
        rBody = GetComponent<Rigidbody>();
    }
    public GameObject Target1;
    public GameObject Target2;
    private bool target1Collected;
    private bool target2Collected;
    public override void OnEpisodeBegin()
    {
        if (this.transform.localPosition.y < 0)
    {
        this.rBody.angularVelocity = Vector3.zero;
        this.rBody.velocity = Vector3.zero;
        this.transform.localPosition = new Vector3(0, 0.5f, 0);
    }
    Target1.transform.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
    Target2.transform.localPosition = new Vector3(Random.value * 8-4, 0.5f, Random.value * 8-4);
    Target1.SetActive(true);
    Target2.SetActive(true);
    target1Collected = false;
    target2Collected = false;
    }
    public override void CollectObservations(VectorSensor sensor)
    {
    sensor.AddObservation(Target1.transform.localPosition);
    sensor.AddObservation(Target2.transform.localPosition);
    sensor.AddObservation(this.transform.localPosition);
    sensor.AddObservation(target1Collected);
    sensor.AddObservation(target2Collected);
    sensor.AddObservation(rBody.velocity.x);
    sensor.AddObservation(rBody.velocity.z);
    }
    public float forceMultiplier = 10;
    public override void OnActionReceived(ActionBuffers actionBuffers)
    {Vector3 controlSignal = Vector3.zero;
    controlSignal.x = actionBuffers.ContinuousActions[0];
    controlSignal.z = actionBuffers.ContinuousActions[1];
    rBody.AddForce(controlSignal * forceMultiplier);
    float distanceToTarget1 = Vector3.Distance(this.transform.localPosition, Target1.transform.localPosition);
    float distanceToTarget2 = Vector3.Distance(this.transform.localPosition, Target2.transform.localPosition);
    if (!target1Collected & distanceToTarget1 < 1.42f)
    {
        target1Collected = true;
        Target1.SetActive(false);
    }
    if (!target2Collected & distanceToTarget2 < 1.42f)
    {
        target2Collected = true;
        Target2.SetActive(false);
    }
    if(target1Collected & target2Collected)
    {
        SetReward(1.0f);
        EndEpisode();
    }
    else if (this.transform.localPosition.y < 0)
    {
        EndEpisode();
    }
}
}
~~~
- Аналогично сделала несколько моделей и обучила их, результат работы:
https://user-images.githubusercontent.com/104152574/197835383-de20e1ed-da48-4d8f-88e3-34968561ee95.mp4
## Выводы
Игровой баланс является одним из требований к «честности» правил. Относительно простой нейронной сети достаточно, чтобы достичь высокой эффективности игры против игроков и традиционного игрового ИИ. Некоторые нейронные сети могут подстраивать баланс игры под хар-ки основного персонажа, по мере прохождения игроком игры, они могут увеличивать хар-ки других персонажей, чтобы вместе с основным героем также развивался и мир вокруг него.Таких агентов можно использовать различными способами, например, для тренировки новых игроков или для выявления неожиданных стратегий. Так же системы машинного обучения могут использоваться для того, чтобы выявить дисбаланс в игре.
| Plugin | README |
| ------ | ------ |
| Dropbox | [plugins/dropbox/README.md][PlDb] |
| GitHub | [plugins/github/README.md][PlGh] |
| Google Drive | [plugins/googledrive/README.md][PlGd] |
| OneDrive | [plugins/onedrive/README.md][PlOd] |
| Medium | [plugins/medium/README.md][PlMe] |
| Google Analytics | [plugins/googleanalytics/README.md][PlGa] |

## Powered by

**BigDigital Team: Denisov | Fadeev | Panov**
