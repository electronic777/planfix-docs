Функция получения информации о группе. Формат вызова: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="userGroup.get">

      <account></account>

      <sid></sid>

      <userGroup>

        <id></id>

      </userGroup>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор группы |   

signature | string(32) | подпись |   

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <userGroup>

        <id></id>

        <name></name>

        <userCount></userCount>

      </userGroup>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор группы |   

name | string | название группы |   

userCount | int | количество пользователей в группе |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
