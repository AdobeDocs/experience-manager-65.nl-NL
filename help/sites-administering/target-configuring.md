---
title: De integratie handmatig configureren met Adobe Target
seo-title: De integratie handmatig configureren met Adobe Target
description: Leer hoe u de integratie met Adobe Target handmatig kunt configureren.
seo-description: Leer hoe u de integratie met Adobe Target handmatig kunt configureren.
uuid: 0bb76a65-f981-4cc5-bee8-5feb3297137c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 20c8eb1d-5847-4902-b7d3-4c3286423b46
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd

---


# De integratie handmatig configureren met Adobe Target {#manually-configuring-the-integration-with-adobe-target}

U kunt de configuraties van de wizard voor aanmelding wijzigen die u hebt gemaakt tijdens het gebruik van de wizard, of u kunt de configuratie handmatig integreren met Adobe Target zonder de wizard te gebruiken.

## De configuratie van de wizard Inschakelen wijzigen {#modifying-the-opt-in-wizard-configurations}

De [Opt-in tovenaar](/help/sites-administering/opt-in.md) die AEM met Adobe Target [](/help/sites-administering/target.md) integreert leidt automatisch tot een de wolkenconfiguratie van het Doel genoemd Provisioned de Configuratie van het Doel. De tovenaar creeert ook een kader van het Doel voor de wolkenconfiguratie genoemd Provisioned Kader van het Doel. U kunt de eigenschappen van de cloudconfiguratie en het framework desgewenst wijzigen.

U kunt Adobe Target ook configureren om Adobe Target te gebruiken als rapportagebron bij het toewijzen van inhoud door de Configuratie van de cloud voor A4T Analytics te configureren.

Ga naar **Cloud Services** via **Extra** > **Implementatie** > **Cloud** om de cloudconfiguratie en het framework te zoeken. ([http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html))Klik of tik onder Adobe Target op **Configuraties** tonen.

### Eigenschappen van provisioned Target Configuration {#provisioned-target-configuration-properties}

De volgende bezitswaarden worden gebruikt in de Provisioned de wolkenconfiguratie van de Configuratie van het Doel die de Opt-in tovenaar creeert:

* **** Clientcode: Zoals ingevoerd in de wizard Inschakelen.
* **** E-mail: Zoals ingevoerd in de wizard Inschakelen.
* **** Wachtwoord: Zoals ingevoerd in de wizard Inschakelen.
* **** API-type: REST
* **** Segmenten synchroniseren met Adobe Target: Geselecteerd.

* **** Clientbibliotheek: mbox.js.
* **** DTM gebruiken om clientbibliotheek te leveren: Niet geselecteerd. Selecteer deze optie als u het bestand mbox.js of AT.js [host met DTM](/help/sites-administering/dtm.md) of een ander tagbeheersysteem. Adobe raadt u aan DTM te gebruiken in plaats van AEM om de bibliotheek te leveren.

* **** Aangepaste mbox.js: Niets specificeerde zodat het standaard mbox.js- dossier wordt gebruikt. Geef het bestand mbox.js op dat u wilt gebruiken. Wordt alleen weergegeven als u mbox.js hebt geselecteerd.
* **** Aangepaste AT.js: Niets specificeerde zodat het standaardAT.js- dossier wordt gebruikt. Geef een aangepast AT.js-bestand op dat u wilt gebruiken. Wordt alleen weergegeven als u AT.js hebt geselecteerd.

