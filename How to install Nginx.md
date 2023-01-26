# How to install Nginx

# Amazon Linux, CentOS, Oracle Linux, and RHEL 
NGINX Plus can be installed on the following versions of Amazon Linux CentOS/Oracle Linux/RHEL:
- Amazon Linux 2018.03+ (x86_64)
- Amazon Linux 2 LTS (x86_64)
- CentOS/Oracle Linux/ Red Hat Enterprise Linux 6.5+ (i386, x86_64), 7.4+ (x86_64, ppc64le), 8.0+ (x86_64)

To install NGINX Plus on Amazon Linux, CentOS, Oracle Linux, and RHEL:
Create the /etc/ssl/nginx directory:
```
$ sudo mkdir /etc/ssl/nginx
$ cd /etc/ssl/nginx
```
Log in to NGINX Plus Customer Portal and download your nginx-repo.crt and nginx-repo.key files.
Copy the files to the /etc/ssl/nginx/ directory:
```
$ sudo cp nginx-repo.crt /etc/ssl/nginx/
$ sudo cp nginx-repo.key /etc/ssl/nginx/
```
Install the required ca-certificates dependency:
```
$ sudo yum install ca-certificates
```
Download the nginx-plus-repo file and copy it to the /etc/yum.repos.d/ directory. Each version of Amazon Linux, CentOS, Oracle Linux, or RHEL has its own repo file.
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
Install the nginx-plus package. Any older NGINX Plus package is automatically replaced.
```
$ sudo yum install nginx-plus
```
To enable the nginx service start at boot, run the command:
```
$ sudo systemctl enable nginx.service
```

# Debian and Ubuntu 
NGINX Plus can be installed on the following versions of Debian or Ubuntu:
	- Debian 9 (“Stretch”)
	- Debian 10 (“Buster”)
	- Ubuntu 16.04 LTS (“Xenial”) (i386, x86_64, ppc64le, aarch64)
	- Ubuntu 18.04 LTS (“Bionic”)
	- Ubuntu 19.04 (“Disco”)
	- Ubuntu 19.10 (“Eoan”)
  
To install NGINX Plus on Debian or Ubuntu:
	1. Create the /etc/ssl/nginx directory:

```
$ sudo mkdir /etc/ssl/nginx
$ cd /etc/ssl/nginx
```

	2. Log in to NGINX Plus Customer Portal and download your nginx-repo.crt and nginx-repo.key files.
	3. Copy the files to the /etc/ssl/nginx/ directory:

```
$ sudo cp nginx-repo.crt /etc/ssl/nginx/
$ sudo cp nginx-repo.key /etc/ssl/nginx/
```

	4. Download the NGINX signing key from nginx.org and add it:

```
$ sudo wget https://nginx.org/keys/nginx_signing.key
$ sudo apt-key add nginx_signing.key
```

    5. Install the apt-utils package and the NGINX Plus repository.
	- For Debian:

```
$ sudo apt-get install apt-transport-https lsb-release ca-certificates
$ printf "deb https://plus-pkgs.nginx.com/debian `lsb_release -cs` nginx-plus\n" | sudo tee /etc/apt/sources.list.d/nginx-plus.list
```

	- For Ubuntu:

```
$ sudo apt-get install apt-transport-https lsb-release ca-certificates
$ printf "deb https://plus-pkgs.nginx.com/ubuntu `lsb_release -cs` nginx-plus\n" | sudo tee /etc/apt/sources.list.d/nginx-plus.list
```

	6. Download the 90nginx file to /etc/apt/apt.conf.d:

```
$ sudo wget -q -O /etc/apt/apt.conf.d/90nginx https://cs.nginx.com/static/files/90nginx
```

	7. Update the repository information:

```
$ sudo apt-get update
```

	8. Install the nginx-plus package. Any older NGINX Plus package is automatically replaced.

```
$ sudo apt-get install -y nginx-plus
```

#  SUSE Linux Enterprise Server 
	NGINX Plus can be installed on the following versions of SUSE Linux Enterprise Server:
	SUSE Linux Enterprise Server 12, 15 (x86_64)
	To install NGINX Plus on SLES:
		1. Create the /etc/ssl/nginx directory:

```
$ sudo mkdir /etc/ssl/nginx
$ cd /etc/ssl/nginx
```

		2. Log in to NGINX Plus Customer Portal and download your nginx-repo.crt and nginx-repo.key files.
		3. Create a file bundle of the certificate and key:

```
$ cat /etc/ssl/nginx/nginx-repo.crt /etc/ssl/nginx/nginx-repo.key > /etc/ssl/nginx/nginx-repo-bundle.crt
```
		4. Install the required ca-certificates dependency:

```
$ zypper install ca-certificates
```

		5. Add the nginx-plus repo.
	For SLES 12:

```
$ zypper addrepo -G -t yum -c 'https://plus-pkgs.nginx.com/sles/12?ssl_clientcert=/etc/ssl/nginx/nginx-repo-bundle.crt&ssl_verify=peer' nginx-plus
```

	For SLES 15:

```
$ zypper addrepo -G -t yum -c 'https://plus-pkgs.nginx.com/sles/15?ssl_clientcert=/etc/ssl/nginx/nginx-repo-bundle.crt&ssl_verify=peer' nginx-plus
```

		6. Install the nginx-plus package. Any older NGINX Plus package is automatically replaced.

```
$ zypper install nginx-plus
```
