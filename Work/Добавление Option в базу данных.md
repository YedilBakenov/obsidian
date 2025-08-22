
#Scala 
#work 

1. postgres

	Создаем новый файл в папке patches с новым названием файла sql
	
	Добавляем через sql новые option 

	В качестве id - указываем номер из файла 91-data_core.sql

	В этом же файле в if прописываем номер предыдущей базы данных

	В файле 95-data_system.sql указываем новую версию базы данных
	![[2 8.png]]

![[3 8.png]]

![[1 11.png]]

2.trax

	В 4-х файлах добавляем новые option, в узб так же указываем как и в русской:
	Options_ru_properties
	Options_uz_properties
	 Options_kz_properties
	  Options_en_properties

![[5 5.png]]


3. core

указываем новую версию БД

![[6 4.png]]