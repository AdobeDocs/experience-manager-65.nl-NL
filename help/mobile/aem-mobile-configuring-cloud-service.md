---
title: Adobe Target-Cloud Service configureren
description: Volg deze pagina om te begrijpen hoe u de juiste set machtigingen voor gebruikers en groepen kunt verkrijgen, cloudservices kunt maken, de toepassing voor de activiteit kunt configureren en ten slotte de inhoud kunt genereren.
contentOwner: User
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MOBILE
topic-tags: developing-adobe-phonegap-enterprise
exl-id: d370d772-ef4d-4f38-826c-e90d07735822
solution: Experience Manager
feature: Mobile
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1254'
ht-degree: 0%

---

# Adobe Target-Cloud Service configureren {#configuring-adobe-target-cloud-service}

>[!NOTE]
>
>De Adobe adviseert het gebruiken van de SPARedacteur voor projecten die op kader-gebaseerde cliënt-zijteruggeven van enige paginatoepassing (bijvoorbeeld, Reageren) vereisen. [ leer meer ](/help/sites-developing/spa-overview.md).

>[!NOTE]
>
>Dit document maakt deel uit van [ Begonnen het Worden met Mobiele (AEM) Gids van Adobe Experience Manager ](/help/mobile/getting-started-aem-mobile.md), een geadviseerd uitgangspunt voor de verwijzing van AEM Mobile.

Er zijn verschillende stappen die moeten worden samengevoegd voordat inhoudsauteurs gerichte inhoud kunnen gaan genereren voor mobiele apps: gebruikers en groepen krijgen de juiste machtigingen, maken cloudservices, configureren de toepassing voor de activiteit en genereren ten slotte de inhoud.

De veronderstelling die vooruit gaat is dat de [ Hybride Toepassing van de Verwijzing van AEM Mobile ](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference) met succes is opgesteld en toegankelijk door middel van het dashboard van AEM Mobile.

## Machtigingen {#permissions}

Gebruikers die toegang tot de aanpassingsconsole nodig hebben, moeten deel uitmaken van de `target-activity-authors` -groep. Voorgesteld wordt dat als onderdeel van de gebruikersinstellingen en groepsinstellingen de doelgroep-activiteit-groep moet worden toegevoegd aan de groep met apps-beheerders. Door de doelgroep-activiteit-auteurs toe te voegen, staat dit gebruikers de capaciteit toe om de ingang van het de navigatiemenu van Personalization te zien.

Het vergeten om de gebruikers of de groepen toe te voegen die u toegang tot de verpersoonlijking Admin Console aan de doel-activiteit-auteursgroep wilt hebben verhindert gebruikers de verpersoonlijkingsconsole te zien.

## Cloud Servicen {#cloud-services}

Om gerichte inhoud te krijgen die voor mobiele toepassingen werkt, zijn er twee diensten die moeten worden gevormd: de Dienst van Adobe Target en de dienst van de Diensten van de Adobe Mobiele. De Adobe Target Service biedt de engine voor het verwerken van clientverzoeken en het retourneren van gepersonaliseerde inhoud. De service Adobe Mobile Services biedt de verbinding tussen de Adobe-services en de mobiele toepassing via het bestand ADBMobileConfig.json dat wordt gebruikt door de insteekmodule AMS Cordova. Vanuit het AEM Mobile-dashboard kunt u de toepassing configureren door de twee services toe te voegen.

## Adobe Target Cloud Service {#adobe-target-cloud-service}

Zoek in het AEM Mobile-dashboard de Cloud Servicen voor beheren op en klik op +.

![ chlimage_1-8 ](assets/chlimage_1-8.png)

Selecteer de &quot;Adobe Target&quot;-cloudservicekaart van de wizard Cloud Service toevoegen en klik op Volgende.

![ chlimage_1-9 ](assets/chlimage_1-9.png)

