---
title: Oplossing voor kwetsbaarheden in het Lentekader voor AEM Forms op JEE
description: Oplossing voor kwetsbaarheden in het Lentekader voor AEM Forms op JEE
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Security
geptopics: SG_AEMFORMS/categories/jee
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 61cce7cd8290156bec6dcc351a59093f545a4ec7
workflow-type: tm+mt
source-wordcount: '563'
ht-degree: 0%

---


# Risico&#39;s van het voorjaarskader voor AEM Forms op JEE verminderen

Dit document biedt richtlijnen voor het verhelpen van twee kritieke kwetsbaarheden in het lentekader die van invloed zijn op AEM Forms op JEE:

- **[CVE-2024-38819 ](https://spring.io/security/cve-2024-38819)**: De kwetsbaarheid van de traversal van de weg in functionele Webkaders
- **[CVE-2024-38820 ](https://spring.io/security/cve-2024-38820)**: De Gevallengevoelige Uitzondering van de Geval van DataBinder van het Kader van het Kader van het Leer Gevoelige

## Betrokken versies

- Adobe Experience Manager 6.5 Forms in juni
- Versies AEM 6.5 Forms GA naar 6.5.22.0

## Resolutie

### Versiespecifieke oplossingen

| AEM Forms-versie | Vereiste actie |
|-------------------|-----------------|
| 6.5.22.0 | 1. [ Download hotfix voor uw milieu ](/help/release-notes/aem-forms-hotfix.md). </br> 2. Om deze moeilijke situatie te installeren, volg de instructies om het Pak van de Dienst op een Vorm van AEM op JEE ](/help/release-notes/aem-forms-current-service-pack-installation-instructions.md) te installeren.[ |
| 6.5.17.0 - 6.5.21.0 | [ pas handmatige matigingsstappen ](#manual-mitigation-steps) toe. |
| 6.5 - 6.5.16.0 | 1. [ installeer het recentste de dienstpak ](/help/release-notes/release-notes.md)<br> 2. [ voert de aangewezen oplossing ](#version-specific-solutions) uit die op uw bijgewerkte versie wordt gebaseerd. |

> **Nota**: AEM Forms steunt officieel slechts de zes meest recente de dienstpakken. Gebruikers met een oudere versie dienen eerst een upgrade uit te voeren naar het nieuwste servicepakket en vervolgens de vereiste hotfix te installeren.

## Overwegingen bij de implementatie

### Voor geclusterde omgevingen

Wanneer het werken met een gegroepeerde plaatsing:

- Pas JAR dossiervervangingen (Stap #4) op **toe alle knopen** in de cluster
- Consistentie behouden door identieke JAR-versies op alle servers te gebruiken
- Voltooi updates op alle knopen alvorens om het even welke dienst opnieuw te beginnen
- Implementeer een gecoördineerde strategie voor opnieuw opstarten om systeemdowntime tot een minimum te beperken

### Voor omgevingen met één knooppunt

Bij het werken met een standalone plaatsing:

- Volg een vereenvoudigd proces omdat er geen locatorservers zijn om te beheren
- Alle stappen met betrekking tot de configuratie of het opstarten van de locator-server weglaten
- Voltooi alle andere stappen zoals die worden geïnstrueerd, met name de vervangingen van JAR en manifestupdates
- Start de toepassingsserver opnieuw nadat u alle wijzigingen hebt geïmplementeerd

## Handmatige correctiestappen

1. Stop de toepassingsservers.
1. Stop- en locatorservers.
1. JAR&#39;s van vering verwijderen uit kern-EAR:
   1. Navigeer naar `[Adobe_Experience_Manager_Forms installation directory]/deploy` .
   1. Open het `adobe-core-<appserver>.ear` -bestand met een hulpprogramma voor archiefbeheer. Waar `<appserver>` kan zijn JBoss, WebLogic of WebSphere, afhankelijk van uw omgeving:
   - **voor JBoss:** navigeer aan de `ear/lib` omslag en schrap de volgende JAR- dossiers:
- `spring-core-<version>.jar`
- `spring-web-<version>.jar`

   - **voor WebLogic of WebSphere:** schrap de volgende JAR dossiers van de wortel van EAR:
- `spring-core-<version>.jar`
- `spring-web-<version>.jar`

   - **voor alle toepassingsservers:** op het wortelniveau van `adobe-core-<appserver>.ear`, open het `adobe-dscf.jar` dossier en geef het `META-INF/MANIFEST.MF` dossier uit om het even welke verwijzingen naar de volgende JAR dossiers te verwijderen:
- `spring-core-<version>.jar`
- `spring-web-<version>.jar`

1. JAR-bestanden vervangen uit Geode-distributie:
   1. Navigeren naar `<Adobe_Experience_Manager_Forms>/lib/caching/lib`
   1. Vervang de bestaande JAR-bestanden door de bijgewerkte versies:
   - `spring-context-<version>.jar` → `spring-context-6.1.14.jar`
   - `spring-beans-<version>.jar` → `spring-beans-6.1.14.jar`
   - `spring-core-<version>.jar` → `spring-core-6.1.14.jar`
   - `spring-jcl-<version>.jar` → `spring-jcl-6.1.14.jar`
   - `spring-web-<version>.jar` → `spring-web-6.1.14.jar`

   Om de nieuwere JAR dossiers te krijgen, download het voorjaar-6.1.14-jars.zip- dossier van [ de Distributie van de Software van Adobe ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/hotfix/aem-6-5-0-hotfix-vuln-30727/spring-6.1.14-jars.zip) en haal het dossier van het PIT om tot de bijgewerkte JAR dossiers van het Kader van de Lente toegang te hebben.

   1. Werk de bestanden MANIFEST.MF bij in de volgende JAR-bestanden:
   - `geode-server-all-<version>.jar`
   - `gfsh-dependencies.jar`

   Voor elke JAR:
   - De JAR openen met een hulpprogramma voor archiefbeheer
   - Het `META-INF/MANIFEST.MF` -bestand zoeken en uitpakken
   - Het bestand MANIFEST.MF bewerken in een teksteditor
   - Zoek de sectie &#39;Class-Path&#39; en werk alle verwijzingen naar het Leerframework bij:
      - `spring-core-<version>.jar` t/m `spring-core-6.1.14.jar`
      - `spring-web-<version>.jar` t/m `spring-web-6.1.14.jar`
      - `spring-context-<version>.jar` t/m `spring-context-6.1.14.jar`
      - `spring-beans-<version>.jar` t/m `spring-beans-6.1.14.jar`
      - `spring-jcl-<version>.jar` t/m `spring-jcl-6.1.14.jar`
   - Het gewijzigde bestand MANIFEST.MF opslaan
   - Vervang het originele MANIFEST.MF in JAR met uw bijgewerkte versie
   - Het JAR-bestand opslaan

   1. Veelvoorkomende problemen om te controleren op:
      - Geen dubbele vermeldingen in manifest controleren
      - Regeleinden behouden
      - Controleren of alle JAR&#39;s waarnaar wordt verwezen, bestaan op de opgegeven locaties

   1. Controlestappen:
      - Controleren of het manifest correct is bijgewerkt
      - Controleren of er correct wordt verwezen naar alle veerafhankelijkheden
      - Zorg ervoor dat er geen oude versieverwijzingen overblijven
      - Test de toepassing om te controleren of er geen problemen met het laden van klassen zijn

1. Voer Configuration Manager uit.

1. Servers opnieuw starten:
   - Locatorservers starten met JDK 17
   - Start de toepassingsservers met dezelfde JDK-versie (JDK 8 of JDK 11) die eerder is gebruikt.
