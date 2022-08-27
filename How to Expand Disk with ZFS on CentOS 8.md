# How to Expand Disk wtih ZFS on CentOS 8

# Probleam:

  For change group LVM disk full with Tools ZFS for expand pool data


# Install ZFS

Step 1
Go to the /etc/yum.repos.d/ directory.

```
 cd /etc/yum.repos.d/
```

Step 2
Run the below commands:

```
sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*
```

Step 3
Update 

```
yum update -y
```

Step 4
Install required packages:

```
yum install -y libuuid-devel zlib-devel libblkid-devel kernel-devel
```

Step 5
Install rpm required packages:

```
rpm -Uvh http://download.zfsonlinux.org/epel/zfs-release.el8_5.noarch.rpm
rpm -Uvh https://forensics.cert.org/cert-forensics-tools-release-el8.rpm
rpm -Uvh http://dl.fedoraproject.org/pub/epel/epel-release-latest-8.noarch.rpm
```

Step 6
Install zfs:

```
yum install -y zfs
dnf config-manager --disable zfs-kmod
dnf config-manager --enable zfs-testing
dnf install kernel-devel zfs
/sbin/modprobe zfs
```

# Create Pool

Step 1
Create directory for mount

```
mkdir /<Your directory>
```

Step 2
Check device disk with command

```
fdisk -l
```

Step 3
Create Group mount to disk

```
zpool create <YourNamePool> <Your Device>
zfs get mountpoint <YourNamePool>
zfs get mounted <YourNamePool>
zfs set mountpoint=/<Your directory> <YourNamePool>
```

Step 4
Run the below commands:

```
systemctl enable zfs-import-cache
systemctl enable zfs-import-scan
systemctl enable zfs-mount
systemctl enable zfs-share
systemctl enable zfs-zed
systemctl enable zfs.target
reboot
```

Step 5
Verify volum disk

```
df -Ph
```

# Increase Pool

Add disk

```
 zpool add <YourNamePool> <Your Device>
```

Check Status

```
 zpool status <YourNamePool>
 example
# zpool status
  pool: zroot
state: ONLINE
  scan: none requested
config:

        NAME        STATE     READ WRITE CKSUM
        zroot       ONLINE       0     0     0
          da0p3     ONLINE       0     0     0
          da1       ONLINE       0     0     0

errors: No known data errors
[root@server /home/admin]# zpool list
NAME    SIZE  ALLOC   FREE    CAP  DEDUP  HEALTH  ALTROOT
zroot  17.9G  4.04G  13.8G    22%  1.00x  ONLINE  -
```