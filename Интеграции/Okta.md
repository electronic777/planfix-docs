Интеграция с [Okta](https://www.okta.com/) позволяет сотрудникам вашей компании входить в ПланФикс и другие сервисы, используя единый пароль (Single Sign-On, или [SSO](Интеграции/SSO.md)). Это повышает удобство, безопасность и упрощает управление учетными записями пользователей. 


## Поддерживаемые функции


  * Инициируемый IdP вход (SSO)

  * Инициируемый SP вход

  * Just-In-Time (JIT) создание пользователей

  * SCIM-провижининг


## Функции SCIM-провижининга


  * Создание пользователей

  * Обновление данных пользователей

  * Деактивация пользователей

  * Импорт пользователей


## Этапы настройки


### **Шаги в ПланФиксе**


  * Перейдите в раздел Управление аккаунтом — Интеграции — Single Sign-On.

  * Активируйте интеграцию с Okta.


### **Шаги в Okta**


  * Откройте административную панель [Okta](https://www.okta.com/) в новой вкладке.

  * Перейдите в раздел Applications.

  * Нажмите Browse App Catalog.

  * Найдите в каталоге «Planfix».

  * Выберите приложение Planfix и нажмите Add.

  * Скопируйте домен вашего аккаунта ПланФикса из настроек интеграции и нажмите Done.

  * Перейдите во вкладку Sign On в настройках приложения.

  * Скопируйте ссылку Metadata URL.

  * Вставьте эту ссылку в соответствующее поле в настройках интеграции в ПланФиксе и сохраните настройки.


Теперь на странице входа в ПланФикс будет доступна авторизация через SSO. Убедитесь, что пользователям предоставлен доступ к приложению Planfix в Okta. При первом входе нового пользователя в ПланФикс его учетная запись создается автоматически с помощью механизма Just-In-Time provisioning. 


## SSO, инициируемый со стороны ПланФикса


  * Перейдите на страницу входа ПланФикса.

  * Нажмите "Войти через Okta".

  * Вы будете перенаправлены на страницу входа Okta.

  * Введите свои учетные данные и нажмите Login.

  * Вы будете автоматически авторизованы и возвращены в ПланФикс.


## Настройка SCIM Provisioning


### **В Okta**


  * Откройте настройки приложения Planfix в Okta.

  * Перейдите в раздел Provisioning.

  * Скопируйте SCIM Token из настроек интеграции в ПланФиксе.

  * Вставьте его в соответствующее поле в Okta.

  * Нажмите Test Connector Configuration для проверки, затем Save.

  * Настройте правила в разделе To App в соответствии с требованиями вашей организации.

  * При необходимости настройте также правила в To Okta (например, для добавления пользователей из ПланФикса в Okta).


## Поддерживаемые атрибуты SCIM


Следующие атрибуты SCIM поддерживаются для создания и управления пользователями по схеме [urn:ietf:params:scim:schemas:core:2.0:User](https://datatracker.ietf.org/doc/html/draft-ietf-scim-core-schema-00#section-6): 


**Отображаемое имя** | **Имя переменной** | **Тип данных** | **Тип атрибута** | **Внешнее имя (синтаксис значения)** | **Пространство имён**  

---|---|---|---|---|---  

Имя пользователя | userName | string | Базовый |  | urn:ietf:params:scim:schemas:core:2.0:User   

Имя | givenName | string | Базовый | name.givenName | urn:ietf:params:scim:schemas:core:2.0:User   

Фамилия | familyName | string | Базовый | name.familyName | urn:ietf:params:scim:schemas:core:2.0:User   

Отчество | middleName | string | Пользовательский | name.middleName | urn:ietf:params:scim:schemas:core:2.0:User   

Предпочтительный язык | preferredLanguage | string | Пользовательский | preferredLanguage | urn:ietf:params:scim:schemas:core:2.0:User   

Локаль | locale | string | Пользовательский | locale | urn:ietf:params:scim:schemas:core:2.0:User   

Часовой пояс | timezone | string | Пользовательский | timezone | urn:ietf:params:scim:schemas:core:2.0:User   

Основной телефон | primaryPhone | string | Пользовательский | phoneNumbers.^[primary==true].value | urn:ietf:params:scim:schemas:core:2.0:User   

Тип основного телефона | primaryPhoneType | string | Пользовательский | phoneNumbers.^[primary==true].type | urn:ietf:params:scim:schemas:core:2.0:User   

Основной email | email | string | Пользовательский | emails.^[primary==true].value | urn:ietf:params:scim:schemas:core:2.0:User   

Тип основного email | emailType | string | Пользовательский | emails.^[primary==true].type | urn:ietf:params:scim:schemas:core:2.0:User   

  

## Важно


Email для назначения задач и персональный email — это разные адреса: 


  * Персональный email используется для регистрации и входа в аккаунт.

  * Email для назначения — это системный адрес (например, @planfix.com), на который можно отправлять задачи извне напрямую в систему.
