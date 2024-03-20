---
title: Pagina's publiceren
description: Nadat u de inhoud hebt gemaakt en gecontroleerd in de auteursomgeving, stelt u deze beschikbaar op uw openbare website.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
docset: aem65
exl-id: 3f6aa06e-b5fd-4ab0-9ecc-14250cb3f55e
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1028'
ht-degree: 0%

---

# Pagina&#39;s publiceren{#publishing-pages}

Nadat u de inhoud hebt gemaakt en gecontroleerd in de auteursomgeving, stelt u deze beschikbaar op uw openbare website (uw publicatieomgeving).

Dit wordt bedoeld als het publiceren van een pagina. Wanneer u een pagina uit het publicatiemilieu wilt verwijderen wordt bedoeld unpublishing. Wanneer u de pagina publiceert en publiceert, blijft deze beschikbaar in de ontwerpomgeving voor verdere wijzigingen totdat u de pagina verwijdert.

U kunt een pagina ook direct of op een vooraf gedefinieerde datum/tijd publiceren of verwijderen.

>[!NOTE]
>
>Bepaalde termen met betrekking tot publicatie kunnen worden verward:
>
>* **Publiceren/Publiceren ongedaan maken**
>  Dit zijn de belangrijkste termen voor de acties die uw inhoud openbaar maken in uw publicatieomgeving (of niet).
>
>* **Activeren/deactiveren**
>  Deze termen zijn synoniem met publiceren/verwijderen.
>
>* **Replicatie/replicatie**
>  Dit zijn de technische termen die de beweging van gegevens (bijvoorbeeld pagina-inhoud, bestanden, code, gebruikerscommentaren) van de ene omgeving naar de andere beschrijven, zoals bij het publiceren of omgekeerd repliceren van gebruikerscommentaren.
>

>[!NOTE]
>
>Als u niet over de vereiste rechten voor het publiceren van een specifieke pagina beschikt:
>
>* Er wordt een workflow gestart om de juiste persoon op de hoogte te stellen van uw verzoek om te publiceren.
>* Er wordt een bericht weergegeven (voor een korte periode) om u hiervan op de hoogte te stellen.
>

## Pagina&#39;s publiceren {#publishing-a-page}

Er zijn twee methoden om een pagina te activeren:

* [vanuit de websiteconsole](#activating-a-page-from-the-websites-console)
* [van het hulplid op de pagina zelf](#activating-a-page-from-sidekick)

>[!NOTE]
>
>U kunt ook een substructuur van meerdere pagina&#39;s activeren met [Boom activeren](#howtoactivateacompletesectiontreeofyourwebsite) op de console van Hulpmiddelen.

### Een pagina activeren via de websiteconsole {#activating-a-page-from-the-websites-console}

U kunt pagina&#39;s activeren in de console Websites. Nadat u een pagina hebt geopend en de inhoud ervan hebt gewijzigd, keert u terug naar de console Websites:

1. Selecteer in de websiteconsole de pagina die u wilt activeren.
1. Selecteren **Activeren** in het bovenste menu of in het vervolgkeuzemenu van het geselecteerde pagina-item.

   Als u de inhoud van de pagina en alle subpagina&#39;s wilt activeren, gebruikt u de opdracht [**Gereedschappen** console](/help/sites-classic-ui-authoring/classic-page-author-publish-pages.md#howtoactivateacompletesectiontreeofyourwebsite).

   ![screen_shot_2012-02-08at13817pm](assets/screen_shot_2012-02-08at13817pm.png)

   >[!NOTE]
   >
   >Indien nodig, AEM u verzoeken om elementen die aan de pagina zijn gekoppeld, te activeren of opnieuw te activeren. U kunt de selectievakjes in- of uitschakelen om deze elementen te activeren.
   >
   >

1. Indien nodig, AEM u verzoeken om elementen die aan de pagina zijn gekoppeld, te activeren of opnieuw te activeren. U kunt de selectievakjes in- of uitschakelen om deze elementen te activeren.

   ![chlimage_1-100](assets/chlimage_1-100.png)

1. AEM WCM activeert de geselecteerde inhoud. De gepubliceerde pagina of pagina&#39;s worden weergegeven in het dialoogvenster [Websiteconsole](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) (groen gemarkeerd) met informatie over wie de inhoud heeft geactiveerd en de datum en tijd van activering.

   ![screen_shot_2012-02-08at14335pm](assets/screen_shot_2012-02-08at14335pm.png)

### Een pagina vanuit Sidekick activeren {#activating-a-page-from-sidekick}

U kunt een pagina ook activeren wanneer u deze hebt geopend voor bewerking.

Nadat u de pagina hebt geopend en de inhoud ervan hebt gewijzigd, kunt u:

1. Selecteer de **Pagina** in de Sidekick.
1. Klikken **Pagina activeren**.
Rechtsboven in het venster wordt een bericht weergegeven waarin wordt bevestigd dat de pagina is geactiveerd.

## Publicatie van een pagina ongedaan maken {#unpublishing-a-page}

Als u een pagina uit de publicatieomgeving wilt verwijderen, deactiveert u de inhoud.

Een pagina deactiveren:

1. Selecteer in de websiteconsole de pagina die u wilt deactiveren.
1. Selecteren **Deactiveren** in het bovenste menu of in het vervolgkeuzemenu van het geselecteerde pagina-item. U wordt gevraagd de verwijdering te bevestigen.

   ![screen_shot_2012-02-08at14859pm](assets/screen_shot_2012-02-08at14859pm.png)

1. Vernieuw de [Websiteconsole](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console) en de inhoud is rood gemarkeerd om aan te geven dat deze niet langer wordt gepubliceerd.

   ![screen_shot_2012-02-08at15018pm](assets/screen_shot_2012-02-08at15018pm.png)

## Later activeren/deactiveren {#activate-deactivate-later}

### Later activeren {#activate-later}

Uw activering voor een later tijdstip plannen:

1. Ga in de websiteconsole naar de **Activeren** en selecteert u **Later activeren**.
1. Geef in het dialoogvenster dat nu wordt geopend de datum en tijd voor activering op en klik op **OK**. Hiermee wordt een versie van de pagina gemaakt die op het opgegeven tijdstip wordt geactiveerd.

   ![screen_shot_2012-02-08at14751pm](assets/screen_shot_2012-02-08at14751pm.png)

Als u later activeert, wordt een workflow gestart om deze versie van de pagina op het opgegeven tijdstip te activeren. Als u later deactiveert, wordt daarentegen een workflow gestart om deze versie van de pagina op een bepaald moment te deactiveren.

Als u deze activering/deactivering wilt annuleren, ga naar [Workflowconsole](/help/sites-administering/workflows-administering.md#main-pars_title_3-yjqslz-refd) om de corresponderende workflow te beëindigen.

### Later deactiveren {#deactivate-later}

U kunt als volgt de deactivering voor een later tijdstip plannen:

1. Ga in de console van de Website naar **Deactiveren** en selecteert u **Later deactiveren**.

1. Geef in het dialoogvenster dat nu wordt geopend de datum en tijd op voor deactivering en klik op **OK**.

   ![screen_shot_2012-02-08at15129pm](assets/screen_shot_2012-02-08at15129pm.png)

**Deactivering laat** r start een workflow om deze versie van de pagina op een bepaald tijdstip te deactiveren.

Als u deze deactivering wilt annuleren, gaat u naar [Workflowconsole](/help/sites-administering/workflows-administering.md#main-pars_title_3-yjqslz-refd) om de corresponderende workflow te beëindigen.

## Geplande activering/deactivering (aan/uit-tijd) {#scheduled-activation-deactivation-on-off-time}

U kunt tijden voor een te publiceren pagina/unpublished plannen gebruikend **Op tijd** en **Uit-tijd** die kunnen worden gedefinieerd in de [Pagina-eigenschappen](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md).

### Status van paginapublicatie bepalen {#determining-page-publication-status-classic-ui}

De status kan worden bekeken vanuit de [Websiteconsole](/help/sites-classic-ui-authoring/author-env-basic-handling.md#page-information-on-the-websites-console). De kleuren geven de publicatiestatus aan.

## Een volledige sectie (structuur) van uw website activeren {#activating-a-complete-section-tree-of-your-website}

Van de **Websites** kunt u de afzonderlijke pagina&#39;s activeren. Wanneer u een aanzienlijk aantal inhoudspagina&#39;s hebt ingevoerd of bijgewerkt - die allen onder de zelfde wortelpagina ingezeten zijn - kan het gemakkelijker zijn om de volledige boom in één actie te activeren. U kunt ook een droog programma uitvoeren om een activering na te bootsen en te markeren welke pagina&#39;s moeten worden geactiveerd.

1. Open de **Gereedschappen** console door het van de **Welkom** en dubbelklikken **Replicatie** de console openen ( `https://localhost:4502/etc/replication.html`).

   ![screen_shot_2012-02-08at125033pm](assets/screen_shot_2012-02-08at125033pm.png)

1. Op de **Replicatie** console, klik **Boom activeren**.

   Het volgende venster ( `https://localhost:4502/etc/replication/treeactivation.html`) wordt weergegeven.

   ![screen_shot_2012-02-08at125033pm-1](assets/screen_shot_2012-02-08at125033pm-1.png)

1. Voer de **Startpad**. Hiermee geeft u het pad op naar de hoofdmap van de sectie die u wilt activeren (publiceren). Deze pagina en alle onderliggende pagina&#39;s worden in overweging genomen voor activering (of worden gebruikt in de emulatie als er een Droge Run is geselecteerd).
1. Activeer de selectiecriteria naar wens:

   * **Alleen gewijzigd**: alleen pagina&#39;s activeren die zijn gewijzigd.
   * **Alleen geactiveerd**: alleen pagina&#39;s activeren die (al) zijn geactiveerd. Werkt als een vorm van reactivering.
   * **Negeren gedeactiveerd**: negeer alle pagina&#39;s die zijn gedeactiveerd.

1. Selecteer de handeling die u wilt uitvoeren:

   1. Selecteren **Droog** als u wilt controleren welke pagina&#39;s *zou* worden geactiveerd. Dit is slechts een emulatie, er worden geen pagina&#39;s geactiveerd.

   1. Selecteren **Activeren** als u de pagina&#39;s wilt activeren.
