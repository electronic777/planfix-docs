Приведем пару простых примеров для иллюстрации работы с ПланФикс API 


Пусть в Управление аккаунтом / Доступ к API у нас следующие данные и создан один токен авторизации 


![tUa3VT.jpg](images/tUa3VT.jpg)


  


APIKey = 583e3bcc38f34a4af6d8deadbeef8e2d 


Токен = 277ebe9f3a5770adeadbeefa2bc3dbb8 


  


## Добавление комментария в задачу


(с номером 23525 в аккаунте testo.planfix.ru) 

    

    

    curl -H 'Accept: application/xml' -H 'Content-Type: application/xml' \

    -u 583e3bcc38f34a4af6d8deadbeef8e2d:277ebe9f3a5770adeadbeefa2bc3dbb8 \

    -d '<request method="action.add">\

    <account>testo</account>\

    <action>\

    <task><general>23525</general></task>\

    <description>текст комментария</description>\

    </action></request>' \

    https://api.planfix.ru/xml/


  


## Добавление комментария в задачу с html разметкой


(с номером 23525 в аккаунте testo.planfix.ru ) 

    

    

    curl -H 'Accept: application/xml' -H 'Content-Type: application/xml' \

    -u 583e3bcc38f34a4af6d8deadbeef8e2d:277ebe9f3a5770adeadbeefa2bc3dbb8 \

    -d '<request method="action.add">\

    <account>testo</account>\

    <action>\

    <task><general>23525</general></task>\

    <description>строка раз&lt;br&gt;строка два&lt;br&gt;&lt;b&gt;жирный текст&lt;/b&gt;</description>\

    </action></request>' \

    https://api.planfix.ru/xml/


  


## Добавление комментария к контакту


(с номером 12300 в аккаунте testo.planfix.ru с html разметкой) 

    

    

    curl -H 'Accept: application/xml' -H 'Content-Type: application/xml' \

    -u 583e3bcc38f34a4af6d8deadbeef8e2d:277ebe9f3a5770adeadbeefa2bc3dbb8 \

    -d '<request method="action.add">\

    <account>testo</account>\

    <action>\

    <contact><general>12300</general></contact>\

    <description>строка раз&lt;br&gt;строка два&lt;br&gt;&lt;b&gt;жирный текст&lt;/b&gt;</description>\

    </action></request>' \

    https://api.planfix.ru/xml/


  


## Поиск контакта по номеру телефона


(в аккаунте testo.planfix.ru) 

    

    

    curl -H 'Accept: application/xml' -H 'Content-Type: application/xml' \

    -u 583e3bcc38f34a4af6d8deadbeef8e2d:277ebe9f3a5770adeadbeefa2bc3dbb8 \

    -d '<request method="contact.getList">\

    <account>testo</account>\

    <pageCurrent>1</pageCurrent>\

    <pageSize>10</pageSize>

    <filters><filter>\

    <type>4003</type>\

    <operator>equal</operator>\

    <value>123456</value>\

    </filter></filters></request>' \

    https://api.planfix.ru/xml/


## Поиск контакта по значению поля типа строка


(с идентификатором поля 10123, в аккаунте testo.planfix.ru) (идентификаторы полей можно получить методом [contact.get](ПланФикс_API_contact.get.md) на шаблоне контакта с этим полем) 

    

    

    curl -H 'Accept: application/xml' -H 'Content-Type: application/xml' \

    -u 583e3bcc38f34a4af6d8deadbeef8e2d:277ebe9f3a5770adeadbeefa2bc3dbb8 \

    -d '<request method="contact.getList">\

    <account>testo</account>\

    <pageCurrent>1</pageCurrent>\

    <pageSize>10</pageSize>

    <filters><filter>\

    <type>4101</type>\

    <field>10123</field>\

    <operator>equal</operator>\

    <value>value_fo_find</value>\

    </filter></filters></request>' \

    https://api.planfix.ru/xml/


## Поиск задачи по значению поля типа строка


(с идентификатором поля 10123, в аккаунте testo.planfix.ru) (идентификаторы полей можно получить методом [task.get](ПланФикс_API_task.get.md) на шаблоне задачи с этим полем, справка фильтрам - [ПланФикс API:Фильтры задач](../Задачи/ПланФикс_API_Фильтры_задач.md)) 

    

    

    curl -H 'Accept: application/xml' -H 'Content-Type: application/xml' \

    -u 583e3bcc38f34a4af6d8deadbeef8e2d:277ebe9f3a5770adeadbeefa2bc3dbb8 \

    -d '<request method="task.getList">\

    <account>testo</account>\

    <pageCurrent>1</pageCurrent>\

    <pageSize>10</pageSize>

    <filters><filter>\

    <type>101</type>\

    <field>10123</field>\

    <operator>equal</operator>\

    <value>value_fo_find</value>\

    </filter></filters></request>' \

    https://api.planfix.ru/xml/
