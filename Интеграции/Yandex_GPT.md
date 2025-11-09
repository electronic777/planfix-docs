В ПланФикс можно [интегрировать](Интеграции/Интеграции.md) Yandex GPT. Для установки требуется тариф "Профессионал". 


Выполните следующие действия: 


  * Установите [конфигурацию](https://planfix.ru/configurations/integracziya-s-yandex-gpt-p160/) из маркетплейса ПланФикса.

  * Подключите YandexGPT в [Yandex Cloud](https://console.cloud.yandex.ru/link/yandexgpt).


## Аккаунт Яндекса


  * Получите OAuth-токен в сервисе Яндекс.OAuth. Для этого: 

    * Перейдите по [ссылке](https://oauth.yandex.ru/authorize?response_type=token&client_id=1a6990aa636648e9b2ef855fa7bec2fb).

    * Нажмите **Разрешить**.

    * Скопируйте полученный OAuth-токен.

  * [Получите идентификатор каталога](https://cloud.yandex.ru/docs/resource-manager/operations/folder/get-id), на который у вашего аккаунта есть роль.

  * Добавьте своей учетной записи права ai.languageModels.user или выше. Для этого: 

    * Перейдите в [консоль управления](https://console.cloud.yandex.ru/cloud).

    * Выберите нужный каталог.

    * Перейдите на вкладку **Права доступа**.

    * Добавьте своей учетной записи права **ai.languageModels.user**.


Пример сценария с пользовательской операцией «Запрос в YandexGPT (аккаунт в Яндексе)»: 


![Funsaf.png](images/Funsaf.png)


## Сервисный аккаунт


  * [Создайте API Key](https://cloud.yandex.ru/docs/iam/operations/api-key/create).

  * API Key — это «Ваш секретный ключ» в окне результата.


Пример сценария с использованием пользовательской операции «Запрос в YandexGPT (сервисный аккаунт - API Key)»: 


![qLAUcK.png](images/qLAUcK.png)


## Модели


В поле «Модель» введите URI модели. Доступные модели смотрите в [документации](https://yandex.cloud/ru/docs/foundation-models/concepts/yandexgpt/models).
