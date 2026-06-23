<h1 align="center"> How to configure Simple Spanned Striped Mirrored RAID Volume </h1>

<img width="1536" height="700" alt="image" src="https://github.com/user-attachments/assets/e72bc6c5-c0af-48ac-adb7-b6edba2e3a0e" />

---


## Introsdution to Simple Spanned Striped Mirrored RAID Volume

### What is Spanned Striped Mirrored RAID Volume
A **Spanned Striped Mirrored RAID Volume** isn’t a single RAID type, it’s a mix of three different Windows dynamic volume concepts (Spanned, Striped, and Mirrored). Each has distinct purposes: spanned for capacity, striped for speed, and mirrored for redundancy. They cannot all be combined directly into one volume, but understanding each helps you choose the right RAID setup.

Core Concepts
- Spanned Volume
  - Combines free space from multiple disks into one large logical volume.
  - Pros: Easy way to expand storage.
  - Cons: No fault tolerance — if one disk fails, all data is lost.
- Striped Volume (RAID 0)
  - Splits data into blocks and writes across multiple disks simultaneously.
  - Pros: High performance (faster read/write).
  - Cons: No redundancy — one disk failure destroys the entire volume.
- Mirrored Volume (RAID 1)
  - Duplicates data across two disks.
  - Pros: Strong fault tolerance — if one disk fails, the other keeps data safe.
  - Cons: Storage efficiency is only 50% (half of total capacity is usable).

---


### Check Hardisk 

On **Windows Server**:
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/39b27e7b-66c4-456c-a2df-3acb3dc73827" />

`Right-Click` on our Windows server also in this I `Right-Click` on `DC01-AD` -> click `Settings`:
<img width="1918" height="1078" alt="image" src="https://github.com/user-attachments/assets/d51ee806-c0b7-4f86-a190-5305167103fc" />

Now I see my **Windows Server** have **Hardisk** only also it have only **Drive C**:
<img width="892" height="897" alt="image" src="https://github.com/user-attachments/assets/78641f42-b36a-4ac0-9179-8269d9ecdf0b" />


After go to view on **Windows Server**:
<img width="1918" height="888" alt="image" src="https://github.com/user-attachments/assets/f33a21d6-6d99-4573-aa22-804045f1b2ce" />

Now I see only one `Drive`.

---

### Manage Hardisk
Open **Server Manager** -> `Tools` -> `Coputer Management`:
<img width="1918" height="882" alt="image" src="https://github.com/user-attachments/assets/d69e6da8-0013-4bc7-b44b-0e37f8847e3f" />

<img width="1912" height="883" alt="image" src="https://github.com/user-attachments/assets/aa3258f9-5fb8-46bb-8dca-b5129111d10d" />



**Disk 0 (59.98 GB, Basic, Online)**: This is your main hard drive/SSD. It’s split into several partitions:

- EFI System Partition (100 MB)
   - Used by the system to boot Windows.
   - Marked Healthy (EFI System Partition).
- C: Drive (59.37 GB, NTFS)
   - Our main partition where Windows, programs, and files are stored.
   - Labeled Healthy (Boot, Page File, Crash Dump, Basic Data Partition).
   - About 39.87 GB free (67%).
- Recovery Partition (524 MB)
   - Hidden partition used for system recovery tools.
   - Marked Healthy (Recovery Partition).

**CD-ROM 0 (D: Drive, 4.70 GB)**:

- This is our DVD drive.
- It currently has a disc inserted: SSS_X64FREE_EN-US_DV9.
- Shows Healthy (Primary Partition) but has 0 MB free (the disc is full).


> **Note**: In our drive C is a basic disk.

---


### Add Hardisk:

#### Add Hardisk 1
On **Windows Server**:

`Right-Click` on `DC01-AD`:
<img width="1912" height="1055" alt="image" src="https://github.com/user-attachments/assets/eb62691b-7896-494c-9c4a-194fd4f13c52" />


<img width="887" height="901" alt="image" src="https://github.com/user-attachments/assets/af942790-52b1-49ce-bdf7-b90d84058361" />

<img width="516" height="532" alt="image" src="https://github.com/user-attachments/assets/bba62e83-1fab-4063-938b-a34c2793a9e2" />


<img width="515" height="527" alt="image" src="https://github.com/user-attachments/assets/53cd9e1f-e93d-480d-9c64-b36eaed4a603" />


