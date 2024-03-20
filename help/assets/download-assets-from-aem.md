---
title: Elementen downloaden
description: Leer hoe u elementen kunt downloaden van [!DNL Adobe Experience Manager] en schakelt u de downloadfunctionaliteit in of uit.
contentOwner: AG
role: User
feature: Asset Management,Asset Distribution
exl-id: 6bda9e52-5a6e-446e-99c7-96793482c190
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '828'
ht-degree: 0%

---

# Elementen downloaden van [!DNL Adobe Experience Manager] {#download-assets-from-aem}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/download-assets-from-aem.html?lang=en) |
| AEM 6,5 | Dit artikel |

U kunt elementen downloaden, zoals statische en dynamische uitvoeringen. U kunt ook e-mails met koppelingen naar middelen rechtstreeks verzenden vanuit [!DNL Adobe Experience Manager Assets]. Gedownloade elementen worden opgenomen in een ZIP-bestand. Het gecomprimeerde ZIP-bestand heeft een maximale bestandsgrootte van 1 GB voor de exporttaak. Er zijn maximaal 500 totale elementen per exporttaak toegestaan.

>[!NOTE]
>
>Elke gebruiker met leesmachtigingen op `/var/dam/share` de locatie kan toegang krijgen tot de downloadkoppeling die in het e-mailbericht wordt gedeeld.
>
>Elke gebruiker met leesmachtigingen voor `/var/dam/jobs/download` de locatie kan elementen downloaden.
>
>De elementtypen - Afbeeldingssets, Draaisets, Gemengde mediasets en Carousel-sets kunnen niet worden gedownload.

<!--
OLD content of the above NOTE, changed wrt CQDOC-18661.
>The email recipients must be members of the `dam-users` group to access the ZIP download link in the email message.
>
-->

**Voer de volgende stappen uit om elementen te downloaden:**

1. Klik in de linkerbovenhoek op het logo. Klik in het linkerspoor op **[!UICONTROL Navigation]**.
1. Op de [!UICONTROL Navigation] pagina, klikt u **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Navigeer naar een map die elementen bevat die u wilt downloaden.
1. Selecteer de map of selecteer een of meer middelen in de map.
1. Klik op de werkbalk op **[!UICONTROL Download]**.
1. Selecteer in het dialoogvenster Downloaden de gewenste downloadopties.

   | De optie Exporteren of downloaden | Beschrijving |
   |---|---|
   | **[!UICONTROL Create separate folder for each asset]** | Selecteer deze optie om elk element dat u downloadt, inclusief elementen, op te nemen in onderliggende mappen die onder de bovenliggende map van het element zijn genest in één map op uw lokale computer. Als deze optie niet standaard is geselecteerd, wordt de maphiërarchie genegeerd en worden alle elementen naar één map op uw lokale computer gedownload. |
   | **[!UICONTROL Email]** | Er wordt een e-mailbericht verzonden naar de gebruiker. De standaard e-mailsjablonen zijn beschikbaar op de volgende locaties:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> De malplaatjes die u tijdens plaatsing aanpast zijn beschikbaar bij de volgende plaatsen: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>U kunt huurdersspecifieke douanemalplaatjes bij de volgende plaatsen opslaan:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Asset(s)]** | Selecteer deze optie als u het element in de oorspronkelijke vorm zonder vertoningen wilt downloaden.<br>De optie voor subactiva is beschikbaar als het oorspronkelijke actief subactiva heeft. |
   | **[!UICONTROL Rendition(s)]** | Een vertoning is de binaire representatie van een element. Elementen hebben een primaire representatie, namelijk die van het geüploade bestand. Zij kunnen om het even welk aantal vertegenwoordiging hebben. <br> Met deze optie kunt u de uitvoeringen selecteren die u wilt downloaden. Welke uitvoeringen beschikbaar zijn, is afhankelijk van het element dat u selecteert. De optie is beschikbaar als het element uitvoeringen heeft. |
   | **[!UICONTROL Smart Crops]** | Selecteer deze optie als u alle slimme uitsnijduitvoeringen van het geselecteerde element vanuit AEM wilt downloaden. Er wordt een ZIP-bestand met de Smart Crop-uitvoeringen gemaakt en gedownload naar uw lokale computer. |
   | **[!UICONTROL Dynamic Rendition(s)]** | Selecteer deze optie als u een reeks alternatieve vertoningen in real-time wilt genereren. Wanneer u deze optie selecteert, selecteert u ook de uitvoeringen die u dynamisch wilt maken door een van de opties [Voorinstelling afbeelding](image-presets.md) lijst. <br>Bovendien kunt u de grootte en maateenheid, de indeling, de kleurruimte, de resolutie en eventuele optionele afbeeldingsaanpassingen selecteren, zoals het omkeren van de afbeelding. De optie is alleen beschikbaar als u [!DNL Dynamic Media] ingeschakeld. |

