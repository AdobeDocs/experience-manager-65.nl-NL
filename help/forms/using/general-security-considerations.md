---
title: Algemene veiligheidsoverwegingen voor AEM Forms in juni
description: Leer hoe u zich voorbereidt op het verharden van uw AEM Forms in JEE-omgeving.
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
docset: aem65
role: Admin
exl-id: 3f150dd5-f486-4f16-9de9-035cde53b034
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1030'
ht-degree: 0%

---

# Algemene veiligheidsoverwegingen voor AEM Forms in juni{#general-security-considerations-for-aem-forms-on-jee}

Dit artikel bevat inleidende informatie die u helpt bij het voorbereiden op het verharden van uw AEM Forms-omgeving. Dit omvat informatie over AEM Forms op JEE, besturingssysteem, toepassingsserver en databasebeveiliging. Controleer deze gegevens voordat u uw omgeving vergrendelt.

## Specifieke beveiligingsinformatie van de leverancier {#vendor-specific-security-information}

Deze sectie bevat veiligheid-verwante informatie over werkende systemen, toepassingsservers, en gegevensbestanden die in uw AEM Forms op oplossing JEE worden opgenomen.

Gebruik de koppelingen in deze sectie om leveranciersspecifieke beveiligingsinformatie voor uw besturingssysteem, database en toepassingsserver te zoeken.

### Beveiligingsgegevens besturingssysteem {#operating-system-security-information}

Wanneer u uw besturingssysteem beveiligt, kunt u zorgvuldig overwegen om de maatregelen te implementeren die zijn beschreven door uw leverancier van het besturingssysteem, waaronder de volgende:

* Gebruikers, rollen en bevoegdheden definiëren en beheren
* Bewaking van logboeken en audittrails
* Het verwijderen van onnodige diensten en toepassingen
* Back-ups maken van bestanden

Zie de bronnen in de tabel voor beveiligingsinformatie over besturingssystemen die AEM Forms op JEE ondersteunt:

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
   <td><p><a href="https://www.ibm.com/support/knowledgecenter/ssw_aix_72/com.ibm.aix.security/security-kickoff.htm" target="_blank">IBM® AIX® Security Benefits</a></p> </td>
  </tr>
  <tr>
   <td><p>Microsoft® Windows Server® 2016 </p> </td>
   <td><p><a href="https://cloudblogs.microsoft.com/windowsserver/2017/08/22/now-available-windows-server-2016-security-guide/">Windows Server 2016 Security Guide</a></p> </td>
  </tr>
  <tr>
   <td><p>Red Hat® Linux® AP of ES</p> </td>
   <td><p><a href="https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/pdf/security_guide/Red_Hat_Enterprise_Linux-7-Security_Guide-en-US.pdf" target="_blank">Red Hat® Enterprise Linux®-beveiligingsgids</a></p> </td>
  </tr>
  <tr>
   <td><p>Sun Solaris™ 11</p> </td>
   <td><p><a href="https://docs.oracle.com/cd/E53394_01/html/E54807/index.html" target="_blank">Richtlijnen voor beveiliging en beveiliging</a></p> </td>
  </tr>
  <tr>
   <td>Oracle Linux® 7 Update 3</td>
   <td><a href="https://docs.oracle.com/en/operating-systems/oracle-linux/7/security/" target="_blank">Beveiligingsgids voor release 7</a><br /> </td>
  </tr>
  <tr>
   <td>CentOS 7<sup> </sup></td>
   <td><a href="https://wiki.centos.org/HowTos/OS_Protection" target="_blank">Beveiligingsdocumentatie</a></td>
  </tr>
 </tbody>
</table>

### Beveiligingsgegevens toepassingsserver {#application-server-security-information}

Wanneer het beveiligen van uw toepassingsserver, denk zorgvuldig na uitvoerend de maatregelen die door uw serververkoper, met inbegrip van het volgende worden beschreven:

* Gebruikend niet duidelijke beheerdergebruikersnaam
* Onnodige services uitschakelen
* De consolemanager beveiligen
* Beveiligde cookies inschakelen
* Onbenodigde poorten sluiten
* Het beperken van cliënten door IP adressen of domeinen
* Het gebruiken van de Manager van de Veiligheid Java™ om voorrechten programmatisch te beperken

Zie de bronnen in deze tabel voor beveiligingsinformatie over toepassingsservers die door AEM Forms op JEE worden ondersteund.

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
   <td><p>Zoek naar Begrip van WebLogic-beveiliging op <a href="https://docs.oracle.com/">https://docs.oracle.com/</a>.</p> </td>
  </tr>
  <tr>
   <td><p>IBM® WebSphere®</p> </td>
   <td><p><a href="https://www.ibm.com/developerworks/websphere/zones/was/security/" target="_blank">Toepassingen en hun omgeving beveiligen</a></p> </td>
  </tr>
  <tr>
   <td><p>Red Hat® JBoss®</p> </td>
   <td><p><a href="https://docs.jboss.org/author/display/AS7/Security%20subsystem%20configuration.html">Configuratie van het subsysteem Beveiliging</a></p> </td>
  </tr>
 </tbody>
</table>

### Beveiligingsgegevens van database {#database-security-information}

Wanneer het beveiligen van uw gegevensbestand, overweeg het uitvoeren van de maatregelen die door uw gegevensbestandverkoper, met inbegrip van het volgende worden beschreven:

* Het beperken van verrichtingen met toegangsbeheerlijsten (ACLs)
* Niet-standaardpoorten gebruiken
* De database achter een firewall plaatsen
* Versleuteling van gevoelige gegevens voordat deze naar de database worden geschreven (zie de documentatie van de fabrikant van de database)

Voor veiligheidsinformatie over gegevensbestanden die AEM Forms op JEE steunt, zie de middelen in deze lijst.

<table>
 <thead>
  <tr>
   <th><p>Database</p> </th>
   <th><p>Beveiligingsbron</p> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>IBM® DB2® 11.1</p> </td>
   <td><p><a href="https://www-01.ibm.com/software/data/db2/library/">DB2® Product Family Library</a></p> </td>
  </tr>
  <tr>
   <td><p>Microsoft® SQL Server 2016</p> </td>
   <td>Zoek het Web naar "SQL Server 2016: Veiligheid"</td>
  </tr>
  <tr>
   <td><p>MySQL 5</p> </td>
   <td><p><a href="https://dev.mysql.com/doc/refman/5.0/en/security.html">MySQL 5.0 - Algemene beveiligingsproblemen</a></p> <p><a href="https://dev.mysql.com/doc/refman/5.1/en/security.html">MySQL 5.1 Algemene beveiligingsproblemen</a></p> </td>
  </tr>
  <tr>
   <td><p>Oracle® 12c</p> </td>
   <td><p>Zie het hoofdstuk Beveiliging in het dialoogvenster <a href="https://docs.oracle.com/database/121/TDPSG/GUID-6E2F4E53-5D87-4FCD-9C9C-6792217D7014.htm#TDPSG94426" target="_blank">Oracle 12g-documentatie</a></p> </td>
  </tr>
 </tbody>
</table>

In deze tabel worden de standaardpoorten beschreven die moeten worden geopend tijdens het AEM Forms-configuratieproces in JEE. Als u verbinding maakt via https, past u de poortgegevens en IP-adressen dienovereenkomstig aan. Voor meer informatie over het vormen van havens, zie *AEM Forms installeren en implementeren op JEE* document voor uw toepassingsserver.

<table>
 <thead>
  <tr>
   <th><p>Product of service</p> </th>
   <th><p>Poortnummer</p> </th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>JBoss®</p> </td>
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
   <td>&gt;<p>WebSphere®</p> </td>
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
   <td>&gt;<p>DB2®</p> </td>
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

