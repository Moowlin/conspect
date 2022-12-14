202107051836
Tags:
___
# Описание
Анализ файлов - неотъемлемая часть работы с ними. Иногда возникает необходимость подсчитать количество строк или слов в тексте. С этой задачей эффективно справляется команда **wc** Linux.

Для запуска утилиты откройте терминал и введите:
`wc`
Терминал будет ожидать ввода данных. После нажатия комбинации клавиш **Ctrl** + **D** командный интерпретатор завершит работу программы и выведет три числа, обозначающих количество строк, слов и байт введённой информации.

Утилита может обрабатывать файлы. Стандартная инструкция выглядит так:
`wc file`
-   **wc** — имя утилиты;
-   **file** — название обрабатываемого файла.

==Параметры:==

| Параметр | Длинный вариант | Значение |
| --- | --- | --- |
| -c | --bytes | Отобразить размер объекта в байтах |
| -m | --count | Показать количесто символов в объекте |
| -l | --lines | Вывести количество строк в объекте |
| -w | --words | Отобразить количество слов в объекте |

>Под объектом следует понимать файл или данные, полученные на стандартный поток ввода.

>Команда может обработать несколько файлов, если указать их через пробел или выбрать по шаблону.




___
##### Links


---
##### Источники
