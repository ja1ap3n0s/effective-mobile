# Effective Mobile — тестовое задание DevOps

## Запуск

Нужны Docker и Docker Compose (v2).

```bash
docker compose up -d --build
```

Если порт 80 занят, в файле `.env` задать нужный порт можно в переменной `NGINX_HOST_PORT` и откройте `http://localhost:<порт>`.

## Проверка результата

```bash
curl http://localhost
```

Ожидаемый ответ:

```
Hello from Effective Mobile!
```

Остановка: `docker compose down`.

## Как работает схема

Запрос приходит на **nginx** (единственный сервис с проброшенным портом на хост). Nginx по внутренней сети Docker пересылает запрос на сервис **backend** (nginx → backend).
