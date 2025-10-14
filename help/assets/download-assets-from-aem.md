---
title: Elementen downloaden
description: Leer hoe te om activa van  [!DNL Adobe Experience Manager]  te downloaden en de downloadfunctionaliteit in of onbruikbaar te maken.
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
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/download-assets-from-aem.html?lang=nl-NL) |
| AEM 6,5 | Dit artikel |

U kunt elementen downloaden, zoals statische en dynamische uitvoeringen. U kunt ook e-mails met koppelingen naar elementen rechtstreeks vanuit [!DNL Adobe Experience Manager Assets] verzenden. Gedownloade elementen worden opgenomen in een ZIP-bestand. Het gecomprimeerde ZIP-bestand heeft een maximale bestandsgrootte van 1 GB voor de exporttaak. Er zijn maximaal 500 totale elementen per exporttaak toegestaan.

>[!NOTE]
>
>Elke gebruiker met leesmachtigingen op de locatie `/var/dam/share` heeft toegang tot de downloadkoppeling die in het e-mailbericht wordt gedeeld.
>
>Gebruikers die machtigingen hebben om `/var/dam/jobs/download` te lezen, kunnen elementen downloaden.
>
>De elementtypen - Afbeeldingssets, Draaisets, Gemengde mediasets en Carousel-sets kunnen niet worden gedownload.

<!--
OLD content of the above NOTE, changed wrt CQDOC-18661.
>The email recipients must be members of the `dam-users` group to access the ZIP download link in the email message.
>
-->

**om activa te downloaden, volg deze stappen:**

