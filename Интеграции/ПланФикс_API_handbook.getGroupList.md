Запрос на получение списка групп справочников имеет следующий вид: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="handbook.getGroupList">

        <account></account>

        <sid></sid>

        <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

account | string | аккаунт, на котором выполняется запрос |   

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](ПланФикс_API_Аутентификация.md)  

signature | string(32) | подпись пакета |   

  

Ответ, при успешном выполнении запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

        <handbookGroups count="count" totalCount="totalCount">

            <group>

                <id></id>

                <name></name>

            </group>

            <group>

                <id></id>

                <name></name>

            </group>

            <!-- ... -->

        </handbookGroups>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**handbookGroups** | int | список групп |   

**handbookGroups** count | int | количество групп в списке |   

**handbookGroups** totalCount | int | количество групп в списке |   

group |  | группа |   

group.id | int | идентификатор группы |   

group.name | string | название группы |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
