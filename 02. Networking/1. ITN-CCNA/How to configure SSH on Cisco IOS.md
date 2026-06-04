<h1> How to configure SSH on Cisco IOS </h1>


---

## Start:

<img width="890" height="464" alt="image" src="https://github.com/user-attachments/assets/a10a2e52-9593-4ba4-afb7-704e103b9a1c" />


<img width="1223" height="897" alt="image" src="https://github.com/user-attachments/assets/6e18144d-6216-4022-b9d8-54dc83944210" />

<img width="1092" height="788" alt="image" src="https://github.com/user-attachments/assets/efaea2ce-e87f-42a7-8c30-16a0cf524158" />

---

### Configure IP Address
Click on `PC0` -> Go to `Desktop` -> Click on `IP Configuration`:

| Field       | Value         |
| ----------- | ------------- |
| IP Address  | 192.168.1.10  |
| Subnet Mask | 255.255.255.0 |
| Gateway     | 192.168.1.1   |

<img width="870" height="678" alt="image" src="https://github.com/user-attachments/assets/6d71db51-af7f-492b-8b1b-18e43358bcef" />


### Configure on Switch

Click on `switch` -> click on `CLI` -> after press `Enter`:
<img width="862" height="836" alt="image" src="https://github.com/user-attachments/assets/19d9f621-9a96-4806-892a-aad7b5172160" />


### Configure mode & change hostname
````
en
conf t
hostname SW!
````
<img width="524" height="145" alt="image" src="https://github.com/user-attachments/assets/5f7d14ce-c7fd-44df-a45f-d2a39763dd09" />


In this I want to verify it:
````
exit
show running-config | include hostname
````
<img width="442" height="121" alt="image" src="https://github.com/user-attachments/assets/03a56244-ae85-4a9b-9374-3547f153cc1c" />



### Configure Management IP

SSH needs an IP address.
````
interface vlan 1
ip address 192.168.1.2 255.255.255.0
no shutdown
exit
````
<img width="653" height="252" alt="image" src="https://github.com/user-attachments/assets/f2a2150e-c93a-4e77-a7c8-bb8f903a5727" />

> **Note**: If you was verify in above you need to user `conf t` again.

#### Verify:
````
exit
show ip interface brief
````
<img width="745" height="651" alt="image" src="https://github.com/user-attachments/assets/cebb4e31-3c81-4d98-a5dd-03755122e18e" />

Now we got success.



### Configure Default Gateway & create local user
````
conf t
ip defualt-gateway 192.168.1.1
````
<img width="555" height="158" alt="image" src="https://github.com/user-attachments/assets/b72a56fe-aa19-4825-b533-a851cd2d2343" />

- SSH uses local authentication.

| Part     | Meaning            |
| -------- | ------------------ |
| username | Create user        |
| k4n0ng    | Login name         |
| secret   | Encrypted password |
| k4n0ng   | Password           |


### Set Enable Password
````
enable secret k4n0ng
````
<img width="301" height="68" alt="image" src="https://github.com/user-attachments/assets/968f2ba6-8969-401e-8c32-2a52320088a6" />


### Configure Domain Name
````
ip domain-name k4n0ng.com
````
<img width="324" height="54" alt="image" src="https://github.com/user-attachments/assets/e050b6b4-da7e-4030-a30a-7f639e305d55" />

In this we can use others domain, in this I want to use my name.


#### Verify:
````
exit
show running-config | include domain
````
<img width="446" height="122" alt="image" src="https://github.com/user-attachments/assets/1705070c-aaeb-4227-a31b-e90c8a7f4589" />

Now we see our domain.


### Generate RSA keys
This is the most important SSH step.

Generate keys:
````
crypto key generate rsa
````
<img width="668" height="253" alt="image" src="https://github.com/user-attachments/assets/65b1e136-94c6-4e16-ae78-342425341a3c" />

In this we can use `1024` or `2048` or others.



#### After verify it:
````
exit
show crypto key k4n0ng mypubkey rsa
````
<img width="712" height="402" alt="image" src="https://github.com/user-attachments/assets/86ad20bf-eecd-4dcf-a4a4-c478bbc7fae8" />




### Enable SSH Version 2
````
conf t
ip ssh version 2
````
<img width="513" height="55" alt="image" src="https://github.com/user-attachments/assets/b868f1f4-0702-40e7-879c-212dd7a7c3dd" />


#### Verify:
````
exit
show ip ssh
````
<img width="504" height="141" alt="image" src="https://github.com/user-attachments/assets/001bce47-9c25-4bb2-bc2d-06765e2bbdea" />



### Configure VTY line
enter VTY configuration:
````
conf t
line vty 0 4
login local
transport input ssh
exit
````

<img width="537" height="184" alt="image" src="https://github.com/user-attachments/assets/52091a55-9a86-44f6-84ab-e6c28338ca0a" />


| Command             | Purpose                     |
| ------------------- | --------------------------- |
| login local         | Use local username database |
| transport input ssh | Allow SSH only              |
| line vty 0 4        | Configure remote sessions   |


### Save configuration:
````
end
copy running-config start-config
````
<img width="466" height="170" alt="image" src="https://github.com/user-attachments/assets/00ce4e3b-e5ee-4aa5-874f-23a706a45fe9" />

Now we finished all.

---


### Verify SSH Configuration
### Check SSH:
````
show ip ssh
````
<img width="476" height="58" alt="image" src="https://github.com/user-attachments/assets/212fb68e-8c11-4cfd-b48e-3ee4e02e70fa" />


#### Check User
````
show running-config | include username
````
<img width="539" height="74" alt="image" src="https://github.com/user-attachments/assets/f98d55b5-ef0a-45ee-864e-5f4f361a933c" />


#### Check VTY
````
show running-config | section vty
````
<img width="370" height="115" alt="image" src="https://github.com/user-attachments/assets/4329d7fb-7c50-474b-bdfe-bdbcc29e48f8" />

---

### test connection:
Click `PC0` -> Go to `Desktop` -> click on `Command Promt`:
<img width="704" height="665" alt="image" src="https://github.com/user-attachments/assets/992ab350-e84b-4e47-9eef-7fe24b2517b7" />



---

### SSH to the Switch
````
ssh -l k4n0ng 192.168.1.2
````
<img width="309" height="153" alt="image" src="https://github.com/user-attachments/assets/d995c724-3f7e-4942-b194-6b166b4ff857" />

In this my Username is: `k4n0ng` and password is `k4n0ng`.
````
enable
````
<img width="331" height="186" alt="image" src="https://github.com/user-attachments/assets/913a7e82-eb0d-468f-bbd4-d77343f9d1a8" />

In this my password is `k4n0ng`.

Now we finished. 


---

### Full SSH Configuration 
````
enable
configure terminal

hostname SW1

interface vlan 1
 ip address 192.168.1.2 255.255.255.0
 no shutdown
exit

ip default-gateway 192.168.1.1

username k4n0ng secret k4n0ng

enable secret Cisco123

ip domain-name k4n0ng.com

crypto key generate rsa
1024

ip ssh version 2

line vty 0 4
 login local
 transport input ssh
exit

end

copy running-config startup-config
````


---
