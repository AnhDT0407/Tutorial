# Uninstall Oracle JDK on macOS

<br>

View list JDK
```
/usr/libexec/java_home -V
```

If you have a JDK installation that was installed by Oracle JDK installer, you need to find the JDK directory in the `/Library/Java/JavaVirtualMachines` path. Open a terminal window, change the current directory:
```
cd /Library/Java/JavaVirtualMachines
```

Then type `ls` command to see the installed JDK directories. You may find more than one JDK. Then type the following command to remove a JDK installation completely from macOS:
```
sudo rm -rf jdk-version
```

This command will be executed under root privilege (password required) - the specified JDK directory will be deleted recursively and forcefully.

If you uninstall JDK 1.8, you also need to remove 2 other directories using the following commands:
```
sudo rm -rf /Library/Internet\ Plug-Ins/JavaAppletPlugin.plugin
sudo rm -rf /Library/PreferencePanes/JavaControlPanel.prefpane
```

Then you’re all done.