| Disk Controller        | Description                                                                                | Hot-Add Support                                     | Performance | Usage                                                        |
| ---------------------- | ------------------------------------------------------------------------------------------ | --------------------------------------------------- | ----------- | -----------------------------------------------------------  |
| **IDE**                | Older disk interface standard. Slower and mainly kept for compatibility.                   | ❌ No (VM usually must be powered off before adding) | Low         | Rarely used today; mainly for old operating systems         |
| **SCSI (Recommended)** | Modern virtual disk controller. Flexible and widely supported by virtualization platforms. | ✅ Yes (supports adding disks while VM is running)   | Good        | Best general choice for most VMs                            |
| **SATA**               | Common interface used in physical computers. Simple and compatible.                        | Usually ❌ No / limited                              | Medium      | Works well for normal desktop VMs                           |
| **NVMe**               | Newer high-speed storage standard designed for SSD performance.                            | ❌ Usually requires VM power off                     | Very High   | Best for high-performance workloads if guest OS supports it |


<img width="522" height="535" alt="image" src="https://github.com/user-attachments/assets/6b6a0d54-bca5-4272-8cc2-4e9d96f03a64" />


In this I choose on:
````
5.0 GB
````
Cause it for test:
<img width="523" height="532" alt="image" src="https://github.com/user-attachments/assets/dac79136-1719-4ae7-ab0e-fbde8bd87e07" />

| Storage Option                             | Description                                           | Pros                                                                                              | Cons                                                                                                     |
| ------------------------------------------ | ----------------------------------------------------- | ------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Store virtual disk as a single file**    | Creates the entire virtual disk as **one large file** | Faster performance<br>Less file management<br> Simpler structure                             |  Harder to move between computers if the file is very large<br> Copying requires moving the whole file |
| **Split virtual disk into multiple files** | Breaks the virtual disk into **smaller file chunks**  | Easier to copy/move the VM<br> Better for portable VMs<br> Avoids some large file size limits |  Slight performance reduction with very large disks<br> More files to manage                           |


<img width="515" height="532" alt="image" src="https://github.com/user-attachments/assets/28c17948-35ed-4930-a958-0b394037238a" />


After it will go to our drive:
<img width="1157" height="826" alt="image" src="https://github.com/user-attachments/assets/8b60f18b-5a46-43f0-bc0e-b0220f42ec3a" />

And in this I input it in my Document folder:
<img width="1163" height="833" alt="image" src="https://github.com/user-attachments/assets/ac287f40-88a3-4c18-9ab4-1abf17d139ce" />

> **Note**: In this we can input it any where that we want.


After I rename it to:
````
Disk1
````
<img width="1162" height="833" alt="image" src="https://github.com/user-attachments/assets/b15d83ca-f052-40c0-83b1-76ce4d264141" />


<img width="518" height="531" alt="image" src="https://github.com/user-attachments/assets/8baf95aa-8a59-44ab-9291-65942d412cbf" />


Now we see one more **Hardisk**:
<img width="888" height="902" alt="image" src="https://github.com/user-attachments/assets/250787ce-cfc1-4a58-917b-3b875e63cb90" />


#### Add Hardisk 2
Do it like what we do in add `Hardisk 1`:

<img width="890" height="897" alt="image" src="https://github.com/user-attachments/assets/a68dd36e-e820-41ea-acf4-4cb99286bc73" />


<img width="513" height="526" alt="image" src="https://github.com/user-attachments/assets/7c7cc089-31f9-4a97-88a5-9c68d40e0cdb" />


<img width="505" height="521" alt="image" src="https://github.com/user-attachments/assets/dceae47d-f6a0-4599-926d-82365169d526" />


<img width="518" height="528" alt="image" src="https://github.com/user-attachments/assets/223cf1fb-bf1b-4c81-8547-02b83a89aea7" />


<img width="521" height="527" alt="image" src="https://github.com/user-attachments/assets/85354227-78dd-40cd-ac01-8cbe4884bfca" />



<img width="522" height="532" alt="image" src="https://github.com/user-attachments/assets/929268d5-9efc-4b48-b271-44e07b784336" />


<img width="1157" height="826" alt="image" src="https://github.com/user-attachments/assets/3540d4f6-2f01-445a-a18e-256f0c4252d5" />

<img width="513" height="527" alt="image" src="https://github.com/user-attachments/assets/f2c96abe-bdc6-41e5-9ca3-31e84d3db8cb" />


Now we see right now we have 3 hardisk:
<img width="891" height="906" alt="image" src="https://github.com/user-attachments/assets/13549a43-7316-4362-a7df-46be5d9770eb" />


