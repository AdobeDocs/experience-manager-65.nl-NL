---
title: AEM Forms versterken op JEE-omgeving
description: Leer een verscheidenheid van veiligheid-verhardende montages om de veiligheid van AEM Forms op JEE te verbeteren die in een collectieve Intranet loopt.
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
role: Admin,User
exl-id: 6fb260f9-d0f8-431e-8d4e-535b451e4124
solution: Experience Manager, Experience Manager Forms
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '7608'
ht-degree: 0%

---

# AEM Forms versterken op JEE-omgeving {#hardening-your-aem-forms-on-jee-environment}

Leer een verscheidenheid van veiligheid-verhardende montages om de veiligheid van AEM Forms op JEE te verbeteren die in een collectieve Intranet loopt.

In het artikel worden aanbevelingen en aanbevolen procedures beschreven voor het beveiligen van servers die AEM Forms uitvoeren op JEE. Dit is geen uitgebreid host-hardend document voor uw besturingssysteem en toepassingsservers. In plaats daarvan, beschrijft dit artikel een verscheidenheid van veiligheid-verhardende montages die u zou moeten uitvoeren om de veiligheid van AEM Forms op JEE te verbeteren die binnen een collectief Intranet loopt. Om ervoor te zorgen dat de AEM Forms op JEE toepassingsservers veilig blijft, echter, zou u veiligheid controle, opsporing, en reactieprocedures ook moeten uitvoeren.

In het artikel worden verhardingstechnieken beschreven die tijdens de levenscyclus van de installatie en configuratie in de volgende fasen moeten worden toegepast:

* **Voorinstallatie:** Gebruik deze technieken voordat u AEM Forms op JEE installeert.
* **Installatie:** Gebruik deze technieken tijdens het installatieproces van AEM Forms on JEE.
* **Na de installatie:** Gebruik deze technieken na installatie en periodiek daarna.

AEM Forms on JEE is zeer aanpasbaar en kan in vele verschillende omgevingen werken. Sommige aanbevelingen passen mogelijk niet in de behoeften van uw organisatie.

## Voorinstallatie {#preinstallation}

Voordat u AEM Forms op JEE installeert, kunt u beveiligingsoplossingen toepassen op de netwerklaag en het besturingssysteem. In deze sectie worden enkele problemen beschreven en worden aanbevelingen gedaan om beveiligingsrisico&#39;s op deze gebieden te verminderen.

**Installatie en configuratie op UNIX en Linux**

U moet AEM Forms niet installeren of configureren op JEE met behulp van een hoofdshell. Standaard worden bestanden geïnstalleerd onder de map /opt en heeft de gebruiker die de installatie uitvoert, alle bestandsmachtigingen onder /opt nodig. Alternatief, kan een installatie onder de /user folder van een individuele gebruiker worden uitgevoerd waar zij reeds alle dossiertoestemmingen hebben.

**Installatie en configuratie in Windows**

U moet de installatie in Windows als beheerder uitvoeren als u AEM Forms op JEE op JBoss installeert met de methode key of als u PDF Generator installeert. Wanneer u PDF Generator installeert op Windows met native toepassingsondersteuning, moet u de installatie uitvoeren als dezelfde Windows-gebruiker die Microsoft Office heeft geïnstalleerd. Zie het document* AEM Forms installeren en implementeren op JEE* voor meer informatie over installatiemacht.

### Netwerklaagbeveiliging {#network-layer-security}

De de veiligheidskwetsbaarheid van het netwerk is onder de eerste bedreigingen aan om het even welke Internet-Onder ogen ziet of intranet-Onder ogen ziet toepassingsserver. Deze sectie beschrijft het proces om gastheren op het netwerk tegen deze kwetsbaarheid te verharden. Het richt netwerksegmentatie, de stapelverharding van het Protocol van de Controle van de Transmissie/van Internet-protocol (TCP/IP), en het gebruik van firewalls voor gastheerbescherming.

De volgende lijst beschrijft gemeenschappelijke processen die de kwetsbaarheid van de netwerkveiligheid verminderen.

