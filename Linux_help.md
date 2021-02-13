# Linux commands that helps.
---
## 1. Tee
Reads from standard input and write to standard output and files

*Usage : *
``` ls | tee [OPTIONS] [FILENAME] ```

## 2. *python -u*
-u is used to force stdin, stdout, and stderr to be unbuffered, which otherwise is line-buffered on the terminal

*Usage : *
``` python -u python_run.py > filename.txt ```
To save the output as soon as the output is in stdout

## 3. Network commands

1. Adding Gateway
```sudo route add default gw 192.168.1.254 eth0```
2. Adding IP address
```sudo vi /etc/network/interfaces``` 
to restart
``` sudo /etc/init.d/networking restart ```  
OR  
```sudo ifconfig eth0 192.168.0.1 netmask 255.255.255.0```
3. Adding nameserver
```sudo vi /etc/resolv.config```
add ```nameserver 8.8.8.8```
