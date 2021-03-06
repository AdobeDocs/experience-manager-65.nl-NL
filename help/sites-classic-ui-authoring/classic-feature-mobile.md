---
title: Een pagina ontwerpen voor mobiele apparaten
seo-title: Een pagina ontwerpen voor mobiele apparaten
description: Wanneer u een mobiele pagina ontwerpt, wordt de pagina weergegeven op een manier die het mobiele apparaat emuleert. Wanneer u de pagina ontwerpt, kunt u schakelen tussen verschillende emulators om te zien wat de eindgebruiker ziet wanneer hij of zij de pagina opent.
seo-description: Wanneer u een mobiele pagina ontwerpt, wordt de pagina weergegeven op een manier die het mobiele apparaat emuleert. Wanneer u de pagina ontwerpt, kunt u schakelen tussen verschillende emulators om te zien wat de eindgebruiker ziet wanneer hij of zij de pagina opent.
uuid: ca16979d-6e5f-444d-b959-ae92542039b2
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 430a27b5-f344-404f-8bf8-0d91b49b605e
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '340'
ht-degree: 0%

---


# Een pagina ontwerpen voor mobiele apparaten{#authoring-a-page-for-mobile-devices}

Wanneer u een mobiele pagina ontwerpt, wordt de pagina weergegeven op een manier die het mobiele apparaat emuleert. Wanneer u de pagina ontwerpt, kunt u schakelen tussen verschillende emulators om te zien wat de eindgebruiker ziet wanneer hij of zij de pagina opent.

Apparaten worden gegroepeerd in de categoriefunctie, de functie voor slim afdrukken en de functie voor aanraken op basis van de mogelijkheden van de apparaten om een pagina weer te geven. Wanneer de eindgebruiker tot een mobiele pagina toegang heeft, AEM ontdekt het apparaat en verzendt de vertegenwoordiging die aan zijn apparatengroep beantwoordt.

>[!NOTE]
>
>Als u een mobiele site wilt maken op basis van een bestaande standaardsite, maakt u een live kopie van de standaardsite. (Zie [Een actieve kopie maken voor verschillende kanalen](/help/sites-administering/msm-livecopy.md).)
>
>AEM ontwikkelaars kunnen nieuwe apparaatgroepen maken. (Zie [Apparaatgroepfilters maken.](/help/sites-developing/groupfilters.md))

Gebruik de volgende procedure om een mobiele pagina te ontwerpen:

1. Ga in uw browser naar de **Siteadmin**-console.
1. Open de pagina **Products** onder **Websites** > **Geometrixx Mobile Demo Site** > **English**.

1. Schakel over naar een andere emulator. Hiervoor kunt u:

   * Klik op het apparaatpictogram boven aan de pagina.
   * Klik op de knop **Bewerken** in **Sidetrap** en selecteer het apparaat in het keuzemenu.

1. Sleep de component **Tekst en afbeelding** van het tabblad Mobiel van de Sidetrap naar de pagina.
1. Bewerk de component en voeg wat tekst toe. Klik **OK** om de wijzigingen op te slaan.

De pagina ziet er hetzelfde uit als:

![mobileipademu](assets/mobileipademu.png)

>[!NOTE]
>
>De emulators worden uitgeschakeld wanneer een pagina op de auteurinstantie wordt opgevraagd bij een mobiel apparaat. U kunt ontwerpen met behulp van de interface met aanraakbediening.

