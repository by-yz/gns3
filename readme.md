# TP3 

### Partie I

R1#show ip interface brief
Interface                  IP-Address      OK? Method Status                Protocol
FastEthernet0/0            unassigned      YES unset  administratively down down
FastEthernet0/1            unassigned      YES unset  administratively down down
FastEthernet1/0            unassigned      YES unset  administratively down down
FastEthernet2/0            unassigned      YES unset  administratively down down

R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.

R1(config)#interface FastEthernet 1/0

R1(config-if)#ip address 10.3.1.254

PC1> show ip

NAME        : PC1[1]
IP/MASK     : 0.0.0.0/0
GATEWAY     : 0.0.0.0
DNS         :
MAC         : 00:50:79:66:68:00
LPORT       : 20026
RHOST:PORT  : 127.0.0.1:20027
MTU         : 1500

PC1> ip 10.3.1.1
Checking for duplicate address...
PC1 : 10.3.1.1 255.255.255.0

PC1> show ip

NAME        : PC1[1]
IP/MASK     : 10.3.1.1/24
GATEWAY     : 0.0.0.0
DNS         :
MAC         : 00:50:79:66:68:00
LPORT       : 20026
RHOST:PORT  : 127.0.0.1:20027
MTU         : 1500

PC2> show ip

NAME        : PC2[1]
IP/MASK     : 0.0.0.0/0
GATEWAY     : 0.0.0.0
DNS         :
MAC         : 00:50:79:66:68:01
LPORT       : 20028
RHOST:PORT  : 127.0.0.1:20029
MTU         : 1500

PC2> ip 10.3.1.2
Checking for duplicate address...
PC2 : 10.3.1.2 255.255.255.0

PC2> show ip

NAME        : PC2[1]
IP/MASK     : 10.3.1.2/24
GATEWAY     : 0.0.0.0
DNS         :
MAC         : 00:50:79:66:68:01
LPORT       : 20028
RHOST:PORT  : 127.0.0.1:20029
MTU         : 1500


R1#show ip interface brief
Interface                  IP-Address      OK? Method Status                Protocol
FastEthernet0/0            unassigned      YES unset  administratively down down
FastEthernet0/1            unassigned      YES unset  administratively down down
FastEthernet1/0            unassigned      YES unset  administratively down down
FastEthernet2/0            10.3.12.1       YES manual administratively down down
R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#interface FastEthernet 1/0
R1(config-if)#ip address 10.3.1.254 255.255.255?
A.B.C.D

R1(config-if)#ip address 10.3.1.254 255.255.255.0
R1(config-if)#no shut
R1(config-if)#exit
R1(config)#
*Mar  1 00:15:46.471: %LINK-3-UPDOWN: Interface FastEthernet1/0, changed state to up
*Mar  1 00:15:47.563: %LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet1/0, changed state to up
R1(config)#exit
R1#
*Mar  1 00:15:50.259: %SYS-5-CONFIG_I: Configured from console by console
R1#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
FastEthernet0/0            unassigned      YES unset  administratively down down
FastEthernet0/1            unassigned      YES unset  administratively down down
FastEthernet1/0            10.3.1.254      YES manual up                    up  
FastEthernet2/0            10.3.12.1       YES manual administratively down down

mauvaise interface -->

R1#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
FastEthernet0/0            unassigned      YES unset  administratively down down
FastEthernet0/1            10.3.1.254      YES manual administratively down down
FastEthernet1/0            10.3.12.1       YES manual up                    up  
FastEthernet2/0            unassigned      YES manual up                    up  


R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#interface FastEthernet 0/0
R1(config-if)#ip address dhcp
R1(config-if)#no shut
R1(config-if)#exit
*Mar  1 00:28:46.211: %LINK-3-UPDOWN: Interface FastEthernet0/0, changed state to up
*Mar  1 00:28:47.211: %LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/0, changed state to up
R1(config-if)#exit
R1(config)#exit

