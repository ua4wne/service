# skillbox-diploma
Чтобы скопировать репозиторий к себе для работы, вам нужно следовать [этим инструкциям](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-on-github/duplicating-a-repository#mirroring-a-repository-in-another-location).

## Runtime
Приложение отвечает по 3 эндпоинтам:  
* /health - 200 ok
* /metrics - в формате метрик для prometheus, включая счётчик запросов в основной эндпоинт `skillbox_http_requests_total`
* / - основной эндпоинт, возвращающий часть запроса и генерирующий строчку лога.

## Как работать с приложением без docker:  
1. Установить golang 1.16
2. Установить зависимости:

   ```shell
   go mod download
   ```

3. Запустить тесты:
   ```shell
   go test -v ./...
   ```
4. Собрать приложение:
   ```
   GO111MODULE=on go build -o app cmd/server/app.go
   ```
5. Запустить его:
   ```shell
   ./app
   ```

## Как работать с приложением в docker:
```
1. Установить значения констант container_name, container_image, host_port и container_port для запускаемого сервиса. Значения констант должны быть понятны из их названия.
2. Перейти в папку ansible и запустить плейбук install_service.yml, который создаст и запустит контейнер с определенными на шаге 1 настройками.```
