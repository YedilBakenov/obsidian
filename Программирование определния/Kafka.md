
Kafka — это распределенная платформа для обработки потоков данных, созданная для обработки, хранения и передачи большого объема данных в режиме реального времени. Она широко используется для логирования, аналитики, обработки событий и других задач, где требуется высокая производительность, отказоустойчивость и масштабируемость.

Kafka состоит из следующих ключевых компонентов:

1. **Брокеры**: Серверы, которые принимают и хранят данные.
2. **Топики**: Каналы, через которые передаются данные.
3. **Продюсеры (Producers)**: Отправляют данные в топики.
4. **Консьюмеры (Consumers)**: Получают данные из топиков.
5. **Zookeeper (или KRaft)**: Служба координации для управления кластерами Kafka (с версии 3.3 KRaft может заменить Zookeeper).


официальная документация: https://kafka.apache.org/documentation/

пример: 
java -jar telltale.jar 

  bootstrap-servers=127.0.0.1:9092 

  topic=client-orders-payment 

  message=ClientOrderPaymentRequestEnvelope

  mode=produce 

  json-file=C:\Users\region_008\Desktop\order.json

В сервисе пмс все есть для понятия что куда и как идет. В тестах можно посмотреть как записываются данные в базу, креды должны быть валидными в джейсон файле.


**➜**  **Desktop** java -jar telltale.jar \

  bootstrap-servers=dev.regionlab.kz:9192 \

  topic=client-orders-payment \

  message=  \

  mode=produce \

  json-file=/Users/region_008/Desktop/order.json

  

Invalid json : [

  {

    "key": "123",

    "message": {

      "create":  {

      "orderId": "123456",

      "clientId": "client_001",

      "currency": "USD",

      "profileId": "profile_123",

      "xLocation": "40.712776,-74.005974",

      "receiver": "payment-response-topic",

      "rewardPartner": true,

      "meta": {

        "key1": "value1",

        "key2": "value2"

      },

      "paymentMethod": {

        "paymentMethod": {

          "cash"

        }

      },

      "clientPhone": "+1234567890"

     }

    }

  }

]