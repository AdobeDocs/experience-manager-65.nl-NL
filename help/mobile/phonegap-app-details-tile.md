---
title: App-tegel beheren
seo-title: App-tegel beheren
description: Volg deze pagina om meer te weten te komen over de Manage App Tile op het app dashboard die de mogelijkheid biedt om details over de toepassing te wijzigen.
seo-description: Volg deze pagina om meer te weten te komen over de Manage App Tile op het app dashboard die de mogelijkheid biedt om details over de toepassing te wijzigen.
uuid: bde75ecd-8694-427c-9b16-2c4ab2fd4d8b
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: authoring-adobe-phonegap-enterprise
discoiquuid: a87834c9-247c-49fa-9978-a969230db91c
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1290'
ht-degree: 0%

---


# App-tegel beheren{#manage-app-tile}

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

Met de **App**-tegel beheren op het dashboard van de app kunt u details over de toepassing wijzigen. Als u de pagina Details wilt openen, klikt u op de detailkoppeling van de app Beheren. Vanuit de beheerpagina kunt u de configuratie-instellingen (config.xml) van de PhoneGap-toepassing bewerken en uw toepassing voorbereiden voor verzending naar de verschillende opslagruimten van toepassingen.

![chlimage_1-116](assets/chlimage_1-116.png)

## De toepassingstegel beheren {#understanding-the-manage-app-tile}

U kunt in elke tegel in **App** beheren tegel boren om details te bekijken of uit te geven door te klikken &#39;..&#39; in de rechterbenedenhoek.

### Het tabblad Standaard {#the-basic-tab}

U kunt **Naam**, **Auteur**, **Korte beschrijving**, en **Beschrijving** voor uw app van dit lusje uitgeven.

![chlimage_1-117](assets/chlimage_1-117.png)

### Het tabblad Geavanceerd {#the-advanced-tab}

Elk mobiel toepassingsplatform beschrijft welke gegevens worden verzameld, specifiek gericht op elke toepassingsopslag.

Weergegeven Platforms worden aangestuurd door de inhoud PhoneGap config.xml:

```xml
<widget>
<gap:platform name="ios"/>
<gap:platform name="android"/>
</widget>
```

Elke winkel voor toepassingen van leveranciers, zoals de Apple App Store of Google Play Store, heeft bijvoorbeeld een of meer schermafbeeldingen van uw mobiele toepassing nodig om uw toepassingsgegevens aan klanten weer te geven. Deze schermafbeeldingen kunnen strikte vereisten hebben rond afmetingen en inhoud (in feite moeten ze de toepassing echt vertegenwoordigen). AEM Apps biedt ondersteuning voor het selecteren en beheren van deze schermafbeeldingen voor de ondersteunde platforms en het bekijken van poortafmetingen, zoals vereist door de toepassingsopslag van elke leverancier.

>[!NOTE]
>
>De app AEM verifiëren biedt de mogelijkheid om schermafbeeldingen rechtstreeks naar uw toepassingsgegevens in AEM te verzenden.
>
>Zie [Mobiele QuickStart voor AEM Verifiëren](/help/mobile/phonegap-mobile-quickstart.md) voor meer informatie.

![chlimage_1-118](assets/chlimage_1-118.png)

### Metagegevens {#metadata}

>[!NOTE]
>
>Als u bekend bent met de **App**-tegel beheren, raadpleegt u [App-metagegevens bewerken](/help/mobile/phonegap-editmetadata.md) om de metagegevens weer te geven en te bewerken.

#### Algemene metagegevens {#common-metadata}

Elke toepassing zou bijbehorende meta-gegevens moeten hebben die in het vormen van verschillende aspecten van de toepassing helpen. De pagina App beheren wordt gescheiden in twee verschillende gebieden die betrekking hebben op de verzameling van metagegevens. Specifieke metagegevens en algemene metagegevens Platforms.

Er zijn algemene configuratie en metagegevens voor alle platforms.

In deze sectie definieert u de URL van de Content Update Server, de openingspagina voor uw mobiele toepassing, de PhoneGap-versie voor compilatie, uw toepassingsversie, naam, beschrijving en meer.

