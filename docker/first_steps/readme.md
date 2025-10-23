### Стенд `first_steps`

Проект включает в себя следующие компоненты:
- **`PostgreSQL`** (Основная БД)
- **`Jupyterlab`** (Код отладка)
- **`Superset`** (Создание дашбордов)

# Управление стендом

- **Jupyter:** http://localhost:8888 Токен: `dataengineer`
- **Superset:** http://localhost:8088 Логин: `admin` Пароль: `admin`

### PostgreSQL
Подключение:
- Хост: `localhost` (При подключении через `DBeaver`)
- Хост: `postgres-db` (При подключении из контейнеров, например [**Jupyter**](http://localhost:8888) или [**Superset**](http://localhost:8088))
- Порт: `5432`
- База: `learn_base` или `kakoy_kaif`
- Пользователь: `admin`
- Пароль: `admin`

# ВАЖНО!! Папки

### Папку `C:\GitHub\kakoy_kaif\docker\first_steps\jupyter\datasets` 
Создаем руками именно с таким именем. Сама папка `datasets` и все что в ней не синхронизируется с `GitHub`. А соответственно в нее можно пихать тяжелые датасеты и вообще любые файлы.
Эти папки монтируются в Jupyter и видны в контейнере по http://localhost:8888 и на локальной машине в `C:\GitHub\kakoy_kaif\docker\first_steps\jupyter\datasets` 
- **Ноутбуки:** `./jupyter/`
- **Датасеты:** `./jupyter/datasets` - эта папка видна в контейнере, но не синхронится с `GitHub`
- Остальное служебное, трогать не надо



--------

# Как развернуть проект:
- Запустить `Docker`
- Открыть `PowerShell`
- Перейти в папку проекта: `cd C:\GitHub\kakoy_kaif\docker\first_steps`
- Находясь в папке с проектом выполнить: `docker compose up -d`
- Для остановки контейнеров выполнить: `docker compose down` (в конце работы) 

После этого докер создаст образы и развернет контейнеры.



## Если `Superset` не принимает пароль

Значит БД с ним не проинициализирована, чтобы исправить:

- Зайти в `PowerShell`
- Обратить внимание, что ты в рабочей папке: `C:\GitHub\kakoy_kaif\docker\first_steps`
- По очереди выполнить команды:
```bash
docker compose exec superset superset db upgrade

docker compose exec superset superset fab create-admin --username admin --firstname Admin --lastname User --email admin@example.com --password admin

docker compose exec superset superset init
```
Но должно все работать, так как я уже один раз прогнал этот сценарий.

