Функция удаления списка файлов. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="file.delete">

      <account></account>

      <sid></sid>

      <files>

        <id></id>

        <id></id>

        <!-- ... -->

      </files>

      <signature></signature>

    </request>


или 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="file.delete">

      <account></account>

      <sid></sid>

      <files>

        <uniqueId></uniqueId>

        <uniqueId></uniqueId>

        <!-- ... -->

      </files>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

files |  | список идентификаторов файлов |   

files.id | int | идентификатор файла |   

files.uniqueId | int | уникальный идентификатор файла |   

signature | string(32) | подпись |   

  

  

Результат выполнения функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <count></count>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

count | int | количество удаленных файлов |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
