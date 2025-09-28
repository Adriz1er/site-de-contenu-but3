---
date: 2025-09-28
---
Pour que les traductions NAT fonctionnent correctement, des interfaces à la fois interne et externe doivent être configurées pour la traduction NAT sur le routeur. Avec des commandes du type :
int *nom de l'interface*
ip nat *inside ou outside*
pour n'importe quel type de nat on est obligé on est obligé de spécifier une interface

Il existe quatre types d’adresses dans la terminologie NAT.
interne locale : adresse privée source (interne)
interne globale : adresse publique source (interne) ; est utilisée par le routeur pour les paquets transmis sur Internet et c'est celle que les autres vont voir
externe locale : adresse privée de destination
externe globale : adresse publique de destination

Les plages d'adresses privées sont :
- Classe A : 10.0.0.0 à 10.255.255.255 (10.0.0.0/8)
- Classe B : 172.16.0.0 à 172.31.255.255 (172.16.0.0/12)
- Classe C : 192.168.0.0 à 192.168.255.255 (192.168.0.0/16)
Si une adresse ne tombe dans aucune de ces classes alors elle est publique

Dans certains schéma s'il y a une adresse pas privée pour un serveur c'est donc son adresse routable et donc son adresse globale externe et pas locale externe. 
S'il y a deux types *différents* d'adresses spécifiées dans une configuration NAT statique, c'est donc quasi toujours locale interne et globale interne

l'ip de l'hôte est interne globale quand elle répond aux requêtes en utilisant l'adresse interne locale

quand on fait uniquement ip nat inside source static *adresse pas réseau* 
on ne mappe qu'un seul hôte sur le routeur

le nat dynamique fonctionne avec les étapes suivantes de l'interne vers l'externe :
1. L’hôte envoie les paquets demandant la connexion au serveur avec son ip
2. le routeur utilisant le nat dynamique vérifie la configuration NAT pour déterminer si ce paquet doit être traduit.
3. S’il n’existe aucune entrée de traduction pour cette adresse IP, le routeur détermine que l’adresse source doit être traduite.
4. Le routeur sélectionne une adresse globale disponible dans le pool d’adresses dynamiques.
5. Le routeur remplace l’adresse source par une adresse globale interne traduite.

L'inconvénient de l’utilisation de la traduction PAT des deux côtés de la transmission présente est que la traçabilité IPv4 de bout en bout est perdue.
il y a moins d'adresse publique disponible que d'adresse privée en général et dans le contexte du ccna

NAT : network address translation
PAT (aussi appelé NAT Overload) : port address translation
on peut utiliser uniquement pour le PAT avec de l'overloading c'est à dire en faisant sortir plusieurs IP 
l'overloading (aussi appelé surcharge) modifie le numéro de port
le NAT dynamique fonctionne avec un pool d'adresses privées pour un pool d'adresses publiques (1-à-1 temporaire)

