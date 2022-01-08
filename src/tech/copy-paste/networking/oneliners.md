# Networking Oneliners

## Netstats

### Check open ports

With **Netstats**

```sh
 netstat -ltnp | grep -w ':80' 
```

- `l` – tells netstat to only show listening sockets.
- `t` – tells it to display tcp connections.
- `n` – instructs it show numerical addresses.
- `p` – enables showing of the process ID and the process name.
- `grep -w` – shows matching of exact string (:80).

## lsof 

### Check open ports

```shell
lsof -i :80
```

## Nmap

### Simply scan a network or host

Get open ports (most commons are scanned) and more info about the host.

```bash 
nmap 192.168.100.0/24
```

`-sP` flag skips port scanning.

### Get info about a device in a network
```bash
sudo nmap -p 0-65535 -O <IP>
```

This command need to be ran as **sudo** `-O` enables OS detection, `-p <port ranges>` only scans specified ports. Additionally you can try `-sV`, it probes open ports to determine service/version info.

#### CVE detection using Nmap
```bash
nmap -Pn --script vuln <IP>
```

`-Pn` treats all hosts as online -- skip host discovery while `--script`
executes a set of Nmap built-in scripts
