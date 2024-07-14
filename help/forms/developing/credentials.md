---
title: Werken met referenties
description: Importeer referenties naar AEM Forms met de Betrouwbaarheidsbeheer-API en de Java-API. Leer bovendien hoe u referenties kunt verwijderen met de API voor Betrouwbaarheidsbeheer en de Java-API.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: 1101c85a-6a90-471d-a7be-8d25765e84bf
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1077'
ht-degree: 0%

---

# Werken met referenties {#working-with-credentials}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

**Ongeveer de Credentiële Dienst**

Een referentie bevat de gegevens van uw persoonlijke sleutel die nodig zijn voor het ondertekenen of identificeren van documenten. Een certificaat is openbare zeer belangrijke informatie die u voor vertrouwen vormt. AEM Forms gebruikt certificaten en referenties voor verschillende doeleinden:

* Acrobat Reader DC-extensies gebruiken een referentie om Adobe Reader-gebruiksrechten in PDF-documenten in te schakelen. (Zie [ Toepassend de Rechten van het Gebruik op de Documenten van PDF ](/help/forms/developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).)
* De handtekeningservice krijgt toegang tot certificaten en gegevens tijdens het uitvoeren van bewerkingen, zoals het digitaal ondertekenen van PDF-documenten. (Zie [ digitaal het Ondertekenen van de Documenten van PDF ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents).)

U kunt programmatically met de dienst van de Referentie in wisselwerking staan gebruikend Java API van de Manager van het Vertrouwen. U kunt de volgende taken uitvoeren:

