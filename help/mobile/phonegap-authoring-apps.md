---
title: Mobiele toepassingen ontwerpen
seo-title: Mobiele toepassingen ontwerpen
description: Met het AEM Mobile-dashboard kunt u uw mobiele toepassing maken, bouwen en implementeren, toepassingsmetagegevens maken, verwijderen en bewerken. Volg deze pagina voor meer informatie.
seo-description: Met het AEM Mobile-dashboard kunt u uw mobiele toepassing maken, bouwen en implementeren, toepassingsmetagegevens maken, verwijderen en bewerken. Volg deze pagina voor meer informatie.
uuid: 293b5d29-df7e-42dd-ae64-8c677317e7a5
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: abfeea65-102d-4800-abeb-304d61afcc13
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Mobiele toepassingen ontwerpen{#authoring-mobile-applications}

>[!NOTE]
>
>Adobe adviseert gebruikend de Redacteur van het KUUROORD voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (b.v. Reageren) vereisen. [Meer](/help/sites-developing/spa-overview.md)informatie.

Met het AEM Mobile-dashboard kunt u uw mobiele toepassing maken, bouwen en implementeren, toepassingsmetagegevens maken, verwijderen en bewerken. Zodra uw toepassing live is, kunt u toepassingsanalyses analyseren, waaronder levenscyclus en gebruiksmetriek om klantconversie en merkloyaliteit te verbeteren.

Raadpleeg de pagina Mobiele toepassingen [maken voor](/help/mobile/building-app-mobile-phonegap.md) AEM Mobile.

Zie AEM [beheren voor gebruik van AEM PhoneGap Enterprise](/help/mobile/administer-phonegap.md)om uw omgeving in te stellen en aan de slag te gaan.

## De catalogus voor AEM Mobile-apps {#the-aem-mobile-apps-catalog}

In de catalogus met [AEM Mobile-apps](http://localhost:4502/aem/apps.html/content/phonegap) worden alle mobiele apps weergegeven die in AEM worden beheerd.

U kunt deze catalogus beschouwen als de &#39;bestemmingspagina&#39; voor AEM Mobile, waar beheerders een nieuwe AEM Mobile-toepassing kunnen starten door een nieuwe AEM Mobile-toepassing te maken op basis van een sjabloon of door een bestaande toepassing te uploaden die al door een mobiele ontwikkelaar is gestart.

Ga als volgt te werk om naar de bestemmingspagina van de catalogus apps te gaan:

1. Blader naar **Navigatie** en kies vervolgens **Mobiel**.

1. Kies **Apps** om de catalogus met apps te openen.

![Catalogus voor AEM Mobile-apps](assets/chlimage_1-135.png)

## Het AEM Mobile-toepassingsdashboard {#the-aem-mobile-app-dashboard}

Als u een AEM Mobile-toepassing selecteert uit de catalogus, wordt het dashboard weergegeven. Hier kunt u uw toepassing beheren, statistieken bekijken, uw inhoud voor mobiele apps maken, implementeren en beheren.

U kunt in elke tegel in het mobiele dashboard van AEM uitvouwen om details te bekijken of uit te geven door te klikken &#39;...&#39; in de rechterbenedenhoek.

![Opdrachtcentrum voor AEM Mobile-toepassingen](assets/chlimage_1-136.png)

### De app-tegel beheren {#the-manage-app-tile}

De Manage App Tegel toont uw toepassingspictogram, naam, beschrijving, gesteunde platforms, vraaghuis voor updates URL en versieinformatie. U kunt in deze tegel boren om de Configuratie van de Toepassing PhoneGap (config.xml) uit te geven en te handhaven en, uw toepassing voor voorlegging aan de diverse toepassingsopslag voor distributie voor te bereiden.

Klik [hier](/help/mobile/phonegap-app-details-tile.md) voor meer informatie.

![chlimage_1-137](assets/chlimage_1-137.png)

### De pagina-inhoudtegel beheren {#the-manage-page-content-tile}

Inhoud kan in AEM Mobile op ongeveer dezelfde manier worden gemaakt, bijgewerkt en verwijderd als in AEM Sites. In de **Tegel** Pagina-inhoud beheren wordt het aantal pagina&#39;s met beheerde inhoud en de laatste wijziging weergegeven. U kunt inhoud inchecken om pagina&#39;s te maken, kopiëren, verplaatsen, verwijderen en bijwerken door op elke record in de tegel te klikken. Als de inhoud eenmaal is bijgewerkt, kunt u een update van de inhoud naar uw klanten uitvoeren via de **Content Packages Tile beheren.**

![Content Tile](assets/chlimage_1-138.png)

### De tegel Inhoud-pakketten beheren {#the-manage-content-packages-tile}

Nadat u de inhoud hebt toegevoegd of gewijzigd via de Content Tile van de Pagina beheren, kunt u deze wijzigingen doorsturen naar uw klanten met een update voor de inhoudsversie.

Met het inhoudspakket kan de AEM App Author pagina-inhoud in AEM beheren en kan uw ontwikkelingsteam wijzigingen aanbrengen in uw PhoneGap Shell-toepassing (d.w.z. toepassingsframework of infrastructuur) en deze wijzigingen vervolgens snel en zonder dat een ontwikkelaar zich hoeft aan te melden bij de verschillende winkels voor distributie.

Met Inhoudspakket wordt voor elke update een ZIP-bestand gemaakt, dat wordt beschouwd als een pakket met de inhoudsversie. Deze pakketten bevatten HTML-bronnen en HTML-pagina&#39;s die tijdens het renderen van de app worden gegenereerd en zijn intelligent genoeg om alleen die bestanden te verpakken die sinds de laatste update zijn gewijzigd.

In de kolom **Type** van Content Package Tile beheren wordt &#39;&#39;App&#39;&#39; weergegeven om de inhoud van Shell van een toepassing aan te duiden, bijvoorbeeld het framework of de infrastructuur van de toepassing die door een ontwikkelaar wordt beheerd, of &#39;&#39;Content&#39;&#39; dat pagina-inhoud vertegenwoordigt die door de auteur van de inhoud wordt beheerd.

Inhoud kan worden weergegeven als een taal of als een bepaald deel van de app waarin meerdere pakketten voor inhoudsrelease worden gebruikt door de app. De keuze van de manier waarop u uw inhoud bundelt, is ontworpen om flexibel te zijn en volledig te beantwoorden aan de manier waarop u inhoud voor uw toepassing wilt beheren.

De kolom **Gewijzigd** geeft aan wanneer de pagina&#39;s het laatst zijn gewijzigd.

De kolom **Staged** toont toen de laatste inhoudsupdate werd gecreeerd. Als u een nieuwe inhoudsupdate wilt maken en uw wijzigingen wilt uitvoeren, opent u alle records in de tegel en maakt u een nieuwe update.

De **Gepubliceerde** kolom toont toen de laatste inhoudsupdate werd gepubliceerd en voor consumptie door uw klanten ter beschikking werd gesteld. Als u inhoud wilt publiceren, moet u eerst die inhoud in het werkgebied plaatsen en de update vervolgens publiceren door naar deze tegel te boren en deze te publiceren via de detailconsole van de inhoudsrelease.

![Content Release Tile](assets/chlimage_1-139.png) ![ContentSync-pakket voor app-shell](do-not-localize/chlimage_1-5.png)

Dit pictogram vertegenwoordigt een pakket met de inhoudsversie voor de app-shell

![](do-not-localize/chlimage_1-6.png)

Deze pictogrammen vertegenwoordigen een pakket Inhoud vrijgeven voor app-inhoud

### De PhoneGap Build-tegel {#the-phonegap-build-tile}

De **PhoneGap Build Tile** maakt verbinding met [https://build.phonegap.com](https://build.phonegap.com) om externe buids te maken en te hosten. Nadat de build is gemaakt, wordt de build beschikbaar gesteld als een download of rechtstreeks aan uw apparaat via een QR-code.

U kunt ook de apparaatbron downloaden om lokaal te bouwen via de [PhoneGap CLI](https://docs.phonegap.com/en/3.5.0/guide_cli_index.md.html).

![PhoneGap Build-tegel](assets/chlimage_1-140.png)

### De metrische tegel {#the-metrics-tile}

>[!CAUTION]
>
>De tegel Metrics wordt alleen weergegeven nadat u de cloudservice hebt geconfigureerd.
>
>Zie [Uw Adobe Mobile Services Cloud Service](/help/mobile/configure-adobe-mobile-cloud-service.md) configureren voor meer informatie.

AEM Mobile integreert met Adobe Analytics via [Adobe Mobile Services SDK](https://www.adobe.com/ca/solutions/digital-marketing/mobile-services/app-sdk.html) (AMS).

De **Metrics Tile** van het Centrum van de Controle de summiere analyses van AMS voor uw toepassing worden getrokken. U kunt naar het dashboard Analytics gaan door op &#39;...&#39; te klikken. rechtsonder.

![Metrische tegel](assets/chlimage_1-141.png)

### De Content-tegel Entiteit beheren {#the-manage-entity-content-tile}

Met de Content Tile van Entiteit beheren kunt u toepassingsdefinities toevoegen en beheren. Toepassingsdefinities zijn een manier om te bepalen welke spaties (en andere configuraties) geschikt zijn voor de app. Op deze manier kunt u een nieuwe spatie toevoegen zonder dat u de app opnieuw hoeft te compileren. De toepassingsdefinitie wordt bijgewerkt en bevat de informatie voor nieuwe spaties.

Klik [hier](/help/mobile/phonegap-app-definitions.md) om uw toepassingsdefinities te maken en te beheren.

U kunt naar het dashboard voor beheerinhoud van entiteit gaan door op &#39;..&#39; te klikken. rechtsonder.

![chlimage_1-142](assets/chlimage_1-142.png)

#### Additional Resources {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwikkelen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/developing-in-phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)

