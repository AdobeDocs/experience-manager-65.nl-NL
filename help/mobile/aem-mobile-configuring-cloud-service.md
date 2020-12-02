---
title: Adobe Target-Cloud Service configureren
seo-title: Adobe Target-Cloud Service configureren
description: Volg deze pagina om te begrijpen hoe u de juiste set machtigingen voor gebruikers en groepen kunt verkrijgen, cloudservices kunt maken, de toepassing voor de activiteit kunt configureren en ten slotte de inhoud kunt genereren.
seo-description: Volg deze pagina om te begrijpen hoe u de juiste set machtigingen voor gebruikers en groepen kunt verkrijgen, cloudservices kunt maken, de toepassing voor de activiteit kunt configureren en ten slotte de inhoud kunt genereren.
uuid: 569f9c6d-f521-488a-9e51-f43b7a214dd9
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
discoiquuid: 8cd6480f-cb4f-40dd-a444-8ba463b78604
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1333'
ht-degree: 0%

---


# Adobe Target-Cloud Service {#configuring-adobe-target-cloud-service} configureren

>[!NOTE]
>
>Adobe raadt aan de SPA Editor te gebruiken voor projecten die renderen op basis van één pagina voor toepassingsframework op de client-side vereisen (bijvoorbeeld Reageren). [Meer](/help/sites-developing/spa-overview.md) informatie.

>[!NOTE]
>
>Dit document maakt deel uit van de [Aan de slag met AEM Mobile](/help/mobile/getting-started-aem-mobile.md) Guide, een aanbevolen startpunt voor AEM Mobile-referentie.

Er zijn een aantal stappen die moeten worden samengevoegd voordat auteurs van inhoud gerichte inhoud kunnen gaan genereren voor mobiele apps: Er is de juiste set machtigingen voor gebruikers en groepen, het maken van cloudservices, het configureren van de toepassing voor de activiteit en het genereren van de inhoud.

De aanname is dat de [AEM Mobile Hybride Referentie-toepassing](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) met succes is geïmplementeerd en toegankelijk is via het AEM Mobile-dashboard.

## Machtigingen {#permissions}

Gebruikers die toegang tot de verpersoonlijkingsconsole nodig hebben, moeten deel uitmaken van de `target-activity-authors`-groep. Voorgesteld wordt dat als onderdeel van de gebruikersinstellingen en groepsinstellingen de doelgroep-activiteit-groep moet worden toegevoegd aan de groep met apps-beheerders. Door de doel-activiteit-auteursgroep toe te voegen zal dit gebruikers capaciteit toestaan om de ingang van het menu van de Navigatie van de Aanpassing te zien.

Het vergeten om de gebruikers of de groepen toe te voegen die u toegang tot de verpersoonlijkings admin console aan de doel-activiteit-auteur groep wilt hebben zal gebruikers verhinderen de verpersoonlijkingsconsole te zien.

## Cloud Services {#cloud-services}

Om gerichte inhoud te krijgen die voor mobiele toepassingen werkt zijn er twee diensten die moeten worden gevormd: De Adobe Target Service en de Adobe Mobile Services-service. De Adobe Target Service biedt de engine voor het verwerken van clientverzoeken en het retourneren van gepersonaliseerde inhoud. De service Adobe Mobile Services biedt de verbinding tussen de Adobe-services en de mobiele toepassing via het bestand ADBMobileConfig.json dat door de AMS Cordova-plug-in wordt gebruikt. Via het AEM Mobile-dashboard kunt u uw toepassing configureren door de twee services toe te voegen.

## Adobe Target Cloud Service {#adobe-target-cloud-service}

Zoek op het AEM Mobile-dashboard de Cloud Services Beheren en klik op +.

![chlimage_1-8](assets/chlimage_1-8.png)

Selecteer de &quot;Adobe Target&quot;-cloudservicekaart van de wizard Cloud Service toevoegen en klik op Volgende.

