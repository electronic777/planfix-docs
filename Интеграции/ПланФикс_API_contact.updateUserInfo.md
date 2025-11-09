Функция обновления информации относящейся к залогиниванию пользователя в системе. Выполнение этой функции требует наличие админ прав. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="contact.updateUserInfo">

      <account></account>

      <sid></sid>

      <contact>

        <id></id>

        <userid></userid>

        <general></general>

        <user>

          <password></password>

          <status></status>

          <email></email>

          <pic></pic>

          <notifyByEmail></notifyByEmail>

        </user>

      </contact>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор контакта |   

userid | int | идентификатор контакта для случаев, когда он используется в системе наравне с сотрудниками (исполнитель задачи и т.п., а также пользовательское поле типа контакт) |   

general | int | номер контакта |   

user |  | информация о учетке используемой для залогинивания |   

user.password | string | пароль |   

user.status | enum | статус | список допустимых значений смотри в разделе [статусы пользователей](../Задачи/ПланФикс_API_Статусы_пользователей.md)  

user.email | string | адрес электронной почты |   

user.jabber | string | Jabber-аккаунт | используется в системе уведомлений   

user.notifyByEmail | bool | получать уведомления по электронной почте | установка этого параметра в 1 (использовать) требует непустого значения для поля **email**  

user.notifyByJabber | bool | получать уведомления по jabber | установка этого параметра в 1 (использовать) требует непустого значения для поля **jabber**  

user.notifyByPlanfix | bool | получать уведомления по внутренней системе уведомлений ПланФикс |   

user.pic | string | base64 закодированное изображение |   

signature | string(32) | подпись |   

  

  

Результат успешного выполнения функции: 

    

    

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
