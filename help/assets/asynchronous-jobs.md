---
title: Asynchrone bewerkingen
description: De Elementen van de Manager van de ervaring optimaliseert prestaties door sommige middel-intensieve taken asynchroon te voltooien.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 566add37d6dd7efe22a99fc234ca42878f050aee
workflow-type: tm+mt
source-wordcount: '595'
ht-degree: 2%

---


# Asynchrone bewerkingen {#asynchronous-operations}

Om negatieve gevolgen voor de prestaties te beperken, verwerkt Adobe Experience Manager Assets bepaalde langlopende en bronnenintensieve middelenbewerkingen asynchroon.

Deze bewerkingen omvatten:

* Veel elementen verwijderen
* Veel elementen of elementen met veel verwijzingen verplaatsen
* Metagegevens van elementen bulksgewijs exporteren/importeren.
* Elementen ophalen die boven de ingestelde drempelwaarde liggen, vanaf een implementatie van een extern Experience Manager.

Asynchrone verwerking omvat het onderzoeken van veelvoudige banen en uiteindelijk het leiden van hen op een periodieke manier afhankelijk van de beschikbaarheid van systeemmiddelen.

U kunt de status van asynchrone taken vanaf de **[!UICONTROL Async Job Status]** pagina weergeven.

>[!NOTE]
>
>Taken in Elementen worden standaard parallel uitgevoerd. Als N het aantal CPU-cores is, kunnen N/2-taken standaard parallel worden uitgevoerd. Als u aangepaste instellingen voor de taakwachtrij wilt gebruiken, wijzigt u de **[!UICONTROL Async Operation Default Queue]** configuratie via de webconsole. Voor meer informatie, zie [rijconfiguraties](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## De status van asynchrone bewerkingen controleren {#monitoring-the-status-of-asynchronous-operations}

Telkens wanneer Elementen een verrichting asynchroon verwerken, ontvangt u een bericht bij uw inbox en door e-mail.

Navigeer naar de **[!UICONTROL Async Job Status]** pagina om de status van de asynchrone bewerkingen in detail weer te geven.

1. Klik in de interface Experience Manager op **[!UICONTROL Operations]** > **[!UICONTROL Jobs]**.

1. Controleer in de **[!UICONTROL Async Job Status]** pagina de details van de bewerkingen.

   ![Status en details van asynchrone bewerkingen](assets/AsyncOperation-status.png)

   Zie de waarde in de **[!UICONTROL Status]** kolom voor informatie over de voortgang van een bepaalde bewerking. Afhankelijk van de voortgang wordt een van de volgende statussen weergegeven:

   * **[!UICONTROL Active]**: De bewerking wordt verwerkt

   * **[!UICONTROL Success]**: De bewerking is voltooid

   * **[!UICONTROL Fail]** of **[!UICONTROL Error]**: De bewerking kan niet worden verwerkt

   * **[!UICONTROL Scheduled]**: De bewerking is gepland voor verwerking op een later tijdstip

1. Als u een actieve bewerking wilt stoppen, selecteert u deze in de lijst en klikt u op **[!UICONTROL Stop]** de werkbalk.

   ![stop_icon](assets/stop_icon.png)

1. Als u meer details wilt weergeven, bijvoorbeeld een beschrijving en logboekbestanden, selecteert u de bewerking en klikt u in de werkbalk **[!UICONTROL Open]** .

   ![open_icon](assets/open_icon.png)

   De pagina met taakdetails wordt weergegeven.

   ![job_details](assets/job_details.png)

1. Als u de bewerking uit de lijst wilt verwijderen, selecteert u deze op de werkbalk. **[!UICONTROL Delete]** Klik op **[!UICONTROL Download]** CSV om de gegevens in een CSV-bestand te downloaden.

   >[!NOTE]
   >
   >U kunt een taak niet verwijderen als de status actief is of in de wachtrij staat.

## Voltooide taken wissen {#purging-completed-jobs}

De Middelen van de Manager van de ervaring stelt een zuiveringstaak elke dag om 1:00 AM in werking om voltooide asynchrone banen te schrappen die meer dan een dag oud zijn.

U kunt het schema voor de zuiveringstaak en de duur wijzigen waarvoor de details van voltooide banen worden behouden alvorens zij worden geschrapt. U kunt ook het maximumaantal voltooide taken configureren waarvoor de details op elk gewenst moment behouden blijven.

1. Klik in de interface van Experience Manager op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open de **[!UICONTROL Adobe CQ DAM Async Jobs Purge Scheduled]** taak.
1. Vermeld het drempelaantal dagen waarna voltooide taken worden verwijderd en het maximumaantal banen waarvoor gegevens in de geschiedenis worden bewaard.

   ![Configuratie om het leegmaken van asynchrone taken te plannen](assets/configmgr_purge_asyncjobs.png)

1. Sla de wijzigingen op.

## Drempels voor asynchrone verwerking configureren {#configuring-thresholds-for-asynchronous-processing}

U kunt het drempelaantal elementen of verwijzingen voor Elementen configureren om een bepaalde bewerking asynchroon te verwerken.

### Drempelwaarden configureren voor asynchrone verwijderingsbewerkingen {#configuring-thresholds-for-asynchronous-delete-operations}

Als het aantal te verwijderen elementen of mappen de drempelwaarde overschrijdt, wordt de verwijderbewerking asynchroon uitgevoerd.

1. Klik in de interface van Experience Manager op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open de **[!UICONTROL Async Delete Operation Job Processing]** configuratie vanuit de webconsole.
1. Geef in het **[!UICONTROL Threshold number of assets]** vak het drempelaantal elementen/mappen op voor de asynchrone verwerking van verwijderingsbewerkingen.

   ![delete_threshold](assets/delete_threshold.png)

1. Sla de wijzigingen op.

### Drempels voor asynchrone verplaatsingsbewerkingen configureren {#configuring-thresholds-for-asynchronous-move-operations}

Als het aantal te verplaatsen elementen/mappen of verwijzingen het drempelnummer overschrijdt, wordt de verplaatsingsbewerking asynchroon uitgevoerd.

1. Klik in de interface van Experience Manager op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open de **[!UICONTROL Async Move Operation Job Processing]** configuratie vanuit de webconsole.
1. Geef in het **[!UICONTROL Threshold number of assets/references]** vak het drempelaantal elementen/mappen of verwijzingen op voor de asynchrone verwerking van verplaatsingsbewerkingen.

   ![move_threshold](assets/move_threshold.png)

1. Sla de wijzigingen op.
