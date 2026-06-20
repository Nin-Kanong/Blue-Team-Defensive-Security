<h1> How to setup and configure File Screening - Disk Quota </h1>

<img width="1536" height="700" alt="image" src="https://github.com/user-attachments/assets/a2ff6e6c-4816-473b-84b8-1c12bb6a82d1" />

---

## Introducion

**File Screening and Disk Quotas** are features of Windows Server’s **File Server Resource Manager (FSRM)** that help administrators control how storage is used. File Screening restricts the types of files users can save, while Disk Quotas limit the amount of space users or folders can consume. Together, they enforce storage policies and prevent misuse.

### File Screening
- **Purpose**: Controls the types of files users can store on a server.
- **How it works**: we define rules based on file extensions (e.g., block .mp3, .exe, or .iso).
- **Notifications**: Can alert admins when users attempt to save unauthorized files.
- **Templates**: we can create reusable screening templates for consistency across multiple folders.
- **Exceptions**: Specific users or folders can be exempted (e.g., allow IT staff to store .exe files).

> Example: Prevent employees from saving personal music files in shared work folders.


### Disk Quotas
- **Purpose**: Limits the amount of storage space a user, group, or folder can use.
- **How it works**: You set a quota (e.g., 5 GB per user). Once reached, users are blocked or warned.

Types of quotas:
- **Hard quota** → Strict limit; users cannot exceed it.
- **Soft quota** → Allows exceeding but generates warnings/reports.
- **Templates**: Standard quota sizes can be applied quickly to new folders.
- **Reports**: Helps track usage trends and identify who consumes the most storage.

> Example: Restrict each department’s shared folder to 100 GB to prevent one team from consuming all disk space.


### Key Differences
| Feature           | File Screening                                              | Disk Quota                                                |
| ----------------- | ----------------------------------------------------------- | --------------------------------------------------------- |
| **Controls**      | File types (extensions)                                     | Storage space (GB/MB)                                     |
| **Use Case**      | Blocks unwanted file types (e.g., media files, executables) | Prevents users from using excessive disk space            |
| **Notifications** | Alerts when blocked files are attempted or saved            | Alerts when quota limit is reached or nearly exceeded     |
| **Flexibility**   | Can allow exceptions for specific users or folders          | Supports soft quotas (warning) and hard quotas (blocking) |
| **Goal**          | Maintain security, compliance, and control over file types  | Ensure fair storage usage and prevent disk overuse        |



---



### Install role FSRM

First go to **Server Manager**, just press `Ctrl + S` -> search:
````
server manager
````
<img width="1042" height="940" alt="image" src="https://github.com/user-attachments/assets/f495dad9-a410-4688-9aab-134a7690a4f5" />

After click on `Add roles and feature`:

<img width="1918" height="883" alt="image" src="https://github.com/user-attachments/assets/b9ffe93e-ff8c-4fd3-8784-ecf7fc108348" />

<img width="986" height="692" alt="image" src="https://github.com/user-attachments/assets/84d6e263-bd9a-4031-b845-d7d1bad1866c" />

<img width="985" height="700" alt="image" src="https://github.com/user-attachments/assets/56071301-d2a0-4824-b95b-feb381997e45" />

<img width="986" height="702" alt="image" src="https://github.com/user-attachments/assets/63c89c4d-11e0-413c-87d3-7eda48734b0a" />

<img width="1917" height="888" alt="image" src="https://github.com/user-attachments/assets/253a68e0-0712-4577-826a-af0ec45cdce5" />

<img width="1918" height="887" alt="image" src="https://github.com/user-attachments/assets/ac4f366b-6220-49ed-81da-27f71a33b15e" />


<img width="1918" height="886" alt="image" src="https://github.com/user-attachments/assets/ccc0a5ce-5e4b-4a98-9a14-f9fd8c1585d9" />

<img width="1918" height="883" alt="image" src="https://github.com/user-attachments/assets/1948aa4c-2856-4d94-b49c-fa73f801c082" />

<img width="980" height="700" alt="image" src="https://github.com/user-attachments/assets/843d6fb4-709c-4f5b-ad04-8388ecf72f40" />


