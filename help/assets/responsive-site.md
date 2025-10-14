---
title: Geoptimaliseerde afbeeldingen voor een responsieve site leveren
description: De functie voor responsieve code gebruiken om geoptimaliseerde afbeeldingen te leveren
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
feature: Asset Management
role: User, Admin
exl-id: 753d806f-5f44-4d73-a3a3-a2a0fc3e154b
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '330'
ht-degree: 8%

---

# Geoptimaliseerde afbeeldingen leveren voor een responsieve site {#delivering-optimized-images-for-a-responsive-site}

Gebruik de functie Responsieve code wanneer u de code wilt delen voor responsieve functies in uw webontwikkelaar. U kopieert de responsieve code (**[!UICONTROL RESS]**) naar het klembord zodat u deze kunt delen met de webontwikkelaar.

Deze functie is handig als uw website zich op een WCM van derden bevindt. Als uw website zich echter op Adobe Experience Manager bevindt, wordt de afbeelding door een externe afbeeldingsserver gerenderd en aan de webpagina geleverd.

Zie ook [&#x200B; bed de VideoKijker op een Web-pagina &#x200B;](embed-code.md) in.

Zie ook [&#x200B; Verbinding URLs aan uw Toepassing van het Web &#x200B;](linking-urls-to-yourwebapplication.md).

**om geoptimaliseerde beelden voor een ontvankelijke plaats te leveren:**

1. Navigeer naar de afbeelding waarvoor u responsieve code wilt opgeven en selecteer **[!UICONTROL Renditions]** in het keuzemenu.

   ![&#x200B; chlimage_1-408 &#x200B;](assets/chlimage_1-408.png)

1. Selecteer een responsieve voorinstelling voor de afbeelding. De knoppen **[!UICONTROL URL]** en **[!UICONTROL RESS]** worden weergegeven.

   ![&#x200B; chlimage_1-409 &#x200B;](assets/chlimage_1-208.png)

   >[!NOTE]
   >
   >De geselecteerde asset *en* de geselecteerde afbeeldings- of viewervoorinstelling moeten worden gepubliceerd om de knoppen **[!UICONTROL URL]** of **[!UICONTROL RESS]** beschikbaar te maken.
   >
   >Dynamic Media - Voor de hybride modus moet u voorinstellingen voor afbeeldingen publiceren. In de modus Dynamic Media - Scene7 worden automatisch voorinstellingen voor afbeeldingen gepubliceerd.

1. Selecteer **[!UICONTROL RESS]** .

   ![&#x200B; chlimage_1-410 &#x200B;](assets/chlimage_1-410.png)

1. Selecteer in het dialoogvenster **[!UICONTROL Embed Responsive Image]** de tekst van de responsieve code, kopieer deze en plak deze in uw website om het responsieve element te openen.
1. Bewerk de standaardonderbrekingspunten in de insluitcode zodat deze overeenkomen met de onderbrekingspunten van de responsieve website, rechtstreeks in de code. Test bovendien de verschillende afbeeldingsresoluties die op verschillende pagina-onderbrekingspunten worden weergegeven.

## HTTP/2 gebruiken om uw Dynamic Media-middelen te leveren {#using-http-to-delivery-your-dynamic-media-assets}

HTTP/2 is het nieuwe, bijgewerkte webprotocol dat de manier verbetert waarop browsers en servers communiceren. Het zorgt voor een snellere overdracht van informatie en vermindert de hoeveelheid verwerkingskracht die nodig is. De levering van Dynamic Media-elementen wordt ondersteund met HTTP/2, dat betere responstijd en laadtijd biedt.

Zie [&#x200B; HTTP2 Levering van Inhoud &#x200B;](http2.md) voor volledige details bij het worden begonnen HTTP/2 met uw rekening van Dynamic Media te gebruiken.
