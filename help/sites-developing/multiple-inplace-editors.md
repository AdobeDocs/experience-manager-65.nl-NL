---
title: Vorm RTE voor veelvoudige op zijn plaats redacteurs.
description: U kunt meerdere lokale editors maken in Adobe Experience Manager door de Rich Text Editor te configureren.
contentOwner: AG
exl-id: 03030317-8b7d-408a-bdfd-619824d7260c
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '437'
ht-degree: 0%

---

# Meerdere lokale editors configureren {#configure-multiple-in-place-editors}

U kunt de Rich Text Editor in Adobe Experience Manager zodanig configureren dat deze meerdere op zijn plaats geplaatste editors heeft. Wanneer gevormd kunt u de aangewezen inhoud selecteren en de aangewezen redacteur openen.

![ een specifieke op zijn plaats redacteur ](assets/rte-inplace-editor.png)

## Meerdere editors configureren {#configure-multiple-editors}

Om meerdere op zijn plaats gevestigde editors in te schakelen, is de structuur van een knooppunttype `cq:InplaceEditingConfig` verbeterd met de definitie van knooppunttype `cq:ChildEditorConfig` .

Bijvoorbeeld:

```js
   /**
       * Configures in-place editing of a component.
       *
       * @prop active true to activate in-place editing for the component.
       * @prop editorType ID of in-place editor to use.
       * @prop cq:childEditors collection of {@link cq:ChildEditorConfig} nodes.
       * @prop configPath path to editor's config (optional).
       * @node config editor's config (used if no configPath is specified; optional).
     */
    [cq:InplaceEditingConfig] > nt:unstructured
      - active (boolean)
      - editorType (string)
      + cq:childEditors (nt:base) = nt:unstructured
      - configPath (string)
      + config (nt:unstructured) = nt:unstructured

    /**
      * Configures one child editor for a sub-component. The name of the this node is
      * used as DD ID.
      *
      * @prop type type of the inline editor. For example, ["image"].
      * @prop title Title of the inline editor.
      * @prop icon Icon to represent the inline editor.
    */
    [cq:ChildEditorConfig] > nt:unstructured
      orderable
      - type (string)
      - title (string)
```

Voer de volgende stappen uit om meerdere editors te configureren:

1. Definieer in het knooppunt `cq:inplaceEditing` (van het type `cq:InplaceEditingConfig` ) de volgende eigenschappen:

   * Naam:`editorType`
   * Type: `String`
   * Waarde: `hybrid`

1. Onder dit knooppunt maakt u een knooppunt:

   * Naam: `cq:ChildEditors`
   * Type: `nt:unstructured`

1. Onder `cq:childEditors` -knooppunt maakt u een knooppunt voor elke interne editor:

   * Naam: De naam van elk knooppunt is de naam van de eigenschap die het vertegenwoordigt, net als bij neerzetdoelen. Bijvoorbeeld `image` en `text` .
   * Type: `cq:ChildEditorConfig`

   >[!NOTE]
   >
   >Er is een correlatie tussen de gedefinieerde neerzetdoelen en de onderliggende editors. De naam van het knooppunt `cq:ChildEditorConfig` wordt beschouwd als de doel-id voor neerzetten, voor gebruik als parameter voor de geselecteerde onderliggende editor. Als het bewerkbare subgebied bijvoorbeeld geen neerzetdoel heeft in een tekstcomponent, wordt de naam van de onderliggende editor nog steeds beschouwd als een id om het overeenkomende bewerkbare gebied te identificeren.

1. Voor elk van deze knopen (`cq:ChildEditorConfig`) bepalen de eigenschappen:

   * Naam: `type`.
   * Waarde: de naam van de geregistreerde interne editor, bijvoorbeeld `image` en `text` .

   * Naam: `title`.
   * Waarde: de titel die wordt weergegeven in de keuzelijst met componenten van de beschikbare editors. Bijvoorbeeld `Image` en `Text` .

### Aanvullende configuratie voor Rich Text Editors {#additional-configuration-for-rich-text-editors}

De configuratie voor veelvoudige Rich Text Editors is lichtjes verschillend aangezien u elke individuele instantie van RTE afzonderlijk kunt vormen. Voor details, zie [ de Rijke Redacteur van de Tekst ](/help/sites-administering/rich-text-editor.md) vormen. Om veelvoudige RTEs te hebben creeer een configuratie voor elke op zijn plaats RTE. De Adobe adviseert creërend de nieuwe configuratieknoop onder `cq:InplaceEditingConfig` aangezien elke individuele RTE een verschillende configuratie kan hebben. Onder de nieuwe knoop creeert elke individuele configuratie van RTE.

```xml
    texttext
        cq:dialog
        cq:editConfig
            cq:inplaceEditing
                cq:childEditors
                    someconfig
                        text1
                            rtePlugins
                        text2
                            rtePlugins
```

>[!NOTE]
>
>Voor RTE wordt de eigenschap `configPath` echter ondersteund wanneer de component slechts één instantie van een teksteditor (bewerkbaar subgebied) bevat. Dit gebruik van `configPath` wordt verstrekt om achterwaartse verenigbaarheid met oudere gebruikersinterfacedialogen van de component te steunen.

>[!CAUTION]
>
>Geef het RTE-configuratieknooppunt geen naam als `config` . Anders, zijn de configuraties RTE beschikbaar voor slechts de beheerders en niet voor de gebruikers in de groep `content-author`.

## Codevoorbeelden {#code-samples}

U kunt de code van deze pagina op [ aem-authoring-hybrideditors project op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors) vinden. U kunt het volledige project als [ aZIP archief ](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors/archive/master.zip) downloaden.

## Een interne editor toevoegen {#add-an-in-place-editor}

Voor algemene informatie over het toevoegen van een op zijn plaats redacteur zie het document [ pagina creatie ](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor) aanpassen.

>[!MORELIKETHIS]
>
>* [ vormt Rich Text Editor in Experience Manager ](/help/sites-administering/rich-text-editor.md).