Van Uitgezocht een drop-down Configuratie, kunt u of een configuratie tot stand brengen of van bestaande selecteren. Als u een configuratie wilt maken, selecteert u &quot;Configuratie maken&quot; in het vervolgkeuzemenu. Voer een titel in voor de doelconfiguratie. Voer uw clientcode, e-mail en wachtwoord in die aan uw Target-account zijn gekoppeld. Als u de waarden voor deze velden niet kent, neemt u contact op met de ondersteuning van Adobe Target. Klik op de knop &quot;Verifiëren&quot; om de referenties te valideren. Zodra geverifieerd, klik de Submit knoop om de wolkendienst tot stand te brengen.

De cloudservice die wordt gemaakt, wordt automatisch gekoppeld aan de mobiele toepassing via de wizard. De eigenschapswaarde cq:cloudserviceconfigs wordt ingesteld op het knooppunt jcr:content van het knooppunt van de groep apps. Voor het hybride app-voorbeeld wordt het ingesteld op /content/mobileapps/hybride-reference-app/jcr:content met de waarde die naar het automatisch gegenereerde frameworkknooppunt verwijst, bevindt het zich op /etc/cloudservices/testandtarget/adobe-aem-apps/framework. Het knooppunt framework heeft twee eigenschappen die standaard zijn ingesteld: geslacht en leeftijd. Het framework wordt alleen gebruikt door AEM voorvertoning en heeft geen invloed op het apparaat.

Nadat de wizard is voltooid, bevat de tegel Cloud Service beheren de doelcloudservice, maar bevat deze een waarschuwing over een ontbrekende account voor de mobiele service van de Adobe.

![ chlimage_1-10 ](assets/chlimage_1-10.png)

## Adobe mobiele service {#adobe-mobile-service}

Het is noodzakelijk om een rekening van de Diensten van de Adobe Mobiele (AMS) aan de toepassing ook te verbinden, verstrekt de dienst AMS het vereiste dossier ADBMobileConfig.json dat de informatie van de de cliëntcode van het Doel bevat. Voordat u een koppeling met de AMS-account maakt, moet de AMS-account worden gewijzigd door een gebruiker die machtigingen voor AMS heeft.

### Clientcode {#client-code}

