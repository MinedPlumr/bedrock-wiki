---
title: Getiing Started
---


# What is WebSocket?

WebSocket is a protocol enabling real-time, two-way communication between a client and server over a persistent connection.

# How can WebSocket be used in Minecraft?
You can subscribe to events and inspect packets to use external APIs in Minecraft.

# Installation Guide
Create a folder and run this command in the terminal.
```bat
npm init -y
npm install ws uuid
```
Once the ``package.json``, ``package-lock.json``, and ``node_modules`` have been created, the installation is complete

If the installation is complete, create an ``index.js`` file inside the folder.

Next, run the command prompt as an administrator and execute the following command.
```bat
CheckNetIsolation LoopbackExempt -a -n="Microsoft.MinecraftUWP_8wekyb3d8bbwe"
```
If you are using the beta version of Minecraft, execute the following command.
```bat
CheckNetIsolation LoopbackExempt -a -n="Microsoft.MinecraftWindowsBeta_8wekyb3d8bbwe"
```
This is to prevent WebSocket connection failure.
