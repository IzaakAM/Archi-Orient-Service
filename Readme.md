# ATTENTION
Impossible de régler les erreurs CORS. 
Pour lancer l'application, il faut désactiver les politiques de gestion des requêtes options du navigeur

Pour contourner temporairement les erreurs CORS lors du développement, vous pouvez lancer votre navigateur sans les politiques de sécurité :

- **Chrome/Edge** : Lancez avec `--disable-web-security --user-data-dir=/tmp/dev` :
  ```bash
  google-chrome --disable-web-security --user-data-dir=/tmp/dev
  ```
- **Firefox** : Modifiez `about:config` :
  - Passez `security.fileuri.strict_origin_policy` à `false`.
  - Utilisez l'extension **CORS Everywhere** pour plus de flexibilité.

⚠️ **Attention** : Cette méthode désactive des mécanismes de sécurité. À utiliser uniquement pour des tests locaux.

# Projet Démo de Microservices

Ce projet est une démonstration de l'utilisation de 4 API Spring Boot avec un design épuré, une documentation Swagger pour chaque API, une gestion des erreurs détaillée et documentée, ainsi qu'une gestion des accès.

## Technologies
### Spring Boot
Spring Boot est utilisé pour développer les 4 API qui composent le projet. Il offre un moyen simple et efficace de créer des applications Spring autonomes et prêtes pour la production.

### Vue.js
Le frontend du projet a été développé avec Vue.js, un framework JavaScript populaire. Vue.js a été choisi pour sa simplicité, sa flexibilité, et sa capacité à créer une présentation complète et exhaustive des fonctionnalités de l'API, en utilisant des bibliothèques telles que Bootstrap et Bootswatch.

### Eureka
Eureka est utilisé comme service de nommage au cœur du projet. Il permet aux services de s'enregistrer eux-mêmes et de découvrir d'autres services, ce qui rend possible la découverte de services de manière dynamique ainsi que l'équilibrage de charge.

#### Pourquoi Eureka ?
Eureka est un bon choix pour ce projet car il permet une découverte dynamique des services et un équilibrage de charge. Cela signifie que si un service est ajouté ou retiré, les autres services peuvent automatiquement le découvrir ou cesser de l'utiliser, sans configuration manuelle.

### Spring Cloud Gateway
Spring Cloud Gateway est utilisé comme passerelle API pour acheminer les requêtes entre le frontend et les 4 API. Il a été préféré à Zuul, car ce dernier n'est plus maintenu, et le projet officiellement destiné à le remplacer est Spring Cloud Gateway.

#### Pourquoi Spring Cloud Gateway ?
Spring Cloud Gateway est un bon choix pour ce projet car il s'agit d'une passerelle API moderne et activement maintenue. Elle fournit des fonctionnalités telles que le routage des requêtes, le filtrage et l'équilibrage de charge, nécessaires pour un projet multi-API.

### Spring Cloud Config
Spring Cloud Config est utilisé pour décentraliser la configuration des microservices. Cela permet de faciliter les ajustements de configuration du projet, même à distance, via un dépôt.

#### Pourquoi Spring Cloud Config ?
Spring Cloud Config est un bon choix pour ce projet car il permet de décentraliser et de gérer simplement et efficacement la configuration des microservices. Cela est particulièrement utile pour un projet comportant plusieurs microservices, car cela permet de modifier facilement la configuration du projet dans son ensemble, sans devoir changer chaque microservice individuellement.

## Authentification
Le projet utilise un système d'authentification basé sur des tokens bearer, où les tokens sont des hachages de l'objet utilisateur. Cela permet de différencier différents types d'utilisateurs, comme les administrateurs.

Pour exécuter le projet localement, vous pouvez cloner la branche master et démarrer le docker-compose. Le projet sera alors accessible sur le port 8984. Les ports 8980, 8981, 8982, et 8983 sont également mappés pour accéder à la documentation Swagger des différentes API via /swagger-ui/index.html. Le port 8986 est également mappé pour la console Eureka. Ces mappages ne sont pas nécessaires si vous n'avez pas besoin d'accéder à la documentation ou aux informations de surveillance, donc n'hésitez pas à les désactiver dans le docker-compose en cas de conflit.

![Architecture.png](https://github.com/IzaakAM/AOS/blob/dev/froome-ui/public/Architecture.png)