After click `Ok`:
<img width="887" height="902" alt="image" src="https://github.com/user-attachments/assets/f13af42b-67df-42d0-9500-34924eb5ab56" />

<img width="893" height="896" alt="image" src="https://github.com/user-attachments/assets/d32415ed-a676-4196-800e-fd5507a7f86f" />


<img width="886" height="894" alt="image" src="https://github.com/user-attachments/assets/aa68edda-0cda-4c7f-a54f-b7f7e2499f6f" />



After back to our **Windows Server**:
<img width="1919" height="890" alt="image" src="https://github.com/user-attachments/assets/fae61f87-13cf-4bcd-af56-23abf4c04863" />

Now we see we have 3 Hardisk.


Right now we can't use this Hardisk, cause we not yet `Online` it:
<img width="1918" height="877" alt="image" src="https://github.com/user-attachments/assets/d0b2745f-931a-4254-8f12-37d0a52d76e7" />


After `Right-Click` on those Disk -> Choose `Online`:
<img width="1918" height="881" alt="image" src="https://github.com/user-attachments/assets/62667eed-d094-4e30-82f4-88f64ca82dd9" />


After `Online` all.

`Right-Click` o Hardisk:
<img width="1918" height="878" alt="image" src="https://github.com/user-attachments/assets/7fc89ddc-5fdf-4b2b-90e5-07c0d5dfeab2" />


Now we see this:
<img width="1919" height="860" alt="image" src="https://github.com/user-attachments/assets/7f188cfe-6236-45df-bd84-3758c5973bab" />


#### After take this Disk to use:

`Right-Click` on disk -> `Initialize Disk`:

<img width="1917" height="882" alt="image" src="https://github.com/user-attachments/assets/736e7d13-a5cd-46b8-8997-d4e38c5fe5d4" />


<img width="500" height="387" alt="image" src="https://github.com/user-attachments/assets/79cfed7a-089d-4a33-a9f7-aae231701d54" />


Now we see this:
<img width="1919" height="882" alt="image" src="https://github.com/user-attachments/assets/01163a6c-bac9-40e9-961e-6862a55b31d6" />

---


#### Simple Disk

After `Righ-Click` on it `New Simple Volume...`:
<img width="1918" height="878" alt="image" src="https://github.com/user-attachments/assets/5c559d9e-185f-4e6c-bc2c-af8479d0b6d5" />


<img width="622" height="492" alt="image" src="https://github.com/user-attachments/assets/55d7c527-2919-4583-9949-e4ffdc6b60c9" />


<img width="626" height="493" alt="image" src="https://github.com/user-attachments/assets/962bf78e-7b46-4e2b-8d01-1b2bd5a0c018" />

<img width="625" height="487" alt="image" src="https://github.com/user-attachments/assets/6771c131-7e60-4504-94d8-ae2ee4cd7e68" />


<img width="617" height="492" alt="image" src="https://github.com/user-attachments/assets/248f1f58-56bf-480a-b0aa-8f0b4d6ec746" />


| File System                           | Description                                          | Advantages                                                                  | Limitations                                                                |
| ------------------------------------- | ---------------------------------------------------- | --------------------------------------------------------------------------- | -------------------------------------------------------------------------- |
| **NTFS (New Technology File System)** | Modern Windows file system                           | Supports large files, file permissions, encryption, compression, journaling | Less compatible with older devices and some non-Windows systems            |
| **FAT32 (File Allocation Table 32)**  | Older file system with wide compatibility            | Works on Windows, macOS, Linux, game consoles, USB devices                  | Maximum file size is **4 GB**, smaller partition limits                    |
| **ReFS (Resilient File System)**      | Newer Microsoft file system designed for reliability | High data integrity, automatic error detection, supports very large storage | Limited compatibility, mainly used in Windows Server and some Pro editions |


<img width="625" height="505" alt="image" src="https://github.com/user-attachments/assets/c765df3f-71ad-4bbf-a502-0e011955cfa6" />


Now we can use this drive:
<img width="1916" height="870" alt="image" src="https://github.com/user-attachments/assets/10b36523-a7c7-4052-8731-5b26e5716674" />


Check it in file, Go to `File Explorer`:
<img width="1918" height="942" alt="image" src="https://github.com/user-attachments/assets/69e3c3a1-c70c-42e0-871d-b35b5f212ecf" />


Now we see it, then I create one file:
````
simple.txt
````
<img width="1919" height="886" alt="image" src="https://github.com/user-attachments/assets/6365ad22-051a-4138-894e-4c5306c259cb" />

