---
title: Starten promoten
description: U promoot opstartiepagina's om de inhoud vóór publicatie terug te plaatsen naar de bron (productie).
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
docset: aem65
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: f59f12a2-ecd6-49cf-90ad-621719fe51bf
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Launches
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '772'
ht-degree: 0%

---

# Starten promoten{#promoting-launches}

U moet opstartiepagina&#39;s promoten om de inhoud vóór publicatie weer naar de bron (productie) te verplaatsen. Wanneer een startpagina wordt bevorderd, wordt de bijbehorende pagina van de bronpagina&#39;s vervangen door de inhoud van de gepromoveerde pagina. De volgende opties zijn beschikbaar bij het promoten van een startpagina:

* Of alleen de huidige pagina of de volledige lancering wordt bevorderd.
* Of de onderliggende pagina&#39;s van de huidige pagina worden bevorderd.
* Of de volledige lancering of slechts pagina&#39;s wordt bevorderd die zijn veranderd.
* Of de introductie moet worden verwijderd nadat deze is bevorderd.

>[!NOTE]
>
>Nadat u de lanceringspagina&#39;s aan het doel (**Productie**) bevordert, kunt u de **Productie** pagina&#39;s als entiteit (om het proces sneller te maken) activeren. Voeg de pagina&#39;s toe aan een workflowpakket en gebruik dit als de payload voor een workflow die een pakket met pagina&#39;s activeert. U moet het workflowpakket maken voordat u de introductie kunt promoten. Zie [ Verwerkingsbevorderde Pagina&#39;s gebruikend het Werkschema van AEM ](#processing-promoted-pages-using-aem-workflow).

>[!CAUTION]
>
>Een enkele lancering kan niet tegelijkertijd worden bevorderd. Dit betekent dat twee promotieacties bij dezelfde introductie tegelijkertijd kunnen resulteren in een fout - `Launch could not be promoted` (samen met conflictfouten in het logbestand).

>[!CAUTION]
>
>Wanneer het bevorderen van lanceringen voor *gewijzigde* pagina&#39;s, worden de wijzigingen in zowel de bron als lanceringstakken overwogen.

## Startpagina&#39;s promoten {#promoting-launch-pages}

