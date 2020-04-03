# Protocole JOCC 0.9 

**Auteur: [Walid] [Massaoudi] (`walid.massaoudi@heig-vd.ch`)**

## Introduction

### Objectifs du protocole
Notre protocole JOCC va offrir aux client  la possibilité de récuppérer des Jokes envoyés par des autres utilisateurs et qui sont stocker dans notre serveur .
Afin de garantir l'établissement de la connection avec le serveur avant les échanges des messages ,on va utiliser un protocole basé sur TCP/IP 

### Fonctionnement général
Comme on a mentioné précédament le protocole TCP sera utilisé  par JOCC comme un protocole transport .Le port par défaut sera le port 6565 (un port au dessus de 1024 (reserved ports)).
Le client va tenter de se connecter sur le serveur ,une fois notre connection est établie le serveur propose la liste des ses services proposé par un message contenant le menu de l'application.
Le client peut envoyer des Jokes au serveur avec le syntaxe Joke [catégorie] ["the joke "], en suite le serveur va stoker ce dernier .les utilisateurs aussi ont la possibilité de récupérer toutes la liste des jokes avec la commande ALLJOKE .Apèrs avoir reçu cette liste chaque Joke sera identifier par un Tag (numéro) ,
ce qui nous permet d'offrir la possibilité d'évaluation des Jokes on tapant LIKE [TAG JOKE].Une commande RANK taper par le client retourne tout simplement une liste des utilisateurs classée premièrement selon l'évaluation (nombre des LIKE total) de Joke puis le nombre de joke (Nombre de JOKE).
Les Joke sont enregistré suivant des catégorie prédéfinie par le serveur .Une fois note client a finit ,il envoie un message END pour fermer la connexion TCP.
## Messages
Le protocole JOCC définit .. messages :
WELCOME ,LIST,ERROR et END
### WELCOME 
### LIST
### ERROR 
### END 

A vous de structurer ce document, en utilisant plusieurs sections. Une de ces sections doit être consacrée à la gestion de l'état, où vous nous expliquez si votre protocole est avec ou sans état, et pourquoi.

## Elements spécifiques
### Service fournie
###Extensibilité
### Traitement d'erreurs
## Remarques

Si vous avez des choses à partager au sujet de l'exercice, utilisez cette dernière section.
