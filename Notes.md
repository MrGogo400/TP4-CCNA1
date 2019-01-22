// Spécifier une route = 

 1. Réseau 
 2. Le Gateway 
 3. Interface de sortie

> Pour faire un ping il faut aussi un pong donc il faut que la machine pingé connaissent la route vers notre machine

Quand on est sur le même réseau de quelqu'un on a pas besoin de sont IP, on peux ping son MAC

> Quand on ping quelqu'un on ping le broadcast pour chercher l’adresse mac du destinataire

Si le pc reçoit un ping avec son ip mais pas la bonne adresse mac il va automatiquement changer l'adresse mac pour celle de la personne voulue et dévier le ping vers la personne

> Si il ne connait pas la personne il fait un "arp broadcast" et il passe par le broadcast

 1. ping ip
 2. Check table routage
		KO -> X
		OK -> gw
 3. Check ARP table
		y-a-t'il "ip de la gw" ?
				KO -> arp broadcast
				OK -> on a déjà sa MAC
4. Le ping part

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYxNDMzMDA4Miw0NDQ5NjUxMzcsLTUxNj
IwNDE4LDE4MzIxODQ2NV19
-->