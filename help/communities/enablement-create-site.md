---
title: Auteur van een nieuwe communautaire site voor activering
seo-title: Author a New Community Site for Enablement
description: Een communitysite maken voor activering
seo-description: Create a community site for enablement
uuid: a75fa566-a570-45fd-aabc-23651ef819cc
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: b9333558-6af9-46b2-9f03-3722645c69a6
docset: aem65
exl-id: 812bbf7b-c49f-4c34-a47d-636b0468e0ba
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1711'
ht-degree: 1%

---

# Auteur van een nieuwe communautaire site voor activering {#author-a-new-community-site-for-enablement}

## Community-site maken {#create-community-site}

[Creatie van gemeenschapssite](/help/communities/sites-console.md) Hiermee gebruikt u een wizard die u door de stappen begeleidt bij het maken van een communitysite. Het is mogelijk verder te gaan naar de `Next` stap of `Back` naar de vorige stap voordat u de site in de laatste stap toewijst.

Ga als volgt te werk om een nieuwe communitysite te maken:

Met de [auteurinstantie](https://localhost:4502/)

* Meld u aan met beheerdersrechten en navigeer naar **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.

* Selecteer **Maken**.

### Stap 1: Sitesjabloon {#step-site-template}

![Sjabloon van de instellingensite](assets/enablement-site-template.png)

Op de **Sitesjabloon** Voer vervolgens een titel, beschrijving, naam voor de URL in en selecteer een sjabloon voor een community-site, bijvoorbeeld:

* **Titel van gemeenschapssite**: `Enablement Tutorial`.

* **Beschrijving van community-site**: `A site for enabling the community to learn.`

* **Hoofdmap van gemeenschapssite**: (leeg laten voor standaardhoofdmap `/content/sites`)

* **Cloudconfiguraties**: (leeg laten als er geen cloudconfiguraties zijn opgegeven) het pad naar de opgegeven cloudconfiguraties bieden.
* **Basis van gemeenschapssite**: (ongewijzigd laten voor één taal: Engels) gebruik drop-down om één te kiezen *of meer* basistalen uit de beschikbare talen: Duits, Italiaans, Frans, Japans, Spaans, Portugees (Brazilië), Chinees (traditioneel) en Chinees (vereenvoudigd). Er wordt één communitysite gemaakt voor elke toegevoegde taal en deze site bestaat in dezelfde sitemap volgens de in [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md). De hoofdpagina van elke site bevat een onderliggende pagina met de taalcode van een van de geselecteerde talen, zoals &#39;en&#39; voor Engels of &#39;fr&#39; voor Frans.

* **Naam van communautaire site**: `enable`

   * De eerste URL wordt onder de naam van de communautaire site weergegeven
   * Voeg voor een geldige URL een basistaalcode + &quot;.html&quot; toe
      *Bijvoorbeeld*, https://localhost:4502/content/sites/ `enable/en.html`

* **Sjabloon verwijzingssite**: naar beneden halen om te kiezen `Reference Structured Learning Site Template`

Selecteren **Volgende**.

### Stap 2: Ontwerp {#step-design}

De stap Ontwerp wordt in twee secties weergegeven voor het selecteren van het thema en de brandbanner:

#### COMMUNAUTAIR SITE-THEMA {#community-site-theme}

Selecteer de gewenste stijl die u op de sjabloon wilt toepassen. Als deze optie is geselecteerd, wordt het thema bedekt met een vinkje.

#### COMMUNAUTAIRE SITOBRANDING {#community-site-branding}

(Optioneel) Upload een bannerafbeelding voor weergave op de sitepagina&#39;s. De banner is vastgezet aan de linkerrand van browser, tussen de communautaire plaatsheader en menu (navigatiekoppelingen). De bannerhoogte wordt bijgesneden tot 120 pixels. Er wordt geen grootte van de banner aangepast aan de breedte van de browser en de hoogte van 120 pixels.

![site-branding1](assets/site-branding1.png)

![site-branding2](assets/site-branding2.png)

Selecteren **Volgende**.

### Stap 3: Instellingen {#step-settings}

Selecteer in de stap Instellingen voordat u `Next`, merk op dat er zeven secties zijn die toegang tot configuraties verlenen die gebruikersbeheer, het etiketteren, rollen, moderatie, analyses, vertaling, en toelaat.

#### GEBRUIKERSBEHEER {#user-management}

Het wordt aanbevolen [gemeenschappen](/help/communities/overview.md#enablement-community) privé zijn.

Een gemeenschapssite is persoonlijk wanneer anonieme sitebezoekers geen toegang krijgen, zich mogelijk niet zelf registreren en geen gebruik maken van sociale aanmelding.

Controleer of de meeste selectievakjes zijn uitgeschakeld [Gebruikersbeheer](/help/communities/sites-console.md#user-management) :

* Sta bezoekers van de site NIET toe zich zelf te registreren.
* Sta geen anonieme sitebezoekers toe om de site te bekijken.
* Optioneel of berichten al dan niet worden toegestaan onder leden van de gemeenschap.
* Meld u NIET aan bij Facebook.
* Meld u NIET aan bij Twitter.

![gebruikersbeheer](assets/user-mgmt.png)

#### TAGS {#tagging}

De tags die kunnen worden toegepast op community-inhoud, worden beheerd door AEM naamruimten te selecteren die eerder zijn gedefinieerd via de [Tagingsconsole](/help/sites-administering/tags.md#tagging-console) (zoals de [Naamruimte voor zelfstudie](/help/communities/enablement-setup.md#create-tutorial-tags)).

Als u bovendien Tagnaamruimten selecteert voor de communitysite, beperkt u de selectie die wordt weergegeven bij het definiëren van catalogi en machtigingsbronnen. Zie [Tags toewijzen](/help/communities/tag-resources.md) voor belangrijke informatie.

Het zoeken naar naamruimten is eenvoudig met &#39;type-ahead&#39;-zoekopdracht. Bijvoorbeeld,

* Type `tut`
* Selecteer `Tutorial`

![enablement-tagging](assets/enablement-tagging.png)

### ROLES {#roles}

[Rol van leden van de Gemeenschap](/help/communities/users.md) worden toegewezen via de instellingen in de sectie Rollen.

Als u een lid van de gemeenschap (of groep leden) de site wilt laten ervaren als gemeenschapsbeheerder, gebruikt u de typecontrole en selecteert u de naam van het lid of de groep in de keuzelijst.

Bijvoorbeeld,

* Type `q`
* Selecteren [Quinn Harper](/help/communities/enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Tunneldienst](/help/communities/deploy-communities.md#tunnel-service-on-author) Hiermee kunt u leden en groepen selecteren die alleen in de publicatieomgeving aanwezig zijn.

![machtigingsrollen](assets/site-admin.png)

#### MODERING {#moderation}

Accepteer de standaard algemene instellingen voor [gematigd](/help/communities/sites-console.md#moderation) door de gebruiker gegenereerde inhoud (UGC).

![moderation1](assets/moderation1.png)

#### ANALYSE {#analytics}

Selecteer in het keuzemenu het cloudserviceframework Analytics dat voor deze communitysite is geconfigureerd.

De selectie in de schermafbeelding, `Communities`, is het kadervoorbeeld van de [configuratiedocumentatie.](/help/communities/analytics.md#aem-analytics-framework-configuration)

![analyse](assets/analytics.png)

#### VERTALING {#translation}

De [Vertaalinstellingen](/help/communities/sites-console.md#translation) specificeren of de UGC al dan niet vertaald kan worden en in welke taal, indien dat het geval is.

* Controleren **Machinevertaling toestaan**
* De standaardinstellingen gebruiken

![vertalen](assets/translation.png)

#### UITSCHAKELING {#enablement}

Voor een machtigingsgemeenschap is het noodzakelijk om één of meerdere Communautaire Beheerders van Enablement te identificeren.

* **Enablement Managers**
(vereist) Leden van de 
`Community Enablement Managers` Deze groep is beschikbaar om te worden geselecteerd voor het beheer van deze communitysite.

   * Type `s`
   * Selecteer `Sirius Nilson`

* **Org-id Marketing Cloud**
(optioneel) De id van een Adobe Analytics-account die nodig is wanneer [Video-hartslaganalyse](/help/communities/analytics.md#video-heartbeat-analytics) in de rapportage over activering.

![inschakelen](assets/enablement.png)

Selecteren **Volgende**.

### Stap 4: Community-site maken {#step-create-community-site}

Selecteer **Maken.**

![voorvertoning](assets/preview.png)

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

   Selecteer het exportpictogram om een pakket te maken van de communitysite waarin beide zijn opgeslagen [pakketbeheer](/help/sites-administering/package-manager.md) en gedownload.
UGC is niet opgenomen in het sitepakket.

* **Site verwijderen**

   Als u de communitysite wilt verwijderen, selecteert u het pictogram Site verwijderen dat verschijnt wanneer u de muisaanwijzer op de site in de Community Site Console plaatst. Met deze actie verwijdert u alle items die aan de site zijn gekoppeld, zoals UGC, gebruikersgroepen, elementen en databaserecords.

   ![inschakelen](assets/enablesiteactions.png)

#### Publiceren selecteren {#select-publish}

Selecteer het pictogram van de wereld om de communitysite te publiceren.

![publicatiesite](assets/publish-site.png)

Er wordt een indicatie gegeven dat de site is gepubliceerd.

![op de site gepubliceerd](assets/site-published.png)

## Community-gebruikers en -gebruikersgroepen {#community-users-user-groups}

### Nieuwe gebruikersgroepen in de Gemeenschap melden {#notice-new-community-user-groups}

Samen met de nieuwe communautaire plaats, worden de nieuwe gebruikersgroepen gecreeerd die de aangewezen toestemmingen hebben die voor diverse administratieve functies worden geplaatst. Ga voor meer informatie naar [Gebruikersgroepen voor communitysites](/help/communities/users.md#usergroupsforcommunitysites).

Voor deze nieuwe communautaire plaats, op basis van de plaatsnaam &quot;laat&quot;toe in Stap 1, kunnen de nieuwe gebruikersgroepen die in het publicatiemilieu bestaan van de [Console leden en groepen van gemeenschappen](/help/communities/members.md#groups-console):

![community_usergroup](assets/community_usergroup.png)

### Leden toewijzen aan de groep van leden voor Community Enable {#assign-members-to-community-enable-members-group}

Op auteur, met de toegelaten tunneldienst, is het mogelijk om toe te wijzen [gebruikers die tijdens de eerste setup zijn gemaakt](/help/communities/enablement-setup.md#publishcreateenablementmembers) aan de communautaire ledengroep voor de nieuwe communautaire site.

Met behulp van de Community Group-console kunnen leden afzonderlijk worden toegevoegd of via lidmaatschap aan een groep worden toegevoegd.

In dit voorbeeld wordt de groep `Community Ski Class` wordt toegevoegd als lid van de groep `Community Enable Members` en lid `Quinn Harper`.

* Navigeren naar **Gemeenschappen, groepen** console
* Selecteren *Leden Gemeenschap inschakelen* groep
* Ga &quot;ski&quot;in **Leden toevoegen aan groep** zoekvak
* Selecteren *Community Ski-klasse* (groep studenten)
* &#39;quinn&#39; invoeren in het zoekvak
* Selecteren *Quinn Harper* (resablement resource contact)

* Selecteren **Opslaan**

![bewerken, groep-instellingen](assets/edit-group-settings.png)

## Configuraties bij publiceren {#configurations-on-publish}

`https://localhost:4503/content/sites/enable/en.html {#http-localhost-content-sites-enable-en-html}`

![enablement-login](assets/enablement-login.png)

### Configureren voor verificatiefout {#configure-for-authentication-error}

Nadat een site is geconfigureerd en geduwd op publiceren, [aanmeldingstoewijzing configureren](/help/communities/sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) op het publicatieexemplaar. Het voordeel is dat als de aanmeldingsgegevens niet correct zijn ingevoerd, de verificatiefout de aanmeldingspagina van de communautaire site opnieuw weergeeft met een foutbericht.

Voeg een `Login Page Mapping` als:

* `/content/sites/enable/en/signin:/content/sites/enable/en`

### (Optioneel) Wijzig de standaardstartpagina {#optional-change-the-default-home-page}

Als u met de publicatiesite werkt voor demonstratiedoeleinden, is het handig om de standaardstartpagina te wijzigen in de nieuwe site.

Hiervoor is het gebruik van [CRX|DE](https://localhost:4503/crx/de) Lite om de [resourcetoewijzing](/help/sites-deploying/resource-mapping.md) publicatietabel.

Aan de slag:

1. Bij publiceren, heb toegang tot CRXDE en login met beheerdervoorrechten

   * Blader bijvoorbeeld naar [https://localhost:4503/crx/de](https://localhost:4503/crx/de) en aanmelden met `admin/admin`

1. Vouw in de projectbrowser uit `/etc/map`
1. Selecteer `http` node

   * Selecteren **Knooppunt maken**

      * **Naam** localhost.4503

         (do *niet* use &#39;:&#39;)

      * **Type** [schuintrekken:toewijzen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Met nieuw gemaakt `localhost.4503` knooppunt geselecteerd

   * Eigenschap toevoegen

      * **Naam** sling:match
      * **Type** String
      * **Waarde** localhost.4503/$

   (moet eindigen met &#39;$&#39; teken)

   * Eigenschap toevoegen

      * **Naam** sling:internalRedirect
      * **Type** String
      * **Waarde** /content/sites/enable/en.html


1. Selecteren **Alles opslaan**
1. (Optioneel) De browsergeschiedenis verwijderen
1. Bladeren naar https://localhost:4503/

   * Ga naar https://localhost:4503/content/sites/enable/en.html

>[!NOTE]
>
>Om onbruikbaar te maken, eenvoudig prepend `sling:match` eigenschapswaarde met een &#39;x&#39; - `xlocalhost.4503/$` - en **Alles opslaan**.

![change-default-homepage](assets/change-default-homepage.png)

#### Problemen oplossen: Fout bij opslaan van kaart {#troubleshooting-error-saving-map}

Als u de wijzigingen niet kunt opslaan, moet u controleren of de knooppuntnaam `localhost.4503`, met een &#39;punt&#39;-scheidingsteken, en niet `localhost:4503` met een &#39;dubbele punt&#39;-scheidingsteken, als `localhost` is geen geldig naamruimtevoorvoegsel.

![error-map](assets/error-map.png)

#### Problemen oplossen: Doorsturen mislukt {#troubleshooting-fail-to-redirect}

De &#39;**$**&#39; aan het einde van de reguliere expressie `sling:match` tekenreeks is van cruciaal belang, zodat alleen `https://localhost:4503/` wordt toegewezen, anders wordt de omleidingswaarde prepended aan om het even welk weg die na server zou kunnen bestaan:haven in URL. Wanneer AEM probeert om naar de aanmeldingspagina om te leiden, mislukt dit.

## Het aanpassen van de communautaire Plaats {#modifying-the-community-site}

Nadat de site voor het eerst is gemaakt, kunnen auteurs de opdracht [Site openen, pictogram](/help/communities/sites-console.md#authoring-site-content) standaardinstellingen voor AEM ontwerpactiviteiten uit te voeren.

Daarnaast kunnen beheerders de opdracht [Site-pictogram bewerken](/help/communities/sites-console.md#modifying-site-properties) om eigenschappen van de site te wijzigen, zoals de titel.

Vergeet niet om na elke wijziging **Opslaan** en re-**Publiceren** de site.

>[!NOTE]
>
>Als u niet bekend bent met AEM, kunt u de documentatie raadplegen op [basisbehandeling](/help/sites-authoring/basic-handling.md) en [snelle handleiding voor het ontwerpen van pagina&#39;s](/help/sites-authoring/qg-page-authoring.md).

### Een catalogus toevoegen {#add-a-catalog}

Het sjabloon voor de communitysite dat voor deze communitysite is gekozen, moet de catalogusfunctie bevatten.

Als dat niet het geval is, kan de catalogusfunctie eenvoudig worden toegevoegd. Hierdoor kunnen andere leden van de gemeenschap die niet zijn toegewezen aan bronnen voor activering of een leerpad, bronnen voor activering selecteren in een catalogus.

Als de sitestructuur al de catalogusfunctie bevat, kan de titel worden gewijzigd.

Als u de structuur van de site wilt wijzigen, navigeert u naar **[!UICONTROL Communities]** > **[!UICONTROL Sites]** console, opent `enable` en selecteert u de **Site bewerken** pictogram voor toegang tot de eigenschappen van `Enablement Tutorial`.

Selecteer het deelvenster STRUCTUUR om een catalogus toe te voegen of een bestaande catalogus te wijzigen:

* **Titel**: `Ski Catalog`

* **URL**: `catalog`

* **Alle naamruimten selecteren**: blijven staan.

* Selecteren **Opslaan**.

![wijzigen-plaats-structuur](assets/modify-site-structure.png)

Gebruik het pictogram Positie om de functie Catalog naar de tweede positie te verplaatsen, na Toewijzingen.

![move-catalog-func](assets/move-catalog-func.png)

Selecteren **Opslaan** in de rechterbovenhoek om de wijzigingen in de communitysite op te slaan.

Dan re-**Publiceren** de site.
