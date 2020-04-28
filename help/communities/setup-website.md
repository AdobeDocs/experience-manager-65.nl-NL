---
title: Websitestructuur instellen
seo-title: Websitestructuur instellen
description: Mappen instellen
seo-description: Mappen instellen
uuid: a31edcd5-dab8-4a42-953b-1d076c2182b2
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: d18c0ece-4c4f-499c-ac94-a9aaa7f883c4
translation-type: tm+mt
source-git-commit: 6d425dcec4fab19243be9acb41c25b531a84ea74

---


# Websitestructuur instellen {#setup-website-structure}

In de onderstaande instructies worden de mappen beschreven die op de volgende locaties moeten worden gemaakt om uw website in te stellen:

* `/apps/an-scf-sandbox`

   Hier bevinden zich aangepaste toepassingen en sjablonen.

* `/etc/designs/an-scf-sandbox`

   Hier bevinden zich downloadbare ontwerpelementen.

* `/content/an-scf-sandbox`

   Hier bevinden zich de downloadbare webpagina&#39;s.

De code in deze zelfstudie vertrouwt erop dat de naam van de hoofdmap gelijk is voor de toepassing, het ontwerp en de inhoud. Als u een andere naam voor uw website kiest, vervangt u deze altijd `an-scf-sandbox` door de naam die u hebt gekozen.

>[!NOTE]
>
>Namen:
>
>* De namen die in CRXDE worden gezien zijn knooppuntnamen die de weg aan adresseerbare inhoud vormen.
>* Node names may contain spaces, but when used in an URI, the space must be encoded either as &#39;%20&#39; or &#39;+&#39;.
>* Node-namen kunnen afbreekstreepjes en onderstrepingstekens bevatten, maar deze moeten worden gecodeerd als er in een Java-bestand naar wordt verwezen als een pakketnaam. Zowel koppeltekens als onderstrepingstekens worden overgeslagen met een onderstrepingsteken gevolgd door de Unicode-waarde:
   >
   >   
   * afbreekstreepje wordt &#39;_002d&#39;
   >   * onderstrepingsteken wordt &#39;_005f&#39;


## De toepassingsmap (/apps) instellen {#setup-the-application-directory-apps}

De map /apps in de opslagplaats bevat de code met implementaties van het gedrag en de rendering van de pagina&#39;s die vanuit de map /content worden aangeboden.

De map /apps is beveiligd en niet toegankelijk voor het publiek, net als de mappen /content en /etc/designs.

1. Map maken `/apps/an-scf-sandbox` .

   Het gebruiken van **[!UICONTROL CRXDE Lite]**, in de verkenner ruit

   1. Selecteer de `/apps` map.
   1. Klik met de rechtermuisknop op **[!UICONTROL Maken]**... of trek het **[!UICONTROL Create...]** -menu.
   1. Map **[!UICONTROL maken selecteren...]**.
   1. Voer in het dialoogvenster Map **** maken `an-scf-sandbox`.
   1. Click **[!UICONTROL OK]**.

1. Submap voor **[!UICONTROL componenten]** maken.

   1. Selecteer de `/apps/an-scf-sandbox` map.
   1. Klik op **[!UICONTROL Maken > Map]** maken.
   1. Voer in het dialoogvenster Map **** maken **[!UICONTROL componenten]** in.
   1. Click **[!UICONTROL OK]**.

1. Submap voor **[!UICONTROL sjablonen]** maken.

   1. Selecteer de `/apps/an-scf-sandbox` map.
   1. Klik op **[!UICONTROL Maken > Map]** maken.
   1. Voer in het dialoogvenster Map **** maken **[!UICONTROL sjablonen]** in.
   1. Click **[!UICONTROL OK]**.
   1. Opnieuw selecteren `/apps/an-scf-sandbox`.
   1. Selecteer **[!UICONTROL Alles]** opslaan.
   Net als bij elk bewerkingsproces, kunt u dit vaak opslaan. Als u problemen ondervindt met het invoeren van gegevens, kan dit zijn omdat er een time-out is opgetreden bij uw aanmelding of omdat u vorige bewerkingen moet opslaan.

1. De structuur in het verkendervenster van CRXDE Lite zou nu iets als dit moeten kijken:

   ![chlimage_1-44](assets/chlimage_1-44.png)

## De ontwerpmap instellen (/etc/designs) {#setup-the-design-directory-etc-designs}

De map /etc/designs bevat de afbeeldingen, scripts en opmaakmodellen die samen met de pagina-inhoud moeten worden gedownload.

1. Als u het Designer-gereedschap wilt gebruiken in de klassieke gebruikersinterface, bladert u naar [https://&lt;server>:&lt;port>/miscadmin](http://localhost:4502/miscadmin).

   Opmerking: Als u CRXDE Lite gebruikt om een Knoop van type tot stand te brengen `cq:Page`, zouden het Toegangsbeheer en de Replicatie niet aan standaardmontages voor een pagina worden geplaatst.

1. Selecteer in het verkendervenster de map **[!UICONTROL Ontwerpen]** en klik vervolgens op **[!UICONTROL Nieuw]** > **[!UICONTROL Nieuwe pagina]**.

   Enter:

   * Titel: Een **[!UICONTROL SCF-sandbox]**
   * Naam: **[!UICONTROL an-scf-sandbox]**
   * Selecteer **[!UICONTROL ontwerppaginasjabloon]**
   Klik op **[!UICONTROL Maken]**.

   ![chlimage_1-45](assets/chlimage_1-45.png)

1. Vernieuw het verkennervenster als de map &quot;An SCF Sandbox&quot; niet wordt weergegeven.

1. Keer terug naar CRXDE Lite (http:// localhost:4502/crx/de) en breid /etc/designs uit om het knooppunt met de naam &quot;an-scf-sandbox&quot; te zien.

   In de rechterbenedenruit van CRXDE, kunt u het lusje van Eigenschappen, het lusje van het Controle van de Toegang en het lusje van de Replicatie bekijken om te zien wat gebruikend het Malplaatje van de Pagina van het Ontwerp werd bepaald.

   ![chlimage_1-46](assets/chlimage_1-46.png)

## De inhoudsdirectory (/inhoud) instellen {#setup-the-content-directory-content}

De map /content in de opslagmap is waar de website-inhoud zich bevindt. De paden onder /content bestaan uit de paden van de URL voor browserverzoeken.

*Nadat* de [paginasjabloon](initial-app.md#createthepagetemplate) is gemaakt als onderdeel van de oorspronkelijke toepassing, kan de eerste pagina-inhoud worden gemaakt op basis van de sjabloon.... [****](initial-app.md)
