## Installing Ansible
* Ansible can be installed in two ways
          * Package Managers
          * Python:https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installing-and-upgrading-ansible
## Python based installation
* `python3 --version`
  `pip3 --version`
  `python3 -m pip install --user ansible`
## Ansible deals with credentials
* Possible Credentials
       * Username and Password
       * Username and key
* Ansible when executing playbook logins to the node using credentials provided and takes help of the python installed on the node to get the job done.
* Login into the node
       * SSH: This is used for linux and mac
       * Winrm: This is used for windows
* ## Username and Password Authentication
* ## Overview
![preview](images/a19.png)
![preview](images/a20.png)

* Linux machines allow us to login using ssh protocol and configurations of ssh are present in 
## to know the how many users are present in the machine `cat /etc/passwd`
 
  
   ![preview](images/a23.png)
* The field __PasswordAuthentication__ should be __yes__.
 ``sudo vi /etc/ssh/sshd_config`
* Change __PasswordAuthentication__ to __yes__
  ``sudo systemctl restart sshd`` 
  ![preview](images/a21.png)
  ![preview](images/a22.png)  
  ![preview](images/a23.png)
  ![preview](images/a24.png)
  !
* Create a user called as jenkins 

* For creating user we have 2 commands and that is given below
<1>
   `` sudo useradd <username>`` 
* To set user password or change `sudo passwd <username>` aftr this you can set the password.
* sudo adduser <username> 
 this will directly ask you to set password.
<2>
 ``sudo adduser jenkins``
 `su jenkins` su= switch-user and jenkins= username 
* to delete user we use  `sudo userdel <username>` 


* Lets make jenkins administrator
* `sudo visudo`
* Lets ask not to prompt for password for jenkins user
* Do the same stuff for node 2 
