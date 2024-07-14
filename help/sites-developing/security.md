---
title: Beveiliging
description: De Veiligheid van de toepassing begint tijdens de ontwikkelingsfase
exl-id: c4f7f45f-224b-4fc3-b4b0-f5b21b8a466f
solution: Experience Manager, Experience Manager Sites
feature: Developing,Security
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Beveiliging{#security}

De Veiligheid van de toepassing begint tijdens de ontwikkelingsfase. Adobe raadt u aan de volgende best practices op het gebied van beveiliging toe te passen.

## Aanvraagsessie gebruiken {#use-request-session}

Na het beginsel van minste voorrecht, adviseert de Adobe dat elke bewaarplaatstoegang wordt gedaan door de zitting te gebruiken verbindend aan het gebruikersverzoek en behoorlijk toegangsbeheer.

## Protect tegen XSS (Cross-Site Scripting) {#protect-against-cross-site-scripting-xss}

Met XSS (Cross-site scripting) kunnen aanvallers code injecteren in webpagina&#39;s die door andere gebruikers worden weergegeven. Deze kwetsbaarheid op het gebied van beveiliging kan door kwaadaardige webgebruikers worden misbruikt om toegangsbesturingselementen te omzeilen.

AEM past het beginsel toe van het filtreren van alle gebruiker-geleverde inhoud op output. Het voorkomen van XSS krijgt de hoogste prioriteit tijdens zowel ontwikkeling als testen.

Het XSS beschermingsmechanisme dat door AEM wordt verstrekt is gebaseerd op de [ Bibliotheek Java™ van AntiSamy ](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) door [ wordt verstrekt OWASP (het Open Project van de Veiligheid van de Toepassing van het Web) ](https://owasp.org/). De standaardconfiguratie van AntiSamy vindt u op

`/libs/cq/xssprotection/config.xml`

Het is belangrijk dat u deze configuratie aanpast aan uw eigen veiligheidsbehoeften door het configuratiedossier te bedekken. De officiële [ documentatie AntiSamy ](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) voorziet u van alle informatie u uw veiligheidsvereisten moet uitvoeren.

>[!NOTE]
>
>De Adobe adviseert dat u altijd tot de XSS bescherming API toegang hebt door [ XSSAPI te gebruiken die door AEM ](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/xss/XSSAPI.html) wordt verstrekt.

Ook, kan een firewall van de Webtoepassing, zoals [ mod_security voor Apache ](https://www.modsecurity.org), betrouwbare, centrale controle over de veiligheid van het plaatsingsmilieu verstrekken en tegen eerder onontdekte dwars-plaats scripting aanvallen beschermen.

## Toegang tot informatie over Cloud Servicen {#access-to-cloud-service-information}

>[!NOTE]
>
>ACLs voor de Informatie van de Cloud Service en de montages OSGi die worden vereist om uw instantie te beveiligen worden geautomatiseerd als deel van de [ Klaar Wijze van de Productie ](/help/sites-administering/production-ready.md). Terwijl dit betekent dat u niet de configuratie moet manueel veranderen, wordt het nog geadviseerd dat u hen controleert alvorens u met uw plaatsing gaat leven.

Wanneer u [ uw AEM instantie met Adobe Experience Cloud ](/help/sites-administering/marketing-cloud.md) integreert, gebruikt u [ de configuraties van de Cloud Service ](/help/sites-developing/extending-cloud-config.md). Informatie over deze configuraties, samen met alle verzamelde statistieken, wordt opgeslagen in de gegevensopslagruimte. Adobe raadt aan dat als u deze functionaliteit gebruikt, u controleert of de standaardbeveiliging van deze informatie aan uw vereisten voldoet.

De module webservicesSupport schrijft statistieken en configuratiegegevens onder:

`/etc/cloudservices`

Met de standaardmachtigingen:

* Auteursomgeving: `read` voor `contributors`

* Publish-omgeving: `read` voor `everyone`

## Protect tegen aanvallen van smeedmachines voor aanvragen voor meerdere sites {#protect-against-cross-site-request-forgery-attacks}

Voor meer informatie over de veiligheidsmechanismen AEM aanwenden om aanvallen te verlichten CSRF, zie de ](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) sectie van de Filter van de Verwijzer van 0} Verschuiving van de Controle van de Veiligheid en de [ documentatie van het Kader van de Bescherming CSRF ](/help/sites-developing/csrf-protection.md).[
