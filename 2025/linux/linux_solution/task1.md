# This file explains the solution for task1 for linux challenge

## Task:
1. Create a user `devops_user` and add them to a group `devops_team`.
2. Set a password and grant 'sudo' access.
3. Restrict SSH login for certain users in `/etc/ssh/sshd_config`.

---

### creating a user `devops_user` and adding them to a group `devops_team`

to create the new user named `devops_user` use the following command

```bash

sudo useradd -m devops_user

```
You will be promted to add a password. You can add the password or keep it blank as well. Press `Enter` to keep it blank.

- `-m`: creates the user's home directory

Adding a new user will always add a new group associated with the new group

### Adding the user to the group `devops_team`

To add the new user to the group `devops_team`, use the following command 

```bash

Sudo usermod -aG devops_team devops_user

```

### Verifying the user and group

TO verify the user details and group the following commands needs to be run

``` bash

id devops_user

```
 
The output will show:

``` bash

uid=1001(devops_user) gid=1002(Devops_team) groups=1002(Devops_team),27(sudo),100(users),1000(ubuntu),1003(sharedgroup)

```

Here, the user `devops_user` has been added to the group `Devops_team` and `ubuntu`

## set a password and grant sudo acess

If you have not set a password for the user while creating it or if you wish to change it, you can use the following command

```bash
sudo gpasswd devops_user
```

This will prompt to enter the password and confirm it

## Providing the sudo access to the user `devops_user`

```bash
sudo usermod -aG sudo devops_user
```

## Providing sudo access to all the members of the group

```bash
sudo visudo
```
add the follwing line to add the sudo access to all the members of the group `devops_team`

```bash
%devops_team ALL=(ALL:ALL) ALL
```

---

### Restricting SSH access

To restrict SSH access to specific users (e.g., `devops_user`), add the following line to the file:

```bash
AllowUsers devops_user
```

This ensures that only `devops_user` can log in via SSH. If you want to allow multiple users, separate them with a space:

```bash
AllowUsers devops_user user2 user3
```

After making changes, restart the SSH service to apply the new configuration:

```bash
sudo systemctl restart sshd
```

#### Find the Server's or local IP Address

To connect to the SSH server, you need its IP address. Use the following command to find it:

```bash
ip a
```

Look for the inet address under your network interface (e.g., eth0 or wlp2s0). For example:

```bash
inet 172.168.1.100/24
```

#### Authenticate using SSH

On another machine (or the same machine if you're testing locally), use the ssh command to connect:

```bash
ssh devops_user@172.168.1.100
```

- Replace 172.168.1.100 with the IP address of your SSH server (or local device).

You will be prompted to enter the password for ssh_user. Enter the password you set previously.
Example Output:

```bash
devops_user@172.168.1.100's password:
Welcome to Ubuntu 22.04 LTS (GNU/Linux 5.15.0-83-generic x86_64)
...

devops_user@hostname:~$
```
