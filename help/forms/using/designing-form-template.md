---
title: Formuliersjablonen ontwerpen voor HTML5-formulieren
description: AEM Forms kan XFA-formuliersjabloon renderen naar HTML5-indeling. Formulierontwerpers kunnen formuliersjablonen ontwerpen met behulp van Designer en gebruikmaken van de5-uitvoermogelijkheden voor HTML.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms,Mobile Forms
exl-id: 7c8d501f-c953-495e-8bac-1f66fd99c783
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '473'
ht-degree: 0%

---

# Formuliersjablonen ontwerpen voor HTML5-formulieren{#designing-form-templates-for-html-forms}

De HTML5-formuliercomponent in AEM kan XFA-formuliersjabloon renderen naar HTML5-indeling. De ontwerpers van de vorm kunnen vormmalplaatjes ontwerpen gebruikend [ Forms Designer ](https://www.adobe.com/go/learn_aemforms_designer_63) en het HTML5 vertoningsvermogen gebruiken. Deze formuliersjablonen kunnen samen met hun elementen in AEM opslagplaats, bestandssysteem of beschikbaar worden gemaakt via http. Als u echter van plan bent uw formulieren te beheren met Forms Manager, moeten de sjablonen en middelen zich in de AEM-opslagplaats bevinden.

Hoewel HTML5-formulieren grotendeels overeenkomen met het gedrag van de PDF forms, zijn er bepaalde functies in beide indelingen die niet van toepassing zijn op de andere indeling. De manier waarop streepjescodes worden toegepast op een PDF-formulier in Adobe Reader, verschilt bijvoorbeeld per mobiel formulier of de manier waarop een formulier digitaal wordt ondertekend, verschilt ook per indeling. Voor meer informatie over dergelijke variaties, zie [ verschil van de Eigenschap tussen HTML5 vormen en PDF forms ](../../forms/using/feature-differentiation-html5-forms-pdf-forms.md).

Raadpleeg de volgende aanbevolen procedures en richtlijnen voor het ontwerpen van formulieren die in beide indelingen werken voor algemene XFA-functies.

## Aanbevolen procedures {#best-practices}

De meeste stappen rondom het ontwerpen van een formuliersjabloon, zoals schemabindingen of het schrijven van formulierlogica, zijn hetzelfde. Nochtans, wegens inherente verschillen tussen het teruggeven en scripting motor van een dikke cliënt zoals Adobe Reader en op browser-gebaseerde vormen, zijn er sommige die aanbevelingen in het [ worden beschreven beste praktijken ](/help/forms/using/design-accessible-html5-forms.md) artikel. Met deze tips kunt u formuliersjablonen ontwerpen die in beide indelingen naar behoren werken.

### Mogelijkheden in AEM Forms Designer voor HTML5 Forms {#capabilities-in-aem-forms-designer-for-html-forms}

#### Voorvertoning HTML {#preview-html}

Het tabblad Voorbeeld-HTML wordt in de ontwerpmodus toegevoegd, zodat formulierontwerpers tijdens het ontwerpproces een voorbeeld van formulieren in de HTML-indeling kunnen bekijken. Voor meer informatie over om dit vermogen in AEM Forms Designer toe te laten en te vormen, zie [ HTML ](../../forms/using/preview-xdp-forms-html.md) van de Voorproef.

#### Krabbelhandtekening {#scribble-signature}

Het belangrijkste doel voor HTML5-formulieren is aanraakapparaten. Daarom wordt er een nieuw besturingselement voor krabbelhandtekeningen toegevoegd in AEM Forms Designer. U kunt op het besturingselement voor krabbelhandtekeningen klikken of het besturingselement voor krabbelhandtekeningen slepen en neerzetten op uw formuliersjabloon en het configureren. Het wordt weergegeven als een krabbelveld in HTML 25-uitvoering en kan worden gebruikt om een handtekening te krabbelen op aanraakapparaten. Op desktopcomputers kan het als krabbelveld worden gebruikt met de muis. Voor meer informatie over hoe te om deze eigenschap te gebruiken, zie [ XFA het KrabbelGebied ](../../forms/using/scribble-signature.md).

![ 4 ](assets/4.png)

#### RTF-indeling {#rich-text-format}

U kunt een tekstveld omzetten in een RTF-veld. Er wordt een lijst met opmaakopties toegevoegd aan het tekstveld. Open de Forms Designer en selecteer het tekstveld in **[!UICONTROL Design View]** om het te converteren. Selecteer op het tabblad **[!UICONTROL Field]** **[!UICONTROL Rich Text]** in de vervolgkeuzelijst **[!UICONTROL Field Format]** . Wanneer het XFA-formulier nu wordt weergegeven als een HTML5-formulier, wordt het veld weergegeven als een RTF-veld. Selecteer ![ maximaliseren ](assets/maximize_icon.svg) om extra het formatteren opties te bekijken.
