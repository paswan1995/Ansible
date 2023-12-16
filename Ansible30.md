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
* ![preview](images/a42.png) `id_rsa` is a private file and  `id_rsa.pub` is public file.
* If both machine in the same network so prefer private ip.
*  ## ssh-copy-id :-  
                    ``ssh-copy-id`` installs an SSH key on a server as an authorized key. Its purpose is to provide access without requiring a password for each login. This facilitates automated, passwordless logins and single sign-on using the SSH protocol
* __So once you copy the key the advantage of this is we no longer need password__.
* ![preview](images/a43.png)
* ![preview](images/a44.png)
* Its not going to ask you to enter password now. We are not using username here (ssh 172-31-38-192) because both username is same that's why we are using private ip here.
* ![preview](images/a45.png) 
* Username is matching. I have given the private ip address and when i give that ip address it will automatically take id_rsa as a default key file. For that id_rsa there should be a matching public key,  That matching public key we have a already copied by using ssh-copy-id for that reason its working. 
* 