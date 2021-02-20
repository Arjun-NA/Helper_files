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
and restart with
``` sudo /etc/init.d/networking restart ```  
OR  
```sudo ifconfig eth0 192.168.0.1 netmask 255.255.255.0```
3. Adding nameserver
```sudo vi /etc/resolv.config```
add ```nameserver 8.8.8.8```

## 4. Kill Process
pkill

## 5. Updating Key for older systems

[https://answers.ros.org/question/325039/apt-update-fails-cannot-install-pkgs-key-not-working/](https://answers.ros.org/question/325039/apt-update-fails-cannot-install-pkgs-key-not-working/)
 
## 6. X11 fowarding help

https://unix.stackexchange.com/questions/17255/is-there-a-command-to-list-all-open-displays-on-a-machine

---

If you want the X connection forwarded over SSH, you need to enable it on both the server side and the client side. (Depending on the distribution, it may be enabled or disabled by default.) On the server side, make sure that you have X11Forwarding yes in /etc/sshd_config (or /etc/ssh/sshd_config or wherever the configuration file is). On the client side, pass the -X option to the ssh command, or put ForwardX11 in your ~/.ssh/config.

If you run ssh -X localhost, you should see that $DISPLAY is (probably) localhost:10.0. Contrast with :0.0, which is the value when you're not connected over SSH. (The .0 part may be omitted; it's a screen number, but multiple screens are rarely used.) There are two forms of X displays that you're likely to ever encounter:

Local displays, with nothing before the :.
TCP displays, with a hostname before the :.
With ssh -X localhost, you can access the X server through both displays, but the applications will use a different method: :NUMBER accesses the server via local sockets and shared memory, whereas HOSTNAME:NUMBER accesses the server over TCP, which is slower and disables some extensions.

Note that you need a form of authorization to access an X server, called a cookie and normally stored behind the scenes in the file ~/.Xauthority. If you're using ssh to access a different user account, or if your distribution puts the cookies in a different file, you may find that DISPLAY=:0 doesn't work within the SSH session (but ssh -X will, if it's enabled in the server; you never need to mess with XAUTHORITY when doing ssh -X). If that's a problem, you need to set the XAUTHORITY environment variable or obtain the other user's cookies.

To answer your actual question:

Local displays correspond to a socket in /tmp/.X11-unix.

(cd /tmp/.X11-unix && for x in X*; do echo ":${x#X}"; done)
Remote displays correspond to open TCP ports above 6000; accessing display number N on machine M is done by connecting to TCP port 6000+N on machine M. From machine M itself:

netstat -lnt | awk '
  sub(/.*:/,"",$4) && $4 >= 6000 && $4 < 6100 {
    print ($1 == "tcp6" ? "ip6-localhost:" : "localhost:") ($4 - 6000)
  }'
(The rest of this bullet point is of academic interest only.)

From another machine, you can use nmap -p 6000-6099 host_name to probe open TCP ports in the usual range. It's rare nowadays to have X servers listening on a TCP socket, especially outside the loopback interface.

Strictly speaking, another application could be using a port in the range usually used by X servers. You can tell whether an X server is listening by checking which program has the port open.

lsof -i -n | awk '$9 ~ /:60[0-9][0-9]$/ {print}'
If that shows something ambiguous like sshd, there's no way to know for sure whether it's an X server or a coincidence.

---

*Configuring xming in windows*  
https://aruljohn.com/info/x11forwarding/  

**Setting Interactive Job in Carbonate with X11**
1.  Run Xming in Host PC (Windows). Launch XLaunch and Setup a display.
2.  In Putty (of Host PC) Enable ```ssh --> X11 --> Enable X11 forwarding```. Set display location as per what Xming server shows you when you hover your mouse over the server. eg: ``` :0.0 ```
3.  Connect to the server as usual with Putty with the above setting.
4.  Run ```xclock``` to check if X11 works. if it does this will pop up a clock in your PC which is a window that is forwarded via X11 from Client to Host.
5.  Running Interactive job requires ```-I``` flag when submitting a job. Additionally ```-X```flag for creating X11 forwardable job.
6.  The command will look like this  
``` srun -I -X -N 1 -p gpu --gpus v100:1 --time 12:00:00 --pty bash```  
This creates a bash for you but here the X11 will not work. Open another SSH connection as per the above settings and then connect to the instance via 
``` ssh -X <partition-name> ``` eg: ```ssh -X g2``` and login with your normal credentials. This is now completely helps is X11 forwarding from the allocated node.


## 7. dmesg
to see connected devices messages





