---
title: Servicecontainer
seo-title: Servicecontainer
description: 'null'
seo-description: 'null'
uuid: 89f2fd3d-63d7-4b70-b335-47314441f3ec
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: development-tools
discoiquuid: dd9c0ec4-a195-4b78-8992-81d0efcc0a7e
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Servicecontainer {#service-container}

De diensten van Vormen AEM die in de de dienstcontainer worden gevestigd (met inbegrip van standaarddiensten zoals de dienst van de Encryptie, langlevende, en kortstondige processen) kunnen worden aangehaald gebruikend diverse leveranciers, zoals een leverancier EJB. Met een EJB-provider kunnen AEM Forms-services worden aangeroepen via RMI/IIOP. Een webserviceprovider stelt services beschikbaar als webservices (WSDL Generation) met standaarden zoals SOAP/HTTP en SOAP/JMS.

In de volgende tabel worden de verschillende manieren beschreven waarop u de services van AEM Forms programmatisch kunt aanroepen.

<table>
 <thead>
  <tr>
   <th><p>Inroeping, methode</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Externe integratie</p></td>
   <td><p>De verre integratie verstrekt de capaciteit voor Flex cliënten om de dienstverrichtingen aan te halen. (Zie AEM-formulieren <a href="/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting">aanroepen met (Verouderd voor AEM-formulieren) AEM-formulieren verwijderen</a>.)</p></td>
  </tr>
  <tr>
   <td><p>Java API</p></td>
   <td><p>Een Java API kan een AEM Forms-service oproepen. De Java API is geordend in clientbibliotheken en de Java Invocation-API. (Zie <a href="/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api">AEM-formulieren aanroepen met de Java API</a>.)</p></td>
  </tr>
  <tr>
   <td><p>Webservices</p></td>
   <td><p>AEM Forms ondersteunt webservicenormen zoals SOAP/HTTP. Een service kan worden aangeboden als een webservice, waarbij de WSDL voldoet aan de webservicenormen die zijn gedefinieerd door W3C.</p><p>De dienst kan van om het even welke Web de dienststapel, met inbegrip van het .NET Kader en Sun™ de Diensten SDK van het Web worden aangehaald. (Zie <a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services">AEM-formulieren aanroepen met behulp van webservices</a>.)</p></td>
  </tr>
  <tr>
   <td><p>REST-verzoeken</p></td>
   <td><p>AEM Forms ondersteunt REST-aanvragen. Een service kan rechtstreeks vanuit een HTML-pagina worden aangeroepen. (Zie <a href="/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests">AEM-formulieren aanroepen met behulp van REST-verzoeken</a>.)</p></td>
  </tr>
 </tbody>
</table>

De volgende illustratie biedt een visuele weergave van de verschillende manieren waarop AEM Forms-services via programmacode kunnen worden aangeroepen.

>[!NOTE]
>
>Naast het gebruik van de AEM Forms SDK om cliënttoepassingen tot stand te brengen die de diensten van de Vormen van AEM kunnen aanhalen, kunt u componenten ook tot stand brengen die aan de de dienstcontainer kunnen worden opgesteld. U kunt bijvoorbeeld een bankcomponent maken die aangepaste gegevenstypen bevat die in processen kunnen worden gebruikt. Met andere woorden, u kunt een gegevenstype maken, zoals `com.adobe.idp.BankAccount`. U kunt vervolgens `com.adobe.idp.BankAccount` instanties maken in uw clienttoepassingen.

De servicecontainer biedt de volgende functionaliteit:

* Hiermee kunnen services van AEM Forms worden aangeroepen met verschillende methoden. U kunt de dienst vormen door eindpunten te plaatsen zodat het kan worden aangehaald gebruikend alle methodes: Verwijderen, de Java API, webservices en REST. (Zie [Programmatiatically het Leiden Eindpunten](/help/forms/developing/programmatically-endpoints.md#programmatically-managing-endpoints).)
* Converteert een bericht naar een genormaliseerde indeling die een aanroepingsverzoek wordt genoemd. Een aanroepingsverzoek wordt verzonden van een cliënttoepassing (of een andere dienst) naar de dienst die in de de dienstcontainer wordt gevestigd. Een aanroepingsverzoek bevat informatie zoals de naam van de dienst om aan te halen en gegevenswaarden die worden vereist om de verrichting uit te voeren. Vele diensten vereisen een document om een verrichting uit te voeren. Daarom bevat een aanroepingsverzoek gewoonlijk een document, dat PDF-gegevens, XDP-gegevens, XML-gegevens enzovoort kan zijn.
* Routes oproepend verzoeken aan de aangewezen diensten (de naam van de dienst om te roepen maakt deel uit van het oproepingsverzoek).
* Voert taken zoals het bepalen uit of de bezoeker toestemming heeft om de gespecificeerde de dienstverrichting aan te halen. De aanroepingsaanvraag moet een geldige gebruikersnaam en wachtwoord voor AEM-formulieren bevatten.

   Er zijn verschillende manieren om een aanroepingsverzoek naar de dienst te verzenden. Er zijn ook verschillende manieren om de vereiste invoerwaarden naar de service te verzenden. Stel dat u de Java API gebruikt om een service aan te roepen waarvoor een PDF-document nodig is. De bijbehorende Java-methode bevat een parameter die een PDF-document accepteert. In deze situatie is het gegevenstype van de parameter `com.adobe.idp.Document`. (Zie Gegevens [doorgeven aan AEM Forms-services met behulp van de Java API](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api).)

   Als u een service aanroept met gecontroleerde mappen, wordt een aanroepingsverzoek verzonden wanneer u een bestand in een geconfigureerde controlemap plaatst. Als u de dienst gebruikend e-mail aanhaalt, dan wordt een aanroepingsverzoek verzonden naar de dienst wanneer een e-mailbericht in gevormd inbox aankomt.

   De de dienstcontainer verzendt een aanroepingsreactie terug zodra de verrichting wordt uitgevoerd. Een aanroepingsreactie bevat informatie zoals de bewerkingsresultaten. Als de bewerking bijvoorbeeld een PDF-document wijzigt, bevat het oproepingsantwoord het gewijzigde PDF-document. Als de bewerking is mislukt, bevat de aanroepingsreactie een foutbericht.

   Een aanroepingsreactie kan op dezelfde manier worden opgehaald als een aanroepingsverzoek. Als de oproepaanvraag wordt verzonden met de Java API, kan een oproepingsreactie worden opgehaald met de Java API. Stel bijvoorbeeld dat een bewerking een PDF-document wijzigt. U kunt het gewijzigde PDF-document ophalen door de geretourneerde waarde op te halen van de Java-methode die de service heeft aangeroepen.

   Wanneer een langdurig proces wordt aangeroepen, bevat een aanroepingsreactie een waarde voor de id die aan de aanroepingsaanvraag is gekoppeld. Met deze id-waarde kunt u de status van het proces op een later tijdstip controleren. Neem bijvoorbeeld de service MortgaugeLoan voor lange tijd. Met de id-waarde kunt u controleren of het proces is voltooid. (Zie [Langdurige processen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)aanroepen vanuit menselijk perspectief.)

   In het volgende diagram ziet u een clienttoepassing (die de Java API gebruikt) die een service aanroept.

   Wanneer een cliënttoepassing de dienst aanhaalt, komen drie gebeurtenissen voor:

   1. Een cliënttoepassing verzendt een aanroepingsverzoek naar de dienst.
   1. De service voert de bewerking uit die in de aanroepingsaanvraag is opgegeven.
   1. De servicecontainer retourneert een aanroepingsreactie op de clienttoepassing.

**Zie ook**

[AEM-formulierprocessen begrijpen](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes)

[AEM-formulieren aanroepen met AEM-formulieren (afgekeurd voor AEM-formulieren) Verwijderen](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[AEM-formulieren aanroepen met de Java API](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[AEM-formulieren aanroepen met webservices](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services)

[Het aanhalen van mens-Centric langlevende Processen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[AEM-formulieren aanroepen met behulp van REST-verzoeken](/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests)
