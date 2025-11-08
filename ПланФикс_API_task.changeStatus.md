Изменение статуса задачи. Формат вызова функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="task.changeStatus">

      <account></account>

      <sid></sid>

      <task>

        <id></id>

        <general></general>

      </task>

      <status></status>

      <dateTime></dateTime>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор задачи |   

general | int | номер задачи (если задан, используется вместо id) |   

status | enum | новый статус задачи | Допустимы значения из раздела [Системные статусы задач](ПланФикс_API_Системные_статусы_задач.md "ПланФикс API:Системные статусы задач") или идентификаторы статусов, полученные в результате вызова функции [taskStatus.getListOfSet](ПланФикс_API_taskStatus.getListOfSet.md "ПланФикс API taskStatus.getListOfSet"). Недопустимое значение параметра: **REJECTED** (отклонить можно специальной функцией)   

dateTime | DateTime | дата активации при переводе в статус _Отложенная_ | обязательное поле для статуса **DELAYED**  

signature | string(32) | подпись |   

  

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <task>

        <id></id>

      </task>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор задачи, у которой поменян статус |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
