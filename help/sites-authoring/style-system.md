---
title: Stijlsysteem
description: Met het Stijlsysteem kan een sjabloonauteur stijlklassen definiëren in het inhoudsbeleid van een component, zodat de auteur van de inhoud deze kan selecteren wanneer hij de component op een pagina bewerkt. Deze stijlen kunnen alternatieve visuele variaties van een component zijn, waardoor het flexibeler wordt.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
exl-id: 1772368a-f5c9-440c-a92a-0f1d34cc4bf8
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '1296'
ht-degree: 1%

---

# Stijlsysteem{#style-system}

Met het Stijlsysteem kan een sjabloonauteur stijlklassen definiëren in het inhoudsbeleid van een component, zodat de auteur van de inhoud deze kan selecteren wanneer hij de component op een pagina bewerkt. Deze stijlen kunnen alternatieve visuele variaties van een component zijn, waardoor de component flexibeler wordt.

Dit elimineert de behoefte om een douanecomponent voor elke stijl te ontwikkelen of het componentendialoogvenster aan te passen om dergelijke stijlfunctionaliteit toe te laten. Het leidt tot herbruikbaardere componenten die snel en gemakkelijk aan de behoeften van inhoudsauteurs zonder enige AEM achterwaartse ontwikkeling kunnen worden aangepast.

## Hoofdletters gebruiken {#use-case}

De auteurs van het malplaatje vergen niet alleen de capaciteit om te vormen hoe de componenten voor de inhoudsauteurs functioneren, maar ook om verscheidene alternatieve visuele variaties van een component te vormen.

Op dezelfde manier hebben inhoudsauteurs niet alleen de mogelijkheid nodig om de inhoud te structureren en te rangschikken, maar ook om te selecteren hoe de inhoud visueel wordt weergegeven.

Het systeem van de Stijl verstrekt een verenigde oplossing aan zowel de vereisten van de malplaatjeauteur als van de inhoudauteur:

* Sjabloonauteurs kunnen stijlklassen definiëren in het inhoudsbeleid van componenten.
* Inhoudsauteurs kunnen deze klassen vervolgens selecteren in een vervolgkeuzelijst wanneer ze de component op een pagina bewerken om de bijbehorende stijlen toe te passen.

De stijlklasse wordt dan opgenomen op het decoratie omslagelement van de component zodat de componentenontwikkelaar zich niet met de behandeling van de stijlen hoeft bezig te houden voorbij het verstrekken van hun CSS regels.

## Overzicht {#overview}

Het gebruik van het Stijlsysteem heeft doorgaans de volgende vorm.

1. De webontwerper maakt verschillende visuele variaties van een component.

1. De HTML-ontwikkelaar krijgt de HTML-uitvoer van de componenten en de gewenste visuele variaties die u wilt implementeren.

1. De HTML-ontwikkelaar definieert de CSS-klassen die overeenkomen met elke visuele variatie en die moeten worden ingevoegd op het element dat de componenten omvat.

1. De HTML-ontwikkelaar implementeert de bijbehorende CSS-code (en eventueel JS-code) voor elk van de visuele variaties, zodat deze er zo uitzien als gedefinieerd.

