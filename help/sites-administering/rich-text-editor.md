---
title: Configureer de Rich Text Editor voor het schrijven van inhoud in Adobe Experience Manager.
description: Leer hoe u de Adobe Experience Manager Rich Text Editor configureert voor het schrijven van inhoud in Adobe Experience Manager.
contentOwner: AG
exl-id: 2e7ec22f-0856-44c4-bb15-1086dae0b85a
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2887'
ht-degree: 0%

---

# De Rich Text Editor configureren {#configure-the-rich-text-editor}

De Rich Text Editor (RTE) biedt auteurs een groot aantal functies voor het bewerken van hun tekstinhoud. Pictogrammen, selectiekaders, werkbalk en menu&#39;s zijn beschikbaar voor een WYSIWYG-ervaring bij het bewerken van tekst.

Om te weten hoe te om eigenschappen RTE voor creatie te gebruiken, zie [Rich Text Editor gebruiken voor ontwerpen](/help/sites-authoring/rich-text-editor.md). RTE kan worden gevormd om, de eigenschappen toe te laten onbruikbaar te maken en uit te breiden beschikbaar in de auteurscomponenten. Het volgende werkschema illustreert een geadviseerde orde om de de configuratietaken van RTE in Experience Manager te voltooien.

![Reeks stappen leren hoe te om RTE te vormen](assets/rte_workflow_v1.png)

*Figuur: Reeks stappen leren hoe te om RTE te vormen*

## Interface met aanraakbediening en klassieke gebruikersinterface {#understand-touch-enabled-ui-and-classic-ui}

De interface met aanraakbediening is de standaardgebruikersinterface voor Experience Managers. Adobe introduceerde Touch-interface met [responsief ontwerp](/help/sites-authoring/responsive-layout.md) voor de ontwerpomgeving. De interface voor touch-apparaten is ontworpen voor touch- en desktopapparaten. De interface verschilt aanzienlijk van de oorspronkelijke klassieke UI.

![De rijke toolbar van de Redacteur van de Tekst in Aanraaks gebruikersinterface](assets/chlimage_1-35.png)

*Afbeelding: Rich Text Editor-werkbalk in Touch-interface*

![De Rich Text Editor-werkbalk in de klassieke gebruikersinterface](assets/rtedefault.png)

*Afbeelding: Rich Text Editor-werkbalk in klassieke gebruikersinterface*

