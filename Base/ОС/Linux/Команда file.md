202104281323
Tags:
___
# Команда file - показывает тип файла           
`file опции название_документа`

Что же касается опций, то их у этой команды несколько десятков. Мы рассмотрим лишь основные:
`-b, --brief` — запрет на демонстрацию имен и адресов файлов в выводе команды;
`-i`,` --mime` — определение MIME-типа документа по его заголовку;
`--mime-type`, `--mime-encoding` — определение конкретного элемента MIME;
`-f`, `--files-from` — анализ документов, адреса которых указаны в простом текстовом файле;
`-l`, `--list` — список паттернов и их длина;
`-s`, `--special-files` — предотвращение проблем, которые могут возникнуть при чтении утилитой специальных файлов;
`-P` — анализ определенной части файла, которая обозначается различными параметрами;
`-r`, `--raw` — отказ от вывода /ooo вместо непечатных символов;
`-z` — анализ содержимого сжатых документов.

Случается, что нужно проверить не один, а несколько файлов. Чтобы не выполнять команду много раз подряд, перечисляйте названия всех файлов через пробел.

Кстати, команда file даёт возможность не только проверить, является ли архив архивом, но и заглянуть внутрь, чтобы узнать, что в нём содержится. Для этой цели используется опция -z.

___
##### Links


---
##### Источники
