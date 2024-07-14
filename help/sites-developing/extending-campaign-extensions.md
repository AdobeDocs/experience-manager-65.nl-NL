---
title: Aangepaste extensies maken
description: Je kunt in Adobe Campaign je aangepaste code bellen van AEM naar Adobe Campaign of van AEM naar.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 0702858e-5e46-451f-9ac3-40a4fec68ca0
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '499'
ht-degree: 0%

---

# Aangepaste extensies maken{#creating-custom-extensions}

Over het algemeen wanneer u een project implementeert, hebt u aangepaste code in zowel AEM als Adobe Campaign. Met het gebruik van de bestaande API kunt u uw aangepaste code in Adobe Campaign aanroepen van AEM of van AEM naar Adobe Campaign. In dit document wordt beschreven hoe u dat doet.

## Vereisten {#prerequisites}

U moet het volgende hebben geïnstalleerd:

* Adobe Experience Manager
* Adobe Campaign 6.1

Zie [ Integrerend AEM met Adobe Campaign 6.1 ](/help/sites-administering/campaignonpremise.md) voor meer informatie.

## Voorbeeld 1: AEM naar Adobe Campaign {#example-aem-to-adobe-campaign}

De standaardintegratie tussen AEM en Campagne is gebaseerd op JSON en JSSP (JavaScript Server Page). Deze JSSP dossiers kunnen in de console van de Campagne worden gevonden, en allen beginnen met **aec** (Adobe Experience Cloud).

![ chlimage_1-15 ](assets/chlimage_1-15a.png)

>[!NOTE]
>
>[ voor dit voorbeeld, zie Geometrixx ](/help/sites-developing/we-retail.md), die van het Aandeel van het Pakket beschikbaar is.

In dit voorbeeld is een nieuw aangepast JSSP-bestand gemaakt en wordt dat vanuit de AEM aangeroepen om het resultaat op te halen. Deze kan bijvoorbeeld worden gebruikt om gegevens op te halen uit Adobe Campaign of om gegevens op te slaan in Adobe Campaign.

1. In Adobe Campaign, om een JSSP dossier tot stand te brengen, klik het **Nieuwe** pictogram.

   ![ het Nieuwe pictogram zoals die door een pagina met een ster dichtbij de upper-left hoek wordt vermeld.](do-not-localize/chlimage_1-4a.png)

1. Voer de naam van dit JSSP-bestand in. In dit voorbeeld, **concentreert:custom.jssp** wordt gebruikt (betekenend is het in **focus** namespace).

   ![ chlimage_1-16 ](assets/chlimage_1-16a.png)

1. Plaats de volgende code in het jssp-bestand:

   ```
   <%
   var origin = request.getParameter("origin");
   document.write("Hello from Adobe Campaign, origin : " + origin);
   %>
   ```

1. Sla uw werk op. Het resterende werk is in AEM.
1. Creeer een eenvoudige servlet op de AEM kant zodat kunt u dit JSSP roepen. In dit voorbeeld kunt u het volgende aannemen:

   * U hebt de verbinding tussen AEM en Campagne
   * De campagnewolkendienst wordt gevormd op **/content/geometrixx-outdoor**

   Het belangrijkste voorwerp in dit voorbeeld is **GenericCampaignConnector**, die u (krijgt en post) jssp- dossiers op de kant van Adobe Campaign laat roepen.

   Hier volgt een klein codefragment:

   ```
   @Reference
   private GenericCampaignConnector campaignConnector;
   ...
   Map<String, String> params = new HashMap<String, String>();
   params.put("origin", "AEM");
   CallResults results = campaignConnector.callGeneric("/jssp/cus/custom.jssp", params, credentials);
   return results.bodyAsString();
   ```

1. In dit voorbeeld, moet u de geloofsbrieven in de vraag overgaan. U kunt ze ophalen met de methode getCredentials(), waarbij u een pagina doorgeeft waarvoor de Campagnewolkenservice is geconfigureerd.

   ```xml
   // page containing the cloudservice for Adobe Campaign
   Configuration config = campaignConnector.getWebserviceConfig(page.getContentResource().getParent());
   CampaignCredentials credentials = campaignConnector.retrieveCredentials(config);
   ```

De volledige code ziet er als volgt uit:

```java
import java.io.IOException;
import java.io.PrintWriter;
import java.util.HashMap;
import java.util.Map;

import javax.servlet.ServletException;

import org.apache.felix.scr.annotations.Reference;
import org.apache.felix.scr.annotations.sling.SlingServlet;
import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.SlingHttpServletResponse;
import org.apache.sling.api.servlets.SlingSafeMethodsServlet;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import com.day.cq.mcm.campaign.CallResults;
import com.day.cq.mcm.campaign.CampaignCredentials;
import com.day.cq.mcm.campaign.GenericCampaignConnector;
import com.day.cq.wcm.api.Page;
import com.day.cq.wcm.api.PageManager;
import com.day.cq.wcm.api.PageManagerFactory;
import com.day.cq.wcm.webservicesupport.Configuration;

@SlingServlet(paths="/bin/campaign", methods="GET")
public class CustomServlet extends SlingSafeMethodsServlet {

 private final Logger log = LoggerFactory.getLogger(this.getClass());

 @Reference
 private GenericCampaignConnector campaignConnector;

 @Reference
 private PageManagerFactory pageManagerFactory;

 @Override
 protected void doGet(SlingHttpServletRequest request,
   SlingHttpServletResponse response) throws ServletException,
   IOException {

  PageManager pm = pageManagerFactory.getPageManager(request.getResourceResolver());

  Page page = pm.getPage("/content/geometrixx-outdoors");

  String result = null;
  if ( page != null) {
   result = callCustomFunction(page);
  }
  if ( result != null ) {
   PrintWriter pw = response.getWriter();
   pw.print(result);
  }
 }

 private String callCustomFunction(Page page ) {
  try {
   Configuration config = campaignConnector.getWebserviceConfig(page.getContentResource().getParent());
   CampaignCredentials credentials = campaignConnector.retrieveCredentials(config);

   Map<String, String> params = new HashMap<String, String>();
   params.put("origin", "AEM");
   CallResults results = campaignConnector.callGeneric("/jssp/cus/custom.jssp", params, credentials);
   return results.bodyAsString();
  } catch (Exception e ) {
   log.error("Something went wrong during the connection", e);
  }
  return null;

 }

}
```

## Voorbeeld 2: Adobe Campaign AEM {#example-adobe-campaign-to-aem}

AEM biedt API&#39;s van de box uit om de objecten op te halen die overal beschikbaar zijn in de browser-weergave van sitebeheer.

![ chlimage_1-17 ](assets/chlimage_1-17a.png)

>[!NOTE]
>
>[ voor dit voorbeeld, zie Geometrixx ](/help/sites-developing/we-retail.md), die van het Aandeel van het Pakket beschikbaar is.

Voor elk knooppunt in de verkenner is er een API die eraan is gekoppeld. Bijvoorbeeld voor het knooppunt:

* [ http://localhost:4502/siteadmin#/content/campaigns/geometrixx/scott-recommends](http://localhost:4502/siteadmin#/content/campaigns/geometrixx/scott-recommends)

De API is:

* [ http://localhost:4502/content/campaigns/geometrixx/scott-recommends.1.json](http://localhost:4502/content/campaigns/geometrixx/scott-recommends.2.json)

Het einde van de URL **.1.json** kan worden vervangen door **.2.json** , **.3.json** , afhankelijk van het aantal subniveaus u in het krijgen geinteresseerd bent. Om elk van hen het sleutelwoord te verkrijgen, **oneindig** kan worden gebruikt:

* [ http://localhost:4502/content/campaigns/geometrixx/scott-recommends.infinity.json](http://localhost:4502/content/campaigns/geometrixx/scott-recommends.2.json)

AEM standaard basisverificatie gebruikt om de API te gebruiken.

Een bibliotheek JS die **amcIntegration.js** wordt genoemd is beschikbaar in 6.1.1 (bouwstijl 8624 en hoger) die die logica onder verscheidene andere degenen uitvoert.

### API-aanroep AEM {#aem-api-call}

```java
loadLibrary("nms:amcIntegration.js");

var cmsAccountId = sqlGetInt("select iExtAccountId from NmsExtAccount where sName=$(sz)","aemInstance")
var cmsAccount = nms.extAccount.load(String(cmsAccountId));
var cmsServer = cmsAccount.server;

var request = new HttpClientRequest(cmsServer+"/content/campaigns/geometrixx.infinity.json")
aemAddBasicAuthentication(cmsAccount, request);
request.method = "GET"
request.header["Content-Type"] = "application/json; charset=UTF-8";
request.execute();
var response = request.response;
```
