## Ansible Setup with Key Based Authentication between ACN and Node
* Overview
* Create two linux vm’s
* ![preview](images/a35.png)
* Create a user on both vms with password
* ![preview](images/a36.png)
* ![preview](images/a37.png)
* ![preview](images/a38.png)
* Ensure the user has sudo permissions
* ![preview](images/a40.png)
* Now create an ssh key pair on Ansible control node
* ![preview](images/a41.png)
* Copy the public key from Ansible control node to node 
* ![preview](images/a34.png)
* 