* [Referenties importeren met de Betrouwbaarheidsbeheer-API](credentials.md#importing-credentials-by-using-the-trust-manager-api)
* [Referenties verwijderen met de Betrouwbaarheidsbeheer-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

>[!NOTE]
>
>U kunt certificaten ook importeren en verwijderen met behulp van de beheerconsole. (Zie [ beleidshulp.](https://www.adobe.com/go/learn_aemforms_admin_63))

## Referenties importeren met de Betrouwbaarheidsbeheer-API {#importing-credentials-by-using-the-trust-manager-api}

Met de Betrouwbaarheidsbeheer-API kunt u via programmacode een referentie naar AEM Forms importeren. U kunt bijvoorbeeld een referentie importeren die wordt gebruikt om een PDF-document te ondertekenen. (Zie [ digitaal het Ondertekenen van de Documenten van PDF ](/help/forms/developing/digitally-signing-certifying-documents.md#digitally-signing-pdf-documents)).

Wanneer u een referentie importeert, geeft u een alias voor de referentie op. De alias wordt gebruikt om een Forms-bewerking uit te voeren waarvoor een referentie vereist is. Zodra ingevoerd, kan een referentie in beleidsconsole worden bekeken, zoals aangetoond in de volgende illustratie. Bericht dat alias voor de referentie *Veilig* is.

![ ww_ww_truststore ](assets/ww_ww_truststore.png)

>[!NOTE]
>
>U kunt met webservices geen referentie naar AEM Forms importeren.

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een referentie te importeren in AEM Forms:

1. Inclusief projectbestanden.
1. Creeer een cliënt van de credentiedienst.
1. Verwijs naar de referentie.
1. Voer de importbewerking uit.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-truststore-client.jar
* adobe-utilities.jar (Vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de plaats van deze JAR dossiers, zie [ Inclusief de bibliotheekdossiers van AEM Forms Java ](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een credentiedienstcliënt**

Voordat u via programmacode een referentie naar AEM Forms kunt importeren, maakt u een client voor de referentieservice. Voor informatie, zie [ Plaatsende verbindingseigenschappen ](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**Verwijzing de referentie**

Verwijs naar een referentie die u in AEM Forms wilt importeren. De snelle start die aan deze sectie is gekoppeld, verwijst naar een P12-bestand in het bestandssysteem.

**voer de invoerverrichting** uit

Importeer de referentie naar AEM Forms nadat u naar de referentie hebt verwezen. Als de referentie niet correct is geïmporteerd, wordt een uitzondering gegenereerd. Wanneer u een referentie importeert, geeft u een alias voor de referentie op.

**zie ook**

[Referenties importeren met de Java API](credentials.md#import-credentials-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Referentieservice-API: snel aan de slag](/help/forms/developing/credential-service-java-api-quick.md#credential-service-java-api-quick-start-soap)

[Referenties verwijderen met de Betrouwbaarheidsbeheer-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

### Referenties importeren met de Java API {#import-credentials-using-the-java-api}

Een referentie importeren in AEM Forms met de Betrouwbaarheidsbeheer-API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-truststore-client.jar, op in het klassenpad van uw Java-project.

1. Een crediteurenserviceclient maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `CredentialServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. Referentie van de referentie

   * Maak een `java.io.FileInputStream` -object met behulp van de constructor. Geef een tekenreekswaarde door die de locatie van de referentie opgeeft.
   * Maak een `com.adobe.idp.Document` -object dat de referentie opslaat met de `com.adobe.idp.Document` -constructor. Geef het object `java.io.FileInputStream` dat de referentie bevat, door aan de constructor.

1. De importbewerking uitvoeren

   * Maak een array met tekenreeksen die één element bevat. Wijs de waarde `truststore.usage.type.sign` toe aan het element.
   * Roep de methode `importCredential` van het object `CredentialServiceClient` aan en geef de volgende waarden door:

      * Een tekenreekswaarde die de alias voor de referentie opgeeft.
      * De `com.adobe.idp.Document` -instantie die de referentie opslaat.
      * Een tekenreekswaarde die het wachtwoord opgeeft dat aan de referentie is gekoppeld.
      * De tekenreeks-array die de gebruikswaarde bevat. U kunt bijvoorbeeld deze waarde opgeven `truststore.usage.type.sign` . Geef `truststore.usage.type.lcre` op als u een extensiereferentie voor Readers wilt importeren.

**zie ook**

[Referenties importeren met de Betrouwbaarheidsbeheer-API](credentials.md#importing-credentials-by-using-the-trust-manager-api)

[Snel starten (SOAP modus): referenties importeren met de Java API](/help/forms/developing/credential-service-java-api-quick.md#quick-start-soap-mode-importing-credentials-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Referenties verwijderen met de Betrouwbaarheidsbeheer-API {#deleting-credentials-by-using-the-trust-manager-api}

U kunt een referentie programmatically schrappen door de Manager API van het Vertrouwen te gebruiken. Wanneer u een referentie verwijdert, geeft u een alias op die overeenkomt met de referentie. Als deze eenmaal is verwijderd, kan een referentie niet worden gebruikt om een bewerking uit te voeren.

>[!NOTE]
>
>U kunt met webservices geen referentie naar AEM Forms verwijderen.

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een referentie te verwijderen:

1. Inclusief projectbestanden.
1. Creeer een cliënt van de credentiedienst.
1. Voer de verwijderbewerking uit.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-truststore-client.jar
* adobe-utilities.jar (Vereist als AEM Forms wordt geïmplementeerd op JBoss)
* jbossall-client.jar (vereist als AEM Forms wordt geïmplementeerd op JBoss)

Voor informatie over de plaats van deze JAR dossiers, zie [ Inclusief de bibliotheekdossiers van AEM Forms Java ](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**creeer een credentiedienstcliënt**

Alvorens u een referentie programmatically kunt schrappen, creeer een de dienstcliënt van de Integratie van Gegevens. Wanneer u een serviceclient maakt, definieert u verbindingsinstellingen die vereist zijn om een service aan te roepen. Voor informatie, zie [ Plaatsende verbindingseigenschappen ](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

**voer de schrappingsverrichting** uit

Als u een referentie wilt verwijderen, geeft u de alias op die overeenkomt met de referentie. Als u een alias opgeeft die niet bestaat, wordt een uitzondering gegenereerd.

**zie ook**

[Referenties importeren met de Java API](credentials.md#import-credentials-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Referenties importeren met de Java API](credentials.md#import-credentials-using-the-java-api)

### Referenties verwijderen met de Java API {#deleting-credentials-using-the-java-api}

Een referentie uit AEM Forms verwijderen met de Betrouwbaarheidsbeheer-API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-truststore-client.jar, op in het klassenpad van uw Java-project.

1. Een crediteurenserviceclient maken

   * Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat.
   * Maak een `CredentialServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven.

1. De verwijderbewerking uitvoeren

   Roep de methode `deleteCredential` van het object `CredentialServiceClient` aan en geef een tekenreekswaarde door die de aliaswaarde opgeeft.

**zie ook**

[Referenties verwijderen met de Betrouwbaarheidsbeheer-API](credentials.md#deleting-credentials-by-using-the-trust-manager-api)

[Snel starten (SOAP modus): referenties verwijderen met de Java API](/help/forms/developing/credential-service-java-api-quick.md#quick-start-soap-mode-deleting-credentials-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
