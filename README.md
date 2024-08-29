### Переменная определена в файле inventory.yaml
```shell
user@ansibletask4-fjkap:~/task$ ansible-playbook -i inventory.yaml lab_import.yaml

PLAY [Import lab] *******************************************************************************************************************************************************************************************

TASK [Gathering Facts] **************************************************************************************************************************************************************************************
ok: [web01]

TASK [Rename] ***********************************************************************************************************************************************************************************************
changed: [web01]

TASK [include_tasks] ****************************************************************************************************************************************************************************************
skipping: [web01]

PLAY RECAP **************************************************************************************************************************************************************************************************
web01                      : ok=2    changed=1    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0   

user@ansibletask4-fjkap:~/task$ ansible all -m shell -a "hostname" -i inventory.yaml 
web01 | CHANGED | rc=0 >>
test

```

### Переменная не определена, но задана через --extra-vars
```shell
ansible-playbook -i inventory.yaml lab_import.yaml --extra-vars "custom_name=server"

PLAY [Import lab] *******************************************************************************************************************************************************************************************

TASK [Gathering Facts] **************************************************************************************************************************************************************************************
ok: [web01]

TASK [Rename] ***********************************************************************************************************************************************************************************************
changed: [web01]

TASK [include_tasks] ****************************************************************************************************************************************************************************************
skipping: [web01]

PLAY RECAP **************************************************************************************************************************************************************************************************
web01                      : ok=2    changed=1    unreachable=0    failed=0    skipped=1    rescued=0    ignored=0   

user@ansibletask4-fjkap:~/task$ ansible all -m shell -a "hostname" -i inventory.yaml 
web01 | CHANGED | rc=0 >>
server

```
