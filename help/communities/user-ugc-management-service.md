---
title: Gebruikersbeheer en UGC-beheerservice in AEM Communities
seo-title: Gebruikersbeheer en UGC-beheerservice in AEM Communities
description: Gebruik API's om door gebruikers gegenereerde inhoud in bulk te verwijderen en te exporteren en gebruikersaccount uit te schakelen.
seo-description: Gebruik API's om door gebruikers gegenereerde inhoud in bulk te verwijderen en te exporteren en gebruikersaccount uit te schakelen.
uuid: 91180659-617d-4f6c-9a07-e680770d0d8f
contentOwner: mgulati
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
discoiquuid: d305821d-1371-4e4a-8b28-8eee8fafa43b
docset: aem65
translation-type: tm+mt
source-git-commit: 18f401babef4cb2aad47e6e4cbb0500b0f8365e2
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---


# Gebruikersbeheer en UGC-beheerservice in AEM Communities {#user-and-ugc-management-service-in-aem-communities}

>[!IMPORTANT]
>
>GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy; zoals GDPR, CCPA enz.


AEM Communities maakt API&#39;s offline beschikbaar voor het beheer van gebruikersprofielen en het bulksgewijs beheren van door gebruikers gegenereerde inhoud (UGC). Zodra toegelaten, staat de dienst **UserUgcManagement** de bevoorrechte gebruikers (communautaire beheerders en moderatoren) toe om gebruikersprofielen onbruikbaar te maken, en bulkschrapping of bulkuitvoer UGC voor specifieke gebruikers. Deze API&#39;s stellen ook de verwerkingsverantwoordelijken en verwerkers van klantgegevens in staat om te voldoen aan de algemene gegevensbeschermingsregels van de Europese Unie (GDPR) en andere op GDPR geïnspireerde privacymandaten.

Zie de pagina [GDPR in het Adobe Privacy Center](https://www.adobe.com/privacy/general-data-protection-regulation.html)voor meer informatie.

>[!NOTE]
>
>Als u [Adobe Analytics hebt geconfigureerd op de AEM Communities](/help/communities/analytics.md) -site, worden de vastgelegde gebruikersgegevens verzonden naar de Adobe Analytics-server. Adobe Analytics biedt API&#39;s waarmee u toegang hebt tot gebruikersgegevens, deze kunt exporteren en verwijderen en die voldoen aan GDPR. Voor meer informatie, zie [Verzoeken](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/gdpr-submit-access-delete.html)van de Toegang voorleggen en van de Schrapping.


Om deze APIs aan gebruik te zetten, moet u het `/services/social/ugcmanagement` eindpunt toelaten door de dienst te activeren UserUgcManagement. Om deze dienst te activeren, installeer [steekproefservlet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) beschikbaar op [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Dan, slag het eindpunt op publiceer geval van uw communautaire plaats met aangewezen parameters gebruikend een HTTP- verzoek, gelijkend op:

`https://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation=<getUgc>`. U kunt echter ook een gebruikersinterface (gebruikersinterface) maken voor het beheer van gebruikersprofielen en door de gebruiker gegenereerde inhoud in het systeem.

Met deze API&#39;s kunnen de volgende functies worden uitgevoerd.

## De UGC van een gebruiker ophalen {#retrieve-the-ugc-of-a-user}

**getUserUgc (ResourceResolver resourceResolver, String user, OutputStream outputStream)** helpt alle UGC van een gebruiker uit het systeem uitvoeren.

* **gebruiker**: Autoriseerbare id van een gebruiker.
* **outputStream**: Het resultaat wordt geretourneerd als een uitvoerstream. Dit is een ZIP-bestand met daarin de door de gebruiker gegenereerde inhoud (als JSON-bestand) en bijlagen (inclusief afbeeldingen of video&#39;s die door de gebruiker zijn geüpload).

Als u bijvoorbeeld de UGC wilt exporteren van een gebruiker met de naam Weston McCall, die weston.mccall@dodgit.com als geautoriseerde id gebruikt om u aan te melden bij de communitysite, kunt u een http-verzoek verzenden dat lijkt op het volgende:

`https://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## De UGC van een gebruiker verwijderen {#delete-the-ugc-of-a-user}

**deleteUserUgc (ResourceResolver resourceResolver, de gebruiker van het Koord)** helpt schrappen al UGC voor een gebruiker van het systeem.

* **gebruiker**: Autoriseerbare id van de gebruiker.

Als u bijvoorbeeld de UGC wilt verwijderen van een gebruiker met de machtigbare id weston.mccall@dodgit.com via de HTTP-POST-aanvraag, gebruikt u de volgende parameters:

* user = `weston.mccall@dodgit.com`
* operation = `deleteUgc`

### UGC verwijderen uit Adobe Analytics {#delete-ugc-from-adobe-analytics}

Als u gebruikersgegevens uit de Adobe Analytics wilt verwijderen, volgt u de [GDPR Analytics-workflow](https://docs.adobe.com/content/help/en/analytics/admin/data-governance/an-gdpr-workflow.html). omdat de API geen gebruikersgegevens van Adobe Analytics verwijdert.

Raadpleeg de volgende afbeelding voor Adobe Analytics-variabeletoewijzingen die AEM Communities gebruikt:

![AEM gemeenschappen variabele mapping voor Adobe Analytics](assets/analytics-communities-mapping.png)

## Gebruikersaccount uitschakelen {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, String user)** helpt een gebruikersaccount onbruikbaar maken.

* **gebruiker**: Autoriseerbare id van de gebruiker.

>[!NOTE]
>
>Als een gebruiker wordt uitgeschakeld, wordt alle door de gebruiker gegenereerde inhoud op de server verwijderd.


Als u bijvoorbeeld het profiel wilt verwijderen van een gebruiker met een machtigbare id `weston.mccall@dodgit.com` via een HTTP-POST-aanvraag, gebruikt u de volgende parameters:

* user = `weston.mccall@dodgit.com`
* operation = `deleteUser`

>[!NOTE]
>
>deleteUserAccount()-API schakelt alleen een gebruikersprofiel in het systeem uit en verwijdert de UGC. Als u echter een gebruikersprofiel van het systeem wilt verwijderen, navigeert u naar **CRXDE Lite**: [https://&lt;server>/crx/de](https://localhost:4502/crx/de), zoek het gebruikersknooppunt en verwijder het.


