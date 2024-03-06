---
title: Elementsjablonen
description: Meer informatie over Asset-sjablonen in [!DNL Adobe Experience Manager Assets] en hoe u asset templates kunt gebruiken om marketingmateriaal te maken.
contentOwner: AG
role: User
feature: Asset Management,Developer Tools
exl-id: 12c92aad-3a1d-486e-a830-31de2fc6d07b
source-git-commit: 0aa929021aa724e4ec18d49fea26f8c0b0538bdc
workflow-type: tm+mt
source-wordcount: '1535'
ht-degree: 0%

---

# Elementsjablonen {#asset-templates}

Elementsjablonen zijn een speciale klasse elementen die het snel opnieuw gebruiken van visueel rijke inhoud voor digitale media en gedrukte media mogelijk maken. Een activamalplaatje omvat twee delen, de vaste overseinensectie en de editable sectie. De sectie met vaste berichten kan eigen inhoud bevatten, zoals merklogo en copyrightinformatie die zijn uitgeschakeld voor bewerking. De bewerkbare sectie kan visuele en tekstuele inhoud bevatten in velden die kunnen worden bewerkt om berichten aan te passen.

Dankzij de flexibiliteit om beperkte bewerkingen uit te voeren en de globale handtekening te beveiligen, zijn asset templates ideaal voor het maken van bouwstenen voor snelle aanpassing en distributie van inhoud als inhoudsartefacten voor verschillende functies. Door inhoud te hergebruiken, worden de kosten voor het beheer van afdruk- en digitale kanalen verlaagd en kunnen holistische en consistente ervaringen op deze kanalen worden opgedaan.

Als markeerteken kunt u sjablonen opslaan en beheren in [!DNL Experience Manager Assets] en gebruik één basissjabloon om eenvoudig meerdere persoonlijke afdrukervaringen te maken. U kunt diverse soorten marketing onderpand, met inbegrip van brochures, vliegers, postcards, visitekaartjes, etc. tot stand brengen, om uw marketing bericht aan klanten lucently over te brengen. U kunt ook uitvoer van meerdere pagina&#39;s samenstellen op basis van bestaande of nieuwe afdrukuitvoerbestanden. Met name kunt u tegelijkertijd eenvoudig zowel digitale als afdrukervaringen bieden, zodat gebruikers een consistente, geïntegreerde ervaring hebben.

Elementsjablonen zijn meestal [!DNL Adobe InDesign] bestanden, kennis van [!DNL Adobe InDesign] is geen belemmering voor het creëren van stellaire artefacten. U hoeft de velden van uw [!DNL Adobe InDesign] sjabloon met uw productvelden die u anders nodig hebt bij het maken van catalogi. U kunt de sjablonen in de WYSIWYG-modus rechtstreeks in de webinterface bewerken. Voor [!DNL Adobe InDesign] om uw het uitgeven veranderingen te verwerken, moet u eerst vormen [!DNL Experience Manager Assets] om te integreren met [!DNL Adobe InDesign Server].

Bewerkbaarheid [!DNL Adobe InDesign] sjablonen van de webinterface bevorderen een betere samenwerking tussen creatief en marketingpersoneel. De verhoogde snelheid van de inhoud vermindert de tijd-aan-markt voor marketing zekerheden.

U kunt het volgende bereiken met middelensjablonen:

* Bewerkbare sjabloonvelden wijzigen vanuit de webinterface.
* Hiermee bepaalt u de basisopmaak van tekst, zoals tekengrootte, stijl en tekst op tagniveau.
* Wijzig de afbeeldingen in de sjabloon met de inhoudkiezer.
* Sjabloonbewerkingen voorvertonen.
* Voeg meerdere sjabloonbestanden samen, zodat u een vervorming van meerdere pagina&#39;s kunt maken.

Wanneer u een sjabloon voor uw onderpand kiest, [!DNL Experience Manager Assets] Hiermee maakt u een kopie van de sjabloon die u kunt bewerken. De oorspronkelijke sjabloon blijft behouden, zodat uw globale handtekening intact blijft en opnieuw kan worden gebruikt om de consistentie van uw merk te handhaven.

