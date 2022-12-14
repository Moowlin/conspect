202106261141
Tags:
___
# Changing File Permissions - `chmod`
Условные значения флагов прав:
-   `---` - нет прав, совсем;
-   `--x` - разрешено только выполнение файла, как программы но не изменение и не чтение;
-   `-w-` - разрешена только запись и изменение файла;
-   `-wx` - разрешено изменение и выполнение, но в случае с каталогом, вы не можете посмотреть его содержимое;
-   `r--` - права только на чтение;
-   `r-x` - только чтение и выполнение, без права на запись;
-   `rw-` - права на чтение и запись, но без выполнения;
-   `rwx` - все права;
-  `--s` -  установлен SUID или SGID бит, первый отображается в поле для владельца, второй для группы;
-   `--t` - установлен sticky-bit, а значит пользователи не могут удалить этот файл.
![[Pasted image 20210428020635.png]]

Менять права можно командой `chmod` 

>**Consider This**
Why is the command named `chmod` instead of `chperm`? Permissions used to be referred to as modes of access, so the command `chmod` really means _**ch**ange the **mod**es of access._

`chmod [<SET><ACTION><PERMISSIONS>]... FILE`

![[Pasted image 20210427231027.png]]

>С помощью опции -R вы можете заставить программу применять изменения ко всем файлам и каталогам рекурсивно

`<SET>`   Категория указывает для какой группы пользователей нужно применять права, как вы помните доступно только три категории:
- **u** - ==U==ser - владелец файла;
- **g** - ==G==roup - группа файла;
- **o** - ==O==thers - другие пользователи.
- **a** - ==A==ll - относится к пользователю, группе и прочим.

`<ACTION>` - указываем символ дейсвтия
- **+** -  добавить разрешение
- **=** - указать специальное разрешение
- **-** - убрать разрешение


Примеры:
`chmod ugo+rwx test5` - всем пользователям полный доступ к файлу test5
`chmod go-rwx test5` - заберем все права у группы и остальных пользователей
`chmod g+rx test5` - Дадим группе право на чтение и выполнение
`chmod o+r test5` - Остальным пользователям только чтение
`chmod u+s test6` - Для файла test6 установим SUID
`chmod g+s test7` - для test7 - SGID
`chmod u=rwx,g=rx,o=r myfile`

## Определение прав доступа в виде числового кода
Каждый тип прав доступа может быть представлен в цифровом виде:
-   r = 4    
-   w = 2    
-   x = 1   
-   \- = 0
Для установки определенных прав доступа используется сумма этих значений


Вот список некоторых часто используемых настроек, цифровых эквивалентов и их значения:
-   `-rw-------` (600) — только владелец имеет права на чтение и изменение файла;   
-   `-rw-r--r--` (644) — только у владельца есть права на чтение и изменение; у группы и остальных есть право только на чтение;    
-   `-rwx------` (700) — только у владельца файла есть права на чтение, изменение и выполнение файла;    
-   `-rwxr-xr-x` (755) — у владельца есть права на чтение, изменение и выполнение, а у группы и остальных пользователей — на чтение и выполнение;    
-   `-rwx--x--x` (711) — у владельца есть права на чтение, изменение и выполнение, а у группы и остальных пользователей — только на выполнение 
-   `-rw-rw-rw-` (666) — любой пользователь может читать и изменять файл (будьте осторожны с такими правами);   
-   `-rwxrwxrwx` (777) — любой пользователь может читать, изменять и выполнять файл (еще раз предупреждаем, что в общем случае использовать такие разрешения опасно).
    

Некоторые часто встречающиеся разрешения для каталогов:
-   `drwx------` (700) — только владелец может читать и изменять данный каталог;   
-   `drwxr-xr-x` (755) — владелец может читать и изменять каталог, у пользователей и группы есть право на чтение и выполнение.

___
##### Links


---
##### Источники