<img width="992" height="832" alt="image" src="https://github.com/user-attachments/assets/ab3e3cd9-3c5b-4de6-95fd-5fa4d9d895d2" />



if in this we want to know this broken or not.

Just `Right-Click` on drive -> choose `Ofline`:
<img width="1915" height="881" alt="image" src="https://github.com/user-attachments/assets/1cb2a617-7fb2-4aee-9c2d-e28495e027cc" />


<img width="1918" height="877" alt="image" src="https://github.com/user-attachments/assets/a1d173f6-1c7f-4aa9-a2c1-2fdc30df23b2" />


After go back to our ``file explorer``:
<img width="1421" height="790" alt="image" src="https://github.com/user-attachments/assets/869f8f10-1a0e-449a-907a-5ce6074726c4" />

Now we don't we our `Drive E`.


After I oline it again:
<img width="1918" height="877" alt="image" src="https://github.com/user-attachments/assets/8800d329-8325-4873-987f-1b697a57cfcf" />

NNow we see `Drive E` back:
<img width="1416" height="773" alt="image" src="https://github.com/user-attachments/assets/7466759d-7d48-4dd2-83d6-34d73c1c3cb1" />

Also with our file:
<img width="1430" height="801" alt="image" src="https://github.com/user-attachments/assets/14988859-29c6-42e3-bfdf-626205111752" />


---




#### Spanned Hardisk

In this first I test to delete `Disk1`:
<img width="1918" height="885" alt="image" src="https://github.com/user-attachments/assets/2dbe28fa-23f5-4e8f-b929-b1035369dea8" />


<img width="513" height="212" alt="image" src="https://github.com/user-attachments/assets/3f670cc8-d921-4c15-85d2-2f24e4343b71" />


<img width="1918" height="880" alt="image" src="https://github.com/user-attachments/assets/e8ff373d-17f8-4560-93e8-d1190aa97a4b" />



After `Right-Click` -> click `New Spanned Volume...`: 
<img width="1918" height="886" alt="image" src="https://github.com/user-attachments/assets/c9ba4da1-6300-4e7f-80d9-9d4c816a61f8" />


| Option                           | Meaning                                                       | Use Case                                                |
| -------------------------------- | ------------------------------------------------------------- | ------------------------------------------------------- |
| **New Simple Volume**            | Creates a normal single partition/volume                      | Most common choice (like creating a D: drive)           |
| **New Spanned Volume**           | Combines free space from multiple disks into one large volume | Example: Disk 1 (100GB) + Disk 2 (100GB) = 200GB volume |
| **New Striped Volume (RAID 0)**  | Splits data across multiple disks for higher speed            | Performance improvement, no fault tolerance             |
| **New Mirrored Volume (RAID 1)** | Copies data to another disk                                   | Data protection; if one disk fails, data remains        |
| **New RAID-5 Volume**            | Uses multiple disks with parity for fault tolerance           | Balance of speed, storage, and recovery (Server use)    |



<img width="621" height="511" alt="image" src="https://github.com/user-attachments/assets/7a6660f1-8e67-49fb-b2be-d282e6f8657e" />


In this I add one Idsk:
<img width="623" height="508" alt="image" src="https://github.com/user-attachments/assets/349bef4b-5a35-4a4d-9409-da126dd4166e" />


In this it mean like if one our **Hardisk** is broken we have one more **Gardisk**.

<img width="622" height="507" alt="image" src="https://github.com/user-attachments/assets/08ca59aa-69a4-4fc8-87d3-8316aaa81dc1" />


<img width="620" height="503" alt="image" src="https://github.com/user-attachments/assets/f7236f5f-5149-4e3a-8fd4-da6102f2ba40" />


<img width="623" height="512" alt="image" src="https://github.com/user-attachments/assets/b4323d60-06e4-4674-b1a0-a6a6faf9f09a" />

<img width="622" height="507" alt="image" src="https://github.com/user-attachments/assets/96a8b071-20cc-4e21-aa44-84d6bd04961d" />


<img width="508" height="262" alt="image" src="https://github.com/user-attachments/assets/ca01ad8e-cba6-4d5a-a5c2-8e3d33f1272f" />

After it show this:
<img width="1916" height="857" alt="image" src="https://github.com/user-attachments/assets/5d1efecb-0ab4-40e8-b2e9-c5c00c585757" />


