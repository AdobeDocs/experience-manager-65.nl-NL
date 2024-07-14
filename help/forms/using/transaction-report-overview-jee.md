---
title: Transactierapporten Overzicht voor AEM Forms op JEE
description: Houd een telling van alle voorgelegde vormen, teruggegeven, documenten die in één formaat aan een andere worden omgezet, en meer.
feature: Transaction Reports
exl-id: 77e95631-6b0d-406e-a1b8-78f8d9cceb63
role: Admin, User, Developer
solution: "Experience Manager, Experience Manager Forms"
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '529'
ht-degree: 0%

---

# Transactierapporten voor AEM Forms inschakelen en weergeven op JEE {#transaction-reports-overview}

<!--Transaction reports in AEM Forms on JEE let you keep a count of all transactions taken place on your AEM Forms deployment. The objective is to provide information about product usage and helps business stakeholders understand their digital processing volumes. Examples of a transaction include:

* Submission of a document
* Rendition of a document
* Conversion of a document from one file format to another 

For more information on what is considered a transaction, see [Billable APIs](../../forms/using/transaction-reports-billable-apis-jee.md). Transaction log helps you to gain information about the number of documents submitted, rendered, and converted.-->

## Transactierapporteren inschakelen {#enable-transaction-reporting}

Standaard is het opnemen van transacties uitgeschakeld. Voer de volgende stappen uit om transactierapportage in te schakelen:

1. Navigeer bijvoorbeeld naar de `/adminui` op uw AEM Forms op JEE `http://10.14.18.10:8080/adminui` .
1. Login als **Beheerder**.
1. Ga naar **Montages** > **de Montages van het Systeem van de Kern** > **Configuraties**.
1. Klik checkbox aan **om transactie toe te laten die** rapporteert en **sparen** de montages.

   ![ steekproef-transactie-rapport-jee ](assets/enable-transaction-jee.png)

1. Start de server opnieuw.
1. Naast de wijzigingen op de server moet u op de client het `adobe-livecycle-client.jar` -bestand in uw project bijwerken als u hetzelfde gebruikt.

