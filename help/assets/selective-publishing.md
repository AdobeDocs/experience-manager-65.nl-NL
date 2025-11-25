---
title: Werken met Selectief publiceren in dynamische media
description: U kunt ervoor kiezen om elementen naar of van Adobe Experience Manager of Dynamic Media op mapniveau te publiceren of de publicatie ervan ongedaan te maken. U kunt ofwel Publicatie beheren of Snel publiceren gebruiken in plaats van alleen te vertrouwen op de Configuratie van dynamische media waarvan de instellingen algemeen zijn voor alle mappen in de instantie Dynamische media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
exl-id: cd025e9d-6fb1-436c-9e78-795f2daaf345
feature: Publishing
solution: Experience Manager, Experience Manager Assets
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '2598'
ht-degree: 0%

---

# Selectieve publicatie op mapniveau in Dynamic Media configureren {#selective-publish-configure-folder}

U kunt ervoor kiezen om elementen naar of van Adobe Experience Manager of Dynamic Media op mapniveau te publiceren of de publicatie ervan ongedaan te maken. U kunt **[!UICONTROL Manage Publication]** of **[!UICONTROL Quick Publish]** gebruiken in plaats van alleen te vertrouwen op de **[!UICONTROL Dynamic Media Configuration]** waarvan de instellingen algemeen gelden voor alle mappen in de instantie Dynamic Media.

Met selectief publiceren kunt u bijvoorbeeld werken aan elementen voor producten die nog niet actief zijn. In een dergelijk geval kan een marketingteam toegang krijgen tot afbeeldingen met slimme uitsnijdingen en dynamische vertoningen die zijn gesynchroniseerd met dynamische media. Ze kunnen promotiematerialen maken zonder dat ze deze middelen naar Dynamic Media hoeven te publiceren voor wereldwijde levering.

>[!IMPORTANT]
>
>Selectieve publicatie is alleen beschikbaar in de modus Dynamische media - Scene7.

>[!NOTE]
>
>*het kopiëren* activa aan en van omslagen ontruimt de publicatiestaat van die activa. Nochtans, wanneer u **&#x200B; activa aan en van omslagen verplaatst het waarvan omslagbezit aan &#x200B;** [!UICONTROL Selective Publish]** wordt geplaatst, publiceert staat van die activa wordt gehandhaafd.

Als u later besluit de **[!UICONTROL Selective Publish]** -instellingen in een map te wijzigen, hebben deze wijzigingen alleen invloed op nieuwe elementen die u vanaf dat punt uploadt naar die map. De publicatiestatus van bestaande elementen in de map blijft ongewijzigd totdat u deze handmatig wijzigt vanuit **[!UICONTROL Quick Publish]** of het dialoogvenster **[!UICONTROL Manage Publication]** .

De optie voor mapniveau **[!UICONTROL Dynamic Media Publish mode]** is altijd standaard ingesteld op de waarde die u vindt in de instelling **[!UICONTROL Publish Assets]** in de **[!UICONTROL Dynamic Media Configuration]** . De volgende stappen in dit onderwerp tonen u echter hoe u deze standaardwaarde op mapniveau (zoals beschreven in de volgende stappen) handmatig wijzigt om de waarde **[!UICONTROL Dynamic Media Configuration]** te overschrijven.

Ongeacht of u op een van de volgende twee manieren vertrouwt:

* **[!UICONTROL Publish Assets]** waarde ingesteld in **[!UICONTROL Dynamic Media Configuration]** .
* **[!UICONTROL Dynamic Media Publish mode]** -waarde ingesteld in eigenschappen op mapniveau.

U kunt **[!UICONTROL Immediately]**, **[!UICONTROL On Activation]** of **[!UICONTROL Selective Publish]** kiezen. U kunt bijvoorbeeld de waarde **[!UICONTROL Publish Assets]** in de **[!UICONTROL Dynamic Media Configuration]** op **[!UICONTROL On Activation]** instellen, maar de waarde voor **[!UICONTROL Dynamic Media Publish]** mode op mapniveau instellen op **[!UICONTROL Selective Publish]** en omgekeerd.

Nadat u selectief publiceren in een omslag vormt, kunt u om het even welke volgend doen:

