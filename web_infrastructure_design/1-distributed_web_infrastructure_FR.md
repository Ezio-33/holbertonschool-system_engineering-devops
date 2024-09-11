# Infrastructure Web Distribuée

## Explication des éléments additionnels

1. **Serveur supplémentaire** : Ajouté pour la redondance et la répartition de la charge, améliorant la disponibilité et les performances du système.

2. **Load-balancer (HAproxy)** : Distribue le trafic entrant entre les deux serveurs, optimisant l'utilisation des ressources et améliorant la disponibilité du service.

3. **Serveur d'application séparé** : Permet une meilleure séparation des responsabilités et une scalabilité plus facile de la couche application.

## Algorithme de distribution du load-balancer

Le load-balancer est configuré avec l'algorithme Round Robin. Cet algorithme distribue les requêtes de manière séquentielle à chaque serveur disponible à tour de rôle. C'est simple, équitable, et efficace pour des charges de travail uniformes.

## Configuration du load-balancer : Active-Active

Dans cette configuration, tous les serveurs traitent simultanément le trafic, maximisant l'utilisation des ressources.

- **Active-Active** : Tous les serveurs sont opérationnels et traitent les requêtes simultanément.
- **Active-Passive** (non utilisé ici) : Un serveur est actif, les autres sont en attente et ne deviennent actifs qu'en cas de défaillance du serveur principal.

## Fonctionnement du cluster de base de données Primary-Replica

Dans notre configuration Primary-Replica (anciennement Master-Slave) :

- Le nœud Primary gère toutes les opérations d'écriture.
- Les nœuds Replica sont synchronisés avec le Primary et gèrent les opérations de lecture.
- En cas de défaillance du Primary, un Replica peut être promu Primary.

## Différence entre le nœud Primary et Replica pour l'application

- **Primary** : Gère toutes les opérations d'écriture (INSERT, UPDATE, DELETE).
- **Replica** : Utilisé pour les opérations de lecture (SELECT), réduisant la charge sur le Primary et améliorant les performances de lecture.

## Problèmes potentiels de cette infrastructure

1. **Points uniques de défaillance (SPOF)** :

   - Le load-balancer est un SPOF potentiel.
   - Le nœud Primary de la base de données est un SPOF pour les opérations d'écriture.

2. **Problèmes de sécurité** :

   - Absence de pare-feu, exposant l'infrastructure à des attaques potentielles.
   - Pas de HTTPS, compromettant la confidentialité et l'intégrité des données en transit.

3. **Absence de monitoring** :
   - Sans système de surveillance, il est difficile de détecter et de réagir rapidement aux problèmes de performance, de coupure de service ou de sécurité.
