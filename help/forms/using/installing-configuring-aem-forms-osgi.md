---
title: Mogelijkheden voor gegevensvastlegging installeren en configureren
description: Installeer en configureer adaptieve formulieren, PDF forms en HTML5 Forms. Configureer Adobe Analytics en Adobe Target voor adaptieve formulieren om het gebruik van formulieren en doelgebruikers te analyseren op basis van hun profiel.
topic-tags: installing
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
role: Admin, User, Developer
exl-id: 19b5765e-50bc-4fed-8af5-f6bb464516c8
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on OSGi
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1867'
ht-degree: 0%

---

# Mogelijkheden voor gegevensvastlegging installeren en configureren{#install-and-configure-data-capture-capabilities}

## Inleiding {#introduction}

AEM Forms biedt een set formulieren voor het verkrijgen van gegevens van eindgebruikers: adaptieve formulieren, HTML5 Forms en PDF forms. Het programma bevat ook gereedschappen waarmee u alle beschikbare formulieren op een webpagina kunt weergeven, het gebruik van formulieren kunt analyseren en doelgebruikers kunt selecteren op basis van hun profiel. Deze mogelijkheden zijn opgenomen in het invoegpakket voor AEM Forms. Het invoegpakket wordt geïmplementeerd op een Author- of Publish-instantie van AEM.

**Aangepaste vormen:** Deze vormen veranderen verschijning die op de het schermgrootte van het apparaat wordt gebaseerd, betreuren, en interactief in aard. Adaptief Forms kan ook worden geïntegreerd met Adobe Analytics, Adobe Sign en Adobe Target. Zo kunt u op basis van demografie en andere functies persoonlijke formulieren en procesgeoriënteerde ervaringen aan gebruikers aanbieden. U kunt adaptieve formulieren ook integreren met Adobe Sign.

**PDF forms** zijn geschikt voor pixel-perfecte druk en digitale informatie vangen binnen een document van PDF. In de digitale avatar kunt u Adobe Acrobat of Acrobat Reader gebruiken om deze formulieren in te vullen. U kunt deze formulieren hosten op uw website of de portal Formulieren gebruiken om deze formulieren weer te geven op een AEM. U kunt deze formulieren ook als bijlagen naar anderen verzenden. Deze formulieren zijn het meest geschikt voor desktopomgevingen.

**HTML5 Forms** is de browser-vriendelijke versie van PDF forms. HTML5 Forms is geschikt voor omgevingen die geen PDF-plug-ins ondersteunen. Met HTML5 Forms kunnen op XFA gebaseerde formulieren worden weergegeven op mobiele apparaten en desktopbrowsers waarop XFA-gebaseerde PDF niet wordt ondersteund. Deze formulieren zijn het meest geschikt voor tablets en desktopomgevingen.

AEM Forms is een krachtig platform op bedrijfsniveau en het vastleggen van gegevens (adaptieve formulieren, PDF forms en HTML5 Forms) is slechts één van de mogelijkheden van AEM Forms. Voor de volledige lijst van mogelijkheden, zie [ Inleiding aan AEM Forms ](/help/forms/using/introduction-aem-forms.md).

## Implementatietopologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. U hebt slechts minimaal één AEM auteur en AEM Publish-instantie nodig om AEM Forms-mogelijkheden voor gegevensvastlegging uit te voeren. De volgende topologie wordt gesuggereerd om AEM Forms AEM Forms gegevens in werking te stellen vangt mogelijkheden. Voor gedetailleerde informatie over de topologie, zie [ Architectuur en plaatsingstopologieën voor AEM Forms ](/help/forms/using/aem-forms-architecture-deployment.md).

![ geadviseerd-topologie ](assets/recommended-topology.png)

## Systeemvereisten {#system-requirements}

Voordat u de mogelijkheid voor gegevensvastlegging van AEM Forms gaat installeren en configureren, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Voor een gedetailleerde lijst van gesteunde hardware en software, zie [ technische vereisten ](/help/sites-deploying/technical-requirements.md).

