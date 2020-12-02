---
title: Auteur van een nieuwe communautaire site
seo-title: Auteur van een nieuwe communautaire site
description: Een nieuwe AEM Communities-site maken
seo-description: Een nieuwe AEM Communities-site maken
uuid: 4f609f5f-ef07-44fc-aeb3-1c616e120d46
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
discoiquuid: 8ae324ea-8b84-47a3-aabf-1fee2a3bd46d
docset: aem65
translation-type: tm+mt
source-git-commit: 2daf00f17058de8b901848fcf1128a5ee9770368
workflow-type: tm+mt
source-wordcount: '1640'
ht-degree: 1%

---


# Auteur een Nieuwe Communautaire Plaats{#author-a-new-community-site}

## Een communautaire site maken {#create-a-community-site}

Gebruik de auteur instantie om een communautaire plaats tot stand te brengen. Instantie van AEM-auteur:

1. Meld u aan met beheerdersrechten.
1. Van globale navigatie, ga naar **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.

De console van de Plaatsen van Gemeenschappen verstrekt een tovenaar om door de stappen te begeleiden om een communautaire plaats tot stand te brengen. Het is mogelijk door te gaan naar de stap `Next` of `Back` naar de vorige stap voordat u de site in de laatste stap toewijst.

Ga als volgt te werk om een nieuwe communitysite te maken:

* Selecteer de `Create` knoop.

![createcommunitysite](assets/createcommunitysite.png)

### Stap 1: Sitesjabloon {#step-site-template}

![sjabloon om site te maken](assets/create-site.png)

