202104262129
Tags:
___
> Калькулятор https://ciscolearning.ru/basics/classless-net/

# IP-адреса
**Бит** – единица измерения информации в двоичной системе исчисления.
 **Байт** -  это единица измерения количества информации, равная 8 битам, т.е. 8 нулей или единиц.
 

 IP адреса нужны для уникальной идентификации компьютеров в крупной составной сети, которая может включать в себя весь мир, например сети Интернет, и различные части сети интернет построенные на разных технологиях [[Канальный уровень| канального уровня]]
 
 
 Сейчас есть 2-е версии протокола IP: версия [[IPv4- адреса | IPv4]] и [[IPv6-адреса | IPv6]]. Основное отличие между версиями протоколов в длине IP адреса. В IPv4 длина адреса 4 байта, а в IPv6 длина адреса 16 байт.
 
 В сети Интернет требуется глобальная уникальность адреса; в случае работы в локальной сети требуется уникальность адреса в пределах сети. 
  
**IP-адрес** -  это уникальный числовой идентификатор устройства в компьютерной сети], работающий по протоколу TCP/IP.

В сетях используется 2 типа адресов:
1. Локальные (серые, статические) - для изолированной сети, назначается администратором сети из специально зарезервированных для таких сетей блоков адресов (10.0.0.0/8, 172.16.0.0/12 или 192.168.0.0/16)
2. Глобальные (белые, динамические): Для выхода в глобальную сеть необходимо, чтобы был IP из другого блока адресов, либо в локальной сети должен быть сервер, подменяющий внутренний IP-адрес (серый) на внешний IP-адрес (белый), например: proxy server, [[Технология NAT|NAT]]. Если же сеть должна работать как составная часть Интернета, то адрес сети выдаётся провайдером либо региональным интернет-регистратором

## IP-адреса и IP-сети

Одна из задач сетевого уровня обеспечить масштабирование, построить такую сеть, которая может работать в масштабах всего мира. *Для этого сетевой уровень работает не с отдельными компьютерами, а с подсетями, которые объединяют множество компьютеров.*

В IP объединение происходит следующим образом, подсеть это некое количество компьютеров, у которых одинаковая старшая часть IP-адреса.

![[Pasted image 20220110163619.png]]
И маршрутизаторы, устройства передающие информацию на сетевом уровне, работают уже не с отдельными IP адресами, а с подсетями.

# Ссылки
---
##### Links
[[Протокол IP]]
[[Примеры задач]]


---
##### Источники
