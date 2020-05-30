---
title: Dynamische media-elementen publiceren
description: Dynamische media-elementen publiceren
uuid: b1bee905-86cf-4284-8d4e-067e11557899
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
discoiquuid: 99d7025f-d022-4213-83c0-815a4712c573
translation-type: tm+mt
source-git-commit: b8fe3267a808f1a64b78620156826e0b6e3a5676
workflow-type: tm+mt
source-wordcount: '421'
ht-degree: 3%

---


# Publishing Dynamic Media Assets {#publishing-dynamic-media-assets}

U publiceert uw dynamische media-elementen door de elementen te selecteren die u al hebt geüpload en te tikken **[!UICONTROL Publish]** of **[!UICONTROL Quick Publish]**. Nadat uw dynamische media-elementen zijn gepubliceerd, zijn deze beschikbaar voor opname in een webpagina via een URL of door de code in te sluiten op de pagina.

U kunt ook direct elementen publiceren die u uploadt—zonder tussenkomst van de gebruiker. Zie het [Vormen Dynamische Media - wijze](config-dms7.md)Scene7.

In het **[!UICONTROL Card View]** gedeelte ziet u een klein globpictogram direct onder de naam van een element en links van de datum en tijd om aan te geven dat het is gepubliceerd. In de **[!UICONTROL List View]** geeft een kolom **[!UICONTROL Published]** aan welke assets zijn gepubliceerd en welke niet.

>[!NOTE]
>
>Als een element al is gepubliceerd, gebruikt u AEM om het element naar een andere map te verplaatsen en vanaf de nieuwe locatie opnieuw te publiceren, is de oorspronkelijke locatie van het gepubliceerde element nog steeds beschikbaar, samen met het opnieuw gepubliceerde element. Het oorspronkelijke gepubliceerde middel is echter &quot;verloren&quot; aan AEM en kan niet ongepubliceerd worden. Daarom is het aan te raden eerst de publicatie van elementen ongedaan te maken voordat u deze naar een andere map verplaatst.

Als u video-elementen direct na het coderen wilt publiceren, moet u ervoor zorgen dat de codering volledig is uitgevoerd. Wanneer video&#39;s nog steeds worden gecodeerd, wordt u via het systeem op de hoogte gebracht van een actieve workflow voor videoverwerking. Wanneer videocodering is voltooid, moet u een voorvertoning van de video-uitvoeringen kunnen bekijken. Op dat moment kunt u de video&#39;s veilig publiceren zonder publicatiefouten te maken.

See also [Linking URLs to your Web Application](linking-urls-to-yourwebapplication.md).

See also [Embedding the Dynamic Media Video or Image viewer on a web page](embed-code.md)

>[!NOTE]
>
>* Elementen moeten worden gepubliceerd om de URL te kunnen gebruiken. Als de elementen niet worden gepubliceerd, werkt het kopiëren en plakken van de URL in een webbrowser niet.
>* Voorinstellingen voor afbeeldingen en viewervoorinstellingen moeten worden geactiveerd en gepubliceerd voor live levering.
>



Zie Elementen [publiceren voor gedetailleerde informatie over het publiceren van een set of element.](managing-assets-touch-ui.md)

## HTTP/2-levering van Dynamic Media-elementen {#http-delivery-of-dynamic-media-assets}

AEM ondersteunt nu de levering van alle Dynamic Media-inhoud (afbeeldingen en video) via HTTP/2. Dit wil zeggen dat er een gepubliceerde URL of insluitcode voor de afbeelding of video beschikbaar is om te worden geïntegreerd met elke toepassing die een gehoste element accepteert. Dat gepubliceerde element wordt vervolgens geleverd via het HTTP/2-protocol. Deze methode van levering verbetert de manier browsers en servers communiceren, die voor betere reactie en ladingstijden van al uw Dynamische activa van Media toestaan.

Zie [HTTP/2 levering van inhoud vaak gestelde vragen](/help/sites-administering/scene7-http2faq.md) om meer te leren.
