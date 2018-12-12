# Script for checking box resources

## Check the connectivity for every box that is added into [env]_hosts file

ansible all -m ping -k -K

### Output example: 

```ie1-abc01-qa.qa.betfair | SUCCESS => {
    "changed": false,
    "ping": "pong"
}```

## Checks CPU resources

ansible-playbook -i prd_hosts playbook/res.yml --tags "cpu" -e"target=native/i2" -kKs

### Output example:

```
PLAY [VM Resource Checker] ****************************************************

TASK: [Check CPU Threads] *****************************************************
changed: [prdebs001.prd.betfair]

TASK: [Number of CPUs] ********************************************************
ok: [prdebs001.prd.betfair] => {
    "msg": "Total CPUs: 6"
}
```

## Checks RAM resources

ansible-playbook -i prd_hosts playbook/res.yml --tags "ram" -e"target=native/i2" -kKs

## Checks DISK capacity - NATIVE

ansible-playbook -i prd_hosts playbook/res.yml --tags "disk_native" -e"target=native/i2" -kKs

## Checks DISK capacity - i2

ansible-playbook -i prd_hosts playbook/res.yml --tags "disk_i2" -e"target=native/i2" -kKs
