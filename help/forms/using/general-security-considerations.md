---
title: Algemene beveiligingsoverwegingen voor AEM Forms on JEE
seo-title: Algemene beveiligingsoverwegingen voor AEM Forms on JEE
description: Leer hoe u zich voorbereidt op het verharden van uw AEM-formulieren in de JEE-omgeving.
seo-description: Leer hoe u zich voorbereidt op het verharden van uw AEM-formulieren in de JEE-omgeving.
uuid: 4d098731-fc8f-41d7-98b5-5c2e31211614
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: 64bc6018-2828-4634-9275-48f1d411452b
docset: aem65
translation-type: tm+mt
source-git-commit: 06335b9a85414b6b1141dd19c863dfaad0812503

---


# Algemene beveiligingsoverwegingen voor AEM Forms on JEE{#general-security-considerations-for-aem-forms-on-jee}

Dit artikel bevat inleidende informatie die u helpt bij het voorbereiden van het verharden van uw AEM Forms-omgeving. Het omvat eerste vereiste informatie over Vormen AEM op JEE, werkend systeem, toepassingsserver, en gegevensbestandveiligheid. Controleer deze gegevens voordat u uw omgeving vergrendelt.

## Specifieke beveiligingsinformatie van de leverancier {#vendor-specific-security-information}

Deze sectie bevat veiligheid-verwante informatie over werkende systemen, toepassingsservers, en gegevensbestanden die in uw Vormen AEM op oplossing JEE worden opgenomen.

Gebruik de koppelingen in deze sectie om leveranciersspecifieke beveiligingsinformatie voor uw besturingssysteem, database en toepassingsserver te zoeken.

### Beveiligingsgegevens besturingssysteem {#operating-system-security-information}

Wanneer u uw besturingssysteem beveiligt, kunt u zorgvuldig overwegen om de maatregelen te implementeren die zijn beschreven door uw leverancier van het besturingssysteem, waaronder de volgende:

* Gebruikers, rollen en bevoegdheden definiëren en beheren
* Bewaking van logboeken en audittrails
* Het verwijderen van onnodige diensten en toepassingen
* Back-ups maken van bestanden

Voor veiligheidsinformatie over werkende systemen die de Vormen van AEM op JEE steunt, zie de middelen in de lijst:

<table>
 <thead>
  <tr>
   <th><p>Besturingssysteem</p> </th>
   <th><p>Beveiligingsbron</p> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>IBM® AIX® 7.2</p> </td>
   <td><p><a href="https://www.ibm.com/support/knowledgecenter/ssw_aix_72/com.ibm.aix.security/security-kickoff.htm" target="_blank">Voordelen van IBM AIX-beveiliging</a></p> </td>
  </tr>
  <tr>
   <td><p>Microsoft Windows Server® 2016 </p> </td>
   <td><p><a href="https://cloudblogs.microsoft.com/windowsserver/2017/08/22/now-available-windows-server-2016-security-guide/">Windows Server 2016 Security Guide</a></p> </td>
  </tr>
  <tr>
   <td><p>Red Hat® Linux® AP of ES</p> </td>
   <td><p><a href="https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/pdf/security_guide/Red_Hat_Enterprise_Linux-7-Security_Guide-en-US.pdf" target="_blank">Red Hat Enterprise Linux-beveiligingsgids</a></p> </td>
  </tr>
  <tr>
   <td><p>Sun Solaris 11</p> </td>
   <td><p><a href="https://docs.oracle.com/cd/E53394_01/html/E54807/index.html" target="_blank">Richtlijnen voor beveiliging en beveiliging</a></p> </td>
  </tr>
  <tr>
   <td>Oracle Linux® 7 Update 3</td>
   <td><a href="https://docs.oracle.com/cd/E52668_01/E54670/E54670.pdf" target="_blank">Beveiligingsgids voor release 7</a><br /> </td>
  </tr>
  <tr>
   <td>CentOS 7<sup></sup></td>
   <td><a href="https://wiki.centos.org/HowTos/OS_Protection" target="_blank">Beveiligingsdocumentatie</a></td>
  </tr>
 </tbody>
</table>

### Beveiligingsgegevens toepassingsserver {#application-server-security-information}

Wanneer het beveiligen van uw toepassingsserver, denk zorgvuldig na uitvoerend de maatregelen die door uw serververkoper, met inbegrip van het volgende worden beschreven:

