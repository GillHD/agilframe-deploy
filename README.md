# AgilFrame Deploy

**Русский** · [English](README.en.md)

Конфигурация Docker Compose для самостоятельного развёртывания AgilFrame Core. Compose собирает образ из репозитория Core по коммиту, указанному в `AGILFRAME_REF`, и хранит данные в именованном томе `core-data`.

[Проект AgilFrame](https://github.com/GillHD/agilframe) · [Core](https://github.com/GillHD/agilframe-core)

## Запуск Core

Установите Docker Engine и Docker Compose. В корне этого репозитория создайте файл `.env` из шаблона.

```bash
cp .env.example .env
```

Замените значения `AGIL_TOKEN_SECRET` и `AGIL_API_KEYS` собственными случайными секретами. Сохраните формат `ключ:организация` для ключа API. Для внешнего доступа укажите публичный HTTPS-адрес в `AGIL_PUBLIC_ORIGIN`.

```bash
docker compose config --quiet
docker compose up -d --build
curl --fail http://localhost:8787/v1/health
```

Порт Core по умолчанию доступен на `127.0.0.1:8787`. Для внешнего доступа поставьте перед ним обратный прокси-сервер с TLS. Включайте `AGIL_TRUST_PROXY` после ограничения прямого доступа к Core.

## Обновление и проверка конфигурации

Перед обновлением сохраните резервную копию тома `core-data`. Укажите проверенный коммит Core в `AGILFRAME_REF` и повторите проверку конфигурации и запуск с пересборкой.

Для проверки синтаксиса Compose без запуска Core используйте шаблон окружения.

```bash
docker compose --env-file .env.example config --quiet
```

[Развёртывание](https://github.com/GillHD/agilframe-core/blob/main/agil/core/docs/deployment.md) · [Резервное копирование и эксплуатация](https://github.com/GillHD/agilframe-core/blob/main/agil/core/docs/operations.md) · [Медианоды](https://github.com/GillHD/agilframe-nodes)

[Лицензия](LICENSE) · [Уведомления](NOTICE) · [Как внести вклад](CONTRIBUTING.md) · [Безопасность](SECURITY.md)
