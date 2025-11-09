Получение списка комментариев с указанной аналитикой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="action.getListWithAnalitic">

      <account></account>

      <sid></sid>

      <analitic>

        <id></id>

      </analitic>

      <task>

        <id></id>

      </task>

      <pageCurrent></pageCurrent>

      <pageSize></pageSize>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

analitic.id | int | идентификатор аналитики | список аналитик можно получить с помощью [ списка доступных аналитик в ПланФикс ](ПланФикс_API_analitic.getList.md)  

task.id | int | если задано значение, то происходит выборка комментариев только из этой задачи | необязательный параметр   

pageCurrent | int | текущая страница |   

pageSize | int | размер запрашиваемой страницы | не может превышать 100   

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
