# foremansible
A sensible Ansible playbook to deploy Foreman (theforeman.org)


# Preparation
- Clone the repository with the command below:
~~~
$ git clone https://github.com/capyroto/foremansible.git
$ cd foremansible
~~~
To be able to run this task, make sure to add your SSH pubkey as root user.
Note that is expected a pre-existing ssh key pairs to be automatically copied to the server.

Create an inventory file with the contents below:
~~~
$ cd ansible
$ vim inventory
[foreman_servers]
192.168.0.1
~~~

Note: On Debian systems, by default the root user is not allowed to connect remotely.
~~~
$ echo "PermitRootLogin yes" >> /etc/ssh/sshd_config
$ /etc/init.d/ssh restart
~~~

Then execute the pre-requisites:
~~~
$ ssh-copy-id -i ~/.ssh/id_rsa.pub root@<SERVER>
$ ansible-playbook -u root --tags="prereq_as_root" main.yml
~~~
