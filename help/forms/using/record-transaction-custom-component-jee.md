---
title: Registreer een transactie voor douane component API voor AEM Forms op JEE.
description: Gebruik de TransactieRecorder API om transactie voor douanecomponent te registreren.
feature: Transaction Reports
source-git-commit: d0db00de6b767a12a9492bbbcec49a8c5d25ff27
workflow-type: tm+mt
source-wordcount: '233'
ht-degree: 0%

---

# Een transactie voor aangepaste component-API&#39;s voor AEM Forms opnemen in JEE {#record-a-transaction-for-custom-components}

Wanneer u factureerbare APIs in uw douanecomponent gebruikt, kunt u transacties rapportering voor de component toelaten. Als u transactierapportage wilt inschakelen, wijzigt u de `component.xml` bestand van de component en voeg de onderstaande tag toe in het kader van de bewerking waarvoor transactierapportage moet worden ingeschakeld.

**Tag**: `<transaction-operation-type>CONVERT</transaction-operation-type> // Supported values are SUBMIT, CONVERT, RENDER.`

| Tag voor oude bewerking | Nieuwe bewerkingstag |
| ----------- | ----------- |
| `<operation>`<br> `<.... tags`<br>`<...>`<br>`<operation>` | `<operation>`<br> `<.... tags`<br>`<...>`<br>`<transaction-operation-type>CONVERT</transaction-operation-type`<br>`<operation>` |

Als er meer dan één transactie voor een API moet worden vastgelegd, bijvoorbeeld in het geval van een batch-API waarbij het aantal transacties kan variëren afhankelijk van het aantal ingevoerde gegevens, moet u in die gevallen het aantal transacties op API-niveau afhandelen. Hieronder volgen de gegeven stappen om het gevarieerde aantal transacties te registreren:

1. Klasse importeren `"com.adobe.idp.dsc.InvocationContextStack"` in de code. De klasse maakt deel uit van de klasse `adobe-livecycle-client.jar` sdk-bestand. Het SDK-bestand is beschikbaar op `<AEM_Forms_JEE_Install>\sdk\client-libs\common`

   >[!NOTE]
   > Werk het hierboven gedeelde clientbestand in uw clientproject bij met het nieuwe bestand voor het geval dat het al is gebundeld.

1. In de API waarvoor verschillende transacties moeten worden geregistreerd:
   1. Voeg logica toe om de transactietelling in één of andere geheelvariabele op te slaan, zoals: `transaction_count`.
   1. Wanneer de bewerking is voltooid, voegt u `InvocationContextStack.recordTransactionCount(transaction_count)`.

<!--For example, you can set count for your custom component by importing class `"com.adobe.idp.dsc.InvocationContextStack"` in the code available at `adobe-livecycle-client.jar`  and determine the transaction count basis API input/result and add (In this case we add count is equal to 3):
`InvocationContextStack.recordTransactionCount(<count>).` to 
`InvocationContextStack.recordTransactionCount(3)`.-->

## Verwante artikelen

* [Transactierapport inschakelen en weergeven voor AEM Forms op JEE](/help/forms/using/transaction-report-overview-jee.md)
* [Lijst met factureerbare API&#39;s voor AEM Forms op JEE](/help/forms/using/transaction-reports-billable-apis-jee.md)