<table> 
 <thead> 
  <tr> 
   <th><p>Probleem</p> </th> 
   <th><p>Beschrijving</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Gedemilitariseerde zones (DMZ's)</p> </td> 
   <td><p>Stel vormenservers binnen een gedemilitariseerde streek (DMZ) op. Segmentatie moet bestaan op ten minste twee niveaus, waarbij de toepassingsserver wordt gebruikt om AEM Forms uit te voeren op JEE die achter de binnenfirewall is geplaatst. Scheid het externe netwerk van DMZ die de Webservers bevat, die beurtelings van het interne netwerk moeten worden gescheiden. Gebruik firewalls om de scheidingslagen te implementeren. Categoriseer en controleer het verkeer dat door elke netwerklaag overgaat om ervoor te zorgen dat slechts het absolute minimum van vereiste gegevens wordt toegestaan.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Persoonlijke IP-adressen</p> </td> 
   <td><p>De Vertaling van het Adres van het Netwerk van het gebruik (NATIONAAL) met RFC 1918 privé IP adressen op de de toepassingsserver van AEM Forms. Wijs privé IP adressen (10.0.0.0/8, 172.16.0.0/12, en 192.168.0.0/16) toe om het voor een aanvaller moeilijker te maken om verkeer aan en van een NATIONAAL interne gastheer door Internet te leiden.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Firewalls</p> </td> 
   <td><p>Gebruik de volgende criteria om een firewalloplossing te selecteren:</p> 
    <ul> 
     <li><p>Voer firewalls uit die volmachtsservers en/of steunen <em>stateful inspectie</em> in plaats van eenvoudige pakketfilteroplossingen.</p> </li> 
     <li><p>Gebruik een firewall die een <em>alle services weigeren, behalve de uitdrukkelijk toegestane</em> veiligheidsparadigma's.</p> </li> 
     <li><p>Voer een firewalloplossing uit die dubbel-homed of multihomed is. Deze architectuur biedt het grootste beveiligingsniveau en helpt te voorkomen dat onbevoegde gebruikers de firewallbeveiliging omzeilen.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Databasepoorten</p> </td> 
   <td><p>Gebruik geen standaard luisterpoorten voor databases (MySQL - 3306, Oracle - 1521, MS SQL - 1433). Raadpleeg de documentatie bij uw database voor informatie over het wijzigen van databasepoorten.</p> <p>Het gebruiken van een verschillende gegevensbestandhaven beïnvloedt algemene AEM Forms op configuratie JEE. Als u standaardhavens verandert, moet u overeenkomstige wijzigingen in andere gebieden van configuratie, zoals de gegevensbronnen voor AEM Forms op JEE aanbrengen.</p> <p>Voor informatie over het configureren van gegevensbronnen in AEM Forms op JEE raadpleegt u AEM Forms installeren en upgraden in JEE of Upgraden naar AEM Forms op JEE voor uw toepassingsserver op <a href="/help/forms/using/introduction-aem-forms.md" target="_blank">AEM Forms-gebruikershandleiding</a>.</p> </td> 
  </tr> 
 </tbody> 
</table>

### Beveiliging van besturingssystemen {#operating-system-security}

In de volgende tabel worden enkele mogelijke benaderingen beschreven om beveiligingskwetsbaarheden die in het besturingssysteem zijn aangetroffen, tot een minimum te beperken.

<table> 
 <thead> 
  <tr> 
   <th><p>Probleem</p></th> 
   <th><p>Beschrijving</p></th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Beveiligingspatches</p></td> 
   <td><p>Er is een verhoogd risico dat een niet-geautoriseerde gebruiker toegang krijgt tot de toepassingsserver als beveiligingspatches en upgrades van leveranciers niet tijdig worden toegepast. Test beveiligingspatches voordat u ze op productieservers toepast.</p><p>Ook kunt u beleidsregels en procedures maken om regelmatig te controleren op patches en deze te installeren.</p></td> 
  </tr> 
  <tr> 
   <td><p>Virusbeveiligingssoftware</p></td> 
   <td><p>Virusscanners kunnen geïnfecteerde bestanden herkennen door te zoeken naar een handtekening of op ongewoon gedrag te kijken. Scanners bewaren hun virushandtekeningen in een bestand dat meestal op de lokale vaste schijf wordt opgeslagen. Omdat nieuwe virussen vaak worden gedetecteerd, moet u dit bestand regelmatig bijwerken voor de virusscanner om alle huidige virussen te identificeren.</p></td> 
  </tr> 
  <tr> 
   <td><p>Netwerktijdprotocol (NTP)</p></td> 
   <td><p>Voor forensische analyse moet u nauwkeurige tijd op de formulierservers houden. Gebruik NTP om de tijd op alle systemen te synchroniseren die direct met Internet worden verbonden.</p></td> 
  </tr> 
 </tbody> 
</table>

Zie voor meer beveiligingsinformatie voor uw besturingssysteem [&quot;Beveiligingsinformatie van besturingssysteem&quot;](https://helpx.adobe.com/aem-forms/6-1/hardening-security/general-security-considerations.html#operating_system_security_information).

## Installatie {#installation}

In deze sectie worden technieken beschreven die u tijdens het AEM Forms-installatieproces kunt gebruiken om beveiligingsrisico&#39;s te beperken. In sommige gevallen maken deze technieken gebruik van opties die deel uitmaken van het installatieproces. In de volgende tabel worden deze technieken beschreven.

<table> 
 <thead> 
  <tr> 
   <th><p>Probleem</p> </th> 
   <th><p>Beschrijving</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Rechten</p> </td> 
   <td><p>Gebruik het minste aantal rechten dat nodig is om de software te installeren. Meld u aan bij uw computer met een account die zich niet in de groep Beheerders bevindt. In Windows kunt u de opdracht Uitvoeren als gebruiken om het AEM Forms-installatieprogramma van JEE als een beheergebruiker uit te voeren. Bij UNIX- en Linux-systemen gebruikt u een opdracht, zoals <code>sudo</code> de software installeren.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Softwarebron</p> </td> 
   <td><p>Download of voer AEM Forms niet uit op JEE van niet-vertrouwde bronnen.</p> <p>De kwaadwillige programma's kunnen code bevatten om veiligheid op verscheidene manieren, met inbegrip van gegevensdiefstal, wijziging en schrapping, en ontkenning van de dienst te schenden. Installeer AEM Forms op JEE vanaf de Adobe-dvd of alleen vanaf een vertrouwde bron.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Schijfpartities</p> </td> 
   <td><p>Plaats AEM Forms op JEE op een toegewezen schijfpartitie. De segmentatie van de schijf is een proces dat specifieke gegevens op uw server op afzonderlijke fysieke schijven voor extra veiligheid houdt. Het schikken van gegevens op deze manier vermindert het risico van folderaanvallen. Maak een partitie die los staat van de systeempartitie waarop u de AEM Forms in de JEE-inhoudsmap kunt installeren. (In Windows bevat de systeempartitie de directory system32 of de opstartpartitie.)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Onderdelen</p> </td> 
   <td><p>Evalueer de bestaande diensten en maak of desinstalleer om het even welke onbruikbaar die niet worden vereist. Installeer geen overbodige onderdelen en services.</p> <p>De standaardinstallatie van een toepassingsserver zou de diensten kunnen omvatten die niet noodzakelijk voor uw gebruik zijn. U zou alle onnodige diensten voorafgaand aan plaatsing moeten onbruikbaar maken om punten van ingang voor een aanval te minimaliseren. Op JBoss kunt u bijvoorbeeld opmerkingen plaatsen over overbodige services in het beschrijvingsbestand META-INF/jboss-service.xml.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Interdomeinbeleidsbestand</p> </td> 
   <td><p>De aanwezigheid van een <code>crossdomain.xml</code> op de server kan die server onmiddellijk verzwakken. U wordt aangeraden de lijst met domeinen zo restrictief mogelijk te maken. Plaats de <code>crossdomain.xml</code> bestand dat tijdens de ontwikkeling naar de productie is gebruikt bij het gebruik van hulplijnen <em>(afgekeurd)</em>. Voor een gids die de Webdiensten gebruikt, als de dienst op de zelfde server is die omhoog de gids, <code>crossdomain.xml</code> bestand is helemaal niet nodig. Maar als de dienst op een andere server is, of als de clusters betrokken zijn, de aanwezigheid van <code>crossdomain.xml</code> bestand is vereist. Zie <a href="https://kb2.adobe.com/cps/142/tn_14213.html">https://kb2.adobe.com/cps/142/tn_14213.html</a>voor meer informatie over het bestand crossdomain.xml.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Beveiligingsinstellingen van besturingssysteem</p> </td> 
   <td><p>Als u 192-bits of 256-bits XML-codering op Solaris-platforms moet gebruiken, moet u de installatie <code>pkcs11_softtoken_extra.so</code> in plaats van <code>pkcs11_softtoken.so</code>.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Stappen na de installatie {#post-installation-steps}

Nadat u AEM Forms met succes op JEE installeert, is het belangrijk om het milieu uit veiligheidsperspectief periodiek te handhaven.

De volgende sectie beschrijft in detail de verschillende taken die worden geadviseerd om de opgestelde Server van Forms te beveiligen.

### AEM Forms-beveiliging {#aem-forms-security}

De volgende aanbevolen instellingen gelden voor de AEM Forms op de JEE-server buiten de beheerwebtoepassing. Als u de beveiligingsrisico&#39;s voor de server wilt beperken, past u deze instellingen direct toe nadat u AEM Forms op JEE hebt geïnstalleerd.

**Beveiligingspatches**

Er is een verhoogd risico dat een onbevoegde gebruiker toegang tot de toepassingsserver zou kunnen krijgen als de patches en upgrades van de verkopersveiligheid niet tijdig worden toegepast. Test beveiligingspatches voordat u ze op productieservers toepast om de compatibiliteit en beschikbaarheid van toepassingen te garanderen. Ook kunt u beleidsregels en procedures maken om regelmatig te controleren op patches en deze te installeren. AEM Forms on JEE-updates zijn beschikbaar op de downloadsite voor Enterprise-producten.

**Servicerekeningen (alleen voor JBoss-sleutel in Windows)**

AEM Forms on JEE installeert standaard een service via de LocalSystem-account. De ingebouwde gebruikersrekening LocalSystem heeft een hoog niveau van toegankelijkheid; het maakt deel uit van de groep van Beheerders. Als een worker-process-identiteit wordt uitgevoerd als LocalSystem-gebruikersaccount, heeft dat arbeidersproces volledige toegang tot het gehele systeem.

Volg de onderstaande instructies om de toepassingsserver uit te voeren waarop AEM Forms op JEE wordt geïmplementeerd met een specifieke niet-beheeraccount:

1. Maak in de Microsoft Management Console (MMC) een lokale gebruiker voor de Forms Server-service om u aan te melden als:

   * Selecteren **Gebruiker kan wachtwoord niet wijzigen**.
   * Op de **Lid van** zorgt u ervoor dat de **Gebruikers** wordt weergegeven.

   >[!NOTE]
   >
   >U kunt deze instelling voor PDF Generator niet wijzigen.

1. Selecteren **Start** > **Instellingen** > **Administratieve gereedschappen** > **Services**.
1. Dubbelklik op JBoss voor AEM Forms op JEE en stop de service.
1. Op de **Aanmelden** tab, selecteert u **Dit account** Blader naar de gebruikersaccount die u hebt gemaakt en voer het wachtwoord voor de account in.
1. In de MMC, open **Lokale beveiligingsinstellingen** en selecteert u **Lokaal beleid** > **Toewijzing gebruikersrechten**.
1. Wijs de volgende rechten toe aan de gebruikersaccount waarop de Forms Server wordt uitgevoerd:

   * Ontken login door de EindDiensten
   * Aanmelden lokaal weigeren
   * Aanmelden als service (moet al zijn ingesteld)

1. Wijzig de machtigingen voor de nieuwe gebruikersaccount voor de volgende directory&#39;s:
   * **GDS-map (Global Document Storage)**: De locatie van de GDS-map wordt handmatig geconfigureerd tijdens het AEM Forms-installatieproces. Als de locatie-instelling tijdens de installatie leeg blijft, wordt de locatie standaard ingesteld op een directory onder de installatie van de toepassingsserver op `[JBoss root]/server/[type]/svcnative/DocumentStorage`
   * **CRX-opslagmap**: De standaardlocatie is `[AEM-Forms-installation-location]\crx-repository`
   * **Tijdelijke AEM Forms-mappen**:
      * (Windows) TMP- of TEMP-pad zoals ingesteld in de omgevingsvariabelen
      * (AIX, Linux, of Solaris) Logged-in de huisfolder van de gebruiker op op UNIX-Gebaseerde systemen, kan een niet wortelgebruiker de volgende folder als tijdelijke folder gebruiken:
      * (Linux) /var/tmp of /usr/tmp
      * (AIX) /tmp of /usr/tmp
      * (Solaris) /var/tmp of /usr/tmp
1. Geef de nieuwe gebruikersaccount schrijfmachtigingen voor de volgende directory&#39;s:
   * [JBoss-directory]\standalone\nimplementatie
   * [JBoss-directory]\standalone\
   * [JBoss-directory]\bin\

   >[!NOTE]
   >
   >De standaardinstallatielocatie van JBoss Application Server:
   >
   >* Windows: C:\Adobe\Adobe_Experience_Manager_Forms\jboss
   >* Linux: /opt/jreliëf/

1. Start de toepassingsserver.

**Het onbruikbaar maken van de reservereserlet van de Manager van de Configuratie**

Configuration Manager maakte gebruik van een servlet die op uw toepassingsserver wordt opgesteld om bootstrapping van AEM Forms op gegevensbestand uit te voeren JEE. Omdat de Manager van de Configuratie tot dit servlet toegang heeft alvorens de configuratie volledig is, is de toegang tot het niet beveiligd voor erkende gebruikers, en het zou moeten worden onbruikbaar gemaakt nadat u met succes de Manager van de Configuratie hebt gebruikt om AEM Forms op JEE te vormen.

1. De adobe-livecycle uitpakken[appserver].ear-bestand.
1. Open het bestand META-INF/application.xml.
1. Zoek naar de adobe-bootstrapper.war sectie:

   ```java
   <!-- bootstrapper start --> 
   <module id="WebApp_adobe_bootstrapper"> 
       <web> 
           <web-uri>adobe-bootstrapper.war</web-uri> 
           <context-root>/adobe-bootstrapper</context-root> 
       </web> 
   </module> 
   <module id="WebApp_adobe_lcm_bootstrapper_redirector"> 
       <web> 
           <web-uri>adobe-lcm-bootstrapper-redirector.war</web-uri> 
           <context-root>/adobe-lcm-bootstrapper</context-root> 
       </web> 
   </module> 
   <!-- bootstrapper end-->
   ```

1. Stop de AEM Forms-server.
1. Maak een commentaarregel van adobe-bootstrapper.war en de adobe-lcm-bootstrapper-redirectory. oorlogsmodules, als hieronder:

   ```java
   <!-- bootstrapper start --> 
   <!-- 
   <module id="WebApp_adobe_bootstrapper"> 
       <web> 
           <web-uri>adobe-bootstrapper.war</web-uri> 
           <context-root>/adobe-bootstrapper</context-root> 
       </web> 
   </module> 
   <module id="WebApp_adobe_lcm_bootstrapper_redirector"> 
       <web> 
           <web-uri>adobe-lcm-bootstrapper-redirector.war</web-uri> 
           <context-root>/adobe-lcm-bootstrapper</context-root> 
       </web> 
   </module> 
   --> 
   <!-- bootstrapper end-->
   ```

1. Sla het bestand META-INF/application.xml op en sluit het.
1. Zip het EAR-bestand en implementeer het opnieuw op de toepassingsserver.
1. Start de AEM Forms-server.
1. Typ de onderstaande URL in een browser om de wijziging te testen en te controleren of deze niet meer werkt.

   https://&lt;localhost>:&lt;port>/adobe-bootstrapper/bootstrap

**Externe toegang vergrendelen tot de Trust Store**

Met Configuratiebeheer kunt u een Acrobat Reader DC-extensie uploaden die is gecrediteerd aan de AEM Forms in de JEE-vertrouwde opslag. Dit betekent dat de toegang tot de Dienst van de Referentie van de Opslag van het Vertrouwen over verre protocollen (ZEEP en EJB) door gebrek is toegelaten. Deze toegang is niet meer noodzakelijk nadat u de credentie van Rechten gebruikend de Manager van de Configuratie hebt geupload of als u besluit om de Console van het Beleid later te gebruiken om geloofsbrieven te beheren.

U kunt de externe toegang tot alle Trust Store-services uitschakelen door de stappen in de sectie uit te voeren [Niet-essentiële externe toegang tot services uitschakelen](https://helpx.adobe.com/aem-forms/6-1/hardening-security/configuring-secure-administration-settings-aem.html#disabling_non_essential_remote_access_to_services).

**Alle niet-essentiële anonieme toegang uitschakelen**

Sommige diensten van de Server van Forms hebben verrichtingen die door een anonieme bezoeker kunnen worden aangehaald. Als anonieme toegang tot deze diensten niet wordt vereist, maak het onbruikbaar door de stappen in te volgen [Niet-essentiële anonieme toegang tot services uitschakelen](https://helpx.adobe.com/aem-forms/6-1/hardening-security/configuring-secure-administration-settings-aem.html#disabling_non_essential_anonymous_access_to_services).

#### Het standaardbeheerderswachtwoord wijzigen {#change-the-default-administrator-password}

Wanneer AEM Forms op JEE is geïnstalleerd, wordt één standaardgebruikersaccount geconfigureerd voor de beheerder van de superbeheerder/aanmeldings-id van de gebruiker met een standaardwachtwoord van *password*. U zou dit wachtwoord onmiddellijk moeten veranderen gebruikend de Manager van de Configuratie.

1. Typ de volgende URL in een webbrowser:

   ```java
   https://[host name]:[port]/adminui
   ```

   Het standaardpoortnummer is een van de volgende:

   **JBoss:** 8080

   **WebLogic-server:** 7001

   **WebSphere** 9080

1. In de **Gebruikersnaam** veld, type `administrator` en in de **Wachtwoord** veld, type `password`.
1. Klikken **Instellingen** > **Gebruikersbeheer** > **Gebruikers en groepen**.
1. Type `administrator` in de **Zoeken** en klik op **Zoeken**.
1. Klikken **Super Administrator** in de lijst met gebruikers.
1. Klikken **Wachtwoord wijzigen** op de pagina Gebruiker bewerken.
1. Geef het nieuwe wachtwoord op en klik op **Opslaan**.

Daarnaast wordt aangeraden het standaardwachtwoord voor CRX Administrator te wijzigen door de volgende stappen uit te voeren:

1. Aanmelden `https://[server]:[port]/lc/libs/granite/security/content/useradmin.html` de standaardgebruikersnaam/het standaardwachtwoord gebruiken.
1. Typ Beheerder in het zoekveld en klik op **Ga**.
1. Selecteren **Beheerder** in het zoekresultaat en klik op de knop **Bewerken** pictogram rechts onder in de gebruikersinterface.
1. Geef het nieuwe wachtwoord op in het dialoogvenster **Nieuw wachtwoord** en het oude wachtwoord in het veld **Uw wachtwoord** veld.
1. Klik op het pictogram Opslaan rechtsonder in de gebruikersinterface.

#### WSDL-generatie uitschakelen {#disable-wsdl-generation}

De generatie van de Definitie van de Taal van de Dienst van het Web (WSDL) zou slechts voor ontwikkelomgevingen moeten worden toegelaten, waar de generatie WSDL door ontwikkelaars wordt gebruikt om hun cliënttoepassingen te bouwen. U kunt verkiezen om de generatie van WSDL in een productiemilieu onbruikbaar te maken vermijden blootstellend de interne details van de dienst.

1. Typ de volgende URL in een webbrowser:

   ```java
   https://[host name]:[port]/adminui
   ```

1. Selecteren **Settings > Core System Settings > Configurations**.
1. Deselecteren **WSDL inschakelen** selecteert u vervolgens **OK**.

### Beveiliging toepassingsserver {#application-server-security}

In de volgende tabel worden enkele technieken beschreven waarmee u uw toepassingsserver kunt beveiligen nadat de AEM Forms op JEE-toepassing is geïnstalleerd.

<table> 
 <thead> 
  <tr> 
   <th><p>Probleem</p> </th> 
   <th><p>Beschrijving</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Beheerconsole toepassingsserver</p> </td> 
   <td><p>Nadat u AEM Forms op JEE op uw toepassingsserver hebt geïnstalleerd, geconfigureerd en geïmplementeerd, moet u de toegang tot de beheerconsoles van de toepassingsserver uitschakelen. Raadpleeg de documentatie bij de toepassingsserver voor meer informatie.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Cookinstellingen toepassingsserver</p> </td> 
   <td><p>Toepassingscookies worden beheerd door de toepassingsserver. Bij het implementeren van de toepassing kan de beheerder van de toepassingsserver cookie-voorkeuren opgeven op een serverspecifieke of toepassingsspecifieke basis. Standaard hebben de serverinstellingen de voorkeur.</p> <p>Alle sessiecookies die door uw toepassingsserver worden gegenereerd, moeten de opdracht <code>HttpOnly</code> kenmerk. Bijvoorbeeld, wanneer het gebruiken van de Server van de Toepassing JBoss, kunt u het element SessionCookie wijzigen aan <code>httpOnly="true"</code> in de <code>WEB-INF/web.xml</code> bestand.</p> <p>U kunt het verzenden van cookies beperken met alleen HTTPS. Als gevolg hiervan worden ze niet ongecodeerd via HTTP verzonden. Beheerders van toepassingsservers moeten beveiligde cookies voor de server op algemene basis inschakelen. Wanneer u bijvoorbeeld de JBoss-toepassingsserver gebruikt, kunt u het verbindingselement aanpassen aan <code>secure=true</code> in de <code>server.xml</code> bestand.</p> <p>Raadpleeg de documentatie bij de toepassingsserver voor meer informatie over cookie-instellingen.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Bladeren door mappen</p> </td> 
   <td><p>Wanneer iemand om een pagina verzoekt die niet bestaat of om de naam van een directeur verzoekt (het verzoekkoord beëindigt met een voorwaartse schuine streep (/)), zou de toepassingsserver niet de inhoud van die folder moeten terugkeren. Om dit te voorkomen, kunt u bladeren door mappen op uw toepassingsserver uitschakelen. U zou dit voor de toepassing van de beleidsconsole en voor andere toepassingen moeten doen die op uw server lopen.</p> <p>Stel voor JBoss de waarde in van de initialisatieparameter voor lijsten in het dialoogvenster <code>DefaultServlet</code> eigenschap aan <code>false</code> in het bestand web.xml, zoals in dit voorbeeld wordt getoond:</p> <p>&lt;servlet&gt;</p> <p>&lt;servlet-name&gt;default&lt;/servlet-name&gt;</p> <p>&lt;servlet-class&gt;</p> <p>org.apache.catalina.servlets.DefaultServlet</p> <p>&lt;/servlet-class&gt;</p> <p>&lt;init-param&gt;</p> <p>&lt;param-name&gt;aanbiedingen&lt;/param-name&gt;</p> <p>&lt;param-value&gt;false&lt;/param-value&gt;</p> <p>&lt;/init-param&gt;</p> <p>&lt;load-on-startup&gt;1&lt;/load-on-startup&gt;</p> <p>&lt;/servlet&gt;</p> <p>Voor WebSphere stelt u de <code>directoryBrowsingEnabled</code> eigenschap in het bestand ibm-web-ext.xmi naar <code>false</code>.</p> <p>Voor WebLogic stelt u de eigenschappen voor indexmappen in het bestand weblogic.xml in op <code>false</code>, zoals in dit voorbeeld wordt getoond:</p> <p>&lt;container-descriptor&gt;</p> <p>&lt;index-directory-enabled&gt;false</p> <p>&lt;/index-directory-enabled&gt;</p> <p>&lt;/container-descriptor&gt;</p> </td> 
  </tr> 
 </tbody> 
</table>

### Databasebeveiliging {#database-security}

Wanneer het beveiligen van uw gegevensbestand, zou u de maatregelen moeten uitvoeren die door uw gegevensbestandverkoper worden beschreven. U zou een gegevensbestandgebruiker met de minimaal vereiste gegevensbestandtoestemmingen moeten toewijzen die voor gebruik door AEM Forms op JEE worden verleend. Gebruik bijvoorbeeld geen account met databasebeheerdersrechten.

Bij Oracle heeft de databaseaccount die u gebruikt alleen de bevoegdheden CONNECT, RESOURCE en CREATE VIEW nodig. Voor vergelijkbare vereisten voor andere databases, zie [Installatie van AEM Forms op JEE (één server) voorbereiden](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_64).

#### Het vormen geïntegreerde veiligheid voor SQL Server op Vensters voor JBoss {#configuring-integrated-security-for-sql-server-on-windows-for-jboss}

1. Wijzigen [JBOSS_HOME]\\standalone\configuration\lc_{datasource.xml} toevoegen `integratedSecurity=true` naar de verbindings-URL, zoals in dit voorbeeld wordt getoond:

   ```java
    jdbc:sqlserver://<serverhost>:<port>;databaseName=<dbname>;integratedSecurity=true
   ```

1. Voeg het bestand sqljdbc_auth.dll toe aan het Windows-systeempad op de computer waarop de toepassingsserver wordt uitgevoerd. Het bestand sqljdbc_auth.dll bevindt zich bij de installatie van het stuurprogramma voor Microsoft SQL JDBC 6.2.1.0.
1. Wijzig JBoss de dienstbezit van Vensters (JBoss voor AEM Forms op JEE) voor Aanmelden vanaf Lokaal Systeem aan een login rekening die het gegevensbestand van AEM Forms en een minimumreeks voorrechten heeft. Als u JBoss van de bevellijn in plaats van als dienst van Vensters in werking stelt, te hoeven u niet om deze stap uit te voeren.
1. Beveiliging voor SQL Server instellen vanuit **Gemengd** modus to **Alleen Windows-verificatie**.

#### Geïntegreerde beveiliging voor SQL Server configureren in Windows voor WebLogic {#configuring-integrated-security-for-sql-server-on-windows-for-weblogic}

1. Start de WebLogic Server Administration Console door de volgende URL te typen in de URL-regel van een webbrowser:

   ```java
   https://[host name]:7001/console
   ```

1. Klik onder Wijzigen in midden op **Vergrendelen en bewerken**.
1. Klik onder Domeinstructuur op *[base_domain]* > **Services** > **JDBC** > **Gegevensbronnen** en klikt u in het rechterdeelvenster op **IDP_DS**.
1. Op het volgende scherm, op het **Configuratie** klikt u op de knop **Verbindingspool** en, in de **Eigenschappen** vak, tekst `integratedSecurity=true`.
1. Klik onder Domeinstructuur op **[base_domain]** > **Services** > **JDBC** > **Gegevensbronnen** en klikt u in het rechterdeelvenster op **RM_DS**.
1. Op het volgende scherm, op het **Configuratie** klikt u op de knop **Verbindingspool** en, in de **Eigenschappen** vak, tekst `integratedSecurity=true`.
1. Voeg het bestand sqljdbc_auth.dll toe aan het Windows-systeempad op de computer waarop de toepassingsserver wordt uitgevoerd. Het bestand sqljdbc_auth.dll bevindt zich bij de installatie van het stuurprogramma voor Microsoft SQL JDBC 6.2.1.0.
1. Beveiliging voor SQL Server instellen vanuit **Gemengd** modus to **Alleen Windows-verificatie**.

#### Het vormen geïntegreerde veiligheid voor SQL Server op Vensters voor WebSphere {#configuring-integrated-security-for-sql-server-on-windows-for-websphere}

Op WebSphere, kunt u geïntegreerde veiligheid vormen slechts wanneer u een externe SQL bestuurder van de Server JDBC, niet de SQL bestuurder van de Server JDBC gebruikt die met WebSphere wordt ingebed.

1. Meld u aan bij de beheerconsole van WebSphere.
1. Klik in de navigatiestructuur op **Bronnen** > **JDBC** > **Gegevensbronnen** en klikt u in het rechterdeelvenster op **IDP_DS**.
1. Klik in het rechterdeelvenster onder Extra eigenschappen op **Aangepaste eigenschappen** en klik vervolgens op **Nieuw**.
1. In de **Naam** vak, tekst `integratedSecurity` en in de **Waarde** vak, tekst `true`.
1. Klik in de navigatiestructuur op **Bronnen** > **JDBC** > **Gegevensbronnen** en klikt u in het rechterdeelvenster op **RM_DS**.
1. Klik in het rechterdeelvenster onder Extra eigenschappen op **Aangepaste eigenschappen** en klik vervolgens op **Nieuw**.
1. In de **Naam** vak, tekst `integratedSecurity` en in de **Waarde** vak, tekst `true`.
1. Voeg op de computer waarop WebSphere is geïnstalleerd het bestand sqljdbc_auth.dll toe aan het systeempad van Windows (C:\Windows). Het bestand sqljdbc_auth.dll bevindt zich op dezelfde locatie als de installatie van het stuurprogramma voor Microsoft SQL JDBC 1.2 (standaard is *[InstallDir]*/sqljdbc_1.2/enu/auth/x86).
1. Selecteren **Start** > **Deelvenster Beheer** > **Services**, klikt u met de rechtermuisknop op de Windows-service voor WebSphere (IBM WebSphere Application Server) &lt;version> - &lt;node>) en selecteert u **Eigenschappen**.
1. Klik in het dialoogvenster Eigenschappen op de knop **Aanmelden** tab.
1. Selecteren **Dit account** en geef de informatie op die nodig is om de aanmeldingsaccount in te stellen die u wilt gebruiken.
1. Beveiliging instellen op SQL Server vanuit **Gemengd** modus to **Alleen Windows-verificatie**.

### Toegang tot gevoelige inhoud in de database beveiligen {#protecting-access-to-sensitive-content-in-the-database}

Het AEM Forms-databaseschema bevat gevoelige informatie over systeemconfiguratie en bedrijfsprocessen en moet achter de firewall worden verborgen. De database moet worden beschouwd binnen dezelfde vertrouwensgrens als de Forms-server. Om tegen informatieonthulling en diefstal van bedrijfsgegevens te beschermen, moet het gegevensbestand door de gegevensbestandbeheerder (DBA) worden gevormd om toegang slechts door erkende beheerders toe te staan.

Als toegevoegde voorzorg, zou u het gebruiken van gegevensbestand verkoper-specifieke hulpmiddelen moeten overwegen om kolommen in lijsten te coderen die de volgende gegevens bevatten:

* Documenttoetsen Rights Management
* Sleutel voor versleuteling HSM PIN-code opslaan
* Hashes lokaal gebruikerswachtwoord

Voor informatie over verkoper-specifieke hulpmiddelen, zie [&quot;Gegevensbeveiligingsinformatie&quot;](https://helpx.adobe.com/aem-forms/6-1/hardening-security/general-security-considerations.html#database_security_information).

### LDAP-beveiliging {#ldap-security}

Een Lightweight Directory Access Protocol (LDAP)-directory wordt door AEM Forms in JEE doorgaans gebruikt als bron voor zakelijke gebruikers- en groepsgegevens en als middel om wachtwoordverificatie uit te voeren. Zorg ervoor dat uw LDAP-directory is geconfigureerd voor gebruik van SSL (Secure Socket Layer) en dat AEM Forms op JEE is geconfigureerd voor toegang tot uw LDAP-directory via de SSL-poort.

#### LDAP-ontkenning van service {#ldap-denial-of-service}

Een algemene aanval met LDAP heeft tot gevolg dat een aanvaller opzettelijk meerdere keren niet verifieert. Hierdoor wordt de LDAP-directoryserver gedwongen een gebruiker uit alle LDAP-afhankelijke services te weren.

U kunt het aantal mislukkingspogingen en de daaropvolgende sluitingstijd instellen die AEM Forms implementeert wanneer een gebruiker er herhaaldelijk niet in slaagt te verifiëren bij AEM Forms. Kies lage waarden in de beheerconsole. Wanneer het selecteren van het aantal mislukkingspogingen, is het belangrijk om te begrijpen dat nadat alle pogingen worden gemaakt, AEM Forms de gebruiker sluit alvorens de Server van de Folder LDAP doet.

#### Automatische accountvergrendeling instellen {#set-automatic-account-locking}

1. Meld u aan bij de beheerconsole.
1. Klikken **Instellingen** > **Gebruikersbeheer** > **Domeinbeheer**.
1. Onder Instellingen voor automatisch vergrendelen van account instellen **Maximale opeenvolgende verificatiefouten** tot een laag aantal, zoals 3.
1. Klikken **Opslaan**.

### Controle en registratie {#auditing-and-logging}

Het juiste en veilige gebruik van toepassingscontrole en het registreren kan helpen ervoor zorgen dat de veiligheid en andere anomalische gebeurtenissen worden gevolgd en zo snel mogelijk ontdekt. Het effectieve gebruik van controle en het registreren binnen een toepassing omvat punten zoals het volgen van succesvolle en ontbroken logins, en zeer belangrijke toepassingsgebeurtenissen zoals de verwezenlijking of de schrapping van zeer belangrijke verslagen.

U kunt controle gebruiken om vele soorten aanvallen, met inbegrip van deze te ontdekken:

* Brugtforce-wachtwoordaanvallen
* Ontkenning van de dienstaanvallen
* Injectie van vijandige input en verwante klassen van scriptaanvallen

In deze tabel worden de controle- en registratietechnieken beschreven die u kunt gebruiken om de kwetsbaarheden van uw server te beperken.

<table> 
 <thead> 
  <tr> 
   <th><p>Probleem</p> </th> 
   <th><p>Beschrijving</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Logbestand-ACL's</p> </td> 
   <td><p>Plaats aangewezen AEM Forms op de lijsten van het de toegangsbeheer van het JEE- logboekdossier (ACLs).</p> <p>Door de juiste referenties in te stellen, voorkomt u dat aanvallers de bestanden verwijderen.</p> <p>De veiligheidstoestemmingen op de folder van het logboekdossier zouden Volledige Controle voor Beheerders en de groepen van het SYSTEEM moeten zijn. De AEM Forms-gebruikersaccount mag alleen de machtiging Lezen en Schrijven hebben.</p> </td> 
  </tr> 
  <tr> 
   <td><p>redundantie van logbestanden</p> </td> 
   <td><p>Als de middelen toelaten, verzend logboeken naar een andere server in real time die niet door de aanvaller (schrijf slechts) door Syslog, Tivoli, de Server van de Manager van de Verrichtingen van Microsoft (MOM), of een ander mechanisme te gebruiken toegankelijk is.</p> <p>Als u logbestanden op deze manier beschermt, voorkomt u dat er wordt geknoeid. Bovendien wordt het opslaan van logbestanden in een centrale opslagplaats ondersteund op het gebied van correlatie en controle (bijvoorbeeld als meerdere formulierservers in gebruik zijn en er op meerdere computers waar elke computer om een wachtwoord wordt gevraagd een aanval met het wachtwoord plaatsvindt).</p> </td> 
  </tr> 
 </tbody> 
</table>

### Niet-beheerdersgebruikers toestaan PDF Generator uit te voeren

U kunt een niet-beheerdergebruiker toelaten om PDF Generator te gebruiken. Normaal gesproken kunnen alleen gebruikers met beheerdersrechten PDF Generator gebruiken. Voer de volgende stappen uit om een niet-beheerdergebruiker toe te laten om PDF Generator in werking te stellen:

1. Maak een omgevingsvariabele met de naam PDFG_NON_ADMIN_ENABLED.

1. Stel waarde van de variabele in op TRUE.

1. Start de AEM Forms-instantie opnieuw.

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

## AEM Forms configureren op JEE voor toegang buiten de onderneming {#configuring-aem-forms-on-jee-for-access-beyond-the-enterprise}

Nadat u AEM Forms op JEE met succes hebt geïnstalleerd, is het belangrijk om de veiligheid van uw milieu periodiek te handhaven. In deze sectie worden de taken beschreven die worden aanbevolen om de beveiliging van uw AEM Forms op de JEE-productieserver te behouden.

### Een reverse-proxy instellen voor webtoegang {#setting-up-a-reverse-proxy-for-web-access}

A *reverse, proxy* kan worden gebruikt om ervoor te zorgen dat één set URL&#39;s voor AEM Forms op JEE-webtoepassingen beschikbaar is voor zowel externe als interne gebruikers. Deze configuratie is veiliger dan gebruikers toe te staan om rechtstreeks met de toepassingsserver te verbinden die AEM Forms op JEE loopt. De reverse-proxy voert alle HTTP-aanvragen uit voor de toepassingsserver waarop AEM Forms op JEE wordt uitgevoerd. Gebruikers hebben alleen netwerktoegang tot de reverse-proxy en kunnen alleen proberen URL-verbindingen te maken die door de reverse-proxy worden ondersteund.

**AEM Forms op URL&#39;s met JEE-hoofdmap voor gebruik met reverse-proxyserver**

De volgende URL&#39;s van de hoofdmap van de toepassing voor elke AEM Forms in JEE-webtoepassing. Configureer de reverse-proxy alleen om URL&#39;s beschikbaar te maken voor de functionaliteit van webtoepassingen die u aan eindgebruikers wilt verschaffen.

Bepaalde URL&#39;s worden gemarkeerd als eindgebruikers gerichte webtoepassingen. U zou moeten vermijden blootstellend andere URLs voor de Manager van de Configuratie voor toegang tot externe gebruikers door de omgekeerde volmacht.

<table> 
 <thead> 
  <tr> 
   <th><p>URL van hoofdmap</p> </th> 
   <th><p>Doel en/of bijbehorende webtoepassing</p> </th> 
   <th><p>Webinterface</p> </th> 
   <th><p>Toegang voor eindgebruikers</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>/ReaderExtensions/*</p> </td> 
   <td><p>Acrobat Reader DC-extensies voor eindgebruikers, webtoepassing voor het toepassen van gebruiksrechten op PDF-documenten</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/edc/*</p> </td> 
   <td><p>De eindgebruikerwebtoepassing van het Rights Management</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/edcws/*</p> </td> 
   <td><p>Webservice-URL voor Rights Management</p> </td> 
   <td><p>Nee</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/pdfgui/*</p> </td> 
   <td><p>Webtoepassing voor beheer van PDF Generatoren</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/workspace/*</p> </td> 
   <td><p>Werkruimte-webtoepassing voor eindgebruikers</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/workspace-server/*</p> </td> 
   <td><p>Werkruimteneservers en gegevensservices die de Workspace client-toepassing vereist</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/adobe-bootstrapper/*</p> </td> 
   <td><p>Servlet voor bootstrapping van de AEM Forms op JEE-opslagplaats</p> </td> 
   <td><p>Nee</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/zeep/*</p> </td> 
   <td><p>Informatiepagina voor Forms Server-webservices</p> </td> 
   <td><p>Nee</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/soap/services/*</p> </td> 
   <td><p>Webservice-URL voor alle Forms Server-services</p> </td> 
   <td><p>Nee</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/edc/admin/*</p> </td> 
   <td><p>Webtoepassing voor beheer van Rights Managementen</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/adminui/*</p> </td> 
   <td><p>Homepage van beheerconsole</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/TruststoreComponent/</p> <p>beveiligd/*</p> </td> 
   <td><p>Beheerpagina's voor winkelbeheer vertrouwen</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/FormsIVS/*</p> </td> 
   <td><p>Forms IVS-toepassing voor het testen en opsporen van fouten bij het genereren van formulieren</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/OutputIVS/*</p> </td> 
   <td><p>Uitvoer IVS toepassing voor het testen en het zuiveren van de outputdienst</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/rmws/*</p> </td> 
   <td><p>REST URL for Rights Management</p> </td> 
   <td><p>Nee</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/OutputAdmin/*</p> </td> 
   <td><p>Uitvoerbeheerpagina's</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/FormServer/*</p> </td> 
   <td><p>Forms-webtoepassingsbestanden</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/FormServer/GetImage</p> <p>Servlet</p> </td> 
   <td><p>Wordt gebruikt voor het ophalen van JavaScript tijdens transformatie van HTML</p> </td> 
   <td><p>Nee</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/FormServerAdmin/*</p> </td> 
   <td><p>Forms-beheerpagina's</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/repository/*</p> </td> 
   <td><p>URL voor WebDAV-toegang (foutopsporing)</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/AACComponent/*</p> </td> 
   <td><p>Gebruikersinterface Toepassingen en Services</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/WorkspaceAdmin/*</p> </td> 
   <td><p>Werkruimtebeheerpagina's</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/rest/*</p> </td> 
   <td><p>Ondersteuningspagina's opnieuw instellen</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/CoreSystemConfig/*</p> </td> 
   <td><p>AEM Forms on JEE Core Configuration Settings page</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/um/</p> </td> 
   <td><p>Verificatie van gebruikersbeheer</p> </td> 
   <td><p>Nee</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/um/*</p> </td> 
   <td><p>Gebruikersbeheerinterface</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/DocumentManager/*</p> </td> 
   <td><p>Uploaden en downloaden van documenten die moeten worden verwerkt wanneer toegang wordt verkregen tot externe eindpunten, SOAP WSDL-eindpunten en de Java SDK via SOAP-transport of EJB-transport met HTTP-documenten ingeschakeld.</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
 </tbody> 
</table>

## Beveiligen tegen aanvallen met Smederij voor meerdere sites {#protecting-from-cross-site-request-forgery-attacks}

Een CSRF-aanval (Cross-Site Request Svervalsing) misbruikt het vertrouwen dat een website heeft voor de gebruiker, om opdrachten door te geven die niet door de gebruiker zijn geautoriseerd en onbedoeld. De aanval wordt opstelling door een verbinding of een manuscript in een Web-pagina, of een URL in een e-mailbericht te omvatten, om tot een andere plaats toegang te hebben waaraan de gebruiker reeds voor authentiek is verklaard.

U kunt bijvoorbeeld zijn aangemeld bij de beheerconsole terwijl u tegelijkertijd door een andere website bladert. Een van de webpagina&#39;s kan een HTML-afbeeldingstag met een `src` kenmerk dat een serverscript op de website van het slachtoffer aanwijst. Door het op cookies gebaseerde mechanisme voor sessieverificatie te gebruiken dat door webbrowsers wordt geboden, kan de aanvallende website kwaadaardige verzoeken verzenden naar dit script op de server van het slachtoffer, waarbij de vraag als de legitieme gebruiker wordt gesteld. Zie voor meer voorbeelden [https://owasp.org/www-community/attacks/csrf#Examples](https://owasp.org/www-community/attacks/csrf#Examples).

De volgende kenmerken komen voor in KVP:

* Neem sites op die afhankelijk zijn van de identiteit van een gebruiker.
* Gebruik het vertrouwen van de site in die identiteit.
* Steek de browser van de gebruiker in het verzenden van HTTP-aanvragen naar een doelsite.
* Neem HTTP-aanvragen op die bijwerkingen hebben.

AEM Forms on JEE gebruikt de functie Filter referentie om CSRF-aanvallen te blokkeren. In deze sectie worden de volgende termen gebruikt om het filtermechanisme van de verwijzer te beschrijven:

* **Toegestane referentie:** Een verwijzing is het adres van de bronpagina die een verzoek naar de server verzendt. Voor JSP-pagina&#39;s of -formulieren is de referentie meestal de vorige pagina in de browsergeschiedenis. Verwijzers voor afbeeldingen zijn meestal de pagina&#39;s waarop de afbeeldingen worden weergegeven. U kunt de Referrer identificeren die toegang tot uw servermiddelen door hen aan de Toegestane lijst van de Referant wordt verleend toe te voegen.
* **Uitzonderingen toegestane verwijzer:** U wilt mogelijk het bereik van toegang voor een bepaalde referentie beperken in uw lijst Toegestane referentie. Als u deze beperking wilt toepassen, kunt u afzonderlijke paden van die referentie toevoegen aan de lijst Toegestane uitzonderingen Referrer. Verzoeken die afkomstig zijn van paden in de lijst Toegestane uitzonderingen door verwijzers kunnen geen bron op de Forms-server aanroepen. U kunt de Uitzonderingen van de Verwijzer van de Toestemming voor een specifieke toepassing bepalen en ook een globale lijst van uitzonderingen gebruiken die op alle toepassingen van toepassing zijn.
* **Toegestane URI&#39;s:** Dit is een lijst met bronnen die moeten worden gebruikt zonder de koptekst van de verwijzer te controleren. De middelen, bijvoorbeeld, hulppagina&#39;s, die niet in staatsveranderingen op de server resulteren, kunnen aan deze lijst worden toegevoegd. De bronnen in de lijst Toegestane URI&#39;s worden nooit geblokkeerd door het filter Referrer, ongeacht wie de Referrer is.
* **Null-referentie:** Een serveraanvraag die niet is gekoppeld aan of niet afkomstig is van een bovenliggende webpagina, wordt beschouwd als een aanvraag van een Null-referentie. Wanneer u bijvoorbeeld een nieuw browservenster opent, typt u een adres en drukt u op Enter, is de referentie die naar de server is verzonden null. Een Desktoptoepassing (.NET of SWING) die een HTTP- verzoek aan een Webserver indienen, verzendt ook een Null Referrer naar de server.

### Filteren van referentie {#referer-filtering}

Het filterproces Referrer kan als volgt worden beschreven:

1. De Forms-server controleert de HTTP-methode die wordt gebruikt voor oproepen:

   1. Als het POST is, voert de Server van Forms de de kopbalcontrole van de Referteur uit.
   1. Als het GET is, wordt de controle Referrer door de Forms-server overgeslagen, tenzij *CSRF_CHECK_GETS* is ingesteld op true, in welk geval de koptekstcontrole Referrer wordt uitgevoerd. *CSRF_CHECK_GETS* wordt opgegeven in het dialoogvenster *web.xml* bestand voor uw toepassing.

1. De server van Forms controleert of gevraagde URI in lijst van gewenste personen bestaat:

   1. Als URI wordt gevoegd op lijst van gewenste personen, accepteert de server de aanvraag.
   1. Als gevraagde URI niet wordt gevoegd op lijst van gewenste personen, wint de server de Referrer van het verzoek terug.

1. Als er een Referrer in het verzoek is, controleert de server of het een Toegestane Referrer is. Als dit is toegestaan, controleert de server op een uitzondering Referrer:

   1. Als het een uitzondering is, wordt het verzoek geblokkeerd.
   1. Als het geen uitzondering is, wordt het verzoek overgegaan.

1. Als er geen Referrer in het verzoek is, controleert de server of een Null Referrer wordt toegestaan:

   1. Als een Null-referentie is toegestaan, wordt het verzoek doorgegeven.
   1. Als een Null Referrer niet wordt toegestaan, controleert de server of gevraagde URI een uitzondering voor de Null Referrer is en behandelt dienovereenkomstig het verzoek.

### Filteren van referenties beheren {#managing-referer-filtering}

AEM Forms on JEE biedt een Referrer Filter om Referrer op te geven die toegang krijgen tot uw serverbronnen. Standaard filtert het filter Referenter geen aanvragen die een veilige HTTP-methode gebruiken, bijvoorbeeld GET, tenzij *CSRF_CHECK_GETS* is ingesteld op true. Als het havenaantal voor een Toegestane ingang van de Verwijzing aan 0 wordt geplaatst, zal AEM Forms op JEE alle verzoeken met Referrer van die gastheer ongeacht het havenaantal toestaan. Als er geen poortnummer is opgegeven, zijn alleen aanvragen van standaardpoort 80 (HTTP) of poort 443 (HTTPS) toegestaan. Filteren met verwijzing is uitgeschakeld als alle items in de lijst Toegestane verwijzing worden verwijderd.

Wanneer u de Diensten van het Document eerst installeert, wordt de Toegestane lijst van de Verwijzing bijgewerkt met het adres van de server waarop de Diensten van het Document geïnstalleerd is. De ingangen voor de server omvatten de servernaam, het IPv4 adres, het IPv6 adres als IPv6 wordt toegelaten, het loopbackadres, en een localhost ingang. De namen die aan de lijst Toegestane verwijzing worden toegevoegd, worden geretourneerd door het hostbesturingssysteem. Bijvoorbeeld, zal een server met een IP adres van 10.40.54.187 de volgende ingangen omvatten: `https://server-name:0, https://10.40.54.187:0, https://127.0.0.1:0, http://localhost:0`. Voor om het even welke niet gekwalificeerde naam die door het werkende systeem van de Gastheer (namen wordt teruggegeven die geen IPv4 adres, IPv6 adres of gekwalificeerde domeinnaam) hebben wordt de lijst van gewenste personen niet bijgewerkt. Wijzig de Toegestane lijst van Referiteers om uw bedrijfsomgeving aan te passen. Implementeer de Forms-server niet in de productieomgeving met de standaardlijst Toegestane verwijzing. Nadat u een van de toegestane referentie-, referentie-uitzonderingen of URI&#39;s hebt gewijzigd, zorgt u ervoor dat de server opnieuw wordt gestart zodat de wijzigingen van kracht worden.

**Toegestane verwijzingslijst beheren**

U kunt de lijst Toegestane verwijzing beheren via de gebruikersbeheerinterface van de beheerconsole. De gebruikersbeheerinterface biedt u de functionaliteit om de lijst te maken, bewerken of verwijderen. Raadpleeg de * [Voorkomen van CSRF-aanvallen](/help/forms/using/admin-help/preventing-csrf-attacks.md)* deel van de *administratie Help* voor meer informatie over het werken met de Toegestane lijst van de Referant.

**Toegestane uitzondering Referrer en Toegestane URI-lijsten beheren**

AEM Forms on JEE biedt API&#39;s voor het beheer van de lijst Uitzondering toegestane verwijzing en de lijst Toegestane URI. U kunt deze API&#39;s gebruiken om de lijst op te halen, te maken, te bewerken of te verwijderen. Hieronder volgt een lijst met beschikbare API&#39;s:

* createAllowedURIsList
* getAllowedURIsList
* updateAllowedURIsList
* deleteAllowedURIsList
* addAllowedRefererExceptions
* getAllowedRefererExceptions
* updateAllowedRefererExceptions
* deleteAllowedRefererExceptions

Raadpleeg de* AEM Forms on JEE API Reference* voor meer informatie over de API&#39;s.

Gebruik de ***LC_GLOBAL_ALLOWED_REFERER_EXCEPTION*** lijst voor de Uitzonderingen van de Verwijzer van de Toegestane Verwijzing op het globale niveau dat, uitzonderingen bepaalt die op alle toepassingen van toepassing zijn. Deze lijst bevat alleen URI&#39;s met een absoluut pad (bijvoorbeeld `/index.html`) of een relatief pad (bijvoorbeeld `/sample/`). U kunt bijvoorbeeld ook een reguliere expressie aan het einde van een relatieve URI toevoegen. `/sample/(.)*`.

De ***LC_GLOBAL_ALLOWED_REFERER_EXCEPTION*** lijst-id is gedefinieerd als een constante in het dialoogvenster `UMConstants` klasse van de `com.adobe.idp.um.api` naamruimte, gevonden in `adobe-usermanager-client.jar`. Met de AEM Forms API&#39;s kunt u deze lijst maken, wijzigen of bewerken. Als u bijvoorbeeld de lijst Uitzonderingen globale toegestane verwijzingsverwijzing wilt maken, gebruikt u:

```java
addAllowedRefererExceptions(UMConstants.LC_GLOBAL_ALLOWED_REFERER_EXCEPTION, Arrays.asList("/index.html", "/sample/(.)*"))
```

Gebruik de ***CSRF_ALLOWED_REFERER_EXCEPTIONS*** lijst voor toepassingsspecifieke uitzonderingen.

**Het filter Referrer uitschakelen**

Als het filter Referrer de toegang tot de Forms-server volledig blokkeert en u de lijst Toegestane verwijzing niet kunt bewerken, kunt u het opstartscript van de server bijwerken en het filteren van referenties uitschakelen.

Inclusief de `-Dlc.um.csrffilter.disabled=true` JAVA-argument in het opstartscript en start de server opnieuw. Zorg ervoor dat u het argument JAVA schrapt nadat u correct de Toegestane lijst van de Verwijzing hebt aangepast.

**Filteren met referenties voor aangepaste WAR-bestanden**

Mogelijk hebt u aangepaste WAR-bestanden gemaakt die u met AEM Forms op JEE kunt gebruiken om aan uw zakelijke vereisten te voldoen. Als u Referrer Filteren wilt inschakelen voor uw aangepaste WAR-bestanden, neemt u ***adobe-usermanager-client.jar*** in het klassepad voor de WAR en neem een filteritem op in het bestand* web.xml* met de volgende parameters:

**CSRF_CHECK_GETS** controleert de controle van de Referateur op verzoeken van GET. Wanneer deze parameter niet is gedefinieerd, wordt de standaardwaarde op false ingesteld. Neem deze parameter alleen op als u uw GET-aanvragen wilt filteren.

**CSRF_ALLOWED_REFERER_EXCEPTIONS** Dit is de id van de lijst Uitzonderingen toegestane verwijzing. Het filter Referrer verhindert verzoeken afkomstig van Verwijzers in de lijst die door lijstidentiteitskaart wordt geïdentificeerd, om het even welke middelen op de Server van Forms te roepen.

**CSRF_ALLOWED_URIS_LIST_NAME** Dit is de id van de lijst Toegestane URI&#39;s. Het filter Referrer blokkeert geen aanvragen voor een van de bronnen in de lijst die door de lijst-id wordt geïdentificeerd, ongeacht de waarde van de verwijzaarheader in de aanvraag.

**CSRF_ALLOW_NULL_REFERER** Hiermee wordt het gedrag Filter referentie ingesteld wanneer de verwijzer null is of niet aanwezig is. Wanneer deze parameter niet is gedefinieerd, wordt de standaardwaarde op false ingesteld. Neem deze parameter alleen op als u Null-referenties wilt toestaan. Het toestaan van ongeldige verwijzers kan sommige types van het Verzoek van de Vervalsing van de Plaats van de Overeenkomst toestaan.

**CSRF_NULL_REFERER_EXCEPTIONS** is een lijst van URIs waarvoor een controle van de Referateur niet wordt uitgevoerd wanneer de Referteur ongeldig is. Deze parameter wordt alleen ingeschakeld wanneer *CSRF_ALLOW_NULL_REFERER* is ingesteld op false. Scheid meerdere URI&#39;s in de lijst met een komma.

Hier volgt een voorbeeld van het filteritem in het dialoogvenster *web.xml* bestand voor een ***MONSTER*** WAR-bestand:

```java
<filter> 
       <filter-name> filter-name </filter-name> 
       <filter-class> com.adobe.idp.um.auth.filter.RemoteCSRFFilter </filter-class> 
     <!-- default is false --> 
     <init-param> 
      <param-name> CSRF_ALLOW_NULL_REFERER </param-name> 
      <param-value> false </param-value> 
     </init-param> 
     <!-- default is false --> 
     <init-param> 
      <param-name> CSRF_CHECK_GETS </param-name> 
      <param-value> true </param-value> 
     </init-param> 
     <!-- Optional --> 
     <init-param> 
       <param-name> CSRF_NULL_REFERER_EXCEPTIONS </param-name> 
       <param-value> /SAMPLE/login, /SAMPLE/logout  </param-value> 
     </init-param> 
     <!-- Optional --> 
     <init-param> 
      <param-name> CSRF_ALLOWED_REFERER_EXCEPTIONS </param-name> 
      <param-value> SAMPLE_ALLOWED_REF_EXP_ID </param-value> 
     </init-param> 
     <!-- Optional --> 
     <init-param> 
      <param-name> CSRF_ALLOWED_URIS_LIST_NAME </param-name> 
      <param-value> SAMPLE_ALLOWED_URI_LIST_ID     </param-value> 
     </init-param> 
</filter> 
    ........ 
    <filter-mapping> 
      <filter-name> filter-name </filter-name> 
      <url-pattern>/*</url-pattern> 
    </filter-mapping>
```

**Problemen oplossen**

Als de legitieme serververzoeken door het filter CSRF worden geblokkeerd, probeer één van het volgende:

* Als het afgewezen verzoek een verwijzingskopbal heeft, denk zorgvuldig na toevoegend het aan de Toegestane lijst van de Referant. Voeg alleen de referentie toe die u vertrouwt.
* Als het afgewezen verzoek geen verwijzingskopbal heeft, wijzig uw cliënttoepassing om een verwijzingskopbal te omvatten.
* Als de client in een browser kan werken, probeert u dat implementatiemodel.
* Als laatste redmiddel kunt u het middel aan de Toegestane lijst URIs toevoegen. Dit is geen aanbevolen instelling.

## Beveiligde netwerkconfiguratie {#secure-network-configuration}

Deze sectie beschrijft de protocollen en de havens die door AEM Forms op JEE worden vereist en verstrekt aanbevelingen voor het opstellen van AEM Forms op JEE in een veilige netwerkconfiguratie.

### Netwerkprotocollen die door AEM Forms op JEE worden gebruikt {#network-protocols-used-by-aem-forms-on-jee}

Wanneer u een veilige netwerkarchitectuur zoals die in de vorige sectie wordt beschreven vormt, worden de volgende netwerkprotocollen vereist voor interactie tussen AEM Forms op JEE en andere systemen in uw ondernemingsnetwerk.

<table> 
 <thead> 
  <tr> 
   <th><p>Protocol</p> </th> 
   <th><p>Gebruiken</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>HTTP</p> </td> 
   <td> 
    <ul> 
     <li><p>Browser toont de Manager van de Configuratie en de toepassingen van het eindgebruikerWeb</p> </li> 
     <li><p>Alle SOAP-verbindingen</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>SOAP</p> </td> 
   <td> 
    <ul> 
     <li><p>De de dienstcliënttoepassingen van het Web, zoals .NET toepassingen</p> </li> 
     <li><p>Adobe Reader® gebruikt SOAP voor AEM Forms op JEE-server webservices</p> </li> 
     <li><p>Adobe Flash®-toepassingen gebruiken SOAP voor Forms Server-webservices</p> </li> 
     <li><p>AEM Forms op JEE SDK-aanroepen bij gebruik in SOAP-modus</p> </li> 
     <li><p>Workbench ontwerpomgeving</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>RMI</p> </td> 
   <td><p>AEM Forms op JEE SDK-aanroepen bij gebruik in de modus Enterprise JavaBeans (EJB)</p> </td> 
  </tr> 
  <tr> 
   <td><p>IMAP/POP3</p> </td> 
   <td> 
    <ul> 
     <li><p>Op e-mail-gebaseerde input aan de dienst (E-maileindpunt)</p> </li> 
     <li><p>Taakmeldingen gebruiker via e-mail</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>UNC-bestand IO</p> </td> 
   <td><p>AEM Forms on JEE bewaking van gecontroleerde mappen voor invoer naar een service (gecontroleerd mapeindpunt)</p> </td> 
  </tr> 
  <tr> 
   <td><p>LDAP</p> </td> 
   <td> 
    <ul> 
     <li><p>Synchronisaties van gebruikers- en groepsgegevens in een directory</p> </li> 
     <li><p>LDAP-verificatie voor interactieve gebruikers</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>JDBC</p> </td> 
   <td> 
    <ul> 
     <li><p>Vraag en procedurevraag aan een extern gegevensbestand tijdens uitvoering van een proces die de dienst JDBC gebruikt wordt gemaakt</p> </li> 
     <li><p>Interne toegang AEM Forms op JEE-opslagplaats</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>WebDAV</p> </td> 
   <td><p>Maakt het op afstand doorbladeren van de AEM Forms in de JEE design-time opslagruimte (formulieren, fragmenten, enzovoort) door elke WebDAV-client mogelijk</p> </td> 
  </tr> 
  <tr> 
   <td><p>AMF</p> </td> 
   <td><p>De toepassingen van de Flash van de Adobe, waar AEM Forms op de serverdiensten JEE met een Verwijderend eindpunt wordt gevormd</p> </td> 
  </tr> 
  <tr> 
   <td><p>JMX</p> </td> 
   <td><p>AEM Forms on JEE stelt MBans beschikbaar voor controle met JMX</p> </td> 
  </tr> 
 </tbody> 
</table>

### Poorten voor toepassingsservers {#ports-for-application-servers}

Deze sectie beschrijft de standaardhavens (en afwisselende configuratiereiken) voor elk type van gesteunde toepassingsserver. Deze poorten moeten in- of uitgeschakeld zijn op de binnenfirewall, afhankelijk van de netwerkfunctionaliteit die u wilt toestaan voor clients die verbinding maken met de toepassingsserver waarop AEM Forms op JEE wordt uitgevoerd.

>[!NOTE]
>
>De server stelt standaard verschillende JMX MBans beschikbaar onder de naamruimte adobe.com. Alleen informatie die nuttig is voor de bewaking van de serverstatus wordt weergegeven. Nochtans, om informatieonthulling te verhinderen, zou u bezoekers in een onvertrouwd netwerk moeten verhinderen omhoog JMX MBans te kijken en tot gezondheidsmetriek toegang te hebben.

**JBoss-poorten**

<table> 
 <thead> 
  <tr> 
   <th><p>Doel</p> </th> 
   <th><p>Poort</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Toegang tot webtoepassingen</p> </td> 
   <td><p>[JBOSS_Root]/standalone/configuration/lc_[database].xml</p> <p>HTTP/1.1 Connector poort 8080</p> <p>AJP 1.3 Connector poort 8009</p> <p>SSL/TLS-connectorpoort 8443</p> </td> 
  </tr> 
  <tr> 
   <td><p>CORBA-ondersteuning</p> </td> 
   <td><p>[JBoss root]/server/all/conf/jacorb.properties</p> <p>OAPort 3528</p> <p>OASSLPort 3529</p> </td> 
  </tr> 
 </tbody> 
</table>

**WebLogic-poorten**

<table> 
 <thead> 
  <tr> 
   <th><p>Doel</p> </th> 
   <th><p>Poort</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Toegang tot webtoepassingen</p> </td> 
   <td> 
    <ul> 
     <li><p>Admin Server listen-poort: de standaardwaarde is 7001</p> </li> 
     <li><p>SSL-luisterpoort van beheerserver: de standaardwaarde is 7002</p> </li> 
     <li><p>Poort geconfigureerd voor beheerde server, bijvoorbeeld 8001</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>WebLogic-beheerpoorten niet vereist voor toegang tot AEM Forms op JEE</p> </td> 
   <td> 
    <ul> 
     <li><p>Beheerde serverluisterpoort: configureerbaar van 1 tot 65534</p> </li> 
     <li><p>Managed Server SSL listen port: configureerbaar van 1 tot 65534</p> </li> 
     <li><p>Node Manager luistert poort: de standaardwaarde is 5556</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**WebSphere-poorten**

Voor informatie over havens WebSphere die AEM Forms op JEE vereist, ga naar het aantal dat van de Haven in WebSphere de Server UI van de Toepassing plaatst.

### SSL configureren {#configuring-ssl}

Verwijzen naar de fysieke architectuur die in de sectie wordt beschreven [AEM Forms op JEE fysieke architectuur](hardening-aem-forms-jee-environment.md#aem-forms-on-jee-physical-architecture)moet u SSL configureren voor alle verbindingen die u wilt gebruiken. Specifiek, moeten alle verbindingen van de ZEEP over SSL worden geleid om blootstelling van gebruikersgeloofsbrieven op een netwerk te verhinderen.

Voor instructies over hoe te om SSL op JBoss, WebLogic, en WebSphere te vormen, zie &quot;het Vormen SSL&quot;in [administratie Help](https://www.adobe.com/go/learn_aemforms_admin_64).

Voor instructies over het importeren van certificaten naar JVM (Java Virtual Machine) die zijn geconfigureerd voor een AEM Forms-server, raadpleegt u de sectie Wederzijdse verificatie in [Help bij AEM Forms Workbench](https://www.adobe.com/go/learn_aemforms_workbench_65).

### SSL-omleiding configureren {#configuring-ssl-redirect}

Nadat u uw toepassingsserver vormt om SSL te steunen, moet u ervoor zorgen dat al verkeer van HTTP aan toepassingen en de diensten wordt afgedwongen om de SSL haven te gebruiken.

Raadpleeg de documentatie bij de toepassingsserver voor informatie over SSL-omleiding voor WebSphere of WebLogic.

1. Open bevelherinnering, navigeer aan /JBOSS_HOME/standalone/configuratiemap, en voer het volgende bevel uit:

   `keytool -genkey -alias jboss7 -keyalg RSA -keystore server.keystore -validity 10950`

1. Open het bestand JBOSS_HOME/standalone/configuration/standalone.xml voor bewerking.

   Na de &lt;subsystem xmlns=&quot;urn&lt;span id=&quot; translate=&quot;no&quot; />domein:web:1.1&quot; native=&quot;false&quot; default-virtual-server=&quot;default-host&quot;>-element, voeg de volgende details toe::jboss:

   &lt;connector name=&quot;https&quot; protocol=&quot;HTTP/1.1&quot; scheme=&quot;https&quot; socket-binding=&quot;https&quot; enabled=&quot;true&quot; secure=&quot;true&quot;/>

1. Voeg de volgende code toe in het https-verbindingselement:

   ```xml
   <connector name="https" protocol="HTTP/1.1" scheme="https" socket-binding="https" secure="true" enabled="true"> 
    <ssl name="jboss7_ssl" key-alias="jboss71" password="Tibco321" certificate-key-file="../standalone/configuration/server.keystore" protocol="TLSv1"/> 
    </connector>
   ```

   Sla het bestand standalone.xml op en sluit het.

## Windows-specifieke beveiligingsaanbevelingen {#windows-specific-security-recommendations}

Deze sectie bevat veiligheidsaanbevelingen die voor Vensters wanneer gebruikt specifiek zijn om AEM Forms op JEE in werking te stellen.

### JBoss-serviceaccounts {#jboss-service-accounts}

Bij de turnkey-installatie van AEM Forms op JEE wordt standaard een serviceaccount ingesteld met behulp van de lokale systeemaccount. De ingebouwde Lokale de gebruikersrekening van het Systeem heeft een hoog niveau van toegankelijkheid; het maakt deel uit van de groep van Beheerders. Als de identiteit van een arbeidersproces als Lokale de gebruikersrekening van het Systeem loopt, heeft dat arbeidersproces volledige toegang tot het volledige systeem.

#### De toepassingsserver uitvoeren met een niet-beheeraccount {#run-the-application-server-using-a-non-administrative-account}

1. Maak in de Microsoft Management Console (MMC) een lokale gebruiker voor de Forms Server-service om u aan te melden als:

   * Selecteren **Gebruiker kan wachtwoord niet wijzigen**.
   * Op de **Lid van** selecteert, controleert u of de gebruikersgroep wordt weergegeven.

1. Selecteren **Instellingen** > **Administratieve gereedschappen** > **Services**.
1. Dubbelklik op de service van de toepassingsserver en stop de service.
1. Op de **Aanmelden** tab, selecteert u **Dit account** Blader naar de gebruikersaccount die u hebt gemaakt en voer het wachtwoord voor de account in.
1. Geef in het venster Lokale beveiligingsinstellingen onder Toewijzing gebruikersrechten de volgende rechten op de gebruikersaccount waarop de Forms-server wordt uitgevoerd:

   * Ontken login door de EindDiensten
   * Aanmelding lokaal weigeren
   * Aanmelden als service (moet al zijn ingesteld)

1. Wijzig de machtigingen voor de nieuwe gebruikersaccount voor de volgende directory&#39;s:
   * **GDS-map (Global Document Storage)**: De locatie van de GDS-map wordt handmatig geconfigureerd tijdens het AEM Forms-installatieproces. Als de locatie-instelling tijdens de installatie leeg blijft, wordt de locatie standaard ingesteld op een directory onder de installatie van de toepassingsserver op `[JBoss root]/server/[type]/svcnative/DocumentStorage`
   * **CRX-opslagmap**: De standaardlocatie is `[AEM-Forms-installation-location]\crx-repository`
   * **Tijdelijke AEM Forms-mappen**:
      * (Windows) TMP- of TEMP-pad zoals ingesteld in de omgevingsvariabelen
      * (AIX, Linux, of Solaris) Logged-in de huisfolder van de gebruiker op op UNIX-Gebaseerde systemen, kan een niet wortelgebruiker de volgende folder als tijdelijke folder gebruiken:
      * (Linux) /var/tmp of /usr/tmp
      * (AIX) /tmp of /usr/tmp
      * (Solaris) /var/tmp of /usr/tmp
1. Geef de nieuwe gebruikersaccount schrijfmachtigingen voor de volgende directory&#39;s:
   * [JBoss-directory]\standalone\nimplementatie
   * [JBoss-directory]\standalone\
   * [JBoss-directory]\bin\

   >[!NOTE]
   >
   >De standaardinstallatielocatie van JBoss Application Server:
   >
   >* Windows: C:\Adobe\Adobe_Experience_Manager_Forms\jboss
   >* Linux: /opt/jreliëf/.

1. Start de service van de toepassingsserver.

### Beveiliging bestandssysteem {#file-system-security}

AEM Forms on JEE gebruikt het bestandssysteem op de volgende manieren:

* Hiermee worden tijdelijke bestanden opgeslagen die worden gebruikt bij de verwerking van de invoer en uitvoer van documenten
* Slaat dossiers in het globale archiefopslag op die worden gebruikt om de oplossingscomponenten te steunen die worden geïnstalleerd
* Gecontroleerde mappen slaan neergezette bestanden op die worden gebruikt als invoer voor een service vanaf de locatie van een bestandssysteemmap

Als u gecontroleerde mappen gebruikt als een manier om documenten te verzenden en te ontvangen met een Forms Server-service, moet u extra voorzorgsmaatregelen treffen met betrekking tot de beveiliging van het bestandssysteem. Wanneer een gebruiker inhoud in de controlemap neerzet, wordt die inhoud via de controlemap weergegeven. In dit geval wordt de werkelijke eindgebruiker niet geverifieerd door de service. In plaats daarvan, baseert het zich op ACL en het niveauveiligheid van het Aandeel op het omslagniveau om te bepalen wie de dienst kan effectief aanhalen.

## JBoss-specifieke veiligheidsaanbevelingen {#jboss-specific-security-recommendations}

Deze sectie bevat aanbevelingen voor de configuratie van toepassingsservers die specifiek zijn voor JBoss 7.0.6 wanneer deze wordt gebruikt om AEM Forms uit te voeren op JEE.

### JBoss Management Console en JMX Console uitschakelen {#disable-jboss-management-console-and-jmx-console}

De toegang tot de JBoss Management Console en de Console JMX is reeds gevormd (JMX controle wordt onbruikbaar gemaakt) wanneer u AEM Forms op JEE op JBoss door de kant-en-klare installatiemethode te gebruiken installeert. Als u uw eigen JBoss Server van de Toepassing gebruikt, zorg ervoor dat de toegang tot de Console van het Beheer JBoss en JMX controleconsole wordt beveiligd. De toegang tot de JMX controleconsole wordt geplaatst in het JBoss configuratiedossier genoemd jmx-invoker-service.xml.

### Bladeren door directory&#39;s uitschakelen {#disable-directory-browsing}

Na het registreren in de Console van het Beleid, is het mogelijk om de de folderlijst van de console te doorbladeren door URL te wijzigen. Als u bijvoorbeeld de URL wijzigt in een van de volgende URL&#39;s, wordt mogelijk een mappenlijst weergegeven:

```java
https://<servername>:8080/adminui/secured/ 
https://<servername>:8080/um/
```

## WebLogic-specifieke beveiligingsaanbevelingen {#weblogic-specific-security-recommendations}

Deze sectie bevat aanbevelingen voor de configuratie van toepassingsservers voor het beveiligen van WebLogic 9.1 wanneer AEM Forms wordt uitgevoerd op JEE.

### Bladeren door directory&#39;s uitschakelen {#disable_directory_browsing-1}

Stel de eigenschappen voor indexmappen in het bestand weblogic.xml in op `false`, zoals in dit voorbeeld wordt getoond:

```xml
<container-descriptor> 
    <index-directory-enabled>false 
    </index-directory-enabled> 
</container-descriptor>
```

### WebLogic SSL-poort inschakelen {#enable-weblogic-ssl-port}

Standaard schakelt WebLogic de standaard SSL-luisterpoort 7002 niet in. Schakel deze poort in de WebLogic Server Administration Console in voordat u SSL configureert.

## WebSphere-specifieke beveiligingsaanbevelingen {#websphere-specific-security-recommendations}

Deze sectie bevat aanbevelingen voor de configuratie van de toepassingsserver om WebSphere te beveiligen die AEM Forms op JEE uitvoert.

### Bladeren door directory&#39;s uitschakelen {#disable_directory_browsing-2}

Stel de `directoryBrowsingEnabled` eigenschap in het bestand ibm-web-ext.xml naar `false`.

### Beveiliging WebSphere inschakelen {#enable-websphere-administrative-security}

1. Meld u aan bij de beheerconsole van WebSphere.
1. Ga in de navigatiestructuur naar **Beveiliging** > **Algemene beveiliging**
1. Selecteren **Beheersbeveiliging inschakelen**.
1. Selectie opheffen **Toepassingsbeveiliging inschakelen** en **Java 2-beveiliging gebruiken**.
1. Klikken **OK** of **Toepassen**.
1. In de **Berichten** vak, klikt u op **Direct opslaan in de hoofdconfiguratie**.
