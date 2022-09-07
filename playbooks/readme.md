# SSH setup
```bash
$ ssh-keygen -t rsa -b 4096 
$ ssh-copy-id xx@sm
$ ssh-copy-id xx@xm
```

# Operations
To use ansible to to perform multiple operations, such as:
- (normal) ping servers
- (normal) check disk space utilization
- (normal) perfrom operation at specific servers only
- (admin) update/upgrade distribution
- (admin) reboot servers
- (admin) shutdown servers

## Normal Operations ##

### For all servers 
```console
$ ansible-playbook ping.yml
$ ansible-playbook df.yml
```

### For specific servers
```console
$ ansible-playbook ping.yml -l xm,jt
$ ansible-playbook ping.yml -l ubuntu,alma
$ ansible-playbook df.yml -l alma,jt
```


## Admin Operations ##

### Update specific servers (alma: sm, xm)
```console
$ ansible-playbook ping.yml -l alma
$ ansible-playbook k-update-alma.yml -K -l alma
$ ansible-playbook K-update.yml -K -l jt
```

### Update all servers
```console
$ ansible-playbook update-all.yml -K
$ ansible-playbook K-update.yml -K
```

### Reboot specific servers (xm,jt)
```console
$ ansible-playbook K-reboot-all.yml -K -l xm,jt
```

### Setup for shutdown
```console
$ ansible-galaxy collection install community.general
```

### Shutdown specific servers (ubuntu: jt,pf,zf)
```console
$ ansible-playbook K-shutdown.yml -K -l ubuntu
```


### Others
```console
$ ansible xm -m ansible.builtin.setup
```

### Check the hosts configuration
```console
$ cat hosts
[all:vars]
ansible_user=xx
ansible_port=22
ansible_become_method=sudo
ansible_python_interpreter=/usr/bin/python3

[vm]
#xx ansible_host=192.168.233.254
jt ansible_host=192.168.233.81
xm anisble_host=192.168.233.82
sm ansible_host=192.168.233.83
pf ansible_host=192.168.233.84
zf anisble_host=192.168.233.85

[ubuntu]
jt ansible_host=192.168.233.81
pf ansible_host=192.168.233.84
zf anisble_host=192.168.233.85

[alma]
sm ansible_host=192.168.233.83
xm anisble_host=192.168.233.82
```
