---
title: "Tasks Nov 2021"
date: 2019-02-11T19:27:37+10:00
weight: 3
summary: Commands of the 2nd round.
---

**Get current user**

```
$ whoami
```

**Get info user**

```console
$ id username
uid=1000(ubuntu) gid=1000(ubuntu) groups=1000(ubuntu),4(adm),20(dialout),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),33(www-data),44(video),46(plugdev),109(netdev),110(lxd)
```

**Get all groups**

```
$ groups
```

**Get user's gruoups**

```
$ groups username
```

**Categories:**

- Nurses on Board - Finance for Board Service
- Surgent IQ Courses
- Self Paced Business Courses
- For Personal and Corporate (course_id > 0)
- For Academic

**Create tar bz2 file**

```
$ tar -cvjf filename.tar.bz2 /local/source_directory
```

**Extract tar file**

```
$ tar -xvjf filename.tar.bz2 --skip-old-files
# example
$ tar -xvjf filename.tar.bz2 /local/source_directory
```

**Send file from local to remote**

```
$ scp -v -P 22 -i /local/keyfile filename.tar.bz2 user@IP_ADDRESS:/remote/directory
# example
$ scp -v -P 22 -i ~/.ssh/key.pem amedocs_build.tar.bz2 ubuntu@52.60.233.18:/ebs/amedocs/
```

**Send file from remote to local**

```
$ scp -v -P 22 -i /local/keyfile user@IP_ADDRESS:/remote/filename /local/directory
# example
$ scp -v -P 22 -i ~/.ssh/key.pem ubuntu@52.60.233.18:/ebs/amedocs/amedocs_build.tar.bz2 /
```

**SSH Permission denied (publickey)**

It seems you didn't add public key of your computer to your server.
Public keys from client computers are stored in _authorized_keys_ file.

1. Change this line in `/etc/ssh/sshd_config` to **yes** (later you can turn it back again)
   ```INI
   PasswordAuthentication yes
   ```
2. Restart ssh

```
   $ sudo service ssh restart
```

3. Then issue the following command from your client computer to export public key to the server:

```Bash
   $ ssh-copy-id usersrv@server
   # example:
   $ ssh-copy-id -i helberth-key ubuntu@52.60.233.18
   # In the command prompt enter your password. After that you will gain access to your server via ssh-keys.
```
