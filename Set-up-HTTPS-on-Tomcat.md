# How to set up HTTPS on Tomcat

This Tomcat Tutorial will show you how to create a self signed cert that you can then use to secure Tomcat.

### Step 1

Open a command prompt window and navigate to your JAVA_HOME bin folder, in our case:
```java
C:\Program Files\Java\jre1.xxx\bin
```


### Step 2

Enter the command:
```java
keytool -genkey -alias tomcat -keyalg RSA -keystore “C:\apache-tomcat-xxx\conf\localhost.jks”
```
_Note: You should update the tomcat path to match your path_


### Step 3

You will then be prompted for a series of values, in our case we entered:

```
enter Keystore password: password
retype keystore password: password
what is your first and last name: localhost
what is the name of your orgainsation unit: IT
what is the name of your organisation: Darren
what is the name of your city: Dublin
what is the name of your state or province: Leinster
What is the two-letter country code for this unit: IE
```
When prompted type yes to confirm all is correct.

Next you will be asked to use the same password for <tomcat>
  

### Step 4

Now open the tomcat server.xml file, in our case the file is located here:

```java
C:\apache-tomcat-xxx\conf\server.xml
```

### Step 5

Add the following block to the file, change password in `keystorePass`:

```xml
	<Connector protocol="HTTP/1.1"
		port="8443" maxThreads="200"
		scheme="https" secure="true" SSLEnabled="true"
		keystoreFile="conf\localhost.jks" keystorePass="password"
		clinetAuth="false" sslProtocol="TLS" />
```

### Step 6

Restart Tomcat.


### Step 7

Navigate to https://localhost:8443.

You should first see a certificate warning, click to bypass the warning.


### Step 8

You should now see Tomcat working over HTTPS

Refer: [here](https://darrenoneill.eu/?p=772)
