---
title: Pagina-informatie ophalen in JSON-indeling
description: Als u de pagina-informatie wilt opvragen, stuurt u een verzoek naar het PageInfo-servlet om de metagegevens van de pagina op te vragen in de JSON-indeling
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
exl-id: 7c856e87-9f90-435d-aceb-994f10ea6f50
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '931'
ht-degree: 0%

---

# Pagina-informatie ophalen in JSON-indeling{#obtaining-page-information-in-json-format}

Als u de pagina-informatie wilt opvragen, stuurt u een verzoek naar het PageInfo-server om de metagegevens van de pagina in JSON-indeling op te halen.

Het PageInfo servlet keert informatie over middelen in de bewaarplaats terug. De servlet is gebonden aan de URL `https://<server>:<port>/libs/wcm/core/content/pageinfo.json` en gebruikt de `path` parameter om de bron te identificeren. De volgende voorbeeld-URL retourneert informatie over de `/content/we-retail/us/en` knooppunt:

```shell
http://localhost:4502/libs/wcm/core/content/pageinfo.json?path=/content/we-retail/us/en
```

>[!NOTE]
>
>Als u paginagegevens in JSON-indeling nodig hebt om inhoud te leveren aan kanalen die niet traditioneel AEM webpagina&#39;s zijn, zoals:
>
>* Toepassingen voor één pagina
>* Systeemeigen mobiele toepassingen
>* Andere kanalen en aanraakpunten buiten AEM
>
>Zie het document [JSON-exportfunctie voor services voor inhoud](/help/sites-developing/json-exporter.md).

## Paginainformatieproviders {#page-information-providers}

Paginacomponenten kunnen aan een of meer `com.day.cq.wcm.api.PageInfoProvider` services die metagegevens over pagina&#39;s genereren. Het PageInfo-servlet roept elke PageInfoProvider-service aan en voegt de metagegevens samen:

1. De HTTP-client verzendt een aanvraag naar het PageInfo-server, die de URL van de pagina bevat.
1. Het PageInfo servlet ontdekt welke component de pagina teruggeeft.
1. Het PageInfo-servlet roept elke PageInfoProvider aan die aan de component is gekoppeld.
1. De servlet aggregeert de meta-gegevens die elke PageInfoProvider terugkeert en voegt de meta-gegevens aan de reactie van HTTP in een voorwerp JSON toe.

![chlimage_1-2](assets/chlimage_1-2a.png)

>[!NOTE]
>
>Net als PageInfoProviders gebruikt u ListInfoProviders om lijsten met informatie in JSON-indeling bij te werken. (Zie [De beheerconsole voor websites aanpassen](/help/sites-developing/customizing-siteadmin.md).)

## Standaardpaginainformatieproviders {#default-page-information-providers}

De `/libs/foundation/components/page` wordt gekoppeld aan de volgende PageInfoProvider-services:

* **Standaardpaginastatusprovider:** Informatie over de status van de pagina, zoals of deze is vergrendeld, of de pagina de lading van een actieve werkstroom is en welke werkstromen beschikbaar zijn voor de pagina.
* **Informatieprovider voor live relaties:** Informatie over MSM (Multi Site Management), zoals of de pagina deel uitmaakt van een blauwe afdruk en of het een live kopie is.
* **Servlet van de Taal van de inhoud:** De taal van de huidige pagina en informatie over elke taal waarin de pagina beschikbaar is.
* **Workflow Status Provider:** Statusinformatie over de actieve werkstroom die de pagina als een lading heeft.
* **Informatieaanbieder voor workflowpakket:** Informatie over elk werkstroompakket dat in de bewaarplaats wordt opgeslagen, en of elk pakket de huidige bron bevat.
* **Emulatorinformatieprovider:** Informatie over de emulators van mobiele apparaten die beschikbaar zijn voor deze bron. Als de paginacomponent geen mobiele pagina&#39;s rendert, zijn er geen emulators beschikbaar.
* **Informatieaanbieder annotaties:** Informatie over annotaties die op de pagina staan.