![chlimage_1-9](assets/chlimage_1-9.png)

Van Uitgezocht een drop-down van de Configuratie kunt u of een nieuwe configuratie tot stand brengen of van bestaande selecteren. Om een nieuwe configuratie tot stand te brengen selecteer &quot;tot Configuratie&quot;van dropdown. Ga een titel voor de configuratie van het Doel in. Voer uw clientcode, e-mail en wachtwoord in die aan uw doelaccount zijn gekoppeld. Als u de waarden voor deze velden niet weet, neemt u contact op met de Adobe Target-ondersteuning. Klik op de knop &quot;Verifiëren&quot; om de referenties te valideren. Zodra geverifieerd, klik de Submit knoop om de wolkendienst tot stand te brengen.

De cloudservice die wordt gemaakt, wordt automatisch gekoppeld aan de mobiele toepassing via de wizard. De eigenschapswaarde cq:cloudserviceconfigs wordt ingesteld op het knooppunt jcr:content van het knooppunt van de groep apps. Voor het hybride app-voorbeeld wordt het ingesteld op /content/mobileapps/hybride-reference-app/jcr:content met de waarde die verwijst naar het automatisch gegenereerde frameworkknooppunt op /etc/cloudservices/testandtarget/adobe-aem-apps/framework. Het knooppunt framework heeft twee eigenschappen die standaard zijn ingesteld: geslacht en leeftijd. Het framework wordt alleen gebruikt door AEM voorvertoning en heeft geen invloed op het apparaat.

Na voltooiing van de tovenaar zal de Manage Cloud Service tegel de de wolkendienst van het Doel bevatten, nochtans bevat het een waarschuwing over een ontbrekende rekening van de Dienst van Adobe Mobile.

![chlimage_1-10](assets/chlimage_1-10.png)

## Adobe Mobile-service {#adobe-mobile-service}

Het is noodzakelijk om een Adobe Mobile Services (AMS)-account ook aan de toepassing te koppelen, biedt de AMS-service het vereiste ADBMobileConfig.json-bestand dat de informatie over de doelclientcode bevat. Voordat u een koppeling met de AMS-account maakt, moet de AMS-account worden gewijzigd door een gebruiker die machtigingen voor AMS heeft.

### Clientcode {#client-code}

