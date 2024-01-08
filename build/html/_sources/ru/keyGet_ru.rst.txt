**Получение ключа TOTP**
========================

Для безопасного управления устройством с аутентификацией по TOTP протоколу необходимо знать ключ, 
который представляет из себя последовательность из 16 байт. Он генерируется облаком в момент первого 
подключения и при каждой привязке к аккаунту.
 
 Получить его можно только через API сервера в 2 этапа:
		* получить токен авторизации для нужной учетной записи
		* получить список устройств с параметрами, привязанных к данной учетной записи

`Получение токена авторизации`
``````````````````````````````

    **POST** `https://{server_url}/api/login/`
	
.. code-block:: json
	
		{
			"email":"user@email.com",
			"password":"myPassword"
		}

**Параметры:**
	- **email** - почта зарегистрированного аккаунта
	- **password** - пароль от аккаунта

**Ответ:**

.. code-block:: json

		{
			"access_token":"9573e6a8e24b025fafbaf81dc2eccbc09b94d187",
			"user_name":"myterneo",
			"is_timezone_chosen":true
		}

``access_token`` - искомый токен авторизации

**Пример:**

  ..  code-block:: html

	{
		POST /api/login/ HTTP/1.1
		Host: my.hmarex.com
		Accept-Language: en
		Content-Type: application/json
		
		{"email":"myterneo@gmail.com","password":"myterneo2018"}	
	}

`Получение списка устройств`
````````````````````````````
    
    **GET** https://my.hmarex.com/api/device/ --header "Authorization: Token ``access_token``"

		**Параметры**
			- ``access_token`` - токен авторизации в заголовке			        
        		
* Ответ:

	.. code-block:: json

		{
			"count": 4,
			"next": null,
			"previous": null,
			"results": [
				{
					"id": 18801,
					"sn": "1100150010434B58363539XXXXXXXX",
					"name": "Room1",
					"":""
					"totp_key": "BW4ERXAJXXXXXXXX"
				}
			]

		}

Поле ``totp_key`` в параметрах каждого устройства содержит искомый ключ для генерации TOTP токена.

* Пример:

  ..  code-block:: html

	{
		GET /api/device/ HTTP/1.1
		Host: my.hmarex.com
		Accept-Language: en
		Content-Type: application/json
		Authorization: Token 9573e6a8e24b025fafbaf81dc2eccbc09b94d187	
	}