---
title: Registreer een transactie voor douane component API voor AEM Forms op JEE.
description: Meer informatie over het gebruik van de API TransactionRecorder om transacties voor een aangepaste component op te nemen.
feature: Transaction Reports
exl-id: 33e1868a-2a7f-4785-8571-95651e661e21
role: Admin, User, Developer
solution: "Experience Manager, Experience Manager Forms"
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '218'
ht-degree: 0%

---

# Een transactie voor aangepaste component-API&#39;s voor AEM Forms opnemen in JEE {#record-a-transaction-for-custom-components}

Wanneer u factureerbare APIs in uw douanecomponent gebruikt, kunt u transactie het melden voor de component toelaten. Als u transactierapportage wilt inschakelen, wijzigt u het `component.xml` -bestand van de component en voegt u de onderstaande tag toe onder de bewerking waarvoor transactierapportage moet worden ingeschakeld.

**Markering**: `<transaction-operation-type>CONVERT</transaction-operation-type> // Supported values are SUBMIT, CONVERT, RENDER.`

| Tag voor oude bewerking | Nieuwe bewerkingstag |
| ----------- | ----------- |
| `<operation>`<br> `<.... tags`<br>`<...>`<br>`<operation>` | `<operation>`<br> `<.... tags`<br>`<...>`<br>`<transaction-operation-type>CONVERT</transaction-operation-type`<br>`<operation>` |

Als u meer dan één transactie voor een API moet vastleggen, zoals een batch-API waarbij het aantal transacties varieert afhankelijk van het aantal ingevoerde gegevens, verwerkt u het aantal transacties op API-niveau.

**om het gevarieerde transactietelling te registreren:**

1. Importklasse `"com.adobe.idp.dsc.InvocationContextStack"` in de code. De klasse maakt deel uit van het `adobe-livecycle-client.jar` sdk-bestand. Het SDK-bestand is beschikbaar op `<AEM_Forms_JEE_Install>\sdk\client-libs\common`

   >[!NOTE]
   > Werk het hierboven gedeelde clientbestand in uw clientproject bij met het nieuwe bestand voor het geval dat het al is gebundeld.

1. In de API waarvoor verschillende transacties moeten worden geregistreerd:
   1. Voeg logica toe zodat u de transactietelling in één of andere geheelvariabele, zoals, kunt opslaan `transaction_count`.
   1. Voeg `InvocationContextStack.recordTransactionCount(transaction_count)` toe wanneer de bewerking is voltooid.

<!--For example, you can set count for your custom component by importing class `"com.adobe.idp.dsc.InvocationContextStack"` in the code available at `adobe-livecycle-client.jar`  and determine the transaction count basis API input/result and add (In this case we add count is equal to 3):
`InvocationContextStack.recordTransactionCount(<count>).` to 
`InvocationContextStack.recordTransactionCount(3)`.-->

## Verwante artikelen

* [Transactierapporten voor AEM Forms inschakelen en weergeven op JEE](/help/forms/using/transaction-report-overview-jee.md)
* [Lijst met factureerbare API&#39;s voor AEM Forms op JEE](/help/forms/using/transaction-reports-billable-apis-jee.md)