#### After create Group And OU
<img width="1917" height="886" alt="image" src="https://github.com/user-attachments/assets/98299f2c-7c07-4669-85a7-aa9f7d130470" />

Also in this I already create **OU, Group and User**:
<img width="835" height="427" alt="image" src="https://github.com/user-attachments/assets/b15c6502-603c-49d2-86ba-010b45a69ba0" />

If in this you not yet create this go to my this path: https://github.com/Nin-Kanong/Blue-Team-Defensive-Security/blob/main/02.%20Networking/2.%20Active%20Directory/3.%20Create%20User%20%26%20Group%20Account%20AD.md#check-on-it-ou


After go to folder -> go to `Local Disk (C:)`, after create folder and also I was create it:
<img width="1025" height="772" alt="image" src="https://github.com/user-attachments/assets/51a39a74-73f6-46df-8fbf-89e5d184f2a6" />

Also in this we need to add permission, also if you not yet create and allow permission go to my path: https://github.com/Nin-Kanong/Blue-Team-Defensive-Security/blob/main/02.%20Networking/2.%20Active%20Directory/4.%20ADDS%20RecycleBin%20Sharing%20%24%20Emunmeration.md#after-go-to-access-folder


---


#### On Windows Client
In this on **Windows Client** login into User that stay in **Group IT**:
<img width="1918" height="923" alt="image" src="https://github.com/user-attachments/assets/ba60366b-1b3f-4943-be9d-57514028b907" />

After go to `File Explorer`, after type:
````
\\dc01-ad\
````
<img width="1918" height="945" alt="image" src="https://github.com/user-attachments/assets/f112f94a-1f8c-4237-8017-1af43c9a443a" />

In it don't see my `ITDocs` cause in this I used `ITDocs` with `$` so in this it hidde.



#### Also in this I create one more Folder 

##### Create folder for IT Group
ON **Windows Server** -> go to `File Explorer`:
<img width="1918" height="883" alt="image" src="https://github.com/user-attachments/assets/a30b317b-7be0-4bf7-a21c-ae31a4295530" />

In this I input name of it is:
````
IT_Red-Team-Operator
````
<img width="1020" height="797" alt="image" src="https://github.com/user-attachments/assets/89166883-0e45-4393-8083-e67ced013f74" />

After add permission, `Right-Click` on `IT_Red-Team-Operator` -> `Properties`:

<img width="1286" height="790" alt="image" src="https://github.com/user-attachments/assets/1b41fa00-f468-44c2-8f19-47370c206323" />


<img width="491" height="670" alt="image" src="https://github.com/user-attachments/assets/645654f6-cb87-4e18-84d3-f6b95b9d3a4e" />


<img width="436" height="452" alt="image" src="https://github.com/user-attachments/assets/d1760e79-cc9c-46bf-87f1-bf9b3f7a3efd" />


<img width="448" height="563" alt="image" src="https://github.com/user-attachments/assets/13b3c5c2-6026-475b-851c-3b4e13ae1b0d" />



<img width="452" height="565" alt="image" src="https://github.com/user-attachments/assets/e69b73a1-ad10-49de-bb1d-10e1df5c450e" />


<img width="572" height="320" alt="image" src="https://github.com/user-attachments/assets/8438f723-1c78-4472-ac1b-726e705f8a0f" />


<img width="712" height="440" alt="image" src="https://github.com/user-attachments/assets/d40ffd20-226f-4b23-a258-28e258b78c8f" />


<img width="568" height="312" alt="image" src="https://github.com/user-attachments/assets/64cc986d-b571-4cec-b70e-25e4ff7594ba" />


<img width="455" height="561" alt="image" src="https://github.com/user-attachments/assets/6df3935f-8c19-4d93-a226-d1a939d72d49" />


<img width="438" height="453" alt="image" src="https://github.com/user-attachments/assets/88ad65e7-15d8-40aa-b360-65da4af4c700" />


<img width="490" height="675" alt="image" src="https://github.com/user-attachments/assets/8cfef676-f60a-4d55-b80f-1b5bbe09a8bb" />