* [&#x200B; publiceert selectief activa aan Dynamische Media of Experience Manager gebruikend leidt Publicatie &#x200B;](#selective-publish-manage-publication).
* [&#x200B; unpublish selectief activa van Dynamische Media of Experience Manager gebruikend leidt Publicatie &#x200B;](#selective-unpublish-manage-publication).
* [&#x200B; publiceer activa aan Dynamische Media of Experience Manager gebruikend Snel publiceren &#x200B;](#quick-publish-aem-dm).
* [&#x200B; publiceert of maakt selectief activa als onderzoeksresultaten &#x200B;](#selective-publish-unpublish-search-results) ongedaan.

**om selectieve het publiceren op het omslagniveau in Dynamische Media te vormen:**

1. Selecteer in Experience Manager het Experience Manager-logo voor toegang tot de algemene navigatieconsole. Selecteer links het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Voer een van de volgende handelingen uit:
   * Bewerk de eigenschappen van een bestaande map - Navigeer in **[!UICONTROL Card View]** , **[!UICONTROL Column View]** of **[!UICONTROL List View]** naar een map waarvan u de eigenschappen wilt bewerken. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Properties]** .
   * Bewerk de eigenschappen van een nieuwe map - In **[!UICONTROL Card View]** , **[!UICONTROL Column View]** of **[!UICONTROL List View]** , in de rechterbovenhoek van de pagina, selecteert u **[!UICONTROL Create]** > **[!UICONTROL Folder]** . Voer in het dialoogvenster **[!UICONTROL Create Folder]** een (vereiste) titel voor de map in en selecteer vervolgens **[!UICONTROL Create]** . Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Properties]** .

1. Selecteer een van de volgende opties in de vervolgkeuzelijst **[!UICONTROL Sync mode]** :

   | Synchronisatiemodus | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Inherited]** | Er staat geen expliciete synchronisatiewaarde in de map. In plaats daarvan neemt de map de synchronisatiewaarde over van een van de bovenliggende mappen of de standaardmodus die is ingesteld in de **[!UICONTROL Dynamic Media Configuration]** . De gedetailleerde status voor **[!UICONTROL Inherited]** wordt weergegeven als knopinfo. |
   | **[!UICONTROL Sync everything in this folder subtree to Dynamic Media]** | Voor het publiceren naar dynamische media moet u de elementen synchroniseren met Dynamic Media. Als u deze optie selecteert, worden alle elementen in deze substructuur opgenomen voor synchronisatie met dynamische media. De mapspecifieke instellingen overschrijven de standaardinstelling in de **[!UICONTROL Dynamic Media Configuration]** . |
   | **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** | Sluit alle elementen in deze substructuur uit van synchroniseren naar dynamische media. |

   ![&#x200B; selectief niveau van de Omslag publiceert &#x200B;](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. Selecteer een optie in de vervolgkeuzelijst **[!UICONTROL Dynamic Media Publish mode]** . De optie **[!UICONTROL Dynamic Media Publish mode]** is altijd standaard ingesteld op de waarde die is ingesteld in **[!UICONTROL Dynamic Media Configuration]** . U kunt deze standaardwaarde voor **[!UICONTROL Dynamic Media Configuration]** echter handmatig overschrijven met een van de volgende opties.

   >[!IMPORTANT]
   >
   >Ongeacht de Dynamische media publiceer wijzeoptie uitgezocht u, om het even welke updates u later aan activa maakt die *reeds* gepubliceerd is, worden die updates onmiddellijk gepubliceerd zonder enige verdere gebruikersactie.
   >
   >Als een gepubliceerde video wordt bijgewerkt, moet deze opnieuw worden gepubliceerd om wijzigingen in de levering te weerspiegelen.

   | Dynamische media publiceren, optie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Immediately]** | Wanneer middelen naar deze map worden geüpload, neemt het systeem de elementen op in Experience Manager en wordt de URL/Embed onmiddellijk weergegeven. Deze optie is alleen gekoppeld aan publicatie in Experience Manager en er is geen tussenkomst van de gebruiker nodig om elementen te publiceren.<br> Deze optie is *niet* beschikbaar als u **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in **[!UICONTROL Sync mode]** in de vorige stap selecteerde. |
   | **[!UICONTROL Upon Activation]** | Wanneer elementen naar deze map worden geüpload, moet u het element eerst expliciet publiceren voordat een koppeling URL/Embed wordt opgegeven. Deze optie is alleen gekoppeld aan Experience Manager-publicaties.<br> Deze optie is *niet* beschikbaar als u **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in **[!UICONTROL Sync mode]** in de vorige stap selecteerde. |
   | **[!UICONTROL Selective Publish]** | Assets wordt naar keuze van Experience Manager of Dynamic Media gepubliceerd voor levering in het publieke domein. Beide publicatiemethoden sluiten elkaar uit. Met andere woorden, u kunt elementen publiceren naar DMS7 zodat u functies zoals Slim uitsnijden of dynamische uitvoeringen kunt gebruiken. Of, kunt u activa uitsluitend aan Experience Manager voor veilige voorproef publiceren; die zelfde activa zijn *niet* gepubliceerd aan DMS7 voor levering in het openbare domein. Deze optie is niet beschikbaar als u in de vorige stap **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in **[!UICONTROL Sync mode]** hebt geselecteerd. |

1. Selecteer in de rechterbovenhoek van de pagina **[!UICONTROL Save & Close]** en selecteer vervolgens **[!UICONTROL OK]** om terug te keren naar Experience Manager Assets.

## Elementen selectief publiceren naar Dynamic Media of Experience Manager met Publicatie beheren{#selective-publish-manage-publication}

Voordat u **[!UICONTROL Manage Publication]** kunt gebruiken om elementen selectief te publiceren naar Dynamic Media of Experience Manager, moet u een van de volgende opties instellen:

* De optie **[!UICONTROL Publish Assets]** in **[!UICONTROL Dynamic Media Configuration]** tot **[!UICONTROL Selective Publish]**
* Configureerde selectieve publicatie op mapniveau.

Zie [&#x200B; een Dynamische configuratie van Media &#x200B;](#configuring-dynamic-media-cloud-services) of [&#x200B; vormen selectief het publiceren op het omslagniveau in Dynamische Media &#x200B;](#selective-publish-configure-folder)

>[!IMPORTANT]
>
>Selectieve publicatie is alleen beschikbaar in de modus Dynamische media - Scene7.

>[!NOTE]
>
>*het kopiëren* activa aan en van omslagen ontruimt de publicatiestaat van die activa. Nochtans, wanneer u **&#x200B; activa aan en van omslagen verplaatst het waarvan omslagbezit aan &#x200B;** [!UICONTROL Selective Publish]** wordt geplaatst, publiceert staat van die activa wordt gehandhaafd.

**om activa aan Dynamische Media of Experience Manager selectief te publiceren gebruikend Manage Publication:**

1. Selecteer in Experience Manager het Experience Manager-logo voor toegang tot de algemene navigatieconsole. Selecteer links het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Manage Publication]** . Gebruik **[!UICONTROL List View]** om de publicatiestatus van een bepaalde map gemakkelijker te kunnen controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Selecteer **[!UICONTROL Manage Publication]** op de werkbalk. Gebruik **[!UICONTROL List View]** om de publicatiestatus van een bepaald element gemakkelijker te kunnen controleren.

     >[!NOTE]
     >
     >Als **[!UICONTROL Manage Publication]** niet op de werkbalk wordt weergegeven, selecteert u de knop voor weglatingsteken en selecteert u vervolgens **[!UICONTROL Manage Publication]** in het lijstmenu.

1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** onder **[!UICONTROL Action]** het gewenste activeringstype.

   | Handeling | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Publish]** (naar Experience Manager) | Selecteer deze optie zodat u elementen naar Experience Manager kunt publiceren voor een veilige voorvertoning. |
   | **[!UICONTROL Publish to Dynamic Media]** | Selecteer deze optie zodat u elementen naar dynamische media kunt publiceren voor levering in het openbare domein of zodat u functies zoals Slim uitsnijden of dynamische uitvoeringen kunt gebruiken.<br> Deze optie is beschikbaar slechts als **[!UICONTROL Dynamic Media Publish mode]** aan **[!UICONTROL Selective Publish]** in de eigenschappen van de omslag wordt geplaatst. |