### JBoss® configureren voor het gebruik van een niet-standaard HTTP-poort {#configuring-jboss-to-use-a-non-default-http-port}

JBoss® Application Server gebruikt 8080 als de standaard HTTP-poort. JBoss® heeft ook pre-gevormde havens 8180, 8280, en 8380, die uit in het jreliëf-service.xml- dossier worden becommentarieerd. Als u een toepassing op uw computer hebt die deze poort al gebruikt, wijzigt u de poort die AEM Forms op JEE gebruikt door de volgende stappen uit te voeren:

1. Open het volgende bestand om te bewerken:

   Eén server installeren: [JBoss® root]/standalone/configuration/standalone.xml

   Clusterinstallaties: [JBoss® root]/domain/configuration/domain.xml

1. De waarde wijzigen van **poort** in het dialoogvenster **&lt;socket-binding>** -tag aan een aangepast poortnummer. Het volgende gebruikt bijvoorbeeld poort 8090:

   &lt;socket-binding name=&quot;http&quot; port=&quot;8090&quot;/>

1. Sla het bestand op en sluit het.
1. Start de JBoss®-toepassingsserver opnieuw.

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

## AEM Forms over JEE-beveiligingsoverwegingen {#aem-forms-on-jee-security-considerations}

In deze sectie worden enkele AEM Forms beschreven over JEE-specifieke beveiligingsproblemen waarvan u op de hoogte moet zijn.

### E-mailreferenties zijn niet gecodeerd in database {#email-credentials-not-encrypted-in-database}

De e-mailgegevens die door toepassingen worden opgeslagen, worden niet versleuteld voordat ze in de AEM Forms in de JEE-database worden opgeslagen. Wanneer u een de diensteindpunt vormt om e-mail te gebruiken, wordt om het even welke wachtwoordinformatie die als deel van die eindpuntconfiguratie wordt gebruikt niet gecodeerd wanneer het in het gegevensbestand wordt opgeslagen.

### Gevoelige inhoud voor Rights Management in de database {#sensitive-content-for-rights-management-in-the-database}

AEM Forms on JEE gebruikt de AEM Forms on JEE-database voor het opslaan van gevoelige informatie over de documentsleutel en ander cryptografisch materiaal dat wordt gebruikt voor beleidsdocumenten. Het beveiligen van de database tegen indringing helpt deze vertrouwelijke informatie te beschermen.

### Wachtwoord in tekstformulier wissen {#password-in-clear-text-format-in-adobe-ds-xml}

De toepassingsserver die wordt gebruikt om AEM Forms op JEE in werking te stellen vereist zijn eigen configuratie voor toegang tot uw gegevensbestand door een gegevensbron die op de toepassingsserver wordt gevormd. Zorg ervoor dat uw toepassingsserver uw databasewachtwoord niet in duidelijke tekst in het configuratiebestand van de gegevensbron weergeeft.

De lc_[database].xml-bestand mag geen wachtwoord in duidelijke-tekstindeling bevatten. Vraag de leverancier van de toepassingsserver hoe u deze wachtwoorden voor uw toepassingsserver kunt coderen.

>[!NOTE]
>
>Met het AEM Forms on JEE JBoss®-installatieprogramma wordt het databasewachtwoord gecodeerd.

IBM® WebSphere® Application Server en Oracle WebLogic Server kunnen standaard gegevensbronwachtwoorden coderen. Nochtans, zou u met uw documentatie van de toepassingsserver moeten bevestigen om ervoor te zorgen dat het gebeurt.

### De persoonlijke sleutel die is opgeslagen in de Trust Store beveiligen {#protecting-the-private-key-stored-in-trust-store}

De persoonlijke sleutels of referenties die in de Trust Store worden geïmporteerd, worden opgeslagen in AEM Forms in de JEE-database. Om het gegevensbestand te beveiligen en toegang tot aangewezen slechts beheerders te beperken, neem aangewezen voorzorgsmaatregelen.
