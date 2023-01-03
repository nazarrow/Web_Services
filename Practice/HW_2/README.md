# Web_services_HW_2

*Задание. Проверить всё ли нормально в работе связки веб-сервисов.*

- Есть 2 веб-сервиса:

|WS_1               |WS_2              |
|:---------:|:---------:|
|162.55.220.72:5021 |23.88.52.139:5022 |

---

|Method |Endpoint |
|:---------:|:---------:|
|GET |162.55.220.72:5021/jobs  |

- WS_1 получает запрос от клиента.  
- При отправке запроса из Postman никаких параметров не нужно.  
- WS_1 парсит json который храниться на файловой системе сервера.  
- Внутри этого json лежит 7 вакансий.  
- WS_1 возвращает клиенту json в котором будет 7 вакансий.  

---

|Method |Endpoint |
|:---------:|:---------:|
|POST |162.55.220.72:5021/jobs  |

- WS_1 получает запрос от клиента.  
- В теле запроса должен быть json:
 
```json
{
  "job_id": 1
} 
```

- После получения запроса, ws_1 парсит json, в которой 7 вакансий и отправляет запрос на ws_2 - 
23.88.52.139:5022/get_job.  
- В теле запроса должен быть json:
  
```json
{
    "job_id": 1, 
    "j_data": json
}
```

- WS_2 получает запрос от WS_1.  
- WS_2 выбирает одну вакансию у которой key = "job_id".  
- WS_2 возвращает json вакансии в WS_1:

```json
"1": {
    "Employee Status": "Full-time",
    "Job Posting": "Aug 02 2022",
    "description": "Experience with Functional Testing, including Regression Testing, Integration Testing, and API Testing. Experience with creating and executing test scripts. Experience testing developments against wireframes and style guide. Experience with systems, integration, and user acceptance testing. Experience in working with offshore /onsite Model",
    "firm_title": "Cognizant Technology Solutions",
    "position_title": "QA Functional Tester",
    "skills": [
        "postman",
        "js",
        "client_server",
        "api_testing"
    ]
    }
```

- WS_1 возвращает json вакансии клиенту.

`РЕШЕНИЕ:`

