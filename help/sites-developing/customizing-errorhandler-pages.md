---
title: Pagina's aanpassen die worden weergegeven door de fouthandler
seo-title: Pagina's aanpassen die worden weergegeven door de fouthandler
description: AEM wordt geleverd met een standaardfouthandler voor de afhandeling van HTTP-fouten
seo-description: AEM wordt geleverd met een standaardfouthandler voor de afhandeling van HTTP-fouten
uuid: aaf940fd-e428-4c7c-af7f-88b1d02c17c6
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
discoiquuid: 63c94c82-ed96-4d10-b645-227fa3c09f4b
translation-type: tm+mt
source-git-commit: c13eabdf4938a47ddf64d55b00f845199591b835

---


# Pagina&#39;s aanpassen die worden weergegeven door de fouthandler{#customizing-pages-shown-by-the-error-handler}

AEM wordt geleverd met een standaardfouthandler voor de afhandeling van HTTP-fouten; bijvoorbeeld door het volgende weer te geven:

![chlimage_1-67](assets/chlimage_1-67a.png)

Door het systeem verschafte scripts bestaan (onder `/libs/sling/servlet/errorhandler`) om te reageren op foutcodes. Standaard zijn de volgende scripts beschikbaar met een standaard CQ-instantie:

* 403,jsp
* 404,jsp

>[!NOTE]
>
>AEM is gebaseerd op Apache Sling. Raadpleeg [https://sling.apache.org/site/errorhandling.html](https://sling.apache.org/site/errorhandling.html) voor meer informatie over foutafhandeling bij verkoop.

>[!NOTE]
>
>Voor een auteurinstantie, [wordt CQ WCM Debug Filter](/help/sites-deploying/osgi-configuration-settings.md) toegelaten door gebrek. Dit resulteert altijd in reactiecode 200. De standaardfoutenmanager antwoordt door het volledige stapelspoor aan de reactie te schrijven.
>
>Op een publicatie-instantie is het CQ WCM-foutopsporingsfilter *altijd* uitgeschakeld (zelfs als dit is geconfigureerd als ingeschakeld).

## Hoe te om Pagina&#39;s aan te passen die door de Handler van de Fout worden getoond {#how-to-customize-pages-shown-by-the-error-handler}

U kunt uw eigen scripts ontwikkelen om de pagina&#39;s aan te passen die door de fouthandler worden weergegeven wanneer een fout optreedt. De aangepaste pagina&#39;s worden gemaakt onder `/apps` en bedekken de standaardpagina&#39;s (die onder `/libs`) liggen.

>[!NOTE]
>
>Zie Bedekkingen [gebruiken](/help/sites-developing/overlays.md) voor meer informatie.

1. Kopieer het standaardscript of de standaardscripts in de gegevensopslagruimte:

   * from `/libs/sling/servlet/errorhandler/`
   * to `/apps/sling/servlet/errorhandler/`
   Aangezien het bestemmingspad niet standaard bestaat, zult u het moeten tot stand brengen wanneer het doen van dit voor het eerst.

1. Navigeer naar `/apps/sling/servlet/errorhandler`. Hier kunt u:

   * bewerk het juiste bestaande script om de vereiste informatie op te geven.
   * Maak en bewerk een nieuw script voor de vereiste code.

1. Sla de wijzigingen op en test u deze.

>[!CAUTION]
>
>De handlers 404.jsp en 403.jsp zijn specifiek ontworpen om voor authentificatie CQ5 te behandelen; met name om systeemaanmelding mogelijk te maken in het geval van deze fouten.
>
>Daarom moeten deze twee handlers met grote zorg worden vervangen.

### De reactie op HTTP 500-fouten aanpassen {#customizing-the-response-to-http-errors}

HTTP 500-fouten worden veroorzaakt door uitzonderingen aan de serverzijde.

* **[500 Interne serverfout](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)**De server heeft een onverwachte voorwaarde aangetroffen waardoor deze de aanvraag niet kon uitvoeren.

Wanneer de verzoekverwerking in een uitzondering resulteert, het kader Apache Sling (dat AEM wordt voortgebouwd):

* meldt de uitzondering
* retourneert:

   * de HTTP-antwoordcode 500
   * de spoor van de uitzonderingsstapel
   in het lichaam van de respons.

Door de pagina&#39;s aan te [passen die door de foutenmanager](#how-to-customize-pages-shown-by-the-error-handler) worden getoond, kan een `500.jsp` manuscript worden gecreeerd. Deze wordt echter alleen gebruikt als `HttpServletResponse.sendError(500)` deze expliciet wordt uitgevoerd; d.w.z. van een uitzonderingscatcher.

Anders is de antwoordcode ingesteld op 500, maar wordt het `500.jsp` script niet uitgevoerd.

Als u 500 fouten wilt afhandelen, moet de bestandsnaam van het script van de fouthandler gelijk zijn aan de uitzonderingsklasse (of superklasse). Om al dergelijke uitzonderingen te behandelen kunt u een manuscript `/apps/sling/servlet/errorhandler/Throwable.js`p of `/apps/sling/servlet/errorhandler/Exception.jsp`tot stand brengen.

>[!CAUTION]
>
>Voor een auteurinstantie, [wordt CQ WCM Debug Filter](/help/sites-deploying/osgi-configuration-settings.md) toegelaten door gebrek. Dit resulteert altijd in reactiecode 200. De standaardfoutenmanager antwoordt door het volledige stapelspoor aan de reactie te schrijven.
>
>Voor een aangepaste fout-manager, zijn de reacties met code 500 nodig - zodat moet het filter [van de Foutopsporing CQ WCM worden onbruikbaar gemaakt](/help/sites-deploying/osgi-configuration-settings.md). Dit zorgt ervoor dat reactiecode 500 is teruggekeerd, die beurtelings de correcte fout-manager van het Sling teweegbrengt.
>
>Op een publicatie-instantie is het CQ WCM-foutopsporingsfilter *altijd* uitgeschakeld (zelfs als dit is geconfigureerd als ingeschakeld).

