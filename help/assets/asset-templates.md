---
title: Elementsjablonen
description: Leer over de malplaatjes van Activa in  [!DNL Adobe Experience Manager Assets]  en hoe te om activamalplaatjes te gebruiken om marketing onderpand tot stand te brengen.
contentOwner: AG
role: User
feature: Asset Management,Developer Tools
exl-id: 12c92aad-3a1d-486e-a830-31de2fc6d07b
solution: Experience Manager, Experience Manager Assets
source-git-commit: 0b90fdd13efc5408ef94ee1966f04a80810b515e
workflow-type: tm+mt
source-wordcount: '1517'
ht-degree: 0%

---

# Elementsjablonen {#asset-templates}

Elementsjablonen zijn een speciale klasse elementen die het snel opnieuw gebruiken van visueel rijke inhoud voor digitale media en gedrukte media mogelijk maken. Een activamalplaatje omvat twee delen, de vaste overseinensectie en de editable sectie. De sectie met vaste berichten kan eigen inhoud bevatten, zoals merklogo en copyrightinformatie die zijn uitgeschakeld voor bewerking. De bewerkbare sectie kan visuele en tekstuele inhoud bevatten in velden die kunnen worden bewerkt om berichten aan te passen.

Asset-sjablonen bieden de flexibiliteit om beperkte bewerkingen uit te voeren en tegelijkertijd de wereldwijde handtekening veilig te houden. Hierdoor zijn ze ideaal als bouwstenen voor het snel aanpassen en distribueren van inhoud over verschillende functies. Door inhoud te hergebruiken, worden de kosten voor het beheer van afdruk- en digitale kanalen verlaagd en kunnen holistische en consistente ervaringen op deze kanalen worden opgedaan.

Als markeerteken kunt u sjablonen opslaan en beheren binnen [!DNL Experience Manager Assets] en één basissjabloon gebruiken om eenvoudig meerdere persoonlijke afdrukervaringen te maken. U kunt diverse soorten marketing onderpand, met inbegrip van brochures, vliegers, postcards, visitekaartjes, etc. tot stand brengen, om uw marketing bericht aan klanten duidelijk over te brengen. U kunt ook uitvoer van meerdere pagina&#39;s samenstellen op basis van bestaande of nieuwe afdrukuitvoerbestanden. Met name kunt u tegelijkertijd eenvoudig zowel digitale als afdrukervaringen bieden, zodat gebruikers een consistente, geïntegreerde ervaring hebben.

Elementsjablonen zijn meestal [!DNL Adobe InDesign] -bestanden, maar de ervaring in [!DNL Adobe InDesign] vormt geen belemmering voor het maken van stellaire artefacten. U hoeft de velden van uw [!DNL Adobe InDesign] -sjabloon niet toe te wijzen aan productvelden die u anders nodig hebt bij het maken van catalogi. U kunt de sjablonen in de WYSIWYG-modus rechtstreeks in de webinterface bewerken. Als u echter wilt dat [!DNL Adobe InDesign] uw bewerkingswijzigingen verwerkt, moet u [!DNL Experience Manager Assets] eerst configureren voor integratie met [!DNL Adobe InDesign Server] .

De mogelijkheid om [!DNL Adobe InDesign] -sjablonen vanuit de webinterface te bewerken, bevordert een betere samenwerking tussen creatief en marketingpersoneel. De verhoogde snelheid van de inhoud vermindert de tijd-aan-markt voor marketing zekerheden.

U kunt het volgende bereiken met middelensjablonen:

* Bewerkbare sjabloonvelden wijzigen vanuit de webinterface.
* Hiermee bepaalt u de basisopmaak van tekst, zoals tekengrootte, stijl en tekst op tagniveau.
* Wijzig de afbeeldingen in de sjabloon met de inhoudkiezer.
* Sjabloonbewerkingen voorvertonen.
* Voeg meerdere sjabloonbestanden samen, zodat u een vervorming van meerdere pagina&#39;s kunt maken.

