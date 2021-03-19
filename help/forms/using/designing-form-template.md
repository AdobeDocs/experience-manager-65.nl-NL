---
title: Formuliersjablonen ontwerpen voor HTML5-formulieren
seo-title: Formuliersjablonen ontwerpen voor HTML5-formulieren
description: AEM Forms biedt rendering van XFA-formuliersjablonen naar HTML5-indeling. Formulierontwerpers kunnen formuliersjablonen ontwerpen met Designer en de HTML5-renderingmogelijkheden gebruiken.
seo-description: AEM Forms biedt rendering van XFA-formuliersjablonen naar HTML5-indeling. Formulierontwerpers kunnen formuliersjablonen ontwerpen met Designer en de HTML5-renderingmogelijkheden gebruiken.
uuid: 4f6b7231-4479-400a-adcd-c68064f06b4e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: f2e9dbe4-e210-41f3-8878-2fc4d166e63c
docset: aem65
feature: Mobile Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---


# Formuliersjablonen ontwerpen voor HTML5-formulieren{#designing-form-templates-for-html-forms}

De HTML5-formuliercomponent in AEM biedt rendering van XFA-formuliersjablonen naar HTML5-indeling. Formulierontwerpers kunnen formuliersjablonen ontwerpen met behulp van [Forms Designer](https://www.adobe.com/go/learn_aemforms_designer_63) en de mogelijkheid van HTML5-uitvoering gebruiken. Deze formuliersjablonen kunnen samen met hun elementen in AEM opslagplaats, bestandssysteem of beschikbaar worden gemaakt via http. Als u echter van plan bent uw formulieren te beheren met Forms Manager, moeten de sjablonen en middelen zich in de AEM-opslagplaats bevinden.

Hoewel HTML5-formulieren grotendeels overeenkomen met het gedrag van de PDF forms, zijn er bepaalde functies in beide indelingen die niet van toepassing zijn op de andere indeling. De manier waarop streepjescodes worden toegepast op een PDF-formulier in Adobe Reader verschilt bijvoorbeeld per mobiel formulier of de manier waarop een formulier digitaal wordt ondertekend, verschilt ook per indeling. Zie [Verschillen in functies tussen HTML5-formulieren en PDF forms](../../forms/using/feature-differentiation-html5-forms-pdf-forms.md) voor meer informatie over dergelijke variaties.

Raadpleeg de volgende aanbevolen procedures en richtlijnen voor het ontwerpen van formulieren die in beide indelingen werken voor algemene XFA-functies.

## Aanbevolen werkwijzen {#best-practices}

De meeste stappen rondom het ontwerpen van een formuliersjabloon, zoals schemabindingen of het schrijven van formulierlogica, zijn hetzelfde. Wegens inherente verschillen tussen het teruggeven en scripting motor van een dikke cliënt zoals Adobe Reader en browser-gebaseerde vormen, zijn er sommige die aanbevelingen in [beste praktijken](/help/forms/using/design-accessible-html5-forms.md) artikel worden beschreven. Met deze tips kunt u formuliersjablonen ontwerpen die in beide indelingen naar behoren werken.

### Mogelijkheden in AEM Forms Designer voor HTML5 Forms {#capabilities-in-aem-forms-designer-for-html-forms}

#### HTML {#preview-html} voorvertonen

Het tabblad Voorbeeld-HTML wordt in de ontwerpmodus toegevoegd zodat formulierontwerpers tijdens het ontwerpproces formulieren in HTML5-indeling kunnen bekijken. Zie [HTML voorvertonen](../../forms/using/preview-xdp-forms-html.md) voor meer informatie over het in- en uitschakelen van deze functie in AEM Forms Designer.

#### Krabbelhandtekening {#scribble-signature}

Het belangrijkste doel voor HTML5-formulieren is aanraakapparaten. Daarom wordt een nieuwe controle van de krabbelhandtekening toegevoegd in de Ontwerper van AEM Forms. U kunt op het besturingselement voor krabbelhandtekeningen klikken of het besturingselement voor krabbelhandtekeningen slepen en neerzetten op uw formuliersjabloon en het configureren. Het wordt weergegeven als een krabbelveld in HTML5-uitvoering en kan worden gebruikt om een handtekening te krabbelen op aanraakapparaten. Op desktopcomputers kan het als krabbelveld worden gebruikt met de muis. Zie [XFA-scriptveld](../../forms/using/scribble-signature.md) voor meer informatie over het gebruik van deze functie.

![4](assets/4.png)

#### RTF-indeling {#rich-text-format}

U kunt een tekstveld omzetten in een RTF-veld. Er wordt een lijst met opmaakopties toegevoegd aan het tekstveld. Als u wilt converteren, opent u Forms Designer en tikt u op het tekstveld in **[!UICONTROL Design View]**. Selecteer op het tabblad **[!UICONTROL Field]** **[!UICONTROL Rich Text]** in de vervolgkeuzelijst **[!UICONTROL Field Format]**. Wanneer het XFA-formulier nu wordt weergegeven als een HTML5-formulier, wordt het veld weergegeven als een RTF-veld. Tik ![Maximaliseer](assets/maximize_icon.svg) om extra opmaakopties weer te geven.
