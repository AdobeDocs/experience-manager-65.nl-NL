---
title: Documentservices-API's starten vanuit de AEM-workflow
seo-title: Documentservices-API's starten vanuit de AEM-workflow
description: Leer hoe u AEM-documentservices oproept op de DDX of de geleverde invoer. Zie ook hoe u PDF naar PDF/A kunt converteren
seo-description: Leer hoe u AEM-documentservices oproept op de DDX of de geleverde invoer. Zie ook hoe u PDF naar PDF/A kunt converteren
uuid: aacec2df-1ad6-4ff2-a99d-ef206efcdc09
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
discoiquuid: 8b85bdc7-3864-49c9-81b0-cf15b8e986d9
translation-type: tm+mt
source-git-commit: 7caf09f7020c066072eac04a349a19b144dfeb7b

---


# Documentservices-API&#39;s starten vanuit de AEM-workflow {#initiate-document-services-apis-from-aem-workflow}

## Assembler {#assembler}

AEM Forms verstrekt douanewerkschema&#39;s om de volgende dienst APIs van de Assembler aan te halen:

* **aanroepen**: Roept bewerkingen aan die in de invoer-DDX zijn opgegeven bij opgegeven invoer.
* **toPDFA**: Hiermee wordt het invoer-PDF-document geconverteerd naar PDF/A-document.

### DDX-workflow aanroepen {#invoke-ddx-workflow}

De **Invoke DDX** -workflow roept de `Invoke` Assembler-service-API aan, waarmee u documenten kunt samenstellen of demonteren, watermerken aan een PDF kunt toevoegen enzovoort.

1. Sleep de stap DX **[!UICONTROL -workflow voor]** aanroepen onder het tabblad Formulierwerkstroom in Sidetrap.
1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, omgevingsopties en uitvoerdocumenten en klik op **[!UICONTROL OK]**.

#### Invoerdocumenten {#input-documents}

Voor de DDX-workflow voor aanroepen zijn de volgende invoerdocumenten vereist:

* **DDX**: Het is een verplichte invoer voor de Invoke DDX-workflowstap en kan worden opgegeven door een van de volgende opties te selecteren in de vervolgkeuzelijst DDX-invoer.

   * *Ten opzichte van Payload*: Het DDX-invoerbestand is relatief ten opzichte van de payload-map voor het workflowitem.
   * *Payload* gebruiken: De lading voor het werkschemapunt wordt gebruikt als inputDDX- document.
   * *Absoluut pad*: Het absolute pad naar het DDX-document in de CRX-opslagplaats.

* **Kaart maken van PayPal**: Als deze optie is geselecteerd, worden alle documenten in de payload-map toegevoegd aan de kaart van het invoerdocument voor de `invoke` API in Assembler. De knooppuntnaam voor elk document wordt gebruikt als sleutel in de kaart.

* **Kaart** invoerdocument: Hiermee geeft u de kaart van het invoerdocument op. U kunt elk gewenst aantal items toevoegen, waarbij elk item de sleutel van het document op de kaart en de bron van het document aangeeft.

#### Omgevingsopties {#environment-options}

Op het tabblad Omgevingsopties kunt u verschillende verwerkingsopties instellen voor de API voor aanroepen.

* *Logboekniveau* taak: Hiermee geeft u het logniveau voor de verwerkingslogboeken op.
* *Alleen* valideren: Controleert de geldigheid van inputDDX.

* *Fout*: Specificeert of de vraag aan de dienst van de Assembler in het geval van een fout zou moeten ontbreken. De standaardwaarde is False.

#### Documenten uitvoeren {#output-documents}

Afhankelijk van de invoer-DDX kan de API voor aanroepen meerdere uitvoerdocumenten produceren. Op het tabblad Uitvoerdocumenten kunt u opgeven waar het uitvoerdocument moet worden opgeslagen.

1. *Uitvoer opslaan in Payload*: Hiermee slaat u uitvoerdocumenten op onder de payload-map of overschrijft u de payload als de payload een bestand is.
1. *Kaart* uitvoerdocument: Hiermee kunt u expliciet opgeven waar elk uitvoerdocument moet worden opgeslagen door één item per uitvoerdocument toe te voegen. Elk item geeft het document aan en waar het moet worden opgeslagen. Een uitvoerdocument kan de lading overschrijven of onder de ladingsomslag worden bewaard. Dit is handig wanneer er meerdere uitvoerdocumenten zijn.

1. *Taaklogboek*: Hier geeft u op waar het taaklogdocument moet worden opgeslagen. Dit is handig voor het oplossen van problemen met fouten.

### Converteren naar PDF/A-workflow {#convert-to-pdf-a-workflow}

Met de workflowstap Converteren naar PDF/A wordt de API voor de `toPDFA` Assembler-service aangeroepen. Deze wordt gebruikt voor het converteren van PDF-documenten naar PDF/A-compatibele documenten.

1. Sleep de stap voor de **[!UICONTROL convertToPDFA]** -workflow onder het tabblad Formulierwerkstroom in Sidetrap.

1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, conversieopties en uitvoerdocumenten en klik op **[!UICONTROL OK]**.

#### Invoerdocumenten {#input-documents-1}

Geef op een van de volgende manieren de bron op van het document dat u wilt converteren naar een PDF/A-compatibel document.

* *Ten opzichte van Payload*: Het invoerdocument is relatief ten opzichte van de payload-map voor het workflowitem.
* *Payload* gebruiken: De lading voor het werkschemapunt wordt gebruikt als inputdocument.
* *Absoluut pad*: Het absolute pad van het invoerdocument in de CRX-opslagplaats.

#### Conversieopties {#conversion-options}

