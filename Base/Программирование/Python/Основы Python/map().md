202105221127
Tags:
___
### Функция map()
позволяет применить заданную в параметре функцию к каждому элементу последовательности. Она имеет такой формат:
``` python
map(<Функция>, <Последовательность1>[, ..., <ПоследовательностьN>])
```
Пример;
```python
list_of_str = ['1', '2', '5', '10']
list(map(int, list_of_str))
[1, 2, 5, 10]
```
Функции map() можно передать несколько последовательностей. В этом случае в функцию обратного вызова будут передаваться сразу несколько элементов, расположенных в последовательностях на одинаковом смещении.
``` python
def func(e1, e2, e3):
	""" Суммирование элементов трех разных списков """
	return e1 + e2 + e3 # Возвращаем новое значение

arr1 = [1, 2, 3, 4, 5]
arr2 = [10, 20, 30, 40, 50]
arr3 = [100, 200, 300, 400, 500]
print(list(map(func, arr1, arr2, arr3)))
# Результат выполнения: [111, 222, 333, 444, 555]
```

___
##### Links


---
##### Источники
