---
title: Asynchrone bewerkingen
description: Adobe Experience Manager optimaliseert prestaties door sommige middel-intensieve taken asynchroon te voltooien.
translation-type: tm+mt
source-git-commit: 69b90432ac6028a64f36300819e1bead1ae8d671
workflow-type: tm+mt
source-wordcount: '771'
ht-degree: 2%

---


# Asynchrone bewerkingen {#asynchronous-operations}

Om negatieve gevolgen voor de prestaties te verminderen, verwerkt Adobe Experience Manager bepaalde langlopende en middelintensieve bewerkingen asynchroon.

Deze bewerkingen omvatten:

* Veel elementen verwijderen
* Veel elementen of elementen met veel verwijzingen verplaatsen
* Metagegevens van elementen bulksgewijs exporteren/importeren
* Middelen ophalen die boven de ingestelde drempelwaarde liggen, vanaf een Experience Manager-implementatie op afstand
* Pagina&#39;s verplaatsen
* Actieve exemplaren uitrollen

Asynchrone verwerking omvat het onderzoeken van veelvoudige banen en het runnen van hen op een periodieke manier afhankelijk van de beschikbaarheid van systeemmiddelen.

U kunt de status van asynchrone taken weergeven vanaf het **[!UICONTROL Async Job Status]** dashboard op **Algemene navigatie** -> **Gereedschappen** -> **Bewerkingen** -> **Taken**.

