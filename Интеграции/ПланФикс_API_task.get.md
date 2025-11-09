Функция получения карточки задачи. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="task.get">

      <account></account>

      <sid></sid>

      <task>

        <id></id>

        <general></general>

      </task>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор задачи, информацию которой хотим получить |   

general | int | номер задачи (если задан, используется вместо id) |   

signature | string(32) | подпись запроса |   

  

Результат успешного выполнения запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <account></account>

      <sid></sid>

      <task>

        <id></id>

        <title></title>

        <description></description>

        <importance></importance>

        <status></status>

        <checkResult></checkResult>

        <type></type>

        <owner>

          <id></id>

          <name></name>

        </owner>

        <parent>

          <id></id>

        </parent>

        <template>

          <id></id>

        </template>

        <project>

          <id></id>

          <title></title>

        </project>

        <client>

          <id></id>

          <name></name>

        </client>

        <beginDateTime></beginDateTime>

        <startTime></startTime>

        <endTime></endTime>

        <duration></duration>

        <durationUnit></durationUnit>

    

        <general></general>

     

        <isOverdued></isOverdued>

        <isCloseToDeadline></isCloseToDeadline>

        <isNotAcceptedInTime></isNotAcceptedInTime>

        <isSummary></isSummary>

        <starred></starred>

        <additionalDescriptionData></additionalDescriptionData>

    

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

          <groups>

            <group>

              <id></id>

              <name></name>

            </group>

            <!-- ... -->

          </groups>

        </auditors>

        <periodicity>

          <!-- ежедневно -->

          <daily>

            <type></type>

            <shift></shift>

          </daily>

          <!-- еженедельно -->

          <weekly>

            <type></type>

            <shift></shift>

            <days></days>

          </weekly>

          <!-- ежемесячно -->

          <monthly>

            <type></type>

            <month></month>

            <day></day>

            <dayType></dayType>

          </monthly>

    

          <startDate></startDate>

          <endCondition>

            <type></type>

            <date></date>

            <repeatCount></repeatCount>

          </endCondition>

          <notify>

            <type></type>

            <day></day>

          </notify>

        </periodicity>

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

      </task>

      <signature></signature>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор задачи |   

title | string | название задачи |   

description | string | о чем задача, описание |   

importance | enum | срочность | перечень допустимых значений смотри в разделе [срочность задач](Задачи/ПланФикс_API_Срочность_задачи.md)  

status | enum | статус задачи | перечень допустимых значений смотри в разделе [статусы задач](Задачи/ПланФикс_API_Статусы_задач.md)  

statusSet | int | идентификатор процесса задачи |   

checkResult | bool | является ли задача задачей с обязательной проверкой результата |   

type | string | тип задачи: task / template / checklist item |   

owner |  | создатель задачи |   

owner.id | int | идентификатор пользователя |   

owner.name | string | имя пользователя |   

parent |  | надзадача |   

parent.id | int | идентификатор задачи, которая будет являться над задачей | 0 (ноль) - над задача отсутствует   

template |  | шаблон |   

template.id | int | идентификатор шаблона задачи |   

project |  | в рамках какого проекта поставлена задача |   

project.id | int | идентификатор проекта |   

project.title | string | заголовок проекта |   

client |  | контрагент |   

client.id | int | идентификатор контрагента |   

client.name | string | имя контрагента |   

beginDateTime | DateTime | время создания задачи |   

startTime | DateTime | время начала работы | в интерфейсе ПланФикс поле _приступить к работе_  

endTime | DateTime | время окончания задачи | в интерфейсе ПланФикс поле _закончить работу До_  

duration | int | длительность задачи | в интерфейсе ПланФикс поле _Длительность_  

durationUnit | int | 0 - минуты, 1 - часы, 2 - дни |   

general | int | сквозной номер |   

isOverdued | bool | задача не выполнена в срок |   

isCloseToDeadline | bool | задача близка к дедлайну |   

isNotAcceptedInTime | bool | задача не принята вовремя |   

isSummary | bool | задача суммарная |   

starred | bool | помещена в избранные |   

additionalDescriptionData | string | дополнительные данные для задач из соц. сетей, которые отображаются в описании задачи |   

workers |  | корневой элемент списка исполнителей задачи |   

workers.users |  | корневой элемент списка пользователей, которым поставлена задача |   

workers.users.user | node | пользователь |   

workers.users.user.id | int | идентификатор пользователя, которому поставлена задача |   

workers.users.user.name | string | имя пользователя |   

