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


# Sociale aanmelding met Facebook en Twitter {#social-login-with-facebook-and-twitter}

Met aanmelden via een sociaal netwerk kunt u een bezoeker van een site de optie geven om zich aan te melden bij zijn Facebook- of Twitter-account. Daarom moeten de toegestane Facebook- of Twitter-gegevens worden opgenomen in het profiel voor AEM leden.

![socialloginweretail](assets/socialloginweretail.png)

## Overzicht van sociale aanmelding {#social-login-overview}

Als u sociale aanmelding wilt opnemen, is het *vereist* om aangepaste Facebook- en Twitter-toepassingen te maken.

Hoewel het voorbeeld van de webwinkel voorbeelden biedt voor Facebook- en Twitter-apps en cloudservices, zijn deze niet beschikbaar op een [productiewebsite](../../help/sites-administering/production-ready.md).

De vereiste stappen zijn:

1. [Schakel OAuth-verificatie](#adobe-granite-oauth-authentication-handler) in voor alle AEM publicatieinstanties.

   Als OAuth niet is ingeschakeld, mislukt het aanmelden.

1. **Maak** een sociale app en cloudservice.

   * U kunt als volgt aanmelding bij Facebook ondersteunen:

      * Maak een [Facebook-app](#create-a-facebook-app).
      * Maak en publiceer een [Facebook Connect-cloudservice](#create-a-facebook-connect-cloud-service).
   * Aanmelden met Twitter ondersteunen:

      * Maak een [Twitter-app](#create-a-twitter-app).
      * Maak en publiceer een [Twitter Connect-cloudservice](#create-a-twitter-connect-cloud-service).


1. [**Schakel** sociale aanmelding](#enable-social-login) voor een communitysite in.

Er zijn twee basisbeginselen:

1. **Bereik** (machtigingen) geeft de gegevens aan die de app mag aanvragen.

   * De instanties Facebook en Twitter [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) bevatten standaard de basismachtigingen voor de app in hun bereik.

1. **Velden** (params) geven de eigenlijke aangevraagde gegevens op met URL-parameters.

   * Deze velden zijn opgegeven in [AEM Communities Facebook OAuth Provider](#aem-communities-facebook-oauth-provider) en [AEM Communities Twitter OAuth Provider](#aem-communities-twitter-oauth-provider).
   * De standaardvelden zijn toereikend voor de meeste gevallen waarin het wordt gebruikt, maar kunnen worden gewijzigd.

## Facebook-aanmelding {#facebook-login}

### Facebook API-versie {#facebook-api-version}

De sociale aanmelding en het Facebook-voorbeeld voor webwinkels werden ontwikkeld toen de Facebook Graph API versie 1.0 was.
Vanaf AEM 6.4 GA en AEM 6.3 SP1 is de sociale aanmelding bijgewerkt om te werken met de nieuwere Facebook Graph API 2.5-versie.

>[!NOTE]
>
>Voor oudere AEM versies, als u met een uitzondering in logboeken wordt geconfronteerd **kan geen teken uit dit** halen, verbetering aan recentste GFP voor die AEM versie.

Zie de wijziging in de API van [Facebook voor informatie over de Facebook Graph API-versie](https://developers.facebook.com/docs/apps/changelog).

### Een Facebook-app maken {#create-a-facebook-app}

Een correct geconfigureerde Facebook-toepassing is vereist om de sociale aanmelding voor Facebook in te schakelen.

Volg de instructies van Facebook op [https://developers.facebook.com/apps/](https://developers.facebook.com/apps/)om een Facebook-toepassing te maken. Wijzigingen in de instructies worden niet in de volgende informatie weergegeven.

In het algemeen geldt vanaf Facebook API v2.7:

* *Een nieuwe Facebook-app toevoegen*
   * Kies bij *Platform* de optie Website:
      * Voer bij URL *van* site in `  https://<server>:<port>.`
      * Voer bij *Weergavenaam* een titel in die u wilt gebruiken als Titel van de Facebook-service Verbinding.
      * Voor *Categorie* kunt u het beste *Apps voor Pagina*&#39;s kiezen, maar dit kan alles zijn.
      * *Product toevoegen:  Facebook-aanmelding*
      * Voer voor *geldige OAuth-omleidings-URI&#39;s* in `  https://<server>:<port>.`

>[!NOTE]
>
>Voor ontwikkeling werkt http://localhost:4503.

Wanneer de toepassing is gemaakt, zoekt u de **[!UICONTROL App ID]** instellingen en de **[!UICONTROL App Secret]** instellingen. Deze informatie is vereist voor het configureren van de [Facebook-cloudservice](#createafacebookcloudservice).

### Een Facebook Connect-Cloud Service maken {#create-a-facebook-connect-cloud-service}

De [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) -instantie, geïnstantieerd door een cloudserviceconfiguratie te maken, identificeert de Facebook-toepassing en de lidgroep(en) waaraan de nieuwe gebruikers worden toegevoegd.

1. Meld u aan bij de AEM auteur-instantie met beheerdersrechten.
1. Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Facebook Social login configuration]**.
1. Selecteer de configuratie **[!UICONTROL context path]**.

   **[!UICONTROL Context path]** moet hetzelfde zijn als het pad voor cloudconfiguratie dat u hebt geselecteerd bij het maken/bewerken van een communitysite.

1. Controleer of uw contextpad is ingeschakeld om hieronder cloudservices te maken.
1. Go to **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**. Selecteer de context en bewerk de eigenschappen. Schakel cloudconfiguraties in als deze nog niet zijn ingeschakeld.

   ![config-eigenschappen](assets/config-propertiespng.png)

   * See the [Configuration Browser](/help/sites-administering/configurations.md) documentation for more information.

1. **Configuratie van Facebook-cloudservice maken/bewerken** .

   ![fbsocialloginconfigpng](assets/fbsocialloginconfigpng.png)

   * **[!UICONTROL Title]** (*Vereist*) Voer een weergavetotel in die de Facebook-app identificeert. Het wordt aanbevolen dezelfde naam in te voeren als de *weergavenaam* voor de Facebook-app.
   * **[!UICONTROL App ID/API Key]** (*Vereist*) Voer de ***app-id*** voor de Facebook-app in. Dit identificeert de [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider) instantie die van het dialoogvenster is gemaakt.
   * **[!UICONTROL App Secret]** (*Vereist*) Voer het ***App-geheim*** in voor de Facebook-app.
   * **[!UICONTROL Create Users]** Als deze optie is ingeschakeld, wordt door het aanmelden met een Facebook-account een AEM gebruikervermelding gemaakt en toegevoegd aan de geselecteerde gebruikersgroep(en).  Standaard is ingeschakeld (sterk aanbevolen).
   * **[!UICONTROL Mask User IDs]**: Laat de selectie uitgeschakeld.
   * **[!UICONTROL Scope Email]**: De e-mailid van de gebruiker moet worden opgehaald van Facebook.
   * **[!UICONTROL Add to User Groups]** Selecteer Gebruikersgroep toevoegen om een of meer [lidgroepen](https://helpx.adobe.com/experience-manager/6-3/communities/using/users.html) te kiezen voor de communitysite waaraan gebruikers worden toegevoegd.

   >[!NOTE]
   >
   >Groepen kunnen op elk gewenst moment worden toegevoegd of verwijderd. Maar het lidmaatschap van bestaande gebruikers wordt hierdoor niet beïnvloed. Automatisch lidmaatschap is alleen van toepassing op nieuwe gebruikers die worden gemaakt na deze veldupdate. Voor sites waar anonieme gebruikers zijn uitgeschakeld, kiest u ervoor gebruikers toe te voegen aan de overeenkomende groep met leden van de community die voor die gesloten communitysite is bedoeld.

   * Selecteer **[!UICONTROL SAVE]**.
   * **[!UICONTROL Publish]**.



Het resultaat is een [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#adobe-granite-oauth-application-and-provider) -instantie waarvoor geen verdere wijziging vereist is, tenzij er een extra bereik (machtigingen) wordt toegevoegd. Het standaardbereik is de standaardmachtigingen voor aanmelding bij Facebook. Als extra werkingsgebied wordt gewenst, is het noodzakelijk om de configuratie direct uit te geven OSGI. Als er aanpassingen rechtstreeks via systeem/console worden uitgevoerd, moet u de configuraties van de cloudservice niet via de interface van de aanraakinterface bewerken om te voorkomen dat deze worden overschreven.

### AEM Communities Facebook OAuth Provider {#aem-communities-facebook-oauth-provider}

De AEM Communities-provider breidt de [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) -instantie uit.

Voor deze provider moet u het volgende bewerken:

* Gebruikers kunnen bijwerken
* Extra velden [binnen bereik toevoegen](#adobe-granite-oauth-application-and-provider)

   * Niet alle velden die standaard zijn toegestaan, worden standaard opgenomen.

Als bewerken nodig is, wordt op elke AEM-publicatie-instantie het volgende weergegeven:

1. Meld u aan met beheerdersrechten.
1. Navigeer naar de [webconsole](../../help/sites-deploying/configuring-osgi.md). Bijvoorbeeld http://localhost:4503/system/console/configMgr.
1. Zoek AEM Communities Facebook OAuth Provider.
1. Selecteer het potloodpictogram dat u wilt openen voor bewerking.

   ![fboauthprov_png](assets/fboauthprov_png.png)

   * **[!UICONTROL OAuth Provider ID]**

      (*Vereist*) De standaardwaarde is *soco-facebook*. Niet bewerken.

   * **[!UICONTROL Cloud Service Config]**

      De standaardwaarde is `/etc/  cloudservices /  facebookconnect`. Niet bewerken.

   * **[!UICONTROL OAuth Provider Service Config]**

      De standaardwaarde is `/apps/social/facebookprovider/config/`. Niet bewerken.

   * **[!UICONTROL Enable Tags]**

      Bewerken niet.

   * **[!UICONTROL User Path]**

      Locatie in de opslagplaats waar gebruikersgegevens worden opgeslagen. Voor een communautaire plaats, om toestemmingen voor leden te verzekeren om elkaars profiel te bekijken, zou de weg het gebrek */huis/gebruikers/gemeenschap* moeten zijn.

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

## Twitter-aanmelding {#twitter-login}

### Een Twitter-app maken {#create-a-twitter-app}

Er is een geconfigureerde Twitter-toepassing vereist om de sociale aanmelding voor Twitter in te schakelen.

Volg de meest recente instructies om een nieuwe Twitter-toepassing te maken op [https://apps.twitter.com](https://apps.twitter.com/).

In het algemeen:

1. Voer een *naam* in die uw Twitter-toepassing identificeert voor de gebruikers van uw website.
1. Voer een *beschrijving* in.
1. Voer voor *website* de gegevens in `https://<server>`.
1. Voor *Callback URL* - ga `https://server`.

   >[!NOTE]
   >
   >Het is niet nodig de poort op te geven.
   >
   >Voor ontwikkeling werkt https://127.0.0.1/.

1. Wanneer de toepassing is gemaakt, zoekt u de toepassing **[!UICONTROL Consumer (API) Key]** en **[!UICONTROL Consumer (API) Secret]**. Deze informatie is nodig voor het configureren van de [Twitter-cloudservice](#createatwittercloudservice).

#### Machtigingen {#permissions}

In de sectie met machtigingen voor het beheer van de Twitter-toepassing:

* **[!UICONTROL Access]**: Selecteer `Read only`.

   * Andere opties worden niet ondersteund

* **[!UICONTROL Additional Permissions]**: Kies optioneel `Request email addresses from users`.

   * Als deze optie niet is geselecteerd, bevat het gebruikersprofiel in AEM geen e-mailadres.
   * In de instructies van Twitter staat dat er nog meer stappen moeten worden gezet.

De enige REST-aanvraag die voor aanmelden via een sociaal netwerk is ingediend, is het *[GET van de gegevens](https://dev.twitter.com/rest/reference/get/account/verify_credentials)* van de account/het verifiëren van de gegevens.

### Een Twitter Connect-Cloud Service maken {#create-a-twitter-connect-cloud-service}

De [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) -instantie, geïnstantieerd door een cloudserviceconfiguratie te maken, identificeert de Twitter-toepassing en de lidgroep(en) waaraan de nieuwe gebruikers worden toegevoegd.

1. Meld u aan met beheerdersrechten voor de auteurinstantie.
1. Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Twitter Social login configuration]**.
1. Kies de **[!UICONTROL context path]** configuratie.

   Het pad naar de context moet hetzelfde zijn als het pad naar de cloudconfiguratie dat u hebt geselecteerd bij het maken/bewerken van een communitysite.

1. Controleer of uw contextpad is ingeschakeld om hieronder cloudservices te maken.
1. Go to **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**. Selecteer de context en bewerk de eigenschappen. Schakel cloudconfiguraties in als deze nog niet zijn ingeschakeld.

   ![twitterconfigproppng](assets/twitterconfigproppng.png)

   * See the [Configuration Browser](/help/sites-administering/configurations.md) documentation for more information.

1. Configuratie van de Twitter-cloudservice maken/bewerken.

   ![twittersocialloginpng](assets/twittersocialloginpng.png)

   * **[!UICONTROL Title]**

      (*Vereist*) Voer een weergavetoewijzing in die de Twitter-app aangeeft. Het wordt aanbevolen dezelfde naam in te voeren als de *weergavenaam* voor de Twitter-app.

   * **[!UICONTROL Consumer Key]**

      (*Vereist*) Voer de sleutel **voor de** consument (API) in voor de Twitter-app. Dit identificeert de [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider) instantie die van het dialoogvenster is gemaakt.

   * **[!UICONTROL Consumer Secret]**

      (*Vereist*) Voer het ***Consumentengeheim*** (API) voor de Twitter-app in.

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

Het resultaat is een [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#adobe-granite-oauth-application-and-provider) -instantie die niet verder hoeft te worden gewijzigd. Het standaardbereik is de standaardmachtigingen voor Twitter-aanmelding.

### AEM Communities Twitter OAuth Provider {#aem-communities-twitter-oauth-provider}

De AEM Communities-configuratie breidt de [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) -instantie uit. Deze provider moet worden bewerkt om gebruikersupdates toe te staan.

Als bewerken nodig is, wordt op elke AEM-publicatie-instantie het volgende weergegeven:

1. Meld u aan met beheerdersrechten.
1. Navigeer naar de [webconsole](../../help/sites-deploying/configuring-osgi.md).

   Bijvoorbeeld http://localhost:4503/system/console/configMgr.

1. Zoek naar AEM Communities Twitter OAuth Provider.
1. Selecteer het potloodpictogram dat u wilt openen voor bewerking.

   ![twitteroauth_png](assets/twitteroauth_png.png)

   * **[!UICONTROL OAuth Provider ID]**

   (*Vereist*) De standaardwaarde is *soco-twitter*. Niet bewerken.

   * **[!UICONTROL Cloud Service Config]**

      The default value is *conf.* Niet bewerken.

   * **[!UICONTROL OAuth Provider Service Config]**

      De standaardwaarde is `/apps/social/twitterprovider/config/`. Niet bewerken.

   * **[!UICONTROL User Path]**

      Locatie in de opslagplaats waar gebruikersgegevens worden opgeslagen. Voor een communautaire plaats, om toestemmingen voor leden te verzekeren om elkaars profiel te bekijken, zou de weg het gebrek moeten zijn `/home/users/community`.

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

Zodra een wolkendienst wordt gevormd, kan het voor het relevante Sociale Aanmelden plaatsen voor een communautaire plaats worden toegelaten gebruikend het subpanel van de Montages van het Beheer van de [Gebruiker](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#USERMANAGEMENT) tijdens de [verwezenlijking](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#SiteCreation) of het [beheer](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#ModifyingSiteProperties)van de communautaire plaats.

1. Kies de context van uw siteconfiguratie waarin u uw inlogconfiguraties voor sociale media hebt opgeslagen.

1. Stel op het tabblad Algemeen cloudconfiguraties in.

   ![beheersites_png](assets/managesites_png.png)

1. Schakel op het tabblad Instellingen de optie **[!UICONTROL Social Logins]** Opslaan in.

   ![usermgmt_png](assets/usermgmt_png.png)

## Sociale aanmelding testen {#test-social-login}

* Zorg ervoor dat [Adobe Granite OAuth Authentication Handler](#adobe-granite-oauth-authentication-handler) is ingeschakeld voor alle publicatieinstanties.
* Controleer of de cloudservices zijn gepubliceerd.
* Controleer of de site van de community is gepubliceerd.
* Start de gepubliceerde site in een browser.
Bijvoorbeeld http://localhost:4503/content/sites/engage/en.html
* Selecteer **[!UICONTROL Login In]**.
* Selecteer **[!UICONTROL Sign in with Facebook]** of **[!UICONTROL Sign in with Twitter]**.
* Meld u aan met de juiste gegevens als u zich nog niet hebt aangemeld bij Facebook of Twitter.
* Het kan nodig zijn machtigingen te verlenen afhankelijk van het dialoogvenster dat wordt weergegeven door de app Facebook of Twitter.
* De werkbalk boven aan de pagina wordt bijgewerkt met de geslaagde aanmelding.
* Selecteren **[!UICONTROL Profile]**: op de pagina Profiel worden de avatar-afbeelding, voornaam en achternaam van de gebruiker weergegeven. De informatie uit het Facebook- of Twitter-profiel wordt ook weergegeven op basis van de toegestane velden/params.

## Platform OAuth-configuraties AEM {#aem-platform-oauth-configurations}

### Adobe Granite OAuth-verificatiehandler {#adobe-granite-oauth-authentication-handler}

De optie `Adobe Granite OAuth Authentication Handler` is niet standaard ingeschakeld en ***moet op alle AEM publicatieinstanties zijn ingeschakeld.***

Om de authentificatiemanager bij toe te laten publiceren, open eenvoudig OSGi config en bewaar het:

* Meld u aan met beheerdersrechten.
* Navigeer naar de [webconsole](../../help/sites-deploying/configuring-osgi.md).
Bijvoorbeeld http://localhost:4503/system/console/configMgr
* Zoeken `Adobe Granite OAuth Authentication Handler`.
* Selecteer deze optie om de configuratie voor bewerking te openen.
* Selecteer **[!UICONTROL Save]**.

![chlimage_1-489](assets/chlimage_1-489.png)

>[!CAUTION]
>
>Let op dat u de verificatiehandler niet verwart met een Facebook- of Twitter-instantie van *Adobe Granite OAuth Application en Provider*.

![chlimage_1-490](assets/chlimage_1-490.png)

### Adobe Granite OAuth-toepassing en -provider {#adobe-granite-oauth-application-and-provider}

Wanneer er een cloudservice voor Facebook of Twitter wordt gemaakt, `Adobe Granite OAuth Authentication Handler` wordt er een exemplaar van gemaakt.

Ga als volgt te werk om de gemaakte instantie voor een Facebook- of Twitter-app te zoeken:

1. Meld u aan met beheerdersrechten.
1. Navigeer naar de [webconsole](../../help/sites-deploying/configuring-osgi.md).

   Bijvoorbeeld http://localhost:4503/system/console/configMgr.

1. Zoek Adobe Granite OAuth Application and Provider.

   * Zoek de instantie waar deze **[!UICONTROL Client ID]** overeenkomt met de **[!UICONTROL App ID]**.

      ![chlimage_1-491](assets/chlimage_1-491.png)

      Met uitzondering van de volgende eigenschappen, verlaat u de andere eigenschappen van de config ongewijzigd:

   * **[!UICONTROL Config ID]**

      (*Vereist*) OAuth configuratie IDs moet uniek zijn. Automatisch gegenereerd wanneer een cloudservice wordt gemaakt.

   * **[!UICONTROL Client ID]**

      (*Vereist*) De toepassings-id die is opgegeven bij het maken van de cloudservice.

   * **[!UICONTROL Client Secret]**

      (*Vereist*) Het toepassingsgeheim dat is opgegeven bij het maken van de cloudservice.

   * **[!UICONTROL Scope]**

      (*Optioneel*) De leverancier kan om aanvullende mogelijkheden vragen. Het standaardbereik omvat de machtigingen die nodig zijn voor het verstrekken van sociale verificatie- en profielgegevens.

   * **[!UICONTROL Provider ID]**

      (*Vereist*) De provider-id voor AEM Communities wordt ingesteld bij het maken van de cloudservice. Niet bewerken. Voor Facebook Connect is de waarde *soco-facebook*. Voor Twitter Connect is de waarde *soco-twitter*.

   * **[!UICONTROL Groups]**

      (*Aanbevolen*) Een of meer lidgroepen waaraan gemaakte gebruikers zijn toegevoegd. Voor AEM Communities wordt aanbevolen de lidgroep voor de community-site op te nemen.

   * **[!UICONTROL Callback URL]**

      (*Optioneel*) URL die is geconfigureerd met de OAuth-providers om de client terug te sturen. Gebruik een relatieve URL om de host van de oorspronkelijke aanvraag te gebruiken. Laat leeg om de oorspronkelijk aangevraagde URL te gebruiken. Achtervoegsel &quot;/callback/j_security_check&quot; wordt automatisch toegevoegd aan deze URL.
   >[!NOTE]
   >
   >Het domein voor de callback moet zijn geregistreerd bij de provider (Facebook of Twitter).

Voor elke configuratie van de authentificatiemanager OAuth, zijn er twee extra configuraties die in de instantie worden gecreeerd:

* Apache Jackrabbit Oak Default Sync Handler (org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler) - Geen bewerkingen vereist in dit venster, maar u kunt de toewijzingen van gebruikersvelden bekijken hoe Facebook-velden worden toegewezen aan een CQ-gebruikersprofielknooppunt. U ziet ook dat &#39;Naam synchronisatiehandler&#39; overeenkomt met de configuratie-id van de configuratie van de OAuth-provider.
* Apache Jackrabbit Oak External Login Module (org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory) - Er zijn geen bewerkingen vereist, maar u kunt zien dat &#39;Naam identiteitsprovider&#39; en &#39;Naam synchronisatiehandler&#39; hetzelfde zijn en verwijzen naar respectievelijk de overeenkomstige OAuth- en sync-handlerconfiguraties.

Zie [Verificatie met Apache Oak External Login Module](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html)voor meer informatie.

## OAuth-prestaties van het gebruikerstraject {#oauth-user-traversal-performance}

Voor sites uit de gebruikersgemeenschap die honderdduizenden gebruikers zien registreren met hun Facebook- of Twitter-aanmelding, kunt u de traversale prestaties van de query die wordt uitgevoerd wanneer een bezoeker van de site zijn sociale aanmelding gebruikt, verbeteren door de volgende Oak-index toe te voegen.

Als er traversale waarschuwingen worden weergegeven in de logboeken, wordt aangeraden deze index toe te voegen.

Op een instantie van de auteur, aangemeld met beheerdersrechten:

1. Vanuit globale navigatie: Selecteer **Hulpmiddelen, [CRX/DE Lite](../../help/sites-developing/developing-with-crxde-lite.md).**
1. Creeer een index genoemd ntBaseLucene-oauth van een exemplaar van ntBaseLucene:

   * Onder knooppunt `/oak:index`
   * Knooppunt selecteren `ntBaseLucene`
   * Selecteer **[!UICONTROL Copy]**
   * Selecteer `/oak:index`
   * Selecteer **[!UICONTROL Paste]**
   * Naam van kopie van ntBaseLucene wijzigen in `ntBaseLucene-oauth`

1. Wijzig de eigenschappen van node ntBaseLucene-oauth:

   * **[!UICONTROL indexPath]**: `/oak:index/ntBaseLucene-oauth`
   * **[!UICONTROL name]**: `oauthid-123****`
   * **[!UICONTROL reindex]**: `true`
   * **[!UICONTROL reindexCount]**: `1`

1. Onder node/oak:index/ntBaseLucene-oauth/indexRules/nt:base/properties:

   * Verwijder alle onderliggende knooppunten, behalve cqTags.
   * Naam van cqTags wijzigen in `oauthid-123****`
   * Eigenschappen van knooppunt wijzigen `oauthid-123****`

      * **[!UICONTROL name]**: `oauthid-123****`
   * Selecteer **[!UICONTROL Save All]**.


* Voor de **naam** vervangt u `oauthid-123`123 *door de Facebook* App ID ***of de Twitter*** Consumer (API)-sleutel ***die de waarde is van de*** **** [](social-login.md#adobe-granite-oauth-application-and-provider) client-id in de OAuth Application and Provider-configuratie vanAdobe Granite.

   ![chlimage_1-492](assets/chlimage_1-492.png)

Voor extra informatie en hulpmiddelen, verwijs naar de Vragen van het [Eik en het Indexeren](../../help/sites-deploying/queries-and-indexing.md).

## Dispatcher Configuration {#dispatcher-configuration}

Zie [Dispatcher configureren voor Gemeenschappen](dispatcher.md).
