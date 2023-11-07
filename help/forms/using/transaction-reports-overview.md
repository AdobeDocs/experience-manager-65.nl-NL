---
title: Overzicht van transactierapporten
seo-title: Transaction Reports Overview
description: Houd een telling van alle voorgelegde vormen, interactieve mededeling teruggegeven, Documenten die in één formaat aan een andere worden omgezet, en meer
seo-description: Keep a count of all the forms submitted, interactive communication rendered, Documents converted to one format to another, and more
uuid: 2c3dc1f3-5bbf-4aab-aa84-7aef5aabadf6
topic-tags: forms-manager
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: b2c09e6b-a1d8-4b30-af2c-988442a3a986
docset: aem65
exl-id: bb812614-f4d8-4f57-bea2-8f7d31457039
source-git-commit: 49688c1e64038ff5fde617e52e1c14878e3191e5
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Overzicht van transactierapporten{#transaction-reports-overview}

## Inleiding {#introduction}

Met transactierapporten in AEM Forms kunt u een telling bijhouden van alle transacties die sinds een opgegeven datum op uw AEM Forms-implementatie zijn uitgevoerd. Het doel is informatie te verstrekken over productgebruik en belanghebbenden in het bedrijfsleven te helpen hun digitale verwerkingsvolumes te begrijpen. Voorbeelden van een transactie zijn:

* Indiening van een adaptief formulier, een HTML5-formulier of een formulierset
* Afdruk of webversie van interactieve communicatie
* Een document omzetten van de ene bestandsindeling naar de andere

Voor meer informatie over wat als een transactie wordt beschouwd, zie [Aanpasbare API&#39;s](../../forms/using/transaction-reports-billable-apis.md).

Transactieopname is standaard uitgeschakeld. U kunt [transactieregistratie inschakelen](../../forms/using/viewing-and-understanding-transaction-reports.md#setting-up-transaction-reports) van AEM webconsole. U kunt transactierapporten weergeven over auteur-, verwerkings- of publicatieinstanties. Transactierapporten weergeven over auteur- of verwerkingsinstanties voor een geaggregeerde som van alle transacties. De transactierapporten van de mening over publiceer instanties voor een telling van alle transacties die slechts op dat publicatiegeval plaatsvinden van waar het rapport in werking wordt gesteld.

Ontwerp geen inhoud (maak adaptieve formulieren, interactieve communicatie, thema&#39;s en andere ontwerpactiviteiten) en verwerkt geen documenten (gebruik workflows, documentservices en andere verwerkingsactiviteiten) op hetzelfde AEM. Houd de transactieopname uitgeschakeld voor AEM Forms-servers die worden gebruikt om inhoud te schrijven. Laat de transactieopname ingeschakeld voor AEM Forms-servers die worden gebruikt om documenten te verwerken.

![sample-transaction-report-schrijver-1](assets/sample-transaction-report-author-1.png)

Een transactie blijft in de buffer voor een gespecificeerde periode (de tijd van de Buffer van de Duw + omgekeerde replicatietijd). Door gebrek, vergt het ongeveer 90 seconden voor de transactietelling om in het transactierapport te weerspiegelen.

Handelingen zoals het verzenden van een PDF-formulier, het gebruik van de gebruikersinterface van de om een voorvertoning van een interactieve communicatie weer te geven of het gebruik van niet-standaardmethoden voor het verzenden van formulieren worden niet als transacties beschouwd. AEM Forms biedt een API om dergelijke transacties op te nemen. Roep API van uw douaneimplementaties aan om een transactie te registreren.

## Ondersteunde topologie {#supported-topology}

Transactierapporten zijn alleen beschikbaar in AEM Forms op OSGi-omgeving. Het steunt auteur-publiceren, auteur-verwerkings-publiceer, en slechts verwerkingstopologieën. Bijvoorbeeld, topologieën, zie [Architectuur en plaatsingstopologieën voor AEM Forms](../../forms/using/transaction-reports-overview.md).

Het aantal transacties wordt omgekeerd herhaald van publicatieinstanties naar auteur- of verwerkingsinstanties. Een indicatieve auteur-publiceer topologie wordt hieronder getoond:

![simpleschrijver-publish-topologie](assets/simple-author-publish-topology.png)

>[!NOTE]
>
>AEM Forms-transactierapporten ondersteunen geen topologieën die alleen publicatieexemplaren bevatten.

### Richtlijnen voor het gebruik van transactierapporten {#guidelines-for-using-transaction-reports}

* Schakel transactierapporten uit op alle instanties van de auteur, aangezien rapporten over instanties van de auteur tijdens ontwerpactiviteiten geregistreerde transacties omvatten.
* De optie **Transacties alleen tonen uit publicatie** optie op de auteurinstantie om cumulatieve transacties van alle te bekijken publiceert instanties. U kunt ook transactierapporten op elke publicatie-instantie weergeven voor feitelijke transacties op alleen die specifieke publicatie-instantie.
* Gebruik geen auteur-instanties om workflows uit te voeren en documenten te verwerken.
* Voordat u transactierapportage gebruikt, moet u ervoor zorgen dat de omgekeerde replicatie is ingeschakeld voor alle publicatieexemplaren als u een topologie hebt met publicatieservers.
* Transactiegegevens worden omgekeerd gerepliceerd van een publicatie-instantie naar alleen de overeenkomstige auteur of verwerkingsinstantie. De auteur of verwerkingsinstantie kan gegevens niet verder repliceren naar een andere instantie. Bijvoorbeeld, als u auteur-verwerkings-publiceer topologie hebt, worden de samengevoegde transactiegegevens herhaald slechts aan de verwerkingsinstantie.

## Verwante artikelen {#related-articles}

* [Transactierapporten weergeven en begrijpen](../../forms/using/viewing-and-understanding-transaction-reports.md)
* [Transactierapporten Billable API&#39;s](../../forms/using/transaction-reports-billable-apis.md)
* [Een transactie opnemen voor aangepaste implementaties](/help/forms/using/record-transaction-custom-implementation.md)
