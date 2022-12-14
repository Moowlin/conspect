202106261933
Tags:
___
# Команда dd
**dd** - это команда терминала для копирования и преобразования файлов.
Не очень понятное описание, но это всё, что делает dd. Вы передаёте ей файл-источник, пункт назначения и пару дополнительных опций. Затем она делает копию одного файла в другой. Вы можете задать точный размер данных, которые нужно записать или скопировать. Работает утилита со всеми устройствами. Например, если вы хотите перезаписать жёсткий диск нулями из /dev/zero, можете сделать это. Также она часто используется для создания LiveUSB или гибридных ISO образов.

Утилита просто переносит по одному блоку данных указанного размера с одного места в другое.
Синтаксис:
`$ dd if=источник_копирования of=место_назначения параметры`

С помощью параметра if вам нужно указать источник, откуда будут копироваться блоки, это может быть устройство, например, /dev/sda или файл - disk.img.
C помощью параметра of необходимо задать устройство или файл назначения.

Теперь давайте рассмотрим дополнительные параметры:

-   `bs` - указывает сколько байт читать и записывать за один раз;
	**с** - один символ;
	**b** - 512 байт;
	**kB** - 1000 байт;
	 **K** - 1024 байт;
	**MB** - 1000 килобайт;
	**M** - 1024 килобайт;
	**GB** - 1000 мегабайт;
	**G** - 1024 мегабайт.
-   `cbs` - сколько байт нужно записывать за один раз;
-   `count` - скопировать указанное количество блоков, размер одного блока указывается в параметре bs;
-   `conv=фильтр,фильтр` - применить фильтры к потоку данных;
-   `ibs` - читать указанное количество байт за раз;
-   `obs` - записывать указанное количество байт за раз;
-   `seek` - пропустить указанное количество байт в начале устройства для чтения;
-   `skip` - пропустить указанное количество байт в начале устройства вывода;
-   `status` - указывает насколько подробным нужно сделать вывод;
-   `iflag, oflag` - позволяет задать дополнительные флаги работы для устройства ввода и вывода, основные из них: nocache, nofollow.

## Примеры использования
`sudo dd if=/dev/sr0 of=~/CD.iso bs=2048 conv=noerror` - сохранить образ диска в файл.  Фильтр noerror позволяет отключить реагирование на ошибки

создать образ жесткого диска или раздела на нем и сохранить этот образ на диск:
`dd if=/dev/sda of=~/disk.img` В вашей домашней папке будет создан файл с именем disk1.img, который в будущем можно будет развернуть и восстановить испорченную систему.

`dd if=/dev/sda of=~/disk.img bs=5M` - копирование диска блоками размером по 5 мегабайт

`sudo dd if=/dev/zero of=file.img bs=1M count=512` - создать файл размером 512 мегабайт, заполнив его нулями из /dev/zero или случайными цифрами из /dev/random

___
##### Links


---
##### Источники
https://losst.ru/komanda-dd-linux
https://ru.wikipedia.org/wiki/Dd