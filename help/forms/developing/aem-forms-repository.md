---
title: Werken met AEM Forms Repository
description: Beheer de AEM Forms-opslagplaats om mappen te maken, mappen te schrijven, weer te geven, te lezen, bij te werken en te zoeken met behulp van de Java API en Web Service API. Bovendien leren hoe te om middelverhoudingen tot stand te brengen, middelen te sluiten en te schrappen.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: a07e51ca-fea0-4719-8071-1b7e805de2ae
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '9036'
ht-degree: 0%

---

# Werken met AEM Forms Repository {#working-with-aem-forms-repository}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

**Ongeveer de Dienst van de Bewaarplaats**

De Repository-service biedt AEM Forms opslagservices en beheerservices voor resources. Wanneer de ontwikkelaars tot een *AEM Forms* toepassing leiden, kunnen zij de activa in de bewaarplaats in plaats van het dossiersysteem opstellen. De elementen kunnen elk type onderpand bevatten, zoals XML-formulieren, PDF forms (inclusief Acrobat-formulieren), formulierfragmenten, afbeeldingen, profielen, beleid, SWF-bestanden, DDX-bestanden, XML-schema&#39;s, WSDL-bestanden en testgegevens.

Bijvoorbeeld, overweeg de volgende toepassing van Forms genoemd *Toepassingen/FormsApplication*:

![ ww_ww_formrepository ](assets/ww_ww_formrepository.png)

Er bevindt zich een bestand met de naam Loan.xdp in de FormsFolder. Als u dit formulierontwerp wilt openen, geeft u het volledige pad op (inclusief versie): `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.

>[!NOTE]
>
>Voor informatie over het creëren van een toepassing van Forms die Workbench gebruikt, zie [ Hulp Workbench ](https://www.adobe.com/go/learn_aemforms_workbench_63).

Het pad naar een resource in de AEM Forms-opslagplaats is:

`Applications/Application-name/Application-version/Folder.../Filename`

De volgende waarden tonen enkele voorbeelden van URI-waarden:

* Applications/AppraisalReport/1.0/Forms/FullForm.xdp
* Applications/AnotherApp/1.1/Assets/picture.jpg
* Applications/SomeApp/2.0/Resources/Data/XSDs/MyData.xsd

>[!NOTE]
>
>U kunt in de AEM Forms Repository bladeren met een webbrowser. Als u in de gegevensopslagruimte wilt bladeren, voert u de volgende URL in een webbrowser `https://[server name]:[server port]/repository` in. U kunt via een webbrowser controleren welke snelstartresultaten worden gekoppeld aan de sectie Werken met AEM Forms Repository. Als u bijvoorbeeld inhoud toevoegt aan de AEM Forms Repository, kunt u de inhoud zien in een webbrowser. (Zie [ Snelle Begin (SOAP wijze): Het schrijven van een middel gebruikend Java API ](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api).)

De API van de dataopslag biedt verschillende bewerkingen die u kunt gebruiken om gegevens op te slaan en op te halen uit de dataopslag. Bijvoorbeeld, kunt u een lijst van middelen verkrijgen of specifieke middelen terugwinnen die in de bewaarplaats worden opgeslagen wanneer een middel als deel van de verwerking van een toepassing nodig is.

>[!NOTE]
>
>De API van de dataopslag kan niet worden gebruikt om met de (afgekeurde) Diensten van de Inhoud in wisselwerking te staan. Als u wilt werken met Content Services (afgekeurd), gebruikt u de API voor documentbeheer.

Met de Repository-service-API kunt u de volgende taken uitvoeren:

* Maak mappen. Zie [ Creërend Omslagen ](aem-forms-repository.md#creating-folders).
* Bronnen en hun eigenschappen schrijven. Zie [ schrijvend Middelen ](aem-forms-repository.md#writing-resources).
* De middelen van de lijst in een bepaalde inzameling of verwant met andere middelen. Zie [ het Lijst Middelen ](aem-forms-repository.md#listing-resources).
* Bronnen en hun eigenschappen lezen. Zie [ Leesmiddelen ](aem-forms-repository.md#reading-resources).
* Bronnen en hun eigenschappen bijwerken. Zie [ Bijwerkend Middelen ](aem-forms-repository.md#updating-resources).
* Zoeken naar bronnen, waaronder hun geschiedenis, gerelateerde bronnen en eigenschappen. Zie [ zoekend naar Middelen ](aem-forms-repository.md#searching-for-resources).
* Geef relaties tussen bronnen op. Zie [ Creërend de Verhoudingen van het Middel ](aem-forms-repository.md#creating-resource-relationships).
* Beheer middeltoegangsbeheer, met inbegrip van het sluiten en het ontgrendelen van middelen, en het lezen en het schrijven toegangsbeheerlijsten (ACLs). Zie [ Vergrendelende Middelen ](aem-forms-repository.md#locking-resources).
* Bronnen en hun eigenschappen verwijderen. Zie [ het schrappen Middelen ](aem-forms-repository.md#deleting-resources).

>[!NOTE]
>
>Met behulp van de API van de dataopslag kunt u het beheer van de resourcetoegang niet beheren, kunt u niet zoeken naar bronnen en kunt u geen relaties met bronnen opgeven met behulp van een ECM-opslagplaats.

>[!NOTE]
>
>Wanneer een gecodeerde PDF naar de opslagplaats wordt geschreven, kan de functie voor automatische relatieextractie niet worden gebruikt. Anders kan een gecodeerde PDF worden opgeslagen in de opslagplaats en later worden opgehaald. De terugwader kan verkiezen om de PDF te decrypteren nadat het van de bewaarplaats wordt teruggewonnen.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

## Mappen maken {#creating-folders}

De omslagen (middelinzamelingen) worden gebruikt om voorwerpen (dossiers of middelen) in georganiseerde groepen op te slaan. Mappen kunnen bronnen en andere mappen bevatten, ook wel submappen genoemd. Bronnen kunnen slechts in één map tegelijk worden opgeslagen.

De dossiers erven toegangsbeheerlijsten (ACLs) van omslagen, en subfolders erven ACLs van hun ouderomslagen. Daarom moeten de bovenliggende mappen bestaan voordat u onderliggende mappen kunt maken. IDE laat u slechts op een omslag-door-omslag basis, niet op een dossier-door-dossier basis communiceren. U kunt geen mappen versieren en dat is niet nodig. Een map bevat geen gegevens zelf. In plaats daarvan is het alleen een container voor bronnen die gegevens bevatten. Standaard ACL is systeem-vlakke toestemming, zo betekent het dat de gebruikers systeemvlakke toestemmingen (lees, schrijf, traverse, het leiden ACLs) moeten hebben tot iemand hen toestemmingen voor een bepaalde omslag geeft. ACLs werkt slechts in winde.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Ga als volgt te werk om een map te maken:

1. Inclusief projectbestanden.
1. Maak de serviceclient.
1. Maak de map.
1. Schrijf de map naar de opslagplaats.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer de de dienstcliënt**

Alvorens u een middelinzameling programmatically kunt tot stand brengen, moet u een verbinding vestigen en geloofsbrieven verstrekken. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**creeer de omslag**

Roep de servicemethode voor opslagplaats aan om de bronverzameling te maken en de bronverzameling te vullen met identificerende informatie, zoals de UUID, mapnaam en beschrijving van de verzameling.

**schrijft de omslag aan de bewaarplaats**

Roep de servicemethode Repository aan om de bronverzameling te schrijven en de URI van de doelmap op te geven.

**zie ook**

[Mappen maken met de Java API](aem-forms-repository.md#create-folders-using-the-java-api)

[Mappen maken met de webservice-API](aem-forms-repository.md#create-folders-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Mappen maken met de Java API {#create-folders-using-the-java-api}

Een map maken met de API voor opslagplaats (Java):

1. Projectbestanden opnemen

   Neem projectbestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. De map maken

   Als u een bronverzameling wilt maken, moet u eerst een `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean` -object maken.

   Roep de methode `newResourceCollection` van het object `repositoryInfomodelFactoryBean` aan en geef de volgende parameters door:

   * Een `com.adobe.repository.infomodel.Id` UUID-id die aan de bron moet worden toegewezen.
   * Een `com.adobe.repository.infomodel.Lid` UUID-id die aan de bron moet worden toegewezen.
   * A `java.lang.String` met de naam van de bronverzameling. Bijvoorbeeld `FormsFolder` .

   De methode retourneert een `com.adobe.repository.infomodel.bean.ResourceCollection` -object dat de nieuwe map vertegenwoordigt.

   Stel de beschrijving van de map in met de methode `setDescription` en geef de volgende parameter door:

   * A `String` dat de middelinzameling beschrijft. In dit voorbeeld wordt `"test Folder"` gebruikt `.`

1. De map naar de opslagplaats schrijven

   Roep de methode `writeResource` van het object `ResourceRepositoryClient` aan en geef de URI van de map en het object `ResourceCollection` door. De URI naar de map kan bijvoorbeeld de volgende waarde `/Applications/FormsApplication/1.0/` zijn.

   De methode retourneert een instantie van het nieuwe `com.adobe.repository.infomodel.bean.Resource` -object. U kunt bijvoorbeeld de id-waarde van de nieuwe bron ophalen door de methode `getId` van het object `com.adobe.repository.infomodel.bean.Resource` aan te roepen.

**zie ook**

[Mappen maken](aem-forms-repository.md#creating-folders)

[Snel starten (SOAP modus): een map maken met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-a-folder-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Mappen maken met de webservice-API {#create-folders-using-the-web-service-api}

Een map maken met de Repository Service API (webservice):

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die de Bewaarplaats WSDL gebruikend base64 verbruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. De serviceclient maken

   Gebruikend de Microsoft .NET cliëntassemblage, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de eigenschap `Credentials` ervan in met een `System.Net.NetworkCredential` -object dat de gebruikersnaam en het wachtwoord bevat.

1. De map maken

   Maak de map met de standaardconstructor voor de klasse `ResourceCollection` en geef de volgende parameters door:

   * Een `Id` -object dat wordt gemaakt door de standaardconstructor voor de `Id` -klasse aan te roepen en toegewezen aan het `Resource` -veld `id` van het object.
   * Een `Lid` -object dat wordt gemaakt door de standaardconstructor voor de `Lid` -klasse aan te roepen en toegewezen aan het `Resource` -veld `lid` van het object.
   * Een tekenreeks met de naam van de bronverzameling die wordt toegewezen aan het veld `name` van het object `Resource` . In dit voorbeeld wordt de naam `"testfolder"` gebruikt.
   * Een tekenreeks met de beschrijving van de bronverzameling die wordt toegewezen aan het veld `description` van het object `Resource` . De beschrijving die in dit voorbeeld wordt gebruikt, is `"test folder"` .

1. De map naar de opslagplaats schrijven

   Roep de methode `writeResource` van het object `RepositoryServiceService` aan en geef de volgende parameters door:

   * Het pad waar de map moet worden gemaakt.
   * Het `ResourceCollection` -object dat de map vertegenwoordigt.
   * Geef `null` door voor de andere twee parameters.

**zie ook**

[Mappen maken](aem-forms-repository.md#creating-folders)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Bronnen schrijven {#writing-resources}

U kunt bronnen maken op een bepaalde locatie in de opslagplaats. De natuurlijke dossiergrootte is onderworpen aan gegevensbestandbeperkingen en zittingsonderbreking. Voor de standaardconfiguratie, zijn de dossiers beperkt tot 25 MB. Als u de maximale bestandsgrootte wilt verhogen of verlagen, moet u de databaseconfiguratie wijzigen.

Het schrijven van bronnen is gelijk aan het opslaan van gegevens in de opslagplaats. Zodra u een middel aan de bewaarplaats schrijft, wordt het toegankelijk voor alle cliënten in het bewaarplaats ecosysteem. Wanneer u bronnen naar de opslagplaats schrijft, zoals XML-schema&#39;s, XDP-bestanden en XSD-bestanden, wordt de inhoud geparseerd op basis van het MIME-type. Als het MIME-type wordt ondersteund, bepaalt de parser of er een impliciete relatie met andere inhoud is. Als een CSS (Cascading Style Sheet) bijvoorbeeld een relatieve URL heeft die verwijst naar een gemeenschappelijke CSS, wordt verwacht dat u de gemeenschappelijke CSS ook in de opslagplaats zult verzenden. De relatie tussen de twee bronnen wordt gedurende een niet-aanpasbare periode van 30 dagen opgeslagen als een hangende relatie. Wanneer u de algemene CSS binnen de periode van 30 dagen naar de opslagplaats verzendt, wordt de relatie gevormd.

Wanneer u een middel creeert, wordt de toegangsbeheerlijst (ACL) geërft van de ouderomslag. De wortelomslag heeft systeem-vlakke toestemmingen tot een eerste middel of een omslag wordt gecreeerd, waarbij het middel of de omslag standaardACL toestemmingen wordt gegeven.

U kunt bronnen programmatisch schrijven met de Java API of webservice van de Repository-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een resource te schrijven:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Geef de URI op van de bron die moet worden gelezen.
1. Lees de bron.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer de de dienstcliënt**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**specificeer URI van de doelomslag voor het middel**

Maak een tekenreeks met de URI van de bron die moet worden gelezen. De syntaxis omvat voorwaartse schuine strepen, zoals in dit voorbeeld: &quot;/*weg*/ *omslag*&quot;.

**creeer het middel**

Roep de servicemethode voor opslagplaats aan om de bron te maken en de bron te vullen met identificerende informatie, waaronder de UUID, de naam van de bron en een beschrijving.

**specificeer de middelinhoud**

Roep de de dienstmethode van de Bewaarplaats aan om middelinhoud tot stand te brengen, en die inhoud in het middel op te slaan.

**schrijf het middel aan de doelomslag**

Roep de servicemethode Repository aan om de bron te schrijven en de URI van de doelmap op te geven.

**zie ook**

[Bronnen schrijven met de Java API](aem-forms-repository.md#write-resources-using-the-java-api)

[Bronnen schrijven met de webservice-API](aem-forms-repository.md#write-resources-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bronnen schrijven met de Java API {#write-resources-using-the-java-api}

Schrijf een bron met behulp van de Repository Service API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. De URI van de doelmap voor de bron opgeven

   Geef de URI van de doelmap voor de bron op. In dit geval is de URI van de map `"/testFolder"` omdat de bron met de naam `testResource` wordt opgeslagen in de map met de naam `testFolder` . De URI wordt opgeslagen als een `java.lang.String` -object.

1. De bron maken

   Als u een bron wilt maken, moet u eerst een `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean` -object maken.

   Roep de methode `newResource` van het object `RepositoryInfomodelFactoryBean` aan, die een object `com.adobe.repository.infomodel.bean.Resource` maakt. In dit voorbeeld worden de volgende parameters opgegeven:

   * Een object `com.adobe.repository.infomodel.Id` dat wordt gemaakt door de standaardconstructor voor de klasse `Id` aan te roepen.
   * Een object `com.adobe.repository.infomodel.Lid` dat wordt gemaakt door de standaardconstructor voor de klasse `Lid` aan te roepen.
   * A `java.lang.String` containing the file name of the resource.

   Als u de beschrijving van de bron wilt opgeven, roept u de methode `setDescription` van het object `Resource` aan en geeft u een tekenreeks met de beschrijving door. In dit voorbeeld is de beschrijving `"test resource"` .

1. De inhoud van de bron opgeven

   Als u inhoud voor de bron wilt maken, roept u de methode `newResourceContent` van het object `RepositoryInfomodelFactoryBean` aan, die een object `com.adobe.repository.infomodel.bean.ResourceContent` retourneert. Voeg inhoud toe aan het `ResourceContent` -object. In dit voorbeeld worden de volgende taken uitgevoerd:

   * De methode `setDataDocument` van het object `ResourceContent` aanroepen en een object `com.adobe.idp.Document` doorgeven
   * De methode `setSize` van het object `ResourceContent` aanroepen en de grootte van het object `Document` in bytes doorgeven

   Voeg de inhoud aan de bron toe door de methode `setContent` van het object `Resource` aan te roepen en het object `ResourceContent` door te geven. Voor meer informatie, zie [ AEM Forms API Verwijzing ](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

1. De bron naar de doelmap schrijven

   Roep de methode `writeResource` van het object `ResourceRepositoryClient` aan en geef de URI van de map en het object `Resource` door.

**zie ook**

[Bronnen schrijven](aem-forms-repository.md#writing-resources)

[Snel starten (SOAP modus): een bron schrijven met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bronnen schrijven met de webservice-API {#write-resources-using-the-web-service-api}

Schrijf een bron met behulp van de Repository Service API (webservice):

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die de Bewaarplaats WSDL gebruikend base64 verbruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. De serviceclient maken

   Gebruikend de Microsoft .NET cliëntassemblage, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de eigenschap `Credentials` ervan in met een `System.Net.NetworkCredential` -object dat de gebruikersnaam en het wachtwoord bevat.

1. De URI van de doelmap voor de bron opgeven

   Geef de URI van de doelmap voor de bron op. In dit geval is de URI van de map `"/testFolder"` omdat de bron met de naam `testResource` wordt opgeslagen in de map met de naam `testFolder` . Wanneer het gebruiken van een taal volgzaam met het Kader van Microsoft .NET (bijvoorbeeld, C#), bewaar URI in een `System.String` voorwerp.

1. De bron maken

   Als u een bron wilt maken, roept u de standaardconstructor voor de klasse `Resource` aan. In dit voorbeeld wordt de volgende informatie opgeslagen in het `Resource` -object:

   * Een `com.adobe.repository.infomodel.Id` -object dat wordt gemaakt door de standaardconstructor voor de `Id` -klasse aan te roepen en toegewezen aan het `Resource` -veld `id` van het object.
   * Een `com.adobe.repository.infomodel.Lid` -object dat wordt gemaakt door de standaardconstructor voor de `Lid` -klasse aan te roepen en toegewezen aan het `Resource` -veld `lid` van het object.
   * Een tekenreeks met de bestandsnaam van de bron die wordt toegewezen aan het veld `name` van het object `Resource` . In dit voorbeeld wordt de naam `"testResource"` gebruikt.
   * Een tekenreeks met de beschrijving van de bron die wordt toegewezen aan het veld `description` van het object `Resource` . De beschrijving die in dit voorbeeld wordt gebruikt, is `"test resource"` .

1. De inhoud van de bron opgeven

   Als u inhoud voor de bron wilt maken, roept u de standaardconstructor voor de klasse `ResourceContent` aan. Voeg vervolgens inhoud toe aan het object `ResourceContent` . In dit voorbeeld worden de volgende taken uitgevoerd:

   * Een `BLOB` -object met een document toewijzen aan het veld `ResourceContent` object `dataDocument` .
   * De grootte van het object `BLOB` in bytes toewijzen aan het veld `ResourceContent` object `size` .

   Voeg de inhoud aan de bron toe door het `ResourceContent` -object toe te wijzen aan het veld `Resource` object `content` .

1. De bron naar de doelmap schrijven

   Roep de methode `writeResource` van het object `RepositoryServiceService` aan en geef de URI van de map en het object `Resource` door. Geef `null` door voor de andere twee parameters.

**zie ook**

[Bronnen schrijven](aem-forms-repository.md#writing-resources)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Aanbiedingsbronnen {#listing-resources}

Je kunt bronnen vinden door bronnen aan te bieden. Een vraag wordt uitgevoerd tegen de bewaarplaats om alle middelen te vinden die met een bepaalde middelinzameling verwant zijn.

Zodra u uw middelen organiseert, kunt u de structuur inspecteren u door een bepaalde tak van de structuur te zien creeerde, veel als u in een werkend systeem zou doen.

De lijstmiddelen werken door verhouding: de middelen zijn leden van omslagen. Lidmaatschap wordt vertegenwoordigd door een relatie van het type &quot;lid van&quot;. Wanneer u bronnen in een bepaalde map opsomt, zoekt u naar bronnen die verwant zijn aan een bepaalde map door de relatie &quot;lid van&quot;. Relaties zijn gericht: een lid van een relatie heeft een bron die lid is van het doel. De bron is de bron; het doel is de bovenliggende map.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om bronnen weer te geven:

1. Inclusief projectbestanden.
1. Maak de serviceclient.
1. Geef het mappad op.
1. Haal de lijst met bronnen op.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer de de dienstcliënt**

Alvorens u een middelinzameling programmatically kunt tot stand brengen, moet u een verbinding vestigen en geloofsbrieven verstrekken. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**specificeer de omslagweg**

Maak een tekenreeks met het pad van de map met de bronnen. De syntaxis omvat voorwaartse schuine strepen, zoals in dit voorbeeld: &quot;/*weg*/ *omslag*&quot;.

**wint de lijst van middelen** terug

Roep de servicemethode voor gegevensopslagruimte aan om de lijst met bronnen op te halen en geef het pad van de doelmap op.

**zie ook**

[Bronnen weergeven met de Java API](aem-forms-repository.md#list-resources-using-the-java-api)

[Bronnen weergeven met de webservice-API](aem-forms-repository.md#list-resources-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bronnen weergeven met de Java API {#list-resources-using-the-java-api}

Bronnen weergeven met behulp van de Repository Service API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. Het mappad opgeven

   Geef de URI op van de bronverzameling die moet worden opgevraagd. In dit geval is de URI `"/testFolder"` . De URI wordt opgeslagen als een `java.lang.String` -object.

1. De lijst met bronnen ophalen

   Roep de methode `listMembers` van het object `ResourceRepositoryClient` aan en geef deze door in de URI van de map.

   De methode retourneert een `java.util.List` van `com.adobe.repository.infomodel.bean.Resource` -objecten die de bron zijn van een `com.adobe.repository.infomodel.bean.Relation` van het type `Relation.TYPE_MEMBER_OF` en die de URI van de bronverzameling als doel hebben. U kunt door dit `List` herhalen om elk van de middelen terug te winnen. In dit voorbeeld worden de naam en beschrijving van elke bron weergegeven.

**zie ook**

[ het Lijst Middelen ](aem-forms-repository.md#listing-resources).

[Snel starten (SOAP modus): bronnen weergeven met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-listing-resources-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bronnen weergeven met de webservice-API {#list-resources-using-the-web-service-api}

Bronnen weergeven met de Repository Service API (webservice):

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die de Bewaarplaats WSDL verbruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. De serviceclient maken

   Gebruikend de Microsoft .NET cliëntassemblage, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de eigenschap `Credentials` ervan in met een `System.Net.NetworkCredential` -object dat de gebruikersnaam en het wachtwoord bevat.

1. Het mappad opgeven

   Geef een tekenreeks op die de URI bevat van de map waarnaar wordt gevraagd. In dit geval is de URI `"/testFolder"` . Wanneer het gebruiken van een taal die met het Kader van Microsoft .NET (bijvoorbeeld, C#) volgzaam is, bewaar URI in een `System.String` voorwerp.

1. De lijst met bronnen ophalen

   Roep de methode `listMembers` van het object `RepositoryServiceService` aan en geef de URI van de map door als de eerste parameter. Geef `null` door voor de andere twee parameters.

   De methode retourneert een array met objecten die naar `Resource` -objecten kunnen worden gecast. U kunt de objectarray doorlopen om elk van de gerelateerde bronnen op te halen. In dit voorbeeld worden de naam en beschrijving van elke bron weergegeven.

**zie ook**

[ het Lijst Middelen ](aem-forms-repository.md#listing-resources).

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Bronnen lezen {#reading-resources}

U kunt bronnen ophalen van een bepaalde locatie in de opslagplaats om de inhoud en metagegevens te lezen. De workflow wordt voorafgegaan door een initialisatieformulier. Het proces heeft alle machtigingen die het nodig heeft om het formulier te lezen. Het systeem haalt het gegevensformulier op en leest de inhoud uit de gegevensopslagruimte. De opslagplaats verleent toegang tot de inhoud en de meta-gegevens (de capaciteit zelfs om het middel te weten bestaat).

De repository heeft de volgende vier machtigingstypen:

* **dwars**: laat u van middelen een lijst maken; namelijk om middelmeta-gegevens, maar geen middelinhoud te lezen
* **gelezen**: laat u middelinhoud lezen
* **schrijft**: laat u middelinhoud schrijven
* **het beheren van toegangsbeheerlijsten (ACLs)**: laat u ACLs op middelen manipuleren

Gebruikers kunnen alleen processen uitvoeren als zij gemachtigd zijn het proces uit te voeren. IDE-gebruikers hebben verplaatsings- en leesmachtigingen nodig om te synchroniseren met de repository. ACLs is slechts in ontwerptijd van toepassing omdat runtime binnen de systeemcontext voorkomt.

U kunt bronnen programmatisch lezen met de Java API of webservice van de Repository-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende stappen uit om een bron te lezen:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Geef de URI op van de bron die moet worden gelezen.
1. Lees de bron.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer de de dienstcliënt**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**specificeer URI van het te lezen middel**

Maak een tekenreeks met de URI van de bron die moet worden gelezen. De syntaxis omvat voorwaartse schuine strepen, zoals in dit voorbeeld: &quot;/*weg*/ *middel*&quot;.

**las het middel**

Roep de servicemethode Repository aan om de bron te lezen en de URI op te geven.

**zie ook**

[Bronnen lezen met de Java API](aem-forms-repository.md#read-resources-using-the-java-api)

[Bronnen lezen met de webservice-API](aem-forms-repository.md#reading-resources-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bronnen lezen met de Java API {#read-resources-using-the-java-api}

Een bron lezen met de API voor opslagplaats (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. De URI opgeven van de te lezen bron

   Geef een tekenreekswaarde op die de URI vertegenwoordigt van de bron die moet worden opgehaald. Bijvoorbeeld, veronderstellend wordt het middel genoemd *testResource* dat in een omslag genoemd *testFolder* is, specificeer `/testFolder/testResource`.

1. De bron lezen

   Roep de methode `readResource` van het object `ResourceRepositoryClient` aan en geef de URI van de bron door als parameter. Deze methode retourneert een `Resource` -instantie die de bron vertegenwoordigt.

**zie ook**

[Bronnen lezen](aem-forms-repository.md#reading-resources)

[Snel starten (SOAP modus): Een bron lezen met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-reading-a-resource-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bronnen lezen met de webservice-API {#reading-resources-using-the-web-service-api}

Een bron lezen met de Repository Service API (webservice):

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die de Bewaarplaats WSDL verbruikt. (Zie [ Creërend een .NET cliëntassemblage die het coderen Base64 ](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding) gebruikt.)
   * Verwijs naar de Microsoft .NET cliëntassemblage. (Zie [ Creërend een .NET cliëntassemblage die het coderen Base64 ](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding) gebruikt.)

1. De serviceclient maken

   Gebruikend de Microsoft .NET cliëntassemblage, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de eigenschap `Credentials` ervan in met een `System.Net.NetworkCredential` -object dat de gebruikersnaam en het wachtwoord bevat.

1. De URI opgeven van de te lezen bron

   Geef een tekenreeks op die de URI bevat van de bron die moet worden opgehaald. In dit geval is de URI `"/testFolder/testResource"` omdat de bron met de naam `testResource` zich in de map met de naam `testFolder` bevindt. Wanneer het gebruiken van een taal volgzaam met het Kader van Microsoft .NET (bijvoorbeeld, C#), bewaar URI in een `System.String` voorwerp.

1. De bron lezen

   Roep de methode `readResource` van het object `RepositoryServiceService` aan en geef de URI van de bron door als de eerste parameter. Geef `null` door voor de andere twee parameters.

**zie ook**

[Bronnen lezen](aem-forms-repository.md#reading-resources)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Bronnen bijwerken {#updating-resources}

U kunt de inhoud van bronnen in de opslagplaats ophalen en bijwerken. Wanneer u middelen bijwerkt, blijft het toegangsbeheer tot die middelen onveranderd tussen versies. Wanneer u een update uitvoert, kunt u de hoofdversie verhogen. Als u er niet voor kiest de hoofdversie te verhogen, wordt de kleine versie automatisch bijgewerkt.

Wanneer u een bron bijwerkt, wordt de nieuwe versie gemaakt op basis van de opgegeven bronkenmerken. Wanneer u een bron bijwerkt, geeft u twee belangrijke parameters op: de doel-URI en een resource-instantie die alle bijgewerkte metagegevens bevat. Het is belangrijk om op te merken dat als u een bepaald attribuut (bijvoorbeeld, de naam) niet verandert, het attribuut nog wordt vereist in de instantie u binnen overgaat. De relaties die worden gemaakt bij het parseren van de inhoud, worden toegevoegd aan de specifieke versie en worden alleen naar voren gebracht als dat is opgegeven.

Als u bijvoorbeeld een XDP-bestand bijwerkt dat verwijzingen naar andere bronnen bevat, worden deze aanvullende verwijzingen ook opgenomen. Stel dat form.xdp versie 1.0 twee externe referenties heeft: een logo en een stijlpagina en u werkt form.xdp vervolgens bij, zodat het nu drie referenties heeft: een logo, een stijlpagina en een schemabestand. Tijdens de update voegt de dataopslag de derde relatie (aan het schemabestand) toe aan de relatietabel die in behandeling is. Zodra het schemadossier in de bewaarplaats aanwezig is, zal de verhouding automatisch worden gevormd. Als form.xdp versie 2.0 het logo echter niet meer gebruikt, heeft form.xdp versie 2.0 geen relatie met het logo.

Alle updatebewerkingen zijn atomisch en transactioneel. Als twee gebruikers bijvoorbeeld dezelfde bron lezen en beide besluiten versie 1.0 bij te werken naar versie 2.0, zal één van hen slagen en één van hen zal ontbreken, zal de integriteit van de repository worden gehandhaafd, en beide zullen een bericht krijgen dat succes of mislukking bevestigt. Als de transactie niet begaan, zal het terugdraaien als er een gegevensbestandmislukking is en uit tijd of terugloop afhankelijk van de toepassingsserver zal zijn.

U kunt bronnen programmatisch bijwerken met de Java API of webservice van de Repository-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om een bron bij te werken:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Haal de bron op die u wilt bijwerken.
1. Werk de bron bij.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer de de dienstcliënt**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**wint het middel terug om worden bijgewerkt**

Lees de bron. Voor meer informatie, zie [ Leesmiddelen ](aem-forms-repository.md#reading-resources).

**werk het middel** bij

Plaats de nieuwe informatie in het middel en haal de de dienstmethode van de Bewaarplaats aan om het middel bij te werken, specificerend URI, het bijgewerkte middel, en hoe de versieinformatie zou moeten worden bijgewerkt.

**zie ook**

[Bronnen bijwerken met de Java API](aem-forms-repository.md#update-resources-using-the-java-api)

[Bronnen bijwerken met de webservice-API](aem-forms-repository.md#update-resources-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bronnen bijwerken met de Java API {#update-resources-using-the-java-api}

Werk een bron bij met behulp van de Repository Service API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. De bron ophalen die moet worden bijgewerkt

   Geef de URI op van de bron die u wilt ophalen en lezen. In dit voorbeeld is de URI van de bron `"/testFolder/testResource"` .

1. De bron bijwerken

   Werk de gegevens van het `Resource` -object bij. Als u in dit voorbeeld de beschrijving wilt bijwerken, roept u de methode `setDescription` van het object `Resource` aan en geeft u de nieuwe beschrijvende tekenreeks door als parameter.

   Roep vervolgens de methode `updateResource` van het object `ServiceClientFactory` aan en geef de volgende parameters door:

   * Een `java.lang.String` -object dat de URI van de bron bevat.
   * Het `Resource` -object dat de bijgewerkte broninformatie bevat.
   * Een `boolean` -waarde die aangeeft of de hoofd- of subversie moet worden bijgewerkt. In dit voorbeeld wordt de waarde `true` doorgegeven om aan te geven dat de hoofdversie moet worden verhoogd.

**zie ook**

[Bronnen bijwerken](aem-forms-repository.md#updating-resources)

[Snel starten (SOAP modus): Een bron bijwerken met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-updating-a-resource-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bronnen bijwerken met de webservice-API {#update-resources-using-the-web-service-api}

Een bron bijwerken met de Repository API (webservice):

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die de Bewaarplaats WSDL verbruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. De serviceclient maken

   Gebruikend de Microsoft .NET cliëntassemblage, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de eigenschap `Credentials` ervan in met een `System.Net.NetworkCredential` -object dat de gebruikersnaam en het wachtwoord bevat.

1. De bron ophalen die moet worden bijgewerkt

   Geef de URI op van de bron die moet worden opgehaald en lees de bron. In dit voorbeeld is de URI van de bron `"/testFolder/testResource"` . Voor meer informatie, zie [ Leesmiddelen ](aem-forms-repository.md#reading-resources).

1. De bron bijwerken

   Werk de gegevens van het `Resource` -object bij. In dit voorbeeld wijst u een nieuwe waarde toe aan het veld `description` van het `Resource` -object om de beschrijving bij te werken.

1. Roep de methode `updateResource` van het object `RepositoryServiceService` aan en geef de volgende parameters door:

   * Een `System.String` -object dat de URI van de bron bevat.
   * Het `Resource` -object dat de bijgewerkte broninformatie bevat.
   * Een `boolean` -waarde die aangeeft of de hoofd- of subversie moet worden bijgewerkt. In dit voorbeeld wordt de waarde `true` doorgegeven om aan te geven dat de hoofdversie moet worden verhoogd.
   * Geef `null` door voor de resterende twee parameters.

**zie ook**

[Bronnen bijwerken](aem-forms-repository.md#updating-resources)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Zoeken naar bronnen {#searching-for-resources}

U kunt vragen construeren die worden gebruikt om naar middelen in de bewaarplaats, met inbegrip van geschiedenis, verwante middelen, en eigenschappen te zoeken.

U kunt gerelateerde bronnen ophalen om de afhankelijkheden tussen een formulier en de bijbehorende fragmenten te bepalen. Als u bijvoorbeeld een formulier hebt, kunt u bepalen welke fragmenten of externe bronnen het gebruikt. Als u een afbeelding hebt, kunt u ook nagaan in welke formulieren de afbeelding wordt gebruikt. U kunt ook naar gerelateerde bronnen zoeken door filteren op basis van eigenschappen. U kunt bijvoorbeeld zoeken naar alle formulieren die een afbeelding met een opgegeven naam gebruiken, of naar afbeeldingen die worden gebruikt door een formulier met een opgegeven naam. U kunt ook zoeken met eigenschappen van bronnen. U kunt bijvoorbeeld een query uitvoeren om alle formulieren of bronnen te zoeken waarvan de naam begint met een bepaalde tekenreeks die jokertekens &#39;%&#39; en &#39;_&#39; kan bevatten. Herinner dat de onderzoeken die op eigenschappen worden gebaseerd niet op verhoudingen zijn gebaseerd; dergelijke onderzoeken zijn gebaseerd op de veronderstelling dat u specifieke kennis over een bepaalde middel hebt.

**verklaringen van de Vraag**

A *vraag* bevat één of meerdere verklaringen die logisch gezien met voorwaarden worden verbonden. A *verklaring* bestaat uit een linkeroperand, een exploitant, en een juiste operand. Bovendien kunt u de sorteervolgorde opgeven die voor de zoekresultaten moet worden gebruikt. De *soortorde* bevat informatie gelijkwaardig aan een SQL `ORDER BY` clausule en bestaat uit elementen die de attributen bevatten waarop het onderzoek werd gebaseerd en een waarde erop wijst die of het stijgen of dalende orde moet worden gebruikt.

U kunt programmatically naar middelen zoeken door de dienstJava API van de Bewaarplaats te gebruiken. Op dit moment is het niet mogelijk om de webservice-API te gebruiken om te zoeken naar bronnen.

**gedrag van de Soort**

De sorteervolgorde wordt niet gerespecteerd wanneer u de methode `searchProperties` van het object `ResourceRepositoryClient` aanroept en een sorteervolgorde opgeeft. Stel dat u een bron maakt met drie aangepaste eigenschappen, waarbij kenmerknamen `name`, `secondName` en `asecondName` zijn. Vervolgens maakt u een sorteervolgordelement op de kenmerknaam en stelt u de `ascending` -waarde in op `true` .

Vervolgens activeert u de methode `searchProperties` van het object `ResourceRepositoryClient` en geeft u de sorteervolgorde door. De zoekopdracht retourneert de juiste bron, met de drie eigenschappen. De eigenschappen worden echter niet gesorteerd op kenmerknaam. Deze worden geretourneerd in de volgorde waarin ze zijn toegevoegd: `name` , `secondName` en `asecondName` .

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-5}

Ga als volgt te werk om naar bronnen te zoeken:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Geef de doelmap voor de zoekopdracht op.
1. Geef de kenmerken op die in de zoekopdracht worden gebruikt.
1. Maak de query die wordt gebruikt in de zoekopdracht.
1. Maak de sorteervolgorde voor de zoekresultaten.
1. Zoek de bronnen.
1. Haal de bronnen op uit het zoekresultaat.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer de de dienstcliënt**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**specificeer de doelomslag voor het onderzoek**

Maak een tekenreeks met het basispad waaruit de zoekopdracht moet worden uitgevoerd. De syntaxis omvat voorwaartse schuine strepen, zoals in dit voorbeeld: &quot;/*weg*/ *omslag*&quot;.

**specificeer de attributen die in het onderzoek** worden gebruikt

U kunt uw zoekopdracht baseren op de kenmerken in de bronnen. Geef de waarden op van de kenmerken waarop de zoekopdracht moet worden uitgevoerd.

**creeer de vraag die in het onderzoek** wordt gebruikt

Construeer een vraag door verklaringen en voorwaarden te gebruiken. Elke instructie geeft het kenmerk op waarop de zoekopdracht moet worden gebaseerd, de voorwaarde die moet worden gebruikt en de kenmerkwaarde die in de zoekopdracht moet worden gebruikt.

**creeer de soortorde voor de onderzoeksresultaten**

De sorteervolgorde bestaat uit elementen, die elk een van de kenmerken bevatten die in de zoekopdracht worden gebruikt en een waarde die aangeeft of oplopende of aflopende volgorde moet worden gebruikt.

**Onderzoek naar de middelen**

Zoek naar de middelen gebruikend de omslag, de vraag, en de soortorde. Geef bovendien de diepte van de zoekopdracht en een bovengrens op voor het aantal resultaten dat moet worden geretourneerd.

**wint de middelen van het onderzoeksresultaat** terug

Doorloop de geretourneerde lijst met bronnen en extraheer de informatie voor verdere verwerking.

**zie ook**

[Zoeken naar bronnen met de Java API](aem-forms-repository.md#search-for-resources-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Zoeken naar bronnen met de Java API {#search-for-resources-using-the-java-api}

Zoek naar een bron met behulp van de Repository Service API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. De doelmap voor de zoekopdracht opgeven

   Geef de URI op van het basispad waaruit de zoekopdracht moet worden uitgevoerd. In dit voorbeeld is de URI van de bron `/testFolder` .

1. De kenmerken opgeven die in de zoekopdracht worden gebruikt

   Geef de waarden op voor de kenmerken waarop de zoekopdracht moet worden uitgevoerd. De kenmerken bestaan binnen een `com.adobe.repository.infomodel.bean.Resource` -object. In dit voorbeeld wordt de zoekopdracht uitgevoerd op het kenmerk name. Daarom wordt een `java.lang.String` met de naam van het object `Resource` gebruikt, wat in dit geval `testResource` is.

1. De query maken die wordt gebruikt in de zoekopdracht

   Als u een query wilt maken, maakt u een `com.adobe.repository.query.Query` -object door de standaardconstructor voor de `Query` -klasse aan te roepen en voegt u instructies toe aan de query.

   Als u een instructie wilt maken, roept u de constructor voor de klasse `com.adobe.repository.query.Query.Statement` aan en geeft u de volgende parameters door:

   * Een linkeroperand die de constante van het middelattribuut bevat. In dit voorbeeld wordt de statische waarde `Resource.ATTRIBUTE_NAME` gebruikt, omdat de naam van de bron wordt gebruikt als basis voor de zoekopdracht.
   * Een operator die de voorwaarde bevat die wordt gebruikt in de zoekopdracht naar het kenmerk. De operator moet een van de statische constanten in de `Query.Statement` -klasse zijn. In dit voorbeeld wordt de statische waarde `Query.Statement.OPERATOR_BEGINS_WITH` gebruikt.
   * Een rechteroperand die de kenmerkwaarde bevat waarop de zoekopdracht moet worden uitgevoerd. In dit voorbeeld wordt het kenmerk name gebruikt, een `String` met de waarde `"testResource"` .

   Geef de naamruimte van de linkeroperand op door de methode `setNamespace` van het object `Query.Statement` aan te roepen en een van de statische waarden in de klasse `com.adobe.repository.infomodel.bean.ResourceProperty` door te geven. In dit voorbeeld wordt `ResourceProperty.RESERVED_NAMESPACE_REPOSITORY` gebruikt.

   Voeg elke instructie aan de query toe door de methode `addStatement` van het object `Query` aan te roepen en het object `Query.Statement` door te geven.

1. De sorteervolgorde voor de zoekresultaten maken

   Als u de sorteervolgorde wilt opgeven die in de zoekresultaten wordt gebruikt, maakt u een `com.adobe.repository.query.sort.SortOrder` -object door de standaardconstructor voor de klasse `SortOrder` aan te roepen en voegt u elementen toe aan de sorteervolgorde.

   Als u een element voor de sorteervolgorde wilt maken, roept u een van de constructors voor de klasse `com.adobe.repository.query.sort.SortOrder.Element` aan. In dit voorbeeld wordt, omdat de naam van de bron wordt gebruikt als basis voor de zoekopdracht, de statische waarde `Resource.ATTRIBUTE_NAME` gebruikt als de eerste parameter en de oplopende volgorde (een `boolean` waarde van `true`) wordt opgegeven als de tweede parameter.

   Voeg elk element aan de sorteervolgorde toe door de methode `addSortElement` van het object `SortOrder` aan te roepen en het object `SortOrder.Element` door te geven.

1. Zoeken naar de bronnen

   Als u naar `resources` wilt zoeken op basis van kenmerkeigenschappen, roept u de methode `ResourceRepositoryClient` object `searchProperties` aan en geeft u de volgende parameters door:

   * Een `String` met het basispad waaruit de zoekopdracht moet worden uitgevoerd. In dit geval wordt `"/testFolder"` gebruikt.
   * De query die wordt gebruikt in de zoekopdracht.
   * De diepte van de zoekopdracht. In dit geval wordt `com.adobe.repository.infomodel.bean.ResourceCollection.DEPTH_INFINITE` gebruikt om aan te geven dat het basispad en alle bijbehorende mappen moeten worden gebruikt.
   * Een `int` -waarde die de eerste rij aangeeft waaruit de niet-gepagineerde resultatenset moet worden geselecteerd. In dit voorbeeld wordt `0` opgegeven.
   * Een `int` -waarde die het maximale aantal resultaten aangeeft dat moet worden geretourneerd. In dit voorbeeld wordt `10` opgegeven.
   * De sorteervolgorde die in de zoekopdracht wordt gebruikt.

   De methode retourneert een `java.util.List` van `Resource` -object in de opgegeven sorteervolgorde.

1. De bronnen ophalen uit het zoekresultaat

   Als u de bronnen in het zoekresultaat wilt ophalen, doorloopt u `List` en cast u elk object naar een `Resource` om de informatie ervan op te halen. In dit voorbeeld wordt de naam van elke bron weergegeven.

**zie ook**

[Zoeken naar bronnen](aem-forms-repository.md#searching-for-resources)

[Snel starten (SOAP modus): zoeken naar bronnen met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Resourcerelaties maken {#creating-resource-relationships}

U kunt relaties tussen bronnen in de opslagplaats opgeven. Er zijn drie soorten relaties:

* **Afhankelijkheid**: een verhouding waarin een middel van andere middelen afhangt, betekenend dat alle verwante middelen in de bewaarplaats nodig zijn.
* **Lidmaatschap (dossiersysteem)**: een verhouding waarin een middel binnen een bepaalde omslag wordt gevestigd.
* **Douane**: een verhouding u tussen middelen specificeert. Bijvoorbeeld, als één middel is afgekeurd en een andere middel in de bewaarplaats is geïntroduceerd, kon u uw eigen vervangingsverhouding specificeren.

U kunt uw eigen aangepaste relaties maken. Als u bijvoorbeeld een HTML-bestand opslaat in de opslagplaats en een afbeelding gebruikt, kunt u een aangepaste relatie opgeven om het HTML-bestand te koppelen aan de afbeelding (aangezien doorgaans alleen XML-bestanden worden gekoppeld aan afbeeldingen die een door de opslagplaats gedefinieerde afhankelijkheidsrelatie gebruiken). Een ander voorbeeld van een aangepaste relatie is als u een andere weergave van de opslagplaats wilt maken met een cyclische grafiekstructuur in plaats van een boomstructuur. U kunt een cirkelvormige grafiek samen met een kijker definiëren om die relaties te doorlopen. Tot slot kon u erop wijzen dat een middel een andere middel vervangt alhoewel de twee middelen volledig verschillend zijn. In dat geval zou u een relatietype buiten de gereserveerde waaier kunnen bepalen en een verhouding tussen die twee middelen tot stand brengen. Uw toepassing zou de enige cliënt zijn die de verhouding kon ontdekken en verwerken, en het zou kunnen worden gebruikt om onderzoeken op die verhouding te voeren.

U kunt via programmacode relaties tussen bronnen opgeven met de Java API of webservice van de Repository-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-6}

Voer de volgende stappen uit om een relatie tussen twee bronnen op te geven:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Geef de URI&#39;s op van de bronnen die moeten worden gerelateerd.
1. Maak de relatie.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer de de dienstcliënt**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**specificeer URIs van de te verwant middelen**

Maak tekenreeksen die de URI&#39;s bevatten van de bron die moet worden gerelateerd. De syntaxis omvat voorwaartse schuine strepen, zoals in dit voorbeeld: &quot;/*weg*/ *middel*&quot;.

**creeer de verhouding**

Roep de servicemethode voor gegevensopslagruimte aan om het type relatie te maken en op te geven.

**zie ook**

[Relatiebronnen maken met de Java API](aem-forms-repository.md#create-relationship-resources-using-the-java-api)

[Relatiebronnen maken met de webservice-API](aem-forms-repository.md#create-relationship-resources-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Relatiebronnen maken met de Java API {#create-relationship-resources-using-the-java-api}

Relatiebronnen maken met de Java API van de Repository-service: voer de volgende taken uit:

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. De URI&#39;s opgeven van de bronnen die moeten worden gekoppeld

   Geef de URI&#39;s op van de bronnen die moeten worden gerelateerd. In dit geval zijn de URI&#39;s `"/testFolder/testResource1"` en `"/testFolder/testResource2"` omdat de bronnen de naam `testResource1` en `testResource2` hebben en zich in de map met de naam `testFolder` bevinden. De URI&#39;s worden opgeslagen als een `java.lang.String` -object. In dit voorbeeld worden de bronnen eerst naar de opslagplaats geschreven en worden hun URI&#39;s opgehaald. Voor meer informatie over het schrijven van een middel, zie [ het Schrijven Middelen ](aem-forms-repository.md#writing-resources).

1. De relatie maken

   Roep de methode `createRelationship` van het object `ResourceRepositoryClient` aan en geef de volgende parameters door:

   * De URI van de bronbron.
   * De URI van de doelbron.
   * Het type relatie, een van de statische constanten in de `com.adobe.repository.infomodel.bean.Relation` -klasse. In dit voorbeeld wordt een afhankelijkheidsrelatie bepaald door de waarde `Relation.TYPE_DEPENDANT_OF` op te geven.
   * Een `boolean` -waarde die aangeeft of de doelbron automatisch wordt bijgewerkt naar de op `com.adobe.repository.infomodel.Id` gebaseerde id van de nieuwe hoofdbron. In dit voorbeeld wordt vanwege de afhankelijkheidsrelatie de waarde `true` opgegeven.

   U kunt ook een lijst met verwante bronnen voor een bepaalde bron ophalen door de methode `getRelated` van het object `ResourceRepositoryClient` aan te roepen en de volgende parameters door te geven:

   * De URI van de bron waarvoor gerelateerde bronnen moeten worden opgehaald. In dit voorbeeld wordt de bronbron ( `"/testFolder/testResource1"`) opgegeven.
   * Een `boolean` -waarde die aangeeft of de opgegeven bron de bronbron in de relatie is. In dit voorbeeld wordt de waarde `true` opgegeven, omdat dit het geval is.
   * Het relatietype, dat een van de statische constanten in de `Relation` -klasse is. In dit voorbeeld wordt een afhankelijkheidsrelatie opgegeven met dezelfde waarde die u eerder hebt gebruikt: `Relation.TYPE_DEPENDANT_OF` .

   De methode `getRelated` retourneert een `java.util.List` van `Resource` -object waarmee u kunt herhalen om alle gerelateerde bronnen op te halen, waarbij de objecten in de `List` naar `Resource` worden gecast terwijl u dat doet. In dit voorbeeld wordt verwacht dat `testResource2` voorkomt in de lijst met geretourneerde bronnen.

**zie ook**

[Resourcerelaties maken](aem-forms-repository.md#creating-resource-relationships)

[Snel starten (SOAP modus): relaties maken tussen bronnen met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-relationships-between-resources-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Relatiebronnen maken met de webservice-API {#create-relationship-resources-using-the-web-service-api}

Relatiebronnen maken met de Repository API (webservice):

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die de Bewaarplaats WSDL verbruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. De serviceclient maken

   Gebruikend de Microsoft .NET cliëntassemblage, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de eigenschap `Credentials` ervan in met een `System.Net.NetworkCredential` -object dat de gebruikersnaam en het wachtwoord bevat.

1. De URI&#39;s opgeven van de bronnen die moeten worden gekoppeld

   Geef de URI&#39;s op van de bronnen die moeten worden gerelateerd. In dit geval zijn de URI&#39;s `"/testFolder/testResource1"` en `"/testFolder/testResource2"` omdat de bronnen de naam `testResource1` en `testResource2` hebben en zich in de map met de naam `testFolder` bevinden. Wanneer het gebruiken van een taal volgzaam met het Kader van Microsoft .NET (bijvoorbeeld, C#), worden URIs opgeslagen als a `System.String` voorwerpen. In dit voorbeeld worden de bronnen eerst naar de opslagplaats geschreven en worden hun URI&#39;s opgehaald. Voor meer informatie over het schrijven van een middel, zie [ het Schrijven Middelen ](aem-forms-repository.md#writing-resources).

1. De relatie maken

   Roep de methode `createRelationship` van het object `RepositoryServiceService` aan en geef de volgende parameters door:

   * De URI van de bronbron.
   * De URI van de doelbron.
   * Het type relatie. In dit voorbeeld wordt een afhankelijkheidsrelatie bepaald door de waarde `3` op te geven.
   * Een `boolean` -waarde die aangeeft of het relatietype is opgegeven. In dit voorbeeld wordt de waarde `true` opgegeven.
   * Een `boolean` -waarde die aangeeft of de doelbron automatisch wordt bijgewerkt naar de op `Id` gebaseerde id van de nieuwe hoofdbron. In dit voorbeeld wordt vanwege de afhankelijkheidsrelatie de waarde `true` opgegeven.
   * Een `boolean` -waarde die aangeeft of de doelkop is opgegeven. In dit voorbeeld wordt de waarde `true` opgegeven.
   * Geef `null` door voor de laatste parameter.

   U kunt ook een lijst met verwante bronnen voor een bepaalde bron ophalen door de methode `getRelated` van het object `RepositoryServiceService` aan te roepen en de volgende parameters door te geven:

   * De URI van de bron waarvoor gerelateerde bronnen moeten worden opgehaald. In dit voorbeeld wordt de bronbron ( `"/testFolder/testResource1"`) opgegeven.
   * Een `boolean` -waarde die aangeeft of de opgegeven bron de bronbron in de relatie is. In dit voorbeeld wordt de waarde `true` opgegeven, omdat dit het geval is.
   * Een `boolean` -waarde die aangeeft of de bronbron is opgegeven. In dit voorbeeld wordt de waarde `true` opgegeven.
   * Een array van gehele getallen die de relatietypen bevatten. In dit voorbeeld wordt een afhankelijkheidsrelatie opgegeven door dezelfde waarde in de array te gebruiken als eerder werd gebruikt: `3` .
   * Geef `null` door voor de resterende twee parameters.

   De methode `getRelated` retourneert een array met objecten die naar `Resource` -objecten kunnen worden gecast, waarmee u kunt herhalen om elk van de gerelateerde bronnen op te halen. In dit voorbeeld wordt verwacht dat `testResource2` voorkomt in de lijst met geretourneerde bronnen.

**zie ook**

[Resourcerelaties maken](aem-forms-repository.md#creating-resource-relationships)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Bronnen vergrendelen {#locking-resources}

U kunt een bron of reeks bronnen vergrendelen voor exclusief gebruik door een bepaalde gebruiker of voor gedeeld gebruik door meerdere gebruikers. Een gedeelde vergrendeling is een indicatie dat er iets met de bron zal gebeuren, maar het belet niemand anders om acties met die bron te ondernemen. Een gedeeld slot zou als signalerend mechanisme moeten worden beschouwd. Een exclusief slot betekent dat de gebruiker die het middel sloot de middel zal veranderen, en het slot zorgt ervoor dat niemand anders dit kan doen tot de gebruiker niet meer toegang tot het middel nodig heeft en het slot heeft vrijgegeven. Als een bewaarnemerbeheerder een middel ontgrendelt, zullen alle exclusieve en gedeelde sloten op dat middel automatisch worden verwijderd. Dit type actie is bedoeld voor situaties waarin een gebruiker niet meer beschikbaar is en de bron niet heeft ontgrendeld.

Wanneer een bron is vergrendeld, wordt een vergrendelingspictogram weergegeven wanneer u het tabblad Bronnen in Workbench bekijkt, zoals in de volgende afbeelding wordt getoond.

![ lr_lr_lockrepository ](assets/lr_lr_lockrepository.png)

U kunt de toegang tot bronnen programmatisch beheren met de Java API of webservice van de Repository-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-7}

Voer de volgende stappen uit om bronnen te vergrendelen en te ontgrendelen:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Geef de URI op van de bron die moet worden vergrendeld.
1. Vergrendel de resource.
1. Haal de sloten voor de bron op.
1. De bron ontgrendelen

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer de de dienstcliënt**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**specificeer URI van het te sluiten middel**

Maak een tekenreeks met de URI van de bron die moet worden vergrendeld. De syntaxis omvat voorwaartse schuine strepen, zoals in dit voorbeeld: &quot;/*weg*/ *middel*&quot;.

**Slot het middel**

Roep de servicemethode Repository aan om de bron te vergrendelen, waarbij de URI, het type vergrendeling en de vergrendelingsdiepte worden opgegeven.

**wint de sloten voor het middel** terug

Roep de de dienstmethode van de Bewaarplaats aan om de sloten voor het middel terug te winnen, die URI specificeren.

**ontgrendel het middel**

Roep de servicemethode Repository aan om de bron te ontgrendelen en de URI op te geven.

**zie ook**

[Bronnen vergrendelen met de Java API](aem-forms-repository.md#lock-resources-using-the-java-api)

[Bronnen vergrendelen met de webservice-API](aem-forms-repository.md#lock-resources-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bronnen vergrendelen met de Java API {#lock-resources-using-the-java-api}

Bronnen vergrendelen met de API voor opslagplaats (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. De URI opgeven van de bron die moet worden vergrendeld

   Geef de URI op van de bron die moet worden vergrendeld. In dit geval is de URI `"/testFolder/testResource"` omdat de bron met de naam `testResource` zich in de map met de naam `testFolder` bevindt. De URI wordt opgeslagen als een `java.lang.String` -object.

1. De bron vergrendelen

   Roep de methode `lockResource` van het object `ResourceRepositoryClient` aan en geef de volgende parameters door:

   * De URI van de resource.
   * Het vergrendelingsbereik. In dit voorbeeld wordt het vergrendelingsbereik opgegeven als `com.adobe.repository.infomodel.bean.Lock.SCOPE_EXCLUSIVE` omdat de bron wordt vergrendeld voor exclusief gebruik.
   * De vergrendelingsdiepte. In dit voorbeeld wordt de vergrendelingsdiepte opgegeven als `Lock.DEPTH_ZERO` omdat de vergrendeling alleen van toepassing is op de specifieke bron en geen van de leden of onderliggende elementen ervan.

   >[!NOTE]
   >
   >De overbelaste versie van de methode `lockResource` die vier parameters vereist, genereert een uitzondering. Zorg ervoor dat u de methode `lockResource` gebruikt waarvoor drie parameters nodig zijn, zoals in deze analyse wordt getoond.

1. Haalt de vergrendelingen voor de bron op

   Roep de methode `getLocks` van het object `ResourceRepositoryClient` aan en geef de URI van de bron door als parameter. De methode retourneert een lijst met vergrendelingsobjecten waarmee u kunt herhalen. In dit voorbeeld worden de eigenaar, diepte en bereik van de vergrendeling voor elk object afgedrukt door respectievelijk de methoden `getOwnerUserId`, `getDepth` en `getType` van elk Lock-object aan te roepen.

1. De bron ontgrendelen

   Roep de methode `unlockResource` van het object `ResourceRepositoryClient` aan en geef de URI van de bron door als parameter. Voor meer informatie, zie de [ AEM Forms API Verwijzing ](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**zie ook**

[Bronnen vergrendelen](aem-forms-repository.md#locking-resources)

[Snel starten (SOAP modus): Een bron vergrendelen met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-locking-a-resource-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bronnen vergrendelen met de webservice-API {#lock-resources-using-the-web-service-api}

Bronnen vergrendelen met behulp van de Repository Service API (webservice):

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die de Bewaarplaats WSDL gebruikend Base64 gebruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. De serviceclient maken

   Gebruikend de Microsoft .NET cliëntassemblage, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de eigenschap `Credentials` ervan in met een `System.Net.NetworkCredential` -object dat de gebruikersnaam en het wachtwoord bevat.

1. De URI opgeven van de bron die moet worden vergrendeld

   Geef een tekenreeks op die de URI bevat van de bron die moet worden vergrendeld. In dit geval is de URI `"/testFolder/testResource"` omdat de bron met de naam `testResource` zich in de map `testFolder` bevindt. Wanneer het gebruiken van een taal volgzaam met het Kader van Microsoft .NET (bijvoorbeeld, C#), bewaar URI in een `System.String` voorwerp.

1. De bron vergrendelen

   Roep de methode `lockResource` van het object `RepositoryServiceService` aan en geef de volgende parameters door:

   * De URI van de resource.
   * Het vergrendelingsbereik. In dit voorbeeld wordt het vergrendelingsbereik opgegeven als `11` omdat de bron wordt vergrendeld voor exclusief gebruik.
   * De vergrendelingsdiepte. In dit voorbeeld wordt de vergrendelingsdiepte opgegeven als `2` omdat de vergrendeling alleen van toepassing is op de specifieke bron en geen van de leden of onderliggende elementen ervan.
   * Een `int` -waarde die het aantal seconden aangeeft tot de vergrendeling vervalt. In dit voorbeeld wordt de waarde van `1000` gebruikt.
   * Geef `null` door voor de laatste parameter.

1. Haalt de vergrendelingen voor de bron op

   Roep de methode `getLocks` van het object `RepositoryServiceService` aan en geef de URI van de bron door als de eerste parameter en `null` voor de tweede parameter. De methode retourneert een `object` -array die `Lock` -objecten bevat waardoor u kunt herhalen. In dit voorbeeld worden de eigenaar van de vergrendeling, de diepte en het bereik voor elk object afgedrukt door respectievelijk de velden `ownerUserId` , `depth` en `type` van elk object te openen.`Lock`

1. De bron ontgrendelen

   Roep de methode `unlockResource` van het object `RepositoryServiceService` aan en geef de URI van de bron door als de eerste parameter en `null` voor de tweede parameter.

**zie ook**

[Bronnen vergrendelen](aem-forms-repository.md#locking-resources)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Bronnen verwijderen {#deleting-resources}

U kunt bronnen programmatisch verwijderen van een bepaalde locatie in de opslagplaats met de Java API(SOAP) van de Repository-service.

Wanneer u een middel schrapt, is de schrapping normaal permanent, hoewel in sommige gevallen ECM bewaart bewaarplaatsen de versies van het middel volgens hun geschiedenismechanismen. Daarom wanneer het schrappen van een middel, is het belangrijk om zeker te zijn dat u nooit die middel opnieuw zult nodig hebben. De gemeenschappelijke redenen om een middel te schrappen omvatten de behoefte om de beschikbare ruimte in het gegevensbestand te verhogen. U kunt een versie van een bron verwijderen, maar als u dat doet, moet u de resource-id opgeven en niet de logische id (LID) of het pad. Als u een map verwijdert, worden alle gegevens in die map, inclusief de submappen en bronnen, automatisch verwijderd.

Gerelateerde bronnen worden niet verwijderd. Als u bijvoorbeeld een formulier hebt waarin het bestand logo.gif wordt gebruikt en u logo.gif verwijdert, wordt een relatie opgeslagen in de relatietabel die in behandeling is. Als alternatief kunt u voor versiedrukking de objectstatus van de meest recente versie instellen op afgekeurd.

Een schrappingsverrichting is niet transactie-veilig in systemen ECM. Als u bijvoorbeeld probeert 100 bronnen te verwijderen en de bewerking op de 50e bron mislukt, worden de eerste 49 instanties verwijderd, maar de rest niet. Anders, is het standaardgedrag terugschroeven (niet-verplichting).

>[!NOTE]
>
>Wanneer u de methode `com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient.deleteResources()` gebruikt met ECM-opslagplaats (EMC Documentum Content Server en IBM FileNet P8 Content Manager), wordt de transactie niet teruggedraaid als de verwijdering mislukt voor een van de opgegeven bronnen, wat betekent dat bestanden die zijn verwijderd, niet kunnen worden verwijderd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-8}

Ga als volgt te werk om een bron te verwijderen:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Geef de URI op van de bron die moet worden verwijderd.
1. Verwijder de bron.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**creeer de de dienstcliënt**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**specificeer URI van het te schrappen middel**

Maak een tekenreeks met de URI van de bron die moet worden verwijderd. De syntaxis omvat voorwaartse schuine strepen, zoals in dit voorbeeld: &quot;/*weg*/ *middel*&quot;. Als de te schrappen bron een omslag is, zal de schrapping recursief zijn.

**Schrap het middel**

Roep de servicemethode Repository aan om de bron te verwijderen en de URI op te geven.

**zie ook**

[Bronnen verwijderen met de Java API](aem-forms-repository.md#delete-resources-using-the-java-api-soap)

[Bronnen verwijderen met de webservice-API](aem-forms-repository.md#delete-resources-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bronnen verwijderen met de Java API(SOAP) {#delete-resources-using-the-java-api-soap}

Verwijder een bron met de Repository API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. De URI opgeven van de bron die moet worden verwijderd

   Geef de URI op van de bron die moet worden opgehaald. In dit geval is de URI van de bron met de naam testResourceToBeDelette in de map met de naam testFolder `/testFolder/testResourceToBeDeleted` . De URI wordt opgeslagen als een `java.lang.String` -object. In dit voorbeeld wordt de bron eerst naar de opslagplaats geschreven en wordt de URI ervan opgehaald. Voor meer informatie over het schrijven van een middel, zie [ het Schrijven Middelen ](aem-forms-repository.md#writing-resources).

1. De bron verwijderen

   Roep de methode `deleteResource` van het object `ResourceRepositoryClient` aan en geef de URI van de bron door als parameter.

**zie ook**

[Bronnen verwijderen](aem-forms-repository.md#deleting-resources)

[Snel starten (SOAP modus): zoeken naar bronnen met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bronnen verwijderen met de webservice-API {#delete-resources-using-the-web-service-api}

Verwijder een bron met de Repository API (webservice):

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die de Bewaarplaats WSDL gebruikend Base64 gebruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. De serviceclient maken

   Gebruikend de Microsoft .NET cliëntassemblage, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de eigenschap `Credentials` ervan in met een `System.Net.NetworkCredential` -object dat de gebruikersnaam en het wachtwoord bevat.

1. De URI opgeven van de bron die moet worden verwijderd

   Geef de URI op van de bron die moet worden opgehaald. In dit geval is de URI `"/testFolder/testResourceToBeDeleted"` omdat de bron met de naam `testResourceToBeDeleted` zich in de map met de naam `testFolder` bevindt. In dit voorbeeld wordt de bron eerst naar de opslagplaats geschreven en wordt de URI ervan opgehaald. Voor meer informatie over het schrijven van een middel, zie [ het Schrijven Middelen ](aem-forms-repository.md#writing-resources).

1. De bron verwijderen

   Roep de methode `deleteResources` van het object `RepositoryServiceService` aan en geef een array `System.String` met de URI van de bron door als eerste parameter. Geef `null` door voor de tweede parameter.

**zie ook**

[Bronnen verwijderen](aem-forms-repository.md#deleting-resources)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
