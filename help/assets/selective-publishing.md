---
title: Werken met Selectief publiceren in dynamische media
description: Informatie over het werken met Selectieve publicatie in dynamische media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
translation-type: tm+mt
source-git-commit: 29f91713f5760ab0b5a557b5c811ef2efee1cc61
workflow-type: tm+mt
source-wordcount: '2538'
ht-degree: 1%

---


# Selectieve publicatie op mapniveau configureren in Dynamic Media {#selective-publish-configure-folder}

U kunt ervoor kiezen om elementen naar of van AEM of Dynamic Media op mapniveau te publiceren of de publicatie ervan ongedaan te maken door **[!UICONTROL Manage Publication]** of **[!UICONTROL Quick Publish]** te gebruiken in plaats van alleen te vertrouwen op **[!UICONTROL Dynamic Media Configuration]** waarvan de instellingen algemeen zijn voor alle mappen in de instantie Dynamic Media.

Met selectief publiceren kunt u bijvoorbeeld werken aan elementen voor producten die nog niet actief zijn. In een dergelijk geval heeft een marketingteam toegang tot SmartCrop-afbeeldingen en dynamische uitvoeringen die zijn gesynchroniseerd met Dynamic Media, zodat ze promotiemateriaal kunnen maken, zonder dat ze deze elementen hoeven te publiceren naar Dynamic Media voor wereldwijde levering.

>[!IMPORTANT]
>
>Selectieve publicatie is alleen beschikbaar in de modus Dynamische media - Scene7.

>[!NOTE]
>
>*Door elementen van en naar mappen te* kopiëren, wordt de publicatiestatus van deze elementen gewist. Wanneer u *echter elementen naar en van mappen verplaatst waarvan de mapeigenschap is ingesteld op **[!UICONTROL Selective Publish]**, blijft de publicatiestatus van deze elementen behouden.*

Als u later besluit om de **[!UICONTROL Selective Publish]** montages in een omslag te veranderen, beïnvloeden die veranderingen slechts nieuwe activa die u aan die omslag van dat punt vooruit uploadt. De publicatiestatus van bestaande elementen in de map blijft ongewijzigd totdat u deze handmatig wijzigt vanuit **[!UICONTROL Quick Publish]** of het dialoogvenster **[!UICONTROL Manage Publication]**.

De optie **[!UICONTROL Dynamic Media Publish mode]** van het omslagniveau blijft altijd aan de waarde in **[!UICONTROL Publish Assets]** het plaatsen in uw **[!UICONTROL Dynamic Media Configuration.]** altijd in gebreke. De volgende stappen in dit onderwerp, echter, tonen u hoe te om deze standaardwaarde op het omslagniveau (zoals die in de volgende stappen wordt beschreven) manueel te veranderen om **[!UICONTROL Dynamic Media Configuration]** waarde met voeten te treden.

Ongeacht of u afhankelijk bent van de waarde **[!UICONTROL Publish Assets]** die is ingesteld in **[!UICONTROL Dynamic Media Configuration]** of de waarde **[!UICONTROL Dynamic Media Publish mode]** die is ingesteld in de eigenschappen op mapniveau, kunt u nog **[!UICONTROL Immediately]**, **[!UICONTROL Upon Activation]** of **[!UICONTROL Selective Publish.]** kiezen. U kunt bijvoorbeeld de waarde **[!UICONTROL Publish Assets]** in uw **[!UICONTROL Dynamic Media Configuration]** instellen op **[!UICONTROL Upon Activation]**, maar u kunt de waarde **[!UICONTROL Dynamic Media Publish]** instellen op de waarde in mapniveau tot **[!UICONTROL Selective Publish]**, vice versa, enzovoort.

Nadat u selectief publiceren in een omslag vormt, kunt u om het even welke volgend doen:

