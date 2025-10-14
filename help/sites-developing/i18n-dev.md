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
* JavaScript in clientbibliotheken of in paginabron.
* Waarden van eigenschappen van JCR-knooppunten worden gebruikt in dialoogvensters en componentconfiguratie-eigenschappen.

Voor een overzicht van het internationalisatie en localisatieproces, zie [&#x200B; Internationaliserende Componenten &#x200B;](/help/sites-developing/i18n.md).

## Internationalisatie van tekenreeksen in Java™- en JSP-code {#internationalizing-strings-in-java-and-jsp-code}

Met het Java™-pakket van `com.day.cq.i18n` kunt u gelokaliseerde tekenreeksen weergeven in uw gebruikersinterface. De klasse `I18n` biedt de methode `get` die gelokaliseerde tekenreeksen ophaalt uit het Adobe Experience Manager-woordenboek (AEM). De enige vereiste parameter van de methode `get` is de letterlijke tekenreeks in de Engelse taal. Engels is de standaardtaal voor UI. In het volgende voorbeeld wordt het woord `Search` gelokaliseerd:

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

Wanneer u de tekenreeks wilt presenteren in de taal die in de gebruikersaccount is opgegeven, gebruikt u de volgende constructor (na het importeren `com.day.cq.i18n.I18n)` :

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

Gebruik de methode `get` van het `I18n` -object om een tekenreeks te internationaliseren. De enige vereiste parameter van de methode `get` is de tekenreeks die moet worden geïnternationaliseerd. De tekenreeks komt overeen met een tekenreeks in een Vertaalwoordenboek. De methode get zoekt de tekenreeks op in het woordenboek en retourneert de vertaling voor de huidige taal.

Het eerste argument van de methode `get` moet aan de volgende regels voldoen:

* De waarde moet een letterlijke tekenreeks zijn. Een variabele van het type `String` is niet acceptabel.
* De letterlijke tekenreeks moet op één regel worden uitgedrukt.
* De tekenreeks is hoofdlettergevoelig.

```xml
i18n.get("Enter a search keyword");
```

#### Vertaalhints gebruiken {#using-translation-hints}

Specificeer de [&#x200B; vertaalwenk &#x200B;](/help/sites-developing/i18n-translator.md#adding-changing-and-removing-strings) van het geïnternationaliseerde koord om tussen dubbele koorden in het woordenboek te onderscheiden. Gebruik de tweede, optionele parameter van de methode `get` om de vertaalhint op te geven. De vertaalhint moet exact overeenkomen met de eigenschap Opmerking van het item in het woordenboek.

Het woordenboek bevat bijvoorbeeld de tekenreeks `Request` tweemaal: een keer als werkwoord en een keer als zelfstandig naamwoord. De volgende code bevat de vertaaltip als een argument in de methode `get` :

```java
i18n.get("Request","A noun, as in a request for a web page");
```

#### Inclusief variabelen in gelokaliseerde zinnen {#including-variables-in-localized-sentences}

Neem variabelen op in de gelokaliseerde tekenreeks om contextuele betekenis in een zin op te nemen. Nadat u zich bijvoorbeeld hebt aangemeld bij een webtoepassing, wordt op de homepage het bericht &quot;Welkom terug Administrator&quot; weergegeven. Je hebt twee berichten in je postvak.&quot; De paginacontext bepaalt de gebruikersnaam en het aantal berichten.

[&#x200B; in het woordenboek &#x200B;](/help/sites-developing/i18n-translator.md#adding-changing-and-removing-strings), worden de variabelen vertegenwoordigd in koorden als gehaakte indexen. Geef de waarden van de variabelen op als argumenten van de methode `get` . De argumenten worden na de vertaalhint geplaatst, en de indexen beantwoorden aan de orde van de argumenten:

```xml
i18n.get("Welcome back {0}. You have {1} messages.", "user name, number of messages", user.getDisplayName(), numItems);
```

De geïnternationaliseerde tekenreeks en de vertaalhint moeten exact overeenkomen met de tekenreeks en de opmerking in het woordenboek. U kunt de lokalisatiehint weglaten door als tweede argument een `null` -waarde op te geven.

#### Het gebruiken van Statische krijgt methode {#using-the-static-get-method}

De klasse `I18N` definieert een statische methode `get` die nuttig is wanneer u een aantal tekenreeksen moet lokaliseren. Naast de parameters van de methode `get` van een object, vereist de statische methode het `SlingHttpRequest` -object of de `ResourceBundle` die u gebruikt, op basis van de manier waarop u de voorkeurstaal van de gebruiker bepaalt:

* Gebruik de taalvoorkeur van de gebruiker: Geef SlingHttpRequest als eerste parameter op.

  `I18n.get(slingHttpRequest, "Welcome back {}. You have {} messages.", "user name, number of messages", user.getDisplayName(), numItems);`
* Gebruik de paginataal: geef de ResourceBundle op als eerste parameter.

  `I18n.get(resourceBundle,"Welcome back {}. You have {} messages.", "user name, number of messages", user.getDisplayName(), numItems);`

### Internationalisatie tekenreeksen in JavaScript-code {#internationalizing-strings-in-javascript-code}

Met de JavaScript API kunt u tekenreeksen lokaliseren op de client. Zoals met [&#x200B; Java™ en JSP &#x200B;](#internationalizing-strings-in-java-and-jsp-code) code, laat JavaScript API u toe om koorden te identificeren te lokaliseren, lokalisatiewenken te verstrekken, en variabelen in de gelokaliseerde koorden te omvatten.

De `granite.utils` [&#x200B; omslag van de cliëntbibliotheek &#x200B;](/help/sites-developing/clientlibs.md) verstrekt JavaScript API. Neem deze clientbibliotheekmap op de pagina op om de API te gebruiken. Localisatiefuncties gebruiken de naamruimte `Granite.I18n` .

Voordat u gelokaliseerde tekenreeksen weergeeft, stelt u de landinstelling in met behulp van de functie `Granite.I18n.setLocale` . De functie vereist de taalcode van de landinstelling als argument:

```
Granite.I18n.setLocale("fr");
```

Als u een gelokaliseerde tekenreeks wilt presenteren, gebruikt u de functie `Granite.I18n.get` :

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

In het volgende voorbeeld wordt JavaScript gebruikt om de welkomstbeheerder te lokaliseren. Je hebt twee berichten in je postvak.&quot; zin:

```
Granite.I18n.setLocale("fr");
Granite.I18n.get("Welcome back {0}. You have {1} new messages in your inbox.", [username, numMsg], "user name, number of messages");
```

### Internationalisatie tekenreeksen van JCR-knooppunten {#internationalizing-strings-from-jcr-nodes}

UI-tekenreeksen zijn vaak gebaseerd op eigenschappen van JCR-knooppunten. De eigenschap `jcr:title` van een pagina wordt bijvoorbeeld doorgaans gebruikt als de inhoud van het element `h1` in de paginacode. De klasse `I18n` biedt de methode `getVar` voor het lokaliseren van deze tekenreeksen.

In het volgende voorbeeld haalt het JSP-script de eigenschap `jcr:title` op uit de gegevensopslagruimte en wordt de gelokaliseerde tekenreeks op de pagina weergegeven:

```java
<% title = properties.get("jcr:title", String.class);%>
<h1><%=i18n.getVar(title) %></h1>
```

#### Vertaaltips opgeven voor JCR-knooppunten {#specifying-translation-hints-for-jcr-nodes}

Gelijkaardig aan [&#x200B; vertaalwenken in Java™ API &#x200B;](#using-translation-hints), kunt u vertaalwenken verstrekken om dubbele koorden in het woordenboek te onderscheiden. Geef de vertaalhint op als een eigenschap van het knooppunt dat de geïnternationaliseerde eigenschap bevat. De naam van de eigenschap hint bestaat uit de naam van de geïnternationaliseerde eigenschapnaam met het achtervoegsel `_commentI18n` :

`${prop}_commentI18n`

Een knooppunt `cq:page` bevat bijvoorbeeld de eigenschap jcr:title die wordt gelokaliseerd. De hint wordt opgegeven als de waarde van de eigenschap met de naam jcr:title_commentI18n.

### Bedekking voor internationalisatie testen {#testing-internationalization-coverage}

Test of u alle tekenreeksen in uw gebruikersinterface hebt geïnternationaliseerd. Als u wilt zien welke tekenreeksen worden bestreken, stelt u de gebruikerstaal in op zz_ZZ en opent u de gebruikersinterface in de webbrowser. De geïnternationaliseerde tekenreeksen worden weergegeven met een stub-vertaling in de volgende indeling:

`USR_*Default-String*_尠`

In de volgende afbeelding ziet u de stub-vertaling voor de AEM homepage:

![&#x200B; chlimage_1 &#x200B;](assets/chlimage_1a.jpeg)

Om de taal voor de gebruiker te plaatsen, vorm het taalbezit van de voorkeurenknoop voor de gebruikersrekening.

Het voorkeurenknooppunt van een gebruiker heeft een pad als volgt:

`/home/users/<letter>/<hash>/preferences`

![&#x200B; chlimage_1-1 &#x200B;](assets/chlimage_1-1a.jpeg)
