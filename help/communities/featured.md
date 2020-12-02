---
title: Functie voor aanbevolen inhoud
seo-title: Functie voor aanbevolen inhoud
description: Met de functie Aanbevolen inhoud kunnen aangemelde sitebezoekers inhoud markeren
seo-description: Met de functie Aanbevolen inhoud kunnen aangemelde sitebezoekers inhoud markeren
uuid: 7a2ff570-01bb-46fb-8d66-3b47e2efa72e
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: ee39435d-80f5-4758-ae01-1ea0d221b00b
translation-type: tm+mt
source-git-commit: cbb5a6bac5e9932fd36abf20d4424890080d39bf
workflow-type: tm+mt
source-wordcount: '339'
ht-degree: 0%

---


# Kenmerk aanbevolen inhoud {#featured-content-feature}

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
* De montages van de configuratie voor `Featured Content` component.

## Aanbevolen inhoud toevoegen aan een pagina {#adding-featured-content-to-a-page}

Als u een `Featured Content`-component in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om te zoeken naar

* `Communities / Featured Content`

en sleep de inhoud naar de juiste plaats op een pagina waar de aanbevolen inhoud moet worden weergegeven.

Voor noodzakelijke informatie, bezoek [de Grondbeginselen van Componenten van Gemeenschappen](basics.md).

Wanneer de [vereiste client-side bibliotheken](essentials-featured.md#essentials-for-client-side) worden opgenomen, wordt de `Featured Content`-component op deze manier weergegeven:

![chlimage_1-13](assets/chlimage_1-13.png)

## Aanbevolen inhoud configureren {#configuring-featured-content}

Selecteer de geplaatste `Featured Content` component en selecteer `Configure` pictogram dat het Edit dialoog opent.

![chlimage_1-14](assets/chlimage_1-14.png)

![chlimage_1-15](assets/chlimage_1-15.png)

### Tabblad Instellingen {#settings-tab}

Geef op het tabblad **[!UICONTROL Settings]** aan welke inhoud u wilt gebruiken:

* **[!UICONTROL Display Name]**

   De titel voor de lijst met aanbevolen inhoud. Bijvoorbeeld `Featured Questions` of `Featured Ideas`. De standaardwaarde is `Featured Content` als deze leeg wordt gelaten.

* **[!UICONTROL Location of the Featured Content]**

   *(Vereist)* Blader naar de pagina die de inhoud bevat die mogelijk aanwezig is (onderdelen van die pagina moeten zo zijn geconfigureerd dat aanbevolen inhoud is toegestaan). Bijvoorbeeld, `/content/sites/engage/en/forum`.

* **[!UICONTROL Display Limit]**

   Het maximumaantal aanbevolen inhoud dat kan worden weergegeven. De standaardwaarde is 5.

## Ervaring {#site-visitor-experience} voor bezoekers van site

De capaciteit om inhoud als kenmerkende inhoud te markeren vereist moderatorvoorrechten.

Wanneer een moderator geposte inhoud bekijkt, hebben zij toegang tot de vlaggen van de in-context moderatie, die de nieuwe `Feature` vlag omvat.

![chlimage_1-16](assets/chlimage_1-16.png)

Als de markering eenmaal is gemarkeerd als functie, verandert de markering voor beweging in `Unfeature`.

Deze post wordt nu opgenomen op de pagina die de component `Featured Content` bevat.

![chlimage_1-17](assets/chlimage_1-17.png)

`Read More` Dit is een link naar de feitelijke post.

## Aanvullende informatie {#additional-information}

Meer informatie vindt u op de pagina [Aanbevolen inhoud](essentials-featured.md) voor ontwikkelaars.

Zie [Door gebruiker gegenereerde inhoud modereren](moderate-ugc.md) voor het markeren van inhoud zoals aanbevolen.
