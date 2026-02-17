Lab is for configuring interfaces on a router and two switches.

Topology is a single LAN, 172.16.0.0/16
<img width="639" height="266" alt="image" src="https://github.com/user-attachments/assets/233b8017-0742-4b5d-9b4b-6678b06e478b" />

First step is to configure the Router 1.

1. Changed hostname to R1
Router(config)#hostname R1

2. Show the current setup
<img width="626" height="239" alt="image" src="https://github.com/user-attachments/assets/0487b13f-6ea4-4d20-9a11-3f3c62dbc2fa" />

3. Changed interfaces config
R1(config-if)#ip address 172.16.255.254 255.255.0.0
R1(config-if)#duplex full
R1(config-if)#speed 1000
R1(config-if)#desc ## to SW1 ##
R1(config-if)#no shut

4. Check status
<img width="626" height="243" alt="image" src="https://github.com/user-attachments/assets/eeacf9f9-f580-43bb-9e75-c5a925ed22b6" />

5. Copy run config to start
R1#copy running-config startup-config

Config PCs IP Addresses
1. Change all default PCs static gateway to 172.16.255.254
2. Change PC1 Static IP Address to 172.16.255.0.1 255.255.0.0
3. Change PC2 Static IP Address to 172.16.255.0.2 255.255.0.0
4. Change PC3 Static IP Address to 172.16.255.0.3 255.255.0.0
5. Change PC4 Static IP Address to 172.16.255.0.4 255.255.0.0

Config SW1
1. Change hostname
Switch(config)#hostname SW1

2. Check current config
SW1(config)#do sh int status

3. Config G0/1-2
SW1(config)#int g0/1
SW1(config-if)#speed 1000
SW1(config-if)#duplex full
SW1(config-if)#desc ## to R1 ##

SW1(config)#int g0/2
SW1(config-if)#speed 1000
SW1(config-if)#duplex full
SW1(config-if)#desc ## to SW2 ##

4. Config f0/1-2
SW1(config-if)#int range f0/1-2
SW1(config-if-range)#desc ## to end hosts ##

5. Config f0/3-24
SW1(config-if-range)#int range f0/3-24
SW1(config-if-range)#desc ## not in use ##
SW1(config-if-range)#shutdown

6. Check status
SW1(config-if-range)#do sh int status
<img width="950" height="623" alt="image" src="https://github.com/user-attachments/assets/ae4cc111-dd09-48e3-82ef-5263271ec7be" />

7. commit changes
SW1#write memory
One last check
SW1#sh startup-config 

Config SW2
1. Change hostname
Switch(config)#hostname SW2

2. Check status
SW2(config)#do show int status
<img width="944" height="618" alt="image" src="https://github.com/user-attachments/assets/3c9e6eee-4481-4b45-94ba-286ce9870868" />

3. Config G0/1
SW2(config)#int g0/1
SW2(config-if)#speed  1000
SW2(config-if)#duplex full
SW2(config-if)#description ## to SW1 ##

4. Config f0/1-2
SW2(config-if)#int range f0/1-2
SW2(config-if-range)#desc ## to end hosts ##

6. Config f0/3-24
SW2(config-if-range)#int range f0/2-24, g0/2
SW2(config-if-range)#desc ## not in use ##
SW2(config-if-range)#shutdown

7. Check status
SW2(config-if-range)#do sh int status
<img width="935" height="617" alt="image" src="https://github.com/user-attachments/assets/32c08162-a1b7-4bea-aa84-2505f4278908" />

8. Write to startup
SW2#write

