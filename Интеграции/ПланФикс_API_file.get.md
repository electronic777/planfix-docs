Функция получения информации о файле. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="file.get">

      <account></account>

      <sid></sid>

      <file>

        <id></id>

        <uniqueId></uniqueId>

      </file>

      <returnDownloadLinks></returnDownloadLinks>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

file.id | int | идентификатор файла |   

file.uniqueId | int | уникальный идентификатор файла | игнорируется, если задан параметр **id**  

returnDownloadLinks | bool | возвращать ли в ответе постоянные ссылки для скачивания файла | значение по-умолчанию 0   

signature | string(32) | подпись |   

  

  

Результат выполнения функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <file>

        <id></id>

        <uniqueId></uniqueId>

        <name></name>

        <version></version>

        <description></description>

        <date></date>

        <sourceType></sourceType>

        <size></size>

        <task>

          <id></id>

          <title></title>

        </task>

        <project>

          <id></id>

          <title></title>

        </project>

        <user>

          <id></id>

          <name></name>

        </user>

        <downloadLink></downloadLink>

      </file>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

id | int | идентификатор файла |   

uniqueId | int | уникальный идентификатор файла |   

name | string | имя файла |   

version | int | версия |   

description | string | описание |   

date | DateTime | дата загрузки файла |   

sourceType | enum | типы файлов | список допустимых значений смотри в [типы файлов](Интеграции/ПланФикс_API_Типы_файлов.md)  

size | int | размер в килобайтах |   

task |  | в рамках какой задачи был залит |   

task.id | int | идентификатор задачи |   

task.title | string | название задачи |   

project |  | в рамках какого проекта был загружен файл |   

project.id | int | идентификатор проекта |   

project.title | string | название проекта |   

user |  | пользователь, который загрузил файл |   

user.id | int | идентификатор пользователя |   

user.name | string | имя пользователя |   

downloadLink | string | ссылка для скачивания файла |   

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
