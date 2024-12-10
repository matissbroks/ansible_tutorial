# ansible_tutorial

Commands used in episodes

---

### EP: 04

- `ansible all --key-file ~/.ssh/<KEY_FILE_NAME> -i inventory -m ping`

- After creating `ansible.cfg` we can shorten previous command. `ansible all -m ping`

- To show all hosts: `ansible all --list-hosts`

- To get facts from servers `ansible all -m gather_facts`
    - To limit only single host add `--limit <HOST_IP_ADDRES>`

---

### EP: 05

- Updating repository index. This will fail, because not run as root user and not used `sudo`
    - `ansible all -m apt -a update_cache=true`

- To run it as `sudo` we use this `ansible all -m apt -a update_cache=true --become --ask-become-pass`
    - This will ask `sudo` password

- Installing package to all hosts at once `ansible all -m apt -a name=vim-nox --become --ask-become-pass`

- Installing package to all hosts at once `ansible all -m apt -a name=tmux --become --ask-become-pass`
    - In video it was already installed, so there was no changes made

- In any of host servers went to log dir `cd /var/log` if there is `apt` folder then `cd apt`
    - And to see `apt` history `cat history.log` will show commands that were run before

- Will update one of package `snapd`, for example, on all hosts. For more than 1 argument need double quotes
    - `ansible all -m apt -a "name=snapd state=latest" --become --ask-become-pass`

- This will upgrade all packages on all host servers: `ansible all -m apt -a "upgrade=dist" --become --ask-become-pass`
---

### EP: 06

- To run playbook who install apache2 and PHP `ansible-playbook --ask-become-pass install_apache.yml`

- To do oposite `ansible-playbook --ask-become-pass remove_apache.yml`

---

### EP: 07

- If have host with no `apt` module this would fail `ansible-playbook --ask-become-pass install_apache.yml`

- After editing playbook, and adding `when` statement

- Get specific data from all server data `ansible all -m gather_facts --limit <HOST_IP_ADDRES> | grep ansible_distribution`

- On CentOS machie started httpd service and opened port 80
    - Starting service `sudo systemctl start httpd`
    - Openeing port 80 `sudo firewall-cmd --add-port=80/tcp`