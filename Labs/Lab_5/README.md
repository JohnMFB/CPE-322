# Lab 5

![image](https://github.com/JohnMFB/CPE-322/assets/122575719/f6269de4-03f0-4822-abde-0ab087a90aad)

## Troubleshoot Summary

- Installed Conda paho-mqtt
- Installed Conda Mosquitto, uninstalled
- Installed Mosquitto within Windows C:\Program Files\Mosquitto
- which mosquitto works only in cmd prompt, msys2 terminal cannot view
- which mosquitto_sub only showed conda until uninstalled from conda
- which mosquitto_sub shows on correct path
- Tried disabling Domain network, Private network, and Public network (active) firewalls to allow mosquitto_sub to run

## Current Problem
- mosquitto command runs fine until closed with Ctrl + C
- mosquitto_sub commands give Error
  - Error: No connection could be made because the target machine actively refused it.
