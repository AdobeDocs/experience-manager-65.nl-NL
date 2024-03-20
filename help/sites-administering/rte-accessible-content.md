---
title: Configureer Rich Text Editor om toegankelijke webpagina's en sites te maken.
description: Configureer Rich Text Editor om toegankelijke webpagina's en sites te maken.
contentOwner: AG
exl-id: d2451710-5abf-4816-8052-57d8f04a228e
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 0%

---

# RTE configureren om toegankelijke webpagina&#39;s en sites te maken {#configure-rte-for-accessibility}

Adobe Experience Manager ondersteunt de meeste standaardtoegankelijkheidsfuncties in overeenstemming met verschillende toegankelijkheidsstandaarden. Daarnaast kunnen ontwikkelaars functies aanpassen of uitbreiden om toegankelijke inhoud te bieden met behulp van Experience Manager-componenten die gebruikmaken van de Rich Text Editor (RTE).

Wanneer het ontwerpen van Web-pagina&#39;s en het toevoegen van inhoud aan de pagina&#39;s, kunnen de inhoudsontwikkelaars en de auteurs eigenschappen van RTE gebruiken om op toegankelijkheid betrekking hebbende informatie te verstrekken. Voeg bijvoorbeeld structuurinformatie toe via koppen en alinea-elementen.

