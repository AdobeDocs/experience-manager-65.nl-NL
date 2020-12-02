---
title: Auteur van een nieuwe communautaire site voor activering
seo-title: Auteur van een nieuwe communautaire site voor activering
description: Een communitysite maken voor activering
seo-description: Een communitysite maken voor activering
uuid: a75fa566-a570-45fd-aabc-23651ef819cc
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: b9333558-6af9-46b2-9f03-3722645c69a6
docset: aem65
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '1724'
ht-degree: 1%

---


# Auteur een Nieuwe Communautaire Plaats voor Enablement {#author-a-new-community-site-for-enablement}

## Community-site maken {#create-community-site}

[Bij het ](/help/communities/sites-console.md) maken van een Community Site wordt een wizard gebruikt die u begeleidt bij het maken van een communitysite. Het is mogelijk door te gaan naar de stap `Next` of `Back` naar de vorige stap voordat u de site in de laatste stap toewijst.

Ga als volgt te werk om een nieuwe communitysite te maken:

De [auteurinstantie](https://localhost:4502/) gebruiken

* Meld u aan met beheerdersrechten en navigeer naar **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.

* Selecteer **Maken**.

### Stap 1: Sitesjabloon {#step-site-template}

![Sjabloon van de instellingensite](assets/enablement-site-template.png)

Voer in de stap **Sitesjabloon** een titel, beschrijving, naam voor de URL in en selecteer bijvoorbeeld een sjabloon voor een communitysite:

* **Titel** van communautaire site:  `Enablement Tutorial`.

* **Beschrijving** van communautaire site:  `A site for enabling the community to learn.`

* **Hoofdmap** van gemeenschapssite: (leeg laten voor standaardhoofdmap  `/content/sites`)

* **Cloudconfiguraties**: (leeg laten als er geen cloudconfiguraties zijn opgegeven) het pad naar de opgegeven cloudconfiguraties bieden.
* **Basistaal** van gemeenschapssite: (ongewijzigd laten voor één taal: (Engels) gebruik de vervolgkeuzelijst om een  *of* meer basistalen te kiezen uit de beschikbare talen: Duits, Italiaans, Frans, Japans, Spaans, Portugees (Brazilië), Chinees (Traditioneel) en Chinees (Vereenvoudigd). Er wordt één communitysite gemaakt voor elke toegevoegde taal en deze wordt in dezelfde sitemap gebruikt volgens de best practices die worden beschreven in [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md). De hoofdpagina van elke site bevat een onderliggende pagina met de taalcode van een van de geselecteerde talen, zoals &#39;en&#39; voor Engels of &#39;fr&#39; voor Frans.

* **Naam** van communautaire site:  `enable`

   * De eerste URL wordt onder de naam van de communautaire site weergegeven
   * Voeg voor een geldige URL een basistaalcode + &quot;.html&quot; toe
      *Bijvoorbeeld* https://localhost:4502/content/sites/  `enable/en.html`

* **Sjabloon** verwijzingssite: naar beneden halen om te kiezen  `Reference Structured Learning Site Template`

Selecteer **Volgende**.

### Stap 2: Ontwerp {#step-design}

De stap Ontwerp wordt in twee secties weergegeven voor het selecteren van het thema en de brandbanner:

#### THEMA VAN COMMUNAUTAIRE SITE {#community-site-theme}

Selecteer de gewenste stijl die u op de sjabloon wilt toepassen. Als deze optie is geselecteerd, wordt het thema bedekt met een vinkje.

#### COMMUNAUTAIRE SITEBRANDING {#community-site-branding}

(Optioneel) Upload een bannerafbeelding voor weergave op de sitepagina&#39;s. De banner is vastgezet aan de linkerrand van browser, tussen de communautaire plaatsheader en menu (navigatiekoppelingen). De bannerhoogte wordt bijgesneden tot 120 pixels. Er wordt geen grootte van de banner aangepast aan de breedte van de browser en de hoogte van 120 pixels.

![chlimage_1-449](assets/chlimage_1-449.png)

![chlimage_1](assets/chlimage_1.jpeg)

Selecteer **Volgende**.

### Stap 3: Instellingen {#step-settings}

Voor de stap van Montages, alvorens `Next` te selecteren, merk er zeven secties zijn die toegang tot configuraties verlenen die gebruikersbeheer, het etiketteren, rollen, moderatie, analyse, vertaling, en enablement impliceren.

#### GEBRUIKERSBEHEER {#user-management}

Aanbevolen wordt [enablement Communities](/help/communities/overview.md#enablement-community) privé te maken.

Een gemeenschapssite is persoonlijk wanneer anonieme sitebezoekers geen toegang krijgen, zich mogelijk niet zelf registreren en geen gebruik maken van sociale aanmelding.

Zorg ervoor dat de meeste selectievakjes zijn uitgeschakeld voor [Gebruikersbeheer](/help/communities/sites-console.md#user-management):

* Sta bezoekers van de site NIET toe zich zelf te registreren.
* Sta geen anonieme sitebezoekers toe om de site te bekijken.
* Optioneel of berichten al dan niet worden toegestaan onder leden van de gemeenschap.
* Meld u NIET aan bij Facebook.
* Meld u NIET aan bij Twitter.

![gebruikersbeheer](assets/user-mgmt.png)

#### TAGS {#tagging}

De tags die kunnen worden toegepast op community-inhoud, worden beheerd door AEM naamruimten te selecteren die eerder zijn gedefinieerd via de [Tagingconsole](/help/sites-administering/tags.md#tagging-console) (zoals de [Zelfstudie-naamruimte](/help/communities/enablement-setup.md#create-tutorial-tags)).

Als u bovendien Tagnaamruimten selecteert voor de communitysite, beperkt u de selectie die wordt weergegeven bij het definiëren van catalogi en machtigingsbronnen. Zie [Tags toewijzen Bronnen](/help/communities/tag-resources.md) voor belangrijke informatie.

Het zoeken naar naamruimten is eenvoudig met &#39;type-ahead&#39;-zoekopdracht. Bijvoorbeeld,

* Type `tut`
* Selecteer `Tutorial`

![enablement-tagging](assets/enablement-tagging.png)

### ROLLEN {#roles}

[De communautaire ](/help/communities/users.md) leden worden toegewezen door de montages in de sectie van Rollen.

Als u een lid van de gemeenschap (of groep leden) de site wilt laten ervaren als gemeenschapsbeheerder, gebruikt u de typecontrole en selecteert u de naam van het lid of de groep in de keuzelijst.

Bijvoorbeeld,

* Tekst `q`
* Selecteer [Quinn Harper](/help/communities/enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Met de tunnelservice ](/help/communities/deploy-communities.md#tunnel-service-on-author) kunt u leden en groepen selecteren die alleen in de publicatieomgeving aanwezig zijn.

![machtigingsrollen](assets/site-admin.png)

#### MODERING {#moderation}

Accepteer de standaard algemene instellingen voor [het modereren](/help/communities/sites-console.md#moderation) door de gebruiker gegenereerde inhoud (UGC).

![chlimage_1-452](assets/chlimage_1-452.png)

#### ANALYSE {#analytics}

Selecteer in het keuzemenu het cloudserviceframework Analytics dat voor deze communitysite is geconfigureerd.

De selectie in het schermafbeelding, `Communities`, is het kadervoorbeeld van de [configuratiedocumentatie.](/help/communities/analytics.md#aem-analytics-framework-configuration)

![chlimage_1-454](assets/chlimage_1-454.png)

#### TRANSLATION {#translation}

Met de [Vertaalinstellingen](/help/communities/sites-console.md#translation) wordt aangegeven of UGC kan worden vertaald en in welke taal, als dat het geval is.

* Schakel **Machinevertaling toestaan**
* De standaardinstellingen gebruiken

![chlimage_1-456](assets/chlimage_1-456.png)

#### INSCHAKELEN {#enablement}

Voor een machtigingsgemeenschap is het noodzakelijk om één of meerdere Communautaire Beheerders van Enablement te identificeren.

* **Beheerders**
 inschakelen (vereist) Leden van de 
`Community Enablement Managers` Deze groep is beschikbaar om te worden geselecteerd voor het beheer van deze communitysite.

   * Tekst `s`
   * Selecteer `Sirius Nilson`

* **Org-id**
 van Marketing Cloud (optioneel) De id voor een Adobe Analytics-account die nodig is wanneer  [Video Heartbone-](/help/communities/analytics.md#video-heartbeat-analytics) analysemogelijkheden worden opgenomen in de actiemelding.

![chlimage_1-457](assets/chlimage_1-457.png)

Selecteer **Volgende**.

### Stap 4: Community-site maken {#step-create-community-site}

Selecteer **Maken.**

![chlimage_1-458](assets/chlimage_1-458.png)

Wanneer het proces is voltooid, wordt de map voor de nieuwe site weergegeven in de console Communities > Sites.

![vereffening](assets/enablementsitecreated.png)

### De nieuwe communautaire site publiceren {#publish-the-new-community-site}

De gecreeerde plaats zou van de Gemeenschappen - de console van Plaatsen moeten worden beheerd, de zelfde console van waar de nieuwe plaatsen kunnen worden gecreeerd.

Nadat u de map van de communitysite hebt geselecteerd, houdt u de muisaanwijzer boven het sitepictogram, zodat er vier actiepictogrammen worden weergegeven:

![locatiehandelingen](assets/siteactionicons.png)

Als u het pictogram Ovalen selecteert (pictogram Meer handelingen), worden de opties Site exporteren en Site verwijderen weergegeven.

![nieuwe sites](assets/siteactionsnew.png)

Van links naar rechts zijn ze:

* **Site openen**

   Selecteer het potloodpictogram om de gemeenschapssite te openen in de modus Bewerken door auteur om paginacomponenten toe te voegen en/of te configureren.

* **Site bewerken**

   Selecteer het eigenschappenpictogram om de communitysite te openen voor wijziging van eigenschappen, zoals de titel, of om het thema te wijzigen.

* **Site publiceren**

   Selecteer het wereldpictogram om de communitysite te publiceren (standaard op localhost:4503).

* **Site exporteren**

   Selecteer het exportpictogram om een pakket te maken van de communitysite die zowel in [pakketbeheer](/help/sites-administering/package-manager.md) is opgeslagen als is gedownload.
UGC is niet opgenomen in het sitepakket.

* **Site verwijderen**

   Als u de communitysite wilt verwijderen, selecteert u het pictogram Site verwijderen dat verschijnt wanneer u de muisaanwijzer op de site in de Community Site Console plaatst. Met deze actie verwijdert u alle items die aan de site zijn gekoppeld, zoals UGC, gebruikersgroepen, elementen en databaserecords.

   ![inschakelen](assets/enablesiteactions.png)

#### Publiceren {#select-publish} selecteren

Selecteer het pictogram van de wereld om de communitysite te publiceren.

![chlimage_1-465](assets/chlimage_1-465.png)

Er wordt een indicatie gegeven dat de site is gepubliceerd.

![chlimage_1-466](assets/chlimage_1-466.png)

## Community-gebruikers en -gebruikersgroepen {#community-users-user-groups}

### Nieuwe gebruikersgroepen van de Gemeenschap {#notice-new-community-user-groups} melden

Samen met de nieuwe communautaire plaats, worden de nieuwe gebruikersgroepen gecreeerd die de aangewezen toestemmingen hebben die voor diverse administratieve functies worden geplaatst. Voor details, bezoek [Gebruikersgroepen voor Communautaire Plaatsen](/help/communities/users.md#usergroupsforcommunitysites).

Voor deze nieuwe communautaire plaats, gezien de plaatsnaam &quot;laat&quot;in Stap 1 toe, kunnen de nieuwe gebruikersgroepen die in het publiceren milieu bestaan van [de leden &amp; van Groepen van Gemeenschappen console](/help/communities/members.md#groups-console) worden gezien:

![community_usergroup](assets/community_usergroup.png)

### Leden toewijzen aan de groep leden {#assign-members-to-community-enable-members-group} voor Community Enable

Op auteur, met de toegelaten tunneldienst, is het mogelijk om [gebruikers toe te wijzen die tijdens Begeleidende Opstelling](/help/communities/enablement-setup.md#publishcreateenablementmembers) aan de groep van Leden Gemeenschap voor de pas gecreëerde communautaire plaats worden gecreeerd.

Met behulp van de Community Group-console kunnen leden afzonderlijk worden toegevoegd of via lidmaatschap aan een groep worden toegevoegd.

In dit voorbeeld wordt de groep `Community Ski Class` toegevoegd als lid van de groep `Community Enable Members` en als lid `Quinn Harper`.

* Navigeer naar **Communities, groups** console
* Selecteer *Community Enable Leden* groep
* Typ &#39;ski&#39; in het zoekvak **Leden toevoegen aan groep**
* Selecteer *Community Ski Class* (groep studenten)
* &#39;quinn&#39; invoeren in het zoekvak
* Selecteer *Quinn Harper* (resablement resource contact inschakelen)

* Selecteer **Opslaan**

![chlimage_1-418](assets/chlimage_1-418.png)

## Configuraties bij publiceren {#configurations-on-publish}

`https://localhost:4503/content/sites/enable/en.html {#http-localhost-content-sites-enable-en-html}`

![enablement-login](assets/enablement-login.png)

### Configureren voor verificatiefout {#configure-for-authentication-error}

Nadat een site is geconfigureerd en geduwd op publiceren, [configureert u de aanmeldingstoewijzing](/help/communities/sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) op de publicatieinstantie. Het voordeel is dat als de aanmeldingsgegevens niet correct zijn ingevoerd, de verificatiefout de aanmeldingspagina van de communautaire site opnieuw weergeeft met een foutbericht.

Een `Login Page Mapping` toevoegen als:

* `/content/sites/enable/en/signin:/content/sites/enable/en`

### (Optioneel) Wijzig de standaardstartpagina {#optional-change-the-default-home-page}

Als u met de publicatiesite werkt voor demonstratiedoeleinden, is het handig om de standaardstartpagina te wijzigen in de nieuwe site.

Hiervoor moet u [CRX|DE](https://localhost:4503/crx/de) Lite gebruiken om de [bronnentoewijzing](/help/sites-deploying/resource-mapping.md)-tabel bij publicatie te bewerken.

Aan de slag:

1. Bij publiceren, heb toegang tot CRXDE en login met beheerdervoorrechten

   * Blader bijvoorbeeld naar [https://localhost:4503/crx/de](https://localhost:4503/crx/de) en meld u aan met `admin/admin`

1. Vouw `/etc/map` in de projectbrowser uit
1. Selecteer de `http` knoop

   * Selecteer **Knooppunt maken**

      * **** Namelocalhost.4503

         (gebruik &#39;:&#39; voor *not*)

      * **** [lettertypen:toewijzen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Met nieuw aangemaakt `localhost.4503`-knooppunt geselecteerd

   * Eigenschap toevoegen

      * **** naamgeving:overeenkomst
      * **** TypeString
      * **** Valuelocalhost.4503/$

   (moet eindigen met &#39;$&#39; teken)

   * Eigenschap toevoegen

      * **** naamgeving:internalRedirect
      * **** TypeString
      * **Waarde** /content/sites/enable/en.html


1. Selecteer **Alles opslaan**
1. (Optioneel) De browsergeschiedenis verwijderen
1. Bladeren naar https://localhost:4503/

   * Ga naar https://localhost:4503/content/sites/enable/en.html

>[!NOTE]
>
>Als u deze optie wilt uitschakelen, voegt u de eigenschapswaarde `sling:match` gewoon toe met een &#39;x&#39; - `xlocalhost.4503/$` - en **Alles opslaan**.

![chlimage_1-364](assets/chlimage_1-364.png)

#### Problemen oplossen: Fout bij opslaan van kaart {#troubleshooting-error-saving-map}

Als u wijzigingen niet kunt opslaan, moet u ervoor zorgen dat de knooppuntnaam `localhost.4503` is, met een &#39;punt&#39;-scheidingsteken en niet `localhost:4503` met een &#39;dubbele punt&#39;-scheidingsteken, omdat `localhost` geen geldig naamruimtevoorvoegsel is.

![chlimage_1-365](assets/chlimage_1-365.png)

#### Problemen oplossen: Kan {#troubleshooting-fail-to-redirect} niet omleiden

De tekenreeks &#39;**$**&#39; aan het einde van de reguliere expressie `sling:match` is van cruciaal belang, zodat alleen exact `https://localhost:4503/` wordt toegewezen. Anders wordt de omleidingswaarde toegevoegd aan elk pad dat mogelijk bestaat na de server:poort in de URL. Wanneer AEM probeert om naar de aanmeldingspagina om te leiden, mislukt dit.

## Het wijzigen van de Communautaire Plaats {#modifying-the-community-site}

Nadat de site voor het eerst is gemaakt, kunnen auteurs het [pictogram Open Site](/help/communities/sites-console.md#authoring-site-content) gebruiken om standaard AEM ontwerpactiviteiten uit te voeren.

Daarnaast kunnen beheerders het [Sitepictogram bewerken](/help/communities/sites-console.md#modifying-site-properties) gebruiken om eigenschappen van de site, zoals de titel, te wijzigen.

Na om het even welke wijziging, herinner aan **sparen** en re-**Publish** de plaats.

>[!NOTE]
>
>Als u niet bekend bent met AEM, bekijkt u de documentatie over [basisverwerking](/help/sites-authoring/basic-handling.md) en een [handleiding voor het schrijven van pagina&#39;s](/help/sites-authoring/qg-page-authoring.md).

### Een catalogus {#add-a-catalog} toevoegen

Het sjabloon voor de communitysite dat voor deze communitysite is gekozen, moet de catalogusfunctie bevatten.

Als dat niet het geval is, kan de catalogusfunctie eenvoudig worden toegevoegd. Hierdoor kunnen andere leden van de gemeenschap die niet zijn toegewezen aan bronnen voor activering of een leerpad, bronnen voor activering selecteren in een catalogus.

Als de sitestructuur al de catalogusfunctie bevat, kan de titel worden gewijzigd.

Als u de structuur van de site wilt wijzigen, navigeert u naar **[!UICONTROL Communities]** > **[!UICONTROL Sites]**-console, opent u de map `enable` en selecteert u het pictogram **Site bewerken** om toegang te krijgen tot de eigenschappen van `Enablement Tutorial`.

Selecteer het deelvenster STRUCTUUR om een catalogus toe te voegen of een bestaande catalogus te wijzigen:

* **Titel**:  `Ski Catalog`

* **URL**:  `catalog`

* **Alle naamruimten** selecteren: blijven staan.

* Selecteer **Opslaan**.

![chlimage_1-299](assets/chlimage_1-299.png)

Gebruik het pictogram Positie om de functie Catalog naar de tweede positie te verplaatsen, na Toewijzingen.

![chlimage_1-300](assets/chlimage_1-300.png)

Selecteer **Opslaan** in de rechterbovenhoek om de wijzigingen in de communitysite op te slaan.

Vervolgens kunt u de site opnieuw **publiceren**.

