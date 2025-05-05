---
title: Ondersteuning voor nieuwe landinstellingen voor lokalisatie van adaptieve formulieren
description: Met AEM Forms kunt u nieuwe landinstellingen toevoegen voor het lokaliseren van adaptieve formulieren. De landinstellingen die standaard worden ondersteund, zijn Engels, Frans, Duits en Japans.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
feature: Adaptive Forms,Foundation Components
role: Admin,User
exl-id: 2ed4d99e-0e90-4b21-ac17-aa6707a3ba7d
solution: Experience Manager, Experience Manager Forms
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Ondersteuning voor nieuwe landinstellingen voor lokalisatie van adaptieve formulieren{#supporting-new-locales-for-adaptive-forms-localization}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/supporting-new-language-localization.html) |
| AEM 6,5 | Dit artikel |

## Over woordenboeken voor landinstellingen {#about-locale-dictionaries}

De lokalisatie van adaptieve formulieren is afhankelijk van twee typen taalwoordenboeken:

**vorm-specifiek woordenboek** bevat koorden die in adaptieve vormen worden gebruikt. Bijvoorbeeld labels, veldnamen, foutberichten, Help-beschrijvingen enzovoort. Het wordt beheerd als een set XLIFF-bestanden voor elke landinstelling en u hebt toegang tot dit bestand via `https://<host>:<port>/libs/cq/i18n/translator.html` .

**Globale woordenboeken** Er zijn twee globale woordenboeken, die als voorwerpen JSON, in AEM cliëntbibliotheek worden beheerd. Deze woordenboeken bevatten standaardfoutberichten, naam van de maand, valutasymbolen, datum- en tijdpatronen, enzovoort. U vindt deze woordenboeken in CRXDe Lite op /libs/fd/xfaforms/clientlibs/I18N. Deze locaties bevatten afzonderlijke mappen voor elke landinstelling. Omdat algemene woordenboeken meestal niet regelmatig worden bijgewerkt, kunnen browsers door afzonderlijke JavaScript-bestanden voor elke landinstelling in cache te houden en het gebruik van de netwerkbandbreedte verminderen wanneer ze verschillende adaptieve formulieren op dezelfde server gebruiken.

### Hoe lokalisatie van adaptief formulier werkt {#how-localization-of-adaptive-form-works}

Er zijn twee methoden om de landinstelling van het adaptieve formulier te bepalen. Wanneer een adaptief formulier wordt gegenereerd, geeft dit de aangevraagde landinstelling aan met:

* Bekijk de `[local]` kiezer in het aangepaste formulier-URL. De opmaak van de URL is `http://host:port/content/forms/af/[afName].[locale].html?wcmmode=disabled` . Met `[local]` -kiezer kunt u een adaptief formulier in de cache plaatsen.

* de volgende parameters in de opgegeven volgorde bekijken:

   * Request-parameter `afAcceptLang`
Als u de landinstelling van de browser van gebruikers wilt overschrijven, kunt u de `afAcceptLang` request-parameter doorgeven om de landinstelling te forceren. De volgende URL is bijvoorbeeld gedwongen om het formulier te genereren in een Japanse landinstelling:
     `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

   * De landinstelling van de browser die voor de gebruiker is ingesteld en die in de aanvraag wordt opgegeven met de header `Accept-Language` .

   * Taalinstelling van de gebruiker die is opgegeven in AEM.

   * Landinstelling browser is standaard ingeschakeld. Als u de landinstelling van de browser wilt wijzigen,
      * Open configuratiebeheer. De URL is `http://[server]:[port]/system/console/configMgr`
      * Zoek en open de **[!UICONTROL Adaptive Form and Interactive Communication Web Channel]** -configuratie.
      * Wijzig de status van de optie **[!UICONTROL Use Browser Locale]** en **[!UICONTROL Save]** de configuratie.

Nadat de landinstelling is vastgesteld, wordt in het adaptieve formulier het formulierspecifieke woordenboek gekozen. Als het formulierspecifieke woordenboek voor de aangevraagde landinstelling niet wordt gevonden, wordt het woordenboek gebruikt voor de taal waarin het adaptieve formulier is geschreven.

Als er geen informatie over de landinstelling aanwezig is, wordt het adaptieve formulier geleverd in de oorspronkelijke taal van het formulier. De oorspronkelijke taal is de taal die wordt gebruikt bij de ontwikkeling van het adaptieve formulier.

Als er geen clientbibliotheek voor de aangevraagde landinstelling bestaat, wordt in de bibliotheek gecontroleerd of er taalcode in de landinstelling aanwezig is. Als de aangevraagde landinstelling bijvoorbeeld `en_ZA` (Zuid-Afrikaans Engels) is en de clientbibliotheek voor `en_ZA` niet bestaat, gebruikt het adaptieve formulier de clientbibliotheek voor de taal `en` (Engels), als deze bestaat. Als er echter geen van deze functies bestaat, wordt in het adaptieve formulier het woordenboek voor de landinstelling `en` gebruikt.

## Ondersteuning voor lokalisatie toevoegen voor niet-ondersteunde landinstellingen {#add-localization-support-for-non-supported-locales}

AEM Forms ondersteunt momenteel de lokalisatie van adaptieve formulieren met inhoud in het Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR).

