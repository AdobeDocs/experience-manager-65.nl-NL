---
title: OSGI-pakketten
seo-title: OSGI-pakketten
description: Tips voor het beheren van uw OSGi-bundels
seo-description: Tips voor het beheren van uw OSGi-bundels
uuid: 07af7089-a233-4e5b-928c-76ddc0af8839
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
discoiquuid: 8d3374ac-51dd-4ff5-84c9-495c937ade12
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '359'
ht-degree: 0%

---


# OSGI-pakketten{#osgi-bundles}

## Semantische versie {#use-semantic-versioning} gebruiken

De best practices voor semantische versienummering zijn overeengekomen op [https://semver.org/](https://semver.org/).

## Sluit niet meer klassen en potten in dan strikt noodzakelijk in bundels OSGi {#do-not-embed-more-classes-and-jars-than-strictly-needed-in-osgi-bundles}

Gemeenschappelijke bibliotheken moeten in afzonderlijke bundels worden opgenomen. Hierdoor kunnen ze opnieuw worden gebruikt in alle bundels. Wanneer het verpakken van *JAR* in een bundel OSGI, zorg ervoor om online bronnen te controleren om te zien of heeft iemand dit reeds eerder gedaan. Enkele gebruikelijke plaatsen om bestaande bundelomhulsels te vinden zijn: Apache Felix, Apache Sling, Apache Geronimo, Apache ServiceMix, Eclipse Bundle Recipes en de SpringSource Enterprise Bundle Repository.

## Afhankelijk van de laagst benodigde bundelversies {#depend-on-the-lowest-needed-bundle-versions}

Voor afhankelijkheden bij compilatie in POM-bestanden is altijd afhankelijk van de laagst vereiste versie die de benodigde API beschikbaar maakt. Dit maakt hogere achterwaartse verenigbaarheid mogelijk en maakt het terugkeren van moeilijke situaties aan oudere versies gemakkelijker.

## Een minimale set pakketten exporteren uit OSGi-bundels {#export-a-minimal-set-of-packages-from-osgi-bundles}

Zodra een pakket is geëxporteerd, hebben we een API gemaakt waarvan anderen afhankelijk kunnen zijn. Zorg ervoor dat u zo weinig mogelijk exporteert en zorg ervoor dat wat wordt geëxporteerd een API is. Het is veel gemakkelijker om een privé methode/klasse te nemen en het openbaar te maken dan het iets te nemen dat eerder werd uitgevoerd en het privé te maken.

Implementaties moeten altijd in een afzonderlijk *impl*-pakket worden geplaatst. Standaard exporteert de *maven-bundle-plugin* alles in het project dat geen *impl* in de naam heeft.

## Altijd expliciet een semantische versie definiëren voor elk geëxporteerd pakket {#always-explicitly-define-a-semantic-version-for-each-package-exported}

Hierdoor kunnen consumenten van uw API samen met u evolueren. Volg daarbij altijd semantische best practices voor versiebeheer. Hierdoor kunnen consumenten van uw API weten welke typen wijzigingen in een nieuwe versie worden verwacht.

## Metatype-informatie opnemen indien beschikbaar {#include-metatype-information-where-exposed}

Door betekenisvolle metatype informatie te specificeren, zal het uw diensten en componenten gemakkelijker maken om in de console van Felix te begrijpen. Een lijst van SCR annotaties en attributen kan worden gevonden bij: [https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html](https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html).
