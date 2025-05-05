---
title: AEM Forms versterken op JEE-omgeving
description: Leer een verscheidenheid van veiligheid-verhardende montages om de veiligheid van AEM Forms op JEE te verbeteren die in een collectieve Intranet loopt.
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
role: Admin,User
exl-id: 6fb260f9-d0f8-431e-8d4e-535b451e4124
solution: Experience Manager, Experience Manager Forms
feature: Document Security,Adaptive Forms
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '7608'
ht-degree: 0%

---

# AEM Forms versterken op JEE-omgeving {#hardening-your-aem-forms-on-jee-environment}

Leer een verscheidenheid van veiligheid-verhardende montages om de veiligheid van AEM Forms op JEE te verbeteren die in een collectieve Intranet loopt.

In het artikel worden aanbevelingen en aanbevolen procedures beschreven voor het beveiligen van servers die AEM Forms uitvoeren op JEE. Dit is geen uitgebreid host-hardend document voor uw besturingssysteem en toepassingsservers. In plaats daarvan, beschrijft dit artikel een verscheidenheid van veiligheid-verhardende montages die u zou moeten uitvoeren om de veiligheid van AEM Forms op JEE te verbeteren die binnen een collectief Intranet loopt. Om ervoor te zorgen dat de AEM Forms op JEE toepassingsservers veilig blijft, echter, zou u veiligheid controle, opsporing, en reactieprocedures ook moeten uitvoeren.

In het artikel worden verhardingstechnieken beschreven die tijdens de levenscyclus van de installatie en configuratie in de volgende fasen moeten worden toegepast:

* **pre-installatie:** gebruik deze technieken alvorens u AEM Forms op JEE installeert.
* **Installatie:** gebruik deze technieken tijdens AEM Forms op JEE installatieproces.
* **Post-installatie:** gebruik deze technieken na installatie en periodiek daarna.

AEM Forms on JEE is zeer aanpasbaar en kan in vele verschillende omgevingen werken. Sommige aanbevelingen passen mogelijk niet in de behoeften van uw organisatie.

## Voorinstallatie {#preinstallation}

Voordat u AEM Forms op JEE installeert, kunt u beveiligingsoplossingen toepassen op de netwerklaag en het besturingssysteem. In deze sectie worden enkele problemen beschreven en worden aanbevelingen gedaan om beveiligingsrisico&#39;s op deze gebieden te verminderen.

**Installatie en configuratie op UNIX en Linux**

U moet AEM Forms niet installeren of configureren op JEE met behulp van een hoofdshell. Standaard worden bestanden geïnstalleerd onder de map /opt en heeft de gebruiker die de installatie uitvoert, alle bestandsmachtigingen onder /opt nodig. Alternatief, kan een installatie onder de /user folder van een individuele gebruiker worden uitgevoerd waar zij reeds alle dossiertoestemmingen hebben.

**Installatie en configuratie op Vensters**

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
     <li><p>Voer firewalls uit die volmachtsservers en/of <em> stateful inspectie </em> in plaats van eenvoudige pakket-filtrerende oplossingen steunen.</p> </li> 
     <li><p>Gebruik een firewall die a <em> steunt ontkent alle diensten behalve die uitdrukkelijk toegelaten </em> veiligheidsparadigma's.</p> </li> 
     <li><p>Voer een firewalloplossing uit die dubbel-homed of multihomed is. Deze architectuur biedt het grootste beveiligingsniveau en helpt te voorkomen dat onbevoegde gebruikers de firewallbeveiliging omzeilen.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Databasepoorten</p> </td> 
   <td><p>Gebruik geen standaard luisterpoorten voor databases (MySQL - 3306, Oracle - 1521, MS SQL - 1433). Raadpleeg de documentatie bij uw database voor informatie over het wijzigen van databasepoorten.</p> <p>Het gebruiken van een verschillende gegevensbestandhaven beïnvloedt algemene AEM Forms op configuratie JEE. Als u standaardhavens verandert, moet u overeenkomstige wijzigingen in andere gebieden van configuratie, zoals de gegevensbronnen voor AEM Forms op JEE aanbrengen.</p> <p>Voor informatie over het vormen van gegevensbronnen in AEM Forms op JEE, zie installeer en bevordert AEM Forms op JEE of Bevorderend aan AEM Forms op JEE voor uw toepassingsserver bij <a href="/help/forms/using/introduction-aem-forms.md" target="_blank"> AEM Forms gebruikersgids </a>.</p> </td> 
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

