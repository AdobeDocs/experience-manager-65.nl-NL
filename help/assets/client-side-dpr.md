---
title: Slimme beeldverwerking gebruiken met pixelverhouding van client-side apparaat
description: Leer hoe u de pixelverhouding van client-side apparaten kunt gebruiken met Smart Imaging in Adobe Experience Manager as a Cloud Service met Dynamic Media.
role: Admin,User
exl-id: e38f522a-242a-4ea9-a866-d8d129950831
solution: Experience Manager, Experience Manager Assets
feature: Smart Imaging
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '324'
ht-degree: 0%

---

# Informatie over Smart Imaging met de pixelverhouding van het client-side apparaat (DPR) {#client-side-dpr}

De huidige oplossing voor Smart Imaging gebruikt userAgent-tekenreeksen om het type apparaat (bureaublad, tablet, mobiel, enzovoort) te bepalen dat wordt gebruikt.

Apparaatdetectiemogelijkheden - DPR op basis van tekenreeksen voor gebruikersagent - zijn vaak onjuist, vooral voor Apple-apparaten. Ook, wanneer een nieuw apparaat wordt gelanceerd, moet het worden bevestigd.

DPR aan de clientzijde biedt u 100% nauwkeurige waarden en werkt voor elk apparaat, of het nu Apple of een ander nieuw apparaat is dat is gestart.

## De client-side DPR-code gebruiken

**server-kant teruggegeven apps**

1. Laad de init van de de dienstarbeider (`srvinit.js`) door het volgende manuscript in de kopbalsectie van uw pagina van de HTML te omvatten:

   ```javascript
   <script type="text/javascript" src="srvinit.js"></script>
   ```

   De Adobe adviseert dat u dit manuscript _vóór_ om het even welke andere manuscripten laadt zodat de de dienstarbeider onmiddellijk initialisatie begint.

1. Neem de volgende DPR-code voor afbeeldingstag op boven aan de hoofdsectie van de pagina HTML:

   ```html
   <img src="aem_dm_dpr_1x.jpg" style="width:1px;height:1px;display:none"
       srcset="aem_dm_dpr_1x.jpg 1x, aem_dm_dpr_1.1x.jpg 1.1x, aem_dm_dpr_1.2x.jpg 1.2x, aem_dm_dpr_1.3x.jpg 1.3x, aem_dm_dpr_1.4x.jpg 1.4x, aem_dm_dpr_1.5x.jpg 1.5x, aem_dm_dpr_1.6x.jpg 1.6x,          aem_dm_dpr_1.7x.jpg 1.7x, aem_dm_dpr_1.8x.jpg 1.8x, aem_dm_dpr_1.9x.jpg 1.9x,
       aem_dm_dpr_2x.jpg 2x, aem_dm_dpr_2.1x.jpg 2.1x, aem_dm_dpr_2.2x.jpg 2.2x, aem_dm_dpr_2.3x.jpg 2.3x, aem_dm_dpr_2.4x.jpg 2.4x, aem_dm_dpr_2.5x.jpg 2.5x, aem_dm_dpr_2.6x.jpg 2.6x, aem_dm_dpr_2.7x.jpg 2.7x, aem_dm_dpr_2.8x.jpg 2.8x, aem_dm_dpr_2.9x.jpg 2.9x,
       aem_dm_dpr_3x.jpg 3x, aem_dm_dpr_3.1x.jpg 3.1x, aem_dm_dpr_3.2x.jpg 3.2x, aem_dm_dpr_3.3x.jpg 3.3x, aem_dm_dpr_3.4x.jpg 3.4x, aem_dm_dpr_3.5x.jpg 3.5x, aem_dm_dpr_3.6x.jpg 3.6x, aem_dm_dpr_3.7x.jpg 3.7x, aem_dm_dpr_3.8x.jpg 3.8x, aem_dm_dpr_3.9x.jpg 3.9x,
       aem_dm_dpr_4x.jpg 4x, aem_dm_dpr_4.1x.jpg 4.1x, aem_dm_dpr_4.2x.jpg 4.2x, aem_dm_dpr_4.3x.jpg 4.3x, aem_dm_dpr_4.4x.jpg 4.4x, aem_dm_dpr_4.5x.jpg 4.5x, aem_dm_dpr_4.6x.jpg 4.6x, aem_dm_dpr_4.7x.jpg 4.7x, aem_dm_dpr_4.8x.jpg 4.8x, aem_dm_dpr_4.9x.jpg 4.9x,
       aem_dm_dpr_5x.jpg 5x">
   ```

   Het is verplicht dat u dit DPR beeld markeringscode _vóór_ alle statische beelden in uw pagina van de HTML omvat.

**Client-kant teruggegeven apps**

1. Neem de volgende DPR-scripts op in de koptekstsectie van de pagina HTML:

   ```javascript
   <script type="text/javascript" src="srvinit.js"></script>
   <script type="text/javascript" src="dprImageInjection.js"></script>
   ```

   U kunt beide DPR manuscripten in één combineren om veelvoudige netwerkverzoeken te vermijden.

   De Adobe adviseert dat u deze manuscripten _vóór_ om het even welke andere manuscripten in de pagina van de HTML laadt.
Adobe raadt u ook aan uw toepassing onder de tag diff HTML te Bootstrappen in plaats van onder een body-element. De reden hiervoor is dat `dprImageInjection.js` de afbeeldingstag dynamisch boven aan de hoofdsectie op de pagina HTML injecteert.

## JavaScript-bestanden downloaden {#client-side-dpr-script}

De volgende JavaScript-bestanden in de download worden alleen ter referentie aan u verstrekt. Als u deze bestanden wilt gebruiken op HTML-pagina&#39;s, moet u de code van elk bestand bewerken zodat deze aan uw eigen vereisten voldoet.

* `dprImageInjection.js`
* `srvinit.js`
* `srvwrk.js`

[JavaScript-bestanden downloaden](/help/assets/assets-dm/aem-dynamicmedia-smartimaging-dpr.zip)

>[!MORELIKETHIS]
>
>* [Smart Imaging](/help/assets/imaging-faq.md)
