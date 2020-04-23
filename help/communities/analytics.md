---
title: Analytische configuratie voor functies van Gemeenschappen
seo-title: Analytische configuratie voor functies van Gemeenschappen
description: Analyses configureren voor Gemeenschappen
seo-description: Analyses configureren voor Gemeenschappen
uuid: 5a083645-9de6-4ecd-a94e-a40143f92edf
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: e6fdaf56-402f-418d-96d8-e46bd3ad1e8c
docset: aem65
translation-type: tm+mt
source-git-commit: 85f3b8f2a5f079954f4907037c1c722a6b25fd91

---


# Analytische configuratie voor functies van Gemeenschappen {#analytics-configuration-for-communities-features}

## Overzicht {#overview}

Adobe Analytics en Adobe Experience Manager (AEM) zijn beide oplossingen van Adobe Marketing Cloud.

Adobe Analytics kan voor AEM-gemeenschappen zo worden geconfigureerd dat, als een lid communiceert met ondersteunde functies van de Gemeenschappen, gebeurtenissen worden verzonden naar Adobe Analytics van waaruit rapporten worden gegenereerd.

Bijvoorbeeld, wanneer een lid van een enablement communautaire plaats een videobron bekijkt die aan hen wordt toegewezen, zal de middelspeler gebeurtenissen naar Analytics, met inbegrip van videohartslaggegevens verzenden. Van de communautaire plaats, kunnen de beheerders diverse rapporten zien betreffende het spelen van de video.

Daarnaast is een analyse nodig voor:

* In de publicatieomgeving:

   * Rapportage over [trends in de gemeenschap](/help/communities/trends.md)
   * Toestaan dat sitebezoekers kunnen sorteren op &quot;meest bekeken&quot;, &quot;meest actief&quot;, &quot;meest geliefd&quot;
   * Tellingen van UGC-lijsten weergeven

* In de ontwerpomgeving:

   * Weergave van gegevens over deelname in de [ledenbeheerconsole](/help/communities/members.md) (weergaven, posten, volgen, zoals)
   * Trend summary, video hartslag en video device for enablement resource [reports](/help/communities/reports.md)

Tot de ondersteunde Gemeenschappen behoren:

* [Middelen inschakelen](/help/communities/resources.md)
* [Forum](/help/communities/forum.md)
* [QnA](/help/communities/working-with-qna.md)
* [Blog](/help/communities/blog-feature.md)
* [Bestandsbibliotheek](/help/communities/file-library.md)
* [Kalender](/help/communities/calendar.md)

In deze sectie van de documentatie wordt beschreven hoe u een serie Analytics-rapporten kunt koppelen aan de functies van Communities. De basisstappen zijn:

