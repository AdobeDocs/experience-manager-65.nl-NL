---
title: Documenten beveiligen met beleid
description: Met de Document Security-service kunt u de instellingen voor vertrouwelijkheid dynamisch toepassen op Adobe PDF-documenten en de controle over de documenten behouden. De dienst van de Veiligheid van het Document laat de gebruikers ook toe om controle over te handhaven hoe de ontvangers het beleid-beschermde document van de PDF gebruiken.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
exl-id: ff42579e-6aaf-433d-8b5d-9e9dd0957250
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '15394'
ht-degree: 0%

---

# Documenten beveiligen met beleid {#protecting-documents-with-policies}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

**Informatie over de Document Security Service**

Met de Document Security-service kunnen gebruikers op dynamische wijze instellingen voor vertrouwelijkheid toepassen op Adobe PDF-documenten en de controle houden over de documenten, ongeacht de mate waarin deze worden verspreid.

De dienst van de Veiligheid van het Document verhindert informatie zich voorbij het bereik van de gebruiker te verspreiden door de gebruikers toe te laten om controle over te houden hoe de ontvangers het beleid-beschermde document van de PDF gebruiken. Een gebruiker kan opgeven wie een document mag openen, hoe hij het kan gebruiken en het document na de verspreiding ervan controleren. Een gebruiker kan ook dynamisch de toegang tot een document beheren dat met een beleid is beveiligd en kan de toegang tot het document zelfs dynamisch intrekken.

De service Documentbeveiliging beschermt ook andere bestandstypen, zoals Microsoft Word-bestanden (DOC-bestanden). U kunt de client-API voor documentbeveiliging gebruiken om met deze bestandstypen te werken. De volgende versies worden ondersteund:

* Microsoft Office 2003-bestanden (DOC-, XLS-, PPT-bestanden)
* Microsoft Office 2007-bestanden (DOCX-, XLSX-, PPTX-bestanden)
* PTC Pro/E-bestanden

Voor de duidelijkheid bespreken de volgende twee secties hoe te met de documenten van Word te werken:

