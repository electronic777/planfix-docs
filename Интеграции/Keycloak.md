Интеграция с Keycloak позволяет сотрудникам вашей компании входить в ПланФикс с использованием единого пароля [SSO](SSO.md). Это упрощает авторизацию, повышает безопасность и облегчает администрирование учетных записей. 


## Настройка Single Sign-On (SSO)


### Шаги в ПланФиксе


  * Перейдите в раздел Управление аккаунтом — Интеграции — Single Sign-On.

  * Активируйте интеграцию с Keycloak.


### Шаги в Keycloak


  * В новой вкладке откройте панель администрирования Keycloak.

  * Создайте или выберите существующий Realm.

  * Перейдите в раздел Clients → Create client.

  * Укажите следующие параметры: 

    * General Settings: 

      * Client type: SAML

      * Client ID: скопируйте из настроек интеграции в ПланФиксе

      * Name: Planfix SAML APP

      * Description: Planfix SAML APP

      * Always display in UI: On

    * Login Settings: 

      * Root URL: скопируйте из настроек интеграции в ПланФиксе

      * Home URL: скопируйте из настроек интеграции в ПланФиксе

      * Valid redirect URIs: скопируйте из настроек интеграции в ПланФиксе

      * Valid post logout redirect URIs: (оставить пустым или настроить по необходимости)

      * IDP-Initiated SSO URL name: (необязательно)

      * IDP Initiated SSO Relay State: (необязательно)

      * Master SAML Processing URL: (необязательно)

  * После создания клиента, перейдите в его настройки и укажите: 

    * Раздел Settings — SAML capabilities: 

      * Name ID format: email

    * Раздел Signature and Encryption: 

      * Sign documents: On

    * Раздел Keys — Signing keys config: 

      * Client signature required: Off


### Финальный шаг


  * Вернитесь в ПланФикс и в настройках интеграции с Keycloak заполните поле Metadata URI.


    

    

    https://{KEYCLOAK-URL}/realms/{REALM-NAME}/protocol/saml/descriptor


Вместо переменных {KEYCLOAK-URL} и {REALM-NAME} подставьте значения из своего Keycloak. 


## Важно


  * Убедитесь, что у пользователей есть доступ к соответствующему приложению в Keycloak.

  * При первой авторизации новая учетная запись будет создана автоматически через механизм JIT (Just-In-Time provisioning).
