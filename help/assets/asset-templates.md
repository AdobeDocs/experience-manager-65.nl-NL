---
title: Elementsjablonen
description: Leer over de malplaatjes van Activa in [!DNL Adobe Experience Manager Assets] en hoe te om activamalplaatjes te gebruiken om marketing onderpand tot stand te brengen.
contentOwner: AG
translation-type: tm+mt
source-git-commit: f9f745369ba0fe242dea1e5a5e5af0b8263b1ec0
workflow-type: tm+mt
source-wordcount: '1503'
ht-degree: 0%

---


# Elementsjablonen {#asset-templates}

Elementsjablonen zijn een speciale klasse elementen die het snel opnieuw gebruiken van visueel rijke inhoud voor digitale media en gedrukte media mogelijk maken. Een activamalplaatje omvat twee delen, de vaste overseinensectie en de editable sectie. De sectie met vaste berichten kan eigen inhoud bevatten, zoals merklogo en copyrightinformatie die zijn uitgeschakeld voor bewerking. De bewerkbare sectie kan visuele en tekstuele inhoud bevatten in velden die kunnen worden bewerkt om berichten aan te passen.

Dankzij de flexibiliteit om beperkte bewerkingen uit te voeren en de globale handtekening te beveiligen, zijn asset templates ideaal voor het maken van bouwstenen voor snelle aanpassing en distributie van inhoud als inhoudsartefacten voor verschillende functies. Inhoud die opnieuw wordt gebruikt, helpt de kosten voor het beheer van afdruk- en digitale kanalen te verlagen en biedt holistische en consistente ervaringen op deze kanalen.

Als markeerteken kunt u sjablonen opslaan en beheren binnen [!DNL Experience Manager Assets] en één basissjabloon gebruiken om eenvoudig meerdere persoonlijke afdrukervaringen te maken. U kunt diverse soorten marketing onderpand, met inbegrip van brochures, vliegers, postcards, visitekaartjes, etc. tot stand brengen om uw marketing bericht aan klanten lucently over te brengen. U kunt ook uitvoer van meerdere pagina&#39;s samenstellen op basis van bestaande of nieuwe afdrukuitvoer. Met name kunt u tegelijkertijd eenvoudig zowel digitale als afdrukervaringen bieden, zodat gebruikers een consistente, geïntegreerde ervaring hebben.

Elementsjablonen zijn meestal [!DNL Adobe InDesign] bestanden, maar de vaardigheid in [!DNL Adobe InDesign] vormt geen belemmering voor het maken van stellaire artefacten. U hoeft de velden van uw [!DNL Adobe InDesign]-sjabloon niet toe te wijzen aan de productvelden die u anders nodig hebt bij het maken van catalogi. U kunt de sjablonen in de WYSIWYG-modus rechtstreeks in de webinterface bewerken. Als u uw bewerkingswijzigingen echter wilt verwerken, moet u [!DNL Adobe InDesign] eerst configureren voor integratie met [!DNL Experience Manager Assets].[!DNL Adobe InDesign Server]

De mogelijkheid om [!DNL Adobe InDesign]-sjablonen vanuit de webinterface te bewerken helpt een betere samenwerking tussen creatief en marketingpersoneel te bevorderen. De verhoogde snelheid van de inhoud vermindert de tijd-aan-markt voor marketing zekerheden.

U kunt het volgende bereiken met middelensjablonen:

* Bewerkbare sjabloonvelden wijzigen vanuit de webinterface.
* Hiermee bepaalt u de basisopmaak van tekst, zoals tekengrootte, stijl en tekst op tagniveau.
* Wijzig de afbeeldingen in de sjabloon met de inhoudkiezer.
* Sjabloonbewerkingen voorvertonen.
* Voeg meerdere sjabloonbestanden samen om een vervorming van meerdere pagina&#39;s te maken.

Wanneer u een sjabloon voor uw onderpand kiest, [!DNL Experience Manager Assets] creeert een exemplaar van het malplaatje dat u kunt uitgeven. De oorspronkelijke sjabloon blijft behouden, zodat uw globale handtekening intact blijft en opnieuw kan worden gebruikt om de consistentie van uw merk te handhaven.

