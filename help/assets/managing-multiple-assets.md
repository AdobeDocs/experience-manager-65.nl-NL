---
title: Meerdere elementen en verzamelingen beheren
description: Leer hoe u de metagegevens van meerdere elementen en verzamelingen tegelijk kunt bewerken om snel algemene wijzigingen in metagegevens door te geven.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 9af0ee0ff9d1089b6cf09c52f7f606cce6775d72

---


# Elementen en verzamelingen beheren {#managing-multiple-assets-and-collections}

Met Adobe Enterprise Manager (AEM)-middelen kunt u de metagegevens van meerdere elementen tegelijk bewerken, zodat u snel algemene metagegevenswijzigingen in elementen bulksgewijs kunt doorgeven. U kunt de metagegevens voor meerdere verzamelingen ook bulksgewijs bewerken.

Gebruik de eigenschappenpagina om wijzigingen in metagegevens uit te voeren voor meerdere elementen of verzamelingen:

* Eigenschappen van metagegevens wijzigen in een algemene waarde
* Tags toevoegen of wijzigen

Gebruik de schema-editor om de pagina met eigenschappen van metagegevens aan te passen, inclusief het toevoegen, wijzigen of verwijderen van eigenschappen van metagegevens.

>[!NOTE]
>
>De bulkbewerkingsmethoden werken voor elementen die beschikbaar zijn in een map of een verzameling. Voor de elementen die beschikbaar zijn in verschillende mappen of die voldoen aan een algemeen criterium, is het mogelijk om de metagegevens na het zoeken [in grote](search-assets.md#metadataupdates)hoeveelheden bij te werken.

## Eigenschappen van metagegevens van meerdere elementen bewerken {#editing-metadata-properties-of-multiple-assets}

1. Navigeer in de gebruikersinterface Elementen naar de locatie van de elementen die u wilt bewerken.
1. Selecteer de elementen waarvan u de algemene eigenschappen wilt bewerken.
1. Tik op of klik op het pictogram **[!UICONTROL Eigenschappen]** op de werkbalk om de pagina met eigenschappen voor de geselecteerde elementen te openen.

   >[!NOTE]
   >
   >Wanneer u meerdere elementen selecteert, wordt het laagste gebruikelijke bovenliggende formulier geselecteerd voor de elementen. Met andere woorden, op de eigenschappenpagina worden alleen metagegevensvelden weergegeven die algemeen zijn op de eigenschappenpagina&#39;s van alle afzonderlijke elementen.

1. Wijzig de eigenschappen van metagegevens voor geselecteerde elementen onder de verschillende tabbladen.
1. Schakel de overige elementen in de lijst uit als u de metagegevenseditor voor een bepaald element wilt weergeven. De gebieden van de meta-gegevensredacteur zijn bevolkt met de meta-gegevens voor het bepaalde middel.

   >[!NOTE]
   >
   >* Op de pagina met eigenschappen kunt u elementen uit de lijst met elementen verwijderen door ze te deselecteren. In de lijst met elementen zijn standaard alle elementen geselecteerd. De metagegevens voor elementen die u uit de lijst verwijdert, worden niet bijgewerkt.
   >* Selecteer boven aan de lijst met elementen het selectievakje bij **[!UICONTROL Titel]** om te schakelen tussen het selecteren van de elementen en het wissen van de lijst.


1. Tik op het pictogram **[!UICONTROL Instellingen]** op de werkbalk en selecteer het gewenste schema om een ander metagegevensschema voor de elementen te selecteren.
1. Sla de wijzigingen op.
1. Als u de nieuwe metagegevens wilt toevoegen aan de bestaande metagegevens in velden die meerdere waarden bevatten, selecteert u de modus **** Toevoegen. Als u deze optie niet selecteert, worden de bestaande metagegevens in de velden vervangen door de nieuwe metagegevens. Tik/klik op **[!UICONTROL Verzenden]**.

   >[!CAUTION]
   >
   >Voor velden met één waarde worden de nieuwe metagegevens niet toegevoegd aan de bestaande waarde in het veld, zelfs niet als u de modus **** Toevoegen selecteert.

## Limiet voor bijwerken van bulkmetagegevens configureren {#configlimit}

Om DOS als situatie te verhinderen, beperkt AEM het aantal parameters die in een Verschuivend verzoek worden gesteund. Wanneer u metagegevens van veel elementen in één keer bijwerkt, kunt u de limiet bereiken en worden de metagegevens niet bijgewerkt voor meer elementen. AEM genereert de volgende waarschuwing in de logboeken:

`org.apache.sling.engine.impl.parameters.Util Too many name/value pairs, stopped processing after 10000 entries`

Als u de limiet wilt wijzigen, opent u de webconsole ( **[!UICONTROL Gereedschappen]** > **[!UICONTROL Bewerkingen]** > **[!UICONTROL Webconsole]**) en wijzigt u de waarde van **[!UICONTROL Maximale POST-parameters]** in de OSGi-configuratie van **[!UICONTROL Apache Sling Request-parameters]** .

>[!MORELIKETHIS]
>
>* [Eigenschappen van metagegevens van meerdere verzamelingen bewerken](managing-collections-touch-ui.md#editing-collection-metadata-in-bulk)

