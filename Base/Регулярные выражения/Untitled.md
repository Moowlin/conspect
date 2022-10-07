202104292232
Tags:
___
###
1. Вывести с помощью команды host только MX-записи (ее приоритет и сама
запись) домена google.com, отсортировать по приоритету.

	`$ host -t MX google.com | sort`

2. С помощью цикла while, команды dig вывести в файл ips.txt A-записи
домена, после чего на следующей строке PTR-запись IP.

	`$ dig localdomain.tech +noall +answer |tee ips.txt | awk '{print $5}' | xargs dig +noall +answer  -x >> ips.txt `

3. Выполнить команду abc, перенаправить вывод потока ошибок в файл
error.txt и вывести поток ошибок на экран без пустых строк.

	`$ abc 2>error.txt || grep -ve '^$' error.txt`

4. Из логов в файле logs.txt * выбрать только IPv4-адреса, с которых
осуществлялись запросы к поддомену "zxc.okerpet.beget.tech", подсчитать
количество этих запросов и отобразить их сумму напротив каждого IP-адреса.
Список соответствия суммы запросов и IP вывести в порядке убывания
(сортировать по количеству запросов).

	`$ grep "zxc.okerpet.beget.tech" logs.txt | cut -d' ' -f2 | sort | uniq -c | sort -r`

5. Вывести на экран все строки файла hello.txt, содержащие слово "Привет", и 5 строк ниже каждой.

	`grep -A5 "Привет" 'hello.txt'`

7. Вывести 2, 3 и 5 слово тз кажой строки файла и добваить "|" в качестве разделителя

	`$ awk '{print $2, sep="|",$3, sep="|", $5, sep="|"}' hello.txt `
	`cat hello.txt | cut -d' ' -f2,3,5 | sed 's/\ /|/g'`



___
##### Links
[[Для работы и управления сетью]]


---
##### Источники
- [команда `awk`](https://losst.ru/ispolzovanie-awk-v-linux)
- перенаправление потоков https://habr.com/ru/post/55136/
- about `sed` and `awk` https://www.opennet.ru/docs/RUS/bash_scripting_guide/a14586.html
- пример использования `cut` https://ardeya.ru/poluchit-spisok-ip-adresov-iz-log-fajla/
- о `grep` http://www.linuxlib.ru/manpages/GREP.1.shtml and https://losst.ru/gerp-poisk-vnutri-fajlov-v-linux
- о циклах  https://losst.ru/tsikly-bash
- o `xrags` https://habr.com/ru/company/selectel/blog/248207/
	Принцип работы `xargs`: программа берет данные из стандартного ввода или из файла, разбивает их в соответствии с указанными параметрами, а затем передает другой программе в качестве аргумента. 
	В общем виде синтаксис команды xargs можно представить так: 
	`[команда_генератор_списка] | xargs [опции_xargs] [команда]`
- [КОМАНДА TEE](https://losst.ru/komanda-tee-linux)
