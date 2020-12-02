---
title: Verbinding maken met Adobe Analytics en frameworks maken
seo-title: Verbinding maken met Adobe Analytics en frameworks maken
description: Leer hoe u AEM verbindt met SiteCatalyst en frameworks maakt.
seo-description: Leer hoe u AEM verbindt met SiteCatalyst en frameworks maakt.
uuid: 3820dd24-4193-42ea-aef2-4669ebfeaa9d
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: 6b545a51-3677-4ea1-ac7e-2d01ba19283e
docset: aem65
translation-type: tm+mt
source-git-commit: 8279cd590244a7f2d20cfaf1c7505a3ef57fae4a
workflow-type: tm+mt
source-wordcount: '1550'
ht-degree: 0%

---


# Verbinding maken met Adobe Analytics en frameworks maken {#connecting-to-adobe-analytics-and-creating-frameworks}

Als u webgegevens wilt bijhouden van uw AEM in Adobe Analytics, maakt u een Adobe Analytics Cloud Services-configuratie en een Adobe Analytics-framework:

* **Adobe Analytics Configuration:** de informatie over uw Adobe Analytics-account. Met de Adobe Analytics-configuratie kunnen AEM verbinding maken met Adobe Analytics. Maak een Adobe Analytics-configuratie voor elk account dat u gebruikt.
* **Adobe Analytics Framework:** Een set toewijzingen tussen eigenschappen van Adobe Analytics-rapportsuite en CQ-variabelen. Gebruik een framework om te configureren hoe uw websitegegevens uw Adobe Analytics-rapporten vullen. Frameworks zijn gekoppeld aan een Adobe Analytics-configuratie. U kunt veelvoudige kaders voor elke configuratie tot stand brengen.

Wanneer u een webpagina aan een framework koppelt, wordt de webpagina en de onderliggende pagina van die pagina bijgehouden. Paginaweergaven kunnen vervolgens worden opgehaald uit Adobe Analytics en worden weergegeven in de Sites-console.

## Vereisten {#prerequisites}

### Adobe Analytics-account {#adobe-analytics-account}

Als u AEM gegevens in Adobe Analytics wilt bijhouden, moet u een geldige Adobe Marketing Cloud Adobe Analytics-account hebben.

De Adobe Analytics-account moet:

* **Beheerdersrechten** hebben
* Wordt toegewezen aan de **Web Service Access**-gebruikersgroep.

>[!CAUTION]
>
>Het bieden van **Beheerdersrechten** (binnen Adobe Analytics) is niet genoeg om een gebruiker in staat te stellen verbinding te maken van AEM naar Adobe Analytics. De account moet ook **Web Service Access** privileges hebben.

![chlimage_1-67](assets/chlimage_1-67.png)

Voordat u verdergaat, moet u ervoor zorgen dat u zich bij Adobe Analytics kunt aanmelden. Via:

* [Aanmelden bij Adobe Experience Cloud](https://login.experiencecloud.adobe.com/exc-content/login.html)

* [Aanmelden bij Adobe Analytics](https://sc.omniture.com/login/)

### AEM configureren voor het gebruik van uw Adobe Analytics-datacenters {#configuring-aem-to-use-your-adobe-analytics-data-centers}

Adobe Analytics [datacenters](https://developer.omniture.com/en_US/content_page/concepts-terminology/c-how-is-data-stored) verzamelen, verwerken en opslaan gegevens die bij uw Adobe Analytics-rapportsuite horen. U moet AEM configureren om het datacenter te gebruiken dat als host fungeert voor uw Adobe Analytics-rapportsuite. In de volgende tabel staan de beschikbare datacenters en de bijbehorende URL.

| Datacenter | URL |
|---|---|
| San Jose | https://api.omniture.com/admin/1.4/rest/ |
| Dallas | https://api2.omniture.com/admin/1.4/rest/ |
| Londen | https://api3.omniture.com/admin/1.4/rest/ |
| Singapore | https://api4.omniture.com/admin/1.4/rest/ |
| Oregon | https://api5.omniture.com/admin/1.4/rest/ |

AEM gebruikt standaard het datacenter van San Jose (https://api.omniture.com/admin/1.4/rest/).

Gebruik de [Webconsole om de bundel OSGi te vormen](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) **Adobe AEM Analytics HTTP Client**. Voeg **Data Center URL** voor het gegevenscentrum toe dat gastheren een rapportreeks waarvoor uw AEM pagina&#39;s gegevens verzamelen.

![aa-07](assets/aa-07.png)

1. Open de webconsole in uw webbrowser. ([https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr))
1. Ga uw geloofsbrieven in om tot de console toegang te hebben.

   >[!NOTE]
   >
   >Neem contact op met de sitebeheerder om te weten te komen of u toegang hebt tot deze console.

1. Selecteer het punt van de Configuratie genoemd **Adobe AEM de Cliënt van HTTP van Analytics**.
1. Als u de URL voor een datacenter wilt toevoegen, drukt u op + naast de lijst **Datacenter-URL&#39;s** en typt u de URL in het vak.

1. Als u een URL uit de lijst wilt verwijderen, klikt u op de knop - naast de URL.
1. Klik op Opslaan.

## De verbinding met Adobe Analytics {#configuring-the-connection-to-adobe-analytics} configureren

>[!CAUTION]
>
>Vanwege beveiligingswijzigingen in de Adobe Analytics API is het niet langer mogelijk om de versie van de Activity Map te gebruiken die in AEM is opgenomen.
>
>De [ActivityMap-plug-in van Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) moet nu worden gebruikt.

## Configureren voor de Activity Map {#configuring-for-the-activity-map}

>[!CAUTION]
>
>Vanwege beveiligingswijzigingen in de Adobe Analytics API is het niet langer mogelijk om de versie van de Activity Map te gebruiken die in AEM is opgenomen.
>
>De [ActivityMap-plug-in van Adobe Analytics](https://docs.adobe.com/content/help/en/analytics/analyze/activity-map/getting-started/get-started-users/activitymap-install.html) moet nu worden gebruikt.

## Een Adobe Analytics-framework maken {#creating-a-adobe-analytics-framework}

Voor identiteitskaart van de Reeks van het Rapport (RSID) die u gebruikt, kunt u controleren welke serverinstanties (auteur, publiceert, of allebei) gegevens aan de Reeks van het Rapport bijdragen:

* **Alles**: De informatie van zowel de auteur als de publicatieinstantie vult de Reeks van het Rapport.
* **Auteur**: Alleen informatie van de auteur wordt in de rapportsuite ingevuld.
* **Publiceren**: Alleen informatie uit de publicatieversie wordt in de rapportsuite ingevuld.

>[!NOTE]
>
>Het selecteren van het type van serverinstantie beperkt geen vraag tot Adobe Analytics, het controleert slechts welke vraag RSID omvat.
>
>Een framework is bijvoorbeeld geconfigureerd om de rapportsuite *diweretail* te gebruiken en de auteur is de geselecteerde serverinstantie. Wanneer de pagina&#39;s samen met het kader worden gepubliceerd, worden de vraag nog gemaakt aan Adobe Analytics, nochtans bevatten deze vraag niet RSID. Slechts omvatten de vraag van de auteursinstantie RSID.

1. Selecteer **Navigatie**, **Gereedschappen**, **Cloud Services** en **Oudere Cloud Services**.
1. Blader naar **Adobe Analytics** en selecteer **Configuraties tonen**.
1. Klik op de koppeling **[+]** naast uw Adobe Analytics-configuratie.

1. In het **Create Kader** dialoogvenster:

   * Geef een **Titel** op.
   * U kunt optioneel de **Naam** opgeven voor het knooppunt dat de frameworkgegevens in de opslagplaats opslaat.
   * Selecteer **Adobe Analytics Framework**

   Klik **Maken**.

   Het framework wordt geopend voor bewerking.

1. Klik in de sectie **Suites rapporteren** van de zijpod (rechterkant van het hoofddeelvenster) op **Item toevoegen**. Vervolgens gebruikt u de vervolgkeuzelijst om de rapportsuite-id te selecteren (bijvoorbeeld `geometrixxauth`) waarmee het framework zal communiceren.

   >[!NOTE]
   >
   >De zoeker naar inhoud aan de linkerkant wordt gevuld met Adobe Analytics-variabelen (SiteCatalyst-variabelen) wanneer u een rapportsuite-id selecteert.

1. Dan gebruik **de drop-down Wijze van de Looppas** (naast identiteitskaart van de Reeks van het Rapport) om de serverinstanties te selecteren die u informatie naar de Reeks van het Rapport wilt verzenden.

   ![aa-framework-01](assets/aa-framework-01.png)

1. Als u het framework beschikbaar wilt maken op de publicatie-instantie van uw site, klikt u op het tabblad **Pagina** van sidekick op **Framework activeren.**

### Serverinstellingen configureren voor Adobe Analytics {#configuring-server-settings-for-adobe-analytics}

Met het raamsysteem kunt u de serverinstellingen binnen elk Adobe Analytics-framework wijzigen.

>[!CAUTION]
>
>Deze instellingen bepalen waar en hoe uw gegevens worden verzonden. Het is dus van essentieel belang dat u *niet met deze instellingen knoeit* en dat uw Adobe Analytics-vertegenwoordiger deze instellingen instelt.

Begin door het paneel te openen. Druk op de pijl-omlaag naast **Servers**:

![server_001](assets/server_001.png)

* **Trackingserver**

   * bevat de URL waarmee Adobe Analytics-aanroepen worden verzonden

      * cname - standaard de *Bedrijfsnaam* van de Adobe Analytics-account
      * d1 - komt overeen met het datacenter waarnaar de informatie wordt verzonden (kan d1, d2 of d3 zijn)
      * sc.omtr dc.net - domeinnaam

* **Secure Tracking Server**

   * Bevat dezelfde segmenten als de trackingserver
   * Dit wordt gebruikt voor het verzenden van gegevens van beveiligde pagina&#39;s (https://)

* **Naamruimte van bezoeker**

   * De naamruimte bepaalt het eerste deel van de URL voor bijhouden.
   * Als u bijvoorbeeld de naamruimte wijzigt in **CNAME**, zullen de aanroepen naar Adobe Analytics er anders uitzien als **CNAME.d1.omtr dc.net** in plaats van als standaard.

## Een pagina koppelen aan een Adobe Analytics-framework {#associating-a-page-with-a-adobe-analytics-framework}

Wanneer een pagina is gekoppeld aan een Adobe Analytics-framework, verzendt de pagina gegevens naar Adobe Analytics wanneer de pagina wordt geladen. Variabelen die op de pagina worden ingevuld, worden toegewezen aan en opgehaald uit Adobe Analytics-variabelen in het framework. Paginaweergaven worden bijvoorbeeld opgehaald uit Adobe Analytics.

Afstammingen van de pagina nemen de koppeling met het framework over. Wanneer u bijvoorbeeld de hoofdpagina van uw site aan een framework koppelt, worden alle pagina&#39;s van de site aan het framework gekoppeld.

1. Selecteer in de console **Sites** de pagina die u wilt instellen met bijhouden.
1. Open **[Pagina-eigenschappen](/help/sites-authoring/editing-page-properties.md)**, rechtstreeks vanuit de console of de pagina-editor.
1. Open het tabblad** Cloud Services**.

1. Gebruik de **Add Configuratie** drop-down om **Adobe Analytics** van de beschikbare opties te selecteren. Als er overerving is, moet u die uitschakelen voordat de kiezer beschikbaar wordt.

1. De keuzelijst voor **Adobe Analytics** wordt toegevoegd aan de beschikbare opties. Gebruik deze optie om de vereiste frameworkconfiguratie te selecteren.

1. Selecteer **Opslaan en sluiten**.
1. **[Publiceer de pagina om de pagina en om het even welke verbonden configuraties/dossiers te activeren.](/help/sites-authoring/publishing-pages.md)** 
1. De laatste stap bestaat uit het bezoeken van de pagina op de publicatie-instantie en het zoeken naar een trefwoord (bijv. een aubergine) met de component **Search**.
1. U kunt dan de vraag controleren die aan Adobe Analytics wordt gemaakt gebruikend een aangewezen hulpmiddel; bijvoorbeeld [Adobe Experience Cloud Debugger](https://docs.adobe.com/content/help/en/debugger/using/experience-cloud-debugger.html).
1. Gebruikend het verstrekte voorbeeld, zou de vraag de ingevoerde waarde (d.w.z. augplant) in eVar7 moeten bevatten en de gebeurtenislijst zou event3 moeten bevatten.

### Paginaweergaven {#page-views}

Wanneer een pagina aan een kader van Adobe Analytics wordt geassocieerd, kan het aantal paginameningen in de mening van de Lijst van de console van Plaatsen worden getoond.

Zie [Gegevens van de Analytics van de Pagina zien](/help/sites-authoring/page-analytics-using.md) voor verdere details.

### Het vormen van het Interval van de Invoer {#configuring-the-import-interval}

Vorm de aangewezen instantie van de **Adobe AEM Beheerde Opiniepeiling Configuratie** dienst:

* **Interval opiniepeiling**: Het interval, in seconden, waarmee de service paginaweergavegegevens van Adobe Analytics ophaalt.
Het standaardinterval is 43200000 ms (12 uur).

* **Inschakelen**: Schakel de service in of uit. Standaard is de service ingeschakeld.

Voor het configureren van deze OSGi-service kunt u de [Webconsole](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) of een [osgiConfig-knooppunt in de opslagruimte](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) gebruiken (de service-PID is `com.day.cq.polling.importer.impl.ManagedPollConfigImpl`).

## Adobe Analytics-configuraties en/of frameworks {#editing-adobe-analytics-configurations-and-or-frameworks} bewerken

Net als bij het maken van een Adobe Analytics-configuratie of -framework, navigeert u naar het **scherm Cloud Services** (verouderd). Selecteer **Configuraties tonen**, dan klik op de verbinding aan de specifieke configuratie u wilt bijwerken.

Wanneer u een Adobe Analytics-configuratie bewerkt, moet u ook op de knop **Bewerken** drukken wanneer deze zich op de configuratiepagina bevindt om het dialoogvenster **Component bewerken** te openen.

## Adobe Analytics-frameworks {#deleting-adobe-analytics-frameworks} verwijderen

Als u een Adobe Analytics-framework wilt verwijderen, moet u het eerst [openen voor bewerken](#editing-adobe-analytics-configurations-and-or-frameworks).

Selecteer vervolgens **Framework** verwijderen op het tabblad **Pagina** van de assistent.

