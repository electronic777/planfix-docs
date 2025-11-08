Изменить принадлежность пользователя к группе. Вызывать имеет право пользователь с правами администратор. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="user.updateGroupMembership ">

      <account></account>

      <sid></sid>

      <user>

        <id></id>

        <addUserGroup>

          <id></id>

          <id></id>

          <!-- ... -->

        </addUserGroup>

    

        <delUserGroup>

          <id></id>

          <id></id>

          <!-- ... -->

        </delUserGroup>

      </user>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

user.id | int | идентификатор пользователя |   

user.addUserGroup |  | список групп к которым присоединяется пользователь |   

user.addUserGroup.id | int | идентификатор группы |   

user.delUserGroup |  | список групп от которых пользователь отсоединяется |   

user.delUserGroup.id | int | идентификатор группы |   

  

  

Ответ, при успешном выполнении запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <user>

        <id></id>

      </user>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

user.id | int | идентификатор пользователя |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
