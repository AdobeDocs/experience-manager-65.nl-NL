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

AEM Communities maakt API&#39;s offline beschikbaar voor het beheer van gebruikersprofielen en het bulksgewijs beheren van door gebruikers gegenereerde inhoud (UGC). Wanneer deze optie is ingeschakeld, wordt de **UserUgcManagement** De dienst staat de bevoorrechte gebruikers (communautaire beheerders en moderatoren) toe om gebruikersprofielen onbruikbaar te maken, en bulkschrapping of bulkexport UGC voor specifieke gebruikers. Deze API&#39;s stellen ook de verwerkingsverantwoordelijken en verwerkers van klantgegevens in staat om te voldoen aan de algemene gegevensbeschermingsregels van de Europese Unie (GDPR) en andere op GDPR geïnspireerde privacymandaten.

Zie voor meer informatie de [GDPR-pagina in het Adobe Privacy Center](https://www.adobe.com/privacy/general-data-protection-regulation.html).

>[!NOTE]
>
>Als u [Adobe Analytics in AEM Communities](/help/communities/analytics.md) de vastgelegde gebruikersgegevens naar de Adobe Analytics-server worden verzonden. Adobe Analytics biedt API&#39;s waarmee u gebruikersgegevens kunt openen, exporteren en verwijderen en die voldoen aan GDPR. Zie voor meer informatie [Toegang verzenden en verzoeken verwijderen](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/gdpr-submit-access-delete.html).

Om deze APIs aan gebruik te zetten, moet u toelaten `/services/social/ugcmanagement` eindpunt door de dienst UserUgcManagement te activeren. Als u deze service wilt activeren, installeert u de [voorbeeldservet](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet) beschikbaar op [GitHub.com](https://github.com/Adobe-Marketing-Cloud/aem-communities-ugc-migration/tree/main/bundles/communities-ugc-management-servlet). Dan, slag het eindpunt op publiceer geval van uw communautaire plaats met aangewezen parameters gebruikend een HTTP- verzoek, gelijkend op:

`https://localhost:port/services/social/ugcmanagement?user=<authorizable ID>&operation=<getUgc>`. U kunt echter ook een gebruikersinterface (gebruikersinterface) maken voor het beheer van gebruikersprofielen en door de gebruiker gegenereerde inhoud in het systeem.

Met deze API&#39;s kunnen de volgende functies worden uitgevoerd.

## De UGC van een gebruiker ophalen {#retrieve-the-ugc-of-a-user}

**getUserUgc(ResourceResolver resourceResolver, String user, OutputStream outputStream)** Hiermee kunt u alle UGC van een gebruiker uit het systeem exporteren.

* **user**: Geautoriseerde id van een gebruiker.
* **outputStream**: Resultaat wordt geretourneerd als uitvoerstream. Dit is een ZIP-bestand met daarin de door de gebruiker gegenereerde inhoud (als JSON-bestand) en bijlagen (waaronder afbeeldingen of video&#39;s die door de gebruiker zijn geüpload).

Als u bijvoorbeeld de UGC wilt exporteren van een gebruiker met de naam Weston McCall, die weston.mccall@dodgit.com als geautoriseerde id gebruikt om u aan te melden bij de communitysite, kunt u een http-verzoek verzenden dat lijkt op het volgende:

`https://localhost:port/services/social/ugcmanagement?user=weston.mccall@dodgit.com&operation=getUgc`

## De UGC van een gebruiker verwijderen {#delete-the-ugc-of-a-user}

**deleteUserUgc(ResourceResolver resourceResolver, String user)** helpt u alle UGC voor een gebruiker uit het systeem te verwijderen.

* **user**: Geautoriseerde id van de gebruiker.

Als u bijvoorbeeld de UGC wilt verwijderen van een gebruiker met de machtigbare id weston.mccall@dodgit.com via de HTTP-POST-aanvraag, gebruikt u de volgende parameters:

* user = `weston.mccall@dodgit.com`
* operation = `deleteUgc`

### UGC verwijderen uit Adobe Analytics {#delete-ugc-from-adobe-analytics}

Als u gebruikersgegevens uit de Adobe Analytics wilt verwijderen, volgt u de opdracht [Workflow voor GDPR-analyse](https://experienceleague.adobe.com/docs/analytics/admin/data-governance/an-gdpr-workflow.html); aangezien de API geen gebruikersgegevens van Adobe Analytics verwijdert.

Raadpleeg de volgende afbeelding voor Adobe Analytics-variabeletoewijzingen die AEM Communities gebruikt:

![AEM gemeenschappen variabele mapping voor Adobe Analytics](assets/analytics-communities-mapping.png)

## Gebruikersaccount uitschakelen {#disable-a-user-account}

**deleteUserAccount(ResourceResolver resourceResolver, String user)** Hiermee kunt u een gebruikersaccount uitschakelen.

* **user**: Geautoriseerde id van de gebruiker.

>[!NOTE]
>
>Als een gebruiker wordt uitgeschakeld, wordt alle door de gebruiker gegenereerde inhoud op de server verwijderd.

Bijvoorbeeld om het profiel van een gebruiker te schrappen die erkende identiteitskaart heeft `weston.mccall@dodgit.com` door HTTP-POST verzoek, gebruik de volgende parameters:

* user = `weston.mccall@dodgit.com`
* operation = `deleteUser`

>[!NOTE]
>
>deleteUserAccount()-API schakelt alleen een gebruikersprofiel in het systeem uit en verwijdert de UGC. Als u echter een gebruikersprofiel van het systeem wilt verwijderen, navigeert u naar **CRXDE Lite**: [https://&lt;server>/crx/de](https://localhost:4502/crx/de), zoek het gebruikersknooppunt en verwijder het.