Wanneer u een sjabloon voor uw onderpand kiest, maakt [!DNL Experience Manager Assets] een kopie van de sjabloon die u kunt bewerken. De oorspronkelijke sjabloon blijft behouden, zodat uw globale handtekening intact blijft en opnieuw kan worden gebruikt om de consistentie van uw merk te handhaven.

U kunt het bijgewerkte bestand in de bovenliggende map exporteren in de indelingen INDD, PDF of JPG. U kunt de uitvoer in deze indelingen ook downloaden naar uw lokale bestandssysteem.

## Een hulpstuk maken {#creating-a-collateral}

Overweeg een scenario waarin u digitaal afdrukbaar materiaal wilt maken, zoals brochures, vliegers en advertenties voor een komende campagne en wereldwijd wilt delen met verkooppunten. Het creëren van onderpand dat op een malplaatje wordt gebaseerd helpt een verenigde klantenervaring over kanalen leveren. Ontwerpers kunnen de campagnemalplaatjes (enig-pagina of multi-page) tot stand brengen gebruikend een creatieve oplossing, zoals [!DNL InDesign] en de malplaatjes uploaden aan [!DNL Experience Manager Assets] voor u. Voordat u een hulpstuk maakt, moet u een of meer INDD-sjablonen vooraf uploaden naar en beschikbaar hebben in [!DNL Experience Manager] .

1. Selecteer [!UICONTROL Assets] in de interface van [!DNL Experience Manager] .

1. Kies uit de opties **[!UICONTROL Templates]** .

   ![ chlimage_1-101 ](assets/chlimage_1-306.png)

1. Selecteer **[!UICONTROL Create]** en kies vervolgens in het menu het element dat u wilt maken. Kies bijvoorbeeld **[!UICONTROL Brochure]** .

   ![ chlimage_1-102 ](assets/chlimage_1-307.png)

1. Een of meer INDD-sjablonen vooraf uploaden naar en beschikbaar hebben in [!DNL Experience Manager] . Kies een sjabloon voor de brochure en klik op **[!UICONTROL Next]** .
1. Geef een naam en een optionele beschrijving voor de brochure op.

   ![ chlimage_1-104 ](assets/chlimage_1-309.png)

1. (Optioneel) Klik op **[!UICONTROL Tags]** en selecteer een of meer tags voor de brochure. Klik op **[!UICONTROL Confirm]** om uw selectie te bevestigen.
1. Klik op **[!UICONTROL Create]**. Een dialoogvenster bevestigt dat er een nieuwe brochure wordt gemaakt. Klik op **[!UICONTROL Open]** om de brochure te openen in de bewerkingsmodus.

   <!--![chlimage_1-106](assets/.png) -->

   U kunt ook het dialoogvenster sluiten en naar de map op de pagina Sjablonen gaan waarmee u bent begonnen om de brochure weer te geven die u hebt gemaakt. Het type van het onderpand verschijnt op zijn duimnagel in kaartmening. In dit geval wordt het woord [!UICONTROL Brochure] bijvoorbeeld weergegeven op de miniatuur.

   ![ chlimage_1-107 ](assets/chlimage_1-312.png)

## Een hulpstuk bewerken {#editing-a-collateral}

U kunt een hulpstuk direct bewerken nadat u het hebt gemaakt. U kunt het bestand ook openen vanaf de pagina [!UICONTROL Templates] of de pagina Element.

