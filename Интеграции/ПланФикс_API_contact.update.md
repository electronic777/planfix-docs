Функция обновления информации о клиенте. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="contact.update">

      <account></account>

      <sid></sid>

      <silent></silent>

      <contact>

        <id></id>

        <userid></userid>

        <general></general>

        <name></name>

        <midName></midName>

        <lastName></lastName>

        <template></template>

        <post></post>

        <email></email>

        <phones>

            <phone>

                <number></number>

                <typeId></typeId>

                <typeName></typeName>

            </phone>

            <!-- ... -->

        </phones>

        <secondaryEmails>

            <email></email>

            <!-- ... -->

        </secondaryEmails>

        <address></address>

        <description></description>

        <sex></sex>

        <site></site>

        <skype></skype>

        <facebook></facebook>

        <vk></vk>

        <icq></icq>

        <birthdate></birthdate>

        <lang></lang>

        <canBeWorker></canBeWorker>

        <canBeClient></canBeClient>

        <group>

          <id></id>

        </group>

        <customData>

          <customValue>

            <id></id>

            <value></value>

          </customValue>

          <!-- ... -->

        </customData>

        <responsible>

          <users>

            <id></id>

            <id></id>

            <!-- ... -->

          </users>

          <groups>

            <id></id>

            <id></id>

            <!-- ... -->

          </groups>

        </responsible>

        <telegram>

          <id></id>

          <username></username>

        </telegram>

      </contact>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

silent | bool | при значении 1 - об изменении не рассылаются уведомления, не создаются действия и записи в логе контакта | обязательно значение 1 при массовых периодических обновлениях контактов   

id | int | идентификатор обновляемого контакта |   

userid | int | идентификатор контакта, если он взят из данных, когда он используется в системе наравне с сотрудниками (исполнитель задачи и т.п., а также пользовательское поле типа контакт) или из переменных {{Контакт.Идентификатор}}, {{Задача.Контрагент.Идентификатор}} и им подобных |   

general | int | номер обновляемого контакта (используется если не задан id) |   

name | string | Имя |   

midName | string | Отчество |   

lastName | string | Фамилия |   

template | int | номер шаблона контакта, (general в результатах contact.getList) | необязательный, при отсутствии не изменяется   

post | string | Должность |   

email | string | адрес электронной почты |   

phones | string | телефоны |   

phone.number | string | номер телефона |   

phone.typeId | int | идентификатор типа номера | допустимые значения можно получить функцией [contact.getPhoneTypes](ПланФикс_API_contact.getPhoneTypes.md)  

phone.typeName | string | название типа номера |   

secondaryEmails | string | дополнительные адреса email |   

secondaryEmails.email | string | email |   

address | string | Адрес |   

description | string | Дополнительная информация |   

sex | enum | пол | допустимые значения смотри в разделе [пол клиента](../Контакты/ПланФикс_API_Пол_клиента.md)  

site | string | веб-сайт |   

skype | string | skype-контакт |   

facebook | string | facebook |   

vk | string | вконтакте |   

icq | string | номер-icq |   

birthdate | DateTime | дата рождения |   

lang | string | язык: Ru, En |   

canBeWorker | boolean | отображается в списке участников задачи |   

canBeClient | boolean | отображается в списке контрагентов задачи |   

group.id | int | идентификатор группы контактов | допустимые значения можно получить функцией [contact.getGroupList](ПланФикс_API_contact.getGroupList.md)  

customData |  | значения пользовательских полей контакта |   

customData.customValue.id |  | идентификатор пользовательского поля контакта |   

customData.customValue.value |  | значение пользовательского поля контакта | (для полей типа набор задач, список сотрудников, набор записей справочника - идентификаторы через запятую в квадратных скобках)   

responsible |  | корневой элемент списка ответственных |   

responsible .users |  | корневой элемент списка ответственных пользователей |   

responsible .users.id | int | идентификатор пользователя |   

responsible .groups |  | корневой элемент списка групп ответственных |   

responsible .groups.id | int | идентификатор группы |   

telegram.id | int | внутренний идентификатор в Telegram |   

telegram.username | string | username в Telegram |   

  

Результат успешного выполнения функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <contact>

        <id></id>

        <general></general>

      </contact>

      <actionid></actionid>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

contact.id | int | идентификатор обновляемого контакта |   

contact.general | int | номер добавленного контакта |   

actionid | int | идентификатор действия об изменении |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
