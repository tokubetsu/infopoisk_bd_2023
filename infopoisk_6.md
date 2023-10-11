# Практика по докеру
## Полезные ссылки
[Докер хаб](https://hub.docker.com/)

[Ссылка на проект на диске](https://drive.google.com/file/d/11tfMKjDeClZF0xLdfEdxsjP41f_QKB6d/view?usp=sharing) (но можете ради интереса достать его из контейнера через volumes или cp)

## Образы
Образ с проектом: `tokubetsu/infopoisk-image`

Маленький образ для работы с volumes (из него можно только создать контейнер, но не запустить...): `tokubetsu/volume-small-image`

## Dockerfile и создание образа
Сам файл:
```
FROM python:3.10-slim

WORKDIR /usr/src/app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY app .

CMD ["python", "main.py"]
```
В папке запуска должны быть:
- файл `Dockerfile`
- файл `requirements.txt`
- папка с проектом `app`

Сама команда:
`docker build -t YOUR_USERNAME/infopoisk-image .`

## Загрузка на докер хаб
Сначала авторизуемся в докере через терминал (командную строку):
`docker login`

Потом присваеваем своему образу какой-то тег (нужен, чтобы различать образы внутри репозитория):
`docker tag YOUR_USERNAME/infopoisk-image YOUR_USERNAME/infopoisk-image:base`

Потом пушим образ на докер хаб:
`docker push YOUR_USERNAME/infopoisk-image:base`

## Работа с volumes
Создаем том:
`docker volume create infopoisk-vol`

Создаем маленький контейнер для переноса данных:
`docker create -v infopoisk-vol:/app/data --name small-volume-cont tokubetsu/volume-small-image`

Копируем данные в контейнер (и, следовательно, в том):
`docker cp /Users/v.i.zykova/lectures/infopoisk/docker/data small-volume-cont:/app`

Создаем и запускаем основной контейнер:
`docker run -v infopoisk-vol:/usr/src/app/data -p 5001:5000 --name cur-infopoisk-cont tokubetsu/infopoisk-image:base`




