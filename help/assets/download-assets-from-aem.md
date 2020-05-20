---
title: Download digitale middelen van [!DNL Adobe Experience Manager].
description: Leer hoe u middelen downloadt van [!DNL Adobe Experience Manager] en de downloadfunctionaliteit in- of uitschakelt.
contentOwner: AG
translation-type: tm+mt
source-git-commit: 23d19d9656d61874cd00a9a2473092be0c53b8f8
workflow-type: tm+mt
source-wordcount: '755'
ht-degree: 0%

---


# Download assets from [!DNL Adobe Experience Manager] {#download-assets-from-aem}

U kunt elementen downloaden, zoals statische en dynamische uitvoeringen. U kunt ook e-mails met koppelingen naar middelen rechtstreeks verzenden vanuit [!DNL Adobe Experience Manager Assets]. Gedownloade elementen worden gebundeld in een ZIP-bestand. Het gecomprimeerde ZIP-bestand heeft een maximale bestandsgrootte van 1 GB voor de exporttaak. Er zijn maximaal 500 totale elementen per exporttaak toegestaan.

>[!NOTE]
>
>Ontvangers van e-mailberichten moeten lid zijn van de `dam-users` groep om toegang te krijgen tot de koppeling voor het downloaden van postadressen in het e-mailbericht. Om de elementen te kunnen downloaden, moeten de leden machtigingen hebben om workflows te starten die het downloaden van elementen activeren.

Als u elementen wilt downloaden, navigeert u naar een element, selecteert u het element en klikt u op **[!UICONTROL Download]** de werkbalk. Geef in het dialoogvenster dat verschijnt de gewenste downloadopties op.

De elementtypen Afbeeldingssets, Spin-sets, Gemengde mediasets en Carousel-sets kunnen niet worden gedownload.

![Beschikbare opties voor het downloaden van middelen van Experience Manager-middelen](assets/asset_download_dialog.png)

*Afbeelding: Beschikbare opties voor het downloaden van elementen van[!DNL Experience Manager Assets].*

Hieronder vindt u de beschikbare opties voor exporteren of downloaden. Dynamische uitvoeringen zijn uniek voor [!DNL Dynamic Media] aanbiedingen. Met deze optie kunt u nieuwe uitvoeringen in real-time genereren, in aanvulling op het element dat u hebt geselecteerd. De optie is alleen beschikbaar als u deze hebt [!DNL Dynamic Media] ingeschakeld.

| Opties voor exporteren of downloaden | Beschrijvingen |
|---|---|
| [!UICONTROL Assets] | Selecteer de optie om het element in de oorspronkelijke vorm zonder vertoningen te downloaden. |
| [!UICONTROL Renditions] | Een vertoning is de binaire representatie van een element. Elementen hebben een primaire representatie, namelijk die van het geüploade bestand. Zij kunnen om het even welk aantal vertegenwoordiging hebben. <br> Met deze optie kunt u de uitvoeringen selecteren die u wilt downloaden. Welke uitvoeringen beschikbaar zijn, is afhankelijk van het element dat u selecteert. |
| [!UICONTROL Dynamic Renditions] | Een dynamische vertoning genereert andere uitvoeringen in real-time. Wanneer u deze optie selecteert, selecteert u ook de uitvoeringen die u dynamisch wilt maken door een optie te selecteren in de lijst [Voorinstellingen](image-presets.md) afbeelding. <br>Bovendien kunt u de grootte en de maateenheid, de indeling, de kleurruimte, de resolutie en alle wijzigingstoetsen voor afbeeldingen selecteren (bijvoorbeeld om de afbeelding om te keren) |
| [!UICONTROL Email] | Er wordt een e-mailbericht verzonden naar de gebruiker. De standaard e-mailsjablonen zijn beschikbaar op de volgende locaties:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> De malplaatjes die u tijdens plaatsing aanpast zouden op deze plaatsen moeten aanwezig zijn: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>U kunt huurdersspecifieke douanesjablonen bij deze plaatsen opslaan:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
| [!UICONTROL Create separate folder for each asset] | Selecteer de optie om de mappenhiërarchie te behouden bij het downloaden van elementen. Standaard wordt de maphiërarchie genegeerd en worden alle elementen in één map in uw lokale bestandssysteem gedownload. |

De optie Uitvoeringen is beschikbaar als het element uitvoeringen heeft. De optie Subassets is beschikbaar als het oorspronkelijke element subassets heeft.

Wanneer u een map selecteert om te downloaden, wordt de volledige elementenhiërarchie onder de map gedownload. Selecteer **[!UICONTROL Create separate folder for each asset]**.

## Enable asset download servlet {#enable-asset-download-servlet}

Met de standaardservlet in [!DNL Experience Manager] kunnen geverifieerde gebruikers willekeurig grote, gelijktijdige downloadaanvragen afgeven voor het maken van ZIP-bestanden met elementen die zichtbaar zijn voor hen die de server en het netwerk kunnen overbelasten. Om potentiële risico&#39;s van Dos te verlichten die door deze eigenschap worden veroorzaakt, wordt de component `AssetDownloadServlet` OSGi onbruikbaar gemaakt door gebrek voor publiceer instanties.

Om het downloaden van activa van uw DAM toe te staan, bijvoorbeeld wanneer het gebruiken van iets zoals de Commons van het Aandeel van Activa of andere portaalachtige implementatie, laat manueel servlet via een configuratie OSGi toe. Adobe raadt u aan de toegestane downloadgrootte zo laag mogelijk in te stellen zonder dat dit van invloed is op de vereisten voor het dagelijks downloaden. Een hoge waarde kan van invloed zijn op de prestaties.

1. Maak een map met een naamgevingsconventie die zich richt op de publicatie-runtime (`config.publish`): `/apps/<your-app-name>/config.publish`. Zie Modi [uitvoeren als u configuratieeigenschappen voor een uitvoeringsmodus wilt definiëren](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode).

1. Maak in de configuratiemap een bestand van het type `nt:file` genaamd `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Vul `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` met de volgende code. Hiermee stelt u een maximale grootte (in bytes) in voor het downloaden als waarde van `asset.download.prezip.maxcontentsize`. In het onderstaande voorbeeld wordt de maximale grootte van de ZIP-download ingesteld op maximaal 100 kB.

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Asset Download-server uitschakelen {#disable-asset-download-servlet}

De functie `Asset Download Servlet` kan worden uitgeschakeld in een [!DNL Experience Manager] publicatie-instantie door de configuratie van de verzender bij te werken om aanvragen voor het downloaden van middelen te blokkeren. servlet kan ook manueel via de console OSGi direct worden onbruikbaar gemaakt.

1. Om activa te blokkeren downloadt verzoeken via een verzenderconfiguratie, geef de `dispatcher.any` configuratie uit en voeg een regel aan de [filtersectie](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#defining-a-filter)toe. `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

1. Schakel de component OSGi op een instantie Publish uit door aan de Console OSGi bij `http://[aem_server]:[port]/system/console/components`. te navigeren. Zoek `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet` en klik op **[!UICONTROL Disable]**.

>[!MORELIKETHIS]
>
>* [Met DRM beveiligde middelen](drm.md)downloaden.
>* [Download middelen via de Experience Manager-bureaubladtoepassing op Windows- of Mac-bureaublad](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html).
>* [Download elementen via Adobe Assets Link vanuit de ondersteunde Adobe Creative Cloud-apps](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html).

