# TP 4.1 – Spring Cloud Eureka (Service Registry & Discovery)

## Description

Ce TP met en œuvre le **registre de services et la découverte des microservices** à l’aide de **Spring Cloud Netflix Eureka**.
Un **Eureka Server** centralise l’enregistrement des microservices, tandis que plusieurs **instances du microservice Produits** s’y déclarent automatiquement.

Le projet s’appuie sur **Spring Cloud Config** pour la gestion centralisée de la configuration.

## Architecture

Le système est composé de :

1. **Config Server**

   * Fournit la configuration externalisée
   * Port : 9101

2. **Eureka Server**

   * Registre et découvre les microservices
   * Port : 9102

3. **Microservice Produits**

   * Client Eureka
   * Plusieurs instances possibles
   * Ports : 9001, 9011, etc.

## Fonctionnalités

* Mise en place d’un Eureka Server
* Enregistrement automatique des microservices
* Découverte des services via Eureka
* Support du déploiement multi-instances
* Centralisation de la configuration via GitHub

## Annotations clés

* `@EnableEurekaServer` : activation du serveur Eureka
* `@EnableDiscoveryClient` : enregistrement du microservice
* `@EnableConfigurationProperties` : gestion des propriétés externalisées

## Accès

* Config Server :

  ```
  http://localhost:9101/eureka-server/default
  ```
* Eureka Server :

  ```
  http://localhost:9102/
  ```
* Microservice Produits :

  ```
  http://localhost:9001/Produits
  ```

## Exécution

### Démarrer le Config Server

```bash
cd config-server
mvn spring-boot:run
```

### Démarrer le Eureka Server

```bash
cd eurekaserver
mvn spring-boot:run
```

### Démarrer le microservice Produits (instance 1)

```bash
cd microservice-produits
mvn spring-boot:run -Dserver.port=9001
```

### Démarrer une deuxième instance

```bash
mvn spring-boot:run -Dserver.port=9011
```

## Vérifications

* Accéder à la console Eureka :

  ```
  http://localhost:9102/
  ```
* Vérifier l’enregistrement des instances du microservice Produits
* Tester l’API Produits via HTTP

## Objectifs pédagogiques

* Comprendre le Service Registry et Discovery
* Mettre en place Eureka Server
* Enregistrer et découvrir des microservices
* Gérer plusieurs instances d’un même service
* Préparer l’intégration avec une API Gateway

---

**MOHAMMED EL KHAYATI & MOUAD MOUDID --5IIR11**