After check on our file, go to `File Exporer`:
<img width="1431" height="797" alt="image" src="https://github.com/user-attachments/assets/078bcb0b-4f7b-4648-b012-a34f3df056d0" />


Now we see also we see it have `10GB`.

After I test to create one file:
<img width="1427" height="795" alt="image" src="https://github.com/user-attachments/assets/78ec753c-f301-413f-abc2-2caa4f74fc42" />


##### Test if has one Hardisk is Broken:
After `Right-Click` -> `Ofline`
<img width="1918" height="886" alt="image" src="https://github.com/user-attachments/assets/41b82648-1268-4318-b0a1-d5619b1dfb4e" />

<img width="1919" height="875" alt="image" src="https://github.com/user-attachments/assets/854e3e93-dfbd-4268-8191-bf1572cbf9c5" />

Now our Drive is broken:
<img width="1918" height="858" alt="image" src="https://github.com/user-attachments/assets/7d0c3954-82b6-4d25-b322-12f3b4fc794e" />


---



#### New Sripped

Kew different between Speened and Sripped:
| Feature                | **Spanned Volume**                                           | **Striped Volume (RAID 0)**                                      |
| ---------------------- | ------------------------------------------------------------ | ---------------------------------------------------------------- |
| **Purpose**            | Combine multiple disks into one large volume                 | Increase speed by spreading data across disks                    |
| **How data is stored** | Fills one disk first, then continues to the next disk        | Splits data into blocks and writes to all disks at the same time |
| **Performance**        | Normal speed                                                 | Faster read/write speed                                          |
| **Example (2 disks)**  | Disk A: 100GB + Disk B: 100GB → 200GB volume (A fills first) | Disk A + Disk B work together → faster 200GB volume              |
| **Data safety**        | No protection                                                | No protection                                                    |
| **If one disk fails**  | Entire volume may become unavailable                         | Entire volume fails and data is lost                             |
| **Minimum disks**      | 2 or more                                                    | 2 or more                                                        |
| **Storage efficiency** | 100% usable space                                            | 100% usable space                                                |
| **Best for**           | Combining unused disk space                                  | Gaming, video editing, high-speed temporary storage              |
| **Example**            | HDD 1 (500GB) + HDD 500GB = 1TB                              | SSD 1 + SSD 2 = faster SSD array                                 |


In this first I delete volume:
<img width="1918" height="887" alt="image" src="https://github.com/user-attachments/assets/ae5f7165-0b4a-49c7-a5f7-10f7593b7a53" />

<img width="513" height="211" alt="image" src="https://github.com/user-attachments/assets/0d981645-9245-4e45-90a9-90976a5d1ca4" />

After we will see this:
<img width="1919" height="847" alt="image" src="https://github.com/user-attachments/assets/47d4f9d0-24a6-4558-ab0e-7c03cded867a" />

`Right-Click` -> Click on `Sripped`:

<img width="1918" height="878" alt="image" src="https://github.com/user-attachments/assets/15b770a1-c160-4efa-93eb-7a5c4c739a34" />


<img width="618" height="512" alt="image" src="https://github.com/user-attachments/assets/59d2b7c7-d9f3-4986-98ec-f8b242539f30" />

<img width="627" height="517" alt="image" src="https://github.com/user-attachments/assets/1fac4a14-6f64-4991-9e40-f895861128fb" />


<img width="622" height="512" alt="image" src="https://github.com/user-attachments/assets/eab44c7f-de89-4317-b655-ad535c01ee55" />

<img width="622" height="506" alt="image" src="https://github.com/user-attachments/assets/5b3c29b9-d688-4323-ad2e-65ee7b6dfe91" />

<img width="618" height="507" alt="image" src="https://github.com/user-attachments/assets/ff6742b3-7ce0-40cb-9bf7-271350928556" />

<img width="623" height="511" alt="image" src="https://github.com/user-attachments/assets/ba37dbd0-4e93-4e0b-9138-10cd3fe5c9ce" />


<img width="508" height="258" alt="image" src="https://github.com/user-attachments/assets/6ec4a675-7b82-4ef2-ab11-1c41092729fe" />

Now we see this:
<img width="1919" height="880" alt="image" src="https://github.com/user-attachments/assets/ee3e73cc-a0e9-451f-8045-7429fde04330" />


After check it in `File Expoer`:
<img width="1427" height="787" alt="image" src="https://github.com/user-attachments/assets/1e664a61-d06f-4c73-96b2-1b945909a5e5" />

Now we see drive E.


