Для настройки интеграции с [виртуальной АТС CallGear](http://callgear.com/): 


1\. Перейдите в раздел **Управление аккаунтом / Интеграции** (доступен владельцу или администратору аккаунта). Нажмите на **Виртуальные АТС** : 


  

![lz3sz6.png](images/lz3sz6.png)


  

и в появившемся списке нажмите **Активировать** напротив CallGear. 


  

![mh4xNi.png](images/mh4xNi.png)


  

2\. В открывшемся окне введите логин, пароль от личного кабинета CallGear, а также принадлежащий вам виртуальный номер, который будет использоваться при исходящих вызовах: 


![EnR4W1.png](images/EnR4W1.png)


3\. Укажите короткие номера сотрудников 


  

4\. В личном кабинете CallGear для работы интеграции должны быть активированы тарифные опции "HTTP notifications", "Call API basic set" и "Data API" 


  

5\. В личном кабинете CallGear разрешите доступ к Call API и к Data API с любых IP-адресов: 


![bAR54j.png](images/bAR54j.png)


![qcvwfK.png](images/qcvwfK.png)


  

6\. Возьмите Notification URL из параметров интеграции в ПланФиксе: 


![UbXw2g.png](images/UbXw2g.png)


Создайте следующие уведомления в Личном кабинете Comagic в разделе "Notifications": 


![fCGX3v.png](images/fCGX3v.png)


Все уведомления отправляются методом POST на Notification URL из параметров интеграции: 


![tajga2.png](images/tajga2.png)


1\. Inbound call on a virtual phone number 

    

    

    {  

      "notification_mnemonic":{{notification_mnemonic}},

      "notification_name":{{notification_name}},

      "virtual_phone_number":{{virtual_phone_number}},

      "notification_time":{{notification_time}},

      "scenario_name": {{scenario_name}},

        "contact_phone_number":{{contact_phone_number}},

        "communication_number":{{communication_number}},

        "contact_id": {{contact_id}},

        "contact_full_name": {{contact_full_name}},

      "call_session_id":{{call_session_id}}

    }


2\. Call finished 

    

    

    {  

      "notification_name":{{notification_name}},

      "notification_mnemonic":{{notification_mnemonic}},

      "virtual_phone_number":{{virtual_phone_number}},

      "notification_time":{{notification_time}},

      "external_id": {{external_id}},

        "contact_phone_number":{{contact_phone_number}},

        "communication_number":{{communication_number}},

        "employee_full_name": {{employee_full_name}},

        "employee_id": {{employee_id}},

        "call_source": {{call_source}},

        "direction": {{direction}},

        "call_session_id":{{call_session_id}},

        "scenario_name": {{scenario_name}},

        "talk_time_duration": {{talk_time_duration}},

        "total_time_duration": {{total_time_duration}},

        "wait_time_duration": {{wait_time_duration}},

        "tag_names": {{tag_names}}

    }


3\. Call recording completed 

    

    

    {

      "notification_name": {{notification_name}},

      "notification_mnemonic":{{notification_mnemonic}},

      "virtual_phone_number": {{virtual_phone_number}},

      "notification_time": {{notification_time}},

      "scenario_name": {{scenario_name}},

        "contact_phone_number": {{contact_phone_number}},

        "communication_number": {{communication_number}},

        "contact_id": {{contact_id}},

        "contact_full_name": {{contact_full_name}},

      "call_session_id": {{call_session_id}},

        "employee_full_name": {{employee_full_name}},

        "employee_id": {{employee_id}},

        "file_link": {{file_link}},

        "file_duration": {{file_duration}},

      "tag_ids": {{tag_ids}},

      "tag_names": {{tag_names}}

    }


4\. Waiting for the answer 

    

    

    {  

      "notification_name":{{notification_name}},

      "notification_mnemonic":{{notification_mnemonic}},

      "virtual_phone_number": {{virtual_phone_number}},

      "notification_time":{{notification_time}},

      "external_id": {{external_id}},

        "contact_phone_number":{{contact_phone_number}},

        "contact_id": {{contact_id}},

        "employee_full_name": {{employee_full_name}},

        "employee_id": {{employee_id}},

      "call_source": {{call_source}},

      "call_session_id":{{call_session_id}},

      "direction": {{direction}},

      "leg_id": {{leg_id}}

    }


5\. Outbound call 

    

    

    {

      "notification_name": {{notification_name}},

      "notification_mnemonic":{{notification_mnemonic}},

      "virtual_phone_number": {{virtual_phone_number}},

      "notification_time": {{notification_time}},

        "contact_phone_number":{{contact_phone_number}},

        "contact_id":{{contact_id}},

        "contact_full_name":{{contact_full_name}},

      "call_session_id":{{call_session_id}},

        "employee_full_name":{{employee_full_name}},

        "employee_id":{{employee_id}},

        "employee_phone_number":{{employee_phone_number}}

    }


6\. Talk started 

    

    

    {  

      "notification_name":{{notification_name}},

      "notification_mnemonic":{{notification_mnemonic}},

      "virtual_phone_number": {{virtual_phone_number}},

      "notification_time":{{notification_time}},

      "external_id": {{external_id}},

        "contact_phone_number":{{contact_phone_number}},

        "contact_id": {{contact_id}},

        "employee_full_name": {{employee_full_name}},

        "employee_id": {{employee_id}},

      "call_source": {{call_source}},

      "call_session_id":{{call_session_id}},

      "direction": {{direction}},

      "leg_ids": {{leg_ids}}

    }


7\. Talk finished 

    

    

    {  

      "notification_name":{{notification_name}},

      "notification_mnemonic":{{notification_mnemonic}},

      "virtual_phone_number":{{virtual_phone_number}},

      "notification_time":{{notification_time}},

      "external_id": {{external_id}},

        "contact_phone_number":{{contact_phone_number}},

        "communication_number":{{communication_number}},

        "employee_full_name": {{employee_full_name}},

        "employee_id": {{employee_id}},

        "call_source": {{call_source}},

        "call_session_id":{{call_session_id}},

        "direction": {{direction}},

        "scenario_name": {{scenario_name}},

        "talk_time_duration": {{talk_time_duration}},

      "leg_ids": {{leg_ids}}

    }


8\. Lost call 

    

    

    {  

      "notification_name":{{notification_name}},

      "notification_mnemonic":{{notification_mnemonic}},

      "virtual_phone_number":{{virtual_phone_number}},

      "notification_time":{{notification_time}},

      "scenario_name": {{scenario_name}},

      "wait_time_duration" : {{wait_time_duration}},

      "employee_ids":{{employee_ids}},

        "contact_phone_number":{{contact_phone_number}},

        "communication_number":{{communication_number}},

        "contact_id": {{contact_id}},

        "contact_full_name":{{contact_full_name}},

      "call_session_id":{{call_session_id}}

    }
