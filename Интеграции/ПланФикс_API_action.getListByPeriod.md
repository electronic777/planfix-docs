Получение списка всех комментариев за заданный период времени: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="action.getListByPeriod">

      <account></account>

      <sid></sid>

      <fromDate></fromDate>

      <toDate></toDate>

      <pageCurrent></pageCurrent>

      <pageSize></pageSize>

      <sort></sort>

      <task>

        <id></id>

      </task>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

fromDate | DateTime | начало периода |   

toDate | DateTime | конец периода |   

pageCurrent | int | текущая страница |   

pageSize | int | размер запрашиваемой страницы | не может превышать 100   

sort | enum: {asc,desc} | сортировка списка | необязательный параметр, по умолчанию desc   

task.id | int | идентификатор задачи | необязательный параметр, по умолчанию выбираются комментарии по всем задачам   

signature | string(32) | подпись |   

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <actions count="count" totalCount="totalCount">

        <action><!-- ... --></action>

        <action><!-- ... --></action>

        <!-- ... -->

      </actions>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**actions** |  | корневой узел содержащий список комментариев |   

**actions** count | int | количество комментариев в ответе |   

**actions** totalCount | int | количество комментариев, удовлетворяющих запросу |   

action |  | комментарий, описание параметра смотри в разделе [ Получить комментарий](ПланФикс_API_action.get.md) |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
