---
title: Maven gebruiken voor Gemeenschappen
description: Adobe Experience Manager Uber API-jar
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 3df90511-e43e-442b-bf73-44c22c1886b7
source-git-commit: ab3d016c7c9c622be361596137b150d8719630bd
workflow-type: tm+mt
source-wordcount: '115'
ht-degree: 0%

---

# Maven gebruiken voor Gemeenschappen {#using-maven-for-communities}

## Overzicht {#overview}

Dit gedeelte van de documentatie van de Adobe Experience Manager (AEM) Communities is een aanvulling op:

* [AEM projecten bouwen met Apache Maven](../../help/sites-developing/ht-projects-maven.md).

Er is slechts één &quot;uber&quot;artefact dat individuele artefacten vervangt:

* AEM [Uber API-jar](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

>[!NOTE]
>
>Vanaf AEM 6.4 worden de communautaire API&#39;s niet expliciet vrijgegeven. Alle Community API&#39;s zijn nu opgenomen in de Uber jar zelf.
>
>Houd up-to-date met de meest recente versie van de Gemeenschappen.
>
>Zie de [Laatste releases](deploy-communities.md#latest-releases) waar u de meest recente versie kunt identificeren.

## Voorbeeld van Geweven afhankelijkheid {#maven-dependency-example}

```xml
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.5.7</version>
    <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>Zie de [AEM Uber jar-opslagplaats](https://mvnrepository.com/artifact/com.adobe.aem/uber-jar) waar je het nieuwste Uber jar artefact kunt identificeren.

<!--
There are now two "uber" artifacts that replace individual artifacts:

* AEM [Communities API jar](#communities-api-jar-artifact)
* AEM [Uber API jar](../../help/sites-developing/ht-projects-maven.md#what-is-the-uberjar)

## Communities API Jar Artifact {#communities-api-jar-artifact}

Following is an example of a GAV for the AEM Communities API jar:

```xml
<dependency>
    <groupId>com.adobe.cq.social</groupId>
    <artifactId>cq-socialcommunities-api</artifactId>
    <version>1.11.170</version>
    <scope>provided</scope>
</dependency>

```

Ensure thet the version specified corresponds with the Communities package version installed for AEM Communities. To verify the installed version number:

1. Log in with adminstrative privileges.
1. Browse to [Package Manager](../../help/sites-administering/package-manager.md). For example, [http://localhost:4502/crx/packmgr/](http://localhost:4502/crx/packmgr/)

1. Locate the package: `cq-socialcommunities-pkg-1.x.xxx`
1. Extract the version from the package name:
   * First version for AEM 6.3 is version 1.11.170.
   * Feature packs will be versions 1.12.xxx.

>[!NOTE]
>
>It is recommended to keep up-to-date with the most recent Communities release.
>
>Visit the [Latest Releases](deploy-communities.md#latest-releases) section to identify the most recent version.

## Maven Dependency Example {#maven-dependency-example}

The Communities API jar must be specified before the Uber API jar.

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
-->
