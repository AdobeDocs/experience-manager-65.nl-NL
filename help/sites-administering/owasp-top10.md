---
title: OWASP Top 10
description: Leer hoe AEM de hoogste tien beveiligingsrisico's van OWASP aanpakt.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: 8b2a2f1d-8286-4ba5-8fe2-627509c72a45
feature: Security
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 48d12388d4707e61117116ca7eb533cea8c7ef34
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# OWASP Top 10{#owasp-top}

De [Beveiligingsproject webtoepassing openen](https://owasp.org/) (OWASP) houdt een lijst bij van wat zij als de [De tien grootste beveiligingsrisico&#39;s voor webtoepassingen](https://owasp.org/www-project-top-ten/).

Deze worden hieronder vermeld, samen met een uitleg van de manier waarop CRX ermee omgaat.

## 1. Injectie {#injection}

* SQL - Voorkomen door ontwerp: De standaardopslagopstelling omvat noch vereist een traditionele gegevensbestand, alle gegevens worden opgeslagen in de inhoudsbewaarplaats. Alle toegang is beperkt tot geverifieerde gebruikers en kan alleen worden uitgevoerd via de JCR API. SQL wordt alleen ondersteund voor zoekopdrachten (SELECT). Bovendien biedt SQL ondersteuning voor waardebinding.
* LDAP - LDAP-injectie is niet mogelijk, omdat de verificatiemodule de invoer filtert en de gebruiker importeert met de methode bind.
* OS - Er wordt geen shell uitgevoerd vanuit de toepassing.

## 2. XSS (Cross-Site Scripting) {#cross-site-scripting-xss}

De algemene matigingspraktijk moet al output van gebruiker-geproduceerde inhoud coderen gebruikend een server-kantXSS beschermingsbibliotheek die op wordt gebaseerd [OWASP Encoder](https://owasp.org/www-project-java-encoder/) en [AntiSamy](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project).

XSS is een hoogste prioriteit tijdens zowel het testen als de ontwikkeling, en om het even welke gevonden kwesties worden (typisch) onmiddellijk opgelost.

## 3. Verbroken verificatie en sessiebeheer {#broken-authentication-and-session-management}

AEM gebruikt correcte en bewezen authentificatietechnieken, die op [Apache Jackrabbit](https://jackrabbit.apache.org/jcr/index.html) en [Apache Sling](https://sling.apache.org/). Browser/HTTP-sessies worden niet gebruikt in AEM.

## 4. Onveilige verwijzingen naar directe objecten {#insecure-direct-object-references}

Alle toegang tot gegevensvoorwerpen wordt bemiddelen door de bewaarplaats en daarom beperkt door op rol-gebaseerd toegangsbeheer.

## 5. Smeeuw voor aanvragen voor andere sites (CSRF) {#cross-site-request-forgery-csrf}

Smeedraaien voor aanvragen tussen sites (CSRF) wordt beperkt door automatisch een cryptografisch token in alle formulieren en AJAX te injecteren en dit token op de server voor elke POST te controleren.

Bovendien AEM schepen met een verwijzing-kopbal gebaseerd filter, dat kan worden gevormd aan *alleen* staan verzoeken van POSTEN van specifieke hosts (gedefinieerd in een lijst) toe.

## 6. Onjuiste beveiliging {#security-misconfiguration}

Het is onmogelijk te garanderen dat alle software altijd correct is geconfigureerd. De Adobe streeft er echter naar zoveel mogelijk begeleiding te bieden en de configuratie zo eenvoudig mogelijk te maken. Bovendien AEM schepen met [geïntegreerde veiligheidscontroles](/help/sites-administering/operations-dashboard.md) die u helpen veiligheidsconfiguratie in een oogopslag controleren.

Controleer de [Beveiligingscontrolelijst](/help/sites-administering/security-checklist.md) voor meer informatie die u van geleidelijke het verharden instructies voorziet.

## 7. Onveilige cryptografische opslag {#insecure-cryptographic-storage}

Wachtwoorden worden opgeslagen als cryptografische hashes in het gebruikersknooppunt. Dergelijke knooppunten kunnen standaard alleen door de beheerder en de gebruiker zelf worden gelezen.

Gevoelige gegevens zoals referenties van derden worden in gecodeerde vorm opgeslagen met behulp van een voor FIPS 140-2 gecertificeerde cryptografische bibliotheek.

## 8. Kan URL-toegang niet beperken {#failure-to-restrict-url-access}

De gegevensopslagruimte maakt het mogelijk om [fijnkorrelige bevoegdheden (zoals gespecificeerd door het JCR)](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html) voor om het even welke bepaalde gebruiker of groep bij om het even welk bepaald weg, door toegangsbeheeringangen. Toegangsbeperkingen worden afgedwongen door de opslagplaats.

## 9. Onvoldoende bescherming van de Laag van het Vervoer {#insufficient-transport-layer-protection}

Gemengde door serverconfiguratie (bijvoorbeeld alleen HTTPS gebruiken).

## 10. Niet-gevalideerde omleidingen en doorsturen {#unvalidated-redirects-and-forwards}

Gematigd door alle omleidingen aan gebruiker-geleverde bestemmingen aan interne plaatsen te beperken.
