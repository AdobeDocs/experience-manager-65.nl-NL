---
title: De invoegtoepassingen van de Rich Text Editor configureren
description: Leer hoe u de insteekmodules van de Adobe Experience Manager Rich Text Editor configureert voor het inschakelen van afzonderlijke functies.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 6f5e650c99017c4b2f04ca8495eea8481b3236cd
workflow-type: tm+mt
source-wordcount: '4383'
ht-degree: 0%

---


# Plug-ins {#configure-the-rich-text-editor-plug-ins} van de Rich Text Editor configureren

De functionaliteit van RTE wordt beschikbaar gemaakt via een reeks stop-ins, elk met eigenschappen bezit. U kunt het eigenschapbezit vormen om, één of meerdere eigenschappen van RTE toe te laten of onbruikbaar te maken. Dit artikel beschrijft hoe te om de stop-ins specifiek te vormen RTE.

Voor details over de andere configuraties RTE, zie [Rich Text Editor](/help/sites-administering/rich-text-editor.md) vormen.

>[!NOTE]
>
>Als u met CRXDE Lite werkt, wordt aangeraden de wijzigingen regelmatig op te slaan met de optie [!UICONTROL Save All].

## Een insteekmodule activeren en de eigenschap features {#activateplugin} configureren

Voer de volgende stappen uit om een plug-in te activeren. Sommige stappen zijn alleen nodig wanneer u een insteekmodule voor het eerst configureert, omdat de bijbehorende knooppunten niet bestaan.

Standaard zijn `format`, `link`, `list`, `justify` en `control` plug-ins en alle bijbehorende functies in RTE ingeschakeld.

>[!NOTE]
>
>Het respectieve `rtePlugins` knooppunt wordt bedoeld als `<rtePlugins-node>` om dubbel werk in dit artikel te vermijden.

1. Zoek met CRXDE Lite de tekstcomponent voor uw project.
1. Creeer de ouderknoop van `<rtePlugins-node>` als het niet bestaat, alvorens om het even welke stop-ins te vormen RTE:

   * Afhankelijk van uw component zijn de bovenliggende knooppunten:

      * `config: .../text/cq:editConfig/cq:inplaceEditing/config`
      * een alternatief configuratieknooppunt: `.../text/cq:editConfig/cq:inplaceEditing/inplaceEditingTextConfig`
      * `text: .../text/dialog/items/tab1/items/text`
   * Zijn van type: **jcr:primaryType** `cq:Widget`
   * Beide hebben de volgende eigenschap:

      * **Naam** `name`
      * **Type** `String`
      * **Waarde** `./text`


1. Afhankelijk van de interface u voor vormt, creeer een knoop `<rtePlugins-node>`, als het niet bestaat:

   * **Naam** `rtePlugins`
   * **Type** `nt:unstructured`

1. Maak hieronder een knooppunt voor elke plug-in die u wilt activeren:

   * **Type** `nt:unstructured`
   * **Geef** de plug-in-id van de vereiste plug-in op.

Nadat u een insteekmodule hebt geactiveerd, volgt u deze richtlijnen om de eigenschap `features` te configureren.

|  | Alle functies inschakelen | Enkele specifieke functies inschakelen | Alle functies uitschakelen |
|---|---|---|---|
| Naam | functies | functies | functies |
| Type | Tekenreeks | String[] (multi-string; Stel Type in op String en klik op Meerdere in CRXDE Lite) | Tekenreeks |
| Waarde | `*` (een sterretje) | ingesteld op een of meer functiewaarden | - |

## Begrijp de findreplace plug-in {#findreplace}

Voor de `findreplace` plug-in is geen configuratie nodig. Het werkt uit de doos.

Wanneer u de vervangingsfunctie gebruikt, moet de te vervangen tekenreeks op hetzelfde moment worden ingevoerd als de zoektekenreeks. U kunt echter nog steeds op Zoeken klikken om de tekenreeks te zoeken voordat u deze vervangt. Als de vervangingstekenreeks wordt ingevoerd nadat op Zoeken is geklikt, wordt de zoekopdracht opnieuw ingesteld op het begin van de tekst.

Het dialoogvenster Zoeken en vervangen wordt transparant wanneer op Zoeken wordt geklikt en wordt dekkend wanneer op Vervangen wordt geklikt. Hierdoor kan de auteur de tekst controleren die de auteur vervangt. Als gebruikers op Alles vervangen klikken, wordt het dialoogvenster gesloten en wordt het aantal aangebrachte vervangingen weergegeven.

## De plakmodi {#pastemodes} configureren

Wanneer het gebruiken van RTE, kunnen de auteurs inhoud in één van de volgende drie wijzen kleven:

* **Browsermodus**: Plak tekst met gebruik van de standaardimplementatie van de browser. Het is geen aanbevolen methode omdat hierdoor ongewenste opmaakcodes kunnen ontstaan.

* **Modus** Onbewerkte tekst: Plak de inhoud van het klembord als onbewerkte tekst. Alle elementen van stijl en opmaak worden uit de gekopieerde inhoud verwijderd voordat deze in AEM component worden ingevoegd.

* **MS Word-modus**: Plak de tekst, inclusief tabellen, met opmaak wanneer u kopieert vanuit MS Word. Het kopiëren en plakken van tekst uit een andere bron, zoals een webpagina of MS Excel, wordt niet ondersteund en behoudt alleen de gedeeltelijke opmaak.

### De beschikbare plakopties op de RTE-werkbalk configureren {#configure-paste-options-available-on-the-rte-toolbar}

U kunt sommige, alle, of geen van deze drie pictogrammen aan uw auteurs in de toolbar van RTE verstrekken:

* **[!UICONTROL Paste (Ctrl+V)]**: Kan vooraf worden geconfigureerd voor een van de drie bovenstaande plakmodi.

* **[!UICONTROL Paste as Text]**: Geeft functionaliteit voor de modus Onbewerkte tekst.

* **[!UICONTROL Paste from Word]**: Biedt functionaliteit in de modus MS Word.

Om RTE te vormen om de vereiste pictogrammen te tonen, volg deze stappen.

1. Navigeer naar de component, bijvoorbeeld `/apps/<myProject>/components/text`.
1. Navigeer naar het knooppunt `rtePlugins/edit`. Zie [Een insteekmodule activeren](#activateplugin) als het knooppunt niet bestaat.
1. Maak de eigenschap `features` op het knooppunt `edit` en voeg een of meer functies toe. Sla alle wijzigingen op.

### Het gedrag van het pictogram Plakken (Ctrl+V) en de sneltoets {#configure-the-behavior-of-the-paste-ctrl-v-icon-and-shortcut} configureren

U kunt het gedrag van het pictogram **[!UICONTROL Paste (Ctrl+V)]** vooraf configureren door de volgende stappen uit te voeren. Deze configuratie definieert ook het gedrag van sneltoetsen Ctrl+V die auteurs gebruiken om inhoud te plakken.

De configuratie staat voor de volgende drie soorten gebruiksgevallen toe:

* Plak tekst met gebruik van de standaardimplementatie van de browser. Het is geen aanbevolen methode omdat hierdoor ongewenste opmaakcodes kunnen ontstaan. Gevormd gebruikend `browser` hieronder.

* Plak de inhoud van het klembord als onbewerkte tekst. Alle elementen van stijl en opmaak worden uit de gekopieerde inhoud verwijderd voordat deze in AEM component worden ingevoegd. Gevormd gebruikend `plaintext` hieronder.

* Plak de tekst, inclusief tabellen, met opmaak wanneer u kopieert vanuit MS Word. Het kopiëren en plakken van tekst uit een andere bron, zoals een webpagina of MS Excel, wordt niet ondersteund en behoudt alleen de gedeeltelijke opmaak. Gevormd gebruikend `wordhtml` hieronder.

1. Navigeer in uw component naar `<rtePlugins-node>/edit`-knooppunt. Maak de knooppunten als deze niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. In de `edit` knoop creeer een bezit gebruikend de volgende details:

   * **Naam** `defaultPasteMode`
   * **Type** `String`
   * **** ValueOne van de vereiste plakwijze  `browser`,  `plaintext`of  `wordhtml`.

### Configureer de toegestane indelingen bij het plakken van inhoud {#pasteformats}

De plakken-als-Microsoft-Word (`paste-wordhtml`) wijze kan verder worden gevormd zodat u kunt uitdrukkelijk bepalen welke stijlen worden toegestaan wanneer het kleven in AEM van een ander programma, zoals Microsoft Word.

Als u bijvoorbeeld alleen vette indelingen en lijsten wilt toestaan bij het plakken in AEM, kunt u de andere indelingen filteren. Dit wordt configureerbare het kleven het filtreren genoemd, die voor allebei kan worden gedaan:

* [Tekst](#pastemodes)
* [Koppelingen](#linkstyles)

Voor koppelingen kunt u ook de protocollen definiëren die automatisch worden geaccepteerd.

Om te vormen welke formaten worden toegestaan wanneer het kleven van tekst in AEM van een ander programma:

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/edit`. Maak de knooppunten als deze niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak een knooppunt onder het knooppunt `edit` voor de HTML-plakregels:

   * **Naam** `htmlPasteRules`
   * **Type** `nt:unstructured`

1. Maak een knooppunt onder `htmlPasteRules` voor de details van de toegestane basisindelingen:

   * **Naam** `allowBasics`
   * **Type** `nt:unstructured`

1. Als u de afzonderlijke geaccepteerde indelingen wilt beheren, maakt u een of meer van de volgende eigenschappen op het knooppunt `allowBasics`:

   * **Naam** `bold`
   * **Naam** `italic`
   * **Naam** `underline`
   * **Naam** `anchor`  (voor zowel koppelingen als benoemde ankers)
   * **Naam** `image`

   Alle eigenschappen zijn van **Type** `Boolean`, zodat kunt u in de juiste **Waarde** het vinkje selecteren of verwijderen om de functionaliteit in of uit te schakelen.

   >[!NOTE]
   >
   >Indien niet expliciet gedefinieerd, wordt de standaardwaarde true gebruikt en wordt de opmaak geaccepteerd.

1. Andere indelingen kunnen ook worden gedefinieerd met behulp van een reeks andere eigenschappen of knooppunten, die ook worden toegepast op het knooppunt `htmlPasteRules`:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschap</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>allowBlockTags</td>
   <td>Tekenreeks[]</td>
   <td><p>Hiermee definieert u de lijst met blokcodes die zijn toegestaan.</p> <p>Enkele mogelijke blokcodes zijn:</p>
    <ul>
     <li>koppen (h1, h2, h3)</li>
     <li>lid p)</li>
     <li>lijsten (ol, ul)</li>
     <li>tabellen (tabel)</li>
    </ul> </td>
  </tr>
  <tr>
   <td>fallbackBlockTag</td>
   <td>Tekenreeks</td>
   <td><p>Definieert de bloktag die wordt gebruikt voor blokken met een bloktag die niet in allowBlockTags zijn opgenomen.</p> <p> p is in de meeste gevallen voldoende.</p> </td>
  </tr>
  <tr>
   <td>table</td>
   <td>nt:ongestructureerd</td>
   <td><p>Bepaalt het gedrag wanneer het kleven van lijsten.<br /> </p> <p>Dit knooppunt moet de eigenschap <code>allow</code> (type <code>Boolean</code>) hebben om te bepalen of het plakken van tabellen is toegestaan.</p> <p>Als <code>allow</code> aan <code>false</code> wordt geplaatst, moet u het bezit <code>ignoreMode</code> (type<code> String</code>) specificeren om te bepalen hoe de gekleefde lijstinhoud wordt behandeld. Geldige waarden voor <code>ignoreMode</code> zijn:</p>
    <ul>
     <li><code>remove</code>: Hiermee verwijdert u tabelinhoud.</li>
     <li><code>paragraph</code>: Hiermee zet u tabelcellen om in alinea's.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>list</td>
   <td>nt:ongestructureerd</td>
   <td><p>Hiermee definieert u het gedrag bij het plakken van lijsten.<br /> </p> <p>U moet de eigenschap <code>allow</code> (type <code>Boolean</code>) hebben om te definiëren of het plakken van lijsten is toegestaan.</p> <p>Als <code>allow</code> aan <code>false</code> wordt geplaatst, moet u het bezit <code>ignoreMode</code> (type <code>String</code>) specificeren om te bepalen hoe te om het even welke gekleefde lijstinhoud te behandelen. Geldige waarden voor <code>ignoreMode</code> zijn:</p>
    <ul>
     <li><code>remove</code>: Hiermee verwijdert u de inhoud van de lijst.</li>
     <li><code>paragraph</code>: Hiermee zet u lijstitems om in alinea's.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Voorbeeld van een geldige `htmlPasteRules`-structuur:

```xml
"htmlPasteRules": {
    "allowBasics": {
        "italic": true,
        "link": true
    },
    "allowBlockTags": [
        "p", "h1", "h2", "h3"
    ],
    "list": {
        "allow": false,
        "ignoreMode": "paragraph"
    },
    "table": {
        "allow": true,
        "ignoreMode": "paragraph"
    }
}
```

1. Sla alle wijzigingen op.

## Tekststijlen configureren {#textstyles}

Auteurs kunnen stijlen toepassen om de weergave van een deel van de tekst te wijzigen. De stijlen zijn gebaseerd op CSS-klassen die u vooraf definieert in uw CSS-stijlpagina. Stileerde inhoud wordt ingesloten in `span`-tags met behulp van het `class`-kenmerk om naar de CSS-klasse te verwijzen. Bijvoorbeeld:

`<span class=monospaced>Monospaced Text Here</span>`

Wanneer de plug-in Stijlen voor de eerste keer is ingeschakeld, zijn er geen standaardstijlen beschikbaar. De pop-uplijst is leeg. Ga als volgt te werk om de auteurs stijlen te voorzien:

* Schakel de vervolgkeuzelijst Stijl in.
* Geef de locatie(s) van de stijlpagina(&#39;s) op.
* Geef de afzonderlijke stijlen op die u kunt selecteren in de vervolgkeuzelijst Stijl.

Voor latere (re-)configuraties, zeg om meer stijlen toe te voegen, volg slechts de instructies om naar een nieuw stijlblad te verwijzen en de extra stijlen te specificeren.

>[!NOTE]
>
>Stijlen kunnen ook worden gedefinieerd voor [tabellen of tabelcellen](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tablestyles). Deze configuraties vereisen afzonderlijke procedures.

### De vervolgkeuzelijst Stijl {#styleselectorlist} inschakelen

Hiervoor schakelt u de insteekmodule Stijlen in.

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/styles`. Maak de knooppunten als deze niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak de eigenschap `features` op het knooppunt `styles`:

   * **Naam** `features`
   * **Type** `String`
   * **Waarde** `*`  (sterretje)

1. Sla alle wijzigingen op.

>[!NOTE]
>
>Zodra de plug-in Stijlen is ingeschakeld, wordt de vervolgkeuzelijst Stijl weergegeven in het dialoogvenster Bewerken. De lijst is echter leeg omdat er geen stijlen zijn geconfigureerd.

### De locatie van het stijlblad opgeven {#locationofstylesheet}

Geef vervolgens de locatie(s) op van de stijlpagina(&#39;s) waarnaar u wilt verwijzen:

1. Navigeer naar het hoofdknooppunt van de tekstcomponent, bijvoorbeeld `/apps/<myProject>/components/text`.
1. Voeg de eigenschap `externalStyleSheets` toe aan het bovenliggende knooppunt van `<rtePlugins-node>`:

   * **Naam** `externalStyleSheets`
   * **Type** `String[]`  (meerdere tekenreeksen; klik op  **** Meerdere CRXDE)
   * **Waarde(s)** Het pad en de bestandsnaam van elk stijlblad dat u wilt opnemen. Gebruik repository paden.

   >[!NOTE]
   >
   >U kunt op elk later moment verwijzingen naar extra stijlbladen toevoegen.

1. Sla alle wijzigingen op.

>[!NOTE]
>
>Wanneer u RTE gebruikt in een dialoogvenster (klassieke gebruikersinterface), kunt u stijlpagina&#39;s opgeven die zijn geoptimaliseerd voor RTF-bewerking. Vanwege technische beperkingen gaat de CSS-context verloren in de editor, dus u kunt deze context emuleren om de WYSIWYG-ervaring te verbeteren.
>
>De rijke Redacteur van de Tekst gebruikt een containerDOM element met een identiteitskaart van `CQrte` die kan worden gebruikt om verschillende stijlen voor het bekijken en het uitgeven te verstrekken:
>
>
```
>#CQ td {
> // defines the style for viewing
> }
>```
>
>
```
>#CQrte td {
> // defines the style for editing
> }
>```

### Geef de beschikbare stijlen op in de pop-uplijst {#stylesindropdown}

1. In de componentendefinitie, navigeer aan de knoop `<rtePlugins-node>/styles`, zoals gecreeerd in [Toelatend de stijldrop-down selecteur](#styleselectorlist).
1. Onder de knoop `styles`, creeer een nieuw knoop (ook genoemd `styles`) om de lijst te houden die beschikbaar wordt gemaakt:

   * **Naam** `styles`
   * **Type** `cq:WidgetCollection`

1. Maak een nieuw knooppunt onder het knooppunt `styles` voor een afzonderlijke stijl:

   * **Naam**, u kunt de naam specificeren, maar het zou voor de stijl geschikt moeten zijn
   * **Type** `nt:unstructured`

1. Voeg de eigenschap `cssName` toe aan dit knooppunt om naar de CSS-klasse te verwijzen:

   * **Naam** `cssName`
   * **Type** `String`
   * **** ValueThe name of the CSS class (without a previous &#39;.&#39;; bijvoorbeeld `cssClass` in plaats van `.cssClass`)

1. Voeg de eigenschap `text` toe aan hetzelfde knooppunt. Hiermee wordt de tekst gedefinieerd die wordt weergegeven in het selectievak:

   * **Naam** `text`
   * **Type** `String`
   * **** ValueDescription of the style; wordt weergegeven in het keuzemenu Stijl.

1. Sla de wijzigingen op.

   Herhaal bovenstaande stappen voor elke vereiste stijl.

### RTE configureren voor optimale woordeinden in het Japans {#jpwordwrap}

Auteurs die AEM gebruiken om inhoud in de Japanse taal te schrijven, kunnen een stijl toepassen op tekens om regeleinde te voorkomen wanneer een regeleinde niet vereist is. Op deze manier kunnen auteurs de zinnen op de gewenste positie laten afbreken. De stijl voor deze functionaliteit is gebaseerd op CSS-klasse die vooraf is gedefinieerd in de CSS-stijlpagina.

>[!NOTE]
>
>Deze eigenschap vereist minstens AEM 6.5 Service Pack 1.

Ga als volgt te werk om de stijl te maken die auteurs op Japanse tekst kunnen toepassen:

1. Maak een nieuw knooppunt onder het knooppunt Stijlen. Zie [een nieuwe stijl specificeren](#stylesindropdown).
   * Naam: `jpn-word-wrap`
   * Type: Verzenden:unstructure

1. Voeg de eigenschap `cssName` toe aan het knooppunt om naar de CSS-klasse te verwijzen. Deze klassenaam is een gereserveerde naam voor de functie voor tekstomloop in Japans.
   * Naam: `cssName`
   * Type: `String`
   * Waarde: `jpn-word-wrap` (zonder voorafgaande `.`)

1. Voeg de bezitstekst aan de zelfde knoop toe. De waarde is de naam van de stijl die de auteurs zien wanneer ze de stijl selecteren.
   * Naam: `text`
*Type: 
`String`
   * Waarde: `Japanese word-wrap`

1. Maak een stijlpagina en geef het pad op. Zie [locatie van stijlpagina](#locationofstylesheet) specificeren. Voeg de volgende inhoud aan de stijlpagina toe. Wijzig de achtergrondkleur naar wens.

   ```css
   .text span.jpn-word-wrap {
       display:inline-block;
   }
   .is-edited span.jpn-word-wrap {
       background-color: #ffddff;
   }
   ```

   ![Stijlblad om de functie voor tekstomloop in Japans beschikbaar te maken voor auteurs](assets/rte_jpwordwrap_stylesheet.jpg)

## De alineaopmaak {#paraformats} configureren

Om het even welke tekst authored in RTE wordt geplaatst binnen een blokmarkering, het gebrek is `<p>`. Als u de insteekmodule `paraformat` inschakelt, geeft u via een vervolgkeuzelijst aanvullende blokcodes op die aan alinea&#39;s kunnen worden toegewezen. Alineaopmaak bepaalt het alineatype door de juiste bloktag toe te wijzen. De auteur kan deze selecteren en toewijzen met de kiezer Indeling. De voorbeeldbloklabels omvatten onder andere de standaardalinea &lt;p> en koppen &lt;h1>, &lt;h2> enzovoort.

>[!CAUTION]
>
>Deze plug-in is niet geschikt voor inhoud met een complexe structuur, zoals lijsten of tabellen.

>[!NOTE]
>
>Als een bloktag, bijvoorbeeld een tag &lt;hr>, niet aan een alinea kan worden toegewezen, is dit geen geldig gebruiksgeval voor een insteekmodule voor paraformat.

Wanneer de insteekmodule Alineopmaak voor het eerst is ingeschakeld, zijn er geen standaardalineaopmaak beschikbaar. De pop-uplijst is leeg. Ga als volgt te werk om de auteurs alineaopmaak te bieden:

* Schakel de vervolgkeuzelijst Indeling in.
* Geef in de vervolgkeuzelijst de blokcodes op die als alineaopmaak kunnen worden geselecteerd.

Voor latere (re-)configuraties, zeg om meer formaten toe te voegen, volg slechts het relevante deel van de instructies.

### De keuzelijst Indeling {#formatselectorlist} inschakelen

Schakel eerst de paraformat-plug-in in:

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/paraformat`. Maak de knooppunten als deze niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak de eigenschap `features` op het knooppunt `paraformat`:

   * **Naam** `features`
   * **Type** `String`
   * **Waarde** `*`  (sterretje)

>[!NOTE]
Als de plug-in niet verder is geconfigureerd, zijn de volgende standaardindelingen ingeschakeld:
* Alinea ( `<p>`)
* Kop 1 ( `<h1>`)
* Kop 2 ( `<h2>`)
* Kop 3 ( `<h3>`)



>[!CAUTION]
Wanneer het vormen van de paragraafformaten van RTE, verwijder niet de paragraafmarkering &lt;p> als het formatteren optie. Als de tag `<p>` wordt verwijderd, kan de auteur van de inhoud de optie **Alineaindelingen** niet selecteren, zelfs niet als er extra indelingen zijn geconfigureerd.

### Geef de beschikbare alineaopmaak op {#paraformatsindropdown}

Alinea-indelingen kunnen voor selectie beschikbaar worden gesteld door:

1. In de componentendefinitie, navigeer aan de knoop `<rtePlugins-node>/paraformat`, zoals gecreeerd in [Het toelaten van de formaatdrop-down selecteur](#styleselectorlist).
1. Onder de `paraformat` knoop creeer een nieuw knooppunt, om de lijst van formaten te houden:

   * **Naam** `formats`
   * **Type** `cq:WidgetCollection`

1. Creeer een nieuw knooppunt onder de `formats` knoop, dit houdt details voor een individueel formaat:

   * **U kunt de naam** opgeven, maar deze moet wel geschikt zijn voor de indeling (bijvoorbeeld mijnalinea, mijnkop1).
   * **Type** `nt:unstructured`

1. Aan dit knooppunt voegt u de eigenschap toe om de gebruikte bloktag te definiëren:

   * **Naam** `tag`
   * **Type** `String`
   * **** ValueThe block tag for the format; bijvoorbeeld: p, h1, h2, enz.

      U hoeft de punthaakjes voor scheidingstekens niet in te voeren.

1. Aan de zelfde knoop voeg een ander bezit toe, voor beschrijvende tekst om in de drop-down lijst te verschijnen:

   * **Naam** `description`
   * **Type** `String`
   * **** ValueThe descriptive text for this format; bijvoorbeeld Alinea, Kop 1, Kop 2 enzovoort. Deze tekst wordt weergegeven in de selectielijst Indeling.

1. Sla de wijzigingen op.

   Herhaal de stappen voor elke vereiste indeling.

>[!CAUTION]
Als u aangepaste indelingen definieert, worden de standaardindelingen (`<p>`, `<h1>`, `<h2>` en `<h3>`) verwijderd. Maak de `<p>`-indeling opnieuw omdat dit de standaardindeling is.

## Speciale tekens {#spchar} configureren

Wanneer in een standaard AEM-installatie de `misctools`-plug-in is ingeschakeld voor speciale tekens (`specialchars`), is er direct een standaardselectie beschikbaar voor gebruik. bijvoorbeeld de symbolen copyright en trademark.

U kunt RTE vormen om uw eigen selectie van karakters beschikbaar te maken; of door verschillende karakters, of een volledige opeenvolging te bepalen.

>[!CAUTION]
Als u uw eigen speciale tekens toevoegt, wordt de standaardselectie genegeerd. Definieer deze tekens desgewenst (opnieuw) in uw eigen selectie.

### Eén teken definiëren {#definesinglechar}

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/misctools`. Maak de knooppunten als deze niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak de eigenschap `features` op het knooppunt `misctools`:

   * **Naam** `features`
   * **Type** `String[]`
   * **Waarde** `specialchars`

          (of `String / *` als u alle functies voor deze plug-in toepast)

1. Onder `misctools` creeer een knoop om de speciale karakterconfiguraties te houden:

   * **Naam** `specialCharsConfig`
   * **Type** `nt:unstructured`

1. Maak onder `specialCharsConfig` een ander knooppunt voor de lijst met tekens:

   * **Naam** `chars`
   * **Type** `nt:unstructured`

1. Voeg onder `chars` een nieuw knooppunt toe voor een afzonderlijke tekendefinitie:

   * **** U kunt de naam opgeven, maar deze moet het teken weerspiegelen; bijvoorbeeld de helft.
   * **Type** `nt:unstructured`

1. Aan deze knoop voeg het volgende bezit toe:

   * **Naam** `entity`
   * **Type** `String`
   * **De** waarde van de HTML-weergave van het vereiste teken; bijvoorbeeld  `&189;` voor de fractie de helft.

1. Sla de wijzigingen op.

In CRXDE, zodra het bezit wordt bewaard, wordt het vertegenwoordigde karakter getoond. Zie onder het voorbeeld van de helft. Herhaal bovenstaande stappen om meer speciale tekens beschikbaar te maken voor auteurs.

![In CRXDE, voeg één enkel karakter toe dat op RTE ](assets/chlimage_1-106.png "toolbarIn CRXDE ter beschikking moet worden gesteld, voeg één enkel karakter toe dat op de toolbar van RTE ter beschikking moet worden gesteld")

### Een tekenbereik definiëren {#definerangechar}

1. Gebruik stap 1 tot en met 3 van [Eén teken definiëren](#definesinglechar).
1. Voeg onder `chars` een nieuw knooppunt toe voor de definitie van het tekenbereik:

   * **** U kunt de naam opgeven, maar deze moet wel het tekenbereik weerspiegelen. bijvoorbeeld potloden .
   * **Type** `nt:unstructured`

1. Voeg onder dit knooppunt (benoemd op basis van uw speciale tekenbereik) de volgende twee eigenschappen toe:

   * **Naam** `rangeStart`

      **Type** `Long`
      **De** waarde van de  [](https://unicode.org/) Unicode-representatie (decimaal) van het eerste teken in het bereik

   * **Naam** `rangeEnd`

      **Type** `Long`
      **De** waarde van de  [](https://unicode.org/) Unicode-representatie (decimaal) van het laatste teken in het bereik

1. Sla de wijzigingen op.

   Als u bijvoorbeeld een bereik definieert tussen 998 en 10000, kunt u de volgende tekens gebruiken.

   ![Definieer in CRXDE een tekenbereik dat beschikbaar moet worden gemaakt in RTE](assets/chlimage_1-107.png)

   *Afbeelding: Definieer in CRXDE een tekenbereik dat beschikbaar moet worden gemaakt in RTE*

   ![Speciale tekens die beschikbaar zijn in RTE worden weergegeven aan auteurs in een pop-](assets/rtepencil.png "upvensterSpeciale tekens die beschikbaar zijn in RTE worden weergegeven aan auteurs in een pop-upvenster")

## Tabelstijlen configureren {#tablestyles}

Stijlen worden doorgaans toegepast op tekst, maar een aparte set stijlen kan ook worden toegepast op een tabel of op een paar tabelcellen. Dergelijke stijlen zijn beschikbaar voor auteurs in het selectievak Stijl in het dialoogvenster Eigenschappen van cel of Tabeleigenschappen. De stijlen zijn beschikbaar wanneer het uitgeven van een lijst binnen een component van de Tekst (of een derivaat) en niet in de standaardcomponent van de Lijst.

>[!NOTE]
U kunt stijlen alleen definiëren voor tabellen en cellen voor klassieke gebruikersinterface.

>[!NOTE]
Het kopiëren en het kleven van lijsten in of van de component van RTE is browser-afhankelijk. De functie wordt niet in het vak ondersteund voor alle browsers. Afhankelijk van de tabelstructuur en de browser krijgt u mogelijk verschillende resultaten. Wanneer u bijvoorbeeld een tabel kopieert en plakt in een RTE-component in Mozilla Firefox in Classic UI en Touch UI, blijft de indeling van de tabel niet behouden.

1. Navigeer binnen uw component naar het knooppunt `<rtePlugins-node>/table`. Maak de knooppunten als deze niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak de eigenschap `features` op het knooppunt `table`:

   * **Naam** `features`
   * **Type** `String`
   * **Waarde** `*`

   >[!NOTE]
   Als u niet alle lijsteigenschappen wilt toelaten kunt u `features` bezit tot stand brengen als:
   * **Type** `String[]`

   * **Waarde** één of beide van het volgende, naargelang van de behoefte:
      * `table` het bewerken van tabeleigenschappen toestaan; inclusief de stijlen.
      * `cellprops` om het bewerken van celeigenschappen mogelijk te maken, inclusief de stijlen.


1. Definieer de locatie van CSS-stijlpagina&#39;s om deze te verwijzen. Zie [De locatie van het stijlblad opgeven](#locationofstylesheet) omdat dit hetzelfde is als wanneer [stijlen voor tekst worden gedefinieerd](#textstyles). De locatie kan worden gedefinieerd als u andere stijlen hebt gedefinieerd.
1. Onder de `table` knoop creeer de volgende nieuwe knopen (zoals vereist):

   * Stijlen definiëren voor de gehele tabel (beschikbaar onder **Tabeleigenschappen**):

      * **Naam** `tableStyles`
      * **Type** `cq:WidgetCollection`
   * Stijlen definiëren voor de afzonderlijke cellen (beschikbaar onder **Celeigenschappen**):

      * **Naam** `cellStyles`
      * **Type** `cq:WidgetCollection`


1. Maak een nieuw knooppunt (onder het knooppunt `tableStyles` of `cellStyles`, al naar gelang van toepassing) om een afzonderlijke stijl weer te geven:

   * **U** kunt de naam opgeven, maar deze moet de stijl weerspiegelen.
   * **Type** `nt:unstructured`

1. Maak op dit knooppunt de eigenschappen:

   * De CSS-stijl definiëren waarnaar moet worden verwezen

      * **Naam** `cssName`
      * **Type** `String`
      * **De** waarde van de naam van de CSS-klasse (zonder een voorafgaande  `.`, bijvoorbeeld,  `cssClass` in plaats van  `.cssClass`)
   * Een beschrijvende tekst definiëren die moet worden weergegeven in de vervolgkeuzelijst

      * **Naam** `text`
      * **Type** `String`
      * **De** waarde van de tekst die in de selectielijst moet worden weergegeven


1. Sla alle wijzigingen op.

Herhaal bovenstaande stappen voor elke vereiste stijl.

### Verborgen koppen in tabellen configureren voor toegankelijkheid {#hiddenheader}

Soms kunt u gegevenslijsten zonder visuele tekst in een kolomkopbal tot stand brengen veronderstellend dat het doel van de kopbal door de visuele verhouding van de kolom met andere kolommen wordt geïmpliceerd. In dit geval moet verborgen binnentekst in de cel in de kopcel worden weergegeven, zodat schermlezers en andere ondersteunende hulpmiddelen het doel van de kolom kunnen begrijpen.

Om toegankelijkheid in dergelijke scenario&#39;s te verbeteren, steunt RTE verborgen kopbalcellen. Bovendien worden er configuratie-instellingen gegeven voor verborgen koppen in tabellen. Met deze instellingen kunt u CSS-stijlen toepassen op verborgen koppen in de bewerkings- en voorvertoningsmodus. Om auteurs te helpen verborgen kopballen in Edit wijze identificeren, omvat de volgende parameters in uw code:

* `hiddenHeaderEditingCSS`: Hiermee geeft u de naam op van de CSS-klasse die wordt toegepast op de cel met verborgen koptekst wanneer RTE wordt bewerkt.
* `hiddenHeaderEditingStyle`: Hiermee geeft u een stijltekenreeks op die wordt toegepast op de cel met verborgen koptekst wanneer RTE wordt bewerkt.

Als u zowel de CSS-tekenreeks als de stijltekenreeks in code opgeeft, heeft de CSS-klasse voorrang op de stijltekenreeks en kan deze alle configuratiewijzigingen overschrijven die de stijltekenreeks aanbrengt.

Om auteurs te helpen CSS op verborgen kopballen op de voorproefwijze toepassen, kunt u de volgende parameters in uw code omvatten:

* `hiddenHeaderClassName`: Hiermee geeft u de naam op van de CSS-klasse die wordt toegepast op de verborgen kopcel in de voorvertoningsmodus.
* `hiddenHeaderStyle`: Hiermee geeft u een stijltekenreeks op die wordt toegepast op de cel met de verborgen koptekst in de voorvertoningsmodus.

Als u zowel de CSS-tekenreeks als de stijltekenreeks in code opgeeft, heeft de CSS-klasse voorrang op de stijltekenreeks en kan deze alle configuratiewijzigingen overschrijven die de stijltekenreeks aanbrengt.

## Woordenboeken toevoegen voor de spellingcontrole {#adddict}

Wanneer de insteekmodule voor spellingcontrole is geactiveerd, gebruikt de RTE woordenboeken voor elke geschikte taal. Deze worden vervolgens geselecteerd volgens de taal van de website door ofwel de taaleigenschap van de substructuur te nemen of de taal uit de URL te halen; bijvoorbeeld. de `/en/` tak wordt gecontroleerd als Engels, de `/de/` tak als Duits.

>[!NOTE]
Het bericht `Spell checking failed` wordt gezien als een controle voor een taal wordt geprobeerd die niet geïnstalleerd is. De standaardwoordenboeken bevinden zich op `/libs/cq/spellchecker/dictionaries`, samen met de juiste leesmij-bestanden. Wijzig de bestanden niet.

Een standaard AEM installatie omvat de woordenboeken voor Amerikaans Engels (`en_us`) en Brits Engels (`en_gb`). Voer de volgende stappen uit om meer woordenboeken toe te voegen.

1. Navigeer naar de pagina [https://extensions.openoffice.org/](https://extensions.openoffice.org/).

1. Ga op een van de volgende manieren te werk om een woordenboek te zoeken waarin u uw taal kunt kiezen:

   * Zoek naar woordenboek van uw taalkeuze. Zoek op de woordenboekpagina de koppeling naar de oorspronkelijke bron of de oorspronkelijke webpagina van de auteur. Zoek de woordenboekbestanden voor v2.x op een dergelijke pagina.
   * Zoek naar v2.x woordenboekbestanden op [https://wiki.openoffice.org/wiki/User:Khirano/Dictionaries](https://wiki.openoffice.org/wiki/User:Khirano/Dictionaries).

1. Download het archief met de spellingdefinities. Extraheer de inhoud van het archief op uw bestandssysteem.

   >[!CAUTION]
   Alleen woordenboeken in de `MySpell`-indeling voor OpenOffice.org v2.0.1 of eerder worden ondersteund. Aangezien de woordenboeken nu archiefbestanden zijn, wordt u aangeraden het archief na het downloaden te verifiëren.

1. Zoek de .aff- en .dic-bestanden. Bestandsnaam in kleine letters behouden. Bijvoorbeeld `de_de.aff` en `de_de.dic`.
1. Laad de .aff- en .dic-bestanden in de opslagplaats op `/apps/cq/spellchecker/dictionaries`.

>[!NOTE]
De spellingcontrole van RTE is beschikbaar op bestelling. Deze wordt niet automatisch uitgevoerd wanneer u tekst gaat typen. Als u de spellingcontrole wilt uitvoeren, klikt u op [!UICONTROL Spellchecker] op de werkbalk. RTE controleert de spelling van woorden en benadrukt de verkeerd gespelde woorden.
Als u een wijziging opneemt die door de spellingcontrole wordt voorgesteld, wordt de status van de tekst gewijzigd en worden onjuist gespelde woorden niet langer gemarkeerd. Als u de spellingcontrole wilt uitvoeren, tikt u nogmaals op de knop Spellingcontrole of klikt u nogmaals op de knop Spellingcontrole.

## De historiegrootte configureren voor het ongedaan maken en opnieuw uitvoeren van handelingen {#undohistory}

Met RTE kunnen auteurs enkele laatste bewerkingen ongedaan maken of opnieuw uitvoeren. Standaard worden 50 bewerkingen opgeslagen in de geschiedenis. U kunt deze waarde naar wens configureren.

1. Navigeer binnen uw component naar het knooppunt `<rtePlugins-node>/undo`. Maak deze knooppunten als deze niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak de eigenschap op het knooppunt `undo`:

   * **Naam** `maxUndoSteps`
   * **Type** `Long`
   * **De** waarde van het aantal stappen ongedaan maken die u in de geschiedenis wilt opslaan. De standaardwaarde is 50. Gebruik `0` om ongedaan te maken/opnieuw.

1. Sla de wijzigingen op.

## De tabgrootte {#tabsize} configureren

Wanneer het tabteken wordt ingedrukt binnen tekst, wordt een vooraf gedefinieerd aantal spaties ingevoegd. Dit zijn standaard drie vaste spaties en één spatie.

De tabgrootte definiëren:

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/keys`. Maak de knooppunten als deze niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak de eigenschap op het knooppunt `keys`:

   * **Naam** `tabSize`
   * **Type** `String`
   * **De** waarde van het aantal spatietekens dat voor de tabulator moet worden gebruikt.

1. Sla de wijzigingen op.

## Inspringingsmarge {#indentmargin} instellen

Wanneer inspringing is ingeschakeld (standaard), kunt u de grootte van de inspringing definiëren:

>[!NOTE]
Deze inspringingsgrootte wordt alleen toegepast op alinea&#39;s (blokken tekst). het heeft geen invloed op de inspringing van feitelijke lijsten.

1. Navigeer binnen uw component naar het knooppunt `<rtePlugins-node>/lists`. Maak deze knooppunten als deze niet bestaan. Zie [Een plug-in activeren](#activateplugin) voor meer informatie.
1. Maak op het knooppunt `lists` de parameter `identSize`:

   * **Naam**:  `identSize`
   * **Type**:  `Long`
   * **Waarde**: aantal pixels dat is vereist voor de inspringingsmarge.

## De hoogte van bewerkbare ruimte {#editablespace} configureren

>[!NOTE]
Dit is alleen van toepassing wanneer u de RTE gebruikt in een dialoogvenster (niet tijdens het bewerken op locatie in een klassieke UI).

U kunt de hoogte van de bewerkbare ruimte definiëren die in het dialoogvenster van de component wordt weergegeven:

1. Maak een nieuwe eigenschap op het knooppunt `../items/text` in de dialoogdefinitie voor de component:

   * **Naam** `height`
   * **Type** `Long`
   * **De** waarde van de hoogte van het bewerkingscanvas in pixels.

   >[!NOTE]
   Hiermee wijzigt u de hoogte van het dialoogvenster niet.

1. Sla de wijzigingen op.

## Stijlen en protocollen voor koppelingen configureren {#linkstyles}

Bij het toevoegen van koppelingen in AEM kunt u het volgende definiëren:

* De CSS-stijlen die moeten worden gebruikt
* De automatisch aanvaarde protocollen

Om te vormen hoe de verbindingen in AEM van een ander programma worden toegevoegd, bepaal de regels van HTML.

1. Zoek met CRXDE Lite de tekstcomponent voor uw project.
1. Maak een nieuw knooppunt op hetzelfde niveau als `<rtePlugins-node>`, dat wil zeggen: maak het knooppunt onder het bovenliggende knooppunt van `<rtePlugins-node>`:

   * **Naam** `htmlRules`
   * **Type** `nt:unstructured`

   >[!NOTE]
   Het knooppunt `../items/text` heeft de eigenschap:
   * **Naam** `xtype`
   * **Type** `String`
   * **Waarde** `richtext`

   De locatie van het knooppunt `../items/text` kan variëren, afhankelijk van de structuur van het dialoogvenster; twee voorbeelden zijn :
   * `/apps/myProject>/components/text/dialog/items/text`
   * `/apps/<myProject>/components/text/dialog/items/panel/items/text`


1. Maak onder `htmlRules` een nieuw knooppunt.

   * **Naam** `links`
   * **Type** `nt:unstructured`

1. Definieer onder het knooppunt `links` de eigenschappen naar wens:

   * CSS-stijl voor interne koppelingen:

      * **Naam** `cssInternal`
      * **Type** `String`
      * **De** waarde van de naam van de CSS-klasse (zonder een voorafgaande &#39;.&#39;; bijvoorbeeld `cssClass` in plaats van `.cssClass`)
   * CSS-stijl voor externe koppelingen

      * **Naam** `cssExternal`
      * **Type** `String`
      * **De** waarde van de naam van de CSS-klasse (zonder een voorafgaande &#39;.&#39;; bijvoorbeeld `cssClass` in plaats van `.cssClass`)
   * Array van geldige **protocollen**. De ondersteunde protocollen zijn `http://`, `https://`, `file://` en `mailto:`.

      * **Naam** `protocols`
      * **Type** `String[]`
      * **Waarde**(s) een of meer protocollen
   * **defaultProtocol**  (eigenschap van het type  **String**): Protocol dat moet worden gebruikt als de gebruiker niet uitdrukkelijk één specificeerde.

      * **Naam** `defaultProtocol`
      * **Type** `String`
      * **Waarde**(s) een of meer standaardprotocollen
   * Definitie van hoe te om het doelattribuut van een verbinding te behandelen. Een nieuw knooppunt maken:

      * **Naam** `targetConfig`
      * **Type** `nt:unstructured`

      Op het knooppunt `targetConfig`: de vereiste eigenschappen definiëren:

      * Geef de doelmodus op:

         * **Naam** `mode`
         * **Type** `String`)
         * **Waarde**(s) :

            * `auto`: betekent dat een automatisch doel wordt gekozen

               (opgegeven door de eigenschap `targetExternal` voor externe koppelingen of `targetInternal` voor interne koppelingen).

            * `manual`: niet van toepassing in dit verband
            * `blank`: niet van toepassing in dit verband
      * Het doel voor interne koppelingen:

         * **Naam** `targetInternal`
         * **Type** `String`
         * **Waarde** van het doel voor interne koppelingen (alleen gebruiken als de modus is  `auto`)
      * Het doel voor externe koppelingen:

         * **Naam** `targetExternal`
         * **Type** `String`
         * **De** waarde van het doel voor externe koppelingen (wordt alleen gebruikt wanneer de modus is  `auto`).








1. Sla alle wijzigingen op.
