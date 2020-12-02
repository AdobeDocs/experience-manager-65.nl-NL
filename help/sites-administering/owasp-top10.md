---
title: OWASP Top 10
seo-title: OWASP Top 10
description: Leer hoe AEM omgaat met de 10 belangrijkste beveiligingsrisico's van OWASP.
seo-description: Leer hoe AEM omgaat met de 10 belangrijkste beveiligingsrisico's van OWASP.
uuid: a5a7e130-e15b-47ae-ba21-448f9ac76074
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: e5323ae8-bc37-4bc6-bca6-9763e18c8e76
translation-type: tm+mt
source-git-commit: cd7331f5f57ec90ea72d41d467891dc832347a3c
workflow-type: tm+mt
source-wordcount: '509'
ht-degree: 0%

---


# OWASP Top 10{#owasp-top}

[Open het Project van de Veiligheid van de Toepassing van het Web](https://www.owasp.org) (OWASP) handhaaft een lijst van wat zij als [Hoogste 10 de Veiligheidsrisico&#39;s van de Veiligheid van de Toepassing van het Web](https://www.owasp.org/index.php/OWASP_Top_Ten_Project) beschouwen.

Deze worden hieronder vermeld, samen met een uitleg van de manier waarop CRX ermee omgaat.

## 1. Injectie {#injection}

* SQL - Voorkomen door ontwerp: De standaardopslagopstelling omvat noch vereist een traditionele gegevensbestand, al gegevens wordt opgeslagen in de inhoudsbewaarplaats. Alle toegang is beperkt tot geverifieerde gebruikers en kan alleen worden uitgevoerd via de JCR API. SQL wordt alleen ondersteund voor zoekopdrachten (SELECT). Bovendien biedt SQL ondersteuning voor waardebinding.
* LDAP - LDAP-injectie is niet mogelijk, omdat de verificatiemodule de invoer filtert en de gebruiker importeert met de methode bind.
* OS - Er wordt geen shell-uitvoering uitgevoerd vanuit de toepassing.

## 2. XSS (cross-site scripting) {#cross-site-scripting-xss}

De algemene matigingspraktijk moet alle output van gebruiker-geproduceerde inhoud coderen gebruikend een server-kantXSS beschermingsbibliotheek die op [OWASP Encoder](https://www.owasp.org/index.php/OWASP_Java_Encoder_Project) en [AntiSamy](https://www.owasp.org/index.php/Category:OWASP_AntiSamy_Project) wordt gebaseerd.

XSS is een hoogste prioriteit tijdens zowel het testen als de ontwikkeling, en om het even welke gevonden kwesties worden (typisch) onmiddellijk opgelost.

## 3. Verbroken verificatie- en sessiebeheer {#broken-authentication-and-session-management}

AEM gebruikt geluidstechnieken en beproefde verificatietechnieken, waarbij wordt uitgegaan van [Apache Jackrabbit](https://jackrabbit.apache.org/) en [Apache Sling](https://sling.apache.org/). Browser/HTTP-sessies worden niet gebruikt in AEM.

## 4. Onveilige directe objectverwijzingen {#insecure-direct-object-references}

Alle toegang tot gegevensvoorwerpen wordt bemiddelen door de bewaarplaats en daarom beperkt door op rol gebaseerd toegangsbeheer.

## 5. Smederij voor verzoeken tussen sites (CSRF) {#cross-site-request-forgery-csrf}

Smeedraaien voor aanvragen tussen sites (CSRF) wordt beperkt door automatisch een cryptografisch token in alle formulieren en AJAX te injecteren en dit token op de server voor elke POST te controleren.

Bovendien AEM schepen met een verwijzing-kopbal gebaseerde filter, die aan *only* kan worden gevormd staan de verzoeken van de POST van specifieke gastheren (die in een lijst worden bepaald) toe.

## 6. Onjuiste configuratie van beveiliging {#security-misconfiguration}

Het is onmogelijk te garanderen dat alle software altijd correct is geconfigureerd. Wij streven er echter naar zoveel mogelijk begeleiding te bieden en de configuratie zo eenvoudig mogelijk te maken. Bovendien AEM schepen met [geïntegreerde Gezondheidscontroles van de Veiligheid](/help/sites-administering/operations-dashboard.md) die u helpen veiligheidsconfiguratie in een blik controleren.

Lees de [Beveiligingschecklist](/help/sites-administering/security-checklist.md) voor meer informatie die u stapsgewijze verhardende instructies biedt.

## 7. Onveilige cryptografische opslag {#insecure-cryptographic-storage}

Wachtwoorden worden opgeslagen als cryptografische hashes in het gebruikersknooppunt; deze knooppunten kunnen standaard alleen door de beheerder en de gebruiker zelf worden gelezen.

Gevoelige gegevens zoals referenties van derden worden in gecodeerde vorm opgeslagen met behulp van een voor FIPS 140-2 gecertificeerde cryptografische bibliotheek.

## 8. Kan URL-toegang niet beperken {#failure-to-restrict-url-access}

De gegevensopslagruimte staat het plaatsen van [volledig-gegrainde voorrechten (zoals gespecificeerd door JCR)](https://docs.adobe.com/content/docs/en/spec/jcr/2.0/16_Access_Control_Management.html) voor om het even welke bepaalde gebruiker of groep op om het even welk bepaald weg toe, door toegangsbeheeringangen. Toegangsbeperkingen worden afgedwongen door de repository.

## 9. Onvoldoende beveiliging van transportlaag {#insufficient-transport-layer-protection}

Gemengde door serverconfiguratie (bijvoorbeeld alleen HTTPS gebruiken).

## 10 Niet-gevalideerde omleidingen en doorsturen {#unvalidated-redirects-and-forwards}

Gematigd door alle omleidingen aan gebruiker-geleverde bestemmingen aan interne plaatsen te beperken.

