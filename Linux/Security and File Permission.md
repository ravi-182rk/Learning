# Security and File Permissions

## Linux Accounts

> ### Linux Security:
Security in linux is a very vast topic and involvs many topics.  
<img width="1302" height="572" alt="image" src="https://github.com/user-attachments/assets/284b190f-0f5b-4bcd-b9f0-6514ed903eea" /></br>
- **Access Control Methods**: Uses user and password based authentication, to decide who can access the system.
- **PAM**: **Pluggable Authentication Model** another way to mange authentication. Normally used to authenticate user for programs and services in linux.
- **Network Security**: To restrict or allow access to services listening on the server. Normally we rely on external firewalls. It can also be setup in system using tools like IPTables and Firewalld.
- **SSH Hardneing**: **Secure Shell** used for remote access. SSH Hardening makes sure only authorized user have access to system.
- **SELinux**: Uses security policies for isolating applications running on the same system from each other. 

> ### User Accounts:
Every user in linux associates with an account. User account maintains <username, passwordm, UID> to login into the system.  
UID - UserID which is unique to each user.  
User account information stored in **`/etc/passwd`** file  
<img width="1405" height="773" alt="image" src="https://github.com/user-attachments/assets/caa9beec-1a6d-4e4e-9fef-620195d550ca" /></br>

> ### Groups:
Group is a collection of user. Used to organize users based on common attributes such as role or a function.  
Group information stored in **`/etc/group`** file.  
Each group has unique identifier which is GID (Group ID)  
Suppose we have two developers bob and michael, who has similar role, we can group them in a "Developer" gorup. So we can provide similar access for them to files and folders in the system.  
<img width="507" height="85" alt="image" src="https://github.com/user-attachments/assets/0df0f986-23e9-4b37-860f-d0f813e88ce8" /></br>

> ### User Account Details:
Every user account contains details like
- **Username**
- **UID (UserID)**, uniquer to each user
- **ID (GroupID)**, group they are part of. User can be part of multiple groups. If no group is specified while creating user, it assign a group with same ID and name as of userID. That wil be primary GID of user.
- **Home Directory**. Ex: `/home/<user_name>`
- **Default shell**. With which user can log in and use. Ex: `/bin/sh`.
 
We can get these details by below command
```
id <username>
```
<img width="922" height="96" alt="image" src="https://github.com/user-attachments/assets/c6c9d926-f495-4adb-978f-05cfb05bb020" />

To check Home directory path and default shell:
```
grep -i <username> /etc/passwd
```
<img width="898" height="76" alt="image" src="https://github.com/user-attachments/assets/ea8183a6-23c5-4f1f-bd17-e83d11e03fd9" />

> ### Account Types

1. **User account**:
   - Belongs to single user
   - **Ex**: Ram, Krishna, Arjun.
2. **Super User Account**:
   - It is **root** account, with UID = 0.
   - It has unrestricted access and control over the system.
   - We can elimante the need ever loggin in as a root user, by assigning `nologin` shell to root user.
   - <img width="522" height="96" alt="image" src="https://github.com/user-attachments/assets/6b5f2346-5f52-4232-a801-931539c2c8fb" />  

3. **System Accounts**:
   - Created during the OS installation, for use by software and services that will not run by super user.
   - UID range: <100, or 500 to 1000.
   - No dedicated home directory. Even if they do, they won't be created under `/home`.
   - **Ex**: SSHD, mail user account.
4. **Service Accounts**:
   - Created when services are installed in linux.
   - For **example**, an **nginx service** makes use of a service account called **nginx**.
     <img width="1102" height="513" alt="image" src="https://github.com/user-attachments/assets/a680aae3-f25d-4b2a-b1e7-700cc0e744e7" />

> ### COMMANDS
- To see the information about user. This command give information like UID, GID.
  ```
  id
  ```
- To list of the users cuurently logged into the system.
  ```
  who
  ```
- To get record of all loggedin users. also shows date and tie when system is rebooted.
  ```
  last
  ```
  <img width="1133" height="387" alt="image" src="https://github.com/user-attachments/assets/e2fa554d-7be7-4821-ad70-daa670582139" />

> ### Switching Users
To swith to any user type command ` su - ` and enter password.
```
su -
```
This can also be used as
```
su -c "whoami"
```
This command requires password of the user you are switching to.
Intead we can use SUDO.
#### SUDO
Sudo makes us use the previlege of root user. So we can intall and run commands with previlege access.  
ex:  
```
sudo apt-get install nginix
```
- We need sudo password for that usser.
- The default configuration is defined under `/etc/sudoers` file.  
- File defines policies applied by `sudo` command.  
- File can be changed by using  
```
visudo
```
- Only users mentioned in the `/etc/sudoers` file can make use of `sudo` command for previleged access.
- Admins can manage which user can do what.
- Example below you can see, **bob** has complete admin previleges, but **sara** can only reboot the system.
- <img width="1421" height="713" alt="image" src="https://github.com/user-attachments/assets/9657d75d-6bb1-455e-978f-f6d33403f560" />
  






