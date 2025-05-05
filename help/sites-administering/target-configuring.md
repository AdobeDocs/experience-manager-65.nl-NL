---
title: De integratie met Adobe Target handmatig configureren
description: Leer hoe u de integratie met Adobe Target handmatig kunt configureren.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 0f710685-dc4f-4333-9847-d002b2637d08
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: d2623c78e8c779b20303865d4bb40effd1e5fe59
workflow-type: tm+mt
source-wordcount: '2125'
ht-degree: 0%

---

# De integratie met Adobe Target handmatig configureren {#manually-configuring-the-integration-with-adobe-target}

U kunt de configuraties van de wizard die u hebt gemaakt tijdens het gebruik van de wizard aanpassen of u kunt handmatig integreren met Adobe Target zonder de wizard te gebruiken.

## De configuratie van de wizard Inschakelen wijzigen {#modifying-the-opt-in-wizard-configurations}

De [ Opt-binnen tovenaar ](/help/sites-administering/opt-in.md) die [ AEM met Adobe Target ](/help/sites-administering/target.md) automatisch tot stand brengt een de wolkenconfiguratie van het Doel genoemd Provisioned Configuratie van het Doel integreert. De tovenaar creeert ook een kader van het Doel voor de wolkenconfiguratie genoemd Provisioned Kader van het Doel. Indien nodig kunt u de eigenschappen van de cloudconfiguratie en het framework wijzigen.

U kunt Adobe Target ook configureren om Adobe Target te gebruiken als rapportagebron wanneer u inhoud als doel instelt door de A4T Analytics Cloud-configuratie te configureren.

Om van de wolkenconfiguratie en het kader de plaats te bepalen, navigeer aan **Cloud Servicen** via **Hulpmiddelen** > **Plaatsing** > **Wolk**. ([ http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html))
Onder Adobe Target, klik **tonen Configuraties**.

### Eigenschappen van provisioned Target Configuration {#provisioned-target-configuration-properties}

De volgende bezitswaarden worden gebruikt in de Provisioned de wolkenconfiguratie van de Configuratie van het Doel die de Opt-in tovenaar creeert:

* **de Code van de Cliënt:** zoals ingegaan in de Opt-in tovenaar.
* **E-mail:** zoals ingegaan in de Opt-in tovenaar.
* **Wachtwoord:** zoals ingegaan in de Opt-in tovenaar.
* **API Type:** REST
* **synchroniseer Segmenten van Adobe Target:** Geselecteerd.

* **bibliotheek van de Cliënt:** mbox.js.
* **Gebruik DTM om cliëntbibliotheek te leveren:** niet geselecteerd. Selecteer deze optie als u [ gebruik DTM ](/help/sites-administering/dtm.md) of een ander systeem van het markeringsbeheer om het mbox.js of dossier te ontvangen AT.js. Adobe raadt u aan DTM te gebruiken in plaats van AEM om de bibliotheek te leveren.

* **Douane mbox.js:** niets specificeerde zodat het standaard mbox.js- dossier wordt gebruikt. Geef desgewenst een aangepast bestand mbox.js op dat u wilt gebruiken. Wordt alleen weergegeven als u mbox.js hebt geselecteerd.
* **Douane AT.js:** niets specificeerde zodat het standaard AT.js- dossier wordt gebruikt. Geef zo nodig een aangepast AT.js-bestand op dat u wilt gebruiken. Wordt alleen weergegeven als u AT.js hebt geselecteerd.

>[!NOTE]
>
>In AEM 6.3, kunt u het dossier van de Bibliotheek van het Doel selecteren, [ AT.JS ](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/mboxcreate-atjs/), dat een nieuwe implementatiebibliotheek voor Adobe Target is die voor zowel typische Webimplementaties als enig-paginatoepassingen wordt ontworpen.
>
>AT.js biedt verschillende verbeteringen aan ten opzichte van de bibliotheek mbox.js:
>
>* Verbeterde laadtijden voor webimplementaties
>* Verbeterde beveiliging
>* Betere implementatieopties voor toepassingen van één pagina
>* AT.js bevat de componenten die in target.js inbegrepen waren, zodat is er niet meer een vraag aan doel.

<!-- OLD URL WHICH IS 404 https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/mbox-implement/mbox-download.html -->

### Voorziene eigenschappen van doelframework {#provisioned-target-framework-properties}

