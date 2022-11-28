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

Структура отчета

- Данные о работе: название работы, фио, группа, выполненные задания.
- Цель работы.
- Задание 1.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 2.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Задание 3.
- Код реализации выполнения задания. Визуализация результатов выполнения (если применимо).
- Выводы.
- ✨Magic ✨

## Цель работы
Ознакомиться с работой перцептрона.
## Задание 1
### В проекте Unity реализовать перцептрон, который производит вычисления:
Ход работы:
- Добавить EmptyObgect и скрипт Perceptron в новый проект.
![image](https://user-images.githubusercontent.com/104152574/204274280-7bd4007e-8154-48bb-9a38-7acb69e381de.png)
- Для всех Element заполняем поле Input:
1) OR - понадобилось 4 эпохи обучения, начиная с 5 он корректно выполняет работу.
![image](https://user-images.githubusercontent.com/104152574/204278051-86562842-c020-4a82-ac0a-57af5adce83e.png)
![image](https://user-images.githubusercontent.com/104152574/204278134-d040d1df-542c-4f04-822f-5353830be136.png)
![image](https://user-images.githubusercontent.com/104152574/204278189-0f626d5e-9042-4c44-82da-c601adf533da.png)
2) AND - понадобилось 5 эпох обучения, начиная с 6 он корректно выполняет работу.
![image](https://user-images.githubusercontent.com/104152574/204279081-250f0434-a9d9-4cf2-9a27-e8809b185f82.png)
![image](https://user-images.githubusercontent.com/104152574/204279166-effb54ee-3c6f-4a3a-ae05-30005082121f.png)
![image](https://user-images.githubusercontent.com/104152574/204279208-b7cf3508-96e3-49b0-8e44-eedfda6af47b.png)
![image](https://user-images.githubusercontent.com/104152574/204279238-48e2bbf3-5626-44b0-aa6f-770b796a464c.png)
3) NAND - понадобилось 6 эпох обучения, начиная с 7 он корректно выполняет работу.
![image](https://user-images.githubusercontent.com/104152574/204279989-63b52f1c-eca8-4d4d-9bd8-613d2d03d040.png)
![image](https://user-images.githubusercontent.com/104152574/204280027-ae78f9c5-48dc-43ec-ab43-382acef4bee7.png)
![image](https://user-images.githubusercontent.com/104152574/204280060-996a7c43-1e64-42f5-8b11-9ed8b5957e31.png)
![image](https://user-images.githubusercontent.com/104152574/204280098-3eec9012-7fd0-43b5-8fef-b8c7fcf7d6f8.png)
![image](https://user-images.githubusercontent.com/104152574/204280132-f1b30b77-2778-4134-b080-0640299d42d1.png)
4) XOR - даже после прохождения 10000 эпох перцептрон не обучился, он некорректно выполняет работу.
![image](https://user-images.githubusercontent.com/104152574/204280833-7e550617-35b5-4e42-9258-895944be1256.png)
![image](https://user-images.githubusercontent.com/104152574/204280796-04164c5c-7a7b-43c0-9954-47630350fe6a.png)
## Задание 2
### Пошагово выполнить каждый пункт раздела "ход работы" с описанием и примерами реализации задач.

## Задание 3
### Должна ли величина loss стремиться к нулю при изменении исходных данных? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ.


## Задание 3
### Какова роль параметра Lr? Ответьте на вопрос, приведите пример выполнения кода, который подтверждает ваш ответ. В качестве эксперимента можете изменить значение параметра.

## Выводы
Я познакомилась с основными операторами языка Python на примере линейной регрессии, узнала о "потерях" предсказания и методе оптиизации для минимизации, некоторых методах библиотек numpy и matplotlib.
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
