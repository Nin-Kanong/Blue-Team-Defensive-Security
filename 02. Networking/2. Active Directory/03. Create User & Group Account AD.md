<h1 align="center"> Create User & Group Account AD  </h1>

<img width="1536" height="700" alt="image" src="https://github.com/user-attachments/assets/0672ad00-b39b-4607-8e3c-7f7ce75144fc" />



---



## Start:

Firsrt open our **Windows Server 2022**:

<img width="1914" height="937" alt="image" src="https://github.com/user-attachments/assets/4194fa6a-18e3-475e-959d-b299ed48e540" />


### Create **OU**:

**OU (Organizational Unit)** in Windows Server Active Directory is a container used to organize users, computers, groups, and other objects inside a domain.


#### OU vs Group
| OU                       | Group                   |
| ------------------------ | ----------------------- |
| Organizes objects        | Assigns permissions     |
| Used for GPO             | Used for access control |
| Administrative container | Security object         |
| Cannot grant file access | Can grant file access   |

#### Main Purpose of OU (Organizational Unit) in Windows Server
| Purpose                          | Description                                                                     | Example                                                      |
| -------------------------------- | ------------------------------------------------------------------------------- | ------------------------------------------------------------ |
| **Organize Objects**             | Group users, computers, and groups into logical containers.                     | IT users in **OU=IT**, HR users in **OU=HR**                 |
| **Apply Group Policies (GPO)**   | Apply specific settings and security policies to selected users or computers.   | Disable Control Panel for all users in **OU=HR**             |
| **Delegate Administration**      | Allow specific administrators to manage only certain parts of Active Directory. | HR manager can manage only **OU=HR**                         |
| **Simplify Management**          | Makes Active Directory easier to manage and navigate.                           | Separate Workstations, Servers, and Users into different OUs |
| **Support Enterprise Structure** | Reflect real company departments and infrastructure.                            | IT, Finance, HR, SOC, and Servers OUs                        |

---

#### Tools 1

To create **OU** we have any ways or tools.

##### Create **OU** for **Sales**
Open our **Server Manager**:

<img width="811" height="848" alt="image" src="https://github.com/user-attachments/assets/b88d8c1e-1275-4b65-8bef-596df1c70685" />

<img width="1920" height="883" alt="image" src="https://github.com/user-attachments/assets/dc020891-a888-4569-a2b2-0d2e0c7a33e4" />

After we will see this:
<img width="1918" height="882" alt="image" src="https://github.com/user-attachments/assets/e0f7df8e-3efc-4a67-b0e1-5dd53ad06d4c" />

`Right-Click` on `cybersec (local)` -> `New` -> `Organization Unit`:
<img width="1922" height="886" alt="image" src="https://github.com/user-attachments/assets/ba3fc659-4983-474e-8f83-54c5563e0201" />

<img width="1916" height="882" alt="image" src="https://github.com/user-attachments/assets/33cc9d16-35f9-4f1d-86d0-4fba5af5d4c7" />

Now we see our **OU**:
<img width="1918" height="880" alt="image" src="https://github.com/user-attachments/assets/661e032f-15ff-44ca-af2c-bcfb8e799f17" />

---


#### Tools 2
Back to our **Server Manager**:

<img width="1918" height="880" alt="image" src="https://github.com/user-attachments/assets/beff1207-aa99-48d5-83cd-74dc9a7fedb5" />

To create **OU** -> `Right-Click` on `cybersec.com`:
<img width="1918" height="880" alt="image" src="https://github.com/user-attachments/assets/b9d3f4c8-5e6e-48af-8c3a-089b68b82d7e" />


##### Create **OU** for **Accounting**:
<img width="545" height="470" alt="image" src="https://github.com/user-attachments/assets/703ee042-0f2c-454c-ba14-e4abe77fa95c" />

Now we see our **OU** that we was create:
<img width="1041" height="497" alt="image" src="https://github.com/user-attachments/assets/f13485fa-edbd-41ac-b6ad-aa6dae33ef84" />

---

##### Create **OU** for **Finance**:

After `Right-Click` on our `cybersec.com`:
<img width="890" height="668" alt="image" src="https://github.com/user-attachments/assets/fd4ef998-9b30-4355-8e92-6a526759a65e" />

<img width="540" height="480" alt="image" src="https://github.com/user-attachments/assets/f4955d69-1e07-4b85-a24c-b59ad92c83ff" />

Now we see our **OU** for **Finance**:
<img width="830" height="510" alt="image" src="https://github.com/user-attachments/assets/018d1bcc-bfd2-43f2-86aa-0b6a0cae5844" />

---


##### Create **OU** for **HR**:
`Right-Click` on `cybersec.com`:
<img width="822" height="677" alt="image" src="https://github.com/user-attachments/assets/53bafcbc-55c7-46f1-9adf-375c9e4bca08" />

Also in this I was `Untick` it:
<img width="551" height="477" alt="image" src="https://github.com/user-attachments/assets/d824bda9-6c16-4bfe-8df4-b817068e8b3c" />

Now we see our **HR OU**:
<img width="822" height="570" alt="image" src="https://github.com/user-attachments/assets/bd2ab631-ee21-4fbc-9b06-35eaff3bb06b" />

---


After I test to delete some **OU** -> `Right-Click` on **Accounting**:
<img width="1080" height="737" alt="image" src="https://github.com/user-attachments/assets/1bddb8d0-5ead-436a-9429-abf94ddda9ea" />


<img width="480" height="215" alt="image" src="https://github.com/user-attachments/assets/a8e5681a-0b6d-46f2-93ce-a79feea73adf" />

Now we see we can't delete this **OU**:
<img width="519" height="219" alt="image" src="https://github.com/user-attachments/assets/4e049a87-f950-4f4f-89d5-eab352f31853" />

Why we can't delete this **OU**?

Cause **Protected from Accidental Deletion (Most Common)**:
- Active Directory has a safety feature that protects important objects from being deleted by mistake
- When this protection is enabled, even administrators can't delete the object unless they specifically disable this protection first