**App** Version is de werkversie van uw toepassing. De gebruikelijke werkwijze is om een notatie met drie decimalen te gebruiken en lager dan 1,0,0 te beginnen vóór de eerste release.

**PhoneGap** Version is de versie waarin u uw toepassing wilt compileren met PhoneGap. De beste manier is om de huidige versie bij te houden zodat u de nieuwste en beste functies en oplossingen voor problemen krijgt.

**De** URL van de Content Update Server is de URL die uw toepassing gebruikt om te bellen naar ContentSync-updates. Deze moet worden ingesteld op de URL van uw verzender of, als u geen verzender gebruikt, op een van uw publicatie-instanties die worden gebruikt om ContentSync-updates aan uw toepassing te leveren.

![chlimage_1-119](assets/chlimage_1-119.png)

>[!NOTE]
>
>Deze sectie kan leeg lijken tenzij er gegevens zijn die de gebieden vullen.
>
>Bovenaan in de weergave Details ziet u de toepassingsversie, PhoneGap-versie en URL bijwerken. Elk van deze waarden kan worden ingesteld in de sectie Algemene metagegevens. De toepassings-id kan echter niet worden bewerkt.

#### Metagegevens Platform {#platform-metadata}

Elk platform dat in PhoneGap config.xml wordt bepaald kan de eigenschappen van het douaneplatform bevatten. Een AEM ontwikkelaar moet de inhoudsstructuur bijdragen om deze eigenschappen vast te leggen. Een voorbeeld van platformspecifieke eigenschappen vindt u bij iOS.

Metagegevens voor alle geconfigureerde platforms worden nu tegelijkertijd weergegeven op het tabblad Geavanceerd van de tegel App beheren.

>[!NOTE]
>
>De gedeelten met platformmetagegevens worden niet gebruikt door PhoneGap tijdens een CLI- of Remote PhoneGap-build, maar AEM pogingen om metagegevens voor platforms vast te leggen, zodat deze later kunnen worden gebruikt wanneer ze worden verzonden naar de toepassingsopslag van de beoogde leverancier.

Voor platforms die niet door AEM worden begrepen, is het nog mogelijk voor een AEM ontwikkelaar om UI uit te breiden om deze meta-gegevens te vangen die later kunnen worden uitgevoerd en tijdens het proces van de toepassingsvoorlegging worden gebruikt.

#### iOS-metagegevens {#ios-metadata}

De Apple AppStore heeft aanvullende metagegevens nodig om uw toepassing voor distributie te kunnen verzenden. De sectie met iOS-metagegevens probeert de vereiste informatie te verzamelen die door het iTMSTransporter-hulpprogramma van Apple kan worden gebruikt om de metagegevens te publiceren naar het bijbehorende account voor Apple-ontwikkelaars.