Het PageInfo-servlet retourneert bijvoorbeeld de volgende JSON-reactie voor de `/content/we-retail/us/en` knooppunt:

```
{
   "status":{
      "path":"/content/we-retail/us/en",
      "isLocked":false,
      "lockOwner":"",
      "canUnlock":false,
      "lastModified":1467202845038,
      "lastModifiedBy":"admin",
      "timeUntilValid":0,
      "onTime":0,
      "offTime":0,
      "replication":{
         "numQueued":0
      },
      "isDesignable":true,
      "isDeveloper":true
   },
   "isPage":true,
   "pageResourceType":"weretail/components/structure/page",
   "enableFragmentIdentifier":false,
   "workflow":{
      "isRunning":false
   },
   "workflows":{
      "wcm":{
         "models":[
            {
               "wid":"/etc/workflow/models/dam/adddamsize/jcr:content/model",
               "label":"Add Asset Size",
               "label_xss":"Add Asset Size"
            },
            {
               "wid":"/etc/workflow/models/ac-newsletter-workflow-simple/jcr:content/model",
               "label":"Approve for Adobe Campaign",
               "label_xss":"Approve for Adobe Campaign"
            },
            {
               "wid":"/etc/workflow/models/dam/dam-autotag-assets/jcr:content/model",
               "label":"DAM Smart Tag Assets",
               "label_xss":"DAM Smart Tag Assets"
            },
            {
               "wid":"/etc/workflow/models/dam/update_asset/jcr:content/model",
               "label":"DAM Update Asset",
               "label_xss":"DAM Update Asset"
            },
            {
               "wid":"/etc/workflow/models/cloudservices/DTM_bundle_download/jcr:content/model",
               "label":"Default DTM Bundle Download",
               "label_xss":"Default DTM Bundle Download"
            },
            {
               "wid":"/etc/workflow/models/dam/dam_download_asset/jcr:content/model",
               "label":"Download Asset",
               "label_xss":"Download Asset"
            },
            {
               "wid":"/etc/workflow/models/dam/dynamic-media-video-thumbnail-replacement/jcr:content/model",
               "label":"Dynamic Media Video Thumbnail Replacement",
               "label_xss":"Dynamic Media Video Thumbnail Replacement"
            },
            {
               "wid":"/etc/workflow/models/dam/dynamic-media-video-user-uploaded-thumbnail/jcr:content/model",
               "label":"Dynamic Media Video User Uploaded Thumbnail Process",
               "label_xss":"Dynamic Media Video User Uploaded Thumbnail Process"
            },
            {
               "wid":"/etc/workflow/models/projects/approval_workflow/jcr:content/model",
               "label":"Project Approval Workflow",
               "label_xss":"Project Approval Workflow"
            },
            {
               "wid":"/etc/workflow/models/publish_example/jcr:content/model",
               "label":"Publish Example",
               "label_xss":"Publish Example"
            },
            {
               "wid":"/etc/workflow/models/publish_to_campaign/jcr:content/model",
               "label":"Publish to Adobe Campaign",
               "label_xss":"Publish to Adobe Campaign"
            },
            {
               "wid":"/etc/workflow/models/s7dam/request_to_publish_to_youtube/jcr:content/model",
               "label":"Publish to YouTube",
               "label_xss":"Publish to YouTube"
            },
            {
               "wid":"/etc/workflow/models/projects/request_copy/jcr:content/model",
               "label":"Request Copy",
               "label_xss":"Request Copy"
            },
            {
               "wid":"/etc/workflow/models/request_for_activation/jcr:content/model",
               "label":"Request for Activation",
               "label_xss":"Request for Activation"
            },
            {
               "wid":"/etc/workflow/models/request_for_deactivation/jcr:content/model",
               "label":"Request for Deactivation",
               "label_xss":"Request for Deactivation"
            },
            {
               "wid":"/etc/workflow/models/request_for_deletion/jcr:content/model",
               "label":"Request for Deletion",
               "label_xss":"Request for Deletion"
            },
            {
               "wid":"/etc/workflow/models/request_to_complete_move_operation/jcr:content/model",
               "label":"Request to complete Move operation",
               "label_xss":"Request to complete Move operation"
            },
            {
               "wid":"/etc/workflow/models/screens-update-asset/jcr:content/model",
               "label":"Screens Update Asset",
               "label_xss":"Screens Update Asset"
            },
            {
               "wid":"/etc/workflow/models/s7dam/request_to_remove_from_youtube/jcr:content/model",
               "label":"Unpublish from YouTube",
               "label_xss":"Unpublish from YouTube"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/create_language_copy/jcr:content/model",
               "label":"WCM: Create Language Copy",
               "label_xss":"WCM: Create Language Copy"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/prepare_translation_project/jcr:content/model",
               "label":"WCM: Prepare Translation Project",
               "label_xss":"WCM: Prepare Translation Project"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/translate-i18n-dictionary/jcr:content/model",
               "label":"WCM: Prepare and Translate I18n-Dictionary",
               "label_xss":"WCM: Prepare and Translate I18n-Dictionary"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/sync_translation_job/jcr:content/model",
               "label":"WCM: Sync Translation Job",
               "label_xss":"WCM: Sync Translation Job"
            },
            {
               "wid":"/etc/workflow/models/wcm-translation/update_language_copy/jcr:content/model",
               "label":"WCM: Update Language Copy",
               "label_xss":"WCM: Update Language Copy"
            }
         ]
      },
      "translation":{
         "models":[
            {
               "wid":"/etc/workflow/models/dam/adddamsize/jcr:content/model",
               "label":"Add Asset Size",
               "label_xss":"Add Asset Size"
            },
            {
               "wid":"/etc/workflow/models/ac-newsletter-workflow-simple/jcr:content/model",
               "label":"Approve for Adobe Campaign",
               "label_xss":"Approve for Adobe Campaign"
            },
            {
               "wid":"/etc/workflow/models/dam/dam-autotag-assets/jcr:content/model",
               "label":"DAM Smart Tag Assets",
               "label_xss":"DAM Smart Tag Assets"
            },
            {
               "wid":"/etc/workflow/models/cloudservices/DTM_bundle_download/jcr:content/model",
               "label":"Default DTM Bundle Download",
               "label_xss":"Default DTM Bundle Download"
            },
            {
               "wid":"/etc/workflow/models/dam/dam_download_asset/jcr:content/model",
               "label":"Download Asset",
               "label_xss":"Download Asset"
            },
            {
               "wid":"/etc/workflow/models/dam/dynamic-media-video-thumbnail-replacement/jcr:content/model",
               "label":"Dynamic Media Video Thumbnail Replacement",
               "label_xss":"Dynamic Media Video Thumbnail Replacement"
            },
            {
               "wid":"/etc/workflow/models/dam/dynamic-media-video-user-uploaded-thumbnail/jcr:content/model",
               "label":"Dynamic Media Video User Uploaded Thumbnail Process",
               "label_xss":"Dynamic Media Video User Uploaded Thumbnail Process"
            },
            {
               "wid":"/etc/workflow/models/projects/approval_workflow/jcr:content/model",
               "label":"Project Approval Workflow",
               "label_xss":"Project Approval Workflow"
            },
            {
               "wid":"/etc/workflow/models/publish_to_campaign/jcr:content/model",
               "label":"Publish to Adobe Campaign",
               "label_xss":"Publish to Adobe Campaign"
            },
            {
               "wid":"/etc/workflow/models/s7dam/request_to_publish_to_youtube/jcr:content/model",
               "label":"Publish to YouTube",
               "label_xss":"Publish to YouTube"
            },
            {
               "wid":"/etc/workflow/models/projects/request_copy/jcr:content/model",
               "label":"Request Copy",
               "label_xss":"Request Copy"
            },
            {
               "wid":"/etc/workflow/models/request_for_deletion/jcr:content/model",
               "label":"Request for Deletion",
               "label_xss":"Request for Deletion"
            },
            {
               "wid":"/etc/workflow/models/request_to_complete_move_operation/jcr:content/model",
               "label":"Request to complete Move operation",
               "label_xss":"Request to complete Move operation"
            },
            {
               "wid":"/etc/workflow/models/screens-update-asset/jcr:content/model",
               "label":"Screens Update Asset",
               "label_xss":"Screens Update Asset"
            },
            {
               "wid":"/etc/workflow/models/translation/jcr:content/model",
               "label":"Translation Prepare",
               "label_xss":"Translation Prepare"
            },
            {
               "wid":"/etc/workflow/models/s7dam/request_to_remove_from_youtube/jcr:content/model",
               "label":"Unpublish from YouTube",
               "label_xss":"Unpublish from YouTube"
            }
         ]
      }
   },
   "translation":{

   },
   "design":{
      "path":"/conf/we-retail/settings/wcm/templates/hero-page/policies",
      "lastModified":0
   },
   "componentsRef":"/libs/wcm/core/content/components.1497341312569.json",
   "editableTemplate":"/conf/we-retail/settings/wcm/templates/hero-page",
   "msm":{
      "msm:isLiveCopy":true,
      "msm:isInBlueprint":false,
      "msm:isSource":false
   },
   "launches":{
      "isLaunch":false,
      "isInLaunch":false
   },
   "language":"en",
   "languages":{
      "rows":[
         {
            "path":"/content/we-retail/us/en",
            "exists":true,
            "hasContent":true,
            "lastModified":0,
            "iso":"en",
            "country":"gb",
            "language":"English"
         },
         {
            "path":"/content/we-retail/us/es",
            "exists":true,
            "hasContent":true,
            "lastModified":0,
            "iso":"es",
            "country":"es",
            "language":"Spanish"
         }
      ]
   },
   "workflowInfo":{
      "isRunning":false
   },
   "workflowPackageInfo":{
      "workflowPackages":[

      ],
      "selectedWorkflowPackages":[

      ],
      "runningSelectedWorkflowPackages":[

      ]
   },
   "emulators":{
      "groups":{
         "responsive":{
            "title":"Responsive Devices",
            "description":"The devices in this group are able to display a website built using responsive design patterns.",
            "path":"/etc/mobile/groups/responsive",
            "galaxy5":{
               "text":"Galaxy S5",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/galaxy5",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":1080,
               "height":1920,
               "device-pixel-ratio":3
            },
            "ipad":{
               "text":"iPad",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/ipad",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":768,
               "height":1024,
               "device-pixel-ratio":1
            },
            "iphone5":{
               "text":"iPhone 5",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/iphone5",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":640,
               "height":1136,
               "device-pixel-ratio":2
            },
            "iphone6":{
               "text":"iPhone 6",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/iphone6",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":750,
               "height":1334,
               "device-pixel-ratio":2
            },
            "iphone4":{
               "text":"iPhone 4",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/iphone4",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":640,
               "height":960,
               "device-pixel-ratio":2
            },
            "iphone6plus":{
               "text":"iPhone 6 Plus",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/ios/iphone6plus",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":1080,
               "height":1920,
               "device-pixel-ratio":2.6
            },
            "nexuss":{
               "text":"Nexus S",
               "action":"start",
               "path":"/libs/wcm/mobile/components/emulators/nexuss",
               "canRotate":true,
               "hasTouchScrolling":true,
               "contentCssPath":"/etc/mobile/groups/responsive/static.css",
               "width":320,
               "height":533,
               "device-pixel-ratio":1
            }
         }
      }
   },
   "annotations":[

   ],
   "permissions":{
      "modify":true,
      "replicate":true,
      "read":true,
      "create":true,
      "delete":true,
      "acl_read":true,
      "acl_edit":true
   },
   "isTargetable":"true",
   "responsive":{
      "breakpoints":{
         "phone":{
            "width":650,
            "title":"Smaller Screen"
         },
         "tablet":{
            "width":1200,
            "title":"Tablet"
         }
      }
   }
}
```

