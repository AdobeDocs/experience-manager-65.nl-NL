---
title: Profielen voor het verwerken van metagegevens, afbeeldingen en video's
description: Een profiel is een set regels met betrekking tot de opties die moeten worden toegepast op elementen die naar een map zijn geüpload. Geef op welk metagegevensprofiel en videocoderingsprofiel u wilt toepassen op de video-elementen die u uploadt. Voor afbeeldingselementen kunt u ook opgeven welk afbeeldingsprofiel u wilt toepassen op afbeeldingselementen om deze op de juiste wijze te laten bijsnijden.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
docset: aem65
role: User, Admin
feature: Workflow,Asset Management,Renditions
exl-id: 3d9367ed-5a02-43aa-abd9-24fae457d4c5
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1337'
ht-degree: 0%

---

# Profielen voor het verwerken van metagegevens, afbeeldingen en video&#39;s{#profiles-for-processing-metadata-images-and-videos}

Een profiel is een recept voor welke opties u kunt toepassen op middelen die naar een map worden geüpload. U kunt bijvoorbeeld opgeven welk metagegevensprofiel en videocoderingsprofiel u wilt toepassen op video-elementen die u uploadt. Of welk afbeeldingsprofiel u wilt toepassen op afbeeldingselementen om deze op de juiste wijze te laten bijsnijden.

Deze regels kunnen het toevoegen van metagegevens, het slim uitsnijden van afbeeldingen of het instellen van videocoderingsprofielen omvatten. In Adobe Experience Manager kunt u drie typen profielen maken, die in detail worden besproken op de volgende koppelingen:

* [Metagegevensprofielen](/help/assets/metadata-config.md#metadata-profiles)
* [Afbeeldingsprofielen](/help/assets/image-profiles.md)
* [Videoprofielen](/help/assets/video-profiles.md)

U hebt beheerdersrechten nodig om metagegevens, afbeeldingen of videoprofielen te maken, te bewerken en te verwijderen.

Nadat u de metagegevens, de afbeelding of het videoprofiel hebt gemaakt, wijst u deze toe aan een of meer mappen die u gebruikt als bestemming voor nieuw geüploade elementen.

Een belangrijk concept voor het gebruik van profielen in Experience Manager Assets is dat deze aan mappen worden toegewezen. Binnen een profiel bevinden zich instellingen in de vorm van metagegevensprofielen, samen met videoprofielen of afbeeldingsprofielen. Met deze instellingen wordt de inhoud van een map samen met een van de submappen van de map verwerkt. Daarom heeft de manier waarop u bestanden en mappen benoemt, de manier waarop u submappen rangschikt en de manier waarop u de bestanden in deze mappen verwerkt, een grote invloed op de manier waarop deze elementen door een profiel worden verwerkt.
Door consistente en geschikte naamgevingsstrategieën voor bestanden en mappen en goede praktijken voor metagegevens te gebruiken, kunt u optimaal gebruikmaken van de verzameling van digitale elementen en ervoor zorgen dat de juiste bestanden door het juiste profiel worden verwerkt.

>[!NOTE]
>
>Assets die u van de ene map naar de andere verplaatst, wordt niet opnieuw verwerkt. Stel dat u Map 1 hebt waaraan profiel A is toegewezen en Map 2 waaraan profiel B is toegewezen. Als u elementen verplaatst van map 1 naar map 2, behouden de verplaatste elementen hun oorspronkelijke verwerking van map 1.
>
>Hetzelfde geldt ook wanneer u elementen verplaatst tussen twee mappen waaraan hetzelfde profiel is toegewezen.

## Elementen in een map opnieuw verwerken {#reprocessing-assets}

>[!NOTE]
>
>Is op *Dynamic Media van toepassing - de wijze van Scene7* slechts in Experience Manager 6.4.6.0 of later.

U kunt elementen opnieuw verwerken in een map die al een bestaand verwerkingsprofiel heeft dat u later hebt gewijzigd.

Stel dat u een afbeeldingsprofiel hebt gemaakt en dit aan een map hebt toegewezen. Bij alle afbeeldingselementen die u naar de map hebt geüpload, wordt het afbeeldingsprofiel automatisch toegepast op de elementen. Later besluit u echter om een nieuwe verhouding voor slimme uitsnijden toe te voegen aan het profiel. Nu, in plaats van het selecteren van en het opnieuw uploaden van de activa aan de omslag over, stelt u eenvoudig het *Dynamic Media opnieuw verwerken* <!-- *Scene7: Reprocess Assets* --> werkschema in werking.

U kunt de herverwerkingsworkflow uitvoeren op een element waarvoor de verwerking de eerste keer is mislukt. Zelfs als u geen verwerkingsprofiel hebt bewerkt of geen verwerkingsprofiel hebt toegepast, kunt u de workflow voor het opnieuw verwerken van een map met middelen op elk moment uitvoeren.

U kunt optioneel de batchgrootte van de workflow voor het opnieuw verwerken aanpassen van een standaard van 50 elementen tot 1000 elementen. Wanneer u _Scene7 in werking stelt: Het 1&rbrace; werkschema van Assets van het opnieuw verwerken &lbrace;op een omslag, worden de activa gegroepeerd in partijen, dan verzonden naar de server van Dynamic Media voor verwerking._ Na de verwerking worden de metagegevens van elk element in de volledige batchset bijgewerkt op Experience Manager. Als de partij groot is, kan er een vertraging optreden bij de verwerking. Als de batch te klein is, kunnen er te veel ronde overgangen naar de Dynamic Media-server plaatsvinden.

Zie [&#x200B; aanpassen de partijgrootte van het herproceswerkschema &#x200B;](#adjusting-load).

>[!NOTE]
>
>Als u een grote migratie van middelen van Dynamic Media Classic naar Experience Manager uitvoert, moet u de de replicatieagent van de Migratie op de server van Dynamic Media toelaten. Wanneer de migratie volledig is, zorg ervoor u de agent onbruikbaar maakt.
>
>De Migratie-publicatieagent moet zijn uitgeschakeld op de Dynamic Media-server, zodat de workflow voor opnieuw verwerken naar behoren functioneert.

<!-- Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media's Image Production System) job. When you run the Dynamic Media Reprocess workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job, and so on, until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. -->

**om activa in een omslag opnieuw te verwerken:**

1. Navigeer in Experience Manager vanaf de Assets-pagina naar een map met elementen waaraan een verwerkingsprofiel is toegewezen en waarvoor u de **[!UICONTROL Dynamic Media Reprocess]** -workflow wilt toepassen,

   Mappen waaraan al een verwerkingsprofiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam in de Kaartweergave weer te geven.

1. Selecteer een map.

   * In de workflow worden alle bestanden in de geselecteerde map recursief bekeken.
   * Als er een of meer submappen met elementen in de geselecteerde hoofdmap staan, worden alle elementen in de maphiërarchie opnieuw verwerkt.
   * U kunt het beste deze workflow niet uitvoeren in een mappenhiërarchie met meer dan 1000 elementen.

1. Selecteer in de vervolgkeuzelijst in de linkerbovenhoek van de pagina de optie **[!UICONTROL Timeline]** .
1. Selecteer in de linkerbenedenhoek van de pagina, rechts van het veld Opmerking, het karatpictogram ( **^** ).

   ![&#x200B; opnieuw verwerken activa werkschema 1 &#x200B;](/help/assets/assets/reprocess-assets1.png)

1. Selecteer **[!UICONTROL Start Workflow]** .
1. Kies **[!UICONTROL Dynamic Media Reprocess]** in de vervolgkeuzelijst **[!UICONTROL Start Workflow]** .
1. (Facultatief) op **ga titel van werkschemagebied** in, ga een naam voor het werkschema in. U kunt de naam gebruiken om naar de werkstroominstantie te verwijzen, indien nodig.

   ![&#x200B; opnieuw verwerken activa 2 &#x200B;](/help/assets/assets/reprocess-assets2.png)

1. Selecteer **[!UICONTROL Start]** en selecteer vervolgens **[!UICONTROL Confirm]** .

   Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** om de workflow te controleren of de voortgang ervan te controleren op de hoofdconsolepagina van de Experience Manager. Selecteer een workflow op de pagina Workflowinstanties. Selecteer **[!UICONTROL Open History]** op de menubalk. U kunt een geselecteerde workflow ook beëindigen, opschorten of de naam ervan wijzigen vanuit dezelfde pagina Workflowinstanties.

### De batchgrootte van de workflow voor opnieuw verwerken aanpassen {#adjusting-load}

(Optioneel) De standaardbatch-grootte in de opwerkingsworkflow is 50 elementen per taak. Deze optimale omvang van de partij wordt bepaald door de gemiddelde omvang van de activa en de MIME-typen van activa waarop het herproces wordt uitgevoerd. Een hogere waarde betekent dat u veel bestanden in één opwerkingstaak hebt. De verwerkingsbanner blijft dus langer op Experience Manager-elementen. Als de gemiddelde bestandsgrootte echter klein is - 1 MB of kleiner - raadt de Adobe u aan de waarde te verhogen tot enkele 100, maar nooit meer dan 1000. Als de gemiddelde bestandsgrootte groot is, bijvoorbeeld honderden megabytes, kunt u het beste de batchgrootte tot 10 verkleinen.

**om naar keuze de partijgrootte van het herproceswerkschema aan te passen:**

1. Selecteer in Experience Manager **[!UICONTROL Adobe Experience Manager]** om toegang te krijgen tot de algemene navigatieconsole en selecteer vervolgens het pictogram **[!UICONTROL Tools]** (hamer) > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .
1. Selecteer **[!UICONTROL Dynamic Media Reprocess]** op de pagina Workflowmodellen in Kaartweergave of Lijstweergave.

   ![&#x200B; pagina van de Modellen van het Werkschema van het Werkschema met Dynamic Media die werkschema in de Mening van de Kaart wordt geselecteerd &#x200B;](/help/assets/assets-dm/reprocess-assets7.png)

1. Selecteer **[!UICONTROL Edit]** op de werkbalk. Een nieuw browsertabblad opent de pagina Dynamic Media Reprocess workflowmodel.
1. Selecteer in de rechterbovenhoek van de Dynamic Media Reprocess workflowpagina **[!UICONTROL Edit]** om de workflow te &quot;ontgrendelen&quot;.
1. Selecteer in de workflow de component Scene7 Batch Upload (-batch uploaden) om de werkbalk te openen en selecteer vervolgens **[!UICONTROL Configure]** op de werkbalk.

   ![&#x200B; de Partij van Scene7 uploadt component &#x200B;](/help/assets/assets-dm/reprocess-assets8.png)

1. Stel in het dialoogvenster **[!UICONTROL Batch Upload to Scene7 – Step Properties]** het volgende in:
   * Voer in de tekstvelden **[!UICONTROL Title]** en **[!UICONTROL Description]** desgewenst een nieuwe titel en beschrijving in voor de taak.
   * Selecteer **[!UICONTROL Handler Advance]** als de handler de volgende stap uitvoert.
   * Voer in het veld **[!UICONTROL Timeout]** de time-out van het externe proces (seconden) in.
   * Voer in het veld **[!UICONTROL Period]** een pollinginterval (seconden) in om te testen of het externe proces is voltooid.
   * Voer in de **[!UICONTROL Batch field]** het maximumaantal elementen (50-1000) in dat u wilt verwerken in een uploadtaak voor de batchverwerking van een Dynamic Media-server.
   * Selecteer **[!UICONTROL Advance on timeout]** als u wilt doorgaan wanneer de time-out is bereikt. Annuleer de selectie als u wilt doorgaan naar het Postvak IN wanneer de time-out is bereikt.

   ![&#x200B; de dialoogdoos van Eigenschappen &#x200B;](/help/assets/assets-dm/reprocess-assets3.png)

1. Selecteer **[!UICONTROL Done]** in de rechterbovenhoek van het dialoogvenster **[!UICONTROL Batch Upload to Scene7 – Step Properties]** .

1. Selecteer **[!UICONTROL Sync]** in de rechterbovenhoek van de pagina Dynamic Media Reprocess workflowmodel. Wanneer u **[!UICONTROL Synced]** ziet, wordt het runtimemodel van de workflow gesynchroniseerd en kunt u elementen in een map opnieuw verwerken.

   ![&#x200B; synchroniseer het werkschemamodel &#x200B;](/help/assets/assets-dm/reprocess-assets1.png)

1. Sluit het browsertabblad waarin het workflowmodel voor opnieuw verwerken van Dynamic Media wordt weergegeven.

<!--1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, select **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then select the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite]**.
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/assets/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, select **[!UICONTROL Add]**. The new property appears as the following:

    ![Saving the new property](/help/assets/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, select **[!UICONTROL Save All]**.
1. In the upper-left corner of the page, select **[!UICONTROL CRXDE Lite]** to return to the main Experience Manager console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Dynamic Media Reprocess workflow model.-->
