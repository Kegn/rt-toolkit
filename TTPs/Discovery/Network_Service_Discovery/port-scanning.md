# Port Scanning

**Description:** This entry describes how to port scan an internal network

**Mitre Att&ck:** [https://attack.mitre.org/techniques/T1046](https://attack.mitre.org/techniques/T1046/)

**Requirements:** netcat, nmap

## Port Scan with netcat

```sh
# flags we are using
# -v verbose
# -n numeric-only IP, no dns
# -r randomize local and remote ports
# -z zero-I/O mode [used for scanning]
# -w timeout in seconds for connects

nc -v -n -r -z -w1 192.168.1.100 1-65535
```

## Port Scan using TCP Sockets

```sh
for port in {1..65535}; do 2>/dev/null > echo >/dev/tcp/192.168.1.100/$port && echo "[*] Port $port is open"; done
```

## Port scan using Nmap

### Top Ports

```sh
nmap --top-ports 1000 192.168.0.1
```

### Scan List of Hosts

```sh
nmap -iL hosts.txt 
```

### TCP Connect Scan on a CIDR range

```sh
nmap -sT 192.168.0.1/24
```

### TCP Syn Scan

```sh
nmap -sS 192.168.0.1
```

## References
* https://linux.die.net/man/1/nmap
