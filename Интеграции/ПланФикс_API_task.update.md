Функция обновления информации задачи. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="task.update">

      <account></account>

      <sid></sid>

      <silent></silent>

      <task>

        <id></id>

        <general></general>

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

silent | bool | при значении 1 - об изменении не рассылаются уведомления, не создаются действия и записи в логе задачи | обязательно значение 1 при массовых периодических обновлениях задач   

id | int | идентификатор обновляемой задачи |   

general | int | номер задачи (если задан, используется вместо id) |   

title | string | название задачи |   

description | string | о чем задача, описание |   

importance | enum | срочность | перечень допустимых значений смотри в разделе [срочность задач](Задачи/ПланФикс_API_Срочность_задачи.md)  

status | enum/int | статус задачи | Допустимы значения из раздела [Системные статусы задач](Задачи/ПланФикс_API_Системные_статусы_задач.md) или идентификаторы статусов, полученные в результате вызова функции [taskStatus.getListOfSet](Интеграции/ПланФикс_API_taskStatus.getListOfSet.md)  

statusSet | int | процесс задачи | Идентификаторы процессов можно получить в результате вызова функции [taskStatus.getSetList](Интеграции/ПланФикс_API_taskStatus.getSetList.md)  

checkResult | bool | является ли задача задачей с обязательной проверкой результата |   

owner |  | создатель задачи | необязательное поле. Если не указано - берется пользователь от имени которого выполняется функция   

owner.id | int | идентификатор пользователя |   

parent |  | над задача | необязательное поле   

parent.id | int | идентификатор задачи, которая будет являться над задачей | допустимо значение 0 (ноль)   

project |  | в рамках какого проекта поставлена задача |   

project.id | int | идентификатор проекта |   

client |  | контрагент | необязательный параметр   

client.id | int | идентификатор контрагента | допустимо значение 0   

startDateIsSet | bool | задана ли дата начала работы |   

startDate | Date | дата начала работы | в интерфейсе ПланФикс поле _приступить к работе_  

startTimeIsSet | bool | задано ли время начала работы |   

startTime | Time | время начала работы | в интерфейсе ПланФикс поле _приступить к работе_  

endDateIsSet | bool | задана ли дата завершения работы |   

endDate | Date | дата завершения работы | в интерфейсе ПланФикс поле _закончить работу До_  

endTimeIsSet | bool | задано ли время завершения работы |   

endTime | Time | время завершения работы | в интерфейсе ПланФикс поле _закончить работу До_  

isSummary | bool - 0/1 | задача является суммарной |   

durationIsSet | bool - 0/1 | задана ли длительность |   

duration | int | длительность |   

durationUnit | int | 0 - минуты, 1 - часы, 2 - дни |   

workers |  | корневой элемент списка исполнителей задачи |   

workers.users |  | корневой элемент списка пользователей, которым поставлена задача |   

workers.users.id | int | идентификатор пользователя которому поставлена задача |   

workers.groups |  | корневой элемент списка групп, которым поставлена задача |   

workers.groups.id | int | идентификатор группы |   

members |  | корневой элемент списка участников задачи |   

members.users |  | корневой элемент списка участников задачи |   

members.users.id | int | идентификатор участника задачи |   

members.groups |  | корневой элемент списка групп участников |   

members.groups.id | int | идентификатор группы участников |   

auditors |  | корневой элемент списка аудиторов задачи, содержимое аналогично workers и members |   

customData |  | значения пользовательских полей задачи |   

customData.customValue.id |  | идентификатор пользовательского поля задачи |   

customData.customValue.value |  | значение пользовательского поля задачи | (для полей типа набор задач, список сотрудников, набор записей справочника - идентификаторы через запятую в квадратных скобках)   

  

Добавляемые даты могут задаваться в двух форматах. Первый формат короткий, указывается только число, год и месяц. Второй формат - полный, дополнительно указывается время начала/завершения, если того требует задача. 


Не указанные параметры (за исключением **id**) заменяются значениями по умолчанию. В результате выполнения запроса данные задачи обновляются на указанные в запросе. 


Ответ при удачном выполнении функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <task>

        <id></id>

      </task>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор обновляемой задачи |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