<!--
* You can [enable transaction recording](../../forms/using/viewing-and-understanding-transaction-reports.md#setting-up-transaction-reports) from AEM Web Console. view transaction reports on author, processing, or publish instances. View transaction reports on author or processing instances for an aggregated sum of all transactions. View transaction reports on the publish instances for a count of all transactions that take place only on that publish instance from where the report is run.
-->

<!--Do not author content (Create adaptive forms, interactive communication, themes, and other authoring activities) and process documents (Use workflows, document services, and other processing activities) on the same AEM instance. Keep the transaction recording disabled for AEM Forms servers used to author content. Keep the transaction recording enabled for AEM Forms servers used to process documents.-->

## Transactierapport weergeven {#view-transaction-report}

Wanneer u transactie het melden toelaat, wordt de informatie over de transactietellingen toegankelijk door het [ transactierapport via dashboard ](#transaction-report-dashboard) en een gedetailleerd [ transactierapport via logboekdossier ](#transaction-report-logfile). Beide worden hieronder uitgelegd:

### Transactierapport via dashboard {#transaction-report-dashboard}

Transactierapport via het dashboard geeft het totale aantal transacties voor elk type transactie. U krijgt bijvoorbeeld de informatie over het totale aantal formulieren dat wordt gegenereerd, geconverteerd en verzonden, zoals in de afbeelding wordt getoond. Het transactierapport ophalen:

1. Navigeer naar de `/adminui` op uw AEM Forms op JEE, bijvoorbeeld: `http://10.13.15.08:8080/adminui` .
1. Login als **Beheerder**.
1. Klik op Health Monitor.
1. Navigeer aan **Reporter van de Transactie** lusje, klik **Totale Transacties** berekent, nu ziet u dat een cirkeldiagram het aantal PDF forms - voorgelegd, teruggegeven, of omgezet vertegenwoordigt.

![ steekproef-transactie-rapport-jee ](assets/transaction-piechart.png)


### Transactierapport via logbestand {#transaction-report-logfile}

Transactierapport via logbestand bevat gedetailleerde informatie over elke transactie. Om tot transactielogboeken toegang te hebben, volg de contextweg met betrekking tot het serveropstarten. Transacties worden standaard vastgelegd in een afzonderlijk logbestand `transaction_log.log` . Het **dossierweg** is met betrekking tot de context van het serverbegin. Het standaardpad voor verschillende servers wordt hieronder weergegeven:

```
For Jboss Turnkey:
"<AEM_Forms_Installation>/jboss/bin/transaction_log.log"

For IBM Websphere: 
"<IBM_WAS_Profile_path>/transaction_log.log"

For Oracle Weblogic:
"<Weblogic_Domain_path>/transaction_log.log"

For Jboss Cluster:
"<Jboss home>/transaction_log.log"
```

Voorbeeld van een voorbeeldtransactierecord:
`[2024-02-28 06:11:27] [INFO] TransactionRecord{service='GeneratePDFService', operation='HtmlFileToPDF', internalService='GeneratePDFService', internalOperation='HtmlFileToPDF', transactionOperationType='CONVERT', transactionCount=1, elapsedTime=1906, transactionDate=Wed Feb 28 06:11:25 UTC 2024}`

#### Transactierecord {#transaction-record-structure-jee}

De structuur van het transactielogboek bepaalt hoe elke transactie door zijn diverse parameters, zoals de dienst, verrichting, transactietype, en anderen wordt geregistreerd. Elke methode wordt hieronder in detail beschreven. De structuur van het transactiebestand is als volgt:

```
TransactionRecord
{
    service='...', 
    operation='...', 
    internalService='...', 
    internalOperation='...', 
    transactionOperationType='...', 
    transactionCount=..., 
    elapsedTime=..., 
    transactionDate=...
}
```

* **de dienst**: Naam van de dienst.
* **verrichting**: De naam van de verrichting.
* **internalService**: Naam van de vraag als er een interne vraag, anders zelfde als de de dienstnaam is.
* **internalOperation**: De naam van de vraag binnen is daar een interne vraag, anders zelfde als de verrichtingsnaam.
* **transactionOperationType**: Type van transactie (voorleggen, teruggeeft, zet) om.
* **transactionCount**: Totale telling van transactie.
* **elapsedTime**: Tijd tussen de vraaginitiatie en ontvangen reactie.
* **transactionDate**: Tijdstempel die op wijst toen de dienst werd aangehaald.

**het transactielogboek van de Steekproef**:

```
[2024-02-14 14:23:25] [INFO] TransactionRecord
{
    service='BarcodedFormsService', 
    operation='decode', 
    internalService='BarcodedFormsService', 
    internalOperation='decode', 
    transactionOperationType='CONVERT', 
    transactionCount=1, 
    elapsedTime=47405, 
    transactionDate=Wed Feb 14 14:22:37 UTC 2024
}
```

## Transactiegerelateerde registratiefrequentie {#transaction-recording-frequency}

<!--Transaction persistence involves updating the total transaction count for SUBMIT, CONVERT, and RENDER operations on the server periodically: -->

De frequentie van opnametransacties wordt bepaald door de updatebewerkingen op de server voor elk formulier dat met succes is verzonden, gerenderd of geconverteerd.

* In **dashboard**, wordt de transactietelling periodiek bijgewerkt, gebrek geplaatst aan 1 minuut. U kunt de frequentie bijwerken door de eigenschap system in te stellen op `"com.adobe.idp.dsc.transaction.recordFrequency"` . In AEM Forms for JEE op JBoss® voegt u bijvoorbeeld `-Dcom.adobe.idp.dsc.transaction.recordFrequency=5` in `JAVA_OPTS` toe om de updatefrequentie in te stellen op 5 minuten.

* In **transactielogboeken**, komt de update voor elke transactie onmiddellijk voor wanneer een vorm met succes wordt voorgelegd, teruggegeven, of omgezet.

<!-- A transaction remains in the buffer for a specified period (Flush Buffer time + Reverse replication time). By default, it takes approximately 90 seconds for the transaction count to reflect in the transaction report.

Actions like submitting a PDF Form, using Agent UI to preview an interactive communication, or using non-standard form submission methods are not accounted as transactions. AEM Forms provides an API to record such transactions. Call the API from your custom implementations to record a transaction.

## Supported Topology {#supported-topology}

Transaction reports are available only on AEM Forms on OSGi environment. It supports author-publish, author-processing-publish, and only processing topologies. For example, topologies, see [Architecture and deployment topologies for AEM Forms](../../forms/using/transaction-reports-overview.md).

The transaction count is reverse replicated from publish instances to author or processing instances. An indicative author-publish topology is displayed below:

![simple-author-publish-topology](assets/simple-author-publish-topology.png)

>[!NOTE]
>
>AEM Forms transaction reports does not support topologies that contain only publish instances.

### Guidelines for using transaction reports {#guidelines-for-using-transaction-reports}

* Disable transaction reports on all author instances as reports on author instances includes transactions registered during authoring activities.
* Enable the **Show transactions from publish only** option on the author instance to view cumulative transactions from all publish instances. You can also view transaction reports on each publish instance for actual transactions on that particular publish instance only.
* Do not use author instances to run workflows and process documents.
* Before using transaction reporting, if you are have a toplogy with publish servers, ensure that the reverse replication is enabled for all the publish instances.
* Transaction data is reverse-replicated from a publish instance to only corresponding author or processing instance. The author or processing instance cannot further replicate data to another instance. For example, if you have author-processing-publish topology, aggregated transaction data is replicated only to the processing instance.-->

## Verwante artikelen {#related-articles}

* [Lijst met factureerbare API&#39;s voor AEM Forms op JEE](../../forms/using/transaction-reports-billable-apis-jee.md)
* [Een transactie voor aangepaste component-API&#39;s voor AEM Forms opnemen in JEE](/help/forms/using/record-transaction-custom-component-jee.md)
