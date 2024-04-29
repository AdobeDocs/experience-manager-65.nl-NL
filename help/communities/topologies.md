---
title: Aanbevolen topologieën voor Gemeenschappen
description: Hoe te om de behandeling van user-generated inhoud (UGC) te benaderen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
exl-id: b6658330-d862-44e3-aac0-824fb91cd087
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '548'
ht-degree: 0%

---

# Aanbevolen topologieën voor Gemeenschappen {#recommended-topologies-for-communities}

Vanaf AEM Communities 6.1 is een unieke aanpak gekozen voor de verwerking van door gebruikers gegenereerde inhoud (UGC) die door sitebezoekers (leden) uit de publicatieomgeving is ingediend.

Deze benadering is fundamenteel verschillend van de manier het AEM platform plaatsinhoud behandelt die over het algemeen van het auteursmilieu wordt beheerd.

Het AEM platform gebruikt een knoopopslag die site-inhoud van auteur voor publicatie repliceert, terwijl AEM Communities één algemene opslag voor UGC gebruikt die nooit wordt gerepliceerd.

Voor de gemeenschappelijke opslag UGC, is het noodzakelijk om een [Storage Resource Provider (SRP)](working-with-srp.md). De aanbevolen opties zijn:

* [DSRP - Relational Database Storage Resource Provider](dsrp.md)
* [MSRP - MongoDB Storage Resource Provider](msrp.md)
* [ASRP - Adobe Storage Resource Provider](asrp.md)

Een andere SRP-optie [JSRP - JCR Storage Resource Provider](jsrp.md), biedt geen ondersteuning voor een algemene UGC-opslag voor de auteur- en publicatieomgeving voor beide toegang.

Het vereisen van een gemeenschappelijke opslagresultaten in de volgende geadviseerde topologieën.

>[!NOTE]
>
>Voor AEM Communities: [UGC wordt nooit herhaald](working-with-srp.md#ugc-never-replicated).
>
>Wanneer de implementatie geen [gemeenschappelijk archief](working-with-srp.md), is UGC alleen zichtbaar op de AEM publicatie- of auteurinstantie waarop het is ingevoerd.
>

>[!NOTE]
>
>Ga voor meer informatie over het AEM [Aanbevolen implementaties](../../help/sites-deploying/recommended-deploys.md) en [Inleiding tot het AEM Platform](../../help/sites-deploying/data-store-config.md).

## Voor productie {#for-production}

Het is van essentieel belang een gemeenschappelijke opslag voor UGC tot stand te brengen, en daarom is de onderliggende implementatie afhankelijk van zijn capaciteit om een gemeenschappelijke opslag te steunen.

Twee voorbeelden:

1. Als het verwachte volume van UGC hoog is en een lokale instantie MongoDB mogelijk is, dan zou de keus zijn [MSRP](msrp.md).

1. Voor optimale prestaties voor pagina-inhoud kiest u een [publicatiebedrijf](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) en [ASRP](asrp.md) zou zorgen voor een optimale schaling van UGC met relatief eenvoudige bewerkingen.

Voor beide, kan de plaatsing op om het even welke OAK microkernel worden gebaseerd.

Houd zorgvuldig rekening met het unieke [kenmerken](working-with-srp.md#characteristics-of-srp-options) van elk.

Ga voor meer informatie over eiken microkorrels naar [Aanbevolen implementaties](../../help/sites-deploying/recommended-deploys.md).

### TarMK Publish Farm {#tarmk-publish-farm}

Wanneer de topologie publiceer landbouwbedrijf is, zijn de relevante onderwerpen van belang:

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

### Aanbevolen: DSRP, MSRP of ASRP {#recommended-dsrp-msrp-or-asrp}

| MicroKernel | SITE-INHOUD | DOOR GEBRUIKER GEGENEREERDE INHOUD | OPSLAGRESOUREUVERLENER | ALGEMENE OPSLAG |
|-------------|------------------------|----------------------------------|---------------------------|---------------|
| alle | JCR | MySQL | DSRP | Ja |
| alle | JCR | MongoDB | MSRP | Ja |
| alle | JCR | Adobe op verzoek | ASRP | Ja |

### JSRP {#jsrp}


| Implementatie | SITE-INHOUD | DOOR GEBRUIKER GEGENEREERDE INHOUD | OPSLAGRESOUREUVERLENER | ALGEMENE OPSLAG |
|----------------------|------------------------|----------------------------------|---------------------------|---------------------------------|
| TarMK Farm (standaard) | JCR | JCR | JSRP | Nee |
| Eak-cluster | JCR | JCR | JSRP | Alleen voor publicatie-omgeving |

## Voor ontwikkeling {#for-development}

Voor niet-productieomgevingen [JSRP](jsrp.md) biedt eenvoud bij het instellen van een ontwikkelomgeving met één auteurinstantie en één publicatie-instantie.

Als u [ASRP](asrp.md), [DSRP](dsrp.md) of [MSRP](msrp.md) voor productie is het ook mogelijk om een vergelijkbare ontwikkelomgeving in te stellen met behulp van Adobe on-demand-opslag of MongoDB. Zie voor een voorbeeld [MongoDB voor demo instellen](demo-mongo.md).

## Verwijzingen {#references}

* [Gebruikerssynchronisatie](sync.md)

  Bespreekt scynchronisatie van gebruikersgegevens onder publiceer landbouwbedrijfinstanties.

* [Gebruikers en gebruikersgroepen beheren](users.md)

  Bespreekt de rollen van gebruikers en gebruikersgroepen in de auteur en publicatiemilieu&#39;s.

* UGC [gemeenschappelijk archief](working-with-srp.md)

  Beschrijft de opslag van communautaire inhoud afzonderlijk van plaatsinhoud.

* [Node Stores and Data Stores](../../help/sites-deploying/data-store-config.md)

  Inhoud van de site wordt in feite opgeslagen in een nodenarchief. Voor Middelen, kan een gegevensopslag worden gevormd om binaire gegevens op te slaan. Voor Gemeenschappen, moet een gemeenschappelijke opslag worden gevormd om SRP te selecteren.

* [Opslagelementen](../../help/sites-deploying/storage-elements-in-aem-6.md)

  Beschrijft de twee implementaties van de knoopopslag: Tar en MongoDB.
