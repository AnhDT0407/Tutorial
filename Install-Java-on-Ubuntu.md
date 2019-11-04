# Install Java on Ubuntu

## Install Java 8 using the Oracle JDK
### 1: Update Ubuntu
Again, you should always update your system first before you do anything else. Run the following commands:

```java
apt-get update && apt-get upgrade
```

And install the required package if you don’t have it already installed:

```java
apt-get install software-properties-common
```
### 2: Add the Java repository
The first thing you need to do is add a 3-rd party repository to get the Oracle JDK. We’ll use the one from WebUpd8, but you can use any other repository:

```java
add-apt-repository ppa:webupd8team/java
```

And then update your package list again:

```java
apt-get update
```

### 3: Install Java
So to install the JDK 8th, outdated version, run the following command:

```java
apt-get install oracle-java8-installer
```

Refer: [here](https://thishosting.rocks/install-java-ubuntu/)