After I test to create file:
<img width="1428" height="805" alt="image" src="https://github.com/user-attachments/assets/40fd846a-b098-4231-8324-effc63956aa5" />



Afte back to our computer management, I `Ofline` it:
<img width="1918" height="883" alt="image" src="https://github.com/user-attachments/assets/ea5c43b1-2a9a-4586-83c5-c13ea22674ee" />

<img width="1918" height="857" alt="image" src="https://github.com/user-attachments/assets/f5308404-268e-4a0d-92cf-3489bd9ca109" />

So in this if drive has broken one data will broken all.

---




#### New Mirrored Volume

| Feature                       | **Spanned Volume**                  | **Striped Volume (RAID 0)**             | **Mirrored Volume (RAID 1)**             |
| ----------------------------- | ----------------------------------- | --------------------------------------- | ---------------------------------------- |
| **Purpose**                   | Combine disks into one large volume | Increase speed                          | Protect data                             |
| **How data is stored**        | Data fills Disk 1, then Disk 2      | Data is split across disks              | Same data is copied to both disks        |
| **Performance**               | Normal speed                        | Fast read/write                         | Read can be faster, write similar/slower |
| **Example (2 × 500GB disks)** | 500GB + 500GB = 1TB                 | 500GB + 500GB = 1TB                     | 500GB + 500GB = 500GB usable             |
| **Data safety**               | ❌ No protection                     | ❌ No protection                         | ✅ Protection (duplicate copy)            |
| **If one disk fails**         | Volume may fail                     | Volume fails                            | Data still available                     |
| **Minimum disks**             | 2                                   | 2                                       | 2                                        |
| **Usable capacity**           | 100%                                | 100%                                    | 50%                                      |
| **Best for**                  | Extra storage space                 | Speed (games, editing, temporary files) | Important files, reliability             |
| **Example**                   | Disk A → full, then Disk B          | File parts split: A+B work together     | Disk A = Disk B (same files)             |


Also in this first I need to `Delete Volume`:
<img width="1918" height="871" alt="image" src="https://github.com/user-attachments/assets/47812af7-7a36-4af9-81bd-43d0ad7b65d5" />


<img width="512" height="213" alt="image" src="https://github.com/user-attachments/assets/352ffd56-4415-4f4b-9e81-9b1f93a8353c" />


<img width="1918" height="875" alt="image" src="https://github.com/user-attachments/assets/6863533a-4daa-49c9-8b6d-7dbd6f568639" />


<img width="622" height="507" alt="image" src="https://github.com/user-attachments/assets/43ee5863-99ad-4c7f-9865-c31e1db2e77d" />


<img width="625" height="506" alt="image" src="https://github.com/user-attachments/assets/1228794f-2dc1-42ab-8070-ec9a3072975c" />


Now in this we see only:
````
5.00GB
````
<img width="625" height="511" alt="image" src="https://github.com/user-attachments/assets/7281c38d-e867-45bd-ab57-ee4a80e78305" />


<img width="621" height="506" alt="image" src="https://github.com/user-attachments/assets/0865127e-225e-493d-bfba-b08bfee938b6" />

<img width="622" height="507" alt="image" src="https://github.com/user-attachments/assets/e62c9a41-27a8-4016-a377-19ca85b57260" />


<img width="610" height="501" alt="image" src="https://github.com/user-attachments/assets/152a6a82-1af5-44db-b0eb-0cc3125efcab" />

<img width="517" height="261" alt="image" src="https://github.com/user-attachments/assets/19e1c79b-39e4-4925-88a1-a0035007cb10" />


Now we see this:
<img width="1917" height="870" alt="image" src="https://github.com/user-attachments/assets/b3e5eef5-d0cf-4491-b4e9-185dc22c3de8" />


After check on `File Explorer`:
<img width="1918" height="865" alt="image" src="https://github.com/user-attachments/assets/1ecfc8ba-399b-4daa-83a8-0569b65112c6" />

Now we see this file.


After I want to create one file:
````
Mirroed
````
<img width="1142" height="829" alt="image" src="https://github.com/user-attachments/assets/3e33332f-b105-4419-92ef-f16ec95ff8c1" />




After I test to `Ofline` one drive in this, cause I mean I want like if one drive has broken we have one drive still work.


<img width="1917" height="877" alt="image" src="https://github.com/user-attachments/assets/d5bda8b3-406d-4b25-aba7-d431ca7fd83c" />


Now we see in this it just show `Warning Fumolar`:
<img width="1918" height="858" alt="image" src="https://github.com/user-attachments/assets/027f9bc3-0cfa-4982-82cf-965a7efdc0fe" />


