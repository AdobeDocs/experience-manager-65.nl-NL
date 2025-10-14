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

Voor de gemeenschappelijke opslag UGC, is het noodzakelijk om de leverancier van het a [&#x200B; opslagmiddel (SRP) &#x200B;](working-with-srp.md) te kiezen. De aanbevolen opties zijn:

* [DSRP - Relational Database Storage Resource Provider](dsrp.md)
* [MSRP - MongoDB Storage Resource Provider](msrp.md)
* [ASRP - Adobe Storage Resource Provider](asrp.md)

Één andere optie SRP, [&#x200B; JSRP - Leverancier van het Middel van de Opslag JCR &#x200B;](jsrp.md), steunt geen gemeenschappelijke opslag UGC voor de auteur en publiceert milieu&#39;s aan beide toegang.

Het vereisen van een gemeenschappelijke opslagresultaten in de volgende geadviseerde topologieën.

>[!NOTE]
>
>Voor AEM Communities, [&#x200B; UGC wordt nooit herhaald &#x200B;](working-with-srp.md#ugc-never-replicated).
>
>Wanneer de plaatsing niet a [&#x200B; gemeenschappelijke opslag &#x200B;](working-with-srp.md) omvat, zal UGC slechts op AEM zichtbaar zijn publiceert of auteursinstantie waarop het was ingegaan.
>

>[!NOTE]
>
>Voor meer informatie over het AEM platform, zie [&#x200B; Geadviseerde Inzet &#x200B;](../../help/sites-deploying/recommended-deploys.md) en [&#x200B; Inleiding aan het AEM Platform &#x200B;](../../help/sites-deploying/data-store-config.md).

## Voor productie {#for-production}

Het is van essentieel belang een gemeenschappelijke opslag voor UGC tot stand te brengen, en daarom is de onderliggende implementatie afhankelijk van zijn capaciteit om een gemeenschappelijke opslag te steunen.

Twee voorbeelden:

1. Als het verwachte volume van UGC hoog is en een lokale instantie MongoDB mogelijk is, dan zou de keus [&#x200B; MSRP &#x200B;](msrp.md) zijn.

1. Voor optimale prestaties voor paginacontent, publiceert de keus van a [&#x200B; landbouwbedrijf &#x200B;](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) en [&#x200B; ASRP &#x200B;](asrp.md) optimale het schrapen van UGC met vrij ongecompliceerde verrichtingen.

Voor beide toepassingen kan de implementatie op elke OAK-microkernel zijn gebaseerd.

Om de aangewezen gemeenschappelijke opslag te kiezen, overweeg zorgvuldig de unieke [&#x200B; kenmerken &#x200B;](working-with-srp.md#characteristics-of-srp-options) van elk.

Voor meer details op de microkoralen van Oak, bezoek [&#x200B; Geadviseerde Plaatsingen &#x200B;](../../help/sites-deploying/recommended-deploys.md).

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
| Oak Cluster | JCR | JCR | JSRP | Alleen voor publicatie-omgeving |

## Voor ontwikkeling {#for-development}

Voor niet-productiemilieu&#39;s, [&#x200B; JSRP &#x200B;](jsrp.md) verstrekt eenvoud in vestiging een ontwikkelomgeving met één auteursinstantie en één publiceer instantie.

Als het kiezen van [&#x200B; ASRP &#x200B;](asrp.md), [&#x200B; DSRP &#x200B;](dsrp.md) of [&#x200B; MSRP &#x200B;](msrp.md) voor productie, is het ook mogelijk om een gelijkaardige ontwikkelomgeving te plaatsen gebruikend Adobe op bestelling opslag of MongoDB. Voor een voorbeeld, zie [&#x200B; HowTo Opstelling MongoDB voor Manifestatie &#x200B;](demo-mongo.md).

## Verwijzingen {#references}

* [Gebruikerssynchronisatie](sync.md)

  Bespreekt scynchronisatie van gebruikersgegevens onder publiceer landbouwbedrijfinstanties.

* [Gebruikers en gebruikersgroepen beheren](users.md)

  Bespreekt de rollen van gebruikers en gebruikersgroepen in de auteur en publicatiemilieu&#39;s.

* UGC [&#x200B; gemeenschappelijke opslag &#x200B;](working-with-srp.md)

  Beschrijft de opslag van communautaire inhoud afzonderlijk van plaatsinhoud.

* [Node Stores and Data Stores](../../help/sites-deploying/data-store-config.md)

  Inhoud van de site wordt in feite opgeslagen in een nodenarchief. Voor Assets, kan een gegevensopslag worden gevormd om binaire gegevens op te slaan. Voor Gemeenschappen, moet een gemeenschappelijke opslag worden gevormd om SRP te selecteren.

* [Opslagelementen](../../help/sites-deploying/storage-elements-in-aem-6.md)

  Beschrijft de twee implementaties van de knoopopslag: Tar en MongoDB.
