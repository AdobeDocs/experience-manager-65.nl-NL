---
title: Profielen voor het verwerken van metagegevens, afbeeldingen en video's
description: Een profiel is een set regels met betrekking tot de opties die moeten worden toegepast op elementen die naar een map zijn geüpload. Geef op welk metagegevensprofiel en videocoderingsprofiel u wilt toepassen op de video-elementen die u uploadt. Voor afbeeldingselementen kunt u ook opgeven welk afbeeldingsprofiel u wilt toepassen op afbeeldingselementen om deze op de juiste wijze te laten bijsnijden.
uuid: 6ded2a2f-a0d3-4f43-af97-02fbc0902c25
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
discoiquuid: b555bf0c-44cb-4fbf-abc4-15971663904d
docset: aem65
translation-type: tm+mt
source-git-commit: 5f3af7041029a1b4dd1cbb4c65bd488b62c7e10c
workflow-type: tm+mt
source-wordcount: '1317'
ht-degree: 2%

---


# Profielen voor het verwerken van metagegevens, afbeeldingen en video&#39;s{#profiles-for-processing-metadata-images-and-videos}

Een profiel is een recept voor welke opties u kunt toepassen op middelen die naar een map worden geüpload. U kunt bijvoorbeeld opgeven welk metagegevensprofiel en videocoderingsprofiel u wilt toepassen op video-elementen die u uploadt. Of welk afbeeldingsprofiel u wilt toepassen op afbeeldingselementen om deze op de juiste wijze te laten bijsnijden.

Deze regels kunnen het toevoegen van metagegevens, het slim uitsnijden van afbeeldingen of het instellen van videocoderingsprofielen omvatten. In AEM kunt u drie typen profielen maken, die in detail worden besproken op de volgende koppelingen:

* [Metadataprofielen](/help/assets/metadata-profiles.md)
* [Afbeeldingsprofielen](/help/assets/image-profiles.md)
* [Videoprofielen](/help/assets/video-profiles.md)

U moet beheerdersrechten hebben om metagegevens, afbeeldingen of videoprofielen te maken, te bewerken en te verwijderen.

Nadat u de metagegevens, de afbeelding of het videoprofiel hebt gemaakt, wijst u deze toe aan een of meer mappen die u gebruikt als bestemming voor nieuw geüploade elementen.

Een belangrijk concept voor het gebruik van profielen in AEM Assets is dat deze aan mappen worden toegewezen. Binnen een profiel bevinden zich instellingen in de vorm van metagegevensprofielen, samen met videoprofielen of afbeeldingsprofielen. Met deze instellingen wordt de inhoud van een map samen met een van de submappen verwerkt. Daarom heeft de manier waarop u bestanden en mappen benoemt, hoe u submappen ordent en hoe u de bestanden in deze mappen verwerkt, een grote invloed op de manier waarop deze elementen door een profiel worden verwerkt.
Door consistente en geschikte naamgevingsstrategieën voor bestanden en mappen te gebruiken, samen met goede praktijken voor metagegevens, kunt u optimaal gebruikmaken van de verzameling van digitale elementen en ervoor zorgen dat de juiste bestanden worden verwerkt door het juiste profiel.

>[!NOTE]
>
>Elementen die u van de ene map naar de andere verplaatst, worden niet opnieuw verwerkt. Stel dat u Map 1 hebt waaraan profiel A is toegewezen en Map 2 waaraan profiel B is toegewezen. Als u elementen verplaatst van map 1 naar map 2, behouden de verplaatste elementen hun oorspronkelijke verwerking van map 1.
>
>Hetzelfde geldt ook wanneer u elementen verplaatst tussen twee mappen waaraan hetzelfde profiel is toegewezen.

## Elementen in een map opnieuw verwerken {#reprocessing-assets}

>[!NOTE]
>
>Is op *Dynamische Media van toepassing - wijze* Scene7 slechts in AEM 6.4.6.0 of later.

U kunt elementen opnieuw verwerken in een map die al een bestaand verwerkingsprofiel heeft dat u later hebt gewijzigd.

Stel dat u een afbeeldingsprofiel hebt gemaakt en dit aan een map hebt toegewezen. Bij alle afbeeldingselementen die u naar de map hebt geüpload, wordt het afbeeldingsprofiel automatisch toegepast op de elementen. Later besluit u echter om een nieuwe verhouding voor slimme uitsnijden toe te voegen aan het profiel. Nu, in plaats van het selecteren van en het opnieuw uploaden van de activa aan de omslag over, stelt u eenvoudig *Scene7 in werking: Workflow Elementen* opnieuw verwerken.

U kunt de herverwerkingsworkflow uitvoeren op een element waarvoor de verwerking de eerste keer is mislukt. Zelfs als u geen verwerkingsprofiel hebt bewerkt of geen verwerkingsprofiel hebt toegepast, kunt u de herverwerkingsworkflow op elk gewenst moment op een map met middelen uitvoeren.

