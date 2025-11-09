Функция используется для изменения списка исполнителей задачи. Формат вызова функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="task.changeWorkers">

      <account></account>

      <sid></sid>

      <task>

        <id></id>

        <workers>

          <addUsers>

            <id></id>

            <id></id>

            <!-- ... -->

          </addUsers>

          <addGroups>

            <id></id>

            <id></id>

            <!-- ... -->

          </addGroups>

          <delUsers>

            <id></id>

            <id></id>

            <!-- ... -->

          </delUsers>

          <delGroups>

            <id></id>

            <id></id>

            <!-- ... -->

          </delGroups>

        </workers>

      </task>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор задачи |   

workers |  | корневой элемент списка исполнителей задачи |   

workers.addUsers |  | корневой элемент списка пользователей, которые подключаются к задаче |   

workers.addUsers.id | int | идентификатор пользователя, который подключается к задаче |   

workers.addGroups |  | корневой элемент списка групп, которые подключаются к задаче |   

workers.addGroups.id | int | идентификатор группы |   

workers.delUsers |  | корневой элемент списка пользователей, которые удаляются из списка исполнителей |   

workers.delUsers.id | int | идентификатор пользователя, который удаляется из списка исполнителей |   

workers.delGroups |  | корневой элемент списка групп, которые удаляются из списка исполнителей |   

workers.delGroups.id | int | идентификатор группы |   

signature | string(32) | подпись |   

  

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <task>

        <id></id>

      </task>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

task.id | int | идентификатор задачи |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
