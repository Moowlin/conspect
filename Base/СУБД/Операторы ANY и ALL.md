202201131416
Tags:
___
# Операторы ANY и ALL
Операторы ANY и ALL используются с предложением [[Оператор WHERE|WHERE]] или [[Оператор HAVING|HAVING]]. Оператор ANY возвращает true, если какое-либо из значений подзапроса соответствует условию. Оператор ALL возвращает true, если все значения подзапроса удовлетворяют условию.



## Синтаксис ANY

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator ANY
(SELECT column_name FROM table_name WHERE condition);
```

### Пример ANY

Оператор ANY возвращает TRUE, если какое-либо из значений подзапроса соответствует условию. Следующий оператор SQL возвращает TRUE и перечисляет имена товаров, если он находит ЛЮБЫЕ записи в таблице info, с количеством = 15:

**Пример:**

```sql
SELECT name
FROM product
WHERE product_id = ANY (SELECT product_id FROM info WHERE counts = 15);
```

Следующий оператор SQL возвращает TRUE и перечисляет имена товаров, если он находит ЛЮБЫЕ записи в таблице info, с количеством > 15:

**Пример:**

```sql
SELECT name
FROM product
WHERE product_id = ANY (SELECT product_id FROM info WHERE counts > 15);
```

## Синтаксис ALL

```sql
SELECT column_name(s)
FROM table_name
WHERE column_name operator ALL
(SELECT column_name FROM table_name WHERE condition);
```



### Пример ALL

Оператор ALL возвращает TRUE, если все значения подзапроса удовлетворяют условию.

Следующий оператор SQL возвращает TRUE и перечисляет имена товаров, если ВСЕ записи в таблице info имеют количество = 7:

**Пример:**

```sql
SELECT name
FROM product
WHERE product_id = ALL (SELECT product_id FROM info WHERE couns =7);
```




# Ссылки
___
##### Links


---
##### Источники












