* [Beleid toepassen op Word-documenten](protecting-documents-policies.md#applying-policies-to-word-documents)
* [Beleid verwijderen uit Word-documenten](protecting-documents-policies.md#removing-policies-from-word-documents)

U kunt deze taken uitvoeren met de documentbeveiligingsservice:

* Beleid maken. Zie voor meer informatie [Beleid maken](protecting-documents-policies.md#creating-policies).
* Beleid wijzigen. Zie voor meer informatie [Beleid wijzigen](protecting-documents-policies.md#modifying-policies).
* Beleid verwijderen. Zie voor meer informatie [Beleid verwijderen](protecting-documents-policies.md#deleting-policies).
* Beleid toepassen op PDF-documenten. Zie voor meer informatie [Beleid toepassen op PDF-documenten](protecting-documents-policies.md#applying-policies-to-pdf-documents).
* Beleid verwijderen uit PDF-documenten. Zie voor meer informatie [Beleid verwijderen uit PDF-documenten](protecting-documents-policies.md#removing-policies-from-pdf-documents).
* Met een beleid beveiligde documenten van Inspect. Zie voor meer informatie [Met beleid beveiligde PDF-documenten controleren](protecting-documents-policies.md#inspecting-policy-protected-pdf-documents).
* Toegang tot PDF-documenten intrekken. Zie voor meer informatie [Toegang tot documenten intrekken](protecting-documents-policies.md#revoking-access-to-documents).
* Toegang tot ingetrokken documenten opnieuw instellen. Zie voor meer informatie [Toegang tot ingetrokken documenten opnieuw instellen](protecting-documents-policies.md#reinstating-access-to-revoked-documents).
* Watermerken maken. Zie voor meer informatie [Watermerken maken](protecting-documents-policies.md#creating-watermarks).
* Zoeken naar gebeurtenissen. Zie voor meer informatie [Zoeken naar gebeurtenissen](protecting-documents-policies.md#searching-for-events).

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

## Beleid maken {#creating-policies}

U kunt beleid programmatisch maken met de Java API voor documentbeveiliging of de webservice-API. A *beleid* is een verzameling gegevens die beveiligingsinstellingen voor documenten, geautoriseerde gebruikers en gebruiksrechten bevat. U kunt een willekeurig aantal beleidsregels maken en opslaan met de beveiligingsinstellingen die geschikt zijn voor verschillende situaties en gebruikers.

Het beleid laat u toe om deze taken uit te voeren:

* Geef de personen op die het document kunnen openen. Ontvangers kunnen tot uw organisatie behoren of zich buiten uw organisatie bevinden.
* Geef op hoe ontvangers het document kunnen gebruiken. U kunt de toegang tot verschillende Acrobat- en Adobe Reader-functies beperken. Deze functies omvatten de mogelijkheid om tekst af te drukken en te kopiëren, handtekeningen toe te voegen en opmerkingen toe te voegen aan een document.
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
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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
* namespace.jar (als AEM Forms wordt opgesteld op JBoss)
* jaxb-api.jar (als AEM Forms wordt geïmplementeerd op JBoss)
* jaxb-impl.jar (als AEM Forms wordt geïmplementeerd op JBoss)
* jaxb-libs.jar (als AEM Forms wordt geïmplementeerd op JBoss)
* jaxb-xjc.jar (als AEM Forms wordt geïmplementeerd op JBoss)
* relaxngDatatype.jar (als AEM Forms wordt geïmplementeerd op JBoss)
* xsdlib.jar (als AEM Forms wordt geïmplementeerd op JBoss)
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar
* adobe-utilities.jar
* jbossall-client.jar (gebruik een ander JAR-bestand als AEM Forms niet is geïmplementeerd op JBoss)

Voor informatie over de locatie van deze JAR-bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

**Een API-object voor documentbeveiliging maken**

Voordat u via programmacode een bewerking met de documentbeveiligingsservice kunt uitvoeren, maakt u een clientobject van de documentbeveiligingsservice.

**De kenmerken van het beleid instellen**

Stel beleidskenmerken in om een beleid te maken. Een verplicht kenmerk is de beleidsnaam. Beleidsnamen moeten uniek zijn voor elke beleidsset. Een beleidsset is gewoon een verzameling van beleidsmaatregelen. Er kunnen twee beleid met dezelfde naam zijn als het beleid tot afzonderlijke beleidsreeksen behoort. Twee beleid binnen één beleidsset kan echter niet dezelfde beleidsnaam hebben.

Een ander nuttig kenmerk dat moet worden ingesteld, is de geldigheidsperiode. Een geldigheidsperiode is de periode waarin een document dat onder een beleid valt, toegankelijk is voor geautoriseerde ontvangers. Als u dit kenmerk niet instelt, is het beleid altijd geldig.

U kunt een geldigheidsperiode instellen op een van de volgende opties:

* Een bepaald aantal dagen dat het document toegankelijk is vanaf het moment dat het document wordt gepubliceerd
* Een einddatum waarna het document niet toegankelijk is
* Een specifiek datumbereik waarvoor het document toegankelijk is
* Altijd geldig

U kunt alleen een begindatum opgeven, wat betekent dat het beleid geldig is na de begindatum. Als u slechts een einddatum specificeert, is het beleid geldig tot de einddatum. Er wordt echter een uitzondering gegenereerd als zowel een begindatum als een einddatum niet zijn gedefinieerd.

Wanneer u kenmerken instelt die tot een beleid behoren, kunt u ook versleutelingsinstellingen instellen. Deze versleutelingsinstellingen zijn van invloed wanneer het beleid wordt toegepast op een document. U kunt de volgende versleutelingswaarden opgeven:

* **AES256**: Vertegenwoordigt het AES-versleutelingsalgoritme met een 256-bits sleutel.
* **AES128**: Vertegenwoordigt het AES-versleutelingsalgoritme met een 128-bits sleutel.
* **NoEncryption:** Vertegenwoordigt geen encryptie.

Wanneer u de opdracht `NoEncryption` kunt u de optie `PlaintextMetadata` optie voor `false`. Wanneer u dit probeert, wordt een uitzondering gegenereerd.

>[!NOTE]
>
>Voor informatie over andere kenmerken die u kunt instellen, raadpleegt u de `Policy` interfacebeschrijving in de [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `DocumentSecurityClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Stel de kenmerken van het beleid in.

   * Een `Policy` door het object aan te roepen `InfomodelObjectFactory` statisch object `createPolicy` methode. Deze methode retourneert een `Policy` object.
   * Stel het naamkenmerk van het beleid in door het `Policy` object `setName` methode en het overgaan van een koordwaarde die de beleidsnaam specificeert.
   * Stel de beschrijving van het beleid in door het `Policy` object `setDescription` methode en het overgaan van een koordwaarde die de beschrijving van het beleid specificeert.
   * Geef de beleidsset op waartoe het nieuwe beleid behoort door de `Policy` object `setPolicySetName` methode en het overgaan van een koordwaarde die de naam van de beleidsreeks specificeert. (U kunt `null` voor deze parameterwaarde die ertoe leidt dat het beleid wordt toegevoegd aan *Mijn beleid* beleidsset.)
   * Maak de geldigheidsperiode van het beleid door de `InfomodelObjectFactory` statisch object `createValidityPeriod` methode. Deze methode retourneert een `ValidityPeriod` object.
   * Stel het aantal dagen in waarvoor een document dat met een beleid is beveiligd, toegankelijk is door het `ValidityPeriod` object `setRelativeExpirationDays` methode en het overgaan van een geheelwaarde die het aantal dagen specificeert.
   * Stel de geldigheidsperiode van het beleid in door de `Policy` object `setValidityPeriod` en het doorgeven van de `ValidityPeriod` object.

1. Maak een beleidsvermelding.

   * Maak een beleidsitem door het `InfomodelObjectFactory` statisch object `createPolicyEntry` methode. Deze methode retourneert een `PolicyEntry` object.
   * Geef de bevoegdheden van het beleid op door de `InfomodelObjectFactory` statisch object `createPermission` methode. Geef een statisch gegevenslid door dat tot de `Permission` interface die de toestemming vertegenwoordigt. Deze methode retourneert een `Permission` object. Bijvoorbeeld, om de toestemming toe te voegen die gebruikers toelaat om gegevens van een beleid-beschermd document van de PDF te kopiëren, ga over `Permission.COPY`. (Herhaal deze stap voor elke machtiging die u wilt toevoegen.)
   * Voeg de toestemming aan de beleidsingang toe door aan te halen `PolicyEntry` object `addPermission` en het doorgeven van de `Permission` object. (Herhaal deze stap voor elke stap `Permission` -object dat u hebt gemaakt).
   * Creeer het beleidshoofd door het `InfomodelObjectFactory` statisch object `createSpecialPrincipal` methode. Geef een gegevenslid door dat tot de `InfomodelObjectFactory` object dat de principal vertegenwoordigt. Deze methode retourneert een `Principal` object. Als u bijvoorbeeld de uitgever van het document als hoofd wilt toevoegen, geeft u `InfomodelObjectFactory.PUBLISHER_PRINCIPAL`.
   * Voeg het hoofd aan de beleidsingang toe door te roepen `PolicyEntry` object `setPrincipal`en het doorgeven van de `Principal` object.
   * Voeg de beleidsingang aan het beleid toe door aan te halen `Policy` object `addPolicyEntry` en het doorgeven van de `PolicyEntry` object.

1. Registreer het beleid.

   * Een `PolicyManager` door het object aan te roepen `DocumentSecurityClient` object `getPolicyManager` methode.
   * Registreer het beleid door de `PolicyManager` object `registerPolicy` en geeft de volgende waarden door:

      * De `Policy` object dat staat voor het te registreren beleid.

   * Een tekenreekswaarde die staat voor de beleidsset waartoe het beleid behoort.

   Als u binnen de verbindingsinstellingen een beheerdersaccount voor AEM formulieren gebruikt om de `DocumentSecurityClient` -object, geeft u vervolgens de naam van de beleidsset op wanneer u het `registerPolicy` methode. Als u een `null` waarde voor de beleidsreeks, wordt het beleid gecreeerd in de beheerders *Mijn beleid* beleidsset.

   Als u een gebruiker van de Veiligheid van het Document binnen verbindingsmontages gebruikt, dan kunt u overbelaste aanhalen `registerPolicy` methode die alleen het beleid accepteert. U hoeft dus geen naam voor de beleidsset op te geven. Het beleid wordt echter toegevoegd aan de benoemde beleidsset *Mijn beleid*. Als u het nieuwe beleid niet aan deze beleidsreeks wilt toevoegen, dan specificeer een naam van de beleidsreeks wanneer u aanhaalt `registerPolicy` methode.

   >[!NOTE]
   >
   >Verwijs bij het maken van een beleid naar een bestaande beleidsset. Als u een beleidsset opgeeft die niet bestaat, wordt een uitzondering gegenereerd.

Zie het volgende voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP modus): beleid maken met de Java API&quot;

### Beleid maken met de webservice-API {#create-a-policy-using-the-web-service-api}

Een beleid maken met de API voor documentbeveiliging (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Een `DocumentSecurityServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `RightsManagementServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Stel de kenmerken van het beleid in.

   * Een `PolicySpec` object met behulp van de constructor.
   * Stel de naam van het beleid in door een tekenreekswaarde toe te wijzen aan de `PolicySpec` object `name` lid.
   * Stel de beschrijving van het beleid in door een tekenreekswaarde toe te wijzen aan de `PolicySpec` object `description` lid.
   * Geef de beleidsset op waartoe het beleid behoort door een tekenreekswaarde toe te wijzen aan de `PolicySpec` object `policySetName` lid. Geef een bestaande naam voor een beleidsset op. (U kunt `null` voor deze parameterwaarde die ertoe leidt dat het beleid wordt toegevoegd aan *Mijn beleid*.)
   * Stel de offline leaseperiode van het beleid in door een geheel-getalwaarde toe te wijzen aan de `PolicySpec` object `offlineLeasePeriod` lid.
   * Stel de `PolicySpec` object `policyXml` gegevenslid met een tekenreekswaarde die PDRL XML-gegevens vertegenwoordigt. Om deze taak uit te voeren, creeer .NET `StreamReader` object met behulp van de constructor. Geef de locatie van een PDRL XML-bestand dat het beleid vertegenwoordigt, door aan de `StreamReader` constructor. Roep vervolgens het `StreamReader` object `ReadLine` en wijs de geretourneerde waarde toe aan een tekenreeksvariabele. Doorlopen `StreamReader` tot de `ReadLine` methode retourneert null. Wijs de tekenreeksvariabele toe aan de `PolicySpec` object `policyXml` lid.

1. Maak een beleidsvermelding.

   Het is niet nodig om een beleidsitem te maken wanneer u een beleid maakt met de webservice-API voor documentbeveiliging. Het beleidsitem wordt gedefinieerd in het PDF-document.

1. Registreer het beleid.

   Registreer het beleid door de `DocumentSecurityServiceClient` object `registerPolicy` en geeft de volgende waarden door:

   * De `PolicySpec` object dat staat voor het te registreren beleid.
   * Een tekenreekswaarde die staat voor de beleidsset waartoe het beleid behoort. U kunt een `null` waarde die ertoe leidt dat het beleid aan *MijnBeleid* beleidsset.

   Als u binnen de verbindingsinstellingen een beheerdersaccount voor AEM formulieren gebruikt om de `DocumentSecurityClient` -object, geeft u de naam van de beleidsset op wanneer u het `registerPolicy` methode.

   Als u een gebruiker van de Veiligheid van het Document SecurityDocument binnen verbindingsmontages gebruikt, dan kunt u overbelaste aanhalen `registerPolicy` methode die alleen het beleid accepteert. U hoeft dus geen naam voor de beleidsset op te geven. Het beleid wordt echter toegevoegd aan de benoemde beleidsset *Mijn beleid*. Als u het nieuwe beleid niet aan deze beleidsreeks wilt toevoegen, dan specificeer een naam van de beleidsreeks wanneer u aanhaalt `registerPolicy` methode.

   >[!NOTE]
   >
   >Wanneer het creëren van een beleid en u specificeert een beleidsreeks, zorg ervoor dat u een bestaande beleidsreeks specificeert. Als u een beleidsset opgeeft die niet bestaat, wordt een uitzondering gegenereerd.

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Quick Start (MTOM): Creating a policy using the web service API&quot;
* &quot;Quick Start (SwaRef): Creating a policy using the web service API&quot;

## Beleid wijzigen {#modifying-policies}

U kunt een bestaand beleid wijzigen met de Java API voor documentbeveiliging of de webservice-API. Om een bestaand beleid te veranderen, wint u het terug, wijzigt het, en werkt dan het beleid op de server bij. Stel dat u een bestaand beleid ophaalt en de geldigheidsperiode ervan verlengt. Voordat de wijziging van kracht wordt, moet u het beleid bijwerken.

U kunt een beleid wijzigen wanneer de bedrijfsvereisten veranderen en het beleid niet meer op deze vereisten wijst. In plaats van een beleid te maken, kunt u gewoon een bestaand beleid bijwerken.

Als u beleidskenmerken wilt wijzigen met behulp van een webservice (bijvoorbeeld met Java-proxyklassen die zijn gemaakt met JAX-WS), moet u ervoor zorgen dat het beleid is geregistreerd bij de Document Security-service. U kunt dan naar het bestaande beleid verwijzen door `PolicySpec.getPolicyXml` en wijzigt u de beleidskenmerken met de toepasselijke methoden. U kunt bijvoorbeeld de offline leaseperiode wijzigen door de `PolicySpec.setOfflineLeasePeriod` methode.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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

Haal een bestaand beleid op om het te wijzigen. Om een beleid terug te winnen, specificeer de beleidsnaam en het beleid dat wordt geplaatst waartot het beleid behoort. Als u een `null` waarde voor de naam van de beleidsset, wordt het beleid opgehaald uit de *Mijn beleid* beleidsset.

**De kenmerken van het beleid instellen**

Als u een beleid wilt wijzigen, wijzigt u de waarde van beleidskenmerken. Het enige beleidskenmerk dat u niet kunt wijzigen, is het naamkenmerk. Bijvoorbeeld, om de off-line huurperiode van het beleid te veranderen, kunt u de waarde van de off-line de huurperiode van het beleid attributen wijzigen.

Wanneer u de offline leaseperiode van een beleid wijzigt met een webservice, wordt de `offlineLeasePeriod` veld op `PolicySpec` interface wordt genegeerd. Als u de offline leaseperiode wilt bijwerken, wijzigt u de `OfflineLeasePeriod` in het PDRL XML-document. Verwijs dan naar het bijgewerkte document PDRL XML door te gebruiken `PolicySpec` interface `policyXML` lid.

>[!NOTE]
>
>Voor informatie over andere kenmerken die u kunt instellen, raadpleegt u de `Policy` interfacebeschrijving in de [AEM Forms API-naslag](https://www.adobe.com/go/learn_aemforms_javadocs_63_en).

**Het beleid bijwerken**

Voordat de wijzigingen die u in een beleid aanbrengt, worden doorgevoerd, moet u het beleid bijwerken met de documentbeveiligingsservice. Wijzigingen in beleid dat documenten beveiligt, worden de volgende keer dat het document met beveiligingsbeleid wordt gesynchroniseerd met de documentbeveiligingsservice bijgewerkt.

### Bestaand beleid wijzigen met de Java API {#modify-existing-policies-using-the-java-api}

Wijzig een bestaand beleid met de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `RightsManagementClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Een bestaand beleid ophalen.

   * Een `PolicyManager` door het object aan te roepen `RightsManagementClient` object `getPolicyManager` methode.
   * Een `Policy` object dat het beleid vertegenwoordigt dat moet worden bijgewerkt door het `PolicyManager` object `getPolicy` methode en geeft de volgende waarden door&quot;

      * Een tekenreekswaarde die staat voor de naam van de beleidsset waartoe het beleid behoort. U kunt `null` dat leidt tot `MyPolicies` de gebruikte beleidsset.
      * Een tekenreekswaarde die de naam van het beleid vertegenwoordigt.

1. Stel de kenmerken van het beleid in.

   Verander de attributen van het beleid om aan uw bedrijfsvereisten te voldoen. Als u bijvoorbeeld de offline leaseperiode van het beleid wilt wijzigen, roept u de `Policy` object `setOfflineLeasePeriod` methode.

1. Werk het beleid bij.

   Werk het beleid bij door aan te halen `PolicyManager` object `updatePolicy` methode. Geef de `Policy` object dat staat voor het beleid dat moet worden bijgewerkt.

**Codevoorbeelden**

Zie Snel starten (modus SOAP): Een beleid wijzigen met de Java API-sectie voor codevoorbeelden met de documentbeveiligingsservice.

### Bestaand beleid wijzigen met de webservice-API {#modify-existing-policies-using-the-web-service-api}

Wijzig een bestaand beleid met de API voor documentbeveiliging (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Een `RightsManagementServiceClient` object met de standaardconstructor.
   * Een `RightsManagementServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `RightsManagementServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een bestaand beleid ophalen.

   Een `PolicySpec` object dat het beleid vertegenwoordigt dat moet worden gewijzigd door het `RightsManagementServiceClient` object `getPolicy` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van de beleidsset opgeeft waartoe het beleid behoort. U kunt `null` dat leidt tot `MyPolicies` de gebruikte beleidsset.
   * Een tekenreekswaarde die de naam van het beleid opgeeft.

1. Stel de kenmerken van het beleid in.

   Verander de attributen van het beleid om aan uw bedrijfsvereisten te voldoen.

1. Werk het beleid bij.

   Werk het beleid bij door het `RightsManagementServiceClient` object `updatePolicyFromSDK` en het doorgeven van de `PolicySpec` object dat staat voor het beleid dat moet worden bijgewerkt.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Quick Start (MTOM): Modifying a policy using the web service API&quot;
* &quot;Quick Start (SwaRef): Modifying a policy using the web service API&quot;

## Beleid verwijderen {#deleting-policies}

U kunt een bestaand beleid verwijderen met de Java API voor documentbeveiliging of de webservice-API. Nadat een beleid is verwijderd, kan het niet meer worden gebruikt om documenten te beschermen. Bestaande documenten die door het beleid worden beschermd, zijn echter nog steeds beveiligd. U kunt een beleid schrappen wanneer nieuwere beschikbaar wordt.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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

Als u een beleid wilt verwijderen, geeft u het beleid op dat u wilt verwijderen en de beleidsset waartoe het beleid behoort. De gebruiker van wie de montages worden gebruikt om AEM Forms aan te halen moet toestemming hebben om het beleid te schrappen; anders komt een uitzondering voor. En als u probeert een beleid te verwijderen dat niet bestaat, treedt een uitzondering op.

### Beleid verwijderen met de Java API {#delete-policies-using-the-java-api}

Een beleid verwijderen met de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `RightsManagementClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Verwijder het beleid.

   * Een `PolicyManager` door het object aan te roepen `RightsManagementClient` object `getPolicyManager` methode.
   * Verwijder het beleid door het `PolicyManager` object `deletePolicy` en geeft de volgende waarden door:

      * Een tekenreekswaarde die de naam van de beleidsset opgeeft waartoe het beleid behoort. U kunt `null` dat leidt tot `MyPolicies` de gebruikte beleidsset.
      * Een tekenreekswaarde die de naam aangeeft van het beleid dat moet worden verwijderd.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP modus): beleid verwijderen met de Java API&quot;

### Beleid verwijderen met de webservice-API {#delete-policies-using-the-web-service-api}

Verwijder een beleid met de API voor documentbeveiliging (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Een `RightsManagementServiceClient` object met de standaardconstructor.
   * Een `RightsManagementServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `RightsManagementServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Verwijder het beleid.

   Een beleid verwijderen door het `RightsManagementServiceClient` object `deletePolicy` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam van de beleidsset opgeeft waartoe het beleid behoort. U kunt `null` dat leidt tot `MyPolicies` de gebruikte beleidsset.
   * Een tekenreekswaarde die de naam aangeeft van het beleid dat moet worden verwijderd.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Quick Start (MTOM): Deleting a policy using the web service API&quot;
* &quot;Quick Start (SwaRef): Deleting a policy using the web service API&quot;

## Beleid toepassen op PDF-documenten {#applying-policies-to-pdf-documents}

U kunt een beleid op een document van de PDF toepassen om het document te beveiligen. Door een beleid op een document van de PDF toe te passen, beperkt u toegang tot het document. U kunt geen beleid op een document toepassen als het document reeds met een beleid wordt beveiligd.

Terwijl het document is geopend, kunt u ook de toegang tot Acrobat- en Adobe Reader-functies beperken, zoals de mogelijkheid om tekst af te drukken en te kopiëren, wijzigingen aan te brengen en handtekeningen en opmerkingen aan een document toe te voegen. Bovendien kunt u een met een beleid beveiligd PDF-document intrekken wanneer u niet langer wilt dat gebruikers het document openen.

U kunt het gebruik van een document dat met een beleid is beveiligd controleren nadat u het hebt verspreid. Dat wil zeggen dat u kunt zien hoe het document wordt gebruikt en wie het gebruikt. U kunt bijvoorbeeld zien wanneer iemand het document heeft geopend.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende stappen uit om een beleid toe te passen op een PDF-document:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Hiermee wordt een PDF-document opgehaald waarop een beleid is toegepast.
1. Pas een bestaand beleid op het document van de PDF toe.
1. Sla het met beleid beveiligde PDF-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u via programmacode een bewerking met de documentbeveiligingsservice kunt uitvoeren, maakt u een clientobject van de documentbeveiligingsservice. Als u de Java API gebruikt, maakt u een `DocumentSecurityClient` object. Als u de API voor documentbeveiliging gebruikt, maakt u een `DocumentSecurityServiceService` object.

**Een PDF-document ophalen**

U kunt een PDF-document ophalen om een beleid toe te passen. Nadat u een beleid op het document van de PDF toepast, worden de gebruikers beperkt wanneer het gebruiken van het document. Als het beleid bijvoorbeeld niet toestaat dat het document offline wordt geopend, moeten gebruikers online zijn om het document te openen.

**Een bestaand beleid toepassen op het PDF-document**

Om een beleid op een document van de PDF toe te passen, verwijs een bestaand beleid en specificeer welk beleid het beleid tot behoort. De gebruiker die de verbindingseigenschappen instelt, moet toegang hebben tot het opgegeven beleid. Als dat niet het geval is, treedt een uitzondering op.

**Het PDF-document opslaan**

Nadat de dienst van de Veiligheid van het Document een beleid op een document van de PDF toepast, kunt u het beleid-beschermde document van de PDF als PDF dossier bewaren.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Toegang tot documenten intrekken](protecting-documents-policies.md#revoking-access-to-documents)

### Een beleid toepassen op een PDF-document met de Java API {#apply-a-policy-to-a-pdf-document-using-the-java-api}

Een beleid toepassen op een PDF-document met behulp van de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `RightsManagementClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Een PDF-document ophalen.

   * Een `java.io.FileInputStream` object dat het PDF-document vertegenwoordigt met behulp van de constructor ervan. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Pas een bestaand beleid op het document van de PDF toe.

   * Een `DocumentManager` door het object aan te roepen `RightsManagementClient` object `getDocumentManager` methode.
   * Pas een beleid op het document van de PDF toe door aan te halen `DocumentManager` object `protectDocument` en geeft de volgende waarden door:

      * De `com.adobe.idp.Document` -object dat het PDF-document bevat waarop het beleid wordt toegepast.
      * Een tekenreekswaarde die de naam van het document aangeeft.
      * Een tekenreekswaarde die de naam opgeeft van de beleidsset waartoe het beleid behoort. U kunt een `null` waarde die resulteert in de `MyPolicies` de gebruikte beleidsset.
      * Een tekenreekswaarde die de beleidsnaam opgeeft.
      * Een tekenreekswaarde die de naam vertegenwoordigt van het gebruikersbeheerdomein van de gebruiker die de uitgever van het document is. Deze parameterwaarde is optioneel en kan null zijn (als deze parameter null is, moet de volgende parameterwaarde null zijn).
      * Een tekenreekswaarde die de naam vertegenwoordigt van de canonieke naam van de gebruiker van de gebruikersmanager die de uitgever van het document is. Deze parameterwaarde is optioneel en kan `null` (als deze parameter null is, moet de vorige parameterwaarde `null`).
      * A `com.adobe.livecycle.rightsmanagement.Locale` dat de landinstelling vertegenwoordigt die wordt gebruikt voor het selecteren van de MS Office-sjabloon. Deze parameterwaarde is optioneel en wordt niet gebruikt voor PDF-documenten. Als u een PDF-document wilt beveiligen, geeft u `null`.

     De `protectDocument` methode retourneert een `RMSecureDocumentResult` -object dat het met een beleid beveiligde PDF-document bevat.

1. Sla het PDF-document op.

   * De `RMSecureDocumentResult` object `getProtectedDoc` methode om het document van de beleid-beschermde PDF te krijgen. Deze methode retourneert een `com.adobe.idp.Document` object.
   * Een `java.io.File` -object en controleer of de bestandsextensie PDF is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `Document` object naar het bestand (gebruik de `Document` object dat is geretourneerd door de `getProtectedDoc` methode).

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (EJB-modus): beleid toepassen op een PDF-document met behulp van de Java API&quot;
* &quot;Snel starten (SOAP modus): beleid toepassen op een PDF-document met behulp van de Java API&quot;

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Een beleid toepassen op een PDF-document met de webservice-API {#apply-a-policy-to-a-pdf-document-using-the-web-service-api}

Pas een beleid op een document van de PDF toe door de Veiligheid API van het Document (Webdienst) te gebruiken:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Een `RightsManagementServiceClient` object met de standaardconstructor.
   * Een `RightsManagementServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `RightsManagementServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een PDF-document ophalen.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een PDF-document op te slaan waarop een beleid wordt toegepast.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. Bepaal de grootte van de bytearray door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Pas een bestaand beleid op het document van de PDF toe.

   Pas een beleid op het document van de PDF toe door aan te halen `RightsManagementServiceClient` object `protectDocument` en geeft de volgende waarden door:

   * De `BLOB` -object dat het PDF-document bevat waarop het beleid wordt toegepast.
   * Een tekenreekswaarde die de naam van het document aangeeft.
   * Een tekenreekswaarde die de naam opgeeft van de beleidsset waartoe het beleid behoort. U kunt een `null` waarde die resulteert in de `MyPolicies` de gebruikte beleidsset.
   * Een tekenreekswaarde die de beleidsnaam opgeeft.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het gebruikersbeheerdomein van de gebruiker die de uitgever van het document is. Deze parameterwaarde is optioneel en kan null zijn (als deze parameter null is, moet de volgende parameterwaarde `null`).
   * Een tekenreekswaarde die de naam vertegenwoordigt van de canonieke naam van de gebruiker van de gebruikersmanager die de uitgever van het document is. Deze parameterwaarde is optioneel en kan null zijn (als deze parameter null is, moet de vorige parameterwaarde `null`).
   * A `RMLocale` waarde die de waarde van de landinstelling opgeeft (bijvoorbeeld `RMLocale.en`).
   * Een parameter van de koordoutput die wordt gebruikt om de waarde van beleidsidentificatie op te slaan.
   * Een parameter van de koordoutput die wordt gebruikt om de beleid-beschermde herkenningstekenwaarde op te slaan.
   * Een parameter van de koordoutput die wordt gebruikt om het mime type op te slaan (bijvoorbeeld `application/pdf`).

   De `protectDocument` methode retourneert een `BLOB` -object dat het met een beleid beveiligde PDF-document bevat.

1. Sla het PDF-document op.

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het met een beleid beveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `protectDocument` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een PDF-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (MTOM): beleid toepassen op een PDF-document met behulp van de webservice-API&quot;
* &quot;Quick Start (SwaRef): Applying a policy to a PDF document using the web service API &quot;

## Beleid verwijderen uit PDF-documenten {#removing-policies-from-pdf-documents}

U kunt een beleid verwijderen uit een document dat met een beleid is beveiligd om de beveiliging van het document te verwijderen. Dat wil zeggen, als u niet langer wilt dat het document wordt beschermd door een beleid. Als u een beleid-beschermd document met een nieuwer beleid wilt bijwerken, dan in plaats van het beleid te verwijderen en het bijgewerkte beleid toe te voegen, is het efficiënter om het beleid te schakelen.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om een beleid te verwijderen uit een met beleid beveiligd PDF-document:

1. Projectbestanden opnemen
1. Maak een API-object voor Document Security Client.
1. Hiermee wordt een met beleid beveiligd PDF-document opgehaald.
1. Verwijder het beleid uit het document van de PDF.
1. Sla het onbeveiligde PDF-document op.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u via programmacode een bewerking met de documentbeveiligingsservice kunt uitvoeren, maakt u een clientobject van de documentbeveiligingsservice.

**Een met beleid beveiligd PDF-document ophalen**

U kunt een met een beleid beveiligd PDF-document ophalen om een beleid te verwijderen. Als u probeert om een beleid uit een document te verwijderen van de PDF dat niet door een beleid wordt beschermd, zult u een uitzondering veroorzaken.

**Het beleid verwijderen uit het PDF-document**

U kunt een beleid uit een beleid-beschermd document van de PDF verwijderen op voorwaarde dat een beheerder in de verbindingsmontages wordt gespecificeerd. Zo niet, dan moet het beleid dat wordt gebruikt om een document te beveiligen het `SWITCH_POLICY` toestemming om een beleid uit een document van de PDF te verwijderen. De gebruiker die is opgegeven in de AEM Forms-verbindingsinstellingen moet ook over deze machtiging beschikken. Anders wordt een uitzondering gegenereerd.

**Het onbeveiligde PDF-document opslaan**

Nadat de documentbeveiligingsservice een beleid uit een PDF-document heeft verwijderd, kunt u het onbeveiligde PDF-document opslaan als een PDF-bestand.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Beleid toepassen op PDF-documenten](protecting-documents-policies.md#applying-policies-to-pdf-documents)

### Een beleid verwijderen uit een PDF-document met de Java API {#remove-a-policy-from-a-pdf-document-using-the-java-api}

Verwijder een beleid uit een beleid-beschermd document van de PDF door de Veiligheid API van het Document (Java) te gebruiken:

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `DocumentSecurityClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Hiermee wordt een met beleid beveiligd PDF-document opgehaald.

   * Een `java.io.FileInputStream` -object dat het met een beleid beveiligde PDF-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Verwijder het beleid uit het document van de PDF.

   * Een `DocumentManager` door het object aan te roepen `DocumentSecurityClient` object `getDocumentManager` methode.
   * Verwijder een beleid uit het document van de PDF door aan te halen `DocumentManager` object `removeSecurity` en het doorgeven van de `com.adobe.idp.Document` -object dat het met een beleid beveiligde PDF-document bevat. Deze methode retourneert een `com.adobe.idp.Document` object dat een onbeveiligd PDF-document bevat.

1. Sla het onbeveiligde PDF-document op.

   * Een `java.io.File` -object en controleer of de bestandsextensie PDF is.
   * De `Document` object `copyToFile` methode om de inhoud van de `Document` object naar het bestand (gebruik de `Document` object dat is geretourneerd door de `removeSecurity` methode).

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP modus): Een beleid verwijderen uit een PDF-document met de Java API&quot;

### Een beleid verwijderen met de webservice-API {#remove-a-policy-using-the-web-service-api}

Verwijder een beleid uit een beleid-beschermd document van de PDF gebruikend de Veiligheid API van het Document (Webdienst):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Een `DocumentSecurityServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `DocumentSecurityServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Hiermee wordt een met beleid beveiligd PDF-document opgehaald.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` -object wordt gebruikt om het met een beleid beveiligde PDF-document op te slaan waaruit het beleid wordt verwijderd.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Verwijder het beleid uit het document van de PDF.

   Verwijder het beleid uit het document van de PDF door te roepen `DocumentSecurityServiceClient` object `removePolicySecurity` en het doorgeven van de `BLOB` -object dat het met een beleid beveiligde PDF-document bevat. Deze methode retourneert een `BLOB` object dat een onbeveiligd PDF-document bevat.

1. Sla het onbeveiligde PDF-document op.

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het onbeveiligde PDF-document vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `removePolicySecurity` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` veld.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Quick Start (MTOM): Remoting a policy from a PDF document using the web service API &quot;
* &quot;Quick Start (SwaRef): Removing a policy from a PDF document using the web service API&quot;

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Toegang tot documenten intrekken {#revoking-access-to-documents}

U kunt de toegang tot een met een beleid beveiligd PDF-document intrekken, waardoor alle kopieën van het document niet toegankelijk zijn voor gebruikers. Wanneer een gebruiker een ingetrokken PDF-document probeert te openen, wordt deze doorgestuurd naar een opgegeven URL waar een gereviseerd document kan worden weergegeven. De URL waarnaar de gebruiker is omgeleid, moet via programmacode worden opgegeven. Wanneer u de toegang tot een document intrekt, wordt de wijziging van kracht wanneer de gebruiker opnieuw synchroniseert met de documentbeveiligingsservice door het document dat met een beleid is beveiligd online te openen.

De mogelijkheid om de toegang tot een document in te trekken biedt extra beveiliging. Stel dat er een nieuwere versie van een document beschikbaar is en dat u niet langer wilt dat iemand de verouderde versie bekijkt. In dit geval kan de toegang tot het oudere document worden ingetrokken en kan niemand het document bekijken tenzij de toegang wordt hersteld.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-5}

Voer de volgende stappen uit om een document dat met een beleid is beveiligd, in te trekken:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Hiermee wordt een met beleid beveiligd PDF-document opgehaald.
1. Intrekken van het document dat met een beleid is beveiligd.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u programmatisch een Document Security-servicebewerking kunt uitvoeren, moet u een Document Security-service-clientobject maken.

**Een met beleid beveiligd PDF-document ophalen**

Haal een document met een door het beleid beschermde PDF op om het in te trekken. U kunt een document dat al is ingetrokken of dat niet door een beleid beveiligd is, niet intrekken.

Als u de waarde van de vergunningsidentificatie van het beleid-beschermde document kent, dan is het niet noodzakelijk om het beleid-beschermde document van de PDF terug te winnen. In de meeste gevallen moet u echter het PDF-document ophalen om de waarde van de licentie-id op te halen.

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `DocumentSecurityClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Een met beleid beveiligd PDF-document ophalen

   * Een `java.io.FileInputStream` -object dat het met een beleid beveiligde PDF-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Intrekken van het document dat met een beleid is beveiligd

   * Een `DocumentManager` door het object aan te roepen `DocumentSecurityClient` object `getDocumentManager` methode.
   * Haal de waarde van de licentie-id van het document dat met een beleid is beveiligd, op door het `DocumentManager` object `getLicenseId` methode. Geef de `com.adobe.idp.Document` object dat staat voor het document dat met een beleid is beveiligd. Deze methode retourneert een tekenreekswaarde die de waarde van de licentie-id vertegenwoordigt.
   * Een `LicenseManager` door het object aan te roepen `DocumentSecurityClient` object `getLicenseManager` methode.
   * Intrekken van het document dat met een beleid is beveiligd door het `LicenseManager` object `revokeLicense` en geeft de volgende waarden door:

      * Een tekenreekswaarde die de waarde van de licentie-id van het document met beleidsbeveiliging opgeeft (geef de geretourneerde waarde van het document op `DocumentManager` object `getLicenseId` methode).
      * Een statisch gegevenslid van de `License` interface die de reden voor het intrekken van het document aangeeft. U kunt bijvoorbeeld `License.DOCUMENT_REVISED`.
      * A `java.net.URL` waarde die de locatie aangeeft waarnaar een gereviseerd document zich bevindt. Als u een gebruiker niet naar een andere URL wilt omleiden, kunt u `null`.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP modus): een document intrekken met de Java API&quot;

### Toegang tot documenten intrekken met de webservice-API {#revoke-access-to-documents-using-the-web-service-api}

De toegang tot een met beleid beveiligd PDF-document intrekken met de API voor documentbeveiliging (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een API-object voor documentbeveiliging maken

   * Een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Een `DocumentSecurityServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `DocumentSecurityServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een met beleid beveiligd PDF-document ophalen

   * Een `BLOB` object met behulp van de constructor. De `BLOB` -object wordt gebruikt om een met een beleid beveiligd PDF-document op te slaan dat wordt ingetrokken.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie vertegenwoordigt van het PDF-document met beveiligingsbeleid dat moet worden ingetrokken en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Intrekken van het document dat met een beleid is beveiligd

   * Haal de waarde van de licentie-id van het document dat met een beleid is beveiligd, op door het `DocumentSecurityServiceClient` object `getLicenseID` en het doorgeven van de `BLOB` object dat staat voor het document dat met een beleid is beveiligd. Deze methode retourneert een tekenreekswaarde die de licentie-id vertegenwoordigt.
   * Intrekken van het document dat met een beleid is beveiligd door het `DocumentSecurityServiceClient` object `revokeLicense` en geeft de volgende waarden door:

      * Een tekenreekswaarde die de waarde van de licentie-id van het document met beleidsbeveiliging opgeeft (geef de geretourneerde waarde van het document op `DocumentSecurityServiceService` object `getLicenseId` methode).
      * Een statisch gegevenslid van de `Reason` een opsomming waarin de reden voor intrekking van het document wordt opgegeven. U kunt bijvoorbeeld `Reason.DOCUMENT_REVISED`.
      * A `string` waarde die de URL-locatie opgeeft waarnaar een gereviseerd document zich bevindt. Als u een gebruiker niet naar een andere URL wilt omleiden, kunt u `null`.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Quick Start (MTOM): Revoking a document using the web service API&quot;
* &quot;Quick Start (SwaRef): Revoking a document using the web service API&quot;

**Zie ook**

[Beleid verwijderen uit Word-documenten](protecting-documents-policies.md#removing-policies-from-word-documents)

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Toegang tot ingetrokken documenten opnieuw instellen {#reinstating-access-to-revoked-documents}

U kunt de toegang tot een ingetrokken PDF-document opnieuw instellen, zodat alle exemplaren van het ingetrokken document toegankelijk zijn voor gebruikers. Wanneer een gebruiker een hersteld document opent dat werd ingetrokken, kan de gebruiker het document bekijken.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-6}

Voer de volgende stappen uit om de toegang tot een ingetrokken PDF-document te herstellen:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Haal de licentiecode van het ingetrokken PDF-document op.
1. Open het ingetrokken PDF-document opnieuw.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u programmatisch een Document Security-servicebewerking kunt uitvoeren, moet u een Document Security-service-clientobject maken. Als u de Java API gebruikt, maakt u een `DocumentSecurityClient` object. Als u de API voor documentbeveiliging gebruikt, maakt u een `DocumentSecurityServiceService` object.

**De licentiecode van het ingetrokken PDF-document ophalen**

Haal de licentie-id van het ingetrokken PDF-document op om een ingetrokken PDF-document opnieuw in te voeren. Nadat u de waarde van de licentie-id hebt gekregen, kunt u een ingetrokken document opnieuw installeren. Als u probeert een document opnieuw in te voegen dat niet is ingetrokken, veroorzaakt u een uitzondering.

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `DocumentSecurityClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Haal de licentiecode van het ingetrokken PDF-document op.

   * Een `java.io.FileInputStream` een object dat het ingetrokken PDF-document vertegenwoordigt met de constructor ervan en een tekenreekswaarde doorgeeft die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.
   * Een `DocumentManager` door het object aan te roepen `DocumentSecurityClient` object `getDocumentManager` methode.
   * Haal de waarde van de licentie-id van het ingetrokken document op door het `DocumentManager` object `getLicenseId` en het doorgeven van de `com.adobe.idp.Document` object dat staat voor het ingetrokken document. Deze methode retourneert een tekenreekswaarde die de licentie-id vertegenwoordigt.

1. Open het ingetrokken PDF-document opnieuw.

   * Een `LicenseManager` door het object aan te roepen `DocumentSecurityClient` object `getLicenseManager` methode.
   * Herstel de toegang tot het ingetrokken PDF-document door het `LicenseManager` object `unrevokeLicense` en geeft u de waarde van de licentie-id van het ingetrokken document door.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP modus): Toegang tot een ingetrokken document opnieuw instellen met de webservice-API&quot;

### Toegang tot ingetrokken documenten opnieuw instellen met de webservice-API {#reinstate-access-to-revoked-documents-using-the-web-service-api}

Toegang tot een ingetrokken document opnieuw instellen met de API voor documentbeveiliging (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Een `DocumentSecurityServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `DocumentSecurityServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Haal de licentiecode van het ingetrokken PDF-document op.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` -object wordt gebruikt om een ingetrokken PDF-document op te slaan dat weer kan worden geopend.
   * Een `System.IO.FileStream` door de constructor aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het ingetrokken PDF-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Open het ingetrokken PDF-document opnieuw.

   * Haal de waarde van de licentie-id van het ingetrokken document op door het `DocumentSecurityServiceClient` object `getLicenseID` en het doorgeven van de `BLOB` object dat staat voor het ingetrokken document. Deze methode retourneert een tekenreekswaarde die de licentie-id vertegenwoordigt.
   * Herstel de toegang tot het ingetrokken PDF-document door het `DocumentSecurityServiceClient` object `unrevokeLicense` methode en het overgaan van een koordwaarde die de waarde van het vergunningsherkenningsteken van het ingetrokken document van de PDF specificeert (ga de terugkeerwaarde van over `DocumentSecurityServiceClient` object `getLicenseId` methode).

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (MTOM): Toegang tot een ingetrokken document opnieuw instellen met de webservice-API&quot;
* &quot;Quick Start (SwaRef): Reinsting access to a revoked document using the web service API&quot;

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Met beleid beveiligde PDF-documenten controleren {#inspecting-policy-protected-pdf-documents}

U kunt de API voor documentbeveiligingsservice (Java en webservice) gebruiken om met beleid beveiligde PDF-documenten te inspecteren. Wanneer u documenten met door een beleid beveiligde PDF controleert, wordt informatie over het document met door een beleid beveiligde PDF geretourneerd. U kunt bijvoorbeeld bepalen welk beleid is gebruikt om het document te beveiligen en op welke datum het document is beveiligd.

U kunt deze taak niet uitvoeren als uw versie van LiveCycle 8.x of een vroegere versie is. Ondersteuning voor het inspecteren van documenten die met een beleid zijn beveiligd, wordt toegevoegd in AEM Forms. Als u probeert om een beleid-beschermd document te inspecteren gebruikend LiveCycle 8.x (of vroeger), wordt een uitzondering geworpen.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-7}

Voer de volgende stappen uit om een met beleid beveiligd PDF-document te inspecteren:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Haal een document op dat met een beleid is beveiligd en dat u wilt inspecteren.
1. Informatie opvragen over het document dat met een beleid is beveiligd.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u de proxybestanden opnemen.

**Een API-object voor documentbeveiliging maken**

Voordat u via programmacode een bewerking met de documentbeveiligingsservice kunt uitvoeren, maakt u een clientobject van de documentbeveiligingsservice. Als u de Java API gebruikt, maakt u een `RightsManagementClient` object. Als u de API voor documentbeveiliging gebruikt, maakt u een `RightsManagementServiceService` object.

**Een document ophalen dat met een beleid is beveiligd om te worden gecontroleerd**

Als u een document wilt inspecteren dat met een beleid is beveiligd, haalt u het op. Als u een document probeert te inspecteren dat niet met een beleid wordt beveiligd of wordt ingetrokken, wordt een uitzondering gegenereerd.

**Het document Inspect**

Nadat u een document hebt opgehaald dat met een beleid is beveiligd, kunt u het controleren.

**Informatie opvragen over het document dat met een beleid is beveiligd**

Nadat u een beleid-beschermd document van de PDF inspecteert, kunt u informatie over het verkrijgen. U kunt bijvoorbeeld bepalen welk beleid wordt gebruikt om het document te beveiligen.

Als u een document met een beleid beveiligt dat tot Mijn Beleid behoort en dan roept `RMInspectResult.getPolicysetName` of `RMInspectResult.getPolicysetId`, null wordt geretourneerd.

Als het document wordt beveiligd met een beleid dat is opgenomen in een beleidsset (anders dan Mijn beleid) dan `RMInspectResult.getPolicysetName` en `RMInspectResult.getPolicysetId` geldige tekenreeksen retourneren.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Inspect Policy Protected PDF Documents using the Java API {#inspect-policy-protected-pdf-documents-using-the-java-api}

Inspect a policy-protected PDF document by using the Document Security Service API (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden voor clients, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project. Voor informatie over de locatie van deze bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).

1. Maak een API-object voor Document Security Client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie [Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).)
   * Een `RightsManagementClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Haal een document op dat met een beleid is beveiligd en dat u wilt inspecteren.

   * Een `java.io.FileInputStream` object dat het met een beleid beveiligde PDF-document vertegenwoordigt met behulp van de constructor ervan. Geef een tekenreekswaarde door die de locatie van het PDF-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Inspect het document.

   * Een `DocumentManager` door het object aan te roepen `RightsManagementClient` object `getDocumentManager` methode.
   * Inspect het document dat met een beleid is beveiligd door het `LicenseManager` object `inspectDocument` methode. Geef de `com.adobe.idp.Document` -object dat het met een beleid beveiligde PDF-document bevat. Deze methode retourneert een `RMInspectResult` object dat informatie bevat over het document dat met een beleid is beveiligd.

1. Informatie opvragen over het document dat met een beleid is beveiligd.

   Om informatie over het beleid-beschermde document te verkrijgen, haal de aangewezen methode aan die behoort `RMInspectResult` object. Als u bijvoorbeeld de naam van het beleid wilt ophalen, roept u de `RMInspectResult` object `getPolicyName` methode.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP modus): Met beleid beveiligde PDF-documenten inspecteren met de Java API&quot;

### Inspect Policy Protected PDF Documents using the web service API {#inspect-policy-protected-pdf-documents-using-the-web-service-api}

Inspect a policy-protected PDF document by the Document Security Service API (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Een `RightsManagementServiceClient` object met de standaardconstructor.
   * Een `RightsManagementServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `RightsManagementServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Haal een document op dat met een beleid is beveiligd en dat u wilt inspecteren.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een PDF-document op te slaan dat moet worden geïnspecteerd.
   * Een `System.IO.FileStream` object door de constructor ervan aan te roepen. Geef een tekenreekswaarde door die staat voor de bestandslocatie van het PDF-document en de modus waarin het bestand moet worden geopend.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Inspect het document.

   Inspect het document dat met een beleid is beveiligd door het `RightsManagementServiceClient` object `inspectDocument` methode. Geef de `BLOB` -object dat het met een beleid beveiligde PDF-document bevat. Deze methode retourneert een `RMInspectResult` object dat informatie bevat over het document dat met een beleid is beveiligd.

1. Informatie opvragen over het document dat met een beleid is beveiligd.

   Om informatie over het beleid beschermde document te verkrijgen, krijg de waarde van het aangewezen gebied dat tot `RMInspectResult` object. Als u bijvoorbeeld de naam van het beleid wilt ophalen, krijgt u de waarde van de knop `RMInspectResult` object `policyName` veld.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (MTOM): met beleid beveiligde PDF-documenten inspecteren met de webservice-API&quot;
* &quot;Quick Start (SwaRef): met een beleid beveiligde PDF-documenten inspecteren met behulp van de webservice-API&quot;

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Watermerken maken {#creating-watermarks}

Watermerken helpen de veiligheid van een document te waarborgen door het document op unieke wijze te identificeren en de inbreuk op het auteursrecht te controleren. U kunt bijvoorbeeld een watermerk maken en plaatsen dat op alle pagina&#39;s van een document de tekst Vertrouwelijk aangeeft. Nadat u een watermerk hebt gemaakt, kunt u dit opnemen in een beleid. U kunt dus het watermerkkenmerk van het beleid instellen met het nieuwe watermerk. Nadat een beleid met een watermerk is toegepast op een document, wordt het watermerk weergegeven in het document dat met een beleid is beveiligd.

>[!NOTE]
>
>Alleen gebruikers met beheerdersrechten voor documentbeveiliging kunnen watermerken maken. Dit betekent dat u een dergelijke gebruiker moet opgeven wanneer u verbindingsinstellingen definieert die vereist zijn om een Document Security Service Client-object te maken.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-8}

Voer de volgende stappen uit om een watermerk te maken:

1. Inclusief projectbestanden.
1. Maak een API-object voor Document Security Client.
1. Stel de kenmerken van de watermerken in.
1. Registreer het watermerk bij de Document Security Service.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een API-object voor documentbeveiliging maken**

Voordat u programmatisch een Document Security-servicebewerking kunt uitvoeren, moet u een Document Security-service-clientobject maken. Als u de Java API gebruikt, maakt u een `RightsManagementClient` object. Als u de API voor documentbeveiliging gebruikt, maakt u een `RightsManagementServiceService` object.

**De kenmerken van de watermerken instellen**

Als u een watermerk wilt maken, moet u de kenmerken van het watermerk instellen. Het kenmerk name moet altijd worden gedefinieerd. Naast het kenmerk name moet u ten minste een van de volgende kenmerken instellen:

* Aangepaste tekst
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
   <td><p>Als deze waarde is opgegeven, <code>WaterBackCmd:IS_SIZE_ENABLED</code> moet aanwezig zijn en de waarde moet waar zijn. Als dit kenmerk niet is opgegeven, wordt het standaardgedrag aan de pagina aangepast.</p></td>
   <td><p>Een waarde groter dan 0,0 en kleiner dan of gelijk aan 1,0.</p></td>
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
   <td><p>Hiermee wordt de aangepaste tekst voor een watermerk opgegeven. Als deze waarde aanwezig is, dan <code>WaterBackCmd:IS_CUSTOMTEXT_ENABLED</code> moet ook aanwezig zijn en op waar worden geplaatst.</p></td>
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

   Inclusief JAR-bestanden voor clients, zoals de `adobe-rightsmanagement-client.jar`, in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `RightsManagementClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. De kenmerken van het watermerk instellen

   * Een `Watermark` door het object aan te roepen `InfomodelObjectFactory` statisch object `createWatermark` methode. Deze methode retourneert een `Watermark` object.
   * Stel het naamkenmerk van het watermerk in door het `Watermark` object `setName` methode en het overgaan van een koordwaarde die de beleidsnaam specificeert.
   * Stel het achtergrondkenmerk van het watermerk in door het `Watermark` object `setBackground` methode en doorgeven `true`. Door dit kenmerk in te stellen, verschijnt het watermerk op de achtergrond van het document.
   * Stel het aangepaste tekstkenmerk van het watermerk in door het `Watermark` object `setCustomText` en een tekenreekswaarde doorgeven die de tekst van het watermerk vertegenwoordigt.
   * Stel het kenmerk Dekking van het watermerk in door het `Watermark` object `setOpacity` methode en het overgaan van een geheelwaarde die het opaciteitniveau specificeert. De waarde 100 geeft aan dat het watermerk volledig dekkend is en de waarde 0 geeft aan dat het watermerk volledig transparant is.

1. Registreer het watermerk.

   * Een `WatermarkManager` door het object aan te roepen `RightsManagementClient` object `getWatermarkManager` methode. Deze methode retourneert een `WatermarkManager` object.
   * Registreer het watermerk door de `WatermarkManager` object `registerWatermark` en het doorgeven van de `Watermark` object dat staat voor het watermerk dat moet worden geregistreerd. Deze methode retourneert een tekenreekswaarde die de identificatiewaarde van het watermerk vertegenwoordigt.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Snel starten (SOAP modus): een watermerk maken met de Java API&quot;

### Watermerken maken met de webservice-API {#create-watermarks-using-the-web-service-api}

Een watermerk maken met de API voor documentbeveiliging (webservice):

1. Maak een API-object voor Document Security Client.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Een `RightsManagementServiceClient` object met de standaardconstructor.
   * Een `RightsManagementServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `RightsManagementServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Stel de kenmerken van het watermerk in.

   * Een `WatermarkSpec` door het object aan te roepen `WatermarkSpec` constructor.
   * Stel de naam van het watermerk in door een tekenreekswaarde toe te wijzen aan de `WatermarkSpec` object `name` lid.
   * De watermerken instellen `id` door een tekenreekswaarde toe te wijzen aan de `WatermarkSpec` object `id` lid.
   * Voor elke watermerkeigenschap die moet worden ingesteld, maakt u een aparte eigenschap `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Stel de sleutelwaarde in door een waarde toe te wijzen aan de `MyMapOf_xsd_string_To_xsd_anyType_Item` object `key` data member (bijvoorbeeld `WaterBackCmd:OPACITY)`.
   * Stel de waarde in door een waarde toe te wijzen aan de `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` data member (bijvoorbeeld `.25`).
   * Een `MyArrayOf_xsd_anyType` object. Voor elke `MyMapOf_xsd_string_To_xsd_anyType_Item` object, activeert het `MyArrayOf_xsd_anyType` object `Add` methode. Geef de `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Wijs het `MyArrayOf_xsd_anyType` aan `WatermarkSpec` object `values` lid.

1. Registreer het watermerk.

   Registreer het watermerk door de `RightsManagementServiceClient` object `registerWatermark` en het doorgeven van de `WatermarkSpec` object dat staat voor het watermerk dat moet worden geregistreerd.

**Codevoorbeelden**

Zie Snel aan de slag voor codevoorbeelden met de Document Security-service:

* &quot;Quick Start (MTOM): Creating a watermark using the web service API&quot;
* &quot;Quick Start (SwaRef): Creating a watermark using the web service API&quot;

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Watermerken wijzigen {#modifying-watermarks}

U kunt een bestaand watermerk wijzigen met de Java API voor documentbeveiliging of de webservice-API. Als u een bestaand watermerk wilt wijzigen, haalt u het op, wijzigt u de kenmerken en werkt u het vervolgens bij op de server. Stel dat u een watermerk ophaalt en het kenmerk Dekking wijzigt. Voordat de wijziging van kracht wordt, moet u het watermerk bijwerken.

Wanneer u een watermerk wijzigt, is de wijziging van invloed op toekomstige documenten waarop het watermerk is toegepast. Dat wil zeggen dat bestaande PDF-documenten die het watermerk bevatten, niet worden beïnvloed.

>[!NOTE]
>
>Alleen gebruikers met beheerdersrechten voor documentbeveiliging kunnen watermerken wijzigen. Dit betekent dat u een dergelijke gebruiker moet opgeven wanneer u verbindingsinstellingen definieert die vereist zijn om een Document Security Service Client-object te maken.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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

**De kenmerken van de watermerken instellen**

Als u een bestaand watermerk wilt wijzigen, wijzigt u de waarde van een of meer watermerkkenmerken. Wanneer u via programmacode een watermerk bijwerkt met behulp van een webservice, moet u alle kenmerken instellen die oorspronkelijk zijn ingesteld, zelfs als de waarde niet verandert. Stel bijvoorbeeld dat de volgende watermerkkenmerken zijn ingesteld: `WaterBackCmd:IS_USERID_ENABLED`, `WaterBackCmd:IS_CUSTOMTEXT_ENABLED`, `WaterBackCmd:OPACITY`, en `WaterBackCmd:SRCTEXT`. Het enige kenmerk dat u wilt wijzigen, is `WaterBackCmd:OPACITY`, moet u instellen dat de andere waarden goed zijn.

>[!NOTE]
>
>Wanneer u de Java API gebruikt om een watermerk te wijzigen, hoeft u niet alle kenmerken op te geven. Stel het watermerkkenmerk in dat u wilt wijzigen.

>[!NOTE]
>
>Voor informatie over de namen van watermerkkenmerken raadpleegt u [Watermerken maken](protecting-documents-policies.md#creating-watermarks).

**Het watermerk bijwerken**

Nadat u de kenmerken van een watermerk hebt gewijzigd, moet u het watermerk bijwerken.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Watermerken maken](protecting-documents-policies.md#creating-watermarks)

### Watermerken wijzigen met de Java API {#modify-watermarks-using-the-java-api}

Een watermerk wijzigen met de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem JAR-bestanden voor clients, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `DocumentSecurityClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Haal het watermerk op dat u wilt wijzigen.

   Een `WatermarkManager` door het object aan te roepen `DocumentSecurityClient` object `getWatermarkManager` en geeft een tekenreekswaarde door die de naam van het watermerk aangeeft. Deze methode retourneert een `Watermark` object dat het watermerk vertegenwoordigt dat moet worden gewijzigd.

1. Stel de kenmerken van het watermerk in.

   Stel het kenmerk Dekking van het watermerk in door het `Watermark` object `setOpacity` methode en het overgaan van een geheelwaarde die het opaciteitniveau specificeert. De waarde 100 geeft aan dat het watermerk volledig dekkend is en de waarde 0 geeft aan dat het watermerk volledig transparant is.

   >[!NOTE]
   >
   >In dit voorbeeld wordt alleen het kenmerk opacity gewijzigd.

1. Werk het watermerk bij.

   * Werk het watermerk bij door de `WatermarkManager` object `updateWatermark` en geeft de `Watermark` object waarvan het kenmerk is gewijzigd.

**Codevoorbeelden**

Zie Snel starten (modus SOAP): Een watermerk wijzigen met behulp van de Java API-sectie voor codevoorbeelden met de documentbeveiligingsservice.

### Watermerken wijzigen met de webservice-API {#modify-watermarks-using-the-web-service-api}

Wijzig een watermerk met de API voor documentbeveiliging (webservice):

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Een `RightsManagementServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `DocumentSecurityServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Haal het watermerk op dat u wilt wijzigen.

   Haal het watermerk op dat u wilt wijzigen door het `DocumentSecurityServiceClient` object `getWatermarkByName` methode. Geef een tekenreekswaarde door die de naam van het watermerk aangeeft. Deze methode retourneert een `WatermarkSpec` object dat het watermerk vertegenwoordigt dat moet worden gewijzigd.

1. Stel de kenmerken van het watermerk in.

   * Voor elke watermerkeigenschap die moet worden bijgewerkt, maakt u een aparte `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Stel de sleutelwaarde in door een waarde toe te wijzen aan de `MyMapOf_xsd_string_To_xsd_anyType_Item` object `key` data member (bijvoorbeeld `WaterBackCmd:OPACITY)`.
   * Stel de waarde in door een waarde toe te wijzen aan de `MyMapOf_xsd_string_To_xsd_anyType_Item` object `value` data member (bijvoorbeeld `.50`).
   * Een `MyArrayOf_xsd_anyType` object. Voor elke `MyMapOf_xsd_string_To_xsd_anyType_Item` object, activeert het `MyArrayOf_xsd_anyType` object `Add` methode. Geef de `MyMapOf_xsd_string_To_xsd_anyType_Item` object.
   * Wijs het `MyArrayOf_xsd_anyType` aan `WatermarkSpec` object `values` lid.

1. Werk het watermerk bij.

   Werk het watermerk bij door de `DocumentSecurityServiceClient` object `updateWatermark` en het doorgeven van de `WatermarkSpec` object dat het watermerk vertegenwoordigt dat moet worden gewijzigd.

**Codevoorbeelden**

Zie het volgende snelle begin voor codevoorbeelden met gebruik van de Document Security-service:

* &quot;Quick Start (MTOM): Modifying a watermark using the web service API&quot;

## Zoeken naar gebeurtenissen {#searching-for-events}

De dienst van het Rights Management volgt specifieke acties aangezien zij voorkomen, zoals het toepassen van een beleid op een document, het openen van een beleid-beschermd document, en het intrekken van toegang tot documenten. Gebeurteniscontrole moet zijn ingeschakeld voor de service Rights Management of gebeurtenissen worden niet bijgehouden.

Gebeurtenissen behoren tot een van de volgende categorieën:

* Beheergebeurtenissen zijn handelingen die betrekking hebben op een beheerder, zoals het maken van een beheerdersaccount.
* Documentgebeurtenissen zijn handelingen die betrekking hebben op een document, zoals het sluiten van een document dat met een beleid is beveiligd.
* Beleidsgebeurtenissen zijn handelingen die betrekking hebben op een beleid, zoals het maken van een beleid.
* De gebeurtenissen van de dienst zijn acties met betrekking tot de dienst van het Rights Management, zoals het synchroniseren met de gebruikersfolder.

U kunt zoeken naar specifieke gebeurtenissen met behulp van de Rights Management Java API of de webservice-API. Door naar gebeurtenissen te zoeken, kunt u taken uitvoeren, zoals het creëren van een logboekdossier van bepaalde gebeurtenissen.

>[!NOTE]
>
>Voor meer informatie over de dienst van het Rights Management, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-10}

Voer de volgende stappen uit om te zoeken naar een Rights Management-gebeurtenis:

1. Inclusief projectbestanden.
1. Maak een Rights Management Client API-object.
1. Geef de gebeurtenis op waarnaar u wilt zoeken.
1. Zoeken naar de gebeurtenis.

**Projectbestanden opnemen**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**Een Rights Management Client API-object maken**

Alvorens u een de dienstverrichting van het Rights Management programmatically kunt uitvoeren, moet u een voorwerp van de de dienstcliënt van het Rights Management tot stand brengen. Als u de Java API gebruikt, maakt u een `DocumentSecurityClient` object. Als u de API voor webservices van het Rights Management gebruikt, maakt u een `DocumentSecurityServiceService` object.

**Geef de gebeurtenissen op waarnaar u wilt zoeken**

Geef op naar welke gebeurtenis moet worden gezocht. U kunt bijvoorbeeld zoeken naar het beleid om een gebeurtenis te maken, die optreedt wanneer een nieuw beleid wordt gemaakt.

**Zoeken naar de gebeurtenis**

Nadat u de gebeurtenis hebt opgegeven waarnaar moet worden gezocht, kunt u de Java API voor Rights Managementen of de API voor webservices van Rights Managementen gebruiken om naar de gebeurtenis te zoeken.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Zoeken naar gebeurtenissen met de Java API {#search-for-events-using-the-java-api}

U kunt naar gebeurtenissen zoeken met de API voor Rights Managementen (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Een Rights Management Client API-object maken

   Een `DocumentSecurityClient` object door de constructor ervan te gebruiken en een `ServiceClientFactory` object dat verbindingseigenschappen bevat.

1. Geef de gebeurtenissen op waarnaar u wilt zoeken

   * Een `EventManager` door het object aan te roepen `DocumentSecurityClient` object `getEventManager` methode. Deze methode retourneert een `EventManager` object.
   * Een `EventSearchFilter` object door de constructor ervan aan te roepen.
   * Geef de gebeurtenis op waarnaar u wilt zoeken door het dialoogvenster `EventSearchFilter` object `setEventCode` methode en het overgaan van een statisch gegevenslid dat tot `EventManager` klasse die de gebeurtenis vertegenwoordigt waarnaar moet worden gezocht. Als u bijvoorbeeld naar het beleid wilt zoeken, moet u `EventManager.POLICY_CREATE_EVENT`.

   >[!NOTE]
   >
   >U kunt aanvullende zoekcriteria definiëren door een aanroep te maken `EventSearchFilter` objectmethoden. Roep bijvoorbeeld het `setUserName` methode om een gebruiker op te geven die aan de gebeurtenis is gekoppeld.

1. Zoeken naar de gebeurtenis

   Zoeken naar de gebeurtenis door de `EventManager` object `searchForEvents` en het doorgeven van de `EventSearchFilter` object dat de zoekcriteria voor gebeurtenissen definieert. Deze methode retourneert een array met `Event` objecten.

**Codevoorbeelden**

Voor codevoorbeelden die de dienst van het Rights Management gebruiken, zie Snel begint:

* &quot;Snel starten (SOAP): zoeken naar gebeurtenissen met de Java API&quot;

### Zoeken naar gebeurtenissen met de webservice-API {#search-for-events-using-the-web-service-api}

U kunt naar gebeurtenissen zoeken met de Rights Management-API (webservice):

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een Rights Management Client API-object maken

   * Een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Een `DocumentSecurityServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `DocumentSecurityServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Geef de gebeurtenissen op waarnaar u wilt zoeken

   * Een `EventSpec` object met behulp van de constructor.
   * Geef het begin op van de periode waarin de gebeurtenis heeft plaatsgevonden door het instellen van de `EventSpec` object `firstTime.date` lid met gegevens `DataTime` instantie die het begin van het datumbereik vertegenwoordigt wanneer de gebeurtenis plaatsvond.
   * De waarde toewijzen `true` aan de `EventSpec` object `firstTime.dateSpecified` lid.
   * Geef het einde op van de periode waarin de gebeurtenis heeft plaatsgevonden door het instellen van de `EventSpec` object `lastTime.date` lid met gegevens `DataTime` instantie die het einde van het datumbereik vertegenwoordigt wanneer de gebeurtenis heeft plaatsgevonden.
   * De waarde toewijzen `true` aan de `EventSpec` object `lastTime.dateSpecified` lid.
   * Stel de gebeurtenis waarnaar u wilt zoeken in door een tekenreekswaarde toe te wijzen aan de `EventSpec` object `eventCode` lid. In de volgende tabel worden de numerieke waarden weergegeven die u aan deze eigenschap kunt toewijzen:

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

   Zoeken naar de gebeurtenis door de `DocumentSecurityServiceClient` object `searchForEvents` en het doorgeven van de `EventSpec` object dat de gebeurtenis vertegenwoordigt waarnaar moet worden gezocht en het maximale aantal resultaten. Deze methode retourneert een `MyArrayOf_xsd_anyType` verzameling waarbij elk element een `AuditSpec` -instantie. Een `AuditSpec` kunt u informatie opvragen over de gebeurtenis, zoals het tijdstip waarop deze heeft plaatsgevonden. De `AuditSpec` instantie bevat een `timestamp` gegevenslid dat deze informatie specificeert.

**Codevoorbeelden**

Voor codevoorbeelden die de dienst van het Rights Management gebruiken, zie Snel begint:

* &quot;Snel starten (MTOM): zoeken naar gebeurtenissen met behulp van de webservice-API&quot;
* &quot;Quick Start (SwaRef): zoeken naar gebeurtenissen met behulp van de webservice-API&quot;

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)

[AEM Forms aanroepen met SwaRef](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-swaref)

## Beleid toepassen op Word-documenten {#applying-policies-to-word-documents}

Naast PDF-documenten biedt de Rights Management-service ondersteuning voor aanvullende documentindelingen, zoals een Microsoft Word-document (DOC-bestand) en andere Microsoft Office-bestandsindelingen. U kunt bijvoorbeeld een beleid toepassen op een Word-document om dit te beveiligen. Door een beleid op een document van Word toe te passen, beperkt u toegang tot het document. U kunt geen beleid op een document toepassen als het document reeds met een beleid wordt beveiligd.

U kunt het gebruik van een beleid-beschermd document van Word controleren nadat u het verspreidt. Dat wil zeggen dat u kunt zien hoe het document wordt gebruikt en wie het gebruikt. U kunt bijvoorbeeld zien wanneer iemand het document heeft geopend.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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

Hiermee wordt een Word-document opgehaald om een beleid toe te passen. Nadat u een beleid op het document van Word toepast, worden de gebruikers beperkt wanneer het gebruiken van het document. Als het beleid bijvoorbeeld niet toestaat dat het document offline wordt geopend, moeten gebruikers online zijn om het document te openen.

**Een bestaand beleid toepassen op het Word-document**

Als u een beleid wilt toepassen op een Word-document, moet u verwijzen naar een bestaand beleid en opgeven tot welke beleidsset het beleid behoort. De gebruiker die de verbindingseigenschappen instelt, moet toegang hebben tot het opgegeven beleid. Als dat niet het geval is, treedt een uitzondering op.

**Het Word-document opslaan**

Nadat de documentbeveiligingsservice een beleid heeft toegepast op een Word-document, kunt u het met een beleid beveiligde Word-document opslaan als een DOC-bestand.

**Zie ook**

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[Toegang tot documenten intrekken](protecting-documents-policies.md#revoking-access-to-documents)

### Een beleid toepassen op een Word-document met behulp van de Java API {#apply-a-policy-to-a-word-document-using-the-java-api}

Een beleid toepassen op een Word-document met behulp van de API voor documentbeveiliging (Java):

1. Inclusief projectbestanden.

   Neem client-JAR-bestanden, zoals adobe-rightManagement-client.jar, op in het klassenpad van uw Java-project.

1. Maak een API-object voor Document Security Client.

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `DocumentSecurityClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Een Word-document ophalen.

   * Een `java.io.FileInputStream` object dat het Word-document vertegenwoordigt met behulp van de constructor en een tekenreekswaarde doorgeeft die de locatie van het Word-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Pas een bestaand beleid op het document van Word toe.

   * Een `DocumentManager` door het object aan te roepen `DocumentSecurityClient` object `getDocumentManager` methode.
   * Pas een beleid op het document van Word toe door aan te halen `DocumentManager` object `protectDocument` en geeft de volgende waarden door:

      * De `com.adobe.idp.Document` -object dat het Word-document bevat waarop het beleid wordt toegepast.
      * Een tekenreekswaarde die de naam van het document aangeeft.
      * Een tekenreekswaarde die de naam opgeeft van de beleidsset waartoe het beleid behoort. U kunt een `null` waarde die resulteert in de `MyPolicies` de gebruikte beleidsset.
      * Een tekenreekswaarde die de beleidsnaam opgeeft.
      * Een tekenreekswaarde die de naam vertegenwoordigt van het gebruikersbeheerdomein van de gebruiker die de uitgever van het document is. Deze parameterwaarde is optioneel en kan null zijn (als deze parameter null is, moet de volgende parameterwaarde null zijn).
      * Een tekenreekswaarde die de naam vertegenwoordigt van de canonieke naam van de gebruiker van de gebruikersmanager die de uitgever van het document is. Deze parameterwaarde is optioneel en kan `null` (als deze parameter `null`moet de vorige parameterwaarde `null`).
      * A `com.adobe.livecycle.rightsmanagement.Locale` dat de landinstelling vertegenwoordigt die wordt gebruikt voor het selecteren van de MS Office-sjabloon. Deze parameterwaarde is optioneel en u kunt `null`.

     De `protectDocument` methode retourneert een `RMSecureDocumentResult` -object dat het door het beleid beveiligde Word-document bevat.

1. Sla het Word-document op.

   * De `RMSecureDocumentResult` object `getProtectedDoc` om het door het beleid beveiligde Word-document op te halen. Deze methode retourneert een `com.adobe.idp.Document` object.
   * Een `java.io.File` -object en zorg ervoor dat de bestandsextensie DOC is.
   * De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `Document` object naar het bestand (gebruik de `Document` object dat is geretourneerd door de `getProtectedDoc` methode).

**Codevoorbeelden**

Zie het volgende snelle begin voor codevoorbeelden met gebruik van de Document Security-service:

* &quot;Snel starten (SOAP modus): beleid toepassen op een Word-document met behulp van de Java API&quot;

### Een beleid toepassen op een Word-document met behulp van de webservice-API {#apply-a-policy-to-a-word-document-using-the-web-service-api}

Pas een beleid op een document van Word toe door de Veiligheid API van het Document (Webdienst) te gebruiken:

1. Inclusief projectbestanden.

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/DocumentSecurityService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Maak een API-object voor Document Security Client.

   * Een `DocumentSecurityServiceClient` object met de standaardconstructor.
   * Een `DocumentSecurityServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/DocumentSecurityService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `DocumentSecurityServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `DocumentSecurityServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `DocumentSecurityServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een Word-document ophalen.

   * Een `BLOB` object met behulp van de constructor. De `BLOB` wordt gebruikt om een Word-document op te slaan waarop een beleid wordt toegepast.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het Word-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. Bepaal de grootte van de bytearray door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` methode. Geef de bytearray, de startpositie en de streamlengte door om te lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Pas een bestaand beleid op het document van Word toe.

   Pas een beleid op het document van Word toe door aan te halen `DocumentSecurityServiceClient` object `protectDocument` en geeft de volgende waarden door:

   * De `BLOB` -object dat het Word-document bevat waarop het beleid wordt toegepast.
   * Een tekenreekswaarde die de naam van het document aangeeft.
   * Een tekenreekswaarde die de naam opgeeft van de beleidsset waartoe het beleid behoort. U kunt een `null` waarde die resulteert in de `MyPolicies` de gebruikte beleidsset.
   * Een tekenreekswaarde die de beleidsnaam opgeeft.
   * Een tekenreekswaarde die de naam vertegenwoordigt van het gebruikersbeheerdomein van de gebruiker die de uitgever van het document is. Deze parameterwaarde is optioneel en kan null zijn (als deze parameter null is, moet de volgende parameterwaarde `null`).
   * Een tekenreekswaarde die de naam vertegenwoordigt van de canonieke naam van de gebruiker van de gebruikersmanager die de uitgever van het document is. Deze parameterwaarde is optioneel en kan null zijn (als deze parameter null is, moet de vorige parameterwaarde `null`).
   * A `RMLocale` waarde die de waarde van de landinstelling opgeeft (bijvoorbeeld `RMLocale.en`).
   * Een parameter van de koordoutput die wordt gebruikt om de waarde van beleidsidentificatie op te slaan.
   * Een parameter van de koordoutput die wordt gebruikt om de beleid-beschermde herkenningstekenwaarde op te slaan.
   * Een parameter van de koordoutput die wordt gebruikt om het mime type op te slaan (bijvoorbeeld `application/doc`).

   De `protectDocument` methode retourneert een `BLOB` -object dat het door het beleid beveiligde Word-document bevat.

1. Sla het Word-document op.

   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het met een beleid beveiligde Word-document vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `protectDocument` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` lid.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.
   * Schrijf de inhoud van de bytearray naar een Word-bestand door het `System.IO.BinaryWriter` object `Write` en geeft u de bytearray door.

**Codevoorbeelden**

Zie het volgende snelle begin voor codevoorbeelden met gebruik van de Document Security-service:

* &quot;Quick Start (MTOM): Applying a policy to a Word document using the web service API &quot;

## Beleid verwijderen uit Word-documenten {#removing-policies-from-word-documents}

U kunt een beleid uit een beleid-beschermd document van Word verwijderen om veiligheid uit het document te verwijderen. Dat wil zeggen, als u niet langer wilt dat het document wordt beschermd door een beleid. Als u een beleid-beschermd document van Word met een nieuwer beleid wilt bijwerken, dan in plaats van het verwijderen van het beleid en het toevoegen van het bijgewerkte beleid, is het efficiënter om het beleid te schakelen.

>[!NOTE]
>
>Voor meer informatie over de dienst van de Veiligheid van het Document, zie [Services Reference for AEM Forms](https://www.adobe.com/go/learn_aemforms_services_63).

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

Woord-document dat door een beleid is beveiligd, ophalen om een beleid te verwijderen. Als u probeert om een beleid uit een document van Word te verwijderen dat niet door een beleid wordt beschermd, zult u een uitzondering veroorzaken.

**Het beleid verwijderen uit het Word-document**

U kunt een beleid uit een beleid-beschermd document van Word verwijderen op voorwaarde dat een beheerder in de verbindingsmontages wordt gespecificeerd. Zo niet, dan moet het beleid dat wordt gebruikt om een document te beveiligen het `SWITCH_POLICY` toestemming om een beleid uit een document van Word te verwijderen. De gebruiker die is opgegeven in de AEM Forms-verbindingsinstellingen moet ook over deze machtiging beschikken. Anders wordt een uitzondering gegenereerd.

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

   * Een `ServiceClientFactory` object dat verbindingseigenschappen bevat.
   * Een `RightsManagementClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object.

1. Een met beleid beveiligd Word-document ophalen

   * Een `java.io.FileInputStream` -object dat het door een beleid beveiligde Word-document vertegenwoordigt door de constructor ervan te gebruiken en een tekenreekswaarde door te geven die de locatie van het Word-document aangeeft.
   * Een `com.adobe.idp.Document` object door de constructor ervan te gebruiken en de `java.io.FileInputStream` object.

1. Het beleid verwijderen uit het Word-document

   * Een `DocumentManager` door het object aan te roepen `RightsManagementClient` object `getDocumentManager` methode.
   * Verwijder een beleid uit het document van Word door aan te halen `DocumentManager` object `removeSecurity` en het doorgeven van de `com.adobe.idp.Document` -object dat het door het beleid beveiligde Word-document bevat. Deze methode retourneert een `com.adobe.idp.Document` object dat een onbeveiligd Word-document bevat.

1. Het onbeveiligde Word-document opslaan

   * Een `java.io.File` -object en zorg ervoor dat de bestandsextensie DOC is.
   * De `Document` object `copyToFile` methode om de inhoud van de `Document` object naar het bestand (gebruik de `Document` object dat is geretourneerd door de `removeSecurity` methode).

**Codevoorbeelden**

Zie het volgende snelle begin voor codevoorbeelden met gebruik van de Document Security-service:

* &quot;Snel starten (SOAP modus): Een beleid verwijderen uit een Word-document met de Java API &quot;

### Een beleid verwijderen uit een Word-document met de webservice-API {#remove-a-policy-from-a-word-document-using-the-web-service-api}

Verwijder een beleid uit een beleid-beschermd document van Word door de Veiligheid API van het Document (Webdienst te gebruiken:

1. Projectbestanden opnemen

   Creeer een Microsoft .NET project dat MTOM gebruikt. Zorg ervoor dat u de volgende definitie van WSDL gebruikt: `http://localhost:8080/soap/services/RightsManagementService?WSDL&lc_version=9.0.1`.

   >[!NOTE]
   >
   >Vervangen `localhost` met het IP-adres van de server die als host fungeert voor AEM Forms.

1. Een API-object voor documentbeveiliging maken

   * Een `RightsManagementServiceClient` object met de standaardconstructor.
   * Een `RightsManagementServiceClient.Endpoint.Address` object door het `System.ServiceModel.EndpointAddress` constructor. Geef een tekenreekswaarde die de WSDL opgeeft door aan de AEM Forms-service (bijvoorbeeld `http://localhost:8080/soap/services/RightsManagementService?WSDL`.) U hoeft de `lc_version` kenmerk. Dit kenmerk wordt gebruikt wanneer u een serviceverwijzing maakt.)
   * Een `System.ServiceModel.BasicHttpBinding` object door de waarde van het object op te halen `RightsManagementServiceClient.Endpoint.Binding` veld. De geretourneerde waarde omzetten in `BasicHttpBinding`.
   * Stel de `System.ServiceModel.BasicHttpBinding` object `MessageEncoding` veld naar `WSMessageEncoding.Mtom`. Deze waarde zorgt ervoor dat MTOM wordt gebruikt.
   * Laat basisauthentificatie van HTTP door de volgende taken uit te voeren toe:

      * Wijs de gebruikersnaam van het AEM aan het veld toe `RightsManagementServiceClient.ClientCredentials.UserName.UserName`.
      * De bijbehorende wachtwoordwaarde aan het veld toewijzen `RightsManagementServiceClient.ClientCredentials.UserName.Password`.
      * De constante waarde toewijzen `HttpClientCredentialType.Basic` naar het veld `BasicHttpBindingSecurity.Transport.ClientCredentialType`.

   * De constante waarde toewijzen `BasicHttpSecurityMode.TransportCredentialOnly` naar het veld `BasicHttpBindingSecurity.Security.Mode`.

1. Een met beleid beveiligd Word-document ophalen

   * Een `BLOB` object met behulp van de constructor. De `BLOB` -object wordt gebruikt om het door het beleid beveiligde Word-document op te slaan waaruit het beleid wordt verwijderd.
   * Een `System.IO.FileStream` -object door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het Word-document en de modus waarin het bestand moet worden geopend, vertegenwoordigt.
   * Maak een bytearray waarin de inhoud van de `System.IO.FileStream` object. U kunt de grootte van de bytearray bepalen door de `System.IO.FileStream` object `Length` eigenschap.
   * De bytearray vullen met streamgegevens door de `System.IO.FileStream` object `Read` en geeft u de bytearray, de startpositie en de streamlengte door die u wilt lezen.
   * Vul de `BLOB` object door het toe te wijzen `MTOM` veld met de inhoud van de bytearray.

1. Het beleid verwijderen uit het Word-document

   Verwijder het beleid uit het document van Word door aan te halen `RightsManagementServiceClient` object `removePolicySecurity` en het doorgeven van de `BLOB` -object dat het door het beleid beveiligde Word-document bevat. Deze methode retourneert een `BLOB` object dat een onbeveiligd Word-document bevat.

1. Het onbeveiligde Word-document opslaan

   * Een `System.IO.FileStream` door de constructor ervan aan te roepen en een tekenreekswaarde door te geven die de bestandslocatie van het onbeveiligde Word-document vertegenwoordigt.
   * Maak een bytearray waarin de gegevensinhoud van de `BLOB` object dat is geretourneerd door de `removePolicySecurity` methode. Vul de bytearray met de waarde van de `BLOB` object `MTOM` veld.
   * Een `System.IO.BinaryWriter` object door de constructor aan te roepen en de `System.IO.FileStream` object.

**Codevoorbeelden**

Zie het volgende snelle begin voor codevoorbeelden met gebruik van de Document Security-service:

* &quot;Quick Start (MTOM): Removing a policy from a Word document using the web service API&quot;

**Zie ook**

[AEM Forms aanroepen met MTOM](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-mtom)
