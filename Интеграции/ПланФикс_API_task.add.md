Функция позволяет создать новую задачу. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="task.add">

      <account></account>

      <sid></sid>

      <task>

        <template></template>

        <title></title>

        <description></description>

        <importance></importance>

        <status></status>

        <statusSet></statusSet>

        <checkResult></checkResult>

        <owner>

          <id></id>

        </owner>

        <parent>

          <id></id>

        </parent>

        <project>

          <id></id>

        </project>

        <client>

          <id></id>

        </client>

        <beginDateTime></beginDateTime>

        <startDateIsSet></startDateIsSet>

        <startDate></startDate>

        <startTimeIsSet></startTimeIsSet>

        <startTime></startTime>

        <endDateIsSet></endDateIsSet>

        <endDate></endDate>

        <endTimeIsSet></endTimeIsSet>

        <endTime></endTime>

        <isSummary></isSummary>

        <duration></duration>

        <durationUnit></durationUnit>

        <durationIsSet></durationIsSet>

        <workers>

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

        </workers>    

        <members>

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

        </members>      

        <auditors>

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

        </auditors>

        <customData>

          <customValue>

            <id></id>

            <value></value>

          </customValue>

          <!-- ... -->

        </customData>

      </task>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

template | id | идентификатор шаблона задачи | id в ответе [task.getList](Интеграции/ПланФикс_API_task.getList.md) с target = template   

Реализация создания задачи по шаблону в API на текущий момент неполна. Из шаблона устанавливается форма создания задачи (и соответственно имеющиеся в задаче пользовательские поля) и часть её свойств. Из шаблона на текущий момент не устанавливаются: сроки задачи, аудиторы, аналитики, файлы, напоминания, чек-листы. Исполнители и участники устанавливаются из шаблона, если они отсутствуют в запросе.   

title | string | название задачи |   

description | string | о чем задача, описание |   

importance | enum | срочность | перечень допустимых значений смотри в разделе [срочность задач](Задачи/ПланФикс_API_Срочность_задачи.md)  

status | enum/int | статус задачи | Допустимы значения из раздела [Системные статусы задач](Задачи/ПланФикс_API_Системные_статусы_задач.md) или идентификаторы статусов, полученные в результате вызова функции [taskStatus.getListOfSet](Интеграции/ПланФикс_API_taskStatus.getListOfSet.md)  

statusSet | int | процесс задачи | Идентификаторы процессов можно получить в результате вызова функции [taskStatus.getSetList](Интеграции/ПланФикс_API_taskStatus.getSetList.md)  

checkResult | bool | является ли задача задачей с обязательной проверкой результата |   

owner |  | создатель задачи | необязательное поле. Если не указано - берется пользователь от имени которого выполняется функция   

owner.id | int | идентификатор пользователя | если это контакт - нужно использовать userid из ответа [contact.get](Интеграции/ПланФикс_API_contact.get.md)  

parent |  | над задача | необязательное поле   

parent.id | int | идентификатор задачи, которая будет являться над задачей | допустимо значение 0 (ноль)   

project |  | в рамках какого проекта поставлена задача |   

project.id | int | идентификатор проекта |   

client |  | контрагент | необязательный параметр   

client.id | int | идентификатор контрагента (id из ответа contact.get) | допустимо значение 0   

beginDateTime | DateTime | дата/время создания - не обязательный, по-умолчанию текущие | может заполняться, только если авторизация была сделана под сотрудником с правами администратора   

startDateIsSet | bool (0/1) | задана ли дата начала работы |   

startDate | Date | дата начала работы | в интерфейсе ПланФикс поле _приступить к работе_  

startTimeIsSet | bool (0/1) | задано ли время начала работы |   

startTime | Time | время начала работы | в интерфейсе ПланФикс поле _приступить к работе_  

endDateIsSet | bool (0/1) | задана ли дата завершения работы |   

endDate | Date | дата завершения работы | в интерфейсе ПланФикс поле _закончить работу До_  

endTimeIsSet | bool (0/1) | задано ли время завершения работы |   

endTime | Time | время завершения работы | в интерфейсе ПланФикс поле _закончить работу До_  

isSummary | bool (0/1) | задача является суммарной |   

durationIsSet | bool | задана ли длительность |   

duration | int | длительность |   

durationUnit | int | 0 - минуты, 1 - часы, 2 - дни |   

workers |  | корневой элемент списка исполнителей задачи |   

workers.users |  | корневой элемент списка пользователей, которым поставлена задача |   

workers.users.id | int | идентификатор пользователя которому поставлена задача | для контактов - нужно использовать userid из ответа [contact.get](Интеграции/ПланФикс_API_contact.get.md)  

workers.groups |  | корневой элемент списка групп, которым поставлена задача |   

workers.groups.id | int | идентификатор группы |   

members |  | корневой элемент списка участников задачи |   

members.users |  | корневой элемент списка участников задачи |   

members.users.id | int | идентификатор участника задачи | для контактов - нужно использовать userid из ответа [contact.get](Интеграции/ПланФикс_API_contact.get.md)  

members.groups |  | корневой элемент списка групп участников |   

members.groups.id | int | идентификатор группы участников |   

auditors |  | корневой элемент списка аудиторов задачи, содержимое аналогично workers и members |   

customData |  | значения пользовательских полей задачи |   

customData.customValue.id |  | идентификатор пользовательского поля задачи |   

customData.customValue.value |  | значение пользовательского поля задачи | (для полей типа набор задач, список сотрудников, набор записей справочника - идентификаторы через запятую в квадратных скобках)   

  

Добавляемые даты могут задаваться в двух форматах. Первый формат короткий, указывается только число, год и месяц. Второй формат - полный, дополнительно указывается время начала/завершения, если того требует задача. 


Ответ при удачном выполнении операции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <task>

        <id></id>

        <general></general>

      </task>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор созданной задачи |   

task.general | int | сквозной номер созданной задачи |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
