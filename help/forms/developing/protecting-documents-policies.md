---
title: Documenten beveiligen met beleid
seo-title: Documenten beveiligen met beleid
description: 'null'
seo-description: 'null'
uuid: 6feb69ef-7b61-4d0b-8c87-d65d98bae9b5
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
discoiquuid: 9b1d2bf3-f28c-41b2-9026-1f3311556422
translation-type: tm+mt
source-git-commit: 1343cc33a1e1ce26c0770a3b49317e82353497ab
workflow-type: tm+mt
source-wordcount: '15466'
ht-degree: 0%

---


# Documenten beveiligen met beleid {#protecting-documents-with-policies}

**Informatie over de Document Security Service**

Met de documentbeveiligingsservice kunnen gebruikers op dynamische wijze instellingen voor vertrouwelijkheid toepassen op Adobe PDF-documenten en de documenten beheren, ongeacht hoe breed ze zijn verspreid.

Met de Document Security-service wordt voorkomen dat informatie buiten het bereik van de gebruiker wordt verspreid doordat gebruikers de controle kunnen behouden over de manier waarop ontvangers het met een beleid beveiligde PDF-document gebruiken. Een gebruiker kan opgeven wie een document mag openen, hoe hij het kan gebruiken en het document na de verspreiding ervan controleren. Een gebruiker kan ook dynamisch de toegang tot een document beheren dat met een beleid is beveiligd en kan de toegang tot het document zelfs dynamisch intrekken.

De service Documentbeveiliging beschermt ook andere bestandstypen, zoals Microsoft Word-bestanden (DOC-bestanden). U kunt de client-API voor documentbeveiliging gebruiken om met deze bestandstypen te werken. De volgende versies worden ondersteund:

* Microsoft Office 2003-bestanden (DOC-, XLS-, PPT-bestanden)
* Microsoft Office 2007-bestanden (DOCX-, XLSX-, PPTX-bestanden)
* PTC Pro/E-bestanden

Voor de duidelijkheid bespreken de volgende twee secties hoe te met de documenten van Word te werken:

* [Beleid toepassen op Word-documenten](protecting-documents-policies.md#applying-policies-to-word-documents)
* [Beleid verwijderen uit Word-documenten](protecting-documents-policies.md#removing-policies-from-word-documents)

U kunt deze taken uitvoeren met de documentbeveiligingsservice:

* Beleid maken. Zie [Beleid](protecting-documents-policies.md#creating-policies)maken voor meer informatie.
* Beleid wijzigen. Zie Beleid [wijzigen voor meer informatie](protecting-documents-policies.md#modifying-policies).
* Beleid verwijderen. Zie Beleid [verwijderen voor meer informatie](protecting-documents-policies.md#deleting-policies).
* Beleid toepassen op PDF-documenten. Zie Beleid [toepassen op PDF-documenten](protecting-documents-policies.md#applying-policies-to-pdf-documents)voor meer informatie.
* Beleid verwijderen uit PDF-documenten. Zie Beleid [verwijderen uit PDF-documenten](protecting-documents-policies.md#removing-policies-from-pdf-documents)voor meer informatie.
* Met een beleid beveiligde documenten controleren. Zie Met [beleid beveiligde PDF-documenten](protecting-documents-policies.md#inspecting-policy-protected-pdf-documents)controleren voor meer informatie.
* Toegang tot PDF-documenten intrekken. Zie Toegang tot documenten [intrekken voor meer informatie](protecting-documents-policies.md#revoking-access-to-documents).
* Toegang tot ingetrokken documenten opnieuw instellen. Zie Toegang [tot ingetrokken documenten](protecting-documents-policies.md#reinstating-access-to-revoked-documents)opnieuw instellen voor meer informatie.
* Watermerken maken. Zie Watermerken [maken voor meer informatie](protecting-documents-policies.md#creating-watermarks).
* Zoeken naar gebeurtenissen. Zie [Zoeken naar gebeurtenissen](protecting-documents-policies.md#searching-for-events)voor meer informatie.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Beleid maken {#creating-policies}

U kunt beleid programmatisch maken met de Java API voor documentbeveiliging of de webservice-API. Een *beleid* is een inzameling van informatie die de montages van de documentveiligheid, geoorloofde gebruikers, en gebruiksrechten omvat. U kunt een willekeurig aantal beleidsregels maken en opslaan met de beveiligingsinstellingen die geschikt zijn voor verschillende situaties en gebruikers.

Het beleid laat u toe om deze taken uit te voeren:

* Geef de personen op die het document kunnen openen. Ontvangers kunnen tot uw organisatie behoren of zich buiten uw organisatie bevinden.
* Geef op hoe ontvangers het document kunnen gebruiken. U kunt de toegang tot verschillende functies van Acrobat en Adobe Reader beperken. Deze functies omvatten de mogelijkheid om tekst af te drukken en te kopiëren, handtekeningen toe te voegen en opmerkingen toe te voegen aan een document.
* Wijzig de toegangs- en beveiligingsinstellingen op elk gewenst moment, zelfs nadat u het document met beveiliging hebt gedistribueerd.
* Controleer het gebruik van het document nadat u het hebt verspreid. U kunt zien hoe het document wordt gebruikt en wie het gebruikt. U kunt bijvoorbeeld erachter komen wanneer iemand het document heeft geopend.

### Beleid maken met behulp van webservices {#creating-a-policy-using-web-services}

Wanneer u een beleid maakt met de webservice-API, verwijst u naar een bestaand XML-bestand (Portable Document Rights Language) waarin het beleid wordt beschreven. Beleidsmachtigingen en de principal worden gedefinieerd in het PDRL-document. Het volgende XML-document is een voorbeeld van een PDRL-document.

```xml
 <?xml version="1.0" encoding="UTF-8" standalone="yes"?>
 <Policy PolicyInstanceVersion="1" PolicyID="5DA3F847-DE76-F9CC-63EA-49A8D59154DE" PolicyCreationTime="2004-08-30T00:02:28.294+00:00" PolicyType="1" PolicySchemaVersion="1.0" PolicyName="SDK Test Policy -4344050357301573237" PolicyDescription="An SDK Test policy" xmlns="https://www.adobe.com/schema/1.0/pdrl">
       <PolicyEntry>
          <ns1:Permission PermissionName="com.adobe.aps.onlineOpen" Access="ALLOW" xmlns:ns1="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns2:Permission PermissionName="com.adobe.aps.offlineOpen" Access="ALLOW" xmlns:ns2="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns3:Permission PermissionName="com.adobe.aps.pdf.editNotes" Access="ALLOW" xmlns:ns3="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns4:Permission PermissionName="com.adobe.aps.pdf.fillAndSign" Access="ALLOW" xmlns:ns4="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
          <Principal PrincipalNameType="SYSTEM">
             <PrincipalDomain>EDC_SPECIAL</PrincipalDomain>
 
             <PrincipalName>all_internal_users</PrincipalName>
          </Principal>
       </PolicyEntry>
       <PolicyEntry>
          <ns5:Permission PermissionName="com.adobe.aps.onlineOpen" Access="ALLOW" xmlns:ns5="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns6:Permission PermissionName="com.adobe.aps.offlineOpen" Access="ALLOW" xmlns:ns6="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns7:Permission PermissionName="com.adobe.aps.pdf.copy" Access="ALLOW" xmlns:ns7="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns8:Permission PermissionName="com.adobe.aps.pdf.printLow" Access="ALLOW" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" xmlns:ns8="https://www.adobe.com/schema/1.0/pdrl" />
 
          <ns9:Permission PermissionName="com.adobe.aps.policySwitch" Access="ALLOW" xmlns:ns9="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns10:Permission PermissionName="com.adobe.aps.revoke" Access="ALLOW" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" xmlns:ns10="https://www.adobe.com/schema/1.0/pdrl" />
 
          <ns11:Permission PermissionName="com.adobe.aps.pdf.edit" Access="ALLOW" xmlns:ns11="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns12:Permission PermissionName="com.adobe.aps.pdf.editNotes" Access="ALLOW" xmlns:ns12="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns13:Permission PermissionName="com.adobe.aps.pdf.fillAndSign" Access="ALLOW" xmlns:ns13="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <ns14:Permission PermissionName="com.adobe.aps.pdf.printHigh" Access="ALLOW" xmlns:ns14="https://www.adobe.com/schema/1.0/pdrl" xmlns="https://www.adobe.com/schema/1.0/pdrl-ex" />
 
          <Principal PrincipalNameType="SYSTEM">
             <PrincipalDomain>EDC_SPECIAL</PrincipalDomain>
 
             <PrincipalName>publisher</PrincipalName>
          </Principal>
       </PolicyEntry>
 
       <OfflineLeasePeriod>
          <Duration>P31D</Duration>
       </OfflineLeasePeriod>
 
       <AuditSettings isTracked="true" />
 
       <PolicyValidityPeriod isAbsoluteTime="false">
          <ValidityPeriodRelative>
             <NotBeforeRelative>PT0S</NotBeforeRelative>
 
             <NotAfterRelative>P20D</NotAfterRelative>
          </ValidityPeriodRelative>
       </PolicyValidityPeriod>
 </Policy>
 
```

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een beleid te maken:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Stel de kenmerken van het beleid in.
1. Maak een beleidsvermelding.
1. Registreer het beleid.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

De volgende JAR-bestanden moeten worden toegevoegd aan het klassepad van uw project:

* adobe-rightsmanagement-client.jar
* namespace.jar (als AEM Forms op JBoss worden opgesteld)
* jaxb-api.jar (als AEM Forms worden geïmplementeerd op JBoss)
* jaxb-impl.jar (als AEM Forms worden geïmplementeerd op JBoss)
* jaxb-libs.jar (als AEM Forms worden geïmplementeerd op JBoss)
* jaxb-xjc.jar (als AEM Forms worden geïmplementeerd op JBoss)
* relaxngDatatype.jar (als AEM Forms worden geïmplementeerd op JBoss)
* xsdlib.jar (als AEM Forms worden geïmplementeerd op JBoss)
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar
* jbossall-client.jar (gebruik een ander JAR-bestand als AEM Forms niet zijn geïmplementeerd op JBoss)

Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze JAR-bestanden.

**Een API-object voor documentbeveiliging maken**

Voordat u via programmacode een bewerking met de documentbeveiligingsservice kunt uitvoeren, maakt u een clientobject van de documentbeveiligingsservice.

**De kenmerken van het beleid instellen**

Stel beleidskenmerken in om een beleid te maken. Een verplicht kenmerk is de naam van het beleid. Beleidsnamen moeten uniek zijn voor elke beleidsset. Een beleidsset is gewoon een verzameling van beleidsmaatregelen. Er kunnen twee beleid met dezelfde naam zijn als het beleid tot afzonderlijke beleidsreeksen behoort. Twee beleid binnen één beleidsset kan echter niet dezelfde beleidsnaam hebben.

Een ander nuttig kenmerk dat moet worden ingesteld, is de geldigheidsperiode. Een geldigheidsperiode is de periode waarin een document dat onder een beleid valt, toegankelijk is voor geautoriseerde ontvangers. Als u dit kenmerk niet instelt, is het beleid altijd geldig.

U kunt een geldigheidsperiode instellen op een van de volgende opties:

* Een bepaald aantal dagen dat het document toegankelijk is vanaf het moment dat het document wordt gepubliceerd
* Een einddatum waarna het document niet toegankelijk is
* Een specifiek datumbereik waarvoor het document toegankelijk is
* Altijd geldig

U kunt alleen een begindatum opgeven, wat betekent dat het beleid geldig is na de begindatum. Als u slechts een einddatum specificeert, is het beleid geldig tot de einddatum. Er wordt echter een uitzondering gegenereerd als zowel een begindatum als een einddatum niet zijn gedefinieerd.

Wanneer u kenmerken instelt die tot een beleid behoren, kunt u ook versleutelingsinstellingen instellen. Deze versleutelingsinstellingen zijn van invloed wanneer het beleid wordt toegepast op een document. U kunt de volgende versleutelingswaarden opgeven:

* **AES256**: Vertegenwoordigt het AES encryptiealgoritme met een sleutel met 256 bits.
* **AES128**: Vertegenwoordigt het AES encryptiealgoritme met een sleutel met 128 bits.
* **NoEncryption:** Vertegenwoordigt geen encryptie.

Wanneer u de `NoEncryption` optie opgeeft, kunt u de `PlaintextMetadata` optie niet instellen op `false`. Wanneer u dit probeert, wordt een uitzondering gegenereerd.

>[!NOTE]
>
>Zie de `Policy` interfacebeschrijving in de API-naslaggids voor [AEM Forms voor informatie over andere kenmerken die u kunt instellen](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Een beleidsitem maken**

Een beleidsingang verbindt hoofden, die groepen en gebruikers zijn, en toestemmingen aan een beleid. Een beleid moet ten minste één beleidslijn hebben. Stel bijvoorbeeld dat u de volgende taken uitvoert:

* Maak en registreer een beleidsvermelding waarmee een groep een document alleen online kan bekijken en ontvangers het niet kunnen kopiëren.
* Koppel de beleidsvermelding aan het beleid.
* Beveilig een document met het beleid door Acrobat te gebruiken.

Hierdoor kunnen ontvangers het document alleen online bekijken en niet kopiëren. Het document blijft beveiligd totdat de beveiliging ervan is verwijderd.

**Het beleid registreren**

Een nieuw beleid moet worden geregistreerd alvorens het kan worden gebruikt. Nadat u een beleid hebt geregistreerd, kunt u het gebruiken om documenten te beschermen.

### Een beleid maken met de Java API {#create-a-policy-using-the-java-api}

Een beleid maken met de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `DocumentSecurityClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Stel de kenmerken van het beleid in.

   * Maak een `Policy` object door de statische `InfomodelObjectFactory` methode van het `createPolicy` object aan te roepen. Deze methode retourneert een `Policy` object.
   * Stel het naamkenmerk van het beleid in door de methode van het `Policy` `setName` object aan te roepen en een tekenreekswaarde door te geven die de naam van het beleid aangeeft.
   * Stel de beschrijving van het beleid in door de methode van het `Policy` `setDescription` object aan te roepen en een tekenreekswaarde door te geven die de beschrijving van het beleid aangeeft.
   * Stel de beleidsset in waartoe het nieuwe beleid behoort door de methode van het `Policy` `setPolicySetName` object aan te roepen en een tekenreekswaarde door te geven die de naam van de beleidsset opgeeft. (U kunt `null` voor deze parameterwaarde specificeren die in het beleid resulteert dat aan de *Mijn het beleidsreeks van Beleid* wordt toegevoegd.)
   * Maak de geldigheidsperiode van het beleid door de statische `InfomodelObjectFactory` methode van het `createValidityPeriod` object aan te roepen. Deze methode retourneert een `ValidityPeriod` object.
   * Stel het aantal dagen in waarvoor een document dat met een beleid is beveiligd, toegankelijk is door de methode van het `ValidityPeriod` `setRelativeExpirationDays` object aan te roepen en een geheel-getalwaarde door te geven die het aantal dagen aangeeft.
   * Stel de geldigheidsperiode van het beleid in door de methode van het `Policy` object aan te roepen en het `setValidityPeriod` `ValidityPeriod` object door te geven.

1. Maak een beleidsvermelding.

   * Maak een beleidsitem door de statische `InfomodelObjectFactory` methode van het `createPolicyEntry` object aan te roepen. Deze methode retourneert een `PolicyEntry` object.
   * Geef de bevoegdheden van het beleid op door de statische `InfomodelObjectFactory` methode van het `createPermission` object aan te roepen. Geef een statisch gegevenslid door dat tot de `Permission` interface behoort die de toestemming vertegenwoordigt. Deze methode retourneert een `Permission` object. Als u bijvoorbeeld de machtiging wilt toevoegen waarmee gebruikers gegevens kunnen kopiëren uit een PDF-document dat met een beleid is beveiligd, geeft u door `Permission.COPY`. (Herhaal deze stap voor elke machtiging die u wilt toevoegen.)
   * Voeg de toestemming aan de beleidsingang toe door de methode van het `PolicyEntry` voorwerp aan te halen en het `addPermission` `Permission` voorwerp over te gaan. (Herhaal deze stap voor elk `Permission` object dat u hebt gemaakt).
   * Creeer het beleidshoofd door de statische methode van het `InfomodelObjectFactory` `createSpecialPrincipal` voorwerp aan te halen. Geef een gegevenslid door dat tot het `InfomodelObjectFactory` voorwerp behoort dat het hoofd vertegenwoordigt. Deze methode retourneert een `Principal` object. Als u bijvoorbeeld de uitgever van het document als hoofd wilt toevoegen, geeft u door `InfomodelObjectFactory.PUBLISHER_PRINCIPAL`.
   * Voeg de principal aan de beleidsingang toe door de `PolicyEntry` methode van het `setPrincipal`voorwerp aan te halen en het `Principal` voorwerp over te gaan.
   * Voeg de beleidsingang aan het beleid toe door de methode van het `Policy` voorwerp aan te halen en het `addPolicyEntry` `PolicyEntry` voorwerp over te gaan.

1. Registreer het beleid.

   * Maak een `PolicyManager` object door de `DocumentSecurityClient` methode van het `getPolicyManager` object aan te roepen.
   * Registreer het beleid door de methode van het `PolicyManager` `registerPolicy` voorwerp aan te halen en de volgende waarden over te gaan:

      * Het `Policy` object dat het te registreren beleid vertegenwoordigt.
   * Een tekenreekswaarde die staat voor de beleidsset waartoe het beleid behoort.

   Als u een beheerdersaccount voor AEM-formulieren binnen de verbindingsinstellingen gebruikt om het `DocumentSecurityClient` object te maken, geeft u de naam van de beleidsset op wanneer u de `registerPolicy` methode aanroept. Als u een `null` waarde voor de beleidsreeks overgaat, wordt het beleid gecreeerd in de beheerders *Mijn het beleidsreeks van Beleid* .

   Als u een gebruiker van de Veiligheid van het Document binnen verbindingsmontages gebruikt, dan kunt u de overbelaste `registerPolicy` methode aanhalen die slechts het beleid goedkeurt. U hoeft dus geen naam voor de beleidsset op te geven. Nochtans, wordt het beleid toegevoegd aan de beleidsreeks genoemd *Mijn Beleid*. Als u niet het nieuwe beleid aan deze beleidreeks wilt toevoegen, dan specificeer een naam van de beleidsreeks wanneer u de `registerPolicy` methode aanhaalt.

   >[!NOTE]
   >
   >Verwijs bij het maken van een beleid naar een bestaande beleidsset. Als u een beleidsset opgeeft die niet bestaat, wordt een uitzondering gegenereerd.

Zie het volgende voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP-modus): Beleid maken met de Java API&quot;

### Beleid maken met de webservice-API {#create-a-policy-using-the-web-service-api}

Een beleid maken met de API voor documentbeveiliging (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Maak een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Maak een `DocumentSecurityServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `RightsManagementServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Stel de kenmerken van het beleid in.

   * Maak een `PolicySpec` object met de constructor ervan.
   * Stel de naam van het beleid in door een tekenreekswaarde toe te wijzen aan het `PolicySpec` gegevenslid van het `name` object.
   * Stel de beschrijving van het beleid in door een tekenreekswaarde toe te wijzen aan het `PolicySpec` gegevenslid van het `description` object.
   * Stel de beleidsset in waartoe het beleid behoort door een tekenreekswaarde toe te wijzen aan het `PolicySpec` gegevenslid van het `policySetName` object. U moet een bestaande naam voor een beleidsset opgeven. (U kunt `null` voor deze parameterwaarde specificeren die in het beleid resulteert dat aan *Mijn Beleid* wordt toegevoegd.)
   * Stel de offline leaseperiode van het beleid in door een geheel-getalwaarde toe te wijzen aan het `PolicySpec` gegevenslid van het `offlineLeasePeriod` object.
   * Stel het `PolicySpec` `policyXml` gegevenslid van het object in met een tekenreekswaarde die PDRL XML-gegevens vertegenwoordigt. Om deze taak uit te voeren, creeer een .NET `StreamReader` voorwerp door zijn aannemer te gebruiken. Geef de locatie van een PDRL XML-bestand dat het beleid vertegenwoordigt door aan de `StreamReader` constructor. Roep vervolgens de `StreamReader` methode van het `ReadLine` object aan en wijs de geretourneerde waarde toe aan een tekenreeksvariabele. Doorlopen van het `StreamReader` object totdat de `ReadLine` methode null retourneert. Wijs de tekenreeksvariabele toe aan het `PolicySpec` gegevenslid van het `policyXml` object.

1. Maak een beleidsvermelding.

   Het is niet nodig om een beleidsitem te maken wanneer u een beleid maakt met de webservice-API voor documentbeveiliging. Het beleidsitem wordt gedefinieerd in het PDRL-document.

1. Registreer het beleid.

   Registreer het beleid door de methode van het `DocumentSecurityServiceClient` `registerPolicy` voorwerp aan te halen en de volgende waarden over te gaan:

   * Het `PolicySpec` object dat het te registreren beleid vertegenwoordigt.
   * Een tekenreekswaarde die staat voor de beleidsset waartoe het beleid behoort. U kunt een `null` waarde specificeren die in het beleid resulteert dat aan de *MyPolicy* beleidsreeks wordt toegevoegd.

   Als u een beheerdersaccount voor AEM-formulieren binnen de verbindingsinstellingen gebruikt om het `DocumentSecurityClient` object te maken, geeft u de naam van de beleidsset op wanneer u de `registerPolicy` methode aanroept.

   Als u een gebruiker van de Veiligheid van het Document SecurityDocument binnen verbindingsmontages gebruikt, dan kunt u de overbelaste `registerPolicy` methode aanhalen die slechts het beleid goedkeurt. U hoeft dus geen naam voor de beleidsset op te geven. Nochtans, wordt het beleid toegevoegd aan de beleidsreeks genoemd *Mijn Beleid*. Als u niet het nieuwe beleid aan deze beleidreeks wilt toevoegen, dan specificeer een naam van de beleidsreeks wanneer u de `registerPolicy` methode aanhaalt.

   >[!NOTE]
   >
   >Wanneer het creëren van een beleid en u specificeert een beleidsreeks, zorg ervoor dat u een bestaande beleidsreeks specificeert. Als u een beleidsset opgeeft die niet bestaat, wordt een uitzondering gegenereerd.

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (MTOM): Beleid maken met de webservice-API&quot;
* &quot;Quick Start (SwaRef): Beleid maken met de webservice-API&quot;

## Beleid wijzigen {#modifying-policies}

U kunt een bestaand beleid wijzigen met de Java API voor documentbeveiliging of de webservice-API. Om veranderingen in een bestaand beleid aan te brengen, wint u het terug, wijzigt het, en werkt dan het beleid op de server bij. Stel dat u een bestaand beleid ophaalt en de geldigheidsperiode ervan verlengt. Voordat de wijziging van kracht wordt, moet u het beleid bijwerken.

U kunt een beleid wijzigen wanneer de bedrijfsvereisten veranderen en het beleid niet meer op deze vereisten wijst. In plaats van een nieuw beleid te maken, kunt u gewoon een bestaand beleid bijwerken.

Als u beleidskenmerken wilt wijzigen met behulp van een webservice (bijvoorbeeld met Java-proxyklassen die zijn gemaakt met JAX-WS), moet u ervoor zorgen dat het beleid is geregistreerd bij de Document Security-service. U kunt dan naar het bestaande beleid verwijzen door de `PolicySpec.getPolicyXml` methode te gebruiken en de beleidsattributen te wijzigen door de toepasselijke methodes te gebruiken. U kunt bijvoorbeeld de offline leaseperiode wijzigen door de `PolicySpec.setOfflineLeasePeriod` methode aan te roepen.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een bestaand beleid te wijzigen:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Een bestaand beleid ophalen.
1. Beleidskenmerken wijzigen.
1. Werk het beleid bij.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u via programmacode een bewerking voor documentbeveiliging kunt uitvoeren, moet u een client-object voor documentbeveiliging maken. Als u de Java API gebruikt, maakt u een `RightsManagementClient` object. Als u de API voor documentbeveiliging gebruikt, maakt u een `RightsManagementServiceService` object.

**Een bestaand beleid ophalen**

U moet een bestaand beleid terugwinnen om het te wijzigen. Om een beleid terug te winnen, specificeer de beleidsnaam en het beleid plaatste waartot het beleid behoort. Als u een `null` waarde voor de naam van de beleidsreeks specificeert, wordt het beleid teruggewonnen van de *Mijn het beleidsreeks van Beleid* .

**De kenmerken van het beleid instellen**

Als u een beleid wilt wijzigen, wijzigt u de waarde van beleidskenmerken. Het enige beleidskenmerk dat u niet kunt wijzigen, is het naamkenmerk. Bijvoorbeeld, om de off-line huurperiode van het beleid te veranderen, kunt u de waarde van de off-line de huurperiode van het beleid attributen wijzigen.

Wanneer het wijzigen van de off-line huurperiode van een beleid gebruikend een Webdienst, wordt het `offlineLeasePeriod` gebied op de `PolicySpec` interface genegeerd. Om de offline huurperiode bij te werken, wijzig het `OfflineLeasePeriod` element in het Pdl- document van XML. Verwijs dan naar het bijgewerkte document PDRL XML door het de `PolicySpec` gegevenslid van de `policyXML` interface te gebruiken.

>[!NOTE]
>
>Zie de `Policy` interfacebeschrijving in de API-naslaggids voor [AEM Forms voor informatie over andere kenmerken die u kunt instellen](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Het beleid bijwerken**

Voordat de wijzigingen die u in een beleid aanbrengt, worden doorgevoerd, moet u het beleid bijwerken met de documentbeveiligingsservice. Wijzigingen in beleid dat documenten beveiligt, worden de volgende keer dat het document met beveiligingsbeleid wordt gesynchroniseerd met de documentbeveiligingsservice bijgewerkt.

### Bestaand beleid wijzigen met de Java API {#modify-existing-policies-using-the-java-api}

Wijzig een bestaand beleid met de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `RightsManagementClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Een bestaand beleid ophalen.

   * Maak een `PolicyManager` object door de `RightsManagementClient` methode van het `getPolicyManager` object aan te roepen.
   * Maak een `Policy` object dat staat voor het beleid dat moet worden bijgewerkt door de `PolicyManager` methode van het `getPolicy` object aan te roepen en de volgende waarden door te geven.&quot;

      * Een tekenreekswaarde die staat voor de naam van de beleidsset waartoe het beleid behoort. U kunt opgeven `null` dat dit resulteert in de gebruikte `MyPolicies` beleidsset.
      * Een tekenreekswaarde die de naam van het beleid vertegenwoordigt.

1. Stel de kenmerken van het beleid in.

   Verander de attributen van het beleid om aan uw bedrijfsvereisten te voldoen. Als u bijvoorbeeld de offline leaseperiode van het beleid wilt wijzigen, roept u de `Policy` methode van het `setOfflineLeasePeriod` object aan.

1. Werk het beleid bij.

   Werk het beleid bij door de methode van `PolicyManager` objecten aan te roepen `updatePolicy` . Geef het `Policy` object door dat het beleid vertegenwoordigt dat moet worden bijgewerkt.

**Codevoorbeelden**

Zie de modus Snel starten (SOAP-modus) voor codevoorbeelden met de Document Security-service: Een beleid wijzigen met de Java API-sectie.

### Bestaand beleid wijzigen met de webservice-API {#modify-existing-policies-using-the-web-service-api}

Wijzig een bestaand beleid met de API voor documentbeveiliging (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Maak een `RightsManagementServiceClient` object met de standaardconstructor.
   * Maak een `RightsManagementServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `RightsManagementServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Een bestaand beleid ophalen.

   Maak een `PolicySpec` object dat het beleid vertegenwoordigt dat moet worden gewijzigd door de methode van het `RightsManagementServiceClient` `getPolicy` object aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam van de beleidsset opgeeft waartoe het beleid behoort. U kunt opgeven `null` dat dit resulteert in de gebruikte `MyPolicies` beleidsset.
   * Een tekenreekswaarde die de naam van het beleid aangeeft.

1. Stel de kenmerken van het beleid in.

   Verander de attributen van het beleid om aan uw bedrijfsvereisten te voldoen.

1. Werk het beleid bij.

   Werk het beleid bij door de methode van het `RightsManagementServiceClient` voorwerp aan te halen en het `updatePolicyFromSDK` `PolicySpec` voorwerp over te gaan dat het bij te werken beleid vertegenwoordigt.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (MTOM): Een beleid wijzigen met de webservice-API&quot;
* &quot;Quick Start (SwaRef): Een beleid wijzigen met de webservice-API&quot;

## Beleid verwijderen {#deleting-policies}

U kunt een bestaand beleid verwijderen met de Java API voor documentbeveiliging of de webservice-API. Nadat een beleid is verwijderd, kan het niet meer worden gebruikt om documenten te beschermen. Bestaande documenten die door het beleid worden beschermd, zijn echter nog steeds beveiligd. U kunt een beleid schrappen wanneer nieuwere beschikbaar wordt.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om een bestaand beleid te verwijderen:

1. Projectbestanden opnemen
1. Maak een API-object voor Document Security Client.
1. Verwijder het beleid.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u programmatisch een Document Security-servicebewerking kunt uitvoeren, moet u een Document Security-service-clientobject maken. Als u de Java API gebruikt, maakt u een `RightsManagementClient` object. Als u de API voor documentbeveiliging gebruikt, maakt u een `RightsManagementServiceService` object.

**Het beleid verwijderen**

Als u een beleid wilt verwijderen, geeft u het beleid op dat u wilt verwijderen en de beleidsset waartoe het beleid behoort. De gebruiker de waarvan montages worden gebruikt om AEM Forms aan te halen moet toestemming hebben om het beleid te schrappen; anders treedt een uitzondering op. En als u probeert een beleid te verwijderen dat niet bestaat, treedt een uitzondering op.

### Beleid verwijderen met de Java API {#delete-policies-using-the-java-api}

Een beleid verwijderen met de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `RightsManagementClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Verwijder het beleid.

   * Maak een `PolicyManager` object door de `RightsManagementClient` methode van het `getPolicyManager` object aan te roepen.
   * Verwijder het beleid door de methode van het `PolicyManager` `deletePolicy` object aan te roepen en de volgende waarden door te geven:

      * Een tekenreekswaarde die de naam van de beleidsset opgeeft waartoe het beleid behoort. U kunt opgeven `null` dat dit resulteert in de gebruikte `MyPolicies` beleidsset.
      * Een tekenreekswaarde die de naam aangeeft van het beleid dat moet worden verwijderd.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP-modus): Een beleid verwijderen met de Java API&quot;

### Beleid verwijderen met de webservice-API {#delete-policies-using-the-web-service-api}

Verwijder een beleid met de API voor documentbeveiliging (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Maak een `RightsManagementServiceClient` object met de standaardconstructor.
   * Maak een `RightsManagementServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `RightsManagementServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Verwijder het beleid.

   Verwijder een beleid door de methode van het `RightsManagementServiceClient` `deletePolicy` object aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam van de beleidsset opgeeft waartoe het beleid behoort. U kunt opgeven `null` dat dit resulteert in de gebruikte `MyPolicies` beleidsset.
   * Een tekenreekswaarde die de naam aangeeft van het beleid dat moet worden verwijderd.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (MTOM): Een beleid verwijderen met de webservice-API&quot;
* &quot;Quick Start (SwaRef): Een beleid verwijderen met de webservice-API&quot;

## Beleid toepassen op PDF-documenten {#applying-policies-to-pdf-documents}

U kunt een beleid toepassen op een PDF-document om het document te beveiligen. Als u een beleid toepast op een PDF-document, beperkt u de toegang tot het document. U kunt geen beleid op een document toepassen als het document reeds met een beleid wordt beveiligd.

Terwijl het document is geopend, kunt u ook de toegang tot functies van Acrobat en Adobe Reader beperken, zoals de mogelijkheid om tekst af te drukken en te kopiëren, wijzigingen aan te brengen en handtekeningen en opmerkingen aan een document toe te voegen. Bovendien kunt u een met een beleid beveiligd PDF-document intrekken wanneer u niet langer wilt dat gebruikers het document openen.

U kunt het gebruik van een document dat met een beleid is beveiligd controleren nadat u het hebt verspreid. Dat wil zeggen dat u kunt zien hoe het document wordt gebruikt en wie het gebruikt. U kunt bijvoorbeeld zien wanneer iemand het document heeft geopend.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende stappen uit om een beleid toe te passen op een PDF-document:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Hiermee wordt een PDF-document opgehaald waarop een beleid is toegepast.
1. Pas een bestaand beleid toe op het PDF-document.
1. Sla het met beleid beveiligde PDF-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u via programmacode een bewerking met de documentbeveiligingsservice kunt uitvoeren, maakt u een clientobject van de documentbeveiligingsservice. Als u de Java API gebruikt, maakt u een `DocumentSecurityClient` object. Als u de API voor documentbeveiliging gebruikt, maakt u een `DocumentSecurityServiceService` object.

**Een PDF-document ophalen**

U kunt een PDF-document ophalen om een beleid toe te passen. Nadat u een beleid op het PDF-document hebt toegepast, worden gebruikers beperkt wanneer ze het document gebruiken. Als het beleid bijvoorbeeld niet toestaat dat het document offline wordt geopend, moeten gebruikers online zijn om het document te openen.

**Een bestaand beleid toepassen op het PDF-document**

Als u een beleid wilt toepassen op een PDF-document, verwijst u naar een bestaand beleid en geeft u op tot welke beleidsset het beleid behoort. De gebruiker die de verbindingseigenschappen instelt, moet toegang hebben tot het opgegeven beleid. Als dat niet het geval is, treedt een uitzondering op.

**Het PDF-document opslaan**

Nadat de documentbeveiligingsservice een beleid heeft toegepast op een PDF-document, kunt u het met een beleid beveiligde PDF-document opslaan als een PDF-bestand.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Toegang tot documenten intrekken](protecting-documents-policies.md#revoking-access-to-documents)

### Een beleid toepassen op een PDF-document met de Java API {#apply-a-policy-to-a-pdf-document-using-the-java-api}

Een beleid toepassen op een PDF-document met behulp van de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `RightsManagementClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Een PDF-document ophalen.

   * Maak een `java.io.FileInputStream` object dat het PDF-document vertegenwoordigt met behulp van de constructor. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Pas een bestaand beleid toe op het PDF-document.

   * Maak een `DocumentManager` object door de `RightsManagementClient` methode van het `getDocumentManager` object aan te roepen.
   * Pas een beleid toe op het PDF-document door de methode van het `DocumentManager` `protectDocument` object aan te roepen en de volgende waarden door te geven:

      * Het `com.adobe.idp.Document` object dat het PDF-document bevat waarop het beleid wordt toegepast.
      * Een tekenreekswaarde die de naam van het document aangeeft.
      * Een tekenreekswaarde die de naam opgeeft van de beleidsset waartoe het beleid behoort. U kunt een `null` waarde opgeven die resulteert in de gebruikte `MyPolicies` beleidsset.
      * Een tekenreekswaarde die de beleidsnaam opgeeft.
      * Een tekenreekswaarde die de naam vertegenwoordigt van het gebruikersbeheerdomein van de gebruiker die de uitgever van het document is. Deze parameterwaarde is optioneel en kan null zijn (als deze parameter null is, moet de volgende parameterwaarde null zijn).
      * Een tekenreekswaarde die de naam vertegenwoordigt van de canonieke naam van de gebruiker van de gebruikersmanager die de uitgever van het document is. Deze parameterwaarde is optioneel en kan `null` (als deze parameter null is, moet de vorige parameterwaarde `null`) zijn.
      * A `com.adobe.livecycle.rightsmanagement.Locale` die de scène vertegenwoordigt die voor het selecteren van het malplaatje van MS Office wordt gebruikt. Deze parameterwaarde is optioneel en wordt niet gebruikt voor PDF-documenten. Geef op om een PDF-document te beveiligen. `null`

      De `protectDocument` methode retourneert een `RMSecureDocumentResult` object dat het met een beleid beveiligde PDF-document bevat.


1. Sla het PDF-document op.

   * Roep de `RMSecureDocumentResult` methode van het `getProtectedDoc` object aan om het met een beleid beveiligde PDF-document op te halen. Deze methode retourneert een `com.adobe.idp.Document` object.
   * Maak een `java.io.File` object en controleer of de bestandsextensie PDF is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `Document` object naar het bestand te kopiëren (zorg dat u het `Document` object gebruikt dat door de `getProtectedDoc` methode is geretourneerd).

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (EJB-modus): Een beleid toepassen op een PDF-document met de Java API&quot;
* &quot;Snel starten (SOAP-modus): Een beleid toepassen op een PDF-document met de Java API&quot;

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een beleid toepassen op een PDF-document met behulp van de webservice-API {#apply-a-policy-to-a-pdf-document-using-the-web-service-api}

Een beleid toepassen op een PDF-document met behulp van de API voor documentbeveiliging (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Maak een `RightsManagementServiceClient` object met de standaardconstructor.
   * Maak een `RightsManagementServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service Forms (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `RightsManagementServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Een PDF-document ophalen.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om een PDF-document op te slaan waarop een beleid wordt toegepast.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. Bepaal de grootte van de bytearray door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Pas een bestaand beleid toe op het PDF-document.

   Pas een beleid toe op het PDF-document door de methode van het `RightsManagementServiceClient` `protectDocument` object aan te roepen en de volgende waarden door te geven:

   * Het `BLOB` object dat het PDF-document bevat waarop het beleid wordt toegepast.
   * Een tekenreekswaarde die de naam van het document aangeeft.
   * Een tekenreekswaarde die de naam opgeeft van de beleidsset waartoe het beleid behoort. U kunt een `null` waarde opgeven die resulteert in de gebruikte `MyPolicies` beleidsset.
   * Een tekenreekswaarde die de beleidsnaam opgeeft.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het gebruikersbeheerdomein van de gebruiker die de uitgever van het document is. Deze parameterwaarde is optioneel en kan null zijn (als deze parameter null is, moet de volgende parameterwaarde `null`) zijn.
   * Een tekenreekswaarde die de naam vertegenwoordigt van de canonieke naam van de gebruiker van de gebruikersmanager die de uitgever van het document is. Deze parameterwaarde is optioneel en kan null zijn (als deze parameter null is, moet de vorige parameterwaarde `null`) zijn.
   * Een `RMLocale` waarde die de waarde van de landinstelling opgeeft (bijvoorbeeld `RMLocale.en`).
   * Een parameter van de koordoutput die wordt gebruikt om de waarde van beleidsidentificatie op te slaan.
   * Een parameter van de koordoutput die wordt gebruikt om de beleid-beschermde herkenningstekenwaarde op te slaan.
   * Een parameter van de koordoutput die wordt gebruikt om het mime type (bijvoorbeeld, `application/pdf`) op te slaan.

   De `protectDocument` methode retourneert een `BLOB` object dat het met een beleid beveiligde PDF-document bevat.

1. Sla het PDF-document op.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het met een beleid beveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het `BLOB` object dat door de `protectDocument` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door de methode van het `System.IO.BinaryWriter` `Write` object aan te roepen en de bytearray door te geven.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (MTOM): Een beleid toepassen op een PDF-document met behulp van de webservice-API.&quot;
* &quot;Quick Start (SwaRef): Een beleid toepassen op een PDF-document met behulp van de webservice-API.&quot;

## Beleid verwijderen uit PDF-documenten {#removing-policies-from-pdf-documents}

U kunt een beleid verwijderen uit een document dat met een beleid is beveiligd om de beveiliging van het document te verwijderen. Dat wil zeggen dat als u het document niet langer wilt beschermen door een beleid. Als u een beleid-beschermd document met een nieuwer beleid wilt bijwerken, dan in plaats van het beleid te verwijderen en het bijgewerkte beleid toe te voegen, is het efficiënter om het beleid te schakelen.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om een beleid te verwijderen uit een PDF-document dat met een beleid is beveiligd:

1. Projectbestanden opnemen
1. Maak een API-object voor Document Security Client.
1. Hiermee haalt u een PDF-document op dat met een beleid is beveiligd.
1. Verwijder het beleid uit het PDF-document.
1. Sla het onbeveiligde PDF-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u via programmacode een bewerking met de documentbeveiligingsservice kunt uitvoeren, maakt u een clientobject van de documentbeveiligingsservice.

**Een met beleid beveiligd PDF-document ophalen**

U kunt een met een beleid beveiligd PDF-document ophalen om een beleid te verwijderen. Als u probeert een beleid te verwijderen uit een PDF-document dat niet wordt beveiligd door een beleid, veroorzaakt u een uitzondering.

**Het beleid verwijderen uit het PDF-document**

U kunt een beleid uit een beleid-beschermd PDF document verwijderen op voorwaarde dat een beheerder in de verbindingsmontages wordt gespecificeerd. Als dat niet het geval is, moet het beleid dat wordt gebruikt om een document te beveiligen de `SWITCH_POLICY` toestemming bevatten om een beleid uit een PDF-document te verwijderen. De gebruiker die is opgegeven in de verbindingsinstellingen voor AEM Forms, moet ook over deze bevoegdheid beschikken. Anders wordt een uitzondering gegenereerd.

**Het onbeveiligde PDF-document opslaan**

Nadat de documentbeveiligingsservice een beleid uit een PDF-document heeft verwijderd, kunt u het onbeveiligde PDF-document opslaan als een PDF-bestand.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beleid toepassen op PDF-documenten](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Een beleid verwijderen uit een PDF-document met de Java API {#remove-a-policy-from-a-pdf-document-using-the-java-api}

Een beleid verwijderen uit een PDF-document dat met een beleid is beveiligd, met de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `DocumentSecurityClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Hiermee haalt u een PDF-document op dat met een beleid is beveiligd.

   * Maak een `java.io.FileInputStream` object dat het met een beleid beveiligde PDF-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Verwijder het beleid uit het PDF-document.

   * Maak een `DocumentManager` object door de `DocumentSecurityClient` methode van het `getDocumentManager` object aan te roepen.
   * Verwijder een beleid uit het PDF-document door de methode van het `DocumentManager` object aan te roepen en het `removeSecurity` `com.adobe.idp.Document` object door te geven dat het met een beleid beveiligde PDF-document bevat. Deze methode retourneert een `com.adobe.idp.Document` object dat een onbeveiligd PDF-document bevat.

1. Sla het onbeveiligde PDF-document op.

   * Maak een `java.io.File` object en controleer of de bestandsextensie PDF is.
   * Roep de `Document` methode van het `copyToFile` object aan om de inhoud van het `Document` object naar het bestand te kopiëren (zorg dat u het `Document` object gebruikt dat door de `removeSecurity` methode is geretourneerd).

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP-modus): Een beleid verwijderen uit een PDF-document met de Java API&quot;

### Een beleid verwijderen met de webservice-API {#remove-a-policy-using-the-web-service-api}

Een beleid verwijderen uit een PDF-document dat met een beleid is beveiligd met de API voor documentbeveiliging (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Maak een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Maak een `DocumentSecurityServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `DocumentSecurityServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Hiermee haalt u een PDF-document op dat met een beleid is beveiligd.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het met een beleid beveiligde PDF-document op te slaan waaruit het beleid wordt verwijderd.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Verwijder het beleid uit het PDF-document.

   Verwijder het beleid uit het PDF-document door de `DocumentSecurityServiceClient` methode van het `removePolicySecurity` object aan te roepen en het `BLOB` object met het door een beleid beveiligde PDF-document door te geven. Deze methode retourneert een `BLOB` object dat een onbeveiligd PDF-document bevat.

1. Sla het onbeveiligde PDF-document op.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het onbeveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het `BLOB` object dat door de `removePolicySecurity` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` veld van het `MTOM` object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (MTOM): Een beleid uit een PDF-document verwijderen met de webservice-API&quot;
* &quot;Quick Start (SwaRef): Een beleid uit een PDF-document verwijderen met de webservice-API&quot;

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Toegang tot documenten intrekken {#revoking-access-to-documents}

U kunt de toegang tot een PDF-document dat met een beleid is beveiligd, intrekken. Hierdoor zijn alle kopieën van het document niet toegankelijk voor gebruikers. Wanneer een gebruiker een ingetrokken PDF-document probeert te openen, wordt deze doorgestuurd naar een opgegeven URL waar een gereviseerd document kan worden weergegeven. De URL waarnaar de gebruiker is omgeleid, moet via programmacode worden opgegeven. Wanneer u de toegang tot een document intrekt, wordt de wijziging van kracht wanneer de gebruiker opnieuw synchroniseert met de documentbeveiligingsservice door het document dat met een beleid is beveiligd online te openen.

De mogelijkheid om de toegang tot een document in te trekken biedt extra beveiliging. Stel dat er een nieuwere versie van een document beschikbaar is en dat u niet langer wilt dat iemand de verouderde versie bekijkt. In dit geval kan de toegang tot het oudere document worden ingetrokken en kan niemand het document bekijken tenzij de toegang wordt hersteld.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-5}

Voer de volgende stappen uit om een document dat met een beleid is beveiligd, in te trekken:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Hiermee haalt u een PDF-document op dat met een beleid is beveiligd.
1. Intrekken van het document dat met een beleid is beveiligd.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u programmatisch een Document Security-servicebewerking kunt uitvoeren, moet u een Document Security-service-clientobject maken.

**Een met beleid beveiligd PDF-document ophalen**

U moet een met een beleid beveiligd PDF-document ophalen om het te kunnen intrekken. U kunt een document dat al is ingetrokken of dat niet door een beleid beveiligd is, niet intrekken.

Als u de waarde van de licentie-id van het document weet dat met een beleid is beveiligd, hoeft u het PDF-document dat met een beleid is beveiligd, niet op te halen. In de meeste gevallen zult u het PDF-document echter moeten ophalen om de waarde van de licentie-id te verkrijgen.

**Intrekken van het document dat met een beleid is beveiligd**

Als u een document wilt intrekken dat met een beleid is beveiligd, geeft u de licentie-id op van het document dat met een beleid is beveiligd. Daarnaast kunt u de URL opgeven van een document dat de gebruiker kan bekijken wanneer hij of zij probeert het ingetrokken document te openen. Dat wil zeggen dat een verouderd document wordt ingetrokken. Wanneer een gebruiker het ingetrokken document probeert te openen, wordt een bijgewerkt document weergegeven in plaats van het ingetrokken document.

>[!NOTE]
>
>Als u een document probeert in te trekken dat al is ingetrokken, wordt een uitzondering gegenereerd.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beleid toepassen op PDF-documenten](protecting-documents-policies.md#applying-policies-to-pdf-documents)

[Toegang tot ingetrokken documenten opnieuw instellen](protecting-documents-policies.md#reinstating-access-to-revoked-documents)

### Toegang tot documenten intrekken met de Java API {#revoke-access-to-documents-using-the-java-api}

Toegang tot een met beleid beveiligd PDF-document intrekken met de API voor documentbeveiliging (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Een API-object voor documentbeveiliging maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `DocumentSecurityClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Een met beleid beveiligd PDF-document ophalen

   * Maak een `java.io.FileInputStream` object dat het met een beleid beveiligde PDF-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Intrekken van het document dat met een beleid is beveiligd

   * Maak een `DocumentManager` object door de `DocumentSecurityClient` methode van het `getDocumentManager` object aan te roepen.
   * Haal de waarde van de licentie-id van het document dat met een beleid is beveiligd, op door de `DocumentManager` methode van het `getLicenseId` object aan te roepen. Geef het `com.adobe.idp.Document` object door dat het document vertegenwoordigt dat met een beleid is beveiligd. Deze methode retourneert een tekenreekswaarde die de waarde van de licentie-id vertegenwoordigt.
   * Maak een `LicenseManager` object door de `DocumentSecurityClient` methode van het `getLicenseManager` object aan te roepen.
   * Intrekken van het document dat met een beleid is beveiligd door de methode van het `LicenseManager` `revokeLicense` object aan te roepen en de volgende waarden door te geven:

      * Een tekenreekswaarde die de waarde van de licentie-id van het document met beveiligingsbeleid opgeeft (geef de geretourneerde waarde van de `DocumentManager` methode van het `getLicenseId` object op).
      * Een statisch gegevenslid van de `License` interface dat de reden opgeeft om het document in te trekken. U kunt bijvoorbeeld opgeven `License.DOCUMENT_REVISED`.
      * Een `java.net.URL` waarde die de locatie opgeeft waar een gereviseerd document zich bevindt. Als u een gebruiker niet naar een andere URL wilt omleiden, kunt u doorgeven `null`.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP-modus): Een document intrekken met de Java API&quot;

### Toegang tot documenten intrekken met de webservice-API {#revoke-access-to-documents-using-the-web-service-api}

De toegang tot een met beleid beveiligd PDF-document intrekken met de API voor documentbeveiliging (webservice):

1. Projectbestanden opnemen

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een API-object voor documentbeveiliging maken

   * Maak een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Maak een `DocumentSecurityServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `DocumentSecurityServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Een met beleid beveiligd PDF-document ophalen

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om een met een beleid beveiligd PDF-document op te slaan dat wordt ingetrokken.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document dat met een beleid is beveiligd en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Intrekken van het document dat met een beleid is beveiligd

   * Haal de waarde van de licentieherkenningsteken van het document met beleidsbescherming op door de methode van het `DocumentSecurityServiceClient` object aan te roepen en het `getLicenseID` `BLOB` object door te geven dat het document met beleidsbeveiliging vertegenwoordigt. Deze methode retourneert een tekenreekswaarde die de licentie-id vertegenwoordigt.
   * Intrekken van het document dat met een beleid is beveiligd door de methode van het `DocumentSecurityServiceClient` `revokeLicense` object aan te roepen en de volgende waarden door te geven:

      * Een tekenreekswaarde die de waarde van de licentie-id van het document met beveiligingsbeleid opgeeft (geef de geretourneerde waarde van de `DocumentSecurityServiceService` methode van het `getLicenseId` object op).
      * Een statisch gegevenslid van de `Reason` opsomming dat de reden opgeeft om het document in te trekken. U kunt bijvoorbeeld opgeven `Reason.DOCUMENT_REVISED`.
      * Een `string` waarde die de URL-locatie opgeeft waarnaar een gereviseerd document zich bevindt. Als u een gebruiker niet naar een andere URL wilt omleiden, kunt u doorgeven `null`.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (MTOM): Een document intrekken met de webservice-API&quot;
* &quot;Quick Start (SwaRef): Een document intrekken met de webservice-API&quot;

**Zie ook**

[Beleid verwijderen uit Word-documenten](protecting-documents-policies.md#removing-policies-from-word-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Toegang tot ingetrokken documenten opnieuw instellen {#reinstating-access-to-revoked-documents}

U kunt de toegang tot een ingetrokken PDF-document opnieuw instellen, zodat alle kopieën van het ingetrokken document toegankelijk zijn voor gebruikers. Wanneer een gebruiker een hersteld document opent dat werd ingetrokken, kan de gebruiker het document bekijken.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-6}

Voer de volgende stappen uit om de toegang tot een ingetrokken PDF-document te herstellen:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Haal de licentie-id van het ingetrokken PDF-document op.
1. Toegang tot het ingetrokken PDF-document opnieuw instellen.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u programmatisch een Document Security-servicebewerking kunt uitvoeren, moet u een Document Security-service-clientobject maken. Als u de Java API gebruikt, maakt u een `DocumentSecurityClient` object. Als u de API voor documentbeveiliging gebruikt, maakt u een `DocumentSecurityServiceService` object.

**De licentie-id van het ingetrokken PDF-document ophalen**

U moet de licentie-id van het ingetrokken PDF-document ophalen om een ingetrokken PDF-document opnieuw in te stellen. Nadat u de waarde van de licentie-id hebt gekregen, kunt u een ingetrokken document opnieuw installeren. Als u probeert een document opnieuw in te voegen dat niet is ingetrokken, veroorzaakt u een uitzondering.

**Toegang tot het ingetrokken PDF-document opnieuw instellen**

Als u de toegang tot een ingetrokken PDF-document wilt herstellen, moet u de licentie-id van het ingetrokken document opgeven. Als u probeert toegang te herstellen tot een PDF-document dat niet is ingetrokken, veroorzaakt u een uitzondering.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beleid toepassen op PDF-documenten](protecting-documents-policies.md#applying-policies-to-pdf-documents)

[Toegang tot documenten intrekken](protecting-documents-policies.md#revoking-access-to-documents)

### Toegang tot ingetrokken documenten opnieuw instellen met de Java API {#reinstate-access-to-revoked-documents-using-the-java-api}

Toegang tot een ingetrokken document opnieuw instellen met de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `DocumentSecurityClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Haal de licentie-id van het ingetrokken PDF-document op.

   * Maak een `java.io.FileInputStream` object dat het ingetrokken PDF-document vertegenwoordigt met de constructor ervan en geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.
   * Maak een `DocumentManager` object door de `DocumentSecurityClient` methode van het `getDocumentManager` object aan te roepen.
   * Haal de waarde van de licentie-id van het ingetrokken document op door de methode van het `DocumentManager` object aan te roepen en het `getLicenseId` `com.adobe.idp.Document` object dat het ingetrokken document vertegenwoordigt door te geven. Deze methode retourneert een tekenreekswaarde die de licentie-id vertegenwoordigt.

1. Toegang tot het ingetrokken PDF-document opnieuw instellen.

   * Maak een `LicenseManager` object door de `DocumentSecurityClient` methode van het `getLicenseManager` object aan te roepen.
   * Herstel de toegang tot het ingetrokken PDF-document door de methode van het `LicenseManager` `unrevokeLicense` object aan te roepen en de waarde van de licentie-id van het ingetrokken document door te geven.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP-modus): Toegang tot een ingetrokken document opnieuw instellen met de webservice-API&quot;

### Toegang tot ingetrokken documenten opnieuw instellen met de webservice-API {#reinstate-access-to-revoked-documents-using-the-web-service-api}

Toegang tot een ingetrokken document opnieuw instellen met de API voor documentbeveiliging (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Maak een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Maak een `DocumentSecurityServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `DocumentSecurityServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Haal de licentie-id van het ingetrokken PDF-document op.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om een ingetrokken PDF-document op te slaan waartoe toegang wordt hersteld.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het ingetrokken PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Toegang tot het ingetrokken PDF-document opnieuw instellen.

   * Haal de waarde van de licentie-id van het ingetrokken document op door de methode van het `DocumentSecurityServiceClient` object aan te roepen en het `getLicenseID` `BLOB` object dat het ingetrokken document vertegenwoordigt door te geven. Deze methode retourneert een tekenreekswaarde die de licentie-id vertegenwoordigt.
   * Herstel de toegang tot het ingetrokken PDF-document door de methode van het `DocumentSecurityServiceClient` object aan te roepen en een tekenreekswaarde door te geven die de waarde van de licentie-id van het ingetrokken PDF-document opgeeft (geef de geretourneerde waarde van de `unrevokeLicense` methode van het `DocumentSecurityServiceClient` `getLicenseId` object door).

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (MTOM): Toegang tot een ingetrokken document opnieuw instellen met de webservice-API&quot;
* &quot;Quick Start (SwaRef): Toegang tot een ingetrokken document opnieuw instellen met de webservice-API&quot;

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Met beleid beveiligde PDF-documenten controleren {#inspecting-policy-protected-pdf-documents}

U kunt de API (Java en webservice) voor documentbeveiliging gebruiken om PDF-documenten die met een beleid zijn beveiligd, te inspecteren. Als u PDF-documenten inspecteert die met een beleid zijn beveiligd, wordt informatie over het met een beleid beveiligde PDF-document geretourneerd. U kunt bijvoorbeeld bepalen welk beleid is gebruikt om het document te beveiligen en op welke datum het document is beveiligd.

U kunt deze taak niet uitvoeren als uw versie van LiveCycle 8.x of een eerdere versie is. Ondersteuning voor het inspecteren van documenten die met een beleid zijn beveiligd, wordt toegevoegd aan AEM Forms. Als u probeert een document te inspecteren dat met een beleid is beveiligd met LiveCycle 8.x (of eerder), wordt een uitzondering gegenereerd.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-7}

Voer de volgende stappen uit om een PDF-document te inspecteren dat met een beleid is beveiligd:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Haal een document op dat met een beleid is beveiligd om te inspecteren.
1. Verkrijg informatie over het beleid-beschermde document.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**Een API-object voor documentbeveiliging maken**

Voordat u via programmacode een bewerking met de documentbeveiligingsservice kunt uitvoeren, maakt u een clientobject van de documentbeveiligingsservice. Als u de Java API gebruikt, maakt u een `RightsManagementClient` object. Als u de API voor documentbeveiliging gebruikt, maakt u een `RightsManagementServiceService` object.

**Een document ophalen dat met een beleid is beveiligd om te worden geïnspecteerd**

Als u een document wilt inspecteren dat met een beleid is beveiligd, haalt u het op. Als u een document probeert te inspecteren dat niet met een beleid wordt beveiligd of wordt ingetrokken, wordt een uitzondering gegenereerd.

**Document controleren**

Nadat u een document hebt opgehaald dat met een beleid is beveiligd, kunt u het controleren.

**Informatie opvragen over het document dat met een beleid is beveiligd**

Nadat u een PDF-document hebt gecontroleerd dat met een beleid is beveiligd, kunt u er informatie over verkrijgen. U kunt bijvoorbeeld bepalen welk beleid wordt gebruikt om het document te beveiligen.

Als u een document met een beleid beveiligt dat tot Mijn Beleid behoort en dan roept `RMInspectResult.getPolicysetName` of `RMInspectResult.getPolicysetId`, ongeldig is teruggekeerd.

Als het document wordt beveiligd met een beleid dat in een beleidsreeks (buiten Mijn Beleid) bevat dan `RMInspectResult.getPolicysetName` en geldige koorden `RMInspectResult.getPolicysetId` terugkeert.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Met beleid beveiligde PDF-documenten controleren met de Java API {#inspect-policy-protected-pdf-documents-using-the-java-api}

Controleer een PDF-document met beveiligingsbeleid met de API (Java) voor documentbeveiliging:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project. Zie [Including AEM Forms Java library files](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze bestanden.

1. Maak een API-object voor Document Security Client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie Verbindingseigenschappen [instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Maak een `RightsManagementClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Haal een document op dat met een beleid is beveiligd om te inspecteren.

   * Maak een `java.io.FileInputStream` object dat het met een beleid beveiligde PDF-document vertegenwoordigt met behulp van de constructor. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Controleer het document.

   * Maak een `DocumentManager` object door de `RightsManagementClient` methode van het `getDocumentManager` object aan te roepen.
   * Controleer het document dat met een beleid is beveiligd door de `LicenseManager` methode van het `inspectDocument` object aan te roepen. Geef het `com.adobe.idp.Document` object door dat het met een beleid beveiligde PDF-document bevat. Deze methode retourneert een `RMInspectResult` object dat informatie bevat over het document dat met een beleid is beveiligd.

1. Verkrijg informatie over het beleid-beschermde document.

   Om informatie over het beleid-beschermde document te verkrijgen, haal de aangewezen methode aan die `RMInspectResult` voorwerp behoort. Als u bijvoorbeeld de naam van het beleid wilt ophalen, roept u de `RMInspectResult` methode van het `getPolicyName` object aan.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP-modus): Met beleid beveiligde PDF-documenten controleren met de Java API&quot;

### Met beleid beveiligde PDF-documenten controleren met de webservice-API {#inspect-policy-protected-pdf-documents-using-the-web-service-api}

Controleer een PDF-document dat met een beleid is beveiligd met de API (webservice) voor documentbeveiliging:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Maak een `RightsManagementServiceClient` object met de standaardconstructor.
   * Maak een `RightsManagementServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `RightsManagementServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Haal een document op dat met een beleid is beveiligd om te inspecteren.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om een PDF-document op te slaan dat moet worden gecontroleerd.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Controleer het document.

   Controleer het document dat met een beleid is beveiligd door de `RightsManagementServiceClient` methode van het `inspectDocument` object aan te roepen. Geef het `BLOB` object door dat het met een beleid beveiligde PDF-document bevat. Deze methode retourneert een `RMInspectResult` object dat informatie bevat over het document dat met een beleid is beveiligd.

1. Verkrijg informatie over het beleid-beschermde document.

   Als u informatie wilt verkrijgen over het document dat met een beleid is beveiligd, krijgt u de waarde van het desbetreffende veld dat bij het `RMInspectResult` object hoort. Als u bijvoorbeeld de naam van het beleid wilt ophalen, moet u de waarde van het `RMInspectResult` veld van het `policyName` object ophalen.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (MTOM): Met beleid beveiligde PDF-documenten controleren met de webservice-API&quot;
* &quot;Quick Start (SwaRef): Met beleid beveiligde PDF-documenten controleren met de webservice-API&quot;

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Watermerken maken {#creating-watermarks}

Watermerken helpen de veiligheid van een document te waarborgen door het document op unieke wijze te identificeren en de inbreuk op het auteursrecht te controleren. U kunt bijvoorbeeld een watermerk maken en plaatsen dat op alle pagina&#39;s van een document de tekst Vertrouwelijk aangeeft. Nadat u een watermerk hebt gemaakt, kunt u dit opnemen in een beleid. Met andere woorden, u kunt het watermerkkenmerk van het beleid instellen met het nieuwe watermerk. Nadat een beleid met een watermerk is toegepast op een document, wordt het watermerk weergegeven in het document dat met een beleid is beveiligd.

>[!NOTE]
>
>Alleen gebruikers met beheerdersrechten voor documentbeveiliging kunnen watermerken maken. Dit betekent dat u een dergelijke gebruiker moet opgeven wanneer u verbindingsinstellingen definieert die vereist zijn om een Document Security Service Client-object te maken.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-8}

Voer de volgende stappen uit om een watermerk te maken:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Stel de kenmerken van de watermerken in.
1. Registreer het watermerk bij de Dienst van de Veiligheid van het Document.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u programmatisch een Document Security-servicebewerking kunt uitvoeren, moet u een Document Security-service-clientobject maken. Als u de Java API gebruikt, maakt u een `RightsManagementClient` object. Als u de API voor documentbeveiliging gebruikt, maakt u een `RightsManagementServiceService` object.

**De kenmerken van watermerken instellen**

Als u een nieuw watermerk wilt maken, moet u de kenmerken van het watermerk instellen. Het kenmerk name moet altijd worden gedefinieerd. Naast het kenmerk name moet u ten minste een van de volgende kenmerken instellen:

* Eigen tekst
* DateIncluded
* UserIdIncluded
* UserNameIncluded

De volgende tabel bevat een lijst met sleutel- en waardeparen die zijn vereist voor het maken van een watermerk met behulp van webservices.

<table>
 <thead>
  <tr>
   <th><p>Sleutelnaam</p></th>
   <th><p>Beschrijving</p></th>
   <th><p>Waarde</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p><code>WaterBackCmd:IS_USERNAME_ENABLED</code></p></td>
   <td><p>Hiermee wordt opgegeven of de gebruikersnaam van de gebruiker die het document opent, deel uitmaakt van het watermerk.</p></td>
   <td><p>Waar of Onwaar</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_USERID_ENABLED</code></p></td>
   <td><p>Hiermee wordt opgegeven of de identificatie van de gebruiker die het document opent, deel uitmaakt van het watermerk.</p></td>
   <td><p>Waar of Onwaar</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_CURRENTDATE_ENABLED</code></p></td>
   <td><p>Hiermee wordt opgegeven of de huidige datum deel uitmaakt van het watermerk.</p></td>
   <td><p>Waar of Onwaar</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_CUSTOMTEXT_ENABLED</code></p></td>
   <td><p>Als deze waarde true is, moet de waarde van de aangepaste tekst worden opgegeven met <code>WaterBackCmd:SRCTEXT</code>.</p></td>
   <td><p>Waar of Onwaar</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:OPACITY</code></p></td>
   <td><p>Hiermee bepaalt u de dekking van het watermerk. De standaardwaarde is 0,5 als deze niet is opgegeven.</p></td>
   <td><p>Een waarde tussen 0,0 en 1,0.</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:ROTATION</code></p></td>
   <td><p>Hiermee wordt de rotatie van het watermerk opgegeven. De standaardwaarde is 0 graden.</p></td>
   <td><p>Een waarde tussen 0 en 359.</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:SCALE</code></p></td>
   <td><p>Als deze waarde is opgegeven, <code>WaterBackCmd:IS_SIZE_ENABLED</code> moet deze aanwezig zijn en moet de waarde true zijn. Als dit kenmerk niet is opgegeven, wordt het standaardgedrag aan de pagina aangepast.</p></td>
   <td><p>Een waarde die groter is dan 0.0 en kleiner dan of gelijk aan 1.0.</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:HORIZ_ALIGN</code></p></td>
   <td><p>Geeft de horizontale uitlijning van het watermerk aan. De standaardwaarde is gecentreerd.</p></td>
   <td><p>links, midden of rechts</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:VERT_ALIGN</code></p></td>
   <td><p>Geeft de verticale uitlijning van het watermerk aan. De standaardwaarde is gecentreerd.</p></td>
   <td><p>boven, midden of onder</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_USE_BACKGROUND</code></p></td>
   <td><p>Hiermee wordt opgegeven of het watermerk een achtergrond is. De standaardwaarde is false.</p></td>
   <td><p>Waar of Onwaar</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:IS_SIZE_ENABLED</code></p></td>
   <td><p>True if a custom scale is specified. Als deze waarde true is, moet SCALE ook worden opgegeven. Als deze waarde false is, wordt de standaardwaarde op pagina toegepast.</p></td>
   <td><p>Waar of Onwaar</p></td>
  </tr>
  <tr>
   <td><p><code>WaterBackCmd:SRCTEXT</code></p></td>
   <td><p>Hiermee wordt de aangepaste tekst voor een watermerk opgegeven. Als deze waarde aanwezig is, <code>WaterBackCmd:IS_CUSTOMTEXT_ENABLED</code> moet deze ook aanwezig zijn en op true worden ingesteld.</p></td>
   <td><p>Waar of Onwaar</p></td>
  </tr>
 </tbody>
</table>

Voor alle watermerken moet een van de volgende kenmerken zijn gedefinieerd:

* `WaterBackCmd:IS_USERNAME_ENABLED`
* `WaterBackCmd:IS_USERID_ENABLED`
* `WaterBackCmd:IS_CURRENTDATE_ENABLED`
* `WaterBackCmd:IS_CUSTOMTEXT_ENABLED`

Alle andere kenmerken zijn optioneel.

**Het watermerk registreren**

Een nieuw watermerk moet bij de dienst van de Veiligheid van het Document worden geregistreerd alvorens het kan worden gebruikt. Nadat u een watermerk hebt geregistreerd, kunt u dit gebruiken binnen het beleid.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beleid toepassen op PDF-documenten](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Watermerken maken met de Java API {#create-watermarks-using-the-java-api}

Een watermerk maken met de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals de bestanden, op in het klassenpad van uw Java-project. `adobe-rightsmanagement-client.jar`

1. Maak een API-object voor Document Security Client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `RightsManagementClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. De kenmerken van het watermerk instellen

   * Maak een `Watermark` object door de statische `InfomodelObjectFactory` methode van het `createWatermark` object aan te roepen. Deze methode retourneert een `Watermark` object.
   * Stel het naamkenmerk van het watermerk in door de methode van het `Watermark` `setName` object aan te roepen en een tekenreekswaarde door te geven die de naam van het beleid aangeeft.
   * Stel het achtergrondkenmerk van het watermerk in door de methode van het `Watermark` object aan te roepen en door te geven `setBackground` `true`. Door dit kenmerk in te stellen, verschijnt het watermerk op de achtergrond van het document.
   * Stel het aangepaste tekstkenmerk van het watermerk in door de methode van het `Watermark` `setCustomText` object aan te roepen en een tekenreekswaarde door te geven die de tekst van het watermerk vertegenwoordigt.
   * Stel het kenmerk opacity van het watermerk in door de methode van het `Watermark` `setOpacity` object aan te roepen en een geheel-getalwaarde door te geven die het dekkingsniveau opgeeft. De waarde 100 geeft aan dat het watermerk volledig dekkend is en de waarde 0 geeft aan dat het watermerk volledig transparant is.

1. Registreer het watermerk.

   * Maak een `WatermarkManager` object door de `RightsManagementClient` methode van het `getWatermarkManager` object aan te roepen. Deze methode retourneert een `WatermarkManager` object.
   * Registreer het watermerk door de methode van het `WatermarkManager` object aan te roepen `registerWatermark` en het `Watermark` object door te geven dat het te registreren watermerk vertegenwoordigt. Deze methode retourneert een tekenreekswaarde die de identificatiewaarde van het watermerk vertegenwoordigt.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP-modus): Watermerken maken met de Java API&quot;

### Watermerken maken met de webservice-API {#create-watermarks-using-the-web-service-api}

Een watermerk maken met de API voor documentbeveiliging (webservice):

1. Maak een API-object voor Document Security Client.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Maak een `RightsManagementServiceClient` object met de standaardconstructor.
   * Maak een `RightsManagementServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `RightsManagementServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Stel de kenmerken van het watermerk in.

   * Maak een `WatermarkSpec` object door de `WatermarkSpec` constructor aan te roepen.
   * Stel de naam van het watermerk in door een tekenreekswaarde toe te wijzen aan het `WatermarkSpec` gegevenslid van het `name` object.
   * Stel het `id` kenmerk van het watermerk in door een tekenreekswaarde toe te wijzen aan het gegevenslid van het `WatermarkSpec` object `id` .
   * Maak een afzonderlijk `MyMapOf_xsd_string_To_xsd_anyType_Item` object voor elke watermerkeigenschap die u wilt instellen.
   * Stel de sleutelwaarde in door een waarde toe te wijzen aan het `MyMapOf_xsd_string_To_xsd_anyType_Item` gegevenslid van het `key` object (bijvoorbeeld `WaterBackCmd:OPACITY)`.
   * Stel de waarde in door een waarde toe te wijzen aan het `MyMapOf_xsd_string_To_xsd_anyType_Item` gegevenslid van het `value` object (bijvoorbeeld `.25`).
   * Create a `MyArrayOf_xsd_anyType` object. Roep voor elk `MyMapOf_xsd_string_To_xsd_anyType_Item` object de `MyArrayOf_xsd_anyType` methode van het `Add` object aan. Geef het `MyMapOf_xsd_string_To_xsd_anyType_Item` object door.
   * Wijs het `MyArrayOf_xsd_anyType` object toe aan het `WatermarkSpec` gegevenslid van het object `values` .

1. Registreer het watermerk.

   Registreer het watermerk door de methode van het `RightsManagementServiceClient` object aan te roepen `registerWatermark` en het `WatermarkSpec` object door te geven dat het te registreren watermerk vertegenwoordigt.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (MTOM): Een watermerk maken met de webservice-API&quot;
* &quot;Quick Start (SwaRef): Een watermerk maken met de webservice-API&quot;

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Watermerken wijzigen {#modifying-watermarks}

U kunt een bestaand watermerk wijzigen met de Java API voor documentbeveiliging of de webservice-API. Als u wijzigingen wilt aanbrengen in een bestaand watermerk, haalt u het watermerk op, wijzigt u de kenmerken ervan en werkt u het watermerk vervolgens bij op de server. Stel dat u een watermerk ophaalt en het kenmerk Dekking wijzigt. Voordat de wijziging van kracht wordt, moet u het watermerk bijwerken.

Wanneer u een watermerk wijzigt, is de wijziging van invloed op toekomstige documenten waarop het watermerk is toegepast. Dit betekent dat bestaande PDF-documenten die het watermerk bevatten, niet worden gewijzigd.

>[!NOTE]
>
>Alleen gebruikers met beheerdersrechten voor documentbeveiliging kunnen watermerken wijzigen. Dit betekent dat u een dergelijke gebruiker moet opgeven wanneer u verbindingsinstellingen definieert die vereist zijn om een Document Security Service Client-object te maken.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-9}

Voer de volgende stappen uit om een watermerk te wijzigen:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Haal het watermerk op dat u wilt wijzigen.
1. Stel de kenmerken van de watermerken in.
1. Werk het watermerk bij.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u programmatisch een Document Security-servicebewerking kunt uitvoeren, moet u een Document Security-service-clientobject maken. Als u de Java API gebruikt, maakt u een `DocumentSecurityClient` object. Als u de API voor documentbeveiliging gebruikt, maakt u een `DocumentSecurityServiceService` object.

**Het te wijzigen watermerk ophalen**

Als u een watermerk wilt wijzigen, moet u een bestaand watermerk ophalen. U kunt een watermerk terugwinnen door zijn naam te specificeren of door zijn herkenningstekenwaarde te specificeren.

**De kenmerken van watermerken instellen**

Als u een bestaand watermerk wilt wijzigen, wijzigt u de waarde van een of meer kenmerken van het watermerk. Wanneer u via programmacode een watermerk bijwerkt met behulp van een webservice, moet u alle kenmerken instellen die oorspronkelijk zijn ingesteld, zelfs als de waarde niet verandert. Stel bijvoorbeeld dat de volgende watermerkkenmerken zijn ingesteld: `WaterBackCmd:IS_USERID_ENABLED`, `WaterBackCmd:IS_CUSTOMTEXT_ENABLED`, `WaterBackCmd:OPACITY`en `WaterBackCmd:SRCTEXT`. Hoewel het enige kenmerk dat u wilt wijzigen, `WaterBackCmd:OPACITY`is, moet u de andere waarden instellen.

>[!NOTE]
>
>Wanneer u de Java API gebruikt om een watermerk te wijzigen, hoeft u niet alle kenmerken op te geven. Stel het watermerkkenmerk in dat u wilt wijzigen.

>[!NOTE]
>
>Zie Watermerken [maken voor meer informatie over de namen van watermerkkenmerken](protecting-documents-policies.md#creating-watermarks).

**Het watermerk bijwerken**

Nadat u de kenmerken van een watermerk hebt gewijzigd, moet u het watermerk bijwerken.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Watermerken maken](protecting-documents-policies.md#creating-watermarks)

### Watermerken wijzigen met de Java API {#modify-watermarks-using-the-java-api}

Een watermerk wijzigen met de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `DocumentSecurityClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Haal het watermerk op dat u wilt wijzigen.

   Maak een `WatermarkManager` object door de methode van het `DocumentSecurityClient` object aan te roepen `getWatermarkManager` en geef een tekenreekswaarde door die de naam van het watermerk aangeeft. Deze methode retourneert een `Watermark` object dat het watermerk vertegenwoordigt dat moet worden gewijzigd.

1. Stel de kenmerken van het watermerk in.

   Stel het kenmerk opacity van het watermerk in door de methode van het `Watermark` `setOpacity` object aan te roepen en een geheel-getalwaarde door te geven die het dekkingsniveau opgeeft. De waarde 100 geeft aan dat het watermerk volledig dekkend is en de waarde 0 geeft aan dat het watermerk volledig transparant is.

   >[!NOTE]
   >
   >In dit voorbeeld wordt alleen het kenmerk opacity gewijzigd.

1. Werk het watermerk bij.

   * Werk het watermerk bij door de methode van het `WatermarkManager` object aan te roepen `updateWatermark` en geef het `Watermark` object door waarvan het kenmerk is gewijzigd.

**Codevoorbeelden**

Zie de modus Snel starten (SOAP-modus) voor codevoorbeelden met de Document Security-service: Een watermerk wijzigen met de Java API-sectie.

### Watermerken wijzigen met de webservice-API {#modify-watermarks-using-the-web-service-api}

Wijzig een watermerk met de API voor documentbeveiliging (webservice):

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Maak een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Maak een `RightsManagementServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `DocumentSecurityServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Haal het watermerk op dat u wilt wijzigen.

   Haal het watermerk op dat u wilt wijzigen door de `DocumentSecurityServiceClient` methode van het `getWatermarkByName` object aan te roepen. Geef een tekenreekswaarde door die de naam van het watermerk aangeeft. Deze methode retourneert een `WatermarkSpec` object dat het watermerk vertegenwoordigt dat moet worden gewijzigd.

1. Stel de kenmerken van het watermerk in.

   * Maak een afzonderlijk `MyMapOf_xsd_string_To_xsd_anyType_Item` object voor elke watermerkeigenschap die moet worden bijgewerkt.
   * Stel de sleutelwaarde in door een waarde toe te wijzen aan het `MyMapOf_xsd_string_To_xsd_anyType_Item` gegevenslid van het `key` object (bijvoorbeeld `WaterBackCmd:OPACITY)`.
   * Stel de waarde in door een waarde toe te wijzen aan het `MyMapOf_xsd_string_To_xsd_anyType_Item` gegevenslid van het `value` object (bijvoorbeeld `.50`).
   * Create a `MyArrayOf_xsd_anyType` object. Roep voor elk `MyMapOf_xsd_string_To_xsd_anyType_Item` object de `MyArrayOf_xsd_anyType` methode van het `Add` object aan. Geef het `MyMapOf_xsd_string_To_xsd_anyType_Item` object door.
   * Wijs het `MyArrayOf_xsd_anyType` object toe aan het `WatermarkSpec` gegevenslid van het object `values` .

1. Werk het watermerk bij.

   Werk het watermerk bij door de methode van het `DocumentSecurityServiceClient` object aan te roepen `updateWatermark` en het `WatermarkSpec` object door te geven dat het te wijzigen watermerk vertegenwoordigt.

**Codevoorbeelden**

Zie het volgende snelle begin voor codevoorbeelden met gebruik van de Document Security-service:

* &quot;Snel starten (MTOM): Een watermerk wijzigen met de webservice-API&quot;

## Zoeken naar gebeurtenissen {#searching-for-events}

De dienst van het Beheer van Rechten volgt specifieke acties aangezien zij voorkomen, zoals het toepassen van een beleid op een document, het openen van een beleid-beschermd document, en het intrekken van toegang tot documenten. De controle van de gebeurtenis moet voor de dienst van het Beheer van Rechten worden toegelaten of de gebeurtenissen worden niet gevolgd.

Gebeurtenissen behoren tot een van de volgende categorieën:

* Beheerdersgebeurtenissen zijn handelingen die betrekking hebben op een beheerder, zoals het maken van een nieuwe beheerdersaccount.
* Documentgebeurtenissen zijn handelingen die betrekking hebben op een document, zoals het sluiten van een document dat met een beleid is beveiligd.
* Beleidsgebeurtenissen zijn acties die betrekking hebben op een beleid, zoals het maken van een nieuw beleid.
* De gebeurtenissen van de dienst zijn acties met betrekking tot de dienst van het Beheer van Rechten, zoals het synchroniseren met de gebruikersfolder.

U kunt zoeken naar specifieke gebeurtenissen met de API of webservice van Rights Management Java. Door naar gebeurtenissen te zoeken, kunt u taken uitvoeren, zoals het creëren van een logboekdossier van bepaalde gebeurtenissen.

>[!NOTE]
>
>Voor meer informatie over de dienst van het Beheer van Rechten, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-10}

Voer de volgende stappen uit om te zoeken naar een Rights Management-gebeurtenis:

1. Inclusief projectbestanden.
1. Maak een Rights Management Client API-object.
1. Geef de gebeurtenis op waarnaar u wilt zoeken.
1. Zoeken naar de gebeurtenis.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een Rights Management-client-API-object maken**

Alvorens u een de dienstverrichting van het Beheer van Rechten programmatically kunt uitvoeren, moet u een de dienstcliëntvoorwerp van het Beheer van Rechten tot stand brengen. Als u de Java API gebruikt, maakt u een `DocumentSecurityClient` object. Als u de webservice-API voor Rights Management gebruikt, maakt u een `DocumentSecurityServiceService` object.

**Geef de gebeurtenissen op waarnaar u wilt zoeken**

U moet de gebeurtenis opgeven waarnaar u wilt zoeken. U kunt bijvoorbeeld zoeken naar het beleid om een gebeurtenis te maken, die optreedt wanneer een nieuw beleid wordt gemaakt.

**Zoeken naar de gebeurtenis**

Nadat u de gebeurtenis hebt opgegeven waarnaar moet worden gezocht, kunt u de Rights Management Java API of de Rights Management-webservice-API gebruiken om naar de gebeurtenis te zoeken.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Zoeken naar gebeurtenissen met de Java API {#search-for-events-using-the-java-api}

U kunt naar gebeurtenissen zoeken met de Rights Management API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Een Rights Management-client-API-object maken

   Maak een `DocumentSecurityClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object door te geven dat verbindingseigenschappen bevat.

1. Geef de gebeurtenissen op waarnaar u wilt zoeken

   * Maak een `EventManager` object door de `DocumentSecurityClient` methode van het `getEventManager` object aan te roepen. Deze methode retourneert een `EventManager` object.
   * Maak een `EventSearchFilter` object door de constructor ervan aan te roepen.
   * Geef de gebeurtenis op waarnaar moet worden gezocht door de methode van het `EventSearchFilter` object aan te roepen en een lid van het type static data door te geven dat behoort tot de `setEventCode` `EventManager` klasse die de gebeurtenis vertegenwoordigt waarnaar moet worden gezocht. Als u bijvoorbeeld wilt zoeken naar het beleid, maakt u een gebeurtenis door `EventManager.POLICY_CREATE_EVENT`.

   >[!NOTE]
   >
   >U kunt aanvullende zoekcriteria definiëren door `EventSearchFilter` objectmethoden aan te roepen. Roep bijvoorbeeld de `setUserName` methode op om een gebruiker op te geven die aan de gebeurtenis is gekoppeld.

1. Zoeken naar de gebeurtenis

   Zoek naar de gebeurtenis door de methode van het `EventManager` voorwerp aan te halen `searchForEvents` en het `EventSearchFilter` voorwerp over te gaan dat de criteria van het gebeurtenisonderzoek bepaalt. Deze methode retourneert een array met `Event` objecten.

**Codevoorbeelden**

Voor codevoorbeelden die de dienst van het Beheer van Rechten gebruiken, zie het volgende Snel Begint:

* &quot;Snel starten (SOAP): Zoeken naar gebeurtenissen met de Java API&quot;

### Zoeken naar gebeurtenissen met de webservice-API {#search-for-events-using-the-web-service-api}

U kunt naar gebeurtenissen zoeken met de Rights Management API (webservice):

1. Projectbestanden opnemen

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een Rights Management-client-API-object maken

   * Maak een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Maak een `DocumentSecurityServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `DocumentSecurityServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Geef de gebeurtenissen op waarnaar u wilt zoeken

   * Maak een `EventSpec` object met de constructor ervan.
   * Geef het begin op van de tijdsperiode waarin de gebeurtenis heeft plaatsgevonden door het `EventSpec` gegevenslid van het `firstTime.date` object in te stellen op `DataTime` instantie die het begin van het datumbereik aangeeft wanneer de gebeurtenis heeft plaatsgevonden.
   * Wijs de waarde toe `true` aan het `EventSpec` gegevenslid van het `firstTime.dateSpecified` object.
   * Geef het einde van de tijdsperiode waarin de gebeurtenis heeft plaatsgevonden op door het `EventSpec` gegevenslid van het `lastTime.date` object in te stellen op `DataTime` instantie die het einde van het datumbereik vertegenwoordigt wanneer de gebeurtenis heeft plaatsgevonden.
   * Wijs de waarde toe `true` aan het `EventSpec` gegevenslid van het `lastTime.dateSpecified` object.
   * Stel de gebeurtenis waarnaar moet worden gezocht in door een tekenreekswaarde toe te wijzen aan het `EventSpec` `eventCode` gegevenslid van het object. In de volgende tabel worden de numerieke waarden weergegeven die u aan deze eigenschap kunt toewijzen:

   <table>
    <thead>
    <tr>
    <th><p>Het type Event</p></th>
    <th><p>Waarde</p></th>
    </tr>
    </thead>
    <tbody>
    <tr>
    <td><p><code>ALL_EVENTS</code></p></td>
    <td><p>999</p></td>
    </tr>
    <tr>
    <td><p><code>USER_CHANGE_PASSWORD_EVENT</code></p></td>
    <td><p>1000</p></td>
    </tr>
    <tr>
    <td><p><code>USER_REGISTER_EVENT</code></p></td>
    <td><p>1001</p></td>
    </tr>
    <tr>
    <td><p><code>USER_PREREGISTER_EVENT</code></p></td>
    <td><p>1002</p></td>
    </tr>
    <tr>
    <td><p><code>USER_ACTIVATE_EVENT</code></p></td>
    <td><p>1003</p></td>
    </tr>
    <tr>
    <td><p><code>USER_DEACTIVATE_EVENT</code></p></td>
    <td><p>1004</p></td>
    </tr>
    <tr>
    <td><p><code>USER_AUTHENTICATE_EVENT</code></p></td>
    <td><p>1005</p></td>
    </tr>
    <tr>
    <td><p><code>USER_AUTHENTICATE_DENY_EVENT </code></p></td>
    <td><p>1006</p></td>
    </tr>
    <tr>
    <td><p><code>USER_ACCOUNT_LOCK_EVENT</code></p></td>
    <td><p>1007</p></td>
    </tr>
    <tr>
    <td><p><code>USER_DELETE_EVENT </code></p></td>
    <td><p>1008</p></td>
    </tr>
    <tr>
    <td><p><code>USER_UPDATE_PROFILE_EVENT </code></p></td>
    <td><p>1009</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_VIEW_EVENT </code></p></td>
    <td><p>2000</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_PRINT_LOW_EVENT </code></p></td>
    <td><p>2001</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_PRINT_HIGH_EVENT </code></p></td>
    <td><p>2002</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_SIGN_EVENT </code></p></td>
    <td><p>2003</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_ADD_ANNOTATION_EVENT </code></p></td>
    <td><p>2004</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_FORM_FILL_EVENT </code></p></td>
    <td><p>2005</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_CLOSE_EVENT </code></p></td>
    <td><p>2006</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_MODIFY_EVENT </code></p></td>
    <td><p>2007</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_CHANGE_SECURITY_HANDLER_EVENT </code></p></td>
    <td><p>2008</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_SWITCH_POLICY_EVENT </code></p></td>
    <td><p>2009</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_REVOKE_EVENT </code></p></td>
    <td><p>2010</p></td>
    </tr>
    <tr>
    <td><p><code>$1</code></p></td>
    <td><p>2011</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_SECURE_EVENT </code></p></td>
    <td><p>2012</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_UNKNOWN_CLIENT_EVENT </code></p></td>
    <td><p>2013</p></td>
    </tr>
    <tr>
    <td><p><code>DOCUMENT_CHANGE_REVOKE_URL_EVENT </code></p></td>
    <td><p>2014</p></td>
    </tr>
    <tr>
    <td><p><code>POLICY_CHANGE_EVENT </code></p></td>
    <td><p>3000</p></td>
    </tr>
    <tr>
    <td><p><code>POLICY_ENABLE_EVENT </code></p></td>
    <td><p>3001</p></td>
    </tr>
    <tr>
    <td><p><code>POLICY_DISABLE_EVENT </code></p></td>
    <td><p>3002</p></td>
    </tr>
    <tr>
    <td><p><code>POLICY_CREATE_EVENT </code></p></td>
    <td><p>3003</p></td>
    </tr>
    <tr>
    <td><p><code>POLICY_DELETE_EVENT </code></p></td>
    <td><p>3004</p></td>
    </tr>
    <tr>
    <td><p><code>POLICY_CHANGE_OWNER_EVENT </code></p></td>
    <td><p>3005</p></td>
    </tr>
    <tr>
    <td><p><code>SERVER_CLIENT_SYNC_EVENT </code></p></td>
    <td><p>4000</p></td>
    </tr>
    <tr>
    <td><p><code>SERVER_SYNC_DIR_INFO_EVENT </code></p></td>
    <td><p>4001</p></td>
    </tr>
    <tr>
    <td><p><code>SERVER_SYNC_DIR_COMPLETE_EVENT </code></p></td>
    <td><p>4002</p></td>
    </tr>
    <tr>
    <td><p><code>SERVER_VERSION_MISMATCH_EVENT </code></p></td>
    <td><p>4003</p></td>
    </tr>
    <tr>
    <td><p><code>SERVER_CONFIG_CHANGE_EVENT </code></p></td>
    <td><p>4004</p></td>
    </tr>
    <tr>
    <td><p><code>SERVER_ENABLE_OFFLINE_ACCESS_EVENT </code></p></td>
    <td><p>4005</p></td>
    </tr>
    <tr>
    <td><p><code>ADMIN_ADD_EVENT </code></p></td>
    <td><p>5000</p></td>
    </tr>
    <tr>
    <td><p><code>ADMIN_DELETE_EVENT </code></p></td>
    <td><p>5001</p></td>
    </tr>
    <tr>
    <td><p><code>ADMIN_EDIT_EVENT </code></p></td>
    <td><p>5002</p></td>
    </tr>
    <tr>
    <td><p><code>ADMIN_ACTIVATE_EVENT </code></p></td>
    <td><p>5003</p></td>
    </tr>
    <tr>
    <td><p><code>ADMIN_DEACTIVATE_EVENT </code></p></td>
    <td><p>5004</p></td>
    </tr>
    <tr>
    <td><p><code>ERROR_DIRECTORY_SERVICE_EVENT </code></p></td>
    <td><p>6000</p></td>
    </tr>
    <tr>
    <td><p><code>CREATED_POLICYSET_EVENT</code></p></td>
    <td><p>7000</p></td>
    </tr>
    <tr>
    <td><p><code>DELETED_POLICYSET_EVENT</code></p></td>
    <td><p>7001</p></td>
    </tr>
    <tr>
    <td><p><code>MODIFIED_POLICYSET_EVENT</code></p></td>
    <td><p>7002</p></td>
    </tr>
    </tbody>
    </table>

1. Zoeken naar de gebeurtenis

   Zoek naar de gebeurtenis door de methode van het `DocumentSecurityServiceClient` voorwerp aan te halen `searchForEvents` en het `EventSpec` voorwerp over te gaan dat de gebeurtenis vertegenwoordigt waarvoor om en het maximumaantal resultaten te zoeken. Deze methode retourneert een `MyArrayOf_xsd_anyType` verzameling waarbij elk element een `AuditSpec` instantie is. Met behulp van een `AuditSpec` instantie kunt u informatie opvragen over de gebeurtenis, zoals de tijd dat deze heeft plaatsgevonden. De `AuditSpec` instantie bevat een `timestamp` gegevenslid dat deze informatie opgeeft.

**Codevoorbeelden**

Voor codevoorbeelden die de dienst van het Beheer van Rechten gebruiken, zie het volgende Snel Begint:

* &quot;Snel starten (MTOM): Zoeken naar gebeurtenissen met de webservice-API&quot;
* &quot;Quick Start (SwaRef): Zoeken naar gebeurtenissen met de webservice-API&quot;

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Beleid toepassen op Word-documenten {#applying-policies-to-word-documents}

Naast PDF-documenten ondersteunt de Rights Management-service extra documentindelingen, zoals een Microsoft Word-document (DOC-bestand) en andere Microsoft Office-bestandsindelingen. U kunt bijvoorbeeld een beleid toepassen op een Word-document om dit te beveiligen. Door een beleid op een document van Word toe te passen, beperkt u toegang tot het document. U kunt geen beleid op een document toepassen als het document reeds met een beleid wordt beveiligd.

U kunt het gebruik van een beleid-beschermd document van Word controleren nadat u het verspreidt. Dat wil zeggen dat u kunt zien hoe het document wordt gebruikt en wie het gebruikt. U kunt bijvoorbeeld zien wanneer iemand het document heeft geopend.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-11}

Voer de volgende stappen uit om een beleid toe te passen op een Word-document:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Hiermee wordt een Word-document opgehaald waarop een beleid wordt toegepast.
1. Pas een bestaand beleid op het document van Word toe.
1. Sla het door het beleid beveiligde Word-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u programmatisch een Document Security-servicebewerking kunt uitvoeren, moet u een Document Security-service-clientobject maken.

**Een Word-document ophalen**

U moet een Word-document opvragen om een beleid toe te passen. Nadat u een beleid op het document van Word toepast, worden de gebruikers beperkt wanneer het gebruiken van het document. Als het beleid bijvoorbeeld niet toestaat dat het document offline wordt geopend, moeten gebruikers online zijn om het document te openen.

**Een bestaand beleid toepassen op het Word-document**

Als u een beleid wilt toepassen op een Word-document, moet u verwijzen naar een bestaand beleid en opgeven tot welke beleidsset het beleid behoort. De gebruiker die de verbindingseigenschappen instelt, moet toegang hebben tot het opgegeven beleid. Als dat niet het geval is, treedt een uitzondering op.

**Het Word-document opslaan**

Nadat de documentbeveiligingsservice een beleid heeft toegepast op een Word-document, kunt u het met een beleid beveiligde Word-document opslaan als een DOC-bestand.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Toegang tot documenten intrekken](protecting-documents-policies.md#revoking-access-to-documents)

### Een beleid toepassen op een Word-document met de Java API {#apply-a-policy-to-a-word-document-using-the-java-api}

Een beleid toepassen op een Word-document met behulp van de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `DocumentSecurityClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Hiermee haalt u een Word-document op.

   * Maak een `java.io.FileInputStream` object dat het Word-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het Word-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Pas een bestaand beleid op het document van Word toe.

   * Maak een `DocumentManager` object door de `DocumentSecurityClient` methode van het `getDocumentManager` object aan te roepen.
   * Pas een beleid op het document van Word toe door de methode van het `DocumentManager` `protectDocument` voorwerp aan te halen en de volgende waarden over te gaan:

      * Het `com.adobe.idp.Document` object dat het Word-document bevat waarop het beleid wordt toegepast.
      * Een tekenreekswaarde die de naam van het document aangeeft.
      * Een tekenreekswaarde die de naam opgeeft van de beleidsset waartoe het beleid behoort. U kunt een `null` waarde opgeven die resulteert in de gebruikte `MyPolicies` beleidsset.
      * Een tekenreekswaarde die de beleidsnaam opgeeft.
      * Een tekenreekswaarde die de naam vertegenwoordigt van het gebruikersbeheerdomein van de gebruiker die de uitgever van het document is. Deze parameterwaarde is optioneel en kan null zijn (als deze parameter null is, moet de volgende parameterwaarde null zijn).
      * Een tekenreekswaarde die de naam vertegenwoordigt van de canonieke naam van de gebruiker van de gebruikersmanager die de uitgever van het document is. Deze parameterwaarde is optioneel en kan `null` (als deze parameter `null`is, moet de vorige parameterwaarde zijn `null`).
      * A `com.adobe.livecycle.rightsmanagement.Locale` die de scène vertegenwoordigt die voor het selecteren van het malplaatje van MS Office wordt gebruikt. Deze parameterwaarde is optioneel en u kunt deze opgeven `null`.

      De `protectDocument` methode retourneert een `RMSecureDocumentResult` object dat het door het beleid beveiligde Word-document bevat.


1. Sla het Word-document op.

   * Roep de `RMSecureDocumentResult` methode van het `getProtectedDoc` object aan om het door het beleid beveiligde Word-document op te halen. Deze methode retourneert een `com.adobe.idp.Document` object.
   * Maak een `java.io.File` object en zorg dat de bestandsextensie DOC is.
   * Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `Document` object naar het bestand te kopiëren (zorg dat u het `Document` object gebruikt dat door de `getProtectedDoc` methode is geretourneerd).

**Codevoorbeelden**

Zie het volgende snelle begin voor codevoorbeelden met gebruik van de Document Security-service:

* &quot;Snel starten (SOAP-modus): Een beleid toepassen op een Word-document met de Java API&quot;

### Een beleid toepassen op een Word-document met behulp van de webservice-API {#apply-a-policy-to-a-word-document-using-the-web-service-api}

Pas een beleid op een document van Word toe door de Veiligheid API van het Document (Webdienst) te gebruiken:

1. Inclusief projectbestanden.

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/DocumentSecurityService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Maak een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Maak een `DocumentSecurityServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `DocumentSecurityServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Hiermee haalt u een Word-document op.

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om een Word-document op te slaan waarop een beleid wordt toegepast.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het Word-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. Bepaal de grootte van de bytearray door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de `System.IO.FileStream` `Read` methode van het object aan te roepen. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Pas een bestaand beleid op het document van Word toe.

   Pas een beleid op het document van Word toe door de methode van het `DocumentSecurityServiceClient` `protectDocument` voorwerp aan te halen en de volgende waarden over te gaan:

   * Het `BLOB` object dat het Word-document bevat waarop het beleid wordt toegepast.
   * Een tekenreekswaarde die de naam van het document aangeeft.
   * Een tekenreekswaarde die de naam opgeeft van de beleidsset waartoe het beleid behoort. U kunt een `null` waarde opgeven die resulteert in de gebruikte `MyPolicies` beleidsset.
   * Een tekenreekswaarde die de beleidsnaam opgeeft.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het gebruikersbeheerdomein van de gebruiker die de uitgever van het document is. Deze parameterwaarde is optioneel en kan null zijn (als deze parameter null is, moet de volgende parameterwaarde `null`) zijn.
   * Een tekenreekswaarde die de naam vertegenwoordigt van de canonieke naam van de gebruiker van de gebruikersmanager die de uitgever van het document is. Deze parameterwaarde is optioneel en kan null zijn (als deze parameter null is, moet de vorige parameterwaarde `null`) zijn.
   * Een `RMLocale` waarde die de waarde van de landinstelling opgeeft (bijvoorbeeld `RMLocale.en`).
   * Een parameter van de koordoutput die wordt gebruikt om de waarde van beleidsidentificatie op te slaan.
   * Een parameter van de koordoutput die wordt gebruikt om de beleid-beschermde herkenningstekenwaarde op te slaan.
   * Een parameter van de koordoutput die wordt gebruikt om het mime type (bijvoorbeeld, `application/doc`) op te slaan.

   De `protectDocument` methode retourneert een `BLOB` object dat het door het beleid beveiligde Word-document bevat.

1. Sla het Word-document op.

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het met een beleid beveiligde Word-document vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het `BLOB` object dat door de `protectDocument` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` `MTOM` gegevenslid van het object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.
   * Schrijf de inhoud van de bytearray naar een Word-bestand door de methode van het `System.IO.BinaryWriter` object aan te roepen `Write` en de bytearray door te geven.

**Codevoorbeelden**

Zie het volgende snelle begin voor codevoorbeelden met gebruik van de Document Security-service:

* &quot;Snel starten (MTOM): Een beleid toepassen op een Word-document met behulp van de webservice-API&quot;

## Beleid verwijderen uit Word-documenten {#removing-policies-from-word-documents}

U kunt een beleid uit een beleid-beschermd document van Word verwijderen om veiligheid uit het document te verwijderen. Dat wil zeggen dat als u het document niet langer wilt beschermen door een beleid. Als u een beleid-beschermd document van Word met een nieuwer beleid wilt bijwerken, dan in plaats van het verwijderen van het beleid en het toevoegen van het bijgewerkte beleid, is het efficiënter om het beleid te schakelen.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie de Verwijzing van de [Diensten voor AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-12}

Voer de volgende stappen uit om een beleid te verwijderen uit een Word-document dat met een beleid is beveiligd:

1. Projectbestanden opnemen
1. Maak een API-object voor Document Security Client.
1. Hiermee haalt u een Word-document op dat met een beleid is beveiligd.
1. Verwijder het beleid uit het Word-document.
1. De onbeveiligde Word-documenten opslaan

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u via programmacode een bewerking met de documentbeveiligingsservice kunt uitvoeren, maakt u een clientobject van de documentbeveiligingsservice.

**Een met beleid beveiligd Word-document ophalen**

U moet een beleid-beschermd document van Word terugwinnen om een beleid te verwijderen. Als u probeert om een beleid uit een document van Word te verwijderen dat niet door een beleid wordt beschermd, zult u een uitzondering veroorzaken.

**Het beleid verwijderen uit het Word-document**

U kunt een beleid uit een beleid-beschermd document van Word verwijderen op voorwaarde dat een beheerder in de verbindingsmontages wordt gespecificeerd. Als niet, dan moet het beleid dat wordt gebruikt om een document te beveiligen de `SWITCH_POLICY` toestemming bevatten om een beleid uit een document van Word te verwijderen. De gebruiker die is opgegeven in de verbindingsinstellingen voor AEM Forms, moet ook over deze bevoegdheid beschikken. Anders wordt een uitzondering gegenereerd.

**Het onbeveiligde Word-document opslaan**

Nadat de documentbeveiligingsservice een beleid uit een Word-document heeft verwijderd, kunt u het onbeveiligde Word-document opslaan als een DOC-bestand.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beleid toepassen op Word-documenten](protecting-documents-policies.md#applying-policies-to-word-documents)

### Een beleid verwijderen uit een Word-document met de Java API {#remove-a-policy-from-a-word-document-using-the-java-api}

Verwijder een beleid uit een beleid-beschermd document van Word door de Veiligheid API van het Document (Java) te gebruiken:

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Een API-object voor documentbeveiliging maken

   * Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Maak een `RightsManagementClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven.

1. Een met beleid beveiligd Word-document ophalen

   * Maak een `java.io.FileInputStream` object dat staat voor het door een beleid beveiligde Word-document met behulp van de constructor en geef een tekenreekswaarde door die de locatie van het Word-document aangeeft.
   * Maak een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en het `java.io.FileInputStream` object door te geven.

1. Het beleid verwijderen uit het Word-document

   * Maak een `DocumentManager` object door de `RightsManagementClient` methode van het `getDocumentManager` object aan te roepen.
   * Verwijder een beleid uit het document van Word door de methode van de `DocumentManager` objecten aan te halen en het `removeSecurity` `com.adobe.idp.Document` voorwerp over te gaan dat het beleid-beschermde document van Word bevat. Deze methode retourneert een `com.adobe.idp.Document` object dat een onbeveiligd Word-document bevat.

1. Het onbeveiligde Word-document opslaan

   * Maak een `java.io.File` object en zorg dat de bestandsextensie DOC is.
   * Roep de `Document` methode van het `copyToFile` object aan om de inhoud van het `Document` object naar het bestand te kopiëren (zorg dat u het `Document` object gebruikt dat door de `removeSecurity` methode is geretourneerd).

**Codevoorbeelden**

Zie het volgende snelle begin voor codevoorbeelden met gebruik van de Document Security-service:

* &quot;Snel starten (SOAP-modus): Een beleid verwijderen uit een Word-document met de Java API&quot;

### Een beleid verwijderen uit een Word-document met de webservice-API {#remove-a-policy-from-a-word-document-using-the-web-service-api}

Verwijder een beleid uit een beleid-beschermd document van Word door de Veiligheid API van het Document (Webdienst te gebruiken:

1. Projectbestanden opnemen

   Creeer een project van Microsoft .NET dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` door het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een API-object voor documentbeveiliging maken

   * Maak een `RightsManagementServiceClient` object met de standaardconstructor.
   * Maak een `RightsManagementServiceClient.Endpoint.Address` object met de `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de service AEM Forms (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft het `lc_version` kenmerk niet te gebruiken. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Maak een `System.ServiceModel.BasicHttpBinding` object door de waarde van het `RightsManagementServiceClient.Endpoint.Binding` veld op te halen. Kiezen naar de geretourneerde waarde `BasicHttpBinding`.
   * Stel het `System.ServiceModel.BasicHttpBinding` veld van het `MessageEncoding` object in op `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam voor AEM-formulieren toe aan het veld `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * Wijs de bijbehorende wachtwoordwaarde aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * Wijs de constante waarde toe `HttpClientCredentialType.Basic` aan het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.
   * Wijs de constante waarde toe `BasicHttpSecurityMode.TransportCredentialOnly` aan het veld `BasicHttpBindingSecurity.Security.Mode`.


1. Een met beleid beveiligd Word-document ophalen

   * Maak een `BLOB` object met de constructor ervan. Het `BLOB` object wordt gebruikt om het door een beleid beveiligde Word-document op te slaan waaruit het beleid wordt verwijderd.
   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het Word-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van het `System.IO.FileStream` object wordt opgeslagen. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` eigenschap van het `Length` object op te halen.
   * Vul de bytearray met streamgegevens door de methode van het `System.IO.FileStream` `Read` object aan te roepen en de bytearray, de startpositie en de lengte van de stream door te geven om te lezen.
   * Vul het `BLOB` object door het `MTOM` veld ervan toe te wijzen met de inhoud van de bytearray.

1. Het beleid verwijderen uit het Word-document

   Verwijder het beleid uit het document van Word door de methode van de `RightsManagementServiceClient` objecten aan te halen en het `removePolicySecurity` `BLOB` voorwerp over te gaan dat het beleid-beschermde document van Word bevat. Deze methode retourneert een `BLOB` object dat een onbeveiligd Word-document bevat.

1. Het onbeveiligde Word-document opslaan

   * Maak een `System.IO.FileStream` object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het onbeveiligde Word-document vertegenwoordigt.
   * Maak een bytearray met de gegevensinhoud van het `BLOB` object dat door de `removePolicySecurity` methode is geretourneerd. Vul de bytearray met de waarde van het `BLOB` veld van het `MTOM` object.
   * Maak een `System.IO.BinaryWriter` object door de constructor ervan aan te roepen en het `System.IO.FileStream` object door te geven.

**Codevoorbeelden**

Zie het volgende snelle begin voor codevoorbeelden met gebruik van de Document Security-service:

* &quot;Snel starten (MTOM): Een beleid verwijderen uit een Word-document met de webservice-API&quot;

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
