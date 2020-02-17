---
title: Pagina-nulinhoud wijzigen in Designer
seo-title: Pagina-nulinhoud wijzigen in Designer
description: Weet u hoe u het bericht kunt wijzigen dat wordt weergegeven op pagina Nul van een XFA PDF wanneer u het weergeeft in een niet-Adobe PDF-viewer?
seo-description: Weet u hoe u het bericht kunt wijzigen dat wordt weergegeven op pagina Nul van een XFA PDF wanneer u het weergeeft in een niet-Adobe PDF-viewer?
uuid: ac23fb21-3f15-48ea-aeeb-4ecc12b771ac
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 56b6a573-8aba-43e7-acb7-c2da45869d95
docset: aem65
translation-type: tm+mt
source-git-commit: f778f8f6acf5f091465b8ec6a0b94bd30758e082

---


# Pagina-nulinhoud wijzigen in Designer{#changing-page-zero-content-in-designer}

Pagina-inhoud nul wordt standaard weergegeven wanneer een niet-Adobe PDF-viewer, zoals de standaard-PDF-viewer in Chrome of Firefox, de inhoud van het PDF/XFA-formulier niet kan lezen. Het standaardbericht Pagina Nul wordt hieronder weergegeven.

![defaultpage0message](assets/defaultpage0message.png)

Met de AEM Forms Feature Pack 1-versie van Designer kunt u het bericht wijzigen dat wordt weergegeven op Pagina Nul. Voer de volgende stappen uit om het bericht Pagina nul te wijzigen:

1. Zorg ervoor dat de versie van Designer van AEM Forms Feature Pack 1 is geïnstalleerd. U kunt de versie controleren van het ongeveer scherm van ontwerper.

1. Open het formulier waarvoor u de inhoud Pagina nul wilt wijzigen.

1. Click **File > Form Properties**.

1. Klik in het dialoogvenster Formuliereigenschappen op ![plus](assets/plus.png) (plus-pictogram) om een aangepaste eigenschap toe te voegen.

1. Specificeer **_pagezerocontent** als naam van het bezit.
1. Voeg het nieuwe bericht Pagina Nul, in Rich Text-indeling, als waarde toe. Bijvoorbeeld:

   `<body xmlns="https://www.w3.org/1999/xhtml" xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">You are seeing this message maybe because you are using a non Adobe PDF Viewer or an Old version of Adobe Reader. You can upgrade to the latest version of Adobe Reader for Windows, Mac, or Linux by visiting <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/reader_download.</p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in"><span style="xfa-spacerun:yes"> </code></p><p style="font-family:'Times';font-size:12pt;letter-spacing:0in">For more assistance with Adobe Reader visit <span style="xfa-spacerun:yes"> </code>https://www.adobe.com/go/acrreader.</p></body>`

1. Sla het formulier op als PDF.

1. Geef het PDF-formulier in een browser weer om te bevestigen dat het bericht is bijgewerkt. De bovenstaande voorbeeldwaarde ziet er als volgt uit:

   ![gewijzigd bericht](assets/changedmessage.png)

>[!NOTE]
>
>De aangepaste eigenschap die u zojuist hebt gemaakt, wordt mogelijk niet correct weergegeven in het dialoogvenster Formuliereigenschappen wanneer u het formulier opnieuw opent. Het werkt echter prima en in het formulier wordt het bijgewerkte bericht Pagina nul weergegeven.

