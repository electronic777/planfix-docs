Функция получения информации о пользователе. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="user.get">

      <account></account>

      <sid></sid>

      <user>

        <id></id>

        <general></general>

      </user>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

user.id | int | идентификатор пользователя | при отсутствии данного параметра и параметра general, возвращаются данные сотрудника, от которого происходит запрос   

user.general | int | номер сотрудника |   

signature | string(32) | подпись |   

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <user>

        <id></id>

        <general></general>

        <name></name>

        <lastName></lastName>

        <midName></midName>

        <login></login>

        <email></email>

        <secondaryEmails>

            <email></email>

            <!-- ... -->

        </secondaryEmails>

        <role></role>

        <status></status>

        <birthdate></birthdate>

        <sex></sex>

        <telegramId></telegramId>

        <phones>

            <phone>

                <number></number>

                <typeId><typeId>

                <typeName><typeName>

            </phone>

            ...

        </phones>

        <isInvisibleOutOfGroup></isInvisibleOutOfGroup>

        <isBlindOutOfGroup></isBlindOutOfGroup>

        <userPic></userPic>

        <isOnline></isOnline>

        <timezone></timezone>

        <post>

            <id></id>

            <name></name>

        </post>

        <userGroups>

          <userGroup>

            <id></id>

            <name></name>

          </userGroup>

          <userGroup>

            <id></id>

            <name></name>

          </userGroup>

          <!-- ... -->

        </userGroups>

      </user>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор сотрудника |   

general | int | номер сотрудника |   

name | string | имя, отчество пользователя |   

lastName | string | фамилия пользователя |   

midName | string | отчество пользователя |   

login | string | имя учетной записи в системе |   

email | string | электронный адрес почты |   

secondaryEmails.email |  | дополнительные адреса email, если есть |   

role | enum | роль пользователя в системе |   

status | enum | статус | список допустимых значений смотри в разделе [статусы пользователей](Задачи/ПланФикс_API_Статусы_пользователей.md)  

birthdate | DateTime | дата рождения | если значение не установлено, то значение пусто   

sex | enum | пол сотрудника | список допустимых значений смотри в разделе [пол сотрудника](Контакты/ПланФикс_API_Пол_сотрудника.md), если значение не установлено, то значение пусто   

phones |  | список телефонов |   

phones.phone.number | string | номер телефона |   

phones.phone.typeId | int | идентификатор типа номера телефона |   

phones.phone.typeName | string | название типа номера телефона |   

isInvisibleOutOfGroup | bool | true=Видит только членов своих групп; false=Видит всех сотрудников | доступно для пользователей с правами администратор   

isBlindOutOfGroup | bool | true=Его видят только члены его групп; false=Его видят все сотрудники | доступно для пользователей с правами администратор   

userPic | string | возвращает полный URL к картинке | если не установлен - узел пустой   

timezone | string | часовой пояс сотрудника |   

post |  | должность пользователя |   

post.id | int | идентификатор должности |   

post.name | string | название должности |   

userGroups |  | список групп в которых состоит пользователь |   

userGroups.userGroup |  | группа |   

userGroups.userGroup.id | int | идентификатор группы |   

userGroups.userGroup.name | string | название группы |   

telegramId | int | внутренний идентификатор в Telegram | возвращается только если включены уведомления в Telegram   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
