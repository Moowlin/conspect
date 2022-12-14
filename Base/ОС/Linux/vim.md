202105101833
Tags:
___

>**Consider This**
The correct way to pronounce the `vi` editor is the vee-eye editor. The letters vi stand for visual, but it was never pronounced this way by the developers, but rather the letter v followed by the letter i.

## Перемещение по файлу
These motions can be prefixed with a number to indicate how many times to perform the movement. For example, 5h would move the cursor five characters to the left and 3w would move the cursor three words to the right.

| команда | действие |
| --- | --- |
| **k** | вверх |
| **j** | вниз |
| **h** | влево |
| **l** | вправо |
| **Ctrl+f** | на страницу (экран) вниз |
| **Ctrl+b** | на страницу (экран) верх |
| **Ctrl+d** | на пол страницы (экрана) вниз |
| **Ctrl+u** | на пол страницы (экрана) верх |
| **Ctrl+y** | на строку вниз, без изменения положения курсора |
| **Ctrl+e** | на строку верх, без изменения положения курсора |
| **Ctrl+g** | узнать номер строки, на которой находится курсор |
| **0** («ноль») | в начало текущей строки |
| **^** | в начало текущей строки (к первому непробельному символу) |
| **$** | в конец текущей строки |
| **w** | на слово вправо |
| **b** | на слово влево |
| **W** | до пробела вправо |
| **B** | до пробела влево |
| **}** | абзац вниз |
| **{** | абзац вверх |
| **gg** | перейти в начало файла |
| **G** | перейти в конец файла |
| **\<number>G** | перейти на конкретную строку <number> |
| **\/\<text>\<CR>** | перейти к \<text> |
| **?\<text>\<CR>** | то же самое, но искать назад |
| **n** | повторить поиск |
| **N** | повторить поиск назад |
| **\[\[** | в начало функции |
| **''** | к месту выполнения команды \[\[ |


## Ввод текста

| команда | действие |
| --- | --- |
| **i** | перейти в режим ввода с текущей позиции  |
| **a** | перейти в режим ввода после курсора  |
| **I** | переместиться в начало строки и перейти в режим ввода  |
| **А** | переместиться в конец строки и перейти в режим ввода  |
| **o** | перейти в режим ввода с новой строки под курсором  |
| **O** | перейти в режим ввода с новой строки над курсором  |
| **s** | заменяет указанное количество символов (удаляет указанное число символов и переходит в режим ввода). В отличии от команды с которая может удалить кусок текста размером не меньше слова (cw), командой s можно удалить любое число символов. Например 4s удалит четыре символа начиная с того который находится под курсором. Эта команда применяется для замены одного или нескольких символов другими символами.  |
| **S** | удаляет всю текущую строку и переходит в режим ввода. Число перед командой показывает сколько нужно удалить строк начиная с текущей. Например 4S удалит четыре строки включая текущую.  |
| **R** | перейти в режим ввода с заменой текста (аналог insert). Символы под курсором заменяются на вводимые. Команда применяется когда неизвестно сколько придётся изменить символов на другие (иначе можно было бы использовать команду s с указанием числа заменяемых символов, например, 7s). При удалении вводимых символов возвращаются те которые были до ввода команды. Такой режим сохраняется до конца строки. При вводе новой строки (по нажатию Enter), происходит не переход на другую строку с тем же режимом замены текста, а создание новой строки.  |
| **r** | заменить один символ. Заменяет символ находящийся под курсором на символ который следует за командой. При этом не происходит выхода из командного режима (не надо нажимать ESC после изменения текста). Например, команда ry - символ под курсором меняется на "y". Числовой показатель указывает сколько символов необходимо заменить на данный. Например, 3ry вставляет три символа "y". |
	
## Удаление и вставка
| команда | действие |
| --- | --- |
| **x** | удалить символ под курсором (<число>x удаляет указанное число символов начиная с того который находится под курсором)  |
| **X** | удалить символ влево (удалить символ перед курсором)  |
| **d** | используется совместно с командами перемещения. Удаляет символы с текущего положения курсора до положения после ввода команды перемещения. Пример:   |
| **dw** | удаляет символы с текущего до конца слова. включая пробел после слова,   |
| **de** | удалет символы до конца слова, но оставвляет пробел после слова   |
| **dE** | удаляет символы с текущего до конца слова, включая символы пунктуации, но оставляет пробел после слова  |
| **diw** | удаляет слово под курсором  |
| **dd** | удалить текущую строку (вырезать)  |
| **d<число>d** или **<число>dd** | стирание числа строк начиная с текущей  |
| **db** | удаляет символы с текущего до начала слова (удаление в обратном направлении)  |
| **d0** | удаление символов с начала строки до текущего положения курсора  |
| **d$** или **D** | удаление символов с текущего положения курсора до конца строки  | 
| **с** | команда аналогичная d, но после удаление переходит в режим ввода  |
| **сс** | команда удаляет текущую строку и переходит в режим ввода  |
| **C** | удаляет текст с текущего положения курсора до конца строки, аналогична команде с$ (где $ - символ конца строки)  |
| **yy (также Y)** | копирование текущей строки в буфер  |
| **y<число>y** | копирование числа строк начиная с текущей в буфер  |
| **p** | вставка содержимого буфера под курсором. Поскольку в vim девять ячеек буфера удаления. Можно вставить не только последнее удаление, но и удаления сделанные ранее. Например "4p" вставит под курсор содержимое четвертого удаления начиная с последнего. Также чтобы поменять местами два символа можно использовать комбинацию команд "удалить" -x (удаление в буфер) и "вставить" - p (вставить из буфера). Таким образом, поставив курсор на первую букву из двух которые необходимо поменять местами и нажав комбинацию клавиш **xp** мы совершим необходимые действия  |
| **P** | вставка содержимого буфера перед курсором  |
| **J** | слияние текущей строки со следующей. Числовой аргумент перед командой показывает сколько следующих линий необходимо объединить с текущей. Например 2J объединить две следующие строки с текущей, на которой расположен курсор  |

### Отмена изменений
	
| команда | действие |
| --- | --- |
| **u** | отмена последней команды  |
| **U** | отмена всех последних изменений в строке, если строка удалена, то применить эту команду к данной строке будет невозможно  |
	
### Поиск
| команда | действие |
| --- | --- |
| **/фраза** | поиск фразы во всем документе  |
| **n** | следующее найденное (вниз)  |
| **N** | предыдущее (вверх)  |
	
### Выход
| команда | действие |
| --- | --- |
| **:q!** | выйти без сохранения  |
| **:wq** | записать файл и выйти  |
| **ZZ** | записать файл и выйти (Если файл не изменяли, то записываться он не будет)  |

___
##### Links


---
##### Источники
