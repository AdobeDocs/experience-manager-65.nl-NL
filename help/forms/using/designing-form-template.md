---
title: Formuliersjablonen ontwerpen voor HTML5-formulieren
seo-title: Formuliersjablonen ontwerpen voor HTML5-formulieren
description: Met AEM Forms wordt XFA-formuliersjablonen weergegeven in de HTML5-indeling. Formulierontwerpers kunnen formuliersjablonen ontwerpen met Designer en de HTML5-renderingmogelijkheden gebruiken.
seo-description: Met AEM Forms wordt XFA-formuliersjablonen weergegeven in de HTML5-indeling. Formulierontwerpers kunnen formuliersjablonen ontwerpen met Designer en de HTML5-renderingmogelijkheden gebruiken.
uuid: 4f6b7231-4479-400a-adcd-c68064f06b4e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: f2e9dbe4-e210-41f3-8878-2fc4d166e63c
docset: aem65
translation-type: tm+mt
source-git-commit: 56c6cfd437ef185336e81373bd5f758205b96317

---


# Formuliersjablonen ontwerpen voor HTML5-formulieren{#designing-form-templates-for-html-forms}

De component HTML5-formulieren in AEM biedt de rendering van XFA-formuliersjablonen naar HTML5-indeling. Formulierontwerpers kunnen formuliersjablonen ontwerpen met [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) en de HTML5-renderingmogelijkheden gebruiken. Deze formuliersjablonen kunnen samen met hun elementen in een AEM-opslagruimte, in een bestandssysteem of via http worden weergegeven. Als u uw formulieren echter wilt beheren met Forms Manager, moeten de sjablonen en middelen zich in de AEM-opslagplaats bevinden.

Hoewel HTML5-formulieren grotendeels overeenkomen met de werking van PDF-formulieren, zijn er bepaalde functies in beide indelingen die niet van toepassing zijn op de andere indeling. De manier waarop streepjescodes in Adobe Reader op een PDF-formulier worden toegepast, verschilt bijvoorbeeld per mobiel formulier of de manier waarop een formulier digitaal wordt ondertekend, verschilt ook per indeling. Zie [Functieverschil tussen HTML5-formulieren en PDF-formulieren](../../forms/using/feature-differentiation-html5-forms-pdf-forms.md)voor meer informatie over dergelijke variaties.

Raadpleeg de volgende aanbevolen procedures en richtlijnen voor het ontwerpen van formulieren die in beide indelingen werken voor algemene XFA-functies.

## Aanbevolen procedures {#best-practices}

De meeste stappen rondom het ontwerpen van een formuliersjabloon, zoals schemabindingen of het schrijven van formulierlogica, zijn hetzelfde. Vanwege inherente verschillen tussen rendering en scripting engine van een dikke client, zoals Adobe Reader, en browserformulieren, worden echter enkele aanbevelingen beschreven in het artikel met [aanbevolen procedures](/help/forms/using/design-accessible-html5-forms.md) . Met deze tips kunt u formuliersjablonen ontwerpen die in beide indelingen naar behoren werken.

### Mogelijkheden in AEM Forms Designer voor HTML5-formulieren {#capabilities-in-aem-forms-designer-for-html-forms}

#### HTML voorvertonen {#preview-html}

Het tabblad Voorbeeld-HTML wordt in de ontwerpmodus toegevoegd zodat formulierontwerpers tijdens het ontwerpproces formulieren in HTML5-indeling kunnen bekijken. Zie [Voorbeeld-HTML](../../forms/using/preview-xdp-forms-html.md)voor meer informatie over het inschakelen en configureren van deze functie in AEM Forms Designer.

#### Krabbelhandtekening {#scribble-signature}

Het belangrijkste doel voor HTML5-formulieren is aanraakapparaten. Daarom wordt een nieuwe controle van de krabbelhandtekening toegevoegd in de Ontwerper van de Vormen AEM. U kunt op het besturingselement voor krabbelhandtekeningen klikken of het besturingselement voor krabbelhandtekeningen slepen en neerzetten op uw formuliersjabloon en het configureren. Het wordt weergegeven als een krabbelveld in HTML5-uitvoering en kan worden gebruikt om een handtekening te krabbelen op aanraakapparaten. Op desktopcomputers kan het als krabbelveld worden gebruikt met de muis. Zie [XFA-scriptveld](../../forms/using/scribble-signature.md)voor meer informatie over het gebruik van deze functie.

![4](assets/4.png)

#### RTF-indeling {#rich-text-format}

U kunt een tekstveld omzetten in een RTF-veld. Er wordt een lijst met opmaakopties toegevoegd aan het tekstveld. Als u wilt converteren, opent u Formulierontwerper en tikt u op het tekstveld in de **[!UICONTROL ontwerpweergave]**. Selecteer op het tabblad **[!UICONTROL Veld]** de optie **[!UICONTROL RTF]** in de vervolgkeuzelijst **[!UICONTROL Veldindeling]** . Wanneer het XFA-formulier nu wordt weergegeven als een HTML5-formulier, wordt het veld weergegeven als een RTF-veld. Tik op ![Maximaliseren](assets/maximize_icon.svg) om extra opmaakopties weer te geven.
