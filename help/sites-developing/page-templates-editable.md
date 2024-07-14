---
title: Paginasjablonen - Bewerkbaar
description: Er zijn bewerkbare sjablonen geïntroduceerd waarmee niet-ontwikkelaars sjablonen kunnen maken en bewerken, sjablonen kunnen bieden die een dynamische verbinding met alle pagina's behouden die van hen zijn gemaakt, en de paginacomponent generischer kunnen maken
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
docset: aem65
exl-id: dcb66b6d-d731-493e-8936-12d529f6cbde
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '3186'
ht-degree: 0%

---

# Paginasjablonen - Bewerkbaar {#page-templates-editable}

Bewerkbare sjablonen zijn geïntroduceerd in:

* Sta gespecialiseerde auteurs toe om [ malplaatjes ](/help/sites-authoring/templates.md) tot stand te brengen en uit te geven.

   * Dergelijke gespecialiseerde auteurs worden genoemd **malplaatjeauteurs**
   * Sjabloonauteurs moeten lid zijn van de groep `template-authors` .

* Geef sjablonen op die een dynamische verbinding behouden met alle pagina&#39;s die van deze sjablonen zijn gemaakt. Zo zorgt u ervoor dat alle wijzigingen in de sjabloon worden doorgevoerd in de pagina&#39;s zelf.
* Maak de paginacomponent generischer zodat kan de kernpaginacomponent zonder aanpassing worden gebruikt.

Met bewerkbare sjablonen worden de onderdelen die een pagina maken, geïsoleerd in componenten. U kunt de noodzakelijke combinaties componenten in een UI vormen zodat u de behoefte aan een nieuwe paginacomponent elimineert die voor elke paginariatie moet worden ontwikkeld.

>[!NOTE]
>
>[ Statische malplaatjes ](/help/sites-developing/page-templates-static.md) zijn ook beschikbaar.

Dit document:

* Geeft een overzicht van het maken van bewerkbare sjablonen

   * Voor details zie [ Creërend de Malplaatjes van de Pagina ](/help/sites-authoring/templates.md)

* Beschrijft de admin/ontwikkelaarstaken die worden vereist om editable malplaatjes tot stand te brengen
* Beschrijft de technische onderbouwing van editable malplaatjes

In dit document wordt ervan uitgegaan dat u vertrouwd bent met het maken en bewerken van sjablonen. Zie het auteursdocument [ Creërend de Malplaatjes van de Pagina ](/help/sites-authoring/templates.md), die de mogelijkheden van editable malplaatjes zoals blootgesteld aan de malplaatjeauteur detailleert.

>[!NOTE]
>
>De volgende zelfstudie kan ook van belang zijn voor het instellen van een bewerkbare paginasjabloon in een nieuw project:
>[Begonnen het worden met AEM Sites Deel 2 - Creërend een Pagina en een Malplaatje van de Basis ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/project-archetype/pages-templates.html)

## Een nieuwe sjabloon maken {#creating-a-new-template}

Het creëren van editable malplaatjes wordt hoofdzakelijk gedaan met de [ malplaatjeconsole en malplaatjeredacteur ](/help/sites-authoring/templates.md) door een malplaatjeauteur. In deze paragraaf wordt een overzicht gegeven van dit proces en wordt een beschrijving gegeven van wat er op technisch niveau gebeurt.

Voor informatie over hoe te om editable malplaatjes in een AEM project te gebruiken zie [ Creërend een AEM project gebruikend Lagen ](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/create-aem-project-structure-using-lazybones/m-p/186478).

Bij het maken van een bewerkbare sjabloon:

1. Creeer a [ omslag voor de malplaatjes ](#template-folders). Deze map is niet verplicht, maar wordt aanbevolen.
1. Selecteer a [ malplaatjetype ](#template-type). Dit type wordt gekopieerd om de [ malplaatjedefinitie ](#template-definitions) tot stand te brengen.

   >[!NOTE]
   >
   >Een selectie van sjabloontypen is beschikbaar buiten het vak. U kunt ook [ uw eigen plaats-specifieke malplaatjetypes ](/help/sites-developing/page-templates-editable.md#creating-template-types) tot stand brengen, indien nodig.

1. Vorm de structuur, inhoudsbeleid, aanvankelijke inhoud, en lay-out van het nieuwe malplaatje.

   **Structuur**

   * Met de structuur kunt u componenten en inhoud voor de sjabloon definiëren.
   * Componenten die in de sjabloonstructuur zijn gedefinieerd, kunnen niet op een resulterende pagina worden verplaatst of uit resulterende pagina&#39;s worden verwijderd.

      * Als u een malplaatje in een douanemap buiten de `We.Retail` steekproefinhoud creeert, kunt u de Componenten van de Stichting kiezen of [ Componenten van de Kern gebruiken ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/overview.html).

   * Als u wilt dat auteurs van pagina&#39;s componenten kunnen toevoegen en verwijderen, voegt u een alineasysteem toe aan de sjabloon.
   * Componenten kunnen worden ontgrendeld en opnieuw worden vergrendeld, zodat u de initiële inhoud kunt definiëren.

   Voor details op hoe een malplaatjeauteur de structuur bepaalt, zie [ Creërend de Malplaatjes van de Pagina ](/help/sites-authoring/templates.md#editing-a-template-structure-template-author).

   Voor technische details van de structuur, zie [ Structuur ](/help/sites-developing/page-templates-editable.md#structure) in dit document.

   **Beleid**

   * Het inhoudsbeleid definieert de ontwerpeigenschappen van een component.

      * Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen.

   * Dit beleid is van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

   Voor details op hoe een malplaatjeauteur beleid bepaalt, zie [ Creërend de Malplaatjes van de Pagina ](/help/sites-authoring/templates.md#editing-a-template-structure-template-author).

   Voor technisch detail van beleid, zie [ Beleid van de Inhoud ](/help/sites-developing/page-templates-editable.md#content-policies) in dit document.

   **Aanvankelijke Inhoud**

   * Met Eerste inhoud wordt inhoud gedefinieerd die wordt weergegeven wanneer een pagina voor het eerst wordt gemaakt op basis van de sjabloon.
   * De initiële inhoud kan vervolgens worden bewerkt door auteurs van pagina&#39;s.

   Voor details op hoe een malplaatjeauteur de structuur bepaalt, zie [ Creërend de Malplaatjes van de Pagina ](/help/sites-authoring/templates.md#editing-a-template-initial-content-author).

   Voor technische details op aanvankelijke inhoud, zie [ Aanvankelijke Inhoud ](/help/sites-developing/page-templates-editable.md#initial-content) in dit document.

   **Lay-out**

   * U kunt de sjabloonlay-out voor een reeks apparaten definiëren.
   * De responsieve indeling voor sjablonen werkt op dezelfde manier als voor het ontwerpen van pagina&#39;s.

   Voor details op hoe een malplaatjeauteur de malplaatjelay-out bepaalt, zie [ Creërend de Malplaatjes van de Pagina ](/help/sites-authoring/templates.md#editing-a-template-layout-template-author).

   Voor technische details op malplaatjelay-out, zie [ Lay-out ](/help/sites-developing/page-templates-editable.md#layout) in dit document.

1. Schakel de sjabloon in en sta deze vervolgens toe voor specifieke inhoudstructuren.

   * U kunt een sjabloon in- of uitschakelen om de sjabloon beschikbaar of niet beschikbaar te maken voor auteurs van pagina&#39;s.
   * Een sjabloon kan beschikbaar worden gesteld of niet beschikbaar zijn voor bepaalde paginasvertakkingen.

   Voor details op hoe een malplaatjeauteur een malplaatje toelaat, zie [ Creërend de Malplaatjes van de Pagina ](/help/sites-authoring/templates.md#enabling-and-allowing-a-template-template-author).

   Voor technische details bij het toelaten van een malplaatje, zie [ Toelatend en Toestaan een Malplaatje voor Gebruik ](/help/sites-developing/page-templates-editable.md#enabling-and-allowing-a-template-for-use) e in dit document

1. Gebruik dit besturingselement om inhoudspagina&#39;s te maken.

   * Wanneer u een sjabloon gebruikt om een pagina te maken, is er geen zichtbaar verschil en is er geen indicatie tussen statische en bewerkbare sjablonen.
   * Voor de auteur van de pagina is het proces transparant.

   Voor details op hoe een paginaauteur malplaatjes gebruikt om een pagina tot stand te brengen, zie [ Creërend en Organiserend Pagina&#39;s ](/help/sites-authoring/managing-pages.md#templates).

   Voor technische details bij het creëren van pagina&#39;s met editable malplaatjes, zie [ Resulterende Pagina&#39;s van de Inhoud ](/help/sites-developing/page-templates-editable.md#resultant-content-pages) in dit document.

>[!TIP]
>
>Voer nooit informatie in die geïnternationaliseerd moet worden in een sjabloon. Voor internaliseringsdoeleinden, wordt de [ lokalisatieeigenschap van de Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html) geadviseerd.

>[!NOTE]
>
>Sjablonen zijn krachtige gereedschappen om de workflow voor het maken van pagina&#39;s te stroomlijnen. Te veel sjablonen kunnen de auteurs echter overweldigen en tot verwarring bij het maken van pagina&#39;s leiden. Een goede regel is om het aantal sjablonen onder de 100 te houden.
>
>Adobe raadt niet aan meer dan 1000 sjablonen te hebben vanwege mogelijke gevolgen voor de prestaties.

>[!NOTE]
>
>In de clientbibliotheek van de editor wordt ervan uitgegaan dat de naamruimte `cq.shared` aanwezig is in inhoudspagina&#39;s. Als deze ontbreekt, resulteert dit in de JavaScript-fout `Uncaught TypeError: Cannot read property 'shared' of undefined` .
>
>Alle pagina&#39;s met voorbeeldinhoud bevatten `cq.shared` , dus alle inhoud die hierop is gebaseerd, bevat automatisch `cq.shared` . Als u echter besluit uw eigen inhoudspagina&#39;s helemaal zelf te maken zonder deze te baseren op voorbeeldinhoud, moet u de naamruimte `cq.shared` wel invoegen.
>
>Zie [ Gebruikend Cliënt-Kant Bibliotheken ](/help/sites-developing/clientlibs.md) voor verdere informatie.

## Sjabloonmappen {#template-folders}

Voor het organiseren van uw sjablonen kunt u de volgende mappen gebruiken:

* **globaal**
* Sitespecifiek
De sitespecifieke mappen die u maakt om uw sjablonen te organiseren, worden gemaakt met beheerdersrechten voor accounts.

>[!NOTE]
>
>Alhoewel u uw omslagen kunt nesten, wanneer de gebruiker hen in de **console van Malplaatjes** bekijkt worden zij voorgesteld als vlakke structuur.

In een standaard AEM instantie, bestaat de **globale** omslag in de malplaatjeconsole. Deze map bevat standaardsjablonen en fungeert als fallback als er geen beleid en/of sjabloontypen in de huidige map zijn gevonden. U kunt uw standaardsjablonen toevoegen aan deze map of een map maken (aanbevolen).

>[!NOTE]
>
>Het wordt aanbevolen een map te maken waarin u uw aangepaste sjablonen kunt opslaan en niet de algemene map te gebruiken.

>[!CAUTION]
>
>Mappen moeten worden gemaakt door een gebruiker met `admin` -rechten.

Sjabloontypen en beleid worden in alle mappen overgeërfd volgens de volgende prioriteitsvolgorde:

1. De huidige map.
1. Bovenliggend item of bovenliggende items van de huidige map.
1. `/conf/global`
1. `/apps`
1. `/libs`

Er wordt een lijst met alle toegestane vermeldingen gemaakt. Als configuraties elkaar overlappen ( `path`/ `label` ), wordt alleen de instantie die zich het dichtst bij de huidige map bevindt, aan de gebruiker getoond.

Ga als volgt te werk om een map te maken:

* Programmaticaal of met CRXDE Lite
* De configuratiebrowser gebruiken

## CRXDE Lite gebruiken {#using-crxde-lite}

1. Een nieuwe omslag (onder /conf) kan voor uw instantie of programmatically of met CRXDE Lite worden gecreeerd.

   De volgende structuur moet worden gebruikt:

   ```xml
   /conf
       <your-folder-name> [sling:Folder]
           settings [sling:Folder]
               wcm [cq:Page]
                   templates [cq:Page]
                   policies [cq:Page]
   ```

1. Vervolgens kunt u de volgende eigenschappen definiëren voor het hoofdknooppunt van de map:

   `<your-folder-name> [sling:Folder]`

   Naam: `jcr:title`

   * Type: `String`

   * Waarde: De titel (voor de omslag) u in de **console van Malplaatjes** wilt verschijnen.

1. In *toevoeging* aan de standaard auteurstoestemmingen en voorrechten (bijvoorbeeld, `content-authors`), wijs groepen toe en bepaal de vereiste toegangsrechten (ACLs) voor uw auteurs om malplaatjes in de nieuwe omslag te kunnen tot stand brengen.

   De `template-authors` -groep is de standaardgroep die moet worden toegewezen. Zie de volgende sectie [ ACLs en Groepen ](/help/sites-developing/page-templates-editable.md#acls-and-groups) voor details.

   Zie ](/help/sites-administering/user-group-ac-admin.md#access-right-management) het Rechterbeheer van de Toegang [ voor volledige details bij het beheren van en het toewijzen van toegangsrechten.

### De configuratiebrowser gebruiken {#using-the-configuration-browser}

1. Ga naar **Globale Navigatie** > **Hulpmiddelen** > **Browser van de Configuratie**.

   De bestaande omslagen worden vermeld aan de linkerzijde met inbegrip van de **globale** omslag.

1. Klik **creëren**.
1. In **creeer de dialoog van de Configuratie**, moeten de volgende gebieden worden gevormd:

   * **Titel**: Verstrek een titel voor de configuratiemap
   * **Bewerkbare Malplaatjes**: Uitgezocht om voor editable malplaatjes binnen deze omslag toe te staan

1. Klik **creëren**

>[!NOTE]
>
>In Browser van de Configuratie, kunt u de globale omslag uitgeven en de **Bewerkbare optie van Malplaatjes** activeren als u malplaatjes binnen deze omslag wilt tot stand brengen. Dit is echter geen aanbevolen beste praktijk.
>
>Zie Browser van de Configuratie ](/help/sites-administering/configurations.md) documentatie 0} {voor meer informatie.[

### ACLs en Groepen {#acls-and-groups}

Nadat uw malplaatjeomslagen (of als CRXDE of met Browser van de Configuratie) worden gecreeerd, moet ACLs voor de aangewezen groepen voor de malplaatjeomslagen worden bepaald om juiste veiligheid te verzekeren.

De malplaatjeomslagen voor de [`We.Retail` verwijzingsimplementatie ](/help/sites-developing/we-retail.md) kunnen als voorbeeld worden gebruikt.

#### De groep sjabloonauteurs {#the-template-authors-group}

De `template-authors` -groep is de groep die wordt gebruikt om toegang tot sjablonen te beheren en wordt standaard met AEM geleverd, maar is leeg. Gebruikers moeten worden toegevoegd aan de groep voor het project of de site.

>[!CAUTION]
>
>De `template-authors` groep is *slechts* voor gebruikers die malplaatjes moeten kunnen tot stand brengen.
>
>Het bewerken van sjablonen is krachtig en als dit niet correct gebeurt, kunnen bestaande sjablonen worden afgebroken. Daarom moet deze rol worden toegespitst en alleen gekwalificeerde gebruikers omvatten.

In de volgende tabel worden de benodigde machtigingen voor sjabloonbewerking weergegeven.

<table>
 <tbody>
  <tr>
   <th>Pad</th>
   <th>Rol/groep</th>
   <th>Machtigingen <br /> </th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/templates</code></td>
   <td>Sjabloonauteurs <br /> </td>
   <td>lezen, schrijven, repliceren</td>
   <td>Sjabloonauteurs die sjablonen maken, lezen, bijwerken, verwijderen en repliceren in sitespecifieke <code>/conf</code> ruimte</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>lezen</td>
   <td>De anonieme Gebruiker van het Web moet malplaatjes lezen terwijl het teruggeven van een pagina</td>
  </tr>
  <tr>
   <td>Inhoudsauteurs</td>
   <td>repliceren</td>
   <td>ReplicateContent-auteurs moeten de sjablonen van een pagina activeren wanneer ze een pagina activeren</td>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/policies</code></td>
   <td><code>Template Author</code></td>
   <td>lezen, schrijven, repliceren</td>
   <td>Sjabloonauteurs die sjablonen maken, lezen, bijwerken, verwijderen en repliceren in sitespecifieke <code>/conf</code> ruimte</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>lezen</td>
   <td>De anonieme Gebruiker van het Web moet beleid lezen terwijl het teruggeven van een pagina</td>
  </tr>
  <tr>
   <td>Inhoudsauteurs</td>
   <td>repliceren</td>
   <td>Inhoudsauteurs moeten het beleid van een sjabloon van een pagina activeren wanneer ze een pagina activeren</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/&lt;site&gt;/settings/template-types</code></td>
   <td>Sjabloonauteur</td>
   <td>lezen</td>
   <td>Sjabloonauteur maakt een sjabloon op basis van een van de vooraf gedefinieerde sjabloontypen.</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>none</td>
   <td>De anonieme Gebruiker van het Web moet tot de malplaatjetypes niet toegang hebben</td>
  </tr>
 </tbody>
</table>

Deze standaardgroep `template-authors` geldt alleen voor de projectinstellingen, waarbij alle `template-authors` -leden toegang hebben tot alle sjablonen en deze mogen samenstellen. Voor complexere montages, waar er een behoefte aan veelvoudige groepen van malplaatjeauteurs is om toegang tot malplaatjes te scheiden, moeten meer de auteursgroepen van het douanemalplaatje worden gecreeerd. De machtigingen voor de groepen sjabloonauteurs zijn echter nog steeds hetzelfde.

#### Oudere sjablonen onder /conf/global {#legacy-templates-under-conf-global}

Sjablonen niet opslaan in `/conf/global` . Voor sommige oude installaties zijn er echter nog sjablonen op deze locatie. *slechts* in dergelijke erfenissituaties zou de volgende `/conf/global` wegen uitdrukkelijk moeten worden gevormd.

<table>
 <tbody>
  <tr>
   <th>Pad</th>
   <th>Rol/groep</th>
   <th>Machtigingen <br /> </th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/global/settings/wcm/templates</code></td>
   <td>Sjabloonauteurs</td>
   <td>lezen, schrijven, repliceren</td>
   <td>Sjabloonauteurs die sjablonen maken, lezen, bijwerken, verwijderen en repliceren in <code>/conf/global</code></td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>lezen</td>
   <td>De anonieme Gebruiker van het Web moet malplaatjes lezen terwijl het teruggeven van een pagina</td>
  </tr>
  <tr>
   <td>Inhoudsauteurs</td>
   <td>repliceren</td>
   <td>Inhoudsauteurs moeten de sjablonen van een pagina activeren wanneer ze een pagina activeren</td>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/global/settings/wcm/policies</code></td>
   <td><code>Template Author</code></td>
   <td>lezen, schrijven, repliceren</td>
   <td>Sjabloonauteurs die sjablonen maken, lezen, bijwerken, verwijderen en repliceren in <code>/conf/global</code></td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>lezen</td>
   <td>De anonieme Gebruiker van het Web moet beleid lezen terwijl het teruggeven van een pagina</td>
  </tr>
  <tr>
   <td>Inhoudsauteurs</td>
   <td>repliceren</td>
   <td>Inhoudsauteurs moeten het beleid van een sjabloon van een pagina activeren wanneer ze een pagina activeren</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/global/settings/wcm/template-types</code></td>
   <td>Sjabloonauteur</td>
   <td>lezen</td>
   <td>Sjabloonauteur maakt een sjabloon op basis van een vooraf gedefinieerd sjabloontype</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>none</td>
   <td>De anonieme Gebruiker van het Web moet tot de malplaatjetypes niet toegang hebben</td>
  </tr>
 </tbody>
</table>

## Sjabloontype {#template-type}

Geef een sjabloontype op wanneer u een sjabloon maakt:

* Sjabloontypen bieden sjablonen voor een sjabloon. Wanneer u een sjabloon maakt, worden de structuur en initiële inhoud van het geselecteerde sjabloontype gebruikt om de sjabloon te maken.

   * Het sjabloontype wordt gekopieerd om de sjabloon te maken.
   * Zodra het exemplaar is voorgekomen, is de enige verbinding tussen het malplaatje en het malplaatjetype een statische verwijzing voor informatiedoeleinden.

* Met sjabloontypen kunt u definiëren:

   * Het middeltype van de paginacomponent.
   * Het beleid van de wortelknoop, die de componenten bepaalt die in de malplaatjeredacteur worden toegestaan.
   * Adobe raadt u aan de onderbrekingspunten voor het responsieve raster en de instelling van de mobiele emulator op te geven voor het sjabloontype. Deze stap is facultatief, omdat de configuratie ook op het individuele malplaatje (zie [ het Type van Malplaatje en Mobiele Groepen van het Apparaat ](/help/sites-developing/page-templates-editable.md#p-template-type-and-mobile-device-groups-br-p)) kon worden bepaald.

* AEM biedt een kleine selectie van sjabloontypen die buiten het vak vallen, zoals HTML5 Pagina en Aangepaste formulierpagina.

   * Extra voorbeelden worden gegeven als onderdeel van de voorbeeldinhoud van [`We.Retail`](/help/sites-developing/we-retail.md) .

* Sjabloontypen worden meestal gedefinieerd door ontwikkelaars.

De sjabloontypen voor de out-of-the-box worden opgeslagen onder:

* `/libs/settings/wcm/template-types`

>[!CAUTION]
>
>Wijzig niets in het `/libs` -pad. De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van uw exemplaar, wordt overschreven (en dat deze kan worden overschreven wanneer u een hotfix- of functiepakket toepast).

Uw sitespecifieke sjabloontypen moeten worden opgeslagen op de vergelijkbare locatie:

* `/apps/settings/wcm/template-types`

Definities voor uw aangepaste sjabloontypen moeten worden opgeslagen in door de gebruiker gedefinieerde mappen (aanbevolen) of anders in `global` . Bijvoorbeeld:

* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/template-types`
* `/conf/<my-folder>/settings/wcm/template-types`
* `/conf/global/settings/wcm/template-types`

>[!CAUTION]
>
>De sjabloontypen moeten de juiste mapstructuur (dat wil zeggen `/settings/wcm/...` ) in acht nemen, anders worden de sjabloontypen niet gevonden.

### Sjabloontype en mobiele apparaatgroepen {#template-type-and-mobile-device-groups-br}

De [ apparatengroepen ](/help/sites-developing/mobile.md#device-groups) die voor een editable malplaatje (geplaatst als relatieve weg van het bezit `cq:deviceGroups`) worden gebruikt bepalen welke mobiele apparaten als mededingers op de [ lay-outwijze ](/help/sites-authoring/responsive-layout.md) van paginaontwerp beschikbaar zijn. Deze waarde kan op twee plaatsen worden ingesteld:

* Op het bewerkbare sjabloontype
* Op de bewerkbare sjabloon

Wanneer u een bewerkbare sjabloon maakt, wordt de waarde van het sjabloontype naar de afzonderlijke sjabloon gekopieerd. Als de waarde niet op het type is ingesteld, kan deze in de sjabloon worden ingesteld. Als een sjabloon eenmaal is gemaakt, is er geen overerving van het type naar de sjabloon.

>[!CAUTION]
>
>De waarde van `cq:deviceGroups` moet worden ingesteld als een relatief pad, zoals `mobile/groups/responsive` , en niet als een absoluut pad, zoals `/etc/mobile/groups/responsive` .

>[!NOTE]
>
>Met [ statische malplaatjes ](/help/sites-developing/page-templates-static.md), zou de waarde van `cq:deviceGroups` bij de wortel van de plaats kunnen worden geplaatst.
>
>Met bewerkbare sjablonen wordt deze waarde nu opgeslagen op sjabloonniveau en wordt deze niet ondersteund op hoofdniveau van de pagina.

### Sjabloontypen maken {#creating-template-types}

Als u een sjabloon hebt gemaakt die als basis voor andere sjablonen kan dienen, kunt u deze sjabloon kopiëren als een sjabloontype.

1. Creeer een malplaatje zoals u om het even welk editable malplaatje [ zoals hier gedocumenteerd ](/help/sites-authoring/templates.md#creating-a-new-template-template-author), dat als basis van uw malplaatjetype kan dienen.
1. Gebruikend CRXDE Lite, kopieer het onlangs gecreeerde malplaatje van de `templates` knoop aan de `template-types` knoop onder de [ malplaatjeomslag ](/help/sites-developing/page-templates-editable.md#template-folders).
1. Schrap het malplaatje van de `templates` knoop onder de [ malplaatjeomslag ](/help/sites-developing/page-templates-editable.md#template-folders).
1. Verwijder in de kopie van de sjabloon onder het knooppunt `template-types` alle eigenschappen `cq:template` en `cq:templateType` uit alle `jcr:content` knooppunten.

U kunt uw eigen malplaatjetype ook ontwikkelen gebruikend een voorbeeld editable malplaatje als basis, beschikbaar op GitHub.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [ open a-sites-example-custom-template-type project op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type)
* Download het project als [ een dossier van het PIT ](https://codeload.github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type/zip/refs/heads/master)

## Sjabloondefinities {#template-definitions}

De definities voor editable malplaatjes worden opgeslagen [ user-defined omslagen ](/help/sites-developing/page-templates-editable.md#template-folders) (geadviseerd) of alternatief in `global`. Bijvoorbeeld:

* `/conf/<my-folder>/settings/wcm/templates`
* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/templates`
* `/conf/global/settings/wcm/templates`

Het hoofdknooppunt van de sjabloon is van het type `cq:Template` met een skeletstructuur van:

```xml
<template-name>
  initial
    jcr:content
      root
        <component>
        ...
        <component>
  jcr:content
    @property status
  policies
    jcr:content
      root
        @property cq:policy
        <component>
          @property cq:policy
        ...
        <component>
          @property cq:policy
  structure
    jcr:content
      root
        <component>
        ...
        <component>
      cq:responsive
        breakpoints
  thumbnail.png
```

De belangrijkste elementen zijn:

* `<template-name>`

   * ` [initial](#initial-content)`
   * `jcr:content`
   * ` [structure](#structure)`
   * ` [policies](#policies)`
   * `thumbnail.png`

### jcr:inhoud {#jcr-content}

Dit knooppunt bevat eigenschappen voor de sjabloon:

* **Naam**: `jcr:title`

* **Naam**: `status`

   * **Type**: `String`

   * **Waarde**: `draft`, `enabled`, of `disabled`

### Structuur {#structure}

Hiermee definieert u de structuur van de resulterende pagina:

* Wordt bij het maken van een pagina samengevoegd met de oorspronkelijke inhoud ( `/initial` ).
* Wijzigingen in de structuur worden weerspiegeld in alle pagina&#39;s die met de sjabloon zijn gemaakt.
* Het knooppunt `root` ( `structure/jcr:content/root` ) definieert de lijst met componenten die beschikbaar zijn op de resulterende pagina.

   * Componenten die zijn gedefinieerd in de sjabloonstructuur kunnen niet worden verplaatst op of verwijderd van resulterende pagina&#39;s.
   * Nadat een component is ontgrendeld, wordt de eigenschap `editable` ingesteld op `true` .

   * Nadat een component die al inhoud bevat, is ontgrendeld, wordt deze inhoud naar de `initial` -vertakking verplaatst.

* Het knooppunt `cq:responsive` bevat definities voor de responsieve indeling.

### Oorspronkelijke inhoud {#initial-content}

Definieert de eerste inhoud van een nieuwe pagina bij het maken:

* Bevat een knooppunt `jcr:content` dat naar nieuwe pagina&#39;s wordt gekopieerd.
* Wordt bij het maken van een pagina samengevoegd met de structuur ( `/structure` ).
* Bestaande pagina&#39;s worden bijgewerkt als de oorspronkelijke inhoud na het maken wordt gewijzigd.
* Het knooppunt `root` bevat een lijst met componenten om te definiëren wat beschikbaar is op de resulterende pagina.
* Als er inhoud wordt toegevoegd aan een component in de structuurmodus en die component later wordt ontgrendeld (of omgekeerd), wordt deze inhoud gebruikt als initiële inhoud.

### Layout {#layout}

Wanneer [ het uitgeven van een malplaatje, u de lay-out ](/help/sites-authoring/templates.md) kunt bepalen, gebruikt deze praktijk [ standaard ontvankelijke lay-out ](/help/sites-authoring/responsive-layout.md) die ook [ kan worden gevormd ](/help/sites-administering/configuring-responsive-layout.md).

### Inhoudsbeleid {#content-policies}

Het inhoudsbeleid (of het ontwerpbeleid) definieert de ontwerpeigenschappen van een component, zoals de beschikbaarheid van de component of de minimum-/maximumafmetingen. Dit beleid is van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt). Het inhoudsbeleid kan worden gemaakt en geselecteerd in de sjablooneditor.

* De eigenschap `cq:policy` op het knooppunt `root`
  `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/root`
Verstrekt een relatieve verwijzing naar het inhoudsbeleid voor het de paragraafsysteem van de pagina.

* De eigenschap `cq:policy` biedt op de componentexpliciete knooppunten onder `root` koppelingen naar het beleid voor de afzonderlijke componenten.

* De feitelijke beleidsdefinities worden opgeslagen onder:
  `/conf/<your-folder>/settings/wcm/policies/wcm/foundation/components`

>[!NOTE]
>
>De paden van beleidsdefinities zijn afhankelijk van het pad van de component. `cq:policy` bevat een relatieve verwijzing naar de configuratie zelf.

>[!NOTE]
>
>Op basis van bewerkbare sjablonen gemaakte pagina&#39;s beschikken niet over een ontwerpmodus in de pagina-editor.
>
>De `policies` -structuur van een bewerkbare sjabloon heeft dezelfde hiërarchie als de ontwerpmodusconfiguratie van een statische sjabloon onder:
>
>`/etc/designs/<my-site>/jcr:content/<component-name>`
>
>De ontwerpmodusconfiguratie van een statische sjabloon is gedefinieerd per paginacomponent.

### Paginabeleid {#page-policies}

Het beleid van de pagina laat u het [ inhoudsbeleid ](#content-policies) voor de pagina (belangrijkste parsys), in of het malplaatje of de resulterende pagina&#39;s bepalen.

### Een sjabloon inschakelen en toestaan voor gebruik {#enabling-and-allowing-a-template-for-use}

1. **laat het Malplaatje** toe

   Voordat een sjabloon kan worden gebruikt, moet deze zijn ingeschakeld door:

   * [ toelatend het malplaatje ](/help/sites-authoring/templates.md#enablingatemplateauthor) van de **console van Malplaatjes**.

   * Setting the status property on the `jcr:content` node.

      * Bijvoorbeeld op:
        `/conf/<your-folder>/settings/wcm/templates/<your-template>/jcr:content`

      * Definieer de eigenschap:

         * Naam: status
         * Type: String
         * Waarde: `enabled`

1. **Toegestane Malplaatjes**

   * [ bepaalt de Toegestane wegen van het Malplaatje op de **Eigenschappen van de Pagina**](/help/sites-authoring/templates.md#allowing-a-template-author) van de aangewezen pagina of wortelpagina van een subtak.
   * Stel de eigenschap in:
     `cq:allowedTemplates`
Op het `jcr:content` -knooppunt van de vereiste vertakking.

   Bijvoorbeeld met een waarde van:

   `/conf/<your-folder>/settings/wcm/templates/.*`

## Resulterende inhoudspagina&#39;s {#resultant-content-pages}

Pagina&#39;s gemaakt op basis van bewerkbare sjablonen:

* Wordt gemaakt met een substructuur die wordt samengevoegd van `structure` en `initial` in de sjabloon

* Verwijzingen hebben naar in de template opgeslagen informatie en naar het sjabloontype. U kunt deze functionaliteit bereiken met een knooppunt `jcr:content` met de eigenschappen:

   * `cq:template`
Verstrekt de dynamische verwijzing naar het daadwerkelijke malplaatje; laat toe dat veranderingen in het malplaatje worden weerspiegeld op de daadwerkelijke pagina&#39;s.

   * `cq:templateType`
Verstrekt een verwijzing naar het malplaatjetype.

![ chlimage_1-71 ](assets/chlimage_1-71.png)

In het bovenstaande diagram ziet u hoe sjablonen, inhoud en componenten met elkaar verweven zijn:

* Controller - `/content/<my-site>/<my-page>`
De resulterende pagina die naar de sjabloon verwijst. De inhoud bepaalt het gehele proces. Volgens de definities heeft het toegang tot de toepasselijke sjabloon en componenten.

* Configuratie - `/conf/<my-folder>/settings/wcm/templates/<my-template>`
Het [ malplaatje en verwante inhoudsbeleid ](#template-definitions) bepalen de paginasonfiguratie.

* Model - OSGi-pakketten
De [ bundels OSGI ](/help/sites-deploying/osgi-configuration-settings.md) voeren de functionaliteit uit.

* Weergeven - `/apps/<my-site>/components`
Op zowel de auteur als publiceert milieu&#39;s, wordt de inhoud teruggegeven door [ componenten ](/help/sites-developing/components.md).

Bij het weergeven van een pagina:

* **Malplaatjes**:

   * De eigenschap `cq:template` van het knooppunt `jcr:content` wordt gebruikt voor toegang tot de sjabloon die overeenkomt met die pagina.

* **Componenten**:

   * De paginacomponent voegt de `structure/jcr:content` -structuur van de sjabloon samen met de `jcr:content` -structuur van de pagina.

   * Met de paginacomponent kan de auteur alleen de knooppunten van de sjabloonstructuur bewerken die als bewerkbaar zijn gemarkeerd (en eventuele onderliggende knooppunten).
   * Wanneer u een component op een pagina rendert, wordt het relatieve pad van die component opgehaald uit het knooppunt `jcr:content` . Vervolgens wordt hetzelfde pad onder het knooppunt `policies/jcr:content` van de sjabloon doorzocht.

      * De eigenschap `cq:policy` van dit knooppunt verwijst naar het daadwerkelijke inhoudsbeleid (dat wil zeggen dat het de ontwerpconfiguratie voor die component bevat).

      * Deze functionaliteit laat u veelvoudige malplaatjes hebben die de zelfde configuraties van het inhoudsbeleid opnieuw gebruiken.
