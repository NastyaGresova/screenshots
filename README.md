# Инструкция для проекта "base_tests"
### 1. Нужно создать подключение к БД

##### **1.1.** Windows -> Панель управления -> Администрирование -> Источники данных (ODBC):
![Источники данных (ODBC)](https://github.com/NastyaGresova/HelloWorld/blob/main/connection_db_1.PNG)

##### 1.2. В окне "Создание нового источника данных" выбрать "ODBC Driver 17 for SQL Server":
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/connection_db2.PNG)

##### 1.3. В окне "Создание источника данных для SQL Server" заполнить имя для источника данных и выбрать нужный сервер:
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/connection_db3.PNG)

##### 1.4. Далее выбрать пункт "проверка подлинности учетной записи SQL Server" и ввести имя пользователя и пароль:
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/connection_db4.PNG)

##### 1.5. Проставить галочку "Использовать по умолчанию базу данных" и выбрать базу данных, к которой нужно подключаться:
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/connection_db5.PNG)

##### 1.6. На следующем этапе ничего не меняем, нажимаем на кнопку "Готово":
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/connection_db6.PNG)

##### 1.7. В окне "Установка ODBC для Microsoft SQL Server" нажать на кнопку "Проверить источник данных...":
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/connection_db7.PNG)

##### 1.8. Если все ок, то получаем такой результат:
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/connection_db8.PNG)


### 2. Теперь нужно настроить в Медиалоге модели для поиска

##### 2.1. В глоссарии для объекта "Амбулаторные назначения", вкладка "Список"
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/base_tests_gloss_simple.PNG)

##### 2.2. В глоссарии для объекта "Амбулаторные назначения", вкладка "Типовые"
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/base_tests_gloss_typical.PNG)

##### 2.3. В окне для поиска медикаментов
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/base_tests_toolbar_drug.PNG)

##### 2.4. В окне для поиска шаблона (схемы) для назначения
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/base_tests_toolbar_drug_scheme.PNG)

##### 2.5. В окне для поиска типовых назначений
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/base_tests_toolbar_typical.PNG)

##### 2.6. В проекте "base_tests" способ введения в назначение добавляется двойным кликом из глоссария, поэтому нужно учесть, что глоссарий со способами введения не должен быть пустым
![Имя изображения](https://github.com/NastyaGresova/HelloWorld/blob/main/base_tests_gloss_intake_methods.PNG)

### 3. Нужно настроить переменные в файле Unit_var.sj

Сейчас в файле Unit_var.sj настроены переменные для следующих тестовых баз:
* \\SQL-SERVER\CLIENTS_BASE\TESTIROVANYE\ALL\TESTERS_800_DEV_BTK
* \\Sql-server2019\clients_base\TESTIROVANYE\ALL\Testers_810_DEV_Collection_7DF
* \\SQL-SERVER2019\CLIENTS_BASE\TESTIROVANYE\ALL\TESTERS_810_4_COLLECTION_7DF

Для того, чтобы запустить проект, нужно в файле Unit_var.sj оставить переменные для базы, на которой будут проводиться тесты, а остальные переменные закомментировать.
Можно не изменять переменные в файле, тогда тесты будут проходить по одним и тем же значениям (под значениями имеются ввиду медикаменты, схема приема, способ введения и т.д.). Но для того, чтобы тесты прогонялись по разным значениям, переменные нужно менять. 
Файл Unit_var.sj разделен на три блока:
* переменные для работы на базе \\SQL-SERVER\CLIENTS_BASE\TESTIROVANYE\ALL\TESTERS_800_DEV_BTK
* переменные для работы на базе \\Sql-server2019\clients_base\TESTIROVANYE\ALL\Testers_810_DEV_Collection_7DF
* переменные для работы на базе \\SQL-SERVER2019\CLIENTS_BASE\TESTIROVANYE\ALL\TESTERS_810_4_COLLECTION_7DF
Чтобы изменить переменные, выберем один из блоков. Например, возьмем переменные для работы на базе \\SQL-SERVER\CLIENTS_BASE\TESTIROVANYE\ALL\TESTERS_800_DEV_BTK. 
В первой части этого блока находится список переменных. Далее идут различные функции. Функции менять не нужно.

var w0_var=Sys.Process("Automedi");  *- переменную w0_var менять не нужно, это сам процесс Automedi, он везде одинаковый*

var version = 5;  *- номер версии, для DEV-версии version = 5, а для пользовательской версии version = 4*

var db = "BTK"  *- это вообще очень спорная штука, ее надо убрать !!!*

var patients_id_var = 535828; *- id пациента, на котором проводятся тесты*

var pr_drugs_id_var = 436;   *- id основного медикамента, этот медикамент будет использоваться в большей части тестов*

var scheme_name="test_1" *- название схемы приема из контекстного меню медикамента*

var scheme_name_window_DirServEditor = "тест_10_02_2022" * - название схемы приема, которая выбирается в окне-редакторе назначения*

var pr_drugs_id_list = [434, 436, 463, 442];  *- id медикаментов, на основе которых делается составное назначение*

var pr_templates_id_var = 220; *- id схемы приема*

var intake_method_i_var = 2; *- просто порядковый номер способа введения из глоссария* 

var pr_template_schemes_id = 4211;  *-  id типового назначения*

var name_motconsu = "Поликлиника - Направления/Назначения"   *- название записи, в которой мы будем работать*

var cancelled_note = "тест123TEST!@#$%)(_"  *- комментарий для отмены назначения*











