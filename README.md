# АНАЛИЗ ДАННЫХ И ИСКУССТВЕННЫЙ ИНТЕЛЛЕКТ [in GameDev]
Отчет по лабораторной работе #1 выполнил(а):
- Иванова Ивана Варкравтовна
- РИ000024
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

## Цель работы
Ознакомиться с основными операторами зыка Python на примере реализации линейной регрессии.

## Задание 1
### Реализовать совместную работу и передачу данных в связке Python - Google-Sheets – Unity.
- Установила Google Sheets API и Google Drive API:
![image](https://user-images.githubusercontent.com/104152574/194777117-fe7ac4d5-5dff-4bda-927f-10d07eb55405.png)
- Создала service account:
![image](https://user-images.githubusercontent.com/104152574/194777299-03bd975b-d74a-4b1a-a7fe-7bf0ab328243.png)
- Создала UnitySheets и добавила редактора:
![image](https://user-images.githubusercontent.com/104152574/194777339-79794399-b701-43f2-a8d3-554288daca26.png)
- Подключила пакеты и заполнила таблицу UnitySheets:
![image](https://user-images.githubusercontent.com/104152574/194777939-e04b91b7-ae7e-4d6b-8d1a-0c8752643175.png)
![image](https://user-images.githubusercontent.com/104152574/194777948-4570e72f-7813-4a3a-9137-68e03c606c54.png)
- Создала API key и сделала UnitySheets доступным для редактирования:
![image](https://user-images.githubusercontent.com/104152574/194778076-e0f62289-6fe4-4f4c-a759-33e0c6e4bad2.png)
![image](https://user-images.githubusercontent.com/104152574/194778120-0ec81860-2d97-4ad5-a7aa-acc9240c6038.png)
- Создала проект и импортировал файлы в Unity:
![image](https://user-images.githubusercontent.com/104152574/194778637-f1c78108-dde5-44bd-b844-be9d49d67b73.png)
- Связала Unity и GoogleSheets:
![image](https://user-images.githubusercontent.com/104152574/194779476-d971a9d0-c558-46ac-a360-66bd9ed901c0.png)
![image](https://user-images.githubusercontent.com/104152574/194779481-96a0ba79-3097-4e03-9429-aef4ad4f0480.png)
![image](https://user-images.githubusercontent.com/104152574/194779504-e805eb4c-b917-427e-8430-3c858e31611c.png)
- Подключила музыку:
![image](https://user-images.githubusercontent.com/104152574/194779766-180a8d99-d216-4776-8a5a-767f98f368a4.png)
![image](https://user-images.githubusercontent.com/104152574/194779777-38380c69-6c2f-401f-8726-6321c7283ba4.png)
- Прослушала аудио:
![image](https://user-images.githubusercontent.com/104152574/194779801-708bbc45-5f76-4af3-82bf-4410f23250ac.png)
## Задание 2
### Реализовать запись в Google-таблицу набора данных, полученных с помощью линейной регрессии из лабораторной работы № 1.
Ход работы:
- Пройдемся 10 раз с шагом в 100, 200 и тд. 100 итераций, посчитаем разницу ошибок на каждой итерации и загрузим данные в таблицу:
![image](https://user-images.githubusercontent.com/104152574/194780496-35ee0590-7fa9-45f8-9591-e07b5c390d24.png)
![image](https://user-images.githubusercontent.com/104152574/194780489-7c5edbc2-63b3-4a39-8769-8f8cc6a4af64.png)
![image](https://user-images.githubusercontent.com/104152574/194780439-ace4d610-6469-4eca-bacf-ff15d21bcbc8.png)
## Задание 3
### Самостоятельно разработать сценарий воспроизведения звукового сопровождения в Unity в зависимости от изменения считанных данных в задании 2.
Ход работы:
- Совершенствуем предыдущий код в юнити:
![image](https://user-images.githubusercontent.com/104152574/194782269-f215d042-1e4f-47da-bf85-e47345864201.png)
## Выводы
Я узнала как работать с Google Spreadsheets API на Python при помощи gspread, узнала как получать данные из Google Spreadsheets в Unity.
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