Om aan login aan de diensten van AMS bezoek [ https://mobilemarketing.adobe.com ](https://mobilemarketing.adobe.com/), selecteer de mobiele toepassing, en klik de montages. Zoek het veld SDK-doelopties en plaats de clientcode in het veld en klik op Opslaan.

![ chlimage_1-11 ](assets/chlimage_1-11.png)

Nu de clientcode aan de mobiele toepassing is gekoppeld, worden de instellingen voor de service-instellingen via het bestand ADBMobileConfig.json geleverd wanneer de AMS-cloudservice via het mobiele dashboard van de Adobe wordt geconfigureerd.

### Adobe mobiele service kan service {#adobe-mobile-service-could-service}

Nu AMS is geconfigureerd, is het tijd om de mobiele toepassing te koppelen in het mobiele dashboard van de Adobe. Zoek in het AEM Mobile-dashboard de Cloud Servicen voor beheren op en klik op +.

![ chlimage_1-12 ](assets/chlimage_1-12.png)

Selecteer de Adobe Mobile Services-kaart en klik op Volgende.

![ chlimage_1-13 ](assets/chlimage_1-13.png)

Van de Create of Uitgezochte tovenaar stap, selecteer de Mobiele drop-down Dienst, en selecteer de Create ingang van de Configuratie. Geef een titel, bedrijf, gebruikersnaam en wachtwoord op en selecteer het juiste datacenter. Als u deze waarden niet kent, contacteer uw beheerder van de Dienst van de Adobe Mobiele om hen te verkrijgen. Nadat alle gebieden worden gevuld, klik **verifieer**. Het verificatieproces gaat naar AMS en verifieert de referenties voor de account. Na een geslaagde validatie wordt een lijst met mobiele toepassingen gevuld. Hierin selecteert u de bijbehorende mobiele toepassing in het vervolgkeuzemenu. Klik op de knop Verzenden om de wizard te voltooien. Het proces kan enige tijd duren om de configuratiegegevens en eventuele bijbehorende analyses voor de toepassing te verkrijgen. Nadat het proces volledig is, klik **Gedaan** van modaal om terug naar het Mobiele Dashboard van de Adobe terug te keren.

Als u terugkeert naar het mobiele dashboard, bevat de titel Cloud Servicen beheren de AMS-cloudservice. Bovendien wordt de tegel Metriek analyseren gevuld met levenscyclusrapporten.

![ chlimage_1-14 ](assets/chlimage_1-14.png)

## Handlers voor het synchroniseren van doelinhoud {#target-content-sync-handlers}

Om inhoud aan het apparaat van de gebruiker te leveren, wordt de inhoud geproduceerd door de aanbiedingen terug te geven die door AEM inhoudsauteurs worden gecreeerd. Voor het afhandelen van de rendering van doelaanbiedingen is er een nieuwe handler voor inhoudssynchronisatie die de aanbiedingen verwerkt. Gebruikend de Hybride Toepassing van de Verwijzing als steekproef, bevat het en (Engelse) inhoudspakket ContentSyncConfig met a [ mobileappoffers ](https://github.com/Adobe-Marketing-Cloud-Apps/aem-mobile-hybrid-reference/blob/master/aem-package/content-author/src/main/content/jcr_root/content/mobileapps/hybrid-reference-app/en/_jcr_content/pge-app/app-config-dev/targetOffers/.content.xml) manager. De volgende stap is van cruciaal belang voor het renderen van aanbiedingen voor het apparaat. De handler mobileappoffers heeft een padeigenschap die het pad naar de personalisatieactiviteit identificeert die voor de toepassing wordt gebruikt.

Bijvoorbeeld, als er een activiteit bij *is/content/campagnes/hybridref*, kopieer deze weg en kleef het als waarde aan het *weg* bezit van de mobileappoffers manager.

Voor de Hybride Toepassing van de Verwijzing, zijn er twee mobileappoffers managers één voor dev en één voor producties.

Nadat het activiteitenpad is ingesteld in de padeigenschap van de handler mobileappoffers, slaat u de handler op. De handler is nu gereed om de renderingaanbiedingen voor mobiele apparaten te starten.

### Rendermodus {#render-mode}

De handler mobileappoffers is anders geconfigureerd voor publicatie- en ontwikkelinstellingen. Voor publiceer montages is er een bezit genoemd *renderMode* met een waarde van *publiceert* geplaatst op cq:ContentSyncConfig knoop. De handler mobileappoffers verwijst naar de renderMode en bewerkt de mbox-id die wordt gemaakt, als deze is ingesteld op publiceren. Standaard wordt in vakken die AEM maakt, een waarde —auteur toegevoegd aan de id van het mbox. Hieruit blijkt dat de activiteit niet is gepubliceerd en de niet-gepubliceerde campagne voor het indienen van voorstellen moet gebruiken.

Wanneer inhoud wordt gefaseerd via het mobiele dashboard van de Adobe, wordt gefaseerde inhoud beschouwd als inhoud die klaar is voor productie en wordt deze weergegeven via de niet-dev Content Sync Config. Op deze manier wordt de auteur —verwijderd van alle id&#39;s van het selectievakje en wordt verwacht dat een gepubliceerde activiteit beschikbaar is op de doelserver. Controleer voordat u inhoud met werkgebied test of de activiteit is gepubliceerd.

## Inhoud maken {#creating-content}

Nu de cloudservices zijn gemaakt en de handler mobileappoffers is geconfigureerd, kunnen auteurs van inhoud nu gerichte ervaringen genereren.
