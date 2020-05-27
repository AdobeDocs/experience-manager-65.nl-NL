---
title: Metagegevensprofielen om de metagegevensvereisten van elementen aan te passen
description: Informatie over metagegevensprofielen voor elementen. Leer hoe u een metagegevensprofiel maakt en toepast op mapelementen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '1310'
ht-degree: 16%

---


# Metadataprofielen {#metadata-profiles}

Met een metagegevensprofiel kunt u standaardmetagegevens toepassen op elementen in een map. Maak een metagegevensprofiel en pas dit toe op een map. Elk element dat u daarna naar de map uploadt, overerft de standaardmetagegevens die u in het metagegevensprofiel hebt geconfigureerd.

## Een metagegevensprofiel toevoegen {#adding-a-metadata-profile}

1. Navigeer naar **[!UICONTROL Tools > Assets > Metadata Profiles]** en klik **[!UICONTROL Create]**.
1. Voer een titel in voor Metagegevensprofiel, bijvoorbeeld Voorbeeldmetagegevens, en klik op **[!UICONTROL Create]**. De [!UICONTROL Edit Form] voor het metagegevensprofiel wordt weergegeven.

   ![chlimage_1-197](assets/chlimage_1-480.png)

1. Klik op een component en configureer de eigenschappen ervan op het **[!UICONTROL Settings]** tabblad. Klik bijvoorbeeld op de **[!UICONTROL Description]** component en bewerk de eigenschappen ervan.

   ![chlimage_1-198](assets/chlimage_1-481.png)

   Bewerk de volgende eigenschappen voor de **[!UICONTROL Description]** component:

   * **[!UICONTROL Field Label]**: De weergavenaam van de eigenschap metadata. Dit is alleen voor de gebruikersverwijzing.

   * **[!UICONTROL Map to Property]**: De waarde van deze eigenschap geeft het relatieve pad/de naam naar het knooppunt met middelen waar het wordt opgeslagen in de opslagplaats. De waarde moet altijd beginnen met `./` omdat dit aangeeft dat het pad zich onder het knooppunt van het element bevindt.
   ![chlimage_1-199](assets/chlimage_1-482.png)

   The value you specify for **[!UICONTROL Map to property]** is stored as a property under the asset&#39;s metadata node. Als u bijvoorbeeld `/jcr:content/metadata/dc:desc` als naam van **[!UICONTROL Map to property]**, slaat Middelen de waarde `dc:desc` bij de de meta-gegevensknoop van het middel op.

   * **[!UICONTROL Default Value]**: Gebruik deze eigenschap om een standaardwaarde voor de metagegevenscomponent toe te voegen. Als u bijvoorbeeld &quot;Mijn beschrijving&quot; opgeeft, wordt deze waarde toegewezen aan de eigenschap `dc:desc` in het metagegevensknooppunt van het element.
   ![chlimage_1-200](assets/chlimage_1-483.png)

   >[!NOTE]
   >
   >Een standaardwaarde toevoegen aan een nieuwe metagegevenseigenschap (die nog niet bestaat op het tabblad . `/jcr:content/metadata` node) geeft de eigenschap en de waarde ervan standaard niet weer op de pagina Eigenschappen van het element. Als u de nieuwe eigenschap wilt weergeven op de pagina met elementen, wijzigt u het corresponderende schema. [!UICONTROL Properties]

1. (Optioneel) Voeg op het tabblad **[!UICONTROL Build Form]** meer componenten toe aan het formulier Bewerken en configureer de eigenschappen ervan op het tabblad **[!UICONTROL Settings]**. De volgende eigenschappen zijn beschikbaar op het tabblad **[!UICONTROL Build Form]**:

| Component | Eigenschappen |
| ----------------------------- | ----------------------------------------------------------------------- |
| [!UICONTROL Section Header] | Veldlabel, <br> beschrijving |
| [!UICONTROL Single Line Text] | Veld, label, <br> toewijzen aan eigenschap, <br> standaardwaarde |
| [!UICONTROL Multi Value Text] | Veld, label, <br> toewijzen aan eigenschap, <br> standaardwaarde |
| [!UICONTROL Number] | Veld, label, <br> toewijzen aan eigenschap, <br> standaardwaarde |
| [!UICONTROL Date] | Veld, label, <br> toewijzen aan eigenschap, <br> standaardwaarde |
| [!UICONTROL Standard Tags] | Veldlabel, <br> Toewijzen aan eigenschap, <br> Standaardwaarde, <br> Beschrijving |

![chlimage_1-201](assets/chlimage_1-484.png)

