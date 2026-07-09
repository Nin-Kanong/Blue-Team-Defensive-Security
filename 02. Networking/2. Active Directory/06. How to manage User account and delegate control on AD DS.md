<h1 align="center"> How to manage User account and delegate control on AD DS </h1>

<img width="1536" height="700" alt="image" src="https://github.com/user-attachments/assets/7ddab1d2-0daa-44bc-95a6-655ff4e8bcf2" />

---


## Introduction to How to manage User account and delegate control on AD DS

**Managing user accounts in Active Directory Domain Services (AD DS)** involves creating, modifying, and controlling access for users, while delegation of control allows administrators to assign specific administrative tasks to other users or groups without giving them full domain admin rights. This ensures security, scalability, and efficient management of large organizations.

### Managing User Accounts in AD DS
User accounts are the foundation of identity in Active Directory. They allow individuals to log in, access resources, and be assigned permissions.
- **Create user accounts** → Done via the Active Directory Users and Computers (ADUC) console.
- **Reset passwords** → Admins can force password changes at next logon.
- **Enable/disable accounts** → Useful for onboarding/offboarding employees.
- **Manage group memberships** → Assign users to security or distribution groups.
- **Remove accounts** → Deletes accounts when no longer needed.

By default, Domain Admins and Enterprise Admins can manage all accounts. Account Operators can create/modify/delete user accounts but cannot manage groups or permissions.



### Delegation of Control in AD DS
Delegation allows you to give limited administrative rights to non-admin users or groups. This prevents overuse of Domain Admin privileges and improves security.

#### Why Delegate?
- **Security** → Reduces risk by limiting who has full admin rights.
- **Efficiency** → Department admins can manage their own users without IT intervention.
- **Scalability** → Large organizations can distribute management tasks.


#### How It Works
- Create Organizational Units (OUs) to group users, computers, or resources.
- Use the Delegation of Control Wizard in ADUC to assign permissions.
- We can delegate tasks such as:
   - Create/delete/manage user accounts
   - Reset passwords
   - Modify group membership
   - Join computers to domain
   - Manage Group Policy links


#### Example OU Delegation Structure
| OU (Organizational Unit) | Purpose                                 | Delegated Control                             |
| ------------------------ | --------------------------------------- | --------------------------------------------- |
| **Users OU**             | Stores employee user accounts           | HR team can create and disable user accounts  |
| **Computers OU**         | Stores workstation computer accounts    | IT staff can join PCs to the domain           |
| **Groups OU**            | Stores security and distribution groups | Department leads can manage group memberships |
| **Admins OU**            | Stores administrator accounts           | Restricted access for Domain Admins only      |



---


## Managing User Accounts in AD DS

### Create group and user
In this if we not yet create Group and user, go to **Server Manager**:
<img width="1918" height="883" alt="image" src="https://github.com/user-attachments/assets/1860e4ad-ae2f-474d-891f-fe3ade1f4bb8" />

After create **OU** or group, also in this I already create **Group IT** so i don't want to create new. if you want to create new go to my path: https://github.com/Nin-Kanong/Blue-Team-Defensive-Security/blob/main/02.%20Networking/2.%20Active%20Directory/3.%20Create%20User%20%26%20Group%20Account%20AD.md#check-on-it-ou

After In this if we ready to create OU and user after go to **Windows Client**:
<img width="1914" height="949" alt="image" src="https://github.com/user-attachments/assets/98aa4418-dfc1-40a6-a1dd-37ea4539e0b9" />

Now this my computer that was join domain. Also if we have others computer that we was join but not yet have group then go to our **Windows Server** -> On **Active Directory Users & Computer**:
<img width="1087" height="522" alt="image" src="https://github.com/user-attachments/assets/4426961f-32c5-4541-a560-71da4114979c" />

also in this I see computer that i was login stay in **Group IT** after in this if we want to see what computer that notyet have domin -> go to **Computer**:

Now I see user `k4n0ng`:
<img width="806" height="401" alt="image" src="https://github.com/user-attachments/assets/83474606-1339-4982-9b5e-d3fa08366089" />

So in this if we want to move this user to what group that we want we can move it, and in this I test to move to Group **Finance**, just `Right-Click` on user `k4n0ng`:

<img width="902" height="461" alt="image" src="https://github.com/user-attachments/assets/ff3cb080-d4db-4649-bd70-438ef21e384f" />

