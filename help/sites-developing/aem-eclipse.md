---
title: AEM Developer Tools for Eclipse
description: Meer informatie over Adobe Experience Manager-ontwikkelaarsgereedschappen voor Eclipse.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 00473769-c447-4966-a71e-117c669e0151
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '746'
ht-degree: 0%

---

# AEM Developer Tools for Eclipse{#aem-developer-tools-for-eclipse}

![ Cirkelvormig beeldmotief voor AEM de Hulpmiddelen van de Ontwikkelaar voor Verduistering.](do-not-localize/chlimage_1-9.png)

## Overzicht {#overview}

&quot;AEM de Hulpmiddelen van de Ontwikkelaar&quot;is een elektrisch toestel Eclipse dat op de [ insteekmodule van de Verduistering voor Apache ](https://sling.apache.org/documentation/development/ide-tooling.html) onder Vergunning 2 wordt vrijgegeven Apache.

Het biedt verschillende functies die AEM ontwikkeling vergemakkelijken:

* Naadloze integratie met AEM instanties door de Schakelaar van de Server van Eclipse.
* Synchronisatie voor inhoud en OSGI-bundels.
* Ondersteuning voor foutopsporing met de functie voor hot-swapping van code.
* Eenvoudige Bootstrap van AEM Projecten door middel van een specifieke Tovenaar van de Aanmaak van het Project.
* Het gemakkelijk uitgeven van eigenschappen JCR.

## Vereisten {#requirements}

Ga als volgt te werk voordat u de AEM Developer Tools gebruikt:

* Download en installeer [ Eclipse winde voor de Ontwikkelaars van Java™ EE ](https://www.eclipse.org/downloads/packages/release/luna/r/eclipse-ide-java-ee-developers). AEM Developer Tools ondersteunt momenteel Eclipse Kepler of nieuwer

* Kan worden gebruikt met AEM versie 5.6.1 of hoger
* Vorm uw eclipse installatie om ervoor te zorgen dat u minstens 1 GB van heapgeheugen door uw `eclipse.ini` configuratiedossier te uitgeven zoals die in [ wordt beschreven Veelgestelde Veelgestelde vragen van de Verduistering ](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse%3F) hebt.

>[!NOTE]
>
>Op macOS, klik **Eclipse.app** met de rechtermuisknop aan, en selecteer dan **tonen de Inhoud van het Pakket** om uw `eclipse.ini` te vinden.

## Hoe te om de Hulpmiddelen van de Ontwikkelaar van de AEM voor Eclipse te installeren {#how-to-install-the-aem-developer-tools-for-eclipse}

Zodra u aan de [ vereisten ](#requirements) hierboven hebt voldaan, kunt u de stop als volgt installeren:

1. Doorblader de **AEM** website van de Hulpmiddelen van de Ontwikkelaar bij `https://eclipse.adobe.com/aem/dev-tools/`.

1. Kopieer de **Verbinding van de Installatie**.

   U kunt ook een archief downloaden in plaats van de installatiekoppeling te gebruiken. Zo kunt u offline installeren, maar u kunt automatische updatemeldingen niet uitvoeren.

1. In Verduistering, open het **menu van de Hulp**.
1. Klik **installeer Nieuwe Software**.
1. Klik **toevoegen...**.
1. In **Naam** type AEM de Hulpmiddelen van de Ontwikkelaar.
1. In **Plaats** kopieert installatie URL.
1. Klik **OK**.
1. Controle zowel **AEM** als **het Verdelen** stoppen.
1. Klik op **Next**.
1. Klik op **Next**.
1. Accepteer de lincese overeenkomsten en klik **Afwerking**.
1. Klik **ja** om Eclipse opnieuw te beginnen.

## Bestaande projecten importeren {#how-to-import-existing-projects}

>[!NOTE]
>
>Zie [ hoe te met een bundel in Verduistering te werken toen het van AEM ](https://stackoverflow.com/questions/29699726/how-to-work-with-a-bundle-in-eclipse-when-it-was-downloaded-from-aem/29705407#29705407) werd gedownload.

## Het AEM perspectief {#the-aem-perspective}

De hulpmiddelen van de Ontwikkeling van de AEM voor Eclipse schepen met een Perspectief dat u volledige controle over uw AEM Projecten en instanties biedt.

![ chlimage_1-2 ](assets/chlimage_1-2a.jpeg)

## Monster nemen van meermoduleproject {#sample-multi-module-project}

De &quot;AEM Hulpmiddelen van de Ontwikkelaar&quot;omvatten een steekproef, multi-moduleproject dat u snel met een projectopstelling in Verduistering helpt krijgen. Het dient ook als gids voor beste praktijken aan verscheidene AEM eigenschappen. [ leer meer over het Archetype van het Project ](https://github.com/adobe/aem-project-archetype).

Voer de volgende stappen uit om het voorbeeldproject te maken:

1. In het **Dossier** > **Nieuw** > **het menu van het Project**, doorblader aan de **AEM** sectie en selecteer **AEM het Project van de Steekproef Multi-Module**.

   ![ chlimage_1-69 ](assets/chlimage_1-69a.png)

1. Klik op **Next**.

   >[!NOTE]
   >
   >Deze stap kan even duren omdat m2eclipse de archetype catalogi moet aftasten.

   ![ chlimage_1-70 ](assets/chlimage_1-70a.png)

1. Kies **com.adobe.granite.archetypes : steekproef-project-archetype: (hoogste aantal)** van het menu, dan klik **daarna**.

   ![ chlimage_1-71 ](assets/chlimage_1-71a.png)

1. Vul a **Naam**, **identiteitskaart van de Groep**, en a **Artifact identiteitskaart** voor het steekproefproject in. U kunt ook bepaalde geavanceerde eigenschappen instellen.

   ![ chlimage_1-72 ](assets/chlimage_1-72a.png)

1. Configureer nu een AEM server waarmee Eclipse verbinding kan maken.

   Om de debugger eigenschap te gebruiken, ben zeker u AEM op zuivert wijze begonnen, die kan worden bereikt door het volgende aan de bevellijn toe te voegen:

   ```
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![ chlimage_1-73 ](assets/chlimage_1-73a.png)

1. Klik **Afwerking**. De projectstructuur wordt gemaakt.

   >[!NOTE]
   >
   >Op een nieuwe installatie (meer specifiek: wanneer bepaalde gebiedsdelen nooit zijn gedownload) zou u het project kunnen krijgen dat met fouten wordt gecreeerd. In dit geval, volg de procedure die in [ wordt beschreven het Oplossen van Ongeldige Definitie van het Project ](#resolving-invalid-project-definition).

## Problemen oplossen {#troubleshooting}

### Ongeldige projectdefinitie oplossen {#resolving-invalid-project-definition}

Om ongeldige gebiedsdelen en projectdefinitie op te lossen ga als volgt te werk:

1. Selecteer alle gemaakte projecten.
1. Klik met de rechtermuisknop. In menu **Gemaakt**, uitgezochte **Projecten van de Update**.
1. Controle **de Updates van de Kracht van Momentopname/Versies**.
1. Klik **OK**. Eclipse probeert de vereiste afhankelijkheden te downloaden.

### Automatisch aanvullen van tagbibliotheek inschakelen in JSP-bestanden {#enabling-tag-library-autocompletion-in-jsp-files}

Automatisch aanvullen van de tagbibliotheek werkt buiten het vak, aangezien de juiste afhankelijkheden aan het project worden toegevoegd. Er is één bekend probleem wanneer u de AEM Uber Jar gebruikt, dat niet de benodigde tld- en TagExtraInfo-bestanden bevat.

Als u dit wilt omzeilen, zorgt u ervoor dat het artefact org.apache.sling.scripting.jsp.taglib zich in het klassepad vóór de AEM Uber Jar bevindt. Voor Geweven projecten, plaats het volgende gebiedsdeel in pom.xml vóór Uber Jar.

```xml
<dependency>
  <groupId>org.apache.sling</groupId>
  <artifactId>org.apache.sling.scripting.jsp.taglib</artifactId>
  <scope>provided</scope>
</dependency>
```

Zorg ervoor om de juiste versie voor uw plaatsing van AEM toe te voegen.

## Meer informatie {#more-information}

Op de officiële Apache Sling IDE-website voor Eclipse vindt u nuttige informatie:

* [**Apache het Verdelen van winde tooling voor de Gids van de Gebruiker van de Verduistering** ](https://sling.apache.org/documentation/development/ide-tooling.html), begeleidt deze documentatie u door de algemene concepten, serverintegratie, en plaatsingsmogelijkheden die door de Hulpmiddelen van de Ontwikkeling van de AEM worden gesteund.
* De [ sectie van het Oplossen van problemen ](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting).
* De [ Bekende lijst van kwesties ](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

De volgende officiële [&#128279;](https://www.eclipse.org/) documentatie van de Verduistering  kan helpen aan opstelling uw milieu:

* [ Begonnen het worden met Verduistering ](https://eclipseide.org/getting-started/)
* [ Eclipse Luna Help System ](https://help.eclipse.org/latest/index.jsp)
* [ Gemaakt Integratie (m2eclipse) ](https://www.eclipse.org/m2e/)
