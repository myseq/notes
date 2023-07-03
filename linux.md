# Notes for Linux sysadm

Some notes on linux administration.

## Password Reset
1. Reboot to GRUB menu.
2. At GRUB menu:
   - press `e` tp edit the commands
   - edit the clause of the 2nd last line from `ro quiet splash $vt_handoff` to `rw init=/bin/sh`
   - press `F10` or ctrl-x to save the edits and boot
3. Confirm the read and write access rights with `moutn | grep -w /`
4. Reset the password for root with `passwd`
5. Reboot the server with `exec /sbin/init`

## Initd Vs Systemd

| Comments | SysVinit | Systemd |
|:-------- | :------: | :-----: |
| system halt | `0` | runlevel0.target, `poweroff.target` |
| single-user mode | `1` | runlevel1.target, `rescue.target` |
| multi-user |	`2`	| runlevel2.target, `multi-user.target` |
| multi-user with Network |	`3`	| runlevel3.target, `multi-user.target` |
| experimental |	`4`	 | runlevel4.target, `multi-user.target` |
| multi-user, with network, graphical mode |	`5` | runlevel5.target, `graphical.target` |
| reboot	| `6` |	runlevel6.target, `reboot.target` |
| emergency shell |	emergency |	`emergency.target` |

### Systemd cmdline

Check the boot time.
```console
$ systemd-analyze time
Startup finished in 47.497s (userspace)
graphical.target reached after 47.434s in userspace
```
Execute a systemd cmd on remote host
```console
$ systemctl status nginx  -H user@host
```

Manage `ufw` service with `systemctl`:
```console
$ systemctl status ufw
$ systemctl show ufw
$ systemctl show -p UMask ufw
$ systemctl stop ufw
$ systemctl start ufw
$ systemctl restart ufw
$ systemctl reload ufw
$ systemctl disable ufw
$ systemctl enable ufw
$ systemctl is-enabled ufw
$ systemctl is-active ufw
$ systemctl is-failed ufw
```

List current units and all units:
```console
$ systemctl list-units
$ systemctl list-units --all
$ systemctl list-units --all --state=inactive
$ systemctl list-units --type=service
$ systemctl list-unit-files
```

Display a unit file:
```console
$ systemctl cat atd.service
```

Check dependencies
```console
$ systemctl list-dependencies sshd.service
$ systemctl show sshd.service -p Conflicts
```

Masking and Unmasking Units
```console
$ sudo systemctl mask nginx.service
$ sudo systemctl unmask nginx.service
```

System state (runlevel) with target
```console
$ systemctl get-default
$ sudo systemctl set-default graphical.target
$ systemctl list-units --type=target
$ systemctl list-units --type=service
$ systemctl list-dependencies multi-user.target
$ sudo systemctl isolate multi-user.target
$ sudo systemctl rescue
$ sudo systemctl halt
$ sudo systemctl poweroff
$ sudo systemctl reboot
```

## Rescue Mode Vs Emergency Mode

Rescue mode is equivalent to single user mode and requires the root password. Rescue mode allows: 
 - to repair your system. 
 - to mount all local file systems and start some important system services.
 - but not activate network interfaces.

Emergency mode provides the most minimal environment possible and allows:
 - to repair system even in situations when fail entering rescue mode. 
 - mounts the root file system as read-only
 - but does not mount any other local file systems
 - but not activate network interfaces.

```grub2
systemd.unit=emergency.target
```

```grub2
systemd.unit=rescue.target
```

```grub2
systemd.debug-shell
```

```console
# systemctl --no-wall emergency
# systemctl isolate emergency.target
```

```console
# systemctl --no-wall rescue
# systemctl isolate rescue.target 
```

