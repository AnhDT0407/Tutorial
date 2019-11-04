# How to set up HTTPS on Tomcat

This Tomcat Tutorial will show you how to create a self signed cert that you can then use to secure Tomcat.

### Step 1

Open a command prompt window and navigate to your JAVA_HOME bin folder, in our case:
```java
C:\Program Files\Java\jre1.8.0_171\bin
```

### Step 2

Enter the command:
```java
keytool -genkey -alias tomcat -keyalg RSA -keystore “C:\apache-tomcat-xxx\conf\localhost.jks”
```
Note: You should update the tomcat path to match your path 

### Step 3

You will then be prompted for a series of values, in our case we entered:

> enter Keystore password: password
> retype keystore password: password
> what is your first and last name: localhost
> what is the name of your orgainsation unit: IT
> what is the name of your organisation: Darren
> what is the name of your city: Dublin
> what is the name of your state or province: Leinster
> What is the two-letter country code for this unit: IE

When prompted type yes to confirm all is correct.
