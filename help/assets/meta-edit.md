---
title: Metagegevens bewerken of toevoegen
description: Meer informatie over metagegevens van middelen vindt u in [!DNL Adobe Experience Manager Assets] en op verschillende manieren waarop u metagegevens van elementen kunt bewerken.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 99ce6e0572797b7bccf755aede93623be6bd5698
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 1%

---


# Metagegevens bewerken of toevoegen {#how-to-edit-or-add-metadata}

Metagegevens zijn aanvullende informatie over het element die kan worden doorzocht. Deze wordt automatisch uitgepakt wanneer u een afbeelding uploadt. U kunt de bestaande metagegevens bewerken of nieuwe eigenschappen van metagegevens toevoegen aan bestaande velden (bijvoorbeeld wanneer een metagegevensveld leeg is).

Omdat organisaties gecontroleerde en betrouwbare taalwoordenboeken voor metagegevens nodig hebben, is het [!DNL Experience Manager Assets] niet mogelijk ad-hocnieuwe eigenschappen voor metagegevens toe te voegen. Hoewel auteurs geen nieuwe metagegevensvelden voor elementen kunnen toevoegen, kunnen ontwikkelaars dat wel. Zie [Nieuwe eigenschap voor metagegevens maken voor elementen](meta-edit.md#editing-metadata-schema).

## Metagegevens voor een element bewerken {#editing-metadata-for-an-asset}

Metagegevens bewerken:

1. Voer een van de volgende handelingen uit:

   * Selecteer het element in de [!DNL Assets] interface en klik op **[!UICONTROL View Properties]** de werkbalk.
   * Selecteer de **[!UICONTROL View Properties]** handeling Snel bij de elementminiatuur.
   * Klik op de elementpagina op **[!UICONTROL View Properties]** change_1-168 ![](assets/chlimage_1-168.png) op de werkbalk.
   Op de elementpagina worden alle metagegevens van het element weergegeven. De metagegevens worden geëxtraheerd wanneer het element wordt geüpload (opgenomen) naar [!DNL Experience Manager].

   ![Elementeigenschappen selecteren om metagegevens weer te geven](assets/asset-metadata.png)

   *Afbeelding: Bewerk of voeg metagegevens toe op de[!UICONTROL Properties]elementpagina.*

1. Make edits to the metadata under the various tabs, as required, and when completed, click **[!UICONTROL Save]** from the toolbar to save your changes. Click **[!UICONTROL Close]** to return to the Assets web interface.

   >[!NOTE]
   >
   >Als een tekstveld leeg is, is er geen bestaande metagegevensset. U kunt een waarde in het veld invoeren en deze opslaan om die eigenschap voor metagegevens toe te voegen.

Wijzigingen in de metagegevens van een element worden teruggeschreven naar het oorspronkelijke binaire bestand als onderdeel van de XMP-gegevens. Dit gebeurt via de workflow voor het terugschrijven van [!DNL Experience Manager] metagegevens. Wijzigingen die worden aangebracht in de bestaande eigenschappen (zoals `dc:title`), worden overschreven en nieuwe eigenschappen (inclusief aangepaste eigenschappen zoals `cq:tags`) worden samen met het schema toegevoegd.

XMP-schrijfback wordt ondersteund en ingeschakeld voor de platforms en bestandsindelingen die in de [technische vereisten worden beschreven.](/help/sites-deploying/technical-requirements.md)

## Metagegevensschema bewerken {#editing-metadata-schema}

Zie [Formulieren](metadata-schemas.md#edit-metadata-schema-forms)in metagegevensschema bewerken voor meer informatie.

## Een aangepaste naamruimte registreren binnen [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

U kunt uw eigen naamruimten toevoegen binnen [!DNL Experience Manager]. Net zoals er vooraf gedefinieerde naamruimten zijn, zoals `cq`, `jcr`en `sling`, kunt u een naamruimte hebben voor de metagegevens van de gegevensopslagruimte en de verwerking van XML.

1. Ga naar de knoop type beleidspagina `https:[aem_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Klik **[!UICONTROL Namespaces]** boven aan de pagina. De pagina voor naamruimtebeheer wordt weergegeven in een venster.

1. Klik **[!UICONTROL New]** onderaan om een naamruimte toe te voegen.
1. Geef een aangepaste naamruimte op in de XML-naamruimteconventie. Geef de id op in de vorm van een URI en een bijbehorend voorvoegsel voor de id. Klik op **[!UICONTROL Save]**.
