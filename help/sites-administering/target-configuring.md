---
title: De integratie met Adobe Target handmatig configureren
seo-title: Manually Configuring the Integration with Adobe Target
description: Leer hoe u de integratie met Adobe Target handmatig kunt configureren.
seo-description: Learn how to manually configure the integration with Adobe Target.
uuid: 0bb76a65-f981-4cc5-bee8-5feb3297137c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 20c8eb1d-5847-4902-b7d3-4c3286423b46
exl-id: 0f710685-dc4f-4333-9847-d002b2637d08
source-git-commit: 813441a61baa560c9d317a5519b9e0c0d1da7a6e
workflow-type: tm+mt
source-wordcount: '2209'
ht-degree: 0%

---

# De integratie met Adobe Target handmatig configureren {#manually-configuring-the-integration-with-adobe-target}

U kunt de configuraties van de wizard die u hebt gemaakt tijdens het gebruik van de wizard aanpassen of u kunt handmatig integreren met Adobe Target zonder de wizard te gebruiken.

## De configuratie van de wizard Inschakelen wijzigen {#modifying-the-opt-in-wizard-configurations}

De [Wizard Inschakelen](/help/sites-administering/opt-in.md) dat [AEM met Adobe Target integreren](/help/sites-administering/target.md) maakt automatisch een doelwolkenconfiguratie met de naam Provisioned Target Configuration. De tovenaar creeert ook een kader van het Doel voor de wolkenconfiguratie genoemd Provisioned Kader van het Doel. U kunt de eigenschappen van de cloudconfiguratie en het framework desgewenst wijzigen.

U kunt Adobe Target ook configureren om Adobe Target te gebruiken als rapportagebron wanneer u inhoud als doel instelt door de A4T Analytics Cloud-configuratie te configureren.

Ga naar **Cloud Services** via **Gereedschappen** > **Implementatie** > **Wolk**. ([http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html)) Onder Adobe Target, klikken of tikken **Configuraties tonen**.

### Eigenschappen van provisioned Target Configuration {#provisioned-target-configuration-properties}

De volgende bezitswaarden worden gebruikt in de Provisioned de wolkenconfiguratie van de Configuratie van het Doel die de Opt-in tovenaar creeert:

* **Clientcode:** Zoals ingevoerd in de wizard Inschakelen.
* **E-mail:** Zoals ingevoerd in de wizard Inschakelen.
* **Wachtwoord:** Zoals ingevoerd in de wizard Inschakelen.
* **API-type:** REST
* **Segmenten uit Adobe Target synchroniseren:** Geselecteerd.

* **Clientbibliotheek:** mbox.js.
* **DTM gebruiken om clientbibliotheek te leveren:** Niet geselecteerd. Selecteer deze optie als u [DTM gebruiken](/help/sites-administering/dtm.md) of een ander tagbeheersysteem als host voor het bestand mbox.js of AT.js. Adobe raadt u aan DTM te gebruiken in plaats van AEM om de bibliotheek te leveren.

* **Aangepaste mbox.js:** Niets specificeerde zodat het standaard mbox.js- dossier wordt gebruikt. Geef het bestand mbox.js op dat u wilt gebruiken. Wordt alleen weergegeven als u mbox.js hebt geselecteerd.
* **Aangepaste AT.js:** Niets specificeerde zodat het standaardAT.js- dossier wordt gebruikt. Geef een aangepast AT.js-bestand op dat u wilt gebruiken. Wordt alleen weergegeven als u AT.js hebt geselecteerd.

>[!NOTE]
>
>In AEM 6.3 kunt u het doelbibliotheekbestand selecteren. [AT.JS](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/mbox-implement/mbox-download.html), een nieuwe implementatiebibliotheek voor Adobe Target die is ontworpen voor zowel standaard webimplementaties als toepassingen van één pagina.
>
>AT.js biedt verschillende verbeteringen aan ten opzichte van de bibliotheek mbox.js:
>
>* Verbeterde laadtijden voor webimplementaties
>* Verbeterde beveiliging
>* Betere implementatieopties voor toepassingen van één pagina
>* AT.js bevat de componenten die in target.js inbegrepen waren, zodat is er niet meer een vraag aan target.js


### Voorziene eigenschappen van doelframework {#provisioned-target-framework-properties}

