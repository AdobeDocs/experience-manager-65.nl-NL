---
title: Problemen met AEM tijdens het ontwerpen oplossen
description: De volgende sectie behandelt sommige kwesties die u wanneer het gebruiken van AEM zou kunnen ontmoeten, samen met suggesties op hoe te om hen problemen op te lossen.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
exl-id: 27a6b012-576e-40bc-9b50-c310b3c56c9e
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '429'
ht-degree: 0%

---

# Problemen met AEM bij ontwerpen oplossen{#troubleshooting-aem-when-authoring}

De volgende sectie behandelt sommige kwesties die u wanneer het gebruiken van AEM zou kunnen ontmoeten, samen met suggesties op hoe te om hen problemen op te lossen.

>[!NOTE]
>
>Wanneer u problemen ondervindt, is het ook de moeite waard om de lijst met [Bekende problemen](/help/release-notes/release-notes.md) voor uw instantie (release- en servicepacks).

>[!NOTE]
>
>Gebruikers die beheerdersrechten hebben en die problemen met AEM willen oplossen, kunnen de in [AEM voor probleemoplossing (voor beheerders)](/help/sites-administering/troubleshoot.md). Als u niet genoeg voorrechten hebt, zie uw systeembeheerder over het oplossen van AEM.

## Oude paginaversie blijft op gepubliceerde site staan {#old-page-version-still-on-published-site}

* **Probleem**:

   * U hebt wijzigingen aangebracht in een pagina en de pagina gerepliceerd naar de publicatiesite, maar de *oud* Er wordt nog steeds een versie van de pagina weergegeven op de publicatiesite.

* **Reden**:

   * Dit kan verscheidene oorzaken hebben, meestal het geheime voorgeheugen (of uw lokale browser of de Verzender), hoewel het soms een kwestie met de replicatierij kan zijn.

* **Oplossingen**:

   * Hier zijn verschillende mogelijkheden:
   * Controleer of de pagina correct is gerepliceerd. Controleer de paginastatus en, indien nodig, de status van de replicatiewachtrij.
   * Wis de cache in uw lokale browser en open de pagina opnieuw.
   * Toevoegen `?` tot het einde van de pagina-URL. Bijvoorbeeld:

     `http://localhost:4502/sites.html/content?`

     Hiermee wordt de pagina rechtstreeks vanaf AEM aangevraagd en wordt de Dispatcher overgeslagen. Als u de bijgewerkte pagina ontvangt, geeft dit aan dat u de cache van de Dispatcher moet wissen.

   * Neem contact op met uw systeembeheerder als er problemen zijn met de replicatiestijden.

## Sidekick niet zichtbaar {#sidekick-not-visible}

* **Probleem**:

   * Sidekick is niet zichtbaar bij het bewerken van een inhoudspagina in de auteursomgeving.

* **Reden**:

   * In zeldzame gevallen zou u de kopbal van uw hulp buiten het werkingsgebied van uw huidig venster kunnen hebben geplaatst. Dit betekent dat u de positie niet opnieuw kunt wijzigen.

* **Oplossing**:

   * Log uit van uw huidige sessie en meld u opnieuw aan. Sidekick keert terug naar de standaardpositie.

## Zoeken en vervangen - niet alle exemplaren worden vervangen {#find-replace-not-all-instances-are-replaced}

* **Probleem:**

   * Wanneer u de opdracht **Zoeken en vervangen** kan voorkomen dat niet alle instanties van de `find` worden vervangen op een pagina.

* **Reden**:

   * De capaciteit van **Zoeken en vervangen** is afhankelijk van de manier waarop de inhoud wordt opgeslagen en of deze kan worden doorzocht. Een blogtekst wordt bijvoorbeeld opgeslagen in `jcr:text` eigenschap die niet is geconfigureerd om te worden doorzocht. Het standaardwerkingsgebied voor het vondst en vervangt servlet behandelt de volgende eigenschappen:

      * `jcr:title`
      * `jcr:description`
      * `jcr:text`
      * `text`

* **Oplossing**:

   * Deze definities kunnen met de configuratie voor **Day CQ WCM-zoekservice vervangen** met de **Webconsole**; bijvoorbeeld bij

     `http://localhost:4502/system/console/configMgr`
