---
date: 2025-09-03
---
- [[généralités sur le wifi|généralités]]
- [[normes du wifi|normes]]
- [[architecture pour wifi|architecture]]
- étude de couverture et zones d'émissions
- besoins et [[sécurisation du wifi|sécurisation]]
- diagnostics et dépannages
___
# TD 1
2,4 ghz à l'extérieur car porte plus loin, mais aussi 5ghz ; on peut enlever le wifi 1 et 2 car les normes [^1] sont négociées au mieux selon les conditions par les appareils, ce qui permet qu'ils ne soient pas choisis par les clients
et 5 ghz à l'intérieur car 2,4 ghz plus sujet à interférence comme micro-ondes

controleur est généralement plus pratique, mais surtout ce qui nous dit qu'il faut avoir centralisé c'est parce que le client sera déjà authentifié donc le problème de roaming [^2] parce que si on est censé activé un audio au moment où on arrive devant un truc ça active un audio donc on peut pas attendre 3 secondes.
Il faut un endroit sécurisé pour le controleur donc il faut le mettre dans les locaux administratifs
Soit mettre des locaux techniques avec des switchs soit fibres pour relier les plus lointains car le parc phoenix fait plus de 100 mètres, sinon wimesh et ajouter quand même l'électricité.
Sauf que wimesh est perturbable car ils se connectent entre eux donc on peut perdre plusieurs bonnes si on perd une borne.
Le mieux serait les switchs car ça peut laisser un aggrandissement du réseau, sauf que si on met des équipements dans une boite la température peut monter. La fibre ne nécessite pas d'équipements

si sur les bords : antennes directionnelles
dans la serre il y aura plus de bornes car humidité 
il peut y avoir des problèmes si les arbres poussent ou tout autre condition du genre ; aussi des problèmes avec le fait que s'il y a beaucoup de gens au même endroit il peut ne plus y avoir de réseaux

([[notes de contenu/but3/wifi]])

[^1]: [[normes du wifi]]

[^2]: [[architecture pour wifi]]
