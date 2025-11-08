Функция позволяет получить список доступных типов телефонных номеров. Формат вызова функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="contact.getPhoneTypes">

      <account></account>

      <sid></sid>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

signature | string(32) | md5 от имени функции, значений всех полей, исключая _signature_ | подробное описание алгоритма формирования подписи смотри в разделе [ПланФикс API:Формирование цифровой подписи](ПланФикс_API_Формирование_цифровой_подписи.md "ПланФикс API:Формирование цифровой подписи")  

  

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <phoneTypes totalCount="x">

        <phoneType>

          <id></id>

          <name></name>

        </phoneType>

        <phoneType>

          <id></id>

          <name></name>

        </phoneType>

        <!-- -->

      </phoneTypes>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**phoneTypes** |  | списоктипов телефонных номеров |   

**phoneTypes** totalCount | int | количество элементов в списке |   

phoneType |  | корневой элемент описывающий тип телефонного номера |   

phoneType.id | int | идентификатор |   

phoneType.name | string | название |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
