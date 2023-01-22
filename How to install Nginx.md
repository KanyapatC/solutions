# How to install Nginx

# Amazon Linux, CentOS, Oracle Linux, and RHEL 
NGINX Plus can be installed on the following versions of Amazon Linux CentOS/Oracle Linux/RHEL:
	• Amazon Linux 2018.03+ (x86_64)
	• Amazon Linux 2 LTS (x86_64)
	• CentOS/Oracle Linux/ Red Hat Enterprise Linux 6.5+ (i386, x86_64), 7.4+ (x86_64, ppc64le), 8.0+ (x86_64)

To install NGINX Plus on Amazon Linux, CentOS, Oracle Linux, and RHEL:
1. Create the /etc/ssl/nginx directory:
```
$ sudo mkdir /etc/ssl/nginx
$ cd /etc/ssl/nginx
```
Log in to NGINX Plus Customer Portal and download your nginx-repo.crt and nginx-repo.key files.
2. Copy the files to the /etc/ssl/nginx/ directory:
```
$ sudo cp nginx-repo.crt /etc/ssl/nginx/
$ sudo cp nginx-repo.key /etc/ssl/nginx/
```
3. Install the required ca-certificates dependency:
```
$ sudo yum install ca-certificates
```

4. Download the nginx-plus-repo file and copy it to the /etc/yum.repos.d/ directory. Each version of Amazon Linux, CentOS, Oracle Linux, or RHEL has its own repo file.
For Amazon Linux:
```
$ sudo wget -P /etc/yum.repos.d https://cs.nginx.com/static/files/nginx-plus-amazon.repo
```
For Amazon Linux 2:
```
$ sudo wget -P /etc/yum.repos.d https://cs.nginx.com/static/files/nginx-plus-amazon2.repo
```
For version 6 of CentOS, Oracle Linux, or RHEL:
```
$ sudo wget -P /etc/yum.repos.d https://cs.nginx.com/static/files/nginx-plus-6.repo
```
For version 7.4+ of CentOS, Oracle Linux, or RHEL:
```
$ sudo wget -P /etc/yum.repos.d https://cs.nginx.com/static/files/nginx-plus-7.4.repo
```
For version 8.0+ of CentOS, Oracle Linux, or RHEL:
```
$ sudo wget -P /etc/yum.repos.d https://cs.nginx.com/static/files/nginx-plus-8.repo
```
5. Install the nginx-plus package. Any older NGINX Plus package is automatically replaced.
```
$ sudo yum install nginx-plus
```
6. To enable the nginx service start at boot, run the command:
```
$ sudo systemctl enable nginx.service
```