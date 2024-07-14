---
title: Servicecontainer
description: AEM Forms-services in de servicecontainer
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding, development-tools
role: Developer
exl-id: 6abf2401-5a87-4f72-9028-74580df5b9de
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 939a2efa64c853928a9082aa30d7338e98deb695
workflow-type: tm+mt
source-wordcount: '923'
ht-degree: 0%

---

# Servicecontainer {#service-container}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

De diensten van AEM Forms in de de dienstcontainer (met inbegrip van standaarddiensten zoals de dienst van de Encryptie, langlevende, en kortstondige processen) kunnen worden aangehaald gebruikend diverse leveranciers, zoals een leverancier EJB. Met een EJB-provider kunnen AEM Forms-services worden aangeroepen via RMI/IIOP. Een webserviceprovider stelt services beschikbaar als webservices (WSDL Generation) met standaarden zoals SOAP/HTTP en SOAP/JMS.

De volgende lijst beschrijft de verschillende manieren waarin u de diensten van AEM Forms programmatically kunt aanhalen.

<table>
 <thead>
  <tr>
   <th><p>Inroepmethode</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Externe integratie</p></td>
   <td><p>Externe integratie biedt Flex-clients de mogelijkheid om servicebewerkingen aan te roepen. (Zie <a href="/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting"> het Aanhalen van AEM Forms die (voor AEM vormen) AEM Forms verwijdert </a> gebruikt.)</p></td>
  </tr>
  <tr>
   <td><p>Java API</p></td>
   <td><p>Een Java API kan een AEM Forms-service oproepen. De Java API is geordend in clientbibliotheken en de Java Invocation-API. (Zie <a href="/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api"> het Aanhalen van AEM Forms gebruikend Java API </a>.)</p></td>
  </tr>
  <tr>
   <td><p>Webservices</p></td>
   <td><p>AEM Forms ondersteunt webservicenormen zoals SOAP/HTTP. Een service kan worden aangeboden als een webservice, waarbij de WSDL voldoet aan de webservicenormen die zijn gedefinieerd door W3C.</p><p>De dienst kan van om het even welke Web de dienststapel, met inbegrip van het .NET Kader en Sun™ de Diensten SDK van het Web worden aangehaald. (Zie <a href="/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services"> het Aanhalen van AEM Forms gebruikend de Diensten van het Web </a>.)</p></td>
  </tr>
  <tr>
   <td><p>REST-verzoeken</p></td>
   <td><p>AEM Forms ondersteunt REST-aanvragen. Een dienst kan direct van een pagina van de HTML worden aangehaald. (Zie <a href="/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests"> het Aanhalen van AEM Forms die REST Verzoeken </a> gebruikt.)</p></td>
  </tr>
 </tbody>
</table>

De volgende illustratie biedt een visuele weergave van de verschillende manieren waarop AEM Forms-services via programmacode kunnen worden aangeroepen.

>[!NOTE]
>
>Naast het gebruiken van SDK van AEM Forms om cliënttoepassingen tot stand te brengen die de diensten van AEM Forms kunnen aanhalen, kunt u componenten ook tot stand brengen die aan de de dienstcontainer kunnen worden opgesteld. U kunt bijvoorbeeld een bankcomponent maken die aangepaste gegevenstypen bevat die in processen kunnen worden gebruikt. U kunt dus een gegevenstype maken, zoals `com.adobe.idp.BankAccount` . Vervolgens kunt u `com.adobe.idp.BankAccount` -instanties maken in uw clienttoepassingen.

De servicecontainer biedt de volgende functionaliteit:

