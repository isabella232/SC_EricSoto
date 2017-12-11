# DeskbookServer Readme

## Summary

Deskbook is an iOS app that shows an employee directory. It is served by the companion "Server" called DeskbookServer. The server is a NodeJS app that feeds both a directory website (not the focus of this Screencast) and an API that is consumed by the iOS app.

In order to follow along with the iOS App, it is necessary to install the DeskbookServer and to run it so that it's feeding data to the app.

Note that the app is coded to the IP address 127.0.0.1. The iOS Simulator has no problem accessing the local network. However, if you want to run run the app on a physical device, you must:

- Figure out your mac's private network IP
- Change the source code to point to your mac's IP
  - See the steps below if you wish to run on your device.

## Installing DeskbookServer

> **Note**: Begin work in the **Server** directory of the materials for this tutorial.

## 1) Install/verify NodeJS

Open up a new terminal window and switch to the **Server** directory. Let's check to see if you already have NodeJS installed.

```bash
node --version
```

If you have NodeJS version 8 or better, skip to the next step! 

To install NodeJS, we've already provided the installer package. Still on the **Server** directory, open the installer package:

```bash
open node-v8.9.0.pkg
```

Follow the prompts to install NodeJS.

## 2) Start up the Deskbook server

Now that we have NodeJS running, let's start our server.

```bash
cd DeskbookServer
./xStartDev.sh
```

This will start up the NodeJS server and you should see something like:

```bash
> deskbookserver@0.0.0 start-dev /your/path/to/DeskbookServer
> nodemon ./bin/www

[nodemon] 1.12.1
[nodemon] to restart at any time, enter `rs`
[nodemon] watching: *.*
[nodemon] starting `node ./bin/www`
```

Then, open up a web browser and visit http://127.0.0.1:3000/. Welcome to Deskbook! Note, clicking on any row takes you to the profile page for the staff member.

If you look back at your terminal, you'll see that NodeJS outputs console information as you interact with the app. We don't really need to pay attention to that, so feel free to minimize terminal (but don't close it because we need that process running!)

## 3) OPTIONAL: Point the Deskbook iOS app to your local server once you know your local network IP (and assuming your phone is connected to the same network as your Mac.)

Open **StaffAPI.swift** (in the **API** group) and change the apiHost:
```
private let apiHost = "http://[your-local-network-ip]:3000/api"
```

