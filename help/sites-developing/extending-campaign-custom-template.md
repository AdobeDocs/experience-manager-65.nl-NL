---
title: Aangepaste AEM paginasjabloon maken met Adobe Campaign-formuliercomponenten
seo-title: Aangepaste AEM paginasjabloon maken met Adobe Campaign-formuliercomponenten
description: Een aangepaste paginasjabloon maken waarin Adobe Campaign-formuliercomponenten worden gebruikt
seo-description: Een aangepaste paginasjabloon maken waarin Adobe Campaign-formuliercomponenten worden gebruikt
uuid: 8162ace2-b661-4c39-b0fb-288e1c035b9c
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: c3f6eed4-bbda-454a-88ce-c7f2041d4217
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---


# Aangepaste AEM paginasjabloon maken met Adobe Campaign-formuliercomponenten{#creating-custom-aem-page-template-with-adobe-campaign-form-components}

Deze pagina verklaart hoe te om een malplaatje van de douanepagina te bouwen dat [Adobe Campaign Form](/help/sites-authoring/adobe-campaign-components.md) componenten gebruikt door te onderzoeken hoe het Geometrixx-outdoor malplaatje ( `/apps/geometrixx-outdoors/components/page_campaign_profile`) wordt uitgevoerd, en wijst u op belangrijke informatie u kan vereisen wanneer het creëren van uw eigen douanemalplaatje.

>[!NOTE]
>
>[E-mail- en formuliervoorbeelden zijn alleen beschikbaar in Geometrixx](/help/sites-developing/we-retail.md). Download voorbeeldinhoud van Geometrixx uit Pakket delen.

Als u een aangepaste AEM paginasjabloon wilt maken met Adobe Campaign-formuliercomponenten, moet u het volgende doen:

1. **Correcte resourceSuperType**

   Zorg ervoor dat de pagina-component overerft van `mcm/campaign/components/profile`.

   Dit is vereist voor de servlets om informatie te verkrijgen en op te slaan

   * `com.day.cq.mcm.campaign.servlets.TemplateListServlet`
   * `com.day.cq.mcm.campaign.servlets.SaveProfileServlet`

   ![chlimage_1-201](assets/chlimage_1-201.png)

1. **ClientContext-instellingen**

   Wanneer u de montages van de cliëntcontext ( `/etc/designs/geometrixx-outdoors/jcr:content/page_campaign_profile`) bekijkt, ziet u de volgende montages:

   * ClientContext verwijst naar `/etc/clientcontext/campaign`
   * Er is ook een extra *config* knoop.

   ![chlimage_1-202](assets/chlimage_1-202.png)

1. **head.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/head.jsp)**

   In **head.jsp**, ziet u de volgende lijnen die **clientcontext-config** en **cloudservice-haak** gebruiken:

   ```
   <cq:include path="config" resourceType="cq/personalization/components/clientcontext_optimized/config"/>
   <sling:include path="contexthub" resourceType="granite/contexthub/components/contexthub"/>
   <cq:include script="/libs/cq/cloudserviceconfigs/components/servicelibs/servicelibs.jsp"/>
   ```

1. **body.jsp (/apps/geometrixx-outdoors/components/page_campaign_profile/body.jsp)**

   In **body.jsp** worden de cloudservices onder aan de pagina geladen:

   ```
   <cq:include path="cloudservices" resourceType="cq/cloudserviceconfigs/components/servicecomponents"/>
   ```

1. **Campagnepagina-eigenschappen**

   Als u een Adobe Campaign-sjabloon wilt selecteren, worden de pagina-eigenschappen uitgebreid met het tabblad **Campagne**:

   `/apps/geometrixx-outdoors/components/page_campaign_profile/dialog/items/tabs/items/campaign`

   ![chlimage_1-203](assets/chlimage_1-203.png)

1. **Sjablooninstellingen**.

   In het malplaatje ( `/apps/geometrixx-outdoors/templates/campaign_profile/jcr:content`) ziet u de volgende standaardwaarden:

   | **acMapping** | mapRecipient (voor Adobe Campaign 6.1), profiel (voor Adobe Campaign Standard) |
   |---|---|
   | **acTemplateId** | post |

   ![chlimage_1-204](assets/chlimage_1-204.png)