* Het installatiepad van de AEM-instantie bevat geen witruimten.
* Er wordt een AEM-instantie uitgevoerd. Voor de gebruikers van Vensters, installeer de AEM instantie op opgeheven wijze. In AEM terminologie is een &quot;instantie&quot; een kopie van AEM die op een server in de auteur- of publicatiemodus wordt uitgevoerd. U vereist minstens twee [ AEM instanties (één Auteur en één Publish) ](/help/sites-deploying/deploy.md) om de gegevens van AEM Forms in werking te stellen vangen mogelijkheden:

   * **Auteur**: Een AEM die instantie wordt gebruikt om, inhoud tot stand te brengen te uploaden en uit te geven en de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Publish**: Een AEM instantie die de gepubliceerde inhoud aan het publiek over Internet of een intern netwerk dient.

* Er wordt voldaan aan de geheugenvereisten. AEM Forms-add-on-pakket vereist:

   * 15 GB tijdelijke ruimte voor Microsoft Windows-installaties.
   * 6 GB tijdelijke ruimte voor UNIX-installaties.

* De replicatie en omgekeerde replicatie voor de auteur en publiceer instanties worden geplaatst. Voor details, zie [ Replicatie ](/help/sites-deploying/replication.md).
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

* Installeer [ Microsoft Visual Studio 2019 Redistributable met 32 bits ](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170).


## AEM Forms-invoegtoepassing installeren {#install-aem-forms-add-on-package}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Het pakket bevat AEM Forms-gegevensvastlegging en andere mogelijkheden. Voer de volgende stappen uit om het invoegpakket te installeren:

1. Open [ Distributie van de Software ](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]** :
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
1. Open [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]** .

   U kunt het pakket via de directe verbinding ook downloaden die in het [ wordt vermeld versies van AEM Forms ](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) artikel.
1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM opnieuw te starten. **begin niet onmiddellijk de server opnieuw.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer in het `[AEM-Installation-Directory]/crx-quickstart/logs/error.log` -bestand worden weergegeven en het logbestand stabiel is.

   >[!NOTE]
   >
   > Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

1. Herhaal stap 1-7 voor alle auteur- en Publish-instanties.

### (Vensters slechts) Automatische installatie van Visual Studio redistributables {#automatic-installation-visual-studio-redistributables}

Als u een AEM instantie op opgeheven wijze installeert, zijn redistributables met 32 bits van Visual Studio automatisch geïnstalleerd tijdens de installatie van het toe:voegen-op pakket van AEM Forms.

Om te evalueren of Visual Studio redistributables automatisch geïnstalleerd is, open het `error.log` dossier beschikbaar bij de `/crx-repository/logs/` folder. De logboeken bevatten het volgende bericht:

`Redist <service name> already installed on system, will not attempt re-installation`

Als redistributables er niet in slagen te installeren, omvatten de logboeken het volgende bericht:

`Current user does not have elevated privileges, aborting installation of redist <service name>`

Start de AEM server opnieuw op, installeer AEM in de verhoogde modus en installeer vervolgens het AEM Forms-invoegpakket.

Als de machtigingscontrole ontbreekt, omvatten de logboeken het volgende bericht:

`Privilege escalation check failed with error: <error message>`

## Post-installatieconfiguraties {#post-installation-configurations}

AEM Forms heeft een paar verplichte en optionele configuraties. De verplichte configuraties omvatten het vormen bibliotheken BouncyCastle en serialization agent. De optionele configuraties zijn het configureren van dispatcher, Forms Portal, Adobe Sign, Adobe Analytics en Adobe Target.

### Verplichte configuraties na installatie {#mandatory-post-installation-configurations}

#### RSA- en BouncyCastle-bibliotheken configureren  {#configure-rsa-and-bouncycastle-libraries}

