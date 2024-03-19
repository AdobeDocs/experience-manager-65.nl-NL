---
title: Ondersteunde platforms voor AEM Forms op JEE
description: Lijst met infrastructuurcomponenten die vereist en ondersteund zijn voor installatie van AEM Forms op JEE
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin
exl-id: 74d22cf4-56b2-48f5-92d9-928eaa134866
source-git-commit: 7f150219bce3036c0e330b7349e679fdf19797d1
workflow-type: tm+mt
source-wordcount: '4011'
ht-degree: 0%

---


# Ondersteunde platforms voor AEM Forms op JEE {#supported-platforms-for-aem-forms-on-jee}

## Ondersteunde platforms {#supported-platforms}

<div class="preview">

Adobe heeft een [volledig installatieprogramma](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) met AEM 6.5 Forms Service Pack 18 (6.5.18.0) op JEE samen met de patchinstallatieprogramma&#39;s. Het volledige installatieprogramma ondersteunt nieuwe platforms, terwijl het installatieprogramma van de patch alleen foutoplossingen bevat.
Als u een nieuwe installatie uitvoert of van plan bent de nieuwste software te gebruiken voor uw AEM 6.5 Forms in JEE-omgeving, raadt de Adobe u aan [AEM 6.5.18.0 Forms op volledig installatieprogramma JEE](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) vrijgegeven op 31 augustus 2023 in plaats van AEM 6.5 Forms installer uitgebracht op 08 april 2019 of AEM 6.5.12 Forms Installer uitgebracht op 03 maart 2022.

</div>

### Ondersteuningsniveaus {#support-levels}

AEM Forms on JEE-server kan worden ingesteld met elke combinatie van ondersteunde besturingssystemen, toepassingsservers, databases, databasestuurprogramma&#39;s, JDK, LDAP-servers en e-mailservers.

In dit document worden de ondersteunde client- en serverplatforms voor AEM Forms op JEE vermeld. Adobe biedt verschillende supportniveaus, zowel voor Adobe aanbevolen configuraties als voor andere configuraties. In het document worden ook andere ondersteunde software en de bijbehorende versie, uitzonderingen, patchdefinities en het ondersteuningsbeleid voor softwarepatches van derden vermeld.

