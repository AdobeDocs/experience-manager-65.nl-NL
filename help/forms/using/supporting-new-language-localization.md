---
title: Ondersteuning voor nieuwe landinstellingen voor lokalisatie van adaptieve formulieren
seo-title: Ondersteuning voor nieuwe landinstellingen voor lokalisatie van adaptieve formulieren
description: Met AEM Forms kunt u nieuwe landinstellingen toevoegen voor het lokaliseren van adaptieve formulieren. De landinstellingen die standaard worden ondersteund, zijn Engels, Frans, Duits en Japans.
seo-description: Met AEM Forms kunt u nieuwe landinstellingen toevoegen voor het lokaliseren van adaptieve formulieren. De landinstellingen die standaard worden ondersteund, zijn Engels, Frans, Duits en Japans.
uuid: 7f9fab6b-8d93-46bb-8c7c-7b723d5159ea
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
discoiquuid: d4e2acb0-8d53-4749-9d84-15b8136e610b
docset: aem65
translation-type: tm+mt
source-git-commit: 1a4bfc91cf91b4b56cc4efa99f60575ac1a9a549
workflow-type: tm+mt
source-wordcount: '813'
ht-degree: 0%

---


# Ondersteuning voor nieuwe landinstellingen voor lokalisatie van adaptieve formulieren{#supporting-new-locales-for-adaptive-forms-localization}

## Over woordenboeken voor landinstellingen {#about-locale-dictionaries}

De lokalisatie van adaptieve formulieren is afhankelijk van twee typen taalwoordenboeken:

**Formulierspecifiek woordenboek** bevat tekenreeksen die worden gebruikt in adaptieve formulieren. Bijvoorbeeld labels, veldnamen, foutberichten, Help-beschrijvingen enzovoort. Het wordt beheerd als een set XLIFF-bestanden voor elke landinstelling en u kunt het bestand openen op `https://<host>:<port>/libs/cq/i18n/translator.html`.

**Algemene woordenboeken** Er zijn twee algemene woordenboeken, beheerd als JSON-objecten, in AEM clientbibliotheek. Deze woordenboeken bevatten standaardfoutberichten, naam van de maand, valutasymbolen, datum- en tijdpatronen, enzovoort. U vindt deze woordenboeken in CRXDe Lite op /libs/fd/xfaforms/clientlibs/I18N. Deze locaties bevatten afzonderlijke mappen voor elke landinstelling. Omdat algemene woordenboeken meestal niet vaak worden bijgewerkt, kunnen browsers door afzonderlijke JavaScript-bestanden voor elke landinstelling te bewaren deze in cache plaatsen en het gebruik van de netwerkbandbreedte verminderen wanneer ze verschillende adaptieve formulieren op dezelfde server gebruiken.

### Hoe lokalisatie van adaptief formulier werkt {#how-localization-of-adaptive-form-works}

Er zijn twee methoden om de landinstelling van het adaptieve formulier te bepalen. Wanneer een adaptief formulier wordt gegenereerd, geeft dit de aangevraagde landinstelling aan met:

* Bekijk de `[local]` kiezer in het aangepaste formulier-URL. The format of the URL is `http://host:port/content/forms/af/[afName].[locale].html?wcmmode=disabled`. Met `[local]` kiezer kunt u een adaptief formulier in de cache plaatsen.

* de volgende parameters in de opgegeven volgorde bekijken:

   * De parameter van het verzoek `afAcceptLang`om de browser scène van gebruikers met voeten te treden, kunt u overgaan 
`afAcceptLang` request parameter to force the locale. Met de volgende URL wordt het formulier bijvoorbeeld geforceerd weergegeven in de Japanse landinstelling:
      `https://'[server]:[port]'/<contextPath>/<formFolder>/<formName>.html?wcmmode=disabled&afAcceptLang=ja`

   * De landinstelling van de browser die voor de gebruiker is ingesteld. Deze landinstelling wordt in de aanvraag opgegeven met behulp van de `Accept-Language` koptekst.

   * Taalinstelling van de gebruiker opgegeven in AEM.

   * Landinstelling browser is standaard ingeschakeld. Als u de landinstelling van de browser wilt wijzigen,
      * Open configuratiebeheer. De URL is `http://[server]:[port]/system/console/configMgr`
      * Zoek en open de **[!UICONTROL Adaptive Form and Interactive Communication Web Channel]** configuratie.
      * Wijzig de status van de **[!UICONTROL Use Browser Locale]** optie en **[!UICONTROL Save]** de configuratie.

Nadat de landinstelling is vastgesteld, wordt in het adaptieve formulier het formulierspecifieke woordenboek gekozen. Als het formulierspecifieke woordenboek voor de aangevraagde landinstelling niet wordt gevonden, wordt het woordenboek gebruikt voor de taal waarin het adaptieve formulier is geschreven.

Als er geen landinstellingsgegevens aanwezig zijn, wordt het adaptieve formulier geleverd in de oorspronkelijke taal van het formulier. De oorspronkelijke taal is de taal die wordt gebruikt bij de ontwikkeling van het adaptieve formulier.

Als er geen clientbibliotheek voor de aangevraagde landinstelling bestaat, wordt in de bibliotheek gecontroleerd of er taalcode aanwezig is in de landinstelling. Als de aangevraagde landinstelling bijvoorbeeld `en_ZA` (Zuid-Afrikaans Engels) is en de clientbibliotheek voor `en_ZA` niet bestaat, gebruikt het adaptieve formulier de clientbibliotheek voor `en` (Engels) taal, als deze bestaat. Als er echter geen van deze mogelijkheden bestaat, wordt in het adaptieve formulier het woordenboek voor de `en` landinstelling gebruikt.

