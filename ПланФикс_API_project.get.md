Функция позволяет получить информацию о проекте. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="project.get">

      <account></account>

      <sid></sid>

      <project>

        <id></id>

        <general></general>

      </project>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

project.id | int | идентификатор запрашиваемого проекта |   

project.general | int | номер проекта | используется при отсутствии параметра id   

signature | string(32) | подпись |   

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <project>

        <id></id>

        <title></title>

        <description></description>

        <owner>

          <id></id>

          <name></name>

        </owner>

        <client>

          <id></id>

          <name></name>

        </client>

        <group>

          <id></id>

          <name></name>

        </group>

        <parent>

          <id></id>

        </parent>

        <template>

          <id></id>

        </template>

        <status></status>

        <hidden></hidden>

        <hasEndDate></hasEndDate>

        <endDate></endDate>

        <beginDate></beginDate>

        <taskCount></taskCount>

        <isOverdued></isOverdued>

        <isCloseToDeadline></isCloseToDeadline>

    

        <workers>

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

        </workers>

        <members>

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

        </members>

        <auditors>

          <users>

            <user>

              <id></id>

              <name></name>

            </user>

            <!-- ... -->

          </users>

        </auditors>

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

      </project>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор проекта |   

title | string | название проекта |   

description | string | описание проекта |   

owner |  | создатель/владелец проекта |   

owner.id | int | идентификатор пользователя создавшего проект |   

owner.name | string | имя пользователя создавшего проект |   

client |  | контрагент |   

client.id | int | идентификатор контрагента |   

client.name | string | имя контрагента |   

group |  | группа проектов |   

group.id | int | идентификатор группы проектов |   

group.name | string | название группы проектов |   

parent |  | надпроект |   

parent.id | int | идентификатор надпроекта |   

template |  | шаблон |   

template.id | int | идентификатор шаблона |   

status | enum | статус проекта | перечень допустимых значений для данного поля смотри в разделе [статусы проектов](ПланФикс_API_Статусы_проектов.md "ПланФикс API:Статусы проектов")  

hidden | bool | скрытый ли проект | отображается ли он в общем списке   

hasEndDate | bool | true/false - имеет ли проект дату завершения |   

endDate | DateTime | дата завершения проекта | имеет значение только если установлен флаг **hasEndDate**  

beginDate | DateTime | дата создания проекта |   

taskCount | int | количество задач в проекте |   

isOverdued | bool | true/false - является ли проект просроченным |   

isCloseToDeadline | bool | true/false | осталось 25% времени до завершения или прошло 75% отведенного времени на выполнение его   

workers |  | корневой элемент списка исполнителей по умолчанию проекта |   

workers.users |  | корневой элемент списка пользователей из числа исполнителей по умолчанию проекта |   

workers.users.user | node | пользователь |   

workers.users.user.id | int | идентификатор пользователя из числа исполнителей по умолчанию проекта |   

workers.users.user.name | string | имя пользователя |   

workers.groups |  | корневой элемент списка групп из числа исполнителей по умолчанию проекта |   

workers.groups.group | node | группа |   

workers.groups.group.id | int | идентификатор группы |   

workers.groups.group.name | string | название группы |   

members |  | корневой элемент списка участников по умолчанию проекта |   

auditors |  | корневой элемент списка аудиторов проекта |   

customData |  | значения пользовательских полей проекта |   

customData.customValue.field.id |  | идентификатор пользовательского поля |   

customData.customValue.field.name |  | название пользовательского поля |   

customData.customValue.value |  | значение пользовательского поля |   

customData.customValue.text |  | текстовое значение пользовательского поля |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
