---
title: Websitestructuur instellen
description: Leer hoe u uw websitestructuur instelt, inclusief de mappen die u wilt maken.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: 1f60a0d4-a272-45e8-9742-4b706be8502e
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '516'
ht-degree: 1%

---

# Websitestructuur instellen {#setup-website-structure}

In de onderstaande instructies worden de mappen beschreven die op de volgende locaties moeten worden gemaakt om uw website in te stellen:

* `/apps/an-scf-sandbox`

  Hier bevinden zich aangepaste toepassingen en sjablonen.

* `/etc/designs/an-scf-sandbox`

  Hier bevinden zich downloadbare ontwerpelementen.

* `/content/an-scf-sandbox`

  Hier bevinden zich de downloadbare webpagina&#39;s.

De code in deze zelfstudie vertrouwt erop dat de naam van de hoofdmap gelijk is voor de toepassing, het ontwerp en de inhoud. Als u een andere naam voor uw website kiest, vervangt u `an-scf-sandbox` altijd door de naam die u hebt gekozen.

>[!NOTE]
>
>Namen:
>
>* De namen die in CRXDE worden gezien zijn knooppuntnamen die de weg aan adresseerbare inhoud vormen.
>* Node names may contain spaces, but when used in an URI, the space must be encoded either as &#39;%20&#39; or &#39;+&#39;.
>* Node-namen kunnen afbreekstreepjes en onderstrepingstekens bevatten, maar deze moeten wel worden gecodeerd als er in een Java™-bestand naar wordt verwezen als een pakketnaam. Zowel koppeltekens als onderstrepingstekens worden overgeslagen met een onderstrepingsteken gevolgd door de Unicode-waarde:
>
>   * afbreekstreepje wordt &#39;_002d&#39;
>   * onderstrepingsteken wordt &#39;_005f&#39;

## De toepassingsmap (/apps) instellen {#setup-the-application-directory-apps}

De map /apps in de opslagplaats bevat de code met implementaties van het gedrag en de rendering van de pagina&#39;s die vanuit de map /content worden aangeboden.

De map /apps is beveiligd en niet toegankelijk voor het publiek, net als de mappen /content en /etc/designs.

1. Map `/apps/an-scf-sandbox` maken.

   Werken met **[!UICONTROL CRXDE Lite]** in het deelvenster Verkenner

   1. Selecteer de map `/apps` .
   1. Klik met de rechtermuisknop **[!UICONTROL Create]** ... of trek het **[!UICONTROL Create...]** -menu omlaag.
   1. Selecteer **[!UICONTROL Create Folder...]** .
   1. Typ `an-scf-sandbox` in het dialoogvenster **[!UICONTROL Create Folder]** .
   1. Klik op **[!UICONTROL OK]**.

1. Submap **[!UICONTROL components]** maken.

   1. Selecteer de map `/apps/an-scf-sandbox` .
   1. Klik op **[!UICONTROL Create > Create Folder]**.
   1. Typ **[!UICONTROL components]** in het dialoogvenster **[!UICONTROL Create Folder]** .
   1. Klik op **[!UICONTROL OK]**.

1. Submap **[!UICONTROL templates]** maken.

   1. Selecteer de map `/apps/an-scf-sandbox` .
   1. Klik op **[!UICONTROL Create > Create Folder]**.
   1. Typ **[!UICONTROL templates]** in het dialoogvenster **[!UICONTROL Create Folder]** .
   1. Klik op **[!UICONTROL OK]**.
   1. Selecteer `/apps/an-scf-sandbox` opnieuw.
   1. Selecteer **[!UICONTROL Save All]** .

   Net als bij elk bewerkingsproces, moet u deze vaak opslaan. Als u problemen ondervindt met het invoeren van gegevens, kan dit zijn omdat er een time-out is opgetreden bij uw aanmelding of omdat u vorige bewerkingen moet opslaan.

1. De structuur in het deelvenster Verkenner van CRXDE Lite moet er nu ongeveer als volgt uitzien:

   ![ crxde-malplaatje ](assets/crxde-template.png)

## De ontwerpmap instellen (/etc/designs) {#setup-the-design-directory-etc-designs}

De map /etc/designs bevat de afbeeldingen, scripts en stijlpagina&#39;s die samen met de pagina-inhoud moeten worden gedownload.

1. Om het hulpmiddel van Designer in Klassieke UI te gebruiken, doorblader aan [ https://&lt;server>:&lt;port>/miscadmin ](http://localhost:4502/miscadmin).

   Opmerking: als u CRXDE Lite gebruikt om een knooppunt van het type `cq:Page` te maken, worden Toegangsbeheer en replicatie niet ingesteld op de standaardinstellingen voor een pagina.

1. Selecteer de map **[!UICONTROL Designs]** in het verkenner-venster en klik op **[!UICONTROL New]** > **[!UICONTROL New Page]** .

   Enter:

   * Titel: **[!UICONTROL An SCF Sandbox]**
   * Naam: **[!UICONTROL an-scf-sandbox]**
   * Selecteren **[!UICONTROL Design Page Template]**

   Klik op **[!UICONTROL Create]**.

   ![ ontwerp-malplaatje ](assets/design-template.png)

1. Vernieuw het verkennervenster als de map &quot;An SCF Sandbox&quot; niet wordt weergegeven.

1. Ga terug naar CRXDE Lite (http:// localhost:4502/crx/de) en vouw /etc/designs uit om het knooppunt met de naam &quot;an-scf-sandbox&quot; weer te geven.

   In de rechterbenedenruit van CRXDE, kunt u het lusje van Eigenschappen, het lusje van het Toegangsbeheer, en het lusje van de Replicatie bekijken om te zien wat werd bepaald gebruikend het Malplaatje van de Pagina van het Ontwerp.

   ![ crxde-configure-malplaatje ](assets/crxde-configure-template.png)

## De inhoudsdirectory (/inhoud) instellen {#setup-the-content-directory-content}

De map /content in de opslagplaats is de locatie waar de website-inhoud zich bevindt. De paden onder /content bestaan uit de paden van de URL voor browserverzoeken.

*nadat* het [ malplaatje ](initial-app.md#createthepagetemplate) als deel van de aanvankelijke toepassing wordt gecreeerd, kan de aanvankelijke paginacontent worden gecreeerd gebaseerd op het malplaatje... [**pagina**](initial-app.md).
