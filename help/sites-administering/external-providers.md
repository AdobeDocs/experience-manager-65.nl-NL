---
title: Analyse met externe providers
description: Leer hoe te om uw eigen instantie van de Generische Fragmenten van Analytics te vormen om een nieuwe de dienstconfiguratie te bepalen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
exl-id: 9bf818f9-6e33-4557-b2e4-b0d4900f2a05
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '445'
ht-degree: 0%

---


# Analyse met externe providers {#analytics-with-external-providers}

Analyses kunnen u belangrijke en interessante informatie geven over het gebruik van uw website.

Verschillende configuraties buiten de box zijn beschikbaar voor integratie met de juiste service, bijvoorbeeld:

* [Adobe Analytics](/help/sites-administering/adobeanalytics.md)
* [Adobe Target](/help/sites-administering/target.md)

U kunt ook uw eigen instantie van de **Algemene analyseclusters** om een nieuwe de dienstconfiguratie te bepalen.

De informatie wordt vervolgens verzameld door kleine codefragmenten die aan de webpagina&#39;s worden toegevoegd. Bijvoorbeeld:

>[!CAUTION]
>
>Scripts niet opnemen in `script` -tags.

```
var _gaq = _gaq || [];
_gaq.push(['_setAccount', 'UA-XXXXX-X']);
_gaq.push(['_trackPageview']);

(function() {
    var ga = document.createElement('script'); ga.type = 'text/javascript'; ga.async = true;
    ga.src = ('https:' == document.location.protocol ? 'https://ssl' : 'https://www') + '.google-analytics.com/ga.js';
    var s = document.getElementsByTagName('script')[0]; s.parentNode.insertBefore(ga, s);
})();
```

Met dergelijke fragmenten kunnen gegevens worden verzameld en rapporten worden gegenereerd. De werkelijk verzamelde gegevens zijn afhankelijk van de provider en het gebruikte codefragment. Voorbeelden van statistieken zijn:

* hoeveel bezoekers in de loop der tijd
* hoeveel pagina&#39;s zijn bezocht
* zoektermen gebruikt
* landingspagina&#39;s

>[!CAUTION]
>
>De demosite Geometrixx-buiten is zo geconfigureerd dat de kenmerken die worden opgegeven in de Pagina-eigenschappen worden toegevoegd aan de HTML-broncode (net boven de `</html>` eindtag) in de bijbehorende `js` script.
>
>Als u uw eigen `/apps` niet overerven van de standaardpagina-component ( `/libs/foundation/components/page`) moet u (of uw ontwikkelaars) ervoor zorgen dat de overeenkomstige `js` scripts worden bijvoorbeeld opgenomen door `cq/cloudserviceconfigs/components/servicescomponents`of met een soortgelijk mechanisme.
>
>Zonder dit, zal geen van de diensten (Generic, Analytics, Doel, etc.) werken.

## Een service maken met een algemeen fragment {#creating-a-new-service-with-a-generic-snippet}

Voor de basisconfiguratie:

1. Open de **Gereedschappen** console.
1. Vouw vanuit het linkerdeelvenster uit **Configuraties van Cloud Servicen**.
1. Dubbelklikken **Generic Analytics-fragment** de pagina openen:

   ![Generic Analytics-fragment](assets/analytics_genericoverview.png)

1. Klik + om een nieuwe configuratie toe te voegen gebruikend de dialoogdoos. Wijs ten minste een naam toe, bijvoorbeeld Googles Analytics:

   ![Configuratie maken](assets/analytics_addconfig.png)

1. Klikken **Maken**, wordt het dialoogvenster Fragment direct geopend. U kunt het JavaScript-fragment dat u wilt gebruiken in het veld plakken:

   ![De component bewerken](assets/analytics_snippet.png)

1. Klikken **OK** opslaan.

## Uw nieuwe service op pagina&#39;s gebruiken {#using-your-new-service-on-pages}

Nadat u de de dienstconfiguratie hebt gecreeerd, moet u de vereiste pagina&#39;s vormen om het te gebruiken:

1. Ga naar de pagina.
1. Open de **Pagina-eigenschappen** van sidekick, dan **Cloud Servicen** tab.
1. Klikken **Service toevoegen** selecteert u vervolgens de gewenste service. Bijvoorbeeld de **Generic Analytics-fragment**:

   ![Een cloudservice toevoegen](assets/analytics_selectservice.png)

1. Klikken **OK** opslaan.
1. U bent teruggekeerd aan **Cloud Servicen** tab. De **Generic Analytics-fragment** wordt nu vermeld met het bericht `Configuration reference missing`. Gebruik de drop-down lijst om uw specifiek de dienstgeval te selecteren. Voorbeeld: google-analytics:

   ![Configuratie van cloudservice toevoegen](assets/analytics_selectspecificservice.png)

1. Klikken **OK** opslaan.

   Het fragment kan nu worden weergegeven als u de paginabron voor de pagina bekijkt.

   Nadat een hoeveelheid tijd is verstreken, kunt u de verzamelde statistieken bekijken.

   >[!NOTE]
   >
   >Als de configuratie aan een pagina in bijlage is die kindpagina&#39;s heeft, wordt de dienst ook geërft door die.
