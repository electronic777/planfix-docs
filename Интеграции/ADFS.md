Интеграция с Active Directory Federation Service (ADFS) позволяет сотрудникам вашей компании входить в ПланФикс с использованием единого пароля [SSO](SSO.md). Это упрощает авторизацию, повышает безопасность и облегчает администрирование учетных записей. 


## Настройка Single Sign-On (SSO)


### Шаги в ПланФиксе


  * Перейдите в раздел Управление аккаунтом — Интеграции — Single Sign-On.

  * Активируйте интеграцию с Active Directory Federation Service (ADFS).


После этого перейдите к настройке на стороне вашего ADFS-сервера. 


## Шаги в ADFS


### Создание Relying Party Trust


  1. В панели ADFS Management перейдите в Trust Relationships — Relying Party Trusts и нажмите Add Relying Party Trust…

  2. На первом экране выберите Claims aware — Next.

  3. На шаге Select Data Source выберите Enter data about the relying party manually — Next.

  4. Укажите Display name, например: Planfix.

  5. Нажмите Next → Next.

  6. Отметьте Enable support for the SAML 2.0 Web SSO protocol.

  7. В поле Relying party SAML 2.0 SSO service URL введите URL из настроек интеграции в ПланФиксе 

         

         https://{account_planfix_url}/saml2/login/sso/adfs


  8. Нажмите Next.

  9. На шаге Configure Identifiers нажмите Add и введите Identifier (Entity ID) из ПланФикса 

         

         https://{account_planfix_url}/saml2/service-provider-metadata/adfs


  10. Нажмите Next → Close.


## Настройка правил выдачи Claim'ов


  * Выберите созданный Relying Party Trust, затем в правой панели нажмите Edit Claim Issuance Policy.

  * Нажмите Add Rule…


### Отправка LDAP-атрибутов


  * Выберите Send LDAP Attributes as Claims

  * Нажмите Next и укажите следующее:


     **LDAP Attribute** | **Outgoing Claim Type**  

---|---  

Display-Name  | Name   

Given-Name  | Given Name   

Surname  | Surname   

User-Principal-Name  | E-Mail Address   

  

  * Нажмите Finish.


### Форматирование Name ID как Email


  1. Нажмите Add Rule…

  2. Выберите шаблон Transform an Incoming Claim

  3. Заполните поля: 

     1. Name: Format NameID as Email

     2. Incoming claim type: UPN

     3. Outgoing claim type: Name ID

     4. Outgoing Name ID format: Email

     5. Pass through all claim values: включено (✓)

  4. Нажмите Finish.


## Важно


Не создавайте дополнительное правило Send LDAP Attributes as Claims для Name ID — только правило Transform an Incoming Claim гарантирует, что в <NameID Format="…"> будет использован формат emailAddress. 


## Финальный шаг


  * Вернитесь в ПланФикс и в настройках интеграции с ADFS заполните поле Metadata URI: 

        

        https://<adfs-server>/FederationMetadata/2007-06/FederationMetadata.xml


  * Сохраните изменения.
