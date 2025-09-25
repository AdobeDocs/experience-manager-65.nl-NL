---
title: Ondersteunde platforms voor AEM Forms op JEE
description: Lijst met infrastructuurcomponenten die vereist en ondersteund zijn voor installatie van AEM Forms op JEE
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin
exl-id: 74d22cf4-56b2-48f5-92d9-928eaa134866
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on JEE,Platform Matrix
source-git-commit: 6d29cc96630292d075597f80043075972b242a8b
workflow-type: tm+mt
source-wordcount: '3809'
ht-degree: 0%

---



# Ondersteunde platforms voor AEM Forms op JEE {#supported-platforms-for-aem-forms-on-jee}


## Ondersteunde platforms {#supported-platforms}


<div class="preview">

Adobe heeft a [ volledige installateur ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) met AEM 6.5.23.0 Forms Service Pack 23 (6.5.23.0) op JEE samen met de flardinstallateurs vrijgegeven. Het volledige installatieprogramma ondersteunt nieuwe platforms, terwijl het installatieprogramma van de patch alleen foutoplossingen bevat.

Als u een nieuwe installatie uitvoert of van plan bent om recentste software voor uw AEM 6.5.23.0 Forms op milieu te gebruiken JEE, adviseert Adobe gebruikend [ AEM 6.5.23.0 Forms op volledig installatieprogramma JEE ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) vrijgegeven op 06 juni 2025 in plaats van AEM 6.5.18 Forms installer die op 31 augustus 2023 of AEM 6.5.12 wordt vrijgegeven Installer op 8 april 2019.


</div>


### Ondersteuningsniveaus {#support-levels}


AEM Forms on JEE-server kan worden ingesteld met elke combinatie van ondersteunde besturingssystemen, toepassingsservers, databases, databasestuurprogramma&#39;s, JDK, LDAP-servers en e-mailservers.


In dit document worden de ondersteunde client- en serverplatforms voor AEM Forms op JEE vermeld. Adobe biedt verschillende ondersteuningsniveaus, zowel voor door Adobe aanbevolen configuraties als voor andere configuraties. In het document worden ook andere ondersteunde software en de bijbehorende versie, uitzonderingen, patchdefinities en het ondersteuningsbeleid voor softwarepatches van derden vermeld.


