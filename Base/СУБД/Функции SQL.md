202201131003
Tags:
___
# Функции SQL

## Функция COUNT()
Оператор SQL COUNT() — функция возвращающая количество записей (строк) таблицы. Запись функции с указанием столбца (синтаксис ниже) вернет количество записей конкретного столбца за исключением NULL записей.
Функция SQL COUNT() имеет следующий синтаксис:
```sql
COUNT(column_name)
```
Запись функции с указанием маски «\*» вернет количество всех записей в таблице.
Синтаксис:
```sql
COUNT(*)
```

### Пример

#### Имеется следующая таблица Universities:

| **ID** | **UniversityName**                      | **Students** | **Faculties** | **Professores** | **Location**     | **Site** |
| ------ | --------------------------------------- | ------------ | ------------- | --------------- | ---------------- | -------- |
| 1      | Perm State National Research University | 12400        | 12            | 1229            | Perm             | psu.ru   |
| 2      | Saint Petersburg State University       | 21300        | 24            | 13126           | Saint-Petersburg | spbu.ru  |
| 3      | Novosibirsk State University            | 7200         | 13            | 1527            | Novosibirsk      | nsu.ru   |
| 4      | Moscow State University                 | 35100        | 39            | 14358           | Moscow           | msu.ru   |
| 5      | Higher School of Economics              | 20335        | 12            | 1615            | Moscow           | hse.ru   |
| 6      | Ural Federal University                 | 57000        | 19            | 5640            | Yekaterinburg    | urfu.ru  |
| 7      | National Research Nuclear University    | 8600         | 10            | 936             | Moscow           | mephi.ru |

**Пример 1.** Вывести число записей таблицы, используя оператор SQL COUNT:
```sql
SELECT COUNT(*) FROM Universities
```
_Ответ: 7_


**Пример 2.** Найти количество университетов расположенных в Москве, используя оператор SQL COUNT:

```sql
SELECT COUNT(*) FROM Universities WHERE Location = 'Moscow'
```
_Ответ: 3_

**Пример 3.** Найти количество университетов с больше чем 20 факультетами, используя оператор SQL COUNT:
```sql
SELECT COUNT(*) FROM Universities WHERE Faculties > 20
```
_Ответ: 2_


## Функция AVG()
Оператор SQL AVG() — Функция возвращающая среднее значение столбца. Применима только для числовых столбцов!
Функция SQL AVG() имеет следующий синтаксис:
```sql
AVG(column_name)
```

