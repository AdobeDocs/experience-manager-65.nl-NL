---
title: Starten maken
seo-title: Starten maken
description: U kunt een lancering tot stand brengen om het bijwerken van een nieuwe versie van bestaande Web-pagina's voor toekomstige activering toe te laten.
seo-description: U kunt een lancering tot stand brengen om het bijwerken van een nieuwe versie van bestaande Web-pagina's voor toekomstige activering toe te laten.
uuid: c1a32710-8189-4a2e-bf2f-428ab30d48c8
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
discoiquuid: 4ec6b408-a165-4617-8d90-e89d8a415bb3
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Starten maken{#creating-launches}

Maak een lancering om het bijwerken van een nieuwe versie van bestaande Web-pagina&#39;s voor toekomstige activering toe te laten. Wanneer u een Starten creeert, specificeert u een titel en de bronpagina:

* De titel wordt weergegeven in de [References](/help/sites-authoring/author-environment-tools.md#references) rail, vanwaar auteurs toegang hebben om er aan te werken.
* De onderliggende pagina&#39;s van de bronpagina worden standaard in de opstart opgenomen. U kunt desgewenst alleen de bronpagina gebruiken.
* Standaard worden de startpagina&#39;s automatisch bijgewerkt door [Live Copy](/help/sites-administering/msm.md) . U kunt opgeven dat er een statische kopie wordt gemaakt om automatische wijzigingen te voorkomen.

U kunt desgewenst de datum **(en de tijd) van** start opgeven om te bepalen wanneer de startpagina&#39;s moeten worden bevorderd en geactiveerd. Nochtans werkt de Datum **van de** Lancering slechts in combinatie met de Klaar **vlag van de** Productie (zie het [Uitgeven van een Configuratie](/help/sites-authoring/launches-editing.md#editing-a-launch-configuration)van de Lancering); voor de acties om automatisch te voorkomen, moeten beide worden geplaatst.

## Starten maken {#creating-a-launch}

U kunt een lancering van of Sites of de console van Lanceringen tot stand brengen:

1. Open de **Sites** - of **Launches** -console.

   >[!NOTE]
   >
   >Wanneer het gebruiken van de console van **Plaatsen** is het gebruikelijk om aan de plaats van de bronpagina te navigeren, maar dit is niet verplicht aangezien u kunt navigeren wanneer het selecteren van de Bron **van de** Lancering in de tovenaar.

1. Afhankelijk van de console die u gebruikt:

   * **Startpagina**:

      1. Selecteer **Starten** maken op de werkbalk om de wizard te openen.
   * **Sites**:

      1. Selecteer **Maken** op de werkbalk om het selectievak te openen.
      1. Selecteer vervolgens Starten **maken** om de wizard te openen.
   >[!NOTE]
   >
   >In de **Sites** -console kunt u ook de [selectiemodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) gebruiken om een pagina te selecteren voordat u **Maken** selecteert.
   >
   >Hiermee gebruikt u de geselecteerde pagina als de eerste bronpagina.

1. In de **Uitgezochte Bron** stap moet u Pagina **&#39;s** toevoegen. U kunt meerdere pagina&#39;s selecteren en het pad voor elke pagina opgeven:

   * Navigeer naar de gewenste locatie.
   * Selecteer de bronpagina(&#39;s) en bevestig (vinkje).
   Herhaal deze bewerking zo nodig.

   ![chlimage_1-225](assets/chlimage_1-225.png)

   >[!NOTE]
   >
   >Als u pagina&#39;s en/of vertakkingen wilt toevoegen aan een lancering, moeten deze zich binnen een site bevinden. d.w.z. onder een gemeenschappelijke hoofdmap.
   >
   >Als een site taalwortels onder het bovenste niveau bevat, moeten de pagina&#39;s en vertakkingen voor een introductie zich onder een gemeenschappelijke hoofdtaalbasis bevinden.

1. Voor elk item kunt u opgeven of:

   * **Inclusief subpagina**&#39;s:

      * Geef op of u de opstart wilt maken met of zonder de onderliggende pagina&#39;s.  Deze subpagina&#39;s worden standaard opgenomen.
   Ga verder met **Volgende**.

   ![chlimage_1-226](assets/chlimage_1-226.png)

1. In de stap **Eigenschappen** van de wizard kunt u het volgende opgeven:

   * **Titel** starten: De naam van de Launch. De naam moet zinvol zijn voor auteurs.
   * **met bestaande inhoud**: de oorspronkelijke inhoud wordt gebruikt om de opstart te maken.
   * **Gebruik een nieuwe sjabloon om de pagina** te vervangen: Zie Starten [maken met nieuwe sjabloon](#create-launch-with-new-template) voor meer informatie.
   * **Live-gegevens** van bronpagina overnemen: Selecteer deze optie als u de inhoud van startpagina&#39;s automatisch wilt bijwerken wanneer de bronpagina&#39;s veranderen. Met deze optie kunt u dit bereiken door een [live kopie](/help/sites-administering/msm.md)te maken.

      Deze optie is standaard geselecteerd.

   * **Startdatum**: de datum en het tijdstip waarop de lanceerkopie moet worden geactiveerd (afhankelijk van de markering **Productie gereed** ; zie [Launches - de Orde van Gebeurtenissen](/help/sites-authoring/launches.md#launches-the-order-of-events)).
   ![chlimage_1-227](assets/chlimage_1-227.png)

1. Gebruik **Maken** om het proces te voltooien en een nieuwe start te maken. In het bevestigingsvenster wordt u gevraagd of u het programma direct wilt starten.

   Als u de console terugkeert (met **Gedaan**) kunt u uw lancering zien (en toegang hebben) van of:

   * de [**Launches **-console](/help/sites-authoring/launches.md#the-launches-console)
   * de [**Verwijzingen **in de console van** Plaatsen **](/help/sites-authoring/launches.md#launches-in-references-sites-console)

### Starten met nieuwe sjabloon maken {#create-launch-with-new-template}

Bij het [maken van een startsjabloon](/help/sites-authoring/launches-creating.md#create-launch-with-new-template) kunt u opgeven of u een nieuwe sjabloon wilt gebruiken:

**een nieuwe sjabloon gebruiken om de pagina te vervangen**

>[!CAUTION]
>
>Deze optie is alleen beschikbaar wanneer u een site start via de **Sites** -console. Deze functie is niet beschikbaar wanneer u een opstart maakt via de **opstartconsole** .

![chlimage_1-228](assets/chlimage_1-228.png)

Selecteer deze optie:

* de andere beschikbare opties bijwerken;
* Neem een nieuwe stap op waarin u de vereiste sjabloon kunt selecteren.

![chlimage_1-229](assets/chlimage_1-229.png)

>[!CAUTION]
>
>Aangezien een andere sjabloon wordt gebruikt, is de nieuwe pagina leeg. Vanwege de verschillende paginastructuur wordt er geen inhoud over gekopieerd.
>
>Dit mechanisme kan worden gebruikt om het malplaatje van een [bestaande pagina](/help/sites-authoring/managing-pages.md#creating-a-new-page) te veranderen - hoewel het verlies van inhoud moet worden overwogen.

### Een geneste start maken {#creating-a-nested-launch}

Door een geneste opstart te maken (opstart binnen een opstart) kunt u een opstart maken op basis van een bestaande opstart, zodat ontwerpers kunnen profiteren van de wijzigingen die al zijn aangebracht, in plaats van meerdere keren dezelfde wijzigingen te moeten doorvoeren voor elke opstart.

>[!NOTE]
>
>Zie ook [Geneste opstart](/help/sites-authoring/launches-promoting.md#promoting-a-nested-launch)bevorderen.

#### Een geneste start maken - Opstartconsole {#creating-a-nested-launch-launches-console}

Het maken van een geneste opstart vanuit de **Launches** -console is in principe hetzelfde als het maken van een andere opstartafbeelding, met uitzondering dat u naar de opstartaftakking moet navigeren `/content/launches`:

1. Selecteer in de **Launches** -console **Maken**.
1. Selecteer Pagina&#39;s **** toevoegen en navigeer naar de startvertakking door `/content/launches` in het filter op te geven. Selecteer de vereiste start en bevestig met **Selecteren**:

   ![chlimage_1-230](assets/chlimage_1-230.png)

1. Ga door met **Volgende** en voltooi de **eigenschappen** zoals bij elke andere lancering.

   ![chlimage_1-231](assets/chlimage_1-231.png)

#### Een geneste start maken - Sites-console {#creating-a-nested-launch-sites-console}

Een geneste start maken via de **Sites** -console op basis van een bestaande introductie:

1. Heb toegang tot de [Lancering van Verwijzingen (de console van Plaatsen)](/help/sites-authoring/launches.md#launches-in-references-sites-console) om de beschikbare acties te tonen.
1. Selecteer Starten **** maken om de wizard te openen (aangezien de bron al is geselecteerd, slaat deze de stap Bron **** selecteren over).

1. Voer de **opstarthandleiding** en alle andere vereiste gegevens in (zoals bij een normale opstart).

1. Gebruik **Maken** om het proces te voltooien en een nieuwe start te maken. In het bevestigingsvenster wordt u gevraagd of u het programma direct wilt starten.

   Als u **Gereed** selecteert, wordt u teruggestuurd naar de **References** -rail van de **Sites** -console. Als u de juiste pagina selecteert, wordt de nieuwe startpagina weergegeven.

### Een Starten verwijderen {#deleting-a-launch}

U kunt een lancering van de [lanceringsconsole](/help/sites-authoring/launches.md#the-launches-console)schrappen:

* Selecteer de start door op de miniatuur te tikken of te klikken.
* De werkbalk wordt weergegeven. Selecteer Verwijderen.
* Bevestig de handeling.

>[!CAUTION]
>
>Als u een opstart verwijdert, wordt de opstart zelf en alle afstammende geneste opstarties verwijderd.

