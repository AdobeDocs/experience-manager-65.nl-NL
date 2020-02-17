---
title: Aangepaste extensies maken
seo-title: Aangepaste extensies maken
description: U kunt uw aangepaste code in Adobe Campaign aanroepen van AEM of van AEM naar Adobe Campaign
seo-description: U kunt uw aangepaste code in Adobe Campaign aanroepen van AEM of van AEM naar Adobe Campaign
uuid: 8392aa0d-06cd-4b37-bb20-f67e6a0550b1
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: f536bcc1-7744-4f05-ac6a-4cec94a1ffb6
translation-type: tm+mt
source-git-commit: 06f1f753b9bb7f7336454f166e03f753e3735a16

---


# Aangepaste extensies maken{#creating-custom-extensions}

Wanneer u een project implementeert, hebt u doorgaans aangepaste code in zowel AEM- als Adobe-campagne. Met behulp van de bestaande API kunt u uw aangepaste code in Adobe Campaign oproepen van AEM of van AEM naar Adobe Campaign. In dit document wordt beschreven hoe u dat doet.

## Vereisten {#prerequisites}

U moet het volgende installeren:

* Adobe Experience Manager
* Adobe-campagne 6.1

Zie [AEM integreren met Adobe Campagne 6.1](/help/sites-administering/campaignonpremise.md) voor meer informatie.

## Voorbeeld 1: AEM naar Adobe-campagne {#example-aem-to-adobe-campaign}

De standaardintegratie tussen AEM en Campagne is gebaseerd op JSON en JSSP (JavaScript Server Page). Deze JSSP-bestanden vindt u in de Campagne-console en beginnen allemaal met **amc** (Adobe Marketing Cloud).

![chlimage_1-15](assets/chlimage_1-15a.png)

>[!NOTE]
>
>[Voor dit voorbeeld, gelieve te zien Geometrixx](/help/sites-developing/we-retail.md), die bij het Aandeel van het Pakket beschikbaar is.

In dit voorbeeld maken we een nieuw aangepast JSSP-bestand en roepen we dat bestand aan vanaf de AEM-zijde om het resultaat op te halen. Dit kan bijvoorbeeld worden gebruikt om gegevens op te halen uit Adobe Campaign of om gegevens op te slaan in Adobe Campaign.

1. Als u in Adobe Campaign een nieuw JSSP-bestand wilt maken, klikt u op het pictogram **Nieuw** .

   ![](do-not-localize/chlimage_1-4a.png)

1. Voer de naam van dit JSSP-bestand in. In dit voorbeeld gebruiken we **cus:custom.jssp** (dit betekent dat deze zich in de naamruimte **cus** bevindt).

   ![chlimage_1-16](assets/chlimage_1-16a.png)

1. Plaats de volgende code in het jssp-bestand:

   ```
   <%
   var origin = request.getParameter("origin");
   document.write("Hello from Adobe Campaign, origin : " + origin);
   %>
   ```

1. Sla uw werk op. Het resterende werk is in AEM.
1. Creeer een eenvoudige servlet op de kant van AEM om dit JSSP te roepen. In dit voorbeeld gaan we uit van het volgende:

   * U hebt een verbinding tussen AEM en Campagne
   * De campagnecloudservice is geconfigureerd op **/content/geometrixx-outdoor**
   Het belangrijkste object in dit voorbeeld is de **GenericCampaignConnector**, waarmee u jssp-bestanden kunt aanroepen (ophalen en posten) aan de zijde van de Adobe-campagne.

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

1. Zoals u in dit voorbeeld ziet, moet u in de geloofsbrieven in de vraag overgaan. U kunt dit bereiken via de methode getCredentials(), waarbij u een pagina doorgeeft waarvoor de Campagnewolkenservice is geconfigureerd.

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

## Voorbeeld 2: Adobe-campagne naar AEM {#example-adobe-campaign-to-aem}

AEM biedt API&#39;s uit de doos aan om de objecten op te halen die overal beschikbaar zijn in de browser-weergave voor sitebeheer.

![chlimage_1-17](assets/chlimage_1-17a.png)

>[!NOTE]
>
>[Voor dit voorbeeld, gelieve te zien Geometrixx](/help/sites-developing/we-retail.md), die bij het Aandeel van het Pakket beschikbaar is.

Voor elk knooppunt in de verkenner is er een API die eraan is gekoppeld. Bijvoorbeeld voor het knooppunt:

* [http://localhost:4502/siteadmin#/content/campaigns/geometrixx/scott-recommends](http://localhost:4502/siteadmin#/content/campaigns/geometrixx/scott-recommends)

de API is:

* [http://localhost:4502/content/campaigns/geometrixx/scott-recommends.1.json](http://localhost:4502/content/campaigns/geometrixx/scott-recommends.2.json)

Het einde van URL **.1.json** kan worden vervangen door **.2.json**, **.3.json**, afhankelijk van het aantal subniveaus u in het krijgen van interesseert u om allen te verkrijgen het sleutelwoord **oneindig** kan worden gebruikt:

* [http://localhost:4502/content/campaigns/geometrixx/scott-recommends.infinity.json](http://localhost:4502/content/campaigns/geometrixx/scott-recommends.2.json)

Nu moeten we weten dat AEM standaard de basisverificatie gebruikt om de API te gebruiken.

Een bibliotheek JS die **amcIntegration.js** wordt genoemd is beschikbaar in 6.1.1 (bouwstijl 8624 en hoger) die die logica onder verscheidene andere uitvoert.

### AEM API-aanroep {#aem-api-call}

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

