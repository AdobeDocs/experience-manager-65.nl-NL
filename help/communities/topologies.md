---
title: Aanbevolen topologieën voor Gemeenschappen
seo-title: Aanbevolen topologieën voor Gemeenschappen
description: Hoe te om de behandeling van user-generated inhoud (UGC) te benaderen
seo-description: Hoe te om de behandeling van user-generated inhoud (UGC) te benaderen
uuid: 4bc1c423-0ba9-4f2e-b11c-4d6824f45641
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
content-type: reference
topic-tags: deploying
discoiquuid: 46f135de-a0bf-451d-bdcc-fb29188250aa
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '562'
ht-degree: 0%

---


# Aanbevolen topologieën voor gemeenschappen {#recommended-topologies-for-communities}

Vanaf AEM Communities 6.1 is een unieke aanpak gekozen voor de verwerking van door gebruikers gegenereerde inhoud (UGC) die door sitebezoekers (leden) uit de publicatieomgeving is ingediend.

Deze benadering is fundamenteel verschillend van de manier het AEM platform plaatsinhoud behandelt die over het algemeen van het auteursmilieu wordt beheerd.

Het AEM platform gebruikt een knoopopslag die site-inhoud van auteur voor publicatie repliceert, terwijl AEM Communities één algemene opslag voor UGC gebruikt die nooit wordt gerepliceerd.

Voor de gemeenschappelijke opslag UGC, is het noodzakelijk om een [leverancier van het opslagmiddel (SRP)](working-with-srp.md) te kiezen. De aanbevolen opties zijn:

* [DSRP - Relational Database Storage Resource Provider](dsrp.md)
* [MSRP - MongoDB Storage Resource Provider](msrp.md)
* [ASRP - Adobe Storage Resource Provider](asrp.md)

Een andere SRP-optie, [JSRP - JCR Storage Resource Provider](jsrp.md), ondersteunt geen gemeenschappelijke UGC-opslag voor de auteur- en publicatieomgevingen voor beide toegang.

Het vereisen van een gemeenschappelijke opslagresultaten in de volgende geadviseerde topologieën.

>[!NOTE]
>
>Voor AEM Communities wordt [UGC nooit gerepliceerd](working-with-srp.md#ugc-never-replicated).
>
>Wanneer de implementatie geen [common store](working-with-srp.md) bevat, is UGC alleen zichtbaar op de AEM publicatie- of auteurinstantie waarop deze is ingevoerd.


>[!NOTE]
>
>Zie [Aanbevolen implementaties](../../help/sites-deploying/recommended-deploys.md) en [Inleiding tot het AEM Platform](../../help/sites-deploying/data-store-config.md) voor meer informatie over het AEM platform.

## Voor productie {#for-production}

Het is van essentieel belang een gemeenschappelijke opslag voor UGC tot stand te brengen, en daarom is de onderliggende implementatie afhankelijk van zijn capaciteit om een gemeenschappelijke opslag te steunen.

Twee voorbeelden:

1. Als het verwachte volume van UGC hoog is en een lokale instantie MongoDB mogelijk is, dan zou de keus [MSRP](msrp.md) zijn.

1. Voor optimale prestaties voor paginainhoud, zou de keus van [publiceer landbouwbedrijf](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) en [ASRP](asrp.md) het optimale schrapen van UGC met vrij ongecompliceerde verrichtingen verstrekken.

Voor beide, kan de plaatsing op om het even welke OAK microkernel worden gebaseerd.

Om de aangewezen gemeenschappelijke opslag te kiezen, zorgvuldig overweeg de unieke [kenmerken](working-with-srp.md#characteristics-of-srp-options) van elk.

Voor meer informatie over eiken microkorrels, bezoek [Aanbevolen Plaatsingen](../../help/sites-deploying/recommended-deploys.md).

### TarMK Publish Farm {#tarmk-publish-farm}

Wanneer de topologie publiceer landbouwbedrijf is, zijn de relevante onderwerpen van belang:

* [Gebruikerssynchronisatie](sync.md)
* [Gebruikers en gebruikersgroepen beheren](users.md)

### Aanbevolen: DSRP, MSRP of ASRP {#recommended-dsrp-msrp-or-asrp}

| MicroKernel | SITE-INHOUD | DOOR GEBRUIKER GEGENEREERDE INHOUD | OPSLAGRESOUREUVERLENER | ALGEMENE OPSLAG |
|-------------|------------------------|----------------------------------|---------------------------|---------------|
| alle | JCR | MySQL | DSRP | Ja |
| alle | JCR | MongoDB | MSRP | Ja |
| alle | JCR | Adobe on-demand-opslag | ASRP | Ja |

### JSRP {#jsrp}


| Implementatie | SITE-INHOUD | DOOR GEBRUIKER GEGENEREERDE INHOUD | OPSLAGRESOUREUVERLENER | ALGEMENE OPSLAG |
|----------------------|------------------------|----------------------------------|---------------------------|---------------------------------|
| TarMK Farm (standaard) | JCR | JCR | JSRP | Nee |
| Eak-cluster | JCR | JCR | JSRP | Alleen voor publicatie-omgeving |

## Voor ontwikkeling {#for-development}

Voor niet-productieomgevingen biedt [JSRP](jsrp.md) eenvoud bij het instellen van een ontwikkelomgeving met één auteurinstantie en één publicatieinstantie.

Als u [ASRP](asrp.md), [DSRP](dsrp.md) of [MSRP](msrp.md) voor productie kiest, is het ook mogelijk om een gelijkaardige ontwikkelomgeving te installeren gebruikend Adobe op bestelling opslag of MongoDB. Voor een voorbeeld, zie [HowTo Opstelling MongoDB voor Demo](demo-mongo.md).

## Verwijzingen {#references}

* [Gebruikerssynchronisatie](sync.md)

   Bespreekt scynchronisatie van gebruikersgegevens onder publiceer landbouwbedrijfinstanties.

* [Gebruikers en gebruikersgroepen beheren](users.md)

   Bespreekt de rollen van gebruikers en gebruikersgroepen in de auteur en publicatiemilieu&#39;s.

* UGC [common store](working-with-srp.md)

   Beschrijft de opslag van communautaire inhoud afzonderlijk van plaatsinhoud.

* [Node Stores and Data Stores](../../help/sites-deploying/data-store-config.md)

   Inhoud van de site wordt in feite opgeslagen in een nodenarchief. Voor Middelen, kan een gegevensopslag worden gevormd om binaire gegevens op te slaan. Voor Gemeenschappen, moet een gemeenschappelijke opslag worden gevormd om SRP te selecteren.

* [Opslagelementen in AEM 6.3](../../help/sites-deploying/storage-elements-in-aem-6.md)

   Beschrijft de twee implementaties van de knoopopslag: Tar en MongoDB.
