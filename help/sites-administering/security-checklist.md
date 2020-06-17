---
title: Beveiligingscontrolelijst
seo-title: Beveiligingscontrolelijst
description: Lees meer over de verschillende beveiligingsoverwegingen bij het configureren en implementeren van AEM.
seo-description: Lees meer over de verschillende beveiligingsoverwegingen bij het configureren en implementeren van AEM.
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

Deze sectie behandelt diverse stappen die u zou moeten nemen om ervoor te zorgen dat uw installatie AEM wanneer opgesteld veilig is. De controlelijst moet van boven naar beneden worden toegepast.

>[!NOTE]
>
>De verdere informatie [is ook beschikbaar over de gevaarlijkste veiligheidsbedreigingen zoals gepubliceerd door Open Project van de Veiligheid van de Toepassing van het Web (OWASP)](https://www.owasp.org/index.php/OWASP_Top_Ten_Project).

>[!NOTE]
>
>Er zijn enkele aanvullende [veiligheidsoverwegingen](/help/sites-developing/dev-guidelines-bestpractices.md#security-considerations) van toepassing op de ontwikkelingsfase.

## Belangrijkste veiligheidsmaatregelen {#main-security-measures}

### AEM uitvoeren in productiekeuze modus {#run-aem-in-production-ready-mode}

Voor meer informatie, zie het [Lopen AEM in Productie Klaar Wijze](/help/sites-administering/production-ready.md).

### HTTPS inschakelen voor beveiliging van transportlagen {#enable-https-for-transport-layer-security}

Het inschakelen van de HTTPS-transportlaag op zowel auteur- als publicatieinstanties is verplicht voor het hebben van een beveiligde instantie.

>[!NOTE]
>
>Zie de sectie HTTP [inschakelen via SSL](/help/sites-administering/ssl-by-default.md) voor meer informatie.

### Beveiligingshotfixes installeren {#install-security-hotfixes}

Controleer of u de nieuwste [beveiligingshotfixes van Adobe](https://helpx.adobe.com/experience-manager/kb/aem63-available-hotfixes.html)hebt geïnstalleerd.

### Standaardwachtwoorden voor AEM- en OSGi-console-beheeraccounts wijzigen {#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts}

Adobe raadt u ten zeerste aan om na de installatie het wachtwoord voor de geprivilegieerde [**AEM **-`admin`accounts](#changing-the-aem-admin-password)te wijzigen (in alle gevallen).

Deze rekeningen omvatten:

* De AEM- `admin` account

   Nadat u het wachtwoord voor de AEM-beheerdersaccount hebt gewijzigd, moet u het nieuwe wachtwoord gebruiken om toegang te krijgen tot CRX.

* Het `admin` wachtwoord voor de console van het Web OSGi

   Deze verandering zal ook op de admin rekening worden toegepast die voor de toegang tot van de console van het Web wordt gebruikt, zodat zult u het zelfde wachtwoord moeten gebruiken wanneer de toegang tot van dat.

Deze twee rekeningen gebruiken afzonderlijke geloofsbrieven en het hebben van verschillend, sterk wachtwoord voor elk is essentieel voor een veilige plaatsing.

#### Het AEM-beheerwachtwoord wijzigen {#changing-the-aem-admin-password}

Het wachtwoord voor de AEM-beheerdersaccount kan worden gewijzigd via de [Granite Operations - Users](/help/sites-administering/granite-user-group-admin.md) console.

Hier kunt u het `admin` account bewerken en het wachtwoord [](/help/sites-administering/granite-user-group-admin.md#changing-the-password-for-an-existing-user)wijzigen.

>[!NOTE]
>
>Als u de beheerdersaccount wijzigt, wordt ook de OSGi-webconsoleversie gewijzigd. Nadat u de beheerdersaccount hebt gewijzigd, moet u de OSGi-account wijzigen in iets anders.

#### Het belang van het wijzigen van het wachtwoord voor de OSGi-webconsole {#importance-of-changing-the-osgi-web-console-password}

Naast de AEM- `admin` account kan het niet wijzigen van het standaardwachtwoord voor de OSGi-webconsole leiden tot:

* Belichting van de server met een standaardwachtwoord tijdens opstarten en afsluiten (wat minuten kan duren voor grote servers);
* Belichting van de server wanneer de opslagplaats is neer/herstart bundel - en OSGI loopt.

Voor meer informatie bij het veranderen van het wachtwoord van de Webconsole, zie het [Veranderend het OSGi wachtwoord](/help/sites-administering/security-checklist.md#changing-the-osgi-web-console-admin-password) van het Webconsole admin hieronder.

#### Het beheerwachtwoord voor de OSGi-webconsole wijzigen {#changing-the-osgi-web-console-admin-password}

U moet het wachtwoord ook veranderen dat voor de toegang tot van de console van het Web wordt gebruikt. Dit wordt gedaan door de volgende eigenschappen van de Console [van het Beheer van](/help/sites-deploying/osgi-configuration-settings.md)Apache Felix OSGi te vormen:

**Gebruikersnaam** en **wachtwoord**, de referenties voor toegang tot de Apache Felix Web Management Console zelf.
Het wachtwoord moet na de eerste installatie worden gewijzigd om de beveiliging van uw exemplaar te garanderen.

Dit doet u als volgt:

1. Navigeer naar de webconsole op `<server>:<port>/system/console/configMgr`.
1. Navigeer naar **Apache Felix OSGi Management Console** en wijzig de **gebruikersnaam** en het **wachtwoord**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Click **Save**.

### Aangepaste fouthandler implementeren {#implement-custom-error-handler}

Adobe raadt u aan aangepaste pagina&#39;s voor fouthandlers te definiëren, met name voor 404- en 500 HTTP-responscodes, om openbaarmaking van informatie te voorkomen.

>[!NOTE]
>
>Zie [hoe ik douanemanuscripten of foutenhandlers](https://helpx.adobe.com/experience-manager/kb/CustomErrorHandling.html) kennisbasisartikel voor meer details kan tot stand brengen.

### Dispatcher-beveiligingscontrolelijst voltooien {#complete-dispatcher-security-checklist}

AEM Dispatcher is een essentieel onderdeel van uw infrastructuur. Adobe raadt u ten zeerste aan de [beveiligingscontrolelijst](https://helpx.adobe.com/experience-manager/dispatcher/using/security-checklist.html)van de verzender in te vullen.

>[!CAUTION]
>
>Met de Dispatcher moet u de kiezer &quot;.form&quot; uitschakelen.

## Controlestappen {#verification-steps}

### Gebruikers voor replicatie en transport configureren {#configure-replication-and-transport-users}

Een standaardinstallatie van AEM specificeert `admin` als gebruiker voor vervoergeloofsbrieven binnen de standaardreplicatieagenten [](/help/sites-deploying/replication.md). Ook, wordt de admin gebruiker gebruikt aan bron de replicatie op het auteurssysteem.

Met het oog op de veiligheid moeten beide aspecten worden gewijzigd om rekening te houden met het specifieke gebruiksgeval in kwestie, waarbij de volgende twee aspecten in acht moeten worden genomen:

* De **vervoergebruiker** zou niet de admin gebruiker moeten zijn. Stel in plaats daarvan een gebruiker in het publicatiesysteem in die alleen toegangsrechten heeft tot de relevante delen van het publicatiesysteem en gebruik de referenties van die gebruiker voor het vervoer.

   U kunt van de gebundelde replicatie-ontvanger gebruiker beginnen en de toegangsrechten van deze gebruiker vormen om uw situatie aan te passen

* De **replicatiegebruiker** of Gebruiker - identiteitskaart **van de** Agent zou niet de admin gebruiker moeten zijn, maar een gebruiker die slechts inhoud kan zien die verondersteld wordt te worden herhaald. De replicatiegebruiker wordt gebruikt om de inhoud te verzamelen die op het auteurssysteem moet worden herhaald alvorens het naar de uitgever wordt verzonden.

### Controleer de beveiligingscontroles op het dashboard Bewerkingen {#check-the-operations-dashboard-security-health-checks}

AEM 6 introduceert het nieuwe Dashboard van Verrichtingen, die op het helpen van systeemexploitanten problemen oplossen en de gezondheid van een geval controleren.

Het dashboard bevat ook een verzameling veiligheidscontroles. U wordt aangeraden de status van alle beveiligingscontroles te controleren voordat u live gaat met uw productieexemplaar. Raadpleeg de documentatie [van het](/help/sites-administering/operations-dashboard.md)vluchthandboek voor meer informatie.

### Controleren of voorbeeldinhoud aanwezig is {#check-if-example-content-is-present}

Alle voorbeeldinhoud en -gebruikers (bijvoorbeeld het Geometrixx-project en de onderdelen ervan) moeten worden verwijderd en volledig op een productiesysteem worden verwijderd voordat het openbaar toegankelijk wordt gemaakt.

>[!NOTE]
>
>De steekproefWij.Retail toepassingen worden verwijderd als deze instantie in de Klaar Wijze [van de](/help/sites-administering/production-ready.md)Productie loopt. Als, om het even welke reden, dit niet het geval is, kunt u de steekproefinhoud desinstalleren door naar de Manager van het Pakket te gaan, dan zoekend naar en desinstalleert alle pakketten Web.Retail. Zie [Werken met pakketten](package-manager.md)voor meer informatie.

### Controleren of de CRX-ontwikkelingsbundels aanwezig zijn {#check-if-the-crx-development-bundles-are-present}

Deze ontwikkelingsOSGi- bundels zouden op zowel auteur moeten worden gedesinstalleerd als productieve systemen publiceren alvorens hen toegankelijk te maken.

* Adobe CRXDE-ondersteuning (com.adobe.granite.crxde-support)
* Adobe Granite CRX Explorer (com.adobe.granite.crx-explorer)
* Adobe Granite CRXDE Lite (com.adobe.granite.crxde-lite)

### Controleren of de ontwikkelingsbundel Sling aanwezig is {#check-if-the-sling-development-bundle-is-present}

De [AEM Developer Tools for Eclipse](/help/sites-developing/aem-eclipse.md) implementeert de Apache Sling Tooling Support Install (org.apache.sling.tooling.support.install).

Deze bundel OSGi zou op zowel auteur moeten worden gedesinstalleerd als productieve systemen publiceren alvorens hen toegankelijk te maken.

### Beschermen tegen Smeeuw voor aanvragen voor meerdere sites {#protect-against-cross-site-request-forgery}

#### Het CSRF-beschermingskader {#the-csrf-protection-framework}

AEM 6.1 schepen met een mechanisme dat hulp tegen de aanvallen van de Vervalsing van het Verzoek van de Deposito&#39;s van de Departement beschermt, genoemd het **Kader** van de Bescherming CSRF. Raadpleeg de [documentatie](/help/sites-developing/csrf-protection.md)voor meer informatie over het gebruik ervan.

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
1. Selecteer in het menu **Configuraties** :

   `Apache Sling Referrer Filter`

1. Voer in het `Allow Hosts` veld alle hosts in die als referentie zijn toegestaan. Elk item moet van het formulier zijn

   &lt;protocol>://&lt;server>:&lt;poort>

   Bijvoorbeeld:

   * `https://allowed.server:80` staat alle verzoeken van deze server met de bepaalde haven toe.
   * Als u ook https-aanvragen wilt toestaan, moet u een tweede regel invoeren.
   * Als u alle poorten van die server toestaat, kunt u `0` als poortnummer gebruiken.

1. Schakel het `Allow Empty` veld in als u lege of ontbrekende verwijzingskoppen wilt toestaan.

   >[!CAUTION]
   >
   >Men adviseert om een verwijzer te verstrekken terwijl het gebruiken van bevellijnhulpmiddelen zoals `cURL` in plaats van het toestaan van een lege waarde aangezien het uw systeem aan aanvallen CSRF zou kunnen blootstellen.

1. Bewerk de methoden die dit filter moet gebruiken voor controles met het `Filter Methods` veld.

1. Klik op **Opslaan** om de wijzigingen op te slaan.

### OSGI-instellingen {#osgi-settings}

Sommige instellingen van OSGI worden standaard ingesteld om foutopsporing in de toepassing te vergemakkelijken. U moet deze instellingen wijzigen in de publicatie- en auteurversie om te voorkomen dat er interne informatie naar het publiek lekt.

>[!NOTE]
>
>Alle onderstaande instellingen, met uitzondering van **het dagfilter** voor foutopsporing in CQ (WCM-debug), worden automatisch gedekt door de [productielocatie](/help/sites-administering/production-ready.md). Daarom raden we u aan alle instellingen te controleren voordat u uw instantie in een productieve omgeving implementeert.

Voor elk van de volgende services moeten de opgegeven instellingen worden gewijzigd:

* [Adobe Granite HTML Library Manager](/help/sites-deploying/osgi-configuration-settings.md#day-cq-html-library-manager):

   * Schakel **Minify** in (om CRLF- en whitespace-tekens te verwijderen).
   * Schakel **Gzip** in (als u wilt dat bestanden met één aanvraag kunnen worden gecomprimeerd en geopend).
   * debug **uitschakelen**
   * uitschakelen **Timing**

* [CQ-foutopsporingsfilter](/help/sites-deploying/osgi-configuration-settings.md#day-cq-wcm-debug-filter)voor dag:

   * uitschakelen **Inschakelen**

* [Dag CQ WCM-filter](/help/sites-deploying/osgi-configuration-settings.md):

   * alleen bij publiceren, stelt u de **WCM-modus** in op &quot;uitgeschakeld&quot;

* [Apache Sling Java Script Handler](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-javascript-handler):

   * uitschakelen **Foutopsporingsinfo genereren**

* [Apache Sling JSP Script Handler](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-jsp-script-handler):

   * uitschakelen **Foutopsporingsinfo genereren**
   * toegewezen **inhoud uitschakelen**

Voor verdere details zie de Montages [van de Configuratie](/help/sites-deploying/osgi-configuration-settings.md)OSGi.

Wanneer het werken met AEM zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie het [Vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

## Verdere lezingen {#further-readings}

### Aanvallen van Denial of Service (DoS) beperken {#mitigate-denial-of-service-dos-attacks}

Een ontkenning van de dienst (Dos) aanval is een poging om een computermiddel niet beschikbaar te maken aan zijn voorgenomen gebruikers. Dit wordt vaak gedaan door de bron te overbelasten; bijvoorbeeld:

* Met een vloed van verzoeken van een externe bron.
* Met een verzoek om meer informatie dan het systeem met succes kan leveren.

   Bijvoorbeeld een JSON-representatie van de gehele repository.

* Door een inhoudspagina met een onbeperkt aantal URL&#39;s aan te vragen, kan URL een handvat, sommige selecteurs, een uitbreiding, en een achtervoegsel omvatten - om het even welke kan worden gewijzigd.

   U kunt bijvoorbeeld `.../en.html` ook het volgende aanvragen:

   * `.../en.ExtensionDosAttack`
   * `.../en.SelectorDosAttack.html`
   * `.../en.html/SuffixDosAttack`
   Alle geldige variaties (bijvoorbeeld retourneren een `200` reactie en zijn geconfigureerd om in cache te worden opgeslagen) worden in de cache opgeslagen door de verzender, wat uiteindelijk leidt tot een volledig bestandssysteem en geen service voor verdere verzoeken.

Er zijn veel punten van configuratie om dergelijke aanvallen te voorkomen, hier bespreken we alleen die welke rechtstreeks verband houden met AEM.

**Het vormen het Verkopen om Dos te verhinderen**

Sling is *inhoudcentrisch*. Dit betekent dat de verwerking wordt geconcentreerd op de inhoud aangezien elk (HTTP) verzoek op inhoud in de vorm van een middel JCR (een gegevensopslagplaats knoop) in kaart wordt gebracht:

* Het eerste doel is de bron (JCR-knooppunt) die de inhoud bevat.
* Ten tweede bevindt de renderer, of het script, zich in combinatie met bepaalde delen van de aanvraag (bijvoorbeeld kiezers en/of de extensie) op basis van de eigenschappen van de resource.

>[!NOTE]
>
>Dit wordt meer in detail besproken onder [Verwerking](/help/sites-developing/the-basics.md#sling-request-processing)verkoopaanvraag.

Deze aanpak maakt Sling zeer krachtig en zeer flexibel, maar zoals altijd is het de flexibiliteit die zorgvuldig moet worden beheerd.

Om misbruik van DoS te helpen voorkomen, kunt u:

1. besturingselementen op toepassingsniveau opnemen; vanwege het aantal mogelijke variaties is een standaardconfiguratie niet haalbaar.

   In uw toepassing moet u:

   * Controleer de kiezers in de toepassing, zodat u *alleen* de vereiste expliciete kiezers kunt bedienen en `404` voor alle anderen kunt retourneren.
   * De uitvoer van een onbeperkt aantal inhoudsknooppunten voorkomen.

1. Controleer de configuratie van de standaardrenderers, die een probleemgebied kunnen zijn.

   * Met name de JSON-renderer die de boomstructuur op meerdere niveaus kan doorlopen.

      Bijvoorbeeld, het verzoek:

      `http://localhost:4502/.json`

      kan de hele opslagplaats in een JSON-representatie dumpen. Dit zou aanzienlijke serverproblemen veroorzaken. Daarom wordt bij Sling een limiet ingesteld voor het aantal maximale resultaten. Als u de diepte van de JSON-rendering wilt beperken, kunt u de waarde instellen voor:

      **JSON Max-resultaten** ( `json.maximumresults`)

      in de configuratie voor [Apache Sling GET Servlet](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet). Wanneer deze limiet wordt overschreden, wordt de rendering samengevouwen. De standaardwaarde voor Verkopen binnen AEM is `200`.

   * Als preventieve maatregel maak de andere standaardrenderers (HTML, gewone tekst, XML) onbruikbaar. Opnieuw door de [Apache Sling GET Servlet](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet)te configureren.
   >[!CAUTION]
   >
   >Schakel de JSON-renderer niet uit. Dit is vereist voor de normale werking van AEM.

1. Gebruik een firewall om toegang tot uw instantie te filteren.

   * Het gebruik van een firewall op besturingssysteemniveau is nodig om toegang tot punten van uw instantie te filteren die tot een Denial of Service-aanval kan leiden als deze niet is beveiligd.

**Matig tegen doS die door de Selecteurs van de Vorm wordt veroorzaakt**

>[!NOTE]
>
>Deze beperking moet alleen worden uitgevoerd op AEM-omgevingen die geen Forms gebruiken.

Aangezien AEM geen uit de doosindexen voor de `FormChooserServlet`verstrekt, zal het gebruiken van vormselecteurs in vragen een dure bewaarplaats traversal teweegbrengen, gewoonlijk die de instantie AEM aan een halt malen. Formulierkiezers kunnen worden gedetecteerd door de aanwezigheid van het **&amp;ast;.form.&amp;ast;** tekenreeks in query&#39;s.

Volg onderstaande stappen om dit te beperken:

1. Ga naar de webconsole door uw browser naar *https://&lt;serveradres>:&lt;serverport>/system/console/configMgr te verwijzen*

1. Zoeken naar **dag CQ WCM-formulierkiezer**
1. Nadat u op de ingang klikt, maak **Geavanceerd Onderzoek vereisen** in het volgende venster onbruikbaar.

1. Click **Save**.

**Mitigate Against DoS Caused by Asset Download Servlet**

Met de standaard Asset Download Server in AEM kunnen geverifieerde gebruikers willekeurig grote, gelijktijdige downloadaanvragen afgeven voor het maken van ZIP-bestanden met middelen die zichtbaar zijn voor hen en die de server en/of het netwerk kunnen overbelasten.

Om potentiële risico&#39;s van Dos te verlichten die door deze eigenschap worden veroorzaakt, is de component `AssetDownloadServlet` OSGi gehandicapt door gebrek voor publiceer instanties op recentste versies AEM.

Als de installatie vereist dat de Asset Download Server is ingeschakeld, raadpleegt u [dit artikel](/help/assets/download-assets-from-aem.md) voor meer informatie.

### WebDAV uitschakelen {#disable-webdav}

WebDAV moet worden uitgeschakeld in zowel de auteur- als de publicatieomgeving. Dit kan worden gedaan door de aangewezen bundels te stoppen OSGi.

1. Verbinding maken met de **Felix Management Console** die wordt uitgevoerd op:

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

### Verifieer dat u geen Persoonlijk identificeerbare informatie in de Weg van het Huis van Gebruikers openbaart {#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path}

Het is belangrijk dat u uw gebruikers beschermt door ervoor te zorgen dat u geen persoonlijk identificeerbare informatie in het pad naar de thuislocatie van gebruikers in de opslagplaats beschikbaar maakt.

Sinds AEM 6.1, wordt de manier de knoopnamen van de gebruiker (die ook als toestemmbaar wordt bekend) identiteitskaart worden opgeslagen veranderd met een nieuwe implementatie van de `AuthorizableNodeName` interface. De nieuwe interface zal niet meer de gebruiker - identiteitskaart in de knoopnaam blootstellen maar zal een willekeurige naam in plaats daarvan produceren.

Er hoeft geen configuratie te worden uitgevoerd om deze in te schakelen, aangezien dit nu de standaardmanier is om autoriseerbare id&#39;s te genereren in AEM.

Hoewel niet geadviseerd, kunt u het onbruikbaar maken voor het geval u de oude implementatie voor achterwaartse verenigbaarheid met uw bestaande toepassingen nodig hebt. Hiervoor moet u:

1. Ga naar de Console van het Web en verwijder de** org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName** ingang van bezit **requiredServicePids** in **Apache Jackrabbit Oak SecurityProvider**.

   U kunt de Leverancier van de Veiligheid van het Eak ook vinden door **org.apache.jackrabbit.oak.security.internal.SecurityProviderRegistration** PID in de configuraties OSGi te zoeken.

1. Verwijder de **Apache Jackrabbit Oak Random Authorizable Node Name** OSGi-configuratie uit de webconsole.

   Voor gemakkelijkere raadpleging, merk op dat PID voor deze configuratie **org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName** is.

>[!NOTE]
>
>Zie de documentatie van het eikel over het genereren van [toegestane knooppuntnamen voor meer informatie](https://jackrabbit.apache.org/oak/docs/security/user/authorizablenodename.html).

### Klikaanvallen voorkomen {#prevent-clickjacking}

Om klikaanvallen te verhinderen adviseren wij dat u uw webserver vormt om de kopbal te verstrekken van `X-FRAME-OPTIONS` HTTP die aan wordt geplaatst `SAMEORIGIN`.

Raadpleeg de OWASP-site voor meer [informatie over het aanklikken op een bestand](https://www.owasp.org/index.php/Clickjacking).

### Zorg ervoor dat u de coderingstoetsen op de juiste wijze dupliceert als dat nodig is {#make-sure-you-properly-replicate-encryption-keys-when-needed}

Bepaalde AEM-functies en verificatieschema&#39;s vereisen dat u de coderingssleutels in alle AEM-instanties dupliceert.

Alvorens u dit doet, gelieve nota te nemen dat de zeer belangrijke replicatie verschillend tussen versies wordt gedaan omdat de manier waarin de sleutels tussen 6.3 en oudere versies worden opgeslagen verschillend is.

Zie hieronder voor meer informatie.

#### Replicatietoetsen voor AEM 6.3 {#replicating-keys-for-aem}

Terwijl in oudere versies de replicatietoetsen in de bewaarplaats werden opgeslagen, beginnend met AEM 6.3 worden zij opgeslagen op het filesystem.

Daarom moet u, om uw sleutels over instanties te repliceren, hen van de broninstantie aan de plaats van de doelinstanties op het filesystem kopiëren.

Meer specifiek, moet u:

1. Toegang krijgen tot de AEM-instantie, doorgaans een instantie van de auteur, die het te kopiëren toetsmateriaal bevat.
1. Zoek de bundel com.adobe.granite.crypto.file in het lokale bestandssysteem. Onder dit pad bijvoorbeeld:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`
   Het `bundle.info` bestand in elke map geeft de naam van de bundel aan.

1. Navigeer naar de gegevensmap. Bijvoorbeeld:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Kopieer de HMAC- en hoofdbestanden.
1. Dan, ga naar de doelinstantie u de sleutel HMAC aan wilt dupliceren, en aan de gegevensomslag navigeren. Bijvoorbeeld:

   * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Plak de twee bestanden die u eerder hebt gekopieerd.
1. [Vernieuw de Crypto Bundle](/help/communities/deploy-communities.md#refresh-the-granite-crypto-bundle) als de doelinstantie reeds loopt.
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
1. Select the `/etc/key` node.
1. Ga naar het tabblad **Replicatie** .
1. Druk de knoop van de **Replicatie** .

### Een beveiligingstest uitvoeren {#perform-a-penetration-test}

Adobe raadt u ten zeerste aan een penetratietest van uw AEM-infrastructuur uit te voeren voordat u verdergaat met de productie.

### Aanbevolen werkwijzen voor ontwikkeling {#development-best-practices}

Het is essentieel dat de nieuwe ontwikkeling de Beste praktijken [van de](/help/sites-developing/security.md) Veiligheid volgt om uw milieu AEM veilig te verzekeren.
