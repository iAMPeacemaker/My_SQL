# Выполнение заданий в рамках курса Базы данных и SQL

---

***- Клонируйте репозиторий:***
```
git clone git@github.com:nikoeremeev/MySQL_scripts.git
```

---
## Семинар №1. Установка СУБД, подключение к БД, просмотр и создание таблиц

### Задание 1. Создайте таблицу с мобильными телефонами, используя графический интерфейс. Заполните БД данными.  

### Задание 2. Выведите название, производителя и цену для товаров, количество которых превышает 2.  

### Задание 3. Выведите весь ассортимент товаров марки “Samsung”.  
### Задание 4*. С помощью регулярных выражений найти:
    4.1. Товары, в которых есть упоминание "Iphone";
    4.2. "Samsung";
    4.3. Товары, в которых есть ЦИФРЫ;
    4.4. Товары, в которых есть ЦИФРА "8".

---
## Семинар №2. SQL – создание объектов, простые запросы выборки

### Задание 1. Используя операторы языка SQL, создайте табличку “sales”. Заполните ее данными.

### Задание 2. Сгруппируйте значений количества в 3 сегмента — меньше 100, 100-300 и больше 300.

### Задание 3. Создайте таблицу “orders”, заполните ее значениями. Покажите “полный” статус заказа, используя оператор CASE.

---
## Семинар №3. SQL – выборка данных, сортировка, агрегатные функции

    ТАБЛИЦА 1: ПРОДАВЦЫ (SALESPEOPLE)
----------------------------------------------
snum | sname | city | comm
--------|-----------|--------------|----------
1001 | Peel | London | .12
1002 | Serres | San Jose | .13
1004 | Motika | London | .11
1007 | Rifkin | Barcelona | .15
1003 | Axelrod | New York | .10
---------------------------------------------

    ТАБЛИЦА 2: ЗАКАЗЧИКИ (CUSTOMERS)
----------------------------------------------
cnum | cname | city | rating | snum
-------|------------|---------|--------|------
2001 | Hoffman | London | 100 | 1001
2002 | Giovanni | Rome | 200 | 1003
2003 | Liu | SanJose | 200 | 1002
2004 | Grass | Berlin | 300 | 1002
2006 | Clemens | London | 100 | 1001
2008 | Cisneros | SanJose | 300 | 1007
2007 | Pereira | Rome | 100 | 1004
----------------------------------------------

    ТАБЛИЦА 3: ЗАКАЗЫ (ORDERS)
-----------------------------------------------
onum | amt | odate | cnum | snum
-------|-----------|-------------|------|------
3001 | 18.69 | 10/03/1990 | 2008 | 1007
3003 | 767.19 | 10/03/1990 | 2001 | 1001
3002 | 1900.10 | 10/03/1990 | 2007 | 1004
3005 | 5160.45 | 10/03/1990 | 2003 | 1002
3006 | 1098.16 | 10/03/1990 | 2008 | 1007
3009 | 1713.23 | 10/04/1990 | 2002 | 1003
3007 | 75.75 | 10/04/1990 | 2004 | 1002
3008 | 4723.00 | 10/05/1990 | 2006 | 1001
3010 | 1309.95 | 10/06/1990 | 2004 | 1002
3011 | 9891.88 | 10/06/1990 | 2006 | 1001
-----------------------------------------------

### Задания ЧАСТЬ 1

1. Напишите запрос, который вывел бы таблицу со столбцами в следующем порядке: city, sname, snum, comm. (к первой или второй таблице, используя SELECT).
2. Напишите команду SELECT, которая вывела бы оценку(rating), сопровождаемую именем каждого заказчика в городе San Jose. (“заказчики”).
3. Напишите запрос, который вывел бы значения snum всех продавцов из таблицы заказов без каких бы то ни было повторений. (уникальные значения в “snum“ “Продавцы”).
4. (*) Напишите запрос, который бы выбирал заказчиков, чьи имена начинаются с буквы G. Используется оператор "LIKE": (“заказчики”) 
5. Напишите запрос, который может дать вам все заказы со значениями суммы выше чем $1,000 (“Заказы”, “amt” - сумма).
6. Напишите запрос который выбрал бы наименьшую сумму заказа. (Из поля “amt” - сумма в таблице “Заказы” выбрать наименьшее значение).
7. Напишите запрос к таблице “Заказчики”, который может показать всех заказчиков, у которых рейтинг больше 100 и они находятся не в Риме.

