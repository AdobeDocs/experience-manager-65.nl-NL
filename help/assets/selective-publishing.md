---
title: Werken met Selectieve publicatie in Dynamic Media
description: U kunt ervoor kiezen om middelen naar of van Adobe Experience Manager of Dynamic Media op mapniveau te publiceren of de publicatie ervan ongedaan te maken. U kunt Publicatie beheren of Snel publiceren gebruiken in plaats van alleen te vertrouwen op de Dynamic Media-configuratie waarvan de instellingen algemeen gelden voor alle mappen in uw Dynamic Media-instantie.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
exl-id: cd025e9d-6fb1-436c-9e78-795f2daaf345
feature: Publishing
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2598'
ht-degree: 0%

---

# Selectieve publicatie op mapniveau in Dynamic Media configureren {#selective-publish-configure-folder}

U kunt ervoor kiezen om middelen naar of van Adobe Experience Manager of Dynamic Media op mapniveau te publiceren of de publicatie ervan ongedaan te maken. U kunt beide **[!UICONTROL Manage Publication]** of **[!UICONTROL Quick Publish]** in plaats van alleen op de **[!UICONTROL Dynamic Media Configuration]** wiens instellingen algemeen zijn voor alle mappen in uw Dynamic Media-exemplaar.

Met selectief publiceren kunt u bijvoorbeeld werken aan elementen voor producten die nog niet actief zijn. In dat geval kan een marketingteam toegang krijgen tot afbeeldingen met slimme uitsnijdingen en dynamische vertoningen die zijn gesynchroniseerd met Dynamic Media. Ze kunnen promotiematerialen maken, zonder dat ze die middelen naar Dynamic Media hoeven te publiceren voor wereldwijde levering.

>[!IMPORTANT]
>
>Selectieve publicatie is alleen beschikbaar in de modus Dynamic Media - Scene7.

>[!NOTE]
>
>*Kopiëren* elementen naar en van mappen wissen de publicatiestatus van deze elementen. Wanneer u echter *move* elementen naar en van mappen waarvan de eigenschap folder is ingesteld op **[!UICONTROL Selective Publish]**, wordt de publicatiestatus van deze activa gehandhaafd.

Als u later besluit om het dialoogvenster **[!UICONTROL Selective Publish]** in een map, hebben deze wijzigingen alleen invloed op nieuwe elementen die u vanaf dat punt uploadt naar die map. De publicatiestatus van bestaande elementen in de map blijft ongewijzigd totdat u deze handmatig wijzigt vanuit een van de volgende **[!UICONTROL Quick Publish]** of de **[!UICONTROL Manage Publication]** in.

Het mapniveau **[!UICONTROL Dynamic Media Publish mode]** Deze optie is altijd standaard ingesteld op de waarde in het dialoogvenster **[!UICONTROL Publish Assets]** instellen in uw **[!UICONTROL Dynamic Media Configuration]**. De volgende stappen in dit onderwerp, echter, tonen u hoe te om deze standaardwaarde op het omslagniveau (zoals die in de volgende stappen wordt beschreven) manueel te veranderen om **[!UICONTROL Dynamic Media Configuration]** waarde.

Ongeacht of u op een van de volgende twee manieren vertrouwt:

* **[!UICONTROL Publish Assets]** waarde ingesteld in **[!UICONTROL Dynamic Media Configuration]**.
* **[!UICONTROL Dynamic Media Publish mode]** waarde ingesteld in eigenschappen op mapniveau.

U kunt **[!UICONTROL Immediately]**, **[!UICONTROL On Activation]**, of **[!UICONTROL Selective Publish]**. U kunt bijvoorbeeld de opdracht **[!UICONTROL Publish Assets]** waarde in uw **[!UICONTROL Dynamic Media Configuration]** tot **[!UICONTROL On Activation]**, maar stelt de **[!UICONTROL Dynamic Media Publish]** moduswaarde op mapniveau tot **[!UICONTROL Selective Publish]** en omgekeerd.

Nadat u selectief publiceren in een omslag vormt, kunt u om het even welke volgend doen:

* [Elementen selectief publiceren naar Dynamic Media of Experience Manager met Publicatie beheren](#selective-publish-manage-publication).
* [Publicatie van middelen van Dynamic Media of Experience Manager selectief ongedaan maken met Publicatie beheren](#selective-unpublish-manage-publication).
* [Elementen publiceren naar Dynamic Media of Experience Manager met Snel publiceren](#quick-publish-aem-dm).
* [Elementen selectief publiceren of de publicatie ervan ongedaan maken via zoekresultaten](#selective-publish-unpublish-search-results).

**Selectieve publicatie op mapniveau in Dynamic Media configureren:**

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Voer een van de volgende handelingen uit:
   * Bewerk de eigenschappen van een bestaande map - In **[!UICONTROL Card View]**, **[!UICONTROL Column View]**, of **[!UICONTROL List View]** navigeer naar een map waarvan u de eigenschappen wilt bewerken. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Properties]**.
   * Bewerk de eigenschappen van een nieuwe map - In **[!UICONTROL Card View]**, **[!UICONTROL Column View]**, of **[!UICONTROL List View]** Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Create]** > **[!UICONTROL Folder]**. In de **[!UICONTROL Create Folder]** voert u een (vereiste) titel voor de map in en selecteert u **[!UICONTROL Create]**. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Properties]**.

1. In de **[!UICONTROL Sync mode]** Selecteer een van de volgende opties in de vervolgkeuzelijst:

   | Synchronisatiemodus | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Inherited]** | Er staat geen expliciete synchronisatiewaarde in de map. In plaats daarvan neemt de map de synchronisatiewaarde over van een van de bovenliggende mappen of de standaardmodus die in de map is ingesteld **[!UICONTROL Dynamic Media Configuration]**. Gedetailleerde status voor **[!UICONTROL Inherited]** wordt weergegeven als knopinfo. |
   | **[!UICONTROL Sync everything in this folder subtree to Dynamic Media]** | Voor het publiceren naar Dynamic Media moet u de middelen synchroniseren met Dynamic Media. Als u deze optie selecteert, worden alle elementen in deze substructuur opgenomen die u kunt synchroniseren met Dynamic Media. De mapspecifieke instellingen overschrijven de standaardinstelling in het dialoogvenster **[!UICONTROL Dynamic Media Configuration]**. |
   | **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** | Sluit alle elementen in deze substructuur uit van synchroniseren naar Dynamic Media. |

   ![Selectieve publicatie op mapniveau](/help/assets/assets-dm/createfolder-properties-selectivepublish.png)

1. In de **[!UICONTROL Dynamic Media Publish mode]** een optie. De **[!UICONTROL Dynamic Media Publish mode]** Deze optie is altijd standaard ingesteld op de waarde die is ingesteld in het dialoogvenster **[!UICONTROL Dynamic Media Configuration]**. U kunt deze standaardinstelling echter handmatig overschrijven **[!UICONTROL Dynamic Media Configuration]** door een van de volgende opties te gebruiken.

   >[!IMPORTANT]
   >
   >Ongeacht de optie die u in de Dynamic Media-publicatiemodus selecteert, worden eventuele updates die u later aanbrengt in een element dat *reeds* gepubliceerd, worden die updates onmiddellijk gepubliceerd zonder verdere gebruikersactie.
   >
   >Als een gepubliceerde video wordt bijgewerkt, moet deze opnieuw worden gepubliceerd om wijzigingen in de levering te weerspiegelen.

   | Dynamic Media-publicatiemodus, optie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Immediately]** | Wanneer elementen naar deze map worden geüpload, worden de elementen door het systeem in de Experience Manager ingevoerd en wordt de URL/Embed onmiddellijk weergegeven. Deze optie is alleen gekoppeld aan publicatie door Experience Managers en er is geen tussenkomst van de gebruiker nodig om elementen te publiceren.<br>Deze optie is *niet* beschikbaar als u **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in **[!UICONTROL Sync mode]** in de vorige stap. |
   | **[!UICONTROL Upon Activation]** | Wanneer elementen naar deze map worden geüpload, moet u het element eerst expliciet publiceren voordat een koppeling URL/Embed wordt opgegeven. Deze optie is alleen gekoppeld aan publiceren via Experience Manager.<br>Deze optie is *niet* beschikbaar als u **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in **[!UICONTROL Sync mode]** in de vorige stap. |
   | **[!UICONTROL Selective Publish]** | De activa worden gepubliceerd aan uw keuze van of Experience Manager of aan Dynamic Media voor levering in het openbare domein. Beide publicatiemethoden sluiten elkaar uit. Met andere woorden, u kunt elementen publiceren naar DMS7 zodat u functies zoals Slim uitsnijden of dynamische uitvoeringen kunt gebruiken. U kunt ook uitsluitend elementen publiceren naar Experience Manager voor een beveiligde voorvertoning. Dezelfde elementen zijn *niet* gepubliceerd aan DMS7 voor levering in het publieke domein. Deze optie is niet beschikbaar als u **[!UICONTROL Exclude everything in this folder subtree from Dynamic Media sync]** in **[!UICONTROL Sync mode]** in de vorige stap. |

