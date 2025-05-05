---
title: Beveiligingscontrolelijst
description: Leer over de diverse veiligheidsoverwegingen wanneer het vormen en het opstellen van AEM.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
docset: aem65
exl-id: 314a6409-398c-470b-8799-0c4e6f745141
feature: Security
solution: Experience Manager, Experience Manager Sites
role: Admin,Developer
source-git-commit: f30decf0e32a520dcda04b89c5c1f5b67ab6e028
workflow-type: tm+mt
source-wordcount: '2959'
ht-degree: 0%

---

# Beveiligingscontrolelijst {#security-checklist}

Deze sectie behandelt diverse stappen die u zou moeten nemen om ervoor te zorgen dat uw AEM installatie wanneer opgesteld veilig is. De controlelijst moet van boven naar beneden worden toegepast.

>[!NOTE]
>
>De verdere informatie is ook beschikbaar over de gevaarlijkste veiligheidsbedreigingen zoals gepubliceerd door [ Open Project van de Veiligheid van de Toepassing van het Web (OWASP) ](https://owasp.org/www-project-top-ten/).

>[!NOTE]
>
>Er zijn sommige extra [ veiligheidsoverwegingen ](/help/sites-developing/dev-guidelines-bestpractices.md#security-considerations) toepasselijk bij de ontwikkelingsfase.

## Belangrijkste veiligheidsmaatregelen {#main-security-measures}

### AEM uitvoeren in de productielodus {#run-aem-in-production-ready-mode}

Voor meer informatie, zie [ lopende AEM in Productie Klaar Wijze ](/help/sites-administering/production-ready.md).

### HTTPS inschakelen voor beveiliging van transportlagen {#enable-https-for-transport-layer-security}

Het inschakelen van de HTTPS-transportlaag op zowel auteur- als publicatieinstanties is verplicht voor het hebben van een beveiligde instantie.

>[!NOTE]
>
>Zie [ toelatend HTTP over SSL ](/help/sites-administering/ssl-by-default.md) sectie voor meer informatie.

### Beveiligingshotfixes installeren {#install-security-hotfixes}

Zorg ervoor dat u recentste [ Hotfixes van de Veiligheid hebt geïnstalleerd die door Adobe ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html) wordt verstrekt.

### Standaardwachtwoorden voor de AEM- en OSGi-console-beheeraccounts wijzigen {#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts}

De Adobe adviseert na installatie dat u het wachtwoord voor de bevoorrechte [**AEM** `admin` rekeningen ](#changing-the-aem-admin-password) (op alle instanties) verandert.

Deze rekeningen omvatten:

* De AEM `admin` -account

  Nadat u het wachtwoord voor de AEM-beheerdersaccount hebt gewijzigd, gebruikt u het nieuwe wachtwoord om CRX te openen.

* Het `admin` wachtwoord voor de console van het Web OSGi

  Deze verandering wordt ook toegepast op de admin rekening die voor de toegang tot van de console van het Web wordt gebruikt, zo gebruik het zelfde wachtwoord wanneer de toegang tot van dat.

Deze twee rekeningen gebruiken afzonderlijke geloofsbrieven en het hebben van verschillend, sterk wachtwoord voor elk is essentieel voor een veilige plaatsing.

#### Het AEM-beheerderswachtwoord wijzigen {#changing-the-aem-admin-password}

Het wachtwoord voor de AEM admin rekening kan via de [ Verrichtingen van de Granite - Gebruikers ](/help/sites-administering/granite-user-group-admin.md) console worden veranderd.

Hier kunt u de `admin` rekening uitgeven en [ veranderen het wachtwoord ](/help/sites-administering/granite-user-group-admin.md#changing-the-password-for-an-existing-user).

>[!NOTE]
>
>Als u de beheerdersaccount wijzigt, wordt ook de OSGi-webconsoleversie gewijzigd. Nadat u de beheerdersaccount hebt gewijzigd, moet u de OSGi-account wijzigen in iets anders.

#### Het belang van het wijzigen van het wachtwoord voor de OSGi-webconsole {#importance-of-changing-the-osgi-web-console-password}

Naast de AEM `admin` -account kan het niet wijzigen van het standaardwachtwoord voor de OSGi-webconsole leiden tot:

* Belichting van de server met een standaardwachtwoord tijdens opstarten en afsluiten (wat minuten kan duren voor grote servers);
* Belichting van de server wanneer de opslagplaats is neer/herstart bundel - en OSGI loopt.

Voor meer informatie bij het veranderen van het wachtwoord van de Webconsole, zie [ Veranderend het OSGi wachtwoord van het Webconsole admin ](/help/sites-administering/security-checklist.md#changing-the-osgi-web-console-admin-password) hieronder.

#### Het beheerwachtwoord voor de OSGi-webconsole wijzigen {#changing-the-osgi-web-console-admin-password}

Wijzig het wachtwoord dat wordt gebruikt voor toegang tot de webconsole. Gebruik een [ configuratie OSGI ](/help/sites-deploying/configuring-osgi.md) om de volgende eigenschappen van de **Console van het Beheer van de Felix van Apache OSGi** bij te werken:

* **Naam van de Gebruiker** en **Wachtwoord**, de geloofsbrieven voor de toegang tot van de Console van het Beheer van het Web van de Felix van Apache zelf.
Het wachtwoord moet *na* de aanvankelijke installatie worden veranderd om de veiligheid van uw instantie te verzekeren.

>[!NOTE]
>
>Zie [ configuratie OSGI ](/help/sites-deploying/configuring-osgi.md) voor volledige details van het vormen van montages OSGi.

**om het OSGi wachtwoord van het Webconsole te veranderen admin**:

1. Gebruikend de **Hulpmiddelen**, **Verrichtingen** menu, open de **Console van het Web** en navigeer aan de **sectie van de Configuratie**.
Bijvoorbeeld bij `<server>:<port>/system/console/configMgr` .
1. Navigeer aan, en open, de ingang voor **Apache Felix OSGi de Console van het Beheer**.
1. Verander de **gebruikersnaam** en **wachtwoord**.

   ![ chlimage_1-3 ](assets/chlimage_1-3.png)

1. Selecteer **sparen**.

### Aangepaste fouthandler implementeren {#implement-custom-error-handler}

Adobe raadt aan aangepaste fouthandlerpagina&#39;s te definiëren, met name voor 404- en 500 HTTP-antwoordcodes, om openbaarmaking van informatie te voorkomen.

>[!NOTE]
>
>Zie [ hoe ik douanemanuscripten of foutenmanagers ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/full-stack/custom-error-page.html) voor meer details kan tot stand brengen.

### Dispatcher-beveiligingscontrolelijst voltooien {#complete-dispatcher-security-checklist}

AEM Dispatcher is een essentieel onderdeel van uw infrastructuur. De Adobe adviseert dat u de [ veiligheid checklist van Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/security-checklist.html) voltooit.

>[!CAUTION]
>
>Met de Dispatcher moet u de kiezer &quot;.form&quot; uitschakelen.

## Controlestappen {#verification-steps}

### Gebruikers voor replicatie en transport configureren {#configure-replication-and-transport-users}

Een standaardinstallatie van AEM specificeert `admin` als gebruiker voor vervoergeloofsbrieven binnen de standaard [ replicatieagenten ](/help/sites-deploying/replication.md). Ook, wordt de admin gebruiker gebruikt aan bron de replicatie op het auteurssysteem.

Met het oog op de veiligheid moeten beide aspecten worden gewijzigd om rekening te houden met het specifieke gebruiksgeval in kwestie, waarbij de volgende twee aspecten in acht moeten worden genomen:

* De **vervoergebruiker** moet niet de admingebruiker zijn. Stel in plaats daarvan een gebruiker in het publicatiesysteem in die alleen toegangsrechten heeft tot de relevante delen van het publicatiesysteem en gebruik de referenties van die gebruiker voor het vervoer.

  U kunt van de gebundelde replicatie-ontvanger gebruiker beginnen en de toegangsrechten van deze gebruiker vormen om uw situatie aan te passen

* De **replicatiegebruiker** of **Gebruiker - identiteitskaart van de Agent** moet ook niet de admin gebruiker zijn, maar een gebruiker die slechts inhoud kan zien die wordt herhaald. De replicatiegebruiker wordt gebruikt om de inhoud te verzamelen die op het auteurssysteem moet worden herhaald alvorens het naar de uitgever wordt verzonden.

### Controleer de beveiligingscontroles op het dashboard Bewerkingen {#check-the-operations-dashboard-security-health-checks}

AEM 6 introduceert het nieuwe Dashboard van Verrichtingen, dat op het helpen van systeemexploitanten problemen oplossen en de gezondheid van een geval controleert.

Het dashboard bevat ook een verzameling veiligheidscontroles. U wordt aangeraden de status van alle beveiligingscontroles te controleren voordat u live gaat met uw productieexemplaar. Voor meer informatie, raadpleeg de [ documentatie van het Dashboard van Verrichtingen ](/help/sites-administering/operations-dashboard.md).

### Controleren of voorbeeldinhoud aanwezig is {#check-if-example-content-is-present}

Alle voorbeeldinhoud en -gebruikers (bijvoorbeeld het Geometrixx-project en de onderdelen ervan) moeten worden verwijderd en volledig op een productiesysteem worden verwijderd voordat het openbaar toegankelijk wordt gemaakt.

>[!NOTE]
>
>De steekproef `We.Retail` toepassingen worden verwijderd als deze instantie op [ Productie Klaar Wijze ](/help/sites-administering/production-ready.md) loopt. Als dit scenario niet het geval is, kunt u de steekproefinhoud desinstalleren door naar de Manager van het Pakket te gaan, dan zoekend, en desinstalleer, alle `We.Retail` pakketten.

Zie [ Werk met Pakketten ](package-manager.md).

### Controleren of de CRX-ontwikkelingsbundels aanwezig zijn {#check-if-the-crx-development-bundles-are-present}

Deze ontwikkelingsOSGi- bundels zouden op zowel auteur moeten worden gedesinstalleerd als productieve systemen publiceren alvorens hen toegankelijk te maken.

* Adobe CRXDE-ondersteuning (com.adobe.granite.crxde-support)
* Adobe Granite CRX Explorer (com.adobe.granite.crx-explorer)
* Graniet-CRXDE Lite Adobe (com.adobe.granite.crxde-lite)

### Controleren of de ontwikkelingsbundel Sling aanwezig is {#check-if-the-sling-development-bundle-is-present}

De [ AEM Hulpmiddelen van de Ontwikkelaar ](/help/sites-developing/aem-eclipse.md) stellen Apache die de Installatie van de Steun van de Tooling van de Tooling van de Tooling (org.apache.sling.tooling.support.install) opstelt.

Deze bundel OSGi zou op zowel auteur moeten worden gedesinstalleerd als productieve systemen publiceren alvorens hen toegankelijk te maken.

### Protect tegen XSS (cross-site request-vervalsing) {#protect-against-cross-site-request-forgery}

#### Het CSRF-beschermingskader {#the-csrf-protection-framework}

AEM 6.1 schepen met een mechanisme dat de hulp tegen de aanvallen van de Versmeding van het Verzoek van de Deposito&#39;s van de Deposito&#39;s beschermt, genoemd het **Kader van de Bescherming CSRF**. Voor meer informatie over hoe te om het te gebruiken, raadpleeg de [ documentatie ](/help/sites-developing/csrf-protection.md).

#### Het filter Verschuivende verwijzing {#the-sling-referrer-filter}

Als u bekende beveiligingsproblemen wilt verhelpen met CSRF-bestanden (Cross-Site Request Smeedery) in CRX WebDAV en Apache Sling, voegt u configuraties voor het filter Referrer toe om dit te gebruiken.

De dienst van de verwijzingsfilter is de dienst OSGi die u het volgende laat vormen:

* welke http-methoden moeten worden gefilterd
* of een lege verwijzingskoptekst is toegestaan
* en een lijst met servers die naast de serverhost zijn toegestaan.

  Standaard staan alle variaties van localhost en de huidige hostnamen waar de server aan gebonden is, in de lijst.

Om de dienst van het verwijzingsfilter te vormen:

1. Open de console van de Felix Apache (**Configuraties**) bij:

   `https://<server>:<port_number>/system/console/configMgr`

1. Meld u aan als `admin` .
1. In het **menu van Configuraties**, selecteer:

   `Apache Sling Referrer Filter`

1. Voer in het veld `Allow Hosts` alle hosts in die als referentie zijn toegestaan. Elke vermelding moet van het formulier zijn

   &lt;protocol>://&lt;server>:&lt;poort>

   Bijvoorbeeld:

   * `https://allowed.server:80` staat alle verzoeken van deze server met de bepaalde haven toe.
   * Als u ook https-aanvragen wilt toestaan, moet u een tweede regel invoeren.
   * Als u alle poorten van die server toestaat, kunt u `0` als poortnummer gebruiken.

1. Controleer het veld `Allow Empty` als u lege of ontbrekende verwijzingskoppen wilt toestaan.

   >[!CAUTION]
   >
   >De Adobe adviseert dat u een verwijzer terwijl het gebruiken van bevel-lijn hulpmiddelen zoals `cURL` verstrekt in plaats van een lege waarde toe te staan aangezien het uw systeem aan aanvallen CSRF zou kunnen blootstellen.

1. Bewerk de methoden die dit filter gebruikt voor controles met het veld `Filter Methods` .

1. Klik **sparen** om uw veranderingen te bewaren.

### OSGI-instellingen {#osgi-settings}

Sommige instellingen van OSGI worden standaard ingesteld om foutopsporing in de toepassing te vergemakkelijken. Wijzig dergelijke instellingen in de productieve exemplaren van uw publicatie en auteur om te voorkomen dat er interne informatie naar het publiek lekt.

>[!NOTE]
>
>Alle montages hieronder, behalve **de Dag CQ WCM zuivert filter**, worden automatisch behandeld door de [ Klaar Wijze van de Productie ](/help/sites-administering/production-ready.md). Als dusdanig, adviseert de Adobe dat u alle montages alvorens uw geval in een productieve milieu te opstellen controleert.

Voor elk van de volgende services moeten de opgegeven instellingen worden gewijzigd:

* [ de Manager van de Bibliotheek van de HTML van de Adobe Granite ](/help/sites-deploying/osgi-configuration-settings.md#day-cq-html-library-manager):

   * laat **toe Minify** (om CRLF en whitespace karakters te verwijderen).
   * laat **Gzip** toe (om dossiers toe te staan om met één verzoek worden gecomprimeerd en worden betreden).
   * maak **Debug** onbruikbaar
   * maak **Timing** onbruikbaar

* [ Dag CQ WCM zuivert filter ](/help/sites-deploying/osgi-configuration-settings.md#day-cq-wcm-debug-filter):

   * uncheck **laat** toe

* [ de Filter van CQ WCM van de Dag ](/help/sites-deploying/osgi-configuration-settings.md):

   * op publiceren slechts, plaats **Wijze WCM** aan &quot;gehandicapt&quot;

* [ Apache Sling JavaScript Handler ](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-javascript-handler):

   * maak **onbruikbaar produceren zuivert Info**

* [ Apache het Verdelen van JSP Manuscript Handler ](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-jsp-script-handler):

   * maak **onbruikbaar produceren zuivert Info**
   * maak **Toegewezen Inhoud** onbruikbaar

Zie [ de Montages van de Configuratie OSGi ](/help/sites-deploying/osgi-configuration-settings.md).

Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [ Vormend OSGi ](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

## Verdere lezingen {#further-readings}

### Aanvallen van Denial of Service (DoS) beperken {#mitigate-denial-of-service-dos-attacks}

Een ontkenning van de dienst (Dos) aanval is een poging om een computermiddel niet beschikbaar te maken aan zijn voorgenomen gebruikers. Deze aanval wordt vaak gedaan door het middel te overbelasten; bijvoorbeeld:

* Een stroom verzoeken van een externe bron.
* Een verzoek om meer informatie dan het systeem met succes kan leveren.

  Bijvoorbeeld een JSON-representatie van de gehele gegevensopslagruimte.

* Door een inhoudspagina met een onbeperkt aantal URL&#39;s aan te vragen, kan URL een handvat, sommige selecteurs, een uitbreiding, en een achtervoegsel omvatten - om het even welke kan worden gewijzigd.

  `.../en.html` kan bijvoorbeeld ook worden aangevraagd als:

   * `.../en.ExtensionDosAttack`
   * `.../en.SelectorDosAttack.html`
   * `.../en.html/SuffixDosAttack`

  Alle geldige variaties (retourneren bijvoorbeeld een `200` -reactie en zijn geconfigureerd om in cache te worden opgeslagen) worden in cache geplaatst door de Dispatcher, wat uiteindelijk leidt tot een volledig bestandssysteem en geen service voor verdere aanvragen.

Er zijn vele punten van configuratie om dergelijke aanvallen te voorkomen, maar alleen die punten die betrekking hebben op AEM worden hier besproken.

**Vormend het Verzenden om Dos** te verhinderen

Sling is *inhoud-centric*. De verwerking wordt geconcentreerd op de inhoud aangezien elk (HTTP) verzoek op inhoud in de vorm van een middel JCR (een gegevensopslagplaats knoop) in kaart wordt gebracht:

* Het eerste doel is de bron (JCR-knooppunt) die de inhoud bevat.
* Ten tweede bevindt de renderer, of het script, zich in de eigenschappen resource met bepaalde onderdelen van de aanvraag (bijvoorbeeld kiezers en/of de extensie).

Zie [ het Verwerking van het Verzoek van de Verzending ](/help/sites-developing/the-basics.md#sling-request-processing) voor meer informatie.

Deze aanpak maakt Sling krachtig en flexibel, maar zoals altijd is het de flexibiliteit die zorgvuldig moet worden beheerd.

Om misbruik van DosS te helpen voorkomen, kunt u het volgende doen:

1. Neem controles op het toepassingsniveau op. Vanwege het aantal mogelijke variaties is een standaardconfiguratie niet mogelijk.

   In uw toepassing moet u:

   * Controle de selecteurs in uw toepassing, zodat u *slechts* de expliciete selecteurs nodig dient en `404` voor alle anderen terugkeert.
   * De uitvoer van een onbeperkt aantal inhoudsknooppunten voorkomen.

1. Controleer de configuratie van de standaardrenderers, die een probleemgebied kunnen zijn.

   * Met name transformeert de JSON-renderer de boomstructuur over meerdere niveaus.

     Bijvoorbeeld, het verzoek:

     `http://localhost:4502/.json`

     kan de hele opslagplaats in een JSON-representatie dumpen, wat aanzienlijke serverproblemen kan veroorzaken. Daarom wordt bij Sling een limiet ingesteld voor het aantal maximale resultaten. Als u de diepte van de JSON-rendering wilt beperken, stelt u de waarde in voor het volgende:

     **JSON Max resultaten** ( `json.maximumresults`)

     in de configuratie voor [ Apache Sling GET Servlet ](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet). Wanneer deze limiet wordt overschreden, wordt de rendering samengevouwen. De standaardwaarde voor Verdelen binnen AEM is `1000` .

   * Als preventieve maatregel, zou u de andere standaardrenderers (HTML, gewone teksten, XML) moeten onbruikbaar maken. Opnieuw, door [ Apache Sling GET Servlet ](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet) te vormen.

   >[!CAUTION]
   >
   >Schakel de JSON-renderer niet uit omdat deze vereist is voor de normale werking van AEM.

1. Gebruik een firewall om toegang tot uw instantie te filteren.

   * Het gebruik van een firewall op besturingssysteemniveau is nodig om toegang tot punten van uw instantie te filteren die tot een Denial of Service-aanval kan leiden als deze niet is beveiligd.

**Mitigate tegen Dos die door de Kiezers van de Vorm wordt veroorzaakt te gebruiken**

>[!NOTE]
>
>Deze beperking moet alleen worden uitgevoerd op AEM omgevingen die geen Forms gebruiken.

Omdat AEM geen out-of-the-box indexen voor `FormChooserServlet` verstrekt, kan het gebruiken van vormselecteurs in vragen een dure bewaarplaats traversal teweegbrengen, die gewoonlijk de AEM instantie aan een halt malen. Formulierkiezers kunnen worden gedetecteerd door de aanwezigheid van het formulier **&ast;.form.&ast;** koord in vragen.

U kunt dit probleem verhelpen door de volgende stappen uit te voeren:

1. Ga naar de Console van het Web door uw browser aan *https://&lt;serveraddress> te richten:&lt;serverport>/system/console/configMgr*

1. Onderzoek naar **Server van de Chooser van de Vorm van CQ WCM**
1. Nadat u de ingang klikt, maak **Geavanceerd Onderzoek** in het volgende venster onbruikbaar.

1. Klik **sparen**.

**Mitigate tegen Dos die door Server van de Download van Activa wordt veroorzaakt**

Met de standaardserver voor het downloaden van middelen kunnen geverifieerde gebruikers willekeurig grote, gelijktijdige, downloadverzoeken afgeven om ZIP-bestanden met elementen te maken. Door grote ZIP-archieven te maken, kunnen de server en het netwerk worden overbelast. Om het potentiële DoS-risico (Denial of Service) dat door dit gedrag wordt veroorzaakt, te beperken, wordt de `AssetDownloadServlet` OSGi-component standaard uitgeschakeld in [!DNL Experience Manager] -publicatie-instantie. Deze is standaard ingeschakeld voor de [!DNL Experience Manager] -instantie.

Als u de downloadmogelijkheden niet nodig hebt, schakelt u de servlet uit bij het ontwerpen en publiceren van implementaties. Als uw opstelling vereist dat het vermogen van de activadownload wordt toegelaten, zie [ de activa van de Download van de Ervaring van de Adobe beheren ](/help/assets/download-assets-from-aem.md) voor meer informatie. Bovendien kunt u een maximale downloadlimiet definiëren die uw implementatie kan ondersteunen.

### WebDAV uitschakelen {#disable-webdav}

Schakel WebDAV op zowel auteur als publicatiemilieu&#39;s uit door de aangewezen bundels tegen te houden OSGi.

1. Verbind met de **Console van het Beheer van de Felix** lopend op:

   `https://<*host*>:<*port*>/system/console`

   Bijvoorbeeld `http://localhost:4503/system/console/bundles` .

1. Zoek in de lijst met bundels naar de bundel met de naam:

   `Apache Sling Simple WebDAV Access to repositories (org.apache.sling.jcr.webdav)`

1. Klik in de kolom Acties op de stopknop om deze bundel te stoppen.

1. Zoek in de lijst met bundels de bundel met de naam:

   `Apache Sling DavEx Access to repositories (org.apache.sling.jcr.davex)`

1. Klik op de stopknop om deze bundel te stoppen.

   >[!NOTE]
   >
   >AEM hoeft niet opnieuw te worden opgestart.

### Verifieer dat u geen Persoonlijk identificeerbare informatie in de Weg van het Huis van Gebruikers openbaart {#verify-that-you-are-not-disclosing-personally-identifiable-information-in-the-users-home-path}

Het is belangrijk om uw gebruikers te beschermen door ervoor te zorgen dat u geen persoonlijk identificeerbare informatie in de huisweg van de gebruikers van de bewaarplaats blootstelt.

Sinds AEM 6.1 wordt de manier waarop namen van gebruikerknooppunten (ook wel autoriseerbare id&#39;s genoemd) worden opgeslagen, gewijzigd met een nieuwe implementatie van de interface `AuthorizableNodeName` . De nieuwe interface stelt niet meer de gebruiker - identiteitskaart in de knoopnaam bloot maar produceert een willekeurige naam in plaats daarvan.

Geen configuratie moet worden uitgevoerd om het toe te laten, omdat het nu de standaardmanier is om toegelaten IDs in AEM te produceren.

Hoewel niet geadviseerd, kunt u het onbruikbaar maken voor het geval u de oude implementatie voor achterwaartse verenigbaarheid met uw bestaande toepassingen nodig hebt. Hiervoor moet u het volgende doen:

1. Ga naar de Console van het Web en verwijder de ***org.apache.jakobbit.security.user.RandomAuthorizableNodeName** ingang van bezit **requiredServicePids** in **Apache Jackrabbit Oak SecurityProvider**.

   U kunt de Leverancier van de Veiligheid van Oak ook vinden door **org.apache.jackrabbit.oak.security.internal.SecurityProviderRegistration** PID in de configuraties te zoeken OSGi.

1. Schrap de **Apache Jackrabbit Oak Willekeurige Authorizable Naam van de Knoop** configuratie OSGi van de Console van het Web.

   Voor gemakkelijkere raadpleging, is PID voor deze configuratie **org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName**.

>[!NOTE]
>
>Voor meer informatie, zie de documentatie van Oak over [ Vergunnbare Generatie van de Naam van de Knoop ](https://jackrabbit.apache.org/oak/docs/security/user/authorizablenodename.html).

### Verhardend pakket anonieme machtigingen {#anonymous-permission-hardening-package}

Standaard worden AEM systeemmetagegevens, zoals `jcr:createdBy` of `jcr:lastModifiedBy` als knooppunteigenschappen, naast gewone inhoud in de opslagplaats opgeslagen. Afhankelijk van de configuratie en de opstelling van het toegangsbeheer, in sommige gevallen zou dit tot blootstelling van persoonlijk identificeerbare informatie (PII) kunnen leiden, bijvoorbeeld wanneer dergelijke knopen als ruwe JSON of XML worden teruggegeven.

Net als alle gegevens in de opslagplaats worden deze eigenschappen gemedieerd door de Oak-machtigingenstapel. De toegang tot deze rechten dient te worden beperkt overeenkomstig het beginsel van de minst bevoorrechte behandeling.

Om dit te steunen, verstrekt de Adobe een toestemmings het verharden pakket als basis voor klanten om op te bouwen. Het werkt door een &quot;ontkent&quot;toegangsbeheeringang bij de bewaarplaatswortel te installeren, die anonieme toegang tot algemeen gebruikte systeemeigenschappen beperkt. Het pakket kan [ worden gedownload ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/helper/anonymous-permissions-pkg-0.1.2.zip) en op alle gesteunde versies van AEM worden geïnstalleerd.

Om de veranderingen te illustreren, kunnen wij de knoopeigenschappen vergelijken die anoniem kunnen worden bekeken alvorens het pakket te installeren:

![ alvorens Pakket ](/help/sites-administering/assets/before_resized.png) te installeren

waarbij de knoppen zichtbaar zijn na de installatie van het pakket, waarbij `jcr:createdBy` en `jcr:lastModifiedBy` niet zichtbaar zijn:

![ na het Installeren van Pakket ](/help/sites-administering/assets/after_resized.png)

Zie de opmerkingen bij de pakketrelease voor meer informatie.

### Klikaanvallen voorkomen {#prevent-clickjacking}

Om klikaanvallen te voorkomen, adviseert de Adobe dat u uw webserver vormt om `X-FRAME-OPTIONS` kopbal te verstrekken die aan `SAMEORIGIN` wordt geplaatst.

Voor meer informatie bij klikjacking, zie de [ plaats van OWASP ](https://www.owasp.org/index.php/Clickjacking).

### Zorg ervoor dat u de coderingstoetsen op de juiste wijze dupliceert als dat nodig is {#make-sure-you-properly-replicate-encryption-keys-when-needed}

Bepaalde AEM en verificatieschema&#39;s vereisen dat u de coderingssleutels in alle AEM kopieert.

Alvorens u dit doet, wordt de zeer belangrijke replicatie gedaan verschillend tussen versies omdat de manier de sleutels tussen 6.3 en oudere versies verschillend zijn opgeslagen.

Zie hieronder voor meer informatie.

#### Toetsen voor AEM 6.3 {#replicating-keys-for-aem}

Terwijl in oudere versies de replicatietoetsen in de bewaarplaats werden opgeslagen, beginnend met AEM 6.3 worden zij opgeslagen op het filesystem.

Als u de sleutels daarom over instanties wilt repliceren, kopieert u ze van de broninstantie naar de locatie van de doelinstanties op het bestandssysteem.

Meer specifiek, moet u het volgende doen:

1. Toegang krijgen tot de AEM instantie - doorgaans een instantie van de auteur - die het te kopiëren toetsmateriaal bevat.
1. Zoek de bundel com.adobe.granite.crypto.file in het lokale bestandssysteem. Onder dit pad bijvoorbeeld:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21`

   Het `bundle.info` -bestand in elke map geeft de bundelnaam aan.

1. Navigeer naar de gegevensmap. Bijvoorbeeld:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Kopieer de HMAC- en hoofdbestanden.
1. Dan, ga naar de doelinstantie u de sleutel HMAC aan wilt dupliceren, en aan de gegevensomslag navigeren. Bijvoorbeeld:

   * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Plak de twee eerder gekopieerde bestanden.
1. [ verfrist de Bundel van Crypto ](/help/communities/deploy-communities.md#refresh-the-granite-crypto-bundle) als de doelinstantie reeds loopt.
1. Herhaal bovenstaande stappen voor alle instanties waaraan u de toets wilt repliceren.

#### Replicatietoetsen voor AEM 6.2 en oudere versies {#replicating-keys-for-aem-and-older-versions}

In AEM 6.2 en oudere versies worden de sleutels opgeslagen in de gegevensopslagruimte onder het knooppunt `/etc/key` .

De geadviseerde manier om de sleutels over uw instanties veilig te herhalen is dit knooppunt slechts te herhalen. U kunt knooppunten selectief repliceren via CRXDE Lite:

1. CRXDE Lite openen door naar *`https://&lt;serveraddress&gt;:4502/crx/de/index.jsp`* te gaan
1. Selecteer het knooppunt `/etc/key` .
1. Ga naar het **lusje van de Replicatie**.
1. Druk de **knoop van de Replicatie**.

### Een beveiligingstest uitvoeren {#perform-a-penetration-test}

De Adobe beveelt aan dat u een penetratietest van uw AEM infrastructuur uitvoert alvorens aan productie te gaan.

### Aanbevolen werkwijzen voor ontwikkeling {#development-best-practices}

Het is kritiek dat de nieuwe ontwikkeling de [ Beste praktijken van de Veiligheid ](/help/sites-developing/security.md) volgt om ervoor te zorgen dat uw AEM milieu veilig blijft.
