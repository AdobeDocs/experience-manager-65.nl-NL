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
>Wanneer het ervaren van problemen het ook de moeite waard is controlerend de lijst van [&#x200B; Bekende Kwesties &#x200B;](/help/release-notes/release-notes.md) voor uw instantie (versie en de dienstpakken).

>[!NOTE]
>
>De gebruikers die beheerdervoorrechten hebben, en die problemen met AEM willen problemen oplossen, kunnen de het oplossen van problemenmethodes gebruiken die in [&#x200B; AEM van het Oplossen van problemen (voor Beheerders) &#x200B;](/help/sites-administering/troubleshoot.md) worden beschreven. Als u niet genoeg voorrechten hebt, zie uw systeembeheerder over het oplossen van AEM.

## Oude paginaversie blijft op gepubliceerde site staan {#old-page-version-still-on-published-site}

* **Uitgave**:

   * U hebt veranderingen in een pagina aangebracht en de pagina aan publiceren plaats herhaald, maar de *oude* versie van de pagina wordt nog getoond op publiceren plaats.

* **Reden**:

   * Dit kan verschillende oorzaken hebben, meestal het geheime voorgeheugen (of uw lokale browser of Dispatcher), hoewel het soms een kwestie met de replicatierij kan zijn.

* **Oplossingen**:

   * Hier zijn verschillende mogelijkheden:
   * Controleer of de pagina correct is gerepliceerd. Controleer de paginastatus en, indien nodig, de status van de replicatiewachtrij.
   * Wis de cache in uw lokale browser en open de pagina opnieuw.
   * Voeg `?` toe aan het einde van de pagina-URL. Bijvoorbeeld:

     `http://localhost:4502/sites.html/content?`

     Hierdoor wordt de pagina rechtstreeks vanaf AEM aangevraagd en wordt de Dispatcher overgeslagen. Als u de bijgewerkte pagina ontvangt, geeft dit aan dat u de Dispatcher-cache moet wissen.

   * Neem contact op met uw systeembeheerder als er problemen zijn met de replicatiestijden.

## Sidekick niet zichtbaar {#sidekick-not-visible}

* **Uitgave**:

   * Sidekick is niet zichtbaar bij het bewerken van een inhoudspagina in de auteursomgeving.

* **Reden**:

   * In zeldzame gevallen zou u de kopbal van uw hulp buiten het werkingsgebied van uw huidig venster kunnen hebben geplaatst. Dit betekent dat u de positie niet opnieuw kunt wijzigen.

* **Oplossing**:

   * Log uit van uw huidige sessie en meld u opnieuw aan. Sidekick keert terug naar de standaardpositie.

## Zoeken en vervangen - niet alle exemplaren worden vervangen {#find-replace-not-all-instances-are-replaced}

* **Uitgave:**

   * Wanneer het gebruiken van de **Vondst &amp; vervangt** optie het kan gebeuren dat niet alle instanties van de `find` termijn op een pagina worden vervangen.

* **Reden**:

   * Het vermogen van **Vondst &amp; vervangt** hangt van af hoe de inhoud wordt bewaard, en of het kan worden gezocht op. Een blogtekst wordt bijvoorbeeld opgeslagen in de eigenschap `jcr:text` , die niet is geconfigureerd om te worden doorzocht. Het standaardwerkingsgebied voor het vondst en vervangt servlet behandelt de volgende eigenschappen:

      * `jcr:title`
      * `jcr:description`
      * `jcr:text`
      * `text`

* **Oplossing**:

   * Deze definities kunnen met de configuratie voor **Dag CQ WCM vinden vervangen Servlet** gebruikend de **Console van het Web** worden veranderd; bijvoorbeeld, bij

     `http://localhost:4502/system/console/configMgr`
