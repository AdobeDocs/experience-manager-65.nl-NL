---
title: Uitgebreid zoeken
description: Zoek uw inhoud sneller met uitgebreide zoekopdrachten.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: dd65b308-c449-4f64-9f46-0797b922910f
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '517'
ht-degree: 5%

---

# Zoeken{#searching}

De auteursomgeving van AEM verstrekt diverse mechanismen om naar inhoud te zoeken, afhankelijk van het middeltype.

>[!NOTE]
>
>Buiten de auteursomgeving zijn andere mechanismen ook beschikbaar voor het zoeken, zoals [Query Builder](/help/sites-developing/querybuilder-api.md) en [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md).

## Basisinformatie zoeken {#search-basics}

Zoeken is beschikbaar op de bovenste werkbalk:

![Zoeken](do-not-localize/chlimage_1-17.png)

Met de zoekrail kunt u:

* Zoeken naar een specifiek trefwoord, pad of tag.
* Filter volgens bronspecifieke criteria, zoals gewijzigde datums, paginastatus, bestandsgrootte enzovoort.
* Definieer een [opgeslagen zoekopdracht](#saved-searches) - op basis van bovenstaande criteria.

>[!NOTE]
>
>Zoeken kan ook worden aangeroepen door de sneltoets te gebruiken `/` (slash) wanneer de zoekrail zichtbaar is.

## Zoeken en filteren {#search-and-filter}

U kunt als volgt uw bronnen zoeken en filteren:

1. Openen **Zoeken** (met het vergrootglas in de werkbalk) en voer uw zoekterm in. Er worden voorstellen gedaan die kunnen worden geselecteerd:

   ![s-01](assets/s-01.png)

   Door gebrek zullen de onderzoeksresultaten tot uw huidige plaats (namelijk console en verwante middeltype) worden beperkt:

   ![screen_shot_2018-03-23at101445](assets/screen_shot_2018-03-23at101445.png)

1. Indien nodig kunt u het locatiefilter verwijderen (selecteer **X** op het filter dat u wilt verwijderen) om te zoeken in alle consoles/middeltypen.
1. De resultaten worden getoond, gegroepeerd volgens console en verwant middeltype.

   U kunt een bepaalde bron selecteren (voor verdere actie) of naar beneden boren door het vereiste type resource te selecteren, bijvoorbeeld **Alle sites weergeven**:

   ![screen-shot_2019-03-05at101900](assets/screen-shot_2019-03-05at101900.png)

1. Als u verder omlaag wilt boren, selecteert u het symbool Rail (linksboven) om het zijpaneel te openen **Filters en opties**.

   ![Filters en opties](do-not-localize/screen_shot_2018-03-23at101542.png)

   Volgens het middeltypeOnderzoek zal een vooraf bepaalde selectie van onderzoek/filtercriteria tonen.

   In het zijpaneel kunt u selecteren:

   * Opgeslagen zoekopdrachten
   * Zoekdirectory
   * Tags
   * Zoekcriteria; bijvoorbeeld Gewijzigde datums, Publicatiestatus en LiveCopy-status.

   >[!NOTE]
   >
   >De zoekcriteria kunnen variëren:
   >
   >
   >
   >    * Afhankelijk van het type bron dat u hebt geselecteerd, zijn bijvoorbeeld de criteria Middelen en Gemeenschappen begrijpelijkerwijs gespecialiseerd.
   >    * Uw instantie als de [Zoeken in Forms](/help/sites-administering/search-forms.md) kan worden aangepast (aangepast aan de locatie in AEM).
   >
   >

   ![screen-shot_2019-03-05at102509](assets/screen-shot_2019-03-05at102509.png)

1. U kunt ook extra zoektermen toevoegen:

   ![screen-shot_2019-03-05at102613](assets/screen-shot_2019-03-05at102613.png)

1. Sluit **Zoeken** met de **X** (rechtsboven).

>[!NOTE]
>
>Zoekcriteria blijven bestaan wanneer u een item in de zoekresultaten selecteert.
>
>Wanneer u een item op de pagina met zoekresultaten selecteert en vervolgens terugkeert naar de zoekpagina nadat u de knop Terug in de browser hebt gebruikt, blijven de zoekcriteria behouden.

## Opgeslagen zoekopdrachten {#saved-searches}

Naast het zoeken op basis van een groot aantal facetten kunt u ook een bepaalde zoekconfiguratie opslaan, zodat deze later kan worden opgehaald en gebruikt:

1. Definieer uw zoekcriteria en selecteer **Opslaan**.

   ![screen-shot_2019-03-05at102613-1](assets/screen-shot_2019-03-05at102613-1.png)

1. Wijs een naam toe, dan gebruik **Opslaan** ter bevestiging:

   ![screen-shot_2019-03-05at102725](assets/screen-shot_2019-03-05at102725.png)

1. De volgende keer dat u het deelvenster Zoeken opent, kunt u de opgeslagen zoekopdracht vanuit de kiezer openen:

   ![screen-shot_2019-03-05at102927](assets/screen-shot_2019-03-05at102927.png)

1. Nadat u het bestand hebt opgeslagen, kunt u:

   * Gebruiken **x** (naast de naam van de opgeslagen zoekopdracht) om een nieuwe query te starten (de opgeslagen zoekopdracht zelf wordt niet verwijderd).
   * **Opgeslagen zoekopdracht bewerken** wijzigt u vervolgens de zoekvoorwaarden **Opslaan** opnieuw.

Opgeslagen zoekopdrachten kunnen worden gewijzigd door de opgeslagen zoekopdracht te selecteren en onder aan het zoekvenster op **Opgeslagen zoekopdracht bewerken** te klikken.

![screen-shot_2019-03-05at103010](assets/screen-shot_2019-03-05at103010.png)