une commande nat pour tout les types de nat c'est ce genre de commande :
ip nat inside/outside source/destination list_*numéro acl*/static_*adresse privée si c'est inside et pas privée si c'est outside*_ *adresse pas privée si c'est inside et privée si c'est outside* pool_*nom*/interface_*nom* overload/*rien*

la commande show ip nat statistics montre l'interface d'entrée et l'interface de sortie sur un routeur

la commande show ip nat translations montre avec des colonnes :
1. pro (protocol)
2. (ip) interne globale
3. (ip) interne locale
4. (ip) externe locale
5. (ip) externe globale

deux technologies catégorisées comme infrastructures WAN privées sont MetroE et Frame Relay
MetroE est aussi appelé WAN Ethernet
Une ligne louée peut être une option repésentative d'une architecture WAN privée

CPE : Customer Premises Equipment : Appareils et câblage aux clients qui se trouvent à la périphérie du réseau de l'entreprise en se connectent à la liaison d'un opérateur.

Point de démarcation : C'est le point physique où se termine la responsabilité du fournisseur de services

Équipement terminal de traitement de données : Périphériques du client qui transfèrent les données à partir du réseau d'un client ou d'un ordinateur hôte pour qu'elles soient transmises via le WAN.

DCE : Périphériques plaçant les données sur la boucle locale (support physique pour l'abonné d'un fournisseur de services).

WAN : wireless area network

Les WAN connectent principalement des réseaux (des routeurs), et non les périphériques terminaux individuels.

Les réseaux WAN sont généralement gérés par plusieurs fournisseurs de services Internet, mais les réseaux locaux sont généralement gérés par des organisations ou des particuliers.

Les réseaux WAN connectent les réseaux locaux à une vitesse plus lente que les réseaux locaux connectent leurs périphériques internes.​

le relais de trame permet de configurer différentes bandes passantes
Digital Subscriber Line permet des débits plus élévés en téléchargement qu'en chargement (upload)
le câble (cable modem) permet de combiner l'internet et la tv et le téléphone
T1 est une ligne de connexion point à point qui a un débit garantie
MetroE permet d'étendre ethernet à une zone métropolitaine

l'algorithme qui est utilisé avec IPsec pour assurer la confidentialité des données est AES

La solution VPN permet d’utiliser un navigateur Web pour établir un tunnel VPN d’accès distant sécurisé vers l’ASA est SSL sans client

La fonction de sécurité IPsec garantit que les données reçues via un VPN n’ont pas été modifiées en transit est intégrité

les deux technologies qui fournissent des solutions VPN gérées par l’entreprise sont Réseau privé virtuel site à site (VPN) et VPN d’accès à distance. 

Couche 2 MPLS VPN et Couche 3 MPLS VPN sont gérés par le fournisseur d'accès à internet ; le MPLS a à la fois des implémentations de couche 2 et de couche 3

les deux types de VPN qui sont des exemples de VPN d’accès à distance gérés par l’entreprise VPN IPsec basé sur le client et VPN SSL sans client

un VPN site à site nécessite une passerelle VPN à chaque extrémité du tunnel pour chiffrer et déchiffrer le trafic. Il ne nécessite pas de logiciel, ce serait pour un VPN d'accès à distance. 
Le vpn site à site est géré par la passerelle. Il faut que la passerelle puisse chiffrer et déchiffre le trafic.
le VPN de site à site n'est pas idéalement adapté à une utilisation par des travailleurs mobiles, le type de VPN idéalement adapté aux travailleurs mobiles est le VPN d'accès à distance (Remote Access VPN).
Le vpn site à site doit être configuré statiquement

Le tunneling ne garantit pas que les deux hôtes sont attribuées à un support physique.
Il met un ou plusieurs protocoles VPN qui encapsulent les paquets d’origine.
Les VPN utilisent des connexions virtuelles pour créer un réseau privé via un réseau public.

la fonction de l’algorithme HMAC (Code d’authentification de message haché) dans la configuration d’un VPN IPsec est de garantir l’intégrité des messages

les deux algorithmes de hachage utilisés avec IPsec AH pour garantir l’authenticité sont le SHA et MD5

Les deux algorithmes sui peuvent faire partie d’une politique IPsec pour fournir le chiffrement et le hachage pour protéger le trafic intéressant sont le SHA et l'AES

la fonction de l’algorithme Diffie-Hellman dans le cadre de travail IPsec est qu'il permet aux pairs d’échanger des clés partagées

Le protocole servant à créer une connexion virtuelle de point à point vers un trafic de tunnel non chiffré entre les routeurs Cisco et provenant de différents types de protocole est : GRE.
IPsec peut l'encapsuler

deux terminaux qui peuvent être de l’autre côté d’un VPN de site à site ASA configuré à l’aide d’ASDM sont : un routeur ISR et un autre ASA

Le type de VPN prend en charge plusieurs sites en appliquant des configurations aux interfaces virtuelles plutôt qu’aux interfaces physiques est Interface de tunnel virtuel IPSec

deux services d’infrastructure WAN qui sont des exemples de connexions privées : Frame Relay (parce qu'il est géré par l'opérateur) et T1/E1

si on fait la commande show ip nat statistics on peut avoir des stats et si il y a zéro en paquets transmis, on peut dire que les informations ne sont pas suffisantes pour savoir si n'importe quel type de NAT fonctionne

([[mise en réseau, sécurité et automatisation des entreprises d'après les modules 6 à 8 du ccna 3]])