>[!NOTE]
>
>asynchrone taken worden standaard parallel uitgevoerd. Als *`n`* het aantal CPU-cores is, kunnen *`n/2`* taken standaard parallel worden uitgevoerd. Als u aangepaste instellingen voor de taakwachtrij wilt gebruiken, wijzigt u de configuratie Verplaatsen en Uitvoeren van de **[!UICONTROL Async Operation Default Queue Config]** bewerkingspagina en de configuratie **** Async vanuit de webconsole.
>
>Voor meer informatie, zie [rijconfiguraties](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## De status van asynchrone bewerkingen controleren {#monitor-the-status-of-asynchronous-operations}

Wanneer AEM een verrichting asynchroon verwerkt, ontvangt u een bericht in uw inbox en door e-mail (als toegelaten).

Navigeer naar de **[!UICONTROL Async Job Status]** pagina om de status van de asynchrone bewerkingen in detail weer te geven.

1. Klik in de Experience Manager-interface **[!UICONTROL Operations]** > **[!UICONTROL Jobs]**.

1. Controleer in de **[!UICONTROL Async Job Status]** pagina de details van de bewerkingen.

   ![Status en details van asynchrone bewerkingen](assets/async-operation-status.png)

   Zie de waarde in de **[!UICONTROL Status]** kolom voor informatie over de voortgang van een bepaalde bewerking. Afhankelijk van de voortgang wordt een van de volgende statussen weergegeven:

   * **[!UICONTROL Active]**: De bewerking wordt verwerkt

   * **[!UICONTROL Success]**: De bewerking is voltooid

   * **[!UICONTROL Fail]** of **[!UICONTROL Error]**: De bewerking kan niet worden verwerkt

   * **[!UICONTROL Scheduled]**: De bewerking is gepland voor verwerking op een later tijdstip

1. Als u een actieve bewerking wilt stoppen, selecteert u deze in de lijst en klikt u op **[!UICONTROL Stop]** de werkbalk.

   ![stop_icon](assets/async-stop-icon.png)

1. Als u meer details wilt weergeven, bijvoorbeeld een beschrijving en logboekbestanden, selecteert u de bewerking en klikt u in de werkbalk **[!UICONTROL Open]** .

   ![open_icon](assets/async-open-icon.png)

   De pagina met taakdetails wordt weergegeven.

   ![job_details](assets/async-job-details.png)

1. Als u de bewerking uit de lijst wilt verwijderen, selecteert u deze op de werkbalk. **[!UICONTROL Delete]** Klik op **[!UICONTROL Download]** CSV om de gegevens in een CSV-bestand te downloaden.

   >[!NOTE]
   >
   >U kunt een taak niet verwijderen als de status **Actief** of **In wachtrij** is.

## Voltooide taken wissen {#purging-completed-jobs}

AEM voert elke dag om 10:00 een zuiveringstaak uit om voltooide asynchrone banen te schrappen die meer dan een dag oud zijn.

U kunt het schema voor de zuiveringstaak en de duur wijzigen waarvoor de details van voltooide banen worden behouden alvorens zij worden geschrapt. U kunt ook het maximumaantal voltooide taken configureren waarvoor de details op elk gewenst moment behouden blijven.

1. Klik in de globale navigatie **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open de **[!UICONTROL Adobe Granite Async Jobs Purge Scheduled Job]** taak.
1. Opgeven:
   * Het drempelaantal dagen waarna voltooide taken worden verwijderd.
   * Het maximumaantal banen waarvoor gegevens in de geschiedenis worden bewaard.
   * De expressie voor uitsnijden waarin moet worden aangegeven wanneer de purge moet worden uitgevoerd.

   ![Configuratie om het leegmaken van asynchrone taken te plannen](assets/async-purge-job.png)

1. Sla de wijzigingen op.

## Asynchrone verwerking configureren {#configuring-asynchronous-processing}

U kunt het drempelaantal elementen, pagina&#39;s of verwijzingen voor AEM configureren om een bepaalde bewerking asynchroon te verwerken en om e-mailmeldingen in en uit te schakelen wanneer de taken worden verwerkt.

### Asynchrone bewerkingen voor het verwijderen van elementen configureren {#configuring-synchronous-delete-operations}

Als het aantal te verwijderen elementen of mappen de drempelwaarde overschrijdt, wordt de verwijderbewerking asynchroon uitgevoerd.

1. Klik in de globale navigatie **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open vanuit de webconsole de **[!UICONTROL Async Process Default Queue Configuration.]**
1. Geef in het **[!UICONTROL Threshold number of assets]** vak het drempelaantal elementen/mappen op voor de asynchrone verwerking van verwijderingsbewerkingen.

   ![Drempel voor verwijderen van element](assets/async-delete-threshold.png)

1. Schakel de optie E-mailmelding **** inschakelen in om e-mailmeldingen voor deze taakstatus te ontvangen. Bijvoorbeeld succes, mislukt.
1. Sla de wijzigingen op.

### Asynchrone verplaatsingsbewerkingen voor middelen configureren {#configuring-asynchronous-move-operations}

Als het aantal te verplaatsen elementen/mappen of verwijzingen het drempelnummer overschrijdt, wordt de verplaatsingsbewerking asynchroon uitgevoerd.

1. Klik in de globale navigatie **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open vanuit de webconsole de **[!UICONTROL Async Move Operation Job Processing Configuration.]**
1. Geef in het **[!UICONTROL Threshold number of assets/references]** vak het drempelaantal elementen/mappen of verwijzingen op voor de asynchrone verwerking van verplaatsingsbewerkingen.

   ![Drempel voor verplaatsing van element](assets/async-move-threshold.png)

1. Schakel de optie E-mailmelding **** inschakelen in om e-mailmeldingen voor deze taakstatus te ontvangen. Bijvoorbeeld succes, mislukt.
1. Sla de wijzigingen op.

### Asynchrone bewerkingen voor verplaatsen van pagina&#39;s configureren {#configuring-asynchronous-page-move-operations}

Als het aantal verwijzingen naar de te verplaatsen pagina(&#39;s) de drempelwaarde overschrijdt, wordt de verplaatsingsbewerking asynchroon uitgevoerd.

1. Klik in de globale navigatie **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open vanuit de webconsole de **[!UICONTROL Async Page Move Operation Job Processing Configuration.]**
1. Geef in het **[!UICONTROL Threshold number of references]** veld het drempelaantal verwijzingen op voor asynchrone verwerking van paginaverplaatsingsbewerkingen.

   ![Drempel voor verplaatsen pagina](assets/async-page-move.png)

1. Schakel de optie E-mailmelding **** inschakelen in om e-mailmeldingen voor deze taakstatus te ontvangen. Bijvoorbeeld succes, mislukt.
1. Sla de wijzigingen op.

### Asynchrone MSM-bewerkingen configureren {#configuring-asynchronous-msm-operations}

1. Klik in de globale navigatie **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open vanuit de webconsole de **[!UICONTROL Async Page Move Operation Job Processing Configuration.]**
1. Schakel de optie E-mailmelding **** inschakelen in om e-mailmeldingen voor deze taakstatus te ontvangen. Bijvoorbeeld succes, mislukt.

   ![MSM-configuratie](assets/async-msm.png)

1. Sla de wijzigingen op.
