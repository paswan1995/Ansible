## Ansible continue
* __variable means jo change hoga future me yaha meri soch hai pura directory change ho sakta hai (variables means what can change)__
* __use ctrl+F3 for select same words in vscode__
* __for redhat ` sudo visudo ` in section of same thing without password is ` devops ALL=(ALL) NOPASSWD:ALL `__
* verboose? when you want to print this value
* refer here: https://docs.ansible.com/ansible/latest/cli/ansible-playbook.html
* When we execute ansible playbook on the node where everything is installed, changes shouldn’t happen. But as of now there are changes during every execution done by ansible.
* Context xml with same contents is created as two files and two times the copy is handled in two tasks in last class/notes.
* Ansible playbook which we have written works only for ubuntu, we need to extend this to work for other linux distributions.
* If we need to make this playbook work for future versions of tomcat it will not as we have hardcoded 10.1.18
* If we want extend this playbook to install any version of java
  
## Variables in Ansible

* Ansible uses variables to manage differences between systems. With Ansible, you can execute tasks and playbooks on multiple different systems with a single command.
* To represent the variations among those different systems, you can create variables with standard YAML syntax, including lists and dictionaries. 
* refer here: https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_variables.html#using-variables
* Lets create a simple playbook
```
 ---
 - name: checking variable demo
   vars: 
     name: anil
   hosts: all
   tasks:
     - name: print variable value
       debug: 
         var: name
     - name: print something else
       debug: 
         var: "hello, {{ name }}"
```
 
![preview](images/a106.png)
![preview](images/a107.png)

__classroom notes__
* Lets introduce the variables for tomcat playbook
* 
* refer here: https://github.com/asquarezone/AnsibleZone/commit/1ae8e17dd8c17967e62755ed6357dabb0d99e628
for the changes done to include default variables.
* refer here: https://github.com/asquarezone/AnsibleZone/commit/6a31423515237e97a62cb9081208c2efff954117 
* refer here: https://github.com/asquarezone/AnsibleZone/commit/6a31423515237e97a62cb9081208c2efff954117 for the changes done to fix the variable usage issue.
  
### Lets try to make this playbook work with centos 7

* Problem 1: Package managers might be different
* Ansible has a module called package. refer here: https://docs.ansible.com/ansible/latest/collections/ansible/builtin/package_module.html
* If the package name is same
  
```
  ---
- name: install utilty softwares
  become: yes
  hosts: all
  vars:
    apache_package: httpd
  tasks:
    - name: install git
      ansible.builtin.package:
        name: git
        state: present
```
