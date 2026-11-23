1.1

r1 - Client and attacker router
r2 - Main router
r3 - Branch client router
Client 1 - End user
Attacker - Security tester
web1 - Server
db1 - Database server for web1?
branch-client - non lan end client
ansible - Used for managing network devices etc
Prometheus - Useful for reading live statistics and comparing them on graphs etc
Grafana - Data visualization and can be used to display metrics
Zabbix - Infrastructure manager

1.2

https://viewer.diagrams.net/?tags=%7B%7D&lightbox=1&highlight=0000ff&edit=_blank&layers=1&nav=1&dark=auto#R%3Cmxfile%3E%3Cdiagram%20name%3D%22Page-1%22%20id%3D%223EL1Dw3B7aLPPR80P6Mq%22%3E5VvbduMmFP0aP2aWAV0fM05mulYvK2vy0GnfsEUstbJwEb7164tisASaOFgWsuO%2BJOIIjsU%2B%2B%2BwDWB6hyWL7leFl%2BitNSD6C42Q7Qg8jCCMUiL%2BVYbc3ABCjvWXOskTaasNz9i%2BRxrG0rrKElFpHTmnOs6VunNGiIDOu2TBjdKN3e6G5%2FqlLPCctw%2FMM523r71nCUzkvGNb2n0g2T9UngyDe31lg1VnOpExxQjcNE3ocoQmjlO%2BvFtsJySvwFC77cV%2FeuHt4MEYKbjPgW%2FmbV%2Fz8bfH4zz1M8dqfxN7DnQwPSVoo1G6lqaQrNiNHfKl%2BfKfAq9w%2By2ZBC%2FHv82zF1qR6IiAajK6K5LU1Fi3KeErntMD5L5QuZZe%2FCOc7SQu84lSYUr7I5V2yzfh3Oby6%2FqO6%2FuTL1sO2cethJxsvtODSIRBB%2BFxyzJQhqjoXid66r2hUz0BYvmR5Lr1JSmI2J%2FwINvAQcJEphC4IZzsxjpEc82ytY48lZeeHfnVUxYUM7AlBDm8jyOCEIIt5sd33ZqMxqmrWw15bFyUHuiQ5jnChEeM8F4JbTXCTZpw8L%2FErSTZC8%2FVY4XK5V%2BGXbFvFXEKwxvlKsQpKE2GcbBsf2AYgbQhrJFV00xBhaZJOvFC2ZalBARThdgMaHBo04Ag0BIcDDQ0M2mK%2B4HfTpSPkAuANhhxAJyj4xZU57CTN1yjM51ZtOfSJZiJIdc6NjZxTbeViX4TlKIM6h8c4g03eR2JTFzKB%2Fw%2BZoFH1vCg0ZcgxnVQFOc4enR3vaHtLyu85x7O%2FCeuk5UFbywHUxRxEOorQH78diPNWDla5dh5akzwTvrstGWzACgzKBc7AslpnnQfWn3g6zbausDocFChiucPKanl1ZhoWZTYVrlyBhczFqDOwOpbAViVooKVDe1qJ0Qpp172rbR2Crbi%2BHz2lhz%2BsVo2QHtPNHxewwJBeFNqthlqOQpM90HC0R8ZdHezzLA1dinsDnrXY8hVdFV9DoNPMt1y9tx2ZZdR8Ftd8Dd%2BmZ18F4yvDL7jAnQoGADbldbClSOQerSdWPWxKVqUzwEJfBywAzgCLb0gOx5%2BiKNQPOcT8XIhi5eSJsEwEQWx3ThPK8LqE0tQ3JeSnCmUUB7ojk7OOhVKtK26EySGCGpNjMDSTr4SgAfD1So6ijpXcFFUEhyXoANvkDZk6O1DwPR0%2F4KwooQE2yYk7oJAJlLn27A%2BoUzbI72med%2FmddK1WNufDDbH0m1p5VCctq7RK1isRQd%2FYNQdex%2B2Mb%2Bzj%2FXjgKu33WaUvX6abxANHiddgOdRo%2Ft53apaMVel7a4z1Yt0RigZmbGBTjPp8i0CdpPT%2B6oWZ%2B8624WqJ5updpo%2BQ5C5yXHHx1nL84lUptsnx8xacU4aLWXo3e%2F3Wr1OGWyw9PWM3H5qn672luAp1P4U8uFSOd8zXLtpgm%2BPxdeW4cZAemC4%2BSo57R%2FjZV46XbN31VTab5DbkFiJnyQ1voX6fva3sfVd5bWt08xW368tt0ax%2Fe7HvXv%2BCBT3%2BBw%3D%3D%3C%2Fdiagram%3E%3C%2Fmxfile%3E

