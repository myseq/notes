# SSH setup
`bash
$ ssh-copy-id xx@sm
$ ssh-copy-id xx@xm
`

# Update Alma Linux
$ ansible-playbook ping.yml -l alma
$ ansible-playbook k-update-alma.yml -K -l alma

# Setup for shutdown
$ ansible-galaxy collection install community.general

# Shutdown servers
$ ansible-playbook K-shutdown.yml -K -l ubuntu



# Others
ansible-playbook ping.yml
ansible-playbook df.yml
ansible-playbook update-all.yml -K
ansible-playbook ping.yml -l xm,jt

$ ansible xm -m ansible.builtin.setup

$ ansible-playbook K-update.yml -K
$ ansible-playbook K-update.yml -K -l jt

$ ansible-playbook K-reboot-all.yml -K -l xm,jt

$ ansible-playbook ping.yml -l ubuntu,alma
