---
date: 2025-09-10
---
![[Pasted image 20250910093500.png]]
encryption wpa3 se fait grâce à une clé

premier c'est wep

wpa a été cassé car produit du wep
![[Pasted image 20250910093547.png]]

wpa2 : beaucoup mieux ;  temporal key utile pour rajouter du hasard même si c'est pas vraiment du hasard, mais surtout pour éviter les man-in-the middle pour pas que les trames soient rejouées. On peut lui envoyer des requêtes de déconnexion et déconnecter tout le monde juste en captant le wifi

wpa3 : nécessite wifi6 ; bssid : id par adresse mac
![[Pasted image 20250910093616.png]]

owe : nécessite wifi6

pendant très longtemps les téléphones se connectaient automatiquement aux wifi ouverts
## radius
![[Pasted image 20250910093654.png]]
dial in : parce que c'est utiliser pour sécuriser les boxs chez nous

authentification : qui es tu ?
autorization : tes droits

![[Pasted image 20250910094003.png]]
![[Pasted image 20250910095012.png]]

![[Pasted image 20250910095549.png]]
udp ça craint un peu parce que si on prend son ip on peut se faire passer pour lui. Mais peap règle ce problème tout en utilisant udp

serveur répond c'est ok même si mdp incorrect
![[Pasted image 20250910101132.png]]
## portails captifs
![[Pasted image 20250910103112.png]]
en coupure : c'est que c'est lui le dhcp et le dns etc...

fait firewall, notamment pour se protéger car ça peut être la faute d'un responsable

peut faire des trucs variables

## législation hotspots
![[Pasted image 20250910103620.png]]
## diverses attaques
![[Pasted image 20250910154307.png]]

([[sécurisation du wifi]])