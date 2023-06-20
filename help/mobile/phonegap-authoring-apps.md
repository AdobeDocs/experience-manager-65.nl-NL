---
title: Mobiele toepassingen ontwerpen
seo-title: Authoring Mobile Applications
description: Met het AEM Mobile-dashboard kunt u uw mobiele toepassing maken, bouwen en implementeren, toepassingsmetagegevens maken, verwijderen en bewerken. Volg deze pagina voor meer informatie.
seo-description: he AEM Mobile Dashboard allows you to create, build and deploy your mobile application, create, delete and edit application metadata. Follow this page to learn more.
uuid: 293b5d29-df7e-42dd-ae64-8c677317e7a5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: abfeea65-102d-4800-abeb-304d61afcc13
exl-id: 073daff7-0c1d-4715-bfd4-3e2336e4cb88
source-git-commit: 17d13e9b201629d9d1519fde4740cf651fe89d2c
workflow-type: tm+mt
source-wordcount: '1005'
ht-degree: 0%

---

# Mobiele toepassingen ontwerpen{#authoring-mobile-applications}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework nodig hebben (bijvoorbeeld Reageren). [Meer informatie](/help/sites-developing/spa-overview.md).

Met het AEM Mobile-dashboard kunt u uw mobiele toepassing maken, bouwen en implementeren, toepassingsmetagegevens maken, verwijderen en bewerken. Zodra uw toepassing live is, kunt u toepassingsanalyses analyseren, waaronder levenscyclus en gebruiksmetriek om klantconversie en merkloyaliteit te verbeteren.

Als u uw AEM Mobile-toepassing wilt maken, raadpleegt u de [Mobiele toepassingen maken](/help/mobile/building-app-mobile-phonegap.md) pagina.

Ga naar [AEM beheren voor gebruik AEM PhoneGap Enterprise](/help/mobile/administer-phonegap.md).

## De AEM Mobile Apps Catalog {#the-aem-mobile-apps-catalog}

