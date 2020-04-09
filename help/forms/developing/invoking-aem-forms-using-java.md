---
title: AEM-formulieren aanroepen met de JavaAPI
seo-title: AEM-formulieren aanroepen met de JavaAPI
description: 'null'
seo-description: 'null'
uuid: 5e2fef2a-05f3-4283-8fd3-2d7dca411000
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
discoiquuid: 0e6e7850-6137-42c5-b8e2-d4e352fddae2
translation-type: tm+mt
source-git-commit: b97452eb42275d889a82eb9364b5daf7075fcc41

---


# AEM-formulieren aanroepen met de Java API {#invoking-aem-forms-using-the-javaapi}

AEM-formulieren kunnen worden aangeroepen met de API van AEM Forms Java. Wanneer u de Java API voor AEM Forms gebruikt, kunt u de API voor oproepen of Java-clientbibliotheken gebruiken. Java-clientbibliotheken zijn beschikbaar voor services zoals Rights Management. Met deze sterk getypeerde API&#39;s kunt u Java-toepassingen ontwikkelen die AEM-formulieren aanroepen.

De oproepings-API zijn klassen die zich in het `com.adobe.idp.dsc` pakket bevinden. Met deze klassen kunt u een aanroepingsverzoek rechtstreeks naar een service verzenden en een geretourneerde aanroepingsreactie afhandelen. Gebruik de oproepings-API om kortstondige of langlevende processen aan te roepen die met Workbench zijn gemaakt.

De geadviseerde manier om een dienst programmatically aan te halen is een de cliëntbibliotheek van Java te gebruiken die aan de dienst in tegenstelling tot de Inroeping API beantwoordt. Als u bijvoorbeeld de coderingsservice wilt aanroepen, gebruikt u de clientbibliotheek van de coderingsservice. Om een de dienstverrichting van de Encryptie uit te voeren, haal een methode aan die tot het de dienstcliëntvoorwerp van de Encryptie behoort. U kunt een PDF-document versleutelen met een wachtwoord door de `EncryptionServiceClient` methode van het `encryptPDFUsingPassword` object aan te roepen.

De Java API ondersteunt de volgende functies:

* Het vervoerprotocol van RMI voor verre aanroeping
* VM-transport voor lokale aanroeping
* SOAP voor externe aanroep
* Verschillende verificatie, zoals gebruikersnaam en wachtwoord
* Synchrone en asynchrone oproepverzoeken

**Adobe Developer-website**

De Adobe Developer-website bevat de volgende artikelen waarin het aanroepen van AEM Forms-services met de Java API wordt besproken:

[Java-servlets gebruiken om AEM-formulierprocessen aan te roepen](https://www.adobe.com/devnet/livecycle/articles/java_servlets.html)

[De API voor AEM Forms Distiller aanroepen vanuit Java](https://www.adobe.com/devnet/livecycle/articles/distiller_java_03.html)

**Zie ook**

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](#including-aem-forms-java-library-files)

[Het aanhalen van mens-Centric langlevende Processen](/help/forms/developing/invoking-human-centric-long-lived.md#main-pars-text-0)

[AEM-formulieren aanroepen met webservices](/help/forms/developing/invoking-aem-forms-using-web.md)

[Verbindingseigenschappen instellen](#setting-connection-properties)

[Gegevens doorgeven aan AEM Forms-services met de Java API](#passing-data-to-aem-forms-services-using-the-java-api)

[Een service aanroepen met een Java-clientbibliotheek](#invoking-a-service-using-a-java-client-library)

[Een kortstondig proces aanroepen met de API voor aanroepen](#invoking-a-short-lived-process-using-the-invocation-api)

[Een Java-webtoepassing maken die een menselijk-centrisch proces van lange duur oproept](/help/forms/developing/invoking-human-centric-long-lived.md)

## Inclusief Java-bibliotheekbestanden voor AEM-formulieren {#including-aem-forms-java-library-files}

Als u een AEM Forms-service via programmacode wilt aanroepen met de Java API, neemt u de vereiste bibliotheekbestanden (JAR-bestanden) op in het klassepad van uw Java-project. De JAR-bestanden die u in het klassenpad van de clienttoepassing opneemt, zijn afhankelijk van verschillende factoren:

* De AEM Forms-service die moet worden aangeroepen. Een cliënttoepassing kan één of meerdere diensten aanhalen.
* De modus waarin u de service AEM Forms wilt activeren. U kunt de modus EJB of SOAP gebruiken. (Zie Verbindingseigenschappen [instellen](invoking-aem-forms-using-java.md#setting-connection-properties).)

>[!NOTE]
>
>(Alleen sleutel) Start de AEM Forms-server met de opdracht `standalone.bat -b <Server IP> -c lc_turnkey.xml` om een server-IP voor EJB op te geven

* De J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

### Servicespecifieke JAR-bestanden {#service-specific-jar-files}

In de volgende tabel staan de JAR-bestanden die vereist zijn om AEM Forms-services aan te roepen.

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
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk//client-libs/&lt;toepassingsserver&gt;</p></td>
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
   <td><p>De service PDF converteren is vereist. </p></td>
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
   <td><p>Vereist om de service Forms aan te roepen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-formdataintegration-client.jar</p></td>
   <td><p>Vereist om de dienst van de Integratie van de Gegevens van de Vorm aan te halen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-generatepdf-client.jar</p></td>
   <td><p>Vereist om de service PDF genereren aan te roepen.</p></td>
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p></td>
  </tr>
  <tr>
   <td><p>adobe-generate3dpdf-client.jar</p></td>
   <td><p>Vereist om de service 3D-PDF genereren aan te roepen.</p></td>
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
   <td><p>Vereist om de service PDF-hulpprogramma's of XMP-hulpprogramma's aan te roepen.</p></td>
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
   <td><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs/common</p><p>&lt;<i>installatiemap</i>&gt;/sdk/client-libs\third</p></td>
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
   <td><p>Vereist om de dienst van het Beheer van Rechten aan te halen.</p><p>Als AEM-formulieren worden geïmplementeerd op JBoss, neemt u al deze bestanden op. </p></td>
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

De volgende tabel bevat een lijst met JAR-bestanden die afhankelijk zijn van de verbindingsmodus en de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd.

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
   <td><p>Als AEM-formulieren wordt aangeroepen in de SOAP-modus, neemt u deze JAR-bestanden op.</p> </td>
   <td><p>&lt;<em>installatiemap</em>&gt;/sdk/client-libs/third-party</p> </td>
  </tr>
  <tr>
   <td><p> jboss-client.jar</p> </td>
   <td><p>Als AEM Forms wordt geïmplementeerd op JBoss Application Server, neemt u dit JAR-bestand op.</p> <p>Vereiste klassen worden niet gevonden door de klasseleider als jreliëf-client.jar en de jars waarnaar wordt verwezen, zich niet op dezelfde locatie bevinden.</p> </td>
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
     <li><p>Als AEM Forms wordt opgesteld op de Server van de Toepassing WebSphere, omvat deze JAR dossiers.</p> </li>
     <li><p>(com.ibm.ws.webservices.thinclient_6.1.0.jar is vereist voor het oproepen van webservices).</p> </li>
    </ul> </td>
   <td><p>WebSphere-specifieke bibliotheekmap (<em>[WAS_HOME]</em>/runtimes)</p> <p>Als u uw clienttoepassing op dezelfde J2EE-toepassingsserver implementeert, hoeft u deze bestanden niet op te nemen.</p> </td>
  </tr>
 </tbody>
</table>

### Oproepen van scenario&#39;s {#invoking-scenarios}

In de volgende tabel worden de aanroepingsscenario&#39;s aangegeven en worden de JAR-bestanden weergegeven die nodig zijn om AEM-formulieren aan te roepen.

<table>
 <thead>
  <tr>
   <th><p>Services</p> </th>
   <th><p>Inroepmodus</p> </th>
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

Als u een upgrade uitvoert van LiveCycle naar AEM Forms, wordt u aangeraden de JAR-bestanden voor AEM-formulieren op te nemen in het klassenpad van uw Java-project. Als u bijvoorbeeld services zoals Rights Management gebruikt, treedt er een compatibiliteitsprobleem op als u geen JAR-bestanden met AEM Forms opneemt in het klassenpad.

Ervan uitgaande dat u een upgrade uitvoert naar AEM Forms. Als u een Java-toepassing wilt gebruiken die de Rights Management-service aanroept, neemt u de versies van AEM Forms van de volgende JAR-bestanden op:

* adobe-rightsmanagement-client.jar
* adobe-livecycle-client.jar
* adobe-usermanager-client.jar

**Zie ook**

[AEM-formulieren aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

[Gegevens doorgeven aan AEM Forms-services met de Java API](invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api)

[Een service aanroepen met een Java-clientbibliotheek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Verbindingseigenschappen instellen {#setting-connection-properties}

U stelt verbindingseigenschappen in om AEM Forms aan te roepen wanneer u de Java API gebruikt. Geef bij het instellen van eigenschappen voor verbindingen op of services extern of lokaal moeten worden aangeroepen en geef ook de verbindingsmodus en verificatiewaarden op. De waarden van de authentificatie worden vereist als de dienstveiligheid wordt toegelaten. Nochtans, als de dienstveiligheid gehandicapt is, is het niet noodzakelijk om authentificatiewaarden te specificeren.

De verbindingsmodus kan SOAP- of EJB-modus zijn. De wijze EJB gebruikt het protocol RMI/IIOP, en de prestaties van de wijze EJB zijn beter dan de prestaties van de wijze van de ZEEP. De wijze van de ZEEP wordt gebruikt om een J2EE afhankelijkheid van de toepassingsserver te elimineren of wanneer een firewall tussen Vormen AEM en de cliënttoepassing wordt gevestigd. De wijze van de ZEEP gebruikt het HTTPS protocol als onderliggend vervoer en kan over firewallgrenzen communiceren. Als noch een J2EE-toepassingsserverafhankelijkheid, noch een firewall een probleem is, wordt u aangeraden de EJB-modus te gebruiken.

Als u een AEM Forms-service wilt aanroepen, stelt u de volgende verbindingseigenschappen in:

* **DSC_DEFAULT_EJB_ENDPOINT:** Als u de EJB-verbindingsmodus gebruikt, vertegenwoordigt deze waarde de URL van de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd. Als u AEM-formulieren op afstand wilt aanroepen, geeft u de naam op van de J2EE-toepassingsserver waarop AEM-formulieren worden geïmplementeerd. Als uw clienttoepassing zich op dezelfde J2EE-toepassingsserver bevindt, kunt u opgeven `localhost`. Afhankelijk van de J2EE-toepassingsserver waarop AEM Forms wordt geïmplementeerd, geeft u een van de volgende waarden op:

   * JBoss: `https://<ServerName>:8080 (default port)`
   * WebSphere: `iiop://<ServerName>:2809 (default port)`
   * WebLogic: `t3://<ServerName>:7001 (default port)`

* **DSC_DEFAULT_SOAP_ENDPOINT**: Als u de verbindingswijze van de ZEEP gebruikt, vertegenwoordigt deze waarde het eindpunt waarnaar een aanroepingsverzoek wordt verzonden. Als u AEM-formulieren op afstand wilt aanroepen, geeft u de naam op van de J2EE-toepassingsserver waarop AEM-formulieren worden geïmplementeerd. Als uw clienttoepassing zich op dezelfde J2EE-toepassingsserver bevindt, kunt u `localhost` (bijvoorbeeld `http://localhost:8080`.)

   * De poortwaarde `8080` is van toepassing als de J2EE-toepassing JBoss is. Als de J2EE-toepassingsserver IBM® WebSphere® is, gebruikt u poort `9080`. En als de J2EE-toepassingsserver WebLogic is, gebruikt u poort `7001`. (Deze waarden zijn standaardpoortwaarden. Als u de havenwaarde verandert, gebruik het toepasselijke havenaantal.)

* **DSC_TRANSPORT_PROTOCOL**: Geef deze waarde op als u de verbindingsmodus EJB gebruikt. `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL` Als u de verbindingsmodus SOAP gebruikt, geeft u op `ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL`.
* **DSC_SERVER_TYPE**: Geeft de J2EE-toepassingsserver op waarop AEM Forms wordt geïmplementeerd. Geldige waarden zijn `JBoss`, `WebSphere`, `WebLogic`.

   * Wanneer u deze verbindingseigenschap instelt op `WebSphere`, wordt de `java.naming.factory.initial` waarde ingesteld op `com.ibm.ws.naming.util.WsnInitCtxFactory`.
   * Wanneer u deze verbindingseigenschap instelt op `WebLogic`, wordt de `java.naming.factory.initial` waarde ingesteld op `weblogic.jndi.WLInitialContextFactory`.
   * Als u deze eigenschap voor verbinding instelt op `JBoss`, wordt de `java.naming.factory.initial` waarde ingesteld op `org.jnp.interfaces.NamingContextFactory`.
   * U kunt de `java.naming.factory.initial` eigenschap instellen op een waarde die aan uw vereisten voldoet als u de standaardwaarden niet wilt gebruiken.
   ***Opmerking**: In plaats van een tekenreeks te gebruiken om de `DSC_SERVER_TYPE` eigenschap connection in te stellen, kunt u een statisch lid van de `ServiceClientFactoryProperties` klasse gebruiken. De volgende waarden kunnen worden gebruikt: `ServiceClientFactoryProperties.DSC_WEBSPHERE_SERVER_TYPE`, `ServiceClientFactoryProperties.DSC_WEBLOGIC_SERVER_TYPE`, of `ServiceClientFactoryProperties.DSC_JBOSS_SERVER_TYPE`.

* **DSC_CREDENTIAL_USERNAME:** Hier geeft u de gebruikersnaam voor AEM-formulieren op. Voor een gebruiker om de dienst van Vormen AEM met succes aan te halen, hebben zij de rol van de Gebruiker van de Diensten nodig. Een gebruiker kan een andere rol ook hebben die de Dienst omvat roept toestemming. Anders, wordt een uitzondering geworpen wanneer zij proberen om de dienst aan te halen. Als de de dienstveiligheid gehandicapt is, is het niet noodzakelijk om dit verbindingsbezit te specificeren.
* **DSC_CREDENTIAL_PASSWORD:** Specifies the corresponding password value. Als de de dienstveiligheid gehandicapt is, is het niet noodzakelijk om dit verbindingsbezit te specificeren.
* **DSC_REQUEST_TIMEOUT:** De standaardlimiet voor de time-out van het verzoek voor SOAP is 1200000 milliseconden (20 minuten). Soms kan een aanvraag langer duren om de bewerking te voltooien. Een SOAP-aanvraag die bijvoorbeeld een grote set records ophaalt, kan een langere time-outlimiet vereisen. U kunt het gebruiken `ServiceClientFactoryProperties.DSC_REQUEST_TIMEOUT` om de de onderbrekingsgrens van de verzoekvraag voor de verzoeken van de ZEEP te verhogen.

   **opmerking**: Alleen op SOAP gebaseerde aanroepen ondersteunen de eigenschap DSC_REQUEST_TIMEOUT.

Voer de volgende taken uit om verbindingseigenschappen in te stellen:

1. Maak een `java.util.Properties` object met de constructor ervan.
1. Als u de eigenschap `DSC_DEFAULT_EJB_ENDPOINT` connection wilt instellen, roept u de `java.util.Properties` methode van het `setProperty` object op en geeft u de volgende waarden door:

   * De `ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT` opsommingswaarde
   * Een tekenreekswaarde die de URL opgeeft van de J2EE-toepassingsserver die als host fungeert voor AEM-formulieren
   >[!NOTE]
   >
   >Als u de verbindingswijze van de ZEEP gebruikt, specificeer de `ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT` opsommingswaarde in plaats van de `ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT` opsommingswaarde.

1. Als u de eigenschap `DSC_TRANSPORT_PROTOCOL` connection wilt instellen, roept u de `java.util.Properties` methode van het `setProperty` object op en geeft u de volgende waarden door:

   * De `ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL` opsommingswaarde
   * De `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL` opsommingswaarde
   >[!NOTE]
   >
   >Als u de verbindingswijze van de ZEEP gebruikt, specificeer de `ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL`opsommingswaarde in plaats van de `ServiceClientFactoryProperties.DSC_EJB_PROTOCOL` opsommingswaarde.

1. Als u de eigenschap `DSC_SERVER_TYPE` connection wilt instellen, roept u de `java.util.Properties` methode van het `setProperty` object op en geeft u de volgende waarden door:

   * De `ServiceClientFactoryProperties.DSC_SERVER_TYPE`opsommingswaarde
   * Een tekenreekswaarde die de J2EE-toepassingsserver opgeeft waarop AEM Forms wordt gehost (bijvoorbeeld als AEM Forms wordt geïmplementeerd op JBoss, geeft u op `JBoss`).

      1. Als u de eigenschap `DSC_CREDENTIAL_USERNAME` connection wilt instellen, roept u de `java.util.Properties` methode van het `setProperty` object op en geeft u de volgende waarden door:
   * De `ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME` opsommingswaarde
   * Een tekenreekswaarde die de gebruikersnaam opgeeft die vereist is om AEM-formulieren aan te roepen

      1. Als u de eigenschap `DSC_CREDENTIAL_PASSWORD` connection wilt instellen, roept u de `java.util.Properties` methode van het `setProperty` object op en geeft u de volgende waarden door:
   * De `ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD` opsommingswaarde
   * Een tekenreekswaarde die de bijbehorende wachtwoordwaarde opgeeft



**De EJB-verbindingsmodus instellen voor JBoss**

In het volgende Java-codevoorbeeld worden eigenschappen voor verbindingen ingesteld om AEM-formulieren aan te roepen die worden geïmplementeerd op JBoss en die de EJB-verbindingsmodus gebruiken.

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

In het volgende Java-codevoorbeeld worden eigenschappen voor verbindingen ingesteld om AEM-formulieren aan te roepen die op WebLogic worden geïmplementeerd en die de EJB-verbindingsmodus gebruiken.

```as3
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "t3://localhost:7001");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "WebLogic");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

**De EJB-verbindingsmodus instellen voor WebSphere**

In het volgende voorbeeld van de Java-code worden eigenschappen voor verbindingen ingesteld om AEM-formulieren aan te roepen die op WebSphere worden geïmplementeerd en die de EJB-verbindingsmodus gebruiken.

```as3
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "iiop://localhost:2809");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "WebSphere");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

**De verbindingsmodus SOAP instellen**

In het volgende voorbeeld van de Java-code worden eigenschappen van de verbinding in de SOAP-modus ingesteld om AEM-formulieren aan te roepen die in JBoss worden geïmplementeerd.

```as3
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "http://localhost:8080");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
```

>[!NOTE]
>
>Als u de SOAP-verbindingsmodus selecteert, moet u ervoor zorgen dat er extra JAR-bestanden worden opgenomen in het klassepad van de clienttoepassing.

**Verbindingseigenschappen instellen wanneer servicebeveiliging is uitgeschakeld**

In het volgende Java-codevoorbeeld worden eigenschappen voor verbindingen ingesteld die vereist zijn om AEM-formulieren aan te roepen die worden geïmplementeerd op JBoss Application Server en wanneer de servicebeveiliging is uitgeschakeld.

```as3
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_EJB_ENDPOINT, "jnp://localhost:1099");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_EJB_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
```

>[!NOTE]
>
>Alle Java-snelstarthandleidingen die zijn gekoppeld aan Programmeren met AEM-formulieren, tonen zowel de verbindingsinstellingen EJB als SOAP.

**De SOAP-verbindingsmodus instellen met de time-outlimiet voor aangepaste aanvragen**

```as3
 Properties ConnectionProps = new Properties();
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "http://localhost:8080");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
 ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
ConnectionProps.setProperty(ServiceClientFactoryProperties.DSC_REQUEST_TIMEOUT, "1800000"); // Request timeout limit 30 Minutes
```

**Een Context-object gebruiken om AEM-formulieren aan te roepen**

U kunt een `com.adobe.idp.Context` object gebruiken om een AEM Forms-service aan te roepen met een geverifieerde gebruiker (het `com.adobe.idp.Context` object vertegenwoordigt een geverifieerde gebruiker). Wanneer u een `com.adobe.idp.Context` object gebruikt, hoeft u de eigenschappen `DSC_CREDENTIAL_USERNAME` of `DSC_CREDENTIAL_PASSWORD` eigenschappen niet in te stellen. U kunt een `com.adobe.idp.Context` object verkrijgen wanneer u gebruikers autoriseert met de `AuthenticationManagerServiceClient` methode van het `authenticate` object.

De `authenticate` methode retourneert een `AuthResult` object dat de resultaten van de verificatie bevat. U kunt een `com.adobe.idp.Context` object maken door de constructor ervan aan te roepen. Roep vervolgens de `com.adobe.idp.Context` methode van het `initPrincipal` object aan en geef het `AuthResult` object door, zoals in de volgende code wordt getoond:

```as3
 Context myCtx = new Context();
 myCtx.initPrincipal(authResult);
```

In plaats van de eigenschappen `DSC_CREDENTIAL_USERNAME` of eigenschappen in te stellen, kunt u de `DSC_CREDENTIAL_PASSWORD` methode van het `ServiceClientFactory` object aanroepen en het `setContext` `com.adobe.idp.Context` object doorgeven. Als u een gebruiker van een AEM-formulier gebruikt om een service aan te roepen, moet u ervoor zorgen dat deze gebruiker de benoemde rol heeft `Services User` die nodig is om een AEM Forms-service aan te roepen.

In het volgende codevoorbeeld ziet u hoe u een `com.adobe.idp.Context` object gebruikt binnen verbindingsinstellingen die worden gebruikt om een `EncryptionServiceClient` object te maken.

```as3
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
>Voor volledige details over het voor authentiek verklaren van een gebruiker, zie [het Voor authentiek verklaren Gebruikers](/help/forms/developing/users.md#authenticating-users).

### Oproepen van scenario&#39;s {#invoking_scenarios-1}

De volgende aanroepende scenario&#39;s worden besproken in deze sectie:

* Een clienttoepassing die wordt uitgevoerd in een eigen Java Virtual Machine (JVM), roept een zelfstandige AEM Forms-instantie aan.
* Een cliënttoepassing die in zijn eigen JVM loopt roept gegroepeerde instanties van Vormen AEM aan.

### Clienttoepassing die een zelfstandige AEM Forms-instantie aanroept {#client-application-invoking-a-stand-alone-aem-forms-instance}

In het volgende diagram ziet u een clienttoepassing die in een eigen JVM wordt uitgevoerd en een zelfstandige AEM Forms-instantie aanroept.

In dit scenario wordt een clienttoepassing uitgevoerd in een eigen JVM en worden de services van AEM Forms aangeroepen.

>[!NOTE]
>
>Dit scenario is het het aanhalen scenario waarop alle Snelle Begint gebaseerd is.

### Clienttoepassing die geclusterde AEM Forms-instanties aanroept {#client-application-invoking-clustered-aem-forms-instances}

In het volgende diagram wordt een clienttoepassing weergegeven die in een eigen JVM wordt uitgevoerd en die instanties van AEM Forms aanroept die zich in een cluster bevinden.

Dit scenario is vergelijkbaar met een clienttoepassing die een zelfstandige instantie van AEM Forms aanroept. De URL van de provider is echter anders. Als een clienttoepassing verbinding wil maken met een specifieke J2EE-toepassingsserver, moet de toepassing de URL wijzigen om naar de specifieke J2EE-toepassingsserver te verwijzen.

Verwijzen naar een specifieke J2EE-toepassingsserver wordt niet aanbevolen, omdat de verbinding tussen de clienttoepassing en AEM Forms wordt beëindigd als de toepassingsserver stopt. Het wordt aanbevolen dat de provider-URL verwijst naar een JNDI-manager op celniveau in plaats van een specifieke J2EE-toepassingsserver.

Clienttoepassingen die de SOAP-verbindingsmodus gebruiken, kunnen de HTTP-taakverdelingpoort voor de cluster gebruiken. Clienttoepassingen die gebruikmaken van de EJB-verbindingsmodus kunnen verbinding maken met de EJB-poort van een specifieke J2EE-toepassingsserver. Met deze handeling wordt de taakverdeling tussen clusterknooppunten afgehandeld.

**WebSphere**

Het volgende voorbeeld toont de inhoud van een jndi.properties- dossier dat wordt gebruikt om met Vormen te verbinden AEM die op WebSphere wordt opgesteld.

```as3
 java.naming.factory.initial=com.ibm.websphere.naming.
 WsnInitialContextFactory
 java.naming.provider.url=corbaloc::appserver1:9810,:appserver2:9810
```

**WebLogic**

In het volgende voorbeeld wordt de inhoud getoond van een bestand jndi.properties dat wordt gebruikt om verbinding te maken met AEM-formulieren die op WebLogic worden geïmplementeerd.

```as3
 java.naming.factory.initial=weblogic.jndi.WLInitialContextFactory
 java.naming.provider.url=t3://appserver1:8001, appserver2:8001
```

**JBoss**

In het volgende voorbeeld wordt de inhoud getoond van een bestand jndi.properties dat wordt gebruikt om verbinding te maken met AEM-formulieren die worden geïmplementeerd op JBoss.

```as3
 java.naming.factory.initial= org.jnp.interfaces.NamingContextFactory
 java.naming.provider.url= jnp://appserver1:1099, appserver2:1099,
 appserver3:1099
```

>[!NOTE]
>
>Raadpleeg uw beheerder om de naam en het poortnummer van de J2EE-toepassingsserver te bepalen.

**Zie ook**

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Gegevens doorgeven aan AEM Forms-services met de Java API](invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api)

[Een service aanroepen met een Java-clientbibliotheek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Gegevens doorgeven aan AEM Forms-services met de Java API {#passing-data-to-aem-forms-services-using-the-java-api}

In AEM Forms worden meestal PDF-documenten gebruikt of geproduceerd. Wanneer u een service oproept, is het soms nodig om een PDF-document (of andere documenttypen zoals XML-gegevens) door te geven aan de service. Soms is het ook nodig om een PDF-document af te handelen dat door de service wordt geretourneerd. De Java-klasse waarmee u gegevens kunt doorgeven van en naar AEM Forms-services is `com.adobe.idp.Document`.

AEM Forms-services accepteren een PDF-document niet als andere gegevenstypen, zoals een `java.io.InputStream` object of een bytearray. Een `com.adobe.idp.Document` object kan ook worden gebruikt om andere typen gegevens, zoals XML-gegevens, aan services door te geven.

Een `com.adobe.idp.Document` voorwerp is een serializable type van Java, zodat kan het over een vraag worden overgegaan RMI. De ontvangende zijde kan (zelfde gastheer, zelfde klassenlader), lokaal (zelfde gastheer, verschillende klassenlader), of ver (verschillende gastheer) worden collocated. Het doorgeven van documentinhoud is voor elk geval geoptimaliseerd. Als de afzender en de ontvanger zich bijvoorbeeld op dezelfde host bevinden, wordt de inhoud doorgegeven via een lokaal bestandssysteem. (In sommige gevallen kunnen documenten in het geheugen worden doorgegeven.)

Afhankelijk van de `com.adobe.idp.Document` objectgrootte worden de gegevens binnen het `com.adobe.idp.Document` object vervoerd of op het bestandssysteem van de server opgeslagen. Eventuele tijdelijke opslagmiddelen die door het `com.adobe.idp.Document` object worden gebruikt, worden automatisch verwijderd bij de `com.adobe.idp.Document` verwijdering. (Zie [Documentobjecten](invoking-aem-forms-using-java.md#disposing-document-objects)verwijderen.)

Soms is het noodzakelijk om het inhoudstype van een `com.adobe.idp.Document` voorwerp te kennen alvorens u het aan de dienst kunt overgaan. Als een bewerking bijvoorbeeld een specifiek inhoudstype vereist, `application/pdf`wordt u aangeraden het inhoudstype te bepalen. (Zie [Het inhoudstype van een document](invoking-aem-forms-using-java.md#determining-the-content-type-of-a-document)bepalen.)

Het `com.adobe.idp.Document` object probeert het inhoudstype te bepalen aan de hand van de verschafte gegevens. Als het inhoudstype niet kan worden opgehaald uit de opgegeven gegevens (bijvoorbeeld wanneer de gegevens zijn opgegeven als een bytearray), stelt u het inhoudstype in. Als u het inhoudstype wilt instellen, roept u de `com.adobe.idp.Document` methode van het `setContentType` object aan. (Zie [Het inhoudstype van een document](invoking-aem-forms-using-java.md#determining-the-content-type-of-a-document)bepalen)

Als secundaire bestanden zich op hetzelfde bestandssysteem bevinden, wordt het sneller een `com.adobe.idp.Document` object te maken. Als secundaire bestanden zich op externe bestandssystemen bevinden, moet een kopieerbewerking worden uitgevoerd die de prestaties beïnvloedt.

Een toepassing kan zowel `com.adobe.idp.Document` als `org.w3c.dom.Document` gegevenstypen bevatten. Zorg er echter voor dat u het `org.w3c.dom.Document` gegevenstype volledig kwalificeert. Zie `org.w3c.dom.Document` Snel starten (EJB-modus) voor informatie over het omzetten van een `com.adobe.idp.Document` object in een [object: Formulieren vooraf invullen met stroombare indelingen met behulp van de Java API](/help/forms/developing/forms-service-api-quick-starts.md#quick-start-soap-mode-prepopulating-forms-with-flowable-layouts-using-the-java-api).

>[!NOTE]
>
>Als u een geheugenlek in WebLogic wilt voorkomen terwijl u een `com.adobe.idp.Document` object gebruikt, leest u de documentinformatie in delen van 2048 bytes of minder. De volgende code leest bijvoorbeeld de documentinformatie in delen van 2048 bytes:

```as3
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

[AEM-formulieren aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Documenten maken {#creating-documents}

Maak een `com.adobe.idp.Document` object voordat u een servicebewerking aanroept waarvoor een PDF-document (of andere documenttypen) als invoerwaarde is vereist. De `com.adobe.idp.Document` klasse biedt constructors waarmee u een document kunt maken van de volgende inhoudstypen:

* Een bytearray
* Een bestaand `com.adobe.idp.Document` object
* Een `java.io.File` object
* Een `java.io.InputStream` object
* Een `java.net.URL` object

#### Een document maken op basis van een bytearray {#creating-a-document-based-on-a-byte-array}

In het volgende codevoorbeeld wordt een `com.adobe.idp.Document` object gemaakt dat is gebaseerd op een bytearray.

**Een object Document maken dat is gebaseerd op een bytearray**

```as3
 Document myPDFDocument = new Document(myByteArray);
```

#### Een document maken op basis van een ander document {#creating-a-document-based-on-another-document}

In het volgende codevoorbeeld wordt een `com.adobe.idp.Document` object gemaakt dat is gebaseerd op een ander `com.adobe.idp.Document` object.

**Een object Document maken dat is gebaseerd op een ander document**

```as3
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

In het volgende codevoorbeeld wordt een `com.adobe.idp.Document` object gemaakt dat is gebaseerd op een PDF-bestand met de naam *map.pdf*. Dit bestand bevindt zich in de hoofdmap van de C-vaste schijf. Deze constructor probeert het MIME-inhoudstype van het `com.adobe.idp.Document` object in te stellen met de bestandsnaamextensie.

De `com.adobe.idp.Document` constructor die een `java.io.File` object accepteert, accepteert ook een Booleaanse parameter. Door deze parameter in te stellen op `true`, verwijdert het `com.adobe.idp.Document` object het bestand. Dit betekent dat u het bestand niet hoeft te verwijderen nadat u het hebt doorgegeven aan de `com.adobe.idp.Document` constructor.

Als u deze parameter instelt op `false` betekent dit dat u de eigendom van dit bestand behoudt. Het instellen van deze parameter op `true` is efficiënter. De reden hiervoor is dat het `com.adobe.idp.Document` object het bestand rechtstreeks naar het lokale beheerde gebied kan verplaatsen in plaats van het te kopiëren (wat langzamer is).

**Een object Document maken dat is gebaseerd op een PDF-bestand**

```as3
 //Create a Document object based on the map.pdf source file
 File mySourceMap = new File("C:\\map.pdf");
 Document myPDFDocument = new Document(mySourceMap,true);
```

#### Een document maken op basis van een InputStream-object {#creating-a-document-based-on-an-inputstream-object}

In het volgende Java-codevoorbeeld wordt een `com.adobe.idp.Document` object gemaakt dat is gebaseerd op een `java.io.InputStream` object.

**Een document maken op basis van een InputStream-object**

```as3
 //Create a Document object based on an InputStream object
 InputStream is = new FileInputStream("C:\\Map.pdf");
 Document myPDFDocument = new Document(is);
```

#### Een document maken op basis van inhoud die toegankelijk is via een URL {#creating-a-document-based-on-content-accessible-from-an-url}

In het volgende Java-codevoorbeeld wordt een `com.adobe.idp.Document` object gemaakt dat is gebaseerd op een PDF-bestand met de naam *map.pdf*. Dit bestand bevindt zich in een webtoepassing met de naam `WebApp` waarop wordt uitgevoerd `localhost`. Deze constructor probeert het MIME-inhoudstype van het `com.adobe.idp.Document` object in te stellen met het inhoudstype dat met het URL-protocol wordt geretourneerd.

De URL die aan het `com.adobe.idp.Document` object wordt gegeven, wordt altijd gelezen aan de zijde waar het oorspronkelijke `com.adobe.idp.Document` object is gemaakt, zoals in dit voorbeeld wordt getoond:

```as3
     Document doc = new Document(new java.net.URL("file:c:/temp/input.pdf"));
```

Het bestand c:/temp/input.pdf moet zich op de clientcomputer bevinden (niet op de servercomputer). Op de clientcomputer wordt de URL gelezen en is het `com.adobe.idp.Document` object gemaakt.

**Een document maken op basis van inhoud die toegankelijk is via een URL**

```as3
 //Create a Document object based on a java.net.URL object
 URL myURL = new URL("http", "localhost", 8080,"/WebApp/map.pdf");
 
 //Create another Document object
 Document myPDFDocument = new Document(myURL);
```

**Zie ook**

[AEM-formulieren aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Teruggestuurde documenten verwerken {#handling-returned-documents}

Servicetaken die een PDF-document (of andere gegevenstypen zoals XML-gegevens) als een uitvoerwaarde retourneren, retourneren een `com.adobe.idp.Document` object. Nadat u een `com.adobe.idp.Document` object hebt ontvangen, kunt u het omzetten in de volgende indelingen:

* Een `java.io.File` object
* Een `java.io.InputStream` object
* Een bytearray

De volgende coderegel zet een `com.adobe.idp.Document` object om in een `java.io.InputStream` object. Stel dat dit `myPDFDocument` een `com.adobe.idp.Document` object vertegenwoordigt:

```as3
     java.io.InputStream resultStream = myDocument.getInputStream();
```

Op dezelfde manier kunt u de inhoud van een bestand kopiëren `com.adobe.idp.Document` naar een lokaal bestand door de volgende taken uit te voeren:

1. Create a `java.io.File` object.
1. Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan en geef het `java.io.File`object door.

In het volgende codevoorbeeld wordt de inhoud van een `com.adobe.idp.Document` object gekopieerd naar het bestand *OtherMap.pdf*.

**De inhoud van een documentobject kopiëren naar een bestand**

```as3
 File outFile = new File("C:\\AnotherMap.pdf");
 myDocument.copyToFile (outFile);
```

**Zie ook**

[AEM-formulieren aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Het inhoudstype van een document bepalen {#determining-the-content-type-of-a-document}

Bepaal het MIME-type van een `com.adobe.idp.Document` object door de `com.adobe.idp.Document` methode van het `getContentType` object aan te roepen. Deze methode retourneert een tekenreekswaarde die het inhoudstype van het `com.adobe.idp.Document` object opgeeft. In de volgende tabel worden de verschillende inhoudstypen beschreven die door AEM Forms worden geretourneerd.

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

**Het inhoudstype van een object Document bepalen**

```as3
 //Determine the content type of the Document object
 String ct = myDocument.getContentType();
 System.out.println("The content type of the Document object is " +ct);
```

**Zie ook**

[AEM-formulieren aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Verbindingseigenschappen instellen](invoking-aem-forms-using-java.md#setting-connection-properties)

### Documentobjecten verwijderen {#disposing-document-objects}

Wanneer u een `Document` object niet meer nodig hebt, wordt u aangeraden het te verwijderen door de `dispose` methode ervan aan te roepen. Elk `Document` object gebruikt een bestandsdescriptor en maar liefst 75 MB aan RAM-ruimte op het hostplatform van uw toepassing. Als een `Document` object niet wordt verwijderd, verwijdert het Java Garage-verzamelingsproces het. Als u dit object echter eerder verwijdert met de `dispose` methode, kunt u het geheugen dat door het `Document` object wordt bezet, vrijmaken.

**Zie ook**

[AEM-formulieren aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Een service aanroepen met een Java-clientbibliotheek](invoking-aem-forms-using-java.md#invoking-a-service-using-a-java-client-library)

## Een service aanroepen met een Java-clientbibliotheek {#invoking-a-service-using-a-java-client-library}

De de dienstverrichtingen van de Vormen van AEM kunnen worden aangehaald door sterk getypte API van de dienst te gebruiken, die als een cliëntbibliotheek van Java wordt bekend. Een *Java-clientbibliotheek* is een reeks concrete klassen die toegang bieden tot services die in de servicecontainer zijn geïmplementeerd. U instantieert een Java-object dat de service vertegenwoordigt die moet worden aangeroepen in plaats van een `InvocationRequest` object te maken met de API voor aanroepen. De oproepings-API wordt gebruikt om processen, zoals langlevende processen, aan te roepen die in Workbench zijn gemaakt. (Zie [Langdurige processen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)aanroepen vanuit menselijk perspectief.)

Als u een servicebewerking wilt uitvoeren, roept u een methode aan die tot het Java-object behoort. Een Java-clientbibliotheek bevat methoden die doorgaans een-op-een toewijzen aan servicebewerkingen. Wanneer u een Java-clientbibliotheek gebruikt, stelt u vereiste verbindingseigenschappen in. (Zie Verbindingseigenschappen [instellen](invoking-aem-forms-using-java.md#setting-connection-properties).)

Nadat u verbindingseigenschappen hebt ingesteld, maakt u een `ServiceClientFactory` object dat wordt gebruikt om een Java-object te instantiëren waarmee u een service kunt aanroepen. Elke service met een Java-clientbibliotheek heeft een overeenkomstig clientobject. Als u bijvoorbeeld de Repository-service wilt aanroepen, maakt u een `ResourceRepositoryClient` object met behulp van de constructor en geeft u het `ServiceClientFactory` object door. Het `ServiceClientFactory` object is verantwoordelijk voor het onderhoud van de verbindingsinstellingen die vereist zijn om AEM Forms-services aan te roepen.

Hoewel het verkrijgen van een `ServiceClientFactory` product doorgaans snel is, is er sprake van enige overhead wanneer de fabriek voor het eerst wordt gebruikt. Dit object is geoptimaliseerd voor hergebruik en gebruik daarom, indien mogelijk, hetzelfde `ServiceClientFactory` object wanneer u meerdere Java-client-objecten maakt. Maak dus geen afzonderlijk `ServiceClientFactory` object voor elk clientbibliotheekobject dat u maakt.

Er is een manager die van de Gebruiker plaatst die het leven van de bevestiging van SAML controleert die binnen het `com.adobe.idp.Context` voorwerp is dat het `ServiceClientFactory` voorwerp beïnvloedt. Met deze instelling bepaalt u de levensduur van alle verificatiecontext in AEM Forms, inclusief alle aanroepen die met de Java API worden uitgevoerd. Standaard kan een `ServiceCleintFactory` object twee uur worden gebruikt.

>[!NOTE]
>
>Om uit te leggen hoe u een service aanroept met de Java API, wordt de `writeResource` bewerking van de Repository-service aangeroepen. Deze verrichting plaatst een nieuwe middel in de bewaarplaats.

U kunt de Repository-service activeren door een Java-clientbibliotheek te gebruiken en de volgende stappen uit te voeren:

1. Neem client-JAR-bestanden, zoals de adobe-repository-client.jar, op in het klassenpad van uw Java-project. Zie [Including AEM Forms Java library files](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor informatie over de locatie van deze bestanden.
1. Stel verbindingseigenschappen in die vereist zijn om een service aan te roepen.
1. Maak een `ServiceClientFactory` object door de statische `ServiceClientFactory` methode van het `createInstance` object aan te roepen en het `java.util.Properties` object dat verbindingseigenschappen bevat door te geven.
1. Maak een `ResourceRepositoryClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven. Gebruik het `ResourceRepositoryClient` object om bewerkingen van de Repository-service aan te roepen.
1. Maak een `RepositoryInfomodelFactoryBean` object met behulp van de constructor en geef het door `null`. Met dit object kunt u een `Resource` object maken dat de inhoud vertegenwoordigt die aan de opslagplaats is toegevoegd.
1. Maak een `Resource` object door de methode van het `RepositoryInfomodelFactoryBean` `newImage` object aan te roepen en de volgende waarden door te geven:

   * Een unieke id-waarde door op te geven `new Id()`.
   * Een unieke UUID-waarde door op te geven `new Lid()`.
   * De naam van de bron. U kunt de bestandsnaam van het XDP-bestand opgeven.
   Kiezen naar de geretourneerde waarde `Resource`.

1. Maak een `ResourceContent` object door de `RepositoryInfomodelFactoryBean` methode van het `newImage` object aan te roepen en de geretourneerde waarde naar te casten `ResourceContent`. Dit object vertegenwoordigt de inhoud die aan de gegevensopslagruimte wordt toegevoegd.
1. Maak een `com.adobe.idp.Document` object door een `java.io.FileInputStream` object door te geven waarin het XDP-bestand wordt opgeslagen dat aan de gegevensopslagruimte moet worden toegevoegd. (Zie Een document [maken op basis van een InputStream-object](invoking-aem-forms-using-java.md#creating-a-document-based-on-an-inputstream-object).)
1. Voeg de inhoud van het `com.adobe.idp.Document` object toe aan het `ResourceContent` object door de `ResourceContent` methode van het `setDataDocument` object aan te roepen. Geef het `com.adobe.idp.Document` object door.
1. Stel het MIME-type van het XDP-bestand in dat u aan de opslagplaats wilt toevoegen door de methode van het `ResourceContent` object aan te roepen en door te geven `setMimeType` `application/vnd.adobe.xdp+xml`.
1. Voeg de inhoud van het `ResourceContent` object toe aan het `Resource` object door de methode van het `Resource` object aan te roepen `setContent` en het `ResourceContent` object door te geven.
1. Voeg een beschrijving van de bron toe door de methode van het `Resource` `setDescription` object aan te roepen en een tekenreekswaarde door te geven die een beschrijving van de bron vertegenwoordigt.
1. Voeg het formulierontwerp toe aan de gegevensopslagruimte door de methode van het `ResourceRepositoryClient` `writeResource` object aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die het pad naar de bronverzameling opgeeft die de nieuwe bron bevat
   * Het `Resource` object dat is gemaakt

**Zie ook**

[Snel starten (EJB-modus): Een bron schrijven met de Java API](/help/forms/developing/repository-service-api-quick-starts.md#quick-start-soap-mode-writing-a-resource-using-the-java-api)

[AEM-formulieren aanroepen met de Java API](invoking-aem-forms-using-java.md#invoking-aem-forms-using-the-java-api)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

## Een kortstondig proces aanroepen met de API voor aanroepen {#invoking-a-short-lived-process-using-the-invocation-api}

U kunt een kortstondig proces aanroepen met de Java Invocation-API. Wanneer u een kortstondig proces aanroept met de Inroeping-API, geeft u vereiste parameterwaarden door met een `java.util.HashMap` object. Voor elke parameter om tot de dienst over te gaan, haalt de methode van het `java.util.HashMap` `put` voorwerp aan en specificeert het naam-waarde paar dat door de dienst wordt vereist om de gespecificeerde verrichting uit te voeren. Geef de exacte naam op van de parameters die bij het kortstondige proces horen.

>[!NOTE]
>
>Voor informatie over het aanhalen van een langdurig proces, zie het [aanhalen van mens-Centric langlevende Processen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

De discussie gaat hier over het gebruik van de oproepings-API om het volgende kortstondig AEM Forms-proces met de naam `MyApplication/EncryptDocument`aan te roepen.

>[!NOTE]
>
>Dit proces is niet gebaseerd op een bestaand AEM Forms-proces. Om samen met het codevoorbeeld te volgen, creeer een proces genoemd `MyApplication/EncryptDocument` gebruikend Workbench. (Zie [Workbench](https://www.adobe.com/go/learn_aemforms_workbench_63)gebruiken.)

Wanneer dit proces wordt aangeroepen, worden de volgende handelingen uitgevoerd:

1. Hiermee verkrijgt u het onbeveiligde PDF-document dat aan het proces wordt doorgegeven. Deze handeling is gebaseerd op de `SetValue` bewerking. De invoerparameter voor dit proces is een `document` procesvariabele met de naam `inDoc`.
1. Hiermee versleutelt u het PDF-document met een wachtwoord. Deze handeling is gebaseerd op de `PasswordEncryptPDF` bewerking. Het met wachtwoord gecodeerde PDF-document wordt geretourneerd in een procesvariabele met de naam `outDoc`.

### Het kortstondige MyApplication/EncryptDocument-proces aanroepen met de Java-oproepings-API {#invoke-the-myapplication-encryptdocument-short-lived-process-using-the-java-invocation-api}

Roep het `MyApplication/EncryptDocument` kortstondige proces aan met de Java-oproepings-API:

1. Neem client-JAR-bestanden, zoals adobe-livecycle-client.jar, op in het klassenpad van uw Java-project. (Zie [Inclusief Java-bibliotheekbestanden](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)voor AEM-formulieren.)
1. Maak een `ServiceClientFactory` object dat verbindingseigenschappen bevat. (Zie Verbindingseigenschappen [instellen](invoking-aem-forms-using-java.md#setting-connection-properties).)
1. Maak een `ServiceClient` object door de constructor ervan te gebruiken en het `ServiceClientFactory` object door te geven. Met een `ServiceClient` object kunt u een servicebewerking aanroepen. Het behandelt taken zoals het lokaliseren van, het verzenden van, en het verpletteren van oproepingsverzoeken.
1. Maak een `java.util.HashMap` object met de constructor ervan.
1. Roep de `java.util.HashMap` methode van het `put` object aan voor elke invoerparameter die aan het langlevende proces wordt doorgegeven. Omdat het `MyApplication/EncryptDocument` kortstondige proces één inputparameter van type vereist `Document`, moet u de `put` methode slechts eenmaal aanhalen, zoals aangetoond in het volgende voorbeeld.

   ```as3
    //Create a Map object to store the parameter value for inDoc
    Map params = new HashMap();
    InputStream inFile = new FileInputStream("C:\\Adobe\Loan.pdf");
    Document inDoc = new Document(inFile);
    params.put("inDoc", inDoc);
   ```

1. Maak een `InvocationRequest` object door de methode van het `ServiceClientFactory` `createInvocationRequest` object aan te roepen en de volgende waarden door te geven:

   * Een tekenreekswaarde die de naam aangeeft van het proces met een lange levensduur dat moet worden aangeroepen. Om het `MyApplication/EncryptDocument` proces aan te halen, specificeer `MyApplication/EncryptDocument`.
   * Een tekenreekswaarde die staat voor de naam van de procesbewerking. De naam van een kortstondige procesbewerking is doorgaans `invoke`.
   * Het `java.util.HashMap` object dat de parameterwaarden bevat die de servicebewerking vereist.
   * Een Booleaanse waarde die opgeeft `true`, die een synchrone aanvraag maakt (deze waarde is van toepassing om een kortstondig proces aan te roepen).

1. Verzend het aanroepingsverzoek naar de service door de methode van het `ServiceClient` object aan te roepen en het `invoke` `InvocationRequest` object door te geven. De `invoke` methode retourneert een `InvocationReponse` object.

   >[!NOTE]
   >
   >Een proces van lange duur kan worden aangeroepen door de waarde `false`als vierde parameter van de `createInvocationRequest` methode door te geven. Als u de waarde doorgeeft, wordt een asynchrone aanvraag `false`*gemaakt.*

1. Haal de geretourneerde waarde van het proces op door de methode van het `InvocationReponse` `getOutputParameter` object aan te roepen en een tekenreekswaarde door te geven die de naam van de uitvoerparameter opgeeft. In deze situatie, specificeer `outDoc` ( `outDoc` is de naam van de outputparameter voor het `MyApplication/EncryptDocument` proces). Kast de terugkeerwaarde aan, `Document`zoals aangetoond in het volgende voorbeeld.

   ```as3
    InvocationResponse response = myServiceClient.invoke(request);
    Document encryptDoc = (Document) response.getOutputParameter("outDoc");
   ```

1. Maak een `java.io.File` object en zorg dat de bestandsextensie .pdf is.
1. Roep de `com.adobe.idp.Document` methode van het `copyToFile` object aan om de inhoud van het `com.adobe.idp.Document` object naar het bestand te kopiëren. Zorg ervoor dat u het `com.adobe.idp.Document` object gebruikt dat door de `getOutputParameter` methode is geretourneerd.

**Zie ook**

[Snel starten: Een kortstondig proces aanroepen met de API voor aanroepen](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-short-lived-process-using-the-invocation-api)

[Het aanhalen van mens-Centric langlevende Processen](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes)

[Inclusief Java-bibliotheekbestanden voor AEM-formulieren](invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)