1. Klik in de linkerbovenhoek op het logo. Klik op **[!UICONTROL Navigation]** in het linkerspoor.
1. Klik op de pagina [!UICONTROL Navigation] op **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Navigeer naar een map die elementen bevat die u wilt downloaden.
1. Selecteer de map of selecteer een of meer middelen in de map.
1. Klik op **[!UICONTROL Download]** op de werkbalk.
1. Selecteer in het dialoogvenster Downloaden de gewenste downloadopties.

   | De optie Exporteren of downloaden | Beschrijving |
   |---|---|
   | **[!UICONTROL Create separate folder for each asset]** | Selecteer deze optie om elk element dat u downloadt, inclusief elementen, op te nemen in onderliggende mappen die onder de bovenliggende map van het element zijn genest in één map op uw lokale computer. Als deze optie niet standaard is geselecteerd, wordt de maphiërarchie genegeerd en worden alle elementen naar één map op uw lokale computer gedownload. |
   | **[!UICONTROL Email]** | Er wordt een e-mailbericht verzonden naar de gebruiker. De standaard e-mailsjablonen zijn beschikbaar op de volgende locaties:<ul><li>`/libs/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/libs/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> De malplaatjes die u tijdens plaatsing aanpast zijn beschikbaar bij de volgende plaatsen: <ul><li>`/apps/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/apps/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul>U kunt huurdersspecifieke douanemalplaatjes bij de volgende plaatsen opslaan:<ul><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/downloadasset`.</li><li>`/conf/<tenant_specific_config_root>/settings/dam/workflow/notification/email/transientworkflowcompleted`.</li></ul> |
   | **[!UICONTROL Asset(s)]** | Selecteer deze optie als u het element in de oorspronkelijke vorm zonder vertoningen wilt downloaden.<br> de subactiva optie is beschikbaar als het originele activa subactiva heeft. |
   | **[!UICONTROL Rendition(s)]** | Een vertoning is de binaire representatie van een element. Assets heeft een primaire representatie: die van het geüploade bestand. Zij kunnen om het even welk aantal vertegenwoordiging hebben. <br> Met deze optie kunt u de uitvoeringen selecteren die u wilt downloaden. Welke uitvoeringen beschikbaar zijn, is afhankelijk van het element dat u selecteert. De optie is beschikbaar als het element uitvoeringen heeft. |
   | **[!UICONTROL Smart Crops]** | Selecteer deze optie als u alle slimme uitsnijduitvoeringen van het geselecteerde element vanuit AEM wilt downloaden. Er wordt een ZIP-bestand met de Smart Crop-uitvoeringen gemaakt en gedownload naar uw lokale computer. |
   | **[!UICONTROL Dynamic Rendition(s)]** | Selecteer deze optie als u een reeks alternatieve vertoningen in real-time wilt genereren. Wanneer u deze optie selecteert, selecteert u ook de vertoningen die u dynamisch wilt tot stand brengen door uit de [&#x200B; Vooraf ingestelde Beeld &#x200B;](image-presets.md) lijst te selecteren. <br> bovendien, kunt u de grootte en de eenheid van meting, formaat, kleurenruimte, resolutie, en om het even welke facultatieve beeldbepalingen selecteren zoals het omkeren van het beeld. De optie is alleen beschikbaar als u [!DNL Dynamic Media] hebt ingeschakeld. |

1. Klik in het dialoogvenster op **[!UICONTROL Download]** .

Wanneer u een map selecteert om te downloaden, wordt de volledige elementenhiërarchie onder de map gedownload. Selecteer **[!UICONTROL Create separate folder for each asset]** als u elk element dat u downloadt (inclusief elementen in onderliggende mappen die onder de bovenliggende map zijn genest), in een afzonderlijke map wilt opnemen.

## Enable asset download servlet {#enable-asset-download-servlet}

Met de standaardservlet in [!DNL Experience Manager] kunnen geverifieerde gebruikers willekeurig grote, gelijktijdige downloadaanvragen afgeven voor het maken van ZIP-bestanden met elementen die zichtbaar zijn voor hen en die de server en het netwerk kunnen overbelasten. `AssetDownloadServlet` De component OSGi is standaard uitgeschakeld voor publicatieinstanties om potentiële DoS-risico&#39;s te beperken die door deze functie worden veroorzaakt.

Om het downloaden van activa van uw DAM toe te staan, bijvoorbeeld wanneer het gebruiken van iets zoals de Commons van het Aandeel van Activa of andere portaal-als implementatie, laat manueel servlet als configuratie OSGi toe. Adobe raadt u aan de toegestane downloadgrootte zo laag mogelijk in te stellen zonder dat dit van invloed is op de dagelijkse downloadvereisten. Een hoge waarde kan de prestaties beïnvloeden.

1. Maak een map met een naamgevingsconventie die is gericht op de publicatieruntime (`config.publish`): `/apps/<your-app-name>/config.publish` . Om configuratieeigenschappen voor een looppaswijze te bepalen, zie [&#x200B; Wijzen van de Looppas &#x200B;](/help/sites-deploying/configure-runmodes.md#defining-configuration-properties-for-a-run-mode).
1. Maak in de configuratiemap een bestand van het type `nt:file` genaamd `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` .
1. Vul `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet.config` met de volgende code. Hiermee stelt u een maximale grootte (in bytes) voor het downloaden in als de waarde `asset.download.prezip.maxcontentsize` . In het onderstaande voorbeeld wordt de maximale grootte van de ZIP-download ingesteld op maximaal 100 kB.

   ```conf
   enabled=B"true"
   asset.download.prezip.maxcontentsize=I"102400"
   ```

[!DNL Experience Manager] past standaard een limiet van 50 MB toe op de downloadgrootte van het ZIP-archief, zodat `GET` bestanden kan downloaden. Deze limiet geldt niet voor downloads die via `POST` -aanvragen of de gebruikersinterface worden gestart.

## Asset Download-server uitschakelen {#disable-asset-download-servlet}

`Asset Download Servlet` kan op een [!DNL Experience Manager] Publish-instantie worden uitgeschakeld door de configuratie van de verzender bij te werken om aanvragen voor het downloaden van middelen te blokkeren. servlet kan ook manueel via de console OSGi direct worden onbruikbaar gemaakt.

1. Om activa te blokkeren downloadverzoeken via een verzenderconfiguratie, geef de `dispatcher.any` configuratie uit en voeg een regel aan de [&#x200B; filtersectie &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=nl-NL#defining-a-filter) toe. `/0100 { /type "deny" /url "*.assetdownload.zip/assets.zip*" }`

1. Om de component OSGi op een instantie van Publish onbruikbaar te maken, heb toegang tot de Console OSGi bij `http://[aem_server]:[port]/system/console/components`. Zoek `com.day.cq.dam.core.impl.servlet.AssetDownloadServlet` en klik op **[!UICONTROL Disable]** .

>[!MORELIKETHIS]
>
>* [&#x200B; de activa van de Download gebruikend Brand Portal &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-brand-portal/using/download/brand-portal-download-assets.html?lang=nl-NL)
>* [&#x200B; Download DRM beschermde activa &#x200B;](drm.md).
>* [&#x200B; de activa van de Download gebruikend Desktop app van de Experience Manager op de Desktop van Win of van Mac &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/using.html?lang=nl-NL#download-assets).
>* [&#x200B; de activa van de Download gebruikend de Verbinding van Assets van de Adobe van binnen gesteunde apps van Adobe Creative Cloud &#x200B;](https://helpx.adobe.com/nl/enterprise/using/manage-assets-using-adobe-asset-link.html).
