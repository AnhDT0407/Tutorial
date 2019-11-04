# How to Install Apache Tomcat 9 on Ubuntu 18.04 & 16.04 LTS

Apache Tomcat is another product released by the Apache Software Foundation. It is an open-source implementation of the Java Servlet and JavaServer Pages (JSP) technologies. Tomcat is a web server used for hosting the Java-based web application. Apache Tomcat team has announced its latest Tomcat 9.0.26 release. This article helps you to install Tomcat 9 on Ubuntu 19.04, 18.04 LTS & 16.04 LTS systems.

### 1: Java Installation
You must have Java installed on the system before installing Apache Tomcat on a Linux VPS. Tomcat 9 required Java 8 or later version to work. You can check and verify that Java is installed with the right version.
```java
java version "11.0.2" 2019-01-15 LTS
Java(TM) SE Runtime Environment 18.9 (build 11.0.2+9-LTS)
Java HotSpot(TM) 64-Bit Server VM 18.9 (build 11.0.2+9-LTS, mixed mode)
```

If you don’t have Java installed on your system or installed a lower version, run below commands to satisfy requirements.
```java
sudo apt-get update
sudo apt-get install default-jdk
```

### 2: Download & Install Tomcat 9
You need to download the Tomcat archive from its official download website or mirrors. Download and Install Tomcat 9 archive file using the following commands. You can also visit official download page to download latest available version.
```java
wget http://www-us.apache.org/dist/tomcat/tomcat-9/v9.0.26/bin/apache-tomcat-9.0.26.tar.gz
tar xzf apache-tomcat-9.0.26.tar.gz
sudo mv apache-tomcat-9.0.26 /usr/local/apache-tomcat9
```

### 3: Configure Environment Variables
Now configure the required environment variables for the Tomcat. Set CATALINA_HOME to the extracted tomcat directory. Also, set Java environment variables as per Java installed on your system.
```java
echo "export CATALINA_HOME="/usr/local/apache-tomcat9"" >> ~/.bashrc
echo "export JAVA_HOME="/usr/lib/jvm/java-11-oracle"" >> ~/.bashrc
echo "export JRE_HOME="/usr/lib/jvm/java-11-oracle"" >> ~/.bashrc
source ~/.bashrc
```

### 4: Setup Tomcat User Accounts
Finally we need to create user accounts to secure and access admin/manager pages. Edit `conf/tomcat-users.xml` file in your editor and paste inside `<tomcat-users> </tomcat-users>` tags.
```xml
<!-- user manager can access only manager section -->
<role rolename="manager-gui" />
<user username="manager" password="_SECRET_PASSWORD_" roles="manager-gui" />

<!-- user admin can access manager and admin section both -->
<role rolename="admin-gui" />
<user username="admin" password="_SECRET_PASSWORD_" roles="manager-gui,admin-gui" />
```
 
### 5: Enable Host/Manager for Remote IP
The default manager and host-manager web pages are enabled to access from localhost only. To access these pages from the remote system, you have to allow your IP or IP range in the application-specific context.xml file.

Manager File: **./webapps/manager/META-INF/context.xml**

Host Manager File: `./webapps/host-manager/META-INF/context.xml`

Edit above files and add your IP address like the screenshot. After making changes restart Tomcat service.

Install Apache Tomcat 9

### 6: Starting Tomcat Service
Tomcat is very easy to use, There is no need to compile its source. You simply extract the archive and start the tomcat server. Tomcat by default start on port 8080, So make sure no other application using the same port.
```java
cd /usr/local/apache-tomcat9
chmod +x ./bin/startup.sh
./bin/startup.sh
```

**[Sample Output]**
```java
Using CATALINA_BASE:   /usr/local/apache-tomcat9
Using CATALINA_HOME:   /usr/local/apache-tomcat9
Using CATALINA_TMPDIR: /usr/local/apache-tomcat9/temp
Using JRE_HOME:        /usr/lib/jvm/java-11-oracle
Using CLASSPATH:       /usr/local/apache-tomcat9/bin/bootstrap.jar:/usr/local/apache-tomcat9/bin/tomcat-juli.jar
Tomcat started.
```

### 7: Access Tomcat in Browser
Tomcat server default works on port 8080. Access tomcat in the web browser by connecting your server on port 8080.

Access Tomcat Home- This is default home screen of tomcat 9. There are no authentication required to access this page..
```java
http://localhost:8080 
```
