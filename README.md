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

<h2>Dealing with account lockouts</h2>

![image](https://github.com/user-attachments/assets/b3465b78-a95a-4261-a737-809145f8a206)
![image](https://github.com/user-attachments/assets/095c1469-5a46-4373-8a3a-f6d0fe49c1d6)
![image](https://github.com/user-attachments/assets/69836024-9636-4444-843d-3fd50fa99e95)
![image](https://github.com/user-attachments/assets/51a26439-a526-4825-b1ed-77e2cc8b0ef0)
![image](https://github.com/user-attachments/assets/91cdd5db-ae2c-4380-838a-3cfce471cb83)
![image](https://github.com/user-attachments/assets/5f4923fd-4405-4bd3-9e2f-90783f55f4e2)
![image](https://github.com/user-attachments/assets/f60a7efd-2b39-41f8-900b-034d5238de7e)


<p>
The first we must complete for the account lockouts to function is open the Group Policy Management Console(GPMC) to create a policy that locks users out of their accounts after a certain amount of failed login attempts. Open the Group policy managment editor and go to computer config > policies > windows settings > security settings > account lockout policy then configure account lockout settings. It will recommend you settings depending on the lockout duration you pick but keep in mind you can still change it. Once this is changed, you COULD wait until the policy changes on its own but we're going to login to jane admin and run a command that forces a group policy update to save time(gpupdate /force). Running gpresult /r as an admin will show those group policy update results and when the group policy was last updated. After trying to log into the user we last used and failing the password attempts you should be locked out of your account. Active directory should show that this user has been locked out of their account, simply check the unlock account field and you should be able to login as that user again with the correct password. To reset password simple right click that user and go to reset password and choose which options apply for the situation. 
</p>
<br />

<h2>Enabling and Disabling Accounts</h2>

![image](https://github.com/user-attachments/assets/e8828a35-b5fd-4e78-9b6e-007ce8068f3e)
![image](https://github.com/user-attachments/assets/2e06197e-2a0a-48a5-93a6-086330107c1a)


<p>
To lock and unlock an account you use the same process as resetting, HOWEVER keep in mind this user may have been locked out for a legitimate reason and for this reason make sure you are checking with your leadership/management to verify if they are allowed to have their account unlocked or not.
</p>
<br />

<h2>Log Observation</h2>

![image](https://github.com/user-attachments/assets/51412f4d-e551-4fd6-a0fd-4b8e1b820f6a)

<p>
To open the logs we'll go back to dc-1 vm and simply type event viewer into the start window and open it. From here we just go to Windows Logs > Security then from here you can view the logs and even press control+f to find the specific user we used and look at any logs showing events that pertain to that specific user.
</p>
<br />
