---
title: Cookie-gebruik configureren
description: AEM biedt een service waarmee u kunt configureren en bepalen hoe cookies worden gebruikt met uw webpagina's.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: 42e8d804-6b6a-432e-a651-940b9f45db4e
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '549'
ht-degree: 0%

---

# Cookie-gebruik configureren{#configuring-cookie-usage}

AEM verstrekt de dienst die u toelaat om te vormen en te controleren hoe de koekjes met uw Web-pagina&#39;s worden gebruikt:

* Een configureerbare server-zijdienst handhaaft een lijst van koekjes die kunnen worden gebruikt.
* Met een JavaScript-API kan uw JavaScript-code controleren of een cookie kan worden gebruikt.

Gebruik deze functie om ervoor te zorgen dat uw pagina&#39;s voldoen aan de toestemming van uw gebruikers met betrekking tot het gebruik van cookies.

## Toegestane cookies configureren {#configuring-allowed-cookies}

Configureer de Adobe Granite Opt-Out Service om op te geven hoe cookies op uw webpagina&#39;s worden gebruikt. In de volgende tabel worden de eigenschappen beschreven die u kunt configureren.

Om de dienst te vormen, kunt u gebruiken [Webconsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) of [Voeg een configuratie OSGi aan de bewaarplaats toe](/help/sites-deploying/configuring-osgi.md#adding-a-new-configuration-to-the-repository). In de volgende tabel worden de eigenschappen beschreven die u voor een van beide methoden nodig hebt. Voor een configuratie OSGi, de dienst PID is `com.adobe.granite.optout`.

| Naam eigenschap (webconsole) | OSGi Eigenschapnaam | Beschrijving |
|---|---|---|
| Cookies uitschakelen | optout.cookies | De namen van cookies die, indien aanwezig op het apparaat van de gebruiker, aangeven dat de gebruiker niet heeft ingestemd met het gebruik van cookies. |
| HTTP-headers uitschakelen | optout.headers | De namen van HTTP-headers die, indien aanwezig, aangeven dat de gebruiker niet heeft ingestemd met het gebruik van cookies. |
| Witte-lijstcookies | optout.whitelist.cookies | Een lijst met cookies die essentieel zijn voor het functioneren van de website en die zonder toestemming van de gebruiker kunnen worden gebruikt. |

## Cookiegebruik valideren {#validating-cookie-usage}

Gebruik client-side JavaScript om de Adobe Granite Opt-Out Service aan te roepen om te controleren of u een cookie kunt gebruiken. Met het JavaScript-object Granite.OptOutUtil kunt u een van de volgende taken uitvoeren:

* Vraag een lijst met cookienamen aan die aangeven dat de gebruiker geen toestemming geeft cookies te gebruiken voor traceringsdoeleinden.
* Verkrijg een lijst van koekjes die kunnen worden gebruikt.
* Bepaal of de webbrowser een cookie bevat die aangeeft dat de gebruiker geen toestemming geeft voor het gebruik van cookies voor tracering.
* Bepaal of een specifieke cookie kan worden gebruikt.

granite.utils [clientbibliotheekmap](/help/sites-developing/clientlibs.md#referencing-client-side-libraries) biedt het Granite.OptOutUtil-object. Voeg de volgende code toe aan de paginakop JSP om een koppeling naar de JavaScript-bibliotheek op te nemen:

`<ui:includeClientLib categories="granite.utils" />`

De volgende JavaScript-functie bepaalt bijvoorbeeld of het cookie COOKIE_NAME is toegestaan voor gebruik voordat ernaar wordt geschreven:

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

De namen van de cookies die, indien aanwezig, aangeven dat de gebruiker geen toestemming heeft gegeven voor het gebruik van cookies.

**Parameters**

Geen.

**Retourneert**

Een array van cookie namen.

#### getWhitelistCookieNames() functie {#getwhitelistcookienames-function}

De namen van cookies die kunnen worden gebruikt, ongeacht de toestemming van de gebruiker.

**Parameters**

Geen.

**Retourneert**

Een array van cookie namen.

#### isOptedOut() functie {#isoptedout-function}

Hiermee wordt bepaald of de browser van de gebruiker cookies bevat die aangeven dat geen toestemming is gegeven om cookies te gebruiken.

**Parameters**

Geen.

**Retourneert**

Een booleaanse waarde van `true` als een cookie wordt gevonden die aangeeft dat er geen toestemming is, en als de waarde `false` als er geen cookies zijn die aangeven dat er geen toestemming is gegeven.

### maySetCookie(cookieName), functie {#maysetcookie-cookiename-function}

Hiermee wordt bepaald of een specifieke cookie in de browser van de gebruiker kan worden gebruikt. Deze functie is gelijk aan het gebruik van de `isOptedOut` om te bepalen of het opgegeven cookie is opgenomen in de lijst die `getWhitelistCookieNames` functie retourneert.

**Parameters**

* cookieName: String. De naam van het cookie.

**Retourneert**

Een booleaanse waarde van `true` indien `cookieName` kan worden gebruikt, of een waarde van `false` indien `cookieName` kan niet worden gebruikt.
