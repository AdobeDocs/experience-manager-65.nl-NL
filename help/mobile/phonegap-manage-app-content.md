---
title: App-inhoud maken en beheren
seo-title: App-inhoud maken en beheren
description: Voor het beheren van app-inhoud is een gezamenlijke inspanning van ontwikkelaars, makers van inhoud en beheerders vereist.  Auteurs manipuleren pagina's, die op hun beurt gebaseerd zijn op sjablonen en componenten die door ontwikkelaars van apps worden gegenereerd.
seo-description: Voor het beheren van app-inhoud is een gezamenlijke inspanning van ontwikkelaars, makers van inhoud en beheerders vereist.  Auteurs manipuleren pagina's, die op hun beurt gebaseerd zijn op sjablonen en componenten die door ontwikkelaars van apps worden gegenereerd.
uuid: ca049bad-9be8-47aa-b010-298258feda26
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: 5c8971ab-b07c-4131-b4cb-f34c52425014
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# App-inhoud maken en beheren{#creating-and-managing-app-content}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

Voor het beheren van app-inhoud is een gezamenlijke inspanning van [ontwikkelaars](#developer), [auteurs](#author) van inhoud en [beheerders](#administrator)vereist. Auteurs manipuleren pagina&#39;s, die op hun beurt gebaseerd zijn op sjablonen en componenten die door ontwikkelaars van apps worden gegenereerd.

Tot slot publiceren beheerders strategisch de bijgewerkte app-inhoud.

>[!NOTE]
>
>**Vereiste**:
>
>Bij het [Opstellen en het Onderhouden](/help/sites-deploying/deploy.md), werden de ontwikkelaars vertrouwd met het systeem van componenten en malplaatjes van AEM.

## De pagina-inhoudtegel beheren {#the-manage-page-content-tile}

>[!CAUTION]
>
>Als u geen out-of-the-box toepassingsmalplaatje gebruikt, moet u een manager van de Synchronisatie van de Inhoud vormen om nieuwe toepassingsinhoud toe te laten om worden gepubliceerd OTA.
>
>Zie [Mobiel met inhoudssynchronisatie](/help/mobile/phonegap-contentsync.md) in de sectie Ontwikkelaar voor meer informatie.

Hier kan inhoud worden gemaakt, bewerkt en verwijderd in AEM Mobile, net als in AEM-sites.

In de tegel **Pagina-inhoud** beheren wordt het aantal pagina&#39;s met beheerde inhoud weergegeven en het laatst gewijzigd voor een bepaalde lading. U kunt inhoud inchecken om pagina&#39;s te maken, kopiëren, verplaatsen, verwijderen en bijwerken door op elke record in de tegel te klikken.

Zodra de inhoud is bijgewerkt, kunnen beheerders een lading van de inhoudsupdate over-the-Air (OTA) aan klanten door de **Manage Tile van de Pakketten van de Inhoud publiceren.**

![chlimage_1-161](assets/chlimage_1-161.png)

Selecteer een van de weergegeven inhoudspakketten om inhoud te maken of te bewerken, zoals het maken, bewerken of verwijderen van pagina&#39;s, het wijzigen van navigatie en paginavolgorde, het maken of bijwerken van inhoud, zoals kopiëren (tekst) en media.

Houd er rekening mee dat *alles inhoud* is, wat betekent dat toepassingsstijlen, kopiëren (tekst), media, pagina&#39;s, navigatie en doelversie van inhoud kunnen worden bewerkt en bijgewerkt, zonder dat er een trip naar een App Store plaatsvindt.

*Voor het bewerken van AEM Mobile-inhoud hebben *AEM-auteurs *een gedegen inzicht nodig in de interface voor het bewerken van inhoud van AEM: Pagina&#39;s [ontwerpen in AEM.](/help/sites-authoring/qg-page-authoring.md)

## De tegel Inhoud-pakketten beheren {#the-manage-content-packages-tile}

Hier kunnen *AEM-beheerders* hun apps snel en eenvoudig bijwerken om aantrekkelijke ervaringen en actuele inhoud te bieden, zodat ze de betrokkenheid van merken kunnen stimuleren en zakelijke doelen kunnen halen, zonder dat een ontwikkelaar of app store opnieuw hoeft te worden ingediend.

![chlimage_1-162](assets/chlimage_1-162.png)

Zodra *AEM-auteurs* inhoud hebben toegevoegd of gewijzigd via de Content Tile beheren, kunnen *AEM-beheerders* deze wijzigingen doorsturen naar klanten met een Content Packages-update.

Met de actie Content Package kan de *AEM-auteur* pagina-inhoud maken en bewerken, terwijl het ontwikkelingsteam wijzigingen aanbrengt in het ontwerp en de implementatie van een hosttoepassing, zoals navigatie, stijl, logica aan de serverzijde, sjablonen en componenten, en deze wijzigingen vervolgens naar klanten verstuurt zonder opnieuw naar de verschillende winkels te moeten verzenden voor distributie.

**Nieuwe of bijgewerkte inhoud publiceren**

Selecteer een inhoudspakket uit de tegel, in dit voorbeeld het Engelse pakket. Een dialoogvenster voor het bijwerken van inhoud bevat de relevante configuratie voor *inhoudssynchronisatie* . Als de inhoud van de app sinds een vorige update is gewijzigd, wordt de status *In behandeling* weergegeven, zoals hieronder wordt weergegeven.

![chlimage_1-163](assets/chlimage_1-163.png)

Selecteer vervolgens de actie **Stage** rechtsboven om de nieuwe inhoudsupdate te maken. Voeg de juiste updategegevens toe en druk op Gereed.

![chlimage_1-164](assets/chlimage_1-164.png)

De handler *Content Sync* maakt vervolgens de vereiste pakketten door een delta te vormen (een pakket *alleen* wat is gewijzigd). Zodra dit pakket met update-inhoud is voltooid, wordt het gefaseerd bijgewerkt, zoals hieronder wordt weergegeven.

Door een update van de inhoud te organiseren, kunnen verschillende updates worden uitgevoerd voordat deze naar OTA worden gepubliceerd naar mobiele apparaten.

>[!NOTE]
>
>De gefaseerde inhoud kan worden geverifieerd met de app AEM Verify voordat deze wordt gepubliceerd.
>
>Zie [Mobile Quickstart voor AEM Verify](/help/mobile/phonegap-mobile-quickstart.md) voor meer informatie over de app AEM Verify.

![chlimage_1-165](assets/chlimage_1-165.png)

Wanneer u klaar bent om nieuwe inhoud aan uw gebruikers van de app te leveren met Content Sync OTA, selecteert u **Publiceren** zoals hieronder wordt weergegeven.

![chlimage_1-166](assets/chlimage_1-166.png)

### De volgende stappen {#the-next-steps}

Nadat u informatie hebt gekregen over het maken en beheren van App-inhoud in het toepassingsdashboard, raadpleegt u de volgende bronnen voor andere ontwerprollen:

* [De app-tegel beheren](/help/mobile/phonegap-app-details-tile.md)
* [App-metagegevens bewerken](/help/mobile/phonegap-editmetadata.md)
* [Toepassingsdefinities](/help/mobile/phonegap-app-definitions.md)
* [Een nieuwe app maken met de wizard App maken](/help/mobile/phonegap-create-new-app.md)
* [Een bestaande hybride app importeren](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Additional Resources {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwikkelen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/developing-in-phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)
