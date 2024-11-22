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

Wireshark
Ping 10.1.1.1
Piece pcap
ARP 
Ping 10 .1.1.1
‘00:50:79:66:68:00  10.1.1.1 expires in 8 seconds’

II
Adresse MAC
PC1> show ip  : 00:50:79:66:68:00
PC2> show ip  : 00:50:79:66:68:01
PC3> show ip  : 00:50:79:66:68:02

IP
PC1> ip 10.1.1.1
Checking for duplicate address...
PC1 : 10.1.1.1 255.255.255.0
PC2> ip 10.1.1.2
Checking for duplicate address...
PC2 : 10.1.1.2 255.255.255.0
PC3> ip 10.1.1.3
Checking for duplicate address...
PC3 : 10.1.1.3 255.255.255.0

Ping 
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

III

dnf -y install dhcp-server

vi /etc/dhcp/dhcpd.conf

subnet 10.1.1.0 netmask 255.255.255.0 {
    range dynamic-bootp 10.0.0.0 10.0.0.50;
    option broadcast-address 10.0.0.255;
}

