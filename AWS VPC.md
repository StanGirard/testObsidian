[[AWS Network]]

# Introduction

Un [[VPC]] est un objet représentant un réseau au sens [[AWS|AWS]], c'est un réseau virtuel privé fourni par Amazon, ses caractéristiques et options sont les suivantes :

![[assets/Pasted image 20210909224159.png]]

→ Un bloc d'adresses IPv4 au minimum ici : **10.40.0.0/16**

→ Un objet d'ACL réseau correspondant à un firewall de bas niveau

→ Une table de routage permettant de rediriger le traffic à destination d'internet ou d'un autre réseau

→ Un jeu d'options DHCP permettant de gérer l'attribution des IPs des machines EC2

## Tips and tricks

---

Si vous souhaitez faire une zone DNS privée en faisant un CNAME vers une adresse privée du VPC, il faudra activer les options suivantes : → Résolution DNS → Noms d'hôtes DNS

# Advanced

- How To
	- [[Create an AWS VPC Peering]]