Создание записи справочника. Формат запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <request method="handbook.addRecord">

      <account></account>

      <sid></sid>

      <handbook>

        <id></id>

      </handbook>

      <parentKey></parentKey>

      <isGroup></isGroup>

      <name></name>

      <archived></archived>

      <customData>

        <customValue>

          <id></id>

          <value></value>

          <files>

            <file>

              <name></name>

              <sourceType></sourceType>

              <otherFile>

                <url></url>

              </otherFile>

              <body></body>

              <description></description>

              <newversion></newversion>

            </file>

          </files>

        </customValue>

        <!-- ... -->

      </customData>

      <signature></signature>

    </request>


Название | Тип | Значение | Примечание   

---|---|---|---  

sid | string(32) | ключ сесии | выдается в результате прохождения [аутентификации](ПланФикс_API_Аутентификация.md "ПланФикс API:Аутентификация")  

handbook.id | int | идентификатор справочника |   

parentKey | int | идентификатор группы записей | необязательный параметр   

isGroup | bool | является ли запись группой |   

name | string | название, если запись является группой |   

archived | bool | является ли запись архивной |   

customData |  | значения полей |   

customData.customValue.id |  | идентификатор поля |   

customData.customValue.value |  | значение поля | (для полей типа набор задач, список сотрудников, набор записей справочника - идентификаторы через запятую в квадратных скобках)   

files |  | корневой элемент содержащий список сохраняемых файлов |   

file |  | сохраняемый файл |   

file.name | string | имя сохраняемого файла |   

file.sourceType | enum | тип источника | список допустимых значений смотри в [типы источников файла](ПланФикс_API_Типы_источников_файла.md "ПланФикс API Типы источников файла"), допустимые значения FILESYSTEM и INTERNET   

file.otherFile |  | Использовать уже существующий файл | используется при sourceType: INTERNET   

file.otherFile.url | string | URL фала в Интернет | используется только при sourceType=INTERNET   

file.body | string | тело файла закодированное base64 | используется при sourceType=FILESYSTEM   

file.description | string | краткое описание содержимого файла | не обязательный параметр   

file.newversion | boolean | если значение равно "1", при совпадении имени файла с ранее загруженным, не выдаётся ошибка, а файл загружается, как новая версия существующего | не обязательный параметр   

  

Ответ при успешном выполнении запроса: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="ok">

      <key></key>

    </response>


Название | Тип | Значение | Примечание   

---|---|---|---  

key | int | идентификатор записи |   

  

В противном случае будет возвращен ответ с ошибкой: 

    

    

    <?xml version="1.0" encoding="UTF-8"?>

    <response status="error">

      <code></code>

    </response>