* Niet-duidelijke gebruikersnaam beheerder gebruiken
* Onnodige services uitschakelen
* De consolemanager beveiligen
* Beveiligde cookies inschakelen
* Onbenodigde poorten sluiten
* Het beperken van cliënten door IP adressen of domeinen
* Het gebruiken van de Manager van de Veiligheid Java™ om voorrechten programmatisch te beperken

Voor veiligheidsinformatie over toepassingsservers die de Vormen van AEM op JEE steunt, zie de middelen in deze lijst.

<table>
 <thead>
  <tr>
   <th><p>Toepassingsserver</p> </th>
   <th><p>Beveiligingsbron</p> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Oracle WebLogic®</p> </td>
   <td><p>Zoek naar Begrip van WebLogic-beveiliging op <a href="https://download.oracle.com/docs/">https://download.oracle.com/docs/</a>.</p> </td>
  </tr>
  <tr>
   <td><p>IBM WebSphere®</p> </td>
   <td><p><a href="https://www.ibm.com/developerworks/websphere/zones/was/security/" target="_blank">Toepassingen en hun omgeving beveiligen</a></p> </td>
  </tr>
  <tr>
   <td><p>Red Hat® JBoss®</p> </td>
   <td><p><a href="https://docs.jboss.org/author/display/AS7/Security+subsystem+configuration">Configuratie van het subsysteem Beveiliging</a></p> </td>
  </tr>
 </tbody>
</table>

### Beveiligingsgegevens van database {#database-security-information}

Wanneer het beveiligen van uw gegevensbestand, overweeg het uitvoeren van de maatregelen die door uw gegevensbestandverkoper, met inbegrip van het volgende worden beschreven:

* Het beperken van verrichtingen met toegangsbeheerlijsten (ACLs)
* Niet-standaardpoorten gebruiken
* De database achter een firewall plaatsen
* Versleuteling van gevoelige gegevens voordat deze naar de database worden geschreven (zie de documentatie van de fabrikant van de database)

Voor veiligheidsinformatie over gegevensbestanden die de Vormen AEM op JEE steunt, zie de middelen in deze lijst.

<table>
 <thead>
  <tr>
   <th><p>Database</p> </th>
   <th><p>Beveiligingsbron</p> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>IBM DB2® 11.1</p> </td>
   <td><p><a href="https://www-01.ibm.com/software/data/db2/library/">DB2-productfamilie</a></p> </td>
  </tr>
  <tr>
   <td><p>Microsoft SQL Server 2016</p> </td>
   <td>Zoek het Web naar "SQL Server 2016: Beveiliging"</td>
  </tr>
  <tr>
   <td><p>MySQL 5</p> </td>
   <td><p><a href="https://dev.mysql.com/doc/refman/5.0/en/security.html">MySQL 5.0 - Algemene beveiligingsproblemen</a></p> <p><a href="https://dev.mysql.com/doc/refman/5.1/en/security.html">MySQL 5.1 Algemene beveiligingsproblemen</a></p> </td>
  </tr>
  <tr>
   <td><p>Oracle® 12c</p> </td>
   <td><p>Raadpleeg het hoofdstuk Beveiliging in de documentatie bij <a href="https://docs.oracle.com/database/121/TDPSG/GUID-6E2F4E53-5D87-4FCD-9C9C-6792217D7014.htm#TDPSG94426" target="_blank">Oracle 12g</a></p> </td>
  </tr>
 </tbody>
</table>

Deze lijst beschrijft de standaardhavens die tijdens uw Vormen AEM op het configuratieproces van JEE moeten worden geopend. Als u verbinding maakt via https, past u de poortgegevens en IP-adressen dienovereenkomstig aan. Voor meer informatie over het vormen van havens, zie het *Installeren en het Opstellen van Vormen AEM op JEE* - document voor uw toepassingsserver.

<table>
 <thead>
  <tr>
   <th><p>Product of service</p> </th>
   <th><p>Poortnummer</p> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>JBoss</p> </td>
   <td><p>8080</p> </td>
  </tr>
  <tr>
   <td><p>WebLogic</p> </td>
   <td><p>7001</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>WebLogic Managed Server</p> </td>
   <td><p>Instellen door beheerder tijdens configuratie</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>WebSphere</p> </td>
   <td><p>9060, als de Globale Veiligheid wordt toegelaten is de standaardSSL havenwaarde 9043.</p> <p>9080</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>BAM-server</p> </td>
   <td><p>7001</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>SOAP</p> </td>
   <td><p>8880</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>MySQL</p> </td>
   <td><p>3306</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>Oracle</p> </td>
   <td><p>1521</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>DB2</p> </td>
   <td><p>50000</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>SQL Server</p> </td>
   <td><p>1433</p> </td>
  </tr>
  <tr>
   <td>&gt;<p>LDAP</p> </td>
   <td><p>De poort waarop de LDAP-server wordt uitgevoerd. De standaardpoort is doorgaans 389. Als u echter de SSL-optie selecteert, is de standaardpoort doorgaans 636. Bevestig met uw beheerder LDAP welke haven om te specificeren.</p> </td>
  </tr>
 </tbody>
