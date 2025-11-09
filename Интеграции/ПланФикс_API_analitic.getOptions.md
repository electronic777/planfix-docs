Получение описания аналитики - полное содержимое полей и их типов значений. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="analitic.getOptions">

      <account></account>

      <sid></sid>

      <analitic>

        <id></id>

      </analitic>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](Интеграции/ПланФикс_API_Аутентификация.md)  

analitic.id | int | идентификатор аналитики |   

  

Ответ при успешном выполнении запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <analitic>

        <id></id>

        <name></name>

        <group>

          <id></id>

        </group>

        <fields>

          <field>

            <id></id>

            <num></num>

            <name></name>

            <type></type>

            <list>

              <value></value>

              <value></value>

              <!-- ... -->

            </list>

            <handbook>

              <id></id>

            </handbook>

          </field>

          <field>

            <id></id>

            <num></num>

            <name></name>

            <type></type>

            <list>

              <value></value>

              <value></value>

              <!-- ... -->

            </list>

            <handbook>

              <id></id>

            </handbook>

          </field>

          <!-- ... -->

        </fields>

      </analitic>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор аналитики |   

name | string | название аналитики |   

group.id | int | идентификатор группы аналитики |   

fields |  | узел, содержащий список полей аналитики |   

fields.field |  | узел, описывающий поле аналитики |   

field.id | int | идентификатор поля | требуется в запросах при добавлении аналитики к действию   

field.num | int | порядковый номер | для интерфейса   

field.name | string | описание поля |   

field.type | enum | тип данных в поле | перечень допустимых значений для данного поля смотри в разделе [типы данных полей аналитики](Аналитика/ПланФикс_API_Типы_данных_полей_аналитики.md)  

field.list |  | список допустимых значений для поля, если **type** =_LIST_ |   

field.list.value | string | значение поля |   

field.handbook.id | int | идентификатор справочника, если **type** =_HANDBOOK_ |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
