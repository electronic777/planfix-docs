Добавление комментария. Неполная версия функции, будет дорабатываться: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="action.add">

      <account></account>

      <sid></sid>

      <action>

        <description></description>

        <task>

          <id></id>

          <general></general>

        </task>

        <contact>

          <general></general>

        </contact>

        <taskNewStatus></taskNewStatus>

        <notifiedList>

          <user>

            <id></id>

            <id></id>

            <!-- ... -->

          </user>

        </notifiedList>

        <isHidden></isHidden>

        <owner>

          <id></id>

        </owner>

        <dateTime></dateTime>

        <analitics>

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

      </action>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

description | string | описание комментария |   

task (contact) |  | задача/контакт, к которым добавляется комментарий — должен присутствовать только один узел (или task или contact) |   

task.id | int | идентификатор задачи |   

task.general | int | номер задачи (если задан, используется вместо id) |   

contact.general | int | номер контакта |   

taskNewStatus | enum | этим комментарием меняется статус задачи на указанный | не обязательный параметр, перечень допустимых значений смотри в разделе [статусы задач](../Задачи/ПланФикс_API_Статусы_задач.md)  

notifiedList |  | этим комментарием необходимо уведомить следующих пользователей | необязательный параметр поле   

notifiedList.user |  | список пользователей, которые получат уведомление |   

notifiedList.user.id | int | идентификатор пользователя |   

isHidden | bool | является ли комментарий скрытым от всех пользователей, за исключением списка уведомленных пользователей | не обязательное поле, по умолчанию равно 0 (false)   

owner |  | автор комментария | необязательное поле. Если не указано — берется пользователь, от имени которого выполняется функция   

owner.id | int | идентификатор автора комментария | если это контакт - нужно использовать userid из ответа [contact.get](ПланФикс_API_contact.get.md)  

dateTime | [ DateTime](ПланФикс_API_Тип_данных_DateTime.md) | дата/время создания — не обязательный, по умолчанию текущие | может заполняться, только если авторизация была сделана под сотрудником с правами администратора   

analitics |  | задается (прикрепляется) список аналитики | не обязательный параметр   

analitics.analitic |  | узел, содержащий данные по прикрепляемой аналитике |   

analitic.id | int | идентификатор аналитики | список доступных аналитик можно получить при помощи функции [analitic.getList](ПланФикс_API_analitic.getList.md)  

analitic.analiticData |  | список значений полей |   

analiticData.itemData |  | значение одного из параметров |   

itemData.fieldId | int | идентификатор параметра | идентификатор параметра равен [field.id](ПланФикс_API_analitic.getOptions.md)  

itemData.value | string | значение |   

| формат значения для разных типов аналитики:   

| DATE | дд-мм-гггг   

| TIME | чч:мм   

| TIMEPERIOD | <begin>чч:мм</begin><end>чч:мм</end>  

| HANDBOOK | int - key записи справочника   

| USER | int - идентификатор сотрудника   

| CLIENT | int - идентификатор контрагента   

| LOGINLIST | <id></id>...<id></id> \- где каждый из узлов (узел может быть один) содержит идентификатор сотрудника, к которому относится аналитика.   

  

  

Результат удачного выполнения запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <action>

        <id></id>

      </action>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

action.id | int | идентификатор добавленного действия |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
