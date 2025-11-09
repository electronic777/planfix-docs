Получение записей справочника. При наличии групп возвращает записи одного уровня. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="handbook.getRecords">

      <account></account>

      <sid></sid>

      <handbook>

        <id></id>

      </handbook>

      <parentKey></parentKey>

      <pageCurrent></pageCurrent>

      <pageSize></pageSize>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](ПланФикс_API_Аутентификация.md)  

handbook.id | int | идентификатор справочника |   

parentKey | int | идентификатор группы записей | необязательный параметр   

pageCurrent | int | номер страницы | от 1   

pageSize | int | размер страницы | до 100   

  

Ответ при успешном выполнении запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <records>

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

        <!--    -->

      </records>

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