Deze functies configureren en aanpassen [vorm de stop RTE](#configure-the-plugin-features) voor de component. Bijvoorbeeld de `paraformat` Met de plug-in kunt u extra semantische elementen op blokniveau toevoegen, waaronder het uitbreiden van het aantal kopniveaus dat boven de basisniveaus wordt ondersteund `H1`, `H2`, en `H3` standaard opgegeven.

RTE is beschikbaar in een verscheidenheid van componenten voor aanraking-toegelaten gebruikersinterface en het Klassieke gebruikersinterface. Nochtans, is de primaire component om RTE te gebruiken **Tekst** component die voor beide interfaces beschikbaar is. In de volgende afbeeldingen ziet u de RTE met een reeks ingeschakelde plug-ins, waaronder `paraformat`:

![Tekstcomponent (RTE) in de modus Volledig scherm in de gebruikersinterface met aanraakbediening.](assets/chlimage_1-206.png)

*Afbeelding: De component Text in de gebruikersinterface met aanraakbediening.*

![Dialoogvenster voor bewerken (RTE) van de tekstcomponent in de klassieke UI.](assets/chlimage_1-207.png)

*Figuur: De component van de Tekst in het Klassieke gebruikersinterface.*

Voor de verschillen tussen de eigenschappen van RTE beschikbaar in de diverse interfaces, zie [Plug-ins en bijbehorende functies](/help/sites-administering/rich-text-editor.md#aboutplugins).

## De insteekmodules configureren {#configure-the-plugin-features}

Voor volledige instructies om RTE te vormen, zie [vormen de Rich Text Editor](/help/sites-administering/rich-text-editor.md) pagina. Hieronder vallen alle kwesties, inclusief de belangrijkste stappen:

* [Plug-ins en de functies](/help/sites-administering/rich-text-editor.md#aboutplugins).
* [Configuratielocaties](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
* [Een plug-in activeren en de eigenschap features configureren](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
* [Andere functies van de RTE configureren](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).

Door een insteekmodule te configureren binnen de juiste `rtePlugins` subvertakking in CRXDE Lite, kunt u of alle of specifieke eigenschappen voor die stop activeren.

![CRXDE Lite die een voorbeeld rtePlugin toont.](assets/chlimage_1-208.png)

### Voorbeeld - geef alineaopmaak op die beschikbaar is in het veld RTE-selectie {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Nieuwe semantische blokformaten kunnen voor selectie beschikbaar worden gesteld door:

1. Afhankelijk van uw RTE, bepaal en navigeer aan [configuratielocatie](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
1. [Het selectieveld Alinea inschakelen](/help/sites-administering/rich-text-editor.md); door [de insteekmodule activeren](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [Geef de indelingen op die beschikbaar moeten zijn in het selectieveld Alinea](/help/sites-administering/rich-text-editor.md).
1. De paragraafformaten zijn dan beschikbaar aan de inhoudauteur van de selectiegebieden in RTE. Zij kunnen worden betreden:

   * Het pictogram voor het schuiven van alinea&#39;s gebruiken in de interface voor aanraakbediening.
   * Met de **Indeling** veld (pop-upkiezer) in de klassieke interface.

Met de structuurelementen beschikbaar in RTE via de opties van het paragraafformaat, AEM verstrekt een goede basis voor de ontwikkeling van toegankelijke inhoud. Inhoudsauteurs kunnen de RTE niet gebruiken om de tekengrootte of kleuren of andere verwante kenmerken op te maken, waardoor inlineopmaak niet mogelijk is. In plaats daarvan moeten ze de juiste structuurelementen selecteren, zoals koppen, en algemene stijlen gebruiken die u hebt gekozen bij de optie Stijlen. Zo zorgt u voor meer opmaak, betere opties voor gebruikers die met hun eigen stijlpagina&#39;s en correct gestructureerde inhoud bladeren.

## De functie voor bronbewerking gebruiken {#use-of-the-source-edit-feature}

In sommige gevallen, zullen de inhoudsauteurs het noodzakelijk vinden om de HTML broncode te onderzoeken en aan te passen die gebruikend RTE wordt gecreeerd. Bijvoorbeeld, kan een stuk van inhoud die binnen RTE wordt gecreeerd extra prijsverhoging vereisen om naleving WCAG 2.0 te verzekeren. Dit kan worden gedaan met de [bronbewerking](/help/sites-administering/rich-text-editor.md#aboutplugins) optie van de RTE. U kunt de [`sourceedit` op de `misctools` insteekmodule](/help/sites-administering/rich-text-editor.md#aboutplugins).

>[!CAUTION]
>
>Gebruik de `sourceedit` zorgvuldig worden uitgevoerd. Door fouten en/of niet-ondersteunde functies te typen kunnen er meer problemen ontstaan.

## Ondersteuning toevoegen voor meer HTML-elementen en -kenmerken {#add-support-for-more-html-elements-and-attributes}

Om de toegankelijkheidskenmerken van AEM verder uit te breiden, is het mogelijk de bestaande componenten op basis van de RTE (zoals de **Tekst** en **Tabel** componenten) met extra elementen en kenmerken.

De volgende procedure laat zien hoe u de **Tabel** component met een **Bijschrift** element dat informatie over een gegevenslijst aan hulptechnologiegebruikers verstrekt:

### Voorbeeld: het bijschrift toevoegen aan het dialoogvenster Tabeleigenschappen {#example-adding-the-caption-to-the-table-properties-dialog}

In de constructor van de `TablePropertiesDialog`voegt u een extra tekstinvoerveld toe dat wordt gebruikt voor het bewerken van het bijschrift. Let op: `itemId` moet worden ingesteld op `caption` (de naam van het DOM-kenmerk) om de inhoud ervan automatisch af te handelen.

In **Tabel**, stelt u het kenmerk expliciet in op het DOM-element of verwijdert u dit. De waarde wordt doorgegeven door het dialoogvenster in het dialoogvenster `config` object. DOM-kenmerken moeten worden ingesteld/verwijderd met de corresponderende `CQ.form.rte.Common` methoden ( `com` is een sneltoets voor `CQ.form.rte.Common`) om gemeenschappelijke valkuilen bij browserimplementaties te voorkomen.

>[!NOTE]
>
>Deze procedure is alleen geschikt voor de klassieke gebruikersinterface.

### Voorbeeld: toegankelijke HTML maken bij gebruik van nadruk in tekst {#create-accessible-html-for-text}

RTE kan `strong` en `em` -tags in plaats van `b` en `i`. Voeg de volgende knoop als sibling aan toe `uiSettings` en `rtePlugins` knooppunten in het dialoogvenster.

```HTML
<htmlRules jcr:primaryType="nt:unstructured">
    <docType jcr:primaryType="nt:unstructured">
        <typeConfig jcr:primaryType="nt:unstructured"
                useSemanticMarkup="{Boolean}true">
            <semanticMarkupMap
                    b="strong"
                    i="em"/>
        </typeConfig>
    </docType>
</htmlRules>
```

### Stapsgewijze instructies {#step-by-step-instructions}

1. Start CRXDE Lite. Bijvoorbeeld: [http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
1. Kopiëren:

   `/libs/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   tot:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`

   >[!NOTE]
   >
   >Mogelijk moet u tussenliggende mappen maken als deze nog niet bestaan.

1. Kopiëren:

   `/libs/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

   tot:

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`.

1. Open het volgende bestand om te bewerken (openen met dubbelklikken):

   `/apps/cq/ui/widgets/source/widgets/form/rte/plugins/TablePropertiesDialog.js`

1. In de `constructor` methode, vóór het lezen van de regel:

   ```
   var dialogRef = this;
   ```

   Voeg de volgende code toe:

   ```
   editItems.push({
       "itemId": "caption",
       "name": "caption",
       "xtype": "textfield",
       "fieldLabel": CQ.I18n.getMessage("Caption"),
       "value": (this.table && this.table.caption ? this.table.caption.textContent : "")
   });
   ```

1. Open het volgende bestand:

   `/apps/cq/ui/widgets/source/widgets/form/rte/commands/Table.js`.

1. Voeg de volgende code toe aan het einde van de `transferConfigToTable` methode:

   ```
   /**
    * Adds Caption Element
   */
   var captionElement;
   if (dom.firstChild && dom.firstChild.tagName.toLowerCase() == "caption")
   {
      captionElement = dom.firstChild;
   }
   if (config.caption)
   {
       var captionTextNode = document.createTextNode(config.caption)
       if (captionElement)
       {
          dom.replaceNode(captionElement.firstChild,captionTextNode);
       } else
       {
           captionElement = document.createElement("caption");
           captionElement.appendChild(captionTextNode);
           if (dom.childNodes.length>0)
           {
              dom.insertBefore(captionElement, dom.firstChild);
           } else
           {
              dom.appendChild(captionElement);
           }
       }
   } else if (captionElement)
   {
     dom.removeChild(captionElement);
   }
   ```

1. Wijzigingen opslaan met **Alles opslaan...**

>[!NOTE]
>
>Een veld zonder opmaak is niet het enige invoertype dat is toegestaan voor de waarde van het bijschriftelement. U kunt elke ExtJS-widget gebruiken die de waarde van de ondertitel via de bijbehorende `getValue()` methode.
>
>Als u bewerkingsmogelijkheden voor meer aanvullende elementen en kenmerken wilt toevoegen, moet u ervoor zorgen dat:
>
>* De `itemId` eigenschap voor elk overeenkomstig veld wordt ingesteld op de naam van het desbetreffende DOM-kenmerk (`TablePropertiesDialog`).
>* Het kenmerk wordt expliciet ingesteld en/of verwijderd op het DOM-element (`Table`).

>[!MORELIKETHIS]
>
>* [Snelle gids aan WCAG 2.0](/help/managing/qg-wcag.md)
>* [Toegankelijke inhoud maken (WCAG 2.0-conformiteit)](/help/sites-authoring/creating-accessible-content.md)
