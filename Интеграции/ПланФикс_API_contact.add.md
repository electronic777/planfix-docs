Функция добавления контакта. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="contact.add">

      <account></account>

      <sid></sid>

      <contact>

        <template></template>

        <name></name>

        <midName></midName>

        <lastName></lastName>

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

        <isCompany></isCompany>

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

      </contact>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

template | int | номер шаблона контакта, (general в результатах contact.getList) |   

Реализация создания контакта по шаблону в API на текущий момент неполна. Из шаблона устанавливается форма создания контакта (и соответственно имеющиеся в контакте пользовательские поля) и часть её свойств. Из шаблона на текущий момент не устанавливаются: аналитики, файлы, чек-листы, напоминания   

name | string | Имя |   

midName | string | Отчество |   

lastName | string | Фамилия |   

post | string | Должность |   

email | string | адрес электронной почты |   

phones | string | телефоны |   

phone.number | string | номер телефона |   

phone.typeId | int | идентификатор типа номера | допустимые значения можно получить функцией [contact.getPhoneTypes](Интеграции/ПланФикс_API_contact.getPhoneTypes.md)  

phone.typeName | string | название типа номера |   

secondaryEmails | string | дополнительные адреса email |   

secondaryEmails.email | string | email |   

address | string | Адрес |   

description | string | Дополнительная информация |   

sex | enum | пол | допустимые значения смотри в разделе [пол клиента](Контакты/ПланФикс_API_Пол_клиента.md)  

site | string | веб-сайт |   

skype | string | skype-контакт |   

facebook | string | facebook |   

vk | string | вконтакте |   

icq | string | номер-icq |   

birthdate | DateTime | дата рождения |   

lang | string | язык: Ru, En |   

isCompany | boolean | является компанией |   

canBeWorker | boolean | отображается в списке участников задачи |   

canBeClient | boolean | отображается в списке контрагентов задачи |   

group.id | int | идентификатор группы контактов | допустимые значения можно получить функцией [contact.getGroupList](Интеграции/ПланФикс_API_contact.getGroupList.md)  

customData |  | значения пользовательских полей контакта |   

customData.customValue.id |  | идентификатор пользовательского поля контакта | можно получив вызвав contact.get шаблона, по которому создается контакт   

customData.customValue.value |  | значение пользовательского поля контакта | (для полей типа набор задач, список сотрудников, набор записей справочника - идентификаторы через запятую в квадратных скобках)   

responsible |  | корневой элемент списка ответственных |   

responsible .users |  | корневой элемент списка ответственных пользователей |   

responsible .users.id | int | идентификатор пользователя |   

responsible .groups |  | корневой элемент списка групп ответственных |   

responsible .groups.id | int | идентификатор группы |   

signature | string(32) | подпись |   

  

Результат успешного выполнения функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <contact>

        <id></id>

        <userid></userid>

        <general></general>

      </contact>

      <actionid></actionid>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

contact.id | int | идентификатор добавленного контакта |   

contact.userid | int | идентификатор контакта для случаев, когда он используется в системе наравне с сотрудниками (исполнитель задачи и т.п.) |   

contact.general | int | номер добавленного контакта |   

actionid | int | идентификатор действия создания контакта |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
