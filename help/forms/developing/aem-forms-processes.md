---
title: AEM Forms-processen begrijpen
seo-title: AEM Forms-processen begrijpen
description: AEM Forms-processen begrijpen
uuid: 7cbebe7d-f222-42fa-8eb6-d2443458a791
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: development-tools, coding
discoiquuid: ac9fe461-63e7-442b-bd1c-eb9576ef55aa
translation-type: tm+mt
source-git-commit: a873cf3e7efd3bc9cd4744bf09078d9040efcdda
workflow-type: tm+mt
source-wordcount: '793'
ht-degree: 0%

---


# AEM Forms-processen begrijpen {#understanding-aem-forms-processes}

Een veel voorkomend geval is dat een set AEM Forms-services op één document werkt. U kunt een verzoek naar de de dienstcontainer verzenden door een proces te creëren gebruikend Workbench. Een proces vertegenwoordigt een bedrijfsproces dat u automatiseert. Zie [Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63)gebruiken voor informatie over het maken van processen.

Zodra een proces wordt geactiveerd, wordt het de dienst en kan als andere diensten worden aangehaald. Één verschil tussen de standaarddienst, zoals de dienst van de Encryptie en de dienst die uit een proces voortkwam, is dat laatstgenoemde één verrichting heeft die vele acties uitvoert. In tegenstelling, heeft een standaarddienst vele verrichtingen. Elke bewerking voert doorgaans één actie uit, zoals het toepassen van een beleid op een document of het versleutelen van een document.

Processen kunnen van korte duur of van lange duur zijn. Een kortstondig proces is een verrichting die synchroon en op de zelfde uitvoeringsdraad wordt uitgevoerd waarvan het werd aangehaald. Korte-levende verrichtingen zijn vergelijkbaar met het standaardgedrag dat in de meeste programmeertalen wordt gevonden, waar een cliënttoepassing een methode roept en op een terugkeerwaarde wacht.

Er zijn echter situaties waarin een proces niet synchroon kan worden voltooid vanwege factoren zoals:

* Een proces kan veel tijd in beslag nemen.
* Een proces kan organisatorische grenzen overspannen.
* Een proces heeft externe input nodig om het te voltooien. Neem bijvoorbeeld een situatie waarin een formulier wordt verzonden naar een manager die buiten het kantoor is. In dit geval is het proces niet volledig totdat de manager het formulier retourneert en invult.

   Deze typen processen worden langlevende processen genoemd. Een proces van lange duur wordt asynchroon uitgevoerd, toestaand voor systemen om als middelen toelaten in wisselwerking te staan en het volgen van en het toezicht op de verrichting toe te staan. Wanneer een proces met een lange levensduur wordt aangeroepen, maakt AEM Forms een waarde voor de aanroepings-id als onderdeel van een record die de status van het proces met een lange levensduur bijhoudt. De record wordt opgeslagen in de AEM Forms-database. U kunt langlevende procesverslagen zuiveren wanneer zij niet meer worden vereist.

>[!NOTE]
>
>AEM Forms maakt geen record wanneer een kortstondig proces wordt aangeroepen.

Met de waarde voor de oproepings-id kunt u de status van het langlevende proces volgen. U kunt bijvoorbeeld de waarde voor de identificatie van de procesaanroep gebruiken om bewerkingen van Process Manager uit te voeren, zoals het beëindigen van een actieve procesinstantie.

**Voorbeeld van een kortlopend proces**

De volgende illustratie is een voorbeeld van een kortstondig proces genoemd *MyApplication/EncryptDocument*.

>[!NOTE]
>
>Dit proces is niet gebaseerd op een bestaand AEM Forms-proces. Om samen met de codevoorbeelden te volgen die bespreken hoe te om dit proces aan te halen, creeer een proces genoemd `MyApplication/EncryptDocument` gebruikend Workbench. (Zie [Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63)gebruiken.)

Wanneer dit proces van korte duur wordt aangehaald, voert het de volgende acties uit:

1. Hiermee krijgt u het onbeveiligde PDF-document dat aan het proces wordt doorgegeven, als invoerwaarde.
1. Hiermee versleutelt u het PDF-document met een wachtwoord. De naam van de invoerparameter voor dit proces is `inDoc` en het gegevenstype is document.
1. Hiermee slaat u het met een wachtwoord gecodeerde PDF-document op als een PDF-bestand naar het lokale bestandssysteem. Hiermee wordt het gecodeerde PDF-document als een uitvoerwaarde geretourneerd. De naam van de uitvoerparameter voor dit proces is `outDoc` en het gegevenstype is document.

   Dit proces wordt synchroon voltooid op de zelfde uitvoeringsdraad waarvan het werd aangehaald. De naam van dit kortstondige proces is `MyApplication/EncryptDocument`en de werking ervan is `invoke`.

   >[!NOTE]
   >
   >Een kortstondig proces bestaat meestal uit meer dan drie acties. U maakt een proces met Workbench. (Zie [Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63)gebruiken.)

   *Het programmeren met AEM* formsbeschrijft de volgende manieren waarin u dit kortstondige proces programmatically kunt aanhalen:

   * [Een kortstondig proces aanroepen door een onbeveiligd document door te geven met AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting) (een Flex-toepassing gebruiken)
   * [Een kortstondig proces aanroepen met de API](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-a-short-lived-process-using-the-invocation-api) Inroeping (Java Invocation API)
   * [AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding) (voorbeeld voor webservice)
   * [AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom) (voorbeeld voor webservice)
   * [AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref) (voorbeeld voor webservice)
   * [AEM Forms aanroepen met behulp van BLOB-gegevens via HTTP](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-blob-data-over-http) (voorbeeld voor webservices)
   * [AEM Forms aanroepen met DIME](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-dime) (voorbeeld van webservice)
   * [Het MyApplication/EncryptDocument-proces aanroepen met REST](/help/forms/developing/invoking-aem-forms-using-rest.md)

**Voorbeeld van langlevend proces**

De volgende illustratie is een voorbeeld van een langdurig proces.

Dit proces wordt aangehaald wanneer een aanvrager een leningformulier indient. Het proces is niet voltooid totdat een leningfunctionaris het leningsverzoek goedkeurt of verwerpt. De naam van dit proces van lange duur is *FirstAppSolution/PreLoanProcess* en de werking ervan is `invoke_Async`. Dit proces moet asynchroon worden aangeroepen. Voor informatie over programmatically het aanhalen van dit langdurig proces, zie het [Aanhalen van mens-Centric langlevende Processen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

>[!NOTE]
>
>Dit proces kan worden gemaakt door de zelfstudie te volgen die is opgegeven in [Uw eerste AEM Forms-toepassing](https://www.adobe.com/go/learn_aemforms_firstapp_ds_63)maken.