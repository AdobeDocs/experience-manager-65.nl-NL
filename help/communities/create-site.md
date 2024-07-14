---
title: Auteur van een communautaire site
description: Leer hoe u een Adobe Experience Manager Communities-site ontwerpt.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: introduction
content-type: reference
docset: aem65
exl-id: d4c1895f-421c-4146-b94a-8d11065ef9e3
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '1535'
ht-degree: 0%

---

# Auteur van een communautaire site{#author-a-new-community-site}

## Een Community-site maken {#create-a-community-site}

Gebruik de auteur instantie om een communautaire plaats tot stand te brengen. Op AEM instantie Auteur:

1. Meld u aan met beheerdersrechten.
1. Van globale navigatie, ga naar **[!UICONTROL Communities]** > **[!UICONTROL Sites]**.

De console van de Plaatsen van Gemeenschappen verstrekt een tovenaar om door de stappen te begeleiden om een communautaire plaats tot stand te brengen. U kunt verdergaan naar de `Next` -stap of `Back` naar de vorige stap voordat u de site in de laatste stap toewijst.

Ga als volgt te werk om een communitysite te maken:

* Selecteer de knop `Create` .

![ createcommunitysite ](assets/createcommunitysite.png)

### Stap 1: Sitjabloon {#step-site-template}

![ malplaatje om plaats ](assets/create-site.png) te creëren

