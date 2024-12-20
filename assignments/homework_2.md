# Домашняя работа № 2
## Общие правила
- **Дедлайн: защита проектов, позже нельзя никак!**

## Общее задание
В рамках данного задания нужно обернуть ваш поиск в API. Обратите внимание, что для API принято возвращать результаты работы программы в формате словаря. Если ваши выходные данные подразумевают список, то сделайте верхнеуровневый словарь вида `{key: your_list}`, где `key` отражает содержание списка.

## На оценку 6 
1. Реализовать следующие эндпоинты API:
    - (1 балл) Возвращает список доступных методов поиска
    - (1 балл) Возвращает информацию о корпусе (хотя бы два поля; например, кол-во токенов и название корпуса)
    - (1 балл) Возвращает результаты поиска по запросу, можно регулировать кол-во текстов в выдаче и используемый вариант поиска
    - (1 балл) Возвращает результаты поиска по запросу с соответствующими оценками релевантности, можно регулировать кол-во текстов в выдаче и используемый вариант поиска (возможно реализовать данный пункт как параметр к предыдущему, а не как отдельный эндпоинт)
2. (1 балл) Все форматы входа и выхода для эндпоинтов должны быть прописаны как модели `pydantic`, варианты поиска и иные коллекции переменных (если есть) как `Enum`
3. (1 балл) Описать в readme файле, как правильно запустить ваш код: описание всех эндпоинтов, команда для запуска, название образа на docker-hub (если есть)

## На оценку выше 6 (не оценивается без выполнения первой части!)
1. (1 балл) Привести в отдельной тетрадке пример всех вариантов запросов к API; описать, какие эндпоинты и как используются в проекте
2. (1 балл) Ваш код должен соответствовать следующим критериям:
    - PEP8, докстринги и тайпинги (через библиотеку `typing`)
    - Осмысленные имена переменных, функций, классов, модулей
    - Разделение на модули (разные файлы для разных больших блоков логики)
    - Разделение на классы/функции
    - Одна очевидная для пользователя точка входа: файл, где стартует сервер API (в случае с докером он должен запускаться в `CMD` части `Dockerfile`)
3. (1 балл) Завернуть проект в докер-образ. После запуска контейнера по вашему образу должно быть возможно сразу обращаться к API.
4. (1 балл) Выложить образ на docker-hub, прикрепить в ридми команду, которой можно запустить контейнер по вашему образу
