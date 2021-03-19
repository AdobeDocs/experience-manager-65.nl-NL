---
title: PDF Generator-configuratiebestanden importeren en exporteren
seo-title: PDF Generator-configuratiebestanden importeren en exporteren
description: Leer PDF Generator-configuratiebestanden importeren en exporteren.
seo-description: Leer PDF Generator-configuratiebestanden importeren en exporteren.
uuid: 3367253b-d222-4c5f-9455-a1810d96112e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e25c1b35-73eb-4353-8e39-a2d4cdccd101
feature: PDF Generator
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 0%

---


# Configuratiebestanden van de PDF Generator importeren en exporteren {#importing-and-exporting-pdf-generator-configuration-files}

Het configuratiebestand bevat de conversiegegevens van de PDF Generator, waaronder de PDF, het bestandstype en de beveiligingsinstellingen.

>[!NOTE]
>
>U kunt de time-outinstelling voor PDF Generator niet wijzigen door een aangepast native2pdfconfig.xml-bestand te importeren. De time-outinstelling in dat bestand is alleen ter informatie en geeft de huidige instelling weer in PDF Generator. Zie &quot;Prestatieparameters van PDF-generator instellen&quot; in [AEM formulieren installeren en implementeren](https://www.adobe.com/go/learn_aemforms_installJBoss_63) als u de time-outinstelling wilt wijzigen.

## Uw huidige configuratiebestand exporteren {#export-your-current-configuration-file}

1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Export Configuration.
1. Als u de instellingen wilt exporteren, selecteert u de gewenste optie:

   * Selecteer Volledige configuratie downloaden om alle benoemde instellingen te exporteren.
   * Als u slechts één Adobe PDF-instelling, beveiligingsinstelling of bestandstype-instelling wilt exporteren, selecteert u Minimale configuratie downloaden.

      Als u een minimale configuratie exporteert, selecteert u de instellingen voor Adobe PDF, beveiliging en bestandstype die u wilt exporteren.

1. Klik op Downloaden en sla het XML-bestand op de gewenste locatie op.

## Een configuratiebestand {#import-a-configuration-file} importeren

>[!NOTE]
>
>Uw systeem wordt opnieuw geconfigureerd op basis van de gegevens in het geïmporteerde bestand.

1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Import Configuration.
1. Selecteer Een bestaand configuratiebestand importeren.
1. Om de dossierplaats in het vakje van het Dossier van de Configuratie te specificeren, doorbladert de klik en selecteert het dossier, en klikt dan **Invoer**.

## Alle lagen in AutoCAD-bestanden converteren {#convert-all-layers-within-autocad-files}

Standaard converteert PDF Generator alleen de standaardlaag AutoCAD-bestanden naar PDF in plaats van alle lagen in het bestand. Volg deze procedure om alle lagen om te zetten.

1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Export Configuration.
1. Selecteer Volledige configuratie downloaden en klik op Downloaden.
1. Open het gedownloade bestand in een teksteditor en voeg onder de tag `AutoCAD` in de tag `PDFMaker` de tekst `convertAllPages="true"` toe.
1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Import Configuration.
1. Selecteer Een bestaand configuratiebestand importeren, geef het bijgewerkte bestand op en klik op Importeren.

   Alle lagen worden omgezet in AutoCAD-bestanden die met het gewijzigde configuratiebestand worden omgezet.

## De configuratie herstellen naar de oorspronkelijke instellingen die zijn geïnstalleerd met de PDF Generator {#reset-your-configuration-to-the-original-settings-installed-with-pdf-generator}

1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Import Configuration.
1. Selecteer Standaardinstellingen configuratie herstellen en klik op Importeren.