<img width="397" height="408" alt="image" src="https://github.com/user-attachments/assets/2dd8983d-e042-4ca4-9759-bda6af5d4ab5" />

After go to **Group Finance**, now we see user `k4n0ng`:
<img width="857" height="401" alt="image" src="https://github.com/user-attachments/assets/474dbf44-ab80-4f74-86de-a68879140856" />

---


### Disable Computer

On `IT Group`, in this I want to `Disable` user `Ronaldo`, just `Right-Click`:
<img width="1055" height="548" alt="image" src="https://github.com/user-attachments/assets/4133f6b6-7d0c-4aa9-9794-089e96685806" />

  <img width="402" height="212" alt="image" src="https://github.com/user-attachments/assets/f353540b-be2c-4863-b5ba-6dec4406778b" />

In **Active Directory (AD DS)**, when we choose **Disable Account**, it means the user account is temporarily turned off — the account still exists, but the person cannot log in or access resources until it is re‑enabled.

###### What “Disable” Does
- **Employee leaves temporarily** → Disable instead of deleting, so you can restore access later.
- **Security incident** → Quickly block a compromised account.
- **Onboarding delay** → Create the account early but keep it disabled until the employee starts.


###### Difference from Delete
- **Disable** → Account remains in AD, but inactive.
- **Delete** → Account is permanently removed, along with group memberships and permissions.

---


#### Test Login on Client:
I test login user `Ronaldo` on my **Windows Client**:
<img width="1918" height="932" alt="image" src="https://github.com/user-attachments/assets/5db98fa0-3d8f-465c-bcca-51432a1d387c" />

Now we see our Account has been disable:
<img width="1305" height="681" alt="image" src="https://github.com/user-attachments/assets/c7a01dc0-64d4-4239-a86c-3106d5d53766" />

now we finsiehd to disable account.

---



### Delegate

**Delegation** in AD DS lets we safely share admin responsibilities by granting limited rights to specific users or groups, usually at the OU level.




#### Folder and OU
In this we need to know about `Folder` and `OU`:
**Organizational Units (OUs)** and **Folders** look similar at first glance because both are containers, but in Active Directory Domain Services (AD DS) they serve very different purposes.


