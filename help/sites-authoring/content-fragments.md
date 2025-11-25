---
title: Inhoud pagina's ontwerpen met inhoudsfragmenten
description: Met AEM Content Fragments kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en gebruiken.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
docset: aem65
exl-id: d5dad844-80ca-4ace-a082-38d892d9ffe2
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Content Fragments
role: User,Admin,Developer
source-git-commit: c77849740fab51377ce60aff5f611e0408dca728
workflow-type: tm+mt
source-wordcount: '1138'
ht-degree: 2%

---

# Pagina&#39;s ontwerpen met inhoudsfragmenten{#page-authoring-with-content-fragments}

Inhoudsfragmenten van Adobe Experience Manager (AEM) worden [gemaakt en beheerd als paginaonafhankelijke assets](/help/assets/content-fragments/content-fragments.md).

U kunt hiermee kanaalneutrale inhoud maken, samen met (mogelijk kanaalspecifieke) variaties. Vervolgens kunt u deze fragmenten en de variaties ervan gebruiken bij het ontwerpen van de inhoudspagina&#39;s.

Samen met de bijgewerkte JSON-exportfunctie kunnen gestructureerde inhoudsfragmenten ook worden gebruikt om AEM-inhoud via Content Services te leveren aan andere kanalen dan AEM-pagina&#39;s.

>[!NOTE]
>
>**de Fragmenten van de Inhoud** en **[Fragmenten van de Ervaring](/help/sites-authoring/experience-fragments.md)** zijn verschillende eigenschappen binnen AEM:
>
>* **de Fragmenten van de Inhoud** zijn redactionele inhoud, hoofdzakelijk tekst, en verwante beelden. Het zijn pure inhoud, zonder ontwerp en lay-out.
>* **de Fragmenten van de Ervaring** zijn volledig opgemaakt inhoud; een fragment van een Web-pagina.
>
>De Fragmenten van de ervaring kunnen inhoud in de vorm van Inhoudsfragmenten bevatten, maar niet andersom.

