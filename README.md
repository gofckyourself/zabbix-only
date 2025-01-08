# Zabbix Monitoring System with Docker Compose

Этот проект позволяет развернуть систему мониторинга Zabbix с использованием Docker Compose. В нем используются три контейнера:

- **Zabbix Server**: Сервер для хранения данных и обработки метрик.
- **Zabbix Web Interface**: Веб-интерфейс для управления Zabbix.
- **MySQL Database**: База данных для хранения данных Zabbix.

## Требования

Перед использованием убедитесь, что у вас установлены следующие компоненты:

- Docker: [Инструкция по установке Docker](https://docs.docker.com/get-docker/)
- Docker Compose: [Инструкция по установке Docker Compose](https://docs.docker.com/compose/install/)

## Установка

1. Клонируйте репозиторий:

    ```bash
    git clone https://github.com/gofckyourself/zabbix-only.git
    cd zabbix-only
    ```

2. Создайте файл `.env` в корне проекта и укажите пароли для MySQL:

    ```bash
    ZABBIX_MYSQL_PASSWORD=your_secure_zabbix_password
    ZABBIX_MYSQL_PASSWORD_ROOT=your_secure_root_password
    ```

    Убедитесь, что ваши пароли надежны и безопасны.

3. Запустите контейнеры с помощью Docker Compose:

    ```bash
    docker-compose up -d
    ```

    Это развернет все три контейнера (Zabbix Server, Zabbix Web, и MySQL).

## Доступ

- Веб-интерфейс Zabbix будет доступен по адресу: `http://ip_адрес_сервера`
    - Стандартные учетные данные:
        - **Логин**: `Admin`
        - **Пароль**: `zabbix`

- Сервер Zabbix будет доступен на порту 10051: `ip_адрес_сервера:10051`

## Технические детали

- **Zabbix Server** использует образ `zabbix/zabbix-server-mysql` и подключается к базе данных MySQL.
- **Zabbix Web Interface** использует образ `zabbix/zabbix-web-nginx-mysql` для предоставления веб-интерфейса.
- **MySQL** использует образ `mysql` для хранения данных.

## Volume

- Данные MySQL сохраняются в локальной папке `./zabbix/database/mysql`.
- Папка с данными будет автоматически создана Docker'ом, если она не существует.