#### Folder
| Feature            | Description                                                                   |
| ------------------ | ----------------------------------------------------------------------------- |
| **Location**       | Exists on a file system (such as `C:\` drive or a network share).             |
| **Purpose**        | Stores files and subfolders for organizing data.                              |
| **Access Control** | Managed using NTFS permissions such as Read, Write, Modify, and Full Control. |
| **Scope**          | Focuses only on data storage and file management.                             |
| **Example**        | `C:\FinanceDocs` stores spreadsheets, reports, and other documents.           |


#### Organizational Unit (OU)
| Feature            | Description                                                                                |
| ------------------ | ------------------------------------------------------------------------------------------ |
| **Location**       | Exists inside **Active Directory**, not in the file system.                                |
| **Purpose**        | Logical container used to organize users, groups, computers, and other OUs.                |
| **Access Control** | Managed through **delegation of control** (who can manage objects inside the OU).          |
| **Scope**          | Used for administration, Group Policy application, and delegation — not for storing files. |
| **Example**        | `OU=Finance` contains Finance department user accounts and computers.                      |


#### Key Differences
| Feature            | Folder                                                        | OU (Organizational Unit)                          |
| ------------------ | ------------------------------------------------------------- | ------------------------------------------------- |
| **Where it lives** | File system                                                   | Active Directory                                  |
| **What it holds**  | Files and subfolders                                          | Users, groups, computers, and other OUs           |
| **Permissions**    | NTFS security permissions (Read, Write, Modify, Full Control) | Delegation of control and Group Policy settings   |
| **Purpose**        | Data storage and file organization                            | Identity management and policy administration     |
| **Example use**    | Store documents and reports                                   | Apply GPO settings to Finance users and computers |



---

In folder we have 2 feature:
1. Sharing
2. Secuity

<img width="1430" height="855" alt="image" src="https://github.com/user-attachments/assets/066fae48-e94a-48a0-8f1e-32a5ec51e620" />


In **OUs** also have 2 feature:
1. Deleigate Control
2. Link Group Policy

<img width="854" height="430" alt="image" src="https://github.com/user-attachments/assets/8b6c2c09-03d0-446e-bd9c-fadf64413ea2" />

In this can see detail, just go to back to our **Server Manager**:

<img width="1918" height="872" alt="image" src="https://github.com/user-attachments/assets/52ebb27d-4dc5-45d4-8718-542f4b1fbc40" />

<img width="899" height="508" alt="image" src="https://github.com/user-attachments/assets/201265b0-e9dd-41f6-a3cc-74401c685958" />

`Right-Click` on OU and now we see `Group Policy`:
<img width="838" height="673" alt="image" src="https://github.com/user-attachments/assets/a2e65f32-b480-4133-8d84-df1d16e41339" />

---



#### Delegate 
Go back to our `Active Directory Users & Computer`, `Right-Click`:
<img width="765" height="737" alt="image" src="https://github.com/user-attachments/assets/f23d6a61-d153-4b67-944f-41082e5327c3" />

<img width="618" height="485" alt="image" src="https://github.com/user-attachments/assets/010d0db6-63d7-45d7-aad1-30e39f5fd36c" />


<img width="622" height="497" alt="image" src="https://github.com/user-attachments/assets/95aa187a-cfbb-4a3c-8d17-fdf3d3a4296d" />

In this we can deligate to what user that we want, also in this I want to deligate to user `Nin Kanong`:
<img width="567" height="308" alt="image" src="https://github.com/user-attachments/assets/707b206f-e75c-4773-a396-5813b7cb2f7d" />

<img width="571" height="311" alt="image" src="https://github.com/user-attachments/assets/9ebce7ba-49ea-470a-b54f-50f8043109bb" />


<img width="620" height="483" alt="image" src="https://github.com/user-attachments/assets/c9ed13ee-14a6-4592-b75a-76de2151db1a" />

Now I deligate this to user `Nin Kanong`:
<img width="622" height="490" alt="image" src="https://github.com/user-attachments/assets/35a0e67a-41dc-4fd1-9392-4963707f97e3" />

**Delegation** of Control Wizard in Active Directory Users and Computers (ADUC). It’s showing the step where you choose which tasks to delegate to another user or group.

Here are all the options you can delegate from this wizard:
| Delegation Permission                                                     | Description                                                                            | Purpose / Usage                                                      |
| ------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| **Manage Group Policy links**                                             | Allows linking or unlinking Group Policy Objects (GPOs) to Organizational Units (OUs). | Used to control which policies apply to users and computers.         |
| **Generate Resultant Set of Policy (Planning)**                           | Simulates how GPOs will apply in a planned scenario before making changes.             | Helps test policy effects without applying them.                     |
| **Generate Resultant Set of Policy (Logging)**                            | Shows reports of which GPOs are actually applied to users or computers.                | Used for troubleshooting and auditing policies.                      |
| **Create, delete, and manage inetOrgPerson accounts**                     | Allows management of LDAP-compatible user objects.                                     | Used for directory integrations and special account management.      |
| **Reset inetOrgPerson passwords and force password change at next logon** | Allows resetting passwords for inetOrgPerson accounts.                                 | Helps administrators manage user access.                             |
| **Read all inetOrgPerson information**                                    | Provides read-only access to inetOrgPerson object properties.                          | Used for viewing account details without modification rights.        |
| **Create a custom task to delegate**                                      | Allows creation of specific delegated permissions.                                     | Gives limited access, such as editing only selected user attributes. |



After click `Finish`:

<img width="620" height="486" alt="image" src="https://github.com/user-attachments/assets/274c64d0-f5e0-4a93-9edf-ecab9e8f1b57" />

Now we finished to delegate.


---


#### Test user

In this I test login into user `Nin Kanong`, also in this I test login normal user in **Windows Server**, And first in this I `Sign out` from my **Windows Server**.

Just press `Ctrl + X`:
<img width="1915" height="943" alt="image" src="https://github.com/user-attachments/assets/22b31b66-53f1-4573-b0eb-ded2a1e00265" />

After I test login:
<img width="1918" height="1048" alt="image" src="https://github.com/user-attachments/assets/872bae9d-127f-4bdd-acd1-36bc3670f864" />


<img width="1914" height="938" alt="image" src="https://github.com/user-attachments/assets/d664b622-b4f8-49c7-b154-2b8dad984ca9" />

Now it show this:

<img width="1703" height="769" alt="image" src="https://github.com/user-attachments/assets/6598190e-26c1-4031-a649-9a6ec74698a9" />

That login error — ``The sign‑in method you’re trying to use isn’t allowed`` — comes from Active Directory Domain Services (AD DS) or Group Policy restrictions. It means the authentication method you tried (like username/password, smart card, or another logon type) has been blocked for that account or computer.

> **Note**: In this normal user can't login into server.

Common Reasons
- **Logon restrictions** → The account is only allowed to log on to certain computers, and you tried on one outside that list.
- **Authentication method blocked** → For example, smart card logon required, but you tried password.
- **Group Policy settings** → Admins may enforce rules that disable certain sign‑in methods.
- **Account disabled** → If the account is disabled, any login attempt will fail.
- **Delegation or OU policy** → The OU where the account resides may have restrictions applied.


---


### Denied Logon Hour

**Logon Hours** are a security feature that lets administrators control when a user account is allowed to sign in to the domain.

##### What Logon Hours Mean
- **Time restrictions** → You can define specific days and times when a user can log on.
- **Access control** → Outside those hours, the user cannot authenticate to the domain.
- **Policy enforcement** → Helps enforce working hours or security rules.

##### Example
- HR staff accounts → Allowed to log on Monday–Friday, 8 AM–6 PM.
- IT admins → Allowed 24/7 access.
- Temporary staff → Restricted to specific shifts only.

#### Config Log on Hour
Go back to our **Windows Server** -> Go to **Server Manager**:
<img width="1091" height="952" alt="image" src="https://github.com/user-attachments/assets/a4d4a2ca-5b11-4cc0-9987-da614b9ddeb4" />

<img width="1918" height="887" alt="image" src="https://github.com/user-attachments/assets/5fd19d6e-3842-415e-b0fe-6fc04d386e47" />

Now In this I want to use with **Group IT**:
<img width="876" height="469" alt="image" src="https://github.com/user-attachments/assets/ea11f7e0-ba15-49a3-80c5-1abcc0f00040" />

Also in this I wan to use `Log on Hour` with user `Ronald`, But in this in my user `Ronaldo` i was `Disable` it then I `Enable` it back:

<img width="1040" height="552" alt="image" src="https://github.com/user-attachments/assets/9216f545-9bfb-4ab1-81c0-7ad1e1a7cd17" />

<img width="405" height="218" alt="image" src="https://github.com/user-attachments/assets/f7d1ed93-2d5c-46e0-a814-cad03fcad6e2" />


Now I was `Enable` it then I do `Log on Hour`, just `Right-Click` on user `Ronaldo`:
<img width="1072" height="555" alt="image" src="https://github.com/user-attachments/assets/e502f11c-2b67-4ac6-ac76-0dd967e6b135" />

On `Account` -> click on `Logon Hours`:
<img width="518" height="682" alt="image" src="https://github.com/user-attachments/assets/4c866966-e7df-4402-875e-caa35df43119" />

Now we see this, after click `Logon Denied`:
<img width="632" height="402" alt="image" src="https://github.com/user-attachments/assets/f157a7e8-d882-403b-950c-606ec2f951f9" />

Also in this I want to allow time from `Monday` to `Friday` and time from `8 AM` to `5PM`:
<img width="632" height="400" alt="image" src="https://github.com/user-attachments/assets/8133fec7-d0b6-477b-926b-077b456e10e0" />


After click on `Logon Permitted`:
<img width="637" height="407" alt="image" src="https://github.com/user-attachments/assets/fe920c1a-d0ae-4ec6-976d-a18cd43646bc" />


<img width="627" height="400" alt="image" src="https://github.com/user-attachments/assets/518e5484-43d3-4f8f-8788-f03580c9e1a2" />


<img width="518" height="677" alt="image" src="https://github.com/user-attachments/assets/ad41d83f-92fa-4987-8842-3d60b1f98ad2" />

Now we finished to set `Logon Hours`.

---


#### Test login 

In this right now I time is `10 PM`, after I test to login to user `Ronaldo` on this time.

Go back to our **Windows Client**:
<img width="1919" height="931" alt="image" src="https://github.com/user-attachments/assets/8d04cf51-b337-4660-9c65-04e3f38c00e6" />


Now we got success to assign `Logon Hours`:
<img width="1133" height="688" alt="image" src="https://github.com/user-attachments/assets/8f9f3f98-39a1-4061-82ce-d8a659c7b1d5" />

**Logon hours restriction** → Our account has a schedule set by the administrator that defines when you’re allowed to log in.

---


### Permitted Logon Hours
Go back to our **Windows Server** and back to our `Active Directory Users & Computer`.

In this I want to `Permitted` all time to user `Nin Kanong`

Just `Right-Click` on `Nin Kanong`:
<img width="1066" height="616" alt="image" src="https://github.com/user-attachments/assets/e7275298-9a3a-4381-a8f2-800c7fc974fa" />


<img width="513" height="675" alt="image" src="https://github.com/user-attachments/assets/21095e7e-837f-48b5-baab-45324186c4e9" />

Now I see this:
<img width="636" height="400" alt="image" src="https://github.com/user-attachments/assets/51441797-bc33-44c2-a16d-69ffc5f9670f" />


After `Hold` full of it:
<img width="632" height="402" alt="image" src="https://github.com/user-attachments/assets/f5dd8947-612c-4772-b33e-e37b64c455b9" />


<img width="635" height="406" alt="image" src="https://github.com/user-attachments/assets/5e599861-6d3e-4b4b-8229-36ecba8dc894" />


<img width="516" height="668" alt="image" src="https://github.com/user-attachments/assets/9d588e6f-cc97-4a27-8c74-00e7dab292b0" />

Now we was finsihed to assign `Lohon Hours`.

---

#### Test Login 

In this after I asign `ogon Hours`, then go back to our **Windows Client**.

Also in this I assign `Logon Hours` with user `Nin Kanong`, so I login into user `Nin Kanong`:

<img width="930" height="635" alt="image" src="https://github.com/user-attachments/assets/44aee914-c4ed-4175-a0cc-74cac9968b46" />


Now I was login into user `Nin Kanong`:
<img width="1919" height="942" alt="image" src="https://github.com/user-attachments/assets/0a9feae5-dd64-41ca-8fc9-45bb5f5607b1" />

Now we got success.


---



## Install Admin Tool
In this after I delegate to user `Nin Kanong` and asign full `Logon Hours`, then we install **Admin Tool**.

Go to `Control Panel`, just `Ctrl + S` -> search:
````
control Panel
````
<img width="1918" height="937" alt="image" src="https://github.com/user-attachments/assets/f7fef068-2af3-4c33-9716-87f47234fd4a" />


<img width="1918" height="660" alt="image" src="https://github.com/user-attachments/assets/54775064-0b06-41ca-97a1-40bb01182740" />


<img width="833" height="327" alt="image" src="https://github.com/user-attachments/assets/859009ad-5f0d-4667-a9b9-6057907055b9" />


Now we see it require Username and Password admin:
<img width="461" height="476" alt="image" src="https://github.com/user-attachments/assets/61e1612d-bf56-4f83-8d26-8e25c6d5fe4a" />

In this that why we join domain, cause it can divide which `Administrator` and which `Normal user`.

After In this I login with Username and Password of admin:
<img width="457" height="487" alt="image" src="https://github.com/user-attachments/assets/bdb73b48-04fc-44d9-9a9a-c34d254d4d44" />



After it show this:
<img width="422" height="372" alt="image" src="https://github.com/user-attachments/assets/ff5911ff-1c81-4a8c-9a92-4a1dd65a3dc2" />

After find `Remote Admin`:
<img width="990" height="784" alt="image" src="https://github.com/user-attachments/assets/8d3a5b72-2881-4cf3-b348-4d5dc7d2bef9" />

But in this I don't see `Remote Admin`, so in this we need to install it.

Also in this we need to have **Internet** to access t internet. And my desktop already have **Internet**:
<img width="1918" height="938" alt="image" src="https://github.com/user-attachments/assets/f1c02e5c-708d-43ec-90da-da3cf527762c" />

If your desktop don't have **Internet** do follow my document: 
[How to make Windows Server have Internet.pdf](https://github.com/user-attachments/files/29179096/How.to.make.Windows.Server.have.Internet.pdf)

This my document will help you a lots to make your computer help **Internet** by you don't do any ways that can make you streess to change back.



#### Install Remote Server Admin on browser
In this after we already have **Internet** then go to browser and install tool:
````
Remote Server Admin
````

Also in this I go to Google first:
````
google.com
````
<img width="1901" height="892" alt="image" src="https://github.com/user-attachments/assets/548c5918-2d5c-436f-8641-c707af666473" />

Now we see we go to google by don't use Chrome:
<img width="1918" height="803" alt="image" src="https://github.com/user-attachments/assets/d5937d72-db9a-48d1-9ffb-14a36591c97c" />

After search this:
````
remote server admin tool
````
<img width="1917" height="806" alt="image" src="https://github.com/user-attachments/assets/41fac17c-fb92-4ac1-a40b-c53e1a9aa448" />

Also in this I choose with **Windows 10**, cause now I use windows 10 to test, if your windows that for test in VM is windows 11 your choose windows 11.

Now I see this:
<img width="1919" height="889" alt="image" src="https://github.com/user-attachments/assets/1c54a8af-26fd-42ce-8b91-be57ec84c6e9" />


After Scroll down:
<img width="1897" height="877" alt="image" src="https://github.com/user-attachments/assets/307c2747-e9df-4518-89d4-0687bcbd4f99" />


Now in this I used Powershell to install.

Go to our windows -> After press `Ctrl + S` -> search: 
````
powershell
````
After choose admin:

<img width="892" height="941" alt="image" src="https://github.com/user-attachments/assets/e87f890e-3cf2-48bf-9a34-0818998a7bf7" />

After it will require password:

<img width="457" height="477" alt="image" src="https://github.com/user-attachments/assets/cfebee87-881b-4032-b800-a8db224b991e" />

After I input Username and password admin:

<img width="451" height="478" alt="image" src="https://github.com/user-attachments/assets/a59864fc-4ca6-4514-b730-4683cdfb0c63" />

Now it was open it:

<img width="818" height="362" alt="image" src="https://github.com/user-attachments/assets/3b92ff18-b8e7-4007-8b15-edf875f583c5" />


After I check **Remote Server Admin** first:
````
Get-WindowsCapability -Name RSAT* -Online
````
<img width="1692" height="899" alt="image" src="https://github.com/user-attachments/assets/653d1377-0d1a-4634-bec0-c2ba4c1427a5" />


PowerShell is the list of RSAT (Remote Server Administration Tools) features available on Windows 10.


##### Install RSAT
````
Add-WindowsCapability -Online -Name Rsat.ActiveDirectory.DS-LDS.Tools~~~~0.0.1.0
````
<img width="951" height="263" alt="image" src="https://github.com/user-attachments/assets/fa8cdbe5-4f54-42f5-8cbd-219151a0d6cc" />

It it start to install.

<img width="802" height="208" alt="image" src="https://github.com/user-attachments/assets/ba7cd67f-d6bc-4654-89f4-0ad6071c7b69" />

Now the command shows that RSAT Active Directory DS-LDS Tools was successfully installed.

Also in this when we install `Remote Server Admin` cause it can help us that can bypass security to make normal user or not administrator can login into **Server**.


---




### Group Policy Management

After back to our **Windows Server** -> After go to **Server Manager**:

<img width="1918" height="890" alt="image" src="https://github.com/user-attachments/assets/e3caeb5d-e30f-4808-a737-ce83879de0a2" />

<img width="803" height="598" alt="image" src="https://github.com/user-attachments/assets/60ffdc97-90c8-4b99-8843-15b4a5b9c561" />

| Active Directory Component      | Description                                                                           | Purpose / Usage                                                                 |
| ------------------------------- | ------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------- |
| **Forest**                      | The top-level container of an Active Directory environment (example: `cybersec.com`). | Contains all domains, users, computers, and policies in the AD environment.     |
| **Domain**                      | A container inside the forest that stores users, computers, and policies.             | Manages authentication, resources, and security settings.                       |
| **Organizational Units (OUs)**  | Sub-containers such as Accounting, Finance, IT, and Sales.                            | Organizes users/computers and allows GPO application.                           |
| **Group Policy Objects (GPOs)** | Policies that control Windows settings.                                               | Manage password rules, software installation, restrictions, and configurations. |
| **Default Domain Policy**       | Built-in GPO applied to the entire domain.                                            | Controls domain-wide settings like password policy and account lockout rules.   |
| **WMI Filters**                 | Advanced filters that apply GPOs only when conditions are met.                        | Targets policies based on OS version, hardware, or system conditions.           |
| **Starter GPOs**                | Templates used to create new GPOs.                                                    | Speeds up creation of standard policies.                                        |
| **Group Policy Modeling**       | Simulation tool that predicts GPO application.                                        | Tests how policies will affect users/computers before deployment.               |
| **Group Policy Results**        | Reports showing which GPOs were actually applied.                                     | Troubleshoots and verifies applied policies.                                    |



After click on `Default Domain Policy`:

<img width="1232" height="601" alt="image" src="https://github.com/user-attachments/assets/eb0465a2-136a-474a-8752-29af14f0a634" />

After we will see this:

<img width="1918" height="860" alt="image" src="https://github.com/user-attachments/assets/450dab7b-f0fe-4ccf-95ff-49584d51ec26" />

After `Right-Click` -> `Edit`:

<img width="1191" height="887" alt="image" src="https://github.com/user-attachments/assets/2c5e416a-0329-43a6-9b30-f3ff1d456d2c" />


After Click `Computer Configuration` -> `Policies` -> `windows Settings` -> `Security Settings` -> `Local Policies` -> `User Rights Assignment`:

<img width="1260" height="863" alt="image" src="https://github.com/user-attachments/assets/99dc0402-6d23-4e2c-b952-f9c6352bb31b" />


After `Double-Click` on `Allow log on through Remote Desktop Services`:
<img width="1918" height="888" alt="image" src="https://github.com/user-attachments/assets/55ba8924-6e06-4faa-9287-07bc791f356c" />

In this I input my name:
````
kanong
````
<img width="461" height="201" alt="image" src="https://github.com/user-attachments/assets/5ffcd673-d3d9-4001-ac98-15361a88356b" />

You can input your user that you want to give permission to get admin.

After input our name user that we want:

<img width="572" height="311" alt="image" src="https://github.com/user-attachments/assets/81e3d78b-9891-466d-821a-61f1bc294384" />


Now this my user:
<img width="573" height="315" alt="image" src="https://github.com/user-attachments/assets/3a0a27a7-af53-447a-8857-a85fd0867a3c" />


<img width="462" height="200" alt="image" src="https://github.com/user-attachments/assets/141a2997-c4b0-4e88-a1bb-248b274f56c0" />


<img width="517" height="640" alt="image" src="https://github.com/user-attachments/assets/bf4d2c94-e56e-47fc-8606-356fecb7746d" />

Now we finished to allow `Remote Admin`.

---


### Test with Remote Server Admin

Also in this after we finshed to install `Remote Server Admin`, then test it.

Go back to our **Windows Client**:
<img width="1919" height="939" alt="image" src="https://github.com/user-attachments/assets/6d52bde1-a130-4b35-b62f-56b6cbddb3f8" />


After go to `Remote Desktop`, just press `Windows + S` -> After search:
````
Remote Desktop Connection
````
After run it as `Admin`:
<img width="862" height="939" alt="image" src="https://github.com/user-attachments/assets/7e5bb96c-8896-454c-a04f-6a8c8afa6984" />

After it will require to type admin:
<img width="457" height="477" alt="image" src="https://github.com/user-attachments/assets/fb7231d0-9da1-482e-af1c-31144915c911" />


After input our name of our **Windows Server**, in this we need to input computer name of wndows server.

Also if you don't know your computer name just go to **Windows Server** -> **Server Manager**:

<img width="1921" height="892" alt="image" src="https://github.com/user-attachments/assets/a5db2059-3b88-466d-879c-c9d75b655395" />

Also this my computer name:
````
DC01-AD
````
Alo we can user small letter:
````
dc01-ad
````


After back to our **Windows Client** -> After input our computer name to remote:
````
dc01-ad
````
<img width="406" height="257" alt="image" src="https://github.com/user-attachments/assets/591f294c-c774-4756-8ee2-fab35374d7dc" />

After it start it will require password.
<img width="1913" height="942" alt="image" src="https://github.com/user-attachments/assets/d6797c5c-793b-427c-9835-aab3dfdcbd6c" />

Just input our password:
<img width="457" height="341" alt="image" src="https://github.com/user-attachments/assets/621db94f-83c1-4ced-a3ef-d7c8d1b55165" />


Now we success full to remote to our **Windows Server**:
<img width="1919" height="943" alt="image" src="https://github.com/user-attachments/assets/4c1bc97c-0856-4437-8de3-5cb2366ca02a" />

<img width="1919" height="938" alt="image" src="https://github.com/user-attachments/assets/3e6640ae-7a08-41e8-89cc-aad96f2c84e8" />

Now we finished this lab.


---
