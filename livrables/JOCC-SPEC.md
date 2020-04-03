# Protocole JOCC 0.9 

**Auteur: [Walid] [Massaoudi] (`walid.massaoudi@heig-vd.ch`)**

## Introduction

### Objectifs du protocole
Notre protocole JOCC va offrir aux client  la possibilité de récuppérer des Jokes envoyés par des autres utilisateurs et qui sont stocker dans notre serveur .
Afin de garantir l'établissement de la connection avec le serveur avant les échanges des messages ,on va utiliser un protocole basé sur TCP/IP 

### Fonctionnement général
Comme on a mentioné précédament le protocole TCP sera utilisé  par JOCC comme un protocole transport .Le port par défaut sera le port 6565 (un port au dessus de 1024 (reserved ports)).
Le client va tenter de se connecter sur le serveur ,une fois notre connection est établie le serveur propose la liste des ses services proposé par un message contenant le menu de l'application.
Le client peut envoyer des Jokes au serveur avec le syntaxe Joke [catégorie] ["the joke "], en suite le serveur va stoker ce dernier .les utilisateurs aussi ont la possibilité de récupérer toutes la liste des jokes avec la commande ALLJOKE ,L'option -r avec cette commande nous retoune la liste des Jokes la plus récente .
Apèrs avoir reçu cette liste chaque Joke sera identifier par un Tag (numéro) ,
ce qui nous permet d'offrir la possibilité d'évaluation des Jokes on tapant LIKE [TAG JOKE].Une commande RANK taper par le client retourne tout simplement une liste des utilisateurs classée premièrement selon l'évaluation (nombre des LIKE total) de Joke puis le nombre de joke (Nombre de JOKE).
Les Jokes sont enregistré suivant des catégorie prédéfinie par le serveur .Une fois note client a finit ,il envoie un message END pour fermer la connexion TCP.
## Messages
Le protocole JOCC définit .. messages :
WELCOME ,LIST,ERROR et END
### WELCOME 
C'est un message envoyé par le serveur juste apèrs l'établissement du connection .Ce message propose la liste des services founies par notre serveur.
Exemple :
WELCOME 
    You want some Jokes ? this is how to use me :
    -JOKE [category]["your joke "] 
          Category : BLACKHUMUR,NOTFUNNY,CRTICAL,ELSE
    -ALLJOKE -r
           -r :lastet
    -LIKE [TAG]
          TAG:tag Joke
    -RANK
                    
### LIST
CE message est générique ,il porte les réponse sous forme d'une liste .
### ERROR 
Ce messag est livré en cas d'erreur.
### END 
un message end indique la fermeture de la connection 

## Elements spécifiques
### Service fournie
   Le  serveur offre deux fonctionnalité principales ,la première est d'ajouter un Joke à la base de donnée de notre serveur,
l'autre est de litser les jokes disponibles .
###Extensibilité
Une implémentation supplémentaire offre des autres fonctionnalitées .Ces options seront communiquer avec le client pendant le message WELCOME.  
### Traitement d'erreurs
En cas d'erreur le serveur envoie un message ERROR contenant le code d'erreur . 
## Remarques
Exemples d'utilisation par le client :
-JOKE NOTFUNNY "my first joke "
-ALLJOKE 

Exemple réponse de la part du serveur à la commande ALLJOKE:
user     joke           NbJokes    Likes
couc     "whatsup"        2          4
couc      "here we go "   2          0

Si vous avez des choses à partager au sujet de l'exercice, utilisez cette dernière section.
