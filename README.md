TP4-CCNA1

## A. Manip 1
Sur `client1`

   - afficher la table ARP
    
    10.1.0.1 dev enp0s8 lladdr 0a:00:27:00:00:07 REACHABLE

 #### Expliquer la seul ligne visible 
 - Cette ligne signifie la connexion entre l'hôte (mon pc) et la VM client1. Cet connexion provient du fait que je sois connecter en SSH sur la VM. 

sur `server1`

   - afficher la table ARP
  

    10.2.0.1 dev enp0s8 lladdr 0a:00:27:00:00:04 REACHABLE

 #### Expliquer la seul ligne visible 
 - Cette ligne signifie la connexion entre l'hôte (mon pc) et la VM serveur1. Cet connexion provient du fait que je sois connecter en SSH sur la VM. 

---

    [root@client1 hugo]# ping server1.tp4
    PING server1.tp4 (10.2.0.10) 56(84) bytes of data.
    64 bytes from server1.tp4 (10.2.0.10): icmp_seq=1 ttl=63 time=1.24 ms
    64 bytes from server1.tp4 (10.2.0.10): icmp_seq=2 ttl=63 time=1.40 ms
    64 bytes from server1.tp4 (10.2.0.10): icmp_seq=3 ttl=63 time=1.25 ms
    
    --- server1.tp4 ping statistics ---
    3 packets transmitted, 3 received, 0% packet loss, time 2019ms
    rtt min/avg/max/mdev = 1.243/1.300/1.403/0.078 ms
    [root@client1 hugo]# ip neigh show
    10.1.0.1 dev enp0s8 lladdr 0a:00:27:00:00:07 REACHABLE
    10.1.0.254 dev enp0s8 lladdr 08:00:27:9c:39:75 REACHABLE

#### Expliquer le changement :

- Maintenant que j'ai ping le server1, on peut voir l'ip du router s'affichait `10.1.0.254`.

---

    [root@server1 hugo]# ip neigh show
    10.2.0.254 dev enp0s8 lladdr 08:00:27:25:24:67 REACHABLE
    10.2.0.1 dev enp0s8 lladdr 0a:00:27:00:00:04 REACHABLE

##  **B. Manip 2**
 Sur `router1`

   Afficher la table ARP
 
 
    [root@router1 hugo]# ip neigh flush all
    [root@router1 hugo]# ip neigh show
    10.1.0.1 dev enp0s8 lladdr 0a:00:27:00:00:07 REACHABLE



   ### expliquer le(s) ligne(s)

La seul connexion établi est entre le `router1` et le `pc hôte` 

---

Sur `client1`

  Ping  `server1`

    [root@client1 hugo]# ping server1.tp4
    PING server1.tp4 (10.2.0.10) 56(84) bytes of data.
    64 bytes from server1.tp4 (10.2.0.10): icmp_seq=1 ttl=63 time=0.987 ms
    64 bytes from server1.tp4 (10.2.0.10): icmp_seq=2 ttl=63 time=0.932 ms
    64 bytes from server1.tp4 (10.2.0.10): icmp_seq=3 ttl=63 time=1.11 ms
    64 bytes from server1.tp4 (10.2.0.10): icmp_seq=4 ttl=63 time=1.27 ms
    ^C
    --- server1.tp4 ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3018ms
    rtt min/avg/max/mdev = 0.932/1.078/1.278/0.137 ms

Sur `router1`

  Afficher la table ARP

    [root@router1 hugo]# ip neigh show
    10.2.0.10 dev enp0s9 lladdr 08:00:27:71:dc:a1 STALE
    10.1.0.1 dev enp0s8 lladdr 0a:00:27:00:00:07 DELAY
    10.1.0.10 dev enp0s8 lladdr 08:00:27:21:17:90 STALE

### expliquer le(s) changement(s)

Maintenant le router reste connecter au `pc hôte` mais possède désormais aussi les connexions vers `server1` et `client1`

## C. Manip 3

Sur l'hôte (votre PC)

