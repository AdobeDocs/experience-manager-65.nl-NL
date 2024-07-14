---
title: Forms ontwikkelen (klassieke gebruikersinterface)
description: Meer informatie over het ontwikkelen van formulieren voor de klassieke gebruikersinterface van Adobe Experience Manager
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
docset: aem65
exl-id: f43e9491-aa8f-40af-9800-123695142559
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1930'
ht-degree: 0%

---

# Forms ontwikkelen (klassieke gebruikersinterface){#developing-forms-classic-ui}

De basisstructuur van een formulier is:

* Begin formulier
* Formulierelementen
* Einde van formulier

Al deze worden gerealiseerd met een reeks standaard [ componenten van de Vorm ](/help/sites-authoring/default-components.md#form), beschikbaar in een standaard AEM installatie.

Naast [ het ontwikkelen van nieuwe componenten ](/help/sites-developing/developing-components-samples.md) voor gebruik op uw vormen kunt u ook:

* [Uw formulier vooraf laden met waarden](#preloading-form-values)
* [(bepaalde) velden met meerdere waarden vooraf laden](#preloading-form-fields-with-multiple-values)
* [Nieuwe acties ontwikkelen](#developing-your-own-form-actions)
* [Nieuwe beperkingen ontwikkelen](#developing-your-own-form-constraints)
* [Specifieke formuliervelden weergeven of verbergen](#showing-and-hiding-form-components)

[ Gebruikend manuscripten ](#developing-scripts-for-use-with-forms) om functionaliteit waar nodig uit te breiden.

>[!NOTE]
>
>Dit document concentreert zich bij het ontwikkelen van vormen gebruikend de [ Componenten van de Stichting ](/help/sites-authoring/default-components-foundation.md) in klassieke UI. De Adobe adviseert gebruikend de nieuwe [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html) en [ Verberg Voorwaarden ](/help/sites-developing/hide-conditions.md) voor vormontwikkeling in touch-Toegelaten UI.

## Formulierwaarden vooraf laden {#preloading-form-values}

De component van het vormbegin verstrekt een gebied voor de **Weg van de Lading**, een facultatieve weg die aan een knoop in de bewaarplaats richt.

Het pad laden is het pad naar knoopeigenschappen dat wordt gebruikt om vooraf gedefinieerde waarden te laden in meerdere velden op het formulier.

Dit is een optioneel veld dat het pad naar een knooppunt in de repository aangeeft. Als dit knooppunt eigenschappen heeft die overeenkomen met de veldnamen, worden de desbetreffende velden op het formulier vooraf geladen met de waarde van die eigenschappen. Als er geen overeenkomst bestaat, bevat het veld de standaardwaarde.

>[!NOTE]
>
>A [ vormactie ](#developing-your-own-form-actions) kan het middel ook plaatsen waarvan om de aanvankelijke waarden te laden. Dit gebeurt met `FormsHelper#setFormLoadResource` inside `init.jsp` .
>
>Alleen als dit niet is ingesteld, wordt het formulier door de auteur ingevuld in de padset die in het beginformulieronderdeel is ingesteld.

### Formuliervelden met meerdere waarden vooraf laden {#preloading-form-fields-with-multiple-values}

De diverse vormgebieden hebben ook de **Pad van de Lading van Punten**, opnieuw een facultatieve weg die aan een knoop in de bewaarplaats richt.

De **Weg van Punten laden** is de weg aan knoopeigenschappen die wordt gebruikt om vooraf bepaalde waarden in dat specifieke gebied op de vorm te laden, bijvoorbeeld, a [ drop-down lijst ](/help/sites-authoring/default-components-foundation.md#dropdown-list), [ de groep van de controledoos ](/help/sites-authoring/default-components-foundation.md#checkbox-group) of [ radiagroep ](/help/sites-authoring/default-components-foundation.md#radio-group).

#### Voorbeeld - Een vervolgkeuzelijst met meerdere waarden vooraf laden {#example-preloading-a-dropdown-list-with-multiple-values}

Een vervolgkeuzelijst kan worden geconfigureerd met uw reeks waarden voor selectie.

De **Weg van de Lading van Punten** kan worden gebruikt om tot een lijst van een omslag in de bewaarplaats toegang te hebben en deze in het gebied vooraf te laden:

1. Een deelmap maken ( `sling:Folder`)
bijvoorbeeld `/etc/designs/<myDesign>/formlistvalues`

1. Voeg een nieuwe eigenschap (bijvoorbeeld `myList` ) van het type tekenreeks met meerdere waarden ( `String[]` ) toe voor de lijst met vervolgkeuzelijsten. Inhoud kan ook worden geïmporteerd met een script, zoals met een JSP-script of cURL in een shell-script.

1. Gebruik de volledige weg op het **Pad van de Lading van Pad** gebied:
bijvoorbeeld `/etc/designs/geometrixx/formlistvalues/myList`

Als de waarden in de `String[]` als volgt zijn opgemaakt:

* `AL=Alabama`
* `AK=Alaska`

en zo verder, dan AEM produceert de lijst als:

* `<option value="AL">Alabama</option>`
* `<option value="AK">Alaska</option>`

Deze functie kan bijvoorbeeld goed worden gebruikt in een meertalige instelling.

### Uw eigen formulierhandelingen ontwikkelen {#developing-your-own-form-actions}

Een formulier heeft een handeling nodig. Met een handeling wordt de bewerking gedefinieerd die wordt uitgevoerd wanneer het formulier wordt verzonden met de gebruikersgegevens.

Een reeks acties wordt voorzien van een standaard AEM installatie, deze kunnen onder worden gezien:

`/libs/foundation/components/form/actions`

en in de **lijst van het Type van Actie** van de **Vorm** component:

![ chlimage_1-8 ](assets/chlimage_1-8.png)

In deze sectie wordt beschreven hoe u uw eigen formulieractie voor opname in deze lijst kunt ontwikkelen.

U kunt als volgt uw eigen actie onder `/apps` toevoegen:

1. Maak een knooppunt van het type `sling:Folder` . Geef een naam op die de uit te voeren handeling weerspiegelt.

   Bijvoorbeeld:

   `/apps/myProject/components/customFormAction`

1. Op deze knoop bepaalt de volgende eigenschappen, dan klik **sparen allen** om uw veranderingen voort te zetten:

   * `sling:resourceType` - instellen als `foundation/components/form/action`

   * `componentGroup` - definiëren als `.hidden`

   * Optioneel:

      * `jcr:title` - geef een gewenste titel op. Deze wordt weergegeven in de vervolgkeuzelijst. Indien niet ingesteld, wordt de knooppuntnaam weergegeven

      * `jcr:description` - voer een beschrijving van uw keuze in

1. Maak in de map een dialoogvenster:

   1. Voeg velden toe, zodat de auteur het dialoogvenster Formulieren kan bewerken zodra de handeling is gekozen.

1. Maak in de map een van de volgende handelingen:

   1. Een postscript.
De naam van het script is bijvoorbeeld `post.POST.<extension>` `post.POST.jsp`
Het postscript wordt aangeroepen wanneer een formulier wordt verzonden om het formulier te verwerken, bevat het de code waarmee de gegevens die uit het formulier afkomstig zijn, worden afgehandeld `POST` .

   1. Voeg een voorwaarts script toe dat wordt aangeroepen wanneer het formulier wordt verzonden.
De naam van het script is bijvoorbeeld `forward.<extension`> `forward.jsp`
Dit script kan een pad definiëren. Het huidige verzoek wordt dan door:sturen aan de gespecificeerde weg.

   De vereiste aanroep is `FormsHelper#setForwardPath` (2 varianten). Doorgaans wordt een validatie, oftewel logica, uitgevoerd om het doelpad te vinden en vervolgens door te sturen naar dat pad, zodat de standaard Sling POST-servlet de werkelijke opslag in JCR kan uitvoeren.

   Er kan ook een andere servlet zijn die de daadwerkelijke verwerking uitvoert, in een dergelijk geval zouden de formulieractie en `forward.jsp` alleen als de &quot;lijm&quot;-code fungeren. Een voorbeeld van dit is de postactie bij `/libs/foundation/components/form/actions/mail`, die details aan `<currentpath>.mail.html` door:sturen waar een postservlet heeft.

   Dus:

   * a `post.POST.jsp` is handig voor kleine bewerkingen die volledig door de handeling zelf worden uitgevoerd
   * terwijl `forward.jsp` nuttig is wanneer slechts delegatie wordt vereist.

   De uitvoeringsvolgorde voor de scripts is:

   * Tijdens het weergeven van het formulier ( `GET`):

      1. `init.jsp`
      1. voor alle beperkingen van het veld: `clientvalidation.jsp`
      1. validationRT van formulier: `clientvalidation.jsp`
      1. formulier wordt geladen via bron laden indien ingesteld
      1. `addfields.jsp` tijdens renderen `<form></form>`

   * bij het verwerken van een formulier `POST` :

      1. `init.jsp`
      1. voor alle beperkingen van het veld: `servervalidation.jsp`
      1. validationRT van formulier: `servervalidation.jsp`
      1. `forward.jsp`
      1. Als een voorwaarts pad is ingesteld ( `FormsHelper.setForwardPath` ), stuurt u de aanvraag door en roept u vervolgens `cleanup.jsp` aan

      1. Als er geen voorwaarts pad is ingesteld, roept u `post.POST.jsp` aan (eindigt hier, geen `cleanup.jsp` aangeroepen)

1. Voeg desgewenst opnieuw toe aan de map:

   1. Een script voor het toevoegen van velden.
De naam van het script is bijvoorbeeld `addfields.<extension>` `addfields.jsp`
Een `addfields` -script wordt direct aangeroepen nadat de HTML voor het starten van het formulier is geschreven. Op deze manier kan de actie aangepaste invoervelden of andere HTML toevoegen in het formulier.

   1. Een initialisatiescript.
De naam van het script is bijvoorbeeld `init.<extension>` `init.jsp`
Dit script wordt aangeroepen wanneer het formulier wordt gegenereerd. Deze kan worden gebruikt om actiespecificaties te initialiseren.

   1. Een opschoonscript.
De naam van het script is bijvoorbeeld `cleanup.<extension>` `cleanup.jsp`
Dit script kan worden gebruikt om opschoning uit te voeren.

1. Gebruik de **component van Forms** in parsys. Het **Type van Actie** drop-down zal nu uw nieuwe actie omvatten.

   >[!NOTE]
   >
   >Standaardhandelingen weergeven die deel uitmaken van het product:
   >
   >
   >`/libs/foundation/components/form/actions`

### Uw eigen formulierbeperkingen ontwikkelen {#developing-your-own-form-constraints}

Beperkingen kunnen op twee niveaus worden opgelegd:

* Voor [ individuele gebieden (zie de volgende procedure) ](#constraints-for-individual-fields)
* Als [ vorm-globale bevestiging ](#form-global-constraints)

#### Restricties voor afzonderlijke velden {#constraints-for-individual-fields}

U kunt als volgt uw eigen beperkingen voor een afzonderlijk veld (onder `/apps`) toevoegen:

1. Maak een knooppunt van het type `sling:Folder` . Geef een naam op die de restrictie weerspiegelt die moet worden geïmplementeerd.

   Bijvoorbeeld:

   `/apps/myProject/components/customFormConstraint`

1. Op deze knoop bepaalt de volgende eigenschappen, dan klik **sparen allen** om uw veranderingen voort te zetten:

   * `sling:resourceType` - ingesteld op `foundation/components/form/constraint`

   * `constraintMessage` - een aangepast bericht dat wordt weergegeven als het veld volgens de beperking niet geldig is op het moment dat het formulier wordt verzonden

   * Optioneel:

      * `jcr:title` - geef een gewenste titel op. Deze wordt weergegeven in de selectielijst. Indien niet ingesteld, wordt de knooppuntnaam weergegeven
      * `hint` - aanvullende informatie voor de gebruiker over het gebruik van het veld

1. In deze map hebt u de volgende scripts nodig:

   * Een clientvalidatiescript:
De naam van het script is bijvoorbeeld `clientvalidation.<extension>` `clientvalidation.jsp`
Dit wordt aangeroepen wanneer het formulierveld wordt gegenereerd. U kunt hiermee JavaScript voor de client maken om het veld op de client te valideren.

   * Een servervalidatiescript:
De naam van het script is bijvoorbeeld `servervalidation.<extension>` `servervalidation.jsp`
Dit wordt aangeroepen wanneer het formulier wordt verzonden. Het kan worden gebruikt om het gebied op de server te bevestigen nadat het wordt voorgelegd.

>[!NOTE]
>
>Voorbeelden van beperkingen zijn:
>
>`/libs/foundation/components/form/constraints`

#### Formulierglobale beperkingen {#form-global-constraints}

De algemene validatie van het formulier wordt opgegeven door een brontype te configureren in de beginformuliercomponent ( `validationRT` ). Bijvoorbeeld:

`apps/myProject/components/form/validation`

Vervolgens kunt u het volgende definiëren:

* a `clientvalidation.jsp` - geïnjecteerd na de validatiescripts van de client van het veld
* en een `servervalidation.jsp` - ook aangeroepen na de afzonderlijke validaties van de veldserver op een `POST` .

### Formuliercomponenten weergeven en verbergen {#showing-and-hiding-form-components}

U kunt het formulier zo configureren dat formuliercomponenten worden weergegeven of verborgen op basis van de waarde van andere velden in het formulier.

Het is handig de zichtbaarheid van een formulierveld te wijzigen als het veld alleen onder bepaalde omstandigheden nodig is. Op een feedbackformulier wordt bijvoorbeeld aan klanten gevraagd of ze productinformatie per e-mail naar hen willen sturen. Als u Ja selecteert, wordt een tekstveld weergegeven waarmee de klant zijn e-mailadres kan typen.

Gebruik **uitgeven tonen/verberg Regels** dialoogdoos om de voorwaarden te specificeren waaronder een vormcomponent wordt getoond of verborgen.

![ showhideeditor ](assets/showhideeditor.png)

Gebruik de velden boven in het dialoogvenster om de volgende informatie op te geven:

* Of u voorwaarden voor het verbergen of weergeven van de component opgeeft.
* Of om het even welke of alle voorwaarden waar moeten zijn om de component te tonen of te verbergen.

Onder deze velden worden een of meer voorwaarden weergegeven. Een voorwaarde vergelijkt de waarde van een andere formuliercomponent (op hetzelfde formulier) met een waarde. Als de werkelijke waarde in het veld aan de voorwaarde voldoet, wordt de waarde true geëvalueerd. De voorwaarden omvatten de volgende informatie:

* De titel van het formulierveld dat wordt getest.
* Een operator.
* Er wordt een waarde vergeleken met de veldwaarde.

Een component Groep keuzerondjes met de titel `Receive email notifications?` * * bevat bijvoorbeeld keuzerondjes `Yes` en `No` . Een component van het Gebied van de Tekst met de titel van `Email Address` gebruikt de volgende voorwaarde zodat het zichtbaar is als `Yes` wordt geselecteerd:

![ showhidCondition ](assets/showhidecondition.png)

In JavaScript gebruiken voorwaarden de waarde van de eigenschap Elementnaam om naar velden te verwijzen. In het vorige voorbeeld is de eigenschap Element Name van de component Radio Group ingesteld op `contact` . De volgende code is de equivalente JavaScript-code voor dat voorbeeld:

`((contact == "Yes"))`

**om een vormcomponent te tonen of te verbergen:**

1. Bewerk de specifieke formuliercomponent.

1. Selecteer **tonen/verbergen** om **uit te openen tonen/verberg de dialoog van Regels**:

   * In de eerste drop-down lijst selecteer of **tonen** of **Verbergen** om te specificeren of uw voorwaarden bepalen of om de component te tonen of te verbergen.

   * Selecteer in de vervolgkeuzelijst aan het einde van de bovenste regel:

      * **allen** - als alle voorwaarden waar moeten zijn om de component te tonen of te verbergen
      * **om het even welk** - als slechts één of meerdere voorwaarden moeten waar zijn om de component te tonen of te verbergen

   * Selecteer in de voorwaardelijn (een wordt standaard weergegeven) een component, operator en geef een waarde op.
   * Voeg meer voorwaarden toe indien nodig door **te klikken toevoegt Voorwaarde**.

   Bijvoorbeeld:

   ![ chlimage_1-9 ](assets/chlimage_1-9.png)

1. Klik **O.K.** om de definitie te bewaren.

1. Nadat u uw definitie bewaarde, geeft **regels** verbinding uit verschijnt naast **tonen/verbergen** optie in de eigenschappen van de vormcomponent. Klik deze verbinding om **te openen geef tonen/verberg Regels** dialoogdoos uit om veranderingen aan te brengen.

   Klik **O.K.** om alle veranderingen te bewaren.

   ![ chlimage_1-10 ](assets/chlimage_1-10.png)

   >[!CAUTION]
   >
   >De effecten van definities tonen/verbergen kunnen worden bekeken en getest:
   >
   >* in **wijze van de Voorproef** op het auteursmilieu (vereist een pagina herladen wanneer eerste omschakeling aan voorproef)
   >
   >* over de publicatieomgeving

#### Verwijzingen naar verbroken componenten afhandelen {#handling-broken-component-references}

Voorwaarden weergeven/verbergen gebruiken de waarde van de eigenschap Elementnaam om te verwijzen naar andere componenten in het formulier. De configuratie Tonen/Verbergen is ongeldig wanneer een van de voorwaarden verwijst naar een component die is verwijderd of waarvan de eigenschap Elementnaam is gewijzigd. Als dit gebeurt, moet u de voorwaarden handmatig bijwerken, anders treedt er een fout op wanneer het formulier wordt geladen.

Wanneer de configuratie Tonen/verbergen ongeldig is, wordt de configuratie alleen als JavaScript-code opgegeven. Bewerk de code om de problemen te verhelpen. De code gebruikt de eigenschap Element Name die oorspronkelijk is gebruikt om naar de componenten te verwijzen.

### Scripts ontwikkelen voor gebruik met Forms {#developing-scripts-for-use-with-forms}

Voor meer informatie over de API elementen die wanneer het schrijven van manuscripten kunnen worden gebruikt zien [ javadocs met betrekking tot vormen ](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/javadoc/com/day/cq/wcm/foundation/forms/package-summary.html).

U kunt dit gebruiken voor handelingen zoals het aanroepen van een service voordat het formulier wordt verzonden en het annuleren van de service als dit mislukt:

* Het type van de validatiebron definiëren
* Een script opnemen voor validatie:

   * Roep in uw JSP de webservice aan en maak een `com.day.cq.wcm.foundation.forms.ValidationInfo` -object met de foutberichten. Als er fouten optreden, worden de formuliergegevens niet gepost.
