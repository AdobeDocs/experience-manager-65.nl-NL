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
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Functie voor activiteitsstromen{#activity-streams-feature}

## Inleiding {#introduction}

De activiteiten van een getekend lid van de gemeenschap, zoals posten op een forum of blog, worden verzameld in een stream die op verschillende manieren kan worden gefilterd en weergegeven door de configuratie van de `Activity Streams` component.

De mogelijkheid om te volgen voegt nog een weergave van activiteiten toe wanneer leden van de gemeenschap belangenverklaringen volgen of de activiteiten van andere leden van de gemeenschap volgen.

In het document wordt beschreven:

* toevoegen van de component van de Streams van de Activiteit aan een plaats AEM
* configuratie-instellingen voor de component Activiteitenstromen

### Activiteitsstromen toevoegen aan een pagina {#adding-activity-streams-to-a-page}

Als u een `Activity Streams` component in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Activity Streams`

en sleep het naar de juiste plaats op een pagina waar de activiteitenstromen moeten verschijnen.

Ga voor de benodigde informatie naar [Community Components Basics](/help/communities/basics.md).

Wanneer de [vereiste client-side bibliotheken](/help/communities/essentials-activities.md#essentials-for-client-side) worden opgenomen, ziet u zo de `Activity Streams` component eruit:

![chlimage_1-24](assets/chlimage_1-24.png)

### Activiteitenstromen configureren {#configuring-activity-streams}

Selecteer de geplaatste `Activity Streams` component die u wilt openen en selecteer het `Configure` pictogram waarmee het dialoogvenster Bewerken wordt geopend.

![chlimage_1-25](assets/chlimage_1-25.png)

Geef op onder het tabblad **Gebruikersactiviteiten** op welke activiteiten u wilt weergeven:

![chlimage_1-26](assets/chlimage_1-26.png)

* **Max. aantal activiteiten** het aantal weer te geven activiteiten

* **Het Pad** van het Middel van de stroom laat leeg aan gebrek aan de communautaire plaats of de communautaire groep. Het pad naar de streambron identificeert de bron van activiteiten. De standaardwaarde is leeg.

* **De Mening** van de Activiteiten van de Gebruiker van de vertoning indien gecontroleerd, zal de activiteitenpagina een lusje omvatten dat activiteiten filtert die op die binnen de gemeenschap door het huidige lid worden geproduceerd. Standaard is ingeschakeld.

* **Geef de weergave** van alle activiteiten weer als deze is ingeschakeld, op de pagina Activiteiten een tabblad wordt weergegeven met alle activiteiten die binnen de gemeenschap zijn gegenereerd waartoe het huidige lid toegang heeft. Standaard is ingeschakeld.

* **Weergeven na weergave** als deze optie is ingeschakeld, bevat de pagina Activiteiten een tabblad waarop de activiteiten worden gefilterd op basis van de activiteiten die het huidige lid volgt. Standaard is ingeschakeld.

### Volgende weergave {#following-view}

Componenten moeten worden geconfigureerd om het volgende in te schakelen. Functies die het volgende toestaan, zijn [blog](/help/communities/blog-feature.md), [forum](/help/communities/forum.md), [QnA](/help/communities/working-with-qna.md), [agenda](/help/communities/calendar.md), [bestandsbibliotheek](/help/communities/file-library.md)[](/help/communities/comments.md)en commentaren.

![chlimage_1-27](assets/chlimage_1-27.png)

Met de knop **Volg **Hier kunt u items opvolgen als activiteiten, [meldingen](/help/communities/notifications.md)of [abonnementen](/help/communities/subscriptions.md). Telkens wanneer de knop **Volg **gebruiken is geselecteerd, kunt u een selectie in- of uitschakelen. De `Email Subscriptions` selectie is alleen aanwezig als deze is geconfigureerd.

Als er een methode van het volgende is geselecteerd, verandert de tekst van de knop in **Volgende**. Voor het gemak is het mogelijk om alle methoden uit `Unfollow All` te schakelen.

De knop **Volg **De wordt weergegeven

* bij het bekijken van het profiel van een ander lid
* op een hoofdpagina met functies, zoals forums, QnA en blogs

   * volgt alle activiteiten voor dat algemene kenmerk

* voor een specifiek bericht, zoals een forumonderwerp, een QnA-vraag of een blogartikel

   * volgt alle activiteiten voor die specifieke vermelding

### Additional Information {#additional-information}

Meer informatie vindt u op de pagina [Activiteitenstromen](/help/communities/essentials-activities.md) voor ontwikkelaars.