Het provisioned Kader van het Doel dat de Opt-in tovenaar creeert wordt gevormd om contextgegevens van de opslag van de Gegevens van het Profiel te verzenden. De pagina- en geslachtsgegevensitems van de winkel worden standaard naar Target verzonden. Uw oplossing vereist waarschijnlijk extra parameters om worden verzonden.

![chlimage_1-158](assets/chlimage_1-158.png)

U kunt het framework zodanig configureren dat aanvullende contextgegevens naar Target worden verzonden, zoals beschreven in [Een doelframework toevoegen](/help/sites-administering/target-configuring.md#adding-a-target-framework).

### A4T Analytics Cloud-configuratie configureren {#configuring-a-t-analytics-cloud-configuration}

U kunt Adobe Target zo configureren dat Adobe Analytics de rapportagebron is voor het opgeven van inhoud.

>[!NOTE]
>
>Gebruikersreferenties (verouderd) functioneren niet met A4T (zowel voor Doel als voor Analytics). Daarom moeten klanten IMS-verificatie gebruiken in plaats van gebruikersreferentie-verificatie.

Hiervoor moet u opgeven welke A4T-cloudconfiguratie u wilt gebruiken om uw Adobe Target-cloudconfiguratie aan te sluiten met:

1. Navigeren naar **Cloud Services** via de **AEM** > **Gereedschappen** > **Implementatie** > **Cloud Services**.
1. In de **Adobe Target** sectie, klikt u op **Nu configureren**.
1. Verbind opnieuw met uw configuratie van Adobe Target.
1. In de **A4T Analytics Cloud-configuratie** selecteert u het framework.

   >[!NOTE]
   >
   >Alleen analytische configuraties die zijn ingeschakeld voor A4T zijn beschikbaar.
   >
   >Wanneer het vormen van A4T met AEM, kunt u een verwijzing van de Configuratie zien ontbrekende ingang. Ga als volgt te werk om het analyseframework te kunnen selecteren:
   >
   >1. Navigeren naar **Gereedschappen** > **Algemeen** > **CRXDE Lite**.
   1. Ga naar de [Dialoogvenster Configuratie A4T-analyse](#a4t-analytics-config-dialog) (zie hieronder)
   1. De eigenschap instellen **disable** tot **false**.
   1. Tik of klik op **Alles opslaan**.


#### Dialoogvenster Configuratie A4T-analyse {#a4t-analytics-config-dialog}

```xml
/libs/cq/analytics/components/testandtargetpage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig
```

![AdobeTargetSettings](assets/adobe-target-settings.jpg)

Klikken **OK**. Wanneer u inhoud aanwijst met Adobe Target, kunt u [selecteer uw rapportbron](/help/sites-authoring/content-targeting-touch.md).

## Handmatig integreren met Adobe Target {#manually-integrating-with-adobe-target}

Handmatig integreren met Adobe Target in plaats van de wizard Optie gebruiken.

>[!NOTE]
het doelbibliotheekbestand, [AT.JS](https://docs.adobe.com/content/help/en/target/using/implement-target/client-side/mbox-implement/mbox-download.html), is een nieuwe implementatiebibliotheek voor Adobe Target die is ontworpen voor zowel gangbare webimplementaties als toepassingen die uit één pagina bestaan. Adobe raadt u aan AT.js te gebruiken in plaats van mbox.js als clientbibliotheek.
AT.js biedt verschillende verbeteringen aan ten opzichte van de bibliotheek mbox.js:
* Verbeterde laadtijden voor webimplementaties
* Verbeterde beveiliging
* Betere implementatieopties voor toepassingen van één pagina
* AT.js bevat de componenten die in target.js inbegrepen waren, zodat is er niet meer een vraag aan target.js
>
U kunt AT.js of mbox.js in selecteren **Clientbibliotheek** vervolgkeuzemenu.

### Een doelcloud-configuratie maken {#creating-a-target-cloud-configuration}

Om AEM in staat te stellen om met Adobe Target in wisselwerking te staan, creeer een de wolkenconfiguratie van het Doel. Als u de configuratie wilt maken, geeft u de Adobe Target-clientcode en gebruikersgegevens op.

U kunt de configuratie van de wolk van het Doel slechts eenmaal tot stand brengen omdat u de configuratie met veelvoudige AEM campagnes kunt associëren. Als u meerdere Adobe Target-clientcodes hebt, maakt u één configuratie voor elke clientcode.

U kunt de wolkenconfiguratie vormen om segmenten van Adobe Target te synchroniseren. Als u synchronisatie inschakelt, worden segmenten op de achtergrond geïmporteerd van Target zodra de cloudconfiguratie is opgeslagen.

Gebruik de volgende procedure om een de wolkenconfiguratie van het Doel in AEM tot stand te brengen:

1. Navigeren naar **Cloud Services** via de **AEM** > **Gereedschappen** > **Implementatie** > **Cloud Services**. ([http://localhost:4502/libs/cq/core/content/tools/cloudservices.html](http://localhost:4502/libs/cq/core/content/tools/cloudservices.html))

   De **Adobe Marketing Cloud** overzichtspagina wordt geopend.

1. In de **Adobe Target** sectie, klikt u op **Nu configureren**.
1. In de **Configuratie maken** dialoogvenster:

   1. Geef de configuratie een **Titel**.
   1. Selecteer **Adobe Target-configuratie** sjabloon.
   1. Klikken **Maken**.

   Het dialoogvenster Bewerken wordt geopend.

   ![AdobeTargetSettings](assets/adobe-target-settings.jpg)

   >[!NOTE]
   Wanneer het vormen van A4T met AEM, kunt u een verwijzing van de Configuratie zien ontbrekende ingang. Ga als volgt te werk om het analyseframework te kunnen selecteren:
   1. Navigeren naar **Gereedschappen** > **Algemeen** > **CRXDE Lite**.
   1. Navigeren naar **/libs/cq/analytics/components/testandtargetPage/dialog/items/tabs/items/tab1_general/items/a4tAnalyticsConfig**
   1. De eigenschap instellen **disable** tot **false**.
   1. Tik of klik op **Alles opslaan**.


1. Geef in het dialoogvenster waarden op voor deze eigenschappen.

   * **Clientcode**: De clientcode van de doelaccount
   * **E-mail**: het e-mailadres voor de doelaccount.
   * **Wachtwoord**: het wachtwoord voor de doelaccount.
   * **API-type**: REST of XML
   * **A4T Analytics Cloud-configuratie**: Selecteer de de wolkenconfiguratie van de Analyse die voor de doelstellingen en metriek van de doelactiviteit wordt gebruikt. Dit is nodig als u Adobe Analytics als rapportagebron gebruikt wanneer u inhoud als doel instelt. Als u de cloudconfiguratie niet ziet, raadpleegt u de opmerking in [A4T Analytics Cloud-configuratie configureren](#configuring-a-t-analytics-cloud-configuration).

   * **Gebruik nauwkeurige gericht:** Dit selectievakje is standaard ingeschakeld. Als deze optie is geselecteerd, wacht de configuratie van de cloudservice tot de context is geladen voordat inhoud wordt geladen. Zie het volgende.
   * **Segmenten uit Adobe Target synchroniseren:** Selecteer deze optie om segmenten te downloaden die in Doel zijn gedefinieerd om deze in AEM te gebruiken. U moet deze optie selecteren wanneer het bezit van het Type API REST is, omdat de gealigneerde segmenten niet worden gesteund en u altijd segmenten van Doel moet gebruiken. (De AEM term &#39;segment&#39; komt overeen met de doelterm &#39;publiek&#39;.)
   * **Clientbibliotheek:** Selecteer of u de clientbibliotheek mbox.js of AT.js wilt.
   * **DTM gebruiken om clientbibliotheek te leveren** - Selecteer deze optie als u AT.js of mbox.js van DTM of een ander systeem voor tagbeheer wilt gebruiken. U moet [De DTM-integratie configureren](/help/sites-administering/dtm.md) om deze optie te gebruiken. Adobe raadt u aan DTM te gebruiken in plaats van AEM om de bibliotheek te leveren.
   * **Aangepaste mbox.js**: Laat leeg als u het vak DTM hebt ingeschakeld of als u de standaard mbox.js wilt gebruiken. U kunt ook uw aangepaste mbox.js uploaden. Wordt alleen weergegeven als u mbox.js hebt geselecteerd.
   * **Aangepaste AT.js**: Laat leeg als u het vak DTM hebt ingeschakeld of als u de standaard-AT.js wilt gebruiken. U kunt ook uw aangepaste AT.js uploaden. Wordt alleen weergegeven als u AT.js hebt geselecteerd.

   >[!NOTE]
   Wanneer u zich aanmeldt bij de Adobe Target-configuratietovenaar, wordt Accurate gericht inschakelen.
   Nauwkeurige het richten betekent dat de configuratie van de wolkendienst op de context wacht te laden alvorens inhoud te laden. Hierdoor kan het, in termen van prestaties, nauwkeuriger richten tot een paar milliseconde vertraging leiden alvorens inhoud te laden.
   Nauwkeurige het richten wordt altijd toegelaten op de auteursinstantie. Op de publicatie-instantie kunt u er echter voor kiezen om nauwkeurig afstemmen globaal uit te schakelen door het vinkje naast Accurate Targeting in de cloudserviceconfiguratie (**http://localhost:4502/etc/cloudservices.html**). U kunt nauwkeurige het richten voor individuele componenten ook nog uitzetten ongeacht uw plaatsen in de configuratie van de wolkendienst.
   Als u ***reeds*** Als u deze instelling wijzigt, hebben de wijzigingen geen invloed op de componenten die u hebt gemaakt. U moet om het even welke veranderingen in die component direct aanbrengen.

1. Klikken **Verbinden met doel** om de verbinding met Doel te initialiseren. Als de verbinding tot stand is gebracht, wordt het bericht **Verbinding gelukt** wordt weergegeven. Klikken **OK** op het bericht en vervolgens **OK** in het dialoogvenster.

   Als u geen verbinding kunt maken met Target, raadpleegt u de [problemen oplossen](/help/sites-administering/target-configuring.md#troubleshooting-target-connection-problems) sectie.

### Een doelframework toevoegen {#adding-a-target-framework}

Nadat u de de wolkenconfiguratie van het Doel vormt, voeg een kader van het Doel toe. Het framework identificeert de standaardparameters die via de beschikbare [Clientcontext](/help/sites-administering/client-context.md) of [ContextHub](/help/sites-developing/ch-configuring.md) componenten. Het doel gebruikt de parameters om de segmenten te bepalen die op de huidige context van toepassing zijn.

U kunt veelvoudige kaders voor één enkele configuratie van het Doel tot stand brengen. Meerdere frameworks zijn handig wanneer u een andere set parameters naar Doel moet sturen voor verschillende gedeelten van uw website. Maak een framework voor elke set parameters die u wilt verzenden. Koppel elk gedeelte van uw website aan het juiste framework. Een webpagina kan slechts één framework tegelijk gebruiken.

1. Voor uw de configuratiepagina van het Doel, klik **+** (plusteken) naast Beschikbare kaders.
1. Geef in het dialoogvenster Kader maken een **Titel**, selecteert u de **Adobe Target Framework** en klik op **Maken**.

   ![chlimage_1-161](assets/chlimage_1-161.png)

   De pagina Framework wordt geopend. Sidetrap biedt componenten die informatie van de [Clientcontext](/help/sites-administering/client-context.md) of [ContextHub](/help/sites-developing/ch-configuring.md) dat u kunt toewijzen.

   ![chlimage_1-162](assets/chlimage_1-162.png)

1. Sleep de component van de Context van de Cliënt die de gegevens vertegenwoordigt die u voor afbeelding aan het dalingsdoel wilt gebruiken. U kunt ook de **ContextHub Store** aan het framework.

   >[!NOTE]
   Bij toewijzing worden parameters via eenvoudige tekenreeksen aan een box doorgegeven. U kunt geen series van ContextHub in kaart brengen.

   Bijvoorbeeld om te gebruiken **Profielgegevens** over uw site-bezoekers om uw doelcampagne te beheren, sleept u de **Profielgegevens** naar de pagina. De variabelen van profielgegevens die voor afbeelding aan de parameters van het Doel beschikbaar zijn verschijnen.

   ![chlimage_1-163](assets/chlimage_1-163.png)

1. Selecteer de variabelen die u zichtbaar wilt maken voor het Adobe Target-systeem door de optie **Delen** in de desbetreffende kolommen.

   ![chlimage_1-164](assets/chlimage_1-164.png)

   >[!NOTE]
   Het synchroniseren van parameters is slechts één manier - van AEM naar Adobe Target.

Uw framework is gemaakt. Als u het framework wilt repliceren naar de publicatie-instantie, gebruikt u de opdracht **Framework activeren** van het hulpwerktuig.

### Activiteiten koppelen aan de doelcloud-configuratie  {#associating-activities-with-the-target-cloud-configuration}

Koppel uw [AEM](/help/sites-authoring/activitylib.md) met uw doelwolkenconfiguratie zodat u de activiteiten in [Adobe Target](https://docs.adobe.com/content/help/en/target/using/experiences/offers/manage-content.html).

>[!NOTE]
Welke soorten activiteiten beschikbaar zijn, wordt bepaald door:
* Als de **alleen_xt** Deze optie is ingeschakeld in de Adobe Target-agent (clientcode) die aan de AEM zijde wordt gebruikt om verbinding te maken met Adobe Target. Vervolgens kunt u **alleen** XT-activiteiten in AEM.
* Als de **alleen_xt** opties zijn **niet** ingeschakeld in de Adobe Target-huurder (clientcode), kunt u vervolgens **beide** XT- en A/B-activiteiten in AEM.
>
**Aanvullende opmerking:** **alleen_xt** Deze opties zijn een instelling die wordt toegepast op een bepaalde doelgebruiker (clientcode) en kunnen alleen rechtstreeks in Adobe Target worden gewijzigd. U kunt deze optie niet in- of uitschakelen in AEM.

### Het doelframework koppelen aan uw site {#associating-the-target-framework-with-your-site}

Nadat u een doelframework hebt gemaakt in AEM, kunt u uw webpagina&#39;s aan het framework koppelen. De doelcomponenten op de pagina&#39;s verzenden de door het framework gedefinieerde gegevens naar Adobe Target voor tracering. (Zie [Inhoud instellen](/help/sites-authoring/content-targeting-touch.md).)

Wanneer u een pagina aan het framework koppelt, nemen de onderliggende pagina&#39;s de koppeling over.

1. In de **Sites** navigeer naar de site die u wilt configureren.
1. beide gebruiken [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions) of [selectiemodus](/help/sites-authoring/basic-handling.md), selecteert u **Eigenschappen weergeven.**
1. Selecteer **Cloud Services** tab.
1. Tikken/klikken **Bewerken**.
1. Tikken/klikken **Configuratie toevoegen** krachtens **Configuraties van Cloud Servicen** en selecteert u **Adobe Target**.

   ![chlimage_1-165](assets/chlimage_1-165.png)

1. Selecteer het framework dat u onder **Configuratieverwijzing**.

   >[!NOTE]
   Zorg ervoor dat u de specifieke **kader** die u hebt gemaakt en niet de doelwolkenconfiguratie waaronder deze is gemaakt.

1. Tikken/klikken **Gereed**.
1. Activeer de hoofdpagina van de website om deze te repliceren naar de publicatieserver. (Zie [Pagina&#39;s publiceren](/help/sites-authoring/publishing-pages.md).)

   >[!NOTE]
   Als het framework dat u aan de pagina hebt gekoppeld nog niet is geactiveerd, wordt een wizard geopend waarmee u het framework ook kunt publiceren.

## Problemen met doelverbinding oplossen {#troubleshooting-target-connection-problems}

Voer de volgende taken uit om problemen op te lossen die voorkomen wanneer het verbinden met Doel:

* Controleer of de gebruikersgegevens die u opgeeft juist zijn.
* Controleer of de AEM-instantie verbinding kan maken met de doelserver. Bijvoorbeeld, zorg ervoor dat de firewallregels uitgaande AEM geen verbindingen blokkeren, of dat AEM wordt gevormd om noodzakelijke volmachten te gebruiken.
* Zoek naar nuttige berichten in het AEM foutenlogboek. Het bestand error.log bevindt zich in de map **crx-quickstart/logs** map waarin AEM is geïnstalleerd.
* Wanneer u de activiteit in Adobe Target bewerkt, verwijst de URL naar de localhost. U kunt dit omzeilen door de AEM externalizer in te stellen op de juiste URL.
