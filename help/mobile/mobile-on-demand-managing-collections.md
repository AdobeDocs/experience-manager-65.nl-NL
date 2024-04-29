---
title: Verzamelingen beheren
description: Verzamelingen vertegenwoordigen een welomschreven emmertje dat is gevuld met inhoud, zoals artikelen of banners, die het thema van de omslag aanpast. Volg deze pagina voor meer informatie.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-on-demand-services-app
exl-id: 0b4aa1a4-449a-4882-8f7c-3ceea6ac7f83
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '790'
ht-degree: 0%

---

# Verzamelingen beheren{#managing-collections}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

De acties van het Beheer van de inhoud zijn de bouwstenen die helpen om inhoud binnen een toepassing tot stand te brengen en te beheren. De volgende handelingen worden uitgevoerd op inhoud binnen de toepassing.

## Overzicht van verzamelingen {#collections-overview}

Verzamelingen vertegenwoordigen een goed gedefinieerde verzameling *emmer* gevuld met inhoud, zoals artikelen of banners, die het thema van de omslag uitpakken.

>[!NOTE]
>
>Zie de volgende bronnen in de online Help voor meer informatie over de volgende onderwerpen in AEM Mobile-apps:
>
>* [Ontwerpaspecten](https://helpx.adobe.com/digital-publishing-solution/help/design-app.html)
>
>* [Verzamelingen beheren](https://helpx.adobe.com/digital-publishing-solution/help/creating-collections.html)
>

## Een verzameling maken {#creating-a-collection}

De algemene workflow voor het maken van een verzameling is als volgt:

1. Selecteren **Mobiel** van de zijspoor.
1. Kies vanuit Mobiel uw mobiele On-Demand-app in de catalogus.
1. Klik op de pijl omlaag in de rechterbovenhoek van het dialoogvenster **Verzamelingen beheren** tegel.
1. Werk door elke stap van de wizard om door te gaan met het maken van uw nieuwe artikel.
1. Klik op **Maken**.
1. Uw nieuwe artikel wordt weergegeven in het dialoogvenster **Verzamelingen beheren** tegel.

![chlimage_1-1](assets/chlimage_1-1.gif)

## Een nieuwe verzameling importeren {#importing-a-new-collection}

Bestaande mobiele on-demand-inhoud kan worden gedownload (geïmporteerd) van Mobile On-Demand naar AEM. Zo kunt u lokale inhoud bewerken en weergeven.

>[!NOTE]
>
>Bij het importeren worden geen afbeeldingen opgenomen.

De workflow voor het importeren van een nieuwe verzameling

1. Kies vanuit Mobiel uw mobiele On-Demand-app in de catalogus.
1. Klik op de pijl omlaag in de rechterbovenhoek van het dialoogvenster **Verzamelingen beheren** tegel en selecteer Verzamelingen importeren.
1. Klikken **Verzamelingen importeren** in het dialoogvenster en vervolgens Sluiten.
1. Uw mobiele verzamelingen op aanvraag worden nu weergegeven in de **Verzamelingen beheren** tegel.

>[!CAUTION]
>
>Koppel eerst een mobiele on-demand-verbinding.

## Een verzameling bewerken {#editing-a-collection}

Met de ingebouwde AEM slepen en neerzetten-editor kunt u een artikel toevoegen of wijzigen. Componenten zoals tekst en afbeeldingen kunnen worden toegevoegd of verwijderd. U kunt afbeeldingen van DAM-middelen invoegen.

De workflow voor het bewerken van een verzameling:

1. Kies vanuit Mobiel uw mobiele On-Demand-app in de catalogus.
1. Selecteer een AEM artikel in het menu **Verzamelingen beheren** tegel.
1. Klik op de gemarkeerde verzameling in de lijstweergave om deze te openen in de inhoudseditor.
1. Gebruik de inhoudeditor om verzamelingsinhoud te slepen (manuscripten, afbeeldingen, tekst, enzovoort).

### De metagegevens in een verzameling weergeven en bewerken {#viewing-and-editing-the-metadata-within-a-collection}

Verzamelingen hebben talrijke eigenschappen, zoals titels, beschrijvingen en afbeeldingen. Deze handeling wordt gebruikt om dergelijke eigenschappen weer te geven en te wijzigen. Deze wijzigingen kunnen optioneel worden geüpload naar Mobile On-Demand tijdens het opslaan.

De algemene workflow voor het weergeven/bewerken van een verzameling:

1. Kies vanuit Mobiel uw mobiele On-Demand-app in de catalogus.
1. Kies een verzameling in het menu **Verzamelingen beheren** tegel.

1. Selecteren **Eigenschappen** in de actiebalk.
1. Alle beschikbare metagegevens voor dat artikel weergeven.
1. Bewerk desgewenst de metagegevens en klik op **Opslaan** wanneer gereed.
1. U kunt de wijzigingen desgewenst direct uploaden naar Mobiel op aanvraag.

## Een verzameling uploaden {#uploading-a-collection}

De uploadactie kopieert de geselecteerde inhoud en voegt het aan een Mobiel project op bestelling toe. Bestaande mobiele on-demand-inhoud wordt vervangen door de nieuwe versie.

De algemene workflow voor het uploaden van een verzameling:

1. Van **Mobiel**, kiest u uw mobiele On-Demand-app in de catalogus.
1. In de **Verzamelingen beheren** Selecteer een artikel dat u wilt uploaden naar Mobile On-Demand.
1. Voeg indien nodig meer verzamelingen toe in de lijstweergave.
1. Selecteren **Uploaden** Klik in de actiebalk op Uploaden in het dialoogvenster.
1. Uw verzameling(en) worden nu geüpload naar Mobiel op aanvraag.

## Een verzameling verwijderen {#deleting-a-collection}

Met deze bewerking verwijdert u de geselecteerde verzameling van Mobiel op aanvraag en optioneel van de lokale AEM.

De algemene workflow voor het verwijderen van een verzameling:

1. Kies vanuit Mobiel uw mobiele On-Demand-app in de catalogus.
1. Selecteer het artikel dat u wilt verwijderen in het dialoogvenster **Verzamelingen beheren** tegel.
1. Zorg ervoor dat deze optie in de lijst is geselecteerd en selecteer de andere opties die u wilt verwijderen.
1. Klikken **Verwijderen** in de actiebalk.
1. Controleer of u gegevens uit AEM en mobiel op aanvraag wilt verwijderen.
1. Klikken **Verwijderen**.
1. Uw verzameling wordt nu verwijderd uit de lijst.

## Inhoud toevoegen aan verzamelingen {#adding-content-to-collections}

Verzamelingen zijn in wezen een categorie met verwante inhoud. Ze verzamelen inhoud, zoals artikelen, banners, in pakketten die de navigatiestructuur van uw toepassing definiëren. Verzamelingen kunnen worden genest.

>[!NOTE]
>
>Inhoud moet worden geüpload naar Mobile On-Demand voordat deze kan worden toegevoegd aan een verzameling.

Verzamelingen zijn in wezen een categorie met verwante inhoud: ze verzamelen inhoud, zoals artikelen, banners, in pakketten die de navigatiestructuur van uw toepassing definiëren. Verzamelingen kunnen worden genest.

1. Kies vanuit Mobiel uw mobiele On-Demand-app in de catalogus.
1. Een eerder geüpload artikel selecteren (of een banner/verzameling)
1. Kies Toevoegen aan op de actiebalk.
1. Selecteer een eerder geüploade verzameling in het dialoogvenster.
1. Klikken **Bijwerken** om inhoud toe te voegen aan de verzameling.

![chlimage_1-2](assets/chlimage_1-2.gif)

### De volgende stappen {#the-next-steps}

Als u meer wilt weten over het beheren van verzamelingen, raadpleegt u

* [Banners beheren](/help/mobile/mobile-on-demand-managing-banners.md)
* [Artikelen beheren](/help/mobile/mobile-on-demand-managing-articles.md)
* [Gedeelde bronnen uploaden](/help/mobile/mobile-on-demand-shared-resources.md)
* [De inhoud publiceren/publiceren ongedaan maken](/help/mobile/mobile-on-demand-publishing-unpublishing.md)
* [Voorvertonen met Preflight](/help/mobile/aem-mobile-manage-ondemand-services.md)
