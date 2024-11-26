# TP1

MAC 1
PC1>show ip
‘00:50:79:66:68:00’
MAC  2
PC2> show ip 
‘00:50:79:66:68:01’

PC1
PC1> show ip
‘ip : O.O.O.O’
Ip 10.1.1.1
PC1> show ip
‘Ip : 10.1.1.1’
PC2
PC2> show ip
‘Ip : 0.0.0.’
PC2> Show ip
Ip 10.1.1.2
PC2> show ip

PC2 -> PC1
Ping 10.1.1.1
‘84 bytes from 10.1.1.1 icmp_seq=1 ttl=64 time=0.906 ms
84 bytes from 10.1.1.1 icmp_seq=2 ttl=64 time=0.936 ms
84 bytes from 10.1.1.1 icmp_seq=3 ttl=64 time=0.832 ms
84 bytes from 10.1.1.1 icmp_seq=4 ttl=64 time=0.765 ms
84 bytes from 10.1.1.1 icmp_seq=5 ttl=64 time=0.595 ms’

### Wireshark
Ping 10.1.1.1
Piece pcap
ARP 
Ping 10 .1.1.1
‘00:50:79:66:68:00  10.1.1.1 expires in 8 seconds’

## II
Adresse MAC
PC1> show ip  : 00:50:79:66:68:00
PC2> show ip  : 00:50:79:66:68:01
PC3> show ip  : 00:50:79:66:68:02

### IP
PC1> ip 10.1.1.1
Checking for duplicate address...
PC1 : 10.1.1.1 255.255.255.0
PC2> ip 10.1.1.2
Checking for duplicate address...
PC2 : 10.1.1.2 255.255.255.0
PC3> ip 10.1.1.3
Checking for duplicate address...
PC3 : 10.1.1.3 255.255.255.0

### Ping 
PC1> ping 10.1.1.2
84 bytes from 10.1.1.2 icmp_seq=1 ttl=64 time=1.286 ms
84 bytes from 10.1.1.2 icmp_seq=2 ttl=64 time=0.539 ms
84 bytes from 10.1.1.2 icmp_seq=3 ttl=64 time=0.616 ms
84 bytes from 10.1.1.2 icmp_seq=4 ttl=64 time=1.022 ms
84 bytes from 10.1.1.2 icmp_seq=5 ttl=64 time=0.867 ms

PC2> ping 10.1.1.3

84 bytes from 10.1.1.3 icmp_seq=1 ttl=64 time=0.622 ms
84 bytes from 10.1.1.3 icmp_seq=2 ttl=64 time=0.758 ms
84 bytes from 10.1.1.3 icmp_seq=3 ttl=64 time=0.724 ms
84 bytes from 10.1.1.3 icmp_seq=4 ttl=64 time=0.663 ms
84 bytes from 10.1.1.3 icmp_seq=5 ttl=64 time=0.553 ms

PC1> ping 10.1.1.3
84 bytes from 10.1.1.3 icmp_seq=1 ttl=64 time=0.824 ms
84 bytes from 10.1.1.3 icmp_seq=2 ttl=64 time=1.246 ms
84 bytes from 10.1.1.3 icmp_seq=3 ttl=64 time=0.630 ms
84 bytes from 10.1.1.3 icmp_seq=4 ttl=64 time=0.570 ms
84 bytes from 10.1.1.3 icmp_seq=5 ttl=64 time=0.922 ms

## III

dnf -y install dhcp-server

vi /etc/dhcp/dhcpd.conf


default-lease-time 3600;
max-lease-time 86400:

authoritative;
subnet 10.1.1.0 netmask 255.255.255.0 {
    range dynamic-bootp 10.1.1.0 10.1.1.50;
    option routers 10.1.1.1;
    option domain-name-servers 8.8.8.8, 8.8.4.4;
    option subnet-mask 255.255.255.0;
}


sudo systemctl enable dhcpd
sudo systemct status dhcpd


PC1> ip dhcp
DDORA IP 10.1.1.10/24 GW 10.1.1.1

PC1> show ip

NAME        : PC1[1]
IP/MASK     : 10.1.1.10/24
GATEWAY     : 10.1.1.1
DNS         : 8.8.8.8  8.8.4.4
DHCP SERVER : 10.1.1.2
DHCP LEASE  : 3555, 3600/1800/3150
MAC         : 00:50:79:66:68:00
LPORT       : 20007
RHOST:PORT  : 127.0.0.1:20008
MTU         : 1500


PC2> ip dhcp
DDORA IP 10.1.1.11/24 GW 10.1.1.1

PC2> show ip

NAME        : PC2[1]
IP/MASK     : 10.1.1.11/24
GATEWAY     : 10.1.1.1
DNS         : 8.8.8.8  8.8.4.4
DHCP SERVER : 10.1.1.2
DHCP LEASE  : 2935, 3600/1800/3150
MAC         : 00:50:79:66:68:01
LPORT       : 20009
RHOST:PORT  : 127.0.0.1:20010
MTU         : 1500

PC3> ip dhcp
DDORA IP 10.1.1.12/24 GW 10.1.1.1


PC3> show ip

NAME        : PC3[1]
IP/MASK     : 10.1.1.12/24
GATEWAY     : 10.1.1.1
DNS         : 8.8.8.8  8.8.4.4
DHCP SERVER : 10.1.1.2
DHCP LEASE  : 3589, 3600/1800/3150
MAC         : 00:50:79:66:68:02
LPORT       : 20012
RHOST:PORT  : 127.0.0.1:20013
MTU         : 1500


sudo apt install dnsmasq
sudo nano /etc/dnsmasq.conf


interface=eth0 
dhcp-range=10.1.1.210,10.1.1.250,12h
dhcp-option=3,10.1.1.1

sudo systemctl restart dnsmasq
sudo systemctl enable dnsmasq


PC3> ip dhcp
DORA IP 10.1.1.247/24 GW 10.1.1.1

PC3> show ip

NAME        : PC3[1]
IP/MASK     : 10.1.1.247/24
GATEWAY     : 10.1.1.1
DNS         : 10.1.1.16
DHCP SERVER : 10.1.1.16
DHCP LEASE  : 43197, 43200/21600/37800
MAC         : 00:50:79:66:68:02
LPORT       : 20012
RHOST:PORT  : 127.0.0.1:20013
MTU         : 1500


## Dhcp Spoofing

PC1> show ip

NAME        : PC1[1]
IP/MASK     : 0.0.0.0/0
GATEWAY     : 0.0.0.0
DNS         :
MAC         : 00:50:79:66:68:01
LPORT       : 20008
RHOST:PORT  : 127.0.0.1:20009
MTU         : 1500

PC1> ip dhcp
DDORA IP 10.1.1.246/24 GW 10.1.1.1

PC1> ip dhcp
DORA IP 10.1.1.11/24 GW 10.1.1.1

PC1> ip dhcp
DORA IP 10.1.1.11/24 GW 10.1.1.1

PC1> ip dhcp
DORA IP 10.1.1.11/24 GW 10.1.1.1

PC1> ip dhcp
DORA IP 10.1.1.246/24 GW 10.1.1.1
