Если пользователь по какой-то причине не может выполнить в установленный срок задачу, он может перенести время выполнения её. Формат вызова функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="task.changeExpectDate">

      <account></account>

      <sid></sid>

      <task>

        <id></id>

      </task>

      <expectDate></expectDate>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор задачи |   

expectDate | DateTime | новая дата завершения задачи |   

signature | string(32) | подпись |   

  

  

При успешном выполнении получим следующий ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <task>

        <id></id>

        <endTime></endTime>

      </task>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор задачи |   

task.endTime | DateTime |  | Если в ответе отсутствует параметр **endTime** \- это говорит о том, что был послан запрос постановщику с предложением о смене даты.   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
