Запрос на получение списка справочников имеет следующий вид: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="handbook.getList">

        <account></account>

        <sid></sid>

        <group>

          <id></id>

        </group>

        <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

account | string | аккаунт, на котором выполняется запрос |   

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](ПланФикс_API_Аутентификация.md)  

group.id | int | идентификатор группы | необязательный параметр   

signature | string(32) | подпись пакета |   

  

Ответ, при успешном выполнении запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

        <handbooks count="count" totalCount="totalCount">

            <handbook>

                <id></id>

                <name></name>

                <group>

                    <id></id>

                    <name></name>

                </group>

            </handbook>

            <handbook>

                <id></id>

                <name></name>

                <group>

                    <id></id>

                    <name></name>

                </group>

            </handbook>

            <!-- ... -->

        </handbooks>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**handbooks** | int | список справочников |   

**handbooks** count | int | количество справочников в списке |   

**handbooks** totalCount | int | количество справочников в списке |   

handbook |  | справочник |   

handbook.id | int | идентификатор справочника |   

handbook.name | string | название справочника |   

handbook.group |  | группа |   

handbook.group.id | int | идентификатор группы |   

handbook.group.name | string | название группы |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
