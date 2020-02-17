---
title: Werken met projectworkflows
seo-title: Werken met projectworkflows
description: Een verscheidenheid van projectwerkschema's is beschikbaar uit de doos.
seo-description: Een verscheidenheid van projectwerkschema's is beschikbaar uit de doos.
uuid: 376922ca-e09e-4ac8-88c8-23dac2b49dbe
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: projects
content-type: reference
discoiquuid: 9d2bf30c-5190-4924-82cd-bcdfde24eb39
translation-type: tm+mt
source-git-commit: 0033dfac2540f56b3903c19f6ca19677af050db3

---


# Werken met projectworkflows{#working-with-project-workflows}

De projectworkflows die beschikbaar zijn uit het vak zijn onder andere:

* **Workflow** voor projectgoedkeuring - Met deze workflow kunt u inhoud toewijzen aan een gebruiker, deze controleren en vervolgens goedkeuren.
* **Starten** aanvragen - Een workflow waarvoor u een opstart wilt aanvragen.
* **Openingspagina** aanvragen - Deze workflow vraagt om een bestemmingspagina.
* **E-mail** aanvragen - Workflow voor het aanvragen van een e-mail.
* **Fotofoto&#39;s van producten en foto&#39;s van producten maken (handel)** - hiermee kunt u middelen toewijzen aan producten
* **DAM maakt en vertaalt kopie en DAM maakt taalkopie** - maakt vertaalde binaire bestanden, metagegevens en tags voor elementen en mappen.

Afhankelijk van het projectsjabloon dat u selecteert, zijn bepaalde workflows beschikbaar:

|  | **Eenvoudig project** | **Mediaproject** | **Fotoproject van product** | **Omzettingsproject** |
|---|:-:|:-:|:-:|:-:|
| Verzoek om kopie |  | x |  |  |
| Fotofoto van product |  | x | x |  |
| Fotofoto van product (handel) |  |  | x |  |
| Projectgoedkeuring | x |  |  |  |
| Verzoek starten | x |  |  |  |
| Openingspagina aanvragen | x |  |  |  |
| E-mail aanvragen | x |  |  |  |
| DAM Create Language Copy&amp;ast; |  |  |  | x |
| DAM &amp;Create and Translate Language Copy;ast; |  |  |  | x |

>[!NOTE]
>
> &amp;ast; Deze werkschema&#39;s zijn niet begonnen van de tegel van het **Werkschema** in Projecten. Zie [Taalkopieën voor elementen maken.](/help/sites-administering/tc-manage.md)

De stappen voor het starten en voltooien van workflows zijn hetzelfde, ongeacht de workflow die u kiest. Alleen de stappen worden gewijzigd.

U start een workflow rechtstreeks in Projecten (behalve voor DAM Create Language Copy of DAM Create and Translate Language Copy). De informatie over om het even welke opmerkelijke taken in een project wordt vermeld in de **tegel van Taken** . Meldingen voor taken die moeten worden voltooid, verschijnen naast het gebruikerspictogram.

Raadpleeg de volgende bronnen voor meer informatie over het werken met workflows in AEM:

* [Deelnemen aan workflows](/help/sites-authoring/workflows-participating.md)
* [Workflows toepassen op pagina&#39;s](/help/sites-authoring/workflows-applying.md)
* [Workflows configureren](/help/sites-administering/workflows.md)

Deze sectie beschrijft de werkschema&#39;s beschikbaar voor Projecten.

## Workflow voor kopiëren aanvragen {#request-copy-workflow}

Met deze workflow kunt u een gebruiker om een manuscript vragen en het vervolgens goedkeuren. De workflow voor het kopiëren van aanvragen starten:

1. Selecteer in uw Media-project het **+** -teken in de tegel **Workflows** en selecteer **Request Copy Workflow**.
1. Voer een eigenschapstitel in en een korte samenvatting van wat u vraagt. Voer, indien van toepassing, een doelwoordtelling, taakprioriteit en een vervaldatum in.

   ![chlimage_1-325](assets/chlimage_1-321.png)

1. Klik op **Maken**. De workflow wordt gestart. De taak wordt weergegeven in de tegel **Taken** .

   ![chlimage_1-322](assets/chlimage_1-322.png)

## Workflow voor foto&#39;s van producten {#product-photo-shoot-workflow}

De workflows van de Foto van het Product Foto Shoot (zowel handel als zonder handel) worden in detail behandeld in [Creative Project](/help/sites-authoring/managing-product-information.md).

## Workflow voor projectgoedkeuring {#project-approval-workflow}

In het werkschema van de Goedkeuring van het Project, wijst u inhoud aan een gebruiker toe, herziet, en keurt dan de inhoud goed.

1. In uw Eenvoudig project, selecteer het **`+`** teken in de tegel van **Werkschema** &#39;s en selecteer het Werkschema **van de Goedkeuring van** Project.
1. Ga een titel in en selecteer aan wie om het van de lijst van het Team toe te wijzen. Voer, indien van toepassing, een beschrijving, een inhoudspad, een taakprioriteit en een vervaldatum in.

   ![chlimage_1-323](assets/chlimage_1-323.png)

1. Klik op **Maken**. De workflow wordt gestart. De taak wordt weergegeven in de tegel **Taken** .

   ![chlimage_1-324](assets/chlimage_1-324.png)

## Verzoek indienen om workflow te starten {#request-launch-workflow}

Met deze workflow kunt u een verzoek indienen om de toepassing te starten.

1. Selecteer in uw Eenvoudig project het **+** -teken in de tegel **Workflows** en selecteer **Request Launch Workflow**.
1. Voer een titel in voor de opstart en geef het bronpad voor de opstart op. U kunt ook een beschrijving en live datum toevoegen, indien van toepassing. Selecteer Live-gegevens van bronpagina overnemen of subpagina&#39;s uitsluiten, afhankelijk van de manier waarop u de opstart wilt laten uitvoeren.

   ![chlimage_1-325](assets/chlimage_1-325.png)

1. Klik op **Maken**. De workflow wordt gestart. **De workflow wordt weergegeven in de lijst** Workflows **(klik op Ovaal**.. op de **werkstroomtegel** voor toegang tot deze lijst).

## Workflow voor aanvragen van bestemmingspagina {#request-landing-page-workflow}

Met deze workflow kunt u een bestemmingspagina aanvragen.

1. Selecteer in uw Eenvoudig project het **+** -teken in de tegel **Workflows** en selecteer Request Landing Page Workflow.
1. Voer een titel in voor de openingspagina en het bovenliggende pad. Voer, indien van toepassing, een live datum in of kies een bestand voor de bestemmingspagina.

   ![chlimage_1-326](assets/chlimage_1-326.png)

1. Klik op **Maken**. De workflow wordt gestart. De taak wordt weergegeven in de tegel **Taken** .

## E-mailworkflow aanvragen {#request-email-workflow}

Met deze workflow kunt u een e-mail aanvragen. Het is dezelfde workflow die wordt weergegeven in de tegel **E-mail** .

1. Selecteer in uw Media- of Eenvoudig project het **+** -teken in de tegel **Workflows** en selecteer **Request-e-mailworkflow**.
1. Voer een e-mailtitel in, evenals de campagne- en sjabloonpaden. Daarnaast kunt u een naam, beschrijving en actieve datum opgeven.

   ![chlimage_1-327](assets/chlimage_1-327.png)

1. Klik op **Maken**. De workflow wordt gestart. De taak wordt weergegeven in de tegel **Taken** .

   ![chlimage_1-328](assets/chlimage_1-328.png)

## Workflow voor taalkopieën maken (en vertalen) voor middelen {#create-and-translate-language-copy-workflow-for-assets}

De workflows **Taalkopie** maken en **Taalkopie** maken en vertalen worden uitgebreid besproken in het [maken van taalkopieën voor middelen.](/help/assets/translation-projects.md)
