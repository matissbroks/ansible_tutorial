# ansible_tutorial

Commands used in episodes

---

### EP: 04

- `ansible all --key-file ~/.ssh/<KEY_FILE_NAME> -i inventory -m ping`

- After creating `ansible.cfg` we can shorten previous command. `ansible all -m ping`

- To show all hosts: `ansible all --list-hosts`

- To get facts from servers `ansible all -m gather_facts`
    - To limit only single host add `--limit <HOST_IP_ADDRES>`
