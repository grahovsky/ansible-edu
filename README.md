# ansible-edu


# ad-hoc commands
ansible lin -m shell -a "df -h"

ansible lin -m copy -a "src=hosts dest=~/ansible_tmp/hosts_ansible"
ansible lin -m copy -a "src=hosts dest=~/ansible_tmp/hosts_ansible" -b # -b - with sudo privileges

ansible lin -m file -a "path=~/ansible_tmp/hosts_ansible state=absent"

ansible lin -m get_url -a "url=https://www.python.org/ftp/python/3.8.3/python-3.8.3.exe dest=~/ansible_tmp"

ansible lin -m yum -a "name=stress state=latest" -b # install package
ansible lin -m yum -a "name=httpd state=latest" -b # install package

ansible lin -m uri -a "url=http://www.adv-it.net return_content=yes"

ansible lin -m service -a "name=httpd state=started enabled=yes" -b # start servers
ansible lin -m yum -a "name=httpd state=removed" -b #


ansible lin -m shell -a "df -h" -vvvv # verbose v, vv, vvv, vvvv

ansible-doc -l | grep win


# Roles
ansible-galaxy init deploy_apache_web

https://docs.ansible.com/ansible/latest/user_guide/playbooks_reuse_roles.html


# extra vars

ansible-playbook playbooks/playbook11.yml --extra-vars "myhosts=lin"
ansible-playbook playbooks/playbook11.yml --extra-vars "myhosts=lin owner=MAX" 

extra-vars - overriding vars


# ansible-vault

- ansible-vault create secrets.txt
- ansible-vault edit secret.txt
- ansible-vault decrypt secrets.txt
- ansible-vault encrypt secrets.txt

- ansible-vault encrypt playbooks/secrets_vars.yml

- ansible-vault encrypt_string
- ansible-vault encrypt_string --stdin-name "superpass222"

- ansible-playbook playbooks/playbook15_vault.yml --vault-password-file mypass.txt


