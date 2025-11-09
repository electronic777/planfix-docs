Функция получения списка руководителей группы. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="userGroup.getHeads">

      <account></account>

      <sid></sid>

      <userGroup>

        <id></id>

      </userGroup>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

userGroup.id | int | идентификатор группы |   

signature | string(32) | подпись |   

  

  

Ответ: 

    

    

    <response status="ok">

      <users count="count" totalCount="totalCount">

        <user>

          <!-- ... -->

        </user>

        <user>

          <!-- ... -->

        </user>

        <!-- ... -->

      </users>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**users** |  | список руководителей |   

users.user |  | описание пользователя, смотри полное описание структуры в разделе [user.get](Интеграции/ПланФикс_API_user.get.md) |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
