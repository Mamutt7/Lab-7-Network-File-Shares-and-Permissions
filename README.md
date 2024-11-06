# Lab-7-Network-File-Shares-and-Permissions
In this home lab, I will create different network file shares and give certain permissions to a random user created in previous labs.



Create some sample file shares with various permissions
1.	Connect/log into DC-1 as your domain admin account (mydomain.com\jane_admin)
2.	Connect/log into Client-1 as a normal user (mydomain\<someuser>)
3.	On DC-1, on the C:\ drive, create 4 folders: “read-access”, “write-access”, “no-access”, “accounting” 

 ![image](https://github.com/user-attachments/assets/d9531b1c-9d69-4e52-9f41-a5528532213e)


4.	Set the following permissions (share the folder)
a.	Folder: “read-access”, Group: “Domain Users”, Permission: “Read”
b.	Folder: “write-access”,  Group: “Domain Users”, Permissions: “Read/Write”
c.	Folder: “no-access”, Group: “Domain Admins”, “Permissions: “Read/Write”
d.	(Skip accounting for now)

 ![image](https://github.com/user-attachments/assets/970aaaea-5d3f-45c1-a5a4-9beace95f48c)


Attempt to access file shares as a normal user
5.	On Client-1, navigate to the shared folder (start, run, \\dc-1)
6.	Try to access the folders you just created. Which folders can you access? Which folders can you create stuff in? Does it make sense?

![image](https://github.com/user-attachments/assets/89a1ebd8-8da3-42c8-b67b-5c7de4854c2f)
 

Logged in as a user (kax.mib) I can access both the read-access and write-access because I allowed it from the dc-1 VM as an admin (jane_admin). I can only create/save/write files in the write-access and not the read-access due to permissions.


Create an “ACCOUNTANTS” Security Group, assign permissions, an test access
7.	Go back to DC-1, in Active Directory, create a security group called “ACCOUNTANTS”

![image](https://github.com/user-attachments/assets/00ae3dfc-1614-4dd5-87c8-ef98d933a170)
 

8.	On the “accounting” folder you created earlier, set the following permissions:
a.	Folder: “accounting”, Group: “ACCOUNTANTS”, Permissions: “Read/Write”

![image](https://github.com/user-attachments/assets/80aabe8d-c4a8-4a3d-8163-f05a215970a2)
 

9.	On Client-1, as  <someuser>, try to access the accountants folder. It should fail. 

![image](https://github.com/user-attachments/assets/5dd2347c-3df5-4557-a107-cfde13cccb98) 

10.	Log out of Client-1 as  <someuser>
11.	On DC-1, make <someuser> a member of the “ACCOUNTANTS”  Security Group

![image](https://github.com/user-attachments/assets/6c2eb1da-def7-4814-89f3-9f33e45fac5b)
 

12.	Sign back into Client-1 as <someuser> and try to access the “accounting” share in \\DC-1

 ![image](https://github.com/user-attachments/assets/802f17f4-8d0b-4ef5-8a2e-a43e05d4c20b)