Voer in de stap [Sjabloon site](/help/communities/sites-console.md#step2013asitetemplate) een titel, beschrijving, naam voor de URL in en selecteer bijvoorbeeld een sjabloon voor een communitysite:

* **Titel** van communautaire site:  `Getting Started Tutorial`
* **Beschrijving** van communautaire site:  `A site for engaging with the community.`
* **Hoofdmap** van gemeenschapssite: (leeg laten voor standaardhoofdmap  `/content/sites`)
* **Cloudconfiguraties**: (leeg laten als er geen cloudconfiguraties zijn opgegeven) het pad naar de opgegeven cloudconfiguraties bieden.
* **Basistaal** van gemeenschapssite: (ongewijzigd laten voor één taal: (Engels) gebruik de drop-down lijst om één  *of* meer basistalen van de beschikbare talen - Duits, Italiaans, Frans, Japans, Spaans, Portugees (Brazilië), Chinees (Traditioneel), en Chinees (Vereenvoudigd) te kiezen. Er wordt één communitysite gemaakt voor elke toegevoegde taal en deze wordt in dezelfde sitemap gebruikt volgens de best practices die worden beschreven in [Inhoud vertalen voor meertalige sites](/help/sites-administering/translation.md). De hoofdpagina van elke site bevat een onderliggende pagina met de taalcode van een van de geselecteerde talen, zoals &#39;en&#39; voor Engels of &#39;fr&#39; voor Frans.

* **Naam** van communautaire site: aangaan

   * Controleer de naam tweemaal omdat deze na het maken van de site niet gemakkelijk kan worden gewijzigd
   * De eerste URL wordt onder de naam van de communautaire site weergegeven
   * Voeg voor een geldige URL een basistaalcode + &quot;.html&quot; toe
   * *Bijvoorbeeld* https://localhost:4502/content/sites/  `engage/en.html`

* **Sjabloon**: naar beneden halen om te kiezen  `Reference Site`

* Selecteer **Volgende**.

### Stap 2: Ontwerp {#step-design}

De stap Ontwerp wordt in twee secties weergegeven voor het selecteren van het thema en de brandbanner:

#### THEMA VAN COMMUNAUTAIRE SITE {#community-site-theme}

Selecteer de gewenste stijl die u op de sjabloon wilt toepassen. Als deze optie is geselecteerd, wordt op het thema een vinkje weergegeven.

#### COMMUNAUTAIRE SITEBRANDING {#community-site-branding}

(Optioneel) Upload een bannerafbeelding voor weergave op de sitepagina&#39;s. De banner is vastgezet aan de linkerrand van browser, tussen de communautaire plaatsheader en navigatiekoppelingen. De bannerhoogte wordt bijgesneden tot 120 pixels. Er wordt geen grootte van de banner aangepast aan de breedte van de browser en de hoogte van 120 pixels.

![branding op de website](assets/community-site-branding.png)

![uploaden naar afbeeldingssite](assets/upload-image-site.png)

Selecteer **Volgende**.

### Stap 3: Instellingen {#step-settings}

Voor de stap van Montages, alvorens `Next` te selecteren, merk op dat er zeven secties die toegang tot configuraties verlenen die gebruikersbeheer, etiketteren, moderatie, groepsbeheer, analyses, vertaling en enablement impliceren.

Bezoek de zelfstudie [Aan de slag met AEM Communities for Enablement](/help/communities/getting-started-enablement.md) om te werken met de functies voor activering.

#### Gebruikersbeheer {#user-management}

Schakel alle selectievakjes in voor [Gebruikersbeheer](/help/communities/sites-console.md#user-management)

* Sitebezoekers toestaan zich te registreren
* Site-bezoekers toestaan de site weer te geven zonder zich aan te melden
* Leden toestaan berichten van andere leden van de gemeenschap te verzenden en te ontvangen
* Aanmelden met Facebook toestaan in plaats van zich te registreren en een profiel te maken
* Aanmelden met Twitter toestaan in plaats van zich te registreren en een profiel te maken

>[!NOTE]
>
>Voor een productieomgeving moeten aangepaste Facebook- en Twitter-toepassingen worden gemaakt. Zie [Sociale aanmelding bij Facebook en Twitter](/help/communities/social-login.md).

![site-instellingen van community](assets/site-settings.png)

#### TAGS {#tagging}

De tags die kunnen worden toegepast op community-inhoud, worden beheerd door AEM naamruimten te selecteren die eerder zijn gedefinieerd via de [Tagingconsole](/help/sites-administering/tags.md#tagging-console) (zoals de [Zelfstudie-naamruimte](/help/communities/setup.md#create-tutorial-tags)).

Het zoeken naar naamruimten is eenvoudig met &#39;type-ahead&#39;-zoekopdracht. Bijvoorbeeld,

* Type `tut`
* Selecteer `Tutorial`

![labelen](assets/tagging.png)

#### ROLLEN {#roles}

[De communautaire ](/help/communities/users.md) leden worden toegewezen door de montages in de sectie van Rollen.

Als u een lid van de gemeenschap (of groep leden) de site wilt laten ervaren als gemeenschapsbeheerder, gebruikt u de typecontrole en selecteert u de naam van het lid of de groep in de keuzelijst.

Bijvoorbeeld,

* Tekst `q`
* Selecteer [Quinn Harper](/help/communities/enablement-setup.md#publishcreateenablementmembers)

>[!NOTE]
>
>[Met de tunnelservice ](https://helpx.adobe.com/experience-manager/6-3/help/communities/deploy-communities.html#tunnel-service-on-author) kunt u leden en groepen selecteren die alleen in de publicatieomgeving aanwezig zijn.

![gebruikersrollen in nieuwe site](assets/site-admin-1.png)

#### MODERING {#moderation}

Accepteer de standaard algemene instellingen voor [het modereren](/help/communities/sites-console.md#moderation) door de gebruiker gegenereerde inhoud (UGC).

![matiging](assets/moderation1.png)

#### ANALYSE {#analytics}

Als Adobe Analytics een licentie heeft en er een cloudservice en -framework voor Analytics zijn geconfigureerd, is het mogelijk Analytics in te schakelen en het framework te selecteren.

Zie [Analyseconfiguratie voor Gemeenschappen-functies](/help/communities/analytics.md).

![analyse](assets/analytics.png)

#### TRANSLATION {#translation}

Met de [Vertaalinstellingen](/help/communities/sites-console.md#translation) wordt de basistaal voor de site opgegeven en wordt aangegeven of UGC al dan niet kan worden vertaald en in welke taal, indien dat het geval is.

* Schakel **Machinevertaling toestaan**
* Laat standaardtalen geselecteerd blijven voor vertaling door de standaardvertaalservice voor machines
* Standaard vertaalprovider en config laten staan
* Er is geen behoefte aan een globale opslag omdat er geen taalexemplaren zijn
* Selecteer **Volledige pagina vertalen**
* De optie Standaardpersistentie behouden

![translatie-instellingen](assets/translation-settings.png)

#### INSCHAKELEN {#enablement}

Laat leeg als u een betrokkenheidsgemeenschap maakt.

Zie [Aan de slag met AEM Communities for Enablement](/help/communities/getting-started-enablement.md) voor een vergelijkbare zelfstudie om snel een [enablement community](/help/communities/overview.md#enablement-community) te maken.

Selecteer **Volgende**.

![inschakelen](assets/enablement.png)

### Stap 4: Communitysite {#step-create-communities-site} maken

Selecteer **Maken.**

![site maken](assets/create-site2.png)

Wanneer het proces is voltooid, wordt de map voor de nieuwe site weergegeven in de console Communities - Sites.

![communautiessitesconsole](assets/communitiessitesconsole.png)

## De communautaire site {#publish-the-community-site} publiceren

De gecreeerde plaats zou van de Gemeenschappen - de console van Plaatsen moeten worden beheerd, de zelfde console van waar de nieuwe plaatsen kunnen worden gecreeerd.

Nadat u de map van de communitysite hebt geselecteerd om deze te openen, houdt u de muisaanwijzer boven het sitepictogram, zodat er vier actiepictogrammen worden weergegeven:

![site-actionicons-1](assets/siteactionicons-1.png)

Als u het vierde ovalenpictogram selecteert (Meer handelingen), worden de opties Site exporteren en Site verwijderen weergegeven.

![site-actionsnew-1](assets/siteactionsnew-1.png)

Van links naar rechts zijn ze:

* **Site openen**

   Selecteer het potloodpictogram om de gemeenschapssite te openen in de modus Bewerken door auteur om paginacomponenten toe te voegen en/of te configureren

* **Site bewerken**

   Selecteer het eigenschappenpictogram om de communitysite te openen voor wijziging van eigenschappen, zoals de titel of om het thema te wijzigen

* **Site publiceren**

   Selecteer het wereldpictogram om de communitysite te publiceren (bijvoorbeeld als uw publicatieserver op uw lokale computer wordt uitgevoerd en vervolgens standaard naar localhost:4503)

* **Site exporteren**

   Selecteer het exportpictogram om een pakket te maken van de communitysite die zowel in [pakketbeheer](/help/sites-administering/package-manager.md) is opgeslagen als is gedownload.
UGC is niet opgenomen in het sitepakket.

* **Site verwijderen**

   Selecteer het verwijderpictogram om de communitysite te verwijderen uit **[!UICONTROL Communities > Sites console]**. Met deze actie verwijdert u alle items die aan de site zijn gekoppeld, zoals UGC, gebruikersgroepen, elementen en databaserecords.

![sitehandelingen](assets/siteactions.png)

>[!NOTE]
>
>Als het gebruiken van standaardhaven 4503 voor publiceer instantie, dan geef de standaard replicatieagent uit om het havenaantal aan de correcte waarde te plaatsen.
>
>In de auteurinstantie, van het belangrijkste menu:
>
>1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Replication]** menu.
>1. Selecteer **[!UICONTROL Agents on author]**.
>1. Selecteer **[!UICONTROL Default Agent (publish)]**.
>1. Selecteer **[!UICONTROL Edit]** naast **[!UICONTROL Settings]**.
>1. Selecteer **[!UICONTROL Transport]** tab in het pop-updialoogvenster Agent-instellingen.
>1. Wijzig in URI het poortnummer 4503 in het gewenste poortnummer. Als u bijvoorbeeld poort 6103 wilt gebruiken: https://localhost:6103/bin/receive?sling:authRequestLogin=1
>1. Selecteer **[!UICONTROL OK]**.
>1. (Optioneel) Selecteer **[!UICONTROL Clear]** of **[!UICONTROL Force Retry]** om de replicatiewachtrij opnieuw in te stellen.


### Publiceren {#select-publish} selecteren

Nadat u ervoor hebt gezorgd dat de publicatieserver actief is, selecteert u het wereldpictogram om de communitysite te publiceren.

![publicatiesite](assets/publish-site.png)

Wanneer de communitysite met succes is gepubliceerd, wordt kort het bericht &#39;Site gepubliceerd&#39; weergegeven.

### Nieuwe gebruikersgroepen in de gemeenschap {#new-community-user-groups}

Samen met de nieuwe communautaire plaats, worden de nieuwe gebruikersgroepen gecreeerd die de aangewezen toestemmingen hebben die voor diverse administratieve functies worden geplaatst. Voor details, bezoek [Gebruikersgroepen voor Communautaire Plaatsen](/help/communities/users.md#usergroupsforcommunitysites).

Voor deze nieuwe communautaire plaats, gezien de plaatsnaam &quot;verbind&quot;in Stap 1, kunnen de vier nieuwe gebruikersgroepen van de [console van Groepen](/help/communities/members.md) (globale navigatie: Gemeenschappen, groepen):

* Community-managers voor community inschakelen
* Gemeenschapsgroepsbeheerders
* Samenvoegingsleden van gemeenschap
* Maatschappelijke experts
* Geprivilegieerde leden van Community Engineering
* Community Engineering Site-inhoudsbeheer

[Aaron McDonald](/help/communities/tutorials.md#demo-users) is lid van

* Community-managers voor community inschakelen
* Maatschappelijke experts
* Community Engage-leden (indirect als lid van de groep Moderatoren)

![gebruikersgroep](assets/user-group.png)

#### https://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![aangaan](assets/engage.png)

## Configureren voor verificatiefout {#configure-for-authentication-error}

Nadat een site is geconfigureerd en geduwd op publiceren, [configureert u de aanmeldingstoewijzing](/help/communities/sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) op de publicatieinstantie. Het voordeel is dat als de aanmeldingsgegevens niet correct zijn ingevoerd, de verificatiefout de aanmeldingspagina van de communautaire site opnieuw weergeeft met een foutbericht.

Een `Login Page Mapping` toevoegen als

* `/content/sites/engage/en/signin:/content/sites/engage/en`

## Optionele stappen {#optional-steps}

### De standaardstartpagina {#change-the-default-home-page} wijzigen

Als u met de publicatiesite werkt voor demonstratiedoeleinden, is het handig om de standaardstartpagina te wijzigen in de nieuwe site.

Hiervoor moet u [CRXDE](https://localhost:4503/crx/de) Lite gebruiken om de [resource-mapping](/help/sites-deploying/resource-mapping.md)-tabel bij publicatie te bewerken.

Aan de slag:

1. Meld u aan bij een publicatieexemplaar met beheerdersrechten.
1. Blader naar [https://localhost:4503/crx/de](https://localhost:4503/crx/de).
1. Vouw `/etc/map.` in de projectbrowser uit
1. Selecteer de `http` knoop:

   * Selecteer **Knooppunt maken:**

      * **** Namelocalhost.4503 ( ** gebruik &#39;:&#39; niet)

      * **** [lettertypen:toewijzen](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Met nieuw aangemaakt `localhost.4503`-knooppunt geselecteerd:

   * Eigenschap toevoegen:

   * **** naamgeving:overeenkomst
      * **** TypeString
      * **** Valuelocalhost.4503/$ (moet eindigen met &#39;$&#39; teken)
   * Eigenschap toevoegen:

      * **** naamgeving:internalRedirect
      * **** TypeString
      * **Waarde** /content/sites/engage/en.html


1. Selecteer **Alles opslaan.**
1. (Optioneel) Verwijder de browsergeschiedenis.
1. Ga naar https://localhost:4503/.

   * Ga naar https://localhost:4503/content/sites/engage/en.html

>[!NOTE]
>
>Als u deze optie wilt uitschakelen, plaatst u gewoon een voorvoegsel voor de waarde van de eigenschap `sling:match` met een &#39;x&#39; - `xlocalhost.4503/$` - en **Alles opslaan**.

![optionele stappen](assets/optional-steps.png)

#### Problemen oplossen: Fout bij opslaan van kaart {#troubleshooting-error-saving-map}

Als u wijzigingen niet kunt opslaan, moet u ervoor zorgen dat de knooppuntnaam `localhost.4503` is, met een &#39;punt&#39;-scheidingsteken en niet `localhost:4503` met een &#39;dubbele punt&#39;-scheidingsteken, omdat `localhost`geen geldig naamruimtevoorvoegsel is.

![foutbericht](assets/error-message.png)

#### Problemen oplossen: Kan {#troubleshooting-fail-to-redirect} niet omleiden

De tekenreeks &#39;**$**&#39; aan het einde van de reguliere expressie `sling:match`is van cruciaal belang, zodat alleen exact `https://localhost:4503/` wordt toegewezen, anders wordt de omleidingswaarde voorafgegaan aan elk pad dat mogelijk bestaat na de server:poort in de URL. Wanneer AEM probeert om naar de aanmeldingspagina om te leiden, mislukt dit.

### De site {#modify-the-site} wijzigen

Nadat de site voor het eerst is gemaakt, kunnen auteurs het [pictogram Open Site](/help/communities/sites-console.md#authoring-site-content) gebruiken om standaard AEM ontwerpactiviteiten uit te voeren.

Daarnaast kunnen beheerders het [Sitepictogram bewerken](/help/communities/sites-console.md#modifying-site-properties) gebruiken om eigenschappen van de site, zoals de titel, te wijzigen.

Na om het even welke wijziging, herinner aan **sparen** en re-**Publish** de plaats.

>[!NOTE]
>
>Als u niet bekend bent met AEM, bekijkt u de documentatie over [basisverwerking](/help/sites-authoring/basic-handling.md) en een [handleiding voor het schrijven van pagina&#39;s](/help/sites-authoring/qg-page-authoring.md).
