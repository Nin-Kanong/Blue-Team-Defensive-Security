



## Lab Solution:
[17.8.2 Packet Tracer - Skills Integration Challenge.docx](https://github.com/user-attachments/files/29848229/17.8.2.Packet.Tracer.-.Skills.Integration.Challenge.docx)



## Start Lab

<img width="966" height="535" alt="image" src="https://github.com/user-attachments/assets/1b4dc963-00b7-4958-baa4-7ce154cf6f58" />


### On Staff

First click on `Staff`:
<img width="921" height="452" alt="image" src="https://github.com/user-attachments/assets/73958701-2a59-4a08-a886-68f3309889bb" />


After Click on `IP Configuration`:
<img width="873" height="886" alt="image" src="https://github.com/user-attachments/assets/66ef88ed-404b-47b1-867e-c17398fbb1d4" />



### On R1

Click on `R1`:

````
en
conf t
hostname R1
no ip domain-lookup
enable secret Ciscoenpa55
login
exit
security password min-length 10
service password-encryption
banner motd #Unauthorized access is prohibited#
````
````
int g0/0
ip add 192.168.0.1 255.255.255.128
ipv6 add 2001:db8:acad::1/64
ipv6 add fe80::1 link-local
no shut
````
````
int g0/1
ip add 192.168.0.129 255.255.255.192
ipv6 add 2001:db8:acad:1::1/64
ipv6 add fe80::1 link-local
no shut
````
````
int g0/2
ip add 192.168.0.193 255.255.255.224
ipv6 add 2001:db8:acad:2::1/64
ipv6 add fe80::1 link-local
no shut
````
````
exit
ip domain-name CCNA-Lab.com
crypto key generate rsa
line
````












































