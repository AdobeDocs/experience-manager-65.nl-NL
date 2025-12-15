---
title: Inhoudsfragmenten beheren
description: Leer hoe u de Assets-console gebruikt om uw AEM Content Fragments, de basis van uw inhoud zonder kop, te beheren.
feature: Content Fragments
role: User
exl-id: 25c91a85-06ff-4666-a809-46778a689e25
solution: Experience Manager, Experience Manager Assets
source-git-commit: 11a8181e860c724c817dd549b351df079c8227e2
workflow-type: tm+mt
source-wordcount: '1728'
ht-degree: 6%

---

# Inhoudsfragmenten beheren {#managing-content-fragments}

Leer hoe u de Assets-console gebruikt om uw AEM Content Fragments, de basis van uw inhoud zonder kop, te beheren.

Na het bepalen van uw [&#x200B; Modellen van het Fragment van de Inhoud &#x200B;](#creating-a-content-model) kunt u deze gebruiken om [&#x200B; uw Fragmenten van de Inhoud &#x200B;](#creating-a-content-fragment) tot stand te brengen.

De [&#x200B; Redacteur van het Fragment van de Inhoud &#x200B;](#opening-the-fragment-editor) verstrekt diverse [&#x200B; wijzen &#x200B;](#modes-in-the-content-fragment-editor) om u toe te laten:

* [&#x200B; geeft de inhoud &#x200B;](#editing-the-content-of-your-fragment) uit en [&#x200B; leidt Variaties &#x200B;](#creating-and-managing-variations-within-your-fragment)
* [Uw fragment notities aanbrengen](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [Inhoud koppelen aan uw fragment](#associating-content-with-your-fragment)
* [De metagegevens configureren](#viewing-and-editing-the-metadata-properties-of-your-fragment)
* [De boomstructuur weergeven](/help/assets/content-fragments/content-fragments-structure-tree.md)
* [Voorvertoning van de JSON-representatie](/help/assets/content-fragments/content-fragments-json-preview.md)


>[!NOTE]
>
>Inhoudsfragmenten kunnen worden gebruikt:
>
>* wanneer het ontwerpen van pagina&#39;s; zie [&#x200B; het Authoring van de Pagina met de Fragmenten van de Inhoud &#x200B;](/help/sites-authoring/content-fragments.md).
>* voor [&#x200B; Hoofdloze Levering van de Inhoud gebruikend de Fragmenten van de Inhoud met GraphQL &#x200B;](/help/assets/content-fragments/content-fragments-graphql.md).

>[!NOTE]
>
>Ben me bewust van de [&#x200B; Beste praktijken &#x200B;](/help/assets/content-fragments/content-fragments.md#best-practices) wanneer het werken met uw Modellen van het Fragment van de Inhoud en de Fragmenten van de Inhoud.

>[!NOTE]
>
>De Fragmenten van de inhoud worden opgeslagen als **Assets**, zodat worden hoofdzakelijk geleid van de **Assets** console.

## Inhoudsfragmenten maken {#creating-content-fragments}

### Een inhoudsmodel maken {#creating-a-content-model}

[&#x200B; de fragmentmodellen van de Inhoud &#x200B;](/help/assets/content-fragments/content-fragments-models.md) kunnen worden toegelaten en worden gecreeerd, voorafgaand aan het creëren van inhoudsfragmenten met gestructureerde inhoud.

### Een inhoudsfragment maken {#creating-a-content-fragment}

De methode voor het maken van een inhoudsfragment is:

1. Ga naar de map **Assets** waar u het fragment wilt maken.
1. Selecteer **Maken** en vervolgens **Inhoudsfragment** om de wizard te openen.
1. In de eerste stap van de wizard moet u de basis van het nieuwe fragment opgeven.

   * [&#x200B; Model &#x200B;](/help/assets/content-fragments/content-fragments-models.md) - gebruikt om een fragment tot stand te brengen dat gestructureerde inhoud vereist; bijvoorbeeld, het **Adventure** model

      * Alle beschikbare modellen worden weergegeven.

   Na selectie, gebruik **daarna** te werk te gaan.

   ![&#x200B; fragmentbasis &#x200B;](assets/cfm-managing-01.png)

1. Geef in de stap **Eigenschappen** het volgende op:

   * **Basis**

      * **Titel**

        De fragmenttitel.

        Verplicht.

      * **Beschrijving**

      * **Markeringen**

   * **Geavanceerd**

      * **Naam**

        De naam; wordt gebruikt om de URL te vormen.

        Verplicht; wordt automatisch afgeleid van de titel, maar kan worden bijgewerkt.

1. Selecteer **Maken** om de actie te voltooien en **open** vervolgens het fragment voor het bewerken of keer terug naar de console met **Gereed**.

   >[!NOTE]
   >Op **Lijst** wijze van de console kunt u de **Montages van de Mening** bijwerken om de **Model van het Fragment van de Inhoud** kolom toe te laten.

## Handelingen voor een inhoudsfragment in de Assets-console {#actions-for-a-content-fragment-assets-console}

In de **Assets** console is een waaier van acties beschikbaar voor uw inhoudsfragmenten, of:

* Vanuit de werkbalk; nadat u het fragment hebt geselecteerd, zijn alle relevante handelingen beschikbaar.
* Als [&#x200B; snelle acties &#x200B;](/help/sites-authoring/basic-handling.md#quick-actions); een ondergroep acties beschikbaar voor de individuele fragmentkaarten.

![&#x200B; acties &#x200B;](assets/cfm-managing-02.png)

Selecteer het fragment om de werkbalk weer te geven met de toepasselijke acties:

* **Download**

   * Sla het fragment op als een ZIP-bestand. U kunt opgeven of u elementen, variaties of metagegevens wilt opnemen.

* **creeer**
* **Controle**
* **Eigenschappen**

   * Hiermee kunt u de metagegevens van het fragment weergeven en/of bewerken.

* **geeft** uit

   * Laat u [&#x200B; het fragment voor het uitgeven van inhoud &#x200B;](/help/assets/content-fragments/content-fragments-variations.md) samen met zijn elementen, variaties, bijbehorende inhoud en meta-gegevens openen.

* **beheert Markeringen**
* **aan Inzameling**
* **Exemplaar** (en **Deeg**)
* **Beweging**
* **Snel publiceren**
* **beheer Publicatie**
* **Schrapping**

>[!NOTE]
>
>Veel van deze zijn [&#x200B; standaardacties voor Assets &#x200B;](/help/assets/manage-assets.md) en/of [&#x200B; Desktop app van AEM &#x200B;](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html).

## De fragmenteditor openen {#opening-the-fragment-editor}

Uw fragment openen voor bewerken:

>[!CAUTION]
>
>Om een inhoudsfragment uit te geven hebt u [&#x200B; de aangewezen toestemmingen &#x200B;](/help/sites-developing/customizing-content-fragments.md#asset-permissions) nodig. Neem contact op met de systeembeheerder als er problemen optreden.

>[!CAUTION]
>
>U hebt de juiste machtigingen nodig om een inhoudsfragment te bewerken. Neem contact op met de systeembeheerder als er problemen optreden.

1. Gebruik de **Assets** console om aan de plaats van uw inhoudsfragment te navigeren.
1. Open het fragment voor bewerking door:

   * Klikken of tikken op de fragment- of fragmentkoppeling (dit is afhankelijk van de consoleweergave).
   * Het selecteren van het fragment, dan **geeft** van de toolbar uit.

1. De fragmenteditor wordt geopend. Breng de gewenste wijzigingen aan:

   ![&#x200B; fragmentredacteur &#x200B;](assets/cfm-managing-03.png)

1. Na het aanbrengen van veranderingen, gebruik **sparen**, **sparen en sluit** of **dicht** zoals vereist.

   >[!NOTE]
   >
   >**sparen &amp; sluit** is beschikbaar via **sparen** dropdown.

   >[!NOTE]
   >
   >Zowel **sparen &amp; dicht** en **dicht** zullen de redacteur weggaan - zie [&#x200B; sparen, dicht en Versies &#x200B;](#save-close-and-versions) voor volledige informatie over hoe de diverse opties voor inhoudsfragmenten werken.

## Modi en handelingen in de Inhoudsfragmenteditor {#modes-actions-content-fragment-editor}

Er zijn verschillende modi en acties beschikbaar in de Inhoudsfragmenteditor.

### Modi in de Content Fragment Editor {#modes-in-the-content-fragment-editor}

Navigeer door de verschillende modi met de pictogrammen in het zijpaneel:

* Variaties: [&#x200B; het uitgeven van de inhoud &#x200B;](#editing-the-content-of-your-fragment) en [&#x200B; het Leiden uw Variaties &#x200B;](#creating-and-managing-variations-within-your-fragment)

* [Annotaties](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [Gekoppelde inhoud](#associating-content-with-your-fragment)
* [Metagegevens](#viewing-and-editing-the-metadata-properties-of-your-fragment)
* [Boomstructuur](/help/assets/content-fragments/content-fragments-structure-tree.md)
* [Voorvertoning](/help/assets/content-fragments/content-fragments-json-preview.md)

![&#x200B; wijzen &#x200B;](assets/cfm-managing-04.png)

### Werkbalkhandelingen in de Inhoudsfragmenteditor {#toolbar-actions-in-the-content-fragment-editor}

Sommige functies in de bovenste werkbalk zijn beschikbaar in meerdere modi:

![&#x200B; wijzen &#x200B;](assets/cfm-managing-top-toolbar.png)

* Er wordt een bericht weergegeven wanneer er al naar het fragment wordt verwezen op een inhoudspagina. U kunt **sluiten** het bericht.

* Het zijpaneel kan worden verborgen/getoond gebruikend het **pictogram van de Kant van de Knevel**.

* Onder de fragmentnaam kunt u de naam van het [&#x200B; Model van het Fragment van de Inhoud zien &#x200B;](/help/assets/content-fragments/content-fragments-models.md) dat voor het creëren van het huidige fragment wordt gebruikt:

   * De naam is ook een verbinding die de modelredacteur opent.

* Zie de status van het fragment, bijvoorbeeld informatie over wanneer het is gemaakt, gewijzigd of gepubliceerd.

* **sparen** verleent toegang tot **sparen &amp; sluit** optie.

* De drie punts (**..**) drop-down verleent toegang tot extra acties:
   * **de paginaverwijzingen van de Update**
      * Hiermee werkt u alle paginaverwijzingen bij.
   * **[Snel publiceren](#publishing-and-referencing-a-fragment)**
   * **[beheer Publicatie](#publishing-and-referencing-a-fragment)**

<!--
* See the status of the fragment; for example, information about when it was created, modified or published. The status is also color-coded:

  * **New**: grey
  * **Draft**: blue
  * **Published**: green
  * **Modified**: orange
  * **Deactivated**: red
-->

<!--
This updates any page references and ensures that the Dispatcher is flushed as required. 
-->

## Opslaan, sluiten en versies {#save-close-and-versions}

>[!NOTE]
>
>De versies kunnen ook [&#x200B; worden gecreeerd, worden vergeleken en van de Chronologie &#x200B;](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments) worden teruggedraaid.

De editor heeft verschillende opties:

* **sparen** en **sparen &amp; sluit**

   * **sparen** zal de recentste veranderingen bewaren en in de redacteur blijven.
   * **sparen &amp; sluit** zal de recentste veranderingen bewaren en de redacteur weggaan.

  >[!CAUTION]
  >
  >Om een inhoudsfragment uit te geven hebt u [&#x200B; de aangewezen toestemmingen &#x200B;](/help/sites-developing/customizing-content-fragments.md#asset-permissions) nodig. Neem contact op met de systeembeheerder als er problemen optreden.

  >[!NOTE]
  >
  >Het is mogelijk om in de redacteur te blijven, makend een reeks veranderingen, alvorens te bewaren.

  >[!CAUTION]
  >
  >Naast het eenvoudig opslaan van uw wijzigingen, werken de acties ook alle verwijzingen bij en zorgen ze ervoor dat de Dispatcher naar wens wordt leeggemaakt. Deze wijzigingen kunnen enige tijd in beslag nemen. Hierdoor kan de prestaties van een groot/complex/zwaar geladen systeem worden beïnvloed.
  >
  >Houd dit in mening wanneer het gebruiken van **sparen &amp; sluit** en dan snel re-binnen de fragmentredacteur om verdere veranderingen aan te brengen en te bewaren.

* **dicht**

  Zal de redacteur weggaan zonder de recentste veranderingen (d.w.z. gemaakt sinds laatste **sparen**) op te slaan.

Terwijl het uitgeven van uw inhoudsfragment maakt AEM automatisch versies om ervoor te zorgen dat de vroegere inhoud kan worden hersteld als u uw veranderingen annuleert (gebruikend **dicht** zonder sparen):

1. Wanneer een inhoudsfragment voor het uitgeven van AEM controles op het bestaan van het op koekje-gebaseerde teken wordt geopend dat erop wijst of een *het uitgeven zitting* bestaat:

   1. Als het token wordt gevonden, wordt het fragment beschouwd als onderdeel van de bestaande bewerkingssessie.
   2. Als het teken *niet* beschikbaar is en de gebruiker begint inhoud uit te geven, wordt een versie gecreeerd en een teken voor deze nieuwe het uitgeven zitting wordt verzonden naar de cliënt, waar het in een koekje wordt bewaard.

2. Terwijl er een *actieve* het uitgeven zitting is, wordt de inhoud die automatisch bewaard om de 600 seconden (gebrek) wordt.

   >[!NOTE]
   >
   >Het interval voor automatisch opslaan kan worden geconfigureerd met het mechanisme `/conf` .
   >
   >Standaardwaarde, zie:
   >  `/libs/settings/dam/cfm/jcr:content/autoSaveInterval`

3. Als de gebruiker de bewerking annuleert, wordt de versie die aan het begin van de bewerkingssessie is gemaakt, hersteld en wordt de token verwijderd om de bewerkingssessie te beëindigen.
4. Als de gebruiker **&#x200B;**&#x200B;selecteert sparen uitgeeft, blijven de bijgewerkte elementen/de variaties voortbestaan en het teken wordt verwijderd om de het uitgeven zitting te beëindigen.

## De inhoud van het fragment bewerken {#editing-the-content-of-your-fragment}

Zodra u uw fragment hebt geopend, kunt u het [&#x200B; lusje van Variaties &#x200B;](/help/assets/content-fragments/content-fragments-variations.md) gebruiken om uw inhoud te schrijven.

## Variaties maken en beheren in uw fragment {#creating-and-managing-variations-within-your-fragment}

Zodra u de Hoofdinhoud hebt gecreeerd, kunt u, [&#x200B; Variaties &#x200B;](/help/assets/content-fragments/content-fragments-variations.md) van die inhoud tot stand brengen en leiden.

## Inhoud koppelen aan uw fragment {#associating-content-with-your-fragment}

U kunt [&#x200B; inhoud &#x200B;](/help/assets/content-fragments/content-fragments-assoc-content.md) met een fragment ook associëren. Dit biedt een verbinding zodat elementen (dat wil zeggen afbeeldingen) (optioneel) met het fragment kunnen worden gebruikt wanneer het aan een inhoudspagina wordt toegevoegd.

## De metagegevens (eigenschappen) van het fragment weergeven en bewerken {#viewing-and-editing-the-metadata-properties-of-your-fragment}

U kunt, de eigenschappen van een fragment bekijken en uitgeven gebruikend het [&#x200B; Meta-gegevens &#x200B;](/help/assets/content-fragments/content-fragments-metadata.md) lusje.

## Tijdlijn voor inhoudsfragmenten {#timeline-for-content-fragments}

Naast de standaardopties, [&#x200B; verstrekt de Chronologie &#x200B;](/help/assets/manage-assets.md#timeline) zowel informatie als acties specifiek voor inhoudsfragmenten:

* Informatie weergeven over versies, opmerkingen en annotaties
* Handelingen voor versies

   * **[keert aan deze Versie](#reverting-to-a-version)** terug (selecteer een bestaand fragment, toen een specifieke versie)

   * **[vergelijk met Huidige](#comparing-fragment-versions)** (selecteer een bestaand fragment, toen een specifieke versie)

   * Voeg a **Etiket** en/of **Commentaar** toe (selecteer een bestaand fragment, toen een specifieke versie)

   * **sparen als Versie** (selecteer een bestaand fragment, dan omhoog pijl bij de bodem van Chronologie)

* Handelingen voor annotaties

   * **Schrapping**

>[!NOTE]
>
>Opmerkingen zijn:
>
>* Standaardfunctionaliteit voor alle elementen
>* Gemaakt in tijdlijn
>* Verwant aan het fragmentelement
>
>Annotaties (voor inhoudsfragmenten) zijn:
>
>* Opgegeven in de fragmenteditor
>* Specifiek voor een geselecteerd tekstsegment binnen het fragment
>

Bijvoorbeeld:

![&#x200B; chronologie &#x200B;](assets/cfm-managing-05.png)

## Fragmentversies vergelijken {#comparing-fragment-versions}

**vergelijk met Huidige** actie is beschikbaar bij de [&#x200B; Chronologie &#x200B;](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments) nadat u een specifieke versie hebt geselecteerd.

Dit wordt geopend:

* de **Huidige** (recentste) versie (verlaten)

* de geselecteerde versie **v&lt; *x.y* >** (juist)

Zij worden naast elkaar getoond, waarbij:

* Eventuele verschillen worden gemarkeerd

   * Verwijderde tekst - rood
   * Ingevoegde tekst - groen
   * Vervangen tekst - blauw

* Met het pictogram voor volledig scherm kunt u een van beide versies afzonderlijk openen en vervolgens terugschakelen naar de parallelle weergave
* U kunt **terugkeren** aan de specifieke versie
* **Gedaan** zal u aan de console terugkeren

>[!NOTE]
>
>U kunt de fragmentinhoud niet bewerken wanneer u fragmenten vergelijkt.

![&#x200B; vergelijkend &#x200B;](assets/cfm-managing-06.png)

## Een versie herstellen  {#reverting-to-a-version}

U kunt terugkeren naar een specifieke versie van het fragment:

* Direct van de [&#x200B; Chronologie &#x200B;](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

  Selecteer de vereiste versie, dan terugkeren **aan deze** actie van Versie.

* Terwijl [&#x200B; het vergelijken van een versie aan de huidige versie &#x200B;](/help/assets/content-fragments/content-fragments-managing.md#comparing-fragment-versions) u **&#x200B;**&#x200B;aan de geselecteerde versie kunt terugkeren.

## Een fragment publiceren en ernaar verwijzen {#publishing-and-referencing-a-fragment}

>[!CAUTION]
>
>Als uw fragment op een model gebaseerd is, dan zou u moeten ervoor zorgen dat het [&#x200B; model &#x200B;](/help/assets/content-fragments/content-fragments-models.md#publishing-a-content-fragment-model) is gepubliceerd.
>
>Als u een inhoudsfragment publiceert waarvoor het model nog niet is gepubliceerd, wordt dit in een selectielijst aangegeven en wordt het model met het fragment gepubliceerd.

Inhoudsfragmenten moeten worden gepubliceerd voor gebruik in de publicatieomgeving. Zij kunnen worden gepubliceerd:

* Na verwezenlijking; het gebruiken van [&#x200B; acties beschikbaar in de console van Assets &#x200B;](#actions-for-a-content-fragment-assets-console).
* Van de [&#x200B; Redacteur van het Fragment van de Inhoud &#x200B;](#toolbar-actions-in-the-content-fragment-editor).
* Wanneer u [&#x200B; een pagina publiceert die het fragment &#x200B;](/help/sites-authoring/content-fragments.md#publishing) gebruikt; het fragment zal in de paginaverwijzingen worden vermeld.

>[!CAUTION]
>
>Nadat een fragment is gepubliceerd en/of waarnaar wordt verwezen, geeft AEM een waarschuwing weer wanneer een auteur het fragment opent voor opnieuw bewerken. Hiermee wordt u gewaarschuwd dat wijzigingen in het fragment ook van invloed zijn op de pagina&#39;s waarnaar wordt verwezen.

## Een fragment verwijderen {#deleting-a-fragment}

Een fragment verwijderen:

1. In de **Assets** console navigeert aan de plaats van het inhoudsfragment.
2. Selecteer het fragment.

   >[!NOTE]
   >
   >De **schrapping** actie is niet beschikbaar als snelle actie.

3. Selecteer **Schrapping** van de toolbar.
4. Bevestig **schrapping** actie.

   >[!CAUTION]
   >
   >Als er al naar het fragment wordt verwezen op een pagina, wordt er een waarschuwingsbericht weergegeven en moet u bevestigen dat u wilt doorgaan met **Verwijderen forceren**. Het fragment wordt samen met de bijbehorende component voor contentfragmenten uit alle contentpagina&#39;s verwijderd.