U kunt het bijgewerkte bestand in de bovenliggende map exporteren in de indelingen INDD, PDF of JPG. U kunt de uitvoer in deze indelingen ook downloaden naar uw lokale bestandssysteem.

## Een zekerheid {#creating-a-collateral} maken

Overweeg een scenario waarin u digitaal afdrukbaar materiaal wilt maken, zoals brochures, vliegers en advertenties voor een komende campagne en wereldwijd wilt delen met verkooppunten. Het creëren van onderpand dat op een malplaatje wordt gebaseerd helpt een verenigde klantenervaring over kanalen leveren. Ontwerpers kunnen de campagnemalplaatjes (enig-pagina of multi-page) tot stand brengen gebruikend een creatieve oplossing, zoals [!DNL InDesign] en de malplaatjes uploaden aan [!DNL Experience Manager Assets] voor u. Voordat u een zekerheid maakt, moet u een of meer INDD-sjablonen vooraf uploaden naar en beschikbaar hebben in [!DNL Experience Manager].

1. Klik in [!DNL Experience Manager] interface [!UICONTROL Assets].

1. Kies **[!UICONTROL Templates]** uit de opties.

   ![chlimage_1-101](assets/chlimage_1-306.png)

1. Klik **[!UICONTROL Create]**, en kies dan het onderpand u van het menu wilt creëren. Kies bijvoorbeeld **[!UICONTROL Brochure]**.

   ![chlimage_1-102](assets/chlimage_1-307.png)

1. Een of meer INDD-sjablonen vooraf uploaden naar en beschikbaar hebben in [!DNL Experience Manager]. Kies een sjabloon voor de brochure en klik op **[!UICONTROL Next]**.
1. Geef een naam en een optionele beschrijving voor de brochure op.

   ![chlimage_1-104](assets/chlimage_1-309.png)

1. (Optioneel) Klik op **[!UICONTROL Tags]** en selecteer een of meer tags voor de brochure. Klik **[!UICONTROL Confirm]** om uw selectie te bevestigen.
1. Klik op **[!UICONTROL Create]**. Een dialoogvenster bevestigt dat er een nieuwe brochure wordt gemaakt. Klik op **[!UICONTROL Open]** om de brochure te openen in de bewerkingsmodus.

   <!--![chlimage_1-106](assets/.png) -->

   U kunt ook het dialoogvenster sluiten en naar de map op de pagina Sjablonen gaan waarmee u bent begonnen om de brochure weer te geven die u hebt gemaakt. Het type van het onderpand verschijnt op zijn duimnagel in kaartmening. In dit geval wordt bijvoorbeeld het woord [!UICONTROL Brochure] weergegeven op de miniatuur.

   ![chlimage_1-107](assets/chlimage_1-312.png)

## Een zekerheid {#editing-a-collateral} bewerken

U kunt direct nadat u het hebt gemaakt, een onderpand bewerken. U kunt de sjabloon ook openen vanaf de pagina [!UICONTROL Templates] of de elementpagina.