Met conversieopties kunt u opties opgeven waarmee het conversieproces van PDF/A wordt gewijzigd.

* *Naleving* : Hiermee wordt de PDF/A-standaard opgegeven waaraan de uitvoer-PDF/A moet voldoen.
* *Resultaatniveau* : Hiermee geeft u het logniveau op dat moet worden gebruikt voor conversielogboeken in PDF/A.
* *Handtekeningen* : Hiermee geeft u op hoe de handtekeningen in het invoerdocument moeten worden verwerkt tijdens de conversie.
* *Kleurruimte* : Hiermee geeft u de vooraf gedefinieerde kleurruimte op die moet worden gebruikt voor de uitvoer van een PDF/A-document.
* *Conversie controleren* : Hiermee wordt opgegeven of het geconverteerde PDF/A-document na conversie moet worden gecontroleerd op compatibiliteit met PDF/A.
* *Logboekniveau* taak: Hiermee geeft u het logniveau op dat moet worden gebruikt voor het verwerken van logbestanden.

* *Schema* voor extensie metagegevens: Hier geeft u het pad op naar het extensieschema voor metagegevens dat moet worden gebruikt voor XMP-eigenschappen in de metagegevens van het PDF-document.

#### Documenten uitvoeren {#output-documents-1}

Op het tabblad Uitvoerdocumenten kunt u het doel voor de uitvoerdocumenten opgeven

* *PDFA-document*: Hier geeft u de locatie op waar het geconverteerde PDF/A-document wordt opgeslagen. U kunt het laaddocument overschrijven of opslaan in de payload-map.
* *Conversielogboek*: Hier geeft u de locatie op waar de conversielogboeken worden opgeslagen. U kunt het document overschrijven of opslaan in de map voor het laden.

## Formulieren {#forms}

De werkstroom PDF-formulier renderen is een omslag rondom de API van de Forms-service om een PDF-formulier te maken met een XDP-sjabloon en gegevens-xml. `renderPDFForm`

### Werkstroom PDF-formulier renderen {#render-pdf-form-workflow}

1. Sleep de werkstroomstap PDF-formulier renderen onder het tabblad Formulierwerkstroom in Sidetrap.
1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, uitvoerdocumenten en aanvullende parameters en klik op **[!UICONTROL OK]**.

#### Invoerdocumenten {#input-documents-2}

* *Sjabloonbestand*: Hiermee geeft u de locatie van de XDP-sjabloon op. Het is een verplicht veld.

* *Gegevensdocument*: Hier geeft u de locatie op van de gegevens-xml die met de sjabloon moeten worden samengevoegd.

#### Documenten uitvoeren {#output-documents-2}

* *Uitvoerdocument*: - Hier geeft u de naam op van het gegenereerde PDF-formulier.

#### Aanvullende parameters {#additional-parameters}

* *Hoofdmap* inhoud: Hiermee geeft u het pad op naar de map in de opslagplaats waar fragmenten of afbeeldingen worden opgeslagen die worden gebruikt in de invoer-XDP-sjabloon.
* *URL* verzenden: Hier geeft u de standaard verzendURL op voor het gegenereerde PDF-formulier.
* *Landinstelling*: Hier geeft u de standaardlandinstelling voor het gegenereerde PDF-formulier op.
* *Acrobat-versie*: Hiermee geeft u de doelversie van Acrobat op voor het gegenereerde PDF-formulier.
* *Gelabelde PDF*: Hiermee geeft u aan of de gegenereerde PDF toegankelijk moet zijn.
* *XCI-document*: Hiermee geeft u het pad naar het XCI-bestand op.

## Output {#output}

De Generate niet Interactive PDF Workflow is een omslag rond de dienst API van de `generatePDFOutput` Output. Hiermee worden niet-interactieve PDF-documenten gegenereerd op basis van XDP-sjabloon en data-xml.

### Niet-interactieve PDF-uitvoerworkflow genereren {#generate-non-interactive-pdf-output-workflow-nbsp}

1. Sleep de werkstroom Niet-interactieve PDF-uitvoer genereren onder het tabblad Formulierwerkstroom in Sidetrap.
1. Dubbelklik op de toegevoegde workflowstap om de component te bewerken.
1. Configureer in het dialoogvenster Component bewerken invoerdocumenten, uitvoerdocumenten en aanvullende parameters en klik op **[!UICONTROL OK]**.

#### Invoerdocumenten {#input-documents-3}

* *Sjabloonbestand*: Hiermee geeft u de locatie van de XDP-sjabloon op. Het is een verplicht veld.

* *Gegevensdocument*: Hier geeft u de locatie op van de gegevens-xml die met de sjabloon moeten worden samengevoegd.

#### Uitvoerdocument {#output-document}

*Uitvoerdocument*: Hier geeft u de naam op van het gegenereerde PDF-formulier.

#### Aanvullende parameters {#additional-parameters-1}

* *Hoofdmap* inhoud: Hiermee geeft u het pad op naar de map in de opslagplaats waar fragmenten of afbeeldingen worden opgeslagen die worden gebruikt in de invoer-XDP-sjabloon.
* *Landinstelling*: Hier geeft u de standaardlandinstelling voor het gegenereerde PDF-formulier op.
* *Acrobat-versie*: Hiermee geeft u de doelversie van Acrobat op voor het gegenereerde PDF-formulier.
* Gelijktijdige PDF: Hiermee geeft u aan of u de gegenereerde PDF wilt optimaliseren voor webweergave.
* *Gelabelde PDF*: Hiermee geeft u aan of de gegenereerde PDF toegankelijk moet zijn.
* *XCI-document*: Hiermee geeft u het pad naar het XCI-bestand op.

