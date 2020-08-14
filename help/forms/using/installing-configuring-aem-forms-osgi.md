---
title: Mogelijkheden voor gegevensvastlegging installeren en configureren
seo-title: Mogelijkheden voor gegevensvastlegging installeren en configureren
description: Aangepaste formulieren, PDF forms en HTML5 Forms installeren en configureren. Configureer Adobe Analytics en Adobe Target voor adaptieve formulieren om het gebruik van formulieren en doelgebruikers te analyseren op basis van hun profiel.
seo-description: Aangepaste formulieren, PDF forms en HTML5 Forms installeren en configureren. Configureer Adobe Analytics en Adobe Target voor adaptieve formulieren om het gebruik van formulieren en doelgebruikers te analyseren op basis van hun profiel.
uuid: 5d49032a-4dea-4f21-9dad-a7a30c5872ea
topic-tags: installing
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: dfc473eb-6091-4f5d-a5a0-789972c513a9
docset: aem65
translation-type: tm+mt
source-git-commit: 24d817bf8e52136980783ef14cea8531519ee622
workflow-type: tm+mt
source-wordcount: '1912'
ht-degree: 0%

---


# Mogelijkheden voor gegevensvastlegging installeren en configureren{#install-and-configure-data-capture-capabilities}

## Inleiding {#introduction}

AEM Forms biedt een set formulieren voor het verkrijgen van gegevens van eindgebruikers: adaptieve formulieren, HTML5 Forms en PDF forms. Het programma bevat ook gereedschappen waarmee u alle beschikbare formulieren op een webpagina kunt weergeven, het gebruik van formulieren kunt analyseren en doelgebruikers kunt selecteren op basis van hun profiel. Deze mogelijkheden zijn opgenomen in het invoegpakket voor AEM Forms. Het invoegpakket wordt geïmplementeerd op een instantie Auteur of Publiceren van AEM.

**Aangepaste formulieren:** Deze formulieren veranderen de weergave op basis van de schermgrootte van het apparaat, zijn aantrekkelijk en interactief van aard. Adaptief Forms kan ook worden geïntegreerd met Adobe Analytics, Adobe Sign en Adobe Target. Hierdoor kunt u op basis van demografie en andere functies persoonlijke formulieren en procesgeoriënteerde ervaringen aan gebruikers aanbieden. U kunt adaptieve formulieren ook integreren met Adobe Sign.

**PDF forms** zijn geschikt voor pixelperfect afdrukken en het vastleggen van digitale informatie in een PDF-document. In de digitale avatar kunt u Adobe Acrobat of Acrobat Reader gebruiken om deze formulieren in te vullen. U kunt deze formulieren hosten op uw website of de portal Formulieren gebruiken om deze formulieren weer te geven op een AEM site. U kunt deze formulieren ook als bijlagen naar anderen verzenden. Deze formulieren zijn het meest geschikt voor desktopomgevingen.

**HTML5 Forms** is de browservriendelijke versie van PDF forms. HTML5 Forms is geschikt voor omgevingen die geen ondersteuning bieden voor PDF-plug-ins. Met HTML5 Forms kunnen op XFA gebaseerde formulieren worden weergegeven op mobiele apparaten en desktopbrowsers waarop XFA-gebaseerde PDF niet wordt ondersteund. Deze formulieren zijn het meest geschikt voor tablets en desktopomgevingen.

AEM Forms is een krachtig platform op bedrijfsniveau en het vastleggen van gegevens (adaptieve formulieren, PDF forms en HTML5 Forms) is slechts een van de mogelijkheden van AEM Forms. Zie [Introductie tot AEM Forms](/help/forms/using/introduction-aem-forms.md)voor de volledige lijst met mogelijkheden.

## Implementatietopologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. U hebt slechts minimaal één instantie van AEM-auteur en AEM-publicatie nodig om AEM Forms-mogelijkheden voor het vastleggen van gegevens uit te voeren. De volgende topologie wordt gesuggereerd om AEM Forms AEM Forms gegevens in werking te stellen vangt mogelijkheden. Voor gedetailleerde informatie over de topologie, zie [Architectuur en plaatsingstopologieën voor AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![aanbevolen topologie](assets/recommended-topology.png)

## Systeemvereisten {#system-requirements}

Voordat u de mogelijkheid voor gegevensvastlegging van AEM Forms gaat installeren en configureren, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Raadpleeg de [technische vereisten](/help/sites-deploying/technical-requirements.md)voor een gedetailleerde lijst met ondersteunde hardware en software.

