Функция обновления данных пользователя. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="user.update">

      <account></account>

      <sid></sid>

      <user>

        <id></id>

        <name></name>

        <midName></midName>

        <lastName></lastName>

        <email></email>

        <role></role>

        <status></status>

        <password></password>

        <birthdate></birthdate>

        <sex></sex>

        <phones>

            <phone>

                <number></number>

                <typeId></typeId>

                <typeName></typeName>

            </phone>

            <!-- ... -->

        </phones>

        <isInvisibleOutOfGroup></isInvisibleOutOfGroup>

        <isBlindOutOfGroup></isBlindOutOfGroup>

        <userPic></userPic>

        <post>

            <id></id>

        </post>

      </user>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int |  |   

name | string | имя пользователя |   

midName | string | отчество пользователя | необязательное поле   

lastName | string | фамилия пользователя | необязательное поле   

email | string | электронный адрес почты | необязательное поле   

role | enum | роль пользователя в системе | необязательное поле. доступно для изменения только пользователям с правами администратор. полный список смотри в разделе [роли пользователей](ПланФикс_API_Роли_пользователей.md "ПланФикс API:Роли пользователей")  

status | enum | статус | необязательное поле. доступно для изменения только пользователям с правами администратор. список допустимых значений смотри в разделе [статусы пользователей](ПланФикс_API_Статусы_пользователей.md "ПланФикс API:Статусы пользователей")  

password | string | пароль | необязательное поле   

birthdate | DateTime | дата рождения | необязательное поле   

sex | enum | пол сотрудника | необязательное поле. список допустимых значений смотри в разделе [пол сотрудника](ПланФикс_API_Пол_сотрудника.md "ПланФикс API:Пол сотрудника")  

phones | string | телефоны |   

phone.number | string | номер телефона |   

phone.typeId | int | идентификатор типа номера | допустимые значения можно получить функцией [contact.getPhoneTypes](ПланФикс_API_contact.getPhoneTypes.md "ПланФикс API contact.getPhoneTypes")  

phone.typeName | string | название типа номера |   

isInvisibleOutOfGroup | bool | true=Видит только членов своих групп; false=Видит всех сотрудников | необязательное поле. доступно для изменения только пользователям с правами администратор   

isBlindOutOfGroup | bool | true=Его видят только члены его групп; false=Его видят все сотрудники | необязательное поле. доступно для изменения только пользователям с правами администратор   

userPic | string | base64 закодированная картинка | необязательное поле   

post.id | int | должность которую занимает пользователь | необязательное поле   

  

  

Результат успешного выполнения функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <user>

        <id></id>

      </user>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

user.id | int | идентификатор обновляемого пользователя |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