Het provisioned Kader van het Doel dat de Opt-in tovenaar creeert wordt gevormd om contextgegevens van de opslag van de Gegevens van het Profiel te verzenden. De pagina- en geslachtsgegevensitems van de winkel worden standaard naar Target verzonden. Uw oplossing vereist waarschijnlijk extra parameters om worden verzonden.

![ Voorgenomen Kader van het Doel ](assets/chlimage_1-158.png)

U kunt het kader vormen om extra contextinformatie naar Doel te verzenden zoals die in [ wordt beschreven Toevoegend een Kader van het Doel ](/help/sites-administering/target-configuring.md#adding-a-target-framework).

### A4T Analytics Cloud-configuratie configureren {#configuring-a-t-analytics-cloud-configuration}

U kunt Adobe Target zo configureren dat Adobe Analytics de rapportagebron is voor het opgeven van inhoud.

>[!NOTE]
>
>Gebruikersreferenties (verouderd) functioneren niet met A4T (zowel voor Doel als voor Analytics). Daarom moeten klanten IMS-verificatie gebruiken in plaats van gebruikersreferentie-verificatie.

Hiervoor geeft u op met welke A4T-cloudconfiguratie uw Adobe Target-cloudconfiguratie wordt verbonden met:

1. Navigeer aan **Cloud Servicen** via het **AEM embleem** > **Hulpmiddelen** > **Plaatsing** > **Cloud Servicen**.
1. In de **Adobe Target** sectie, klik **nu** vormen.
1. Verbind opnieuw met uw configuratie van Adobe Target.
1. In het **A4T de drop-down menu van de Configuratie van Analytics Cloud**, selecteer het kader.

   >[!NOTE]
   >
   >Alleen analytische configuraties die zijn ingeschakeld voor A4T zijn beschikbaar.
   >
   >Wanneer het vormen van A4T met AEM, kunt u een verwijzing van de Configuratie zien ontbrekende ingang. Ga als volgt te werk om het analyseframework te kunnen selecteren:
   >
   >1. Navigeer aan **Hulpmiddelen** > **Algemeen** > **CRXDE Lite**.
   >1. Navigeer aan de [ Dialoog van de Configuratie van de Analyse A4T ](#a4t-analytics-config-dialog) (zie hieronder)
   >1. Plaats het bezit **onbruikbaar maken** aan **vals**.
   >1. Klik **sparen allen**.

#### Dialoogvenster Configuratie A4T-analyse {#a4t-analytics-config-dialog}

```xml
/libs/cq/analytics/components/testandtargetpage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig
```

![ AdobeTargetSettings ](assets/adobe-target-settings.jpg)

Klik **OK**. Wanneer u inhoud met Adobe Target richt, kunt u uw rapportbron [ selecteren ](/help/sites-authoring/content-targeting-touch.md).

## Handmatig integreren met Adobe Target {#manually-integrating-with-adobe-target}

Handmatig integreren met Adobe Target in plaats van de wizard Optie gebruiken.

>[!NOTE]
>
>Het dossier van de Bibliotheek van het Doel, [ AT.JS ](https://developer.adobe.com/target/implement/client-side/atjs/atjs-functions/mboxcreate-atjs/), is een nieuwe implementatiebibliotheek voor Adobe Target die voor zowel typische Webimplementaties als enig-paginatoepassingen wordt ontworpen. De Adobe adviseert dat u AT.js in plaats van mbox.js als cliëntbibliotheek gebruikt.
>
>AT.js biedt verschillende verbeteringen aan ten opzichte van de bibliotheek mbox.js:
>
>* Verbeterde laadtijden voor webimplementaties
>* Verbeterde beveiliging
>* Betere implementatieopties voor toepassingen van één pagina
>* AT.js bevat de componenten die in target.js inbegrepen waren, zodat is er niet meer een vraag aan target.js
>
>U kunt AT.js of mbox.js in het **de bibliotheek van de Cliënt** drop-down menu selecteren.

<!-- OLD URL from above was 404 https://experienceleague.adobe.com/docs/target/using/implement-target/client-side/mbox-implement/mbox-download.html -->

### Een doelcloud-configuratie maken {#creating-a-target-cloud-configuration}

Om AEM in staat te stellen om met Adobe Target in wisselwerking te staan, creeer een de wolkenconfiguratie van het Doel. Als u de configuratie wilt maken, geeft u de Adobe Target-clientcode en gebruikersgegevens op.

U kunt de configuratie van de wolk van het Doel slechts eenmaal tot stand brengen omdat u de configuratie met veelvoudige AEM campagnes kunt associëren. Als u meerdere Adobe Target-clientcodes hebt, maakt u één configuratie voor elke clientcode.

U kunt de wolkenconfiguratie vormen om segmenten van Adobe Target te synchroniseren. Als u synchronisatie inschakelt, worden segmenten op de achtergrond geïmporteerd van Target wanneer de cloudconfiguratie wordt opgeslagen.

Gebruik de volgende procedure om een de wolkenconfiguratie van het Doel in AEM tot stand te brengen:

1. Navigeer aan **Cloud Servicen** via het **AEM embleem** > **Hulpmiddelen** > **Cloud Servicen** > **Verouderde Cloud Servicen**. ([ http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html))

   De **Cloud Servicen** overzichtspagina opent.

1. In de **Adobe Target** sectie, klik **nu** vormen.
1. In **creeer de dialoog van de Configuratie**:

   1. Geef de configuratie a **Titel**.
   1. Selecteer het **malplaatje van de Configuratie van 0&rbrace; Adobe Target.**

      ![ Configuratie van Adobe Target ](assets/adobe-target-create-configuration.png)

1. Klik **creëren**.

   Het dialoogvenster Bewerken wordt geopend.

   ![ AdobeTargetSettings ](assets/adobe-target-settings.jpg)

   >[!NOTE]
   >
   >Wanneer het vormen van A4T met AEM, kunt u een verwijzing van de Configuratie zien ontbrekende ingang. Ga als volgt te werk om het analyseframework te kunnen selecteren:
   >
   >1. Navigeer aan **Hulpmiddelen** > **Algemeen** > **CRXDE Lite**.
   >1. Navigeer naar **/libs/cq/analytics/components/testandtargetPage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig**
   >1. Plaats het bezit **onbruikbaar maken** aan **vals**.
   >1. Klik **sparen allen**.

1. Geef in het dialoogvenster waarden op voor deze eigenschappen.

   * **Code van de Cliënt**: De code van de de rekeningscliënt van het Doel
   * **E-mail**: De rekening e-mail van het Doel.
   * **Wachtwoord**: het de rekeningswachtwoord van het Doel.
   * **API Type**: of REST of XML
   * **A4T de Configuratie van Analytics Cloud**: Selecteer de configuratie van Analytics Cloud die voor de doelstellingen en metriek van de doelactiviteit wordt gebruikt. U hebt deze configuratie nodig als u Adobe Analytics gebruikt als de rapportbron wanneer u inhoud als doel instelt. Als u uw wolkenconfiguratie niet ziet, zie nota in [ Vormend Configuratie A4T Analytics Cloud ](#configuring-a-t-analytics-cloud-configuration).

   * **het nauwkeurige richten van het Gebruik:** Door gebrek wordt dit controlevakje geselecteerd. Als deze optie is geselecteerd, wacht de configuratie van de cloudservice tot de context is geladen voordat inhoud wordt geladen. Zie het volgende.
   * **synchroniseer Segmenten van Adobe Target:** selecteer deze optie zodat kunt u segmenten downloaden die in Doel worden bepaald om hen in AEM te gebruiken. Selecteer deze optie als de eigenschap API Type REST is, omdat inline-segmenten niet worden ondersteund en u segmenten van Target moet gebruiken. (De AEM term &#39;segment&#39; komt overeen met de doelterm &#39;publiek&#39;.)
   * **de bibliotheek van de Cliënt:** selecteer of u mbox.js of AT.js cliëntbibliotheek wilt.
   * **Gebruik DTM om cliëntbibliotheek** te leveren - selecteer deze optie om of AT.js of mbox.js van DTM of een ander systeem van het markeringsbeheer te gebruiken. Vorm [ de integratie DTM ](/help/sites-administering/dtm.md) om deze optie te gebruiken. Adobe raadt u aan DTM te gebruiken in plaats van AEM om de bibliotheek te leveren.
   * **Douane mbox.js**: Laat leeg als u de doos DTM controleerde of om standaard mbox.js te gebruiken. U kunt ook uw aangepaste mbox.js uploaden. Wordt alleen weergegeven als u mbox.js hebt geselecteerd.
   * **Douane AT.js**: Laat leeg als u het DTM vakje controleerde of om het gebrek AT.js te gebruiken. U kunt ook uw aangepaste AT.js uploaden. Wordt alleen weergegeven als u AT.js hebt geselecteerd.

   >[!NOTE]
   >
   >Wanneer u zich aanmeldt bij de Adobe Target-configuratietovenaar, wordt Accurate gericht inschakelen.
   >
   >Nauwkeurige het richten betekent dat de de dienstconfiguratie van de wolk op de context wacht te laden alvorens inhoud te laden. Hierdoor kan het, in termen van prestaties, nauwkeuriger richten tot een paar milliseconde vertraging leiden alvorens inhoud te laden.
   >
   >Nauwkeurige het richten wordt altijd toegelaten op de auteursinstantie. Nochtans, op publiceer instantie kunt u verkiezen om nauwkeurige gericht uit te zetten globaal door het vinkje naast Accurate het richten in de configuratie van de wolkendienst (**http://localhost:4502/etc/cloudservices.html**) te ontruimen. U kunt nauwkeurige het richten voor individuele componenten ook nog uitzetten ongeacht uw plaatsen in de configuratie van de wolkendienst.
   >
   >Als u ***reeds*** gecreeerd gerichte componenten hebt en u dit het plaatsen verandert, beïnvloeden uw veranderingen niet die componenten. Wijzig deze componenten rechtstreeks.

1. Klik **verbinden met Doel** om de verbinding met Doel te initialiseren. Als de verbinding succesvol is, wordt het bericht **succesvolle Verbinding** getoond. Klik **O.K.** op het bericht en dan **O.K.** op de dialoog.

   Als u niet met Doel kunt verbinden, zie de [ het oplossen van problemen](/help/sites-administering/target-configuring.md#troubleshooting-target-connection-problems) sectie.

### Een doelframework toevoegen {#adding-a-target-framework}

Nadat u de de wolkenconfiguratie van het Doel vormt, voeg een kader van het Doel toe. Het kader identificeert de standaardparameters die naar Adobe Target van de beschikbare [ Context van de Cliënt ](/help/sites-administering/client-context.md) of [ ContextHub ](/help/sites-developing/ch-configuring.md) componenten worden verzonden. Het doel gebruikt de parameters om de segmenten te bepalen die op de huidige context van toepassing zijn.

U kunt veelvoudige kaders voor één enkele configuratie van het Doel creëren. Meerdere frameworks zijn handig wanneer u een andere set parameters naar Doel moet sturen voor verschillende gedeelten van uw website. Maak een framework voor elke set parameters die u verzendt. Koppel elk gedeelte van uw website aan het juiste framework. Een webpagina kan slechts één framework tegelijk gebruiken.

1. Voor uw de configuratiepagina van het Doel, klik **+** (plusteken) naast Beschikbare Kaders.
1. In de Create dialoog van het Kader, specificeer a **Titel**, selecteer het **Kader van Adobe Target**, en klik **creeer**.

   ![ creeer de dialoog van het Kader ](assets/chlimage_1-161.png)

   De pagina Framework wordt geopend. Sidekick verstrekt componenten die informatie van de [ Context van de Cliënt ](/help/sites-administering/client-context.md) of [ ContextHub ](/help/sites-developing/ch-configuring.md) vertegenwoordigen die u in kaart kunt brengen.

   ![ Componenten voor kader ](assets/chlimage_1-162.png)

1. Sleep de component van de Context van de Cliënt die de gegevens vertegenwoordigt die u voor afbeelding aan het dalingsdoel wilt gebruiken. Alternatief, sleep de {**component 1} ContextHub van 0&rbrace; aan het kader.**

   >[!NOTE]
   >
   >Bij toewijzing worden parameters via eenvoudige tekenreeksen aan een box doorgegeven. U kunt geen series van ContextHub in kaart brengen.

   Bijvoorbeeld, om **Gegevens van het Profiel** over uw plaatsbezoekers te gebruiken om uw campagne van het Doel te controleren, sleep de **component van de Gegevens van het Profiel** aan de pagina. De variabelen van profielgegevens die voor afbeelding aan de parameters van het Doel beschikbaar zijn verschijnen.

   ![ profielgegevens ](assets/chlimage_1-163.png)

1. Selecteer de variabelen die u zichtbaar aan het systeem van Adobe Target wilt maken door het **aandeel** checkbox in de aangewezen kolommen te selecteren.

   ![ Aandeel ](assets/chlimage_1-164.png)

   >[!NOTE]
   >
   >Het synchroniseren van parameters is slechts één manier - van AEM naar Adobe Target.

Uw framework is gemaakt. Om het kader aan te herhalen publiceer instantie, gebruik **activeer Kader** optie van sidekick.

### Activiteiten koppelen aan de doelcloud-configuratie  {#associating-activities-with-the-target-cloud-configuration}

Koppel uw [ AEM activiteiten ](/help/sites-authoring/activitylib.md) met uw de wolkenconfiguratie van het Doel zodat u de activiteiten in [ Adobe Target ](https://experienceleague.adobe.com/docs/target/using/experiences/offers/manage-content.html) kunt weerspiegelen.

>[!NOTE]
>
>Welke soorten activiteiten beschikbaar zijn, wordt bepaald door:
>
>
>* Als de **xt_only** optie op de huurder van Adobe Target (cliëntcode) wordt toegelaten die aan de AEM kant wordt gebruikt om met Adobe Target te verbinden, dan kunt u **slechts** activiteiten XT in AEM tot stand brengen.
>
>* Als de **xt_only** optie **niet** op de huurder van Adobe Target (cliëntcode) wordt toegelaten, dan kunt u **zowel** XT als activiteiten A/B in AEM tot stand brengen.
>
>**Extra nota:** **xt_only** optie is het plaatsen die op een bepaalde huurder van het Doel wordt toegepast (clientcode) en kan slechts direct in Adobe Target worden gewijzigd. U kunt deze optie niet in- of uitschakelen in AEM.

### Het doelframework koppelen aan uw site {#associating-the-target-framework-with-your-site}

Nadat u een doelframework hebt gemaakt in AEM, kunt u uw webpagina&#39;s aan het framework koppelen. De doelcomponenten op de pagina&#39;s verzenden de door het framework gedefinieerde gegevens naar Adobe Target voor tracering. (Zie [ Inhoud richtend ](/help/sites-authoring/content-targeting-touch.md).)

Wanneer u een pagina aan het framework koppelt, nemen de onderliggende pagina&#39;s de koppeling over.

1. In de **console van Plaatsen**, navigeer aan de plaats die u wilt vormen.
1. Gebruikend of [ snelle acties ](/help/sites-authoring/basic-handling.md#quick-actions) of [ selectiewijze ](/help/sites-authoring/basic-handling.md), selecteer **Eigenschappen van de Mening.**
1. Selecteer de **Cloud Servicen** tabel.
1. Klik **uitgeven**.
1. Klik **toevoegen Configuratie** onder **Configuraties van de Cloud Service** en selecteer **Adobe Target**.

   ![ voeg Configuratie ](assets/chlimage_1-165.png) toe

1. Selecteer het kader dat u onder **Verwijzing van de Configuratie** wilt.

   >[!NOTE]
   >
   >Zorg ervoor dat u het specifieke **kader** selecteert dat u en niet de de wolkenconfiguratie creeerde van het Doel waaronder het werd gecreeerd.

1. Klik **Gedaan**.
1. Activeer de hoofdpagina van de website zodat u deze naar de publicatieserver kopieert. (Zie [ hoe te de Pagina&#39;s van Publish ](/help/sites-authoring/publishing-pages.md).)

   >[!NOTE]
   >
   >Als het framework dat u aan de pagina hebt gekoppeld nog niet is geactiveerd, wordt een wizard geopend waarmee u het ook kunt publiceren.

## Problemen met doelverbinding oplossen {#troubleshooting-target-connection-problems}

Om problemen op te lossen die wanneer het verbinden met Doel voorkomen, kunt u de volgende taken uitvoeren:

* Controleer of de gebruikersgegevens die u opgeeft juist zijn.
* Controleer of de AEM-instantie verbinding kan maken met de doelserver. Bijvoorbeeld, zorg ervoor dat de firewallregels uitgaande AEM geen verbindingen blokkeren, of dat AEM wordt gevormd om noodzakelijke volmachten te gebruiken.
* Zoek naar nuttige berichten in het AEM foutenlogboek. Het error.log dossier is in de **crx-quickstart/logs** folder waar AEM geïnstalleerd is.
* Wanneer u de activiteit in Adobe Target bewerkt, verwijst de URL naar de localhost. U kunt dit begrijpen omzeilen door de AEM Externalzer in te stellen op de juiste URL.
