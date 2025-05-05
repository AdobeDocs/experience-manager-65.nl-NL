---
title: Aangepaste AEM paginasjabloon maken met Adobe Campaign-formuliercomponenten
description: Een aangepaste paginasjabloon maken waarin Adobe Campaign-formuliercomponenten worden gebruikt
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: de5c634a-c0d7-4e69-b941-d2fbfe83117d
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: ad8f849384e58511de97611d1b26c4fc96022062
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Aangepaste AEM paginasjabloon maken met Adobe Campaign-formuliercomponenten{#creating-custom-aem-page-template-with-adobe-campaign-form-components}

Deze pagina verklaart hoe te om een malplaatje van de douanepagina te bouwen dat [&#128279;](/help/sites-authoring/adobe-campaign-components.md) componenten gebruikt van de Vorm van 0&rbrace; Adobe Campaign door te onderzoeken hoe het malplaatje Geometrixx-outdoor (`/apps/geometrixx-outdoors/components/page_campaign_profile`) wordt uitgevoerd, en richt u aan belangrijke informatie u kunt nodig hebben wanneer het creëren van uw eigen douanemalplaatje.

>[!NOTE]
>
>[ E-mail en vormsteekproeven zijn slechts beschikbaar in Geometrixx ](/help/sites-developing/we-retail.md). Download voorbeeldinhoud van het Geometrixx van het Pakket Delen.

>[!CAUTION]
>
>De AEM e-mailcomponenten zijn vervangen. Vanwege de aard van e-mail, waarin inhoud en stijl worden samengevoegd, worden de e-mailcomponenten die door AEM buiten de box worden geleverd van beperkte hergebruik voor klanten omdat aangepaste stijlen moeten worden geïmplementeerd in alle componenten die vereist zijn voor projecten.
>
>E-mailcomponenten kunnen op projectniveau worden geïmplementeerd en de verouderde AEM e-mailcomponenten laten zien hoe dat kan worden bereikt. Gebruik deze vervangen componenten echter niet voor projecten.


Als u een aangepaste AEM paginasjabloon wilt maken met Adobe Campaign-formuliercomponenten, moet u het volgende doen:

1. **Correct resourceSuperType**

   Zorg ervoor dat de pagina-component overerft van `mcm/campaign/components/profile` .

   Dit is vereist voor de servlets om informatie te verkrijgen en op te slaan

   * `com.day.cq.mcm.campaign.servlets.TemplateListServlet`
   * `com.day.cq.mcm.campaign.servlets.SaveProfileServlet`

   ![ chlimage_1-201 ](assets/chlimage_1-201.png)

1. **de Montages van de ClientContext**

   Wanneer u de clientcontext-instellingen ( `/etc/designs/geometrixx-outdoors/jcr:content/page_campaign_profile` ) bekijkt, ziet u de volgende instellingen:

   * ClientContext wijst naar `/etc/clientcontext/campaign`
   * Er is ook een extra *config* knoop.

   ![ chlimage_1-202 ](assets/chlimage_1-202.png)

1. **head.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/head.jsp)**

   In **head.jsp**, ziet u de volgende lijnen die **clientcontext-config** en **cloudservice-haak** gebruiken:

   ```
   <cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub"/>
   <cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
   ```

1. **body.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/body.jsp)**

   In **body.jsp**, worden de wolkendiensten geladen bij de bodem van de pagina:

   ```
   <cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
   ```

1. **de paginaeigenschappen van de Campagne**

   Om een malplaatje van Adobe Campaign te kunnen selecteren worden de pagina-eigenschappen uitgebreid met **Campagne** tabel:

   `/apps/geometrixx-outdoors/components/page_campaign_profile/dialog/items/tabs/items/campaign`

   ![ chlimage_1-203 ](assets/chlimage_1-203.png)

1. **montages van het Malplaatje**.

   In de sjabloon ( `/apps/geometrixx-outdoors/templates/campaign_profile/jcr:content` ) ziet u de volgende standaardwaarden:

   | **acMapping** | mapRecipient (voor Adobe Campaign 6.1), profiel (voor Adobe Campaign Standard) |
   |---|---|
   | **acTemplateId** | post |

   ![ chlimage_1-204 ](assets/chlimage_1-204.png)
