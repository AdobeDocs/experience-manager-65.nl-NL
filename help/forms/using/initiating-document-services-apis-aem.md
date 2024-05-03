---
title: Documentservices-API's starten vanuit AEM workflow
description: Leer hoe u AEM documentservices oproept op de DDX of de geleverde invoer. Zie ook hoe u PDF kunt omzetten in PDF/A
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
exl-id: 123087a2-9d09-4579-9185-2ccd7d25bf8d
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 0%

---

# Documentservices-API&#39;s starten vanuit AEM workflow  {#initiate-document-services-apis-from-aem-workflow}

## Assembler {#assembler}

AEM Forms biedt aangepaste workflows om de volgende API&#39;s van de Assembler-service aan te roepen:

* **oproepen**: Roept bewerkingen aan die zijn opgegeven in de invoer-DDX bij de opgegeven invoer.
* **toPDFA**: Hiermee wordt het invoer-PDF-document geconverteerd naar PDF/A-document.

### DDX-workflow aanroepen {#invoke-ddx-workflow}

De **DDX aanroepen** workflow roept de `Invoke` De dienst API van de assembleur, die u kunt gebruiken om documenten samen te stellen of te demonteren, watermerk aan een PDF toe te voegen, etc.

1. Sleep de **[!UICONTROL Invoke DDX]** workflowstap onder het tabblad Forms Workflow in Sidekick.
1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, omgevingsopties en uitvoerdocumenten en klik op **[!UICONTROL OK]**.

#### Invoerdocumenten {#input-documents}

Voor de DDX-workflow voor aanroepen zijn de volgende invoerdocumenten vereist:

* **DDX**: Het is een verplichte invoer voor de stap van de DDX-workflow Invoke en kan worden opgegeven door een van de volgende opties te selecteren in de vervolgkeuzelijst voor DDX-invoer.

   * *Ten opzichte van Payload*: Het DDX-invoerbestand is relatief ten opzichte van de payload-map voor het workflowitem.
   * *Payload gebruiken*: De payload voor het workflowitem wordt gebruikt als het invoer-DDX-document.
   * *Absoluut pad*: Het absolute pad naar het DDX-document in de CRX-opslagruimte.

* **Kaart maken van PayLoad**: Als deze optie is geselecteerd, worden alle documenten in de payload-map toegevoegd aan de Kaart van het invoerdocument voor de opdracht `invoke` API in Assembler. De knooppuntnaam voor elk document wordt gebruikt als sleutel in de kaart.

* **Kaart van invoerdocument**: geeft de kaart van het invoerdocument op. U kunt elk gewenst aantal items toevoegen, waarbij voor elk item de sleutel van het document op de kaart en de bron van het document worden opgegeven.

#### Omgevingsopties {#environment-options}

Op het tabblad Omgevingsopties kunt u verschillende verwerkingsopties instellen voor de API voor aanroepen.

* *Taaklogniveau*: Geeft het logniveau voor de verwerkingslogbestanden aan.
* *Alleen valideren*: Controleert de geldigheid van de input-DDX.

* *Fout: mislukt*: Geeft aan of de aanroep naar de Assembler-service moet mislukken als er een fout is. De standaardwaarde is False.

#### Documenten uitvoeren {#output-documents}

Afhankelijk van de invoer-DDX kan de API voor aanroepen meerdere uitvoerdocumenten produceren. Op het tabblad Uitvoerdocumenten kunt u opgeven waar het uitvoerdocument moet worden opgeslagen.

1. *Uitvoer opslaan in Payload*: Hiermee slaat u uitvoerdocumenten op onder de payload-map of overschrijft u de payload als de payload een bestand is.
1. *Kaart van uitvoerdocument*: Hiermee kunt u expliciet opgeven waar elk uitvoerdocument moet worden opgeslagen door één item per uitvoerdocument toe te voegen. Elk item geeft het document aan en waar het moet worden opgeslagen. Een uitvoerdocument kan de lading overschrijven of onder de ladingsomslag worden bewaard. Dit is handig wanneer er meerdere uitvoerdocumenten zijn.

1. *Taaklog*: Hiermee geeft u aan waar het taaklogdocument moet worden opgeslagen. Dit is handig bij het oplossen van problemen met fouten.

### Omzetten in PDF/A-workflow {#convert-to-pdf-a-workflow}

Met de workflowstap Omzetten in PDF/A wordt de `toPDFA` Assembler-service-API. Deze wordt gebruikt voor het converteren van PDF-documenten naar documenten die compatibel zijn met PDF/A.

1. Sleep de **[!UICONTROL ConvertToPDFA]** workflowstap onder het tabblad Forms Workflow in Sidekick.

1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, conversieopties en uitvoerdocumenten en klik op **[!UICONTROL OK]**.

#### Invoerdocumenten {#input-documents-1}

Geef op een van de volgende manieren de bron op van het document dat u wilt converteren naar een document dat compatibel is met PDF/A.

* *Ten opzichte van Payload*: Het invoerdocument is relatief ten opzichte van de payload-map voor het workflowitem.
* *Payload gebruiken*: De payload voor het workflowitem wordt gebruikt als het invoerdocument.
* *Absoluut pad*: Het absolute pad van het invoerdocument in de CRX-opslagplaats.

#### Conversieopties {#conversion-options}

