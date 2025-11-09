Получение справочника для аналитики. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="analitic.getHandbook">

      <account></account>

      <sid></sid>

      <handbook>

        <id></id>

      </handbook>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](ПланФикс_API_Аутентификация.md)  

handbook.id | int | идентификатор справочника | получается в результате выполнения функции [получить описание аналитики](ПланФикс_API_analitic.getOptions.md)  

  

Ответ при успешном выполнении запроса: 

    

    

    <response status="ok">

      <records>

        <record>

          <key></key>

          <parentKey></parentKey>

          <isGroup></isGroup>

          <value value="" name="" isDisplayed="" />

          <value value="" name="" isDisplayed="" />

          <!-- ... -->

        </record>

        <record>

          <key></key>

          <parentKey></parentKey>

          <isGroup></isGroup>

          <value value="" name="" isDisplayed="" />

          <value value="" name="" isDisplayed="" />

          <!-- ... -->

        </record>

        <!-- ... -->

      </records>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

records |  | список записей в справочнике |   

record |  | узел описывающий запись в справочнике |   

record.key | int | идентификатор записи |   

record.parentKey | int | идентификатор родительской записи |   

record.isGroup | bool | является ли узел родителем/названием группы | записи данного типа не могут использоваться для аналитике, используются для группировки данных   

record.value |  | узел описывающий данные в записи |   

value **value** | string | значение поля |   

value **name** | string | имя |   

value **isDisplayed** | bool | отображаемое поле или нет |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
