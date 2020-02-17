---
title: Workflowmodellen maken
seo-title: Workflowmodellen maken
description: U maakt een workflowmodel om de reeks stappen te definiëren die worden uitgevoerd wanneer een gebruiker de workflow start.
seo-description: U maakt een workflowmodel om de reeks stappen te definiëren die worden uitgevoerd wanneer een gebruiker de workflow start.
uuid: 31071d3a-d6d5-4476-9ac0-7b335de406d9
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: c097b60f-bcdf-45de-babe-b4c2e2b746a1
docset: aem65
translation-type: tm+mt
source-git-commit: ec528e115f3e050e4124b5c232063721eaed8df5

---


# Workflowmodellen maken{#creating-workflow-models}

>[!CAUTION]
>
>Zie de documentatie [van](https://helpx.adobe.com/experience-manager/6-3/help/sites-developing/workflows-models.html) AEM 6.3 voor informatie over het gebruik van de klassieke interface.

U maakt een [workflowmodel](/help/sites-developing/workflows.md#model) om de reeks stappen te definiëren die worden uitgevoerd wanneer een gebruiker de workflow start. U kunt ook modeleigenschappen definiëren, zoals of de workflow van voorbijgaande aard is of meerdere bronnen gebruikt.

Wanneer een gebruiker een workflow start, wordt een instantie gestart; Dit is het corresponderende runtimemodel dat is gemaakt toen u uw wijzigingen [synchroniseerde](#sync-your-workflow-generate-a-runtime-model) .

## Nieuwe workflow maken {#creating-a-new-workflow}

Wanneer u voor het eerst een nieuw workflowmodel maakt, bevat dit model:

* De stappen, het Begin **van de** Stroom en het Eind **van de**Stroom.
Deze vertegenwoordigen het begin en einde van de workflow. Deze stappen zijn vereist en kunnen niet worden bewerkt/verwijderd.
* Een voorbeeldstap van de **Deelnemer** genoemd **Stap 1**.
Deze stap wordt gevormd om een het werkpunt aan de werkschemainitiatiefnemer toe te wijzen. Bewerk of verwijder deze stap en voeg desgewenst stappen toe.

Een nieuwe workflow maken met de editor:

1. Open de console **Workflowmodellen** ; via **Hulpmiddelen**, **Werkschema**, **Modellen** of, bijvoorbeeld: [https://localhost:4502/aem/workflow](https://localhost:4502/aem/workflow)
1. Selecteer **Maken** en vervolgens **Model** maken.
1. Het dialoogvenster **Werkstroommodel** toevoegen wordt weergegeven. Voer de **titel** en de **naam** (optioneel) in voordat u **Gereed** selecteert.
1. Het nieuwe model wordt vermeld in de console van de Modellen van het **Werkschema** .
1. Selecteer uw nieuwe workflow en gebruik vervolgens [**Bewerken **om deze te openen voor configuratie](#editinganexistingworkflow):   ![wf-01](assets/wf-01.png)

>[!NOTE]
>
>Als u met programmacode modellen maakt (met behulp van een crx-pakket), kunt u ook een submap maken binnen:
>
>`/var/workflow/models`

>Bijvoorbeeld, `/var/workflow/models/prototypes`
>Deze map kan vervolgens worden gebruikt voor het [beheer van de toegang tot de modellen in die map](/help/sites-administering/workflows-managing.md#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that).

## Een workflow bewerken {#editing-a-workflow}

U kunt elk bestaand workflowmodel bewerken in:

* [stappen](#addingasteptoamodel-) en de bijbehorende [parameters definiëren](#configuring-a-workflow-step)
* workfloweigenschappen configureren, inclusief [stadia](#configuring-workflow-stages-that-show-workflow-progress), [of de workflow van voorbijgaande aard](#creatingatransientworkflow-) is en/of meerdere bronnen [gebruikt](#configuring-a-workflow-for-multi-resource-support)

Het bewerken van een [**standaard- en/of verouderde **workflow](#editing-a-default-or-legacy-workflow-for-the-first-time)(out-of-the-box) heeft een extra stap om ervoor te zorgen dat er een[veilige kopie](/help/sites-developing/workflows-best-practices.md#locations-workflow-models)wordt gemaakt voordat de wijzigingen worden aangebracht.

Wanneer updates van uw workflow zijn voltooid, moet u **Synchroniseren** gebruiken om een runtimemodel **te** genereren. Zie [Uw workflow](#sync-your-workflow-generate-a-runtime-model) synchroniseren voor meer informatie.

### Uw workflow synchroniseren - Een runtimemodel genereren {#sync-your-workflow-generate-a-runtime-model}

**Met Sync** (rechts op de editor-werkbalk) wordt een [runtimemodel](/help/sites-developing/workflows.md#runtime-model)gegenereerd. Het runtimemodel is het model dat daadwerkelijk wordt gebruikt wanneer een gebruiker een workflow start. Als u uw wijzigingen niet **synchroniseert** , zijn de wijzigingen niet beschikbaar tijdens de runtime.

Wanneer u (of een andere gebruiker) wijzigingen aanbrengt in de workflow, moet u **Synchroniseren** gebruiken om een runtimemodel te genereren, zelfs wanneer afzonderlijke dialoogvensters (bijvoorbeeld voor stappen) hun eigen opslagopties hebben.

Wanneer de wijzigingen worden gesynchroniseerd met het (opgeslagen) runtimemodel, wordt in plaats daarvan **Gesynchroniseerd** weergegeven.

Sommige stappen hebben verplichte velden en/of ingebouwde validatie. Wanneer niet aan deze voorwaarden wordt voldaan, wordt een fout weergegeven wanneer u probeert het model te **synchroniseren** . Wanneer bijvoorbeeld geen deelnemer is gedefinieerd voor een stap **Deelnemer** :

![wf-21](assets/wf-21.png)

### Een standaardworkflow of oudere workflow voor het eerst bewerken {#editing-a-default-or-legacy-workflow-for-the-first-time}

Wanneer u een [standaardmodel en/of verouderd model](/help/sites-developing/workflows.md#workflow-types) opent voor bewerking:

* De browser Stappen is niet beschikbaar (links).
* De werkbalk bevat een handeling **Bewerken** (rechterkant).
* In eerste instantie worden het model en de eigenschappen ervan in de modus Alleen-lezen weergegeven als:
   * Standaardworkflows bevinden zich in `/libs`
   * Verouderde workflows bevinden zich in `/etc`het selecteren van **Bewerken** :
* neem een kopie van de workflow naar `/conf`
* stelt browser Stappen ter beschikking
* laten u toe om veranderingen aan te brengen

>[!NOTE]
Zie [Locations of Workflow Models](/help/sites-developing/workflows-best-practices.md#locations-workflow-models) voor meer informatie.

![wf-22](assets/wf-22.png)

### Een stap toevoegen aan een model {#adding-a-step-to-a-model}

U moet stappen aan uw model toevoegen om de uit te voeren activiteit te vertegenwoordigen - elke stap voert een specifieke activiteit uit. Een selectie van step-componenten is beschikbaar in een standaard AEM-instantie.

Wanneer u een model bewerkt, worden de beschikbare stappen weergegeven in de verschillende groepen van de **Stappen-browser**. Bijvoorbeeld:

![wf-10](assets/wf-10.png)

>[!NOTE]
Voor informatie over de primaire stapcomponenten die met AEM worden geïnstalleerd, zie de Verwijzing [van de Stappen van het](/help/sites-developing/workflows-step-ref.md)Werkschema.

Stappen toevoegen aan uw workflowmodel:

1. Open een bestaand workflowmodel voor bewerking. Selecteer in de **Workflows Model** -console het vereiste model en **bewerk** het vervolgens.
1. Open de browser Stappen; met **Zijpaneel** in-/uitschakelen, helemaal links op de bovenste werkbalk. Hier kunt u:

   * **Filter** voor specifieke stappen.
   * Gebruik de keuzelijst om de selectie te beperken tot een specifieke groep stappen.
   * Selecteer het pictogram Beschrijving tonen ![wf-stepinfo-icon](assets/wf-stepinfo-icon.png) om meer details over de aangewezen stap te tonen.
   ![wf-02](assets/wf-02.png)

1. Sleep de desbetreffende stap(en) naar de gewenste locatie in het model.

   Bijvoorbeeld een **deelnemersstap**.

   Zodra toegevoegd aan de stroom kunt u de stap [](#configuring-a-workflow-step)vormen.

   ![wf-03](assets/wf-03.png)

1. Voeg zo veel stappen, of andere updates toe, zoals vereist.

   Tijdens de uitvoering worden de stappen uitgevoerd in de volgorde waarin ze in het model worden weergegeven. Nadat u de onderdelen met stappen hebt toegevoegd, kunt u deze naar een andere locatie in het model slepen.

   U kunt ook bestaande stappen kopiëren, knippen, plakken, groeperen of verwijderen. zoals in de [paginaeditor.](/help/sites-authoring/editing-content.md)

   Gesplitste stappen kunnen ook worden samengevouwen/uitgevouwen met de werkbalkoptie: ![wf-collapse-toolbar-icon](assets/wf-collapseexpand-toolbar-icon.png)

1. Bevestig de wijzigingen met **Sync** (editor-werkbalk) om het runtimemodel te genereren.

   Zie [Uw workflow](#sync-your-workflow-generate-a-runtime-model) synchroniseren voor meer informatie.

### Een workflowstap configureren {#configuring-a-workflow-step}

U kunt het gedrag van een werkschemastap **vormen** en aanpassen gebruikend de dialoogvensters van de Eigenschappen **van de** Stap.

1. U opent als volgt het dialoogvenster **Step Properties** :

   * Klik/tik de * stap in het werkschemamodel en selecteer **vormen** van de componententoolbar.

   * Dubbelklik op de stap.
   >[!NOTE]
   Voor informatie over de primaire stapcomponenten die met AEM worden geïnstalleerd, zie de Verwijzing [van de Stappen van het](/help/sites-developing/workflows-step-ref.md)Werkschema.

1. Configureer desgewenst de **stapeigenschappen** ; Welke eigenschappen beschikbaar zijn, is afhankelijk van het type stap. Er kunnen ook verschillende tabbladen beschikbaar zijn. Bijvoorbeeld, de standaard Stap **van de** Deelnemer, in een nieuw werkschema als `Step 1`:

   ![wf-11](assets/wf-11.png)

1. Bevestig uw updates met de tik.
1. Bevestig de wijzigingen met **Sync** (editor-werkbalk) om het runtimemodel te genereren.

   Zie [Uw workflow](#sync-your-workflow-generate-a-runtime-model) synchroniseren voor meer informatie.

### Een tijdelijke workflow maken {#creating-a-transient-workflow}

U kunt een [tijdelijk](/help/sites-developing/workflows.md#transient-workflows) workflowmodel maken bij het maken van een nieuw model of door een bestaand model te bewerken:

1. Open het workflowmodel voor [bewerking](#editinganexistingworkflow).
1. Selecteer Eigenschappen **workflowmodel** op de werkbalk.
1. Activeer in het dialoogvenster de **tijdelijke workflow** (of deactiveer indien nodig):

   ![wf-07](assets/wf-07.png)

1. Bevestig de wijziging met **Opslaan en sluiten**. gevolgd door **Sync** (editor toolbar) om het runtimemodel te genereren.

   Zie [Uw workflow](#sync-your-workflow-generate-a-runtime-model) synchroniseren voor meer informatie.

>[!NOTE]
Wanneer u een workflow uitvoert in de modus [transient](/help/sites-developing/workflows.md#transient-workflows) , slaat AEM geen workflowhistorie op. Daarom wordt in de [tijdlijn](/help/sites-authoring/basic-handling.md#timeline) geen informatie over die workflow weergegeven. [](/help/sites-authoring/basic-handling.md#timeline)

## Workflowmodellen beschikbaar stellen in Touch UI {#classic2touchui}

Als een workflowmodel aanwezig is in de klassieke gebruikersinterface maar ontbreekt in het pop-upmenu voor selectie in de tijdlijntrack van de aanraakinterface, volgt u de configuratie om het beschikbaar te maken. De volgende stappen illustreren het gebruik van de workflowmodellen van AEM Assets, genaamd **[!UICONTROL Verzoek om activering]** en **[!UICONTROL Verzoek om deactivering]**.

1. Bevestig dat het model niet beschikbaar is in een interface met aanraakbediening. Een element openen met `/assets.html/content/dam` pad. Selecteer het element. Open **[!UICONTROL tijdlijn]** in linkerraster. Klik op Workflow **** starten. U ziet dat **[!UICONTROL Verzoek om activering]** en **[!UICONTROL Verzoek om deactivering]** niet aanwezig zijn in de pop-uplijst.
1. Klik op **[!UICONTROL Gereedschappen > Algemeen > Tags toevoegen]**. Selecteer **[!UICONTROL Workflow]**.
1. Klik op **[!UICONTROL Maken > Tag]** maken. Stel **[!UICONTROL Titel]** in op `DAM` en **[!UICONTROL Naam]** op `dam`. Klik op **[!UICONTROL Verzenden]**.

   ![Tag maken in workflowmodel](assets/workflow_create_tag.png)

1. Klik op **[!UICONTROL Gereedschappen > Workflow > Modellen]**. Selecteer **[!UICONTROL Verzoek om activering]** (of **[!UICONTROL Verzoek om deactivering]**). Click **[!UICONTROL Edit]**.
1. Ga in de assistent naar het tabblad **[!UICONTROL Pagina]** . Open **[!UICONTROL Pagina-eigenschappen]**.
1. Toevoegen `Workflow : DAM` aan veld **[!UICONTROL Tags/Trefwoorden]** . Click **[!UICONTROL OK]**. Click **[!UICONTROL Save]**.

   ![Pagina-eigenschappen van model bewerken](assets/workflow_model_edit_activation1.png)

### Een workflow configureren voor ondersteuning van meerdere bronnen {#configuring-a-workflow-for-multi-resource-support}

U kunt een workflowmodel configureren voor [Multi Resource Support](/help/sites-developing/workflows.md#multi-resource-support) bij het maken van een nieuw model of door een bestaand model te bewerken:

1. Open het workflowmodel voor [bewerking](#editinganexistingworkflow).
1. Selecteer Eigenschappen **workflowmodel** op de werkbalk.

1. Activeer in het dialoogvenster **Ondersteuning** voor meerdere bronnen (of deactiveer indien nodig):

   ![wf-08](assets/wf-08.png)

1. Bevestig de wijziging met **Opslaan en sluiten**. gevolgd door **Sync** (editor toolbar) om het runtimemodel te genereren.

   Zie [Uw workflow](#sync-your-workflow-generate-a-runtime-model) synchroniseren voor meer informatie.

### Werkstroomfasen configureren (die de voortgang van de workflow weergeven) {#configuring-workflow-stages-that-show-workflow-progress}

[Workflowfasen](/help/sites-developing/workflows.md#workflow-stages) helpen u de voortgang van een workflow bij het uitvoeren van taken te visualiseren.

>[!CAUTION]
Als werkstroomfasen zijn gedefinieerd in **Pagina-eigenschappen**, maar niet worden gebruikt voor werkstroomstappen, wordt op de voortgangsbalk geen voortgang weergegeven (ongeacht de huidige werkstroomstap).

De stadia die beschikbaar moeten zijn, worden gedefinieerd in de workflowmodellen; bestaande workflowmodellen kunnen worden bijgewerkt met werkgebieddefinities. U kunt een willekeurig aantal fasen voor het workflowmodel definiëren.

U definieert als volgt **fasen** voor uw workflow:

1. Open uw workflowmodel voor bewerking.
1. Selecteer Eigenschappen **workflowmodel** op de werkbalk. Open vervolgens het tabblad **Staven** .
1. Voeg de gewenste **stappen** toe (en plaats deze). U kunt een willekeurig aantal fasen voor het workflowmodel definiëren.

   Bijvoorbeeld:

   ![wf-08-1](assets/wf-08-1.png)

1. Klik op **Opslaan en sluiten** om de eigenschappen op te slaan.
1. Wijs een werkgebied aan elk van de stappen in het werkschemamodel toe. Bijvoorbeeld:

   ![wf-09](assets/wf-09.png)

   Een werkgebied kan aan meerdere stappen worden toegewezen. Bijvoorbeeld:

   | **Stap** | **Werkgebied** |
   |---|---|
   | Stap 1 | Maken |
   | Stap 2 | Maken |
   | Stap 3 | Controleren |
   | Stap 4 | Goedkeuren |
   | Stap 5 | Goedkeuren |
   | Stap 6 | Voltooid |

1. Bevestig de wijzigingen met **Sync** (editor-werkbalk) om het runtimemodel te genereren.

   Zie [Uw workflow](#sync-your-workflow-generate-a-runtime-model) synchroniseren voor meer informatie.

## Een workflowmodel exporteren in een pakket {#exporting-a-workflow-model-in-a-package}

Een workflowmodel exporteren in een pakket:

1. Een nieuw pakket maken met [Pakketbeheer](/help/sites-administering/package-manager.md#package-manager):

   1. Navigeer naar de Manager van het Pakket via **Hulpmiddelen**, **Plaatsing**, **Pakketten**.

   1. Klik op Pakket **** maken.
   1. Geef de **pakketnaam** op en geef desgewenst andere gegevens op.
   1. Click **OK**.

1. Klik op **Bewerken** op de werkbalk van het nieuwe pakket.

1. Open het tabblad **Filters** .

1. Selecteer Filter **** toevoegen en geef het pad van het *ontwerp* van het workflowmodel op:

   `/conf/global/settings/workflow/models/<*your-model-name*>`

   Klik op **Gereed**.

1. Selecteer Filter **** toevoegen en geef het pad van het workflowmodel voor de *runtime* op:

   `/var/workflow/models/<*your-model-name*>`

   Klik op **Gereed**.

1. Voeg extra filters toe voor om het even welke douanescripts die door uw model worden gebruikt.
1. Klik op **Opslaan** om uw filterdefinities te bevestigen.
1. Selecteer **Samenstellen** op de werkbalk van de pakketdefinitie.
1. Selecteer **Downloaden** op de pakketwerkbalk.

## Workflows gebruiken om formulierverzendingen te verwerken {#using-workflows-to-process-form-submissions}

U kunt een formulier configureren voor verwerking door de geselecteerde workflow. Wanneer gebruikers het formulier verzenden, wordt een nieuwe werkstroominstantie gemaakt met de gegevens van het verzenden van het formulier als lading.

U configureert als volgt de workflow die met het formulier moet worden gebruikt:

1. Maak een nieuwe pagina en open deze voor bewerking.
1. Voeg een **component Form** aan de pagina toe.
1. **Configureer** de **component Start** van formulier die op de pagina werd weergegeven.
1. Gebruik **Start Workflow** om de gewenste workflow te kiezen uit de beschikbare workflows:

   ![wf-12](assets/wf-12.png)

1. Bevestig de nieuwe formulierconfiguratie met de tik.

## Testworkflows {#testing-workflows}

Het is een goede praktijk wanneer het testen van een werkschema om een verscheidenheid van ladingstypes te gebruiken; met inbegrip van typen die verschillen van de soorten waarvoor zij is ontwikkeld. Als u bijvoorbeeld van plan bent om in uw workflow te werken met Elementen, test u deze door een Pagina in te stellen als een payload en controleer of er geen fouten optreden.

Test bijvoorbeeld de nieuwe workflow als volgt:

1. [Start uw workflowmodel](/help/sites-administering/workflows-starting.md) vanaf de console.
1. Bepaal de **Payload** en bevestig.

1. Voer de vereiste handelingen uit zodat de workflow doorgaat.
1. Controleer de logbestanden terwijl de workflow wordt uitgevoerd.

U kunt AEM ook configureren om **FOUTOPSPORING** -berichten weer te geven in de logbestanden. Zie [Logging](/help/sites-deploying/configure-logging.md) voor verdere informatie en wanneer de ontwikkeling wordt gebeëindigd, plaats het Niveau **van het** Logboek terug naar **Info**.

## Voorbeelden {#examples}

### Voorbeeld: Een (eenvoudige) workflow maken om een publicatieaanvraag te accepteren of af te wijzen {#example-creating-a-simple-workflow-to-accept-or-reject-a-request-for-publication}

In het volgende voorbeeld wordt een variatie in de `Publish Example` workflow gemaakt om enkele mogelijkheden voor het maken van een workflow te illustreren.

1. [Maak een nieuw workflowmodel](#creating-a-new-workflow).

   De nieuwe workflow bevat:

   * **Stroom starten**
   * `Step 1`
   * **Einde stroom**

1. Verwijderen `Step 1` (omdat dit het verkeerde staptype is voor dit voorbeeld):

   * Klik op de stap en selecteer **Verwijderen** in de werkbalk van de component. Bevestig de handeling.

1. Sleep vanuit de **workflowselectie** van de stappen browser een stap **voor de** deelnemer naar de workflow en plaats deze tussen **Stroombegin** en **Stroomeinde**.
1. U opent als volgt het dialoogvenster Eigenschappen:

   * Klik op de deelnemersstap en selecteer **Vorm** van de componententoolbar.
   * Dubbelklik op de stap voor deelnemers.

1. Voer op het tabblad **Algemeen** zowel `Validate Content` de **titel** als de **beschrijving** in.
1. Open het tabblad **Gebruiker/Groep** :

   * Activeer **Bericht per e-mail**.
   * Selecteer `Administrator` ( `admin`) voor het veld **Gebruiker/Groep** .
   >[!NOTE]
   De gegevens van [de mailservice en gebruikersaccount moeten geconfigureerd](/help/sites-administering/notification.md)zijn voor het verzenden van e-mails.

1. Bevestig de updates met de tik.

   U wordt teruggestuurd naar het overzicht van het workflowmodel, waar de naam van de deelnemer is gewijzigd in `Validate Content`.

1. Sleep een **of gesplitst** naar de werkstroom en plaats deze tussen `Validate Content` en **stroomeinde**.
1. Open de **of gesplitst** voor configuratie.
1. Configureren:

   * **Vaak**: Geef de naam van de splitsing op.
   * **Tak 1**: Selecteer **StandaardRoute**.

   * **Tak 2**: verzekert **StandaardRoute** niet wordt geselecteerd.

1. Bevestig uw updates voor de **OR-splitsing**.
1. Sleep een Stap **van de** Deelnemer aan de linkertak, open de eigenschappen, specificeer de volgende waarden, dan bevestig de veranderingen:

   * **Titel**: `Reject Publish Request`

   * **Gebruiker/groep**: bijvoorbeeld: `projects-administrators`

   * **Gebruikers via e-mail** op de hoogte stellen: Activeer deze functie om de gebruiker per e-mail op de hoogte te stellen.

1. Sleep een Stap **van het** Proces aan de juiste tak, open de eigenschappen, specificeer de volgende waarden, dan bevestig de veranderingen:

   * **Titel**: `Publish Page as Requested`

   * **Proces**: selecteren `Activate Page`. Dit proces publiceert de geselecteerde pagina naar de uitgeversinstanties.

1. Klik op **Synchroniseren** (editor-werkbalk) om het runtimemodel te genereren.

   Zie [Uw workflow](#sync-your-workflow-generate-a-runtime-model) synchroniseren voor meer informatie.

   Uw nieuwe workflowmodel ziet er als volgt uit:

   ![wf-13](assets/wf-13.png)

1. Pas deze workflow toe op de pagina, zodat gebruikers die de stap Inhoud **** valideren **voltooien** , kunnen kiezen of ze de pagina willen **publiceren zoals gevraagd** of de publicatieaanvraag **willen** afwijzen.

   ![chlimage_1-72](assets/chlimage_1-72.png)

### Voorbeeld: Een regel definiëren voor een OR-splitsing met behulp van een ECMA-script {#defineruleecmascript}

**OF Met de stappen Splitsen** kunt u voorwaardelijke verwerkingspaden in uw workflow introduceren.

Ga als volgt te werk om een OR-regel te definiëren:

1. Maak twee scripts en sla deze op in de repository, bijvoorbeeld onder:

   `/apps/myapp/workflow/scripts`

   >[!NOTE]
   De scripts moeten een [functie hebben `check()`](#function-check) die een Booleaanse waarde retourneert.

1. Bewerk de workflow en voeg de **OR-splitsing** toe aan het model.
1. Bewerk de eigenschappen van **vertakking 1** van de **OR-splitsing**:

   * Bepaal dit als **StandaardRoute** door de **Waarde** te plaatsen aan `true`.

   * Als **Regel**, plaats de weg aan het manuscript. Bijvoorbeeld:
      `/apps/myapp/workflow/scripts/myscript1.ecma`
   >[!NOTE]
   U kunt de vertakkingsvolgorde desgewenst wijzigen.

1. Bewerk de eigenschappen van **vertakking 2** van de **OR-splitsing**.

   * Als **Regel**, plaats de weg aan het andere manuscript. Bijvoorbeeld:
      `/apps/myapp/workflow/scripts/myscript2.ecma`

1. Stel de eigenschappen van de afzonderlijke stappen in elke vertakking in. Controleer of de **gebruiker/groep** is ingesteld.
1. Klik op **Synchroniseren** (editor-werkbalk) om uw wijzigingen in het runtimemodel voort te zetten.

   Zie [Uw workflow](#sync-your-workflow-generate-a-runtime-model) synchroniseren voor meer informatie.

#### Functie check() {#function-check}

>[!NOTE]
Zie [ECMAScript](/help/sites-developing/workflows-customizing-extending.md#using-ecmascript)gebruiken.

Het volgende voorbeeldscript retourneert `true` als het knooppunt zich onder een `JCR_PATH` locatie bevindt `/content/we-retail/us/en`:

```
function check() {
    if (workflowData.getPayloadType() == "JCR_PATH") {
      var path = workflowData.getPayload().toString();
      var node = jcrSession.getItem(path);

      if (node.getPath().indexOf("/content/we-retail/us/en") >= 0) {
       return true;
      } else {
       return false;
      }
     } else {
      return false;
     }
}
```

### Voorbeeld: Aangepast verzoek om activering {#example-customized-request-for-activation}

U kunt om het even welke uit-van-de-doos workflows aanpassen. Voor aangepast gedrag bedekt u de details van de juiste workflow.

Bijvoorbeeld **Verzoek om activering**. Deze workflow wordt gebruikt voor het publiceren van pagina&#39;s binnen **sites** en wordt automatisch geactiveerd wanneer een auteur van inhoud niet de juiste replicatierechten heeft. Zie [Paginaontwerp aanpassen - De activeringsaanvraag](/help/sites-developing/customizing-page-authoring-touch.md#customizing-the-request-for-activation-workflow) aanpassen voor meer informatie.
