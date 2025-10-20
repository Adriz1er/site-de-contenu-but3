---
date: 2025-10-03
---
Le bénéfice principal de l'utilisation d'un marquage de Qualité de Service (QoS) (au niveau de la couche 3 (réseau)) est sa capacité à maintenir l'information de QoS de bout en bout à travers différents segments et équipements du réseau, y compris les routeurs.
- Le marquage de couche 3 utilise le champ DSCP (Differentiated Services Code Point) dans l'en-tête IP (Internet Protocol).
- Comme le paquet IP reste inchangé (à l'exception de certaines valeurs comme le Time To Live) en traversant différents sous-réseaux et routeurs, le marquage DSCP est préservé sur l'ensemble du chemin IP. Cela permet à tous les routeurs et équipements de couche 3 de prendre des décisions cohérentes en matière de QoS (priorisation, mise en file d'attente, etc.) pour ce flux de trafic spécifique.
Les commutateurs (switches) de couche 2 opèrent sur les adresses MAC (couche 2). Pour qu'un commutateur prenne en compte la QoS, il utilise le champ CoS (Class of Service) dans l'en-tête 802.1Q. CoS est distinct de QoS
QoS ne peut pas être utilisé pour transporter du trafic non-ip car il est dans l'entête ip

La ligne de confiance indique l’endroit où les marquages de QoS sur un paquet qui entre dans le réseau d’une entreprise sont jugés pertinents ; donc pas besoin que le trafic soit précédemment marqué. 
La ligne de confiance permet de savoir quels appareils se fient au marquage sur les paquets qui entrent dans le réseau.

les deux approches permettant d’empêcher la perte de paquets induite par la congestion d’une interface sont d':
- Abandonner les paquets moins prioritaires.
- Augmenter la capacité des liaisons.
- à la rigueur d'augmenter la mémoire tampon

le scénario de configuration qui offrirait le plus de protection à SNMP pour obtenir et définir des messages est SNMPv3 configuré avec le niveau de sécurité d’authentification

La commande ntp server *adresse IP* sert à synchroniser l'horloge du système avec l'heure de l'appareil correspondant à l'ip

EtherChannel est utilisé sur un réseau en vue d’accroître les capacités de vitesse en regroupant plusieurs ports physiques au sein d’une ou plusieurs liaisons EtherChannel logiques entre deux commutateurs ; pas à faire de la redondance

la définition d’une conception du réseau LAN à deux niveaux est que les couches de distribution et cœur de réseau sont regroupées dans un niveau, et la couche d’accès sur un niveau distinct

les trois couches du modèle de conception hiérarchique de commutateur sont distribution, accès, cœur de réseau

Le cœur de réseau peut fournir une connectivité haut débit du réseau fédérateur [^1] , et agit en tant qu'associateur  de tous les blocs de campus (par exemple les différents batiments)
La couche distribution définit la limite du cœur de réseau, elle peut servir à implémenter une politique d’accès réseau comme QoS.
La couche d'accès permet de connecter les terminaux, ce qui constitue la périphérie du réseau, elle fournit un accès réseau à l'utilisateur.

Une ligne de base du réseau est créée afin de fournir un point de comparaison, lorsque le réseau fonctionne de manière optimale, vis-à-vis des modifications implémentées dans l’infrastructure. La planification initiale permet d’assurer le suivi des performances et des modèles de trafic, et de surveiller le comportement du réseau dans le temps.
Des règles requises pour le réseau c'est celle pour le QoS, qu'il faut prévoir de manière réaliste 

Quand un ordinateur n'arrive pas à accéder au web mais aux appareils de son réseau, c'est qu'il a probablement une adresse de passerelle qui n'est pas la bonne

Réduire l’étendue des causes probables, passe d'abord par savoir sur quelle couche se situe le problème

Le terme gigue désigne la variation de latence ou de délai entre les paquets reçus.

L'algorithme de mise en file ne présente qu’une file d’attente et qui traite tous les paquets de manière égale est FIFO

Le LLQ (Low Latency Queuing) permet de prioriser certains types de trafic

Le QoS n’offre pas de garantie de livraison des paquets.
Il permet de traiter tous les paquets de la même façon.

L'ip du serveur et le nom du fichier du nouveau fichier de configuration est nécessaire pour charger un nouveau fichier de config

syslog fonctionne lors d'évènements et fournit des messages sur les évènements. Syslog sert à la : 
- collecte des informations d’enregistrement
- sélection du type d’informations à enregistrer
- sélection de la destination des informations enregistrées

La MIB (Management Information Base) réside sur un appareil du réseau et stocke les données relatives au fonctionnement de l’appareil ; c'est l'agent SNMP qui utilise la MiB pour stocker ses infos.
Un système de gestion de réseau (NMS) interroge périodiquement les agents SNMP qui résident sur les périphériques gérés à l’aide d’une requête get en vue d’obtenir des données de ces périphériques.
Une requête set est utilisée par le système de gestion de réseau (NMS) afin de modifier les variables de configuration du périphérique de l’agent.

Dans le résultat de la commande show lldp , sous Capability, R indique un routeur et B indique un pont (commutateur). 
Dans cette même commande Device ID indique les périphériques connectés au périphérique courant.
Cette commande n'indique pas tout les commutateurs.

utiliser de manière adaptable et intelligente les ressources pour distribuer la charge de trafic c'est de la flexibilité

pouvoir ajouter des services et pouvoir étendre le réseau de manière fluide c'est de la modularité

La conception hiérarchique divise le réseau en couches ce qui simplifie le déploiement de périphériques tout en connaissant leurs rôles.

La résilience c'est pouvoir toujours répondre aux attentes des utilisateurs.

Un domaine défaillant est la zone d’un réseau qui est affectée en cas de défaillance ; et les périphériques conservés par cette zone sont ceux qui sont affectés en conséquence de la panne.

Quand un administrateur veut mettre un bloc de commutateurs ainsi de ce type de philosophie à l'instant t ça n'a aucun impact sur l'utilisateur.

Un commutateur multicouche permet de créer une table de routage, et c'est pas le cas pour un commutateur de couche 2

L'adresse de la passerelle ne peut pas être la même que celle du pc.

après un show running-config dans les acls il y a un deny any any qu'on ne voit pas

pour résoudre un problème de mise en oeuvre ospf avec plusieurs routeurs il faut tester leurs connectivité.
Seule la commande show ip ospf neighbor nous permet de vérifier réellement de l'état de l'adjacence

Si une aire est partagée par deux routeurs il faut qu'ils soient dans le même sous-réseau pour qu'il y ait une contiguïté

quand une adresse publique est accessible mais pas un nom de domaine souvent c'est la faute du DNS

Le type de trafic décris comme nécessitant une latence ne dépassant pas 150 millisecondes est : voix

La commande show file systems affiche la quantité de mémoire disponible et libre, le type de système de fichiers et ses autorisations.

Quand la QoS est implémentée on peut améliorer les performances avec le délai et avec la gigue (variation de délai entre les paquets)

Le routeur sélectionne une image en fonction de la commande boot system dans la configuration.

Pour savoir les types d'appareils dans show cdp neighbors il faut regarder dans plateformes les modèles par exemple : routeur de la série Cisco 2811, un routeur de la série Cisco 1941 et un commutateur Cisco 2960.

Pour maintenir l'architecture réseau il faut de la redondance et de la flexibilité pour distribuer la charge

Pour faire de la redondance il faut d'autres chemins physiques

La connectivité sans fil au niveau de la couche d’accès offre une plus grande flexibilité, et des coûts réduits

Pour mesurer les opérations réseaux il faut qu'il y ait un trafic standard, il faut qu'il y ait une même heure sur des jours ouvrables moyens

diviser et conquérir désigne le fait que par une couche supérieure on a aussi vérifié les couches inférieures

pour vérifier l’en-tête des trames quittant un hôte précis on peut utiliser un Analyseur de protocole

Le type de trafic décris comme ayant tendance à être imprévisible, incohérent et surbaissant est la vidéo

la commande confreg 0x2142 permet d'ignorer le fichier de configuration de démarrage pendant le démarrage et de contourner les mots de passe requis.

Pour configurer le routeur pour charger une nouvelle image à partir de flash pendant le démarrage, il faut utiliser : boot system

La commande boot system est une commande de configuration globale permettant à l’utilisateur de spécifier la source pour l’image de logiciel Cisco IOS à charger ; notamment à partir d'un serveur tftp.
Le routeur utilisera l’image ROMmon se trouvant dans la mémoire morte (ROM) s’il ne parvient pas à trouver le serveur TFTP ou s’il ne parvient pas à charger une image valide à partir du serveur TFTP.

Les routeurs pour être contigus en ospf ont besoin d'avoir leurs ports liés dans une zone commune.

La QoS est importante dans un réseau convergé qui combine communications vocales, vidéo et de données parce qu'il est plus vulnérable à la latence.

Avec UDP il n'est pas possible d'utiliser les outils de prévention de congestion.

Le trafic avec de la voix est décrit comme prévisible et fluide

Le trafic avec des donnés est décris comme étant constitué d’un trafic dont la priorité est inférieure s’il n’est pas critique pour la mission

Le trafic avec de la vidéo est décris comme ayant un volume élevé de données par paquet.

Pour déterminer la taille du fichier image Cisco IOS sur le périphérique réseau il faut utiliser show flash:0

La latence du trafic vocal ne doit pas excéder 150 ms.
Les paquets de trafic vocal ne sont pas retransmis.



([[optimisation surveillance et dépannage des réseaux d'après les modules 9 et 12 du ccna3]])

[^1]: [[concepts à propos du module 1 et 2 du ccna ospf monozone]]
