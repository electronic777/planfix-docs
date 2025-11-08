Функция обновление информации о группе. Доступна только для пользователя с правами администратора. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="userGroup.update">

      <account></account>

      <sid></sid>

      <userGroup>

        <id></id>

        <name></name>

      </userGroup>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор обновляемой группы |   

name | string | новое название группы |   

signature | string(32) | подпись |   

  

Ответ при удачном выполнении функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <userGroup>

        <id></id>

      </userGroup>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

userGroup.id | int | идентификатор обновляемой группы |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
