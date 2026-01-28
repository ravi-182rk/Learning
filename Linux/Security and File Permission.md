# Security and File Permissions

## Linux Accounts

### Linux Security:
Security in linux is a very vast topic and involvs many topics.  
<img width="1302" height="572" alt="image" src="https://github.com/user-attachments/assets/284b190f-0f5b-4bcd-b9f0-6514ed903eea" /></br>
- **Access Control Methods**: Uses user and password based authentication, to decide who can access the system.
- **PAM**: **Pluggable Authentication Model** another way to mange authentication. Normally used to authenticate user for programs and services in linux.
- **Network Security**: To restrict or allow access to services listening on the server. Normally we rely on external firewalls. It can also be setup in system using tools like IPTables and Firewalld.
- **SSH Hardneing**: **Secure Shell** used for remote access. SSH Hardening makes sure only authorized user have access to system.
- **SELinux**: Uses security policies for isolating applications running on the same system from each other. 

### User Accounts:
Every user in linux associates with an account. User account maintains <username, passwordm, UID> to login into the system.  
UID - UserID which is unique to each user.  
User account information stored in **`/etc/passwd`** file  
<img width="1405" height="773" alt="image" src="https://github.com/user-attachments/assets/caa9beec-1a6d-4e4e-9fef-620195d550ca" /></br>

### Groups:
Group is a collection of user. Used to organize users based on common attributes such as role or a function.  
Group information stored in **`/etc/group`** file.  
Each group has unique identifier which is GID (Group ID)  
Suppose we have two developers bob and michael, who has similar role, we can group them in a "Developer" gorup. So we can provide similar access for them to files and folders in the system.  
<img width="507" height="85" alt="image" src="https://github.com/user-attachments/assets/0df0f986-23e9-4b37-860f-d0f813e88ce8" /></br>

