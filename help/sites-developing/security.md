---
title: Beveiliging
seo-title: Beveiliging
description: De Veiligheid van de toepassing begint tijdens de ontwikkelingsfase
seo-description: De Veiligheid van de toepassing begint tijdens de ontwikkelingsfase
uuid: efd5f3bc-da07-4fc8-a6ce-f1e6f5084c9e
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
discoiquuid: d2267663-6c1d-413c-9862-e82e21ae6906
translation-type: tm+mt
source-git-commit: 5128a08d4db21cda821de0698b0ac63ceed24379

---


# Beveiliging{#security}

De Veiligheid van de toepassing begint tijdens de ontwikkelingsfase. Adobe raadt u aan de volgende best practices op het gebied van beveiliging toe te passen.

## Aanvraagsessie gebruiken {#use-request-session}

Adobe raadt aan dat elke toegang tot de opslagplaats wordt uitgevoerd volgens het principe van toegangsrechten voor de gebruiker. Hierbij wordt gebruikgemaakt van de sessie die is gebonden aan de aanvraag van de gebruiker en van een juiste toegangscontrole.

## Beveiligen tegen XSS (Cross-Site Scripting) {#protect-against-cross-site-scripting-xss}

Met XSS (Cross-site scripting) kunnen aanvallers code injecteren in webpagina&#39;s die door andere gebruikers worden weergegeven. Deze kwetsbaarheid op het gebied van beveiliging kan door kwaadaardige webgebruikers worden misbruikt om toegangsbesturingselementen te omzeilen.

AEM past het beginsel toe om alle gebruiker-geleverde inhoud op output te filtreren. Het voorkomen van XSS krijgt de hoogste prioriteit tijdens zowel ontwikkeling als testen.

Het XSS-beveiligingsmechanisme dat door AEM wordt geboden, is gebaseerd op de [AntiSamy Java-bibliotheek](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) van [OWASP (het Open Web Application Security Project)](https://www.owasp.org/). De standaardconfiguratie van AntiSamy vindt u op

`/libs/cq/xssprotection/config.xml`

Het is belangrijk dat u deze configuratie aan uw eigen veiligheidsbehoeften aanpast door het configuratiedossier te bedekken. De officiële [documentatie](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) AntiSamy zal u van alle informatie voorzien u nodig hebt om uw veiligheidsvereisten uit te voeren.

>[!NOTE]
>
>We raden u ten zeerste aan om altijd toegang te krijgen tot de XSS-beveiligings-API met behulp van de [XSSAPI-API van AEM](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/adobe/granite/xss/XSSAPI.html).

Bovendien, kan een firewall van de Webtoepassing, zoals [mod_security voor Apache](https://www.modsecurity.org), betrouwbare, centrale controle over de veiligheid van het plaatsingsmilieu verstrekken en tegen eerder niet ontdekte dwars-plaats scripting aanvallen beschermen.

## Toegang tot Cloud Service-informatie {#access-to-cloud-service-information}

>[!NOTE]
>
>ACLs voor de Informatie van de Dienst van de Wolk evenals de montages OSGi die worden vereist om uw instantie te beveiligen worden geautomatiseerd als deel van de Klaar Wijze [van de](/help/sites-administering/production-ready.md)Productie. Terwijl dit betekent dat u niet de configuratieveranderingen manueel hoeft aan te brengen, wordt het nog geadviseerd dat u hen herzien alvorens u met uw plaatsing gaat leven.

Wanneer u uw AEM-exemplaar [integreert met de Adobe Marketing Cloud](/help/sites-administering/marketing-cloud.md) , gebruikt u [Cloud Service-configuraties](/help/sites-developing/extending-cloud-config.md). Informatie over deze configuraties, samen met alle verzamelde statistieken, wordt opgeslagen in de gegevensopslagruimte. Wij adviseren dat, als u deze functionaliteit gebruikt, u controleert of de standaardveiligheid op deze informatie uw vereisten aanpast.

De module webservicesSupport schrijft statistieken en configuratiegegevens onder:

`/etc/cloudservices`

Met de standaardmachtigingen:

* Auteursomgeving: `read` for `contributors`

* Publicatie-omgeving: `read` for `everyone`

## Beveiligen tegen aanvallen van smeden voor meerdere sites {#protect-against-cross-site-request-forgery-attacks}

Voor meer informatie over de veiligheidsmechanismen gebruikt AEM om aanvallen te verlichten CSRF, zie de sectie van de Filter [van de Verkoper van de](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) Verkoop van de Controle van de Veiligheid en de documentatie [van het Kader van de Bescherming](/help/sites-developing/csrf-protection.md)CSRF.