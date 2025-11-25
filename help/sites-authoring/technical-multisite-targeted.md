---
title: Hoe multisite beheer voor gerichte inhoud is gestructureerd
description: Een diagram toont hoe multisite steun voor gerichte inhoud gestructureerd is
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
exl-id: d8ba91ff-ad6e-4540-baff-a2c0c764a299
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Hoe multisite beheer voor gerichte inhoud is gestructureerd{#how-multisite-management-for-targeted-content-is-structured}

Het volgende diagram toont hoe multisite steun voor gerichte inhoud gestructureerd is.

Gebieden verschijnen onder **/content/campagnes/&lt;brand>** en door gebrek heeft elk merk een hoofdgebied, dat automatisch wordt gecreeerd. Elk gebied bevat zijn eigen reeks activiteiten, ervaringen en aanbiedingen.

![&#x200B; chlimage_1-268 &#x200B;](assets/chlimage_1-268.png)

Om gerichte inhoud op te zoeken, kunnen de pagina&#39;s of de plaatsen aan een gebied in kaart brengen. Als er geen gebied is geconfigureerd, valt AEM terug naar het hoofdgebied voor dit specifieke merk.

Het volgende diagram is een voorbeeld van hoe de logica voor drie plaatsen, genoemd site1, site2, en site3 werkt.

![&#x200B; chlimage_1-269 &#x200B;](assets/chlimage_1-269.png)

* site1 zoekt myarea1 op merk1 en other area2 op merk2 op basis van gebiedstoewijzing.
* site2 zoekt myarea1 op voor merk1 en hoofdgebied voor merk2 omdat alleen de gebiedstoewijzing voor merk1 is gedefinieerd.
* site3 zoekt het hoofdgebied voor merk1 en merk2 op omdat er helemaal geen andere gebiedstoewijzing voor deze site is gedefinieerd.
