#self-taught 
# NAT
Network Address Translation
Parliamo di terzo livello
Classi di Indirizzi Privati:

| Classe               | Network Number                 | Network Mask  | # of networks | # of hosts per network |
| -------------------- | ------------------------------ | ------------- | :-----------: | :--------------------: |
| A                    | 10.0.0.0                       | 255.0.0.0     |      126      |       16.646.144       |
| B                    | 172.16.0.0 -> 172.31.0.0       | 255.255.0.0   |    16.383     |         65.024         |
| C                    | 192.168.0.0 -> 192.168.255.255 | 255.255.255.0 |   2.097.151   |          254           |
| LOOPBACK (localhost) | 127.0.0.0->127.0.0.7           | 255.255.255.0 |       -       |           -            |
# Mac Addresses
Media Access Control Addresses
Segnalato da "ether" nell'`ifconfig`. Quando parliamo di Indirizzi Mac, parliamo di ___layer 2 (o switching)___. Gli indirizzi MAC hanno identificatori: le prime tre coppie dell'indirizzo possono essere inserite in un _Mac Address Lookup_, per vedere quale ditta ha fabbricato la scheda di rete.
# Protocolli
Stiamo parlando del quarto livello.
___Three-way Handshake___: inviamo un pacchetto ___SYN___, riceviamo indietro un pacchetto ___SYN ACK___ e a quel punto inviamo il pacchetto ___ACK___. 
___TCP___ = transmission control protocol. Protocollo orientato alla connessione. Più affidabile, usato per siti web, ssh ecc. Funziona su una stretta a 3 mani.
	FTP (21) -> file transfer protocol, mettere/togliere file da un server
	SSH (22) -> encrypted remote work
	Telnet (23) -> remote work
	SMTP (25) -> mail
	DNS (53) -> domain name system, passare da indirizzi IP a nomi 
	HTTP (80) / HTTPS (443) -> siti web
	POP3 (110) -> mail
	SMB (139 + 445) -> file shares / samba
	IMAP (142) -> mail
___UDP___ = user datagram protocol. Protocollo senza connessione.
	DNS (53)
	DHCP (67, 68) -> ti assegna un indirizzo ipv4, a meno che tu non ne richieda uno statico
	TFTP (69) -> trivial FTP
	SNMP (161) -> simple network manager protocol
# Il Modello OSI
1 P -> ___physical layer___
2 D -> ___switching layer___, mac addresses
3 N -> ___network layer___: ip addresses,  routing
4 T -> ___transport layer___: tcp/udp
5 S -> ___session layer___: session management
6 P -> ___presentation layer___, media: wmv, jpeg, mov
7 A -> ___application layer___: https, smtp
# Subnetting
Normalmente i network domestici sono a _/24_, quindi permette di avere 256 hosts (254) e la mask è 255.255.255.0
Subnetting cheat sheet:

| Subnet x.0.0.0          |               |                      |             |             |             |            |            |            |
| ----------------------- | ------------- | -------------------- | ----------- | ----------- | ----------- | ---------- | ---------- | ---------- |
| CIDR                    | /1            | /2                   | /3          | /4          | /5          | /6         | /7         | /8         |
| Hosts                   | 2.147.483.648 | 1.073.741.824        | 536.870.912 | 268.435.456 | 134.217.728 | 67.108.864 | 33.554.432 | 16.777.216 |
| Class A                 |               | Subnet 255.x.0.0     |             |             |             |            |            |            |
| CIDR                    | /9            | /10                  | /11         | /12         | /13         | /14        | /15        | /16        |
| Hosts                   | 8.388.608     | 4.194.304            | 2.097.152   | 1.048.576   | 524.2880    | 262.144    | 131.072    | 65.536     |
| Class B                 |               | Subnet 255.255.x.0   |             |             |             |            |            |            |
| CIDR                    | /17           | /18                  | /19         | /20         | /21         | /22        | /23        | /24        |
| Hosts                   | 32.768        | 16.384               | 8.192       | 4.096       | 2.048       | 1.024      | 512        | 256        |
| Class C                 |               | Subnet 255.255.255.x |             |             |             |            |            |            |
| CIDR                    | /25           | /26                  | /27         | /28         | /29         | /30        | /31        | /32        |
| Hosts                   | 128           | 64                   | 32          | 16          | 8           | 4          | 2          | 1          |
| Subnet mask (replace x) | 128           | 192                  | 224         | 240         | 248         | 252        | 254        | 255        |
ipaddressguide.com/cidr 
# Unix
`ifconfig` 
```c++
[kwisatzhaderach@thufirhawat ~]$ ifconfig  
lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536  
       inet 127.0.0.1  netmask 255.0.0.0
       inet6 ::1  prefixlen 128  scopeid 0x10<host>
       loop  txqueuelen 1000  (Local Loopback)  
       RX packets 674  bytes 53576 (52.3 KiB)
       RX errors 0  dropped 0  overruns 0  frame 0  
       TX packets 674  bytes 53576 (52.3 KiB)  
       TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0  
  
wlan0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500  
       inet 192.168.1.16  netmask 255.255.255.0  broadcast 192.168.1.255 //ipv4 address, ogni numero è in 4 byte, 2^32 combinazioni, già tutte comprate da ditte
       inet6 fe80::ce8a:eaf:a1dc:fb5e  prefixlen 64  scopeid 0x20<link> //ipv6 adress di solito è in esadecimale, 2^128 combinazioni
       ether c0:b8:83:7c:e7:af  txqueuelen 1000  (Ethernet) //MAC ADDress, c0:b8:83 indica Intel per esempio
       RX packets 92078  bytes 115333734 (109.9 MiB)  
       RX errors 0  dropped 0  overruns 0  frame 0  
       TX packets 13166  bytes 2217903 (2.1 MiB)  
       TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```
