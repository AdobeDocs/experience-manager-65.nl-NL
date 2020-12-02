---
title: Beveiligingscontrolelijst
seo-title: Beveiligingscontrolelijst
description: Leer over de diverse veiligheidsoverwegingen wanneer het vormen en het opstellen van AEM.
seo-description: Leer over de diverse veiligheidsoverwegingen wanneer het vormen en het opstellen van AEM.
uuid: 8e293316-4177-4271-87c6-9dc1a2e85a07
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: de7d7209-c194-4d19-853b-468ebf3fa4b2
docset: aem65
translation-type: tm+mt
source-git-commit: 474fc122f557f32d34fddd9d35a113431f6ce491
workflow-type: tm+mt
source-wordcount: '2841'
ht-degree: 0%

---


# Beveiligingscontrolelijst {#security-checklist}

Deze sectie behandelt diverse stappen die u zou moeten nemen om ervoor te zorgen dat uw AEM installatie wanneer opgesteld veilig is. De controlelijst moet van boven naar beneden worden toegepast.

>[!NOTE]
>
>Aanvullende informatie [is ook beschikbaar over de gevaarlijkste veiligheidsbedreigingen zoals gepubliceerd door Open Web Application Security Project (OWASP)](https://www.owasp.org/index.php/OWASP_Top_Ten_Project).

>[!NOTE]
>
>Er zijn enkele [beveiligingsoverwegingen](/help/sites-developing/dev-guidelines-bestpractices.md#security-considerations) van toepassing op de ontwikkelingsfase.

## Belangrijkste beveiligingsmaatregelen {#main-security-measures}

### AEM uitvoeren in productieklaar {#run-aem-in-production-ready-mode}

Voor meer informatie, zie [lopende AEM in Productie Klaar Wijze ](/help/sites-administering/production-ready.md).

### HTTPS inschakelen voor beveiliging van transportlagen {#enable-https-for-transport-layer-security}

Het inschakelen van de HTTPS-transportlaag op zowel auteur- als publicatieinstanties is verplicht voor het hebben van een beveiligde instantie.

>[!NOTE]
>
>Zie [HTTP inschakelen over SSL](/help/sites-administering/ssl-by-default.md) voor meer informatie.

### Beveiligingshotfixes {#install-security-hotfixes} installeren

Zorg ervoor dat u de nieuwste [beveiligingshotfixes van Adobe](https://helpx.adobe.com/experience-manager/kb/aem63-available-hotfixes.html) hebt geïnstalleerd.

### Standaardwachtwoorden voor de AEM- en OSGi-console-beheeraccounts wijzigen {#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts}

Adobe adviseert sterk dat u na installatie het wachtwoord voor bevoorrechte [**AEM** `admin` rekeningen](#changing-the-aem-admin-password) (op alle instanties) verandert.

Deze rekeningen omvatten:

* De AEM `admin`-account

   Nadat u het wachtwoord voor de AEM-beheerdersaccount hebt gewijzigd, moet u het nieuwe wachtwoord gebruiken om toegang te krijgen tot CRX.

* Het `admin` wachtwoord voor de console van het Web OSGi

   Deze verandering zal ook op de admin rekening worden toegepast die voor de toegang tot van de console van het Web wordt gebruikt, zodat zult u het zelfde wachtwoord moeten gebruiken wanneer de toegang tot van dat.

Deze twee rekeningen gebruiken afzonderlijke geloofsbrieven en het hebben van verschillend, sterk wachtwoord voor elk is essentieel voor een veilige plaatsing.

#### Het AEM beheerderswachtwoord {#changing-the-aem-admin-password} wijzigen

Het wachtwoord voor de AEM-beheerdersaccount kan worden gewijzigd via de console [Granite Operations - Users](/help/sites-administering/granite-user-group-admin.md).

Hier kunt u de `admin` rekening uitgeven en [het wachtwoord ](/help/sites-administering/granite-user-group-admin.md#changing-the-password-for-an-existing-user) veranderen.

>[!NOTE]
>
>Als u de beheerdersaccount wijzigt, wordt ook de OSGi-webconsoleversie gewijzigd. Nadat u de beheerdersaccount hebt gewijzigd, moet u de OSGi-account wijzigen in iets anders.

#### Het belang van het wijzigen van het wachtwoord {#importance-of-changing-the-osgi-web-console-password} voor de OSGi-webconsole

Naast de AEM `admin` rekening, kan het nalaten het standaardwachtwoord voor het wachtwoord van de Webconsole te veranderen OSGi tot leiden:

* Belichting van de server met een standaardwachtwoord tijdens opstarten en afsluiten (wat minuten kan duren voor grote servers);
* Belichting van de server wanneer de opslagplaats is neer/herstart bundel - en OSGI loopt.

Voor meer informatie bij het veranderen van het wachtwoord van de Webconsole, zie [Veranderend het OSGi wachtwoord van de Webconsole admin](/help/sites-administering/security-checklist.md#changing-the-osgi-web-console-admin-password) hieronder.

#### Het beheerwachtwoord {#changing-the-osgi-web-console-admin-password} voor de OSGi-webconsole wijzigen

U moet het wachtwoord ook veranderen dat voor de toegang tot van de console van het Web wordt gebruikt. Dit wordt gedaan door de volgende eigenschappen van [Apache Felix OSGi Management Console](/help/sites-deploying/osgi-configuration-settings.md) te vormen:

**Gebruikersnaam** en  **wachtwoord**, de referenties voor toegang tot de Apache Felix Web Management Console zelf.
Het wachtwoord moet na de eerste installatie worden gewijzigd om de beveiliging van uw exemplaar te garanderen.

Dit doet u als volgt:

1. Navigeer naar de webconsole op `<server>:<port>/system/console/configMgr`.
1. Navigeer naar **Apache Felix OSGi Management Console** en wijzig de **gebruikersnaam** en **wachtwoord**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Klik **Opslaan**.

### Aangepaste fouthandler {#implement-custom-error-handler} implementeren

Adobe raadt aan aangepaste pagina&#39;s voor fouthandlers te definiëren, met name voor 404- en 500 HTTP-antwoordcodes, om openbaarmaking van informatie te voorkomen.

>[!NOTE]
>
>Zie [Hoe kan ik douanescripten of foutenmanagers](https://helpx.adobe.com/experience-manager/kb/CustomErrorHandling.html) kennisbasisartikel voor meer details tot stand brengen.

### Volledige controlelijst voor beveiliging van verzender {#complete-dispatcher-security-checklist}

AEM Dispatcher is een essentieel onderdeel van uw infrastructuur. Adobe adviseert sterk dat u [de controlelijst ](https://helpx.adobe.com/experience-manager/dispatcher/using/security-checklist.html) van de veiligheidscontrole van de verzender voltooit.

>[!CAUTION]
>
>Met de Dispatcher moet u de kiezer &quot;.form&quot; uitschakelen.

## Verificatiestappen {#verification-steps}

### Gebruikers voor replicatie en transport configureren {#configure-replication-and-transport-users}

Een standaardinstallatie van AEM specificeert `admin` als gebruiker voor vervoergeloofsbrieven binnen het gebrek [replicatieagenten](/help/sites-deploying/replication.md). Ook, wordt de admin gebruiker gebruikt aan bron de replicatie op het auteurssysteem.

Met het oog op de veiligheid moeten beide aspecten worden gewijzigd om rekening te houden met het specifieke gebruiksgeval in kwestie, waarbij de volgende twee aspecten in acht moeten worden genomen:

* De **vervoergebruiker** zou niet de admin gebruiker moeten zijn. Stel in plaats daarvan een gebruiker in het publicatiesysteem in die alleen toegangsrechten heeft tot de relevante delen van het publicatiesysteem en gebruik de referenties van die gebruiker voor het vervoer.

   U kunt van de gebundelde replicatie-ontvanger gebruiker beginnen en de toegangsrechten van deze gebruiker vormen om uw situatie aan te passen

* De **replicatiegebruiker** of **Agent Gebruiker ID** zou ook niet de admin gebruiker moeten zijn, maar een gebruiker die slechts inhoud kan zien die verondersteld om wordt herhaald. De replicatiegebruiker wordt gebruikt om de inhoud te verzamelen die op het auteurssysteem moet worden herhaald alvorens het naar de uitgever wordt verzonden.

### Controleer de beveiligingscontroles {#check-the-operations-dashboard-security-health-checks} op het dashboard Bewerkingen

AEM 6 introduceert het nieuwe Dashboard van Verrichtingen, dat op het helpen van systeemexploitanten problemen oplossen en de gezondheid van een geval controleert.

Het dashboard bevat ook een verzameling veiligheidscontroles. U wordt aangeraden de status van alle beveiligingscontroles te controleren voordat u live gaat met uw productieexemplaar. Raadpleeg voor meer informatie de [documentatie van het dashboard Bewerkingen](/help/sites-administering/operations-dashboard.md).

### Controleren of voorbeeldinhoud aanwezig is {#check-if-example-content-is-present}

Alle voorbeeldinhoud en -gebruikers (bijvoorbeeld het Geometrixx-project en de onderdelen ervan) moeten worden verwijderd en volledig op een productiesysteem worden verwijderd voordat het openbaar toegankelijk wordt gemaakt.

>[!NOTE]
>
>De voorbeeldtoepassingen Web.Retail worden verwijderd als deze instantie wordt uitgevoerd in [Productie Ready Mode](/help/sites-administering/production-ready.md). Als, om het even welke reden, dit niet het geval is, kunt u de steekproefinhoud desinstalleren door naar de Manager van het Pakket te gaan, dan zoekend naar en desinstalleert alle pakketten Web.Retail. Zie [Werken met pakketten](package-manager.md) voor meer informatie.

### Controleren of de CRX-ontwikkelingsbundels aanwezig zijn {#check-if-the-crx-development-bundles-are-present}

Deze ontwikkelingsOSGi- bundels zouden op zowel auteur moeten worden gedesinstalleerd als productieve systemen publiceren alvorens hen toegankelijk te maken.

* Adobe CRXDE-ondersteuning (com.adobe.granite.crxde-support)
* Adobe Granite CRX Explorer (com.adobe.granite.crx-explorer)
* Adobe graniet CRXDE Lite (com.adobe.granite.crxde-lite)

### Controleren of de ontwikkelingsbundel voor splitsen aanwezig is {#check-if-the-sling-development-bundle-is-present}

De [AEM Developer Tools for Eclipse](/help/sites-developing/aem-eclipse.md) implementeert de Apache Sling Tooling Support Install (org.apache.sling.tooling.support.install).

Deze bundel OSGi zou op zowel auteur moeten worden gedesinstalleerd als productieve systemen publiceren alvorens hen toegankelijk te maken.

### Protect tegen XSS (cross-site request-vervalsing){#protect-against-cross-site-request-forgery}

#### Het CSRF-beschermingskader {#the-csrf-protection-framework}

AEM 6.1 schepen met een mechanisme dat hulp tegen de aanvallen van het Verzoek van de Vervalsing van de Vertoning van de Deposito&#39;s van de Deposito&#39;s beschermt, genoemd **CSRF Kader**. Raadpleeg de [documentatie](/help/sites-developing/csrf-protection.md) voor meer informatie over het gebruik ervan.

#### Het filter Verschuivende verwijzing {#the-sling-referrer-filter}

Als u bekende beveiligingsproblemen wilt verhelpen met CSRF-bestanden (Cross-Site Request Smeedery) in CRX WebDAV en Apache Sling, moet u configuraties toevoegen voor het filter Referrer om dit te kunnen gebruiken.

De dienst van de verwijzingsfilter is de dienst OSGi die u toestaat om te vormen:

* welke http-methoden moeten worden gefilterd
* Geeft aan of een lege verwijzingskoptekst is toegestaan
* en een lijst met servers die naast de serverhost zijn toegestaan.

   Standaard staan alle variaties van localhost en de huidige hostnamen waar de server aan gebonden is, in de lijst.

Om de dienst van het verwijzingsfilter te vormen:

1. Open de Apache Felix-console (**Configurations**) op:

   `https://<server>:<port_number>/system/console/configMgr`

1. Aanmelden als `admin`.
1. Selecteer in het menu **Configuraties**:

   `Apache Sling Referrer Filter`

1. Voer in het veld `Allow Hosts` alle hosts in die als referentie zijn toegestaan. Elk item moet van het formulier zijn

   &lt;protocol>://&lt;server>:&lt;port>

   Bijvoorbeeld:

   * `https://allowed.server:80` staat alle verzoeken van deze server met de bepaalde haven toe.
   * Als u ook https-aanvragen wilt toestaan, moet u een tweede regel invoeren.
   * Als u alle poorten van die server toestaat, kunt u `0` als poortnummer gebruiken.

1. Schakel het veld `Allow Empty` in als u lege/ontbrekende verwijzingskoppen wilt toestaan.

   >[!CAUTION]
   >
   >Men adviseert om een verwijzer te verstrekken terwijl het gebruiken van bevellijnhulpmiddelen zoals `cURL` in plaats van het toestaan van een lege waarde aangezien het uw systeem aan aanvallen CSRF zou kunnen blootstellen.

1. Bewerk de methoden die dit filter moet gebruiken voor controles met het veld `Filter Methods`.

1. Klik **Opslaan** om uw wijzigingen op te slaan.

### OSGI-instellingen {#osgi-settings}

Sommige instellingen van OSGI worden standaard ingesteld om foutopsporing in de toepassing te vergemakkelijken. U moet deze instellingen wijzigen in de publicatie- en auteurversie om te voorkomen dat er interne informatie naar het publiek lekt.

>[!NOTE]
>
>Alle onderstaande instellingen, met uitzondering van **Het Day CQ WCM Debug Filter** worden automatisch gedekt door de [Productie Ready Mode](/help/sites-administering/production-ready.md). Daarom raden we u aan alle instellingen te controleren voordat u uw instantie in een productieve omgeving implementeert.

Voor elk van de volgende services moeten de opgegeven instellingen worden gewijzigd:

* [Adobe Granite HTML Library Manager](/help/sites-deploying/osgi-configuration-settings.md#day-cq-html-library-manager):

   * Schakel **Minify** in (om CRLF- en spatietekens te verwijderen).
   * Schakel **Gzip** in (om bestanden in staat te stellen om te worden gecomprimeerd en geopend met één aanvraag).
   * uitschakelen **Foutopsporing**
   * **Timing** uitschakelen

* [CQ-foutopsporingsfilter](/help/sites-deploying/osgi-configuration-settings.md#day-cq-wcm-debug-filter) voor dag:

   * uitschakelen **Inschakelen**

* [Dag CQ WCM-filter](/help/sites-deploying/osgi-configuration-settings.md):

   * alleen bij publicatie **WCM-modus** instellen op &quot;uitgeschakeld&quot;

* [Apache Sling Java Script Handler](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-javascript-handler):

   * uitschakelen **Foutopsporingsinfo genereren**

* [Apache Sling JSP Script Handler](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-jsp-script-handler):

   * uitschakelen **Foutopsporingsinfo genereren**
   * uitschakelen **Toegewezen inhoud**

Zie [OSGi Configuration Settings](/help/sites-deploying/osgi-configuration-settings.md) voor meer informatie.

Wanneer het werken met AEM zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [Het vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

## Verdere lezingen {#further-readings}

### Aanvallen op DoS-aanvallen (Denial of Service) beperken {#mitigate-denial-of-service-dos-attacks}

Een ontkenning van de dienst (Dos) aanval is een poging om een computermiddel niet beschikbaar te maken aan zijn voorgenomen gebruikers. Dit wordt vaak gedaan door de bron te overbelasten; bijvoorbeeld:

* Met een vloed van verzoeken van een externe bron.
* Met een verzoek om meer informatie dan het systeem met succes kan leveren.

   Bijvoorbeeld een JSON-representatie van de gehele repository.

* Door een inhoudspagina met een onbeperkt aantal URL&#39;s aan te vragen, kan URL een handvat, sommige selecteurs, een uitbreiding, en een achtervoegsel omvatten - om het even welke kan worden gewijzigd.

   `.../en.html` kan bijvoorbeeld ook worden aangevraagd als:

   * `.../en.ExtensionDosAttack`
   * `.../en.SelectorDosAttack.html`
   * `.../en.html/SuffixDosAttack`

   Alle geldige variaties (bijvoorbeeld retourneren een `200`-reactie en zijn geconfigureerd om in cache te worden opgeslagen) worden in de cache opgeslagen door de verzender, wat uiteindelijk leidt tot een volledig bestandssysteem en geen service voor verdere verzoeken.

Er zijn veel punten van configuratie om dergelijke aanvallen te voorkomen, hier bespreken we alleen die welke rechtstreeks verband houden met AEM.

**Het vormen het Verkopen om Dos te verhinderen**

Sling is *inhoudcentric*. Dit betekent dat de verwerking wordt geconcentreerd op de inhoud aangezien elk (HTTP) verzoek op inhoud in de vorm van een middel JCR (een gegevensopslagplaats knoop) in kaart wordt gebracht:

* Het eerste doel is de bron (JCR-knooppunt) die de inhoud bevat.
* Ten tweede bevindt de renderer, of het script, zich in combinatie met bepaalde delen van de aanvraag (bijvoorbeeld kiezers en/of de extensie) op basis van de eigenschappen van de resource.

>[!NOTE]
>
>Dit wordt meer in detail behandeld onder [Verwerking van het Verzoek van het Verkopen](/help/sites-developing/the-basics.md#sling-request-processing).

Deze aanpak maakt Sling zeer krachtig en zeer flexibel, maar zoals altijd is het de flexibiliteit die zorgvuldig moet worden beheerd.

Om misbruik van DoS te helpen voorkomen, kunt u:

1. besturingselementen op toepassingsniveau opnemen; vanwege het aantal mogelijke variaties is een standaardconfiguratie niet haalbaar.

   In uw toepassing moet u:

   * Bedien de selecteurs in uw toepassing, zodat u *only* de expliciete selecteurs nodig dienen en `404` voor alle anderen terugkeren.
   * De uitvoer van een onbeperkt aantal inhoudsknooppunten voorkomen.

1. Controleer de configuratie van de standaardrenderers, die een probleemgebied kunnen zijn.

   * Met name de JSON-renderer die de boomstructuur op meerdere niveaus kan doorlopen.

      Bijvoorbeeld, het verzoek:

      `http://localhost:4502/.json`

      kan de hele opslagplaats in een JSON-representatie dumpen. Dit zou aanzienlijke serverproblemen veroorzaken. Daarom wordt bij Sling een limiet ingesteld voor het aantal maximale resultaten. Als u de diepte van de JSON-rendering wilt beperken, kunt u de waarde instellen voor:

      **JSON Max resultaten** (  `json.maximumresults`)

      in de configuratie voor [Apache Sling GET Servlet](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet). Wanneer deze limiet wordt overschreden, wordt de rendering samengevouwen. De standaardwaarde voor Verdelen binnen AEM is `200`.

   * Als preventieve maatregel maak de andere standaardrenderers (HTML, gewone tekst, XML) onbruikbaar. Opnieuw door [Apache Sling GET Servlet](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet) te vormen.
   >[!CAUTION]
   >
   >Schakel de JSON-renderer niet uit. Dit is vereist voor de normale werking van AEM.

1. Gebruik een firewall om toegang tot uw instantie te filteren.

   * Het gebruik van een firewall op besturingssysteemniveau is nodig om toegang tot punten van uw instantie te filteren die tot een Denial of Service-aanval kan leiden als deze niet is beveiligd.

**Matig tegen doS die door de Selecteurs van de Vorm wordt veroorzaakt**

>[!NOTE]
>
>Deze beperking moet alleen worden uitgevoerd op AEM omgevingen die geen Forms gebruiken.

Aangezien AEM geen uit de doosindexen voor `FormChooserServlet` verstrekt, zal het gebruiken van vormselecteurs in vragen een dure bewaarplaats traversal teweegbrengen, gewoonlijk het malen van de AEM instantie aan een halt. Formulierkiezers kunnen worden gedetecteerd door de aanwezigheid van het **&amp;ast;.form.&amp;ast;** tekenreeks in query&#39;s.

Volg onderstaande stappen om dit te beperken:

1. Ga naar de webconsole door uw browser naar *https://&lt;serveradres>:&lt;serverport>/system/console/configMgr* te verwijzen

1. Zoeken naar **Day CQ WCM Form Chooser Servlet**
1. Nadat u op de ingang klikt, maak **Geavanceerd Onderzoek vereisen** in het volgende venster onbruikbaar.

1. Klik **Opslaan**.

**Mitigate Against DoS Caused by Asset Download Servlet**

De standaard Server van de Download van Activa in AEM staat voor authentiek verklaarde gebruikers toe om willekeurig-grote, gezamenlijke downloadverzoeken uit te geven voor het creëren van ZIP dossiers van activa zichtbaar aan hen die de server en/of het netwerk kunnen overbelasten.

Om potentiële risico&#39;s van Dos te verlichten die door deze eigenschap worden veroorzaakt, `AssetDownloadServlet` OSGi component is door gebrek voor publiceer instanties op recentste AEM versies.

Als de installatie vereist dat de Asset Download Server is ingeschakeld, raadpleegt u [dit artikel](/help/assets/download-assets-from-aem.md) voor meer informatie.

### WebDAV {#disable-webdav} uitschakelen

WebDAV moet worden uitgeschakeld in zowel de auteur- als de publicatieomgeving. Dit kan worden gedaan door de aangewezen bundels te stoppen OSGi.

1. Verbind met **Felix Management Console** die op loopt:

   `https://<*host*>:<*port*>/system/console`

   Bijvoorbeeld `http://localhost:4503/system/console/bundles`.

1. Zoek in de lijst met bundels naar de bundel met de naam:

   `Apache Sling Simple WebDAV Access to repositories (org.apache.sling.jcr.webdav)`

1. Klik op de stopknop (in de kolom Handelingen) om deze bundel te stoppen.

1. Zoek in de lijst met bundels de bundel met de naam:

   `Apache Sling DavEx Access to repositories (org.apache.sling.jcr.davex)`

1. Klik op de stopknop om deze bundel te stoppen.

   >[!NOTE]
   >
   >AEM hoeft niet opnieuw te worden opgestart.

### Verifieer dat u geen Persoonlijk identificeerbare informatie in de Weg van het Huis van Gebruikers {#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path} openbaart

Het is belangrijk dat u uw gebruikers beschermt door ervoor te zorgen dat u geen persoonlijk identificeerbare informatie in het pad naar de thuislocatie van gebruikers in de opslagplaats beschikbaar maakt.

Sinds AEM 6.1, wordt de manier de gebruiker (ook als toestemmbaar bekend) knoopnamen van identiteitskaart opgeslagen met een nieuwe implementatie van de `AuthorizableNodeName` interface veranderd. De nieuwe interface zal niet meer de gebruiker - identiteitskaart in de knoopnaam blootstellen maar zal een willekeurige naam in plaats daarvan produceren.

Er hoeft geen configuratie te worden uitgevoerd om deze in te schakelen, aangezien dit nu de standaardmanier is om autoriseerbare id&#39;s in AEM te genereren.

Hoewel niet geadviseerd, kunt u het onbruikbaar maken voor het geval u de oude implementatie voor achterwaartse verenigbaarheid met uw bestaande toepassingen nodig hebt. Hiervoor moet u:

1. Ga naar de webconsole en verwijder het item** org.apache.jackrabbit.security.user.RandomAuthorizableNodeName** uit de eigenschap **requiredServicePids** in **Apache Jackrabbit Oak SecurityProvider**.

   U kunt de Leverancier van de Veiligheid van het Eak ook vinden door **org.apache.jackrabbit.oak.security.internal.SecurityProviderRegistration** PID in de configuraties te zoeken OSGi.

1. Verwijder de **Apache Jackrabbit Oak Random Authorizable Node Name** OSGi configuratie uit de Console van het Web.

   Voor gemakkelijkere raadpleging, merk op dat PID voor deze configuratie **org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName** is.

>[!NOTE]
>
>Raadpleeg de documentatie bij het eikel over [genereren van naam van machtigingsknooppunt](https://jackrabbit.apache.org/oak/docs/security/user/authorizablenodename.html) voor meer informatie.

### Klikjacking {#prevent-clickjacking} voorkomen

Om klikaanvallen te verhinderen adviseren wij dat u uw webserver vormt om `X-FRAME-OPTIONS` kopbal te verstrekken die aan `SAMEORIGIN` wordt geplaatst.

Voor meer [informatie over klikjacking gelieve te zien de plaats van OWASP](https://www.owasp.org/index.php/Clickjacking).

### Zorg ervoor u behoorlijk encryptiesleutels wanneer nodig {#make-sure-you-properly-replicate-encryption-keys-when-needed} dupliceert

Bepaalde AEM en verificatieschema&#39;s vereisen dat u de coderingssleutels in alle AEM kopieert.

Alvorens u dit doet, gelieve nota te nemen dat de zeer belangrijke replicatie verschillend tussen versies wordt gedaan omdat de manier waarin de sleutels tussen 6.3 en oudere versies worden opgeslagen verschillend is.

Zie hieronder voor meer informatie.

#### Replicatietoetsen voor AEM 6.3 {#replicating-keys-for-aem}

Terwijl in oudere versies de replicatietoetsen in de bewaarplaats werden opgeslagen, beginnend met AEM 6.3 worden zij opgeslagen op het filesystem.

Daarom moet u, om uw sleutels over instanties te repliceren, hen van de broninstantie aan de plaats van de doelinstanties op het filesystem kopiëren.

Meer specifiek, moet u:

1. Toegang krijgen tot de AEM instantie, doorgaans een instantie van de auteur, die het te kopiëren toetsmateriaal bevat.
1. Zoek de bundel com.adobe.granite.crypto.file in het lokale bestandssysteem. Onder dit pad bijvoorbeeld:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`

   In het `bundle.info`-bestand in elke map wordt de bundelnaam weergegeven.

1. Navigeer naar de gegevensmap. Bijvoorbeeld:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Kopieer de HMAC- en master bestanden.
1. Dan, ga naar de doelinstantie u de sleutel HMAC aan wilt dupliceren, en aan de gegevensomslag navigeren. Bijvoorbeeld:

   * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Plak de twee bestanden die u eerder hebt gekopieerd.
1. [Vernieuw de Crypto-](/help/communities/deploy-communities.md#refresh-the-granite-crypto-bundle) bundel als de doelinstantie al wordt uitgevoerd.
1. Herhaal de bovenstaande stappen voor alle gevallen waarin u de toets wilt repliceren.

>[!NOTE]
>
>U kunt terugkeren naar de methode van pre 6.3 om sleutels op te slaan door de hieronder parameter toe te voegen wanneer u eerst AEM installeert:
>
>`-Dcom.adobe.granite.crypto.file.disable=true`

#### Replicatietoetsen voor AEM 6.2 en oudere versies {#replicating-keys-for-aem-and-older-versions}

In AEM 6.2 en oudere versies worden de sleutels opgeslagen in de bewaarplaats onder de `/etc/key` knoop.

De geadviseerde manier om de sleutels over uw instanties veilig te herhalen is dit knooppunt slechts te herhalen. U kunt knooppunten selectief repliceren via CRXDE Lite:

1. Open CRXDE Lite door naar *https://&lt;serveradres> te gaan:4502/crx/de/index.jsp*
1. Selecteer de `/etc/key` knoop.
1. Ga naar **Replication** tabel.
1. Druk **Replication** knoop.

### Een penetratietest uitvoeren {#perform-a-penetration-test}

Adobe raadt u ten zeerste aan een penetratietest van uw AEM uit te voeren voordat u verdergaat met de productie.

### Aanbevolen werkwijzen voor ontwikkeling {#development-best-practices}

Het is essentieel dat de nieuwe ontwikkeling [Beste praktijken van de Veiligheid ](/help/sites-developing/security.md) volgt om uw AEM milieu te verzekeren blijft veilig.
