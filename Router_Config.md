`R#enable` <br>
`R#configure terminal` <br>
`R(conf)#hostname R1` <br>
`R1(conf)#interface GigabitEthernet0/0` <br>
`R1(conf-if)#ip address 10.0.1.1 255.255.255.252` <br>
`R1(conf-if)#no shutdown` <br>
`R1(conf-if)#ex` <br>
`R1(conf)#interface GigabitEthernet0/1` <br>
`R1(conf-if)#ip address 10.0.2.1 255.255.255.252` <br>
`R1(conf-if)#no shutdown` <br>
`R1(conf-if)#ex` <br>
`R1(conf)#interface GigabitEthernet0/2` <br>
`R1(conf-if)#ip address 10.0.4.1 255.255.255.252` <br>
`R1(conf-if)#no shutdown` <br>
`R1(conf-if)#ex` <br>
`R1(conf-if)#interface Loopback0`  **виртуальный интерфейс, который существует, только пока работает сам роутер. Он никогда не "падает"** <br>
`R1(conf-if)#ip address 1.1.1.1 255.255.255.255`  **маска /32 означает, что это адрес конкретного хоста (самого себя).** <br>
`R1(conf-if)#ex` <br>
`! Настройка OSPF` <br>
`R1(conf)#router ospf 1` **запускаем процесс OSPF с номером 1** <br>
`R1(conf-router)#router-id 1.1.1.1`  **Принудительно указываем OSPF использовать этот идентификатор. Должен совпадать с Loopback, чтобы было понятно.** <br>
`R1(conf-router)#network 10.0.1.0 0.0.0.3 area 0`  **активировать OSPF на найденных интерфейсах и отнести их к зоне 0.** <br>
`R1(conf-router)#network 10.0.2.0 0.0.0.3 area 1` <br>
`R1(conf-router)#network 10.0.4.0 0.0.0.3 area 3` <br>
`R1(conf-router)#network 1.1.1.1 0.0.0.0 area 0`  <br>
`R1(conf-router)#area 3 stub no-summary` **объявляем, что зона 3 является тупиковой** <br>

`end` <br>
`write memory` <br>
<img width="1125" height="835" alt="Screenshot_1" src="https://github.com/user-attachments/assets/6033028c-4c2a-401c-ae4c-55285cef5208" />
<img width="1118" height="830" alt="Screenshot_2" src="https://github.com/user-attachments/assets/a989b61d-5df8-4f34-9e0a-f0fc28e9ad92" />
<img width="1122" height="827" alt="Screenshot_4" src="https://github.com/user-attachments/assets/1df448cd-bd6e-4808-9f0c-cb7e15e4b6fe" />





