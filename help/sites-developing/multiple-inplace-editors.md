---
title: Vorm RTE voor veelvoudige op zijn plaats redacteurs.
description: Creeer veelvoudige op zijn plaats redacteurs in Adobe Experience Manager door de Rich Redacteur van de Tekst te vormen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: e49411a99a80e91c983afc103a8ea826e75569b8
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 2%

---


# Meerdere lokale editors configureren {#configure-multiple-in-place-editors}

U kunt de Rich Text Editor in Adobe Experience Manager zodanig configureren dat deze meerdere op zijn plaats geplaatste editors heeft. Wanneer gevormd kunt u de aangewezen inhoud selecteren en de aangewezen redacteur openen.

![Een specifieke interne editor](assets/rte-inplace-editor.png)

## Meerdere editors configureren {#configure-multiple-editors}

Om veelvoudige op zijn plaats redacteurs toe te laten is de structuur van een `cq:InplaceEditingConfig` knooptype verbeterd met de definitie van `cq:ChildEditorConfig` knooptype.

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

1. Definieer in het knooppunt `cq:inplaceEditing` (van het type `cq:InplaceEditingConfig`) de volgende eigenschappen:

   * Naam:`editorType`
   * Type: `String`
   * Waarde: `hybrid`

1. Onder dit knooppunt maakt u een knooppunt:

   * Naam: `cq:ChildEditors`
   * Type: `nt:unstructured`

1. Onder `cq:childEditors` knoop, creeer een knoop voor elke op zijn plaats redacteur:

   * Naam: De naam van elke knoop is de naam van het bezit dat het vertegenwoordigt, zoals het geval met dalingsdoelstellingen is. Bijvoorbeeld `image` en `text`.
   * Type: `cq:ChildEditorConfig`
   >[!NOTE]
   >
   >Er is een correlatie tussen de gedefinieerde neerzetdoelen en de onderliggende editors. De naam van de `cq:ChildEditorConfig` knoop wordt beschouwd als dalingsdoel identiteitskaart, voor gebruik als parameter aan de geselecteerde kindredacteur. Als het bewerkbare subgebied bijvoorbeeld geen neerzetdoel heeft in een tekstcomponent, wordt de naam van de onderliggende editor nog steeds beschouwd als een id om het overeenkomende bewerkbare gebied te identificeren.

1. Definieer op elk van deze knooppunten (`cq:ChildEditorConfig`) de eigenschappen:

   * Naam: `type`.
   * Waarde: de naam van de geregistreerde interne editor; bijvoorbeeld `image` en `text`.

   * Naam: `title`.
   * Waarde: De titel die wordt weergegeven in de keuzelijst met componenten van de beschikbare editors. Bijvoorbeeld `Image` en `Text`.

### Aanvullende configuratie voor Rich Text Editors {#additional-configuration-for-rich-text-editors}

De configuratie voor veelvoudige Rich Text Editors is lichtjes verschillend aangezien u elke individuele instantie van RTE afzonderlijk kunt vormen. Voor details, zie de Rich [Redacteur](/help/sites-administering/rich-text-editor.md)van de Tekst vormen. Om veelvoudige RTEs te hebben creeer een configuratie voor elke op zijn plaats RTE. Adobe raadt u aan het nieuwe configuratieknooppunt te maken, `cq:InplaceEditingConfig` aangezien elke afzonderlijke RTE een andere configuratie kan hebben. Onder de nieuwe knoop creeert elke individuele configuratie van RTE.

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
>Voor RTE wordt de `configPath` eigenschap echter ondersteund wanneer de component slechts één instantie van een teksteditor (bewerkbaar subgebied) bevat. Dit gebruik van `configPath` wordt verstrekt om achterwaartse verenigbaarheid met oudere gebruikersinterfacedialogen van de component te steunen.

>[!CAUTION]
>
>Noem niet de de configuratieknoop van RTE zoals `config`. Anders, zijn de configuraties RTE beschikbaar voor slechts de beheerders en niet voor de gebruikers in de groep `content-author`.

## Codevoorbeelden {#code-samples}

U kunt de code van deze pagina op [aem-authoring-hybrideditors project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors)vinden. U kunt het volledige project downloaden als [een ZIP-archief](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors/archive/master.zip).

## Een interne editor toevoegen {#add-an-in-place-editor}

Voor algemene informatie over het toevoegen van een op plaats-redacteur zie het document pagina [aanpassen creatie](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor).

>[!MORELIKETHIS]
>
>* [Rich Text Editor configureren in Experience Manager](/help/sites-administering/rich-text-editor.md).

