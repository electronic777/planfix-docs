Получение данных аналитик по заданному условию. 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="analitic.getDataByCondition">

      <account></account>

      <sid></sid>

      <analitic>

        <id></id>

      </analitic>

      <task>

        <id></id>

        <general></general>

      </task>

      <filters>

        <filter>

          <field></field>

          <fromDate></fromDate>

          <toDate></toDate>

          <userid></userid>

        </filter>			  

      </filters>

      <pageSize></pageSize>

      <pageCurrent></pageCurrent>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](ПланФикс_API_Аутентификация.md)  

analitic.id | int | идентификатор аналитики |   

task.id | int | идентификатор задачи  | необязательный, если отсутствует - выбор по всем задачам   

task.general | int | номер задачи   

pageCurrent | int | страница |   

pageSize | int | размер страницы (максимум 100) |   

filters |  | условия |   

filter.field | int | идентификатор поля аналитики по которому делается условие |   

filter.fromDate | DateTime | для условия по дате - от даты |   

filter.toDate | DateTime | для условия по дате - до даты |   

filter.userid | int | для условия по полю типа Список пользователей / Сотрудник / Группа, сотрудник или контакт - идентификатор сотрудника, как он возвращается функцией user.GetList |   

  

Ответ при успешном выполнении запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <analiticDatas>

        <analiticData>

          <key></key>

          <task>

            <id></id>

          </task>

          <action>

            <id></id>

          </action>

          <itemData>

            <id></id>

            <name></name>

            <value></value>

            <valueId></valueId>

          </itemData>

          <!-- ... -->

        </analiticData>

        <analiticData>

          <key></key>

          <itemData>

            <id></id>

            <name></name>

            <value></value>

            <valueId></valueId>

          </itemData>

          <!-- ... -->

        </analiticData>

        <!-- ... -->

      </analiticDatas>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

analiticDatas |  | список запрошенных аналитик |   

analiticData |  | узел описывающий данные, которые содержит аналитика |   

analiticData.key | int | идентификатор данных |   

analiticData.task.id | int | идентификатор задачи, к которой прикреплена аналитика |   

analiticData.action.id | int | идентификатор действия, к которому прикреплена аналитика |   

analiticData.itemData |  | узел описывающие запись с данными в аналитике |   

itemData.id | int | идентификатор, он равен [field.id](ПланФикс_API_analitic.getOptions.md) |   

itemData.name | string | имя поля |   

itemData.value | string | текстовое значение |   

itemData.valueId | string | значение идентификатор, для полей-объектов |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
