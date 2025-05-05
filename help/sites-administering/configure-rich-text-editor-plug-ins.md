---
title: De invoegtoepassingen van de Rich Text Editor configureren
description: Leer hoe u de insteekmodules van de Adobe Experience Manager Rich Text Editor configureert voor het inschakelen van afzonderlijke functies.
contentOwner: AG
exl-id: 6bfd6caa-a68a-40ba-9826-4ba02cd1dbfb
solution: Experience Manager, Experience Manager Sites
feature: Configuring
role: Admin
source-git-commit: f64a1014dfd1155bcf815e75a27102244ef6c6de
workflow-type: tm+mt
source-wordcount: '4376'
ht-degree: 0%

---


# De invoegtoepassingen van de Rich Text Editor configureren {#configure-the-rich-text-editor-plug-ins}

De functionaliteit van RTE wordt beschikbaar gemaakt via een reeks stop-ins, elk met eigenschappen bezit. U kunt het eigenschapbezit vormen om één of meerdere eigenschappen van RTE toe te laten of onbruikbaar te maken. Dit artikel beschrijft hoe te om de stop-ins specifiek te vormen RTE.

Voor details over de andere configuraties van RTE, zie [ RichRedacteur van de Tekst ](/help/sites-administering/rich-text-editor.md) vormen.

>[!NOTE]
>
>Als u met CRXDE Lite werkt, wordt u aangeraden de wijzigingen regelmatig op te slaan met de optie [!UICONTROL Save All] .

## Een insteekmodule activeren en de eigenschap features configureren {#activateplugin}

Voer de volgende stappen uit om een plug-in te activeren. Sommige stappen zijn alleen nodig wanneer u een insteekmodule voor het eerst configureert, omdat de bijbehorende knooppunten niet bestaan.

Standaard zijn `format` -, `link` -, `list` -, `justify` - en `control` -plug-ins en alle bijbehorende functies ingeschakeld in RTE.

>[!NOTE]
>
>Het respectievelijke `rtePlugins` -knooppunt wordt `<rtePlugins-node>` genoemd om dubbel werk in dit artikel te voorkomen.

1. Zoek met CRXDE Lite de tekstcomponent voor uw project.
1. Maak het bovenliggende knooppunt van `<rtePlugins-node>` als dit niet bestaat, voordat u eventuele RTE-plug-ins configureert:

   * Afhankelijk van uw component zijn de bovenliggende knooppunten:

      * `config: .../text/cq:editConfig/cq:inplaceEditing/config`
      * een alternatief configuratieknooppunt: `.../text/cq:editConfig/cq:inplaceEditing/inplaceEditingTextConfig`
      * `text: .../text/dialog/items/tab1/items/text`

   * Zijn van type: **jcr:primaryType** `cq:Widget`
   * Beide hebben de volgende eigenschappen:

      * **Naam** `name`
      * **Type** `String`
      * **Waarde** `./text`

1. Afhankelijk van de interface waarvoor u vormt, creeer een knoop `<rtePlugins-node>`, als het niet bestaat:

   * **Naam** `rtePlugins`
   * **Type** `nt:unstructured`

1. Maak hieronder een knooppunt voor elke plug-in die u wilt activeren:

   * **Type** `nt:unstructured`
   * **Naam** vereiste Plug-in identiteitskaart van de insteekmodule

Nadat u een plug-in hebt geactiveerd, volgt u deze richtlijnen om de eigenschap `features` te configureren.

| | Alle functies inschakelen | Enkele specifieke functies inschakelen | Alle functies uitschakelen |
|---|---|---|---|
| Naam | functies | functies | functies |
| Type | String | Tekenreeks [] (meerdere tekenreeksen; stel Type in op String en klik op Meerdere in CRXDE Lite) | String |
| Waarde | `*` (een sterretje) | ingesteld op een of meer functiewaarden | - |

## Begrijp de findreplace plug-in {#findreplace}

Voor de insteekmodule `findreplace` is geen configuratie nodig. Het werkt uit de doos.

Wanneer u de vervangingsfunctie gebruikt, moet de te vervangen tekenreeks op hetzelfde moment worden ingevoerd als de zoektekenreeks. U kunt echter nog steeds op Zoeken klikken om de tekenreeks te zoeken voordat u deze vervangt. Als de vervangingstekenreeks wordt ingevoerd nadat op Zoeken is geklikt, wordt de zoekopdracht opnieuw ingesteld op het begin van de tekst.

Het dialoogvenster Zoeken en vervangen wordt transparant wanneer op Zoeken wordt geklikt en wordt dekkend wanneer op Vervangen wordt geklikt. Hierdoor kan de auteur de tekst controleren die de auteur vervangt. Als gebruikers op Alles vervangen klikken, wordt het dialoogvenster gesloten en wordt het aantal aangebrachte vervangingen weergegeven.

## De plakmodi configureren {#paste-modes}

Wanneer het gebruiken van RTE, kunnen de auteurs inhoud in één van de volgende drie wijzen kleven:

* **Browser wijze**: De tekst van het Deeg die browser standaard deegimplementatie gebruikt. Het is geen aanbevolen methode omdat hierdoor ongewenste opmaakcodes kunnen ontstaan.

* **Onbewerkte tekstwijze**: Plak de inhoud van het klembord als gewone tekst. Alle elementen van stijl en opmaak worden uit de gekopieerde inhoud verwijderd voordat deze in de component [!DNL Experience Manager] worden ingevoegd.

* **MS® Word wijze**: Plak de tekst, met inbegrip van lijsten, met het formatteren wanneer het kopiëren van MS® Word. Het kopiëren en plakken van tekst uit een andere bron, zoals een webpagina of MS® Excel, wordt niet ondersteund en behoudt alleen de gedeeltelijke opmaak.

