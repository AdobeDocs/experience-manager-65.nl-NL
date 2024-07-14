---
title: Configuratiebestanden van PDF Generatoren importeren en exporteren
description: Leer hoe u configuratiebestanden van PDF Generatoren kunt importeren en exporteren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
exl-id: b363b23a-29bb-4ea4-a8f2-5ba9fe3c7b27
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '372'
ht-degree: 0%

---

# Configuratiebestanden van PDF Generatoren importeren en exporteren {#importing-and-exporting-pdf-generator-configuration-files}

Het configuratiebestand bevat de conversiegegevens van de PDF Generator, waaronder de PDF, het bestandstype en de beveiligingsinstellingen.

>[!NOTE]
>
>U kunt de time-out-instelling voor PDF Generator niet wijzigen door een aangepast native2pdfconfig.xml-bestand te importeren. De time-out-instelling in dat bestand is alleen ter informatie en geeft de huidige instelling in PDF Generator weer. Om onderbreking te veranderen die plaatsen, zie &quot;Plaatsende de prestatieparameters van de PDF Generator&quot;in [ het Installeren van en het Opstellen van AEM vormen ](https://www.adobe.com/go/learn_aemforms_installJBoss_63).

## Het huidige configuratiebestand exporteren {#export-your-current-configuration-file}

1. Klik in de beheerconsole op Services > PDF Generator > Configuratiebestanden > Configuratie exporteren.
1. Als u de instellingen wilt exporteren, selecteert u de gewenste optie:

   * Selecteer Volledige configuratie downloaden om alle benoemde instellingen te exporteren.
   * Als u slechts één Adobe PDF-instelling, beveiligingsinstelling of bestandstype-instelling wilt exporteren, selecteert u Minimale configuratie downloaden.

     Als u een minimale configuratie exporteert, selecteert u de instellingen voor Adobe PDF, beveiliging en bestandstype die u wilt exporteren.

1. Klik op Downloaden en sla het XML-bestand op de gewenste locatie op.

## Een configuratiebestand importeren {#import-a-configuration-file}

>[!NOTE]
>
>Uw systeem wordt opnieuw geconfigureerd op basis van de gegevens in het geïmporteerde bestand.

1. Klik in de beheerconsole op Services > PDF Generator > Configuratiebestanden > Configuratie importeren.
1. Selecteer Een bestaand configuratiebestand importeren.
1. Om de dossierplaats in het vakje van het Dossier van de Configuratie te specificeren, doorbladert de klik en selecteert het dossier, en klikt dan **de Invoer**.

## Alle lagen in AutoCAD-bestanden converteren {#convert-all-layers-within-autocad-files}

Standaard wordt met PDF Generator alleen de standaardlaag AutoCAD-bestanden omgezet in PDF in plaats van alle lagen in het bestand. Volg deze procedure om alle lagen om te zetten.

1. Klik in de beheerconsole op Services > PDF Generator > Configuratiebestanden > Configuratie exporteren.
1. Selecteer Volledige configuratie downloaden en klik op Downloaden.
1. Open het gedownloade bestand in een teksteditor en voeg de tekst toe onder de tag `AutoCAD` in de tag `PDFMaker` `convertAllPages="true"` .
1. Klik in de beheerconsole op Services > PDF Generator > Configuratiebestanden > Configuratie importeren.
1. Selecteer Een bestaand configuratiebestand importeren, geef het bijgewerkte bestand op en klik op Importeren.

   Alle lagen worden omgezet in AutoCAD-bestanden die met het gewijzigde configuratiebestand worden omgezet.

## De configuratie herstellen naar de oorspronkelijke instellingen die met de PDF Generator zijn geïnstalleerd {#reset-your-configuration-to-the-original-settings-installed-with-pdf-generator}

1. Klik in de beheerconsole op Services > PDF Generator > Configuratiebestanden > Configuratie importeren.
1. Selecteer Standaardinstellingen configuratie herstellen en klik op Importeren.
