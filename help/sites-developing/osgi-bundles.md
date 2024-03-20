---
title: OSGi-bundels
description: Lees wat tips voor het beheer van uw OSGi-bundels in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: e18065c7-75b9-4b37-8294-cf94122a4dcf
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# OSGi-bundels{#osgi-bundles}

## Semantische versienummering gebruiken {#use-semantic-versioning}

De beste werkwijzen voor semantische versienummering zijn overeengekomen op [https://semver.org/](https://semver.org/).

## Sluit niet meer klassen en potten in dan strikt noodzakelijk in bundels OSGi {#do-not-embed-more-classes-and-jars-than-strictly-needed-in-osgi-bundles}

Gemeenschappelijke bibliotheken moeten in afzonderlijke bundels worden opgenomen. Hierdoor kunnen ze opnieuw worden gebruikt in alle bundels. Bij het omsluiten van een *JAR* in een bundel OSGi, zorg ervoor om online bronnen te controleren om te zien of heeft iemand dit reeds eerder gedaan. Een aantal gangbare plaatsen om bestaande bundelpakjes te vinden zijn: Apache Felix, Apache Sling, Apache Geronimo, Apache ServiceMix, Eclipse Bundle Recipes en de SpringSource Enterprise Bundle Repository.

## Afhankelijk van de laagst benodigde bundelversies {#depend-on-the-lowest-needed-bundle-versions}

Voor afhankelijkheden bij compilatie in POM-bestanden is altijd afhankelijk van de versie die het laagst nodig is en die de benodigde API beschikbaar maakt. Hierdoor is meer compatibiliteit met oudere versies mogelijk en worden terugwerkende oplossingen voor oudere versies eenvoudiger.

## Een minimale set pakketten exporteren uit OSGi-bundels {#export-a-minimal-set-of-packages-from-osgi-bundles}

Wanneer een pakket is geëxporteerd, is een API gemaakt waarvan anderen afhankelijk zijn. Zorg ervoor dat u zo weinig mogelijk exporteert en zorg ervoor dat wat wordt geëxporteerd een API is. Het is veel gemakkelijker om een privé methode/klasse te nemen en het openbaar te maken dan het iets te nemen dat eerder werd uitgevoerd en het privé te maken.

Implementaties altijd in een aparte map plaatsen *impl* pakket. Standaard worden de *maven-bundle-plugin* exporteert alle onderdelen van het project die geen *impl* in zijn naam.

## Altijd expliciet een semantische versie definiëren voor elk geëxporteerd pakket {#always-explicitly-define-a-semantic-version-for-each-package-exported}

Hierdoor kunnen consumenten van uw API samen met u evolueren. Volg daarbij altijd semantische best practices voor versiebeheer. Hierdoor kunnen consumenten van uw API weten welke typen wijzigingen in een nieuwe versie worden verwacht.

## Metatype-informatie opnemen als deze wordt weergegeven {#include-metatype-information-where-exposed}

Door betekenisvolle metatype informatie te specificeren, maakt het uw diensten en componenten gemakkelijker te begrijpen in de console van Felix. Een lijst van SCR annotaties en attributen kan worden gevonden bij: [https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html](https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html).
