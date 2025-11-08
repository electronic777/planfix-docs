Функция позволяет получить список доступных текущему сотруднику фильтров задач для функции [task.getList](ПланФикс_API_task.getList.md "ПланФикс API task.getList"). Формат вызова функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="task.getFilterList">

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

      <taskFilterList totalCount="x">

        <taskFilter>

          <ID></ID>

          <Name></Name>

        </taskFilter>

        <taskFilter>

          <ID></ID>

          <Name></Name>

        </taskFilter>

        <!-- -->

      </taskFilterList>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**taskFilterList** |  | список фильтров задач |   

**taskFilterList** totalCount | int | количество элементов в списке |   

taskFilter |  | корневой элемент описывающий фильтр задач |   

taskFilter.ID | int|string | идентификатор фильтра (числовые идентификаторы у пользовательских фильтров и текстовые идентификаторы, начинающиеся с ":" - у системных фильтров Все, Входящие и т.п.) |   

taskFilter.Name | string | название фильтра |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