1.3

10.10.10.0/24	Käyttäjäverkko	r1: 10.10.10.1 ja 10.10.10.254 | Verkossa on käyttäjät
10.10.20.0/24	Palvelinverkko	r2: 10.10.20.1 | Verkossa on palvelimet ja niiden databaset
10.10.30.0/24	Haaratoimiston verkko	r3: 10.10.30.1 | Branch-Client yms
10.10.99.0/24	Erillinen hallintapalveluiden LAN	r2: 10.10.99.1 | Siellä pyörii hallintaohjelmat yms
10.255.12.0/30	Reitittimien r1–r2 välinen linkki	r1: 10.255.12.1, r2: 10.255.12.2 | silta
10.255.23.0/30	Reitittimien r2–r3 välinen linkki	r2: 10.255.23.1, r3: 10.255.23.2 | silta

1.4

Kaikiin muihin toimii, paitsi hallintapalveluihin.
Reitti kulkee R1 -> R2 ja siitä eteenmpäin kaikkialle muualle kuin hallintapalveluihin.

root@client1:/# ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
73: eth0@if74: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default
    link/ether 02:42:ac:14:14:0b brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet 172.20.20.11/24 brd 172.20.20.255 scope global eth0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:acff:fe14:140b/64 scope link
       valid_lft forever preferred_lft forever
99: eth1@if100: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 9500 qdisc noqueue state UP group default
    link/ether aa:c1:ab:39:02:fb brd ff:ff:ff:ff:ff:ff link-netnsid 1
    altname clab-o-05031180f95d8850
    inet 10.10.10.101/24 scope global eth1
       valid_lft forever preferred_lft forever
    inet6 fe80::a8c1:abff:fe39:2fb/64 scope link
       valid_lft forever preferred_lft forever
root@client1:/# ip route
default via 10.10.10.1 dev eth1
10.10.10.0/24 dev eth1 proto kernel scope link src 10.10.10.101
172.20.20.0/24 dev eth0 proto kernel scope link src 172.20.20.11
root@client1:/# ^C
root@client1:/# ip route
default via 10.10.10.1 dev eth1
10.10.10.0/24 dev eth1 proto kernel scope link src 10.10.10.101
172.20.20.0/24 dev eth0 proto kernel scope link src 172.20.20.11
root@client1:/# ping -c 4 10.10.30.101
PING 10.10.30.101 (10.10.30.101) 56(84) bytes of data.
64 bytes from 10.10.30.101: icmp_seq=1 ttl=61 time=1.26 ms
64 bytes from 10.10.30.101: icmp_seq=2 ttl=61 time=0.248 ms
64 bytes from 10.10.30.101: icmp_seq=3 ttl=61 time=0.246 ms
64 bytes from 10.10.30.101: icmp_seq=4 ttl=61 time=0.120 ms

--- 10.10.30.101 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.120/0.467/1.256/0.458 ms
root@client1:/# ping -c 4 10.10.20.101
PING 10.10.20.101 (10.10.20.101) 56(84) bytes of data.
64 bytes from 10.10.20.101: icmp_seq=1 ttl=62 time=0.390 ms
64 bytes from 10.10.20.101: icmp_seq=2 ttl=62 time=0.191 ms
64 bytes from 10.10.20.101: icmp_seq=3 ttl=62 time=0.171 ms
64 bytes from 10.10.20.101: icmp_seq=4 ttl=62 time=0.518 ms

--- 10.10.20.101 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.171/0.317/0.518/0.143 ms
root@client1:/# traceroute 10.10.30.101
traceroute to 10.10.30.101 (10.10.30.101), 30 hops max, 60 byte packets

 1  10.10.10.1 (10.10.10.1)  1.095 ms  0.801 ms  0.781 ms
 2  10.255.12.2 (10.255.12.2)  0.769 ms  0.637 ms  0.618 ms
 3  10.255.23.2 (10.255.23.2)  0.599 ms  0.468 ms  0.443 ms
 4  10.10.30.101 (10.10.30.101)  0.381 ms  0.302 ms  0.231 ms