R1#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
FastEthernet0/0            192.168.122.237 YES DHCP   up                    up  
FastEthernet0/1            10.3.1.254      YES manual up                    up  
FastEthernet1/0            10.3.12.1       YES manual up                    up  
FastEthernet2/0            unassigned      YES manual up                    up  


on refais la même mais pour r2 ( ya eu un bug donc j'ai juste la fin)
R2#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
FastEthernet0/0            10.3.12.2       YES manual up                    up  
FastEthernet0/1            10.3.2.254      YES manual up                    up  
FastEthernet1/0            unassigned      YES unset  administratively down down
FastEthernet2/0            unassigned      YES unset  administratively down down


PC3> show ip

NAME        : PC3[1]
IP/MASK     : 0.0.0.0/0
GATEWAY     : 0.0.0.0
DNS         :
MAC         : 00:50:79:66:68:03
LPORT       : 20030
RHOST:PORT  : 127.0.0.1:20031
MTU         : 1500

PC3> ip 10.3.2.1
Checking for duplicate address...
PC3 : 10.3.2.1 255.255.255.0

PC3> show ip

NAME        : PC3[1]
IP/MASK     : 10.3.2.1/24
GATEWAY     : 0.0.0.0
DNS         :
MAC         : 00:50:79:66:68:03
LPORT       : 20030
RHOST:PORT  : 127.0.0.1:20031
MTU         : 1500


PC4> show ip

NAME        : PC4[1]
IP/MASK     : 0.0.0.0/0
GATEWAY     : 0.0.0.0
DNS         :
MAC         : 00:50:79:66:68:01
LPORT       : 20032
RHOST:PORT  : 127.0.0.1:20033
MTU         : 1500

PC4> ip 10.3.2.2
Checking for duplicate address...
PC4 : 10.3.2.2 255.255.255.0

PC4> show ip

NAME        : PC4[1]
IP/MASK     : 10.3.2.2/24
GATEWAY     : 0.0.0.0
DNS         :
MAC         : 00:50:79:66:68:01
LPORT       : 20032
RHOST:PORT  : 127.0.0.1:20033
MTU         : 1500

PC3> ping 10.3.1.1

84 bytes from 10.3.1.1 icmp_seq=1 ttl=62 time=40.644 ms
84 bytes from 10.3.1.1 icmp_seq=3 ttl=62 time=41.821 ms
84 bytes from 10.3.1.1 icmp_seq=5 ttl=62 time=44.604 ms

R1#show arp
Protocol  Address          Age (min)  Hardware Addr   Type   Interface
Internet  10.3.12.1               -   c401.0531.0010  ARPA   FastEthernet1/0
Internet  10.3.12.2              48   c402.054f.0000  ARPA   FastEthernet1/0
Internet  10.3.1.1                6   0050.7966.6802  ARPA   FastEthernet0/1
Internet  10.3.1.2                4   0050.7966.6800  ARPA   FastEthernet0/1
Internet  192.168.122.1           6   5254.0023.04c2  ARPA   FastEthernet0/0
Internet  10.3.1.254              -   c401.0531.0001  ARPA   FastEthernet0/1
Internet  192.168.122.237         -   c401.0531.0000  ARPA   FastEthernet0/0

R1#ping 1.1.1.1

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 1.1.1.1, timeout is 2 seconds:
!!!!!
Success rate is 100 percent (5/5), round-trip min/avg/max = 88/97/124 ms


PC1> ping 1.1.1.1

84 bytes from 1.1.1.1 icmp_seq=1 ttl=57 time=74.438 ms
84 bytes from 1.1.1.1 icmp_seq=2 ttl=57 time=52.365 ms
84 bytes from 1.1.1.1 icmp_seq=3 ttl=57 time=47.411 ms
84 bytes from 1.1.1.1 icmp_seq=4 ttl=57 time=43.226 ms
84 bytes from 1.1.1.1 icmp_seq=5 ttl=57 time=66.272 ms


PC3> ping 8.8.8.8

8.8.8.8 icmp_seq=1 timeout
8.8.8.8 icmp_seq=2 timeout
8.8.8.8 icmp_seq=3 timeout
84 bytes from 8.8.8.8 icmp_seq=4 ttl=113 time=48.200 ms
84 bytes from 8.8.8.8 icmp_seq=5 ttl=113 time=61.872 ms


### Partie II

modif ip vpcs dans config

IOU1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
IOU1(config)#vlan 10
IOU1(config-vlan)#name admins
IOU1(config-vlan)#exit
IOU1(config)#vlan 20
IOU1(config-vlan)#name guests
IOU1(config-vlan)#exit
IOU1(config)#exit
IOU1#show vl
*Dec 16 12:58:56.752: %SYS-5-CONFIG_I: Configured from console by console
IOU1#show vlan

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Et0/0, Et0/1, Et0/2, Et0/3
                                                Et1/0, Et1/1, Et1/2, Et1/3
                                                Et2/0, Et2/1, Et2/2, Et2/3
                                                Et3/0, Et3/1, Et3/2, Et3/3
10   admins                           active
20   guests                           active
1002 fddi-default                     act/unsup
1003 token-ring-default               act/unsup
1004 fddinet-default                  act/unsup
1005 trnet-default                    act/unsup

VLAN Type  SAID       MTU   Parent RingNo BridgeNo Stp  BrdgMode Trans1 Trans2
---- ----- ---------- ----- ------ ------ -------- ---- -------- ------ ------
1    enet  100001     1500  -      -      -        -    -        0      0
10   enet  100010     1500  -      -      -        -    -        0      0
20   enet  100020     1500  -      -      -        -    -        0      0
1002 fddi  101002     1500  -      -      -        -    -        0      0
1003 tr    101003     1500  -      -      -        -    -        0      0
1004 fdnet 101004     1500  -      -      -        ieee -        0      0
1005 trnet 101005     1500  -      -      -        ibm  -        0      0
 --More--



IOU1(config)#interface Ethernet 0/2
IOU1(config-if)#switchport mode access
IOU1(config-if)#switchport access vlan 10
IOU1(config-if)#exit
IOU1(config)#interface Ethernet 0/3
IOU1(config-if)#switchport mode access
IOU1(config-if)#switchport access vlan 20
IOU1(config-if)#exit
IOU1(config)#exit
IOU1#show
*Dec 16 13:04:24.592: %SYS-5-CONFIG_I: Configured from console by console
IOU1#show vlan br

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Et0/0, Et0/1, Et1/0, Et1/1
                                                Et1/2, Et1/3, Et2/0, Et2/1
                                                Et2/2, Et2/3, Et3/0, Et3/1
                                                Et3/2, Et3/3
10   admins                           active    Et0/2
20   guests                           active    Et0/3
1002 fddi-default                     act/unsup
1003 token-ring-default               act/unsup
1004 fddinet-default                  act/unsup
1005 trnet-default                    act/unsup

R1(config)#interface FastEthernet 0/1.10
R1(config-subif)#encapsulation dot1Q 10
R1(config-subif)#ip address 10.3.1.254 255.255.255.0
R1(config-subif)#exit
R1(config)#interface FastEthernet 0/1.20
R1(config-subif)#encapsulation dot1Q 20
R1(config-subif)#ip address 10.3.2.254 255.255.255.0
R1(config-subif)#exit
R1(config)#interface FastEthernet 0/1.30
R1(config-subif)#encapsulation dot1Q 20

%Configuration of multiple subinterfaces of the same main
interface with the same VID (20) is not permitted.
This VID is already configured on FastEthernet0/1.20.

R1(config-subif)#encapsulation dot1Q 30
R1(config-subif)#ip address 10.3.3.254 255.255.255.0
R1(config-subif)#exit
R1(config)#exit
R1#conf
*Mar  1 00:06:40.103: %SYS-5-CONFIG_I: Configured from console by console
R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#interface FastEthernet 0/1
R1(config-if)#no shut
R1(config-if)#exit
R1(config)#
*Mar  1 00:07:00.963: %LINK-3-UPDOWN: Interface FastEthernet0/1, changed state to up
*Mar  1 00:07:01.963: %LINEPROTO-5-UPDOWN: Line protocol on Interface FastEthernet0/1, changed state to up
R1(config)#exit
R1#show
*Mar  1 00:07:03.179: %SYS-5-CONFIG_I: Configured from console by console
R1#show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
FastEthernet0/0            192.168.122.199 YES DHCP   up                    up  
FastEthernet0/1            unassigned      YES unset  up                    up  
FastEthernet0/1.10         10.3.1.254      YES manual up                    up  
FastEthernet0/1.20         10.3.2.254      YES manual up                    up  
FastEthernet0/1.30         10.3.3.254      YES manual up                    up  
FastEthernet1/0            unassigned      YES unset  administratively down down
FastEthernet2/0            unassigned      YES unset  administratively down down




IOU1(config)#interface Ethernet 0/0
IOU1(config-if)#switchport trunk encapsulation dot1Q
IOU1(config-if)#switchport mode trunk
IOU1(config-if)#
*Dec 16 13:28:47.888: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/0, changed state to down
IOU1(config-if)#switchport trunk
*Dec 16 13:28:50.888: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/0, changed state to up
IOU1(config-if)#switchport trunk allowed vlan add 10,20,30
*Dec 16 13:29:02.435: %CDP-4-DUPLEX_MISMATCH: duplex mismatch discovered on Ethernet0/0 (not half duplex), with R1 FastEthernet0/1 (half duplex).
IOU1(config-if)#switchport trunk allowed vlan add 10,20,30
IOU1(config-if)#exit
IOU1(config)#exit
IOU1#
*Dec 16 13:29:16.113: %SYS-5-CONFIG_I: Configured from console by console

IOU1(config)#vlan 30
IOU1(config-vlan)#name enplus
IOU1(config-vlan)#exit
IOU1#show interface trunk

Port        Mode             Encapsulation  Status        Native vlan
Et0/0       on               802.1q         trunking      1

Port        Vlans allowed on trunk
Et0/0       1-4094

Port        Vlans allowed and active in management domain
Et0/0       1,10,20,30

Port        Vlans in spanning tree forwarding state and not pruned
Et0/0       1,10,20
IOU1#


IOU1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
IOU1(config)#interface Ethernet 0/1
IOU1(config-if)#
*Dec 16 13:37:33.820: %CDP-4-DUPLEX_MISMATCH: duplex mismatch discovered on Ethernet0/0 (not half duplex), with R1 FastEthernet0/1 (half duplex).
IOU1(config-if)#switchport trunk encapluslation dot1Q
                                      ^
% Invalid input detected at '^' marker.

IOU1(config-if)#switchport trunk encapsulation dot1Q
IOU1(config-if)#switchport mode trunk
IOU1(config-if)#switchport trunk mode allowed
*Dec 16 13:38:37.279: %CDP-4-DUPLEX_MISMATCH: duplex mismatch discovered on Ethernet0/0 (not half duplex), with R1 FastEthernet0/1 (half duplex).
IOU1(config-if)#switchport trunk mode allowed vlan 10?
% Unrecognized command
IOU1(config-if)#switchport trunk mode allowed vlan 10,20,30
                                 ^
% Invalid input detected at '^' marker.

IOU1(config-if)#switchport trunk allowed vlan 10,20,30
IOU1(config-if)#exit
IOU1(config)#exit
IOU1#show
*Dec 16 13:38:57.630: %SYS-5-CONFIG_I: Configured from console by console
IOU1#show int trunk

Port        Mode             Encapsulation  Status        Native vlan
Et0/0       on               802.1q         trunking      1
Et0/1       on               802.1q         trunking      1

Port        Vlans allowed on trunk
Et0/0       1-4094
Et0/1       10,20,30

Port        Vlans allowed and active in management domain
Et0/0       1,10,20,30
Et0/1       10,20,30

Port        Vlans in spanning tree forwarding state and not pruned
Et0/0       1,10,20,30
Et0/1       10,20,30
IOU1#

IOU2(config)#vlan 10
IOU2(config-vlan)#name admins
IOU2(config-vlan)#exit
IOU2(config)#vlan 20
IOU2(config-vlan)#name guest
IOU2(config-vlan)#exit
IOU2(config)#vlan 30
IOU2(config-vlan)#name enplus
IOU2(config-vlan)#exit
IOU2(config)#interface Ethernet 0/0
IOU2(config-if)#switchport mode trunk
Command rejected: An interface whose trunk encapsulation is "Auto" can not be configured to "trunk" mode.
IOU2(config-if)#switchport trunk encapsulation dot1Q
IOU2(config-if)#switchport trunk allowed vlan add 10,20,30
IOU2(config-if)#exit
IOU2(config)#exit
IOU2#
*Dec 16 13:41:14.278: %SYS-5-CONFIG_I: Configured from console by console
IOU2#show int trun

Port        Mode             Encapsulation  Status        Native vlan
Et0/0       auto             802.1q         trunking      1

Port        Vlans allowed on trunk
Et0/0       1-4094

Port        Vlans allowed and active in management domain
Et0/0       1,10,20,30

Port        Vlans in spanning tree forwarding state and not pruned
Et0/0       1,10,20,30
IOU2#


IOU2#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
IOU2(config)#interface Ethernet 0/1
IOU2(config-if)#switchport mode access
IOU2(config-if)#switchport access vlan 10
IOU2(config-if)#exit
IOU2(config)#interface Ethernet 0/2
IOU2(config-if)#switchport mode access
IOU2(config-if)#switchport access vlan 20
IOU2(config-if)#exit
IOU2(config)#exit
IOU2#show
*Dec 16 13:43:33.302: %SYS-5-CONFIG_I: Configured from console by console
IOU2#show vlan br

VLAN Name                             Status    Ports
---- -------------------------------- --------- -------------------------------
1    default                          active    Et0/3, Et1/0, Et1/1, Et1/2
                                                Et1/3, Et2/0, Et2/1, Et2/2
                                                Et2/3, Et3/0, Et3/1, Et3/2
                                                Et3/3
10   admins                           active    Et0/1
20   guest                            active    Et0/2
30   enplus                           active
1002 fddi-default                     act/unsup
1003 token-ring-default               act/unsup
1004 fddinet-default                  act/unsup
1005 trnet-default                    act/unsup
IOU2#


PC1> ping 10.3.1.2

84 bytes from 10.3.1.2 icmp_seq=1 ttl=64 time=6.965 ms
84 bytes from 10.3.1.2 icmp_seq=2 ttl=64 time=6.424 ms
84 bytes from 10.3.1.2 icmp_seq=3 ttl=64 time=5.307 ms
^C
PC1>

on modifie les conf de vpcs et ajoute une route
PC1> ping 10.3.2.1

84 bytes from 10.3.2.1 icmp_seq=1 ttl=63 time=19.350 ms
84 bytes from 10.3.2.1 icmp_seq=2 ttl=63 time=18.237 ms

R1(config)#interface FastEthernet 0/1.10
R1(config-subif)#ip nat inside

*Mar  1 00:03:41.283: %LINEPROTO-5-UPDOWN: Line protocol on Interface NVI0, changed state to up
R1(config-subif)#
*Mar  1 00:03:48.203: %SYS-3-CPUHOG: Task is running for (2044)msecs, more than (2000)msecs (0/0),process = Exec.
-Traceback= 0x61F80240 0x61F478D0 0x61F47B90 0x61F47CB4 0x61F47CB4 0x61F48B84 0x61F7B9D4 0x61F87BCC 0x61F71FC4 0x61F72C28 0x61F73B78 0x6177395C 0x61165B10 0x61181DD4 0x6214B2AC 0x6214B290
*Mar  1 00:03:48.615: %SYS-3-CPUYLD: Task ran for (2456)msecs, more than (2000)msecs (0/0),process = Exec
R1(config-subif)#exit
R1(config)#interface FastEthernet 0/1.20
R1(config-subif)#ip nat inside
R1(config-subif)#exit
R1(config)#interface FastEthernet 0/1.30
R1(config-subif)#ip nat inside
R1(config-subif)#exit
R1(config)#access-list 1 permit any
R1(config)#ip nat inside source list 1 interface FastEthernet 0/0 overload
R1(config)#interface FastEthernet 0/0
R1(config-if)#ip nat outside
R1(config-if)#exit

PC1> ping 1.1.1.1

84 bytes from 1.1.1.1 icmp_seq=1 ttl=57 time=41.533 ms
84 bytes from 1.1.1.1 icmp_seq=2 ttl=57 time=40.309 ms
84 bytes from 1.1.1.1 icmp_seq=3 ttl=57 time=46.051 ms
84 bytes from 1.1.1.1 icmp_seq=4 ttl=57 time=41.123 ms
84 bytes from 1.1.1.1 icmp_seq=5 ttl=57 time=37.057 ms


### Partie III


apres avoir bien conf le serv dhcp ( comme dhab )
PC4> show ip

NAME        : PC4[1]
IP/MASK     : 0.0.0.0/0
GATEWAY     : 0.0.0.0
DNS         :
MAC         : 00:50:79:66:68:03
LPORT       : 20026
RHOST:PORT  : 127.0.0.1:20027
MTU         : 1500

PC4> ip dhcp
DDORA IP 10.3.2.10/24 GW 10.3.2.254

PC4> show ip

NAME        : PC4[1]
IP/MASK     : 10.3.2.10/24
GATEWAY     : 10.3.2.254
DNS         : 1.1.1.1
DHCP SERVER : 10.3.2.253
DHCP LEASE  : 3594, 3600/1800/3150
MAC         : 00:50:79:66:68:03
LPORT       : 20026
RHOST:PORT  : 127.0.0.1:20027
MTU         : 1500


PC4> ping efrei.fr
efrei.fr resolved to 51.255.68.208

84 bytes from 51.255.68.208 icmp_seq=1 ttl=49 time=50.062 ms
84 bytes from 51.255.68.208 icmp_seq=2 ttl=49 time=50.448 ms
84 bytes from 51.255.68.208 icmp_seq=3 ttl=49 time=43.706 ms
84 bytes from 51.255.68.208 icmp_seq=4 ttl=49 time=49.855 ms


PC4> ip dhcp
DORA IP 10.3.2.10/24 GW 10.3.2.254



PC4> show ip

NAME        : PC4[1]
IP/MASK     : 10.3.2.10/24
GATEWAY     : 10.3.2.254
DNS         : 10.3.3.1
DHCP SERVER : 10.3.2.253
DHCP LEASE  : 2682, 3600/1800/3150
MAC         : 00:50:79:66:68:03
LPORT       : 20021
RHOST:PORT  : 127.0.0.1:20022
MTU         : 1500



apres moulte peripetie

PC4> ping dns.tp3.b2
dns.tp3.b2 resolved to 10.3.3.1

84 bytes from 10.3.3.1 icmp_seq=1 ttl=63 time=22.576 ms
84 bytes from 10.3.3.1 icmp_seq=2 ttl=63 time=16.156 ms
84 bytes from 10.3.3.1 icmp_seq=3 ttl=63 time=19.775 ms
84 bytes from 10.3.3.1 icmp_seq=4 ttl=63 time=22.510 ms
84 bytes from 10.3.3.1 icmp_seq=5 ttl=63 time=22.680 ms

PC4> ping efrei.fr
efrei.fr resolved to 51.255.68.208

84 bytes from 51.255.68.208 icmp_seq=1 ttl=53 time=62.301 ms
84 bytes from 51.255.68.208 icmp_seq=2 ttl=53 time=55.514 ms
84 bytes from 51.255.68.208 icmp_seq=3 ttl=53 time=52.567 ms
84 bytes from 51.255.68.208 icmp_seq=4 ttl=53 time=41.024 ms
^C



[root@localhost ~]# curl http://web.tp3.b2
<!doctype html>
<html>
  <head>
    <meta charset='utf-8'>
    <meta name='viewport' content='width=device-width, initial-scale=1'>
    <title>HTTP Server Test Page powered by: Rocky Linux</title>
    <style type="text/css">
      /*<![CDATA[*/

      html {
        height: 100%;
        width: 100%;
      }
        body {
  background: rgb(20,72,50);
  background: -moz-linear-gradient(180deg, rgba(23,43,70,1) 30%, rgba(0,0,0,1) 90%)  ;
  background: -webkit-linear-gradient(180deg, rgba(23,43,70,1) 30%, rgba(0,0,0,1) 90%) ;
  background: linear-gradient(180deg, rgba(23,43,70,1) 30%, rgba(0,0,0,1) 90%);
  background-repeat: no-repeat;
  background-attachment: fixed;
  filter: progid:DXImageTransform.Microsoft.gradient(startColorstr="#3c6eb4",endColorstr="#3c95b4",GradientType=1);
        color: white;
        font-size: 0.9em;
        font-weight: 400;
        font-family: 'Montserrat', sans-serif;
        margin: 0;
        padding: 10em 6em 10em 6em;
        box-sizing: border-box;

      }


  h1 {
    text-align: center;
    margin: 0;
    padding: 0.6em 2em 0.4em;
    color: #fff;
    font-weight: bold;
    font-family: 'Montserrat', sans-serif;
    font-size: 2em;
  }
  h1 strong {
    font-weight: bolder;
    font-family: 'Montserrat', sans-serif;
  }
  h2 {
    font-size: 1.5em;
    font-weight:bold;
  }

  .title {
    border: 1px solid black;
    font-weight: bold;
    position: relative;
    float: right;
    width: 150px;
    text-align: center;
    padding: 10px 0 10px 0;
    margin-top: 0;
  }

  .description {
    padding: 45px 10px 5px 10px;
    clear: right;
    padding: 15px;
  }

  .section {
    padding-left: 3%;
   margin-bottom: 10px;
  }

  img {

    padding: 2px;
    margin: 2px;
  }
  a:hover img {
    padding: 2px;
    margin: 2px;
  }

  :link {
    color: rgb(199, 252, 77);
    text-shadow:
  }
  :visited {
    color: rgb(122, 206, 255);
  }
  a:hover {
    color: rgb(16, 44, 122);
  }
  .row {
    width: 100%;
    padding: 0 10px 0 10px;
  }

  footer {
    padding-top: 6em;
    margin-bottom: 6em;
    text-align: center;
    font-size: xx-small;
    overflow:hidden;
    clear: both;
  }

  .summary {
    font-size: 140%;
    text-align: center;
  }

  #rocky-poweredby img {
    margin-left: -10px;
  }

  #logos img {
    vertical-align: top;
  }

  /* Desktop  View Options */

  @media (min-width: 768px)  {

    body {
      padding: 10em 20% !important;
    }

    .col-md-1, .col-md-2, .col-md-3, .col-md-4, .col-md-5, .col-md-6,
    .col-md-7, .col-md-8, .col-md-9, .col-md-10, .col-md-11, .col-md-12 {
      float: left;
    }

    .col-md-1 {
      width: 8.33%;
    }
    .col-md-2 {
      width: 16.66%;
    }
    .col-md-3 {
      width: 25%;
    }
    .col-md-4 {
      width: 33%;
    }
    .col-md-5 {
      width: 41.66%;
    }
    .col-md-6 {
      border-left:3px ;
      width: 50%;


    }
    .col-md-7 {
      width: 58.33%;
    }
    .col-md-8 {
      width: 66.66%;
    }
    .col-md-9 {
      width: 74.99%;
    }
    .col-md-10 {
      width: 83.33%;
    }
    .col-md-11 {
      width: 91.66%;
    }
    .col-md-12 {
      width: 100%;
    }
  }

  /* Mobile View Options */
  @media (max-width: 767px) {
    .col-sm-1, .col-sm-2, .col-sm-3, .col-sm-4, .col-sm-5, .col-sm-6,
    .col-sm-7, .col-sm-8, .col-sm-9, .col-sm-10, .col-sm-11, .col-sm-12 {
      float: left;
    }

    .col-sm-1 {
      width: 8.33%;
    }
    .col-sm-2 {
      width: 16.66%;
    }
    .col-sm-3 {
      width: 25%;
    }
    .col-sm-4 {
      width: 33%;
    }
    .col-sm-5 {
      width: 41.66%;
    }
    .col-sm-6 {
      width: 50%;
    }
    .col-sm-7 {
      width: 58.33%;
    }
    .col-sm-8 {
      width: 66.66%;
    }
    .col-sm-9 {
      width: 74.99%;
    }
    .col-sm-10 {
      width: 83.33%;
    }
    .col-sm-11 {
      width: 91.66%;
    }
    .col-sm-12 {
      width: 100%;
    }
    h1 {
      padding: 0 !important;
    }
  }


  </style>
  </head>
  <body>
    <h1>HTTP Server <strong>Test Page</strong></h1>

    <div class='row'>

      <div class='col-sm-12 col-md-6 col-md-6 '></div>
          <p class="summary">This page is used to test the proper operation of
            an HTTP server after it has been installed on a Rocky Linux system.
            If you can read this page, it means that the software is working
            correctly.</p>
      </div>

      <div class='col-sm-12 col-md-6 col-md-6 col-md-offset-12'>


        <div class='section'>
          <h2>Just visiting?</h2>

          <p>This website you are visiting is either experiencing problems or
          could be going through maintenance.</p>

          <p>If you would like the let the administrators of this website know
          that you've seen this page instead of the page you've expected, you
          should send them an email. In general, mail sent to the name
          "webmaster" and directed to the website's domain should reach the
          appropriate person.</p>

          <p>The most common email address to send to is:
          <strong>"webmaster@example.com"</strong></p>

          <h2>Note:</h2>
          <p>The Rocky Linux distribution is a stable and reproduceable platform
          based on the sources of Red Hat Enterprise Linux (RHEL). With this in
          mind, please understand that:

        <ul>
          <li>Neither the <strong>Rocky Linux Project</strong> nor the
          <strong>Rocky Enterprise Software Foundation</strong> have anything to
          do with this website or its content.</li>
          <li>The Rocky Linux Project nor the <strong>RESF</strong> have
          "hacked" this webserver: This test page is included with the
          distribution.</li>
        </ul>
        <p>For more information about Rocky Linux, please visit the
          <a href="https://rockylinux.org/"><strong>Rocky Linux
          website</strong></a>.
        </p>
        </div>
      </div>
      <div class='col-sm-12 col-md-6 col-md-6 col-md-offset-12'>
        <div class='section'>

          <h2>I am the admin, what do I do?</h2>

        <p>You may now add content to the webroot directory for your
        software.</p>

        <p><strong>For systems using the
        <a href="https://httpd.apache.org/">Apache Webserver</strong></a>:
        You can add content to the directory <code>/var/www/html/</code>.
        Until you do so, people visiting your website will see this page. If
        you would like this page to not be shown, follow the instructions in:
        <code>/etc/httpd/conf.d/welcome.conf</code>.</p>

        <p><strong>For systems using
        <a href="https://nginx.org">Nginx</strong></a>:
        You can add your content in a location of your
        choice and edit the <code>root</code> configuration directive
        in <code>/etc/nginx/nginx.conf</code>.</p>

        <div id="logos">
          <a href="https://rockylinux.org/" id="rocky-poweredby"><img src="icons/poweredby.png" alt="[ Powered by Rocky Linux ]" /></a> <!-- Rocky -->
          <img src="poweredby.png" /> <!-- webserver -->
        </div>
      </div>
      </div>

      <footer class="col-sm-12">
      <a href="https://apache.org">Apache&trade;</a> is a registered trademark of <a href="https://apache.org">the Apache Software Foundation</a> in the United States and/or other countries.<br />
      <a href="https://nginx.org">NGINX&trade;</a> is a registered trademark of <a href="https://">F5 Networks, Inc.</a>.
      </footer>

  </body>
</html>
[root@localhost ~]#
