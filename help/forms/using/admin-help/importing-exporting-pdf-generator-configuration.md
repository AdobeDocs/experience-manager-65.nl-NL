---
title: PDF Generator-configuratiebestanden importeren en exporteren
seo-title: Importing and exporting PDF Generator configuration files
description: Leer hoe u configuratiebestanden van PDF Generator importeert en exporteert.
seo-description: Learn how to import and export PDF Generator configuration files.
uuid: 3367253b-d222-4c5f-9455-a1810d96112e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: e25c1b35-73eb-4353-8e39-a2d4cdccd101
feature: PDF Generator
exl-id: b363b23a-29bb-4ea4-a8f2-5ba9fe3c7b27
source-git-commit: 9d142ce9e25e048512440310beb05d762468f6a2
workflow-type: tm+mt
source-wordcount: '378'
ht-degree: 0%

---

# PDF Generator-configuratiebestanden importeren en exporteren {#importing-and-exporting-pdf-generator-configuration-files}

Het configuratiebestand bevat de conversiegegevens van de PDF Generator, waaronder de PDF, het bestandstype en de beveiligingsinstellingen.

>[!NOTE]
>
>U kunt niet onderbreking veranderen die voor de Generator van PDF plaatst door een douane native2pdfconfig.xml- dossier in te voeren. De time-out-instelling in dat bestand is alleen ter informatie en geeft de huidige instelling weer in PDF Generator. Als u de time-outinstelling wilt wijzigen, raadpleegt u &quot;Prestatieparameters van PDF Generator instellen&quot; in [AEM installeren en implementeren](https://www.adobe.com/go/learn_aemforms_installJBoss_63).

## Het huidige configuratiebestand exporteren {#export-your-current-configuration-file}

1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Export Configuration.
1. Als u de instellingen wilt exporteren, selecteert u de gewenste optie:

   * Selecteer Volledige configuratie downloaden om alle benoemde instellingen te exporteren.
   * Als u slechts één Adobe PDF-instelling, beveiligingsinstelling of bestandstype-instelling wilt exporteren, selecteert u Minimale configuratie downloaden.

      Als u een minimale configuratie exporteert, selecteert u de instellingen voor Adobe PDF, beveiliging en bestandstype die u wilt exporteren.

1. Klik op Downloaden en sla het XML-bestand op de gewenste locatie op.

## Een configuratiebestand importeren {#import-a-configuration-file}

>[!NOTE]
>
>Uw systeem wordt opnieuw geconfigureerd op basis van de gegevens in het geïmporteerde bestand.

1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Import Configuration.
1. Selecteer Een bestaand configuratiebestand importeren.
1. Als u de bestandslocatie wilt opgeven in het vak Configuratiebestand, klikt u op Bladeren om het bestand te zoeken en te selecteren. Klik vervolgens op **Importeren**.

## Alle lagen in AutoCAD-bestanden converteren {#convert-all-layers-within-autocad-files}

Standaard wordt met PDF Generator alleen de standaardlaag AutoCAD-bestanden omgezet in PDF in plaats van alle lagen in het bestand. Volg deze procedure om alle lagen om te zetten.

1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Export Configuration.
1. Selecteer Volledige configuratie downloaden en klik op Downloaden.
1. Open het gedownloade bestand in een teksteditor en open het onder de `AutoCAD` -tag binnen de `PDFMaker` -tag, de tekst toevoegen `convertAllPages="true"`.
1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Import Configuration.
1. Selecteer Een bestaand configuratiebestand importeren, geef het bijgewerkte bestand op en klik op Importeren.

   Alle lagen worden omgezet in AutoCAD-bestanden die met het gewijzigde configuratiebestand worden omgezet.

## Stel uw configuratie aan originele montages terug die met de Generator van PDF worden geïnstalleerd {#reset-your-configuration-to-the-original-settings-installed-with-pdf-generator}

1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Import Configuration.
1. Selecteer Standaardinstellingen configuratie herstellen en klik op Importeren.