1. Stel onder **[!UICONTROL Schedule]** de tijdinstelling van de publicatie in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de elementen direct te publiceren. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de elementen op een bepaalde datum en tijd te publiceren. |

1. Selecteer **[!UICONTROL Manage Publication]** in de rechterbovenhoek van de pagina **[!UICONTROL Next]** .
1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:

   * Selecteer zo nodig een of meer elementen die u uit publicatie wilt verwijderen.
   * Selecteer **[!UICONTROL Manage Publication - Scope]** of **[!UICONTROL Publish]** in de rechterbovenhoek van de pagina **[!UICONTROL Publish to Dynamic Media]** .
1. Selecteer **[!UICONTROL OK]** .

### Publicatie van middelen van Dynamic Media of Experience Manager selectief ongedaan maken met Publicatie beheren {#selective-unpublish-manage-publication}

1. Selecteer in Experience Manager het Experience Manager-logo voor toegang tot de algemene navigatieconsole. Selecteer links het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Manage Publication]** . Gebruik **[!UICONTROL List View]** om de publicatiestatus van een bepaalde map gemakkelijker te kunnen controleren.
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Open de map en selecteer vervolgens een of meer elementen. Selecteer **[!UICONTROL Manage Publication]** op de werkbalk. Gebruik **[!UICONTROL List View]** om de publicatiestatus van een bepaald element gemakkelijker te kunnen controleren.

     >[!NOTE]
     >
     >Als **[!UICONTROL Manage Publication]** niet op de werkbalk wordt weergegeven, selecteert u de knop voor weglatingsteken en selecteert u vervolgens **[!UICONTROL Manage Publication]** in het lijstmenu.

