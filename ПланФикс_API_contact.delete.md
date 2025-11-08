Функция позволяет удалить контакт. Выполнение этой функции требует наличие соответствующих прав. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="contact.delete">

      <account></account>

      <sid></sid>

      <contact>

        <id></id>

        <userid></userid>

        <general></general>

      </contact>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор контакта |   

signature | string(32) | подпись |   

  

  

Результат успешного выполнения функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <contact>

        <id></id>

      </contact>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор контакта |   

userid | int | идентификатор контакта для случаев, когда он используется в системе наравне с сотрудниками (исполнитель задачи и т.п., а также пользовательское поле типа контакт) |   

general | int | номер контакта |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
