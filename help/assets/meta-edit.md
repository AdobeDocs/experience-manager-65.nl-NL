---
title: Metagegevens bewerken of toevoegen
description: Meer informatie over metagegevens van elementen in AEM Assets en verschillende manieren waarop u metagegevens van elementen kunt bewerken.
contentOwner: AG
translation-type: tm+mt
source-git-commit: a39ee0f435dc43d2c2830b2947e91ffdcf11c7f6

---


# Metagegevens bewerken of toevoegen {#how-to-edit-or-add-metadata}

Metagegevens zijn aanvullende informatie over het element die kan worden doorzocht. Deze wordt automatisch uitgepakt wanneer u een afbeelding uploadt. U kunt de bestaande metagegevens bewerken of nieuwe eigenschappen van metagegevens toevoegen aan bestaande velden (bijvoorbeeld wanneer een metagegevensveld leeg is).

Omdat bedrijven gecontroleerde en betrouwbare taalwoordenboeken voor metagegevens nodig hebben, staat AEM Assets het niet toe om ad-hocnieuwe eigenschappen voor metagegevens toe te voegen. Hoewel auteurs geen nieuwe metagegevensvelden voor elementen kunnen toevoegen, kunnen ontwikkelaars dat wel. Zie [Nieuwe eigenschap voor metagegevens maken voor elementen](meta-edit.md#editing-metadata-schema).

## Metagegevens voor een element bewerken {#editing-metadata-for-an-asset}

Metagegevens bewerken:

1. Voer een van de volgende handelingen uit:

   * Selecteer het element in de interface Elementen en klik op het pictogram **[!UICONTROL Weergave-eigenschappen]** of tik erop op de werkbalk.
   * Selecteer in de elementminiatuur de snelle actie **[!UICONTROL Weergave-eigenschappen]** .
   * Klik/tik op het pictogram **[!UICONTROL Weergave-eigenschappen]** op de werkbalk vanaf de elementpagina.
      ![chlimage_1-168](assets/chlimage_1-168.png)
   Op de elementpagina worden alle metagegevens van het element weergegeven. Deze metagegevens zijn automatisch geëxtraheerd wanneer deze werden geüpload (opgenomen) naar AEM Assets.

   ![chlimage_1-169](assets/chlimage_1-169.png)

1. Breng desgewenst wijzigingen aan in de metagegevens op de verschillende tabbladen en klik, wanneer u klaar bent, op **[!UICONTROL Opslaan]** op de werkbalk om de wijzigingen op te slaan. Klik op **[!UICONTROL Sluiten]** /tik op Sluiten om terug te keren naar de webinterface Middelen.

   >[!NOTE]
   >
   >Als een tekstveld leeg is, is er geen bestaande metagegevensset. U kunt een waarde in het veld invoeren en deze opslaan om die eigenschap voor metagegevens toe te voegen.

Wijzigingen in de metagegevens van een element worden teruggeschreven naar het oorspronkelijke binaire bestand als onderdeel van de XMP-gegevens. Dit gebeurt via de terugschrijfworkflow voor AEM-metagegevens. Wijzigingen die worden aangebracht in de bestaande eigenschappen (zoals `dc:title`), worden overschreven en nieuwe eigenschappen (inclusief aangepaste eigenschappen zoals `cq:tags`) worden samen met het schema toegevoegd.

XMP-schrijfback wordt ondersteund en ingeschakeld voor de platforms en bestandsindelingen die in de [technische vereisten worden beschreven.](/help/sites-deploying/technical-requirements.md)

## Metagegevensschema bewerken {#editing-metadata-schema}

Zie [Formulieren](metadata-schemas.md#edit-metadata-schema-forms)in metagegevensschema bewerken voor meer informatie over het bewerken van het schema voor metagegevens.

## Een aangepaste naamruimte registreren in AEM {#registering-a-custom-namespace-within-aem}

U kunt uw eigen naamruimten toevoegen in AEM. Net zoals er vooraf gedefinieerde naamruimten zijn, zoals cq, jcr en sling, kunt u een naamruimte hebben voor de metagegevens van de gegevensopslagruimte en de verwerking van de xml.

1. Ga naar de knoop type beleidspagina `https:[aem_server]:[port]/crx/explorer/nodetypes/index.jsp`.
1. Klik of tik **[!UICONTROL Namespaces]** bij de bovenkant van de pagina. De pagina voor naamruimtebeheer wordt weergegeven in een venster.

1. Als u een naamruimte wilt toevoegen, klikt u of tikt u onderaan op **[!UICONTROL Nieuw]** .
1. Geef een aangepaste naamruimte op in de XML-naamruimteconventie (geef de id op in de vorm van een URI en een bijbehorend voorvoegsel voor de id) en klik of tik op **[!UICONTROL Opslaan]**.
