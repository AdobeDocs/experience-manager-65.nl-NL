---
title: Single Sign On
seo-title: Single Sign On
description: Leer hoe te om Enige Sign aan (SSO) voor een AEM instantie te vormen.
seo-description: Leer hoe te om Enige Sign aan (SSO) voor een AEM instantie te vormen.
uuid: b8dcb28e-4604-4da5-b8dd-4e1e2cbdda18
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring, Security
content-type: reference
discoiquuid: 86e8dc12-608d-4aff-ba7a-5524f6b4eb0d
feature: Configuring
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '756'
ht-degree: 0%

---


# Enkelvoudige aanmelding {#single-sign-on}

Met Single Sign On (SSO) heeft een gebruiker toegang tot meerdere systemen nadat hij de verificatiegegevens (zoals een gebruikersnaam en wachtwoord) eenmaal heeft opgegeven. Een afzonderlijk systeem (dat als vertrouwde op authentiek wordt bekend) voert de authentificatie uit en verstrekt Experience Manager de gebruikersgeloofsbrieven. De Experience Manager controleert en handhaaft de toegangstoestemmingen voor de gebruiker (d.w.z. bepaalt welke middelen de gebruiker wordt toegestaan om toegang te hebben).

De service SSO Authentication Handler ( `com.adobe.granite.auth.sso.impl.SsoAuthenticationHandler`) verwerkt de verificatieresultaten die door de vertrouwde authenticator worden verschaft. De manager van de Authentificatie SSO zoekt naar een ssid (Herkenningsteken SSO) als waarde van een speciaal attribuut in de volgende plaatsen in deze orde:

1. Aanvraagkoppen
1. Cookies
1. Parameters aanvragen

Wanneer een waarde wordt gevonden, is het onderzoek gebeëindigd en deze waarde wordt gebruikt.

Vorm de volgende twee diensten om de naam van de attributen te erkennen die de steun opslaan:

* De aanmeldingsmodule.
* De SSO-verificatieservice.

U moet dezelfde kenmerknaam opgeven voor beide services. Het attribuut is inbegrepen in `SimpleCredentials` die aan `Repository.login` wordt verstrekt. De waarde van het kenmerk is irrelevant en wordt genegeerd, de aanwezigheid ervan is alleen belangrijk en geverifieerd.

## SSO {#configuring-sso} configureren

