---
title: Download digitale middelen van [!DNL Adobe Experience Manager].
description: Leer hoe u middelen downloadt van [!DNL Adobe Experience Manager] en de downloadfunctionaliteit in- of uitschakelt.
contentOwner: AG
translation-type: tm+mt
source-git-commit: abc4821ec3720969bf1c2fb068744c07477aca46

---


# Download assets from [!DNL Adobe Experience Manager] {#download-assets-from-aem}

U kunt elementen downloaden, zoals statische en dynamische uitvoeringen. U kunt ook e-mails met koppelingen naar middelen rechtstreeks verzenden vanuit [!DNL Adobe Experience Manager Assets]. Gedownloade elementen worden gebundeld in een ZIP-bestand. Het gecomprimeerde ZIP-bestand heeft een maximale bestandsgrootte van 1 GB voor de exporttaak. U kunt maximaal 500 elementen per exporttaak gebruiken.

>[!NOTE]
>
>Ontvangers van e-mailberichten moeten lid zijn van de `dam-users` groep om toegang te krijgen tot de koppeling voor het downloaden van postadressen in het e-mailbericht. Om de elementen te kunnen downloaden, moeten de leden machtigingen hebben om workflows te starten die het downloaden van elementen activeren.

Als u elementen wilt downloaden, navigeert u naar een element, selecteert u het element en tikt u op **[!UICONTROL Downloaden]** op de werkbalk. Geef in het dialoogvenster dat verschijnt de gewenste downloadopties op.

De elementtypen Afbeeldingssets, Spin-sets, Gemengde mediasets en Carousel-sets kunnen niet worden gedownload.

![Beschikbare opties voor het downloaden van middelen van Experience Manager-middelen](assets/asset_download_dialog.png)

*Afbeelding: Beschikbare opties voor het downloaden van elementen van[!DNL Experience Manager Assets].*

Hieronder vindt u de opties Exporteren/downloaden. Dynamische uitvoeringen zijn uniek voor Dynamische media en u kunt uitvoeringen ter plekke genereren naast het element dat u hebt geselecteerd. Deze optie is alleen beschikbaar als u Dynamische media hebt ingeschakeld.

| Opties voor exporteren of downloaden | Beschrijvingen |
|---|---|
| [!UICONTROL Assets] | Selecteer deze optie om het element in de oorspronkelijke vorm te downloaden zonder dat er uitvoeringen plaatsvinden. |
| [!UICONTROL Uitvoeringen] | Een vertoning is de binaire representatie van een element. Elementen hebben een primaire representatie, namelijk die van het geüploade bestand. Zij kunnen om het even welk aantal vertegenwoordiging hebben. <br> Met deze optie kunt u de uitvoeringen selecteren die u wilt downloaden. Welke uitvoeringen beschikbaar zijn, is afhankelijk van het element dat u selecteert. |
| [!UICONTROL Dynamische uitvoeringen] | Een dynamische vertoning genereert andere uitvoeringen ter plekke. Wanneer u deze optie selecteert, selecteert u ook de uitvoeringen die u dynamisch wilt maken door een optie te selecteren in de lijst [Voorinstellingen](image-presets.md) afbeelding. <br>Bovendien kunt u de grootte en de maateenheid, de indeling, de kleurruimte, de resolutie en alle wijzigingstoetsen voor afbeeldingen selecteren (bijvoorbeeld om de afbeelding om te keren) |
| [!UICONTROL E-mail] | Er wordt een e-mailbericht verzonden naar de gebruiker. De standaard e-mailsjablonen zijn beschikbaar op de volgende locaties:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`</li></ul> De malplaatjes die u tijdens plaatsing aanpast zouden op deze plaatsen moeten aanwezig zijn: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`</li></ul>U kunt huurdersspecifieke douanesjablonen bij deze plaatsen opslaan:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`</li></ul> |
| [!UICONTROL Afzonderlijke map maken voor elk element] | Selecteer deze optie om de mappenhiërarchie te behouden tijdens het downloaden van elementen. Standaard wordt de maphiërarchie genegeerd en worden alle elementen in één map op uw lokale systeem gedownload. |

De optie Uitvoeringen van optie is beschikbaar als het element uitvoeringen heeft. De optie Subassets is beschikbaar als het element subassets bevat.

Wanneer u een map selecteert om te downloaden, wordt de volledige elementenhiërarchie onder de map gedownload. Als u elk element dat u downloadt (inclusief elementen in onderliggende mappen die onder de bovenliggende map zijn genest), in een afzonderlijke map wilt opnemen, selecteert u **[!UICONTROL Een aparte map maken voor elk element]**.

## Enable asset download servlet {#enable-asset-download-servlet}

Met de standaardservlet in [!DNL Experience Manager] kunnen geverifieerde gebruikers willekeurig grote, gelijktijdige downloadaanvragen afgeven voor het maken van ZIP-bestanden met elementen die zichtbaar zijn voor hen die de server en het netwerk kunnen overbelasten. Om potentiële risico&#39;s van Dos te verlichten die door deze eigenschap worden veroorzaakt, wordt de component `AssetDownloadServlet` OSGi onbruikbaar gemaakt door gebrek voor publiceer instanties.

Om het downloaden van activa van uw DAM toe te staan, bijvoorbeeld wanneer het gebruiken van iets zoals de Commons van het Aandeel van Activa of andere portaalachtige implementatie, laat manueel servlet via een configuratie OSGi toe. Adobe raadt u aan de toegestane downloadgrootte zo laag mogelijk in te stellen zonder dat dit van invloed is op de vereisten voor het dagelijks downloaden. Een hoge waarde kan van invloed zijn op de prestaties.

1. Maak een map met een naamgevingsconventie die zich richt op de publicatie-runtime, namelijk `config.publish`:

   `/apps/<your-app-name>/config.publish`

   Om configuratieeigenschappen voor een looppaswijze te bepalen, zie Wijzen [van de](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode) Looppas voor meer informatie.

1. Maak in de configuratiemap een nieuw bestand van het type `nt:file` genaamd `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Vul `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` met de volgende code. Hiermee stelt u een maximale grootte (in bytes) in voor het downloaden als waarde van `asset.download.prezip.maxcontentsize`. In het onderstaande voorbeeld wordt de maximale grootte van de ZIP-download ingesteld op maximaal 100 kB.

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

## Asset Download-server uitschakelen {#disable-asset-download-servlet}

De functie `Asset Download Servlet` kan worden uitgeschakeld in een [!DNL Experience Manager] publicatie-instantie door de configuratie van de verzender bij te werken om aanvragen voor het downloaden van middelen te blokkeren. servlet kan ook manueel via de console OSGi direct worden onbruikbaar gemaakt.

1. Om activa te blokkeren downloadverzoeken via een verzenderconfiguratie geef de `dispatcher.any` configuratie uit en voeg een nieuwe regel aan de [filtersectie](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#defining-a-filter)toe.

   `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

1. U kunt de component OSGi op een Publish instantie manueel onbruikbaar maken, door aan de Console te navigeren OSGi bij `<aem-host>/system/console/components`. Zoek `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet` en klik op **[!UICONTROL Uitschakelen]**.

>[!MORELIKETHIS]
>
>* [Met DRM beveiligde middelen downloaden](drm.md)
>* [Elementen downloaden met de bureaublad-app Experience Manager op de Windows- of Mac-desktop](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html)
>* [Elementen downloaden met Adobe Assets Link vanuit de ondersteunde Adobe Creative Cloud-toepassingen](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html)

