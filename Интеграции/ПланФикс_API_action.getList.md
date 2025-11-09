Получение списка комментариев в задаче: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="action.getList">

      <account></account>

      <sid></sid>

      <task>

        <id></id>

        <general></general>

      </task>

      <contact>

        <general></general>

      </contact>

      <pageCurrent></pageCurrent>

      <pageSize></pageSize>

      <sort></sort>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

task (contact) |  | задача/контакт, из которого получаем комментарии — должен присутствовать только один узел (или task или contact) |   

task.id | int | идентификатор задачи |   

task.general | int | номер задачи (если задан, используется вместо id) |   

contact.general | int | номер контакта |   

pageCurrent | int | текущая страница |   

pageSize | int | размер запрашиваемой страницы | не может превышать 100   

sort | enum: {asc,desc} | сортировка списка | необязательный параметр, по умолчанию desc   

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

**actions** totalCount | int | количество комментариев удовлетворяющих запросу |   

action |  | комментарий, описание параметра смотри в разделе [ Получить комментарий](ПланФикс_API_action.get.md) |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