>[!MORELIKETHIS]
>
>* [UI-aanbevelingen](/help/sites-deploying/ui-recommendations.md)
>* Informatie over het vervangen van de klassieke gebruikersinterface vindt u in [Opmerkingen bij de release Experience Manager 6.5](/help/release-notes/deprecated-removed-features.md)
>* Voor verschil tussen UIs, zie [Aanraakinterface en klassieke gebruikersinterface](https://aemcq5pedia.wordpress.com/2018/01/05/touch-enabled-ui-aem6-3/)
>* Als u de interface met aanraakbediening gedetailleerd wilt begrijpen, raadpleegt u [Concepten van Experience Manager Touch UI](/help/sites-developing/touch-ui-concepts.md)

## Verschillende bewerkingsmodi {#editingmodes}

Auteurs kunnen tekstinhoud in Experience Manager maken en bewerken met de verschillende modi van componenten. De toolbaropties voor het ontwerpen en het formatteren van inhoud en de gebruikerservaring van rte-toegelaten componenten op verschillende het uitgeven wijze variëren gebaseerd op configuraties RTE.

| Bewerkmodus | Bewerkingsgebied | Aanbevolen functies om te worden ingeschakeld | Aanraakinterface | Klassieke interface |
|--- |--- |--- |--- |--- |
| Inline | Lokaal bewerken voor snelle, kleine bewerkingen; opmaken zonder dialoogvenster te openen | Minimale RTE-functies | Y | Y |
| RTE volledig scherm | Behandelt gehele pagina | Alle vereiste eigenschappen van RTE | Y | N |
| Dialoog | Dialoogvenster boven op de pagina-inhoud, maar heeft geen betrekking op de gehele pagina | Alle vereiste eigenschappen van RTE in Klassieke UI; laat oordeelkundig eigenschappen in Touch UI toe | Y | Y |
| Dialoogvenster volledig scherm | Hetzelfde als de modus Volledig scherm; bevat velden van het dialoogvenster naast RTE | Alle vereiste eigenschappen van RTE | Y | N |

>[!NOTE]
>
>De functie voor het bewerken van bronnen is niet beschikbaar in de inline bewerkingsmodus van de interface met aanraakbediening. U kunt afbeeldingen niet naar het volledige scherm slepen. Alle andere functies werken in alle modi.

### Inline bewerken {#inline-editing}

Als u de inhoud opent (met een langzaam dubbelklikken), kan deze op de pagina worden bewerkt. Er wordt een compacte werkbalk weergegeven met zeer basisopties.

![Inline bewerken met de standaardwerkbalk in Touch-gebruikersinterface](assets/chlimage_1-36.png)

*Afbeelding: Inline bewerken met standaardwerkbalk in Touch-gebruikersinterface*

In de klassieke gebruikersinterface kunt u langzaam dubbelklikken op de component om inline te bewerken en wordt de inhoud gemarkeerd met een oranje omtrek. Als de Inhoudszoeker is geopend, wordt boven in het venster een werkbalk weergegeven met de beschikbare RTE-opmaakopties. Als de Inhoudszoeker niet is geopend, worden de opmaakopties niet weergegeven en kunt u alleen standaardtekstbewerkingen uitvoeren.

### Volledig scherm bewerken {#full-screen-editing}

Componenten van Experience Managers kunnen worden geopend in de weergave Volledig scherm, waarin de pagina-inhoud wordt verborgen en het beschikbare scherm wordt ingenomen. U kunt overwegen om een gedetailleerde versie van de inlinebewerking op volledig scherm te bewerken, aangezien deze de meeste bewerkingsopties biedt. U kunt het openen door op ![rte_fullscreen](assets/rte_fullscreen.png)op de compacte werkbalk als u de inline bewerkingsmodus gebruikt.

In de modus Volledig scherm van het dialoogvenster zijn, samen met een gedetailleerde RTE-werkbalk, ook de opties en componenten beschikbaar in een dialoogvenster. Het is alleen van toepassing voor een dialoog die naast andere componenten RTE bevat.

![De gedetailleerde RTE-werkbalk wanneer u bewerkingen uitvoert in de modus Volledig scherm in de gebruikersinterface met aanraakbediening](assets/chlimage_1-37.png)

*Afbeelding: De gedetailleerde RTE-werkbalk wanneer u bewerkingen uitvoert in de modus Volledig scherm in de interface met aanraakbediening*

### Dialoogvenster bewerken {#dialog-editing}

Wanneer dubbelgeklikt wordt op een component, wordt een dialoogvenster geopend voor het bewerken van de inhoud. Het dialoogvenster wordt boven op de bestaande pagina geopend. In sommige specifieke scenario&#39;s, opent de dialoog als pop-up venster. Wanneer een tekstcomponent bijvoorbeeld deel uitmaakt van een kolom in een paginalay-out met meerdere kolommen en het gebied dat beschikbaar is voor het dialoogvenster kleiner is.

![Dialoogbewerkingsmodus in interface met aanraakbediening](assets/dialog_editing_modetouchui.png)

*Afbeelding: Dialoogbewerkingsmodus in interface met aanraakbediening*

![Dialoogvenster in klassieke gebruikersinterface met gedetailleerde werkbalk voor bewerken](assets/chlimage_1-38.png)

*Afbeelding: Dialoogvenster in klassieke gebruikersinterface met gedetailleerde werkbalk voor bewerken*

## Informatie over RTE-plug-ins en de bijbehorende functies {#aboutplugins}

De functionaliteit wordt beschikbaar gesteld via een reeks plug-ins, elk met:

* A `features` eigenschap:

   * Wordt gebruikt om de basisfunctionaliteit van die plug-in te activeren of te deactiveren
   * Dat kan worden gevormd gebruikend een gestandaardiseerde procedure

* Indien van toepassing, extra eigenschappen en opties die gespecialiseerde configuratie vereisen.

De basisfuncties van de RTE worden geactiveerd of gedeactiveerd door de waarde van de `features` eigenschap op een knooppunt dat specifiek is voor de juiste insteekmodule.

In de volgende tabel worden de huidige plug-ins weergegeven:

* Plug-in-id&#39;s met een koppeling naar de API-documentatie. ID wordt gebruikt als knooppuntnaam wanneer [een plug-in activeren](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin).
* Toegestane waarden voor de `features` eigenschap.
* Een beschrijving van de functionaliteit die door de plug-in wordt geboden.

| Plug-in-id | functies | Beschrijving |
|--- |--- |--- |
| bewerken | cut copy paste-default paste-plaintext paste-wordhtml | [De drie plakmodi knippen, kopiëren en](/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles). |
| findreplace | zoeken, vervangen | Zoeken en vervangen. |
| format | vet cursief onderstrepen | [Basistekstopmaak](/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles). |
| image | image | Basisondersteuning voor afbeeldingen (slepen vanuit de inhoud of de Finder). Afhankelijk van de browser heeft de ondersteuning verschillende gedragingen voor auteurs |
| toetsen |  | Zie voor het definiëren van deze waarde [tabgrootte](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tabsize). |
| uitvullen | uitvullen, links uitvullen, rechts uitvullen | Alinea-uitlijning. |
| koppelingen | ontkoppelingsanker wijzigen | [Hyperlinks en ankers](/help/sites-administering/configure-rich-text-editor-plug-ins.md#linkstyles). |
| lijsten | geordende ongeordende inspringing uitspringen | Deze insteekmodule bestuurt beide [inspringing en lijsten](/help/sites-administering/configure-rich-text-editor-plug-ins.md#indentmargin); inclusief geneste lijsten. |
| misverstanden | specialchars-bronbewerking | Met diverse gereedschappen kunnen auteurs toegang krijgen tot [speciale tekens](/help/sites-administering/configure-rich-text-editor-plug-ins.md#spchar) of bewerk de HTML-bron. U kunt ook een geheel toevoegen [bereik van speciale tekens](/help/sites-administering/configure-rich-text-editor-plug-ins.md#definerangechar) als u uw eigen lijst wilt bepalen. |
| Paraformat | paraformat | De standaardindelingen voor alinea&#39;s zijn Alinea, Kop 1, Kop 2 en Kop 3 (`<p>`, `<h1>`, `<h2>`, en `<h3>`). U kunt [meer alinea-indelingen toevoegen](/help/sites-administering/configure-rich-text-editor-plug-ins.md#paraformats) of breid de lijst uit. |
| spelling | checktext | [Spellingcontrole taalbewust](/help/sites-administering/configure-rich-text-editor-plug-ins.md#adddict). |
| stijlen | stijlen | Ondersteuning voor opmaak met behulp van een CSS-klasse. [Nieuwe tekststijlen toevoegen](/help/sites-administering/configure-rich-text-editor-plug-ins.md#textstyles) als u uw eigen reeks stijlen wilt toevoegen (of uitbreiden) voor gebruik met tekst. |
| subsuperscript | subscript, superscript | Extensies voor de basisindelingen, subscript en superscript toevoegen. |
| table | verwijderbaar inzetbare verwijderbare insteekmodule removerow insert column removecolumn cellprops mergecells splitcell selectrow selected columns | Zie [tabelstijlen configureren](/help/sites-administering/configure-rich-text-editor-plug-ins.md#tablestyles), als u uw eigen stijlen voor of volledige lijsten of individuele cellen wilt toevoegen. |
| ongedaan maken | ongedaan maken, opnieuw uitvoeren | Grootte historie van [ongedaan maken en opnieuw uitvoeren](/help/sites-administering/configure-rich-text-editor-plug-ins.md#undohistory) bewerkingen. |

>[!NOTE]
>
>De plug-in Volledig scherm wordt niet ondersteund in de dialoogmodus. Gebruik van de `dialogFullScreen` instellen om de werkbalk voor de modus Volledig scherm te configureren.

## Begrijp de configuratiewegen en plaatsen {#understand-the-configuration-paths-and-locations}

De [wijze van het uitgeven van RTE (en UI)](#editingmodes) die u voor uw auteurs verstrekt bepaalt de plaats voor de configuratiedetails wanneer u [het activeren van de stop-ins van RTE](/help/sites-administering/configure-rich-text-editor-plug-ins.md#activateplugin):

| Bewerkmodus | Locatie voor aanraakinterface | Locatie voor klassieke gebruikersinterface |
|---|---|---|
| Inline | `cq:editConfig/cq:inplaceEditing` | `cq:editConfig/cq:inplaceEditing` |
| Volledig scherm | `cq:editConfig/cq:inplaceEditing` | Niet van toepassing |
| Dialoog | `cq:dialog` | `dialog` |
| Dialoogvenster Volledig scherm | `cq:dialog` | Niet van toepassing |

>[!NOTE]
>
>Geef het knooppunt onder geen naam `cq:inplaceEditing` als `config`. Aan `cq:inplaceEditing` node, definieert u de volgende eigenschappen:
>* **Naam**: `configPath`
>* **Type**: `String`
>* **Waarde**: pad van het knooppunt met de werkelijke configuratie
>
>Noem niet de knoop van de configuratie RTE als `config`. Anders, worden de configuraties RTE van kracht voor slechts de beheerders en niet voor de gebruikers in de groep `content-author`.

Configureer de volgende eigenschappen die alleen van toepassing zijn in de bewerkingsmodus Dialoogvenster in Touch UI:

* `useFixedInlineToolbar`: Stel deze Booleaanse eigenschap in die op de RTE-node is gedefinieerd (één met sling:resourceType= `cq/gui/components/authoring/dialog/richtext`) naar `True`om de RTE-werkbalk vast te maken in plaats van zwevend.

  Wanneer deze eigenschap true is, wordt het bewerken van Richtingstekst standaard gestart op de gebeurtenis &quot;foundation-contentloaded&quot;.

  Als u dit wilt voorkomen, stelt u de eigenschap in `customStart` tot `True`en activeer de gebeurtenis &#39;rte-start&#39; om RTE-bewerking te starten. Wanneer deze eigenschap &#39;true&#39; is, werkt het standaardgedrag bij klikken met de beginwaarde niet.

* `customStart`: Stel deze Booleaanse eigenschap die op het RTE-knooppunt is gedefinieerd in op `True`, om te controleren wanneer om RTE te beginnen door de gebeurtenis in werking te stellen `rte-start`.

* `rte-start`: activeer deze gebeurtenis op de `contenteditable-div` van RTE, wanneer beginnen RTE uit te geven. Dit werkt alleen als `customStart` is ingesteld op true.

Wanneer RTE wordt gebruikt in de aanraking-toegelaten dialoog, plaatsend het bezit `useFixedInlineToolbar` naar waar is verplicht om problemen te voorkomen .

## Op plaats bewerken aanpassen {#customizing-in-place-editing}

U kunt definiëren op welke HTML-kiezer de teksteditor begint door de volgende eigenschappen te configureren:

* **`editElementQuery`** - Gedefinieerd op `cq:InplaceEditingConfig`, wordt deze eigenschap gebruikt om een kiezer op te geven van het element HTML waarop de inline-bewerking voor de tekstcomponent wordt gestart. Als u deze optie niet opgeeft, wordt het inline bewerken direct gestart op de HTML van de tekstcomponent.
* **`textPropertyName`** - Gedefinieerd op `cq:InplaceEditingConfig`, wordt deze eigenschap gebruikt om de naam op te geven van de eigenschap die wordt opgeslagen op het inhoudsknooppunt waar de HTML-waarde van de tekstcomponent na inline-bewerking wordt voortgezet.

De overeenkomende eigenschap voor de dialoogmodus is `name`.

## RTE-functies inschakelen door plug-ins te activeren {#enable-rte-functionalities-by-activating-plug-ins}

De functionaliteit van RTE wordt beschikbaar gemaakt via een reeks stop-ins, elk met eigenschappen bezit. U kunt de eigenschap features configureren om de verschillende functies van elke insteekmodule in of uit te schakelen.

Voor gedetailleerde configuraties van de stop-ins van RTE, zie [hoe te om de stop van RTE te activeren en te vormen](/help/sites-administering/configure-rich-text-editor-plug-ins.md).

**Monster**: Downloaden [deze voorbeeldconfiguratie](/help/sites-administering/assets/rte-sample-all-features-enabled-10.zip) dat illustreert hoe te om RTE te vormen. In dit pakket zijn alle functies ingeschakeld.

>[!NOTE]
>
>De [Tekstcomponent Core Components](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/components/text.html#the-text-component-and-the-rich-text-editor) staat malplaatjeredacteurs toe om vele steekmodules van RTE in GUI als inhoudsbeleid te vormen, die de behoefte aan technische configuratie elimineren. Het inhoudsbeleid kan werken met RTE UI-configuraties, zoals in dit document wordt beschreven.
>
>Zie de klasse [De montages van de UI van RTE en inhoudsbeleid](/help/sites-administering/rich-text-editor.md) van dit document en [Paginasjablonen maken](/help/sites-authoring/templates.md) en de [Documentatie voor ontwikkelaars van kerncomponenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/developing.html).

>[!NOTE]
>
>Ter referentie kunt u de standaardtekstcomponenten (geleverd als onderdeel van een standaardinstallatie) vinden op:
>
>* `/libs/wcm/foundation/components/text`
>* `/libs/foundation/components/text`
>
>Als u uw eigen tekstcomponent wilt maken, kopieert u de bovenstaande component in plaats van deze componenten te bewerken.

## RTE-werkbalk configureren {#dialogfullscreen}

Met AEM kunt u de interface voor de Rich Text Editor op een andere manier configureren voor de verschillende bewerkingsmodi. De standaardinstellingen worden hieronder gegeven. U kunt deze standaardinstellingen op basis van uw vereisten overschrijven. U kunt alleen de werkbalkfuncties aanpassen die u aan de auteurs wilt geven. U hoeft niet alle werkbalkconfiguraties op te geven.

De werkbalk configureren voor `dialogFullScreen`en gebruikt u de volgende voorbeeldconfiguratie.

```java
<uiSettings jcr:primaryType="nt:unstructured">
  <cui jcr:primaryType="nt:unstructured">
    <inline
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,#justify,#lists,links#modifylink,links#unlink,#paraformat]">
      <popovers jcr:primaryType="nt:unstructured">
        <justify
          jcr:primaryType="nt:unstructured"
          items="[justify#justifyleft,justify#justifycenter,justify#justifyright,justify#justifyjustify]"
          ref="justify"/>
        <lists
          jcr:primaryType="nt:unstructured"
          items="[lists#unordered,lists#ordered,lists#outdent,lists#indent]"
          ref="lists"/>
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </inline>
    <dialogFullScreen
      jcr:primaryType="nt:unstructured"
      toolbar="[format#bold,format#italic,format#underline,justify#justifyleft,justify#justifycenter,justify#justifyright,justify#justifyjustify,lists#unordered,lists#ordered,lists#outdent,lists#indent,links#modifylink,links#unlink,table#createoredit,#paraformat,image#imageProps]">
      <popovers jcr:primaryType="nt:unstructured">
        <paraformat
          jcr:primaryType="nt:unstructured"
          items="paraformat:getFormats:paraformat-pulldown"
          ref="paraformat"/>
      </popovers>
    </dialogFullScreen>
    <tableEditOptions
      jcr:primaryType="nt:unstructured"
      toolbar="[table#insertcolumn-before,table#insertcolumn-after,table#removecolumn,-,table#insertrow-before,table#insertrow-after,table#removerow,-,table#mergecells-right,table#mergecells-down,table#mergecells,table#splitcell-horizontal,table#splitcell-vertical,-,table#selectrow,table#selectcolumn,-,table#ensureparagraph,-,table#modifytableandcell,table#removetable,-,undo#undo,undo#redo,-,table#exitTableEditing,-]">
    </tableEditOptions>
  </cui>
</uiSettings>
```

Er worden verschillende UI-instellingen gebruikt voor de inlinemodus en de modus Volledig scherm. De eigenschap toolbar wordt gebruikt om de knoppen van de werkbalk op te geven.

Als de knop zelf bijvoorbeeld een functie is (bijvoorbeeld `Bold`), wordt het opgegeven als `PluginName#FeatureName` (bijvoorbeeld `links#modifylink`).

Als de knop een pop-up is (met enkele functies van een plug-in), wordt deze opgegeven als `#PluginName` (bijvoorbeeld `#format`).

Scheidingstekens (`|`) tussen een groep knoppen kan worden opgegeven met `-`.

Het pop-upknooppunt onder de modus Inline of Volledig scherm bevat een lijst met de popovers die worden gebruikt. Elk onderliggend knooppunt onder het knooppunt &#39;popovers&#39; krijgt een naam na de insteekmodule (bijvoorbeeld de indeling). Deze heeft een eigenschap &#39;items&#39; die een lijst bevat met functies van de plug-in (bijvoorbeeld format#bold).

## RTE-gebruikersinterface-instellingen en inhoudsbeleid {#rtecontentpolicies}

De beheerders kunnen de opties controleren RTE gebruikend inhoudsbeleid, zeggen in plaats van de configuratie zoals hierboven beschreven. In het inhoudsbeleid worden de ontwerpeigenschappen van een component gedefinieerd wanneer deze als onderdeel van een component worden gebruikt [bewerkbare sjabloon](/help/sites-authoring/templates.md). Als bijvoorbeeld een tekstcomponent die de RTE gebruikt wordt gebruikt met een bewerkbare sjabloon, kan het inhoudsbeleid definiëren dat de optie Vet beschikbaar is en zijn enkele opties voor alineaopmaak beschikbaar. Het inhoudsbeleid is herbruikbaar en kan op meerdere sjablonen worden toegepast.

De beschikbare opties in RTE stromen stroomafwaarts van de configuraties van het gebruikersinterface aan het inhoudsbeleid.

* De de configuratiemontages van de gebruikersinterface bepalen welke opties aan het inhoudsbeleid beschikbaar zijn.
* Als de gebruikersinterfaceconfiguratie van RTE verwijderde of geen punt toelaat, kan het inhoudsbeleid niet het vormen.
* Een auteur heeft toegang tot slechts dergelijke functionaliteit die door de gebruikersinterfaceconfiguraties en het inhoudsbeleid ter beschikking wordt gesteld.

Als voorbeeld kunt u de [Documentatie van de component Text Core](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/text.html#the-text-component-and-the-rich-text-editor).

## Toewijzing aanpassen tussen werkbalkpictogrammen en -opdrachten {#iconstoolbar}

U kunt de afbeelding aanpassen tussen de koraalpictogrammen die worden weergegeven op de RTE-werkbalk en de beschikbare opdrachten. U kunt geen andere pictogrammen gebruiken behalve Koraalpictogrammen.

1. Een knooppunt maken met de naam `icons` krachtens `uiSettings/cui`.

1. Maak knooppunten voor afzonderlijke pictogrammen eronder.
1. Geef voor elk van de afzonderlijke pictogramknooppunten een koraalpictogram en een opdracht op om aan het pictogram toe te wijzen.

Hieronder ziet u een voorbeeldfragment waarmee u de opdracht Vet maken toewijst aan het pictogram Koraal met de naam `textItalic`.

```java
<text jcr:primaryType="nt:unstructured" sling:resourceType="cq/gui/components/authoring/dialog/richtext" name="./text" useFixedInlineToolbar="{Boolean}true">
    <rtePlugins jcr:primaryType="nt:unstructured">
        <format jcr:primaryType="nt:unstructured" features="bold,italic"/>
    </rtePlugins>
    <uiSettings jcr:primaryType="nt:unstructured">
        <cui jcr:primaryType="nt:unstructured">
            <inline jcr:primaryType="nt:unstructured"
                toolbar="[format#bold,format#italic,format#underline,links#modifylink,links#unlink]">
            </inline>
            <icons jcr:primaryType="nt:unstructured">
                <bold jcr:primaryType="nt:unstructured"
                    command="format#bold"
                    icon="textItalic"/>
            </icons>
        </cui>
    </uiSettings>
</text>
```

## Overschakelen naar de KoralUI 2 Rich Text Editor {#switch-to-coralui-rich-text-editor}

Voor een pagina, kunt u of CoralUI 2 KTE clientlib of CoralUI 3 KTE clientlib omvatten. Standaard bevat de Rich Text Editor de CoralUI 3 RTE clientlib. Ga als volgt te werk om over te schakelen op CoralUI 2 RTE.

>[!NOTE]
>
>Adobe beveelt dit niet aan als beste praktijk. Schakel als laatste redmiddel over naar CoralUI 2 RTE. Aangepaste plug-ins voor CoralUI 2 RTE werken met CoralUI 3 RTE als de plug-ins niet afhankelijk zijn van interne RTE-bronnen, zoals klassen.
>
>Als u aangepaste plug-ins gebruikt voor CoralUI3 RTE, gebruikt u `rte.coralui3` bibliotheek.


1. Het knooppunt bedekken `/libs/cq/gui/components/authoring/editors/clientlibs/core` krachtens `/apps`en voer de volgende handelingen uit:

   * Vervangen `rte.coralui3` with `rte.coralui2` voor het gebiedsdeelbezit.
   * Vervangen `cq.authoring.editor.core.inlineediting.rte.coralui3` with `cq.authoring.editor.core.inlineediting.rte.coralui2` voor de eigenschap embed.
   * Vervangen `cq.authoring.rte.coralui3` with `cq.authoring.rte.coralui2` voor de eigenschap embed.

1. De knooppunten bedekken `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` en `/libs/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2` krachtens `/apps`.

   Categorie verwijderen `cq.authoring.dialog` van `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui3` en voeg deze toe aan `/apps/cq/gui/components/authoring/dialog/richtext/clientlibs/rte/coralui2`.

1. Wijzig een andere afhankelijkheid die op de pagina wordt opgenomen vanuit `rte.coralui3` tot `rte.coralui2`. Bijvoorbeeld na het bedekken van het knooppunt `/libs/mcm/campaign/components/touch-ui/clientlibs/rte` krachtens `/apps`, wijzigt u de afhankelijkheid ervan `rte.coralui3` tot `rte.coralui2`.

1. Het knooppunt bedekken `cq/ui/widgets` krachtens `/apps`. De afhankelijkheid vervangen `cq.rte` op het knooppunt `/apps/cq/ui/widgets` with `cq.coralui2.rte`.

>[!NOTE]
>
>CoralUI 2 RTE gebruikt handlebars malplaatjes voor stop-in dialogen. Daarom had CoralUI 2 RTE clientlib een afhankelijkheid van handlebars clientlib. CoralUI 3 RTE gebruikt geen zakbalkmalplaatjes en heeft geen bijbehorende gebiedsdeel. Als uw aangepaste plug-ins handbalksjablonen gebruiken, neemt u de client lib-handgrepen op uw webpagina.

## Aanvullende informatie {#further-information}

Voor meer informatie over het vormen van RTE, zie [Widget-API AEM](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.RichText) referentie.

Met name om de beschikbare plug-ins en bijbehorende opties te zien:

* De [CQ.form.RichText](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.RichText) verstrekt een vormgebied voor het uitgeven van gestileerde tekstinformatie (rijke teksten). Zie Configuratieopties voor meer informatie over alle parameters die beschikbaar zijn voor het RTF-formulier.
* De component RichText verstrekt een brede waaier van functionaliteit gebruikend stop-ins die onder worden vermeld [CQ.form.rate.plugins.Plugin](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html?class=CQ.form.rte.plugins.Plugin). Voor elke insteekmodule:

   * zie de Eigenschappen voor details van functionaliteit die kan worden toegelaten (of worden onbruikbaar gemaakt)
   * Zie de Opties Config voor alle parameters beschikbaar voor gedetailleerde configuratie van de aangewezen stop - binnen

* Meer informatie over de Regels van de HTML voor verbindingen is ook beschikbaar.

Deze kunnen worden gebruikt om uw eigen RTE uit te breiden en aan te passen. Als u bijvoorbeeld de ankers wilt weergeven die beschikbaar zijn op de pagina wanneer u een koppeling maakt, kunt u uw eigen implementatie van de `LinkPlugin`.

## Bekende beperkingen {#known-limitations}

AEM het vermogen van RTE heeft de volgende beperkingen:

* De mogelijkheden van RTE worden gesteund slechts in AEM componentendialogen. RTE wordt niet gesteund op wizards of Stichting-vormen als [Pagina-eigenschappen](/help/sites-developing/page-properties-views.md) en [Basisstructuur](/help/sites-authoring/scaffolding.md) op interface met aanraakbediening.

* AEM werkt niet aan [Hybride apparaten](/help/release-notes/release-notes.md).

* Noem niet de knoop van de configuratie RTE `config`. Anders, treedt de configuratie RTE voor slechts de beheerders en niet voor de gebruikers in de groep van kracht `content-author`.

* RTE biedt geen ondersteuning voor inlineframe of iframe voor het insluiten van inhoud.

## Tips en trucs {#best-practices-and-tips}

* Schakel alleen de plug-ins zonder pop-up in voor een zwevend dialoogvenster. Plug-ins zonder pop-up zijn kleiner en zijn het meest geschikt voor een zwevend dialoogvenster.
* De plug-ins met grotere pop-ups inschakelen, zoals de `Paste` alleen in de modus Volledig scherm of in de modus Volledig scherm. Plug-ins met een grote pop-up hebben meer ruimte in het scherm nodig voor een goede ontwerpervaring.
* Als u aangepaste plug-ins gebruikt voor CoralUI3 RTE, gebruikt u `rte.coralui3` bibliotheek.

## Veelvoorkomende problemen met RTE oplossen {#troubleshoot-issues-with-aem-rich-text-editor}

**Meerdere tabelcellen selecteren?**

Als u meerdere cellen in een tabel wilt selecteren, drukt u op `Ctrl` of `Cmd` en klik vervolgens één voor één op de tabelcellen.

Voer nu een bewerking uit op de selectie en stel bijvoorbeeld de eigenschappen van de geselecteerde cellen in.

**Hyperlinks gaan verloren wanneer een component wordt bewerkt met de knop Configureren**

Voeg een hyperlink in een tekstcomponent toe door het uit te geven gebruikend de Configure knoop. U kunt de hyperlink verliezen wanneer u deze opnieuw bewerkt en de hyperlink voor de tweede keer valideert.

Als tussenoplossing kunt u in de tekstcomponent klikken wanneer het dialoogvenster voor bewerken de tweede keer wordt weergegeven en vervolgens de koppelingsvalidatie uitvoeren.

Dit probleem is opgelost in AEM 6.3 en hoger.

**HTML-inhoud die in de bronbewerkingsmodus is toegevoegd, gaat verloren**

Voeg geen XSS-prone HTML toe. AEM, en niet RTE, kunnen sommige inhoud van HTML verwijderen om aan de XSS antisamy regels te voldoen.

Controleer de opgeslagen inhoud in CRXDE (in het inhoudsknooppunt) om te controleren of de geplakte HTML is opgeslagen.

Als niet bewaard, moet de HTML door RTE zijn verwijderd aangezien het niet aan de regels van RTE volgde.

Indien opgeslagen in CRXDE maar niet gerenderd op de Pagina (om het teruggeven te controleren, zie [voorvertoning](/help/sites-authoring/editing-content.md#preview-mode), wordt het verwijderd door AEM XSS-regels.

**Multifield-component werkt niet zoals verwacht**

Als u een component met meerdere velden wilt maken, gebruikt u uitsluitend CoralUI 3. Gebruik geen dialoogvensters met CoralUI 2-componenten.

Controleer ook of de implementatiecode en de knooppuntstructuur voor meerdere velden correct zijn.

**Configuratie beschikbaar voor beheerders is niet beschikbaar voor auteurs**

Als de updates van interfaceconfiguraties voor beheerders maar niet voor auteursrekeningen worden weerspiegeld, zorg ervoor dat de configuratieknoopknoop niet wordt genoemd `config`. Gebruik de [`configPath` eigenschap](/help/sites-developing/components-basics.md#cq-inplaceediting).

>[!MORELIKETHIS]
>
>* [RTE-plug-ins configureren](configure-rich-text-editor-plug-ins.md)
>* [Rich Text Editor gebruiken voor ontwerpen](../sites-authoring/rich-text-editor.md)
>* [RTE voor toegankelijke sites configureren](rte-accessible-content.md)
>* [Aanraakinterface en Klassieke UI-functiepariteit](../release-notes/touch-ui-features-status.md)
>* [Zelfstudie als voorbeeld voor het maken van een samengestelde component met meerdere velden](https://experience-aem.blogspot.com/2019/05/aem-65-touchui-composite-multifield-with-coral3-rte-rich-text.html)