1. Klik op **[!UICONTROL Done]**. Het metagegevensprofiel wordt toegevoegd aan de lijst met profielen op de **[!UICONTROL Metadata Profiles]** pagina.<br>

   ![Metagegevensprofiel toegevoegd aan pagina Metagegevensprofielen](assets/MetadataProfiles-page.png)

## Een metagegevensprofiel kopiëren {#copying-a-metadata-profile}

1. Selecteer op de **[!UICONTROL Metadata Profiles]** pagina een metagegevensprofiel om er een kopie van te maken.

   ![chlimage_1-203](assets/chlimage_1-486.png)

1. Klik op **[!UICONTROL Copy]** de werkbalk.
1. Voer in het **[!UICONTROL Copy Metadata Profile]** dialoogvenster een titel in voor de nieuwe kopie van het metagegevensprofiel.
1. Klik op **[!UICONTROL Copy]**. De kopie van het metadataprofiel wordt weergegeven in de lijst met profielen op de pagina **[!UICONTROL Metadata Profiles]**.

   ![Een kopie van het metagegevensprofiel dat is toegevoegd aan de pagina Metagegevensprofielen](assets/copy-metadata-profile.png)

## Een metagegevensprofiel verwijderen {#deleting-a-metadata-profile}

1. Selecteer op de **[!UICONTROL Metadata Profiles]** pagina een profiel dat u wilt verwijderen.

   ![chlimage_1-205](assets/chlimage_1-488.png)

1. Ta[] **[!UICONTROL Delete Metadata Profiles]** in the toolbar.
1. Klik in het dialoogvenster **[!UICONTROL Delete]** om het verwijderen te bevestigen. Het metagegevensprofiel wordt uit de lijst verwijderd.

## Een metagegevensprofiel toepassen op mappen {#applying-a-metadata-profile-to-folders}

Wanneer u een metagegevensprofiel toewijst aan een map, nemen eventuele submappen het profiel automatisch over van de bovenliggende map. Dit betekent dat u slechts één metagegevensprofiel kunt toewijzen aan een map. Denk daarom zorgvuldig na over de mapstructuur van de locatie waar u middelen uploadt, opslaat, gebruikt en archiveert.

Als u een ander metagegevensprofiel aan een map hebt toegewezen, overschrijft het nieuwe profiel het vorige profiel. De vorige bestaande mapelementen blijven ongewijzigd. Het nieuwe profiel wordt toegepast op de elementen die later aan de map worden toegevoegd.

Mappen waaraan een profiel is toegewezen, worden in de gebruikersinterface aangeduid met de naam van het profiel dat in de kaartnaam wordt weergegeven.

![chlimage_1-206](assets/chlimage_1-489.png)

U kunt metagegevensprofielen toepassen op specifieke mappen of op alle elementen.