Als u de specifieke Apple-metagegevens wilt verkrijgen, moet u eerst uw toepassing maken op [https://itunesconnect.apple.com](https://itunesconnect.apple.com/). Apple genereert bij het maken van uw toepassing metagegevens die vereist zijn in de sectie iOS-metagegevens als u de Apple iTMSTransporter-tool wilt gebruiken om de metagegevens te valideren en te uploaden naar itunesconnect.apple.com. Als u alleen de metagegevens wilt verzamelen, hoeft u niet noodzakelijkerwijs de specifieke iOS-metagegevens in te vullen. U kunt nog steeds de metagegevens exporteren die de iOS en algemene metagegevens samenvoegen en alle schermafbeeldingen verzamelen in een ZIP-bestand dat op elk gewenst moment kan worden gedownload.

Het gedownloade zip-bestand bevat een gps-bestand dat kan worden gecontroleerd op metadata.xml. Het itmsp-bestand bevat de geëxporteerde metagegevens (in het bestand metadata.xml) en alle bijbehorende schermafbeeldingen.

De exportfunctionaliteit wordt gebruikt om een handige manier te bieden om de schermafbeeldingen en metagegevens te verzamelen die kunnen worden doorgegeven aan de uitgever van de toepassing voor invoer in de specifieke toepassingsopslag van de leverancier.

![chlimage_1-120](assets/chlimage_1-120.png)

#### Android-metagegevens {#android-metadata}

Wanneer u het Android-platform selecteert, zijn er op dit punt geen aangepaste metagegevens die kunnen worden ingesteld. Wanneer u als ZIP-bestand op de downloadknop klikt, wordt een eigenschappenbestand gegenereerd dat alle metagegevens en de bijbehorende schermafbeeldingen bevat.

De exportfunctionaliteit wordt gebruikt om een handige manier te bieden om de schermafbeeldingen en metagegevens te verzamelen die kunnen worden doorgegeven aan de uitgever van de toepassing voor invoer in de specifieke toepassingsopslag van de leverancier.

![chlimage_1-121](assets/chlimage_1-121.png)

### Server-URL voor bijwerken van inhoud {#content-update-server-url}

Een van de belangrijkste functies van AEM Apps is de mogelijkheid om een mobiele toepassing nieuwe inhoud te laten aanvragen via ContentSync, waar inhoud kan bestaan uit HTML-bronnen, pagina&#39;s, video, afbeeldingen, tekst en meer. Nadat de inhoud door de auteur is bijgewerkt en vervolgens is gepubliceerd, stelt de server de update van de inhoud beschikbaar zodat de mobiele toepassing deze kan downloaden.

Het bezit van de Server URL van de Update van de Inhoud is URL die aan een te publiceren instantie moet richten; rechtstreeks of via de verzender of CDN. De indeling van de URL is eenvoudig:

`https://[hostname]:[port]`

>[!NOTE]
>
>Als de instantie van de auteurserver aan veelvoudige publicatie serverinstanties (gemeenschappelijke architectuur voor AEM) dupliceert, zal elke publicatieserver de zelfde updateinhoud hebben omdat de update op de auteur wordt voortgebouwd en aan alle publicatieinstanties wordt herhaald. In principe worden taakverdeling en failover volledig ondersteund.

### Het tabblad Plug-ins {#the-plugins-tab}

Op het tabblad **Plugins** worden de plug-ins beschreven die aan uw app zijn gekoppeld. Deze informatie wordt gebruikt om de juiste insteekmodule op te halen tijdens een build.

![chlimage_1-122](assets/chlimage_1-122.png)

### Het tabblad Schermafbeeldingen {#the-screenshots-tab}

Op het tabblad **Screenshots** worden de ondersteunde schermresoluties weergegeven op verschillende platforms.

![chlimage_1-123](assets/chlimage_1-123.png)

>[!NOTE]
>
>Zie [App-metagegevens bewerken](/help/mobile/phonegap-editmetadata.md) om schermafbeeldingen toe te voegen en te verwijderen.

### Het tabblad Verificatie {#the-authentication-tab}

Met het tabblad **Verificatie** kunt u een OAuth-client selecteren die aan uw toepassing moet worden gekoppeld en kan een ontwikkelaar Adobe Experience Manager OAuth-verificatie gebruiken.

![chlimage_1-124](assets/chlimage_1-124.png)

### De volgende stappen {#the-next-steps}

Nadat u kennis hebt genomen van het beheren van App Tile in het toepassingsdashboard, raadpleegt u de volgende bronnen voor andere ontwerprollen:

* [App-metagegevens bewerken](/help/mobile/phonegap-editmetadata.md)
* [Toepassingsdefinities](/help/mobile/phonegap-app-definitions.md)
* [Een nieuwe app maken met de wizard App maken](/help/mobile/phonegap-create-new-app.md)
* [Een bestaande hybride app importeren](/help/mobile/phonegap-adding-content-to-imported-app.md)
* [Inhoudsservices](/help/mobile/develop-content-as-a-service.md)

### Aanvullende bronnen {#additional-resources}

Meer informatie over de rollen en verantwoordelijkheden van een Beheerder en Ontwikkelaar vindt u in de volgende bronnen:

* [Ontwikkelen voor Adobe PhoneGap Enterprise met AEM](/help/mobile/developing-in-phonegap.md)
* [Inhoud voor Adobe PhoneGap Enterprise beheren met AEM](/help/mobile/administer-phonegap.md)

