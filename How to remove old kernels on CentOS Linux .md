# How to remove old kernels on CentOS Linux
For clear old kernels 
Command:

```
# uname -a
Linux localhost.localdomain 3.10.0-693.5.2.el7.x86_64 #1 SMP Fri Oct 20 20:32:50 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```

Check version kernals

```
# rpm -q kernel
kernel-3.10.0-327.36.3.el7.x86_64
kernel-3.10.0-514.2.2.el7.x86_64
kernel-3.10.0-693.5.2.el7.x86_64

```
Remove old unused kernel automatically

Command:

```
# package-cleanup --oldkernels --count=1
```
