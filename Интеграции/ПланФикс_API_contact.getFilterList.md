Функция позволяет получить список доступных текущему сотруднику фильтров контактов для функции [contact.getList](Интеграции/ПланФикс_API_contact.getList.md). Формат вызова функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="contact.getFilterList">

      <account></account>

      <sid></sid>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

signature | string(32) | md5 от имени функции, значений всех полей, исключая _signature_ | подробное описание алгоритма формирования подписи смотри в разделе [ПланФикс API:Формирование цифровой подписи](Интеграции/ПланФикс_API_Формирование_цифровой_подписи.md)  

  

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <contactFilterList totalCount="x">

        <contactFilter>

          <ID></ID>

          <Name></Name>

        </contactFilter>

        <contactFilter>

          <ID></ID>

          <Name></Name>

        </contactFilter>

        <!-- -->

      </contactFilterList>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**contactFilterList** |  | список фильтров контактов |   

**contactFilterList** totalCount | int | количество элементов в списке |   

contactFilter |  | корневой элемент описывающий фильтр контактов |   

contactFilter.ID | int|string | идентификатор фильтра (числовые идентификаторы у пользовательских фильтров и текстовые идентификаторы, начинающиеся с ":" - у системных фильтров Контакты и Компании) |   

contactFilter.Name | string | название фильтра |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
