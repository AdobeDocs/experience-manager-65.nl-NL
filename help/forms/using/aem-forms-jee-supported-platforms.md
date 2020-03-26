---
title: Ondersteunde platforms voor AEM-formulieren op JEE
seo-title: Ondersteunde platforms voor AEM-formulieren op JEE
description: Lijst met infrastructuurcomponenten die vereist en ondersteund zijn voor de installatie van AEM Forms in JEE
seo-description: Lijst met infrastructuurcomponenten die vereist en ondersteund zijn voor de installatie van AEM Forms in JEE
uuid: 777f943b-4cb4-444e-a036-8032b9fce5be
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
geptopics: SG_AEMFORMS/categories/jee
discoiquuid: f777865e-d4a8-40ef-87b0-130c19eb1b91
docset: aem65
translation-type: tm+mt
source-git-commit: 6cf69dc86ce70a43e77b00d6b3986fa40ae0a4ec

---


# Ondersteunde platforms voor AEM-formulieren op JEE{#supported-platforms-for-aem-forms-on-jee}

## Ondersteunde platforms {#supported-platforms}

### Ondersteuningsniveaus {#support-levels}

AEM Forms on JEE Server kan worden ingesteld met elke combinatie van ondersteunde besturingssystemen, toepassingsservers, databases, databasestuurprogramma&#39;s, JDK, LDAP-servers en e-mailservers.

In dit document worden de ondersteunde client- en serverplatforms voor AEM Forms on JEE vermeld. Adobe biedt verschillende ondersteuningsniveaus, zowel voor onze aanbevolen configuraties als voor andere configuraties. In het document worden ook andere ondersteunde software en de bijbehorende versie, uitzonderingen, patchdefinities en het ondersteuningsbeleid voor softwarepatches van derden vermeld.

