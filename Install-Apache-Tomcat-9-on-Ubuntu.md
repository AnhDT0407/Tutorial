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
