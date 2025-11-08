Функция для получения списка процессов задач. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="taskStatus.getSetList">

      <account></account>

      <sid></sid>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

signature | string(32) | подпись |   

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <taskStatusSets totalCount="totalCount">

        <taskStatusSet>

          <id></id>

          <name></name>

        </taskStatusSet>

        <!-- ... -->

      </taskStatusSets>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**taskStatusSets** |  | корневой элемент, содержит список процессов задач |   

**taskStatusSets** totalCount | int | количество процессов задач |   

taskStatusSet |  | корневой элемент, описывающий процесс в списке |   

id | int | идентификатор процесса |   

name | string | название процесса |   

  

Пустой ответ не **генерирует ошибку**. Если в результирующую выборку не попадают никакие процессы, то ответ будет иметь следующую форму: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <taskStatusSets totalCount="0"></taskStatusSets>

    </response>


В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