U kunt het bijgewerkte bestand in de bovenliggende map exporteren in de indelingen INDD, PDF of JPG. U kunt de uitvoer in deze indelingen ook downloaden naar uw lokale bestandssysteem.

## Een hulpstuk maken {#creating-a-collateral}

Overweeg een scenario waarin u digitaal afdrukbaar materiaal wilt maken, zoals brochures, vliegers en advertenties voor een komende campagne en wereldwijd wilt delen met verkooppunten. Het creëren van onderpand dat op een malplaatje wordt gebaseerd helpt een verenigde klantenervaring over kanalen leveren. Ontwerpers kunnen de campagnemalplaatjes (enige pagina of multi-page) tot stand brengen gebruikend een creatieve oplossing, zoals [!DNL InDesign] en upload de sjablonen naar [!DNL Experience Manager Assets] voor jou. Voordat u een hulpstuk maakt, moet u een of meer INDD-sjablonen uploaden naar en beschikbaar hebben in [!DNL Experience Manager] vooraf.

1. In de [!DNL Experience Manager] interface, selecteren [!UICONTROL Assets].

1. Kies in de opties de optie **[!UICONTROL Templates]**.

   ![chlimage_1-101](assets/chlimage_1-306.png)

1. Selecteren **[!UICONTROL Create]** en kiest u vervolgens in het menu het element dat u wilt maken. Kies bijvoorbeeld **[!UICONTROL Brochure]**.

   ![chlimage_1-102](assets/chlimage_1-307.png)

1. Een of meer INDD-sjablonen hebben geüpload naar en beschikbaar in [!DNL Experience Manager] vooraf. Kies een sjabloon voor de brochure en klik op **[!UICONTROL Next]**.
1. Geef een naam en een optionele beschrijving voor de brochure op.

   ![chlimage_1-104](assets/chlimage_1-309.png)

1. (Optioneel) Klik op **[!UICONTROL Tags]** en selecteer een of meer tags voor de brochure. Klikken **[!UICONTROL Confirm]** om uw selectie te bevestigen.
1. Klik op **[!UICONTROL Create]**. Een dialoogvenster bevestigt dat er een nieuwe brochure wordt gemaakt. Klikken **[!UICONTROL Open]** om de brochure te openen in de bewerkingsmodus.

   <!--![chlimage_1-106](assets/.png) -->

   U kunt ook het dialoogvenster sluiten en naar de map op de pagina Sjablonen gaan waarmee u bent begonnen om de brochure weer te geven die u hebt gemaakt. Het type van het onderpand verschijnt op zijn duimnagel in kaartmening. In dit geval wordt bijvoorbeeld het woord [!UICONTROL Brochure] wordt weergegeven op de miniatuur.

   ![chlimage_1-107](assets/chlimage_1-312.png)

## Een hulpstuk bewerken {#editing-a-collateral}

U kunt een hulpstuk direct bewerken nadat u het hebt gemaakt. U kunt het bestand ook openen vanuit het dialoogvenster [!UICONTROL Templates] pagina of de elementpagina.

