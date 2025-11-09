## Команды от стороннего чата к ПланФиксу


## **newMessage**


Команда для передачи нового сообщения из стороннего чата в ПланФикс. 


  

**Параметры запроса:**


Имя | Описание | Тип/формат данных | Примечание   

---|---|---|---  

cmd | тип операции, в данном случае newMessage | string |   

providerId | идентификатор сторонней системы | string | не должен содержать символ "~"   

channel | дополнительный идентификатор канала на стороне сторонней системы | string | не обязателен, может использоваться при необходимости.   

chatId | уникальный id чата | string |   

planfix_token | ключ (token) ПланФикса, указанный в настройках интеграции | string |   

message | содержимое сообщения | string |   

title | заголовок сообщения | string | необязательный, если есть, используется для формирования названия задачи   

contactId | уникальный идентификатор контакта | string |   

contactName | имя контакта | string |   

contactLastName | фамилия контакта | string | необязательный   

contactIco | фото контакта | string | необязательный   

contactEmail | email контакта | string | необязательный   

contactPhone | телефон контакта | string | необязательный   

contactData | дополнительные данные контакта | string | необязательный   

attachments[name] | вложение (имя) | string | необязательный, допускается несколько   

attachments[url] | вложение (ссылка) | string | необязательный, допускается несколько   

isEcho | исходящее сообщение | boolean | необязательный   

userEmail | email сотрудника-автора исходящего сообщения | string | необязательный, при отсутствии автором будет сотрудник указанный в настройках интеграции, при отсутствии кого-либо и там - сотрудник подключавший интеграцию.   

data_имя_поля_задачи | дополнительные данные, которые надо внести в создаваемую в планфиксе задачу для этого чата. Имя поля в задаче должно точно совпадать с текстом после data_, таких параметров может быть столько, сколько полей заполняется, по одному на каждое поле. К примеру, если вы передаете в запросе параметры data_utm_source и data_utm_medium, то для сохранения этих данных в ПланФиксе, необходимо чтобы в шаблоне задачи были добавлены поля типа Строка с названиями utm_source и utm_medium  | string | необязательный   

  

  

**Пример запроса:**

    

    

    POST https://test.planfix.ru/webchat/api

    

    cmd=newMessage

    providerId=superchat

    chatId=EFHASFN1239351

    planfix_token=303cb962ac59075b964b07152d234b70

    message=Здравствуйте, есть вопрос

    contactId=57487124

    contactName=Иван

    contactLastName=Иванов

    contactIco=https://superchat.io/avatars/183712.png

    contactEmail=ivan@ivanov.com

    contactPhone=79051234567

    contactData=пришёл по запросу газовые котлы

    attachments[name]=фото1.jpg

    attachments[url]=https://superchat.io/files/5444.jpg

    attachments[name]=фото2.jpg

    attachments[url]=https://superchat.io/files/5445.jpg


  

**Варианты ответа:**


HTTP код | Тело | Описание   

---|---|---  

200 |  | ОК   

400 | { error: "Invalid parameters" } | Переданы некорректные параметры   

401 | { error: "Invalid token" } | Передан неверный ключ (token)   

  

## **getTask**


Команда для получения номера задачи в ПланФиксе. 


  

**Параметры запроса:**


Имя | Описание | Тип/формат данных | Примечание   

---|---|---|---  

cmd | тип операции, в данном случае getContact | string |   

providerId | идентификатор сторонней системы | string | не должен содержать символ "~"   

planfix_token | ключ (token) ПланФикса, указанный в настройках интеграции | string |   

chatId | уникальный id чата | string |   

  

  

**Пример запроса:**

    

    

    POST https://test.planfix.ru/webchat/api

    

    cmd=getTask

    providerId=superchat

    planfix_token=303cb962ac59075b964b07152d234b70

    chatId=EFHASFN1239351


  

**Варианты ответа:**


HTTP код | Тело | Описание   

---|---|---  

200 | { "data": {"number": 1014}} | ОК   

400 | { "error": "task not found" } | Задача не найдена   

401 | { "error": "Invalid token" } | Передан неверный ключ (token)   

  

## **getContact**


Команда для получения номера контакта в ПланФиксе. 


  

**Параметры запроса:**


