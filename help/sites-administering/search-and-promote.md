---
title: Integreren met Adobe Search&Promote
description: Leer hoe u kunt integreren met Adobe Search&Promote.
uuid: 7e9384d9-9e4f-4e00-a1c9-35547de6ceb8
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
discoiquuid: aca444f6-418a-4c01-ae19-663b4e04fab9
docset: aem65
exl-id: 15f45978-a983-49a0-91cf-c7610fc37eef
source-git-commit: f4b7566abfa0a8dbb490baa0e849de6c355a3f06
workflow-type: tm+mt
source-wordcount: '849'
ht-degree: 1%

---

# Integreren met Adobe Search&amp;Promote{#integrating-with-adobe-search-promote}

Voer de volgende taken uit om de service Adobe Search&amp;Promote van uw website aan te roepen:

1. Geef de URL van de cloud op.
1. Configureer de verbinding met de service Search&amp;Promote.
1. Voeg Search&amp;Promote-componenten toe aan Sidetrap.
1. Gebruik de componenten om de inhoud te ontwerpen. (Zie [Search&amp;Promote-functies toevoegen aan een webpagina](/help/sites-authoring/search-and-promote.md).)
1. Voeg banners toe aan uw pagina&#39;s. Bannerafbeeldingen zijn gevoelig voor Search&amp;Promote-gegevens.
1. Genereer een site-overzicht voor de service Search&amp;Promote die u wilt gebruiken.

