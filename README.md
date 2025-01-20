## Описание
В данном проекте я знакомился с ОС ubuntu server и базовым инструментам в linux:   
Установка ОС;  
Создание пользователя;  
Настройка сети ОС;  
Обновление ОС;  
Использование команды  sudo;  
Установка и настройка службы времени;  
Установка и использование текстовых редакторов;  
Установка и базовая настройка сервиса SSHD;  
Установка и использование утилит top, htop;  
Использование утилиты fdisk;  
Использование утилиты df;  
Использование утилиты du;  
Установка и использование утилиты ncdu;  
Работа с системными журналами;  
Использование планировщика заданий CRON.  

## Part 1. Установка ОС

- ``версия Ubuntu после установки ``<br>
![Alt text](./images/1.png "Optional Title")<br>

---

## Part 2. Создание пользователя

- ``скриншот вызова команды для создания пользователя ``<br>
![Alt text](./images/2(1).png "Optional Title")<br>

- ``пользователь должен быть в выводе команды cat /etc/passwd ``<br>
![Alt text](./images/2(2).png "Optional Title")<br>

---

## Part 3. Настройка сети ОС
- ``название машины вида user-1``<br>
![Alt text](./images/3(1).png "Optional Title")<br>

- ``временная зона, соответствующая текущему местоположению``<br>
![Alt text](./images/3(2).png "Optional Title")<br>

- ``название сетевых интерфейсов с помощью консольной команды``<br>
![Alt text](./images/3(3).png "Optional Title")<br>

Интерфейс lo в Linux - виртуальный loopback интерфейс, используемый для локальной коммуникации между процессами на одной машине. Он ассоциируется с IP-адресом 127.0.0.1 и обеспечивает прозрачное тестирование сетевых приложений без воздействия на реальную сеть.

- ``используя консольную команду получил ip адрес устройства, на котором работаю, от DHCP сервера``<br>
![Alt text](./images/3(4).png "Optional Title")<br>

DHCP (Dynamic Host Configuration Protocol) - протокол автоматической настройки сети, предоставляющий устройствам IP-адреса и другие сетевые параметры без необходимости ручной настройки.

- ``вывод внешнего ip-адрес шлюза (ip)``<br>
![Alt text](./images/3(5(1)).png "Optional Title")<br>

- ``внутренний IP-адрес шлюза``<br>
![Alt text](./images/3(5(2)).png "Optional Title")<br>

- ``задаю статичные настройки ip, gw, dns``<br>
![Alt text](./images/3(6(2)).png "Optional Title")<br>
![Alt text](./images/3(6(1)).png "Optional Title")<br>
![Alt text](./images/3(6(3)).png "Optional Title")<br>


- ``Перезагрузка. Проверяем, статичные сетевые настройки (ip, gw, dns)``<br>
![Alt text](./images/3(6(2)).png "Optional Title")<br>
![Alt text](./images/3(7(1)).png "Optional Title")<br>

- ``Ping 1.1.1.1, ya.ru``<br>
![Alt text](./images/3(7(2)).png "Optional Title")<br>

## Part 4. Обновление ОС

``Обновление системных пакетов до последней на момент выполнения задания версии`` <br>
![Alt text](./images/4(1).png "Optional Title")<br>

## Part 5. Использование команды sudo

``Разрешить пользователю, созданному в Part 2, выполнять команду sudo`` <br>
![Alt text](./images/5(1).png "Optional Title")<br>

``Смена hostname от юзера s21ramonagr`` <br>
![Alt text](./images/5(2).png "Optional Title")<br>

## Part 6. Установка и настройка службы времени
``Настройка службы автоматической синхронизации времени`` <br>
Вывод команды должен содержать NTPSynchronized=yes: timedatectl show <br>
Cкрины с корректным временем и выводом.<br>
![Alt text](./images/6.png "Optional Title")<br>

## Part 7. Установка и использование текстовых редакторов
``VIM Выход+save esc -> : -> wq`` <br>
![Alt text](./images/7(1).png "Optional Title")<br>

``NANO Выход+save ctrl+x -> y -> enter`` <br>
![Alt text](./images/7(2).png "Optional Title")<br>

``MCEDIT Выход+save F2 (save) -> F10 (exit)`` <br>
![Alt text](./images/7(3).png "Optional Title")<br>

``VIM Выход esc -> : -> q!`` <br>
![Alt text](./images/7(1(1)).png "Optional Title")<br>

``NANO Выход ctrl+x -> n -> enter`` <br>
![Alt text](./images/7(2(1)).png "Optional Title")<br>

``MCEDIT Выход F10 -> n`` <br>
![Alt text](./images/7(3(1)).png "Optional Title")<br>

``VIM Поиск esc -> / -> 21 (optional)`` <br>
![Alt text](./images/7(1(2)).png "Optional Title")<br>

``VIM Замена esc -> :s/21/ramonagr/ -> enter (optional)`` <br>
![Alt text](./images/7(1(3)).png "Optional Title")<br>

``NANO Поиск ctrl+w -> write search -> enter`` <br>
![Alt text](./images/7(2(2)).png "Optional Title")<br> 

``NANO Замена ctrl+w -> ctrl+r -> write what to change -> enter -> write word -> enter -> Y`` <br>
![Alt text](./images/7(2(3)).png "Optional Title")<br>

``MCEDIT Поиск F7 -> write -> press ok `` <br>
![Alt text](./images/7(3(2)).png "Optional Title")<br> 

``MCEDIT Замена F4 -> write x2 -> press ok -> press confirm `` <br>
![Alt text](./images/7(3(3)).png "Optional Title")<br> 

