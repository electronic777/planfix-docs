Функция получения списка пользователей. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="user.getList">

      <account></account>

      <sid></sid>

      <status></status>

      <onlyOnline></onlyOnline>

      <userGroup>

        <id></id>

      </userGroup>

      <sortType></sortType>

      <pageCurrent></pageCurrent>

      <pageSize></pageSize>

      <filters>

        <filter>

          <type></type>

          <operator></operator>

          <value></value>

        </filter>

        ...

      </filters>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

status | enum | статус пользователя | список допустимых значений смотри в разделе [статусы пользователей](ПланФикс_API_Статусы_пользователей.md "ПланФикс API:Статусы пользователей"). Игнорируется если задана группа   

onlyOnline | bool | показывать только сотрудников online |   

userGroup.id | int | идентификатор группы (фильтр по группе) |   

sortType | enum | тип сортировки | список допустимых значений смотри в разделе [типы сортировок пользователей](ПланФикс_API_Типы_сортировок_пользователей.md "ПланФикс API:Типы сортировок пользователей")  

pageCurrent | int | текущая страница | 0 - используется для получения количества сотрудников   

pageSize | int | размер получаемого списка | не больше 100   

filters |  | дополнительные фильтры | перечень и формат допустимых значений смотри в разделе [фильтры сотрудников](ПланФикс_API_Фильтры_сотрудников.md "ПланФикс API:Фильтры сотрудников")  

  

  

Ответ: 

    

    

    <response status="ok">

      <users count="count" totalCount="totalCount">

        <user>

          <!-- ... -->

        </user>

        <user>

          <!-- ... -->

        </user>

        <!-- ... -->

      </users>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**users** |  | список пользователей |   

**users** count | int | количество пользователей в списке |   

**users** totalCount | int | количество пользователей удовлетворяющих условию запроса |   

users.user |  | описание пользователя, смотри полное описание структуры в разделе [user.get](ПланФикс_API_user.get.md "ПланФикс API user.get") |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
