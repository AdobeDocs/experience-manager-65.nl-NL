---
title: Adobe Analytics Framework aanpassen
description: Leer hoe u het Adobe Analytics-framework voor Adobe Experience Manager kunt aanpassen.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: ab0d4f2e-f761-4510-ba51-4a2dcea49601
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Developer
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '1610'
ht-degree: 0%

---

# Adobe Analytics Framework aanpassen{#customizing-the-adobe-analytics-framework}

Het Adobe Analytics-framework bepaalt welke informatie wordt bijgehouden met Adobe Analytics. Als u het standaardframework wilt aanpassen, gebruikt u JavaScript om aangepaste tracking toe te voegen, Adobe Analytics-plug-ins te integreren en algemene instellingen te wijzigen in het framework dat wordt gebruikt voor bijhouden.

## Over de gegenereerde JavaScript for Frameworks {#about-the-generated-javascript-for-frameworks}

Wanneer een pagina met een kader van Adobe Analytics wordt geassocieerd, en de pagina [&#x200B; verwijzingen naar de module van Analytics &#x200B;](/help/sites-administering/adobeanalytics.md) omvat, wordt een analytics.sitecatalyst.js- dossier automatisch geproduceerd voor de pagina.

JavaScript in de pagina leidt tot een `s_gi` voorwerp (dat de s_code.js Adobe Analytics bibliotheek bepaalt) en wijst waarden aan zijn eigenschappen toe. De naam van de objectinstantie is `s` . In de codevoorbeelden die in deze sectie worden weergegeven, worden verschillende verwijzingen naar deze `s` -variabele gegeven.

De volgende voorbeeldcode lijkt op de code in het bestand analytics.sitecatalyst.js:

```
var s_account = "my_sitecatalyst_account";
var s = s_gi(s_account);
s.fpCookieDomainPeriods = "3";
s.currencyCode= 'USD';
s.trackInlineStats= true;
s.linkTrackVars= 'None';
s.charSet= 'UTF-8';
s.linkLeaveQueryString= false;
s.linkExternalFilters= '';
s.linkTrackEvents= 'None';
s.trackExternalLinks= true;
s.linkDownloadFileTypes= 'exe,zip,wav,mp3,mov,mpg,avi,wmv,doc,pdf,xls';
s.linkInternalFilters= 'javascript:,'+window.location.hostname;
s.trackDownloadLinks= true;

s.visitorNamespace = "mynamespace";
s.trackingServer = "xxxxxxx.net";
s.trackingServerSecure = "xxxxxxx.net";

/* Plugin Config */
/*
s.usePlugins=false;
function s_doPlugins(s) {
    //add your custom plugin code here
}
s.doPlugins=s_doPlugins;
*/
```

Wanneer u aangepaste JavaScript-code gebruikt om het framework aan te passen, wijzigt u de inhoud van dit bestand.

## Adobe Analytics-eigenschappen configureren {#configuring-adobe-analytics-properties}

Er zijn verscheidene vooraf bepaalde variabelen binnen Adobe Analytics die op een kader configureerbaar zijn. De **charset**, **cookieLifetime**, **currencyCode**, en **trackInlineStats** variabelen zijn inbegrepen in de **Algemene Lijst van de Montages van de Analyse** door gebrek.

![&#x200B; a-22 &#x200B;](assets/aa-22.png)

U kunt namen en waarden van variabelen aan de lijst toevoegen. Deze vooraf gedefinieerde variabelen en alle variabelen die u toevoegt, worden gebruikt om de eigenschappen van het object `s` in het bestand analytics.sitecatalyst.js te configureren. In het volgende voorbeeld wordt getoond hoe de toegevoegde `prop10` eigenschap of value `CONSTANT` wordt vertegenwoordigd in de JavaScript-code:

```
var s_account = "my_sitecatalyst_account";
var s = s_gi(s_account);
s.fpCookieDomainPeriods = "3";
s.currencyCode= 'USD';
s.trackInlineStats= true;
s.linkTrackVars= 'None';
s.charSet= 'UTF-8';
s.linkLeaveQueryString= false;
s.linkExternalFilters= '';
s.linkTrackEvents= 'None';
s.trackExternalLinks= true;
s.linkDownloadFileTypes= 'exe,zip,wav,mp3,mov,mpg,avi,wmv,doc,pdf,xls';
s.prop10= 'CONSTANT';
s.linkInternalFilters= 'javascript:,'+window.location.hostname;
s.trackDownloadLinks= true;

s.visitorNamespace = "mynamespace";
s.trackingServer = "xxxxxxx.net";
s.trackingServerSecure = "xxxxxxx.net";
```

Gebruik de volgende procedure om variabelen aan de lijst toe te voegen:

1. Voor uw het kaderpagina van Adobe Analytics, breid het **Algemene gebied van de Montages van de Analyse** uit.
1. Klik onder de lijst met variabelen op Item toevoegen om een nieuwe variabele aan de lijst toe te voegen.
1. Voer in de linkercel een naam voor de variabele in, bijvoorbeeld `prop10` .

1. Voer in de rechterkolom een waarde voor de variabele in, bijvoorbeeld `CONSTANT` .

1. Als u een variabele wilt verwijderen, klikt u op de knop (-) naast de variabele.

>[!NOTE]
>
>Wanneer het ingaan van variabelen en waarden, zorg ervoor zij correct geformatteerd en gespeld zijn, of de **vraag zal niet** met de correcte waarde/veranderlijk paar worden verzonden. Verkeerd gespelde variabelen en de waarden kunnen vraag zelfs verhinderen voor te komen.
>
>Neem contact op met uw Adobe Analytics-vertegenwoordiger om ervoor te zorgen dat deze variabelen correct zijn ingesteld.

>[!CAUTION]
>
>Sommige variabelen in deze lijst zijn **verplicht** voor de vraag van Adobe Analytics correct (bijvoorbeeld, **currencyCode**, **charSet**) te functioneren.
>
>Dus zelfs als ze uit het framework zelf worden verwijderd, zullen ze nog steeds met een standaardwaarde worden gekoppeld wanneer de Adobe Analytics-oproep wordt gedaan.

### Aangepaste JavaScript toevoegen aan een Adobe Analytics-framework {#adding-custom-javascript-to-an-adobe-analytics-framework}

Vrije-van de doos van JavaScript in het **Algemene gebied van de Montages van de Analyse** laat u douanecode aan een kader van Adobe Analytics toevoegen.

![&#x200B; a-21 &#x200B;](assets/aa-21.png)

De code die u toevoegt, wordt toegevoegd aan het bestand analytics.sitecatalyst.js. Daarom hebt u toegang tot de variabele `s` . Dit is een instantie van het `s_gi` JavaScript-object dat is gedefinieerd in `s_code.js` . Het toevoegen van de volgende code is bijvoorbeeld gelijk aan het toevoegen van een variabele met de naam `prop10` of value `CONSTANT` . Dit is het voorbeeld in de vorige sectie:

`s.prop10= 'CONSTANT';`

De code in het {[&#128279;](/help/sites-developing/extending-analytics-components.md) dossier 0} analytics.sitecatalyst.js (die de inhoud van het Adobe Analytics `s-code.js` dossier omvat) bevat de volgende code:

`if (s.usePlugins) s.doPlugins(s)`

De volgende procedure laat zien hoe u het vak JavaScript gebruikt om het bijhouden van Adobe Analytics aan te passen. Als uw JavaScript de stoppen van Adobe Analytics moet gebruiken, [&#x200B; integreert hen &#x200B;](/help/sites-administering/adobeanalytics.md) in AEM.

1. Voeg de volgende JavaScript-code toe aan het vak, zodat `s.doPlugins` wordt uitgevoerd:

   ```
   s.usePlugins=true;
   function s_doPlugins(s) {
       //add your custom code here
   }
   s.doPlugins=s_doPlugins;
   ```

   >[!CAUTION]
   >
   >Deze code is noodzakelijk als u variabelen in een vraag van Adobe Analytics wilt verzenden die op één of andere manier zijn aangepast die niet door de basis belemmering &amp; dalingsinterface OF door gealigneerde JavaScript in de Mening van Adobe Analytics kan worden gedaan.
   >
   >Als de douanevariabelen buiten de functie s_doPlugins zijn zullen zij als *undefined *in de vraag van Adobe Analytics worden verzonden

1. Voeg uw code van JavaScript in de **s_doPlugins** functie toe.

In het volgende voorbeeld worden de gegevens die op een pagina in hiërarchische volgorde zijn vastgelegd, samengevoegd met een algemeen scheidingsteken &quot;|&quot;.

Een Adobe Analytics-framework heeft de volgende configuraties:

* De variabele `prop2` Adobe Analytics wordt toegewezen aan de eigenschap `pagedata.sitesection` site.

* De variabele `prop3` Adobe Analytics wordt toegewezen aan de eigenschap `pagedata.subsection` site.

* De volgende code wordt toegevoegd aan het vak free-from JavaScript:

  ```
  s.usePlugins=true;
   function s_doPlugins(s) {
   s.prop1 = s.prop2+'|'+s.prop3;
   }
   s.doPlugins=s_doPlugins;
  ```

* Wanneer de webpagina die gebruikmaakt van het framework wordt bezocht (of in de bewerkingsmodus wordt de pagina opnieuw geladen of voorvertoond), worden de aanroepen naar Adobe Analytics uitgevoerd.

De volgende waarden worden bijvoorbeeld gegenereerd in Adobe Analytics:

![&#x200B; a-20 &#x200B;](assets/aa-20.png)

### Global Custom Code toevoegen voor alle Adobe Analytics-frameworks {#adding-global-custom-code-for-all-adobe-analytics-frameworks}

Aangepaste JavaScript-code opgeven die in alle Adobe Analytics-frameworks is geïntegreerd. Wanneer het kader van Adobe Analytics van een pagina geen douane [&#x200B; vrij-vorm JavaScript &#x200B;](/help/sites-administering/adobeanalytics.md) bevat, wordt JavaScript dat het manuscript /libs/cq/analytics/components/sitecatalyst/config.js.jsp produceert toegevoegd aan het {[&#128279;](/help/sites-administering/adobeanalytics.md) dossier 2} analytics.sitecatalyst.js.  Het script heeft standaard geen effect omdat het geen opmerkingen bevat. De code stelt ook `s.usePlugins` in op `false` :

```
/* Plugin Config */
/*
s.usePlugins=false;
function s_doPlugins(s) {
    //add your custom plugin code here
}
s.doPlugins=s_doPlugins;
*/
```

De code in het bestand analytics.sitecatalyst.js (die de inhoud van het bestand s_code.js van Adobe Analytics bevat) bevat de volgende code:

als (s.usePlugins) s.doPlugins

Daarom moet uw JavaScript `s.usePlugins` instellen op `true` , zodat alle code in de functie `s_doPlugins` wordt uitgevoerd. Als u de code wilt aanpassen, bedekt u het bestand config.js.jsp met een bestand dat gebruikmaakt van uw eigen JavaScript. Als uw JavaScript de stoppen van Adobe Analytics moet gebruiken, [&#x200B; integreert hen &#x200B;](/help/sites-administering/adobeanalytics.md) in AEM.

>[!NOTE]
>
>Bewerk het bestand /libs/cq/analytics/components/sitecatalyst/config.js.jsp niet. Bepaalde AEM upgrade- of onderhoudstaken kunnen het oorspronkelijke bestand opnieuw installeren, waardoor uw wijzigingen worden verwijderd.

1. Maak in CRXDE Lite de mapstructuur /apps/cq/analytics/components:

   1. Klik met de rechtermuisknop op de map /apps en klik op Maken > Map maken.
   1. Geef `cq` op als mapnaam en klik op OK.
   1. Maak de mappen `analytics` en `components` .

1. Klik met de rechtermuisknop op de map `components` die u hebt gemaakt en klik op Maken > Component maken. Geef de volgende eigenschapswaarden op:

   * Label: `sitecatalyst`
   * Titel: `sitecatalyst`
   * Supertype: `/libs/cq/analytics/components/sitecatalyst`
   * Groep: `hidden`

1. Klik herhaaldelijk op Volgende totdat de knop OK is ingeschakeld en klik vervolgens op OK.

   De component sitecatalyst bevat het automatisch gemaakte bestand sitecatalyst.jsp.

1. Klik met de rechtermuisknop op het bestand sitecatalyst.jsp en klik op Verwijderen.

1. Klik met de rechtermuisknop op de component sitecatalyst en klik op Maken > Bestand maken. Geef de naam `config.js.jsp` op en klik op OK.

   Het bestand config.js.jsp wordt automatisch geopend voor bewerking.

1. Voeg de volgende tekst toe aan het bestand en klik op Alles opslaan:

   ```java
   <%@page session="true"%>
   /* Plugin Config */
   s.usePlugins=true;
   function s_doPlugins(s) {
       //add your custom plugin code here
   }
   s.doPlugins=s_doPlugins;
   ```

   De JavaScript-code die door het script /apps/cq/analytics/components/sitecatalyst/config.js.jsp wordt gegenereerd, wordt nu ingevoegd in het bestand analytics.sitecatalyst.js voor alle pagina&#39;s die een Adobe Analytics-framework gebruiken.

1. Voeg de JavaScript-code toe die u wilt uitvoeren in de functie `s_doPlugins` en klik op Alles opslaan.

>[!CAUTION]
>
>Als er tekst aanwezig is in de vrije vorm-JavaScript van het framework van een pagina (zelfs alleen witruimte), wordt config.js.jsp genegeerd.

### Adobe Analytics-plug-ins in AEM gebruiken {#using-adobe-analytics-plugins-in-aem}

Vraag de JavaScript-code voor Adobe Analytics-plug-ins aan en integreer deze in AEM in uw Adobe Analytics-framework. Voeg de code toe aan een clientbibliotheekmap van de categorie `sitecatalyst.plugins` zodat deze beschikbaar zijn voor uw aangepaste JavaScript-code.

Als u bijvoorbeeld de `getQueryParams` -insteekmodule integreert, kunt u de insteekmodule aanroepen vanuit de `s_doPlugins` -functie van uw aangepaste JavaScript. De volgende voorbeeldcode verzendt het vraagkoord in **&quot;pid&quot;** van URL van de verwijzer als **eVar1**, wanneer een vraag van Adobe Analytics wordt teweeggebracht.

```
s.usePlugins=true;
function s_doPlugins(s) {
   // take the query string from the referrer
   s.eVar1=s.getQueryParam('pid','',document.referrer);
}
s.doPlugins=s_doPlugins;
```

AEM installeert de volgende Adobe Analytics-plug-ins, zodat deze standaard beschikbaar zijn:

* getQueryParam()
* getPreviousValue()
* split()

De clientbibliotheekmap /libs/cq/analytics/clientlibs/sitecatalyst/plugins bevat deze plug-ins in de categorie sitecatalyst.plugins.

>[!NOTE]
>
>Maak een clientbibliotheekmap voor uw plug-ins. Voeg geen plug-ins toe aan de map `/libs/cq/analytics/clientlibs/sitecatalyst/plugins` . Op deze manier weet u zeker dat uw bijdrage aan de categorie `sitecatalyst.plugins` niet wordt overschreven tijdens AEM herinstallatie- of upgradetaken.

Gebruik de volgende procedure om de map met de clientbibliotheek voor uw plug-ins te maken. U hoeft deze procedure slechts eenmaal uit te voeren. Gebruik de volgende procedure om een plug-in toe te voegen aan de map met clientbibliotheken.

1. Open CRXDE Lite in een webbrowser. ([&#x200B; http://localhost:4502/crx/de](http://localhost:4502/crx/de))

1. Klik met de rechtermuisknop op de map /apps/my-app/clientlibs en klik op Maken > Node maken. Voer de volgende eigenschapswaarden in en klik op OK:

   * Naam: een naam voor de bibliotheekmap van de client, zoals mijn plug-ins

   * Type: cq:ClientLibraryFolder

1. Selecteer de clientbibliotheekmap die u hebt gemaakt en gebruik de onderste eigenschappenbalk rechts om de volgende eigenschap toe te voegen:

   * Naam: categorieën
   * Type: String
   * Waarde: sitecatalyst.plugins
   * Meerdere: geselecteerd

   Klik op OK in het venster Bewerken om de waarde van de eigenschap te bevestigen.

1. Klik met de rechtermuisknop op de clientbibliotheekmap die u hebt gemaakt en klik op Maken > Bestand maken. Typ js.txt als bestandsnaam en klik op OK.

1. Klik op Alles opslaan.

Gebruik de volgende procedure om de insteekmodulecode op te halen, de code op te slaan in de AEM opslagplaats en de code toe te voegen aan de map met de clientbibliotheek.

1. Login aan [&#x200B; sc.omniture.com &#x200B;](https://sc.omniture.com/login/) gebruikend uw rekening van Adobe Analytics.
1. Ga op de bestemmingspagina naar Help > Help Home.
1. Klik in de inhoudsopgave aan de linkerkant op Plug-ins voor implementatie.
1. Klik op de koppeling naar de plug-in die u wilt toevoegen. Wanneer de pagina wordt geopend, zoekt u de JavaScript-broncode voor de plug-in en selecteert u de code en kopieert u deze.

1. Klik met de rechtermuisknop op de clientbibliotheekmap en klik op Maken > Bestand maken. Typ voor de bestandsnaam de naam van de plug-in die u wilt integreren, gevolgd door .js, en klik op OK. Als u bijvoorbeeld de insteekmodule getQueryParam integreert, geeft u het bestand de naam getQueryParam.js.

   Wanneer u het bestand maakt, wordt het geopend voor bewerking.

1. Plak de JavaScript-insteekmodule in het bestand, klik op Alles opslaan en sluit het bestand.

1. Open het bestand js.txt vanuit de clientbibliotheekmap.

1. Voeg in een nieuwe regel de naam toe van het bestand dat de insteekmodule bevat, bijvoorbeeld getQueryParam.js. Klik vervolgens op Alles opslaan en sluit het bestand.

>[!NOTE]
>
>Als u plug-ins gebruikt, moet u ook eventuele ondersteunende plug-ins integreren. Als dit niet het geval is, herkent de JavaScript van de plug-in de aanroepen van de functies in de ondersteunende plug-in niet. De getPreviousValue()-insteekmodule vereist bijvoorbeeld dat de split()-insteekmodule correct werkt.
>
>De naam van de steunstop moet ook aan **js.txt** worden toegevoegd.
