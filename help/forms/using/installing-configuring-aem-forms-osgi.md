---
title: Mogelijkheden voor gegevensvastlegging installeren en configureren
seo-title: Mogelijkheden voor gegevensvastlegging installeren en configureren
description: Aangepaste formulieren, PDF-formulieren en HTML5-formulieren installeren en configureren. Configureer Adobe Analytics en Adobe Target voor adaptieve formulieren om het gebruik van formulieren en doelgebruikers te analyseren op basis van hun profiel.
seo-description: Aangepaste formulieren, PDF-formulieren en HTML5-formulieren installeren en configureren. Configureer Adobe Analytics en Adobe Target voor adaptieve formulieren om het gebruik van formulieren en doelgebruikers te analyseren op basis van hun profiel.
uuid: 5d49032a-4dea-4f21-9dad-a7a30c5872ea
topic-tags: installing
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: dfc473eb-6091-4f5d-a5a0-789972c513a9
docset: aem65
translation-type: tm+mt
source-git-commit: f323b490c37effc3cbb36c793b62fa788eca9545

---


# Mogelijkheden voor gegevensvastlegging installeren en configureren{#install-and-configure-data-capture-capabilities}

## Inleiding {#introduction}

AEM Forms biedt een set formulieren voor het verkrijgen van gegevens van eindgebruikers: adaptieve formulieren, HTML5-formulieren en PDF-formulieren. Het programma bevat ook gereedschappen waarmee u alle beschikbare formulieren op een webpagina kunt weergeven, het gebruik van formulieren kunt analyseren en doelgebruikers kunt selecteren op basis van hun profiel. Deze mogelijkheden zijn opgenomen in het invoegpakket voor AEM Forms. Het invoegpakket wordt geïmplementeerd op een instantie Auteur of Publiceren van AEM.

**Aangepaste formulieren:** Deze formulieren veranderen de weergave op basis van de schermgrootte van het apparaat, zijn aantrekkelijk en interactief van aard. Adaptieve formulieren kunnen ook worden geïntegreerd met Adobe Analytics, Adobe Sign en Adobe Target. Hierdoor kunt u op basis van demografie en andere functies persoonlijke formulieren en procesgeoriënteerde ervaringen aan gebruikers aanbieden. U kunt adaptieve formulieren ook integreren met Adobe Sign.

**PDF-formulieren** zijn geschikt voor pixelperfecte afdrukken en voor het vastleggen van digitale gegevens in een PDF-document. In de digitale avatar kunt u deze formulieren invullen met Adobe Acrobat of Acrobat Reader. U kunt deze formulieren hosten op uw website of met de portal Formulieren deze formulieren weergeven op een AEM-site. U kunt deze formulieren ook als bijlagen naar anderen verzenden. Deze formulieren zijn het meest geschikt voor desktopomgevingen.

**HTML5 Forms** is de browservriendelijke versie van PDF Forms. HTML5 Forms is geschikt voor omgevingen die geen ondersteuning bieden voor PDF-plug-ins. Met HTML5 Forms kunt u op XFA gebaseerde formulieren weergeven op mobiele apparaten en desktopbrowsers waarop XFA-gebaseerde PDF niet wordt ondersteund. Deze formulieren zijn het meest geschikt voor tablets en desktopomgevingen.

AEM Forms is een krachtig platform op bedrijfsniveau en het vastleggen van gegevens (adaptieve formulieren, PDF-formulieren en HTML5 Forms) is slechts een van de mogelijkheden van AEM Forms. Voor de volledige lijst van mogelijkheden, zie [Inleiding aan Vormen](/help/forms/using/introduction-aem-forms.md)AEM.

## Implementatietopologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. U hebt slechts minimaal één instantie van AEM-auteur en AEM-publicatie nodig om de mogelijkheden voor gegevensvastlegging in AEM Forms uit te voeren. De volgende topologie wordt gesuggereerd om AEM Forms AEM gegevens vangen mogelijkheden in werking te stellen. Voor gedetailleerde informatie over de topologie, zie [Architectuur en plaatsingstopologieën voor Vormen](/help/forms/using/aem-forms-architecture-deployment.md)AEM.

![aanbevolen topologie](assets/recommended-topology.png)

## Systeemvereisten {#system-requirements}

