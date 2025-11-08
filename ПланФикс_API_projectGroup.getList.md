Функция для получения списка групп проектов. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="projectGroup.getList">

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

      <projectGroups totalCount="totalCount">

        <projectGroup>

          <id></id>

          <name></name>

        </projectGroup>

        <!-- ... -->

      </projectGroups>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**projectGroups** |  | корневой элемент, содержит список групп проектов |   

**projectGroups** totalCount | int | количество групп проектов |   

projectGroup |  | корневой элемент, описывающий группу проектов в списке |   

id | int | идентификатор группы проектов |   

name | string | название группы проектов |   

  

Пустой ответ не **генерирует ошибку**. Если в результирующую выборку не попадают никакие группы проектов, то ответ будет иметь следующую форму: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <projectGroups totalCount="0"></projectGroups>

    </response>


В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
