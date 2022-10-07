202105221130
Tags:
___
#### Функция any()
Функция `any` возвращает True, если хотя бы один элемент истинный.
Пример:
```python
def ignore_command(command):
    '''
 Функция проверяет содержится ли в команде слово из списка ignore.
 command - строка. Команда, которую надо проверить
 Возвращает True, если в команде содержится слово из списка ignore, False - если нет
 '''
    ignore = ['duplex', 'alias', 'Current configuration']

    return any(word in command for word in ignore)202105221130
Tags:
___
###

___
##### Links


---
##### Источники

```

___
##### Links


---
##### Источники