Voordat u de mogelijkheid voor het vastleggen van gegevens van AEM Forms gaat installeren en configureren, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Raadpleeg de [technische vereisten](/help/sites-deploying/technical-requirements.md)voor een gedetailleerde lijst met ondersteunde hardware en software.

* Het installatiepad van de AEM-instantie bevat geen spaties.
* Er wordt een AEM-instantie uitgevoerd. In AEM-terminologie is een &quot;instantie&quot; een kopie van AEM die wordt uitgevoerd op een server in de auteur- of publicatiemodus. U hebt ten minste twee [AEM-instanties nodig (één auteur en één publiceer)](/help/sites-deploying/deploy.md) om de mogelijkheden voor gegevensvastlegging in AEM Forms uit te voeren:

   * **Auteur**: Een AEM-instantie die wordt gebruikt om inhoud te maken, te uploaden en te bewerken en om de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Publiceren**: Een AEM-instantie die de gepubliceerde inhoud via internet of een intern netwerk aan het publiek levert.

* Er wordt voldaan aan de geheugenvereisten. AEM Forms add-on package vereist:

   * 15 GB tijdelijke ruimte voor op Microsoft Windows gebaseerde installaties.
   * 6 GB tijdelijke ruimte voor UNIX-installaties.

* De replicatie en omgekeerde replicatie voor de auteur en publiceer instanties worden geplaatst. For details, see [Replication](/help/sites-deploying/replication.md).
* Voor op UNIX gebaseerde systemen:

   * Installeer de volgende 32-bits pakketten van de installatiemedia:

<table>
 <tbody>
  <tr>
   <td>uitzetten</td>
   <td>fontconfig</td>
   <td>freetype</td>
   <td>glibc</td>
  </tr>
  <tr>
   <td>libcurl</td>
   <td>libICE</td>
   <td>libicu</td>
   <td>libSM</td>
  </tr>
  <tr>
   <td>libuuid</td>
   <td>libX11</td>
   <td><p>libXau</p> </td>
   <td>libxcb</td>
  </tr>
  <tr>
   <td>libXext</td>
   <td>libXinerama</td>
   <td>libXrandr</td>
   <td>libXrender</td>
  </tr>
  <tr>
   <td>nss-softokn-freebl</td>
   <td>OpenSSL</td>
   <td>zlib</td>
   <td> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Als OpenSSL al op de server is geïnstalleerd, voert u een upgrade uit naar de meest recente versie.
>* Maak libcurl.so, libcrypto.so en libssl.so symlinks naar de nieuwste versie van respectievelijk de bibliotheken libcurl, libcrypto en libssl.
>



* Installeer het volgende 64-bits pakket van de installatiemedia:

   * libicu

## AEM Forms add-on-pakket installeren {#install-aem-forms-add-on-package}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Het pakket bevat AEM Forms-gegevensvastlegging en andere mogelijkheden. Voer de volgende stappen uit om het invoegpakket te installeren:

1. Meld u als beheerder aan bij de [AEM-server](https://localhost:4502) en open [pakketshare](https://localhost:4502/crx/packageshare). U hebt een Adobe-id nodig om u aan te melden bij het delen van het pakket.
1. Zoek in [AEM-pakketdeling](https://localhost:4502/crx/packageshare/login.html)in **AEM 6.5-formulierinvoegpakketten** naar het pakket dat op uw besturingssysteem van toepassing is en klik op **Downloaden**. Lees en accepteer de licentieovereenkomst en klik op **OK**. Het downloaden begint. Nadat u het bestand hebt gedownload, staat het woord **Gedownload** naast het pakket.

   U kunt het versienummer ook gebruiken om een add-on pakket te zoeken. Raadpleeg het [artikel over de release](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) van AEM Forms voor het versienummer van het meest recente pakket.

1. Klik op **Gedownload** nadat het downloaden is voltooid. U wordt omgeleid naar pakketbeheer. Zoek in pakketbeheer naar het gedownloade pakket en klik op **Installeren**.

   Als u het pakket handmatig downloadt via de directe koppeling in het [artikel met de release](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) van AEM Forms, meldt u zich aan bij pakketbeheer, klikt u op Pakket **** uploaden, selecteert u het gedownloade pakket en klikt u op Uploaden. Nadat het pakket is geüpload, klikt u op de pakketnaam en klikt u op **Installeren.**

1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM-instantie opnieuw te starten. **Start de server niet onmiddellijk opnieuw.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer in het `[AEM-Installation-Directory]/crx-quickstart/logs/error.log` bestand worden weergegeven en het logbestand stabiel is.
1. Herhaal stap 1-4 voor alle instanties Auteur en Publiceren.

## Configuratie na installatie {#post-installation-configurations}

AEM Forms heeft een aantal verplichte en optionele configuraties. De verplichte configuraties omvatten het vormen bibliotheken BouncyCastle en serialization agent. Tot de optionele configuraties behoren het configureren van dispatcher, Forms Portal, Adobe Sign, Adobe Analytics en Adobe Target.

### Verplichte configuraties na installatie {#mandatory-post-installation-configurations}

#### RSA- en BouncyCastle-bibliotheken configureren {#configure-rsa-and-bouncycastle-libraries}

Voer de volgende stappen op alle Auteur uit en publiceer instanties om de bibliotheken op te starten afvaardigen:

1. Stop de onderliggende AEM-instantie.
1. Open het `[AEM installation directory]\crx-quickstart\conf\sling.properties` bestand om het te bewerken.

   Als u eerst AEM hebt gestart, bewerkt u de eigenschappen sling.property op `[AEM installation directory]\crx-quickstart\bin\start.bat` `[AEM_root]\crx-quickstart\`.

1. Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. Sla het bestand op, sluit het en start de AEM-instantie.
1. Herhaal stap 1-4 voor alle instanties Auteur en Publiceren.

#### Vorm de rangschikkingsagent {#configure-the-serialization-agent}

Voer de volgende stappen uit op alle instanties Auteur en Publiceren om het pakket te whitelist:

1. Open AEM Configuration Manager in een browservenster. De standaard-URL is `https://'[server]:[port]'/system/console/configMgr`.
1. Zoek naar **com.adobe.cq.deserfw.impl.DeserializationFirewallImpl.name** en open de configuratie.
1. Voeg het pakket **sun.util.agenda** toe aan het veld **whitelist** . Click **Save**.
1. Herhaal stap 1-3 voor alle instanties Auteur en Publiceren.

### Optionele configuraties na installatie {#optional-post-installation-configurations}

#### Dispatcher configureren {#configure-dispatcher}

Dispatcher is een programma voor het in cache plaatsen en taakverdeling voor AEM. AEM Dispatcher helpt ook de AEM-server tegen aanvallen te beschermen. U kunt de beveiliging van uw AEM-instantie verhogen door de Dispatcher te gebruiken in combinatie met een webserver op bedrijfsniveau. Als u [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html)gebruikt, voert u de volgende configuraties voor AEM Forms uit:

1. Toegang voor AEM-formulieren configureren:

   Open het bestand dispatcher.any voor bewerking. Navigeer naar de filtersectie en voeg het volgende filter toe aan de filtersectie:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Sla het bestand op en sluit het. Raadpleeg de documentatie bij [Verzender](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html)voor meer informatie over filters.

1. Configureer de referentiefilterservice:

   Meld u als beheerder aan bij het configuratiebeheer van Apache Felix. De standaard-URL van het configuratiemanager is `https://[server]:[port_number]/system/console/configMgr`. Selecteer in het menu **Configuraties** de optie **Filter** Apache-schuifverwijzing. Voer in het veld Hosts toestaan de hostnaam van de verzender in om het als referentie toe te staan en klik op **Opslaan**. De indeling van de invoer is &quot;https://[server]:[port]&quot;.

#### Cache configureren {#configure-cache}

Caching is een mechanisme om gegevenstoegang te verkorten, latentie te verminderen, en input/output (I/O) snelheden te verbeteren. In de cache van adaptieve formulieren worden alleen HTML-inhoud en JSON-structuur van een adaptief formulier opgeslagen zonder dat vooraf ingevulde gegevens worden opgeslagen. Hierdoor wordt de tijd die nodig is om een adaptief formulier te genereren, verkort.

* Als u de cache voor adaptieve formulieren gebruikt, gebruikt u de [AEM Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) om clientbibliotheken (CSS en JavaScript) van een adaptief formulier in cache te plaatsen.
* Zorg tijdens het ontwikkelen van aangepaste componenten dat de cache van adaptieve formulieren uitgeschakeld blijft op de server die voor ontwikkeling wordt gebruikt.

Voer de volgende stappen uit om de cache voor adaptieve formulieren te configureren:

1. Ga naar AEM webconsoleconfiguratiebeheer op https://&#39;[server]:[port]&#39;/system/console/configMgr.
1. Klik de **Aangepaste Vorm en de Interactieve Configuratie** van het Kanaal van de Communicatie van het Web om zijn configuratiewaarden uit te geven. Geef in het dialoogvenster Configuratiewaarden bewerken het maximumaantal formulieren of documenten op dat een instantie van de AEM Forms-server in cache kan plaatsen in het veld **Aantal adaptieve formulieren** . De standaardwaarde is 100. Click **Save**.

   >[!NOTE]
   >
   >Als u de cache wilt uitschakelen, stelt u de waarde in het veld Aantal adaptieve formulieren in op **0**. De cache wordt opnieuw ingesteld en alle formulieren en documenten worden uit de cache verwijderd wanneer u de cachemonfiguratie uitschakelt of wijzigt.

#### SSL-communicatie configureren voor formuliergegevensmodel {#configure-ssl-communcation-for-form-data-model}

U kunt SSL-communicatie inschakelen voor het formuliergegevensmodel. Als u SSL-communicatie wilt inschakelen voor het formuliergegevensmodel, voegt u certificaten toe aan de Java Trust Store van alle exemplaren voordat u een AEM Forms-instantie start. U kunt de onderstaande opdracht uitvoeren om de certificaten toe te voegen: &quot;

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

#### Adobe-ondertekening configureren {#configure-adobe-sign}

Met Adobe Sign kunnen workflows voor e-handtekeningen worden gebruikt voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

In een standaard Adobe-scenario voor ondertekenen en aanpassen van formulieren vult een gebruiker een adaptief formulier in om een **aanvraag voor een service** in te dienen. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. Serviceprovider controleert de toepassing en gebruikt Adobe Sign om de goedgekeurde toepassing te markeren. Als u vergelijkbare workflows voor elektronische handtekeningen wilt inschakelen, kunt u Adobe Sign met AEM Forms integreren.

Als u Adobe Sign with AEM Forms wilt gebruiken, [integreert u Adobe Sign with AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

#### Adobe Analytics configureren {#configure-adobe-analytics}

AEM Forms is geïntegreerd met Adobe Analytics waarmee u prestatiegegevens voor gepubliceerde formulieren en documenten kunt vastleggen en bijhouden. Het doel van de analyse van deze gegevens is om geïnformeerde beslissingen te nemen op basis van gegevens over de wijzigingen die nodig zijn om formulieren of documenten bruikbaarder te maken.

Zie Analyses en rapporten [configureren als u Adobe Analytics met AEM Forms wilt gebruiken](/help/forms/using/configure-analytics-forms-documents.md).

#### Adobe-doel integreren {#integrate-adobe-target}

Uw klanten zullen waarschijnlijk een formulier verlaten als de ervaring die het biedt, niet aantrekkelijk is. Hoewel het voor de klanten frustrerend is, kan het het steunvolume en de kosten voor uw organisatie ook herstellen. Het is kritiek evenals uitdagend om de juiste klantenervaring te identificeren en te verstrekken die de omrekeningskoers verhoogt. AEM-formulieren vormen de sleutel tot dit probleem.

AEM-formulieren worden geïntegreerd met Adobe Target, een Adobe Marketing Cloud-oplossing, om persoonlijke en boeiende ervaringen van klanten via meerdere digitale kanalen te bieden. Als u Adobe Target wilt gebruiken voor adaptieve formulieren voor A/B-tests, [integreert u Adobe Target met AEM-formulieren](/help/forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

## Volgende stappen {#next-steps}

U hebt een omgeving geconfigureerd voor het gebruik van de mogelijkheden voor gegevensvastlegging in AEM Forms. De volgende stappen in de richting van het gebruik van de mogelijkheid zijn:

* [Uw eerste adaptieve formulier maken](/help/forms/using/create-your-first-adaptive-form.md)
* [Uw eerste PDF-formulier maken](http://www.adobe.com/go/learn_aemforms_designer_quick_start_65)
* [Inleiding tot HTML5-formulieren](/help/forms/using/introduction.md)

