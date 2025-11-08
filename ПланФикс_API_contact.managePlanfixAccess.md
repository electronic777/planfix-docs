Функция позволяет разрешить или запретить доступ для контакта. Выполнение этой функции требует наличие админ прав. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="contact.managePlanfixAccess">

      <account></account>

      <sid></sid>

      <contact>

        <id></id>

        <userid></userid>

        <general></general>

        <email></email>

        <havePlanfixAccess></havePlanfixAccess>

      </contact>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор контакта |   

userid | int | идентификатор контакта для случаев, когда он используется в системе наравне с сотрудниками (исполнитель задачи и т.п., а также пользовательское поле типа контакт) |   

general | int | номер контакта |   

email | string | использовать указанный e-mail для организации доступа в ПланФикс | не обязательный параметр, используется только в первый раз, при открытии доступа к ПланФик'су   

havePlanfixAccess | bool | запретить (0) или открыть(1) доступ к ПланФикс |   

signature | string(32) | подпись |   

  

  

Результат успешного выполнения функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <contact>

        <id></id>

        <status></status>

      </contact>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор контакта |   

status | enum | результат выполнения операции | список допустимых значений смотри в разделе [результат выполнения contact.managePlanfixAccess](ПланФикс_API_Результат_выполнения_contact.managePlanfixAccess.md "ПланФикс API:Результат выполнения contact.managePlanfixAccess")  

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