### De beschikbare plakopties op de werkbalk RTE configureren  {#configure-paste-options-available-on-the-rte-toolbar}

U kunt sommige, alle, of geen van deze drie pictogrammen aan uw auteurs in de toolbar van RTE verstrekken:

* **[!UICONTROL Paste (Ctrl+V)]**: kan vooraf worden geconfigureerd om overeen te komen met een van de drie bovenstaande plakmodi.

* **[!UICONTROL Paste as Text]**: biedt functionaliteit voor normale tekstmodus.

* **[!UICONTROL Paste from Word]**: biedt functionaliteit in de MS® Word-modus.

Om RTE te vormen om de vereiste pictogrammen te tonen, volg deze stappen.

1. Navigeer naar de component, bijvoorbeeld `/apps/<myProject>/components/text` .
1. Navigeer naar het knooppunt `rtePlugins/edit` . Zie [ insteekmodule ](#activateplugin) activeren als de knoop niet bestaat.
1. Maak de eigenschap `features` op het knooppunt `edit` en voeg een of meer functies toe. Sla alle wijzigingen op.

### Het gedrag van het pictogram en de sneltoets Plakken (Ctrl+V) configureren {#configure-the-behavior-of-the-paste-ctrl-v-icon-and-shortcut}

U kunt het gedrag van het pictogram **[!UICONTROL Paste (Ctrl+V)]** vooraf configureren door de volgende stappen uit te voeren. Deze configuratie definieert ook het gedrag van sneltoetsen Ctrl+V die auteurs gebruiken om inhoud te plakken.

De configuratie staat voor de volgende drie soorten gebruiksgevallen toe:

* Plak tekst met gebruik van de standaardimplementatie van de browser. Het is geen aanbevolen methode omdat hierdoor ongewenste opmaakcodes kunnen ontstaan. geconfigureerd met `browser` verderop.

* Plak de inhoud van het klembord als onbewerkte tekst. Alle elementen van stijl en opmaak worden uit de gekopieerde inhoud verwijderd voordat deze in AEM component worden ingevoegd. geconfigureerd met `plaintext` verderop.

* Plak de tekst, inclusief tabellen, met opmaak wanneer u kopieert vanuit MS® Word. Het kopiëren en plakken van tekst uit een andere bron, zoals een webpagina of MS® Excel, wordt niet ondersteund en behoudt alleen de gedeeltelijke opmaak. geconfigureerd met `wordhtml` verderop.

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/edit` . Maak de knooppunten als deze niet bestaan. Voor meer informatie, zie [ een elektrisch toestel ](#activateplugin) activeren.
1. Maak in het knooppunt `edit` een eigenschap met de volgende details:

   * **Naam** `defaultPasteMode`
   * **Type** `String`
   * **Waarde** Één van de vereiste deegwijze `browser`, `plaintext`, of `wordhtml`.

### Indelingen configureren die zijn toegestaan bij het plakken van inhoud {#pasteformats}

De deeg-als-Microsoft-Word (`paste-wordhtml`) wijze kan verder worden gevormd zodat u kunt uitdrukkelijk bepalen welke stijlen worden toegestaan wanneer het kleven in AEM van een ander programma, zoals Microsoft® Word.

Als u bijvoorbeeld alleen vette indelingen en lijsten wilt toestaan bij het plakken in AEM, kunt u de andere indelingen filteren. Dit wordt configureerbare het kleven het filtreren genoemd, die voor allebei kan worden gedaan:

* [Tekst](#paste-modes)
* [Koppelingen](#linkstyles)

Voor koppelingen kunt u ook de protocollen definiëren die automatisch worden geaccepteerd.

Om te vormen welke formaten worden toegestaan wanneer het kleven van tekst in AEM van een ander programma:

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/edit` . Maak de knooppunten als deze niet bestaan. Voor meer details, zie [ een elektrisch toestel ](#activateplugin) activeren.
1. Maak een knooppunt onder het knooppunt `edit` zodat u de plakregels voor HTML kunt bevatten:

   * **Naam** `htmlPasteRules`
   * **Type** `nt:unstructured`

1. Maak een knooppunt onder `htmlPasteRules` , zodat u details kunt bevatten over de toegestane basisindelingen:

   * **Naam** `allowBasics`
   * **Type** `nt:unstructured`

1. Als u de afzonderlijke geaccepteerde indelingen wilt beheren, maakt u een of meer van de volgende eigenschappen op het knooppunt `allowBasics` :

   * **Naam** `bold`
   * **Naam** `italic`
   * **Naam** `underline`
   * **Naam** `anchor` (voor zowel verbindingen als genoemde ankers)
   * **Naam** `image`

   Alle eigenschappen zijn van **Type** `Boolean`, zodat in de aangewezen **Waarde** kunt u of het vinkje selecteren of verwijderen om de functionaliteit toe te laten of onbruikbaar te maken.

   >[!NOTE]
   >
   >Indien niet expliciet gedefinieerd, wordt de standaardwaarde true gebruikt en wordt de opmaak geaccepteerd.

1. Andere indelingen kunnen ook worden gedefinieerd met behulp van een reeks andere eigenschappen of knooppunten, die ook worden toegepast op het knooppunt `htmlPasteRules` . Sla alle wijzigingen op.

U kunt de volgende eigenschappen gebruiken voor `htmlPasteRules` .

| Eigenschap | Type | Beschrijving |
|---|---|---|
| `allowBlockTags` | String | Hiermee definieert u de lijst met blokcodes die zijn toegestaan. Enkele mogelijke blokcodes zijn: <ul> <li>koppen (h1, h2, h3)</li> <li>lid p)</li> <li>lijsten (ol, ul)</li> <li>tabellen (tabel)</li> </ul> |
| `fallbackBlockTag` | String | Definieert de bloktag die wordt gebruikt voor blokken met een bloktag die niet in `allowBlockTags` zijn opgenomen. `p` is meestal voldoende. |
| table | nt:ongestructureerd | Hiermee definieert u het gedrag bij het plakken van tabellen. Dit knooppunt moet de eigenschap `allow` (type Boolean) hebben om te bepalen of het plakken van tabellen is toegestaan. Als allow is ingesteld op `false` , moet u de eigenschap `ignoreMode` (type String) opgeven om te bepalen hoe geplakte tabelinhoud wordt verwerkt. Geldige waarden voor `ignoreMode` zijn: <ul> <li>`remove`: hiermee wordt tabelinhoud verwijderd.</li> <li>`paragraph`: hiermee worden tabelcellen omgezet in alinea&#39;s.</li> </ul> |
| list | nt:ongestructureerd | Hiermee definieert u het gedrag bij het plakken van lijsten. U moet de eigenschap `allow` (type Boolean) hebben om te definiëren of het plakken van lijsten is toegestaan. Wanneer `allow` is ingesteld op `false` , moet u de eigenschap `ignoreMode` (type String) opgeven om te bepalen hoe inhoud uit de lijst moet worden verwerkt. Geldige waarden voor `ignoreMode` zijn: <ul><li> `remove`: hiermee verwijdert u de inhoud van de lijst.</li> <li>`paragraph`: zet lijstitems om in alinea&#39;s.</li> </ul> |

Hieronder ziet u een voorbeeld van een geldige `htmlPasteRules` -structuur.

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

## Tekststijlen configureren {#textstyles}

Auteurs kunnen stijlen toepassen om de weergave van een deel van de tekst te wijzigen. De stijlen zijn gebaseerd op CSS-klassen die u vooraf definieert in uw CSS-stijlpagina. Stileerde inhoud wordt ingesloten in `span` -tags, waarbij het kenmerk `class` naar de CSS-klasse verwijst. Bijvoorbeeld `<span class=monospaced>Monospaced Text Here</span>` .

Wanneer de plug-in Stijlen voor de eerste keer is ingeschakeld, zijn er geen standaardstijlen beschikbaar. De pop-uplijst is leeg. Ga als volgt te werk om de auteurs stijlen te voorzien:

* Schakel de vervolgkeuzelijst Stijl in.
* Geef de locaties van de stijlpagina&#39;s op.
* Geef de afzonderlijke stijlen op die u kunt selecteren in de vervolgkeuzelijst Stijl.

Voor latere configuraties, bijvoorbeeld om meer stijlen toe te voegen, volg slechts de instructies om naar een nieuw stijlblad te verwijzen en de extra stijlen te specificeren.

>[!NOTE]
>
>U kunt Stijlen voor [ lijsten of lijstcellen ](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tablestyles) bepalen. Deze configuraties vereisen afzonderlijke procedures.

### De vervolgkeuzelijst Stijl inschakelen {#styleselectorlist}

U doet dit door de plug-in Stijl in te schakelen.

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/styles` . Maak de knooppunten als deze niet bestaan. Voor meer details, zie [ een elektrisch toestel ](#activateplugin) activeren.
1. Maak de eigenschap `features` op het knooppunt `styles` :

   * **Naam** `features`
   * **Type** `String`
   * **Waarde** `*` (asterisk)

1. Sla alle wijzigingen op.

>[!NOTE]
>
>Zodra de plug-in Stijlen is ingeschakeld, wordt de vervolgkeuzelijst Stijl weergegeven in het dialoogvenster Bewerken. De lijst is echter leeg omdat er geen stijlen zijn geconfigureerd.

### De locatie van de stijlpagina opgeven {#locationofstylesheet}

Geef vervolgens de locaties op van de stijlpagina&#39;s waarnaar u wilt verwijzen:

1. Navigeer naar het hoofdknooppunt van de tekstcomponent, bijvoorbeeld `/apps/<myProject>/components/text` .
1. Voeg de eigenschap `externalStyleSheets` toe aan het bovenliggende knooppunt van `<rtePlugins-node>` :

   * **Naam** `externalStyleSheets`
   * **Type** `String[]` (multi-koord; klik **Multi** in CRXDE)
   * **Waarden** de weg en filename van elk stijlblad dat u wilt omvatten. Gebruik repository paden.

   >[!NOTE]
   >
   >U kunt op elk later moment verwijzingen naar extra stijlbladen toevoegen.

1. Sla alle wijzigingen op.

>[!NOTE]
>
>Wanneer u RTE gebruikt in een dialoogvenster (Klassieke UI), kunt u stijlpagina&#39;s opgeven die zijn geoptimaliseerd voor RTF-bewerking. Vanwege technische beperkingen gaat de CSS-context verloren in de editor, dus u kunt deze context emuleren om de WYSIWYG-ervaring te verbeteren.
>
>De Rich Text Editor gebruikt een container-DOM-element met de id `CQrte` die kan worden gebruikt voor verschillende stijlen voor weergave en bewerking:
>
>`#CQ td {`
>` // defines the style for viewing }`
>
>`#CQrte td {`
>` // defines the style for editing }`

### Geef de beschikbare stijlen op in de pop-uplijst {#stylesindropdown}

1. In de componentendefinitie, navigeer aan de knoop `<rtePlugins-node>/styles`, zoals gecreeerd in [ toelatend de stijldrop-down selecteur ](#styleselectorlist).
1. Onder het knooppunt `styles` maakt u een knooppunt (ook wel `styles` genoemd) voor de opname van de lijst die beschikbaar wordt gesteld:

   * **Naam** `styles`
   * **Type** `cq:WidgetCollection`

1. Maak een knooppunt onder het knooppunt `styles` , zodat u een afzonderlijke stijl kunt voorstellen:

   * **Naam**, kunt u de naam specificeren, maar het zou voor de stijl geschikt moeten zijn
   * **Type** `nt:unstructured`

1. Voeg de eigenschap `cssName` toe aan dit knooppunt zodat u naar de CSS-klasse kunt verwijzen:

   * **Naam** `cssName`
   * **Type** `String`
   * **Waarde** de naam van de CSS klasse (zonder het voorafgaande &#39;.&#39;; bijvoorbeeld `cssClass` in plaats van `.cssClass` )

1. Voeg de eigenschap `text` toe aan hetzelfde knooppunt. Hiermee wordt de tekst in het selectievak gedefinieerd:

   * **Naam** `text`
   * **Type** `String`
   * **Beschrijving van de Waarde** van de stijl; verschijnt in de drop-down de selectiedoos van de Stijl.

1. Sla de wijzigingen op.

   Herhaal bovenstaande stappen voor elke vereiste stijl.

### RTE configureren voor optimale woordeinden in het Japans {#jpwordwrap}

Auteurs die AEM gebruiken om inhoud in het Japans te ontwerpen, kunnen een stijl toepassen op tekens om regeleinden te voorkomen wanneer een regeleinde niet vereist is. Op deze manier kunnen auteurs de zinnen op de gewenste positie laten afbreken. De stijl voor deze functionaliteit is gebaseerd op CSS-klasse die vooraf is gedefinieerd in de CSS-stijlpagina.

>[!NOTE]
>
>Deze eigenschap vereist minstens AEM 6.5 Service Pack 1.

Ga als volgt te werk om de stijl te maken die auteurs op Japanse tekst kunnen toepassen:

1. Maak een knooppunt onder het knooppunt Stijlen. Zie [ een nieuwe stijl ](#stylesindropdown) specificeren.
   * Naam: `jpn-word-wrap`
   * Type: `nt:unstructure`

1. Voeg de eigenschap `cssName` toe aan het knooppunt zodat u naar de CSS-klasse kunt verwijzen. Deze klassenaam is een gereserveerde naam voor de functie voor tekstomloop in Japans.
   * Naam: `cssName`
   * Type: `String`
   * Waarde: `jpn-word-wrap` (zonder voorafgaande `.`)

1. Voeg de bezitstekst aan de zelfde knoop toe. De waarde is de naam van de stijl die de auteur ziet bij het selecteren van de stijl.
   * Naam: `text`
*Type: `String`
   * Waarde: `Japanese word-wrap`

1. Maak een stijlpagina en geef het pad op. Zie [ plaats van stijlblad ](#locationofstylesheet) specificeren. Voeg de volgende inhoud toe aan de stijlpagina. Wijzig de achtergrondkleur naar wens.

   ```css
   .text span.jpn-word-wrap {
       display:inline-block;
   }
   .is-edited span.jpn-word-wrap {
       background-color: #ffddff;
   }
   ```

   ![ Stylesheet om de Japanse eigenschap van de woordomslag ter beschikking te stellen aan auteurs ](assets/rte_jpwordwrap_stylesheet.jpg)

## Alinea-indelingen configureren {#paraformats}

Tekst die in RTE wordt geschreven, wordt binnen een bloktag geplaatst, waarbij de standaardwaarde `<p>` is. Als u de plug-in `paraformat` inschakelt, geeft u via een vervolgkeuzelijst aanvullende blokcodes op die aan alinea&#39;s kunnen worden toegewezen. Alineaopmaak bepaalt het alineatype door de juiste bloktag toe te wijzen. De auteur kan deze selecteren en toewijzen met de kiezer Indeling. De voorbeeldbloklabels omvatten onder andere de standaardalinea &lt;p> en koppen &lt;h1>, &lt;h2> enzovoort.

>[!CAUTION]
>
>Deze plug-in is niet geschikt voor inhoud met complexe structuren, zoals lijsten of tabellen.

>[!NOTE]
>
>Als een bloktag, bijvoorbeeld een tag &lt;hr>, niet aan een alinea kan worden toegewezen, is dit geen geldig gebruiksgeval voor een insteekmodule voor paraformat.

Wanneer de insteekmodule Alineopmaak voor het eerst is ingeschakeld, zijn er geen standaardalineaopmaak beschikbaar. De pop-uplijst is leeg. Ga als volgt te werk om de auteurs alinea-indelingen te bieden:

* Schakel de vervolgkeuzelijst Indeling in.
* Geef in de vervolgkeuzelijst de blokcodes op die als alineaopmaak kunnen worden geselecteerd.

Voor recentere configuraties of herconfiguraties, zeg om meer formaten toe te voegen, volg slechts het relevante deel van de instructies.

### De keuzelijst Indeling inschakelen {#formatselectorlist}

Schakel eerst de paraformat-plug-in in:

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/paraformat` . Maak de knooppunten als deze niet bestaan. Voor meer details, zie [ een elektrisch toestel ](#activateplugin) activeren.
1. Maak de eigenschap `features` op het knooppunt `paraformat` :

   * **Naam** `features`
   * **Type** `String`
   * **Waarde** `*` (asterisk)

>[!NOTE]
>
>Als de plug-in niet verder is geconfigureerd, zijn de volgende standaardindelingen ingeschakeld:
>
>* Alinea ( `<p>`)
>* Kop 1 ( `<h1>`)
>* Kop 2 ( `<h2>`)
>* Kop 3 ( `<h3>`)
>

>[!CAUTION]
>
>Wanneer het vormen van het paragraafformaat van RTE, verwijder niet de paragraafmarkering &lt;p> als het formatteren optie. Als de `<p>` markering wordt verwijderd, dan kan de inhoudauteur niet de **Indelingen van de Paragraaf** optie selecteren zelfs als er extra gevormde formaten zijn.

### Beschikbare alineaopmaak opgeven {#paraformatsindropdown}

Alinea-indelingen kunnen voor selectie beschikbaar worden gesteld door:

1. In de componentendefinitie, navigeer aan de knoop `<rtePlugins-node>/paraformat`, zoals gecreeerd in [ toelatend de formaatdrop-down selecteur ](#styleselectorlist).
1. Maak onder het knooppunt `paraformat` een knooppunt voor de lijst met indelingen:

   * **Naam** `formats`
   * **Type** `cq:WidgetCollection`

1. Maak een knooppunt onder het knooppunt `formats` . Dit bevat gegevens voor een afzonderlijke indeling:

   * **Naam**, kunt u de naam specificeren, maar het zou voor het formaat (bijvoorbeeld, mijnparagraaf, myheading1) geschikt moeten zijn.
   * **Type** `nt:unstructured`

1. Aan dit knooppunt voegt u de eigenschap toe om de gebruikte bloktag te definiëren:

   * **Naam** `tag`
   * **Type** `String`
   * **Waarde** de blokmarkering voor het formaat; bijvoorbeeld: p, h1, h2.

     U hoeft de punthaakjes voor scheidingstekens niet in te voeren.

1. Aan de zelfde knoop voeg een ander bezit toe, voor beschrijvende tekst om in de drop-down lijst te verschijnen:

   * **Naam** `description`
   * **Type** `String`
   * **Waarde** de beschrijvende tekst voor dit formaat; bijvoorbeeld, Paragraaf, Kop 1, Kop 2. Deze tekst wordt weergegeven in de selectielijst Indeling.

1. Sla de wijzigingen op.

   Herhaal de stappen voor elke vereiste indeling.

>[!CAUTION]
>
>Als u aangepaste indelingen definieert, worden de standaardindelingen ( `<p>` , `<h1>` , `<h2>` en `<h3>` ) verwijderd. Maak de `<p>` -indeling opnieuw omdat dit de standaardindeling is.

## Speciale tekens configureren {#spchar}

Wanneer de plug-in `misctools` in een standaard AEM is ingeschakeld voor speciale tekens ( `specialchars` ), is er direct een standaardselectie beschikbaar voor gebruik, bijvoorbeeld de symbolen copyright en handelsmerk.

U kunt RTE vormen om uw eigen selectie van karakters beschikbaar te maken; of door verschillende karakters, of een volledige opeenvolging te bepalen.

>[!CAUTION]
>
>Als u uw eigen speciale tekens toevoegt, wordt de standaardselectie genegeerd. Definieer deze tekens desgewenst in uw eigen selectie of definieer ze opnieuw.

### Eén teken definiëren {#definesinglechar}

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/misctools` . Maak de knooppunten als deze niet bestaan. Voor meer details, zie [ een elektrisch toestel ](#activateplugin) activeren.
1. Maak de eigenschap `features` op het knooppunt `misctools` :

   * **Naam** `features`
   * **Type** `String[]`
   * **Waarde** `specialchars`

         (of `String / *` als u alle functies voor deze plug-in toepast)

1. Onder `misctools` maakt u een knooppunt voor de speciale tekenconfiguraties:

   * **Naam** `specialCharsConfig`
   * **Type** `nt:unstructured`

1. Onder `specialCharsConfig` maakt u een ander knooppunt voor de lijst met tekens:

   * **Naam** `chars`
   * **Type** `nt:unstructured`

1. Voeg onder `chars` een knooppunt toe voor een afzonderlijke tekendefinitie:

   * **Naam** u kunt de naam specificeren, maar het zou op het karakter moeten wijzen; bijvoorbeeld, de helft.
   * **Type** `nt:unstructured`

1. Voeg de volgende eigenschap toe aan dit knooppunt:

   * **Naam** `entity`
   * **Type** `String`
   * **Waarde** de vertegenwoordiging van de HTML van het vereiste karakter; bijvoorbeeld, `&189;` voor de fractie één helft.

1. Sla de wijzigingen op.

In CRXDE, zodra het bezit wordt bewaard, wordt het vertegenwoordigde karakter getoond. Zie onder het voorbeeld van de helft. Herhaal bovenstaande stappen zodat u auteurs meer speciale tekens ter beschikking kunt stellen.

![ in CRXDE, voeg één enkel karakter toe dat in de toolbar van RTE ](assets/chlimage_1-106.png " in CRXDE beschikbaar moet worden gemaakt, voeg één enkel karakter toe dat op de toolbar van RTE ") beschikbaar moet worden gemaakt

### Een tekenbereik definiëren {#definerangechar}

1. De stappen 1 van het gebruik - 3 van [ die Één enkel Karakter ](#definesinglechar) bepalen.
1. Voeg onder `chars` een knooppunt toe voor de definitie van het tekenbereik:

   * **Naam** u kunt de naam specificeren, maar het zou op de karakterwaaier moeten wijzen; bijvoorbeeld, potloden.
   * **Type** `nt:unstructured`

1. Voeg onder dit knooppunt (benoemd op basis van uw speciale tekenbereik) de volgende twee eigenschappen toe:

   * **Naam** `rangeStart`

     **Type** `Long`
     **Waarde** de [ vertegenwoordiging van Unicode ](https://unicode.org/) (decimaal) van het eerste karakter in de waaier

   * **Naam** `rangeEnd`

     **Type** `Long`
     **Waarde** de [ vertegenwoordiging van Unicode ](https://unicode.org/) (decimaal) van het laatste karakter in de waaier

1. Sla de wijzigingen op.

   Als u bijvoorbeeld een bereik 9998 - 10000 definieert, kunt u de volgende tekens gebruiken.

   ![ in CRXDE, bepaal een waaier van karakters die in RTE ](assets/chlimage_1-107.png) beschikbaar moeten worden gemaakt

   *Cijfer: In CRXDE, bepaal een waaier van karakters die in RTE* beschikbaar moeten worden gemaakt

   ![ Speciale karakters beschikbaar in RTE worden getoond aan auteurs in een pop-up venster ](assets/rtepencil.png " Speciale karakters beschikbaar in RTE worden getoond aan auteurs in een pop-up venster ")

## Tabelstijlen configureren {#tablestyles}

Stijlen worden doorgaans toegepast op tekst, maar een aparte set stijlen kan ook worden toegepast op een tabel of op een paar tabelcellen. Dergelijke stijlen zijn beschikbaar voor auteurs in het selectievak Stijl in het dialoogvenster Eigenschappen van cel of Tabeleigenschappen. De stijlen zijn beschikbaar wanneer het uitgeven van een lijst binnen een component van de Tekst (of een derivaat) en niet in de standaardcomponent van de Lijst.

>[!NOTE]
>
>U kunt stijlen alleen definiëren voor tabellen en cellen voor klassieke gebruikersinterface.

>[!NOTE]
>
>Het kopiëren en het kleven van lijsten in of van de component van RTE is browser-afhankelijk. De functie wordt niet in het vak ondersteund voor alle browsers. Afhankelijk van de tabelstructuur en de browser krijgt u mogelijk verschillende resultaten. Wanneer u bijvoorbeeld een tabel kopieert en plakt in een RTE-component in Mozilla Firefox in Classic UI en Touch UI, blijft de indeling van de tabel niet behouden.

1. Navigeer binnen uw component naar het knooppunt `<rtePlugins-node>/table` . Maak de knooppunten als deze niet bestaan. Voor meer details, zie [ een elektrisch toestel ](#activateplugin) activeren.
1. Maak de eigenschap `features` op het knooppunt `table` :

   * **Naam** `features`
   * **Type** `String`
   * **Waarde** `*` (asterisk)

   >[!NOTE]
   >
   >Als u niet alle tabelfuncties wilt inschakelen, kunt u de eigenschap `features` maken als volgt:
   >
   >* **Type** `String[]`
   >
   >* **Waarde** één, of allebei, van het volgende, zoals vereist:
   >* `table` om het bewerken van tabeleigenschappen mogelijk te maken, inclusief de stijlen.
   >* `cellprops` gebruiken om celeigenschappen, waaronder de stijlen, te kunnen bewerken.

1. Definieer de locatie van CSS-stijlpagina&#39;s zodat u deze kunt raadplegen. Zie [ het specificeren van de plaats van uw stijlblad ](#locationofstylesheet) aangezien dit het zelfde als wanneer het bepalen van [ stijlen voor tekst ](#textstyles) is. De locatie kan worden gedefinieerd als u andere stijlen hebt gedefinieerd.
1. Maak onder het knooppunt `table` de volgende nieuwe knooppunten (naar wens):

   * Om stijlen voor de volledige lijst (beschikbaar onder **eigenschappen van de Lijst**) te bepalen:

      * **Naam** `tableStyles`
      * **Type** `cq:WidgetCollection`

   * Om stijlen voor de individuele cellen (beschikbaar onder **eigenschappen van de Cel**) te bepalen:

      * **Naam** `cellStyles`
      * **Type** `cq:WidgetCollection`

1. Maak een knooppunt (onder het knooppunt `tableStyles` of `cellStyles` , al naar gelang), zodat u een afzonderlijke stijl kunt vertegenwoordigen:

   * **Naam** u kunt de naam specificeren, maar het zou op de stijl moeten wijzen.
   * **Type** `nt:unstructured`

1. Voor deze knoop, creeer de eigenschappen:

   * De CSS-stijl definiëren waarnaar moet worden verwezen

      * **Naam** `cssName`
      * **Type** `String`
      * **Waarde** de naam van de CSS klasse (zonder voorafgaande `.`, bijvoorbeeld, `cssClass` in plaats van `.cssClass`)

   * Een beschrijvende tekst definiëren die moet worden weergegeven in de vervolgkeuzelijst

      * **Naam** `text`
      * **Type** `String`
      * **Waarde** de tekst die in de selectielijst moet verschijnen

1. Sla alle wijzigingen op.

Herhaal bovenstaande stappen voor elke vereiste stijl.

### Verborgen koppen in tabellen configureren voor toegankelijkheid {#hiddenheader}

Soms kunt u gegevenslijsten zonder visuele tekst in een kolomkopbal tot stand brengen veronderstellend dat het doel van de kopbal door de visuele verhouding van de kolom met andere kolommen wordt geïmpliceerd. In dit geval moet verborgen binnentekst in de cel in de kopcel worden opgenomen. Hierdoor kunnen schermlezers en andere ondersteunende hulpmiddelen het doel van de kolom beter begrijpen.

Om toegankelijkheid in dergelijke scenario&#39;s te verbeteren, steunt RTE verborgen kopbalcellen. Bovendien worden er configuratie-instellingen gegeven voor verborgen koppen in tabellen. Met deze instellingen kunt u CSS-stijlen toepassen op verborgen koppen in de bewerkings- en voorvertoningsmodus. Om auteurs te helpen verborgen kopballen in Edit wijze identificeren, omvat de volgende parameters in uw code:

* `hiddenHeaderEditingCSS` - Geeft de naam op van de CSS-klasse die wordt toegepast op de cel met de verborgen koptekst wanneer RTE wordt bewerkt.
* `hiddenHeaderEditingStyle` - Geeft een stijltekenreeks op die wordt toegepast op de cel met de verborgen koptekst wanneer RTE wordt bewerkt.

Als u zowel de CSS-tekenreeks als de stijltekenreeks in code opgeeft, heeft de CSS-klasse voorrang op de stijltekenreeks en kan deze alle configuratiewijzigingen overschrijven die de stijltekenreeks aanbrengt.

Om auteurs te helpen CSS op verborgen kopballen op de voorproefwijze toepassen, kunt u de volgende parameters in uw code omvatten:

* `hiddenHeaderClassName` - Geeft de naam op van de CSS-klasse die wordt toegepast op de verborgen kopcel in de voorvertoningsmodus.
* `hiddenHeaderStyle` - Geeft een stijltekenreeks op die wordt toegepast op de verborgen kopcel in de voorvertoningsmodus.

Als u zowel de CSS-tekenreeks als de stijltekenreeks in code opgeeft, heeft de CSS-klasse voorrang op de stijltekenreeks en kan deze alle configuratiewijzigingen overschrijven die de stijltekenreeks aanbrengt.

## Woordenboeken toevoegen voor de spellingcontrole {#adddict}

Wanneer de insteekmodule voor spellingcontrole is geactiveerd, gebruikt de RTE woordenboeken voor elke geschikte taal. Deze worden vervolgens geselecteerd volgens de taal van de website door de eigenschap language van de substructuur te gebruiken of de taal uit de URL te halen. De `/en/` -vertakking wordt bijvoorbeeld als Engels gecontroleerd, de `/de/` -vertakking als Duits.

>[!NOTE]
>
>Het bericht `Spell checking failed` wordt weergegeven als wordt geprobeerd een taal te controleren die niet is geïnstalleerd. De standaardwoordenboeken staan op `/libs/cq/spellchecker/dictionaries`, samen met de juiste leesmij-bestanden. Wijzig de bestanden niet.

Een standaard AEM installatie omvat de woordenboeken voor Amerikaans Engels (`en_us`) en Brits Engels (`en_gb`). Voer de volgende stappen uit om meer woordenboeken toe te voegen.

1. Navigeer aan de pagina [ https://extensions.openoffice.org/ ](https://extensions.openoffice.org/).

1. Ga op een van de volgende manieren te werk om een woordenboek te zoeken waarin u uw taal kunt kiezen:

   * Zoek naar woordenboek van uw taalkeuze. Zoek op de woordenboekpagina de koppeling naar de oorspronkelijke bron of de oorspronkelijke webpagina van de auteur. Zoek de woordenboekbestanden voor v2.x op een dergelijke pagina.
   * Onderzoek naar v2.x woordenboekdossiers in [ https://wiki.openoffice.org/wiki/User:Khirano/Dictionaries ](https://wiki.openoffice.org/wiki/User:Khirano/Dictionaries).

1. Download het archief met de spellingdefinities. Extraheer de inhoud van het archief op uw bestandssysteem.

   >[!CAUTION]
   >
   >Alleen woordenboeken in de `MySpell` -indeling voor OpenOffice.org v2.0.1 of eerder worden ondersteund. Aangezien de woordenboeken nu archiefbestanden zijn, wordt u aangeraden het archief na het downloaden te verifiëren.

1. Zoek de bestanden `.aff` en `.dic` . Bestandsnaam in kleine letters behouden. Bijvoorbeeld `de_de.aff` en `de_de.dic` .
1. Laad de `.aff` - en `.dic` -bestanden in de opslagplaats op `/apps/cq/spellchecker/dictionaries` .

>[!NOTE]
>
>De spellingcontrole van RTE is beschikbaar op bestelling. Deze wordt niet automatisch uitgevoerd wanneer u tekst gaat typen. Klik op [!UICONTROL Spellchecker] op de werkbalk om de spellingcontrole uit te voeren. RTE controleert de spelling van woorden en benadrukt de verkeerd gespelde woorden.
>
>Als u een wijziging opneemt die door de spellingcontrole wordt voorgesteld, wordt de status van de tekst gewijzigd en worden onjuist gespelde woorden niet langer gemarkeerd. Klik nogmaals op de knop Spellingcontrole om de spellingcontrole uit te voeren.

## De historiegrootte voor acties voor ongedaan maken en opnieuw uitvoeren configureren {#undohistory}

Met RTE kunnen auteurs enkele laatste bewerkingen ongedaan maken of opnieuw uitvoeren. Standaard worden 50 bewerkingen opgeslagen in de geschiedenis. U kunt deze waarde naar wens configureren.

1. Navigeer binnen uw component naar het knooppunt `<rtePlugins-node>/undo` . Maak deze knooppunten als deze niet bestaan. Voor meer details, zie [ een elektrisch toestel ](#activateplugin) activeren.
1. Maak de eigenschap op het knooppunt `undo` :

   * **Naam** `maxUndoSteps`
   * **Type** `Long`
   * **Waarde** het aantal ongedaan maakt stappen u in de geschiedenis wilt bewaren. De standaardwaarde is 50. Gebruik `0` om ongedaan te maken/opnieuw uit te voeren.

1. Sla de wijzigingen op.

## De tabgrootte configureren {#tabsize}

Wanneer het tabteken wordt ingedrukt binnen tekst, wordt een vooraf gedefinieerd aantal spaties ingevoegd. Standaard is dit drie vaste spaties en één spatie.

De tabgrootte definiëren:

1. Navigeer in uw component naar het knooppunt `<rtePlugins-node>/keys` . Maak de knooppunten als deze niet bestaan. Voor meer details, zie [ een elektrisch toestel ](#activateplugin) activeren.
1. Maak de eigenschap op het knooppunt `keys` :

   * **Naam** `tabSize`
   * **Type** `String`
   * **Waarde** het aantal ruimtekarakters dat voor de tabulator moet worden gebruikt

1. Sla de wijzigingen op.

## Inspringingsmarge instellen {#indentmargin}

Wanneer inspringing is ingeschakeld (standaard), kunt u de grootte van de inspringing definiëren:

>[!NOTE]
>
>Deze inspringingsgrootte wordt alleen toegepast op alinea&#39;s (blokken tekst), maar heeft geen invloed op de inspringing van feitelijke lijsten.

1. Navigeer binnen uw component naar het knooppunt `<rtePlugins-node>/lists` . Maak deze knooppunten als deze niet bestaan. Voor meer details, zie [ een elektrisch toestel ](#activateplugin) activeren.
1. Maak in het knooppunt `lists` de parameter `indentSize` :

   * **Naam**: `indentSize`
   * **Type**: `Long`
   * **Waarde**: aantal pixel die voor de paragraafmarge worden vereist.

## De hoogte van bewerkbare ruimte configureren {#editablespace}

>[!NOTE]
>
>Dit is alleen van toepassing wanneer u de RTE gebruikt in een dialoogvenster (niet tijdens het bewerken op locatie in een klassieke UI).

U kunt de hoogte van de bewerkbare ruimte definiëren die in het dialoogvenster van de component wordt weergegeven:

1. Maak een eigenschap op het knooppunt `../items/text` in de dialoogdefinitie voor de component:

   * **Naam** `height`
   * **Type** `Long`
   * **Waarde** de hoogte van geeft canvas in pixel uit.

   >[!NOTE]
   >
   >Hiermee wijzigt u de hoogte van het dialoogvenster niet.

1. Sla de wijzigingen op.

## Stijlen en protocollen voor koppelingen configureren {#linkstyles}

Bij het toevoegen van koppelingen in AEM kunt u het volgende definiëren:

* De CSS-stijlen die moeten worden gebruikt
* De automatisch aanvaarde protocollen

Om te vormen hoe de verbindingen in AEM van een ander programma worden toegevoegd, bepaal de regels van de HTML.

1. Zoek met CRXDE Lite de tekstcomponent voor uw project.
1. Maak een knooppunt op hetzelfde niveau als `<rtePlugins-node>` , dat wil zeggen: maak het knooppunt onder het bovenliggende knooppunt van `<rtePlugins-node>` :

   * **Naam** `htmlRules`
   * **Type** `nt:unstructured`

   >[!NOTE]
   >
   >Het knooppunt `../items/text` heeft de eigenschap:
   >
   >* **Naam** `xtype`
   >* **Type** `String`
   >* **Waarde** `richtext`
   >
   >De locatie van het knooppunt `../items/text` kan variëren, afhankelijk van de structuur van het dialoogvenster. Twee voorbeelden zijn `/apps/myProject>/components/text/dialog/items/text` en `/apps/<myProject>/components/text/dialog/items/panel/items/text` .

1. Maak onder `htmlRules` een knooppunt.

   * **Naam** `links`
   * **Type** `nt:unstructured`

1. Definieer onder het knooppunt `links` de vereiste eigenschappen:

   * CSS-stijl voor interne koppelingen:

      * **Naam** `cssInternal`
      * **Type** `String`
      * **Waarde** de naam van de CSS klasse (zonder het voorafgaande &quot;.&quot;; bijvoorbeeld `cssClass` in plaats van `.cssClass` )

   * CSS-stijl voor externe koppelingen

      * **Naam** `cssExternal`
      * **Type** `String`
      * **Waarde** de naam van de CSS klasse (zonder het voorafgaande &quot;.&quot;; bijvoorbeeld `cssClass` in plaats van `.cssClass` )

   * Serie van geldige **protocollen**. De ondersteunde protocollen zijn `http://` , `https://` , `file://` en `mailto:` .

      * **Naam** `protocols`
      * **Type** `String[]`
      * **Waarde**, of meer, protocollen

   * **defaultProtocol** (bezit van type **Koord**): Protocol dat moet worden gebruikt als de gebruiker niet uitdrukkelijk één specificeerde.

      * **Naam** `defaultProtocol`
      * **Type** `String`
      * **Waarde**, of meer, standaardprotocollen

   * Definitie van hoe te om het doelattribuut van een verbinding te behandelen. Een knooppunt maken:

      * **Naam** `targetConfig`
      * **Type** `nt:unstructured`

     Definieer in het knooppunt `targetConfig` de vereiste eigenschappen:

      * Geef de doelmodus op:

         * **Naam** `mode`
         * **Type** `String`
         * **Waarde**

            * `auto`: betekent dat een automatisch doel wordt gekozen

              (opgegeven door de eigenschap `targetExternal` voor externe koppelingen of `targetInternal` voor interne koppelingen).

            * `manual`: niet van toepassing in deze context
            * `blank`: niet van toepassing in deze context

      * Het doel voor interne koppelingen:

         * **Naam** `targetInternal`
         * **Type** `String`
         * **Waarde** het doel voor interne verbindingen (slechts gebruik wanneer de wijze `auto` is)

      * Het doel voor externe koppelingen:

         * **Naam** `targetExternal`
         * **Type** `String`
         * **Waarde** het doel voor externe verbindingen (slechts gebruikt wanneer de wijze `auto` is).

1. Sla alle wijzigingen op.
