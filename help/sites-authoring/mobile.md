---
title: Een inhoudspagina voor mobiele apparaten ontwerpen
description: Wanneer het ontwerpen voor mobiel, kunt u tussen verscheidene mededingers schakelen om te zien wat de eindgebruiker ziet.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: 9c6c6386-5ffd-4fa6-9aa1-f5b0e31d1046
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '226'
ht-degree: 0%

---

# Een pagina ontwerpen voor mobiele apparaten{#authoring-a-page-for-mobile-devices}

Wanneer u een mobiele pagina ontwerpt, wordt de pagina weergegeven op een manier die het mobiele apparaat emuleert. Wanneer u de pagina ontwerpt, kunt u schakelen tussen verschillende emulators om te zien wat de eindgebruiker ziet wanneer hij of zij de pagina opent.

Apparaten worden gegroepeerd in de categoriefunctie, de functie voor slim afdrukken en de functie voor aanraken op basis van de mogelijkheden van de apparaten om een pagina weer te geven. Wanneer de eindgebruiker tot een mobiele pagina toegang heeft, AEM ontdekt het apparaat en verzendt de vertegenwoordiging die aan zijn apparatengroep beantwoordt.

>[!NOTE]
>
>Als u een mobiele site wilt maken op basis van een bestaande standaardsite, maakt u een live kopie van de standaardsite. (Zie [ Creërend Levend Exemplaar voor Verschillende Kanalen ](/help/sites-administering/msm-livecopy.md).)
>
>AEM ontwikkelaars kunnen nieuwe apparaatgroepen maken. (Zie [ Creërend de Filters van de Groep van het Apparaat ](/help/sites-developing/groupfilters.md).)

Gebruik de volgende procedure om een mobiele pagina te ontwerpen:

1. Van globale navigatie open de **console van Plaatsen**.
1. Open de pagina **Wij.Retail** > **Verenigde Staten** > **Engels**.

1. Schakelaar aan **wijze van de Voorproef**.
1. Schakel over naar de gewenste emulator door op het apparaatpictogram boven aan de pagina te klikken.
1. Sleep componenten van de componentbrowser naar de pagina.

De pagina ziet er ongeveer als volgt uit:

![ mobileipademu ](assets/mobileipademu.png)

>[!NOTE]
>
>De emulators worden uitgeschakeld wanneer een pagina op de auteurinstantie wordt opgevraagd bij een mobiel apparaat.
