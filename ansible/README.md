# Notes on ansible

Ansible is a deployment tool usually used by devops. It can be used to perform tasks on remote machines from a central controller. 

* Ansible needs to be installed on the controller machine
* It can be executed in both adhoc manner and by using a playbook (set of instructions)
* It needs a dir structure of `./hosts ./roles/tasks/main.yml`
* The hosts file consists of a lit of host files reachable via ssh (ssh is the primary means of communication for ansible)
* Tasks can be performed selectively using roles. A role is a collection of tasks for a specific purpose. Ex: Java8 can be a role that installs java 8 on remote machines, install_basic_packages can be a role that can install basic apt packages and so on..
* Example of using it in adhoc manner: `ansible -m shell -a 'df -h' all`
* This above command logs into each machine listed in hosts file and executes `df -h` command. The results are gathered back at the controller
* Tasks can also be performed in a more non-adhoc way using playbooks
* A playbook is a collection of roles to be executed on a set of nodes
* Example: `ansible-playbook setup-nodes.yml all`
* This executes all the roles mentioned in setup-nodes.yml
* Surf through the repo for more sensible examples
