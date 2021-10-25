## Подключение к Базе Данных из Excel.

### Для пользователей Mac Os:

К сожалению, на MacOS ODBC драйвера платные, может бесплатно где-то и лежат, но ссылки на такие ресурсы мы дать не можем :(
Ссылка на iODBC Driver Manager (управление и настройка ODBC драйверов) - 
http://www.iodbc.org/dataspace/doc/iodbc/wiki/iodbcWiki/Downloads#Stable%20Version%203.52.15

### Для пользователей Windows:

Для того, чтобы из Excel подключиться к Базе Данных должен быть установлен Excel и нужно установить ODBC драйвера.

Нужно перейти по ссылке для скачивания [ODBC драйвера](https://www.postgresql.org/ftp/odbc/versions/msi/), скачать 12 или 13 версию драйвера в зависимости от разрядности Операционной Системы.

1. Разархивируете скачанный файл, запускаете установочный файл, нажимаете Далее

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/1.png)

2. Соглашаетесь с Лицензионным соглашением и нажимаете Далее

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/2.png)

3. Нажимаете Далее

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/3.png)

4. Нажимаете Далее

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/4.png)

5. Нажимаете Установить.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/5.png)

6. Нажимаете Завершить.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/6.png)

7. После этого нажимаете **WIN + R** и копируете команду: 

Если у Вас установлен Excel 64 бит  ```%windir%\syswow64\odbcad32.exe```

Если у Вас установлен Excel 32 бит  ```odbcad32.exe```

Откроется окно Администратора источника данных ODBC. Нажимаете Добавить, откроется окно Создания нового источника данных.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/7.png)

8. Опускаетесь вниз и выбираете PostgreSQL Unicode, нажимаете Готово.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/8.png)

9. Заполняете данные согласно таблицы, что бы настроить подключение к облачной учебной Базе Данных.

Параметр | Значение 
--- | ---
Хост | 84.201.152.11
Порт | 19001
База данных | postgres
Пользователь | netology
Пароль | NetoSQL2019

Нажимаете Test

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/9.png)

10. Нажимаете Ок и после Сохранить.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/10.png)

11. Нажимаете Ок и окно закроется.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/11.png)

12. Открываете Excel, создаете новую Книгу, переходите во вкладку Данные (в старых версиях вкладка Power Query) и нажимаете “Получить данные”

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/12.png)

13. Далее выбираете “Из других источников” и выбираете “Из ODBC”

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/13.png)

14. Имя источника данных выбираете PostgreSQL и нажимаете Ок.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/14.png)

15. Далее еще раз вводите логин и пароль и нажимаете “Подключение”

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/15.png)

16. Можете раскрыть содержимое Базы Данных. Далее либо преобразуете данные, либо загружаете, в зависимости от задачи.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/odbc/images/16.png)

