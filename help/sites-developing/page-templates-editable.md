---
title: Paginasjablonen - Bewerkbaar
seo-title: Page Templates - Editable
description: Bewerkbare sjablonen zijn geïntroduceerd om, niet-ontwikkelaars toe te staan sjablonen te maken en te bewerken, sjablonen op te geven die een dynamische verbinding met alle pagina's behouden die van hen zijn gemaakt, en de paginacomponent generischer te maken
seo-description: Editable templates have been introduced to, allow non-developers to create and edit templates, provide templates that retain a dynamic connection to any pages created from them, and make the page component more generic
uuid: 61791960-fdef-4e49-878a-11fdf1d4f0ab
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 1099cc44-de6d-499e-8b52-f2f5811ae086
docset: aem65
exl-id: dcb66b6d-d731-493e-8936-12d529f6cbde
source-git-commit: 2801ef5ec5ed7b01f4eb046baa439f6d5de56b75
workflow-type: tm+mt
source-wordcount: '3249'
ht-degree: 0%

---

# Paginasjablonen - Bewerkbaar {#page-templates-editable}

Bewerkbare sjablonen zijn geïntroduceerd in:

* Speciale auteurs toestaan [sjablonen maken en bewerken](/help/sites-authoring/templates.md).

   * Dergelijke gespecialiseerde auteurs worden genoemd **sjabloonauteurs**
   * Sjabloonauteurs moeten lid zijn van de `template-authors` groep.

* Geef sjablonen op die een dynamische verbinding behouden met alle pagina&#39;s die van deze sjablonen zijn gemaakt. Zo zorgt u ervoor dat wijzigingen in de sjabloon ook op de pagina&#39;s zelf worden doorgevoerd.
* Maak de paginacomponent generischer zodat kan de kernpaginacomponent zonder aanpassing worden gebruikt.

Met bewerkbare sjablonen worden de onderdelen die een pagina maken, geïsoleerd in componenten. U kunt de noodzakelijke combinaties componenten in een UI vormen, daardoor eliminerend de behoefte aan een nieuwe paginacomponent die voor elke paginariatie moet worden ontwikkeld.

>[!NOTE]
>
>[Statische sjablonen](/help/sites-developing/page-templates-static.md) zijn ook beschikbaar.

Dit document:

* Geeft een overzicht van het maken van bewerkbare sjablonen

   * Zie voor meer informatie [Paginasjablonen maken](/help/sites-authoring/templates.md)

* Beschrijft de admin/ontwikkelaarstaken die worden vereist om editable malplaatjes tot stand te brengen
* Beschrijft de technische onderbouwing van editable malplaatjes

In dit document wordt ervan uitgegaan dat u vertrouwd bent met het maken en bewerken van sjablonen. Zie het ontwerpdocument [Paginasjablonen maken](/help/sites-authoring/templates.md), waarin de mogelijkheden van bewerkbare sjablonen worden beschreven zoals deze aan de sjabloonauteur worden getoond.

>[!NOTE]
>
>De volgende zelfstudie kan ook van belang zijn voor het instellen van een bewerkbare paginasjabloon in een nieuw project:
>[Aan de slag met AEM Sites Deel 2 - Een basispagina en sjabloon maken](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part2.html)

## Een nieuwe sjabloon maken {#creating-a-new-template}

Bewerkbare sjablonen maken wordt voornamelijk uitgevoerd met de opdracht [sjabloonconsole en sjablooneditor](/help/sites-authoring/templates.md) door een sjabloonauteur. In deze paragraaf wordt een overzicht gegeven van dit proces en wordt een beschrijving gegeven van wat er op technisch niveau gebeurt.