* [Publiceer selectief middelen naar Dynamic Media of AEM met Publicatie beheren.](#selective-publish-manage-publication)
* [Publiceer selectief elementen van Dynamic Media of AEM met Publicatie beheren.](#selective-unpublish-manage-publication)
* [Elementen publiceren naar dynamische media of AEM met Snel publiceren.](#quick-publish-aem-dm)
* [Publiceer elementen selectief of maak de publicatie ongedaan in de vorm van zoekresultaten.](#selective-publish-unpublish-search-results)

**Selectieve publicatie op mapniveau in Dynamic Media configureren**

1. Tik in AEM op het AEM om toegang te krijgen tot de globale navigatieconsole. Tik links op het navigatiepictogram (net boven het gereedschapspictogram) en tik op **[!UICONTROL Assets > Files.]**
1. Voer een van de volgende handelingen uit:
   * Bewerk de eigenschappen van een bestaande map - Navigeer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** naar een map waarvan u de eigenschappen wilt bewerken. Selecteer de map en tik vervolgens op de werkbalk op **[!UICONTROL Properties.]**
   * Bewerk de eigenschappen van een nieuwe map - tik **[!UICONTROL Create > Folder.]** in het dialoogvenster **[!UICONTROL Create Folder]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** in de rechterbovenhoek van de pagina op &lt;a4/> Voer in &lt;a4/> een titel (vereist) voor de map in en tik vervolgens op **[!UICONTROL Create.]** Selecteer de map, tik vervolgens op de werkbalk op **[!UICONTROL Properties.]****[!UICONTROL Card View]**

1. Selecteer een van de volgende opties in de vervolgkeuzelijst **[!UICONTROL Sync mode]**:

   | Synchronisatiemodus | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Inherited]** | Geen expliciete synchronisatiewaarde in de map; in plaats daarvan, erft de omslag de synchronisatiewaarde van één van zijn voorouderomslagen of de standaardwijze die in uw **[!UICONTROL Dynamic Media Configuration.]** wordt geplaatst de gedetailleerde status voor **[!UICONTROL Inherited]** toont als hulpmiddeluiteinde. |
   | **[!UICONTROL Sync everything in this folder sub-tree to dynamicmedia]** | Voor het publiceren naar dynamische media moet u de elementen synchroniseren met Dynamic Media. Als u deze optie selecteert, worden alle elementen in deze substructuur opgenomen voor synchronisatie met dynamische media. De omslag-specifieke montages treden het gebrek met voeten dat in **[!UICONTROL Dynamic Media Configuration.]** plaatst |
   | **[!UICONTROL Exclude everything in this folder sub-tree from dynamicmedia sync]** | Sluit alle elementen in deze substructuur uit van synchroniseren naar dynamische media. |

   ![Selectieve publicatie op mapniveau](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. Selecteer een optie in de vervolgkeuzelijst **[!UICONTROL Dynamic Media Publish mode]**. Houd er rekening mee dat de optie **[!UICONTROL Dynamic Media Publish mode]** altijd standaard de waarde heeft die is ingesteld in **[!UICONTROL Dynamic Media Configuration.]** U kunt deze standaardwaarde **[!UICONTROL Dynamic Media Configuration]** echter handmatig overschrijven met een van de volgende opties.

   >[!IMPORTANT]
   >
   >Ongeacht de optie voor dynamische media-publicatie die u selecteert, worden eventuele updates die u later aanbrengt in een element dat *al* gepubliceerd is, onmiddellijk gepubliceerd zonder verdere actie van de gebruiker.

   | Dynamische media publiceren, optie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Immediately]** | Wanneer middelen naar deze map worden geüpload, neemt het systeem de elementen in AEM en wordt de URL/Embed onmiddellijk weergegeven. Deze optie is alleen gekoppeld aan AEM publicatie en er is geen tussenkomst van de gebruiker nodig om elementen te publiceren.<br>Deze optie is niet  ** beschikbaar als u  **[!UICONTROL Exclude everything in this folder sub-tree from dynamicmedia sync]** in  **[!UICONTROL Sync mode]** de vorige stap selecteerde. |
   | **[!UICONTROL Upon Activation]** | Wanneer elementen naar deze map worden geüpload, moet u het element eerst expliciet publiceren voordat er een koppeling URL/Embed wordt opgegeven. Deze optie is alleen gekoppeld aan AEM publiceren.<br>Deze optie is niet  ** beschikbaar als u  **[!UICONTROL Exclude everything in this folder sub-tree from dynamicmedia sync]** in  **[!UICONTROL Sync mode]** de vorige stap selecteerde. |
   | **[!UICONTROL Selective Publish]** | De activa worden gepubliceerd aan uw keus van of AEM of aan Dynamische Media voor levering in het openbare domein. Beide publicatiemethoden sluiten elkaar uit.  Met andere woorden, u kunt elementen publiceren naar DMS7 zodat u functies zoals Slim uitsnijden of dynamische uitvoeringen kunt gebruiken. U kunt ook uitsluitend elementen publiceren naar AEM voor een beveiligde voorvertoning. dezelfde activa worden *niet* gepubliceerd naar DMS7 voor levering in het publieke domein. Deze optie is niet beschikbaar als u **[!UICONTROL Exclude everything in this folder sub-tree from dynamicmedia sync]** in **[!UICONTROL Sync mode]** in de vorige stap selecteerde. |

1. Tik in de rechterbovenhoek van de pagina op **[!UICONTROL Save & Close]** en tik vervolgens op **[!UICONTROL OK]** om terug te keren naar AEM Assets.

## Elementen selectief publiceren naar dynamische media of AEM met Publicatie beheren{#selective-publish-manage-publication}

Voordat u **[!UICONTROL Manage Publication]** kunt gebruiken om elementen selectief te publiceren naar Dynamic Media of om te AEM, moet u de optie **[!UICONTROL Publish Assets]** in **[!UICONTROL Dynamic Media Configuration]** instellen op **[!UICONTROL Selective Publish]** of selectieve publicatie op mapniveau configureren.

Zie [Creating a Dynamic Media Configuration](#configuring-dynamic-media-cloud-services) of [Configureer selectieve publicatie op mapniveau in Dynamic Media](#selective-publish-configure-folder)

>[!IMPORTANT]
>
>Selectieve publicatie is alleen beschikbaar in de modus Dynamische media - Scene7.

>[!NOTE]
>
>*Door elementen van en naar mappen te* kopiëren, wordt de publicatiestatus van deze elementen gewist. Wanneer u *echter elementen naar en van mappen verplaatst waarvan de mapeigenschap is ingesteld op **[!UICONTROL Selective Publish]**, blijft de publicatiestatus van deze elementen behouden.*

**Elementen selectief publiceren naar dynamische media of AEM met Publicatie beheren**

1. Tik in AEM op het AEM om toegang te krijgen tot de globale navigatieconsole. Tik links op het navigatiepictogram (net boven het gereedschapspictogram) en tik op **[!UICONTROL Assets > Files.]**
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en tik vervolgens op de werkbalk op **[!UICONTROL Manage Publication.]** Mogelijk is het handig om **[!UICONTROL List View]** te gebruiken, zodat u de publicatiestatus van een bepaalde map eenvoudiger kunt controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Tik op **[!UICONTROL Manage Publication.]** Als u **[!UICONTROL List View]** wilt gebruiken, kunt u de publicatiestatus van een bepaald element eenvoudiger controleren.

      >[!NOTE]
      >
      >Als **[!UICONTROL Manage Publication]** niet op de werkbalk wordt weergegeven, tikt u op de knop voor weglatingsteken en selecteert u **[!UICONTROL Manage Publication]** in het lijstmenu.

1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** onder **[!UICONTROL Action]** het gewenste activeringstype.

   | Actie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Publish]** (tot AEM) | Selecteer deze optie als u elementen wilt publiceren die u wilt AEM voor een beveiligde voorvertoning. |
   | **[!UICONTROL Publish to Dynamic Media]** | Selecteer deze optie om elementen naar dynamische media te publiceren voor levering in het publieke domein of zodat u functies zoals Slim uitsnijden of dynamische uitvoeringen kunt gebruiken.<br>Deze optie is alleen beschikbaar als  **[!UICONTROL Dynamic Media Publish mode]** deze is ingesteld  **[!UICONTROL Selective Publish]** in de eigenschappen van de map. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de publicatie in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de elementen direct te publiceren. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de elementen op een bepaalde datum en tijd te publiceren. |

1. Tik in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication]** op **[!UICONTROL Next.]**
1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:

   * Selecteer zo nodig een of meer elementen die u uit publicatie wilt verwijderen.
   * Tik in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Scope]** op **[!UICONTROL Publish]** of **[!UICONTROL Publish to Dynamic Media.]**
1. Tik op **[!UICONTROL OK.]**

### Publicatie van middelen via Dynamic Media selectief ongedaan maken of AEM met Publicatie beheren {#selective-unpublish-manage-publication}

1. Tik in AEM op het AEM om toegang te krijgen tot de globale navigatieconsole. Tik links op het navigatiepictogram (net boven het gereedschapspictogram) en tik op **[!UICONTROL Assets > Files.]**
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Selecteer de map en tik vervolgens op de werkbalk op **[!UICONTROL Manage Publication.]** Mogelijk is het handig om **[!UICONTROL List View]** te gebruiken, zodat u de publicatiestatus van een bepaalde map eenvoudiger kunt controleren.
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Open de map en selecteer vervolgens een of meer elementen. Tik op **[!UICONTROL Manage Publication.]** Als u **[!UICONTROL List View]** wilt gebruiken, kunt u de publicatiestatus van een bepaald element eenvoudiger controleren.

      >[!NOTE]
      >
      >Als **[!UICONTROL Manage Publication]** niet op de werkbalk wordt weergegeven, tikt u op de knop voor weglatingsteken en selecteert u **[!UICONTROL Manage Publication]** in het lijstmenu.

1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** onder **[!UICONTROL Action]** het gewenste type deactivering.

   | Actie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Unpublish]** (van AEM) | Selecteer deze optie als u de publicatie van elementen uit AEM wilt opheffen. |
   | **[!UICONTROL Unpublish from Dynamic Media]** | Selecteer deze optie als u de publicatie van elementen van Dynamic Media ongedaan wilt maken.<br>Deze optie is alleen beschikbaar als  **[!UICONTROL Dynamic Media Publish mode]** deze is ingesteld  **[!UICONTROL Selective Publish]** in de eigenschappen van de map. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de deactivering in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de publicatie van de elementen direct ongedaan te maken. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de publicatie van de elementen op een bepaalde datum en tijd ongedaan te maken. |

