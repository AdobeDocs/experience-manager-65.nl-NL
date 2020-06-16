---
title: Cookie-gebruik configureren
seo-title: Cookie-gebruik configureren
description: AEM biedt een service waarmee u kunt configureren en bepalen hoe cookies worden gebruikt met uw webpagina's
seo-description: AEM biedt een service waarmee u kunt configureren en bepalen hoe cookies worden gebruikt met uw webpagina's
uuid: 10d95176-0a56-41f1-9d36-01dbdac757d4
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 5773ec1a-f15b-462d-8f9f-54ee1d7ead44
translation-type: tm+mt
source-git-commit: f64eb57a69f2124523bd6eaed3e2f58a54c1ea8e
workflow-type: tm+mt
source-wordcount: '576'
ht-degree: 2%

---


# Cookie-gebruik configureren{#configuring-cookie-usage}

AEM verleent de dienst die u toelaat om te vormen en te controleren hoe de koekjes met uw Web-pagina&#39;s worden gebruikt:

* Een configureerbare server-zijdienst handhaaft een lijst van koekjes die kunnen worden gebruikt.
* Met een javascript-API kan uw JavaScript-code controleren of een cookie kan worden gebruikt.

Gebruik deze functie om ervoor te zorgen dat uw pagina&#39;s voldoen aan de toestemming van uw gebruikers met betrekking tot het gebruik van cookies.

## Toegestane cookies configureren {#configuring-allowed-cookies}

Configureer de Adobe Granite Opt-Out Service om op te geven hoe cookies op uw webpagina&#39;s worden gebruikt. In de volgende tabel worden de eigenschappen beschreven die u kunt configureren.

Om de dienst te vormen, kunt u de Console [van het](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) Web gebruiken of een configuratie [toevoegen OSGi aan de bewaarplaats](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository). In de volgende tabel worden de eigenschappen beschreven die u voor een van beide methoden nodig hebt. Voor een configuratie OSGi, is de dienst PID `com.adobe.granite.optout`.

| Naam eigenschap (webconsole) | OSGi Eigenschapnaam | Beschrijving |
|---|---|---|
| Cookies uitschakelen | optout.cookies | De namen van cookies die aangeven dat de gebruiker, indien aanwezig op het apparaat van de gebruiker, niet heeft ingestemd met het gebruik van cookies. |
| HTTP-headers uitschakelen | optout.headers | De namen van HTTP-headers die, indien aanwezig, aangeven dat de gebruiker niet heeft ingestemd met het gebruik van cookies. |
| Witte-lijstcookies | optout.whitelist.cookies | Een lijst met cookies die essentieel zijn voor het functioneren van de website en die zonder toestemming van de gebruiker kunnen worden gebruikt. |

## Cookiegebruik valideren {#validating-cookie-usage}

Gebruik JavaScript op de client om Adobe Granite Opt-Out Service aan te roepen om te controleren of u een cookie kunt gebruiken. Gebruik het JavaScript-object Granite.OptOutUtil om een van de volgende taken uit te voeren:

* Vraag een lijst met cookienamen aan die aangeven dat de gebruiker geen toestemming geeft cookies te gebruiken voor traceringsdoeleinden.
* Verkrijg een lijst van koekjes die kunnen worden gebruikt.
* Bepaal of de webbrowser een cookie bevat die aangeeft dat de gebruiker geen toestemming geeft voor het gebruik van cookies voor tracering.
* Bepaal of een specifieke cookie kan worden gebruikt.

De [clientbibliotheekmap](/help/sites-developing/clientlibs.md#referencing-client-side-libraries) granite.utils biedt het object Granite.OptOutUtil. Voeg de volgende code aan uw paginakop JSP toe om een verbinding aan de bibliotheek te omvatten javascript:

`<ui:includeClientLib categories="granite.utils" />`

De volgende javascript-functie bepaalt bijvoorbeeld of het cookie COOKIE_NAME mag worden gebruikt voordat ernaar wordt geschreven:

```
function writeCookie(value){
   if (!Granite.OptOutUtil.maySetCookie("COOKIE_NAME"))
      return;
   if (value) {
      value = encodeURIComponent(value);
      document.cookie = "COOKIE_NAME=" + value;
   }
}
```

## Het JavaScript-object Granite.OptOutUtil {#the-granite-optoututil-javascript-object}

Granite.OptOutUtil laat u toe om te bepalen of het koekjesgebruik wordt toegestaan.

### getCookieNames() functie {#getcookienames-function}

Geeft de namen van de cookies weer die, indien aanwezig, aangeven dat de gebruiker geen toestemming heeft gegeven voor het gebruik van cookies.

**Parameters**

Geen.

**Geeft als resultaat**

Een array van cookie namen.

#### getWhitelistCookieNames() functie {#getwhitelistcookienames-function}

Retourneert de namen van cookies die kunnen worden gebruikt, ongeacht de toestemming van de gebruiker.

**Parameters**

Geen.

**Geeft als resultaat**

Een array van cookie namen.

#### isOptedOut() functie {#isoptedout-function}

Hiermee wordt bepaald of de browser van de gebruiker cookies bevat die aangeven dat geen toestemming is gegeven om cookies te gebruiken.

**Parameters**

Geen.

**Geeft als resultaat**

Een booleaanse waarde van `true` als een cookie wordt gevonden die geen toestemming aangeeft en een waarde van `false` als er geen cookies zijn die aangeven dat er geen toestemming is.

### maySetCookie(cookieName), functie {#maysetcookie-cookiename-function}

Hiermee wordt bepaald of een specifieke cookie in de browser van de gebruiker kan worden gebruikt. Deze functie is gelijk aan het gebruik van de `isOptedOut` functie in combinatie met het bepalen of het gegeven cookie is opgenomen in de lijst die de `getWhitelistCookieNames` functie retourneert.

**Parameters**

* cookieName: Tekenreeks. De naam van het cookie.

**Geeft als resultaat**

Een booleaanse waarde van `true` if `cookieName` kan worden gebruikt, of een waarde van `false` als `cookieName` niet kan worden gebruikt.
