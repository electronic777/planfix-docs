В [REST API](REST_API.md) можно получить список типов пользовательских полей c помощью метода **/customfield/type**. 


ID | Name | Название   

---|---|---  

0 | Line | Строка   

1 | Number | Число   

2 | Text | Текст   

3 | Date | Дата   

4 | Time | Время   

5 | Date and time | Дата и время   

6 | Period of time | Период времени   

7 | Checkbox | Чекбокс   

8 | List | Список   

9 | Directory entry | Запись справочника   

10 | Contact | Контакт   

11 | Employee | Сотрудник   

12 | Counterparty | Контрагент   

13 | Group, employee, or contact | Группа, сотрудник или контакт   

14 | List of users | Список пользователей   

15 | Set of directory values | Набор значений справочника   

16 | Task | Задача   

17 | Task set | Набор задач   

20 | Set of values | Набор значений   

21 | Files | Файлы   

22 | Project | Проект   

23 | Data tag summaries | Итоги аналитик   

24 | Calculated field | Вычисляемое поле   

25 | Location | Местоположение   

26 | Subtask total | Сумма подзадач   

27 | AI results field | Результат обучения   

28 | Date with time frame | Дата с периодом времени   

29 | Totals field | Суммарное поле   

  

## Пример


Запрос 

    

    

    curl -X 'GET' \

      'https://test.planfix.ru/rest/customfield/type' \

      -H 'accept: application/json' \

      -H 'Authorization: Bearer o4l3kwh6lkj43h6'

    


Ответ 

    

    

    {

      "result": "success",

      "customFieldTypes": [

        {

          "id": 0,

          "name": "Line"

        },

        {

          "id": 1,

          "name": "Number"

        },

        {

          "id": 2,

          "name": "Text"

        },

        {

          "id": 3,

          "name": "Date"

        },

        {

          "id": 4,

          "name": "Time"

        },

        {

          "id": 5,

          "name": "Date and time"

        },

        {

          "id": 6,

          "name": "Period of time"

        },

        {

          "id": 7,

          "name": "Checkbox"

        },

        {

          "id": 8,

          "name": "List"

        },

        {

          "id": 9,

          "name": "Directory entry"

        },

        {

          "id": 10,

          "name": "Contact"

        },

        {

          "id": 11,

          "name": "Employee"

        },

        {

          "id": 12,

          "name": "Counterparty"

        },

        {

          "id": 13,

          "name": "Group, employee, or contact"

        },

        {

          "id": 14,

          "name": "List of users"

        },

        {

          "id": 15,

          "name": "Set of directory values"

        },

        {

          "id": 16,

          "name": "Task"

        },

        {

          "id": 17,

          "name": "Task set"

        },

        {

          "id": 20,

          "name": "Set of values"

        },

        {

          "id": 21,

          "name": "Files"

        },

        {

          "id": 22,

          "name": "Project"

        },

        {

          "id": 23,

          "name": "Data tag summaries"

        },

        {

          "id": 24,

          "name": "Calculated field"

        },

        {

          "id": 25,

          "name": "Location"

        },

        {

          "id": 26,

          "name": "Subtask total"

        },

        {

          "id": 27,

          "name": "AI results field"

        },

        {

          "id": 28,

          "name": "Date with time frame"

        },

        {

          "id": 29,

          "name": "Totals field"

        }

      ]

    }
