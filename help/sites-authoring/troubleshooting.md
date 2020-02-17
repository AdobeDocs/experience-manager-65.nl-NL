---
title: AEM-probleem bij ontwerpen oplossen
seo-title: AEM-probleem bij ontwerpen oplossen
description: Sommige problemen die u kunt tegenkomen bij het gebruik van AEM
seo-description: Sommige problemen die u kunt tegenkomen bij het gebruik van AEM
uuid: 99af51ea-8628-4811-83f2-ab3f88f0279e
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: da0a5644-2e1d-4394-a6aa-11bb41406ba6
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# AEM-probleem bij ontwerpen oplossen{#troubleshooting-aem-when-authoring}

In de volgende sectie worden enkele problemen beschreven die u kunt tegenkomen bij het gebruik van AEM, samen met suggesties voor het oplossen van problemen met deze problemen.

>[!NOTE]
>
>Wanneer het ervaren van problemen het ook de moeite waard is de lijst van [Bekende Kwesties](/help/release-notes/known-issues.md) voor uw instantie (versie en de dienstpakken) te controleren.

>[!NOTE]
>
>De gebruikers die beheerdervoorrechten hebben, en die problemen met AEM willen oplossen, kunnen de het oplossen van problemenmethodes gebruiken die in het [Oplossen van problemen AEM (voor Beheerders)](/help/sites-administering/troubleshoot.md)worden beschreven. Als u niet voldoende rechten hebt, raadpleegt u uw systeembeheerder over het oplossen van problemen met AEM.

## Oude paginaversie blijft op gepubliceerde site staan {#old-page-version-still-on-published-site}

* **Probleem**:

   * U hebt wijzigingen aangebracht in een pagina en de pagina gekopieerd naar de publicatiesite, maar de *oude* versie van de pagina wordt nog wel weergegeven op de publicatiesite.

* **Reden**:

   * Dit kan verscheidene oorzaken hebben, meestal het geheime voorgeheugen (of uw lokale browser of de Verzender), hoewel het soms een kwestie met de replicatierij kan zijn.

* **Oplossingen**:

   * Hier zijn verschillende mogelijkheden:
   * Controleer of de pagina correct is gerepliceerd. Controleer de paginastatus en, indien nodig, de status van de replicatiewachtrij.
   * Wis de cache in uw lokale browser en open de pagina opnieuw.
   * Toevoegen `?` aan het einde van de pagina-URL. Bijvoorbeeld:

      * `http://localhost:4502/sites.html/content?`
      * Hiermee wordt de pagina rechtstreeks bij AEM aangevraagd en wordt de Dispatcher overgeslagen. Als u de bijgewerkte pagina ontvangt, geeft dit aan dat u de cache van de Dispatcher moet wissen.
   * Neem contact op met uw systeembeheerder als er problemen zijn met de replicatiestijden.


## Componenthandelingen niet zichtbaar op werkbalk {#component-actions-not-visible-on-toolbar}

* **Probleem**:

   * Het volledige bereik van toepasselijke componentacties is niet zichtbaar wanneer u een inhoudspagina bewerkt in de auteursomgeving.

* **Reden**:

   * In zeldzame gevallen kan een eerdere actie gevolgen hebben voor de werkbalk.

* **Oplossing**:

   * Vernieuw de pagina.

