---
date: 2025-09-20
alias:
  - concepts à propos du module 1 du ccna | ospf monozone
---
le dead timing détermine si un routeur est toujours joignable et est 4 fois plus long que les timings hello en ospfv2

le routage hiérarchique est plus facile en multi-zone parce que seulement les routeurs d'une même zones calculent spf avec les états des liens, alors que dans ospf les zones s'ajustent hiérarchiquement et elles se connectent à une zone fédératrice où tout les routeurs sont connectés
L'avantage de ospf est que les modifications de topologie dans une zone n’entraînent pas de recalculs SPF dans les autres zones.

Les timings hello et dead sont utiles pour former l'adjacence en ospf, et si les timings dead ne sont pas les mêmes les paquets qui sont inutiles en étant trop occurrents vont expirer 

hello est le premier paquet échangé entre les routeurs ospf, et contient notamment l'intervalle hello et dead
Le paquet DBD (Database Description) est utilisé pour envoyer une liste résumée de la base de données d'état de liens (LSDB étant la base de donnée sur laquelle est fait le résumé) d'un routeur à son voisin. Cela permet de comparer la topologie locale à celle envoyée par un autre routeur.
Le paquet LSR (Link-State Request) est envoyé par un routeur à son voisin après la comparaison des DBD. Si un routeur constate qu'il lui manque certaines informations de topologie (LSA) à ce moment le routeur crée une table topologique, il envoie un LSR pour demander ces informations spécifiques.
Le paquet LSU (Link-State Update) sert à annoncer les nouvelles informations et est utilisé pour envoyer les informations d'état de liens demandées (LSA) en réponse à un LSR. C'est le paquet qui contient les informations détaillées sur la topologie du réseau (liens, routeurs, etc.).
Le paquet LSAck (Link-State Acknowledgment) sert à confirmer la réception d'une mise à jour et est une simple confirmation de la réception d'un LSU. Il garantit que le processus de mise à jour s'est déroulé correctement et que le routeur a bien reçu l'information demandée.

la valeur de priorité d'un routeur est 1 par défaut, 0 sert à un routeur qui ne sera jamais élu (DROther), la priorité la plus haute parmi les interfaces des routeurs désigne le routeur DR la priorité peut aller jusque 255 et si elle est égale pour 2 routeurs le routeur id le plus élevé désignera le routeur prioritaire, un routeur avec une plus haute priorité sera DR et le routeur de secours sera BDR (il n'y en a qu'un seul).
les interfaces par défaut ont cette priorité
Si un routeur est nommé DR il le reste jusqu'à ce qu'il tombe en panne, peu importe les priorités des autres routeurs

les différents états de voisinage ospf :
1. down ; pour le prochain état on envoie des paquets hello ; la contiguïté (étape du processus de routage) est inactive
2. init : on a reçu un paquet hello, mais dans ce paquet le routeur ne voit son id parce qu'il a juste reçu sans que son envoi précédent ait un impact sur les autres paquets envoyés par le(s) autre(s) routeur(s) ; la contiguïté est init
3. two way : quand chaque routeur voit son id dans les paquets hello reçus ; la contiguïté est établit ; la contiguïté est bidirectionnelle
4. exstrat : négociation du "maitre" "esclave" 
	- il faut que les routeurs se considèrent comme connectés pour faire ça
5. exchange : échange de paquets DBD entre "maître" et "esclave"
6. loading : routeurs comparent les DBD, LSR pour demander des infos et LSU pour recevoir ces infos ; l'échange d'annonce à état de lien est faite
7. full : base de donnée synchronisées, la table topologique (LSDB) est synchro
	- et ensuite les routeurs executent spf pour déterminer les meilleurs chemins vers chaque destination
	- et enfin choisit la meilleure route

base de donnée de contiguïté signifie détaille sur les routeurs voisins, alors que la bdd d'état de liens contient la table topologique (et est la seule qui est identique sur tout les routeurs ospf d'une même zone)
Chaque interface de la liaison reliant les routeurs OSPF doit être dans le même sous-réseau pour qu’une contiguïté soit établie.

une fois que l'état est full les paquets LSU sont envoyés aux routeurs voisins lorsqu’une modification de topologie réseau est détectée (mises à jour qu'à propos du changement en lui-même) toutes les 30 minutes

l'id ospf du routeur permet aussi d'identifier un routeur au sein de ospf
le format de l’ID du routeur sur un routeur compatible OSPF est un nombre de 32 bits formaté comme une adresse IPv4

l'id du routeur par défaut (si  la commande router-id n'a pas assigné une ip) est choisi en priorité en prenant :
1. ip de loopback la plus élevée
2. ip d'interface physique la plus élevée

R1(config)# router ospf *id-de-processus-ospf*
R1(config-router)# network *réseau* *wildmask* area *numéro_aire*

wildmask est l'inverse du masque classique de réseaux

la commande router(config-router)# network *un_réseau* 0.0.0.0 area *une_aire*
permet d'utiliser ospf pour annoncer un sous-réseau en particulier

La commande show ip ospf interface serial 0/0/0 affiche les intervalles « hello » et « minuteur dead » configurés sur une liaison WAN série point à point entre deux routeurs OSPFv2
La commande show ipv6 ospf interface serial 0/0/0 affiche les intervalles « hello » et « minuteur dead » configurés sur une liaison WAN série point à point entre deux routeurs OSPFv3.
La commande show ip ospf interface fastethernet 0/1 affiche les intervalles « hello » et « minuteur dead » configurés sur une liaison multi-accès entre deux (ou plusieurs) routeurs OSPFv2
La commande show ip ospf neighbor affiche l’intervalle mort écoulé depuis la réception du dernier message hello, mais n’affiche pas la valeur configurée de la minuterie. La commande show ip ospf neighbor indique si deux routeurs adjacents ont échangé des messages OSPF afin de former une relation de voisin.

Coût ospf = bande passante de référence / bande passante de l'interface
La valeur par défaut est de 100 Mbit/s (100 000 000 bit/s)
Mais dans les faits d'un routeur à un autre doit ajouter le coût des liens qui se calcule de la même manière : Gigabit Ethernet => 100.000.000 / 1.000.000.000 = 1. Une liaison Fastethernet fais 100Mbit/s
sauf que si on fait +0.1 alors dans les faits ça augmente de 1 alors il faut modifier la valeur de référence pour refléter plus précisément le coût des liaisons qui dépassent 100 Mbit/s

Une route par défaut est utile pour diriger vers internet donc elle sera sur le routeur qui est connecté à internet

R1# show ip ospf interface serial0/0/1 ; affiche des infos sur l'interface et  sur son utilisation d'ospf

le problème d'une passive interface est qu'elle n'est pas encore activée pour ospfv2

pour identifier un routeur cisco recommande de Configurer une valeur à l’aide de la commande router-id

la méthode préférée pour rendre le nouvel ID du routeur efficace est de réinitialiser le processus de routage OSPF en entrant soit la commande clear ip ospf process , soit la commande reload

la commande network *réseau* 0.0.0.0 area *numéro d'aire* active sur l'interface  associée ospf

show ip protocols est utilisée pour vérifier que OSPF est activé et fournit également une liste des réseaux annoncés par le réseau
La commande show ip route ospf affiche les entrées apprises via OSPF dans la table de routage.

([[concepts à propos du module 1 et 2 du ccna ospf monozone]])