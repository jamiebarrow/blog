# 2014-12-30 Finding the hostname for an IP address on Windows

tags: command line, hostname, ip address, mac address, netbios, networking, Windows

When trying to investigate networking issues, most people know about ping and nslookup. I discovered today that there's also a utility called nbtstat to get some NetBIOS info, including the hostname and MAC address from an IP address.


```shell
nbtstat -a IPADDRESS
```