>[!NOTE]
>
>* Zie [Uitzonderingen op ondersteunde serverplatforms](../../forms/using/aem-forms-jee-supported-platforms.md#p-exceptions-to-supported-server-platforms-p)voor een volledige lijst met uitzonderingen op ondersteunde serverplatforms.
>* AEM Forms on JEE ondersteunt alleen Engelse, Franse, Duitse en Japanse versies van de ondersteunde besturingssystemen en toepassingen.
>



### Aanbevolen configuraties {#recommendedconfigurations}

Adobe raadt deze configuraties aan en biedt volledige of beperkte ondersteuning in het kader van de standaard overeenkomst voor softwareonderhoud:

<table>
 <tbody>
  <tr>
   <th>Ondersteuningsniveau</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>A: Ondersteund<br /> </td>
   <td>Adobe biedt volledige ondersteuning en onderhoud voor deze configuratie. Deze configuratie wordt gedekt door het kwaliteitsborgingsproces van Adobe.</td>
  </tr>
  <tr>
   <td>R: Beperkte ondersteuning</td>
   <td>Adobe biedt volledige ondersteuning voor deze configuratie als aan bepaalde voorwaarden is voldaan. Neem contact op met de ondersteuning van Adobe-bedrijven voor meer informatie over de voorwaarden en om een aanvraag voor ondersteuning in te dienen.</td>
  </tr>
  <tr>
   <td>L: Beperkte steun</td>
   <td>Adobe biedt volledige ondersteuning en onderhoud voor deze configuraties als aan bepaalde voorwaarden is voldaan. Niet zijn alle mogelijkheden beschikbaar op de configuratie. Neem contact op met de ondersteuning van Adobe-bedrijven voor meer informatie over de voorwaarden en om een aanvraag voor ondersteuning in te dienen.<br /> </td>
  </tr>
 </tbody>
</table>

### Niet-ondersteunde configuraties {#unsupported-configurations}

| Ondersteuningsniveau | Beschrijving |
|---|---|
| E: Werken verwacht | De configuratie zal naar verwachting werken en er zijn geen meldingen van het tegendeel. |
| Z: Niet ondersteund | De configuratie wordt niet ondersteund. Adobe geeft geen instructies over de werking van de configuratie en biedt geen ondersteuning voor deze configuratie. |

>[!NOTE]
>
>Om klanten van AEM Forms te helpen de kosten van eigendom verminderen, de plaatsingsarchitectuur vereenvoudigen, en de ontwikkelingsstapel moderniseren, beweegt het ondernemingsplatform van de Manager van de Ervaring van Adobe zich van op toepassingsserver-gebaseerde plaatsingen in het voordeel van standalone op OSGi-Gebaseerde plaatsingen. Adobe blijft de JEE-stapel van AEM Forms ondersteunen met een beperkte matrix van infrastructuurcomponenten.
>
>Met de release van 6.5 worden infrastructuurcomponenten die het laagste gebruik onder onze klanten hebben, niet meer ondersteund, zoals hieronder:
>・ Oracle WebLogic-toepassingsserver
>IBM DB2-database
>・ IBM AIX en Sun Solaris besturingssystemen
>
>Voor nieuwe installaties, waar mogelijk, wordt geadviseerd om Vormen AEM op de moderne OSGi stapel op te stellen om de recentste innovaties rond ontvankelijke Adaptieve Vormen voor mobiele, multi-kanaals Interactieve Mededelingen, en backendgegevensintegratie te gebruiken het Model van de Gegevens van de Vorm.
>
>We erkennen dat bestaande gebruikers AEM Forms moeten blijven implementeren in een JEE-stapel. In dergelijke scenario&#39;s vereist Adobe de implementatie van AEM Forms JEE op ondersteunde infrastructuur, zoals in deze documentatie wordt beschreven. Als u een upgrade uitvoert naar AEM 6.5 Forms en een niet-ondersteund platform gebruikt in de vorige versie van AEM Forms, kunt u contact opnemen met de Technische Ondersteuning van Adobe voor hulp bij de upgrade naar een ondersteund platform.

### Java Virtual Machines (JVM) {#java-virtual-machines-jvm}

Voor Adobe Experience Manager Forms is een Java Virtual Machine vereist die wordt geleverd door de JDK-distributie (Java Development Kit). Adobe Experience Manager werkt met de volgende versies van de Java Virtual Machines:

<table>
 <tbody>
  <tr>
   <th><p><strong>Platform</strong></p> </th>
   <th><p><strong>Ondersteuningsniveau</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td><p>Oracle Java™ SE 11 (64-bits)</p> </td>
   <td><p>Z: Niet ondersteund</p> </td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td>Oracle Java™ SE 8 (64-bits)</td>
   <td>A: Ondersteund</td>
   <td>Kleine releases en updates</td>
  </tr>
  <tr>
   <td>IBM® J9 Virtual Machine (build 2.8, JRE 1.8.0)</td>
   <td>A: Ondersteund</td>
   <td>Kleine releases en updates</td>
  </tr>
  <tr>
   <td>IBM® J9 Virtual Machine (build 2.9, JRE 1.8.0)<br /> </td>
   <td>A: Ondersteund</td>
   <td>Kleine releases en updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* AEM Forms on JEE ondersteunt alleen 64-bits JVM&#39;s in productieomgevingen.
>* Het wordt aanbevolen de beveiligingsbulletins van de Java-leverancier bij te houden om de veiligheid en beveiliging van productieomgevingen te garanderen en de nieuwste Java-updates te installeren.
>



### Databases en CRX-persistentie {#databases-and-crx-persistence}

<table>
 <tbody>
  <tr>
   <td><p><strong>Platform</strong></p> </td>
   <td><p><strong> Beschrijving</strong></p> </td>
   <td><p><strong>Ondersteuningsniveau</strong></p> </td>
  </tr>
  <tr>
   <td><p>Bestandssysteem</p> </td>
   <td><p>Repository Microkernel (TAR MK-bestanden)</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
  <tr>
   <td><p>MongoDB Enterprise 4.0 </p> </td>
   <td><p>Repository Microkernel</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
  <tr>
   <td><p>Oracle Database 12c Release 1</p> </td>
   <td><p>Repository Microkernel</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
  <tr>
   <td>Oracle Database 18c </td>
   <td>Repository Microkernel</td>
   <td>Ondersteund</td>
  </tr>

<tr>
   <td>Oracle Database 19c </td>
   <td>Bewaarplaats</td>
   <td>Ondersteund</td>
  </tr>
  <tr>
   <td><p>Microsoft SQL Server 2016</p> </td>
   <td><p>Repository Microkernel</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
  <tr>
   <td>IBM DB2 11.1</td>
   <td>Repository Microkernel</td>
   <td>R: Beperkte ondersteuning</td>
  </tr>
    <tr>
   <td>MySQL 5.7.19 </td>
   <td>-</td>
   <td>R: Beperkte ondersteuning</td>
  </tr>
 </tbody>
</table>

* IBM DB2 wordt niet ondersteund voor nieuwe installaties. Deze functie wordt alleen ondersteund voor bestaande klanten die upgraden naar AEM 6.5 Forms.
* MongoDB is software van derden en is niet opgenomen in het AEM-licentiepakket. Zie de pagina [MongoDB-licentiebeleid](https://www.mongodb.org/about/licensing/) voor meer informatie.
* Adobe raadt u aan een licentie voor de MongoDB Enterprise-versie aan te schaffen om optimaal gebruik te kunnen maken van uw AEM-implementatie.
* De klantenservice van Adobe helpt in aanmerking komende problemen met betrekking tot het gebruik van MongoDB met AEM. Zie de pagina [](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager)MongoDB voor Adobe Experience Manager voor meer informatie.
* &#39;Bestandssysteem&#39; omvat blokopslag die compatibel is met POSIX. Dit omvat netwerkopslagtechnologie. Houd er rekening mee dat de prestaties van het bestandssysteem kunnen variëren en van invloed zijn op de algehele prestaties. Het wordt aanbevolen AEM-test te laden in combinatie met het netwerk/externe bestandssysteem.
* Alleen MongoDB Storage Engine WiredTiger wordt ondersteund.
* Delen via MongoDB wordt niet ondersteund in AEM.
* AEM Forms on JEE biedt geen ondersteuning voor MySQL voor RDBMK-persistentie.
* De module Documentbeveiliging maakt geen gebruik van de gegevensopslagruimte. Dit houdt in dat als u alleen Documentbeveiliging gebruikt en geen gebruik wilt maken van HTML Workspace, HTML5-formulieren of adaptieve formulieren, u geen opslagplaats voor inhoud hoeft te installeren.
* AEM Forms on JEE biedt geen ondersteuning voor het gebruik van MySQL voor het permanent opslaan van AEM Repository (CRX-Repository).


### Databasestuurprogramma&#39;s {#database-drivers}

<table>
 <tbody>
  <tr>
   <th>Database </th>
   <th><p><strong>Platform</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td>MySQL</td>
   <td><p>MySQL Connector/J 5.7</p> <p>mysql-connector-java-5.1.44-bin.jar(versie 5.1.44)</p> </td>
   <td><p>Wordt geleverd bij AEM Forms op JEE-installatie</p> </td>
  </tr>
  <tr>
   <td>Microsoft SQL Server<br /> </td>
   <td><p>Microsoft® SQL Server JDBC-stuurprogramma 6.2.1.0<br /> </p> <p>sqljdbc6.jar</p> </td>
   <td><p>Wordt geleverd bij AEM Forms op JEE-installatie.</p> </td>
  </tr>
  <tr>
   <td>Oracle</td>
   <td><p>Oracle Database 19.3.0.0.0 JDBC-stuurprogramma</p> <p>ojdbc8.jar (versie 19.3.0.0.0)<br /> </p> </td>
   <td><p>Downloaden vanaf <a href="https://www.oracle.com/technetwork/database/features/jdbc/jdbc-ucp-122-3110062.html">Oracle-website</a>.</p> </td>
  </tr>
 </tbody>
</table>

### Toepassingsservers {#application-servers}

<table>
 <tbody>
  <tr>
   <td><p><strong> Platform</strong></p> </td>
   <td><p><strong>Ondersteuningsniveau</strong></p> </td>
   <td><p><strong>Ondersteunde patchdefinities</strong></p> </td>
  </tr>
  <tr>
   <td>IBM® WebSphere® Application Server 9.0 <sup>[1] [4]</sup><br /> </td>
   <td>A: Ondersteund</td>
   <td>Servicepack en kritieke updates</td>
  </tr>
  <tr>
   <td><p>JBoss® Enterprise Application Platform (EAP) 7.1.4 <sup>[2] [3] [7]</sup></p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Patches en cumulatieve patches voor de ondersteunde EAP-versie</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>IBM® WebSphere®-clusters worden alleen ondersteund in Network Deployment-edities.

### Serverbesturingssystemen {#server-operating-systems}

#### Productieomgevingen {#production-environments}

<table>
 <tbody>
  <tr>
   <th><p><strong> Platform</strong></p> </th>
   <th><p><strong>Ondersteuningsniveau</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td>Microsoft Windows Server 2016 (64-bits)</td>
   <td>A: Ondersteund</td>
   <td>Servicepacks en kritieke updates</td>
  </tr>
  <tr>
   <td><p>Red Hat Enterprise Linux 7 (Kernel 3.x) (64-bits)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Kleine releases, cumulatieve updates en kritieke updates</p> </td>
  </tr>
  <tr>
   <td><p>SUSE® Linux® Enterprise Server 12 (64-bits)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Servicepacks, cumulatieve patches en kritieke beveiligingsupdates</p> </td>
  </tr>
  <tr>
   <td>Oracle Linux® 7 Update 3 (64-bits)</td>
   <td>A: Ondersteund</td>
   <td>Servicepacks, cumulatieve patches en kritieke beveiligingsupdates</td>
  </tr>
  <tr>
   <td>CentOS 7 (64-bits)<sup> [6]</sup></td>
   <td>A: Ondersteund</td>
   <td>Servicepacks, cumulatieve patches en kritieke beveiligingsupdates</td>
  </tr>
 </tbody>
</table>

#### Gevirtualiseerde omgeving {#virtualized-environment}

U kunt AEM Forms op JEE op een fysieke machine of een virtuele omgeving in werking stellen. Als u echter een probleem tegenkomt met AEM Forms in een virtuele omgeving, probeert u het probleem te repliceren op een fysieke computer. Neem contact op met de Technische Ondersteuning van Adobe voor een oplossing als het probleem zich blijft voordoen op de fysieke computer. Neem contact op met de leverancier van de virtuele omgeving voor de problemen die u niet op een fysieke computer kunt repliceren.

#### Ontwikkelomgevingen {#development-environments}

<table>
 <tbody>
  <tr>
   <th><p><strong>Platform (basisversie)</strong></p> </th>
   <th>Ondersteuningsniveau</th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td><p>Microsoft® Windows® 10 64-bits</p> </td>
   <td>E: Werken verwacht</td>
   <td><p>Servicepack en kritieke updates</p> </td>
  </tr>
 </tbody>
</table>

### Uitzonderingen op ondersteunde serverplatforms {#exceptions-to-supported-server-platforms}

Houd rekening met de volgende uitzonderingen wanneer u een platform kiest voor het instellen van uw AEM-formulieren op de JEE-server.

1. AEM Forms on JEE biedt geen ondersteuning voor IBM® WebSphere® met MySQL.
1. AEM Forms on JEE biedt geen ondersteuning voor JBoss op SUSE Linux Enterprise Server 12. Alleen IBM WebSphere wordt ondersteund op SUSE Linux Enterprise Server 12.
1. AEM Forms on JEE biedt geen ondersteuning voor JDK met JBoss® anders dan Oracle Java™ SE.
1. AEM Forms on JEE biedt geen ondersteuning voor andere JDK&#39;s met IBM® WebSphere® dan IBM® JDK.
1. CRX-opslagplaats steunt persistentie van type TarMK, MongoDB, en relationele gegevensbestanden (RDBMK). U kunt geen twee verschillende gegevensbestandsystemen tussen de toepassingsserver en CRX-bewaarplaats hebben. Op een AEM Forms on JEE-omgeving kunt u echter MongoMK gebruiken met CRX-gegevensopslagruimte en een ondersteunde relationele database met toepassingsserver.
1. AEM Forms on JEE biedt geen ondersteuning voor WebSphere-toepassingsserver op CentOS.
1. AEM Forms on JEE biedt geen ondersteuning voor op JBoss gebaseerde toegangsbeheer (RBAC).

Houd rekening met de volgende punten wanneer u software voor Adobe AEM Forms kiest voor JEE-implementaties:

* AEM Forms on JEE ondersteunt updates, patches en repareert pakketten boven op de opgegeven primaire en secundaire versie van ondersteunde software. Bijwerken naar de volgende hoofd- of subversie wordt echter alleen ondersteund als dit is opgegeven.
* Clustergebaseerde installaties ondersteunen TarMK-persistentie niet. Zie Een persistentietype [kiezen voor een AEM Forms-installatie](/help/forms/using/choosing-persistence-type-for-aem-forms.md)voor meer informatie over ondersteunde persistentie.
* AEM Forms on JEE biedt ondersteuning voor diverse software van derden volgens ons beleid voor softwareondersteuning van [derden](../../forms/using/aem-forms-jee-supported-platforms.md#p-third-party-patch-support-policy-p).
* AEM Forms on JEE ondersteunt platforms op basis van de ondersteuning van externe leveranciers. Sommige combinaties zijn mogelijk niet toegestaan door externe leveranciers. Veel leveranciers hebben hun toepassingsservers bijvoorbeeld niet gecertificeerd met Oracle. Hierdoor worden deze combinaties ook niet ondersteund door AEM Forms on JEE. Om ervoor te zorgen dat u de gesteunde softwareversies kiest, controleer de steunmatrijs ook voor de derdeverkopers.
* AEM Forms on JEE biedt geen ondersteuning voor TarMK Cold Standby.
* AEM Forms on JEE biedt geen ondersteuning voor verticale clustering.
* AEM Forms on JEE biedt geen ondersteuning voor MySQL-database in een geclusterde omgeving.
* Zie [AEM 6.5 Forms New Feature Summary](../../forms/using/whats-new.md) -document voor een lijst met verwijderde of bijgewerkte platforms.

### LDAP-servers (optioneel) {#ldap-servers-optional}

<table>
 <tbody>
  <tr>
   <th><p><strong>Product (basisversie)</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td>Oracle Unified Directory (OUD) 11g Release 2</td>
   <td>Servicepakketten</td>
  </tr>
  <tr>
   <td>Microsoft Active Directory 2016</td>
   <td>Onderhoudsrelease en -reparatiepakketten</td>
  </tr>
  <tr>
   <td><p>IBM® Tivoli Directory Server 6.4</p> </td>
   <td><p>Functiepakketten en tussentijdse correcties</p> </td>
  </tr>
 </tbody>
</table>

### E-mailservers (optioneel) {#email-servers-optional}

| Product |
|---|
| IBM Lotus Domino 9.0 |
| Microsoft Exchange 2013 |
| Microsoft Office 365 |

### Inhoudsmanagers en bijbehorende connectors {#content-managers-and-corresponding-connectors}

<table>
 <tbody>
  <tr>
   <td><strong>Product<br /> </strong></td>
   <td><strong>Versie</strong></td>
  </tr>
  <tr>
   <td>EMC Documentum</td>
   <td>7.3</td>
  </tr>
  <tr>
   <td>IBM-filter</td>
   <td>5.2</td>
  </tr>
  <tr>
   <td>IBM Content Manager Server</td>
   <td>8.5 Fix pack 2</td>
  </tr>
  <tr>
   <td>IBM Content Manager-client</td>
   <td>8.5 </td>
  </tr>
  <tr>
   <td>Microsoft Sharepoint</td>
   <td>2016<br /> </td>
  </tr>
 </tbody>
</table>

### Steun voor Cordova {#support-for-cordova}

AEM Forms App ondersteunt nu Apache Cordova. Hier volgen de platformspecifieke versies van Cordova die worden ondersteund:

* Apache Cordova 6.4.0
* Cordova iOS 4.3.0
* Cordova Android 6.0.0
* Cordova Windows 4.4.3

### Softwareondersteuning voor PDF Generator {#software-support-for-pdf-generator}

<table>
 <tbody>
  <tr>
   <th><p><strong>Product</strong></p> </th>
   <th><p><strong>Ondersteunde indelingen voor conversie naar PDF</strong></p> </th>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017 klassiek nummer</a> nieuwste versie</td>
   <td>XPS, afbeeldingsindelingen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF en DWF</td>
  </tr>
  <tr>
   <td>Microsoft® Office 2016</td>
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF en TXT</td>
  </tr>
  <tr>
   <td>WordPerfect X7</td>
   <td>WP, WPD</td>
  </tr>
  <tr>
   <td>Microsoft® Office Visio 2016<br /> </td>
   <td>VSD, VSDX</td>
  </tr>
  <tr>
   <td>Microsoft® Publisher 2016<br /> </td>
   <td>PUB</td>
  </tr>
  <tr>
   <td>Microsoft® Project 2016<br /> </td>
   <td>MPP</td>
  </tr>
  <tr>
   <td>OpenOffice 4.1.2</td>
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXC, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, afbeeldingsindelingen (BMP, GIF, JPEG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, RTF en TXT</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>PDF Generator ondersteunt alleen Engelse, Franse, Duitse en Japanse versies van de ondersteunde besturingssystemen en toepassingen.
>
>Daarnaast:
>
>* PDF Generator vereist de 32-bits versie van [Acrobat 2017 klassieke trackversie 17.011.30078 of hoger](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) om de conversie uit te voeren.
>* PDF Generator ondersteunt alleen de 32-bits Retail-versie van Microsoft Office Professional Plus en andere software die vereist is voor conversie.
>* PDF Generator ondersteunt Microsoft Office 365 niet.
>* Conversies van PDF-generator voor OpenOffice worden alleen ondersteund in Windows en Linux.
>* De functies OCR PDF, PDF optimaliseren en PDF exporteren worden alleen ondersteund in Windows.
>* Een versie van Acrobat wordt meegeleverd met AEM Forms om PDF Generator-functionaliteit in te schakelen. De gebundelde versie is alleen via programmacode toegankelijk met AEM Forms tijdens de periode van de AEM Forms-licentie voor gebruik met AEM Forms PDF Generator. Raadpleeg voor meer informatie de productbeschrijving van AEM Forms volgens uw implementatie ([On-Premise](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) of [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html)).&quot;
   >
   >
* De service PDF Generator biedt geen ondersteuning voor Microsoft Windows 10.
>



### Uitzonderingen op toegankelijkheidsondersteuning {#exceptions-to-accessibility-support}

De volgende subsystemen van AEM Forms zijn niet [508](https://www.section508.gov/) -compatibel:

* Gebruikersinterface Adaptive Forms Authoring
* Gebruikersinterface voor formulierbeheer
* Gebruikersinterface Correspondentenbeheer
* Admin UI (interface beheerconsole)

## Systeemvereisten voor AEM-formulieren in JEE {#system-requirements-for-aem-forms-on-jee}

### Minimale hardwarevereisten {#minimum-hardware-requirements}

<table>
 <tbody>
  <tr>
   <td>Platform</td>
   <td>Minimale hardwarevereisten</td>
  </tr>
  <tr>
   <td>Microsoft Windows Server</td>
   <td>Intel® Xeon® E5-2680, 2,4 GHz processor of vergelijkbare<br /> VMWare ESX 5.1 of hoger<br /> RAM: 6 GB (64-bits besturingssysteem met 64-bits JVM)<br /> vrije schijfruimte: 15 GB tijdelijke ruimte plus 22 GB<br /> voor AEM-formulieren in JEE</td>
  </tr>
  <tr>
   <td>SUSE Linux Enterprise Server</td>
   <td>Intel Xeon E5-2670v2, 1 vCPU, 2,5 GHz processor<br /> AWS m3.medium (3 Ecu's)<br /> RAM: 6 GB (64-bits besturingssysteem met 64-bits JVM)<br /> vrije schijfruimte: 6 GB tijdelijke ruimte plus 22 GB<br /> voor AEM-formulieren in JEE</td>
  </tr>
  <tr>
   <td>Red Hat Enterprise Linux</td>
   <td>Intel Xeon E5-2670v2, 1 vCPU, 2,5 GHz processor<br /> AWS m3.medium (3 Ecu's)<br /> RAM: 6 GB (64-bits besturingssysteem met 64-bits JVM)<br /> vrije schijfruimte: 6 GB tijdelijke ruimte plus 22 GB<br /> voor AEM-formulieren in JEE<br /> </td>
  </tr>
  <tr>
   <td>Hardwarevereisten voor een kleine productieomgeving</td>
   <td>
    <ul>
     <li><strong>Intel-omgeving</strong>: Intel® Xeon® E5-2680, 2,4 GHz of hoger. Het gebruik van een dual core processor zal de prestaties verder verbeteren</li>
     <li><strong>Geheugen: </strong>4 GB <br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Zie voor aanvullende vereisten:

* [Systeemvereisten voor AEM Forms van één server bij JEE-implementatie](https://www.adobe.com/go/learn_aemforms_sysreq_single_63)
* [Systeemvereisten voor geclusterde AEM-formulieren bij JEE-implementatie
   ](https://www.adobe.com/go/learn_aemforms_sysreq_cluster_63)

## Ondersteunde clients voor AEM Forms on JEE {#supported-clients-for-aem-forms-on-jee}

### Workbench {#workbench}

<table>
 <tbody>
  <tr>
   <th><p><strong>Platform</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td><p>Microsoft® Windows® 10 (Enterprise, Pro, Basic)</p> <p>32-bits of 64-bits versie</p> <p> </p> </td>
   <td>Servicepacks en kritieke updates</td>
  </tr>
  <tr>
   <td>Microsoft® Windows® 2016 Server</td>
   <td>Servicepacks en kritieke updates</td>
  </tr>
 </tbody>
</table>

* Schijfruimte voor installatie: 1,7 GB alleen voor Workbench, 2,7 GB op één schijf voor een volledige installatie van Workbench, Designer en de samplingverzameling 400 MB voor tijdelijke installatiemappen - 200 MB in de map met gebruikerstempels en 200 MB in de tijdelijke map van Windows. Als al deze locaties zich op één station bevinden, moet er tijdens de installatie 1,5 GB aan ruimte beschikbaar zijn. De naar de tijdelijke mappen gekopieerde bestanden worden verwijderd wanneer de installatie is voltooid.

* Geheugen voor het uitvoeren van Workbench: 2 GB RAM
* Hardwarevereisten: Intel® Pentium® 4 of AMD equivalent, 1 GHz processor
* Minimale monitorresolutie van 1024 x 768 pixels of hoger met 16-bits kleur of hoger
* TCP/IPv4- of TCP/IPv6-netwerkverbinding met AEM Forms on JEE-server
* U moet over beheerdersrechten beschikken om Workbench in Windows te installeren. Als u een niet-beheerdersaccount gebruikt, wordt u door het installatieprogramma gevraagd om de referenties voor een geschikte account.

### Designer {#designer}

**Opmerking:** Als u Designer in Windows wilt installeren, voert u het installatieprogramma uit met beheerdersrechten.

* Microsoft® Windows® 2016 Server, Microsoft Windows 10

   * Processor van 1 GHz of sneller met ondersteuning voor PAE, NX en SSE2.
   * 1 GB RAM voor 32-bits of 2 GB RAM voor 64-bits besturingssysteem
   * 16 GB schijfruimte voor 32-bits of 20 GB schijfruimte voor 64-bits besturingssysteem

* Grafisch geheugen - 128 MB GPU (256 MB aanbevolen)
* 2,35 GB beschikbare ruimte op de vaste schijf
* Dvd-rom-station
* Internet Explorer 10 of 11; Firefox 45.x
* Monitorresolutie van 1024 x 768 pixels of hoger
* Hardwareversnelling voor video (optioneel)
* Acrobat Pro DC, Acrobat Standard DC of Adobe Acrobat Reader DC.

### Adobe Acrobat en Adobe Reader {#adobe-acrobat-and-adobe-reader}

<table>
 <tbody>
  <tr>
   <th><p><strong>Acrobat en Adobe Reader (basis)</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td>Acrobat 2017 (klassieke track)</td>
   <td>Versie 17.011.30078 of hoger<br /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>De productfamilie van Acrobat DC introduceert twee tracks voor zowel Acrobat als Reader die in wezen verschillende producten zijn: &quot;Klassiek&quot; en &quot;Doorlopend&quot;. Zie [https://www.adobe.com/go/acrobatdctracks voor meer informatie en een vergelijking van de twee tracks.](https://www.adobe.com/go/acrobatdctracks)

### Browsers {#browsers}

#### Desktops {#desktops}

<table>
 <tbody>
  <tr>
   <th><p><strong>Browser (basis)</strong></p> </th>
   <th><p><strong>Ondersteuningsniveau</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td><p>Microsoft Edge (Evergreen)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Servicepacks en -updates</p> </td>
  </tr>
  <tr>
   <td><p>Mozilla Firefox (Evergreen)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td>Alle updates</td>
  </tr>
  <tr>
   <td>Microsoft Firefox ESR</td>
   <td>E: Werken verwacht</td>
   <td> Alle updates</td>
  </tr>
  <tr>
   <td><p>Google Chrome (Evergreen)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td>Alle updates</td>
  </tr>
  <tr>
   <td>Google Chrome en Firefox op MAC OS X</td>
   <td>A: Ondersteund<br /><br /> </td>
   <td>Alle updates</td>
  </tr>
  <tr>
   <td>Apple Safari 11.x</td>
   <td>A: Ondersteund</td>
   <td>Alle updates</td>
  </tr>
  <tr>
   <td>Apple Safari 12.x<br /><br /> </td>
   <td>A: Ondersteund</td>
   <td>Alle updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Bepaalde browsergerelateerde uitzonderingen voor desktops zijn als volgt:
>
>* De meeste moderne browsers bieden geen ondersteuning meer voor op NPAPI gebaseerde plug-ins. Zie [Stoppen met NPAPI-browserplug-ins en het effect](https://helpx.adobe.com/aem-forms/kb/discontinuation-of-npapi-plugins-impact-on-aem-forms.html)ervan voor informatie over de invloed van de functie op toepassingen en workflows van AEM Forms.
>* Safari wordt alleen ondersteund op Macintosh OS X.
>* De werkruimte biedt ondersteuning voor Safari 5.1 op Macintosh OS X 10.6 en 10.7 met Acrobat DC of hoger. Ga voor meer informatie over de compatibiliteit met Safari 5.1 en Adobe Reader, Acrobat, naar [https://helpx.adobe.com/x-productkb/multi/safari-5-1-incompatible-reader.html](https://helpx.adobe.com/x-productkb/multi/safari-5-1-incompatible-reader.html).
>* Beheerconsole wordt niet ondersteund in Safari.
>* Correspondence Management biedt geen ondersteuning voor Windows® Internet Explorer 9.0 voor AEM 6.1-formulieren.
>* Forms Portal ondersteunt JAWS 14.0-schermlezersoftware in Internet Explorer 11 voor toegankelijkheid.
>



#### Mobiele clients {#mobile-clients}

<table>
 <tbody>
  <tr>
   <th><p><strong>Browser (basis)</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td><p>Chrome op Android™ 4.1.2 en hoger</p> </td>
   <td><p>Alle updates</p> </td>
  </tr>
  <tr>
   <td>Safari op iOS 11.0 en hoger</td>
   <td>Alle updates</td>
  </tr>
  <tr>
   <td>Microsoft Edge<br /> </td>
   <td>Alle updates<br /> </td>
  </tr>
  <tr>
   <td>Systeemeigen Android-browser op Android™ 4.4 en hoger</td>
   <td>Alle updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Forms Portal wordt alleen ondersteund op Safari op iPad.
>



### AEM Forms-app {#aem-forms-workspace-app}

#### Ondersteuning voor mobiele apparaten {#mobile-device-support}

De app AEM Forms is beschikbaar op de volgende platforms:

| **Platform** | **Ondersteunde apparaten** |
|---|---|
| Apple iOS | Apple iPhone, iPad, iPad Air en iPad mini met iOS 11 en hoger. |
| Google Android | Android 5.1 en hoger. De app AEM Forms is gecertificeerd op Samsung Galaxy-tablets van 7 en 10 inch en populaire smartphones. |
| Microsoft Windows | Microsoft Surface-apparaten, -tablets, -laptops en -desktops waarop het Microsoft Windows 10-besturingssysteem wordt uitgevoerd. |

### Adobe Flash Player {#adobe-flash-player}

<table>
 <tbody>
  <tr>
   <th><p><strong>Flash Player (basis)</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td><p>Nieuwste versie van Flash Player</p> </td>
   <td><p>Kleine versies en updates</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Het bijwerken en verspreiden van Flash Player [wordt door Adobe eind 2020 stopgezet](https://theblog.adobe.com/adobe-flash-update/).

### Adobe Document Security Extension voor Microsoft Office {#adobe-rights-management-extension-for-microsoft-office}

Klik [hier](https://www.adobe.com/products/livecycle/rightsmanagement/extension/downloads.html) om de systeemvereisten voor Adobe Document Security Extension voor Microsoft® Office te bekijken.

### Uitzonderingen op clientondersteuning {#exceptions-to-client-support}

AEM Forms on JEE ondersteunt updates, patches en repareert pakketten boven op de opgegeven primaire en secundaire versie van ondersteunde software. Bijwerken naar de volgende hoofd- of subversie wordt echter alleen ondersteund als dit is opgegeven.

## Flardondersteuningsbeleid van derden {#third-party-patch-support-policy}

De softwarevereisten van derden voor AEM Forms on JEE worden beschreven in de sectie &quot;Systeemvereisten&quot; van hun respectieve productdocumenten. Alle documentatie is toegankelijk via [https://adobe.com/go/learn_aemforms_documentation_65](https://adobe.com/go/learn_aemforms_documentation_65) .

AEM-formulieren op de referentieplatforms van derden van JEE vermelden het specifieke patchniveau van de infrastructuur van derden dat actief was tijdens de ontwikkeling en release van AEM Forms on JEE en van het minimale patchniveau/servicepack van de infrastructuur die door die versie van AEM Forms op JEE wordt ondersteund.

Adobe biedt bij de release ondersteuning voor urgente of aanbevolen patches die door externe leveranciers worden uitgegeven, ervan uitgaande dat externe leveranciers achterwaartse compatibiliteit met de versies garanderen die door AEM Forms op JEE worden ondersteund. Adobe biedt alleen ondersteuning voor patches die worden uitgebracht nadat het minimale patchniveau is opgegeven in de AEM Forms on JEE-documentatie.

In sommige gevallen biedt Adobe geen ondersteuning voor updates van derden die belangrijke functionaliteit wijzigen en biedt het dus geen ondersteuning voor volledige achterwaartse compatibiliteit. Zie [Ondersteunde patchdefinities](https://helpx.adobe.com/aem-forms/aem-forms-third-party-software-patch.html) voor specifieke producten van leveranciers en de patchtypen die door Adobe worden ondersteund voor meer informatie over de ondersteunde updates.

Onder omstandigheden waarover Adobe geen controle heeft, kunnen patches van derden die compatibiliteit met oudere versies claimen, negatieve gevolgen hebben voor de Adobe-producten of de omgeving van klanten. In dergelijke gevallen raadt Adobe klanten aan de gevolgen van een patch van een derde te beoordelen voordat ze deze op kritieke systemen toepassen. Adobe zal met derden samenwerken en daarbij redelijke zakelijke inspanningen leveren om dergelijke problemen op te lossen, door middel van normale Adobe-ondersteuningsprogramma&#39;s of door derden die het probleem in hun patch corrigeren. Dit garandeert niet dat een nieuw uitgebracht patch van derden die door Adobe wordt ondersteund, werkt zoals wordt beschreven door de leverancier of met AEM Forms on JEE.

Adobe behoudt zich het recht voor om de referentieplatforms van derden die worden ondersteund door een AEM Forms on JEE-release en de ondersteunde patchdefinities op een bepaald punt te wijzigen.

Aanvullende informatie voor patches van derden vindt u ook op de Adobe Enterprise Support-site op de website met knowledgebase-artikelen die betrekking hebben op uw product.

[Contact opnemen met ondersteuning](https://www.adobe.com/account/sign-in.supportportal.html)
