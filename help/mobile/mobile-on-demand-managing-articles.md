---
title: Artikelen beheren
seo-title: Managing Articles
description: Volg deze pagina voor meer informatie over het maken en beheren van artikelen.
seo-description: Follow this page to learn about creating and managing Articles.
uuid: 72b86cd7-3016-41b6-a001-9dce4084e9db
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-on-demand-services-app
discoiquuid: b46058f9-4691-4fba-a656-0f8507875a79
exl-id: ea6c8aa3-f86e-4878-8550-fe1662f10696
source-git-commit: 259f257964829b65bb71b5a46583997581a91a4e
workflow-type: tm+mt
source-wordcount: '679'
ht-degree: 0%

---

# Artikelen beheren{#managing-articles}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework nodig hebben (bijvoorbeeld Reageren). [Meer informatie](/help/sites-developing/spa-overview.md).

De acties van het Beheer van de inhoud zijn de bouwstenen die helpen om artikelen binnen een toepassing tot stand te brengen en te beheren. De volgende handelingen worden uitgevoerd op artikelen in de toepassing.

## Artikeloverzicht {#articles-overview}

Artikelen vertegenwoordigen de tekst die samen met illustraties wordt gebaseerd om informatie over te brengen.

>[!NOTE]
>
>Zie de volgende bronnen in de online Help voor meer informatie over de volgende onderwerpen in AEM Mobile-apps:
>
>* [Ontwerpaspecten](https://helpx.adobe.com/digital-publishing-solution/help/design-app.html)
>
>* [Artikelen beheren](https://helpx.adobe.com/digital-publishing-solution/help/creating-articles.html)
>

## Een artikel maken {#creating-an-article}

De algemene workflow voor het maken van een artikel is als volgt:

1. Selecteren **Mobiel** van de zijspoor.
1. Kies vanuit Mobiel uw mobiele On-Demand-app in de catalogus.
1. Klik op de pijl omlaag in de rechterbovenhoek van het dialoogvenster **Artikelen beheren** tegel.
1. Kies een artikelsjabloon en klik op **Volgende**.
1. Werk door elke stap van de wizard om door te gaan met het maken van uw nieuwe artikel.
1. Klik, indien gereed, op **Maken**.
1. Uw nieuwe artikel wordt weergegeven in het dialoogvenster **Artikelen beheren** tegel.

## Een nieuw artikel importeren {#importing-a-new-article}

Bestaande mobiele on-demand-inhoud kan worden gedownload (geïmporteerd) van Mobile On-Demand naar AEM. Zo kunt u lokale inhoud bewerken en weergeven.

>[!NOTE]
>
>Bij het importeren worden geen afbeeldingen opgenomen.

De workflow voor het importeren van een nieuw artikel

1. Kies vanuit Mobiel uw mobiele On-Demand-app in de catalogus.
1. Klik op de pijl omlaag in de rechterbovenhoek van het dialoogvenster **Artikelen beheren** tegel en selecteer Artikelen importeren.
1. Klikken **Artikelen importeren** in het dialoogvenster en vervolgens Sluiten.
1. Uw mobiele On-Demand-artikelen worden nu weergegeven in de **Artikelen beheren** tegel.

>[!CAUTION]
>
>U moet eerst een mobiele On-Demand-verbinding koppelen.

![chlimage_1-3](assets/chlimage_1-3.gif)

## Een artikel bewerken {#editing-an-article}

Met de ingebouwde AEM slepen en neerzetten-editor kunt u een artikel toevoegen of wijzigen. Componenten zoals tekst en afbeeldingen kunnen worden toegevoegd of verwijderd. U kunt afbeeldingen van DAM-middelen invoegen.

>[!CAUTION]
>
>Alleen artikelen die zijn gemaakt in AEM kunnen worden geopend in de editor.

De workflow voor het bewerken van een artikel:

1. Kies vanuit Mobiel uw mobiele On-Demand-app in de catalogus.
1. Selecteer een AEM artikel in het menu **Artikelen beheren** tegel.
1. Klik op het gemarkeerde artikel in de lijstweergave om het te openen in de inhoudseditor.
1. Gebruik de inhoudeditor om artikelinhoud (manuscripten, afbeeldingen, tekst, enz.) te slepen.

### De metagegevens weergeven en bewerken in een artikel {#viewing-and-editing-the-metadata-within-an-article}

Inhoud zoals artikelen, banners, enz. heeft talrijke eigenschappen, zoals titels, beschrijvingen, afbeeldingen. Deze handeling wordt gebruikt om dergelijke eigenschappen weer te geven en te wijzigen. Deze wijzigingen kunnen optioneel worden geüpload naar Mobile On-Demand tijdens het opslaan.

De algemene workflow voor het weergeven/bewerken van een artikel:

1. Kies vanuit Mobiel uw mobiele On-Demand-app in de catalogus.
1. Kies een artikel in het menu **Artikelen beheren** tegel.

1. Selecteren **Eigenschappen weergeven** in de actiebalk.
1. Alle beschikbare metagegevens voor dat artikel weergeven.
1. Bewerk desgewenst de metagegevens en klik op **Opslaan** wanneer gereed.
1. U kunt de wijzigingen desgewenst direct uploaden naar Mobiel op aanvraag.

## Een artikel uploaden {#uploading-an-article}

De uploadactie kopieert de geselecteerde inhoud en voegt het aan een Mobiel project op bestelling toe. Bestaande mobiele on-demand-inhoud wordt vervangen door de nieuwe versie.

De algemene workflow voor het uploaden van een artikel:

1. Van **Mobiel**, kiest u uw mobiele On-Demand-app in de catalogus.
1. In de **Artikelen beheren** Selecteer een artikel dat u wilt uploaden naar Mobile On-Demand.
1. Voeg desgewenst meer artikelen toe in de lijstweergave.
1. Selecteren **Uploaden** Klik in de actiebalk op Uploaden in het dialoogvenster.
1. Uw artikelen worden nu geüpload naar Mobile On-Demand.

![chlimage_1-4](assets/chlimage_1-4.gif)

## Een artikel verwijderen {#deleting-an-article}

Met deze bewerking verwijdert u de geselecteerde inhoud van Mobiel op aanvraag en optioneel van de lokale AEM.

De algemene workflow voor het verwijderen van een artikel:

1. Kies vanuit Mobiel uw mobiele On-Demand-app in de catalogus.
1. Selecteer het artikel dat u wilt verwijderen in het dialoogvenster **Artikelen beheren** tegel.
1. Zorg ervoor dat deze optie is geselecteerd in de lijst (selecteer de andere opties die u wilt verwijderen).
1. Klikken **Verwijderen** in de actiebalk.
1. Controleer of u niet alleen mobiele apparaten op aanvraag maar ook AEM wilt verwijderen.
1. Klikken **Verwijderen**.
1. Uw artikel is nu verwijderd uit de lijst.

![chlimage_1-5](assets/chlimage_1-5.gif)

### De volgende stappen {#the-next-steps}

Ga voor meer informatie over het beheren van artikelen naar

* [Banners beheren](/help/mobile/mobile-on-demand-managing-banners.md)
* [Verzamelingen beheren](/help/mobile/mobile-on-demand-managing-collections.md)
* [Gedeelde bronnen uploaden](/help/mobile/mobile-on-demand-shared-resources.md)
* [De inhoud publiceren/verwijderen](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Voorvertonen met Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
