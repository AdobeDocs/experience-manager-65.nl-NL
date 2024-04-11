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
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '2959'
ht-degree: 0%

---

# Beveiligingscontrolelijst {#security-checklist}

Deze sectie behandelt diverse stappen die u zou moeten nemen om ervoor te zorgen dat uw AEM installatie wanneer opgesteld veilig is. De controlelijst moet van boven naar beneden worden toegepast.

>[!NOTE]
>
>Er is ook meer informatie beschikbaar over de gevaarlijkste veiligheidsbedreigingen, zoals gepubliceerd door [Open Web Application Security Project (OWASP)](https://owasp.org/www-project-top-ten/).

>[!NOTE]
>
>Er zijn nog enkele [beveiligingsoverwegingen](/help/sites-developing/dev-guidelines-bestpractices.md#security-considerations) van toepassing op de ontwikkelingsfase.

## Belangrijkste veiligheidsmaatregelen {#main-security-measures}

### AEM uitvoeren in de productielodus {#run-aem-in-production-ready-mode}

Zie voor meer informatie [AEM uitvoeren in productielocatie](/help/sites-administering/production-ready.md).

### HTTPS inschakelen voor beveiliging van transportlagen {#enable-https-for-transport-layer-security}

Het inschakelen van de HTTPS-transportlaag op zowel auteur- als publicatieinstanties is verplicht voor het hebben van een beveiligde instantie.

>[!NOTE]
>
>Zie de [HTTP via SSL inschakelen](/help/sites-administering/ssl-by-default.md) voor meer informatie.

### Beveiligingshotfixes installeren {#install-security-hotfixes}

Zorg ervoor dat u de nieuwste [Beveiligingshotfixes verstrekt door Adobe](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html).

### Standaardwachtwoorden voor de AEM- en OSGi-console-beheeraccounts wijzigen {#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts}

Adobe beveelt na installatie aan dat u het wachtwoord voor geprivilegieerde personen wijzigt [**AEM** `admin` rekeningen](#changing-the-aem-admin-password) (in alle gevallen).

Deze rekeningen omvatten:

* De AEM `admin` account

  Nadat u het wachtwoord voor de AEM-beheerdersaccount hebt gewijzigd, gebruikt u het nieuwe wachtwoord voor toegang tot CRX.

* De `admin` wachtwoord voor de console van het Web OSGi

  Deze verandering wordt ook toegepast op de admin rekening die voor de toegang tot van de console van het Web wordt gebruikt, zo gebruik het zelfde wachtwoord wanneer de toegang tot van dat.

Deze twee rekeningen gebruiken afzonderlijke geloofsbrieven en het hebben van verschillend, sterk wachtwoord voor elk is essentieel voor een veilige plaatsing.

#### Het AEM-beheerderswachtwoord wijzigen {#changing-the-aem-admin-password}

Het wachtwoord voor de AEM-beheerdersaccount kan worden gewijzigd via de [Graniet-bewerkingen - gebruikers](/help/sites-administering/granite-user-group-admin.md) console.

Hier kunt u de `admin` rekening en [het wachtwoord wijzigen](/help/sites-administering/granite-user-group-admin.md#changing-the-password-for-an-existing-user).

>[!NOTE]
>
>Als u de beheerdersaccount wijzigt, wordt ook de OSGi-webconsoleversie gewijzigd. Nadat u de beheerdersaccount hebt gewijzigd, moet u de OSGi-account wijzigen in iets anders.

#### Het belang van het wijzigen van het wachtwoord voor de OSGi-webconsole {#importance-of-changing-the-osgi-web-console-password}

Aside van de AEM `admin` account, als het standaardwachtwoord voor het OSGi-webconsolewachtwoord niet wordt gewijzigd, kan dit leiden tot:

* Belichting van de server met een standaardwachtwoord tijdens opstarten en afsluiten (wat minuten kan duren voor grote servers);
* Belichting van de server wanneer de opslagplaats is neer/herstart bundel - en OSGI loopt.

Voor meer informatie bij het veranderen van het wachtwoord van de Webconsole, zie [Het beheerwachtwoord voor de OSGi-webconsole wijzigen](/help/sites-administering/security-checklist.md#changing-the-osgi-web-console-admin-password) hieronder.

#### Het beheerwachtwoord voor de OSGi-webconsole wijzigen {#changing-the-osgi-web-console-admin-password}

Wijzig het wachtwoord dat wordt gebruikt voor toegang tot de webconsole. Een [Configuratie van SDAB](/help/sites-deploying/configuring-osgi.md) om de volgende eigenschappen van **Apache Felix OSGi Management Console**:

* **Gebruikersnaam** en **Wachtwoord**, de referenties voor toegang tot de Apache Felix Web Management Console zelf.
Het wachtwoord moet worden gewijzigd *na* de eerste installatie om de veiligheid van uw instantie te verzekeren.

>[!NOTE]
>
>Zie [Configuratie van SDAB](/help/sites-deploying/configuring-osgi.md) voor volledige details van het vormen van montages OSGi.

**Het beheerwachtwoord voor de OSGi-webconsole wijzigen**:

1. Met de **Gereedschappen**, **Bewerkingen** menu, opent u de **Webconsole** en navigeer naar de **Configuratie** sectie.
Bijvoorbeeld bij `<server>:<port>/system/console/configMgr`.
1. Navigeer naar en open het item voor **Apache Felix OSGi Management Console**.
1. Wijzig de **gebruikersnaam** en **password**.

   ![chlimage_1-3](assets/chlimage_1-3.png)

1. Selecteren **Opslaan**.

### Aangepaste fouthandler implementeren {#implement-custom-error-handler}

Adobe raadt aan aangepaste fouthandlerpagina&#39;s te definiëren, met name voor 404- en 500 HTTP-antwoordcodes, om openbaarmaking van informatie te voorkomen.

>[!NOTE]
>
>Zie [Hoe kan ik aangepaste scripts of fouthandlers maken](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/implementing/developing/full-stack/custom-error-page.html) voor meer informatie .

### Volledige lijst voor beveiligingscontrole voor verzending {#complete-dispatcher-security-checklist}

AEM Dispatcher is een essentieel onderdeel van uw infrastructuur. Adobe raadt u aan de [Controlelijst voor beveiliging van verzending](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/security-checklist.html).

>[!CAUTION]
>
>Met de Dispatcher moet u de kiezer &quot;.form&quot; uitschakelen.

## Controlestappen {#verification-steps}

### Gebruikers voor replicatie en transport configureren {#configure-replication-and-transport-users}

Een standaardinstallatie van AEM specificeert `admin` als de gebruiker voor vervoergeloofsbrieven binnen het gebrek [replicatiemiddelen](/help/sites-deploying/replication.md). Ook, wordt de admin gebruiker gebruikt aan bron de replicatie op het auteurssysteem.

Met het oog op de veiligheid moeten beide aspecten worden gewijzigd om rekening te houden met het specifieke gebruiksgeval in kwestie, waarbij de volgende twee aspecten in acht moeten worden genomen:

* De **transportgebruiker** mag niet de beheerder zijn. Stel in plaats daarvan een gebruiker in het publicatiesysteem in die alleen toegangsrechten heeft tot de relevante delen van het publicatiesysteem en gebruik de referenties van die gebruiker voor het vervoer.

  U kunt van de gebundelde replicatie-ontvanger gebruiker beginnen en de toegangsrechten van deze gebruiker vormen om uw situatie aan te passen

* De **replicatiegebruiker** of **Gebruiker-id agent** moet ook niet de admin gebruiker zijn, maar een gebruiker die slechts inhoud kan zien die wordt herhaald. De replicatiegebruiker wordt gebruikt om de inhoud te verzamelen die op het auteurssysteem moet worden herhaald alvorens het naar de uitgever wordt verzonden.

### Controleer de beveiligingscontroles op het dashboard Bewerkingen {#check-the-operations-dashboard-security-health-checks}

AEM 6 introduceert het nieuwe Dashboard van Verrichtingen, dat op het helpen van systeemexploitanten problemen oplossen en de gezondheid van een geval controleert.

Het dashboard bevat ook een verzameling veiligheidscontroles. U wordt aangeraden de status van alle beveiligingscontroles te controleren voordat u live gaat met uw productieexemplaar. Voor meer informatie raadpleegt u de [Documentatie van het operatiedashboard](/help/sites-administering/operations-dashboard.md).

### Controleren of voorbeeldinhoud aanwezig is {#check-if-example-content-is-present}

Alle voorbeeldinhoud en -gebruikers (bijvoorbeeld het Geometrixx-project en de onderdelen ervan) moeten worden verwijderd en volledig op een productiesysteem worden verwijderd voordat het openbaar toegankelijk wordt gemaakt.

>[!NOTE]
>
>Het voorbeeld `We.Retail` toepassingen worden verwijderd als deze instantie wordt uitgevoerd in [Productiemodus](/help/sites-administering/production-ready.md). Als dit scenario niet het geval is, kunt u de steekproefinhoud desinstalleren door naar de Manager van het Pakket te gaan, dan het zoeken naar, en het desinstalleren, allen `We.Retail` pakketten.

Zie [Werken met pakketten](package-manager.md).

### Controleren of de CRX-ontwikkelingsbundels aanwezig zijn {#check-if-the-crx-development-bundles-are-present}

Deze ontwikkelingsOSGi- bundels zouden op zowel auteur moeten worden gedesinstalleerd als productieve systemen publiceren alvorens hen toegankelijk te maken.

* Adobe CRXDE-ondersteuning (com.adobe.granite.crxde-support)
* Adobe in CRX Explorer (com.adobe.granite.crx-explorer)
* Graniet-CRXDE Lite Adobe (com.adobe.granite.crxde-lite)

### Controleren of de ontwikkelingsbundel Sling aanwezig is {#check-if-the-sling-development-bundle-is-present}

De [AEM Developer Tools](/help/sites-developing/aem-eclipse.md) Implementeer de Apache Sling Tooling Support Install (org.apache.sling.tooling.support.install).

Deze bundel OSGi zou op zowel auteur moeten worden gedesinstalleerd als productieve systemen publiceren alvorens hen toegankelijk te maken.

### Protect tegen XSS (cross-site request-vervalsing) {#protect-against-cross-site-request-forgery}

#### Het CSRF-beschermingskader {#the-csrf-protection-framework}

AEM 6.1 schepen met een mechanisme dat tegen de aanvallen van de smeedmachine van het Verzoek van de Verkeer van de Deposito&#39;s van de Deposito&#39;s helpt beschermen, genoemd **CSRF-beschermingskader**. Raadpleeg voor meer informatie over het gebruik ervan de [documentatie](/help/sites-developing/csrf-protection.md).

#### Het filter Verschuivende verwijzing {#the-sling-referrer-filter}

Als u bekende beveiligingsproblemen wilt verhelpen met CSRF-bestanden (Cross-Site Request Smeedery) in CRX WebDAV en Apache Sling, voegt u configuraties voor het filter Referrer toe om dit te gebruiken.

De dienst van de verwijzingsfilter is de dienst OSGi die u het volgende laat vormen:

* welke http-methoden moeten worden gefilterd
* of een lege verwijzingskoptekst is toegestaan
* en een lijst met servers die naast de serverhost zijn toegestaan.

  Standaard staan alle variaties van localhost en de huidige hostnamen waar de server aan gebonden is, in de lijst.

Om de dienst van het verwijzingsfilter te vormen:

1. Open de Apache Felix-console (**Configuraties**) om:

   `https://<server>:<port_number>/system/console/configMgr`

1. Aanmelden als `admin`.
1. In de **Configuraties** -menu, selecteert u:

   `Apache Sling Referrer Filter`

1. In de `Allow Hosts` veld, voert u alle hosts in die als referentie zijn toegestaan. Elke vermelding moet van het formulier zijn

   &lt;protocol>://&lt;server>:&lt;port>

   Bijvoorbeeld:

   * `https://allowed.server:80` staat alle verzoeken van deze server met de bepaalde haven toe.
   * Als u ook https-aanvragen wilt toestaan, moet u een tweede regel invoeren.
   * Als u alle poorten van die server toestaat, kunt u `0` als het poortnummer.

1. Controleer de `Allow Empty` veld, als u lege/ontbrekende verwijzingskoppen wilt toestaan.

   >[!CAUTION]
   >
   >Adobe raadt u aan een referentie op te geven terwijl u opdrachtregelprogramma&#39;s gebruikt, zoals `cURL` in plaats van een lege waarde toe te staan aangezien het uw systeem aan aanvallen CSRF zou kunnen blootstellen.

1. Bewerk de methoden die dit filter gebruikt voor controles met de `Filter Methods` veld.

1. Klikken **Opslaan** om uw wijzigingen op te slaan.

### OSGI-instellingen {#osgi-settings}

Sommige instellingen van OSGI worden standaard ingesteld om foutopsporing in de toepassing te vergemakkelijken. Wijzig dergelijke instellingen in de productieve exemplaren van uw publicatie en auteur om te voorkomen dat er interne informatie naar het publiek lekt.

>[!NOTE]
>
>Alle onderstaande instellingen, behalve **Het dagfilter voor WCM-foutopsporing** worden automatisch gedekt door de [Productiemodus](/help/sites-administering/production-ready.md). Als dusdanig, adviseert de Adobe dat u alle montages alvorens uw geval in een productieve milieu te opstellen controleert.

Voor elk van de volgende services moeten de opgegeven instellingen worden gewijzigd:

* [Adobe Granite HTML Library Manager](/help/sites-deploying/osgi-configuration-settings.md#day-cq-html-library-manager):

   * enable **Minieren** (om CRLF- en spatietekens te verwijderen).
   * enable **Gzip** (zodat bestanden met één aanvraag kunnen worden uitgepakt en geopend).
   * disable **Foutopsporing**
   * disable **Timing**

* [Day CQ WCM-foutopsporingsfilter](/help/sites-deploying/osgi-configuration-settings.md#day-cq-wcm-debug-filter):

   * uitschakelen **Inschakelen**

* [Day CQ WCM-filter](/help/sites-deploying/osgi-configuration-settings.md):

   * alleen bij publiceren, instellen **WCM-modus** naar &quot;disabled&quot;

* [Apache Sling JavaScript-handler](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-javascript-handler):

   * disable **Foutopsporingsinfo genereren**

* [Apache Sling JSP Script Handler](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-jsp-script-handler):

   * disable **Foutopsporingsinfo genereren**
   * disable **Toegewezen inhoud**

Zie [OSGi-configuratie-instellingen](/help/sites-deploying/osgi-configuration-settings.md).

Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor meer details en de aanbevolen werkwijzen.

## Verdere lezingen {#further-readings}

### Aanvallen van Denial of Service (DoS) beperken {#mitigate-denial-of-service-dos-attacks}

Een ontkenning van de dienst (Dos) aanval is een poging om een computermiddel niet beschikbaar te maken aan zijn voorgenomen gebruikers. Deze aanval wordt vaak gedaan door het middel te overbelasten; bijvoorbeeld:

* Een stroom verzoeken van een externe bron.
* Een verzoek om meer informatie dan het systeem met succes kan leveren.

  Bijvoorbeeld een JSON-representatie van de gehele gegevensopslagruimte.

* Door een inhoudspagina met een onbeperkt aantal URL&#39;s aan te vragen, kan URL een handvat, sommige selecteurs, een uitbreiding, en een achtervoegsel omvatten - om het even welke kan worden gewijzigd.

  Bijvoorbeeld: `.../en.html` kan ook worden aangevraagd als:

   * `.../en.ExtensionDosAttack`
   * `.../en.SelectorDosAttack.html`
   * `.../en.html/SuffixDosAttack`

  Alle geldige variaties (retourneren bijvoorbeeld een `200` reactie en worden gevormd om) in het voorgeheugen onder te brengen door Dispatcher, uiteindelijk leidend tot een volledig dossiersysteem en geen dienst voor verdere verzoeken.

Er zijn vele punten van configuratie om dergelijke aanvallen te voorkomen, maar alleen die punten die betrekking hebben op AEM worden hier besproken.

**Het vormen het Verkopen om Dos te verhinderen**

Verkopen is *inhoudgericht*. De verwerking wordt geconcentreerd op de inhoud aangezien elk (HTTP) verzoek op inhoud in de vorm van een middel JCR (een gegevensopslagplaats knoop) in kaart wordt gebracht:

* Het eerste doel is de bron (JCR-knooppunt) die de inhoud bevat.
* Ten tweede bevindt de renderer, of het script, zich in de eigenschappen resource met bepaalde onderdelen van de aanvraag (bijvoorbeeld kiezers en/of de extensie).

Zie [Verwerking van aanvraag voor verzending](/help/sites-developing/the-basics.md#sling-request-processing) voor meer informatie .

Deze aanpak maakt Sling krachtig en flexibel, maar zoals altijd is het de flexibiliteit die zorgvuldig moet worden beheerd.

Om misbruik van DosS te helpen voorkomen, kunt u het volgende doen:

1. Neem controles op het toepassingsniveau op. Vanwege het aantal mogelijke variaties is een standaardconfiguratie niet mogelijk.

   In uw toepassing moet u:

   * Beheer de kiezers in de toepassing, zodat u *alleen* de vereiste expliciete kiezers bedienen en retourneren `404` voor alle anderen.
   * De uitvoer van een onbeperkt aantal inhoudsknooppunten voorkomen.

1. Controleer de configuratie van de standaardrenderers, die een probleemgebied kunnen zijn.

   * Met name transformeert de JSON-renderer de boomstructuur over meerdere niveaus.

     Bijvoorbeeld, het verzoek:

     `http://localhost:4502/.json`

     kan de hele opslagplaats in een JSON-representatie dumpen, wat aanzienlijke serverproblemen kan veroorzaken. Daarom wordt bij Sling een limiet ingesteld voor het aantal maximale resultaten. Als u de diepte van de JSON-rendering wilt beperken, stelt u de waarde in voor het volgende:

     **JSON Max-resultaten** ( `json.maximumresults`)

     in de configuratie voor de [Apache Sling GET Servlet](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet). Wanneer deze limiet wordt overschreden, wordt de rendering samengevouwen. De standaardwaarde voor Verdelen binnen AEM is `1000`.

   * Als preventieve maatregel, zou u de andere standaardrenderers (HTML, gewone teksten, XML) moeten onbruikbaar maken. Opnieuw, door te vormen [Apache Sling GET Servlet](/help/sites-deploying/osgi-configuration-settings.md#apache-sling-get-servlet).

   >[!CAUTION]
   >
   >Schakel de JSON-renderer niet uit omdat deze vereist is voor de normale werking van AEM.

1. Gebruik een firewall om toegang tot uw instantie te filteren.

   * Het gebruik van een firewall op besturingssysteemniveau is nodig om toegang tot punten van uw instantie te filteren die tot een Denial of Service-aanval kan leiden als deze niet is beveiligd.

**Matig tegen doS die door de Selecteurs van de Vorm wordt veroorzaakt**

>[!NOTE]
>
>Deze beperking moet alleen worden uitgevoerd op AEM omgevingen die geen Forms gebruiken.

Omdat AEM geen out-of-the-box indexen voor verstrekt `FormChooserServlet`Door formulierkiezers te gebruiken in query&#39;s, kan een kostbare repository traversal worden geactiveerd, waarbij de AEM instantie meestal tot stilstand wordt gebracht. Formulierkiezers kunnen worden gedetecteerd door de aanwezigheid van de **&amp;ast;.form.&amp;asteren;** tekenreeks in query&#39;s.

U kunt dit probleem verhelpen door de volgende stappen uit te voeren:

1. Ga naar de webconsole door uw browser naar *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*

1. Zoeken naar **Day CQ WCM-formulierkiezerserver**
1. Nadat u op de ingang klikt, maak onbruikbaar **Geavanceerd zoeken vereist** in het volgende venster.

1. Klikken **Opslaan**.

**Mitigate Against DoS Caused by Asset Download Servlet**

Met de standaardserver voor het downloaden van middelen kunnen geverifieerde gebruikers willekeurig grote, gelijktijdige, downloadverzoeken afgeven om ZIP-bestanden met elementen te maken. Door grote ZIP-archieven te maken, kunnen de server en het netwerk worden overbelast. Om een potentieel Weigeren van de Dienst (Dos) risico te verlichten dat door dit gedrag wordt veroorzaakt, `AssetDownloadServlet` De component OSGi is standaard uitgeschakeld [!DNL Experience Manager] -instantie publiceren. De functie is ingeschakeld op [!DNL Experience Manager] instantie van de auteur door gebrek.

Als u de downloadmogelijkheden niet nodig hebt, schakelt u de servlet uit bij het ontwerpen en publiceren van implementaties. Als de installatie vereist dat de mogelijkheid voor het downloaden van middelen is ingeschakeld, raadpleegt u [dit artikel](/help/assets/download-assets-from-aem.md) voor meer informatie . Bovendien kunt u een maximale downloadlimiet definiëren die uw implementatie kan ondersteunen.

### WebDAV uitschakelen {#disable-webdav}

Schakel WebDAV op zowel auteur als publicatiemilieu&#39;s uit door de aangewezen bundels tegen te houden OSGi.

1. Verbinding maken met de **Felix Management Console** uitgevoerd op:

   `https://<*host*>:<*port*>/system/console`

   Bijvoorbeeld: `http://localhost:4503/system/console/bundles`.

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

Sinds AEM 6.1 wordt de manier waarop namen van gebruikerknooppunten (ook wel wel autoriseerbare id&#39;s genoemd) worden opgeslagen, gewijzigd met een nieuwe implementatie van de `AuthorizableNodeName` interface. De nieuwe interface stelt niet meer de gebruiker - identiteitskaart in de knoopnaam bloot maar produceert een willekeurige naam in plaats daarvan.

Geen configuratie moet worden uitgevoerd om het toe te laten, omdat het nu de standaardmanier is om toegelaten IDs in AEM te produceren.

Hoewel niet geadviseerd, kunt u het onbruikbaar maken voor het geval u de oude implementatie voor achterwaartse verenigbaarheid met uw bestaande toepassingen nodig hebt. Hiervoor moet u het volgende doen:

1. Ga naar de webconsole en verwijder het item** org.apache.jackrabbit.security.user.RandomAuthorizableNodeName** uit de eigenschap **requiredServicePids** in **Apache Jackrabbit Oak SecurityProvider**.

   U kunt ook de Oak Security Provider vinden op zoek naar de **org.apache.jackrabbit.oak.security.internal.SecurityProviderRegistration** PID in de configuraties OSGi.

1. Verwijder de **Apache Jackrabbit Oak Random Authoriable Node Name** OSGi-configuratie vanuit de webconsole.

   Voor gemakkelijkere raadpleging, PID voor deze configuratie is **org.apache.jackrabbit.oak.security.user.RandomAuthorizableNodeName**.

>[!NOTE]
>
>Raadpleeg de documentatie bij de eiken over [Authorizable Node Name Generation](https://jackrabbit.apache.org/oak/docs/security/user/authorizablenodename.html).

### Verhardend pakket anonieme machtigingen {#anonymous-permission-hardening-package}

AEM slaat standaard systeemmetagegevens op, zoals `jcr:createdBy` of `jcr:lastModifiedBy` als knoopeigenschappen, naast regelmatige inhoud, in de bewaarplaats. Afhankelijk van de configuratie en de opstelling van het toegangsbeheer, in sommige gevallen zou dit tot blootstelling van persoonlijk identificeerbare informatie (PII) kunnen leiden, bijvoorbeeld wanneer dergelijke knopen als ruwe JSON of XML worden teruggegeven.

Net als alle gegevens in de opslagplaats worden deze eigenschappen gemedieerd door de Oak-machtigingenstapel. De toegang tot deze rechten dient te worden beperkt overeenkomstig het beginsel van de minst bevoorrechte behandeling.

Om dit te steunen, verstrekt de Adobe een toestemmings het verharden pakket als basis voor klanten om op te bouwen. Het werkt door een &quot;ontkent&quot;toegangsbeheeringang bij de bewaarplaatswortel te installeren, die anonieme toegang tot algemeen gebruikte systeemeigenschappen beperkt. Het pakket kan worden gedownload [hier](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/helper/anonymous-permissions-pkg-0.1.2.zip) en kan op alle gesteunde versies van AEM worden geïnstalleerd.

Om de veranderingen te illustreren, kunnen wij de knoopeigenschappen vergelijken die anoniem kunnen worden bekeken alvorens het pakket te installeren:

![Voordat u het pakket installeert](/help/sites-administering/assets/before_resized.png)

met de apparaten die na de installatie van het pakket zichtbaar zijn, waarbij `jcr:createdBy` en `jcr:lastModifiedBy` zijn niet zichtbaar:

![Na installatie van pakket](/help/sites-administering/assets/after_resized.png)

Zie de opmerkingen bij de pakketrelease voor meer informatie.

### Klikaanvallen voorkomen {#prevent-clickjacking}

Om klikaanvallen te verhinderen, adviseert de Adobe dat u uw webserver vormt om `X-FRAME-OPTIONS` HTTP-header ingesteld op `SAMEORIGIN`.

Voor meer informatie over klikjacking, zie [OWASP-site](https://www.owasp.org/index.php/Clickjacking).

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

   De `bundle.info` in elke map de naam van de bundel aangeeft.

1. Navigeer naar de gegevensmap. Bijvoorbeeld:

   * `<author-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Kopieer de HMAC- en hoofdbestanden.
1. Dan, ga naar de doelinstantie u de sleutel HMAC aan wilt dupliceren, en aan de gegevensomslag navigeren. Bijvoorbeeld:

   * `<publish-aem-install-dir>/crx-quickstart/launchpad/felix/bundle21/data`

1. Plak de twee eerder gekopieerde bestanden.
1. [De Cryptobundel vernieuwen](/help/communities/deploy-communities.md#refresh-the-granite-crypto-bundle) als de doelinstantie al actief is.
1. Herhaal bovenstaande stappen voor alle instanties waaraan u de toets wilt repliceren.

#### Replicatietoetsen voor AEM 6.2 en oudere versies {#replicating-keys-for-aem-and-older-versions}

In AEM 6.2 en oudere versies worden de sleutels in de bewaarplaats onder `/etc/key` knooppunt.

De geadviseerde manier om de sleutels over uw instanties veilig te herhalen is dit knooppunt slechts te herhalen. U kunt knooppunten selectief repliceren via CRXDE Lite:

1. CRXDE Lite openen door naar *`https://&lt;serveraddress&gt;:4502/crx/de/index.jsp`*
1. Selecteer de `/etc/key` knooppunt.
1. Ga naar de **Replicatie** tab.
1. Druk op **Replicatie** knop.

### Een beveiligingstest uitvoeren {#perform-a-penetration-test}

De Adobe beveelt aan dat u een penetratietest van uw AEM infrastructuur uitvoert alvorens aan productie te gaan.

### Aanbevolen werkwijzen voor ontwikkeling {#development-best-practices}

Het is van essentieel belang dat de nieuwe ontwikkelingen [Aanbevolen werkwijzen voor beveiliging](/help/sites-developing/security.md) om ervoor te zorgen dat uw AEM omgeving veilig blijft.