1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Save & Close]** selecteert u vervolgens **[!UICONTROL OK]** terug naar Experience Manager Assets.

## Elementen selectief publiceren naar Dynamic Media of Experience Manager met Publicatie beheren{#selective-publish-manage-publication}

Wat u moet doen **[!UICONTROL Manage Publication]** als u elementen selectief wilt publiceren naar Dynamic Media of Experience Manager, moet u een van de volgende instellingen hebben ingesteld:

* De **[!UICONTROL Publish Assets]** optie in **[!UICONTROL Dynamic Media Configuration]** tot **[!UICONTROL Selective Publish]**
* Configureerde selectieve publicatie op mapniveau.

Zie [Een Dynamic Media-configuratie maken](#configuring-dynamic-media-cloud-services) of [Selectieve publicatie op mapniveau in Dynamic Media configureren](#selective-publish-configure-folder)

>[!IMPORTANT]
>
>Selectieve publicatie is alleen beschikbaar in de modus Dynamic Media - Scene7.

>[!NOTE]
>
>*Kopiëren* elementen naar en van mappen wissen de publicatiestatus van deze elementen. Wanneer u echter *move* elementen naar en van mappen waarvan de eigenschap folder is ingesteld op **[!UICONTROL Selective Publish]**, wordt de publicatiestatus van deze activa gehandhaafd.

**Elementen selectief publiceren naar Dynamic Media of Experience Manager met Publicatie beheren:**

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. In **[!UICONTROL Card View]**, **[!UICONTROL Column View]**, of **[!UICONTROL List View]** Voer een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Manage Publication]**. Gebruiken **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaalde map gemakkelijker kunt controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Selecteer op de werkbalk de optie **[!UICONTROL Manage Publication]**. Gebruiken **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaald middel gemakkelijker kunt controleren.

     >[!NOTE]
     >
     >Indien **[!UICONTROL Manage Publication]** niet zichtbaar is op de werkbalk, selecteert u in plaats daarvan de knop Ovaal. Selecteer vervolgens **[!UICONTROL Manage Publication]** in het lijstmenu.

1. In de **[!UICONTROL Manage Publication - Options]** pagina, onder **[!UICONTROL Action]**, selecteert u het gewenste activeringstype.

   | Handeling | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Publish]** (naar Experience Manager) | Selecteer deze optie zodat u elementen naar de Experience Manager kunt publiceren voor een veilige voorvertoning. |
   | **[!UICONTROL Publish to Dynamic Media]** | Selecteer deze optie zodat u elementen naar Dynamic Media kunt publiceren voor levering in het publieke domein of zodat u functies zoals Slim uitsnijden of dynamische uitvoeringen kunt gebruiken.<br>Deze optie is alleen beschikbaar als **[!UICONTROL Dynamic Media Publish mode]** is ingesteld op **[!UICONTROL Selective Publish]** in de eigenschappen van de map. |

1. Onder **[!UICONTROL Schedule]**, stelt u de timing van de publicatie in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de elementen direct te publiceren. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de elementen op een bepaalde datum en tijd te publiceren. |

1. In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Manage Publication]** pagina, selecteert u **[!UICONTROL Next]**.
1. In de **[!UICONTROL Manage Publication - Scope]** pagina, voer een van de volgende handelingen uit:

   * Selecteer zo nodig een of meer elementen die u uit publicatie wilt verwijderen.
   * In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Manage Publication - Scope]** pagina, selecteert u **[!UICONTROL Publish]** of **[!UICONTROL Publish to Dynamic Media]**.
1. Selecteren **[!UICONTROL OK]**.

### Publicatie van middelen van Dynamic Media of Experience Manager selectief ongedaan maken met Publicatie beheren {#selective-unpublish-manage-publication}

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. In **[!UICONTROL Card View]**, **[!UICONTROL Column View]**, of **[!UICONTROL List View]** Voer een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Manage Publication]**. Gebruiken **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaalde map gemakkelijker kunt controleren.
   * Navigeer naar een map waarvan u de publicatie ongedaan wilt maken. Open de map en selecteer vervolgens een of meer elementen. Selecteer op de werkbalk de optie **[!UICONTROL Manage Publication]**. Gebruiken **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaald middel gemakkelijker kunt controleren.

     >[!NOTE]
     >
     >Indien **[!UICONTROL Manage Publication]** niet zichtbaar is op de werkbalk, selecteert u in plaats daarvan de knop Ovaal. Selecteer vervolgens **[!UICONTROL Manage Publication]** in het lijstmenu.

