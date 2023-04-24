---
title: Technische vereisten
description: Een lijst met de ondersteunde client- en serverplatforms voor Adobe Experience Manager.
topic-tags: platform
exl-id: 47529b9a-c4e5-434f-ac26-b01714ff863b
source-git-commit: fe9c77644daf3669df8cca18e65fb0f6918f853b
workflow-type: tm+mt
source-wordcount: '3513'
ht-degree: 0%

---

# Technische vereisten{#technical-requirements}

Adobe ondersteunt (AEM) Adobe Experience Manager op de platforms, zoals wordt beschreven in de volgende informatie in dit document.

Neem contact op met de leverancier van het platform voor alle problemen die betrekking hebben op het platform.

>[!NOTE]
>
>Afhankelijk van het platform waarop u AEM installeert, kunnen er verschillende reeksen vereisten voor gebruikersbeheer zijn.

## Vereisten {#prerequisites}

Minimumeisen voor de installatie van Adobe Experience Manager:

* Geïnstalleerd Java™-Platform, Standard Edition JDK of andere ondersteunde onderdelen [Java™ Virtuele machines](#java-virtual-machines)
* QuickStart-bestand voor Experience Manager (zelfstandige WAR voor JAR- of webtoepassingsimplementatie)

### Minimale groottevereisten {#minimum-sizing-requirements}

Minimumvereisten voor Adobe Experience Manager:

* 5 GB vrije schijfruimte in de installatiemap
* 2 GB geheugen

>[!NOTE]
>
>* Voor het gebruik van digitale middelen is meer basisgeheugen nodig. Zie [Implementeren en onderhouden](/help/sites-deploying/deploy.md#default-local-install) voor meer informatie.
>* [AEM Forms-invoegtoepassing](/help/forms/using/installing-configuring-aem-forms-osgi.md) vereist 15 GB tijdelijke ruimte.
>


Zie voor meer informatie de [Richtlijnen voor hardwareaanpassing](/help/managing/hardware-sizing-guidelines.md).

### Ondersteuningsniveaus {#support-levels}

In dit document worden de ondersteunde client- en serverplatforms voor Adobe Experience Manager vermeld. Adobe biedt verschillende ondersteuningsniveaus, zowel voor aanbevolen configuraties als voor andere configuraties.

### Ondersteunde configuraties {#supported-configurations}

Adobe raadt deze configuraties aan en biedt volledige ondersteuning als onderdeel van de standaard overeenkomst voor softwareonderhoud.

<table>
 <tbody>
  <tr>
   <td>Ondersteuningsniveau</td>
   <td>Beschrijving<br /> </td>
  </tr>
  <tr>
   <td><strong>A: Ondersteund</strong></td>
   <td>Adobe biedt volledige ondersteuning en onderhoud voor deze configuratie. Deze configuratie wordt gedekt door het kwaliteitsborgingsproces van Adobe.</td>
  </tr>
  <tr>
   <td><strong>R: Beperkte ondersteuning</strong></td>
   <td>Om ervoor te zorgen dat het project van de klant slaagt, biedt Adobe volledige steun binnen een beperkt steunprogramma, dat vereist dat aan specifieke voorwaarden wordt voldaan. Voor ondersteuning op R-niveau is een formeel verzoek van de klant en een bevestiging door Adobe vereist. Neem voor meer informatie contact op met de klantenservice van Adobe.</td>
  </tr>
 </tbody>
</table>

### Niet-ondersteunde configuraties {#unsupported-configurations}

| Ondersteuningsniveau | Beschrijving |
|---|---|
| **Z: Niet ondersteund** | De configuratie wordt niet ondersteund. Adobe legt geen verklaringen over of de configuratie werkt, en steunt het niet. |

## Ondersteunde Platforms {#supported-platforms}

### Java™ Virtuele machines {#java-virtual-machines}

De toepassing vereist dat een Java™ Virtual Machine wordt uitgevoerd, die wordt geleverd door de JDK-distributie (Java™ Development Kit).

Adobe Experience Manager werkt met de volgende versies van Java™ Virtual Machines:

>[!CAUTION]
>
>Volg de beveiligingsbulletins van de Java™-leverancier. Dit garandeert de veiligheid en beveiliging van productieomgevingen. Installeer ook altijd de nieuwste Java™-updates.

| **Platform** | **Ondersteuningsniveau** | **Koppeling** |
|---|---|---|
| Oracle Java™ SE 17 JDK | Z: Niet ondersteund `[1]` |
| Oracle Java™ SE 11 JDK - 64-bits | A: Ondersteund `[1]` | [Downloaden](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?fulltext=Oracle*+JDK*+11*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=24&lt;td>) |
| Oracle Java™ SE 10 JDK | Z: Niet ondersteund `[1]` |
| Oracle Java™ SE 9 JDK | Z: Niet ondersteund `[1]` |
| Oracle Java™ SE 8 JDK - 64-bits | A: Ondersteund `[1]` | [Downloaden](https://experience.adobe.com/#/downloads/content/software-distribution/en/general.html?fulltext=Oracle*+JDK*+8*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=10) |
| IBM® J9 VM - build 2.9, JRE 1.8.0 | A: Ondersteund `[2]` |
| IBM® J9 VM - build 2.8, JRE 1.8.0 | A: Ondersteund `[2]` |
| Azul Zulu OpenJDK 11 - 64-bits | A: Ondersteund `[3]` |  |
| Azul Zulu OpenJDK 8 - 64-bits | A: Ondersteund `[3]` |  |

1. Oracle is overgestapt op een LTS-model (Long Term Support) voor Oracle Java™ SE-producten. Java™ 9, Java™ 10 en Java™ 12 zijn niet-LTS releases per Oracle (zie [Ondersteuning voor roadmap voor oracle Java™ SE](https://www.oracle.com/technetwork/java/eol-135779.html)). Om AEM in productieomgeving te implementeren, biedt Adobe alleen ondersteuning voor de LTS-versies van Java™. Ondersteuning en distributie van het Oracle Java™ SE JDK, inclusief alle onderhoudsupdates van LTS-releases na afloop van de openbare updates, wordt door Adobe direct ondersteund voor alle AEM klanten die de Oracle Java™ SE-technologie gebruiken. Zie de [Java™-ondersteuningsbeleid voor Adobe Experience Manager](assets/Java_Policy_for_Adobe_Experience_Manager.pdf).
   **Belangrijk: Oracle Java™ 11 wordt minimaal ondersteund tot september 2026. Ondersteuning voor Oracle Java™ 17 is in voorbereiding.**

1. IBM® JRE wordt alleen ondersteund in combinatie met WebSphere® Application Server.

1. Azul Zulu OpenJDK LTS versies worden gesteund voor plaatsingen op-gebouw AEM die met versie 6.5 SP9 beginnen. Voor de ondersteuning en distributie van de Azul Zulu JDK LTS-versies moet een directe licentie worden verleend door klanten van Adobe.


### Opslag en duurzaamheid {#storage-persistence}

Er zijn verschillende opties om de opslagplaats van Adobe Experience Manager te implementeren. Zie de volgende lijst voor ondersteunde technologieën en opslagopties.

| **Platform** | **Beschrijving** | **Ondersteuningsniveau** |
|---|---|---|
| **Bestandssysteem met TAR-bestanden** `[1]` | Bewaarplaats | A: Ondersteund |
| **Bestandssysteem met Datastore** `[1]` | Binden | A: Ondersteund |
| Binaire bestanden opslaan in TAR-bestanden op bestandssysteem `[1]` | Binden | Z: Niet ondersteund voor productie |
| Amazon S3 | Binden | A: Ondersteund |
| Microsoft® Azure Blob Storage | Binden | A: Ondersteund |
| MongoDB Enterprise 4.4 | Bewaarplaats | A: Ondersteund `[2, 3, 4]` |
| MongoDB Enterprise 4.2 | Bewaarplaats | A: Ondersteund `[2, 3, 4]` |
| MongoDB Enterprise 4.0 | Bewaarplaats | Z: Niet ondersteund |
| MongoDB Enterprise 3.6 | Bewaarplaats | Z: Niet ondersteund |
| MongoDB Enterprise 3.4 | Bewaarplaats | Z: Niet ondersteund |
| IBM® DB2® 10.5 | Opslagplaats en Forms-database | R: Beperkte ondersteuning `[5]` |
| Database van oracle 12c (12.1.x) | Opslagplaats en Forms-database | R: Beperkte ondersteuning |
| Microsoft® SQL Server 2016 | Forms-database | A: Ondersteund |
| **Apache Lucene (QuickStart ingebouwd)** | Zoekservice | A: Ondersteund |
| Apache Solr | Zoekservice | A: Ondersteund |

1. &#39;Bestandssysteem&#39; omvat blokopslag die voldoet aan POSIX. Omvat de technologie van de netwerkopslag. Houd er rekening mee dat de prestaties van het bestandssysteem kunnen variëren en van invloed zijn op de algehele prestaties. Laad AEM met het netwerk/externe bestandssysteem.
1. Voor MongoDB Enterprise versie 4.2 en 4.4 is minimaal AEM 6.5 SP9 vereist.
1. Delen via MongoDB wordt niet ondersteund in AEM.
1. MongoDB Storage Engine WiredTiger wordt alleen ondersteund.
1. Ondersteund voor AEM Forms-upgradeklanten. Niet ondersteund voor nieuwe installaties.

>[!NOTE]
Zie [Gemeenschappen inzetten](/help/communities/deploy-communities.md) voor aanvullende informatie over de AEM Communities-capaciteit.

>[!NOTE]
MongoDB is software van derden en is niet opgenomen in het AEM licentiepakket. Zie voor meer informatie de [MongoDB-licentiebeleid](https://www.mongodb.com/community/licensing) pagina.
Om optimaal gebruik te kunnen maken van uw AEM met MongoDB, raadt Adobe aan een licentie te verlenen voor de MongoDB Enterprise-versie, zodat deze profiteert van professionele ondersteuning. Zie [Aanbevolen implementaties](/help/sites-deploying/recommended-deploys.md#prerequisites-and-recommendations-when-deploying-aem-with-mongomk) voor meer informatie .
De licentie bevat een standaard replicaset, die bestaat uit één primaire en twee secundaire instanties die kunnen worden gebruikt voor de auteur of de publicatieimplementaties.
Als u zowel de auteur als de publicatie op MongoDB wilt uitvoeren, moet u twee aparte licenties aanschaffen.
De klantenservice van Adobe helpt kwalificerende problemen met betrekking tot het gebruik van MongoDB met AEM.
Zie voor meer informatie de [Pagina MongoDB voor Adobe Experience Manager](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).

>[!NOTE]
Ondersteunde relationele databases zoals hierboven vermeld, zijn software van derden en zijn niet opgenomen in het AEM licentiepakket.
Om AEM 6.5 met een gesteunde relationele gegevensbestand in werking te stellen, wordt een afzonderlijk steuncontract met een gegevensbestandverkoper vereist. De klantenservice van Adobe helpt kwalificerende problemen met betrekking tot het gebruik van relationele databases met AEM 6.5.
**De meeste relationele gegevensbanken worden momenteel ondersteund in niveau-R op AEM 6.5, dat vergezeld gaat van steuncriteria en een steunprogramma zoals vermeld in de bovenstaande beschrijving van niveau-R.**

### Servlet-engines/toepassingsservers {#servlet-engines-application-servers}

Adobe Experience Manager kan worden uitgevoerd als een zelfstandige server (het QuickStart JAR-bestand) of als een webtoepassing binnen een externe toepassingsserver (het WAR-bestand).

De minimaal vereiste versie van de servlet-API is Servlet 3.1

| Platform | Ondersteuningsniveau |
|---|---|
| **QuickStart ingebouwde Servlet Engine (Jetty 9.4)** | A: Ondersteund |
| Oracle WebLogic Server 12.2 (12cR2) | Z: Niet ondersteund |
| IBM® WebSphere® Application Server Continuous Delivery (LibertyProfile) met Web Profile 7.0 en IBM® JRE 1.8 | R: Beperkte steun voor nieuwe contracten `[2]` |
| IBM® WebSphere® Application Server 9.0 en IBM® JRE 1.8 | R: Beperkte steun voor nieuwe contracten `[1]` `[2]` |
| Apache Tomcat 8.5.x | R: Beperkte steun voor nieuwe contracten `[2]` |
| JBoss® EAP 7.2.x met JBoss® Application Server | Z: Niet ondersteund |
| JBoss® EAP 7.1.4 met JBoss® Application Server | R: Beperkte steun voor nieuwe contracten `[1]` `[2]` |
| JBoss® EAP 7.0.x met JBoss® Application Server | Z: Niet ondersteund |

1. Aanbevolen voor implementaties met AEM Forms.
1. De aanvang AEM 6.5 plaatsingen op toepassingsservers beweegt zich aan Beperkte Steun. Bestaande klanten kunnen upgraden naar AEM 6.5 en blijven toepassingsservers gebruiken. Voor nieuwe klanten wordt het geleverd met steuncriteria en een steunprogramma zoals die in de hierboven beschreven Niveau-R beschrijving worden vermeld.

### Serverbesturingssystemen {#server-operating-systems}

Adobe Experience Manager werkt met de volgende serverplatforms voor productieomgevingen:

| **Platform** | **Ondersteuningsniveau** |
|---|---|
| **Linux®, gebaseerd op Red Hat® distributie** | A: Ondersteund `[1]` `[3]` |
| Linux®, gebaseerd op Debian distribution incl. Ubuntu | A: Ondersteund `[1]` `[2]` |
| Linux®, gebaseerd op SUSE®-distributie | A: Ondersteund `[1]` |
| Microsoft® Windows Server 2019 `[4]` | R: Beperkte steun voor nieuwe contracten `[5]` |
| Microsoft® Windows Server 2016 `[4]` | R: Beperkte steun voor nieuwe contracten `[5]` |
| Microsoft® Windows Server 2012 R2 | Z: Niet ondersteund |
| Oracle Solaris™ 11 | Z: Niet ondersteund |
| IBM® AIX® 7.2 | Z: Niet ondersteund |

1. Linux® Kernel 2.6, 3. x, 4. x en 5. x bevat derivaten van Red Hat®-distributie, waaronder Red Hat® Enterprise Linux®, CentOS, Oracle Linux® en Amazon Linux®. AEM Forms-add-onfuncties worden alleen ondersteund in CentOS 7, Red Hat® Enterprise Linux® 7, Red Hat® Enterprise Linux® 8 en Red Hat® Enterprise Linux® 9.
1. AEM Forms wordt ondersteund op Ubuntu 20.04 LTS.
1. Linux®-distributie ondersteund door Adobe Managed Services.
1. Microsoft® Windows-productieimplementaties worden ondersteund voor klanten die upgraden naar versie 6.5 en voor niet-productiegebruik. Nieuwe implementaties zijn op aanvraag voor AEM Sites en Assets.
1. AEM Forms wordt ondersteund op Microsoft® Window Server zonder de ondersteuningsbeperkingen.

>[!NOTE]
Als u AEM Forms 6.5 installeert, zorg ervoor u volgende 32 beetje Microsoft® Visuele C++ redistributable geïnstalleerd hebt.
* Microsoft® Visual C++ 2008 herdistribueerbaar
* Microsoft® Visual C++ 2010 herdistribueerbaar
* Microsoft® Visual C++ 2012 herdistribueerbaar
* Microsoft® Visual C++ 2013 herdistribueerbaar (vanaf 6.5)



### Virtuele en Cloud Computing-omgevingen {#virtual-cloud-computing-environments}

Adobe Experience Manager wordt ondersteund bij uitvoering in een virtuele machine in cloudcomputeromgevingen. Deze omgevingen zijn onder andere Microsoft® Azure en Amazon Web Services (AWS), die worden uitgevoerd in overeenstemming met de technische vereisten die op deze pagina worden vermeld, en volgens de standaardondersteuningsvoorwaarden voor Adobe.

Voor een cloud-native omgeving bekijkt u het nieuwste aanbod via de AEM productlijn: Adobe Experience Manager as a Cloud Service. Zie [Adobe Experience Manager as a Cloud Service-documentatie](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html?lang=en) voor meer informatie.

Adobe biedt ook Adobe Managed Services om AEM te implementeren in Azure of AWS. Adobe Managed Services biedt experts ervaring en vaardigheden voor het implementeren en gebruiken van AEM in deze cloud computing-omgevingen. Zie [aanvullende documentatie over Adobe Managed Services](https://business.adobe.com/products/experience-manager/managed-services.html?aemClk=t).

In alle andere gevallen van implementatie van AEM op Azure of AWS, of in elke andere cloud computing-omgeving, is ondersteuning van Adobe beperkt tot de virtuele computeromgeving. Die virtuele omgeving moet worden uitgevoerd in overeenstemming met de technische specificaties die op deze pagina worden vermeld. Elk gemeld probleem met betrekking tot AEM die in een van deze cloudomgevingen worden uitgevoerd, moet kunnen worden gereproduceerd onafhankelijk van elke cloudservice die specifiek is voor de cloud computing-omgeving. Dat wil zeggen, tenzij de cloudservice wordt ondersteund als onderdeel van de technische vereisten die op deze pagina worden vermeld, bijvoorbeeld Azure Blob-opslag of AWS S3.

Voor aanbevelingen voor de implementatie van AEM op Azure of AWS, buiten Adobe Managed Services, raadt Adobe u aan rechtstreeks met de cloud provider te werken. Of u werkt samen met Adobe-partners die de implementatie van AEM ondersteunen in de cloud-omgeving van uw keuze. De geselecteerde wolkenleverancier of partner is verantwoordelijk voor de rangschikkingsspecificaties, het ontwerp, en de implementatie van de architectuur, om aan uw specifieke prestaties, lading, scalability, en veiligheidsvereisten te voldoen.

### Dispatcher-Platforms (webservers) {#dispatcher-platforms-web-servers}

De Dispatcher is de component voor caching en taakverdeling. [Download de nieuwste versie van Dispatcher](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/release-notes.html?lang=en). Experience Manager 6.5 vereist Dispatcher versie 4.3.2 of hoger.

De volgende webservers worden ondersteund voor gebruik met Dispatcher versie 4.3.2:

| Platform | Ondersteuningsniveau |
|---|---|
| **Apache httpd 2.4.x** `[1,2]` | A: Ondersteund |
| Microsoft® IIS 10 (Internet Information Server) | A: Ondersteund |
| Microsoft® IIS 8.5 (Internet Information Server) | Z: Niet ondersteund |

1. Webservers die zijn gebaseerd op Apache httpd-broncode, bieden evenveel ondersteuning als de versie van httpd waarop deze is gebaseerd. In geval van twijfel, vraag Adobe om bevestiging van het steunniveau met betrekking tot het respectieve serverproduct. In de volgende gevallen:

   1. De HTTP-server is gemaakt met alleen officiële Apache-brondistributies, of
   1. De HTTP-server is geleverd als onderdeel van het besturingssysteem waarop deze wordt uitgevoerd. Voorbeelden: IBM® HTTP Server, Oracle HTTP Server

1. Dispatcher is niet beschikbaar voor Apache 2.4.x voor Windows-besturingssystemen.

## Ondersteunde client-Platforms {#supported-client-platforms}

### Ondersteunde browsers voor gebruikersinterface voor ontwerpen {#supported-browsers-for-authoring-user-interface}

De Adobe Experience Manager-gebruikersinterface werkt met de volgende clientplatforms. Alle browsers worden getest met de standaardset insteekmodules en invoegtoepassingen.

De AEM gebruikersinterface is geoptimaliseerd voor grotere schermen (doorgaans laptops en desktopcomputers) en tabletvormfactoren (zoals Apple iPad of Microsoft® Surface). De telefoonvormfactor wordt niet ondersteund.

>[!NOTE]
**Ondersteuning voor browsers met snelle releasecycli:**
De release van Mozilla Firefox, Google Chrome en Microsoft® Edge wordt elke paar maanden bijgewerkt. Adobe heeft zich ertoe verbonden updates beschikbaar te stellen voor Adobe Experience Manager om het supportniveau te handhaven zoals hieronder vermeld in de komende versies van deze browsers.

<table>
 <tbody>
  <tr>
   <td><strong>Browser</strong></td>
   <td><strong>Ondersteuning voor UI<br /> </strong></td>
   <td><strong>Ondersteuning voor klassieke gebruikersinterface</strong></td>
  </tr>
  <tr>
   <td><strong>Google Chrome (Evergreen)</strong></td>
   <td>A: Ondersteund</td>
   <td>A: Ondersteund</td>
  </tr>
  <tr>
   <td>Microsoft® Edge (Evergreen)</td>
   <td>A: Ondersteund</td>
   <td>A: Ondersteund</td>
  </tr>
  <tr>
   <td>Microsoft® Internet Explorer 11</td>
   <td>Z: Niet ondersteund</td>
   <td>Z: Niet ondersteund</td>
  </tr>
  <tr>
   <td>Mozilla Firefox (Evergreen)</td>
   <td>A: Ondersteund</td>
   <td>A: Ondersteund</td>
  </tr>
  <tr>
   <td>Mozilla Firefox laatste ESR [1]</td>
   <td>A: Ondersteund</td>
   <td>A: Ondersteund</td>
  </tr>
  <tr>
   <td>Apple Safari op macOS (Evergreen)</td>
   <td>A: Ondersteund</td>
   <td>A: Ondersteund</td>
  </tr>
  <tr>
   <td>Apple Safari 11.x op macOS</td>
   <td>Z: Niet ondersteund</td>
   <td>Z: Niet ondersteund</td>
  </tr>
  <tr>
   <td>Apple Safari op iOS 12.x</td>
   <td>A: Ondersteund [2]</td>
   <td>Z: Niet ondersteund</td>
  </tr>
  <tr>
   <td>Apple Safari op iOS 11.x</td>
   <td>Z: Niet ondersteund</td>
   <td>Z: Niet ondersteund</td>
  </tr>
 </tbody>
</table>

1. Uitgebreide ondersteuningsrelease van Firefox [Meer informatie over mozilla.org](https://www.mozilla.org/en-US/firefox/enterprise/)
1. ondersteuning voor Apple iPad

### Ondersteunde browsers voor websites {#supported-browsers-for-websites}

Over het algemeen is browserondersteuning voor websites die door AEM Sites worden weergegeven afhankelijk van de implementatie van AEM paginasjablonen, het ontwerp en de uitvoer van onderdelen. Daarom is deze ondersteuning van toepassing op de partij die deze onderdelen implementeert.

### WebDAV-clients {#webdav-clients}

**Microsoft® Windows 7+**

Wanneer u verbinding maakt met Microsoft® Windows 7+ met een AEM die niet met SSL is beveiligd, moet de basisverificatie via een onbeveiligd netwerk in Windows zijn ingeschakeld. Het vereist een verandering in de Registratie van Vensters van WebClient:

1. De registersubsleutel zoeken:

   * HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WebClient\Parameters

1. Voeg de BasisAuthLevel registratieingang aan deze subkey toe gebruikend een waarde van 2 of meer.

## Aanvullende opmerkingen bij Platforms {#additional-platform-notes}

Deze sectie bevat speciale notities en meer gedetailleerde informatie over het uitvoeren van Adobe Experience Manager en de invoegtoepassingen ervan.

### IPv4 en IPv6 {#ipv-and-ipv}

Alle elementen van Adobe Experience Manager (Instance, Dispatcher) kunnen in zowel IPv4- als IPv6-netwerken worden geïnstalleerd.

De bewerking is naadloos omdat er geen speciale configuratie vereist is. U specificeert een IP adres gebruikend het formaat dat aan uw netwerktype, indien nodig aangewezen is.

Wanneer een IP adres moet worden gespecificeerd, kunt u (zoals vereist) van het volgende selecteren:

* Een IPv6-adres. Bijvoorbeeld, `https://[ab12::34c5:6d7:8e90:1234]:4502`

* Een IPv4-adres. Bijvoorbeeld, `https://123.1.1.4:4502`

* Een servernaam. Bijvoorbeeld, `https://www.yourserver.com:4502`

* Het standaardgeval van `localhost` wordt geïnterpreteerd voor zowel IPv4 als IPv6 netwerkinstallaties. Bijvoorbeeld, `https://localhost:4502`

### Vereisten voor AEM invoegtoepassing Dynamic Media {#requirements-for-aem-dynamic-media-add-on}

AEM Dynamic Media is standaard uitgeschakeld. Zie hier [Dynamic Media inschakelen](/help/assets/config-dynamic.md#enabling-dynamic-media).

Als Dynamic Media ingeschakeld is, zijn de volgende aanvullende technische voorschriften van toepassing.

>[!NOTE]
Deze systeemvereisten **alleen** toepassen als u de Dynamic Media - hybride modus gebruikt; Dynamic Media - Hybride modus heeft een ingesloten imageserver, die alleen op bepaalde besturingssystemen is gecertificeerd.
Voor Dynamic Media-klanten die de Dynamic Media-Scene7-modus (dat wil zeggen: **dynamicmedia_scene7** &quot;run mode&quot;), zijn er geen aanvullende systeemvereisten; alleen dezelfde systeemvereisten als AEM. Dynamic Media - Scene7-modusarchitectuur gebruikt de op cloud gebaseerde beeldservice en niet de service die in AEM is ingesloten.

#### Hardware {#hardware}

De volgende hardwarevereisten zijn van toepassing voor zowel Linux® als Windows:

* Intel Xeon® of AMD® Opteron CPU met ten minste vier kernen
* Minstens, 16 GB RAM

#### Linux® {#linux}

Als u Dynamic Media op Linux® gebruikt, moet aan de volgende voorwaarden worden voldaan:

* Red Hat® Enterprise 7 of CentOS 7 en hoger met de nieuwste herstelpatches
* 64-bits besturingssysteem
* Wisselen uitgeschakeld (aanbevolen)
* SELinux uitgeschakeld (zie onderstaande opmerking)

>[!NOTE]
Als de landinstelling zo is ingesteld dat LC_CTYPE niet gelijk is aan `en_US.UTF-8`, werkt Dynamic Media niet. Om te zien wat zijn waarde is, typ &quot;scène&quot;bij de bevelherinnering. Als het niet behoorlijk plaatst, dan plaats de LC_CTYPE milieuvariabele aan het lege koord door &quot;uitvoer LC_CTYPE=&quot;te typen alvorens AEM in werking te stellen.

>[!NOTE]
**SELinux uitschakelen:** De service Image Serving werkt niet wanneer SELinux is ingeschakeld. Deze optie is standaard ingeschakeld. Als u dit probleem wilt verhelpen, bewerkt u de **/etc/selinux/config** en wijzig de SELinux-waarde van:
`SELINUX=enforcing` **tot** `SELINUX=disabled`

>[!NOTE]
**NUMA-architectuur:** Systemen met processors met AMD64 en Intel® EM64T worden doorgaans geconfigureerd als niet-uniforme geheugenarchitectuurplatforms (NUMA). Dat wil zeggen dat de kernel meerdere geheugenknooppunten samenstelt bij opstarttijd in plaats van één geheugenknooppunt te maken.
De meervoudige knoopaannemer kan in geheugenuitputting op één of meerdere knopen resulteren alvorens andere knopen worden uitgeput. Wanneer de geheugenuitputting gebeurt kan de pit besluiten om processen (bijvoorbeeld, de Server van het Beeld of de Server van het Platform) te doden alhoewel er beschikbaar geheugen is.
Daarom adviseert Adobe dat als u zulk een systeem in werking stelt dat u NUMA gebruikend **numa=off** laarsoptie om de kernel te vermijden die deze processen doden.

>[!NOTE]
**Serverhostnaam moet worden opgelost:** Zorg ervoor dat de hostnaam van de server kan worden omgezet naar een IP-adres. Als dat niet mogelijk is, voeg volledig - gekwalificeerde gastheernaam en het IP adres aan toe **/etc/hosts**:
`<ip address> <fully qualified hostname>`

#### Windows {#windows}

* Microsoft® Windows Server 2016
* Ruimte wisselen gelijk aan minstens tweemaal de hoeveelheid fysiek geheugen (RAM)

Als u Dynamic Media in Windows wilt gebruiken, installeert u Microsoft® Visual Studio 2010, 2013 en 2015 opnieuw distribueerbaar voor x64 en x86.

Voor Windows x64:

* Microsoft® Visual Studio 2010 opnieuw distribueerbaar bij [https://www.microsoft.com/en-us/download/details.aspx?id=26999](https://www.microsoft.com/en-us/download/details.aspx?id=26999)
* Microsoft® Visual Studio 2013 opnieuw distribueerbaar bij [https://www.microsoft.com/en-us/download/details.aspx?id=40784](https://www.microsoft.com/en-us/download/details.aspx?id=40784)
* Microsoft® Visual Studio 2015 opnieuw distribueerbaar krijgen op [https://www.microsoft.com/en-us/download/details.aspx?id=48145](https://www.microsoft.com/en-us/download/details.aspx?id=48145)

Voor Windows x86:

* Microsoft® Visual Studio 2010 opnieuw distribueerbaar bij [https://www.microsoft.com/en-us/download/details.aspx?id=26999](https://www.microsoft.com/en-us/download/details.aspx?id=26999)
* Microsoft® Visual Studio 2013 opnieuw distribueerbaar bij [https://www.microsoft.com/en-in/download/details.aspx?id=40769](https://www.microsoft.com/en-in/download/details.aspx?id=40769)
* Microsoft® Visual Studio 2015 opnieuw distribueerbaar krijgen op [https://www.microsoft.com/en-us/download/details.aspx?id=52685](https://www.microsoft.com/en-us/download/details.aspx?id=52685)

#### macOS {#macos}

* 10.9.x en hoger
* Alleen ondersteund voor proefversie en demo-doeleinden

### Eisen voor AEM Forms PDF Generator {#requirements-for-aem-forms-pdf-generator}

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
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html">Acrobat 2017 klassiek spoor</a> nieuwste versie (afgekeurd)</td>
   <td>XPS, afbeeldingsindelingen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM, DWG, DXF en DWF</td>
  </tr>
  <tr>
   <td>Microsoft® Office 2019</td>
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF en TXT</td>
  </tr>
  <tr>
   <td>Microsoft® Office 2016 (afgekeurd)</td>
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF en TXT</td>
  </tr>
  <tr>
   <td>WordPerfect 2020<br /> </td>
   <td>WP, WPD</td>
  </tr>
  <tr>
   <td>Microsoft® Office Visio 2016 (afgekeurd)<br /> </td>
   <td>VSD, VSDX</td>
  </tr>
  <tr>
   <td>Microsoft® Publisher 2019<br /> </td>
   <td>PUB</td>
  </tr>
  <tr>
   <td>Microsoft® Publisher 2016 (afgekeurd)<br /> </td>
   <td>PUB</td>
  </tr>
  <tr>
   <td>Microsoft® Project 2016 (afgekeurd)<br /> </td>
   <td>MPP</td>
  </tr>
  <tr>
   <td>OpenOffice 4.1.10</td>
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXC, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, afbeeldingsindelingen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC) HTML, , HTM, RTF en TXT</td>
  </tr>
  <tr>
   <td>OpenOffice 4.1.2 (afgekeurd)</td>
   <td>ODT, ODP, ODS, ODG, ODF, SXW, SXC, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, afbeeldingsindelingen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC) HTML, , HTM, RTF en TXT</td>
  </tr>  
 </tbody>
</table>

>[!NOTE]
PDF Generator ondersteunt alleen Engelse, Franse, Duitse en Japanse versies van de ondersteunde besturingssystemen en toepassingen.
Daarnaast
* PDF Generator vereist 32-bits versie van [Acrobat 2020 klassieke trackversie 20.004.3006](https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html) of Acrobat 2017 versie 17.011.30078 om de conversie uit te voeren.
* PDF Generator-conversies voor OpenOffice worden alleen ondersteund in Windows en Linux®.
* PDF Generator ondersteunt alleen de 32-bits Retail-versie van Microsoft® Office Professional Plus en andere software die vereist is voor conversie op Windows-besturingssystemen.
* PDF Generator ondersteunt de 32-bits en 64-bits versies van OpenOffice op het Linux®-besturingssysteem.
* PDF Generator biedt geen ondersteuning voor Microsoft® Office 365.
* De functies OCR PDF, Optimize PDF en Export PDF worden alleen in Windows ondersteund.
* Een versie van Acrobat wordt met AEM Forms gebundeld om de functionaliteit van de PDF Generator in te schakelen. Tijdens de looptijd van de AEM Forms-licentie heeft de gebundelde versie alleen via programmacode toegang tot de gebundelde versie met AEM Forms, voor gebruik met AEM Forms PDF Generator. Zie de productbeschrijving van AEM Forms volgens uw implementatie ([Op locatie](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-on-premise.html) of [Managed Services](https://helpx.adobe.com/legal/product-descriptions/adobe-experience-manager-managed-services.html))
* PDF Generator-service biedt geen ondersteuning voor Microsoft® Windows 10.
* PDF Generator kan bestanden niet converteren met Microsoft® Visio 2019. U kunt Microsoft® Visio 2016 blijven gebruiken voor conversie `.VSD` en `.VSDX` bestanden.
* PDF Generator kan bestanden niet converteren met Microsoft® Project 2019. U kunt Microsoft® Project 2016 blijven gebruiken voor conversie `.VSD` en `.VSDX` bestanden.
>


### Vereisten voor AEM Forms Designer {#requirements-for-aem-forms-designer}

* Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server of Microsoft® Windows® 10
* Processor van 1 GHz of sneller met ondersteuning voor PAE, NX en SSE2.
* 1 GB RAM voor 32-bits of 2 GB RAM voor 64-bits besturingssysteem
* 16 GB schijfruimte voor 32-bits of 20 GB schijfruimte voor 64-bits besturingssysteem
* Grafisch geheugen - 128 MB GPU (256 MB aanbevolen)
* 2,35 GB beschikbare ruimte op de vaste schijf
* Monitorresolutie van 1024 x 768 pixels of hoger
* Hardwareversnelling voor video (optioneel)
* Acrobat Pro DC, Acrobat Standard DC of Adobe Acrobat Reader DC.
* Beheerdersrechten voor het installeren van Designer.

### Vereisten voor het terugschrijven van metagegevens van AEM Assets XMP {#requirements-for-aem-assets-xmp-metadata-write-back}

XMP terugschrijven wordt ondersteund en ingeschakeld voor de volgende platforms en bestandsindelingen:

* **Besturingssystemen:**

   * Linux® (32-bits en 32-bits toepassingsondersteuning op 64-bits systemen). Ga voor stappen voor het installeren van 32-bits clientbibliotheken naar [Hoe kan ik XMP extractie en terugschrijven inschakelen bij de 64-bits Red Hat® Linux®](https://helpx.adobe.com/experience-manager/kb/enable-xmp-write-back-64-bit-redhat.html).

   * Windows Server
   * macOS X (64-bits)

* **Bestandsindelingen**: JPEG, PNG, TIFF, PDF, INDD, AI en EPS.

### Vereisten voor AEM Assets om zwaar materiaal met metagegevens te verwerken op Linux® {#assetsonlinux}

Voor het XMPFilesProcessor-proces is de bibliotheek GLIBC_2.14 vereist. Gebruik een Linux® kernel die GLIBC_2.14 bevat, bijvoorbeeld Linux® kernel versie 3.1.x. Het verbetert de prestaties voor het verwerken van elementen die een grote hoeveelheid metagegevens bevatten, zoals PSD-bestanden. Als u een vorige versie van GLIBC gebruikt, treedt er een fout op in logbestanden die begint met `com.day.cq.dam.core.impl.handler.xmp.NCommXMPHandler Failed to read XMP`.
