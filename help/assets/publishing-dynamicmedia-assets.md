---
title: Dynamic Media-middelen publiceren
description: Leer hoe u Dynamic Media-elementen, zoals video's en afbeeldingen, publiceert, inclusief de HTTP/2-levering van dergelijke elementen.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
role: User, Admin
exl-id: 750627fc-2a29-43ff-867e-55cb2e371043
feature: Publishing
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '468'
ht-degree: 2%

---

# Dynamic Media-elementen publiceren {#publishing-dynamic-media-assets}

U publiceert uw Dynamic Media-elementen door de elementen te selecteren die u al hebt geüpload en te tikken **[!UICONTROL Publish]** of **[!UICONTROL Quick Publish]**. Nadat uw Dynamic Media-elementen zijn gepubliceerd, kunt u ze via een URL in een webpagina opnemen of door de code in te sluiten op de webpagina.

U kunt ook direct elementen publiceren die u uploadt, zonder tussenkomst van de gebruiker. Zie [Dynamic Media configureren - Scene7-modus](config-dms7.md).
Of u kunt selectief elementen publiceren naar Dynamic Media of Adobe Experience Manager, wederzijds exclusief elkaar, met behulp van **[!UICONTROL Selective Publish]** op mapniveau. Zie [Werken met Selectieve publicatie in Dynamic Media](/help/assets/selective-publishing.md).

In de **[!UICONTROL Card View]**, wordt een klein globpictogram direct onder de naam van een element weergegeven en links van de datum en tijd om aan te geven dat het element is gepubliceerd. In de **[!UICONTROL List View]** geeft een kolom **[!UICONTROL Published]** aan welke assets zijn gepubliceerd en welke niet.

>[!NOTE]
>
>Als een element al is gepubliceerd, gebruikt u Experience Manager om het element naar een andere map te verplaatsen en opnieuw te publiceren vanaf de nieuwe locatie. De oorspronkelijke locatie van de gepubliceerde middelen is nog steeds beschikbaar, samen met het nieuwe, opnieuw gepubliceerde middel. Het oorspronkelijke gepubliceerde middel is echter &quot;verloren&quot; voor de Experience Manager en kan niet ongepubliceerd worden. Daarom is het aan te raden eerst de publicatie van elementen ongedaan te maken voordat u deze naar een andere map verplaatst.

Als u video-elementen direct na het coderen wilt publiceren, moet u ervoor zorgen dat het coderen is voltooid. Tijdens het coderen van video&#39;s wordt op het systeem gemeld dat er een videoverwerkingsworkflow wordt uitgevoerd. Wanneer videocodering is voltooid, kunt u een voorvertoning van de video-uitvoeringen bekijken. Op dat moment kunt u de video&#39;s veilig publiceren zonder publicatiefouten te maken.

Zie ook [URL&#39;s koppelen aan uw webtoepassing](linking-urls-to-yourwebapplication.md).

Zie ook [De Dynamic Media Video- of Image-viewer insluiten op een webpagina](embed-code.md)

>[!NOTE]
>
>* Elementen moeten worden gepubliceerd om de URL te kunnen gebruiken. Als de elementen niet worden gepubliceerd, werkt het kopiëren en plakken van de URL in een webbrowser niet.
>* Voorinstellingen voor afbeeldingen en viewervoorinstellingen moeten worden geactiveerd en gepubliceerd voor live levering.
>

Ga voor gedetailleerde informatie over het publiceren van een set of element naar [Elementen publiceren](manage-assets.md).

## HTTP/2 levering van Dynamic Media-middelen {#http-delivery-of-dynamic-media-assets}

Experience Manager ondersteunt nu de levering van alle Dynamic Media-inhoud (afbeeldingen en video) via HTTP/2. Dit wil zeggen dat er een gepubliceerde URL of insluitcode voor de afbeelding of video beschikbaar is om te worden geïntegreerd met elke toepassing die een gehoste element accepteert. Dat gepubliceerde element wordt vervolgens geleverd via het HTTP/2-protocol. Deze leveringsmethode verbetert de manier waarop browsers en servers communiceren, waardoor u betere responstijd en laadtijden voor al uw Dynamic Media-middelen krijgt.

Zie voor meer informatie [HTTP/2 levering van inhoud vaak gestelde vragen](/help/sites-administering/scene7-http2faq.md).