1. In de **[!UICONTROL Manage Publication - Options]** pagina, onder **[!UICONTROL Action]** Selecteer het gewenste type deactivering.

   | Handeling | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Unpublish]** (van Experience Manager) | Selecteer deze optie als u de publicatie van elementen in de Experience Manager ongedaan wilt maken. |
   | **[!UICONTROL Unpublish from Dynamic Media]** | Selecteer deze optie als u de publicatie van elementen uit Dynamic Media wilt opheffen.<br>Deze optie is alleen beschikbaar als **[!UICONTROL Dynamic Media Publish mode]** is ingesteld op **[!UICONTROL Selective Publish]** in de eigenschappen van de map. |

1. Onder **[!UICONTROL Schedule]**, stelt u de timing van de deactivering in.

   | Schema | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Now]** | Selecteer deze optie om de publicatie van de elementen direct ongedaan te maken. |
   | **[!UICONTROL Later]** | Selecteer deze optie om de publicatie van de elementen op een bepaalde datum en tijd ongedaan te maken. |

1. In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Manage Publication]** pagina, selecteert u **[!UICONTROL Next]**.
1. In de **[!UICONTROL Manage Publication - Scope]** pagina, voer een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit het ongedaan maken van de publicatie wilt verwijderen.
   * In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Manage Publication - Scope]** pagina, selecteert u **[!UICONTROL Unpublish]** of **[!UICONTROL Unpublish from Dynamic Media]**.
1. Selecteren **[!UICONTROL OK]**.

## Elementen publiceren naar Dynamic Media of Experience Manager met Snel publiceren {#quick-publish-aem-dm}

U kunt **[!UICONTROL Quick Publish]** voor eenvoudige gevallen van activering van middelen. **[!UICONTROL Quick Publish]** publiceert de geselecteerde middelen onmiddellijk zonder verdere gebruikersinteractie. Vanwege deze handeling worden niet-gepubliceerde verwijzingen ook automatisch gepubliceerd.

>[!NOTE]
>
>Te gebruiken **[!UICONTROL Quick Publish]** om elementen te publiceren naar Dynamic Media of Experience Manager, zorg ervoor **[!UICONTROL Selective Publish]** is ingeschakeld in uw **[!UICONTROL Dynamic Media Configuration]** of in de mapeigenschappen van de geselecteerde map.

**Elementen publiceren naar Dynamic Media of Experience Manager met Snel publiceren:**

1. In Experience Manager, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links op de pagina het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens aan de rechterkant van de pagina **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. In **[!UICONTROL Card View]**, **[!UICONTROL Column View]**, of **[!UICONTROL List View]** Voer een van de volgende handelingen uit:
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Selecteer de map en selecteer vervolgens op de werkbalk **[!UICONTROL Quick Publish]**. Gebruiken **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaalde map gemakkelijker kunt controleren.
   * Navigeer naar een map waarvan u de elementen wilt publiceren. Open de map en selecteer vervolgens een of meer elementen. Selecteer op de werkbalk de optie **[!UICONTROL Quick Publish]**. Gebruiken **[!UICONTROL List View]** zodat u de publicatiestatus van een bepaald middel gemakkelijker kunt controleren.

     >[!NOTE]
     >
     >Indien **[!UICONTROL Quick Publish]** niet zichtbaar is op de werkbalk, selecteert u in plaats daarvan de knop Ovaal. Selecteer vervolgens **[!UICONTROL Quick Publish]** in het lijstmenu.

     ![Snel publiceren op mapniveau naar Dynamic Media](/help/assets/assets-dm/selective-publish-folder-quick-publish-to-dm.png)

