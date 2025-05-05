---
title: Single Sign On
description: Leer hoe u SSO (Single Sign On) voor een instantie van Adobe Experience Manager (AEM) configureert.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring, Security
content-type: reference
feature: Security
exl-id: 7d2e4620-c3a5-4f5a-9eb6-42a706479d41
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '723'
ht-degree: 0%

---

# Single Sign On {#single-sign-on}

Met Single Sign On (SSO) heeft een gebruiker toegang tot meerdere systemen nadat hij de verificatiegegevens (zoals een gebruikersnaam en wachtwoord) eenmaal heeft opgegeven. Een afzonderlijk systeem (dat als vertrouwde op authentiek wordt bekend) voert de authentificatie uit en verstrekt Experience Manager de gebruikersgeloofsbrieven. De Experience Manager controleert en dwingt de toegangstoestemmingen voor de gebruiker (namelijk bepaalt welke middelen de gebruiker wordt toegestaan om toegang te hebben) af.

De service SSO Authentication Handler ( `com.adobe.granite.auth.sso.impl.SsoAuthenticationHandler` ) verwerkt de verificatieresultaten die door de vertrouwde authenticator worden verschaft. De manager van de Authentificatie SSO zoekt naar een Herkenningsteken SSO (SSID) als waarde van een speciaal attribuut in de volgende plaatsen in deze orde:

1. Aanvraagkoppen
1. Cookies
1. Parameters aanvragen

Wanneer een waarde wordt gevonden, is het onderzoek gebeëindigd en deze waarde wordt gebruikt.

Vorm de volgende twee diensten om de naam van de attributen te erkennen die SSID opslaat:

* De aanmeldingsmodule.
* De service SSO-verificatie.

Geef dezelfde kenmerknaam op voor beide services. Het kenmerk wordt opgenomen in de `SimpleCredentials` die aan `Repository.login` wordt geleverd. De waarde van het kenmerk is irrelevant en wordt genegeerd, de aanwezigheid ervan is alleen belangrijk en geverifieerd.

## SSO configureren {#configuring-sso}

