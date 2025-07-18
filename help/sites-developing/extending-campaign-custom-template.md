---
title: Aangepaste AEM-paginasjabloon maken met Adobe Campaign-formuliercomponenten
description: Een aangepaste paginasjabloon maken waarin Adobe Campaign-formuliercomponenten worden gebruikt
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: de5c634a-c0d7-4e69-b941-d2fbfe83117d
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
index: false
source-git-commit: 389d5fa8de320a7237fc8290992a33743b15db99
workflow-type: tm+mt
source-wordcount: '297'
ht-degree: 0%

---


# Aangepaste AEM-paginasjabloon maken met Adobe Campaign-formuliercomponenten{#creating-custom-aem-page-template-with-adobe-campaign-form-components}

Deze pagina verklaart hoe te om een malplaatje van de douanepagina te bouwen dat [ componenten gebruikt van de Vorm van 0} Adobe Campaign door te onderzoeken hoe het malplaatje Geometrixx-outdoor (](/help/sites-authoring/adobe-campaign-components.md)) wordt uitgevoerd, en richt u aan belangrijke informatie u kunt nodig hebben wanneer het creëren van uw eigen douanemalplaatje.`/apps/geometrixx-outdoors/components/page_campaign_profile`

>[!CAUTION]
>
>De e-mailcomponenten van AEM zijn vervangen. Door de aard van e-mail, die inhoud en stijl samenvoegt, worden de e-mailcomponenten die door AEM buiten de doos worden verstrekt van beperkte hergebruik voor klanten wegens de behoefte om douanestijlen in om het even welke componenten uit te voeren die voor projecten worden vereist.
>
>E-mailcomponenten kunnen op projectniveau worden geïmplementeerd en de verouderde AEM-e-mailcomponenten laten zien hoe dat kan worden bereikt. Gebruik deze vervangen componenten echter niet voor projecten.


Als u een aangepaste AEM-paginasjabloon wilt maken met Adobe Campaign-formuliercomponenten, moet u het volgende doen:

1. **Correct resourceSuperType**

   Zorg ervoor dat de pagina-component overerft van `mcm/campaign/components/profile` .

   Dit is vereist voor de servlets om informatie te verkrijgen en op te slaan

   * `com.day.cq.mcm.campaign.servlets.TemplateListServlet`
   * `com.day.cq.mcm.campaign.servlets.SaveProfileServlet`

   ![ chlimage_1-201 ](assets/chlimage_1-201.png)

1. **de Montages van ClientContext**

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
