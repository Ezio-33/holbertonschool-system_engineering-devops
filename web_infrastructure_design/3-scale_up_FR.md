# Infrastructure Web Évolutive

## Éléments ajoutés et leurs justifications

1. **Serveur supplémentaire** :
   Ajouté pour permettre la séparation des composants et améliorer la scalabilité de l'infrastructure.

2. **Load-balancer (HAproxy) en cluster** :
   Un deuxième load-balancer est ajouté et configuré en cluster avec l'existant pour éliminer le point unique de défaillance au niveau de la répartition de charge et améliorer la disponibilité du service.

3. **Séparation des composants** :
   Les composants (serveur web, serveur d'application, base de données) sont maintenant sur des serveurs dédiés pour les raisons suivantes :

   a. **Serveur Web dédié** :

   - Optimisé pour gérer les requêtes HTTP et servir le contenu statique.
   - Permet une mise à l'échelle indépendante de la couche web.

   b. **Serveur d'Application dédié** :

   - Concentré sur l'exécution du code de l'application.
   - Facilite l'optimisation des ressources pour les besoins spécifiques de l'application.

   c. **Serveur de Base de Données dédié** :

   - Optimisé pour les opérations de base de données.
   - Améliore les performances et la sécurité des données.

## Avantages de cette architecture évolutive

1. **Meilleure scalabilité** :
   Chaque composant peut être mis à l'échelle indépendamment selon les besoins.

2. **Performance améliorée** :
   Les ressources de chaque serveur sont optimisées pour leur tâche spécifique.

3. **Maintenance facilitée** :
   Les mises à jour et la maintenance peuvent être effectuées sur chaque composant sans affecter les autres.

4. **Sécurité renforcée** :
   La séparation des composants permet une meilleure isolation et la mise en place de politiques de sécurité spécifiques.
   L'utilisation aussi de firewall different permet aussi une meilleurs sécurité par rapport au attaques.

5. **Haute disponibilité** :
   Le cluster de load-balancers élimine un point unique de défaillance critique.

## Considérations supplémentaires

- Cette architecture augmente la complexité et les coûts de l'infrastructure, mais offre une meilleure flexibilité et des performances optimisées.
- Une stratégie de sauvegarde et de reprise après sinistre doit être mise en place pour chaque serveur.
- Le monitoring devient encore plus crucial pour surveiller la santé et les performances de chaque composant séparé.
