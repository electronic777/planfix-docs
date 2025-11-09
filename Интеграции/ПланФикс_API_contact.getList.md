Функция получения списка контактов. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="contact.getList">

      <account></account>

      <sid></sid>

      <pageCurrent></pageCurrent>

      <pageSize></pageSize>

      <target></target>

      <company></company>

      <search></search>

      <filters>

        <filter>

          <type></type>

          <operator></operator>

          <value></value>

          <field></field>

          ...

        </filter>

        ...

      </filters>

      <fields>

        <field>lastUpdateDate</field>

        ...

      </fields>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

pageCurrent | int | запрашиваемая страница |   

pageSize | int | размер запрашиваемого списка |   

target | enum / int | контакты, компании или заданный фильтр задач | допустимые значения смотри ниже   

company | int | идентификатор компании, контакты которой надо выбрать | необязательный, при отсутствии узла - выборка не ограничивается одной компанией   

search | string | строка для поиска контактов, если задана будут возвращены контакты, в которых данная строка встречается в имени, фамилии или email |   

filters |  | дополнительные сложные фильтры | перечень и формат допустимых значений смотри в разделе [фильтры контактов](../Контакты/ПланФикс_API_Фильтры_контактов.md)  

fields |  | получить дополнительные поля |   

fields.field | string | поле, возможные значения: 


  * **lastUpdateDate** \- дата последнего изменения

  * **lastCommentDate** \- дата последнего комментария


| одноименное поле будет добавлено в ответ в узел contact   

signature | string(32) | подпись |   

  

### Допустимые значения параметра target


Значение | Описание | Примечание   

---|---|---  

contact | контакты | значение по умолчанию   

company | компании |   

template | шаблоны |   

идентификатор фильтра контактов | доступные фильтры можно получить функцией [contact.getFilterList](ПланФикс_API_contact.getFilterList.md) |   

  

Результат успешного выполнения запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <contacts count="count" totalCount="totalCount">

        <contact>

          <id></id>

          <userid></userid>

          <general></general>

          <template>

            <id></id>

          </template>

          <name></name>

          <lastName></lastName>

          <isCompany></isCompany>

          <post></post>

          <email></email>

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

          <skype></skype>

          <facebook></facebook>

          <vk></vk>

          <telegramId></telegramId>

          <icq></icq>

          <userPic></userPic>

          <birthdate></birthdate>

          <havePlanfixAccess>{true|false}</havePlanfixAccess>

          <user>

            <login></login>

            <role></role>

            <status></status>

            <email></email>

          </user>

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

        </contact>

        <!-- ... -->

      </contacts>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**contacts** |  | список контактов |   

**contacts** count | int | количество контактов в списке |   

**contacts** totalCount | int | количество контактов удовлетворяющих условию запроса |   

contact |  | узел, описывающий контакт |   

id | int | идентификатор контакта |   

userid | int | идентификатор контакта для случаев, когда он используется в системе наравне с сотрудниками (исполнитель задачи и т.п., а также пользовательское поле типа контакт) |   

general | int | номер контакта |   

template.id | int | номер шаблона контакта |   

name | string | Имя Отчество |   

lastName | string | Фамилия |   

isCompany | boolean | Является компанией |   

post | string | Должность |   

email | string | адрес электронной почты |   

phones |  | список телефонов |   

phones.phone.number | string | номер телефона |   

phones.phone.typeId | int | идентификатор типа номера телефона |   

phones.phone.typeName | string | название типа номера телефона |   

address | string | Адрес |   

description | string | Дополнительная информация |   

sex | enum | пол | допустимые значения смотри в разделе [пол клиента](../Контакты/ПланФикс_API_Пол_клиента.md)  

skype | string | skype-контакт |   

facebook | string | facebook |   

vk | string | vk |   

telegramId | string | telegramId |   

icq | string | номер-icq |   

userPic | string | ссылка на изображение |   

birthdate | DateTime | дата рождения |   

signature | string(32) | подпись |   

contractors |  | список контрагентов, к которым он относится |   

contractors.client |  | описание контрагента |   

contractors.client.id | int | идентификатор клиента/контрагента |   

contractors.client.name | string | имя/название контрагента |   

havePlanfixAccess | bool | имеет ли контакт доступ к ПланФикс | данный параметр возвращается только пользователю с правами администратор   

user |  | учетные данные контакта | данный параметр возвращается только пользователю с правами администратор   

user.login | string | логин в системе |   

user.role | string | роль |   

user.status | enum | статус |   

user.email | string | адрес электронной почты |   

customData |  | значения пользовательских полей задачи |   

customData.customValue.field.id |  | идентификатор пользовательского поля |   

customData.customValue.field.name |  | название пользовательского поля |   

customData.customValue.value |  | значение пользовательского поля |   

customData.customValue.text |  | текстовое значение пользовательского поля |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
