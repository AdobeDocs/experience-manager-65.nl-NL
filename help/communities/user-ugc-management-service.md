---
title: Gebruikers- en UGC-beheerservice in AEM Communities
description: Gebruik API's om door gebruikers gegenereerde inhoud in bulk te verwijderen en te exporteren en gebruikersaccount uit te schakelen.
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
docset: aem65
role: Admin
exl-id: 526ef0fa-3f20-4de4-8bc5-f435c60df0d0
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Gebruikers- en UGC-beheerservice in AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy, zoals GDPR, CCPA, enzovoort.

AEM Communities maakt API&#39;s offline beschikbaar voor het beheer van gebruikersprofielen en het bulksgewijs beheren van door gebruikers gegenereerde inhoud (UGC). Zodra toegelaten, staat de **** dienst UserUgcManagement de bevoorrechte gebruikers (communautaire beheerders en moderatoren) toe om gebruikersprofielen onbruikbaar te maken, en bulkschrapping of bulkuitvoer UGC voor specifieke gebruikers. Deze API&#39;s stellen ook de verwerkingsverantwoordelijken en verwerkers van klantgegevens in staat om te voldoen aan de algemene gegevensbeschermingsregels van de Europese Unie (GDPR) en andere op GDPR geïnspireerde privacymandaten.

Voor verdere informatie zie de [ pagina GDPR bij het Centrum van de Privacy van de Adobe ](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Als u [ Adobe Analytics in AEM Communities ](/help/communities/analytics.md) plaats vormde, wordt het gevangen gebruikersgegeven verzonden naar de server van Adobe Analytics. Adobe Analytics biedt API&#39;s waarmee u gebruikersgegevens kunt openen, exporteren en verwijderen en die voldoen aan GDPR. Voor meer informatie, zie [ Verzoeken van de Toegang voorleggen en van de Schrapping ](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Om deze APIs aan gebruik te zetten, moet u het `/services/social/ugcmanagement` eindpunt toelaten door de dienst te activeren UserUgcManagement. Om deze dienst te activeren, installeer [ steekproefservlet ](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) beschikbaar op [ GitHub.com ](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Dan, slag het eindpunt op publiceer geval van uw communautaire plaats met aangewezen parameters gebruikend een HTTP- verzoek, gelijkend op:

`https://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation=<getUgc>`. U kunt echter ook een gebruikersinterface (gebruikersinterface) maken voor het beheer van gebruikersprofielen en door de gebruiker gegenereerde inhoud in het systeem.

Met deze API&#39;s kunnen de volgende functies worden uitgevoerd.

## De UGC van een gebruiker ophalen {#retrieve-the-ugc-of-a-user}

**getUserUgc (ResourceResolver resourceResolver, de gebruiker van het Koord, OutputStream outputStream)** hulp voert al UGC van een gebruiker uit het systeem uit.

* **gebruiker**: Vergunning identiteitskaart van een gebruiker.
* **outputStream**: Het resultaat is teruggekeerd als outputstroom, die een zip dossier met inbegrip van de gebruiker geproduceerde inhoud (als jsdossier) en gehechtheid (die beelden of video&#39;s omvatten die door de gebruiker worden geupload) is.

Als u bijvoorbeeld de UGC wilt exporteren van een gebruiker met de naam Weston McCall, die weston.mccall@dodgit.com als geautoriseerde id gebruikt om u aan te melden bij de communitysite, kunt u een http-verzoek verzenden dat lijkt op het volgende:

`https://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## De UGC van een gebruiker verwijderen {#delete-the-ugc-of-a-user}

**deleteUserUgc (ResourceResolver resourceResolver, de gebruiker van het Koord)** hulp schrapt al UGC voor een gebruiker van het systeem.

* **gebruiker**: Vergunning identiteitskaart van de gebruiker.

Als u bijvoorbeeld de UGC wilt verwijderen van een gebruiker met de machtigbare id weston.mccall@dodgit.com via de HTTP-POST-aanvraag, gebruikt u de volgende parameters:

* user = `weston.mccall@dodgit.com`
* operation = `deleteUgc`

### UGC verwijderen uit Adobe Analytics {#delete-ugc-from-adobe-analytics}

Om gebruikersgegevens van Adobe Analytics te schrappen, volg het [ GDPR Analytics werkschema ](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/an-gdpr-workflow.html); aangezien API gebruikersgegevens van Adobe Analytics niet schrapt.

Raadpleeg de volgende afbeelding voor Adobe Analytics-variabeletoewijzingen die AEM Communities gebruikt:

![ AEM gemeenschappen veranderlijke afbeelding voor Adobe Analytics ](assets/analytics-communities-mapping.png)

## Gebruikersaccount uitschakelen {#disable-a-user-account}

**deleteUserAccount (ResourceResolver resourceResolver, de gebruiker van het Koord)** hulp maakt een gebruikersrekening onbruikbaar.

* **gebruiker**: Vergunning identiteitskaart van de gebruiker.

>[!NOTE]
>
>Als een gebruiker wordt uitgeschakeld, wordt alle door de gebruiker gegenereerde inhoud op de server verwijderd.

Als u bijvoorbeeld het profiel wilt verwijderen van een gebruiker met een autoriseerbare id `weston.mccall@dodgit.com` via een HTTP-POST-aanvraag, gebruikt u de volgende parameters:

* user = `weston.mccall@dodgit.com`
* operation = `deleteUser`

>[!NOTE]
>
>deleteUserAccount()-API schakelt alleen een gebruikersprofiel in het systeem uit en verwijdert de UGC. Nochtans, om een gebruikersprofiel van het systeem te schrappen, navigeer aan **CRXDE Lite**: [ https://&lt;server>/crx/de ](https://localhost:4502/crx/de), bepaal de plaats van de gebruikersknoop en schrap het.