Voor de [ stap van het Malplaatje van de Plaats ](/help/communities/sites-console.md#step2013asitetemplate), ga een titel, een beschrijving, de naam voor URL in, en selecteer een malplaatje van de communautaire plaats, bijvoorbeeld:

* **Titel van de Communautaire Plaats**: `Getting Started Tutorial`
* **Beschrijving van de Communautaire Plaats**: `A site for engaging with the community.`
* **Hoofdmap van de Communautaire Plaats**: (verlaten leeg voor standaardwortel `/content/sites`)
* **de Configuraties van de Wolk**: (verlaten leeg als geen wolkenconfiguraties worden gespecificeerd) verstrekken weg aan de gespecificeerde wolkenconfiguraties.
* **Communautaire Taal van de Basis van de Plaats**: (verlaten onaangeroerd voor enige taal: Engels) gebruik de drop-down lijst om één *of meer* basistalen van beschikbare talen - Duits, Italiaans, Frans, Japans, Spaans, Portugees (Brazilië), Chinees (Traditioneel), en Chinees (Vereenvoudigd) te kiezen. Één communautaire plaats wordt gecreeerd voor elke toegevoegde taal, en bestaat binnen de zelfde plaatsomslag na de beste praktijken die in [ worden beschreven Vertaalend Inhoud voor Meertalige Plaatsen ](/help/sites-administering/translation.md). De hoofdpagina van elke site bevat een onderliggende pagina die wordt genoemd door de taalcode van een van de geselecteerde talen, zoals &#39;en&#39; voor Engels of &#39;fr&#39; voor Frans.

* **Communautaire Naam van de Plaats**: verbind

   * Controleer de naam tweemaal omdat deze na het maken van de site niet gemakkelijk kan worden gewijzigd
   * De eerste URL wordt weergegeven onder de naam van de communautaire site
   * Voeg voor een geldige URL een basistaalcode + &quot;.html&quot; toe
   * *bijvoorbeeld*, https://localhost:4502/content/sites/ `engage/en.html`

* **Malplaatje**: trek neer om te kiezen `Reference Site`

* Selecteer **daarna**.

### Stap 2: Ontwerp {#step-design}

De stap Ontwerp wordt in twee secties weergegeven voor het selecteren van het thema en de brandbanner:

#### COMMUNAUTAIR SITE-THEMA {#community-site-theme}

Selecteer de gewenste stijl die u op de sjabloon wilt toepassen. Als deze optie is geselecteerd, wordt het thema bedekt met een vinkje.

#### COMMUNAUTAIRE SITOBRANDING {#community-site-branding}

(Optioneel) Upload een bannerafbeelding voor weergave op de sitepagina&#39;s. De banner is vastgezet aan de linkerrand van browser, tussen de communautaire plaatsheader en navigatiekoppelingen. De bannerhoogte wordt bijgesneden tot 120 pixels. Er wordt geen grootte van de banner aangepast aan de breedte van de browser en de hoogte van 120 pixels.

![ gemeenschap-plaats-branding ](assets/community-site-branding.png)

![ upload-image-plaats ](assets/upload-image-site.png)

Selecteer **daarna**.

### Stap 3: Instellingen {#step-settings}

Voor de stap van Montages, alvorens `Next` te selecteren, zijn er zeven secties die toegang tot configuraties verlenen die gebruikersbeheer, etiketteren, moderatie, groepsbeheer, analyses, en vertaling impliceren.

#### Gebruikersbeheer {#user-management}

Controle alle controledozen voor [ Gebruikersbeheer ](/help/communities/sites-console.md#user-management)

* Sitebezoekers toestaan zich te registreren
* Site-bezoekers toestaan de site weer te geven zonder zich aan te melden
* Leden toestaan berichten van andere leden van de gemeenschap te verzenden en te ontvangen
* Aanmelden met Facebook toestaan in plaats van zich te registreren en een profiel te maken
* Aanmelden met Twitter toestaan in plaats van een profiel te registreren en te maken

>[!NOTE]
>
>Voor een productieomgeving is het nodig om aangepaste Facebook- en Twitter-toepassingen te maken. Zie [ Sociale Login met Facebook en Twitter ](/help/communities/social-login.md).

![ montages van de communautaire plaats ](assets/site-settings.png)

#### TAGS {#tagging}

De markeringen die op communautaire inhoud worden toegepast worden gecontroleerd door AEM te selecteren namespaces die eerder door de [ Tagende Console ](/help/sites-administering/tags.md#tagging-console) worden bepaald (zoals [ Tutorial namespace ](/help/communities/setup.md#create-tutorial-tags)).

Het zoeken naar naamruimten is eenvoudig met &#39;type-ahead&#39;-zoekopdracht. Bijvoorbeeld:

* Tekst `tut`
* Selecteren `Tutorial`

![ etiketterend ](assets/tagging.png)

#### ROLES {#roles}

[ Communautaire lidrollen ](/help/communities/users.md) worden toegewezen door de montages in de sectie van Rollen.

Als u een lid van de gemeenschap (of groep leden) de site wilt laten ervaren als gemeenschapsbeheerder, gebruikt u de typecontrole en selecteert u de naam van het lid of de groep in de keuzelijst.

Bijvoorbeeld:

* Tekst `q`
* Quinn Harper selecteren

>[!NOTE]
>
>[ de dienst van de Tunnel ](https://helpx.adobe.com/experience-manager/6-3/help/communities/deploy-communities.html#tunnel-service-on-author) staat selectie van leden en groepen toe die slechts in publiceren milieu bestaan.

![ gebruikersrollen in nieuwe plaats ](assets/site-admin-1.png)

#### MODERING {#moderation}

Accepteer de standaard globale montages voor [ het modereren ](/help/communities/sites-console.md#moderation) gebruiker-geproduceerde inhoud (UGC).

![ matiging ](assets/moderation1.png)

#### ANALYTICA {#analytics}

Als Adobe Analytics een licentie heeft en er een Analytics Cloud-service en -framework zijn geconfigureerd, is het mogelijk om Analytics in te schakelen en het framework te selecteren.

Zie [ Configuratie Analytics voor de Eigenschappen van Gemeenschappen ](/help/communities/analytics.md).

![ analytics ](assets/analytics.png)

#### VERTALING {#translation}

De [ Vertaalmontages ](/help/communities/sites-console.md#translation) specificeren de basistaal voor de plaats en of UGC kan worden vertaald en in welke taal, als zo.

* Controle **staat de Vertaling van de Machine toe**
* Laat standaardtalen geselecteerd blijven voor vertaling door de standaardvertaalservice voor machines
* Standaard vertaalprovider en config laten staan
* Er is geen behoefte aan een globale opslag omdat er geen taalexemplaren zijn
* Selecteer **volledige pagina vertalen**
* De optie Standaardpersistentie behouden

![ vertaling-montages ](assets/translation-settings.png)

### Stap 4: Create Communities Site {#step-create-communities-site}

Selecteer **creëren.**

![ creeer-plaats ](assets/create-site2.png)

Wanneer het proces is voltooid, wordt de map voor de nieuwe site weergegeven in de console Communities - Sites.

![ communitiessitesconsole ](assets/communitiessitesconsole.png)

## Publish the Community Site {#publish-the-community-site}

De gecreeerde plaats zou van de Gemeenschappen - de console van Plaatsen moeten worden beheerd, de zelfde console van waar de nieuwe plaatsen kunnen worden gecreeerd.

Nadat u de map van de communitysite hebt geselecteerd om deze te openen, houdt u de muisaanwijzer boven het sitepictogram, zodat er vier actiepictogrammen worden weergegeven:

![ plaats actionicons-1 ](assets/siteactionicons-1.png)

Als u het vierde ovalenpictogram selecteert (Meer handelingen), worden de opties Site exporteren en Site verwijderen weergegeven.

![ plaatsen nieuw-1 ](assets/siteactionsnew-1.png)

Van links naar rechts zijn ze:

* **Open Plaats**

  Als u het potloodpictogram selecteert, wordt de gemeenschapssite geopend in de modus Auteur bewerken, waar u paginacomponenten kunt toevoegen of configureren.

* **geef Plaats** uit

  Als u het eigenschappenpictogram selecteert, wordt de communautaire site geopend voor het wijzigen van eigenschappen, zoals de titel, of voor het wijzigen van het thema.

* **Publish Plaats**

  Als u het wereldpictogram selecteert, wordt de communitysite gepubliceerd (als de publicatieserver bijvoorbeeld op uw lokale computer wordt uitgevoerd, standaard naar localhost:4503).

* **de Plaats van de Uitvoer**

  Het selecteren van het uitvoerpictogram leidt tot een pakket van de communautaire plaats die zowel in [ Manager van het Pakket ](/help/sites-administering/package-manager.md) wordt opgeslagen en gedownload. UGC is niet opgenomen in het sitepakket.

* **plaats van de Schrapping**

  Als u het verwijderpictogram selecteert, wordt de communitysite verwijderd uit **[!UICONTROL Communities > Sites console]** . Deze actie verwijdert alle punten verbonden aan de plaats, zoals UGC, gebruikersgroepen, activa, en gegevensbestandverslagen.

![ plaatsacties ](assets/siteactions.png)

>[!NOTE]
>
>Als het gebruiken van standaardhaven 4503 voor publiceer instantie, dan geef de standaard replicatieagent uit om het havenaantal aan de correcte waarde te plaatsen.
>
>In de auteurinstantie, van het belangrijkste menu:
>
>1. Ga naar het menu **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Replication]** .
>1. Selecteer **[!UICONTROL Agents on author]** .
>1. Selecteer **[!UICONTROL Default Agent (publish)]** .
>1. Selecteer **[!UICONTROL Edit]** naast **[!UICONTROL Settings]** .
>1. Selecteer **[!UICONTROL Transport]** tab in het pop-updialoogvenster Agent-instellingen.
>1. Wijzig in URI het poortnummer 4503 in het gewenste poortnummer. Als u bijvoorbeeld poort 6103 wilt gebruiken: https://localhost:6103/bin/receive?sling:authRequestLogin=1
>1. Selecteer **[!UICONTROL OK]** .
>1. (Optioneel) Selecteer **[!UICONTROL Clear]** of **[!UICONTROL Force Retry]** om de replicatiewachtrij opnieuw in te stellen.

### Publish selecteren {#select-publish}

Nadat u ervoor hebt gezorgd dat de publicatieserver actief is, selecteert u het wereldpictogram om de communitysite te publiceren.

![ publiceren-plaats ](assets/publish-site.png)

Wanneer de communitysite met succes is gepubliceerd, wordt kort het bericht &#39;Site gepubliceerd&#39; weergegeven.

### Nieuwe gebruikersgroepen in de community {#new-community-user-groups}

Samen met de nieuwe communautaire plaats, worden de nieuwe gebruikersgroepen gecreeerd die de aangewezen toestemmingen hebben die voor diverse administratieve functies worden geplaatst. Voor details, bezoek [ Gebruikersgroepen voor Communautaire Plaatsen ](/help/communities/users.md#usergroupsforcommunitysites).

Voor deze nieuwe communautaire plaats, gezien de plaatsnaam &quot;verbind&quot;in Stap 1, kunnen de vier nieuwe gebruikersgroepen van de [ console van Groepen ](/help/communities/members.md) (globale navigatie: Gemeenschappen, Groepen) worden gezien:

* Community-managers voor community inschakelen
* Gemeenschapsgroepsbeheerders
* Samenvoegingsleden van gemeenschap
* Maatschappelijke experts
* Geprivilegieerde leden van Community Engineering
* Community Engineering Site-inhoudsbeheer

[ Aaron McDonald ](/help/communities/tutorials.md#demo-users) is een lid van

* Community-managers voor community inschakelen
* Maatschappelijke experts
* Community Engage-leden (indirect als lid van de groep Moderatoren)

![ gebruiker-groep ](assets/user-group.png)

#### https://localhost:4503/content/sites/engage/en.html {#http-localhost-content-sites-engage-en-html}

![ verbind ](assets/engage.png)

## Configureren voor verificatiefout {#configure-for-authentication-error}

Zodra een plaats is gevormd en geduwd om te publiceren, [ vormt login afbeelding ](/help/communities/sites-console.md#configure-for-authentication-error) ( `Adobe Granite Login Selector Authentication Handler`) op publiceer instantie. Het voordeel is dat wanneer de login geloofsbrieven niet correct zijn ingegaan, de authentificatiefout de login van de communautaire plaats pagina met een foutenmelding opnieuw toont.

Een `Login Page Mapping` toevoegen als

* `/content/sites/engage/en/signin:/content/sites/engage/en`

## Optionele stappen {#optional-steps}

### De standaardstartpagina wijzigen {#change-the-default-home-page}

Als u met de publicatiesite werkt voor demonstratiedoeleinden, is het handig om de standaardstartpagina te wijzigen in de nieuwe site.

Om dit te doen vereist het gebruiken van [ CRXDE ](https://localhost:4503/crx/de) Lite om de [ middel-afbeelding ](/help/sites-deploying/resource-mapping.md) lijst op uit te geven publiceren.

Aan de slag:

1. Meld u aan bij een publicatieexemplaar met beheerdersrechten.
1. Blader naar [ https://localhost:4503/crx/de ](https://localhost:4503/crx/de).
1. Vouw in de projectbrowser uit `/etc/map.`
1. Selecteer het knooppunt `http` :

   * Selecteer **Create Knoop:**

      * **Naam** localhost.4503
(gebruik *niet* &#39;:&#39;)

      * **Type** [ helling:Toewijzing ](https://sling.apache.org/documentation/the-sling-engine/mappings-for-resource-resolution.html)

1. Met nieuw gemaakt `localhost.4503` -knooppunt geselecteerd:

   * Eigenschap toevoegen:

   * **Naam** helling:gelijke
      * **Type** Koord
      * **Waarde** localhost.4503/$
(moet eindigen met &#39;$&#39; teken)

   * Eigenschap toevoegen:

      * **Naam** sling:internalRedirect
      * **Type** Koord
      * **Waarde** /content/sites/engage/en.html

1. Selecteer **sparen allen.**
1. (Optioneel) Verwijder de browsergeschiedenis.
1. Ga naar https://localhost:4503/.

   * Ga naar https://localhost:4503/content/sites/engage/en.html

>[!NOTE]
>
>Om onbruikbaar te maken, presteer eenvoudig de `sling:match` bezitswaarde met &quot;x&quot; - `xlocalhost.4503/$` - en **sparen allen**.

![ facultatief-stappen ](assets/optional-steps.png)

#### Problemen oplossen: fout bij opslaan kaart {#troubleshooting-error-saving-map}

Als u geen wijzigingen kunt opslaan, moet u ervoor zorgen dat de knooppuntnaam `localhost.4503` is, met een &#39;punt&#39;-scheidingsteken en niet `localhost:4503` met een &#39;dubbele punt&#39;-scheidingsteken, omdat `localhost` geen geldig naamruimtevoorvoegsel is.

![ fout-bericht ](assets/error-message.png)

#### Problemen oplossen: kan niet worden omgeleid {#troubleshooting-fail-to-redirect}

Het &quot;**$**&quot;aan het eind van het regelmatige uitdrukking `sling:match` koord is cruciaal, zodat slechts `https://localhost:4503/` in kaart wordt gebracht, anders wordt de omleidingswaarde vooraf bepaald aan om het even welk weg die na de server zou kunnen bestaan:haven in URL. Wanneer AEM probeert om naar de aanmeldingspagina om te leiden, mislukt dit.

### De site wijzigen {#modify-the-site}

Nadat de plaats aanvankelijk is gecreeerd, kunnen de auteurs het [ Open pictogram van de Plaats ](/help/communities/sites-console.md#authoring-site-content) gebruiken om standaard AEM auteursactiviteiten uit te voeren.

Bovendien kunnen de beheerders [ gebruiken uitgeven het pictogram van de Plaats ](/help/communities/sites-console.md#modifying-site-properties) om eigenschappen van de plaats, zoals de titel te wijzigen.

Na om het even welke wijziging, herinner aan **sparen** en re- **Publish** de plaats.

>[!NOTE]
>
>Als niet vertrouwd met AEM, bekijk de documentatie over [ basisbehandeling ](/help/sites-authoring/basic-handling.md) en a [ snelle gids aan auteurspagina&#39;s ](/help/sites-authoring/qg-page-authoring.md).
