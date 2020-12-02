---
title: Lanceringen maken
seo-title: Lanceringen maken
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
workflow-type: tm+mt
source-wordcount: '1008'
ht-degree: 14%

---


# Lanceringen maken{#creating-launches}

Maak een lancering om het bijwerken van een nieuwe versie van bestaande Web-pagina&#39;s voor toekomstige activering toe te laten. Wanneer u een Starten creeert, specificeert u een titel en de bronpagina:

* De titel wordt weergegeven in de [References](/help/sites-authoring/author-environment-tools.md#references) rail, vanwaar auteurs ze kunnen openen om er aan te werken.
* De onderliggende pagina&#39;s van de bronpagina worden standaard in de opstart opgenomen. U kunt desgewenst alleen de bronpagina gebruiken.
* Standaard worden de startpagina&#39;s automatisch bijgewerkt met [Live kopie](/help/sites-administering/msm.md) als de bronpagina&#39;s veranderen. U kunt opgeven dat er een statische kopie wordt gemaakt om automatische wijzigingen te voorkomen.

U kunt desgewenst de **Startdatum** (en -tijd) opgeven om te bepalen wanneer de startpagina&#39;s moeten worden gepromoveerd en geactiveerd. De **startdatum** werkt echter alleen in combinatie met de markering **Geschikt voor productie** (zie [Een startconfiguratie bewerken](/help/sites-authoring/launches-editing.md#editing-a-launch-configuration)). Opdat de acties automatisch zouden optreden, moeten beide worden ingesteld.

## Starten {#creating-a-launch} maken

U kunt een lancering van of Sites of de console van Lanceringen tot stand brengen:

1. Open de **Sites** of **Launches** console.

   >[!NOTE]
   >
   >Wanneer u de console **Sites** gebruikt, is het gebruikelijk om naar de locatie van de bronpagina te navigeren, maar dit is niet verplicht, aangezien u kunt navigeren wanneer u **Bron starten** in de wizard selecteert.

1. Afhankelijk van de console die u gebruikt:

   * **Lanceringen**:

      1. Selecteer **Start maken** op de werkbalk om de wizard te openen.
   * **Sites**:

      1. Selecteer **Maken** op de werkbalk om het selectievak te openen.
      1. Selecteer **Launch** maken om de wizard te openen.

   >[!NOTE]
   >
   >In de **Sites**-console kunt u ook de [selectiemodus](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) gebruiken om een pagina te selecteren voordat u **Maken** selecteert.
   >
   >Hiermee gebruikt u de geselecteerde pagina als de eerste bronpagina.

1. In **Selecteer Bron** stap moet u **Pagina&#39;s toevoegen**. U kunt meerdere pagina&#39;s selecteren en het pad voor elke pagina opgeven:

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

   Ga verder met **Next**.

   ![chlimage_1-226](assets/chlimage_1-226.png)

1. In de stap **Eigenschappen** van de tovenaar kunt u specificeren:

   * **Titel** starten: De naam van de Launch. De naam moet zinvol zijn voor auteurs.
   * **met bestaande inhoud**: de oorspronkelijke inhoud wordt gebruikt om de opstart te maken.
   * **Gebruik een nieuwe sjabloon om de pagina** te vervangen: Zie Starten  [maken met nieuwe ](#create-launch-with-new-template) sjabloon voor meer informatie.
   * **Live-gegevens** van bronpagina overnemen: Selecteer deze optie als u de inhoud van startpagina&#39;s automatisch wilt bijwerken wanneer de bronpagina&#39;s veranderen. Met deze optie bereikt u dit door de opstart te maken tot een [live kopie](/help/sites-administering/msm.md).

      Deze optie is standaard geselecteerd.

   * **Startdatum**: de datum en het tijdstip waarop de lanceerkopie moet worden geactiveerd (afhankelijk van de  **productievlag** Readyflag; zie  [Launches - de Orde van Gebeurtenissen](/help/sites-authoring/launches.md#launches-the-order-of-events)).

   ![chlimage_1-227](assets/chlimage_1-227.png)

1. Gebruik **Maken** om het proces te voltooien en uw nieuwe start te maken. In het bevestigingsvenster wordt u gevraagd of u het programma direct wilt starten.

   Als u de console terugkeert (met **Done**) kunt u uw lancering zien (en toegang hebben) van of:

   * de [**Launches** console](/help/sites-authoring/launches.md#the-launches-console)
   * de [**References** in de **Sites** console](/help/sites-authoring/launches.md#launches-in-references-sites-console)

### Starten maken met nieuwe sjabloon {#create-launch-with-new-template}

Wanneer u een opstart maakt[kunt u kiezen of u een nieuwe sjabloon wilt gebruiken:](/help/sites-authoring/launches-creating.md#create-launch-with-new-template)

**een nieuwe sjabloon gebruiken om de pagina te vervangen**

>[!CAUTION]
>
>Deze optie is alleen beschikbaar wanneer u een opstart maakt via de console **Sites**. Het is niet beschikbaar wanneer het creëren van een lancering van de **console van Lanceringen**.

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
>Zie ook [Een geneste start promoten](/help/sites-authoring/launches-promoting.md#promoting-a-nested-launch).

#### Een geneste start maken - Opstartconsole {#creating-a-nested-launch-launches-console}

Het maken van een geneste opstart vanuit de **Launches**-console is in principe hetzelfde als het maken van een andere opstarthandeling, met uitzondering dat u naar de opstartaftakking `/content/launches` moet navigeren:

1. Selecteer **Maken** in de **Launches**-console.
1. Selecteer **Pagina&#39;s toevoegen** en ga naar de startvertakking door `/content/launches` in het filter op te geven. Selecteer de vereiste start en bevestig dit met **Selecteren**:

   ![chlimage_1-230](assets/chlimage_1-230.png)

1. Ga verder met **Volgende** en vul **Eigenschappen** in zoals bij elke andere lancering.

   ![chlimage_1-231](assets/chlimage_1-231.png)

#### Een geneste start maken - Siteconsole {#creating-a-nested-launch-sites-console}

Om een geneste lancering van **Sites** te creëren console - die op een bestaande lancering wordt gebaseerd:

1. Open [Starten vanuit Referenties (Sites-console)](/help/sites-authoring/launches.md#launches-in-references-sites-console) om de beschikbare handelingen weer te geven.
1. Selecteer **Start maken** om de wizard te openen (aangezien de bron al is geselecteerd, wordt de stap **Bron selecteren** overgeslagen).

1. Voer de **Titel starten** en alle andere vereiste gegevens in (zoals bij een normale start).

1. Gebruik **Maken** om het proces te voltooien en uw nieuwe start te maken. In het bevestigingsvenster wordt u gevraagd of u het programma direct wilt starten.

   Als u **Gereed** selecteert, keert u terug naar het spoor met **Referenties** van de **Sites**-console. Als u de juiste pagina selecteert, wordt de nieuwe startpagina weergegeven.

### Starten {#deleting-a-launch} verwijderen

U kunt een lancering van [lanceert console](/help/sites-authoring/launches.md#the-launches-console) schrappen:

* Selecteer de start door op de miniatuur te tikken of te klikken.
* De werkbalk wordt weergegeven. Selecteer Verwijderen.
* Bevestig de handeling.

>[!CAUTION]
>
>Als u een opstart verwijdert, wordt de opstart zelf en alle afstammende geneste opstarties verwijderd.

