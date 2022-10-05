# Flutter-on-Ubuntu-20.04-LTS


## Step 1: Prerequisites

a) You should have a running Ubuntu 20.04 LTS Server.

b) You should have sudo or root access to run privileged commands.

c) You should have snap, apt, wget and tar utility available in your Server.


## Step 2: Update Your Server
You can update your System packages to the latest version by using apt update command. 

```
root@nikhil:~# apt update
```


## Step 3: Install Flutter

There are multiple ways to install flutter on Linux based systems. Here we will see the installation by two different ways. You can choose to install using either of them.

### a) Using Snapd
```
snap install flutter --classic
```

### b) Using Tar File
```
wget https://storage.googleapis.com/flutter_infra_release/releases/stable/linux/flutter_linux_2.8.1-stable.tar.xz
```
Then extract the package by using tar -xvf flutter_linux_2.8.1-stable.tar.xz command. This will extract the package in a local flutter directory.


Then export the flutter bin directory using export PATH="$PATH:`pwd`/flutter/bin" command.
Be mindful that this is just a temporary export which will not work if you close your current session. So to make it permanent it is always recommended to export your path from either ~/.profile or ~/.bashrc.

```
export PATH="$PATH:`pwd`/flutter/bin"
```

## Step 4: Check Flutter Version

```
flutter --version
```

## Step 5: Check SDK Path(Optional)

Once you have the snap installed, you can use flutter sdk-path command to display your flutter SDK path. It is important to note here that below command will only work if you have installed flutter as a snap.

```
flutter sdk-path
```

## Step 6: Run Flutter Doctor

You can run flutter doctor to check if there are any dependencies you need to install to complete the setup. 
```
flutter doctor
```

## Step 7: Run Flutter Devices

You can check for any connected devices using flutter devices command. If chrome is already installed then this command will output a chrome device that opens the chrome browser with your app running and a web server that provides the URL serving the app.

```
flutter devices
```

## Step 8: Create a New App

To create a new app, you need to use flutter create <app_name> syntax. 

```
flutter create myapp
```

## Step 9: Run Flutter App

Once the app created successfully, you can go inside the app and launch it by using flutter run command. This will serve your app from localhost in Google Chrome.

 if you have multiple connected devices and you want to launch your app in chrome only then you need to use flutter run -d chrome command. Since in our case we have only chrome so running flutter run will by default launch the app in Chrome browser.

```
root@nikhil:~# cd myapp/
root@nikhil:~/myapp# flutter run
```


## Step 10: Uninstall Flutter

```
 snap remove flutter
 ```
 
 
 ## Useful flutter commands
 
 
 ```
 flutter create my_app

cd my_app

flutter analyze =  The flutter analyze command is a wrapper around the dartanalyzer tool. It performs static analysis of your code. 

flutter test = Flutter automated testing

flutter run lib/main.dart

flutter devices

flutter config --enable-web = Once web is enabled, flutter devices outputs a device named Chrome . After enabling web support, restart the IDE. You should now see Chrome (web) in the device pulldown.

flutter run -d chrome = To serve your app from localhost in Chrome, enter the following from the top of the package, If there aren’t any other connected devices, the -d chrome is optional.


flutter build web = Add web support, you should see a build folder (/build/web) in the root directory, just copy that folder and host it on a web server
```
