Для отклонения задачи, необходимо вызвать следующую функцию: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="task.reject">

      <account></account>

      <sid></sid>

      <task>

        <id></id>

      </task>

      <reason></reason>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор задачи, которую отклоняет пользователь |   

reason | string | причина | обязательное поле, не может быть пустым   

signature | string(32) | подпись |   

  

  

Результатом удачного выполнения функции будет следующий ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <task>

        <id></id>

      </task>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор задачи, которую отклонил пользователь |   

  

  


В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
