# Лекция 5
## Коммутация
### Обозначение
![коммутация](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_1.png)
### Виды схем
Простая схема коммутации:

![1-я схема](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_2.png)

Схема с маршрутизатором:

![с маршрутизатором](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_3.png)

Стекирование: несколько физических коммутаторов формируют один логический коммутатор с одним MAC и одним IP:

![стекирование](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_4.png)

Повышение скоростей на медленных портах:

![](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_5.png)

Семейство STP, повышение надёжности:

![повышение надёжности](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_6.png)

### Классификация коммутаторов
#### По структуре
1. Модульные
![модульные](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_7.png)
2. Немодульные
![немодульные](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_8.png)
#### По типу подключения
##### Обозначения
- Медные линии
- Оптические линии
##### Виды
- С медными портами
- С оптическими портами
- комбинированые
- SFP сменный модуль порта
#### По параметрам источника электропитания
U_n = 220В, f = 50/60Гц

± 12В, ± 24В, ± 36В, ± 48В, ± 60В
#### По области применения
- Small office home office (SOHO) — небольшие пропускные способности
- Small & medium business (SMB) 
- Enterprise — корпоративный (операторский)  
![enterprise](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_9.png)
#### По функциям
- Второго уровня — кадры
- Третьего уровня — пакеты
- Многоуровневые (4+) — сегменты (датаграммы фильтрации, firewall) 
#### По возможности электропитания пользовательских устройств
- Power over Ethernet (PoE) — IEEE802.3af & IEEE802.3at
![PoE](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_10.png)
  - активные PoE
  - пассивные PoE
### Пример работы
<pre>
[MAC-1]----[oooo]----[MAC-2]
</pre>

<pre>
+---------+-------------------+---------------------------------------+
| N Порта | Физический адрес  | Время жизни                           |
+---------+-------------------+---------------------------------------+
| 1       | MAC-1             | infinity при ручной настройке         |
| 2       | -----             | либо Top при автоматической настройке |
| 3       | -----             |                                       |
| 4       | MAC-2             |                                       |
+---------+-------------------+---------------------------------------+
</pre>

Кадр:
<pre>
+----+----+-----+
| SA | DA | ... |
+----+----+-----+
</pre>

SA = MAC-1; DA = MAC-2

Могут быть ситуации, когда на одном порте несколько MAC-адресов

Discover Protocol (DP) — для работы с соседними устройствами. Виды: LCDP, CDP, NDP, PDP, ...

## VLAN
Virtual Local Area Network — логическая локальная компьютерная сеть, представляет собой группу хостов с общим набором требований, которые взаимодействуют так, как если бы они были подключены к широковещательному домену, независимо от их физического местонахождения.

<pre>
          VLAN1 
[Кадр] + [Метка] = [Метка|Кадр] для VLAN #1
          VLAN2  
[Кадр] + [Метка] = [Метка|Кадр] для VLAN #1
</pre>


<pre>
+---------+--------+------------------+---------------------------------------+
| N Порта | Метка  |Физический адрес  | Время жизни                           |
+---------+--------+------------------+---------------------------------------+
| 1       | VLAN1  | MAC-1            | infinity при ручной настройке         |
| 2       | VLAN1  | -----            | либо Top при автоматической настройке |
| 3       | VLAN2  | -----            |                                       |
| 4       | VLAN2  | MAC-2            |                                       |
+---------+--------+------------------+---------------------------------------+
</pre>
На метку выделяется 12 бит, т.е. бывает 4096 меток. 
### Добавление метки бывает: 
- port-based
- mac-based
- protocol-based
### Виды портов:
- access — порт доступа к VLAN, untagged
- trunk — порт обмена данными между различными VLAN, tagged
- VLAN Trunking Protocol — протокол доставки информации о VLAN
- Spanning Tree Protocol (STP) — основной задачей STP является устранение петель в топологии произвольной сети Ethernet, в которой есть один или более сетевых мостов
- Rapid Spanning Tree Protocol (RSTP) — более новая версия, ускоренная 

## Маршрутизация
<pre>
[Сетевое устройство]---[Сетевой элемент]
</pre>
![scheme1](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_11.png)
![scheme2](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_12.png)
![scheme3](https://raw.githubusercontent.com/krasnotsvetov/Networks_course/master/Images/5_13.png)
## Маршруты
- По способу формирования
  - статические
  - динамические
- По направлению передачи сообщения
  - прямой
  - обратный
- По количеству сетей, которые могут быть достижимы на маршруте
- Протокол маршрутизации на основе сост. каналов
  - реактивные (по событию)
  - проактивные (по запросу)
