Инструкция по подготовке ПК к работе с PostgreSQL DB
====================================================

# Оглавление
* [Предусловие](#Precondition)
* [Инструкия по работе с локальной БД](#Instructions-for-working-with-a-local-database)
    * [Что мы научимся делать в рамках настройки работы с локальной БД](#что-мы-научимся-делать-в-рамках-настройки-работы-с-локальной-бд)
    * [Какое программное обеспечение нам потребуется](#какое-программное-обеспечение-нам-потребуется)
        * [Установка DBeaver](#установка-dbeaver)
        * [Установка PostgreSQL Server](#установка-postgresql-server)
        * [Загрузка базы из бекапа dvd-rental](#загрузка-базы-из-бекапа-dvd-rental)
        * [Ручное добавление JAR драйвера для работы с БД](#ручное-добавление-jar-драйвера-для-работы-с-бд)
        * [Ручное добавление локального клиента в DBeaver](#ручное-добавление-локального-клиента-в-dbeaver)
        * [Ручной экспорт результатов из DBeaver в Excel](#ручной-экспорт-результатов-из-dbeaver-в-excel)
        * [Ручное восстановление дампа, если DBeaver завис](#ручное-восстановление-дампа-если-dbeaver-завис)
    * [Подключение к облачной базе данных](#подключение-к-облачной-базе-данных)
    * [Установка на MacOS](#установка-на-macos)
    * [Восстановление пароля](#восстановление-пароля)



<a name="Precondition"></a>

## Предусловие

На текущий момент существует 2 способа выполнения заданий с помощью DBeaver, выполняемых в рамках курса по SQL:

1. работа с облачной БД с помощью DBeaver, предполагающая только наличие ПО для работы с имеющейся БД;
2. работа с локальной БД с помощью DBeaver, предполагающая наличие собственного PostgreSQL Server, а также наличие ПО для работы с БД.

В чем основные отличия в этих двух способах:

В первом случае, мы будем взаимодействовать с базой данных, установленной на серверах Нетологии. Соответственно, нам не придется заниматься настройкой собственного сервера.

Во втором случае мы пройдем полный путь и развернем локальную копии базы данных на собственном компьютере и будем полностью отвечать за ее работоспособность.

Так как никто не знает с чем вам предстоит взаимодействовать в процессе работы - мы рассмотрим оба варианта для полноты знаний.

**Важное уточнение:**

Версии ПО, используемые в данной инструкции, могут отличаться от тех, что представлены на сайтах разработчиков программных продуктов. В процессе выполнения инструкции вам необходимо выбирать актуальные **стабильные** версии, которые соответствуют требованиям и характеристикам вашей системы (под системой мы подразумеваем ваш персональный компьютер/ноутбук/виртуальную машину и т.д.), с которой вы осуществляете работу.


<a name="Instructions-for-working-with-a-local-database"></a>

## Инструкция по работе с локальной БД

<a name="что-мы-научимся-делать-в-рамках-настройки-работы-с-локальной-бд"></a>

### Что мы научимся делать в рамках настройки работы с локальной БД

1. установка PostgreSQL Server;
2. настройка базы данных в PostgreSQL Server для работы с ней;
3. использование бекапа базы данных для последующей работы с ним;
4. установка и настройка DBeaver для работы с базой данных PostgreSQL.


<a name="какое-программное-обеспечение-нам-потребуется"></a>

### Какое программное обеспечение нам потребуется

1. PostgreSQL Server от EDB - https://www.enterprisedb.com/downloads/postgres-postgresql-download;
2. DBeaver - https://dbeaver.io;
3. бекап базы данных dvd - rental: https://drive.google.com/file/d/1p3CM1Foye-fX695COvfq70YeIRA-a6XR/view?usp=sharing 
4. бекап схемы hr (для выполнения 7 занятия): https://drive.google.com/file/d/1Cx4yM-boIUVDdc3ExYp8zYsbwH-Wgxh8/view?usp=sharing


<a name="установка-dbeaver"></a>

### Установка DBeaver

Для подключения к учебной облачной базе данных, а также для работы с локальной учебной базой данных, нам надо скачать и установить DBeaver — клиентское приложение для управления СУБД, которое даёт возможность администрировать структуру БД, выполнять запросы на SQL, получать результаты запросов, импортировать и экспортировать данные и т. д.

Для установки ПО переходим по ссылке [на сайт сообщества DBeaver](https://dbeaver.io) и нажимаем кнопку загрузки.

![Кнопка перехода в раздел скачивания на сайте DBeaver](/sql-main/resources/InstallDbeaver/DBeaverDownloadButton.png)

Сразу оговоримся, что DBeaver постоянно обновляется, сказать точно, какая версия будет актуальной на момент вашего обучения, невозможно. На апрель 2022  года действует Community Edition 22.0.3. Поэтому - скачиваем последнюю стабильную версию.

**Внимание:** Если у вас 32-х битная разрядность системы - вам необходимо использовать DBeaver не выше версии 6.0.0!!! (Ссылка на скачивание: https://dbeaver.io/files/6.0.0/)

Есть две версии программы DBeaver:

* Community Edition;
* Enterprise Edition (Внимание: Указанная версия платная и при установке вам будет выдан бесплатный доступ только на 30 дней. Поэтому советуем использовать Community Edition, он покроет все ваши потребности в рамках учебных задач).

Разница лишь в том, что в Enterprise Edition есть поддержка NoSQL баз данных, таких как MongoDB и Cassandra. Мы же воспользуемся бесплатной версией — Community Edition.

Выбирайте вариант вашей операционной системы и скачивайте ПО. К примеру, для Mac OS X жмём на ссылку Mac OS X (dmg).

![Список скачиваемых версий DBeaver](/sql-main/resources/InstallDbeaver/DBeaverDownload.png)

Далее нам необходимо определиться с типом установки Dbeaver.

Если вы желаете установить стандартную версию, вам необходимо скачать стандартный инсталлятор с сайта и запустить его.

![Выбираем DBeaver Windows(installer)](/sql-main/resources/InstallDbeaver/DBeaverWindowsInstaller.png)

Если при попытке запуска инсталлятора у вас запрашивает права администратора (и они у вас есть) - ждем “Да” (обычно запрашивать не должно).

Нажимаем “Далее >”

![Нажимаем далее](/sql-main/resources/InstallDbeaver/Dbeaver1.png)

Принимаем лицензионное соглашение, нажав “Принимаю” (можете прочитать, если хотите =_=)

![Принимаем соглашение](/sql-main/resources/InstallDbeaver/Dbeaver2.png)

Далее вам необходимо определиться кому будет доступен для запуска DBeaver. Если ваш ПК используют несколько пользователей под разными учетными записями и вы не хотите чтобы они видели установленный DBeaver у себя - выбирайте “For me (User)” и нажмите “Далее >”.

Если вы хотите дать доступ всем пользователям - выберите“For anyone who uses this computer (all users)” и нажмите “Далее >” (для продолжения потребуются права администратора - жмем “Да”).

Далее вам необходимо поставить галочки напротив следующих пунктов (смотрим на скриншоте):


![Выставляем Dbeaver Community, Include Java, Associate .SQL files](/sql-main/resources/InstallDbeaver/Dbeaver3.png)

После чего нам необходимо выбрать папку установки Dbeaver (желательно использовать предложенную). Нажимаем “Далее >”

![Выбираем путь установки DBeaver](/sql-main/resources/InstallDbeaver/Dbeaver4.png)

В следующем окне жмем “Установить”.

![Нажимаем установить](/sql-main/resources/InstallDbeaver/Dbeaver5.png)

Далее инсталлятору потребуется некоторое время для установки, по окончанию нажимаем “Finish” или “Завершить”.

Поздравляю, вы установили Dbeaver. Процесс его настройки продолжим после установки PostgreSQL Server.

**Дополнительный вариант установки (portable version):**

Для использования программы с внешнего накопителя (portable version) её лучше всего скачать в виде архива. К примеру, для Windows жмём на ссылку Windows 64 bit (zip archive). Portable версию скачиваете и запускаете, ее устанавливать не нужно.

![Portable Version (Windows(zip))](/sql-main/resources/InstallDbeaver/PortableDBeaver.png)

Для запуск Portable версии необходимо разархивировать скачанный zip - архив в удобное для вас место, после чего зайти в папку dbeaver и запустить dbeaver.exe.

![Запусктите dbeaver.exe в разархивированной папке](/sql-main/resources/InstallDbeaver/PortableDBeaver1.png)

Если вам достаточно Portable версии - переходите к установке и настройке PostgreSQL Server (описано ниже). Если вы слабо разбираетесь в ПО - советуем установить стандартную версию DBeaver.

<a name="установка-postgresql-server"></a>

### Установка PostgreSQL Server

**Скачайте Database Server PostgreSQL версии 12.х** по ссылке в зависимости от Вашей операционной системы: https://www.enterprisedb.com/downloads/postgres-postgresql-downloads


![Выбирайте версию выше 12 для вашей ОС](/sql-main/resources/InstallPostgreSQLServer/PostgreSQLDownload.png)

Запустите скачанный файл (если запросит права администратора, нажмите “Да”).

В случае отсутствия установленного на компьютере Microsoft Visual C++, установка произойдет автоматически, данный компонент необходим для работы сервера.

![Установка MVC](/sql-main/resources/InstallPostgreSQLServer/MVC.png)

Далее произойдет открытие инсталлятора PostgreSQL Server, необходимо нажать “Next”

![Нажимаем Next >](/sql-main/resources/InstallPostgreSQLServer/PostgreSQL1.png)

Выберите необходимый путь установки (лучше использовать предложенный)

![Выберите путь установки](/sql-main/resources/InstallPostgreSQLServer/PostgreSQL2.png)

Далее выберите следующие пункты, изображенные на скриншоте

![Выбираем PostgreSQL Server + Command Line Tools](/sql-main/resources/InstallPostgreSQLServer/PostgreSQL3.png)


Выберите место хранения PostgreSQL Server (лучше использовать стандартное)

![Выбираем место хранения PostgreSQL Server](/sql-main/resources/InstallPostgreSQLServer/PostgreSQL4.png)

Укажите пароль, он потребуется при создании подключения и нажмите Next. Если запроса на создание пароля нет, значит PostgreSQL Database Server уже был установлен ранее.

**Внимание:** Этот пароль очень важен, т.к. в случае его утраты вы потеряете доступ к серверу PostgreSQL и придется осуществлять переустановку.

![Указываем пароль](/sql-main/resources/InstallPostgreSQLServer/PostgreSQL5.png)

Введите номер порта для подключения к серверу и нажмите Next (введите 5432, он считается стандартным):

![Указываем порт подключения к серверу](/sql-main/resources/InstallPostgreSQLServer/PostgreSQL6.png)

Нажмите Next

![Нажимаем Next](/sql-main/resources/InstallPostgreSQLServer/PostgreSQL7.png)

Нажмите Next

![Нажимаем Next](/sql-main/resources/InstallPostgreSQLServer/PostgreSQL8.png)

Нажмите Next и дождитесь окончания установки

![Нажимаем Next](/sql-main/resources/InstallPostgreSQLServer/PostgreSQL9.png)

Нажмите Finish

![Нажимаем Next](/sql-main/resources/InstallPostgreSQLServer/PostgreSQL10.png)

Зайдите в Процессы Диспетчера задач (правая кнопка мыши на панели задач -> диспетчер задач) и убедитесь, что сервер запущен. В случае отсутствия, проверьте, что отображаются процессы для “всех пользователей”

![Проверяем в диспетчере задач наличие процессов PostgreSQL Server](/sql-main/resources/InstallPostgreSQLServer/PostgreSQL11.png)

Поздравляю, вы установили PostgreSQL Server и полностью настроили текущую базу для загрузки бекапа (рассмотрим ниже).

Также полный процесс ручной установки PostgreSQL Database Server рассмотрен в следующем видео: https://letsdocode.ru/sql-main/localserver.mp4


<a name="загрузка-базы-из-бекапа-dvd-rental"></a>

### Загрузка базы из бекапа dvd-rental


Запустите DBeaver и нажмите на кнопку “Новое соединение”

![Открываем DBeaver и нажимаем кнопку "Новое соединение"](/sql-main/resources/Backup/Backup1.png)

Выберите PostgreSQL и нажмите Далее

![Выбираем PostgreSQL](/sql-main/resources/Backup/Backup2.png)

В поле Пароль укажите тот пароль, **который указывали при установке PostgreSQL Database Server**, локальный клиент выберите PostgreSQL 10.11 или PostgreSQL Binaries, все остальные данные остаются без изменений. Нажмите Тест соединения.

![Указываем параметры подключения](/sql-main/resources/Backup/Backup3.png)

Dbeaver предложит скачать необходимые драйвера, нажмите Скачать

![Скачиваем необходимые драйвера](/sql-main/resources/Backup/Backup4.png)

Появится окно об успешном прохождении теста, нажмите ОК

![Нажимаем готово](/sql-main/resources/Backup/Backup5.png)

На запрос о создании образца базы данных выберите Нет

![Нажимаем "Нет"](/sql-main/resources/Backup/Backup6.png)

В левой части окна будет доступно подключение с пустой базой данных

![Папка с БД](/sql-main/resources/Backup/Backup7.png)

Нажмите на иконку “папки”

![Экран восстановления](/sql-main/resources/Backup/Backup8.png)

Выберите файл бэкапа базы данных, который заранее скачали по ссылке: https://drive.google.com/file/d/1p3CM1Foye-fX695COvfq70YeIRA-a6XR/view?usp=sharing

![Выбираем файл с Backup'ом](/sql-main/resources/Backup/Backup9.png)

Нажмите “Локальный клиент”

![Нажимаем локальный клиент](/sql-main/resources/Backup/Backup10.png)

Выберите клиент PostgreSQL Binaries

![Выберите клиент PostgreSQL Binaries](/sql-main/resources/Backup/Backup11.png)

Нажмите Старт

![Нажмите Старт](/sql-main/resources/Backup/Backup12.png)

По окончании восстановления нажмите ОК
Иногда Восстановление может закончится ошибкой с кодом 1, это связано с разницей в версиях ПО и ОС, фактически база полностью восстановлена и работоспособна. База dvd-rental будет расположена в схеме **public**. 

**Важно:** восстановление учебной базы данных по прокату дисков dvd-rental происходит в базу данных postgres и схему public. Никаких объектов с названием dvd-rental создано не будет.

![Нажмите OK](/sql-main/resources/Backup/Backup13.png)

Нажмите Закрыть

![Нажмите Закрыть](/sql-main/resources/Backup/Backup14.png)

Теперь у Вас локально установлен сервер PostgreSQL и все необходимые базы данных для прохождения курса!

![Список схем в БД](/sql-main/resources/Backup/Backup15.png)



<a name="ручное-добавление-jar-драйвера-для-работы-с-бд"></a>

### Ручное добавление JAR драйвера для работы с БД

При необходимости (ошибки, отсутствие установленного драйвера для работы с БД и т.п.) мы можем вручную установить указанный JDBC драйвер в формате JAR файла в DBeaver.

Для этого нужно выполнить следующие шаги:

1. Перейти на официальный сайт PostgreSQL в раздел имеющихся драйверов для установки - https://jdbc.postgresql.org/download.html

2. Выбираем актуальный драйвер для скачивания в столбце JDBC 4.2

![Выбираем нужную нам версию](/sql-main/resources/jarInstall/Jar1.png)

3. Сохраняем его на компьютер в место, которое вам необходимо (**Внимание:** Желательно его сохранить туда, где вы его не удалите, т.к. он будет использоваться для подключения к БД).

4. Открываем DBeaver и переходим в раздел “База данных” - “Управление драйверами” 

![Открываем база данных - управление драйверами](/sql-main/resources/jarInstall/Jar2.png)

5. Необходимо выбрать PostgreSQL, после чего перейти в раздел библиотеки. Далее необходимо удалить все имеющиеся библиотеки, после чего нажать кнопку “Добавить файл” и указать путь к загруженному ранее JAR файлу JDBC драйвера 

![Выполняем установку JAR файла](/sql-main/resources/jarInstall/Jar3.png)

6. Нажимаем ОК в редактировании драйвера PostgreSQL, а затем закрыть в менеджере драйверов. JDBC драйвер успешно установлен! Далее необходимо проверить соединение к базе данных, чтобы удостоверится что драйвер отрабатывает корректно.

<a name="ручное-добавление-локального-клиента-в-dbeaver"></a>

### Ручное добавление локального клиента в DBeaver

Полный процесс установки локального клиента в DBeaver рассмотрен в следующем видео: https://letsdocode.ru/sql-main/localclient.mp4


<a name="ручной-экспорт-результатов-из-dbeaver-в-excel"></a>

### Ручной экспорт результатов из DBeaver в Excel

Полный процесс создания экспорта результатов из DBeaver в Excel рассмотрен в следующем видео: https://letsdocode.ru/sql-main/localserver.mp4


<a name="ручное-восстановление-дампа-если-dbeaver-завис"></a>

### Ручное восстановление дампа, если DBeaver завис

Полный процесс ручного восстановления дампа рассмотрен в следующем видео: https://letsdocode.ru/sql-main/dump_restore.mp4

<a name="подключение-к-облачной-базе-данных"></a>

### Подключение к облачной базе данных

Данные для подключения к облачной базе:

| Хост         | 51.250.106.132                                                                                                  |
|--------------|-----------------------------------------------------------------------------------------------------------------|
| Порт         | 19001                                                                                                           |
| База данных  | **postgres** - основная бд (только чтение) **workplace** - для выполнения домашнего задания по 4 лекции и экспериментов |
| Пользователь | netology                                                                                                        |
| Пароль       | NetoSQL2019                                                                                                     |

Настройка соединения аналогична той, которую вы используете при подключении к локальной базе данных (описано выше).

При работе в общей облачной базе данных (workplace) вы создаёте под себя новую схему (щелчок по правой кнопки мыши на папке «Схемы») и в ней работаете: если создаёте схему, то делаете префикс с фамилией — create schema lecture_4_фамилия (лучше указывать фамилию на английском, например: create table author_ivanova).

![Подключение к БД](/sql-main/resources/ConnectDB.png)

<a name="установка-на-macos"></a>

### Установка на MacOS

Установка программного обеспечения на MacOS ничем не отличается от установки на ОС Windows.

Основная проблема, которая возникает - это DBeaver не видит нативного клиента PostgreSQL. 

Для этого в настройках соединения

![Открываем настройки соединения](/sql-main/resources/MacOS/Mac1.png)

или в настройках восстановления

![Открываем настройки восстановления](/sql-main/resources/MacOS/Mac2.png)

необходимо нажать на “локальный клиент” / “Client…” и во всплывающем меню выбрать пункт “Выбрать”

![Выбираем клиент](/sql-main/resources/MacOS/Mac3.png)

Нажать кнопку “Добавить” и указать путь к папке с PostgreSQL.
Чтобы найти верный путь в программе Finder в поиске задайте PostgreSQL. Как правило путь выглядит **/Library/PostgreSQL/версия_программы/bin**

Чтобы была возможность указать самостоятельно путь, нужно нажать комбинацию **shift+command+G**

Указываете данный путь и нажимаете “Выбор папки”, после этого в окне “Клиенты БД” появится нужный клиент. Обратите внимание, что все поля должны быть заполнены, если это не так, значит путь указан не верно.

![Итоговые настройки](/sql-main/resources/MacOS/Mac4.png)

Нажимаете “ОК” и можете приступать к работе.

<a name="восстановление-пароля"></a>

### Восстановление пароля

Если пароль для непривилегированного аккаунта был каким-либо образом утерян, то его легко можно восстановить, зайдя на сервер под пользователем postgres и просто установив новый пароль взамен утерянного.

Если же был утерян пароль от пользователя postgres, то для его восстановление необходимо выполнить следующие действия:

*Без локального доступа к СУБД изменить пароль не получиться, поэтому все описанные ниже шаги необходимо выполнять локально на самом сервере СУБД.*

1. Зайти в папку с PostgreSQL, где находится файл конфигурации, например: 
C:\Program Files\PostgreSQL\12\data
2. Изменить файл pg_hba.conf так, чтобы можно было зайти на локальную СУБД без пароля
```bash
host  postgres   postgres  127.0.0.1/32    trust
```

3. Перезагрузить настройки сервера.

```bash
Пуск -> Службы -> postgresql-x64-12 - PostgreSQL Server 12 -> Перезапустить
```

4. Зайти на сервер через консоль под стандартным суперпользователем postgres или использовать DBeaver, где в настройках подключения указать логин postgres, а поле пароля оставить пустым.

```bash
psql -U postgres -h 127.0.0.1
```

5. Сменить утерянный пароль для суперпользователя

```sql
ALTER ROLE superuser PASSWORD 'secret';
```

6. Закомментировать строку в pg_hba.conf

```bash
host  postgres   postgres  127.0.0.1/32    trust
```

7. Перезагрузить настройки сервера

```bash
Пуск -> Службы -> postgresql-x64-12 - PostgreSQL Server 12 -> Перезапустить
```
В результате выполнения всех вышеперечисленных шагов доступ пользователя к базе данных будет восстановлен.