Ondersteuning voor een nieuwe landinstelling toevoegen bij runtime voor adaptieve formulieren:

1. [Een landinstelling toevoegen aan de GuideLocalizationService-service](../../forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [XFA-clientbibliotheek toevoegen voor een landinstelling](../../forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Aangepaste clientbibliotheek voor een landinstelling toevoegen](../../forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Ondersteuning voor landinstellingen toevoegen voor het woordenboek](../../forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [De server opnieuw starten](../../forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### Een landinstelling toevoegen aan de Guide Localization-service {#add-a-locale-to-the-guide-localization-service-br}

1. Ga naar `https://'[server]:[port]'/system/console/configMgr` .
1. Klik om de **component van de Dienst van de Lokalisatie van de Gids uit te geven 0&rbrace;.**
1. Voeg de landinstelling toe die u wilt toevoegen aan de lijst met ondersteunde landinstellingen.

![ GuideLocalizationService ](assets/configservice.png)

### XFA-clientbibliotheek toevoegen voor een landinstelling {#add-xfa-client-library-for-a-locale-br}

Maak een knooppunt van het type `cq:ClientLibraryFolder` onder `etc/<folderHierarchy>` , met categorie `xfaforms.I18N.<locale>` en voeg de volgende bestanden toe aan de clientbibliotheek:

* **I18N.js** bepalend `xfalib.locale.Strings` voor `<locale>` zoals bepaald in `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`.

* **js.txt** die het volgende bevatten:

```text
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Aangepaste clientbibliotheek voor een landinstelling toevoegen {#add-adaptive-form-client-library-for-a-locale-br}

Maak een knooppunt van het type `cq:ClientLibraryFolder` onder `etc/<folderHierarchy>` , met categorie als `guides.I18N.<locale>` en afhankelijkheden als `xfaforms.3rdparty` , `xfaforms.I18N.<locale>` en `guide.common` . &quot;

Voeg de volgende bestanden toe aan de clientbibliotheek:

* **i18n.js** het bepalen `guidelib.i18n`, die patronen van &quot;agendaSymbols&quot;hebben, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` voor `<locale>` volgens de XFA specificaties in [ Vastgestelde Specificatie van de Landinstelling ](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf) worden beschreven. U kunt ook zien hoe deze is gedefinieerd voor andere ondersteunde landinstellingen in `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js` .
* **LogMessages.js** definiërend `guidelib.i18n.strings` en `guidelib.i18n.LogMessages` voor `<locale>` zoals die in `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js` wordt bepaald.
* **js.txt** die het volgende bevatten:

```text
i18n.js
LogMessages.js
```

### Ondersteuning voor landinstellingen toevoegen voor het woordenboek {#add-locale-support-for-the-dictionary-br}

Voer deze stap alleen uit als de `<locale>` die u toevoegt, niet behoort tot `en` , `de` , `es` , `fr` , `it` , `pt-br` , `zh-cn` , `zh-tw` , `ja` , `ko-kr` .

1. Maak een `nt:unstructured` node `languages` under `etc` , als dit nog niet het geval is.

1. Voeg een multi-getaxeerde koordbezit `languages` aan de knoop toe, als niet reeds aanwezig.
1. Voeg de `<locale>` standaardwaarden voor de landinstelling `de` , `es` , `fr` , `it` , `pt-br` , `zh-cn` , `zh-tw` , `ja` en `ko-kr` toe als deze nog niet aanwezig zijn.

1. Voeg de waarde `<locale>` toe aan de waarden van de eigenschap `languages` van `/etc/languages` .

De `<locale>` wordt weergegeven bij `https://'[server]:[port]'/libs/cq/i18n/translator.html` .

### De server opnieuw starten {#restart-the-server}

Start de AEM server opnieuw om de toegevoegde landinstelling te activeren.

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

## Voorbeeldbibliotheken voor het toevoegen van ondersteuning voor Spaans {#sample-libraries-for-adding-support-for-spanish}

Voorbeeld van clientbibliotheken voor het toevoegen van ondersteuning voor Spaans

[Bestand ophalen](assets/sample.zip)
