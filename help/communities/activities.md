---
title: Functie voor activiteitsstromen
description: Leer hoe de activiteiten van een getekend lid van de community worden verzameld in een stream die u kunt filteren en weergeven via de component Activiteitenstromen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
docset: aem65
exl-id: 2b2a5de0-e7c7-4417-a217-4b929bc7dcfb
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Functie voor activiteitsstromen {#activity-streams-feature}

## Inleiding {#introduction}

De activiteiten van een getekend lid van de gemeenschap, zoals posten op een forum of blog, worden verzameld in een stream die op verschillende manieren kan worden gefilterd en weergegeven via de configuratie van de `Activity Streams` component.

De mogelijkheid om te volgen voegt nog een weergave van activiteiten toe wanneer leden van de gemeenschap belangenverklaringen volgen of de activiteiten van andere leden van de gemeenschap volgen.

In het document wordt beschreven:

* De component Activiteitsstromen toevoegen aan een AEM-site
* Configuratie-instellingen voor de component Activiteitenstromen

### Activiteitsstromen toevoegen aan een pagina {#adding-activity-streams-to-a-page}

Als u een `Activity Streams` van een component aan een pagina op auteurswijze, gebruik componentenbrowser om van

* `Communities / Activity Streams`

En sleep het naar zijn plaats op een pagina waar de activiteitenstromen zouden moeten verschijnen.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](/help/communities/basics.md).

Wanneer de [vereiste clientbibliotheken](/help/communities/essentials-activities.md#essentials-for-client-side) worden opgenomen, is dit hoe `Activity Streams` wordt weergegeven:

![activity-streams](assets/activity-component.png)

### Activiteitenstromen configureren {#configuring-activity-streams}

Selecteer de geplaatste `Activity Streams` zodat u toegang hebt tot `Configure` wordt het dialoogvenster Bewerken geopend.

![vormen](assets/configure-new.png)

Onder de **Gebruikersactiviteiten** tab, geef op welke activiteiten moeten worden weergegeven:

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

### Volgende weergave {#following-view}

Componenten moeten worden geconfigureerd om het volgende in te schakelen. Functies die het volgende toestaan, zijn [blog](/help/communities/blog-feature.md), [forum](/help/communities/forum.md), [QnA](/help/communities/working-with-qna.md), [kalender](/help/communities/calendar.md), [bestandsbibliotheek](/help/communities/file-library.md), en [opmerkingen](/help/communities/comments.md).

![volgende weergave](assets/following-activities.png)

De **Volgen** button biedt een manier om inzendingen te volgen als activiteiten, [meldingen](/help/communities/notifications.md), of [abonnementen](/help/communities/subscriptions.md). Elke keer als **Volgen** is geselecteerd, is het mogelijk om een selectie in of uit te schakelen. De `Email Subscriptions` selectie is alleen aanwezig als dit is geconfigureerd.

Als een van de volgende methoden is geselecteerd, verandert de tekst van de knop in **volgende**. Voor het gemak is het mogelijk `Unfollow All` om alle methoden uit te schakelen.

De **Volgen** wordt weergegeven:

* Bij weergave van het profiel van een ander lid.
* Op een hoofdpagina met functies, zoals forums, QnA en blogs.

   * Volg alle activiteiten voor die algemene functie.

* Voor een specifiek bericht, zoals een forumonderwerp, een QnA-vraag of een blogartikel.

   * Hiermee wordt alle activiteit voor die specifieke vermelding gevolgd.

### Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Essentiële elementen voor activiteitsstromen](/help/communities/essentials-activities.md) pagina voor ontwikkelaars.
