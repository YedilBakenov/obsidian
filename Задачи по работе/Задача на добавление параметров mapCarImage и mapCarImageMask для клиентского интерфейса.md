#task
#Scala 

1. Надо отправить три запроса, запрос get:
	 первый на получение настроек тарифов на геозоне
2. Отравить запрос на окружение на добавление параметров
    ClientAppProfiles.editZoneTariff 1.0
   3. Отправить запрос на получение настроек 
   ClientAppProfiles.getZoneTariff 1.0
4. Надо будет скачать водительское и установить эти параметры




 - на коре в классе DtoTariff не используются эти два параметра
 - на коре в классе DtoTariffConversions.scala есть мои изменения, которые я не вносил


5. Тестирование запроса ClientAppProfiles.getZoneTariff 1.0
	Параметры:
		{"profileId": "2c0c7985-9da6-454f-a0cc-3c14644fc2ff",
		"zoneId": "d71d2030-56a2-4ead-be0c-fc5c3146175b",
		"tariffId": "993000000051655"
		}
	Ответ:
		{
		  "id": "993000000051655",
		  "profileId": "2c0c7985-9da6-454f-a0cc-3c14644fc2ff",
		  "zoneId": "d71d2030-56a2-4ead-be0c-fc5c3146175b",
		  "title": "Тестовый тариф",
		  "settings": {
		    "shortDescription": "",
		    "longDescription": "",
		    "minPreorderTime": 0,
		    "showIfDriversNotFound": true,
		    "showCalculatedCost": true,
		    "allowanceEnabled": false,
		    "allowanceVariants": [],
		    "allowanceChangeTimeout": 0,
		    "destinationAddressRequired": false,
		    "destinationAddressesLimit": 4
		  }
		}	


		ClientAppProfiles - это сохранение в клиент ауз сервисе
		
