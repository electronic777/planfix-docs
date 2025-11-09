Запрос на получение списка аналитик имеет следующий вид: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="analitic.getList">

        <account></account>

        <sid></sid>

        <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

account | string | аккаунт, на котором выполняется запрос |   

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](Интеграции/ПланФикс_API_Аутентификация.md)  

signature | string(32) | подпись пакета |   

  

Ответ, при успешном выполнении запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

        <analitics  count="count" totalCount="totalCount">

            <analitic>

                <id></id>

                <name></name>

                <group>

                    <id></id>

                    <name></name>

                </group>

            </analitic>

            <analitic>

                <id></id>

                <name></name>

                <group>

                    <id></id>

                    <name></name>

                </group>

            </analitic>

            <!-- ... -->

        </analitics>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**analitics** | int | список аналитик |   

**analitics** count | int | количество аналитик в списке |   

**analitics** totalCount | int | количество аналитик в списке |   

analitic |  | аналитика |   

analitic.id | int | идентификатор аналитики |   

analitic.name | string | название аналитики |   

analitic.group |  | группа |   

analitic.group.id | int | идентификатор группы |   

analitic.group.name | string | название группы |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
