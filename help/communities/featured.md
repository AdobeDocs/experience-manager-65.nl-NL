---
title: Functie voor aanbevolen inhoud
seo-title: Featured Content Feature
description: Met de functie Aanbevolen inhoud kunnen aangemelde sitebezoekers inhoud markeren
seo-description: The Featured Content feature lets signed-in site visitors highlight content
uuid: 7a2ff570-01bb-46fb-8d66-3b47e2efa72e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ee39435d-80f5-4758-ae01-1ea0d221b00b
exl-id: 76b76e0e-531b-4f80-be70-68532ef81a7f
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '326'
ht-degree: 1%

---

# Functie voor aanbevolen inhoud {#featured-content-feature}

## Inleiding {#introduction}

De functie voor aanbevolen inhoud biedt een gebied voor ingetekende sitebezoekers (leden van de community) in de publicatieomgeving waarin inhoud wordt gemarkeerd voor:

* [Blogs](blog-feature.md)
* [Kalenders](calendar.md)
* [Forums](forum.md)
* [Ideas](ideation-feature.md)
* [QnA](working-with-qna.md)

Als inhoud eenmaal is gemarkeerd als aanbevolen, wordt deze weergegeven in dit onderdeel, dat kan worden geplaatst op specifieke aanlandingspagina&#39;s of gebieden die gemakkelijk de aandacht van de leden van de gemeenschap trekken.

De mogelijkheid om inhoud te voorzien van functies is per component mogelijk toegestaan of niet toegestaan.

In dit gedeelte van de documentatie wordt het volgende beschreven:

* Aanbevolen inhoud toevoegen aan een communitysite.
* De montages van de configuratie voor de `Featured Content` component.

## Aanbevolen inhoud toevoegen aan een pagina {#adding-featured-content-to-a-page}

Als u een `Featured Content` van een component aan een pagina op auteurswijze, gebruik componentenbrowser om van

* `Communities / Featured Content`

en sleep de inhoud naar de juiste plaats op een pagina waar de aanbevolen inhoud moet worden weergegeven.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](basics.md).

Wanneer de [vereiste clientbibliotheken](essentials-featured.md#essentials-for-client-side) worden opgenomen, is dit hoe `Featured Content` wordt weergegeven:

![featuretisch](assets/featuredcontent.png)

## Aanbevolen inhoud configureren {#configuring-featured-content}

Selecteer de geplaatste `Featured Content` te openen en de component te selecteren `Configure` wordt het dialoogvenster Bewerken geopend.

![configure-new](assets/configure-new.png)

![featuredcontent1](assets/featuredcontent1.png)

### Het tabblad Instellingen {#settings-tab}

Onder de **[!UICONTROL Settings]** , geeft u aan welke inhoud u wilt gebruiken:

* **[!UICONTROL Display Name]**

   De titel voor de lijst met aanbevolen inhoud. Bijvoorbeeld `Featured Questions` of `Featured Ideas`. Standaard is `Featured Content` indien leeg gelaten.

* **[!UICONTROL Location of the Featured Content]**

   *(Vereist)* Blader naar de pagina die de inhoud bevat die mogelijk aanwezig is (componenten van die pagina moeten zo zijn geconfigureerd dat aanbevolen inhoud is toegestaan). Bijvoorbeeld, `/content/sites/engage/en/forum`.

* **[!UICONTROL Display Limit]**

   Het maximumaantal aanbevolen inhoud dat kan worden weergegeven. De standaardwaarde is 5.

## Ervaring met sitebezoekers {#site-visitor-experience}

De capaciteit om inhoud als kenmerkende inhoud te markeren vereist moderatorvoorrechten.

Wanneer een moderator geposte inhoud bekijkt, hebben zij toegang tot de vlaggen van de in-context moderatie, die nieuwe omvat `Feature` markering.

![site-bezoeker](assets/site-visitor-experience.png)

Als de markering voor beweging eenmaal is gemarkeerd, wordt de markering voor beweging ingesteld op `Unfeature`.

De pagina met de `Featured Content` bevat nu dit bericht.

![site-visitor-experience1](assets/site-visitor-experience1.png)

`Read More` Dit is een link naar de feitelijke post.

## Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Aanbevolen inhoud](essentials-featured.md) pagina voor ontwikkelaars.

Voor het markeren van inhoud zoals aanbevolen raadpleegt u [Door gebruiker gegenereerde inhoud modereren](moderate-ugc.md).
