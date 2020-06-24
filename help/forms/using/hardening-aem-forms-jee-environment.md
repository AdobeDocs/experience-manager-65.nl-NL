---
title: Verharding van uw AEM Forms op JEE-omgeving
seo-title: Verharding van uw AEM Forms op JEE-omgeving
description: Leer een verscheidenheid van veiligheid-verhardende montages om de veiligheid van AEM Forms op JEE te verbeteren die in een collectieve Intranet lopen.
seo-description: Leer een verscheidenheid van veiligheid-verhardende montages om de veiligheid van AEM Forms op JEE te verbeteren die in een collectieve Intranet lopen.
uuid: f6c63690-6376-4fe1-9df2-a14fbfd62aff
content-type: reference
topic-tags: Security
products: SG_EXPERIENCEMANAGER/6.4
discoiquuid: 6b380e92-f90d-4875-b7a2-f3958daf2364
translation-type: tm+mt
source-git-commit: 6cb05cab9ecbb9fc88e16cc1ab24cafccf7d0b16
workflow-type: tm+mt
source-wordcount: '7603'
ht-degree: 0%

---


# Verharding van uw AEM Forms op JEE-omgeving {#hardening-your-aem-forms-on-jee-environment}

Leer een verscheidenheid van veiligheid-verhardende montages om de veiligheid van AEM Forms op JEE te verbeteren die in een collectieve Intranet lopen.

Het artikel beschrijft aanbevelingen en beste praktijken voor het beveiligen van servers die AEM Forms op JEE in werking stellen. Dit is geen uitgebreid host-hardend document voor uw besturingssysteem en toepassingsservers. In plaats daarvan, beschrijft dit artikel een verscheidenheid van veiligheid-verhardende montages die u zou moeten uitvoeren om de veiligheid van AEM Forms op JEE te verbeteren die binnen een collectief Intranet loopt. Om ervoor te zorgen dat de AEM Forms op JEE toepassingsservers veilig blijven, echter, zou u veiligheid controle, opsporing, en reactieprocedures ook moeten uitvoeren.

In het artikel worden verhardingstechnieken beschreven die tijdens de levenscyclus van de installatie en configuratie in de volgende fasen moeten worden toegepast:

* **Voorinstallatie:** Gebruik deze technieken voordat u AEM Forms op JEE installeert.
* **Installatie:** Gebruik deze technieken tijdens de AEM Forms bij het JEE-installatieproces.
* **Na de installatie:** Gebruik deze technieken na installatie en periodiek daarna.

AEM Forms op JEE zijn zeer aanpasbaar en kunnen in veel verschillende omgevingen werken. Sommige aanbevelingen passen mogelijk niet in de behoeften van uw organisatie.

## Voorinstallatie {#preinstallation}

Voordat u AEM Forms op JEE installeert, kunt u beveiligingsoplossingen toepassen op de netwerklaag en het besturingssysteem. In deze sectie worden enkele problemen beschreven en worden aanbevelingen gedaan om beveiligingsrisico&#39;s op deze gebieden te verminderen.

**Installatie en configuratie op UNIX en Linux**

U zou geen AEM Forms op JEE moeten installeren of vormen gebruikend wortelshell. Standaard worden bestanden geïnstalleerd onder de map /opt en heeft de gebruiker die de installatie uitvoert, alle bestandsmachtigingen onder /opt nodig. Een installatie kan ook worden uitgevoerd in de map /user van een individuele gebruiker, waar deze al over alle bestandsmachtigingen beschikt.

**Installatie en configuratie in Windows**

U moet de installatie in Windows als beheerder uitvoeren als u AEM Forms op JEE op JBoss installeert met de methode key turnkey of als u PDF Generator installeert. Wanneer u PDF Generator in Windows installeert met ondersteuning voor native toepassingen, moet u de installatie uitvoeren als dezelfde Windows-gebruiker die Microsoft Office heeft geïnstalleerd. Zie het document* AEM Forms installeren en implementeren in JEE* voor meer informatie over installatiemacht.

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
   <td><p>Stel vormenservers binnen een gedemilitariseerde streek (DMZ) op. De segmentatie zou in minstens twee niveaus met de toepassingsserver moeten bestaan die wordt gebruikt om AEM Forms op JEE in werking te stellen die achter de binnenfirewall wordt geplaatst. Scheid het externe netwerk van DMZ die de Webservers bevat, die beurtelings van het interne netwerk moeten worden gescheiden. Gebruik firewalls om de scheidingslagen te implementeren. Categoriseer en controleer het verkeer dat door elke netwerklaag overgaat om ervoor te zorgen dat slechts het absolute minimum van vereiste gegevens wordt toegestaan.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Persoonlijke IP-adressen</p> </td> 
   <td><p>De Vertaling van het Adres van het Netwerk van het gebruik (NATIONAAL) met privé IP adressen RFC 1918 op de toepassingsserver van AEM Forms. Wijs privé IP adressen (10.0.0.0/8, 172.16.0.0/12, en 192.168.0.0/16) toe om het voor een aanvaller moeilijker te maken om verkeer aan en van een NATIONAAL interne gastheer door Internet te leiden.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Vuurmuren</p> </td> 
   <td><p>Gebruik de volgende criteria om een firewalloplossing te selecteren:</p> 
    <ul> 
     <li><p>Voer firewalls uit die volmachtsservers en/of <em>stateful inspectie</em> in plaats van eenvoudige pakket-filtrerende oplossingen steunen.</p> </li> 
     <li><p>Gebruik een firewall die steunt <em>ontkent alle diensten behalve die uitdrukkelijk toegelaten</em> veiligheidsparadigma's.</p> </li> 
     <li><p>Voer een firewalloplossing uit die dubbel-homed of multihomed is. Deze architectuur biedt het grootste beveiligingsniveau en helpt te voorkomen dat onbevoegde gebruikers de firewallbeveiliging omzeilen.</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>Databasepoorten</p> </td> 
   <td><p>Gebruik geen standaard luisterpoorten voor databases (MySQL - 3306, Oracle - 1521, MS SQL - 1433). Raadpleeg de documentatie bij uw database voor informatie over het wijzigen van databasepoorten.</p> <p>Het gebruiken van een verschillende gegevensbestandhaven beïnvloedt de algemene AEM Forms op configuratie JEE. Als u standaardhavens verandert, moet u overeenkomstige wijzigingen in andere gebieden van configuratie, zoals de gegevensbronnen voor AEM Forms op JEE maken.</p> <p>Voor informatie over het vormen van gegevensbronnen in AEM Forms op JEE, zie installeren en bevorderen AEM Forms op JEE of Bevorderen aan AEM Forms op JEE voor uw toepassingsserver bij de gebruikershandleiding <a href="/help/forms/using/introduction-aem-forms.md" target="_blank">van</a>AEM Forms.</p> </td> 
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

