# Ansible cheat-sheet

### Test server
Gather ansible-facts to show which server is online
```bash
$ ansible linux -m ping
```

### Run command on servers
```bash
$ ansible linux -a "cat /etc/os-release"
```

### Using a playbook
```bash
$ ansible-playbook df.yml
```