1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** onder **[!UICONTROL Action]** het gewenste type deactivering.

   | Handeling | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Unpublish]** (uit Experience Manager) | Selecteer deze optie als u de publicatie van elementen uit Experience Manager wilt opheffen. |
   | **[!UICONTROL Unpublish from Dynamic Media]** | Selecteer deze optie als u de publicatie van elementen op dynamische media ongedaan wilt maken.<br> Deze optie is beschikbaar slechts als **[!UICONTROL Dynamic Media Publish mode]** aan **[!UICONTROL Selective Publish]** in de eigenschappen van de omslag wordt geplaatst. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de deactivering in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de publicatie van de elementen direct ongedaan te maken. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de publicatie van de elementen op een bepaalde datum en tijd ongedaan te maken. |

1. Selecteer **[!UICONTROL Manage Publication]** in de rechterbovenhoek van de pagina **[!UICONTROL Next]** .
1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit het ongedaan maken van de publicatie wilt verwijderen.
   * Selecteer **[!UICONTROL Manage Publication - Scope]** of **[!UICONTROL Unpublish]** in de rechterbovenhoek van de pagina **[!UICONTROL Unpublish from Dynamic Media]** .
1. Selecteer **[!UICONTROL OK]** .

## Elementen publiceren naar Dynamic Media of Experience Manager met Snel publiceren {#quick-publish-aem-dm}

U kunt **[!UICONTROL Quick Publish]** gebruiken voor eenvoudige gevallen van activering van elementen. **[!UICONTROL Quick Publish]** publiceert de geselecteerde middelen onmiddellijk zonder verdere gebruikersinteractie. Vanwege deze handeling worden niet-gepubliceerde verwijzingen ook automatisch gepubliceerd.

>[!NOTE]
>
>Als u **[!UICONTROL Quick Publish]** wilt gebruiken om elementen te publiceren naar Dynamic Media of Experience Manager, moet u ervoor zorgen dat **[!UICONTROL Selective Publish]** is ingeschakeld in uw **[!UICONTROL Dynamic Media Configuration]** of in de mapeigenschappen van de geselecteerde map.

**om activa aan Dynamische Media of Experience Manager te publiceren gebruikend Snel publiceren:**