Om SSO voor een AEM instantie te vormen, vormt u de [ manager van de Authentificatie SSO ](/help/sites-deploying/osgi-configuration-settings.md#adobegranitessoauthenticationhandler):

1. Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [ Vormend OSGi ](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

   Bijvoorbeeld voor NTLM-set:

   * **Weg:** zoals vereist; bijvoorbeeld, `/`
   * **de Namen van de Kopbal**: `LOGON_USER`
   * **Formaat van identiteitskaart**: `^<DOMAIN>\\(.+)$`

     Waar `<*DOMAIN*>` wordt vervangen door de naam van uw eigen domein.

   Voor CoSign:

   * **Weg:** zoals vereist; bijvoorbeeld, `/`
   * **Namen van de Kopbal**: remote_user
   * **Formaat van identiteitskaart:** AsIs

   Voor SiteMinder:

   * **Weg:** zoals vereist; bijvoorbeeld, `/`
   * **de Namen van de Kopbal:** SM_USER
   * **Formaat van identiteitskaart**: AsIs

1. Bevestig dat Single Sign On naar wens werkt, inclusief autorisatie.

>[!CAUTION]
>
>Zorg ervoor dat de gebruikers tot AEM niet direct kunnen toegang hebben als SSO wordt gevormd.
>
>Door gebruikers te vereisen om door een Webserver te gaan die de agent van uw SSO systeem in werking stelt, wordt het gewaarborgd dat geen gebruiker een kopbal, een koekje, of een parameter kan direct verzenden die de gebruiker zal leiden om door AEM worden vertrouwd, aangezien de agent dergelijke informatie zal filtreren indien verzonden van de buitenkant.
>
>Om het even welke gebruiker die tot uw AEM instantie direct kan toegang hebben zonder door de Webserver te gaan zal als om het even welke gebruiker kunnen handelen door kopbal, koekje, of parameter te verzenden als de namen gekend zijn.
>
>Zorg ook dat van kopballen, koekjes, en de namen van de verzoekparameter, u slechts vormt die voor uw opstelling SSO wordt vereist.
>

>[!NOTE]
>
>Enig Sign wordt vaak gebruikt met [ LDAP ](/help/sites-administering/ldap-config.md).

>[!NOTE]
>
>Als u ook [ Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=nl-NL) met de Server van de Informatie van Microsoft® Internet (IIS) gebruikt, dan wordt de extra configuratie vereist binnen:
>
>* `disp_iis.ini`
>* IIS
>
>In `disp_iis.ini` set:
>(zie [ installerend Dispatcher met de Server van de Informatie van Microsoft® Internet ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/getting-started/dispatcher-install.html?lang=nl-NL#microsoft-internet-information-server) voor volledige details)
>
>* `servervariables=1` (stuurt IIS-servervariabelen als aanvraagheaders door naar de externe instantie)
>* `replaceauthorization=1` (vervangt een header met de naam &quot;Authorization&quot; (behalve &quot;Basic&quot;) door de waarde &quot;Basic&quot; (equivalent))
>
>In IIS:
>
>* maak **Anonieme toegang** onbruikbaar
>
>* laat **Geïntegreerde authentificatie van Vensters** toe
>

U kunt zien welke authentificatiemanager op om het even welke sectie van de inhoudsboom wordt toegepast door de **Authenticator** optie van de Console van de Felix te gebruiken; bijvoorbeeld:

`http://localhost:4502/system/console/slingauth`

De handler die het beste overeenkomt met het pad wordt als eerste gevraagd. Als u bijvoorbeeld handler-A configureert voor het pad `/` en handler-B voor het pad `/content` , zal een aanvraag naar `/content/mypage.html` eerst handler-B opvragen.

![ screen_shot_2012-02-15at21006pm ](assets/screen_shot_2012-02-15at21006pm.png)

### Voorbeeld {#example}

Voor een cookieaanvraag (met de URL `http://localhost:4502/libs/wcm/content/siteadmin.html`):

```xml
GET /libs/cq/core/content/welcome.html HTTP/1.1
Host: localhost:4502
Cookie: TestCookie=admin
```

De volgende configuratie gebruiken:

* **Weg**: `/`

* **de Namen van de Kopbal**: `TestHeader`

* **Namen van het Koekje**: `TestCookie`

* **Namen van de Parameter**: `TestParameter`

* **Formaat van identiteitskaart**: `AsIs`

Het antwoord zou zijn:

```xml
HTTP/1.1 200 OK
Connection: Keep-Alive
Server: Day-Servlet-Engine/4.1.24
Content-Type: text/html;charset=utf-8
Date: Thu, 23 Aug 2012 09:58:39 GMT
Transfer-Encoding: chunked

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "https://www.w3.org/TR/html4/strict.dtd">
<html>
<head>
    <meta http-equiv="content-type" content="text/html; charset=UTF-8">
    <title>Welcome to Adobe&reg; CQ5</title>
....
```

Dit werkt ook als u daarom vraagt:
`http://localhost:4502/libs/cq/core/content/welcome.html?TestParameter=admin`

Of u kunt de volgende krullopdracht gebruiken om de `TestHeader` header naar `admin:` te verzenden
`curl -D - -H "TestHeader: admin" http://localhost:4502/libs/cq/core/content/welcome.html`

>[!NOTE]
>
>Wanneer u de aanvraagparameter in een browser gebruikt, ziet u slechts een deel van de HTML - zonder CSS. Dit komt omdat alle verzoeken van de HTML zonder de verzoekparameter worden gedaan.

## Koppelingen AEM afmelden verwijderen {#removing-aem-sign-out-links}

Wanneer u SSO gebruikt, worden aanmelden en afmelden extern afgehandeld, zodat AEM eigen aftekenkoppelingen niet langer van toepassing zijn en moeten worden verwijderd.

U kunt de koppeling voor uitloggen op het welkomstscherm als volgt verwijderen.

1. Bedekken `/libs/cq/core/components/welcome/welcome.jsp` tot `/apps/cq/core/components/welcome/welcome.jsp`
1. het volgende deel uit het gsp verwijderen.

   `<a href="#" onclick="signout('<%= request.getContextPath() %>');" class="signout"><%= i18n.get("sign out", "welcome screen") %>`

Ga als volgt te werk om de koppeling voor uitloggen die beschikbaar is in het persoonlijke menu van de gebruiker in de rechterbovenhoek te verwijderen:

1. Bedekken `/libs/cq/ui/widgets/source/widgets/UserInfo.js` tot `/apps/cq/ui/widgets/source/widgets/UserInfo.js`

1. Verwijder het volgende deel uit het bestand:

   ```
   menu.addMenuItem({
       "text":CQ.I18n.getMessage("Sign out"),
       "cls": "cq-userinfo-logout",
       "handler": this.logout
   });
   menu.addSeparator();
   ```
