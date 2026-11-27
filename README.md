# AgilFrame Deploy

Готовые конфигурации развёртывания AgilFrame.

[AgilFrame](https://github.com/users/GillHD/projects/1) · [Core и документация](https://github.com/GillHD/agilframe-core)

Исходная версия компонентов: [e49af79](https://github.com/GillHD/agilframe-core/commit/e49af79496ed8d4e200f520e2f7dd162bf789a7d). [Лицензия](LICENSE) · [Уведомления](NOTICE)

## Запуск Core через Docker Compose

1. Скопируйте `.env.example` в `.env`.
2. Установите собственный случайный секрет подписи и отдельный ключ API. Сохраните формат `ключ:организация`. Для сетевого запуска укажите HTTPS-адрес Core.
3. Выполните `docker compose config --quiet`, затем `docker compose up -d --build`.
4. Проверьте `http://localhost:8787/v1/health`. Данные находятся в именованном томе `core-data`.

Compose собирает образ из закреплённого коммита [AgilFrame](https://github.com/GillHD/agilframe-core), а порт публикуется только на loopback. Для внешнего доступа настройте reverse proxy с TLS. Включайте доверие к proxy после ограничения прямого доступа к Core. Перед обновлением сделайте резервную копию тома, затем измените `AGILFRAME_REF` на проверенный SHA и пересоберите образ.

[Развёртывание](https://github.com/GillHD/agilframe-core/blob/main/agil/core/docs/deployment.md) · [Ноды](https://github.com/GillHD/agilframe-nodes) · [Бэкап и эксплуатация](https://github.com/GillHD/agilframe-core/blob/main/agil/core/docs/operations.md)
