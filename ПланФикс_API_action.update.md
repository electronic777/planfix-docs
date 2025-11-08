Функция обновления данных в комментарии. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="action.update">

      <account></account>

      <sid></sid>

      <action>

        <id></id>

        <description></description>

        <taskNewStatus></taskNewStatus>

        <notifiedList>

          <user>

            <id></id>

            <id></id>

            <!-- ... -->

          </user>

        </notifiedList>

        <isHidden></isHidden>

        <dateTime></dateTime>

        <analitics>

          <analitic>

            <id></id>

            <analiticData>

              <key></key>

              <itemData>

                <fieldId></fieldId>

                <value></value>

              </itemData>

              <itemData>

                <fieldId></fieldId>

                <value></value>

              </itemData>

              <!-- ... -->

            </analiticData>

          </analitic>

          <!-- ... -->

          <analitic>

            <id></id>

            <analiticData>

              <itemData>

                <fieldId></fieldId>

                <value></value>

              </itemData>

              <itemData>

                <fieldId></fieldId>

                <value></value>

              </itemData>

              <!-- ... -->

            </analiticData>

          </analitic>

          <!-- ... -->

        </analitics>

        <deletedAnalitics>

          <key></key>

          <key></key>

          <!-- ... -->

        </deletedAnalitics>

      </action>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор комментария |   

description | string | текст комментария |   

taskNewStatus | enum | этим комментарием меняется статус задачи на указанный | не обязательный параметр, перечень допустимых значений смотри в разделе [статусы задач](ПланФикс_API_Статусы_задач.md "ПланФикс API:Статусы задач"), попытка поменять на неправильный статус или поменять статус не последним комментарием приведет к ошибке   

notifiedList |  | этим комментарием необходимо уведомить следующих пользователей |   

notifiedList.user |  | список пользователей, которые получат уведомление |   

notifiedList.user.id | int | идентификатор пользователя |   

isHidden | bool | является ли комментарий скрытым от всех пользователей, за исключением списка уведомленных пользователей | не обязательное поле, по умолчанию равно 0 (false)   

dateTime | [ DateTime](ПланФикс_API_Тип_данных_DateTime.md "ПланФикс API:Тип данных DateTime") | дата/время создания - не обязательный, по умолчанию - не изменяется | может заполняться, только если авторизация была сделана под сотрудником с правами администратора   

analitics |  | список обновляемых аналитик | не обязательный параметр   

analitics.analitic |  | узел, содержащий данные по аналитике |   

analitic.id | int | идентификатор аналитики | список доступных аналитик можно получить при помощи функции [analitic.getList](ПланФикс_API_analitic.getList.md "ПланФикс API analitic.getList")  

analitic.analiticData |  | список строк аналитики |   

analiticData.key | int | идентификатор строки аналитики, если в запросе этот атрибут присутствует - происходит изменения аналитики с этим идентификатором, если нет - добавление новой строки аналитики |   

analiticData.itemData |  | значение поля аналитики |   

itemData.fieldId | int | идентификатор поля аналитики | идентификаторы можно получить методом [feild.id](ПланФикс_API_analitic.getOptions.md "ПланФикс API analitic.getOptions")  

itemData.value | string | значение поля аналитики |   

deletedAnalitics |  | список удаленных аналитик |   

deletedAnalitics.key | int | ключ данных удаляемой аналитики | данное поле становится доступным после выполнения [функции analitic.getData](ПланФикс_API_analitic.getData.md "ПланФикс API analitic.getData")  

signature | string(32) | подпись |   

  

Помните, можно обновлять комментарии с типом **ACTION** и **COMMENT**. Остальные попытки будут вызывать ошибку. 


  

Результат удачного выполнения запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <action>

        <id></id>

      </action>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

action.id | int | идентификатор обновляемого комментария |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
