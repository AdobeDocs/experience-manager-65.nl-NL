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
source-git-commit: 5bd621b14e3bcd21431c1df5629fe4669b14052c
workflow-type: tm+mt
source-wordcount: '1216'
ht-degree: 0%

---


# AEM Developer Tools for Eclipse {#aem-developer-tools-for-eclipse}

![&#x200B; Experience Manager Developer Tools for Eclipse logo &#x200B;](assets/eclipse-logo.png)

## Overzicht {#overview}

_Experience Manager de Hulpmiddelen van de Ontwikkelaar voor Verduistering_ is een stop van de Verduistering die op de [&#x200B; wordt gebaseerd de stop van de Verduistering voor Apache die &#x200B;](https://sling.apache.org/documentation/development/ide-tooling.html) onder Vergunning 2 wordt vrijgegeven Apache.

Het biedt verschillende functies die de ontwikkeling van AEM vereenvoudigen:

* Naadloze integratie met AEM-instanties via Eclipse Server Connector
* Synchronisatie voor zowel inhoud als OSGi-bundels
* Ondersteuning voor foutopsporing met functie voor hot-swapping van code
* Eenvoudige Bootstrap van AEM-projecten via een specifieke wizard voor het maken van projecten
* Eenvoudig bewerken van JCR-eigenschappen

## Vereisten {#requirements}

Voordat u de AEM Developer Tools kunt gebruiken, moet u:

* De download en installeert [&#x200B; winde van de Verduistering voor Onderneming Java en de Ontwikkelaars van het Web.](https://www.eclipse.org/downloads/packages/)
   * Versie 1.4.0 van de AEM Developer Tools for Eclipse is compatibel met Eclipse 2022-12 (4.26) of hoger en vereist dat Java 17 of hoger wordt uitgevoerd.
* Vorm uw installatie van de Verduistering om ervoor te zorgen dat u minstens 1 GB van heapgeheugen door uw `eclipse.ini` configuratiedossier zoals die in [&#x200B; wordt beschreven Veelgestelde vragen van de Verduistering hebt.](https://wiki.eclipse.org/FAQ_How_do_I_increase_the_heap_size_available_to_Eclipse%3F)

>[!NOTE]
>
>Op macOS, moet u **Eclipse.app** met de rechtermuisknop aanklikken, en dan selecteren **toont de Inhoud van het Pakket** om uw `eclipse.ini` te vinden.

## AEM Developer Tools for Eclipse installeren {#how-to-install-the-aem-developer-tools-for-eclipse}

Wanneer u aan de [&#x200B; vereisten &#x200B;](#requirements) hierboven hebt voldaan, kunt u de stop van ontwikkelaarshulpmiddelen als volgt installeren:

1. Open de [&#x200B; Website van de Hulpmiddelen van de Ontwikkelaar van AEM.](https://eclipse.adobe.com/)

1. Kopieer de **Verbinding van de Installatie**.

   * U kunt ook een archief downloaden in plaats van de installatiekoppeling te gebruiken.
   * Deze methode staat offlineinstallatie toe maar u ontvangt geen automatische updatedeclaraties.

1. In Verduistering, open het **menu van de Hulp**.
1. Klik **installeer Nieuwe Software**.
1. Klik **toevoegen...**.
1. Op het **gebied van de Naam**, ga `AEM Developer Tools` in.
1. Op het **gebied van de Plaats**, kopieer de installatie URL.
1. Klik **toevoegen**.
1. Controle zowel **AEM** als **het Verdelen** stoppen.
1. Klik op **Next**.
1. In het **installeer Details** venster, herzie de te installeren punten en klik **daarna** opnieuw.
1. Accepteer de vergunningsovereenkomsten en klik **Afwerking**.
1. In de **dialoog van de Autoriteiten van het Vertrouwen** die verschijnt, selecteer het gezag/de plaats `https://eclipse.adobe.com` en klik **Geselecteerd Vertrouwen**.
1. In de **dialoog van het Vertrouwen** die verschijnt, selecteer de codeondertekenaars en klik **Geselecteerd Vertrouwen**.
1. Klik **RestartNow** om Eclipse opnieuw te beginnen.

## Het AEM-perspectief {#the-aem-perspective}

In Verduistering, bepaalt het a **Perspectief** de acties en de meningen beschikbaar binnen een venster en laat taakgerichte interactie met middelen in Verduistering toe. Voor meer details over vooruitzichten, zie de [&#x200B; documentatie van de Verduistering.](https://help.eclipse.org/latest/index.jsp).

De _Hulpmiddelen van de Ontwikkeling van Experience Manager voor Verduistering_ verstrekken een perspectief van AEM dat u volledige controle over uw projecten en instanties van AEM aanbiedt. Het AEM-perspectief openen:

1. Van de het menubar van de Verduistering, uitgezocht **Venster** Perspectief **>** Open Perspectief **>** Andere **.**
1. Selecteer **AEM** in de dialoog en klik **Open**.

![&#x200B; het perspectief van AEM in Verduistering &#x200B;](assets/eclipse-aem-perspective.png)

## Monster nemen van meermoduleproject {#sample-multi-module-project}

De _Hulpmiddelen van de Ontwikkelaar van Experience Manager voor Verduistering_ komen met een steekproef multi-moduleproject dat u snel met een projectopstelling in Verduistering helpt omhoog krijgen. Het dient ook als best-practice gids aan verscheidene eigenschappen van AEM, leveraging het [&#x200B; Archetype van het Project van AEM.](https://github.com/adobe/aem-project-archetype)

Ga als volgt te werk om het voorbeeldproject te maken:

1. In het **Dossier** > **Nieuw** > **het menu van het Project**, doorblader aan de **sectie van AEM** en selecteer **de Steekproef van AEM Multi-Module Project**.

   ![&#x200B; de Steekproef van AEM Multi-Module Project &#x200B;](assets/aem-sample-project.png)

1. Klik op **Next**.

   >[!NOTE]
   >
   >Deze stap zou een ogenblik kunnen nemen omdat [&#x200B; m2eclipse &#x200B;](https://eclipse.dev/m2e/) de archetype catalogi moet aftasten.

1. `com.adobe.aem : aem-project-archetype : <highest-number>` zou automatisch in **Archetype** drop-down moeten worden geselecteerd. Selecteer desgewenst een vorige versie. Klik op **Next**.

   ![&#x200B; Uitgezochte archetype versie &#x200B;](assets/select-archetype.png)

1. Geef de volgende velden op voor het voorbeeldproject:

   * **Naam**
   * **Identiteitskaart van de Groep**
   * **Artefact identiteitskaart**
   * **appId** - u kunt de **Geavanceerde** opties moeten uitbreiden om deze waarde te plaatsen.
   * **appTitle** - u kunt de **Geavanceerde** opties moeten uitbreiden om deze waarde te plaatsen.
   * **Pakket** - u kunt de **Geavanceerde** opties moeten uitbreiden om deze waarde te plaatsen.

   ![&#x200B; bepaalt archetype eigenschappen &#x200B;](assets/archetype-properties.png)

1. Klik op **Next**.

1. Vorm een server van AEM waaraan de Verduistering door **de nieuwe server van de Opstelling te selecteren** verbindt en een servernaam en de noodzakelijke verbindingsdetails te verstrekken.

   ![&#x200B; verbind met de server van AEM &#x200B;](assets/connect-server.png)

   * Als u de functie voor foutopsporing wilt gebruiken, moet u AEM starten in de foutopsporingsmodus door de parameter `-agentlib` op te geven, bijvoorbeeld:

   ```text
   $ java -agentlib:jdwp=transport=dt_socket,server=y,suspend=n,address=*:5005 -jar aem-author-p4502.jar
   ```

   >[!TIP]
   >
   >Voor meer details bij het zuiveren van uw project dat op lokale AEM SDK loopt, gelieve het document [&#x200B; Verre het zuiveren van AEM SDK te zien.](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/debugging/debugging-aem-sdk/remote-debugging)

1. Klik **Afwerking**.

De projectstructuur wordt gemaakt. Het kan even duren om de noodzakelijke artefacten aan het project te downloaden.

>[!NOTE]
>
>Op een nieuwe installatie of wanneer de Geweven gebiedsdelen niet eerder zijn gedownload, kan Eclipse melden dat het project met fouten werd gecreeerd. In dit geval, volg de procedure die in de sectie [&#x200B; wordt beschreven het Oplossen van Ongeldige Definitie van het Project.](#resolving-invalid-project-definition)

## Bestaande projecten importeren {#how-to-import-existing-projects}

Gebruik de **Nieuwe eigenschap van het Project** om de basisprojectstructuur tot stand te brengen.

1. Volg de instructies om a [&#x200B; Monster te creëren Multi-Module Project, &#x200B;](#sample-multi-module-project) dat tot een basisprojectstructuur met een gezonde scheiding van zorgen leidt:

   * `PROJECT.ui.apps` voor `/apps` en `/etc` inhoud
   * `PROJECT.ui.content` for `/content` dat is gemaakt
   * `PROJECT.core` voor Java-pakketten
   * `PROJECT.it.launcher` en `PROJECT.it.tests` voor integratietests

1. Vervang de inhoud van het `PROJECT.ui.apps` -project door de mappen `apps` en `etc` van het pakket:

   1. In het **paneel van de Ontdekkingsreiziger van het Project**, breid `PROJECT.ui.apps` > `src` > `main` > `content` > `jcr_root` > `apps` uit.
   1. Klik met de rechtermuisknop op de `apps` omslag en kies **Tonen in** > **Ontdekkingsreiziger van het Systeem**.
   1. Verwijder de mappen `apps` en `etc` .
   1. Plaats de mappen `apps` en `etc` van het inhoudspakket op dezelfde locatie.
   1. In Verduistering, klik het `PROJECT.ui.apps` project met de rechtermuisknop aan en kies **verfrissen**.

1. Doe dan het zelfde voor `PROJECT.ui.content` en vervang zijn inhoudsomslag met één van uw pakketten:

   1. In het **paneel van de Ontdekkingsreiziger van het Project**, breid `PROJECT.ui.content` > `src` > `main` > `content` > `jcr_root` > `content` uit.
   1. Klik de diepere inhoudsomslag met de rechtermuisknop aan en kies **Tonen in** > **Ontdekkingsreiziger van het Systeem**.
   1. Verwijder de inhoudsmap daar.
   1. Plaats de inhoudsmap van het inhoudspakket op dezelfde locatie.
   1. In Verduistering, klik het `PROJECT.ui.content` project met de rechtermuisknop aan en kies **verfrissen**.

1. Werk de `filter.xml` bestanden van deze twee projecten bij zodat ze overeenkomen met de inhoud van het inhoudspakket door het `META-INF/vault/filter.xml` -bestand van het inhoudspakket te openen in een aparte tekst-/code-editor.

   * Dit is een voorbeeld van hoe uw `filter.xml` -bestand eruit kan zien:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <workspaceFilter version="1.0">
       <filter root="/apps/foo"/>
       <filter root="/apps/foundation/components/bar"/>
       <filter root="/etc/designs/foo"/>
       <filter root="/content/foo"/>
       <filter root="/content/dam/foo"/>
       <filter root="/content/usergenerated/content/foo"/>
   </workspaceFilter>
   ```

1. Wat de inhoud van het pakket betreft dat in twee projecten is gesplitst, moet u deze filterregels ook in twee splitsen en de `filter.xml` -bestanden van de twee projecten dienovereenkomstig bijwerken.

   1. Open `PROJECT.ui.apps/src/main/content/META-INF/filter.xml` in Eclipse.
   1. Vervang de inhoud van het element `<workspaceFilter>` door de regels van het pakket die beginnen met `/apps` en `/etc`
      * Bijvoorbeeld:

        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <workspaceFilter version="1.0">
           <filter root="/apps/foo"/>
           <filter root="/apps/foundation/components/bar"/>
           <filter root="/etc/designs/foo"/>
        </workspaceFilter>
        ```

   1. Open vervolgens `PROJECT.ui.content/src/main/content/META-INF/filter.xml` .
   1. Vervang de regels door de regels in het pakket die beginnen met `/content` .
      * Bijvoorbeeld:

        ```xml
        <?xml version="1.0" encoding="UTF-8"?>
        <workspaceFilter version="1.0">
           <filter root="/content/foo"/>
           <filter root="/content/dam/foo"/>
           <filter root="/content/usergenerated/content/foo"/>
        </workspaceFilter>
        ```

1. Zorg ervoor dat u al uw wijzigingen opslaat. U kunt deze nieuwe inhoud nu synchroniseren met uw AEM-exemplaar.

1. In het **paneel van Servers**, zorg ervoor dat uw verbinding is begonnen, en als, niet het begint.

1. Klik **Schoon en publiceer** pictogram.

Als u klaar bent, moet het pakket op uw exemplaar worden uitgevoerd. Bij het opslaan worden wijzigingen automatisch gesynchroniseerd met de instantie.

Als u een pakket uit uw project wilt re-bouwen, klik `PROJECT.ui.apps` of `PROJECT.ui.content` met de rechtermuisknop aan en kies **Looppas zoals** > **Gemaakt installeert**.

Er is nu een doelmap gemaakt met de pakketmap in die map (bijvoorbeeld `PROJECT.ui.apps-0.0.1-SNAPSHOT.zip` genoemd).

## Problemen oplossen {#troubleshooting}

### Ongeldige projectdefinitie oplossen {#resolving-invalid-project-definition}

Om ongeldige gebiedsdelen en projectdefinitie op te lossen ga als volgt te werk:

1. Selecteer alle gemaakte projecten.
1. Klik met de rechtermuisknop.
1. In het contextmenu, uitgezochte **Gemaakt** > **Projecten van de Update**.
1. Controle **de Updates van de Kracht van Momentopname/Versies**.
1. Klik **OK**.

Eclipse downloadt de vereiste afhankelijkheden. Dit kan even duren.

## Meer informatie {#more-information}

Op de officiële Apache Sling IDE-website voor Eclipse vindt u nuttige aanvullende informatie:

* De [**Apache het Verdelen hulpmiddelen van winde voor de Gids van de Gebruiker van de Verduistering** &#x200B;](https://sling.apache.org/documentation/development/ide-tooling.html) begeleidt u door de algemene concepten, serverintegratie, en plaatsingsmogelijkheden die door de Hulpmiddelen van de Ontwikkeling van AEM worden gesteund.
* [&#x200B; het Oplossen van problemen Apache het Verdelen van het hulpmiddel van winde &#x200B;](https://sling.apache.org/documentation/development/ide-tooling.html#troubleshooting)
* [&#x200B; Bekende kwesties lijst &#x200B;](https://sling.apache.org/documentation/development/ide-tooling.html#known-issues)

De volgende officiële [&#x200B; documentatie van de Verduistering &#x200B;](https://www.eclipse.org/) kan helpen aan opstelling uw milieu:

* [&#x200B; Begonnen het worden met Verduistering &#x200B;](https://eclipseide.org/getting-started/)
* [&#x200B; Eclipse Luna Help System &#x200B;](https://help.eclipse.org/latest/index.jsp)
* [&#x200B; Gemaakt Integratie (m2eclipse) &#x200B;](https://www.eclipse.org/m2e/)
