---
title: Mobiele toepassingen ontwerpen
description: Met het AEM Mobile-dashboard kunt u uw mobiele toepassing maken, bouwen en implementeren, toepassingsmetagegevens maken, verwijderen en bewerken. Volg deze pagina voor meer informatie.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
exl-id: 073daff7-0c1d-4715-bfd4-3e2336e4cb88
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 2dae56dc9ec66f1bf36bbb24d6b0315a5f5040bb
workflow-type: tm+mt
source-wordcount: '982'
ht-degree: 0%

---

# Mobiele toepassingen ontwerpen{#authoring-mobile-applications}

{{ue-over-mobile}}

Met het AEM Mobile-dashboard kunt u uw mobiele toepassing maken, bouwen en implementeren, toepassingsmetagegevens maken, verwijderen en bewerken. Zodra uw toepassing live is, kunt u toepassingsanalyses analyseren, waaronder levenscyclus en gebruiksmetriek om klantconversie en merkloyaliteit te verbeteren.

Om uw toepassing van AEM Mobile te bouwen, zie de [ Bouwend Mobiele pagina van Toepassingen ](/help/mobile/building-app-mobile-phonegap.md).

Aan opstelling uw milieu en begonnen worden, zie [ het Beheer AEM om de Onderneming van PhoneGap ](/help/mobile/administer-phonegap.md) te gebruiken AEM.

## De AEM Mobile Apps Catalog {#the-aem-mobile-apps-catalog}

