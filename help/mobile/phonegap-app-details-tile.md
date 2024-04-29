---
title: App-tegel beheren
description: Meer informatie over de tegel "App beheren" op het dashboard van de app vindt u waarin u details over de toepassing kunt bewerken.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
exl-id: 8bcf70ef-94d2-4958-90b5-bc375b360916
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1218'
ht-degree: 0%

---

# App-tegel beheren{#manage-app-tile}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [Meer informatie](/help/sites-developing/spa-overview.md).

De **`Manage App`** kunt u details over de toepassing bewerken met de tegel op het dashboard van de app. Klik op de pagina Details om deze te openen **`Manage App`** de detaillink van de tegel. Van binnen **`Manage App`** pagina, kunt u de montages van de Configuratie van de Toepassing van PhoneGap (config.xml) uitgeven en uw toepassing voor voorlegging aan de diverse toepassingsopslag voorbereiden.

![chlimage_1-116](assets/chlimage_1-116.png)

## De `Manage App` tegel {#understanding-the-manage-app-tile}

U kunt in elke tegel in de **`Manage App`** U kunt een tegel toevoegen om details weer te geven of te bewerken door te klikken op &#39;...&#39; in de rechterbenedenhoek.

### Het tabblad Standaard {#the-basic-tab}

U kunt de **Naam**, **Auteur**, **Korte beschrijving** en de **Beschrijving** voor uw app op dit tabblad.

![chlimage_1-117](assets/chlimage_1-117.png)

### Het tabblad Geavanceerd {#the-advanced-tab}

Elk mobiel toepassingsplatform beschrijft welke gegevens worden verzameld, specifiek gericht op elke toepassingsopslag.

De getoonde platforms worden gedreven door de inhoud PhoneGap config.xml:

```xml
<widget>
<gap:platform name="ios"/>
<gap:platform name="android"/>
</widget>
```

Elke winkel van leverancierstoepassingen, bijvoorbeeld Apple App Store of Google Play Store, vereist een of meer schermafbeeldingen van uw mobiele toepassing om uw toepassingsdetails aan klanten te tonen. Deze schermafbeeldingen kunnen strikte vereisten hebben rond afmetingen en inhoud (in feite moeten ze de toepassing echt vertegenwoordigen). AEM toepassingen ondersteunen het selecteren en beheren van deze schermafbeeldingen voor de ondersteunde platforms en het weergeven van de poortafmetingen die vereist zijn voor de toepassingsopslag van elke leverancier.

>[!NOTE]
>
>Met de app AEM verifiëren kunt u schermafbeeldingen rechtstreeks in AEM naar uw toepassingsgegevens sturen.
>
>Zie [Mobile QuickStart voor AEM verifiëren](/help/mobile/phonegap-mobile-quickstart.md) voor meer informatie .

![chlimage_1-118](assets/chlimage_1-118.png)

### Metagegevens {#metadata}

>[!NOTE]
>
>Als u eenmaal vertrouwd bent met de **`Manage App`** tegel, zie [App-metagegevens bewerken](/help/mobile/phonegap-editmetadata.md) om de metagegevens weer te geven en te bewerken.

#### Algemene metagegevens {#common-metadata}

Elke toepassing zou bijbehorende meta-gegevens moeten hebben die in het vormen van verschillende aspecten van de toepassing helpen. De pagina App beheren wordt gescheiden in twee verschillende gebieden die betrekking hebben op de verzameling van metagegevens. Platformspecifieke metagegevens en algemene metagegevens.

Er zijn algemene configuratie en metagegevens voor alle platforms.

In deze sectie definieert u de URL van de Content Update Server, de openingspagina voor uw mobiele toepassing, de PhoneGap-versie voor compilatie, uw toepassingsversie, naam, beschrijving en meer.

**App-versie** is de werkende versie van uw toepassing. De beste manier is om een notatie met drie decimalen te gebruiken en onder 1,0,0 te beginnen voor de eerste release.

