---
title: OSGi-bundels
description: Lees wat tips voor het beheer van uw OSGi-bundels in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
exl-id: e18065c7-75b9-4b37-8294-cf94122a4dcf
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '334'
ht-degree: 0%

---

# OSGi-bundels{#osgi-bundles}

## Semantische versienummering gebruiken {#use-semantic-versioning}

Overeengekomen op beste praktijken voor semantische versienummering kunnen in [ https://semver.org/ ](https://semver.org/) worden gevonden.

## Sluit niet meer klassen en potten in dan strikt noodzakelijk in bundels OSGi {#do-not-embed-more-classes-and-jars-than-strictly-needed-in-osgi-bundles}

Gemeenschappelijke bibliotheken moeten in afzonderlijke bundels worden opgenomen. Hierdoor kunnen ze opnieuw worden gebruikt in alle bundels. Wanneer het verpakken van a *JAR* in een bundel OSGi, zorg ervoor om online bronnen te controleren om te zien of heeft iemand dit eerder reeds gedaan. Een aantal gangbare plaatsen om bestaande bundelpakjes te vinden zijn: Apache Felix, Apache Sling, Apache Geronimo, Apache ServiceMix, Eclipse Bundle Recipes en de SpringSource Enterprise Bundle Repository.

## Afhankelijk van de laagst benodigde bundelversies {#depend-on-the-lowest-needed-bundle-versions}

Voor afhankelijkheden bij compilatie in POM-bestanden is altijd afhankelijk van de versie die het laagst nodig is en die de benodigde API beschikbaar maakt. Hierdoor is meer compatibiliteit met oudere versies mogelijk en worden terugwerkende oplossingen voor oudere versies eenvoudiger.

## Een minimale set pakketten exporteren uit OSGi-bundels {#export-a-minimal-set-of-packages-from-osgi-bundles}

Wanneer een pakket is geëxporteerd, is een API gemaakt waarvan anderen afhankelijk zijn. Zorg ervoor dat u zo weinig mogelijk exporteert en zorg ervoor dat wat wordt geëxporteerd een API is. Het is veel gemakkelijker om een privé methode/klasse te nemen en het openbaar te maken dan het iets te nemen dat eerder werd uitgevoerd en het privé te maken.

Plaats altijd implementaties in een afzonderlijk *impl* pakket. Door gebrek, *maven-bundle-plugin* voert om het even wat in het project uit dat geen *impl* in zijn naam heeft.

## Altijd expliciet een semantische versie definiëren voor elk geëxporteerd pakket {#always-explicitly-define-a-semantic-version-for-each-package-exported}

Hierdoor kunnen consumenten van uw API samen met u evolueren. Volg daarbij altijd semantische best practices voor versiebeheer. Hierdoor kunnen consumenten van uw API weten welke typen wijzigingen in een nieuwe versie worden verwacht.

## Metatype-informatie opnemen als deze wordt weergegeven {#include-metatype-information-where-exposed}

Door betekenisvolle metatype informatie te specificeren, maakt het uw diensten en componenten gemakkelijker te begrijpen in de console van Felix. Een lijst van SCR annotaties en attributen kan in worden gevonden: [ https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html ](https://felix.apache.org/documentation/subprojects/apache-felix-maven-scr-plugin/scr-annotations.html).