Voor informatie over hoe te om editable malplaatjes in een AEM project te gebruiken zie [Een AEM maken met behulp van Lazybones](https://helpx.adobe.com/experience-manager/using/aem_lazybones.html).

Bij het maken van een nieuwe bewerkbare sjabloon:

1. Een [map voor de sjablonen](#template-folders). Dit is niet verplicht, maar aanbevolen beste praktijken.
1. Selecteer een [sjabloontype](#template-type). Deze wordt gekopieerd om de [sjabloondefinitie](#template-definitions).

   >[!NOTE]
   >
   >Een selectie van sjabloontypen is beschikbaar buiten het vak. U kunt ook [uw eigen sitespecifieke sjabloontypen maken](/help/sites-developing/page-templates-editable.md#creating-template-types) indien nodig.

1. Vorm de structuur, inhoudsbeleid, aanvankelijke inhoud, en lay-out van het nieuwe malplaatje.

   **Structuur**

   * Met de structuur kunt u componenten en inhoud voor de sjabloon definiëren.
   * Componenten die in de sjabloonstructuur zijn gedefinieerd, kunnen niet op een resulterende pagina worden verplaatst of uit resulterende pagina&#39;s worden verwijderd.

      * Als u een malplaatje in een douanemap buiten de wij.Retail steekproefinhoud creeert, kunt u de Componenten van de Stichting kiezen of gebruiken [Kernonderdelen](https://helpx.adobe.com/experience-manager/core-components/using/developing.html).
   * Als u wilt dat auteurs van pagina&#39;s componenten kunnen toevoegen en verwijderen, voegt u een alineasysteem toe aan de sjabloon.
   * Componenten kunnen worden ontgrendeld en opnieuw worden vergrendeld, zodat u de initiële inhoud kunt definiëren.

   Zie voor meer informatie over de manier waarop een sjabloonauteur de structuur definieert [Paginasjablonen maken](/help/sites-authoring/templates.md#editing-a-template-structure-template-author).

   Voor technische details van de structuur, zie [Structuur](/help/sites-developing/page-templates-editable.md#structure) in dit document.

   **Beleid**

   * Het inhoudsbeleid definieert de ontwerpeigenschappen van een component.

      * Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen.
   * Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt).

   Zie voor meer informatie over de manier waarop een sjabloonauteur beleid definieert [Paginasjablonen maken](/help/sites-authoring/templates.md#editing-a-template-structure-template-author).

   Voor technische details van het beleid raadpleegt u [Inhoudsbeleid](/help/sites-developing/page-templates-editable.md#content-policies) in dit document.

   **Oorspronkelijke inhoud**

   * Met Eerste inhoud wordt inhoud gedefinieerd die wordt weergegeven wanneer een pagina voor het eerst wordt gemaakt op basis van de sjabloon.
   * De initiële inhoud kan vervolgens worden bewerkt door auteurs van pagina&#39;s.

   Zie voor meer informatie over de manier waarop een sjabloonauteur de structuur definieert [Paginasjablonen maken](/help/sites-authoring/templates.md#editing-a-template-initial-content-author).

   Voor technische details over de initiële inhoud raadpleegt u [Oorspronkelijke inhoud](/help/sites-developing/page-templates-editable.md#initial-content) in dit document.

   **Indeling**

   * U kunt de sjabloonlay-out voor een reeks apparaten definiëren.
   * De responsieve indeling voor sjablonen werkt op dezelfde manier als voor het ontwerpen van pagina&#39;s.

   Zie voor meer informatie over de manier waarop de sjabloonlay-out door de sjabloonauteur wordt gedefinieerd [Paginasjablonen maken](/help/sites-authoring/templates.md#editing-a-template-layout-template-author).

   Voor technische details over de indeling van de template raadpleegt u [Layout](/help/sites-developing/page-templates-editable.md#layout) in dit document.

1. Schakel de sjabloon in en sta deze vervolgens toe voor specifieke inhoudstructuren.

   * U kunt een sjabloon in- of uitschakelen om de sjabloon beschikbaar of niet beschikbaar te maken voor auteurs van pagina&#39;s.
   * Een sjabloon kan beschikbaar worden gesteld of niet beschikbaar zijn voor bepaalde paginasvertakkingen.

   Voor details over hoe een malplaatjeauteur een malplaatje toelaat, zie [Paginasjablonen maken](/help/sites-authoring/templates.md#enabling-and-allowing-a-template-template-author).

   Voor technische details over het toelaten van een malplaatje, zie [Een sjabloon voor ons inschakelen en toestaan](/help/sites-developing/page-templates-editable.md#enabling-and-allowing-a-template-for-use)e in dit document

1. Gebruik dit besturingselement om inhoudspagina&#39;s te maken.

   * Wanneer u een sjabloon gebruikt om een nieuwe pagina te maken, is er geen zichtbaar verschil en is er geen indicatie tussen statische en bewerkbare sjablonen.
   * Voor de auteur van de pagina is het proces transparant.

   Zie voor meer informatie over hoe een auteur van een pagina sjablonen gebruikt om een pagina te maken [Pagina&#39;s maken en ordenen](/help/sites-authoring/managing-pages.md#templates).

   Voor technische details over het maken van pagina&#39;s met bewerkbare sjablonen raadpleegt u [Resulterende inhoudspagina&#39;s](/help/sites-developing/page-templates-editable.md#resultant-content-pages) in dit document.

>[!TIP]
>
>Voer nooit informatie in die u wilt internationaliseren in een sjabloon. Voor internaliseringsdoeleinden wordt de [lokalisatiefunctie van de Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/localization.html) aanbevolen.

>[!NOTE]
>
>Sjablonen zijn krachtige gereedschappen om de workflow voor het maken van pagina&#39;s te stroomlijnen. Te veel sjablonen kunnen de auteurs echter overweldigen en tot verwarring bij het maken van pagina&#39;s leiden. Een goede regel is om het aantal sjablonen onder de 100 te houden.
>
>Adobe adviseert niet om meer dan 1000 malplaatjes wegens potentiële prestatiesgevolgen te hebben.

>[!NOTE]
>
>In de clientbibliotheek van de editor wordt ervan uitgegaan dat de editor `cq.shared` naamruimte in inhoudspagina&#39;s en als deze ontbreekt, de JavaScript-fout `Uncaught TypeError: Cannot read property 'shared' of undefined` resulteert.
>
>Alle pagina&#39;s met voorbeeldinhoud bevatten `cq.shared`, dus alle inhoud die erop is gebaseerd, omvat automatisch `cq.shared`. Als u echter besluit zelf inhoudspagina&#39;s te maken zonder deze op voorbeeldinhoud te baseren, moet u ervoor zorgen dat u de `cq.shared` naamruimte.
>
>Zie [Client-Side bibliotheken gebruiken](/help/sites-developing/clientlibs.md) voor nadere informatie.

## Sjabloonmappen {#template-folders}

Voor het organiseren van uw sjablonen kunt u de volgende mappen gebruiken:

* **global**
* Sitespecifiek De sitespecifieke mappen die u maakt om uw sjablonen te organiseren, worden gemaakt met beheerdersrechten voor een account.

>[!NOTE]
>
>Ook al kunt u uw mappen nesten, wanneer de gebruiker ze in het dialoogvenster **Sjablonen** worden weergegeven als een platte structuur.

In een standaardinstelling AEM **globaal** bestaat al in de sjabloonconsole. Dit houdt standaardmalplaatjes vast en doet dienst als reserve als geen beleid en/of malplaatje-types in de huidige omslag worden gevonden. U kunt uw standaardsjablonen toevoegen aan deze map of een nieuwe map maken (aanbevolen).

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

Er wordt een lijst met alle toegestane vermeldingen gemaakt. Als een van de configuraties elkaar overlappen ( `path`/ `label`), wordt alleen de instantie die zich het dichtst bij de huidige map bevindt, aan de gebruiker getoond.

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

   * Waarde: De titel (voor de map) die u wilt weergeven in het dialoogvenster **Sjablonen** console.

1. In *optellen* volgens de standaardmachtigingen en -bevoegdheden voor het schrijven van programmacode (bv. `content-authors`) moet u nu groep(en) toewijzen en de vereiste toegangsrechten (ACL&#39;s) definiëren voor uw auteurs om sjablonen in de nieuwe map te kunnen maken.

   De `template-authors` groep is de standaardgroep die moet worden toegewezen. Zie de volgende sectie [ACLs en Groepen](/help/sites-developing/page-templates-editable.md#acls-and-groups) voor meer informatie.

   Zie [Toegangsbeheer](/help/sites-administering/user-group-ac-admin.md#access-right-management) voor volledige informatie over het beheren en toewijzen van toegangsrechten.

### De configuratiebrowser gebruiken {#using-the-configuration-browser}

1. Ga naar **Algemene navigatie** -> **Gereedschappen** > **Configuratiebrowser**.

   De bestaande mappen worden links weergegeven, inclusief **globaal** map.

1. Klikken **Maken**.
1. In de **Configuratie maken** moeten de volgende velden worden geconfigureerd:

   * **Titel**: Geef een titel op voor de configuratiemap
   * **Bewerkbare sjablonen**: Tik om bewerkbare sjablonen toe te staan in deze map

1. Klikken **Maken**

>[!NOTE]
>
>In Browser van de Configuratie, kunt u de globale omslag uitgeven en activeren **Bewerkbare sjablonen** als u sjablonen in deze map wilt maken, wordt dit echter niet aanbevolen.
>
>Zie de [Configuratiebrowser](/help/sites-administering/configurations.md) documentatie voor meer informatie.

### ACLs en Groepen {#acls-and-groups}

Zodra uw malplaatjeomslagen (of via CRXDE of met Browser van de Configuratie) worden gecreeerd, moet ACLs voor de aangewezen groepen voor de malplaatjeomslagen worden bepaald om juiste veiligheid te verzekeren.

De sjabloonmappen voor de [We.Retail-referentieimplementatie](/help/sites-developing/we-retail.md) kan als voorbeeld worden gebruikt.

#### De groep sjabloonauteurs {#the-template-authors-group}

De `template-authors` de groep is de groep wordt gebruikt om toegang tot malplaatjes te beheren en komt standaard met AEM, maar is leeg. Gebruikers moeten worden toegevoegd aan de groep voor het project of de site.

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
   <td>Sjabloonauteurs die sjablonen maken, lezen, bijwerken, verwijderen en repliceren in sitespecifieke sjablonen <code>/conf</code> spatie</td>
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
   <td>Sjabloonauteurs die sjablonen maken, lezen, bijwerken, verwijderen en repliceren in sitespecifieke sjablonen <code>/conf</code> spatie</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>lezen</td>
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
   <td>lezen</td>
   <td>Sjabloonauteur maakt een nieuwe sjabloon op basis van een van de vooraf gedefinieerde sjabloontypen.</td>
  </tr>
  <tr>
   <td>Anonieme webgebruiker</td>
   <td>none</td>
   <td>De anonieme Gebruiker van het Web moet tot de malplaatjetypes niet toegang hebben</td>
  </tr>
 </tbody>
</table>

Deze standaard `template-authors` groep omvat alleen de projectinstellingen, waarbij alle `template-authors` leden hebben toegang tot alle sjablonen en mogen deze ontwerpen . Voor complexere montages, waar de veelvoudige groepen van malplaatjeauteurs nodig zijn om toegang tot malplaatjes te scheiden, moeten meer de auteursgroepen van het douanemalplaatje worden gecreeerd. De machtigingen voor de groepen sjabloonauteurs zijn echter nog steeds hetzelfde.

#### Oudere sjablonen onder /conf/global {#legacy-templates-under-conf-global}

Sjablonen mogen niet meer worden opgeslagen in `/conf/global`Voor sommige oude installaties zijn er echter nog sjablonen op deze locatie. ALLEEN in dergelijke verouderde situaties dient het volgende te gebeuren: `/conf/global` de wegen worden uitdrukkelijk gevormd.

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
   <td>Auteurs van inhoud moeten het beleid van een sjabloon op een pagina activeren wanneer ze een pagina activeren</td>
  </tr>
  <tr>
   <td rowspan="2"><code>/conf/global/settings/wcm/template-types</code></td>
   <td>Sjabloonauteur</td>
   <td>lezen</td>
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
   * Het wordt aanbevolen de onderbrekingspunten voor het responsieve raster en de instelling van de mobiele emulator op te geven voor het sjabloontype. Dit is optioneel omdat de configuratie ook op de afzonderlijke sjabloon kan worden gedefinieerd (zie [Sjabloontype en mobiele apparaatgroepen](/help/sites-developing/page-templates-editable.md#p-template-type-and-mobile-device-groups-br-p)).

* AEM biedt een kleine selectie van sjabloontypen die buiten het vak vallen, zoals HTML5 Pagina en Aangepaste formulierpagina.

   * Als onderdeel van het [Wij.Detailhandel](/help/sites-developing/we-retail.md) voorbeeldinhoud.

* Sjabloontypen worden meestal gedefinieerd door ontwikkelaars.

De sjabloontypen voor de out-of-the-box worden opgeslagen onder:

* `/libs/settings/wcm/template-types`

>[!CAUTION]
>
>U mag niets wijzigen in het dialoogvenster `/libs` pad. Dit komt omdat de inhoud van `/libs` wordt de volgende keer overschreven dat u een upgrade uitvoert van uw exemplaar (en kan worden overschreven wanneer u een hotfix- of functiepakket toepast).

Uw sitespecifieke sjabloontypen moeten worden opgeslagen op de vergelijkbare locatie:

* `/apps/settings/wcm/template-types`

De definities voor uw aangepaste malplaatjetypes zouden in user-defined omslagen (geadviseerd) of anders in moeten worden opgeslagen `global`. Bijvoorbeeld:

* `/conf/<my-folder-01>/<my-folder-02>/settings/wcm/template-types`
* `/conf/<my-folder>/settings/wcm/template-types`
* `/conf/global/settings/wcm/template-types`

>[!CAUTION]
>
>De sjabloontypen moeten de juiste mapstructuur in acht nemen (d.w.z. `/settings/wcm/...`), anders worden de sjabloontypen niet gevonden.

### Sjabloontype en mobiele apparaatgroepen {#template-type-and-mobile-device-groups-br}

De [apparaatgroepen](/help/sites-developing/mobile.md#device-groups) gebruikt voor een bewerkbare sjabloon (ingesteld als relatief pad van de eigenschap) `cq:deviceGroups`) bepalen welke mobiele apparaten als emulators beschikbaar zijn in de [lay-outmodus](/help/sites-authoring/responsive-layout.md) pagina&#39;s ontwerpen. Deze waarde kan op twee plaatsen worden ingesteld:

* Op het bewerkbare sjabloontype
* Op de bewerkbare sjabloon

Wanneer u een nieuwe bewerkbare sjabloon maakt, wordt de waarde van het sjabloontype naar de afzonderlijke sjabloon gekopieerd. Als de waarde niet op het type is ingesteld, kan deze in de sjabloon worden ingesteld. Als een sjabloon eenmaal is gemaakt, is er geen overerving van het type naar de sjabloon.

>[!CAUTION]
>
>De waarde van `cq:deviceGroups` moet worden ingesteld als een relatief pad, zoals `mobile/groups/responsive` en niet als een absoluut pad, zoals `/etc/mobile/groups/responsive`.

>[!NOTE]
>
>Met [statische sjablonen](/help/sites-developing/page-templates-static.md), de waarde van `cq:deviceGroups` kan worden ingesteld als de hoofdmap van de site.
>
>Met bewerkbare sjablonen wordt deze waarde nu opgeslagen op sjabloonniveau en wordt deze niet ondersteund op hoofdniveau van de pagina.

### Sjabloontypen maken {#creating-template-types}

Als u een sjabloon hebt gemaakt die als basis voor andere sjablonen kan dienen, kunt u deze sjabloon kopiëren als een sjabloontype.

1. Een sjabloon maken zoals elke bewerkbare sjabloon [zoals hier beschreven](/help/sites-authoring/templates.md#creating-a-new-template-template-author), die als basis voor uw sjabloontype zal dienen.
1. Kopieer de nieuwe sjabloon met CRXDE Lite van de `templates` aan de `template-types` knooppunt onder [sjabloonmap](/help/sites-developing/page-templates-editable.md#template-folders).
1. De sjabloon verwijderen uit het dialoogvenster `templates` knooppunt onder [sjabloonmap](/help/sites-developing/page-templates-editable.md#template-folders).
1. In de kopie van de sjabloon die zich onder de `template-types` knooppunt, alles verwijderen `cq:template` en `cq:templateType` `jcr:content` eigenschappen.

U kunt uw eigen malplaatjetype ook ontwikkelen gebruikend een voorbeeld editable malplaatje als basis, beschikbaar op GitHub.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [Open a-plaatsen-voorbeeld-douane-malplaatje-type project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type)
* Het project downloaden als [een ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-sites-example-custom-template-type/archive/master.zip)

## Sjabloondefinities {#template-definitions}

Definities voor bewerkbare sjablonen worden opgeslagen [door de gebruiker gedefinieerde mappen](/help/sites-developing/page-templates-editable.md#template-folders) (aanbevolen) of als alternatief `global`. Bijvoorbeeld:

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

   * **Waarde**: `draft`, `enabled` of `disabled`

### Structuur {#structure}

Hiermee definieert u de structuur van de resulterende pagina:

* Is samengevoegd met de oorspronkelijke inhoud ( `/initial`) bij het maken van een nieuwe pagina.
* Wijzigingen in de structuur worden weerspiegeld in alle pagina&#39;s die met de sjabloon worden gemaakt.
* De `root` ( `structure/jcr:content/root`) definieert de lijst met componenten die beschikbaar zullen zijn op de resulterende pagina.

   * Componenten die zijn gedefinieerd in de sjabloonstructuur kunnen niet worden verplaatst op of verwijderd van resulterende pagina&#39;s.
   * Als een component eenmaal is ontgrendeld, wordt het `editable` eigenschap is ingesteld op `true`.

   * Wanneer een component die al inhoud bevat, is ontgrendeld, wordt deze inhoud naar de `initial` vertakking.

* De `cq:responsive` node bevat definities voor de responsieve lay-out.

### Oorspronkelijke inhoud {#initial-content}

Definieert de eerste inhoud die een nieuwe pagina krijgt wanneer deze wordt gemaakt:

* Bevat een `jcr:content` knooppunt dat naar nieuwe pagina&#39;s wordt gekopieerd.
* Is samengevoegd met de structuur ( `/structure`) bij het maken van een nieuwe pagina.
* Bestaande pagina&#39;s worden niet bijgewerkt als de oorspronkelijke inhoud na het maken wordt gewijzigd.
* De `root` node bevat een lijst met componenten om te definiëren wat er beschikbaar is op de resulterende pagina.
* Als er inhoud wordt toegevoegd aan een component in de structuurmodus en die component vervolgens wordt ontgrendeld (of vice versa), wordt deze inhoud gebruikt als initiële inhoud.

### Indeling {#layout}

Wanneer [bewerken van een sjabloon die u kunt definiëren](/help/sites-authoring/templates.md)gebruikt [standaardresponsieve indeling](/help/sites-authoring/responsive-layout.md) dat ook [geconfigureerd](/help/sites-administering/configuring-responsive-layout.md).

### Inhoudsbeleid {#content-policies}

Met het inhoudsbeleid (of het ontwerpbeleid) worden de ontwerpeigenschappen van een component gedefinieerd. Bijvoorbeeld de beschikbare componenten of de minimum-/maximumafmetingen. Deze zijn van toepassing op de sjabloon (en op pagina&#39;s die met de sjabloon zijn gemaakt). Het inhoudsbeleid kan worden gemaakt en geselecteerd in de sjablooneditor.

* De eigenschap `cq:policy`over de `root` node
   `/conf/<your-folder>/settings/wcm/templates/<your-template>/policies/jcr:content/root`
Verstrekt een relatieve verwijzing naar het inhoudsbeleid voor het de paragraafsysteem van de pagina.

* De eigenschap `cq:policy`, op de componentexpliciete knooppunten onder `root`koppelingen naar het beleid voor de afzonderlijke componenten te verschaffen.

* De feitelijke beleidsdefinities worden opgeslagen onder:
   `/conf/<your-folder>/settings/wcm/policies/wcm/foundation/components`

>[!NOTE]
>
>De paden van beleidsdefinities zijn afhankelijk van het pad van de component. `cq:policy` bevat een relatieve verwijzing naar de configuratie zelf.

>[!NOTE]
>
>Op basis van bewerkbare sjablonen gemaakte pagina&#39;s beschikken niet over een ontwerpmodus in de pagina-editor.
>
>De `policies` De structuur van een bewerkbare sjabloon heeft dezelfde hiërarchie als de configuratie van de ontwerpmodus van een statische sjabloon onder:
>
>`/etc/designs/<my-site>/jcr:content/<component-name>`
>
>De ontwerpmodusconfiguratie van een statische sjabloon is gedefinieerd per paginacomponent.

### Paginabeleid {#page-policies}

Met paginabeleid kunt u de [inhoudsbeleid](#content-policies) voor de pagina (belangrijkste parsys), in of het malplaatje of resulterende pagina&#39;s.

### Een sjabloon inschakelen en toestaan voor gebruik {#enabling-and-allowing-a-template-for-use}

1. **Sjabloon inschakelen**

   Voordat een sjabloon kan worden gebruikt, moet deze zijn ingeschakeld door:

   * [De sjabloon inschakelen](/help/sites-authoring/templates.md#enablingatemplateauthor) van de **Sjablonen** console.

   * De statuseigenschap instellen op de knop `jcr:content` knooppunt.

      * Bijvoorbeeld op:
         `/conf/<your-folder>/settings/wcm/templates/<your-template>/jcr:content`

      * Definieer de eigenschap:

         * Naam: status
         * Type: String
         * Waarde: `enabled`

1. **Toegestane sjablonen**

   * [Definieer de toegestane sjabloonpaden op het tabblad **Pagina-eigenschappen**](/help/sites-authoring/templates.md#allowing-a-template-author) van de desbetreffende pagina of basispagina van een subvertakking.
   * Stel de eigenschap in:
      `cq:allowedTemplates`
Op de 
`jcr:content` knooppunt van de vereiste vertakking.
   Bijvoorbeeld met een waarde van:

   `/conf/<your-folder>/settings/wcm/templates/.*`

## Resulterende inhoudspagina&#39;s {#resultant-content-pages}

Pagina&#39;s die zijn gemaakt op basis van bewerkbare sjablonen:

* Wordt gemaakt met een substructuur waaruit wordt samengevoegd `structure` en `initial` in de sjabloon

* Verwijzingen hebben naar in de template opgeslagen informatie en naar het sjabloontype. Dit wordt bereikt met een `jcr:content` knooppunt met de eigenschappen:

   * `cq:template`
Verstrekt de dynamische verwijzing naar het daadwerkelijke malplaatje; Hiermee kunnen wijzigingen in de sjabloon op de werkelijke pagina&#39;s worden weergegeven.

   * `cq:templateType`
Verstrekt een verwijzing naar het malplaatjetype.

![chlimage_1-71](assets/chlimage_1-71.png)

In het bovenstaande diagram ziet u hoe sjablonen, inhoud en componenten met elkaar verweven zijn:

* Controller - `/content/<my-site>/<my-page>`
De resulterende pagina die naar de sjabloon verwijst. De inhoud bepaalt het gehele proces. Volgens de definities heeft het toegang tot de toepasselijke sjabloon en componenten.

* Configuratie - `/conf/<my-folder>/settings/wcm/templates/<my-template>`
De [sjabloonbeleid en beleid inzake gerelateerde inhoud](#template-definitions) definieert u de paginaconfiguratie.

* Model - OSGi bundelt de [OSGI-pakketten](/help/sites-deploying/osgi-configuration-settings.md) de functionaliteit implementeren.

* Weergeven - `/apps/<my-site>/components`
In zowel de auteur- als de publicatieomgeving wordt de inhoud gerenderd door [componenten](/help/sites-developing/components.md).

Bij het weergeven van een pagina:

* **Sjablonen**:

   * De `cq:template` eigendom van zijn `jcr:content` Het knooppunt wordt opgeroepen om toegang te krijgen tot de sjabloon die overeenkomt met die pagina.

* **Onderdelen**:

   * De component page voegt de `structure/jcr:content` structuur van de sjabloon met de `jcr:content` boomstructuur van de pagina.

   * Met de paginacomponent kan de auteur alleen de knooppunten van de sjabloonstructuur bewerken die als bewerkbaar zijn gemarkeerd (en eventuele onderliggende knooppunten).
   * Wanneer u een component op een pagina rendert, wordt het relatieve pad van die component overgenomen van de `jcr:content` knooppunt; hetzelfde pad onder `policies/jcr:content` het knooppunt van de sjabloon wordt doorzocht.

      * De `cq:policy` Het bezit van deze knoop wijst aan het daadwerkelijke inhoudsbeleid (d.w.z. het houdt de ontwerpconfiguratie voor die component).

      * Dit staat u toe om veelvoudige malplaatjes te hebben die de zelfde configuraties van het inhoudsbeleid opnieuw gebruiken.
