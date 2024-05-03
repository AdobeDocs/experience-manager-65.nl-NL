---
title: Standaardstijlen van HTML5-formulieren wijzigen
description: HTML5-formulierstijlen zijn gebaseerd op CSS. U kunt de standaardstijlen van het formulier wijzigen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
docset: aem65
feature: HTML5 Forms
exl-id: 4c84cfd1-50a4-416f-b4a5-7f2f4c7f10af
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '366'
ht-degree: 0%

---

# Standaardstijlen van HTML5-formulieren wijzigen{#changing-default-styles-of-html-forms}

HTML5-formulieren worden gegenereerd met HTML5-functies en de opmaak van het gegenereerde formulier wordt uitgevoerd met CSS. De standaardweergave van een HTML5-formulier is vergelijkbaar met de uitvoering van de PDF. Ontwikkelaars kunnen aangepaste CSS gebruiken om de standaardweergave van HTML5-formulieren te wijzigen.

Dit artikel biedt stapsgewijze informatie om de stijl van een HTML5-formulier te wijzigen en [Inleiding tot stijlen](/help/forms/using/css-styles.md) het artikel bevat gedetailleerde informatie over diverse opmaakaspecten van HTML5 - formulieren . Zorg ervoor dat u Inleiding aan stijlartikel leest alvorens stappen uit te voeren die in dit artikel worden vermeld.

De volgende twee afbeeldingen laten het verschil zien tussen de standaard en aangepaste stijlen.

![picture-002-small](assets/pictures-002-small.png)

## Uw formulieren opmaken {#style-your-forms}

1. **Een profiel kiezen om aangepaste stijlen toe te voegen**

   Heb toegang tot de interface CRX DE bij URL: **https://&lt;server>:&lt;port>/crx/de** en maak een profiel of kies een bestaand profiel. Zie voor informatie over het maken van een profiel [Een profiel maken](/help/forms/using/custom-profile.md)

1. **Een CSS-stijlpagina maken voor het opmaken van de HTML5-formulieren**

   Navigeer naar de map waarin u de profielrenderer hebt gemaakt en maak een CSS-stijlbladbestand. De volgende stappen zijn:

   1. Klik met de rechtermuisknop op de map en selecteer **maken** > **bestand maken** in het menu

   1. Voer in het dialoogvenster Bestand maken de naam van de stijlpagina in. Controleer of u de extensie .css gebruikt (bijvoorbeeld stylesheet.css)
   1. Open vanuit het navigatievenster het CSS-bestand dat u hebt gemaakt.
   1. Definieer de CSS-klassen van de componenten die u wilt opmaken en voeg stijlen toe in die klassen.

   Zie voor meer informatie over de CSS-klassen die u voor een bepaalde component in uw HTML5-formulieren wilt maken [Inleiding tot stijlen](/help/forms/using/css-styles.md).

1. **Stijlblad opnemen in renderer profiel**

   Open de pagina Renderer van het Profiel (jsp- dossier) in CRX DE, en neem het CSS dossier in de pagina net onder de XFA cliëntbibliotheek op. Voer deze stappen uit om het CSS-bestand in profiel op te nemen.

   1. Zoek op de rendererpagina naar de volgende regel:

      &lt;cq:includeClientLib categories=&quot;xfaforms.profile&quot; />

   1. Voeg het volgende onder de bovenstaande regel in om de stijlpagina op te nemen:

      &lt;link href=&quot;/path/to/stylesheet&quot; rel=&quot;stylesheet&quot; type=&quot;text/css&quot;/>

   1. Sla het bestand op.