## Workflowpakketinformatie filteren {#filtering-workflow-package-information}

Vorm de dienst van de Leverancier van de Informatie van het Pakket van het Pakket van het Werkschema van de Dag CQ WCM zodat het informatie over slechts de werkschemapakketten terugkeert waarin u geinteresseerd bent. Standaard retourneert de Workflow Package Info Provider service informatie over elk workflowpakket in de repository. Het herhalen over een ondergroep van werkschemapakketten gebruikt minder servermiddelen.

>[!NOTE]
>
>Het tabblad Workflow van Sidekick gebruikt het PageInfo-servlet om een lijst met workflowpakketten te verkrijgen. In de lijst kunt u het pakket selecteren waaraan u de huidige pagina wilt toevoegen. De filters die u creeert beïnvloeden deze lijst.
>

De id van de service is `com.day.cq.wcm.workflow.impl.WorkflowPackageInfoProvider`. Als u een filter wilt maken, geeft u een waarde op voor `workflowpackageinfoprovider.filter` eigenschap.

Eigenschapwaarden beginnen met een plusteken (+ of -) gevolgd door het pakketpad:

* Het pad is het pad van het hoofdknooppunt van het workflowpakket. Het pad gebruikt de FileVault-syntaxis.
* Als u een pakket wilt opnemen, gebruikt u het voorvoegsel +.
* Als u een pakket wilt uitsluiten, gebruikt u het voorvoegsel -.

