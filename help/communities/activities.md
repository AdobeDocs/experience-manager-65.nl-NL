---
title: Functie voor activiteitsstromen
seo-title: Functie voor activiteitsstromen
description: Activiteiten van een aangemeld lid van de gemeenschap
seo-description: Activiteiten van een aangemeld lid van de gemeenschap
uuid: decd2d6c-4d4b-4698-a92c-2b5b441458cf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 89f3630f-c01a-4dc0-9ff5-169785f22c01
docset: aem65
translation-type: tm+mt
source-git-commit: fcdae5363e7a0070b5d6b76227e5c65efb71bc03
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---


# Functie voor activiteitsstromen {#activity-streams-feature}

## Inleiding {#introduction}

De activiteiten van een ondertekend lid van de gemeenschap, zoals het posten aan een forum of blog, worden verzameld in een stroom die op verschillende manieren door configuratie van `Activity Streams` component kan worden gefiltreerd en getoond.

De mogelijkheid om te volgen voegt nog een weergave van activiteiten toe wanneer leden van de gemeenschap belangenverklaringen volgen of de activiteiten van andere leden van de gemeenschap volgen.

In het document wordt beschreven:

* De component Activiteitsstromen toevoegen aan een AEM-site
* Configuratie-instellingen voor de component Activiteitenstromen

### Activiteitsstromen toevoegen aan een pagina {#adding-activity-streams-to-a-page}

Als u een component `Activity Streams` in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Activity Streams`

en sleep het naar de juiste plaats op een pagina waar de activiteitenstromen moeten verschijnen.

Voor noodzakelijke informatie, bezoek [de Grondbeginselen van Componenten van Gemeenschappen](/help/communities/basics.md).

Wanneer de [vereiste client-side bibliotheken](/help/communities/essentials-activities.md#essentials-for-client-side) worden opgenomen, wordt de `Activity Streams`-component op deze manier weergegeven:

![activity-streams](assets/activity-component.png)

### Activiteitenstromen configureren {#configuring-activity-streams}

Selecteer de geplaatste `Activity Streams` component en selecteer `Configure` pictogram dat het Edit dialoog opent.

![vormen](assets/configure-new.png)

Geef onder het tabblad **Gebruikersactiviteiten** op welke activiteiten moeten worden weergegeven:

![gebruikersactiviteiten](assets/user-activities.png)

* **Max. aantal activiteiten**

   Aantal weer te geven activiteiten

* **Stroombronpad**

   Blanco laten om standaard in te stellen op de communitysite of -groep. Het pad naar de streambron identificeert de bron van activiteiten. De standaardwaarde is leeg.

* **Weergave gebruikersactiviteiten weergeven**

   Als deze optie is ingeschakeld, bevat de pagina met activiteiten een tabblad waarop de activiteiten worden gefilterd op basis van de activiteiten die door het huidige lid binnen de gemeenschap worden gegenereerd. Standaard is ingeschakeld.

* **Alle activiteiten weergeven**

   Als deze optie is ingeschakeld, bevat de pagina met activiteiten een tabblad dat alle activiteiten bevat die zijn gegenereerd binnen de gemeenschap waartoe het huidige lid toegang heeft. Standaard is ingeschakeld.

* **Na weergave weergeven**

   Als deze optie is ingeschakeld, bevat de pagina met activiteiten een tabblad waarop de activiteiten worden gefilterd op basis van de activiteiten die het huidige lid volgt. Standaard is ingeschakeld.

### Na weergave {#following-view}

Componenten moeten worden geconfigureerd om het volgende in te schakelen. Functies die het volgende toestaan, zijn [blog](/help/communities/blog-feature.md), [forum](/help/communities/forum.md), [QnA](/help/communities/working-with-qna.md), [agenda](/help/communities/calendar.md), [bestandsbibliotheek](/help/communities/file-library.md) en [commentaren](/help/communities/comments.md).

![volgende weergave](assets/following-activities.png)

Met de knop **Follow** kunt u vermeldingen als activiteiten, [meldingen](/help/communities/notifications.md) of [abonnementen](/help/communities/subscriptions.md) volgen. Telkens wanneer de **Follow** knoop wordt geselecteerd, is het mogelijk om of van een selectie van een knevel te voorzien. De `Email Subscriptions` selectie is slechts aanwezig wanneer gevormd.

Als een methode van het volgende wordt geselecteerd, verandert de tekst van de knoop in **volgend**. Voor het gemak, is het mogelijk om `Unfollow All` te selecteren om alle methodes van een knevel te voorzien.

De **Follow** knoop zal verschijnen:

* Bij weergave van het profiel van een ander lid.
* Op een hoofdpagina met functies, zoals forums, QnA en blogs.

   * Volg alle activiteiten voor die algemene functie.

* Voor een specifiek bericht, zoals een forumonderwerp, een QnA-vraag of een blogartikel.

   * Hiermee wordt alle activiteit voor die specifieke vermelding gevolgd.

### Aanvullende informatie {#additional-information}

Meer informatie vindt u op de pagina [Activiteitsstromen Essentials](/help/communities/essentials-activities.md) voor ontwikkelaars.