Имя | Описание | Тип/формат данных | Примечание   

---|---|---|---  

cmd | тип операции, в данном случае getContact | string |   

providerId | идентификатор сторонней системы | string | не должен содержать символ "~"   

planfix_token | ключ (token) ПланФикса, указанный в настройках интеграции | string |   

contactId | уникальный идентификатор контакта | string |   

  

  

**Пример запроса:**

    

    

    POST https://test.planfix.ru/webchat/api

    

    cmd=getContact

    providerId=superchat

    planfix_token=303cb962ac59075b964b07152d234b70

    contactId=57487124


  

**Варианты ответа:**


HTTP код | Тело | Описание   

---|---|---  

200 | { "data": {"number": 1058}} | ОК   

400 | { "error": "unknown contact" } | Контакт не найден   

401 | { "error": "Invalid token" } | Передан неверный ключ (token)   

  

  


## **updateContact**


Команда для обновления данных контакта в ПланФиксе сторонним чатом. 


  

**Параметры запроса:**


Имя | Описание | Тип/формат данных | Примечание   

---|---|---|---  

cmd | тип операции, в данном случае updateContact | string |   

providerId | идентификатор сторонней системы | string | не должен содержать символ "~"   

planfix_token | ключ (token) ПланФикса, указанный в настройках интеграции | string |   

contactId | уникальный идентификатор контакта | string |   

contactName | имя контакта | string |   

contactLastName | фамилия контакта | string | необязательный   

contactIco | фото контакта | string | необязательный   

contactEmail | email контакта | string | необязательный   

contactPhone | телефон контакта | string | необязательный   

contactData | дополнительные данные контакта | string | необязательный   

  

  

**Пример запроса:**

    

    

    POST https://test.planfix.ru/webchat/api

    

    cmd=updateContact

    providerId=superchat

    planfix_token=303cb962ac59075b964b07152d234b70

    contactId=57487124

    contactName=Пётр

    contactLastName=Петров

    contactIco=https://superchat.io/avatars/183712.png

    contactEmail=petr@petrov.com

    contactPhone=79051234567

    contactData=пришёл по запросу газовые котлы


  

**Варианты ответа:**


HTTP код | Тело | Описание   

---|---|---  

200 |  | ОК   

400 | { error: "Invalid parameters" } | Переданы некорректные параметры   

401 | { error: "Invalid token" } | Передан неверный ключ (token)   

  

## **messageStatus**


Команда для передачи в ПланФикс статуса отправки / прочтения сообщения 


  

**Параметры запроса:**


Имя | Описание | Тип/формат данных | Примечание   

---|---|---|---  

cmd | тип операции, в данном случае messageStatus | string |   

providerId | идентификатор сторонней системы | string | не должен содержать символ "~"   

planfix_token | ключ (token) ПланФикса, указанный в настройках интеграции | string |   

messageId | идентификатор сообщения - messageId из запроса отправки сообщения из ПланФикса в сторонний чат | string |   

messageStatus | статус отправки | string | 


  * error - ошибка, в ПланФиксе рисуется знак ошибки

  * sent - отправлено, в ПланФиксе рисуется одна галочка

  * read - прочитано, в ПланФиксе рисуется две галочки


любое другое значение обрабатывается как sent   

messageStatusText | дополнительная информация о статусе отправки, если необходима | string | необязательный   

  

  

**Пример запроса:**

    

    

    POST https://test.planfix.ru/webchat/api

    

    cmd=messageStatus

    providerId=superchat

    planfix_token=303cb962ac59075b964b07152d234b70

    messageId=4188849

    messageStatus=read


  

**Варианты ответа:**


HTTP код | Тело | Описание   

---|---|---  

200 |  | ОК   

400 | { error: "Invalid parameters" } | Переданы некорректные параметры   

401 | { error: "Invalid token" } | Передан неверный ключ (token)   

  

  


## Команды от ПланФикса к стороннему чату


## **newMessage**


Команда для передачи нового сообщения из ПланФикса в сторонний чат. 


  

**Параметры запроса:**


Имя | Описание | Тип/формат данных | Примечание   

---|---|---|---  

cmd | тип операции, в данном случае newMessage | string |   

providerId | идентификатор сторонней системы | string |   

