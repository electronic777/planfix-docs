Функция позволяет прикрепить файл к проекту или задаче. Формат вызова: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="file.upload">

      <account></account>

      <sid></sid>

      <task>

        <id></id>

      </task>

      <project>

        <id></id>

      </project>

      <owner>

        <id></id>

      </owner>

      <target></target>

      <action>

        <id></id>

      </action>

      <files>

        <file>

          <name></name>

          <sourceType></sourceType>

          <otherFile>

            <id></id>

            <url></url>

          </otherFile>

          <body></body>

          <description></description>

          <newversion></newversion>

        </file>

      </files>

      <notifiedList>

        <users>

          <id></id>

          <id></id>

          <!-- ... -->

        </users>

      </notifiedList>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

silent | bool | при значении 1 - об изменении не рассылаются уведомления | обязательное значение 1 при массовых периодических обновлениях задач   

task |  | в рамках какой задачи сохраняется | исключает наличие **project**  

task.id | int | идентификатор задачи |   

project |  | в рамках какого проекта сохраняется | используется, если не задан **task**  

project.id | int | идентификатор проекта |   

owner |  | автор загружаемых файлов | необязательное поле. Если не указано - берется пользователь от имени которого выполняется функция   

owner.id | int | идентификатор автора файлов |   

target | string | куда прикрепить файл, может принимать одно из следующих значений: 


  * action - к существующему действию (указанному в action.id)

  * task - к самой задаче (нужны права на ее изменение у автора запроса)


| необязательный параметр, по умолчанию файл крепится новым действием к задаче   

action.id | int | идентификатор действия, к которому крепится файл |   

files |  | корневой элемент содержащий список сохраняемых файлов |   

file |  | сохраняемый файл |   

file.name | string | имя сохраняемого файла | игнорируется, если **sourceType** =PROJECT   

file.sourceType | enum | тип источника | список допустимых значений смотри в [типы источников файла](ПланФикс_API_Типы_источников_файла.md "ПланФикс API Типы источников файла")  

file.otherFile |  | Использовать уже существующий файл | используется при sourceType: INTERNET, PROJECT   

file.otherFile.id | int | идентификатор файла, используется при ссылке на файл из проекта | sourceType=PROJECT   

file.otherFile.url | string | URL файла в Интернет | используется только при sourceType=INTERNET   

file.body | string | тело файла закодированное base64 | используется при sourceType=FILESYSTEM   

file.description | string | краткое описание содержимого файла | не обязательный параметр, игнорируется, если **sourceType** =PROJECT   

file.newversion | boolean | если значение равно "1", при совпадении имени файла с ранее загруженным, не выдаётся ошибка, а файл загружается, как новая версия существующего | не обязательный параметр   

notifiedList |  | список пользователей которых должны уведомить |   

notifiedList.users |  | корневой элемент списка пользователей |   

notifiedList.users.id | int | идентификатор пользователя |   

  

  

Результат удачного выполнения запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <files>

        <file>

          <uniqueId></uniqueId>

          <name></name>

        </file>

        <file>

          <uniqueId></uniqueId>

          <name></name>

        </file>

        <!-- ... -->

      </files>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

action.id | int | идентификатор добавленного действия |   

  

Ответ является списком файлов из имён файлов и присвоенных им идентификаторов. 


В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

      <id></id>

      <name></name>  

    </response>


Параметры id и name присутствуют при code=9006 (имя файла совпадает с именем уже существующего в данном проекте), и в них содержится имя и идентификатор существующего файла.