### Задания ЧАСТЬ 2 (Таблица для работы из семинара)

1. Отсортируйте поле “зарплата” в порядке убывания и возрастания.
2. Отсортируйте по возрастанию поле “Зарплата” и выведите 5 строк с наибольшей заработной платой.
3. Выполните группировку всех сотрудников по специальности, суммарная зарплата которых превышает 100000.

---
## Семинар №4. SQL – работа с несколькими таблицами

### Задание 1. Вывести на экран сколько машин каждого цвета для машин марок BMW и LADA.


### Задание 2. Вывести на экран марку авто и количество AUTO не этой марки.

### Задание 3. Даны 2 таблицы, созданные следующим образом:  
    create table test_a (id number, data varchar2(1));
    create table test_b (id number);
    insert into test_a(id, data) values
    (10, 'A'),
    (20, 'A'),
    (30, 'F'),
    (40, 'D'),
    (50, 'C');
    insert into test_b(id) values
    (10),
    (30),
    (50);
*   Напишите запрос, который вернет строки из таблицы test_a, id которых нет в таблице test_b, НЕ используя ключевого слова NOT.

---
## Семинар №5. SQL – оконные функции

### Задание 1. Таблица Cars:
    mysql> SELECT * FROM Cars;
-----------------------------------------------
 Id | Name       | Cost   
-------|-----------|-------------
  1 | Audi       |  52642 
  2 | Mercedes   |  57127 
  3 | Skoda      |   9000 
  4 | Volvo      |  29000 
  5 | Bentley    | 350000 
  6 | Citroen    |  21000 
  7 | Hummer     |  41400 
  8 | Volkswagen |  21600 
-----------------------------------------------

### Задание 1.1. Создайте представление, в которое попадут автомобили стоимостью до 25 000 долларов.  

### Задание 1.2. Изменить в существующем представлении порог для стоимости: пусть цена будет до 30 000 долларов (используя оператор ALTER VIEW).

### Задание 1.3. Создайте представление, в котором будут только автомобили марки “Шкода” и “Ауди”.

### Задание 2. Вывести название и цену для всех анализов, которые продавались 5 февраля 2020 и всю следующую неделю. (таблицы см. в презентации).
*    Есть таблица анализов Analysis:  
    an_id — ID анализа;  
    an_name — название анализа;  
    an_cost — себестоимость анализа;  
    an_price — розничная цена анализа;  
    an_group — группа анализов.
*    Есть таблица групп анализов Groups:  
    gr_id — ID группы;  
    gr_name — название группы;  
    gr_temp — температурный режим хранения.
*    Есть таблица заказов Orders:  
    ord_id — ID заказа;  
    ord_datetime — дата и время заказа;  
    ord_an — ID анализа.


### Задание 3. Добавьте новый столбец под названием «время до следующей станции». 
    Чтобы получить это значение, мы вычитаем время станций для пар смежных станций. Мы можем вычислить это значение без использования оконной функции SQL, но это может быть очень сложно. Проще это сделать с помощью оконной функции LEAD. Эта функция сравнивает значения из одной строки со следующей строкой, чтобы получить результат. В этом случае функция сравнивает значения в столбце «время» для станции со станцией сразу после нее. (таблицы см. в презентации).  
*   ![Задание3](s5t3.png)

---
## Семинар №6. SQL – Транзакции. Временные таблицы, управляющие конструкции, циклы

### Задание 1. Создайте функцию, которая принимает кол-во сек и форматирует их в кол-во дней, часов, минут и секунд.  
    Пример: 123456 ->'1 days 10 hours 17 minutes 36 seconds '

### Задание 2.	Выведите только четные числа от 1 до 10 включительно.  
    Пример: 2,4,6,8,10 (можно сделать через шаг +  2: х = 2, х+=2)


