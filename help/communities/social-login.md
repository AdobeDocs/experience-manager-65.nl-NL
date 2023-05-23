---
title: Sociale aanmelding met Facebook en Twitter
seo-title: Social Login with Facebook and Twitter
description: Met aanmelden via een sociaal netwerk kunnen sitebezoekers zich aanmelden met hun Facebook- of Twitter-account.
seo-description: Social login lets site visitors to sign in with their Facebook or Twitter account.
uuid: f70e346e-0d8c-41a0-a100-206a420088dc
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: c0a71870-8f95-40c8-9ffd-b7af49723288
role: Admin
exl-id: aed9247c-eb81-470c-9fa4-a98c3df2dcaa
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '2630'
ht-degree: 0%

---

# Sociale aanmelding met Facebook en Twitter {#social-login-with-facebook-and-twitter}

Met aanmelden via een sociaal netwerk kan een sitebezoeker de optie krijgen om zich aan te melden bij zijn Facebook- of Twitter-account. Daarom moeten toegestane Facebook- of Twitter-gegevens worden opgenomen in het profiel AEM lid.

![socialloginweretail](assets/socialloginweretail.png)

## Overzicht van sociale aanmelding {#social-login-overview}

Als u sociale aanmelding wilt opnemen, is het *vereist* om aangepaste Facebook- en Twitter-toepassingen te maken.

Hoewel het voorbeeld van de webhandel voorbeelden biedt voor Facebook- en Twitter-apps en cloudservices, zijn deze niet beschikbaar op een [productiewebsite](../../help/sites-administering/production-ready.md).

De vereiste stappen zijn:

1. [OAuth-verificatie inschakelen](#adobe-granite-oauth-authentication-handler) op alle AEM publicatieinstanties.

   Als OAuth niet is ingeschakeld, mislukt het aanmelden.

1. **Maken** een sociale app en cloudservice.

   * Aanmelden met Facebook ondersteunen:

      * Een [Facebook-app](#create-a-facebook-app).
      * Een [Facebook Connect Cloud Service](#create-a-facebook-connect-cloud-service).
   * Aanmelden met Twitter ondersteunen:

      * Een [Twitter-app](#create-a-twitter-app).
      * Een [Twitter Connect Cloud Service](#create-a-twitter-connect-cloud-service).


1. [**Inschakelen** sociale aanmelding](#enable-social-login) voor een community-site.

Er zijn twee basisbeginselen:

1. **Toepassingsgebied** (machtigingen) geeft de gegevens aan die de toepassing mag aanvragen.

   * Facebook en Twitter [Adobe Granite OAuth-toepassing en -provider](#adobe-granite-oauth-application-and-provider) deze instanties nemen standaard de basismachtigingen voor de toepassing op in hun bereik.

1. **Velden** (params) geeft de eigenlijke aangevraagde gegevens op met URL-parameters.

   * Deze velden zijn opgegeven in [AEM Communities Facebook OAuth Provider](#aem-communities-facebook-oauth-provider) en [AEM Communities Twitter OAuth Provider](#aem-communities-twitter-oauth-provider).
   * De standaardvelden zijn toereikend voor de meeste gevallen waarin het wordt gebruikt, maar kunnen worden gewijzigd.

## Aanmelden bij facebook {#facebook-login}

### Facebook API-versie {#facebook-api-version}

De sociale aanmelding en het voorbeeld van de wij-retail Facebook werden ontwikkeld toen de Facebook Graph API versie 1.0 was. Vanaf AEM 6.4 GA en AEM 6.3 SP1 is de sociale aanmelding bijgewerkt om te werken met de nieuwere versie van Facebook Graph API 2.5.

>[!NOTE]
>
>Voor oudere AEM als u wordt geconfronteerd met een uitzondering in logboeken **Kan hier geen token uit extraheren**, upgrade naar het nieuwste GVB voor die AEM.

Voor de Facebook Graph API-versiegegevens raadpleegt u de [Facebook API-wijziging](https://developers.facebook.com/docs/apps/changelog).

### Een Facebook-app maken {#create-a-facebook-app}

Een correct geconfigureerde Facebook-toepassing is vereist om de aanmelding voor sociale Facebook in te schakelen.

Volg de instructies van Facebook op om een Facebook-toepassing te maken [https://developers.facebook.com/apps/](https://developers.facebook.com/apps/). Wijzigingen in de instructies worden niet in de volgende informatie weergegeven.

In het algemeen geldt vanaf Facebook API v2.7 het volgende:

* *Een nieuwe Facebook-app toevoegen*
   * Voor *Platform* kiest u Website:
      * Voor *Site-URL*, enter `  https://<server>:<port>.`
      * Voor *Weergavenaam*, voert u een titel in voor gebruik als Titel van de Facebook Connect-service.
      * Voor *Categorie*, aanbevolen *Apps voor pagina&#39;s*, maar kan alles zijn.
      * *Product toevoegen: Aanmelden bij facebook*
      * Voor *Geldige OAuth-omleidings-URI&#39;s*, enter `  https://<server>:<port>.`

>[!NOTE]
>
>Voor ontwikkeling werkt http://localhost:4503.

Wanneer de toepassing is gemaakt, zoekt u de **[!UICONTROL App ID]** en **[!UICONTROL App Secret]** instellingen. Deze informatie is vereist voor het configureren van de [Facebook-cloudservice](#createafacebookcloudservice).

### Een Facebook Connect-Cloud Service maken {#create-a-facebook-connect-cloud-service}

De [Adobe Granite OAuth-toepassing en -provider](#adobe-granite-oauth-application-and-provider) -instantie, geïnstantieerd door het maken van een cloudserviceconfiguratie, identificeert de Facebook-toepassing en de lidgroep(en) waaraan de nieuwe gebruikers worden toegevoegd.

1. Meld u aan bij de AEM auteur-instantie met beheerdersrechten.
1. Selecteer bij globale navigatie de optie **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Facebook Social login configuration]**.
1. Selecteer de configuratie **[!UICONTROL context path]**.

   **[!UICONTROL Context path]** moet hetzelfde zijn als het pad voor cloudconfiguratie dat u hebt geselecteerd bij het maken/bewerken van een communitysite.

1. Controleer of uw contextpad is ingeschakeld om hieronder cloudservices te maken.
1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**. Selecteer de context en bewerk de eigenschappen. Schakel cloudconfiguraties in als deze nog niet zijn ingeschakeld.

   ![config-eigenschappen](assets/config-propertiespng.png)

   * Zie de [Configuratiebrowser](/help/sites-administering/configurations.md) documentatie voor meer informatie.

1. **Maken/bewerken** Configuratie van facebook-cloudservice.

   ![fbsocialloginconfigpng](assets/fbsocialloginconfigpng.png)

   * **[!UICONTROL Title]** (*Vereist*) Voer een weergavetoewijzing in die de Facebook-app identificeert. Het wordt aanbevolen dezelfde naam te gebruiken als de naam die u hebt ingevoerd voor *Weergavenaam* voor de Facebook-app.
   * **[!UICONTROL App ID/API Key]** (*Vereist*) Voer de ***Toepassings-id*** voor de Facebook App. Dit identificeert de [Adobe Granite OAuth-toepassing en -provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider) -instantie die in het dialoogvenster is gemaakt.
   * **[!UICONTROL App Secret]** (*Vereist*) Voer de ***App Secret*** voor de Facebook App.
   * **[!UICONTROL Create Users]** Als deze optie is ingeschakeld, wordt bij het aanmelden met een Facebook-account een AEM gebruikervermelding gemaakt en toegevoegd aan de geselecteerde gebruikersgroep(en).  Standaard is ingeschakeld (sterk aanbevolen).
   * **[!UICONTROL Mask User IDs]**: Laat de selectie uitgeschakeld.
   * **[!UICONTROL Scope Email]**: e-mailadres van gebruiker moet worden opgehaald uit Facebook.
   * **[!UICONTROL Add to User Groups]** Selecteer Gebruikersgroep toevoegen om een of meer te kiezen [ledengroepen](https://helpx.adobe.com/experience-manager/6-3/communities/using/users.html) voor de site van de gemeenschap waaraan gebruikers worden toegevoegd.

   >[!NOTE]
   >
   >Groepen kunnen op elk gewenst moment worden toegevoegd of verwijderd. Maar het lidmaatschap van bestaande gebruikers wordt hierdoor niet beïnvloed. Automatisch lidmaatschap is alleen van toepassing op nieuwe gebruikers die worden gemaakt na deze veldupdate. Voor sites waar anonieme gebruikers zijn uitgeschakeld, kiest u ervoor gebruikers toe te voegen aan de overeenkomende groep met leden van de community die voor die gesloten communitysite is bedoeld.

   * Selecteer **[!UICONTROL SAVE]**.
   * **[!UICONTROL Publish]**.


Het resultaat is een [Adobe Granite OAuth-toepassing en -provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#adobe-granite-oauth-application-and-provider) instantie die geen verdere wijziging vereist tenzij het toevoegen van extra werkingsgebied (toestemmingen). Het standaardbereik is de standaardmachtigingen voor Facebook-aanmelding. Als extra werkingsgebied wordt gewenst, is het noodzakelijk om de configuratie direct uit te geven OSGI. Als er aanpassingen rechtstreeks via systeem/console worden uitgevoerd, moet u de configuraties van de cloudservice niet via de interface van de aanraakinterface bewerken om te voorkomen dat deze worden overschreven.

### AEM Communities Facebook OAuth Provider {#aem-communities-facebook-oauth-provider}

De AEM Communities-provider breidt de [Adobe Granite OAuth-toepassing en -provider](#adobe-granite-oauth-application-and-provider) -instantie.

Voor deze provider moet u het volgende bewerken:

* Gebruikers kunnen bijwerken
* Extra velden toevoegen [binnen bereik](#adobe-granite-oauth-application-and-provider)

   * Niet alle velden die standaard zijn toegestaan, worden standaard opgenomen.

Als bewerken nodig is, wordt op elke AEM-publicatie-instantie het volgende weergegeven:

1. Meld u aan met beheerdersrechten.
1. Ga naar de [Webconsole](../../help/sites-deploying/configuring-osgi.md). Bijvoorbeeld http://localhost:4503/system/console/configMgr.
1. Zoek AEM Communities Facebook OAuth Provider.
1. Selecteer het potloodpictogram dat u wilt openen voor bewerking.

   ![fboauthprov_png](assets/fboauthprov_png.png)

   * **[!UICONTROL OAuth Provider ID]**

      (*Vereist*) Standaardwaarde is *soco-facebook*. Niet bewerken.

   * **[!UICONTROL Cloud Service Config]**

      De standaardwaarde is `/etc/  cloudservices /  facebookconnect`. Niet bewerken.

   * **[!UICONTROL OAuth Provider Service Config]**

      De standaardwaarde is `/apps/social/facebookprovider/config/`. Niet bewerken.

   * **[!UICONTROL Enable Tags]**

      Bewerken niet.

   * **[!UICONTROL User Path]**

      Locatie in de opslagplaats waar gebruikersgegevens worden opgeslagen. Voor een communautaire plaats, om toestemmingen voor leden te verzekeren om elkaars profiel te bekijken, zou de weg het gebrek moeten zijn */home/users/community*.

   * **[!UICONTROL Enable fields]**

      Als deze optie is ingeschakeld, worden de vermelde velden opgegeven in de aanvraag naar Facebook voor gebruikersverificatie en -informatie. De standaardinstelling is uitgeschakeld.

   * **[!UICONTROL Fields]**

      Wanneer Velden zijn ingeschakeld, worden de volgende velden opgenomen wanneer de Facebook Graph API wordt aangeroepen. De velden moeten zijn toegestaan binnen het bereik dat is gedefinieerd in de configuratie van de cloudservice. Voor extra velden is mogelijk goedkeuring door Facebook vereist. Raadpleeg het gedeelte Facebook-aanmeldingsmachtigingen van de Facebook-documentatie. De standaardvelden die als parameters worden toegevoegd, zijn:

      * id
      * name
      * first_name
      * last_name
      * link
      * landinstelling
      * beeld
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

## Aanmelden bij twitter {#twitter-login}

### Een Twitter-app maken {#create-a-twitter-app}

Een geconfigureerde Twitter-toepassing is vereist om de aanmelding voor sociale Twitter in te schakelen.

Volg de meest recente instructies om een nieuwe Twitter-toepassing te maken op [https://apps.twitter.com](https://apps.twitter.com/).

In het algemeen:

1. Voer een *Naam* Hiermee wordt uw Twitter-toepassing geïdentificeerd voor de gebruikers van uw website.
1. Voer een *Beschrijving*.
1. Voor *website* - enter `https://<server>`.
1. Voor *URL voor terugbellen* - enter `https://server`.

   >[!NOTE]
   >
   >Het is niet nodig de poort op te geven.
   >
   >Voor ontwikkeling werkt https://127.0.0.1/.

1. Wanneer de toepassing is gemaakt, zoekt u de **[!UICONTROL Consumer (API) Key]** en **[!UICONTROL Consumer (API) Secret]**. Deze informatie is nodig voor het configureren van de [Twitter-cloudservice](#createatwittercloudservice).

#### Machtigingen {#permissions}

In de sectie met bevoegdheden van het Twitter-toepassingsbeheer:

* **[!UICONTROL Access]**: Selecteer `Read only`.

   * Andere opties worden niet ondersteund

* **[!UICONTROL Additional Permissions]**: Optioneel kiezen `Request email addresses from users`.

   * Als deze optie niet is geselecteerd, bevat het gebruikersprofiel in AEM geen e-mailadres.
   * In twitter-instructies worden extra stappen beschreven.

De enige REST-aanvraag die voor sociale aanmelding is ingediend, is: *[Account GET/verificatiegegevens](https://dev.twitter.com/rest/reference/get/account/verify_credentials)*.

### Een Twitter Connect-Cloud Service maken {#create-a-twitter-connect-cloud-service}

De [Adobe Granite OAuth-toepassing en -provider](#adobe-granite-oauth-application-and-provider) -instantie, geïnstantieerd door het maken van een cloudserviceconfiguratie, identificeert de Twitter-toepassing en de lidgroep(en) waaraan de nieuwe gebruikers worden toegevoegd.

1. Meld u aan met beheerdersrechten voor de auteurinstantie.
1. Selecteer bij globale navigatie de optie **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Twitter Social login configuration]**.
1. Kies de optie **[!UICONTROL context path]** configuratie.

   Het pad naar de context moet hetzelfde zijn als het pad naar de cloudconfiguratie dat u hebt geselecteerd bij het maken/bewerken van een communitysite.

1. Controleer of uw contextpad is ingeschakeld om hieronder cloudservices te maken.
1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**. Selecteer de context en bewerk de eigenschappen. Schakel cloudconfiguraties in als deze nog niet zijn ingeschakeld.

   ![twitterconfigproppng](assets/twitterconfigproppng.png)

   * Zie de [Configuratiebrowser](/help/sites-administering/configurations.md) documentatie voor meer informatie.

1. Twitter-cloudserviceconfiguratie maken/bewerken.

   ![twittersocialloginpng](assets/twittersocialloginpng.png)

   * **[!UICONTROL Title]**

      (*Vereist*) Voer een weergavetoewijzing in die de Twitter-app identificeert. Het wordt aanbevolen dezelfde naam te gebruiken als de naam die u hebt ingevoerd voor *Weergavenaam* voor de Twitter-app.

   * **[!UICONTROL Consumer Key]**

      (*Vereist*) Voer de **Consumentencode (API)** voor de Twitter-app. Dit identificeert de [Adobe Granite OAuth-toepassing en -provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider) -instantie die in het dialoogvenster is gemaakt.

   * **[!UICONTROL Consumer Secret]**

      (*Vereist*) Voer de ***Consumer(API) Secret*** voor de Twitter App.

   * **[!UICONTROL Create Users]**

      Als deze optie is ingeschakeld, wordt bij het aanmelden met een Twitter-account een AEM gebruikervermelding gemaakt en toegevoegd aan de geselecteerde gebruikersgroep(en). Standaard is ingeschakeld (sterk aanbevolen).

   * **[!UICONTROL Mask User IDs]**

      Laat de selectie uitgeschakeld.

   * **[!UICONTROL Add to User Groups]**

      Selecteer Gebruikersgroep toevoegen om een of meer te kiezen [ledengroepen](https://helpx.adobe.com/experience-manager/6-3/communities/using/users.html) voor de site van de gemeenschap waaraan gebruikers worden toegevoegd.
   >[!NOTE]
   >
   >Groepen kunnen op elk gewenst moment worden toegevoegd of verwijderd. Het lidmaatschap van bestaande gebruikers wordt echter niet beïnvloed. Automatisch lidmaatschap is alleen van toepassing op nieuwe gebruikers die worden gemaakt na deze veldupdate. Voor Plaatsen waar de anonieme gebruikers gehandicapt zijn, voeg gebruikers aan overeenkomstige gemeenschap-lidgroep toe die voor die gesloten communautaire plaats wordt bedoeld.

1. Selecteren **[!UICONTROL SAVE]** en **[!UICONTROL Publish]**.

Het resultaat is een [Adobe Granite OAuth-toepassing en -provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#adobe-granite-oauth-application-and-provider) instantie die niet verder hoeft te worden gewijzigd. Het standaardbereik is de standaardmachtigingen voor Twitter-aanmelding.

### AEM Communities Twitter OAuth Provider {#aem-communities-twitter-oauth-provider}

De AEM Communities-configuratie breidt de [Adobe Granite OAuth-toepassing en -provider](#adobe-granite-oauth-application-and-provider) -instantie. Deze provider moet worden bewerkt om gebruikersupdates toe te staan.

Als bewerken nodig is, wordt op elke AEM-publicatie-instantie het volgende weergegeven:

1. Meld u aan met beheerdersrechten.
1. Ga naar de [Webconsole](../../help/sites-deploying/configuring-osgi.md).

   Bijvoorbeeld http://localhost:4503/system/console/configMgr.

1. Zoek AEM Communities Twitter OAuth Provider.
1. Selecteer het potloodpictogram dat u wilt openen voor bewerking.

   ![twitteroauth_png](assets/twitteroauth_png.png)

   * **[!UICONTROL OAuth Provider ID]**

   (*Vereist*) De standaardwaarde is *soco-twitter*. Niet bewerken.

   * **[!UICONTROL Cloud Service Config]**

      De standaardwaarde is *conf.* Niet bewerken.

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

Zodra een wolkendienst wordt gevormd, kan het voor het relevante Sociale Aanmelden plaatsen voor een communautaire plaats worden toegelaten gebruikend [Gebruikersbeheer](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#USERMANAGEMENT) Subdeelvenster Instellingen tijdens de communitysite [creatie](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#SiteCreation) of [management](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#ModifyingSiteProperties).

1. Kies de context van uw siteconfiguratie waarin u uw inlogconfiguraties voor sociale media hebt opgeslagen.

1. Stel op het tabblad Algemeen cloudconfiguraties in.

   ![beheersites_png](assets/managesites_png.png)

1. Schakel op het tabblad Instellingen de optie **[!UICONTROL Social Logins]** en Opslaan.

   ![usermgmt_png](assets/usermgmt_png.png)

## Sociale aanmelding testen {#test-social-login}

* Zorgen [Adobe Granite OAuth-verificatiehandler](#adobe-granite-oauth-authentication-handler) is ingeschakeld voor alle publicatie-instanties.
* Controleer of de cloudservices zijn gepubliceerd.
* Controleer of de site van de community is gepubliceerd.
* Start de gepubliceerde site in een browser.
Bijvoorbeeld http://localhost:4503/content/sites/engage/en.html
* Selecteer **[!UICONTROL Login In]**.
* Selecteer **[!UICONTROL Sign in with Facebook]** of **[!UICONTROL Sign in with Twitter]**.
* Meld u aan met de juiste gegevens als u zich nog niet hebt aangemeld bij Facebook of Twitter.
* Het kan nodig zijn machtigingen te verlenen afhankelijk van het dialoogvenster dat wordt weergegeven door de Facebook- of Twitter-app.
* De werkbalk boven aan de pagina wordt bijgewerkt met de geslaagde aanmelding.
* Selecteren **[!UICONTROL Profile]**: op de pagina Profiel worden de avatar-afbeelding, voornaam en achternaam van de gebruiker weergegeven. De informatie uit het Facebook- of Twitter-profiel wordt ook weergegeven op basis van de toegestane velden/params.

## Platform OAuth-configuraties AEM {#aem-platform-oauth-configurations}

### Adobe Granite OAuth-verificatiehandler {#adobe-granite-oauth-authentication-handler}

De `Adobe Granite OAuth Authentication Handler` is niet standaard ingeschakeld en ***moet op alle AEM publicatieinstanties zijn ingeschakeld.***

Om de authentificatiemanager bij toe te laten publiceren, open eenvoudig OSGi config en bewaar het:

* Meld u aan met beheerdersrechten.
* Ga naar de [Webconsole](../../help/sites-deploying/configuring-osgi.md).
Bijvoorbeeld http://localhost:4503/system/console/configMgr
* Zoeken `Adobe Granite OAuth Authentication Handler`.
* Selecteer deze optie om de configuratie voor bewerking te openen.
* Selecteer **[!UICONTROL Save]**.

![graniteoauth](assets/graniteoauth.png)

>[!CAUTION]
>
>Let op dat u de verificatiehandler niet verwart met een Facebook- of Twitter-instantie van *Adobe Granite OAuth-toepassing en -provider*.

![graniteoauth1](assets/graniteoauth1.png)

### Adobe Granite OAuth-toepassing en -provider {#adobe-granite-oauth-application-and-provider}

Wanneer een cloudservice voor Facebook of Twitter wordt gemaakt, wordt een instantie van `Adobe Granite OAuth Authentication Handler` wordt gemaakt.

Ga als volgt te werk om de gemaakte instantie voor een Facebook- of Twitter-app te zoeken:

1. Meld u aan met beheerdersrechten.
1. Ga naar de [Webconsole](../../help/sites-deploying/configuring-osgi.md).

   Bijvoorbeeld http://localhost:4503/system/console/configMgr.

1. Zoek Adobe Granite OAuth Application and Provider.

   * Zoek de instantie waar **[!UICONTROL Client ID]** komt overeen met de **[!UICONTROL App ID]**.

      ![graniteoauth2](assets/graniteoauth2.png)

      Met uitzondering van de volgende eigenschappen, verlaat u de andere eigenschappen van de config ongewijzigd:

   * **[!UICONTROL Config ID]**

      (*Vereist*) OAuth-configuratie-id&#39;s moeten uniek zijn. Automatisch gegenereerd wanneer een cloudservice wordt gemaakt.

   * **[!UICONTROL Client ID]**

      (*Vereist*) De toepassings-id die is opgegeven toen de cloudservice werd gemaakt.

   * **[!UICONTROL Client Secret]**

      (*Vereist*) Het toepassingsgeheim dat is opgegeven bij het maken van de cloudservice.

   * **[!UICONTROL Scope]**

      (*Optioneel*) De leverancier kan om aanvullende mogelijkheden vragen voor wat is toegestaan. Het standaardbereik omvat de machtigingen die nodig zijn voor het verstrekken van sociale verificatie- en profielgegevens.

   * **[!UICONTROL Provider ID]**

      (*Vereist*) De provider-id voor AEM Communities wordt ingesteld op het moment dat de cloudservice werd gemaakt. Niet bewerken. Voor Facebook Connect is de waarde *soco-facebook*. Voor Twitter Connect is de waarde *soco-twitter*.

   * **[!UICONTROL Groups]**

      (*Aanbevolen*) Een of meer ledengroepen waaraan gebruikers zijn toegevoegd. Voor AEM Communities wordt aanbevolen de lidgroep voor de community-site op te nemen.

   * **[!UICONTROL Callback URL]**

      (*Optioneel*) URL geconfigureerd met de OAuth-providers om de client terug te sturen. Gebruik een relatieve URL om de host van de oorspronkelijke aanvraag te gebruiken. Laat leeg om de oorspronkelijk aangevraagde URL te gebruiken. Achtervoegsel &quot;/callback/j_security_check&quot; wordt automatisch toegevoegd aan deze URL.
   >[!NOTE]
   >
   >Het domein voor de callback moet bij de leverancier (Facebook of Twitter) worden geregistreerd.

Voor elke configuratie van de authentificatiemanager OAuth, zijn er twee extra configuraties die in de instantie worden gecreeerd:

* Apache Jackrabbit Oak Default Sync Handler (org.apache.jackrabbit.oak.spi.security.authentication.external.impl.DefaultSyncHandler) - Geen bewerkingen vereist in dit venster, maar u kunt de toewijzingen van gebruikersvelden bekijken hoe Facebook-velden worden toegewezen aan een CQ-gebruikersprofielknooppunt. U ziet ook dat &#39;Naam synchronisatiehandler&#39; overeenkomt met de configuratie-id van de configuratie van de OAuth-provider.
* Apache Jackrabbit Oak External Login Module (org.apache.jackrabbit.oak.spi.security.authentication.external.impl.ExternalLoginModuleFactory) - Er zijn geen bewerkingen vereist, maar u kunt zien dat &#39;Naam identiteitsprovider&#39; en &#39;Naam synchronisatiehandler&#39; hetzelfde zijn en verwijzen naar respectievelijk de overeenkomstige OAuth- en sync-handlerconfiguraties.

Zie voor meer informatie [Verificatie met Apache Oak External Login Module](https://jackrabbit.apache.org/oak/docs/security/authentication/externalloginmodule.html).

## OAuth-prestaties van het gebruikerstraject {#oauth-user-traversal-performance}

Voor gemeenschapssites die honderdduizenden gebruikers zien registreren die hun Facebook- of Twitter-aanmelding gebruiken, kunnen de prestaties tijdens het doorlopen van de query die wordt uitgevoerd wanneer een sitebezoeker zijn sociale aanmelding gebruikt, worden verbeterd door de volgende Oak-index toe te voegen.

Als er traversale waarschuwingen worden weergegeven in de logboeken, wordt aangeraden deze index toe te voegen.

Op een instantie van de auteur, aangemeld met beheerdersrechten:

1. Vanuit globale navigatie: selecteren **Gereedschappen, [CRX/DE Lite](../../help/sites-developing/developing-with-crxde-lite.md).**
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


* Voor de **name** `oauthid-123`vervangen *123* met de Facebook ***Toepassings-id*** of Twitter ***Consumentencode (API)*** dat de waarde van de **Client-id** in de [Adobe Granite OAuth-toepassing en -provider](social-login.md#adobe-granite-oauth-application-and-provider) configuratie.

   ![graniteoauth-crxde](assets/graniteoauth-crxde.png)

Raadpleeg voor meer informatie en gereedschappen [Oak-query&#39;s en indexering](../../help/sites-deploying/queries-and-indexing.md).

## Dispatcher Configuration {#dispatcher-configuration}

Zie [Dispatcher configureren voor Gemeenschappen](dispatcher.md).