* Hiermee kunnen AEM Forms-services met verschillende methoden worden aangeroepen. U kunt de dienst vormen door eindpunten te plaatsen zodat het kan worden aangehaald gebruikend alle methodes: Verwijderen, Java API, Webdiensten, en REST. (Zie [ programmatically het Leiden Eindpunten ](/help/forms/developing/programmatically-endpoints.md#programmatically-managing-endpoints).)
* Converteert een bericht naar een genormaliseerde indeling die een aanroepingsverzoek wordt genoemd. Een aanroepingsverzoek wordt verzonden van een cliënttoepassing (of een andere dienst) naar de dienst in de de dienstcontainer. Een aanroepingsverzoek bevat informatie zoals de naam van de dienst om aan te halen en gegevenswaarden die worden vereist om de verrichting uit te voeren. Vele diensten vereisen een document om een verrichting uit te voeren. Daarom bevat een aanroepingsverzoek gewoonlijk een document, dat PDF-gegevens, XDP-gegevens, XML-gegevens enzovoort kan zijn.
* Routes oproepend verzoeken aan de aangewezen diensten (de naam van de dienst om te roepen maakt deel uit van het oproepingsverzoek).
* Voert taken zoals het bepalen uit of de bezoeker toestemming heeft om de gespecificeerde de dienstverrichting aan te halen. De aanroepingsaanvraag moet een geldige gebruikersnaam en wachtwoord voor AEM formulieren bevatten.

  Er zijn verschillende manieren om een aanroepingsverzoek naar de dienst te verzenden. Er zijn ook verschillende manieren om de vereiste invoerwaarden naar de service te verzenden. Stel dat u de Java API gebruikt om een service aan te roepen waarvoor een PDF-document nodig is. De overeenkomstige Java-methode bevat een parameter die een PDF-document accepteert. In deze situatie is het gegevenstype van de parameter `com.adobe.idp.Document` . (Zie [ het overgaan van gegevens tot de diensten van AEM Forms gebruikend Java API ](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api).)

  Als u een service aanroept met gecontroleerde mappen, wordt een aanroepingsverzoek verzonden wanneer u een bestand in een geconfigureerde controlemap plaatst. Als u de dienst gebruikend e-mail aanhaalt, dan wordt een aanroepingsverzoek verzonden naar de dienst wanneer een e-mailbericht in gevormd inbox aankomt.

  De de dienstcontainer verzendt een aanroepingsreactie terug zodra de verrichting wordt uitgevoerd. Een aanroepingsreactie bevat informatie zoals de bewerkingsresultaten. Als de bewerking bijvoorbeeld een PDF-document wijzigt, bevat de aanroepingsreactie het gewijzigde PDF-document. Als de bewerking is mislukt, bevat de aanroepingsreactie een foutbericht.

  Een aanroepingsreactie kan op dezelfde manier worden opgehaald als een aanroepingsverzoek. Als de oproepaanvraag wordt verzonden met de Java API, kan een oproepingsreactie worden opgehaald met de Java API. Stel bijvoorbeeld dat een bewerking een PDF-document wijzigt. U kunt het gewijzigde document van de PDF terugwinnen door de terugkeerwaarde van de methode van Java te krijgen die de dienst aanhaalde.

  Wanneer een langdurig proces wordt aangeroepen, bevat een aanroepingsreactie een waarde voor de id die aan de aanroepingsaanvraag is gekoppeld. Met deze id-waarde kunt u de status van het proces op een later tijdstip controleren. Neem bijvoorbeeld de service MortgaugeLoan voor lange tijd. Met de id-waarde kunt u controleren of het proces is voltooid. (Zie [ het aanhalen van mens-Centric langlevende Processen ](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

  In het volgende diagram ziet u een clienttoepassing (die de Java API gebruikt) die een service aanroept.

  Wanneer een cliënttoepassing de dienst aanhaalt, komen drie gebeurtenissen voor:

   1. Een cliënttoepassing verzendt een aanroepingsverzoek naar de dienst.
   1. De service voert de bewerking uit die in de aanroepingsaanvraag is opgegeven.
   1. De servicecontainer retourneert een aanroepingsreactie op de clienttoepassing.

**zie ook**

[AEM Forms-processen begrijpen](/help/forms/developing/aem-forms-processes.md#understanding-aem-forms-processes)

[AEM Forms aanroepen met (Vervangen voor AEM formulieren) AEM Forms Remoting](/help/forms/developing/invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[AEM Forms aanroepen met de Java API](/help/forms/developing/invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[AEM Forms aanroepen met webservices](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-web-services)

[Het aanhalen van mens-Centric langlevende Processen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[AEM Forms aanroepen met REST-verzoeken](/help/forms/developing/invoking-aem-forms-using-rest.md#invoking-aem-forms-using-rest-requests)
