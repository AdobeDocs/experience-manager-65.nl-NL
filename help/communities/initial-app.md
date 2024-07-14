---
title: Aanvankelijke zandbaktoepassing
description: Leer hoe u de sjabloon Inhoud gebruikt om inhoudspagina's en een component en script te maken waarmee websitepagina's worden weergegeven.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: developing
content-type: reference
exl-id: cbf9ce36-53a2-4f4b-a96f-3b05743f6217
solution: Experience Manager
feature: Communities
role: Developer
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '599'
ht-degree: 0%

---

# Aanvankelijke zandbaktoepassing {#initial-sandbox-application}

In deze sectie maakt u het volgende:

* Het **[malplaatje](#createthepagetemplate)** dat wordt gebruikt om inhoudspagina&#39;s in de voorbeeldwebsite tot stand te brengen.
* De **[component en het manuscript](#create-the-template-s-rendering-component)** dat wordt gebruikt om de websitepagina&#39;s terug te geven.

## De inhoudssjabloon maken {#create-the-content-template}

Een sjabloon definieert de standaardinhoud van een nieuwe pagina. Complexe websites kunnen verschillende sjablonen gebruiken om de verschillende typen pagina&#39;s op de site te maken. Verder, kan de reeks malplaatjes een blauwdruk worden die wordt gebruikt om veranderingen in een cluster van servers uit te voeren.

In deze exercitie, zijn alle pagina&#39;s gebaseerd op één eenvoudig malplaatje.

1. In het deelvenster Verkenner van CRXDE Lite:

   * Selecteren `/apps/an-scf-sandbox/templates`
   * **[!UICONTROL Create]** > **[!UICONTROL Create Template]**

1. Typ de volgende waarden in het dialoogvenster Sjabloon maken en klik op **[!UICONTROL Next]** :

   * Label: `playpage`
   * Titel: `An SCF Sandbox Play Template`
   * Beschrijving: `An SCF Sandbox template for play pages`
   * Type bron: `an-scf-sandbox/components/playpage`
   * Rangschikking: &lt;als standaard verlaten>

   Het label wordt gebruikt voor de knooppuntnaam.

   Het type Resource wordt op het knooppunt `jcr:content` van `playpage` weergegeven als de eigenschap `sling:resourceType` . Het identificeert de component (bron) die de inhoud teruggeeft wanneer daarom door browser wordt gevraagd.

   In dit geval worden alle pagina&#39;s die met de sjabloon `playpage` zijn gemaakt, gerenderd door de component `an-scf-sandbox/components/playpage` . Standaard is het pad naar de component relatief, zodat Sling eerst naar de bron in de map `/apps` en, indien deze niet wordt gevonden, in de map `/libs` kan zoeken.

   ![ creeer-content-malplaatje ](assets/create-content-template-1.png)

1. Als u kopiëren/plakken gebruikt, dient u ervoor te zorgen dat de waarde voor Type bron geen voorloopspaties of navolgende spaties bevat.

   Klik op **[!UICONTROL Next]**.

1. &#39;Toegestane paden&#39; verwijst naar de paden van pagina&#39;s die deze sjabloon gebruiken, zodat de sjabloon wordt weergegeven in het dialoogvenster **[!UICONTROL New Page]** .

   Als u een pad wilt toevoegen, klikt u op de plusknop `+` en typt u `/content(/.&ast;)?` in het tekstvak dat wordt weergegeven. Als u kopieert/plakt, moet u ervoor zorgen dat er geen voorloopspaties of navolgende spaties zijn.

   Nota: De waarde van het toegestane wegbezit is a *regelmatige uitdrukking*. Inhoudspagina&#39;s met een pad dat overeenkomt met de expressie, kunnen de sjabloon gebruiken. In dit geval komt de reguliere expressie overeen met het pad van de map **/content** en alle subpagina&#39;s ervan.

   Wanneer een auteur een pagina onder `/content` maakt, wordt de sjabloon `playpage` &quot;An SCF Sandbox Page Template&quot; weergegeven in een lijst met beschikbare sjablonen die u kunt gebruiken.

   Nadat de basispagina van de sjabloon is gemaakt, kan de toegang tot de sjabloon worden beperkt tot deze website door de eigenschap te bewerken en het hoofdpad op te nemen in de reguliere expressie.

   `/content/an-scf-sandbox(/.&ast;)?`

   ![ vorm-malplaatje-weg ](assets/configure-template-path.png)

1. Klik op **[!UICONTROL Next]**.

   Klik op **[!UICONTROL Next]** in het deelvenster **[!UICONTROL Allowed Parents]** .

   Klik op **[!UICONTROL Next]** in het deelvenster **[!UICONTROL Allowed Children]** .

   Klik op **[!UICONTROL OK]**.

1. Nadat u op OK hebt geklikt en de sjabloon hebt gemaakt, ziet u de rode driehoeken die in de hoeken van de waarden op het tabblad Eigenschappen van de nieuwe `playpage` -sjabloon worden weergegeven. Deze rode driehoeken geven bewerkingen aan die niet zijn opgeslagen.

   Klik op **[!UICONTROL Save All]** om de nieuwe sjabloon op te slaan in de repository.

   ![ verifieer-inhoud-malplaatje ](assets/verify-content-template.png)

### De renderingcomponent van de sjabloon maken {#create-the-template-s-rendering-component}

Creeer de *component* die de inhoud bepaalt en om het even welke gecreeerde pagina&#39;s teruggeeft die op het [ playpage malplaatje ](#createthepagetemplate) worden gebaseerd.

1. Klik met de rechtermuisknop **`/apps/an-scf-sandbox/components`** in CRXDE Lite en klik op **[!UICONTROL Create > Component]** .
1. Door de naam van de knoop (Etiket) aan *playpage* te plaatsen, is de weg aan de component

   `/apps/an-scf-sandbox/components/playpage`

   Dit komt overeen met het Resource Type van de playpage-sjabloon (optioneel minus het oorspronkelijke **`/apps/`** -gedeelte van het pad).

   Typ in het dialoogvenster **[!UICONTROL Create Component]** de volgende eigenschapswaarden:

   * Etiket: **playpage**
   * Titel: **een component van het Spel van SCF Sandbox**
   * Beschrijving: **dit is de component die inhoud voor een SCF Sandbox pagina teruggeeft.**
   * Supertype: *&lt;leave blank>*
   * Groep: *&lt;leave blank>*

   ![ creeer-malplaatje-component ](assets/create-template-component.png)

1. Klik op **[!UICONTROL Next]** totdat het deelvenster **[!UICONTROL Allowed Children]** van het dialoogvenster wordt weergegeven:

   * Klik op **[!UICONTROL OK]**.
   * Klik op **[!UICONTROL Save All]**.

1. Verifieer dat de weg aan de component en resourceType voor het malplaatje aanpast.

   >[!CAUTION]
   >
   >De overeenstemming tussen de weg aan de playpage component en het `sling:resourceType` bezit van het playpage malplaatje is essentieel voor het correcte functioneren van de website.

   ![ verifieer-malplaatje-component ](assets/verify-template-component.png)
