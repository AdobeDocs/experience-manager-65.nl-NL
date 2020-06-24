---
title: Markering
seo-title: Markering
description: Wanneer u ontwerpt, gebruikt de inhoudsfragmenteditor markeringssyntaxis, zodat u gemakkelijk inhoud kunt schrijven.
seo-description: Wanneer u ontwerpt, gebruikt de inhoudsfragmenteditor markeringssyntaxis, zodat u gemakkelijk inhoud kunt schrijven.
uuid: afcbf82f-3a75-4491-9172-706188db65bb
contentOwner: Alison Heimoz
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: content-fragments
content-type: reference
discoiquuid: b193f28c-46c2-4eab-bbb8-578530f80ba5
docset: aem65
translation-type: tm+mt
source-git-commit: afed13a2f832b91d0df825d1075852cc84443646
workflow-type: tm+mt
source-wordcount: '540'
ht-degree: 4%

---


# Markering{#markdown}

Wanneer u [creeert](content-fragments-variations.md#authoring-your-content), gebruikt de redacteur van het inhoudsfragment *prijsverhogingssyntaxis* om u toe te staan om inhoud gemakkelijk te schrijven:

![markeringseditor](/help/assets/content-fragments/assets/cfm-6420-08.png)

U kunt het volgende definiëren:

* [Kop](/help/assets/content-fragments/content-fragments-markdown.md#heading-notation)
* [Alinea&#39;s en regeleinden](/help/assets/content-fragments/content-fragments-markdown.md#paragraphs-and-line-breaks)
* [Koppelingen](/help/assets/content-fragments/content-fragments-markdown.md#links)
* [Afbeeldingen](/help/assets/content-fragments/content-fragments-markdown.md#images)
* [Aanhalingstekens blokkeren](/help/assets/content-fragments/content-fragments-markdown.md#block-quotes)
* [Lijsten](/help/assets/content-fragments/content-fragments-markdown.md#lists)
* [Nadruk](/help/assets/content-fragments/content-fragments-markdown.md#emphasis)
* [Codeblokken](/help/assets/content-fragments/content-fragments-markdown.md#code-blocks)
* [Backslash-escape](/help/assets/content-fragments/content-fragments-markdown.md#backslash-escapes)

## Kop {#heading-notation}

Een koptekst maken door een hashtag (#) vóór de kop te plaatsen. Eén hashtag (#) wordt gebruikt voor een H1-, twee hash-tags (##) voor een H2-tag, enzovoort. U kunt maximaal 6 hashtags gebruiken. Bijvoorbeeld:

    `## This is an H2`

    `### This is an H3`

    `###### This is a H6`

U kunt desgewenst een H1 maken door de tekst in gelijke tekens te onderstrepen en een H2 te maken door de tekst in mintekens te onderstrepen. Bijvoorbeeld:

    `This is an H1`

    `=============`

    `This is an H2`

    `-------------`

## Alinea&#39;s en regeleinden {#paragraphs-and-line-breaks}

Een alinea is gewoon een of meer opeenvolgende tekstregels, gescheiden door een of meer lege regels. Een lege regel is een regel die alleen spaties of tabs bevat. Normale alinea&#39;s mogen niet met spaties of tabs worden ingesprongen.

Een regeleinde wordt gemaakt door een regel met twee of meer spaties te eindigen en een regeleinde.

## Koppelingen {#links}

U kunt inline-koppelingen en verwijzingskoppelingen maken.

In beide stijlen wordt de koppelingstekst gescheiden door vierkante haakjes `[]`.

Dit zijn voorbeelden van inlineverbindingen:

    `This is [an example](https://example.com/ "Title") inline link.`

    `This is [an example of an email link](emailto:myaddress@mydomain.info)`

    `[This link](https://example.net/) has no title attribute.`

Een verwijzingskoppeling heeft de volgende syntaxis:

    `Hey you should [checkout][0] this [cool thing][wiki] that I [made][].`

    `[0]: https://www.google.ca`

    `[wiki]: https://www.wikipedia.org`

    `[made]: https://www.stackoverflow.com`

## Afbeeldingen {#images}

De syntaxis voor afbeeldingen lijkt op die voor koppelingen. U kunt inline-afbeeldingen en afbeeldingen waarnaar wordt verwezen maken.

Een inline-afbeelding heeft bijvoorbeeld de volgende syntaxis:

    `![Alt text](/path/to/img.jpg)`

    `![Alt text](/path/to/img.jpg "Optional title")`

De syntaxis bevat:

* Een uitroepteken: !;
* gevolgd door een set vierkante haakjes die de tekst van het alt-kenmerk voor de afbeelding bevat;
* gevolgd door een reeks haakjes, die de URL of het pad naar de afbeelding bevatten, en een optioneel titelkenmerk dat tussen dubbele of enkele aanhalingstekens staat.

Een afbeelding in de stijl Referentie heeft de volgende syntaxis:

    `![Alt text][id]`

Waarbij &quot;id&quot; de naam van een gedefinieerde afbeeldingsverwijzing is. Verwijzingen naar afbeeldingen worden gedefinieerd met dezelfde syntaxis als verwijzingen naar koppelingen:

    `[id]: url/to/image "Optional title attribute"`

## Aanhalingstekens blokkeren {#block-quotes}

U kunt tekst aanhalen door het symbool > vóór de tekst toe te voegen. Bijvoorbeeld:

    `>This is block quotes`

    `>asdhfjlkasdhlf`

    `>asdfahsdlfasdfj`

U kunt geneste blokaanhalingstekens hebben. Bijvoorbeeld:

    `> This is the first level of quoting.`

    `>`

        `>> This is nested blockquote.`

    `>`

    `> Back to the first level.`

## Lijsten {#lists}

U kunt zowel geordende als ongeordende lijsten maken.

Als u een niet-geordende lijst wilt maken, gebruikt u de optie &amp;ast; vóór de items in de lijst. Bijvoorbeeld:

    `* item in list`

    `* item in list`

    `* item in list`

Als u een geordende lijst wilt maken, voegt u de nummers toe, gevolgd door een punt, vóór elk item in de lijst. Bijvoorbeeld:

    `1. First item in list.`

    `2. Second item in list.`

    `3. Third item in list.`

## Nadruk {#emphasis}

U kunt cursieve of vette opmaak toevoegen aan uw tekst.

U kunt als volgt cursief maken:

    `*single asterisks*`

    `_single underscores_`

    `Keyboard shortcut: Ctrl-I (Cmd-I)`

U kunt tekst als volgt vet maken:

    `**double asterisks**`

    `__double underscores__`

    `Keyboard shortcut: Ctrl-B (Cmd-B)`

Als u een reeks codes wilt aangeven, plaatst u deze tussen aanhalingstekens (`). In tegenstelling tot een vooraf opgemaakt codeblok geeft een codebereik code binnen een normale alinea aan.

Bijvoorbeeld:

    ``Use the `printf()` function.``

## Codeblokken {#code-blocks}

Codeblokken worden doorgaans gebruikt om broncode te illustreren. U kunt codeblokken maken door de code in te springen met een tab of een minimum van 4 spaties. Bijvoorbeeld:

    `This is a normal paragraph.`

        `This is a code block.`

## Backslash-escape {#backslash-escapes}

Met backslash-escape kunt u letterlijke tekens genereren die een speciale betekenis hebben in de opmaaksyntaxis. Als u bijvoorbeeld een woord met letterlijke sterretjes wilt omringen (in plaats van een HTML-tag), kunt u als volgt backslashes vóór de sterretjes gebruiken:

    `\\*literal asterisks\\*`

Backslash-escapes zijn beschikbaar voor de volgende tekens:

    `\ backslash`

    ` backtick

    `* asterisk`

    `_ underscore`

    `{} curly braces`

    `[] square brackets`

    `() parentheses`

    `# hash mark`

    `+ plus sign`

    `- minus sign (hyphen)`

    `. dot`