If we want to delete it:

- Open ``Active Directory Users and Computers``.
- Click on ``View`` in the top menu and ensure ``Advanced Features`` is checked. (This is crucial; otherwise, you won't see the Object tab).
- ``Right-click`` the ``Accounting OU`` and select ``Properties``.
- Go to the ``Object`` tab.
- Uncheck the box that says **Protect object from accidental deletion**.
- Click ``OK``.
- Try ``deleting`` the OU again.

But in this I don't want to delete.


After I test to delete `HR OU` that in this I don't `Tick` on `Protect Container from accidental deletion`:

<img width="968" height="740" alt="image" src="https://github.com/user-attachments/assets/f8c68acf-6588-45ea-972b-c86af075fd3c" />

<img width="483" height="212" alt="image" src="https://github.com/user-attachments/assets/961f1174-ff00-4d44-9921-3509b02a57bb" />

Now we got successfu to delete:
<img width="868" height="486" alt="image" src="https://github.com/user-attachments/assets/e4a87204-a4ac-4bf0-92c8-90055439b680" />

> In this if we `Tick` on `Protect Container from accidental deletion` we can't delete the **OU**.
> Also if we don't `Tick` on `Protect Container from accidental deletion` we can delete it as normal.

---



#### Check on IT OU:
<img width="657" height="463" alt="image" src="https://github.com/user-attachments/assets/48f00691-f521-4550-8a10-953d27ec841b" />

Now we see user `Nin Kanong`.

`Double-Click` on `Nin Kanong`:
<img width="509" height="670" alt="image" src="https://github.com/user-attachments/assets/91e3a62a-42b7-4fc1-92a7-839db5d5e5ed" />

Now we see this then add some:
<img width="512" height="668" alt="image" src="https://github.com/user-attachments/assets/f4ba9c51-2479-4f9c-be9e-fd583ef7b94e" />


After `Click` on `Address`:
<img width="517" height="675" alt="image" src="https://github.com/user-attachments/assets/7638c38f-be57-47cb-8d2e-978bd412f258" />


#### Create Manager:
After exit from user `Nin Kanong` -> then back to our **IT** OU -> `Right-Click`:
<img width="685" height="711" alt="image" src="https://github.com/user-attachments/assets/180485f2-0564-4434-864d-ff79ad27efb8" />

<img width="548" height="472" alt="image" src="https://github.com/user-attachments/assets/bc775f8a-6593-453e-b96f-2f1199b7b293" />


> **Note**: All of credentail or name you can use different from me.

In this my password **Manager** is:
````
@k4-hack/
@k4-hack/
````
<img width="547" height="467" alt="image" src="https://github.com/user-attachments/assets/32952836-365d-466b-841c-621fbeb3ddd1" />

> **Note**: In this we need to use strong password.

Now we got a new user **Manager**:
<img width="552" height="476" alt="image" src="https://github.com/user-attachments/assets/a65f1594-6dec-4bbc-9907-01288d4fb0be" />

Now we see the new user is **Manager**:
<img width="835" height="462" alt="image" src="https://github.com/user-attachments/assets/9fd9e7ec-1984-4d94-868a-7aba2736bc60" />

After `Double-Click` on `k4 k4n0ng` also in this I want my name company is:
````
CyberSec Solutions
````
<img width="511" height="675" alt="image" src="https://github.com/user-attachments/assets/629cde8f-007e-466e-a7dd-ee64578b6d99" />

Now we finished to set role.

#### Create Group
`Right-Click` on `IT` -> `New` -> `Group`:
<img width="712" height="700" alt="image" src="https://github.com/user-attachments/assets/b52a6d06-16fd-4046-9cfc-444c380d6ff5" />

The name ``IT_GG`` is the group name we chose when creating a new Active Directory group. Let’s break down what it usually means:

``IT`` → This prefix indicates the department or function. In Our case, it’s the Information Technology team.

``GG`` → This is often shorthand for Global Group. In AD naming conventions, admins sometimes add suffixes like:
- ``GG`` = Global Group
- ``DG`` = Domain Local Group
- ``UG`` = Universal Group

So ``IT_GG`` literally means: ``IT Department – Global Group``.

That tells anyone looking at the directory that this group is:

Related to the IT department.

Scoped as a Global Group, meaning it can be used across the domain but typically contains users from the same domain.

A Security group (since you selected Security type), so it’s intended for assigning permissions and access rights.

<img width="547" height="506" alt="image" src="https://github.com/user-attachments/assets/6f5edc59-4b5b-4f1f-a89e-39bf22d26c75" />

Now we see this:
<img width="801" height="448" alt="image" src="https://github.com/user-attachments/assets/dbfc7cbb-4891-4c48-b426-65407b84b922" />


After `Double-Click` on `Nin Kanong`:
<img width="1143" height="740" alt="image" src="https://github.com/user-attachments/assets/4f8699a1-160a-4aad-bea9-a091bac9d5a3" />

<img width="513" height="675" alt="image" src="https://github.com/user-attachments/assets/c18ae63c-3478-4b90-be5c-7e9caba59f0c" />

In this just type:
````
IT
````
Then click on `Checkname`:
<img width="572" height="317" alt="image" src="https://github.com/user-attachments/assets/b3fa2720-a3f7-4dd5-b367-deb883def116" />

After it wil show this the click `Ok`:
<img width="570" height="315" alt="image" src="https://github.com/user-attachments/assets/919e9885-7e87-45b8-909c-7d40cbe3fe2b" />

<img width="517" height="677" alt="image" src="https://github.com/user-attachments/assets/59fe8116-58c7-4b7d-9dd3-dd33622f8417" />

After `Add` user `k4 k4n0ng` into group ``IT``, just `Right-Click` on `k4 k4n0ng`:
<img width="831" height="637" alt="image" src="https://github.com/user-attachments/assets/847f5087-1de5-42fc-bdd8-4e24882fb7ec" />

<img width="572" height="313" alt="image" src="https://github.com/user-attachments/assets/e13e860a-08eb-46b2-91b2-39f0b07b3c4d" />

<img width="573" height="315" alt="image" src="https://github.com/user-attachments/assets/c62f3972-cecf-4a74-a8de-3fafa48ac5cb" />

<img width="482" height="212" alt="image" src="https://github.com/user-attachments/assets/d59fd0b6-69ec-4b7c-914c-5227421ea850" />

Now we finished to add to `Group`.

---

#### Add Manager

`Double-Click` on `Nin Kanong`:
<img width="1152" height="741" alt="image" src="https://github.com/user-attachments/assets/8656ef05-0dee-4493-8432-d60cb863862f" />

In this my company is:
````
CyberSec Solutions
````
<img width="510" height="672" alt="image" src="https://github.com/user-attachments/assets/3a32b77c-2e30-4c68-9975-7b0e78969f14" />


Just type:
````
k4
````
then click on `Checkname`:
<img width="572" height="315" alt="image" src="https://github.com/user-attachments/assets/9d1f4f1d-f6d3-45f8-9ec2-ba58f443d5f7" />

Now we see `k4 k4n0ng (k4n0ng.k4@cybersec.com)`:
<img width="570" height="312" alt="image" src="https://github.com/user-attachments/assets/25891f03-f751-413f-a4b2-bf6f81f902d6" />

Now we see the **Manager** of `Nin Kanong` is `k4 k4n0ng`:
<img width="515" height="672" alt="image" src="https://github.com/user-attachments/assets/fe4f5f27-f813-4103-8614-8fb5d2e880ae" />

Now we finished to add manager of `Nin Kanong`.


#### IF have one user stay in the same department like IT:
If have user that stay in the same department, in this we just copy from user that have like in this I want to add user that stay in the same:

Just `Right-Click` on `Nin Kanong` -> select on `Copy`:
<img width="882" height="592" alt="image" src="https://github.com/user-attachments/assets/70f7610a-9d93-400a-a396-5bcb2c4d4f01" />

Now I want to add user `Cristiano Ronaldo`:
<img width="542" height="472" alt="image" src="https://github.com/user-attachments/assets/2af526aa-42bf-4b33-9646-39fc0c8c1a05" />

After I set passsword of this user to:
````
@hacker.pepe.k4n0ng
````
<img width="545" height="470" alt="image" src="https://github.com/user-attachments/assets/f62dae8d-893e-4d2e-87a7-8e97b4f81f99" />

After click on `Finish`:
<img width="545" height="477" alt="image" src="https://github.com/user-attachments/assets/89b4f15d-1f1a-4e13-82d2-f2fe37bad2de" />

Now we got a user `Cristiano Ronaldo`:
<img width="913" height="448" alt="image" src="https://github.com/user-attachments/assets/2a14c1ed-4b93-455b-9ed3-7635c93e3b2c" />

After check user  have connect what `Cristiano Ronaldo`attribute -> Just  `Right-Click` on user `Cristiano Ronaldo`:
<img width="1042" height="548" alt="image" src="https://github.com/user-attachments/assets/16c31528-a227-49f7-bdfb-4d3dfc1868e3" />

Now we see in `General` has no connect atribute:
<img width="513" height="675" alt="image" src="https://github.com/user-attachments/assets/eff11538-e988-4a34-84de-f74f352766cf" />

Now we see in `Address` it have connect atribute, cause it a address of company:
<img width="512" height="673" alt="image" src="https://github.com/user-attachments/assets/c597156b-7718-4ed3-9cbd-2506fe0cc211" />

In `Organization` it also have connect atribute:
<img width="516" height="678" alt="image" src="https://github.com/user-attachments/assets/4f84e5cc-380b-437e-b88c-5c781225b0a3" />

Then in this I want to add `Job Title` and user `Cristiano Ronaldo` he worked in `IT Security Analyst`:
````
IT Security Analyst
````
<img width="517" height="672" alt="image" src="https://github.com/user-attachments/assets/763e267c-12d6-4b8a-975f-3bbcc5e538ec" />

Aso check this user stay in which group, and I see thsi user stay in `IT_GG`:
<img width="516" height="673" alt="image" src="https://github.com/user-attachments/assets/b4cb93d2-6df7-412c-801c-2882cf0ec4ba" />

Now we finished to create new user.

---

### Create User on Department Sales:
`Right-Click` on `Sales`:
<img width="743" height="736" alt="image" src="https://github.com/user-attachments/assets/542178ea-f3d8-4ee8-8d26-cadd3e8e82a2" />

<img width="546" height="512" alt="image" src="https://github.com/user-attachments/assets/a4e04398-829a-4be6-9a3a-ea28028624f1" />

Now we see the new **Group**:
<img width="860" height="448" alt="image" src="https://github.com/user-attachments/assets/4a9e1f4e-db72-4a32-a530-8d72f651e0bc" />

Now we finished to create new `Group`.

---


#### Create New USer
`Right-Click` -> `Sales`:
<img width="767" height="735" alt="image" src="https://github.com/user-attachments/assets/781711bf-66fa-40ff-93de-802704cd29ad" />

Now my new user on department **Sales** is `Pe Pe` and User Logon is:
````
pe.p@cybersec.com
````
<img width="548" height="477" alt="image" src="https://github.com/user-attachments/assets/ef682cd2-7d33-42ea-909f-4b656ea9ea12" />

After I set password is:
````
@<he.hacker>-k4
````
<img width="545" height="470" alt="image" src="https://github.com/user-attachments/assets/870a2934-555f-4f8a-b54a-8238add2fdb4" />


After click on `Finish`
<img width="546" height="472" alt="image" src="https://github.com/user-attachments/assets/141dce8a-be64-42cb-86ef-3ebce7c0024b" />

Now we see a new user `Pe Pe`:
<img width="866" height="431" alt="image" src="https://github.com/user-attachments/assets/d68bddcc-7757-4642-8034-6eb384c7c39f" />

Now we finsihed to create new user.

---


#### Add user to Group:
Add user `Pe Pe` to group, Just `Right-Click` on user `Pe Pe`:
<img width="1061" height="546" alt="image" src="https://github.com/user-attachments/assets/935c963b-306d-47be-af42-c017d58d6992" />

Just type:
````
Sal
````
After click on `Checkname`:
<img width="571" height="313" alt="image" src="https://github.com/user-attachments/assets/13c6d4b0-e998-4bb7-89cc-f45cd68529e2" />


After it will auto to `Sales_GG`:
<img width="576" height="316" alt="image" src="https://github.com/user-attachments/assets/7c3ca57e-1a65-492a-ac3d-d33697269d25" />


<img width="485" height="207" alt="image" src="https://github.com/user-attachments/assets/d8bdeb1b-f0a2-4663-b85f-c264df06933e" />

Now we finished to add user to Group.

---


### Test Login
Go to our **Windows Client**:

To login to user just click on `Other user`
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/6ea624be-fc5d-4b48-b262-35a0413eb901" />

Now it require to input `Username` & `Password`:
<img width="1544" height="933" alt="image" src="https://github.com/user-attachments/assets/3480fe71-fe06-46d4-b2d7-cfe682bf6a39" />

So in this my credentail is:
````
Username: k4n0ng.k4@cybersec.com
Password: @k4-hack/
````
<img width="1537" height="923" alt="image" src="https://github.com/user-attachments/assets/07315f2a-4eef-4f07-a124-810a54b20859" />

> Note: Also in this we can use username like this: `/administrator` like `cybersec/administrator`.

> Also in this we need to remeber your password.

After it require us to change password before login:
<img width="1022" height="660" alt="image" src="https://github.com/user-attachments/assets/29a6f0b0-f6a1-4be5-b0b9-3e3bb58b97c7" />

And in this I input new password is:
````
@k4$%^&*()<>
````
<img width="771" height="697" alt="image" src="https://github.com/user-attachments/assets/b7149df1-e540-43d8-9e9d-652c19bbeb90" />

Now password has been reset, also I use this password:
````
@k4$%^&*()<>
````
<img width="836" height="582" alt="image" src="https://github.com/user-attachments/assets/4463d4e2-ac45-423b-8508-ce84a1d36b09" />

Now it will get start new user:
<img width="1345" height="699" alt="image" src="https://github.com/user-attachments/assets/f00d7fa5-bcc4-4c06-8393-ba6a41a594c9" />

Now the windows of new user:
<img width="1556" height="892" alt="image" src="https://github.com/user-attachments/assets/c3cbfeca-84fe-4fbf-86f3-36dd6c88af11" />

After test it, just go to `CMD` -> type this:
````
hostname
````
<img width="441" height="171" alt="image" src="https://github.com/user-attachments/assets/3775a699-a9d5-4163-88e0-fbccd1c212be" />

Now we go into user `k4 k4n0ng`.

---


### Share folder

#### Create folder
Back to our **Windows Server** -> click on `File Explorer`:

<img width="1908" height="935" alt="image" src="https://github.com/user-attachments/assets/7928d750-3d77-4cfc-8240-7e9c392b5fdd" />

<img width="1409" height="746" alt="image" src="https://github.com/user-attachments/assets/b6090bc8-2a54-4ce2-a3cf-6a2a6da03842" />

Now we see this:
<img width="1409" height="744" alt="image" src="https://github.com/user-attachments/assets/5083f7b1-1815-423a-b710-01bbe4555e8c" />

Then I want to create new folder name:
````
Public
````
Just `Right-Click` on space:
<img width="1417" height="747" alt="image" src="https://github.com/user-attachments/assets/38810129-0c77-4ae8-a7e5-dd61e766a55a" />

Or in this if we want to fast just press `Ctrl + Shift + N`:
<img width="1407" height="742" alt="image" src="https://github.com/user-attachments/assets/1fffb753-35b9-4678-80b0-d7f830a012f0" />

Now we see a new folder name `Public`.

After I want to crete share folder all the same in my department in my companay (`Cybersec Solutions)`:
<img width="832" height="480" alt="image" src="https://github.com/user-attachments/assets/8d6f1006-a0a7-4826-9cbf-717fb891e598" />

<img width="1402" height="740" alt="image" src="https://github.com/user-attachments/assets/eca1d147-dc60-44af-b74c-55770166008c" />

Now we finished to create folder.


#### Share folder
`Right-Click` on `Public` -> `Properties`
<img width="1276" height="786" alt="image" src="https://github.com/user-attachments/assets/71b9e05a-44a8-472a-a5f4-c87b2385d4f9" />

<img width="485" height="593" alt="image" src="https://github.com/user-attachments/assets/1420aedd-b767-4f45-883d-364d93f84b57" />

<img width="448" height="457" alt="image" src="https://github.com/user-attachments/assets/4db06abf-f4a1-4e93-b8af-6da871e62b10" />


<img width="452" height="567" alt="image" src="https://github.com/user-attachments/assets/9aff26b6-f67a-4b52-beac-a2d84a3ffd1e" />

- **Group or user names**: ``Everyone`` → This means the permissions apply to all users who connect to this shared folder.

- Permissions for Everyone → It shows what level of access those users have:
   - ``Read (Allowed)`` → Users can open and view files in the folder.
   - ``Change (Not allowed)`` → Users cannot edit, delete, or add files.
   - ``Full Control (Not allowed)`` → Users cannot change permissions or take ownership.

> **Note**: In this if we input it as `Everyone` it not secure.


<img width="457" height="562" alt="image" src="https://github.com/user-attachments/assets/6ed443ba-225b-45fb-a5a8-89ea1d8f1c14" />

In this we set it as only `Authenticate`:
<img width="570" height="317" alt="image" src="https://github.com/user-attachments/assets/077c5a44-0c7d-4132-b87f-20d79792fd72" />

<img width="710" height="433" alt="image" src="https://github.com/user-attachments/assets/3478d372-9c96-4516-8f95-e0d11517b70b" />

In this it mean have only user that stay in this AD that can to go this.

<img width="455" height="565" alt="image" src="https://github.com/user-attachments/assets/e7d67267-3920-4ee7-8498-7a5dadc042d4" />

<img width="442" height="456" alt="image" src="https://github.com/user-attachments/assets/9f56b629-d637-42b3-bd7a-ce23592d674d" />

In this if we not sure about this, then we need to dibale inherit:
<img width="482" height="591" alt="image" src="https://github.com/user-attachments/assets/1b666c36-a49d-430e-bf3f-b32f597614e6" />

<img width="1025" height="640" alt="image" src="https://github.com/user-attachments/assets/f44bab94-9784-4953-b363-ba9ef6d02327" />

<img width="647" height="370" alt="image" src="https://github.com/user-attachments/assets/98c75411-d396-4c6b-b65f-ad82fc95f070" />


Now on my server see this, also in others maybe see any more, after click on `Add`:
<img width="1027" height="637" alt="image" src="https://github.com/user-attachments/assets/f284fb69-4382-491e-be7f-b2a3ae67f2d4" />

<img width="1223" height="732" alt="image" src="https://github.com/user-attachments/assets/aa7b04d0-870e-4189-bc74-6fea84c63977" />

<img width="607" height="313" alt="image" src="https://github.com/user-attachments/assets/78e7eec2-0583-4c5c-96db-f656aab53c64" />

Also in this I add `Administrator`:
<img width="761" height="428" alt="image" src="https://github.com/user-attachments/assets/3a484591-6978-4a34-848b-1da1b9d9ec4e" />

<img width="607" height="307" alt="image" src="https://github.com/user-attachments/assets/570b6e6c-4bd9-4735-8256-127189533af7" />

<img width="1217" height="727" alt="image" src="https://github.com/user-attachments/assets/7cfb28e5-a3d7-4cc8-82be-66b09977f5a9" />

Now we see `Administrator`:
<img width="1021" height="642" alt="image" src="https://github.com/user-attachments/assets/4b21405c-a0d7-4790-a208-7251439b8832" />


Also In this I want to add permission to others group:
<img width="1223" height="730" alt="image" src="https://github.com/user-attachments/assets/9fa35054-b270-40d5-886f-aaf14c36482f" />


##### In this I grant Permission to group `IT`:
<img width="611" height="312" alt="image" src="https://github.com/user-attachments/assets/7201b56e-9dff-4108-8f92-ffb81bf08104" />

<img width="610" height="312" alt="image" src="https://github.com/user-attachments/assets/d345567f-2d9e-455c-a4db-aea8839e7fc0" />

After I allow this permission:
<img width="1228" height="728" alt="image" src="https://github.com/user-attachments/assets/d7373530-006d-44b1-93cd-894c15efc6e9" />

In this I allow only:
- Read & Execute
- List folder content
- Read
- Write

Now we see IT Group:
<img width="1022" height="633" alt="image" src="https://github.com/user-attachments/assets/c2871831-1528-493c-8409-ec43f127216d" />


##### Add others Group
In this I want to add permission to `Sales` Group:
<img width="1023" height="636" alt="image" src="https://github.com/user-attachments/assets/ce58bba6-179d-4f8a-a8fd-bfb761e70d88" />


<img width="1222" height="727" alt="image" src="https://github.com/user-attachments/assets/c768729a-24b4-402b-a162-2523e64a2bb2" />

<img width="607" height="307" alt="image" src="https://github.com/user-attachments/assets/068e23e3-818c-489a-bd5d-f46cf260ec47" />

Now in this we see we can't add permission to **Sales Group**:
<img width="615" height="317" alt="image" src="https://github.com/user-attachments/assets/aa92dc81-954c-4388-8600-49d2546db310" />

Why?
Cause in this it a ditribution group.


IF we want to also add to this group:

Go to `Server Manager` -> `Tools`:
<img width="1918" height="883" alt="image" src="https://github.com/user-attachments/assets/b25b2c87-aa10-46ad-9be8-4914865a73a4" />

Go to Group `Sales` -> `Right-Click` on `Sales_GG` -> `Properties`:
<img width="1097" height="485" alt="image" src="https://github.com/user-attachments/assets/5209c961-2fc6-4676-84ca-ad2252f3d3f5" />

Choose `Security`:
<img width="503" height="572" alt="image" src="https://github.com/user-attachments/assets/ab2a715d-243f-4adf-ae45-0c4d45519746" />

<img width="875" height="447" alt="image" src="https://github.com/user-attachments/assets/c6423e1d-506e-4f25-8b44-09ab1f6ed8f5" />

After back to our `File Explorer` -> Folder than we want to assign permission:
<img width="1222" height="725" alt="image" src="https://github.com/user-attachments/assets/957295a1-9104-4e3b-8612-5a2dc7bb16fe" />

<img width="617" height="343" alt="image" src="https://github.com/user-attachments/assets/8ae7d32c-bac1-4eab-9411-f6c0414a4af1" />

Now we can assign permission:
<img width="620" height="346" alt="image" src="https://github.com/user-attachments/assets/0cd8e083-7471-4dc6-b38c-48780f7144fa" />

After in this I assign this permission, also if we want to assign more permission -> Click on `Show Advance Permission`:
<img width="1226" height="721" alt="image" src="https://github.com/user-attachments/assets/3d56316a-9940-4ce7-806f-00a67f58ada2" />

In this we can assign permission that we want, but in this I don't want to assign more permission:
<img width="1221" height="731" alt="image" src="https://github.com/user-attachments/assets/20986aad-ac7a-4dd5-aff3-57e259435493" />

Now we see this also Idon't want to add other, so I click `Ok`:
<img width="1025" height="647" alt="image" src="https://github.com/user-attachments/assets/1342b435-8011-4bfb-ab2b-d7122be66529" />

<img width="490" height="587" alt="image" src="https://github.com/user-attachments/assets/831950e0-e2cf-4e9d-9ae9-9e72aa85829f" />


---



#### How we can Access to folder that we was add permission:
`Right-Click` on folder that we was add or allow permission, also in this I add permission with Folder `Public` -> So `Right-Click` on `Public` -> `Property`:
<img width="1270" height="765" alt="image" src="https://github.com/user-attachments/assets/a7773f3d-fdae-4f91-bafd-434f18cbc4be" />

Go to `Sharing` now below `Network Path` so we see this:
````
\\DC01-AD\Public
````
<img width="485" height="596" alt="image" src="https://github.com/user-attachments/assets/72278338-fe7e-435a-80ef-3107709c9b61" />


##### After ON my Windows Client:
In my windows client I login with User in IT group:

<img width="1919" height="932" alt="image" src="https://github.com/user-attachments/assets/76e64362-80fa-4741-b567-b198e188e3e8" />


Go to `File Explorer` -> go to `Network` -> type our path:
````
\\DC01-AD\Public
````
<img width="1916" height="942" alt="image" src="https://github.com/user-attachments/assets/582398dd-8cb2-426b-81f4-920f5433319d" />


Now in this I stay in User in IT Group, Also I test to create file:

`Right-Click` -> `New` -> `Text Document`:
<img width="1407" height="722" alt="image" src="https://github.com/user-attachments/assets/d87a4ae2-5d50-4e32-9d6a-97b770a15caf" />

Now we see this, In this our IT Group has permission only `Read` and `Write`m don't have permission to create file:
<img width="1404" height="728" alt="image" src="https://github.com/user-attachments/assets/cc073d6b-8d7b-4dd9-8200-094fc96304fe" />

---


##### Access Netwok folder apth by IP 

In this we can access network path by IP, on **Windows Server** -> Check IP:
````
ipconfig
````
<img width="706" height="400" alt="image" src="https://github.com/user-attachments/assets/16633f22-f076-4726-98a0-1c057ba7a270" />

Now my **Windows Server** IP is:
````
192.168.127.10
````


After back to our **Windows Client** -> On `File Explorer` -> `Network`:
````
\\192.168.127.10\Public
````
<img width="1590" height="940" alt="image" src="https://github.com/user-attachments/assets/acf83b64-c089-4a58-9782-7f68d1b5e60f" />

Now we can access to folder.

---


#### Create Test file:
Back to our **Windows Server** -> on `File Explorer` -> Go to folder that we was create folder for add permission -> After go to file that we was create:
<img width="1918" height="967" alt="image" src="https://github.com/user-attachments/assets/e1173b89-f475-4c68-9e88-0766f8af09e1" />

Now it show this:
<img width="550" height="282" alt="image" src="https://github.com/user-attachments/assets/c57a5eb2-5fdb-4be5-935a-ceb570ab6b4a" />

If our **Windows Server** so this, don't worry -> `Right-Click` -> `Properties`:
<img width="1410" height="742" alt="image" src="https://github.com/user-attachments/assets/2b85703f-b3fc-4950-8a6d-2c4b51e04149" />

<img width="487" height="597" alt="image" src="https://github.com/user-attachments/assets/19f45f04-2406-411b-bd2a-6b418eae1d21" />

Click on `Administrator` -> Select all:
<img width="477" height="560" alt="image" src="https://github.com/user-attachments/assets/ae685e63-48c7-445b-af56-f2eadb8ae552" />

<img width="486" height="602" alt="image" src="https://github.com/user-attachments/assets/de387477-eac4-4c95-a047-6bae4681f0e8" />


After test to create file again:
<img width="1410" height="737" alt="image" src="https://github.com/user-attachments/assets/11f40ba1-f993-4e6c-b8d9-90a3ed21dad2" />

Now I was success to create file:
<img width="1125" height="743" alt="image" src="https://github.com/user-attachments/assets/f30410ae-987f-406e-8a85-3e83292a3f8c" />

Also in this I want to  input some data in this:
<img width="1037" height="303" alt="image" src="https://github.com/user-attachments/assets/7059c2ba-11f4-42df-93e2-1d96af13a0b4" />

Just press `Ctrl + S` to save it.

After back to our **Windows Client**:
<img width="1410" height="677" alt="image" src="https://github.com/user-attachments/assets/dd23866c-3baa-4a01-bf66-a686b5b824a9" />


Now I saw file.

---


#### Assign Permission Group IT:

`Right-Click` on folder IT:
<img width="1411" height="741" alt="image" src="https://github.com/user-attachments/assets/4a1a7e40-9509-469d-88a7-2848af520938" />

<img width="477" height="592" alt="image" src="https://github.com/user-attachments/assets/cd2d091c-f7fb-4e0d-a35c-2d0ef98d89d4" />


<img width="442" height="461" alt="image" src="https://github.com/user-attachments/assets/865a14fb-1a97-425b-8b9d-d0bcdb7df8b8" />


<img width="448" height="566" alt="image" src="https://github.com/user-attachments/assets/77df63e0-ef12-4827-8dac-4aa3ff9c208e" />

<img width="457" height="562" alt="image" src="https://github.com/user-attachments/assets/09b69673-50d3-4591-b7fc-ca94b50e8802" />

<img width="571" height="312" alt="image" src="https://github.com/user-attachments/assets/5ea5fa6b-ee70-4927-8333-4abc93c8806d" />

<img width="712" height="438" alt="image" src="https://github.com/user-attachments/assets/febc431e-8649-4b82-bc9d-37aabf9ca629" />

<img width="573" height="308" alt="image" src="https://github.com/user-attachments/assets/5f907097-8bf7-4d83-a8b2-8ba1650a7bb1" />

<img width="452" height="562" alt="image" src="https://github.com/user-attachments/assets/f455757b-be3d-4735-ae85-2578a7013897" />

<img width="441" height="447" alt="image" src="https://github.com/user-attachments/assets/0b83cecf-bd6b-4967-8929-caba769443f4" />

<img width="488" height="590" alt="image" src="https://github.com/user-attachments/assets/6f10d06c-b6b5-4994-b551-20885529f851" />

<img width="1020" height="641" alt="image" src="https://github.com/user-attachments/assets/f73d4ef9-fbcd-4b40-adbc-41ef4848e1c7" />

<img width="648" height="372" alt="image" src="https://github.com/user-attachments/assets/102733f6-f372-423d-b54e-002c27968c30" />

Now in this I don't see any user:
<img width="1023" height="637" alt="image" src="https://github.com/user-attachments/assets/247f3314-04f7-47d2-b549-42583e082fbc" />

After first I want to add Authorized user:
<img width="1217" height="721" alt="image" src="https://github.com/user-attachments/assets/cf33562d-ad58-407b-b24e-6c8f68b963d0" />

<img width="611" height="313" alt="image" src="https://github.com/user-attachments/assets/9660a1da-8231-4878-aac8-f8782ea1d763" />

<img width="767" height="468" alt="image" src="https://github.com/user-attachments/assets/3728fb4d-8e37-40b2-8680-f1d9c28305df" />

<img width="611" height="308" alt="image" src="https://github.com/user-attachments/assets/4d47f7fd-18c1-4fe5-9a6f-dddea9b65a58" />

<img width="1227" height="727" alt="image" src="https://github.com/user-attachments/assets/c6872e53-4232-44f8-abcc-1fcbb640fa23" />

Now I see `Admin` User:
<img width="1021" height="640" alt="image" src="https://github.com/user-attachments/assets/e6eb12d1-2473-458b-b175-5916c7a76626" />

After I want to add permission  to Group IT:
<img width="1217" height="732" alt="image" src="https://github.com/user-attachments/assets/1bf2b7a4-b865-4c3e-8cd7-70193e52b257" />

<img width="613" height="308" alt="image" src="https://github.com/user-attachments/assets/1e408485-85ad-460e-b85d-b102d7d08442" />


<img width="613" height="310" alt="image" src="https://github.com/user-attachments/assets/a8815a80-58fd-4117-ba62-c3c1057908cf" />

<img width="1221" height="730" alt="image" src="https://github.com/user-attachments/assets/50a5ba58-4010-4645-a020-1b8c2758d09d" />

<img width="1411" height="743" alt="image" src="https://github.com/user-attachments/assets/c5be60ad-9401-4885-bde3-ff3dbefd72a2" />

<img width="486" height="591" alt="image" src="https://github.com/user-attachments/assets/45c22db4-619b-4601-aef1-dcdb113aa5ea" />

Now we finished to add permission to group IT.


After I want to test create file in **Windows Client**, so in this on our **Windows Server** and IT folder -> `Right-Click` -> `Propertoes` -> `Sharing` below the `Network Path`:


<img width="1412" height="742" alt="image" src="https://github.com/user-attachments/assets/35a1f146-6455-47ee-a759-dced64192042" />

Now we see:
````
\\Dc01-ad\it
````
<img width="487" height="593" alt="image" src="https://github.com/user-attachments/assets/033c2a35-b4e9-4643-a75b-71c8bd5665c3" />


> **Note**: In this we need to click on folder IT after we do like above.

After Back to our **Windows Client**:

Go to `File Explorer` -> `Network` -> after type this:
````
\\Dc01-ad\it
````
or in this we can use this:
````
\\192.168.127.10\IT
````
<img width="1918" height="965" alt="image" src="https://github.com/user-attachments/assets/0d926041-9b37-4787-91a6-9704e4c88f7f" />

Now we see acces to folder IT.

> **Note**: In this we see to use with your IP, cause `192.168.127.10` is my IP.


After I  test to create one file, just `Right-Click`:
<img width="1357" height="790" alt="image" src="https://github.com/user-attachments/assets/fc8cc21c-b68e-4700-87c4-89c57249b0de" />

Now I can create file:
<img width="1005" height="652" alt="image" src="https://github.com/user-attachments/assets/66910763-976d-4d18-8799-f5253426d639" />

Now we got successful to allow permission.
---

##### Add permission from Sales Folder

In this I need to login into **Sales** user, so my user in **Sales** is:
````
Pe Pe
````
<img width="891" height="462" alt="image" src="https://github.com/user-attachments/assets/9799df69-37b8-4694-95b7-83c01bf324d7" />

If you want to check -> **Server Manager** -> **Tools** > **Active Directory Users & Computers** -> After we can view what folder that you want.

Now this my user Group **Sales** name `Pe Pe`:
<img width="1919" height="950" alt="image" src="https://github.com/user-attachments/assets/cb5b4fb5-ef67-4c97-9ef8-ac6026a56bd6" />


After back to our **Windows Server**:
<img width="1918" height="943" alt="image" src="https://github.com/user-attachments/assets/70ab2093-f76d-4ba0-86b0-32e5b9a4757e" />

After clear Inherit:
<img width="482" height="596" alt="image" src="https://github.com/user-attachments/assets/03fa50ba-b904-4e2a-a2ff-caa097f5d3ce" />

<img width="1022" height="640" alt="image" src="https://github.com/user-attachments/assets/09ed153c-7f8c-4050-96cf-c31ed4d484fe" />

<img width="643" height="375" alt="image" src="https://github.com/user-attachments/assets/1d96ea43-b94c-497e-9d44-5db04b030f98" />

<img width="1020" height="638" alt="image" src="https://github.com/user-attachments/assets/2d4579c2-a983-4df6-a0d6-d752ff7a94f8" />

<img width="553" height="241" alt="image" src="https://github.com/user-attachments/assets/4b4752e7-3967-4518-a3c9-5416408cf8d2" />

<img width="491" height="597" alt="image" src="https://github.com/user-attachments/assets/6352bb20-a810-43fe-9f4d-2976c494694b" />

<img width="487" height="561" alt="image" src="https://github.com/user-attachments/assets/ab03550e-143d-4196-b8b9-356fb88bdc05" />

<img width="603" height="307" alt="image" src="https://github.com/user-attachments/assets/7e68bf1a-e9af-410b-9d15-5a338a9b4a34" />

<img width="760" height="430" alt="image" src="https://github.com/user-attachments/assets/2bf2deeb-6ebc-40b1-b956-50bd0189235e" />

<img width="613" height="308" alt="image" src="https://github.com/user-attachments/assets/9601637d-2e4b-4002-8bed-e1d7defaf13b" />

<img width="487" height="552" alt="image" src="https://github.com/user-attachments/assets/b22e5162-8a42-4f19-824a-04802efb59b5" />

##### Add Group Sales
<img width="482" height="551" alt="image" src="https://github.com/user-attachments/assets/5d752cde-b553-4779-a4b3-7b1c609125ab" />

<img width="612" height="312" alt="image" src="https://github.com/user-attachments/assets/d39d883f-95eb-4281-85cd-19e0ef2df499" />

<img width="612" height="316" alt="image" src="https://github.com/user-attachments/assets/8c22d794-8993-4868-b3b7-280b37134044" />

<img width="482" height="553" alt="image" src="https://github.com/user-attachments/assets/5e24406e-1cd0-44ce-b750-119347312129" />

<img width="493" height="557" alt="image" src="https://github.com/user-attachments/assets/101c199f-b476-4081-8dc6-a7f6938fbd36" />

<img width="492" height="595" alt="image" src="https://github.com/user-attachments/assets/f1e3b3eb-1bd7-41e0-a302-844b5faf417a" />

Now we finshed to add permission.

After check path -> `Right-Click` on :
<img width="1275" height="803" alt="image" src="https://github.com/user-attachments/assets/ab095e68-d4c9-4534-a7ac-c747932be1f2" />

In this if we don't see Path, don't worry:
<img width="488" height="597" alt="image" src="https://github.com/user-attachments/assets/b629befe-0e71-4883-a318-f5f06a52ab42" />

Click on `Advance Sharing`:
<img width="447" height="457" alt="image" src="https://github.com/user-attachments/assets/5c52ba4e-711b-4cdd-9d03-8e7f3437ff50" />

<img width="452" height="563" alt="image" src="https://github.com/user-attachments/assets/cff45734-7137-4240-9191-0aa561f89115" />

<img width="450" height="557" alt="image" src="https://github.com/user-attachments/assets/8ec83f09-ac8d-489e-a20a-64e92437fb20" />

<img width="572" height="310" alt="image" src="https://github.com/user-attachments/assets/83db963c-a656-4878-b7ba-3e93c4198f77" />

<img width="712" height="437" alt="image" src="https://github.com/user-attachments/assets/b4bef391-0fa3-4f82-bc7d-6163fcd52178" />

<img width="577" height="317" alt="image" src="https://github.com/user-attachments/assets/7d8fe982-7e60-46c4-a43b-5399c4dd50c9" />

<img width="451" height="562" alt="image" src="https://github.com/user-attachments/assets/b0c583e6-2aa7-4324-9806-b408f12887ef" />

<img width="567" height="310" alt="image" src="https://github.com/user-attachments/assets/7357e94e-bb0b-4a9a-9a2f-b9d0326df890" />

<img width="573" height="315" alt="image" src="https://github.com/user-attachments/assets/23a7035e-32dc-420d-9029-4cece61d5b81" />

<img width="452" height="558" alt="image" src="https://github.com/user-attachments/assets/a0c3729c-8dcf-47e3-88e4-44ea1f66f3e8" />

<img width="437" height="460" alt="image" src="https://github.com/user-attachments/assets/ea10d183-8e34-49e1-8acb-badd1a1367c1" />

Now we see the Path:
<img width="486" height="595" alt="image" src="https://github.com/user-attachments/assets/8b371b11-514e-4067-a03e-d2eb7a883db8" />


After back to our **Windows CLient** -> after type this:
````
\\dc01-ad
````
<img width="1126" height="588" alt="image" src="https://github.com/user-attachments/assets/b9ac44d5-7216-41b0-99ea-e2fa888ad64e" />

Now we see folder **Sales**, After I test to create folder:
<img width="1126" height="582" alt="image" src="https://github.com/user-attachments/assets/4a739c31-250c-4448-8e46-c2b8d839b4a8" />

Now I have permission to create:
<img width="1126" height="589" alt="image" src="https://github.com/user-attachments/assets/9a3e20da-4836-45ae-963f-58f8e7a68f41" />

After I test to go to folder IT:
<img width="1128" height="599" alt="image" src="https://github.com/user-attachments/assets/d99a1ada-0c64-48bd-b65c-d4a4a3340395" />

Now I don't have permission into this.

---



### Create Mapdrive

After we create folder of Group then use ``MapDrive``, also in this I test with folder **Sales**, `Right-Click` on foder `Sales`:
<img width="1918" height="897" alt="image" src="https://github.com/user-attachments/assets/3fd229a3-7f26-4b79-9acb-7494a6c5e58c" />

After I set it to `s`, `s = sales`:
<img width="612" height="448" alt="image" src="https://github.com/user-attachments/assets/5fe0fac6-0896-40a2-92a7-9f470ec69a82" />

Now we see folder `Sales`:
<img width="1921" height="673" alt="image" src="https://github.com/user-attachments/assets/5aba5077-37a6-4ed1-80fc-c342a30b47f4" />

Now we got success.


#### Create Map Drive about Folder Public

Go to folder `Public`, `Right-Click` on folder `Public`:
<img width="1918" height="698" alt="image" src="https://github.com/user-attachments/assets/30d30ea5-cf10-42a5-8219-e4fe6482dda0" />

<img width="612" height="457" alt="image" src="https://github.com/user-attachments/assets/0cba5fea-f7c8-4060-8d68-7f03c1ed43ea" />

Now we see folder `Public`:
<img width="1128" height="591" alt="image" src="https://github.com/user-attachments/assets/0e1704d7-11dd-4049-9bdd-d1197e21f703" />

Now we got success to create folder.

Afte I test, in this I `Shutdown` my PC:
<img width="1749" height="744" alt="image" src="https://github.com/user-attachments/assets/e4b81c3b-3ac1-4cfe-844d-3493dba92604" />

Now after I open back I still see:
<img width="1918" height="675" alt="image" src="https://github.com/user-attachments/assets/03c8c732-adba-4dfb-8e4c-90c9a17633eb" />

Now we finished to completed share folder.


---
