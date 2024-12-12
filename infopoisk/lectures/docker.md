# Практика по докеру
## Полезные ссылки
[Докер хаб](https://hub.docker.com/)
[Ссылка на проект на диске](https://drive.google.com/file/d/1JawFxQwG4md3fqgMocusTOVvkj24Mcy5/view?usp=sharing)

## Dockerfile и создание образа
Сам файл (лежит в архиве с проектом, но на всякий случай):
```
FROM python:3.10-slim

WORKDIR /usr/src/app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY app .

RUN python prepare.py

EXPOSE 8000

CMD ["python", "app.py"]

```
В папке запуска должны быть:
- файл `Dockerfile`
- файл `requirements.txt`
- папка с проектом `app`

Команда для сборки образа:
`docker build -t YOUR_USERNAME/PROJECT_NAME:TAG .`

Пример:
`docker build -t some_user/small_api:base .`

Команда для запуска контейнера:
`docker run -p HOST_PORT:CONTAINER_PORT --name CONTAINER_NAME YOUR_USERNAME/PROJECT_NAME:TAG`

Пример:
`docker run -p 8000:8000 --name small_api some_user/small_api:base`

Если не хочется, чтобы запущенный контейнер висел в терминале, то можно запустить его в фоне, для чего необходимо добавить параметр `-d` в команду запуска:
`docker run -d -p HOST_PORT:CONTAINER_PORT --name CONTAINER_NAME YOUR_USERNAME/PROJECT_NAME:TAG`

## Загрузка на докер хаб
Сначала авторизуемся в докере через терминал (командную строку):
`docker login`

Потом присваеваем своему образу какой-то тег (нужен, чтобы различать образы внутри репозитория), если не сделали этого ранее:
`docker tag YOUR_USERNAME/PROJECT_NAME YOUR_USERNAME/PROJECT_NAME:TAG`

Потом пушим образ на докер хаб:
`docker push YOUR_USERNAME/PROJECT_NAME:TAG`
