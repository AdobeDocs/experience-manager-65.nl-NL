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
source-git-commit: 3296db289b2e2f4ca0d1981597ada6ca1310bd46

---


# Sociale aanmelding met Facebook en Twitter {#social-login-with-facebook-and-twitter}

Met aanmelden via een sociaal netwerk kunt u een bezoeker van een site de optie geven om zich aan te melden bij zijn Facebook- of Twitter-account. Daarom moeten toegestane Facebook- of Twitter-gegevens worden opgenomen in het profiel voor AEM-leden.

![socialloginweretail](assets/socialloginweretail.png)

## Overzicht van sociale aanmelding {#social-login-overview}

Als u sociale aanmelding wilt opnemen, is het *vereist* om aangepaste Facebook- en Twitter-toepassingen te maken.

Hoewel het voorbeeld van de webwinkel voorbeelden biedt voor Facebook- en Twitter-apps en cloudservices, zijn deze niet beschikbaar op een [productiewebsite](../../help/sites-administering/production-ready.md).

De vereiste stappen zijn:

1. [Schakel OAuth-verificatie](#adobe-granite-oauth-authentication-handler) in alle AEM-publicatieexemplaren.

   Als OAuth niet is ingeschakeld, mislukt het aanmelden.

1. **Maak** een sociale app en cloudservice.

   * U kunt als volgt aanmelding bij Facebook ondersteunen:

      * Maak een [Facebook-app](#create-a-facebook-app).
      * Maak en publiceer een [Facebook Connect-cloudservice](#create-a-facebook-connect-cloud-service).
   * Aanmelden met Twitter ondersteunen:

      * Maak een [Twitter-app](#create-a-twitter-app).
      * Maak en publiceer een [Twitter Connect-cloudservice](#create-a-twitter-connect-cloud-service).


1. [**Schakel **sociale aanmelding](#enable-social-login)voor een communitysite in.

Er zijn twee basisbeginselen:

1. **Bereik** (machtigingen) geeft de gegevens aan die de app mag aanvragen.

   * De instanties Facebook en Twitter [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) bevatten standaard de basismachtigingen voor de app in hun bereik.

1. **Velden** (params) geven de eigenlijke aangevraagde gegevens op met URL-parameters.

   * Deze velden zijn opgegeven in [AEM Communities Facebook OAuth Provider](#aem-communities-facebook-oauth-provider) en [AEM Communities Twitter OAuth Provider](#aem-communities-twitter-oauth-provider).
   * De standaardvelden zijn toereikend voor de meeste gevallen waarin het wordt gebruikt, maar kunnen worden gewijzigd.

## Facebook-aanmelding {#facebook-login}

### Facebook API-versie {#facebook-api-version}

De sociale aanmelding en het Facebook-voorbeeld voor webwinkels werden ontwikkeld toen de Facebook Graph API versie 1.0 was.
Vanaf AEM 6.4 GA en AEM 6.3 SP1 werd de sociale aanmelding bijgewerkt om te werken met de nieuwere versie van Facebook Graph API 2.5.

>[!NOTE]
>
>Voor oudere versies AEM, als u met een uitzondering in logboeken wordt geconfronteerd **kan geen teken van dit** halen, verbetering aan recentste GFP voor die versie van AEM.


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


Nadat de toepassing is gemaakt, zoekt u de instellingen voor de **[!UICONTROL toepassings-id]** en de **[!UICONTROL toepassingsgeheim]** . Deze informatie is vereist voor het configureren van de [Facebook-cloudservice](#createafacebookcloudservice).

### Een Facebook Connect Cloud-service maken {#create-a-facebook-connect-cloud-service}

De [Adobe Granite OAuth Application and Provider](https://chl-author.corp.adobe.com/content/help/en/experience-manager/6-4/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider) -instantie, die is geïnstantieerd door een cloudserviceconfiguratie te maken, identificeert de Facebook-toepassing en de lidgroep(en) waaraan de nieuwe gebruikers zijn toegevoegd.

1. Meld u aan bij de AEM-auteur-instantie met beheerdersrechten.
1. Selecteer **[!UICONTROL Gereedschappen]** > **[!UICONTROL Cloudservices]** > **[!UICONTROL Sociale aanmeldingsconfiguratie]** op Facebook vanuit de globale navigatie.
1. Selecteer het pad naar de **[!UICONTROL configuratiecontext]**.

   **[!UICONTROL Contextpad]** moet hetzelfde zijn als het pad voor de cloudconfiguratie dat u hebt geselecteerd bij het maken/bewerken van een communitysite.

1. Controleer of uw contextpad is ingeschakeld om hieronder cloudservices te maken.
1. Ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Algemeen]** > **[!UICONTROL Configuratiebrowser]**. Selecteer de context en bewerk de eigenschappen. Schakel cloudconfiguraties in als deze nog niet zijn ingeschakeld.

   ![config-eigenschappen](assets/config-propertiespng.png)

1. **Configuratie van Facebook-cloudservice maken/bewerken** .

   ![fbsocialloginconfigpng](assets/fbsocialloginconfigpng.png)

   * **[!UICONTROL Titel]** (*vereist*) Voer een weergavetoetitel in die de Facebook-app identificeert. Het wordt aanbevolen dezelfde naam in te voeren als de *weergavenaam* voor de Facebook-app.
   * **[!UICONTROL Toepassings-id/API-sleutel]** (*vereist*) Voer de ***toepassings-id*** voor de Facebook-app in. Dit is de identificatie van de [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider) -instantie die in het dialoogvenster is gemaakt.
   * **[!UICONTROL Toepassingsgeheim]** (*vereist*) Voer het ***App-geheim*** voor de Facebook-app in.
   * **[!UICONTROL Maak gebruikers]** als deze optie is ingeschakeld en u aanmeldt met een Facebook-account, maakt u een AEM-gebruikersvermelding en voegt u deze als lid toe aan de geselecteerde gebruikersgroep(en).  Standaard is ingeschakeld (sterk aanbevolen).
   * **[!UICONTROL Gebruikersnamen]** masker: Laat de selectie uitgeschakeld.
   * **[!UICONTROL E-mail]** bereik: De e-mailid van de gebruiker moet worden opgehaald van Facebook.
   * **[!UICONTROL Voeg toe aan Gebruikersgroepen]** uitgezocht voeg de Groep van de Gebruiker toe om één of meerdere [lidgroepen](https://helpx.adobe.com/experience-manager/6-3/communities/using/users.html) voor de communautaire plaats te kiezen waaraan de gebruikers zullen worden toegevoegd.
   >[!NOTE]
   >
   >Groepen kunnen op elk gewenst moment worden toegevoegd of verwijderd. Maar het lidmaatschap van bestaande gebruikers wordt hierdoor niet beïnvloed. Automatisch lidmaatschap is alleen van toepassing op nieuwe gebruikers die worden gemaakt na deze veldupdate. Voor sites waar anonieme gebruikers zijn uitgeschakeld, kiest u ervoor gebruikers toe te voegen aan de overeenkomende groep met leden van de community die voor die gesloten communitysite is bedoeld.

   * Selecteer **[!UICONTROL OPSLAAN]**.
   * **[!UICONTROL Publiceren]**.




Het resultaat is een [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#adobe-granite-oauth-application-and-provider) -instantie waarvoor geen verdere wijziging nodig is, tenzij er een extra bereik (machtigingen) wordt toegevoegd. Het standaardbereik is de standaardmachtigingen voor aanmelding bij Facebook. Als extra werkingsgebied wordt gewenst, is het noodzakelijk om de configuratie direct uit te geven OSGI. Als er aanpassingen rechtstreeks via systeem/console worden uitgevoerd, moet u de configuraties van de cloudservice niet via de interface van de aanraakinterface bewerken om te voorkomen dat deze worden overschreven.

### AEM Communities Facebook OAuth Provider {#aem-communities-facebook-oauth-provider}

De AEM Communities-provider breidt de [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) -instantie uit.

Voor deze provider moet u het volgende bewerken:

* Gebruikers kunnen bijwerken
* Extra velden [binnen bereik toevoegen](#adobe-granite-oauth-application-and-provider)

   * Niet alle velden die standaard zijn toegestaan, worden standaard opgenomen.

Als bewerken nodig is, publiceert elke AEM-publicatie-instantie:

1. Meld u aan met beheerdersrechten.
1. Navigeer naar de [webconsole](../../help/sites-deploying/configuring-osgi.md). Bijvoorbeeld http://localhost:4503/system/console/configMgr.
1. Zoek AEM Communities Facebook OAuth Provider.
1. Selecteer het potloodpictogram dat u wilt openen voor bewerking.

   ![fboauthprov_png](assets/fboauthprov_png.png)

   * **[!UICONTROL OAuth Provider-id]**

      (*Vereist*) De standaardwaarde is *soco-facebook*. Niet bewerken.

   * **[!UICONTROL Cloud Service Config]**

      De standaardwaarde is `/etc/  cloudservices /  facebookconnect`. Niet bewerken.

   * **[!UICONTROL Configuratie van OAuth Provider-service]**

      De standaardwaarde is `/apps/social/facebookprovider/config/`. Niet bewerken.

   * **[!UICONTROL Labels inschakelen]**

      Bewerken niet.

   * **[!UICONTROL Pad gebruiker]**

      Locatie in de opslagplaats waar gebruikersgegevens worden opgeslagen. Voor een communautaire plaats, om toestemmingen voor leden te verzekeren om elkaars profiel te bekijken, zou de weg het gebrek */huis/gebruikers/gemeenschap* moeten zijn.

   * **[!UICONTROL Velden inschakelen]**

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

   * **[!UICONTROL Gebruiker bijwerken]**

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

1. Nadat de toepassing is gemaakt, zoekt u de API-sleutel **[!UICONTROL (]** Consumer) en het **[!UICONTROL consumentensecret]**. Deze informatie is nodig voor het configureren van de [Twitter-cloudservice](#createatwittercloudservice).

#### Machtigingen {#permissions}

In de sectie met machtigingen voor het beheer van de Twitter-toepassing:

* **[!UICONTROL Toegang]**: Selecteer `Read only`.

   * Andere opties worden niet ondersteund

* **[!UICONTROL Aanvullende machtigingen]**: Kies optioneel `Request email addresses from users`.

   * Als deze optie niet is geselecteerd, bevat het gebruikersprofiel in AEM geen e-mailadres.
   * In de instructies van Twitter staat dat er nog meer stappen moeten worden gezet.

De enige REST-aanvraag die voor aanmelden via een sociaal netwerk is ingediend, is het *[ophalen van account/verifiëren van referenties](https://dev.twitter.com/rest/reference/get/account/verify_credentials)*.

### Een Twitter Connect Cloud-service maken {#create-a-twitter-connect-cloud-service}

De [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) -instantie, geïnstantieerd door een cloudserviceconfiguratie te maken, identificeert de Twitter-toepassing en de lidgroep(en) waaraan de nieuwe gebruikers worden toegevoegd.

1. Meld u aan met beheerdersrechten voor de auteurinstantie.
1. Selecteer **[!UICONTROL Gereedschappen]** > **[!UICONTROL Cloudservices]** > **[!UICONTROL Twitter-aanmeldingsconfiguratie]** voor sociaal profiel in de globale navigatie.
1. Kies de configuratie van het **[!UICONTROL contextpad]** .

   Het pad naar de context moet hetzelfde zijn als het pad naar de cloudconfiguratie dat u hebt geselecteerd bij het maken/bewerken van een communitysite.

1. Controleer of uw contextpad is ingeschakeld om hieronder cloudservices te maken.
1. Ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Algemeen]** > **[!UICONTROL Configuratiebrowser]**. Selecteer de context en bewerk de eigenschappen. Schakel cloudconfiguraties in als deze nog niet zijn ingeschakeld.

   ![twitterconfigproppng](assets/twitterconfigproppng.png)

1. Configuratie van de Twitter-cloudservice maken/bewerken.

   ![twittersocialloginpng](assets/twittersocialloginpng.png)

   * **[!UICONTROL Titel]**

      (*Vereist*) Voer een weergavetoewijzing in die de Twitter-app aangeeft. Het wordt aanbevolen dezelfde naam te gebruiken als de *weergavenaam* voor de Twitter-app.

   * **[!UICONTROL Consumentencode]**

      (*Vereist*) Voer de sleutel **voor de** consument (API) in voor de Twitter-app. Dit is de identificatie van de [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#AdobeGraniteOAuthApplicationandProvider) -instantie die in het dialoogvenster is gemaakt.

   * **[!UICONTROL Consumentengeheim]**

      (*Vereist*) Voer het ***Consumentengeheim*** (API) voor de Twitter-app in.

   * **[!UICONTROL Gebruikers maken]**

      Als deze optie is ingeschakeld, wordt bij het aanmelden met een Twitter-account een AEM-gebruikersvermelding gemaakt en toegevoegd aan de geselecteerde gebruikersgroep(en). Standaard is ingeschakeld (sterk aanbevolen).

   * **[!UICONTROL Gebruikersnamen maskeren]**

      Laat de selectie uitgeschakeld.

   * **[!UICONTROL Toevoegen aan gebruikersgroepen]**

      Selecteer Gebruikersgroep toevoegen om een of meer [lidgroepen](https://helpx.adobe.com/experience-manager/6-3/communities/using/users.html) te kiezen voor de communitysite waaraan gebruikers worden toegevoegd.
   >[!NOTE]
   >
   >Groepen kunnen op elk gewenst moment worden toegevoegd of verwijderd. Het lidmaatschap van bestaande gebruikers wordt echter niet beïnvloed. Automatisch lidmaatschap is alleen van toepassing op nieuwe gebruikers die worden gemaakt na deze veldupdate. Voor Plaatsen waar de anonieme gebruikers gehandicapt zijn, voeg gebruikers aan overeenkomstige gemeenschap-lidgroep toe die voor die gesloten communautaire plaats wordt bedoeld.

1. Selecteer **[!UICONTROL OPSLAAN]** en **[!UICONTROL Publiceren]**.

Het resultaat is een [Adobe Granite OAuth Application and Provider](https://helpx.adobe.com/experience-manager/6-3/communities/using/social-login.html#adobe-granite-oauth-application-and-provider) -instantie die niet verder hoeft te worden gewijzigd. Het standaardbereik is de standaardmachtigingen voor Twitter-aanmelding.

### AEM Communities Twitter OAuth Provider {#aem-communities-twitter-oauth-provider}

De configuratie van AEM Communities breidt de [Adobe Granite OAuth Application and Provider](#adobe-granite-oauth-application-and-provider) -instantie uit. Deze provider moet worden bewerkt om gebruikersupdates toe te staan.

Als bewerken nodig is, publiceert elke AEM-publicatie-instantie:

1. Meld u aan met beheerdersrechten.
1. Navigeer naar de [webconsole](../../help/sites-deploying/configuring-osgi.md).

   Bijvoorbeeld http://localhost:4503/system/console/configMgr.

1. Zoek op Twitter OAuth Provider van AEM-gemeenschappen.
1. Selecteer het potloodpictogram dat u wilt openen voor bewerking.

   ![twitteroauth_png](assets/twitteroauth_png.png)

   * **[!UICONTROL OAuth Provider-id]**
   (*Vereist*) De standaardwaarde is *soco-twitter*. Niet bewerken.

   * **[!UICONTROL Cloud Service Config]**

      The default value is *conf.* Niet bewerken.

   * **[!UICONTROL Configuratie van OAuth Provider-service]**

      De standaardwaarde is `/apps/social/twitterprovider/config/`. Niet bewerken.

   * **[!UICONTROL Pad gebruiker]**

      Locatie in de opslagplaats waar gebruikersgegevens worden opgeslagen. Voor een communautaire plaats, om toestemmingen voor leden te verzekeren om elkaars profiel te bekijken, zou de weg het gebrek moeten zijn `/home/users/community`.

   * **[!UICONTROL Params]** inschakelen niet bewerken
   * **[!UICONTROL URL-parameters]** worden niet bewerkt
   * **[!UICONTROL Gebruiker bijwerken]**

      Als deze optie is ingeschakeld, worden de gebruikersgegevens in de dataopslag bij elke aanmelding vernieuwd om rekening te houden met profielwijzigingen of aanvullende aangevraagde gegevens. De standaardinstelling is uitgeschakeld.


#### Volgende stappen {#next-steps-1}

De volgende stappen zijn hetzelfde voor zowel Facebook als Twitter:

* [De configuraties van de cloudservice publiceren](#publishcloudservices)
* [Inschakelen voor een communitysite](#enable-social-login)

## Sociale aanmelding inschakelen {#enable-social-login}

### AEM Community Sites Console {#aem-communities-sites-console}

Zodra een wolkendienst wordt gevormd, kan het voor het relevante Sociale Aanmelden plaatsen voor een communautaire plaats worden toegelaten gebruikend het subpanel van de Montages van het Beheer van de [Gebruiker](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#USERMANAGEMENT) tijdens de [verwezenlijking](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#SiteCreation) of het [beheer](https://helpx.adobe.com/experience-manager/6-3/communities/using/sites-console.html#ModifyingSiteProperties)van de communautaire plaats.

1. Kies de context van uw siteconfiguratie waarin u uw inlogconfiguraties voor sociale media hebt opgeslagen.

1. Stel op het tabblad Algemeen cloudconfiguraties in.

   ![beheersites_png](assets/managesites_png.png)

1. Schakel op het tabblad Instellingen de optie **[!UICONTROL Sociale aanmeldingen]** en Opslaan in.

   ![usermgmt_png](assets/usermgmt_png.png)

## Sociale aanmelding testen {#test-social-login}

* Controleer of [Adobe Granite OAuth Authentication Handler](#adobe-granite-oauth-authentication-handler) is ingeschakeld voor alle publicatieinstanties.
* Controleer of de cloudservices zijn gepubliceerd.
* Controleer of de site van de community is gepubliceerd.
* Start de gepubliceerde site in een browser.
Bijvoorbeeld http://localhost:4503/content/sites/engage/en.html
* Selecteer **[!UICONTROL Aanmelden]**.
* Selecteer **[!UICONTROL Aanmelden bij Facebook]** of **[!UICONTROL Aanmelden bij Twitter]**.
* Meld u aan met de juiste gegevens als u zich nog niet hebt aangemeld bij Facebook of Twitter.
* Het kan nodig zijn machtigingen te verlenen afhankelijk van het dialoogvenster dat wordt weergegeven door de app Facebook of Twitter.
* De werkbalk boven aan de pagina wordt bijgewerkt met de geslaagde aanmelding.
* Selecteer **[!UICONTROL profiel]**: op de pagina Profiel worden de avatar-afbeelding, voornaam en achternaam van de gebruiker weergegeven. De informatie uit het Facebook- of Twitter-profiel wordt ook weergegeven op basis van de toegestane velden/params.

## OAuth-configuraties voor AEM-platform {#aem-platform-oauth-configurations}

### Adobe Granite OAuth-verificatiehandler {#adobe-granite-oauth-authentication-handler}

De optie `Adobe Granite OAuth Authentication Handler` is niet standaard ingeschakeld en ***moet op alle AEM-publicatie-instanties zijn ingeschakeld.***

Om de authentificatiemanager bij toe te laten publiceren, open eenvoudig OSGi config en bewaar het:

* Meld u aan met beheerdersrechten.
* Navigeer naar de [webconsole](../../help/sites-deploying/configuring-osgi.md).
Bijvoorbeeld http://localhost:4503/system/console/configMgr
* Zoeken `Adobe Granite OAuth Authentication Handler`.
* Selecteer deze optie om de configuratie voor bewerking te openen.
* Selecteer **[!UICONTROL Opslaan]**.

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

   * Zoek de instantie waarbij de **[!UICONTROL client-id]** overeenkomt met de **[!UICONTROL toepassings-id]**.

      ![chlimage_1-491](assets/chlimage_1-491.png)

      Met uitzondering van de volgende eigenschappen, verlaat u de andere eigenschappen van de config ongewijzigd:

   * **[!UICONTROL Configuratie-id]**

      (*Vereist*) OAuth configuratie IDs moet uniek zijn. Automatisch gegenereerd wanneer een cloudservice wordt gemaakt.

   * **[!UICONTROL Client-id]**

      (*Vereist*) De toepassings-id die is opgegeven bij het maken van de cloudservice.

   * **[!UICONTROL Clientgeheim]**

      (*Vereist*) Het toepassingsgeheim dat is opgegeven bij het maken van de cloudservice.

   * **[!UICONTROL Scope]**

      (*Optioneel*) De leverancier kan om aanvullende mogelijkheden vragen. Het standaardbereik omvat de machtigingen die nodig zijn voor het verstrekken van sociale verificatie- en profielgegevens.

   * **[!UICONTROL Provider-id]**

      (*Vereist*) De provider-id voor AEM-gemeenschappen wordt ingesteld op het moment dat de cloudservice werd gemaakt. Niet bewerken. Voor Facebook Connect is de waarde *soco-facebook*. Voor Twitter Connect is de waarde *soco-twitter*.

   * **[!UICONTROL Groepen]**

      (*Aanbevolen*) Een of meer lidgroepen waaraan gemaakte gebruikers zijn toegevoegd. Voor AEM-gemeenschappen wordt aanbevolen de ledengroep voor de community-site op te nemen.

   * **[!UICONTROL URL voor terugbellen]**

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

1. Vanuit globale navigatie: Selecteer **Hulpmiddelen,[CRX/DE Lite](../../help/sites-developing/developing-with-crxde-lite.md).**
1. Creeer een index genoemd ntBaseLucene-oauth van een exemplaar van ntBaseLucene:

   * Onder knooppunt `/oak:index`
   * Knooppunt selecteren `ntBaseLucene`
   * Kopie **[!UICONTROL selecteren]**
   * Selecteer `/oak:index`
   * Plakken **[!UICONTROL selecteren]**
   * Naam van kopie van ntBaseLucene wijzigen in `ntBaseLucene-oauth`

1. Wijzig de eigenschappen van node ntBaseLucene-oauth:

   * **[!UICONTROL indexPath]**: `/oak:index/ntBaseLucene-oauth`
   * **[!UICONTROL naam]**: `oauthid-123****`
   * **[!UICONTROL redex]**: `true`
   * **[!UICONTROL redexCount]**: `1`

1. Onder node/oak:index/ntBaseLucene-oauth/indexRules/nt:base/properties:

   * Verwijder alle onderliggende knooppunten, behalve cqTags.
   * Naam van cqTags wijzigen in `oauthid-123****`
   * Eigenschappen van knooppunt wijzigen `oauthid-123****`

      * **[!UICONTROL naam]**: `oauthid-123****`
   * Selecteer **[!UICONTROL Alles]** opslaan.


* Voor de **naam** vervangt u `oauthid-123`123 *door de Facebook* App ID ***of de Twitter*** Consumer (API)-sleutel ***die de waarde van de*** **** [](social-login.md#adobe-granite-oauth-application-and-provider) client-id in de toepassing Adobe Granite OAuth en de configuratie Provideris.

   ![chlimage_1-492](assets/chlimage_1-492.png)

Voor extra informatie en hulpmiddelen, verwijs naar de Vragen van het [Eik en het Indexeren](../../help/sites-deploying/queries-and-indexing.md).

## Dispatcher Configuration {#dispatcher-configuration}

Zie [Dispatcher configureren voor Gemeenschappen](dispatcher.md).
