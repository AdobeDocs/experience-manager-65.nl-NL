---
title: Sociale aanmelding met Facebook en Twitter
seo-title: Sociale aanmelding met Facebook en Twitter
description: Met aanmelden via sociale media kunnen bezoekers zich aanmelden met hun Facebook- of Twitter-account.
seo-description: Met aanmelden via sociale media kunnen bezoekers zich aanmelden met hun Facebook- of Twitter-account.
uuid: f70e346e-0d8c-41a0-a100-206a420088dc
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: c0a71870-8f95-40c8-9ffd-b7af49723288
translation-type: tm+mt
source-git-commit: ce64b148ba96cc64670aaf96c1b201bafa282b98
workflow-type: tm+mt
source-wordcount: '2650'
ht-degree: 0%

---


# Sociale aanmelding bij Facebook en Twitter {#social-login-with-facebook-and-twitter}

Met aanmelden via een sociaal netwerk kunt u een bezoeker van een site de optie geven om zich aan te melden bij zijn Facebook- of Twitter-account. Daarom moeten de toegestane Facebook- of Twitter-gegevens worden opgenomen in het profiel voor AEM leden.

![socialloginweretail](assets/socialloginweretail.png)

## Overzicht van sociale aanmelding {#social-login-overview}

Als u sociale aanmelding wilt opnemen, is *vereist* om aangepaste Facebook- en Twitter-toepassingen te maken.

Hoewel het voorbeeld van de webwinkel voorbeelden biedt voor Facebook- en Twitter-apps en cloudservices, zijn deze niet beschikbaar op een [productiewebsite](../../help/sites-administering/production-ready.md).

De vereiste stappen zijn:

1. [Schakel OAuth-](#adobe-granite-oauth-authentication-handler) verificatie in voor alle AEM-publicatie-instanties.

   Als OAuth niet is ingeschakeld, mislukt het aanmelden.

1. **Creëer** sociale app en cloudservice.

   * U kunt als volgt aanmelding bij Facebook ondersteunen:

      * Maak een [Facebook-app](#create-a-facebook-app).
      * Maak en publiceer een [Facebook Connect-cloudservice](#create-a-facebook-connect-cloud-service).
   * Aanmelden met Twitter ondersteunen:

      * Maak een [Twitter-app](#create-a-twitter-app).
      * Maak en publiceer een [Twitter Connect-cloudservice](#create-a-twitter-connect-cloud-service).


1. [**** Hiermee kunt u sociaal ](#enable-social-login) aanmelden voor een gemeenschapssite.

Er zijn twee basisbeginselen:

1. **Scope**  (toestemmingen) specificeert de gegevens de app wordt toegestaan om te verzoeken.

   * De instanties Facebook en Twitter [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) bevatten standaard de basismachtigingen voor de app binnen hun bereik.

1. **Velden**  (params) geven de eigenlijke aangevraagde gegevens op met URL-parameters.

   * Deze velden zijn opgegeven in [AEM Communities Facebook OAuth Provider](#aem-communities-facebook-oauth-provider) en [AEM Communities Twitter OAuth Provider](#aem-communities-twitter-oauth-provider).
   * De standaardvelden zijn toereikend voor de meeste gevallen waarin het wordt gebruikt, maar kunnen worden gewijzigd.

## Facebook-aanmelding {#facebook-login}

### Facebook API-versie {#facebook-api-version}

De sociale aanmelding en het Facebook-voorbeeld voor webwinkels werden ontwikkeld toen de Facebook Graph API versie 1.0 was.
Vanaf AEM 6.4 GA en AEM 6.3 SP1 is de sociale aanmelding bijgewerkt om te werken met de nieuwere Facebook Graph API 2.5-versie.

>[!NOTE]
>
>Voor oudere AEM versies, als u met een uitzondering in logboeken **Kan geen teken uit dit** halen, verbetering aan recentste GVB voor die AEM versie.

Zie [Wijzigingen in de Facebook API-interface](https://developers.facebook.com/docs/apps/changelog) voor informatie over de Facebook Graph API-versie.

### Een Facebook-app {#create-a-facebook-app} maken

Een correct geconfigureerde Facebook-toepassing is vereist om de sociale aanmelding voor Facebook in te schakelen.

Volg de instructies van Facebook op [https://developers.facebook.com/apps/](https://developers.facebook.com/apps/) om een Facebook-toepassing te maken. Wijzigingen in de instructies worden niet in de volgende informatie weergegeven.

In het algemeen geldt vanaf Facebook API v2.7:

* *Een nieuwe Facebook-app toevoegen*
   * Kies Website voor *Platform*:
      * Voer `  https://<server>:<port>.` in voor *Site-URL*
      * Voer bij *Weergavenaam* een titel in die u wilt gebruiken als Titel van de Facebook Connect-service.
      * Voor *Categorie*, geadviseerd kiezen *Toepassingen voor Pagina&#39;s*, maar kan om het even wat zijn.
      * *Product toevoegen: Facebook-aanmelding*
      * Voor *Geldige OAuth omleiden URIs* voert u `  https://<server>:<port>.` in

>[!NOTE]
>
>Voor ontwikkeling werkt http://localhost:4503.

Wanneer de toepassing is gemaakt, zoekt u de instellingen **[!UICONTROL App ID]** en **[!UICONTROL App Secret]**. Deze informatie is vereist voor het configureren van de [Facebook-cloudservice](#createafacebookcloudservice).

### Een Facebook Connect-Cloud Service maken {#create-a-facebook-connect-cloud-service}

Met de [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider)-instantie, die is geïnstantieerd door een cloudserviceconfiguratie te maken, worden de Facebook-toepassing en de lidgroep(en) geïdentificeerd waaraan de nieuwe gebruikers worden toegevoegd.

1. Meld u aan bij de AEM auteur-instantie met beheerdersrechten.
1. Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Facebook Social login configuration]** bij globale navigatie.
1. Selecteer de configuratie **[!UICONTROL context path]**.

   **[!UICONTROL Context path]** moet hetzelfde zijn als het pad voor cloudconfiguratie dat u hebt geselecteerd bij het maken/bewerken van een communitysite.

1. Controleer of uw contextpad is ingeschakeld om hieronder cloudservices te maken.
1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**. Selecteer de context en bewerk de eigenschappen. Schakel cloudconfiguraties in als deze nog niet zijn ingeschakeld.

   ![config-eigenschappen](assets/config-propertiespng.png)

   * Zie de [Configuration Browser](/help/sites-administering/configurations.md) documentatie voor meer informatie.

1. **Configuratie van Facebook-cloudservice maken/** bewerken.

   ![fbsocialloginconfigpng](assets/fbsocialloginconfigpng.png)

   * **[!UICONTROL Title]** (*Vereist*) Voer een weergavetotel in die de Facebook-app identificeert. Het wordt aanbevolen dezelfde naam te gebruiken als de *Weergavenaam* voor de Facebook-app.
   * **[!UICONTROL App ID/API Key]** (*Vereist*) Voer de  ***app-*** id in voor de Facebook-app. Dit identificeert de [Adobe granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider) instantie die van de dialoog wordt gecreeerd.
   * **[!UICONTROL App Secret]** (*Vereist*) Voer de  ***App-*** secretaris in voor de Facebook-app.
   * **[!UICONTROL Create Users]** Als deze optie is ingeschakeld, wordt door het aanmelden met een Facebook-account een AEM gebruikervermelding gemaakt en toegevoegd aan de geselecteerde gebruikersgroep(en).  Standaard is ingeschakeld (sterk aanbevolen).
   * **[!UICONTROL Mask User IDs]**: Laat de selectie uitgeschakeld.
   * **[!UICONTROL Scope Email]**: De e-mailid van de gebruiker moet worden opgehaald van Facebook.
   * **[!UICONTROL Add to User Groups]** Selecteer Gebruikersgroep toevoegen om een of meer  [lidgroepen ](https://helpx.adobe.com/experience-manager/6-3/communities/using/users.html) voor de communautaire site te kiezen waaraan gebruikers worden toegevoegd.

   >[!NOTE]
   >
   >Groepen kunnen op elk gewenst moment worden toegevoegd of verwijderd. Maar het lidmaatschap van bestaande gebruikers wordt hierdoor niet beïnvloed. Automatisch lidmaatschap is alleen van toepassing op nieuwe gebruikers die worden gemaakt na deze veldupdate. Voor sites waar anonieme gebruikers zijn uitgeschakeld, kiest u ervoor gebruikers toe te voegen aan de overeenkomende groep met leden van de community die voor die gesloten communitysite is bedoeld.

   * Selecteer **[!UICONTROL SAVE]**.
   * **[!UICONTROL Publish]**.



Het resultaat is een [Adobe granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#adobe-granite-oauth-application-and-provider) instantie die geen verdere wijziging vereist tenzij het toevoegen van extra werkingsgebied (toestemmingen). Het standaardbereik is de standaardmachtigingen voor aanmelding bij Facebook. Als extra werkingsgebied wordt gewenst, is het noodzakelijk om de configuratie direct uit te geven OSGI. Als er aanpassingen rechtstreeks via systeem/console worden uitgevoerd, moet u de configuraties van de cloudservice niet via de interface van de aanraakinterface bewerken om te voorkomen dat deze worden overschreven.

### AEM Communities Facebook OAuth Provider {#aem-communities-facebook-oauth-provider}

De AEM Communities-provider breidt de [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider)-instantie uit.

Voor deze provider moet u het volgende bewerken:

* Gebruikers kunnen bijwerken
* Extra velden [binnen bereik](#adobe-granite-oauth-application-and-provider) toevoegen

   * Niet alle velden die standaard zijn toegestaan, worden standaard opgenomen.

Als bewerken nodig is, wordt op elke AEM-publicatie-instantie het volgende weergegeven:

1. Meld u aan met beheerdersrechten.
1. Navigeer naar [Webconsole](../../help/sites-deploying/configuring-osgi.md). Bijvoorbeeld http://localhost:4503/system/console/configMgr.
1. Zoek AEM Communities Facebook OAuth Provider.
1. Selecteer het potloodpictogram dat u wilt openen voor bewerking.

   ![fboauthprov_png](assets/fboauthprov_png.png)

   * **[!UICONTROL OAuth Provider ID]**

      (*Required*) De standaardwaarde is *soco-facebook*. Niet bewerken.

   * **[!UICONTROL Cloud Service Config]**

      De standaardwaarde is `/etc/  cloudservices /  facebookconnect`. Niet bewerken.

   * **[!UICONTROL OAuth Provider Service Config]**

      De standaardwaarde is `/apps/social/facebookprovider/config/`. Niet bewerken.

   * **[!UICONTROL Enable Tags]**

      Bewerken niet.

   * **[!UICONTROL User Path]**

      Locatie in de opslagplaats waar gebruikersgegevens worden opgeslagen. Voor een communautaire plaats, om toestemmingen voor leden te verzekeren om elkaars profiel te bekijken, zou de weg het gebrek */home/users/community* moeten zijn.

   * **[!UICONTROL Enable fields]**

      Als deze optie is ingeschakeld, worden de vermelde velden opgegeven in de aanvraag naar Facebook voor gebruikersverificatie en -informatie. De standaardinstelling is uitgeschakeld.

   * **[!UICONTROL Fields]**

      Wanneer Velden zijn ingeschakeld, worden de volgende velden opgenomen wanneer de API voor grafieken op Facebook wordt aangeroepen. De velden moeten zijn toegestaan binnen het bereik dat is gedefinieerd in de configuratie van de cloudservice. Voor extra velden moet Facebook mogelijk toestemming geven. Raadpleeg de sectie over Facebook-aanmeldmachtigingen in de Facebook-documentatie. De standaardvelden die als parameters worden toegevoegd, zijn:

      * id
      * name
      * first_name
      * last_name
      * link
      * locale
      * picture
      * tijdzone
      * update_time
      * geverifieerd
      * email

   Als een veld wordt toegevoegd of gewijzigd, werkt u de overeenkomstige standaardconfiguratie van de synchronisatiehandler bij om de toewijzing te corrigeren.

   * **[!UICONTROL Update User]**

      Als deze optie is ingeschakeld, worden de gebruikersgegevens in de dataopslag bij elke aanmelding vernieuwd om rekening te houden met profielwijzigingen of aanvullende aangevraagde gegevens. Standaard is uitgeschakeld.


#### Volgende stappen {#next-steps}

De volgende stappen zijn hetzelfde voor zowel Facebook als Twitter:

* [De configuraties van de cloudservice publiceren](#publishcloudservices)
* [Inschakelen voor een communitysite](#enable-social-login)

## Aanmelden bij Twitter {#twitter-login}

### Een Twitter-app {#create-a-twitter-app} maken

Er is een geconfigureerde Twitter-toepassing vereist om de sociale aanmelding voor Twitter in te schakelen.

Volg de meest recente instructies om een nieuwe Twitter-toepassing te maken op [https://apps.twitter.com](https://apps.twitter.com/).

In het algemeen:

1. Voer een *Naam* in die uw Twitter-toepassing identificeert voor de gebruikers van uw website.
1. Voer een *Beschrijving* in.
1. Voer `https://<server>` in voor *website*.
1. Voor *Callback URL* - ga `https://server` in.

   >[!NOTE]
   >
   >Het is niet nodig de poort op te geven.
   >
   >Voor ontwikkeling werkt https://127.0.0.1/.

1. Wanneer de toepassing is gemaakt, zoekt u **[!UICONTROL Consumer (API) Key]** en **[!UICONTROL Consumer (API) Secret]**. Deze informatie is nodig voor het configureren van de [Twitter-cloudservice](#createatwittercloudservice).

#### Machtigingen {#permissions}

In de sectie met machtigingen voor het beheer van de Twitter-toepassing:

* **[!UICONTROL Access]**: Selecteer `Read only`.

   * Andere opties worden niet ondersteund

* **[!UICONTROL Additional Permissions]**: Kies optioneel  `Request email addresses from users`.

   * Als deze optie niet is geselecteerd, bevat het gebruikersprofiel in AEM geen e-mailadres.
   * In de instructies van Twitter staat dat er nog meer stappen moeten worden gezet.

Het enige REST-verzoek dat voor aanmelden via een sociaal netwerk wordt gedaan, is naar *[GET account/verificatiegegevens](https://dev.twitter.com/rest/reference/get/account/verify_credentials)*.

### Een Twitter Connect-Cloud Service maken {#create-a-twitter-connect-cloud-service}

Met de [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider)-instantie, die is geïnstantieerd door een cloudserviceconfiguratie te maken, worden de Twitter-toepassing en de lidgroep(en) geïdentificeerd waaraan de nieuwe gebruikers worden toegevoegd.

1. Meld u aan met beheerdersrechten voor de auteurinstantie.
1. Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Twitter Social login configuration]** bij globale navigatie.
1. Kies de **[!UICONTROL context path]** configuratie.

   Het pad naar de context moet hetzelfde zijn als het pad naar de cloudconfiguratie dat u hebt geselecteerd bij het maken/bewerken van een communitysite.

1. Controleer of uw contextpad is ingeschakeld om hieronder cloudservices te maken.
1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**. Selecteer de context en bewerk de eigenschappen. Schakel cloudconfiguraties in als deze nog niet zijn ingeschakeld.

   ![twitterconfigproppng](assets/twitterconfigproppng.png)

   * Zie de [Configuration Browser](/help/sites-administering/configurations.md) documentatie voor meer informatie.

1. Configuratie van de Twitter-cloudservice maken/bewerken.

   ![twittersocialloginpng](assets/twittersocialloginpng.png)

   * **[!UICONTROL Title]**

      (*Required*) ga een vertoningstitel in die de Twitter App identificeert. Het wordt aanbevolen dezelfde naam te gebruiken als de *Weergavenaam* voor de Twitter-app.

   * **[!UICONTROL Consumer Key]**

      (*Required*) ga **Consumer (API) Sleutel** voor Twitter app in. Dit identificeert de [Adobe granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider) instantie die van de dialoog wordt gecreeerd.

   * **[!UICONTROL Consumer Secret]**

      (*Required*) ga ***Consumer(API) Geheim*** voor de Twitter App in.

   * **[!UICONTROL Create Users]**

      Als deze optie is ingeschakeld, wordt door aanmelden met een Twitter-account een AEM gebruikervermelding gemaakt en toegevoegd aan de geselecteerde gebruikersgroep(en). Standaard is ingeschakeld (sterk aanbevolen).

   * **[!UICONTROL Mask User IDs]**

      Laat de selectie uitgeschakeld.

   * **[!UICONTROL Add to User Groups]**

      Selecteer Gebruikersgroep toevoegen om een of meer [lidgroepen](https://helpx.adobe.com/experience-manager/6-3/communities/using/users.html) te kiezen voor de communitysite waaraan gebruikers worden toegevoegd.
   >[!NOTE]
   >
   >Groepen kunnen op elk gewenst moment worden toegevoegd of verwijderd. Het lidmaatschap van bestaande gebruikers wordt echter niet beïnvloed. Automatisch lidmaatschap is alleen van toepassing op nieuwe gebruikers die worden gemaakt na deze veldupdate. Voor Plaatsen waar de anonieme gebruikers gehandicapt zijn, voeg gebruikers aan overeenkomstige gemeenschap-lidgroep toe die voor die gesloten communautaire plaats wordt bedoeld.

1. Selecteer **[!UICONTROL SAVE]** en **[!UICONTROL Publish]**.

Het resultaat is een [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#adobe-granite-oauth-application-and-provider)-instantie die niet verder hoeft te worden gewijzigd. Het standaardbereik is de standaardmachtigingen voor Twitter-aanmelding.

### AEM Communities Twitter OAuth Provider {#aem-communities-twitter-oauth-provider}

De configuratie van AEM Communities breidt [Adobe granite OAuth Application en Provider](#adobe-granite-oauth-application-and-provider) instantie uit. Deze provider moet worden bewerkt om gebruikersupdates toe te staan.

Als bewerken nodig is, wordt op elke AEM-publicatie-instantie het volgende weergegeven:

1. Meld u aan met beheerdersrechten.
1. Navigeer naar [Webconsole](../../help/sites-deploying/configuring-osgi.md).

   Bijvoorbeeld http://localhost:4503/system/console/configMgr.

1. Zoek naar AEM Communities Twitter OAuth Provider.
1. Selecteer het potloodpictogram dat u wilt openen voor bewerking.

   ![twitteroauth_png](assets/twitteroauth_png.png)

   * **[!UICONTROL OAuth Provider ID]**

   (*Required*) De standaardwaarde is *soco-twitter*. Niet bewerken.

   * **[!UICONTROL Cloud Service Config]**

      De standaardwaarde is *conf.* Niet bewerken.

   * **[!UICONTROL OAuth Provider Service Config]**

      De standaardwaarde is `/apps/social/twitterprovider/config/`. Niet bewerken.

   * **[!UICONTROL User Path]**

      Locatie in de opslagplaats waar gebruikersgegevens worden opgeslagen. Voor een communautaire plaats, om toestemmingen voor leden te verzekeren om elkaars profiel te bekijken, zou de weg het gebrek `/home/users/community` moeten zijn.

   * **[!UICONTROL Enable Params]** niet bewerken
   * **[!UICONTROL URL Parameters]** niet bewerken
   * **[!UICONTROL Update User]**

      Als deze optie is ingeschakeld, worden de gebruikersgegevens in de dataopslag bij elke aanmelding vernieuwd om rekening te houden met profielwijzigingen of aanvullende aangevraagde gegevens. De standaardinstelling is uitgeschakeld.


#### Volgende stappen {#next-steps-1}

De volgende stappen zijn hetzelfde voor zowel Facebook als Twitter:

* [De configuraties van de cloudservice publiceren](#publishcloudservices)
* [Inschakelen voor een communitysite](#enable-social-login)

## Sociale aanmelding inschakelen {#enable-social-login}

### AEM Communities Sites Console {#aem-communities-sites-console}

Nadat een cloudservice is geconfigureerd, kan deze worden ingeschakeld voor de relevante instelling voor sociale aanmelding voor een communitysite met behulp van het subdeelvenster Instellingen [Gebruikersbeheer](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#USERMANAGEMENT) tijdens de communitysite [creation](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#SiteCreation) of [management](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#ModifyingSiteProperties).

1. Kies de context van uw siteconfiguratie waarin u uw inlogconfiguraties voor sociale media hebt opgeslagen.

1. Stel op het tabblad Algemeen cloudconfiguraties in.

   ![beheersites_png](assets/managesites_png.png)

1. Schakel op het tabblad Instellingen **[!UICONTROL Social Logins]** en Opslaan in.

   ![usermgmt_png](assets/usermgmt_png.png)

## Sociale aanmelding testen {#test-social-login}

* Zorg ervoor dat [Adobe granite OAuth Authentication Handler](#adobe-granite-oauth-authentication-handler) is ingeschakeld op alle publicatieinstanties.
* Controleer of de cloudservices zijn gepubliceerd.
* Controleer of de site van de community is gepubliceerd.
* Start de gepubliceerde site in een browser.
Bijvoorbeeld http://localhost:4503/content/sites/engage/en.html
* Selecteer **[!UICONTROL Login In]**.
* Selecteer **[!UICONTROL Sign in with Facebook]** of **[!UICONTROL Sign in with Twitter]**.
* Meld u aan met de juiste gegevens als u zich nog niet hebt aangemeld bij Facebook of Twitter.
* Het kan nodig zijn machtigingen te verlenen afhankelijk van het dialoogvenster dat wordt weergegeven door de app Facebook of Twitter.
* De werkbalk boven aan de pagina wordt bijgewerkt met de geslaagde aanmelding.
* Selecteer **[!UICONTROL Profile]**: op de pagina Profiel worden de avatar-afbeelding, voornaam en achternaam van de gebruiker weergegeven. De informatie uit het Facebook- of Twitter-profiel wordt ook weergegeven op basis van de toegestane velden/params.

## AEM Platform OAuth Configurations {#aem-platform-oauth-configurations}

### Adobe graniet OAuth-verificatiehandler {#adobe-granite-oauth-authentication-handler}

`Adobe Granite OAuth Authentication Handler` is niet standaard ingeschakeld en ***moet zijn ingeschakeld op alle AEM publicatieinstanties.***

Om de authentificatiemanager bij toe te laten publiceren, open eenvoudig OSGi config en bewaar het:

* Meld u aan met beheerdersrechten.
* Navigeer naar [Webconsole](../../help/sites-deploying/configuring-osgi.md).
Bijvoorbeeld http://localhost:4503/system/console/configMgr
* `Adobe Granite OAuth Authentication Handler` zoeken.
* Selecteer deze optie om de configuratie voor bewerking te openen.
* Selecteer **[!UICONTROL Save]**.

![chlimage_1-489](assets/chlimage_1-489.png)

>[!CAUTION]
>
>Let op dat u de verificatiehandler niet verwart met een Facebook- of Twitter-instantie van *Adobe Granite OAuth Application and Provider*.

![chlimage_1-490](assets/chlimage_1-490.png)

### Adobe graniet OAuth-toepassing en -provider {#adobe-granite-oauth-application-and-provider}

Wanneer een cloudservice voor Facebook of Twitter wordt gemaakt, wordt een exemplaar van `Adobe Granite OAuth Authentication Handler` gemaakt.

Ga als volgt te werk om de gemaakte instantie voor een Facebook- of Twitter-app te zoeken:

1. Meld u aan met beheerdersrechten.
1. Navigeer naar [Webconsole](../../help/sites-deploying/configuring-osgi.md).

   Bijvoorbeeld http://localhost:4503/system/console/configMgr.

1. Zoek Adobe Granite OAuth Application and Provider.

   * Zoek de instantie waarbij **[!UICONTROL Client ID]** overeenkomt met **[!UICONTROL App ID]**.

      ![chlimage_1-491](assets/chlimage_1-491.png)

      Met uitzondering van de volgende eigenschappen, verlaat u de andere eigenschappen van de config ongewijzigd:

   * **[!UICONTROL Config ID]**

      (*Required*) OAuth configuratie IDs moet uniek zijn. Automatisch gegenereerd wanneer een cloudservice wordt gemaakt.

   * **[!UICONTROL Client ID]**

      (*Required*) De toepassings-id die is opgegeven toen de cloudservice werd gemaakt.

   * **[!UICONTROL Client Secret]**

      (*Required*) Het toepassingsgeheim verstrekte toen de wolkendienst werd gecreeerd.

   * **[!UICONTROL Scope]**

      (*Optioneel*) De provider kan om extra mogelijkheden vragen voor wat is toegestaan. Het standaardbereik omvat de machtigingen die nodig zijn voor het verstrekken van sociale verificatie- en profielgegevens.

   * **[!UICONTROL Provider ID]**

      (*Required*) De leverancier-id voor AEM Communities wordt ingesteld op het moment dat de cloudservice werd gemaakt. Niet bewerken. Voor Facebook Connect is de waarde *soco-facebook*. Voor Twitter Connect is de waarde *soco -twitter*.

   * **[!UICONTROL Groups]**

      (*Aanbevolen*) Één of meerdere lidgroepen waaraan de gecreeerde gebruikers worden toegevoegd. Voor AEM Communities wordt aanbevolen de lidgroep voor de community-site op te nemen.

   * **[!UICONTROL Callback URL]**

      (*Optionele*) URL die met de OAuth-providers is geconfigureerd om de client terug te sturen. Gebruik een relatieve URL om de host van de oorspronkelijke aanvraag te gebruiken. Laat leeg om de oorspronkelijk aangevraagde URL te gebruiken. Achtervoegsel &quot;/callback/j_security_check&quot; wordt automatisch toegevoegd aan deze URL.
   >[!NOTE]
   >
   >Het domein voor de callback moet zijn geregistreerd bij de provider (Facebook of Twitter).

Voor elke configuratie van de authentificatiemanager OAuth, zijn er twee extra configuraties die in de instantie worden gecreeerd:

* Apache Jackrabbit Oak Default Sync Handler (org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler) - Geen bewerkingen vereist in dit venster, maar u kunt de toewijzingen van gebruikersvelden bekijken hoe Facebook-velden worden toegewezen aan een CQ-gebruikersprofielknooppunt. U ziet ook dat &#39;Naam synchronisatiehandler&#39; overeenkomt met de configuratie-id van de configuratie van de OAuth-provider.
* Apache Jackrabbit Oak External Login Module (org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory) - Er zijn geen bewerkingen vereist, maar u kunt zien dat &#39;Naam identiteitsprovider&#39; en &#39;Naam synchronisatiehandler&#39; hetzelfde zijn en verwijzen naar respectievelijk de overeenkomstige OAuth- en sync-handlerconfiguraties.

Zie [Verificatie met Apache Oak External Login Module](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html) voor meer informatie.

## OAuth User Traversal Performance {#oauth-user-traversal-performance}

Voor sites uit de gebruikersgemeenschap die honderdduizenden gebruikers zien registreren met hun Facebook- of Twitter-aanmelding, kunt u de traversale prestaties van de query die wordt uitgevoerd wanneer een bezoeker van de site zijn sociale aanmelding gebruikt, verbeteren door de volgende Oak-index toe te voegen.

Als er traversale waarschuwingen worden weergegeven in de logboeken, wordt aangeraden deze index toe te voegen.

Op een instantie van de auteur, aangemeld met beheerdersrechten:

1. Vanuit globale navigatie: Selecteer **Gereedschappen, [CRX/DE Lite](../../help/sites-developing/developing-with-crxde-lite.md).**
1. Creeer een index genoemd ntBaseLucene-oauth van een exemplaar van ntBaseLucene:

   * Onder knooppunt `/oak:index`
   * Knooppunt `ntBaseLucene` selecteren
   * Selecteer **[!UICONTROL Copy]**
   * Selecteer `/oak:index`
   * Selecteer **[!UICONTROL Paste]**
   * Naam van kopie van ntBaseLucene wijzigen in `ntBaseLucene-oauth`

1. Wijzig de eigenschappen van node ntBaseLucene-oauth:

   * **[!UICONTROL indexPath]**: `/oak:index/ntBaseLucene-oauth`
   * **[!UICONTROL name]**:  `oauthid-123****`
   * **[!UICONTROL reindex]**:  `true`
   * **[!UICONTROL reindexCount]**:  `1`

1. Onder node/oak:index/ntBaseLucene-oauth/indexRules/nt:base/properties:

   * Verwijder alle onderliggende knooppunten, behalve cqTags.
   * Naam van cqTags wijzigen in `oauthid-123****`
   * De eigenschappen van het knooppunt `oauthid-123****` wijzigen

      * **[!UICONTROL name]**:  `oauthid-123****`
   * Selecteer **[!UICONTROL Save All]**.


* Voor de **naam** `oauthid-123` vervangt u *123* door Facebook ***App ID*** of Twitter ***Consumer (API) Key*** die de waarde is van **Client ID** in [ Adobe Granite OAuth Application and Provider](social-login.md#adobe-granite-oauth-application-and-provider) configuration.

   ![chlimage_1-492](assets/chlimage_1-492.png)

Raadpleeg [Vragen en indexeren](../../help/sites-deploying/queries-and-indexing.md) voor aanvullende informatie en gereedschappen.

## Configuratie {#dispatcher-configuration}

Zie [Dispatcher configureren voor Communities](dispatcher.md).
