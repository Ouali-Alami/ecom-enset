# ecom-enset - App E-commerce

**ecom-enset** est une application e-commerce basée sur l'architecture microservices et Spring.

## L'architecture de l'application 
  Todo: draw flow diagram
## Listes des services qutilise l'appication

- product-service : Gestion des produits
- inventory-service : Gestion des catégories
- product service : Gestion des paniers
- order-service  : Gestion des commandes
- config service: Gestion des configurations services
- gateway-service: pont entre les differents services et les clients
- consul-service: Gestion des services(Enregistrement, Recherche) 

Le service config-service va chercher ses configurations à l'endroit que j'ai défini via le fichier application.properties du service config-service. Assurez-vous de mettre les bonnes informations, par exemple :

```properties
server.port=8888
spring.application.name=config-service
spring.cloud.config.server.git.uri=git@github.com:Ouali-Alami/ms-enset.git
spring.cloud.config.server.git.search-paths=config-repo
spring.cloud.config.server.git.default-label=main
```
## Prérequis

- **Java 17+** (ou version supérieure)
- **Maven** (pour la gestion des dépendances et la construction du projet)
- **Git** (pour cloner le dépôt et gérer les sous-modules)

## Installation et Configuration

Assurez-vous d'avoir le même jdk17 partout.
Si vous voulez créer vos propres applications Spring basées sur les microservices et Consul, il vous faudra cloner à minima les services config-service, gateway-service et consul-service.

TODO : ajouter les dépôts des différents services
```bash
git clone git@github.com:Ouali-Alami/
git clone git@github.com:Ouali-Alami/
git clone git@github.com:Ouali-Alami/
```

Ici, on supposera que vous voulez simplement tester l'application ecom-enset.

Installer les dépendances avec Maven:

```bash
git clone git@github.com:Ouali-Alami/ms-enset.git
    cd ecom-enset
    mvn install
```
Assurez-vous d'avoir tous les fichiers .properties des différents services à jour avec votre propre configuration.

## Démarrage des services 
Dans ce projet on utilisera consul afin d'enregistrer et rechercher des services.
On va tout d'abord démarrer un agent consul en mode serveur via la commande:
```bash
ip=$(hostname -I)
consul agent -server -bootstrap-expect=1 -data-dir=consul-data -ui -bind="$ip"
```
Vous pourrez voir l'interface de Consul à l'adresse :
```bash
http://localhost:8500
```
puis demarrer l'app via :
```bash
mvn spring-boot:run
```

TODO: FR -> EN





