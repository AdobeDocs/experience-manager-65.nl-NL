---
title: AEM Forms aanroepen met de JavaAPI
description: Gebruik het AEM Forms Java API for RMI-transportprotocol voor externe aanroeping, VM-transport voor lokale aanroeping, SOAP voor externe aanroeping, andere verificatie, zoals gebruikersnaam en wachtwoord, en synchrone en asynchrone aanroepingsverzoeken.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
role: Developer
exl-id: 036c35c1-1be7-4825-bbb6-ea025e49c6f6
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '5333'
ht-degree: 0%

---

# AEM Forms aanroepen met de Java API {#invoking-aem-forms-using-the-javaapi}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

AEM Forms kan worden aangeroepen met de AEM Forms Java API. Wanneer u de AEM Forms Java API gebruikt, kunt u de Invocation API- of Java-clientbibliotheken gebruiken. Java-clientbibliotheken zijn beschikbaar voor services zoals de service Rights Management. Met deze sterk getypeerde API&#39;s kunt u Java-toepassingen ontwikkelen die AEM Forms aanroepen.

De oproepings-API zijn klassen die zich in het `com.adobe.idp.dsc` -pakket bevinden. Met deze klassen kunt u een aanroepingsverzoek rechtstreeks naar een service verzenden en een geretourneerde aanroepingsreactie afhandelen. Gebruik de oproepings-API om kortstondige of langlevende processen aan te roepen die met Workbench zijn gemaakt.

De geadviseerde manier om een dienst programmatically aan te halen is een de cliëntbibliotheek van Java te gebruiken die aan de dienst in tegenstelling tot de Inroeping API beantwoordt. Als u bijvoorbeeld de coderingsservice wilt aanroepen, gebruikt u de clientbibliotheek van de coderingsservice. Om een de dienstverrichting van de Encryptie uit te voeren, haal een methode aan die tot het de dienstcliëntvoorwerp van de Encryptie behoort. U kunt een PDF-document versleutelen met een wachtwoord door de methode `encryptPDFUsingPassword` van het object `EncryptionServiceClient` aan te roepen.

De Java API ondersteunt de volgende functies:

* Het vervoerprotocol van RMI voor verre aanroeping
* VM-transport voor lokale aanroeping
* SOAP voor externe aanroeping
* Andere verificatie, zoals gebruikersnaam en wachtwoord
* Synchrone en asynchrone oproepverzoeken

