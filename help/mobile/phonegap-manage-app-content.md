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
workflow-type: tm+mt
source-wordcount: '742'
ht-degree: 0%

---


# Toepassingsinhoud maken en beheren{#creating-and-managing-app-content}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

Voor het beheren van toepassingsinhoud is een collectieve inspanning van [developers](#developer), content [auteurs](#author) en [beheerders](#administrator) vereist. Auteurs manipuleren pagina&#39;s, die op hun beurt gebaseerd zijn op sjablonen en componenten die door ontwikkelaars van apps worden gegenereerd.

Tot slot publiceren beheerders strategisch de bijgewerkte app-inhoud.

>[!NOTE]
>
>**Vereiste**:
>
>In [Implementeren en onderhouden](/help/sites-deploying/deploy.md) werden ontwikkelaars vertrouwd met AEM systeem van componenten en sjablonen.

## De pagina-inhoudtegel beheren {#the-manage-page-content-tile}

>[!CAUTION]
>
>Als u geen out-of-the-box toepassingsmalplaatje gebruikt, moet u een manager van de Synchronisatie van de Inhoud vormen om nieuwe toepassingsinhoud toe te laten om worden gepubliceerd OTA.
>
>Zie [Mobiel met inhoudssynchronisatie](/help/mobile/phonegap-contentsync.md) in de sectie Ontwikkelaar voor meer informatie.

Hier kunt u inhoud maken, bewerken en verwijderen in AEM Mobile, net als in AEM Sites.

In de **Tile van de pagina-inhoud beheren** wordt het aantal pagina&#39;s met beheerde inhoud weergegeven en de laatste pagina die voor een bepaalde lading is gewijzigd. U kunt inhoud inchecken om pagina&#39;s te maken, kopiëren, verplaatsen, verwijderen en bijwerken door op elke record in de tegel te klikken.

Als de inhoud eenmaal is bijgewerkt, kunnen beheerders via de **Tile Content Packages TileLoad Over-the-Air (OTA) naar klanten publiceren voor het bijwerken van inhoud.**

![chlimage_1-161](assets/chlimage_1-161.png)

Selecteer een van de weergegeven inhoudspakketten om inhoud te maken of te bewerken, zoals het maken, bewerken of verwijderen van pagina&#39;s, het wijzigen van navigatie en paginavolgorde, het maken of bijwerken van inhoud, zoals kopiëren (tekst) en media.

Opmerking *alles is inhoud*. Dit houdt in dat toepassingsstijlen, kopiëren (tekst), media, pagina&#39;s, navigatie en doelversie van inhoud allemaal kunnen worden bewerkt en bijgewerkt, zonder dat er naar een App Store hoeft te worden gegaan.

Voor het bewerken van AEM Mobile-inhoud hebben *AEM auteurs *een gedegen kennis nodig van de interface voor het bewerken van AEM inhoud: [Pagina&#39;s ontwerpen in AEM.](/help/sites-authoring/qg-page-authoring.md)

## De Content Packages-tegel beheren {#the-manage-content-packages-tile}

Hier kunnen *AEM Beheerders* hun toepassingen snel en eenvoudig bijwerken om boeiende ervaringen en actuele inhoud te bieden om de betrokkenheid van merken te stimuleren en zakelijke doelen te halen zonder dat een ontwikkelaar of app store opnieuw hoeft te worden ingediend.

![chlimage_1-162](assets/chlimage_1-162.png)

Als *AEM-auteurs* eenmaal inhoud hebben toegevoegd of gewijzigd via de Content Tile beheren, kunnen *AEM Beheerders* deze wijzigingen doorsturen naar klanten met een Content Packages-update.

Met de actie Inhoudspakket kan de *AEM-auteur* pagina-inhoud maken en bewerken, terwijl het ontwikkelingsteam wijzigingen aanbrengt in het ontwerp en de implementatie van een hosttoepassing, zoals navigatie, stijl, logica aan de serverzijde, sjablonen en componenten, en deze wijzigingen vervolgens naar klanten doorvoert zonder opnieuw naar de verschillende winkels te moeten verzenden voor distributie.

**Nieuwe of bijgewerkte inhoud publiceren**

Selecteer een inhoudspakket uit de tegel, in dit voorbeeld het Engelse pakket. Een dialoogvenster voor het bijwerken van inhoud bevat de relevante *Configuratie van Content Sync*. Als de toepassingsinhoud sinds een vorige update is gewijzigd, zal de status *Pending*, zoals hieronder getoond tonen.

![chlimage_1-163](assets/chlimage_1-163.png)

Selecteer vervolgens de handeling **Stage** rechtsboven om de nieuwe inhoudsupdate te maken. Voeg de juiste updategegevens toe en druk op Gereed.

![chlimage_1-164](assets/chlimage_1-164.png)

De *handler Content Sync* maakt vervolgens de vereiste pakketten door een delta te vormen (een pakket van *only* wat is gewijzigd). Zodra dit pakket met update-inhoud is voltooid, wordt het gefaseerd bijgewerkt, zoals hieronder wordt weergegeven.

Door een update van de inhoud te organiseren, kunnen verschillende updates worden uitgevoerd voordat deze naar OTA worden gepubliceerd naar mobiele apparaten.

>[!NOTE]
>
>De gefaseerde inhoud kan worden geverifieerd met de app AEM verifiëren voordat deze wordt gepubliceerd.
>
>Zie [Mobiele QuickStart voor AEM Verifiëren](/help/mobile/phonegap-mobile-quickstart.md) voor meer informatie over AEM app verifiëren.

![chlimage_1-165](assets/chlimage_1-165.png)

Wanneer u klaar bent om nieuwe inhoud aan uw gebruikers van de app te leveren met Content Sync OTA, selecteert u **Publiceren** zoals hieronder wordt weergegeven.

![chlimage_1-166](assets/chlimage_1-166.png)

### De volgende stappen {#the-next-steps}

Nadat u informatie hebt gekregen over het maken en beheren van App-inhoud in het dashboard van de toepassing, raadpleegt u de volgende bronnen voor andere ontwerprollen:

* [De app-tegel beheren](/help/mobile/phonegap-app-details-tile.md)
* [App-metagegevens bewerken](/help/mobile/phonegap-editmetadata.md)
* [Toepassingsdefinities](/help/mobile/phonegap-app-definitions.md)
* [Een nieuwe app maken met de wizard App maken](/help/mobile/phonegap-create-new-app.md)
* [Een bestaande hybride app importeren](/help/mobile/phonegap-adding-content-to-imported-app.md)

### Aanvullende bronnen {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwikkelen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/developing-in-phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)
