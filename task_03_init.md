# Инициализация сервисов

## Как развернуть проект:
- Запустить `Docker`
- Открыть `PowerShell`
- Перейти в папку проекта: `cd C:\GitHub\kakoy_kaif\docker\first_steps`
- Находясь в папке с проектом выполнить: `docker compose up -d`
- Для остановки контейнеров выполнить: `docker compose down` (в конце работы) 

После этого докер создаст образы и развернет контейнеры.

Проект включает в себя следующие компоненты:
- **`PostgreSQL`** (Основная БД)
- **`Jupyterlab`** (Код отладка)
- **`Superset`** (Создание дашбордов)

# Управление стендом

### Интерфейсы сервисов (когда контейнеры стартовали)
- **Jupyter:** http://localhost:8888 Токен: `dataengineer`
- **Superset:** http://localhost:8088 Логин: `admin` Пароль: `admin`

### PostgreSQL
Подключение:
- Хост: `localhost` (При подключении напрямую с компа, например `DBeaver` или `Jupyter` в системе)
- Хост: `postgres-db` (При подключении из контейнеров, например [**Jupyter**](http://localhost:8888) или [**Superset**](http://localhost:8088))
- Порт: `5432`
- База: `learn_base` или `kakoy_kaif`
- Пользователь: `admin`
- Пароль: `admin`

### Рабочие папки

- **Ноутбуки:** `./jupyter/work/`
- **Датасеты:** `./jupyter/work/datasets` - эта папка не синхронится с `GitHub` (можно пихать тяжелые файлы)

> - Эти папки монтируются в Jupyter и видны в контейнере по http://localhost:8888
> - И на локальной машине в `C:\GitHub\kakoy_kaif\docker\first_steps\jupyter\`
> - Внутри можно создавать любые папки, все будет синхронизировано с GitHub кроме папки `datasets`

Остальное служебное, трогать не надо

# Задание

- Зайди во все сервисы, Superset, Jupyter, потыкай там.
- В базу зайди через DBeaver, тоже потыкай.
- Остальное в следующем задании


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
