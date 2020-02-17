---
title: Werken met AEM Forms Repository
seo-title: Werken met AEM Forms Repository
description: 'null'
seo-description: 'null'
uuid: 6ead49f9-ca0d-4ee4-86a6-0a9ced6ec4f8
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: d2c95881-6c02-4e34-85af-84607df54287
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Werken met AEM Forms Repository {#working-with-aem-forms-repository}

**Over de Repository Service**

De dienst van de Bewaarplaats verleent de opslag van middelen en beheersdiensten aan Vormen AEM. Wanneer ontwikkelaars een *AEM Forms* -toepassing maken, kunnen ze de middelen in de opslagplaats implementeren in plaats van in het bestandssysteem. De elementen kunnen elk type element bevatten, zoals XML-formulieren, PDF-formulieren (inclusief Acrobat-formulieren), formulierfragmenten, afbeeldingen, profielen, beleid, SWF-bestanden, DDX-bestanden, XML-schema&#39;s, WSDL-bestanden en testgegevens.

Neem bijvoorbeeld de volgende Forms-toepassing met de naam *Applications/FormsApplication*:

![ww_ww_formrepository](assets/ww_ww_formrepository.png)

Er bevindt zich een bestand met de naam Loan.xdp in de FormsFolder. Als u dit formulierontwerp wilt openen, geeft u het volledige pad op (inclusief versie): `Applications/FormsApplication/1.0/FormsFolder/Loan.xdp`.

>[!NOTE]
>
>Zie [Workbench Help](https://www.adobe.com/go/learn_aemforms_workbench_63)voor informatie over het maken van een Forms-toepassing met Workbench.

Het pad naar een bron in de AEM Forms-opslagplaats is:

`Applications/Application-name/Application-version/Folder.../Filename`

De volgende waarden tonen enkele voorbeelden van URI-waarden:

* Applications/AppraisalReport/1.0/Forms/FullForm.xdp
* Applications/AnotherApp/1.1/Assets/picture.jpg
* Applications/SomeApp/2.0/Resources/Data/XSDs/MyData.xsd

>[!NOTE]
>
>U kunt in de AEM Forms Repository door een webbrowser bladeren. Als u in de opslagplaats wilt bladeren, voert u de volgende URL in in een webbrowser https://[servernaam]:[serverpoort]/opslagplaats. U kunt via een webbrowser controleren welke snelstartresultaten worden gekoppeld aan de sectie Werken met AEM Forms Repository. Als u bijvoorbeeld inhoud toevoegt aan de AEM Forms Repository, kunt u de inhoud zien in een webbrowser. (Zie [Snel starten (SOAP-modus): Een bron schrijven met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api).)

De API van de dataopslag biedt een aantal bewerkingen die u kunt gebruiken om gegevens op te slaan en op te halen uit de dataopslag. Bijvoorbeeld, kunt u een lijst van middelen verkrijgen of specifieke middelen terugwinnen die in de bewaarplaats worden opgeslagen wanneer een middel als deel van de verwerking van een toepassing nodig is.

>[!NOTE]
>
>De API van de dataopslag kan niet worden gebruikt om met de (afgekeurde) Diensten van de Inhoud in wisselwerking te staan. Als u wilt werken met Content Services (afgekeurd), gebruikt u de API voor documentbeheer.

Met de Repository-service-API kunt u de volgende taken uitvoeren:

* Maak mappen. Zie Mappen [maken](aem-forms-repository.md#creating-folders).
* Bronnen en hun eigenschappen schrijven. Zie [wegschrijven van bronnen](aem-forms-repository.md#writing-resources).
* De middelen van de lijst in een bepaalde inzameling of verwant met andere middelen. Zie [Verkoopbronnen](aem-forms-repository.md#listing-resources).
* Bronnen en hun eigenschappen lezen. Zie Bronnen [lezen](aem-forms-repository.md#reading-resources).
* Bronnen en hun eigenschappen bijwerken. Zie Bronnen [bijwerken](aem-forms-repository.md#updating-resources).
* Zoeken naar bronnen, waaronder hun geschiedenis, gerelateerde bronnen en eigenschappen. Zie [Zoeken naar bronnen](aem-forms-repository.md#searching-for-resources).
* Geef relaties tussen bronnen op. Zie [Resourcerelaties](aem-forms-repository.md#creating-resource-relationships)maken.
* Beheer middeltoegangsbeheer, met inbegrip van het sluiten en het ontgrendelen van middelen, en het lezen en het schrijven toegangsbeheerlijsten (ACLs). Zie Bronnen [vergrendelen](aem-forms-repository.md#locking-resources).
* Bronnen en hun eigenschappen verwijderen. Zie [Bronnen](aem-forms-repository.md#deleting-resources)verwijderen.

>[!NOTE]
>
>Met behulp van de API van de dataopslag kunt u het beheer van de resourcetoegang niet beheren, kunt u niet zoeken naar bronnen en kunt u geen relaties met bronnen opgeven met behulp van een ECM-opslagplaats.

>[!NOTE]
>
>Wanneer een gecodeerde PDF naar de opslagplaats wordt geschreven, kan de functie voor automatische relatie-extractie niet worden gebruikt. Anders kan een gecodeerde PDF worden opgeslagen in de opslagplaats en later worden opgehaald. De opzoeker kan ervoor kiezen de PDF te decoderen nadat deze uit de opslagplaats is opgehaald.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

## Mappen maken {#creating-folders}

De omslagen (middelinzamelingen) worden gebruikt om voorwerpen (dossiers of middelen) in georganiseerde groepen op te slaan. Mappen kunnen bronnen en andere mappen bevatten, ook wel submappen genoemd. Bronnen kunnen slechts in één map tegelijk worden opgeslagen.

De dossiers erven toegangsbeheerlijsten (ACLs) van omslagen, en subfolders erven ACLs van hun ouderomslagen. Daarom moeten de bovenliggende mappen bestaan voordat u onderliggende mappen kunt maken. IDE laat u slechts op een omslag-door-omslag basis, niet op een dossier-door-dossier basis communiceren. U kunt geen mappen versieren en dit hoeft niet te gebeuren; een map bevat geen gegevens zelf. In plaats daarvan is het alleen een container voor bronnen die gegevens bevatten. Standaard ACL is systeem-vlakke toestemming, zo betekent het dat de gebruikers systeemvlakke toestemmingen (lees, schrijf, traverse, het leiden ACLs) moeten hebben tot iemand hen toestemmingen voor een bepaalde omslag geeft. ACLs werkt slechts in winde.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary-of-steps}

Ga als volgt te werk om een map te maken:

1. Inclusief projectbestanden.
1. Maak de serviceclient.
1. Maak de map.
1. Schrijf de map naar de opslagplaats.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**De serviceclient maken**

Alvorens u een middelinzameling programmatically kunt tot stand brengen, moet u een verbinding vestigen en geloofsbrieven verstrekken. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**De map maken**

Roep de servicemethode voor opslagplaats aan om de bronverzameling te maken en de bronverzameling te vullen met identificerende informatie, zoals de UUID, mapnaam en beschrijving van de verzameling.

**De map naar de opslagplaats schrijven**

Roep de servicemethode Repository aan om de bronverzameling te schrijven en de URI van de doelmap op te geven.

**Zie ook**

[Mappen maken met de Java API](aem-forms-repository.md#create-folders-using-the-java-api)

[Mappen maken met de webservice-API](aem-forms-repository.md#create-folders-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Mappen maken met de Java API {#create-folders-using-the-java-api}

Een map maken met de API voor opslagplaats (Java):

1. Projectbestanden opnemen

   Neem projectbestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. De map maken

   Als u een bronverzameling wilt maken, moet u eerst een `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean` object maken.

   Roep de `repositoryInfomodelFactoryBean` methode van het `newResourceCollection` object aan en geef de volgende parameters door:

   * A `com.adobe.repository.infomodel.Id` UID identifier to be assigned to the resource.
   * A `com.adobe.repository.infomodel.Lid` UID identifier to be assigned to the resource.
   * A `java.lang.String` containing the name of the resource collection. Bijvoorbeeld, `FormsFolder`.
   De methode retourneert een `com.adobe.repository.infomodel.bean.ResourceCollection` object dat de nieuwe map vertegenwoordigt.

   Stel de beschrijving van de map in met de `setDescription` methode en geef de volgende parameter door:

   * A `String` dat de middelinzameling beschrijft. In dit voorbeeld wordt `"test Folder"` gebruikt `.`


1. De map naar de opslagplaats schrijven

   Roep de `ResourceRepositoryClient` methode van het `writeResource` object aan en geef de URI van de map en het `ResourceCollection` object door. De URI naar de map kan bijvoorbeeld de volgende waarde zijn `/Applications/FormsApplication/1.0/`.

   De methode retourneert een instantie van het nieuwe `com.adobe.repository.infomodel.bean.Resource` object. U kunt bijvoorbeeld de id-waarde van de nieuwe bron ophalen door de `com.adobe.repository.infomodel.bean.Resource` methode van het `getId` object aan te roepen.

**Zie ook**

[Mappen maken](aem-forms-repository.md#creating-folders)

[Snel starten (SOAP-modus): Een map maken met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-a-folder-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Mappen maken met de webservice-API {#create-folders-using-the-web-service-api}

Een map maken met de Repository Service API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die de Bewaarplaats WSDL gebruikend base64 gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. De serviceclient maken

   Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de `Credentials` eigenschap in met een `System.Net.NetworkCredential` object dat de gebruikersnaam en het wachtwoord bevat.

1. De map maken

   Maak de map met de standaardconstructor voor de `ResourceCollection` klasse en geef de volgende parameters door:

   * Een `Id` object dat wordt gemaakt door de standaardconstructor voor de `Id` klasse aan te roepen en toegewezen aan het `Resource` veld van het `id` object.
   * Een `Lid` object dat wordt gemaakt door de standaardconstructor voor de `Lid` klasse aan te roepen en toegewezen aan het `Resource` veld van het `lid` object.
   * Een tekenreeks met de naam van de bronverzameling die wordt toegewezen aan het `Resource` veld van het `name` object. De naam die in dit voorbeeld wordt gebruikt, is `"testfolder"`.
   * Een tekenreeks die de beschrijving bevat van de bronverzameling, die wordt toegewezen aan het `Resource` veld van het `description` object. De beschrijving die in dit voorbeeld wordt gebruikt, is `"test folder"`.

1. De map naar de opslagplaats schrijven

   Roep de methode van het `RepositoryServiceService` `writeResource` object aan en geef de volgende parameters door:

   * Het pad waar de map moet worden gemaakt.
   * Het `ResourceCollection` object dat de map vertegenwoordigt.
   * Geef `null` de andere twee parameters door.

**Zie ook**

[Mappen maken](aem-forms-repository.md#creating-folders)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Bronnen schrijven {#writing-resources}

U kunt bronnen maken op een bepaalde locatie in de opslagplaats. De natuurlijke dossiergrootte is onderworpen aan gegevensbestandbeperkingen en zittingsonderbreking. Voor de standaardconfiguratie, zijn de dossiers beperkt tot 25 MB. Als u de maximale bestandsgrootte wilt verhogen of verlagen, moet u de databaseconfiguratie wijzigen.

Het schrijven van bronnen is gelijk aan het opslaan van gegevens in de opslagplaats. Zodra u een middel aan de bewaarplaats schrijft, wordt het toegankelijk voor alle cliënten in het bewaarplaats ecosysteem. Wanneer u bronnen naar de opslagplaats schrijft, zoals XML-schema&#39;s, XDP-bestanden en XSD-bestanden, wordt de inhoud geparseerd op basis van het MIME-type. Als het MIME-type wordt ondersteund, bepaalt de parser of er een impliciete relatie met andere inhoud is. Als een CSS (Cascading Style Sheet) bijvoorbeeld een relatieve URL heeft die verwijst naar een gemeenschappelijke CSS, wordt verwacht dat u de gemeenschappelijke CSS ook in de opslagplaats zult verzenden. De relatie tussen de twee bronnen wordt gedurende een niet-aanpasbare periode van 30 dagen opgeslagen als een hangende relatie. Wanneer u de algemene CSS binnen de periode van 30 dagen naar de opslagplaats verzendt, wordt de relatie gevormd.

Wanneer u een middel creeert, wordt de toegangsbeheerlijst (ACL) geërft van de ouderomslag. De wortelomslag heeft systeem-vlakke toestemmingen tot een eerste middel of een omslag wordt gecreeerd, waarbij het middel of de omslag standaardACL toestemmingen wordt gegeven.

U kunt bronnen programmatisch schrijven met de Java API of webservice van de Repository-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een resource te schrijven:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Geef de URI op van de bron die moet worden gelezen.
1. Lees de bron.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**De serviceclient maken**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**De URI van de doelmap voor de bron opgeven**

Maak een tekenreeks met de URI van de bron die moet worden gelezen. De syntaxis bevat slashes, zoals in dit voorbeeld: &quot;/*path*/*folder*&quot;.

**De bron maken**

Roep de servicemethode voor opslagplaats aan om de bron te maken en de bron te vullen met identificerende informatie, waaronder de UUID, de naam van de bron en een beschrijving.

**De inhoud van de bron opgeven**

Roep de de dienstmethode van de Bewaarplaats aan om middelinhoud tot stand te brengen, en die inhoud in het middel op te slaan.

**De bron naar de doelmap schrijven**

Roep de servicemethode Repository aan om de bron te schrijven en de URI van de doelmap op te geven.

**Zie ook**

[Bronnen schrijven met de Java API](aem-forms-repository.md#write-resources-using-the-java-api)

[Bronnen schrijven met de webservice-API](aem-forms-repository.md#write-resources-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bronnen schrijven met de Java API {#write-resources-using-the-java-api}

Schrijf een bron met behulp van de Repository Service API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. De URI van de doelmap voor de bron opgeven

   Geef de URI van de doelmap voor de bron op. In dit geval is de URI van de map omdat de benoemde bron `testResource` wordt opgeslagen in de map `testFolder`met de naam `"/testFolder"`. De URI wordt opgeslagen als een `java.lang.String` object.

1. De bron maken

   Als u een bron wilt maken, moet u eerst een `com.adobe.repository.infomodel.bean.RepositoryInfomodelFactoryBean` object maken.

   Roep de `RepositoryInfomodelFactoryBean` methode van het `newResource` object aan, waarmee een `com.adobe.repository.infomodel.bean.Resource` object wordt gemaakt. In dit voorbeeld worden de volgende parameters opgegeven:

   * Een `com.adobe.repository.infomodel.Id` object dat wordt gemaakt door de standaardconstructor voor de `Id` klasse aan te roepen.
   * Een `com.adobe.repository.infomodel.Lid` object dat wordt gemaakt door de standaardconstructor voor de `Lid` klasse aan te roepen.
   * A `java.lang.String` containing the file name of the resource.
   Als u de beschrijving van de bron wilt opgeven, roept u de methode van het `Resource` `setDescription` object aan en geeft u een tekenreeks met de beschrijving door. In dit voorbeeld is de beschrijving `"test resource"`.

1. De inhoud van de bron opgeven

   Als u inhoud voor de bron wilt maken, roept u de `RepositoryInfomodelFactoryBean` methode van het object aan, die een `newResourceContent` `com.adobe.repository.infomodel.bean.ResourceContent` object retourneert. Voeg inhoud toe aan het `ResourceContent` object. In dit voorbeeld worden de volgende taken uitgevoerd:

   * De methode van het `ResourceContent` object aanroepen en een `setDataDocument` `com.adobe.idp.Document` object doorgeven
   * De methode van het `ResourceContent` object aanroepen en de grootte van het `setSize` `Document` object in bytes doorgeven
   Voeg de inhoud aan de bron toe door de methode van het `Resource` object aan te roepen `setContent` en het `ResourceContent` object door te geven. Zie [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)voor meer informatie.

1. De bron naar de doelmap schrijven

   Roep de `ResourceRepositoryClient` methode van het `writeResource` object aan en geef de URI van de map en het `Resource` object door.

**Zie ook**

[Bronnen schrijven](aem-forms-repository.md#writing-resources)

[Snel starten (SOAP-modus): Een bron schrijven met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bronnen schrijven met de webservice-API {#write-resources-using-the-web-service-api}

Schrijf een bron met behulp van de Repository Service API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die de Bewaarplaats WSDL gebruikend base64 gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. De serviceclient maken

   Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de `Credentials` eigenschap in met een `System.Net.NetworkCredential` object dat de gebruikersnaam en het wachtwoord bevat.

1. De URI van de doelmap voor de bron opgeven

   Geef de URI van de doelmap voor de bron op. In dit geval is de URI van de map omdat de benoemde bron `testResource` wordt opgeslagen in de map `testFolder`met de naam `"/testFolder"`. Wanneer het gebruiken van een taal volgzaam met het Kader van Microsoft .NET (bijvoorbeeld, C#), sla URI in een `System.String` voorwerp op.

1. De bron maken

   Als u een bron wilt maken, roept u de standaardconstructor voor de `Resource` klasse aan. In dit voorbeeld wordt de volgende informatie in het `Resource` object opgeslagen:

   * Een `com.adobe.repository.infomodel.Id` object dat wordt gemaakt door de standaardconstructor voor de `Id` klasse aan te roepen en toegewezen aan het `Resource` veld van het `id` object.
   * Een `com.adobe.repository.infomodel.Lid` object dat wordt gemaakt door de standaardconstructor voor de `Lid` klasse aan te roepen en toegewezen aan het `Resource` veld van het `lid` object.
   * Een tekenreeks die de bestandsnaam van de bron bevat, die wordt toegewezen aan het `Resource` veld van het `name` object. De naam die in dit voorbeeld wordt gebruikt, is `"testResource"`.
   * Een tekenreeks die de beschrijving bevat van de bron, die wordt toegewezen aan het `Resource` veld van het `description` object. De beschrijving die in dit voorbeeld wordt gebruikt, is `"test resource"`.

1. De inhoud van de bron opgeven

   Als u inhoud voor de bron wilt maken, roept u de standaardconstructor voor de `ResourceContent` klasse aan. Voeg vervolgens inhoud aan het `ResourceContent` object toe. In dit voorbeeld worden de volgende taken uitgevoerd:

   * Een `BLOB` object met een document toewijzen aan het `ResourceContent` veld van het `dataDocument` object.
   * De grootte van het `BLOB` object in bytes toewijzen aan het `ResourceContent` veld van het `size` object.
   Voeg de inhoud aan de bron toe door het `ResourceContent` object toe te wijzen aan het `Resource` veld van het `content` object.

1. De bron naar de doelmap schrijven

   Roep de `RepositoryServiceService` methode van het `writeResource` object aan en geef de URI van de map en het `Resource` object door. Geef `null` de andere twee parameters door.

**Zie ook**

[Bronnen schrijven](aem-forms-repository.md#writing-resources)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Aanbiedingsbronnen {#listing-resources}

Je kunt bronnen vinden door bronnen aan te bieden. Een vraag wordt uitgevoerd tegen de bewaarplaats om alle middelen te vinden die met een bepaalde middelinzameling verwant zijn.

Zodra u uw middelen organiseert, kunt u de structuur inspecteren u door een bepaalde tak van de structuur te zien creeerde, veel als u in een werkend systeem zou doen.

Bronnen voor lijsten werken op basis van relatie: bronnen zijn leden van mappen. Lidmaatschap wordt vertegenwoordigd door een relatie van het type &quot;lid van&quot;. Wanneer u bronnen in een bepaalde map opsomt, zoekt u naar bronnen die verwant zijn aan een bepaalde map door de relatie &quot;lid van&quot;. Relaties zijn gericht: een lid van een verhouding heeft een bron die een lid van het doel is. De bron is de bron; het doel is de bovenliggende map.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om bronnen weer te geven:

1. Inclusief projectbestanden.
1. Maak de serviceclient.
1. Geef het mappad op.
1. Haal de lijst met bronnen op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**De serviceclient maken**

Alvorens u een middelinzameling programmatically kunt tot stand brengen, moet u een verbinding vestigen en geloofsbrieven verstrekken. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**Het mappad opgeven**

Maak een tekenreeks met het pad van de map met de bronnen. De syntaxis bevat slashes, zoals in dit voorbeeld: &quot;/*path*/*folder*&quot;.

**De lijst met bronnen ophalen**

Roep de servicemethode voor gegevensopslagruimte aan om de lijst met bronnen op te halen en geef het pad van de doelmap op.

**Zie ook**

[Bronnen weergeven met de Java API](aem-forms-repository.md#list-resources-using-the-java-api)

[Bronnen weergeven met de webservice-API](aem-forms-repository.md#list-resources-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bronnen weergeven met de Java API {#list-resources-using-the-java-api}

Bronnen weergeven met behulp van de Repository Service API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. Het mappad opgeven

   Geef de URI op van de bronverzameling die moet worden opgevraagd. In dit geval is de URI `"/testFolder"`. De URI wordt opgeslagen als een `java.lang.String` object.

1. De lijst met bronnen ophalen

   Roep de `ResourceRepositoryClient` methode van het `listMembers` object aan en geef de URI van de map door.

   De methode keert een `java.util.List` van `com.adobe.repository.infomodel.bean.Resource` voorwerpen terug die de bron van een `com.adobe.repository.infomodel.bean.Relation` van type `Relation.TYPE_MEMBER_OF` zijn en de middelinzameling URI als doel hebben. U kunt dit doorlopen `List` om elk van de bronnen op te halen. In dit voorbeeld worden de naam en beschrijving van elke bron weergegeven.

**Zie ook**

[Aanbiedingsbronnen](aem-forms-repository.md#listing-resources).

[Snel starten (SOAP-modus): Bronnen weergeven met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-listing-resources-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bronnen weergeven met de webservice-API {#list-resources-using-the-web-service-api}

Bronnen weergeven met de Repository Service API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die de Bewaarplaats WSDL verbruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. De serviceclient maken

   Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de `Credentials` eigenschap in met een `System.Net.NetworkCredential` object dat de gebruikersnaam en het wachtwoord bevat.

1. Het mappad opgeven

   Geef een tekenreeks op die de URI bevat van de map waarnaar wordt gevraagd. In dit geval is de URI `"/testFolder"`. Wanneer het gebruiken van een taal die met het Kader van Microsoft .NET (bijvoorbeeld, C#) volgzaam is, sla URI in een `System.String` voorwerp op.

1. De lijst met bronnen ophalen

   Roep de `RepositoryServiceService` methode van het `listMembers` object aan en geef de URI van de map door als de eerste parameter. Geef `null` de andere twee parameters door.

   De methode retourneert een array met objecten die naar `Resource` objecten kunnen worden gecast. U kunt de objectarray doorlopen om elk van de gerelateerde bronnen op te halen. In dit voorbeeld worden de naam en beschrijving van elke bron weergegeven.

**Zie ook**

[Aanbiedingsbronnen](aem-forms-repository.md#listing-resources).

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Bronnen lezen {#reading-resources}

U kunt bronnen ophalen van een bepaalde locatie in de opslagplaats om de inhoud en metagegevens te lezen. De workflow wordt voorafgegaan door een initialisatieformulier. Het proces heeft alle machtigingen die het nodig heeft om het formulier te lezen. Het systeem haalt het gegevensformulier op en leest de inhoud uit de gegevensopslagruimte. De opslagplaats verleent toegang tot de inhoud en de meta-gegevens (de capaciteit zelfs om het middel te weten bestaat).

De repository heeft de volgende vier machtigingstypen:

* **doorlopen**: staat u toe om van middelen een lijst te maken; dat wil zeggen, bronmetagegevens lezen, maar geen broninhoud
* **lezen**: staat u toe om middelinhoud te lezen
* **schrijven**: staat u toe om middelinhoud te schrijven
* **het beheren van toegangsbeheerlijsten (ACLs)**: staat u toe om ACLs op middelen te manipuleren

Gebruikers kunnen alleen processen uitvoeren als zij gemachtigd zijn het proces uit te voeren. IDE-gebruikers hebben verplaatsings- en leesmachtigingen nodig om te synchroniseren met de repository. ACLs is slechts in ontwerptijd van toepassing omdat runtime binnen de systeemcontext voorkomt.

U kunt bronnen programmatisch lezen met de Java API of webservice van de Repository-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende stappen uit om een bron te lezen:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Geef de URI op van de bron die moet worden gelezen.
1. Lees de bron.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**De serviceclient maken**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**De URI opgeven van de bron die moet worden gelezen**

Maak een tekenreeks met de URI van de bron die moet worden gelezen. De syntaxis bevat slashes, zoals in dit voorbeeld: &quot;/*path*/*resource*&quot;.

**De bron lezen**

Roep de servicemethode Repository aan om de bron te lezen en de URI op te geven.

**Zie ook**

[Bronnen lezen met de Java API](aem-forms-repository.md#read-resources-using-the-java-api)

[Bronnen lezen met de webservice-API](aem-forms-repository.md#reading-resources-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bronnen lezen met de Java API {#read-resources-using-the-java-api}

Een bron lezen met de API voor opslagplaats (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. De URI opgeven van de bron die moet worden gelezen

   Geef een tekenreekswaarde op die de URI vertegenwoordigt van de bron die moet worden opgehaald. Bijvoorbeeld, veronderstellend wordt het middel genoemd *testResource* die in een omslag genoemd *testFolder* wordt gevestigd, specificeer `/testFolder/testResource`.

1. De bron lezen

   Roep de `ResourceRepositoryClient` methode van het `readResource` object aan en geef de URI van de bron als parameter door. Deze methode retourneert een `Resource` instantie die de bron vertegenwoordigt.

**Zie ook**

[Bronnen lezen](aem-forms-repository.md#reading-resources)

[Snel starten (SOAP-modus): Een bron lezen met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-reading-a-resource-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bronnen lezen met de webservice-API {#reading-resources-using-the-web-service-api}

Een bron lezen met de Repository Service API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die de Bewaarplaats WSDL verbruikt. (Zie het [Creëren van een .NET cliëntassemblage die Base64 het coderen](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding). gebruikt)
   * Verwijs naar de cliëntassemblage van Microsoft .NET. (Zie het [Creëren van een .NET cliëntassemblage die Base64 het coderen](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding). gebruikt)

1. De serviceclient maken

   Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de `Credentials` eigenschap in met een `System.Net.NetworkCredential` object dat de gebruikersnaam en het wachtwoord bevat.

1. De URI opgeven van de bron die moet worden gelezen

   Geef een tekenreeks op met de URI van de bron die moet worden opgehaald. In dit geval is de URI van de resource `testResource` . De genoemde `testFolder`bevindt zich in de map met de naam `"/testFolder/testResource"`. Wanneer het gebruiken van een taal volgzaam met het Kader van Microsoft .NET (bijvoorbeeld, C#), sla URI in een `System.String` voorwerp op.

1. De bron lezen

   Roep de `RepositoryServiceService` methode van het `readResource` object aan en geef de URI van de bron door als de eerste parameter. Geef `null` de andere twee parameters door.

**Zie ook**

[Bronnen lezen](aem-forms-repository.md#reading-resources)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Bronnen bijwerken {#updating-resources}

U kunt de inhoud van bronnen in de opslagplaats ophalen en bijwerken. Wanneer u middelen bijwerkt, blijft het toegangsbeheer tot die middelen onveranderd tussen versies. Wanneer u een update uitvoert, kunt u de hoofdversie verhogen. Als u er niet voor kiest de hoofdversie te verhogen, wordt de kleine versie automatisch bijgewerkt.

Wanneer u een bron bijwerkt, wordt de nieuwe versie gemaakt op basis van de opgegeven bronkenmerken. Wanneer u een bron bijwerkt, geeft u twee belangrijke parameters op: de doel-URI en een resource-instantie die alle bijgewerkte metagegevens bevatten. Het is belangrijk om op te merken dat als u een bepaald attribuut (bijvoorbeeld, de naam) niet verandert, het attribuut nog wordt vereist in de instantie u binnen overgaat. De relaties die worden gemaakt bij het parseren van de inhoud, worden toegevoegd aan de specifieke versie en worden alleen naar voren gebracht als dat is opgegeven.

Als u bijvoorbeeld een XDP-bestand bijwerkt dat verwijzingen naar andere bronnen bevat, worden deze aanvullende verwijzingen ook opgenomen. Veronderstel dat form.xdp versie 1.0 twee externe verwijzingen heeft: een logo en een stijlpagina, en u werkt vervolgens form.xdp bij zodat het nu drie verwijzingen heeft: een logo, een stijlpagina en een schemabestand. Tijdens de update voegt de dataopslag de derde relatie (aan het schemabestand) toe aan de relatietabel die in behandeling is. Zodra het schemadossier in de bewaarplaats aanwezig is, zal de verhouding automatisch worden gevormd. Als form.xdp versie 2.0 het logo echter niet meer gebruikt, heeft form.xdp versie 2.0 geen relatie met het logo.

Alle updatebewerkingen zijn atomisch en transactioneel. Als twee gebruikers bijvoorbeeld dezelfde bron lezen en beide besluiten versie 1.0 bij te werken naar versie 2.0, zal één van hen slagen en één van hen zal ontbreken, zal de integriteit van de repository worden gehandhaafd, en beide zullen een bericht krijgen dat succes of mislukking bevestigt. Als de transactie niet begaan, zal het in het geval van gegevensbestandmislukking terugdraaien en uit tijd of terugloop afhankelijk van de toepassingsserver.

U kunt bronnen programmatisch bijwerken met de Java API of webservice van de Repository-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om een bron bij te werken:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Haal de bron op die u wilt bijwerken.
1. Werk de bron bij.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**De serviceclient maken**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**De bron ophalen die moet worden bijgewerkt**

Lees de bron. Zie [Bronnen](aem-forms-repository.md#reading-resources)lezen voor meer informatie.

**De bron bijwerken**

Plaats de nieuwe informatie in het middel en haal de de dienstmethode van de Bewaarplaats aan om het middel bij te werken, specificerend URI, het bijgewerkte middel, en hoe de versieinformatie zou moeten worden bijgewerkt.

**Zie ook**

[Bronnen bijwerken met de Java API](aem-forms-repository.md#update-resources-using-the-java-api)

[Bronnen bijwerken met de webservice-API](aem-forms-repository.md#update-resources-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bronnen bijwerken met de Java API {#update-resources-using-the-java-api}

Werk een bron bij met behulp van de Repository Service API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. De bron ophalen die moet worden bijgewerkt

   Geef de URI op van de bron die u wilt ophalen en lezen. In dit voorbeeld is de URI van de bron `"/testFolder/testResource"`.

1. De bron bijwerken

   Werk de gegevens van het `Resource` object bij. In dit voorbeeld roept u de methode van het `Resource` `setDescription` object op en geeft u de nieuwe beschrijvingstekenreeks door als een parameter om de beschrijving bij te werken.

   Roep vervolgens de `ServiceClientFactory` methode van het `updateResource` object aan en geef de volgende parameters door:

   * Een `java.lang.String` object dat de URI van de bron bevat.
   * Het `Resource` object met de bijgewerkte broninformatie.
   * Een `boolean` waarde die aangeeft of de primaire of secundaire versie moet worden bijgewerkt. In dit voorbeeld `true` wordt een waarde van doorgegeven om aan te geven dat de hoofdversie moet worden verhoogd.

**Zie ook**

[Bronnen bijwerken](aem-forms-repository.md#updating-resources)

[Snel starten (SOAP-modus): Een bron bijwerken met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-updating-a-resource-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bronnen bijwerken met de webservice-API {#update-resources-using-the-web-service-api}

Een bron bijwerken met de Repository API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die de Bewaarplaats WSDL verbruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. De serviceclient maken

   Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de `Credentials` eigenschap in met een `System.Net.NetworkCredential` object dat de gebruikersnaam en het wachtwoord bevat.

1. De bron ophalen die moet worden bijgewerkt

   Geef de URI op van de bron die moet worden opgehaald en lees de bron. In dit voorbeeld is de URI van de bron `"/testFolder/testResource"`. Zie [Bronnen](aem-forms-repository.md#reading-resources)lezen voor meer informatie.

1. De bron bijwerken

   Werk de gegevens van het `Resource` object bij. Als u in dit voorbeeld de beschrijving wilt bijwerken, wijst u een nieuwe waarde toe aan het `Resource` veld van het `description` object.

1. Roep de `RepositoryServiceService` methode van het `updateResource` object aan en geef de volgende parameters door:

   * Een `System.String` object dat de URI van de bron bevat.
   * Het `Resource` object met de bijgewerkte broninformatie.
   * Een `boolean` waarde die aangeeft of de primaire of secundaire versie moet worden bijgewerkt. In dit voorbeeld `true` wordt een waarde van doorgegeven om aan te geven dat de hoofdversie moet worden verhoogd.
   * Geef `null` de resterende twee parameters door.

**Zie ook**

[Bronnen bijwerken](aem-forms-repository.md#updating-resources)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Zoeken naar bronnen {#searching-for-resources}

U kunt vragen construeren die worden gebruikt om naar middelen in de bewaarplaats, met inbegrip van geschiedenis, verwante middelen, en eigenschappen te zoeken.

U kunt gerelateerde bronnen ophalen om de afhankelijkheden tussen een formulier en de bijbehorende fragmenten te bepalen. Als u bijvoorbeeld een formulier hebt, kunt u bepalen welke fragmenten of externe bronnen het gebruikt. Als u een afbeelding hebt, kunt u ook nagaan in welke formulieren de afbeelding wordt gebruikt. U kunt ook naar gerelateerde bronnen zoeken door filteren op basis van eigenschappen. U kunt bijvoorbeeld zoeken naar alle formulieren die een afbeelding met een opgegeven naam gebruiken, of naar afbeeldingen die worden gebruikt door een formulier met een opgegeven naam. U kunt ook zoeken met eigenschappen van bronnen. U kunt bijvoorbeeld een query uitvoeren om alle formulieren of bronnen te zoeken waarvan de naam begint met een bepaalde tekenreeks die jokertekens &#39;%&#39; en &#39;_&#39; kan bevatten. Vergeet niet dat zoekopdrachten op basis van eigenschappen niet op relaties zijn gebaseerd. dergelijke onderzoeken zijn gebaseerd op de veronderstelling dat u specifieke kennis over een bepaalde middel hebt.

**Query-instructies**

Een *vraag* bevat één of meerdere verklaringen die logisch gezien met voorwaarden worden verbonden. Een *instructie* bestaat uit een linkeroperand, een operator en een rechteroperand. Bovendien kunt u de sorteervolgorde opgeven die voor de zoekresultaten moet worden gebruikt. De *sorteervolgorde* bevat informatie die gelijk is aan een SQL- `ORDER BY` component en bestaat uit elementen die de kenmerken bevatten waarop de zoekopdracht is gebaseerd, en een waarde die aangeeft of oplopende of aflopende volgorde moet worden gebruikt.

U kunt programmatically naar middelen zoeken door de dienstJava API van de Bewaarplaats te gebruiken. Op dit moment is het niet mogelijk om met de webservice-API naar bronnen te zoeken.

**Sorteergedrag**

De sorteervolgorde wordt niet gerespecteerd wanneer de methode van het `ResourceRepositoryClient` `searchProperties` object wordt aangeroepen en een sorteervolgorde wordt opgegeven. Stel bijvoorbeeld dat u een bron met drie aangepaste eigenschappen maakt, waarbij kenmerknamen `name`, `secondName`en `asecondName`. Vervolgens maakt u een sorteervolgordelement op de kenmerknaam en stelt u de `ascending` waarde in op `true`.

Vervolgens activeert u de `ResourceRepositoryClient` `searchProperties` methode van het object en geeft u de sorteervolgorde door. De zoekopdracht retourneert de juiste bron, met de drie eigenschappen. De eigenschappen worden echter niet gesorteerd op kenmerknaam. Ze worden geretourneerd in de volgorde waarin ze zijn toegevoegd: `name`, `secondName`, en `asecondName`.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

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

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**De serviceclient maken**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**De doelmap voor de zoekopdracht opgeven**

Maak een tekenreeks met het basispad waaruit de zoekopdracht moet worden uitgevoerd. De syntaxis bevat slashes, zoals in dit voorbeeld: &quot;/*path*/*folder*&quot;.

**De kenmerken opgeven die in de zoekopdracht worden gebruikt**

U kunt uw zoekopdracht baseren op de kenmerken in de bronnen. Geef de waarden op van de kenmerken waarop de zoekopdracht moet worden uitgevoerd.

**De query maken die wordt gebruikt in de zoekopdracht**

Construeer een vraag door verklaringen en voorwaarden te gebruiken. Elke instructie geeft het kenmerk op waarop de zoekopdracht moet worden gebaseerd, de voorwaarde die moet worden gebruikt en de kenmerkwaarde die in de zoekopdracht moet worden gebruikt.

**De sorteervolgorde voor de zoekresultaten maken**

De sorteervolgorde bestaat uit elementen, die elk een van de kenmerken bevatten die in de zoekopdracht worden gebruikt en een waarde die aangeeft of oplopende of aflopende volgorde moet worden gebruikt.

**Zoeken naar de bronnen**

Zoek naar de middelen gebruikend de omslag, de vraag, en de soortorde. Geef bovendien de diepte van de zoekopdracht en een bovengrens op voor het aantal resultaten dat moet worden geretourneerd.

**De bronnen ophalen uit het zoekresultaat**

Doorloop de geretourneerde lijst met bronnen en extraheer de informatie voor verdere verwerking.

**Zie ook**

[Zoeken naar bronnen met de Java API](aem-forms-repository.md#search-for-resources-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Zoeken naar bronnen met de Java API {#search-for-resources-using-the-java-api}

Zoek naar een bron met behulp van de Repository Service API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. De doelmap voor de zoekopdracht opgeven

   Geef de URI op van het basispad waaruit de zoekopdracht moet worden uitgevoerd. In dit voorbeeld is de URI van de bron `/testFolder`.

1. De kenmerken opgeven die in de zoekopdracht worden gebruikt

   Geef de waarden op voor de kenmerken waarop de zoekopdracht moet worden uitgevoerd. De kenmerken bestaan in een `com.adobe.repository.infomodel.bean.Resource` object. In dit voorbeeld wordt de zoekopdracht uitgevoerd op het kenmerk name. Daarom wordt een `java.lang.String` object met de naam van het `Resource` object gebruikt, wat in dit `testResource` geval het geval is.

1. De query maken die wordt gebruikt in de zoekopdracht

   Als u een query wilt maken, maakt u een `com.adobe.repository.query.Query` object door de standaardconstructor voor de `Query` klasse aan te roepen en voegt u instructies toe aan de query.

   Als u een instructie wilt maken, roept u de constructor voor de `com.adobe.repository.query.Query.Statement` klasse op en geeft u de volgende parameters door:

   * Een linkeroperand die de constante van het middelattribuut bevat. In dit voorbeeld wordt de statische waarde gebruikt, omdat de naam van de bron wordt gebruikt als basis voor de zoekopdracht. `Resource.ATTRIBUTE_NAME`
   * Een operator die de voorwaarde bevat die wordt gebruikt in de zoekopdracht naar het kenmerk. De operator moet een van de statische constanten in de `Query.Statement` klasse zijn. In dit voorbeeld `Query.Statement.OPERATOR_BEGINS_WITH` wordt de statische waarde gebruikt.
   * Een rechteroperand die de kenmerkwaarde bevat waarop de zoekopdracht moet worden uitgevoerd. In dit voorbeeld wordt het kenmerk name gebruikt, een `String` element met de waarde `"testResource"`.
   Geef de naamruimte van de linkeroperand op door de methode van het `Query.Statement` object aan te roepen en een van de statische waarden in de `setNamespace` `com.adobe.repository.infomodel.bean.ResourceProperty` klasse door te geven. In dit voorbeeld wordt `ResourceProperty.RESERVED_NAMESPACE_REPOSITORY` gebruikt.

   Voeg elke instructie aan de query toe door de methode van het `Query` object aan te roepen en het `addStatement` `Query.Statement` object door te geven.

1. De sorteervolgorde voor de zoekresultaten maken

   Als u de sorteervolgorde wilt opgeven die in de zoekresultaten wordt gebruikt, maakt u een `com.adobe.repository.query.sort.SortOrder` object door de standaardconstructor voor de `SortOrder` klasse aan te roepen en voegt u elementen toe aan de sorteervolgorde.

   Als u een element voor de sorteervolgorde wilt maken, roept u een van de constructors voor de `com.adobe.repository.query.sort.SortOrder.Element` klasse aan. In dit voorbeeld `Resource.ATTRIBUTE_NAME` wordt de statische waarde gebruikt als de eerste parameter en wordt de oplopende volgorde (een `boolean` waarde van `true`) opgegeven als de tweede parameter, omdat de naam van de bron wordt gebruikt als de basis voor de zoekopdracht.

   Voeg elk element aan de sorteervolgorde toe door de methode van het `SortOrder` object aan te roepen en het `addSortElement` `SortOrder.Element` object door te geven.

1. Zoeken naar de bronnen

   Als u wilt zoeken op `resources` basis van kenmerkeigenschappen, roept u de `ResourceRepositoryClient` methode van het `searchProperties` object op en geeft u de volgende parameters door:

   * A `String` containing the base path from which to execute the search. In dit geval `"/testFolder"` wordt gebruikt.
   * De query die wordt gebruikt in de zoekopdracht.
   * De diepte van de zoekopdracht. In dit geval `com.adobe.repository.infomodel.bean.ResourceCollection.DEPTH_INFINITE` wordt gebruikt om aan te geven dat het basispad en alle bijbehorende mappen moeten worden gebruikt.
   * Een `int` waarde die de eerste rij aangeeft waaruit de niet-gepagineerde resultatenset moet worden geselecteerd. In dit voorbeeld wordt `0` opgegeven.
   * Een `int` waarde die het maximale aantal resultaten aangeeft dat moet worden geretourneerd. In dit voorbeeld wordt `10` opgegeven.
   * De sorteervolgorde die in de zoekopdracht wordt gebruikt.
   De methode retourneert een `java.util.List` van de `Resource` objecten in de opgegeven sorteervolgorde.

1. De bronnen ophalen uit het zoekresultaat

   Als u de bronnen in het zoekresultaat wilt ophalen, doorloopt u het object `List` en cast u elk object naar een object `Resource` om de informatie ervan te extraheren. In dit voorbeeld wordt de naam van elke bron weergegeven.

**Zie ook**

[Zoeken naar bronnen](aem-forms-repository.md#searching-for-resources)

[Snel starten (SOAP-modus): Zoeken naar bronnen met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

## Resourcerelaties maken {#creating-resource-relationships}

U kunt relaties tussen bronnen in de opslagplaats opgeven. Er zijn drie soorten relaties:

* **Afhankelijkheid**: een relatie waarin een middel van andere middelen afhangt, betekenend dat alle verwante middelen in de bewaarplaats nodig zijn.
* **Lidmaatschap (bestandssysteem)**: een relatie waarin een bron zich in een bepaalde map bevindt.
* **Aangepast**: een relatie die u opgeeft tussen bronnen. Bijvoorbeeld, als één middel is afgekeurd en een andere middel in de bewaarplaats is geïntroduceerd, kon u uw eigen vervangingsverhouding specificeren.

U kunt uw eigen aangepaste relaties maken. Als u bijvoorbeeld een HTML-bestand opslaat in de opslagplaats en een afbeelding gebruikt, kunt u een aangepaste relatie opgeven om het HTML-bestand te koppelen aan de afbeelding (aangezien gewoonlijk alleen XML-bestanden worden gekoppeld aan afbeeldingen met behulp van een door de opslagplaats gedefinieerde afhankelijkheidsrelatie). Een ander voorbeeld van een aangepaste relatie is als u een andere weergave van de opslagplaats wilt maken met een cyclische grafiekstructuur in plaats van een boomstructuur. U kunt een cirkelvormige grafiek samen met een kijker definiëren om die relaties te doorlopen. Tot slot kon u erop wijzen dat een middel een andere middel vervangt alhoewel de twee middelen volledig verschillend zijn. In dat geval zou u een relatietype buiten de gereserveerde waaier kunnen bepalen en een verhouding tussen die twee middelen tot stand brengen. Uw toepassing zou de enige cliënt zijn die de verhouding kon ontdekken en verwerken, en het zou kunnen worden gebruikt om onderzoeken op die verhouding te voeren.

U kunt via programmacode relaties tussen bronnen opgeven met de Java API of webservice van de Repository-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary_of_steps-6}

Voer de volgende stappen uit om een relatie tussen twee bronnen op te geven:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Geef de URI&#39;s op van de bronnen die moeten worden gerelateerd.
1. Maak de relatie.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**De serviceclient maken**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**De URI&#39;s opgeven van de bronnen die moeten worden gekoppeld**

Maak tekenreeksen die de URI&#39;s bevatten van de bron die moet worden gerelateerd. De syntaxis bevat slashes, zoals in dit voorbeeld: &quot;/*path*/*resource*&quot;.

**De relatie maken**

Roep de servicemethode voor gegevensopslagruimte aan om het type relatie te maken en op te geven.

**Zie ook**

[Relatiebronnen maken met de Java API](aem-forms-repository.md#create-relationship-resources-using-the-java-api)

[Relatiebronnen maken met de webservice-API](aem-forms-repository.md#create-relationship-resources-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Relatiebronnen maken met de Java API {#create-relationship-resources-using-the-java-api}

Relatiebronnen maken met de Java API van Repository-service en de volgende taken uitvoeren:

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. De URI&#39;s opgeven van de bronnen die moeten worden gekoppeld

   Geef de URI&#39;s op van de bronnen die moeten worden gerelateerd. In dit geval, omdat de middelen genoemd en `testResource1` en in de genoemde omslag worden gevestigd `testResource2` , zijn hun URIs `testFolder`en `"/testFolder/testResource1"` `"/testFolder/testResource2"`. De URI&#39;s worden opgeslagen als `java.lang.String` objecten. In dit voorbeeld worden de bronnen eerst naar de opslagplaats geschreven en worden hun URI&#39;s opgehaald. Voor meer informatie over het schrijven van een middel, zie het [Schrijven van Middelen](aem-forms-repository.md#writing-resources).

1. De relatie maken

   Roep de methode van het `ResourceRepositoryClient` `createRelationship` object aan en geef de volgende parameters door:

   * De URI van de bronbron.
   * De URI van de doelbron.
   * Het type relatie, een van de statische constanten in de `com.adobe.repository.infomodel.bean.Relation` klasse. In dit voorbeeld wordt een afhankelijkheidsrelatie tot stand gebracht door de waarde op te geven `Relation.TYPE_DEPENDANT_OF`.
   * Een `boolean` waarde erop wijst die of het doelmiddel automatisch aan het `com.adobe.repository.infomodel.Id`-gebaseerde herkenningsteken van het nieuwe hoofdmiddel wordt bijgewerkt. In dit voorbeeld `true` wordt vanwege de afhankelijkheidsrelatie de waarde opgegeven.
   U kunt ook een lijst met verwante bronnen voor een bepaalde bron ophalen door de methode van het `ResourceRepositoryClient` `getRelated` object aan te roepen en de volgende parameters door te geven:

   * De URI van de bron waarvoor gerelateerde bronnen moeten worden opgehaald. In dit voorbeeld wordt de bronbron ( `"/testFolder/testResource1"`) opgegeven.
   * Een `boolean` waarde die aangeeft of de opgegeven bron de bronbron in de relatie is. In dit voorbeeld `true` wordt de waarde opgegeven, omdat dit het geval is.
   * Het relatietype, dat een van de statische constanten in de `Relation` klasse is. In dit voorbeeld wordt een afhankelijkheidsrelatie opgegeven door dezelfde waarde te gebruiken die eerder is gebruikt: `Relation.TYPE_DEPENDANT_OF`.
   De `getRelated` methode retourneert een `java.util.List` van `Resource` objecten waarmee u kunt herhalen om elk van de gerelateerde bronnen op te halen, waarbij u de objecten in de map op dezelfde manier `List` naar `Resource` kunt casten. In dit voorbeeld `testResource2` wordt verwacht dat het zich in de lijst met geretourneerde bronnen bevindt.

**Zie ook**

[Resourcerelaties maken](aem-forms-repository.md#creating-resource-relationships)

[Snel starten (SOAP-modus): Relaties maken tussen bronnen met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-creating-relationships-between-resources-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Relatiebronnen maken met de webservice-API {#create-relationship-resources-using-the-web-service-api}

Relatiebronnen maken met de Repository API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die de Bewaarplaats WSDL verbruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. De serviceclient maken

   Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de `Credentials` eigenschap in met een `System.Net.NetworkCredential` object dat de gebruikersnaam en het wachtwoord bevat.

1. De URI&#39;s opgeven van de bronnen die moeten worden gekoppeld

   Geef de URI&#39;s op van de bronnen die moeten worden gerelateerd. In dit geval, omdat de middelen genoemd en `testResource1` en in de genoemde omslag worden gevestigd `testResource2` , zijn hun URIs `testFolder`en `"/testFolder/testResource1"` `"/testFolder/testResource2"`. Wanneer het gebruiken van een taal volgzaam met het Kader van Microsoft .NET (bijvoorbeeld, C#), worden URIs opgeslagen als `System.String` voorwerpen. In dit voorbeeld worden de bronnen eerst naar de opslagplaats geschreven en worden hun URI&#39;s opgehaald. Voor meer informatie over het schrijven van een middel, zie het [Schrijven van Middelen](aem-forms-repository.md#writing-resources).

1. De relatie maken

   Roep de methode van het `RepositoryServiceService` `createRelationship` object aan en geef de volgende parameters door:

   * De URI van de bronbron.
   * De URI van de doelbron.
   * Het type relatie. In dit voorbeeld wordt een afhankelijkheidsrelatie tot stand gebracht door de waarde op te geven `3`.
   * Een `boolean` waarde die aangeeft of het relatietype is opgegeven. In dit voorbeeld `true` wordt de waarde opgegeven.
   * Een `boolean` waarde erop wijst die of het doelmiddel automatisch aan het `Id`-gebaseerde herkenningsteken van het nieuwe hoofdmiddel wordt bijgewerkt. In dit voorbeeld `true` wordt vanwege de afhankelijkheidsrelatie de waarde opgegeven.
   * Een `boolean` waarde die aangeeft of de doelkop is opgegeven. In dit voorbeeld `true` wordt de waarde opgegeven.
   * Geef `null` de laatste parameter door.
   U kunt ook een lijst met verwante bronnen voor een bepaalde bron ophalen door de methode van het `RepositoryServiceService` `getRelated` object aan te roepen en de volgende parameters door te geven:

   * De URI van de bron waarvoor gerelateerde bronnen moeten worden opgehaald. In dit voorbeeld wordt de bronbron ( `"/testFolder/testResource1"`) opgegeven.
   * Een `boolean` waarde die aangeeft of de opgegeven bron de bronbron in de relatie is. In dit voorbeeld `true` wordt de waarde opgegeven, omdat dit het geval is.
   * Een `boolean` waarde die aangeeft of de bronbron is opgegeven. In dit voorbeeld `true` wordt de waarde opgegeven.
   * Een array van gehele getallen die de relatietypen bevatten. In dit voorbeeld wordt een afhankelijkheidsrelatie opgegeven door dezelfde waarde in de array te gebruiken als eerder werd gebruikt: `3`.
   * Geef `null` de resterende twee parameters door.
   De `getRelated` methode keert een serie van voorwerpen terug die aan `Resource` voorwerpen kunnen worden gegoten waardoor u kunt herhalen om elk van de verwante middelen terug te winnen. In dit voorbeeld `testResource2` wordt verwacht dat het zich in de lijst met geretourneerde bronnen bevindt.

**Zie ook**

[Resourcerelaties maken](aem-forms-repository.md#creating-resource-relationships)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Bronnen vergrendelen {#locking-resources}

U kunt een bron of reeks bronnen vergrendelen voor exclusief gebruik door een bepaalde gebruiker of voor gedeeld gebruik door meerdere gebruikers. Een gedeelde vergrendeling is een indicatie dat er iets met de bron zal gebeuren, maar het belet niemand anders om acties met die bron te ondernemen. Een gedeeld slot zou als signalerend mechanisme moeten worden beschouwd. Een exclusief slot betekent dat de gebruiker die het middel sloot de middel zal veranderen, en het slot zorgt ervoor dat niemand anders dit kan doen tot de gebruiker niet meer toegang tot het middel nodig heeft en het slot heeft vrijgegeven. Als een bewaargegevensbeheerder een middel ontgrendelt, zullen alle exclusieve en gedeelde sloten op dat middel automatisch worden verwijderd. Dit type actie is bedoeld voor situaties waarin een gebruiker niet meer beschikbaar is en de bron niet heeft ontgrendeld.

Wanneer een bron is vergrendeld, wordt een vergrendelingspictogram weergegeven wanneer u het tabblad Bronnen in Workbench bekijkt, zoals in de volgende afbeelding wordt getoond.

![lr_lr_lockrepository](assets/lr_lr_lockrepository.png)

U kunt de toegang tot bronnen programmatisch beheren met de Java API of webservice van de Repository-service.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary_of_steps-7}

Voer de volgende stappen uit om bronnen te vergrendelen en te ontgrendelen:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Geef de URI op van de bron die moet worden vergrendeld.
1. Vergrendel de resource.
1. Haal de sloten voor de bron op.
1. De bron ontgrendelen

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**De serviceclient maken**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**De URI opgeven van de bron die moet worden vergrendeld**

Maak een tekenreeks met de URI van de bron die moet worden vergrendeld. De syntaxis bevat slashes, zoals in dit voorbeeld: &quot;/*path*/*resource*&quot;.

**De bron vergrendelen**

Roep de servicemethode Repository aan om de bron te vergrendelen, waarbij de URI, het type vergrendeling en de vergrendelingsdiepte worden opgegeven.

**Haalt de vergrendelingen voor de bron op**

Roep de de dienstmethode van de Bewaarplaats aan om de sloten voor het middel terug te winnen, die URI specificeren.

**De bron ontgrendelen**

Roep de servicemethode Repository aan om de bron te ontgrendelen en de URI op te geven.

**Zie ook**

[Bronnen vergrendelen met de Java API](aem-forms-repository.md#lock-resources-using-the-java-api)

[Bronnen vergrendelen met de webservice-API](aem-forms-repository.md#lock-resources-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bronnen vergrendelen met de Java API {#lock-resources-using-the-java-api}

Bronnen vergrendelen met de API voor opslagplaats (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. De URI opgeven van de bron die moet worden vergrendeld

   Geef de URI op van de bron die moet worden vergrendeld. In dit geval is de URI van de resource `testResource` . De genoemde `testFolder`bevindt zich in de map met de naam `"/testFolder/testResource"`. De URI wordt opgeslagen als een `java.lang.String` object.

1. De bron vergrendelen

   Roep de methode van het `ResourceRepositoryClient` `lockResource` object aan en geef de volgende parameters door:

   * De URI van de resource.
   * Het vergrendelingsbereik. In dit voorbeeld, omdat het middel voor exclusief gebruik zal worden gesloten, wordt het slotwerkingsgebied gespecificeerd zoals `com.adobe.repository.infomodel.bean.Lock.SCOPE_EXCLUSIVE`.
   * De vergrendelingsdiepte. In dit voorbeeld wordt de vergrendelingsdiepte opgegeven als `Lock.DEPTH_ZERO`. De vergrendelingsinstelling is namelijk alleen van toepassing op de specifieke bron en niet op de leden of onderliggende elementen van de vergrendelingsbron.
   >[!NOTE]
   >
   >De overbelaste versie van de `lockResource` methode die vier parameters vereist werpt een uitzondering. Verzeker om de `lockResource` methode te gebruiken die drie parameters zoals aangetoond in deze analyse vereist.

1. Haalt de vergrendelingen voor de bron op

   Roep de `ResourceRepositoryClient` methode van het `getLocks` object aan en geef de URI van de bron als parameter door. De methode retourneert een lijst met vergrendelingsobjecten waarmee u kunt herhalen. In dit voorbeeld worden de eigenaar, diepte en bereik van de vergrendeling voor elk object afgedrukt door respectievelijk de methoden `getOwnerUserId`, `getDepth``getType` en methoden van elk Lock-object aan te roepen.

1. De bron ontgrendelen

   Roep de `ResourceRepositoryClient` methode van het `unlockResource` object aan en geef de URI van de bron als parameter door. Zie de [AEM Forms API Reference](https://www.adobe.com/go/learn_aemforms_javadocs_63_en)voor meer informatie.

**Zie ook**

[Bronnen vergrendelen](aem-forms-repository.md#locking-resources)

[Snel starten (SOAP-modus): Een bron vergrendelen met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-locking-a-resource-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bronnen vergrendelen met de webservice-API {#lock-resources-using-the-web-service-api}

Bronnen vergrendelen met behulp van de Repository Service API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die de Bewaarplaats WSDL gebruikend Base64 gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. De serviceclient maken

   Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de `Credentials` eigenschap in met een `System.Net.NetworkCredential` object dat de gebruikersnaam en het wachtwoord bevat.

1. De URI opgeven van de bron die moet worden vergrendeld

   Geef een tekenreeks op die de URI bevat van de bron die moet worden vergrendeld. In dit geval, omdat de genoemde bron in de omslag `testResource` is `testFolder`, is zijn URI `"/testFolder/testResource"`. Wanneer het gebruiken van een taal volgzaam met het Kader van Microsoft .NET (bijvoorbeeld, C#), sla URI in een `System.String` voorwerp op.

1. De bron vergrendelen

   Roep de methode van het `RepositoryServiceService` `lockResource` object aan en geef de volgende parameters door:

   * De URI van de resource.
   * Het vergrendelingsbereik. In dit voorbeeld, omdat het middel voor exclusief gebruik zal worden gesloten, wordt het slotwerkingsgebied gespecificeerd zoals `11`.
   * De vergrendelingsdiepte. In dit voorbeeld wordt de vergrendelingsdiepte opgegeven als `2`. De vergrendelingsinstelling is namelijk alleen van toepassing op de specifieke bron en niet op de leden of onderliggende elementen van de vergrendelingsbron.
   * Een `int` waarde die op het aantal seconden wijst tot het slot verloopt. In dit voorbeeld wordt de waarde van `1000` gebruikt.
   * Geef `null` de laatste parameter door.

1. Haalt de vergrendelingen voor de bron op

   Roep de `RepositoryServiceService` methode van het `getLocks` object aan en geef de URI van de bron door als de eerste parameter en `null` voor de tweede parameter. De methode retourneert een `object` array met `Lock` objecten die u kunt doorlopen. In dit voorbeeld worden de eigenaar van de vergrendeling, de diepte en het bereik voor elk object afgedrukt door toegang te krijgen tot respectievelijk de velden `Lock` , `ownerUserId`en `depth``type` velden van elk object.

1. De bron ontgrendelen

   Roep de `RepositoryServiceService` methode van het `unlockResource` object aan en geef de URI van de bron door als de eerste parameter en `null` voor de tweede parameter.

**Zie ook**

[Bronnen vergrendelen](aem-forms-repository.md#locking-resources)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

## Bronnen verwijderen {#deleting-resources}

U kunt bronnen programmatisch verwijderen van een bepaalde locatie in de opslagplaats met behulp van de Java API (SOAP) van de Repository-service.

Wanneer u een middel schrapt, is de schrapping normaal permanent, hoewel in sommige gevallen ECM bewaart bewaarplaatsen de versies van het middel volgens hun geschiedenismechanismen. Daarom wanneer het schrappen van een middel, is het belangrijk om zeker te zijn dat u nooit die middel opnieuw zult nodig hebben. De gemeenschappelijke redenen om een middel te schrappen omvatten de behoefte om de beschikbare ruimte in het gegevensbestand te verhogen. U kunt een versie van een bron verwijderen, maar als u dat doet, moet u de resource-id opgeven en niet de logische id (LID) of het pad. Als u een map verwijdert, worden alle gegevens in die map, inclusief de submappen en bronnen, automatisch verwijderd.

Gerelateerde bronnen worden niet verwijderd. Als u bijvoorbeeld een formulier hebt waarin het bestand logo.gif wordt gebruikt en u logo.gif verwijdert, wordt een relatie opgeslagen in de relatietabel die in behandeling is. Als alternatief kunt u voor versiedrukking de objectstatus van de meest recente versie instellen op afgekeurd.

Een schrappingsverrichting is niet transactie-veilig in systemen ECM. Als u bijvoorbeeld probeert 100 bronnen te verwijderen en de bewerking op de 50e bron mislukt, worden de eerste 49 instanties verwijderd, maar de rest niet. Anders, is het standaardgedrag terugschroeven (niet-verplichting).

>[!NOTE]
>
>Bij gebruik van de `com.adobe.repository.bindings.dsc.client.ResourceRepositoryClient.deleteResources()` methode met de ECM-opslagplaats (EMC Documentum Content Server en IBM FileNet P8 Content Manager) wordt de transactie niet teruggedraaid als de verwijdering mislukt voor een van de opgegeven bronnen, wat betekent dat de bestanden die zijn verwijderd, niet kunnen worden verwijderd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Bewaarplaats, zie de Verwijzing van de [Diensten voor Vormen](https://www.adobe.com/go/learn_aemforms_services_63)AEM.

### Overzicht van de stappen {#summary_of_steps-8}

Ga als volgt te werk om een bron te verwijderen:

1. Inclusief projectbestanden.
1. Maak een Repository Service-client.
1. Geef de URI op van de bron die moet worden verwijderd.
1. Verwijder de bron.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, neemt u de proxybestanden op.

**De serviceclient maken**

Voordat u een bron via programmacode kunt lezen, moet u een verbinding tot stand brengen en referenties opgeven. Dit wordt verwezenlijkt door een de dienstcliënt te creëren.

**De URI opgeven van de bron die moet worden verwijderd**

Maak een tekenreeks met de URI van de bron die moet worden verwijderd. De syntaxis bevat slashes, zoals in dit voorbeeld: &quot;/*path*/*resource*&quot;. Als de te schrappen bron een omslag is, zal de schrapping recursief zijn.

**De bron verwijderen**

Roep de servicemethode Repository aan om de bron te verwijderen en de URI op te geven.

**Zie ook**

[Bronnen verwijderen met de Java API](aem-forms-repository.md#delete-resources-using-the-java-api-soap)

[Bronnen verwijderen met de webservice-API](aem-forms-repository.md#delete-resources-using-the-web-service-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Repository Service API](/help/forms/developing/repository-service-api-quick-starts.md#repository-service-api-quick-starts)

### Bronnen verwijderen met de Java API (SOAP) {#delete-resources-using-the-java-api-soap}

Verwijder een bron met de Repository API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden op in het klassenpad van uw Java-project.

1. De serviceclient maken

   Maak een `ResourceRepositoryClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. De URI opgeven van de bron die moet worden verwijderd

   Geef de URI op van de bron die moet worden opgehaald. In dit geval, omdat het middel genoemd testResourceToBeDelette in de omslag genoemd testFolder is, is zijn URI `/testFolder/testResourceToBeDeleted`. De URI wordt opgeslagen als een `java.lang.String` object. In dit voorbeeld wordt de bron eerst naar de opslagplaats geschreven en wordt de URI ervan opgehaald. Voor meer informatie over het schrijven van een middel, zie het [Schrijven van Middelen](aem-forms-repository.md#writing-resources).

1. De bron verwijderen

   Roep de `ResourceRepositoryClient` methode van het `deleteResource` object aan en geef de URI van de bron als parameter door.

**Zie ook**

[Bronnen verwijderen](aem-forms-repository.md#deleting-resources)

[Snel starten (SOAP-modus): Zoeken naar bronnen met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-searching-for-resources-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Bronnen verwijderen met de webservice-API {#delete-resources-using-the-web-service-api}

Verwijder een bron met de Repository API (webservice):

1. Projectbestanden opnemen

   * Creeer een de cliëntassemblage van Microsoft .NET die de Bewaarplaats WSDL gebruikend Base64 gebruikt.
   * Verwijs naar de cliëntassemblage van Microsoft .NET.

1. De serviceclient maken

   Gebruikend de de cliëntassemblage van Microsoft .NET, creeer een `RepositoryServiceService` voorwerp door zijn standaardaannemer aan te halen. Stel de `Credentials` eigenschap in met een `System.Net.NetworkCredential` object dat de gebruikersnaam en het wachtwoord bevat.

1. De URI opgeven van de bron die moet worden verwijderd

   Geef de URI op van de bron die moet worden opgehaald. In dit geval is de URI van de resource `testResourceToBeDeleted` . De genoemde `testFolder`bevindt zich in de map met de naam `"/testFolder/testResourceToBeDeleted"`. In dit voorbeeld wordt de bron eerst naar de opslagplaats geschreven en wordt de URI ervan opgehaald. Voor meer informatie over het schrijven van een middel, zie het [Schrijven van Middelen](aem-forms-repository.md#writing-resources).

1. De bron verwijderen

   Roep de `RepositoryServiceService` methode van het `deleteResources` object aan en geef een `System.String` array met de URI van de bron door als de eerste parameter. Geef `null` de tweede parameter door.

**Zie ook**

[Bronnen verwijderen](aem-forms-repository.md#deleting-resources)

[AEM-formulieren aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)
