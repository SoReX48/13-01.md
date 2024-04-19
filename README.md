# Домашнее задание к занятию "`Защита сети`" - `Пешкин Евгений`

### Задание 1.
sudo nmap -sA < ip-адрес >

Никаких логов suricata не отобразила

<br/>
<br/>
sudo nmap -sT < ip-адрес >
<br/>
![Скриншот к заданию 1](https://github.com/SoReX48/13-03.md/blob/main/Защита_cети/2.png)

Был обнаружен потенциально плохой трафик сканирования следующих портов на машине в которой запущен suricata
а также в случае внц попытка утечки информации
3306,1433,1521,5900-5920,5432
ip адрес сканировавшего 192.168.0.113
<br/>
<br/>
Было так же замечено что nmap использует пользовательские порты скорее всего для того чтобы скрыться под обычный сетевой трафик а так же стоит заметить что nmap сканирует на 4 модели уровне osi транспортном уровне 
<br/>
<br/>
sudo nmap -sS < ip-адрес >
<br/>
![Скриншот к заданию 2](https://github.com/SoReX48/13-03.md/blob/main/Защита_сети/3.png)

Результат идентичен предыдущему сканированию кроме момента что в этот раз nmap сканировал vnc порт 5915
<br/>
<br/>
sudo nmap -sV < ip-адрес >
<br/>
![Скриншот к заданию 3](https://github.com/SoReX48/13-03.md/blob/main/Защита_сети/4.png)

Помимо уже вышеперечисленных обнаружений были в этот раз выявлены атаки на веб приложения


### Задание 2.
<br/>
![Скриншот к заданию 4](https://github.com/SoReX48/13-03.md/blob/main/Защита_сети/5.png)
<br/>
Логи fail2ban показали что было найдено 20 попыток авторизации по ssh на 20 попытку был выдан бан по ип адресу второй локальной машины
<br/>
<br/>
Логи suricata говорили о следующем:
<br/>
![Скриншот к заданию 5](https://github.com/SoReX48/13-03.md/blob/main/Защита_сети/6.png)
<br/>
SURICATA STREAM pkt seen on wrong thread: предупреждение о том, что пакет TCP был замечен на неправильном потоке.
<br/>
ET SCAN Potential SSH Scan: Это сигнал того, что обнаружены потенциальные попытки сканирования SSH.
<br/>
SURICATA Applayer Detect protocol only one direction: предупреждение о том, что Suricata обнаружил протокол только в одном направлении трафика.