After go to this drive to make sure we see our file or not:
<img width="1096" height="822" alt="image" src="https://github.com/user-attachments/assets/e07aebff-c928-45ef-af66-3b139c2f855b" />

Now we still see our file.


---



#### RAID 5

In this I need to `delete Volume`:
<img width="1919" height="869" alt="image" src="https://github.com/user-attachments/assets/a5e4575f-59a6-4af2-bbdf-e9b312ff6e3d" />

Now I was delete it all.


Also **RAID 5** we need Hardisk over 3, and in this I add one more Harddisk:
<img width="1918" height="1053" alt="image" src="https://github.com/user-attachments/assets/6720bf09-0292-4984-a687-aaa68a8e6702" />

<img width="882" height="900" alt="image" src="https://github.com/user-attachments/assets/836f62b8-7d72-4981-8ff3-3c3675b02df0" />

<img width="510" height="526" alt="image" src="https://github.com/user-attachments/assets/69b0bceb-e14b-48a6-a868-14ba5be35478" />

<img width="513" height="527" alt="image" src="https://github.com/user-attachments/assets/905a5257-f189-4ba1-b00d-a8762db504b5" />

<img width="516" height="512" alt="image" src="https://github.com/user-attachments/assets/8c578efc-1bdc-4acd-a22a-b2196426c828" />


<img width="517" height="528" alt="image" src="https://github.com/user-attachments/assets/a0c16c6c-2bf9-4122-8b34-fb95ec9b3b79" />

<img width="508" height="522" alt="image" src="https://github.com/user-attachments/assets/d011c869-5543-4ccb-9fe0-0a2e60df9f67" />


<img width="1158" height="827" alt="image" src="https://github.com/user-attachments/assets/fcfe3add-0f84-40c9-a51e-82681cd28a62" />


<img width="520" height="532" alt="image" src="https://github.com/user-attachments/assets/f080127e-2820-4b30-81a9-f20ec0faaab0" />


<img width="880" height="903" alt="image" src="https://github.com/user-attachments/assets/fa66d436-2912-4d09-a98a-f4ff79b513db" />


Now it was add ot our drive:
<img width="1918" height="887" alt="image" src="https://github.com/user-attachments/assets/411c4634-ccb4-4058-9aa7-b1354ebb03ef" />


After `Online` it:
<img width="1918" height="886" alt="image" src="https://github.com/user-attachments/assets/3125c55a-b515-4279-ac41-ae8fc70b91ab" />


<img width="1908" height="886" alt="image" src="https://github.com/user-attachments/assets/117e236a-06cd-4828-9046-5ad17c74acad" />


<img width="502" height="387" alt="image" src="https://github.com/user-attachments/assets/c8480bc1-0e06-4e44-934a-7f7de42c929b" />

Now all our drive we can user all:
<img width="1917" height="883" alt="image" src="https://github.com/user-attachments/assets/b1e7143d-51b4-4db6-bc8b-f3d0611e12fc" />


If our file show this, just `Right-Click`:
<img width="1918" height="852" alt="image" src="https://github.com/user-attachments/assets/0fa54f91-6e28-4e83-84e2-9c92be6fd11b" />

<img width="1918" height="862" alt="image" src="https://github.com/user-attachments/assets/1563dbd9-8c83-4677-ba67-65e0b2924f1e" />

<img width="582" height="301" alt="image" src="https://github.com/user-attachments/assets/cd15d5e3-497f-4f31-8d3a-6e06747fd5f9" />

<img width="560" height="323" alt="image" src="https://github.com/user-attachments/assets/d5835d2f-4ba4-4056-bcda-b0ebdec71907" />

After Delete Volume:
<img width="1918" height="867" alt="image" src="https://github.com/user-attachments/assets/5853b568-9687-494e-a480-805d45b378eb" />

<img width="517" height="216" alt="image" src="https://github.com/user-attachments/assets/d10459e5-4bdb-4b81-8934-58989ae8e6e1" />

<img width="1918" height="856" alt="image" src="https://github.com/user-attachments/assets/8081a760-ac36-4ce2-82e5-0111fdc324c8" />


##### Use RAID 5 