## Part 8. Установка и базовая настройка сервиса SSHD
Установка <br>
sudo apt install openssh-server <br>

Автостарт службы <br>
sudo systemctl start ssh.service <br>
sudo systemctl enable ssh.service <br>

Перенастройка службы SSHd на порт 2022 <br>
sudo vim /etc/ssh/sshd_config <br>
Port 2022 :wq <br>


Отобразил наличие процесса <br>
ps -e | grep ssh <br>
ps - выводит сведения о процессах в статическом виде <br>
-e - позволяет выбрать все процессы <br>
| grep sshd - поиск по выводу <br>

netstat -tan <br>
![Alt text](./images/8.png "Optional Title")<br> 

-tan: <br>
-t - Отображать TCP подключения <br>
-a - Показывать состояние всех сокетов; обычно сокеты, используемые серверными процессами, не показываются. <br>
-n - Показывать сетевые адреса как числа. netstat обычно показывает адреса как символы. <br>

Proto - Содержит тип протокола <br>
Recv-Q - Счётчик байтов не скопированных программой пользователя из этого сокета. <br>
Send-Q - Счётчик байтов, не подтверждённых удалённым узлом. <br>
Local Address - Адрес и номер порта локального конца сокета. <br>
Foreign Address - Адрес и номер порта удалённого конца сокета. <br>
State - Состояние сокета. <br>
LISTEN Сокет ожидает входящих подключений. <br>
Time_WAIT в TCP указывает на ожидание завершения всех пакетов для сокета после закрытия соединения, обеспечивая правильное завершение и предотвращая повторное использование адреса и порта. <br>


## Part 9. Установка и использование утилит top, htop

Установка и запуск:
sudo apt install htop <br> 
top, htop

![Alt text](./images/9.png "Optional Title")<br> 
uptime - 4:03 <br> 
количество авторизованных пользователей - 1 user <br> 
общую загрузку системы - load average: 0.00, 0.00, 0.00 <br> 
общее количество процессов - 101 total <br> 
загрузку cpu - 0.0us, 0.3 sy, 0.0 ni <br> 
загрузку памяти - 3912.3 total, 3086.7 free, 231,1 used <br> 
pid процесса занимающего больше всего памяти (shift + M) - 652 <br> 
pid процесса, занимающего больше всего процессорного времени (shift + P) - 2480 <br> 

htop отсортированному по PID <br>
![Alt text](./images/9(1).png "Optional Title")<br> 
htop отсортированному по PERCENT_CPU <br>
![Alt text](./images/9(2).png "Optional Title")<br> 
htop отсортированному по PERCENT_MEM <br>
![Alt text](./images/9(3).png "Optional Title")<br> 
htop отсортированному по TIME <br>
![Alt text](./images/9(4).png "Optional Title")<br> 
htop отфильтрованному для процесса sshd <br> 
![Alt text](./images/9(5).png "Optional Title")<br> 
htop с процессом syslog, найденным, используя поиск
![Alt text](./images/9(6).png "Optional Title")<br> 
htop с добавленным выводом hostname, clock и uptime
![Alt text](./images/9(7).png "Optional Title")<br> 

## Part 10. Использование утилиты fdisk
команда fdisk -l<br>
![Alt text](./images/10.png "Optional Title")<br> 
название жесткого диска - /dev/sda <br> 
размер - 23,73 GB <br>
количество секторов - 49756160 <br>
размер swap - 2G <br>

## Part 11. Использование утилиты df

для корневого раздела (/): <br>
![Alt text](./images/11(1).png "Optional Title")<br> 
размер раздела - 11101392 <br>
размер занятого пространства - 5425992 <br>
размер свободного пространства - 5089672 <br>
процент использования - 52 <br>

Единица измерения в выводе - байты <br>

df -Th <br>
![Alt text](./images/11(2).png "Optional Title")<br> 
размер раздела - 11G <br>
размер занятого пространства - 5,2G <br>
размер свободного пространства - 4,9G <br>
процент использования - 52 <br>
тип файловой системы для раздела - ext4

## Part 12. Использование утилиты du
размер папки /home <br>
![Alt text](./images/12(1).png "Optional Title")<br> 
размер папки /var <br>
![Alt text](./images/12(2).png "Optional Title")<br> 
размер папки /var/log <br>
![Alt text](./images/12(3).png "Optional Title")<br> 

Размер всего содержимого в /var/log (не общее, а каждого вложенного элемента, используя *) <br>
![Alt text](./images/12(4).png "Optional Title")<br> 

## Part 13. Установка и использование утилиты ncdu
размер папки /home <br>
![Alt text](./images/13.png "Optional Title")<br> 
размер папки /var <br>
![Alt text](./images/13(1).png "Optional Title")<br> 
размер папки /var/log <br>
![Alt text](./images/13(2).png "Optional Title")<br> 

## Part 14. Работа с системными журналами
/var/log/auth.log <br>
![Alt text](./images/14.png "Optional Title")<br> 
время последней успешной авторизации - 00:57:24 <br>
имя пользователя - ramonagr <br>
метод входа в систему - LOGIN <br> 

Перезапуск службы SSHd <br> 
![Alt text](./images/14(1).png "Optional Title")<br> 

## Part 15. Использование планировщика заданий CRON
Список текущих заданий crontab <br>
![Alt text](./images/15(2).png "Optional Title")<br> 

В системном журнале строчки о выполнении <br>
![Alt text](./images/15(1).png "Optional Title")<br> 

Удалить все задачи <br>
![Alt text](./images/15(3).png "Optional Title")<br> 