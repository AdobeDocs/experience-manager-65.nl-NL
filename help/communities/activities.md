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

De activiteiten van een ondertekend lid van de gemeenschap, zoals het posten aan een forum of blog, worden verzameld in een stroom die op verschillende manieren door configuratie van de `Activity Streams` component kan worden gefiltreerd en worden getoond.

De mogelijkheid om te volgen voegt nog een weergave van activiteiten toe wanneer leden van de gemeenschap belangenverklaringen volgen of de activiteiten van andere leden van de gemeenschap volgen.

In het document wordt beschreven:

* De component Activiteitsstromen toevoegen aan een AEM-site
* Configuratie-instellingen voor de component Activiteitenstromen

### Activiteitsstromen toevoegen aan een pagina {#adding-activity-streams-to-a-page}

Als u een component `Activity Streams` in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Activity Streams`

En sleep het naar zijn plaats op een pagina waar de activiteitenstromen zouden moeten verschijnen.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen [&#128279;](/help/communities/basics.md).

Wanneer de [&#x200B; vereiste cliënt-zijbibliotheken &#x200B;](/help/communities/essentials-activities.md#essentials-for-client-side) inbegrepen zijn, is dit hoe de `Activity Streams` component verschijnt:

![&#x200B; activiteit-stromen &#x200B;](assets/activity-component.png)

### Activiteitenstromen configureren {#configuring-activity-streams}

Selecteer de geplaatste component `Activity Streams` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![&#x200B; vormen &#x200B;](assets/configure-new.png)

Onder het **lusje van de Activiteiten van de Gebruiker**, specificeer welke activiteiten aan vertoning:

![&#x200B; gebruiker-activiteiten &#x200B;](assets/user-activities.png)

* **Max aantal activiteiten**

  Aantal weer te geven activiteiten

* **Pad van het Middel van de Stroom**

  Blanco laten om standaard in te stellen op de communitysite of -groep. Het pad naar de streambron identificeert de bron van activiteiten. De standaardwaarde is leeg.

* **Mening van de Activiteiten van de Gebruiker van de Vertoning**

  Als deze optie is ingeschakeld, bevat de pagina met activiteiten een tabblad waarop de activiteiten worden gefilterd op basis van de activiteiten die door het huidige lid binnen de gemeenschap worden gegenereerd. Standaard is ingeschakeld.

* **Vertoning Alle Mening van Activiteiten**

  Als deze optie is ingeschakeld, bevat de pagina met activiteiten een tabblad dat alle activiteiten bevat die zijn gegenereerd binnen de gemeenschap waartoe het huidige lid toegang heeft. Standaard is ingeschakeld.

* **Vertoning na Mening**

  Als deze optie is ingeschakeld, bevat de pagina met activiteiten een tabblad waarop de activiteiten worden gefilterd op basis van de activiteiten die het huidige lid volgt. Standaard is ingeschakeld.

### Volgende weergave {#following-view}

Componenten moeten worden geconfigureerd om het volgende in te schakelen. De eigenschappen die het volgende toestaan zijn [&#x200B; blog &#x200B;](/help/communities/blog-feature.md), [&#x200B; forum &#x200B;](/help/communities/forum.md), [&#x200B; QnA &#x200B;](/help/communities/working-with-qna.md), [&#x200B; kalender &#x200B;](/help/communities/calendar.md), [&#x200B; dossierbibliotheek &#x200B;](/help/communities/file-library.md), en [&#x200B; commentaren &#x200B;](/help/communities/comments.md).

![&#x200B; volgend-mening &#x200B;](assets/following-activities.png)

**volgt** knoop een middel om ingangen als activiteiten, [&#x200B; berichten &#x200B;](/help/communities/notifications.md), of [&#x200B; abonnementen &#x200B;](/help/communities/subscriptions.md) te volgen. Telkens als **volgt** knoop wordt geselecteerd, is het mogelijk om op of van een selectie van een knevel te voorzien. De selectie van `Email Subscriptions` is alleen aanwezig als deze is geconfigureerd.

Als om het even welke methode van het volgende wordt geselecteerd, verandert de tekst van de knoop in **volgend**. Voor het gemak is het mogelijk om `Unfollow All` te selecteren om alle methoden uit te schakelen.

De **volg** knoop verschijnt:

* Bij weergave van het profiel van een ander lid.
* Op een hoofdpagina met functies, zoals forums, QnA en blogs.

   * Volg alle activiteiten voor die algemene functie.

* Voor een specifiek bericht, zoals een forumonderwerp, een QnA-vraag of een blogartikel.

   * Hiermee wordt alle activiteit voor die specifieke vermelding gevolgd.

### Aanvullende informatie {#additional-information}

Meer informatie kan op de [&#x200B; pagina van de Hoofdzaak van de Streams van de Activiteit &#x200B;](/help/communities/essentials-activities.md) voor ontwikkelaars worden gevonden.
