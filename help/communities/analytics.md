---
title: Analytische configuratie voor functies van Gemeenschappen
description: Leer hoe u Adobe Analytics for AEM Communities zo configureert dat gebeurtenissen naar Adobe Analytics worden verzonden wanneer een lid communiceert met ondersteunde functies van de Gemeenschappen.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: 7d54928b-6512-4da9-a209-eb4488bf2b64
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '2644'
ht-degree: 0%

---

# Analytische configuratie voor functies van Gemeenschappen {#analytics-configuration-for-communities-features}

## Overzicht {#overview}

Adobe Analytics en Adobe Experience Manager (AEM) zijn beide oplossingen van Adobe Experience Cloud.

Adobe Analytics kan voor AEM Communities zodanig worden geconfigureerd dat, als lid communiceert met ondersteunde functies van de Gemeenschappen, gebeurtenissen worden verzonden naar Adobe Analytics waaruit rapporten worden gegenereerd.

Bijvoorbeeld, van de communautaire plaats, kunnen de beheerders diverse rapporten zien betreffende het spelen van de video.

Daarnaast is een analyse nodig voor:

* In Publish:

   * Het melden van communautaire [&#x200B; tendensen &#x200B;](/help/communities/trends.md)
   * Toestaan dat sitebezoekers kunnen sorteren op &quot;meest bekeken&quot;, &quot;meest actief&quot;, &quot;meest geliefd&quot;
   * De tellingen van de mening op (Gebruiker-Gegenereerde Inhoud) lijsten UGC

* In de ontwerpomgeving:

   * Toon van medezeggenschapsgegevens in de [&#x200B; console van het ledenbeheer &#x200B;](/help/communities/members.md) (meningen, posten, volgen, houdt)
   * De samenvatting van de tendensen, videingshoogte, en videoapparaat voor het middel van enablement [&#x200B; rapporten &#x200B;](/help/communities/reports.md)

Tot de ondersteunde Gemeenschappen behoren:

* [Forum](/help/communities/forum.md)
* [QnA](/help/communities/working-with-qna.md)
* [Blog](/help/communities/blog-feature.md)
* [Bestandsbibliotheek](/help/communities/file-library.md)
* [Kalender](/help/communities/calendar.md)

In deze sectie van de documentatie wordt beschreven hoe u een serie Analytics-rapporten kunt koppelen aan de functies van Communities. De basisstappen zijn:

1. [&#x200B; Repliceer crypto sleutel &#x200B;](#replicate-the-crypto-key) zodat kunt u ervoor zorgen dat de encryptie/de decryptie correct op alle AEM instanties voorkomt
1. Bereid een Adobe Analytics [&#x200B; rapportreeks &#x200B;](#adobe-analytics-report-suite-for-video-reporting) voor
1. Creeer de dienst van de Wolk van de Analyse van de AEM [&#128279;](#aem-analytics-cloud-service-configuration) en [&#x200B; kader &#x200B;](#aem-analytics-framework-configuration)

1. [&#x200B; laat Analytics &#x200B;](#enable-analytics-for-a-community-site) voor een communautaire plaats toe
1. [**verifieer**](#verify-analytics-to-aem-variable-mapping) Analyses aan AEM veranderlijke afbeelding
1. Identificeer [&#x200B; primaire uitgever &#x200B;](#primary-publisher)
1. [&#x200B; Publish &#x200B;](#publish-community-site-and-analytics-cloud-service) de communautaire plaats
1. Vorm [&#x200B; invoer van rapportgegevens &#x200B;](#obtaining-reports-from-analytics) van Adobe Analytics aan de communautaire plaats

## Vereisten {#prerequisites}

Om Analytics voor de eigenschappen van Gemeenschappen te vormen, is het noodzakelijk om met uw rekeningsvertegenwoordiger te werken aan opstelling een rekening van Adobe Analytics en [&#x200B; rapportreeks &#x200B;](#adobe-analytics-report-suite-for-video-reporting). Zodra dit is vastgesteld, moet de volgende informatie beschikbaar zijn:

* **Bedrijfsnaam**

  Het bedrijf dat is gekoppeld aan de Adobe Analytics-account.

* **Naam van de Gebruiker**

  De aanmeldingsgebruikersnaam voor de gebruiker die gemachtigd is om de account Analytics te beheren
(zou de voorrechten van de Toegang van de Dienst van het Web moeten omvatten).

* **Wachtwoord**

  Het aanmeldingswachtwoord voor de geautoriseerde gebruiker.

* **Centrum van Gegevens van Analytics**

  De URL van het datacenter Analytics voor de account.

* **Reeks van het Rapport**

  De naam van de te gebruiken analytische rapportsuite.

## Adobe Analytics Report Suite for Video Reporting {#adobe-analytics-report-suite-for-video-reporting}

Gebruikend de Manager van de Reeks van het Rapport van Adobe Experience Cloud [&#128279;](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/c-new-report-suite/new-report-suite.html?lang=nl-NL), kunnen de het rapportsuites van Analytics worden gevormd zodat een communautaire plaats kan worden toegelaten om rapporten voor de eigenschappen van Gemeenschappen te verstrekken.

Door binnen aan [&#x200B; Adobe Experience Cloud &#x200B;](https://experienceleague.adobe.com/docs/analytics/analyze/analysis-workspace/home.html?lang=nl-NL) met [&#x200B; Naam van het Bedrijf en Naam van de Gebruiker &#x200B;](/help/communities/analytics.md#prerequisites) te ondertekenen, is het mogelijk om een nieuwe of bestaande rapportreeks te vormen om te hebben:

* [&#x200B; 11 de Variabelen van de Omzetting &#x200B;](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/conversion-variables/conversion-var-admin.html?lang=nl-NL) (eVars)

   * **`evar1`** tot en met **`evar11`** ingeschakeld

   * Kan bestaande eVars opnieuw gebruiken (naam wijzigen) of bestaande eVars maken voor gebruik door communautaire functies

* [&#x200B; 7 Gebeurtenissen van het Succes &#x200B;](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/manage-report-suites/edit-report-suite/conversion-variables/success-events/success-event.html?lang=nl-NL) (gebeurtenissen)

   * **`event1`** tot en met **`event7`** ingeschakeld

   * type **`Counter`**

      * not **`Counter (no subrelations)`**

   * Kan bestaande gebeurtenissen opnieuw gebruiken (naam wijzigen) of gebeurtenissen maken die kunnen worden gebruikt voor communautaire functies

* [&#x200B; Videobeheer &#x200B;](https://experienceleague.adobe.com/docs/media-analytics/using/media-overview.html?lang=nl-NL)

   * Video Reporting-console

      * `Video Core` inschakelen
      * Selecteer Opslaan

   * Video Core-meetconsole

      * Selecteren `Use Solution Variables`
      * Selecteer Opslaan

Als het gebruiken van a **nieuwe rapportreeks**, kan een nieuwe rapportreeks slechts 4 gebeurtenissen en 6 gebeurtenisvariabelen hebben, terwijl 11 gebeurtenissen en 7 gebeurtenisvars voor Gemeenschappen worden vereist.

Als het gebruiken van een **bestaande rapportreeks**, kan het noodzakelijk zijn [&#x200B; de veranderlijke afbeelding &#x200B;](#modifying-analytics-variable-mapping) te wijzigen alvorens het kader van Analytics voor een communautaire plaats te activeren.

Neem contact op met uw accountvertegenwoordiger voor eventuele problemen met betrekking tot de variabelen die voor Gemeenschappen zijn bestemd.

>[!CAUTION]
>
>**als het gebruiken van een bestaande rapportreeks die reeds variabelen binnen** gebruikt
>
>* **`evar1`** tot en met **`evar11`**
>
>* **`event1`** tot en met **`event7`**
>
>**toen alvorens de communautaire plaats wordt gepubliceerd,** is het belangrijk om de reeds bestaande afbeelding te herstellen door de AEM variabelen te bewegen die automatisch aan de variabelen van Analytics werden in kaart gebracht toen de Analytics voor een communautaire plaats werd toegelaten.
>
>Om de reeds bestaande afbeelding te herstellen en AEM variabelen naar andere variabelen van de Analyse te bewegen, zie de sectie op [&#x200B; het Wijzigen Variabele van de Analyse &#x200B;](#modifying-analytics-variable-mapping).
>
>Als u dit niet doet, kan dit leiden tot onherstelbaar gegevensverlies.

### Video-hartslaganalyse {#video-heartbeat-analytics}

Wanneer er een licentie is voor Video Heartbeat Analytics, wordt er een `Marketing Cloud Org Id` toegewezen.

Om Video toe te laten hartslag rapporterend na [&#x200B; vormend de het rapportreeks van Analytics voor video die &#x200B;](#adobe-analytics-report-suite-for-video-reporting) rapporteert:

* Creeer de [&#x200B; dienst van Analytics Cloud &#x200B;](#aem-analytics-cloud-service-configuration)
* Laat [&#x200B; Analytics voor een communautaire plaats &#x200B;](#enable-analytics-for-a-community-site) toe
* Koppel de `Marketing Cloud Org Id` aan de communitysite

`Marketing Cloud Org Id` kan op het tijdstip van [&#x200B; communautaire plaatsinstelling &#x200B;](/help/communities/sites-console.md) of later door [&#x200B; zijn ingegaan wijzigend &#x200B;](/help/communities/sites-console.md#modifying-site-properties) de eigenschappen van de communautaire plaats.

![&#x200B; marketing-org-id &#x200B;](assets/marketing-org-id.png)

Wanneer Video Heartbone Analytics wordt toegelaten, concretiseert de code van JavaScript (JS) voor de videospeler de video hartslagbibliotheekcode (ook in JS). De code handelt alle logica voor het verzenden van videostatusupdates naar de analytische video het volgen servers om de 10 seconden (niet configureerbaar) af. Uiteindelijk wordt een cumulatief rapport van de videosessie naar de belangrijkste Analyseservers verzonden.

Als deze optie niet is ingeschakeld, wordt de videohartslagcode nooit geïnstantieerd en wordt alleen de videovoortgang en het volgen van de hervattingspositie voortgezet in SRP voor rapportage.

## Configuratie van Analytics Cloud-service AEM {#aem-analytics-cloud-service-configuration}

Om een Integratie van Analytics tot stand te brengen, die Adobe Analytics met de AEM communautaire plaats integreert, gebruikend standaard UI op de auteursinstantie:

* Vanuit globale navigatie: **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > **[!UICONTROL Cloud Services]**
* Omlaag schuiven naar **[!UICONTROL Adobe Analytics]**
* Selecteren **[!UICONTROL Configure Now]** of **[!UICONTROL Show Configurations]**

![&#x200B; wolk-config &#x200B;](assets/cloud-config1.png)

### Configuratiedialoogvenster maken {#create-configuration-dialog}

* Selecteer het pictogram `[+]` naast **[!UICONTROL Available Configurations]** , zodat u een configuratie kunt maken.

In het dialoogvenster Configuratie maken identificeren de waarden die moeten worden ingevoerd de configuratie.

![&#x200B; creeer-wolk-config &#x200B;](assets/cloud-config2.png)

* **Titel**

  (Vereist) Een weergavetitel voor de configuratie.
Bijvoorbeeld, ga *Communautaire Analytics* in

* **Naam**

  (Optioneel) Indien niet opgegeven, krijgt de naam standaard een geldige knooppuntnaam die is afgeleid van de titel.
Bijvoorbeeld, ga *gemeenschappen* in

* **Malplaatje**

  Selecteren `Adobe Analytics Configuration`

* Selecteer **creëren**

   * Hiermee wordt de configuratiepagina gestart en het dialoogvenster `Analytics Settings` geopend

### Dialoogvenster Analyse-instellingen {#analytics-settings-dialog}

Het eerste ontwerp van een nieuwe analytische configuratie resulteert in de weergave van de configuratie en een nieuw dialoogvenster voor het invoeren van de Analytische instellingen. Deze dialoog vereist de [&#x200B; in de eerste plaats vereiste rekeningsinformatie &#x200B;](#prerequisites) die van de rekeningsvertegenwoordiger wordt verkregen.

![&#x200B; analyse-montages &#x200B;](assets/analytics-settings.png)

* **Bedrijf**

  Het bedrijf dat is gekoppeld aan de Adobe Analytics-account.

* **Naam van de Gebruiker**

  De aanmeldingsgebruikersnaam voor de gebruiker die is geautoriseerd voor het beheer van de account Analytics.

* **Wachtwoord**

  Het aanmeldingswachtwoord voor de geautoriseerde gebruiker.

* **Centrum van Gegevens**

  Selecteer het datacenter Analytics dat als host fungeert voor de rapportsuite.

* **voeg geen het volgen markering aan pagina** toe

  Standaard laten (uitgeschakeld).

* **AppMeasurement van het Gebruik**

  Standaard laten (uitgeschakeld).

* **importeert paginamonpressies (auteur)**

  Standaard laten (uitgeschakeld).

* **importeert paginamonpressies (publiceren)**

  Standaard laten (uitgeschakeld).

De instellingen opslaan:

* Selecteer **verbind met Analytics**

   * Indien niet gelukt,

      * Controleer of vermeldingen geen spaties voor de regelafstand bevatten.
      * Probeer een ander datacenter.

* Selecteer **O.K.**.

  ![&#x200B; analyse-montages &#x200B;](assets/analytics-settings1.png)

### Framework maken {#create-framework}

Nadat de basisverbinding met Adobe Analytics met succes is geconfigureerd, moet u een framework voor de communitysite maken of bewerken. Het doel van het kader is om de eigenschapvariabelen van de Gemeenschappen (AEM) aan (rapportreeks) variabelen Analytics in kaart te brengen.

* Selecteer het pictogram `[+]` naast **[!UICONTROL &#x200B; Available Frameworks]** , zodat u een framework kunt maken.

  ![&#x200B; analyse-kader &#x200B;](assets/analytics-framework.png)

* **Titel**

  (Vereist) Een titel voor het weergeven van het framework
Bijvoorbeeld, ga *Communautair Kader* in.

* **Naam**

  (Optioneel) Indien niet opgegeven, krijgt de naam standaard een geldige knooppuntnaam die is afgeleid van de titel.
Bijvoorbeeld, ga *gemeenschappen* in.

* *Malplaatje*

  Selecteer `Adobe Analytics Framework` .

* Selecteer **creeer**.

Het creëren van het Kader van Analytics opent het kader voor configuratie.

## Configuratie van AEM Analytics Framework {#aem-analytics-framework-configuration}

Het doel van het kader is AEM variabelen toe te wijzen aan analytische variabelen (eVars en events). De variabelen van Analytics beschikbaar voor afbeelding worden [&#x200B; bepaald in de rapportreeks &#x200B;](#adobe-analytics-report-suite-for-video-reporting).

![&#x200B; analyse-kader &#x200B;](assets/analytics-framework1.png)

### Rapportsuite selecteren {#select-report-suite}

Selecteer de rapportsuite die is ingesteld voor videoverslag.

Zie de vorige sectie als er nog geen rapportsuite is gemaakt of niet juist is ingesteld:
[&#x200B; Reeks van het Rapport van Adobe Analytics voor Video die &#x200B;](#adobe-analytics-report-suite-for-video-reporting) meldt

De Sidekick is niet nodig en kan worden geminimaliseerd zodat het de toegang tot de montages van de Suites van het Rapport niet belemmert.

#### Dialoogvenster Suitten rapporteren vóór en na het selecteren van Item toevoegen {#report-suites-dialog-before-and-after-selecting-add-item}

![&#x200B; rapport-reeks &#x200B;](assets/report-suite.png)

1. Selecteer **Punt +** toevoegen.

   Er worden twee vervolgkeuzelijsten weergegeven.

1. Kies een `Report suite.`

   De rapportsuites verbonden aan de rekening van het Bedrijf zijn beschikbaar voor selectie.

1. Selecteer **ja** in de dialoog die opent:

   ```
   Load default server settings?
    Do you want to load the default server settings and overwrite current values in the Server section?
   ```

1. Kies een `Run Mode` .

1. Selecteer **Publish**.

![&#x200B; analytics-framework2 &#x200B;](assets/analytics-framework2.png)

De analytische cloudservice en het framework zijn nu voltooid. De toewijzingen worden bepaald nadat een communautaire plaats met deze toegelaten dienst van Analytics wordt gecreeerd.

## Analyses inschakelen voor een Community-site {#enable-analytics-for-a-community-site}

### Inschakelen voor nieuwe Community-site {#enable-for-new-community-site}

Om de dienst van Analytics Cloud toe te voegen terwijl [&#x200B; creërend een communautaire plaats &#x200B;](/help/communities/sites-console.md):

* In stap 3, onder het [&#x200B; ANALYTICS lusje &#x200B;](/help/communities/sites-console.md#analytics):
   * Selecteer **toelaten de controledoos van Analytics**.
   * Selecteer het framework in de keuzelijst.

* U kunt desgewenst terugkeren naar de configuratie van het analyseframework om de variabeletoewijzingen aan te passen.

### Inschakelen voor bestaande communautaire site {#enable-for-existing-community-site}

Om de dienst van Analytics Cloud aan een [&#x200B; bestaande communautaire plaats &#x200B;](/help/communities/sites-console.md#modifying-site-properties) toe te voegen:

* Navigeer aan de **Gemeenschappen > de console van Plaatsen**.
* Selecteer het pictogram Site bewerken van de communitysite.
* Selecteer de instellingen.
* In de sectie Analytics:
   * Selecteer **toelaten de controledoos van Analytics**.
   * Kies het framework in de keuzelijst.

* U kunt desgewenst terugkeren naar de configuratie van het analyseframework om de variabeletoewijzingen aan te passen.

### Inschakelen voor aangepaste sites {#enable-for-customized-sites}

Voor het bijhouden en importeren van analysemogelijkheden voor een communitysite moet een pagina-element met de `scf-js-site-title` -klasse en href-kenmerken aanwezig zijn. Er mag slechts één dergelijk element op de pagina voorkomen, zoals in een ongewijzigd `sitepage.hbs` -script voor een communitysite. De waarde van `siteUrl` wordt gehaald en verzonden naar Adobe Analytics als *de plaatsweg*.

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

Voor a **aangepaste communautaire plaats** die het `sitepage.hbs` manuscript bedekt, zorg ervoor dat het element aanwezig is. De variabele `siteUrl` wordt ingesteld wanneer deze op de server wordt gerenderd voordat deze aan de client wordt doorgegeven.

Voor a **generische AEM plaats** die de componenten van de Gemeenschappen omvat, maar niet met de [&#x200B; tovenaar van de plaatsverwezenlijking &#x200B;](/help/communities/sites-console.md) wordt gecreeerd, is het noodzakelijk om het element toe te voegen. De waarde van de href moet het pad naar de site zijn. Als het sitepad bijvoorbeeld `/content/my/company/en` is, gebruikt u:

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

De configuratie van OSGi van het auteursmilieu [&#128279;](/help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Component Configuration`, verstrekt een lijst van de componenten die van instrumenten voor Analytics zijn voorzien. De automatische toewijzing van variabelen wordt bepaald door de vermelde componenten.

Als nieuwe douanecomponenten worden gecreeerd die voor Analytics van instrumenten worden voorzien, zouden zij aan deze lijst van gevormde componenten moeten worden toegevoegd.

### Componentconfiguratie {#component-configuration}

![&#x200B; component-configuration1 &#x200B;](assets/component-configuration1.png)

>[!NOTE]
>
>De dagboekcomponenten worden gebruikt om de blogeigenschap uit te voeren.

### Analyses toegewezen aan AEM variabelen {#mapped-analytics-to-aem-variables}

Nadat de communitysite is opgeslagen en Analytics is ingeschakeld en het Cloud config-framework is geselecteerd, worden de AEM variabelen automatisch toegewezen aan de Analytics Vars en -gebeurtenissen. Het begint met evar1 en event1, respectievelijk, en toename door 1.

Als het gebruiken van een bestaande rapportreeks die om het even welke variabelen binnen evar1 door evar11 en event1 door event7 in kaart bracht, wordt het noodzakelijk om [&#x200B; de AEM variabelen &#x200B;](#modifying-analytics-variable-mapping) opnieuw in kaart te brengen en de originele afbeelding te herstellen.

Hier volgt een voorbeeld van standaardtoewijzingen:

![&#x200B; kaart-analytics &#x200B;](assets/map-analytics1.png)

#### Kaart met eVars die met elke gebeurtenis worden verzonden {#map-of-evars-sent-with-each-event}

<table>
 <tbody>
  <tr>
   <td><strong> </strong></td>
   <td><strong><br /> Resource <br /> Type van Enablement</strong></td>
   <td><strong>Titel van site <br /></strong></td>
   <td><strong>Functie<br /> Type</strong></td>
   <td><strong>Groep <br /> Titel</strong></td>
   <td><strong>Pad groeperen <br /></strong></td>
   <td><strong>Type UGC<br /></strong></td>
   <td><strong>UGC<br />-titel</strong></td>
   <td><strong>Gebruiker <br /> (Lid)</strong></td>
   <td><strong>UGC<br />-pad</strong></td>
   <td><strong>Pad naar site <br /></strong></td>
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
   <td><strong>event1 <br /> Resource Play</strong></td>
   <td><em>a)</em></td>
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
   <td><em>a)</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>d)</em></td>
   <td><em>e)</em></td>
   <td><em>f)</em></td>
   <td><em>g)</em></td>
   <td><em>h)</em></td>
   <td><em>i)</em></td>
   <td><em>(j)</em></td>
  </tr>
  <tr>
   <td><strong>event3 <br /> SCFCreate (Post)</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>d)</em></td>
   <td><em>e)</em></td>
   <td><em>f)</em></td>
   <td><em>g)</em></td>
   <td><em>h)</em></td>
   <td><em>i)</em></td>
   <td><em>(j)</em></td>
  </tr>
  <tr>
   <td><strong>event4<br /> SCFFollow</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>d)</em></td>
   <td><em>e)</em></td>
   <td><em>f)</em></td>
   <td><em>g)</em></td>
   <td><em>h)</em></td>
   <td><em>i)</em></td>
   <td><em>(j)</em></td>
  </tr>
  <tr>
   <td><strong>event5<br /> SCFVoteUp</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>d)</em></td>
   <td><em>e)</em></td>
   <td><em>f)</em></td>
   <td><em>g)</em></td>
   <td><em>h)</em></td>
   <td><em>i)</em></td>
   <td><em>(j)</em></td>
  </tr>
  <tr>
   <td><strong>event6<br /> SCFVoteDown</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>d)</em></td>
   <td><em>e)</em></td>
   <td><em>f)</em></td>
   <td><em>g)</em></td>
   <td><em>h)</em></td>
   <td><em>i)</em></td>
   <td><em>(j)</em></td>
  </tr>
  <tr>
   <td><strong>event7<br /> SCFRate</strong></td>
   <td><em>-</em></td>
   <td><em>b)</em></td>
   <td><em>c)</em></td>
   <td><em>d)</em></td>
   <td><em>e)</em></td>
   <td><em>f)</em></td>
   <td><em>g)</em></td>
   <td><em>h)</em></td>
   <td><em>i)</em></td>
   <td><em>(j)</em></td>
  </tr>
 </tbody>
</table>

**Voorbeelden voor waarden van eVar:**

* *[MIME type &#x200B;](https://www.iana.org/assignments/media-types/media-types.xhtml)*: video/mp4
* *[de titel van de communautaire plaats](/help/communities/sites-console.md#step13asitetemplate)*: De Gemeenschappen van de Geometrixx
* *[naam van de communautaire functie](/help/communities/functions.md)*: Forum
* *[de naam van de communautaire groep](/help/communities/creating-groups.md#creating-a-new-group)*: Hiking
* *weg aan de inhoud van de communautaire groep*: `/content/sites/<site name>/en/groups/hiking`
* *[UGC component resourceType](/help/communities/essentials.md)*: `social/forum/components/hbs/topic`
* *UGC componententitel*: Het verven Onderwerpen
* *login (authorizableId)*: `aaron.mcdonald@mailinator.com`
* *SRP weg aan UGC*: `/content/usergenerated/asi/.../forum/jmtz-topic3`
of *weg van te volgen component*: `/content/sites/<site name>/en/jcr:content/content/primary/forum`

* *weg aan de inhoud van de communautaire plaats*: `/content/sites/<site name>/en`

### Variabele-toewijzing Analytics wijzigen {#modifying-analytics-variable-mapping}

De toewijzing van Analytics Vars en events aan AEM variabelen is zichtbaar van de kaderconfiguratie nadat Analytics voor een communautaire plaats wordt toegelaten.

Nadat Analytics is ingeschakeld en voordat de site van de community wordt gepubliceerd, kan de toewijzing in het framework worden gewijzigd. U sleept de gewenste Analytics-gebeurtenis of -gebeurtenis gewoon van het linkerspoor naar de desbetreffende rij in de toewijzingstabel.

Als u dubbele toewijzingen wilt voorkomen, moet u de vervangen Analytics verwijderen uit de rij door de muis erboven te plaatsen en de X te selecteren die rechts van het variabele-element Analytics wordt weergegeven.

Als Communities Vars en events toewijzingen overschrijven die al in de rapportsuite bestonden, dan om gegevensverlies te voorkomen, wijst u de AEM variabelen voor Gemeenschapsfuncties toe aan andere Analytics Vars of -gebeurtenissen en herstelt u de oorspronkelijke toewijzingen.

>[!CAUTION]
>
>Het is belangrijk om opnieuw in kaart te brengen alvorens de communautaire plaats [&#128279;](#publishing-the-community-site) met toegelaten Analytics wordt gepubliceerd, anders is er risico van gegevensverlies.

#### Voorbeeldstap 1: Analytics evar14 naar toewijzingstabel slepen {#example-step-dragging-analytics-evar-into-mapping-table}

![&#x200B; analytics-afbeelding-evar &#x200B;](assets/analytics-mapping-evar.png)

#### Voorbeeld van stap 2: het selecteren van &#39;x&#39; om vervangen evar11 te verwijderen {#example-step-selecting-x-to-remove-replaced-evar}

![&#x200B; analytics-mapping-evar1 &#x200B;](assets/analytics-mapping-evar1.png)

#### Voorbeeld stap 3: AEM var eventData.siteId opnieuw toegewezen aan Analytics evar14 {#example-step-aem-var-eventdata-siteid-remapped-to-analytics-evar}

![&#x200B; analytics-mapping-evar2 &#x200B;](assets/analytics-mapping-evar2.png)

## De website van de Gemeenschap publiceren {#publishing-the-community-site}

### Analyses controleren op AEM variabele toewijzing {#verify-analytics-to-aem-variable-mapping}

Het is verstandig om de variabeletoewijzing te controleren voordat de site van de gebruikersgemeenschap wordt gepubliceerd, die ook de Analytics Cloud-service en het-framework publiceert.

Zie secties:

* [Analyses toegewezen aan AEM variabelen](#mapped-analytics-to-aem-variables)
* [Variabele-toewijzing Analytics wijzigen](#modifying-analytics-variable-mapping)

>[!CAUTION]
>
>**als het gebruiken van een bestaande rapportreeks die reeds variabelen binnen** gebruikt
>
>* **`evar1`** tot en met **`evar11`**
>
>* **`event1`** tot en met **`event7`**
>
>**dan alvorens de communautaire plaats wordt gepubliceerd,** herstel de reeds bestaande afbeelding. Verplaats Gemeenschappen AEM variabelen die automatisch werden toegewezen (toen Analytics voor de communautaire plaats werd toegelaten) aan andere variabelen van de Analyse. Deze hertoewijzing moet consistent zijn in alle onderdelen van de Gemeenschappen.
>
>Als u dit niet doet, kan dit leiden tot onherstelbaar gegevensverlies.

### Primaire uitgever {#primary-publisher}

Wanneer de gekozen plaatsing a [&#x200B; landbouwbedrijf &#x200B;](/help/communities/topologies.md#tarmk-publish-farm) publiceert, dan moet één AEM instantie als primaire uitgever voor het opiniepeilen Adobe Analytics voor rapportgegevens worden geïdentificeerd om aan [&#x200B; SRP &#x200B;](/help/communities/working-with-srp.md) te schrijven.

Door gebrek, identificeert de `AEM Communities Publisher Configuration` configuratie OSGi zijn publicatieinstantie als primaire uitgever, zodat alle publiceer instanties in een publicatielandbouwbedrijf zich als primair zou identificeren.

Daarom is het noodzakelijk om de configuratie op alle secundaire publiceer instanties uit te geven om het **Primaire de controlevakje van de Uitgever** te schrappen.

Voor specifieke instructies, zie de primaire uitgeverssectie van [&#x200B; het Opstellen van Gemeenschappen &#x200B;](/help/communities/deploy-communities.md#primary-publisher).

>[!CAUTION]
>
>Het is belangrijk dat de primaire uitgever wordt gevormd om het opiniepeilen van veelvoudige publicatieinstanties te verhinderen.

### De cryptosleutel dupliceren {#replicate-the-crypto-key}

De Adobe Analytics-referenties worden versleuteld. Om het repliceren of verzenden van gecodeerde analysegegevens tussen auteur en uitgever te vergemakkelijken, moeten alle AEM instanties dezelfde primaire coderingssleutel delen.

Om dit te doen, volg de instructies bij [&#x200B; Repliceer Crypto Sleutel &#x200B;](/help/communities/deploy-communities.md#replicate-the-crypto-key).

### Publish Community Site en Analytics Cloud Service {#publish-community-site-and-analytics-cloud-service}

Nadat de dienst van Analytics Cloud voor een communautaire plaats wordt toegelaten en, indien nodig, wordt de [&#x200B; afbeelding van Analytics aan AEM variabelen aangepast &#x200B;](#mapped-analytics-to-aem-variables), repliceer de configuratie aan het publicatiemilieu door [&#x200B; (herpubliceer) de communautaire plaats &#x200B;](/help/communities/sites-console.md#publishing-the-site).

## Rapporten van Analytics verkrijgen {#obtaining-reports-from-analytics}

### Rapportbeheer {#report-management}

De auteur en de primaire configuratie van OSGi van de uitgever [&#128279;](/help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Report Management`, wordt gebruikt aan vraagAnalytics.

Bij de auteur zijn de vragen voor real-time rapporten.

Voor de primaire uitgever, worden de vragen gebruikt om informatie ter voorbereiding van de de gegevensinvoer van de Importeur van het Rapport Analytische te verstrekken.

Het vraaginterval blijft aan 10 seconden in gebreke.

### Rapportimportmodule {#report-importer}

Zodra een Analytics toegelaten communautaire plaats is gepubliceerd, kan de configuratie van OSGi van de primaire uitgever [&#128279;](/help/sites-deploying/configuring-osgi.md), `AEM Communities Analytics Report Importer`, worden gevormd om het standaardpolling interval voor die configuraties te plaatsen die niet individueel in CRXDE worden gevormd.

Het opiniepeilingsinterval controleert de frequentie van verzoeken aan Adobe Analytics voor gegevens die moeten worden getrokken en in [&#x200B; SRP &#x200B;](/help/communities/working-with-srp.md) worden bewaard.

Wanneer de gegevens als &quot;grote gegevens&quot; kunnen worden gecategoriseerd, kan een frequentere opiniepeiling een grote belasting op de plaats van de gemeenschap veroorzaken.

Het standaardopiniepeilend **interval van de Invoer** wordt geplaatst aan 12 uren.

![&#x200B; rapport-importeur &#x200B;](assets/report-importer.png)

### Componentrapport aanpassen {#component-report-customization}

Momenteel, om de metriek aan spoor aan te passen, worden de knopen gecreeerd in de bewaarplaats die tijdsperioden bepalen waarvoor om een rapport over dat metrisch te produceren.

Het forumonderwerp is momenteel het enige voorbeeld van deze aanpassing:

* Meld u aan bij de primaire uitgever met beheerdersrechten.
* Navigeer aan [&#x200B; CRXDE Lite &#x200B;](/help/sites-developing/developing-with-crxde-lite.md). Bijvoorbeeld, [&#x200B; https://localhost:4503/crx/de &#x200B;](https://localhost:4503/crx/de).

* Navigeer onder het knooppunt `jcr:content` van de hoofdtaal (bijvoorbeeld `/content/sites/engage/en/jcr:content` ) naar de component die is geconfigureerd voor het rapporteren van analysemogelijkheden.
Bijvoorbeeld: **`analytics/reportConfigs/social_forum_components_hbs_topic`**

* Let op de gemaakte tijdsperiodes:

   * `last30Days`
   * `last90Days`
   * `thisYear`

* Merk de `total` knoop op.

   * Als u de eigenschap **`interval`** wijzigt, wordt het interval van de rapportimportmodule genegeerd.
   * De waarde is in seconden en wordt ingesteld op vier uur (14400 seconden).

![&#x200B; component-rapport &#x200B;](assets/component-report.png)

## Gebruikersgegevens beheren in Analytics {#manage-user-data-in-analytics}

Adobe Analytics biedt API&#39;s waarmee u gebruikersgegevens kunt openen, exporteren en verwijderen. Voor meer informatie, zie [&#x200B; Verzoeken van de Toegang voorleggen en van de Schrapping &#x200B;](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/data-governance/an-gdpr-workflow.html?lang=nl-NL).

## Bronnen {#resources}

* Adobe Experience Cloud: [&#x200B; de Hulp en Verwijzing van Analytics &#x200B;](https://experienceleague.adobe.com/docs/analytics.html?lang=nl-NL)
* AEM: [&#x200B; Integrerend met Adobe Analytics &#x200B;](/help/sites-administering/adobeanalytics.md)
* AEM: [&#x200B; Analytics met Externe Leveranciers &#x200B;](/help/sites-administering/external-providers.md)
