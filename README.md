TP4-CCNA1

### A. Manip 1
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

###  **B. Manip 2**
 
 

    [root@router1 hugo]# ip neigh flush all
    [root@router1 hugo]# ip neigh show
    10.1.0.1 dev enp0s8 lladdr 0a:00:27:00:00:07 REACHABLE

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMDMyMzQ3NzIsMzYzNzM3OTk1LC05OD
QwODczNzksMTEzMTM1NTA5MywxMTk1MTg0ODMzLDU1ODEyNzUy
MCwtMTk1MTU2ODEyOCwtNjYwNDUzMTI5XX0=
-->