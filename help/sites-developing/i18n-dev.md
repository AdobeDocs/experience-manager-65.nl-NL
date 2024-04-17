---
title: Internationalisatie van UI-tekenreeksen
description: Java&trade; en JavaScript APIs laten u toe om koorden te internationaliseren
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components
exl-id: bc5b1cb7-a011-42fe-8759-3c7ee3068aad
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1091'
ht-degree: 0%

---

# Internationalisatie van UI-tekenreeksen {#internationalizing-ui-strings}

Met Java™- en JavaScript API&#39;s kunt u tekenreeksen internationaliseren in de volgende typen bronnen:

* Java™-bronbestanden.
* JSP-scripts.
* JavaScript in client-side bibliotheken of in paginabron.
* Waarden van eigenschappen van JCR-knooppunten worden gebruikt in dialoogvensters en componentconfiguratie-eigenschappen.

Voor een overzicht van het internationalisatie- en lokalisatieproces gaat u naar [Internationaliserende componenten](/help/sites-developing/i18n.md).

## Internationalisatie van tekenreeksen in Java™- en JSP-code {#internationalizing-strings-in-java-and-jsp-code}

De `com.day.cq.i18n` Met het Java™-pakket kunt u gelokaliseerde tekenreeksen weergeven in uw gebruikersinterface. De `I18n` klasse biedt de `get` methode die gelokaliseerde tekenreeksen ophaalt uit het Adobe Experience Manager-woordenboek (AEM). De enige vereiste parameter van de `get` method is the string literal in the English language. Engels is de standaardtaal voor UI. In het volgende voorbeeld wordt het woord gelokaliseerd `Search`:

`i18n.get("Search");`

Het identificeren van de tekenreeks in de Engelse taal verschilt van gangbare internationalisatiekaders waar een id een tekenreeks identificeert en wordt gebruikt om bij uitvoering naar de tekenreeks te verwijzen. Het gebruik van de letterlijke Engelse tekenreeks biedt de volgende voordelen:

* Code is gemakkelijk te begrijpen.
* De tekenreeks in de standaardtaal is altijd beschikbaar.

### De taal van de gebruiker bepalen {#determining-the-user-s-language}

Er zijn twee manieren om de taal te bepalen die de gebruiker verkiest:

* Voor geverifieerde gebruikers bepaalt u de taal aan de hand van de voorkeuren in de gebruikersaccount.
* De landinstelling van de aangevraagde pagina.

Het taalbezit van de gebruikersrekening is de aangewezen methode omdat het betrouwbaarder is. Nochtans, moet de gebruiker worden het programma geopend om deze methode te gebruiken.

#### Het I18n Java™-object maken {#creating-the-i-n-java-object}

De klasse I18n biedt twee constructors. Hoe u de aangewezen taal van de gebruiker bepaalt de te gebruiken aannemer.

Gebruik de volgende constructor (na het importeren) om de tekenreeks weer te geven in de taal die is opgegeven in de gebruikersaccount `com.day.cq.i18n.I18n)`:

```java
I18n i18n = new I18n(slingRequest);
```

De constructor gebruikt de `SlingHTTPRequest` om de taalinstelling van de gebruiker op te halen.

Om de paginalandaal te gebruiken om de taal te bepalen, verkrijg eerst ResourceBundle voor de taal van de gevraagde pagina:

```java
Locale pageLang = currentPage.getLanguage(false);
ResourceBundle resourceBundle = slingRequest.getResourceBundle(pageLang);
I18n i18n = new I18n(resourceBundle);
```

#### Een tekenreeks internationaliseren {#internationalizing-a-string}

Gebruik de `get` van de `I18n` object gebruiken om een tekenreeks te internationaliseren. De enige vereiste parameter van de `get` methode is de tekenreeks die geïnternationaliseerd moet worden. De tekenreeks komt overeen met een tekenreeks in een Vertaalwoordenboek. De methode get zoekt de tekenreeks op in het woordenboek en retourneert de vertaling voor de huidige taal.

