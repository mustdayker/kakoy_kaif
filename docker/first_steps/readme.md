### Стенд `first_steps`

Проект включает в себя следующие компоненты:
- **`PostgreSQL`** (Основная БД)
- **`Jupyterlab`** (Код отладка)
- **`Superset`** (Создание дашбордов)

# Управление стендом

**Старт работы**
- Развернуть сервисы: `docker compose up -d`
- Остановить сервисы: `docker compose down` 

**Интерфейсы сервисов** (когда контейнеры стартовали)
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

# ВАЖНО!! Папки

### Папку `C:\GitHub\kakoy_kaif\docker\first_steps\jupyter\datasets` 
- Создаем руками именно с таким именем. 
- Сама папка `datasets` и все что в ней не синхронизируется с `GitHub`. 
- А соответственно в нее можно пихать тяжелые датасеты и вообще любые файлы.

Эти папки монтируются в Jupyter и видны в контейнере по http://localhost:8888 и на локальной машине в `C:\GitHub\kakoy_kaif\docker\first_steps\jupyter\` 
- **Ноутбуки:** `./jupyter/`
- **Датасеты:** `./jupyter/datasets` - эта папка видна в контейнере, но не синхронится с `GitHub`
- Остальное служебное, трогать не надо


