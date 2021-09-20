---
title: Werken met Selectieve publicatie in Dynamic Media
description: Informatie over het werken met Selectieve publicatie in Dynamic Media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
exl-id: cd025e9d-6fb1-436c-9e78-795f2daaf345
feature: Publishing
source-git-commit: a5164c0c2ef175f1bf63ef911bf92df36e413a6f
workflow-type: tm+mt
source-wordcount: '2558'
ht-degree: 1%

---

# Selectieve publicatie op mapniveau in Dynamic Media configureren {#selective-publish-configure-folder}

U kunt ervoor kiezen om middelen naar of van Adobe Experience Manager of Dynamic Media op mapniveau te publiceren of de publicatie ervan ongedaan te maken. U kunt **[!UICONTROL Manage Publication]** of **[!UICONTROL Quick Publish]** gebruiken in plaats van alleen te vertrouwen op **[!UICONTROL Dynamic Media Configuration]** waarvan de instellingen algemeen zijn voor alle mappen in uw Dynamic Media-instantie.

Met selectief publiceren kunt u bijvoorbeeld werken aan elementen voor producten die nog niet actief zijn. In dat geval kan een marketingteam toegang krijgen tot afbeeldingen met slimme uitsnijdingen en dynamische vertoningen die zijn gesynchroniseerd met Dynamic Media. Ze kunnen promotiematerialen maken, zonder dat ze die middelen naar Dynamic Media hoeven te publiceren voor wereldwijde levering.

>[!IMPORTANT]
>
>Selectieve publicatie is alleen beschikbaar in de modus Dynamic Media - Scene7.

>[!NOTE]
>
>*Door elementen van en naar mappen te* kopiëren, wordt de publicatiestatus van deze elementen gewist. Wanneer u *echter elementen naar en van mappen verplaatst waarvan de mapeigenschap is ingesteld op **[!UICONTROL Selective Publish]**, blijft de publicatiestatus van deze elementen behouden.*

Als u later besluit om de **[!UICONTROL Selective Publish]** montages in een omslag te veranderen, beïnvloeden die veranderingen slechts nieuwe activa die u aan die omslag van dat punt vooruit uploadt. De publicatiestatus van bestaande elementen in de map blijft ongewijzigd totdat u deze handmatig wijzigt vanuit **[!UICONTROL Quick Publish]** of het dialoogvenster **[!UICONTROL Manage Publication]**.

De optie **[!UICONTROL Dynamic Media Publish mode]** op mapniveau is altijd standaard ingesteld op de waarde die wordt gevonden in de instelling **[!UICONTROL Publish Assets]** in **[!UICONTROL Dynamic Media Configuration]**. De volgende stappen in dit onderwerp, echter, tonen u hoe te om deze standaardwaarde op het omslagniveau (zoals die in de volgende stappen wordt beschreven) manueel te veranderen om de **[!UICONTROL Dynamic Media Configuration]** waarde met voeten te treden.

Ongeacht of u op een van de volgende twee manieren vertrouwt:

* **[!UICONTROL Publish Assets]** waarde ingesteld in  **[!UICONTROL Dynamic Media Configuration]**.
* **[!UICONTROL Dynamic Media Publish mode]** waarde ingesteld in eigenschappen op mapniveau.

U kunt **[!UICONTROL Immediately]**, **[!UICONTROL On Activation]**, of **[!UICONTROL Selective Publish]** kiezen. U kunt bijvoorbeeld de waarde **[!UICONTROL Publish Assets]** in uw **[!UICONTROL Dynamic Media Configuration]** instellen op **[!UICONTROL On Activation]**, maar de moduswaarde **[!UICONTROL Dynamic Media Publish]** op mapniveau instellen op **[!UICONTROL Selective Publish]** en omgekeerd.

Nadat u selectief publiceren in een omslag vormt, kunt u om het even welke volgend doen:

* [Publiceer selectief middelen naar Dynamic Media of Experience Manager met Publicatie](#selective-publish-manage-publication) beheren.
* [Publiceer selectief elementen van Dynamic Media of Experience Manager met Publicatie](#selective-unpublish-manage-publication) beheren.
* [Elementen publiceren naar Dynamic Media of Experience Manager met Snel publiceren](#quick-publish-aem-dm).
* [Publiceer elementen selectief of maak de publicatie ongedaan door zoekresultaten](#selective-publish-unpublish-search-results).

**Selectieve publicatie op mapniveau in Dynamic Media configureren:**

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Voer een van de volgende handelingen uit:
   * Bewerk de eigenschappen van een bestaande map - Navigeer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** naar een map waarvan u de eigenschappen wilt bewerken. Selecteer de map en selecteer **[!UICONTROL Properties]** op de werkbalk.
   * Bewerk de eigenschappen van een nieuwe map - Selecteer **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** in de rechterbovenhoek van de pagina **[!UICONTROL Create]** > **[!UICONTROL Folder]**. Voer in het dialoogvenster **[!UICONTROL Create Folder]** een titel (vereist) voor de map in en selecteer **[!UICONTROL Create]**. Selecteer de map en selecteer **[!UICONTROL Properties]** op de werkbalk.

1. Selecteer een van de volgende opties in de vervolgkeuzelijst **[!UICONTROL Sync mode]**:

   | Synchronisatiemodus | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Inherited]** | Geen expliciete synchronisatiewaarde in de map; in plaats daarvan, erft de omslag de synchronisatiewaarde van één van zijn voorouderomslagen of de standaardwijze die in uw **[!UICONTROL Dynamic Media Configuration]** wordt geplaatst. De gedetailleerde status voor **[!UICONTROL Inherited]** wordt weergegeven als knopinfo. |
   | **[!UICONTROL Sync everything in this folder subtree to Dynamic Media]** | Voor het publiceren naar Dynamic Media moet u de middelen synchroniseren met Dynamic Media. Als u deze optie selecteert, worden alle elementen in deze substructuur opgenomen die u kunt synchroniseren met Dynamic Media. De omslag-specifieke montages treden het gebrek met voeten dat in **[!UICONTROL Dynamic Media Configuration]** plaatst. |
   | **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** | Sluit alle elementen in deze substructuur uit van synchroniseren naar Dynamic Media. |

   ![Selectieve publicatie op mapniveau](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. Selecteer een optie in de vervolgkeuzelijst **[!UICONTROL Dynamic Media Publish mode]**. De optie **[!UICONTROL Dynamic Media Publish mode]** is altijd standaard ingesteld op de waarde die is ingesteld in **[!UICONTROL Dynamic Media Configuration]**. U kunt deze standaardwaarde **[!UICONTROL Dynamic Media Configuration]** echter handmatig overschrijven met een van de volgende opties.

   >[!IMPORTANT]
   >
   >Ongeacht de door u geselecteerde optie in de Dynamic Media-publicatiemodus worden eventuele updates die u later aanbrengt in een element dat *al* is gepubliceerd, onmiddellijk gepubliceerd zonder verdere actie van de gebruiker.
   >
   >Als een gepubliceerde video wordt bijgewerkt, moet deze opnieuw worden gepubliceerd om wijzigingen in de levering te weerspiegelen.

   | Dynamic Media-publicatiemodus, optie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Immediately]** | Wanneer elementen naar deze map worden geüpload, worden de elementen door het systeem in de Experience Manager ingevoerd en wordt de URL/Embed onmiddellijk weergegeven. Deze optie is alleen gekoppeld aan publicatie door Experience Managers en er is geen tussenkomst van de gebruiker nodig om elementen te publiceren.<br>Deze optie is niet  ** beschikbaar als u  **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in  **[!UICONTROL Sync mode]** de vorige stap selecteerde. |
   | **[!UICONTROL Upon Activation]** | Wanneer elementen naar deze map worden geüpload, moet u het element eerst expliciet publiceren voordat een koppeling URL/Embed wordt opgegeven. Deze optie is alleen gekoppeld aan publiceren via Experience Manager.<br>Deze optie is niet  ** beschikbaar als u  **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in  **[!UICONTROL Sync mode]** de vorige stap selecteerde. |
   | **[!UICONTROL Selective Publish]** | De activa worden gepubliceerd aan uw keuze van of Experience Manager of aan Dynamic Media voor levering in het openbare domein. Beide publicatiemethoden sluiten elkaar uit. Met andere woorden, u kunt elementen publiceren naar DMS7 zodat u functies zoals Slim uitsnijden of dynamische uitvoeringen kunt gebruiken. U kunt ook uitsluitend elementen publiceren naar Experience Manager voor een veilige voorvertoning. dezelfde activa worden *niet* gepubliceerd naar DMS7 voor levering in het publieke domein. Deze optie is niet beschikbaar als u **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in **[!UICONTROL Sync mode]** in de vorige stap selecteerde. |

1. Selecteer **[!UICONTROL Save & Close]** in de rechterbovenhoek van de pagina en selecteer **[!UICONTROL OK]** om terug te keren naar Experience Manager Assets.

## Elementen selectief publiceren naar Dynamic Media of Experience Manager met Publicatie beheren{#selective-publish-manage-publication}

Voordat u **[!UICONTROL Manage Publication]** kunt gebruiken om elementen selectief te publiceren naar Dynamic Media of Experience Manager, moet u een van de volgende opties instellen:

* De optie **[!UICONTROL Publish Assets]** in **[!UICONTROL Dynamic Media Configuration]** tot **[!UICONTROL Selective Publish]**
* Configureerde selectief publiceren op mapniveau.

Zie [Een Dynamic Media-configuratie maken](#configuring-dynamic-media-cloud-services) of [Selectieve publicatie op mapniveau in Dynamic Media configureren](#selective-publish-configure-folder)

>[!IMPORTANT]
>
>Selectieve publicatie is alleen beschikbaar in de modus Dynamic Media - Scene7.

>[!NOTE]
>
>*Door elementen van en naar mappen te* kopiëren, wordt de publicatiestatus van deze elementen gewist. Wanneer u *echter elementen naar en van mappen verplaatst waarvan de mapeigenschap is ingesteld op **[!UICONTROL Selective Publish]**, blijft de publicatiestatus van deze elementen behouden.*

**Elementen selectief publiceren naar Dynamic Media of Experience Manager met Publicatie beheren:**

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en selecteer **[!UICONTROL Manage Publication]** op de werkbalk. Gebruik **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaalde map eenvoudiger kunt controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Selecteer **[!UICONTROL Manage Publication]** op de werkbalk. Gebruik **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaald element eenvoudiger kunt controleren.

      >[!NOTE]
      >
      >Als **[!UICONTROL Manage Publication]** niet op de toolbar wordt gezien, selecteer in plaats daarvan de ellipsknoop, dan uitgezocht **[!UICONTROL Manage Publication]** van het lijstmenu.

1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** onder **[!UICONTROL Action]** het gewenste activeringstype.

   | Actie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Publish]** (naar Experience Manager) | Selecteer deze optie zodat u elementen naar de Experience Manager kunt publiceren voor een veilige voorvertoning. |
   | **[!UICONTROL Publish to Dynamic Media]** | Selecteer deze optie zodat u elementen naar Dynamic Media kunt publiceren voor levering in het publieke domein of zodat u functies zoals Slim uitsnijden of dynamische uitvoeringen kunt gebruiken.<br>Deze optie is alleen beschikbaar als  **[!UICONTROL Dynamic Media Publish mode]** deze is ingesteld  **[!UICONTROL Selective Publish]** in de eigenschappen van de map. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de publicatie in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de elementen direct te publiceren. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de elementen op een bepaalde datum en tijd te publiceren. |

1. Selecteer **[!UICONTROL Next]** in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication]**.
1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:

   * Selecteer zo nodig een of meer elementen die u uit publicatie wilt verwijderen.
   * Selecteer **[!UICONTROL Publish]** of **[!UICONTROL Publish to Dynamic Media]** in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Scope]**.
1. Selecteer **[!UICONTROL OK]**.

### Publicatie van middelen van Dynamic Media of Experience Manager selectief ongedaan maken met Publicatie beheren {#selective-unpublish-manage-publication}

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Selecteer de map en selecteer **[!UICONTROL Manage Publication]** op de werkbalk. Gebruik **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaalde map eenvoudiger kunt controleren.
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Open de map en selecteer vervolgens een of meer elementen. Selecteer **[!UICONTROL Manage Publication]** op de werkbalk. Gebruik **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaald element eenvoudiger kunt controleren.

      >[!NOTE]
      >
      >Als **[!UICONTROL Manage Publication]** niet op de toolbar wordt gezien, selecteer in plaats daarvan de ellipsknoop, dan uitgezocht **[!UICONTROL Manage Publication]** van het lijstmenu.

1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** onder **[!UICONTROL Action]** het gewenste type deactivering.

   | Actie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Unpublish]** (van Experience Manager) | Selecteer deze optie als u de publicatie van elementen in de Experience Manager ongedaan wilt maken. |
   | **[!UICONTROL Unpublish from Dynamic Media]** | Selecteer deze optie als u de publicatie van elementen uit Dynamic Media wilt opheffen.<br>Deze optie is alleen beschikbaar als  **[!UICONTROL Dynamic Media Publish mode]** deze is ingesteld  **[!UICONTROL Selective Publish]** in de eigenschappen van de map. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de deactivering in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de publicatie van de elementen direct ongedaan te maken. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de publicatie van de elementen op een bepaalde datum en tijd ongedaan te maken. |

