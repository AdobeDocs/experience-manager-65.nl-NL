---
title: Configureer Rich Text Editor om toegankelijke webpagina's en sites te maken.
description: Configureer Rich Text Editor om toegankelijke webpagina's en sites te maken.
contentOwner: AG
translation-type: tm+mt
source-git-commit: df992fc0204519509c4662a7d4315939af2fc92c
workflow-type: tm+mt
source-wordcount: '933'
ht-degree: 0%

---


# RTE configureren om toegankelijke webpagina&#39;s en sites te maken {#configure-rte-for-accessibility}

Adobe Experience Manager ondersteunt de meeste standaardtoegankelijkheidsfuncties in overeenstemming met verschillende toegankelijkheidsstandaarden. Daarnaast kunnen ontwikkelaars functies aanpassen of uitbreiden om toegankelijke inhoud te bieden met behulp van Experience Manager-componenten die gebruikmaken van de Rich Text Editor (RTE).

Wanneer het ontwerpen van Web-pagina&#39;s en het toevoegen van inhoud aan de pagina&#39;s, kunnen de inhoudsontwikkelaars en de auteurs eigenschappen van RTE gebruiken om op toegankelijkheid betrekking hebbende informatie te verstrekken. Voeg bijvoorbeeld structuurinformatie toe via koppen en alinea-elementen.