## Ondersteuning voor lokalisatie toevoegen voor niet-ondersteunde landinstellingen {#add-localization-support-for-non-supported-locales}

AEM Forms ondersteunt momenteel de lokalisatie van adaptieve formulieren met inhoud in het Engels (en), Spaans (es), Frans (fr), Italiaans (it), Duits (de), Japans (ja), Portugees-Braziliaans (pt-BR), Chinees (zh-CN), Chinees-Taiwan (zh-TW) en Koreaans (ko-KR).

Ondersteuning voor een nieuwe landinstelling toevoegen bij runtime voor adaptieve formulieren:

1. [Een landinstelling toevoegen aan de GuideLocalizationService-service](../../forms/using/supporting-new-language-localization.md#p-add-a-locale-to-the-guide-localization-service-br-p)

1. [XFA-clientbibliotheek toevoegen voor een landinstelling](../../forms/using/supporting-new-language-localization.md#p-add-xfa-client-library-for-a-locale-br-p)

1. [Aangepaste clientbibliotheek voor een landinstelling toevoegen](../../forms/using/supporting-new-language-localization.md#p-add-adaptive-form-client-library-for-a-locale-br-p)
1. [Ondersteuning voor landinstellingen toevoegen voor het woordenboek](../../forms/using/supporting-new-language-localization.md#p-add-locale-support-for-the-dictionary-br-p)
1. [De server opnieuw starten](../../forms/using/supporting-new-language-localization.md#p-restart-the-server-p)

### Een landinstelling toevoegen aan de Guide Localization-service {#add-a-locale-to-the-guide-localization-service-br}

1. Go to `https://'[server]:[port]'/system/console/configMgr`.
1. Klik om de **Guide Localization Service** -component te bewerken.
1. Voeg de landinstelling toe die u wilt toevoegen aan de lijst met ondersteunde landinstellingen.

![GuideLocalizationService](assets/configservice.png)

### XFA-clientbibliotheek toevoegen voor een landinstelling {#add-xfa-client-library-for-a-locale-br}

Maak een knooppunt van het type `cq:ClientLibraryFolder` onder `etc/<folderHierarchy>`, met categorie `xfaforms.I18N.<locale>`, en voeg de volgende bestanden toe aan de clientbibliotheek:

* **I18N.js** die `xfalib.locale.Strings` voor `<locale>` zoals bepaald in `/etc/clientlibs/fd/xfaforms/I18N/ja/I18N`. bepaalt

* **js.txt** met het volgende:

```text
/libs/fd/xfaforms/clientlibs/I18N/Namespace.js
I18N.js
/etc/clientlibs/fd/xfaforms/I18N/LogMessages.js
```

### Aangepaste clientbibliotheek voor een landinstelling toevoegen {#add-adaptive-form-client-library-for-a-locale-br}

Maak een knooppunt van het type `cq:ClientLibraryFolder` onder `etc/<folderHierarchy>`, met categorie als `guides.I18N.<locale>` en en afhankelijkheden als `xfaforms.3rdparty`, `xfaforms.I18N.<locale>` en `guide.common`. &quot;

Voeg de volgende bestanden toe aan de clientbibliotheek:

* **i18n.js** die `guidelib.i18n`, met patronen van &quot;kalenderSymbols&quot;, `datePatterns`, `timePatterns`, `dateTimeSymbols`, `numberPatterns`, `numberSymbols`, `currencySymbols`, `typefaces` `<locale>` [](https://helpx.adobe.com/content/dam/Adobe/specs/xfa_spec_3_3.pdf)voor de specificaties van XFA die in de SpecificationLocale worden beschreven wordt beschreven definiëren. U kunt ook zien hoe deze wordt gedefinieerd voor andere ondersteunde landinstellingen in `/etc/clientlibs/fd/af/I18N/fr/javascript/i18n.js`.
* **LogMessages.js** die `guidelib.i18n.strings` en `guidelib.i18n.LogMessages` voor `<locale>` zoals die in `/etc/clientlibs/fd/af/I18N/fr/javascript/LogMessages.js`wordt bepaald.
* **js.txt** met het volgende:

```text
i18n.js
LogMessages.js
```

### Ondersteuning voor landinstellingen toevoegen voor het woordenboek {#add-locale-support-for-the-dictionary-br}

Voer deze stap alleen uit als de stap die `<locale>` u toevoegt, niet behoort tot `en`, `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja``ko-kr`.

1. Maak een `nt:unstructured` knooppunt `languages` onder `etc`, indien niet aanwezig.

1. Voeg een multi-getaxeerde koordbezit `languages` aan de knoop toe, als niet reeds aanwezig.
1. Voeg de `<locale>` standaardwaarden voor de landinstelling toe `de`, `es`, `fr`, `it`, `pt-br`, `zh-cn`, `zh-tw`, `ja`, `ko-kr`als deze nog niet aanwezig zijn.

1. Voeg de waarden toe `<locale>` aan de waarden van de `languages` eigenschap van `/etc/languages`.

De `<locale>` tekst verschijnt om `https://'[server]:[port]'/libs/cq/i18n/translator.html`.

### De server opnieuw starten {#restart-the-server}

Start de AEM server opnieuw om de toegevoegde landinstelling te activeren.

## Voorbeeldbibliotheken voor het toevoegen van ondersteuning voor Spaans {#sample-libraries-for-adding-support-for-spanish}

Voorbeeld van clientbibliotheken voor het toevoegen van ondersteuning voor Spaans

[Bestand ophalen](assets/sample.zip)
