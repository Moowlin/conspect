202201131433
Tags:
___
# Оператор  ALTER TABLE

Оператор SQL ALTER TABLE используется тогда, когда необходимо внести изменения в структуру уже существующей таблицы.

Оператор SQL ALTER TABLE имеет следующий синтаксис:

```sql
ALTER TABLE table_name
ADD column_name datatype
```

Примеры оператора SQL ALTER TABLE. Имеется следующая таблица Artists:

| Singer | Album | Year | Sale |
| --- | --- | --- | --- |
| The Prodigy | Invaders Must Die | 2008 | 1200000 |
| Drowning Pool | Sinner | 2001 | 400000 |
| Massive Attack | 	Mezzanine | 1998 | 2300000 |


Пример 1. Добавить столбец Producer, используя оператор SQL ALTER TABLE:


```sql
ATLER TABLE Artists ADD Producer varchar(20)
```
В результате, в таблицу Artists будет добавлен столбец Producer:

```sql
SELECT * FROM Artists
```
Результат:

| Singer | Album | Year | Sale | Producer |
| --- | --- | --- | --- | --- |
| The Prodigy | Invaders Must Die | 2008 | 1200000 |  |
| Drowning Pool | Sinner | 2001 | 400000 |  |
| Massive Attack | Mezzanine | 1998 | 2300000 |  |





# Ссылки
___
##### Links


---
##### Источники





































                                                                                                                                                                                           