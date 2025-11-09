Функция добавления нового пользователя. Выполнение данной функции разрешено пользователю с админ правами. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="user.add">

      <account></account>

      <sid></sid>

      <user>

        <name>Имя</name>

        <midName>Отчество</midName>

        <lastName>Фамилия</lastName>

        <email></email>

        <role></role>

        <status></status>

        <post>

          <id></id>

        </post>

        <phones>

            <phone>

                <number></number>

                <typeId></typeId>

                <typeName></typeName>

            </phone>

            <!-- ... -->

        </phones>

      </user>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

name | string | имя пользователя |   

midName | string | отчество пользователя |   

lastName | string | фамилия пользователя |   

email | string | email пользователя |   

role | enum | роль пользователя в системе | допустимые значения _ADMIN_ , **USER**. полный список смотри в разделе [роли пользователей](Интеграции/ПланФикс_API_Роли_пользователей.md)  

post.id | int | идентификатор должности | не обязательное поле   

status | enum | статус пользователя | список допустимых значений смотри в разделе [статусы пользователей](Задачи/ПланФикс_API_Статусы_пользователей.md)  

phones | string | телефоны |   

phone.number | string | номер телефона |   

phone.typeId | int | идентификатор типа номера | допустимые значения можно получить функцией [contact.getPhoneTypes](Интеграции/ПланФикс_API_contact.getPhoneTypes.md)  

phone.typeName | string | название типа номера |   

signature | string(32) | подпись |   

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <user>

        <id></id>

      </user>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор созданного пользователя |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
