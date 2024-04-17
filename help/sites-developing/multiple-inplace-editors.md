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

![Een specifieke interne editor](assets/rte-inplace-editor.png)

## Meerdere editors configureren {#configure-multiple-editors}

Om veelvoudige op zijn plaats redacteurs toe te laten de structuur van een `cq:InplaceEditingConfig` het knooptype is verbeterd met de definitie van `cq:ChildEditorConfig` knooppunttype.

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

1. Op het knooppunt `cq:inplaceEditing` (van het type `cq:InplaceEditingConfig`) definieert u de volgende eigenschappen:

   * Naam:`editorType`
   * Type: `String`
   * Waarde: `hybrid`

1. Onder dit knooppunt maakt u een knooppunt:

   * Naam: `cq:ChildEditors`
   * Type: `nt:unstructured`

1. Onder `cq:childEditors` knoop, creeer een knoop voor elke op zijn plaats redacteur:

   * Naam: De naam van elk knooppunt is de naam van de eigenschap die het vertegenwoordigt, net als bij neerzetdoelen. Bijvoorbeeld: `image` en `text`.
   * Type: `cq:ChildEditorConfig`

   >[!NOTE]
   >
   >Er is een correlatie tussen de gedefinieerde neerzetdoelen en de onderliggende editors. De naam van `cq:ChildEditorConfig` knooppunt wordt beschouwd als doel-id voor neerzetten, voor gebruik als parameter voor de geselecteerde onderliggende editor. Als het bewerkbare subgebied bijvoorbeeld geen neerzetdoel heeft in een tekstcomponent, wordt de naam van de onderliggende editor nog steeds beschouwd als een id om het overeenkomende bewerkbare gebied te identificeren.

1. Op elk van deze knooppunten (`cq:ChildEditorConfig`) de eigenschappen definiëren:

   * Naam: `type`.
   * Waarde: de naam van de geregistreerde interne editor, bijvoorbeeld `image` en `text`.

   * Naam: `title`.
   * Waarde: de titel die wordt weergegeven in de keuzelijst met componenten van de beschikbare editors. Bijvoorbeeld: `Image` en `Text`.

### Aanvullende configuratie voor Rich Text Editors {#additional-configuration-for-rich-text-editors}

De configuratie voor veelvoudige Rich Text Editors is lichtjes verschillend aangezien u elke individuele instantie van RTE afzonderlijk kunt vormen. Zie voor meer informatie [vormen de Rich Text Editor](/help/sites-administering/rich-text-editor.md). Om veelvoudige RTEs te hebben creeer een configuratie voor elke op zijn plaats RTE. Adobe raadt u aan het nieuwe configuratieknooppunt onder te maken `cq:InplaceEditingConfig` aangezien elke individuele RTE een verschillende configuratie kan hebben. Onder de nieuwe knoop creeert elke individuele configuratie van RTE.

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
>Voor RTE geldt echter dat `configPath` eigenschap wordt ondersteund wanneer de component slechts één instantie van een teksteditor (bewerkbaar subgebied) bevat. Dit gebruik van `configPath` wordt verstrekt om achterwaartse verenigbaarheid met oudere gebruikersinterfacedialogen van de component te steunen.

>[!CAUTION]
>
>Noem niet de knoop van de configuratie RTE als `config`. Anders, zijn de configuraties RTE beschikbaar voor slechts de beheerders en niet voor de gebruikers in de groep `content-author`.

## Codevoorbeelden {#code-samples}

U kunt de code van deze pagina vinden op [aem-authoring-hybrideditors-project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors). U kunt het volledige project downloaden als [een ZIP-archief](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors/archive/master.zip).

## Een interne editor toevoegen {#add-an-in-place-editor}

Zie het document voor algemene informatie over het toevoegen van een interne editor [paginaontwerp aanpassen](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor).

>[!MORELIKETHIS]
>
>* [Rich Text Editor in Experience Manager configureren](/help/sites-administering/rich-text-editor.md).
