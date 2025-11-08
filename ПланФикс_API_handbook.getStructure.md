Получение описания справочника - полное содержимое полей и их типов значений. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="handbook.getStructure">

      <account></account>

      <sid></sid>

      <handbook>

        <id></id>

      </handbook>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](ПланФикс_API_Аутентификация.md "ПланФикс API:Аутентификация")  

handbook.id | int | идентификатор справочника |   

  

Ответ при успешном выполнении запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <handbook>

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

      </handbook>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор справочника |   

name | string | название справочника |   

group.id | int | идентификатор группы справочников |   

fields |  | узел, содержащий список полей справочника |   

fields.field |  | узел, описывающий поле справочника |   

field.id | int | идентификатор поля | требуется в запросах при добавлении записи   

field.num | int | порядковый номер | для интерфейса   

field.name | string | описание поля |   

field.type | enum | тип данных в поле | перечень допустимых значений для данного поля смотри в разделе [типы данных полей аналитики](ПланФикс_API_Типы_данных_полей_аналитики.md "ПланФикс API:Типы данных полей аналитики")  

field.list |  | список допустимых значений для поля, если **type** =_LIST_ |   

field.list.value | string | значение поля |   

field.handbook.id | int | идентификатор справочника, если **type** =_HANDBOOK_ |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
