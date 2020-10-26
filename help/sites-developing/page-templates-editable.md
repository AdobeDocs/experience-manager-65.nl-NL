---
title: Paginasjablonen - Bewerkbaar
seo-title: Paginasjablonen - Bewerkbaar
description: Bewerkbare sjablonen zijn geïntroduceerd om, niet-ontwikkelaars toe te staan sjablonen te maken en te bewerken, sjablonen op te geven die een dynamische verbinding met alle pagina's behouden die van hen zijn gemaakt, en de paginacomponent generischer te maken
seo-description: Bewerkbare sjablonen zijn geïntroduceerd om, niet-ontwikkelaars toe te staan sjablonen te maken en te bewerken, sjablonen op te geven die een dynamische verbinding met alle pagina's behouden die van hen zijn gemaakt, en de paginacomponent generischer te maken
uuid: 61791960-fdef-4e49-878a-11fdf1d4f0ab
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 1099cc44-de6d-499e-8b52-f2f5811ae086
docset: aem65
translation-type: tm+mt
source-git-commit: ce64b148ba96cc64670aaf96c1b201bafa282b98
workflow-type: tm+mt
source-wordcount: '3218'
ht-degree: 0%

---


# Paginasjablonen - Bewerkbaar {#page-templates-editable}

Bewerkbare sjablonen zijn geïntroduceerd in:

* Sta gespecialiseerde auteurs toe om malplaatjes [te](/help/sites-authoring/templates.md)creëren en uit te geven.

   * Dergelijke gespecialiseerde auteurs worden **sjabloonauteurs genoemd**
   * Sjabloonauteurs moeten lid zijn van de `template-authors` groep.

* Geef sjablonen op die een dynamische verbinding behouden met alle pagina&#39;s die van deze sjablonen zijn gemaakt. Zo zorgt u ervoor dat wijzigingen in de sjabloon ook op de pagina&#39;s zelf worden doorgevoerd.
* Maak de paginacomponent generischer zodat kan de kernpaginacomponent zonder aanpassing worden gebruikt.

Met bewerkbare sjablonen worden de onderdelen die een pagina maken, geïsoleerd in componenten. U kunt de noodzakelijke combinaties componenten in een UI vormen, daardoor eliminerend de behoefte aan een nieuwe paginacomponent die voor elke paginariatie moet worden ontwikkeld.

>[!NOTE]
>
>[Statische sjablonen](/help/sites-developing/page-templates-static.md) zijn ook beschikbaar.

Dit document:

* Geeft een overzicht van het maken van bewerkbare sjablonen

   * Zie Paginasjablonen [maken voor meer informatie](/help/sites-authoring/templates.md)

* Beschrijft de admin/ontwikkelaarstaken die worden vereist om editable malplaatjes tot stand te brengen
* Beschrijft de technische onderbouwing van editable malplaatjes

In dit document wordt ervan uitgegaan dat u vertrouwd bent met het maken en bewerken van sjablonen. Zie het ontwerpdocument [Creating Page Templates](/help/sites-authoring/templates.md), waarin de mogelijkheden van bewerkbare sjablonen worden beschreven zoals deze aan de sjabloonauteur worden getoond.

>[!NOTE]
>
>De volgende zelfstudie kan ook van belang zijn voor het instellen van een bewerkbare paginasjabloon in een nieuw project:
>[Aan de slag met AEM Sites Deel 2 - Een basispagina en sjabloon maken](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part2.html)

## Creating a New Template {#creating-a-new-template}

Het creëren van editable malplaatjes wordt hoofdzakelijk gedaan met de [malplaatjeconsole en malplaatjeredacteur](/help/sites-authoring/templates.md) door een malplaatjeauteur. In deze paragraaf wordt een overzicht gegeven van dit proces en wordt een beschrijving gegeven van wat er op technisch niveau gebeurt.