De service past het cumulatieve resultaat van alle filters toe. De volgende filterwaarden sluiten bijvoorbeeld alle workflowpakketten uit, behalve de pakketten in de map Editions:

```
-/etc/workflow/packages(/.*)?
+/etc/workflow/packages/Editions(/.&ast;)?
```

>[!NOTE]
>
>Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke diensten te beheren. Zie [OSGi configureren](/help/sites-deploying/configuring-osgi.md) voor volledige informatie.

Bijvoorbeeld, om de dienst te vormen gebruikend CRXDE Lite:

1. CRXDE Lite openen ([http://localhost:4502/crx/de](http://localhost:4502/crx/de)).
1. Maak een knooppunt in de configuratiemap van uw toepassing:

   * Naam: `com.day.cq.wcm.workflow.impl.WorkflowPackageInfoProvider`
   * Type: `sling:OsgiConfig`

1. Selecteer het knooppunt en voeg een eigenschap toe:

   * Naam: `workflowpackageinfoprovider.filter`
   * Type: `String[]`
   * Waarde: het pad naar het workflowpakket met de juiste indeling.

1. Klik op Alles opslaan.

Om de dienst in uw projectbron te vormen:

1. Zoek of maak de configuratiemap voor uw AEM toepassing in uw projectbron.

   Als u bijvoorbeeld het archetype met meerdere modules van de insteekmodule Inhoudspakket hebt gebruikt om uw project te maken, is het mappad `<projectroot>/content/src/ for example, content/src/main/content/jcr_root/apps/<appname>/config`.
1. Maak in de configuratiemap een tekstbestand met de naam com.day.cq.wcm.workflow.impl.WorkflowPackageInfoProvider.xml
1. Kopieer de volgende tekst naar het bestand:

   ```
   <?xml version="1.0" encoding="UTF-8"?>
    <jcr:root xmlns:sling="https://sling.apache.org/jcr/sling/1.0"
    xmlns:jcr="https://www.jcp.org/jcr/1.0"
    jcr:primaryType="sling:OsgiConfig"
    workflowpackageinfoprovider.filter="[]"/>
   ```

1. Binnen de vierkante haakjes (`[]`) die de `workflowpackageinfoprovider.filter` eigenschap, typt u een door komma&#39;s gescheiden lijst met filterwaarden, vergelijkbaar met het volgende voorbeeld:

   `workflowpackageinfoprovider.filter="[-/etc/workflow/packages(/.*)?,+/etc/workflow/packages/Editions(/.*)?]"/>`

1. Sla het bestand op.

## Een paginainformatieprovider maken {#creating-a-page-information-provider}

Maak een aangepaste service van de provider van paginagegevens om metagegevens toe te voegen die uw toepassing gemakkelijk kan ophalen.

1. Implementeer de `com.day.cq.wcm.api.PageInfoProvider` interface.
1. Bundel en stel de klasse als dienst OSGi op.
1. Maak een pagina-component in uw toepassing. Gebruiken `foundation/components/page` als de waarde van de `sling:resourceSuperType` eigenschap.

1. Een knooppunt toevoegen onder het componentknooppunt genaamd `cq:infoProviders`.
1. Onder de `cq:infoProviders` knooppunt, voegt u een knooppunt toe voor uw PageInfoProvider-service. U kunt elke naam voor het knooppunt opgeven.
1. Voeg de volgende eigenschap toe aan het knooppunt PageInfoProvider:

   * Naam: className
   * Type: String
   * Waarde: de PID van uw PageInfoProvider-service.

Voor bronnen die uw component van de toepassingspagina als `sling:resourceType`, retourneert het PageInfo-servlet naast de standaardmetagegevens van PageInfoProvider ook de aangepaste PageInfoProvider-metagegevens.

### Voorbeeld van implementatie van PageInfoProvider {#example-pageinfoprovider-implementation}

De volgende Java-klasse implementeert [PageInfoProvider](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/index.html) en retourneert de gepubliceerde URL van de huidige paginabron.

```java
package com.adobe.example;

import org.apache.felix.scr.annotations.Component;
import org.apache.felix.scr.annotations.Properties;
import org.apache.felix.scr.annotations.Property;
import org.apache.felix.scr.annotations.ReferenceCardinality;
import org.apache.felix.scr.annotations.Service;
import org.apache.felix.scr.annotations.Reference;

import org.apache.sling.api.SlingHttpServletRequest;
import org.apache.sling.api.resource.Resource;
import org.apache.sling.api.resource.ResourceResolver;

import org.apache.sling.commons.json.JSONException;
import org.apache.sling.commons.json.JSONObject;

import com.day.cq.wcm.api.Page;
import com.day.cq.wcm.api.PageInfoProvider;

@Component(metatype = false)
@Properties({
 @Property(name="service.description", value="Returns the public URL of a resource.")
})
@Service
public class PageUrlInfoProvider implements PageInfoProvider {

 @Reference(cardinality = ReferenceCardinality.OPTIONAL_UNARY)
 private com.day.cq.commons.Externalizer externalizer;

 private String fetchExternalUrl(ResourceResolver rr, String path) {
  return externalizer.publishLink(rr, path);
 }

 public void updatePageInfo(SlingHttpServletRequest request, JSONObject info, Resource resource)
   throws JSONException {

  Page page = resource.adaptTo(Page.class);
  JSONObject urlinfo = new JSONObject();
  urlinfo.put("publishURL", fetchExternalUrl(null,page.getPath()));
  info.put("URLs",urlinfo);
 }
}
```

In het volgende voorbeeld, in CRXDE Lite, wordt de paginacomponent getoond die is geconfigureerd om de PageUrlInfoProvider-service te gebruiken:

![chlimage_1-3](assets/chlimage_1-3a.png)

De PageUrlInfoProvider-service retourneert de volgende gegevens voor de `/content/we-retail/us/en` knooppunt:

```xml
"URLs": {
    "publishURL": "http://localhost:4503/content/we-retail/us/en"
}
```
