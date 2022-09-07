# SSH setup
```bash
$ ssh-keygen -t rsa -b 4096 
$ ssh-copy-id xx@sm
$ ssh-copy-id xx@xm
```

# Update Alma Linux
```console
$ ansible-playbook ping.yml -l alma
$ ansible-playbook k-update-alma.yml -K -l alma
```

# Setup for shutdown
```console
$ ansible-galaxy collection install community.general
```

### Shutdown servers
```console
$ ansible-playbook K-shutdown.yml -K -l ubuntu
```


## Others
```console
$ ansible-playbook ping.yml
$ ansible-playbook df.yml
$ ansible-playbook update-all.yml -K
$ ansible-playbook ping.yml -l xm,jt
```

```console
$ ansible xm -m ansible.builtin.setup

$ ansible-playbook K-update.yml -K
$ ansible-playbook K-update.yml -K -l jt

$ ansible-playbook K-reboot-all.yml -K -l xm,jt

$ ansible-playbook ping.yml -l ubuntu,alma
```
