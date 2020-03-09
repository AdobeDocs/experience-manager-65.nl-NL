---
title: Formuliersjablonen ontwerpen voor HTML5-formulieren
seo-title: Formuliersjablonen ontwerpen voor HTML5-formulieren
description: De aanbiedingen die van de Vormen van AEM XFA vormmalplaatje aan het formaat van HTML5 teruggeven. De ontwerpers van de vorm kunnen vormmalplaatjes ontwerpen gebruikend Ontwerper en het HTML5 renditievermogen gebruiken.
seo-description: De aanbiedingen die van de Vormen van AEM XFA vormmalplaatje aan het formaat van HTML5 teruggeven. De ontwerpers van de vorm kunnen vormmalplaatjes ontwerpen gebruikend Ontwerper en het HTML5 renditievermogen gebruiken.
uuid: 4f6b7231-4479-400a-adcd-c68064f06b4e
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: f2e9dbe4-e210-41f3-8878-2fc4d166e63c
docset: aem65
translation-type: tm+mt
source-git-commit: 147c50adb02b48be8e3aba760dbac309ab49badf

---


# Formuliersjablonen ontwerpen voor HTML5-formulieren{#designing-form-templates-for-html-forms}

De HTML5 vormencomponent in AEM biedt het teruggeven van XFA vormmalplaatje aan formaat HTML5 aan. De ontwerpers van de vorm kunnen vormmalplaatjes ontwerpen gebruikend de Ontwerper [van](https://www.adobe.com/go/learn_aemforms_designer_63) Vormen en het HTML5 renditievermogen gebruiken. Deze vormmalplaatjes, samen met hun activa, kunnen in bewaarplaats AEM, dossiersysteem verblijven, of via http worden blootgesteld. Nochtans, als u van plan bent om uw vormen te beheren gebruikend de Manager van Vormen, zouden de malplaatjes en de activa in de bewaarplaats moeten verblijven AEM.

Hoewel de vormen HTML5 het gedrag van de vormen PDF in grote mate aanpassen, zijn er sommige eigenschappen in beide formaten die niet op het andere formaat van toepassing zijn. Bijvoorbeeld, hoe de streepjescodes worden toegepast op een vorm PDF in de Lezer van Adobe varieert van een Mobiele vorm of hoe een vorm digitaal wordt ondertekend varieert ook tussen de formaten. Voor meer informatie over dergelijke variaties, zie de differentiatie van de [Eigenschap tussen HTML5 vormen en Vormen](../../forms/using/feature-differentiation-html5-forms-pdf-forms.md)PDF.

Voor gemeenschappelijke eigenschappen XFA, zie de volgende beste praktijken en de richtlijnen om een vorm te ontwerpen die in beide formaten werkt.

## Beste praktijken {#best-practices}

De meeste stappen rond het ontwerpen van een vormmalplaatje, zoals schemabanden of het schrijven van vormlogica zijn het zelfde. Nochtans, wegens inherente verschillen tussen het teruggeven van en het scripting van motor van een dikke cliënt zoals de Lezer van Adobe en op browser-gebaseerde vormen, zijn er sommige aanbevelingen die in het [beste praktijkartikel](/help/forms/using/design-accessible-html5-forms.md) worden beschreven. Deze beste praktijken helpen u vormmalplaatjes ontwerpen om te werken zoals verwacht in beide formaten.

### Mogelijkheden in de Ontwerper van Vormen AEM voor de Vormen van HTML5 {#capabilities-in-aem-forms-designer-for-html-forms}

#### HTML bekijken {#preview-html}

Het lusje van HTML van de Voorproef wordt toegevoegd op de wijze van het Ontwerp voor de Ontwerpers van de Vorm aan voorproefvormen in formaat HTML5 tijdens het ontwerpproces. Voor meer informatie over om dit vermogen in de Ontwerper van Vormen toe te laten en te vormen AEM, zie HTML [van de](../../forms/using/preview-xdp-forms-html.md)Voorproef.

#### Scribble-handtekening {#scribble-signature}

Het belangrijkste doel voor HTML5 vormen is aanrakingsapparaten. Daarom wordt een nieuwe gekrabbelde handtekeningscontrole toegevoegd in de Ontwerper van Vormen AEM. U kunt klikken of slepen-en-dalings de controle van de krabbelhandtekening op uw vormmalplaatje en het vormen. Het wordt teruggegeven als gekrabbel gebied in de renditie van HTML5 en kan worden gebruikt om handtekening op aanrakingsapparaten in te schrijven. Op Desktopmachines, kan het als krabbelgebied worden gebruikt gebruikend muiscontrole. Voor meer informatie over hoe te om deze eigenschap te gebruiken, zie het Gebied van de Geschiktheid van [XFA](../../forms/using/scribble-signature.md).

![4](assets/4.png)

#### Rich text Format {#rich-text-format}

Bepaal een rijk formaat van het tekstgebied voor het tekstgebied in de Ontwerper van Vormen om een lijst van het formatteren opties aan het gebied in de teruggegeven vorm toe te voegen HTML5. Om de montages toe te passen, tik het tekstgebied in de Mening **[!UICONTROL van het]** Ontwerp. In het **[!UICONTROL lusje van het Gebied]** , uitgezochte **[!UICONTROL Rijke Tekst]** van de drop-down lijst van het Formaat **[!UICONTROL van het]** Gebied. Het tekstgebied toont het formatteren opties wanneer teruggegeven in een vorm HTML5.

[Contact opnemen met ondersteuning](https://www.adobe.com/account/sign-in.supportportal.html)
