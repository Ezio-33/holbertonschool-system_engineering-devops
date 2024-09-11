# Infrastructure Web Sécurisée et Surveillée

## Explication des éléments additionnels

1. **Pare-feu (3)** :
   Ajoutés pour filtrer le trafic entrant et sortant, protégeant l'infrastructure contre les accès non autorisés et les attaques potentielles.

2. **Certificat SSL** :
   Ajouté pour permettre le chiffrement HTTPS, assurant la confidentialité et l'intégrité des données échangées entre les utilisateurs et le site web.

3. **Clients de monitoring (3)** :
   Ajoutés pour collecter des données sur la performance, la sécurité et la santé de chaque serveur et du load balancer.

## Rôle des pare-feu

Les pare-feu servent à :

- Filtrer le trafic réseau entrant et sortant
- Bloquer les accès non autorisés
- Établir une zone démilitarisée (DMZ)

## Pourquoi le trafic est servi en HTTPS

Le trafic est servi en HTTPS pour :

- Chiffrer les données échangées entre le client et le serveur
- Assurer l'intégrité des données transmises
- Authentifier le site web auprès des utilisateurs
- Protéger la confidentialité des informations des utilisateurs

## Utilité du monitoring

Le monitoring est utilisé pour :

- Surveiller la santé et les performances des serveurs
- Détecter rapidement les problèmes ou les pannes
- Analyser les tendances d'utilisation des ressources
- Permet de déterminer les besoins d'evolution

## Collecte de données par l'outil de monitoring

L'outil de monitoring collecte les données en :

- Installant des agents sur chaque serveur et le load balancer
- Récupérant des métriques système (CPU, mémoire, disque, réseau)
- Analysant les logs des applications
- Effectuant des vérifications de disponibilité et de performance

## Surveillance du QPS (Queries Per Second) du serveur web

Pour surveiller le QPS du serveur web :

- Configurer l'outil de monitoring pour collecter les logs du serveur web
- Mettre en place des métriques spécifiques pour compter les requêtes
- Créer des tableaux de bord pour visualiser le QPS en temps réel
- Configurer des alertes pour des seuils de QPS spécifiques

## Problèmes potentiels de cette infrastructure

1. **Terminaison SSL au niveau du load balancer** :

   - Le trafic entre le load balancer et les serveurs n'est pas chiffré
   - Augmente la charge de travail du load balancer
   - Peut créer un point unique de défaillance pour la sécurité

2. **Un seul serveur MySQL pour les écritures** :

   - Point unique de défaillance pour les opérations d'écriture
   - Risque de perte de données en cas de panne
   - Limite la scalabilité des opérations d'écriture

3. **Serveurs avec les mêmes composants** :
   - Manque de spécialisation des ressources
   - Difficulté à optimiser chaque serveur pour des tâches spécifiques
   - Risque de surcharge uniforme sur tous les serveurs en cas de pic de trafic