De [Catalogus AEM Mobile-toepassingen](http://localhost:4502/aem/apps.html/content/phonegap) geeft alle mobiele apps weer die in AEM worden beheerd.

U kunt deze catalogus beschouwen als de &quot;bestemmingspagina&quot; voor AEM Mobile, waar beheerders een nieuwe AEM Mobile-toepassing kunnen starten door een sjabloon te maken of een bestaande toepassing te uploaden die al door een mobiele ontwikkelaar is gestart.

Ga als volgt te werk om naar de bestemmingspagina van de catalogus apps te gaan:

1. Bladeren naar **Navigatie** en kies vervolgens **Mobiel**.

1. Kies **Apps** om de catalogus met apps te openen.

![Catalogus AEM Mobile-toepassingen](assets/chlimage_1-135.png)

## Het AEM Mobile App-dashboard {#the-aem-mobile-app-dashboard}

Als u een AEM Mobile-toepassing in de catalogus selecteert, wordt het bijbehorende dashboard weergegeven. Hier kunt u uw toepassing beheren, statistieken bekijken, uw inhoud voor mobiele apps maken, implementeren en beheren.

U kunt elke tegel in het AEM Mobile-dashboard uitvouwen om details weer te geven of te bewerken door op de knop &#39;..&#39; te klikken. in de rechterbenedenhoek.

![AEM Mobile Applications Command Center](assets/chlimage_1-136.png)

### De app-tegel beheren {#the-manage-app-tile}

De Manage App Tegel toont uw toepassingspictogram, naam, beschrijving, gesteunde platforms, vraaghuis voor updates URL en versieinformatie. U kunt in deze tegel boren om de Configuratie van de Toepassing PhoneGap (config.xml) uit te geven en te handhaven en, uw toepassing voor voorlegging aan de diverse toepassingsopslag voor distributie voor te bereiden.

Klikken [hier](/help/mobile/phonegap-app-details-tile.md) voor meer informatie.

![chlimage_1-137](assets/chlimage_1-137.png)

### De pagina-inhoudtegel beheren {#the-manage-page-content-tile}

Inhoud kan in AEM Mobile op dezelfde manier worden gemaakt, bijgewerkt en verwijderd als in AEM Sites. De **Tile met pagina-inhoud beheren** Hiermee geeft u het aantal pagina&#39;s met beheerde inhoud en de laatst gewijzigde inhoud weer. U kunt inhoud inroepen om pagina&#39;s te maken, kopiëren, verplaatsen, verwijderen en bijwerken door op elke record in de tegel te klikken. Als de inhoud eenmaal is bijgewerkt, kunt u via de **De Content Packages Tile beheren.**

![Content Tile](assets/chlimage_1-138.png)

### De tegel Inhoud-pakketten beheren {#the-manage-content-packages-tile}

Nadat u de inhoud hebt toegevoegd of gewijzigd via de Content Tile van de Pagina beheren, kunt u deze wijzigingen doorsturen naar uw klanten met een update voor de inhoudsversie.

Met het inhoudspakket kan de AEM App Author pagina-inhoud beheren in AEM en kan uw ontwikkelingsteam wijzigingen aanbrengen in uw PhoneGap Shell-toepassing (dat wil zeggen, toepassingsframework of infrastructuur) en deze wijzigingen vervolgens snel en zonder dat een ontwikkelaar zich hoeft aan te melden bij de verschillende winkels voor distributie.

Met Inhoudspakket wordt voor elke update een ZIP-bestand gemaakt, dat wordt beschouwd als een pakket met de inhoudsversie. Deze pakketten bevatten HTML-bronnen en HTML-pagina&#39;s die tijdens het renderen van de app worden gegenereerd en zijn intelligent genoeg om alleen die bestanden te verpakken die sinds de laatste update zijn gewijzigd.

De tegels van het inhoudspakket beheren **Type** de kolomvertoningen of &quot;App&quot;om de inhoud van Shell van de Toepassing, bijvoorbeeld kader of infrastructuur van app te betekenen die door een ontwikkelaar wordt geleid of, &quot;Inhoud&quot;die pagina inhoud vertegenwoordigt die door de inhoudauteur wordt beheerd.

Inhoud kan worden weergegeven als een taal of als een bepaald deel van de app waarin meerdere pakketten voor inhoudsrelease worden gebruikt door de app. De manier waarop u uw inhoud bundelt, is flexibel en volledig geschikt voor het beheren van inhoud voor uw toepassing.

De **Gewijzigd** de kolom geeft aan wanneer de pagina&#39;s voor het laatst zijn gewijzigd.

De **Staand** wordt weergegeven wanneer de laatste inhoudsupdate is gemaakt. Als u een inhoudsupdate wilt maken en uw wijzigingen wilt uitvoeren, opent u alle records in de tegel en maakt u een update.

De **Gepubliceerd** de kolom toont wanneer de laatste inhoudsupdate werd gepubliceerd en voor consumptie door uw klanten ter beschikking gesteld. Als u inhoud wilt publiceren, moet u eerst die inhoud in het werkgebied plaatsen en de update vervolgens publiceren door naar deze tegel te boren en deze te publiceren via de detailconsole van de inhoudsrelease.

![Content Release Tile](assets/chlimage_1-139.png) ![ContentSync-pakket voor de app-shell](do-not-localize/chlimage_1-5.png)

Dit pictogram vertegenwoordigt een pakket met de inhoudsversie voor de app-shell

![](do-not-localize/chlimage_1-6.png)

Deze pictogrammen vertegenwoordigen een pakket met de inhoudsversie voor app-inhoud

### De PhoneGap Build-tegel {#the-phonegap-build-tile}

De **PhoneGap Build-tegel** verbindt met `https://build.phonegap.com` om verre bouwstijlen te bouwen en te ontvangen. Nadat de build is gemaakt, wordt de build beschikbaar gesteld als een download of rechtstreeks aan uw apparaat via een QR-code.

U kunt ook de apparaatbron downloaden om lokaal te bouwen via de PhoneGap CLI (`https://docs.phonegap.com/en/3.5.0/guide_cli_index.md.html`).

![PhoneGap Build-tegel](assets/chlimage_1-140.png)

### De metrische tegel {#the-metrics-tile}

>[!CAUTION]
>
>De tegel Metrics wordt alleen weergegeven nadat u de cloudservice hebt geconfigureerd.
>
>Zie [Uw Adobe Mobile Services-Cloud Service configureren](/help/mobile/configure-adobe-mobile-cloud-service.md) voor meer informatie.

AEM Mobile integreert met Adobe Analytics via [Adobe Mobile Services SDK](https://experienceleague.adobe.com/docs/mobile.html?lang=en) (AMS).

Het controlecentrum **Metrische tegel** geeft een overzichtsanalyse weer die door AMS voor uw toepassing is gemaakt. U kunt naar het dashboard Analytics gaan door op &#39;...&#39; te klikken. rechtsonder.

![Metrische tegel](assets/chlimage_1-141.png)

### De Content-tegel Entiteit beheren {#the-manage-entity-content-tile}

Met de Content Tile van Entiteit beheren kunt u toepassingsdefinities toevoegen en beheren. Toepassingsdefinities zijn een manier om te bepalen welke spaties (en andere configuraties) geschikt zijn voor de app. Op deze manier kunt u een nieuwe spatie toevoegen zonder dat u de app opnieuw hoeft te compileren. De toepassingsdefinitie wordt bijgewerkt en bevat de informatie voor nieuwe spaties.

Klikken [hier](/help/mobile/phonegap-app-definitions.md) om uw toepassingsdefinities te maken en te beheren.

U kunt naar het beheerdersinhouddashboard gaan door op &#39;..&#39; te klikken. rechtsonder.

![chlimage_1-142](assets/chlimage_1-142.png)

#### Aanvullende bronnen {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwikkelen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/developing-in-phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)
