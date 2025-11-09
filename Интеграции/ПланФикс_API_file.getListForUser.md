Функция получение списка файлов, которые загрузил пользователь. Данную функцию можно вызывать с правами администратора для любого пользователя, либо получать список собственных файлов. 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="file.getListForUser">

      <account></account>

      <sid></sid>

      <user>

        <id></id>

      </user>

      <pageCurrent></pageCurrent>

      <pageSize></pageSize>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

user.id | int | идентификатор пользователя |   

pageCurrent | int | текущая страница | нумерация с 1. 0 - используется для получения количества   

pageSize | int | размер запрашиваемой страницы |   

signature | string(32) | подпись |   

  

Результат выполнения функции: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <files count="count" totalCount="totalCount">

        <file>

          <id></id>

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

        </file>

        <file>

          <!-- ... -->

        </file>

        <!-- ... -->

      </files>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

**files** |  |  |   

**files** count | int | количество возвращенных запросом файлов |   

**files** totalCount | int | количество файлов удовлетворяющих запросу |   

file |  | узел описывающий файл |   

id | int | идентификатор файла |   

name | string | имя файла |   

version | int | версия |   

description | string | описание |   

date | DateTime | дата загрузки файла |   

sourceType | enum | типы файлов | список допустимых значений смотри в [типы файлов](ПланФикс_API_Типы_файлов.md)  

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

  

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