### Пример
[[Функции SQL#Имеется следующая таблица Universities|таблица Universities]]

**Пример 1.** Используя оператор SQL AVG найти среднее число студентов (Students) всех университетов:

```sql
SELECT AVG(Students)
FROM Universities
```
_Ответ: 23133_

**Пример 2.** Используя оператор SQL AVG найти среднее число факультетов (Faculties) в университетах Москвы:

```sql
SELECT AVG(Faculties)
FROM Univetsities
WHERE Location ='Moscow'
```
_Ответ: 20_

## Функция MIN()
Оператор SQL MIN() — функция возвращающая минимальное значение столбца.
Функция SQL MIN() имеет следующий синтаксис:
```sql
MIN(column_name)
```
### Пример
[[Функции SQL#Имеется следующая таблица Universities|таблица Universities]]
**Пример 1.** Используя оператор SQL MIN найти минимальное значение столбца Professores:
```sql
SELECT MIN(Professores)
FROM Universities
```
_Ответ: 936_

**Пример 2.** Используя оператор SQL MIN найти минимальное значение колонки Students, где расположение университета (Location) — Moscow:
```sql
SELECT MIN(Students)
FROM Universities
WHERE Location ='Moscow'
```
_Ответ: 8600_

**Пример 3.** Используя оператор SQL MIN найти город (Location), в университете меньше всего студентов (Students):
```sql
SELECT Location
FROM Universities
WHERE Students = ( SELECT MIN(Students) FROM Universities)
```
_Ответ: Novosibirsk_


## Функция MAX()
Оператор SQL MAX() — функция возвращающая максимальное значение столбца таблицы.
Функция SQL MAX() имеет следующий синтаксис:
```sql
MAX(column_name)
```

## Функция SUM()
Оператор SQL SUM() — функция, возвращающая сумму значений столбца таблицы. Используется только для числовых столбцов.
Функция SQL SUM() имеет следующий синтаксис:
```sql
`SUM( [ALL|DISTINCT] expression )
```
Параметр **ALL** — является параметром по умолчанию. Считается сумма всех строк.
При указании параметра **DISTINCT** — происходит подсчет только уникальных значений.

## Функция ROUND()
Оператор SQL ROUND() — функция для округления десятичных чисел. Работает только с числовыми столбцами или произвольными вещественными числами.
Функция SQL ROUND() имеет следующий синтаксис:
```sql
ROUND(expression, length)
```
*expression* — название столбца или столбцов, а так же вещественное число.
*length *— указывает точность округления для числа.


## Функция UCASE()
Оператор SQL UCASE() — функция, возвращающая значения столбца или столбцов в верхнем регистре букв.
Функция SQL UCASE() имеет следующий синтаксис:
```sql
UCASE(column_name)
```

>В СУБД **MS SQL Server** аналогом оператора SQL UCASE() является функция UPPER с тем же синтаксисом.

## Функция LCASE()
Оператор SQL LCASE() — функция, возвращающая значения столбца или столбцов в нижнем регистре букв.
Функция SQL LCASE() имеет следующий синтаксис:
```sql
LCASE(column_name)
```
>В СУБД **MS SQL Server** аналогом оператора SQL LCASE() является функция LOWER с тем же синтаксисом.

## Функция LEN()
Оператор SQL LEN() — функция, возвращающая длину значения в поле записи.
Функция SQL LEN() имеет следующий синтаксис:
```sql
LEN(column_name)
```

>Функция SQL LEN() исключает из подсчета конечные пробелы.

## Функция MID()
Оператор SQL MID() — функция, выводящая определенное количество символов текстового поля таблицы.
Функция SQL MID() имеет следующий синтаксис:

```sql
MID(colunm_name,start [,length])
```

Параметр **start** задает позицию начального символа.
Параметр **length** устанавливает количество символов для вывода начиная с позиции, указанной в параметре **start**.

## Функция NOW()
Оператор SQL NOW() — функция, возвращающая системное время и дату.
Функция SQL NOW() имеет следующий синтаксис:
```sql
NOW()
```
### Пример
[[Функции SQL#Имеется следующая таблица Universities|таблица Universities]]
**Пример 1.** Вывести сколько на текущий момент студентов обучается в каждом университете. используя оператор SQL NOW:
```sql
SELECT UniversityName, Students, NOW() AS CurDate FROM Universities
```
_Результат:_

| **UniversityName** | **Students** | **CurDate** |
| --- | --- | --- |
| Perm State National Research University | 12400 | 6/26/2013 2:11:07 PM |
| Saint Petersburg State University | 21300 | 6/26/2013 2:11:07 PM |
| Novosibirsk State University | 7200 | 6/26/2013 2:11:07 PM |
| Moscow State University | 35100 | 6/26/2013 2:11:07 PM |
| Higher School of Economics | 20335 | 6/26/2013 2:11:07 PM |
| Ural Federal University | 57000 | 6/26/2013 2:11:07 PM |
| National Research Nuclear University | 8600 | 6/26/2013 2:11:07 PM |


## Функция  FIRST()
Оператор SQL FIRST() — функция, возвращающая первое значение столбца или столбцов таблицы.
>**Используется только в СУБД MS Access!**
Функция SQL FIRST() имеет следующий синтаксис:
```sql
FIRST (column_name)
```
>Аналогом функции SQL FIRST() для **MySQL** будет оператор LIMIT. Для **MS SQL Server** оператор TOP. Для **Oracle** оператор ROWNUM. https://unetway.com/tutorial/sql-predlozenie-select-top

### Пример
**Примеры оператора SQL LAST.** Имеется следующая таблица Planets:

| **ID** | **PlanetName** | **Radius** | **SunSeason** | **OpeningYear** | **HavingRings** | **Opener** |
| --- | -------- | --- | --- | --- | --- | --- |
| 1 | Mars | 3396 | 687 | 1659 | No | Christiaan Huygens |
| 2 | Saturn | 60268 | 10759.22 | — | Yes | — |
| 3 | Neptune | 24764 | 60190 | 1846 | Yes | John Couch Adams |
| 4 | Mercury | 2439 | 115.88 | 1631 | No | Nicolaus Copernicus |
| 5 | Venus | 6051 | 243 | 1610 | No | Galileo Galilei |

**Пример 1.** Используя оператор SQL FIRST вывести первое значение столбца PlanetName:
Решение для **MS Access:**

```sql
SELECT FIRST (PlanetName)
FROM Planets
```

Решение для **MySQL:**

```sql
SELECT PlanetName
FROM Planets
ORDER BY PlanetName ASC
LIMIT 1
```

Решение для **MS SQL Server:**

```sql
SELECT TOP 1 PlanetName
FROM Planets
ORDER BY PlanetName ASC
```

Решение для **Oracle:**

```sql
SELECT PlanetName
FROM Planets
ORDER BY PlanetName AS
WHERE ROWNUM <=1
```

_Результат:_

| **PlanetName** |
| --- |
|Mars  |

## Функция LAST()

Оператор SQL LAST() — функция, возвращающая последнее значение столбца или столбцов таблицы.

>**Используется только в СУБД MS Access!**

Функция SQL LAST() имеет следующий синтаксис:

```sql
LAST(column_name)
```

>Аналогом функции SQL LAST() для **MySQL** будет [[оператор LIMIT]]. Для **MS SQL Server**[ [оператор TOP]]. Для **Oracle** [[оператор ROWNUM]].

### Пример
**Примеры оператора SQL LAST.** Имеется следующая таблица Planets:

| **ID** | **PlanetName** | **Radius** | **SunSeason** | **OpeningYear** | **HavingRings** | **Opener** |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | Mars | 3396 | 687 | 1659 | No | Christiaan Huygens |
| 2 | Saturn | 60268 | 10759.22 | — | Yes | — |
| 3 | Neptune | 24764 | 60190 | 1846 | Yes | John Couch Adams |
| 4 | Mercury | 2439 | 115.88 | 1631 | No | Nicolaus Copernicus |
| 5 | Venus | 6051 | 243 | 1610 | No | Galileo Galilei |


**Пример 1.** Используя оператор SQL LAST вывести последнее значение столбца Opener:

Решение для **MS Access**:

```sql
SELECT LAST (Opener)
FROM Planets
```

Решение для **MySQL:**

```sql
SELECT Opener
FROM Planets
ORDER BY Opener DESC
LIMIT 1
```

Решение для **MS SQL Server:**
```sql
SELECT TOP 1 Opener
FROM Planets
ORDER BY Opener DESC
```

Решение для **Oracle:**
```sql
SELECT Opener
FROM Planets
ORDER BY Opener DESC
WHERE ROWNUM <= 1
```

_Результат:_

| **Opener** |
| --- |
| Galileo Galilei |



















# Ссылки
___
##### Links


---
##### Источники




































        