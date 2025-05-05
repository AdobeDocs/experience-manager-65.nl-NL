---
title: Problemen weergeven voor op XFA gebaseerde PDF forms en documenten die met een beleid zijn beveiligd
description: Problemen weergeven voor op XFA gebaseerde PDF forms en documenten die met een beleid zijn beveiligd
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: ebb61f2c5056a780e829e64031f8eba69a8ae25b
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Problemen weergeven voor op XFA gebaseerde PDF forms en documenten die met een beleid zijn beveiligd

Controleer om de volgende redenen of u geen op XFA gebaseerd PDF-formulier of een met beleid beveiligd document kunt openen met Adobe LiveCycle Rights Management:

* Voor PDF forms op basis van XFA en documenten die zijn beveiligd met een beleid, is Adobe® Acrobat® of Adobe® Reader®, versie 8 en hoger vereist. Zie [ de Downloads van Adobe ](https://www.adobe.com/downloads.html) voor het downloaden van recentste Reader of Acrobat.
* Browsers zoals Mozilla Firefox en Google Chrome bieden een ingebouwde PDF-viewer die geen XFA-gebaseerde PDF forms ondersteunt. Als u op XFA gebaseerde PDF forms in deze browsers wilt weergeven, moet u configureren om PDF&#39;s te openen met Acrobat of Reader. Zie op XFA gebaseerde PDF forms op Mozilla Firefox en Google Chrome voor meer informatie.
* Met Acrobat en Reader kunt u in Microsoft® Windows® configureren voor het openen van PDF&#39;s in de Beveiligde weergave. Hierdoor wordt voorkomen dat PDF forms op basis van XFA en documenten die met een beleid zijn beveiligd, worden geopend. Zorg ervoor dat de Beveiligde weergavemodus in uw Acrobat of Reader is uitgeschakeld. Voor meer informatie, zie [ Beschermde Mening (Vensters slechts) ](https://helpx.adobe.com/nl/acrobat/kb/end-of-support-acrobat-x-reader-x.html).
* Neem het volgende in overweging als u toegang probeert te krijgen tot PDF forms-documenten op basis van XFA of documenten die met een beleid zijn beveiligd op uw mobiele apparaat:

   * Voor het openen van documenten die met een beleid zijn beveiligd op mobiele apparaten is Adobe Reader voor mobiele apparaten vereist. Voor meer informatie, zie [ mobiele app van Adobe Reader ](https://www.adobe.com/in/acrobat/mobile/acrobat-reader.html).
   * Mobiele iOS-, Android- en Blackberry-apparaten en smartphones bieden geen ondersteuning voor de insteekmodule Adobe Reader voor XFA-formulieren. LiveCycle ES4 biedt een service die geschikt is voor mobiele apparaten met HTML5. De maker van het formulier moet deze service gebruiken om formulieren op deze apparaten te kunnen gebruiken.
   * Als u de metro-stijl gebruikt op een mobiel Windows 8-apparaat, schakelt u over naar de klassieke weergave of maakt u gebruik van HTML5 met LiveCycle ES4.

>[!NOTE]
>
>LiveCycle ES4 biedt ondersteuning voor het weergeven van XFA-formulieren in HTML5, zodat de formulieren kunnen worden geopend in browsers met HTML5-ondersteuning, inclusief formulieren die op mobiele apparaten zoals iPad worden uitgevoerd. De HTML5-uitvoering van de formulieren behoudt de indeling van het formulierontwerp en ondersteunt de meeste formulierlogica (zoals JavaScript, Form Calc en formuliervalidaties) die is ingesloten in de XFA-formuliersjabloon. Op deze manier worden uw technologieinvesteringen in XFA-formulieren eenvoudig overgedragen naar apparaten waarop de Adobe Reader-insteekmodule niet kan worden uitgevoerd.
>Voor meer informatie, zie Bevorderend aan [ LiveCycle productdocumentatie ](https://business.adobe.com/products/experience-manager/forms/aem-forms.html).

[ Juridische Mededelingen ](https://chl-author-preview.corp.adobe.com/content/help/en/legal/legal-notices.html)    |    [ Online Beleid van de Privacy ](https://www.adobe.com/privacy.html)