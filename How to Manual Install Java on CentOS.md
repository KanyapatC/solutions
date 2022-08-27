# How to Manual Install Java on CentOs

# Install ZFS

Step 1
Go to Download Java 

Link:

https://adoptopenjdk.net/ 

https://docs.aws.amazon.com/corretto/

https://www.azul.com/downloads/?package=jdk

https://bell-sw.com/pages/downloads/#/java-17-lts%20/%20current

https://community.chocolatey.org/packages/openjdk#versionhistory

Recommend: Verify End-of-life product

Create directory

```
 mkdir /app
 mkdir /app/java
 mkdir /app/setup
```

Step 2
Run the below commands:

```
cd /app/setup
wget https://objects.githubusercontent.com/github-production-release-asset-2e65be/372924883/70b80b22-3dc5-4824-bb2d-d0158a3b9b57?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Credential=AKIAIWNJYAX4CSVEH53A%2F20220827%2Fus-east-1%2Fs3%2Faws4_request&X-Amz-Date=20220827T060841Z&X-Amz-Expires=300&X-Amz-Signature=5516f8b80443a25440cd6166c03077dceb6eccce1fa1ea82458ffcf975f34f68&X-Amz-SignedHeaders=host&actor_id=56994838&key_id=0&repo_id=372924883&response-content-disposition=attachment%3B%20filename%3DOpenJDK11U-jdk_x64_linux_hotspot_11.0.16.1_1.tar.gz&response-content-type=application%2Foctet-stream

tar -zxvf OpenJDK11U-jdk_x64_linux_hotspot_11.0.16.1_1.tar.gz.tar.gz
mv jdk-11.0.11+9 /app/java
```

Step 3

Set Enviroment:

```
vim  .bash_profile 
# .bash_profile
# Get the aliases and functions
if [ -f ~/.bashrc ]; then
 . ~/.bashrc
fi
# User specific environment and startup programs
PATH=$PATH:$HOME/.local/bin:$JAVA_HOME/bin
export PATH

JAVA_HOME=/app/java/jdk-11.0.11+9
export JAVA_HOME
```

Step 4

Run the below commands:

```
export JAVA_HOME=/app/java/jdk-11.0.11+9
export PATH=$PATH:$HOME/.local/bin:$JAVA_HOME/bin
```

Step 5

Run the below commands:

```
alternatives --install /usr/bin/java java /app/java/jdk-11.0.11+9/bin/java 2
alternatives --config java
```

Step 6
Select Your Java:

```
alternatives --install /usr/bin/jar jar /app/java/jdk-11.0.11+9/bin/jar 2
alternatives --install /usr/bin/javac javac /app/java/jdk-11.0.11+9/bin/javac 2
alternatives --set jar /app/java/jdk-11.0.11+9/bin/jar 
alternatives --set javac /app/java/jdk-11.0.11+9/bin/javac
```

Step 7
Verify Java version:

```
java -version
openjdk version "11.0.11" 2021-04-20
OpenJDK Runtime Environment AdoptOpenJDK-11.0.11+9 (build 11.0.11+9)
OpenJDK 64-Bit Server VM AdoptOpenJDK-11.0.11+9 (build 11.0.11+9, mixed mode)
```
