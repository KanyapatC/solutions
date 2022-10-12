# How to setup SFTP without password

You can sftp to server both (Linux to Linux or Linux to Windows) by ** windows must install Openssh https://github.com/PowerShell/Win32-OpenSSH/releases
And Linux install OpenSSH

```
yum –y install openssh-server openssh-clients
```

Start / Stop service sshd

```
systemctl start sshd
systemctl stop sshd
```

# Genarent as Key Pair

Execute the following commands at Localhost
```
user@localhost~$> ssh-keygen -t rsa 
```

Press ENTER for all options prompted. No values need to be typed.
```
user@localhost~$> cd .ssh
user@localhost~$> cp -p id_rsa.pub authorized_keys
user@localhost~$> sftp user@remoteserver
Password:
```

Execute the following commands at Remote Hosts.
```
user@remotehost~$> mkdir .ssh
user@remotehost~$> chmod 700 .ssh
user@remotehost~$> cd .ssh
user@remotehost~$> put authorized_keys
user@remotehost~$> chmod 600 authorized_keys
user@remotehost~$> exit
```

Test result you can remote sftp without a password.
```
user@localhost~$> sftp user@remoteserver
Sftp>
```