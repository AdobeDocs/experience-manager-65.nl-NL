---
title: Pagina's publiceren
seo-title: Pagina's publiceren
description: Nadat u de inhoud hebt gemaakt en gecontroleerd in de auteursomgeving, is het de bedoeling deze beschikbaar te maken op uw openbare website.
seo-description: Nadat u de inhoud hebt gemaakt en gecontroleerd in de auteursomgeving, is het de bedoeling deze beschikbaar te maken op uw openbare website.
uuid: ab5ffc59-1c41-46fe-904e-9fc67d7ead04
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 46d6bde0-8645-4cff-b79c-8e1615ba4ed4
docset: aem65
translation-type: tm+mt
source-git-commit: bcb1840d23ae538c183eecb0678b6a75d346aa50
workflow-type: tm+mt
source-wordcount: '1069'
ht-degree: 0%

---


# Pagina&#39;s publiceren{#publishing-pages}

Nadat u de inhoud in de ontwerpomgeving hebt gemaakt en gecontroleerd, kunt u deze beschikbaar stellen op uw openbare website (uw publicatieomgeving).

Dit wordt bedoeld als het publiceren van een pagina. Wanneer u een pagina uit het publicatiemilieu wilt verwijderen wordt bedoeld unpublishing. Wanneer u de pagina publiceert en publiceert, blijft deze beschikbaar in de ontwerpomgeving voor verdere wijzigingen totdat u de pagina verwijdert.

U kunt een pagina ook direct of op een vooraf gedefinieerde datum/tijd publiceren of verwijderen.

>[!NOTE]
>
>Bepaalde termen met betrekking tot publicatie kunnen worden verward:
>
>* **Publiceren/Publiceren ongedaan maken**
   >  Dit zijn de belangrijkste termen voor de acties die uw inhoud openbaar maken in uw publicatieomgeving (of niet).
   >
   >
* **Activeren/deactiveren**
   >  Deze termen zijn synoniem met publiceren/verwijderen.
   >
   >
* **Replicatie/replicatie**
   >  Dit zijn de technische termen die de beweging van gegevens (bijvoorbeeld pagina-inhoud, bestanden, code, gebruikerscommentaren) van de ene omgeving naar de andere beschrijven, zoals bij het publiceren of omgekeerd repliceren van gebruikerscommentaren.
>



>[!NOTE]
>
>Als u niet over de vereiste rechten voor het publiceren van een specifieke pagina beschikt:
>
>* Er wordt een workflow gestart om de juiste persoon op de hoogte te stellen van uw verzoek om te publiceren.
>* Er wordt een bericht weergegeven (voor een korte periode) om u hiervan op de hoogte te stellen.

>



## Een pagina {#publishing-a-page} publiceren

Er zijn twee methoden om een pagina te activeren:

* [vanuit de websiteconsole](#activating-a-page-from-the-websites-console)
* [van het hulplid op de pagina zelf](#activating-a-page-from-sidekick)

>[!NOTE]
>
>U kunt ook een substructuur van meerdere pagina&#39;s activeren met [Tree](#howtoactivateacompletesectiontreeofyourwebsite) activeren op de console Tools.

### Een pagina activeren via de websiteconsole {#activating-a-page-from-the-websites-console}

U kunt pagina&#39;s activeren in de console Websites. Nadat u een pagina hebt geopend en de inhoud ervan hebt gewijzigd, keert u terug naar de console Websites:

1. Selecteer in de websiteconsole de pagina die u wilt activeren.
1. Selecteer **Activeer** in het bovenste menu of in het vervolgkeuzemenu op het geselecteerde pagina-item.

   Om de inhoud van de pagina en al zijn subpagina&#39;s te activeren gebruik [**Tools** console](/help/sites-classic-ui-authoring/classic-page-author-publish-pages.md#howtoactivateacompletesectiontreeofyourwebsite).

   ![screen_shot_2012-02-08at13817pm](assets/screen_shot_2012-02-08at13817pm.png)

   >[!NOTE]
   >
   >Indien nodig, AEM u verzoeken om elementen die aan de pagina zijn gekoppeld, te activeren of opnieuw te activeren. U kunt de selectievakjes in- of uitschakelen om deze elementen te activeren.

1. Indien nodig, AEM u verzoeken om elementen die aan de pagina zijn gekoppeld, te activeren of opnieuw te activeren. U kunt de selectievakjes in- of uitschakelen om deze elementen te activeren.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. AEM WCM activeert de geselecteerde inhoud. De gepubliceerde pagina of pagina&#39;s worden weergegeven in de [Websiteconsole](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) (groen gemarkeerd) met informatie over wie de inhoud heeft geactiveerd en over de datum en tijd van activering.

   ![screen_shot_2012-02-08at14335pm](assets/screen_shot_2012-02-08at14335pm.png)

### Een pagina activeren vanaf Sidetrap {#activating-a-page-from-sidekick}

U kunt een pagina ook activeren wanneer u deze hebt geopend voor bewerking.

Nadat u de pagina hebt geopend en de inhoud ervan hebt gewijzigd, kunt u:

1. Selecteer het tabblad **Pagina** in de Sidetrap.
1. Klik **Pagina activeren**.
Rechtsboven in het venster wordt een bericht weergegeven waarin wordt bevestigd dat de pagina is geactiveerd.

## Publicatie van een pagina {#unpublishing-a-page} ongedaan maken

Als u een pagina uit de publicatieomgeving wilt verwijderen, deactiveert u de inhoud.

Een pagina deactiveren:

1. Selecteer in de websiteconsole de pagina die u wilt deactiveren.
1. Selecteer **Deactiveren** in het bovenste menu of in het vervolgkeuzemenu op het geselecteerde pagina-item. U wordt gevraagd de verwijdering te bevestigen.

   ![screen_shot_2012-02-08at14859pm](assets/screen_shot_2012-02-08at14859pm.png)

1. Vernieuw de [Websiteconsole](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) en de inhoud is rood gemarkeerd, erop wijzend dat het niet meer wordt gepubliceerd.

   ![screen_shot_2012-02-08at15018pm](assets/screen_shot_2012-02-08at15018pm.png)

## Later {#activate-deactivate-later} activeren/deactiveren

### Later {#activate-later} activeren

Uw activering voor een later tijdstip plannen:

1. Ga in de websiteconsole naar het menu **Activeren** en selecteer **Later activeren**.
1. In het dialoogvenster dat wordt geopend, geeft u de datum en tijd voor activering op en klikt u op **OK**. Hiermee wordt een versie van de pagina gemaakt die op het opgegeven tijdstip wordt geactiveerd.

   ![screen_shot_2012-02-08at14751pm](assets/screen_shot_2012-02-08at14751pm.png)

Als u later activeert, wordt een workflow gestart om deze versie van de pagina op het opgegeven tijdstip te activeren. Als u later deactiveert, wordt daarentegen een workflow gestart om deze versie van de pagina op een bepaald moment te deactiveren.

Als u deze activering/deactivering wilt annuleren, gaat u naar [Workflowconsole](/help/sites-administering/workflows-administering.md#main-pars_title_3-yjqslz-refd) om de bijbehorende workflow te beëindigen.

### Later {#deactivate-later} deactiveren

U kunt als volgt de deactivering voor een later tijdstip plannen:

1. Ga in de console van de Website, naar **Deactivate** menu, en selecteer **Deactivate later**.

1. In het dialoogvenster dat wordt geopend, geeft u de datum en tijd voor deactivering op en klikt u op **OK**.

   ![screen_shot_2012-02-08at15129pm](assets/screen_shot_2012-02-08at15129pm.png)

**Als u** later deactiveert, wordt een workflow gestart om deze versie van de pagina op een bepaald moment te deactiveren.

Als u deze deactivering wilt annuleren, gaat u naar [Workflowconsole](/help/sites-administering/workflows-administering.md#main-pars_title_3-yjqslz-refd) om de bijbehorende workflow te beëindigen.

## Geplande activering/deactivering (aan/uit tijd) {#scheduled-activation-deactivation-on-off-time}

U kunt tijden voor een pagina plannen die worden gepubliceerd/unpublished gebruikend **On Tijd** en **Uit Tijd** die in [Pagina Eigenschappen](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md) kan worden bepaald.

### Status van paginapublicatie bepalen {#determining-page-publication-status-classic-ui}

De status kan van [Websites worden gezien console](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console). De kleuren geven de publicatiestatus aan.

## Een volledige sectie (structuur) van uw website {#activating-a-complete-section-tree-of-your-website} activeren

Via het tabblad **Websites** kunt u de afzonderlijke pagina&#39;s activeren. Wanneer u een aanzienlijk aantal inhoudspagina&#39;s hebt ingevoerd of bijgewerkt - die allen onder de zelfde wortelpagina ingezeten zijn - kan het gemakkelijker zijn om de volledige boom in één actie te activeren. U kunt ook een droog programma uitvoeren om een activering na te bootsen en te markeren welke pagina&#39;s moeten worden geactiveerd.

1. Open de **Tools**-console door deze te selecteren op de pagina **Welkom** en dubbelklik vervolgens op **Replication** om de console te openen ( `https://localhost:4502/etc/replication.html`).

   ![screen_shot_2012-02-08at125033pm](assets/screen_shot_2012-02-08at125033pm.png)

1. Op **Replication** console, klik op **Activate Tree**.

   Het volgende venster ( `https://localhost:4502/etc/replication/treeactivation.html`) zal worden getoond.

   ![screen_shot_2012-02-08at125033pm-1](assets/screen_shot_2012-02-08at125033pm-1.png)

1. Voer het **Beginpad** in. Hiermee geeft u het pad op naar de hoofdmap van de sectie die u wilt activeren (publiceren). Deze pagina en alle onderliggende pagina&#39;s worden in overweging genomen voor activering (of worden gebruikt in de emulatie als er een Droge Run is geselecteerd).
1. Activeer de selectiecriteria naar wens:

   * **Alleen gewijzigd**: alleen pagina&#39;s activeren die zijn gewijzigd.
   * **Alleen geactiveerd**: alleen pagina&#39;s activeren die (al) zijn geactiveerd. Werkt als een vorm van reactivering.
   * **gedeactiveerd** negeren: pagina&#39;s die zijn gedeactiveerd, negeren.

1. Selecteer de handeling die u wilt uitvoeren:

   1. Selecteer **Drogen uitvoeren** als u wilt controleren welke pagina *zou* moeten worden geactiveerd. Dit is slechts een emulatie, er worden geen pagina&#39;s geactiveerd.

   1. Selecteer **Activeren** als u de pagina&#39;s wilt activeren.
