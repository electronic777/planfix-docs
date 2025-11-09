Функция для получения списка проектов. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="project.getList">

      <account></account>

      <sid></sid>

      <user>

        <id></id>

      </user>

      <target></target>

      <status></status>

      <sortType></sortType>

      <pageCurrent></pageCurrent>

      <pageSize></pageSize>

      <client>

        <id></id>

      </client>

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

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

user |  | пользователь ПланФикса | не обязательный параметр. задается для того чтоб посмотреть проекты в которых принимает участие указанный пользователь. этот параметр должен задаваться только в том случае, если выполняется запрос от учетной записи с админ правами   

user.id | int | идентификатор пользователя |   

target | enum | фильтр по вкладкам | не обязательный параметр. список допустимых значений смотри в разделе [фильтр вкладки для проектов](Проекты/ПланФикс_API_Фильтр_вкладки_для_проектов.md)  

status | enum | фильтр по статусу | не обязательный параметр. перечень допустимых значений для данного поля смотри в разделе [статусы проектов](Задачи/ПланФикс_API_Статусы_проектов.md)  

sortType | enum | тип сортировки | не обязательный параметр. список допустимых значений смотри в разделе [типы сортировок для проектов](Проекты/ПланФикс_API_Типы_сортировок_для_проектов.md)  

pageCurrent | int | постраничная навигация | не обязательный параметр. значение меньше 1 или отсутствие этого параметра будут инициировать процедуру подсчета количества элементов.   

pageSize | int | количество выдаваемых значений в результате. не может превышать значение **100** | не обязательный параметр. если будет опущен, возьмется значение по умолчанию.   

client |  |  | не обязательный параметр   

client.id | int | идентификатор контрагента, выступает в качестве фильтра |   

filters |  | дополнительные сложные фильтры | перечень и формат допустимых значений смотри в разделе [фильтры проектов](Проекты/ПланФикс_API_Фильтры_проектов.md)  

signature | string(32) | подпись |   

  

Все параметры, за исключением **account** , **sid** , **signature** не являются обязательными. Если опустить параметр **user** , то будет получен список проектов доступных для текущего пользователя, необходимо помнить что только администраторы могут смотреть проекты других участников. 


Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <projects count="count" totalCount="totalCount">

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

        <!-- ... -->

      </projects>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**projects** |  | корневой элемент, содержит список проектов |   

**projects** count | int | количество узлов/проектов возвращенных в результате выполнения запроса |   

**projects** totalCount | int | количество проектов удовлетворяющих запросу |   

project |  | корневой элемент, описывающий проект в списке |   

id | int | идентификатор проекта |   

title | string | название проекта |   

description | string | описание проекта |   

owner |  | владелец/создатель проекта |   

owner.id | int | идентификатор пользователя |   

owner.name | string | имя пользователя, создавшего проект |   

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

status | enum | статус в котором находится сейчас проект | перечень допустимых значений для данного поля смотри в разделе [статусы проектов](Задачи/ПланФикс_API_Статусы_проектов.md)  

hidden | bool | скрытый |   

hasEndDate | bool | признак того, что для проекта установлена дата окончания |   

endDate | DateTime | дата окончания проекта | установлена, только при **hasEndDate** = _true_  

beginDate | DateTime | дата создания проекта |   

taskCount | int | количество задач в проекте |   

isOverdued | bool | признак того, что проект просрочен |   

isCloseToDeadline | bool | осталось 25% времени до завершения или прошло 75% отведенного времени на выполнение его |   

customData |  | значения пользовательских полей задачи |   

customData.customValue.field.id |  | идентификатор пользовательского поля |   

customData.customValue.field.name |  | название пользовательского поля |   

customData.customValue.value |  | значение пользовательского поля |   

customData.customValue.text |  | текстовое значение пользовательского поля |   

  

Атрибут **totalCount** у элемента **projects** показывает сколько всего может быть возвращено данным запросом проектов. Это позволяет избежать дополнительный запрос на полный подсчет количества проектов. Если требуется узнать только количество элементов, достаточно послать запрос с параметром **pageCurrent** =0. 


Пустой ответ не **генерирует ошибку**. Если в результирующую выборку не попадают никакие проекты, то ответ будет иметь следующую форму: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <projects count="0" totalCount="0"></projects>

    </response>


В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
