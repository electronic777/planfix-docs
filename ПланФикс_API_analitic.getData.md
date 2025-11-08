Получение данных аналитики прикрепленной действием. Список доступных аналитик получают из [списка действий](ПланФикс_API_action.getList.md "ПланФикс API action.getList"). Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="analitic.getData">

      <account></account>

      <sid></sid>

      <analiticKeys>

        <key></key>

        <key></key>

        <!-- ... -->

      </analiticKeys>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](ПланФикс_API_Аутентификация.md "ПланФикс API:Аутентификация")  

analiticKeys.key | int | идентификатор строки данных аналитики | возвращается функцией [action.get](ПланФикс_API_action.get.md "ПланФикс API action.get")  

  

Допускается одним запросом получать данные сразу нескольких добавленных аналитик. Если в запросе был передан идентификатор несуществующей аналитики, то будет возвращена пустая аналитика, ошибка при этом не будет генерироваться. 


Ответ при успешном выполнении запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <analiticDatas>

        <analiticData>

          <key></key>

          <itemData>

            <id></id>

            <name></name>

            <value></value>

            <valueId></valueId>

          </itemData>

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

analiticData.itemData |  | узел описывающие запись с данными в аналитике |   

itemData.id | int | идентификатор, он равен [field.id](ПланФикс_API_analitic.getOptions.md "ПланФикс API analitic.getOptions") |   

itemData.name | string | имя поля |   

itemData.value | string | значение (строковое представления) |   

itemData.valueId | string | значение (идентификатор для полей, содержащих объект) |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
