<p align="center">
<img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>On-premises Active Directory File shares & Permissions (Azure)</h1>
This tutorial outlines the implementation of on-premises Active Directory within Azure Virtual Machines.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Active Directory Domain Services
- PowerShell

<h2>Operating Systems Used </h2>

- Windows Server 2022
- Windows 10 (21H2)

<h2>High-Level Deployment and Configuration Steps</h2>

- Step 1
- Step 2
- Step 3
- Step 4

<h2>Create sample file shares with various permissions</h2>

![image](https://github.com/user-attachments/assets/5101dd03-e611-4a50-b343-43650de01986)
![image](https://github.com/user-attachments/assets/adc8a7ea-4bb1-4bea-9e21-40d227dd77a5)
![image](https://github.com/user-attachments/assets/8ea809b6-2552-4725-b82f-2e2b157fc51e)




<p>
First we go to the DC-1 vm and create some folders that will be named "read-access", "write-access", "no-access", "accounting". Now we'll go to each of these folders and right click them for properties then go to share and share to domain users for the read access and write access folders and give them the permissions that correspond with their names. For no access we will give only domain admins read and write priviledges. Now go to our normal user and try to access each share folder we created to make sure the permissions worked correctly.  
</p>
<br />

<h2>Try to open file as a normal user</h2>

![image](https://github.com/user-attachments/assets/4ad410f9-fcad-4293-8b33-8eab3dcead1a)



<p>
We can see that on our user we can read files in the read folder but we cant create or modify folders. In the write folder we can read, create, and modify files. Lastly, in the no access folder we can't even open this folder at all as the regular user as only domain admins have permissions to do so.
</p>
<br />

<h2>Make a new Accountants Security Group and assign permissions, then test access</h2>

![image](https://github.com/user-attachments/assets/a2df596c-42ce-4069-87d3-71c125530c06)
![image](https://github.com/user-attachments/assets/d816a075-45c9-4285-b20b-1718e8115565)
![image](https://github.com/user-attachments/assets/bdbf2391-acb6-4914-ac37-e1e94b35c338)
![image](https://github.com/user-attachments/assets/084da307-a4eb-48cc-b098-f83212e4c333)
![image](https://github.com/user-attachments/assets/0e9eaa7f-9b75-4e2c-8603-e4b1ba13b029)


<p>
First we make an OU for accountants to match our folder in the network file share. Next, we'll go to the folder again in file explorer and give accountants read/write permissions. Going back to our regular user we cant access the accounting folder which is to be expected. The last step here is to make our user a member of the accountants security group in Active Directory so they can now access the folder in the file share, thus completing our lab.
</p>
<br />
