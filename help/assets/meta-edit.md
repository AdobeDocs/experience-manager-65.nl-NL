---
title: Metagegevens bewerken of toevoegen
description: Meer informatie over metagegevens van middelen vindt u in [!DNL Adobe Experience Manager Assets] en op verschillende manieren waarop u metagegevens van elementen kunt bewerken.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 90f9c0b60d4b0878f56eefea838154bb7627066d

---


# Metagegevens bewerken of toevoegen {#how-to-edit-or-add-metadata}

Metagegevens zijn aanvullende informatie over het element die kan worden doorzocht. Deze wordt automatisch uitgepakt wanneer u een afbeelding uploadt. U kunt de bestaande metagegevens bewerken of nieuwe eigenschappen van metagegevens toevoegen aan bestaande velden (bijvoorbeeld wanneer een metagegevensveld leeg is).

Omdat organisaties gecontroleerde en betrouwbare taalwoordenboeken voor metagegevens nodig hebben, is het [!DNL Experience Manager Assets] niet mogelijk ad-hocnieuwe eigenschappen voor metagegevens toe te voegen. Hoewel auteurs geen nieuwe metagegevensvelden voor elementen kunnen toevoegen, kunnen ontwikkelaars dat wel. Zie [Nieuwe eigenschap voor metagegevens maken voor elementen](meta-edit.md#editing-metadata-schema).

## Metagegevens voor een element bewerken {#editing-metadata-for-an-asset}

Metagegevens bewerken:

1. Voer een van de volgende handelingen uit:

   * Selecteer het element in de [!DNL Assets] interface en klik op Eigenschappen **** weergeven op de werkbalk.
   * Selecteer in de elementminiatuur de snelle actie **[!UICONTROL Weergave-eigenschappen]** .
   * Klik op de elementpagina op **[!UICONTROL Eigenschappen]** van ![werkbalk](assets/chlimage_1-168.png) weergeven.
   Op de elementpagina worden alle metagegevens van het element weergegeven. De metagegevens worden geëxtraheerd wanneer het element wordt geüpload (opgenomen) in Experience Manager.

   ![Elementeigenschappen selecteren om metagegevens weer te geven](assets/asset-metadata.png)

   *Afbeelding: Bewerk of voeg metagegevens toe op de pagina Eigenschappen van element.*

1. Make edits to the metadata under the various tabs, as required, and when completed, click **[!UICONTROL Save]** from the toolbar to save your changes. Click **[!UICONTROL Close]** to return to the Assets web interface.

   >[!NOTE]
   >
   >Als een tekstveld leeg is, is er geen bestaande metagegevensset. U kunt een waarde in het veld invoeren en deze opslaan om die eigenschap voor metagegevens toe te voegen.

Wijzigingen in de metagegevens van een element worden teruggeschreven naar het oorspronkelijke binaire bestand als onderdeel van de XMP-gegevens. Dit gebeurt via de workflow voor het terugschrijven van metagegevens van Experience Manager. Wijzigingen die worden aangebracht in de bestaande eigenschappen (zoals `dc:title`), worden overschreven en nieuwe eigenschappen (inclusief aangepaste eigenschappen zoals `cq:tags`) worden samen met het schema toegevoegd.

XMP-schrijfback wordt ondersteund en ingeschakeld voor de platforms en bestandsindelingen die in de [technische vereisten worden beschreven.](/help/sites-deploying/technical-requirements.md)

## Metagegevensschema bewerken {#editing-metadata-schema}

Zie [Formulieren](metadata-schemas.md#edit-metadata-schema-forms)in metagegevensschema bewerken voor meer informatie over het bewerken van het schema voor metagegevens.

## Een aangepaste naamruimte registreren in Experience Manager {#registering-a-custom-namespace-within-aem}

U kunt uw eigen naamruimten toevoegen in Experience Manager. Net zoals er vooraf gedefinieerde naamruimten zijn, zoals cq, jcr en sling, kunt u een naamruimte hebben voor de metagegevens van de gegevensopslagruimte en de verwerking van de xml.

1. Ga naar de knoop type beleidspagina `https:[aem_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Klik op **[!UICONTROL Naamruimten]** boven aan de pagina. De pagina voor naamruimtebeheer wordt weergegeven in een venster.

1. Als u een naamruimte wilt toevoegen, klikt u op **[!UICONTROL Nieuw]** onderaan.
1. Geef een aangepaste naamruimte op in de XML-naamruimteconventie (geef de id op in de vorm van een URI en een bijbehorend voorvoegsel voor de id) en klik op **[!UICONTROL Opslaan]**.
