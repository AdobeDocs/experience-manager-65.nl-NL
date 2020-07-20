---
title: Metagegevens bewerken of toevoegen
description: U kunt de metagegevens van elementen [!DNL Adobe Experience Manager Assets] op verschillende manieren bewerken.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 4748eed3ce484e8446b641ccbc7b5d76cb66f428
workflow-type: tm+mt
source-wordcount: '424'
ht-degree: 1%

---


# Metagegevens bewerken of toevoegen {#how-to-edit-or-add-metadata}

Metagegevens zijn aanvullende informatie over het element die kan worden doorzocht. Deze wordt automatisch uitgepakt wanneer u een afbeelding uploadt. U kunt de bestaande metagegevens bewerken of nieuwe eigenschappen van metagegevens toevoegen aan een bestaand veld, bijvoorbeeld wanneer een metagegevensveld leeg is.

Organisaties hebben beheerste en betrouwbare metagegevenswoordenboeken nodig. Het is daarom [!DNL Experience Manager Assets] niet mogelijk om op aanvraag nieuwe eigenschappen voor metagegevens toe te voegen. Ontwikkelaars en niet auteurs kunnen nieuwe metagegevensvelden voor elementen toevoegen. Zie eigenschap metadata [maken voor elementen](meta-edit.md#editing-metadata-schema).

## Metagegevens voor een element bewerken {#editing-metadata-for-an-asset}

Ga als volgt te werk als u metagegevens wilt bewerken:

1. Voer een van de volgende handelingen uit:

   * Selecteer het element in de [!DNL Assets] interface en klik op **[!UICONTROL View Properties]** de werkbalk.
   * Selecteer de **[!UICONTROL View Properties]** handeling Snel bij de elementminiatuur.
   * Klik op de elementpagina op het pictogram **[!UICONTROL View Properties]** voor de informatie over ![](assets/do-not-localize/info-circle-icon.png) elementen op de werkbalk.

   Op de elementpagina worden alle metagegevens van het element weergegeven. De metagegevens worden geëxtraheerd wanneer het element wordt geüpload (opgenomen) naar [!DNL Experience Manager].

   ![Eigenschappen van een element selecteren om de metagegevens van het element weer te geven](assets/asset-metadata.png)

   *Afbeelding: Bewerk of voeg metagegevens toe op de[!UICONTROL Properties]elementpagina.*

1. Make edits to the metadata under the various tabs, as required, and when completed, click **[!UICONTROL Save]** from the toolbar to save your changes. Click **[!UICONTROL Close]** to return to the [!DNL Assets] web interface.

   >[!NOTE]
   >
   >Als een tekstveld leeg is, is er geen bestaande metagegevensset. U kunt een waarde in het veld invoeren en deze opslaan om die eigenschap voor metagegevens toe te voegen.

Wijzigingen in de metagegevens van een element worden teruggeschreven naar het oorspronkelijke binaire bestand als onderdeel van de XMP-gegevens. De workflow voor het terugschrijven van metagegevens voegt de metagegevens toe aan het oorspronkelijke binaire bestand. Wijzigingen die worden aangebracht in de bestaande eigenschappen (zoals `dc:title`) worden overschreven en nieuwe eigenschappen (zoals aangepaste eigenschappen `cq:tags`) worden toegevoegd aan het schema.

XMP-schrijfback wordt ondersteund en ingeschakeld voor de platforms en bestandsindelingen die in de [technische vereisten worden beschreven.](/help/sites-deploying/technical-requirements.md)

## Metagegevensschema bewerken {#editing-metadata-schema}

Zie [Formulieren](metadata-schemas.md#edit-metadata-schema-forms)in metagegevensschema bewerken voor meer informatie.

## Een aangepaste naamruimte registreren binnen [!DNL Experience Manager] {#registering-a-custom-namespace-within-aem}

U kunt uw eigen naamruimten toevoegen binnen [!DNL Experience Manager]. Net zoals er vooraf gedefinieerde naamruimten zijn, zoals `cq`, `jcr`en `sling`, kunt u een naamruimte hebben voor de metagegevens van de gegevensopslagruimte en de verwerking van XML.

1. Heb toegang tot de knoop type beleidspagina `https://[aem_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Klik boven aan de pagina om de pagina voor naamruimtebeheer te openen. **[!UICONTROL Namespaces]**
1. Als u een naamruimte wilt toevoegen, klikt u **[!UICONTROL New]** onder aan de pagina.
1. Geef een aangepaste naamruimte op in de XML-naamruimteconventie. Geef de id op in de vorm van een URI en een bijbehorend voorvoegsel voor de id. Klik op **[!UICONTROL Save]**.

>[!MORELIKETHIS]
>
>* [Informatie over metagegevens en de behoefte aan metagegevens in Middelen](metadata.md)
>* [XMP-metadata](xmp.md)
>* [Referentie metagegevensschema](meta-ref.md)