>[!NOTE]
>
>Dit omvat de handmatige actie van het bevorderen van lanceringspagina&#39;s wanneer er slechts één lanceringsniveau is. Zie:
>
>* [ Bevorderend een Genestelde Lancering ](#promoting-a-nested-launch) wanneer er meer dan één lancering in de structuur is.
>* [ Lanceringen - de Orde van Gebeurtenissen ](/help/sites-authoring/launches.md#launches-the-order-of-events) voor verdere details over automatische bevordering en publicatie.
>

U kunt lanceringen van of de **console van Plaatsen** of de **console van Lanceringen** bevorderen:

1. Openen:

   * de **console van Plaatsen**:

      1. Open het [ verwijzingenspoor ](/help/sites-authoring/author-environment-tools.md#showingpagereferences) en selecteer de vereiste bronpagina gebruikend [ selectiemodus ](/help/sites-authoring/basic-handling.md) (of selecteer en open de verwijzingsspoorwegen, is de orde niet belangrijk). Alle verwijzingen worden weergegeven.

      1. Selecteer **Lanceringen** (bijvoorbeeld, Lanceringen (1)) om een lijst van de specifieke lanceringen te tonen.
      1. Selecteer de specifieke lancering om de beschikbare acties te tonen.
      1. Selecteer **Bevorderen lancering** om de tovenaar te openen.

   * de **console van Lanceringen**:

      1. Selecteer de start (klik op de miniatuur).
      1. Selecteer **bevorderen**.

1. In de eerste stap kunt u het volgende opgeven:

   * **Doel**

      * **schrapping lancering na bevordering**

   * **Reikwijdte**

      * **bevorderen volledige lancering**
      * **bevordert gewijzigde pagina&#39;s**
      * **bevordert huidige pagina**
      * **bevordert huidige pagina en subpagina&#39;s**

   Als u bijvoorbeeld alleen gewijzigde pagina&#39;s wilt promoten:

   ![ lanceert-pd-06 ](assets/launches-pd-06.png)

   >[!NOTE]
   >
   >Dit behandelt één enkele lancering, als u genestelde lanceringen zie [ Bevorderend een Genestelde Lancering ](#promoting-a-nested-launch).

1. Selecteer **daarna** te werk te gaan.
1. U kunt de pagina&#39;s bekijken die u wilt promoten. Deze zijn afhankelijk van het gekozen paginabereik:

   ![ pagina&#39;s van het Overzicht die moeten worden bevorderd ](assets/chlimage_1-102.png)

1. Selecteer **bevorderen**.

## Starten van pagina&#39;s tijdens bewerken bevorderen {#promoting-launch-pages-when-editing}

Wanneer u een lanceringspagina uitgeeft, **bevordert de 1} actie van de Lancering {ook beschikbaar bij** Informatie van de Pagina **.** Hierdoor wordt de wizard geopend die de benodigde informatie verzamelt.

![ bevorderen Lanceer ](assets/chlimage_1-103.png)

>[!NOTE]
>
>Dit is beschikbaar voor enige en [ genestelde lanceringen ](#promoting-a-nested-launch).

## Een geneste start bevorderen {#promoting-a-nested-launch}

Nadat u een geneste start hebt gemaakt, kunt u deze herstellen naar een van de bronnen, inclusief de hoofdbron (productie).

![ Overzicht van het bevorderen van een genestelde lancering ](assets/chlimage_1-104.png)

1. Zoals met [ Creërend een Genestelde Lancering ](#creatinganestedlaunchlaunchwithinalaunch), navigeer aan en selecteer de vereiste lancering in of de **3} console van Lanceringen {of het** spoor van Verwijzingen **.**
1. Selecteer **Bevorderen lancering** om de tovenaar te openen.

1. Voer de vereiste gegevens in:

   * **Doel**

      * **doel van de Bevordering**
U kunt een van de bronnen promoten.

      * **schrapping lancering na bevordering**
Na de promotie worden de geselecteerde lancering, en om het even welke genestelde lanceringen binnen het, geschrapt.

   * **Reikwijdte**
Hier kunt u kiezen of u de volledige opstart wilt bevorderen of alleen pagina&#39;s die daadwerkelijk zijn bewerkt. In het laatste geval kunt u opgeven of u subpagina&#39;s wilt opnemen of uitsluiten. De standaardconfiguratie is dat alleen paginawijzigingen voor de huidige pagina worden bevorderd:

      * **bevorderen volledige lancering**
      * **bevordert gewijzigde pagina&#39;s**
      * **bevordert huidige pagina**
      * **bevordert huidige pagina en subpagina&#39;s**

   ![ Montages voor het bevorderen van een lancering ](assets/chlimage_1-105.png)

1. Selecteer **daarna**.
1. Herzie de promotiedetails alvorens **te selecteren bevorderen**:

   ![ de details van het Overzicht en bevorderen ](assets/chlimage_1-106.png)

   >[!NOTE]
   >
   >De vermelde pagina&#39;s zullen van het **Gedefinieerde Werkingsgebied** en misschien de pagina&#39;s afhangen die eigenlijk zijn uitgegeven.

1. Uw veranderingen zullen in de **console van Lanceringen** worden bevorderd en worden weerspiegeld:

   ![ console van Lanceringen ](assets/chlimage_1-107.png)

## Promotiepagina&#39;s verwerken met AEM Workflow {#processing-promoted-pages-using-aem-workflow}

Gebruik workflowmodellen voor bulkverwerking van geconverteerde startpagina&#39;s:

1. Maak een workflowpakket.
1. Wanneer auteurs startpagina&#39;s promoten, slaan ze deze op in het workflowpakket.
1. Start een workflowmodel met het pakket als de payload.

Om een werkschema automatisch te beginnen wanneer de pagina&#39;s worden bevorderd, [ vormt een werkschemalancerer ](/help/sites-administering/workflows-starting.md#workflows-launchers) voor de pakketknoop.

U kunt bijvoorbeeld automatisch aanvragen voor paginanactivering genereren wanneer auteurs pagina&#39;s voor Starten promoten. Configureer een werkstroomstartprogramma om de workflow voor activering van aanvragen te starten wanneer het pakketknooppunt wordt gewijzigd.

![ Startprogramma van het Werkschema ](assets/chlimage_1-108.png)