**PhoneGap-versie** Dit is de versie waarin u uw toepassing wilt compileren met PhoneGap. De beste manier is om de huidige versie bij te houden zodat u de nieuwste en beste functies en oplossingen voor problemen krijgt.

**URL van server voor bijwerken van inhoud** Dit is de URL die uw toepassing gebruikt om te vragen om ContentSync-updates. Deze moet worden ingesteld op de URL van uw verzender of, als u geen Dispatcher gebruikt, op een van uw publicatie-instanties die wordt gebruikt om ContentSync-updates aan uw toepassing te leveren.

![chlimage_1-119](assets/chlimage_1-119.png)

>[!NOTE]
>
>Deze sectie kan leeg lijken tenzij er gegevens zijn die de gebieden vullen.
>
>Bovenaan in de weergave Details ziet u Toepassingsversie, PhoneGap-versie en URL bijwerken. Elk van deze waarden kan worden ingesteld in de sectie Algemene metagegevens. De toepassings-id kan echter niet worden bewerkt.

#### Metagegevens platform {#platform-metadata}

Elk platform dat in PhoneGap config.xml wordt bepaald kan de eigenschappen van het douaneplatform bevatten. Een AEM ontwikkelaar moet de inhoudsstructuur bijdragen om deze eigenschappen vast te leggen. Een voorbeeld van platformspecifieke eigenschappen vindt u in iOS.

Metagegevens voor alle geconfigureerde platforms worden nu tegelijkertijd weergegeven op het tabblad Geavanceerd van het dialoogvenster `Manage App` tegel.

>[!NOTE]
>
>De gedeelten met platformmetagegevens worden niet gebruikt door PhoneGap tijdens een CLI of build van Remote PhoneGap. AEM probeert in plaats daarvan metagegevens vast te leggen voor platforms, zodat deze later kunnen worden gebruikt wanneer ze worden ingediend bij de toepassingsopslag van de beoogde leverancier.

Voor platforms die niet door AEM worden begrepen, is het nog mogelijk voor een AEM ontwikkelaar om UI uit te breiden om deze meta-gegevens te vangen die later kunnen worden uitgevoerd en tijdens het proces van de toepassingsvoorlegging worden gebruikt.

#### iOS-metagegevens {#ios-metadata}

De Apple AppStore heeft extra metagegevens nodig om uw toepassing voor distributie te verzenden. In de sectie met iOS-metagegevens wordt geprobeerd de vereiste informatie te verzamelen die door het iTMSTransporter-hulpprogramma van Apple kan worden gebruikt om de metagegevens te publiceren naar de bijbehorende Apple-ontwikkelaarsaccount.