1. Tik in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication]** op **[!UICONTROL Next.]**
1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit het ongedaan maken van de publicatie wilt verwijderen.
   * Tik in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Scope]** op **[!UICONTROL Unpublish]** of **[!UICONTROL Unpublish from Dynamic Media.]**
1. Tik op **[!UICONTROL OK.]**

## Elementen publiceren naar dynamische media of AEM met Snel publiceren {#quick-publish-aem-dm}

U kunt **[!UICONTROL Quick Publish]** voor eenvoudige gevallen van activering van elementen gebruiken. **[!UICONTROL Quick Publish]** publiceert de geselecteerde middelen onmiddellijk zonder verdere gebruikersinteractie. Daarom worden niet-gepubliceerde verwijzingen ook automatisch gepubliceerd.

>[!NOTE]
>
>Als u **[!UICONTROL Quick Publish]** wilt gebruiken om elementen naar dynamische media of AEM te publiceren, moet **[!UICONTROL Selective Publish]** zijn ingeschakeld in uw **[!UICONTROL Dynamic Media Configuration]** of in de mapeigenschappen van de geselecteerde map.

**Elementen publiceren naar dynamische media of AEM met Snel publiceren**

1. Tik in AEM op het AEM om toegang te krijgen tot de globale navigatieconsole. Tik links op de pagina op het navigatiepictogram (net boven het pictogram Gereedschappen) en tik vervolgens rechts op de pagina op **[!UICONTROL Assets > Files.]**
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en tik vervolgens op de werkbalk op **[!UICONTROL Quick Publish.]** Mogelijk is het handig om **[!UICONTROL List View]** te gebruiken, zodat u de publicatiestatus van een bepaalde map eenvoudiger kunt controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Tik op **[!UICONTROL Quick Publish.]** Als u **[!UICONTROL List View]** wilt gebruiken, kunt u de publicatiestatus van een bepaald element eenvoudiger controleren.

      >[!NOTE]
      >
      >Als **[!UICONTROL Quick Publish]** niet op de werkbalk wordt weergegeven, tikt u op de knop voor weglatingsteken en selecteert u **[!UICONTROL Quick Publish]** in het lijstmenu.

      ![Snel publiceren op mapniveau naar dynamische media](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Selecteer een van de volgende opties in de menulijst **[!UICONTROL Quick Publish]**.

   | Snel publiceren, optie | Wat het doet |
   | --- | --- | 
   | Publiceren naar AEM | Hiermee publiceert u de geselecteerde elementen direct naar AEM. |
   | Publiceren naar Brand Portal | Hiermee publiceert u de geselecteerde elementen direct naar **[!UICONTROL Brand Portal.]**<br>Deze optie is alleen beschikbaar als uw AEM Assets-instantie al **[!UICONTROL Brand Portal]**heeft geconfigureerd. |
   | Publiceren naar dynamische media | Hiermee publiceert u de geselecteerde elementen direct naar Dynamic Media.<br>Een middel moet reeds aan Dynamische Media worden gesynchroniseerd. Indien nodig moet **[!UICONTROL Sync mode]** in de eigenschappen van een map al zijn ingesteld op **[!UICONTROL Sync everything in this folder sub-tree to dynamicmedia.]** |

1. Tik **[!UICONTROL OK]** en tik vervolgens op **[!UICONTROL Close.]**

## Elementen selectief publiceren of verwijderen via zoekresultaten {#selective-publish-unpublish-search-results}

In de zoekresultaten kunt u elementen uit verschillende elementmappen met verschillende publicatie-instellingen voor Dynamische media weergeven. Wanneer u een of meer elementen hebt geselecteerd in zoekresultaten en de elementen verschillende instellingen voor de publicatiemodus Dynamische media hebben, kunt u **[!UICONTROL Manage Publication]** vanuit de werkbalk activeren om te publiceren of de publicatie ervan ongedaan te maken.

Zie ook [Middelen zoeken in AEM.](/help/assets/search-assets.md)

**Elementen selectief publiceren of verwijderen via zoekresultaten**

1. Tik in AEM, linksboven op de pagina, op het AEM logo om toegang te krijgen tot de algemene navigatieconsole. Tik links op de pagina op het navigatiepictogram (net boven het pictogram Gereedschappen) en tik op **[!UICONTROL Assets > Files.]**
1. Tik in de werkbalk rechtsboven op de pagina op het pictogram Zoeken (vergrootglas).
1. Voer in het tekstveld **[!UICONTROL Type to search]** een trefwoord in en druk op **[!UICONTROL Enter.]**
1. Tik in de rechterbovenhoek van de pagina op het pictogram **[!UICONTROL List View]**.
1. Tik in de linkerbovenhoek van de pagina op het pictogram **[!UICONTROL Filters]**.

   ![Lijstweergave en filters in zoekresultaten](/help/assets/assets-dm/select-publish-search-result.png)

1. Vouw in het linkerdeelvenster **[!UICONTROL Status]** uit en vouw vervolgens de zoekvoorspelling **[!UICONTROL Dynamic Media]** uit.
1. Gebruik de selectievakjes **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** om de zoekresultaten verder te verfijnen op basis van de gepubliceerde status van Dynamic Media-elementen.
U kunt deze selectievakjes ook gebruiken in combinatie met de zoekvoorspelling **[!UICONTROL Publish]** om de zoekresultaten van de AEM **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** te verfijnen.
1. Voer een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u wilt publiceren of waarvan u de publicatie ongedaan wilt maken.
   * Tik in de rechterbovenhoek van de pagina **[!UICONTROL Search Results]** op **[!UICONTROL Select All.]**
1. Tik op de werkbalk op **[!UICONTROL Manage Publication.]** Mogelijk moet u tikken op het ellipsiepictogram op de werkbalk om **[!UICONTROL Manage Publication.]** te zien
1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** de gewenste actie.

   | Geselecteerde actie | Instelling Middelen publiceren in dynamische mediaconfiguratie | Elementen zijn |
   | --- | --- | --- |
   | Publicatie | Onmiddellijk of bij activering | Gepubliceerd naar AEM en dynamische media. |
   | Publicatie | Selectieve publicatie | Alleen naar AEM gepubliceerd. |
   | Publiceren ongedaan maken | Onmiddellijk of bij activering | Niet gepubliceerd via AEM en Dynamic Media. |
   | Publiceren ongedaan maken | Selectieve publicatie | Alleen niet gepubliceerd vanuit AEM. |
   | Publiceren naar dynamische media | Onmiddellijk of bij activering | Niet gepubliceerd naar AEM, of Dynamic Media, of beide. |
   | Publiceren naar dynamische media | Selectieve publicatie | Alleen gepubliceerd naar dynamische media. |
   | Publiceren van dynamische media ongedaan maken | Onmiddellijk of bij activering | Niet ongepubliceerd van AEM, of Dynamic Media, of beide. |
   | Publiceren van dynamische media ongedaan maken | Selectieve publicatie | Niet gepubliceerd met alleen Dynamic Media. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de deactivering in.

   | Geselecteerd schema | Wat er gebeurt |
   | --- | --- |
   | Nu | De geselecteerde actie wordt onmiddellijk uitgevoerd. |
   | Later | De geselecteerde actie wordt uitgevoerd op de geselecteerde bepaalde datum en tijd. |

1. Tik in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Options]** op **[!UICONTROL Next.]**
1. (Optioneel) Controleer op de pagina **[!UICONTROL Manage Publication - Scope]** de kolom **[!UICONTROL Publish Target]** in de tabel voor de geselecteerde elementen.

   | Instelling Middelen publiceren in dynamische mediaconfiguratie | Geselecteerde actie | Publicatiedoel |
   | --- | --- | --- |
   | Onmiddellijk of <br>Bij activering | Publicatie | AEM en dynamische media |
   | Onmiddellijk of <br>Bij activering | Publiceren naar dynamische media | Geen |
   | Selectieve publicatie | Publicatie | AEM |
   | Selectieve publicatie | Publiceren naar dynamische media |  Dynamic Media  |
   | Onmiddellijk of <br>Bij activering | Publiceren ongedaan maken | AEM en dynamische media |
   | Onmiddellijk of <br>Bij activering | Publiceren van dynamische media ongedaan maken | Geen |
   | Selectieve publicatie | Publiceren ongedaan maken | AEM |
   | Selectieve publicatie | Publiceren van dynamische media ongedaan maken |  Dynamic Media  |

