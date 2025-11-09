Функция получения множества карточек задач. Позволяет получить данные до 100 задач за запрос. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="task.getMulti">

      <account></account>

      <sid></sid>

      <tasks>

        <id></id>

        <id></id>

        <general></general>

        <general></general>

        <!-- ... -->

      </tasks>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

tasks.id | int | идентификаторы задач, информацию о которых хотим получить |   

tasks.general | int | номера задач, информацию о которых хотим получить |   

signature | string(32) | подпись запроса |   

  

В случае удачного выполнения функции будет получен ответ следующего вида: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <tasks count="count">

        <task>

          <id></id>

          <!-- ... -->

        </task>

        <!-- ... -->

      </tasks>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**tasks** |  | корневой элемент, содержит список задач |   

**tasks** count | int | количество задач возвращенных в результате выполнения функции |   

task |  | задача | описание данного параметра смотрите в секции [ответ на получении карточки задачи](ПланФикс_API_task.get.md)  

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