1. Selecteer een van de volgende opties in het menu **[!UICONTROL Quick Publish]** lijst.

   | Snel publiceren, optie | Wat doet het? |
   | --- | --- | 
   | Publiceren naar Experience Manager | Hiermee publiceert u de geselecteerde elementen direct naar de Experience Manager. |
   | Publiceren naar Brand Portal | Hiermee publiceert u de geselecteerde elementen direct naar **[!UICONTROL Brand Portal]**.<br>Deze optie is alleen beschikbaar als uw Experience Manager Assets-exemplaar **[!UICONTROL Brand Portal]** al geconfigureerd. |
   | Publiceren naar Dynamic Media | Hiermee publiceert u de geselecteerde elementen direct naar Dynamic Media.<br>Een middel moet aan Dynamic Media worden gesynchroniseerd. Zorgt er zo nodig voor dat **[!UICONTROL Sync mode]** in de eigenschappen van een map is al ingesteld op **[!UICONTROL Sync everything in this folder subtree to Dynamic Media]**. |

1. Selecteren **[!UICONTROL OK]** selecteert u vervolgens **[!UICONTROL Close]**.

## Elementen selectief publiceren of de publicatie ervan ongedaan maken via zoekresultaten {#selective-publish-unpublish-search-results}

In de zoekresultaten kunt u elementen uit verschillende middelenmappen met verschillende Dynamic Media-publicatie-instellingen weergeven. Wanneer u meerdere elementen selecteert in zoekresultaten en elk element verschillende Dynamic Media-instellingen voor de publicatiemodus heeft, kunt u een trigger **[!UICONTROL Manage Publication]** op de werkbalk om te publiceren of om de publicatie ongedaan te maken.

Zie ook [Middelen zoeken in Experience Manager](/help/assets/search-assets.md).

**Elementen selectief publiceren of verwijderen via zoekresultaten:**

1. In Experience Manager, in de upper-left hoek van de pagina, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links op de pagina het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. Selecteer in de werkbalk rechtsboven op de pagina het pictogram Zoeken (vergrootglas).
1. In de **[!UICONTROL Type to search]** tekstveld, voer een trefwoord in en druk op **[!UICONTROL Enter]**.
1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL List View]** pictogram.
1. Selecteer in de linkerbovenhoek van de pagina de optie **[!UICONTROL Filters]** pictogram.

   ![Lijstweergave en filters in zoekresultaten](/help/assets/assets-dm/select-publish-search-result.png)

1. Vouw in het linkerdeelvenster uit **[!UICONTROL Status]** en breid vervolgens de **[!UICONTROL Dynamic Media]** zoekvoorspelling.
1. Gebruik de **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** selectievakjes om de zoekresultaten verder te verfijnen op basis van de gepubliceerde status van Dynamic Media-elementen.
U kunt deze selectievakjes desgewenst ook gebruiken met de **[!UICONTROL Publish]** zoekvoorspelling om de zoekresultaten van **[!UICONTROL Published]** en **[!UICONTROL Unpublished]** Experience Manager-elementen.
1. Voer een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u wilt publiceren of maak de publicatie ongedaan.
   * In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Search Results]** pagina, selecteert u **[!UICONTROL Select All]**.
1. Selecteer op de werkbalk de optie **[!UICONTROL Manage Publication]**. Selecteer het ellipsiepictogram op de werkbalk zodat u het dialoogvenster kunt openen **[!UICONTROL Manage Publication]**.
1. Op de **[!UICONTROL Manage Publication - Options]** selecteert u de gewenste actie.

   | Geselecteerde actie | Instelling Middelen publiceren in Dynamic Media-configuratie | Elementen zijn |
   | --- | --- | --- |
   | Publiceren | Onmiddellijk of bij activering | Gepubliceerd aan Experience Manager en Dynamic Media. |
   | Publiceren | Selectieve publicatie | Alleen gepubliceerd naar Experience Manager. |
   | Publiceren ongedaan maken | Onmiddellijk of bij activering | Niet gepubliceerd vanuit Experience Manager en Dynamic Media. |
   | Publiceren ongedaan maken | Selectieve publicatie | Niet gepubliceerd alleen vanuit Experience Manager. |
   | Publiceren naar Dynamic Media | Onmiddellijk of bij activering | Niet gepubliceerd naar Experience Manager, Dynamic Media of beide. |
   | Publiceren naar Dynamic Media | Selectieve publicatie | Alleen gepubliceerd naar Dynamic Media. |
   | Publiceren vanuit Dynamic Media ongedaan maken | Onmiddellijk of bij activering | Niet ongepubliceerd vanuit Experience Manager, Dynamic Media of beide. |
   | Publiceren vanuit Dynamic Media ongedaan maken | Selectieve publicatie | Alleen niet gepubliceerd vanuit Dynamic Media. |

