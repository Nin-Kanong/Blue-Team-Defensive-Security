<h1 align="center"> configure Default-Routing </h1>


## Start Lab:

<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/a0522a93-b82c-4c3d-9fbe-9a0a077cee5a" />


<img width="873" height="880" alt="image" src="https://github.com/user-attachments/assets/440a148e-467a-4981-ab7b-23f329dde2b3" />


<img width="1255" height="655" alt="image" src="https://github.com/user-attachments/assets/0c760c1c-3b81-463b-bf36-51b178167cf3" />

<img width="873" height="877" alt="image" src="https://github.com/user-attachments/assets/48fd6451-ee94-417f-a7f4-b075be0706e6" />


<img width="873" height="846" alt="image" src="https://github.com/user-attachments/assets/755437c8-5f1f-406b-9df6-112ff496e611" />

<img width="1436" height="925" alt="image" src="https://github.com/user-attachments/assets/236dc150-b316-4765-9060-f55a77e239e2" />

<img width="1317" height="591" alt="image" src="https://github.com/user-attachments/assets/20a030be-066d-40a0-ae20-b789ae56310d" />

<img width="1407" height="852" alt="image" src="https://github.com/user-attachments/assets/d97b2946-0ec6-4864-bebf-0395cefcf8d2" />

<img width="1576" height="816" alt="image" src="https://github.com/user-attachments/assets/c1090010-d03b-4518-a16f-04958e310b03" />


<img width="1916" height="1078" alt="image" src="https://github.com/user-attachments/assets/fba41e38-8732-4466-b429-c4192bda26fb" />


<img width="1172" height="645" alt="image" src="https://github.com/user-attachments/assets/a6a6df0c-16d9-45a9-9cef-da003c8e54fe" />

In this In others computer we do like this all.

<img width="1183" height="594" alt="image" src="https://github.com/user-attachments/assets/d46422ed-ad89-42fb-8f53-985595745f83" />


After set IP Address:
<img width="1040" height="555" alt="image" src="https://github.com/user-attachments/assets/38fa8730-145e-4029-9703-1324bc86728f" />

After click ``Router 0``:

<img width="1011" height="578" alt="image" src="https://github.com/user-attachments/assets/6de55070-4a39-46e2-b27a-378522af4d55" />


<img width="872" height="850" alt="image" src="https://github.com/user-attachments/assets/981f9e55-302c-43c6-95a1-9a053ad3d87f" />

```
no
```
<img width="862" height="886" alt="image" src="https://github.com/user-attachments/assets/b69657c9-62dc-4c64-b4a5-e8bf592634e2" />



```
en
config t
interface serial 0/0/0
ip address 192.168.20.1 255.255.255.0
clock rate 128000
no shutdown
interface fastethernet 0/0
ip address 192.168.10.1 255.255.255.0
no shutdown
exit
ip route 0.0.0.0 0.0.0.0 192.168.20.2
exit
copy running-config startup-config
```
<img width="721" height="592" alt="image" src="https://github.com/user-attachments/assets/7524d9ca-2f41-454f-b099-545ad995819c" />



After config **Router 1**:
<img width="1913" height="741" alt="image" src="https://github.com/user-attachments/assets/7748a35a-c05e-4e4c-a07c-a9802b373bf4" />



```
en
config
interface serial 0/0/0
ip address 192.168.20.2 255.255.255.0
no shutdown
exit
interface fastethernet 0/0
ip address 192.168.30.1 255.255.255.0
no shutdown
exit
ip route 0.0.0.0 0.0.0.0 192.168.20.1
exit
copy running-config startup-config
```
<img width="795" height="747" alt="image" src="https://github.com/user-attachments/assets/0241c6ba-34e1-4827-b248-0fb356661867" />



### On PC 0

Click on **PC 0 ** -> **Desktop** -> **IP configuration**:

<img width="759" height="753" alt="image" src="https://github.com/user-attachments/assets/df057c05-6a00-45c9-9948-c279ddd47441" />



### PC 1


<img width="880" height="743" alt="image" src="https://github.com/user-attachments/assets/82acc057-b33a-4d1e-93d7-1aaed9d5baa2" />



### PC 2
<img width="873" height="741" alt="image" src="https://github.com/user-attachments/assets/15fbb481-1d5d-4dce-9930-3730f27c7a97" />




## Router 1:


### PC 0


<img width="865" height="696" alt="image" src="https://github.com/user-attachments/assets/8752c986-ad07-4115-9049-05447822ce7b" />


### PC 1
<img width="872" height="699" alt="image" src="https://github.com/user-attachments/assets/8e626072-a31e-4d37-bfe0-2590f4ff81a0" />


### PC 2
<img width="874" height="746" alt="image" src="https://github.com/user-attachments/assets/48f2a4ee-7faa-40db-8a40-fee7bbfe0adb" />



## After we completed test connection:
<img width="1810" height="812" alt="image" src="https://github.com/user-attachments/assets/f8abe05f-7092-4d9b-9602-44e09659d942" />


````
ping 192.168.30.4
````

<img width="1908" height="911" alt="image" src="https://github.com/user-attachments/assets/bfa50de7-6e12-492f-81f8-e886cb335016" />

Now we got successfully.

---
















