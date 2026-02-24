`R#enable` <br>
`R#configure terminal` <br>
`R(conf)#hostname router1` <br>
`router1(conf)#interface GigabitEthernet0/0` <br>
`router1(conf-if)#no shutdown` <br>
`router1(conf-if)#ip address 10.0.1.1 255.255.255.252` <br>
`router1(conf-if)#ip ospf 1 are 0` <br> **указываем в каком домене будет работать интерфейс и в какой зоне**
`router1(conf-if)#ip ospf network point-to-point` <br> **для экономии ресурсов роутера указывает что маршрутизиторы соедененны PtP, это исключает поиск DR и BDR**
`router1(conf-if)#ex` <br>
`router1(conf)#interface GigabitEthernet1/0` <br>
`router1(conf-if)#no shutdown` <br>
`router1(conf-if)#ip address 10.0.4.2 255.255.255.252` <br>
`router1(conf-if)#ip ospf 1 are 0` <br>
`router1(conf-if)#ip ospf network point-to-point` <br>
`router1(conf-if)#ex` <br>
`router1(conf)#interface GigabitEthernet2/0` <br>
`router1(conf-if)#no shutdown` <br>
`router1(conf-if)#ip address 10.0.10.1 255.255.255.252` <br>
`router1(conf-if)#ip ospf 1 are 1 ` <br> ****
`router1(conf-if)#ex` <br>
`router1(conf-if)#interface Loopback0`  **виртуальный интерфейс, который существует, только пока работает сам роутер. Он никогда не "падает"** <br>
`router1(conf-if)#ip address 1.1.1.1 255.255.255.255`  **маска /32 означает, что это адрес конкретного хоста (самого себя).** <br>
`router1(conf-if)#ip ospf 1 are 0` <br>
`router1(conf-if)#ex` <br>
`router1(conf)#router ospf 1` **запускаем процесс OSPF с номером 1** <br>
`router1(conf-router)#router-id 1.1.1.1`  **Принудительно указываем OSPF использовать этот идентификатор. Должен совпадать с Loopback, чтобы было понятно.** <br>
`router1(conf-router)#passive-interface g2/0`  **Принудительно указываем interface g2/0 пассивным** <br>
`router1(conf-router)#area 1 stub no-summary` **объявляем, что зона 1 является тупиковой** <br>