1. Selecteer **[!UICONTROL Next]** in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication]**.
1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit het ongedaan maken van de publicatie wilt verwijderen.
   * Selecteer **[!UICONTROL Unpublish]** of **[!UICONTROL Unpublish from Dynamic Media]** in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Scope]**.
1. Selecteer **[!UICONTROL OK]**.

## Elementen publiceren naar Dynamic Media of Experience Manager met Snel publiceren {#quick-publish-aem-dm}

U kunt **[!UICONTROL Quick Publish]** voor eenvoudige gevallen van activering van elementen gebruiken. **[!UICONTROL Quick Publish]** publiceert de geselecteerde middelen onmiddellijk zonder verdere gebruikersinteractie. Vanwege deze handeling worden niet-gepubliceerde verwijzingen ook automatisch gepubliceerd.

>[!NOTE]
>
>Als u **[!UICONTROL Quick Publish]** wilt gebruiken om elementen te publiceren naar Dynamic Media of Experience Manager, moet **[!UICONTROL Selective Publish]** zijn ingeschakeld in uw **[!UICONTROL Dynamic Media Configuration]** of in de mapeigenschappen van de geselecteerde map.

**Elementen publiceren naar Dynamic Media of Experience Manager met Snel publiceren:**

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links op de pagina het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens aan de rechterkant **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en selecteer **[!UICONTROL Quick Publish]** op de werkbalk. Gebruik **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaalde map eenvoudiger kunt controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Selecteer **[!UICONTROL Quick Publish]** op de werkbalk. Gebruik **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaald element eenvoudiger kunt controleren.

      >[!NOTE]
      >
      >Als **[!UICONTROL Quick Publish]** niet op de toolbar wordt gezien, selecteer in plaats daarvan de ellipsknoop, dan uitgezocht **[!UICONTROL Quick Publish]** van het lijstmenu.

      ![Snel publiceren op mapniveau naar Dynamic Media](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Selecteer een van de volgende opties in de menulijst **[!UICONTROL Quick Publish]**.

   | Snel publiceren, optie | Wat het doet |
   | --- | --- | 
   | Publiceren naar Experience Manager | Hiermee publiceert u de geselecteerde elementen direct naar de Experience Manager. |
   | Publiceren naar Brand Portal | Hiermee publiceert u de geselecteerde elementen direct naar **[!UICONTROL Brand Portal]**.<br>Deze optie is alleen beschikbaar als de Experience Manager Assets-instantie  **[!UICONTROL Brand Portal]** al is geconfigureerd. |
   | Publiceren naar Dynamic Media | Hiermee publiceert u de geselecteerde elementen direct naar Dynamic Media.<br>Een middel moet aan Dynamic Media worden gesynchroniseerd. Indien nodig, zorg ervoor dat **[!UICONTROL Sync mode]** in de eigenschappen van een omslag reeds aan **[!UICONTROL Sync everything in this folder subtree to Dynamic Media]** wordt geplaatst. |

1. Selecteer **[!UICONTROL OK]** en selecteer **[!UICONTROL Close]**.

## Elementen selectief publiceren of de publicatie ervan ongedaan maken door middel van zoekresultaten {#selective-publish-unpublish-search-results}

In de zoekresultaten kunt u elementen uit verschillende middelenmappen met verschillende Dynamic Media-publicatie-instellingen weergeven. Wanneer u meerdere elementen selecteert in zoekresultaten en elk element verschillende Dynamic Media-instellingen voor de publicatiemodus heeft, kunt u **[!UICONTROL Manage Publication]** activeren op de werkbalk om te publiceren of te publiceren.

Zie ook [Elementen zoeken in Experience Manager](/help/assets/search-assets.md).

**Elementen selectief publiceren of verwijderen via zoekresultaten:**

1. In Experience Manager, in de upper-left hoek van de pagina, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links op de pagina het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Selecteer in de werkbalk, rechtsboven in de pagina, het pictogram Zoeken (vergrootglas).
1. Voer in het tekstveld **[!UICONTROL Type to search]** een trefwoord in en druk op **[!UICONTROL Enter]**.
1. Selecteer in de rechterbovenhoek van de pagina het pictogram **[!UICONTROL List View]**.
1. Selecteer het pictogram **[!UICONTROL Filters]** in de linkerbovenhoek van de pagina.

   ![Lijstweergave en filters in zoekresultaten](/help/assets/assets-dm/select-publish-search-result.png)

1. Vouw in het linkerdeelvenster **[!UICONTROL Status]** uit en vouw vervolgens de zoekvoorspelling **[!UICONTROL Dynamic Media]** uit.
1. Gebruik de selectievakjes **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** om de zoekresultaten verder te verfijnen op basis van de gepubliceerde status van Dynamic Media-elementen.
U kunt deze selectievakjes ook gebruiken met de zoekvoorspelling **[!UICONTROL Publish]** om de zoekresultaten van de elementen **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** Experience Manager te verfijnen.
1. Voer een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u wilt publiceren of waarvan u de publicatie ongedaan wilt maken.
   * Selecteer **[!UICONTROL Select All]** in de rechterbovenhoek van de pagina **[!UICONTROL Search Results]**.
1. Selecteer **[!UICONTROL Manage Publication]** op de werkbalk. Selecteer het ellipspictogram op de werkbalk zodat u **[!UICONTROL Manage Publication]** kunt openen.
1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** de gewenste actie.

   | Geselecteerde actie | Instelling Middelen publiceren in Dynamic Media-configuratie | Elementen zijn |
   | --- | --- | --- |
   | Publicatie | Onmiddellijk of bij activering | Gepubliceerd aan Experience Manager en Dynamic Media. |
   | Publicatie | Selectieve publicatie | Alleen gepubliceerd naar Experience Manager. |
   | Publiceren ongedaan maken | Onmiddellijk of bij activering | Niet gepubliceerd vanuit Experience Manager en Dynamic Media. |
   | Publiceren ongedaan maken | Selectieve publicatie | Niet gepubliceerd alleen vanuit Experience Manager. |
   | Publiceren naar Dynamic Media | Onmiddellijk of bij activering | Niet gepubliceerd naar Experience Manager, Dynamic Media of beide. |
   | Publiceren naar Dynamic Media | Selectieve publicatie | Alleen gepubliceerd naar Dynamic Media. |
   | Publiceren vanuit Dynamic Media ongedaan maken | Onmiddellijk of bij activering | Niet ongepubliceerd vanuit Experience Manager, Dynamic Media of beide. |
   | Publiceren vanuit Dynamic Media ongedaan maken | Selectieve publicatie | Alleen niet gepubliceerd vanuit Dynamic Media. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de deactivering in.

   | Geselecteerd schema | Wat er gebeurt |
   | --- | --- |
   | Nu | De geselecteerde actie wordt onmiddellijk uitgevoerd. |
   | Later | De geselecteerde actie wordt uitgevoerd op de geselecteerde bepaalde datum en tijd. |

1. Selecteer **[!UICONTROL Next]** in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Options]**.
1. (Optioneel) Controleer op de pagina **[!UICONTROL Manage Publication - Scope]** de kolom **[!UICONTROL Publish Target]** in de tabel voor de geselecteerde elementen.

   | Instelling Middelen publiceren in Dynamic Media-configuratie | Geselecteerde actie | Publicatiedoel |
   | --- | --- | --- |
   | Onmiddellijk of <br>Bij activering | Publicatie | Experience Manager en Dynamic Media |
   | Onmiddellijk of <br>Bij activering | Publiceren naar Dynamic Media | Geen |
   | Selectieve publicatie | Publicatie | Experience Manager |
   | Selectieve publicatie | Publiceren naar Dynamic Media |  Dynamic Media  |
   | Onmiddellijk of <br>Bij activering | Publiceren ongedaan maken | Experience Manager en Dynamic Media |
   | Onmiddellijk of <br>Bij activering | Publiceren vanuit Dynamic Media ongedaan maken | Geen |
   | Selectieve publicatie | Publiceren ongedaan maken | Experience Manager |
   | Selectieve publicatie | Publiceren vanuit Dynamic Media ongedaan maken |  Dynamic Media  |

