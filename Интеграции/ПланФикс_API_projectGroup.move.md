Функция перемещения группы проектов в списке: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="projectGroup.move">

      <account></account>

      <sid></sid>

      <move>

        <projectGroup>

          <id></id>    

        </projectGroup>

      </move>

      <after>

        <projectGroup>

          <id></id>    

        </projectGroup>

      </after>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](Интеграции/ПланФикс_API_Аутентификация.md)  

move |  | Перемещаемая группа проектов |   

move.projectGroup.id | int | Идентификатор перемещаемой группы проектов |   

after |  | Группа, после которой в списке необходимо расположить перемещаемую группу проектов |   

after.projectGroup.id | int | Идентификатор группы проектов |   

  

Ответ при успешном перемещении группы проектов: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <projectGroup>

        <id></id>

      </projectGroup>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

projectGroup.id | int | идентификатор перемещенной группы проектов |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
