<h1> How to configure Telnet Cisco Switch and Router </h1>


---


## Start:

<img width="803" height="445" alt="image" src="https://github.com/user-attachments/assets/29606d1e-af8f-4dc7-a43b-60bfe9413147" />


<img width="971" height="922" alt="image" src="https://github.com/user-attachments/assets/8e48ce22-be69-4b9b-855b-eeb7af596084" />



<img width="1007" height="728" alt="image" src="https://github.com/user-attachments/assets/62453228-786b-4c8d-b008-3b300eec645d" />


<img width="755" height="500" alt="image" src="https://github.com/user-attachments/assets/28c10904-a08a-44ba-950e-e6a72a3babdb" />


<img width="866" height="883" alt="image" src="https://github.com/user-attachments/assets/3d3f51d2-ca46-4f93-b5e8-06066a13be0e" />



### Configure VLAN Interface
````
en
conf t
hostname SW1
interface vlan 1
ip address 192.168.1.2 255.255.255.0
no shutdown
exit
````
<img width="861" height="801" alt="image" src="https://github.com/user-attachments/assets/5b92636f-e821-4bf9-88b1-2c5812aac21d" />


### Configure defualt Gateway
````
ip default-gateway 192.168.1.1
enable secret k4n0ng
line vty 0 15
password k4n0ng
login
transport input telnet
exit
copy running-config startup-config
````
<img width="457" height="407" alt="image" src="https://github.com/user-attachments/assets/7dd353a5-be66-4268-8edd-d4ca26292158" />




### Configure PC Address
Click on `PC0`:
<img width="872" height="892" alt="image" src="https://github.com/user-attachments/assets/e1fce591-e93a-4bd9-9ac2-67bf6bbe3199" />

| Setting         | Value         |
| --------------- | ------------- |
| IP Address      | 192.168.1.10  |
| Subnet Mask     | 255.255.255.0 |
| Default Gateway | 192.168.1.1   |

<img width="873" height="682" alt="image" src="https://github.com/user-attachments/assets/5258825b-546f-4133-b778-1317517b4f6a" />

Now we finished.

---

### Test ping
<img width="858" height="860" alt="image" src="https://github.com/user-attachments/assets/ab7f94bc-afaa-4dbc-9b88-a9e59f2cc264" />

````
ping 192.168.1.2
````
<img width="513" height="289" alt="image" src="https://github.com/user-attachments/assets/e2407995-5200-4b02-a103-0677b1b7f71d" />


---

### Test Telnet:
In PC Command Prompt:
````
telnet 192.168.1.2
````
<img width="312" height="165" alt="image" src="https://github.com/user-attachments/assets/4d163bb1-1736-4f02-b964-9a874f106d5f" />

In this my password is: `k4n0ng`.

And now we got successful.

---

### We can Useful Verification Commands
On ``switch``:
````
show ip interface brief
show running-config
show vlan brief
show interfaces status
show mac address-table
show users
````
---

