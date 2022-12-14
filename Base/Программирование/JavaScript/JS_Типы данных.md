202210311003
Tags:
___
# Типы данных


В JavaScript есть 8 основных типов данных.
Семь из них называют «примитивными» типами данных:
- `number` для любых чисел: целочисленных или чисел с плавающей точкой; целочисленные значения ограничены диапазоном `±(253-1)`.
- `bigint` для целых чисел произвольной длины.
- `string` для строк. Строка может содержать ноль или больше символов, нет отдельного символьного типа.
- `boolean` для `true`/`false`.
- `null` для неизвестных значений – отдельный тип, имеющий одно значение `null`.
- `undefined` для неприсвоенных значений – отдельный тип, имеющий одно значение `undefined`.
- `symbol` для уникальных идентификаторов.
- И один не является «примитивным» и стоит особняком:
- `object` для более сложных структур данных.

## number
```javascript
let n = 123; 
n = 12.345;
```
Числовой тип данных (number) представляет как целочисленные значения, так и числа с плавающей точкой.

Кроме обычных чисел, существуют так называемые «специальные числовые значения», которые относятся к этому типу данных: `Infinity`, `-Infinity` и `NaN`.

`Infinity` представляет собой математическую бесконечность ∞. Это особое значение, которое больше любого числа.

Мы можем получить его в результате деления на ноль:
```javascript
alert( 1 / 0 ); // Infinity
```
Или задать его явно:
```javascript
alert( Infinity ); // Infinity
```

`NaN` означает вычислительную ошибку. Это результат неправильной или неопределённой математической операции, например:
```javascript
alert( "не число" / 2 ); // NaN, такое деление является ошибкой
```
Значение `NaN` «прилипчиво». Любая математическая операция с `NaN` возвращает `NaN`:
```javascript
alert( NaN + 1 ); // NaN 
alert( 3 * NaN ); // NaN 
alert( "не число" / 2 - 1 ); // NaN
```

Если где-то в математическом выражении есть `NaN`, то оно распространяется на весь результат (есть только одно исключение: `NaN ** 0` равно `1`).


## bigint
Тип `BigInt` был добавлен в JavaScript, чтобы дать возможность работать с целыми числами произвольной длины.
Чтобы создать значение типа `BigInt`, необходимо добавить `n` в конец числового литерала:
```javascript
// символ "n" в конце означает, что это BigInt 
const bigInt = 1234567890123456789012345678901234567890n;
```
>В данный момент `BigInt` поддерживается только в браузерах Firefox, Chrome, Edge и Safari, но не поддерживается в IE.

## string
Строка (`string`) в JavaScript должна быть заключена в кавычки.
```javascript
let str = "Привет"; 
let str2 = 'Одинарные кавычки тоже подойдут'; 
let phrase = `Обратные кавычки позволяют встраивать переменные ${str}`;
```

В JavaScript существует три типа кавычек.
1.  Двойные кавычки: `"Привет"`.
2.  Одинарные кавычки: `'Привет'`.
3.  Обратные кавычки: `` `Привет` ``.

Двойные или одинарные кавычки являются «простыми», между ними нет разницы в JavaScript.
Обратные же кавычки имеют расширенную функциональность. Они позволяют нам встраивать выражения в строку, заключая их в `${…}`. Например:
```javascript
let name = "Иван"; 
// Вставим переменную 
alert( `Привет, ${name}!` ); // Привет, Иван! 
// Вставим выражение 
alert( `результат: ${1 + 2}` ); // результат: 3
```
Выражение внутри `${…}` вычисляется, и его результат становится частью строки. Мы можем положить туда всё, что угодно: переменную `name`, или выражение `1 + 2`, или что-то более сложное.
Обратите внимание, что это можно делать только в обратных кавычках. Другие кавычки не имеют такой функциональности встраивания!
```javascript
alert( "результат: ${1 + 2}" ); // результат: ${1 + 2} (двойные кавычки ничего не делают)
```
>В некоторых языках, например C и Java, для хранения одного символа, например `"a"` или `"%"`, существует отдельный тип. В языках C и Java это `char`.
>В JavaScript подобного типа нет, есть только тип `string`. Строка может содержать ноль символов (быть пустой), один символ или множество.


## boolean
Булевый тип (`boolean`) может принимать только два значения: `true` (истина) и `false` (ложь).
Такой тип, как правило, используется для хранения значений да/нет: `true` значит «да, правильно», а `false` значит «нет, не правильно».
```javascript
let nameFieldChecked = true; // да, поле отмечено 
let ageFieldChecked = false; // нет, поле не отмечено
```
Булевые значения также могут быть результатом сравнений:
```javascript
let isGreater = 4 > 1; 
alert( isGreater ); // true (результатом сравнения будет "да")
```

## null

Специальное значение `null` не относится ни к одному из типов, описанных выше.
Оно формирует отдельный тип, который содержит только значение `null`:
```javascript
let age = null;
```
>В JavaScript `null` не является «ссылкой на несуществующий объект» или «нулевым указателем», как в некоторых других языках.
>Это просто специальное значение, которое представляет собой «ничего», «пусто» или «значение неизвестно».

В приведённом выше коде указано, что значение переменной `age` неизвестно.

## undefined
**Тип данных undefined** переменная имеет в тот момент, когда она объявлена, но еще не инициализирована, то есть ее создали, а значение еще не присвоили.
```javascript
let age; 
alert(age); // выведет "undefined"
```
Технически мы можем присвоить значение `undefined` любой переменной:
```javascript
let age = 123; 
// изменяем значение на undefined 
age = undefined; 
alert(age); // "undefined"
```
…Но так делать не рекомендуется. Обычно `null` используется для присвоения переменной «пустого» или «неизвестного» значения, а `undefined` – для проверок, была ли переменная назначена.

## symbol

Тип `symbol` (символ) используется для создания уникальных идентификаторов в объектах.

## object

# Оператор typeof

Оператор `typeof` возвращает тип аргумента. Это полезно, когда мы хотим обрабатывать значения различных типов по-разному или просто хотим сделать проверку.
У него есть две синтаксические формы:

1.  Синтаксис оператора: `typeof x`.
2.  Синтаксис функции: `typeof(x)`.
Другими словами, он работает со скобками или без скобок. Результат одинаковый.

Вызов `typeof x` возвращает строку с именем типа:

```javascript
typeof undefined // "undefined" 
typeof 0 // "number" 
typeof 10n // "bigint" 
typeof true // "boolean" 
typeof "foo" // "string" 
typeof Symbol("id") // "symbol" 
typeof Math // "object" (1)
typeof null // "object" (2)
typeof alert // "function" (3)
```

Последние три строки нуждаются в пояснении:

1.  `Math` — это встроенный объект, который предоставляет математические операции и константы. Мы рассмотрим его подробнее в главе [Числа](https://learn.javascript.ru/number). Здесь он служит лишь примером объекта.
2.  Результатом вызова `typeof null` является `"object"`. Это официально признанная ошибка в `typeof`, ведущая начало с времён создания JavaScript и сохранённая для совместимости. Конечно, `null` не является объектом. Это специальное значение с отдельным типом.
3.  Вызов `typeof alert` возвращает `"function"`, потому что `alert` является функцией. Мы изучим функции в следующих главах, где заодно увидим, что в JavaScript нет специального типа «функция». Функции относятся к объектному типу. Но `typeof` обрабатывает их особым образом, возвращая `"function"`. Так тоже повелось от создания JavaScript. Формально это неверно, но может быть удобным на практике.


# Ссылки
___
##### Links


---
##### Источники
https://learn.javascript.ru/types