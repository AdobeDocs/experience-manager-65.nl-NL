---
title: Problemen bij het ontwerpen in AEM oplossen
description: Sommige problemen die u bij het gebruik van AEM kunt tegenkomen.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
exl-id: 05586b17-35d4-496e-8f0e-293c755eb066
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '294'
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

      * `http://localhost:4502/sites.html/content?`
      * Hierdoor wordt de pagina rechtstreeks vanaf AEM aangevraagd en wordt de Dispatcher overgeslagen. Als u de bijgewerkte pagina ontvangt, geeft dit aan dat u de Dispatcher-cache moet wissen.

   * Neem contact op met uw systeembeheerder als er problemen zijn met de replicatiestijden.

## Componenthandelingen niet zichtbaar op werkbalk {#component-actions-not-visible-on-toolbar}

* **Uitgave**:

   * Het volledige bereik van toepasselijke componentacties is niet zichtbaar wanneer u een inhoudspagina bewerkt in de auteursomgeving.

* **Reden**:

   * In zeldzame gevallen kan een eerdere actie gevolgen hebben voor de werkbalk.

* **Oplossing**:

   * Vernieuw de pagina.
