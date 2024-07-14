---
title: Functie voor aanbevolen inhoud
description: Met de functie Aanbevolen inhoud kunnen aangemelde sitebezoekers inhoud markeren
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 76b76e0e-531b-4f80-be70-68532ef81a7f
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '329'
ht-degree: 0%

---

# Functie voor aanbevolen inhoud {#featured-content-feature}

## Inleiding {#introduction}

De functie voor aanbevolen inhoud biedt een gebied voor ingetekende sitebezoekers (leden van de community) in de publicatieomgeving waarin inhoud wordt gemarkeerd voor:

* [Blogs](blog-feature.md)
* [Kalenders](calendar.md)
* [Forums](forum.md)
* [Ideas](ideation-feature.md)
* [QnA](working-with-qna.md)

Als inhoud eenmaal is gemarkeerd als aanbevolen, wordt deze weergegeven in dit onderdeel, dat kan worden geplaatst op specifieke aanlandingspagina&#39;s of gebieden die gemakkelijk de aandacht van de leden van de gemeenschap kunnen trekken.

De mogelijkheid om inhoud te voorzien van functies is per component mogelijk toegestaan of niet toegestaan.

In dit gedeelte van de documentatie wordt het volgende beschreven:

* Aanbevolen inhoud toevoegen aan een communitysite.
* Configuration settings for the `Featured Content` component.

## Aanbevolen inhoud toevoegen aan een pagina {#adding-featured-content-to-a-page}

Als u een component `Featured Content` in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Featured Content`

En sleep het naar de juiste plaats op een pagina waar de aanbevolen inhoud moet worden weergegeven.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen ](basics.md).[

Wanneer de [ vereiste cliënt-zijbibliotheken ](essentials-featured.md#essentials-for-client-side) inbegrepen zijn, is dit hoe de `Featured Content` component verschijnt:

![ eigenschap ](assets/featuredcontent.png)

## Aanbevolen inhoud configureren {#configuring-featured-content}

Selecteer de geplaatste component `Featured Content` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![ vorm-nieuw ](assets/configure-new.png)

![ featuredcontent1 ](assets/featuredcontent1.png)

### Het tabblad Instellingen {#settings-tab}

Geef op het tabblad **[!UICONTROL Settings]** aan welke inhoud u wilt gebruiken:

* **[!UICONTROL Display Name]**

  De titel voor de lijst met aanbevolen inhoud. Bijvoorbeeld `Featured Questions` of `Featured Ideas` . De standaardwaarde is `Featured Content` als deze leeg blijft.

* **[!UICONTROL Location of the Featured Content]**

  *(Vereist)* doorblader aan de pagina die de inhoud bevat die kan worden omvat die (de componenten van die pagina moeten worden gevormd om Aanbevolen Inhoud toe te staan). Bijvoorbeeld `/content/sites/engage/en/forum` .

* **[!UICONTROL Display Limit]**

  Het maximumaantal aanbevolen inhoud dat kan worden weergegeven. De standaardwaarde is 5.

## Ervaring met sitebezoekers {#site-visitor-experience}

De capaciteit om inhoud als kenmerkende inhoud te markeren vereist moderatorvoorrechten.

Wanneer een moderator geposte inhoud bekijkt, hebben zij toegang tot de vlaggen van de in-context moderatie, die de nieuwe `Feature` vlag omvat.

![ plaats-bezoeker-ervaring ](assets/site-visitor-experience.png)

Nadat deze als een functie is gemarkeerd, verandert de moderatiemarkering in `Unfeature` .

De pagina met de component `Featured Content` bevat nu dit bericht.

![ plaats-bezoeker-ervaring1 ](assets/site-visitor-experience1.png)

De `Read More` verwijst naar het daadwerkelijke bericht.

## Aanvullende informatie {#additional-information}

Meer informatie kan op de [ Aanbevolen pagina van de Inhoud ](essentials-featured.md) voor ontwikkelaars worden gevonden.

Voor het vlaggen van inhoud zoals voorzien, zie [ het Matigen van Gebruiker-Gegenereerde Inhoud ](moderate-ugc.md).
