---
title: Community Components Guide
seo-title: Community Components Guide
description: Een interactief ontwikkelingsinstrument om aan de slag te gaan met het raamwerk voor sociale componenten (SCF)
seo-description: An interactive development tool to get started with the social component framework (SCF)
uuid: 120e56d1-b93c-4f92-bab4-6bb5e40e0ddf
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
discoiquuid: a777a3f1-b39f-4d90-b9b6-02d3e321a86f
exl-id: 12c0eae5-fd76-4480-a012-25d3312f3570
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '1184'
ht-degree: 0%

---

# Community Components Guide  {#community-components-guide}

De Community Components Guide is een interactief ontwikkelingsinstrument voor de [Sociaal-componentkader (SCF)](scf.md). Het biedt een lijst met beschikbare AEM Communities-componenten of de complexere functies van meerdere componenten.

Samen met basisinformatie voor elke component, staat de gids voor het experimenteren met toe hoe de componenten SCF/de eigenschappen werken en hoe zij kunnen worden gevormd of worden aangepast.

Voor informatie over de essentiële ontwikkelingsaspecten van elke component, zie [Essentiële functies en componenten](essentials.md).

## Aan de slag {#getting-started}

De handleiding is bedoeld voor gebruik in ontwikkelinstallaties van de auteur (localhost:4502) en publiceer instanties (localhost:4503).

De site Community Components is toegankelijk door naar