Afficher la table ARP

    C:\Users\Hugo>arp -a
    
    Interface : 192.168.0.19 --- 0x2
      Adresse Internet      Adresse physique      Type
      192.168.0.1           d0-84-b0-f5-96-4c     dynamique
      192.168.0.2           18-1e-78-e6-62-28     dynamique
      192.168.0.255         ff-ff-ff-ff-ff-ff     statique
      224.0.0.22            01-00-5e-00-00-16     statique
      224.0.0.251           01-00-5e-00-00-fb     statique
      224.0.0.252           01-00-5e-00-00-fc     statique
      239.255.255.250       01-00-5e-7f-ff-fa     statique
      255.255.255.255       ff-ff-ff-ff-ff-ff     statique
    
    Interface : 10.2.0.1 --- 0x4
      Adresse Internet      Adresse physique      Type
      10.2.0.10             08-00-27-71-dc-a1     dynamique
      10.2.0.254            08-00-27-25-24-67     dynamique
      10.2.0.255            ff-ff-ff-ff-ff-ff     statique
      224.0.0.22            01-00-5e-00-00-16     statique
      224.0.0.251           01-00-5e-00-00-fb     statique
      224.0.0.252           01-00-5e-00-00-fc     statique
      239.255.255.250       01-00-5e-7f-ff-fa     statique
    
    Interface : 10.1.0.1 --- 0x7
      Adresse Internet      Adresse physique      Type
      10.1.0.10             08-00-27-21-17-90     dynamique
      10.1.0.254            08-00-27-9c-39-75     dynamique
      10.1.0.255            ff-ff-ff-ff-ff-ff     statique
      224.0.0.22            01-00-5e-00-00-16     statique
      224.0.0.251           01-00-5e-00-00-fb     statique
      224.0.0.252           01-00-5e-00-00-fc     statique
      239.255.255.250       01-00-5e-7f-ff-fa     statique
    
    Interface : 192.168.56.1 --- 0x9
      Adresse Internet      Adresse physique      Type
      192.168.56.255        ff-ff-ff-ff-ff-ff     statique
      224.0.0.22            01-00-5e-00-00-16     statique
      224.0.0.251           01-00-5e-00-00-fb     statique
      224.0.0.252           01-00-5e-00-00-fc     statique
      239.255.255.250       01-00-5e-7f-ff-fa     statique
    
    Interface : 192.168.168.1 --- 0xe
      Adresse Internet      Adresse physique      Type
      192.168.168.255       ff-ff-ff-ff-ff-ff     statique
      224.0.0.22            01-00-5e-00-00-16     statique
      224.0.0.251           01-00-5e-00-00-fb     statique
      224.0.0.252           01-00-5e-00-00-fc     statique
      239.255.255.250       01-00-5e-7f-ff-fa     statique
    
    Interface : 192.168.49.1 --- 0x14
      Adresse Internet      Adresse physique      Type
      192.168.49.255        ff-ff-ff-ff-ff-ff     statique
      224.0.0.22            01-00-5e-00-00-16     statique
      224.0.0.251           01-00-5e-00-00-fb     statique
      224.0.0.252           01-00-5e-00-00-fc     statique
      239.255.255.250       01-00-5e-7f-ff-fa     statique

-   vider la table ARP

    C:\WINDOWS\system32>netsh interface ip delete arpcache
    Ok.
    
    
    C:\WINDOWS\system32>arp -a
    
    Interface : 192.168.0.19 --- 0x2
      Adresse Internet      Adresse physique      Type
      192.168.0.1           d0-84-b0-f5-96-4c     dynamique
      224.0.0.22            01-00-5e-00-00-16     statique
    
    Interface : 10.2.0.1 --- 0x4
      Adresse Internet      Adresse physique      Type
      224.0.0.22            01-00-5e-00-00-16     statique
    
    Interface : 10.1.0.1 --- 0x7
      Adresse Internet      Adresse physique      Type
      224.0.0.22            01-00-5e-00-00-16     statique
    
    Interface : 192.168.56.1 --- 0x9
      Adresse Internet      Adresse physique      Type
      224.0.0.22            01-00-5e-00-00-16     statique
    
    Interface : 192.168.168.1 --- 0xe
      Adresse Internet      Adresse physique      Type
      224.0.0.22            01-00-5e-00-00-16     statique
    
    Interface : 192.168.49.1 --- 0x14
      Adresse Internet      Adresse physique      Type
      224.0.0.22            01-00-5e-00-00-16     statique

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MzYxNDIxMjgsLTgzODM0MTE2Myw2OD
c4MTg1ODUsMTUxNTQ1NDQ5MiwzNjM3Mzc5OTUsLTk4NDA4NzM3
OSwxMTMxMzU1MDkzLDExOTUxODQ4MzMsNTU4MTI3NTIwLC0xOT
UxNTY4MTI4LC02NjA0NTMxMjldfQ==
-->