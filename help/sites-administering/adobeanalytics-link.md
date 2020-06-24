---
title: Koppelingen bijhouden configureren voor Adobe Analytics
seo-title: Koppelingen bijhouden configureren voor Adobe Analytics
description: Leer over het vormen van verbinding het volgen voor SiteCatalyst.
seo-description: Leer over het vormen van verbinding het volgen voor SiteCatalyst.
uuid: b6d5bd1c-f91a-4d38-9e9e-dc2bcb271dae
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: fe6ba6af-f500-4c0d-b984-fb617d4bf48a
translation-type: tm+mt
source-git-commit: 70b18dbe351901abb333d491dd06a6c1c1c569d6
workflow-type: tm+mt
source-wordcount: '1615'
ht-degree: 0%

---


# Koppelingen bijhouden configureren voor Adobe Analytics{#configuring-link-tracking-for-adobe-analytics}

Wanneer gebruikers op koppelingen op pagina&#39;s van uw website klikken, kunt u gerelateerde informatie vastleggen in Adobe Analytics. Gebruik bijvoorbeeld het bijhouden van koppelingen om te leren hoe gebruikers met uw site werken, het downloaden van bestanden bijhouden en afsluitkoppelingen volgen.

## Koppelingen bijhouden configureren voor een Adobe Analytics Framework {#configuring-link-tracking-for-an-adobe-analytics-framework}

1. Ga met **Navigatie** via **Implementatie** naar de sectie **Adobe Analytics** . Ga **Cloud Servicen** naar de sectie Adobe.

1. Open het vereiste Adobe Analytics-framework met **Configuraties** tonen.
1. Breid de sectie van de Configuratie **van het Volgen van de** Verbinding uit en vorm zoals vereist (deze pagina verstrekt verdere details):

   ![aa-08](assets/aa-08.png)

## Bestandsdownloads volgen {#tracking-file-downloads}

Configureer het Adobe Analytics-framework zodat bestanden die u hebt gedownload van gekoppelde pagina&#39;s, automatisch worden bijgehouden als downloads in Adobe Analytics. Wanneer u het bijhouden van downloads inschakelt, worden alleen de bestandstypen bijgehouden die u opgeeft.

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

Als downloadtracering bijvoorbeeld is ingeschakeld voor PDF-bestanden en gebruikers op koppelingen naar PDF-bestanden klikken, wordt de download van de PDF bijgehouden.

De eigenschappen voor het bijhouden van de download van het framework worden geïmplementeerd als code in het `analytics.sitecatalyst.js` bestand dat voor een pagina wordt gegenereerd. In het volgende codevoorbeeld wordt de standaardconfiguratie voor het bijhouden van downloads weergegeven:

```
s.trackDownloadLinks= true;
s.linkDownloadFileTypes= 'exe,zip,wav,mp3,mov,mpg,avi,wmv,doc,pdf,xls';
```

U schakelt het bijhouden van downloads voor uw Adobe Analytics-framework als volgt in:

