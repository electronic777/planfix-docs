Для дальнейшей работы с задачей, пользователь должен принять задачу. Вызов функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="task.accept">

      <account></account>

      <sid></sid>

      <task>

        <id></id>

      </task>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор задачи, которую принимает пользователь |   

signature | string(32) | подпись |   

  

Результатом корректного выполнения запроса будет: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <task>

        <id></id>

      </task>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор задачи, которую принял пользователь |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
