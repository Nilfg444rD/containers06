# Лабораторная работа: Название лабораторной работы

## Цель работы

Ознакомиться с работой многоконтейнерного приложения на базе docker-compose.

## Задание

Создать php приложение на базе трех контейнеров: nginx, php-fpm, mariadb, используя docker-compose.

## Описание выполнения работы с ответами на вопросы

    1.Подготовительные шаги: Инициализация репозитория containers06 и его клонирование на локальный ПК.
    2.Разработка сайта на PHP: В папке containers06/mounts/site производится создание веб-сайта на PHP.
    3.Настройка конфигурационных файлов: Формируются необходимые конфигурационные файлы, включая .gitignore, nginx/default.conf и docker-compose.yml.
    4.Конфигурация базы данных: Генерируется файл mysql.env с настройками переменных окружения для MySQL.
    5.Запуск и проверка функционирования: Контейнеры активируются через docker-compose up -d, после чего осуществляется проверка функциональности сайта через веб-браузер.





### Вопросы:

#### В каком порядке запускаются контейнеры?
Контейнеры в Docker Compose обычно запускаются в порядке зависимостей, указанных в файле `docker-compose.yml`. Если один контейнер зависит от другого (например, frontend может зависеть от backend), то сначала запустится backend.

#### Где хранятся данные базы данных?
Данные базы данных обычно хранятся в Docker volumes. Это обеспечивает постоянство данных между запусками контейнеров и улучшает производительность по сравнению с хранением данных в контейнере.

#### Как называются контейнеры проекта?
Названия контейнеров проекта обычно задаются в файле `docker-compose.yml` под ключом `services`. Каждый сервис в этом файле будет именоваться согласно указанному названию.

#### Файл app.env
Нужно Создать файл app.env в корневой директории проекта containers06 с содержанием:
APP_VERSION=1.0.0
Далее нужно Отредактировать  файл docker-compose.yml, добавив ссылку на этот файл в сервисах backend и frontend:
services:
  backend:
    env_file:
      - app.env
  frontend:
    env_file:
      - app.env

