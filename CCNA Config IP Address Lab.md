Configuring IP Addresses on a Cisco Router
This lab is changing the IP Address and it's preconfigured with a class A, B and C Networks.
Class A
15.0.0.0/8

Class B
182.98.0.0/16

Class C
201.191.20.0/24

Commands used
On the router, do the following.

We change the router hostname to R1.
Router>en
Router#conf t
Router(config)#hostname R1

Show the interfaces and the currently set IP Addresses
R1(config)#do sh ip int brief
All Int are down and the IP Addresses are not assigned.
<img width="624" height="238" alt="Screenshot 2026-02-10 184644" src="https://github.com/user-attachments/assets/44aeafdc-4250-4d84-8640-9dd46d130d4a" />

Change int G0/0 IP, turn it on and added description
R1(config)#int g0/0
R1(config-if)#ip add
R1(config-if)#ip address 15.255.255.254 255.0.0.0
R1(config-if)#desc ## to SW1 ##
R1(config-if)#no shut

Do the same for int G0/1
R1(config)#int g0/0
R1(config-if)#ip add
R1(config-if)#ip address 15.255.255.254 255.0.0.0
R1(config-if)#desc ## to SW2 ##
R1(config-if)#no shut

Same for int G0/2

R1(config)#int g0/2
R1(config-if)#ip address  201.191.20.254 255.255.255.0
R1(config-if)#desc ## to SW3 ##
R1(config-if)#no shut

Now we check IP Interface
R1#sh ip int brief

<img width="627" height="237" alt="image" src="https://github.com/user-attachments/assets/be3e635c-e646-49a3-ac9e-fb6ebbe5379d" />

Then check running-config
R1#sh run

<img width="456" height="491" alt="image" src="https://github.com/user-attachments/assets/4d444192-a9d9-4c82-aefc-c2cff5b769a4" />

Then save the changes.
R1#copy running-config start
R1#write mem

Now we changes IP Address of PC1 on Class A
Go to the PC and change the FastEthernet0 Static IP to 15.0.0.1/8

<img width="682" height="472" alt="image" src="https://github.com/user-attachments/assets/b2a95e96-df87-4dc6-8948-dc6a16cfd105" />

Do the same for PC2 on Class B

<img width="681" height="435" alt="image" src="https://github.com/user-attachments/assets/3f528795-5db8-4c62-8962-4539b12ce8a8" />

Do the same for PC3 on Class C

<img width="681" height="438" alt="image" src="https://github.com/user-attachments/assets/5c376d82-bbe8-4e85-8a04-643ef0664fbc" />

We can now ping PC2 and PC3 from PC1

<img width="583" height="317" alt="image" src="https://github.com/user-attachments/assets/e5b19471-aaec-4243-a705-bae351d5db69" />
<img width="573" height="322" alt="image" src="https://github.com/user-attachments/assets/9dae910a-5570-4a71-85b5-f27f62de78ca" />

In this lab, we learned how to configure IP Addresses on router interfaces, enable interfaces and confirmed reachability with ping.















