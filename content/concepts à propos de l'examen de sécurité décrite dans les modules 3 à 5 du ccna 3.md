---
date: 2025-09-21
---
la raison qui pousse les cybercriminels à attaquer des réseaux est le gain financier

le type de hacker agit pour des raisons politiques et sociales est un Hacktiviste

un cheval de Troie se présente sous la forme d’un logiciel utile, mais dissimule un code malveillant

en intéraction avec un utilisateur un hacker peut utiliser la manipulation psychologique

Un balayage ping est un outil utilisé au cours d’une attaque de reconnaissance. Chaque adresse IP dans la plage est testée pour voir si elle répond à la requête.

Les zombies sont des ordinateurs infectés. Les zombies sont utilisés pour déployer une attaque par déni de service distribué (DDoS).

Pour trouver un masque wildcard commun, on convertit les réseaux en binaire et là où ça diffère on met des 1

Les listes de contrôle d’accès étendues filtrent généralement les adresses source et de destination IPv4 et les numéros de port TCP ou UDP. Un filtrage supplémentaire peut être fourni pour les types de protocoles.

Généralement une liste de contrôle d’accès standard est généralement placée aussi près que possible du réseau de destination car les expressions de contrôle d’accès dans une liste de contrôle d’accès standard n’incluent pas les informations sur le réseau de destination.

Une liste de contrôle d’accès étendue sert à filtrer les adresses d’hôte source et de destination spécifiques. Généralement, le meilleur emplacement pour une liste de contrôle d’accès étendue est le plus proche de la source, c'est à dire la première interface de routeur qui utilise le paquet.

Le type d’ACL étendue offre une grande flexibilité et un meilleur contrôle sur l’accès au réseau. Les listes d’accès standard filtrent uniquement l’adresse IP source et la direction in ou out. les acl étendues filtrent :
- Adresse IP source et adresse IP de destination.
- Le protocole (TCP, UDP, ICMP, etc.).
- Les ports source et de destination (par exemple, bloquer le port 80 pour le trafic web ou le port 22 pour le trafic SSH).
exemple : Router1(config-ext-nacl)# permit tcp *réseau* *wildcard masque* any eq www ; pour autoriser un réseau vers toutes destinations en port 80 sous tcp

l’invite CLI après avoir entré la commande ip access-list standard aaa à partir du mode de configuration global change en Router(config-std-nacl)#

après l’exécution de la commande no access-list *numéro de l'acl* La liste de contrôle d’accès respective est supprimée de la configuration en cours.
pour désactiver une liste de contrôle d’accès sur une interface, la commande R1(config-if)# no ip access-group doit être saisie.

On peut pas deny une acl un réseau et permit ensuite son sous-réseau

Il faut d'abord deny un réseau avec une acl standard et ensuite tout autoriser avec une autre acl standard si on veut juste qu'il n'y ait pas un réseau en particulier

Une ACE est une acl avec un numéro, elles sont évaluées dans l'ordre croissant
Il faut d'abord deny un sous réseau avec un numéro, ensuite autoriser son réseau avec un numéro plus grand, et enfin mettre un numéro d'ace plus grand pour deny any. Pour autoriser un réseau sans un sous-réseau ; si on fait l'inverse (ordre) y compris avec des protocoles on autorise si c'est inclus dans le permit

par défaut après avoir configuré des acl il y a un deny any à la fin des acl

configurer une ACL standard afin que seule l’adresse IP 192.168.15.23 puisse passer par le routeur, il faut ses deux commandes :
Router1(config)# access-list *num acl* permit *ip hôte* 0.0.0.0
Router1 (config)# access-list *num acl* permit host *ip hôte*

pour configurer une acl sur un sous-réseau dont on connait le masque et que l'on a une ip d'exemple :
- 32 - *masque*
- 2 puissance ce nombre : 
- -2 : ce nombre d'adresse nous donne le nombre d'adresses disponibles
on fait aussi : 
- masque - 24 ou 16 ou 8 pour savoir combien de bits on a en plus d'un masque classique
- 2 puissance 7 + 2 puissance 6 ... chaque terme le nombre de bits qu'on a trouvé précédemment 
- on inverse pour trouver le wildcard masque
on assemble ces deux trucs dans cette commande :
- access-list 1 permit *réseau* *wildcard masque*

show access-list *mon acl*
montre notamment dans le cas des permit le nombre de fois qu'ils ont été utilisés par règle par numéro ACE
et ne montre pas le deny any any par défaut (écrit sous forme acl étendue)

submerger un hôte cible au moyen de connexions TCP semi-ouvertes est une Attaque par inondation SYN. Lors d’une attaque par inondation SYN TCP, le hacker envoie à l’hôte cible un flot continu de requêtes de session SYN TCP avec une adresse IP source usurpée. L’hôte cible répond avec un paquet TCP-SYN-ACK à chacune des requêtes de session SYN et attend un TCP ACK qui n’arrivera jamais. Finalement, la cible est submergée par des connexions TCP semi-ouvertes.

lorsqu’un cybercriminel fournit une passerelle non valide afin de lancer une attaque de l’homme du milieu, il attaque le protocole DHCP. Un cybercriminel peut configurer un serveur DHCP pirate qui fournit un ou plusieurs des éléments suivants :
Une passerelle par défaut incorrecte utilisée pour lancer une attaque de l’homme du milieu et permettre au hacker d’intercepter des données
Un serveur DNS incorrect en raison duquel l’utilisateur est redirigé vers un site web malveillant.
Une adresse IP de passerelle par défaut non valide qui provoque une attaque par déni de service sur le client DHCP

([[concepts à propos de l'examen de sécurité décrite dans les modules 3 à 5 du ccna 3]])