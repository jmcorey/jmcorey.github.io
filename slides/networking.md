# BASIC NETWORKING INTRODUCTION SLIDES

-----

## A network is a graph

### Nodes and edges...

![big bad network](https://www.xkl.com/wp-content/uploads/2015/09/networkDesign.jpg)

-----

## "an internet"

![x](https://c2.staticflickr.com/4/3878/15074300456_ffa071b2f4_b.jpg)

-----

## Undersea Fiber Optics

![x](https://upload.wikimedia.org/wikipedia/commons/a/aa/Network_Map.png)

-----

## Also wireless

![x](https://upload.wikimedia.org/wikipedia/commons/8/83/Wireless_mesh_network_diagram.jpg)

-----

## The Internet

![x](https://upload.wikimedia.org/wikipedia/en/thumb/4/4b/Internet_map_4096.GIF/768px-Internet_map_4096.GIF)

-----
## IPv4 addresses

* 4 byte address, which allows for delivering packets, for example:
* 7.254.27.130  (some computer at MIT)<!-- .element: class="fragment" -->
* 7.0.0.0/8  (shorthand--all 16 million addresses at MIT)<!-- .element: class="fragment" -->
* 9.0.0.0/8  (shorthand--all 16 million addresses at IBM)<!-- .element: class="fragment" -->
* 10.0.0.0/8  (a private/local address space--not internet routed)<!-- .element: class="fragment" -->
* X.0.0.0/8  (a Class A subnet -- first 8 bits specified, last 24 free to vary)<!-- .element: class="fragment" -->
* X.Y.0.0/16  (a Class B subnet -- first 16 bits specified -> 65536 addresses)<!-- .element: class="fragment" -->
* X.Y.Z.0/24  (a Class C subnet -- first 24 bits specified -> 256 addresses)<!-- .element: class="fragment" -->
* 50.54.141.94  (neniam.net)<!-- .element: class="fragment" -->
* 127.0.0.0/8  (is all localhost, only the first 8 bits matter)<!-- .element: class="fragment" -->
* 192.168.0.0/16  (another private address range)<!-- .element: class="fragment" -->
* 192.168.255.255  (broadcast address)<!-- .element: class="fragment" -->
* 50.54.171.127  (broadcast address for 50.54.171.94/26)<!-- .element: class="fragment" -->
* 224.0.0.0/4  (IP multicast addresses)<!-- .element: class="fragment" -->

-----

## CIDR

![x](https://s-media-cache-ak0.pinimg.com/originals/cf/94/5b/cf945bdaf28ed2b40923f9df980e4948.png)

-----

## CIDR and subnet masks

![x](http://www.2000trainers.com/aimg/article346-71-image006.jpg)

-----

## Hostname translation

```
% host tripplanner.kingcounty.gov
tripplanner.kingcounty.gov has address 146.129.240.238

% host 146.129.240.238
238.240.129.146.in-addr.arpa domain name pointer tripplanner.kingcounty.gov.
238.240.129.146.in-addr.arpa domain name pointer tripplanner2.kingcounty.gov.

% host neniam.net
neniam.net has address 50.54.141.94

% host 50.54.141.94
94.141.54.50.in-addr.arpa domain name pointer
50-54-141-94.evrt.wa.frontiernet.net.
```

-----

## Not just IPv4...

```
% host www.youtube.com
www.youtube.com is an alias for youtube-ui.l.google.com.
youtube-ui.l.google.com has address 216.58.216.174
youtube-ui.l.google.com has IPv6 address 2607:f8b0:400a:808::200e

% host maps.google.com
maps.google.com has address 172.217.3.174
maps.google.com has IPv6 address 2607:f8b0:400a:808::200e

% host www.wikipedia.org
www.wikipedia.org has address 198.35.26.96
www.wikipedia.org has IPv6 address 2620:0:863:ed1a::1

```

-----

## IPv6 Addresses

#### (because IPv4 addresses are pretty much used up)

![x](https://upload.wikimedia.org/wikipedia/commons/thumb/1/15/Ipv6_address.svg/1024px-Ipv6_address.svg.png)

-----

## IP packets

#### Can travel over different types of networks

![x](http://www.mathcs.emory.edu/~cheung/Courses/455/Syllabus/4b-internet/FIGS/IP-over-pigeons.gif)

-----

## What's my address?

```
% ifconfig

enp6s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.16  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::7e29:848c:79c7:ba0e  prefixlen 64  scopeid 0x20<link>
        ether 00:25:90:72:3c:72  txqueuelen 1000  (Ethernet)

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
```

-----

## Packet delivery may not be reliable

![x](http://www.mathcs.emory.edu/~cheung/Courses/455/Syllabus/4b-internet/FIGS/datagram4.gif)

-----

## Ping Command

```
% ping 50.54.141.94
PING 50.54.141.94 (50.54.141.94) 56(84) bytes of data.
64 bytes from 50.54.141.94: icmp_seq=1 ttl=64 time=0.722 ms
64 bytes from 50.54.141.94: icmp_seq=2 ttl=64 time=0.726 ms
64 bytes from 50.54.141.94: icmp_seq=3 ttl=64 time=0.695 ms
64 bytes from 50.54.141.94: icmp_seq=4 ttl=64 time=0.720 ms
64 bytes from 50.54.141.94: icmp_seq=5 ttl=64 time=0.699 ms
^C
--- 50.54.141.94 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4098ms
rtt min/avg/max/mdev = 0.695/0.712/0.726/0.027 ms
```

-----

## IPv4 Packet Header

```
    0                   1                   2                   3
    0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1 2 3 4 5 6 7 8 9 0 1
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |Version|  IHL  |Type of Service|          Total Length         |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |         Identification        |Flags|      Fragment Offset    |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |  Time to Live |    Protocol   |         Header Checksum       |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |                       Source Address                          |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |                    Destination Address                        |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
   |                    Options                    |    Padding    |
   +-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

-----

## DATAGRAMS (UDP) VS STREAMS (TCP)

![x](img/udptcp.png)

-----

## TCP PROTOCOL

![x](http://intronetworks.cs.luc.edu/1/html/_images/tcp_ladder_states.png)

-----

## TCP COPES WITH LOSS

![x](img/tcpseq.png)

-----

## TCP vs UDP

| TCP | UDP |
| --- | --- |
| Connection Setup and Acks | No Persistent Connection |
| Sequential Reliable Stream | Best-Effort Datagram (thin wrapper over IPv4) |
| Flow Control | Drop on the floor |

-----

## TCP and UDP headers

![x](http://microchip.wikidot.com/local--files/tcpip:tcp-vs-udp/TCP_UDP_headers.JPG)

-----

## Network layers

![x](http://www.cellbiol.com/bioinformatics_web_development/wp-content/uploads/2017/01/tpc-ip-and-osi-model-cellbiol.com_.png)

-----

## Header wrapping

![x](http://www.cellbiol.com/bioinformatics_web_development/wp-content/uploads/2017/01/the_encapsulated_structure_of_tcp_ip_packets_cellbiol.com_-1-1024x938.png)

-----

## Tcpdump and Netcat

Host A sends:

```
% echo uh | nc -u 192.168.1.255 5001
```

Host B dumps packets:

```
% # tcpdump -v -n -nn -x -i enp6s0 port 5001
tcpdump: listening on enp6s0, link-type EN10MB (Ethernet), capture size 262144 bytes
18:55:42.218277 IP (tos 0x0, ttl 64, id 64952, offset 0, flags [DF], proto UDP (17), length 31)
    192.168.1.14.60930 > 192.168.1.255.5001: UDP, length 3
	0x0000:  4500 001f fdb8 4000 4011 b8b7 c0a8 010e
	0x0010:  c0a8 01ff ee02 1389 000b fa85 7568 0a00
	0x0020:  0000 0000 0000 0000 0000 0000 0000
```
