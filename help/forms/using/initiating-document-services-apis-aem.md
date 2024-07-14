---
title: Documentservices-API's starten vanuit AEM workflow
description: Leer hoe u AEM documentservices oproept op de DDX of de geleverde invoer. Zie ook hoe u PDF kunt omzetten in PDF/A
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
exl-id: 123087a2-9d09-4579-9185-2ccd7d25bf8d
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication
role: User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 0%

---

# Documentservices-API&#39;s starten vanuit AEM workflow  {#initiate-document-services-apis-from-aem-workflow}

## Assembler {#assembler}

AEM Forms biedt aangepaste workflows om de volgende API&#39;s van de Assembler-service aan te roepen:

* **haalt** aan: Roept verrichtingen aan die in inputDDX op geleverde input worden gespecificeerd.
* **toPDFA**: Zet document van inputPDF in document PDF/A om.

### DDX-workflow aanroepen {#invoke-ddx-workflow}

Het **roept DDX** werkschema DDX `Invoke` de dienst API van de Assembler aan, die u kunt gebruiken om documenten samen te stellen of te demonteren, watermerk aan PDF toe te voegen, etc.

1. Sleep de werkstroomstap van **[!UICONTROL Invoke DDX]** onder het tabblad Forms Workflow in Sidekick.
1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, omgevingsopties en uitvoerdocumenten en klik op **[!UICONTROL OK]** .

#### Invoerdocumenten {#input-documents}

Voor de DDX-workflow voor aanroepen zijn de volgende invoerdocumenten vereist:

* **DDX**: Het is een verplichte input voor de Invoke DX- werkschemastap en kan worden gespecificeerd door één van de volgende opties van de DDX inputdrop-down te selecteren.

   * *met betrekking tot Payload*: Het DDX inputdossier is met betrekking tot de ladingsomslag voor het werkschemapunt.
   * *de Payload van het Gebruik*: De nuttige lading voor het werkschemapunt wordt gebruikt als document inputDDX.
   * *Absolute Weg*: De absolute weg aan het DX- document in de bewaarplaats van CRX.

* **creeer Kaart van PayLoad**: Wanneer geselecteerd, worden alle documenten onder de ladingsomslag toegevoegd aan de Kaart van het Document van de Input voor `invoke` API in Assembler. De knooppuntnaam voor elk document wordt gebruikt als sleutel in de kaart.

* **Kaart van het Document van de Input**: Specificeert de Kaart van het Document van de Invoer. U kunt elk gewenst aantal items toevoegen, waarbij voor elk item de sleutel van het document op de kaart en de bron van het document worden opgegeven.

#### Omgevingsopties {#environment-options}

Op het tabblad Omgevingsopties kunt u verschillende verwerkingsopties instellen voor de API voor aanroepen.

* *Niveau van het Logboek van de Baan*: Specificeert het logboekniveau voor de verwerkingslogboeken.
* *bevestigt slechts*: Controleert de geldigheid van inputDDX.

* *Gebrek op Fout*: Specificeert of de vraag aan de dienst van de Assembler zou moeten ontbreken als er een fout is. De standaardwaarde is False.

#### Documenten uitvoeren {#output-documents}

Afhankelijk van de invoer-DDX kan de API voor aanroepen meerdere uitvoerdocumenten produceren. Op het tabblad Uitvoerdocumenten kunt u opgeven waar het uitvoerdocument moet worden opgeslagen.

1. *sparen Output in Payload*: Bewaart outputdocumenten onder de ladingsomslag, of beschrijft de nuttige lading, als de lading een dossier is.
1. *Kaart van het Document van de Output*: Laat u uitdrukkelijk specificeren waar te om elk outputdocument te bewaren door één ingang per outputdocument toe te voegen. Elk item geeft het document aan en waar het moet worden opgeslagen. Een uitvoerdocument kan de lading overschrijven of onder de ladingsomslag worden bewaard. Dit is handig wanneer er meerdere uitvoerdocumenten zijn.

1. *Logboek van de Baan*: Specificeert waar te om het document van het baanlogboek te bewaren, dat in het oplossen van problemenmislukkingen nuttig is.

### Omzetten in PDF/A-workflow {#convert-to-pdf-a-workflow}

Met de workflowstap Omzetten in PDF/A wordt de `toPDFA` Assembler-service-API aangeroepen. Deze wordt gebruikt voor het converteren van PDF-documenten naar documenten die compatibel zijn met PDF/A.

1. Sleep de werkstroomstap van **[!UICONTROL ConvertToPDFA]** onder het tabblad Forms Workflow in Sidekick.

1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, conversieopties en uitvoerdocumenten en klik op **[!UICONTROL OK]** .

#### Invoerdocumenten {#input-documents-1}

Geef op een van de volgende manieren de bron op van het document dat u wilt converteren naar een document dat compatibel is met PDF/A.

* *met betrekking tot Payload*: Het inputdocument is met betrekking tot de ladingsomslag voor het werkschemapunt.
* *Payload van het Gebruik*: De nuttige lading voor het werkschemapunt wordt gebruikt als inputdocument.
* *Absolute Weg*: De absolute weg van het inputdocument in de bewaarplaats van CRX.

