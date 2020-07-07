---
title: Configureer asynchrone bewerkingen in [!DNL-Adobe Experience Manager].
description: U kunt asynchroon een aantal bronnenintensieve taken uitvoeren om de prestaties te optimaliseren in [!DNL Experience Manager Assets].
contentOwner: AG
translation-type: tm+mt
source-git-commit: b59f7471ab9f3c5e6eb3365122262b592c8e6244
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 2%

---


# Asynchrone bewerkingen {#asynchronous-operations}

Om negatieve gevolgen voor prestaties te verminderen, [!DNL Adobe Experience Manger Assets] verwerkt bepaalde langlopende en middel-intensieve activa verrichtingen asynchroon. Asynchrone verwerking omvat het navragen van veelvoudige taken en uiteindelijk het uitvoeren van hen op een periodieke manier afhankelijk van de beschikbaarheid van systeemmiddelen. Deze bewerkingen omvatten:

* Veel elementen verwijderen.
* Veel elementen of elementen met veel verwijzingen verplaatsen.
* Metagegevens van elementen bulksgewijs exporteren en importeren.
* Het vinden van activa van een verre [!DNL Experience Manager] plaatsing, die meer dan een vastgestelde drempelgrens zijn. De limiet geldt voor het aantal activa.

U kunt de status van asynchrone taken vanaf de **[!UICONTROL Async Job Status]** pagina weergeven.

>[!NOTE]
>
>Standaard worden de [!DNL Assets] taken parallel uitgevoerd. Als `N` het aantal CPU-cores is, kunnen `N/2` taken standaard parallel worden uitgevoerd. Om douanemontages voor de taakrij te gebruiken, wijzig de **[!UICONTROL Async Operation Default Queue]** configuratie van [!UICONTROL Web Console]. Voor meer informatie, zie [rijconfiguraties](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## De status van asynchrone bewerkingen controleren {#monitoring-the-status-of-asynchronous-operations}

Wanneer [!DNL Assets] u een bewerking asynchroon verwerkt, ontvangt u een melding in uw [!DNL Experience Manager] Postvak [IN](/help/sites-authoring/inbox.md) en via een e-mail. Navigeer naar de **[!UICONTROL Async Job Status]** pagina om de status van de asynchrone bewerkingen in detail weer te geven.

1. Klik in de [!DNL Experience Manager] interface op **[!UICONTROL Operations]** > **[!UICONTROL Jobs]**.

1. Controleer in de **[!UICONTROL Async Job Status]** pagina de details van de bewerkingen.

   ![Status en details van asynchrone bewerkingen](assets/AsyncOperation-status.png)

   Zie de **[!UICONTROL Status]** kolom voor meer informatie over de voortgang van een bewerking. Afhankelijk van de voortgang wordt een van de volgende statussen weergegeven:

   * **[!UICONTROL Active]**: De bewerking wordt verwerkt.
   * **[!UICONTROL Success]**: De bewerking is voltooid.
   * **[!UICONTROL Fail]** of **[!UICONTROL Error]**: De bewerking kan niet worden verwerkt.
   * **[!UICONTROL Scheduled]**: De bewerking is gepland voor verwerking op een later tijdstip.

1. Als u een actieve bewerking wilt stoppen, selecteert u deze in de lijst en klikt u op het pictogram **[!UICONTROL Stop]** ![](assets/do-not-localize/stop_icon.svg) Stoppen op de werkbalk.

1. Als u extra details wilt weergeven, bijvoorbeeld beschrijving en logbestanden, selecteert u de bewerking en klikt u op **[!UICONTROL Open]** open_icon ![](assets/do-not-localize/edit_icon.svg) op de werkbalk. De pagina met taakdetails wordt weergegeven.

   ![Details van een importtaak voor metagegevens](assets/job_details.png)

1. Als u de bewerking uit de lijst wilt verwijderen, selecteert u deze op de werkbalk. **[!UICONTROL Delete]** Klik op **[!UICONTROL Download]** CSV om de gegevens in een CSV-bestand te downloaden.

   >[!NOTE]
   >
   >U kunt een taak niet verwijderen als de status actief is of in de wachtrij staat.

## Voltooide taken wissen {#purge-completed-tasks}

[!DNL Experience Manager Assets] Voert een zuiveringstaak elke dag bij 100 uren uit om voltooide asynchrone taken te schrappen die meer dan een dag oud zijn.

<!-- TBD: Find out from the engineering team and mention the time zone of this 1:00 am task.
-->

U kunt het programma voor de zuiveringstaak en de duur wijzigen waarvoor de details van voltooide taken worden behouden alvorens zij worden geschrapt. U kunt ook het maximale aantal voltooide taken configureren waarvoor de details op elk gewenst moment behouden blijven.

1. Klik in de [!DNL Experience Manager] interface **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open de **[!UICONTROL Adobe CQ DAM Async Jobs Purge Scheduled]** taak.
1. Geef het drempelaantal dagen op waarna voltooide taken worden verwijderd en het maximumaantal taken waarvoor details in de geschiedenis worden bewaard. Sla de wijzigingen op.

   ![Configuratie om het zuiveren van asynchrone taken te plannen](assets/configmgr_purge_asyncjobs.png)

## Drempel configureren voor asynchrone verwijderingsbewerkingen {#configure-thresholds-for-asynchronous-delete-operations}

Als het aantal elementen of mappen dat moet worden verwijderd, de ingestelde drempelwaarde overschrijdt, wordt de verwijderbewerking asynchroon uitgevoerd.

1. Klik in de [!DNL Experience Manager] interface **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open de [!UICONTROL Web Console]configuratie vanuit de **[!UICONTROL Async Delete Operation Job Processing]** toepassing.
1. Geef in het **[!UICONTROL Threshold number of assets]** vak de drempelnummers op voor het asynchroon verwijderen van elementen, mappen of verwijzingen. Sla de wijzigingen op.

   ![De drempellimiet instellen voor de taak om elementen te verwijderen](assets/delete_threshold.png)

## Drempel voor asynchrone verplaatsingsbewerkingen configureren {#configure-thresholds-for-asynchronous-move-operations}

Als het aantal te verplaatsen elementen, mappen of verwijzingen het ingestelde drempelnummer overschrijdt, wordt de verplaatsingsbewerking asynchroon uitgevoerd.

1. Klik in de [!DNL Experience Manager] interface op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open de [!UICONTROL Web Console]configuratie vanuit de **[!UICONTROL Async Move Operation Job Processing]** toepassing.
1. Geef in het **[!UICONTROL Threshold number of assets/references]** vak de drempelnummers op voor het asynchroon verplaatsen van elementen, mappen of verwijzingen. Sla de wijzigingen op.

   ![De drempellimiet instellen voor de taak om elementen te verplaatsen](assets/move_threshold.png)

>[!MORELIKETHIS]
>
>* [E-mail configureren in Experience Manager](/help/sites-administering/notification.md).
>* [Metagegevens van elementen in bulk](/help/assets/metadata-import-export.md)importeren en exporteren.
>* [Gebruik Connected Assets om DAM-middelen van externe implementaties](/help/assets/use-assets-across-connected-assets-instances.md)te delen.

