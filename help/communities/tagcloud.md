---
title: Sociale tagcloud gebruiken
seo-title: Sociale tagcloud gebruiken
description: Een component van de sociale tag Cloud toevoegen aan een pagina
seo-description: Een component van de sociale tag Cloud toevoegen aan een pagina
uuid: 8c400030-976c-457a-bb5f-e473909647a9
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: authoring
content-type: reference
discoiquuid: 23a5a65e-774d-4789-9659-09e8be0c2bcd
translation-type: tm+mt
source-git-commit: 2fcd87cd1def7fc265ba40c83b50db86618f3b70
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---


# Sociale tagcloud {#using-social-tag-cloud} gebruiken

## Inleiding {#introduction}

De component `Social Tag Cloud` markeert tags die door leden van de gemeenschap zijn toegepast bij het plaatsen van inhoud. Dit is een manier om trending onderwerpen te identificeren en bezoekers van de site in staat te stellen snel gelabelde inhoud te zoeken.

Voor een andere manier om huidige tendensen te identificeren, bezoek [Activiteitstrends](trends.md).

Deze pagina documenteert de `Social Tag Cloud` montages van de componentendialoog en beschrijft de gebruikerservaring.

Zie [Tagelementen](tag.md) voor gedetailleerde informatie voor ontwikkelaars.

Zie [Tags beheren](../../help/sites-administering/tags.md) voor informatie over het maken en beheren van tags en over de inhoudstags die zijn toegepast.

## Een sociale-tagcloud toevoegen {#adding-a-social-tag-cloud}

Als u een `Social Tag Cloud`-component in de ontwerpmodus aan een pagina wilt toevoegen, gebruikt u de componentbrowser om `Communities / Social Tag Cloud` te zoeken en deze naar de juiste plaats op een pagina te slepen waar de tagcloud moet worden weergegeven.

Voor noodzakelijke informatie, bezoek [de Grondbeginselen van Componenten van Gemeenschappen](basics.md).

Wanneer de [vereiste client-side bibliotheken](tag.md#essentials-for-client-side) worden opgenomen, wordt de `Social Tag Cloud`-component op deze manier weergegeven:

![social-tag](assets/social-tag.png)

## Cloud voor sociale tag configureren {#configuring-social-tag-cloud}

Selecteer de geplaatste `Social Tag Cloud` component en selecteer `Configure` pictogram dat het Edit dialoog opent.

![vormen](assets/configure-new.png)

Geef onder het tabblad **[!UICONTROL Social Tag Cloud]** op welke tags u wilt weergeven en geef, als de tags actieve koppelingen zijn, de locatie van de pagina op voor de zoekresultaten:

![social-tag-cloud](assets/social-tag-cloud.png)

* **[!UICONTROL Social Tags to Display]**
Bepaal welke UGC-tags moeten worden weergegeven. De pull-down opties zijn:

   * `From page and child pages`
   * `All tags`

   De standaardinstelling is `From page and child pages`, waarbij &quot;pagina&quot; verwijst naar de instelling **Pagina** hieronder.

* **[!UICONTROL Page]**

   (Vereist als niet `All tags)` De weg aan UGC voor een pagina. Standaard is de huidige pagina als deze leeg blijft.

* **[!UICONTROL No links on tags]**

   Als deze optie is ingeschakeld, worden de labels in de labelcloud weergegeven als onbewerkte tekst. Als deze optie is uitgeschakeld, worden de tags weergegeven als actieve koppelingen die zoeken op alle inhoud waarop de tag wordt toegepast. De standaardinstelling is uitgeschakeld en moet **[!UICONTROL Search Result Path]** worden ingesteld.

* **[!UICONTROL Search Result Path]**

   Het pad naar een pagina waarop een `Search Result`-component is geplaatst, geconfigureerd om te verwijzen naar UGC, dat het UGC-pad bevat dat is opgegeven door de instelling **Pagina**.

## Weergave van sociale-tagcloud wijzigen {#change-display-of-social-tag-cloud}

Als u de weergave van de **Sociale tagcloud** wilt bewerken, voert u [Ontwerpmodus](../../help/sites-authoring/default-components-designmode.md) in en dubbelklikt u op de geplaatste `Social Tag Cloud`-component om een dialoogvenster met een extra tabblad te openen.

Geef met het tabblad **[!UICONTROL Social Tag Cloud (Design)]** op hoe tags moeten worden weergegeven. Een tag kan een eenvoudige tag zijn, een enkel woord in de standaardnaamruimte of een hiërarchische taxonomie:

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

   `Geometrixx Media (the namespace)`,  `Gadgets`en  `Cars`

   * Ingeschakeld: Alleen `Cars` wordt weergegeven, indien toegepast.
   * Niet ingeschakeld: `Geometrixx Media` en `Gadgets`en `Cars` worden weergegeven, indien toegepast.

   Een eenvoudige tag is een bladtag.

   De optie Standaard is uitgeschakeld.

* **[!UICONTROL Link Template]**

   Een andere sjabloon dan een standaard die wordt gebruikt om de koppelingen in een tagcloud weer te geven wanneer koppelingen zijn ingeschakeld via het dialoogvenster voor bewerken van componenten.

* **[!UICONTROL Same size for all tags]**

   Als deze optie is ingeschakeld, worden alle woorden in de tagcloud dezelfde stijl toegewezen. Als deze optie is uitgeschakeld, worden woorden anders opgemaakt op basis van hun gebruik. De optie Standaard is uitgeschakeld.

## Aanvullende informatie {#additional-information}

Meer informatie vindt u op de pagina [Tagelementen](tag.md) voor ontwikkelaars.

Zie [Door gebruiker gegenereerde inhoud coderen](tag-ugc.md) (UGC) voor informatie over het maken en beheren van tags.
