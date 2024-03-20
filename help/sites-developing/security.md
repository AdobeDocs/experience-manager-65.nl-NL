---
title: Beveiliging
description: De Veiligheid van de toepassing begint tijdens de ontwikkelingsfase
exl-id: c4f7f45f-224b-4fc3-b4b0-f5b21b8a466f
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
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

Het door AEM geboden XSS-beveiligingsmechanisme is gebaseerd op [AntiSamy Java™-bibliotheek](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) verstrekt door [EIWASP (het Open Project van de Veiligheid van de Toepassing van het Web)](https://owasp.org/). De standaardconfiguratie van AntiSamy vindt u op

`/libs/cq/xssprotection/config.xml`

Het is belangrijk dat u deze configuratie aanpast aan uw eigen veiligheidsbehoeften door het configuratiedossier te bedekken. De ambtenaar [AntiSamy-documentatie](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) verstrekt u van alle informatie u uw veiligheidsvereisten moet uitvoeren.

>[!NOTE]
>
>Adobe raadt u aan om altijd toegang te krijgen tot de XSS-beveiligings-API met de [XSSAPI verstrekt door AEM](https://developer.adobe.com/experience-manager/reference-materials/6-5/javadoc/com/adobe/granite/xss/XSSAPI.html).

Ook een webtoepassingsfirewall, zoals [mod_security voor Apache](https://www.modsecurity.org), kan betrouwbare, centrale controle over de veiligheid van het plaatsingsmilieu verstrekken en tegen eerder onontdekte dwars-plaats scripting aanvallen beschermen.

## Toegang tot informatie over Cloud Servicen {#access-to-cloud-service-information}

>[!NOTE]
>
>ACLs voor de Informatie van de Cloud Service en de montages OSGi die worden vereist om uw instantie te beveiligen worden geautomatiseerd als deel van [Productiemodus](/help/sites-administering/production-ready.md). Terwijl dit betekent dat u niet de configuratie moet manueel veranderen, wordt het nog geadviseerd dat u hen controleert alvorens u met uw plaatsing gaat leven.

Wanneer u [uw AEM-exemplaar integreren met de Adobe Experience Cloud](/help/sites-administering/marketing-cloud.md), gebruikt u [Cloud Service configuraties](/help/sites-developing/extending-cloud-config.md). Informatie over deze configuraties, samen met alle verzamelde statistieken, wordt opgeslagen in de gegevensopslagruimte. Adobe raadt aan dat als u deze functionaliteit gebruikt, u controleert of de standaardbeveiliging van deze informatie aan uw vereisten voldoet.

De module webservicesSupport schrijft statistieken en configuratiegegevens onder:

`/etc/cloudservices`

Met de standaardmachtigingen:

* Auteursomgeving: `read` for `contributors`

* Publicatie-omgeving: `read` for `everyone`

## Protect tegen aanvallen van smeedmachines voor aanvragen voor meerdere sites {#protect-against-cross-site-request-forgery-attacks}

Voor meer informatie over de veiligheidsmechanismen AEM tewerkstellen om aanvallen te verlichten CSRF, zie [Filter Verschuivingsverwijzing](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) van de lijst van beveiligingscontroles en de [CSRF-beschermingskaderdocumentatie](/help/sites-developing/csrf-protection.md).