1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit publiceren of verwijderen.
   * Selecteer **[!UICONTROL Publish]** of **[!UICONTROL Unpublish]** in de rechterbovenhoek van de pagina **[!UICONTROL Manage Publication - Scope]** om de handeling te starten.
1. Selecteer **[!UICONTROL OK]**.

## De publicatiestatus van een element controleren {#check-publish-status-of-asset}

U kunt **[!UICONTROL Timeline]** met **[!UICONTROL Card view]**, **[!UICONTROL Column View]**, of **[!UICONTROL List View]** in Experience Manager gebruiken om de publicatiestatus van een element snel te controleren.

**De publicatiestatus van een element controleren:**

1. In Experience Manager, in de upper-left hoek van de pagina, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links op de pagina het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Open in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** (onderstaande schermafbeelding geeft de **[!UICONTROL List View]** weer) een map met elementen die u hebt gepubliceerd of die u niet hebt gepubliceerd.
1. Selecteer een element, zodat dit met een vinkje wordt weergegeven. Zie onderstaande schermafbeelding.
1. Selecteer **[!UICONTROL Timeline]** in de linkerbovenhoek van de pagina in het keuzemenu. Het gebied **[!UICONTROL Status]** in het linkerpaneel toont de publicatiestatus van het geselecteerde element.
Wanneer u **[!UICONTROL List View]** gebruikt, verschijnt een extra kolom voor **[!UICONTROL Dynamic Media]** publicatiestatus.
   * In een map die is geconfigureerd voor synchronisatie met Dynamic Media, wordt standaard de **[!UICONTROL Dynamic Media]**-kolom weergegeven.
   * Als een map *not* is geconfigureerd voor synchronisatie met Dynamic Media, wordt de Dynamic Media-kolom niet weergegeven.
      ![Lijstweergave en tijdlijn](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Problemen met selectief publiceren oplossen {#selective-publish-troubleshoot}

Een middel dat niet aan Dynamic Media wordt gesynchroniseerd maar een Dynamic Media publicatieactie teweegbrengt die op het in werking treedt resulteert in het volgende foutenbericht en de oplossing:

![Selectieve publicatiefout](/help/assets/assets-dm/selective-publish-error.png)
