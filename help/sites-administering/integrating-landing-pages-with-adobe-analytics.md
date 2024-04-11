---
title: Openingspagina's integreren met Adobe Analytics
description: Leer hoe u bestemmingspagina's kunt integreren met Adobe Analytics.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: da3f7b7e-87e5-446a-9a77-4b12b850a381
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
source-git-commit: eae057caed533ef16bb541b4ad41b8edd7aaa1c7
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Openingspagina&#39;s integreren met Adobe Analytics{#integrating-landing-pages-with-adobe-analytics}

AEM heeft de landingspagina-oplossing geïntegreerd met [Adobe Analytics](https://www.omniture.com/en/products/analytics/sitecatalyst) door de volgende vraag-aan-actie (CTA) componenten te gebruiken:

1. Klikken door component
1. Grafische koppelingscomponent

Deze componenten maken bepaalde kenmerken beschikbaar die via Adobe Analytics-variabelen (Verkeer, Conversievariabelen) en succesgebeurtenissen kunnen worden toegewezen om informatie naar Adobe Analytics te verzenden.

## Vereisten {#prerequisites}

Adobe raadt u aan de [bestaande AEM-Adobe Analytics-integratie](/help/sites-administering/adobeanalytics.md) om te begrijpen hoe deze integratie werkt.

## Componenten beschikbaar voor toewijzing {#components-available-for-mapping}

In AEM **Oproep tot actie** componenten - **ClickThroughLink** en **GraphicalLink** - hier in het hulpslot wordt getoond, kan aan variabelen van Adobe Analytics worden in kaart gebracht.

![chlimage_1-21](assets/chlimage_1-21a.jpeg)

### Onderdelen van bestemmingspagina aan Adobe Analytics toewijzen {#mapping-landing-page-components-to-adobe-analytics}

U kunt landingspaginacomponenten toewijzen aan Adobe Analytics:

1. Nadat u de Adobe Analytics-configuratie hebt gemaakt en een framework hebt gemaakt, selecteert u de gewenste rapportsuite in het keuzemenu. Hierdoor worden de Adobe Analytics-variabelen opgehaald en weergegeven in de zoekfunctie voor inhoud.
1. De belemmering en laat vallen Vraag aan de componenten van de Actie (CTA) van sidekick in het kaartingsgebied in het midden van de pagina, zoals aangewezen.

<table>
 <tbody>
  <tr>
   <td><strong>Componentnaam</strong></td>
   <td><strong>Kenmerken beschikbaar</strong></td>
   <td><strong>Betekenis van kenmerk</strong></td>
  </tr>
  <tr>
   <td><strong>CTA-klik via koppeling</strong></td>
   <td><i>eventdata.clickLinkLabel</i> <br /> </td>
   <td>Het label op de koppeling of de tekst van de koppeling </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.clickLinkTarget</i> <br /> </td>
   <td>Het doel waar u naartoe gaat wanneer u op de koppeling klikt </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.events.clickthroughLinkClick</i> <br /> </td>
   <td>De gebeurtenis click </td>
  </tr>
  <tr>
   <td><strong>Grafische koppeling CTA</strong></td>
   <td><i>eventdata.clickroughImageLabel</i> <br /> </td>
   <td>De titel van de CTA-afbeelding </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.clickroughImageTarget</i> <br /> </td>
   <td>Het doel waar u naartoe gaat wanneer u op de afbeelding met een koppeling klikt</td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.clickroughImageAsset</i> <br /> </td>
   <td>Het pad naar het afbeeldingselement in de repository </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.events.clickStrokeImageClick</i> <br /> </td>
   <td>De gebeurtenis click</td>
  </tr>
 </tbody>
</table>

1. Wijs deze belichte kenmerken toe aan alle Adobe Analytics-variabelen van de zoeker naar inhoud. Het framework is nu gebruiksklaar.
1. U kunt nu een bestemmingspagina tot stand brengen of een bestaande landingspagina met bestaande componenten openen CTA en klikken **Cloud Servicen** tab in **Pagina-eigenschappen** in het zijpaneel (in de interface met geoptimaliseerde aanrakingen) selecteert u **Eigenschappen openen** en klik op **Cloud Servicen**) en configureert u het framework dat u wilt gebruiken met de bestemmingspagina. Selecteer het framework in de vervolgkeuzelijst.

   ![chlimage_1-25](assets/chlimage_1-25a.png)

1. Nadat u het framework hebt geconfigureerd met de bestemmingspagina, kunt u nu de van instrumenten voorziene componenten gebruiken en worden eventuele klikken op CTA opgenomen in Adobe Analytics.
