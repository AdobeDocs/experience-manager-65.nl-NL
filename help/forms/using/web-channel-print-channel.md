---
title: Kanaal en webkanaal afdrukken
seo-title: Kanaal en webkanaal afdrukken
description: Afdrukkanaalsjablonen importeren en webkanaalsjablonen maken en inschakelen
seo-description: Afdrukkanaalsjablonen importeren en webkanaalsjablonen maken en inschakelen
uuid: 2361b1ee-c789-4a5a-9575-8b62b603da1e
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 96d2b1cc-3252-4cc7-8b06-a897cbef8599
docset: aem65
translation-type: tm+mt
source-git-commit: ce64b148ba96cc64670aaf96c1b201bafa282b98
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%

---


# Kanaal en webkanaal afdrukken{#print-channel-and-web-channel}

De interactieve Mededelingen kunnen door twee kanalen worden geleverd: afdrukken en web. Het afdrukkanaal wordt gebruikt om PDF&#39;s en papieren communicatie te maken, zoals een gedrukte brief als een herinnering voor verzekeringspremies, terwijl het webkanaal wordt gebruikt om online ervaringen te bieden, zoals een creditcardverklaring op een website.

Auteurs van interactieve communicatie kunnen elementen zoals documentfragmenten en afbeeldingen hergebruiken om zowel afdruk- als webversies van interactieve communicatie te maken.

Een van de voorwaarden voor het maken van een interactieve communicatie[ is dat de sjablonen voor afdrukken en/of webkanaal beschikbaar zijn op de server. ](../../forms/using/create-interactive-communication.md) Hoewel sjabloonauteurs de webkanaalsjabloon op AEM zelf maken, wordt de XDP-afdruksjabloon gemaakt in Adobe Forms Designer en geüpload naar de server.

## Kanaal {#printchannel} afdrukken

Het kanaal van de druk van een Interactieve Communicatie gebruikt XFA vormmalplaatje, XDP. Een XDP is ontworpen in Adobe Forms Designer. Zie [Layout Design](../../forms/using/layout-design-details.md) voor meer informatie over het maken van afdrukkanaalsjablonen. Als u een sjabloon voor een afdrukkanaal wilt gebruiken in uw interactieve communicatie, moet u de sjabloon uploaden naar de AEM Forms-server.

### Interactieve communicatiekanaalsjabloon uploaden {#upload-interactive-communication-print-channel-template}

Als u de sjabloon wilt uploaden, moet u lid zijn van de gebruikersgroep voor formulieren. Gebruik de volgende stappen om de sjabloon voor het afdrukkanaal (XDP) te uploaden naar AEM Forms:

1. Selecteer **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.

1. Tik op **[!UICONTROL Create]** > **[!UICONTROL File Upload]**.

   Navigeer en selecteer de juiste sjabloon voor het afdrukkanaal (XDP) en tik **[!UICONTROL Open]**.

## Webkanaal {#web-channel}

Sjabloonauteurs en -beheerders kunnen websjablonen maken, bewerken en inschakelen. Als u andere gebruikers wilt toestaan websjablonen te maken, moet u ze rechten geven. Voor meer informatie, zie [Gebruiker, Groep en het Beleid van de Rechten van de Toegang](/help/sites-administering/user-group-ac-admin.md).

### Webkanaalsjabloon ontwerpen {#authoring-web-channel-template}

Als u een webkanaalsjabloon wilt maken, moet u eerst een sjabloonmap maken. Nadat u een websjabloon in een sjabloonmap hebt gemaakt, moet u de sjabloon zo instellen dat gebruikers van formulieren een interactief communicatiekanaal kunnen maken op basis van de sjabloon.

Voer de volgende stappen uit om een webkanaalsjabloon te maken:

1. Maak een sjabloonmap om uw interactieve communicatiesweb-sjablonen te behouden, als u dat nog niet hebt. Zie Sjabloonmappen in [Paginasjablonen - Bewerkbaar](/help/sites-developing/page-templates-editable.md) voor meer informatie.

   1. Tik **[!UICONTROL Tools]** ![gereedschappen](assets/tools.png) > **[!UICONTROL Configuration Browser]**.
      * Zie de [Configuration Browser](/help/sites-administering/configurations.md) documentatie voor meer informatie.
   1. Tik op **[!UICONTROL Create]** in de pagina Configuration Browser.
   1. Geef in het dialoogvenster Configuratie maken een titel op voor de map, controleer **[!UICONTROL Editable Templates]** en tik **[!UICONTROL Create]**.

      De omslag wordt gecreeerd en vermeld in Browser van de Configuratie pagina.

1. Navigeer naar de juiste sjabloonmap en maak een websjabloon.

   1. Navigeer naar de desbetreffende sjabloonmap door **[!UICONTROL Tools]** > **[!UICONTROL Templates]** > **`[Folder]`** te selecteren.
   1. Tik op **[!UICONTROL Create]**.
   1. Selecteer **[!UICONTROL Interactive Communication - Web Channel]** en tik **[!UICONTROL Next]**.
   1. Voer een titel en beschrijving van een sjabloon in en tik op **[!UICONTROL Create]**.

      De sjabloon wordt gemaakt en er verschijnt een dialoogvenster.

   1. Tik **[!UICONTROL Open]** om de sjabloon te openen die u in de Sjablooneditor hebt gemaakt.

      De Sjablooneditor wordt weergegeven.

      ![webchannelsjabloon](assets/webchanneltemplate.png)

      Bij het maken of bewerken van een sjabloon zijn er verschillende aspecten die een sjabloonauteur kan definiëren. Het maken of bewerken van een sjabloon lijkt op het ontwerpen van pagina&#39;s. Zie Sjablonen bewerken - Sjabloonauteurs in [Paginasjablonen maken](/help/sites-authoring/templates.md) voor meer informatie.

1. Schakel de sjabloon in als u het gebruik van deze sjabloon voor het maken van interactieve communicatie wilt toestaan.

   1. Tik **[!UICONTROL Tools]** ![gereedschappen](assets/tools.png) > **[!UICONTROL Templates]**.
   1. Navigeer naar de desbetreffende sjabloon, selecteer deze en tik **[!UICONTROL Enable]** en tik in het waarschuwingsbericht op **[!UICONTROL Enable]**.

      Het malplaatje wordt toegelaten en zijn status wordt getoond zoals Toegelaten. Nu kunt u doorgaan met het maken van een interactieve communicatie waarin u de zojuist gemaakte sjabloon voor webkanalen kunt gebruiken.

### Kanaal afdrukken als master voor webkanaal {#print-channel-as-master-for-web-channel}

Tijdens het ontwerpen van een interactieve communicatie kunnen auteurs deze optie selecteren om het webkanaal synchroon met het afdrukkanaal te maken. Als u het afdrukkanaal gebruikt als master voor het webkanaal, weet u zeker dat de inhoud, overerving en gegevensbinding van het webkanaal worden afgeleid van het afdrukkanaal en dat de wijzigingen die in het afdrukkanaal zijn aangebracht, worden weerspiegeld in het webkanaal. De interactieve auteurs van communicatie mogen echter de overerving voor specifieke componenten in het webkanaal onderbreken, indien nodig.

![Kanaal afdrukken als ](assets/create_ic_print_master_new.png) ![hoofdwebkanaal met afdrukkanaal als master](assets/create_ic_print_master_web_new.png)