>[!CAUTION]
>
>Deze pagina moet met [ het Werken met de Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md) (en verwante pagina&#39;s) worden gelezen omdat het basisterminologie en concepten, samen met het creëren en het beheren van fragmenten introduceert.

Met de inhoudsfragmenten kunt u:

* **marketing en Campagne Strategie**

   * Inhoud controleren via centraal beheerde inhoudsfragmenten.

* **Creative Pro**

   * Het bijhouden van creatieve elementen via verzamelingen die zijn gekoppeld aan inhoudsfragmenten.

* **Schrijvers van het Exemplaar**

   * Schrijf in de AEM-inhoudsfragmenteditor.
   * Kan inhoudvariaties maken.
   * Kan relevante inhoud aan het inhoudsfragment koppelen.
   * Kan versioning/workflow gebruiken.
   * Kan inhoudsfragment delen.
   * Kan vertalingen centraal beheren.

* **Producenten en de Managers van de Reis**

   * Maak een keuze uit vooraf gedefinieerde fragmenten en variaties bij het ontwerpen in AEM.
   * Kan erop vertrouwen dat het fragment en de bijbehorende inhoud altijd up-to-date zijn terwijl kopieerschrijvers en -creatieven hun updates in centraal beheerde fragmenten en elementen maken.
   * Kan voor relevantie vertrouwen op gekoppelde media-inhoud die wordt verwerkt.
   * U kunt ad-hocinhoudvariaties maken terwijl u er toch voor zorgt dat deze variaties centraal worden beheerd in het fragment.

## Een inhoudsfragment toevoegen aan uw pagina {#adding-a-content-fragment-to-your-page}

1. Open de pagina om deze te bewerken.

1. Voeg de **component van het Fragment van de Inhoud** toe; van of **Componenten** browser of **Tussenvoegsel Nieuwe Component**.

1. U kunt:

   * Open **browser van Assets** en filter voor **de Fragmenten van de Inhoud** (het gebrek is Beelden). Sleep het gewenste fragment vervolgens naar de componentinstantie.

   * Selecteer de component van het inhoudsfragment, dan **vorm** van de toolbar. In de dialoog, kunt u de doos van de selectiedialoog openen om het vereiste **Fragment van de Inhoud** te doorbladeren en te selecteren.

   >[!NOTE]
   >
   >Een andere methode is om een specifiek inhoudsfragment rechtstreeks naar de pagina te slepen. Hiermee wordt automatisch de bijbehorende component (inhoudsfragment) gemaakt.

1. Aanvankelijk wordt de inhoud van het **Belangrijkste** Element en **Hoofd** (variatie) getoond. U kunt [ andere elementen en/of variaties ](#selecting-the-element-or-variation) zoals vereist selecteren.

   ![ cfm-6420-01 ](assets/cfm-6420-01.png)

   >[!NOTE]
   >
   >Raadpleeg de volgende secties voor meer informatie over de verdere bewerkingsfunctionaliteit:
   >
   >
   >
   >    * [Responsieve lay-out](/help/sites-authoring/responsive-layout.md)
   >    * [Paginacontent bewerken](/help/sites-authoring/editing-content.md)
   >
   >

### Het element of de variatie selecteren {#selecting-the-element-or-variation}

Open de de dialoogdoos van de Configuratie van het fragment **** zodat kunt u het fragment voor gebruik op de huidige pagina vormen. Het dialoogvenster kan afhankelijk zijn van de gebruikte component.

In het aangewezen de dialoogvakje van de Configuratie, kunt u de beschikbare parameters selecteren, die omvatten:

* **het Fragment van de Inhoud**

  Geef op welk fragment moet worden gebruikt.

* **Wijze van de Vertoning**:

   * **Enig Element van de Tekst**

   * **Veelvoudig Element**

* **Element**

   * Het gebrek **Hoofd** is altijd beschikbaar.
   * Er is een selectie beschikbaar als het fragment met een geschikte sjabloon is gemaakt.

  >[!NOTE]
  >
  >De beschikbare elementen zijn afhankelijk van de gebruikte sjabloon.

* **Variatie**

   * Het gebrek **Hoofd** is altijd beschikbaar.
   * Er is een selectie beschikbaar als er variaties zijn gemaakt voor het fragment.

* **Paragraaf**: specificeer de waaier van paragrafen om te omvatten:

   * **allen**
   * **Waaier**: bijvoorbeeld, `1`, `3-5`, `9-*`

      * **handvatrubrieken als hun eigen paragrafen**

* **handvatrubrieken als hun eigen paragrafen**

### Snelle verbinding met de fragmenteditor {#quick-connection-to-fragment-editor}

U kunt de fragmentbron voor het uitgeven (de activa) openen gebruikend **uitgeeft** pictogram op de componententoolbar. Dit laat u [ uitgeven en het inhoudsfragment ](/help/assets/content-fragments/content-fragments.md) beheren.

>[!CAUTION]
>
>Zoals altijd kan het bewerken van de fragmentbron gevolgen hebben voor alle pagina&#39;s die naar dat inhoudsfragment verwijzen.

### Tussenliggende inhoud toevoegen {#adding-in-between-content}

Wanneer een specifiek inhoudsfragment aan de pagina wordt toegevoegd, is er de componenten van de a **Belemmering hier** placeholder tussen elke paragraaf van HTML (en bij de bovenkant/bodem) van het fragment.

Dit laat u extra inhoud [ binnen-tussen (namelijk in-tussen inhoud) ](/help/assets/content-fragments/content-fragments.md#in-between-content-when-page-authoring-with-content-fragments) toevoegen de fragmentinhoud (op om het even welke beschikbare punten), zonder het moeten het wortelfragment veranderen.

Voor tussenliggende inhoud kunt u:

* Voeg componenten van [ browser van Componenten ](/help/sites-authoring/author-environment-tools.md#components-browser) toe.
* Voeg activa van [ browser van Assets ](/help/sites-authoring/author-environment-tools.md#assets-browser) toe.
* Het gebruik [ Verwante Inhoud ](#using-associated-content) als bron voor binnen-tussen inhoud.

>[!CAUTION]
>
>De tussenliggende inhoud is pagina-inhoud. Deze wordt niet opgeslagen in het inhoudsfragment.

![ cfm-6420-02 ](assets/cfm-6420-02.png)

>[!NOTE]
>
>U kunt visuele activa (beelden) aan het fragment ook [ opnemen zelf ](/help/assets/content-fragments/content-fragments-variations.md#inserting-assets-into-your-fragment).
>
>Visuele elementen die in het fragment zelf worden ingevoegd, worden aan de voorafgaande alinea in het fragment gekoppeld. Dit betekent dat u geen tussenliggende inhoud tussen een visueel element en de voorgaande alinea kunt plaatsen.

>[!CAUTION]
>
>Nadat u tussenliggende inhoud aan een inhoudsfragment op uw pagina hebt toegevoegd, kan het wijzigen van de structuur van het onderliggende inhoudsfragment (dat wil zeggen in de inhoudfragmenteditor) leiden tot onjuiste/onverwachte resultaten.
>
>Wanneer dit gebeurt, wordt de tussenliggende inhoud als volgt bewaard:
>
>* Tussen componenten heeft een absolute positie binnen de reeks componenten in de fragmentstroom. Deze positie verandert niet, zelfs niet wanneer de inhoud van alinea&#39;s in het fragment verandert.
>
>  Hierdoor kan het lijken alsof de relatieve positionering is gewijzigd, aangezien de tussenliggende alinea&#39;s geen contextafhankelijke relatie hebben met de (fragment)alinea&#39;s naast de alinea&#39;s.
>* Tenzij de twee alinea&#39;s met elkaar in strijd zijn, wordt in dat geval de tussenliggende inhoud niet weergegeven (hoewel deze intern nog steeds aanwezig is).
>

### Gekoppelde inhoud gebruiken {#using-associated-content}

Als u [ bijbehorende inhoud ](/help/assets/content-fragments/content-fragments-assoc-content.md) met het [ inhoudsfragment ](/help/assets/content-fragments/content-fragments.md) hebt, zijn deze activa beschikbaar van het zijpaneel (nadat u uw fragment op de inhoudspagina plaatst). Gekoppelde content is in feite een speciale bron van content voor [tussenliggende content](#adding-in-between-content).

>[!NOTE]
>
>Er zijn diverse methodes om [ visuele activa (bijvoorbeeld, beelden) ](/help/assets/content-fragments/content-fragments.md#fragments-with-visual-assets) aan het fragment en/of de pagina toe te voegen.

>[!NOTE]
>
>Als u veelvoudige inhoudsfragmenten op één pagina hebt, toont het **Verwante Inhoud** lusje activa aangewezen aan alle fragmenten.

Zodra u een fragment met bijbehorende inhoud aan uw pagina hebt toegevoegd, wordt een nieuw lusje (**Geassocieerde Inhoud**) geopend in het zijpaneel.

Van hieruit kunt u de elementen naar de gewenste locatie slepen (naar een bestaande component of naar de gewenste positie waar de desbetreffende component is gemaakt):

![ cfm-6420-03 ](assets/cfm-6420-03.png)

### Assets ingevoegd in het fragment {#assets-inserted-into-the-fragment}

Als elementen (bijvoorbeeld afbeeldingen) in het fragment zelf zijn ingevoegd, zijn de opties voor het bewerken van deze elementen in de pagina-editor beperkt. <!-- Removed link as it was a 404 on helpx -->

Voor een afbeelding kunt u bijvoorbeeld

* Snijd, roteer of draai de afbeelding.
* Voeg een titel of alternatieve tekst toe.
* Geef een grootte op.
* U kunt ook de lay-out configureren.

Andere wijzigingen, zoals verplaatsen, kopiëren en verwijderen, moeten worden aangebracht in de fragmenteditor.

### Publiceren {#publishing}

Fragmenten moeten worden gepubliceerd zodat ze op gepubliceerde webpagina&#39;s kunnen worden gebruikt:

* Een fragment kan na [ worden gepubliceerd creërend het fragment in de console van Assets ](/help/assets/content-fragments/content-fragments.md#publishingandreferencingafragment).
* Als een *niet gepubliceerd fragment* op een pagina wordt gebruikt die wordt gepubliceerd, kan het fragment ook nu worden gepubliceerd.
