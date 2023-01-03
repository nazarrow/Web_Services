# Web_services_HW_1

*Задание. Проверить всё ли нормально в работе связки веб-сервисов.*

- Есть 2 веб-сервиса:

|WS_1                           |WS_2                                |
|:---------:|:---------:|
|http://162.55.220.72:5011/user |http://23.88.52.139:5012/users_team |

- WS_1 получает запрос от клиента:

Method POST  
Body (Raw JSON):

*Вставьте свой уникальный user_id*

```json
{
   "user_id":1
}
``` 

- После получения запроса, ws_1 отправляет запрос на ws_2:

Method POST  
Body (Raw JSON):

```json
{
  "type": "padawan",
  "spec": "QA",
  "ex": "1",
  "current_user": {
    "uid": 1,
    "uip:": "5.152.62.104"
  }
}
```

- WS_2 принимает запрос от ws_1, дополняет полученную Json дополнительной информацией.  
- WS_2 отправляет ответ на ws_1 в виде:

```json
{
  "user_divices_data": {
    "comp": {
      "model": "Macbook",
      "monitor_diagonal": 16,
      "ram": 32,
      "resolution": [
        "Liquid Retina XDR",
        "3456x2234"
      ],
      "ssd": 1000,
      "year": 2021
    },
    "mobile": {
      "cpu": "ARM, SnapDragon 840",
      "model": "Samsung a52",
      "os": "Android",
      "ram": 6
    }
  },
  "user_static_data": {
    "current_user": {
      "uid": 1,
      "uip:": "127.0.0.1"
    },
    "ex": "1",
    "spec": "QA",
    "type": "padawan"
  }
}
```

- Ws_1 перенаправляет запрос клиенту.

`РЕШЕНИЕ:`

1. Создать коллекцию в Postman с именем "Web_services"
2. Отправить запрос "Task_1_WS_1" (http://162.55.220.72:5011/user) с указанными параметрами выше (Postman -> WS_1):  
   
Request:  
Method POST  
Body (Raw JSON):

```json
{
"user_id":88
}
```  

Response: 

```json
{
  "user_divices_data": {
    "comp": {
      "model": "Macbook",
      "monitor_diagonal": 16,
      "ram": 32,
      "resolution": [
        "Liquid Retina XDR",
        "3456x2234"
      ],
      "ssd": 1000,
      "year": 2021
    },
    "mobile": {}
  },
  "user_static_data": {
    "current_user": {
      "uid": 88,
      "uip:": "93.171.161.50"
    },
    "ex": "1",
    "spec": "QA",
    "type": "padawan"
  }
}
```

3. Отправить запрос "Task_1_WS_2" (http://23.88.52.139:5012/users_team) с указанными параметрами выше (WS_1 -> WS_2):  
   
Request:  
Method POST  
Body (Raw JSON):

```json
{
  "type": "padawan",
  "spec": "QA",
  "ex": "1",
  "current_user": {
    "uid": 88,
    "uip:": "5.152.62.104"
  }
}
```

Response: 

```json
{
  "current_user": {
    "uid": 88,
    "uip:": "5.152.62.104"
  },
  "ex": "1",
  "spec": "QA",
  "type": "padawan",
  "user_divices_data": {
    "comp": {
      "model": "Macbook",
      "monitor_diagonal": 16,
      "ram": 32,
      "resolution": [
        "Liquid Retina XDR",
        "3456x2234"
      ],
      "ssd": 1000,
      "year": 2021
    },
    "mobile": {}
  }
}
```

`РУЗУЛЬТАТ:`

1. Отсутствует часть json в ответе от WS_1 при выполнении запроса от клиента (Postman) -> WS_1:
   
```json
"mobile": {}
```

2. Отсутствует часть json в ответе от WS_2 при выполнении запроса WS_1 -> WS_2:

```json
"mobile": {}
```

```
ЗАКЛЮЧЕНИЕ: имеется ошибка в работе WS_2.
```