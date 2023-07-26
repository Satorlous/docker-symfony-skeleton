## Начало работы

1. Установить [Docker Desktop](https://www.docker.com/products/docker-desktop/)
2. Запустить `docker compose build --pull --no-cache` или `make build` для сборки образов
3. Запустить `docker compose up --detach` или `make up` для запуска контейнеров
4. При **первом** запуске - дождаться окончания установки Composer пакетов.\
Проект устанавливается в папку **/tmp**. Она удалится, а все файлы из нее перенесутся в корень.
5. Приложение доступно по адресу `http://localhost:80`
6. Запустить `docker compose down --remove-orphans` или `make down` для остановки контейнеров.\
Флаг `--remove-orphans` удаляет контейнеры.

## Быстродействие при разработке

### WARNING: Действия строго после первого запуска!

Если для разработки вы используете **MacOS** или **Windows** и испытываете медленную скорость загрузки страницы,
то в файле `docker-compose.override.yml` раскомментируйте строку в блоке `volume` чтобы исключить директорию `vendor`
из маунта в контейнер:\
``- srv/app/vendor``

## Установка дополнительных Composer зависимостей

Composer зависимости необходимо устанавливать изнутри `php` контейнера. \
Для этого выполните команду `docker compose exec php sh` или `make sh`, чтобы попасть в терминал контейнера.
Вы окажетесь в корне проекта по пути `/srv/app`