>[!NOTE]
>
>Als u Search&amp;Promote met een configuratie van de douanevolmacht gebruikt, moet u zowel de volmachtsconfiguraties van de Cliënt van HTTP vormen aangezien sommige functionaliteiten van Adobe Experience Manager 3.x APIs en sommige anderen 4.x APIs gebruiken:
>
>* 3.x is geconfigureerd met [https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x wordt geconfigureerd met [https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)

>



## De service-URL van de Search&amp;Promote wijzigen {#changing-the-search-promote-service-url}

De standaard URL die voor de dienst van de Search&amp;Promote wordt gevormd is `https://searchandpromote.omniture.com/px/`. Om de verschillende dienst te gebruiken, gebruik de console OSGi om een verschillende URL te specificeren.

1. Open de console OSGi en selecteer **[!UICONTROL Configuration]** tabel. ([https://localhost:4502/system/console/configMgr](https://localhost:4502/system/console/configMgr))
1. Selecteer het item Search&amp;Promote dag-CQ.
1. Voer de URL in het vak URI van externe server in en selecteer **[!UICONTROL Save]**.

## De verbinding met Search&amp;Promote configureren {#configuring-the-connection-to-search-promote}

Vorm één of meerdere verbindingen aan Search&amp;Promote zodat uw Web-pagina&#39;s met de dienst kunnen interactie aangaan. Als u verbinding wilt maken, hebt u de lididentificatie en het accountnummer van uw Search&amp;Promote-account nodig.

1. Navigeer in Experience Manager naar **[!UICONTROL Tools]** > **[!UICONTROL Deployment]** > selecteer **[!UICONTROL Cloud Services]**.

   Als u zich op een lokale computer bevindt, ziet de URL van het dashboard er ongeveer als volgt uit:

   [https://localhost:4502/libs/cq/core/content/tools/cloudservices.html](https://localhost:4502/libs/cq/core/content/tools/cloudservices.html)

1. Selecteer op de pagina Cloud Services de koppeling Adobe Search&amp;Promote of Search&amp;Promote.

1. Als u Adobe Search&amp;Promote voor het eerst vormt, uitgezocht **[!UICONTROL Configure Now]** om het Create paneel van de Configuratie te openen.

   Selecteer **[!UICONTROL Learn More]** voor meer informatie over Search&amp;Promote.

   ![](assets/chlimage_1-59.png)

1. Voer een **[!UICONTROL Title]** in die herkenbaar is voor auteurs van pagina&#39;s en voer een unieke **[!UICONTROL Name]** in.
1. Selecteer **[!UICONTROL Create]**.

   Ook, verschijnt de pas gecreëerde Configuratie onder **Beschikbare Configuraties** op **Cloud Services dashboard** de lijstpunt van de Search&amp;Promote van de Adobe.

   ![](assets/chlimage_1-60.png)

1. Voeg in het dialoogvenster **[!UICONTROL Edit Component]** het volgende toe aan de velden.

   * **Lid-id**
   * **Rekeningnummer**

   >[!NOTE]
   >
   >Om deze informatie **uzelf te krijgen,** moet u eerst login
   >
   >[https://searchandpromote.omniture.com/center/](https://searchandpromote.omniture.com/center/)
   >
   >
   >met uw geldige e-mail&amp;Promote referenties (e-mail/wachtwoord).
   >Vervolgens moet u in de adresbalk van uw browser naar de URL kijken die er ongeveer als volgt uitziet:
   >[](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >[https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY](https://searchandpromote.omniture.com/px/home/?sp_id=XXXXXXXX-spYYYYYYYY)
   >
   >**Waar:**
   >
   >    * **** XXXXXXXXXX komt overeen met uw** lid-id**
   >    * **** spYYYYYY komt overeen met uw  **accountnummer**


1. Selecteer **[!UICONTROL Connect To Search&Promote]**.

   Selecteer **[!UICONTROL OK]** wanneer het bericht over het succes van de verbinding wordt weergegeven.

   (Na verbinding wordt de knoptekst gewijzigd in** Opnieuw verbinden met Search&amp;Promote**.)

1. Selecteer **[!UICONTROL OK]**. De pagina Instellingen Search&amp;Promote wordt weergegeven voor de configuratie die u hebt gemaakt.

## Het datacenter configureren {#configuring-the-data-center}

Als uw Search&amp;Promote-account zich in Azië of Europa bevindt, moet u het standaarddatacenter wijzigen zodat het naar het juiste datacenter wijst (het standaarddatacenter is voor Noord-Amerikaanse accounts).

**Het datacenter configureren:**

1. Navigeer naar de webconsole op `https://localhost:4502/system/console/configMgr/com.day.cq.searchpromote.impl.SearchPromoteServiceImpl`

   ![](assets/chlimage_1-61.png)

1. Wijzig afhankelijk van de locatie van de server de URI in een van de volgende:

   * Noord-Amerika: [https://center.atomz.com/px/](https://center.atomz.com/px/)
   * EMEA: [https://center.lon5.atomz.com/px/](https://center.lon5.atomz.com/px/)
   * APAC: [https://center.sin2.atomz.com/px/](https://center.sin2.atomz.com/px/)

1. Selecteer **[!UICONTROL Save]**.

## Search&amp;Promote-componenten toevoegen aan Sidetrap {#adding-search-promote-components-to-sidekick}

Bewerk in de ontwerpmodus een **par**-component om de Search&amp;Promote-componenten in Sidetrap toe te staan. (Zie de documentatie [Components](/help/sites-developing/components.md#addinganewcomponenttotheparagraphsystemdesignmode) voor meer informatie.)

Zie [Search&amp;Promote-functies toevoegen aan een webpagina](/help/sites-authoring/search-and-promote.md) voor informatie over het gebruik van de componenten.)

## Geef de service Search&amp;Promote op die uw pagina&#39;s gebruiken {#specifying-the-search-promote-service-that-your-pages-use}

Webpagina&#39;s configureren zodat deze een specifieke Search&amp;Promote-service gebruiken. Componenten van Search&amp;Promote gebruiken automatisch de service van hun hostpagina.

Wanneer u de Search&amp;Promote-eigenschappen voor een pagina configureert, nemen alle onderliggende pagina&#39;s de instellingen over. Indien nodig, kunt u kindpagina&#39;s vormen om de geërfte montages met voeten te treden.

>[!NOTE]
>
>De de dienstverbinding moet vooraf worden gevormd. (Zie [De verbinding met Search&amp;Promote](#connection) configureren.)

1. Open het dialoogvenster **[!UICONTROL Page Properties]**. Klik bijvoorbeeld op de pagina** Websites** met de rechtermuisknop op de pagina en selecteer **[!UICONTROL Properties]**.
1. Selecteer het tabblad **[!UICONTROL Cloud Services]**.
1. Als u de overerving van configuraties van cloudservices van een bovenliggende pagina wilt uitschakelen, selecteert u het hangslotpictogram naast het overervingspad.

   ![](assets/sandpinheritpadlock.png)

1. Selecteer **[!UICONTROL Add Service]**.
1. Selecteer **[!UICONTROL Adobe Search&Promote]** en selecteer **[!UICONTROL OK]**.
1. Selecteer de verbindingsconfiguratie voor uw Search&amp;Promote-account en selecteer **OK**.

## Productfeed {#product-feed}

Met de Search&amp;Promote-integratie kunt u het volgende doen:

* Gebruik de eCommerce-API, onafhankelijk van de onderliggende repository structuur en het handelsplatform.
* Gebruik de functie Indexaansluiting van Search&amp;Promote, zodat u een productfeed in XML-indeling kunt hebben.
* Gebruik de eigenschap van de Controle van de Verre van Search&amp;Promote als u op bestelling of geplande verzoeken van de productvoer wilt uitvoeren.
* De productie van voer voor verschillende rekeningen van Search&amp;Promote, die als configuraties van de wolkendiensten worden gevormd.

Zie [Productfeed](/help/sites-administering/product-feed.md) voor meer informatie.
