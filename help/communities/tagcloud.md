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

De component `Social Tag Cloud` markeert de tags die door leden van de gemeenschap zijn toegepast bij het plaatsen van inhoud. Dit is een manier om trending onderwerpen te identificeren en bezoekers van de site in staat te stellen snel gelabelde inhoud te zoeken.

Voor een andere manier om huidige tendensen te identificeren, bezoek [&#x200B; Trends van de Activiteit &#x200B;](trends.md).

Op deze pagina worden de dialooginstellingen van de component `Social Tag Cloud` gedocumenteerd en wordt de gebruikerservaring beschreven.

Voor gedetailleerde informatie voor ontwikkelaars, zie {de Hoofdzaak van de Markering 0} [&#128279;](tag.md).

Zie [&#x200B; het Beheer Markeringen &#x200B;](../../help/sites-administering/tags.md) voor informatie over het creëren van en het leiden van markeringen, en waarop inhoudsmarkeringen zijn toegepast.

## Een sociale-tagcloud toevoegen {#adding-a-social-tag-cloud}

Als u een component `Social Tag Cloud` in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om `Communities / Social Tag Cloud` te zoeken en sleept u deze naar de gewenste locatie op een pagina voor de tagcloud.

Voor noodzakelijke informatie, bezoek {de Grondbeginselen van de Componenten van 0} Gemeenschappen [&#128279;](basics.md).

Wanneer de [&#x200B; vereiste cliënt-zijbibliotheken &#x200B;](tag.md#essentials-for-client-side) inbegrepen zijn, is dit hoe de `Social Tag Cloud` component verschijnt:

![&#x200B; sociaal-markering &#x200B;](assets/social-tag.png)

## Cloud voor sociale tags configureren {#configuring-social-tag-cloud}

Selecteer de geplaatste component `Social Tag Cloud` , zodat u het pictogram `Configure` kunt openen en selecteren waarmee het dialoogvenster Bewerken wordt geopend.

![&#x200B; vormen &#x200B;](assets/configure-new.png)

Geef onder het tabblad **[!UICONTROL Social Tag Cloud]** op welke tags u wilt weergeven en, als de tags actieve koppelingen zijn, de locatie van de pagina voor de zoekresultaten:

![&#x200B; sociaal-markering-wolk &#x200B;](assets/social-tag-cloud.png)

* **[!UICONTROL Social Tags to Display]**
Bepaal welke UGC-tags moeten worden weergegeven. De pull-down opties zijn:

   * `From page and child pages`
   * `All tags`

  Het gebrek is `From page and child pages`, waar de &quot;pagina&quot;naar **pagina** het plaatsen hieronder verwijst.

* **[!UICONTROL Page]**

  (Vereist als niet `All tags)` Het pad naar de UGC voor een pagina. Standaard is de huidige pagina als deze leeg blijft.

* **[!UICONTROL No links on tags]**

  Als deze optie is ingeschakeld, worden de labels in de labelcloud weergegeven als onbewerkte tekst. Als deze optie is uitgeschakeld, worden de tags weergegeven als actieve koppelingen die zoeken op alle inhoud waarop de tag wordt toegepast. De optie Standaard is uitgeschakeld en de eigenschap **[!UICONTROL Search Result Path]** moet worden ingesteld.

* **[!UICONTROL Search Result Path]**

  De weg aan een pagina waarop een `Search Result` component is geplaatst, gevormd om UGC van verwijzingen te voorzien die de weg UGC omvat die door **wordt gespecificeerd Pagina** het plaatsen.

## Weergave van sociale-tagcloud wijzigen {#change-display-of-social-tag-cloud}

Om de vertoning van de **Sociale Wolk van de Markering** uit te geven, ga [&#x200B; Wijze van het Ontwerp &#x200B;](../../help/sites-authoring/default-components-designmode.md) in en klik de geplaatste `Social Tag Cloud` component tweemaal om een dialoog met een extra lusje te openen.

Geef met het tabblad **[!UICONTROL Social Tag Cloud (Design)]** op hoe tags moeten worden weergegeven. Een tag kan een eenvoudige tag zijn, een enkel woord in de standaardnaamruimte of een hiërarchische taxonomie:

![&#x200B; sociaal-markering-wolk-ontwerp &#x200B;](assets/social-tag-cloud-design.png)

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

  `Geometrixx Media (the namespace)` , `Gadgets` en `Cars`

   * Ingeschakeld: alleen `Cars` wordt weergegeven, indien toegepast.
   * Niet ingeschakeld: `Geometrixx Media` , `Gadgets` en `Cars` worden weergegeven, indien toegepast.

  Een eenvoudige tag is een bladtag.

  De optie Standaard is uitgeschakeld.

* **[!UICONTROL Link Template]**

  Een andere sjabloon dan een standaard die wordt gebruikt om de koppelingen in een tagcloud weer te geven wanneer koppelingen zijn ingeschakeld via het dialoogvenster voor bewerken van componenten.

* **[!UICONTROL Same size for all tags]**

  Als deze optie is ingeschakeld, worden alle woorden in de tagcloud dezelfde stijl toegewezen. Als deze optie is uitgeschakeld, worden woorden anders opgemaakt op basis van hun gebruik. De optie Standaard is uitgeschakeld.

## Aanvullende informatie {#additional-information}

Meer informatie kan op de [&#x200B; pagina van de Hoofdzaak van de Markering &#x200B;](tag.md) voor ontwikkelaars worden gevonden.

Zie [&#x200B; Tags Gebruiker Gegenereerde Inhoud &#x200B;](tag-ugc.md) (UGC) voor informatie over het creëren van en het beheren van markeringen.
