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

sur `client1`

-   ping  `server1`
-   afficher la table ARP


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNzM0NzgxNjAsNTU4MTI3NTIwLC0xOT
UxNTY4MTI4LC02NjA0NTMxMjldfQ==
-->