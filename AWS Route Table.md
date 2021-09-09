[[AWS Network]]
tags: #description 

Une table de routage au sens AWS peut se situer sur plusieurs objets réseaux différents :

→ Un [[AWS VPC|VPC]]

→ Un subnet

→ Une Transit gateway

Elle permet de renseigner le chemin à prendre pour acheminer un paquet destiné à un autre réseau

eg. Envoi d'un paquet à l'adresse 10.210.10.1 (10.210.0.0/16) vers l'adresse 10.200.10.1 (10.200.0.0/16)

Sur AWS elle se compose de :

![[assets/Pasted image 20210909224903.png]]

→ Une association à un ou plusieurs subnets (Prévalence de la table de routage du subnet par rapport au VPC)

→ Une association à un VPC

→ Est-ce que c'est la table de routage principal du VPC (Principal)