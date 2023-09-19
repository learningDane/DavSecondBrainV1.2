#self-taught 
WireGuard è un programma open-source e un protocollo che implementa la tecnica della [[VPN]] per creare connessioni sicure punto-punto in configurazione routed o bridged. Viene eseguito come modulo nel kernel linux e punta ad avere prestazioni migliori rispetto ad [[IPsec]] e [[OpenVPN]]
# Configurazione del client su Linux
To enter client configuration:
``sudo nano /etc/wireguard/wg0.conf ``

Write the following replacing "xxxx": 

```
[Interface] 
Address = 10.0.0.2/32 
PrivateKey = "contents-of-client-privatekey" 
DNS = 1.1.1.1 

[Peer] 
PublicKey = "contents-of-server-publickey" 
Endpoint = "server-public-ip":51820 
AllowedIPs = 0.0.0.0/0, ::/0
```


To start the connection:
``sudo wg-quick up wg0``
or `sudo systemctl start wg-quick@wg0`

To end the connection:
`sudo wg-quick down wg0`
or `sudo systemctl stop wg-quick@wg0`