<img width="1015" height="633" alt="image" src="https://github.com/user-attachments/assets/b868d15c-be43-4473-8f39-36c38e74d5c2" />


<img width="642" height="367" alt="image" src="https://github.com/user-attachments/assets/3dec201d-efab-4895-b2d0-4cb5a36a8c6a" />


<img width="1023" height="640" alt="image" src="https://github.com/user-attachments/assets/5809e9ee-7874-481e-b353-1b48d7273764" />


<img width="1216" height="733" alt="image" src="https://github.com/user-attachments/assets/6ea48fba-0545-4bff-bcbe-2bf45caedb52" />


<img width="601" height="311" alt="image" src="https://github.com/user-attachments/assets/7e397ca9-fa37-4757-8ce6-b24547130684" />


<img width="758" height="426" alt="image" src="https://github.com/user-attachments/assets/21976e4e-1322-40b4-9148-45c50fbbefc5" />


<img width="601" height="312" alt="image" src="https://github.com/user-attachments/assets/c19c4afa-2d98-436d-a3c1-94e7c2352c40" />


<img width="1217" height="727" alt="image" src="https://github.com/user-attachments/assets/0743fe85-c17c-4912-8e6d-b03df24ccff1" />


<img width="1025" height="636" alt="image" src="https://github.com/user-attachments/assets/4f5c84fd-8000-4216-b2da-fbbe1fa101f0" />


<img width="1225" height="732" alt="image" src="https://github.com/user-attachments/assets/891fd30e-ca6b-47cd-9345-70ebcc3fa194" />


<img width="611" height="302" alt="image" src="https://github.com/user-attachments/assets/b09d51e4-bc61-419a-b55a-4f17061bd9fd" />


<img width="606" height="308" alt="image" src="https://github.com/user-attachments/assets/2f18db87-0db8-4e06-bfc9-ad2e7dc066d2" />


<img width="1230" height="727" alt="image" src="https://github.com/user-attachments/assets/7ad1d2c8-6ce3-4312-9134-bbb7221589a4" />


<img width="1027" height="641" alt="image" src="https://github.com/user-attachments/assets/b2ba85f7-8c0c-4dfb-9d65-3d792f992ffe" />


<img width="493" height="668" alt="image" src="https://github.com/user-attachments/assets/9f16b611-8647-46f1-9f13-ca0e06fdea9a" />

Now we was finished to add permssion.

---


#### Test on Windows Client
On **Windows Client** now we see our folder that we was create:

<img width="1918" height="767" alt="image" src="https://github.com/user-attachments/assets/990edf07-9027-4aa0-8085-a6624d5f8d06" />

After go to `Options`, in this if we use `Windows 11` click on this:
<img width="1918" height="1033" alt="image" src="https://github.com/user-attachments/assets/34837a73-2d98-4ce7-b4c6-66db25386709" />


And in this I used `Windows 10` for this lab, so do this:

<img width="1918" height="900" alt="image" src="https://github.com/user-attachments/assets/73788cc8-0fe3-4f61-a113-c518c821d79d" />

Or in this we can `Ctrl + F1`.


After it show this:
<img width="380" height="476" alt="image" src="https://github.com/user-attachments/assets/03f9b901-b665-4d44-a84a-1fa6f782f5b6" />


After I create test file about each `Extension`:
````
test.txt
test.pdf
test.docx
test.mp4
test.mp3
````
<img width="1060" height="700" alt="image" src="https://github.com/user-attachments/assets/a90da47a-a5c5-4f4a-b56d-9e911e0ced36" />

Now we ready to create test folder.


---


### Create File Screening
In this go back to our **FSRM** that we was install it:
<img width="985" height="702" alt="image" src="https://github.com/user-attachments/assets/e772d0ee-49e8-42a2-a825-719be2104240" />

And in this we ready to installed it.



##### File Server Manager
Click on `Tools`:
<img width="1918" height="882" alt="image" src="https://github.com/user-attachments/assets/8295e11f-9ecb-4090-be7d-ebbd4ea9c537" />


After we see this:
<img width="1906" height="863" alt="image" src="https://github.com/user-attachments/assets/f5cf5bd4-38eb-47bc-817b-984516239bd1" />


