---
title: Asynchrone taken
description: Adobe Experience Manager optimaliseert prestaties door sommige resource-intensieve taken asynchroon te voltooien.
exl-id: 4af1bcfe-9f2e-44a4-8666-881f2dccc3bc
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '715'
ht-degree: 83%

---

# Asynchrone bewerkingen {#asynchronous-operations}

Om negatieve gevolgen voor de prestaties te verminderen verwerkt Adobe Experience Manager bepaalde langlopende en resource-intensieve bewerkingen asynchroon. Bij asynchrone verwerking worden meervoudige taken in wachtrijen geplaatst en serieel uitgevoerd, afhankelijk van de beschikbaarheid van systeembronnen.

Deze bewerkingen omvatten:

* Veel assets verwijderen
* Veel assets verplaatsen, of assets met veel verwijzingen verplaatsen
* Metadata van assets bulksgewijs exporteren/importeren
* Assets die boven de ingestelde drempelwaarde liggen, importeren vanaf een externe Experience Manager-implementatie
* Actieve exemplaren uitrollen

U kunt het statuut van asynchrone banen van het **[!UICONTROL Async Job Status]** dashboard bij **Globale Navigatie** bekijken > **Hulpmiddelen** > **Verrichtingen** > **Banen**.

>[!NOTE]
>
>Asynchrone taken worden standaard parallel uitgevoerd. Als *`n`* het aantal CPU-cores is, kunnen standaard *`n/2`* taken parallel worden uitgevoerd. Als u aangepaste instellingen voor de taakwachtrij wilt gebruiken, wijzigt u **[!UICONTROL Async Operation Default Queue Config]** en de **Async Operation Page Move and Rollout Config** vanaf de webconsole.
>
>Voor meer informatie raadpleegt u [wachtrijconfiguraties](https://sling.apache.org/documentation/bundles/apache-sling-eventing-and-job-handling.html#queue-configurations).

## De status van asynchrone bewerkingen controleren {#monitor-the-status-of-asynchronous-operations}

Wanneer AEM een bewerking asynchroon verwerkt, ontvangt u een bericht in uw [inbox](/help/sites-authoring/inbox.md) en via e-mail (mits ingeschakeld).

Navigeer naar de pagina **[!UICONTROL Async Job Status]** om de status van de asynchrone bewerkingen in detail weer te geven.

1. Klik in de Experience Manager-interface op **[!UICONTROL Operations]** > **[!UICONTROL Jobs]**.

1. Controleer op de pagina **[!UICONTROL Async Job Status]** de details van de bewerkingen.

   ![Status en details van asynchrone bewerkingen](assets/async-operation-status.png)

   Bekijk de waarde in de kolom **[!UICONTROL Status]** voor informatie over de voortgang van een bepaalde bewerking. Afhankelijk van de voortgang wordt een van de volgende statussen weergegeven:

   * **[!UICONTROL Active]**: De bewerking wordt verwerkt

   * **[!UICONTROL Success]**: De bewerking is voltooid

   * **[!UICONTROL Fail]** of **[!UICONTROL Error]**: De bewerking kan niet worden verwerkt

   * **[!UICONTROL Scheduled]**: De bewerking is gepland voor verwerking op een later tijdstip

1. Als u een actieve bewerking wilt stoppen, selecteert u deze in de lijst en klikt u op de werkbalk op **[!UICONTROL Stop]**.

   ![stop_icon](assets/async-stop-icon.png)

1. Als u meer details wilt weergeven, bijvoorbeeld een beschrijving en logboekbestanden, selecteert u de bewerking en klikt u op **[!UICONTROL Open]** op de werkbalk.

   ![open_icon](assets/async-open-icon.png)

   De pagina met taakdetails wordt weergegeven.

   ![job_details](assets/async-job-details.png)

1. Als u de bewerking uit de lijst wilt verwijderen, selecteert u **[!UICONTROL Delete]** op de werkbalk. Klik op **[!UICONTROL Download]** om de details naar een csv-bestand te downloaden.

   >[!NOTE]
   >
   >U kunt een taak niet verwijderen als de status **Actief** of **In wachtrij** is.

## Voltooide taken wissen {#purging-completed-jobs}

AEM voert elke dag om 01:00 een opschoontaak uit om voltooide, asynchrone taken te wissen die meer dan een dag oud zijn.

U kunt het schema wijzigen voor de opschoontaak en hoe lang details van voltooide taken bewaard blijven voordat ze worden verwijderd. U kunt ook het maximum aantal voltooide taken configureren waarvoor de details tot een gewenst tijdstip bewaard blijven.

1. Klik vanuit Algemene navigatie op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open de taak **[!UICONTROL Adobe Granite Async Jobs Purge Scheduled Job]**.
1. Geef het volgende op:
   * Het maximum aantal dagen waarna voltooide taken worden verwijderd.
   * Het maximum aantal taken waarvan data in de geschiedenis worden bewaard.
   * De cron-expressie waarmee wordt opgegeven wanneer de opschoning moet worden uitgevoerd.

   ![Configuratie voor het opschonen van asynchrone taken](assets/async-purge-job.png)

1. Sla de wijzigingen op.

## Asynchrone verwerking configureren {#configuring-asynchronous-processing}

U kunt het drempelaantal elementen, pagina&#39;s of verwijzingen voor AEM configureren om een bepaalde bewerking asynchroon te verwerken en e-mailmeldingen in en uit te schakelen wanneer de taken worden verwerkt.

### Asynchrone bewerkingen voor het verwijderen van elementen configureren {#configuring-synchronous-delete-operations}

Als het aantal te verwijderen assets of mappen de drempelwaarde overschrijdt, wordt de verwijderingsbewerking asynchroon uitgevoerd.

1. Klik vanuit Algemene navigatie op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open vanuit de webconsole de **[!UICONTROL Async Process Default Queue Configuration.]**
1. Geef in het vak **[!UICONTROL Threshold number of assets]** het drempelaantal assets/mappen op voor de asynchrone verwerking van verwijderingsbewerkingen.

   ![Drempel voor verwijdering van assets](assets/async-delete-threshold.png)

1. Schakel de optie **E-mailmeldingen inschakelen** in om e-mailmeldingen te ontvangen voor deze taakstatus. succes bijvoorbeeld, mislukt.
1. Sla de wijzigingen op.

### Asynchrone verplaatsingsbewerkingen voor middelen configureren {#configuring-asynchronous-move-operations}

Als het aantal te verplaatsen assets/mappen de drempelwaarde overschrijdt, wordt de verplaatsingsbewerking asynchroon uitgevoerd.

1. Klik vanuit Algemene navigatie op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open vanuit de webconsole de **[!UICONTROL Async Move Operation Job Processing Configuration.]**
1. Geef in het vak **[!UICONTROL Threshold number of assets/references]** het drempelaantal assets/mappen of verwijzingen op voor de asynchrone verwerkings- of verplaatsingsbewerkingen.

   ![Drempel voor verplaatsing van assets](assets/async-move-threshold.png)

1. Schakel de optie **E-mailmeldingen inschakelen** in om e-mailmeldingen te ontvangen voor deze taakstatus. succes bijvoorbeeld, mislukt.
1. Sla de wijzigingen op.

### Asynchrone MSM-bewerkingen configureren {#configuring-asynchronous-msm-operations}

1. Klik vanuit Algemene navigatie op **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.
1. Open vanuit de webconsole de **[!UICONTROL Async Page Move Operation Job Processing Configuration.]**
1. Schakel de optie **E-mailmeldingen inschakelen** in om e-mailmeldingen te ontvangen voor deze taakstatus. succes bijvoorbeeld, mislukt.

   ![MSM-configuratie](assets/async-msm.png)

1. Sla de wijzigingen op.

>[!MORELIKETHIS]
>
>* [Pagina&#39;s maken en indelen](/help/sites-authoring/managing-pages.md)
>* [ Creërend en het Synchroniseren Actieve Exemplaren ](/help/sites-administering/msm-livecopy.md)
>* [ vorm e-mail in Experience Manager ](/help/sites-administering/notification.md).
>* [ de meta-gegevens van de Activa van de Invoer ](/help/assets/metadata.md#import-metadata).
>* [ de activameta-gegevens van de Uitvoer ](/help/assets/metadata.md#export-metadata).
>* [Connected Assets gebruiken om DAM-assets te delen vanuit externe implementaties](/help/assets/use-assets-across-connected-assets-instances.md).