De [ Catalogus van de Apps van AEM Mobile ](http://localhost:4502/aem/apps.html/content/phonegap) toont al uw mobiele die app in AEM wordt beheerd.

U kunt deze catalogus beschouwen als de &quot;bestemmingspagina&quot; voor AEM Mobile, waar beheerders een nieuwe AEM Mobile-toepassing kunnen starten door een sjabloon te maken of een bestaande toepassing te uploaden die al door een mobiele ontwikkelaar is gestart.

Ga als volgt te werk om naar de bestemmingspagina van de catalogus apps te gaan:

1. Blader aan **Navigatie** en kies dan **Mobiel**.

1. Kies **Apps** om de apps catalogus te openen.

![ AEM Mobile Apps Catalog ](assets/chlimage_1-135.png)

## Het AEM Mobile App-dashboard {#the-aem-mobile-app-dashboard}

Als u een AEM Mobile-toepassing in de catalogus selecteert, wordt het bijbehorende dashboard weergegeven. Hier kunt u uw toepassing beheren, statistieken bekijken, uw inhoud voor mobiele apps maken, implementeren en beheren.

U kunt elke tegel in het AEM Mobile-dashboard uitvouwen om details weer te geven of te bewerken door op de knop &#39;...&#39; in de rechterbenedenhoek te klikken.

![ Centrum van het Bevel van Toepassingen van AEM Mobile ](assets/chlimage_1-136.png)

### De app-tegel beheren {#the-manage-app-tile}

De Manage App Tegel toont uw toepassingspictogram, naam, beschrijving, gesteunde platforms, vraaghuis voor updates URL en versieinformatie. U kunt in deze tegel boren om de Configuratie van de Toepassing PhoneGap (config.xml) uit te geven en te handhaven en, uw toepassing voor voorlegging aan de diverse toepassingsopslag voor distributie voor te bereiden.

Klik [ hier ](/help/mobile/phonegap-app-details-tile.md) voor details.

![ chlimage_1-137 ](assets/chlimage_1-137.png)

### De pagina-inhoudtegel beheren {#the-manage-page-content-tile}

Inhoud kan in AEM Mobile op dezelfde manier worden gemaakt, bijgewerkt en verwijderd als in AEM Sites. **beheert de Tegel van de Inhoud van de Pagina** toont het aantal pagina&#39;s van beheerde inhoud en laatst gewijzigd. U kunt inhoud inroepen om pagina&#39;s te maken, kopiëren, verplaatsen, verwijderen en bijwerken door op elke record in de tegel te klikken. Zodra de inhoud is bijgewerkt, kunt u een inhoudsupdate aan uw klanten door **duwen leidt de Tegel van de Pakketten van de Inhoud.**

![ Content Tile ](assets/chlimage_1-138.png)

### De tegel Inhoud-pakketten beheren {#the-manage-content-packages-tile}

Nadat u de inhoud hebt toegevoegd of gewijzigd via de Content Tile van de Pagina beheren, kunt u deze wijzigingen doorsturen naar uw klanten met een update voor de inhoudsversie.

Het Pakket van de inhoud staat de AEM App Author toe om paginacontent in AEM te beheren en, uw ontwikkelingsteam uw Toepassing van Shell te hebben PhoneGap (namelijk app kader of infrastructuur) en dan die veranderingen uit te duwen aan uw klanten snel en zonder het moeten een ontwikkelaar ertoe aanzetten om aan de diverse opslag voor distributie opnieuw voor te leggen.

Met Inhoudspakket wordt voor elke update een ZIP-bestand gemaakt, dat wordt beschouwd als een pakket met de inhoudsversie. Deze pakketten bevatten HTML-bronnen en HTML-pagina&#39;s die tijdens het renderen van de app worden gegenereerd en zijn intelligent genoeg om alleen die bestanden te verpakken die sinds de laatste update zijn gewijzigd.

De Manage de kolomvertoningen van het Type van het Pakket van de Inhoud **** van het Pakket van de Inhoud {of &quot;App&quot;om de inhoud van Shell van de Toepassing, bijvoorbeeld, kader of infrastructuur van app te betekenen die door een ontwikkelaar wordt geleid of, &quot;Inhoud&quot;die pagina inhoud vertegenwoordigt die door de inhoudauteur wordt beheerd.

Inhoud kan worden weergegeven als een taal of als een bepaald deel van de app waarin meerdere pakketten voor inhoudsrelease worden gebruikt door de app. De manier waarop u uw inhoud bundelt, is flexibel en volledig geschikt voor het beheren van inhoud voor uw toepassing.

De **Gewijzigde** kolom wijst erop wanneer de pagina&#39;s onlangs werden gewijzigd.

De **Gelaagde** kolom toont toen de laatste inhoudsupdate werd gecreeerd. Als u een inhoudsupdate wilt maken en uw wijzigingen wilt uitvoeren, opent u alle records in de tegel en maakt u een update.

De **Gepubliceerde** kolom toont toen de laatste inhoudsupdate werd gepubliceerd en beschikbaar voor consumptie door uw klanten werd gemaakt. Als u inhoud wilt publiceren, moet u eerst die inhoud in het werkgebied plaatsen en de update vervolgens publiceren door naar deze tegel te boren en deze te publiceren via de detailconsole van de inhoudsrelease.

](assets/chlimage_1-139.png) ![ het pakket ContentSync van de Versie van de Inhoud 1} ![ Inhoud {](do-not-localize/chlimage_1-5.png)

Dit pictogram vertegenwoordigt een pakket met de inhoudsversie voor de app-shell

![ het pakketpictogram van de Versie van de Inhoud die door twee vierkant, overlappende pakketsymbolen wordt vermeld.](do-not-localize/chlimage_1-6.png)

Deze pictogrammen vertegenwoordigen een pakket met de inhoudsversie voor app-inhoud

### De PhoneGap Build-tegel {#the-phonegap-build-tile}

De **PhoneGap Build Tile** verbindt met `https://build.phonegap.com` om verre bouwstijlen te bouwen en te ontvangen. Nadat de build is gemaakt, wordt de build beschikbaar gesteld als een download of rechtstreeks aan uw apparaat via een QR-code.

Alternatief, kunt u de apparatenbron downloaden om plaatselijk door CLI te bouwen PhoneGap (`https://docs.phonegap.com/en/3.5.0/guide_cli_index.md.html`).

![ PhoneGap Build Tile ](assets/chlimage_1-140.png)

### De metrische tegel {#the-metrics-tile}

>[!CAUTION]
>
>De tegel Metrics wordt alleen weergegeven nadat u de cloudservice hebt geconfigureerd.
>
>Zie [ uw Cloud Service van de Diensten van de Adobe Mobiele ](/help/mobile/configure-adobe-mobile-cloud-service.md) voor details vormen.

AEM Mobile integreert met Adobe Analytics door [ de Mobiele Diensten SDK van de Adobe Mobiele ](https://experienceleague.adobe.com/docs/mobile.html) (AMS).

Het centrum van de Controle **Metriek Tile** toont summiere analyses die van AMS voor uw toepassing worden getrokken. U kunt naar het dashboard Analytics gaan door op &#39;...&#39; in de rechterbenedenhoek te klikken.

![ de Tegeltje van Metriek ](assets/chlimage_1-141.png)

### De Content-tegel Entiteit beheren {#the-manage-entity-content-tile}

Met de Content Tile van Entiteit beheren kunt u toepassingsdefinities toevoegen en beheren. Toepassingsdefinities zijn een manier om te bepalen welke spaties (en andere configuraties) geschikt zijn voor de app. Op deze manier kunt u een nieuwe spatie toevoegen zonder dat u de app opnieuw hoeft te compileren. De toepassingsdefinitie wordt bijgewerkt en bevat de informatie voor nieuwe spaties.

Klik [ hier ](/help/mobile/phonegap-app-definitions.md) om uw toepassingsdefinities tot stand te brengen en te beheren.

U kunt naar het beheerdersinhouddashboard gaan door op &#39;..&#39; in de rechterbenedenhoek te klikken.

![ chlimage_1-142 ](assets/chlimage_1-142.png)

#### Aanvullende bronnen {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwikkelen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/developing-in-phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)
