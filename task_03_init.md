# Инициализация сервисов

## Как развернуть проект:
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
