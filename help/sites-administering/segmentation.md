---
title: Het vormen Segmentatie met ContextHub
description: Leer hoe te om segmentatie met de Hub van de Context te vormen.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
exl-id: 8bd6c88b-f36a-422f-ae6c-0d59f365079a
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1745'
ht-degree: 0%

---

# Het vormen Segmentatie met ContextHub{#configuring-segmentation-with-contexthub}

>[!NOTE]
>
>Deze sectie beschrijft het vormen segmentatie wanneer het gebruiken van ContextHub. Als u de functionaliteit van de Context van de Cliënt gebruikt, zie de relevante documentatie voor [segmentatie configureren voor clientcontext](/help/sites-administering/campaign-segmentation.md).
>

Segmentering is een belangrijke overweging bij het maken van een campagne. Zie [Soorten publiek beheren](/help/sites-authoring/managing-audiences.md) voor informatie over hoe de segmentatie werkt en zeer belangrijke termijnen.

Afhankelijk van de informatie die u reeds over uw plaatsbezoekers en de doelstellingen hebt verzameld u wilt bereiken, moet u de segmenten en de strategieën bepalen nodig voor uw gerichte inhoud.

Deze segmenten worden vervolgens gebruikt om een bezoeker specifieke inhoud te bieden. Deze inhoud blijft behouden in het dialoogvenster [Personalisatie](/help/sites-authoring/personalization.md) van de website. [Activiteiten](/help/sites-authoring/activitylib.md) Hier gedefinieerd kan op elke pagina worden opgenomen en definiëren voor welk bezoekerssegment de gespecialiseerde inhoud van toepassing is.

Met AEM kunt u de gebruikerservaring eenvoudig aanpassen. Het laat u ook de resultaten van uw segmentdefinities verifiëren.

## Segmenten openen {#accessing-segments}

De [Soorten publiek](/help/sites-authoring/managing-audiences.md) console wordt gebruikt om segmenten voor ContextHub of de Context en het publiek van de Cliënt voor uw rekening van Adobe Target te beheren. Deze documentatie behandelt het beheren van segmenten voor ContextHub. Voor [Clientcontextsegmenten](/help/sites-administering/campaign-segmentation.md) en Adobe Target-segmenten, zie de relevante documentatie.

Om tot uw segmenten toegang te hebben moet u uw configuratie selecteren. Selecteer in globale navigatie **Navigation > Personalisatie > Soorten publiek**. De beschikbare configuraties worden weergegeven:

![Soorten publiek - configuraties](assets/segmentation-access-confs.png)

Selecteer uw configuratie om de segmenten, bijvoorbeeld, Plaats WKND te zien:

![Soorten publiek - segmenten](assets/segmentation-access-segments.png)

## Segment-editor {#segment-editor}

