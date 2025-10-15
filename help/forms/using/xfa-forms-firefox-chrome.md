---
title: Hoe kan ik op XFA gebaseerde PDF forms openen op Firefox en Chrome?
description: Hoe kan ik op XFA gebaseerde PDF forms openen op Firefox en Chrome?
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: ebb61f2c5056a780e829e64031f8eba69a8ae25b
workflow-type: tm+mt
source-wordcount: '287'
ht-degree: 0%

---

# Hoe kan ik op XFA gebaseerde PDF forms openen op Firefox en Chrome?

## Probleem

De ingebouwde PDF-viewer die is geïntroduceerd met Mozilla Firefox en Google Chrome biedt geen ondersteuning voor PDF forms op basis van XFA. PDF forms op basis van XFA kan daarom niet worden geopend in latere versies van Firefox en Chrome.

## Oplossing

Als u op XFA gebaseerde PDF forms wilt gebruiken in Firefox en Chrome, voert u de volgende stappen uit om Firefox en Chrome te configureren voor het openen van PDF&#39;s met Adobe Reader of Adobe Acrobat.

>[!NOTE]
> 
> Zorg ervoor dat Adobe Reader of Adobe Acrobat op uw computer is geïnstalleerd.

### Firefox configureren

1. In Firefox, kies **Hulpmiddelen > Opties**.

1. In de dialoog van Opties, klik **Toepassingen**.

1. Typ PDF in het zoekveld op het tabblad Toepassingen.

1. Voor Portable Document Format (PDF) inhoudssoort in het onderzoeksresultaat, uitgezochte **Gebruik Adobe Acrobat (in Firefox)** van de drop-down lijst van de Actie.
   ![&#x200B; gebruik-adobe-acrobat &#x200B;](/help/forms/using/assets/use-adobe-acrobat.png)
1. Klik op OK.

1. Start Firefox opnieuw.

### Chrome configureren

1. Ga in Chrome naar chrome://plugins/.

1. Klik op Uitschakelen onder Chrome PDF Viewer en klik op Inschakelen onder Adobe PDF Plug-In.
   ![&#x200B; chroom-pdf-viewer &#x200B;](/help/forms/using/assets/chrome-image.png)
Voor meer informatie, zie [&#x200B; insteekmodule Adobe PDF &#x200B;](https://support.google.com/chrome/?hl=en&visit_id=638803785294106945-2276548125&rd=4&topic=3421431#topic=7439538) documentatie door Google.

>[!NOTE]
> 
> LiveCycle ES4 biedt ondersteuning voor het weergeven van XFA-formulieren in HTML5, zodat de formulieren kunnen worden geopend in browsers met HTML5-ondersteuning, inclusief formulieren die op mobiele apparaten zoals iPad worden uitgevoerd. De HTML5-uitvoering van de formulieren behoudt de indeling van het formulierontwerp en ondersteunt de meeste formulierlogica (zoals JavaScript, Form Calc en formuliervalidaties) die is ingesloten in de XFA-formuliersjabloon. Op deze manier worden uw technologieinvesteringen in XFA-formulieren eenvoudig overgedragen naar apparaten waarop de Adobe Reader-insteekmodule niet kan worden uitgevoerd.
>Voor meer informatie, zie [&#x200B; LiveCycle productdocumentatie &#x200B;](https://business.adobe.com/nl/products/experience-manager/forms/aem-forms.html).

[&#x200B; Juridische Mededelingen &#x200B;](https://chl-author-preview.corp.adobe.com/content/help/en/legal/legal-notices.html)    |    [&#x200B; Online Beleid van de Privacy &#x200B;](https://www.adobe.com/privacy.html)