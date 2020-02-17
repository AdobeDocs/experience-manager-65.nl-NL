---
title: Maven gebruiken voor Gemeenschappen
seo-title: Maven gebruiken voor Gemeenschappen
description: AEM Communities API jar en AEM Uber API jar
seo-description: AEM Communities API jar en AEM Uber API jar
uuid: ea37a89a-db6c-4018-8ab9-f5717e6c0421
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a726c904-aadd-4678-be84-9e05808ab8be
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Maven gebruiken voor Gemeenschappen {#using-maven-for-communities}

## Overzicht {#overview}

Dit gedeelte van de documentatie van de AEM Communities is een aanvulling op:

* [AEM-projecten bouwen met Apache Maven](../../help/sites-developing/ht-projects-maven.md)

Er zijn nu twee &#39;Number&#39;-artefacten die afzonderlijke artefacten vervangen:

* AEM [Communities API-jar](#communities-api-jar-artifact)
* AEM [Uber API-jar](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

## Communities API Jar Artifact {#communities-api-jar-artifact}

Hier volgt een voorbeeld van een GAV voor de API-jar van AEM Communities:

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>
```

Zorg ervoor dat de opgegeven versie overeenstemt met de pakketversie van de Gemeenschappen die voor AEM Communities is geïnstalleerd. Om het geïnstalleerde versienummer te verifiëren:

1. Aanmelden met beheerdersrechten.
2. Blader naar [Pakketbeheer](../../help/sites-administering/package-manager.md). Bijvoorbeeld: [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)

3. zoek het pakket *cq-social gemeenschappen-pkg-1.x.xxx*
4. de versie ophalen uit de pakketnaam
   * De eerste versie voor AEM 6.3 is versie 1.11.170
   * de eigenschappakken zullen versies 1.12.xxx zijn

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
