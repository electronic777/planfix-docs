Функция обновления пользовательских полей контакта. Может использоваться, если у пользователя нет прав на изменение контакта и поэтому использовать функцию contact.update он не может, но при этом есть права на изменение пользовательских полей. 


Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="contact.updateCustomData">

      <account></account>

      <sid></sid>

      <contact>

        <id></id>

        <general></general>

        <customData>

          <customValue>

            <id></id>

            <value></value>

          </customValue>

          <!-- ... -->

        </customData>

      </contact>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор обновляемого контакта |   

general | int | номер обновляемого контакта (используется если не задан id) |   

customData |  | значения пользовательских полей контакта |   

customData.customValue.id |  | идентификатор пользовательского поля контакта |   

customData.customValue.value |  | значение пользовательского поля контакта | (для полей типа набор задач, список сотрудников, набор записей справочника - идентификаторы через запятую в квадратных скобках)   

signature | string(32) | подпись |   

  

Результат успешного выполнения функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <contact>

        <id></id>

        <general></general>

      </contact>

      <actionid></actionid>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

contact.id | int | идентификатор обновляемого контакта |   

contact.general | int | номер добавленного контакта |   

actionid | int | идентификатор действия об изменении |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
