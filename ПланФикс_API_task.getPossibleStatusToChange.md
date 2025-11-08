Функция позволяет получить список доступных статусов для функции [task.changeStatus](ПланФикс_API_task.changeStatus.md "ПланФикс API task.changeStatus"). Формат вызова функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="task.getPossibleStatusToChange">

      <account></account>

      <sid></sid>

      <task>

        <id></id>

      </task>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор задачи |   

signature | string(32) | подпись |   

  

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <statusList totalCount="x">

        <status>

          <title></title>

          <value></value>

        </status>

        <status>

          <title></title>

          <value></value>

        </status>

        <!-- -->

      </statusList>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**statusList** |  | список статусов |   

**statusList** totalCount | int | количество элементов в списке |   

status |  | корневой элемент описывающий статус |   

status.value | enum | значение | список принимаемых значений в разделе [статусы задач](ПланФикс_API_Статусы_задач.md "ПланФикс API:Статусы задач")  

status.title | string | текстовое представление статуса |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
