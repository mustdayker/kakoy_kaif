### Стенд `first_steps`

Проект включает в себя следующие компоненты:
- **`PostgreSQL`** (Основная БД)
- **`Jupyterlab`** (Код отладка)
- **`Superset`** (Создание дашбордов)

# Как развернуть проект:
- Запустить `Docker`
- Открыть `PowerShell`
- Перейти в папку проекта: `cd C:\GitHub\kakoy_kaif\docker\first_steps`
- Находясь в папке с проектом выполнить: `docker compose up -d`
- Для остановки контейнеров выполнить: `docker compose down` (в конце работы) 

После этого докер создаст образы и развернет контейнеры.

### При первом запуске надо проинициализировать `Superset`

- Зайти в `PowerShell`
- Обратить внимание, что ты в рабочей папке: `C:\GitHub\kakoy_kaif\docker\first_steps`
- По очереди выполнить команды:
```bash
docker compose exec superset superset db upgrade

docker compose exec superset superset fab create-admin --username admin --firstname Admin --lastname User --email admin@example.com --password admin

docker compose exec superset superset init
```

--------------

# Управление стендом

- **Jupyter:** http://localhost:8888 Токен: `dataengineer`
- **Superset:** http://localhost:8088 Логин: `admin` Пароль: `admin`

### PostgreSQL (через `DBeaver`)
Подключение:
- Хост: `localhost`
- Порт: `5432`
- База: `learn_base` или `kakoy_kaif`
- Пользователь: `admin`
- Пароль: `admin`

### Папки

- **Ноутбуки:** `./jupyter/notebooks/`
- **База Superset:** `./superset/data/`
- Остальное служебное, трогать не надо

## Скрипты для Jupyterlab

### Проверка соединения с БД

```python

```