Voer de volgende stappen uit op alle instanties van de Auteur en van Publish om de bibliotheken te laars afgevaardigde:

1. Stop de onderliggende AEM instantie.
1. Open het `[AEM installation directory]\crx-quickstart\conf\sling.properties` -bestand om het te bewerken.

   Als u `[AEM installation directory]\crx-quickstart\bin\start.bat` hebt gebruikt om AEM te starten, bewerkt u de eigenschappen sling.property op `[AEM_root]\crx-quickstart\` .

1. Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```shell
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*  
   ```

1. Sla het bestand op, sluit het en start het AEM.
1. Herhaal stap 1-4 voor alle auteur- en Publish-instanties.

#### Vorm de rangschikkingsagent {#configure-the-serialization-agent}

Voer de volgende stappen uit op alle instanties van de Auteur en van Publish om het pakket aan de lijst van gewenste personen toe te voegen:

1. Open AEM Configuration Manager in een browservenster. De standaard-URL is `https://'[server]:[port]'/system/console/configMgr` .
1. Onderzoek naar **com.adobe.cq.deserfw.impl.DeserializationFirewallImpl.name** en open de configuratie.
1. Voeg het {**pakket 0} sun.util.endar aan het** lijst van gewenste personen **gebied toe.** Klik **sparen**.
1. Herhaal stap 1-3 op alle instanties van Auteur en van Publish.

### Optionele configuraties na installatie {#optional-post-installation-configurations}

#### Dispatcher configureren {#configure-dispatcher}

Dispatcher is een Adobe Experience Manager-programma voor caching en/of taakverdeling dat kan worden gebruikt in combinatie met een webserver op bedrijfsniveau. Als u [ Dispatcher ](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) gebruikt, dan voer de volgende configuraties voor AEM Forms uit:

1. Toegang voor AEM Forms configureren:

   Open het bestand dispatcher.any voor bewerking. Navigeer naar de filtersectie en voeg het volgende filter toe aan de filtersectie:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Sla het bestand op en sluit het. Voor gedetailleerde informatie over filters, zie {de documentatie van 0} Dispatcher [&#128279;](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Configureer de referentiefilterservice:

   Meld u als beheerder aan bij Apache Felix. De standaard-URL van het configuratiebeheer is `https://[server]:[port_number]/system/console/configMgr` . In het **menu van Configuraties**, selecteer de **Apache het Verdelen van de Filter van de Verwijzing** optie. In het Allow gebied van Gastheren, ga gastheernaam van de verzender in om het als verwijzer toe te staan en klik **sparen**. De opmaak van de vermelding is `https://[server]:[port]` .

#### Cache configureren {#configure-cache}

Caching is een mechanisme om gegevenstoegang te verkorten, latentie te verminderen, en input/output (I/O) snelheden te verbeteren. In de cache van adaptieve formulieren worden alleen de HTML-inhoud en de JSON-structuur van een adaptief formulier opgeslagen zonder dat vooraf ingevulde gegevens worden opgeslagen. Hierdoor wordt de tijd die nodig is om een adaptief formulier te genereren, verkort.

* Bij het gebruiken van het adaptieve vormengeheime voorgeheugen, gebruik [ AEM Dispatcher ](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) om cliëntbibliotheken (CSS en JavaScript) van een adaptieve vorm in het voorgeheugen onder te brengen.
* Zorg tijdens het ontwikkelen van aangepaste componenten dat de cache van adaptieve formulieren uitgeschakeld blijft op de server die voor ontwikkeling wordt gebruikt.

Voer de volgende stappen uit om de cache voor adaptieve formulieren te configureren:

1. Ga naar AEM manager van de Webconsoleconfiguratie in https://&#39;[ server ]:[ haven ]&#39;/system/console/configMgr.
1. Klik **Aangepaste Vorm en Interactieve Configuratie van het Kanaal van de Communicatie van het Web** om zijn configuratiewaarden uit te geven. In geef de dialoog van de configuratiewaarden uit, specificeer het maximumaantal vormen of documenten een geval van de server van AEM Forms in het **Aantal van het AanpassingsForms** gebied in cache kan plaatsen. De standaardwaarde is 100. Klik **sparen**.

   >[!NOTE]
   >
   >Om het geheime voorgeheugen onbruikbaar te maken, plaats de waarde op het Aantal van het AanpassingsForms gebied aan **0**. De cache wordt opnieuw ingesteld en alle formulieren en documenten worden uit de cache verwijderd wanneer u de cachemonfiguratie uitschakelt of wijzigt.

#### SSL-communicatie configureren voor formuliergegevensmodel {#configure-ssl-communcation-for-form-data-model}

U kunt SSL-communicatie inschakelen voor het formuliergegevensmodel. Als u SSL-communicatie wilt inschakelen voor het formuliergegevensmodel, voegt u certificaten toe aan het Java Trust Store van alle exemplaren voordat u een AEM Forms-exemplaar start. U kunt de onderstaande opdracht uitvoeren om de certificaten toe te voegen: &quot;

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

#### Adobe Sign configureren {#configure-adobe-sign}

Adobe Sign maakt workflows voor e-handtekeningen mogelijk voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

In een typisch Adobe Sign en adaptief vormenscenario, vult een gebruiker een adaptieve vorm aan **van toepassing is voor de dienst**. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. De dienstverlener controleert de toepassing en gebruikt Adobe Sign om de goedgekeurde toepassing te merken. Als u vergelijkbare workflows voor elektronische handtekeningen wilt inschakelen, kunt u Adobe Sign integreren met AEM Forms.

Om Adobe Sign met AEM Forms te gebruiken, [ integreer Adobe Sign met AEM Forms ](/help/forms/using/adobe-sign-integration-adaptive-forms.md).

#### Adobe Analytics configureren {#configure-adobe-analytics}

AEM Forms is geïntegreerd met Adobe Analytics waarmee u prestatiegegevens voor gepubliceerde formulieren en documenten kunt vastleggen en bijhouden. Het doel van de analyse van deze gegevens is om geïnformeerde beslissingen te nemen op basis van gegevens over de wijzigingen die nodig zijn om formulieren of documenten bruikbaarder te maken.

Om Adobe Analytics met AEM Forms te gebruiken, zie [ het Vormen analyses en rapporten ](/help/forms/using/configure-analytics-forms-documents.md).

#### Adobe Target integreren {#integrate-adobe-target}

Uw klanten zullen waarschijnlijk een formulier verlaten als de ervaring die het biedt, niet aantrekkelijk is. Hoewel het voor de klanten frustrerend is, kan het het steunvolume en de kosten voor uw organisatie ook herstellen. Het is kritiek en uitdagend om de juiste klantenervaring te identificeren en te verstrekken die de omzettingssnelheid verhoogt. AEM formulieren vormen de sleutel tot dit probleem.

AEM formulieren kunnen worden geïntegreerd met Adobe Target, een Adobe Marketing Cloud-oplossing, om persoonlijke en aantrekkelijke klantervaringen te bieden via meerdere digitale kanalen. Om Adobe Target aan A/B te gebruiken test adaptieve vormen, [ integreer Adobe Target met AEM Forms ](/help/forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

## Volgende stappen {#next-steps}

U hebt een omgeving geconfigureerd voor het gebruik van AEM Forms-mogelijkheden voor het vastleggen van gegevens. De volgende stappen in de richting van het gebruik van de mogelijkheid zijn:

* [Uw eerste adaptieve formulier maken](/help/forms/using/create-your-first-adaptive-form.md)
* [ creeer uw eerste vorm van PDF ](https://www.adobe.com/go/learn_aemforms_designer_quick_start_65)
* [Inleiding tot HTML5 Forms](/help/forms/using/introduction.md)