* [https://&lt;server>:&lt;port>/content/community-components/en.html](http://localhost:4502/content/community-components/en.html)

De wisselwerking met de communautaire componenten is afhankelijk van:

* De server (auteur of publicatie).
* Of de bezoeker van de site al dan niet is aangemeld.
* Indien aangemeld, de aan het lid toegewezen rechten.
* Al dan niet de standaard SRP [JSRP](jsrp.md), is in gebruik.

Als de auteur de bewerkingsmodus wil activeren, voegt u een van de volgende twee in `editor.html` of `cf#` als het eerste padsegment na de servernaam:

* Standaardinterface:

   [https://&lt;server>:&lt;port>/editor.html/content/community-components/en.html](http://localhost:4502/editor.html/content/community-components/en.html)

* Klassieke interface:

   [https://&lt;server>:&lt;port>/cf#/content/community-components/en.html](http://localhost:4502/cf#/content/community-components/en.html)

>[!NOTE]
>
>Op auteur in Edit wijze, zijn de verbindingen op een pagina niet actief.
>
>Als u naar een componentpagina wilt navigeren, selecteert u eerst de modus Voorbeeld om de koppelingen te activeren.
>
>Wanneer de componentpagina in de browser wordt weergegeven, gaat u terug naar de modus Bewerken om het dialoogvenster voor bewerken van de component te openen.
>
>Voor algemene ontwerpinformatie bekijkt u de [snelle handleiding voor het ontwerpen van pagina&#39;s](../../help/sites-authoring/qg-page-authoring.md).
>
>Als u niet bekend bent met AEM, kunt u de documentatie raadplegen op [basisbehandeling](../../help/sites-authoring/basic-handling.md).

### Startpagina {#home-page}

De handleiding bevat een lijst met SCF-componenten die beschikbaar zijn voor voorvertoning en prototypen aan de linkerkant van de pagina.

De Gids van Componenten zoals bekeken op een auteursinstantie op Edit wijze:

![community-component1](assets/community-component1.png)

## Componentpagina&#39;s {#component-pages}

Selecteer een component in de lijst links op de pagina.

![community-component-pagina&#39;s](assets/community-component2.png)

De hoofdtekst van de hulplijn wordt weergegeven:

1. Titel: De naam van de geselecteerde component
1. [Clientbibliotheken](#client-side-libraries): Een lijst van een of meer verplichte categorieën
1. [Inclusief](scf.md#add-or-include-a-communities-component): Als de component dynamisch kan worden opgenomen, kunt u in de bewerkingsmodus van de auteur schakelen tussen de statussen:

   * Indien toegevoegd, wordt weergegeven tekst: &quot;Deze component is opgenomen via het pari-knooppunt.&quot;
   * Indien inbegrepen, wordt weergegeven tekst: &quot;Deze component wordt dynamisch opgenomen.&quot;
   * Indien niet inbegrepen, dan wordt geen tekst getoond

1. Voorbeeldcomponent of -functie: een actieve instantie van de component of eigenschap. Als een component, kan het met veranderingen worden veranderd die in de malplaatjes, CSS en gegevens worden aangebracht die in de lusjesectie worden verstrekt.

>[!NOTE]
>
>Nadat u links een selectie hebt gemaakt, wordt de component hieronder weergegeven in plaats van naast de componenten wanneer het browservenster te smal is.

### Interacties tussen auteurs {#author-interactions}

Wanneer u de handleiding gebruikt voor een instantie van de auteur, kunt u het configureren van een component ervaren door het dialoogvenster te openen. Informatie voor ontwikkelaars is te vinden in het [Grondbeginselen van componenten en functies](essentials.md) in de documentatie, terwijl de dialoogvensterinstellingen worden beschreven in [Community-componenten](author-communities.md) voor auteurs.

Voor de Community Components-handleiding worden bepaalde dialoogvensterinstellingen van componenten overschreven door de [Inclusief](scf.md#add-or-include-a-communities-component) schakelstatus. Als u wilt schakelen tussen het gebruik van de bestaande bron of een dynamisch opgenomen bron, selecteert u in de bewerkingsmodus zowel de component als de insluitende tekst en dubbelklikt u om het dialoogvenster Bewerken te openen:

![community-component3](assets/community-component3.png)

Onder de **Sjablonen** tab:

![community-component4](assets/community-component4.png)

* **Inclusief de onderliggende component met sling:include**

   Als deze optie niet is ingeschakeld, gebruikt de Component Guide de bestaande bron in de repository (een jcr-knooppunt dat een onderliggend knooppunt is van een par-knooppunt).

   * weergegeven tekst is: &quot;Deze component is opgenomen via het pari-knooppunt.&quot;

   Indien gecontroleerd, zal de Gids van de Component sling gebruiken om dynamisch een component van het resourceType van de kindknoop (niet-bestaande middel) te omvatten.

   * weergegeven tekst is: &quot;Deze component wordt dynamisch opgenomen.&quot;

   De optie Standaard is uitgeschakeld.

### Interacties publiceren {#publish-interactions}

Wanneer u de handleiding gebruikt op een publicatie-instantie, kunt u de componenten en functies ervaren als bezoeker van de site (niet aangemeld) en als leden met verschillende bevoegdheden wanneer u zich hebt aangemeld.

>[!NOTE]
>
>Houd rekening met het volgende als de SRP in gebreke blijft [JSRP](jsrp.md), dan is UGC die op de publicatieinstantie is ingevoerd, alleen zichtbaar bij publicatie en wordt *niet* zijn zichtbaar vanaf de [matiging](moderate-ugc.md) console op de auteurinstantie.

## Client-Side bibliotheken {#client-side-libraries}

De client-side bibliotheken (clientlibs) die voor elke component worden vermeld, zijn de *vereist* waarnaar moet worden verwezen wanneer de component op een pagina wordt geplaatst. De clientlibs bieden een manier om het downloaden van Javascript en CSS die worden gebruikt om de component in de browser te renderen, te beheren en te optimaliseren.

Ga voor meer informatie naar [Clientlibs voor Community-componenten](clientlibs.md).

## Imitatie {#impersonation}

Voor de auteurinstantie, waar men vaak als beheerder of ontwikkelaar wordt aangemeld, om de component te ervaren die als een andere gebruiker wordt aangemeld, gebruik het tekstvakje links van **[!UICONTROL Impersonate]** om in de gebruikersnaam te typen of om een keuze te maken in de keuzelijst en vervolgens op de knop te klikken. Klik op Vorige versie om af te melden en de imitatie te beëindigen.

De publicatie-instantie hoeft zich niet voor te doen. U gebruikt gewoon de koppeling Aanmelden/Afmelden om verschillende gebruikers na te bootsen, zoals de [demo-gebruikers](tutorials.md#demo-users).

## Aanpassing {#customization}

Wanneer toegelaten, is elke component SCF beschikbaar voor prototyping van mogelijke aanpassingen door het malplaatje van de component, CSS en gegevens tijdelijk te wijzigen.

### Aanpassing inschakelen {#enabling-customization}

>[!NOTE]
>
>**Dit gereedschap is alleen-lezen**. Geen van de bewerkingen aan sjablonen, CSS of gegevens worden opgeslagen in de gegevensopslagruimte.

Als u snel wilt experimenteren met aanpassingen, `scg:showIde`eigenschap moet worden toegevoegd aan het JCR-knooppunt voor inhoud van de componentpagina en op true worden ingesteld.

De component comments als voorbeeld gebruiken voor de auteur of de publicatie-instantie, aangemeld met beheerdersrechten:

1. Bladeren naar [CRXDE Lite](../../help/sites-developing/developing-with-crxde-lite.md)

   Bijvoorbeeld: [http://localhost:4503/crx/de](http://localhost:4503/crx/de)

1. Selecteer de componenten `jcr:content` node

   Bijvoorbeeld, `/content/community-components/en/comments/jcr:content`

1. Een eigenschap toevoegen

   * **Naam** `scg:showIde`
   * **Type** `String`
   * **Waarde** `true`

1. Selecteer **[!UICONTROL Save All]**
1. Laad de pagina Opmerkingen in de handleiding opnieuw

   [http://localhost:4503/content/community-components/en/comments.html](http://localhost:4503/content/community-components/en/comments.html)

1. Er zijn nu drie tabbladen voor sjablonen, CSS en gegevens.

![community-component5](assets/community-component5.png)

![community-component6](assets/community-component6.png)

### Tabblad Sjablonen {#templates-tab}

Selecteer het tabblad Sjablonen om de sjablonen weer te geven die aan de component zijn gekoppeld.

Met de Sjablooneditor kunnen lokale bewerkingen worden gecompileerd en toegepast op de voorbeeldcomponentinstantie boven aan de pagina zonder dat dit van invloed is op de component in de opslagplaats.

Wanneer compileert op lokale bewerkingen, worden eventuele fouten gemarkeerd door een punt in de tussenruimte te plaatsen en de tekst rood te markeren.

### CSS-tabblad {#css-tab}

Selecteer het tabblad CSS om de CSS weer te geven die aan de component is gekoppeld.

Als een component een samenstelling van veelvoudige componenten is, kan sommige CSS onder één van de andere componenten worden vermeld.

Met de CSS-editor kunt u de CSS wijzigen en toepassen op de voorbeeldcomponentinstantie boven aan de pagina.

U kunt een regel selecteren om de onderdelen van het DOM te markeren met behulp van die regel door naast de regel in de tussenruimte te klikken.

### Tabblad Gegevens {#data-tab}

Selecteer het lusje van Gegevens om de .social.json eindpuntgegevens te tonen. Dit gegeven is editable en wordt toegepast op de instantie van de steekproefcomponent.

Syntaxisfouten kunnen in de tussenruimte worden gemarkeerd en in de editor worden gemarkeerd.