#### Conversieopties {#conversion-options}

Met de opties voor conversie kunt u opties opgeven waarmee het conversieproces van PDF/A wordt gewijzigd.

* *Naleving* : Specificeert de norm PDF/A waaraan de output PDF/A moet voldoen.
* *Niveau van het Resultaat* : Specificeert het logboekniveau dat voor PDF/A omzettingslogboeken moet worden gebruikt.
* *Handtekeningen* : Specificeert hoe de handtekeningen in inputdocument tijdens omzetting moeten worden verwerkt.
* *Ruimte van de Kleur*: Specificeert de vooraf bepaalde kleurenruimte die voor output PDF/A document moet worden gebruikt.
* *verifieer* Omzetting: Specificeert of het omgezette PDF/A- document voor naleving PDF/A na omzetting zou moeten worden geverifieerd.
* *Niveau van het Logboek van de Baan* : Specificeert het logboekniveau dat voor verwerkingslogboeken moet worden gebruikt.

* *Schema van de Uitbreiding van Meta-gegevens* : Specificeert de weg aan het schema van de meta-gegevensuitbreiding dat voor XMP eigenschappen in de meta-gegevens van het document van PDF moet worden gebruikt.

#### Documenten uitvoeren {#output-documents-1}

Op het tabblad Uitvoerdocumenten kunt u het doel voor de uitvoerdocumenten opgeven

* *PDFA Document*: Specificeert de plaats waar het omgezette PDF/A- document wordt bewaard. U kunt het laaddocument overschrijven of opslaan in de payload-map.
* *Logboek van de Omzetting*: Specificeert de plaats waar de omzettingslogboeken worden bewaard. U kunt het document overschrijven of opslaan in de map voor het laden.

## Forms {#forms}

De werkstroom PDF-formulier renderen is een omslag rond de `renderPDFForm` Forms service-API om een PDF-formulier te maken met een XDP-sjabloon en data-xml.

### Workflow voor PDF-formulier weergeven {#render-pdf-form-workflow}

1. Sleep de werkstroomstap PDF-formulier renderen onder het tabblad Forms Workflow in Sidekick.
1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, uitvoerdocumenten en aanvullende parameters en klik op **[!UICONTROL OK]** .

#### Invoerdocumenten {#input-documents-2}

* *Dossier van het Malplaatje*: Specificeert de plaats van het malplaatje XDP. Het is een verplicht veld.

* *Document van Gegevens*: Specificeert de plaats van gegevens xml die met het malplaatje moeten worden samengevoegd.

#### Documenten uitvoeren {#output-documents-2}

* *Document van de Output*: - specificeert de naam van de geproduceerde vorm van de PDF.

#### Aanvullende parameters {#additional-parameters}

* *Wortel van de Inhoud*: Specificeert de weg aan de omslag in de bewaarplaats waar de fragmenten of de beelden die in het inputXDP malplaatje worden gebruikt worden opgeslagen.
* *legt Url* voor: Specificeert het gebrek verzend URL voor geproduceerde vorm van PDF.
* *Landinstelling*: Specificeert de standaardscène voor de geproduceerde vorm van de PDF.
* *Versie van Acrobat*: Specificeert de gerichte versie van Acrobat voor de geproduceerde vorm van PDF.
* *Tagged PDF*: Specificeert of om de geproduceerde PDF toegankelijk te maken.
* *XCI document*: Specificeert de weg aan het XCI dossier.

## Uitvoer {#output}

De Generate niet Interactive PDF Workflow is een omslag rond de `generatePDFOutput` Output service-API. Deze wordt gebruikt om niet-interactieve PDF-documenten te genereren op basis van XDP-sjabloon en data-xml.

### Niet-interactieve PDF-uitvoerworkflow genereren   {#generate-non-interactive-pdf-output-workflow-nbsp}

1. Sleep de workflow Niet-interactieve PDF-uitvoer genereren onder het tabblad Forms Workflow in Sidekick.
1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, uitvoerdocumenten en aanvullende parameters en klik op **[!UICONTROL OK]** .

#### Invoerdocumenten {#input-documents-3}

* *Dossier van het Malplaatje*: Specificeert de plaats van het malplaatje XDP. Het is een verplicht veld.

* *Document van Gegevens*: Specificeert de plaats van gegevens xml die met het malplaatje moeten worden samengevoegd.

#### Uitvoerdocument {#output-document}

*Document van de Output*: Specificeert de naam van de geproduceerde vorm van de PDF.

#### Aanvullende parameters {#additional-parameters-1}

* *Wortel van de Inhoud*: Specificeert de weg aan de omslag in de bewaarplaats waar de fragmenten of de beelden die in het inputXDP malplaatje worden gebruikt worden opgeslagen.
* *Landinstelling*: Specificeert de standaardscène voor de geproduceerde vorm van PDF.
* *Versie van Acrobat*: Specificeert de gerichte versie van Acrobat voor de geproduceerde vorm van PDF.
* Lineaire PDF: geeft aan of de gegenereerde PDF moet worden geoptimaliseerd voor webweergave.
* *Tagged PDF*: Specificeert of om de geproduceerde PDF toegankelijk te maken.
* *XCI document*: Specificeert de weg aan het XCI dossier.