Voor informatie over hoe te om editable malplaatjes in een AEM project te gebruiken zie het [Creëren van een AEM project gebruikend Lzybones](https://helpx.adobe.com/experience-manager/using/aem_lazybones.html).

Bij het maken van een nieuwe bewerkbare sjabloon:

1. Maak een [map voor de sjablonen](#template-folders). Dit is niet verplicht, maar aanbevolen beste praktijken.
1. Selecteer een [sjabloontype](#template-type). Deze wordt gekopieerd om de [sjabloondefinitie](#template-definitions)te maken.

   >[!NOTE]
   >
   >Een selectie van sjabloontypen is beschikbaar buiten het vak. U kunt desgewenst ook uw eigen sitespecifieke sjabloontypen [](/help/sites-developing/page-templates-editable.md#creating-template-types) maken.

1. Vorm de structuur, inhoudsbeleid, aanvankelijke inhoud, en lay-out van het nieuwe malplaatje.

   **Structuur**

   * Met de structuur kunt u componenten en inhoud voor de sjabloon definiëren.
   * Componenten die in de sjabloonstructuur zijn gedefinieerd, kunnen niet op een resulterende pagina worden verplaatst of uit resulterende pagina&#39;s worden verwijderd.

      * Als u een malplaatje in een douanemap buiten de wij.Retail steekproefinhoud creeert, kunt u de Componenten van de Stichting kiezen of de Componenten [van de](https://helpx.adobe.com/experience-manager/core-components/using/developing.html)Kern gebruiken.
   * Als u wilt dat auteurs van pagina&#39;s componenten kunnen toevoegen en verwijderen, voegt u een alineasysteem toe aan de sjabloon.
   * Componenten kunnen worden ontgrendeld en opnieuw worden vergrendeld, zodat u de initiële inhoud kunt definiëren.

   Zie [Paginasjablonen](/help/sites-authoring/templates.md#editing-a-template-structure-template-author)maken voor meer informatie over de manier waarop de sjabloonauteur de structuur definieert.

   Zie [Structuur](/help/sites-developing/page-templates-editable.md#structure) in dit document voor technische details over de structuur.

   **Beleid**

   * Het inhoudsbeleid definieert de ontwerpeigenschappen van een component.

      * Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen.
   * Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

   Zie [Paginasjablonen](/help/sites-authoring/templates.md#editing-a-template-structure-template-author)maken voor meer informatie over de manier waarop sjabloonauteur beleid definieert.

   Zie [Inhoudsbeleid](/help/sites-developing/page-templates-editable.md#content-policies) in dit document voor technische details over het beleid.

   **Oorspronkelijke inhoud**

   * Met Eerste inhoud wordt inhoud gedefinieerd die wordt weergegeven wanneer een pagina voor het eerst wordt gemaakt op basis van de sjabloon.
   * De initiële inhoud kan vervolgens worden bewerkt door auteurs van pagina&#39;s.

   Zie [Paginasjablonen](/help/sites-authoring/templates.md#editing-a-template-initial-content-author)maken voor meer informatie over de manier waarop de sjabloonauteur de structuur definieert.

   Zie [Initiële inhoud](/help/sites-developing/page-templates-editable.md#initial-content) in dit document voor technische details over de initiële inhoud.

   **Indeling**

   * U kunt de sjabloonlay-out voor een reeks apparaten definiëren.
   * De responsieve indeling voor sjablonen werkt op dezelfde manier als voor het ontwerpen van pagina&#39;s.

   Zie [Paginasjablonen](/help/sites-authoring/templates.md#editing-a-template-layout-template-author)maken voor meer informatie over de manier waarop de sjabloonindeling door de sjabloonauteur wordt gedefinieerd.

   Zie [Lay-out](/help/sites-developing/page-templates-editable.md#layout) in dit document voor technische details over de sjabloonlay-out.

1. Schakel de sjabloon in en sta deze vervolgens toe voor specifieke inhoudstructuren.

   * U kunt een sjabloon in- of uitschakelen om de sjabloon beschikbaar of niet beschikbaar te maken voor auteurs van pagina&#39;s.
   * Een sjabloon kan beschikbaar worden gesteld of niet beschikbaar zijn voor bepaalde paginasvertakkingen.

   Zie [Paginasjablonen](/help/sites-authoring/templates.md#enabling-and-allowing-a-template-template-author)maken voor meer informatie over de manier waarop een sjabloonauteur een sjabloon inschakelt.

   Voor technische details bij het toelaten van een malplaatje, zie het [Toelaten van en het Toestaan van een Malplaatje voor](/help/sites-developing/page-templates-editable.md#enabling-and-allowing-a-template-for-use)Gebruik in dit document

1. Gebruik dit besturingselement om inhoudspagina&#39;s te maken.

   * Wanneer u een sjabloon gebruikt om een nieuwe pagina te maken, is er geen zichtbaar verschil en is er geen indicatie tussen statische en bewerkbare sjablonen.
   * Voor de auteur van de pagina is het proces transparant.

   Zie Pagina&#39;s [maken en ordenen voor meer informatie over hoe een auteur van een pagina sjablonen gebruikt om een pagina te maken](/help/sites-authoring/managing-pages.md#templates).

   Zie [Resulterende inhoudspagina&#39;s in dit document voor technische details over het maken van pagina&#39;s met bewerkbare sjablonen](/help/sites-developing/page-templates-editable.md#resultant-content-pages) .

>[!NOTE]
>
>In de clientbibliotheek van de editor wordt ervan uitgegaan dat de `cq.shared` naamruimte aanwezig is op de inhoudspagina&#39;s. Als deze ontbreekt, `Uncaught TypeError: Cannot read property 'shared' of undefined` treedt de JavaScript-fout op.
>
>Alle pagina&#39;s met voorbeeldinhoud bevatten `cq.shared`dus alle inhoud die hierop is gebaseerd, bevat automatisch `cq.shared`. Als u echter besluit uw eigen inhoudspagina&#39;s helemaal zelf te maken zonder deze te baseren op voorbeeldinhoud, moet u de `cq.shared` naamruimte ook opnemen.
>
>Zie [Client-Side Libraries](/help/sites-developing/clientlibs.md) gebruiken voor meer informatie.

>[!CAUTION]
>
>Voer nooit informatie in die u wilt [internationaliseren](/help/sites-developing/i18n.md) in een sjabloon.

## Sjabloonmappen {#template-folders}

Voor het organiseren van uw sjablonen kunt u de volgende mappen gebruiken:

* **global**
* SitespecifiekDe sitespecifieke mappen die u maakt om uw sjablonen te organiseren, worden gemaakt met beheerdersrechten voor een account.

>[!NOTE]
>
>Hoewel u uw omslagen kunt nesten, wanneer de gebruiker hen in de console van **Malplaatjes** bekijkt worden zij voorgesteld als vlakke structuur.

In een standaard AEM bestaat de **algemene** map al in de sjabloonconsole. Dit houdt standaardmalplaatjes vast en doet dienst als reserve als geen beleid en/of malplaatje-types in de huidige omslag worden gevonden. U kunt uw standaardsjablonen toevoegen aan deze map of een nieuwe map maken (aanbevolen).

>[!NOTE]
>
>Het wordt aanbevolen een nieuwe map te maken waarin u uw aangepaste sjablonen kunt opslaan en niet de algemene map te gebruiken.

>[!CAUTION]
>
>Mappen moeten worden gemaakt door een gebruiker met `admin` rechten.

Sjabloontypen en beleid worden in alle mappen overgeërfd volgens de volgende prioriteitsvolgorde:

1. De huidige map.
1. Bovenliggend item of bovenliggende items van de huidige map.
1. `/conf/global`
1. `/apps`
1. `/libs`

Er wordt een lijst met alle toegestane vermeldingen gemaakt. Als configuraties elkaar overlappen ( `path`/ `label`), wordt alleen de instantie weergegeven die zich het dichtst bij de huidige map bevindt.

Als u een nieuwe map wilt maken, kunt u het volgende doen:

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

   * Waarde: De titel (voor de map) die u wilt weergeven in de **Sjabloonconsole** .

1. Naast *de* standaardmachtigingen en -bevoegdheden (bijvoorbeeld `content-authors`) moet u nu groep(en) toewijzen en de vereiste toegangsrechten (ACL&#39;s) definiëren voor uw auteurs om sjablonen in de nieuwe map te kunnen maken.

   De `template-authors` groep is de standaardgroep die moet worden toegewezen. Zie volgende sectie [ACLs en Groepen](/help/sites-developing/page-templates-editable.md#acls-and-groups) voor details.

   Zie [Toegang Right Management](/help/sites-administering/user-group-ac-admin.md#access-right-management) voor volledige details over het beheren en toewijzen van toegangsrechten.

### De configuratiebrowser gebruiken {#using-the-configuration-browser}

1. Ga naar **Globale Navigatie** -> **Hulpmiddelen** > Browser **van de** Configuratie.

   De bestaande mappen worden links weergegeven, inclusief de **** algemene map.

1. Klik op **Maken**.
1. In het dialoogvenster Configuratie **** maken moeten de volgende velden worden geconfigureerd:

   * **Titel**: Geef een titel op voor de configuratiemap
   * **Bewerkbare sjablonen**: Tik om bewerkbare sjablonen toe te staan in deze map

1. Klik op **Maken**

>[!NOTE]
>
>In Browser van de Configuratie, kunt u de globale omslag uitgeven en de **Bewerkbare optie van Malplaatjes** activeren als u wenst om malplaatjes binnen deze omslag tot stand te brengen, nochtans wordt dit niet geadviseerd beste praktijken.
>
>See the [Configuration Browser](/help/sites-administering/configurations.md) documentation for more information.

### ACLs en Groepen {#acls-and-groups}

Zodra uw malplaatjeomslagen (of via CRXDE of met Browser van de Configuratie) worden gecreeerd, moet ACLs voor de aangewezen groepen voor de malplaatjeomslagen worden bepaald om juiste veiligheid te verzekeren.

De malplaatjeomslagen voor de [Wij.Retail verwijzingsimplementatie](/help/sites-developing/we-retail.md) kunnen als voorbeeld worden gebruikt.

#### De groep sjabloonauteurs {#the-template-authors-group}

De `template-authors` groep is de groep die wordt gebruikt om toegang tot malplaatjes te beheren en komt standaard met AEM, maar is leeg. Gebruikers moeten worden toegevoegd aan de groep voor het project of de site.

>[!CAUTION]
>
>De `template-authors` groep is *alleen* voor gebruikers die nieuwe sjablonen moeten kunnen maken.
>
>Het bewerken van sjablonen is bijzonder krachtig en als dit niet het geval is, kunnen bestaande sjablonen worden verbroken. Daarom moet deze rol worden toegespitst en alleen gekwalificeerde gebruikers omvatten.

In de volgende tabel worden de benodigde machtigingen voor sjabloonbewerking weergegeven.

<table>
 <tbody>
  <tr>
   <th>Pad</th>
   <th>Rol/groep</th>
   <th>Machtigingen<br /> </th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td rowspan="3"><code>/conf/&lt;<i>your-folder</i>&gt;/settings/wcm/templates</code></td>
   <td>Sjabloonauteurs<br /> </td>
   <td>lezen, schrijven, repliceren</td>
   <td>Sjabloonauteurs die sjablonen in sitespecifieke <code>/conf</code> ruimte maken, lezen, bijwerken, verwijderen en repliceren</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>read</td>
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
   <td>Sjabloonauteurs die sjablonen in sitespecifieke <code>/conf</code> ruimte maken, lezen, bijwerken, verwijderen en repliceren</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>read</td>
   <td>De anonieme Gebruiker van het Web moet beleid lezen terwijl het teruggeven van een pagina</td>
  </tr>
  <tr>
   <td>Inhoudsauteurs</td>
   <td>repliceren</td>
   <td>Auteurs van inhoud moeten het beleid van een sjabloon op een pagina activeren wanneer ze een pagina activeren</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/&lt;site&gt;/settings/template-types</code></td>
   <td>Sjabloonauteur</td>
   <td>read</td>
   <td>Sjabloonauteur maakt een nieuwe sjabloon op basis van een van de vooraf gedefinieerde sjabloontypen.</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>none</td>
   <td>De anonieme Gebruiker van het Web moet tot de malplaatjetypes niet toegang hebben</td>
  </tr>
 </tbody>
</table>

Deze standaardgroep behandelt slechts de projectmontages, waar alle `template-authors` `template-authors` leden tot alle malplaatjes toegang hebben en auteur. Voor complexere montages, waar de veelvoudige groepen van malplaatjeauteurs nodig zijn om toegang tot malplaatjes te scheiden, moeten meer de auteursgroepen van het douanemalplaatje worden gecreeerd. De machtigingen voor de groepen sjabloonauteurs zijn echter nog steeds hetzelfde.

#### Oudere sjablonen onder /conf/global {#legacy-templates-under-conf-global}

De malplaatjes zouden niet meer in moeten worden opgeslagen, `/conf/global`nochtans voor sommige erfenisinstallaties kunnen er nog malplaatjes in deze plaats zijn. ALLEEN in dergelijke verouderde situaties moeten de volgende `/conf/global` paden expliciet worden geconfigureerd.

<table>
 <tbody>
  <tr>
   <th>Pad</th>
   <th>Rol/groep</th>
   <th>Machtigingen<br /> </th>
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
   <td>read</td>
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
   <td>read</td>
   <td>De anonieme Gebruiker van het Web moet beleid lezen terwijl het teruggeven van een pagina</td>
  </tr>
  <tr>
   <td>Inhoudsauteurs</td>
   <td>repliceren</td>
   <td>Auteurs van inhoud moeten het beleid van een sjabloon op een pagina activeren wanneer ze een pagina activeren</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/global/settings/wcm/template-types</code></td>
   <td>Sjabloonauteur</td>
   <td>read</td>
   <td>Sjabloonauteur maakt een nieuwe sjabloon op basis van een van de vooraf gedefinieerde sjabloontypen</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>none</td>
   <td>De anonieme Gebruiker van het Web moet tot de malplaatjetypes niet toegang hebben</td>
  </tr>
 </tbody>
</table>

## Sjabloontype {#template-type}

Wanneer u een nieuwe sjabloon maakt, moet u een sjabloontype opgeven:

* Sjabloontypen bieden sjablonen voor een sjabloon. Wanneer u een nieuwe sjabloon maakt, worden de structuur en initiële inhoud van het geselecteerde sjabloontype gebruikt om aan de nieuwe sjabloon te maken.

   * Het sjabloontype wordt gekopieerd om de sjabloon te maken.
   * Zodra het exemplaar is voorgekomen, is de enige verbinding tussen het malplaatje en het malplaatjetype een statische verwijzing voor informatiedoeleinden.

* Met sjabloontypen kunt u het volgende definiëren:

   * Het middeltype van de paginacomponent.
   * Het beleid van de wortelknoop, die de componenten bepaalt die in de malplaatjeredacteur worden toegestaan.
   * Het wordt aanbevolen de onderbrekingspunten voor het responsieve raster en de instelling van de mobiele emulator op te geven voor het sjabloontype. Dit is optioneel omdat de configuratie ook op de afzonderlijke sjabloon kan worden gedefinieerd (zie [Sjabloontype en Mobiele apparaatgroepen](/help/sites-developing/page-templates-editable.md#p-template-type-and-mobile-device-groups-br-p)).

* AEM biedt een kleine selectie van out-of-box sjabloontypen, zoals HTML5 Page en Adaptive Form Page.

   * Extra voorbeelden worden verstrekt als deel van de [Wij.Detailhandel](/help/sites-developing/we-retail.md) steekproefinhoud.

* Sjabloontypen worden meestal gedefinieerd door ontwikkelaars.

De sjabloontypen voor de out-of-the-box worden opgeslagen onder:

* `/libs/settings/wcm/template-types`

>[!CAUTION]
>
>U mag niets in het `/libs` pad wijzigen. De reden hiervoor is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van de instantie, wordt overschreven (en dat deze kan worden overschreven wanneer u een hotfix- of functiepakket toepast).

Uw sitespecifieke sjabloontypen moeten worden opgeslagen op de vergelijkbare locatie:

* `/apps/settings/wcm/template-types`

De definities voor uw aangepaste malplaatjetypes zouden in user-defined omslagen (geadviseerd) of alternatief in moeten worden opgeslagen `global`. Bijvoorbeeld:

* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/template-types`
* `/conf/<my-folder>/settings/wcm/template-types`
* `/conf/global/settings/wcm/template-types`

>[!CAUTION]
>
>De sjabloontypen moeten de juiste mapstructuur in acht nemen (d.w.z. `/settings/wcm/...`), anders worden de sjabloontypen niet gevonden.

### Sjabloontype en mobiele apparaatgroepen {#template-type-and-mobile-device-groups-br}

De [apparaatgroepen](/help/sites-developing/mobile.md#device-groups) die worden gebruikt voor een bewerkbare sjabloon (ingesteld als relatief pad van de eigenschap `cq:deviceGroups`) definiëren welke mobiele apparaten beschikbaar zijn als emulators in de [lay-outmodus](/help/sites-authoring/responsive-layout.md) van het ontwerpen van pagina&#39;s. Deze waarde kan op twee plaatsen worden ingesteld:

* Op het bewerkbare sjabloontype
* Op de bewerkbare sjabloon

Wanneer u een nieuwe bewerkbare sjabloon maakt, wordt de waarde van het sjabloontype naar de afzonderlijke sjabloon gekopieerd. Als de waarde niet op het type is ingesteld, kan deze in de sjabloon worden ingesteld. Als een sjabloon eenmaal is gemaakt, is er geen overerving van het type naar de sjabloon.

>[!CAUTION]
>
>De waarde van `cq:deviceGroups` moet worden ingesteld als een relatief pad, zoals `mobile/groups/responsive` en niet als een absoluut pad, zoals `/etc/mobile/groups/responsive`.

>[!NOTE]
>
>Met [statische sjablonen](/help/sites-developing/page-templates-static.md)kan de waarde van `cq:deviceGroups` worden ingesteld op de hoofdmap van de site.
>
>Met bewerkbare sjablonen wordt deze waarde nu opgeslagen op sjabloonniveau en wordt deze niet ondersteund op hoofdniveau van de pagina.

### Sjabloontypen maken {#creating-template-types}

Als u een sjabloon hebt gemaakt die als basis voor andere sjablonen kan dienen, kunt u deze sjabloon kopiëren als een sjabloontype.

1. Maak een sjabloon zoals u elke bewerkbare sjabloon [zoals hier](/help/sites-authoring/templates.md#creating-a-new-template-template-author)wordt beschreven. Deze sjabloon fungeert als basis voor uw sjabloontype.
1. Met CRXDE Lite kopieert u de nieuw gemaakte sjabloon van het `templates` knooppunt naar het `template-types` knooppunt onder de [sjabloonmap](/help/sites-developing/page-templates-editable.md#template-folders).
1. Verwijder de sjabloon uit het `templates` knooppunt onder de [sjabloonmap](/help/sites-developing/page-templates-editable.md#template-folders).
1. Verwijder alle `template-types` en `cq:template` eigenschappen in de kopie van de sjabloon onder het `cq:templateType` `jcr:content` knooppunt.

U kunt uw eigen malplaatjetype ook ontwikkelen gebruikend een voorbeeld editable malplaatje als basis, beschikbaar op GitHub.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open a-plaatsen-voorbeeld-douane-malplaatje-type project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type)
* Het project downloaden als [ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type/archive/master.zip)

## Sjabloondefinities {#template-definitions}

Definities voor bewerkbare sjablonen zijn opgeslagen door de [gebruiker gedefinieerde mappen](/help/sites-developing/page-templates-editable.md#template-folders) (aanbevolen) of anders in `global`. Bijvoorbeeld:

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

### jcr:content {#jcr-content}

Dit knooppunt bevat eigenschappen voor de sjabloon:

* **Naam**: `jcr:title`

* **Naam**: `status`

   * ``**Type**: `String`

   * **Waarde**: `draft`, `enabled` of `disabled`

### Structuur {#structure}

Hiermee definieert u de structuur van de resulterende pagina:

* Wordt bij het maken van een nieuwe pagina samengevoegd met de oorspronkelijke inhoud ( `/initial`).
* Wijzigingen in de structuur worden weerspiegeld in alle pagina&#39;s die met de sjabloon worden gemaakt.
* Het knooppunt `root` ( `structure/jcr:content/root`) definieert de lijst met componenten die beschikbaar zullen zijn op de resulterende pagina.

   * Componenten die zijn gedefinieerd in de sjabloonstructuur kunnen niet worden verplaatst op of verwijderd van resulterende pagina&#39;s.
   * Wanneer een component ontgrendeld is, wordt de `editable` eigenschap ingesteld op `true`.

   * Wanneer een component die al inhoud bevat, is ontgrendeld, wordt deze inhoud naar de `initial` vertakking verplaatst.

* Het `cq:responsive` knooppunt bevat definities voor de responsieve lay-out.

### Oorspronkelijke inhoud {#initial-content}

Definieert de eerste inhoud die een nieuwe pagina krijgt wanneer deze wordt gemaakt:

* Bevat een `jcr:content` knooppunt dat naar nieuwe pagina&#39;s wordt gekopieerd.
* Wordt samengevoegd met de structuur ( `/structure`) wanneer u een nieuwe pagina maakt.
* Bestaande pagina&#39;s worden niet bijgewerkt als de oorspronkelijke inhoud na het maken wordt gewijzigd.
* Het `root` knooppunt bevat een lijst met componenten om te definiëren wat er beschikbaar is op de resulterende pagina.
* Als er inhoud wordt toegevoegd aan een component in de structuurmodus en die component vervolgens wordt ontgrendeld (of vice versa), wordt deze inhoud gebruikt als initiële inhoud.

### Indeling {#layout}

Wanneer u een sjabloon [bewerkt, kunt u de lay-out](/help/sites-authoring/templates.md)definiëren. Hierbij wordt gebruikgemaakt van [een responsieve standaardlay-out](/help/sites-authoring/responsive-layout.md) die ook kan worden [geconfigureerd](/help/sites-administering/configuring-responsive-layout.md).

### Inhoudsbeleid {#content-policies}

Met het inhoudsbeleid (of het ontwerpbeleid) worden de ontwerpeigenschappen van een component gedefinieerd. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt). Het inhoudsbeleid kan worden gemaakt en geselecteerd in de sjablooneditor.

* De eigenschap `cq:policy`, op het `root` knooppunt
   `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/root`
Verstrekt een relatieve verwijzing naar het inhoudsbeleid voor het de paragraafsysteem van de pagina.

* De eigenschap `cq:policy`, op de componentexpliciete knooppunten onder `root`, biedt koppelingen naar het beleid voor de afzonderlijke componenten.

* De feitelijke beleidsdefinities worden opgeslagen onder:
   `/conf/<your-folder>/settings/wcm/policies/wcm/foundation/components`

>[!NOTE]
>
>De paden van beleidsdefinities zijn afhankelijk van het pad van de component. `cq:policy` bevat een relatieve verwijzing naar de configuratie zelf.

>[!NOTE]
>
>Op basis van bewerkbare sjablonen gemaakte pagina&#39;s beschikken niet over een ontwerpmodus in de pagina-editor.
>
>De `policies` structuur van een bewerkbare sjabloon heeft dezelfde hiërarchie als de configuratie van de ontwerpmodus van een statische sjabloon onder:
>
>`/etc/designs/<my-site>/jcr:content/<component-name>`
>
>De ontwerpmodusconfiguratie van een statische sjabloon is gedefinieerd per paginacomponent.

### Paginabeleid {#page-policies}

Het beleid van de pagina staat u toe om het [inhoudsbeleid](#content-policies) voor de pagina (belangrijkste parsys), in of het malplaatje of de resulterende pagina&#39;s te bepalen.

### Een sjabloon inschakelen en toestaan voor gebruik {#enabling-and-allowing-a-template-for-use}

1. **Sjabloon inschakelen**

   Voordat een sjabloon kan worden gebruikt, moet deze zijn ingeschakeld door:

   * [Het toelaten van het malplaatje](/help/sites-authoring/templates.md#enablingatemplateauthor) van de console van **Malplaatjes** .

   * Setting the status property on the `jcr:content` node.

      * Bijvoorbeeld op:
         `/conf/<your-folder>/settings/wcm/templates/<your-template>/jcr:content`

      * Definieer de eigenschap:

         * Naam: status
         * Type: String
         * Waarde: `enabled`

1. **Toegestane sjablonen**

   * [Definieer de toegestane sjabloonpaden op de **Pagina-eigenschappen**](/help/sites-authoring/templates.md#allowing-a-template-author) van de desbetreffende pagina of basispagina van een subvertakking.
   * Stel de eigenschap in:
      `cq:allowedTemplates`
Op de 
`jcr:content` knooppunt van de vereiste vertakking.
   Bijvoorbeeld met een waarde van:

   `/conf/<your-folder>/settings/wcm/templates/.*`

## Resulterende inhoudspagina&#39;s {#resultant-content-pages}

Pagina&#39;s die zijn gemaakt op basis van bewerkbare sjablonen:

* Wordt gemaakt met een substructuur die vanuit `structure` `initial` en in de sjabloon wordt samengevoegd

* Verwijzingen hebben naar in de template opgeslagen informatie en naar het sjabloontype. Dit wordt bereikt met een `jcr:content` knooppunt met de eigenschappen:

   * `cq:template`
Verstrekt de dynamische verwijzing naar het daadwerkelijke malplaatje; Hiermee kunnen wijzigingen in de sjabloon op de werkelijke pagina&#39;s worden weergegeven.

   * `cq:templateType`
Verstrekt een verwijzing naar het malplaatjetype.

![chlimage_1-71](assets/chlimage_1-71.png)

In het bovenstaande diagram ziet u hoe sjablonen, inhoud en componenten met elkaar verweven zijn:

* Controller - `/content/<my-site>/<my-page>`de resulterende pagina die naar de sjabloon verwijst. De inhoud bepaalt het gehele proces. Volgens de definities heeft het toegang tot de toepasselijke sjabloon en componenten.

* Configuratie - `/conf/<my-folder>/settings/wcm/templates/<my-template>`de [malplaatje en het verwante inhoudsbeleid](#template-definitions) bepalen de paginasonfiguratie.

* Model - OSGi-bundelsDe [OSGI-bundels](/help/sites-deploying/osgi-configuration-settings.md) implementeren de functionaliteit.

* Weergave - `/apps/<my-site>/components`In zowel de auteur- als de publicatieomgeving wordt de inhoud gerenderd door [componenten](/help/sites-developing/components.md).

Bij het weergeven van een pagina:

* **Sjablonen**:

   * Het `cq:template` bezit van zijn `jcr:content` knoop zal worden van verwijzingen voorzien om tot het malplaatje toegang te hebben dat aan die pagina beantwoordt.

* **Onderdelen**:

   * De paginacomponent voegt de `structure/jcr:content` boomstructuur van het malplaatje met de `jcr:content` boom van de pagina samen.

   * Met de paginacomponent kan de auteur alleen de knooppunten van de sjabloonstructuur bewerken die als bewerkbaar zijn gemarkeerd (en eventuele onderliggende knooppunten).
   * Bij het renderen van een component op een pagina wordt het relatieve pad van die component opgehaald uit het `jcr:content` knooppunt; hetzelfde pad onder het `policies/jcr:content` knooppunt van de sjabloon wordt vervolgens doorzocht.

      * Het `cq:policy` bezit van deze knoop wijst aan het daadwerkelijke inhoudsbeleid (d.w.z. het houdt de ontwerpconfiguratie voor die component).

      * Dit staat u toe om veelvoudige malplaatjes te hebben die de zelfde configuraties van het inhoudsbeleid opnieuw gebruiken.
