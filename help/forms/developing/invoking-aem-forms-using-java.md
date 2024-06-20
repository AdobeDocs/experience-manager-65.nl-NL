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
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '5333'
ht-degree: 0%

---

# AEM Forms aanroepen met de Java API {#invoking-aem-forms-using-the-javaapi}

**Voorbeelden en voorbeelden in dit document gelden alleen voor AEM Forms in JEE-omgeving.**

AEM Forms kan worden aangeroepen met de AEM Forms Java API. Wanneer u de AEM Forms Java API gebruikt, kunt u de Invocation API- of Java-clientbibliotheken gebruiken. Java-clientbibliotheken zijn beschikbaar voor services zoals de service Rights Management. Met deze sterk getypeerde API&#39;s kunt u Java-toepassingen ontwikkelen die AEM Forms aanroepen.

De oproepings-API bevindt zich in de volgende klassen `com.adobe.idp.dsc` pakket. Met deze klassen kunt u een aanroepingsverzoek rechtstreeks naar een service verzenden en een geretourneerde aanroepingsreactie afhandelen. Gebruik de oproepings-API om kortstondige of langlevende processen aan te roepen die met Workbench zijn gemaakt.

De geadviseerde manier om een dienst programmatically aan te halen is een de cliëntbibliotheek van Java te gebruiken die aan de dienst in tegenstelling tot de Inroeping API beantwoordt. Als u bijvoorbeeld de coderingsservice wilt aanroepen, gebruikt u de clientbibliotheek van de coderingsservice. Om een de dienstverrichting van de Encryptie uit te voeren, haal een methode aan die tot het de dienstcliëntvoorwerp van de Encryptie behoort. U kunt een PDF-document versleutelen met een wachtwoord door het `EncryptionServiceClient` object `encryptPDFUsingPassword` methode.

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
* De modus waarin u een AEM Forms-service wilt aanroepen. U kunt de modus EJB of SOAP gebruiken. (Zie [Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>(Alleen Turkije) Start de AEM Forms-server met de opdracht `standalone.bat -b <Server IP> -c lc_turnkey.xml` om serverIP voor EJB te specificeren

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
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-usermanager-client.jar</p></td>
   <td><p>Moet altijd worden opgenomen in het klassepad van een Java-clienttoepassing.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-utilities.jar</p></td>
   <td><p>Moet altijd worden opgenomen in het klassepad van een Java-clienttoepassing.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk//client-libs/&lt;app server=""&gt;</p></td>
  </tr>
  <tr>
   <td><p>adobe-applicationmanager-client-sdk.jar</p></td>
   <td><p>Vereist om de dienst van de Manager van de Toepassing aan te halen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-assembler-client.jar</p></td>
   <td><p>Vereist om de dienst van de Assembler aan te halen. </p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-backup-restore-client-sdk.jar</p></td>
   <td><p>Vereist om de service-API voor back-up en herstel aan te roepen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-barcodedforms-client.jar</p></td>
   <td><p>Vereist om de service voor formulieren met streepjescodes aan te roepen. </p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-convertpdf-client.jar</p></td>
   <td><p>Vereist om de dienst van de PDF van de Bekeerling aan te halen. </p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-distiller-client.jar</p></td>
   <td><p>Vereist om de Distiller-service aan te roepen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-docconverter-client.jar</p></td>
   <td><p>Vereist om de dienst DocConverter aan te halen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-contentservices-client.jar</p></td>
   <td><p>Vereist om de service Documentbeheer aan te roepen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-encryption-client.jar</p></td>
   <td><p>Vereist om de dienst van de Encryptie aan te halen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-forms-client.jar</p></td>
   <td><p>Vereist om de Forms-service aan te roepen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-formdataintegration-client.jar</p></td>
   <td><p>Vereist om de dienst van de Integratie van de Gegevens van de Vorm aan te halen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-generatepdf-client.jar</p></td>
   <td><p>Vereist om de Generate dienst van PDF aan te halen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-generate3dpdf-client.jar</p></td>
   <td><p>Vereist om de Generate 3D dienst van PDF aan te halen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-jobmanager-client-sdk.jar</p></td>
   <td><p>Vereist om de service Taakbeheer aan te roepen. </p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-output-client.jar</p></td>
   <td><p>Vereist om de dienst van de Output aan te halen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-pdfutility-client.jar</p></td>
   <td><p>Vereist om de dienst van de Hulpprogramma's van de PDF of XMP aan te halen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-reader-extensions-client.jar</p></td>
   <td><p>Vereist om de Acrobat Reader DC-extensieservice aan te roepen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-repository-client.jar</p><p>commons-codec-1.3.jar</p></td>
   <td><p>Vereist om de dienst van de Bewaarplaats aan te halen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs\third-party</p></td>
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
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p><p>JBoss-specifieke lib-map</p></td>
  </tr>
  <tr>
   <td><p>adobe-signatures-client.jar</p></td>
   <td><p>Vereist om de service Handtekening aan te roepen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-taskmanager-client-sdk.jar</p></td>
   <td><p>Vereist om de dienst van de Manager van de Taak aan te halen. </p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-truststore-client.jar</p></td>
   <td><p>Vereist om de dienst van de Opslag van het Vertrouwen aan te halen. </p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
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
   <td><p>&lt;<em>installatiemap</em>&gt;/sdk/client-libs/third-party</p> </td>
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
   <td><p>WebSphere-specifieke lib-map (<em>[WAS_HOME]</em>/runtimes)</p> <p>Als u uw clienttoepassing op dezelfde J2EE-toepassingsserver implementeert, hoeft u deze bestanden niet op te nemen.</p> </td>
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

**Zie ook**

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

[Gegevens doorgeven aan AEM Forms-services met de Java API](invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api)

[Een service aanroepen met een Java-clientbibliotheek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Verbindingseigenschappen instellen {#setting-connection-properties}

U stelt verbindingseigenschappen in om AEM Forms aan te roepen wanneer u de Java API gebruikt. Geef bij het instellen van eigenschappen voor verbindingen op of services extern of lokaal moeten worden aangeroepen en geef ook de verbindingsmodus en verificatiewaarden op. De waarden van de authentificatie worden vereist als de dienstveiligheid wordt toegelaten. Nochtans, als de dienstveiligheid gehandicapt is, is het niet noodzakelijk om authentificatiewaarden te specificeren.

De verbindingsmodus kan SOAP of EJB zijn. De modus EJB maakt gebruik van het RMI/IIOP-protocol en de prestaties van de modus EJB zijn beter dan die van de SOAP. De SOAP modus wordt gebruikt om een J2EE-toepassingsserverafhankelijkheid te elimineren of wanneer een firewall zich tussen AEM Forms en de clienttoepassing bevindt. De SOAP wijze gebruikt het HTTPS protocol als onderliggend vervoer en kan over firewallgrenzen communiceren. Als noch een J2EE-toepassingsserverafhankelijkheid, noch een firewall een probleem is, wordt u aangeraden de EJB-modus te gebruiken.

Als u een AEM Forms-service wilt aanroepen, stelt u de volgende verbindingseigenschappen in:

* **DSC_DEFAULT_EJB_ENDPOINT:** Als u de EJB-verbindingsmodus gebruikt, vertegenwoordigt deze waarde de URL van de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Als u AEM Forms op afstand wilt aanroepen, geeft u de naam op van de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Als uw clienttoepassing zich op dezelfde J2EE-toepassingsserver bevindt, kunt u `localhost`. Afhankelijk van welke J2EE-toepassingsserver AEM Forms wordt geïmplementeerd, geeft u een van de volgende waarden op:

   * JBoss: `https://<ServerName>:8080 (default port)`
   * WebSphere `iiop://<ServerName>:2809 (default port)`
   * WebLogic: `t3://<ServerName>:7001 (default port)`

* **DSC_DEFAULT_SOAP_ENDPOINT**: Als u de SOAP verbindingsmodus gebruikt, vertegenwoordigt deze waarde het eindpunt waarnaar een aanroepingsverzoek wordt verzonden. Als u AEM Forms op afstand wilt aanroepen, geeft u de naam op van de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Als uw clienttoepassing zich op dezelfde J2EE-toepassingsserver bevindt, kunt u `localhost` (bijvoorbeeld `http://localhost:8080`.)

   * De poortwaarde `8080` is van toepassing als de J2EE-toepassing JBoss is. Als de J2EE-toepassingsserver IBM® WebSphere® is, gebruikt u poort `9080`. En als de J2EE-toepassingsserver WebLogic is, gebruikt u poort `7001`. (Deze waarden zijn standaardpoortwaarden. Als u de havenwaarde verandert, gebruik het toepasselijke havenaantal.)

* **DSC_TRANSPORT_PROTOCOL**: Als u de EJB-verbindingsmodus gebruikt, geeft u `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL` voor deze waarde. Als u de SOAP-verbindingsmodus gebruikt, geeft u `ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL`.
* **DSC_SERVER_TYPE**: Geeft de J2EE-toepassingsserver aan waarop AEM Forms wordt geïmplementeerd. Geldige waarden zijn `JBoss`, `WebSphere`, `WebLogic`.

   * Als u deze eigenschap instelt op `WebSphere`de `java.naming.factory.initial` waarde is ingesteld op `com.ibm.ws.naming.util.WsnInitCtxFactory`.
   * Als u deze eigenschap instelt op `WebLogic`de `java.naming.factory.initial` waarde is ingesteld op `weblogic.jndi.WLInitialContextFactory`.
   * En als u deze eigenschap voor de verbinding instelt op `JBoss`de `java.naming.factory.initial` waarde is ingesteld op `org.jnp.interfaces.NamingContextFactory`.
   * U kunt de `java.naming.factory.initial` aan een waarde die aan uw vereisten voldoet als u niet de standaardwaarden wilt gebruiken.

  >[!NOTE]
  >
  >In plaats van een tekenreeks te gebruiken, stelt u de `DSC_SERVER_TYPE` verbinding, bezit, kunt u een statisch lid van gebruiken `ServiceClientFactoryProperties` klasse. De volgende waarden kunnen worden gebruikt: `ServiceClientFactoryProperties.DSC_WEBSPHERE_SERVER_TYPE`, `ServiceClientFactoryProperties.DSC_WEBLOGIC_SERVER_TYPE`, of `ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE`.

* **DSC_CREDENTIAL_USERNAME:** Hier geeft u de gebruikersnaam voor AEM formulieren op. Voor een gebruiker om de dienst van AEM Forms met succes aan te halen, hebben zij de rol van de Gebruiker van de Diensten nodig. Een gebruiker kan een andere rol ook hebben die de Dienst omvat roept toestemming. Anders, wordt een uitzondering geworpen wanneer zij proberen om de dienst aan te halen. Als de de dienstveiligheid gehandicapt is, is het niet noodzakelijk om dit verbindingsbezit te specificeren.
* **DSC_CREDENTIAL_PASSWORD:** Specifies the corresponding password value. Als de de dienstveiligheid gehandicapt is, is het niet noodzakelijk om dit verbindingsbezit te specificeren.
* **DSC_REQUEST_TIMEOUT:** De standaardtime-outlimiet voor verzoeken voor het SOAP verzoek is 1200000 milliseconden (20 minuten). Soms kan een aanvraag langer duren om de bewerking te voltooien. Een SOAP aanvraag die een grote set records ophaalt, kan bijvoorbeeld een langere time-outlimiet vereisen. U kunt de `ServiceClientFactoryProperties.DSC_REQUEST_TIMEOUT` om de de onderbrekingsgrens van de verzoekvraag voor de SOAP verzoeken te verhogen.

  **notitie**: Alleen op SOAP gebaseerde aanroepen ondersteunen de eigenschap DSC_REQUEST_TIMEOUT.

Voer de volgende taken uit om verbindingseigenschappen in te stellen:

1. Een `java.util.Properties` object met behulp van de constructor.
1. Als u het dialoogvenster `DSC_DEFAULT_EJB_ENDPOINT` eigenschap connection, activeer de `java.util.Properties` object `setProperty` en geeft de volgende waarden door:

   * De `ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT` opsommingswaarde
   * Een tekenreekswaarde die de URL van de J2EE-toepassingsserver opgeeft die als host fungeert voor AEM Forms

   >[!NOTE]
   >
   >Als u de SOAP-verbindingsmodus gebruikt, geeft u de `ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT` opsommingswaarde in plaats van de `ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT` opsommingswaarde.

1. Als u het dialoogvenster `DSC_TRANSPORT_PROTOCOL` eigenschap connection, activeer de `java.util.Properties` object `setProperty` en geeft de volgende waarden door:

   * De `ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL` opsommingswaarde
   * De `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL` opsommingswaarde

   >[!NOTE]
   >
   >Als u de SOAP-verbindingsmodus gebruikt, geeft u de `ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL`opsommingswaarde in plaats van de `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL` opsommingswaarde.

1. Als u het dialoogvenster `DSC_SERVER_TYPE` eigenschap connection, activeer de `java.util.Properties` object `setProperty` en geeft de volgende waarden door:

   * De `ServiceClientFactoryProperties.DSC_SERVER_TYPE`opsommingswaarde
   * Een tekenreekswaarde die de J2EE-toepassingsserver opgeeft waarop AEM Forms wordt gehost (als AEM Forms bijvoorbeeld wordt geïmplementeerd op JBoss, geeft u op `JBoss`).

      1. Als u het dialoogvenster `DSC_CREDENTIAL_USERNAME` eigenschap connection, activeer de `java.util.Properties` object `setProperty` en geeft de volgende waarden door:

   * De `ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME` opsommingswaarde
   * Een tekenreekswaarde die de gebruikersnaam opgeeft die vereist is om AEM Forms aan te roepen

      1. Als u het dialoogvenster `DSC_CREDENTIAL_PASSWORD` eigenschap connection, activeer de `java.util.Properties` object `setProperty` en geeft de volgende waarden door:

   * De `ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD` opsommingswaarde
   * Een tekenreekswaarde die de bijbehorende wachtwoordwaarde opgeeft

**De EJB-verbindingsmodus instellen voor JBoss**

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

**De EJB-verbindingsmodus instellen voor WebLogic**

In het volgende Java-codevoorbeeld worden eigenschappen voor verbindingen ingesteld om AEM Forms aan te roepen dat wordt geïmplementeerd op WebLogic en met de EJB-verbindingsmodus.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "t3://localhost:7001");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "WebLogic");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

**De EJB-verbindingsmodus instellen voor WebSphere**

In het volgende Java-codevoorbeeld worden eigenschappen van een verbinding ingesteld om AEM Forms aan te roepen dat wordt geïmplementeerd op WebSphere en met de EJB-verbindingsmodus.

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "iiop://localhost:2809");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "WebSphere");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