>[!NOTE]
>
>- Voor een volledige lijst met uitzonderingen op ondersteunde serverplatforms raadpleegt u [Uitzonderingen op ondersteunde serverplatforms](../../forms/using/aem-forms-jee-supported-platforms.md#p-exceptions-to-supported-server-platforms-p).
>- AEM Forms on JEE biedt alleen ondersteuning voor Engelse, Franse, Duitse en Japanse versies van de ondersteunde besturingssystemen en toepassingen.

### Beleid voor upgrades en ondersteuning

#### Volledig installatieprogramma

- **Upgrade-ondersteuning voor volledige installatieprogramma&#39;s**: Een volledig installatieprogramma wordt vrijgegeven met elke zesde Versie van AEM Service Pack. Er is bijvoorbeeld een volledig installatieprogramma uitgebracht met 6.5.12.0 en 6.5.18.0 SP-releases. AEM Forms staat rechtstreekse upgrades uitsluitend toe vanaf de laatste twee volledige installatieprogramma&#39;s. AEM Forms maakt bijvoorbeeld alleen directe upgrades naar versie 6.5.18.0 mogelijk vanaf de laatste twee volledige installatieprogramma&#39;s, namelijk 6.5.12.0 en 6.5.6.0. Als u van een vroegere verbetering moet bevorderen, kunt u een multi-hop verbetering gebruiken om eerst naar een gesteunde volledige installateursversie en dan aan de recentste versie te gaan.

- **Verdringing en verwijdering**: De platformondersteuning wordt bijgewerkt met elke volledige installerrelease. Alle software die tijdens een volledige installateursrelease in de platformmatrix is afgekeurd, mag in een volgende volledige installateursrelease uit de ondersteunde platformmatrix worden verwijderd, wat het einde van de ondersteuning voor de software aangeeft.

#### Servicepacks

- **Service Pack-dekking**: Adobe biedt technische ondersteuning voor AEM Forms-omgevingen met behulp van de nieuwste zes servicepacks. Als uw huidige versie de laatste zes de dienstpakken voorafgaat, adviseert de Adobe sterk bevordering aan de recentste versie voor optimale prestaties, veiligheid, en ononderbroken steun.

- **Richtlijnen voor patchinstallatieprogramma**: Wanneer u de patchinstallatieprogramma&#39;s gebruikt om bij te werken, is het van cruciaal belang om te controleren of de onderliggende volledige installateursversie niet meer dan twee versies oud is. Zorg er bijvoorbeeld tijdens de installatie van servicepack 6.5.19.0 voor dat de onderliggende versie van het volledige installatieprogramma 6.5.18.0 of 6.5.12.0 is.

- **Ondersteuning voor patchupgrade**: U kunt een upgrade uitvoeren naar het nieuwste servicepakket totdat u ook een upgrade uitvoert naar de meest recente ondersteunde platforms. Bijvoorbeeld, is het bevorderen van de dienstpak 6.5.12.0 aan 6.5.19.0 mogelijk, op voorwaarde dat u naar een platformcombinatie overgaat die voor 6.5.19.0 wordt gesteund.

### Aanbevolen configuraties {#recommendedconfigurations}

Adobe raadt deze configuraties aan en biedt volledige of beperkte ondersteuning als onderdeel van de standaard overeenkomst voor softwareonderhoud:

<table>
 <tbody>
  <tr>
   <th>Ondersteuningsniveau</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>A: Ondersteund<br /> </td>
   <td>Adobe biedt volledige ondersteuning en onderhoud voor deze configuratie. Deze configuratie valt onder het kwaliteitsborgingsproces van de Adobe.</td>
  </tr>
  <tr>
   <td>R: Beperkte ondersteuning</td>
   <td>Adobe verleent volledige steun voor deze configuratie nadat bepaalde eerste vereisten worden voldaan. Neem contact op met de Enterprise Support van de Adobe voor meer informatie over de voorwaarden en vraag om ondersteuning.</td>
  </tr>
  <tr>
   <td>L: Beperkte ondersteuning</td>
   <td>Adobe biedt volledige ondersteuning en onderhoud voor deze configuratie nadat aan bepaalde voorwaarden is voldaan. Niet zijn alle mogelijkheden beschikbaar op de configuratie. Neem contact op met de Enterprise Support van de Adobe voor meer informatie over de voorwaarden en vraag om ondersteuning.<br /> </td>
  </tr>
 </tbody>
</table>

### Niet-ondersteunde configuraties {#unsupported-configurations}

| Ondersteuningsniveau | Beschrijving |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| E: Naar verwachting werken | De configuratie zal naar verwachting werken en er zijn geen meldingen van het tegendeel. |
| Z: Niet ondersteund | De configuratie wordt niet ondersteund. Adobe legt geen verklaringen over of de configuratie werkt, en steunt het niet. |

>[!NOTE]
>
>Om klanten van AEM Forms te helpen de kosten van eigendom verminderen, de plaatsingsarchitectuur vereenvoudigen, en de ontwikkelingsstapel moderniseren, beweegt het ondernemingsplatform van Adobe Experience Manager zich van op toepassingsserver-gebaseerde plaatsingen in de plaats van op standalone op OSGi-Gebaseerde plaatsingen. Adobe blijft de AEM Forms JEE-stack met een beperkte matrix van infrastructuurcomponenten ondersteunen.
>
>Met de versie van 6.5, worden de infrastructuurcomponenten die het laagste gebruik onder Adobe klanten hebben niet meer gesteund, als volgt:
>
>- IBM® DB2® database
>- Besturingssystemen van IBM® AIX® en Sun Solaris™
>
>Voor nieuwe installaties, waar mogelijk, wordt geadviseerd om AEM Forms op de moderne OSGi stapel op te stellen om de recentste innovaties rond ontvankelijke Adaptive Forms voor mobiele, multi-kanaals Interactieve Mededelingen, en backendgegevensintegratie te gebruiken gebruikend het Model van de Gegevens van de Vorm.
>
>Adobe erkent dat bestaande gebruikers AEM Forms moeten blijven implementeren in JEE-stack. In dergelijke scenario&#39;s, vereist de Adobe de plaatsing van AEM Forms JEE op gesteunde infrastructuur zoals die in deze documentatie wordt beschreven. Als u een upgrade uitvoert naar AEM 6.5 Forms en een niet-ondersteund platform gebruikt in de vorige AEM Forms-release, kunt u contact opnemen met Adobe Support voor hulp bij de upgrade naar een ondersteund platform.

### Java™ Virtual Machines (JVM) {#java-virtual-machines-jvm}

Adobe Experience Manager Forms vereist dat een Java™ Virtual Machine wordt uitgevoerd, die wordt geleverd door de JDK-distributie (Java™ Development Kit). Adobe Experience Manager werkt met de volgende versies van Java™ Virtual Machines:

<table>
 <tbody>
  <tr>
   <th><p><strong>Platform</strong></p> </th>
   <th><p><strong>Ondersteuningsniveau</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr> 
   <td><p>Oracle Java™ SE 11 (64-bits) <sup> [8] </sup> </p>  </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Kleine releases en updates </p> </td>
  </tr>
  <tr>
   <td>Azul Zulu OpenJDK 11 - 64 bits</td>
   <td>Z: Niet ondersteund</td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td>Azul Zulu OpenJDK 8 - 64 bits</td>
   <td>Z: Niet ondersteund</td>
   <td><p> </p> </td>
  </tr>
  <tr>
   <td>Oracle Java™ SE 8 (64-bits)</td>
   <td>A: Ondersteund</td>
   <td>Kleine releases en updates</td>
  </tr>
  <tr>
   <td>IBM® J9 Virtual Machine (build 2.9, JRE 1.8.0) IBM® JDK SR6-FP26<br /> </td>
   <td>A: Ondersteund</td>
   <td>Kleine releases en updates</td>
  </tr>
  <tr>
   <td>IBM® JAVA1.8.0_291(build 8.0.6.30)<br /> </td>
   <td>A: Ondersteund</td>
   <td>Kleine releases en updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>- Volg de beveiligingsbulletins van de Java™-leverancier om de veiligheid en beveiliging van productieomgevingen te garanderen en installeer de nieuwste Java™-updates.
>- AEM Forms on JEE ondersteunt alleen 64-bits JVM&#39;s in productieomgevingen.

### Databases en CRX-permanente {#databases-and-crx-persistence}

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
   <td><p> MongoDB Enterprise 5.0</p> </td>
   <td><p>Repository Microkernel</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
    <tr>
   <td><p> MongoDB Enterprise 6.0 </p> </td>
   <td><p>Repository Microkernel</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
   <tr>
   <td>Database 19c van oracles (Standard, Real Application Clusters (RAC) en Enterprise-edities) </td>
   <td>Repository Microkernal </td>
   <td>Ondersteund</td>
  </tr>
  <tr>
   <td><p>Repository Microkernel</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
  <tr>
   <td><p>Microsoft® SQL Server 2019 </p> </td>
   <td><p>Repository Microkernel</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
  <tr>
   <td>IBM® DB2® 11.1 (Afgekeurd)</td>
   <td>Repository Microkernel</td>
   <td>R: Beperkte ondersteuning</td>
  </tr>
  <tr>
  <tr>
   <td>MySQL 8.0.27</td>
   <td>-</td>
   <td>R: Beperkte ondersteuning</td>
  </tr>
 </tbody>
</table>

- IBM® DB2® wordt niet ondersteund voor nieuwe installaties. Deze wordt alleen ondersteund voor bestaande klanten die een upgrade uitvoeren naar AEM 6.5 Forms.
- MongoDB is software van derden en is niet opgenomen in het AEM licentiepakket. Zie voor meer informatie [Beleid voor MongoDB-licenties](https://www.mongodb.org/about/licensing/).
- Om optimaal gebruik te kunnen maken van uw AEM, raadt Adobe u aan een licentie te verlenen voor de MongoDB Enterprise-versie, zodat u kunt profiteren van professionele ondersteuning.
- De Klantenservice van de Adobe helpt kwalificerende problemen met betrekking tot het gebruik van MongoDB met AEM. Zie de klasse [Pagina MongoDB voor Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).
- &#39;Bestandssysteem&#39; omvat blokopslag die voldoet aan POSIX. Dit omvat netwerkopslagtechnologie. Houd er rekening mee dat de prestaties van het bestandssysteem kunnen variëren en van invloed zijn op de algehele prestaties. U wordt aangeraden AEM te laden met het netwerk of externe bestandssysteem.
- Alleen MongoDB Storage Engine WiredTiger wordt ondersteund.
- Delen via MongoDB wordt niet ondersteund in AEM.
- AEM Forms op JEE biedt geen ondersteuning voor MySQL voor RDBMK-persistentie.
- De module Documentbeveiliging maakt geen gebruik van Inhoudsopslagruimte. Dit houdt in dat als u alleen Documentbeveiliging gebruikt en geen HTML Workspace, HTML5-formulieren of adaptieve formulieren wilt gebruiken, u geen Content Repository hoeft te installeren.
- AEM Forms op JEE biedt geen ondersteuning voor het gebruik van MySQL voor het blijvend AEM Repository (CRX-Repository).

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
   <td>Microsoft® SQL Server<br /> </td>
   <td><p>Microsoft® SQL Server JDBC-stuurprogramma 8.2.2<br /> </p> <p>sqljdbc8.jar</p> </td>
   <td><p>Downloaden vanaf Microsoft®-website.</p> </td>
  </tr>
  <tr>
   <td>Oracle</td>
   <td><p>JDBC-stuurprogramma voor oracle Database 19.3.0.0.0</p> <p>ojdbc8.jar (versie 19.3.0.0.0)<br /> </p> </td>
   <td><p>Downloaden van <a href="https://www.oracle.com/database/technologies/appdev/jdbc-ucp-19c-downloads.html">Website oracle</a>.</p> </td>
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
   <td>Oracle WebLogic Server 12.2.1 (12c R2) (Afgekeurd) <sup>[9]</sup></td>
   <td>A: Ondersteund</td>
   <td>Servicepack en kritieke updates</td>
  </tr>
  <tr>
   <td>Oracle WebLogic Server 14c <sup>[9]</sup></td>
   <td>A: Ondersteund</td>
   <td>Servicepack en kritieke updates</td>
  </tr>
  <tr>
   <td>IBM® WebSphere® Application Server 9.0.0.10 <sup>[1] [4]</sup><br /> </td>
   <td>A: Ondersteund</td>
   <td>Servicepack en kritieke updates</td>
  </tr>
  <tr>
   <td><p>JBoss® Enterprise Application Platform (EAP) 7.4 <sup>[2] [3] [7]</sup> </p> </td>
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
   <td>Microsoft® Windows Server 2019 (64-bits) (afgekeurd)</td>
   <td>A: Ondersteund</td>
   <td>Servicepacks en kritieke updates</td>
  </tr>
     <tr>
   <td>Microsoft® Windows Server 2022 (64-bits)</td>
   <td>A: Ondersteund</td>
   <td>Servicepacks en kritieke updates</td>
  </tr>
  <tr>
   <td>Ubuntu 20,04</td>
   <td>A: Ondersteund</td>
   <td>Servicepacks en kritieke updates</td>
  </tr>
  <tr>
   <td><p>Red Hat® Enterprise Linux® 8 (Kernel 4.x) (64-bits)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Kleine releases, cumulatieve updates en kritieke updates</p> </td>
  </tr>
  <tr>
   <td><p>Red Hat® Enterprise Linux® 7 (Kernel 3.x) (64-bits) (afgekeurd)</td>
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

U kunt AEM Forms op JEE op een fysieke machine of een virtuele omgeving uitvoeren. Als u echter een probleem tegenkomt met AEM Forms in een virtuele omgeving, probeert u het probleem te repliceren op een fysieke computer. Neem contact op met de Adobe Support voor een oplossing als het probleem zich blijft voordoen op de fysieke computer. Voor de problemen die u niet op een fysieke machine kunt repliceren, contacteer uw virtuele milieuverkoper.

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
   <td>E: Naar verwachting werken</td>
   <td><p>Servicepack en kritieke updates</p> </td>
  </tr>
 </tbody>
</table>

### Uitzonderingen op ondersteunde serverplatforms {#exceptions-to-supported-server-platforms}

Houd rekening met de volgende uitzonderingen wanneer u een platform kiest voor het instellen van uw AEM Forms op de JEE-server.

1. AEM Forms on JEE biedt geen ondersteuning voor IBM® WebSphere® met MySQL.
1. AEM Forms op JEE biedt geen ondersteuning voor en JBoss® op SUSE® Linux® Enterprise Server 12. Alleen IBM® WebSphere® wordt ondersteund op SUSE® Linux® Enterprise Server 12.
1. AEM Forms op JEE biedt geen ondersteuning voor JDK met JBoss® anders dan Oracle Java™ SE.
1. AEM Forms on JEE biedt geen ondersteuning voor JDK met IBM® WebSphere®, behalve IBM® JDK.
1. CRX-opslagplaats steunt persistentie van type TarMK, MongoDB, en relationele gegevensbestanden (RDBMK). U kunt geen twee verschillende gegevensbestandsystemen tussen de toepassingsserver en CRX-bewaarplaats hebben. Op een AEM Forms op JEE-omgeving kunt u echter MongoMK gebruiken met CRX-gegevensopslagruimte en een ondersteunde relationele database met toepassingsserver.
1. AEM Forms op JEE biedt geen ondersteuning voor WebSphere®-toepassingsserver op CentOS.
1. AEM Forms on JEE biedt geen ondersteuning voor JBoss® op rollen gebaseerde toegangsbeheer (RBAC).
1. AEM Forms on JEE biedt alleen ondersteuning voor Oracle Java™ SE 11 (64-bits) SDK voor de toepassingsserver JBoss® EAP 7.4.
1. JDK-versies hoger dan 1.8.0_281 worden niet ondersteund voor WebLogic-server. (FORMS-8498)
1. JDK 11.0.20 wordt niet ondersteund voor de installatie van AEM Forms op JEE Installer. Alleen JDK 11.0.19 of eerdere versies worden ondersteund voor de installatie van AEM Forms op JEE Installer.

<!-- 
1. [!DNL Microsoft&reg; Windows Server 2019] does not support [!DNL MySQL 5.7] and [!DNL JBoss&reg; EAP 7.1], [!DNL Microsoft&reg; Windows Server 2019] does not support turnkey installations for [!DNL Experience Manager Forms Service Pack 6.5.10.0 and later]. (CQDOC-18312) 
-->

Houd rekening met de volgende punten wanneer u software kiest voor de Adobe van AEM Forms bij JEE-implementaties:

- AEM Forms on JEE ondersteunt updates, patches en repareert pakketten boven op de opgegeven primaire en secundaire versie van ondersteunde software. Bijwerken naar de volgende hoofd- of subversie wordt echter alleen ondersteund als dit is opgegeven.
- Clustergebaseerde installaties ondersteunen TarMK-persistentie niet. Zie voor informatie over ondersteunde persistentie [Een persistentietype kiezen voor een AEM Forms-installatie](/help/forms/using/choosing-persistence-type-for-aem-forms.md).
- AEM Forms on JEE biedt ondersteuning voor verschillende software van derden, zoals bepaald door de Adobe [Beleid voor softwareondersteuning van derden](../../forms/using/aem-forms-jee-supported-platforms.md#p-third-party-patch-support-policy-p).
- AEM Forms on JEE biedt ondersteuning voor platforms die overeenkomen met de ondersteuning van externe leveranciers. Sommige combinaties zijn mogelijk niet toegestaan door externe leveranciers. Veel leveranciers hebben hun toepassingsservers bijvoorbeeld niet met Oracle gecertificeerd. Als gevolg hiervan biedt AEM Forms op JEE ook geen ondersteuning voor deze combinaties. Om ervoor te zorgen dat u de gesteunde softwareversies kiest, controleer de steunmatrijs ook voor de derdeverkopers.
- AEM Forms op JEE ondersteunt TarMK Cold Standby niet.
- AEM Forms op JEE biedt geen ondersteuning voor verticale clustering.
- AEM Forms on JEE biedt geen ondersteuning voor MySQL-database in een geclusterde omgeving.
- Voor de lijst met verwijderde of bijgewerkte platforms raadpleegt u [AEM 6.5 Forms - Overzicht van nieuwe functies](../../forms/using/whats-new.md) document.

### LDAP-servers (optioneel) {#ldap-servers-optional}

<table>
 <tbody>
  <tr>
   <th><p><strong>Product (basisversie)</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td>Microsoft® Active Directory 2016 (afgekeurd)</td>
   <td>Onderhoudsrelease en -reparatiepakketten</td>
  </tr>
  <tr>
   <td>Microsoft® Active Directory 2022</td>
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
| ----------------------- |
| Microsoft® Exchange 2013 |
| Microsoft® Office 365 |

### Inhoudsmanagers en bijbehorende connectors {#content-managers-and-corresponding-connectors}

<table>
 <tbody>
  <tr>
   <td><strong>Product<br /> </strong></td>
   <td><strong>Versie</strong></td>
  </tr>
  <tr>
   <td>EMC Documentum®</td>
   <td>7,3</td>
  </tr>
  <tr>
   <td>IBM® FileNet</td>
   <td>5.5.2.</td>
  </tr>
  <tr>
   <td>IBM® Content Manager Server (afgekeurd) </td>
   <td>8.5 Fix pack 2</td>
  </tr>
  <tr>
   <td> IBM® Content Manager Client (afgekeurd)</td>
   <td>8,5 </td>
  </tr>
   <td>Microsoft® Sharepoint </td>
   <td>19<br /> </td>
  </tr>
 </tbody>
</table>

### Steun voor Cordova {#support-for-cordova}

AEM Forms App ondersteunt nu de Apache Cordova. Hier volgen de platformspecifieke versies van Cordova die worden ondersteund:

- Apache Cordova 6.4.0
- Cordova iOS 4.3.0
- Cordova Android™ 6.0.0
- Cordova Windows 4.4.3

### Softwareondersteuning voor PDF Generator {#software-support-for-pdf-generator}

<table>
 <tbody>
  <tr>
   <th><p><strong>Product</strong></p> </th>
   <th><p><strong>Ondersteunde indelingen voor conversie naar PDF</strong></p> </th>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2020 klassiek spoor</a> nieuwste versie</td>
   <td>XPS, afbeeldingsindelingen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF en DWF</td>
  </tr>
  <tr>
   <td>Microsoft® Office 2019</td>
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF en TXT</td>
  </tr>
  <tr>
   <td>WordPerfect 2020<br /> </td>
   <td>WP, WPD</td>
  </tr>
  <tr>
   <td>Microsoft® Publisher 2019<br /> </td>
   <td>PUB</td>
  </tr>
  <tr>
   <td>OpenOffice 4.1.10</td>
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXC, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, afbeeldingsindelingen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC) HTML, , HTM, RTF en TXT</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>PDF Generator ondersteunt alleen de Engelse, Franse, Duitse en Japanse versies van de ondersteunde besturingssystemen en toepassingen.
>
>Daarnaast:
>
>- PDF Generator ondersteunt alleen de 32-bits versie in de detailhandel van Microsoft® Office Professional Plus en andere software die vereist is voor conversie.
>- PDF Generator biedt geen ondersteuning voor Microsoft® Office 365.
>- PDF Generator-conversies voor OpenOffice worden alleen ondersteund in Windows en Linux®.
>- De functies OCR PDF, Optimize PDF en Export PDF worden alleen in Windows ondersteund.
>- Een versie van Acrobat wordt met AEM Forms gebundeld om de functionaliteit van de PDF Generator in te schakelen. De gebundelde versie zou slechts programmatically met AEM Forms, tijdens de termijn van de vergunning van AEM Forms, voor gebruik met AEM Forms PDF Generator moeten worden betreden. Zie de productbeschrijving van AEM Forms volgens uw implementatie ([Op locatie](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) of [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;
>- PDF Generator-service biedt geen ondersteuning voor Microsoft® Windows 10.
>- PDF Generator kan bestanden niet converteren met Microsoft® Visio 2019.
>- PDF Generator kan bestanden niet converteren met Microsoft® Project 2019.
>- Als een Microsoft® Office-installatie om welke reden dan ook gedeactiveerd of zonder licentie wordt, zoals een installatie met volumelicentie die binnen een bepaalde periode geen KMS-host kan vinden, kunnen conversies mislukken totdat de installatie opnieuw in licentie wordt gegeven en opnieuw wordt geactiveerd.

<!-- Removed lines: >- PDF Generator fails to convert files using Microsoft&reg; Visio 2019. You can continue to use Microsoft&reg; Visio 2016 to convert .VSD and .VSDX files.
>- PDF Generator fails to convert files using Microsoft&reg; Project 2019. You can continue to use Microsoft&reg; Project 2016 to convert .MPP files.-->

### Uitzonderingen op toegankelijkheidsondersteuning {#exceptions-to-accessibility-support}

De volgende subsystemen van AEM Forms zijn niet [508](https://www.section508.gov/) compatibel:

- Aangepaste Forms Authoring UI
- Gebruikersinterface voor Forms Manager
- Gebruikersinterface Correspondentenbeheer
- Admin UI (interface beheerconsole)

## Systeemvereisten voor AEM Forms op JEE {#system-requirements-for-aem-forms-on-jee}

### Minimale hardwarevereisten {#minimum-hardware-requirements}

<table>
 <tbody>
  <tr>
   <td>Platform</td>
   <td>Minimale hardwarevereisten</td>
  </tr>
  <tr>
   <td>Microsoft® Windows Server</td>
   <td>Intel Xeon® E5-2680-, 2,4-GHz-processor of gelijkwaardig<br /> VMWare ESX 5.1 of hoger<br /> RAM: 6 GB (64-bits besturingssysteem met 64-bits JVM)<br /> Vrije schijfruimte: 15 GB tijdelijke ruimte plus 22 GB<br /> voor AEM Forms op JEE</td>
  </tr>
  <tr>
   <td>SUSE® Linux® Enterprise Server</td>
   <td>Intel Xeon® E5-2670v2, 1 vCPU, 2,5-GHz processor<br /> AWS m3.medium (3 Ecu)<br /> RAM: 6 GB (64-bits besturingssysteem met 64-bits JVM)<br /> Vrije schijfruimte: 6 GB tijdelijke ruimte plus 22 GB<br /> voor AEM Forms op JEE</td>
  </tr>
  <tr>
   <td>Red Hat® Enterprise Linux®</td>
   <td>Intel Xeon® E5-2670v2, 1 vCPU, 2,5-GHz processor<br /> AWS m3.medium (3 Ecu)<br /> RAM: 6 GB (64-bits besturingssysteem met 64-bits JVM)<br /> Vrije schijfruimte: 6 GB tijdelijke ruimte plus 22 GB<br /> voor AEM Forms op JEE<br /> </td>
  </tr>
  <tr>
   <td>Hardwarevereisten voor een kleine productieomgeving</td>
   <td>
    <ul>
     <li><strong>Intel® processoromgeving</strong>: Intel Xeon® E5-2680, 2,4 GHz of hoger. Het gebruik van een dual core processor zal de prestaties verder verbeteren</li>
     <li><strong>Geheugen: </strong>4 GB <br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Zie voor aanvullende vereisten:

- [Systeemvereisten voor AEM Forms op één server bij JEE-implementatie](https://www.adobe.com/go/learn_aemforms_sysreq_single_65)
- [Systeemvereisten voor een geclusterde AEM Forms bij JEE-implementatie](https://www.adobe.com/go/learn_aemforms_sysreq_cluster_65)

## Ondersteunde clients voor AEM Forms op JEE {#supported-clients-for-aem-forms-on-jee}

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
   <td>Microsoft® Windows® 2019 Server (afgekeurd)</td>
   <td>Servicepacks en kritieke updates</td>
  </tr>
  <tr>
   <td>Microsoft® Windows® 2022 Server</td>
   <td>Servicepacks en kritieke updates</td>
  </tr>
 </tbody>
</table>

- Schijfruimte voor installatie: 1,7 GB alleen voor Workbench, 2,7 GB op één station voor een volledige installatie van Workbench, Designer en de samplesamenstelling 400 MB voor tijdelijke installatiemappen - 200 MB in de map met gebruikerstempels en 200 MB in de tijdelijke map van Windows. Als al deze locaties zich op één station bevinden, moet er tijdens de installatie 1,5 GB aan ruimte beschikbaar zijn. De naar de tijdelijke mappen gekopieerde bestanden worden verwijderd wanneer de installatie is voltooid.

- Geheugen voor het uitvoeren van Workbench: 2 GB RAM
- Hardwarevereisten: Intel® Pentium® 4- of AMD®-equivalent, 1-GHz processor
- Minimale monitorresolutie van 1024 x 768 pixels of hoger met 16-bits kleur of hoger
- TCP/IPv4- of TCP/IPv6-netwerkverbinding met de AEM Forms op JEE-server
- U moet over beheerdersrechten beschikken om Workbench in Windows te installeren. Als u een niet-beheerdersaccount installeert, vraagt het installatieprogramma u om de referenties voor een geschikte account.

### Designer {#designer}

- Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server, Microsoft® Windows® 10 of Windows® 11
- Processor van 1 GHz of sneller met ondersteuning voor PAE, NX en SSE2.
- 1 GB RAM voor 32-bits of 2 GB RAM voor 64-bits besturingssysteem
- 16 GB schijfruimte voor 32-bits of 20 GB schijfruimte voor 64-bits besturingssysteem
- Grafisch geheugen - 128 MB GPU (256 MB aanbevolen)
- 2,35 GB beschikbare ruimte op de vaste schijf
- Monitorresolutie van 1024 x 768 pixels of hoger
- Hardwareversnelling voor video (optioneel)
- Acrobat Pro DC, Acrobat Standard DC of Adobe Acrobat Reader DC
- Beheerdersrechten voor de installatie van Designer
- Microsoft® Visual C++ 2019 (VC 14.28 of hoger) 32-bits runtime

### Adobe Acrobat en Adobe Reader {#adobe-acrobat-and-adobe-reader}

<table>
 <tbody>
  <tr>
   <th><p><strong>Acrobat en Adobe Reader (basis)</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td>Acrobat 2020 (klassieke track)</td>
   <td>Versie 20.004.3006 of hoger<br /> </td>
  </tr>

</tbody>
</table>

>[!NOTE]
>
>De Acrobat DC productfamilie introduceert twee sporen voor zowel Acrobat als Reader die verschillende producten zijn: &quot;Klassiek&quot; en &quot;Doorlopend&quot;. Zie voor meer informatie en een vergelijking van de twee sporen [https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/whatsnewdc.html](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/whatsnewdc.html).

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
   <td><p>Microsoft® Edge (Evergreen)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Servicepacks en -updates</p> </td>
  </tr>
  <tr>
   <td><p>Mozilla Firefox (Evergreen)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td>Alle updates</td>
  </tr>
  <tr>
   <td>Mozilla Firefox ESR</td>
   <td>E: Naar verwachting werken</td>
   <td> Alle updates</td>
  </tr>
  <tr>
   <td><p>Google Chrome (Evergreen)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td>Alle updates</td>
  </tr>
  <tr>
   <td>Apple Safari op macOS</td>
   <td>A: Ondersteund</td>
   <td>Alle updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Bepaalde browsergerelateerde uitzonderingen voor desktops zijn als volgt:
>
>- Safari wordt alleen ondersteund op Macintosh OS X.
>- De werkruimte biedt ondersteuning voor Safari 5.1 op Macintosh OS X 10.6 en 10.7 met Acrobat DC of latere versies. Zie voor meer informatie over de compatibiliteit met Adobe Reader, Acrobat, Safari 5.1 [https://helpx.adobe.com/x-productkb/multi/safari-5-1-incompatible-reader.html](https://helpx.adobe.com/x-productkb/multi/safari-5-1-incompatible-reader.html).
>- Beheerconsole wordt niet ondersteund in Safari.
>- Correspondence Management biedt geen ondersteuning voor Windows® Internet Explorer 9.0 voor AEM 6.1-formulieren.
>- Forms Portal ondersteunt JAWS 14.0-schermlezersoftware in Internet Explorer 11 voor toegankelijkheid.

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
   <td>Safari op iOS 15.1 en hoger</td>
   <td>Alle updates</td>
  </tr>
  <tr>
   <td>Microsoft® Edge<br /> </td>
   <td>Alle updates<br /> </td>
  </tr>
  <tr>
   <td>Systeemeigen Android™-browser op Android™ 4.4 en hoger</td>
   <td>Alle updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>- Forms Portal wordt alleen ondersteund op Safari op iPad.

### AEM Forms-app {#aem-forms-workspace-app}

#### Ondersteuning voor mobiele apparaten {#mobile-device-support}

De AEM Forms-app is beschikbaar op de volgende platforms:

| **Platform** | **Ondersteunde apparaten** |
| ----------------- | ------------------------------------------------------------------------------------------------------------------- |
| Apple iOS | Apple iPhone, iPad, iPad Air en iPad mini met iOS 15.1 en hoger. |
| Google Android™ | Android™ 5.1 en hoger. De AEM Forms-app is gecertificeerd voor Samsung Galaxy-tablets van 7 en 10 inch en voor populaire smartphones. |
| Microsoft® Windows | Microsoft® Surface devices, tablets, notebooks en desktops met Microsoft® Windows 10 besturingssysteem. |

### Documentbeveiligingsextensie Adoben voor Microsoft® Office {#adobe-rights-management-extension-for-microsoft-office}

Klikken [hier](https://www.adobe.com/products/livecycle/rightsmanagement/extension/downloads.html) om de systeemvereisten voor de Uitbreiding van de Veiligheid van het Document van de Adobe voor Microsoft® Office te zien.

### Uitzonderingen op clientondersteuning {#exceptions-to-client-support}

AEM Forms on JEE ondersteunt updates, patches en repareert pakketten boven op de opgegeven primaire en secundaire versie van ondersteunde software. Bijwerken naar de volgende hoofd- of subversie wordt echter alleen ondersteund als dit is opgegeven.

## Flardondersteuningsbeleid van derden {#third-party-patch-support-policy}

De softwarevereisten van derden voor AEM Forms op JEE worden beschreven in het gedeelte &quot;Systeemvereisten&quot; van hun respectieve productdocumenten. Alle documentatie openen vanuit [https://adobe.com/go/learn_aemforms_documentation_65](https://adobe.com/go/learn_aemforms_documentation_65) .

AEM Forms op de referentieplatforms van derden van JEE vermeldt het specifieke patchniveau van de infrastructuur van derden dat tijdens de ontwikkeling en release van AEM Forms op JEE actueel was, en van het minimale patchniveau/servicepack van de infrastructuur die door die versie van AEM Forms op JEE wordt ondersteund.

De Adobe steunt dringende of geadviseerde patches die door derdeverkopers op hun versie worden uitgegeven veronderstellend dat derdeverkopers achterwaartse verenigbaarheid met de versies waarborgen die AEM Forms op JEE steun. Adobe biedt alleen ondersteuning voor patches die worden vrijgegeven na het minimale patchniveau dat in de AEM Forms in JEE-documentatie is vermeld.

Soms biedt Adobe geen ondersteuning voor updates van derden die belangrijke functionaliteit wijzigen en dus geen ondersteuning bieden voor volledige achterwaartse compatibiliteit. Zie voor meer informatie over de ondersteunde updates [Ondersteunde patchdefinities](https://helpx.adobe.com/aem-forms/aem-forms-third-party-software-patch.html) voor specifieke verkopersproducten en de Adobe van flardtypes steunt.

Onder omstandigheden waarover de Adobe geen controle heeft, kunnen patches van derden die zich beroepen op achterwaartse compatibiliteit, negatieve gevolgen hebben voor de producten van de Adobe of de omgeving van de klant. In dergelijke gevallen raadt de Adobe klanten aan de gevolgen van een noodpatch van een derde te beoordelen voordat ze deze op kritieke systemen toepassen. Adobe werkt met derden samen door redelijke zakelijke inspanningen te leveren om dergelijke problemen op te lossen, hetzij via normale ondersteuningsprogramma&#39;s voor Adoben, hetzij door derden die het probleem in hun patch verhelpen. Dit garandeert niet dat een nieuw vrijgegeven patch van derden die door de Adobe wordt ondersteund, werkt zoals beschreven door de leverancier of met AEM Forms op JEE.

De Adobe behoudt zich het recht voor om de derdeverwijzingsplatforms te veranderen die door AEM Forms op JEE versie en hun gesteunde flarddefinities op om het even welk bepaald punt worden gesteund.

Aanvullende informatie voor patches van derden vindt u ook op de website Enterprise Support van de Adobe op artikelen in de kennisdatabase die betrekking hebben op uw product.

<!--

## Platform updates {#platform-updates}

The following platforms are marked as deprecated with AEM Forms 6.5.18.0 release on August 31, 2023:

- Microsoft&reg; Windows Server 2019 (64-bit)
- Microsoft&reg; Active Directory 2016

The following platforms are marked as deprecated with AEM Forms 6.5.13.0 release on June 2, 2022:
- Microsoft&reg; SharePoint 2016

The following platforms are marked as deprecated with AEM Forms 6.5.10.0 release on September 7, 2021:

- Adobe Acrobat 2017 - [Core support for Adobe Acrobat 2017 ends on June 6, 2022](https://helpx.adobe.com/support/programs/eol-matrix.html).
- Red Hat&reg; Enterprise Linux&reg; 7 (Kernel 3.x) (64-bit)
- Microsoft&reg; Windows Server 2016 (64-bit) 
- Microsoft&reg; Office 2016
- OpenOffice 4.1.2

-->


## Revisie-overzicht {#revision-history}

<!--

- 6.5.18.0 (Aug 31, 2023)
  - **Added support**: [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platforms:
    - MongoDB Enterprise 4.4
    - Oracle WebLogic Server 14c
    - My SQL JDBC connector 8
    - Active Directory 2022
    - Microsoft&reg; Windows Server 2022 (64-bit)

  - **Removed support**: [!DNL Adobe Experience Manager Forms] on JEE has removed support for the following platforms:
    - Windows Server 2016 (64-bit)
    - MongoDB Enterprise 4.0
    - Oracle Database 12c Release 2 (12.2.0.1.0)
    - MySQL 5.7.35
    - Microsoft&reg; SQL Server 2016
    - JBoss&reg; EAP 7.1.4
    - My SQL JDBC connector 5.1.44
    - Microsoft&reg; SQL Server JDBC driver 6.2.1.0
    - Microsoft&reg; SQL Server JDBC driver 6.2.2.0
    - Microsoft&reg; JDBC Driver 8.x for SQL Server

    The release has also removed support for the following platforms for PDF Generator and in-general:
    - Microsoft&reg; Sharepoint 2016
    - Microsoft&reg; Office 2016
    - Microsoft&reg; Office Visio 2016 
    - Microsoft&reg; Publisher 2016
    - Microsoft&reg; Project 2016
    - OpenOffice 4.1.2
    - Acrobat 2017 (Classic track) Version 17.011.30078 or later

  - **Deprecated support**: [!DNL Adobe Experience Manager Forms] on JEE has deprecated the following platforms:
    - Microsoft&reg; Windows Server 2019 (64-bit)
    - Microsoft&reg; Active Directory 2016
    
- 6.5.13.0 (June 2, 2022)

  The following platforms are deprecated with AEM Forms 6.5.13.0 release on:
 
  - Microsoft&reg; SharePoint 2016

- 6.5.12.0 (March 3, 2022)

    - **Platform Updates**: [!DNL Adobe Experience Manager Forms] on JEE has removed support for the following platforms:
      - IBM&reg; J9 Virtual Machine (build 2.8, JRE 1.8.0)
      - Oracle Database 12c Release 1
      - Oracle Database 18c
      - Oracle Unified Directory (OUD) 11g Release 2
      - IBM&reg; Lotus Domino 9.0
      - IBM&reg; FileNet 5.2
      - Adobe Flash Player

    - **Platform Updates**: [!DNL Adobe Experience Manager Forms] on JEE has deprecated the following platforms:

      - MongoDB Enterprise 4.0
      - MongoDB Enterprise 4.2
      - IBM&reg; DB2&reg; 11.1
      - Oracle Database 12c Release 2
      - MySQL 5.7.35
      - Microsoft&reg; SQL Server JDBC driver 6.2.1.0
      - JBoss&reg; Enterprise Application Platform (EAP) 7.1.4
      - IBM&reg; Content Manager Server 8.5 Fix pack 2
      - IBM&reg; Content Manager Client 8.5
      - Microsoft&reg; SQL Server 2016

- 6.5.10.0 (Sep 01, 2022)

  - **Added support**: [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platform:
  
    - Oracle Java&trade; SE 11 (64 bit) SDK for application server JBoss&reg; EAP 7.4.
  - **Deprecated support**: [!DNL Adobe Experience Manager Forms] on JEE has deprecated the following platforms:

    - Adobe Acrobat 2017 - [Core support for Adobe Acrobat 2017 ends on June 6, 2022](https://helpx.adobe.com/support/programs/eol-matrix.html).
    - Red Hat&reg; Enterprise Linux&reg; 7 (Kernel 3.x) (64-bit)
    - Microsoft&reg; Windows Server 2016 (64-bit) 
    - Microsoft&reg; Office 2016
    - OpenOffice 4.1.2


-->

### Release 6.5.19.1 (15 december 2023)

| Toegevoegde ondersteuning | Verwijderde ondersteuning | Verouderde ondersteuning |
| -------------- | --------------- | ------------------- |
| MongoDB Enterprise 6.0 | MongoDB Enterprise 4.4 |  |
| MongoDB Enterprise 5.0 |  |  |
|  | |  |

### Release 6.5.18.0 (31 augustus 2023)

| Toegevoegde ondersteuning | Verwijderde ondersteuning | Verouderde ondersteuning |
| -------------- | --------------- | ------------------- |
| MongoDB Enterprise 4.4 | Windows Server 2016 (64-bits) | Microsoft® Windows Server 2019 (64-bits) |
| Oracle WebLogic Server 14c | MongoDB Enterprise 4.0 | Microsoft® Active Directory 2016 |
| Mijn SQL JDBC-connector 8 | Database van het oracle 12c Release 2 (12.2.0.1.0) |  |
| Active Directory 2022 | MySQL 5.7.35 |  |
| Microsoft® Windows Server 2022 (64-bits) | Microsoft® SQL Server 2016 |  |
|  | JBoss® EAP 7.1.4 |  |
|  | My SQL JDBC-connector 5.1.44 |  |
|  | Microsoft® SQL Server JDBC-stuurprogramma 6.2.1.0 |  |
|  | Microsoft® SQL Server JDBC-stuurprogramma 6.2.2.0 |  |
|  | Microsoft® JDBC-stuurprogramma 8.x voor SQL Server |  |
|  |  |  |
|  | **Verwijderde ondersteuning (PDF Generator en Algemeen):** |  |
|  | Microsoft® Sharepoint 2016 |  |
|  | Microsoft® Office 2016 |  |
|  | Microsoft® Office Visio 2016 |  |
|  | Microsoft® Publisher 2016 |  |
|  | Microsoft® Project 2016 |  |
|  | OpenOffice 4.1.2 |  |
|  | Acrobat 2017 (Classic track) versie 17.011.30078 of hoger |  |


### Release 6.5.13.0 (2 juni 2022)

| Toegevoegde ondersteuning | Verwijderde ondersteuning | Verouderde ondersteuning |
| -------------- | --------------- | ------------------- |
|  |  | Microsoft® SharePoint 2016 |


### Release 6.5.12.0 (3 maart 2022)

| Toegevoegde ondersteuning | Verwijderde ondersteuning | Verouderde ondersteuning |
| -------------- | --------------- | ------------------- |
|  | IBM® J9 Virtual Machine (build 2.8, JRE 1.8.0) | MongoDB Enterprise 4.0 |
|  | Database van oracles 12c, Release 1 | MongoDB Enterprise 4.2 |
|  | Database van oracles 18c | IBM® DB2® 11.1 |
|  | Oracle Verenigde Folder (OUD) Versie 11g 2 | Database van oracles 12c, Release 2 |
|  | IBM® Lotus Domino 9.0 | MySQL 5.7.35 |
|  | IBM® FileNet 5.2 | Microsoft® SQL Server JDBC-stuurprogramma 6.2.1.0 |
|  | Adobe Flash Player | JBoss® Enterprise Application Platform (EAP) 7.1.4 |
|  | | IBM® Content Manager Server 8.5 Fix Pack 2 |
|  | | IBM® Content Manager Client 8.5 |
|  | | Microsoft® SQL Server 2016 |
|  | | Microsoft® Windows Server 2016 |

### Release 6.5.10.0 (1 september 2022)

| Toegevoegde ondersteuning | Verwijderde ondersteuning | Verouderde ondersteuning |
| -------------- | --------------- | ------------------- |
| Oracle Java™ SE 11 (64-bits) SDK voor toepassingsserver JBoss® EAP 7.4. | | [Adobe Acrobat 2017 - Core support for Adobe Acrobat 2017 eindigt op 6 juni 2022.](https://helpx.adobe.com/support/programs/eol-matrix.html) |
|  | | Red Hat® Enterprise Linux® 7 (Kernel 3.x) (64-bits) |
|  | | Microsoft® Windows Server 2016 (64-bits) |
|  | | Microsoft® Office 2016 |
|  | | OpenOffice 4.1.2 |


>[!NOTE]
>
> Een vervangen platform blijft ondersteuning ontvangen tot de volgende volledige installateursrelease of tot de ondersteuning van een externe leverancier voor het platform aan het einde van de levensduur is bereikt, afhankelijk van wat eerder is.

<!-- 
- Oct 10, 2021

  - Changed supported version of iOS for AEM Forms App to iOS 15.1. The previous version was iOS 12.

- Sep 07, 2021
  - **Platform Updates**: [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platforms:
    - [!DNL Adobe Acrobat 2020]
    - [!DNL Ubuntu 20.04]
    - [!DNL Open Office 4.1.10]
    - [!DNL Microsoft&reg;&reg; Office 2016]
    - [!DNL Microsoft&reg;&reg; Windows Server 2016]
    - [!DNL RHEL8]

- Dec 03, 2020
  - Support added with AEM Forms 6.5.7.0 or later for the following platform:
    - [!DNL Microsoft&reg;&reg; SQL Server 2019]

- Sep 09, 2020

    - Changed supported version of iOS for AEM Forms App to iOS 12. The previous version was iOS 11.

    -->