1. Отправить запрос "Task_2_WS_1_get" (http://162.55.220.72:5021/jobs) (Postman -> WS_1):  
   
Request:  
Method GET  
   
Response: 

```json
{
  "1": {
    "Employee Status": "Full-time",
    "Job Posting": "Aug 02 2022",
    "description": "Experience with Functional Testing, including Regression Testing, Integration Testing, and API Testing. Experience with creating and executing test scripts. Experience testing developments against wireframes and style guide. Experience with systems, integration, and user acceptance testing. Experience in working with offshore /onsite Model",
    "firm_title": "Cognizant Technology Solutions",
    "position_title": "QA Functional Tester",
    "skills": [
      "postman",
      "js",
      "client_server",
      "api_testing"
    ]
  },
  "2": {
    "Employee Status": "Full-time",
    "Job Posting": "Nov 10 2022",
    "description": "Under supervision, to monitor and evaluate testing results against predetermined objectives and apply recommended actions for improvements; to perform the design, development, execution and reporting efforts for projects using a single software testing technology competency (i.e., functional, systems, automation, performance, data accuracy, etc.) within a Waterfall and/or Agile software development process.",
    "firm_title": "The County of Santa Clara - Assessor",
    "position_title": "Test Engineer",
    "skills": [
      "DBAs",
      "Load test",
      "test plans"
    ]
  },
  "3": {
    "Employee Status": "Full-time",
    "Job Posting": "Nov 30 2022",
    "description": "Working closely with the business functions such as Quality and Regulatory Affairs to create ongoing enhancements and capabilities. Participating in deployment projects as a QA – including but not limited to requirements analysis, requirements documentation, and the creation and execution of test scripts.",
    "firm_title": "Jade Global",
    "position_title": "Jr. QA",
    "skills": [
      "functional testing",
      "user acceptance testing",
      "requirements documentation testing"
    ]
  },
  "4": {
    "Employee Status": "Full-time",
    "Job Posting": "Nov 22 2022",
    "description": "We are seeking a System Integration and Test Engineer to be responsible for development and maintenance of test scripts to be used during all satellite test phases. You should understand principles and disciplines such as policy, procedures, process discipline, operations, safety, and command media to perform job duties of Space Vehicle Test Engineering.",
    "firm_title": "LOCKHEED MARTIN CORPORATION",
    "position_title": "Test Engineer",
    "skills": [
      "Python Scripting Experience",
      "functionality test",
      "verbal communication skills",
      " strong social skills",
      "Familiarity with Git"
    ]
  },
  "5": {
    "Employee Status": "Full-time",
    "Job Posting": "Oct 14, 2022",
    "description": "The Bluetooth Quality team is looking for a motivated, highly-technical Bluetooth Quality Engineer with an ability to seek solutions to unusual problems with valued interpersonal skills. You will be responsible for ensuring the best customer experience and quality of Bluetooth in the latest Apple products.",
    "firm_title": "Apple",
    "position_title": "Wireless Bluetooth QA Engineer",
    "skills": [
      "Excellent written and verbal skills",
      "Excellent teammate ",
      "Bluetooth testing"
    ]
  },
  "6": {
    "Employee Status": "Full-time",
    "Job Posting": "Nov 15 2022",
    "description": "We are looking for a Quality Assurance (QA) engineer to develop and execute exploratory and automated tests to ensure product quality. QA engineer responsibilities include designing and implementing tests, debugging and defining corrective actions. You will also review system requirements and track quality assurance metrics.",
    "firm_title": "Banyan Data Services",
    "position_title": "Quality Assurance Engineer",
    "skills": [
      "API Testing",
      "Mobile testing",
      "Appium",
      "Selenium"
    ]
  },
  "7": {
    "Employee Status": " Full-time",
    "Job Posting": "Nov 29 2022",
    "description": "Focusing on web automation the team is primarily looking for people who experience in UI and API testing. Will need to have experience with Postman, Java, Selenium, TestNG and Cucumber. Develop, modify, automate and execute automated test scripts for various business scenarios in collaboration with Developers, Tech Leads and product partners. Keep up with close to 100% automation coverage for the teams. Improve areas where there are gap in automation coverage.",
    "firm_title": "Tek Ninjas",
    "position_title": "QA Engineer",
    "skills": [
      "Java"
    ]
  }
}
```

2. Отправить запрос "Task_2_WS_1_post" (http://162.55.220.72:5021/jobs) (Postman -> WS_1):
   
Request:  
Method POST  
Body (Raw JSON):

```json
{
  "job_id": 1
}
```

Response: 

```json
{
  "Employee Status": "Full-time",
  "description": "Experience with Functional Testing, including Regression Testing, Integration Testing, and API Testing. Experience with creating and executing test scripts. Experience testing developments against wireframes and style guide. Experience with systems, integration, and user acceptance testing. Experience in working with offshore /onsite Model",
  "firm_title": "Cognizant Technology Solutions",
  "position_title": "QA Functional Tester",
  "skills": [
    "postman",
    "js",
    "client_server",
    "api_testing"
  ]
}
```

3. Отправить запрос "Task_2_WS_2" (23.88.52.139:5022/get_job) (WS_1 -> WS_2):
   
Request:  
Method POST  
Body (Raw JSON):

```json
{
  "job_id": 1,
  "j_data": {
    "1": {
      "Employee Status": "Full-time",
      "description": "Experience with Functional Testing, including Regression Testing, Integration Testing, and API Testing. Experience with creating and executing test scripts. Experience testing developments against wireframes and style guide. Experience with systems, integration, and user acceptance testing. Experience in working with offshore /onsite Model",
      "firm_title": "Cognizant Technology Solutions",
      "position_title": "QA Functional Tester",
      "skills": [
        "postman",
        "js",
        "client_server",
        "api_testing"
      ]
    }
  }
}
```

Response: 

```json
{
  "Employee Status": "Full-time",
  "description": "Experience with Functional Testing, including Regression Testing, Integration Testing, and API Testing. Experience with creating and executing test scripts. Experience testing developments against wireframes and style guide. Experience with systems, integration, and user acceptance testing. Experience in working with offshore /onsite Model",
  "firm_title": "Cognizant Technology Solutions",
  "position_title": "QA Functional Tester",
  "skills": [
    "postman",
    "js",
    "client_server",
    "api_testing"
  ]
}
```

4. Отправить запрос "Task_2_WS_2_Checking_the_server" (23.88.52.139:5022/get_job) (WS_1 -> WS_2). Проверка работы WS_2:

Request:  
Method POST  
Body (Raw JSON):

```json
{
  "job_id": 1,
  "j_data": {
    "1": {
      "Employee Status": "Full-time",
      "Job Posting": "Aug 02 2022",
      "description": "Experience with Functional Testing, including Regression Testing, Integration Testing, and API Testing. Experience with creating and executing test scripts. Experience testing developments against wireframes and style guide. Experience with systems, integration, and user acceptance testing. Experience in working with offshore /onsite Model",
      "firm_title": "Cognizant Technology Solutions",
      "position_title": "QA Functional Tester",
      "skills": [
        "postman",
        "js",
        "client_server",
        "api_testing"
      ]
    },
    "2": {
      "Employee Status": "Full-time",
      "Job Posting": "Nov 10 2022",
      "description": "Under supervision, to monitor and evaluate testing results against predetermined objectives and apply recommended actions for improvements; to perform the design, development, execution and reporting efforts for projects using a single software testing technology competency (i.e., functional, systems, automation, performance, data accuracy, etc.) within a Waterfall and/or Agile software development process.",
      "firm_title": "The County of Santa Clara - Assessor",
      "position_title": "Test Engineer",
      "skills": [
        "DBAs",
        "Load test",
        "test plans"
      ]
    },
    "3": {
      "Employee Status": "Full-time",
      "Job Posting": "Nov 30 2022",
      "description": "Working closely with the business functions such as Quality and Regulatory Affairs to create ongoing enhancements and capabilities. Participating in deployment projects as a QA – including but not limited to requirements analysis, requirements documentation, and the creation and execution of test scripts.",
      "firm_title": "Jade Global",
      "position_title": "Jr. QA",
      "skills": [
        "functional testing",
        "user acceptance testing",
        "requirements documentation testing"
      ]
    },
    "4": {
      "Employee Status": "Full-time",
      "Job Posting": "Nov 22 2022",
      "description": "We are seeking a System Integration and Test Engineer to be responsible for development and maintenance of test scripts to be used during all satellite test phases. You should understand principles and disciplines such as policy, procedures, process discipline, operations, safety, and command media to perform job duties of Space Vehicle Test Engineering.",
      "firm_title": "LOCKHEED MARTIN CORPORATION",
      "position_title": "Test Engineer",
      "skills": [
        "Python Scripting Experience",
        "functionality test",
        "verbal communication skills",
        " strong social skills",
        "Familiarity with Git"
      ]
    },
    "5": {
      "Employee Status": "Full-time",
      "Job Posting": "Oct 14, 2022",
      "description": "The Bluetooth Quality team is looking for a motivated, highly-technical Bluetooth Quality Engineer with an ability to seek solutions to unusual problems with valued interpersonal skills. You will be responsible for ensuring the best customer experience and quality of Bluetooth in the latest Apple products.",
      "firm_title": "Apple",
      "position_title": "Wireless Bluetooth QA Engineer",
      "skills": [
        "Excellent written and verbal skills",
        "Excellent teammate ",
        "Bluetooth testing"
      ]
    },
    "6": {
      "Employee Status": "Full-time",
      "Job Posting": "Nov 15 2022",
      "description": "We are looking for a Quality Assurance (QA) engineer to develop and execute exploratory and automated tests to ensure product quality. QA engineer responsibilities include designing and implementing tests, debugging and defining corrective actions. You will also review system requirements and track quality assurance metrics.",
      "firm_title": "Banyan Data Services",
      "position_title": "Quality Assurance Engineer",
      "skills": [
        "API Testing",
        "Mobile testing",
        "Appium",
        "Selenium"
      ]
    },
    "7": {
      "Employee Status": " Full-time",
      "Job Posting": "Nov 29 2022",
      "description": "Focusing on web automation the team is primarily looking for people who experience in UI and API testing. Will need to have experience with Postman, Java, Selenium, TestNG and Cucumber. Develop, modify, automate and execute automated test scripts for various business scenarios in collaboration with Developers, Tech Leads and product partners. Keep up with close to 100% automation coverage for the teams. Improve areas where there are gap in automation coverage.",
      "firm_title": "Tek Ninjas",
      "position_title": "QA Engineer",
      "skills": [
        "Java"
      ]
    }
  }
}
```

Response: 

```json
{
  "Employee Status": "Full-time",
  "Job Posting": "Aug 02 2022",
  "description": "Experience with Functional Testing, including Regression Testing, Integration Testing, and API Testing. Experience with creating and executing test scripts. Experience testing developments against wireframes and style guide. Experience with systems, integration, and user acceptance testing. Experience in working with offshore /onsite Model",
  "firm_title": "Cognizant Technology Solutions",
  "position_title": "QA Functional Tester",
  "skills": [
    "postman",
    "js",
    "client_server",
    "api_testing"
  ]
}
```

`РУЗУЛЬТАТ:`

1. Отсутствует часть json в ответе от WS_1 при выполнении запроса от клиента (Postman) -> WS_1 методом POST:
   
```json
"Job Posting": "..."
```

2. Требуемый json приходит в ответе от WS_2 при выполнении запроса WS_1 -> WS_2(п.4 "Решение").

```
ЗАКЛЮЧЕНИЕ: имеется ошибка в работе WS_1.
```