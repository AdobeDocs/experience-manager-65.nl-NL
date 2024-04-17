---
title: Zoeken in Forms configureren
description: Leer hoe u Zoeken in Forms kunt gebruiken om de selectie van zoekvoorspelden aan te passen die worden gebruikt in de zoekdeelvensters die beschikbaar zijn in AEM consoles en deelvensters van de auteursomgeving.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: f82391d7-e30d-48d2-8f66-88fcae3dfb5f
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '2072'
ht-degree: 1%

---


# Zoeken in Forms configureren{#configuring-search-forms}

Gebruiken **Zoeken in Forms** om de selectie aan te passen van zoekvoorspelden die worden gebruikt in de zoekdeelvensters die beschikbaar zijn in verschillende AEM en/of deelvensters van de auteursomgeving. Als u deze deelvensters aanpast, is de zoekfunctionaliteit veelzijdig op basis van uw specifieke behoeften.

A [predikaat](#predicates-and-their-settings)s is beschikbaar buiten de doos. U kunt meerdere voorspelden toevoegen, waaronder (onder andere) de voorspelling van de eigenschap, om te zoeken naar elementen die overeenkomen met één eigenschap die door u is opgegeven. Of de opties verwijzen naar zoekelementen die overeenkomen met een of meer waarden die u voor een bepaalde eigenschap opgeeft.

U kunt [de zoekformulieren configureren](#configuring-your-search-forms) worden gebruikt in verschillende consoles en de middelenbrowser (bij het bewerken van pagina&#39;s). De [dialoogvensters voor het configureren van deze formulieren](#configuring-your-search-forms) kan worden geraadpleegd via:

* **Gereedschappen**

   * **Algemeen**

      * **Zoeken in Forms**

Wanneer u eerst tot deze console toegang hebt, kunt u zien dat alle configuraties een hangslotsymbool hebben. Dit wijst erop dat de aangewezen configuratie de standaardconfiguratie (uit-van-de-doos) is - en kan niet worden geschrapt. Nadat u de configuratie hebt aangepast, verdwijnt het slot tenzij u [verwijder uw aangepaste configuratie](#deleting-a-configuration-to-reinstate-the-default). In dat geval wordt de standaardinstelling (en de hangslotindicator) hersteld.

![Venster Formulieren zoeken](assets/chlimage_1-374.png)

## Configuraties {#configurations}

De beschikbare standaardconfiguraties zijn:

* **Pagina-editor (zoeken naar documenten):**

  Deze configuratie bepaalt de beschikbare opties wanneer het zoeken naar document in middelenbrowser (wanneer het uitgeven van een pagina).

* **Pagina-editor (zoeken naar afbeeldingen):**

  Deze configuratie bepaalt de beschikbare opties wanneer het zoeken naar beelden in middelenbrowser (wanneer het uitgeven van een pagina).

* **Pagina-editor (Manuscript Search):**

  Deze configuratie bepaalt de beschikbare opties wanneer het zoeken naar manuscripten in middelenbrowser (wanneer het uitgeven van een pagina).

* **Pagina-editor (zoeken naar pagina):**

  Deze configuratie bepaalt de beschikbare opties wanneer het zoeken naar pagina&#39;s in middelenbrowser (wanneer het uitgeven van een pagina).

* **Pagina-editor (zoeken naar alinea&#39;s):**

  Deze configuratie bepaalt de beschikbare opties wanneer het zoeken naar paragrafen in middelenbrowser (wanneer het uitgeven van een pagina).

* **Pagina-editor (zoeken naar producten):**

  Deze configuratie bepaalt de beschikbare opties wanneer het zoeken naar producten in middelenbrowser (wanneer het uitgeven van een pagina).

* **Pagina-editor (Dynamic Media Classic [voorheen Scene7] zoeken)**:

  Deze configuratie definieert de beschikbare opties bij het zoeken naar Scene7-bronnen in de middelenbrowser (bij het bewerken van een pagina).

* **Sites Admin Search Rail**:

  Deze configuratie bepaalt de onderzoeksopties beschikbaar aan de gebruiker wanneer het gebruiken van de onderzoekslijn van de console van Plaatsen.

* **Pagina-editor (videozoekopdracht):**

  Deze configuratie bepaalt de beschikbare opties wanneer het zoeken naar video&#39;s in middelenbrowser (wanneer het uitgeven van een pagina).

* **Middelen Admin Search Rail:**

  Deze configuratie bepaalt de onderzoeksopties beschikbaar aan de gebruiker wanneer het gebruiken van de console van Activa.

* **Zoekspoor voor catalogusbeheer:**

  Deze configuratie bepaalt de onderzoeksopties beschikbaar aan de gebruiker wanneer het zoeken van een handelscatalogus.

* **Zoekspoor voor bestellingen Admin:**

  Deze configuratie bepaalt de onderzoeksopties beschikbaar aan de gebruiker wanneer het zoeken van handelsorden.

* **Zoekspoor voor productverzamelingen Admin:**

  Deze configuratie bepaalt de onderzoeksopties beschikbaar aan de gebruiker wanneer het zoeken van handelsproductinzamelingen.

* **Zoekspoor voor productbeheer:**

  Deze configuratie bepaalt de onderzoeksopties beschikbaar aan de gebruiker wanneer het zoeken van handelsproducten.

* **Zoekspoor voor projectbeheerder:**

  Deze configuratie bepaalt de onderzoeksopties beschikbaar aan de gebruiker wanneer het zoeken van projecten.

## Voorspellen en de bijbehorende instellingen {#predicates-and-their-settings}

### Voorspellen {#predicates}

De volgende predikaten zijn beschikbaar, afhankelijk van de configuratie:

<table>
 <tbody>
  <tr>
   <th>Voorspelend</th>
   <th>Doel</th>
   <th>Instellingen</th>
  </tr>
  <tr>
   <td>Analyse </td>
   <td>Mogelijkheden zoeken/filteren in de Sites-browser bij het weergeven van gegevens met analysemogelijkheden. De zoekfilters van Analytics laden tot aan de in kaart gebrachte aangepaste analytische kolommen.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Element laatst gewijzigd </td>
   <td>Datum waarop het element voor het laatst is gewijzigd.<br /> </td>
   <td>Een aangepaste voorspelling op basis van de datumvoorspelling.</td>
  </tr>
  <tr>
   <td>Onderdelen </td>
   <td>Hiermee kan een auteur zoeken/filteren op pagina's die een specifieke component bevatten. Bijvoorbeeld een afbeeldingsgalerie.<br /> </td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam*</li>
     <li>Diepte van eigenschap</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Datum </td>
   <td>Op schuifregelaars gebaseerde zoekopdracht naar elementen op basis van een datumeigenschap.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Datumbereik </td>
   <td>Zoek in een opgegeven bereik gemaakte elementen naar een datumeigenschap. In het deelvenster Zoeken kunt u begin- en einddatums opgeven.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam*</li>
     <li>Bereik tekst (Van)*</li>
     <li>Bereik tekst (naar)*</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Vervalstatus </td>
   <td>Zoeken in middelen op basis van vervalstatus.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Bestandsgrootte </td>
   <td>Elementen zoeken op basis van hun grootte.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Optiepad</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Verborgen filter</td>
   <td>Een filter op eigenschap en waarde, niet zichtbaar voor de gebruiker.</td>
   <td>
    <ul>
     <li>Eigenschapnaam</li>
     <li>Waarde van eigenschap</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Opties </td>
   <td><p>De opties zijn inhoudsknooppunten die door de gebruiker zijn gemaakt.</p> <p>Zie <a href="#addinganoptionspredicate">Vooraf ingestelde opties toevoegen</a> voor meer informatie .</p> </td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>JSON-pad</li>
     <li>Eigenschapnaam*</li>
     <li>Enkel selecteren</li>
     <li>Optiepad</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Opties, eigenschap </td>
   <td>Zoeken op een eigenschap van de optie.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Pad naar knooppunt Opties<br /> </li>
     <li>Enkel selecteren</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Paginastatus </td>
   <td>Pagina's zoeken op basis van hun status.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam publiceren</li>
     <li>Eigenschapnaam van LiveCopy</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Pad </td>
   <td>Zoeken naar elementen die zich onder een specifiek pad bevinden.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Zoekpad toevoegen</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Eigenschap </td>
   <td>Zoeken op een opgegeven eigenschap.</td>
   <td>none</td>
  </tr>
  <tr>
   <td>Status publiceren </td>
   <td>Middelen zoeken op basis van hun publicatiestatus</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Bereik </td>
   <td>Zoekbronnen binnen een opgegeven bereik. In het paneel van het Onderzoek, kunt u minimum en maximumwaarden voor de waaier specificeren.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Bereik-opties </td>
   <td>Een specifieke zoekvoorspelling voor elementen en hetzelfde als gewone voorspelling van Slider. Is nog steeds beschikbaar vanwege compatibiliteitsproblemen met oudere versies.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Optiepad</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Classificatie </td>
   <td>Elementen zoeken op basis van hun waardering.<br /> </td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Optiepad</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Relatieve datum </td>
   <td>Elementen zoeken op basis van de relatieve datum waarop ze zijn gemaakt<br /> </td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Relatieve datum</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Schuifbereik </td>
   <td>Een gemeenschappelijke onderzoeksvoorspelling die de waaiervoorspelling met het schuifvermogen uitbreidt. De waarde van de gezochte eigenschap moet tussen de schuifregelaargrenzen liggen.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Tag </td>
   <td>Zoeken in elementen op basis van tags. U kunt het bezit van de Weg vormen om diverse markeringen in de lijst van Markeringen te bevolken.</td>
   <td>
    <ul>
     <li>Veldlabel</li>
     <li>Eigenschapnaam*</li>
     <li>Optiepad</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Tags </td>
   <td>Zoeken op basis van tags.</td>
   <td>
    <ul>
     <li>Plaatsaanduiding</li>
     <li>Eigenschapnaam*</li>
     <li>Beschrijving</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* De algemene zoekvoorspelling wordt gedefinieerd in:
>  `/libs/cq/gui/components/common/admin/customsearch/searchpredicates`
>
>* Zoekvoorspellingen die alleen betrekking hebben op sitebeheer (klassieke UI) bevinden zich onder:
>  `/libs/cq/gui/components/siteadmin/admin/searchpanel/searchpredicates`
>   * Deze zijn verouderd en zijn alleen beschikbaar voor achterwaartse compatibiliteit.
>
>Deze informatie is uitsluitend ter referentie. Niet wijzigen `/libs`.

### Instellingen voor voorspelling {#predicate-settings}

Afhankelijk van de voorspelling is een selectie van instellingen beschikbaar voor configuratie:

* **Veldlabel**

  Het label dat wordt weergegeven als de inklapbare koptekst of als veldlabel van de voorspelling.

* **Beschrijving**

  Beschrijvende details voor de gebruiker.

* **Plaatsaanduiding**

  Lege tekst of de plaatsaanduiding van de voorspelling voor het geval er geen filtertekst wordt ingevoerd.

* **Eigenschapnaam**

  De eigenschap waarop moet worden gezocht. Er wordt een relatief pad en de jokertekens gebruikt `*/*/*` Geef de diepte van de eigenschap op ten opzichte van de `jcr:content` knooppunt (elke asterisk vertegenwoordigt één knooppuntniveau).

  Als u slechts op een eerste-vlakke kindknoop van het middel wilt zoeken dat heeft `x` eigenschap op de `jcr:content` knooppuntgebruik `*/jcr:content/x`

* **Diepte van eigenschap**

  De maximumdiepte om naar dat bezit binnen de middelen te zoeken. Een zoekopdracht naar die eigenschap kan dus worden uitgevoerd op een resource en recursieve onderliggende elementen totdat het niveau van de onderliggende objecten gelijk is aan de opgegeven diepte.

* **Waarde van eigenschap**

  De eigenschapswaarde als een absolute tekenreeks of als expressietaal, bijvoorbeeld `cq:Page` of

  `${empty requestPathInfo.suffix ? "/content" : requestPathInfo.suffix}`.

* **Bereik tekst**

  Het label van het bereikveld in het dialoogvenster **Datumbereik** voorspellen.

* **Optiepad**

  De gebruiker kan het pad selecteren met behulp van de Padbrowser op het tabblad Voorspelfunctie. Na het selecteren **+**, wordt het pictogram gebruikt om de selectie toe te voegen aan de lijst met geldige opties (en vervolgens de optie **-** pictogram om te verwijderen, indien nodig).

  De opties zijn inhoudsknooppunten die door de gebruiker zijn gemaakt en die de volgende structuur hebben:

  `(jcr:primaryType = nt:unstructured, value (String), jcr:title (String))`

* **Pad naar knooppunt Opties**
In feite hetzelfde als het **Pad naar opties** Alleen dit gebeurt in het gemeenschappelijke voorspelde veld, het andere is specifiek voor elementen.

* **Enkel selecteren**
Als deze optie is ingeschakeld, worden de opties weergegeven als selectievakjes die slechts één selectie toestaan. Als u per ongeluk een selectievakje hebt ingeschakeld, kan dit worden uitgeschakeld.

* **Eigenschapnamen voor publicaties en live kopiëren**
De etiketten voor publiceren en levende exemplaarcontroledozen voor het specifieke predikaat van Plaatsen.

* De &amp;laatste; op de veldlabels in de **Instellingen** betekent dat de velden verplicht zijn en dat er een foutbericht wordt weergegeven als de velden leeg zijn gelaten.

## Uw zoekopdracht configureren, Forms {#configuring-your-search-forms}

### Een aangepaste configuratie maken/openen {#creating-opening-a-customized-configuration}

1. Navigeren naar **Gereedschappen** >>  **Algemeen** >> **Zoeken in Forms**.

1. Selecteer de configuratie die u wilt aanpassen.
1. Gebruik de **Bewerken** om de configuratie voor bijwerken te openen.
1. Als u een nieuwe aanpassing wilt maken, is het waarschijnlijk verstandig [nieuwe basisvelden toevoegen en de instellingen definiëren](#add-edit-a-predicate-field-and-define-field-settings) zoals vereist. Als er al een aanpassing is, kunt u een bestaand veld selecteren en [de instellingen bijwerken](#add-edit-a-predicate-field-and-define-field-settings).
1. Selecteren **Gereed** om de configuratie op te slaan.

   >[!NOTE]
   >
   >De aangepaste configuraties worden (indien van toepassing) opgeslagen onder:
   >
   >* `/apps/cq/gui/content/facets/<option>`
   >* `/apps/commerce/gui/content/facets/<option>`

### Een voorspelbaar veld toevoegen/bewerken en veldinstellingen definiëren {#add-edit-a-predicate-field-and-define-field-settings}

U kunt velden toevoegen of bewerken en de instellingen van velden definiëren/bijwerken:

1. [Open de aangepaste configuratie](#creating-opening-a-customized-configuration) voor bijwerken.
1. Als u een gebied wilt toevoegen, open **Predicate selecteren** en sleep de vereiste voorspelling naar de gewenste locatie. Bijvoorbeeld de **Datumbereik**:

   ![Een zoekformulier bewerken](assets/chlimage_1-375.png)

1. Afhankelijk van of:

   * U voegt een veld toe:

     Na het toevoegen van predikaat, **Instellingen** wordt geopend en worden de eigenschappen weergegeven die kunnen worden gedefinieerd.

   * U wilt een bestaande voorspelling bijwerken:

     Selecteer het voorloopveld (rechts) en open vervolgens het **Instellingen** tab.

   De instellingen voor de **Datumbereik**:

   ![Eigenschappen voor Datumbereik](assets/chlimage_1-376.png)

1. Breng de gewenste wijzigingen aan en bevestig deze met **Gereed**.

### Een voorvertoning weergeven van de zoekconfiguratie {#previewing-the-search-configuration}

1. Selecteer het pictogram Voorvertoning:

   ![Voorbeeld van zoekformulieren](do-not-localize/chlimage_1-31.png)

1. Op deze manier worden de zoekformulieren weergegeven zoals ze worden weergegeven (volledig uitgevouwen) in de kolom Zoeken van de desbetreffende console.

   ![Een voorbeeld van het zoekformulier bekijken](assets/chlimage_1-377.png)

1. **Sluiten** de voorvertoning zodat u de configuratie kunt terugzetten en voltooien.

### Een voorspelbaar veld verwijderen {#deleting-a-predicate-field}

1. [Open de aangepaste configuratie](#creating-opening-a-customized-configuration) voor bijwerken.
1. Selecteer het voorloopveld (rechts) en open het dialoogvenster **Instellingen** en selecteert u vervolgens de **Verwijderen** pictogram (linksonder).

   ![Pictogram Verwijderen](do-not-localize/chlimage_1-32.png)

1. Een dialoogvenster vraagt om bevestiging van de verwijderactie.

1. Bevestig dit en eventuele andere wijzigingen met **Gereed**.

### Een configuratie verwijderen (om de standaardinstelling te herstellen) {#deleting-a-configuration-to-reinstate-the-default}

Nadat u een configuratie hebt aangepast, treedt dit de gebreken met voeten. U kunt de standaardconfiguratie herstellen door uw aangepaste configuratie te schrappen.

>[!NOTE]
>
>U kunt geen van beide standaardconfiguraties verwijderen.

Het schrappen van een aangepaste configuratie wordt gedaan van de console:

1. Selecteer de vereiste configuratie (bijvoorbeeld **Pagina-editor (zoeken in alinea&#39;s)**) en vervolgens de **Verwijderen** pictogram in de werkbalk:

   ![Een formulier verwijderen](assets/chlimage_1-378.png)

1. De aangepaste configuratie wordt verwijderd en de standaardinstelling wordt hersteld (dit wordt aangegeven door het opnieuw verschijnen van het hangslotsymbool in de console).

### Voorwaarden voor opties toevoegen {#adding-options-predicates}

Met de voorspelling van opties (Opties, eigenschap Opties) kunt u een item configureren waarnaar moet worden gezocht. Ze worden gebruikt om rechtstreeks onder de pagina naar iets te zoeken, bijvoorbeeld een eigenschap op het paginaknooppunt.

In het volgende voorbeeld (om te zoeken op basis van de sjabloon die wordt gebruikt om een pagina te maken) worden de desbetreffende stappen geïllustreerd:

1. Maak het knooppunt waarin de eigenschap wordt gedefinieerd waarop moet worden gezocht.

   U hebt een basisknooppunt met definities van de afzonderlijke opties nodig om beschikbaar te zijn voor de gebruiker.

   De knooppunten voor de afzonderlijke opties hebben de volgende eigenschappen nodig:

   * `jcr:title` - het veldetiket dat in de zoekrail moet worden aangebracht
   * `value` - de waarde van de eigenschap waarop moet worden gezocht

   ![Opties toevoegen in CRXDE](assets/chlimage_1-379.png)

   >[!NOTE]
   >
   >Do ***niet*** om het even wat in `/libs` pad.
   >
   >Dit komt omdat de inhoud van `/libs` wordt de volgende keer overschreven wanneer u een upgrade uitvoert van uw exemplaar (en kan worden overschreven wanneer u een hotfix- of functiepakket toepast).
   >
   >De aanbevolen methode voor configuratie en andere wijzigingen is:
   >
   >1. Het vereiste item opnieuw maken, zoals dit bestaat in `/libs`, onder `/apps`. In dit geval:
   >1. `/libs/cq/gui/content/common/options/predicates`
   >1. Breng wijzigingen aan in `/apps.`

1. Open de **Zoeken in Forms** console en selecteer de configuratie u wilt bijwerken. Bijvoorbeeld: **Sites Admin Search Rail**.

   Klik vervolgens op de knop **Zoekformulieren bewerken** pictogram.

1. Afhankelijk van de configuratie voegt u een **Opties** of **Opties, eigenschap** naar de configuratie.
1. Werk de velden bij, met name:

   * **Eigenschapnaam**

     Specifiek het knoopbezit dat op de doelknopen moet worden gezocht. Bijvoorbeeld:

     `jcr:content/cq:template`

   * **Pad naar knooppunt Option**

     Selecteer het pad naar de locatie waar uw opties staan. Bijvoorbeeld:

     `/apps/cq/gui/content/common/options/predicates/templatetype`

   ![Eigenschapspad toevoegen](assets/chlimage_1-380.png)

1. Selecteren **Gereed** om uw configuratie op te slaan.
1. Navigeer aan de aangewezen console (in dit voorbeeld, **Sites**) en opent u de **Zoeken** spoorwegen. De nieuwe zoekformulieren en de verschillende opties zijn zichtbaar. Selecteer de gewenste optie zodat u de zoekresultaten kunt zien:

   ![De eindresultaten](assets/chlimage_1-381.png)

## Gebruikersmachtigingen {#user-permissions}

In de volgende tabel worden de machtigingen weergegeven die vereist zijn voor het uitvoeren van bewerkingen, verwijderen en voorvertoningen van handelingen op zoekformulieren.

<table>
 <tbody>
  <tr>
   <td><strong>Handeling</strong></td>
   <td><strong>Machtigingen</strong></td>
  </tr>
  <tr>
   <td>Bewerken </td>
   <td>Lezen, schrijven toestemmingen op <code>/apps </code>knooppunt.</td>
  </tr>
  <tr>
   <td>Verwijderen</td>
   <td>De machtigingen Lezen, Schrijven en Verwijderen voor de <code>/apps</code> node</td>
  </tr>
  <tr>
   <td>Voorvertoning</td>
   <td>De machtigingen Lezen, Schrijven en Verwijderen voor de <code>/var/dam/content</code> knooppunt.<br /> Lezen, schrijven toestemmingen op <code>/apps</code> knooppunt.</td>
  </tr>
 </tbody>
</table>