Om SSO voor een AEM instantie te vormen, moet u [de Handler van de Authentificatie van SSO](/help/sites-deploying/osgi-configuration-settings.md#adobegranitessoauthenticationhandler) vormen:

1. Wanneer het werken met AEM zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren; zie [Het vormen OSGi](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

   Bijvoorbeeld voor NTLM-set:

   * **Pad:** indien vereist; bijvoorbeeld:  `/`
   * **Namen** koptekst:  `LOGON_USER`
   * **Id-indeling**:  `^<DOMAIN>\\(.+)$`

      Waar `<*DOMAIN*>` door uw eigen domeinnaam wordt vervangen.
   Voor CoSign:

   * **Pad:** indien vereist; bijvoorbeeld:  `/`
   * **Namen** koptekst: remote_user
   * **ID-indeling:** asIs

   Voor SiteMinder:

   * **Pad:** indien vereist; bijvoorbeeld:  `/`
   * **koptekstnamen:** SM_USER
   * **Id-indeling**: asIs



1. Bevestig dat Single Sign On naar wens werkt. met inbegrip van de vergunning.

>[!CAUTION]
>
>Zorg ervoor dat de gebruikers tot AEM niet direct kunnen toegang hebben als SSO wordt gevormd.
>
>Door gebruikers te verplichten door een Webserver te gaan die de agent van uw SSO systeem in werking stelt, wordt gewaarborgd dat geen gebruiker een kopbal, een koekje of een parameter kan direct verzenden die de gebruiker zal leiden om door AEM worden vertrouwd, aangezien de agent dergelijke informatie zal filtreren indien verzonden van de buitenkant.
>
>Elke gebruiker die rechtstreeks toegang heeft tot de AEM zonder de webserver te gebruiken, kan als gebruiker optreden door de header, cookie of parameter te verzenden als de namen bekend zijn.
>
>Zorg ook dat van kopballen, koekjes en de namen van de verzoekparameter, u slechts vormt die voor uw opstelling SSO wordt vereist.


>[!NOTE]
>
>Single Sign On wordt vaak gebruikt in combinatie met [LDAP](/help/sites-administering/ldap-config.md).

>[!NOTE]
>
>Als u ook [Dispatcher](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher.html) met de Server van de Informatie van Microsoft Internet (IIS) gebruikt, dan zal de extra configuratie binnen worden vereist:
>
>* `disp_iis.ini`
>* IIS

>
>
In `disp_iis.ini`-set:
>(zie [De Dispatcher installeren met Microsoft Internet Information Server](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-install.html#microsoft-internet-information-server) voor volledige details)
>
>* `servervariables=1` (stuurt IIS-servervariabelen als aanvraagheaders door naar de externe instantie)
>* `replaceauthorization=1` (Vervangt een koptekst met de naam &quot;Autorisatie&quot;, anders dan &quot;Standaard&quot;, door de waarde &quot;Standaard&quot;.)

>
>
In IIS:
>
>* uitschakelen **Anonieme toegang**
   >
   >
* **Geïntegreerde Windows-verificatie** inschakelen

>



U kunt zien welke authentificatiemanager op om het even welke sectie van de inhoudsboom wordt toegepast door **Authenticator** optie van de Console van Felix te gebruiken; bijvoorbeeld:

`http://localhost:4502/system/console/slingauth`

De handler die het beste overeenkomt met het pad wordt als eerste gevraagd. Bijvoorbeeld, als u manager-A voor de weg `/` en manager-B voor de weg `/content` vormt, dan zal een verzoek aan `/content/mypage.html` eerst manager-B vragen.

![screen_shot_2012-02-15at21006pm](assets/screen_shot_2012-02-15at21006pm.png)

### Voorbeeld {#example}

Voor een cookieverzoek (gebruikend URL `http://localhost:4502/libs/wcm/content/siteadmin.html`):

```xml
GET /libs/cq/core/content/welcome.html HTTP/1.1
Host: localhost:4502
Cookie: TestCookie=admin
```

De volgende configuratie gebruiken:

* **Pad**:  `/`

* **Namen** koptekst:  `TestHeader`

* **Cookie-namen**:  `TestCookie`

* **Parameternamen**:  `TestParameter`

* **Id-indeling**:  `AsIs`

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

U kunt ook de volgende krullopdracht gebruiken om de `TestHeader`-koptekst naar `admin:` te sturen
`curl -D - -H "TestHeader: admin" http://localhost:4502/libs/cq/core/content/welcome.html`

>[!NOTE]
>
>Als u de parameter request in een browser gebruikt, ziet u slechts een deel van de HTML - zonder CSS. Dit komt omdat alle verzoeken van HTML zonder de verzoekparameter worden gedaan.

## Koppelingen voor AEM afmelden verwijderen {#removing-aem-sign-out-links}

Wanneer u SSO gebruikt, worden aanmelden en afmelden extern afgehandeld, zodat AEM eigen aftekenkoppelingen niet langer van toepassing zijn en moeten worden verwijderd.

U kunt de koppeling Afmelden op het welkomstscherm als volgt verwijderen.

1. Bedekken `/libs/cq/core/components/welcome/welcome.jsp` tot `/apps/cq/core/components/welcome/welcome.jsp`
1. het volgende deel uit het gsp verwijderen.

   `<a href="#" onclick="signout('<%= request.getContextPath() %>');" class="signout"><%= i18n.get("sign out", "welcome screen") %>`

Voer de volgende stappen uit om de koppeling Afmelden die beschikbaar is in het persoonlijke menu van de gebruiker in de rechterbovenhoek te verwijderen:

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