1. Voer een van de volgende handelingen uit om het onderpand te openen voor bewerking:

   * Open het onderpand (brochure in dit geval) u in stap 7 van [creeerde een onderpand](/help/assets/asset-templates.md#creating-a-collateral).
   * Navigeer op de pagina Sjablonen naar de map waarin u het onderpand hebt gemaakt en klik op de snelle handeling [!UICONTROL Edit] op de miniatuur van een onderpand.
   * Klik op **[!UICONTROL Edit]** op de werkbalk op de elementpagina voor het onderpand.
   * Selecteer het onderpand en klik **[!UICONTROL Edit]** van de toolbar.

   <!--![chlimage_1-108](assets/chlimage_1-313.png) -->

   De elementenzoeker en de teksteditor worden links op de pagina weergegeven. De teksteditor is standaard geopend.

   U kunt de teksteditor gebruiken om de tekst te wijzigen die u in het tekstveld wilt weergeven. U kunt de tekengrootte, stijl, kleur en tekst op tagniveau wijzigen.

   Met behulp van de zoekfunctie voor elementen kunt u bladeren naar afbeeldingen in [!DNL Experience Manager Assets] en de bewerkbare afbeeldingen in de sjabloon vervangen door afbeeldingen van uw keuze.

   ![chlimage_1-189](assets/chlimage_1-314.png)

   De bewerkbare tekst wordt rechts weergegeven. Een veld kan alleen worden bewerkt in [!DNL Experience Manager Assets] als het desbetreffende veld in de sjabloon is gelabeld in [!DNL InDesign]. Met andere woorden, ze moeten worden gemarkeerd als bewerkbaar in [!DNL InDesign].

   >[!NOTE]
   >
   >Zorg ervoor dat uw [!DNL Experience Manager]-implementatie is geïntegreerd met een [!DNL InDesign Server] om [!DNL Experience Manager Assets] in staat te stellen gegevens te extraheren uit de [!DNL InDesign]-sjabloon en deze beschikbaar te maken voor bewerking. Zie [Elementen van Experience Managers integreren met InDesign Server](/help/assets/indesign.md) voor meer informatie.

1. Als u de tekst in een bewerkbaar veld wilt wijzigen, klikt u op het tekstveld in de lijst met bewerkbare velden en bewerkt u de tekst in het veld.

   ![chlimage_1-111](assets/chlimage_1-316.png)

   U kunt de teksteigenschappen, zoals lettertypestijl, -kleur en -grootte, bewerken met de beschikbare opties.

1. Klik **[!UICONTROL Preview]** om een voorvertoning van de tekstwijzigingen weer te geven.

1. Als u een afbeelding wilt omwisselen, klikt u op **[!UICONTROL Asset Finder]** ![chlimage_1-113](assets/chlimage_1-318.png).

1. Selecteer het afbeeldingsveld in de lijst met bewerkbare velden en sleep een gewenste afbeelding van de elementkiezer naar het bewerkbare veld.

   ![chlimage_1-115](assets/chlimage_1-319.png)

   U kunt ook naar afbeeldingen zoeken met behulp van trefwoorden, tags en op basis van hun publicatiestatus. U kunt door [!DNL Experience Manager Assets] bewaarplaats doorbladeren en aan de plaats van het gewenste beeld navigeren.

   ![chlimage_1-114](assets/chlimage_1-320.png)

1. Klik op **[!UICONTROL Preview]** om een voorvertoning van de afbeelding weer te geven.
1. Als u een specifieke pagina in een pagina-element wilt bewerken dat uit meerdere pagina&#39;s bestaat, gebruikt u de paginanavigator onderaan.

1. Klik op **[!UICONTROL Preview]** op de werkbalk om een voorvertoning van alle wijzigingen weer te geven. Klik **[!UICONTROL Done]** om de het uitgeven veranderingen in het onderpand te bewaren.

   >[!NOTE]
   >
   >De opties Voorbeeld en Gereed zijn alleen ingeschakeld wanneer de bewerkbare afbeeldingsvelden in het onderpand geen ontbrekende pictogrammen hebben. Als er pictogrammen ontbreken in uw onderpand, komt dit omdat [!DNL Experience Manager] de afbeeldingen in de [!DNL InDesign] sjabloon niet kan oplossen. Doorgaans kan [!DNL Experience Manager] geen afbeeldingen oplossen in de volgende gevallen:
   >
   >* Afbeeldingen worden niet ingesloten in de onderliggende [!DNL InDesign]-sjabloon.
   >* Afbeeldingen worden gekoppeld vanuit het lokale bestandssysteem.

   >
   >Ga als volgt te werk om [!DNL Experience Manager] in te schakelen om afbeeldingen op te lossen:
   >
   >* Afbeeldingen insluiten tijdens het maken van [!DNL InDesign]-sjablonen (zie [Over koppelingen en ingesloten afbeeldingen](https://helpx.adobe.com/indesign/using/graphics-links.html)).
   >* Koppel [!DNL Experience Manager] aan uw lokale bestandssysteem en wijs vervolgens ontbrekende pictogrammen toe aan bestaande elementen in [!DNL Experience Manager].

   >
   >Zie [aanbevolen procedures voor het werken met InDesign-documenten in Experience Manager](https://helpx.adobe.com/experience-manager/kb/best-practices-idd-docs-aem.html) voor meer informatie over het werken met [!DNL InDesign]-documenten.

1. Als u een PDF-uitvoering voor de brochure wilt genereren, selecteert u de optie Acrobat in het dialoogvenster en klikt u op **[!UICONTROL Continue]**.
1. Het onderpand wordt gecreeerd in de omslag u met begon. Als u de vertoningen wilt weergeven, opent u het desbetreffende element en kiest u **[!UICONTROL Renditions]** in de lijst GlobalNav.

   ![chlimage_1-118](assets/chlimage_1-323.png)

1. Klik op de PDF-uitvoering in de lijst met uitvoeringen om het PDF-bestand te downloaden. Open het PDF-bestand om het onderpand te bekijken.

   ![chlimage_1-119](assets/chlimage_1-324.png)

## Onderpanden {#merge-collateral} samenvoegen

1. Klik in de interface [!DNL Experience Manager] op [!UICONTROL Assets] op de navigatiepagina.

1. Kies **[!UICONTROL Templates]** uit de opties.

1. Klik op **[!UICONTROL Create]** en kies **[!UICONTROL Merge]** in het menu.

   ![chlimage_1-120](assets/chlimage_1-325.png)

1. Klik op [!UICONTROL Template Merge] ![Elementen toevoegen](assets/do-not-localize/assets_add_icon.png) op de pagina &lt;a0/>.**[!UICONTROL Merge]**

1. Navigeer naar de locatie van de elementen die u wilt samenvoegen en klik op de miniaturen van de elementen die u wilt samenvoegen om deze te selecteren.

   ![chlimage_1-122](assets/chlimage_1-327.png)

   U kunt ook naar sjablonen zoeken in het vak Onderzoek.

   U kunt door [!DNL Experience Manager Assets] bewaarplaats of inzamelingen doorbladeren, en aan de plaats van de gewenste malplaatjes navigeren en dan hen selecteren om samen te voegen.

   U kunt verschillende filters toepassen om de gewenste sjablonen te doorzoeken. U kunt bijvoorbeeld naar sjablonen zoeken op basis van het bestandstype of de tags.

1. Klik op **[!UICONTROL Next]** op de werkbalk.
1. Wijzig in het scherm **[!UICONTROL Preview & Reorder]** desgewenst de sjablonen en geef een voorvertoning weer van de sjablonen die u wilt samenvoegen. Klik vervolgens op **[!UICONTROL Next]** op de werkbalk.

   ![chlimage_1-126](assets/chlimage_1-331.png)

1. Geef in het scherm [!UICONTROL Configure Template] een naam op voor het onderpand. U kunt desgewenst tags opgeven die u geschikt acht. Selecteer **[!UICONTROL Acrobat (.PDF)]** als u de uitvoer in PDF-indeling wilt exporteren. Standaard wordt het onderpand geëxporteerd in de JPG- en [!DNL InDesign]-indeling. Als u de weergaveminiatuur voor het uit meerdere pagina&#39;s bestaande element wilt wijzigen, klikt u op **[!UICONTROL Change Thumbnail]**.

   ![chlimage_1-127](assets/chlimage_1-332.png)

1. Klik op **[!UICONTROL Save]** en vervolgens op **[!UICONTROL OK]** in het dialoogvenster om het dialoogvenster te sluiten. Het uit meerdere pagina&#39;s bestaande element wordt gemaakt in de map waarmee u bent begonnen.

   >[!NOTE]
   >
   >U kunt een samengevoegd onderpand later niet bewerken of gebruiken om ander onderpand te maken.

## Beste werkwijzen en beperkingen {#best-practices-limitations-tips}

* De [!DNL InDesign] redacteur in [!DNL Experience Manager] werkt bij een markeringsniveau en al tekst onder één enkele markering wordt beschouwd als één enkele entiteit. Als u de tekstopmaak en stijlen tijdens het bewerken wilt behouden, moet u elke alinea (of tekst met een andere opmaak) afzonderlijk labelen.