Om deze eigenschappen te vormen en aan te passen, [vorm de steekmodules van RTE](#configure-the-plugin-features) voor de component. Met de `paraformat`-plug-in kunt u bijvoorbeeld extra semantische elementen op blokniveau toevoegen, zoals het uitbreiden van het aantal kopniveaus dat wordt ondersteund tot voorbij de standaard `H1`, `H2` en `H3`.

RTE is beschikbaar in een verscheidenheid van componenten voor aanraking-toegelaten gebruikersinterface en het Klassieke gebruikersinterface. Nochtans, is de primaire component om RTE te gebruiken de **component Text** die voor beide interfaces beschikbaar is. De volgende afbeeldingen tonen de RTE met een bereik van ingeschakelde plug-ins, waaronder `paraformat`:

![Tekstcomponent (RTE) in de modus Volledig scherm in de gebruikersinterface met aanraakbediening.](assets/chlimage_1-206.png)

*Afbeelding: De component Text in de gebruikersinterface met aanraakbediening.*

![Dialoogvenster voor bewerken (RTE) van de tekstcomponent in de klassieke UI.](assets/chlimage_1-207.png)

*Afbeelding: De component Text in de klassieke gebruikersinterface.*

Voor de verschillen tussen de eigenschappen RTE beschikbaar in de diverse interfaces, zie [Insteekmodules en hun eigenschappen](/help/sites-administering/rich-text-editor.md#aboutplugins).

## De insteekmodule {#configure-the-plugin-features} configureren

Voor de volledige instructies om RTE te vormen, zie [vorm de Rich Text Editor](/help/sites-administering/rich-text-editor.md) pagina. Hieronder vallen alle kwesties, inclusief de belangrijkste stappen:

* [Plugins en de functies](/help/sites-administering/rich-text-editor.md#aboutplugins).
* [Configuratielocaties](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
* [Activeer een plug-in en configureer de eigenschap](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins) features.
* [Andere functies van RTE](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins) vormen.

Door een plug-in te configureren in de desbetreffende `rtePlugins`-subvertakking in CRXDE Lite, kunt u alle of specifieke functies voor die plug-in activeren.

![CRXDE Lite die een voorbeeld rtePlugin toont.](assets/chlimage_1-208.png)

### Voorbeeld - specificeer paragraafformaten beschikbaar op het gebied van de selectie van RTE {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Nieuwe semantische blokformaten kunnen voor selectie beschikbaar worden gesteld door:

1. Afhankelijk van uw RTE, bepaal en navigeer aan [configuratielocatie](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
1. [Het selectieveld](/help/sites-administering/rich-text-editor.md) Alinea inschakelen. door de  [insteekmodule](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins) te activeren.
1. [Geef de indelingen op die u beschikbaar wilt hebben in het selectieveld](/help/sites-administering/rich-text-editor.md) Alinea.
1. De paragraafformaten zijn dan beschikbaar aan de inhoudauteur van de selectiegebieden in RTE. Zij kunnen worden betreden:

   * Het pictogram voor het schuiven van alinea&#39;s gebruiken in de interface voor aanraakbediening.
   * Het veld **Indeling** (pop-upkiezer) gebruiken in de klassieke gebruikersinterface.

Met de structuurelementen beschikbaar in RTE via de opties van het paragraafformaat, AEM verstrekt een goede basis voor de ontwikkeling van toegankelijke inhoud. Inhoudsauteurs kunnen de RTE niet gebruiken om de tekengrootte of kleuren of andere verwante kenmerken op te maken, waardoor inlineopmaak niet mogelijk is. In plaats daarvan moeten ze de juiste structuurelementen selecteren, zoals koppen, en algemene stijlen gebruiken die u hebt gekozen bij de optie Stijlen. Zo zorgt u voor meer opmaak, betere opties voor gebruikers die met hun eigen stijlpagina&#39;s en correct gestructureerde inhoud bladeren.

## Gebruik van de bronbewerkingsfunctie {#use-of-the-source-edit-feature}

In sommige gevallen zullen inhoudsauteurs het nodig vinden om de HTML-broncode die met de RTE is gemaakt, te onderzoeken en aan te passen. Bijvoorbeeld, kan een stuk van inhoud die binnen RTE wordt gecreeerd extra prijsverhoging vereisen om naleving WCAG 2.0 te verzekeren. Dit kan met [bron worden gedaan uitgeven](/help/sites-administering/rich-text-editor.md#aboutplugins) optie van RTE. U kunt de [ `sourceedit` eigenschap op `misctools` stop in ](/help/sites-administering/rich-text-editor.md#aboutplugins) specificeren.

>[!CAUTION]
>
>Gebruik de functie `sourceedit` zorgvuldig. Door fouten en/of niet-ondersteunde functies te typen kunnen er meer problemen ontstaan.

## Ondersteuning toevoegen voor meer HTML-elementen en -kenmerken {#add-support-for-more-html-elements-and-attributes}

Om de toegankelijkheidskenmerken van AEM verder uit te breiden, is het mogelijk om de bestaande componenten die op RTE (zoals **Text** en **Table** componenten) worden gebaseerd met extra elementen en attributen uit te breiden.

De volgende procedure laat zien hoe u de component **Tabel** kunt uitbreiden met een element **Bijschrift** dat informatie over een gegevenstabel bevat voor gebruikers van ondersteunende technologie:

### Voorbeeld - voeg het bijschrift toe aan het dialoogvenster Tabeleigenschappen {#example-adding-the-caption-to-the-table-properties-dialog}

Voeg in de constructor van de `TablePropertiesDialog` een extra tekstinvoerveld toe dat wordt gebruikt voor het bewerken van het bijschrift. `itemId` moet worden ingesteld op `caption` (d.w.z. de naam van het DOM-kenmerk) om de inhoud ervan automatisch te kunnen verwerken.

In **Lijst**, plaats uitdrukkelijk of verwijder de attributen aan/uit het element DOM. De waarde wordt doorgegeven door het dialoogvenster in het object `config`. DOM-kenmerken moeten worden ingesteld/verwijderd met de corresponderende `CQ.form.rte.Common`-methoden ( `com` is een sneltoets voor `CQ.form.rte.Common`) om gemeenschappelijke valkuilen bij browserimplementaties te voorkomen.

>[!NOTE]
>
>Deze procedure is alleen geschikt voor de klassieke gebruikersinterface.

### Voorbeeld: toegankelijke HTML maken bij gebruik van nadruk in tekst {#create-accessible-html-for-text}

RTE kan `strong` en `em` markeringen in plaats van `b` en `i` gebruiken. Voeg de volgende knoop als sibling aan `uiSettings` en `rtePlugins` knopen in de dialoog toe.

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

1. Bij de methode `constructor`, vóór het lezen van de regel:

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

1. Voeg de volgende code aan het einde van de methode `transferConfigToTable` toe:

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

1. Sla uw wijzigingen op met **Alles opslaan..**

>[!NOTE]
>
>Een veld zonder opmaak is niet het enige invoertype dat is toegestaan voor de waarde van het bijschriftelement. U kunt elke ExtJS-widget gebruiken die de waarde van de ondertitel via de `getValue()`-methode biedt.
>
>Als u bewerkingsmogelijkheden voor meer aanvullende elementen en kenmerken wilt toevoegen, moet u ervoor zorgen dat:
>
>* De eigenschap `itemId` voor elk overeenkomend veld wordt ingesteld op de naam van het desbetreffende DOM-kenmerk (`TablePropertiesDialog`).
>* Het kenmerk wordt expliciet ingesteld en/of verwijderd op het DOM-element (`Table`).


>[!MORELIKETHIS]
>
>* [Snelle gids aan WCAG 2.0](/help/managing/qg-wcag.md)
>* [Toegankelijke inhoud maken (WCAG 2.0-conformiteit)](/help/sites-authoring/creating-accessible-content.md)

