---
title: ContextHub configureren
description: Leer hoe te om de Hub van de Context van Adobe Experience Manager te vormen om uw ervaringen te personaliseren.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: 61208bd5-475b-40be-ba00-31bbbc952adf
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1727'
ht-degree: 0%

---

# ContextHub configureren {#configuring-contexthub}

ContextHub is een kader voor het opslaan van, het manipuleren van, en het voorstellen van contextgegevens. Voor meer detail op ContextHub, zie [ontwikkelaarsdocumentatie](/help/sites-developing/contexthub.md). ContextHub vervangt [Clientcontext](/help/sites-administering/client-context.md) in de aanraakinterface.

Vorm [ContextHub](/help/sites-developing/contexthub.md) toolbar om te controleren of het op de wijze van de Voorproef verschijnt, om opslag te creëren ContextHub, en modules toe te voegen UI gebruikend touch-Geoptimaliseerde UI.

## ContextHub uitschakelen {#disabling-contexthub}

Door gebrek, wordt ContextHub toegelaten in een AEM installatie. ContextHub kan worden onbruikbaar gemaakt om het te verhinderen js/css te laden en te initialiseren.

<!--
There are two options to disable ContextHub:

* Edit the ContextHub's configuration and check the option **Disable ContextHub**

    1. In the rail click **Tools &gt; Sites &gt; ContextHub**
    1. Click the appropriate **Configuration Container**
    1. Select the **ContextHub Configuration** and click **Edit Selected Element**
    1. Click **Disable ContextHub** and click **Save**

or
-->

* CRXDE Lite gebruiken om de eigenschap in te stellen `disabled` tot **true** krachtens `/libs/settings/cloudsettings/legacy/contexthub`

>[!NOTE]
>
>[Als gevolg van de herstructurering van de opslagplaats in AEM 6.4,](/help/sites-deploying/repository-restructuring.md) de plaats van configuraties ContextHub veranderde van `/etc/cloudsettings` tot:
>
>* `/libs/settings/cloudsettings`
>* `/conf/global/settings/cloudsettings`
>* `/conf/<tenant>/settings/cloudsettings`

## Het tonen van en het Verbergen van ContextHub UI {#showing-and-hiding-the-contexthub-ui}

Vorm de dienst van ContextHub OSGi van Granite van de Adobe om te tonen of te verbergen [ContextHub UI](/help/sites-authoring/ch-previewing.md) op uw pagina&#39;s. De PID van deze service is `com.adobe.granite.contexthub.impl.ContextHubImpl.`

Om de dienst te vormen kunt u of gebruiken [Webconsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) of gebruik een [JCR-knooppunt in de gegevensopslagruimte](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository):

* **Webconsole:** Om UI te tonen, selecteer het bezit UI van de Show. Om UI te verbergen, ontruim het bezit UI van de Huid.
* **JCR-knooppunt:** Om UI te tonen, plaats boolean `com.adobe.granite.contexthub.show_ui` eigenschap aan `true`. Als u de gebruikersinterface wilt verbergen, stelt u de eigenschap in op `false`.

Wanneer het tonen van ContextHub UI, verschijnt het slechts op pagina&#39;s op AEM auteursinstanties. De interface wordt niet weergegeven op pagina&#39;s met publicatie-instanties.

## ContextHub UI-modi en modules toevoegen {#adding-contexthub-ui-modes-and-modules}

Vorm de wijzen UI en de modules die op de toolbar ContextHub op de wijze van de Voorproef verschijnen:

* UI-modi: Groepen gerelateerde modules
* Modules: widgets die contextgegevens uit een winkel beschikbaar maken en auteurs in staat stellen de context te manipuleren

UI-modi worden als een reeks pictogrammen aan de linkerkant van de werkbalk weergegeven. Wanneer geselecteerd, verschijnen de modules van een wijze UI aan het recht.

![chlimage_1-319](assets/chlimage_1-319.png)

Pictogrammen zijn verwijzingen uit de [Pictogrambibliotheek van Koral UI](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableIcons).

### UI-modus toevoegen {#adding-a-ui-mode}

