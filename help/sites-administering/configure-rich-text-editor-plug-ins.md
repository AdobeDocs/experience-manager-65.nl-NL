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


# De invoegtoepassingen van de Rich Text Editor configureren {#configure-the-rich-text-editor-plug-ins}

De functionaliteit van RTE wordt beschikbaar gemaakt via een reeks stop-ins, elk met eigenschappen bezit. U kunt het eigenschapbezit vormen om, één of meerdere eigenschappen van RTE toe te laten of onbruikbaar te maken. Dit artikel beschrijft hoe te om de stop-ins specifiek te vormen RTE.

Voor details over de andere configuraties RTE, zie [Rich Text Editor](/help/sites-administering/rich-text-editor.md)vormen.

>[!NOTE]
>
>Als u met CRXDE Lite werkt, wordt u aangeraden de wijzigingen regelmatig op te slaan met behulp van [!UICONTROL Save All] deze optie.

## Een insteekmodule activeren en de eigenschap features configureren {#activateplugin}

Voer de volgende stappen uit om een plug-in te activeren. Sommige stappen zijn alleen nodig wanneer u een insteekmodule voor het eerst configureert, omdat de bijbehorende knooppunten niet bestaan.

Standaard zijn `format`, `link`, `list`, `justify`, en de `control` stoppen en al hun eigenschappen toegelaten in RTE.

>[!NOTE]
>
>Het respectieve `rtePlugins` knooppunt wordt genoemd `<rtePlugins-node>` om dubbel werk in dit artikel te voorkomen.

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
   * **Geef** de plug-in-id van de vereiste plug-in een naam.

Nadat u een insteekmodule hebt geactiveerd, volgt u deze richtlijnen om de `features` eigenschap te configureren.

|  | Alle functies inschakelen | Enkele specifieke functies inschakelen | Alle functies uitschakelen |
|---|---|---|---|
| Naam | functies | functies | functies |
| Type | Tekenreeks | String[] (multi-string; Stel Type in op String en klik op Meerdere in CRXDE Lite) | Tekenreeks |
| Waarde | `*` (een sterretje) | ingesteld op een of meer functiewaarden | - |

## Begrijp de findreplace plug-in {#findreplace}

Voor de `findreplace` insteekmodule is geen configuratie nodig. Het werkt uit de doos.

Wanneer u de vervangingsfunctie gebruikt, moet de te vervangen tekenreeks op hetzelfde moment worden ingevoerd als de zoektekenreeks. U kunt echter nog steeds op Zoeken klikken om de tekenreeks te zoeken voordat u deze vervangt. Als de vervangingstekenreeks wordt ingevoerd nadat op Zoeken is geklikt, wordt de zoekopdracht opnieuw ingesteld op het begin van de tekst.

Het dialoogvenster Zoeken en vervangen wordt transparant wanneer op Zoeken wordt geklikt en wordt dekkend wanneer op Vervangen wordt geklikt. Hierdoor kan de auteur de tekst controleren die de auteur vervangt. Als gebruikers op Alles vervangen klikken, wordt het dialoogvenster gesloten en wordt het aantal aangebrachte vervangingen weergegeven.

## De plakmodi configureren {#pastemodes}

Wanneer het gebruiken van RTE, kunnen de auteurs inhoud in één van de volgende drie wijzen kleven:

* **Browsermodus**: Plak tekst met gebruik van de standaardimplementatie van de browser. Het is geen aanbevolen methode omdat hierdoor ongewenste opmaakcodes kunnen ontstaan.

* **Modus** Onbewerkte tekst: Plak de inhoud van het klembord als onbewerkte tekst. Alle elementen van stijl en opmaak worden uit de gekopieerde inhoud verwijderd voordat deze in AEM component worden ingevoegd.

* **MS Word-modus**: Plak de tekst, inclusief tabellen, met opmaak wanneer u kopieert vanuit MS Word. Het kopiëren en plakken van tekst uit een andere bron, zoals een webpagina of MS Excel, wordt niet ondersteund en behoudt alleen de gedeeltelijke opmaak.

### De beschikbare plakopties op de werkbalk RTE configureren  {#configure-paste-options-available-on-the-rte-toolbar}

U kunt sommige, alle, of geen van deze drie pictogrammen aan uw auteurs in de toolbar van RTE verstrekken:

* **[!UICONTROL Paste (Ctrl+V)]**: Kan vooraf worden geconfigureerd voor een van de drie bovenstaande plakmodi.

* **[!UICONTROL Paste as Text]**: Geeft functionaliteit voor de modus Onbewerkte tekst.