Als u de specifieke metagegevens van Apple wilt opvragen, maakt u uw toepassing op [https://itunesconnect.apple.com](https://itunesconnect.apple.com/). Tijdens het maken van uw toepassing genereert Apple metagegevens die vereist zijn in de sectie met iOS-metagegevens als u de Apple iTMSTransporter-tool wilt gebruiken om de metagegevens te valideren en te uploaden naar itunesconnect.apple.com. Als u de te verzamelen metagegevens wilt verkrijgen, hoeft u de specifieke iOS-metagegevens niet in te vullen. U kunt nog steeds de metagegevens exporteren waarin de iOS en de algemene metagegevens worden samengevoegd en alle schermafbeeldingen verzamelen in een ZIP-bestand dat op elk gewenst moment kan worden gedownload.

Het gedownloade zip-bestand bevat een gps-bestand dat kan worden geïnspecteerd op metadata.xml. Het itmsp-bestand bevat de geëxporteerde metagegevens (in het bestand metadata.xml) en alle bijbehorende schermafbeeldingen.

De exportfunctionaliteit wordt gebruikt om een handige manier te bieden om de schermafbeeldingen en metagegevens te verzamelen die kunnen worden doorgegeven aan de uitgever van de toepassing voor invoer in de leverancierspecifieke toepassingsopslag.

![chlimage_1-120](assets/chlimage_1-120.png)

#### Metagegevens Android™ {#android-metadata}

Wanneer u het Android™-platform selecteert, zijn er op dit punt geen aangepaste metagegevens die kunnen worden ingesteld. Wanneer u op de knop Downloaden klikt, wordt een ZIP-bestand gegenereerd met een eigenschappenbestand dat alle metagegevens en de bijbehorende schermafbeeldingen bevat.

De exportfunctionaliteit wordt gebruikt om een handige manier te bieden om de schermafbeeldingen en metagegevens te verzamelen die kunnen worden doorgegeven aan de uitgever van de toepassing voor invoer in de leverancierspecifieke toepassingsopslag.

![chlimage_1-121](assets/chlimage_1-121.png)

### URL van server voor bijwerken van inhoud {#content-update-server-url}

Een van de belangrijkste functies van AEM Apps is de mogelijkheid om een mobiele toepassing nieuwe inhoud te laten aanvragen via ContentSync, waarbij inhoud uit HTML-bronnen, pagina&#39;s, video, afbeeldingen, tekst en meer kan bestaan. Nadat de auteur van de inhoud de inhoud heeft bijgewerkt en deze inhoud vervolgens heeft gepubliceerd, stelt de server de update van de inhoud beschikbaar voor de mobiele toepassing die deze kan downloaden.

Het bezit van de Server URL van de Update van de Inhoud is URL die aan een te publiceren instantie moet richten; of direct of door de Verzender of CDN. De indeling van de URL is eenvoudig:

`https://[hostname]:[port]`

>[!NOTE]
>
>Als de instantie van de auteurserver aan vele instanties van de publicatieserver (gemeenschappelijke architectuur voor AEM) dupliceert, heeft elke publicatieserver de zelfde updateinhoud. De reden hiervoor is dat de update is gebaseerd op de auteur en is gerepliceerd naar alle publicatie-instanties. In principe worden taakverdeling en failover volledig ondersteund.

### Het tabblad Plug-ins {#the-plugins-tab}

De **Plug-ins** bevat een beschrijving van de plug-ins die aan uw app zijn gekoppeld. Deze informatie wordt gebruikt om de aangewezen stop in tijdens een bouwstijl terug te winnen.

![chlimage_1-122](assets/chlimage_1-122.png)

### Het tabblad Schermopnamen {#the-screenshots-tab}

De **Screenshots** worden de ondersteunde schermresoluties op verschillende platforms weergegeven.

![chlimage_1-123](assets/chlimage_1-123.png)

>[!NOTE]
>
>Als u schermafbeeldingen wilt toevoegen en verwijderen, raadpleegt u [App-metagegevens bewerken](/help/mobile/phonegap-editmetadata.md).

### Het tabblad Verificatie {#the-authentication-tab}

De **Verificatie** kunt u een OAuth-client selecteren die u aan uw toepassing wilt koppelen en een ontwikkelaar in staat stellen Adobe Experience Manager OAuth-verificatie te gebruiken.

![chlimage_1-124](assets/chlimage_1-124.png)

### De volgende stappen {#the-next-steps}

Zodra u over het Leiden van de Toepassing in het toepassingsdashboard hebt geleerd, zie de volgende middelen voor andere auteursrollen:

* [App-metagegevens bewerken](/help/mobile/phonegap-editmetadata.md)
* [Toepassingsdefinities](/help/mobile/phonegap-app-definitions.md)
* [Een nieuwe app maken met de wizard App maken](/help/mobile/phonegap-create-new-app.md)
* [Een bestaande hybride app importeren](/help/mobile/phonegap-adding-content-to-imported-app.md)
* [Inhoudsservices](/help/mobile/develop-content-as-a-service.md)

### Overige bronnen {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwikkelen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/developing-in-phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)
