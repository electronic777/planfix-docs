Позволяет получить количество добавленных пользователем действий за заданный период. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="user.actionsAdded">

      <account></account>

      <sid></sid>

      <user>

        <id></id>

      </user>

      <period>

        <begin></begin>

        <end></end>

      </period>

      <actionType></actionType>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

user.id | int | идентификатор пользователя |   

period.begin | DateTime | дата начала периода |   

period.end | DateTime | дата конца периода |   

actionType | enum | тип действия, необязательный параметр | список возможных значений смотри в разделе [типы действий](../Автоматизация/ПланФикс_API_Список_типов_действий.md)  

signature | string(32) | подпись |   

  

В ответе будет передано количество действий указанного типа (либо же любого типа), добавленных пользователем в заданный период. 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <count></count>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

count | int | количество действий |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
