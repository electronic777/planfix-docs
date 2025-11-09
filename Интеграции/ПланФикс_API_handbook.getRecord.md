Получение записи справочника. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="handbook.getRecord">

      <account></account>

      <sid></sid>

      <handbook>

        <id></id>

      </handbook>

      <key></key>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](ПланФикс_API_Аутентификация.md)  

handbook.id | int | идентификатор справочника |   

key | int | идентификатор записи |   

  

Ответ при успешном выполнении запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

        <record>

          <parentKey></parentKey>

          <isGroup></isGroup>

          <key></key>

          <name></name>

          <archived></archived>

          <customData>

            <customValue>

              <field>

                <id></id>

              </field>

              <value></value>

              <text></text>

            </customValue>

            <!-- -->

          </customData>

        </record>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

parentKey | int | идентификатор группы записей |   

isGroup | bool | является ли запись группой |   

key | int | идентификатор записи |   

name | string | название, если запись является группой |   

archived | bool | является ли запись архивной |   

customData |  | данные записи |   

customData.customValue.field.id |  | идентификатор поля |   

customData.customValue.value |  | значение поля |   

customData.customValue.text |  | текстовое значение поля |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
