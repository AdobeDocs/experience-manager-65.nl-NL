---
title: Maven gebruiken voor Gemeenschappen
seo-title: Maven gebruiken voor Gemeenschappen
description: AEM Communities API-jar en AEM Uber API-jar
seo-description: AEM Communities API-jar en AEM Uber API-jar
uuid: ea37a89a-db6c-4018-8ab9-f5717e6c0421
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a726c904-aadd-4678-be84-9e05808ab8be
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '183'
ht-degree: 0%

---


# Maven gebruiken voor Gemeenschappen {#using-maven-for-communities}

## Overzicht {#overview}

Deze sectie van de documentatie van AEM Communities is naast:

* [Bouwen AEM projecten met Apache Maven](../../help/sites-developing/ht-projects-maven.md).

Er zijn nu twee &#39;Number&#39;-artefacten die afzonderlijke artefacten vervangen:

* AEM [Community API-jar](#communities-api-jar-artifact)
* AEM [Uber API-jar](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

## Communities API Jar Artifact {#communities-api-jar-artifact}

Hier volgt een voorbeeld van een GAV voor de AEM Communities API-jar:

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>
```

Zorg ervoor dat de opgegeven versie overeenkomt met de versie van het communautaire pakket die voor AEM Communities is geïnstalleerd. Om het geïnstalleerde versienummer te verifiëren:

1. Meld u aan met beheerdersrechten.
1. Blader naar [Pakketbeheer](../../help/sites-administering/package-manager.md). Bijvoorbeeld: [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)

1. Zoek het pakket: `cq-socialcommunities-pkg-1.x.xxx`
1. Extraheer de versie uit de pakketnaam:
   * De eerste versie voor AEM 6.3 is versie 1.11.170.
   * De pakken van de eigenschap zullen versies 1.12.xxx zijn.

>[!NOTE]
>
>Aanbevolen wordt de meest recente versie van de Gemeenschappen bij te houden.
>
>Ga naar de sectie [Laatste releases](deploy-communities.md#latest-releases) om de meest recente versie te identificeren.

## Voorbeeld van Geweven afhankelijkheid {#maven-dependency-example}

De Community API jar moet worden opgegeven vóór de Uber API jar.

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.3.0</version>
    <scope>provided</scope>
    <classifier>apis</classifier>
</dependency>
```