Met de opties voor conversie kunt u opties opgeven waarmee het conversieproces van PDF/A wordt gewijzigd.

* *Compatibiliteit* : Geeft de PDF/A-standaard aan waaraan de uitvoer PDF/A moet voldoen.
* *Resultaatniveau* : Geeft het logniveau op dat moet worden gebruikt voor conversielogboeken voor PDF/A.
* *Handtekeningen* : Geeft aan hoe de handtekeningen in het invoerdocument moeten worden verwerkt tijdens de conversie.
* *Kleurruimte* : Geeft de vooraf gedefinieerde kleurruimte op die moet worden gebruikt voor uitvoer van PDF/A-document.
* *Verifiëren* Conversie: geeft aan of het omgezette PDF/A-document na conversie moet worden gecontroleerd op PDF/A-compatibiliteit.
* *Taaklogniveau* : Geeft het logniveau op dat moet worden gebruikt voor de verwerking van logbestanden.

* *Metagegevensextensieschema* : Geeft het pad naar het schema voor metagegevensextensie op dat moet worden gebruikt voor XMP eigenschappen in de metagegevens van het PDF-document.

#### Documenten uitvoeren {#output-documents-1}

Op het tabblad Uitvoerdocumenten kunt u het doel voor de uitvoerdocumenten opgeven

* *PDFA-document*: Geeft de locatie op waar het omgezette PDF/A-document wordt opgeslagen. U kunt het laaddocument overschrijven of opslaan in de payload-map.
* *Conversielogboek*: Hiermee geeft u de locatie op waar de conversielogbestanden worden opgeslagen. U kunt het document overschrijven of opslaan in de map voor het laden.

## Forms {#forms}

De werkstroom PDF-formulier renderen is omwikkeld `renderPDFForm` Forms service-API om een PDF-formulier te maken met een XDP-sjabloon en data-xml.

### Workflow voor PDF-formulier weergeven {#render-pdf-form-workflow}

1. Sleep de werkstroomstap PDF-formulier renderen onder het tabblad Forms Workflow in Sidekick.
1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, uitvoerdocumenten en aanvullende parameters en klik op **[!UICONTROL OK]**.

#### Invoerdocumenten {#input-documents-2}

* *Sjabloonbestand*: Geeft de locatie van de XDP-sjabloon op. Het is een verplicht veld.

* *Gegevensdocument*: Geeft de locatie op van de gegevens-xml die met de sjabloon moeten worden samengevoegd.

#### Documenten uitvoeren {#output-documents-2}

* *Uitvoerdocument*: - Hier geeft u de naam op van het gegenereerde PDF-formulier.

#### Aanvullende parameters {#additional-parameters}

* *Inhoudsbasis*: Geeft het pad aan naar de map in de opslagplaats waar fragmenten of afbeeldingen worden opgeslagen die worden gebruikt in de invoer-XDP-sjabloon.
* *URL verzenden*: Hiermee geeft u de standaard verzendURL op voor het gegenereerde PDF-formulier.
* *Landinstelling*: Geeft de standaardlandinstelling voor het gegenereerde PDF-formulier aan.
* *Acrobat-versie*: Hiermee geeft u de beoogde Acrobat-versie op voor het gegenereerde PDF-formulier.
* *Tagged PDF*: Geeft aan of de gegenereerde PDF toegankelijk moet worden gemaakt.
* *XCI-document*: Geeft het pad naar het XCI-bestand op.

## Uitvoer {#output}

De Generate Niet Interactive PDF Workflow is een omslag rond `generatePDFOutput` Uitvoerservice-API. Deze wordt gebruikt om niet-interactieve PDF-documenten te genereren op basis van XDP-sjabloon en data-xml.

### Niet-interactieve PDF-uitvoerworkflow genereren   {#generate-non-interactive-pdf-output-workflow-nbsp}

1. Sleep de workflow Niet-interactieve PDF-uitvoer genereren onder het tabblad Forms Workflow in Sidekick.
1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, uitvoerdocumenten en aanvullende parameters en klik op **[!UICONTROL OK]**.

#### Invoerdocumenten {#input-documents-3}

* *Sjabloonbestand*: Geeft de locatie van de XDP-sjabloon op. Het is een verplicht veld.

* *Gegevensdocument*: Geeft de locatie op van de gegevens-xml die met de sjabloon moeten worden samengevoegd.

#### Uitvoerdocument {#output-document}

*Uitvoerdocument*: Hiermee geeft u de naam op van het gegenereerde PDF-formulier.

#### Aanvullende parameters {#additional-parameters-1}

* *Inhoudsbasis*: Geeft het pad aan naar de map in de opslagplaats waar fragmenten of afbeeldingen worden opgeslagen die worden gebruikt in de invoer-XDP-sjabloon.
* *Landinstelling*: Geeft de standaardlandinstelling voor het gegenereerde PDF-formulier aan.
* *Acrobat-versie*: Hiermee geeft u de beoogde Acrobat-versie op voor het gegenereerde PDF-formulier.
* Lineaire PDF: geeft aan of de gegenereerde PDF moet worden geoptimaliseerd voor webweergave.
* *Tagged PDF*: Geeft aan of de gegenereerde PDF toegankelijk moet worden gemaakt.
* *XCI-document*: Geeft het pad naar het XCI-bestand op.
