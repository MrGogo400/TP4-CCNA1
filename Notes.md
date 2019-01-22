// Spécifier une route = 

 1. Réseau 
 2. Le Gateway 
 3. Interface de sortie

> Pour faire un ping il faut aussi un pong donc il faut que la machine pingé connaissent la route vers notre machine

Quand on est sur le même réseau de quelqu'un on a pas besoin de sont IP, on peux ping son MAC

> Quand on ping quelqu'un on ping le broadcast pour chercher l’adresse mac du destinataire

Si le pc reçoit un ping avec son ip mais pas la bonne adresse mac il va automatiquement changer l'adresse mac pour celle de la personne voulue et dévier le ping vers la personne

> Si il ne connait pas la personne il fait un "arp broadcast" et il passe par le broadcast

<!--stackedit_data:
eyJoaXN0b3J5IjpbNDQ0OTY1MTM3LC01MTYyMDQxOCwxODMyMT
g0NjVdfQ==
-->