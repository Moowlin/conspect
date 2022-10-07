202105221129
Tags:
___
#### Функция filter()
Функция `filter` применяет функцию ко всем элементам последовательности и возвращает итератор с теми объектами, для которых функция вернула *True*.
```filter(<Функция>, <Последовательность>)```
Пример:
```python
>>>list_of_strings = ['one', 'two', 'list', '', 'dict', '100', '1', '50']
>>>filter(str.isdigit, list_of_strings)
<filter at 0xb45eb1cc>

>>>list(filter(str.isdigit, list_of_strings))
['100', '1', '50']
```

___
##### Links


---
##### Источники
