---
title: Overzicht van transactierapporten
description: Houd een telling van alle voorgelegde vormen, interactieve mededeling teruggegeven, Documenten die in één formaat aan een andere worden omgezet, en meer
topic-tags: forms-manager
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Transaction Reports
exl-id: bb812614-f4d8-4f57-bea2-8f7d31457039
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '476'
ht-degree: 0%

---

# Transactierapporten voor AEM Forms op OSGi {#transaction-reports-overview}

<!--## Introduction {#introduction}

Transaction reports in AEM Forms let you keep a count of all transactions taken place since a specified date on your AEM Forms deployment. The objective is to provide information about product usage and help business stakeholders understand their digital processing volumes. Examples of a transaction include:

* Submission of an adaptive form, an HTML5 Form, or a form set
* Rendition of a print or a web version of an interactive communication
* Conversion of a document from one file format to another

For more information on what is considered a transaction, see [Billable APIs](../../forms/using/transaction-reports-billable-apis.md).-->

Transactieopname is standaard uitgeschakeld. U kunt [&#x200B; transactieopname &#x200B;](../../forms/using/viewing-and-understanding-transaction-reports.md#setting-up-transaction-reports) van AEM Console van het Web toelaten. U kunt transactierapporten weergeven over auteur-, verwerkings- of publicatieinstanties. Transactierapporten weergeven over auteur- of verwerkingsinstanties voor een geaggregeerde som van alle transacties. De transactierapporten van de mening over publiceer instanties voor een telling van alle transacties die slechts op dat publicatiegeval plaatsvinden van waar het rapport in werking wordt gesteld.

Ontwerp geen inhoud (maak adaptieve formulieren, interactieve communicatie, thema&#39;s en andere ontwerpactiviteiten) en verwerkt geen documenten (gebruik workflows, documentservices en andere verwerkingsactiviteiten) op hetzelfde AEM. Houd de transactieopname uitgeschakeld voor AEM Forms-servers die worden gebruikt om inhoud te schrijven. Laat de transactieopname ingeschakeld voor AEM Forms-servers die worden gebruikt om documenten te verwerken.

![&#x200B; steekproef-transactie-rapport-auteur-1 &#x200B;](assets/sample-transaction-report-author-1.png)

Een transactie blijft in de buffer voor een gespecificeerde periode (de tijd van de Buffer van de Duw + omgekeerde replicatietijd). Door gebrek, vergt het ongeveer 90 seconden voor de transactietelling om in het transactierapport te weerspiegelen.

Handelingen zoals het verzenden van een PDF-formulier, het gebruik van de gebruikersinterface van de om een voorvertoning van een interactieve communicatie weer te geven of het gebruik van niet-standaardmethoden voor het verzenden van formulieren worden niet als transacties beschouwd. AEM Forms biedt een API om dergelijke transacties op te nemen. Roep API van uw douaneimplementaties aan om een transactie te registreren.

## Ondersteunde topologie {#supported-topology}

Transactierapporten zijn alleen beschikbaar in AEM Forms op OSGi-omgeving. Het steunt auteur-publiceren, auteur-verwerkings-publiceer, en slechts verwerkingstopologieën. Bijvoorbeeld, topologieën, zie [&#x200B; Architectuur en plaatsingstopologieën voor AEM Forms &#x200B;](../../forms/using/transaction-reports-overview.md).

Het aantal transacties wordt omgekeerd herhaald van publicatieinstanties naar auteur- of verwerkingsinstanties. Een indicatieve auteur-publiceer topologie wordt hieronder getoond:

![&#x200B; eenvoudig-auteur-publish-topologie &#x200B;](assets/simple-author-publish-topology.png)

>[!NOTE]
>
>AEM Forms-transactierapporten ondersteunen geen topologieën die alleen publicatieexemplaren bevatten.

### Richtlijnen voor het gebruik van transactierapporten {#guidelines-for-using-transaction-reports}

* Schakel transactierapporten uit op alle instanties van de auteur, aangezien rapporten over instanties van de auteur tijdens ontwerpactiviteiten geregistreerde transacties omvatten.
* Laat **toe tonen transacties van publiceren slechts** optie op de auteursinstantie om cumulatieve transacties van alle te bekijken publiceert instanties. U kunt ook transactierapporten op elke publicatie-instantie weergeven voor feitelijke transacties op alleen die specifieke publicatie-instantie.
* Gebruik geen auteur-instanties om workflows uit te voeren en documenten te verwerken.
* Voordat u transactierapportage gebruikt, moet u ervoor zorgen dat de omgekeerde replicatie is ingeschakeld voor alle publicatieexemplaren als u een topologie hebt met publicatieservers.
* Transactiegegevens worden omgekeerd gerepliceerd van een publicatie-instantie naar alleen de overeenkomstige auteur of verwerkingsinstantie. De auteur of verwerkingsinstantie kan gegevens niet verder repliceren naar een andere instantie. Bijvoorbeeld, als u auteur-verwerkings-publiceer topologie hebt, worden de samengevoegde transactiegegevens herhaald slechts aan de verwerkingsinstantie.

## Verwante artikelen {#related-articles}

* [Een transactierapport voor AEM Forms bekijken en begrijpen op OSGi](../../forms/using/viewing-and-understanding-transaction-reports.md)
* [Transactierapporten Billable API&#39;s voor AEM Forms op OSGi](../../forms/using/transaction-reports-billable-apis.md)
* [Registreer een transactie voor douaneimplementaties voor AEM Forms op OSGi](/help/forms/using/record-transaction-custom-implementation.md)