1. [Open het Adobe Analytics-framework en vouw de sectie](#configuring-link-tracking-for-an-adobe-analytics-framework)Configuratie van bijhouden van koppelingen uit.
1. Schakel **Trackdownloads** in.
1. Typ in het vak Bestandstypen **** downloaden de bestandsextensies voor de bestandstypen die u wilt bijhouden.

## Externe koppelingen bijhouden {#tracking-external-links}

U kunt het klikken van externe verbindingen (uitgangsverbindingen) op uw pagina&#39;s volgen.

Externe koppelingen voor uw Adobe Analytics-framework volgen:

1. [Open het Adobe Analytics-framework en vouw de sectie Configuratie **van** Koppeling bijhouden uit](#configuring-link-tracking-for-an-adobe-analytics-framework).
1. Configureer de volgende eigenschappen volgens uw vereisten.

Eigenschappen voor het bijhouden wanneer op externe koppelingen wordt geklikt:

* **Houd External** Enables external link tracking bij.

* **Externe filters**(optioneel) Definieert filters voor het afstemmen van de externe URL&#39;s van de koppelingsdoelen. Wanneer de koppelingsdoelen overeenkomen met het filter, wordt de koppeling bijgehouden. Externe filters zijn handig voor het bijhouden van slechts enkele externe koppelingen op uw pagina&#39;s.

   Als u de externe koppelingen wilt opgeven die moeten worden bijgehouden, typt u de volledige URL of een deel van de URL van het koppelingsdoel. Scheid meerdere filters met een komma. Letterlijke tekens voor tekenreeksen sluiten binnen enkele aanhalingstekens. Bij geen enkele waarde (de standaardwaarde van `''`, twee enkele aanhalingstekens) worden alle externe koppelingen bijgehouden.

* **Interne filters** definiëren filters voor het afstemmen van de URL&#39;s van interne koppelingen. Wanneer de koppeling verwijst naar URL&#39;s die overeenkomen met dit filter, wordt de koppeling niet bijgehouden. De standaardwaarde is een javascript-opdracht die de hostnaam van de URL voor het huidige vensteradres retourneert.

   Als u de interne koppelingen wilt opgeven die niet worden bijgehouden, typt u de volledige of gedeeltelijke interne URL van het koppelingsdoel. Scheid meerdere filters met een komma. Letterlijke tekens voor tekenreeksen sluiten binnen enkele aanhalingstekens.

   De standaardwaarde is `'javascript:,'+window.location.hostname`

* **Kies Tekenreeks** niet gebruiken om URL-parameters op te nemen bij het evalueren van overeenkomsten met interne en externe filters.

   Schakel deze optie in om URL-parameters op te nemen wanneer u URL&#39;s van koppelingsdoelen evalueert op basis van externe en interne filters.

De externe eigenschappen voor het bijhouden van koppelingen worden geïmplementeerd als code in het `analytics.sitecatalyst.js` bestand dat voor een pagina wordt gegenereerd. De volgende voorbeeldcode wordt geproduceerd voor een pagina die met een kader wordt geassocieerd dat externe verbinding het volgen met de volgende configuratie heeft toegelaten:

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

U kunt AEM zodanig configureren dat gebeurtenis- en variabele gegevens naar Adobe Analytics worden verzonden wanneer een gebruiker op een koppeling klikt. Met de eigenschappen Configuratie **van** Koppeling bijhouden kunt u de Adobe Analytics-gebeurtenissen en -variabelen opgeven die moeten worden bijgehouden wanneer op een koppeling wordt geklikt.

De frameworktoewijzingen bepalen de gebeurtenis- en veranderlijke waarden. U kunt Adobe Analytics-variabelen toewijzen aan de variabelen van uw inhoudscomponenten, waarin de gegevens worden opgeslagen die u wilt bijhouden wanneer op koppelingen wordt geklikt.

Om veranderlijke gegevens met verbinding te verzenden klikt:

1. [Open het Adobe Analytics-framework en vouw de sectie](#configuring-link-tracking-for-an-adobe-analytics-framework)Configuratie van bijhouden van koppelingen uit.
1. Configureer de volgende eigenschappen volgens uw vereisten.

Eigenschappen voor het verzenden van variabele gegevens met koppelingsklikken:

* **Gebeurtenissen** bijhouden koppelen Voer de Adobe Analytics-gebeurtenisvariabelen in die u wilt gebruiken voor het tellen van koppelingsklikken.

   Scheid meerdere variabelennamen met een komma.

   De standaardwaarde van `None` zorgt ervoor dat gebeurtenissen niet worden bijgehouden.

* **Koppelingentrack Vars** Voer de Adobe Analytics-variabelen in die u naar Adobe Analytics wilt verzenden wanneer op koppelingen wordt geklikt. Scheid meerdere variabelennamen met een komma.

   De standaardwaarde van `None` zorgt ervoor dat geen variabele gegevens worden verzonden.

Wanneer u de gebeurtenissen en variabelen specificeert om te verzenden, wordt de configuratie uitgevoerd als code in het `analytics.sitecatalyst.js` dossier dat voor een pagina wordt geproduceerd. De volgende voorbeeldcode wordt gegenereerd voor een pagina wanneer het framework de `event10` gebeurtenis en de `prop4` eigenschap bijhoudt:

```
s.linkTrackEvents= 'event10';
s.linkTrackVars= 'prop4';
```

## Configuratie voorbeeldkoppeling bijhouden {#example-link-tracking-configuration}

Voer de volgende procedures uit om het gedrag van het volgen van koppelingen van de integratie van Adobe Analytics te onderzoeken. De procedures tonen resultaten van Foutopsporing van de [Adobe Marketing Cloud](https://docs.adobe.com/content/help/en/debugger/using/experience-cloud-debugger.html).

### Algemene configuratie {#general-configuration}

In dit voorbeeld wordt getoond hoe de toewijzing werkt in de context van tracering en foutopsporing:

1. Open het framework dat aan een webpagina is gekoppeld.
1. Sleep de component **Pagina** naar het toewijzingsgebied van het framework. De component **Pagina** behoort tot de **groep Algemeen** in Sidetrap.

   >[!NOTE]
   >
   >De component die u in een real-life scenario zou moeten gebruiken hangt van de component af die van (als bij allen) wordt geërft.
   >
   >Als dit niet het geval is, wordt er een eigen component weergegeven (door een subknooppunt Analytics in de paginacomponent te definiëren).

   Configureer de toewijzing volgens de volgende tabel door de variabele Analytics (SiteCatalyst) vanuit het linkerzijpaneel te slepen:

<table>
 <tbody>
  <tr>
   <th>CQ-variabele<br /> </th>
   <th>Invoer in de Variabelebrowser<br /> </th>
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

1. Sleep de component Search naar het toewijzingsgebied van het framework. De component van het Onderzoek behoort tot de Algemene componentengroep in Sidetrap. Configureer de toewijzing volgens de volgende tabel door de variabele Analytics (SiteCatalyst) vanuit het linkerzijpaneel te slepen:

<table>
 <tbody>
  <tr>
   <th>CQ-variabele<br /> </th>
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

### Externe koppelingcontrole configureren {#configure-external-link-tracking}

1. In uw kader, breid het gebied van de Configuratie van de **Verbinding het volgen** uit.
1. Schakel **Downloads** bijhouden uit.

1. Selecteer Externe **** track.
1. Schakel **Zoekreeks** behouden uit.
1. Gebruik de volgende waarde voor de lijst **Externe filters** om deze als een externe URL te identificeren:

   `‘yahoo.com’`

1. Voeg de volgende waarde aan het gebied van de Gebeurtenissen **van het Spoor van de** Verbinding toe:

   ```
       event1,event2
   ```

1. Voeg de volgende waarde aan het de spoorvars van de **Verbinding** gebied toe:

   ```
       eVar1,eVar2
   ```

1. Voeg op de pagina die aan het framework is gekoppeld een **component Text** toe. Voeg binnen de component **Text** een hyperlink toe die naar het volgende adres verwijst:

   `https://search.yahoo.com/?p=this`

1. Schakel over naar de modus **** Voorvertoning en klik op de koppeling.

De aangeroepen oproep ziet er als volgt uit wanneer deze wordt bekeken met de Adobe Marketing Cloud Foutopsporing:

![aa-leavequery search-blank](assets/aa-leavequerysearch-blank.png)

>[!NOTE]
>
>De URL bevat niet de queryreeks: `?p=this`

### De URL-parameter opnemen {#include-the-url-parameter}

1. In het kader, breid het **Verbinding het Volgen gebied van de Configuratie** uit.
1. Schakel **Zoekreeks** behouden in.
1. Laad de paginavoorvertoning opnieuw en klik op de koppeling.

De vraagdetails die in Foutopsporing van de Adobe Marketing Cloud verschijnen zijn gelijkaardig aan het volgende voorbeeld:

![aa-leavequeryquerysearch-active](assets/aa-leavequerysearch-active.png)

>[!NOTE]
>
>Dit keer bevat de URL wel de queryreeks: `?p=this`

## Ad-hoc-koppeling bijhouden {#ad-hoc-link-tracking}

Bij het bijhouden van ad-hockoppelingen kunnen auteurs van inhoud het bijhouden van koppelingen voor een component configureren. De configuratie van de component treedt de Configuratie **van het** Spoor van de Verbinding van het kader met voeten, zodat op pagina&#39;s die met het kader worden geassocieerd, kunnen de componenten van de **Tekst** voor verbinding het volgen van URLs worden gevormd.

Met Ad-hockoppelingen kunt u downloadkoppelingen, externe koppelingen en gebeurtenis- en variabelen bijhouden.

Als u ad-hockoppelingen wilt bijhouden, moet u:

* [Koppel de pagina die de **component Text** bevat aan het framework](/help/sites-administering/adobeanalytics-connect.md#associating-a-page-with-a-adobe-analytics-framework).
* [Configureer het Adobe Analytics-framework om ad-hockoppelingen te kunnen bijhouden](#enabling-ad-hoc-link-tracking).
* [Configureer Koppeling bijhouden voor een tekstcomponent](#configuring-link-tracking-for-a-text-component).

### Ad-hockoppelingen bijhouden inschakelen {#enabling-ad-hoc-link-tracking}

Configureer uw Adobe Analytics-framework om het bijhouden van ad-hockoppelingen in te schakelen.

1. Open het Adobe Analytics-framework en vouw de sectie Configuratie **van** Koppeling bijhouden uit.

1. Schakel **Ad-hockoppelingen bijhouden** in.

   >[!NOTE]
   >
   >Niet alle gebruikerstypen hebben toegang tot dit selectievakje. Neem contact op met de sitebeheerder als u toegang nodig hebt.

>[!NOTE]
>
>De configuratie van XSS Antisamy is nu in SLING onder weg **/libs/sling/xss.config.xml** en de volgende regels moeten aan voor ad hoc het verbinden aan het werk worden toegevoegd:

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

Voordat u ad-hockoppelingen bijhouden kunt configureren voor **Text** -componenten zelf, moeten de volgende configuraties al zijn geïmplementeerd:

* Het [Adobe Analytics-framework is geconfigureerd om ad-hockoppelingen te kunnen bijhouden](#enabling-ad-hoc-link-tracking).
* De [pagina die de **component Text** bevat, is gekoppeld aan het framework](/help/sites-administering/adobeanalytics-connect.md#associating-a-page-with-a-adobe-analytics-framework).

Gebruik de volgende procedure om verbinding het volgen voor een component van de **Tekst** te vormen:

1. Open de pagina in de bewerkingsmodus en bewerk de **tekstcomponent** .

1. Selecteer de tekst die u als hypertekst wilt gebruiken en klik op de knop Hyperlink.

   ![](do-not-localize/chlimage_1.png)

1. Voeg de doel-URL toe in het vak Koppelen naar en vouw vervolgens het gebied Koppeling bijhouden uit.

   >[!NOTE]
   >
   >Het bijhouden van aangepaste koppelingen is zichtbaar als een aparte actie naast de handeling Koppeling/Ontkoppelen (Analytics-pictogram).
   >
   >Het zal slechts worden toegelaten wanneer u een geldige Verbinding in RTE hebt geselecteerd.

   ![aa-17](assets/aa-17.png)

1. Schakel **Aangepaste koppeling bijhouden** in om de configuratie voor het bijhouden van koppelingen van het Adobe Analytics-framework te overschrijven en om het bijhouden van koppelingen voor de huidige koppeling in te schakelen.

1. (Optioneel) Als u gebeurtenissen wilt bijhouden met de klik op de koppeling, voegt u Adobe Analytics-gebeurtenisnamen toe in het veld Adobe Analytics-variabelen **opnemen** . Meerdere gebeurtenisnamen van elkaar scheiden met komma&#39;s, bijvoorbeeld

   `event1, event22`.

1. (Optioneel) Als u variabele gegevens wilt bijhouden met de klik op de koppeling, voegt u Adobe Analytics-variabelen toe in het veld Adobe Analytics-variabelen **opnemen** . Gebruik een van de volgende indelingen:

   * *`<Variable-name>`*: *`<Dynamic Value>`*
   * *`<Variable-name>`*: *`‘CONSTANT'`*
   Aan de hand van de volgende voorbeelden wordt elke indeling geïllustreerd:

   * `eVar10:pagedata.title`
   * `prop1: ‘Aubergine'`
   Scheid meerdere waarden met een komma.

1. Selecteer **OK**.

