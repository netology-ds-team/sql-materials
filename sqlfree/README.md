# Инструкция по установке ПО

*Версии программ, указанные в данной инструкции, могут отличаться от представленных на сайтах разработчиков программных продуктов. 
Выбирайте стабильные версии, соответствующие требованиям Вашей системы и характеристикам Вашей машины.*

**Данные для подключения к облачной базе:**

Параметр | Значение 
--- | ---
Хост | 84.201.152.11
Порт | 19001
База данных | postgres
Пользователь | netology
Пароль | NetoSQL2019

## Установка DBeaver

Для подключения к учебной облачной базе данных нужно скачать и установить **DBeaver** — клиентское приложение для управления СУБД, которое дает возможность
администрировать структуру БД, выполнять запросы на SQL, получать результаты запросов, импортировать и экспортировать данные и т. д.

1\. Переходим по ссылке на [сайт сообщества DBeaver](https://dbeaver.io/download/)

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/1.png)

2\. Выбираем **Community Edition** версию программы в соответствии с Вашей операционной системой, которая должна иметь разрядность *64 бита*.
Скачиваете либо установочный файл, либо *zip* архив. Архив содержит *portable версию*, которую не нужно устанавливать.

3\. Если Ваша операционная система имеет разрядность 32 бита, переходите по [ссылке](https://dbeaver.io/files/6.0.0/) и скачиваете установочный файл в 
соответствии с Вашей операционной системой 

4\. После того, как установочный файл скачан - запускаете его.

4.1. Выбираете язык установки

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/2.png)

4.2. Нажимаете “Далее”

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/3.png)

4.3. Нажимаете “Принимаю”

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/4.png)

4.4. Нажимаете “Далее”

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/5.png)

4.5. Выбираете *DBeaver Community* и *Java* и нажимаете “Далее”. Если пункта *Java* нет, значит данный компонент уже установлен

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/6.png)

4.6. Выбираете пть установки или оставляете по умолчанию и нажимаете “Далее”

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/7.png)

4.7. Нажимаете “Установить”

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/8.png)

4.8. По окончанию установки можете указать "Создать ярлык на рабочем столе" и нажимаете “Готово”

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/9.png)

## Подключение к облачной базе

5\. После того, как **DBeaver** был установлен, запускаете его

5.1. В верхнем левом углу нажимаете на кнопку "Новое соединение"

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/10.png)

5.2. Выбираете PostgreSQL и нажимаете "Далее"

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/11.png)

5.3. Заполняете реквизиты подключения. Указываете хост, порт, название базы данных, имя пользователя и пароль согласно таблицы, в начале инструкции

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/12.png)

5.4. Нажимаете "Тест соединения", DBeaver попросит скачать драйвера - соглашаетесь и если все данные были указаны корректно, получите следующий результат

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/13.png)

5.5. Нажимаете "Ок", закрываете окно с настройками подключения и слева будет отображено подключение

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/14.png)

## Работа со схемами

6\. Уже существующая схема public только для чтения, ничего изменять / добавлять / удалять в ней не получится согласно прав доступа.

6.1. Раскрываете подключение, раскрываете базу данных *postgres*, раскрываете *схемы*.

Скриншот сделан на чистой и свежей базе, до того, как учащиеся стали создавать свои собственные схемы.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/15.png)

6.2. Нажимаете правую кнопку мыши на *Схемы* и выбираете "Создать объект Схема"

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/16.png)

6.3. В "Название схемы" указываете свою фамилию и инициалы, можете добавить еще какие-то символы, что бы идентифицировать новую схему, как свою. Если схема с таким названием уже существует, значит нужно придумать что-то новое.

**В разделе "Владелец" нужно обязательно выбрать netology.** И нажимаете "Ок".

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/17.png)

Данная схема будет нужна для выполнения одного из заданий и для самостоятельной практики на создание сущностей базы данных.

6.4. Для того, что бы начать писать запросы к учебным данным, нужно нажать правую кнопку мыши на схеме *public* и выбрать "Редактор SQL" -> "Новый редактор SQL"

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/18.png)

6.5. Что бы переключаться между схемами, можно использовать верхнее меню. В левом меню выбираете подключение (если их несколько), в правом меню выбираете схему, к которой будете писать запросы.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/19.png)

## Восстановление бэкапа с данными в свою схему

7\. Нужно скачать [дамп учебной базы данных](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/dump.sql)

Нажимаете правую кнопку мыши на "View raw" и выбираете "Сохранить ссылку как"

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/28.png)

7.1. Открываете файл в любом текстовом редакторе (блокнот будет отличным вариантом) и выбираете "Заменить". В поле "Что заменить" копируете фразу **ЗАМЕНИТЬ_НА_НАЗВАНИЕ_СВОЕЙ_СХЕМЫ**, в поле чем заменить - название схемы, которую создали. Нажимаете **"Заменить все"**.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/20.png)

7.2. Если все сделали верно, то в файле будет отображаться нужное название. После сохраняете файл и закрываете его.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/21.png)

7.3. Открываете DBeaver, раскрываете подключение к облачной машине, нажимаете правую конпку мыши на названии базы данных *postgres*, выбираете "Инструменты" -> "Выполнить скрипт".

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/22.png)

7.4. В поле "Входной файл" выбираете измененный дамп файл и нажимаете "Старт"

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/23.png)

7.5. Начнется процесс восстановления данных, который может занять до 15 минут. Можно выпить чай / кофе ;)

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/24.png)

7.6. По окончании восстановления появится следующее окно, нажимаете "Ок".

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/25.png)

7.7. Если окно "Выполнить скрипт" автоматически не закроется, то нажимаете "Отмена"

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/26.png)

7.8. Раскройте схемы, нажмите правую кнопку мыши на "Схемы" и выберите "Обновить". После этого можете открыть редактор SQL к данным в вашей схеме и приступать к написанию запросов.

![](https://github.com/netology-ds-team/sql-materials/blob/main/sqlfree/images/27.png)

### Успешного обучения!