1. [Repliceer de cryptosleutel](#replicate-the-crypto-key) om ervoor te zorgen dat codering/decodering op de juiste wijze plaatsvindt op alle AEM-instanties
1. Een Adobe Analytics- [rapportsuite voorbereiden](#adobe-analytics-report-suite-for-video-reporting)
1. Een AEM Analytics- [cloudservice](#aem-analytics-cloud-service-configuration) en - [framework maken](#aem-analytics-framework-configuration)

1. [Analyse](#enable-analytics-for-a-community-site) voor een communitysite inschakelen
1. [**Analyse **](#verify-analytics-to-aem-variable-mapping)van variabele aan AEM-toewijzing verifiëren
1. Identificeer [primaire uitgever](#primary-publisher)
1. [De communitysite publiceren](#publish-community-site-and-analytics-cloud-service)
1. Het [importeren van rapportgegevens](#obtaining-reports-from-analytics) van Adobe Analytics naar de communitysite configureren

## Vereisten {#prerequisites}

Voor het configureren van Analytics voor Community-functies moet u samenwerken met uw accountvertegenwoordiger om een Adobe Analytics-account en een [rapportsuite](#adobe-analytics-report-suite-for-video-reporting)in te stellen. Zodra dit is vastgesteld, moet de volgende informatie beschikbaar zijn:

* **Bedrijfsnaam**

   Het bedrijf dat is gekoppeld aan de Adobe Analytics-account.

* **Gebruikersnaam**

   De login gebruikersnaam voor de gebruiker die wordt gemachtigd om de rekening van Analytics te beheren (zou de voorrechten van de Toegang van de Dienst van het Web moeten omvatten).

* **Wachtwoord**

   Het aanmeldingswachtwoord voor de geautoriseerde gebruiker.

* **Analysecentrum**

   De URL van het datacenter Analytics voor de account.

* **Rapportsuite**

   De naam van de te gebruiken analytische rapportsuite.

## Adobe Analytics Report Suite for Video Reporting {#adobe-analytics-report-suite-for-video-reporting}

Met de rapportsuite [](https://marketing.adobe.com/resources/help/en_US/reference/new_report_suite.html)van Adobe Marketing Cloud kunnen de Analytics-rapporten worden geconfigureerd, zodat een communitysite mogelijk rapporten kan leveren voor de functies van de Community.

Door u aan te melden bij [Adobe Marketing Cloud](https://marketing.adobe.com/resources/help/en_US/analytics/getting-started/analytics-navigation.html) met [bedrijfsnaam en gebruikersnaam](/help/communities/analytics.md#prerequisites), is het mogelijk een nieuwe of bestaande rapportsuite te configureren met:

* [11 Conversievariabelen](https://marketing.adobe.com/resources/help/en_US/reference/conversion_var_admin.html) (eVars)

   * **`evar1`** via **`evar11`** ingeschakeld

   * Kan bestaande eVars opnieuw gebruiken (naam wijzigen) of nieuwe sites maken voor gebruik door communautaire functies

* [7 Succesgebeurtenissen](https://marketing.adobe.com/resources/help/en_US/reference/success_event.html) (gebeurtenissen)

   * **`event1`** via **`event7`** ingeschakeld

   * type **`Counter`**

      * not **`Counter (no subrelations)`**
   * Kan bestaande gebeurtenissen opnieuw gebruiken (naam wijzigen) of nieuwe gebeurtenissen maken die kunnen worden gebruikt voor communautaire functies


* [Videobeheer](https://marketing.adobe.com/resources/help/en_US/sc/appmeasurement/hbvideo/video_analytics_config.html)

   * Video Reporting-console

      * Inschakelen `Video Core`
      * Selecteer Opslaan
   * Video Core-meetconsole

      * Selecteer `Use Solution Variables`
      * Selecteer Opslaan


Als u een **nieuwe rapportsuite** gebruikt, dient u er rekening mee te houden dat een nieuwe rapportsuite slechts 4 gebeurtenissen en 6 gebeurtenisvariabelen kan bevatten, terwijl 11 gebeurtenissen en 7 gebeurtenisvars vereist zijn voor de Gemeenschappen.

Als het gebruiken van een **bestaande rapportreeks**, kan het noodzakelijk zijn om de veranderlijke afbeelding [te](#modifying-analytics-variable-mapping) wijzigen alvorens het kader van Analytics voor een communautaire plaats te activeren. Neem contact op met uw accountvertegenwoordiger voor eventuele problemen met betrekking tot de variabelen die voor Gemeenschappen zijn bestemd.

>[!CAUTION]
>
>**Als u een bestaande rapportsuite gebruikt die al variabelen gebruikt binnen**
>
>* **`evar1`** doorheen **`evar11`**
   >
   >
* **`event1`** doorheen **`event7`**
>
>
**Voordat de communitysite wordt gepubliceerd,** is het belangrijk dat de bestaande toewijzing wordt hersteld door de AEM-variabelen te verplaatsen die automatisch zijn toegewezen aan analytische variabelen wanneer Analytics is ingeschakeld voor een communitysite.
>
>Zie de sectie over het [aanpassen van de variabele Toewijzing](#modifying-analytics-variable-mapping)Analytics voor het herstellen van de bestaande toewijzing en het verplaatsen van AEM-variabelen naar andere analytische variabelen.
>
>Als u dit niet doet, kan dit leiden tot onherstelbaar gegevensverlies.

### Video-hartslaganalyse {#video-heartbeat-analytics}

Als er een licentie is voor Video Heartbeat Analytics, `Marketing Cloud Org Id` wordt er een toegewezen.

Om Video toe te laten hartslagrapportering na het [vormen van de het rapportreeks van Analytics voor videorapportering](#adobe-analytics-report-suite-for-video-reporting):

* Een [Analytics-cloudservice maken](#aem-analytics-cloud-service-configuration)
* Analyse [voor een communitysite inschakelen](#enable-analytics-for-a-community-site)
* Koppel de `Marketing Cloud Org Id` site aan de site van de community

U `Marketing Cloud Org Id` kunt de site invoeren op het moment dat de site wordt gemaakt [of later door de eigenschappen van de site van de](/help/communities/sites-console.md#enablement) community te [wijzigen](/help/communities/sites-console.md#modifying-site-properties) . [](#aem-analytics-cloud-service-configuration)

![chlimage_1-177](assets/chlimage_1-177.png)

Wanneer Video Heartbone Analytics wordt toegelaten, concretiseert de code JavaScript (JS) voor de videospeler de videohartslagbibliotheekcode (ook in JS) die al logica voor het verzenden van videostatusupdates naar de Analytics video volgende servers om de 10 seconden (niet configureerbaar) behandelt en uiteindelijk verzendt een cumulatief rapport van de videozitting naar de belangrijkste servers van Analytics.

Als deze optie niet is ingeschakeld, wordt de videohartslagcode nooit geïnstantieerd en wordt alleen de videovoortgang en het volgen van de hervattingspositie voortgezet in SRP voor rapportage.

## Configuratie van AEM Analytics Cloud Service {#aem-analytics-cloud-service-configuration}

Een nieuwe integratie voor Analytics maken, waarmee Adobe Analytics wordt geïntegreerd met de AEM-communitysite. Hierbij wordt de standaardgebruikersinterface van de auteur gebruikt:

* Vanuit globale navigatie: **[!UICONTROL Extra > Implementatie > Cloud Services]**
* Omlaag schuiven naar **[!UICONTROL Adobe Analytics]**
* Selecteer nu **[!UICONTROL configureren]** of Configuraties **[!UICONTROL tonen]**

![chlimage_1-178](assets/chlimage_1-178.png)

### Configuratiedialoogvenster maken {#create-configuration-dialog}

* Selecteer `[+]` pictogram naast **[!UICONTROL Beschikbare Configuraties]** om een nieuwe configuratie te creëren

In het dialoogvenster Configuratie maken identificeren de waarden die moeten worden ingevoerd de configuratie.

![chlimage_1-179](assets/chlimage_1-179.png)

* **Titel**

   (Vereist) Een weergavetitel voor de configuratie.
Voer bijvoorbeeld Community Analytics *inschakelen in*

* **Naam**

   (Optioneel) Indien niet opgegeven, wordt de naam standaard ingesteld op een geldige knooppuntnaam die is afgeleid van de titel.
For example, enter *communities*

* **Sjabloonmodel**

   Selecteer `Adobe Analytics Configuration`

* Selecteer **Maken**

   * Hiermee start u de configuratiepagina en opent u het `Analytics Settings` dialoogvenster

### Dialoogvenster Analyse-instellingen {#analytics-settings-dialog}

Het eerste ontwerp van een nieuwe analytische configuratie resulteert in de weergave van de configuratie en een nieuw dialoogvenster voor het invoeren van de Analytische instellingen. Deze dialoog vereist de [vereiste rekeninginformatie](#prerequisites) die van de rekeningsvertegenwoordiger wordt verkregen.

![chlimage_1-180](assets/chlimage_1-180.png)

* **Bedrijf**

   Het bedrijf dat is gekoppeld aan de Adobe Analytics-account

* **Gebruikersnaam**

   De aanmeldingsgebruikersnaam voor de gebruiker die gemachtigd is om de account Analytics te beheren

* **Wachtwoord**

   Het aanmeldingswachtwoord voor de geautoriseerde gebruiker

* **Datacenter**

   Selecteer het datacenter Analytics dat als host fungeert voor de rapportsuite

* **Trackingtag niet toevoegen aan pagina**

   Als standaard behouden (uitgeschakeld)

* **AppMeasurement gebruiken**

   Als standaard behouden (uitgeschakeld)

* **Pagina-afbeeldingen niet elke avond importeren (auteur)**

   Als standaard behouden (uitgeschakeld)

* **Pagina-afbeeldingen niet elke avond (publiceren)** als standaard importeren (uitgeschakeld)

De instellingen opslaan:

* Selecteer **Verbinding maken met Analyse**

   * Indien niet gelukt,

      * Verifieer de ingangen geen belangrijke ruimten bevatten
      * Probeer een ander datacenter
      * Neem contact op met uw accountvertegenwoordiger

* Selecteer **OK**

![chlimage_1-181](assets/chlimage_1-181.png)

### Framework maken {#create-framework}

Nadat de basisverbinding met Adobe Analytics is geconfigureerd, moet u een framework voor de communitysite maken of bewerken. Het doel van het framework is om AEM-variabelen (Communities feature) toe te wijzen aan variabelen van Analytics (report suite).

* Selecteer `[+]` pictogram naast **[!UICONTROL Beschikbare kaders]** om een nieuw kader tot stand te brengen

![chlimage_1-182](assets/chlimage_1-182.png)

* **Titel**

   (Vereist) Een weergavetitel voor het frameworkVoer bijvoorbeeld het communautaire *kader voor activering in*

* **Naam**

   (Optioneel) Indien niet opgegeven, wordt de naam standaard ingesteld op een geldige knooppuntnaam die is afgeleid van de titel.
For example, enter *communities*

* *Sjabloonmodel*

   Selecteer `Adobe Analytics Framework`

* Selecteer **Maken**

Het creëren van het Kader van Analytics opent het kader voor configuratie.

## Configuratie van AEM Analytics Framework {#aem-analytics-framework-configuration}

Het doel van het framework is om AEM-variabelen toe te wijzen aan analytische variabelen (eVars en events). De variabelen van Analytics beschikbaar voor afbeelding worden [bepaald in de rapportreeks](#adobe-analytics-report-suite-for-video-reporting).

![chlimage_1-183](assets/chlimage_1-183.png)

### Rapportsuite selecteren {#select-report-suite}

Selecteer de rapportsuite die is ingesteld voor videoverslag.

Zie de vorige sectie als er nog geen rapportsuite is gemaakt of niet juist is ingesteld:
Rapportsuite van[Adobe Analytics voor videomelding](#adobe-analytics-report-suite-for-video-reporting)

De Sidetrap is niet nodig en kan worden geminimaliseerd zodat het de toegang tot de montages van de Suites van het Rapport niet belemmert.

#### Dialoogvenster Suitten rapporteren vóór en na het selecteren van Item toevoegen {#report-suites-dialog-before-and-after-selecting-add-item}

![chlimage_1-184](assets/chlimage_1-184.png)

1. Item **toevoegen + selecteren**

   Er worden twee vervolgkeuzelijsten weergegeven.

1. Kies een `Report suite.`

   De rapportsuites verbonden aan de rekening van het Bedrijf zijn beschikbaar voor selectie.

1. Selecteer **Ja** in het dialoogvenster dat wordt geopend:

   ```
   Load default server settings?
    Do you want to load the default server settings and overwrite current values in the Server section?
   ```

1. Kies een `Run Mode`

1. Publiceren **selecteren**

![chlimage_1-185](assets/chlimage_1-185.png)

De analytische cloudservice en het framework zijn nu voltooid. De toewijzingen worden gedefinieerd zodra een communitysite is gemaakt en deze Analytics-service is ingeschakeld.

## Analyses inschakelen voor een Community-site {#enable-analytics-for-a-community-site}

### Inschakelen voor nieuwe Community-site {#enable-for-new-community-site}

U voegt als volgt de cloudservice Analytics toe terwijl u een nieuwe communitysite [maakt](/help/communities/sites-console.md):

* In stap 3, onder het tabblad [](/help/communities/sites-console.md#analytics)ANALYSE:
   * Schakel het selectievakje Analyse **** inschakelen in.
   * Selecteer het framework in de keuzelijst.

* U kunt desgewenst terugkeren naar de configuratie van het analyseframework om de variabele toewijzingen aan te passen.

### Inschakelen voor bestaande communautaire site {#enable-for-existing-community-site}

U kunt als volgt de cloudservice Analytics toevoegen aan een [bestaande communitysite](/help/communities/sites-console.md#modifying-site-properties):

* Navigeer naar de console **Communities > Sites** .
* Selecteer het pictogram Site bewerken van de communitysite.
* Selecteer de INSTELLINGEN.
* In de sectie Analytics:
   * Schakel het selectievakje Analyse **** inschakelen in.
   * Kies het framework in de keuzelijst.

* U kunt desgewenst terugkeren naar de configuratie van het analyseframework om de variabele toewijzingen aan te passen.

### Inschakelen voor aangepaste sites {#enable-for-customized-sites}

Voor het correct werken van Analytics het volgen en de invoer voor een communautaire plaats, moet een paginaelement met de `scf-js-site-title` klasse en de attributen href aanwezig zijn. Er mag slechts één dergelijk element op de pagina voorkomen, zoals in een ongewijzigd `sitepage.hbs` script voor een communitysite. De waarde van `siteUrl` wordt geëxtraheerd en naar Adobe Analytics verzonden als het *sitepad*.

```xml
# present in default sitepage.hbs
# only one scf-js-site-title class should be included
# this example sets it to be hidden as it serves no visual purpose
<div
    class="navbar-brand scf-js-site-title"
    href="{{siteUrl}}.html"
    style="visibility: hidden;"
>
</div>
```

Voor een **aangepaste communautaire plaats** die het `sitepage.hbs` manuscript bedekt, zorg ervoor het element aanwezig is. De `siteUrl`variabele wordt ingesteld wanneer deze op de server wordt gerenderd voordat de client wordt ingeschakeld.

Voor een **generische plaats** AEM die de componenten van de Gemeenschappen omvat, maar niet met de tovenaar [van de](/help/communities/sites-console.md)plaatsverwezenlijking wordt gecreeerd, is het noodzakelijk om het element toe te voegen. De waarde van de href moet het pad naar de site zijn. Als het sitepad bijvoorbeeld `/content/my/company/en`het volgende is:

```xml
<div
    class="navbar-brand scf-js-site-title"
    href="/content/my/company/en.html"
    style="visibility: hidden;"
>
</div>
```

## Analyses voor functies van Gemeenschappen {#analytics-for-communities-features}

Analytics wordt automatisch gebruikt voor verschillende functies van de Gemeenschappen.

De configuratie [](/help/sites-deploying/configuring-osgi.md)OSGi van het auteursmilieu, `AEM Communities Analytics Component Configuration`, verstrekt een lijst van de componenten die voor Analytics van instrumenten zijn voorzien. De automatische toewijzing van variabelen wordt bepaald door de vermelde componenten.

Als nieuwe douanecomponenten worden gecreeerd die voor Analytics van instrumenten worden voorzien, zouden zij aan deze lijst van gevormde componenten moeten worden toegevoegd.

### Componentconfiguratie {#component-configuration}

![chlimage_1-186](assets/chlimage_1-186.png)

>[!NOTE]
>
>De dagboekcomponenten worden gebruikt om de blogeigenschap uit te voeren.

### Toegewezen analyses aan AEM-variabelen {#mapped-analytics-to-aem-variables}

Zodra de communautaire plaats met toegelaten Analytics en het cloud config kader wordt bewaard, zullen de variabelen AEM automatisch aan Analytics eVars en gebeurtenissen worden in kaart gebracht die met evar1 en event1, respectievelijk beginnen, en het verhogen met 1.

Als het gebruiken van een bestaande rapportreeks die om het even welke variabelen binnen evar1 tot evar11 en event1 door event7 in kaart bracht, zal het noodzakelijk zijn om de variabelen [opnieuw in](#modifying-analytics-variable-mapping) kaart te brengen AEM en de originele afbeelding te herstellen.

Hier volgt een voorbeeld van standaardtoewijzingen na het volgen van de [aan de slag-zelfstudie](/help/communities/getting-started-enablement.md):

![chlimage_1-187](assets/chlimage_1-187.png)

#### Kaart met eVars die met elke gebeurtenis worden verzonden {#map-of-evars-sent-with-each-event}

<table>
 <tbody>
  <tr>
   <td><strong> </strong></td>
   <td><strong>Resource<br /><br /> Type inschakelen</strong></td>
   <td><strong>Titel site<br /></strong></td>
   <td><strong>Type functie<br /></strong></td>
   <td><strong>Groepsnaam<br /></strong></td>
   <td><strong>Pad groeperen<br /></strong></td>
   <td><strong>UGC<br /> -type</strong></td>
   <td><strong>UGC<br /> -titel</strong></td>
   <td><strong>Gebruiker<br /> (lid)</strong></td>
   <td><strong>UGC<br /> -pad</strong></td>
   <td><strong>Sitepad<br /></strong></td>
  </tr>
  <tr>
   <td><strong> </strong></td>
   <td><strong>eVar1</strong></td>
   <td><strong>eVar2</strong></td>
   <td><strong>eVar3</strong></td>
   <td><strong>eVar4</strong></td>
   <td><strong>eVar5</strong></td>
   <td><strong>eVar6</strong></td>
   <td><strong>eVar7</strong></td>
   <td><strong>eVar8</strong></td>
   <td><strong>eVar9</strong></td>
   <td><strong>eVar10</strong></td>
  </tr>
  <tr>
   <td><strong>event1<br /> Resource Play</strong></td>
   <td><em>(a)</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>-</em></td>
   <td><em>i)</em></td>
   <td><em>-</em></td>
  </tr>
  <tr>
   <td><strong>event2<br /> SCFView</strong></td>
   <td><em>(a)</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>(d)</em></td>
   <td><em>e)</em></td>
   <td><em>(f)</em></td>
   <td><em>(g)</em></td>
   <td><em>(h)</em></td>
   <td><em>i)</em></td>
   <td><em>j)</em></td>
  </tr>
  <tr>
   <td><strong>event3<br /> SCFCreate (Post)</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>(d)</em></td>
   <td><em>e)</em></td>
   <td><em>(f)</em></td>
   <td><em>(g)</em></td>
   <td><em>(h)</em></td>
   <td><em>i)</em></td>
   <td><em>j)</em></td>
  </tr>
  <tr>
   <td><strong>event4<br /> SCFFollow</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>(d)</em></td>
   <td><em>e)</em></td>
   <td><em>(f)</em></td>
   <td><em>(g)</em></td>
   <td><em>(h)</em></td>
   <td><em>i)</em></td>
   <td><em>j)</em></td>
  </tr>
  <tr>
   <td><strong>event5<br /> SCFVoteUp</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>(d)</em></td>
   <td><em>e)</em></td>
   <td><em>(f)</em></td>
   <td><em>(g)</em></td>
   <td><em>(h)</em></td>
   <td><em>i)</em></td>
   <td><em>j)</em></td>
  </tr>
  <tr>
   <td><strong>event6<br /> SCFVoteDown</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>(d)</em></td>
   <td><em>e)</em></td>
   <td><em>(f)</em></td>
   <td><em>(g)</em></td>
   <td><em>(h)</em></td>
   <td><em>i)</em></td>
   <td><em>j)</em></td>
  </tr>
  <tr>
   <td><strong>event7<br /> SCFRate</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>(d)</em></td>
   <td><em>e)</em></td>
   <td><em>(f)</em></td>
   <td><em>(g)</em></td>
   <td><em>(h)</em></td>
   <td><em>i)</em></td>
   <td><em>j)</em></td>
  </tr>
 </tbody>
</table>

**Voorbeelden voor eVar-waarden:**

* *[MIME-type](https://www.iana.org/assignments/media-types)*: video/mp4
* *[titel](/help/communities/sites-console.md#step13asitetemplate)*van gemeenschapssite: Geometrixgemeenschappen
* *[communautaire functienaam](/help/communities/functions.md)*: Forum
* *[groepsnaam](/help/communities/creating-groups.md#creating-a-new-group)*van de gemeenschap: Hiking
* *pad naar inhoud* van groep met gemeenschappen: `/content/sites/communities/en/groups/hiking`
* *[Resourcetype](/help/communities/essentials.md)*UGC-component:`social/forum/components/hbs/topic`
* *Titel* van UGC-component: Wikingonderwerpen
* *login (authorizableId)*: `aaron.mcdonald@mailinator.com`
* *SRP-pad naar UGC*: `/content/usergenerated/asi/.../forum/jmtz-topic3`of *pad van te volgen* component: `/content/sites/communities/en/jcr:content/content/primary/forum`

* *pad naar community-site-inhoud*: `/content/sites/community/en`

### Variabele-toewijzing Analytics wijzigen {#modifying-analytics-variable-mapping}

De toewijzing van analytische variabelen en gebeurtenissen aan AEM variabelen is zichtbaar van de kaderconfiguratie nadat Analytics voor een communautaire plaats wordt toegelaten.

Nadat Analytics is toegelaten en alvorens de communautaire plaats wordt gepubliceerd, kan de afbeelding in het kader worden veranderd door de gewenste Analytics evar of de gebeurtenis van de linkerspoorstaaf te slepen en het neer te zetten in de relevante rij in de mappingstabel.

Als u dubbele toewijzingen wilt voorkomen, moet u de vervangen Analytics verwijderen uit de rij door de muis erboven te plaatsen en de X te selecteren die rechts van het variabele-element Analytics wordt weergegeven.

Als Communities Vars en events toewijzingen overschrijven die al in de rapportsuite bestonden, dan om gegevensverlies te voorkomen, wijst u de AEM-variabelen voor Gemeenschapsfuncties toe aan andere Analytics Vars of -gebeurtenissen en herstelt u de oorspronkelijke toewijzingen.

>[!CAUTION]
>
>Het is belangrijk om opnieuw toe te wijzen alvorens de communautaire plaats met toegelaten Analytics wordt [gepubliceerd](#publishing-the-community-site) , anders is er risico van gegevensverlies.

#### Voorbeeld, stap 1: Analytics evar14 naar toewijzingstabel slepen {#example-step-dragging-analytics-evar-into-mapping-table}

![chlimage_1-188](assets/chlimage_1-188.png)

#### Voorbeeld stap 2: Vervangen evar11 verwijderen door &#39;x&#39; te selecteren {#example-step-selecting-x-to-remove-replaced-evar}

![chlimage_1-189](assets/chlimage_1-189.png)

#### Voorbeeld stap 3: AEM var eventData.siteId opnieuw toegewezen aan Analytics evar14 {#example-step-aem-var-eventdata-siteid-remapped-to-analytics-evar}

![chlimage_1-190](assets/chlimage_1-190.png)

## De website van de Gemeenschap publiceren {#publishing-the-community-site}

### Analyse van variabele AEM-toewijzing verifiëren {#verify-analytics-to-aem-variable-mapping}

Het is verstandig om de variabeletoewijzing te controleren voordat de communitysite wordt gepubliceerd, die ook de cloudservice en het framework Analytics publiceert.

Zie secties:

* [Toegewezen analyses aan AEM-variabelen](#mapped-analytics-to-aem-variables)
* [Variabele-toewijzing Analytics wijzigen](#modifying-analytics-variable-mapping)

>[!CAUTION]
>
>**Als u een bestaande rapportsuite gebruikt die al variabelen gebruikt binnen**
>
>* **`evar1`** doorheen **`evar11`**
   >
   >
* **`event1`** doorheen **`event7`**
>
>
**Voordat de site van de community wordt gepubliceerd,** is het belangrijk dat de bestaande toewijzing wordt hersteld en dat de AEM-variabelen van de Communities die automatisch zijn toegewezen (wanneer Analytics is ingeschakeld voor de site van de community), worden verplaatst naar andere analytische variabelen. Deze nieuwe toewijzing moet voor alle onderdelen van de Gemeenschappen consistent zijn.
>
>Als u dit niet doet, kan dit leiden tot onherstelbaar gegevensverlies.

### Primaire uitgever {#primary-publisher}

Wanneer de gekozen plaatsing een [publiceerlandbouwbedrijf](/help/communities/topologies.md#tarmk-publish-farm)is, dan moet één AEM publiceren instantie als primaire uitgever voor het opiniepeilen van de Analyse van Adobe voor rapportgegevens worden geïdentificeerd om aan [SRP](/help/communities/working-with-srp.md)te schrijven.

Door gebrek, identificeert de configuratie `AEM Communities Publisher Configuration` OSGi zijn publicatiegeval als primaire uitgever, zodat alle publiceer instanties in een publicatielandbouwbedrijf zich als primair zou identificeren.

Daarom is het noodzakelijk om de configuratie op alle secundaire publicatieinstanties uit te geven om de **Primaire de controledoos van de Uitgever** te schrappen.

Voor specifieke instructies, zie de primaire uitgeverssectie van het [Opstellen van Gemeenschappen](/help/communities/deploy-communities.md#primary-publisher).

>[!CAUTION]
>
>Het is belangrijk dat de primaire uitgever wordt gevormd om het opiniepeilen van veelvoudige publicatieinstanties te verhinderen.

### De cryptosleutel dupliceren {#replicate-the-crypto-key}

De gegevens voor Adobe Analytics zijn gecodeerd. Om het repliceren of verzenden van gecodeerde analysegegevens tussen auteur en uitgever te vergemakkelijken, moeten alle AEM-instanties dezelfde hoofdcoderingssleutel delen.

Volg hiervoor de instructies bij [Replicate the Crypto Key](/help/communities/deploy-communities.md#replicate-the-crypto-key).

### Community Site en Analytics Cloud Service publiceren {#publish-community-site-and-analytics-cloud-service}

Zodra de Analytics-cloudservice is ingeschakeld voor een communitysite en, indien nodig, de [toewijzing van Analytics aan AEM-variabelen is aangepast](#mapped-analytics-to-aem-variables), moet de configuratie worden gerepliceerd naar de publicatieomgeving door de communitysite [](/help/communities/sites-console.md#publishing-the-site)(opnieuw) te publiceren.

## Rapporten van Analytics verkrijgen {#obtaining-reports-from-analytics}

### Rapportbeheer {#report-management}

De auteur en de primaire configuratie [OSGi van de uitgever,](/help/sites-deploying/configuring-osgi.md)`AEM Communities Analytics Report Management`, wordt gebruikt om Analytics te vragen.

Bij de auteur zijn de vragen bestemd voor real-time rapporten.

Voor de primaire uitgever, worden de vragen gebruikt om informatie ter voorbereiding van de de gegevensinvoer van de Importeur van het Rapport Analytische te verstrekken.

Het vraaginterval blijft aan 10 seconden in gebreke.

### Rapportimportmodule {#report-importer}

Zodra een Analytics toegelaten communautaire plaats is gepubliceerd, kan de configuratie [](/help/sites-deploying/configuring-osgi.md)OSGi van de primaire uitgever, `AEM Communities Analytics Report Importer`, worden gevormd om het standaardopiniepeilingsinterval voor die configuraties te plaatsen die niet individueel in CRXDE worden gevormd.

Met het pollinginterval bepaalt u de frequentie van aanvragen bij Adobe Analytics voor gegevens die in [SRP](/help/communities/working-with-srp.md)moeten worden opgehaald en opgeslagen.

Wanneer de gegevens als &quot;grote gegevens&quot; kunnen worden gecategoriseerd, kan een frequentere opiniepeiling een grote belasting op de plaats van de gemeenschap veroorzaken.

Het standaardpollinginterval voor **importeren** is ingesteld op 12 uur.

![chlimage_1-191](assets/chlimage_1-191.png)

### Componentrapport aanpassen {#component-report-customization}

Momenteel, om de metriek aan spoor aan te passen, worden de knopen gecreeerd in de bewaarplaats die tijdsperioden bepalen waarvoor om een rapport over dat metrisch te produceren.

Het forumonderwerp is momenteel het enige voorbeeld van deze aanpassing:

* Meld u aan bij de primaire uitgever met beheerdersrechten.
* Navigeer naar [CRXDE Lite](/help/sites-developing/developing-with-crxde-lite.md). Bijvoorbeeld [https://localhost:4503/crx/de](https://localhost:4503/crx/de).

* Onder het jcr:content-knooppunt van de taalhoofdmap (navigeer bijvoorbeeld `/content/sites/engage/en/jcr:content),`naar de component die is geconfigureerd voor Analytics-rapportage.
Bijvoorbeeld, **`analytics/reportConfigs/social_forum_components_hbs_topic`**

* Let op de gemaakte tijdsperiodes:

   * `last30Days`
   * `last90Days`
   * `thisYear`

* Let op het `total`knooppunt.

   * Het wijzigen van het **`interval`** bezit treedt het interval van de Importeur van het Rapport met voeten.
   * De waarde is in seconden en wordt ingesteld op 4 uur (14400 seconden).

![chlimage_1-192](assets/chlimage_1-192.png)

## Gebruikersgegevens beheren in Analytics {#manage-user-data-in-analytics}

Adobe Analytics biedt API&#39;s waarmee u gebruikersgegevens kunt openen, exporteren en verwijderen. Voor meer informatie, zie [Verzoeken](https://marketing.adobe.com/resources/help/en_US/analytics/gdpr/gdpr_submit_access_delete.html)van de Toegang voorleggen en van de Schrapping.

## Bronnen {#resources}

* Adobe Marketing Cloud: Help en referentie [Analytics](https://marketing.adobe.com/resources/help/en_US/reference/)
* AEM: [Integrating with Adobe Analytics](/help/sites-administering/adobeanalytics.md)
* AEM: [Analyse met externe providers](/help/sites-administering/external-providers.md)

