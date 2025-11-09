Функция получения информации о комментарии. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="action.get">

      <account></account>

      <sid></sid>

      <action>

        <id></id>

      </action>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

action.id | int | идентификатор комментария |   

signature | string(32) | подпись |   

  

  

Ответ: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <action>

        <id></id>

        <description></description>

        <type></type>

        <statusChange>

          <oldStatus></oldStatus>

          <newStatus></newStatus>

        </statusChange>

        <isNotRead></isNotRead>

        <fromEmail></fromEmail>

        <dateTime></dateTime>

        <task>

          <id></id>

          <title></title>

        </task>

        <contact>

          <general></general>

          <name></name>

        </contact>

        <owner>

          <id></id>

          <name></name>

        </owner>

        <project>

          <id></id>

          <title></title>

        </project>

        <taskExpectDateChanged>

          <oldDate></oldDate>

          <newDate></newDate>

        </taskExpectDateChanged>

        <taskStartTimeChanged>

          <oldDate></oldDate>

          <newDate></newDate>

        </taskStartTimeChanged>

        <files>

          <file>

            <id></id>

            <name></name>

          </file>

          <file>

            <id></id>

            <name></name>

          </file>

          <!-- ... -->

        </files>

        <notifiedList>

          <user>

            <id></id>

            <name></name>

          </user>

          <user>

            <id></id>

            <name></name>

          </user>

          <!-- ... -->

        </notifiedList>

        <analitics>

          <analitic>

            <id></id>

            <key></key>

            <name></name>

          </analitic>

          <analitic>

            <id></id>

            <key></key>

            <name></name>

          </analitic>

          <!-- ... -->

        </analitics>

      </action>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор комментария |   

description | string | описание комментария |   

type | enum | тип действия | список возможных значений смотри в разделе [типы действий](../Автоматизация/ПланФикс_API_Список_типов_действий.md)  

statusChange |  | наличие данного узла свидетельствует о том, что этим комментарием был изменен статус задачи |   

statusChange.oldStatus | enum | старый статус | список допустимых значений смотри [статусы задач](../Задачи/ПланФикс_API_Статусы_задач.md)  

statusChange.newStatus | enum | новый статус | список допустимых значений смотри [статусы задач](../Задачи/ПланФикс_API_Статусы_задач.md)  

isNotRead | bool | комментарий не помечен как прочитанный |   

fromEmail | bool | комментарий создан из письма по электронной почте |   

dateTime | DateTime | дата добавления комментария |   

task |  | информация о задаче |   

task.id | int | идентификатор задачи |   

task.title | string | название задачи |   

contact |  | информация о контакте | присутствует, только если комментарий добавлен к контакту   

contact.general | int | номер контакта |   

contact.name | string | имя контакта |   

owner |  | пользователь, который создал комментарий |   

owner.id | int | идентификатор пользователя |   

owner.name | string | имя пользователя |   

project |  | в рамках какого проекта был создан комментарий |   

project.id | int | идентификатор проекта |   

project.title | string | название проекта |   

taskExpectDateChanged |  | если задан данный узел, то этим комментарием было изменено время окончания задачи |   

taskExpectDateChanged.oldDate | DateTime | прежнее время |   

taskExpectDateChanged.newDate | DateTime | новое время |   

taskStartTimeChanged |  | если задан данный узел, то этим комментарием было изменено время начала задачи (приступить к работе) |   

taskStartTimeChanged.oldDate | DateTime | прежнее время |   

taskStartTimeChanged.newDate | DateTime | новое время |   

files |  | список файлов прикрепленных этим комментарием |   

files.file |  | узел, описывающий файл |   

files.file.id | int | идентификатор файла |   

files.file.name | string | имя файла |   

notifiedList |  | список пользователей, которых должны уведомить о комментарии |   

notifiedList.user |  | пользователь |   

notifiedList.user.id | int | идентификатор пользователя |   

notifiedList.user.name | string | имя пользователя |   

analitics |  | список прикрепленных аналитик к комментарию |   

analitics.analitic |  | аналитика |   

analitics.analitic.id | int | идентификатор аналитики |   

analitics.analitic.key | int | идентификатор строки данных аналитики |   

analitics.analitic.name | string | название аналитики |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
