---
title: Pagina's aanpassen die worden weergegeven door de fouthandler
description: Adobe Experience Manager wordt geleverd met een standaardfouthandler voor de afhandeling van HTTP-fouten.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
exl-id: d6745baa-44da-45dd-b5d5-a9b218e7e8cf
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Pagina&#39;s aanpassen die worden weergegeven door de fouthandler{#customizing-pages-shown-by-the-error-handler}

Adobe Experience Manager (AEM) wordt geleverd met een standaardfouthandler voor de afhandeling van HTTP-fouten, bijvoorbeeld door het volgende weer te geven:

![chlimage_1-67](assets/chlimage_1-67a.png)

Door het systeem verschafte scripts bestaan (onder `/libs/sling/servlet/errorhandler`) om te reageren op foutcodes, standaard is het volgende beschikbaar bij een standaard CQ-instantie:

* 403.jsp
* 404.jsp

>[!NOTE]
>
>AEM is gebaseerd op Apache Sling. Zie als zodanig [Foutafhandeling](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html) voor meer informatie over foutafhandeling bij verkoop.

>[!NOTE]
>
>Voor een instantie van de auteur: [CQ WCM-foutopsporingsfilter](/help/sites-deploying/osgi-configuration-settings.md) is standaard ingeschakeld. Dit resulteert altijd in reactiecode 200. De standaardfoutenmanager antwoordt door het volledige stapelspoor aan de reactie te schrijven.
>
>Voor een publicatie-instantie is het CQ WCM-foutopsporingsfilter *altijd* uitgeschakeld (zelfs als geconfigureerd als ingeschakeld).

## Hoe te om Pagina&#39;s aan te passen die door de Handler van de Fout worden getoond {#how-to-customize-pages-shown-by-the-error-handler}

U kunt uw eigen scripts ontwikkelen om de pagina&#39;s aan te passen die door de fouthandler worden weergegeven wanneer een fout optreedt. Uw aangepaste pagina&#39;s worden gemaakt onder `/apps` en bedekken de standaardpagina&#39;s (die onder `/libs`).

>[!NOTE]
>
>Zie [Bedekkingen gebruiken](/help/sites-developing/overlays.md) voor meer informatie .

1. Kopieer de standaardscripts in de opslagplaats:

   * Van `/libs/sling/servlet/errorhandler/`
   * tot `/apps/sling/servlet/errorhandler/`

   Aangezien het bestemmingspad niet standaard bestaat, moet u het creëren wanneer het doen dit voor het eerst.

1. Navigeren naar `/apps/sling/servlet/errorhandler` en voer een van de volgende handelingen uit:

   * bewerk het juiste bestaande script, zodat u de vereiste informatie kunt opgeven.
   * Maak en bewerk een nieuw script voor de vereiste code.

1. Sla de wijzigingen op en test u deze.

>[!CAUTION]
>
>De handlers 404.jsp en 403.jsp zijn ontworpen om voor authentificatie CQ5 te behandelen; in het bijzonder, om systeemlogin toe te staan als er deze fouten zijn.
>
>Daarom moeten deze twee handlers met grote zorg worden vervangen.

### De reactie op HTTP 500-fouten aanpassen {#customizing-the-response-to-http-errors}

HTTP 500 fouten worden veroorzaakt door server-zijuitzonderingen.

* **[500 Interne serverfout](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)**
De server heeft een onverwachte voorwaarde aangetroffen waardoor deze de aanvraag niet kan uitvoeren.

Wanneer de verzoekverwerking in een uitzondering resulteert, het kader van Apache Sling (dat AEM wordt voortgebouwd op):

* meldt de uitzondering
* retourneert:

   * de HTTP-antwoordcode 500
   * de spoor van de uitzonderingsstapel

  in het lichaam van de reactie.

Door [aanpassen van de pagina&#39;s die worden weergegeven door de fouthandler](#how-to-customize-pages-shown-by-the-error-handler) a `500.jsp` kan worden gemaakt. Het wordt echter alleen gebruikt als `HttpServletResponse.sendError(500)` wordt uitgevoerd uitdrukkelijk; namelijk van een uitzonderingsvanger.

Anders is de antwoordcode ingesteld op 500, maar wordt de `500.jsp` script niet uitgevoerd.

Als u 500 fouten wilt afhandelen, moet de bestandsnaam van het script van de fouthandler gelijk zijn aan de uitzonderingsklasse (of superklasse). Om al dergelijke uitzonderingen te behandelen, kunt u een manuscript tot stand brengen `/apps/sling/servlet/errorhandler/Throwable.js`p of `/apps/sling/servlet/errorhandler/Exception.jsp`.

>[!CAUTION]
>
>Voor een instantie van de auteur: [CQ WCM-foutopsporingsfilter](/help/sites-deploying/osgi-configuration-settings.md) is standaard ingeschakeld. Dit resulteert altijd in reactiecode 200. De standaardfoutenmanager antwoordt door het volledige stapelspoor aan de reactie te schrijven.
>
>Voor een aangepaste fout-handler zijn reacties met code 500 nodig - dus de [CQ WCM-foutopsporingsfilter moet worden uitgeschakeld](/help/sites-deploying/osgi-configuration-settings.md). Dit zorgt ervoor dat reactiecode 500 is teruggekeerd, die beurtelings de correcte fout-manager van het Sling teweegbrengt.
>
>Voor een publicatie-instantie is het CQ WCM-foutopsporingsfilter *altijd* uitgeschakeld (zelfs als geconfigureerd als ingeschakeld).
