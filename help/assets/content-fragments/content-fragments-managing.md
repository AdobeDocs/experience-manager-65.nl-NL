---
title: Inhoudsfragmenten beheren
description: Leer hoe u de middelenconsole kunt gebruiken om uw AEM inhoudsfragmenten, de basis van uw inhoud zonder kop, te beheren.
feature: Content Fragments
role: User
exl-id: 25c91a85-06ff-4666-a809-46778a689e25
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1712'
ht-degree: 6%

---

# Inhoudsfragmenten beheren {#managing-content-fragments}

Leer hoe u de middelenconsole kunt gebruiken om uw AEM inhoudsfragmenten, de basis van uw inhoud zonder kop, te beheren.

Na het definiëren van uw [Modellen van inhoudsfragmenten](#creating-a-content-model) U kunt deze [Inhoudsfragmenten maken](#creating-a-content-fragment).

De [Inhoudsfragmenteditor](#opening-the-fragment-editor) biedt diverse [modi](#modes-in-the-content-fragment-editor) om u in staat te stellen:

* [De inhoud bewerken](#editing-the-content-of-your-fragment) en [Variaties beheren](#creating-and-managing-variations-within-your-fragment)
* [Uw fragment notities aanbrengen](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [Inhoud koppelen aan uw fragment](#associating-content-with-your-fragment)
* [De metagegevens configureren](#viewing-and-editing-the-metadata-properties-of-your-fragment)
* [De boomstructuur weergeven](/help/assets/content-fragments/content-fragments-structure-tree.md)
* [Voorvertoning van de JSON-representatie](/help/assets/content-fragments/content-fragments-json-preview.md)


>[!NOTE]
>
>Inhoudsfragmenten kunnen worden gebruikt:
>
>* bij het ontwerpen van pagina&#39;s; zie [Pagina&#39;s ontwerpen met inhoudsfragmenten](/help/sites-authoring/content-fragments.md).
>* for [Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL](/help/assets/content-fragments/content-fragments-graphql.md).

>[!NOTE]
>
>Inhoudsfragmenten worden opgeslagen als **Activa**, en dus in de eerste plaats vanuit de **Activa** console.

## Inhoudsfragmenten maken {#creating-content-fragments}

### Een inhoudsmodel maken {#creating-a-content-model}

[Inhoudsfragmentmodellen](/help/assets/content-fragments/content-fragments-models.md) kunnen worden ingeschakeld en gemaakt voordat u inhoudsfragmenten met gestructureerde inhoud maakt.

### Een inhoudsfragment maken {#creating-a-content-fragment}

De methode voor het maken van een inhoudsfragment is:

1. Ga naar de map **Assets** waar u het fragment wilt maken.
1. Selecteer **Maken** en vervolgens **Inhoudsfragment** om de wizard te openen.
1. In de eerste stap van de wizard moet u de basis van het nieuwe fragment opgeven.

   * [Model](/help/assets/content-fragments/content-fragments-models.md) - wordt gebruikt om een fragment te maken waarvoor gestructureerde inhoud nodig is, bijvoorbeeld de **Adventure** model

      * Alle beschikbare modellen worden weergegeven.

   Na selectie kunt u **Volgende** om verder te gaan.

   ![fragmentbasis](assets/cfm-managing-01.png)

1. Geef in de stap **Eigenschappen** het volgende op:

   * **Basis**

      * **Titel**

        De fragmenttitel.

        Verplicht.

      * **Beschrijving**

      * **Tags**

   * **Geavanceerd**

      * **Naam**

        De naam; wordt gebruikt om de URL te vormen.

        Verplicht; wordt automatisch afgeleid van de titel, maar kan worden bijgewerkt.

1. Selecteer **Maken** om de actie te voltooien en **open** vervolgens het fragment voor het bewerken of keer terug naar de console met **Gereed**.

   >[!NOTE]
   >In **Lijst** wijze van de console u kunt bijwerken **Instellingen weergeven** de **Inhoudsfragmentmodel** kolom.

## Handelingen voor een inhoudsfragment in de middelenconsole {#actions-for-a-content-fragment-assets-console}

In de **Activa** een reeks acties beschikbaar is voor uw inhoudsfragmenten:

* Vanuit de werkbalk; nadat u het fragment hebt geselecteerd, zijn alle relevante handelingen beschikbaar.
* Als [snelle acties](/help/sites-authoring/basic-handling.md#quick-actions); een subset van acties beschikbaar voor de afzonderlijke fragmentkaarten.

![handelingen](assets/cfm-managing-02.png)

Selecteer het fragment om de werkbalk weer te geven met de toepasselijke acties:

* **Downloaden**

   * Sla het fragment op als een ZIP-bestand. U kunt opgeven of u elementen, variaties of metagegevens wilt opnemen.

* **Maken**
* **Afhandeling**
* **Eigenschappen**

   * Hiermee kunt u de metagegevens van het fragment weergeven en/of bewerken.

* **Bewerken**

   * Laat u [het fragment openen voor het bewerken van inhoud](/help/assets/content-fragments/content-fragments-variations.md) samen met de elementen, variaties, bijbehorende inhoud en metagegevens.

* **Tags beheren**
* **Naar verzameling**
* **Kopiëren** (en **Plakken**)
* **Verplaatsen**
* **Snel publiceren**
* **Publicatie beheren**
* **Verwijderen**

>[!NOTE]
>
>Veel van deze zijn [standaardhandelingen voor elementen](/help/assets/manage-assets.md) en/of de [Bureaubladapp AEM](https://helpx.adobe.com/experience-manager/desktop-app/aem-desktop-app.html).

## De fragmenteditor openen {#opening-the-fragment-editor}

Uw fragment openen voor bewerken:

>[!CAUTION]
>
>Als u een inhoudsfragment wilt bewerken, hebt u [de juiste machtigingen](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Neem contact op met de systeembeheerder als er problemen optreden.

>[!CAUTION]
>
>U hebt de juiste machtigingen nodig om een inhoudsfragment te bewerken. Neem contact op met de systeembeheerder als er problemen optreden.

1. Gebruik de **Activa** -console om naar de locatie van het inhoudsfragment te navigeren.
1. Open het fragment voor bewerking door:

   * Klikken of tikken op de fragment- of fragmentkoppeling (dit is afhankelijk van de consoleweergave).
   * Het fragment selecteren en vervolgens **Bewerken** op de werkbalk.

1. De fragmenteditor wordt geopend. Breng de gewenste wijzigingen aan:

   ![fragmenteditor](assets/cfm-managing-03.png)

1. Nadat u wijzigingen hebt aangebracht, kunt u **Opslaan**, **Opslaan en sluiten** of **Sluiten** zoals vereist.

   >[!NOTE]
   >
   >**Opslaan en sluiten** is beschikbaar via **Opslaan** vervolgkeuzelijst.

   >[!NOTE]
   >
   >Beide **Opslaan en sluiten** en **Sluiten** sluit de editor af - zie [Opslaan, sluiten en versies](#save-close-and-versions) voor volledige informatie over de werking van de verschillende opties voor inhoudsfragmenten.

## Modi en handelingen in de Inhoudsfragmenteditor {#modes-actions-content-fragment-editor}

Er zijn verschillende modi en acties beschikbaar in de Inhoudsfragmenteditor.

### Modi in de Content Fragment Editor {#modes-in-the-content-fragment-editor}

Navigeer door de verschillende modi met de pictogrammen in het zijpaneel:

* Variaties: [De inhoud bewerken](#editing-the-content-of-your-fragment) en [Uw variaties beheren](#creating-and-managing-variations-within-your-fragment)

* [Annotaties](/help/assets/content-fragments/content-fragments-variations.md#annotating-a-content-fragment)
* [Gekoppelde inhoud](#associating-content-with-your-fragment)
* [Metagegevens](#viewing-and-editing-the-metadata-properties-of-your-fragment)
* [Boomstructuur](/help/assets/content-fragments/content-fragments-structure-tree.md)
* [Voorvertoning](/help/assets/content-fragments/content-fragments-json-preview.md)

![modi](assets/cfm-managing-04.png)

### Werkbalkhandelingen in de Inhoudsfragmenteditor {#toolbar-actions-in-the-content-fragment-editor}

Sommige functies in de bovenste werkbalk zijn beschikbaar in meerdere modi:

![modi](assets/cfm-managing-top-toolbar.png)

* Er wordt een bericht weergegeven wanneer er al naar het fragment wordt verwezen op een inhoudspagina. U kunt **Sluiten** het bericht.

* Het zijpaneel kan worden verborgen of weergegeven met de opdracht **Zijpaneel in-/uitschakelen** pictogram.

* Onder de fragmentnaam ziet u de naam van de component [Inhoudsfragmentmodel](/help/assets/content-fragments/content-fragments-models.md) gebruikt voor het maken van het huidige fragment:

   * De naam is ook een verbinding die de modelredacteur opent.

* Zie de status van het fragment, bijvoorbeeld informatie over wanneer het is gemaakt, gewijzigd of gepubliceerd.

* **Opslaan** verleent toegang tot **Opslaan en sluiten** -optie.

* De drie stippen (**...**) biedt toegang tot extra handelingen:
   * **Paginaverwijzingen bijwerken**
      * Hiermee werkt u alle paginaverwijzingen bij.
   * **[Snel publiceren](#publishing-and-referencing-a-fragment)**
   * **[Publicatie beheren](#publishing-and-referencing-a-fragment)**

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
>Versies kunnen ook [gemaakt, vergeleken en teruggezet vanaf de tijdlijn](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

De editor heeft verschillende opties:

* **Opslaan** en **Opslaan en sluiten**

   * **Opslaan** slaat de laatste wijzigingen op en blijft deze in de editor.
   * **Opslaan en sluiten** slaat de laatste wijzigingen op en sluit de editor af.

  >[!CAUTION]
  >
  >Als u een inhoudsfragment wilt bewerken, hebt u [de juiste machtigingen](/help/sites-developing/customizing-content-fragments.md#asset-permissions). Neem contact op met de systeembeheerder als er problemen optreden.

  >[!NOTE]
  >
  >Het is mogelijk om in de redacteur te blijven, makend een reeks veranderingen, alvorens te bewaren.

  >[!CAUTION]
  >
  >Naast het eenvoudig opslaan van uw wijzigingen, werken de acties ook verwijzingen bij en zorgen ervoor dat de Dispatcher wordt leeggemaakt zoals vereist. Deze wijzigingen kunnen enige tijd in beslag nemen. Hierdoor kan de prestaties van een groot/complex/zwaar geladen systeem worden beïnvloed.
  >
  >Houd hier rekening mee wanneer u **Opslaan en sluiten** en voert u vervolgens snel de fragmenteditor opnieuw in om verdere wijzigingen aan te brengen en op te slaan.

* **Sluiten**

  Sluit de editor af zonder de laatste wijzigingen op te slaan (dat wil zeggen sinds de laatste **Opslaan**).

AEM tijdens het bewerken van het inhoudsfragment automatisch versies maken om ervoor te zorgen dat eerdere inhoud kan worden hersteld als u de wijzigingen annuleert (met **Sluiten** zonder opslaan):

1. Wanneer een inhoudsfragment wordt geopend om te bewerken, wordt op het bestaan van een cookie-token gecontroleerd dat aangeeft of een *bewerksessie* bestaat:

   1. Als het token wordt gevonden, wordt het fragment beschouwd als onderdeel van de bestaande bewerkingssessie.
   2. Als het token *niet* beschikbaar is en de gebruiker begint met het bewerken van inhoud, wordt een versie gemaakt en wordt een token voor deze nieuwe bewerkingssessie verzonden naar de client, waar deze in een cookie wordt opgeslagen.

2. Terwijl er een *actief* tijdens het bewerken van de sessie wordt de inhoud die wordt bewerkt automatisch om de 600 seconden opgeslagen (standaard).

   >[!NOTE]
   >
   >Het auto sparen interval is configureerbaar gebruikend `/conf` mechanisme.
   >
   >Standaardwaarde, zie:
   >  `/libs/settings/dam/cfm/jcr:content/autoSaveInterval`

3. Als de gebruiker de bewerking annuleert, wordt de versie die aan het begin van de bewerkingssessie is gemaakt, hersteld en wordt de token verwijderd om de bewerkingssessie te beëindigen.
4. Als de gebruiker selecteert om **Opslaan** de bewerkingen, de bijgewerkte elementen/variaties worden voortgezet en het token wordt verwijderd om de bewerkingssessie te beëindigen.

## De inhoud van het fragment bewerken {#editing-the-content-of-your-fragment}

Als u het fragment hebt geopend, kunt u de opdracht [Variaties](/help/assets/content-fragments/content-fragments-variations.md) gebruiken om uw inhoud te ontwerpen.

## Variaties maken en beheren in uw fragment {#creating-and-managing-variations-within-your-fragment}

Als u de inhoud van het stramien hebt gemaakt, kunt u [Variaties](/help/assets/content-fragments/content-fragments-variations.md) van die inhoud.

## Inhoud koppelen aan uw fragment {#associating-content-with-your-fragment}

U kunt [gekoppelde inhoud](/help/assets/content-fragments/content-fragments-assoc-content.md) met een fragment. Dit biedt een verbinding zodat elementen (dat wil zeggen afbeeldingen) (optioneel) met het fragment kunnen worden gebruikt wanneer het aan een inhoudspagina wordt toegevoegd.

## De metagegevens (eigenschappen) van het fragment weergeven en bewerken {#viewing-and-editing-the-metadata-properties-of-your-fragment}

U kunt de eigenschappen van een fragment weergeven en bewerken met de opdracht [Metagegevens](/help/assets/content-fragments/content-fragments-metadata.md) tab.

## Tijdlijn voor inhoudsfragmenten {#timeline-for-content-fragments}

Naast de standaardopties [Tijdlijn](/help/assets/manage-assets.md#timeline) biedt zowel informatie als acties die specifiek zijn voor inhoudsfragmenten:

* Informatie weergeven over versies, opmerkingen en annotaties
* Handelingen voor versies

   * **[Deze versie herstellen](#reverting-to-a-version)** (selecteer een bestaand fragment en selecteer vervolgens een specifieke versie)

   * **[Vergelijken met huidige](#comparing-fragment-versions)** (selecteer een bestaand fragment en selecteer vervolgens een specifieke versie)

   * Voeg een **Label** en/of **Opmerking** (selecteer een bestaand fragment en selecteer vervolgens een specifieke versie)

   * **Opslaan als versie** (selecteer een bestaand fragment en klik vervolgens op de pijl omhoog onder aan de tijdlijn)

* Handelingen voor annotaties

   * **Verwijderen**

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

![tijdlijn](assets/cfm-managing-05.png)

## Fragmentversies vergelijken {#comparing-fragment-versions}

De **Vergelijken met huidige** actie is beschikbaar via de [Tijdlijn](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments) nadat u een specifieke versie hebt geselecteerd.

Dit wordt geopend:

* de **Huidig** (meest recente) versie (links)

* de geselecteerde versie **v&lt;*x.y*>** (rechts)

Zij worden naast elkaar getoond, waarbij:

* Eventuele verschillen worden gemarkeerd

   * Verwijderde tekst - rood
   * Ingevoegde tekst - groen
   * Vervangen tekst - blauw

* Met het pictogram voor volledig scherm kunt u een van beide versies afzonderlijk openen en vervolgens terugschakelen naar de parallelle weergave
* U kunt **Vorige versie** naar de specifieke versie
* **Gereed** zult u aan de console terugkeren

>[!NOTE]
>
>U kunt de fragmentinhoud niet bewerken wanneer u fragmenten vergelijkt.

![vergelijking](assets/cfm-managing-06.png)

## Een versie herstellen  {#reverting-to-a-version}

U kunt terugkeren naar een specifieke versie van het fragment:

* Rechtstreeks vanuit de [Tijdlijn](/help/assets/content-fragments/content-fragments-managing.md#timeline-for-content-fragments).

  Selecteer de gewenste versie en klik vervolgens op **Deze versie herstellen** handeling.

* while [een versie vergelijken met de huidige versie](/help/assets/content-fragments/content-fragments-managing.md#comparing-fragment-versions) u kunt **Vorige versie** naar de geselecteerde versie.

## Een fragment publiceren en ernaar verwijzen {#publishing-and-referencing-a-fragment}

>[!CAUTION]
>
>Als het fragment op een model is gebaseerd, moet u ervoor zorgen dat de [model is gepubliceerd](/help/assets/content-fragments/content-fragments-models.md#publishing-a-content-fragment-model).
>
>Als u een inhoudsfragment publiceert waarvoor het model nog niet is gepubliceerd, wordt dit in een selectielijst aangegeven en wordt het model met het fragment gepubliceerd.

Inhoudsfragmenten moeten worden gepubliceerd voor gebruik in de publicatieomgeving. Zij kunnen worden gepubliceerd:

* Na het maken; gebruiken [acties beschikbaar in de middelenconsole](#actions-for-a-content-fragment-assets-console).
* Van de [Inhoudsfragmenteditor](#toolbar-actions-in-the-content-fragment-editor).
* Wanneer u [Een pagina publiceren die het fragment gebruikt](/help/sites-authoring/content-fragments.md#publishing); het fragment wordt weergegeven in de paginaverwijzingen.

>[!CAUTION]
>
>Nadat een fragment is gepubliceerd en/of waarnaar wordt verwezen, geeft AEM een waarschuwing weer wanneer een auteur het fragment opent om opnieuw te bewerken. Hiermee wordt u gewaarschuwd dat wijzigingen in het fragment ook van invloed zijn op de pagina&#39;s waarnaar wordt verwezen.

## Een fragment verwijderen {#deleting-a-fragment}

Een fragment verwijderen:

1. In de **Activa** navigeren naar de locatie van het inhoudsfragment.
2. Selecteer het fragment.

   >[!NOTE]
   >
   >De **Verwijderen** Handeling is niet beschikbaar als een snelle handeling.

3. Selecteren **Verwijderen** op de werkbalk.
4. Bevestig de **Verwijderen** handeling.

   >[!CAUTION]
   >
   >Als er al naar het fragment wordt verwezen op een pagina, wordt er een waarschuwingsbericht weergegeven en moet u bevestigen dat u wilt doorgaan met **Verwijderen forceren**. Het fragment wordt samen met de bijbehorende component voor contentfragmenten uit alle contentpagina&#39;s verwijderd.