1. Onder **[!UICONTROL Schedule]**, stelt u de timing van de deactivering in.

   | Geselecteerd schema | Wat gebeurt er? |
   | --- | --- |
   | Nu | De geselecteerde actie wordt onmiddellijk uitgevoerd. |
   | Later | De geselecteerde actie wordt uitgevoerd op de geselecteerde bepaalde datum en tijd. |

1. In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Manage Publication - Options]** pagina, selecteert u **[!UICONTROL Next]**.
1. (Optioneel) In het dialoogvenster **[!UICONTROL Manage Publication - Scope]** pagina, bekijk de **[!UICONTROL Publish Target]** in de tabel voor de geselecteerde elementen.

   | Instelling Middelen publiceren in Dynamic Media-configuratie | Geselecteerde actie | Publicatiedoel |
   | --- | --- | --- |
   | Onmiddellijk of <br>Bij activering | Publiceren | Experience Manager en Dynamic Media |
   | Onmiddellijk of <br>Bij activering | Publiceren naar Dynamic Media | Geen |
   | Selectieve publicatie | Publiceren | Experience Manager |
   | Selectieve publicatie | Publiceren naar Dynamic Media | Dynamic Media |
   | Onmiddellijk of <br>Bij activering | Publiceren ongedaan maken | Experience Manager en Dynamic Media |
   | Onmiddellijk of <br>Bij activering | Publiceren vanuit Dynamic Media ongedaan maken | Geen |
   | Selectieve publicatie | Publiceren ongedaan maken | Experience Manager |
   | Selectieve publicatie | Publiceren vanuit Dynamic Media ongedaan maken | Dynamic Media |

1. In de **[!UICONTROL Manage Publication - Scope]** pagina, voer een van de volgende handelingen uit:
   * Selecteer een of meer elementen die u uit publiceren of verwijderen.
   * In de rechterbovenhoek van het dialoogvenster **[!UICONTROL Manage Publication - Scope]** pagina, selecteert u **[!UICONTROL Publish]** of **[!UICONTROL Unpublish]** om de handeling te starten.
1. Selecteren **[!UICONTROL OK]**.

## De publicatiestatus van een element controleren {#check-publish-status-of-asset}

U kunt **[!UICONTROL Timeline]** with **[!UICONTROL Card view]**, **[!UICONTROL Column View]**, of **[!UICONTROL List View]** in Experience Manager om snel de publicatiestatus van een element te controleren.

**De publicatiestatus van een element controleren:**

1. In Experience Manager, in de upper-left hoek van de pagina, selecteer het embleem van de Experience Manager om tot de globale navigatieconsole toegang te hebben. Selecteer links op de pagina het navigatiepictogram (net boven het pictogram Gereedschappen) en selecteer vervolgens **[!UICONTROL Assets]** > **[!UICONTROL Files]**.
1. In **[!UICONTROL Card View]**, **[!UICONTROL Column View]**, of **[!UICONTROL List View]** (onderstaande schermafbeelding toont de **[!UICONTROL List View]**), opent u een map met elementen die u hebt gepubliceerd of niet hebt gepubliceerd.
1. Selecteer een element, zodat dit met een vinkje wordt weergegeven. Zie onderstaande schermafbeelding.
1. Selecteer in de linkerbovenhoek van de pagina in het keuzemenu de optie **[!UICONTROL Timeline]**. De **[!UICONTROL Status]** in het linkerdeelvenster wordt de publicatiestatus van het geselecteerde element weergegeven.
Wanneer u **[!UICONTROL List View]**, een extra kolom voor **[!UICONTROL Dynamic Media]** publicatiestatus wordt weergegeven.
   * In een map die is geconfigureerd voor synchronisatie met Dynamic Media, wordt het dialoogvenster **[!UICONTROL Dynamic Media]** kolom standaard.
   * Een map die *niet* geconfigureerd voor synchronisatie met Dynamic Media, geeft de Dynamic Media-kolom niet weer.
     ![Lijstweergave en tijdlijn](/help/assets/assets-dm/selective-publish-status-timeline.png)

## Problemen met selectief publiceren oplossen {#selective-publish-troubleshoot}

Een middel dat niet aan Dynamic Media wordt gesynchroniseerd maar een Dynamic Media publicatieactie teweegbrengt die op het in werking treedt resulteert in het volgende foutenbericht en de oplossing:

![Selectieve publicatiefout](/help/assets/assets-dm/selective-publish-error.png)
