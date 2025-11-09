Запрос на создание группы проектов. Выполнение данной функции разрешено только пользователю с админ правами. Имеет следующий вид: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="projectGroup.add">

      <account></account>

      <sid></sid>

      <projectGroup>

        <name></name>

      </projectGroup>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](Интеграции/ПланФикс_API_Аутентификация.md)  

name | string | Название группы проектов |   

  

Ответ при успешном создании группы проектов: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <projectGroup>

        <id></id>

      </projectGroup>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

projectGroup.id | int | идентификатор созданной группы проектов |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
