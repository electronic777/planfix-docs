Функция позволяет удалить комментарий. Её выполнение требует наличие соответствующих прав. Также не может быть удален комментарий, которым менялся статус задачи. 


Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="action.delete">

      <account></account>

      <sid></sid>

      <action>

        <id></id>

      </action>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор комментария |   

signature | string(32) | подпись |   

  

  

Результат успешного выполнения функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <action>

        <id></id>

      </action>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор комментария |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
