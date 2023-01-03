# Web_services_HW_3

*Задание. Проверить всё ли нормально в работе связки веб-сервисов.*

- Есть 2 веб-сервиса:

|WS_1                           |WS_2                                |
|:---------:|:---------:|
|162.55.220.72:5031             |23.88.52.139:5032 |

---

|Method |Endpoint |
|:---------:|:---------:|
|GET |162.55.220.72:5031/jobs_count  |

- WS_1 получает запрос от клиента. 
- Никаких параметров не нужно.
- WS_1 отправляет запрос на WS_2 - 23.88.52.139:5032/get_jobs_count.
- WS_2 получает запрос от WS_1.
- WS_2 парсит json, в которой 7 вакансий и считает количество вакансий. По умолчанию в json 7 вакансий.
- WS_2 отправляет ответ на WS_1 в котором будет json:
  
```json
{
  "jobs_count": 7
}
```

- WS_1 получает ответ от WS_2 и отправляет json {“jobs_count”:7} клиенту.

`РЕШЕНИЕ:`

1. Отправить запрос "Task_2_WS_1_jobs_count" (http://162.55.220.72:5031/jobs_count) (Postman -> WS_1):  
   
Request:  
Method GET  
   
Response: 

```json
{
    "jobs_count": 276
}
```

2. Отправить запрос "Task_3_WS_2_get_jobs_count" (http://23.88.52.139:5032/get_jobs_count) (WS_1 -> WS_2):
   
Request:  
Method GET  
   
Response: 

```json
{
    "jobs_count": 276
}
```

---

|Method |Endpoint |
|:---------:|:---------:|
|GET |162.55.220.72:5031/all_jobs  |

- WS_1 получает запрос от клиента. 
- Никаких параметров не нужно.
- WS_1 отправляет запрос на WS_2.
- WS_2 получает запрос от WS_1.
- WS_2 парсит json, в которой 7 вакансий и считает количество вакансий. По умолчанию в json 7 вакансий.
- WS_2 отправляет ответ на WS_1 в котором будет json + все добавленные пользователем вакансии.
- WS_1 получает ответ от WS_2 и отправляет json клиенту.

`РЕШЕНИЕ:`

1. Отправить запрос "Task_3_WS_1_all_jobs" (http://162.55.220.72:5031/all_jobs) (Postman -> WS_1):
   
Request:  
Method GET  
   
Response: 

```json
{
Очень большой json. Можно посмотреть в коллекции;)
}
```

2. Отправить запрос "Task_3_WS_2_get_all_jobs" (http://23.88.52.139:5032/get_all_jobs) (WS_1 -> WS_2): 
   
Request:    
Method GET   
   
Response: 

```json
{
Очень большой json. Можно посмотреть в коллекции;)
}
```

---

|Method |Endpoint |
|:---------:|:---------:|
|POST |162.55.220.72:5031/add_job  |

- WS_1 получает запрос от клиента в теле которого должна быть json-ка:

```json
{
   "firm_title": “firm_title”,
   "position_title": “position_title”,
   "skills": [“skill_1”, “skill_2”, “skill_3”]
   "description": description,
   "Job Posting": job_posting,
   "Employee Status": employee_status
}
```

- WS_1 отправляет запрос на WS_2 - 23.88.52.139:5032/add_job_item
- В теле запроса должен быть json полученный от клиента.

```json
 {"firm_title": “firm_title”,
"position_title": “position_title”,
"skills": [“skill_1”, “skill_2”, “skill_3”]
 "description": description,
"Job Posting": job_posting,
"Employee Status": employee_status}
```

- WS_2 получает запрос от WS_1.
- WS_2 парсит json, в которой 7 вакансий и считает количество вакансий. По умолчанию в json 7 вакансий.
- WS_2 добавляет в  json присланную из WS_1 json.
- У добавленной вакансии будет id = +1 к общему количеству вакансий в json (n+1)

- WS_2 отправляет ответ на WS_1 в котором будет json

```json
{"result_message":"Job added. Job id is 8",
"check_message": "call /all_jobs endpoint for checking."}
```

`РЕШЕНИЕ:`

1. Отправить запрос "Task_3_WS_1_add_all_jobs" (http://162.55.220.72:5031/add_job) (Postman -> WS_1):
   
Request:  
Method POST
Body (Raw JSON):

Request:

```json
{
  "firm_title": "System Technologies",
  "position_title": "QA Manual",
  "skills": [
    "Postman",
    "Charles proxy",
    "client_server",
    "soft skills"
  ],
  "description": "Looking for a QA Manual (#Junior+/Middle) for a new project",
  "Job Posting": "Jan 03 2023",
  "Employee Status": "Remote, full time"
}
```
   
Response: 

```json
{
   "check_message": "call /all_jobs endpoint for checking.",
   "result_essage": "Job added. Job id is 277"
}
```

2. Отправить запрос "Task_3_WS_2_add_job_item" (http://23.88.52.139:5032/add_job_item) (WS_1 -> WS_2):
   
Request:    
Method POST  
Body (Raw JSON):  

Request:

```json
{
  "firm_title": "System Technologies",
  "position_title": "QA Manual",
  "skills": [
    "Postman",
    "Charles proxy",
    "client_server",
    "soft skills"
  ],
  "description": "Looking for a QA Manual (#Junior+/Middle) for a new project",
  "Job Posting": "Jan 03 2023",
  "Employee Status": "Remote, full time"
}
```
   
Response: 

```json
{
   "check_message": "call /all_jobs endpoint for checking.",
   "result_essage": "Job added. Job id is 278"
}
```

`РУЗУЛЬТАТ:`

1. Отсутствует часть json в ответах от 23.88.52.139:5032/add_job_item при выполнении запросов:
   
```json
"Job Posting": "..."
```

```
ЗАКЛЮЧЕНИЕ: имеется ошибка в работе 23.88.52.139:5032/add_job_item.
```