>[!NOTE]
>
>In AEM 6.3 kunt u het doelbibliotheekbestand [AT.JS](https://marketing.adobe.com/resources/help/en_US/target/ov2/c_target-atjs-implementation.html)selecteren. Dit is een nieuwe implementatiebibliotheek voor Adobe Target die is ontworpen voor zowel gangbare webimplementaties als toepassingen die uit één pagina bestaan.
>
>AT.js biedt verschillende verbeteringen aan ten opzichte van de bibliotheek mbox.js:
>
>* Verbeterde laadtijden voor webimplementaties
>* Verbeterde beveiliging
>* Betere implementatieopties voor toepassingen van één pagina
>* AT.js bevat de componenten die in target.js inbegrepen waren, zodat is er niet meer een vraag aan target.js
>
>
Zie Opmerkingen bij de release [Target](https://marketing.adobe.com/resources/help/en_US/target/rn/201604.html) voor meer informatie.

### Voorziene eigenschappen van doelframework {#provisioned-target-framework-properties}

Het provisioned Kader van het Doel dat de Opt-in tovenaar creeert wordt gevormd om contextgegevens van de opslag van de Gegevens van het Profiel te verzenden. De pagina- en geslachtsgegevensitems van de winkel worden standaard naar Target verzonden. Uw oplossing vereist waarschijnlijk extra parameters om worden verzonden.

![chlimage_1-158](assets/chlimage_1-158.png)

U kunt het kader vormen om extra contextinformatie naar Doel te verzenden zoals die in het [Toevoegen van een Kader](/help/sites-administering/target-configuring.md#adding-a-target-framework)van het Doel wordt beschreven.

### Configuratie van de cloud voor A4T Analytics configureren {#configuring-a-t-analytics-cloud-configuration}

U kunt Adobe Target zodanig configureren dat Adobe Analytics wordt gebruikt als de bron voor rapportage wanneer u inhoud als doel instelt.

Hiervoor moet u opgeven welke A4T-cloudconfiguratie u wilt gebruiken om uw Adobe Target-cloudconfiguratie te verbinden met:

1. Ga naar **Cloud Services** via het **AEM-logo** > **Gereedschappen** > **Implementatie** > **Cloud Services**.
1. Klik in de sectie **Adobe Target** op **Nu** configureren.
1. Maak opnieuw verbinding met uw Adobe Target-configuratie.
1. Selecteer het framework in het keuzemenu Configuratie **van de cloud voor** A4T Analytics Cloud.

   >[!NOTE]
   >
   >Alleen analytische configuraties die zijn ingeschakeld voor A4T zijn beschikbaar.
   >
   >Wanneer het vormen van A4T met AEM, kunt u een verwijzing van de Configuratie zien ontbrekende ingang. Ga als volgt te werk om het analyseframework te kunnen selecteren:
   >
   >1. Ga naar **Gereedschappen** > **Algemeen** > **CRXDE Lite**.
   1. Navigeer naar **/libs/cq/analytics/components/testandtargetPage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig**
   1. Stel de eigenschap **disable** in op **false**.
   1. Tik of klik op **Alles** opslaan.


   ![chlimage_1-159](assets/chlimage_1-159.png)

   Click **OK**. Wanneer u inhoud met Adobe Target als doel instelt, kunt u uw rapportbron [](/help/sites-authoring/content-targeting-touch.md)selecteren.

## Handmatig integreren met Adobe Target {#manually-integrating-with-adobe-target}

Handmatig integreren met Adobe Target in plaats van de wizard Aanmelden te gebruiken.

>[!NOTE]
Het doelbibliotheekbestand, [AT.JS](https://marketing.adobe.com/resources/help/en_US/target/ov2/c_target-atjs-implementation.html), is een nieuwe implementatiebibliotheek voor Adobe Target die is ontworpen voor zowel gangbare webimplementaties als toepassingen die uit één pagina bestaan. Adobe raadt u aan AT.js te gebruiken in plaats van mbox.js als de clientbibliotheek.
AT.js biedt verschillende verbeteringen aan ten opzichte van de bibliotheek mbox.js:
* Verbeterde laadtijden voor webimplementaties
* Verbeterde beveiliging
* Betere implementatieopties voor toepassingen van één pagina
* AT.js bevat de componenten die in target.js inbegrepen waren, zodat is er niet meer een vraag aan target.js

Zie Opmerkingen bij de release [Target](https://marketing.adobe.com/resources/help/en_US/target/rn/201604.html) voor meer informatie.
U kunt AT.js of mbox.js in het de bibliotheekdrop-down menu van de **Cliënt** selecteren.

### Een doelcloud-configuratie maken {#creating-a-target-cloud-configuration}

Maak een doelwolkenconfiguratie zodat AEM kan communiceren met Adobe Target. Als u de configuratie wilt maken, geeft u de Adobe Target-clientcode en de gebruikersgegevens op.

U kunt de doelwolkenconfiguratie slechts eenmaal maken omdat u de configuratie aan veelvoudige campagnes kunt associëren AEM. Als u meerdere Adobe Target-clientcodes hebt, maakt u één configuratie voor elke clientcode.

U kunt de wolkenconfiguratie vormen om segmenten van Adobe Target te synchroniseren. Als u synchronisatie inschakelt, worden segmenten op de achtergrond geïmporteerd van Target zodra de cloudconfiguratie is opgeslagen.

Gebruik de volgende procedure om een doelwolkenconfiguratie in AEM tot stand te brengen:

1. Ga naar **Cloud Services** via het **AEM-logo** > **Gereedschappen** > **Implementatie** > **Cloud Services**. ([http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html))

   De overzichtspagina van **Adobe Marketing Cloud** wordt geopend.

1. Klik in de sectie **Adobe Target** op **Nu** configureren.
1. In het dialoogvenster **Configuratie** maken:

   1. Geef de configuratie een **Titel**.
   1. Selecteer de sjabloon **Adobe Target Configuration** .
   1. Klik op **Maken**.
   Het dialoogvenster Bewerken wordt geopend.

   ![chlimage_1-160](assets/chlimage_1-160.png)

   >[!NOTE]
   Wanneer het vormen van A4T met AEM, kunt u een verwijzing van de Configuratie zien ontbrekende ingang. Ga als volgt te werk om het analyseframework te kunnen selecteren:
   1. Ga naar **Gereedschappen** > **Algemeen** > **CRXDE Lite**.
   1. Navigeer naar **/libs/cq/analytics/components/testandtargetPage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig**
   1. Stel de eigenschap **disable** in op **false**.
   1. Tik of klik op **Alles** opslaan.


1. Geef in het dialoogvenster waarden op voor deze eigenschappen.

   * **Clientcode**: De clientcode van de doelaccount
   * **E-mail**: het e-mailadres voor de doelaccount.
   * **Wachtwoord**: het wachtwoord voor de doelaccount.
   * **API-type**: REST of XML
   * **A4T Analytics Cloud Configuration**: Selecteer de de wolkenconfiguratie van de Analyse die voor de doelstellingen en metriek van de doelactiviteit wordt gebruikt. Dit is nodig als u Adobe Analytics als bron voor rapportage gebruikt wanneer u inhoud als doel instelt. Als u uw wolkenconfiguratie niet ziet, zie nota in het [Vormen van de Cloud van A4T Analytics Configuratie](#configuring-a-t-analytics-cloud-configuration).

   * **** Gebruik nauwkeurige gericht: Dit selectievakje is standaard ingeschakeld. Als deze optie is geselecteerd, wacht de configuratie van de cloudservice tot de context is geladen voordat inhoud wordt geladen. Zie het volgende.
   * **** Segmenten synchroniseren met Adobe Target: Selecteer deze optie als u segmenten die in Doel zijn gedefinieerd, wilt downloaden en in AEM wilt gebruiken. U moet deze optie selecteren wanneer het bezit van het Type API REST is, omdat de gealigneerde segmenten niet worden gesteund en u altijd segmenten van Doel moet gebruiken. (De AEM-term &#39;segment&#39; komt overeen met de doelterm &#39;publiek&#39;.)
   * **** Clientbibliotheek: Selecteer of u de clientbibliotheek mbox.js of AT.js wilt.
   * **Gebruik DTM om de clientbibliotheek** te leveren - Selecteer deze optie als u AT.js of mbox.js van DTM of een ander systeem voor tagbeheer wilt gebruiken. U moet de DTM-integratie [](/help/sites-administering/dtm.md) configureren om deze optie te gebruiken. Adobe raadt u aan DTM te gebruiken in plaats van AEM om de bibliotheek te leveren.
   * **Aangepaste mbox.js**: Laat leeg als u het vak DTM hebt ingeschakeld of als u de standaard mbox.js wilt gebruiken. U kunt ook uw aangepaste mbox.js uploaden. Wordt alleen weergegeven als u mbox.js hebt geselecteerd.
   * **Aangepaste AT.js**: Laat leeg als u het vak DTM hebt ingeschakeld of als u de standaard AT.js wilt gebruiken. U kunt ook uw aangepaste AT.js uploaden. Wordt alleen weergegeven als u AT.js hebt geselecteerd.
   >[!NOTE]
   Als u zich aanmeldt bij de configuratietovenaar van Adobe Target, wordt de functie voor nauwkeurige oriëntatie standaard ingeschakeld.
   Nauwkeurige het richten betekent dat de configuratie van de wolkendienst op de context wacht te laden alvorens inhoud te laden. Hierdoor kan het, in termen van prestaties, nauwkeuriger richten tot een paar milliseconde vertraging leiden alvorens inhoud te laden.
   Nauwkeurige het richten wordt altijd toegelaten op de auteursinstantie. Op de publicatie-instantie kunt u er echter voor kiezen om nauwkeurig afstemmen globaal uit te schakelen door het vinkje naast Accurate Targeting in de cloudserviceconfiguratie (**http://localhost:4502/etc/cloudservices.html**) te wissen. U kunt nauwkeurige het richten voor individuele componenten ook nog uitzetten ongeacht uw plaatsen in de configuratie van de wolkendienst.
   Als u ***al*** doelcomponenten hebt gemaakt en u deze instelling wijzigt, hebben de wijzigingen geen invloed op deze componenten. U moet om het even welke veranderingen in die component direct aanbrengen.

1. Klik op **Verbinding maken met doel** om de verbinding met Doel te initialiseren. Als de verbinding succesvol is, wordt het bericht **Verbinding succesvol** getoond. Klik op **OK** in het bericht en vervolgens op **OK** in het dialoogvenster.

   Als u geen verbinding kunt maken met Target, raadpleegt u de sectie [Problemen](/help/sites-administering/target-configuring.md#troubleshooting-target-connection-problems) oplossen.

### Een doelframework toevoegen {#adding-a-target-framework}

Nadat u de de wolkenconfiguratie van het Doel vormt, voeg een kader van het Doel toe. Het framework identificeert de standaardparameters die vanuit de beschikbare Context [- of](/help/sites-administering/client-context.md) ContextHub [-componenten van de](/help/sites-administering/contexthub-config.md) client naar Adobe Target worden verzonden. Het doel gebruikt de parameters om de segmenten te bepalen die op de huidige context van toepassing zijn.

U kunt veelvoudige kaders voor één enkele configuratie van het Doel tot stand brengen. Meerdere frameworks zijn handig wanneer u een andere set parameters naar Doel moet sturen voor verschillende gedeelten van uw website. Maak een framework voor elke set parameters die u wilt verzenden. Koppel elk gedeelte van uw website aan het juiste framework. Een webpagina kan slechts één framework tegelijk gebruiken.

1. Klik op de configuratiepagina Doel op **+** (plusteken) naast Beschikbare frameworks.
1. Geef in het dialoogvenster Kader maken een **titel** op, selecteer het **Adobe Target-framework** en klik op **Maken**.

   ![chlimage_1-161](assets/chlimage_1-161.png)

   De pagina Framework wordt geopend. Sidetrap verstrekt componenten die informatie van de Context [of](/help/sites-administering/client-context.md) ContextHub [van de](/help/sites-administering/contexthub-config.md) Cliënt vertegenwoordigen die u kunt in kaart brengen.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Sleep de component van de Context van de Cliënt die de gegevens vertegenwoordigt die u voor afbeelding aan het dalingsdoel wilt gebruiken. Alternatief, sleep **de component van de Winkel** ContextHub aan het kader.

   >[!NOTE]
   Bij toewijzing worden parameters via eenvoudige tekenreeksen aan een box doorgegeven. U kunt geen series van ContextHub in kaart brengen.

   Als u bijvoorbeeld **Profielgegevens** over uw sitebezoekers wilt gebruiken om uw doelcampagne te beheren, sleept u de component **Profielgegevens** naar de pagina. De variabelen van profielgegevens die voor afbeelding aan de parameters van het Doel beschikbaar zijn verschijnen.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Selecteer de variabelen die u zichtbaar wilt maken voor het Adobe Target-systeem door het selectievakje **Delen** in de desbetreffende kolommen in te schakelen.

   ![chlimage_1-164](assets/chlimage_1-164.png)

   >[!NOTE]
   Het synchroniseren van parameters verloopt slechts in één richting: van AEM naar Adobe Target.

Uw framework is gemaakt. Als u het framework wilt repliceren naar de publicatie-instantie, gebruikt u de optie Framework **** activeren van de assistent.

### Activiteiten koppelen aan de doelcloud-configuratie {#associating-activities-with-the-target-cloud-configuration}

Koppel uw [AEM-activiteiten](/help/sites-authoring/activitylib.md) aan uw doelwolkenconfiguratie zodat u de activiteiten in [Adobe Target](https://marketing.adobe.com/resources/help/en_US/target/target/c_manage_content.html)kunt weerspiegelen.

>[!NOTE]
Welke soorten activiteiten beschikbaar zijn, wordt bepaald door:
* Als de optie **xt_only** op de huurder van het Doel van Adobe (cliëntcode) wordt toegelaten die op AEM wordt gebruikt om met Adobe Target te verbinden, dan kunt u **slechts** XT activiteiten in AEM tot stand brengen.

* Als de **xt_only** opties **niet** op de huurder van het Doel van Adobe (cliëntcode) wordt toegelaten, dan kunt u **zowel** XT als A/B activiteiten in AEM tot stand brengen.

**** Aanvullende opmerking: Opties **xt_only** zijn een instelling die wordt toegepast op een bepaalde doelgebruiker (clientcode) en kunnen alleen rechtstreeks worden gewijzigd in Adobe Target. U kunt deze optie niet in- of uitschakelen in AEM.

### Het doelframework koppelen aan uw site {#associating-the-target-framework-with-your-site}

Nadat u een doelframework in AEM hebt gemaakt, koppelt u uw webpagina&#39;s aan het framework. De doelcomponenten op de pagina&#39;s verzenden de door het framework gedefinieerde gegevens naar Adobe Target voor tracering. (Zie [Inhoud voorbereiden](/help/sites-authoring/content-targeting-touch.md).)

Wanneer u een pagina aan het framework koppelt, nemen de onderliggende pagina&#39;s de koppeling over.

1. Navigeer in de **Sites** -console naar de site die u wilt configureren.
1. Selecteer [Eigenschappen](/help/sites-authoring/basic-handling.md#quick-actions) weergeven met snelle handelingen [of](/help/sites-authoring/basic-handling.md)selectiemodus **.**
1. Selecteer het tabblad **Cloud Services** .
1. Tik/klik op **Bewerken**.
1. Tik/klik op **Configuratie** toevoegen onder **Cloud Service Configurations** en selecteer **Adobe Target**.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Selecteer het framework dat u onder **Configuratieverwijzing** wilt gebruiken.

   >[!NOTE]
   Zorg ervoor dat u het specifieke **framework** selecteert dat u hebt gemaakt en niet de doelwolkenconfiguratie waaronder het is gemaakt.

1. Tik/klik op **Gereed**.
1. Activeer de hoofdpagina van de website om deze te repliceren naar de publicatieserver. (Zie [Pagina&#39;s](/help/sites-authoring/publishing-pages.md)publiceren.)

   >[!NOTE]
   Als het framework dat u aan de pagina hebt gekoppeld nog niet is geactiveerd, wordt een wizard geopend waarmee u het framework ook kunt publiceren.

## Problemen met doelverbinding oplossen {#troubleshooting-target-connection-problems}

Voer de volgende taken uit om problemen op te lossen die voorkomen wanneer het verbinden met Doel:

* Controleer of de gebruikersgegevens die u opgeeft juist zijn.
* Controleer of de AEM-instantie verbinding kan maken met de doelserver. Bijvoorbeeld, zorg ervoor dat de firewallregels uitgaande verbindingen niet blokkeren AEM, of dat AEM wordt gevormd om noodzakelijke volmachten te gebruiken.
* Zoek naar nuttige berichten in het AEM foutenlogboek. Het bestand error.log bevindt zich in de map **crx-quickstart/logs** waar AEM is geïnstalleerd.
* Wanneer u de activiteit in Adobe Target bewerkt, verwijst de URL naar de localhost. U kunt dit omzeilen door de AEM-externalizer in te stellen op de juiste URL.