U kunt optioneel de batchgrootte van de workflow voor het opnieuw verwerken aanpassen van een standaard van 50 elementen tot 1000 elementen. Wanneer u _Scene7 in werking stelt: De workflow Middelen_ in een map opnieuw verwerken. Elementen worden gegroepeerd in batches en vervolgens naar de Dynamic Media-server verzonden voor verwerking. Na de verwerking worden de metagegevens van elk element in de volledige batchset bijgewerkt in AEM. Als de partij erg groot is, kan er een vertraging optreden bij de verwerking. Als de batch te klein is, kunnen er te veel ronde overgangen naar de Dynamic Media-server plaatsvinden.

Zie De [batchgrootte van de workflow](#adjusting-load)voor opnieuw verwerken aanpassen.

>[!NOTE]
>
>Als u een bulkmigratie van activa van Dynamic Media Classic aan AEM uitvoert, moet u de de replicatieagent van de Migratie op de Dynamische server van Media toelaten. Wanneer de migratie volledig is, zorg ervoor u de agent onbruikbaar maakt.
De migratiepublicatieagent moet zijn uitgeschakeld op de Dynamic Media-server, zodat de workflow voor opnieuw verwerken naar behoren werkt.

<!-- Batch size is the number of assets that are amalgamated into a single IPS (Dynamic Media’s Image Production System) job. When you run the Scene7: Reprocess Assets workflow, the job is triggered on IPS. The number of IPS jobs that are triggered is based on the total number of assets in the folder, divided by the batch size. For example, suppose you had a folder with 150 assets and a batch size of 50. In this case, three IPS jobs are triggered. The assets are updated when the entire batch size (50 in our example) is processed in IPS. The job then moves onto the next IPS job and so on until complete. If you increase the batch size, you may notice a longer delay with assets getting updated. -->

**Elementen in een map** opnieuw verwerken:
1. In AEM, van de pagina van Activa, navigeer aan een omslag van activa die een verwerkingsprofiel heeft dat aan het wordt toegewezen en waarvoor u **Scene7 wilt toepassen: Workflow voor opnieuw verwerken van bedrijfsmiddelen** ,

   Mappen waaraan al een verwerkingsprofiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam in de Kaartweergave weer te geven.

1. Selecteer een map.

   * In de workflow worden alle bestanden in de geselecteerde map recursief bekeken.
   * Als er een of meer submappen met elementen in de geselecteerde hoofdmap staan, wordt elk element in de mappenhiërarchie opnieuw verwerkt.
   * U kunt het beste deze workflow niet uitvoeren in een mappenhiërarchie met meer dan 1000 elementen.

1. Klik in de linkerbovenhoek van de pagina in de vervolgkeuzelijst op **[!UICONTROL Timeline]**.
1. Klik in de linkerbenedenhoek van de pagina, rechts van het veld Opmerking, op het pictogram van het karaat ( **^** ).

   ![Workflow 1 voor opnieuw verwerken van middelen](/help/assets/assets/reprocess-assets1.png)

1. Klik op **[!UICONTROL Start Workflow]**.
1. From the **[!UICONTROL Start Workflow]** drop-down list, choose **[!UICONTROL Scene7: Reprocess Assets]**.
1. (Optioneel) Voer in het tekstveld Titel **invoeren van workflow** een naam in voor de workflow. U kunt de naam gebruiken om naar de werkstroominstantie te verwijzen, indien nodig.

   ![Activa opnieuw verwerken 2](/help/assets/assets/reprocess-assets2.png)

1. Klik **[!UICONTROL Start]** en klik vervolgens op **[!UICONTROL Confirm]**.

   Klik op de hoofdconsolepagina van AEM om de workflow te controleren of de voortgang te controleren. **[!UICONTROL Tools > Workflow]** Klik op de pagina met de AEM-hoofdconsole. Selecteer een workflow op de pagina Workflowinstanties. Klik op de menubalk **[!UICONTROL Open History]**. U kunt een geselecteerde workflow ook beëindigen, opschorten of hernoemen vanuit dezelfde pagina Workflowinstanties.

### De batchgrootte van de workflow voor opnieuw verwerken aanpassen {#adjusting-load}

(Optioneel) De standaardbatch-grootte in de opwerkingsworkflow is 50 elementen per taak. Deze optimale omvang van de partij wordt bepaald door de gemiddelde omvang van de activa en de MIME-typen van activa waarop het herproces wordt uitgevoerd. Een hogere waarde betekent dat u veel bestanden in één herverwerkingstaak hebt. De verwerkingsbanner blijft daarom langer op AEM-elementen staan. Als de gemiddelde bestandsgrootte echter klein-1 MB of kleiner is, raadt Adobe u aan de waarde te verhogen tot enkele honderden, maar nooit meer dan 1000. Als de gemiddelde bestandsgrootte groot is tot honderden megabytes, raadt Adobe u aan de batch tot 10 te verkleinen.

**De batchgrootte van de workflow voor opnieuw verwerken optioneel aanpassen**

1. Tik in Experience Manager op **[!UICONTROL Adobe Experience Manager]** om naar de globale navigatieconsole te gaan en tik vervolgens op het pictogram **[!UICONTROL Tools]** (hamer) > **[!UICONTROL Workflow > Models]**.
1. Selecteer op de pagina Workflowmodellen in Kaartweergave of Lijstweergave de optie **[!UICONTROL Scene7: Reprocess Assets]**.

   ![De pagina van Modellen van het werkschema met Scene7: Workflow voor opnieuw verwerken van middelen die zijn geselecteerd in Kaartweergave](/help/assets/assets-dm/reprocess-assets7.png)

1. Klik op de werkbalk **[!UICONTROL Edit]**. Een nieuw browser lusje opent Scene7: Modelpagina voor middelenwerkstroom opnieuw verwerken.
1. Op Scene7: Tik in de rechterbovenhoek op de pagina voor de nieuwe middelenworkflow **[!UICONTROL Edit]** om de workflow te ontgrendelen.
1. In het werkschema, selecteer de Partij Scene7 uploadt component om de toolbar te openen, dan tik op **[!UICONTROL Configure]** de toolbar.

   ![Scene7 Partij uploaden component](/help/assets/assets-dm/reprocess-assets8.png)

1. Stel in het **[!UICONTROL Batch Upload to Scene7—Step Properties]** dialoogvenster het volgende in:
   * In the **[!UICONTROL Title]** and **[!UICONTROL Description]** text fields, enter a new title and description for the job, if desired.
   * Selecteer **[!UICONTROL Handler Advance]** als uw manager aan de volgende stap zal verdergaan.
   * Voer in het **[!UICONTROL Timeout]** veld de time-out van het externe proces (seconden) in.
   * Voer in het **[!UICONTROL Period]** veld een pollinginterval (seconden) in om te testen of het externe proces is voltooid.
   * In the **[!UICONTROL Batch field]**, enter the maximum number of assets (50-1000) to process in a Dynamic Media server batch processing upload job.
   * Selecteer **[!UICONTROL Advance on timeout]** als u wilt vooruitgaan wanneer de onderbreking wordt bereikt. Schakel deze optie uit als u wilt doorgaan naar het Postvak IN wanneer de time-out is bereikt.
   ![Eigenschappen, dialoogvenster](/help/assets/assets-dm/reprocess-assets3.png)

1. Tik in de rechterbovenhoek van het **[!UICONTROL Batch Upload to Scene7 – Step Properties]** dialoogvenster op **[!UICONTROL Done]**.

1. In de hoger-juiste hoek van Scene7: Pagina met het workflowmodel voor opnieuw verwerken van middelen tikken **[!UICONTROL Sync]**. Wanneer u ziet **[!UICONTROL Synced]**, wordt het model van de werkstroomruntime gesynchroniseerd en is het klaar om elementen in een map opnieuw te verwerken.

   ![Het workflowmodel synchroniseren](/help/assets/assets-dm/reprocess-assets1.png)

1. Sluit het browser lusje dat Scene7 toont: Workflowmodel voor opnieuw verwerken van middelen.

<!--1. Return to the browser tab that has the open Workflow Models page, then press **Esc** to exit the selection.
1. In the upper-left corner of the page, tap **[!UICONTROL Adobe Experience Manager]** to access the global navigation console, then tap the **[!UICONTROL Tools]** (hammer) icon > **[!UICONTROL General > CRXDE Lite]**.
1. In the folder tree on the left side of the CRXDE Lite page, navigate to the following location:

   `/conf/global/settings/workflow/models/scene7_reprocess_assets/jcr:content/flow/reprocess/metaData`

   ![CRXDE Lite](/help/assets/assets/workflow-models9.png)

1. On the right side of the CRXDE Lite page, in the lower portion, enter the following name, type, and value in its respective field:
    * **[!UICONTROL Name]**: `reprocess-batch-size`
    * **[!UICONTROL Type]**: `Long`
    * **[!UICONTROL Value]**: enter a default value (50-1000) for the batch size
1. In the lower-right corner, tap **[!UICONTROL Add]**. The new property appears as the following:

    ![Saving the new property](/help/assets/assets/workflow-models10.png)

1. On the menu bar of the CRXDE Lite page, tap **[!UICONTROL Save All]**.
1. In the upper-left corner of the page, tap **[!UICONTROL CRXDE Lite]** to return to the main AEM console
1. Repeat steps 1-7 to re-synchronize the new batch size to the Scene7: Reprocess Assets workflow model.-->
