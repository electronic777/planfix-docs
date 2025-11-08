Получение полного списка групп пользователей на аккаунте. Не требует админ прав. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="userGroup.getList">

      <account></account>

      <sid></sid>

      <sortType></sortType>

      <pageCurrent></pageCurrent>

      <pageSize></pageSize>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

account | string | имя аккаунта, на котором выполняется функция |   

sid | string(32) | ключ сессии |   

sortType | enum | тип сортировки | не обязательный параметр. список допустимых значений смотри в разделе [типы сортировок для групп](ПланФикс_API_Типы_сортировок_для_групп.md "ПланФикс API:Типы сортировок для групп")  

pageCurrent | int | постраничная навигация | не обязательный параметр. значения меньше 1 будут инициировать процедуру подсчета количества элементов.   

pageSize | int | количество выдаваемых значений в результате. не может превышать значение **100** | не обязательный параметр. если будет опущен, возьмется значение по умолчанию.   

signature | string(32) | подпись |   

  

Отвте: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <userGroups count="count" totalCount="totalCount">

        <userGroup>

          <id></id>

          <name></name>

          <userCount></userCount>

        </userGroup>

        <userGroup>

          <id></id>

          <name></name>

          <userCount></userCount>

        </userGroup>

        <!-- ... -->

      </userGroups>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**userGroups** |  | корневой элемент, содержащий список групп |   

**userGroups** count | int | количество групп возвращенных запросом |   

**userGroups** totalCount | int | количество групп удовлетворяющих запросу |   

userGroup |  | элемент группы |   

userGroup.id | int | идентификатор группы |   

userGroup.name | string | название группы |   

userGroup.userCount | int | количество пользоавателей в группе |   

  

Для пользователей не с админ правами, значение поля **userCount** \- будет всегда рано **0** (ноль). 


  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