1. Klik op **[!UICONTROL Download]**.

Wanneer u een map selecteert om te downloaden, wordt de volledige elementenhiërarchie onder de map gedownload. Selecteer **[!UICONTROL Create separate folder for each asset]**.

## Enable asset download servlet {#enable-asset-download-servlet}

De standaardserver [!DNL Experience Manager] Hiermee kunnen geverifieerde gebruikers willekeurig grote, gelijktijdige downloadaanvragen afgeven voor het maken van ZIP-bestanden met elementen die zichtbaar zijn voor hen die de server en het netwerk kunnen overbelasten. Om potentiële risico&#39;s van Dos te verlichten die door deze eigenschap worden veroorzaakt, `AssetDownloadServlet` De component OSGi is standaard uitgeschakeld voor publicatie-instanties.

Om het downloaden van activa van uw DAM toe te staan, bijvoorbeeld wanneer het gebruiken van iets zoals de Commons van het Aandeel van Activa of andere portaal-als implementatie, laat manueel servlet als configuratie OSGi toe. Adobe raadt u aan de toegestane downloadgrootte zo laag mogelijk in te stellen zonder dat dit van invloed is op de dagelijkse downloadvereisten. Een hoge waarde kan de prestaties beïnvloeden.

1. Een map maken met een naamgevingsconventie die is gericht op de publicatierunmode (`config.publish`): `/apps/<your-app-name>/config.publish`. Om configuratieeigenschappen voor een looppaswijze te bepalen, zie [Modi uitvoeren](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode).
1. Maak in de configuratiemap een bestandstype `nt:file` benoemd `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config`.
1. Vullen `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` met het volgende. Hiermee stelt u een maximale grootte (in bytes) in voor het downloaden als waarde van `asset.download.prezip.maxcontentsize`. In het onderstaande voorbeeld wordt de maximale grootte van de ZIP-download ingesteld op maximaal 100 kB.

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

Standaard, voor `GET` verzoeken om bestanden te downloaden, [!DNL Experience Manager] Hiermee wordt een limiet van 50 MB opgelegd aan de downloadgrootte van het ZIP-archief. Downloads die zijn gestart via `POST` verzoeken of de gebruikersinterface worden niet beïnvloed door deze beperking.

## Asset Download-server uitschakelen {#disable-asset-download-servlet}

De `Asset Download Servlet` kan worden uitgeschakeld op [!DNL Experience Manager] Publiceer instanties door de dispatcherconfiguratie bij te werken om het even welke verzoeken van de activadownload te blokkeren. servlet kan ook manueel via de console OSGi direct worden onbruikbaar gemaakt.

1. Als u aanvragen voor het downloaden van middelen wilt blokkeren via een dispatcherconfiguratie, bewerkt u de `dispatcher.any` configuratie en voeg een regel toe aan de [filtersectie](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#defining-a-filter). `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

1. Om de component OSGi op een Publish instantie onbruikbaar te maken, heb toegang tot de Console OSGi bij `http://[aem_server]:[port]/system/console/components`. Zoeken `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet` en klik op **[!UICONTROL Disable]**.

>[!MORELIKETHIS]
>
>* [Elementen downloaden met Brand Portal](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html)
>* [Met DRM beveiligde middelen downloaden](drm.md).
>* [Elementen downloaden met de bureaubladtoepassing Experience Manager op Win- of Mac-computers](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html#download-assets).
>* [Elementen downloaden via Adobe Assets Link vanuit de ondersteunde Adobe Creative Cloud-apps](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html).