1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit publiceren of verwijderen.
   * Tik in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Scope]** op **[!UICONTROL Publish]** of **[!UICONTROL Unpublish]** om de handeling te starten.
1. Tik op **[!UICONTROL OK.]**

## De publicatiestatus van een element {#check-publish-status-of-asset} controleren

U kunt **[!UICONTROL Timeline]** met **[!UICONTROL Card view]**, **[!UICONTROL Column View]**, of **[!UICONTROL List View]** in AEM gebruiken om de publicatiestatus van een middel snel te controleren.

**De publicatiestatus van een element controleren**

1. Tik in AEM, linksboven op de pagina, op het AEM logo om toegang te krijgen tot de algemene navigatieconsole. Tik links op de pagina op het navigatiepictogram (net boven het pictogram Gereedschappen) en tik op **[!UICONTROL Assets > Files.]**
1. Open in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** (onderstaande schermafbeelding geeft de **[!UICONTROL List View]** weer) een map met elementen die u hebt gepubliceerd of die u niet hebt gepubliceerd.
1. Selecteer een element, zodat dit met een vinkje wordt weergegeven. Zie onderstaande schermafbeelding.
1. Selecteer in de linkerbovenhoek van de pagina in het keuzemenu **[!UICONTROL Timeline.]** Het gebied **[!UICONTROL Status]** in het linkerdeelvenster toont de publicatiestatus van het geselecteerde element.
Wanneer u **[!UICONTROL List View]** gebruikt, verschijnt een extra kolom voor **[!UICONTROL Dynamic Media]** publicatiestatus.
   * Een omslag die aan synchronisatie aan Dynamische Media wordt gevormd zal **[!UICONTROL Dynamic Media]** kolom door gebrek tonen.
   * Een omslag die *not* wordt gevormd om aan Dynamische Media te synchroniseren zal niet de Dynamische kolom van Media tonen.
      ![Lijstweergave en tijdlijn](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Problemen met Selectieve publicatie {#selective-publish-troubleshoot} oplossen

Een middel dat niet aan Dynamische Media wordt gesynchroniseerd maar een Dynamische Media heeft publicatieactie teweeggebracht op het resulteert in het volgende foutenbericht en de oplossing:

![Selectieve publicatiefout](/help/assets/assets-dm/selective-publish-error.png)

