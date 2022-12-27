# SUAI Cloud App

## Структура репозитория

* `README.md` - файл, который вы сейчас читаете;
* `sca` - веб-приложение;
* `config.toml` - файл конфигурации веб-приложения, написанный в нотации [TOML](https://ru.wikipedia.org/wiki/TOML).

## Конфигурация приложения

Для корректной работы приложения необходимо выполнить настройку [файла конфигурации](config.toml).

### Структура файла конфигурации

* `server` - параметры веб-серера
  * `host` - ip-адрес запуска сервера (`0.0.0.0` для того, чтобы сервер принимал запросы с любых адресов)
  * `port` - порт, на котором будет работать сервер
* `s3` - параметры Object Storage
  * `bucket` - имя Object Storage bucket
* `redis` - параметры Redis
  * `host` - адрес подключения
  * `port` - порт подключения
  * `password` - пароль
* `ydb` - параметры YDB
  * `database` - имя таблицы YDB

Пример конфигурации:

```toml
[server]
host = '0.0.0.0'
port = 8080

[s3]
bucket = 'suaicloudbucket'

[redis]
host = 'c-c9q7agm0d7mnjih2viem.rw.mdb.yandexcloud.net'
port = 6379
password = 'qwer1234'

[ydb]
database = '/ru-central1/b1gao46fjamokcltm31f/etne937s6d9mtntk6gsb'
```

Предполагается, что после внесения изменений данный файл конфигурации будет загружен в S3 bucket, с которого и будет автоматически загружаться на ВМ.
