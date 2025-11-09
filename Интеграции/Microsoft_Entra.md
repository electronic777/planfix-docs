Интеграция с [Microsoft Entra](https://www.microsoft.com/en-us/security/business/microsoft-entra) позволяет сотрудникам вашей компании входить в ПланФикс и другие сервисы, используя единый пароль (Single Sign-On, или SSO). Это повышает удобство, безопасность и упрощает управление учетными записями пользователей. 


## Поддерживаемые функции


  * Инициируемый IdP вход (SSO)

  * Инициируемый SP вход

  * Just-In-Time (JIT) создание пользователей

  * SCIM Provisioning


## Функции SCIM Provisioning


  * Создание пользователей

  * Обновление данных пользователей

  * Деактивация пользователей

  * Импорт пользователей


## Этапы настройки


### Шаги в ПланФиксе


  * Перейдите в раздел Управление аккаунтом — Интеграции — Single Sign-On.

  * Активируйте интеграцию с Microsoft Entra.


### Шаги в Microsoft Entra


  * Создание Enterprise Application 

    * Откройте консоль Microsoft Entra под учетной записью с правами администратора.

    * Перейдите в Applications — Enterprise applications.

    * Нажмите + New application — + Create your own application.

    * Задайте имя, например: Planfix Entra.

    * В разделе назначения выберите: 

          

          Integrate any other application you don’t find in the gallery (Non-gallery)


    * После создания приложения откройте его карточку.

  * Настройка SAML SSO 

    * В меню приложения откройте **Single sign-on** и выберите метод **SAML**.

    * В блоке **Basic SAML Configuration** укажите данные:


     **Поле** | **Значение**  

---|---  

Identifier (Entity ID) | https://{account_planfix_url}/saml2/service-provider-metadata/entra   

Reply URL (Assertion Consumer Service URL) | https://{account_planfix_url}/saml2/sso/entra   

  

  * Сохраните настройки.


### Шаги в ПланФиксе


  * Вернитесь в Интеграции — Single Sign-On.

  * В поле **Metadata URI** укажите **App Federation Metadata Url** , скопированный из настроек Entra-приложения.

  * Сохраните изменения.


### Назначение пользователей


  * В настройках приложения откройте раздел **Users and groups**.

  * Добавьте пользователей или группы, которым необходим доступ к ПланФиксу через SSO.


### Проверка


  * В разделе Single sign-on приложения в Entra нажмите кнопку **Test**.

  * Убедитесь, что перенаправление и авторизация через ПланФикс проходят корректно.


## Настройка SCIM Provisioning


  * В Entra-приложении перейдите в Provisioning — Provisioning.

  * В поле **Provisioning Mode** выберите **Automatic**.

  * В разделе **Admin Credentials** укажите:


     **Поле** | **Значение**  

---|---  

Authentication Method | Bearer Authentication   

Tenant URL | SCIM URL из настроек ПланФикса   

Secret Token | SCIM Token из настроек ПланФикса   

  

  * Нажмите **Test Connection** для проверки соединения.

  * Перейдите в раздел **Mappings** и отключите опцию **Provision Microsoft Entra ID Groups**.

  * Сохраните изменения.


## Итоговая проверка интеграции


Убедитесь, что выполнены все пункты: 


  * В ПланФиксе активирована интеграция SSO с Microsoft Entra.

  * В Entra создано приложение **Enterprise Application** и корректно настроен **SAML SSO**.

  * В ПланФиксе указано значение **Metadata URI** из приложения Entra.

  * Пользователи (или группы) назначены приложению в Entra.

  * В Entra выполнен успешный тест авторизации (**Test**) и вход через ПланФикс работает.

  * Настроен **SCIM Provisioning** , проверено соединение (**Test Connection**).

  * В SCIM Mappings отключено автоматическое создание групп (**Provision Microsoft Entra ID Groups**).

  * Пользователи корректно создаются или обновляются в ПланФиксе через SCIM.