workers.groups |  | корневой элемент списка групп, которым поставлена задача |   

workers.groups.group | node | группа |   

workers.groups.group.id | int | идентификатор группы |   

workers.groups.group.name | string | название группы |   

members |  | корневой элемент списка участников задачи, содержимое аналогично списку workers |   

auditors |  | корневой элемент списка аудиторов задачи, содержимое аналогично списку workers |   

periodicity | node | задает периодичность выполнения задачи | смотри описание структуры узлов _daily_ , _weekly_ и _monthly_ ниже; отсутствие параметра, говорит о том что периодичность отсутствует   

periodicity.startDate | DateTime | начиная с этой даты начинает работать повторение задачи |   

periodicity.endCondition |  | условия окончания повторения |   

periodicity.endCondition.type | enum | условие окончания | допустимые значения: **ENDLESS** \- нет конечной даты, **BYCOUNT** \- После _repeatCount_ повторений, **BYENDDATE** \- до даты определенной в **date**  

periodicity.endCondition.date | DateTime | дата, после которой повторение задачи перестает работать | используется при type=BYENDDATE   

periodicity.endCondition.repeatCount | int | количество повторений, после которого задача перестает повторяться | используется при type=BYCOUNT   

periodicity.notify |  | уведомления |   

periodicity.notify.type | int | тип период, 0 - рабочий день, 1 - неделя |   

periodicity.notify.day | int | размер период | если type=0 и day=2, то уведомление прийдет за 2 рабочих дня до начала задачи   

customData |  | значения пользовательских полей задачи |   

customData.customValue.field.id |  | идентификатор пользовательского поля |   

customData.customValue.field.name |  | название пользовательского поля |   

customData.customValue.value |  | значение пользовательского поля |   

customData.customValue.text |  | текстовое значение пользовательского поля |   

  

Периодичность - не обязательный параметр. Внутри тега **periodicity** может быть только один из перечисленных элементов: _daily_ , _weekly_ , _monthly_. 


### описание параметра periodicity


Описание параметра _daily_ , параметры _weekly_ и _monthly_ в этом случае не могут быть заданы. Указывает что задача должна повторяться ежедневно, согласно установленным критериям: 


Название | Тип | Значение | Примечание   

---|---|---|---  

type | enum | определяет периодичность | допустимые значения EVERY или EVERY_WORKING, или AFTER_COMPLETE   

shift | int | определяет сдвиг в днях | используется только при значениях type равным EVERY или AFTER_COMPLETE   

  

Значение EVERY интерпретируется как каждый N-й день, заданный в параметре **shift**. EVERY_WORKING - каждый рабочий день. Значение AFTER_COMPLETE интерпретируется как ставить новую задачу через N-й день после каждого завершения, заданный в параметре **shift**. 


Описание параметра _weekly_ , параметры _daily_ и _monthly_ в этом случае не могут быть заданы. Указывает что задача должна повторяться еженедельно, согласно установленным критериям: 


Название | Тип | Значение | Примечание   

---|---|---|---  

type | enum | определяет периодичность | допустимые значения EVERY или AFTER_COMPLETE   

shift | int | сдвиг в неделях |   

days | set/list | перечень дней недели, разделитель символ запятой (,). понедельник имеет индекс 1, воскресение - 7. | используется только при type=EVERY   

  

Значение AFTER_COMPLETE интерпретируется как: ставить задачу через N-й неделю после каждого завершения, заданную в параметре **shift**. 


Описание параметра _monthly_ , параметры _daily_ и _weekly_ в этом случае не могут быть заданы. Указывает что задача должна повторяться ежемесяно, согласно установленным критериям: 


Название | Тип | Значение | Примечание   

---|---|---|---  

type | enum | периодичность | допустимые значения AFTER_COMPLETE или EVERY, или EXACT   

month | int | задает месяц в/через который должно действие/задача повторяться |   

day | int | задает день в/через который должна задача повторяться | не используется при type=AFTER_COMPLETE   

dayType | enum | определяет тип дня | используется при type=EXACT. Допустимые значения смотри в разделе [тип дня для повторяющейся задачи](Задачи/ПланФикс_API_Тип_дня_для_повторяющейся_задачи.md)  

  

EXACT - ежемесячно в **day** день **dayType** каждого **month** месяца;  

EVERY - ежемесячно повторять **day** числа каждого **month** месяца;  

AFTER_COMPLETE - ежемесячно ставить новую задачу через **month** месяц после каждого завершения.  


В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