>[!NOTE]
>
>- Voor een volledige lijst van uitzonderingen aan gesteunde serverplatforms, zie [ Uitzonderingen aan gesteunde serverplatforms ](#exceptions-to-supported-server-platforms).
>- AEM Forms on JEE biedt alleen ondersteuning voor Engelse, Franse, Duitse en Japanse versies van de ondersteunde besturingssystemen en toepassingen.

### Beleid voor upgrades en ondersteuning

#### Volledig installatieprogramma

- **Steun van de Verbetering voor volledige installateurs**: Een volledig installatieprogramma wordt vrijgegeven met elke zesde Versie van het Pak van de Dienst van AEM. Er is bijvoorbeeld een volledig installatieprogramma uitgebracht met 6.5.12.0 en 6.5.18.0 SP-releases. AEM Forms staat rechtstreekse upgrades uitsluitend toe vanaf de laatste twee volledige installatieprogramma&#39;s. AEM Forms biedt bijvoorbeeld alleen de mogelijkheid om rechtstreeks upgrades uit te voeren naar versie 6.5.23.0 vanaf de laatste twee volledige installatieprogramma&#39;s, namelijk 6.5.18.0 en 6.5.12.0 . Als u van een vroegere verbetering moet bevorderen, kunt u een multi-hop verbetering gebruiken om eerst naar een gesteunde volledige installateursversie en dan aan de recentste versie te gaan.

- **Verdringing**: De steun van het platform wordt bijgewerkt met elke volledige installateursversie. Alle software die in de platformmatrix is gemarkeerd als verouderd, kan in volgende releases van de ondersteunde platforms worden verwijderd of wanneer de software het einde van de ondersteuning bereikt.

#### Servicepacks


- **Coverage van het Pak van de Dienst**: Adobe verleent technische steun voor de milieu&#39;s van AEM Forms gebruikend om het even welke recentste zes de dienstpakken. Als uw huidige versie dateert van vóór de laatste zes servicepakketten, raadt Adobe u ten zeerste aan een upgrade uit te voeren naar de nieuwste versie voor optimale prestaties, beveiliging en continue ondersteuning.

- **Richtlijnen van de Update van het Patch**: Terwijl het gebruiken van de flardinstallateurs om bij te werken, is het cruciaal om te verifiëren dat de onderliggende volledige installateursversie niet meer dan twee oude versies is. Zorg er bijvoorbeeld tijdens de installatie van het servicepack 6.5.23.0 voor dat de onderliggende volledige installatieversie 6.5.18.0 of 6.5.12.0 is.

<!--
- **Patch Upgrade Support**: You can upgrade from an older service pack to a newer one (for example, from 6.5.18.0 to 6.5.23.0) using the patch installer, as long as the destination platform (OS, JDK, application server, etc.) is supported by the newer service pack.-->

### Aanbevolen configuraties {#recommendedconfigurations}


Adobe raadt deze configuraties aan en biedt volledige of beperkte ondersteuning als onderdeel van de standaard overeenkomst voor softwareonderhoud:


<table>
<tbody>
 <tr>
  <th>Ondersteuningsniveau</th>
  <th>Beschrijving</th>
 </tr>
 <tr>
  <td>A: Ondersteund <br /> </td>
  <td>Adobe biedt volledige ondersteuning en onderhoud voor deze configuratie. Deze configuratie valt onder het kwaliteitsborgingsproces van Adobe.</td>
 </tr>
 <tr>
  <td>R: Beperkte ondersteuning</td>
  <td>Adobe biedt volledige ondersteuning voor deze configuratie als aan bepaalde voorwaarden is voldaan. Neem contact op met de Adobe Enterprise Support voor meer informatie over de voorwaarden en vraag om ondersteuning.</td>
 </tr>
 <tr>
  <td>L: Beperkte ondersteuning</td>
  <td>Adobe biedt volledige ondersteuning en onderhoud voor deze configuratie nadat aan bepaalde voorwaarden is voldaan. Niet zijn alle mogelijkheden beschikbaar op de configuratie. Contacteer de ondernemingssteun van Adobe om over de eerste vereisten te leren en een verzoek om de steun op te heffen.<br /> </td>
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
>Om klanten van AEM Forms te helpen de kosten van eigendom verminderen, de plaatsingsarchitectuur vereenvoudigen, en de ontwikkelingsstapel moderniseren, beweegt het ondernemingsplatform van Adobe Experience Manager zich van op toepassingsserver-gebaseerde plaatsingen in de plaats van op standalone op OSGi-Gebaseerde plaatsingen. Adobe blijft de AEM Forms JEE-stack ondersteunen met een beperkte matrix van infrastructuurcomponenten.
>&#x200B;><br>
>&#x200B;>Met de release van 6.5 worden infrastructuurcomponenten die het laagste gebruik onder Adobe-klanten kennen, niet meer ondersteund, zoals hieronder:
>
> - IBM® DB2® database
> - Besturingssystemen van IBM® AIX® en Sun Solaris™
>
>
>Voor nieuwe installaties, waar mogelijk, wordt geadviseerd om AEM Forms op de moderne OSGi stapel op te stellen om de recentste innovaties rond ontvankelijke Adaptive Forms voor mobiele, multi-kanaals Interactieve Mededelingen, en backendgegevensintegratie te gebruiken gebruikend het Model van de Gegevens van de Vorm.
>
>Adobe erkent dat bestaande gebruikers AEM Forms moeten blijven implementeren in JEE-stack. In dergelijke scenario&#39;s vereist Adobe de implementatie van AEM Forms JEE op ondersteunde infrastructuur, zoals beschreven in deze documentatie. Als u een upgrade uitvoert naar AEM 6.5 Forms en een niet-ondersteund platform gebruikt in de vorige AEM Forms-release, kunt u contact opnemen met Adobe Support voor hulp bij de upgrade naar een ondersteund platform.

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
  <td>Oracle Java™ SE 8 (64 bits)</td>
  <td>A: Ondersteund</td>
  <td>Kleine releases en updates</td>
 </tr>
 <tr>
  <td>IBM® J9 Virtual Machine (build 2.9, JRE 1.8.0) IBM® JDK SR6-FP26 <br /> </td>
  <td>A: Ondersteund</td>
  <td>Kleine releases en updates</td>
 </tr>
 <tr>
  <td>IBM® JAVA1.8.0_291(build 8.0.6.30) <br /> </td>
  <td>A: Ondersteund</td>
  <td>Kleine releases en updates</td>
 </tr>
</tbody>
</table>


>[!NOTE]
>
>- Volg de beveiligingsbulletins van de Java™-leverancier om de veiligheid en beveiliging van productieomgevingen te garanderen en installeer de nieuwste Java™-updates.
>- AEM Forms on JEE ondersteunt alleen 64-bits JVM&#39;s in productieomgevingen.

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
  <td><p> MongoDB Enterprise 6.0 (afgekeurd) </p> </td>
  <td><p>Repository Microkernel</p> </td>
  <td><p>Ondersteund</p> </td>
 </tr>
 <tr>
  <td><p> MongoDB Enterprise 7.0 </p> </td>
  <td><p>Repository Microkernel</p> </td>
  <td><p>Ondersteund</p> </td>
 </tr>
  <tr>
  <td>Oracle Database 19c (Standard, Real Application Clusters (RAC) en Enterprise-edities) </td>
  <td>Repository Microkernal </td>
  <td>Ondersteund</td>
 </tr>
 <tr>
  <td><p>Repository Microkernel</p> </td>
  <td><p>Ondersteund</p> </td>
  <td></td>
 </tr>
 <tr>
  <td><p>Microsoft® SQL Server 2019 (afgekeurd) </p> </td>
  <td><p>Repository Microkernel</p> </td>
  <td><p>Ondersteund</p> </td>
 </tr>
 <tr>
  <td><p>Microsoft® SQL Server 2022 </p> </td>
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
  <td>MySQL 8.0.27 (afgekeurd) </td>
  <td>-</td>
  <td>R: Beperkte ondersteuning</td>
 </tr>
 <tr>
 <tr>
  <td>MySQL 8.4</td>
  <td>-</td>
  <td>R: Beperkte ondersteuning</td>
 </tr>
</tbody>
</table>


- IBM® DB2® wordt niet ondersteund voor nieuwe installaties. Deze wordt alleen ondersteund voor bestaande klanten die een upgrade uitvoeren naar AEM 6.5 Forms.
- MongoDB is software van derden en is niet opgenomen in het AEM-licentiepakket. Voor meer informatie, zie [ MongoDB het verlenen van vergunningen beleid ](https://www.mongodb.org/about/licensing/).
- Om optimaal gebruik te kunnen maken van uw AEM-implementatie, raadt Adobe aan een licentie te verlenen voor de MongoDB Enterprise-versie, zodat deze profiteert van professionele ondersteuning.
@@ -242,187 +206,150 @@ Adobe Experience Manager Forms vereist dat een Java™ Virtual Machine wordt uitgevoerd, die
- De module Documentbeveiliging maakt geen gebruik van Inhoudsopslagruimte. Dit houdt in dat als u alleen Documentbeveiliging gebruikt en geen HTML Workspace-, HTML5-formulieren of adaptieve formulieren wilt gebruiken, u geen opslagplaats voor inhoud hoeft te installeren.
- AEM Forms op JEE biedt geen ondersteuning voor het gebruik van MySQL voor het permanent opslaan van AEM Repository (CRX-Repository).


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
  <td><p>MySQL Connector/J 5.7 (afgekeurd)</p> </td>
  <td><p>Wordt geleverd bij AEM Forms op JEE-installatie</p> </td>
 </tr>
 <tr>
  <td>MySQL</td>
  <td><p>MySQL Connector/J 8.4</p> </td>
  <td><p>Wordt geleverd bij AEM Forms op JEE-installatie</p> </td>
 </tr>
 <tr>
  <td>Microsoft® SQL Server <br /> </td>
  <td><p>Microsoft® SQL Server JDBC-stuurprogramma 8.2.2 <br /> </p> <p>sqljdbc8.jar (afgekeurd) </p> </td>
  <td><p>Downloaden vanaf Microsoft®-website.</p> </td>
 </tr>
 <tr>
  <td>Microsoft® SQL Server <br /> </td>
  <td><p>Microsoft® SQL Server JDBC-stuurprogramma 12.10.0 <br /> </p> <p>sqljdbc12.10.0.jar</p> </td>
  <td><p>Downloaden vanaf Microsoft®-website.</p> </td>
 </tr>
 <tr>
  <td>Oracle</td>
  <td><p>Oracle Database 19.3.0.0.0 JDBC-stuurprogramma</p> <p>ojdbc8.jar (versie 19.3.0.0.0) <br /> </p> </td>
  <td><p>De download van <a href="https://www.oracle.com/database/technologies/appdev/jdbc-ucp-19c-downloads.html"> Website van Oracle </a>.</p> </td>
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
  <td>Oracle WebLogic Server 12.2.1 (12c R2) (Afgekeurd) <sup>[9] </sup></td>
  <td>A: Ondersteund</td>
  <td>Servicepack en kritieke updates</td>
 </tr>
 <tr>
  <td>Oracle WebLogic Server 14c <sup>[9] </sup></td>
  <td>A: Ondersteund</td>
  <td>Servicepack en kritieke updates</td>
 </tr>
 <tr>
  <td>IBM® WebSphere® Application Server 9.0.0.10 <sup> [1] [4] </sup><br /> </td>
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
  <td><p>Red Hat® Enterprise Linux® 8 (Kernel 4.x) (64-bits) (afgekeurd)</p> </td>
  <td><p>A: Ondersteund</p> </td>
  <td><p>Kleine releases, cumulatieve updates en kritieke updates</p> </td>
 </tr>
 <tr>
  <td><p>Red Hat® Enterprise Linux® 9 (Kernel 4.x) (64-bits)</p> </td>
  <td><p>A: Ondersteund</p> </td>
  <td><p>Kleine releases, cumulatieve updates en kritieke updates</p> </td>
 </tr>
 <tr>
  <td><p>SUSE® Linux® Enterprise Server 15 SP6 (64-bits) </p> </td>
  <td><p>A: Ondersteund</p> </td>
  <td><p>Servicepacks, cumulatieve patches en kritieke beveiligingsupdates</p> </td>
 </tr>
 <tr>
  <td>Oracle Linux® 7 Update 3 (64-bits)</td>
  <td>A: Ondersteund</td>
  <td>Servicepacks, cumulatieve patches en kritieke beveiligingsupdates</td>
 </tr>
</tbody>
</table>


>[!NOTE]
>
> Voor Linux®-gebaseerde servers zijn de volgende runtimeafhankelijkheden vereist:
>
> - glibc.x86_64 (2.17-196)
> - libX11.x86_64 (1.6.7-4)
> - zlib.x86-64 (1.2.7-17)
> - libxcb.x86_64 (1.13-1.el7)
> - libXau.x86_64 (1.0.8-2.1.el7)
> - glibc-locale.x86_64 (2,17 of hoger)
> - OpenSSL 3 (vereist op standaardlocatie op het besturingssysteem).

Voor installatie OpenSSL 3: de bibliotheken libcrypto.so.3 en libssl.so.3 moeten beschikbaar zijn in het standaard bibliotheekpad dat wordt vertegenwoordigd door de LD_LIBRARY_PATH omgevingsvariabele. Als ze op een niet-standaardlocatie zijn geïnstalleerd, moet u ervoor zorgen dat dit pad aan LD_LIBRARY_PATH wordt toegevoegd voordat u de server start.

#### Gevirtualiseerde omgeving {#virtualized-environment}


U kunt AEM Forms op JEE op een fysieke machine of een virtuele omgeving uitvoeren. Als u echter een probleem tegenkomt met AEM Forms in een virtuele omgeving, probeert u het probleem te repliceren op een fysieke computer. Neem contact op met Adobe Support voor een oplossing als het probleem zich blijft voordoen op de fysieke computer. Voor de problemen die u niet op een fysieke machine kunt repliceren, contacteer uw virtuele milieuverkoper.


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
1. AEM Forms on JEE biedt geen ondersteuning voor JBoss® op SUSE® Linux® Enterprise Server 12. Alleen IBM® WebSphere® wordt ondersteund op SUSE® Linux® Enterprise Server 12.
1. AEM Forms op JEE biedt geen ondersteuning voor JDK met JBoss® anders dan Oracle Java™ SE.
1. AEM Forms on JEE biedt geen ondersteuning voor JDK met IBM® WebSphere®, behalve IBM® JDK.
1. CRX-repository ondersteunt persistentie van het type TarMK, MongoDB en relationele databases (RDBMK). U kunt geen twee verschillende databasesystemen hebben tussen de toepassingsserver en de CRX-opslagplaats. Op een AEM Forms op JEE-omgeving kunt u echter MongoMK gebruiken met CRX-repository en een ondersteunde relationele database met toepassingsserver.
@@ -432,12 +359,12 @@ Houd rekening met de volgende uitzonderingen wanneer u een platform kiest voor het instellen van uw AEM F
1. JDK-versies hoger dan 1.8.0_281 worden niet ondersteund voor WebLogic-server. (FORMS-8498)
1. JDK 11.0.20 wordt niet ondersteund voor de installatie van AEM Forms op JEE Installer. Alleen JDK 11.0.19 of eerdere versies worden ondersteund voor de installatie van AEM Forms op JEE Installer.

1. [!DNL Microsoft® Windows Server 2019] ondersteunt [!DNL MySQL 5.7] en [!DNL JBoss® EAP 7.1] niet, [!DNL Microsoft® Windows Server 2019] ondersteunt geen kant-en-klare installaties voor [!DNL Experience Manager Forms Service Pack 6.5.10.0 and later] . (CQDOC-18312)


Houd rekening met de volgende punten wanneer u software kiest voor Adobe AEM Forms bij JEE-implementaties:


- AEM Forms on JEE ondersteunt updates, patches en repareert pakketten boven op de opgegeven primaire en secundaire versie van ondersteunde software. Bijwerken naar de volgende hoofd- of subversie wordt echter alleen ondersteund als dit is opgegeven.
- Clustergebaseerde installaties ondersteunen TarMK-persistentie niet. Voor informatie over gesteunde persistentie, zie [ het Kiezen van een persistentietype voor een installatie van AEM Forms ](/help/forms/using/choosing-persistence-type-for-aem-forms.md).
- AEM Forms op JEE steunt diverse derdesoftware zoals per Adobe [ het Beleid van de de softwaresteun van de Derde ](../../forms/using/aem-forms-jee-supported-platforms.md#p-third-party-patch-support-policy-p).
@@ -449,274 +376,219 @@ Houd rekening met de volgende punten wanneer u software kiest voor Adobe AEM

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
  <td>2019 <br /> </td>
 </tr>
</tbody>
</table>


### Steun voor Cordova {#support-for-cordova}


AEM Forms App ondersteunt nu de Apache Cordova. Hier volgen de platformspecifieke versies van Cordova die worden ondersteund:


- Apache Cordova 6.4.0
- Cordova iOS 4.3.0
- Cordova Android™ 6.0.0
- Cordova Windows 4.4.3

### Overwegingen voor PDF Generator

<table>
<tbody>
 <tr>
  <th><p><strong>Product</strong></p> </th>
  <th><p><strong>Ondersteunde indelingen voor conversie naar PDF</strong></p> </th>
 </tr>
 <tr>
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html"> Acrobat Pro DC </a> recentste versie</td>
   <td>XPS, afbeeldingsindelingen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML en HTM</td>
  </tr>
 <tr>
  <td>Microsoft® Office 2021  </td>
  <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF en TXT</td>
 </tr>
 </tr>

<tr>
  <td>WordPerfect 2020 <br /> </td>
  <td>WP, WPD</td>
 </tr>
 <tr>
  <td>Microsoft® Publisher 2019 <br /> </td>
  <td>PUB</td>
 </tr>
 <tr>
  <td>Microsoft® Publisher 2021 <br /> </td>
  <td>PUB</td>
 </tr>
 <tr>
  <td>OpenOffice 4.1.10</td>
  <td>ODT, ODP, ODS, ODG, ODF, SXW, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, afbeeldingsindelingen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM F en TXT</td>
 </tr>
</tbody>
</table>


>[!NOTE]
>
>PDF Generator ondersteunt alleen Engelse, Franse, Duitse en Japanse versies van de ondersteunde besturingssystemen en toepassingen.
>
>Daarnaast:
>
>- Voor PDF Generator is Adobe Acrobat Pro DC (32-bits) vereist om de conversie uit te voeren.
>- PDF Generator ondersteunt alleen de 32-bits versie van Microsoft® Office Professional Plus en andere software die vereist is voor conversie.
>- De Microsoft® Office Professional Plus-installatie kan gebruikmaken van een volumelicentie op basis van Retail of MAK/KMS/AD.
>- Als een Microsoft® Office-installatie om welke reden dan ook gedeactiveerd of zonder licentie wordt, zoals een installatie met volumelicentie die binnen een bepaalde periode geen KMS-host kan vinden, kunnen conversies mislukken totdat de installatie opnieuw in licentie wordt gegeven en opnieuw wordt geactiveerd.
>- PDF Generator ondersteunt Microsoft® Office 365 niet.
>- PDF Generator ondersteunt de 32-bits versie van OpenOffice op het Linux®-besturingssysteem.
>- PDF Generator-conversies voor OpenOffice worden alleen ondersteund in Windows en Linux®.
>- De functies OCR PDF, Optimize PDF en Export PDF worden alleen ondersteund in Windows.
>- Een versie van Acrobat wordt meegeleverd met AEM Forms om PDF Generator-functionaliteit in te schakelen. De gebundelde versie mag alleen via programmacode toegankelijk zijn met AEM Forms, tijdens de looptijd van de AEM Forms-licentie, voor gebruik met AEM Forms PDF Generator. Voor meer informatie, zie het productbeschrijving van AEM Forms zoals per uw plaatsing ([ op-Premise ](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) of [ Managed Services ](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))&quot;
>- PDF Generator service biedt geen ondersteuning voor Microsoft® Windows 10.
>- PDF Generator kan bestanden niet converteren met Microsoft® Visio 2019.
>- PDF Generator kan bestanden niet converteren met Microsoft® Project 2019.

PDF Generator ondersteunt alleen de 32-bits versie van Microsoft® Office Professional Plus en andere software die vereist is voor conversie.


De Microsoft® Office Professional Plus-installatie kan gebruikmaken van een volumelicentie op basis van Retail of MAK/KMS/AD.


Als een Microsoft® Office-installatie om welke reden dan ook gedeactiveerd of zonder licentie wordt, zoals een installatie met volumelicentie die binnen een bepaalde periode geen KMS-host kan vinden, kunnen conversies mislukken totdat de installatie opnieuw in licentie wordt gegeven en opnieuw wordt geactiveerd.

<!-- Removed lines: >- PDF Generator fails to convert files using Microsoft&reg; Visio 2019. You can continue to use Microsoft&reg; Visio 2016 to convert .VSD and .VSDX files.
>- PDF Generator fails to convert files using Microsoft&reg; Project 2019. You can continue to use Microsoft&reg; Project 2016 to convert .MPP files.-->


### Uitzonderingen op toegankelijkheidsondersteuning {#exceptions-to-accessibility-support}


De volgende subsystemen van AEM Forms zijn niet [ 508 ](https://www.section508.gov/) volgzaam:


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
  <td>Intel Xeon® E5-2680, 2.4-GHz processor of equivalent <br /> VMWare ESX 5.1 of hoger <br /> RAM: 6 GB (64-bits besturingssysteem met 64-bits JVM) <br /> vrije schijfruimte: 15 GB tijdelijke ruimte plus 22 GB <br /> voor AEM Forms op JEE</td>
 </tr>
 <tr>
  <td>SUSE® Linux® Enterprise Server</td>
  <td>Intel Xeon® E5-2670v2, 1 vCPU, 2,5 GHz processor <br /> AWS m3.medium (3 Ecu's) <br /> RAM: 6 GB (64-bits besturingssysteem met 64-bits JVM) <br /> vrije schijfruimte: 6 GB tijdelijke ruimte plus 22 GB <br /> voor AEM Forms op JEE</td>
 </tr>
 <tr>
  <td>Red Hat® Enterprise Linux®</td>
  <td>Intel Xeon® E5-2670v2, 1 vCPU, 2,5 GHz processor <br /> AWS m3.medium (3 Ecu's) <br /> RAM: 6 GB (64-bits besturingssysteem met 64-bits JVM) <br /> vrije schijfruimte: 6 GB tijdelijke ruimte plus 22 GB <br /> voor AEM Forms op JEE <br /> </td>
 </tr>
 <tr>
  <td>Hardwarevereisten voor een kleine productieomgeving</td>
  <td>
   <ul>
    <li><strong> Intel® aangedreven milieu </strong>: Intel Xeon® E5-2680, 2.4 GHz of groter. Het gebruik van een dual core processor zal de prestaties verder verbeteren</li>
    <li><strong> Geheugen: </strong> 4 GB <br /> </li>
   </ul> </td>
 </tr>
</tbody>
</table>


Zie voor aanvullende vereisten:

- [ vereisten van het Systeem voor enig-server AEM Forms op plaatsing JEE ](https://www.adobe.com/go/learn_aemforms_sysreq_single_65)
- [ vereisten van het Systeem voor gegroepeerde AEM Forms op plaatsing JEE ](https://www.adobe.com/go/learn_aemforms_sysreq_cluster_65)


### Adobe Acrobat en Adobe Reader {#adobe-acrobat-and-adobe-reader}


<table>
<tbody>
 <tr>
  <th><p><strong>Acrobat en Adobe Reader (basis)</strong></p> </th>
  <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
 </tr>
 <tr>
  <td>Acrobat 2020 (klassieke track)</td>
  <td>Versie 20.004.3006 of hoger <br /> </td>
 </tr>
 </tbody>
</table>


>[!NOTE]
>
>De productfamilie van Acrobat DC introduceert twee tracks voor zowel Acrobat als Reader die verschillende producten zijn: &quot;Klassiek&quot; en &quot;Doorlopend&quot;. Voor details en een vergelijking van de twee sporen, zie [ https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/whatsnewdc.html ](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/whatsnewdc.html).

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


- Schijfruimte voor installatie: 1,7 GB alleen voor Workbench, 2,7 GB op één station voor een volledige installatie van Workbench, Designer en de samplingverzameling 400 MB voor tijdelijke installatiemappen - 200 MB in de map met gebruikerstempels en 200 MB in de tijdelijke map van Windows. Als al deze locaties zich op één station bevinden, moet er tijdens de installatie 1,5 GB aan ruimte beschikbaar zijn. De naar de tijdelijke mappen gekopieerde bestanden worden verwijderd wanneer de installatie is voltooid.


- Geheugen voor het uitvoeren van Workbench: 2 GB RAM
- Hardwarevereisten: Intel® Pentium® 4- of AMD®-equivalent, 1-GHz processor
- Minimale monitorresolutie van 1024 x 768 pixels of hoger met 16-bits kleur of hoger
- TCP/IPv4- of TCP/IPv6-netwerkverbinding met de AEM Forms op JEE-server
- U moet over beheerdersrechten beschikken om Workbench in Windows te installeren. Als u een niet-beheerdersaccount installeert, vraagt het installatieprogramma u om de referenties voor een geschikte account.


### Designer {#designer}


- Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server, Microsoft® Windows® 10 of Windows® 11
- Processor van 1 GHz of sneller met ondersteuning voor PAE, NX en SSE2.
- 1 GB RAM voor 32-bits of 2 GB RAM voor 64-bits besturingssysteem
@@ -729,49 +601,45 @@ Voor aanvullende vereisten, zie:
- Beheerdersrechten voor het installeren van Designer
- Microsoft® Visual C++ 2019 (VC 14.28 of hoger) 32-bits runtime


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
>- Correspondence Management ondersteunt geen Windows® Internet Explorer 9.0 voor AEM 6.1-formulieren.
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
  <td>Microsoft® Edge <br /> </td>
  <td>Alle updates <br /> </td>
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


| **Platform** | **Ondersteunde Apparaten** |
| ----------------- | ------------------------------------------------------------------------------------------------------------------- |
| Apple iOS | Apple iPhone, iPad, iPad Air en iPad mini met iOS 15.1 en hoger. |
| Google Android™ | Android™ 5.1 en hoger. De AEM Forms-app is gecertificeerd voor Samsung Galaxy-tablets van 7 en 10 inch en voor populaire smartphones. |
| Microsoft® Windows | Microsoft® Surface devices, tablets, notebooks en desktops met Microsoft® Windows 10 besturingssysteem. |


### Adobe Document Security Extension for Microsoft® Office {#adobe-rights-management-extension-for-microsoft-office}


Klik [ hier ](https://www.adobe.com/products/livecycle/rightsmanagement/extension/downloads.html) om de systeemvereisten voor de Uitbreiding van de Veiligheid van het Document van Adobe voor Microsoft® Office te zien.


### Uitzonderingen op clientondersteuning {#exceptions-to-client-support}


AEM Forms on JEE ondersteunt updates, patches en repareert pakketten boven op de opgegeven primaire en secundaire versie van ondersteunde software. Bijwerken naar de volgende hoofd- of subversie wordt echter alleen ondersteund als dit is opgegeven.


## Flardondersteuningsbeleid van derden {#third-party-patch-support-policy}


De softwarevereisten van derden voor AEM Forms op JEE worden beschreven in het gedeelte &quot;Systeemvereisten&quot; van hun respectieve productdocumenten. Heb toegang tot alle documentatie van [ https://adobe.com/go/learn_aemforms_documentation_65 ](https://adobe.com/go/learn_aemforms_documentation_65).


AEM Forms op de referentieplatforms van derden van JEE vermeldt het specifieke patchniveau van de infrastructuur van derden dat tijdens de ontwikkeling en release van AEM Forms op JEE actueel was, en van het minimale patchniveau/servicepack van de infrastructuur die door die versie van AEM Forms op JEE wordt ondersteund.


Adobe biedt bij de release ondersteuning voor urgente of aanbevolen patches die door externe leveranciers worden uitgegeven, ervan uitgaande dat externe leveranciers achterwaartse compatibiliteit met de versies garanderen die AEM Forms op JEE ondersteunt. Adobe biedt alleen ondersteuning voor patches die worden vrijgegeven na het minimale patchniveau dat in de AEM Forms in JEE-documentatie is vermeld.


Soms biedt Adobe geen ondersteuning voor updates van derden die belangrijke functionaliteit wijzigen en dus geen ondersteuning bieden voor volledige achterwaartse compatibiliteit. Voor details op de gesteunde updates, zie [ Gesteunde flarddefinities ](https://helpx.adobe.com/aem-forms/aem-forms-third-party-software-patch.html) voor specifieke verkopersproducten en de flardtypes Adobe steunen.


Onder omstandigheden buiten de controle van Adobe, kunnen de derdepatches die achterwaartse verenigbaarheid eisen negatieve gevolgen voor de producten van Adobe of klantenmilieu&#39;s hebben. In dergelijke gevallen raadt Adobe klanten aan de gevolgen van een noodpatch van een derde te beoordelen voordat ze deze op kritieke systemen toepassen. Adobe werkt met derden samen door redelijke zakelijke inspanningen te leveren om dergelijke problemen op te lossen, hetzij via normale Adobe-ondersteuningsprogramma&#39;s, hetzij door derden die het probleem in hun patch verhelpen. Dit garandeert niet dat een nieuw vrijgegeven patch van derden die door Adobe wordt ondersteund, werkt zoals wordt beschreven door de leverancier of met AEM Forms op JEE.


Adobe behoudt zich het recht voor om de referentieplatforms van derden die worden ondersteund door een AEM Forms bij JEE-release en de door hen ondersteunde patchdefinities op een bepaald punt te wijzigen.


Aanvullende informatie voor patches van derden vindt u ook op de website van Adobe Enterprise Support op de website van knowledgebase-artikelen over uw product.


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
### Release 6.5.23.0 (June 06, 2025)
| Added Support | Removed Support | Deprecated Support |
| -------------- | --------------- | ------------------- |
| MongoDB Enterprise 7.0 |    MongoDB Enterprise 5.0 | MongoDB Enterprise 6.0 |
| MYSQL 8.4 |SUSE&reg; Linux&reg; Enterprise Server 12 (64-bit) | MYSQL 8.0.27 |
| Microsoft&reg; SQL Server 2022 | |Microsoft&reg; SQL Server 2019 |
| Microsoft&reg; SQL Server JDBC driver 12.8 | | Microsoft&reg; SQL Server JDBC driver 8.2 |
| Microsoft&reg; Office 2021 | | Microsoft&reg; Office 2019 |
| Red Hat&reg; Enterprise Linux&reg; 9 (Kernel 4.x) (64-bit) | |Red Hat&reg; Enterprise Linux&reg; 8 (Kernel 4.x) (64-bit)  |
-->

### Release 6.5.23.0 (6 juni 2025)

| Toegevoegde ondersteuning | Verwijderde ondersteuning | Verouderde ondersteuning |
| -------------- | --------------- | ------------------- |
| MongoDB Enterprise 7.0 | MongoDB Enterprise 5.0 | MongoDB Enterprise 6.0 |
| MYSQL 8.4 | SUSE® Linux® Enterprise Server 12 (64-bits) | MYSQL 8.0.27 |
| Microsoft® SQL Server 2022 | Centos 7 | Microsoft® SQL Server 2019 |
| Microsoft® SQL Server JDBC-stuurprogramma 12.10.0 | Red Hat® Enterprise Linux® 7 (Kernel 4.x) (64-bits) | Microsoft® SQL Server JDBC-stuurprogramma 8.2 |
| Red Hat® Enterprise Linux® 9 (Kernel 4.x) (64-bits) | | Red Hat® Enterprise Linux® 8 (Kernel 4.x) (64-bits) |

### Release 6.5.22.0 (29 november 2024)


| Toegevoegde ondersteuning | Verwijderde ondersteuning | Verouderde ondersteuning |
| -------------- | --------------- | ------------------- |
| SUSE® Linux® Enterprise Server 15 SP6 (64-bits) | |  |

### Release 6.5.21.0 (13 juni 2024)

| Toegevoegde ondersteuning | Verwijderde ondersteuning | Verouderde ondersteuning |
| -------------- | --------------- | ------------------- |
| Microsoft® Office 2021 |  |  |

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
|  | Acrobat 2017 (Classic track) versie 17.011.30078 of hoger |  |

### Release 6.5.13.0 (2 juni 2022)


| Toegevoegde ondersteuning | Verwijderde ondersteuning | Verouderde ondersteuning |
| -------------- | --------------- | ------------------- |
|  |  | Microsoft® SharePoint 2016 |

### Release 6.5.12.0 (3 maart 2022)


| Toegevoegde ondersteuning | Verwijderde ondersteuning | Verouderde ondersteuning |
| -------------- | --------------- | ------------------- |
|  | IBM® J9 Virtual Machine (build 2.8, JRE 1.8.0) | MongoDB Enterprise 4.0 |
|  | | Microsoft® SQL Server 2016 |
|  | | Microsoft® Windows Server 2016 |

### Release 6.5.10.0 (1 september 2022)


| Toegevoegde ondersteuning | Verwijderde ondersteuning | Verouderde ondersteuning |
| -------------- | --------------- | ------------------- |
| Oracle Java™ SE 11 (64-bits) SDK voor toepassingsserver JBoss® EAP 7.4. | | [ Adobe Acrobat 2017 - de steun van de Kern voor Adobe Acrobat 2017 eindigt op 6 juni 2022.](https://helpx.adobe.com/support/programs/eol-matrix.html) |
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