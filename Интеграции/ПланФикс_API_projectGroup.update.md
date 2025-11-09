Функция обновления данных о группе проектов: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="projectGroup.update">

      <account></account>

      <sid></sid>

      <projectGroup>

        <id></id>

        <name></name>

      </projectGroup>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](Интеграции/ПланФикс_API_Аутентификация.md)  

id | int | Идентификатор группы проектов |   

name | string | Название группы проектов |   

  

Ответ при успешном изменении группы проектов: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <projectGroup>

        <id></id>

      </projectGroup>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

projectGroup.id | int | идентификатор измененной группы проектов |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