1. Selecteer in Experience Manager het Experience Manager-logo voor toegang tot de algemene navigatieconsole. Selecteer links op de pagina het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens rechts op de pagina **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Voer in **[!UICONTROL Card View]**, **[!UICONTROL Column View]** of **[!UICONTROL List View]** een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Quick Publish]** . Gebruik **[!UICONTROL List View]** om de publicatiestatus van een bepaalde map gemakkelijker te kunnen controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Selecteer **[!UICONTROL Quick Publish]** op de werkbalk. Gebruik **[!UICONTROL List View]** om de publicatiestatus van een bepaald element gemakkelijker te kunnen controleren.

     >[!NOTE]
     >
     >Als **[!UICONTROL Quick Publish]** niet op de werkbalk wordt weergegeven, selecteert u de knop voor weglatingsteken en selecteert u vervolgens **[!UICONTROL Quick Publish]** in het lijstmenu.

     ![&#x200B; omslag-vlakke Snel publiceren aan Dynamische Media &#x200B;](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Selecteer een van de volgende opties in de menulijst van **[!UICONTROL Quick Publish]** .

   | Snel publiceren, optie | Wat doet het? |
   | --- | --- |
   | Publiceren naar Experience Manager | Hiermee publiceert u de geselecteerde elementen direct naar Experience Manager. |
   | Publiceren naar Brand Portal | Hiermee publiceert u de geselecteerde elementen direct naar **[!UICONTROL Brand Portal]** .<br> Deze optie is slechts beschikbaar als uw instantie van Experience Manager Assets **[!UICONTROL Brand Portal]** reeds gevormd heeft. |
   | Publiceren naar dynamische media | Hiermee publiceert u de geselecteerde elementen direct naar Dynamic Media.<br> activa moeten aan Dynamische Media worden gesynchroniseerd. Controleer, indien nodig, of **[!UICONTROL Sync mode]** in de eigenschappen van een map al is ingesteld op **[!UICONTROL Sync everything in this folder subtree to Dynamic Media]** . |

1. Selecteer **[!UICONTROL OK]** en selecteer vervolgens **[!UICONTROL Close]** .

## Elementen selectief publiceren of de publicatie ervan ongedaan maken via zoekresultaten {#selective-publish-unpublish-search-results}

In de zoekresultaten kunt u elementen uit de verschillende elementmappen met verschillende publicatie-instellingen voor Dynamische media weergeven. Wanneer u meerdere elementen selecteert in zoekresultaten en elk element verschillende instellingen voor de publicatiemodus Dynamische media heeft, kunt u **[!UICONTROL Manage Publication]** activeren op de werkbalk om te publiceren of te publiceren.

Zie ook [&#x200B; activa van het Onderzoek in Experience Manager &#x200B;](/help/assets/search-assets.md).

**om activa als onderzoeksresultaten selectief te publiceren of unpublish:**

1. Selecteer in Experience Manager linksboven op de pagina het Experience Manager-logo voor toegang tot de algemene navigatieconsole. Selecteer links op de pagina het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Selecteer in de werkbalk rechtsboven op de pagina het pictogram Zoeken (vergrootglas).
1. Voer in het tekstveld **[!UICONTROL Type to search]** een trefwoord in en druk op **[!UICONTROL Enter]** .
1. Selecteer in de rechterbovenhoek van de pagina het pictogram **[!UICONTROL List View]** .
1. Selecteer het pictogram **[!UICONTROL Filters]** in de linkerbovenhoek van de pagina.

   ![&#x200B; de Mening van de Lijst en Filters in onderzoeksresultaten &#x200B;](/help/assets/assets-dm/select-publish-search-result.png)

1. Vouw in het linkerdeelvenster **[!UICONTROL Status]** uit en vouw vervolgens de **[!UICONTROL Dynamic Media]** zoekvoorspelling uit.
1. Gebruik de selectievakjes **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** om de zoekresultaten verder te verfijnen op basis van de gepubliceerde status van Dynamic Media-elementen.
U kunt deze selectievakjes ook gebruiken met de zoekvoorspelling **[!UICONTROL Publish]** om de zoekresultaten van de Experience Manager-elementen **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** te verfijnen.
1. Voer een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u wilt publiceren of maak de publicatie ongedaan.
   * Selecteer **[!UICONTROL Search Results]** in de rechterbovenhoek van de pagina **[!UICONTROL Select All]** .
1. Selecteer **[!UICONTROL Manage Publication]** op de werkbalk. Selecteer het ellipspictogram op de werkbalk zodat u **[!UICONTROL Manage Publication]** kunt openen.
1. Selecteer op de pagina **[!UICONTROL Manage Publication - Options]** de gewenste actie.

   | Geselecteerde actie | Assets-instelling publiceren in Dynamic Media Configuration | Assets zijn |
   | --- | --- | --- |
   | Publiceren | Onmiddellijk of bij activering | Gepubliceerd naar Experience Manager en Dynamic Media. |
   | Publiceren | Selectieve publicatie | Alleen gepubliceerd naar Experience Manager. |
   | Publiceren ongedaan maken | Onmiddellijk of bij activering | Niet gepubliceerd vanuit Experience Manager en Dynamic Media. |
   | Publiceren ongedaan maken | Selectieve publicatie | Alleen niet gepubliceerd vanuit Experience Manager. |
   | Publiceren naar dynamische media | Onmiddellijk of bij activering | Niet gepubliceerd naar Experience Manager, Dynamic Media of beide. |
   | Publiceren naar dynamische media | Selectieve publicatie | Alleen gepubliceerd naar dynamische media. |
   | Publiceren van dynamische media ongedaan maken | Onmiddellijk of bij activering | Niet ongepubliceerd vanuit Experience Manager, Dynamic Media of beide. |
   | Publiceren van dynamische media ongedaan maken | Selectieve publicatie | Niet gepubliceerd met alleen Dynamic Media. |

1. Stel onder **[!UICONTROL Schedule]** de timing van de deactivering in.

   | Geselecteerd schema | Wat gebeurt er? |
   | --- | --- |
   | Nu | De geselecteerde actie wordt onmiddellijk uitgevoerd. |
   | Later | De geselecteerde actie wordt uitgevoerd op de geselecteerde bepaalde datum en tijd. |

1. Selecteer **[!UICONTROL Manage Publication - Options]** in de rechterbovenhoek van de pagina **[!UICONTROL Next]** .
1. (Optioneel) Controleer op de pagina **[!UICONTROL Manage Publication - Scope]** de kolom **[!UICONTROL Publish Target]** in de tabel voor de geselecteerde elementen.

   | Assets-instelling publiceren in Dynamic Media Configuration | Geselecteerde actie | Publicatiedoel |
   | --- | --- | --- |
   | Onmiddellijk of <br> op Activering | Publiceren | Experience Manager en Dynamic Media |
   | Onmiddellijk of <br> op Activering | Publiceren naar dynamische media | Geen |
   | Selectieve publicatie | Publiceren | Experience Manager |
   | Selectieve publicatie | Publiceren naar dynamische media | Dynamische media |
   | Onmiddellijk of <br> op Activering | Publiceren ongedaan maken | Experience Manager en Dynamic Media |
   | Onmiddellijk of <br> op Activering | Publiceren van dynamische media ongedaan maken | Geen |
   | Selectieve publicatie | Publiceren ongedaan maken | Experience Manager |
   | Selectieve publicatie | Publiceren van dynamische media ongedaan maken | Dynamische media |

1. Voer op de pagina **[!UICONTROL Manage Publication - Scope]** een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit publiceren of verwijderen.
   * Selecteer **[!UICONTROL Manage Publication - Scope]** of **[!UICONTROL Publish]** in de rechterbovenhoek van de pagina **[!UICONTROL Unpublish]** om de handeling te starten.
1. Selecteer **[!UICONTROL OK]** .

## De publicatiestatus van een element controleren {#check-publish-status-of-asset}

U kunt **[!UICONTROL Timeline]** met **[!UICONTROL Card view]** , **[!UICONTROL Column View]** of **[!UICONTROL List View]** in Experience Manager gebruiken om snel de publicatiestatus van een element te controleren.

**om het publiceren status van activa te controleren:**

1. Selecteer in Experience Manager linksboven op de pagina het Experience Manager-logo voor toegang tot de algemene navigatieconsole. Selecteer links op de pagina het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Open in **[!UICONTROL Card View]** , **[!UICONTROL Column View]** of **[!UICONTROL List View]** (in de onderstaande schermafbeelding ziet u de **[!UICONTROL List View]** ) een map met elementen die u hebt gepubliceerd of die u niet hebt gepubliceerd.
1. Selecteer een element, zodat dit met een vinkje wordt weergegeven. Zie onderstaande schermafbeelding.
1. Selecteer **[!UICONTROL Timeline]** in de linkerbovenhoek van de pagina in het keuzemenu. Het gebied **[!UICONTROL Status]** in het linkerpaneel toont de publicatiestatus van het geselecteerde element.
Wanneer u **[!UICONTROL List View]** gebruikt, wordt een extra kolom voor de publicatiestatus **[!UICONTROL Dynamic Media]** weergegeven.
   * In een map die is geconfigureerd voor synchronisatie met Dynamic Media, wordt standaard de kolom **[!UICONTROL Dynamic Media]** weergegeven.
   * Een omslag die *niet* wordt gevormd om aan Dynamische Media te synchroniseren toont niet de Dynamische kolom van Media.
     ![&#x200B; de Mening van de Lijst en Chronologie &#x200B;](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Problemen met selectief publiceren oplossen {#selective-publish-troubleshoot}

Een middel dat niet aan Dynamische Media wordt gesynchroniseerd maar een Dynamische Media heeft publicatieactie teweeggebracht op het resulteert in het volgende foutenbericht en de oplossing:

![&#x200B; Selectieve publiceer fout &#x200B;](/help/assets/assets-dm/selective-publish-error.png)
