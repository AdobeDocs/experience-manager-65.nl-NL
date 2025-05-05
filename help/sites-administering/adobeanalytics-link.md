---
title: Koppeling bijhouden configureren voor Adobe Analytics
description: Leer over het vormen van verbinding het volgen voor SiteCatalyst.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
exl-id: 9fa3e531-11b3-4b8d-a87c-a08faf06f5b7
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: a28883778c5e8fb90cbbd0291ded17059ab2ba7e
workflow-type: tm+mt
source-wordcount: '1615'
ht-degree: 0%

---


# Koppeling bijhouden configureren voor Adobe Analytics{#configuring-link-tracking-for-adobe-analytics}

Wanneer gebruikers op koppelingen op pagina&#39;s van uw website klikken, kunt u gerelateerde informatie in Adobe Analytics vastleggen. Gebruik bijvoorbeeld het bijhouden van koppelingen om te leren hoe gebruikers met uw site werken, het downloaden van bestanden bijhouden en afsluitkoppelingen volgen.

## Koppelingen bijhouden configureren voor een Adobe Analytics-framework {#configuring-link-tracking-for-an-adobe-analytics-framework}

1. Gebruikend **Navigatie**, ga via **Plaatsing**, **Cloud Servicen** aan de **Adobe Analytics** sectie.

1. Gebruikend **toon Configuraties**, open het vereiste kader van Adobe Analytics.
1. Vouw de **sectie van de Configuratie van het Spoor van de Verbinding** uit en vorm zoals vereist (deze pagina verstrekt verdere details):

   ![ het kader van Analytics ](assets/aa-08.png)

## Bestandsdownloads volgen {#tracking-file-downloads}

Configureer het Adobe Analytics-framework zodanig dat bestanden die zijn gedownload van gekoppelde pagina&#39;s automatisch worden bijgehouden als downloads in Adobe Analytics. Wanneer u het bijhouden van downloads inschakelt, worden alleen de bestandstypen bijgehouden die u opgeeft.

Downloads van de volgende bestandstypen worden standaard bijgehouden:

* exe
* zip
* wav
* mp3
* mov
* mpg
* avi
* wmv
* doc
* pdf
* xls

Als het bijhouden van de download bijvoorbeeld is ingeschakeld voor PDF-bestanden, wordt het downloaden van de PDF bijgehouden wanneer gebruikers op koppelingen naar PDF-bestanden klikken.

De eigenschappen voor het bijhouden van de download van het framework worden geïmplementeerd als code in het `analytics.sitecatalyst.js` -bestand dat voor een pagina wordt gegenereerd. In het volgende codevoorbeeld wordt de standaardconfiguratie voor het bijhouden van downloads weergegeven:

```
s.trackDownloadLinks= true;
s.linkDownloadFileTypes= 'exe,zip,wav,mp3,mov,mpg,avi,wmv,doc,pdf,xls';
```

Downloadtracering inschakelen voor uw Adobe Analytics-framework:

1. [ open het kader van Adobe Analytics en breid de Verbinding die sectie van de Configuratie ](#configuring-link-tracking-for-an-adobe-analytics-framework) volgen uit.
1. Laat **Downloads van het Spoor** toe.
1. In het **vakje van de Types van Dossier van de Download**, typ de filename uitbreidingen voor de types van dossiers die u gevolgd wilt.

## Externe koppelingen bijhouden {#tracking-external-links}

U kunt het klikken van externe verbindingen (uitgangsverbindingen) op uw pagina&#39;s volgen.

Externe koppelingen voor uw Adobe Analytics-framework volgen:

1. [ open het kader van Adobe Analytics en breid de **Verbinding die sectie van de Configuratie** ](#configuring-link-tracking-for-an-adobe-analytics-framework) volgen uit.
1. Configureer de volgende eigenschappen volgens uw vereisten.

Eigenschappen voor het bijhouden wanneer op externe koppelingen wordt geklikt:

* **Extern Spoor**
Hiermee schakelt u het bijhouden van externe koppelingen in.

* **Externe Filters**
(Optioneel) Definieert filters voor het afstemmen van de externe URL&#39;s van de koppelingsdoelen. Wanneer de koppelingsdoelen overeenkomen met het filter, wordt de koppeling bijgehouden. Externe filters zijn handig voor het bijhouden van slechts enkele externe koppelingen op uw pagina&#39;s.

  Als u de externe koppelingen wilt opgeven die moeten worden bijgehouden, typt u de volledige URL of een deel van de URL van het koppelingsdoel. Scheid meerdere filters met een komma. Letterlijke tekens voor tekenreeksen sluiten binnen enkele aanhalingstekens. Geen waarde (de standaardwaarde `''`, twee enkele aanhalingstekens) zorgt ervoor dat alle externe koppelingen worden bijgehouden.

* **Interne Filters**
Definieert filters voor het afstemmen van de URL&#39;s van interne koppelingen. Wanneer de koppeling verwijst naar URL&#39;s die overeenkomen met dit filter, wordt de koppeling niet bijgehouden. De standaardwaarde is een javascript-opdracht die de hostnaam van de URL voor het huidige vensteradres retourneert.

  Als u de interne koppelingen wilt opgeven die niet worden bijgehouden, typt u de volledige of gedeeltelijke interne URL van het koppelingsdoel. Scheid meerdere filters met een komma. Letterlijke tekens voor tekenreeksen sluiten binnen enkele aanhalingstekens.

  De standaardwaarde is `'javascript:,'+window.location.hostname`

* **Koord van de Vraag van het Verlof**
Neemt URL-parameters op bij het evalueren van overeenkomsten met interne en externe filters.

  Schakel deze optie in als u URL-parameters wilt opnemen wanneer u URL&#39;s van koppelingsdoelen evalueert op basis van externe en interne filters.

De externe eigenschappen voor het bijhouden van koppelingen worden als code geïmplementeerd in het `analytics.sitecatalyst.js` -bestand dat voor een pagina wordt gegenereerd. De volgende voorbeeldcode wordt geproduceerd voor een pagina die met een kader wordt geassocieerd dat externe verbinding het volgen met de volgende configuratie heeft toegelaten:

* Extern filter is `'google.com'`
* Intern filter is de standaardwaarde van `'javascript:,'+window.location.hostname`
* De koorden van de vraag zijn niet inbegrepen wanneer het evalueren van het verbindingsdoel tegen filters.

```
s.trackExternalLinks= false;
s.linkExternalFilters= 'google.com';
s.linkInternalFilters= 'javascript:,'+window.location.hostname;
s.linkLeaveQueryString= false;
```

## Variabelegegevens verzenden met klikken op koppeling {#sending-variable-data-with-link-clicks}

U kunt AEM configureren om gebeurtenis- en variabele gegevens naar Adobe Analytics te verzenden wanneer een gebruiker op een koppeling klikt. De **eigenschappen van de Configuratie van de 1&rbrace; Verbinding het Volgen van de Configuratie** laten u toe om de gebeurtenissen en de variabelen van Adobe Analytics te specificeren om te volgen wanneer de verbinding klikt voorkomen.

De frameworktoewijzingen bepalen de gebeurtenis- en de veranderlijke waarden. U kunt Adobe Analytics-variabelen toewijzen aan de variabelen van de inhoudscomponenten die de gegevens opslaan die u wilt bijhouden wanneer op koppelingen wordt geklikt.

Om veranderlijke gegevens met verbinding te verzenden klikt:

1. [ open het kader van Adobe Analytics en breid de Verbinding die sectie van de Configuratie ](#configuring-link-tracking-for-an-adobe-analytics-framework) volgen uit.
1. Configureer de volgende eigenschappen volgens uw vereisten.

Eigenschappen voor het verzenden van variabele gegevens met koppelingsklikken:

* **Gebeurtenissen van het Spoor van de Verbinding**
Voer de Adobe Analytics-gebeurtenisvariabelen in die u wilt gebruiken voor het tellen van koppelingsklikken.

  Scheid meerdere variabelennamen met een komma.

  De standaardwaarde van `None` zorgt ervoor dat gebeurtenissen niet worden bijgehouden.

* **Spoor Vars van de Verbinding**
Voer de Adobe Analytics-variabelen in die u naar Adobe Analytics wilt verzenden wanneer op koppelingen wordt geklikt. Scheid meerdere variabelennamen met een komma.

  De standaardwaarde van `None` zorgt ervoor dat geen variabele gegevens worden verzonden.

Wanneer u de te verzenden gebeurtenissen en variabelen opgeeft, wordt de configuratie geïmplementeerd als code in het `analytics.sitecatalyst.js` -bestand dat voor een pagina wordt gegenereerd. De volgende voorbeeldcode wordt gegenereerd voor een pagina wanneer het framework de gebeurtenis `event10` en de eigenschap `prop4` bijhoudt:

```
s.linkTrackEvents= 'event10';
s.linkTrackVars= 'prop4';
```

## Configuratie voorbeeldkoppeling bijhouden {#example-link-tracking-configuration}

Voer de volgende procedures uit om het gedrag van het verbinden volgen van de integratie van Adobe Analytics te onderzoeken. De procedures tonen resultaten van [ Debugger van Adobe Marketing Cloud ](https://experienceleague.adobe.com/docs/debugger/using/experience-cloud-debugger.html).

### Algemene configuratie {#general-configuration}

In dit voorbeeld wordt getoond hoe de toewijzing werkt in de context van tracering en foutopsporing:

1. Open het framework dat aan een webpagina is gekoppeld.
1. Sleep de **component van de Pagina** aan het het in kaart brengen gebied van het kader. De **component van de Pagina** behoort tot de **Algemene** componentengroep in Sidekick.

   >[!NOTE]
   >
   >De component die u in een real-life scenario zou moeten gebruiken hangt van de component af die van (als bij allen) wordt geërft.
   >
   >Als dit niet het geval is, wordt er een eigen component weergegeven (door een subknooppunt Analytics in de paginacomponent te definiëren).

   Configureer de toewijzing volgens de volgende tabel door de variabele Analytics (SiteCatalyst) vanuit het linkerzijpaneel te slepen:

<table>
 <tbody>
  <tr>
   <th>CQ-variabele <br /> </th>
   <th>Ingang in de Browser van Variabelen <br /> </th>
   <th>Adobe Analytics-variabele</th>
  </tr>
  <tr>
   <td>pagedata.title</td>
   <td>Aangepaste eVar 1 (eVar1)</td>
   <td>eVar1</td>
  </tr>
  <tr>
   <td>eventdata.events.pageView</td>
   <td>Aangepast 1 (gebeurtenis1)</td>
   <td>event1</td>
  </tr>
 </tbody>
</table>

1. Sleep de component Search naar het toewijzingsgebied van het framework. De component van het Onderzoek behoort tot de Algemene componentengroep in Sidekick. Configureer de toewijzing volgens de volgende tabel door de variabele Analytics (SiteCatalyst) vanuit het linkerzijpaneel te slepen:

<table>
 <tbody>
  <tr>
   <th>CQ-variabele <br /> </th>
   <th>Invoer in de Variabelebrowser</th>
   <th>Adobe Analytics-variabele</th>
  </tr>
  <tr>
   <td>eventdata.keyword</td>
   <td>Aangepaste eVar 2 (eVar2)</td>
   <td>eVar2</td>
  </tr>
  <tr>
   <td>eventdata.results</td>
   <td>Aangepaste eVar 3 (eVar3)</td>
   <td>eVar3</td>
  </tr>
  <tr>
   <td>eventdata.events.search</td>
   <td>Aangepast 2 (gebeurtenis2)</td>
   <td>event2</td>
  </tr>
 </tbody>
</table>

### Externe koppelingstracering configureren {#configure-external-link-tracking}

1. In uw kader, breid het **gebied van de Configuratie van de Verbinding 0&rbrace; het volgen &lbrace;uit.**
1. Deselecteer **Downloads van het Spoor**.

1. Selecteer **Extern Spoor**.
1. Deselecteer **Koord van de Vraag van het Verlof**.
1. Gebruik de volgende waarde voor de **Externe lijst van Filters** om het als externe URL te identificeren:

   `'yahoo.com'`

1. Voeg de volgende waarde aan het **gebied van de Gebeurtenissen van het Spoor van de Verbinding** toe:

   ```
       event1,event2
   ```

1. Voeg de volgende waarde aan het **spoor van de Verbinding vars** gebied toe:

   ```
       eVar1,eVar2
   ```

1. Op de pagina die met het kader wordt geassocieerd, voeg de component van de Tekst van de a **&#x200B;**&#x200B;toe. Binnen de **component van de Tekst**, voeg een hyperlink toe die aan het volgende adres richt:

   `https://search.yahoo.com/?p=this`

1. Schakelaar aan **wijze van de Voorproef** en klik de verbinding.

De aangeroepen oproep ziet er zo uit als u deze bekijkt met de Adobe Marketing Cloud Debugger:

![ Debugger van Adobe Marketing Cloud ](assets/aa-leavequerysearch-blank.png)

>[!NOTE]
>
>De URL bevat niet de queryreeks: `?p=this`

### De URL-parameter opnemen {#include-the-url-parameter}

1. In het kader, breid het **gebied van de Configuratie van de Verbinding van 0&rbrace; het Volgen &lbrace;uit.**
1. Laat **Koord van de Vraag van het Verlof** toe.
1. Laad de paginavoorvertoning opnieuw en klik op de koppeling.

De vraagdetails die in Foutopsporing van Adobe Marketing Cloud verschijnen zijn gelijkaardig aan het volgende voorbeeld:

![ Debugger van Adobe Marketing Cloud opnieuw ](assets/aa-leavequerysearch-active.png)

>[!NOTE]
>
>Dit keer bevat de URL wel de queryreeks: `?p=this`

## Ad-hoc-koppeling bijhouden {#ad-hoc-link-tracking}

Bij het bijhouden van ad-hockoppelingen kunnen auteurs van inhoud het bijhouden van koppelingen voor een component configureren. De configuratie van de component treedt de **Verbinding het Volgen Configuratie** van het kader met voeten, zodat op pagina&#39;s die met het kader worden geassocieerd, **Tekst** componenten kunnen voor verbinding het volgen van URLs worden gevormd.

Bij het bijhouden van ad-hockoppelingen kunt u downloadkoppelingen, externe koppelingen en gebeurtenis- en variabelen bijhouden.

Als u ad-hockoppelingen wilt bijhouden, moet u:

* [ associeer de pagina die de **2&rbrace; component van de Tekst &lbrace;met het kader ](/help/sites-administering/adobeanalytics-connect.md#associating-a-page-with-a-adobe-analytics-framework) bevat.**
* [ vorm het kader van Adobe Analytics om ad-hoc verbinding het volgen ](#enabling-ad-hoc-link-tracking) toe te laten.
* [ vorm Verbinding het Volgen voor een component van de Tekst ](#configuring-link-tracking-for-a-text-component).

### Ad-hockoppelingen bijhouden inschakelen {#enabling-ad-hoc-link-tracking}

Configureer uw Adobe Analytics-framework om het bijhouden van ad-hockoppelingen in te schakelen.

1. Open het kader van Adobe Analytics en breid de **Verbinding die sectie van de Configuratie** volgen uit.

1. Laat **Ad hoc Verbinding het Volgen** toe.

   >[!NOTE]
   >
   >Niet alle gebruikerstypen hebben toegang tot dit selectievakje. Neem contact op met de sitebeheerder als u toegang nodig hebt.

>[!NOTE]
>
>De configuratie van XSS Antisamy is nu in SLING onder weg **/libs/sling/xss.config.xml** en de volgende regels moeten aan ad hoc worden toegevoegd zodat het verbinden werkt:

#### Toevoegingsregel ankertag {#anchor-tag-rule-extension}

```xml
<attribute name="onclick">
    <literal-list>
        <literal value="CQ_Analytics.Sitecatalyst.customTrack(this)"/>
    </literal-list>
</attribute>
<attribute name="adhocenable">
    <literal-list>
        <literal value="true"/>
        <literal value="false"/>
    </literal-list>
</attribute>
<attribute name="adhocevents">
    <regexp-list>
        <regexp name="anything"/>
    </regexp-list>
</attribute>
<attribute name="adhocevars">
    <regexp-list>
        <regexp name="anything"/>
    </regexp-list>
</attribute>
```

### Koppeling bijhouden configureren voor een tekstcomponent {#configuring-link-tracking-for-a-text-component}

Alvorens u ad hoc verbinding het volgen voor **componenten van de Tekst** kunt vormen zelf, moeten de volgende configuraties reeds uitgevoerd zijn:

* Het [ kader van Adobe Analytics wordt gevormd om ad hoc verbinding het volgen ](#enabling-ad-hoc-link-tracking) toe te laten.
* De [ pagina die de **2&rbrace; component van de Tekst &lbrace;bevat wordt geassocieerd met het kader ](/help/sites-administering/adobeanalytics-connect.md#associating-a-page-with-a-adobe-analytics-framework).**

Gebruik de volgende procedure om verbinding het volgen voor de component van de a **Tekst** te vormen:

1. Open de pagina op geef wijze uit en geef de **&#x200B;**&#x200B;component van de Tekst uit.

1. Selecteer de tekst die u als hypertekst wilt gebruiken en klik op de knop Hyperlink.

   ![ het pictogram van de Verbinding ](do-not-localize/chlimage_1.png)

1. Voeg de doel-URL toe in het vak Koppelen naar en vouw vervolgens het gebied Koppeling bijhouden uit.

   >[!NOTE]
   >
   >Het bijhouden van aangepaste koppelingen is zichtbaar als een afzonderlijke actie naast de handeling Koppeling/Ontkoppelen (pictogram Analyse).
   >
   >Het zal slechts worden toegelaten wanneer u een geldige Verbinding in RTE hebt geselecteerd.

   ![ Toelatend verbinding het volgen ](assets/aa-17.png)

1. Laat **het Volgen van de Verbinding van de Douane toe** om de verbinding het volgen configuratie van het kader van Adobe Analytics met voeten te treden en verbinding het volgen voor de huidige verbinding toe te laten.

1. (Facultatief) om gebeurtenissen met de verbinding te volgen klikt, voeg de gebeurtenisnamen van Adobe Analytics op het **omvatten de Variabelen van Adobe Analytics** gebied toe. Plaats bijvoorbeeld een komma tussen de verschillende gebeurtenisnamen

   `event1, event22`.

1. (Facultatief) om veranderlijke gegevens met de verbinding te volgen klikt, voeg de variabelen van Adobe Analytics op het **omvatten de Variabelen van Adobe Analytics** gebied toe. Gebruik een van de volgende indelingen:

   * *`<Variable-name>`*: *`<Dynamic Value>`*
   * *`<Variable-name>`*: *`'CONSTANT'`*

   Aan de hand van de volgende voorbeelden wordt elke indeling geïllustreerd:

   * `eVar10:pagedata.title`
   * `prop1: 'Aubergine'`

   Scheid meerdere waarden met een komma.

1. Selecteer **O.K.**.
