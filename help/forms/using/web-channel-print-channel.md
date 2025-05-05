---
title: Kanaal en webkanaal afdrukken
description: Afdrukkanaalsjablonen importeren en webkanaalsjablonen maken en inschakelen
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: cd7dbdac-dc76-4a1f-b850-0a9f47ae08de
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '668'
ht-degree: 0%

---

# Kanaal en webkanaal afdrukken{#print-channel-and-web-channel}

Interactieve communicatie kan via twee kanalen worden aangeboden: afdrukken en web. Het afdrukkanaal wordt gebruikt om PDF en papieren communicatie te maken, zoals een gedrukte brief als een herinnering voor verzekeringspremies, terwijl het webkanaal wordt gebruikt om online ervaringen te bieden, zoals een creditcardverklaring op een website.

Auteurs van interactieve communicatie kunnen elementen zoals documentfragmenten en afbeeldingen hergebruiken om zowel afdruk- als webversies van interactieve communicatie te maken.

Één van de eerste vereisten voor [ Creërend een Interactieve Communicatie ](../../forms/using/create-interactive-communication.md) moet de malplaatjes voor druk en/of Webkanaal hebben beschikbaar op de server. Hoewel sjabloonauteurs de webkanaalsjabloon op AEM zelf maken, wordt de XDP-afdruksjabloon gemaakt in Adobe Forms Designer en geüpload naar de server.

## Kanaal afdrukken {#printchannel}

Het kanaal van de druk van een Interactieve Communicatie gebruikt XFA vormmalplaatje, XDP. Een XDP is ontworpen in Adobe Forms Designer. Voor meer informatie bij het creëren van de malplaatjes van het drukkanaal, zie [ Ontwerp van de Lay-out ](../../forms/using/layout-design-details.md). Als u een sjabloon voor een afdrukkanaal wilt gebruiken in uw interactieve communicatie, moet u de sjabloon uploaden naar de AEM Forms-server.

### Interactieve communicatiekanaalsjabloon uploaden {#upload-interactive-communication-print-channel-template}

Als u de sjabloon wilt uploaden, moet u lid zijn van de gebruikersgroep voor formulieren. Gebruik de volgende stappen om de sjabloon voor het afdrukkanaal (XDP) te uploaden naar AEM Forms:

1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .

1. Selecteer **[!UICONTROL Create]** > **[!UICONTROL File Upload]** .

   Navigeer en selecteer de juiste sjabloon voor het afdrukkanaal (XDP) en selecteer **[!UICONTROL Open]** .

## Webkanaal {#web-channel}

Sjabloonauteurs en -beheerders kunnen websjablonen maken, bewerken en inschakelen. Als u andere gebruikers wilt toestaan websjablonen te maken, moet u ze rechten geven. Voor meer informatie, zie [ Gebruiker, Groep en het Beleid van de Rechten van de Toegang ](/help/sites-administering/user-group-ac-admin.md).

### Webkanaalsjabloon ontwerpen {#authoring-web-channel-template}

Als u een webkanaalsjabloon wilt maken, moet u eerst een sjabloonmap maken. Nadat u een websjabloon in een sjabloonmap hebt gemaakt, moet u de sjabloon zo instellen dat gebruikers van formulieren een interactief communicatiekanaal kunnen maken op basis van de sjabloon.

Voer de volgende stappen uit om een webkanaalsjabloon te maken:

1. Maak een sjabloonmap om uw interactieve communicatiesweb-sjablonen te behouden, als u dat nog niet hebt. Voor meer informatie, zie de Omslagen van het Malplaatje in [ Malplaatjes van de Pagina - editable ](/help/sites-developing/page-templates-editable.md).

   1. Selecteer **[!UICONTROL Tools]** ![ hulpmiddelen ](assets/tools.png) > **[!UICONTROL Configuration Browser]**.
      * Zie Browser van de Configuratie [&#128279;](/help/sites-administering/configurations.md) documentatie 0&rbrace; &lbrace;voor meer informatie.
   1. Selecteer **[!UICONTROL Create]** op de pagina Configuration Browser.
   1. Geef in het dialoogvenster Configuratie maken een titel op voor de map, controleer **[!UICONTROL Editable Templates]** en selecteer **[!UICONTROL Create]** .

      De omslag wordt gecreeerd en vermeld in Browser van de Configuratie pagina.

1. Navigeer naar de juiste sjabloonmap en maak een websjabloon.

   1. Navigeer naar de juiste sjabloonmap door **[!UICONTROL Tools]** > **[!UICONTROL Templates]** > **`[Folder]`** te selecteren.
   1. Selecteer **[!UICONTROL Create]** .
   1. Selecteer **[!UICONTROL Interactive Communication - Web Channel]** en selecteer **[!UICONTROL Next]** .
   1. Voer een titel en beschrijving voor de sjabloon in en selecteer vervolgens **[!UICONTROL Create]** .

      De sjabloon wordt gemaakt en er verschijnt een dialoogvenster.

   1. Selecteer **[!UICONTROL Open]** om de sjabloon te openen die u in de Sjablooneditor hebt gemaakt.

      De Sjablooneditor wordt weergegeven.

      ![ webchanneltemplate ](assets/webchanneltemplate.png)

      Bij het maken of bewerken van een sjabloon zijn er verschillende aspecten die een sjabloonauteur kan definiëren. Het maken of bewerken van een sjabloon lijkt op het ontwerpen van pagina&#39;s. Voor meer informatie, zie het Uitgeven Malplaatjes - de Auteurs van het Malplaatje in [ Creërend de Malplaatjes van de Pagina ](/help/sites-authoring/templates.md).

1. Schakel de sjabloon in als u het gebruik van deze sjabloon voor interactieve communicatie wilt toestaan.

   1. Selecteer **[!UICONTROL Tools]** ![ hulpmiddelen ](assets/tools.png) > **[!UICONTROL Templates]**.
   1. Navigeer naar de desbetreffende sjabloon, selecteer deze en selecteer **[!UICONTROL Enable]** in het waarschuwingsbericht en selecteer **[!UICONTROL Enable]** .

      Het malplaatje wordt toegelaten en zijn status wordt getoond zoals Toegelaten. Nu kunt u doorgaan met het maken van een interactieve communicatie waarin u de zojuist gemaakte sjabloon voor webkanalen kunt gebruiken.

### Kanaal afdrukken als stramien voor webkanaal {#print-channel-as-master-for-web-channel}

Tijdens het ontwerpen van een interactieve communicatie kunnen auteurs deze optie selecteren om het webkanaal synchroon met het afdrukkanaal te maken. Als u het afdrukkanaal gebruikt als stramien voor webkanalen, weet u zeker dat de inhoud, overerving en gegevensbinding van het webkanaal zijn afgeleid van het afdrukkanaal en dat de wijzigingen die in het afdrukkanaal zijn aangebracht, worden weerspiegeld in het webkanaal. De interactieve auteurs van communicatie mogen echter de overerving voor specifieke componenten in het webkanaal onderbreken, indien nodig.

![ het kanaal van de Druk als meester ](assets/create_ic_print_master_new.png) ![ kanaal van het Web met drukkanaal als meester ](assets/create_ic_print_master_web_new.png)
