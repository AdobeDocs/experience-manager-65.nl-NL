---
title: Sociale tagcloud gebruiken
description: Leer hoe u een component van de cloud voor sociale tags toevoegt aan een pagina waarop ingetekende communityleden snel trending topics kunnen identificeren en gecodeerde inhoud kunnen zoeken.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
exl-id: 56af5362-78de-4308-8958-63a45e8573cc
solution: Experience Manager
feature: Communities
role: Admin
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '532'
ht-degree: 0%

---

# Sociale tagcloud gebruiken {#using-social-tag-cloud}

## Inleiding {#introduction}

De `Social Tag Cloud` component markeert tags die door leden van de gemeenschap worden toegepast bij het plaatsen van inhoud. Dit is een manier om trending onderwerpen te identificeren en bezoekers van de site in staat te stellen snel gelabelde inhoud te zoeken.

Voor een andere manier om de huidige trends te identificeren, gaat u naar [Activiteitendensen](trends.md).

Deze pagina documenteert de `Social Tag Cloud` en beschrijft de gebruikerservaring.

Voor gedetailleerde informatie voor ontwikkelaars, zie [Grondbeginselen van tags](tag.md).

Zie [Tags beheren](../../help/sites-administering/tags.md) voor informatie over het maken en beheren van tags en waarop inhoudstags zijn toegepast.

## Een sociale-tagcloud toevoegen {#adding-a-social-tag-cloud}

Als u een `Social Tag Cloud` van een component aan een pagina op auteurswijze, gebruik componentenbrowser om van `Communities / Social Tag Cloud` en sleep het naar de juiste plaats op een pagina waar de tagcloud moet worden weergegeven.

Voor de nodige informatie gaat u naar [Grondbeginselen van Community-componenten](basics.md).

Wanneer de [vereiste clientbibliotheken](tag.md#essentials-for-client-side) worden opgenomen, is dit hoe `Social Tag Cloud` wordt weergegeven:

![social-tag](assets/social-tag.png)

## Cloud voor sociale tags configureren {#configuring-social-tag-cloud}

Selecteer de geplaatste `Social Tag Cloud` zodat u toegang hebt tot `Configure` wordt het dialoogvenster Bewerken geopend.

![vormen](assets/configure-new.png)

Onder de **[!UICONTROL Social Tag Cloud]** , geeft u op welke tags moeten worden weergegeven en, als de tags actieve koppelingen zijn, de locatie van de pagina voor zoekresultaten:

![social-tag-cloud](assets/social-tag-cloud.png)

* **[!UICONTROL Social Tags to Display]**
Bepaal welke UGC-tags moeten worden weergegeven. De pull-down opties zijn:

   * `From page and child pages`
   * `All tags`

  De standaardwaarde is `From page and child pages`, waarbij &quot;pagina&quot; verwijst naar de **Pagina** hieronder instellen.

* **[!UICONTROL Page]**

  (Vereist indien niet `All tags)` Het pad naar de UGC voor een pagina. Standaard is de huidige pagina als deze leeg blijft.

* **[!UICONTROL No links on tags]**

  Als deze optie is ingeschakeld, worden de labels in de labelcloud weergegeven als onbewerkte tekst. Als deze optie is uitgeschakeld, worden de tags weergegeven als actieve koppelingen die zoeken op alle inhoud waarop de tag wordt toegepast. De optie Standaard is uitgeschakeld en vereist de opdracht **[!UICONTROL Search Result Path]** in te stellen.

* **[!UICONTROL Search Result Path]**

  Het pad naar een pagina waarop een `Search Result` -component is geplaatst, geconfigureerd om te verwijzen naar UGC, dat het UGC-pad bevat dat is opgegeven door het **Pagina** instellen.

## Weergave van sociale-tagcloud wijzigen {#change-display-of-social-tag-cloud}

De weergave van het dialoogvenster **Sociale-tagcloud**, enter [Ontwerpmodus](../../help/sites-authoring/default-components-designmode.md) en dubbelklikt u op de geplaatste `Social Tag Cloud` om een dialoogvenster met een extra tabblad te openen.

Met de **[!UICONTROL Social Tag Cloud (Design)]** , geeft u op hoe tags moeten worden weergegeven. Een tag kan een eenvoudige tag zijn, een enkel woord in de standaardnaamruimte of een hiërarchische taxonomie:

![social-tag-cloud-design](assets/social-tag-cloud-design.png)

* **[!UICONTROL Show full title paths]**

  Als deze optie is ingeschakeld, worden de titels voor de bovenliggende tags en naamruimte voor elke toegepaste tag weergegeven.

  Bijvoorbeeld:

   * Ingeschakeld: `Geometrixx Media: Gadgets / Cars`
   * Niet ingeschakeld: `Cars`

  Er is geen verschil voor een eenvoudige tag.

  De optie Standaard is uitgeschakeld.

* **[!UICONTROL Show only leaf tags]**

  Als deze optie is ingeschakeld, worden alleen toegepaste tags weergegeven die geen andere tags bevatten.

  Voorbeeld van de tagID van:

  `Geometrixx Media: Gadgets / Cars`

  Er zijn drie tags die kunnen worden toegepast:

  `Geometrixx Media (the namespace)`, `Gadgets`, en `Cars`

   * Ingeschakeld: alleen `Cars` worden weergegeven, indien van toepassing.
   * Niet ingeschakeld: `Geometrixx Media`, `Gadgets`, en `Cars` worden weergegeven, indien toegepast.

  Een eenvoudige tag is een bladtag.

  De optie Standaard is uitgeschakeld.

* **[!UICONTROL Link Template]**

  Een andere sjabloon dan een standaard die wordt gebruikt om de koppelingen in een tagcloud weer te geven wanneer koppelingen zijn ingeschakeld via het dialoogvenster voor bewerken van componenten.

* **[!UICONTROL Same size for all tags]**

  Als deze optie is ingeschakeld, worden alle woorden in de tagcloud dezelfde stijl toegewezen. Als deze optie is uitgeschakeld, worden woorden anders opgemaakt op basis van hun gebruik. De optie Standaard is uitgeschakeld.

## Aanvullende informatie {#additional-information}

Meer informatie is te vinden op de [Grondbeginselen van tags](tag.md) pagina voor ontwikkelaars.

Zie [Door gebruiker gegenereerde inhoud labelen](tag-ugc.md) (UGC) voor informatie over het maken en beheren van tags.
