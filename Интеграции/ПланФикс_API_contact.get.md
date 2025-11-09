Функция получения информации о клиенте. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="contact.get">

      <account></account>

      <sid></sid>

      <contact>

        <id></id>

        <userid></userid>

        <general></general>

      </contact>

      <fields>

        <field>lastUpdateDate</field>

        ...

      </fields>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

contact.id | int | идентификатор контакта |   

general | int | номер контакта | если задан, используется вместо id   

userid | int | идентификатор контакта для случаев, когда он используется в системе наравне с сотрудниками (исполнитель задачи и т.п., а также пользовательское поле типа контакт) | если задан, используется вместо id при отсутствии general   

fields |  | получить дополнительные поля |   

fields.field | string | поле, возможные значения: 


  * **lastUpdateDate** \- дата последнего изменения

  * **lastCommentDate** \- дата последнего комментария


| одноименное поле будет добавлено в ответ в узел contact   

signature | string(32) | подпись |   

  

  

Результат успешного выполнения функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <contact>

        <id></id>

        <userid></userid>

        <general></general>

        <template>

          <id></id>

        </template>

        <name></name>

        <midName></midName>

        <lastName></lastName>

        <isCompany></isCompany>

        <post></post>

        <email></email>

        <secondaryEmails>

            <email></email>

            <!-- ... -->

        </secondaryEmails>

        <phones>

            <phone>

                <number></number>

                <typeId><typeId>

                <typeName><typeName>

            </phone>

            ...

        </phones>

        <address></address>

        <description></description>

        <sex></sex>

        <site></site>

        <skype></skype>

        <icq></icq>

        <userPic></userPic>

        <birthdate></birthdate>

        <group>

          <id></id>

          <name></name>

        </group>

        <contractors>

          <client>

            <id></id>

            <name></name>

          </client>

          <client>

            <id></id>

            <name></name>

          </client>

          <!-- ... -->

        </contractors>

        <havePlanfixAccess>{true|false}</havePlanfixAccess>

        <telegram>

          <id></id>

        </telegram>

        <customData>

          <customValue>

            <field>

              <id></id>

              <name></name>

            </field>

            <value></value>

            <text></text>

          </customValue>

          <customValue>

            <!-- ... -->

          </customValue>

          <!-- ... -->

        </customData>

        <responsible>

          <users>

            <user>

              <id></id>

              <name></name>

            </user>

            <!-- ... -->

          </users>

          <groups>

            <group>

              <id></id>

              <name></name>

            </group>

            <!-- ... -->

          </groups>

        </responsible>

      </contact>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор контакта |   

userid | int | идентификатор контакта для случаев, когда он используется в системе наравне с сотрудниками (исполнитель задачи и т.п., а также пользовательское поле типа контакт) |   

general | int | номер контакта |   

template.id | int | номер шаблона контакта |   

name | string | Имя Отчество |   

midName | string | Отчество |   

lastName | string | Фамилия |   

isCompany | boolean | Является компанией |   

post | string | Должность |   

email | string | адрес электронной почты |   

secondaryEmails.email |  | дополнительные адреса email, если есть |   

phones |  | список телефонов |   

phones.phone.number | string | номер телефона |   

phones.phone.typeId | int | идентификатор типа номера телефона |   

phones.phone.typeName | string | название типа номера телефона |   

address | string | Адрес |   

description | string | Дополнительная информация |   

sex | enum | пол | допустимые значения смотри в разделе [пол клиента](Контакты/ПланФикс_API_Пол_клиента.md), если значение не установлено, то значение пусто   

site | string | веб-сайт |   

skype | string | skype-контакт |   

icq | string | номер-icq |   

userPic | string | ссылка на изображение |   

birthdate | DateTime | дата рождения |   

group |  | группа контакта |   

group.id | int | идентификатор группы |   

group.name | string | название группы |   

signature | string(32) | подпись |   

contractors |  | список компаний, к которым он относится |   

contractors.client |  | описание компании |   

contractors.client.id | int | идентификатор компании |   

contractors.client.name | string | имя/название компании |   

havePlanfixAccess | bool | имеет ли контакт доступ к ПланФикс | данный параметр возвращается только пользователю с правами администратор   

telegram.id | int | внутренний идентификатор в Telegram | возвращается только для контактов из Telegram   

customData |  | значения пользовательских полей задачи |   

customData.customValue.field.id |  | идентификатор пользовательского поля |   

customData.customValue.field.name |  | название пользовательского поля |   

customData.customValue.value |  | значение пользовательского поля |   

customData.customValue.text |  | текстовое значение пользовательского поля |   

responsible |  | корневой элемент списка ответственных |   

responsible.users |  | корневой элемент списка ответственных |   

responsible.users.user | node | пользователь |   

responsible.users.user.id | int | идентификатор пользователя |   

responsible.users.user.name | string | имя пользователя |   

responsible.groups |  | корневой элемент списка групп ответственных |   

responsible.groups.group | node | группа |   

responsible.groups.group.id | int | идентификатор группы |   

responsible.groups.group.name | string | название группы |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