1. Voer een van de volgende handelingen uit om het onderpand te openen voor bewerking:

   * Open het onderpand (brochure in dit geval) dat u in stap 7 van [Een hulpstuk maken](/help/assets/asset-templates.md#creating-a-collateral).
   * Navigeer op de pagina Sjablonen naar de map waarin u het onderpand hebt gemaakt en klik op de knop [!UICONTROL Edit] snelle actie op de duimnagel van een hulpstuk.
   * Klik op de elementpagina voor de zekerheid op **[!UICONTROL Edit]** op de werkbalk.
   * Selecteer het onderpand en klik **[!UICONTROL Edit]** op de werkbalk.

   <!--![chlimage_1-108](assets/chlimage_1-313.png) -->

   De elementenzoeker en de teksteditor worden links op de pagina weergegeven. De teksteditor is standaard geopend.

   Met de teksteditor kunt u de tekst wijzigen die u in het tekstveld wilt weergeven. U kunt de tekengrootte, stijl, kleur en tekst op tagniveau wijzigen.

   Als u de functie voor zoeken naar elementen wilt gebruiken, kunt u in [!DNL Experience Manager Assets] en vervangt u de bewerkbare afbeeldingen in de sjabloon door de gewenste afbeeldingen.

   ![chlimage_1-109](assets/chlimage_1-314.png)

   De bewerkbare afbeeldingen worden rechts weergegeven. Een veld dat bewerkbaar moet zijn in [!DNL Experience Manager Assets], moet het desbetreffende veld in de sjabloon worden gelabeld in [!DNL InDesign]. Met andere woorden, ze moeten worden gemarkeerd als bewerkbaar in [!DNL InDesign].

   >[!NOTE]
   >
   >Zorg ervoor dat uw [!DNL Experience Manager] implementatie is geïntegreerd met een [!DNL InDesign Server] om [!DNL Experience Manager Assets] om gegevens te extraheren uit de [!DNL InDesign] en ter beschikking stellen voor bewerken. Zie voor meer informatie [Experience Manager Assets integreren met InDesign Server](/help/assets/indesign.md).

1. Als u de tekst in een bewerkbaar veld wilt wijzigen, klikt u op het tekstveld in de lijst met bewerkbare velden en bewerkt u de tekst in het veld.

   ![chlimage_1-111](assets/chlimage_1-316.png)

   U kunt de teksteigenschappen, zoals lettertypestijl, -kleur en -grootte, bewerken met de beschikbare opties.

1. Selecteren **[!UICONTROL Preview]** zodat u een voorvertoning van de tekstwijzigingen kunt bekijken.

1. Als u een afbeelding wilt wisselen, selecteert u de optie **[!UICONTROL Asset Finder]** ![chlimage_1-113](assets/chlimage_1-318.png).

1. Selecteer het afbeeldingsveld in de lijst met bewerkbare velden en sleep een gewenste afbeelding van de elementkiezer naar het bewerkbare veld.

   ![chlimage_1-114](assets/chlimage_1-319.png)

   U kunt ook naar afbeeldingen zoeken met behulp van trefwoorden, tags en op basis van hun publicatiestatus. U kunt door [!DNL Experience Manager Assets] en navigeer naar de locatie van de gewenste afbeelding.

   ![chlimage_1-115](assets/chlimage_1-320.png)

1. Selecteren **[!UICONTROL Preview]** zodat u een voorvertoning van de afbeelding kunt bekijken.
1. Als u een specifieke pagina in een pagina-element wilt bewerken dat uit meerdere pagina&#39;s bestaat, gebruikt u de paginanavigator onderaan.

1. Selecteren **[!UICONTROL Preview]** op de werkbalk, zodat u een voorvertoning van alle wijzigingen kunt weergeven. Selecteren **[!UICONTROL Done]** om de bewerkingswijzigingen in het hulpstuk op te slaan.

   >[!NOTE]
   >
   >De opties Voorbeeld en Gereed zijn alleen ingeschakeld wanneer de bewerkbare afbeeldingsvelden in het onderpand geen ontbrekende pictogrammen hebben. Als er pictogrammen ontbreken in het onderpand, komt dat omdat [!DNL Experience Manager] kan de afbeeldingen in het dialoogvenster [!DNL InDesign] sjabloon. Gewoonlijk [!DNL Experience Manager] kan geen afbeeldingen oplossen in de volgende gevallen:
   >
   >* Afbeeldingen worden niet in de onderliggende afbeelding ingesloten [!DNL InDesign] sjabloon.
   >* Afbeeldingen worden gekoppeld vanuit het lokale bestandssysteem.
   >
   >Inschakelen [!DNL Experience Manager] Voer de volgende handelingen uit om afbeeldingen op te lossen:
   >
   >* Afbeeldingen insluiten tijdens het maken [!DNL InDesign] sjablonen (zie [Over koppelingen en ingesloten afbeeldingen](https://helpx.adobe.com/indesign/using/graphics-links.html)).
   >* Koppelen [!DNL Experience Manager] naar uw lokale bestandssysteem en wijs vervolgens ontbrekende pictogrammen toe met bestaande elementen in [!DNL Experience Manager].
   >
   >Meer informatie over werken met [!DNL InDesign] documenten, zie [aanbevolen procedures voor het werken met InDesigns documenten in Experience Manager](https://helpx.adobe.com/experience-manager/kb/best-practices-idd-docs-aem.html).

1. Als u een PDF-uitvoering voor de brochure wilt genereren, selecteert u de Acrobat-optie in het dialoogvenster en klikt u op **[!UICONTROL Continue]**.
1. Het hulpstuk wordt gecreeerd in de omslag die u met begon. Als u de vertoningen wilt bekijken, opent u het onderpand en kiest u **[!UICONTROL Renditions]** uit de lijst GlobalNav.

   ![chlimage_1-118](assets/chlimage_1-323.png)

1. Selecteer de PDF-uitvoering in de lijst met uitvoeringen, zodat u het PDF-bestand kunt downloaden. Open het PDF-bestand om het onderpand te bekijken.

   ![chlimage_1-119](assets/chlimage_1-324.png)

## Zekerheden samenvoegen {#merge-collateral}

1. In de [!DNL Experience Manager] interface, selecteren [!UICONTROL Assets] op de navigatiepagina.

1. Selecteer in de opties de optie **[!UICONTROL Templates]**.

1. Selecteren **[!UICONTROL Create]** Selecteer vervolgens in het menu de optie **[!UICONTROL Merge]**.

   ![chlimage_1-120](assets/chlimage_1-325.png)

1. Van de [!UICONTROL Template Merge] pagina, selecteert u **[!UICONTROL Merge]** ![elementen toevoegen](assets/do-not-localize/assets_add_icon.png).

1. Navigeer naar de locatie van het hulpstuk dat u wilt samenvoegen, selecteer de miniaturen van het element dat u wilt samenvoegen om deze te selecteren.

   ![chlimage_1-122](assets/chlimage_1-327.png)

   U kunt ook naar sjablonen zoeken in het vak Onderzoek.

   U kunt door [!DNL Experience Manager Assets] bewaarplaats of inzamelingen, en navigeer aan de plaats van de gewenste malplaatjes en selecteer dan hen om samen te voegen.

   U kunt verschillende filters toepassen om de gewenste sjablonen te doorzoeken. U kunt bijvoorbeeld naar sjablonen zoeken op basis van het bestandstype of de tags.

1. Selecteren **[!UICONTROL Next]** op de werkbalk.
1. In de **[!UICONTROL Preview & Reorder]** , indien nodig de sjablonen opnieuw rangschikken en een voorvertoning weergeven van de selectie van de sjablonen die u wilt samenvoegen. Selecteer **[!UICONTROL Next]** in de werkbalk.

   ![chlimage_1-126](assets/chlimage_1-331.png)

1. In de [!UICONTROL Configure Template] -scherm, geeft u een naam op voor het onderpand. U kunt desgewenst tags opgeven die u geschikt acht. Als u de uitvoer wilt exporteren in de indeling PDF, selecteert u **[!UICONTROL Acrobat (.PDF)]**. Standaard wordt de zekerheid geëxporteerd in JPG en [!DNL InDesign] gebruiken. Klik op **[!UICONTROL Change Thumbnail]**.

   ![chlimage_1-127](assets/chlimage_1-332.png)

1. Selecteren **[!UICONTROL Save]** en sluit vervolgens het dialoogvenster door **[!UICONTROL OK]**. Het uit meerdere pagina&#39;s bestaande element wordt gemaakt in de map waarmee u bent begonnen.

   >[!NOTE]
   >
   >U kunt een samengevoegd onderliggend element niet later bewerken of gebruiken om een ander onderliggend element te maken.

## Aanbevolen werkwijzen en beperkingen {#best-practices-limitations-tips}

* De [!DNL InDesign] editor in [!DNL Experience Manager] werkt op labelniveau en alle tekst onder één label wordt beschouwd als één geheel. Als u de tekstopmaak en stijlen tijdens het bewerken wilt behouden, moet u elke alinea (of tekst met een andere opmaak) afzonderlijk labelen.
