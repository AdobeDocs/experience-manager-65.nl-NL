---
title: AEM Developer Tools for Eclipse
seo-title: AEM Developer Tools for Eclipse
description: 'null'
seo-description: 'null'
uuid: 566e49f2-6f28-4aa7-bfe0-b5f9675310bf
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: a2ae76a8-50b0-4e43-b791-ad3be25b8582
translation-type: tm+mt
source-git-commit: 6d216e7521432468a01a29ad2879f8708110d970

---


# AEM Developer Tools for Eclipse{#aem-developer-tools-for-eclipse}

![](do-not-localize/chlimage_1-9.png)

## Overzicht {#overview}

De AEM Developer Tools for Eclipse is een Eclipse-plug-in die is gebaseerd op de [Eclipse-plug-in voor Apache Sling](https://sling.apache.org/documentation/development/ide-tooling.html) die is uitgebracht onder de Apache-licentie 2.

Het biedt verschillende functies die AEM-ontwikkeling vereenvoudigen:

* Naadloze integratie met AEM-instanties via Eclipse Server Connector.
* Synchronisatie voor inhoud en OSGI-bundels.
* Ondersteuning voor foutopsporing met de functie voor hot-swapping van code.
* Eenvoudige laarzentrekker van projecten AEM via een specifieke Tovenaar van de Aanmaak van het Project.
* Eenvoudig bewerken van JCR-eigenschappen.

## Vereisten {#requirements}

Voordat u de AEM Developer Tools kunt gebruiken, moet u:

* Download en installeer [Eclipse IDE voor Java EE-ontwikkelaars](https://eclipse.org/downloads/packages/eclipse-ide-java-ee-developers/lunar). AEM Developer Tools biedt momenteel ondersteuning voor Eclipse Kepler of nieuwer

* Kan worden gebruikt met AEM versie 5.6.1 of hoger
* Configureer uw excapse-installatie om ervoor te zorgen dat u ten minste 1 gigabyte heapgeheugen hebt door uw `eclipse.ini` configuratiebestand te bewerken, zoals beschreven in de veelgestelde vragen over [Eclipse](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse%3F).

>[!NOTE]
>
>In MacOS moet u met de rechtermuisknop op **Eclipse.app** klikken en vervolgens **Pakketinhoud** tonen selecteren om uw `eclipse.ini`**.**

## AEM Developer Tools voor Eclipse installeren {#how-to-install-the-aem-developer-tools-for-eclipse}

Nadat u aan de bovenstaande [vereisten](#requirements) hebt voldaan, kunt u de insteekmodule als volgt installeren:

1. Blader door de [**AEM **Developer Tools-website](https://eclipse.adobe.com/aem/dev-tools/).

1. Kopieer de **installatiekoppeling**.

   U kunt ook een archief downloaden in plaats van de installatiekoppeling te gebruiken. Hierdoor kunt u offline installeren, maar op deze manier gaan automatische updatemeldingen verloren.

1. Open het menu **Help** in Eclipse.
1. Klik op **Nieuwe software** installeren.
1. **Klik op** Toevoegen... .
1. Typ in **Naam** AEM Developer Tools.
1. Kopieer de installatie-URL in **Locatie** .
1. Click **Ok**.
1. Controleer zowel **AEM** - als **Sling** -plug-ins.
1. Click **Next**.
1. Click **Next**.
1. Accepteer de lokale overeenkomsten en klik op **Voltooien**.
1. Klik op **Ja** om Eclipse opnieuw te starten.

## Bestaande projecten importeren {#how-to-import-existing-projects}

>[!NOTE]
>
>Zie [Werken met een bundel in Eclipse toen het van AEM](https://stackoverflow.com/questions/29699726/how-to-work-with-a-bundle-in-eclipse-when-it-was-downloaded-from-aem/29705407#29705407)werd gedownload.

## Het AEM-perspectief {#the-aem-perspective}

De hulpmiddelen van de Ontwikkeling AEM voor Eclipse schepen met een Perspectief dat u volledige controle over uw projecten en instanties AEM biedt.

![chlimage_1-2](assets/chlimage_1-2a.jpeg)

## Monster nemen van meermoduleproject {#sample-multi-module-project}

De hulpmiddelen van de Ontwikkelaar AEM voor Eclipse komen met een steekproef, multi-moduleproject dat u snel met een projectopstelling in Verduistering helpt te versnellen, evenals dienst als best-praktijkgids aan verscheidene eigenschappen AEM. [Meer informatie over het Projectarchetype](https://github.com/Adobe-Marketing-Cloud/aem-project-archetype).

Ga als volgt te werk om het voorbeeldproject te maken:

1. Blader in het menu **Bestand** > **Nieuw** > **Project** naar de **sectie AEM** en selecteer **AEM-voorbeeldproject** voor meerdere modules.

   ![chlimage_1-69](assets/chlimage_1-69a.png)

1. Click **Next**.

   >[!NOTE]
   >
   >Deze stap kan even duren omdat m2eclipse de catalogi van archetype moet aftasten.

   ![chlimage_1-70](assets/chlimage_1-70a.png)

1. Kies **com.adobe.granite.archetypes: sample-project-archetype: (hoogste aantal)** van het menu, dan klik **daarna**.

   ![chlimage_1-71](assets/chlimage_1-71a.png)

1. Vul een **Naam**, identiteitskaart **van de** Groep en **Artefactidentiteitskaart** voor het steekproefproject in. U kunt er ook voor kiezen om bepaalde geavanceerde eigenschappen in te stellen.

   ![chlimage_1-72](assets/chlimage_1-72a.png)

1. Vervolgens moet u een AEM-server configureren waarmee Eclipse verbinding maakt.

   Om de debugger eigenschap te gebruiken, moet u AEM op zuivert wijze begonnen zijn - die kan worden bereikt bijvoorbeeld door het volgende aan de bevellijn toe te voegen:

   ```
       -nofork -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=10123
   ```

   ![chlimage_1-73](assets/chlimage_1-73a.png)

1. Click **Finish**. De projectstructuur wordt gemaakt.

   >[!NOTE]
   >
   >Op een nieuwe installatie (meer bepaald: wanneer bepaalde gebiedsdelen nooit zijn gedownload) zou u het project kunnen krijgen dat met fouten wordt gecreeerd. In dit geval volgt u de procedure die wordt beschreven in [Ongeldige projectdefinitie](#resolving-invalid-project-definition)oplossen.

## Problemen oplossen {#troubleshooting}

### Ongeldige projectdefinitie oplossen {#resolving-invalid-project-definition}

Om ongeldige gebiedsdelen en projectdefinitie op te lossen ga als volgt te werk:

1. Selecteer alle gemaakte projecten.
1. Klik met de rechtermuisknop. Selecteer Projecten **** bijwerken in het menu **Maven**.
1. Controleer **de updates van momentopnamen/releases** forceren.
1. Click **OK**. Eclipse probeert de vereiste afhankelijkheden te downloaden.

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

Zorg ervoor dat u de juiste versie voor uw implementatie van AEM toevoegt.

## Meer informatie {#more-information}

Op de officiële Apache Sling IDE-website voor Eclipse vindt u nuttige informatie:

* Met de [**Apache Sling IDE-tooling voor Eclipse **User Guide](https://sling.apache.org/documentation/development/ide-tooling.html), begeleidt deze documentatie u door de algemene concepten, serverintegratie en implementatiemogelijkheden die worden ondersteund door de AEM Development Tools.
* De sectie [](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting)Problemen oplossen.
* De lijst met [bekende problemen](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues).

De volgende officiële [Eclipse](https://eclipse.org/) -documentatie kan u helpen uw omgeving in te stellen:

* [Aan de slag met Eclipse](https://eclipse.org/users/)
* [Help-systeem Eclipse Luna](https://help.eclipse.org/luna/index.jsp)
* [Maven Integration (m2eclipse)](https://www.eclipse.org/m2e/)