1. De ontwikkelaar van AEM plaatst verstrekte CSS (en facultatieve JS) in de Bibliotheek van de a [&#x200B; Cliënt &#x200B;](/help/sites-developing/clientlibs.md) en stelt het op.

1. De AEM-ontwikkelaar of sjabloonauteur configureert de paginasjablonen en bewerkt het beleid van elke opgemaakte component, voegt de gedefinieerde CSS-klassen toe, geeft gebruikersvriendelijke namen aan elke stijl en geeft aan welke stijlen kunnen worden gecombineerd.

1. De auteur van de AEM-pagina kan vervolgens de ontworpen stijlen in de pagina-editor kiezen via het stijlmenu van de werkbalk van de component.

Merk op dat slechts de laatste drie stappen daadwerkelijk in AEM worden uitgevoerd. Dit betekent dat alle ontwikkeling van de vereiste CSS en JavaScript kan worden uitgevoerd zonder AEM.

Voor een feitelijke implementatie van de stijlen is alleen implementatie op AEM en selectie binnen de componenten van de gewenste sjablonen vereist.

Het volgende diagram illustreert de architectuur van het Systeem van de Stijl.

![&#x200B; aem-style-system &#x200B;](assets/aem-style-system.png)

## Gebruiken {#use}

Om de eigenschap aan te tonen, zullen wij [&#x200B; WKND &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html) implementatie van de 2&rbrace; titelcomponent van de kerncomponent [&#x200B; als voorbeeld gebruiken.](https://www.adobe.com/go/aem_cmp_title_v2)

De volgende secties [&#x200B; als Inhoudsauteur &#x200B;](#as-a-content-author) en [&#x200B; als Auteur van het Malplaatje &#x200B;](#as-a-template-author) beschrijven hoe te om de functionaliteit van het Systeem van de Stijl te testen gebruikend het Systeem van de Stijl van WKND.

Ga als volgt te werk als u het Stijlsysteem voor uw eigen componenten wilt gebruiken:

1. Installeer CSS als cliëntbibliotheken zoals die in het sectie [&#x200B; Overzicht &#x200B;](#overview) worden besproken.
1. Vorm de CSS klassen die u wenst om aan uw inhoudsauteurs ter beschikking te stellen zoals die in de sectie [&#x200B; als Auteur van het Malplaatje &#x200B;](#as-a-template-author) wordt beschreven.
1. De auteurs van de inhoud kunnen de stijlen dan gebruiken zoals die in de sectie [&#x200B; als Inhoudsauteur &#x200B;](#as-a-content-author) worden beschreven.

### Als inhoudsauteur {#as-a-content-author}

1. Nadat u het WKND-project hebt geïnstalleerd, navigeert u naar de hoofdpagina voor de Engelse taal van WKND op `http://<host>:<port>/sites.html/content/wknd/language-masters/en` en bewerkt u de pagina.
1. Selecteer a **component van de Titel** verder onderaan de pagina

   ![&#x200B; Systeem van de Stijl voor de auteur &#x200B;](assets/style-system-author.png)

1. Klik de **knoop van Stijlen** op de toolbar van de **component van de Lijst** om het stijlmenu te openen en de verschijning van de component te veranderen.

   ![&#x200B; Selecterend stijlen &#x200B;](assets/style-system-author2.png)

   >[!NOTE]
   >
   >In dit voorbeeld, zijn de **Kleuren** stijlen (**Zwart**, **Wit**, en **Grijs**) wederzijds exclusief, terwijl de **Stijl** opties (**onderstreept**, **richt rechts**, en **Mini die** verdelen) kan worden gecombineerd. Dit kan [in de sjabloon worden geconfigureerd als sjabloonauteur](#as-a-template-author).

### Als sjabloonauteur {#as-a-template-author}

1. Terwijl het uitgeven van de Engelse taalmeester van WKND homepage bij `http://<host>:<port>/sites.html/content/wknd/language-masters/en`, geef het malplaatje van de pagina via **de Informatie van de Pagina uit > geeft Malplaatje** uit.

   ![&#x200B; geef Malplaatje &#x200B;](assets/style-system-edit-template.png) uit

1. Bewerk het beleid van de **component van de Titel** door het **Beleid** knoop van de component te tikken of te klikken.

   ![&#x200B; geeft beleid &#x200B;](assets/style-system-edit-policy.png) uit

1. Op het tabblad Stijlen van de eigenschappen kunt u zien hoe de stijlen zijn geconfigureerd.

   ![&#x200B; geeft eigenschappen &#x200B;](assets/style-system-properties.png) uit

   * **de Naam van de Groep:** de Stijlen kunnen samen binnen het stijlmenu worden gegroepeerd dat de inhoudsauteur wanneer het vormen van de stijl van de component zal zien.
   * **de Stijlen kunnen worden gecombineerd:** staat voor veelvoudige stijlen binnen die groep toe om in één keer worden geselecteerd.
   * **Naam van de Stijl:** de beschrijving van de stijl die aan de inhoudauteur wanneer het vormen van de stijl van de component zal tonen.
   * **CSS Klassen:** De daadwerkelijke naam van de CSS klasse verbonden aan de stijl.

   Gebruik de sleephandgrepen om de volgorde van de groepen en de stijlen in de groepen te bepalen. Met de pictogrammen Toevoegen of Verwijderen kunt u groepen of stijlen in de groepen toevoegen of verwijderen.

>[!CAUTION]
>
>De CSS klassen (en om het even welke noodzakelijke JavaScript) die als stijleigenschappen van het beleid van een component worden gevormd moeten als [&#x200B; Bibliotheken van de Cliënt &#x200B;](/help/sites-developing/clientlibs.md) worden opgesteld om te werken.

## Instellen {#setup}

Versie 2 en later van de Componenten van de kern wordt volledig toegelaten om uit het Systeem van de Stijl voordeel te halen en geen extra configuratie te vereisen.

De volgende stappen zijn slechts noodzakelijk om het Systeem van de Stijl voor uw eigen douanecomponenten toe te laten of [&#x200B; toe te laten het facultatieve lusje van Stijlen in de Edit dialoog.](#enable-styles-tab-edit)

### Het tabblad Stijl in het dialoogvenster Ontwerpen inschakelen {#enable-styles-tab-design}

Een component werkt alleen met het AEM-stijlsysteem en geeft het stijltabblad weer in het ontwerpdialoogvenster als de ontwikkelaar het tabblad Stijl met de volgende instellingen in de component heeft opgenomen:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_design/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

Met de gevormde component, zullen de stijlen die door de paginaauteurs worden gevormd automatisch door AEM op het decoratie element worden opgenomen dat AEM automatisch rond elke editable component verpakt. De component zelf hoeft niets anders te doen om dit te bewerkstelligen.

### Het tabblad Stijlen inschakelen in het dialoogvenster Bewerken {#enable-styles-tab-edit}

Vanaf AEM-versie 6.5.3.0 is een optioneel tabblad Stijlen in het dialoogvenster Bewerken nu beschikbaar. In tegenstelling tot het tabblad Ontwerpdialoogvenster is het tabblad in het dialoogvenster Bewerken niet essentieel voor het functioneren van het Stijlsysteem, maar is het een optionele alternatieve interface voor de auteur van inhoud om stijlen in te stellen.

Het tabblad Bewerken kan op vergelijkbare wijze worden opgenomen als het tabblad van het dialoogvenster Ontwerpen:

* `path = "/mnt/overlay/cq/gui/components/authoring/dialog/style/tab_edit/styletab"`
* `sling:resourceType = "granite/ui/components/coral/foundation/include"`

>[!NOTE]
>
>Het tabblad Stijlen in het dialoogvenster Bewerken is niet standaard ingeschakeld.

### Stijlen met elementnamen {#styles-with-element-names}

Een ontwikkelaar kan ook een lijst met toegestane elementnamen voor stijlen op de component configureren met de eigenschap `cq:styleElements` string array. Vervolgens kan de sjabloonauteur op het tabblad Stijlen van het beleid in het ontwerpdialoogvenster ook een elementnaam kiezen die voor elke stijl moet worden ingesteld. Hiermee wordt de elementnaam van het omvattende element ingesteld.

Deze eigenschap wordt ingesteld op het knooppunt `cq:Component` . Bijvoorbeeld:

* `/apps/<yoursite>/components/content/list@cq:styleElements=[div,section,span]`

>[!CAUTION]
>
>Definieer geen elementnamen voor stijlen die kunnen worden gecombineerd. Wanneer de veelvoudige elementnamen worden bepaald, is de orde van prioriteit:
>
>1. HTML heeft voorrang op alles: `data-sly-resource="${'path/to/resource' @ decorationTagName='span'}`
>1. Dan onder veelvoudige actieve stijlen, wordt de eerste stijl in de lijst van stijlen die in het beleid van de component worden gevormd genomen.
>1. Ten slotte wordt de waarde `cq:htmlTag`/ `cq:tagName` van de component beschouwd als een terugvalwaarde.
>

Deze mogelijkheid om stijlnamen te definiëren, is handig voor zeer algemene componenten, zoals de container van de layout of de component Content Fragment, zodat ze een extra betekenis krijgen.

Zo kan een container voor lay-out bijvoorbeeld semantiek als `<main>` , `<aside>` , `<nav>` enzovoort krijgen.
