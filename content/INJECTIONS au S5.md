---
date: 2025-10-20
---
faire du fusing c'est utiliser pleins de caractères différents, pour utiliser le système de base de donnée pour trouver une faille
on peut toujours activer l'http history, et chaque élément on peut l'envoyer vers un autre outil (notamment repeater)

ssrf : server side request
# SQL
## SQL injection vulnerability allowing login bypass
- ouvrir burpsuite
- mettre mode proxy et intercept et intercept on (que quand on est sur la page login)
- cliquer sur login sur le site
- cliquer sur la requête post sur burp
- changer le username dans la requête en : administrator'--
- cliquer sur forward all

' permet de fermer une requête sql
## SQL injection vulnerability in WHERE clause allowing retrieval of hidden data
- ouvrir burpsuite
- mettre mode proxy et HTTP history
- on ra

1=1 c'est comme mettre TRUE à la requête SQL

# XSS
permet à l'attaquant d'executer du code (plupart du temps du js)

on peut en faire dans du inner html pour si les balises scripts sont bloqués
# XXE
XML entity permet d’exécuter des commandes systèmes

svg c'est du xml 
# OS command
pour qu'un site soit vulnérable il faut qu'il fasse une commande système, par exemple trouver le dernier server mail qui a émis le mail

([[INJECTIONS au S5]])