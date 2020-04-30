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
source-git-commit: 77d00c1d6e94b257aa0533ca88b5f9a12dba0054

---


# Aanbevolen topologieën voor Gemeenschappen {#recommended-topologies-for-communities}

Vanaf AEM Communities 6.1 is een unieke aanpak gekozen voor de verwerking van door gebruikers gegenereerde inhoud (UGC) die door sitebezoekers (leden) uit de publicatieomgeving is ingediend.

Deze benadering is fundamenteel verschillend van de manier het platform AEM plaatsinhoud behandelt die over het algemeen van het auteursmilieu wordt beheerd.

Het AEM-platform gebruikt een knooppuntenarchief dat site-inhoud van auteur dupliceert om te publiceren, terwijl AEM-gemeenschappen één algemene opslag voor UGC gebruiken die nooit wordt gerepliceerd.

Voor de gemeenschappelijke opslag UGC, is het noodzakelijk om een leverancier van het [opslagmiddel (SRP)](working-with-srp.md)te kiezen. De aanbevolen opties zijn:

* [DSRP - Relational Database Storage Resource Provider](dsrp.md)
* [MSRP - MongoDB Storage Resource Provider](msrp.md)
* [ASRP - Adobe Storage Resource Provider](asrp.md)

Een andere SRP-optie, [JSRP - JCR Storage Resource Provider](jsrp.md), ondersteunt geen algemene UGC-opslag voor de auteur- en publicatieomgevingen voor beide toegang.

Het vereisen van een gemeenschappelijke opslagresultaten in de volgende geadviseerde topologieën.

>[!NOTE]
>
>Voor AEM-gemeenschappen wordt [UGC nooit gerepliceerd](working-with-srp.md#ugc-never-replicated).
>
>Wanneer de plaatsing geen [gemeenschappelijke opslag](working-with-srp.md)omvat, zal UGC slechts op publiceren AEM of auteursinstantie zichtbaar zijn waarop het was ingegaan.


>[!NOTE]
>
>Voor meer informatie over het platform AEM, zie [Aanbevolen Plaatsingen](../../help/sites-deploying/recommended-deploys.md) en [Inleiding aan het Platform](../../help/sites-deploying/data-store-config.md)AEM.


## Voor productie {#for-production}

Het is van essentieel belang een gemeenschappelijke opslag voor UGC tot stand te brengen, en daarom is de onderliggende implementatie afhankelijk van zijn capaciteit om een gemeenschappelijke opslag te steunen.

Twee voorbeelden:

1. Als het verwachte volume van UGC hoog is en een lokale instantie MongoDB mogelijk is, dan zou de keus [MSRP](msrp.md)zijn.

1. Voor optimale prestaties voor paginacontent, zou de keus van een [publicatiecentrum](../../help/sites-deploying/recommended-deploys.md#tarmk-farm) en [ASRP](asrp.md) optimale schrapping van UGC met vrij ongecompliceerde verrichtingen verstrekken.

Voor beide, kan de plaatsing op om het even welke OAK microkernel worden gebaseerd.

Houd zorgvuldig rekening met de unieke [kenmerken](working-with-srp.md#characteristics-of-srp-options) van elke winkel om de juiste gemeenschappelijke opslagplaats te kiezen.

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

Voor non-production milieu&#39;s, verstrekt [JSRP](jsrp.md) eenvoud in vestiging een ontwikkelomgeving met één auteursinstantie en één publicatieinstantie.

Als u [ASRP](asrp.md), [DSRP](dsrp.md) of [MSRP](msrp.md) kiest voor productie, is het ook mogelijk om een vergelijkbare ontwikkelomgeving in te stellen met behulp van Adobe on-demand-opslag of MongoDB. Voor een voorbeeld, zie [hoe te MongoDB voor Demo](demo-mongo.md)plaatsen.

## Verwijzingen {#references}

* [Gebruikerssynchronisatie](sync.md)

   Bespreekt scynchronisatie van gebruikersgegevens onder publiceer landbouwbedrijfinstanties.

* [Gebruikers en gebruikersgroepen beheren](users.md)

   Bespreekt de rollen van gebruikers en gebruikersgroepen in de auteur en publicatiemilieu&#39;s.

* UGC [Common Store](working-with-srp.md)

   Beschrijft de opslag van communautaire inhoud afzonderlijk van plaatsinhoud.

* [Node Stores and Data Stores](../../help/sites-deploying/data-store-config.md)

   Inhoud van de site wordt in feite opgeslagen in een nodenarchief. Voor Middelen, kan een gegevensopslag worden gevormd om binaire gegevens op te slaan. Voor Gemeenschappen, moet een gemeenschappelijke opslag worden gevormd om SRP te selecteren.

* [Opslagelementen in AEM 6.3](../../help/sites-deploying/storage-elements-in-aem-6.md)

   Beschrijft de twee implementaties van de knoopopslag: Tar en MongoDB.
