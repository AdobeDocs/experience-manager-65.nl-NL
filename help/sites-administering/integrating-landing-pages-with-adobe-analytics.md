---
title: Openingspagina's integreren met Adobe Analytics
seo-title: Openingspagina's integreren met Adobe Analytics
description: Leer hoe u bestemmingspagina's kunt integreren met Adobe Analytics.
seo-description: Leer hoe u bestemmingspagina's kunt integreren met Adobe Analytics.
uuid: 8f6672d1-497f-4ccb-b3cc-f6120fc467ba
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 8ae7ccec-489b-4d20-ac56-6101402fb18a
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd

---


# Openingspagina&#39;s integreren met Adobe Analytics{#integrating-landing-pages-with-adobe-analytics}

AEM heeft de landende paginaoplossing met [Adobe Analytics](https://www.omniture.com/en/products/analytics/sitecatalyst) door de volgende vraag-aan-actie (CTA) componenten te gebruiken geïntegreerd:

1. Klikken door component
1. Grafische koppelingscomponent

Deze componenten maken bepaalde kenmerken beschikbaar die via Adobe Analytics-variabelen (Verkeer, Conversievariabelen) en succesgebeurtenissen kunnen worden toegewezen om informatie naar Adobe Analytics te verzenden.

## Vereisten {#prerequisites}

Adobe raadt u aan de [bestaande integratie](/help/sites-administering/adobeanalytics.md) van AEM-Adobe Analytics door te nemen om te begrijpen hoe deze integratie werkt.

## Componenten beschikbaar voor toewijzing {#components-available-for-mapping}

In AEM, kan de **Vraag aan de componenten van de Actie** - **ClickThroughLink** en **GraphicalLink** - hier in het hulpslot worden getoond, aan de variabelen van de Analyse van Adobe worden in kaart gebracht.

![chlimage_1-21](assets/chlimage_1-21a.jpeg)

### Onderdelen van bestemmingspagina aan Adobe Analytics toewijzen {#mapping-landing-page-components-to-adobe-analytics}

U kunt landingspaginacomponenten toewijzen aan Adobe Analytics:

1. Nadat u de configuratie voor Adobe Analytics hebt gemaakt en een nieuw framework hebt gemaakt, selecteert u de gewenste rapportsuite in het keuzemenu. Dit resulteert in het ophalen van de Adobe Analytics-variabelen en het weergeven van deze variabelen in de zoekfunctie voor inhoud.
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
   <td><i>eventdata.clickLinkLabel</i><br /> </td>
   <td>Het label op de koppeling of de tekst van de koppeling </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.clickLinkTarget</i><br /> </td>
   <td>De bestemming waar u wordt genomen wanneer u op de verbinding klikt </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.events.clickLinkClick</i><br /> </td>
   <td>De gebeurtenis click </td>
  </tr>
  <tr>
   <td><strong>Grafische koppeling CTA</strong></td>
   <td><i>eventdata.clickroughImageLabel</i><br /> </td>
   <td>De titel van de CTA-afbeelding </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.clickroughImageTarget</i><br /> </td>
   <td>Het doel waar u naartoe gaat wanneer u klikt op de afbeelding die een koppeling bevat</td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.clickroughImageAsset</i><br /> </td>
   <td>Het pad naar het afbeeldingselement in de repository </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i>eventdata.events.clickStrokeImageClick</i><br /> </td>
   <td>De gebeurtenis click</td>
  </tr>
 </tbody>
</table>

1. Wijs deze belichte kenmerken toe aan Adobe Analytics-variabelen uit de zoeker naar inhoud. Het framework is nu gebruiksklaar.
1. U kunt nu een nieuwe bestemmingspagina maken of een bestaande landingspagina met bestaande componenten openen CTA en het lusje van de Diensten **van de** Wolk in de Eigenschappen **van de** Pagina van sidekick (in aanraking-geoptimaliseerde UI, selecteer **Open Eigenschappen** en klik de Diensten **van de** Wolk) en vorm het kader aan gebruik met het landen pagina. Selecteer het framework in de vervolgkeuzelijst.

   ![chlimage_1-25](assets/chlimage_1-25a.png)

1. Nadat u het framework hebt geconfigureerd met de bestemmingspagina, kunt u nu de van instrumenten voorziene componenten gebruiken. Wanneer u op CTA klikt, worden deze opgenomen in Adobe Analytics.

