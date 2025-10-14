---
title: Configureer Rich Text Editor om toegankelijke webpagina's en sites te maken.
description: Configureer Rich Text Editor om toegankelijke webpagina's en sites te maken.
contentOwner: AG
exl-id: d2451710-5abf-4816-8052-57d8f04a228e
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '930'
ht-degree: 0%

---

# RTE configureren om toegankelijke webpagina&#39;s en sites te maken {#configure-rte-for-accessibility}

Adobe Experience Manager ondersteunt de meeste standaardtoegankelijkheidsfuncties in overeenstemming met verschillende toegankelijkheidsstandaarden. Daarnaast kunnen ontwikkelaars functies aanpassen of uitbreiden om toegankelijke inhoud te bieden met behulp van Experience Manager-componenten die gebruikmaken van de Rich Text Editor (RTE).

Wanneer het ontwerpen van Web-pagina&#39;s en het toevoegen van inhoud aan de pagina&#39;s, kunnen de inhoudsontwikkelaars en de auteurs eigenschappen van RTE gebruiken om op toegankelijkheid betrekking hebbende informatie te verstrekken. Voeg bijvoorbeeld structuurinformatie toe via koppen en alinea-elementen.

Om deze eigenschappen te vormen en aan te passen, [&#x200B; vormen de stoppen RTE &#x200B;](#configure-the-plugin-features) voor de component. Met de insteekmodule `paraformat` kunt u bijvoorbeeld extra semantische elementen op blokniveau toevoegen, zoals het uitbreiden van het aantal kopniveaus dat wordt ondersteund buiten de standaard `H1` , `H2` en `H3` geboden.

RTE is beschikbaar in een verscheidenheid van componenten voor aanraking-toegelaten gebruikersinterface en het Klassieke gebruikersinterface. Nochtans, is de primaire component om RTE te gebruiken de **&#x200B;**&#x200B;component van de Tekst die voor beide interfaces beschikbaar is. De volgende afbeeldingen tonen de RTE met een bereik van ingeschakelde plug-ins, waaronder `paraformat` :

![&#x200B; component van de Tekst (RTE) op volledig-scherm-wijze in aanraking-toegelaten UI.](assets/chlimage_1-206.png)

*Cijfer: De component van de Tekst in het aanraking-Toegelaten gebruikersinterface.*

![&#x200B; geef dialoog (RTE) van de tekstcomponent in klassieke UI uit.](assets/chlimage_1-207.png)

*Cijfer: De component van de Tekst in het Klassieke gebruikersinterface.*

Voor de verschillen tussen de eigenschappen RTE beschikbaar in de diverse interfaces, zie [&#x200B; Insteekmodules en hun eigenschappen &#x200B;](/help/sites-administering/rich-text-editor.md#aboutplugins).

## De insteekmodules configureren {#configure-the-plugin-features}

Voor de volledige instructies om RTE te vormen, zie [&#x200B; de Rijke pagina van de Redacteur van de Tekst &#x200B;](/help/sites-administering/rich-text-editor.md) vormen. Hieronder vallen alle kwesties, inclusief de belangrijkste stappen:

* [&#x200B; Insteekmodules en de eigenschappen &#x200B;](/help/sites-administering/rich-text-editor.md#aboutplugins).
* [&#x200B; plaatsen van de Configuratie &#x200B;](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
* [&#x200B; activeer een stop en vorm het eigenschapbezit &#x200B;](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
* [&#x200B; vormt andere functionaliteit van RTE &#x200B;](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).

Door een plug-in te configureren in de juiste `rtePlugins` -subvertakking in CRXDE Lite, kunt u alle of specifieke functies voor die plug-in activeren.

![&#x200B; CRXDE Lite die een voorbeeld rtePlugin toont.](assets/chlimage_1-208.png)

### Voorbeeld - geef alineaopmaak op die beschikbaar is in het veld RTE-selectie {#example-specifying-paragraph-formats-available-in-rte-selection-field}

Nieuwe semantische blokformaten kunnen voor selectie beschikbaar worden gesteld door:

1. Afhankelijk van uw RTE, bepaal en navigeer aan de [&#x200B; configuratielocatie &#x200B;](/help/sites-administering/rich-text-editor.md#understand-the-configuration-paths-and-locations).
1. [&#x200B; laat het gebied van de paragraafselectie &#x200B;](/help/sites-administering/rich-text-editor.md) toe; door [&#x200B; de stop te activeren &#x200B;](/help/sites-administering/rich-text-editor.md#enable-rte-functionalities-by-activating-plug-ins).
1. [&#x200B; specificeer de formaten u op het de selectiegebied van Alinea &#x200B;](/help/sites-administering/rich-text-editor.md) beschikbaar wilt hebben.
1. De paragraafformaten zijn dan beschikbaar aan de inhoudauteur van de selectiegebieden in RTE. Zij kunnen worden betreden:

   * Het pictogram voor het schuiven van alinea&#39;s gebruiken in de interface voor aanraakbediening.
   * Gebruikend het **gebied van het Formaat** (pop-up selecteur) in Klassieke UI.

Met de structuurelementen beschikbaar in RTE via de opties van het paragraafformaat, AEM verstrekt een goede basis voor de ontwikkeling van toegankelijke inhoud. Inhoudsauteurs kunnen de RTE niet gebruiken om de tekengrootte of kleuren of andere verwante kenmerken op te maken, waardoor inlineopmaak niet mogelijk is. In plaats daarvan moeten ze de juiste structuurelementen selecteren, zoals koppen, en algemene stijlen gebruiken die u hebt gekozen bij de optie Stijlen. Zo zorgt u voor meer opmaak, betere opties voor gebruikers die met hun eigen stijlpagina&#39;s en correct gestructureerde inhoud bladeren.

## De functie voor bronbewerking gebruiken {#use-of-the-source-edit-feature}

In sommige gevallen, zullen de inhoudsauteurs het noodzakelijk vinden om de HTML broncode te onderzoeken en aan te passen die gebruikend RTE wordt gecreeerd. Bijvoorbeeld, kan een stuk van inhoud die binnen RTE wordt gecreeerd extra prijsverhoging vereisen om naleving WCAG 2.0 te verzekeren. Dit kan met [&#x200B; bron worden gedaan geeft &#x200B;](/help/sites-administering/rich-text-editor.md#aboutplugins) optie van RTE uit. U kunt de functie [`sourceedit` opgeven in de `misctools` plug-in &#x200B;](/help/sites-administering/rich-text-editor.md#aboutplugins) .

>[!CAUTION]
>
>Gebruik de functie `sourceedit` zorgvuldig. Door fouten en/of niet-ondersteunde functies te typen kunnen er meer problemen ontstaan.

## Ondersteuning toevoegen voor meer HTML-elementen en -kenmerken {#add-support-for-more-html-elements-and-attributes}

Om de toegankelijkheidseigenschappen van AEM verder uit te breiden, is het mogelijk om de bestaande componenten uit te breiden die op RTE (zoals de **Tekst** en **3&rbrace; componenten van de Lijst) met extra elementen en attributen worden gebaseerd.**

De volgende procedure illustreert hoe te om de **component van de Lijst** met a **het element van de Titel** uit te breiden dat informatie over een gegevenslijst aan hulptechnologiegebruikers verstrekt:

### Voorbeeld: het bijschrift toevoegen aan het dialoogvenster Tabeleigenschappen {#example-adding-the-caption-to-the-table-properties-dialog}

Voeg in de constructor van de `TablePropertiesDialog` een extra tekstinvoerveld toe dat wordt gebruikt voor het bewerken van het bijschrift. `itemId` moet zijn ingesteld op `caption` (de naam van het DOM-kenmerk) om de inhoud ervan automatisch te kunnen verwerken.

In **Lijst**, plaats uitdrukkelijk of verwijder de attributen aan/van het DOM element. De waarde wordt doorgegeven door het dialoogvenster in het `config` -object. DOM-kenmerken moeten worden ingesteld/verwijderd met de overeenkomende `CQ.form.rte.Common` -methoden ( `com` is een sneltoets voor `CQ.form.rte.Common` ) om gemeenschappelijke valkuilen bij browserimplementaties te voorkomen.

>[!NOTE]
>
>Deze procedure is alleen geschikt voor de klassieke gebruikersinterface.

### Voorbeeld: toegankelijke HTML maken bij gebruik van nadruk in tekst {#create-accessible-html-for-text}

RTE kan `strong` - en `em` -tags gebruiken in plaats van `b` en `i` . Voeg het volgende knooppunt toe als een knooppunt op hetzelfde niveau als de knooppunten `uiSettings` en `rtePlugins` in het dialoogvenster.

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

1. Start CRXDE Lite. Bijvoorbeeld: [&#x200B; http://localhost:4502/crx/de/](http://localhost:4502/crx/de/)
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

1. In de methode `constructor` , vóór het lezen van de regel:

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

1. Voeg de volgende code toe aan het einde van de methode `transferConfigToTable` :

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

1. Sparen uw veranderingen gebruikend **sparen allen..**

>[!NOTE]
>
>Een veld zonder opmaak is niet het enige invoertype dat is toegestaan voor de waarde van het bijschriftelement. U kunt elke ExtJS-widget gebruiken die via de `getValue()` -methode de waarde van de ondertitel biedt.
>
>Als u bewerkingsmogelijkheden voor meer aanvullende elementen en kenmerken wilt toevoegen, moet u ervoor zorgen dat:
>
>* De eigenschap `itemId` voor elk overeenkomend veld wordt ingesteld op de naam van het desbetreffende DOM-kenmerk (`TablePropertiesDialog` ).
>* Het kenmerk wordt expliciet ingesteld en/of verwijderd op het DOM-element (`Table`).

>[!MORELIKETHIS]
>
>* [&#x200B; Snelle Gids aan WCAG 2.0 &#x200B;](/help/managing/qg-wcag.md)
>* [&#x200B; creeer toegankelijke inhoud (WCAG 2.0 conformiteit) &#x200B;](/help/sites-authoring/creating-accessible-content.md)