[Inclusief AEM Forms Java-bibliotheekbestanden](#including-aem-forms-java-library-files)

[Het aanhalen van mens-Centric langlevende Processen](invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[AEM Forms aanroepen met webservices](/help/forms/developing/invoking-aem-forms-using-web.md)

[Verbindingseigenschappen instellen](#setting-connection-properties)

[Gegevens doorgeven aan AEM Forms-services met de Java API](#passing-data-to-aem-forms-services-using-the-java-api)

[Een service aanroepen met een Java-clientbibliotheek](#invoking-a-service-using-a-java-client-library)

[Een kortstondig proces aanroepen met de API voor aanroepen](#invoking-a-short-lived-process-using-the-invocation-api)

[Een Java-webtoepassing maken die een menselijk-centrisch proces van lange duur oproept](/help/forms/developing/invoking-human-centric-long-lived.md)

## Inclusief AEM Forms Java-bibliotheekbestanden {#including-aem-forms-java-library-files}

Als u een AEM Forms-service programmatisch wilt aanroepen met de Java API, neemt u de vereiste bibliotheekbestanden (JAR-bestanden) op in het klassepad van uw Java-project. De JAR-bestanden die u in het klassepad van uw clienttoepassing opneemt, zijn afhankelijk van verschillende factoren:

* De AEM Forms-service die moet worden aangeroepen. Een cliënttoepassing kan één of meerdere diensten aanhalen.
* De modus waarin u een AEM Forms-service wilt aanroepen. U kunt de modus EJB of SOAP gebruiken. (Zie [&#x200B; Plaatsende verbindingseigenschappen &#x200B;](invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>(Alleen Turkije) Start de AEM Forms-server met de opdracht `standalone.bat -b <Server IP> -c lc_turnkey.xml` om een server-IP voor EJB op te geven

* De J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

### Servicespecifieke JAR-bestanden {#service-specific-jar-files}

In de volgende tabel worden de JAR-bestanden weergegeven die nodig zijn om AEM Forms-services aan te roepen.

<table>
 <thead>
  <tr>
   <th><p>Bestand</p></th>
   <th><p>Beschrijving</p></th>
   <th><p>Locatie</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>adobe-livecycle-client.jar</p></td>
   <td><p>Moet altijd worden opgenomen in het klassepad van een Java-clienttoepassing.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-usermanager-client.jar</p></td>
   <td><p>Moet altijd worden opgenomen in het klassepad van een Java-clienttoepassing.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-utilities.jar</p></td>
   <td><p>Moet altijd worden opgenomen in het klassepad van een Java-clienttoepassing.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk//client-libs/&lt;app server&gt;</p></td>
  </tr>
  <tr>
   <td><p>adobe-applicationmanager-client-sdk.jar</p></td>
   <td><p>Vereist om de dienst van de Manager van de Toepassing aan te halen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-assembler-client.jar</p></td>
   <td><p>Vereist om de dienst van de Assembler aan te halen. </p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-backup-restore-client-sdk.jar</p></td>
   <td><p>Vereist om de service-API voor back-up en herstel aan te roepen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-barcodedforms-client.jar</p></td>
   <td><p>Vereist om de service voor formulieren met streepjescodes aan te roepen. </p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-convertpdf-client.jar</p></td>
   <td><p>Vereist om de dienst van de PDF van de Bekeerling aan te halen. </p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-distiller-client.jar</p></td>
   <td><p>Vereist om de Distiller-service aan te roepen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-docconverter-client.jar</p></td>
   <td><p>Vereist om de dienst DocConverter aan te halen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-contentservices-client.jar</p></td>
   <td><p>Vereist om de service Documentbeheer aan te roepen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-encryption-client.jar</p></td>
   <td><p>Vereist om de dienst van de Encryptie aan te halen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-forms-client.jar</p></td>
   <td><p>Vereist om de Forms-service aan te roepen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-formdataintegration-client.jar</p></td>
   <td><p>Vereist om de dienst van de Integratie van de Gegevens van de Vorm aan te halen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-generatepdf-client.jar</p></td>
   <td><p>Vereist om de Generate dienst van PDF aan te halen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-generate3dpdf-client.jar</p></td>
   <td><p>Vereist om de Generate 3D dienst van PDF aan te halen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-jobmanager-client-sdk.jar</p></td>
   <td><p>Vereist om de service Taakbeheer aan te roepen. </p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-output-client.jar</p></td>
   <td><p>Vereist om de dienst van de Output aan te halen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-pdfutility-client.jar</p></td>
   <td><p>Vereist om de dienst van de Hulpprogramma's van de PDF of XMP aan te halen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-reader-extensions-client.jar</p></td>
   <td><p>Vereist om de Acrobat Reader DC-extensieservice aan te roepen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-repository-client.jar</p><p>commons-codec-1.3.jar</p></td>
   <td><p>Vereist om de dienst van de Bewaarplaats aan te halen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p><p>&lt;<i> installeer folder </i>&gt;/sdk/cliënt-libs \ derde</p></td>
  </tr>
  <tr>
   <td>
    <ul>
     <li><p>adobe-rightsmanagement-client.jar</p></li>
     <li><p>namespace.jar</p></li>
     <li><p>jaxb-api.jar</p></li>
     <li><p>jaxb-impl.jar</p></li>
     <li><p>jaxb-libs.jar</p></li>
     <li><p>jaxb-xjc.jar</p></li>
     <li><p>relaxngDatatype.jar</p></li>
     <li><p>xsdlib.jar</p></li>
    </ul></td>
   <td><p>Vereist om de dienst van het Rights Management aan te halen.</p><p>Als AEM Forms wordt geïmplementeerd op JBoss, neemt u al deze bestanden op. </p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p><p>JBoss-specifieke lib-map</p></td>
  </tr>
  <tr>
   <td><p>adobe-signatures-client.jar</p></td>
   <td><p>Vereist om de service Handtekening aan te roepen.</p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-taskmanager-client-sdk.jar</p></td>
   <td><p>Vereist om de dienst van de Manager van de Taak aan te halen. </p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-truststore-client.jar</p></td>
   <td><p>Vereist om de dienst van de Opslag van het Vertrouwen aan te halen. </p></td>
   <td><p>&lt;<i> installatiemap </i>&gt;/sdk/client-libs/common</p></td>
  </tr>
 </tbody>
</table>

### Verbindingsmodus en JAR-bestanden voor J2EE-toepassing {#connection-mode-and-j2ee-application-jar-files}

In de volgende tabel worden de JAR-bestanden weergegeven die afhankelijk zijn van de verbindingsmodus en de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

<table>
 <thead>
  <tr>
   <th><p>Bestand</p> </th>
   <th><p>Beschrijving</p> </th>
   <th><p>Locatie</p> </th>
  </tr>
 &lt;/thead align="left"&gt;
 <tbody>
  <tr>
   <td>
    <ul>
     <li><p>activation.jar</p> </li>
     <li><p>axis.jar</p> </li>
     <li><p>commons-codec-1.3.jar</p> </li>
     <li><p>commons-collections-3.1.jar</p> </li>
     <li><p>commons-discovery.jar</p> </li>
     <li><p>commons-logging.jar</p> </li>
     <li><p>dom3-xml-apis-2.5.0.jar</p> </li>
     <li><p>jaxen-1,1-bèta-9.jar</p> </li>
     <li><p>jaxrpc.jar</p> </li>
     <li><p>log4j.jar</p> </li>
     <li><p>mail.jar</p> </li>
     <li><p>saaj.jar</p> </li>
     <li><p>wsdl4j.jar</p> </li>
     <li><p>xalan.jar</p> </li>
     <li><p>xbean.jar</p> </li>
    </ul>
    <ul>
     <li>xercesImpl.jar<br /> </li>
     <li>commons-httpclient-3.1.jar</li>
    </ul> <p> </p> </td>
   <td><p>Als AEM Forms wordt aangeroepen in de SOAP-modus, neemt u deze JAR-bestanden op.</p> </td>
   <td><p>&lt;<em> installeer folder </em>&gt;/sdk/cliënt-libs/derdepartij</p> </td>
  </tr>
  <tr>
   <td><p> jboss-client.jar</p> </td>
   <td><p>Als AEM Forms is geïmplementeerd op JBoss Application Server, neemt u dit JAR-bestand op.</p> <p>Vereiste klassen worden niet gevonden door de klasseleider als jreliëf-client.jar en de jars waarnaar wordt verwezen, zich niet op dezelfde locatie bevinden.</p> </td>
   <td><p>JBoss client lib directory</p> <p>Als u uw clienttoepassing op dezelfde J2EE-toepassingsserver implementeert, hoeft u dit bestand niet op te nemen.</p> </td>
  </tr>
  <tr>
   <td><p>wlclient.jar</p> </td>
   <td><p>Als AEM Forms wordt geïmplementeerd op BEA WebLogic Server®, neemt u dit JAR-bestand op.</p> </td>
   <td><p>WebLogic-specifieke lib-directory</p> <p>Als u uw clienttoepassing op dezelfde J2EE-toepassingsserver implementeert, hoeft u dit bestand niet op te nemen.</p> </td>
  </tr>
  <tr>
   <td>
    <ul>
     <li><p>com.ibm.ws.admin.client_6.1.0.jar</p> </li>
     <li><p>com.ibm.ws.webservices.thinclient_6.1.0.jar</p> </li>
    </ul> </td>
   <td>
    <ul>
     <li><p>Als AEM Forms wordt geïmplementeerd op WebSphere Application Server, neemt u deze JAR-bestanden op.</p> </li>
     <li><p>(com.ibm.ws.webservices.thinclient_6.1.0.jar is vereist voor het oproepen van webservices).</p> </li>
    </ul> </td>
   <td><p>WebSphere-specifieke lib folder (<em> [WAS_HOME] </em>/runtimes)</p> <p>Als u uw clienttoepassing op dezelfde J2EE-toepassingsserver implementeert, hoeft u deze bestanden niet op te nemen.</p> </td>
  </tr>
 </tbody>
</table>

### Oproepen van scenario&#39;s {#invoking-scenarios}

In de volgende tabel worden de aanroepingsscenario&#39;s aangegeven en worden de JAR-bestanden weergegeven die AEM Forms moeten aanroepen.

<table>
 <thead>
  <tr>
   <th><p>Services</p> </th>
   <th><p>Inroeping, modus</p> </th>
   <th><p>J2EE-toepassingsserver</p> </th>
   <th><p>Vereiste JAR-bestanden</p> </th>
  </tr>
 &lt;/thead align="left"&gt;
 <tbody>
  <tr>
   <td><p>Forms-service</p> </td>
   <td><p>EJB</p> </td>
   <td><p>JBoss</p> </td>
   <td>
    <ul>
     <li><p>adobe-livecycle-client.jar</p> </li>
     <li><p>adobe-usermanager-client.jar</p> </li>
    </ul>
    <ul>
     <li>jboss-client.jar</li>
    </ul>
    <ul>
     <li>adobe-forms-client.jar<br /> </li>
     <li>commons-httpclient-3.1.jar</li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Forms-service</p> <p>Acrobat Reader DC-extensieservice</p> <p>Handtekeningenservice</p> </td>
   <td><p>EJB</p> </td>
   <td><p>JBoss</p> </td>
   <td>
    <ul>
     <li><p>adobe-livecycle-client.jar</p> </li>
     <li><p>adobe-usermanager-client.jar</p> </li>
    </ul>
    <ul>
     <li>jboss-client.jar<br /> </li>
     <li>commons-httpclient-3.1.jar</li>
    </ul>
    <ul>
     <li><p>adobe-forms-client.jar</p> </li>
     <li><p>adobe-reader-extensions-client.jar</p> </li>
     <li><p>adobe-signatures-client.jar</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Forms-service</p> </td>
   <td><p>SOAP</p> </td>
   <td><p>WebLogic</p> </td>
   <td>
    <ul>
     <li><p>adobe-livecycle-client.jar</p> </li>
     <li><p>adobe-usermanager-client.jar</p> </li>
     <li><p>wlclient.jar</p> </li>
     <li><p>activation.jar</p> </li>
     <li><p>axis.jar</p> </li>
     <li><p>commons-codec-1.3.jar</p> </li>
     <li><p>commons-collections-3.1.jar</p> </li>
     <li><p>commons-discovery.jar</p> </li>
     <li><p>commons-logging.jar</p> </li>
     <li><p>dom3-xml-apis-2.5.0.jar</p> </li>
     <li><p>jai_imageio.jar</p> </li>
     <li><p>jaxen-1,1-bèta-9.jar</p> </li>
     <li><p>jaxrpc.jar</p> </li>
     <li><p>log4j.jar</p> </li>
     <li><p>mail.jar</p> </li>
     <li><p>saaj.jar</p> </li>
     <li><p>wsdl4j.jar</p> </li>
     <li><p>xalan.jar</p> </li>
     <li><p>xbean.jar</p> </li>
     <li><p>xercesImpl.jar</p> </li>
     <li><p>adobe-forms-client.jar</p> </li>
    </ul> </td>
  </tr>
  <tr>
   <td><p>Forms-service</p> <p>Acrobat Reader DC-extensieservice</p> <p>Handtekeningenservice</p> </td>
   <td><p>SOAP</p> </td>
   <td><p>WebLogic</p> </td>
   <td>
    <ul>
     <li><p>adobe-livecycle-client.jar</p> </li>
     <li><p>adobe-usermanager-client.jar</p> </li>
     <li><p>wlclient.jar</p> </li>
     <li><p>activation.jar</p> </li>
     <li><p>axis.jar</p> </li>
     <li><p>commons-codec-1.3.jar</p> </li>
     <li><p>commons-collections-3.1.jar</p> </li>
     <li><p>commons-discovery.jar</p> </li>
     <li><p>commons-logging.jar</p> </li>
     <li><p>dom3-xml-apis-2.5.0.jar</p> </li>
     <li><p>jai_imageio.jar</p> </li>
     <li><p>jaxen-1,1-bèta-9.jar</p> </li>
     <li><p>jaxrpc.jar</p> </li>
     <li><p>log4j.jar</p> </li>
     <li><p>mail.jar</p> </li>
     <li><p>saaj.jar</p> </li>
     <li><p>wsdl4j.jar</p> </li>
     <li><p>xalan.jar</p> </li>
     <li><p>xbean.jar</p> </li>
     <li><p>xercesImpl.jar</p> </li>
     <li><p>adobe-forms-client.jar</p> </li>
     <li><p>adobe-reader-extensions-client.jar</p> </li>
     <li><p>adobe-signatures-client.jar</p> </li>
    </ul> </td>
  </tr> xmp-uti
 </tbody>
</table>

### JAR-bestanden bijwerken {#upgrading-jar-files}

Als u een upgrade uitvoert van LiveCycle naar AEM Forms, wordt u aangeraden de AEM Forms JAR-bestanden op te nemen in het klassenpad van uw Java-project. Als u bijvoorbeeld services zoals de service Rights Management gebruikt, treedt er een compatibiliteitsprobleem op als u geen AEM Forms JAR-bestanden opneemt in het klassenpad.

Ervan uitgaande dat u een upgrade uitvoert naar AEM Forms. Als u een Java-toepassing wilt gebruiken die de service Rights Management aanroept, neemt u de AEM Forms-versies van de volgende JAR-bestanden op:

* adobe-rightsmanagement-client.jar
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar

**zie ook**

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

[Gegevens doorgeven aan AEM Forms-services met de Java API](invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api)

[Een service aanroepen met een Java-clientbibliotheek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Verbindingseigenschappen instellen {#setting-connection-properties}

U stelt verbindingseigenschappen in om AEM Forms aan te roepen wanneer u de Java API gebruikt. Geef bij het instellen van eigenschappen voor verbindingen op of services extern of lokaal moeten worden aangeroepen en geef ook de verbindingsmodus en verificatiewaarden op. De waarden van de authentificatie worden vereist als de dienstveiligheid wordt toegelaten. Nochtans, als de dienstveiligheid gehandicapt is, is het niet noodzakelijk om authentificatiewaarden te specificeren.

De verbindingsmodus kan SOAP of EJB zijn. De modus EJB maakt gebruik van het RMI/IIOP-protocol en de prestaties van de modus EJB zijn beter dan die van de SOAP. De SOAP modus wordt gebruikt om een J2EE-toepassingsserverafhankelijkheid te elimineren of wanneer een firewall zich tussen AEM Forms en de clienttoepassing bevindt. De SOAP wijze gebruikt het HTTPS protocol als onderliggend vervoer en kan over firewallgrenzen communiceren. Als noch een J2EE-toepassingsserverafhankelijkheid, noch een firewall een probleem is, wordt u aangeraden de EJB-modus te gebruiken.

Als u een AEM Forms-service wilt aanroepen, stelt u de volgende verbindingseigenschappen in:

* **DSC_DEFAULT_EJB_ENDPOINT:** Als u de verbindingswijze EJB gebruikt, vertegenwoordigt deze waarde URL van de J2EE toepassingsserver waarop AEM Forms wordt opgesteld. Als u AEM Forms op afstand wilt aanroepen, geeft u de naam op van de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Als uw clienttoepassing zich op dezelfde J2EE-toepassingsserver bevindt, kunt u `localhost` opgeven. Afhankelijk van welke J2EE-toepassingsserver AEM Forms wordt geïmplementeerd, geeft u een van de volgende waarden op:

   * JBoss: `https://<ServerName>:8080 (default port)`
   * WebSphere: `iiop://<ServerName>:2809 (default port)`
   * WebLogic: `t3://<ServerName>:7001 (default port)`

* **DSC_DEFAULT_SOAP_ENDPOINT**: Als u de SOAP verbindingswijze gebruikt, vertegenwoordigt deze waarde het eindpunt waarnaar een aanroepingsverzoek wordt verzonden. Als u AEM Forms op afstand wilt aanroepen, geeft u de naam op van de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Als uw clienttoepassing zich op dezelfde J2EE-toepassingsserver bevindt, kunt u `localhost` opgeven (bijvoorbeeld `http://localhost:8080` .)

   * De poortwaarde `8080` is van toepassing als de J2EE-toepassing JBoss is. Als de J2EE-toepassingsserver IBM® WebSphere® is, gebruikt u poort `9080` . En als de J2EE-toepassingsserver WebLogic is, gebruikt u poort `7001` . (Deze waarden zijn standaardpoortwaarden. Als u de havenwaarde verandert, gebruik het toepasselijke havenaantal.)

* **DSC_TRANSPORT_PROTOCOL**: Als u de EJB verbindingswijze gebruikt, specificeer `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL` voor deze waarde. Geef `ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL` op als u de SOAP-verbindingsmodus gebruikt.
* **DSC_SERVER_TYPE**: Specificeert de J2EE toepassingsserver waarop AEM Forms wordt opgesteld. Geldige waarden zijn `JBoss` , `WebSphere` , `WebLogic` .

   * Wanneer u deze eigenschap connection instelt op `WebSphere` , wordt de waarde `java.naming.factory.initial` ingesteld op `com.ibm.ws.naming.util.WsnInitCtxFactory` .
   * Wanneer u deze eigenschap connection instelt op `WebLogic` , wordt de waarde `java.naming.factory.initial` ingesteld op `weblogic.jndi.WLInitialContextFactory` .
   * Als u deze eigenschap voor verbinding instelt op `JBoss` , wordt de waarde `java.naming.factory.initial` ingesteld op `org.jnp.interfaces.NamingContextFactory` .
   * U kunt de eigenschap `java.naming.factory.initial` instellen op een waarde die aan uw vereisten voldoet als u de standaardwaarden niet wilt gebruiken.

  >[!NOTE]
  >
  >In plaats van een tekenreeks te gebruiken om de eigenschap `DSC_SERVER_TYPE` connection in te stellen, kunt u een statisch lid van de klasse `ServiceClientFactoryProperties` gebruiken. De volgende waarden kunnen worden gebruikt: `ServiceClientFactoryProperties.DSC_WEBSPHERE_SERVER_TYPE`, `ServiceClientFactoryProperties.DSC_WEBLOGIC_SERVER_TYPE` of `ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE` .

* **DSC_CREDENTIAL_USERNAME:** specificeert de AEM de gebruikersnaam van de vormengebruiker. Voor een gebruiker om de dienst van AEM Forms met succes aan te halen, hebben zij de rol van de Gebruiker van de Diensten nodig. Een gebruiker kan een andere rol ook hebben die de Dienst omvat roept toestemming. Anders, wordt een uitzondering geworpen wanneer zij proberen om de dienst aan te halen. Als de de dienstveiligheid gehandicapt is, is het niet noodzakelijk om dit verbindingsbezit te specificeren.
* **DSC_CREDENTIAL_PASSWORD:** specificeert de overeenkomstige wachtwoordwaarde. Als de de dienstveiligheid gehandicapt is, is het niet noodzakelijk om dit verbindingsbezit te specificeren.
* **DSC_REQUEST_TIMEOUT:** de grens van de standaardverzoekonderbreking voor het SOAP verzoek is 120000 milliseconden (20 minuten). Soms kan een aanvraag langer duren om de bewerking te voltooien. Een SOAP aanvraag die een grote set records ophaalt, kan bijvoorbeeld een langere time-outlimiet vereisen. U kunt `ServiceClientFactoryProperties.DSC_REQUEST_TIMEOUT` gebruiken om de de onderbrekingsgrens van de verzoekvraag voor de SOAP verzoeken te verhogen.

  **nota**: Slechts steunen de op SOAP-gebaseerde aanroepen het bezit DSC_REQUEST_TIMEOUT.

Voer de volgende taken uit om verbindingseigenschappen in te stellen:

1. Maak een `java.util.Properties` -object met behulp van de constructor.
1. Als u de eigenschap `DSC_DEFAULT_EJB_ENDPOINT` connection wilt instellen, roept u de methode `java.util.Properties` object `setProperty` aan en geeft u de volgende waarden door:

   * De opsommingswaarde `ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT`
   * Een tekenreekswaarde die de URL van de J2EE-toepassingsserver opgeeft die als host fungeert voor AEM Forms

   >[!NOTE]
   >
   >Als u de SOAP verbindingsmodus gebruikt, geeft u de opsommingswaarde `ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT` op in plaats van de opsommingswaarde `ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT` .

1. Als u de eigenschap `DSC_TRANSPORT_PROTOCOL` connection wilt instellen, roept u de methode `java.util.Properties` object `setProperty` aan en geeft u de volgende waarden door:

   * De opsommingswaarde `ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL`
   * De opsommingswaarde `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL`

   >[!NOTE]
   >
   >Als u de SOAP verbindingswijze gebruikt, specificeer de `ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL` opsommingswaarde in plaats van de `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL` opsommingswaarde.

1. Als u de eigenschap `DSC_SERVER_TYPE` connection wilt instellen, roept u de methode `java.util.Properties` object `setProperty` aan en geeft u de volgende waarden door:

   * De `ServiceClientFactoryProperties.DSC_SERVER_TYPE` opsommingswaarde
   * Een tekenreekswaarde die de J2EE-toepassingsserver opgeeft die als host fungeert voor AEM Forms (geef bijvoorbeeld `JBoss` op als AEM Forms op JBoss wordt geïmplementeerd).

      1. Als u de eigenschap `DSC_CREDENTIAL_USERNAME` connection wilt instellen, roept u de methode `java.util.Properties` object `setProperty` aan en geeft u de volgende waarden door:

   * De opsommingswaarde `ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME`
   * Een tekenreekswaarde die de gebruikersnaam opgeeft die vereist is om AEM Forms aan te roepen

      1. Als u de eigenschap `DSC_CREDENTIAL_PASSWORD` connection wilt instellen, roept u de methode `java.util.Properties` object `setProperty` aan en geeft u de volgende waarden door:

   * De opsommingswaarde `ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD`
   * Een tekenreekswaarde die de bijbehorende wachtwoordwaarde opgeeft

**plaatsend de EJB verbindingswijze voor JBoss**

In het volgende Java-codevoorbeeld worden eigenschappen voor verbindingen ingesteld om AEM Forms aan te roepen dat wordt geïmplementeerd op JBoss en met de EJB-verbindingsmodus.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "https://<hostname>:8080");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DOCUMENT_HTTP_ENDPOINT,"https://<hostname>:8080");
```

**plaatsend de EJB verbindingswijze voor WebLogic**

In het volgende Java-codevoorbeeld worden eigenschappen voor verbindingen ingesteld om AEM Forms aan te roepen dat wordt geïmplementeerd op WebLogic en met de EJB-verbindingsmodus.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "t3://localhost:7001");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "WebLogic");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

**plaatsend de EJB verbindingswijze voor WebSphere**

In het volgende Java-codevoorbeeld worden eigenschappen van een verbinding ingesteld om AEM Forms aan te roepen dat wordt geïmplementeerd op WebSphere en met de EJB-verbindingsmodus.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "iiop://localhost:2809");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "WebSphere");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

**plaatsend de SOAP verbindingswijze**

In het volgende Java-codevoorbeeld worden eigenschappen van een verbinding in SOAP modus ingesteld om AEM Forms aan te roepen dat wordt geïmplementeerd op JBoss.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "http://localhost:8080");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

>[!NOTE]
>
>Als u de SOAP verbindingsmodus selecteert, moet u ervoor zorgen dat er extra JAR-bestanden worden opgenomen in het klassepad van de clienttoepassing.

**plaatsende verbindingseigenschappen wanneer de dienstveiligheid gehandicapt is**

In het volgende Java-codevoorbeeld worden verbindingseigenschappen ingesteld die vereist zijn om AEM Forms aan te roepen dat wordt geïmplementeerd op JBoss Application Server en wanneer de servicebeveiliging is uitgeschakeld.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "jnp://localhost:1099");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
```

>[!NOTE]
>
>Alle Java-snelstarthandleidingen die zijn gekoppeld aan Programmeren met AEM Forms, tonen zowel de EJB-instellingen als SOAP verbindingsinstellingen.

**plaatsend de SOAP verbindingswijze met de grens van de douaneverzoekonderbreking**

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "http://localhost:8080");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_REQUEST_TIMEOUT, "1800000"); // Request timeout limit 30 Minutes
```

**Gebruikend een voorwerp van de Context om AEM Forms** aan te halen

U kunt een `com.adobe.idp.Context` -object gebruiken om een AEM Forms-service met een geverifieerde gebruiker aan te roepen (het `com.adobe.idp.Context` -object vertegenwoordigt een geverifieerde gebruiker). Wanneer u een `com.adobe.idp.Context` -object gebruikt, hoeft u de eigenschappen `DSC_CREDENTIAL_USERNAME` of `DSC_CREDENTIAL_PASSWORD` niet in te stellen. U kunt een `com.adobe.idp.Context` -object verkrijgen wanneer u gebruikers ontwerpt met de methode `AuthenticationManagerServiceClient` object `authenticate` .

De methode `authenticate` retourneert een `AuthResult` -object dat de resultaten van de verificatie bevat. U kunt een `com.adobe.idp.Context` -object maken door de constructor ervan aan te roepen. Roep vervolgens de methode `initPrincipal` van het object `com.adobe.idp.Context` aan en geef het object `AuthResult` door, zoals in de volgende code wordt getoond:

```java
 Context myCtx = new Context();
 myCtx.initPrincipal(authResult);
```

In plaats van de eigenschappen `DSC_CREDENTIAL_USERNAME` of `DSC_CREDENTIAL_PASSWORD` in te stellen, kunt u de methode `ServiceClientFactory` van het object `setContext` aanroepen en het object `com.adobe.idp.Context` doorgeven. Wanneer u een gebruiker van een AEM gebruikt om een service aan te roepen, moet u ervoor zorgen dat deze de rol `Services User` heeft die nodig is om een AEM Forms-service aan te roepen.

In het volgende codevoorbeeld wordt getoond hoe u een `com.adobe.idp.Context` -object gebruikt binnen verbindingsinstellingen die worden gebruikt om een `EncryptionServiceClient` -object te maken.

```java
 //Authenticate a user and use the Context object within connection settings
 // Authenticate the user
 String username = "wblue";
 String password = "password";
 AuthResult authResult = authClient.authenticate(username, password.getBytes());
 
 //Set a Content object that represents the authenticated user
 //Use the Context object to invoke the Encryption service
 Context myCtx = new Context();
 myCtx.initPrincipal(authResult);
 
 //Set connection settings
 Properties connectionProps = new Properties();
 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "jnp://<server>:1099");
 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL, ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE);
 connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DOCUMENT_HTTP_ENDPOINT,"jnp://<server>:1099");

 
 //Create a ServiceClientFactory object
 ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 myFactory.setContext(myCtx);
 
 //Create an EncryptionServiceClient object
 EncryptionServiceClient encryptClient  = new EncryptionServiceClient(myFactory);
```

>[!NOTE]
>
>Voor volledige details over het voor authentiek verklaren van een gebruiker, zie [&#x200B; Voor authentiek verklaren Gebruikers &#x200B;](/help/forms/developing/users.md#authenticating-users).

### Oproepen van scenario&#39;s {#invoking_scenarios-1}

De volgende aanroepende scenario&#39;s worden besproken in deze sectie:

* Een clienttoepassing die in een eigen Java Virtual Machine (JVM) wordt uitgevoerd, roept een zelfstandige AEM Forms-instantie aan.
* Een clienttoepassing die in een eigen JVM wordt uitgevoerd, roept geclusterde AEM Forms-instanties aan.

### Clienttoepassing die een zelfstandige AEM Forms-instantie aanroept {#client-application-invoking-a-stand-alone-aem-forms-instance}

In het volgende diagram ziet u een clienttoepassing die in een eigen JVM wordt uitgevoerd en een zelfstandige AEM Forms-instantie aanroept.

In dit scenario wordt een clienttoepassing uitgevoerd in een eigen JVM en worden AEM Forms-services aangeroepen.

>[!NOTE]
>
>Dit scenario is het het aanhalen scenario waarop alle Snelle Begint gebaseerd is.

### Clienttoepassing die geclusterde AEM Forms-instanties aanroept {#client-application-invoking-clustered-aem-forms-instances}

In het volgende diagram wordt een clienttoepassing weergegeven die in een eigen JVM wordt uitgevoerd en die AEM Forms-instanties in een cluster oproept.

Dit scenario is vergelijkbaar met een clienttoepassing die een zelfstandige AEM Forms-instantie aanroept. De URL van de provider is echter anders. Als een clienttoepassing verbinding wil maken met een specifieke J2EE-toepassingsserver, moet de toepassing de URL wijzigen om naar de specifieke J2EE-toepassingsserver te verwijzen.

Verwijzen naar een specifieke J2EE-toepassingsserver wordt niet aanbevolen omdat de verbinding tussen de clienttoepassing en AEM Forms wordt verbroken als de toepassingsserver wordt gestopt. Het wordt aanbevolen dat de provider-URL verwijst naar een JNDI-manager op celniveau in plaats van een specifieke J2EE-toepassingsserver.

Clienttoepassingen die de SOAP verbindingsmodus gebruiken, kunnen de HTTP-taakverdelingpoort voor de cluster gebruiken. Clienttoepassingen die gebruikmaken van de EJB-verbindingsmodus kunnen verbinding maken met de EJB-poort van een specifieke J2EE-toepassingsserver. Met deze handeling wordt de taakverdeling tussen clusterknooppunten afgehandeld.

**WebSphere**

In het volgende voorbeeld wordt de inhoud getoond van een bestand jndi.properties dat wordt gebruikt om verbinding te maken met AEM Forms dat op WebSphere is geïmplementeerd.

```ini
 java.naming.factory.initial=com.ibm.websphere.naming.
 WsnInitialContextFactory
 java.naming.provider.url=corbaloc::appserver1:9810,:appserver2:9810
```

**Weblogica**

Het volgende voorbeeld toont de inhoud van het bestand jndi.properties dat wordt gebruikt om verbinding te maken met AEM Forms dat is gedistribueerd via WebLogic.

```ini
 java.naming.factory.initial=weblogic.jndi.WLInitialContextFactory
 java.naming.provider.url=t3://appserver1:8001, appserver2:8001
```

**JBoss**

In het volgende voorbeeld wordt de inhoud getoond van een bestand jndi.properties dat wordt gebruikt om verbinding te maken met AEM Forms dat op JBoss wordt geïmplementeerd.

```ini
 java.naming.factory.initial= org.jnp.interfaces.NamingContextFactory
 java.naming.provider.url= jnp://appserver1:1099, appserver2:1099,
 appserver3:1099
```

>[!NOTE]
>
>Raadpleeg uw beheerder om de naam en het poortnummer van de J2EE-toepassingsserver te bepalen.

**Zie ook**

[Inclusief Java-bibliotheekbestanden van AEM Forms](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Gegevens doorgeven aan AEM Forms-services met gebruik van de Java-API](invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api)

[Een service aanroepen met behulp van een Java-clientbibliotheek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Gegevens doorgeven aan AEM Forms-services met gebruik van de Java-API {#passing-data-to-aem-forms-services-using-the-java-api}

Bij AEM Forms-servicetaken worden doorgaans PDF-documenten gebruikt of geproduceerd. Wanneer u de dienst aanhaalt, soms is het noodzakelijk om een document van de PDF (of andere documenttypes zoals de gegevens van XML) tot de dienst over te gaan. Soms is het ook nodig om een PDF-document te verwerken dat van de service is geretourneerd. De Java-klasse waarmee u gegevens kunt doorgeven van en naar AEM Forms-services is `com.adobe.idp.Document` .

AEM Forms-services accepteren een PDF-document niet als andere gegevenstypen, zoals een `java.io.InputStream` -object of een bytearray. Een `com.adobe.idp.Document` -object kan ook worden gebruikt om andere gegevenstypen, zoals XML-gegevens, aan services door te geven.

Een `com.adobe.idp.Document` -object is een Java-type met serienummering, zodat het kan worden doorgegeven via een RMI-aanroep. De ontvangende zijde kan (zelfde gastheer, zelfde klassenlader), lokaal (zelfde gastheer, verschillende klassenlader), of ver (verschillende gastheer) worden collocated. Het doorgeven van documentinhoud is voor elk geval geoptimaliseerd. Als de afzender en de ontvanger zich bijvoorbeeld op dezelfde host bevinden, wordt de inhoud doorgegeven via een lokaal bestandssysteem. (In sommige gevallen kunnen documenten in het geheugen worden doorgegeven.)

Afhankelijk van de objectgrootte van `com.adobe.idp.Document` worden de gegevens binnen het `com.adobe.idp.Document` -object vervoerd of op het bestandssysteem van de server opgeslagen. Eventuele tijdelijke opslagbronnen die door het object `com.adobe.idp.Document` worden gebruikt, worden automatisch verwijderd wanneer `com.adobe.idp.Document` wordt verwijderd. (Zie [&#x200B; het Verwerpen de voorwerpen van het Document &#x200B;](invoking-aem-forms-using-java.md#disposing-document-objects).)

Soms is het nodig het inhoudstype van een `com.adobe.idp.Document` -object te kennen voordat u het aan een service kunt doorgeven. Als een bewerking bijvoorbeeld een specifiek inhoudstype vereist, zoals `application/pdf` , wordt u aangeraden het inhoudstype te bepalen. (Zie [&#x200B; Bepalend het inhoudstype van een document &#x200B;](invoking-aem-forms-using-java.md#determining-the-content-type-of-a-document).)

Het `com.adobe.idp.Document` -object probeert het inhoudstype te bepalen aan de hand van de verschafte gegevens. Als het inhoudstype niet kan worden opgehaald uit de opgegeven gegevens (bijvoorbeeld wanneer de gegevens zijn opgegeven als een bytearray), stelt u het inhoudstype in. Als u het inhoudstype wilt instellen, roept u de methode `setContentType` van het object `com.adobe.idp.Document` aan. (Zie [&#x200B; Bepalend het inhoudstype van een document &#x200B;](invoking-aem-forms-using-java.md#determining-the-content-type-of-a-document))

Als secundaire bestanden zich op hetzelfde bestandssysteem bevinden, kunt u sneller een `com.adobe.idp.Document` -object maken. Als secundaire bestanden zich op externe bestandssystemen bevinden, moet er een kopieerbewerking worden uitgevoerd die de prestaties beïnvloedt.

Een toepassing kan zowel `com.adobe.idp.Document` als `org.w3c.dom.Document` gegevenstypen bevatten. Zorg er echter voor dat u het gegevenstype `org.w3c.dom.Document` volledig kwalificeert. Voor informatie over het omzetten van een `org.w3c.dom.Document` voorwerp in een `com.adobe.idp.Document` voorwerp, zie [&#x200B; Snel Begin (wijze EJB): Prepopulating Forms met Stroombare Lay-outs die Java API gebruiken &#x200B;](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-prepopulating-forms-with-flowable-layouts-using-the-java-api).

>[!NOTE]
>
>Als u een geheugenlek in WebLogic wilt voorkomen terwijl u een `com.adobe.idp.Document` -object gebruikt, leest u de documentinformatie in delen van 2048 bytes of minder. De volgende code leest bijvoorbeeld de documentinformatie in delen van 2048 bytes:

```java
        // Set up the chunk size to prevent a potential memory leak
        int buffSize = 2048;
 
        // Determine the total number of bytes to read
        int docLength = (int) inDoc.length();
        byte [] byteDoc = new byte[docLength];
 
        // Set up the reading position
        int pos = 0;
 
        // Loop through the document information, 2048 bytes at a time
        while (docLength > 0) {
      // Read the next chunk of information
            int toRead = Math.min(buffSize, docLength);
            int bytesRead = inDoc.read(pos, byteDoc, pos, toRead);
 
            // Handle the exception in case data retrieval failed
            if (bytesRead == -1) {
 
                inDoc.doneReading();
                inDoc.dispose();
                throw new RuntimeException("Data retrieval failed!");
 
            }
 
             // Update the reading position and number of bytes remaining
             pos += bytesRead;
             docLength -= bytesRead;
 
        }
 
        // The document information has been successfully read
        inDoc.doneReading();
        inDoc.dispose();
```

**zie ook**

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Documenten maken {#creating-documents}

Maak een `com.adobe.idp.Document` -object voordat u een servicebewerking aanroept waarvoor een PDF-document (of andere documenttypen) als invoerwaarde is vereist. De klasse `com.adobe.idp.Document` biedt constructors waarmee u een document kunt maken van de volgende inhoudstypen:

* Een bytearray
* Een bestaand `com.adobe.idp.Document` -object
* Een object `java.io.File`
* Een object `java.io.InputStream`
* Een object `java.net.URL`

#### Een document maken op basis van een bytearray {#creating-a-document-based-on-a-byte-array}

In het volgende codevoorbeeld wordt een `com.adobe.idp.Document` -object gemaakt dat is gebaseerd op een bytearray.

**Creërend een voorwerp van het Document dat op een byteserie** gebaseerd is

```java
 Document myPDFDocument = new Document(myByteArray);
```

#### Een document maken op basis van een ander document {#creating-a-document-based-on-another-document}

In het volgende codevoorbeeld wordt een `com.adobe.idp.Document` -object gemaakt dat is gebaseerd op een ander `com.adobe.idp.Document` -object.

**Creërend een voorwerp van het Document dat op een ander document** gebaseerd is

```java
 //Create a Document object based on a byte array
 InputStream is = new FileInputStream("C:\\Map.pdf");
 int len = is.available();
 byte [] myByteArray = new byte[len];
 int i = 0;
 while (i < len) {
       i += is.read(myByteArray, i, len);
 }
 Document myPDFDocument = new Document(myByteArray);
 
 //Create another Document object
 Document anotherDocument = new Document(myPDFDocument);
```

#### Een document maken op basis van een bestand {#creating-a-document-based-on-a-file}

Het volgende codevoorbeeld leidt tot een `com.adobe.idp.Document` voorwerp dat op een PDF dossier genoemd *map.pdf* gebaseerd is. Dit bestand bevindt zich in de hoofdmap van de C-vaste schijf. Deze constructor probeert het MIME-inhoudstype van het `com.adobe.idp.Document` -object in te stellen met de bestandsnaamextensie.

De constructor `com.adobe.idp.Document` die een `java.io.File` -object accepteert, accepteert ook een Booleaanse parameter. Door deze parameter in te stellen op `true` , verwijdert het `com.adobe.idp.Document` -object het bestand. Deze handeling houdt in dat u het bestand niet hoeft te verwijderen nadat u het hebt doorgegeven aan de constructor `com.adobe.idp.Document` .

Als u deze parameter instelt op `false` , blijft de eigendom van dit bestand behouden. Het instellen van deze parameter op `true` is efficiënter. De reden hiervoor is dat het `com.adobe.idp.Document` -object het bestand rechtstreeks naar het lokale beheerde gebied kan verplaatsen in plaats van het te kopiëren (wat langzamer is).

**Creërend een voorwerp van het Document dat op een dossier van PDF** gebaseerd is

```java
 //Create a Document object based on the map.pdf source file
 File mySourceMap = new File("C:\\map.pdf");
 Document myPDFDocument = new Document(mySourceMap,true);
```

#### Een document maken op basis van een InputStream-object {#creating-a-document-based-on-an-inputstream-object}

In het volgende Java-codevoorbeeld wordt een object `com.adobe.idp.Document` gemaakt dat is gebaseerd op een object `java.io.InputStream` .

**Creërend een document dat op een voorwerp InputStream** wordt gebaseerd

```java
 //Create a Document object based on an InputStream object
 InputStream is = new FileInputStream("C:\\Map.pdf");
 Document myPDFDocument = new Document(is);
```

#### Een document maken op basis van inhoud die toegankelijk is via een URL {#creating-a-document-based-on-content-accessible-from-an-url}

Het volgende de codevoorbeeld van Java leidt tot een `com.adobe.idp.Document` voorwerp dat op een PDF dossier genoemd *map.pdf* gebaseerd is. Dit bestand bevindt zich in een webtoepassing met de naam `WebApp` die wordt uitgevoerd op `localhost` . Deze constructor probeert het MIME-inhoudstype van het `com.adobe.idp.Document` -object in te stellen met het inhoudstype dat met het URL-protocol wordt geretourneerd.

De URL die aan het object `com.adobe.idp.Document` wordt geleverd, wordt altijd gelezen aan de zijde waar het oorspronkelijke object `com.adobe.idp.Document` is gemaakt, zoals in dit voorbeeld wordt getoond:

```java
     Document doc = new Document(new java.net.URL("file:c:/temp/input.pdf"));
```

Het c:/temp/input.pdf-bestand moet zich op de clientcomputer bevinden (niet op de servercomputer). Het is de clientcomputer waar de URL wordt gelezen en waar het `com.adobe.idp.Document` object is gemaakt.

**Creërend een document dat op inhoud toegankelijk van een URL** wordt gebaseerd

```java
 //Create a Document object based on a java.net.URL object
 URL myURL = new URL("http", "localhost", 8080,"/WebApp/map.pdf");
 
 //Create another Document object
 Document myPDFDocument = new Document(myURL);
```

**zie ook**

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Geretourneerde documenten afhandelen {#handling-returned-documents}

Servicebewerkingen die een PDF-document (of andere gegevenstypen zoals XML-gegevens) als uitvoerwaarde retourneren, retourneren een `com.adobe.idp.Document` object. Nadat u een `com.adobe.idp.Document` object hebt ontvangen, kunt u het converteren naar de volgende indelingen:

* Een `java.io.File` object
* Een `java.io.InputStream` object
* Een bytearray

De volgende coderegel zet een `com.adobe.idp.Document` -object om in een `java.io.InputStream` -object. Stel dat `myPDFDocument` een `com.adobe.idp.Document` -object vertegenwoordigt:

```java
     java.io.InputStream resultStream = myDocument.getInputStream();
```

Op dezelfde manier kunt u de inhoud van een `com.adobe.idp.Document` naar een lokaal bestand kopiëren door de volgende taken uit te voeren:

1. Maak een `java.io.File` -object.
1. Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan en geef het object `java.io.File` door.

Het volgende codevoorbeeld kopieert de inhoud van a `com.adobe.idp.Document` voorwerp aan een dossier genoemd *anotherMap.pdf*.

**Kopieert de inhoud van een documentvoorwerp aan een dossier**

```java
 File outFile = new File("C:\\AnotherMap.pdf");
 myDocument.copyToFile (outFile);
```

**zie ook**

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Het inhoudstype van een document bepalen {#determining-the-content-type-of-a-document}

Bepaal het MIME-type van een `com.adobe.idp.Document` -object door de methode `com.adobe.idp.Document` object `getContentType` aan te roepen. Deze methode retourneert een tekenreekswaarde die het inhoudstype van het `com.adobe.idp.Document` -object opgeeft. In de volgende tabel worden de verschillende inhoudstypen beschreven die AEM Forms retourneert.

<table>
 <thead>
  <tr>
   <th><p>MIME-type</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p><code>application/pdf</code></p></td>
   <td><p>PDF-document</p></td>
  </tr>
  <tr>
   <td><p><code>application/vnd.adobe.xdp+xml</code></p></td>
   <td><p>XML Data Packaging (XDP), dat wordt gebruikt voor geëxporteerde XFA-formulieren (XML Forms Architecture)</p></td>
  </tr>
  <tr>
   <td><p><code>text/xml</code></p></td>
   <td><p>Bladwijzers, bijlagen of andere XML-documenten</p></td>
  </tr>
  <tr>
   <td><p><code>application/vnd.fdf</code></p></td>
   <td><p>Forms Data Format (FDF), die wordt gebruikt voor geëxporteerde Acrobat-formulieren</p></td>
  </tr>
  <tr>
   <td><p><code>application/vnd.adobe.xfdf</code></p></td>
   <td><p>XML Forms Data Format (XFDF), die wordt gebruikt voor geëxporteerde Acrobat-formulieren</p></td>
  </tr>
  <tr>
   <td><p><code>application/rdf+xml</code></p></td>
   <td><p>Rijke gegevensindeling en XML</p></td>
  </tr>
  <tr>
   <td><p><code>application/octet-stream</code></p></td>
   <td><p>Algemene gegevensindeling</p></td>
  </tr>
  <tr>
   <td><p><code>NULL</code></p></td>
   <td><p>Niet-opgegeven MIME-type</p></td>
  </tr>
 </tbody>
</table>

Het volgende codevoorbeeld bepaalt het inhoudstype van een `com.adobe.idp.Document` voorwerp.

**Bepalend het inhoudstype van een voorwerp van het Document**

```java
 //Determine the content type of the Document object
 String ct = myDocument.getContentType();
 System.out.println("The content type of the Document object is " +ct);
```

**zie ook**

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Documentobjecten verwijderen {#disposing-document-objects}

Wanneer u een `Document` -object niet meer nodig hebt, wordt u aangeraden het te verwijderen door de `dispose` -methode aan te roepen. Elk `Document` -object gebruikt een bestandsdescriptor en maar liefst 75 MB aan RAM-ruimte op het hostplatform van uw toepassing. Als een `Document` -object niet wordt verwijderd, verwijdert het Java Garage-verzamelingsproces het object. Als u deze methode echter eerder verwijdert met de methode `dispose` , kunt u het geheugen dat door het object `Document` wordt gebruikt, vrijmaken.

**zie ook**

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Een service aanroepen met een Java-clientbibliotheek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Een service aanroepen met een Java-clientbibliotheek {#invoking-a-service-using-a-java-client-library}

De de dienstverrichtingen van AEM Forms kunnen worden aangehaald door sterk getypte API van de dienst te gebruiken, die als een cliëntbibliotheek van Java wordt bekend. A *de cliëntbibliotheek van Java* is een reeks concrete klassen die toegang tot de diensten verlenen die in de de dienstcontainer worden opgesteld. U instantieert een Java-object dat de service vertegenwoordigt die moet worden aangeroepen in plaats van een `InvocationRequest` -object te maken met de Invocation API. De oproepings-API wordt gebruikt om processen, zoals langlevende processen, aan te roepen die in Workbench zijn gemaakt. (Zie [&#x200B; het aanhalen van mens-Centric langlevende Processen &#x200B;](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

Als u een servicebewerking wilt uitvoeren, roept u een methode aan die tot het Java-object behoort. Een Java-clientbibliotheek bevat methoden die doorgaans een-op-een toewijzen aan servicebewerkingen. Wanneer u een Java-clientbibliotheek gebruikt, stelt u de vereiste verbindingseigenschappen in. (Zie [&#x200B; Plaatsende verbindingseigenschappen &#x200B;](invoking-aem-forms-using-java.md#setting-connection-properties).)

Nadat u verbindingseigenschappen hebt ingesteld, maakt u een `ServiceClientFactory` -object dat wordt gebruikt om een Java-object te instantiëren waarmee u een service kunt aanroepen. Elke service met een Java-clientbibliotheek heeft een overeenkomstig clientobject. Als u bijvoorbeeld de Repository-service wilt aanroepen, maakt u een `ResourceRepositoryClient` -object met de constructor ervan en geeft u het `ServiceClientFactory` -object door. Het `ServiceClientFactory` object is verantwoordelijk voor het behoud van de verbindingsinstellingen die vereist zijn voor het aanroepen van AEM Forms-services.

Hoewel het verkrijgen van een `ServiceClientFactory` doorgaans snel is, is er enige overhead van belang wanneer de factory voor het eerst wordt gebruikt. Dit object is geoptimaliseerd voor hergebruik en gebruik daarom, indien mogelijk, hetzelfde `ServiceClientFactory` -object wanneer u meerdere Java-client-objecten maakt. Maak dus geen afzonderlijk `ServiceClientFactory` -object voor elk clientbibliotheekobject dat u maakt.

Er is een instelling voor Gebruikersbeheer die de levensduur van de SAML-bewering bepaalt die zich binnen het `com.adobe.idp.Context` -object bevindt dat het `ServiceClientFactory` -object beïnvloedt. Deze instelling bepaalt de levensduur van alle verificatiecontext in AEM Forms, inclusief alle aanroepen die worden uitgevoerd met de Java API. Standaard kan een `ServiceCleintFactory` -object twee uur worden gebruikt.

>[!NOTE]
>
>Als u wilt uitleggen hoe u een service aanroept met de Java API, wordt de bewerking `writeResource` van de Repository-service aangeroepen. Met deze bewerking plaatst u een nieuwe bron in de opslagplaats.

U kunt de service Opslagplaats aanroepen door gebruik te maken van een Java-clientbibliotheek en de volgende stappen uit te voeren:

1. Neem jar-bestanden van de client op, zoals de adobe-repository-client.jar, in het klassenpad van uw Java-project. Voor informatie over de plaats van deze dossiers, zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Stel verbindingseigenschappen in die vereist zijn om een service aan te roepen.
1. Maak een `ServiceClientFactory` -object door de statische methode van het `ServiceClientFactory` object `createInstance` aan te roepen en het `java.util.Properties` -object dat verbindingseigenschappen bevat, door te geven.
1. Maak een `ResourceRepositoryClient` object door de constructor te gebruiken en het object door te `ServiceClientFactory` geven. Gebruik het `ResourceRepositoryClient` object om bewerkingen van de opslagplaatsservice te activeren.
1. Maak een object met behulp van de constructor en geef `null`een `RepositoryInfomodelFactoryBean` Met dit object kunt u een `Resource` object maken dat de inhoud vertegenwoordigt die aan de opslagplaats wordt toegevoegd.
1. Maak een `Resource` object door de methode van `newImage` het `RepositoryInfomodelFactoryBean` object aan te roepen en de volgende waarden door te geven:

   * Een unieke ID-waarde door `new Id()`.
   * Een unieke UUID-waarde door `new Lid()` op te geven.
   * De naam van de bron. U kunt de bestandsnaam van het XDP-bestand opgeven.

   De geretourneerde waarde wordt gecast naar `Resource` .

1. Maak een `ResourceContent` -object door de methode `RepositoryInfomodelFactoryBean` object `newImage` aan te roepen en de geretourneerde waarde naar `ResourceContent` te casten. Dit object vertegenwoordigt de inhoud die aan de gegevensopslagruimte wordt toegevoegd.
1. Maak een `com.adobe.idp.Document` -object door een `java.io.FileInputStream` -object door te geven dat het XDP-bestand opslaat dat aan de gegevensopslagruimte moet worden toegevoegd. (Zie [&#x200B; Creërend een document dat op een voorwerp InputStream &#x200B;](invoking-aem-forms-using-java.md#creating-a-document-based-on-an-inputstream-object) wordt gebaseerd.)
1. Voeg de inhoud van het `com.adobe.idp.Document` -object toe aan het `ResourceContent` -object door de methode `setDataDocument` van het `ResourceContent` -object aan te roepen. Geef het object `com.adobe.idp.Document` door.
1. Stel het MIME-type van het XDP-bestand in dat u aan de opslagplaats wilt toevoegen door de methode `setMimeType` van het object `ResourceContent` aan te roepen en door te geven `application/vnd.adobe.xdp+xml` .
1. Voeg de inhoud van het `ResourceContent` -object toe aan het `Resource` -object door de methode `setContent` van het `Resource` -object aan te roepen en het `ResourceContent` -object door te geven.
1. Voeg een beschrijving van de bron toe door de methode `setDescription` van het object `Resource` aan te roepen en een tekenreekswaarde door te geven die een beschrijving van de bron vertegenwoordigt.
1. Voeg het formulierontwerp toe aan de gegevensopslagruimte door de methode `writeResource` van het object `ResourceRepositoryClient` aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die het pad naar de bronverzameling opgeeft die de nieuwe bron bevat
   * Het gemaakte `Resource` -object

**zie ook**

[Snel starten (EJB-modus): een bron schrijven met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

## Een kortstondig proces aanroepen met de API voor aanroepen {#invoking-a-short-lived-process-using-the-invocation-api}

U kunt een kortstondig proces aanroepen met de Java Invocation-API. Wanneer u een kortstondig proces aanroept met behulp van de Inroeping-API, geeft u vereiste parameterwaarden door met behulp van een `java.util.HashMap` -object. Voor elke parameter om aan de dienst over te gaan, haalt de methode `put` van het voorwerp `java.util.HashMap` aan en specificeert het naam-waardepaar dat door de dienst wordt vereist om de gespecificeerde verrichting uit te voeren. Geef de exacte naam op van de parameters die bij het kortstondige proces horen.

>[!NOTE]
>
>Voor informatie over het aanhalen van een proces van lange duur, zie [&#x200B; het Aanhalen van mens-Centric langlevende Processen &#x200B;](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

Het volgende onderwerp gaat over het gebruik van de API Inroeping om het volgende kortstondige AEM Forms-proces met de naam `MyApplication/EncryptDocument` aan te roepen.

>[!NOTE]
>
>Dit proces is niet gebaseerd op een bestaand AEM Forms-proces. Als u het codevoorbeeld wilt volgen, maakt u een proces met de naam `MyApplication/EncryptDocument` met Workbench. (Zie [&#x200B; Gebruikend Workbench &#x200B;](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wanneer dit proces wordt aangeroepen, worden de volgende handelingen uitgevoerd:

1. Verkrijgt het onbeveiligde document van de PDF dat tot het proces wordt overgegaan. Deze handeling is gebaseerd op de bewerking `SetValue` . De invoerparameter voor dit proces is een `document` procesvariabele met de naam `inDoc` .
1. Hiermee versleutelt u het PDF-document met een wachtwoord. Deze handeling is gebaseerd op de bewerking `PasswordEncryptPDF` . Het met wachtwoord gecodeerde PDF-document wordt geretourneerd in een procesvariabele met de naam `outDoc` .

### Het kortstondige MyApplication/EncryptDocument-proces aanroepen met de Java-oproepings-API {#invoke-the-myapplication-encryptdocument-short-lived-process-using-the-java-invocation-api}

Roep het `MyApplication/EncryptDocument` kortstondige proces aan met behulp van de Java-oproepings-API:

1. Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project. (Zie [&#x200B; Inclusief de bibliotheekdossiers van AEM Forms Java &#x200B;](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).)
1. Maak een `ServiceClientFactory` -object dat verbindingseigenschappen bevat. (Zie [&#x200B; Plaatsende verbindingseigenschappen &#x200B;](invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Maak een `ServiceClient` -object door de constructor ervan te gebruiken en het `ServiceClientFactory` -object door te geven. Met een `ServiceClient` -object kunt u een servicebewerking aanroepen. Het behandelt taken zoals het lokaliseren van, het verzenden van, en het verpletteren van oproepingsverzoeken.
1. Maak een `java.util.HashMap` -object met behulp van de constructor.
1. Roep de methode `put` van het `java.util.HashMap` -object aan voor elke invoerparameter die wordt doorgegeven aan het langlevende proces. Omdat voor het `MyApplication/EncryptDocument` kortstondige proces één invoerparameter van het type `Document` vereist is, hoeft u de methode `put` slechts eenmaal aan te roepen, zoals in het volgende voorbeeld wordt getoond.

   ```java
    //Create a Map object to store the parameter value for inDoc
    Map params = new HashMap();
    InputStream inFile = new FileInputStream("C:\\Adobe\Loan.pdf");
    Document inDoc = new Document(inFile);
    params.put("inDoc", inDoc);
   ```

1. Maak een `InvocationRequest` -object door de methode `ServiceClientFactory` object `createInvocationRequest` aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam aangeeft van het proces met een lange levensduur dat moet worden aangeroepen. Geef `MyApplication/EncryptDocument` op om het `MyApplication/EncryptDocument` -proces op te roepen.
   * Een tekenreekswaarde die staat voor de naam van de procesbewerking. De naam van een kortstondige procesbewerking is doorgaans `invoke` .
   * Het `java.util.HashMap` -object dat de parameterwaarden bevat die de servicebewerking vereist.
   * Een Booleaanse waarde die `true` opgeeft en die een synchrone aanvraag maakt (deze waarde is van toepassing om een kortstondig proces aan te roepen).

1. Verzend de aanroepingsaanvraag naar de service door de methode `invoke` van het object `ServiceClient` aan te roepen en het object `InvocationRequest` door te geven. De methode `invoke` retourneert een `InvocationReponse` -object.

   >[!NOTE]
   >
   >Een proces van lange duur kan worden aangehaald door de waarde `false` als vierde parameter van de `createInvocationRequest` methode over te gaan. Het overgaan van de waarde `false`*leidt tot een asynchroon verzoek.*

1. Haal de geretourneerde waarde van het proces op door de methode `getOutputParameter` van het object `InvocationReponse` aan te roepen en een tekenreekswaarde door te geven die de naam van de uitvoerparameter opgeeft. In dit geval geeft u `outDoc` op ( `outDoc` is de naam van de uitvoerparameter voor het `MyApplication/EncryptDocument` -proces). Cast de geretourneerde waarde naar `Document`, zoals in het volgende voorbeeld wordt getoond.

   ```java
    InvocationResponse response = myServiceClient.invoke(request);
    Document encryptDoc = (Document) response.getOutputParameter("outDoc");
   ```

1. Maak een `java.io.File` -object en controleer of de bestandsextensie .pdf is.
1. Roep de methode `copyToFile` van het object `com.adobe.idp.Document` aan om de inhoud van het object `com.adobe.idp.Document` naar het bestand te kopiëren. Gebruik het object `com.adobe.idp.Document` dat door de methode `getOutputParameter` is geretourneerd.

**zie ook**

[Snel starten: Een kortstondig proces aanroepen met de API voor aanroepen](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-short-lived-process-using-the-invocation-api)

[Het aanhalen van mens-Centric langlevende Processen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[Inclusief AEM Forms Java-bibliotheekbestanden](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