| Feature                       | **RAID 5 (Striping with Parity)**                                                           |
| ----------------------------- | ------------------------------------------------------------------------------------------- |
| **Purpose**                   | Balance performance, storage efficiency, and data protection                                |
| **How data is stored**        | Data is striped across 3 or more disks + parity information is distributed across all disks |
| **Performance**               | Good read speed, moderate write speed (due to parity calculation)                           |
| **Example (3 × 500GB disks)** | Total usable space = 1000GB (2 disks worth, 1 disk used for parity)                         |
| **Data safety**               | Fault tolerant (can survive 1 disk failure)                                               |
| **If one disk fails**         | System keeps working using parity data                                                      |
| **Minimum disks**             | 3                                                                                           |
| **Usable capacity**           | (N - 1) × disk size                                                                         |
| **Best for**                  | File servers, backups, business storage systems                                             |
| **Example**                   | 3 disks → 1 disk parity, data still safe if 1 disk dies                                     |



Just `Right-Click`:
<img width="1915" height="877" alt="image" src="https://github.com/user-attachments/assets/bb1451bd-fc01-4c3d-b703-65f86e22e927" />

<img width="622" height="512" alt="image" src="https://github.com/user-attachments/assets/86e908b0-59b2-43e8-b0ff-d58f24cd7898" />

<img width="623" height="516" alt="image" src="https://github.com/user-attachments/assets/d9dc9961-a33e-41f2-9631-0b1e32250602" />

<img width="618" height="505" alt="image" src="https://github.com/user-attachments/assets/ff5bd98e-bf59-45fc-aba4-65844dbf8ee9" />


<img width="620" height="508" alt="image" src="https://github.com/user-attachments/assets/f25dc6e3-afed-4010-b7de-c7052050165b" />


<img width="622" height="507" alt="image" src="https://github.com/user-attachments/assets/951445b4-7ab3-4dde-8560-8846f9c64365" />


<img width="618" height="507" alt="image" src="https://github.com/user-attachments/assets/d489bb89-f67b-4eac-9ae4-36c6bafcc3ea" />

<img width="622" height="506" alt="image" src="https://github.com/user-attachments/assets/3651c249-f539-4014-87ad-3d1d99f7f804" />

<img width="515" height="260" alt="image" src="https://github.com/user-attachments/assets/91bcf108-06dd-413e-9e13-da500f59ff5b" />

Now we see this:
<img width="1917" height="881" alt="image" src="https://github.com/user-attachments/assets/f4a23962-50d8-4aa2-a9da-bda4dfd4f5d6" />


Afte I check on `File Explorer`:
<img width="1918" height="866" alt="image" src="https://github.com/user-attachments/assets/296ada28-3579-456b-b2ab-edfd5616e179" />


After I test to crete one file:
<img width="1077" height="829" alt="image" src="https://github.com/user-attachments/assets/808c2e08-93f9-496c-8d24-db493165e846" />


After I test to `Ofline` it to similar like if have one drive is `Broken` we have one.
<img width="1918" height="872" alt="image" src="https://github.com/user-attachments/assets/c99bd586-ae10-48d3-9436-7c61de01d742" />


Now it just show `Warning`:
<img width="1917" height="858" alt="image" src="https://github.com/user-attachments/assets/f6ccc5ba-49fd-455a-b0c3-19a45616a941" />

After back to our `File Explore`:
<img width="1919" height="867" alt="image" src="https://github.com/user-attachments/assets/5ba0abcd-c5e9-4a50-98c5-bc4231215619" />

Now we still see our drive E.

Afte I want to test to make one Hardisk is Broken:
<img width="1918" height="876" alt="image" src="https://github.com/user-attachments/assets/d2d800ef-fb15-4167-886e-d8696b24a08c" />

Now our data has been broken all:
<img width="1918" height="874" alt="image" src="https://github.com/user-attachments/assets/c46c2737-fabd-46c5-bd53-4b70280750a7" />

In **RAID 5** if it broken 1 hardisk we need to find more hardisk to prepare to make it not broken all.



After `Online` all of it:

<img width="1918" height="866" alt="image" src="https://github.com/user-attachments/assets/cd4d42b4-7206-4517-9554-dcc9fac28587" />

If it show this:
<img width="1913" height="883" alt="image" src="https://github.com/user-attachments/assets/1f07ecbe-0f03-45d2-af86-418bfeb8eaf4" />


<img width="1913" height="877" alt="image" src="https://github.com/user-attachments/assets/05f4b991-4da4-42d5-b2dc-58219e38665b" />


Now it back to normal all:
<img width="1919" height="871" alt="image" src="https://github.com/user-attachments/assets/48473e93-45fd-4ad2-8464-42d8a39bd0d2" />


Now we got successfull to complete this lab.

---
