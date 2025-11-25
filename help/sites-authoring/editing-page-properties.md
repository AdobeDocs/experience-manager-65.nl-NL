---
title: Pagina-eigenschappen bewerken
description: Definieer de vereiste eigenschappen voor een pagina in Adobe Experience Manager.
exl-id: 3cd9374f-6f16-40fb-97cf-5f9a750b8dd2
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
mini-toc-levels: 2
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '2477'
ht-degree: 1%

---


# Pagina-eigenschappen bewerken{#editing-page-properties}

U kunt de vereiste eigenschappen voor een pagina definiëren. Deze kunnen afhankelijk van de aard van de pagina variëren. Sommige pagina&#39;s kunnen bijvoorbeeld zijn verbonden met een live kopie, andere niet en de live kopieergegevens worden beschikbaar, indien van toepassing.

## Pagina-eigenschappen {#page-properties}

De eigenschappen worden verdeeld over verscheidene lusjes.

### Basis {#basic}

#### Titel en tags {#tile}

* **Titel** - de titel van de pagina wordt getoond in diverse plaatsen
   * Bijvoorbeeld, de **het tablijst van Websites** en de **3} kaart/lijstmeningen van Plaatsen {.**
   * Dit is een verplicht veld.
* **Markeringen** - hier kunt u markeringen toevoegen of verwijderen uit de pagina door de lijst in de selectievak bij te werken.
   * Nadat u een tag hebt geselecteerd, wordt deze weergegeven onder het selectievak. U kunt een tag uit deze lijst verwijderen met de x.
   * U kunt een nieuwe tag invoeren door de naam in een leeg selectievak te typen.
      * De nieuwe tag wordt gemaakt wanneer u op Enter drukt.
      * De nieuwe tag wordt weergegeven met een kleine ster aan de rechterkant die aangeeft dat het een nieuwe tag is.
   * In de vervolgkeuzelijst kunt u bestaande tags selecteren.
   * Een x wordt weergegeven wanneer u met de muis over een tag-item in het selectievak beweegt. Hiermee kunt u die tag voor deze pagina verwijderen.
   * Voor meer informatie over markeringen, zie [ Gebruikend Markeringen.](/help/sites-authoring/tags.md)
* **Verbergen in Navigatie** - wijst erop of de pagina in de paginanavigatie van de resulterende plaats wordt getoond of verborgen

#### Branding {#branding}

Pas een consistente merkidentiteit toe op de verschillende pagina&#39;s door een merkmarkering aan elke paginatitel toe te voegen. Deze functionaliteit vereist gebruik van de Component van de Pagina van versie 2.14.0 of later van de [ Componenten van de Kern.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)

* **met voeten treden** - Controle om de merkschuine streep op deze pagina te bepalen.
   * De waarde wordt geërft door om het even welke kindpagina&#39;s tenzij zij ook hun **vastgestelde waarden van de Overschrijving** hebben.
* **Waarde van de Overschrijving** - de tekst van de merkslogan die aan de paginatitel moet worden toegevoegd
   * De waarde wordt aan de paginatitel toegevoegd na een pipe-teken, zoals `Cycling Tuscany | Always ready for the WKND`

#### Meer titels en beschrijving {#more}

* **Titel van de Pagina** - een titel die op de pagina moet worden gebruikt
   * Doorgaans gebruikt door titelcomponenten
   * Als leeg, wordt de **Titel** gebruikt.
* **Titel van de Navigatie** - U kunt een afzonderlijke titel voor gebruik in de navigatie (bijvoorbeeld, specificeren als u iets beknopter wilt).
   * Als leeg, wordt de **Titel** gebruikt.
* **Ondertitel** - een ondertitel voor gebruik op de pagina
* **Beschrijving** - Uw beschrijving van de pagina, zijn doel, of een andere details u wilt toevoegen

#### Aan/UitTime {#on-time}

De aan/uit-tijd voor een pagina is een handige manier om inhoud die al is gepubliceerd, tijdelijk te verbergen. De inhoud blijft op de publicatie-instantie staan wanneer deze is uitgeschakeld. Als u een pagina uitschakelt, wordt de publicatie van de inhoud niet ongedaan gemaakt.

* **op Tijd** - de datum en de tijd waarop de gepubliceerde pagina zichtbaar (teruggegeven) op het publicatiemilieu wordt gemaakt. De pagina moet, of manueel of door pre-gevormde auto-replicatie worden gepubliceerd.

   * Als reeds [ gepubliceerd, ](/help/sites-authoring/publishing-pages.md) is deze pagina beschikbaar op publiceer instantie, maar gehouden slapend (verborgen) tot het teruggeven op de gespecificeerde tijd.
   * Als niet gepubliceerd en [ voor auto-replicatie wordt gevormd, ](/help/sites-deploying/replication.md) wordt de pagina automatisch gepubliceerd, dan teruggegeven, op de gespecificeerde tijd.
   * Als niet gepubliceerd en niet gevormd voor auto-replicatie, wordt de pagina niet automatisch gepubliceerd, zodat wordt 404 gezien wanneer een poging om tot de pagina toegang te hebben wordt gemaakt.

* **Van Tijd** - Gelijkaardig aan en vaak gebruikt in combinatie met **op Tijd**, bepaalt dit de tijd waarbij de gepubliceerde pagina op het publicatiemilieu wordt verborgen.

Verlaat deze gebieden (**op Tijd** en **van Tijd**) leeg voor pagina&#39;s u wilt publiceren en beschikbaar hebben onmiddellijk en beschikbaar op publiceer milieu tot zij (het normale scenario) worden gedeactiveerd.

>[!NOTE]
>Als of **op Tijd** of **van Tijd** in het verleden is, en de automatische replicatie wordt gevormd, dan wordt de relevante actie onmiddellijk teweeggebracht.

>[!TIP]
>
>Aan/uit-tijden hebben uitsluitend betrekking op inhoud die al is gepubliceerd (handmatig of via automatische replicatie). Daarom hebben publicatieworkflows, zoals die voor het goedkeuren van inhoud, geen invloed op de publicatiestatus van de pagina als gevolg van aan-/uittijden en aan/uit-tijden. Daarom zijn aan/uit-tijden het meest geschikt voor het tijdelijk tonen/verbergen van inhoud die al is goedgekeurd en gepubliceerd.
>
>Als u wenst om nieuwe inhoud met alle bijbehorende werkschema&#39;s te publiceren of (unpublish inhoud) volledig te verwijderen uit uw plaats, overweeg [ het leiden van uw publicatie.](/help/sites-authoring/publishing-pages.md#manage-publication)

#### Vanity URL {#vanity-url}

Voer een vanity-URL voor deze pagina in, zodat u een kortere en/of meer expressieve URL kunt gebruiken.

Bijvoorbeeld, als de URL van de Vanity aan `welcome` aan de pagina wordt geplaatst die door de weg `/v1.0/startpage` voor de website `http://example.com,` wordt geïdentificeerd dan `http://example.com/welcome` zou ijdelheid URL van `http://example.com/content/v1.0/startpage` zijn

>[!CAUTION]
>
>Vanity-URL&#39;s:
>
>* Moet uniek zijn.
>* Geen ondersteuning voor regex-patronen.
>* Deze mag niet op een bestaande pagina worden ingesteld.

Configureer Dispatcher om toegang tot vanity-URL&#39;s in te schakelen. Zie [ Toelatend Toegang tot Vanity URLs ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#enabling-access-to-vanity-urls-vanity-urls) voor meer details.

* **voeg** toe - Tik of klik om een ijdelheid URL toe te voegen.
* **verwijder** - Tik of klik om een ijdelheid URL te verwijderen.
  **Redirect Vanity URL** - wijst erop of u de pagina de ijdelheid URL wilt gebruiken of aan daadwerkelijke URL van de pagina opnieuw richten

### Geavanceerd {#advanced}

#### Instellingen {#settings}

* **Taal** - de paginataal
* **Wortel van de Taal** - moet worden gecontroleerd als de pagina de wortel van een taalexemplaar is
* **opnieuw richt** - wijst op de pagina waaraan deze pagina automatisch zou moeten opnieuw richten
* **Ontwerp** - wijst op het [ ontwerp ](/help/sites-developing/designer.md) dat voor deze pagina moet worden gebruikt.
* **Alias** - specificeert een alias die met deze pagina moet worden gebruikt
   * Als u bijvoorbeeld een alias van `private` voor de pagina `/content/wknd/us/en/magazine/members-only` definieert, kunt u deze pagina ook openen via `/content/wknd/us/en/magazine/private`
   * Als u een alias maakt, wordt de eigenschap `sling:alias` op het paginaknooppunt ingesteld. Dit heeft alleen invloed op de bron, niet op het pad naar de opslagplaats.
   * Pagina&#39;s die door aliassen in de editor worden benaderd, kunnen niet worden gepubliceerd. [ publiceer opties ](/help/sites-authoring/publishing-pages.md) in de redacteur zijn slechts beschikbaar voor pagina&#39;s die via hun daadwerkelijke wegen worden betreden.
   * Voor verdere details, zie [ Gelokaliseerde paginanamen onder SEO en de Beste praktijken van het Beheer URL ](/help/managing/seo-and-url-management.md#localized-page-names).

#### Configuratie {#configuration}

* **Geërft van &lt;*weg* >** - laat/maakt overerving van de **Configuratie van de Wolk** voor de pagina toe
* **Configuratie van de Wolk** - de weg aan de configuratie

#### Sjablooninstellingen {#templates}

* **Toegestane Malplaatjes** - [ bepaalt de lijst van malplaatjes die ](/help/sites-authoring/templates.md#allowingatemplate) binnen deze subtak beschikbaar zijn

#### Verificatievereiste {#authentication}

* **laat** toe - laat (of maak onbruikbaar) het gebruik van authentificatie toe zodat kunt u tot de pagina toegang hebben
* **Login Pagina** - de pagina die voor login moet worden gebruikt

>[!NOTE]
>
>De gesloten gebruikersgroepen voor de pagina worden bepaald op de **[Toestemmingen](/help/sites-authoring/editing-page-properties.md#permissions)** tabel.

>[!CAUTION]
>
>Het **[lusje van Toestemmingen](#permissions)** staat het uitgeven van de configuraties van de KUG toe die op de aanwezigheid van de `granite:AuthenticationRequired` mengen worden gebaseerd. Als de paginamachtigingen gebruikend afgekeurde configuraties van de CUG worden gevormd, die op de aanwezigheid van `cq:cugEnabled` bezit worden gebaseerd, wordt een waarschuwingsbericht getoond onder **de Vereiste van de Authentificatie** en de optie is niet editable, noch zijn de [ Toestemmingen ](/help/sites-authoring/editing-page-properties.md#permissions) editable.
>
>
>In zulk een geval moeten de toestemmingen van de KUG in [ klassieke UI ](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md) worden uitgegeven.

#### Exporteren {#export}

* **Configuratie** - specificeert een de uitvoerconfiguratie

#### SEO {#seo}

* **Canonical Url** - die wordt gebruikt om canonical URL van de pagina te beschrijven
   * Als de URL van de pagina leeg wordt gelaten, is deze de canonieke URL.
* **Codes Robots** - gebruik dropdown om de robots markeringen te selecteren om het gedrag van de kruipende zoekmachine te controleren
   * Sommige opties zijn in strijd met elkaar, in welk geval de meer permissieve optie voorrang krijgt.
* **produceer Sitemap** - wanneer geselecteerd, wordt a `sitemap.xml` geproduceerd voor deze pagina, en zijn nakomelingen.

### Afbeeldingen {#images}

#### Aanbevolen afbeelding {#featured-image}

Deze sectie wordt gebruikt om het beeld te selecteren en te vormen om te omvatten. Dit wordt gebruikt in componenten die verwijzen naar de pagina, bijvoorbeeld stramienen, paginalijsten, enzovoort.

* **Beeld** - u kunt **** een activa kiezen, of voor een dossier doorbladeren om te uploaden, dan **uitgeven**, of **ontruimen** het geselecteerde beeld.
* **Alternatieve Tekst** - Tekst die wordt gebruikt om de betekenis en/of functie van het beeld te vertegenwoordigen, algemeen gebruikt door het schermlezers
* **erven - Waarde die van de activa DAM** wordt genomen - wanneer gecontroleerd, wordt de alternatieve tekst bevolkt met de waarde van de `dc:description` meta-gegevens in DAM.

#### Miniatuur {#thumbnail}

STthis section is used to select and configure the image thumbnail for the page. Dit wordt gebruikt in componenten die verwijzen naar de pagina, bijvoorbeeld stramienen, paginalijsten, enzovoort.

* **produceer Voorproef** - produceert een voorproef van de pagina die u als duimnagel wilt gebruiken
* **uploadt Beeld** - uploadt een beeld dat u als duimnagel wilt gebruiken
* **Uitgezochte Beeld** - Selecteert een bestaand Activum dat u als duimnagel wilt gebruiken
* **terugkeren** - deze optie wordt beschikbaar nadat u de duimnagel hebt veranderd. Als u de wijziging niet wilt behouden, kunt u die wijziging herstellen voordat u de wijziging opslaat.

### Cloud Services {#cloud-services}

* **de Configuraties van Cloud Service** - bepaalt welke configuratie voor de wolkendiensten voor de pagina wordt gebruikt
* **die van** wordt overgeërfd - voor Levende Exemplaren en de Kopieën van de Taal, worden de wolkenconfiguraties door gebrek geërfd van de Vervaging.
   * Uitschakelen om overerving te overschrijven

### Personalization {#personalization}

#### ContextHub-configuraties {#contexthub}

* **Geërft van** - configuraties ContextHub worden door gebrek geërft van de ouderpagina.
   * Schakel de optie uit om overerving te overschrijven.
* **ContextHub Weg** - Selecteert de [ Configuratie ContextHub ](/help/sites-developing/ch-configuring.md)
* **Weg van Segmenten** - selecteert de [ Weg van Segmenten ](/help/sites-administering/segmentation.md).

#### Doelconfiguratie {#targeting}

Selecteer a [ Merk om een werkingsgebied voor het richten te specificeren.](/help/sites-authoring/target-adobe-campaign.md)

>[!NOTE]
>Deze optie vereist de gebruikersrekening om in de `Target Adminstrators` groep te zijn.

### Machtigingen {#permissions}

Gebruik het **lusje van Toestemmingen** om te bepalen welke gebruikers, groepen, of [ gesloten gebruikersgroepen (CUGs) ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/advanced/closed-user-groups.html) tot de pagina kunnen toegang hebben en/of wijzigen.

* [Machtigingen toevoegen](/help/sites-administering/user-group-ac-admin.md)
* [Gesloten gebruikersgroep bewerken](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)
* Bekijk de [ Effectieve Toestemmingen ](/help/sites-administering/user-group-ac-admin.md)

>[!CAUTION]
>
>Het **lusje van Toestemmingen** staat het uitgeven van de configuraties van de KUG toe die op de aanwezigheid van de `granite:AuthenticationRequired` mengeling worden gebaseerd. Als de paginamachtigingen gebruikend afgekeurde configuraties van de CUG worden gevormd, die op de aanwezigheid van `cq:cugEnabled` bezit worden gebaseerd, wordt een waarschuwingsbericht getoond en de toestemmingen van de CUG zijn niet editable, noch is het Vereiste van de Authentificatie op het [ Geavanceerde ](/help/sites-authoring/editing-page-properties.md#advanced) lusje editable.
>
>
>In zulk een geval moeten de toestemmingen van de KUG in [ klassieke UI ](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md) worden uitgegeven.

>[!NOTE]
>
>Het lusje van Toestemmingen staat niet de verwezenlijking van lege groepen CUG toe, die als eenvoudige manier kunnen nuttig zijn om toegang tot elke gebruiker te ontkennen. Hiervoor moet CRX Explorer worden gebruikt. Zie het document [ Gebruiker, Groep, en Beleid van de Rechten van de Toegang ](/help/sites-administering/user-group-ac-admin.md) voor meer informatie.

### Blauwdruk {#blueprint}

Dit tabblad is alleen zichtbaar voor pagina&#39;s die als blauwdrukken fungeren. De blauwdrukken dienen als basis voor Levende Kopieën, en maken deel uit van [ Multisite Beheer.](/help/sites-administering/msm.md)

* **Uitvoer** - stelt een uitrol van blauwdrukinhoud aan Levende Exemplaren in werking
* **Levend Overzicht van het Exemplaar** - opent een venster om de Levende de paginastructuur van het Exemplaar te doorbladeren
* **Huidige Levende Kopieën** - een lijst van pagina&#39;s die op (namelijk Levende Kopieën van) worden gebaseerd de geselecteerde blauwdrukpagina
* **Configuratie van de Output** - bepaalt de rollout configuratie voor de pagina

### Live kopie {#live-copy}

Dit tabblad is alleen zichtbaar voor pagina&#39;s die zijn geconfigureerd als live kopieën. Zoals met [ blauwdrukken, ](#blueprint) Levende Exemplaren deel van [ Multisite Beheer zijn.](/help/sites-administering/msm.md)

* **synchroniseer** - synchroniseert Levend Exemplaar met blauwdruk, die lokale aanpassingen houden
* **Teruggestelde** - stelt Levend Exemplaar aan staat van blauwdruk terug, verwijderend lokale wijzigingen
* **Onderbreek** - onderbreekt Levend Exemplaar van verdere rollout wijzigingen
* **losmaken** - ontkoppelt Levend Exemplaar van blauwdruk

#### Source {#source}

* Hiermee geeft u het pad van de blauwdruk voor deze actieve kopie weer

#### Status {#status}

* Hiermee geeft u de huidige status van Live kopie van de pagina weer

#### Configuratie {#live-copy-config}

* **Levende Overerving van het Exemplaar** - als gecontroleerd, is de Levende configuratie van het Exemplaar efficiënt op alle kinderen.
* **erven de Vorm van de Output van het Overerven van Bovenliggend** - als gecontroleerd, wordt de rollout configuratie geërft van de ouder van de pagina.
* **kies Configuratie van de Uitvoer** - bepaalt de omstandigheden waaronder de wijzigingen van het Vervagen en slechts beschikbaar worden verspreid wanneer **Inherit de Vorm van de Uitvoer van Bovenliggend** niet wordt geselecteerd
* **Lijst van uitgesloten wegen**

## Pagina-eigenschappen bewerken {#editing-page-properties-1}

U kunt pagina-eigenschappen definiëren:

* Van de **console van Plaatsen**:

   * [ Creërend een pagina ](/help/sites-authoring/managing-pages.md#creating-a-new-page) (een ondergroep van de eigenschappen)

   * Het klikken of het tappen **Eigenschappen**

      * Voor één pagina
      * Voor meerdere pagina&#39;s (alleen een subset van de eigenschappen is beschikbaar voor massabewerking)

* Vanuit de pagina-editor:

   * **Pagina-informatie** gebruiken (en vervolgens **Eigenschappen openen**)

### Vanuit de siteconsole - Eén pagina {#from-the-sites-console-single-page}

Het klikken of het tappen **Eigenschappen** om de pagina eigenschappen te bepalen:

1. Gebruikend de **console van Plaatsen**, navigeer aan de plaats van de pagina waarvoor u eigenschappen bekijken en wilt uitgeven.

1. Selecteer de **optie van Eigenschappen** voor de vereiste pagina die of gebruikt:

   * [Snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-authoring/basic-handling.md#selectionmode)

   De pagina-eigenschappen worden weergegeven met de juiste tabbladen.

1. Bekijk of bewerk de eigenschappen naar wens.

1. Dan gebruik **sparen** om uw updates te bewaren die door **worden gevolgd dicht** zodat kunt u aan de console terugkeren.

### Bij het bewerken van een pagina {#when-editing-a-page}

Wanneer het uitgeven van een pagina, kunt u **Informatie van de Pagina** gebruiken om de paginaeigenschappen te bepalen:

1. Open de pagina waarvan u de eigenschappen wilt bewerken.

1. Selecteer het **pictogram van de Informatie van de Pagina** om het selectiemenu te openen:

   ![ screen_shot_2018-03-22at095740 ](assets/screen_shot_2018-03-22at095740.png)

1. Selecteer **Open Eigenschappen** en een dialoogdoos opent het laten u de eigenschappen uitgeven, die door het aangewezen lusje worden gesorteerd. De volgende knoppen zijn ook beschikbaar aan de rechterkant van de werkbalk:

   * **annuleert**
   * **sparen &amp; Sluiten**

1. Gebruik **sparen &amp; sluit** knoop om de veranderingen te bewaren.

### Van de Console van Plaatsen - Meerdere Pagina&#39;s {#from-the-sites-console-multiple-pages}

Van de **console van Plaatsen**, kunt u verscheidene pagina&#39;s dan gebruiken **Eigenschappen van de Mening** om de pagina eigenschappen te bekijken en/of uit te geven. Dit wordt het bulkgewijs bewerken van pagina-eigenschappen genoemd.

>[!NOTE]
>
>Bulkbewerking van eigenschappen is ook beschikbaar voor Assets. Het is vergelijkbaar, maar op een paar punten verschilt het. Zie [ het Uitgeven Eigenschappen van Veelvoudige Assets ](/help/assets/metadata.md) voor details.
>
>Er is ook de [ BulkRedacteur ](/help/sites-administering/bulk-editor.md). Met deze editor kunt u zoeken naar inhoud van meerdere pagina&#39;s met behulp van GQL (Google Query Language) en de inhoud vervolgens rechtstreeks bewerken met de Bulk-editor voordat u de wijzigingen opslaat in de oorspronkelijke pagina&#39;s.

U kunt meerdere pagina&#39;s selecteren voor bulkbewerking op verschillende manieren, zoals:

* Wanneer het doorbladeren van de **console van Plaatsen**
* Na het gebruiken van **Onderzoek** om van een reeks pagina&#39;s de plaats te bepalen

![ epp-01 ](assets/epp-01.png)

Na het selecteren van de pagina&#39;s en dan het klikken of het tikken van de **optie van Eigenschappen**, worden de bulkeigenschappen getoond:

![ epp-02 ](assets/epp-02.png)

U kunt alleen pagina&#39;s bulksgewijs bewerken die:

* Hetzelfde brontype delen
* Maakt geen deel uit van een livecopy

   * Als een van de pagina&#39;s zich in een live kopie bevindt, wordt een bericht weergegeven wanneer de eigenschappen worden geopend.

Nadat u de optie Bulk bewerken hebt ingevoerd, kunt u het volgende doen:

* **Mening**

  Wanneer u Pagina-eigenschappen voor meerdere pagina&#39;s bekijkt, ziet u het volgende:

   * Een lijst met de betrokken pagina&#39;s

      * U kunt desgewenst selecteren of deselecteren

   * Tabs

      * Net als bij het weergeven van eigenschappen voor één pagina, worden de eigenschappen onder tabbladen geordend.

   * Een subset van eigenschappen

      * Eigenschappen die beschikbaar zijn op alle geselecteerde pagina&#39;s en die expliciet zijn gedefinieerd als beschikbaar voor bulkbewerking, zijn zichtbaar.
      * Als u de paginaselectie tot één pagina reduceert, zijn alle eigenschappen zichtbaar.

   * Algemene eigenschappen met een gemeenschappelijke waarde

      * Alleen eigenschappen met een gemeenschappelijke waarde worden weergegeven in de weergavemodus.
      * Wanneer het gebied multi-waarde (bijvoorbeeld, Markeringen) is, worden de waarden slechts getoond wanneer *allen* gemeenschappelijk zijn. Als slechts enkele van de algemene voorbeelden voorkomen, worden deze alleen weergegeven tijdens het bewerken.

  Wanneer er geen eigenschappen met een gemeenschappelijke waarde bestaan, wordt een bericht weergegeven.

* **geeft** uit

  Bij het bewerken van Pagina-eigenschappen voor meerdere pagina&#39;s:

   * U kunt de waarden in de beschikbare velden bijwerken.

      * De nieuwe waarden worden toegepast op alle geselecteerde pagina&#39;s wanneer u **Gereed** selecteert.
      * Als het veld meerdere waarden heeft (bijvoorbeeld Codes), kunt u een nieuwe waarde toevoegen of een gemeenschappelijke waarde verwijderen.

   * Velden die veel voorkomen, maar verschillende waarden hebben op de verschillende pagina&#39;s, worden aangegeven met een speciale waarde, zoals de tekst `<Mixed Entries>` .

>[!NOTE]
>
>De paginacomponent kan worden gevormd om de gebieden te specificeren beschikbaar voor bulkbewerking. Zie [ Vormend uw pagina voor bulkhet uitgeven van paginaeigenschappen ](/help/sites-developing/bulk-editing.md).