* **[!UICONTROL Paste from Word]**: Biedt functionaliteit in de modus MS Word.

Om RTE te vormen om de vereiste pictogrammen te tonen, volg deze stappen.

1. Navigeer naar de component, bijvoorbeeld `/apps/<myProject>/components/text`.
1. Navigeer naar het knooppunt `rtePlugins/edit`. Zie een plug-in [activeren](#activateplugin) als het knooppunt niet bestaat.
1. Maak de `features` eigenschap op het `edit` knooppunt en voeg een of meer functies toe. Sla alle wijzigingen op.

### Het gedrag van het pictogram en de sneltoets Plakken (Ctrl+V) configureren {#configure-the-behavior-of-the-paste-ctrl-v-icon-and-shortcut}

U kunt het gedrag van het **[!UICONTROL Paste (Ctrl+V)]** pictogram vooraf configureren door de volgende stappen uit te voeren. Deze configuratie definieert ook het gedrag van sneltoetsen Ctrl+V die auteurs gebruiken om inhoud te plakken.

De configuratie staat voor de volgende drie soorten gebruiksgevallen toe:

* Plak tekst met gebruik van de standaardimplementatie van de browser. Het is geen aanbevolen methode omdat hierdoor ongewenste opmaakcodes kunnen ontstaan. Gevormd met `browser` hieronder.

* Plak de inhoud van het klembord als onbewerkte tekst. Alle elementen van stijl en opmaak worden uit de gekopieerde inhoud verwijderd voordat deze in AEM component worden ingevoegd. Gevormd met `plaintext` hieronder.

* Plak de tekst, inclusief tabellen, met opmaak wanneer u kopieert vanuit MS Word. Het kopiëren en plakken van tekst uit een andere bron, zoals een webpagina of MS Excel, wordt niet ondersteund en behoudt alleen de gedeeltelijke opmaak. Gevormd met `wordhtml` hieronder.

1. Navigeer in uw component naar het `<rtePlugins-node>/edit` knooppunt. Maak de knooppunten als deze niet bestaan. Zie Een plug-in [activeren voor meer informatie](#activateplugin).
1. In de `edit` knoop creeer een bezit gebruikend de volgende details:

   * **Naam** `defaultPasteMode`
   * **Type** `String`
   * **Waarde** Een van de vereiste plakmodus `browser`, `plaintext`of `wordhtml`.

### Indelingen configureren die zijn toegestaan bij het plakken van inhoud {#pasteformats}

De plakken-als-Microsoft-Word (`paste-wordhtml`) wijze kan verder worden gevormd zodat u kunt uitdrukkelijk bepalen welke stijlen worden toegestaan wanneer het kleven in AEM van een ander programma, zoals Microsoft Word.

Als u bijvoorbeeld alleen vette indelingen en lijsten wilt toestaan bij het plakken in AEM, kunt u de andere indelingen filteren. Dit wordt configureerbare het kleven het filtreren genoemd, die voor allebei kan worden gedaan:

* [Tekst](#pastemodes)
* [Koppelingen](#linkstyles)

Voor koppelingen kunt u ook de protocollen definiëren die automatisch worden geaccepteerd.

Om te vormen welke formaten worden toegestaan wanneer het kleven van tekst in AEM van een ander programma:

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/edit`. Maak de knooppunten als deze niet bestaan. Zie Een plug-in [activeren voor meer informatie](#activateplugin).
1. Maak een knooppunt onder het `edit` knooppunt voor de HTML-plakregels:

   * **Naam** `htmlPasteRules`
   * **Type** `nt:unstructured`

1. Maak een knooppunt onder `htmlPasteRules`, voor meer informatie over de toegestane basisindelingen:

   * **Naam** `allowBasics`
   * **Type** `nt:unstructured`

1. Als u de afzonderlijke geaccepteerde indelingen wilt beheren, maakt u een of meer van de volgende eigenschappen op het `allowBasics` knooppunt:

   * **Naam** `bold`
   * **Naam** `italic`
   * **Naam** `underline`
   * **Naam** `anchor` (voor zowel koppelingen als benoemde ankers)
   * **Naam** `image`

   Alle eigenschappen zijn van het **Type** `Boolean`, zodat kunt u in de aangewezen **Waarde** of het vinkje selecteren of verwijderen om de functionaliteit toe te laten of onbruikbaar te maken.

   >[!NOTE]
   >
   >Indien niet expliciet gedefinieerd, wordt de standaardwaarde true gebruikt en wordt de opmaak geaccepteerd.

1. Andere indelingen kunnen ook worden gedefinieerd met een reeks andere eigenschappen of knooppunten, die ook op het `htmlPasteRules` knooppunt worden toegepast:

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
   <td><p>Hiermee definieert u het gedrag bij het plakken van tabellen.<br /> </p> <p>Dit knooppunt moet de eigenschap <code>allow</code> (type <code>Boolean</code>) hebben om te bepalen of het plakken van tabellen is toegestaan.</p> <p>Als <code>allow</code> deze is ingesteld op <code>false</code>, moet u de eigenschap <code>ignoreMode</code> (type<code> String</code>) opgeven om te bepalen hoe geplakte tabelinhoud wordt verwerkt. Geldige waarden voor <code>ignoreMode</code> zijn:</p>
    <ul>
     <li><code>remove</code>: Hiermee verwijdert u tabelinhoud.</li>
     <li><code>paragraph</code>: Hiermee zet u tabelcellen om in alinea's.</li>
    </ul> </td>
  </tr>
  <tr>
   <td>list</td>
   <td>nt:ongestructureerd</td>
   <td><p>Hiermee definieert u het gedrag bij het plakken van lijsten.<br /> </p> <p>U moet de eigenschap <code>allow</code> (type <code>Boolean</code>) hebben om te definiëren of het plakken van lijsten is toegestaan.</p> <p>Wanneer <code>allow</code> deze eigenschap is ingesteld op <code>false</code>, moet u de eigenschap <code>ignoreMode</code> (type <code>String</code>) opgeven om te bepalen hoe inhoud uit de lijst moet worden verwerkt. Geldige waarden voor <code>ignoreMode</code> zijn:</p>
    <ul>
     <li><code>remove</code>: Hiermee verwijdert u de inhoud van de lijst.</li>
     <li><code>paragraph</code>: Hiermee zet u lijstitems om in alinea's.</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Voorbeeld van een geldige `htmlPasteRules` structuur:

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

Auteurs kunnen stijlen toepassen om de weergave van een deel van de tekst te wijzigen. De stijlen zijn gebaseerd op CSS-klassen die u vooraf definieert in uw CSS-stijlpagina. Stileerde inhoud wordt ingesloten in `span` tags die het `class` kenmerk gebruiken om naar de CSS-klasse te verwijzen. Bijvoorbeeld:

`<span class=monospaced>Monospaced Text Here</span>`

Wanneer de plug-in Stijlen voor de eerste keer is ingeschakeld, zijn er geen standaardstijlen beschikbaar. De pop-uplijst is leeg. Ga als volgt te werk om de auteurs stijlen te voorzien:

* Schakel de vervolgkeuzelijst Stijl in.
* Geef de locatie(s) van de stijlpagina(&#39;s) op.
* Geef de afzonderlijke stijlen op die u kunt selecteren in de vervolgkeuzelijst Stijl.

Voor latere (re-)configuraties, zeg om meer stijlen toe te voegen, volg slechts de instructies om naar een nieuw stijlblad te verwijzen en de extra stijlen te specificeren.

>[!NOTE]
>
>Stijlen kunnen ook worden gedefinieerd voor [tabellen of tabelcellen](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tablestyles). Deze configuraties vereisen afzonderlijke procedures.

### De vervolgkeuzelijst Stijl inschakelen {#styleselectorlist}

Hiervoor schakelt u de insteekmodule Stijlen in.

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/styles`. Maak de knooppunten als deze niet bestaan. Zie Een plug-in [activeren voor meer informatie](#activateplugin).
1. Maak de `features` eigenschap op het `styles` knooppunt:

   * **Naam** `features`
   * **Type** `String`
   * **Waarde** `*` (sterretje)

1. Sla alle wijzigingen op.

>[!NOTE]
>
>Zodra de plug-in Stijlen is ingeschakeld, wordt de vervolgkeuzelijst Stijl weergegeven in het dialoogvenster Bewerken. De lijst is echter leeg omdat er geen stijlen zijn geconfigureerd.

### De locatie van de stijlpagina opgeven {#locationofstylesheet}

Geef vervolgens de locatie(s) op van de stijlpagina(&#39;s) waarnaar u wilt verwijzen:

1. Navigeer bijvoorbeeld naar het hoofdknooppunt van de tekstcomponent `/apps/<myProject>/components/text`.
1. Voeg de eigenschap toe `externalStyleSheets` aan het bovenliggende knooppunt van `<rtePlugins-node>`:

   * **Naam** `externalStyleSheets`
   * **Type** `String[]` (meerdere tekenreeksen; klik op **Multi** in (CRXDE)
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

1. In de componentendefinitie, navigeer aan de knoop `<rtePlugins-node>/styles`, zoals gecreeerd in het [Toelaten van de stijldrop-down selecteur](#styleselectorlist).
1. Onder het knooppunt `styles`, maakt u een nieuw knooppunt (ook wel `styles`genoemd) dat de lijst bevat die beschikbaar wordt gesteld:

   * **Naam** `styles`
   * **Type** `cq:WidgetCollection`

1. Maak een nieuw knooppunt onder het `styles` knooppunt voor een afzonderlijke stijl:

   * **Naam**, u kunt de naam specificeren, maar het zou voor de stijl geschikt moeten zijn
   * **Type** `nt:unstructured`

1. Voeg de eigenschap toe `cssName` aan dit knooppunt om naar de CSS-klasse te verwijzen:

   * **Naam** `cssName`
   * **Type** `String`
   * **Waarde** De naam van de CSS-klasse (zonder een voorafgaande &#39;.&#39;; for example, `cssClass` instead of `.cssClass`)

1. Voeg de eigenschap toe `text` aan hetzelfde knooppunt. Hiermee wordt de tekst gedefinieerd die wordt weergegeven in het selectievak:

   * **Naam** `text`
   * **Type** `String`
   * **Beschrijving van de waarde** van de stijl; wordt weergegeven in het keuzemenu Stijl.

1. Sla de wijzigingen op.

   Herhaal bovenstaande stappen voor elke vereiste stijl.

### RTE configureren voor optimale woordeinden in het Japans {#jpwordwrap}

Auteurs die AEM gebruiken om inhoud in de Japanse taal te schrijven, kunnen een stijl toepassen op tekens om regeleinde te voorkomen wanneer een regeleinde niet vereist is. Op deze manier kunnen auteurs de zinnen op de gewenste positie laten afbreken. De stijl voor deze functionaliteit is gebaseerd op CSS-klasse die vooraf is gedefinieerd in de CSS-stijlpagina.

>[!NOTE]
>
>Deze eigenschap vereist minstens AEM 6.5 Service Pack 1.

Ga als volgt te werk om de stijl te maken die auteurs op Japanse tekst kunnen toepassen:

1. Maak een nieuw knooppunt onder het knooppunt Stijlen. Zie [een nieuwe stijl](#stylesindropdown)opgeven.
   * Naam: `jpn-word-wrap`
   * Type: Verzenden:unstructure

1. Voeg de eigenschap toe `cssName` aan het knooppunt om naar de CSS-klasse te verwijzen. Deze klassenaam is een gereserveerde naam voor de functie voor tekstomloop in Japans.
   * Naam: `cssName`
   * Type: `String`
   * Waarde: `jpn-word-wrap` (zonder voorafgaande `.`)

1. Voeg de bezitstekst aan de zelfde knoop toe. De waarde is de naam van de stijl die de auteurs zien wanneer ze de stijl selecteren.
   * Naam: `text`
*Type: 
`String`
   * Waarde: `Japanese word-wrap`

1. Maak een stijlpagina en geef het pad op. Zie [de locatie van stijlpagina](#locationofstylesheet)opgeven. Voeg de volgende inhoud aan de stijlpagina toe. Wijzig de achtergrondkleur naar wens.

   ```css
   .text span.jpn-word-wrap {
       display:inline-block;
   }
   .is-edited span.jpn-word-wrap {
       background-color: #ffddff;
   }
   ```

   ![Stijlblad om de functie voor tekstomloop in Japans beschikbaar te maken voor auteurs](assets/rte_jpwordwrap_stylesheet.jpg)

## Alinea-indelingen configureren {#paraformats}

Elke tekst die in RTE wordt geschreven, wordt binnen een bloktag geplaatst, waarbij de standaardwaarde `<p>`is. Als u de `paraformat` plug-in inschakelt, geeft u via een vervolgkeuzelijst aanvullende blokcodes op die aan alinea&#39;s kunnen worden toegewezen. Alineaopmaak bepaalt het alineatype door de juiste bloktag toe te wijzen. De auteur kan deze selecteren en toewijzen met de kiezer Indeling. De voorbeeldbloklabels omvatten onder andere de standaardalinea &lt;p> en koppen &lt;h1>, &lt;h2> enzovoort.

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

### De keuzelijst Indeling inschakelen {#formatselectorlist}

Schakel eerst de paraformat-plug-in in:

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/paraformat`. Maak de knooppunten als deze niet bestaan. Zie Een plug-in [activeren voor meer informatie](#activateplugin).
1. Maak de `features` eigenschap op het `paraformat` knooppunt:

   * **Naam** `features`
   * **Type** `String`
   * **Waarde** `*` (sterretje)

>[!NOTE]
Als de plug-in niet verder is geconfigureerd, zijn de volgende standaardindelingen ingeschakeld:
* Alinea ( `<p>`)
* Heading 1 ( `<h1>`)
* Heading 2 ( `<h2>`)
* Heading 3 ( `<h3>`)



>[!CAUTION]
Wanneer het vormen van de paragraafformaten van RTE, verwijder niet de paragraafmarkering &lt;p> als het formatteren optie. Als het `<p>` label wordt verwijderd, kan de auteur van de inhoud de optie **Alinea-indelingen** niet selecteren, zelfs niet als er extra indelingen zijn geconfigureerd.

### Beschikbare alineaopmaak opgeven {#paraformatsindropdown}

Alinea-indelingen kunnen voor selectie beschikbaar worden gesteld door:

1. In de componentendefinitie, navigeer aan de knoop `<rtePlugins-node>/paraformat`, zoals gecreeerd in het [Toelaten van de formaatdrop-down selecteur](#styleselectorlist).
1. Onder het `paraformat` knooppunt maakt u een nieuw knooppunt voor de lijst met indelingen:

   * **Naam** `formats`
   * **Type** `cq:WidgetCollection`

1. Maak een nieuw knooppunt onder het `formats` knooppunt. Dit bevat gegevens voor een afzonderlijke indeling:

   * **U kunt de naam** opgeven, maar deze moet wel geschikt zijn voor de indeling (bijvoorbeeld mijnalinea, mijnkop1).
   * **Type** `nt:unstructured`

1. Aan dit knooppunt voegt u de eigenschap toe om de gebruikte bloktag te definiëren:

   * **Naam** `tag`
   * **Type** `String`
   * **Waarde** de bloktag voor de indeling; bijvoorbeeld: p, h1, h2, enz.

      U hoeft de punthaakjes voor scheidingstekens niet in te voeren.

1. Aan de zelfde knoop voeg een ander bezit toe, voor beschrijvende tekst om in de drop-down lijst te verschijnen:

   * **Naam** `description`
   * **Type** `String`
   * **Waarde** de beschrijvende tekst voor deze opmaak. bijvoorbeeld Alinea, Kop 1, Kop 2 enzovoort. Deze tekst wordt weergegeven in de selectielijst Indeling.

1. Sla de wijzigingen op.

   Herhaal de stappen voor elke vereiste indeling.

>[!CAUTION]
Als u aangepaste indelingen definieert, worden de standaardindelingen (`<p>`, `<h1>`, `<h2>`en `<h3>`) verwijderd. Maak `<p>` opmaak opnieuw omdat dit de standaardindeling is.

## Speciale tekens configureren {#spchar}

Wanneer de `misctools` plug-in in een standaard AEM is ingeschakeld voor speciale tekens (`specialchars`), is er direct een standaardselectie beschikbaar voor gebruik. bijvoorbeeld de symbolen copyright en trademark.

U kunt RTE vormen om uw eigen selectie van karakters beschikbaar te maken; of door verschillende karakters, of een volledige opeenvolging te bepalen.

>[!CAUTION]
Als u uw eigen speciale tekens toevoegt, wordt de standaardselectie genegeerd. Definieer deze tekens desgewenst (opnieuw) in uw eigen selectie.

### Eén teken definiëren {#definesinglechar}

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/misctools`. Maak de knooppunten als deze niet bestaan. Zie Een plug-in [activeren voor meer informatie](#activateplugin).
1. Maak de `features` eigenschap op het `misctools` knooppunt:

   * **Naam** `features`
   * **Type** `String[]`
   * **Waarde** `specialchars`

          (of `String / *` als u alle functies voor deze plug-in toepast)

1. Onder `misctools` creeer een knoop om de speciale karakterconfiguraties te houden:

   * **Naam** `specialCharsConfig`
   * **Type** `nt:unstructured`

1. Onder `specialCharsConfig` creeer een andere knoop om de lijst van karakters te houden:

   * **Naam** `chars`
   * **Type** `nt:unstructured`

1. Onder `chars` voeg een nieuw knooppunt toe voor het opnemen van een afzonderlijke tekendefinitie:

   * **U kunt een naam** opgeven, maar deze moet het teken aangeven. bijvoorbeeld de helft.
   * **Type** `nt:unstructured`

1. Aan deze knoop voeg het volgende bezit toe:

   * **Naam** `entity`
   * **Type** `String`
   * **Waarde** voor de HTML-weergave van het vereiste teken; bijvoorbeeld `&189;` voor de fractie de helft.

1. Sla de wijzigingen op.

In CRXDE, zodra het bezit wordt bewaard, wordt het vertegenwoordigde karakter getoond. Zie onder het voorbeeld van de helft. Herhaal bovenstaande stappen om meer speciale tekens beschikbaar te maken voor auteurs.

![In CRXDE, voeg één enkel karakter toe dat op RTE](assets/chlimage_1-106.png "toolbarIn CRXDE ter beschikking moet worden gesteld, voeg één enkel karakter toe dat op de toolbar van RTE ter beschikking moet worden gesteld")

### Een tekenbereik definiëren {#definerangechar}

1. Gebruik stap 1 tot en met 3 van [Eén teken](#definesinglechar)definiëren.
1. Voeg onder `chars` een nieuw knooppunt toe voor de definitie van het tekenbereik:

   * **U kunt een naam** opgeven, maar deze moet wel het tekenbereik weerspiegelen. bijvoorbeeld potloden .
   * **Type** `nt:unstructured`

1. Voeg onder dit knooppunt (benoemd op basis van uw speciale tekenbereik) de volgende twee eigenschappen toe:

   * **Naam** `rangeStart`

      **Type** `Long`
      **Waarde** de [Unicode](https://unicode.org/) -representatie (decimaal) van het eerste teken in het bereik

   * **Naam** `rangeEnd`

      **Type** `Long`
      **Waarde** de [Unicode](https://unicode.org/) -representatie (decimaal) van het laatste teken in het bereik

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

1. Navigeer binnen uw component naar het knooppunt `<rtePlugins-node>/table`. Maak de knooppunten als deze niet bestaan. Zie Een plug-in [activeren voor meer informatie](#activateplugin).
1. Maak de `features` eigenschap op het `table` knooppunt:

   * **Naam** `features`
   * **Type** `String`
   * **Waarde** `*`

   >[!NOTE]
   Als u niet alle tabelfuncties wilt inschakelen, kunt u de `features` eigenschap als volgt maken:
   * **Type** `String[]`

   * **Waarde**&#x200B;één of beide van het volgende, naargelang van de behoefte:
      * `table` het bewerken van tabeleigenschappen toestaan; inclusief de stijlen.
      * `cellprops` om het bewerken van celeigenschappen mogelijk te maken, inclusief de stijlen.


1. Definieer de locatie van CSS-stijlpagina&#39;s om deze te verwijzen. Zie [De locatie van het stijlblad](#locationofstylesheet) opgeven omdat dit dezelfde is als bij het definiëren van [stijlen voor tekst](#textstyles). De locatie kan worden gedefinieerd als u andere stijlen hebt gedefinieerd.
1. Maak onder het `table` knooppunt de volgende nieuwe knooppunten (naar wens):

   * Stijlen definiëren voor de gehele tabel (beschikbaar onder **Tabeleigenschappen**):

      * **Naam** `tableStyles`
      * **Type** `cq:WidgetCollection`
   * Stijlen definiëren voor de afzonderlijke cellen (beschikbaar onder **Celeigenschappen**):

      * **Naam** `cellStyles`
      * **Type** `cq:WidgetCollection`


1. Maak een nieuw knooppunt (onder het `tableStyles` of het `cellStyles` knooppunt naar gelang van het geval) voor een afzonderlijke stijl:

   * **U kunt een naam** opgeven, maar deze moet de stijl weerspiegelen.
   * **Type** `nt:unstructured`

1. Maak op dit knooppunt de eigenschappen:

   * De CSS-stijl definiëren waarnaar moet worden verwezen

      * **Naam** `cssName`
      * **Type** `String`
      * **Waarde** de naam van de CSS-klasse (zonder een voorafgaande `.`, bijvoorbeeld, `cssClass` in plaats van `.cssClass`)
   * Een beschrijvende tekst definiëren die moet worden weergegeven in de vervolgkeuzelijst

      * **Naam** `text`
      * **Type** `String`
      * **De waarde** van de tekst die in de selectielijst moet worden weergegeven


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

Wanneer de insteekmodule voor spellingcontrole is geactiveerd, gebruikt de RTE woordenboeken voor elke geschikte taal. Deze worden vervolgens geselecteerd volgens de taal van de website door ofwel de taaleigenschap van de substructuur te nemen of de taal uit de URL te halen; bijvoorbeeld. de `/en/` vertakking wordt gecontroleerd als Engels, de `/de/` vertakking als Duits.

>[!NOTE]
Het bericht `Spell checking failed` wordt gezien als een controle voor een taal wordt geprobeerd die niet geïnstalleerd is. De standaardwoordenboeken bevinden zich in `/libs/cq/spellchecker/dictionaries`de map en de juiste leesmij-bestanden. Wijzig de bestanden niet.

Een standaard AEM installatie omvat de woordenboeken voor Amerikaans Engels (`en_us`) en Brits Engels (`en_gb`). Voer de volgende stappen uit om meer woordenboeken toe te voegen.

1. Ga naar de pagina [https://extensions.openoffice.org/](https://extensions.openoffice.org/).

1. Ga op een van de volgende manieren te werk om een woordenboek te zoeken waarin u uw taal kunt kiezen:

   * Zoek naar woordenboek van uw taalkeuze. Zoek op de woordenboekpagina de koppeling naar de oorspronkelijke bron of de oorspronkelijke webpagina van de auteur. Zoek de woordenboekbestanden voor v2.x op een dergelijke pagina.
   * Zoek naar bestanden voor v2.x-woordenboeken op [https://wiki.openoffice.org/wiki/User:Khirano/Dictionaries](https://wiki.openoffice.org/wiki/User:Khirano/Dictionaries).

1. Download het archief met de spellingdefinities. Extraheer de inhoud van het archief op uw bestandssysteem.

   >[!CAUTION]
   Alleen woordenboeken in de `MySpell` indeling voor OpenOffice.org v2.0.1 of eerder worden ondersteund. Aangezien de woordenboeken nu archiefbestanden zijn, wordt u aangeraden het archief na het downloaden te verifiëren.

1. Zoek de .aff- en .dic-bestanden. Bestandsnaam in kleine letters behouden. Bijvoorbeeld `de_de.aff` en `de_de.dic`.
1. Laad de .aff- en .dic-bestanden in de opslagplaats op `/apps/cq/spellchecker/dictionaries`.

>[!NOTE]
De spellingcontrole van RTE is beschikbaar op bestelling. Deze wordt niet automatisch uitgevoerd wanneer u tekst gaat typen. Klik op de werkbalk om de spellingcontrole uit te voeren. [!UICONTROL Spellchecker] RTE controleert de spelling van woorden en benadrukt de verkeerd gespelde woorden.
Als u een wijziging opneemt die door de spellingcontrole wordt voorgesteld, wordt de status van de tekst gewijzigd en worden onjuist gespelde woorden niet langer gemarkeerd. Als u de spellingcontrole wilt uitvoeren, tikt u nogmaals op de knop Spellingcontrole of klikt u nogmaals op de knop Spellingcontrole.

## De historiegrootte voor acties voor ongedaan maken en opnieuw uitvoeren configureren {#undohistory}

Met RTE kunnen auteurs enkele laatste bewerkingen ongedaan maken of opnieuw uitvoeren. Standaard worden 50 bewerkingen opgeslagen in de geschiedenis. U kunt deze waarde naar wens configureren.

1. Navigeer binnen uw component naar het knooppunt `<rtePlugins-node>/undo`. Maak deze knooppunten als deze niet bestaan. Zie Een plug-in [activeren voor meer informatie](#activateplugin).
1. Maak de eigenschap op het `undo` knooppunt:

   * **Naam** `maxUndoSteps`
   * **Type** `Long`
   * **Waarde** het aantal stappen voor ongedaan maken dat u in de geschiedenis wilt opslaan. De standaardwaarde is 50. Gebruik deze optie `0` om de bewerking Ongedaan maken/Opnieuw volledig uit te schakelen.

1. Sla de wijzigingen op.

## De tabgrootte configureren {#tabsize}

Wanneer het tabteken wordt ingedrukt binnen tekst, wordt een vooraf gedefinieerd aantal spaties ingevoegd. Dit zijn standaard drie vaste spaties en één spatie.

De tabgrootte definiëren:

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/keys`. Maak de knooppunten als deze niet bestaan. Zie Een plug-in [activeren voor meer informatie](#activateplugin).
1. Maak de eigenschap op het `keys` knooppunt:

   * **Naam** `tabSize`
   * **Type** `String`
   * **Waarde** het aantal spatietekens dat voor de tabulator moet worden gebruikt.

1. Sla de wijzigingen op.

## Inspringingsmarge instellen {#indentmargin}

Wanneer inspringing is ingeschakeld (standaard), kunt u de grootte van de inspringing definiëren:

>[!NOTE]
Deze inspringingsgrootte wordt alleen toegepast op alinea&#39;s (blokken tekst). het heeft geen invloed op de inspringing van feitelijke lijsten.

1. Navigeer binnen uw component naar het knooppunt `<rtePlugins-node>/lists`. Maak deze knooppunten als deze niet bestaan. Zie Een plug-in [activeren voor meer informatie](#activateplugin).
1. Maak op het `lists` knooppunt de `identSize` parameter:

   * **Naam**: `identSize`
   * **Type**: `Long`
   * **Waarde**: aantal pixels dat is vereist voor de inspringingsmarge.

## De hoogte van bewerkbare ruimte configureren {#editablespace}

>[!NOTE]
Dit is alleen van toepassing wanneer u de RTE gebruikt in een dialoogvenster (niet tijdens het bewerken op locatie in een klassieke UI).

U kunt de hoogte van de bewerkbare ruimte definiëren die in het dialoogvenster van de component wordt weergegeven:

1. Maak een nieuwe eigenschap op het `../items/text` knooppunt in de dialoogdefinitie voor de component:

   * **Naam** `height`
   * **Type** `Long`
   * **Geef** de hoogte van het bewerkingscanvas op in pixels.

   >[!NOTE]
   Hiermee wijzigt u de hoogte van het dialoogvenster niet.

1. Sla de wijzigingen op.

## Stijlen en protocollen voor koppelingen configureren {#linkstyles}

Bij het toevoegen van koppelingen in AEM kunt u het volgende definiëren:

* De CSS-stijlen die moeten worden gebruikt
* De automatisch aanvaarde protocollen

Om te vormen hoe de verbindingen in AEM van een ander programma worden toegevoegd, bepaal de regels van HTML.

1. Zoek met CRXDE Lite de tekstcomponent voor uw project.
1. Maak een nieuw knooppunt op hetzelfde niveau als `<rtePlugins-node>`, dat wil zeggen, maak het knooppunt onder het bovenliggende knooppunt van `<rtePlugins-node>`:

   * **Naam** `htmlRules`
   * **Type** `nt:unstructured`

   >[!NOTE]
   Het `../items/text` knooppunt heeft de eigenschap:
   * **Naam** `xtype`
   * **Type** `String`
   * **Waarde** `richtext`

   De locatie van het `../items/text` knooppunt kan variëren, afhankelijk van de structuur van het dialoogvenster; twee voorbeelden zijn :
   * `/apps/myProject>/components/text/dialog/items/text`
   * `/apps/<myProject>/components/text/dialog/items/panel/items/text`


1. Maak onder `htmlRules`een nieuw knooppunt.

   * **Naam** `links`
   * **Type** `nt:unstructured`

1. Definieer onder het `links` knooppunt de vereiste eigenschappen:

   * CSS-stijl voor interne koppelingen:

      * **Naam** `cssInternal`
      * **Type** `String`
      * **Waarde** de naam van de CSS-klasse (zonder een voorafgaande &#39;.&#39;; for example, `cssClass` instead of `.cssClass`)
   * CSS-stijl voor externe koppelingen

      * **Naam** `cssExternal`
      * **Type** `String`
      * **Waarde** de naam van de CSS-klasse (zonder een voorafgaande &#39;.&#39;; for example, `cssClass` instead of `.cssClass`)
   * Array met geldige **protocollen**. De ondersteunde protocollen zijn `http://`, `https://`, `file://`en `mailto:`.

      * **Naam** `protocols`
      * **Type** `String[]`
      * **Waarde**(s) een of meer protocollen
   * **defaultProtocol** (eigenschap van het type **String**): Protocol dat moet worden gebruikt als de gebruiker niet uitdrukkelijk één specificeerde.

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

               (opgegeven door de `targetExternal` eigenschap voor externe koppelingen of `targetInternal` voor interne koppelingen).

            * `manual`: niet van toepassing in dit verband
            * `blank`: niet van toepassing in dit verband
      * Het doel voor interne koppelingen:

         * **Naam** `targetInternal`
         * **Type** `String`
         * **Waarde** van het doel voor interne koppelingen (alleen gebruiken als de modus is `auto`)
      * Het doel voor externe koppelingen:

         * **Naam** `targetExternal`
         * **Type** `String`
         * **Waarde** het doel voor externe koppelingen (wordt alleen gebruikt als de modus is `auto`).








1. Sla alle wijzigingen op.
