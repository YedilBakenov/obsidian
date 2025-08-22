
Для замены статического значения `cache-config.ttl` на динамическое значение, получаемое из базы данных через сервис настроек, нужно изменить конфигурацию и методы, использующие это значение.

Нужно вынести cache-config.ttl из конфига дэплоя в настройки сервиса.


Костино уточнение:

Так ты глянь что то такое cache ttl
Это ровно то что у тебя лежит в базе и спеке уже
Одно на другое заменяем, зачем тебе что-то ещё в спеке
Там лежит FiniteDuration, его можно из строки получить
cache ttl везде нужно удалить
ttl это time to live
У тебя теперь есть более конкретные параметры
Щас там грубо говоря хардкод
Название переменной не понятное и везде одно и тоже
Что для драфта, что для завки
И даже разницы между клиентом и водителем там не делается
Поэтому у тебя 4 переменных а не одна
Чтобы можно было более тонко настроить приложение


1. Создал таблицу в миграции
2. Создал слой дао
3. Создал сервис
4.  - Нужно везде заменить в сервисе от статичного значения ttl из конфига на динамическое значение из базы данных кассандра



Работал по замечаниям в  задачке с Конфигурацией времени жизни заявки. Настройки которой берутся из базы данных кассандры.

1. Внес изменения в dao в запросе `updateSettings` для  для корректного использования интерполятора `cql` с полями типа `Option`
2. **Замечание по обработке настроек в `SettingsService`**:
	 Внес изменения в метод `getSettings`по обрабокам ошибок

3.  Замечание по обработке опций в `ClientTicketService`
    В методах `save` и `put` сервиса `ClientTicketService` внесены изменения для обработки отсутствующих настроек.

4. Замечание по улучшению кода в `ClientTicketService`




нужно переделать запрос в сql 

192.168.1 - локальный порт на подключение к тестированию - менять в файле Context

поменять tcp get tcp в Context


поменть локальный порт - чтобы тестить локально тесты - там же в it/Context


  session <- getLocal(client, cassandra, 9042).flatMap { (host, port) => - должно быть так для тестов
        CassandraSession.connect[IO](
          CqlSession
            .builder
            .addContactPoint(new InetSocketAddress(host.show, port.value))
        )
      }
      redisConn <- getLocal(client, redis, 6379).flatMap { (host, port) =>
        RedisConnection
          .pool[IO]
          .withHost(host)
          .withPort(port)
          .build
      }




 session <- getDevHostPort(client, cassandra, 9042).flatMap { (host, port) =>
        CassandraSession.connect[IO](
          CqlSession
            .builder
            .addContactPoint(new InetSocketAddress(host.show, port.value))
        )
      }
      redisConn <- getDevHostPort(client, redis, 6379).flatMap { (host, port) =>
        RedisConnection
          .pool[IO]
          .withHost(host)
          .withPort(port)
          .build
      }

добавить еще hhtp ендпоинт, чтобы он ходил в сервис

в кейс классе Settings сделать два поля только, убрать вложенность, убрать айди, будет только два поля 


Посмотреть как разбиваются партиции в кассандре, Костя скинул послежний мр в гитлабе с двумя партициями

https://gitlab.com/hivetaxi/backend/intercity/-/merge_requests/7/diffs?page=2#1e830d68375de4d9717fbb94a41e78b1b8b6d98b_0_25

[https://gitlab.com/hivetaxi/backend/intercity/-/merge_requests/7/diffs?page=2#c04e2a880436996eae37aefadd4c0d71bf25550d_0_24](https://gitlab.com/hivetaxi/backend/intercity/-/merge_requests/7/diffs?page=2#c04e2a880436996eae37aefadd4c0d71bf25550d_0_24)


https://gitlab.com/hivetaxi/backend/intercity/-/merge_requests/3/diffs?page=3#e7ff28cca16a555fca8861cb94c428bf311e245b_176_194



Ай, больно. У тебя уже сгенерирован Endpoint. Тебе его нужно просто превратить в route => навесить на него хэндлер