U kunt elementen opnieuw verwerken in een map die al een bestaand metagegevensprofiel heeft dat u later hebt gewijzigd. Zie Elementen [opnieuw verwerken in een map nadat u het verwerkingsprofiel](processing-profiles.md#reprocessing-assets)hebt bewerkt.

### Metagegevensprofielen toepassen op specifieke mappen {#applying-metadata-profiles-to-specific-folders}

U kunt een metadataprofiel toepassen op een map vanuit het menu **[!UICONTROL Tools]**, of vanuit **[!UICONTROL Properties]** als u zich in een map bevindt. In deze sectie wordt beschreven hoe u op beide manieren metadataprofielen kunt toepassen op mappen.

Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. Zie Elementen [opnieuw verwerken in een map nadat u het verwerkingsprofiel](processing-profiles.md#reprocessing-assets)hebt bewerkt.

#### Metagegevensprofielen toepassen op mappen vanuit de gebruikersinterface Profielen {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

Voer de stappen uit om het metagegevensprofiel toe te passen:

1. Klik op het logo van Experience Manager en navigeer naar **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Selecteer het metagegevensprofiel dat u wilt toepassen op een of meerdere mappen.

   ![chlimage_1-207](assets/chlimage_1-490.png)

1. Click **[!UICONTROL Apply Metadata Profile to Folder(s)]** and select the folder or multiple folders you want use to receive the newly uploaded assets and click **[!UICONTROL Done]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

#### Metagegevensprofielen toepassen op mappen vanuit Eigenschappen {#applying-metadata-profiles-to-folders-from-properties}

1. Klik in de linkertrack **[!UICONTROL Assets]** en navigeer naar de map waarop u een metagegevensprofiel wilt toepassen.
1. Klik in de map op het vinkje om het te selecteren en klik vervolgens **[!UICONTROL Properties]**.

1. Selecteer het tabblad **[!UICONTROL Metadata Profiles]**, selecteer het profiel in het vervolgkeuzemenu en klik op **[!UICONTROL Save]**.

   ![chlimage_1-208](assets/chlimage_1-491.png)

   Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

### Een metagegevensprofiel algemeen toepassen {#applying-a-metadata-profile-globally}

Naast het toepassen van een profiel op een map, kunt u er ook een globaal toepassen, zodat het geselecteerde profiel wordt toegepast op inhoud die wordt geüpload naar de middelen van Experience Manager in elke map.

U kunt elementen opnieuw verwerken in een map die al een bestaand metagegevensprofiel heeft dat u later hebt gewijzigd. Zie Elementen [opnieuw verwerken in een map nadat u het verwerkingsprofiel](processing-profiles.md#reprocessing-assets)hebt bewerkt.

Ga als volgt te werk als u een metagegevensprofiel globaal wilt toepassen:

* Navigeer naar `https://[aem_server]:[port]/mnt/overlay/dam/gui/content/assets/foldersharewizard.html/content/dam` en pas het juiste profiel toe en klik op **[!UICONTROL Save]**.

   ![chlimage_1-209](assets/chlimage_1-492.png)

* Navigeer in CRXDE Lite naar het volgende knooppunt: `/content/dam/jcr:content`. Voeg de eigenschap toe `metadataProfile:/etc/dam/metadata/dynamicmedia/<name of metadata profile>` en klik **[!UICONTROL Save All]**.

   ![chlimage_1-210](assets/chlimage_1-493.png)

## Een metagegevensprofiel uit mappen verwijderen {#removing-a-metadata-profile-from-folders}

Wanneer u een metagegevensprofiel uit een map verwijdert, nemen eventuele submappen automatisch de verwijdering van het profiel uit de bovenliggende map over. Alle verwerking van bestanden die in de mappen zijn opgetreden, blijft echter intact.

You can remove a metadata profile from a folder from within the **[!UICONTROL Tools]** menu or if you are in the folder, from the **[!UICONTROL Properties]**. In deze sectie wordt beschreven hoe u metadataprofielen op beide manieren uit mappen kunt verwijderen.

### Metaprofielen uit mappen verwijderen via de gebruikersinterface Profielen {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Klik op het logo van Experience Manager en navigeer naar **[!UICONTROL Tools > Assets > Metadata Profiles]**.
1. Selecteer het metagegevensprofiel dat u uit een of meerdere mappen wilt verwijderen.
1. Click **[!UICONTROL Remove Metadata Profile from Folder(s)]** and select the folder or multiple folders you want use to remove a profile from and click **[!UICONTROL Done]**.

   U kunt bevestigen dat het metagegevensprofiel niet meer wordt toegepast op een map omdat de naam niet langer onder de mapnaam wordt weergegeven.

### Metagegevensprofielen uit mappen verwijderen via eigenschappen {#removing-metadata-profiles-from-folders-via-properties}

1. Klik op het logo van Experience Manager en navigeer **[!UICONTROL Assets]** naar de map waaruit u een metagegevensprofiel wilt verwijderen.
1. Klik in de map op het vinkje om het te selecteren en klik vervolgens **[!UICONTROL Properties]**.
1. Selecteer het tabblad **[!UICONTROL Metadata Profiles]**, selecteer **[!UICONTROL None]** in het vervolgkeuzemenu en klik op **[!UICONTROL Save]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

## Beperkingen en aanbevolen procedures {#limitations-best-practices-tips}

* U kunt al bestaande metagegevensprofielen hebben sinds de upgrade naar [!DNL Experience Manager] 6.5. Als u een dergelijk profiel na de upgrade toepast in de map [!UICONTROL Properties] op het [!UICONTROL Metadata Profiles] tabblad, worden de velden voor metagegevens niet weergegeven. Als u echter een nieuw metagegevensprofiel toepast, worden de formuliervelden weergegeven, maar niet beschikbaar zoals u had verwacht. Er gaat geen functionaliteit verloren, maar als u de (niet-beschikbare) formuliervelden wilt zien, bewerkt en slaat u de bestaande metagegevensprofielen op.

>[!MORELIKETHIS]
>
>* [Profielen voor het verwerken van metagegevens, afbeeldingen en video&#39;s](processing-profiles.md)
>* [Aanbevolen procedures voor het ordenen van uw digitale middelen voor het gebruik van verwerkingsprofielen](/help/assets/organize-assets.md)