chatId | уникальный id чата | string |   

contactPhone | телефон контакта | string | необязательный   

channel | дополнительный идентификатор канала на стороне сторонней системы | string | не обязателен, может использоваться при необходимости.   

token | ключ (token) стороннего чата, указанный в настройках интеграции | string |   

message | содержимое сообщения | string |   

messageId | идентификатор сообщения | string |   

userName | имя ответившего сотрудника | string |   

userLastName | фамилия ответившего сотрудника | string |   

userIco | аватар ответившего сотрудника | string |   

taskEmail | емайл-адрес задачи в ПланФиксе | string |   

attachments[name] | вложение (имя) | string | необязательный, допускается несколько   

attachments[url] | вложение (ссылка) | string | необязательный, допускается несколько   

  

  

**Пример запроса:**

    

    

    POST https://domain/planfix_api.php

    

    cmd=newMessage

    providerId=superchat

    chatId=EFHASFN1239351

    token=202cb962ac59075b964b07152d234b70

    message=Здравствуйте, что вас интересует?

    userName=Петр

    userLastName=Петров

    userIco=https://account.planfix.ru/?action=getuserpic&id=77

    attachments[name]=файл1.doc

    attachments[url]=https://account.planfix.ru/file/aadkapdoa5456454

    attachments[name]=файл2.doc

    attachments[url]=https://account.planfix.ru/file/aadkapdoa5456455


  

**Параметры ответа:**


Имя | Описание | Тип/формат данных | Примечание   

---|---|---|---  

chatId | уникальный id чата | string |   

contactId | уникальный идентификатор контакта | string |   

  

  

**Варианты ответа:**


HTTP код | Тело | Описание   

---|---|---  

200 | { chatId: "chatId", contactId: "contactId" } | ОК   

400 | { error: "Invalid parameters" } | Переданы некорректные параметры   

401 | { error: "Invalid token" } | Передан неверный ключ (token)   

  

## **newMessage (первое сообщение из ПланФикса)**


Команда для передачи первого сообщения из ПланФикса в сторонний чат, в случае, когда активна опция Отображать кнопку "Написать" для контактов с телефоном 


  

**Параметры запроса:**


Имя | Описание | Тип/формат данных | Примечание   

---|---|---|---  

cmd | тип операции, в данном случае newMessage | string |   

providerId | идентификатор сторонней системы | string |   

contactPhone | телефон контакта | string |   

channel | дополнительный идентификатор канала на стороне сторонней системы | string | не обязателен, может использоваться при необходимости.   

token | ключ (token) стороннего чата, указанный в настройках интеграции | string |   

message | содержимое сообщения | string |   

messageId | идентификатор сообщения | string |   

userName | имя ответившего сотрудника | string |   

userLastName | фамилия ответившего сотрудника | string |   

userIco | аватар ответившего сотрудника | string |   

taskEmail | емайл-адрес задачи в ПланФиксе | string |   

attachments[name] | вложение (имя) | string | необязательный, допускается несколько   

attachments[url] | вложение (ссылка) | string | необязательный, допускается несколько   

  

  

**Пример запроса:**

    

    

    POST https://domain/planfix_api.php

    

    cmd=newMessage

    providerId=superchat

    contactPhone=71234567890

    token=202cb962ac59075b964b07152d234b70

    message=Здравствуйте, что вас интересует?

    userName=Петр

    userLastName=Петров

    userIco=https://account.planfix.ru/?action=getuserpic&id=77

    attachments[name]=файл1.doc

    attachments[url]=https://account.planfix.ru/file/aadkapdoa5456454

    attachments[name]=файл2.doc

    attachments[url]=https://account.planfix.ru/file/aadkapdoa5456455


  

**Параметры ответа:**


Имя | Описание | Тип/формат данных | Примечание   

---|---|---|---  

chatId | уникальный id чата | string | обязательный   

contactId | уникальный идентификатор контакта | string | обязательный   

  

  

**Варианты ответа:**


HTTP код | Тело | Описание   

---|---|---  

200 | { chatId: "chatId", contactId: "contactId" } | ОК   

400 | { error: "Invalid parameters" } | Переданы некорректные параметры   

401 | { error: "Invalid token" } | Передан неверный ключ (token)
