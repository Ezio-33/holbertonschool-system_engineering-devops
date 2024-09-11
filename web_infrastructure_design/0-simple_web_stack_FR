# Explication de l'Infrastructure Web Simple

## 1. Qu'est-ce qu'un Serveur ?

Un serveur est une machine physique ou virtuelle qui fournit des services, des ressources ou des données à d'autres ordinateurs (clients) via un réseau. Il exécute un logiciel serveur qui écoute les requêtes des clients et y répond avec les données ou services appropriés.

## 2. Rôle du Nom de Domaine

Le nom de domaine (ex: www.foobar.com) est une adresse lisible par l'homme que les utilisateurs saisissent dans leurs navigateurs web. Il est traduit en adresse IP via le DNS (Domain Name System), permettant au navigateur de localiser et de se connecter au serveur hébergeant le site web.

## 3. Type d'Enregistrement DNS pour www dans www.foobar.com

Le sous-domaine 'www' dans 'www.foobar.com' est généralement un enregistrement A ou CNAME :

- **Enregistrement A :** Pointe directement vers l'adresse IP du serveur (ex: 8.8.8.8).
- **Enregistrement CNAME :** Pointe vers un autre nom de domaine qui résout l'adresse IP du serveur.

## 4. Rôle du Serveur Web

Le serveur web (ex: Nginx) gère les requêtes HTTP des utilisateurs. Il sert le contenu statique (HTML, CSS, JavaScript) et transmet les requêtes de contenu dynamique au serveur d'application. Il gère également les sessions utilisateurs et d'autres tâches liées au web.

## 5. Rôle du Serveur d'Application

Le serveur d'application traite le contenu dynamique en exécutant le code de l'application. Il gère les requêtes nécessitant une interaction avec la base de données et génère des réponses basées sur la logique définie dans les fichiers d'application. Il communique avec le serveur web pour renvoyer les données au client.

## 6. Rôle de la Base de Données

La base de données (ex: MySQL) stocke et gère les données utilisées par l'application, telles que les informations utilisateurs, le contenu et les paramètres de configuration. Le serveur d'application interroge la base de données pour récupérer ou mettre à jour les données nécessaires à la génération du contenu demandé.

## 7. Communication entre le Serveur et l'Ordinateur de l'Utilisateur

Le serveur communique avec l'ordinateur de l'utilisateur via HTTP (Hypertext Transfer Protocol) ou HTTPS (HTTP Secure) sur Internet. Ces protocoles facilitent l'échange de données entre le navigateur web de l'utilisateur et le serveur.

# Problèmes de cette Infrastructure

## 1. Point Unique de Défaillance (SPOF)

Tous les composants étant hébergés sur un seul serveur, une panne de ce serveur rend le site web entièrement indisponible. Il n'y a pas de redondance ou de mécanisme de basculement pour assurer une disponibilité continue.

## 2. Temps d'Arrêt lors de la Maintenance

La maintenance, comme le déploiement de nouveau code ou la mise à jour du serveur, nécessite le redémarrage du serveur web ou d'autres composants. Cela peut entraîner des interruptions de service pour les utilisateurs, le serveur étant temporairement indisponible.

## 3. Incapacité à Gérer un Trafic Élevé

La configuration à serveur unique a une capacité limitée pour gérer une augmentation du trafic. En cas de pic de visiteurs, le serveur peut être surchargé, entraînant des problèmes de performance ou des plantages.

## Solution que je préconise :

Des serveurs supplémentaires avec du load balancing pour gérer des volumes de trafic plus élevés sans perte de performance en plus d'une sécurité en cas de panne ou de mise à jour des serveurs pour assurer une continuité de services.
