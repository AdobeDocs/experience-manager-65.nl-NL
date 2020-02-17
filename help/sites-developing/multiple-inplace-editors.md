---
title: Meerdere lokale editors configureren
seo-title: Meerdere lokale editors configureren
description: Het is mogelijk om uw component te vormen zodat het veelvoudige op zijn plaats redacteurs heeft
seo-description: Het is mogelijk om uw component te vormen zodat het veelvoudige op zijn plaats redacteurs heeft
uuid: 4abbfcd5-fe1b-4c02-b115-97db20e60e1e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
discoiquuid: 0fac1e4a-f08f-4c46-b070-cb1d5a05b6e0
translation-type: tm+mt
source-git-commit: b3e1493811176271ead54bae55b1cd0cf759fe71

---


# Meerdere lokale editors configureren{#configuring-multiple-in-place-editors}

U kunt de component zo configureren dat deze meerdere interne editors heeft binnen de interface met aanraakbediening.

Wanneer gevormd kunt u de aangewezen inhoud selecteren en de aangewezen redacteur openen. Bijvoorbeeld:

![chlimage_1-8](assets/chlimage_1-8a.png)

## Meerdere editors configureren {#configuring-multiple-editors}

Om veelvoudige op zijn plaats redacteurs toe te laten is de structuur van een `cq:InplaceEditingConfig` knooptype verbeterd met de definitie van `cq:ChildEditorConfig` knooptype.

Bijvoorbeeld:

```
   /**
       * Configures inplace editing of a component.
       *
       * @prop active true to activate inplace editing for the component
       * @prop editorType ID of inplace editor to use
       * @prop cq:childEditors collection of {@link cq:ChildEditorConfig} nodes.
       * @prop configPath path to editor's config (optional)
       * @node config editor's config (used if no configPath is specified; optional)
     */
    [cq:InplaceEditingConfig] > nt:unstructured
      - active (boolean)
      - editorType (string)
      + cq:childEditors (nt:base) = nt:unstructured
      - configPath (string)
      + config (nt:unstructured) = nt:unstructured

    /**
      * Configures one child editor for a subcomponent. The name of the this node will
      * be used as DD id.
      *
      * @prop type type of the inline editor. eg: ["image"]
      * @prop title totle od the inline editor
      * @prop icon icon to represent the inline editor
    */
    [cq:ChildEditorConfig] > nt:unstructured
      orderable
      - type (string)
      - title (string)
```

Meerdere editors configureren:

1. Definieer de eigenschap op het knooppunt `cq:inplaceEditing` (van het type `cq:InplaceEditingConfig`):

   * Naam:`editorType`
   * Type: `String`
   * Waarde: `hybrid`

1. Onder dit knooppunt maakt u een nieuw knooppunt:

   * Naam: `cq:ChildEditors`
   * Type: `nt:unstructured`

1. Onder het `cq:childEditors` knooppunt maakt u een nieuw knooppunt voor elke interne editor:

   * Naam: De naam van elk knooppunt moet de naam zijn van de eigenschap die het vertegenwoordigt (zoals bij neerzetdoelen). Bijvoorbeeld, `image`, `text`.
   * Type: cq: `ChildEditorConfig`
   >[!NOTE]
   >
   >Er is een correlatie tussen de gedefinieerde neerzetdoelen en de onderliggende editors. De naam van de `cq:ChildEditorConfig` knoop zal worden beschouwd als om dalingsdoel ID, voor gebruik als parameter aan de geselecteerde kindredacteur te zijn. Als het bewerkbare subgebied geen neerzetdoel heeft (bijvoorbeeld zoals bij een tekstcomponent), wordt de naam van de onderliggende editor nog steeds beschouwd als een id om het overeenkomende bewerkbare gebied te identificeren.

1. Definieer op elk van deze knooppunten ( `cq:ChildEditorConfig`) de eigenschappen:

   * Naam: `type`
   * Waarde: naam van de geregistreerde ondergeschikte; bijvoorbeeld: `image`, `text`

   * Naam: `title`
   * Waarde: de titel die u in de lijst van de componentenselectie (van beschikbare redacteurs) wilt tonen; bijvoorbeeld: `Image`, `Text`

### Aanvullende configuratie voor Rich Text Editors {#additional-configuration-for-rich-text-editors}

De configuratie voor veelvoudige Rich Text Editors is lichtjes verschillend aangezien u elke individuele instantie van RTE afzonderlijk kunt vormen.

>[!NOTE]
>
>Voor meer details zie het [Vormen van de Rich Teksteditor](/help/sites-administering/rich-text-editor.md).

Om veelvoudige RTEs te hebben hebt u een configuratie voor elk op zijn plaats RTE nodig:

* Onder `cq:InplaceEditingConfig` definieert u een `config` knooppunt.

   * Onder de `config` knoop bepaalt elke individuele configuratie van RTE.

```xml
    texttext
        cq:dialog
        cq:editConfig
            cq:inplaceEditing
                cq:childEditors
                    config
                        text1
                            rtePlugins
                        text2
                            rtePlugins
```

>[!NOTE]
>
>De geadviseerde beste praktijken moeten de `config` knoop onder bepalen `cq:InplaceEditingConfig` aangezien elke individuele RTE een verschillende configuratie kan hebben.
>
>Voor RTE wordt de `configPath` eigenschap echter ondersteund wanneer de component slechts één instantie van een teksteditor (bewerkbaar subgebied) bevat. Dit gebruik van `configPath` wordt verstrekt om achterwaartse verenigbaarheid met oudere dialogen UI van de component te steunen.

## Codevoorbeelden {#code-samples}

**CODE VOOR GITHUB**

U kunt de code van deze pagina op GitHub vinden

* [Open aem-authoring-hybrideditors-project op GitHub](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors)
* Het project downloaden als [ZIP-bestand](https://github.com/Adobe-Marketing-Cloud/aem-authoring-hybrideditors/archive/master.zip)

## Een op plaats-editor toevoegen {#adding-an-in-place-editor}

Voor algemene informatie over het toevoegen van een interne editor raadpleegt u het document [Paginaontwerp](/help/sites-developing/customizing-page-authoring-touch.md#add-new-in-place-editor)aanpassen.