Als u zich wilt aanmelden bij de AMS-services, gaat u naar [https://mobilemarketing.adobe.com](https://mobilemarketing.adobe.com/), selecteert u de mobiele toepassing en klikt u op de instellingen. Zoek het veld SDK-doelopties en plaats de clientcode in het veld en klik op Opslaan.

![chlimage_1-11](assets/chlimage_1-11.png)

Nu de clientcode aan de mobiele toepassing is gekoppeld, worden de instellingen voor de service-instellingen via het bestand ADBMobileConfig.json geleverd wanneer de AMS-cloudservice via het dashboard Adobe Mobile is geconfigureerd.

### Adobe Mobile-service kan {#adobe-mobile-service-could-service}

Nu AMS is geconfigureerd, is het tijd om de mobiele toepassing te koppelen aan het dashboard voor mobiele Adobe. Zoek op het AEM Mobile-dashboard de Cloud Services Beheren en klik op +.

![chlimage_1-12](assets/chlimage_1-12.png)

Selecteer de Adobe Mobile Services-kaart en klik op Volgende.

![chlimage_1-13](assets/chlimage_1-13.png)

Selecteer in de stap Maken of Selecteren van de wizard het vervolgkeuzemenu Mobiele service en selecteer de vermelding Configuratie maken. Geef een titel, bedrijf, gebruikersnaam en wachtwoord op en selecteer het juiste datacenter. Als u deze waarden niet kent, neemt u contact op met de beheerder van de Adobe Mobile-service om deze te verkrijgen. Klik op de knop Verifiëren als alle velden zijn ingevuld. Het verificatieproces gaat naar AMS en verifieert de referenties voor de account. Na een geslaagde validatie wordt een lijst met mobiele toepassingen gevuld. Hierin selecteert u de bijbehorende mobiele toepassing in het vervolgkeuzemenu. Klik op de knop Verzenden om de wizard te voltooien. Het proces kan enige tijd duren om de configuratiegegevens en eventuele bijbehorende analyses voor de toepassing te verkrijgen. Als het proces is voltooid, klikt u op de knop Gereed van het modaal om terug te keren naar het mobiele dashboard van Adobe.

Als u terugkeert naar het mobiele dashboard, bevat de titel Cloud Services beheren de AMS-cloudservice. U zult ook opmerken dat de Analyze de tegel van Metriek met levenscyclusrapporten zal worden bevolkt.

![chlimage_1-14](assets/chlimage_1-14.png)

## Handlers voor synchronisatie van doelinhoud {#target-content-sync-handlers}

Om inhoud aan de het apparateninhoud van de gebruiker te leveren wordt geproduceerd door de aanbiedingen terug te geven die door AEM inhoudsauteurs worden gecreeerd. Voor het afhandelen van de rendering van doelaanbiedingen is er een nieuwe handler voor inhoudssynchronisatie die de aanbiedingen verwerkt. Gebruikend de Hybride Toepassing van de Verwijzing als onze steekproef, bevat het en (Engelse) inhoudspakket ContentSyncConfig met een [mobileappoffers](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/aem-package/content-author/src/main/content/jcr_root/content/mobileapps/hybrid-reference-app/en/_jcr_content/pge-app/app-config-dev/targetOffers/.content.xml) manager. De volgende stap is van cruciaal belang voor het renderen van aanbiedingen voor het apparaat. De handler mobileappoffers heeft een padeigenschap die het pad naar de personalisatieactiviteit aangeeft die voor de toepassing moet worden gebruikt.

Als er bijvoorbeeld een activiteit is die zich op */content/campagnes/hybridref* bevindt, kopieert u dit pad en plakt u het als de waarde naar de eigenschap *path* van de handler mobileappoffers.

Voor de Hybride Toepassing van de Verwijzing zijn er twee mobileappoffers managers één voor dev en één voor producties.

Zodra de activiteitenweg in het de wegbezit van de mobileappoffers manager is geplaatst sparen de manager. De handler is nu gereed om de renderingaanbiedingen voor onze mobiele apparaten te starten.

### Rendermodus {#render-mode}

De handler mobileappoffers is anders geconfigureerd voor publicatie- en ontwikkelinstellingen. Voor publicatie-instellingen is er een eigenschap met de naam *renderMode*, met de waarde *publish* ingesteld op het knooppunt cq:ContentSyncConfig. De handler mobileappoffers verwijst naar de renderMode en zal, indien ingesteld op publiceren, de id van het mbox wijzigen die wordt gemaakt. Standaard wordt in vakken die AEM maakt, een waarde —auteur toegevoegd aan de id van het mbox. Hieruit blijkt dat de activiteit niet is gepubliceerd en de niet-gepubliceerde campagne voor het indienen van voorstellen moet gebruiken.

Wanneer inhoud wordt gefaseerd via het mobiele dashboard van Adobe, wordt gefaseerde inhoud beschouwd als inhoud die klaar is voor productie en wordt deze weergegeven via de niet-dev Content Sync Config. Als u deze manier weergeeft, wordt de auteur —verwijderd van alle id&#39;s van het selectievakje en wordt verwacht dat een gepubliceerde activiteit beschikbaar is op de doelserver. Controleer voordat u inhoud met werkgebied test of de activiteit is gepubliceerd.

## Inhoud {#creating-content} maken

Nu de cloudservices zijn gemaakt en de handler mobileappoffers is geconfigureerd, kunnen auteurs van inhoud nu gerichte ervaringen genereren.
