---
title: Problemen bij het ontwerpen in AEM oplossen
description: Sommige problemen die kunnen optreden bij het gebruik van AEM.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
exl-id: 05586b17-35d4-496e-8f0e-293c755eb066
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '294'
ht-degree: 0%

---

# Problemen met AEM bij ontwerpen oplossen{#troubleshooting-aem-when-authoring}

In de volgende sectie worden enkele problemen beschreven die u kunt tegenkomen bij het gebruik van AEM, samen met suggesties voor het oplossen van problemen met deze problemen.

>[!NOTE]
>
>Wanneer het ervaren van problemen het ook de moeite waard is controlerend de lijst van [ Bekende Kwesties ](/help/release-notes/release-notes.md) voor uw instantie (versie en de dienstpakken).

>[!NOTE]
>
>De gebruikers die beheerdervoorrechten hebben, en die problemen met AEM willen problemen oplossen, kunnen de het oplossen van problemenmethodes gebruiken die in [ worden beschreven het Oplossen van problemen AEM (voor Beheerders) ](/help/sites-administering/troubleshoot.md). Als u niet voldoende rechten hebt, raadpleegt u de systeembeheerder over het oplossen van problemen met AEM.

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
      * Hiermee wordt de pagina direct bij AEM aangevraagd en wordt de Dispatcher overgeslagen. Als u de bijgewerkte pagina ontvangt, geeft dit aan dat u de Dispatcher-cache moet wissen.

   * Neem contact op met uw systeembeheerder als er problemen zijn met de replicatiestijden.

## Componenthandelingen niet zichtbaar op werkbalk {#component-actions-not-visible-on-toolbar}

* **Uitgave**:

   * Het volledige bereik van toepasselijke componentacties is niet zichtbaar wanneer u een inhoudspagina bewerkt in de auteursomgeving.

* **Reden**:

   * In zeldzame gevallen kan een eerdere actie gevolgen hebben voor de werkbalk.

* **Oplossing**:

   * Vernieuw de pagina.