Zie [&quot;Beveiligingsgegevens van besturingssysteem&quot;](https://helpx.adobe.com/aem-forms/6-1/hardening-security/general-security-considerations.html#operating_system_security_information)voor aanvullende beveiligingsinformatie voor uw besturingssysteem.

## Installatie {#installation}

In deze sectie worden technieken beschreven die u tijdens het installatieproces van AEM Forms kunt gebruiken om beveiligingsrisico&#39;s te beperken. In sommige gevallen maken deze technieken gebruik van opties die deel uitmaken van het installatieproces. In de volgende tabel worden deze technieken beschreven.

<table> 
 <thead> 
  <tr> 
   <th><p>Probleem</p> </th> 
   <th><p>Beschrijving</p> </th> 
  </tr> 
 </thead> 
 <tbody>
  <tr> 
   <td><p>Bevoegdheden</p> </td> 
   <td><p>Gebruik het minste aantal rechten dat nodig is om de software te installeren. Meld u aan bij uw computer met een account die zich niet in de groep Beheerders bevindt. In Windows kunt u de opdracht Als uitvoeren gebruiken om de AEM Forms als een beheergebruiker uit te voeren in het JEE-installatieprogramma. Gebruik op UNIX- en Linux-systemen een opdracht, bijvoorbeeld <code>sudo</code> om de software te installeren.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Softwarebron</p> </td> 
   <td><p>Download of voer geen AEM Forms uit op JEE van niet-vertrouwde bronnen.</p> <p>De kwaadwillige programma's kunnen code bevatten om veiligheid op verscheidene manieren, met inbegrip van gegevensdiefstal, wijziging en schrapping, en ontkenning van de dienst te schenden. Installeer AEM Forms op JEE vanaf de Adobe-dvd of alleen vanaf een vertrouwde bron.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Schijfpartities</p> </td> 
   <td><p>Plaats AEM Forms op JEE op een toegewezen schijfpartitie. De segmentatie van de schijf is een proces dat specifieke gegevens op uw server op afzonderlijke fysieke schijven voor extra veiligheid houdt. Het schikken van gegevens op deze manier vermindert het risico van folderaanvallen. Maak een partitie die los staat van de systeempartitie waarop u de AEM Forms in de map JEE-inhoud kunt installeren. (In Windows bevat de systeempartitie de directory system32 of de opstartpartitie.)</p> </td> 
  </tr> 
  <tr> 
   <td><p>Onderdelen</p> </td> 
   <td><p>Evalueer de bestaande diensten en maak of desinstalleer om het even welke onbruikbaar die niet worden vereist. Installeer geen overbodige onderdelen en services.</p> <p>De standaardinstallatie van een toepassingsserver zou de diensten kunnen omvatten die niet noodzakelijk voor uw gebruik zijn. U zou alle onnodige diensten voorafgaand aan plaatsing moeten onbruikbaar maken om punten van ingang voor een aanval te minimaliseren. Op JBoss kunt u bijvoorbeeld opmerkingen plaatsen over overbodige services in het beschrijvingsbestand META-INF/jboss-service.xml.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Interdomeinbeleidsbestand</p> </td> 
   <td><p>De aanwezigheid van een <code>crossdomain.xml</code> bestand op de server kan de server onmiddellijk verzwakken. U wordt aangeraden de lijst met domeinen zo restrictief mogelijk te maken. Plaats het <code>crossdomain.xml</code> bestand dat tijdens de ontwikkeling is gebruikt, niet in productie wanneer u hulplijnen gebruikt <em>(afgekeurd)</em>. Voor een gids die de Webdiensten gebruikt, als de dienst op de zelfde server is die de gids opdiende, is een <code>crossdomain.xml</code> dossier helemaal niet nodig. Maar als de dienst op een andere server is, of als de clusters betrokken zijn, zou de aanwezigheid van een <code>crossdomain.xml</code> dossier nodig zijn. Raadpleeg <a href="https://kb2.adobe.com/cps/142/tn_14213.html">https://kb2.adobe.com/cps/142/tn_14213.html</a>voor meer informatie over het bestand crossdomain.xml.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Beveiligingsinstellingen van besturingssysteem</p> </td> 
   <td><p>Als u 192-bits of 256-bits XML-codering op Solaris-platforms moet gebruiken, moet u de installatie <code>pkcs11_softtoken_extra.so</code> in plaats van <code>pkcs11_softtoken.so</code>.</p> </td> 
  </tr> 
 </tbody> 
</table>

## Stappen na de installatie {#post-installation-steps}

Nadat u met succes AEM Forms op JEE installeert, is het belangrijk om het milieu uit veiligheidsperspectief periodiek te handhaven.

In de volgende sectie worden de verschillende taken beschreven die worden aanbevolen om de geïmplementeerde formulierserver te beveiligen.

### Beveiliging AEM Forms {#aem-forms-security}

De volgende aanbevolen instellingen zijn van toepassing op de AEM Forms op de JEE-server buiten de beheerwebtoepassing. Als u de beveiligingsrisico&#39;s voor de server wilt beperken, past u deze instellingen direct toe nadat u AEM Forms op JEE hebt geïnstalleerd.

**Beveiligingspatches**

Er is een verhoogd risico dat een onbevoegde gebruiker toegang tot de toepassingsserver zou kunnen krijgen als de patches en upgrades van de verkopersveiligheid niet tijdig worden toegepast. Test beveiligingspatches voordat u ze op productieservers toepast om de compatibiliteit en beschikbaarheid van toepassingen te garanderen. Ook kunt u beleidsregels en procedures maken om regelmatig te controleren op patches en deze te installeren. AEM Forms over JEE-updates vindt u op de downloadsite voor Enterprise-producten.

**Servicerekeningen (alleen voor JBoss-sleutel in Windows)**

AEM Forms op JEE installeert de dienst, door gebrek, door de rekening te gebruiken LocalSystem. De ingebouwde LocalSystem-gebruikersaccount heeft een hoog toegankelijkheidsniveau; het maakt deel uit van de groep Beheerders. Als een worker-process-identiteit wordt uitgevoerd als LocalSystem-gebruikersaccount, heeft dat arbeidersproces volledige toegang tot het gehele systeem.

Als u de toepassingsserver wilt uitvoeren waarop AEM Forms op JEE worden geïmplementeerd, gebruikt u een specifieke niet-beheeraccount, volgt u deze instructies:

1. In de Console van het Beheer van Microsoft (MMC), creeer een lokale gebruiker voor de dienst van de vormenserver om login als:

   * Selecteer **Gebruiker kan wachtwoord** niet wijzigen.
   * Controleer op het **tabblad Lid van** of de groep **Gebruikers** wordt weergegeven.
   >[!NOTE]
   >
   >U kunt deze instelling niet wijzigen voor PDF Generator.

1. Selecteer **Start** > **Instellingen** > **Systeembeheer** > **Services**.
1. Dubbelklik op JBoss voor AEM Forms op JEE en stop de service.
1. Selecteer op het tabblad **Aanmelden** de optie **Deze account**, blader naar de gebruikersaccount die u hebt gemaakt en voer het wachtwoord voor de account in.
1. Open in de MMC de optie **Lokale beveiligingsinstellingen** en selecteer **Lokaal beleid** > Toewijzing **gebruikersrechten**.
1. Wijs de volgende rechten toe aan de gebruikersaccount waarop de formulierserver wordt uitgevoerd:

   * Ontken login door de EindDiensten
   * Aanmelden lokaal weigeren
   * Aanmelden als service (moet al zijn ingesteld)

1. Wijzig de machtigingen voor de nieuwe gebruikersaccount voor de volgende directory&#39;s:
   * **GDS-map**(Global Document Storage): De locatie van de GDS-map wordt handmatig geconfigureerd tijdens het installatieproces van AEM Forms. Als de locatie-instelling tijdens de installatie leeg blijft, wordt de locatie standaard ingesteld op een directory onder de installatie van de toepassingsserver op `[JBoss root]/server/[type]/svcnative/DocumentStorage`
   * **CRX-Repository directory**: De standaardlocatie is `[AEM-Forms-installation-location]\crx-repository`
   * **Tijdelijke mappen** voor AEM Forms:
      * (Windows) TMP- of TEMP-pad zoals ingesteld in de omgevingsvariabelen
      * (AIX, Linux, of Solaris) Logged-in de huisfolder van de gebruiker Op op UNIX-Gebaseerde systemen, kan een niet wortelgebruiker de volgende folder als tijdelijke folder gebruiken:
      * (Linux) /var/tmp of /usr/tmp
      * (AIX) /tmp of /usr/tmp
      * (Solaris) /var/tmp of /usr/tmp
1. Geef de nieuwe gebruikersaccount schrijfmachtigingen voor de volgende directory&#39;s:
   * [JBoss-directory]\standalone\deployment
   * [JBoss-directory]\standalone\
   * [JBoss-directory]\bin\
   >[!NOTE]
   >
   > De standaardinstallatielocatie van JBoss Application Server:
   > * Windows: C:\Adobe\Adobe_Experience_Manager_Forms\jboss
   > * Linux: /opt/jreliëf/

1. Start de toepassingsserver.

**Het onbruikbaar maken van de reservereserlet van de Manager van de Configuratie**

De Manager van de configuratie maakte gebruik van servlet die op uw toepassingsserver wordt opgesteld om bootstrapping van de AEM Forms op gegevensbestand uit te voeren JEE. Omdat de Manager van de Configuratie tot dit servlet toegang heeft alvorens de configuratie volledig is, is de toegang tot het niet beveiligd voor erkende gebruikers, en het zou moeten worden onbruikbaar gemaakt nadat u met succes de Manager van de Configuratie hebt gebruikt om AEM Forms op JEE te vormen.

1. Pak het bestand adobe-livecycle-[appserver].ear uit.
1. Open het bestand META-INF/application.xml.
1. Zoek naar de adobe-bootstrapper.war sectie:

   ```as3
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

1. Stop de server van AEM Forms.
1. Maak een commentaarregel van adobe-bootstrapper.war en de adobe-lcm-bootstrapper-redirectory. oorlogsmodules, als hieronder:

   ```as3
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

Met Configuration Manager kunt u een Acrobat Reader DC-extensie uploaden die als referentie dient voor de AEM Forms in de JEE-vertrouwde opslag. Dit betekent dat de toegang tot de Dienst van de Referentie van de Opslag van het Vertrouwen over verre protocollen (ZEEP en EJB) door gebrek is toegelaten. Deze toegang is niet meer noodzakelijk nadat u de credentie van Rechten gebruikend de Manager van de Configuratie hebt geupload of als u besluit om de Console van het Beleid later te gebruiken om geloofsbrieven te beheren.

U kunt verre toegang tot alle diensten van de Opslag van het Vertrouwen onbruikbaar maken door de stappen in de sectie te volgen [onbruikbaar makend niet essentiële verre toegang tot de diensten](https://helpx.adobe.com/aem-forms/6-1/hardening-security/configuring-secure-administration-settings-aem.html#disabling_non_essential_remote_access_to_services).

**Alle niet-essentiële anonieme toegang uitschakelen**

Sommige diensten van de vormenserver hebben verrichtingen die door een anonieme bezoeker kunnen worden aangehaald. Als de anonieme toegang tot deze diensten niet wordt vereist, maak het onbruikbaar door de stappen in het [onbruikbaar maken van niet essentiële anonieme toegang tot de diensten](https://helpx.adobe.com/aem-forms/6-1/hardening-security/configuring-secure-administration-settings-aem.html#disabling_non_essential_anonymous_access_to_services)te volgen.

#### Het standaardbeheerderswachtwoord wijzigen {#change-the-default-administrator-password}

Wanneer AEM Forms op JEE worden geïnstalleerd, wordt één enkel standaardgebruikersrekening gevormd voor gebruiker Super Beheerder/login-id Beheerder met een standaardwachtwoord van *wachtwoord*. U zou dit wachtwoord onmiddellijk moeten veranderen gebruikend de Manager van de Configuratie.

1. Typ de volgende URL in een webbrowser:

   ```as3
   https://[host name]:[port]/adminui
   ```

   Het standaardpoortnummer is een van de volgende:

   **JBoss:** 8080

   **WebLogic-server:** 7001

   **WebSphere:** 9080.

1. Typ in het veld **Gebruikersnaam** `administrator` en typ in het veld **Wachtwoord** `password`.
1. Klik op **Instellingen** > **Gebruikersbeheer** > **Gebruikers en groepen**.
1. Typ `administrator` in het veld **Zoeken** en klik op **Zoeken**.
1. Klik op **Super Administrator** in de lijst met gebruikers.
1. Klik op Wachtwoord **** wijzigen op de pagina Gebruiker bewerken.
1. Geef het nieuwe wachtwoord op en klik op **Opslaan**.

Daarnaast wordt aangeraden het standaardwachtwoord voor CRX Administrator te wijzigen door de volgende stappen uit te voeren:

1. Meld u aan `https://[server]:[port]/lc/libs/granite/security/content/useradmin.html` met de standaardgebruikersnaam/het standaardwachtwoord.
1. Typ Beheerder in het zoekveld en klik op **Ga**.
1. Selecteer **Beheerder** in het zoekresultaat en klik op het pictogram **Bewerken** rechtsonder in de gebruikersinterface.
1. Geef het nieuwe wachtwoord op in het veld **Nieuw wachtwoord** en het oude wachtwoord in het veld **Uw wachtwoord** .
1. Klik op het pictogram Opslaan rechtsonder in de gebruikersinterface.

#### WSDL-generatie uitschakelen {#disable-wsdl-generation}

De generatie van de Definitie van de Taal van de Dienst van het Web (WSDL) zou slechts voor ontwikkelomgevingen moeten worden toegelaten, waar de generatie WSDL door ontwikkelaars wordt gebruikt om hun cliënttoepassingen te bouwen. U kunt verkiezen om de generatie van WSDL in een productiemilieu onbruikbaar te maken vermijden blootstellend de interne details van de dienst.

1. Typ de volgende URL in een webbrowser:

   ```as3
   https://[host name]:[port]/adminui
   ```

1. Klik op **Instellingen > Core System Settings > Configurations**.
1. Schakel **WSDL** inschakelen uit en klik op **OK**.

### Beveiliging toepassingsserver {#application-server-security}

In de volgende tabel worden enkele technieken beschreven waarmee u uw toepassingsserver kunt beveiligen nadat de AEM Forms in de JEE-toepassing zijn geïnstalleerd.

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
   <td><p>Nadat u, AEM Forms op JEE op uw toepassingsserver installeert vormt en opstelt, zou u toegang tot de administratieve consoles van de toepassingsserver moeten onbruikbaar maken. Raadpleeg de documentatie bij de toepassingsserver voor meer informatie.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Cookinstellingen toepassingsserver</p> </td> 
   <td><p>Toepassingscookies worden beheerd door de toepassingsserver. Bij het implementeren van de toepassing kan de beheerder van de toepassingsserver cookie-voorkeuren opgeven op een serverspecifieke of toepassingsspecifieke basis. Standaard hebben de serverinstellingen de voorkeur.</p> <p>Alle sessiecookies die door uw toepassingsserver worden gegenereerd, moeten het <code>HttpOnly</code> kenmerk bevatten. Bijvoorbeeld, wanneer het gebruiken van de Server van de Toepassing JBoss, kunt u het element SessionCookie aan <code>httpOnly="true"</code> in het <code>WEB-INF/web.xml</code> dossier wijzigen.</p> <p>U kunt het verzenden van cookies beperken met alleen HTTPS. Als gevolg hiervan worden ze niet ongecodeerd via HTTP verzonden. Toepassingsserverbeheerders moeten beveiligde cookies voor de server op algemene basis inschakelen. Bijvoorbeeld, wanneer het gebruiken van de Server van de Toepassing JBoss, kunt u het schakelaarelement wijzigen aan <code>secure=true</code> in het <code>server.xml</code> dossier.</p> <p>Raadpleeg de documentatie bij de toepassingsserver voor meer informatie over cookie-instellingen.</p> </td> 
  </tr> 
  <tr> 
   <td><p>Bladeren door mappen</p> </td> 
   <td><p>Wanneer iemand om een pagina verzoekt die niet bestaat of om de naam van een directeur verzoekt (het verzoekkoord beëindigt met een voorwaartse schuine streep (/)), zou de toepassingsserver niet de inhoud van die folder moeten terugkeren. Om dit te voorkomen, kunt u bladeren door mappen op uw toepassingsserver uitschakelen. U zou dit voor de toepassing van de beleidsconsole en voor andere toepassingen moeten doen die op uw server lopen.</p> <p>Voor JBoss, plaats de waarde van de parameter van de lijstinitialisatie van het <code>DefaultServlet</code> bezit aan <code>false</code> in het web.xml- dossier, zoals aangetoond in dit voorbeeld:</p> <p>&lt;servlet&gt;</p> <p>&lt;servlet-name&gt;default&lt;/servlet-name&gt;</p> <p>&lt;servlet-class&gt;</p> <p>org.apache.catalina.servlets.DefaultServlet</p> <p>&lt;/servlet-class&gt;</p> <p>&lt;init-param&gt;</p> <p>&lt;param-name&gt;aanbiedingen&lt;/param-name&gt;</p> <p>&lt;param-value&gt;false&lt;/param-value&gt;</p> <p>&lt;/init-param&gt;</p> <p>&lt;load-on-startup&gt;1&lt;/load-on-startup&gt;</p> <p>&lt;/servlet&gt;</p> <p>Stel voor WebSphere de <code>directoryBrowsingEnabled</code> eigenschap in het bestand ibm-web-ext.xmi in op <code>false</code>.</p> <p>Voor WebLogic stelt u de eigenschappen van de indexmappen in het bestand weblogic.xml in op <code>false</code>, zoals in dit voorbeeld:</p> <p>&lt;container-descriptor&gt;</p> <p>&lt;index-directory-enabled&gt;false</p> <p>&lt;/index-directory-enabled&gt;</p> <p>&lt;/container-descriptor&gt;</p> </td> 
  </tr> 
 </tbody> 
</table>

### Databasebeveiliging {#database-security}

Wanneer het beveiligen van uw gegevensbestand, zou u de maatregelen moeten uitvoeren die door uw gegevensbestandverkoper worden beschreven. U zou een gegevensbestandgebruiker met de minimaal vereiste gegevensbestandtoestemmingen moeten toewijzen die voor gebruik door AEM Forms op JEE worden verleend. Gebruik bijvoorbeeld geen account met databasebeheerdersrechten.

Bij Oracle heeft de databaseaccount die u gebruikt alleen de bevoegdheden CONNECT, RESOURCE en CREATE VIEW nodig. Voor gelijkaardige vereisten op andere gegevensbestanden, zie het [Voorbereiden om AEM Forms op JEE (Enige Server)](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_64)te installeren.

#### Het vormen geïntegreerde veiligheid voor SQL Server op Vensters voor JBoss {#configuring-integrated-security-for-sql-server-on-windows-for-jboss}

1. Wijzig [JBOSS_HOME]\\standalone\configuration\lc_{datasource.xml} om `integratedSecurity=true` aan verbindingsURL, zoals aangetoond in dit voorbeeld toe te voegen:

   ```as3
    jdbc:sqlserver://<serverhost>:<port>;databaseName=<dbname>;integratedSecurity=true
   ```

1. Voeg het bestand sqljdbc_auth.dll toe aan het Windows-systeempad op de computer waarop de toepassingsserver wordt uitgevoerd. Het bestand sqljdbc_auth.dll bevindt zich bij de installatie van het stuurprogramma JDBC 6.2.1.0 van Microsoft SQL.
1. Wijzig JBoss de dienstbezit van Vensters (JBoss voor AEM Forms op JEE) voor Aanmelden vanaf Lokaal Systeem aan een login rekening die het gegevensbestand van AEM Forms en een minimumreeks voorrechten heeft. Als u JBoss van de bevellijn in plaats van als dienst van Vensters in werking stelt, te hoeven u niet om deze stap uit te voeren.
1. Plaats Veiligheid voor SQL Server van **Gemengde** wijze aan de Authentificatie van **Vensters slechts**.

#### Geïntegreerde beveiliging voor SQL Server configureren in Windows voor WebLogic {#configuring-integrated-security-for-sql-server-on-windows-for-weblogic}

1. Start de WebLogic Server Administration Console door de volgende URL te typen in de URL-regel van een webbrowser:

   ```as3
   https://[host name]:7001/console
   ```

1. Klik onder Midden wijzigen op **Vergrendelen en bewerken**.
1. Klik onder Domeinstructuur op *[base_domain]* > **Services** > **JDBC** > **Gegevensbronnen** en klik in het rechterdeelvenster op **IDP_DS**.
1. Klik in het volgende scherm op het tabblad **Configuratie** op het tabblad **Verbindingspool** en typ in het vak **Eigenschappen** `integratedSecurity=true`.
1. Klik onder Domeinstructuur op **[base_domain]** > **Services** > **JDBC** > **Gegevensbronnen** en klik in het rechterdeelvenster op **RM_DS**.
1. Klik in het volgende scherm op het tabblad **Configuratie** op het tabblad **Verbindingspool** en typ in het vak **Eigenschappen** `integratedSecurity=true`.
1. Voeg het bestand sqljdbc_auth.dll toe aan het Windows-systeempad op de computer waarop de toepassingsserver wordt uitgevoerd. Het bestand sqljdbc_auth.dll bevindt zich bij de installatie van het stuurprogramma JDBC 6.2.1.0 van Microsoft SQL.
1. Plaats Veiligheid voor SQL Server van **Gemengde** wijze aan de Authentificatie van **Vensters slechts**.

#### Het vormen geïntegreerde veiligheid voor SQL Server op Vensters voor WebSphere {#configuring-integrated-security-for-sql-server-on-windows-for-websphere}

Op WebSphere, kunt u geïntegreerde veiligheid vormen slechts wanneer u een externe SQL bestuurder van de Server JDBC, niet de SQL bestuurder van de Server JDBC gebruikt die met WebSphere wordt ingebed.

1. Meld u aan bij de beheerconsole van WebSphere.
1. In de navigatieboom, klik **Middelen** > **JDBC** > **Gegevensbronnen** en, in de juiste ruit, klik **IDP_DS**.
1. Klik in het rechterdeelvenster onder Extra eigenschappen op **Aangepaste eigenschappen** en klik vervolgens op **Nieuw**.
1. Typ in het vak **Naam** `integratedSecurity` en typ in het vak **Waarde** `true`.
1. In de navigatieboom, klik **Middelen** > **JDBC** > **Gegevensbronnen** en, in de juiste ruit, klik **RM_DS**.
1. Klik in het rechterdeelvenster onder Extra eigenschappen op **Aangepaste eigenschappen** en klik vervolgens op **Nieuw**.
1. Typ in het vak **Naam** `integratedSecurity` en typ in het vak **Waarde** `true`.
1. Voeg op de computer waarop WebSphere is geïnstalleerd het bestand sqljdbc_auth.dll toe aan het systeempad van Windows (C:\Windows). Het bestand sqljdbc_auth.dll bevindt zich op dezelfde locatie als de installatie van het stuurprogramma voor Microsoft SQL JDBC 1.2 (standaard *[InstallDir]*/sqljdbc_1.2/enu/auth/x86).
1. Selecteer **Start** > **Configuratiescherm** > **Services**, klik met de rechtermuisknop op de Windows-service voor WebSphere (IBM WebSphere Application Server &lt;version> - &lt;node>) en selecteer **Eigenschappen**.
1. Klik in het dialoogvenster Eigenschappen op het tabblad **Aanmelden** .
1. Selecteer **Dit account** en geef de informatie op die nodig is voor het instellen van het aanmeldingsaccount dat u wilt gebruiken.
1. Plaats Veiligheid op SQL Server van **Gemengde** wijze aan de Authentificatie van **Vensters slechts**.

### Toegang tot gevoelige inhoud in de database beveiligen {#protecting-access-to-sensitive-content-in-the-database}

Het het gegevensbestandschema van AEM Forms bevat gevoelige informatie over systeemconfiguratie en bedrijfsprocessen en zou achter de firewall moeten worden verborgen. De database moet worden beschouwd binnen dezelfde vertrouwensgrens als de formulierserver. Om tegen informatieonthulling en diefstal van bedrijfsgegevens te beschermen, moet het gegevensbestand door de gegevensbestandbeheerder (DBA) worden gevormd om toegang slechts door erkende beheerders toe te staan.

Als toegevoegde voorzorg, zou u het gebruiken van gegevensbestand verkoper-specifieke hulpmiddelen moeten overwegen om kolommen in lijsten te coderen die de volgende gegevens bevatten:

* Documentsleutels voor rechtenbeheer
* Sleutel voor versleuteling HSM PIN-code opslaan
* Hashes lokaal gebruikerswachtwoord

Voor informatie over verkoper-specifieke hulpmiddelen, zie [&quot;de veiligheidsinformatie van het Gegevensbestand&quot;](https://helpx.adobe.com/aem-forms/6-1/hardening-security/general-security-considerations.html#database_security_information).

### LDAP-beveiliging {#ldap-security}

Een Lightweight Directory Access Protocol (LDAP)-directory wordt door AEM Forms op JEE doorgaans gebruikt als bron voor zakelijke gebruikers- en groepsgegevens en als middel om wachtwoordverificatie uit te voeren. Zorg ervoor dat uw LDAP-directory is geconfigureerd voor gebruik van SSL (Secure Socket Layer) en dat AEM Forms in JEE zijn geconfigureerd voor toegang tot uw LDAP-directory via de SSL-poort.

#### LDAP-ontkenning van service {#ldap-denial-of-service}

Een algemene aanval met LDAP heeft tot gevolg dat een aanvaller opzettelijk meerdere keren niet verifieert. Hierdoor wordt de LDAP-directoryserver gedwongen een gebruiker uit alle LDAP-afhankelijke services te sluiten.

U kunt het aantal mislukkingspogingen en de verdere sluitingstijd plaatsen die de AEM Forms uitvoert wanneer een gebruiker herhaaldelijk er niet in slaagt om aan AEM Forms voor authentiek te verklaren. Kies lage waarden in de beheerconsole. Wanneer het selecteren van het aantal mislukkingspogingen, is het belangrijk om te begrijpen dat nadat alle pogingen worden gemaakt, AEM Forms de gebruiker sluit uit alvorens de Server van de Folder LDAP doet.

#### Automatische accountvergrendeling instellen {#set-automatic-account-locking}

1. Meld u aan bij de beheerconsole.
1. Klik op **Instellingen** > **Gebruikersbeheer** > **Domeinbeheer**.
1. Stel onder Instellingen voor automatisch vergrendelen van accounts de optie **Maximum aantal opeenvolgende verificatiefouten** in op een laag getal, bijvoorbeeld 3.
1. Click **Save**.

### Controle en registratie {#auditing-and-logging}

Het juiste en veilige gebruik van toepassingscontrole en het registreren kan helpen ervoor zorgen dat de veiligheid en andere anomalische gebeurtenissen worden gevolgd en zo snel mogelijk ontdekt. Het effectieve gebruik van controle en het registreren binnen een toepassing omvat punten zoals het volgen van succesvolle en ontbroken logins, evenals zeer belangrijke toepassingsgebeurtenissen zoals de verwezenlijking of de schrapping van zeer belangrijke verslagen.

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
   <td><p>Plaats aangewezen AEM Forms op de toegangsbeheerlijsten van het JEE- logboekdossier (ACLs).</p> <p>Door de juiste referenties in te stellen, voorkomt u dat aanvallers de bestanden verwijderen.</p> <p>De veiligheidstoestemmingen op de folder van het logboekdossier zouden Volledige Controle voor Beheerders en de groepen van het SYSTEEM moeten zijn. De gebruikersaccount voor AEM Forms moet alleen lees- en schrijfmachtigingen hebben.</p> </td> 
  </tr> 
  <tr> 
   <td><p>redundantie van logbestanden</p> </td> 
   <td><p>Als de middelen toelaten, verzend logboeken naar een andere server in real time die niet door de aanvaller (schrijf slechts) door Syslog, Tivoli, de Server van de Manager van de Verrichtingen van Microsoft (MOM), of een ander mechanisme te gebruiken toegankelijk is.</p> <p>Als u logbestanden op deze manier beschermt, voorkomt u dat er wordt geknoeid. Bovendien wordt het opslaan van logbestanden in een centrale opslagplaats ondersteund op het gebied van correlatie en controle (bijvoorbeeld als meerdere formulierservers in gebruik zijn en er op meerdere computers waar elke computer om een wachtwoord wordt gevraagd een aanval met het wachtwoord plaatsvindt).</p> </td> 
  </tr> 
 </tbody> 
</table>

## Het vormen AEM Forms op JEE voor toegang voorbij de onderneming {#configuring-aem-forms-on-jee-for-access-beyond-the-enterprise}

Nadat u met succes AEM Forms op JEE installeert, is het belangrijk om de veiligheid van uw milieu periodiek te handhaven. Deze sectie beschrijft de taken die worden geadviseerd om de veiligheid van uw AEM Forms op de productieserver van JEE te handhaven.

### Een reverse-proxy instellen voor webtoegang {#setting-up-a-reverse-proxy-for-web-access}

Een *reverse-proxy* kan worden gebruikt om ervoor te zorgen dat één set URL&#39;s voor AEM Forms in JEE-webtoepassingen beschikbaar is voor zowel externe als interne gebruikers. Deze configuratie is veiliger dan gebruikers toe te staan om rechtstreeks met de toepassingsserver te verbinden die AEM Forms op JEE loopt. De reverse-proxy voert alle HTTP-aanvragen uit voor de toepassingsserver waarop AEM Forms wordt uitgevoerd op JEE. Gebruikers hebben alleen netwerktoegang tot de reverse-proxy en kunnen alleen proberen URL-verbindingen te maken die door de reverse-proxy worden ondersteund.

**AEM Forms in URL&#39;s van JEE-hoofdmap voor gebruik met reverse-proxyserver**

De volgende URL&#39;s van de hoofdmap van de toepassing voor elke AEM Forms in de JEE-webtoepassing. Configureer de reverse-proxy alleen om URL&#39;s beschikbaar te maken voor de functionaliteit van webtoepassingen die u aan eindgebruikers wilt verschaffen.

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
   <td><p>Rights Management-webtoepassing voor eindgebruikers</p> </td> 
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
   <td><p>PDF Generator-beheerwebtoepassing</p> </td> 
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
   <td><p>Servlet voor bootstrapping van de AEM Forms op de gegevensopslagplaats van JEE</p> </td> 
   <td><p>Nee</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/zeep/*</p> </td> 
   <td><p>Informatiepagina voor webservices voor formulierserver</p> </td> 
   <td><p>Nee</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/soap/services/*</p> </td> 
   <td><p>Webservice-URL voor alle services van formulierservers</p> </td> 
   <td><p>Nee</p> </td> 
   <td><p>Nee</p> </td> 
  </tr> 
  <tr> 
   <td><p>/edc/admin/*</p> </td> 
   <td><p>Rights Management-webtoepassing</p> </td> 
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
   <td><p>Formulierwebtoepassingsbestanden</p> </td> 
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
   <td><p>Formulierbeheerpagina's</p> </td> 
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
   <td><p>AEM Forms op pagina met JEE Core-configuratie-instellingen</p> </td> 
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

U kunt bijvoorbeeld zijn aangemeld bij de beheerconsole terwijl u tegelijkertijd door een andere website bladert. Een van de webpagina&#39;s kan een HTML-afbeeldingstag bevatten met een `src` kenmerk dat een serverscript aanwijst op de website van het slachtoffer. Door gebruik te maken van het op cookies gebaseerde mechanisme voor sessieverificatie dat door webbrowsers wordt geboden, kan de aanvallende website kwaadaardige verzoeken verzenden naar dit script op de server van het slachtoffer, waarbij de vraag als de legitieme gebruiker wordt gesteld. Zie [https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)#Examples](https://www.owasp.org/index.php/Cross-Site_Request_Forgery_(CSRF)#Examples)voor meer voorbeelden.

De volgende kenmerken komen voor in KVP:

* Neem sites op die afhankelijk zijn van de identiteit van een gebruiker.
* Gebruik het vertrouwen van de site in die identiteit.
* Steek de browser van de gebruiker in het verzenden van HTTP-aanvragen naar een doelsite.
* Neem HTTP-aanvragen op die bijwerkingen hebben.

AEM Forms op JEE gebruiken de eigenschap van de Filter van de Referateur om aanvallen te blokkeren CSRF. In deze sectie worden de volgende termen gebruikt om het filtermechanisme van de verwijzer te beschrijven:

* **Toegestane referentie:** Een verwijzing is het adres van de bronpagina die een verzoek naar de server verzendt. Voor JSP-pagina&#39;s of -formulieren is de referentie meestal de vorige pagina in de browsergeschiedenis. Verwijzers voor afbeeldingen zijn meestal de pagina&#39;s waarop de afbeeldingen worden weergegeven. U kunt de Referrer identificeren die toegang tot uw servermiddelen door hen aan de Toegestane lijst van de Referant wordt verleend toe te voegen.
* **Uitzonderingen toegestane verwijzer:** U wilt mogelijk het bereik van toegang voor een bepaalde referentie beperken in uw lijst Toegestane referentie. Als u deze beperking wilt toepassen, kunt u afzonderlijke paden van die referentie toevoegen aan de lijst Toegestane uitzonderingen Referrer. Verzoeken die afkomstig zijn van paden in de lijst Toegestane uitzonderingen voor referenties kunnen geen bron op de formulierserver aanroepen. U kunt de Uitzonderingen van de Verwijzer van de Toestemming voor een specifieke toepassing bepalen en ook een globale lijst van uitzonderingen gebruiken die op alle toepassingen van toepassing zijn.
* **Toegestane URI&#39;s:** Dit is een lijst met bronnen die moeten worden gebruikt zonder de koptekst van de verwijzer te controleren. De middelen, bijvoorbeeld, hulppagina&#39;s, die niet in staatsveranderingen op de server resulteren, kunnen aan deze lijst worden toegevoegd. De bronnen in de lijst Toegestane URI&#39;s worden nooit geblokkeerd door het filter Referrer, ongeacht wie de Referrer is.
* **Null-referentie:** Een serveraanvraag die niet is gekoppeld aan of niet afkomstig is van een bovenliggende webpagina, wordt beschouwd als een aanvraag van een Null-referentie. Wanneer u bijvoorbeeld een nieuw browservenster opent, typt u een adres en drukt u op Enter, is de referentie die naar de server is verzonden null. Een Desktoptoepassing (.NET of SWING) die een HTTP- verzoek aan een Webserver indienen, verzendt ook een Null Referrer naar de server.

### Filterverwijzing {#referer-filtering}

Het filterproces Referrer kan als volgt worden beschreven:

1. De formulierserver controleert de HTTP-methode die wordt gebruikt voor oproepen:

   1. Als het POST is, voert de formulierserver de koptekstcontrole Referrer uit.
   1. Als het GET is, overslaat de formulierserver de controle Referrer, tenzij *CSRF_CHECK_GETS* is ingesteld op true, in welk geval de headercontrole Referrer wordt uitgevoerd. *CSRF_CHECK_GETS* wordt gespecificeerd in het *web.xml* dossier voor uw toepassing.

1. De formulierserver controleert of de aangevraagde URI bestaat in allowlist:

   1. Als de URI is toegestaan, accepteert de server de aanvraag.
   1. Als de aangevraagde URI niet is toegestaan, haalt de server de Referrer van de aanvraag op.

1. Als er een Referrer in het verzoek is, controleert de server of het een Toegestane Referrer is. Als dit is toegestaan, controleert de server op een uitzondering Referrer:

   1. Als het een uitzondering is, wordt het verzoek geblokkeerd.
   1. Als het geen uitzondering is, wordt het verzoek overgegaan.

1. Als er geen Referrer in het verzoek is, controleert de server of een Null Referrer wordt toegestaan:

   1. Als een Null-referentie is toegestaan, wordt het verzoek doorgegeven.
   1. Als een Null Referrer niet wordt toegestaan, controleert de server of gevraagde URI een uitzondering voor de Null Referrer is en behandelt dienovereenkomstig het verzoek.

### Filteren van referenties beheren {#managing-referer-filtering}

AEM Forms op JEE beschikken over een verwijzingsfilter om Referrer op te geven die toegang hebben tot uw serverbronnen. Standaard filtert het filter Referrer geen aanvragen die een veilige HTTP-methode gebruiken, bijvoorbeeld GET, tenzij *CSRF_CHECK_GETS* is ingesteld op true. Als het havenaantal voor een Toegestane ingang van de Referentie aan 0 wordt geplaatst, zullen de AEM Forms op JEE alle verzoeken met Referrer van die gastheer ongeacht het havenaantal toestaan. Als er geen poortnummer is opgegeven, zijn alleen aanvragen van standaardpoort 80 (HTTP) of poort 443 (HTTPS) toegestaan. Filteren met verwijzing is uitgeschakeld als alle items in de lijst Toegestane verwijzing worden verwijderd.

Wanneer u de Diensten van het Document eerst installeert, wordt de Toegestane lijst van de Verwijzing bijgewerkt met het adres van de server waarop de Diensten van het Document geïnstalleerd is. De ingangen voor de server omvatten de servernaam, het IPv4 adres, het IPv6 adres als IPv6 wordt toegelaten, het loopbackadres, en een localhost ingang. De namen die aan de lijst Toegestane verwijzing worden toegevoegd, worden geretourneerd door het hostbesturingssysteem. Een server met een IP-adres van 10.40.54.187 bevat bijvoorbeeld de volgende vermeldingen: `https://server-name:0, https://10.40.54.187:0, https://127.0.0.1:0, http://localhost:0`. Voor elke niet-gekwalificeerde naam die door het besturingssysteem Host wordt geretourneerd (namen die geen IPv4-adres, IPv6-adres of gekwalificeerde domeinnaam hebben), wordt de allowlist niet bijgewerkt. Wijzig de Toegestane lijst van Referiteers om uw bedrijfsomgeving aan te passen. Implementeer de formulierserver niet in de productieomgeving met de standaardlijst Toegestane verwijzing. Nadat u een van de toegestane referentie-, referentie-uitzonderingen of URI&#39;s hebt gewijzigd, zorgt u ervoor dat de server opnieuw wordt gestart zodat de wijzigingen van kracht worden.

**Toegestane verwijzingslijst beheren**

U kunt de lijst Toegestane verwijzing beheren via de gebruikersbeheerinterface van de beheerconsole. De gebruikersbeheerinterface biedt u de functionaliteit om de lijst te maken, bewerken of verwijderen. Raadpleeg de sectie * [Preventing CSRF aanvallen](/help/forms/using/admin-help/preventing-csrf-attacks.md)* van de *beleidsHelp* voor meer informatie over het werken met de lijst Allowed Referrer.

**Toegestane uitzondering Referrer en Toegestane URI-lijsten beheren**

AEM Forms op JEE verschaffen API&#39;s voor het beheer van de lijst Uitzondering toegestane verwijzing en de lijst Toegestane URI. U kunt deze API&#39;s gebruiken om de lijst op te halen, te maken, te bewerken of te verwijderen. Hieronder volgt een lijst met beschikbare API&#39;s:

* createAllowedURIsList
* getAllowedURIsList
* updateAllowedURIsList
* deleteAllowedURIsList
* addAllowedRefererExceptions
* getAllowedRefererExceptions
* updateAllowedRefererExceptions
* deleteAllowedRefererExceptions

Raadpleeg de* AEM Forms over de API-naslaggids voor JEE* voor meer informatie over de API&#39;s.

Gebruik de lijst ***LC_GLOBAL_ALLOWED_REFERER_EXCEPTION*** voor de Uitzonderingen van de Verwijzer op globaal niveau toe te staan, d.w.z. om uitzonderingen te bepalen die op alle toepassingen van toepassing zijn. Deze lijst bevat alleen URI&#39;s met een absoluut pad (bijvoorbeeld `/index.html`) of een relatief pad (bijvoorbeeld `/sample/`). U kunt ook een reguliere expressie toevoegen aan het einde van een relatieve URI, bijvoorbeeld `/sample/(.)*`.

De lijst-id ***LC_GLOBAL_ALLOWED_REFERER_EXCEPTION*** wordt gedefinieerd als een constante in de `UMConstants` klasse van de `com.adobe.idp.um.api` naamruimte, gevonden in `adobe-usermanager-client.jar`. U kunt de AEM Forms-API&#39;s gebruiken om deze lijst te maken, te wijzigen of te bewerken. Als u bijvoorbeeld de lijst Uitzonderingen globale toegestane verwijzingsverwijzing wilt maken, gebruikt u:

```as3
addAllowedRefererExceptions(UMConstants.LC_GLOBAL_ALLOWED_REFERER_EXCEPTION, Arrays.asList("/index.html", "/sample/(.)*"))
```

Gebruik de ***lijst CSRF_ALLOWED_REFERER_EXCEPTIONS*** voor toepassing-specifieke uitzonderingen.

**Het filter Referrer uitschakelen**

Als het filter Referrer de toegang tot de formulierserver volledig blokkeert en u de lijst Toegestane verwijzing niet kunt bewerken, kunt u het opstartscript van de server bijwerken en het filteren van referenties uitschakelen.

Neem het argument `-Dlc.um.csrffilter.disabled=true` JAVA op in het opstartscript en start de server opnieuw. Zorg ervoor dat u het argument JAVA schrapt nadat u correct de Toegestane lijst van de Verwijzing hebt aangepast.

**Filteren met referenties voor aangepaste WAR-bestanden**

Mogelijk hebt u aangepaste WAR-bestanden gemaakt die u kunt gebruiken voor AEM Forms op JEE om aan uw zakelijke vereisten te voldoen. Als u het filteren van verwijzingen wilt inschakelen voor uw aangepaste WAR-bestanden, neemt u ***adobe-usermanager-client.jar*** op in het klassepad voor de WAR en neemt u een filteritem op in het bestand* web.xml* met de volgende parameters:

**CSRF_CHECK_GETS** controleert de controle van de Referateur op GET verzoeken. Wanneer deze parameter niet is gedefinieerd, wordt de standaardwaarde op false ingesteld. Neem deze parameter alleen op als u uw GET-aanvragen wilt filteren.

**CSRF_ALLOWED_REFERER_EXCEPTIONS** is identiteitskaart van de Toegestane lijst van Uitzonderingen van de Referteur. Met het filter Referrer voorkomt u dat aanvragen die afkomstig zijn van referenties in de lijst die met de lijst-id wordt aangegeven, een bron op de formulierserver aanroepen.

**CSRF_ALLOWED_URIS_LIST_NAME** is identiteitskaart van de Toegestane lijst URIs. Het filter Referrer blokkeert geen aanvragen voor een van de bronnen in de lijst die door de lijst-id wordt geïdentificeerd, ongeacht de waarde van de verwijzaarheader in de aanvraag.

**CSRF_ALLOW_NULL_REFERER** controleert het gedrag van de Filter van de Referteur wanneer de Referrer ongeldig of niet aanwezig is. Wanneer deze parameter niet is gedefinieerd, wordt de standaardwaarde op false ingesteld. Neem deze parameter alleen op als u Null-referenties wilt toestaan. Het toestaan van ongeldige verwijzers kan sommige types van het Verzoek van de Vervalsing van de Plaats van de Overeenkomst toestaan.

**CSRF_NULL_REFERER_EXCEPTIONS** is een lijst van URIs waarvoor geen controle van de Referteur wordt uitgevoerd wanneer de Referrer ongeldig is. Deze parameter wordt toegelaten slechts wanneer *CSRF_ALLOW_NULL_REFERER* aan vals wordt geplaatst. Scheid meerdere URI&#39;s in de lijst met een komma.

Hieronder ziet u een voorbeeld van de filtervermelding in het bestand *web.xml* voor een ***WAR-bestand van het type SAMPLE*** :

```as3
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

### De protocollen van het netwerk die door AEM Forms op JEE worden gebruikt {#network-protocols-used-by-aem-forms-on-jee}

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
     <li><p>Adobe Reader® gebruikt SOAP voor AEM Forms op JEE-server-webservices</p> </li> 
     <li><p>Adobe Flash®-toepassingen gebruiken SOAP voor webservices voor formulierservers</p> </li> 
     <li><p>AEM Forms op JEE SDK-aanroepen bij gebruik in de SOAP-modus</p> </li> 
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
   <td><p>AEM Forms bij JEE-controle van gecontroleerde mappen voor invoer naar een service (gecontroleerd mapeindpunt)</p> </td> 
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
     <li><p>Interne AEM Forms voor toegang tot JEE-opslagplaats</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>WebDAV</p> </td> 
   <td><p>Laat ver doorbladeren van de AEM Forms op ontwerp-tijd bewaarplaats JEE (vormen, fragmenten, etc.) door om het even welke cliënt WebDAV toe</p> </td> 
  </tr> 
  <tr> 
   <td><p>AMF</p> </td> 
   <td><p>Adobe Flash-toepassingen, waarbij AEM Forms op JEE-serverservices zijn geconfigureerd met een eindpunt Remoting</p> </td> 
  </tr> 
  <tr> 
   <td><p>JMX</p> </td> 
   <td><p>AEM Forms op JEE stellen MBans voor controle beschikbaar gebruikend JMX</p> </td> 
  </tr> 
 </tbody> 
</table>

### Poorten voor toepassingsservers {#ports-for-application-servers}

Deze sectie beschrijft de standaardhavens (en afwisselende configuratiereiken) voor elk type van gesteunde toepassingsserver. Deze poorten moeten in- of uitgeschakeld zijn op de binnenfirewall, afhankelijk van de netwerkfunctionaliteit die u wilt toestaan voor clients die verbinding maken met de toepassingsserver waarop AEM Forms op JEE worden uitgevoerd.

>[!NOTE]
>
>Standaard stelt de server verschillende JMX MBans beschikbaar onder de naamruimte adobe.com. Alleen informatie die nuttig is voor de bewaking van de serverstatus wordt weergegeven. Nochtans, om informatieonthulling te verhinderen, zou u bezoekers in een onvertrouwd netwerk moeten verhinderen omhoog JMX MBans te kijken en tot gezondheidsmetriek toegang te hebben.

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
     <li><p>Admin Server-luisterpoort: standaardwaarde is 7001</p> </li> 
     <li><p>SSL-luisterpoort voor Admin Server: standaardwaarde is 7002</p> </li> 
     <li><p>Poort geconfigureerd voor beheerde server, bijvoorbeeld 8001</p> </li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td><p>WebLogic-beheerpoorten niet vereist voor toegang tot AEM Forms op JEE</p> </td> 
   <td> 
    <ul> 
     <li><p>Aanluisterpoort voor beheerde server: Configureerbaar van 1 tot 65534</p> </li> 
     <li><p>SSL-luisterpoort voor beheerde server: Configureerbaar van 1 tot 65534</p> </li> 
     <li><p>Node Manager luistert poort: standaardwaarde is 5556</p> </li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

**WebSphere-poorten**

Voor informatie over havens WebSphere die AEM Forms op JEE vereisen, ga naar het aantal dat van de Haven in WebSphere de Server UI van de Toepassing plaatst.

### SSL configureren {#configuring-ssl}

Verwijzend naar de fysieke architectuur die in de sectie [AEM Forms over fysieke architectuur](hardening-aem-forms-jee-environment.md#aem-forms-on-jee-physical-architecture)JEE wordt beschreven, zou u SSL voor alle verbindingen moeten vormen die u van plan bent te gebruiken. Specifiek, moeten alle verbindingen van de ZEEP over SSL worden geleid om blootstelling van gebruikersgeloofsbrieven op een netwerk te verhinderen.

Voor instructies op hoe te om SSL op JBoss, WebLogic, en WebSphere te vormen, zie &quot;het Vormen SSL&quot;in de [beleidshulp](https://www.adobe.com/go/learn_aemforms_admin_64).

### SSL-omleiding configureren {#configuring-ssl-redirect}

Nadat u uw toepassingsserver vormt om SSL te steunen, moet u ervoor zorgen dat al verkeer van HTTP aan toepassingen en de diensten wordt afgedwongen om de SSL haven te gebruiken.

Raadpleeg de documentatie bij de toepassingsserver voor informatie over SSL-omleiding voor WebSphere of WebLogic.

1. Open bevelherinnering, navigeer aan /JBOSS_HOME/standalone/configuratiemap, en voer het volgende bevel uit:

   `keytool -genkey -alias jboss7 -keyalg RSA -keystore server.keystore -validity 10950`

1. Open het bestand JBOSS_HOME/standalone/configuration/standalone.xml voor bewerking.

   Voeg de volgende details toe na het &lt;subsysteem xmlns=&quot;urn:jreliëf:domain:1.1&quot; native=&quot;false&quot; default-virtual-server=&quot;default-host&quot;>-element:

   &lt;naam van connector=&quot;https&quot; protocol=&quot;HTTP/1.1&quot; scheme=&quot;https&quot; socket-binding=&quot;https&quot; enabled=&quot;true&quot; secure=&quot;true&quot;/>

1. Voeg de volgende code toe in het https-verbindingselement:

   ```
   <connector name="https" protocol="HTTP/1.1" scheme="https" socket-binding="https" secure="true" enabled="true"> 
    <ssl name="jboss7_ssl" key-alias="jboss71" password="Tibco321" certificate-key-file="../standalone/configuration/server.keystore" protocol="TLSv1"/> 
    </connector>
   ```

   Sla het bestand standalone.xml op en sluit het.

## Windows-specifieke beveiligingsaanbevelingen {#windows-specific-security-recommendations}

Deze sectie bevat veiligheidsaanbevelingen die voor Vensters wanneer gebruikt specifiek zijn om AEM Forms op JEE in werking te stellen.

### JBoss-serviceaccounts {#jboss-service-accounts}

De AEM Forms bij de turnkey van JEE-installatie stellen standaard een serviceaccount in met behulp van de lokale systeemaccount. De ingebouwde gebruikersaccount voor het lokale systeem heeft een hoge mate van toegankelijkheid; het maakt deel uit van de groep Beheerders. Als de identiteit van een arbeidersproces als Lokale de gebruikersrekening van het Systeem loopt, heeft dat arbeidersproces volledige toegang tot het volledige systeem.

#### De toepassingsserver uitvoeren met een niet-beheeraccount {#run-the-application-server-using-a-non-administrative-account}

1. In de Console van het Beheer van Microsoft (MMC), creeer een lokale gebruiker voor de dienst van de vormenserver om login als:

   * Selecteer **Gebruiker kan wachtwoord** niet wijzigen.
   * Controleer op het tabblad **Lid van** of de gebruikersgroep wordt weergegeven.

1. Selecteer **Instellingen** > **Systeembeheer** > **Services**.
1. Dubbelklik op de service van de toepassingsserver en stop de service.
1. Selecteer op het tabblad **Aanmelden** de optie **Deze account**, blader naar de gebruikersaccount die u hebt gemaakt en voer het wachtwoord voor de account in.
1. Geef in het venster Lokale beveiligingsinstellingen onder Toewijzing gebruikersrechten de volgende rechten op de gebruikersaccount waarop de formulierserver wordt uitgevoerd:

   * Ontken login door de EindDiensten
   * Aanmelding lokaal weigeren
   * Aanmelden als service (moet al zijn ingesteld)

1. Wijzig de machtigingen voor de nieuwe gebruikersaccount voor de volgende directory&#39;s:
   * **GDS-map**(Global Document Storage): De locatie van de GDS-map wordt handmatig geconfigureerd tijdens het installatieproces van AEM Forms. Als de locatie-instelling tijdens de installatie leeg blijft, wordt de locatie standaard ingesteld op een directory onder de installatie van de toepassingsserver op `[JBoss root]/server/[type]/svcnative/DocumentStorage`
   * **CRX-Repository directory**: De standaardlocatie is `[AEM-Forms-installation-location]\crx-repository`
   * **Tijdelijke mappen** voor AEM Forms:
      * (Windows) TMP- of TEMP-pad zoals ingesteld in de omgevingsvariabelen
      * (AIX, Linux, of Solaris) Logged-in de huisfolder van de gebruiker Op op UNIX-Gebaseerde systemen, kan een niet wortelgebruiker de volgende folder als tijdelijke folder gebruiken:
      * (Linux) /var/tmp of /usr/tmp
      * (AIX) /tmp of /usr/tmp
      * (Solaris) /var/tmp of /usr/tmp
1. Geef de nieuwe gebruikersaccount schrijfmachtigingen voor de volgende directory&#39;s:
   * [JBoss-directory]\standalone\deployment
   * [JBoss-directory]\standalone\
   * [JBoss-directory]\bin\
   >[!NOTE]
   >
   > De standaardinstallatielocatie van JBoss Application Server:
   > * Windows: C:\Adobe\Adobe_Experience_Manager_Forms\jboss
   > * Linux: /opt/jreliëf/.


1. Start de service van de toepassingsserver.

### Beveiliging bestandssysteem {#file-system-security}

AEM Forms op JEE gebruiken het bestandssysteem op de volgende manieren:

* Hiermee worden tijdelijke bestanden opgeslagen die worden gebruikt bij de verwerking van de invoer en uitvoer van documenten
* Slaat dossiers in het globale archiefopslag op die worden gebruikt om de oplossingscomponenten te steunen die worden geïnstalleerd
* Gecontroleerde mappen slaan neergezette bestanden op die worden gebruikt als invoer voor een service vanaf de locatie van een bestandssysteemmap

Als u gecontroleerde mappen gebruikt als een manier om documenten met een service van de formulierserver te verzenden en te ontvangen, moet u extra voorzorgsmaatregelen treffen met betrekking tot de beveiliging van het bestandssysteem. Wanneer een gebruiker inhoud in de controlemap neerzet, wordt die inhoud via de controlemap weergegeven. In dit geval wordt de werkelijke eindgebruiker niet geverifieerd door de service. In plaats daarvan, baseert het zich op ACL en het niveauveiligheid van het Aandeel op het omslagniveau om te bepalen wie de dienst kan effectief aanhalen.

## JBoss-specifieke veiligheidsaanbevelingen {#jboss-specific-security-recommendations}

Deze sectie bevat de configuratieaanbevelingen van de toepassingsserver die voor JBoss 7.0.6 wanneer gebruikt specifiek zijn om AEM Forms op JEE in werking te stellen.

### JBoss Management Console en JMX Console uitschakelen {#disable-jboss-management-console-and-jmx-console}

De toegang tot de JBoss Management Console en de Console JMX wordt reeds gevormd (de controle JMX wordt onbruikbaar gemaakt) wanneer u AEM Forms op JEE op JBoss door de kant-en-klare installatiemethode te gebruiken installeert. Als u uw eigen JBoss Server van de Toepassing gebruikt, zorg ervoor dat de toegang tot de Console van het Beheer JBoss en JMX controleconsole wordt beveiligd. De toegang tot de JMX controleconsole wordt geplaatst in het JBoss configuratiedossier genoemd jmx-invoker-service.xml.

### Bladeren door directory&#39;s uitschakelen {#disable-directory-browsing}

Na het registreren in de Console van het Beleid, is het mogelijk om de de folderlijst van de console te doorbladeren door URL te wijzigen. Als u bijvoorbeeld de URL wijzigt in een van de volgende URL&#39;s, wordt mogelijk een mappenlijst weergegeven:

```as3
https://<servername>:8080/adminui/secured/ 
https://<servername>:8080/um/
```

## WebLogic-specifieke beveiligingsaanbevelingen {#weblogic-specific-security-recommendations}

Deze sectie bevat aanbevelingen voor de configuratie van toepassingsservers voor het beveiligen van WebLogic 9.1 wanneer het runnen van AEM Forms op JEE.

### Bladeren door directory&#39;s uitschakelen {#disable_directory_browsing-1}

Stel de eigenschappen voor indexmappen in het bestand weblogic.xml in op `false`, zoals in dit voorbeeld:

```as3
<container-descriptor> 
    <index-directory-enabled>false 
    </index-directory-enabled> 
</container-descriptor>
```

### WebLogic SSL-poort inschakelen {#enable-weblogic-ssl-port}

Standaard schakelt WebLogic de standaard SSL-luisterpoort 7002 niet in. Schakel deze poort in de WebLogic Server Administration Console in voordat u SSL configureert.

## WebSphere-specifieke beveiligingsaanbevelingen {#websphere-specific-security-recommendations}

Deze sectie bevat de configuratieaanbevelingen van de toepassingsserver voor het beveiligen van WebSphere die AEM Forms op JEE in werking stellen.

### Bladeren door directory&#39;s uitschakelen {#disable_directory_browsing-2}

Stel de `directoryBrowsingEnabled` eigenschap in het bestand ibm-web-ext.xml in op `false`.

### Beveiliging van WebSphere-beheer inschakelen {#enable-websphere-administrative-security}

1. Meld u aan bij de beheerconsole van WebSphere.
1. Ga in de navigatiestructuur naar **Beveiliging** > **Algemene beveiliging**
1. Selecteer **Beheersbeveiliging** inschakelen.
1. Schakel zowel **Toepassingsbeveiliging** inschakelen als Java 2-beveiliging **** gebruiken uit.
1. Klik op **OK** of **Toepassen**.
1. Klik in het vak **Berichten** rechtstreeks op **Opslaan in de hoofdconfiguratie**.