* Het installatiepad van de AEM-instantie bevat geen witruimten.
* Er wordt een AEM-instantie uitgevoerd. Voor de gebruikers van Vensters, installeer de AEM instantie op opgeheven wijze. In AEM terminologie is een &quot;instantie&quot; een kopie van AEM die op een server in de auteur- of publicatiemodus wordt uitgevoerd. U hebt minstens twee [AEM instanties (één auteur en één publiceer)](/help/sites-deploying/deploy.md) nodig om AEM Forms-mogelijkheden voor gegevensvastlegging te kunnen uitvoeren:

   * **Auteur**: Een AEM die wordt gebruikt om inhoud te maken, te uploaden en te bewerken en om de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Publiceren**: Een AEM instantie die de gepubliceerde inhoud via internet of een intern netwerk aan het publiek levert.

* Er wordt voldaan aan de geheugenvereisten. AEM Forms-add-on-pakket vereist:

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

## AEM Forms-invoegtoepassing installeren {#install-aem-forms-add-on-package}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Het pakket bevat AEM Forms-gegevensvastlegging en andere mogelijkheden. Voer de volgende stappen uit om het invoegpakket te installeren:

1. Open [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Tik **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In het **[!UICONTROL Filters]** gedeelte:
   1. Selecteer een optie **[!UICONTROL Forms]** in de **[!UICONTROL Solution]** vervolgkeuzelijst.
   2. Selecteer de versie en typ voor het pakket. U kunt de **[!UICONTROL Search Downloads]** optie ook gebruiken om de resultaten te filteren.
1. Tik op de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en tik op **[!UICONTROL Download]**.
1. Open [Package Manager](https://docs.adobe.com/content/help/en/experience-manager-65/administering/contentmanagement/package-manager.html) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik **[!UICONTROL Install]**.

   U kunt het pakket ook downloaden via de directe koppeling in het [AEM Forms-releaseartikel](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) .
1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM opnieuw te starten. **Start de server niet onmiddellijk opnieuw.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED in het `[AEM-Installation-Directory]/crx-quickstart/logs/error.log` bestand zijn gestopt en het logbestand stabiel is.
1. Herhaal stap 1-7 voor alle instanties Auteur en Publiceren.

### (Vensters slechts) Automatische installatie van Visual Studio redistributables {#automatic-installation-visual-studio-redistributables}

Als u een AEM instantie op opgeheven wijze installeert, zijn de ontbrekende Visual Studio redistributables automatisch geïnstalleerd tijdens de installatie van AEM Forms toe:voegen-op pakket.

Om te evalueren als Visual Studio redistributables automatisch geïnstalleerd is, open het `error.log` dossier beschikbaar bij de `/crx-repository/logs/` folder. De logboeken bevatten het volgende bericht:

`Redist <service name> already installed on system, will not attempt re-installation`

Als redistributables er niet in slagen te installeren, omvatten de logboeken het volgende bericht:

`Current user does not have elevated privileges, aborting installation of redist <service name>`

Start de AEM server opnieuw op, installeer AEM in de verhoogde modus en installeer vervolgens het AEM Forms-invoegpakket.

Als de machtigingscontrole ontbreekt, omvatten de logboeken het volgende bericht:

`Privilege escalation check failed with error: <error message>`

## Configuratie na installatie {#post-installation-configurations}

AEM Forms heeft een paar verplichte en optionele configuraties. De verplichte configuraties omvatten het vormen bibliotheken BouncyCastle en serialization agent. De optionele configuraties zijn het configureren van dispatcher, Forms Portal, Adobe Sign, Adobe Analytics en Adobe Target.

### Verplichte configuraties na installatie {#mandatory-post-installation-configurations}

#### RSA- en BouncyCastle-bibliotheken configureren  {#configure-rsa-and-bouncycastle-libraries}

Voer de volgende stappen op alle Auteur uit en publiceer instanties om de bibliotheken op te starten afvaardigen:

1. Stop de onderliggende AEM instantie.
1. Open het `[AEM installation directory]\crx-quickstart\conf\sling.properties` bestand om het te bewerken.

   Als u eerst `[AEM installation directory]\crx-quickstart\bin\start.bat` de AEM hebt gestart, bewerkt u de eigenschap sling.properties op `[AEM_root]\crx-quickstart\`.

1. Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```shell
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. Sla het bestand op, sluit het en start het AEM.
1. Herhaal stap 1-4 voor alle instanties Auteur en Publiceren.

#### Vorm de rangschikkingsagent {#configure-the-serialization-agent}

Voer de volgende stappen uit op alle instanties Auteur en Publish om het pakket aan de lijst van gewenste personen toe te voegen:

1. Open AEM Configuration Manager in een browservenster. De standaard-URL is `https://'[server]:[port]'/system/console/configMgr`.
1. Zoek naar **com.adobe.cq.deserfw.impl.DeserializationFirewallImpl.name** en open de configuratie.
1. Voeg het pakket **sun.util.agenda** toe aan het veld **lijst van gewenste personen** . Click **Save**.
1. Herhaal stap 1-3 voor alle instanties Auteur en Publiceren.

### Optionele configuraties na installatie {#optional-post-installation-configurations}

#### Dispatcher configureren {#configure-dispatcher}

Dispatcher is een programma voor het in cache plaatsen en taakverdeling voor AEM. AEM Dispatcher helpt ook AEM server tegen aanvallen te beschermen. U kunt de veiligheid van uw AEM instantie verhogen door Dispatcher samen met een onderneming-klasse Webserver te gebruiken. Als u [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html)gebruikt, voert u de volgende configuraties uit voor AEM Forms:

1. Toegang voor AEM Forms configureren:

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
1. Klik de **Aangepaste Vorm en de Interactieve Configuratie** van het Kanaal van de Communicatie van het Web om zijn configuratiewaarden uit te geven. Geef in het dialoogvenster Configuratiewaarden bewerken het maximumaantal formulieren of documenten op dat een instantie van de AEM Forms-server in cache kan plaatsen in het veld **Aantal adaptieve Forms** . De standaardwaarde is 100. Click **Save**.

   >[!NOTE]
   >
   >Als u de cache wilt uitschakelen, stelt u de waarde in het veld Aantal adaptieve Forms in op **0**. De cache wordt opnieuw ingesteld en alle formulieren en documenten worden uit de cache verwijderd wanneer u de cachemonfiguratie uitschakelt of wijzigt.

#### SSL-communicatie configureren voor formuliergegevensmodel {#configure-ssl-communcation-for-form-data-model}

U kunt SSL-communicatie inschakelen voor het formuliergegevensmodel. Als u SSL-communicatie wilt inschakelen voor het formuliergegevensmodel, voegt u certificaten toe aan het Java Trust Store van alle exemplaren voordat u een AEM Forms-exemplaar start. U kunt de onderstaande opdracht uitvoeren om de certificaten toe te voegen: &quot;

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

#### Adobe Sign configureren {#configure-adobe-sign}

Adobe Sign maakt workflows voor e-handtekeningen mogelijk voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

In een standaard Adobe Sign- en adaptief formulierscenario vult een gebruiker een adaptief formulier om een **aanvraag voor een service** in te dienen. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. De serviceprovider controleert de toepassing en gebruikt Adobe Sign om de goedgekeurde toepassing te markeren. Als u vergelijkbare workflows voor elektronische handtekeningen wilt inschakelen, kunt u Adobe Sign integreren met AEM Forms.

Als u Adobe Sign wilt gebruiken met AEM Forms, [integreert u Adobe Sign met AEM Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

#### Adobe Analytics configureren {#configure-adobe-analytics}

AEM Forms is geïntegreerd met Adobe Analytics waarmee u prestatiegegevens voor gepubliceerde formulieren en documenten kunt vastleggen en bijhouden. Het doel van de analyse van deze gegevens is om geïnformeerde beslissingen te nemen op basis van gegevens over de wijzigingen die nodig zijn om formulieren of documenten bruikbaarder te maken.

Zie Analyses en rapporten [](/help/forms/using/configure-analytics-forms-documents.md)configureren voor gebruik van Adobe Analytics met AEM Forms.

#### Adobe Target integreren {#integrate-adobe-target}

Uw klanten zullen waarschijnlijk een formulier verlaten als de ervaring die het biedt, niet aantrekkelijk is. Hoewel het voor de klanten frustrerend is, kan het het steunvolume en de kosten voor uw organisatie ook herstellen. Het is kritiek evenals uitdagend om de juiste klantenervaring te identificeren en te verstrekken die de omrekeningskoers verhoogt. AEM formulieren vormen de sleutel tot dit probleem.

AEM formulieren kunnen worden geïntegreerd met Adobe Target, een Adobe Marketing Cloud-oplossing, om persoonlijke en aantrekkelijke klantervaringen te bieden via meerdere digitale kanalen. Als u adaptieve formulieren wilt gebruiken voor Adobe Target to A/B-tests, [integreert u Adobe Target met AEM Forms](/help/forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

## Volgende stappen {#next-steps}

U hebt een omgeving geconfigureerd voor het gebruik van AEM Forms-mogelijkheden voor het vastleggen van gegevens. De volgende stappen in de richting van het gebruik van de mogelijkheid zijn:

* [Uw eerste adaptieve formulier maken](/help/forms/using/create-your-first-adaptive-form.md)
* [Uw eerste PDF-formulier maken](http://www.adobe.com/go/learn_aemforms_designer_quick_start_65)
* [Inleiding tot HTML5 Forms](/help/forms/using/introduction.md)