Voeg een wijze UI aan groep verwante modules ContextHub toe. Wanneer u de wijze UI creeert, verstrekt u de titel en het pictogram die in de toolbar ContextHub verschijnen.

1. Voor de spoorstaaf van de Experience Manager, klik Hulpmiddelen > Plaatsen > de Hub van de Context.
1. Klik de standaardContainer van de Configuratie.
1. Klik de Configuratie van de Hub van de Context.
1. Klik de Create knoop, en klik dan de Wijze UI van de Hub van de Context.

   ![chlimage_1-320](assets/chlimage_1-320.png)

1. Geef waarden op voor de volgende eigenschappen:

   * UI Mode Title: The title that identify the UI mode
   * Pictogram Modus: De kiezer voor de [Pictogram Koraalinterface](https://helpx.adobe.com/experience-manager/6-4/sites/developing/using/reference-materials/coral-ui/coralui3/Coral.Icon.html#availableIcons) bijvoorbeeld `coral-Icon--user`
   * Toegelaten: Uitgezocht om de wijze UI op de toolbar te tonen ContextHub

1. Klik op Opslaan.

### Een UI-module toevoegen {#adding-a-ui-module}

Voeg een module ContextHub UI aan een wijze UI toe zodat het in de toolbar ContextHub voor het voorvertonen van paginainhoud verschijnt. Wanneer u een module UI toevoegt, creeert u een geval van een moduletype dat met ContextHub wordt geregistreerd. Om een module UI toe te voegen, moet u de naam van het bijbehorende moduletype kennen.

AEM verstrekt een moduletype van basisUI evenals verscheidene types van steekproefUI Module waarop u een module UI kunt baseren. In de volgende tabel vindt u een korte beschrijving van elke tabel. Voor informatie over het ontwikkelen van een module van douaneUI, zie [ContextHub UI-modules maken](/help/sites-developing/ch-extend.md#creating-contexthub-ui-module-types).

De eigenschappen van de module UI omvatten een detailconfiguratie waar u waarden voor module-specifieke eigenschappen kunt verstrekken. U verstrekt de detailconfiguratie in formaat JSON. De kolom van het Type van Module in de lijst verstrekt verbindingen aan informatie over de code JSON die voor elk UI moduletype wordt vereist.

| Moduletype | Beschrijving | Winkel |
|---|---|---|
| [contexthub.base](/help/sites-developing/ch-samplemodules.md#contexthub-base-ui-module-type) | Een generiek type UI-module | Gevormd in de eigenschappen van de UI module |
| [contexthub.browserinfo](/help/sites-developing/ch-samplemodules.md#contexthub-browserinfo-ui-module-type) | Hiermee wordt informatie over de browser weergegeven | surferinfo |
| [contexthub.datetime](/help/sites-developing/ch-samplemodules.md#contexthub-datetime-ui-module-type) | Datum- en tijdgegevens weergeven | datetime |
| [contexthub.device](/help/sites-developing/ch-samplemodules.md#contexthub-device-ui-module-type) | Het clientapparaat weergeven | emulators |
| [contexthub.location](/help/sites-developing/ch-samplemodules.md#contexthub-location-ui-module-type) | Geeft de breedte en lengte van de client en de locatie op een kaart weer. Hiermee kunt u de locatie wijzigen. | geolocatie |
| [contexthub.screen-orientation](/help/sites-developing/ch-samplemodules.md#contexthub-screen-orientation-ui-module-type) | Geeft de schermstand van het apparaat (liggend of staand) weer | emulators |
| [contexthub.tagcloud](/help/sites-developing/ch-samplemodules.md#contexthub-tagcloud-ui-module-type) | Statistieken over paginatags weergeven | tagcloud |
| [graniet.profile](/help/sites-developing/ch-samplemodules.md#granite-profile-ui-module-type) | Hiermee wordt de profielinformatie voor de huidige gebruiker weergegeven, inclusief authorizableID, displayName en familyName. U kunt de waarde van displayName en familyName wijzigen. | profiel |

1. Voor de spoorstaaf van de Experience Manager, klik Hulpmiddelen > Plaatsen > ContextHub.
1. Klik de Container van de Configuratie waaraan u een module UI wilt toevoegen.
1. Klik of typ de Configuratie ContextHub waaraan u de module UI wilt toevoegen.
1. Klik de wijze UI waaraan u de module UI toevoegt.
1. Klik de Create knoop, dan klik de Module van ContextHub (algemeen).

   ![chlimage_1-321](assets/chlimage_1-321.png)

1. Geef waarden op voor de volgende eigenschappen:

   * UI Module Title: Een titel die de UI module identificeert
   * Moduletype: het moduletype
   * Toegelaten: Uitgezocht om de module UI in de toolbar te tonen ContextHub

1. (Optioneel) Als u de standaardwinkelconfiguratie wilt overschrijven, voert u een JSON-object in om de UI-module te configureren.
1. Klik op Opslaan.

## Een ContextHub-winkel maken {#creating-a-contexthub-store}

Creeer een opslag van de Hub van de Context om gebruikersgegevens en toegang tot de gegevens voort te zetten zoals nodig. ContextHub-winkels zijn gebaseerd op geregistreerde winkelkandidaten. Wanneer u de opslag creeert, hebt u de waarde van storeType nodig waarmee de opslagkandidaat werd geregistreerd. (Zie [Aangepaste winkelkandidaten maken](/help/sites-developing/ch-extend.md#creating-custom-store-candidates).)

### Gedetailleerde opslagconfiguratie {#detailed-store-configuration}

Wanneer u een opslag vormt, laat het bezit van de Configuratie van het Detail u toe om waarden voor store-specific eigenschappen te verstrekken. De waarde is gebaseerd op de `config` parameter van de opslag `init` functie. Daarom of u deze waarde, en het formaat van de waarde moet verstrekken, hangt van de opslag af.

De waarde van het bezit van de Configuratie van het Detail is een `config` object in JSON-indeling.

### Voorbeeld van winkelkandidaten {#sample-store-candidates}

AEM verstrekt de volgende kandidaten van de steekproefopslag waarop u een opslag kunt baseren.

| Winkeltype | Beschrijving |
|---|---|
| [aem.segmentation](/help/sites-developing/ch-samplestores.md#aem-segmentation-sample-store-candidate) | Bewaren voor opgeloste en onopgeloste segmenten ContextHub. Wint automatisch segmenten van ContextHub SegmentManager terug |
| [aem.resolvedsegments](/help/sites-developing/ch-samplestores.md#aem-resolvedsegments-sample-store-candidate) | Hiermee slaat u de momenteel opgeloste segmenten op. Luistert aan de dienst ContextHub SegmentManager om de opslag automatisch bij te werken |
| [contexthub.geolocation](/help/sites-developing/ch-samplestores.md#contexthub-geolocation-sample-store-candidate) | Hiermee slaat u de breedte en lengte van de browserlocatie op. |
| [contexthub.datetime](/help/sites-developing/ch-samplestores.md#contexthub-datetime-sample-store-candidate) | Hiermee worden de huidige datum, tijd en seizoen voor de browserlocatie opgeslagen |
| [graniet.emulators](/help/sites-developing/ch-samplestores.md#granite-emulators-sample-store-candidate) | Definieert eigenschappen en mogelijkheden voor verschillende apparaten en detecteert het huidige clientapparaat |
| [contexthub.generic-jsonp](/help/sites-developing/ch-samplestores.md#contexthub-generic-jsonp-sample-store-candidate) | Wint en slaat gegevens van de dienst JSONP op |
| [graniet.profile](/help/sites-developing/ch-samplestores.md#granite-profile-sample-store-candidate) | Hiermee worden profielgegevens voor de huidige gebruiker opgeslagen |
| [contexthub.surferinfo](/help/sites-developing/ch-samplestores.md#contexthub-surferinfo-sample-store-candidate) | Hiermee wordt informatie over de client opgeslagen, zoals apparaatinformatie, browsertype en vensterrichting |
| [contexthub.tagcloud](/help/sites-developing/ch-samplestores.md#contexthub-tagcloud-sample-data-store) | Hiermee worden paginatags en tellingen van tags opgeslagen |

1. Voor de spoorstaaf van de Experience Manager, klik Hulpmiddelen > Plaatsen > ContextHub.
1. Klik op de standaardconfiguratiecontainer.
1. Klik op Contexthub-configuratie
1. Om een opslag toe te voegen, klik het Create pictogram en klik dan de Configuratie van de Winkel ContexHub.

   ![chlimage_1-322](assets/chlimage_1-322.png)

1. Geef waarden op voor de basisconfiguratie-eigenschappen en klik op Volgende:

   * **Configuratitel:** De titel die de winkel identificeert
   * **Winkeltype:** De waarde van het storeType bezit van de opslagkandidaat waarop om de opslag te baseren
   * **Vereist:** Selecteren
   * **Ingeschakeld:** Selecteren om de winkel in te schakelen

1. (Optioneel) Als u de standaardopslagconfiguratie wilt overschrijven, voert u een JSON-object in het vak Detail Configuration (JSON) in.
1. Klik op Opslaan.

## Voorbeeld: een JSONP-service gebruiken  {#example-using-a-jsonp-service}

Dit voorbeeld illustreert hoe te om een opslag te vormen en de gegevens in een module UI te tonen. In dit voorbeeld wordt de MD5-service van de site jsontest.com gebruikt als gegevensbron voor een winkel. De service retourneert de MD5-hash-code van een tekenreeks in JSON-indeling.

Een contexthub.generic-jsonp-opslag is geconfigureerd zodat deze gegevens opslaat voor de serviceaanroep `https://md5.jsontest.com/?text=%22text%20to%20md5%22`. De dienst keert de volgende gegevens terug die in een module UI worden getoond:

```xml
{
   "md5": "919a56ab62b6d5e1219fe1d95248a2c5",
   "original": "\"text to md5\""
}
```

### Een contexthub.generic-jsonp Store maken {#creating-a-contexthub-generic-jsonp-store}

De contextthub.generic-jsonp-voorbeeldopslagkandidaat stelt u in staat gegevens op te halen uit een JSONP-service of een webservice die JSON-gegevens retourneert. Voor deze opslagkandidaat, gebruik de opslagconfiguratie om details over de dienst te verstrekken JSONP aan gebruik.

De [init](/help/sites-developing/contexthub-api.md#init-name-config) de functie van de `ContextHub.Store.JSONPStore` JavaScript-klasse definieert een `config` object dat deze winkelkandidaat initialiseert. De `config` object bevat een `service` object dat details over de JSONP-service bevat. Om de opslag te vormen, verstrekt u `service` object in JSON-indeling als de waarde voor de eigenschap Detail Configuration.

Als u gegevens wilt opslaan van de MD5-service van de site jsontest.com, gebruikt u de procedure in [Een ContextHub-winkel maken](/help/sites-developing/ch-configuring.md#creating-a-contexthub-store) de volgende eigenschappen gebruiken:

* **Configuratitel:** md5
* **Winkeltype:** contexthub.generic-jsonp
* **Vereist:** Selecteren
* **Ingeschakeld:** Selecteren
* **Detailconfiguratie (JSON):**

  ```xml
  {
   "service": {
   "jsonp": false,
   "timeout": 1000,
   "ttl": 1800000,
   "secure": false,
   "host": "md5.jsontest.com",
   "port": 80,
   "params":{
   "text":"text to md5"
       }
     }
   }
  ```

### Een UI-module toevoegen voor de md5-gegevens {#adding-a-ui-module-for-the-md-data}

Voeg een module UI aan de toolbar ContextHub toe om de gegevens te tonen die in het voorbeeld md5 opslag wordt opgeslagen. In dit voorbeeld wordt de module contexthub.base gebruikt om de volgende UI-module te produceren:

![chlimage_1-323](assets/chlimage_1-323.png)

Gebruik de procedure in [Een UI-module toevoegen](#adding-a-ui-module) om de module UI aan een bestaande Wijze UI, zoals de wijze toe te voegen Perona UI van de steekproef. Voor de Module UI, gebruik de volgende bezitswaarden:

* **UI-moduletitel:** MD5
* **Moduletype:** contexthub.base
* **Detailconfiguratie (JSON):**

  ```xml
  {
   "icon": "coral-Icon--data",
   "title": "MD5 Converstion",
   "storeMapping": { "md5": "md5" },
   "template": "<p> {{md5.original}}</p>;
                <p>{{md5.md5}}</p>"
  }
  ```

## Foutopsporing in ContextHub {#debugging-contexthub}

Een het zuiveren wijze voor ContextHub kan worden toegelaten om voor het oplossen van problemen toe te staan. Zuiver wijze kan of door de configuratie ContextHub of via CRXDE worden toegelaten.

### Via de configuratie {#via-the-configuration}

Bewerk de configuratie van ContextHub en controleer de optie **Foutopsporing**

1. Klik in het spoor **Extra > Sites > ContextHub**
1. Klik op de standaardinstelling **Configuratie-container**
1. Selecteer de **ContextHub-configuratie** en klik op **Geselecteerd element bewerken**
1. Klikken **Foutopsporing** en klik op **Opslaan**

### Via CRXDE {#via-crxde}

CRXDE Lite gebruiken om de eigenschap in te stellen `debug` tot **true** onder:

* `/conf/global/settings/cloudsettings` of
* `/conf/<tenant>/settings/cloudsettings`

>[!NOTE]
>
>Voor configuraties ContextHub die nog onder hun erfeniswegen worden gevestigd, de plaats om te plaatsen `debug property` is `/libs/settings/cloudsettings/legacy/contexthub`.

### Stille modus {#silent-mode}

In de modus Stil worden alle foutopsporingsgegevens onderdrukt. In tegenstelling tot normale zuiveren optie, die onafhankelijk voor elke configuratie kan worden geplaatst ContextHub, is de stille wijze het globale plaatsen die precedent over om het even welke neemt zuiveren montages op het ContextHub configuratieniveau.

Dit is nuttig voor uw publicatie-instantie, waar u helemaal geen foutopsporingsinformatie wilt. Omdat het een globaal plaatsen is, wordt het toegelaten via OSGi.

1. Open de **Configuratie Adobe Experience Manager-webconsole** om `http://<host>:<port>/system/console/configMgr`
1. Zoeken naar **ContextHub met Adobe graniet**
1. Klik op de configuratie **ContextHub met Adobe graniet** om de eigenschappen te bewerken
1. Schakel de optie in **Stille modus** en klik op **Opslaan**

## Het terugkrijgen van Configuraties ContextHub na Bevordering {#recovering-contexthub-configurations-after-upgrading}

Wanneer een [upgrade naar AEM](/help/sites-deploying/upgrade.md) wordt uitgevoerd, worden de configuraties ContextHub gesteund en in een veilige plaats opgeslagen. Tijdens de verbetering, zijn de standaardconfiguraties ContextHub geïnstalleerd, die de bestaande configuraties vervangen. De back-up is vereist om eventuele wijzigingen of toevoegingen te behouden.

ContextHub-configuraties worden opgeslagen in een map met de naam `contexthub` onder de volgende knooppunten:

* `/conf/global/settings/cloudsettings`
* `/conf/<tenant>/settings/cloudsettings`

Na een upgrade wordt de back-up opgeslagen in een map met de naam `contexthub` onder een knooppunt met de naam:

`/conf/global/settings/cloudsettings/default-pre-upgrade_yyyymmdd_xxxxxxx` of
`/conf/<tenant>/settings/cloudsettings/default-pre-upgrade_yyyymmdd_xxxxxxx`

De `yyyymmdd` Het gedeelte van de knooppuntnaam is de datum toen de verbetering werd uitgevoerd.

Om uw configuraties ContextHub terug te krijgen, gebruik CRXDE Lite om de knopen te kopiëren die uw opslag, wijzen UI, en modules UI van onder vertegenwoordigen `default-pre-upgrade_yyyymmdd_xxxxxx` knooppunt tot hieronder:

* `/conf/global/settings/cloudsettings` of
* `/conf/<tenant>/settings/cloudsettings`