</table>

### JBoss configureren voor het gebruik van een niet-standaard HTTP-poort {#configuring-jboss-to-use-a-non-default-http-port}

JBoss de Server van de Toepassing gebruikt 8080 als standaardhaven van HTTP. JBoss heeft ook pre-gevormde havens 8180, 8280, en 8380, die uit in het jreliëf-service.xml- dossier worden becommentarieerd. Als er een toepassing op uw computer staat die deze poort al gebruikt, wijzigt u de poort die AEM Forms op JEE gebruikt door de volgende stappen uit te voeren:

1. Open het volgende bestand om te bewerken:

   Installatie van één server: [JBoss-hoofdmap]/standalone/configuration/standalone.xml

   Clusterinstallaties: [JBoss-hoofdmap]/domain/configuration/domain.xml

1. Wijzig de waarde van het **poortkenmerk** in de **&lt;socket-binding>** -tag in een aangepast poortnummer. Het volgende gebruikt bijvoorbeeld poort 8090:

   &lt;socket-binding name=&quot;http&quot; port=&quot;8090&quot;/>

1. Sla het bestand op en sluit het.
1. Start de JBoss-toepassingsserver opnieuw.

## AEM-formulieren uit beveiligingsoverwegingen met betrekking tot JEE {#aem-forms-on-jee-security-considerations}

In deze sectie worden enkele AEM-formulieren beschreven voor JEE-specifieke beveiligingsproblemen die u bekend moeten maken.

### E-mailreferenties zijn niet gecodeerd in database {#email-credentials-not-encrypted-in-database}

De e-mailgegevens die door toepassingen worden opgeslagen, worden niet versleuteld voordat ze in de AEM Forms in de JEE-database worden opgeslagen. Wanneer u een de diensteindpunt vormt om e-mail te gebruiken, wordt om het even welke wachtwoordinformatie die als deel van die eindpuntconfiguratie wordt gebruikt niet gecodeerd wanneer het in het gegevensbestand wordt opgeslagen.

### Gevoelige inhoud voor Rights Management in de database {#sensitive-content-for-rights-management-in-the-database}

AEM Forms on JEE gebruikt de AEM Forms on JEE-database voor het opslaan van vertrouwelijke informatie over documentsleutels en ander cryptografisch materiaal dat wordt gebruikt voor beleidsdocumenten. Het beveiligen van de database tegen indringing helpt deze vertrouwelijke informatie te beschermen.

### Wachtwoord in tekstformulier wissen {#password-in-clear-text-format-in-adobe-ds-xml}

De toepassingsserver die wordt gebruikt om Vormen AEM op JEE in werking te stellen vereist zijn eigen configuratie voor toegang tot uw gegevensbestand door een gegevensbron die op de toepassingsserver wordt gevormd. Zorg ervoor dat uw toepassingsserver uw databasewachtwoord niet in duidelijke tekst in het configuratiebestand van de gegevensbron weergeeft.

Het bestand lc_[database].xml mag geen wachtwoord in duidelijke tekstindeling bevatten. Vraag de leverancier van de toepassingsserver hoe u deze wachtwoorden voor uw toepassingsserver kunt coderen.

>[!NOTE]
>
>Met het installatieprogramma van AEM Forms on JEE JBoss wordt het databasewachtwoord gecodeerd.

IBM WebSphere Application Server en Oracle WebLogic Server kunnen standaard gegevensbronwachtwoorden coderen. Bevestig echter met de documentatie van de toepassingsserver dat dit gebeurt.

### De persoonlijke sleutel die is opgeslagen in de Trust Store beveiligen {#protecting-the-private-key-stored-in-trust-store}

De persoonlijke sleutels of referenties die in de Trust Store worden geïmporteerd, worden opgeslagen in AEM Forms in de JEE-database. Neem de juiste voorzorgsmaatregelen om de database te beveiligen en beperk de toegang tot alleen de aangewezen beheerders.