Het eerste argument van het `get` de methode moet aan de volgende regels voldoen:

* De waarde moet een letterlijke tekenreeks zijn. Een variabele van het type `String` is niet aanvaardbaar.
* De letterlijke tekenreeks moet op één regel worden uitgedrukt.
* De tekenreeks is hoofdlettergevoelig.

```xml
i18n.get("Enter a search keyword");
```

#### Vertaalhints gebruiken {#using-translation-hints}

Geef de [vertaalhint](/help/sites-developing/i18n-translator.md#adding-changing-and-removing-strings) van de geïnternationaliseerde tekenreeks om onderscheid te maken tussen dubbele tekenreeksen in het woordenboek. Gebruik de tweede, optionele parameter van de `get` methode om de vertaalhint op te geven. De vertaalhint moet exact overeenkomen met de eigenschap Opmerking van het item in het woordenboek.

Het woordenboek bevat bijvoorbeeld de tekenreeks `Request` tweemaal: eenmaal als werkwoord en eenmaal als zelfstandig naamwoord. De volgende code bevat de vertaalhint als een argument in het dialoogvenster `get` methode:

```java
i18n.get("Request","A noun, as in a request for a web page");
```

#### Inclusief variabelen in gelokaliseerde zinnen {#including-variables-in-localized-sentences}

Neem variabelen op in de gelokaliseerde tekenreeks om contextuele betekenis in een zin op te nemen. Nadat u zich bijvoorbeeld hebt aangemeld bij een webtoepassing, wordt op de homepage het bericht &quot;Welkom terug Administrator&quot; weergegeven. Je hebt twee berichten in je postvak.&quot; De paginacontext bepaalt de gebruikersnaam en het aantal berichten.

[In het woordenboek](/help/sites-developing/i18n-translator.md#adding-changing-and-removing-strings), worden de variabelen vertegenwoordigd in koorden als gehaakte indexen. Geef de waarden van de variabelen op als argumenten van de `get` methode. De argumenten worden na de vertaalhint geplaatst, en de indexen beantwoorden aan de orde van de argumenten:

```xml
i18n.get("Welcome back {0}. You have {1} messages.", "user name, number of messages", user.getDisplayName(), numItems);
```

De geïnternationaliseerde tekenreeks en de vertaalhint moeten exact overeenkomen met de tekenreeks en de opmerking in het woordenboek. U kunt de lokalisatiehint weglaten door een `null` waarde als het tweede argument.

#### Het gebruiken van Statische krijgt methode {#using-the-static-get-method}

De `I18N` klasse definieert een statische klasse `get` Deze methode is handig wanneer u een aantal tekenreeksen moet lokaliseren. Naast de parameters van de `get` de statische methode vereist `SlingHttpRequest` of het `ResourceBundle` die u gebruikt, op basis van hoe u de voorkeurstaal van de gebruiker bepaalt:

* Gebruik de taalvoorkeur van de gebruiker: Geef SlingHttpRequest als eerste parameter op.

  `I18n.get(slingHttpRequest, "Welcome back {}. You have {} messages.", "user name, number of messages", user.getDisplayName(), numItems);`
* Gebruik de paginataal: geef de ResourceBundle op als eerste parameter.

  `I18n.get(resourceBundle,"Welcome back {}. You have {} messages.", "user name, number of messages", user.getDisplayName(), numItems);`

### Tekenreeksen internationaliseren in JavaScript-code {#internationalizing-strings-in-javascript-code}

Met de JavaScript-API kunt u tekenreeksen lokaliseren op de client. Zoals met [Java™ en JSP](#internationalizing-strings-in-java-and-jsp-code) Met de JavaScript-API kunt u tekenreeksen identificeren die u wilt lokaliseren, lokalisatietips opgeven en variabelen opnemen in de gelokaliseerde tekenreeksen.

De `granite.utils` [clientbibliotheekmap](/help/sites-developing/clientlibs.md) bevat de JavaScript-API. Neem deze clientbibliotheekmap op de pagina op om de API te gebruiken. De lokalisatiefuncties gebruiken de `Granite.I18n` naamruimte.

Voordat u gelokaliseerde tekenreeksen weergeeft, stelt u de landinstelling in met de `Granite.I18n.setLocale` functie. De functie vereist de taalcode van de landinstelling als argument:

```
Granite.I18n.setLocale("fr");
```

Als u een gelokaliseerde tekenreeks wilt presenteren, gebruikt u de `Granite.I18n.get` functie:

```
Granite.I18n.get("string to localize");
```

In het volgende voorbeeld wordt de tekenreeks &quot;Welcome back&quot; geïnternationaliseerd:

```
Granite.I18n.setLocale("fr");
Granite.I18n.get("string to localize", [variables], "localization hint");
```

De functieparameters verschillen van de Java™ I18n.get-methode:

* De eerste parameter is de letterlijke tekenreeks die moet worden gelokaliseerd.
* De tweede parameter is een array van waarden die in de letterlijke tekenreeks moeten worden geïnjecteerd.
* De derde parameter is de lokalisatiehint.

In het volgende voorbeeld wordt JavaScript gebruikt om de &quot;Welkom back Administrator&quot; te lokaliseren. Je hebt twee berichten in je postvak.&quot; zin:

```
Granite.I18n.setLocale("fr");
Granite.I18n.get("Welcome back {0}. You have {1} new messages in your inbox.", [username, numMsg], "user name, number of messages");
```

### Internationalisatie tekenreeksen van JCR-knooppunten {#internationalizing-strings-from-jcr-nodes}

UI-tekenreeksen zijn vaak gebaseerd op eigenschappen van JCR-knooppunten. Bijvoorbeeld de `jcr:title` eigenschap van een pagina wordt doorgaans gebruikt als de inhoud van de `h1` in de paginacode. De `I18n` klasse biedt de `getVar` methode voor het lokaliseren van deze tekenreeksen.

Het volgende JSP-voorbeeldscript haalt het `jcr:title` eigenschap van de opslagplaats en geeft de gelokaliseerde tekenreeks op de pagina weer:

```java
<% title = properties.get("jcr:title", String.class);%>
<h1><%=i18n.getVar(title) %></h1>
```

#### Vertaaltips opgeven voor JCR-knooppunten {#specifying-translation-hints-for-jcr-nodes}

Vergelijkbaar met [vertaalhints in de Java™ API](#using-translation-hints)kunt u vertaaltips opgeven om dubbele tekenreeksen in het woordenboek te onderscheiden. Geef de vertaalhint op als een eigenschap van het knooppunt dat de geïnternationaliseerde eigenschap bevat. De naam van de eigenschap hint bestaat uit de naam van de geïnternationaliseerde eigenschapnaam met de naam `_commentI18n` achtervoegsel:

`${prop}_commentI18n`

Bijvoorbeeld een `cq:page` de node bevat de eigenschap jcr:title die wordt gelokaliseerd. De hint wordt opgegeven als de waarde van de eigenschap met de naam jcr:title_commentI18n.

### Bedekking voor internationalisatie testen {#testing-internationalization-coverage}

Test of u alle tekenreeksen in uw gebruikersinterface hebt geïnternationaliseerd. Als u wilt zien welke tekenreeksen worden bestreken, stelt u de gebruikerstaal in op zz_ZZ en opent u de gebruikersinterface in de webbrowser. De geïnternationaliseerde tekenreeksen worden weergegeven met een stub-vertaling in de volgende indeling:

`USR_*Default-String*_尠`

In de volgende afbeelding ziet u de stub-vertaling voor de AEM homepage:

![chlimage_1](assets/chlimage_1a.jpeg)

Om de taal voor de gebruiker te plaatsen, vorm het taalbezit van de voorkeurenknoop voor de gebruikersrekening.

Het voorkeurenknooppunt van een gebruiker heeft een pad als volgt:

`/home/users/<letter>/<hash>/preferences`

![chlimage_1-1](assets/chlimage_1-1a.jpeg)