1. Voer een van de volgende handelingen uit om het onderpand te openen voor bewerking:

   * Open het onderpand (brochure in dit geval) u in stap 7 van [ creeerde een onderpandsstuk ](/help/assets/asset-templates.md#creating-a-collateral).
   * Navigeer op de pagina Sjablonen naar de map waarin u het onderpand hebt gemaakt en klik op de [!UICONTROL Edit] snelle actie op de miniatuur van een hulpstuk.
   * Klik op **[!UICONTROL Edit]** op de werkbalk op de elementpagina voor het element.
   * Selecteer het onderpand en klik **[!UICONTROL Edit]** van de toolbar.

   <!--![chlimage_1-108](assets/chlimage_1-313.png) -->

   De elementenzoeker en de teksteditor worden links op de pagina weergegeven. De teksteditor is standaard geopend.

   Met de teksteditor kunt u de tekst wijzigen die u in het tekstveld wilt weergeven. U kunt de tekengrootte, stijl, kleur en tekst op tagniveau wijzigen.

   Als u de functie voor het zoeken naar elementen wilt gebruiken, kunt u bladeren naar afbeeldingen in [!DNL Experience Manager Assets] en de bewerkbare afbeeldingen in de sjabloon vervangen door afbeeldingen van uw keuze.

   ![ chlimage_1-109 ](assets/chlimage_1-314.png)

   De bewerkbare afbeeldingen worden rechts weergegeven. Een veld kan alleen worden bewerkt in [!DNL Experience Manager Assets] als het bijbehorende veld in de sjabloon is gelabeld in [!DNL InDesign] . Met andere woorden, ze moeten worden gemarkeerd als bewerkbaar in [!DNL InDesign] .

   >[!NOTE]
   >
   >Integreer uw [!DNL Experience Manager] -implementatie met een [!DNL InDesign Server] zodat [!DNL Experience Manager Assets] gegevens kan extraheren uit de [!DNL InDesign] -sjabloon en deze beschikbaar kan maken voor bewerking. Voor details, zie [ Experience Manager Assets met InDesign Server ](/help/assets/indesign.md) integreren.

1. Als u de tekst in een bewerkbaar veld wilt wijzigen, klikt u op het tekstveld in de lijst met bewerkbare velden en bewerkt u de tekst in het veld.

   ![ chlimage_1-111 ](assets/chlimage_1-316.png)

   U kunt de teksteigenschappen, zoals lettertypestijl, -kleur en -grootte, bewerken met de beschikbare opties.

1. Selecteer **[!UICONTROL Preview]** om een voorvertoning van de tekstwijzigingen weer te geven.

1. Om een beeld te ruilen, selecteer **[!UICONTROL Asset Finder]** ![ chlimage_1-113 ](assets/chlimage_1-318.png).

1. Selecteer het afbeeldingsveld in de lijst met bewerkbare velden en sleep een gewenste afbeelding van de elementkiezer naar het bewerkbare veld.

   ![ chlimage_1-114 ](assets/chlimage_1-319.png)

   U kunt ook naar afbeeldingen zoeken met behulp van trefwoorden, tags en op basis van hun publicatiestatus. U kunt door de [!DNL Experience Manager Assets] -opslagplaats bladeren en naar de locatie van de gewenste afbeelding navigeren.

   ![ chlimage_1-115 ](assets/chlimage_1-320.png)

1. Selecteer **[!UICONTROL Preview]** om een voorvertoning van de afbeelding weer te geven.
1. Als u een specifieke pagina in een pagina-element wilt bewerken dat uit meerdere pagina&#39;s bestaat, gebruikt u de paginanavigator onderaan.

1. Selecteer **[!UICONTROL Preview]** op de werkbalk, zodat u een voorvertoning van alle wijzigingen kunt weergeven. Selecteer **[!UICONTROL Done]** om de bewerkingswijzigingen in het hulpstuk op te slaan.

   >[!NOTE]
   >
   >De opties Voorbeeld en Gereed zijn alleen ingeschakeld wanneer de bewerkbare afbeeldingsvelden in het onderpand geen ontbrekende pictogrammen hebben. Als er pictogrammen ontbreken in het onderpand, komt dat doordat [!DNL Experience Manager] de afbeeldingen in de [!DNL InDesign] -sjabloon niet kan oplossen. Doorgaans kan [!DNL Experience Manager] geen afbeeldingen oplossen in de volgende gevallen:
   >
   >* Afbeeldingen worden niet ingesloten in de onderliggende [!DNL InDesign] -sjabloon.
   >* Afbeeldingen worden gekoppeld vanuit het lokale bestandssysteem.
   >
   >Ga als volgt te werk om [!DNL Experience Manager] in te schakelen om afbeeldingen op te lossen:
   >
   >* Sluit beelden in terwijl het creëren van [!DNL InDesign] malplaatjes (zie [ Ongeveer verbindingen en ingebedde grafiek ](https://helpx.adobe.com/indesign/using/graphics-links.html)).
   >* Koppel [!DNL Experience Manager] aan uw lokale bestandssysteem en wijs de ontbrekende pictogrammen toe aan bestaande elementen in [!DNL Experience Manager] .
   >

1. Als u een PDF-uitvoering voor de brochure wilt genereren, selecteert u de optie Acrobat in het dialoogvenster en klikt u op **[!UICONTROL Continue]** .
1. Het hulpstuk wordt gecreeerd in de omslag die u met begon. Als u de vertoningen wilt weergeven, opent u het desbetreffende element en kiest u **[!UICONTROL Renditions]** in de lijst GlobalNav.

   ![ chlimage_1-118 ](assets/chlimage_1-323.png)

1. Selecteer de PDF-uitvoering in de lijst met uitvoeringen, zodat u het PDF-bestand kunt downloaden. Open het PDF-bestand om het onderpand te bekijken.

   ![ chlimage_1-119 ](assets/chlimage_1-324.png)

## Zekerheden samenvoegen {#merge-collateral}

1. Selecteer in de interface [!DNL Experience Manager] de optie [!UICONTROL Assets] op de navigatiepagina.

1. Selecteer **[!UICONTROL Templates]** bij de opties.

1. Selecteer **[!UICONTROL Create]** en selecteer vervolgens in het menu **[!UICONTROL Merge]** .

   ![ chlimage_1-120 ](assets/chlimage_1-325.png)

1. Van de [!UICONTROL Template Merge] pagina, uitgezochte **[!UICONTROL Merge]** ![ voegt activa ](assets/do-not-localize/assets_add_icon.png) toe.

1. Navigeer naar de locatie van het hulpstuk dat u wilt samenvoegen, selecteer de miniaturen van het element dat u wilt samenvoegen om deze te selecteren.

   ![ chlimage_1-122 ](assets/chlimage_1-327.png)

   U kunt ook naar sjablonen zoeken in het vak Onderzoek.

   U kunt door de [!DNL Experience Manager Assets] bewaarplaats of inzamelingen doorbladeren, en aan de plaats van de gewenste malplaatjes navigeren en dan hen selecteren om samen te voegen.

   U kunt verschillende filters toepassen om de gewenste sjablonen te doorzoeken. U kunt bijvoorbeeld naar sjablonen zoeken op basis van het bestandstype of de tags.

1. Selecteer **[!UICONTROL Next]** op de werkbalk.
1. Wijzig de rangschikking van de sjablonen desgewenst in het scherm **[!UICONTROL Preview & Reorder]** en bekijk een voorvertoning van de selectie van de sjablonen die u wilt samenvoegen. Selecteer **[!UICONTROL Next]** in de werkbalk.

   ![ chlimage_1-126 ](assets/chlimage_1-331.png)

1. Geef in het scherm [!UICONTROL Configure Template] een naam op voor het element. U kunt desgewenst tags opgeven die u geschikt acht. Selecteer **[!UICONTROL Acrobat (.PDF)]** als u de uitvoer in PDF-indeling wilt exporteren. Standaard wordt het onderpand geëxporteerd in JPG- en [!DNL InDesign] -indeling. Klik op **[!UICONTROL Change Thumbnail]** als u de weergaveminiatuur voor het uit meerdere pagina&#39;s bestaande element wilt wijzigen.

   ![ chlimage_1-127 ](assets/chlimage_1-332.png)

1. Selecteer **[!UICONTROL Save]** en sluit het dialoogvenster door **[!UICONTROL OK]** te selecteren. Het uit meerdere pagina&#39;s bestaande element wordt gemaakt in de map waarmee u bent begonnen.

   >[!NOTE]
   >
   >U kunt een samengevoegd onderliggend element niet later bewerken of gebruiken om een ander onderliggend element te maken.

## Aanbevolen werkwijzen en beperkingen {#best-practices-limitations-tips}

* De [!DNL InDesign] editor in [!DNL Experience Manager] werkt op tagniveau en alle tekst onder één tag wordt als één entiteit beschouwd. Als u de tekstopmaak en stijlen tijdens het bewerken wilt behouden, moet u elke alinea (of tekst met een andere opmaak) afzonderlijk labelen.