De **Segment-editor** Hiermee kunt u een segment gemakkelijk wijzigen. Om een segment uit te geven, selecteer een segment in [lijst van segmenten](/help/sites-administering/segmentation.md#accessing-segments) en klik op de knop **Bewerken** knop.

![segmenteditor](assets/segmenteditor.png)

Met de componentenbrowser kunt u toevoegen **EN** en **OF** containers om de segmentlogica te bepalen, dan voeg extra componenten toe om eigenschappen en waarden of verwijzingsmanuscripten en andere segmenten te vergelijken om de selectiecriteria te bepalen (zie [Een nieuw segment maken](#creating-a-new-segment)) om het exacte scenario voor het selecteren van het segment te bepalen.

Wanneer de volledige verklaring aan waar evalueert dan heeft het segment opgelost. Als er meerdere toepasselijke segmenten zijn, **Verhogen** wordt ook gebruikt. Zie [Een nieuw segment maken](#creating-a-new-segment) voor meer informatie over de [stimulerende factor.](/help/sites-administering/campaign-segmentation.md#boost-factor)

>[!CAUTION]
>
>De segmentredacteur controleert geen cirkelverwijzingen. Bijvoorbeeld, verwijst segment A naar een ander segment B, dat op zijn beurt weer naar segment A verwijst. Zorg ervoor dat uw segmenten geen cirkelverwijzingen bevatten.

### Containers {#containers}

De volgende containers zijn beschikbaar uit-van-de-doos en laten u vergelijkingen en verwijzingen samen groeperen voor booleaanse evaluatie. U kunt deze vanuit de componentbrowser naar de editor slepen. Zie de volgende sectie [AND en OR-containers gebruiken](/help/sites-administering/segmentation.md#using-and-and-or-containers) voor meer informatie .

<table>
 <tbody>
  <tr>
   <td>Container en<br /> </td>
   <td>De Booleaanse operator AND<br /> </td>
  </tr>
  <tr>
   <td>Container OF<br /> </td>
   <td>De operator Boolean OR</td>
  </tr>
 </tbody>
</table>

### Vergelijkingen {#comparisons}

De volgende segmentvergelijkingen zijn beschikbaar uit-van-de-doos om segmenteigenschappen te evalueren. U kunt deze vanuit de componentbrowser naar de editor slepen.

<table>
 <tbody>
  <tr>
   <td>Eigenschap-waarde<br /> </td>
   <td>Vergelijkt een bezit van een opslag met een bepaalde waarde<br /> </td>
  </tr>
  <tr>
   <td>Eigenschap</td>
   <td>Vergelijkt één bezit van een opslag aan een ander bezit<br /> </td>
  </tr>
  <tr>
   <td>Eigenschap-segmentverwijzing</td>
   <td>Vergelijkt een bezit van een opslag aan een ander referenced segment<br /> </td>
  </tr>
  <tr>
   <td>Eigenschapverwijzing</td>
   <td>Vergelijkt een bezit van een opslag met de resultaten van een manuscript<br /> </td>
  </tr>
  <tr>
   <td>Referentie-script voor segment</td>
   <td>Vergelijkt een segment waarnaar wordt verwezen met de resultaten van een script<br /> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Wanneer het vergelijken van waarden, als het gegevenstype van de vergelijking niet wordt geplaatst (d.w.z. wordt geplaatst om auto te ontdekken), zal de de segmenteringsmotor van ContextHub eenvoudig de waarden zoals javascript vergelijken. Er worden geen waarden naar de verwachte typen gecast, wat tot misleidende resultaten kan leiden. Bijvoorbeeld:
>
>`null < 30 // will return true`
>
>Daarom [een segment maken](/help/sites-administering/segmentation.md#creating-a-new-segment)selecteert u een **gegevenstype** wanneer de typen van de vergeleken waarden bekend zijn. Bijvoorbeeld:
>
>Bij vergelijking van de eigenschap `profile/age`, weet u reeds dat het vergeleken type zal zijn **getal**, zelfs als `profile/age` is niet ingesteld, een vergelijking `profile/age` minder dan 30 wordt geretourneerd **false**, zoals u zou verwachten.

### Verwijzingen {#references}

De volgende verwijzingen zijn beschikbaar uit-van-de-doos om rechtstreeks met een manuscript of een ander segment te verbinden. U kunt deze vanuit de componentbrowser naar de editor slepen.

<table>
 <tbody>
  <tr>
   <td>Segmentverwijzing<br /> </td>
   <td>Evalueer het referenced segment</td>
  </tr>
  <tr>
   <td>Scriptreferentie</td>
   <td>Evalueer het referenced manuscript. Zie de volgende sectie <a href="/help/sites-administering/segmentation.md#using-script-references">Scriptverwijzingen gebruiken</a> voor meer informatie .</td>
  </tr>
 </tbody>
</table>

## Een nieuw segment maken {#creating-a-new-segment}

Het nieuwe segment definiëren:

1. Na [toegang krijgen tot de segmenten](/help/sites-administering/segmentation.md#accessing-segments), [naar de map navigeren](#organizing-segments) waar u het segment wilt maken.

1. Klik op de knop Maken en selecteer **ContextHub-segment maken**.

   ![chlimage_1-311](assets/chlimage_1-311.png)

1. In de **Nieuw ContextHub-segment** Voer een titel voor het segment in en geef indien nodig een ophaalwaarde op en klik vervolgens op **Maken**.

   ![chlimage_1-312](assets/chlimage_1-312.png)

   Elk segment heeft een verhogingsparameter die als weegfactor wordt gebruikt. Een hoger getal geeft aan dat het segment bij voorkeur wordt geselecteerd boven een segment met een lager getal in gevallen waarin meerdere segmenten geldig zijn.

   * Minimumwaarde: `0`
   * Maximumwaarde: `1000000`

1. Sleep een vergelijking of een verwijzing naar de segmentredacteur het in het gebrek EN container zal verschijnen.
1. Dubbelklik op de optie voor het configureren van de nieuwe verwijzing of het nieuwe segment om de specifieke parameters te bewerken. In dit voorbeeld testen we op mensen in San Jose.

   ![screen_shot_2012-02-02at103135am](assets/screen_shot_2012-02-02at103135ama.png)

   Altijd een **Gegevenstype** indien mogelijk om ervoor te zorgen dat uw vergelijkingen correct worden geëvalueerd. Zie [Vergelijkingen](/help/sites-administering/segmentation.md#comparisons) voor meer informatie .

1. Klikken **OK** om uw definitie op te slaan:
1. Voeg desgewenst meer componenten toe. U kunt booleaanse expressies formuleren met behulp van de containercomponenten voor AND en OR vergelijkingen (zie [en/of containers gebruiken](/help/sites-administering/segmentation.md#using-and-and-or-containers) hieronder). Met de segmentredacteur kunt u componenten schrappen niet meer nodig, of hen slepen aan nieuwe posities binnen de verklaring.

### AND en OR-containers gebruiken {#using-and-and-or-containers}

Gebruikend EN en OF containercomponenten, kunt u complexe segmenten in AEM construeren. Hierbij is het nuttig om u bewust te maken van een aantal basispunten:

* Het hoogste niveau van de definitie is altijd de EN container die aanvankelijk wordt gecreeerd. Dit kan niet worden veranderd, maar heeft geen effect op de rest van uw segmentdefinitie.
* Zorg ervoor dat het nesten van de container zinvol is. De containers kunnen als steunen van uw booleaanse uitdrukking worden bekeken.

Het volgende voorbeeld wordt gebruikt om bezoekers te selecteren die in onze primaire leeftijdsgroep worden overwogen:

Mannelijk en tussen 30 en 59 jaar

OF

Vrouwen tussen 30 en 59 jaar

U begint door een OF containercomponent binnen het gebrek EN container te plaatsen. Binnen de container OR, kunt u twee EN containers en binnen allebei toevoegen u het bezit of de verwijzingscomponenten.

![screen_shot_2012-02-02at105145am](assets/screen_shot_2012-02-02at105145ama.png)

### Scriptverwijzingen gebruiken {#using-script-references}

Door de component van de Verwijzing van het Manuscript te gebruiken, kan de evaluatie van een segmentbezit aan een extern manuscript worden afgevaardigd. Zodra het manuscript behoorlijk wordt gevormd, kan het als een andere component van een segmentvoorwaarde worden gebruikt.

#### Een script definiëren naar verwijzing {#defining-a-script-to-reference}

1. Bestand toevoegen aan `contexthub.segment-engine.scripts` clientlib.
1. Voer een functie uit die een waarde terugkeert. Bijvoorbeeld:

   ```
   ContextHub.console.log(ContextHub.Shared.timestamp(), '[loading] contexthub.segment-engine.scripts - script.profile-info.js');
   
   (function() {
       'use strict';
   
       /**
        * Sample script returning profile information. Returns user info if data is available, false otherwise.
        *
        * @returns {Boolean}
        */
       var getProfileInfo = function() {
           /* let the SegmentEngine know when script should be re-run */
           this.dependOn(ContextHub.SegmentEngine.Property('profile/age'));
           this.dependOn(ContextHub.SegmentEngine.Property('profile/givenName'));
   
           /* variables */
           var name = ContextHub.get('profile/givenName');
           var age = ContextHub.get('profile/age');
   
           return name === 'Joe' && age === 123;
       };
   
       /* register function */
       ContextHub.SegmentEngine.ScriptManager.register('getProfileInfo', getProfileInfo);
   
   })();
   ```

1. Script registreren met `ContextHub.SegmentEngine.ScriptManager.register`.

Als het script afhankelijk is van aanvullende eigenschappen, moet het script worden aangeroepen `this.dependOn()`. Als het script bijvoorbeeld afhankelijk is van `profile/age`:

```
this.dependOn(ContextHub.SegmentEngine.Property('profile/age'));
```

#### Naar een script verwijzen {#referencing-a-script}

1. Creeer segment ContextHub.
1. Toevoegen **Scriptreferentie** op de gewenste plaats van het segment.
1. Het dialoogvenster Bewerken van het dialoogvenster **Scriptreferentie** component. Indien [correct geconfigureerd](/help/sites-administering/segmentation.md#defining-a-script-to-reference), moet het script beschikbaar zijn in het dialoogvenster **Scriptnaam** vervolgkeuzelijst.

## Segmenten ordenen {#organizing-segments}

Als u veel segmenten hebt, kunnen deze moeilijk te beheren worden als een platte lijst. In dergelijke gevallen kan het handig zijn om mappen te maken voor het beheer van uw segmenten.

### Een nieuwe map maken {#create-folder}

1. Na [toegang krijgen tot de segmenten](#accessing-segments)klikt u op de knop **Maken** en selecteert u **Map**.

   ![Map toevoegen](assets/contexthub-create-segment.png)

1. Geef een **Titel** en **Naam** voor uw map.
   * De **Titel** moeten beschrijvend zijn.
   * De **Naam** wordt de knooppuntnaam in de repository.
      * Het wordt automatisch gegenereerd op basis van de titel en aangepast op basis van [AEM naamconventies.](/help/sites-developing/naming-conventions.md)
      * Deze kan zo nodig worden aangepast.

   ![Map maken](assets/contexthub-create-folder.png)

1. Klikken **Maken**.

   ![Map bevestigen](assets/contexthub-confirm-folder.png)

1. De map wordt weergegeven in de lijst met segmenten.
   * Hoe u de kolommen sorteert, is van invloed op de plaats in de lijst waar de nieuwe map verschijnt.
   * U kunt op de kolomkoppen klikken om de sortering aan te passen.
     ![De nieuwe map](assets/contexthub-folder.png)

### Bestaande mappen wijzigen {#modify-folders}

1. Na [toegang krijgen tot de segmenten](#accessing-segments), klikt u op de map die u wilt wijzigen om deze te selecteren.

   ![Map selecteren](assets/contexthub-select-folder.png)

1. Klikken **Naam wijzigen** in de werkbalk om de naam van de map te wijzigen.

1. Nieuwe **Maptitel** en klik op **Opslaan**.

   ![Naam map wijzigen](assets/contexthub-rename-folder.png)

>[!NOTE]
>
>Bij het wijzigen van de mapnaam kan alleen de titel worden gewijzigd. De naam kan niet worden gewijzigd.

### Een map verwijderen

1. Na [toegang krijgen tot de segmenten](#accessing-segments), klikt u op de map die u wilt wijzigen om deze te selecteren.

   ![Map selecteren](assets/contexthub-select-folder.png)

1. Klikken **Verwijderen** om de map te verwijderen.

1. Een dialoogvenster bevat een lijst met mappen die zijn geselecteerd om te worden verwijderd.

   ![Verwijderen bevestigen](assets/contexthub-confirm-segment-delete.png)

   * Klikken **Verwijderen** ter bevestiging.
   * Klikken **Annuleren** om af te breken.

1. Als een van de geselecteerde mappen submappen of segmenten bevat, moet de verwijdering ervan worden bevestigd.

   ![Verwijderen van kinderen bevestigen](assets/contexthub-confirm-segment-child-delete.png)

   * Klikken **Verwijderen forceren** ter bevestiging.
   * Klikken **Annuleren** om af te breken.

>[!NOTE]
>
>Het is niet mogelijk een segment van de ene map naar de andere te verplaatsen.

## De toepassing van een segment testen {#testing-the-application-of-a-segment}

Zodra het segment is bepaald, kunnen de potentiële resultaten met behulp van worden getest **[ContextHub](/help/sites-authoring/ch-previewing.md).**

1. Een voorvertoning van een pagina weergeven
1. Klik het pictogram ContextHub om de toolbar te openbaren ContextHub
1. Selecteer een persoon die overeenkomt met het segment dat u hebt gemaakt
1. ContextHub zal de toepasselijke segmenten voor de geselecteerde persoon oplossen

Bijvoorbeeld, is onze eenvoudige segmentdefinitie om gebruikers in onze primaire leeftijdsgroep te identificeren een eenvoudige segmentdefinitie gebaseerd op de leeftijd en het geslacht van de gebruiker. Als u een specifieke persoon laadt die overeenkomt met die criteria, wordt getoond of het segment is opgelost:

![screen_shot_2012-02-02at105926am](assets/screen_shot_2012-02-02at105926am.png)

Of indien deze niet is opgelost:

![screen_shot_2012-02-02at110019am](assets/screen_shot_2012-02-02at110019am.png)

>[!NOTE]
>
>Alle kenmerken worden onmiddellijk opgelost, maar de meeste wijzigingen worden alleen toegepast wanneer de pagina opnieuw wordt geladen.

Dergelijke tests kunnen ook worden uitgevoerd op inhoudspagina&#39;s en in combinatie met gerichte inhoud en verwante **Activiteiten** en **Ervaringen**.

Als u opstelling een activiteit en ervaring het gebruiken van het hierboven voorbeeld van het groepssegment van de eerste pagina hebt, kunt u uw segment met de activiteit gemakkelijk testen. Voor meer informatie over het instellen van een activiteit raadpleegt u de verwante [documentatie over het ontwerpen van gerichte inhoud](/help/sites-authoring/content-targeting-touch.md).

1. In de bewerkingsmodus van een pagina waarop u doelinhoud hebt ingesteld, ziet u dat de inhoud als doel is ingesteld via het pijlpictogram op de inhoud.

   ![chlimage_1-313](assets/chlimage_1-313.png)

1. De schakelaar aan voorproefwijze en het gebruiken van de contexthub, schakelaar aan een persoon die niet de segmentatie aanpast die voor de ervaring wordt gevormd.

   ![chlimage_1-314](assets/chlimage_1-314.png)

1. De schakelaar aan een persoon die de segmentatie aanpast die voor de ervaring wordt gevormd en ziet dat de ervaring dienovereenkomstig verandert.

   ![chlimage_1-315](assets/chlimage_1-315.png)

## Uw segment gebruiken {#using-your-segment}

De segmenten worden gebruikt om de daadwerkelijke inhoud te sturen die door specifiek doelpubliek wordt gezien. Zie [Soorten publiek beheren](/help/sites-authoring/managing-audiences.md) voor meer informatie over doelgroepen en segmenten en [Doelinhoud ontwerpen](/help/sites-authoring/content-targeting-touch.md) over het gebruik van soorten publiek en segmenten om inhoud als doel in te stellen.
