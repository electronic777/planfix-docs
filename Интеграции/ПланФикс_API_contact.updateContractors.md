Функция изменение информации о принадлежности контакта к компании. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="contact.updateContractors">

      <account></account>

      <sid></sid>

      <contact>

        <id></id>

        <contractors>

          <addClient>

            <id></id>

            <id></id>

            <!-- -->

          </addClient>

          <delClient>

            <id></id>

            <id></id>

            <!-- -->

          </delClient>

        </contractors>

      </contact>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

id |  |  |   

contractors |  | корневой элемент компаний |   

contractors.addClient |  | список компаний, к которым относится контакт |   

contractors.addClient.id | id | идентификатор компании |   

contractors.delClient |  | список компаний, которые исключаются из списка компаний контакта |   

contractors.delClient.id | id | идентификатор компании |   

signature |  |  |   

  

  

Результат успешного выполнения: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <contact>

        <id></id>

      </contact>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

contact.id | int | идентификатор контакта |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
