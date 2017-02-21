# piji
Generate Ansible files with... Ansible!

Dependenices:
Ansible (v2.0+)

Usage:
create `project.yml` and populate it with following values:

```
project:
    project_name: web-project
    owner: me
    managed_by: me


requirements:
    ansible-galaxy.role1:
        custom_var: something
        custom_var2: else
    ansible-galaxy.role1:
        feature: yes

inventory:
    vagrant:
        fqdn: web-app.local
        requires:
            ansible-galaxy.role1:
                another_var: customvar
                another_var2: customvar2
        groups:
            - webserver
            - ubuntu
            - database

    staging:
        fqdn: web-app.aws
        groups:
            - webserver
            - database
            - bigdata
            - something
        requires:
            ansible-galaxy.role1:
                some_var: testing
                some_var: testing
```

save and from the same directory run:
ansible-playbook generate.yml

