---
title: Metagegevens van vele elementen en verzamelingen in [!DNL Adobe Enterprise Manager]beheren.
description: Bewerk de metagegevens van veel elementen en verzamelingen tegelijk om wijzigingen in algemene metagegevens snel door te geven.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9fc1201db83ae0d3bb902d4dc3ab6d78cc1dc251
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 12%

---


# Elementen en verzamelingen beheren {#managing-multiple-assets-and-collections}

[!DNL Adobe Enterprise Manager Assets] Hiermee kunt u de metagegevens van meerdere elementen tegelijk bewerken, zodat u snel algemene wijzigingen in metagegevens in elementen bulksgewijs kunt doorgeven. U kunt de metagegevens voor meerdere verzamelingen ook bulksgewijs bewerken.

Gebruik de eigenschappenpagina om wijzigingen in metagegevens uit te voeren voor meerdere elementen of verzamelingen:

* Eigenschappen van metagegevens wijzigen in een algemene waarde
* Tags toevoegen of wijzigen

Gebruik de schema-editor om de pagina met eigenschappen van metagegevens aan te passen, inclusief het toevoegen, wijzigen of verwijderen van eigenschappen van metagegevens.

>[!NOTE]
>
>De bulkbewerkingsmethoden werken voor elementen die beschikbaar zijn in een map of een verzameling. Voor de elementen die beschikbaar zijn in verschillende mappen of die voldoen aan een algemeen criterium, is het mogelijk om de metagegevens na het zoeken [in grote](search-assets.md#metadataupdates)hoeveelheden bij te werken.

## Eigenschappen van metagegevens van meerdere elementen bewerken {#editing-metadata-properties-of-multiple-assets}

1. Navigeer in de [!DNL Assets] gebruikersinterface naar de locatie van de elementen die u wilt bewerken.
1. Selecteer de elementen waarvan u de algemene eigenschappen wilt bewerken.
1. Klik in de werkbalk **[!UICONTROL Properties]** om de pagina met eigenschappen voor de geselecteerde elementen te openen.

   >[!NOTE]
   >
   >Wanneer u meerdere elementen selecteert, wordt het laagste gebruikelijke bovenliggende formulier geselecteerd voor de elementen. Met andere woorden, op de eigenschappenpagina worden alleen metagegevensvelden weergegeven die gemeenschappelijk zijn op de eigenschappenpagina&#39;s van alle afzonderlijke elementen.

1. Wijzig de eigenschappen van metagegevens voor geselecteerde elementen onder de verschillende tabbladen.
1. Schakel de overige elementen in de lijst uit als u de metagegevenseditor voor een bepaald element wilt weergeven. De gebieden van de meta-gegevensredacteur zijn bevolkt met de meta-gegevens voor het bepaalde middel.

   >[!NOTE]
   >
   >* Op de pagina met eigenschappen kunt u elementen uit de lijst met elementen verwijderen door ze te deselecteren. In de lijst met elementen zijn standaard alle elementen geselecteerd. De metagegevens voor elementen die u uit de lijst verwijdert, worden niet bijgewerkt.
   >* Schakel boven aan de lijst met elementen het selectievakje in **[!UICONTROL Title]** om te schakelen tussen het selecteren van de elementen en het wissen van de lijst.


1. Als u een ander metagegevensschema voor de elementen wilt selecteren, klikt u op **[!UICONTROL Settings]** de werkbalk en selecteert u het gewenste schema.
1. Sla de wijzigingen op.
1. Selecteer **[!UICONTROL Append mode]** om de nieuwe metadata toe te voegen aan de bestaande metadata in velden die meerdere waarden bevatten. Als u deze optie niet selecteert, worden de bestaande metadata in de velden vervangen door de nieuwe metadata. Klik op **[!UICONTROL Submit]**.

   >[!CAUTION]
   >
   >Voor velden met één waarde worden de nieuwe metadata niet toegevoegd aan de bestaande waarde in het veld, zelfs niet als u **[!UICONTROL Append mode]** selecteert.

## Limiet voor bijwerken van bulkmetagegevens configureren {#configlimit}

Om DOS als situatie te verhinderen, beperkt de Manager van de Onderneming het aantal parameters die in een Verkoop verzoek worden gesteund. Wanneer u metagegevens van vele elementen in één keer bijwerkt, kunt u de limiet bereiken en worden de metagegevens niet bijgewerkt voor meer elementen. Enterprise Manager genereert de volgende waarschuwing in de logboeken:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

To change the limit, access **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** and change the value of **[!UICONTROL Maximum POST Parameters]** in **[!UICONTROL Apache Sling Request Parameter Handling]** OSGi configuration.

>[!MORELIKETHIS]
>
>* [Eigenschappen van metagegevens van meerdere verzamelingen bewerken](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)