**De SOAP-verbindingsmodus instellen**

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

**Verbindingseigenschappen instellen wanneer servicebeveiliging is uitgeschakeld**

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

**De SOAP verbindingsmodus instellen met de time-outlimiet voor aangepaste aanvragen**

```java
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "http://localhost:8080");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_REQUEST_TIMEOUT, "1800000"); // Request timeout limit 30 Minutes
```

**AEM Forms aanroepen met een Context-object**

U kunt een `com.adobe.idp.Context` object om een AEM Forms-service aan te roepen met een geverifieerde gebruiker (de `com.adobe.idp.Context` -object staat voor een geverifieerde gebruiker). Wanneer u een `com.adobe.idp.Context` -object, hoeft u de `DSC_CREDENTIAL_USERNAME` of `DSC_CREDENTIAL_PASSWORD` eigenschappen. U kunt een `com.adobe.idp.Context` object wanneer gebruikers worden geautoriseerd met de opdracht `AuthenticationManagerServiceClient` object `authenticate` methode.

De `authenticate` methode retourneert een `AuthResult` object dat de resultaten van de verificatie bevat. U kunt een `com.adobe.idp.Context` object door de constructor ervan aan te roepen. Roep vervolgens het `com.adobe.idp.Context` object `initPrincipal` en geeft de `AuthResult` object, zoals in de volgende code wordt getoond:

```java
 Context myCtx = new Context();
 myCtx.initPrincipal(authResult);
```

In plaats van de `DSC_CREDENTIAL_USERNAME` of `DSC_CREDENTIAL_PASSWORD` eigenschappen, kunt u de `ServiceClientFactory` object `setContext` en geeft de `com.adobe.idp.Context` object. Wanneer u een gebruiker van een AEM formulier gebruikt om een service aan te roepen, moet u ervoor zorgen dat deze gebruiker de benoemde rol heeft `Services User` die vereist is om een AEM Forms-service aan te roepen.

Het volgende codevoorbeeld toont hoe te om een `com.adobe.idp.Context` object binnen verbindingsinstellingen dat wordt gebruikt om een `EncryptionServiceClient` object.

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
>Voor volledige informatie over het verifiëren van een gebruiker raadpleegt u [Gebruikers verifiëren](/help/forms/developing/users.md#authenticating-users).

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

Bij AEM Forms-servicetaken worden doorgaans PDF-documenten gebruikt of geproduceerd. Wanneer u de dienst aanhaalt, soms is het noodzakelijk om een document van de PDF (of andere documenttypes zoals de gegevens van XML) tot de dienst over te gaan. Soms is het ook nodig om een PDF-document te verwerken dat van de service is geretourneerd. De Java-klasse waarmee u gegevens kunt doorgeven van en naar AEM Forms-services is `com.adobe.idp.Document`.

AEM Forms-services accepteren een PDF-document niet als andere gegevenstypen, zoals een `java.io.InputStream` object of een bytearray. A `com.adobe.idp.Document` -object kan ook worden gebruikt om andere gegevenstypen, zoals XML-gegevens, aan services door te geven.

A `com.adobe.idp.Document` Het object is een serialiseerbaar Java-type, zodat het kan worden doorgegeven via een RMI-aanroep. De ontvangende zijde kan (zelfde gastheer, zelfde klassenlader), lokaal (zelfde gastheer, verschillende klassenlader), of ver (verschillende gastheer) worden collocated. Het doorgeven van documentinhoud is voor elk geval geoptimaliseerd. Als de afzender en de ontvanger zich bijvoorbeeld op dezelfde host bevinden, wordt de inhoud doorgegeven via een lokaal bestandssysteem. (In sommige gevallen kunnen documenten in het geheugen worden doorgegeven.)

Afhankelijk van de `com.adobe.idp.Document` objectgrootte, de gegevens worden binnen de `com.adobe.idp.Document` object of opgeslagen op het bestandssysteem van de server. Eventuele tijdelijke opslagmiddelen die door de `com.adobe.idp.Document` object wordt automatisch verwijderd bij het `com.adobe.idp.Document` verwijdering. (Zie [Documentobjecten verwijderen](invoking-aem-forms-using-java.md#disposing-document-objects).)

Soms is het nodig om het inhoudstype van een `com.adobe.idp.Document` -object voordat u het aan een service kunt doorgeven. Als een bewerking bijvoorbeeld een specifiek inhoudstype vereist, zoals `application/pdf`wordt aangeraden het inhoudstype te bepalen. (Zie [Het inhoudstype van een document bepalen](invoking-aem-forms-using-java.md#determining-the-content-type-of-a-document).)

De `com.adobe.idp.Document` -object probeert het inhoudstype te bepalen aan de hand van de opgegeven gegevens. Als het inhoudstype niet kan worden opgehaald uit de opgegeven gegevens (bijvoorbeeld wanneer de gegevens zijn opgegeven als een bytearray), stelt u het inhoudstype in. Als u het inhoudstype wilt instellen, roept u de opdracht `com.adobe.idp.Document` object `setContentType` methode. (Zie [Het inhoudstype van een document bepalen](invoking-aem-forms-using-java.md#determining-the-content-type-of-a-document))

Als secundaire bestanden zich op hetzelfde bestandssysteem bevinden, maakt u een `com.adobe.idp.Document` object sneller is. Als secundaire bestanden zich op externe bestandssystemen bevinden, moet er een kopieerbewerking worden uitgevoerd die de prestaties beïnvloedt.

Een toepassing kan beide `com.adobe.idp.Document` en `org.w3c.dom.Document` gegevenstypen. Zorg er echter voor dat u de `org.w3c.dom.Document` gegevenstype. Voor informatie over het omzetten van een `org.w3c.dom.Document` object naar een `com.adobe.idp.Document` object, zie [Snel starten (EJB-modus): Forms vooraf vullen met stroombare indelingen met de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-prepopulating-forms-with-flowable-layouts-using-the-java-api).

>[!NOTE]
>
>Om een geheugenlek in WebLogic te voorkomen tijdens het gebruik van een `com.adobe.idp.Document` de documentinformatie in delen van 2048 bytes of minder lezen. De volgende code leest bijvoorbeeld de documentinformatie in delen van 2048 bytes:

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

**Zie ook**

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Documenten maken {#creating-documents}

Een `com.adobe.idp.Document` -object voordat u een servicebewerking aanroept waarvoor een PDF-document (of andere documenttypen) als invoerwaarde is vereist. De `com.adobe.idp.Document` klasse biedt constructors waarmee u een document kunt maken van de volgende inhoudstypen:

* Een bytearray
* Een bestaande `com.adobe.idp.Document` object
* A `java.io.File` object
* A `java.io.InputStream` object
* A `java.net.URL` object

#### Een document maken op basis van een bytearray {#creating-a-document-based-on-a-byte-array}

In het volgende codevoorbeeld wordt een `com.adobe.idp.Document` object dat is gebaseerd op een bytearray.

**Een object Document maken dat is gebaseerd op een bytearray**

```java
 Document myPDFDocument = new Document(myByteArray);
```

#### Een document maken op basis van een ander document {#creating-a-document-based-on-another-document}

In het volgende codevoorbeeld wordt een `com.adobe.idp.Document` object dat is gebaseerd op een ander object `com.adobe.idp.Document` object.

**Een object Document maken dat is gebaseerd op een ander document**

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

In het volgende codevoorbeeld wordt een `com.adobe.idp.Document` object dat is gebaseerd op een PDF-bestand met de naam *map.pdf*. Dit bestand bevindt zich in de hoofdmap van de C-vaste schijf. Deze constructor probeert het MIME-inhoudstype in te stellen van de `com.adobe.idp.Document` met de bestandsnaamextensie.

De `com.adobe.idp.Document` constructor die een `java.io.File` -object accepteert ook een Booleaanse parameter. Door deze parameter in te stellen op `true`de `com.adobe.idp.Document` het bestand wordt verwijderd. Dit betekent dat u het bestand niet hoeft te verwijderen nadat u het hebt doorgegeven aan de `com.adobe.idp.Document` constructor.

Deze parameter instellen op `false` betekent dat u de eigendom van dit bestand behoudt. Deze parameter instellen op `true` is efficiënter. De reden is dat de `com.adobe.idp.Document` kan het bestand rechtstreeks naar het lokale beheerde gebied verplaatsen in plaats van het te kopiëren (wat langzamer is).

**Een object Document maken dat is gebaseerd op een PDF-bestand**

```java
 //Create a Document object based on the map.pdf source file
 File mySourceMap = new File("C:\\map.pdf");
 Document myPDFDocument = new Document(mySourceMap,true);
```

#### Een document maken op basis van een InputStream-object {#creating-a-document-based-on-an-inputstream-object}

In het volgende Java-codevoorbeeld wordt een `com.adobe.idp.Document` object dat is gebaseerd op een `java.io.InputStream` object.

**Een document maken op basis van een InputStream-object**

```java
 //Create a Document object based on an InputStream object
 InputStream is = new FileInputStream("C:\\Map.pdf");
 Document myPDFDocument = new Document(is);
```

#### Een document maken op basis van inhoud die toegankelijk is via een URL {#creating-a-document-based-on-content-accessible-from-an-url}

In het volgende Java-codevoorbeeld wordt een `com.adobe.idp.Document` object dat is gebaseerd op een PDF-bestand met de naam *map.pdf*. Dit bestand bevindt zich in een webtoepassing met de naam `WebApp` dat wordt uitgevoerd `localhost`. Deze constructor probeert het `com.adobe.idp.Document` MIME-inhoudstype van het object met het inhoudstype dat met het URL-protocol wordt geretourneerd.

De URL die aan de `com.adobe.idp.Document` object wordt altijd gelezen aan de zijde waar het origineel `com.adobe.idp.Document` -object wordt gemaakt, zoals in dit voorbeeld wordt getoond:

```java
     Document doc = new Document(new java.net.URL("file:c:/temp/input.pdf"));
```

Het c:/temp/input.pdf-bestand moet zich op de clientcomputer bevinden (niet op de servercomputer). Het is de clientcomputer waar de URL wordt gelezen en waar het `com.adobe.idp.Document` object is gemaakt.

**Een document maken op basis van inhoud die toegankelijk is via een URL**

```java
 //Create a Document object based on a java.net.URL object
 URL myURL = new URL("http", "localhost", 8080,"/WebApp/map.pdf");
 
 //Create another Document object
 Document myPDFDocument = new Document(myURL);
```

**Zie ook**

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Geretourneerde documenten afhandelen {#handling-returned-documents}

Servicebewerkingen die een PDF-document (of andere gegevenstypen zoals XML-gegevens) als uitvoerwaarde retourneren, retourneren een `com.adobe.idp.Document` object. Nadat u een `com.adobe.idp.Document` object hebt ontvangen, kunt u het converteren naar de volgende indelingen:

* Een `java.io.File` object
* Een `java.io.InputStream` object
* Een bytearray

Met de volgende coderegel wordt een `com.adobe.idp.Document` object naar een `java.io.InputStream` object. aannemen dat `myPDFDocument` vertegenwoordigt a `com.adobe.idp.Document` object:

```java
     java.io.InputStream resultStream = myDocument.getInputStream();
```

Op dezelfde manier kunt u de inhoud van een `com.adobe.idp.Document` naar een lokaal bestand door de volgende taken uit te voeren:

1. Een `java.io.File` object.
1. De `com.adobe.idp.Document` object `copyToFile` en geeft de `java.io.File`object.

In het volgende codevoorbeeld wordt de inhoud van een `com.adobe.idp.Document` object naar een bestand met de naam *anotherMap.pdf*.

**De inhoud van een documentobject kopiëren naar een bestand**

```java
 File outFile = new File("C:\\AnotherMap.pdf");
 myDocument.copyToFile (outFile);
```

**Zie ook**

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Het inhoudstype van een document bepalen {#determining-the-content-type-of-a-document}

Het MIME-type van een `com.adobe.idp.Document` door het object aan te roepen `com.adobe.idp.Document` object `getContentType` methode. Deze methode retourneert een tekenreekswaarde die het inhoudstype van het dialoogvenster `com.adobe.idp.Document` object. In de volgende tabel worden de verschillende inhoudstypen beschreven die AEM Forms retourneert.

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

In het volgende codevoorbeeld wordt het inhoudstype van een `com.adobe.idp.Document` object.

**Het inhoudstype van een object Document bepalen**

```java
 //Determine the content type of the Document object
 String ct = myDocument.getContentType();
 System.out.println("The content type of the Document object is " +ct);
```

**Zie ook**

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Documentobjecten verwijderen {#disposing-document-objects}

Wanneer u niet langer een `Document` -object wordt aangeraden het te verwijderen door het `dispose` methode. Elk `Document` -object gebruikt een bestandsdescriptor en maar liefst 75 MB aan RAM-ruimte op het hostplatform van uw toepassing. Indien een `Document` Het object wordt niet verwijderd. Het Java Garage-verzamelingsproces verwijdert het. Echter, door het eerder te verwijderen met behulp van de `dispose` kunt u geheugen vrijmaken dat door de `Document` object.

**Zie ook**

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Een service aanroepen met een Java-clientbibliotheek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Een service aanroepen met een Java-clientbibliotheek {#invoking-a-service-using-a-java-client-library}

De de dienstverrichtingen van AEM Forms kunnen worden aangehaald door sterk getypte API van de dienst te gebruiken, die als een cliëntbibliotheek van Java wordt bekend. A *Java-clientbibliotheek* is een reeks concrete klassen die toegang tot de diensten verlenen die in de de dienstcontainer worden opgesteld. U instantieert een Java-object dat de service vertegenwoordigt die moet worden aangeroepen in plaats van een `InvocationRequest` met de API voor oproepen. De oproepings-API wordt gebruikt om processen, zoals langlevende processen, aan te roepen die in Workbench zijn gemaakt. (Zie [Het aanhalen van mens-Centric langlevende Processen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).)

Als u een servicebewerking wilt uitvoeren, roept u een methode aan die tot het Java-object behoort. Een Java-clientbibliotheek bevat methoden die doorgaans een-op-een toewijzen aan servicebewerkingen. Wanneer u een Java-clientbibliotheek gebruikt, stelt u de vereiste verbindingseigenschappen in. (Zie [Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties).)

Nadat u verbindingseigenschappen hebt ingesteld, maakt u een `ServiceClientFactory` object dat wordt gebruikt om een Java-object te instantiëren waarmee u een service kunt aanroepen. Elke service met een Java-clientbibliotheek heeft een overeenkomstig clientobject. Als u bijvoorbeeld de Repository-service wilt aanroepen, maakt u een `ResourceRepositoryClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object. Het `ServiceClientFactory` object is verantwoordelijk voor het behoud van de verbindingsinstellingen die vereist zijn voor het aanroepen van AEM Forms-services.

Hoewel u een `ServiceClientFactory` is gewoonlijk snel, is sommige overheadkosten geïmpliceerd wanneer de fabriek voor het eerst wordt gebruikt. Dit object is geoptimaliseerd voor hergebruik en gebruik daarom, indien mogelijk, hetzelfde `ServiceClientFactory` -object wanneer u meerdere Java-client-objecten maakt. Maak dus geen aparte `ServiceClientFactory` object voor elk clientbibliotheekobject dat u maakt.

Er is een Manager die van de Gebruiker plaatst die het leven van de bevestiging van SAML controleert die binnen is `com.adobe.idp.Context` object dat invloed heeft op de `ServiceClientFactory` object. Deze instelling bepaalt de levensduur van alle verificatiecontext in AEM Forms, inclusief alle aanroepen die worden uitgevoerd met de Java API. Door gebrek, de periode waarin `ServiceCleintFactory` -object kan worden gebruikt binnen twee uur.

>[!NOTE]
>
>Om uit te leggen hoe u een service aanroept met de Java API, `writeResource` bewerking wordt aangeroepen. Met deze bewerking plaatst u een nieuwe bron in de opslagplaats.

U kunt de service Opslagplaats aanroepen door gebruik te maken van een Java-clientbibliotheek en de volgende stappen uit te voeren:

1. Neem jar-bestanden van de client op, zoals de adobe-repository-client.jar, in het klassenpad van uw Java-project. Voor informatie over de locatie van deze bestanden raadpleegt u [Inclusief AEM Forms Java-bibliotheekbestanden](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).
1. Stel verbindingseigenschappen in die vereist zijn om een service aan te roepen.
1. Een `ServiceClientFactory` door het object aan te roepen `ServiceClientFactory` statisch object `createInstance` en het doorgeven van de `java.util.Properties` object dat verbindingseigenschappen bevat.
1. Maak een `ResourceRepositoryClient` object door de constructor te gebruiken en het object door te `ServiceClientFactory` geven. Gebruik het `ResourceRepositoryClient` object om bewerkingen van de opslagplaatsservice te activeren.
1. Maak een object met behulp van de constructor en geef `null`een `RepositoryInfomodelFactoryBean` Met dit object kunt u een `Resource` object maken dat de inhoud vertegenwoordigt die aan de opslagplaats wordt toegevoegd.
1. Maak een `Resource` object door de methode van `newImage` het `RepositoryInfomodelFactoryBean` object aan te roepen en de volgende waarden door te geven:

   * Een unieke ID-waarde door `new Id()`.
   * Een unieke UUID-waarde door het opgeven van `new Lid()`.
   * De naam van de bron. U kunt de bestandsnaam van het XDP-bestand opgeven.

   De geretourneerde waarde omzetten in `Resource`.

1. Een `ResourceContent` door het object aan te roepen `RepositoryInfomodelFactoryBean` object `newImage` en de geretourneerde waarde naar `ResourceContent`. Dit object vertegenwoordigt de inhoud die aan de gegevensopslagruimte wordt toegevoegd.
1. Een `com.adobe.idp.Document` door een object door te geven `java.io.FileInputStream` object dat het XDP-bestand opslaat dat aan de gegevensopslagruimte moet worden toegevoegd. (Zie [Een document maken op basis van een InputStream-object](invoking-aem-forms-using-java.md#creating-a-document-based-on-an-inputstream-object).)
1. Voeg de inhoud van de `com.adobe.idp.Document` aan `ResourceContent` door het object aan te roepen `ResourceContent` object `setDataDocument` methode. Geef de `com.adobe.idp.Document` object.
1. Stel het MIME-type van het XDP-bestand in om aan de opslagplaats toe te voegen door het `ResourceContent` object `setMimeType` methode en doorgeven `application/vnd.adobe.xdp+xml`.
1. Voeg de inhoud van de `ResourceContent` aan `Resource` door het object aan te roepen `Resource` object `setContent` en het doorgeven van de `ResourceContent` object.
1. Voeg een beschrijving van de bron toe door de `Resource` object `setDescription` methode en het overgaan van een koordwaarde die een beschrijving van het middel vertegenwoordigt.
1. Voeg het formulierontwerp toe aan de gegevensopslagruimte door de `ResourceRepositoryClient` object `writeResource` en geeft de volgende waarden door:

   * Een tekenreekswaarde die het pad naar de bronverzameling opgeeft die de nieuwe bron bevat
   * De `Resource` object dat is gemaakt

**Zie ook**

[Snel starten (EJB-modus): een bron schrijven met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[AEM Forms aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

## Een kortstondig proces aanroepen met de API voor aanroepen {#invoking-a-short-lived-process-using-the-invocation-api}

U kunt een kortstondig proces aanroepen met de Java Invocation-API. Wanneer u een kortstondig proces met de Inroeping API aanroept, geeft u vereiste parameterwaarden door door te gebruiken `java.util.HashMap` object. Voor elke parameter om tot de dienst over te gaan, roep `java.util.HashMap` object `put` methode en specificeer het naam-waarde paar dat door de dienst wordt vereist om de gespecificeerde verrichting uit te voeren. Geef de exacte naam op van de parameters die bij het kortstondige proces horen.

>[!NOTE]
>
>Voor informatie over het aanroepen van een langdurig proces, zie [Het aanhalen van mens-Centric langlevende Processen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

De discussie gaat hier over het gebruik van de oproepings-API om het volgende kortstondige AEM Forms-proces met de naam `MyApplication/EncryptDocument`.

>[!NOTE]
>
>Dit proces is niet gebaseerd op een bestaand AEM Forms-proces. Om samen met het codevoorbeeld te volgen, creeer een proces genoemd `MyApplication/EncryptDocument` met Workbench. (Zie [Workbench gebruiken](https://www.adobe.com/go/learn_aemforms_workbench_63).)

Wanneer dit proces wordt aangeroepen, worden de volgende handelingen uitgevoerd:

1. Verkrijgt het onbeveiligde document van de PDF dat tot het proces wordt overgegaan. Deze actie is gebaseerd op de `SetValue` -bewerking. De invoerparameter voor dit proces is een `document` procesvariabele met de naam `inDoc`.
1. Hiermee versleutelt u het PDF-document met een wachtwoord. Deze actie is gebaseerd op de `PasswordEncryptPDF` -bewerking. Het wachtwoord gecodeerde PDF document is teruggekeerd in een procesvariabele genoemd `outDoc`.

### Het kortstondige MyApplication/EncryptDocument-proces aanroepen met de Java-oproepings-API {#invoke-the-myapplication-encryptdocument-short-lived-process-using-the-java-invocation-api}

De `MyApplication/EncryptDocument` kortstondig proces met de Java-oproepings-API:

1. Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project. (Zie [Inclusief AEM Forms Java-bibliotheekbestanden](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files).)
1. Een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie [Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Een `ServiceClient` object door de constructor ervan te gebruiken en de `ServiceClientFactory` object. A `ServiceClient` kunt u een servicebewerking aanroepen. Het behandelt taken zoals het lokaliseren van, het verzenden van, en het verpletteren van oproepingsverzoeken.
1. Een `java.util.HashMap` object met behulp van de constructor.
1. De `java.util.HashMap` object `put` methode voor elke inputparameter om tot het langlevende proces over te gaan. Omdat de `MyApplication/EncryptDocument` kortstondig proces vereist één invoerparameter van type `Document`, hoeft u alleen de `put` methode één keer, zoals in het volgende voorbeeld wordt getoond.

   ```java
    //Create a Map object to store the parameter value for inDoc
    Map params = new HashMap();
    InputStream inFile = new FileInputStream("C:\\Adobe\Loan.pdf");
    Document inDoc = new Document(inFile);
    params.put("inDoc", inDoc);
   ```

1. Een `InvocationRequest` door het object aan te roepen `ServiceClientFactory` object `createInvocationRequest` en geeft de volgende waarden door:

   * Een tekenreekswaarde die de naam aangeeft van het proces met een lange levensduur dat moet worden aangeroepen. Om het `MyApplication/EncryptDocument` proces, specificeren `MyApplication/EncryptDocument`.
   * Een tekenreekswaarde die staat voor de naam van de procesbewerking. Doorgaans is de naam van een kortstondige procesbewerking `invoke`.
   * De `java.util.HashMap` object dat de parameterwaarden bevat die de servicebewerking vereist.
   * Een Booleaanse waarde die `true`, die een synchrone aanvraag maakt (deze waarde is van toepassing om een kortstondig proces aan te roepen).

1. Verzend het oproepingsverzoek naar de service door het `ServiceClient` object `invoke` en het doorgeven van de `InvocationRequest` object. De `invoke` methode retourneert een `InvocationReponse` object.

   >[!NOTE]
   >
   >Een langdurig proces kan worden aangeroepen door de waarde door te geven `false`als de vierde parameter van de `createInvocationRequest` methode. De waarde doorgeven `false`*maakt een asynchrone aanvraag.*

1. Haal de geretourneerde waarde van het proces op door de `InvocationReponse` object `getOutputParameter` methode en het overgaan van een koordwaarde die de naam van de outputparameter specificeert. Geef in dit geval aan: `outDoc` ( `outDoc` is de naam van de uitvoerparameter voor de `MyApplication/EncryptDocument` proces). De geretourneerde waarde omzetten in `Document`, zoals in het volgende voorbeeld wordt getoond.

   ```java
    InvocationResponse response = myServiceClient.invoke(request);
    Document encryptDoc = (Document) response.getOutputParameter("outDoc");
   ```

1. Een `java.io.File` en zorg dat de bestandsextensie .pdf is.
1. De `com.adobe.idp.Document` object `copyToFile` methode om de inhoud van de `com.adobe.idp.Document` naar het bestand. Zorg ervoor dat u de `com.adobe.idp.Document` object dat is geretourneerd door de `getOutputParameter` methode.

**Zie ook**

[Snel starten: Een kortstondig proces aanroepen met de API voor aanroepen](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-short-lived-process-using-the-invocation-api)

[Het aanhalen van mens-Centric langlevende Processen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[Inclusief AEM Forms Java-bibliotheekbestanden](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)
