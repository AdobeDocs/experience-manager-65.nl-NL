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
source-git-commit: 99fb808013da18ed028d59c43deab5e815169e26
workflow-type: tm+mt
source-wordcount: '1724'
ht-degree: 1%

---


# Auteur van een nieuwe communautaire site voor activering {#author-a-new-community-site-for-enablement}

## Community-site maken {#create-community-site}

[Bij het maken](/help/communities/sites-console.md) van een Community Site wordt een wizard gebruikt die u door de stappen begeleidt bij het maken van een communitysite. U kunt verder gaan naar de `Next` stap of `Back` naar de vorige stap voordat u de site in de laatste stap toewijst.

Ga als volgt te werk om een nieuwe communitysite te maken:

De [instantie van de auteur gebruiken](https://localhost:4502/)

* Meld u aan met beheerdersrechten en navigeer naar **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.

* Selecteer **Maken**.

### Stap 1: Sitesjabloon {#step-site-template}

![Sjabloon van de instellingensite](assets/enablement-site-template.png)

Voor de stap van het Malplaatje **van de** Plaats, ga een titel, een beschrijving, de naam voor URL in, en selecteer een malplaatje van de communautaire plaats, bijvoorbeeld:

* **Titel** van communautaire site: `Enablement Tutorial`.

* **Beschrijving** van communautaire site: `A site for enabling the community to learn.`

* **Hoofdmap** van gemeenschapssite: (leeg laten voor standaardhoofdmap `/content/sites`)

* **Cloudconfiguraties**: (leeg laten als er geen cloudconfiguraties zijn opgegeven) het pad naar de opgegeven cloudconfiguraties bieden.
* **Basistaal** van gemeenschapssite: (ongewijzigd laten voor één taal: (Engels) gebruik het drop-down om één *of meerdere* basistalen van de beschikbare talen - Duits, Italiaans, Frans, Japans, Spaans, Portugees (Brazilië), Chinees (Traditioneel), en Chinees (Vereenvoudigd) te kiezen. Er wordt één communitysite gemaakt voor elke toegevoegde taal en deze wordt in dezelfde sitemap gebruikt volgens de beste praktijken die worden beschreven in Inhoud [vertalen voor Meerdere sites](/help/sites-administering/translation.md). De hoofdpagina van elke site bevat een onderliggende pagina met de taalcode van een van de geselecteerde talen, zoals &#39;en&#39; voor Engels of &#39;fr&#39; voor Frans.

* **Naam** van communautaire site: `enable`

   * De eerste URL wordt onder de naam van de communautaire site weergegeven
   * Voeg voor een geldige URL een basistaalcode + &quot;.html&quot; toe
      *Bijvoorbeeld* https://localhost:4502/content/sites/ `enable/en.html`

* **Sjabloon** verwijzingssite: naar beneden halen om te kiezen `Reference Structured Learning Site Template`

Selecteer **Volgende**.

### Stap 2: Ontwerp {#step-design}

De stap Ontwerp wordt in twee secties weergegeven voor het selecteren van het thema en de brandbanner:

#### COMMUNAUTAIR SITE-THEMA {#community-site-theme}

Selecteer de gewenste stijl die u op de sjabloon wilt toepassen. Als deze optie is geselecteerd, wordt het thema bedekt met een vinkje.

#### COMMUNAUTAIRE SITOBRANDING {#community-site-branding}

(Optioneel) Upload een bannerafbeelding voor weergave op de sitepagina&#39;s. De banner is vastgezet aan de linkerrand van browser, tussen de communautaire plaatsheader en menu (navigatiekoppelingen). De bannerhoogte wordt bijgesneden tot 120 pixels. Er wordt geen grootte van de banner aangepast aan de breedte van de browser en de hoogte van 120 pixels.

![chlimage_1-449](assets/chlimage_1-449.png)

![chlimage_1](assets/chlimage_1.jpeg)

Selecteer **Volgende**.

### Stap 3: Instellingen {#step-settings}

Voor de stap van Montages, alvorens te selecteren `Next`, merk er zeven secties zijn die toegang tot configuraties verlenen die gebruikersbeheer, het etiketteren, rollen, moderatie, analyses, vertaling, en enablement impliceren.

#### GEBRUIKERSBEHEER {#user-management}

Aanbevolen wordt [gemeenschappen](/help/communities/overview.md#enablement-community) van arbeidskrachten privé te laten zijn.

Een gemeenschapssite is persoonlijk wanneer anonieme sitebezoekers geen toegang krijgen, zich mogelijk niet zelf registreren en geen gebruik maken van sociale aanmelding.

Controleer of de meeste selectievakjes zijn uitgeschakeld voor [Gebruikersbeheer](/help/communities/sites-console.md#user-management) :

* Sta bezoekers van de site NIET toe zich zelf te registreren.
* Sta geen anonieme sitebezoekers toe om de site te bekijken.
* Optioneel of berichten al dan niet worden toegestaan onder leden van de gemeenschap.
* Meld u NIET aan bij Facebook.
* Meld u NIET aan bij Twitter.

![gebruikersbeheer](assets/user-mgmt.png)

#### TAGGING {#tagging}

De tags die kunnen worden toegepast op community-inhoud, worden beheerd door AEM naamruimten te selecteren die eerder zijn gedefinieerd via de [Tagingconsole](/help/sites-administering/tags.md#tagging-console) (zoals de naamruimte [van de](/help/communities/enablement-setup.md#create-tutorial-tags)zelfstudie).

Als u bovendien Tagnaamruimten selecteert voor de communitysite, beperkt u de selectie die wordt weergegeven bij het definiëren van catalogi en machtigingsbronnen. Zie [Tags toewijzen Hulpbronnen](/help/communities/tag-resources.md) voor belangrijke informatie.

Het zoeken naar naamruimten is eenvoudig met &#39;type-ahead&#39;-zoekopdracht. Bijvoorbeeld,

* Type `tut`
* Selecteer `Tutorial`

![enablement-tagging](assets/enablement-tagging.png)

### ROLES {#roles}

[De rollen](/help/communities/users.md) van het communautaire lid worden toegewezen door de montages in de sectie van Rollen.

Als u een lid van de gemeenschap (of groep leden) de site wilt laten ervaren als gemeenschapsbeheerder, gebruikt u de typecontrole en selecteert u de naam van het lid of de groep in de keuzelijst.

Bijvoorbeeld,

* Type `q`
* Quinn Harper [selecteren](/help/communities/enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[De dienst](/help/communities/deploy-communities.md#tunnel-service-on-author) van de tunnel staat selectie van leden en groepen toe die slechts in publicatiemilieu bestaan.


![machtigingsrollen](assets/site-admin.png)

#### MODERING {#moderation}

Accepteer de standaard algemene instellingen voor het [modereren](/help/communities/sites-console.md#moderation) van door de gebruiker gegenereerde inhoud (UGC).

![chlimage_1-452](assets/chlimage_1-452.png)

#### ANALYSE {#analytics}

Selecteer in het keuzemenu het cloudserviceframework Analytics dat voor deze communitysite is geconfigureerd.

De selectie die in het schermafbeelding wordt gezien, `Communities`is het frameworkvoorbeeld uit de [configuratiedocumentatie.](/help/communities/analytics.md#aem-analytics-framework-configuration)

![chlimage_1-454](assets/chlimage_1-454.png)

#### VERTALING {#translation}

In de [vertalingsinstellingen](/help/communities/sites-console.md#translation) wordt aangegeven of UGC kan worden vertaald en in welke taal, indien van toepassing.

* Controleren **machinevertaling toestaan**
* De standaardinstellingen gebruiken

![chlimage_1-456](assets/chlimage_1-456.png)

#### UITSCHAKELING {#enablement}

Voor een machtigingsgemeenschap is het noodzakelijk om één of meerdere Communautaire Beheerders van Enablement te identificeren.

* **Beheerders** inschakelen (vereist) Leden van de 
`Community Enablement Managers` Deze groep is beschikbaar om te worden geselecteerd voor het beheer van deze communitysite.

   * Type `s`
   * Selecteer `Sirius Nilson`

* **Org-id** van Marketing Cloud (optioneel) De id voor een Adobe Analytics-account die nodig is wanneer [Video Heartbone Analytics](/help/communities/analytics.md#video-heartbeat-analytics) wordt opgenomen in de actierapportage.

![chlimage_1-457](assets/chlimage_1-457.png)

Selecteer **Volgende**.

### Stap 4: Community-site maken {#step-create-community-site}

Selecteer **Maken.**

![chlimage_1-458](assets/chlimage_1-458.png)

Wanneer het proces is voltooid, wordt de map voor de nieuwe site weergegeven in de console Communities > Sites.

![vereffening](assets/enablementsitecreated.png)

### De nieuwe Community-site publiceren {#publish-the-new-community-site}

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

   Selecteer het exportpictogram om een pakket van de communitysite te maken dat zowel in [pakketbeheer](/help/sites-administering/package-manager.md) is opgeslagen als is gedownload.
UGC is niet opgenomen in het sitepakket.

* **Site verwijderen**

   Als u de communitysite wilt verwijderen, selecteert u het pictogram Site verwijderen dat verschijnt wanneer u de muisaanwijzer op de site in de Community Site Console plaatst. Met deze actie verwijdert u alle items die aan de site zijn gekoppeld, zoals UGC, gebruikersgroepen, elementen en databaserecords.

   ![inschakelen](assets/enablesiteactions.png)

#### Publiceren selecteren {#select-publish}

Selecteer het pictogram van de wereld om de communitysite te publiceren.

![chlimage_1-465](assets/chlimage_1-465.png)

Er wordt een indicatie gegeven dat de site is gepubliceerd.

![chlimage_1-466](assets/chlimage_1-466.png)

## Community-gebruikers en -gebruikersgroepen {#community-users-user-groups}

### Nieuwe gebruikersgroepen in de Gemeenschap melden {#notice-new-community-user-groups}

Samen met de nieuwe communautaire plaats, worden de nieuwe gebruikersgroepen gecreeerd die de aangewezen toestemmingen hebben die voor diverse administratieve functies worden geplaatst. Ga voor meer informatie naar [Gebruikersgroepen voor communitysites](/help/communities/users.md#usergroupsforcommunitysites).

Voor deze nieuwe communautaire plaats, gezien de plaatsnaam &quot;toelaat&quot;in Stap 1, kunnen de nieuwe gebruikersgroepen die in het publiceren milieu bestaan van de leden van [Gemeenschappen &amp; de console](/help/communities/members.md#groups-console)van Groepen worden gezien:

![community_usergroup](assets/community_usergroup.png)

### Leden toewijzen aan de groep van leden voor Community Enable {#assign-members-to-community-enable-members-group}

Op auteur, met de toegelaten tunneldienst, is het mogelijk om de [gebruikers toe te wijzen die tijdens Aanvankelijke Opstelling](/help/communities/enablement-setup.md#publishcreateenablementmembers) aan de groep van Leden Gemeenschap voor de pas gecreëerde communautaire plaats worden gecreeerd.

Met behulp van de Community Group-console kunnen leden afzonderlijk worden toegevoegd of via lidmaatschap aan een groep worden toegevoegd.

In dit voorbeeld `Community Ski Class` wordt de groep toegevoegd als lid van de groep `Community Enable Members` en als lid `Quinn Harper`.

* Navigeer naar **Communities, console Groepen**
* Groep leden *inschakelen* Gemeenschap selecteren
* Geef &#39;ski&#39; op in het zoekvak Leden **toevoegen aan groep** .
* Selecteer *Klasse* communautair skigebied (groep studenten)
* &#39;quinn&#39; invoeren in het zoekvak
* Selecteer *Quinn Harper* (resablement resource contact)

* Selecteer **Opslaan**

![chlimage_1-418](assets/chlimage_1-418.png)

## Configuraties bij publiceren {#configurations-on-publish}

`https://localhost:4503/content/sites/enable/en.html {#http-localhost-content-sites-enable-en-html}`

![enablement-login](assets/enablement-login.png)

### Configureren voor verificatiefout {#configure-for-authentication-error}

Zodra een plaats is gevormd en geduwd om te publiceren, [vorm login afbeelding](/help/communities/sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) op publiceer instantie. Het voordeel is dat als de aanmeldingsgegevens niet correct zijn ingevoerd, de verificatiefout de aanmeldingspagina van de communautaire site opnieuw weergeeft met een foutbericht.

Een bestand toevoegen `Login Page Mapping` als:

* `/content/sites/enable/en/signin:/content/sites/enable/en`

### (Optioneel) Wijzig de standaardstartpagina {#optional-change-the-default-home-page}

Als u met de publicatiesite werkt voor demonstratiedoeleinden, is het handig om de standaardstartpagina te wijzigen in de nieuwe site.

Hiervoor moet u [CRX|DE](https://localhost:4503/crx/de) Lite gebruiken om de [bronnentoewijzingstabel](/help/sites-deploying/resource-mapping.md) te bewerken bij publicatie.

Aan de slag:

1. Bij publiceren, heb toegang tot CRXDE en login met beheerdervoorrechten

   * Blader bijvoorbeeld naar [https://localhost:4503/crx/de](https://localhost:4503/crx/de) en meld u aan met `admin/admin`

1. Vouw in de projectbrowser uit `/etc/map`
1. Selecteer het `http` knooppunt

   * Knooppunt **maken selecteren**

      * **Naam** localhost.4503

         (gebruik *niet* &#39;:&#39;)

      * **Tekst** [schuintrekken:toewijzen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Met nieuw aangemaakt `localhost.4503` knooppunt geselecteerd

   * Eigenschap toevoegen

      * **Naam** kiezen:overeenkomst
      * **Tekenreeks**
      * **Value** localhost.4503/$

   (moet eindigen met &#39;$&#39; teken)

   * Eigenschap toevoegen

      * **Naam** kiezen:internalRedirect
      * **Tekenreeks**
      * **Value** /content/sites/enable/en.html


1. Alles **opslaan selecteren**
1. (Optioneel) De browsergeschiedenis verwijderen
1. Bladeren naar https://localhost:4503/

   * Ga naar https://localhost:4503/content/sites/enable/en.html

>[!NOTE]
>
>Als u deze optie wilt uitschakelen, voegt u de waarde van de `sling:match` eigenschap gewoon toe met een &#39;&#39;x&#39;&#39; - `xlocalhost.4503/$` - en **Alles** opslaan.


![chlimage_1-364](assets/chlimage_1-364.png)

#### Problemen oplossen: Fout bij opslaan van kaart {#troubleshooting-error-saving-map}

Als het niet lukt om wijzigingen op te slaan, moet u ervoor zorgen dat de naam van het knooppunt `localhost.4503`met een &#39;punt&#39;-scheidingsteken is en niet `localhost:4503` met een &#39;dubbele punt&#39;-scheidingsteken, omdat dit geen geldig naamruimtevoorvoegsel `localhost` is.

![chlimage_1-365](assets/chlimage_1-365.png)

#### Problemen oplossen: Doorsturen mislukt {#troubleshooting-fail-to-redirect}

De &#39;**$**&#39; aan het einde van de reguliere-expressiereeks `sling:match` is van cruciaal belang, zodat alleen exact `https://localhost:4503/` wordt toegewezen. Anders wordt de omleidingswaarde toegevoegd aan elk pad dat mogelijk bestaat na de server:poort in de URL. Wanneer AEM probeert om naar de aanmeldingspagina om te leiden, mislukt dit.

## Het aanpassen van de communautaire Plaats {#modifying-the-community-site}

Nadat de site voor het eerst is gemaakt, kunnen auteurs het pictogram [](/help/communities/sites-console.md#authoring-site-content) Open Site gebruiken om standaard AEM ontwerpactiviteiten uit te voeren.

Daarnaast kunnen beheerders het pictogram [Site](/help/communities/sites-console.md#modifying-site-properties) bewerken gebruiken om eigenschappen van de site, zoals de titel, te wijzigen.

Vergeet niet de site op te **slaan** en opnieuw te **publiceren** nadat u een wijziging hebt aangebracht.

>[!NOTE]
>
>Als u niet bekend bent met AEM, bekijkt u de documentatie over [basisverwerking](/help/sites-authoring/basic-handling.md) en een [handleiding voor het ontwerpen van pagina](/help/sites-authoring/qg-page-authoring.md)&#39;s.


### Een catalogus toevoegen {#add-a-catalog}

Het sjabloon voor de communitysite dat voor deze communitysite is gekozen, moet de catalogusfunctie bevatten.

Als dat niet het geval is, kan de catalogusfunctie eenvoudig worden toegevoegd. Hierdoor kunnen andere leden van de gemeenschap die niet zijn toegewezen aan bronnen voor activering of een leerpad, bronnen voor activering selecteren in een catalogus.

Als de sitestructuur al de catalogusfunctie bevat, kan de titel worden gewijzigd.

Als u de structuur van de site wilt wijzigen, navigeert u naar **[!UICONTROL Communities]** >- **[!UICONTROL Sites]** console, opent u de `enable` map en selecteert u het pictogram Site **** bewerken om toegang te krijgen tot de eigenschappen van `Enablement Tutorial`.

Selecteer het deelvenster STRUCTUUR om een catalogus toe te voegen of een bestaande catalogus te wijzigen:

* **Titel**: `Ski Catalog`

* **URL**: `catalog`

* **Alle naamruimten** selecteren: blijven staan.

* Selecteer **Opslaan**.

![chlimage_1-299](assets/chlimage_1-299.png)

Gebruik het pictogram Positie om de functie Catalog naar de tweede positie te verplaatsen, na Toewijzingen.

![chlimage_1-300](assets/chlimage_1-300.png)

Selecteer **Opslaan** in de rechterbovenhoek om de wijzigingen in de communitysite op te slaan.

Vervolgens **publiceert** u de site opnieuw.