Voor extra veiligheidsinformatie voor uw werkend systeem, zie [ &quot;de veiligheidsinformatie van het werkende systeem&quot;](https://helpx.adobe.com/aem-forms/6-1/hardening-security/general-security-considerations.html#operating_system_security_information).

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
   <td><p>Gebruik het minste aantal rechten dat nodig is om de software te installeren. Meld u aan bij uw computer met een account die zich niet in de groep Beheerders bevindt. In Windows kunt u de opdracht Uitvoeren als gebruiken om het AEM Forms-installatieprogramma van JEE als een beheergebruiker uit te voeren. Op UNIX- en Linux-systemen gebruikt u een opdracht zoals <code>sudo</code> om de software te installeren.</p> </td> 
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
   <td><p>De aanwezigheid van een <code>crossdomain.xml</code> -bestand op de server kan de server direct verzwakken. U wordt aangeraden de lijst met domeinen zo restrictief mogelijk te maken. Plaats niet het <code>crossdomain.xml</code> dossier dat tijdens ontwikkeling in productie toen het gebruiken van Gidsen <em> (afgekeurd) </em> werd gebruikt. Voor een gids die de Webdiensten gebruikt, als de dienst op de zelfde server is die de gids opdiende, is een <code>crossdomain.xml</code> dossier helemaal niet nodig. Maar als de service zich op een andere server bevindt of als er clusters bij betrokken zijn, is de aanwezigheid van een <code>crossdomain.xml</code> -bestand vereist. Verwijs naar <a href="https://kb2.adobe.com/cps/142/tn_14213.html"> https://kb2.adobe.com/cps/142/tn_14213.html </a>, voor meer informatie over het crossdomain.xml- dossier.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Beveiligingsinstellingen van besturingssysteem</p> </td> 
   <td><p>Als u 192-bits of 256-bits XML-codering op Solaris-platforms moet gebruiken, moet u <code>pkcs11_softtoken_extra.so</code> installeren in plaats van <code>pkcs11_softtoken.so</code> .</p> </td> 
  </tr> 
 </tbody> 
</table>

## Post-installatiestappen {#post-installation-steps}

Nadat u AEM Forms met succes op JEE installeert, is het belangrijk om het milieu uit veiligheidsperspectief periodiek te handhaven.

De volgende sectie beschrijft in detail de verschillende taken die worden geadviseerd om de opgestelde Server van Forms te beveiligen.

### AEM Forms-beveiliging {#aem-forms-security}

De volgende aanbevolen instellingen gelden voor de AEM Forms op de JEE-server buiten de beheerwebtoepassing. Als u de beveiligingsrisico&#39;s voor de server wilt beperken, past u deze instellingen direct toe nadat u AEM Forms op JEE hebt geïnstalleerd.

**de flarden van de Veiligheid**

Er is een verhoogd risico dat een onbevoegde gebruiker toegang tot de toepassingsserver zou kunnen krijgen als de patches en upgrades van de verkopersveiligheid niet tijdig worden toegepast. Test beveiligingspatches voordat u ze op productieservers toepast om de compatibiliteit en beschikbaarheid van toepassingen te garanderen. Ook kunt u beleidsregels en procedures maken om regelmatig te controleren op patches en deze te installeren. AEM Forms on JEE-updates zijn beschikbaar op de downloadsite voor Enterprise-producten.

**de rekeningen van de Dienst (JBoss turnkey op Vensters slechts)**

AEM Forms on JEE installeert standaard een service via de LocalSystem-account. De ingebouwde gebruikersrekening LocalSystem heeft een hoog niveau van toegankelijkheid; het maakt deel uit van de groep van Beheerders. Als een worker-process-identiteit wordt uitgevoerd als LocalSystem-gebruikersaccount, heeft dat arbeidersproces volledige toegang tot het gehele systeem.

Volg de onderstaande instructies om de toepassingsserver uit te voeren waarop AEM Forms op JEE wordt geïmplementeerd met een specifieke niet-beheeraccount:

1. Maak in de Microsoft Management Console (MMC) een lokale gebruiker voor de Forms Server-service om u aan te melden als:

   * Selecteer **Gebruiker kan geen wachtwoord** veranderen.
   * Op het **Lid van** lusje, zorg ervoor dat de **gebruikers** groep vermeld is.

   >[!NOTE]
   >
   >U kunt deze instelling voor PDF Generator niet wijzigen.

1. Selecteer **Begin** > **Montages** > **Administratieve Hulpmiddelen** > **de Diensten**.
1. Dubbelklik op JBoss voor AEM Forms op JEE en stop de service.
1. Op het **Logboek** lusje, selecteer **Deze Rekening**, doorblader voor de gebruikersrekening u creeerde, en ga het wachtwoord voor de rekening in.
1. In MMC, open **Lokale Montages van de Veiligheid** en selecteer **Lokaal Beleid** > **Toewijzing van de Rechten van de Gebruiker**.
1. Wijs de volgende rechten toe aan de gebruikersaccount waarop de Forms Server wordt uitgevoerd:

   * Ontken login door de EindDiensten
   * Aanmelden lokaal weigeren
   * Aanmelden als service (moet al zijn ingesteld)

1. Wijzig de machtigingen voor de nieuwe gebruikersaccount voor de volgende directory&#39;s:
   * **Globale folder van de Opslag van het Document (GDS)**: De plaats van de GDS folder wordt gevormd manueel tijdens het installatieproces van AEM Forms. Als de locatie-instelling tijdens de installatie leeg blijft, wordt standaard een map onder de installatie van de toepassingsserver op `[JBoss root]/server/[type]/svcnative/DocumentStorage` weergegeven
   * **CRX-Repository folder**: De standaardplaats is `[AEM-Forms-installation-location]\crx-repository`
   * **tijdelijke folders van AEM Forms**:
      * (Windows) TMP- of TEMP-pad zoals ingesteld in de omgevingsvariabelen
      * (AIX, Linux, of Solaris) Logged-in de huisfolder van de gebruiker
Op UNIX-gebaseerde systemen, kan een niet-wortelgebruiker de volgende folder als tijdelijke folder gebruiken:
      * (Linux) /var/tmp of /usr/tmp
      * (AIX) /tmp of /usr/tmp
      * (Solaris) /var/tmp of /usr/tmp
1. Geef de nieuwe gebruikersaccount schrijfmachtigingen voor de volgende directory&#39;s:
   * [ JBoss-folder ] \ standalone \ plaatsing
   * [ JBoss-folder ] \ standalone\
   * [ JBoss-folder ] \ bak \

   >[!NOTE]
   >
   >De standaardinstallatielocatie van JBoss Application Server:
   >
   >* Windows: C:\Adobe\Adobe_Experience_Manager_Forms\jboss
   >* Linux: /opt/jreliëf/

1. Start de toepassingsserver.

**onbruikbaar makend bootstrap servlet van de Manager van de Configuratie**

Configuration Manager maakte gebruik van een servlet die op uw toepassingsserver wordt opgesteld om bootstrapping van AEM Forms op gegevensbestand uit te voeren JEE. Omdat de Manager van de Configuratie tot dit servlet toegang heeft alvorens de configuratie volledig is, is de toegang tot het niet beveiligd voor erkende gebruikers, en het zou moeten worden onbruikbaar gemaakt nadat u met succes de Manager van de Configuratie hebt gebruikt om AEM Forms op JEE te vormen.

1. Pak adobe-livecycle uit [ appserver ] .ear- dossier.
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

**Vergrendeling verre toegang tot de Opslag van het Vertrouwen**

Met Configuratiebeheer kunt u een Acrobat Reader DC-extensie uploaden die is gecrediteerd aan de AEM Forms in de JEE-vertrouwde opslag. Dit betekent dat de toegang tot de Dienst van de Referentie van de Opslag van het Vertrouwen over verre protocollen (SOAP en EJB) door gebrek is toegelaten. Deze toegang is niet meer noodzakelijk nadat u de credentie van Rechten gebruikend de Manager van de Configuratie hebt geupload of als u besluit om de Console van het Beleid later te gebruiken om geloofsbrieven te beheren.

U kunt verre toegang tot alle diensten van de Opslag van het Vertrouwen onbruikbaar maken door de stappen in de sectie [ te volgen onbruikbaar makend niet-essentiële verre toegang tot de diensten ](https://helpx.adobe.com/aem-forms/6-1/hardening-security/configuring-secure-administration-settings-aem.html#disabling_non_essential_remote_access_to_services).

**maak al niet essentiële anonieme toegang** onbruikbaar

Sommige diensten van de Server van Forms hebben verrichtingen die door een anonieme bezoeker kunnen worden aangehaald. Als de anonieme toegang tot deze diensten niet wordt vereist, maak het onbruikbaar door de stappen in [ te volgen onbruikbaar makend niet-essentiële anonieme toegang tot de diensten ](https://helpx.adobe.com/aem-forms/6-1/hardening-security/configuring-secure-administration-settings-aem.html#disabling_non_essential_anonymous_access_to_services).

#### Het standaardbeheerderswachtwoord wijzigen {#change-the-default-administrator-password}

Wanneer AEM Forms op JEE wordt geïnstalleerd, wordt één enkele standaardgebruikersrekening gevormd voor gebruiker Super Beheerder/login-id Beheerder met een standaardwachtwoord van *wachtwoord*. U zou dit wachtwoord onmiddellijk moeten veranderen gebruikend de Manager van de Configuratie.

1. Typ de volgende URL in een webbrowser:

   ```java
   https://[host name]:[port]/adminui
   ```

   Het standaardpoortnummer is een van de volgende:

   **JBoss:** 8080

   **Server WebLogic:** 7001

   **9080 WebSphere.**

1. Op het **gebied van de Naam van 0&rbrace; Gebruiker {, type `administrator` en, op het** 4} gebied van het Wachtwoord &lbrace;, type `password`.**&#x200B;**
1. Klik **Montages** > **Gebruikersbeheer** > **Gebruikers en Groepen**.
1. Het type `administrator` op het **Vondst** gebied, en klikt **Vondst**.
1. Klik **Beheerder van de Leverancier** van de lijst van gebruikers.
1. Klik **Wachtwoord van de Verandering** op de Edit pagina van de Gebruiker.
1. Specificeer het nieuwe wachtwoord en klik **sparen**.

Daarnaast wordt aangeraden het standaardwachtwoord voor CRX Administrator te wijzigen door de volgende stappen uit te voeren:

1. Meld u aan bij `https://[server]:[port]/lc/libs/granite/security/content/useradmin.html` met de standaardgebruikersnaam/het standaardwachtwoord.
1. De Beheerder van het type op het onderzoeksgebied en klikt **gaan**.
1. Selecteer **Beheerder** van het onderzoeksresultaat en klik **uitgeven** pictogram bij het lagere recht van het gebruikersinterface.
1. Specificeer het nieuwe wachtwoord op het **Nieuwe gebied van het Wachtwoord** en het oude wachtwoord op het **Uw Wachtwoord** gebied.
1. Klik op het pictogram Opslaan rechtsonder in de gebruikersinterface.

#### WSDL-generatie uitschakelen {#disable-wsdl-generation}

De generatie van de Definitie van de Taal van de Dienst van het Web (WSDL) zou slechts voor ontwikkelomgevingen moeten worden toegelaten, waar de generatie WSDL door ontwikkelaars wordt gebruikt om hun cliënttoepassingen te bouwen. U kunt verkiezen om de generatie van WSDL in een productiemilieu onbruikbaar te maken vermijden blootstellend de interne details van de dienst.

1. Typ de volgende URL in een webbrowser:

   ```java
   https://[host name]:[port]/adminui
   ```

1. Selecteer **Montages > de Montages van het Systeem van de Kern > Configuraties**.
1. Deselecteer **WSDL** toelaten, dan selecteren **O.K.**.

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
   <td><p>Toepassingscookies worden beheerd door de toepassingsserver. Bij het implementeren van de toepassing kan de beheerder van de toepassingsserver cookie-voorkeuren opgeven op een serverspecifieke of toepassingsspecifieke basis. Standaard hebben de serverinstellingen de voorkeur.</p> <p>Alle sessiecookies die door uw toepassingsserver worden gegenereerd, moeten het kenmerk <code>HttpOnly</code> bevatten. Als u bijvoorbeeld de JBoss Application Server gebruikt, kunt u het SessionCookie-element wijzigen in <code>httpOnly="true"</code> in het <code>WEB-INF/web.xml</code> -bestand.</p> <p>U kunt het verzenden van cookies beperken met alleen HTTPS. Als gevolg hiervan worden ze niet ongecodeerd via HTTP verzonden. Beheerders van toepassingsservers moeten beveiligde cookies voor de server op algemene basis inschakelen. Als u bijvoorbeeld de JBoss Application Server gebruikt, kunt u het verbindingselement wijzigen in <code>secure=true</code> in het <code>server.xml</code> -bestand.</p> <p>Raadpleeg de documentatie bij de toepassingsserver voor meer informatie over cookie-instellingen.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Bladeren door mappen</p> </td> 
   <td><p>Wanneer iemand om een pagina verzoekt die niet bestaat of om de naam van een directeur verzoekt (het verzoekkoord beëindigt met een voorwaartse schuine streep (/)), zou de toepassingsserver niet de inhoud van die folder moeten terugkeren. Om dit te voorkomen, kunt u bladeren door mappen op uw toepassingsserver uitschakelen. U zou dit voor de toepassing van de beleidsconsole en voor andere toepassingen moeten doen die op uw server lopen.</p> <p>Stel voor JBoss de waarde van de initialisatieparameter voor lijsten van de eigenschap <code>DefaultServlet</code> in op <code>false</code> in het bestand web.xml, zoals in dit voorbeeld:</p> <p>&lt;servlet&gt;</p> <p>&lt;servlet-name&gt;default&lt;/servlet-name&gt;</p> <p>&lt;servlet-class&gt;</p> <p>org.apache.catalina.servlets.DefaultServlet</p> <p>&lt;/servlet-class&gt;</p> <p>&lt;init-param&gt;</p> <p>&lt;param-name&gt;aanbiedingen&lt;/param-name&gt;</p> <p>&lt;param-value&gt;false&lt;/param-value&gt;</p> <p>&lt;/init-param&gt;</p> <p>&lt;load-on-startup&gt;1&lt;/load-on-startup&gt;</p> <p>&lt;/servlet&gt;</p> <p>Stel voor WebSphere de eigenschap <code>directoryBrowsingEnabled</code> in het bestand ibm-web-ext.xmi in op <code>false</code> .</p> <p>Voor WebLogic stelt u de eigenschappen van indexmappen in het bestand weblogic.xml in op <code>false</code>, zoals in dit voorbeeld:</p> <p>&lt;container-descriptor&gt;</p> <p>&lt;index-directory-enabled&gt;false</p> <p>&lt;/index-directory-enabled&gt;</p> <p>&lt;/container-descriptor&gt;</p> </td> 
  </tr> 
 </tbody> 
</table>

### Databasebeveiliging {#database-security}

Wanneer het beveiligen van uw gegevensbestand, zou u de maatregelen moeten uitvoeren die door uw gegevensbestandverkoper worden beschreven. U zou een gegevensbestandgebruiker met de minimaal vereiste gegevensbestandtoestemmingen moeten toewijzen die voor gebruik door AEM Forms op JEE worden verleend. Gebruik bijvoorbeeld geen account met databasebeheerdersrechten.

Bij Oracle heeft de databaseaccount die u gebruikt alleen de bevoegdheden CONNECT, RESOURCE en CREATE VIEW nodig. Voor gelijkaardige vereisten op andere gegevensbestanden, zie [ Voorbereidend om AEM Forms op JEE (Enige Server) te installeren ](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_64).

#### Het vormen geïntegreerde veiligheid voor SQL Server op Vensters voor JBoss {#configuring-integrated-security-for-sql-server-on-windows-for-jboss}

1. Wijzig [ JBOSS_HOME ] \\standalone\configuration\lc_{datasource.xml} om `integratedSecurity=true` aan verbinding URL, zoals aangetoond in dit voorbeeld toe te voegen:

   ```java
    jdbc:sqlserver://<serverhost>:<port>;databaseName=<dbname>;integratedSecurity=true
   ```

1. Voeg het bestand sqljdbc_auth.dll toe aan het Windows-systeempad op de computer waarop de toepassingsserver wordt uitgevoerd. Het bestand sqljdbc_auth.dll bevindt zich bij de installatie van het stuurprogramma voor Microsoft SQL JDBC 6.2.1.0.
1. Wijzig JBoss de dienstbezit van Vensters (JBoss voor AEM Forms op JEE) voor Aanmelden vanaf Lokaal Systeem aan een login rekening die het gegevensbestand van AEM Forms en een minimumreeks voorrechten heeft. Als u JBoss van de bevellijn in plaats van als dienst van Vensters in werking stelt, te hoeven u niet om deze stap uit te voeren.
1. Plaats Veiligheid voor SQL Server van **Gemengde** wijze aan **slechts Authentificatie van Vensters**.

#### Geïntegreerde beveiliging voor SQL Server configureren in Windows voor WebLogic {#configuring-integrated-security-for-sql-server-on-windows-for-weblogic}

1. Start de WebLogic Server Administration Console door de volgende URL te typen in de URL-regel van een webbrowser:

   ```java
   https://[host name]:7001/console
   ```

1. Onder het Centrum van de Verandering, klik **Slot &amp; geef** uit.
1. Onder de Structuur van het Domein, klik *[base_domain]* > **Diensten** > **JDBC** > **Gegevensbronnen** en, in de juiste ruit, klik **IDP_DS**.
1. Op het volgende scherm, op het **lusje van de Configuratie**, klik de **Pool van de Verbinding** tabel en, in de **Eigenschappen** doos, type `integratedSecurity=true`.
1. Onder de Structuur van het Domein, klik **[base_domain]** > **Diensten** > **JDBC** > **Gegevensbronnen** en, in de juiste ruit, klik **RM_DS**.
1. Op het volgende scherm, op het **lusje van de Configuratie**, klik de **Pool van de Verbinding** tabel en, in de **Eigenschappen** doos, type `integratedSecurity=true`.
1. Voeg het bestand sqljdbc_auth.dll toe aan het Windows-systeempad op de computer waarop de toepassingsserver wordt uitgevoerd. Het bestand sqljdbc_auth.dll bevindt zich bij de installatie van het stuurprogramma voor Microsoft SQL JDBC 6.2.1.0.
1. Plaats Veiligheid voor SQL Server van **Gemengde** wijze aan **slechts Authentificatie van Vensters**.

#### Het vormen geïntegreerde veiligheid voor SQL Server op Vensters voor WebSphere {#configuring-integrated-security-for-sql-server-on-windows-for-websphere}

Op WebSphere, kunt u geïntegreerde veiligheid vormen slechts wanneer u een externe SQL bestuurder van de Server JDBC, niet de SQL bestuurder van de Server JDBC gebruikt die met WebSphere wordt ingebed.

1. Meld u aan bij de beheerconsole van WebSphere.
1. In de navigatieboom, klik **Middelen** > **JDBC** > **Gegevensbronnen** en, in de juiste ruit, klik **IDP_DS**.
1. In de juiste ruit, onder Extra Eigenschappen, klik **Eigenschappen van de Douane**, en klik dan **Nieuw**.
1. In het **vakje van de Naam**, type `integratedSecurity` en, in de **doos van de Waarde**, type `true`.
1. In de navigatieboom, klik **Middelen** > **JDBC** > **Gegevensbronnen** en, in de juiste ruit, klik **RM_DS**.
1. In de juiste ruit, onder Extra Eigenschappen, klik **Eigenschappen van de Douane**, en klik dan **Nieuw**.
1. In het **vakje van de Naam**, type `integratedSecurity` en, in de **doos van de Waarde**, type `true`.
1. Voeg op de computer waarop WebSphere is geïnstalleerd het bestand sqljdbc_auth.dll toe aan het systeempad van Windows (C:\Windows). Het sqljdbc_auth.dll- dossier is in de zelfde plaats zoals de de bestuurdersinstallatie van Microsoft SQL JDBC 1.2 (het gebrek is *[InstallDir]*/sqljdbc_1.2/enu/auth/x86).
1. Selecteer **Begin** > **Controlebord** > **Diensten**, klik de dienst van Vensters voor WebSphere (de Server van de Toepassing van IBM WebSphere &lt;version> - &lt;node>) met de rechtermuisknop aan en selecteer **Eigenschappen**.
1. In het de dialoogvakje van Eigenschappen, klik het **Logboek** tabel.
1. Selecteer **Deze Rekening** en verstrek de informatie die wordt vereist om de login rekening te plaatsen u wilt gebruiken.
1. Plaats Veiligheid op SQL Server van **Gemengde** wijze aan **slechts Authentificatie van Vensters**.

### Toegang tot gevoelige inhoud in de database beveiligen {#protecting-access-to-sensitive-content-in-the-database}

Het AEM Forms-databaseschema bevat gevoelige informatie over systeemconfiguratie en bedrijfsprocessen en moet achter de firewall worden verborgen. De database moet worden beschouwd binnen dezelfde vertrouwensgrens als de Forms-server. Om tegen informatieonthulling en diefstal van bedrijfsgegevens te beschermen, moet het gegevensbestand door de gegevensbestandbeheerder (DBA) worden gevormd om toegang slechts door erkende beheerders toe te staan.

Als toegevoegde voorzorg, zou u het gebruiken van gegevensbestand verkoper-specifieke hulpmiddelen moeten overwegen om kolommen in lijsten te coderen die de volgende gegevens bevatten:

* Documenttoetsen Rights Management
* Sleutel voor versleuteling HSM PIN-code opslaan
* Hashes lokaal gebruikerswachtwoord

Voor informatie over verkoper-specifieke hulpmiddelen, zie [ &quot;de veiligheidsinformatie van het Gegevensbestand&quot;](https://helpx.adobe.com/aem-forms/6-1/hardening-security/general-security-considerations.html#database_security_information).

### LDAP-beveiliging {#ldap-security}

Een Lightweight Directory Access Protocol (LDAP)-directory wordt door AEM Forms in JEE doorgaans gebruikt als bron voor zakelijke gebruikers- en groepsgegevens en als middel om wachtwoordverificatie uit te voeren. Zorg ervoor dat uw LDAP-directory is geconfigureerd voor gebruik van SSL (Secure Socket Layer) en dat AEM Forms op JEE is geconfigureerd voor toegang tot uw LDAP-directory via de SSL-poort.

#### LDAP-ontkenning van service {#ldap-denial-of-service}

Een algemene aanval met LDAP heeft tot gevolg dat een aanvaller opzettelijk meerdere keren niet verifieert. Hierdoor wordt de LDAP-directoryserver gedwongen een gebruiker uit alle LDAP-afhankelijke services te weren.

U kunt het aantal mislukkingspogingen en de daaropvolgende sluitingstijd instellen die AEM Forms implementeert wanneer een gebruiker er herhaaldelijk niet in slaagt te verifiëren bij AEM Forms. Kies lage waarden in de beheerconsole. Wanneer het selecteren van het aantal mislukkingspogingen, is het belangrijk om te begrijpen dat nadat alle pogingen worden gemaakt, AEM Forms de gebruiker sluit alvorens de Server van de Folder LDAP doet.

#### Automatische accountvergrendeling instellen {#set-automatic-account-locking}

1. Meld u aan bij de beheerconsole.
1. Klik **Montages** > **Beheer van de Gebruiker** > **Beheer van het Domein**.
1. Onder de Automatische Montages van het Vergrendelen van de Rekening, plaats **Maximum Opeenvolgende Authentificatie ontbreekt** aan een laag aantal, zoals 3.
1. Klik **sparen**.

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

A *omgekeerde volmacht* kan worden gebruikt om ervoor te zorgen dat één reeks URLs voor AEM Forms op het Webtoepassingen van JEE aan zowel externe als interne gebruikers beschikbaar is. Deze configuratie is veiliger dan gebruikers toe te staan om rechtstreeks met de toepassingsserver te verbinden die AEM Forms op JEE loopt. De reverse-proxy voert alle HTTP-aanvragen uit voor de toepassingsserver waarop AEM Forms op JEE wordt uitgevoerd. Gebruikers hebben alleen netwerktoegang tot de reverse-proxy en kunnen alleen proberen URL-verbindingen te maken die door de reverse-proxy worden ondersteund.

**AEM Forms op wortel URLs JEE voor gebruik met omgekeerde volmachtsserver**

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
   <td><p>Workspace-webtoepassing voor eindgebruikers</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
  <tr> 
   <td><p>/workspace-server/*</p> </td> 
   <td><p>Workspace-servlets en gegevensservices die de Workspace-clienttoepassing vereist</p> </td> 
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
   <td><p>Wordt gebruikt voor het ophalen van JavaScript tijdens HTML-transformatie</p> </td> 
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
   <td><p>Workspace-beheerpagina's</p> </td> 
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
   <td><p>Uploaden en downloaden van documenten die moeten worden verwerkt wanneer toegang wordt verkregen tot externe eindpunten, SOAP WSDL-eindpunten en de Java SDK via SOAP transport of EJB-transport met HTTP-documenten ingeschakeld.</p> </td> 
   <td><p>Ja</p> </td> 
   <td><p>Ja</p> </td> 
  </tr> 
 </tbody> 
</table>

## Beveiligen tegen aanvallen met Smederij voor meerdere sites {#protecting-from-cross-site-request-forgery-attacks}

Een CSRF-aanval (Cross-Site Request Svervalsing) misbruikt het vertrouwen dat een website heeft voor de gebruiker, om opdrachten door te geven die niet door de gebruiker zijn geautoriseerd en onbedoeld. De aanval wordt opstelling door een verbinding of een manuscript in een Web-pagina, of een URL in een e-mailbericht te omvatten, om tot een andere plaats toegang te hebben waaraan de gebruiker reeds voor authentiek is verklaard.

U kunt bijvoorbeeld zijn aangemeld bij de beheerconsole terwijl u tegelijkertijd door een andere website bladert. Een van de webpagina&#39;s kan een HTML-afbeeldingstag met een `src` -kenmerk bevatten die een serverscript op de slachtofferwebsite aanwijst. Door het op cookies gebaseerde mechanisme voor sessieverificatie te gebruiken dat door webbrowsers wordt geboden, kan de aanvallende website kwaadaardige verzoeken verzenden naar dit script op de server van het slachtoffer, waarbij de vraag als de legitieme gebruiker wordt gesteld. Voor meer voorbeelden, zie [ https://owasp.org/www-community/attacks/csrf#Examples ](https://owasp.org/www-community/attacks/csrf#Examples).

De volgende kenmerken komen voor in KVP:

* Neem sites op die afhankelijk zijn van de identiteit van een gebruiker.
* Gebruik het vertrouwen van de site in die identiteit.
* Steek de browser van de gebruiker in het verzenden van HTTP-aanvragen naar een doelsite.
* Neem HTTP-aanvragen op die bijwerkingen hebben.

AEM Forms on JEE gebruikt de functie Filter referentie om CSRF-aanvallen te blokkeren. In deze sectie worden de volgende termen gebruikt om het filtermechanisme van de verwijzer te beschrijven:

* **Toegestane Referrer:** A Referrer is het adres van de bronpagina die een verzoek naar de server verzendt. Voor JSP-pagina&#39;s of -formulieren is de referentie meestal de vorige pagina in de browsergeschiedenis. Verwijzers voor afbeeldingen zijn meestal de pagina&#39;s waarop de afbeeldingen worden weergegeven. U kunt de Referrer identificeren die toegang tot uw servermiddelen door hen aan de Toegestane lijst van de Referant wordt verleend toe te voegen.
* **Toegestane Uitzonderingen van de Verwijzer:** u kunt het werkingsgebied van toegang voor een bepaalde Verwijzer in uw Toegestane lijst van de Referant willen beperken. Als u deze beperking wilt toepassen, kunt u afzonderlijke paden van die referentie toevoegen aan de lijst Toegestane uitzonderingen Referrer. Verzoeken die afkomstig zijn van paden in de lijst Toegestane uitzonderingen door verwijzers kunnen geen bron op de Forms-server aanroepen. U kunt de Uitzonderingen van de Verwijzer van de Toestemming voor een specifieke toepassing bepalen en ook een globale lijst van uitzonderingen gebruiken die op alle toepassingen van toepassing zijn.
* **Toegestane URIs:** dit is een lijst van middelen die moeten worden gediend zonder de Kopbal van de Referentie te controleren. De middelen, bijvoorbeeld, hulppagina&#39;s, die niet in staatsveranderingen op de server resulteren, kunnen aan deze lijst worden toegevoegd. De bronnen in de lijst Toegestane URI&#39;s worden nooit geblokkeerd door het filter Referrer, ongeacht wie de Referrer is.
* **Null Referrer:** Een serververzoek dat niet met wordt geassocieerd of niet uit een ouderWeb-pagina voortkomt wordt beschouwd als een verzoek van een Null Referrer. Wanneer u bijvoorbeeld een nieuw browservenster opent, typt u een adres en drukt u op Enter, is de referentie die naar de server is verzonden null. Een Desktoptoepassing (.NET of SWING) die een HTTP- verzoek aan een Webserver indienen, verzendt ook een Null Referrer naar de server.

### Filteren van referentie {#referer-filtering}

Het filterproces Referrer kan als volgt worden beschreven:

1. De Forms-server controleert de HTTP-methode die wordt gebruikt voor oproepen:

   1. Als het POST is, voert de Server van Forms de de kopbalcontrole van de Referteur uit.
   1. Als het GET is, overslaat de Server van Forms de controle van de Referateur, tenzij *CSRF_CHECK_GETS* aan waar wordt geplaatst, in welk geval het de kopbalcontrole van de Referteur uitvoert. *CSRF_CHECK_GETS* wordt gespecificeerd in het *web.xml* dossier voor uw toepassing.

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

AEM Forms on JEE biedt een Referrer Filter om Referrer op te geven die toegang krijgen tot uw serverbronnen. Door gebrek, filtert de filter van de Referentie geen verzoeken die een veilige methode van HTTP, bijvoorbeeld, GET gebruiken, tenzij *CSRF_CHECK_GETS* aan waar wordt geplaatst. Als het havenaantal voor een Toegestane ingang van de Verwijzing aan 0 wordt geplaatst, zal AEM Forms op JEE alle verzoeken met Referrer van die gastheer ongeacht het havenaantal toestaan. Als er geen poortnummer is opgegeven, zijn alleen aanvragen van standaardpoort 80 (HTTP) of poort 443 (HTTPS) toegestaan. Filteren met verwijzing is uitgeschakeld als alle items in de lijst Toegestane verwijzing worden verwijderd.

Wanneer u de Diensten van het Document eerst installeert, wordt de Toegestane lijst van de Verwijzing bijgewerkt met het adres van de server waarop de Diensten van het Document geïnstalleerd is. De ingangen voor de server omvatten de servernaam, het IPv4 adres, het IPv6 adres als IPv6 wordt toegelaten, het loopbackadres, en een localhost ingang. De namen die aan de lijst Toegestane verwijzing worden toegevoegd, worden geretourneerd door het hostbesturingssysteem. Een server met een IP-adres van 10.40.54.187 bevat bijvoorbeeld de volgende vermeldingen: `https://server-name:0, https://10.40.54.187:0, https://127.0.0.1:0, http://localhost:0` . Voor om het even welke niet gekwalificeerde naam die door het werkende systeem van de Gastheer (namen wordt teruggegeven die geen IPv4 adres, IPv6 adres of gekwalificeerde domeinnaam) hebben wordt de lijst van gewenste personen niet bijgewerkt. Wijzig de Toegestane lijst van Referiteers om uw bedrijfsomgeving aan te passen. Implementeer de Forms-server niet in de productieomgeving met de standaardlijst Toegestane verwijzing. Nadat u een van de toegestane referentie-, referentie-uitzonderingen of URI&#39;s hebt gewijzigd, zorgt u ervoor dat de server opnieuw wordt gestart zodat de wijzigingen van kracht worden.

**het Leiden Toegestane lijst van de Verwijzing**

U kunt de lijst Toegestane verwijzing beheren via de gebruikersbeheerinterface van de beheerconsole. De gebruikersbeheerinterface biedt u de functionaliteit om de lijst te maken, bewerken of verwijderen. Verwijs naar * [ het verhinderen van aanvallen CSRF ](/help/forms/using/admin-help/preventing-csrf-attacks.md)* sectie van de *beleidshulp* voor meer informatie bij het werken met de Toegestane lijst van de Referentie.

**het Leiden Toegestane Uitzondering van de Referentie en Toegestane lijsten URI**

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

Gebruik ***LC_GLOBAL_ALLOWED_REFERER_EXCEPTION*** lijst voor de Uitzonderingen van de Verwijzer op het globale niveau dat is, om uitzonderingen te bepalen die op alle toepassingen van toepassing zijn. Deze lijst bevat alleen URI&#39;s met een absoluut pad (bijvoorbeeld `/index.html` ) of een relatief pad (bijvoorbeeld `/sample/` ). U kunt ook een reguliere expressie toevoegen aan het einde van een relatieve URI, bijvoorbeeld `/sample/(.)*` .

***LC_GLOBAL_ALLOWED_REFERER_EXCEPTION*** lijst ID wordt bepaald als constante in de `UMConstants` klasse van `com.adobe.idp.um.api` namespace, die in `adobe-usermanager-client.jar` wordt gevonden. Met de AEM Forms API&#39;s kunt u deze lijst maken, wijzigen of bewerken. Als u bijvoorbeeld de lijst Uitzonderingen globale toegestane verwijzingsverwijzing wilt maken, gebruikt u:

```java
addAllowedRefererExceptions(UMConstants.LC_GLOBAL_ALLOWED_REFERER_EXCEPTION, Arrays.asList("/index.html", "/sample/(.)*"))
```

Gebruik ***CSRF_ALLOWED_REFERER_EXCEPTIONS*** lijst voor toepassing-specifieke uitzonderingen.

**onbruikbaar makend de Filter van de Verwijzing**

Als het filter Referrer de toegang tot de Forms-server volledig blokkeert en u de lijst Toegestane verwijzing niet kunt bewerken, kunt u het opstartscript van de server bijwerken en het filteren van referenties uitschakelen.

Neem het argument `-Dlc.um.csrffilter.disabled=true` JAVA op in het opstartscript en start de server opnieuw. Zorg ervoor dat u het argument JAVA schrapt nadat u correct de Toegestane lijst van de Verwijzing hebt aangepast.

**het Filtreren van de Referateur voor de dossiers van de OORLOG van de Douane**

Mogelijk hebt u aangepaste WAR-bestanden gemaakt die u met AEM Forms op JEE kunt gebruiken om aan uw zakelijke vereisten te voldoen. Om het Filtreren van de Referateur voor uw dossiers van douaneWAR toe te laten, omvat ***adobe-usermanager-client.jar*** in de klassenweg voor WAR en omvat een filteringang in het* web.xml* dossier met de volgende parameters:

**CSRF_CHECK_GETS** controleert de controle van de Referateur op verzoeken van GET. Wanneer deze parameter niet is gedefinieerd, wordt de standaardwaarde op false ingesteld. Neem deze parameter alleen op als u uw GET-aanvragen wilt filteren.

**CSRF_ALLOWED_REFERER_EXCEPTIONS** is identiteitskaart van de Toegestane lijst van de Uitzonderingen van de Referentie. Het filter Referrer verhindert verzoeken afkomstig van Verwijzers in de lijst die door lijstidentiteitskaart wordt geïdentificeerd, om het even welke middelen op de Server van Forms te roepen.

**CSRF_ALLOWED_URIS_LIST_NAME** is identiteitskaart van de Toegestane lijst URIs. Het filter Referrer blokkeert geen aanvragen voor een van de bronnen in de lijst die door de lijst-id wordt geïdentificeerd, ongeacht de waarde van de verwijzaarheader in de aanvraag.

**CSRF_ALLOW_NULL_REFERER** controleert het gedrag van de Filter van de Referteur wanneer de Referteur ongeldig of niet aanwezig is. Wanneer deze parameter niet is gedefinieerd, wordt de standaardwaarde op false ingesteld. Neem deze parameter alleen op als u Null-referenties wilt toestaan. Het toestaan van ongeldige verwijzers kan sommige types van het Verzoek van de Vervalsing van de Plaats van de Overeenkomst toestaan.

**CSRF_NULL_REFERER_EXCEPTIONS** is een lijst van URIs waarvoor een controle van de Referteur niet wordt uitgevoerd wanneer de Referrer ongeldig is. Deze parameter wordt toegelaten slechts wanneer *CSRF_ALLOW_NULL_REFERER* aan vals wordt geplaatst. Scheid meerdere URI&#39;s in de lijst met een komma.

Na is een voorbeeld van de filteringang in het *web.xml* dossier voor a ***SAMPLE*** dossier van WAR:

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
     <li><p>Alle SOAP</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>SOAP</p> </td> 
   <td> 
    <ul> 
     <li><p>De de dienstcliënttoepassingen van het Web, zoals .NET toepassingen</p> </li> 
     <li><p>Adobe Reader® gebruikt SOAP voor AEM Forms op JEE server webservices</p> </li> 
     <li><p>Adobe Flash®-toepassingen gebruiken SOAP voor Forms Server-webservices</p> </li> 
     <li><p>AEM Forms op JEE SDK-aanroepen bij gebruik in SOAP modus</p> </li> 
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

**JBoss havens**

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

**havens WebLogic**

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

**havens WebSphere**

Voor informatie over havens WebSphere die AEM Forms op JEE vereist, ga naar het aantal dat van de Haven in WebSphere de Server UI van de Toepassing plaatst.

### SSL configureren {#configuring-ssl}

Verwijzend naar de fysieke architectuur die in de sectie [ AEM Forms op fysieke architectuur JEE ](hardening-aem-forms-jee-environment.md#aem-forms-on-jee-physical-architecture) wordt beschreven, zou u SSL voor alle verbindingen moeten vormen die u van plan bent te gebruiken. Met name moeten alle SOAP verbindingen via SSL worden uitgevoerd om blootstelling van gebruikersgeloofsbrieven op een netwerk te verhinderen.

Voor instructies op hoe te om SSL op JBoss, WebLogic, en WebSphere te vormen, zie &quot;het Vormen SSL&quot;in de [ beleidshulp ](https://www.adobe.com/go/learn_aemforms_admin_64).

Voor instructies op hoe te om certificaten in JVM (de Virtuele Machine van Java) in te voeren die voor een server van AEM Forms worden gevormd, zie de Wederzijdse sectie van de Authentificatie in [ de Hulp van de Werkbench van AEM Forms ](https://www.adobe.com/go/learn_aemforms_workbench_65).

### SSL-omleiding configureren {#configuring-ssl-redirect}

Nadat u uw toepassingsserver vormt om SSL te steunen, moet u ervoor zorgen dat al verkeer van HTTP aan toepassingen en de diensten wordt afgedwongen om de SSL haven te gebruiken.

Raadpleeg de documentatie bij de toepassingsserver voor informatie over SSL-omleiding voor WebSphere of WebLogic.

1. Open bevelherinnering, navigeer aan /JBOSS_HOME/standalone/configuratiemap, en voer het volgende bevel uit:

   `keytool -genkey -alias jboss7 -keyalg RSA -keystore server.keystore -validity 10950`

1. Open het bestand JBOSS_HOME/standalone/configuration/standalone.xml voor bewerking.

   Na &lt;subsystem xmlns= &quot;urn :jboss: domein :web: 1.1&quot; native= &quot;vals&quot; gebrek-virtueel-server= &quot;gebrek-gastheer&quot;> element, voeg de volgende details toe:

   &lt;naam van connector=&quot;https&quot; protocol=&quot;HTTP/1.1&quot; scheme=&quot;https&quot; socket-binding=&quot;https&quot; enabled=&quot;true&quot; secure=&quot;true&quot;/>

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

   * Selecteer **Gebruiker kan geen wachtwoord** veranderen.
   * Voor het **Lid van** lusje, zorg ervoor dat de gebruikersgroep vermeld is.

1. Selecteer **Montages** > **Administratieve Hulpmiddelen** > **de Diensten**.
1. Dubbelklik op de service van de toepassingsserver en stop de service.
1. Op het **Logboek** lusje, selecteer **Deze Rekening**, doorblader voor de gebruikersrekening u creeerde, en ga het wachtwoord voor de rekening in.
1. Geef in het venster Lokale beveiligingsinstellingen onder Toewijzing gebruikersrechten de volgende rechten op de gebruikersaccount waarop de Forms-server wordt uitgevoerd:

   * Ontken login door de EindDiensten
   * Aanmelding lokaal weigeren
   * Aanmelden als service (moet al zijn ingesteld)

1. Wijzig de machtigingen voor de nieuwe gebruikersaccount voor de volgende directory&#39;s:
   * **Globale folder van de Opslag van het Document (GDS)**: De plaats van de GDS folder wordt gevormd manueel tijdens het installatieproces van AEM Forms. Als de locatie-instelling tijdens de installatie leeg blijft, wordt standaard een map onder de installatie van de toepassingsserver op `[JBoss root]/server/[type]/svcnative/DocumentStorage` weergegeven
   * **CRX-Repository folder**: De standaardplaats is `[AEM-Forms-installation-location]\crx-repository`
   * **tijdelijke folders van AEM Forms**:
      * (Windows) TMP- of TEMP-pad zoals ingesteld in de omgevingsvariabelen
      * (AIX, Linux, of Solaris) Logged-in de huisfolder van de gebruiker
Op UNIX-gebaseerde systemen, kan een niet-wortelgebruiker de volgende folder als tijdelijke folder gebruiken:
      * (Linux) /var/tmp of /usr/tmp
      * (AIX) /tmp of /usr/tmp
      * (Solaris) /var/tmp of /usr/tmp
1. Geef de nieuwe gebruikersaccount schrijfmachtigingen voor de volgende directory&#39;s:
   * [ JBoss-folder ] \ standalone \ plaatsing
   * [ JBoss-folder ] \ standalone\
   * [ JBoss-folder ] \ bak \

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

Stel de eigenschappen van de indexmappen in het bestand weblogic.xml in op `false` , zoals in dit voorbeeld:

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

Stel de eigenschap `directoryBrowsingEnabled` in het bestand ibm-web-ext.xml in op `false` .

### Beveiliging WebSphere inschakelen {#enable-websphere-administrative-security}

1. Meld u aan bij de beheerconsole van WebSphere.
1. In de navigatieboom, ga naar **Veiligheid** > **Globale Veiligheid**
1. Selecteer **administratieve veiligheid** toelaten.
1. Deselecteer zowel **toepassingsveiligheid** toelaten en **Java 2 veiligheid van het Gebruik**.
1. Klik **O.K.** of **toepassen**.
1. In het **vakje van Berichten**, klik **direct sparen aan de hoofdconfiguratie**.
