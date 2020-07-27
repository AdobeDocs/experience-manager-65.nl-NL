---
title: Een transactie opnemen voor aangepaste implementaties
seo-title: Een transactie opnemen voor aangepaste implementaties
description: Gebruik de API TransactionRecorder om handelingen op te nemen die niet automatisch als transacties worden beschouwd
seo-description: Gebruik de API TransactionRecorder om handelingen op te nemen die niet automatisch als transacties worden beschouwd
uuid: a22b1a0b-7553-4a17-8fb4-a3bee97b4a98
contentOwner: khsingh
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-manager
discoiquuid: 0d961630-573b-4c8e-902f-996f1d1265b6
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# Een transactie opnemen voor aangepaste implementaties {#record-a-transaction-for-custom-implementations}

Gebruik de API TransactionRecorder om handelingen op te nemen die niet automatisch als transacties worden beschouwd

U kunt een aangepaste code gebruiken om een PDF-formulier te verzenden, om een voorbeeld-URL voor de gebruikersinterface van de agent te verzenden naar eindgebruikers voor een interactieve communicatie of om een formulier te verzenden met behulp van aangepaste methoden in plaats van verzendmethoden te gebruiken die bij AEM Forms worden geleverd. Alle eerder vermelde acties en aangepaste implementaties van AEM Forms-API&#39;s worden niet als transacties beschouwd. AEM Forms verstrekt API, [TransactionRecorder](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/aem/transaction/core/ITransactionRecorder.html), om dergelijke acties als transacties te registreren.

Om een transactie te registreren, schrijf het [standaardsling servlet](https://helpx.adobe.com/experience-manager/using/custom-sling-servlets.html) en vraag servlet van een cliënt om een transactie te registreren. U kunt servlet roepen gebruikend AJAX of een andere standaardmethode.

## Voorbeeld van code op de server {#sample-server-sided-code}

U kunt de onderstaande voorbeeldcode gebruiken om de API TransactionRecorder uit te voeren vanuit een JAVA-klasse met behulp van een aangepaste OSGi-bundel.

```java
import com.adobe.aem.transaction.core.ITransactionRecorder;
import com.adobe.aem.transaction.core.model.TransactionRecord;
import com.adobe.aem.transaction.core.exception.TransactionException;
import com.adobe.aem.transaction.core.FormsTransactionConstants;

@Reference
private ITransactionRecorder transactionRecorder;

doPost (SlingHttpServletRequest request, SlingHttpServletResponse response) {
    transactionRecorder.startContext();
    TransactionRecord txRecord = extractTxRecordFromRequest(request); //extract transaction relevant data from request
    try {
        bool success = doBillableWork();
        if (success) {
            transactionRecorder.recordTransaction(txRecord);
        }
    } catch (Exception e) {
        //exception handling
    } finally {
        transactionRecorder.endContext();
    }
}

//Here, it is assumed that txInfo is passed in Stringified json form in the ajax call (in data parameter). You can pass txInfo from client in any way that you find suitable.
private TransactionRecord extractTxRecordFromRequest(SlingHttpServletRequest request) {
    BufferedReader bufferedReader = new BufferedReader(new InputStreamReader(request.getInputStream()));
    Map<String, Object> txDataMap = new HashMap<String, Object>();
    String txData = bufferedReader.readLine();
    JSONObject txInfo= new JSONObject(txData );
    try {
        String resourceType= txInfo.getString("resourceType");
        String transactionType = txInfo.getString("transactionType");
        Integer transactionCount = (Integer)txInfo.get("transactionCount");
        //Extract all the relevant tx record attributes similarly and pass them in Transaction Record constructor as per the java doc}
        return new TransactionRecord(transactionCount, transactionType, resourceType, ..);
    } catch (JSONException e) {
        //exception handling
    } finally {
        bufferedReader.close();
    }
}
```

## Voorbeeld van code aan clientzijde {#sample-client-side-code}

U kunt de onderstaande voorbeeldcode gebruiken om de servlet met de `TransactionRecorder`API aan te roepen.

```javascript
$.ajax({
   type: 'POST',
   url: url, //servlet url
   contentType: 'application/json; UTF-8',
   data: JSON.stringify({transactionCount : 1,
                        transactionType: "SUBMIT",
                        resourceType: "FORM",
                        resourceSubType: "ADAPTIVE-FORM"}),
   success: successHandler,
   error: faultHandler
})
```

## Verwante artikelen {#related-articles}

* [Overzicht van transactierapporten](/help/forms/using/transaction-reports-overview.md)
* [Transactierapporten weergeven en begrijpen](/help/forms/using/viewing-and-understanding-transaction-reports.md)
* [Transactierapporten Billable API&#39;s](/help/forms/using/transaction-reports-billable-apis.md)

