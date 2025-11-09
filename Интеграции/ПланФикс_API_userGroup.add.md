Функция создания группы. Функция доступна пользователю с правами администратор. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="userGroup.add">

      <account></account>

      <sid></sid>

      <userGroup>

        <name></name>

      </userGroup>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

userGroup.name | string | название создаваемой группы пользователей |   

signature | string(32) | подпись |   

  

Ответ при удачном создании группы: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <userGroup>

        <id></id>

      </userGroup>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

userGroup.id | int | идентификатор созданной группы |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
