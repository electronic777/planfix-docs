Функция позволяет получить информацию о группе проектов. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="projectGroup.get">

      <account></account>

      <sid></sid>

      <projectGroup>

        <id></id>

      </projectGroup>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

projectGroup.id | int | идентификатор запрашиваемой группы проектов |   

signature | string(32) | подпись |   

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <projectGroup>

        <id></id>

        <name></name>

      </projectGroup>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор группы проектов |   

name | string | название группы проектов |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