<img width="1915" height="872" alt="image" src="https://github.com/user-attachments/assets/5ff261f4-c02d-4027-925c-87d8e27920ba" />

After in this I browe to folder that I was create and share:
<img width="503" height="578" alt="image" src="https://github.com/user-attachments/assets/aae5e92b-d66d-4b07-9642-db3dbaabb012" />

<img width="921" height="750" alt="image" src="https://github.com/user-attachments/assets/afb09f71-0c5b-4e13-87fd-6e06b25472c4" />


<img width="506" height="583" alt="image" src="https://github.com/user-attachments/assets/26908bfc-ca1e-4098-83c5-c6dff8f8d24d" />


File Screening in Windows Server (FSRM)

| File Screening Type                     | Description                                                                                | Purpose / Usage                                                               |
| --------------------------------------- | ------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------- |
| **Block Audio and Video Files**         | Prevents users from saving media files such as `.mp3`, `.mp4`, `.avi`.                     | Reduces unnecessary storage usage and controls non-business files.            |
| **Block Executable Files**              | Stops users from storing program files such as `.exe`.                                     | Improves security by preventing unauthorized applications or malware storage. |
| **Block Image Files**                   | Restricts saving image files such as `.jpg`, `.png`, `.gif`.                               | Controls storage usage and prevents unwanted file types.                      |
| **Block E-mail Files**                  | Blocks email data files such as `.pst`, `.eml`.                                            | Protects sensitive email data and manages storage.                            |
| **Monitor Executable and System Files** | Allows files but records activity and sends alerts when executable/system files are saved. | Provides monitoring without blocking user activity.                           |


Now we see our block:
<img width="1918" height="863" alt="image" src="https://github.com/user-attachments/assets/2f8f4ba7-baf6-4709-8281-94d3a0a9224a" />


Now we finished to add role block.

---


#### Tes from Windows Client
In this I test to create file that we was block to make sure it correct:
<img width="1918" height="820" alt="image" src="https://github.com/user-attachments/assets/af262c40-8ba9-488c-b6b2-b5d45270df8b" />

Now when I test to create file that end with extension `.mov`, it doesn't have permission.



#### Create MapDrive
<img width="1133" height="721" alt="image" src="https://github.com/user-attachments/assets/30529796-6766-4b0f-9909-c602255d7cf1" />


<img width="613" height="455" alt="image" src="https://github.com/user-attachments/assets/ac2f4545-e362-49ce-b73f-701c51ac1063" />


<img width="1918" height="748" alt="image" src="https://github.com/user-attachments/assets/46a1d6de-f2bc-499c-8ffc-f8bbb6d8076c" />


Now we finished.

---


### Create Quota Management
Back to our **Windows Server** on `File Server Resource Manager` -> click on `Qutota` -> `Right-Click` on `Quotas` -> click on `Create Quota...`:
<img width="1921" height="786" alt="image" src="https://github.com/user-attachments/assets/a65cd7f9-819b-4b8c-991e-cbba0c3b5cb8" />


<img width="500" height="618" alt="image" src="https://github.com/user-attachments/assets/d4830961-b7e5-4e5d-88f8-54d186b8a93a" />


<img width="917" height="750" alt="image" src="https://github.com/user-attachments/assets/108d1bff-5dfe-4887-8812-0b285d55f622" />


In this we can choose what you want:
<img width="508" height="616" alt="image" src="https://github.com/user-attachments/assets/f9dcc3fd-ae21-4e0b-8a88-5024e80fad1c" />


<img width="498" height="612" alt="image" src="https://github.com/user-attachments/assets/13ff4c7f-c41b-4189-bd24-a6671ea98689" />

Now we was ready to set it:
<img width="1918" height="862" alt="image" src="https://github.com/user-attachments/assets/38d71f4e-1e65-41e7-b75a-1ff46ffb3977" />

Now we finished to setup Qutota.

---

After back to our **Windows Client**:
<img width="1918" height="862" alt="image" src="https://github.com/user-attachments/assets/11e0167a-4868-4319-89f8-4243339839b6" />


Now we see capacity of this folder is only `100 MB`.


Now we finished to config Quota.

---
