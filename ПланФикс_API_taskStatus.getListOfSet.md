Функция для получения списка статусов процесса. Возвращает все статусы, которые присутствуют в наборе статусов процесса. Для получения статусов в который можно перевести задачу в данный момент существует функция [task.getPossibleStatusToChange](ПланФикс_API_task.getPossibleStatusToChange.md "ПланФикс API task.getPossibleStatusToChange")


Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="taskStatus.getListOfSet">

      <account></account>

      <sid></sid>

      <taskStatusSet>

         <id></id>

      </taskStatusSet>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

taskStatusSet.id | int | Идентификатор процесса |   

signature | string(32) | подпись |   

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <taskStatuses totalCount="totalCount">

        <taskStatus>

          <id></id>

          <name></name>

          <color></color>

          <isActive></isActive>

          <hasDeadline></hasDeadline>

          <texts>

            <text>

              <lang></lang>

              <name></name>

            </text>

            <!-- ... -->

          </texts>

        </taskStatus>

        <!-- ... -->

      </taskStatuses>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**taskStatuses** |  | корневой элемент, содержит список статусов задач |   

**taskStatuses** totalCount | int | количество статусов в наборе процесса |   

taskStatus |  | корневой элемент, описывающий статус задачи |   

id | int | идентификатор статуса задачи |   

name | string | название статуса задачи |   

color | string | цвет |   

isActive | boolean | статус активен (1) или неактивен (0) |   

hasDeadline | boolean | отслеживаются (1) или не отслеживаются (0) сроки задач в этом статусе, если сроки в данном статусе отслеживаются и задача находится в данном статусе после даты планируемого завершения, она становится просроченной |   

texts |  | информация на доступных языках |   

text.lang | string | обозначение языка (на текущий момент Ru/En) |   

text.name | string | название статуса на этом языке |   

  

Пустой ответ не **генерирует ошибку**. Если в результирующую выборку не попадают никакие статусы задач, то ответ будет иметь следующую форму: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <taskStatuses totalCount="0"></taskStatuses>

    </response>


В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
