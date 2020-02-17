---
title: Workflows ontwikkelen en uitbreiden
seo-title: Workflows ontwikkelen en uitbreiden
description: AEM verstrekt verscheidene hulpmiddelen en middelen voor het creëren van werkschemamodellen, het ontwikkelen van werkschemastappen en voor programmatically het in wisselwerking staan met werkschema's
seo-description: AEM verstrekt verscheidene hulpmiddelen en middelen voor het creëren van werkschemamodellen, het ontwikkelen van werkschemastappen en voor programmatically het in wisselwerking staan met werkschema's
uuid: 5a857589-3b13-4519-bda2-b1dab6005550
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: 8954e3df-3afa-4d53-a7e1-255f3b8f499f
translation-type: tm+mt
source-git-commit: 2fc35bfd93585a586cb1d4e3299261611db49ba6

---


# Workflows ontwikkelen en uitbreiden{#developing-and-extending-workflows}

AEM verstrekt verscheidene hulpmiddelen en middelen voor het creëren van werkschemamodellen, het ontwikkelen van werkschemastappen, en voor programmatically het in wisselwerking staan met werkschema&#39;s.

Met workflows kunt u processen automatiseren voor het beheer van bronnen en het publiceren van inhoud in uw AEM-omgeving. Workflows bestaan uit een reeks stappen waarbij elke stap een afzonderlijke taak uitvoert. U kunt logica en runtime gegevens gebruiken om besluiten te nemen over wanneer een proces kan verdergaan en de volgende stap van één van veelvoudige mogelijke stappen selecteren.

Zo bevatten bedrijfsprocessen voor het maken en publiceren van webpagina&#39;s goedkeurings- en aftekeningstaken van verschillende deelnemers. Deze processen kunnen worden gemodelleerd met AEM-workflows en worden toegepast op specifieke inhoud.

De belangrijkste aspecten komen hieronder aan de orde, terwijl op de volgende pagina&#39;s nadere bijzonderheden worden gegeven:

* [Workflowmodellen maken](/help/sites-developing/workflows-models.md)
* [Uitbreiding van workflowfunctionaliteit](/help/sites-developing/workflows-customizing-extending.md)
* [Programmatische interactie met Workflows](/help/sites-developing/workflows-program-interaction.md)
* [Referentie workflowstap](/help/sites-developing/workflows-step-ref.md)
* [Referentie workflowproces](/help/sites-developing/workflows-process-ref.md)
* [Best practices voor workflow](/help/sites-developing/workflows-best-practices.md)

>[!NOTE]
>
>Voor informatie over:
>
>* Als u deelneemt aan workflows, raadpleegt u [Workflows](/help/sites-authoring/workflows.md)gebruiken.
>* Zie Workflows [beheren voor het beheren van workflows](/help/sites-administering/workflows.md).
>* Zie Digitale elementen [wijzigen met Adobe Experience Manager Workflows voor een end-to-end Community-artikel.](https://helpx.adobe.com/experience-manager/using/modify_asset_workflow.html)
>* Zie [Vraag het aan de deskundigen van AEM Webinar over Werkschema](https://bit.ly/ATACE218).
>* Zie Een aangepaste stap [](https://helpx.adobe.com/experience-manager/using/dynamic-steps-aem63.html)voor Adobe Experience Manager 6.3 voor een end-to-end Community-artikel.
>* Wijzigingen in de locatie van informatie zie Herstructurering van [bewaarplaats in AEM 6.5](/help/sites-deploying/repository-restructuring.md) en [Workflowbeste praktijken - Locaties](/help/sites-developing/workflows-best-practices.md#locations).
>



## Model {#model}

A `WorkflowModel` staat voor een definitie (model) van een workflow. Het is gemaakt van `WorkflowNodes` en `WorkflowTransitions`. De overgangen verbinden de knopen en bepalen de *stroom*. Het model heeft altijd een beginknooppunt en een eindknooppunt.

### Runtimemodel {#runtime-model}

Workflowmodellen hebben een versienummer. Wanneer u een workflowinstantie uitvoert, wordt het runtimemodel van de workflow gebruikt (en bewaard) (zoals beschikbaar op het moment dat de workflow werd gestart).

Er wordt een runtimemodel [gegenereerd wanneer **Sync** wordt geactiveerd in de werkstroommodeleditor](/help/sites-developing/workflows-models.md#sync-your-workflow-generate-a-runtime-model).

Bewerkingen aan het workflowmodel dat optreedt en/of runtimemodellen die worden gegenereerd *nadat* de specifieke instantie is gestart, worden niet op die instantie toegepast.

>[!CAUTION]
>
>De uitgevoerde stappen zijn die zoals die door het [runtime model](/help/sites-developing/workflows-models.md#sync-your-workflow-generate-a-runtime-model)worden bepaald; dit wordt gegenereerd op het moment dat de handeling **Sync** wordt geactiveerd in de werkstroommodeleditor.
>
>Als het workflowmodel na dit tijdstip wordt gewijzigd (zonder dat **Sync** wordt geactiveerd), worden deze wijzigingen niet doorgevoerd in de runtime-instantie. Alleen runtimemodellen die na de update worden gegenereerd, weerspiegelen de wijzigingen. Uitzonderingen zijn de onderliggende ECMA-scripts, die slechts eenmaal worden bijgehouden en er worden wijzigingen in aangebracht.

### Step {#step}

Elke stap voert een afzonderlijke taak uit. Er zijn verschillende typen workflowstappen:

* Deelnemer (gebruiker/groep): Met deze stappen wordt een tijdelijk item gegenereerd en toegewezen aan een gebruiker of groep. Een gebruiker moet het het werkpunt voltooien om de werkschema vooruit te gaan.
* Proces (script, Java-methodeaanroep): Deze stappen worden automatisch uitgevoerd door het systeem. Een ECMA- of Java-klasse implementeert de stap. De diensten kunnen worden ontwikkeld om aan speciale werkschemagebeurtenissen te luisteren en taken volgens de bedrijfslogica uit te voeren.
* Container (subworkflow): Met dit type stap wordt een ander workflowmodel gestart.
* OF Splitsen/verbinden: Gebruik logica om te beslissen welke stap u vervolgens in de workflow wilt uitvoeren.
* EN Splitsen/verbinden: Hiermee kunnen meerdere stappen tegelijkertijd worden uitgevoerd.

Alle stappen delen de volgende algemene eigenschappen: `Autoadvance` en `Timeout` waarschuwingen (scriptbaar).

### Overgang {#transition}

A `WorkflowTransition` staat voor een overgang tussen twee `WorkflowNodes` van een `WorkflowModel`.

* De koppeling tussen twee opeenvolgende stappen wordt gedefinieerd.
* Het is mogelijk regels toe te passen.

### WorkItem {#workitem}

A `WorkItem` is de eenheid die door een `Workflow` geval van een `WorkflowModel`. wordt overgegaan. Het bevat de code `WorkflowData` waarop de instantie reageert en een verwijzing naar de `WorkflowNode` onderliggende werkstroomstap.

* Het wordt gebruikt om de taak te identificeren en in respectieve inbox gezet.
* Een workflowinstantie kan een of meer `WorkItems` tegelijk hebben (afhankelijk van het workflowmodel).
* De `WorkItem` verwijzing naar de werkstroominstantie.
* In de opslagplaats `WorkItem` wordt het opgeslagen onder de werkstroominstantie.

### Payload {#payload}

Verwijst naar de bron die door een werkstroom moet worden geavanceerd.

De nuttige ladingimplementatie verwijst naar een middel in de bewaarplaats (door weg, UUID of URL) of door een geserialiseerd voorwerp van Java. Verwijzen naar een bron in de gegevensopslagplaats is zeer flexibel en in combinatie met zeer productief leveren; Het knooppunt waarnaar wordt verwezen, kan bijvoorbeeld worden weergegeven als een formulier.

### Levenscyclus {#lifecycle}

Wordt gemaakt bij het starten van een nieuwe workflow (door het desbetreffende workflowmodel te kiezen en de lading te definiëren) en eindigt wanneer het eindknooppunt wordt verwerkt.

De volgende acties zijn mogelijk op een werkstroominstantie:

* Beëindigen
* Onderbreken
* Hervatten
* Opnieuw starten

Voltooide en beëindigde exemplaren worden gearchiveerd.

### Inbox {#inbox}

Elke gebruikersaccount heeft een eigen workflow-inbox waarin de toegewezen gebruikersaccount toegankelijk `WorkItems` is.

De gegevens `WorkItems` worden rechtstreeks toegewezen aan de gebruikersaccount of aan de groep waartoe ze behoren.

### Workflowtypen {#workflow-types}

Er zijn verschillende typen werkstromen die worden aangegeven in de console Workflowmodellen:

![wf-upgrade-03](assets/wf-upgraded-03.png)

* **Standaard**

   Dit zijn de werkstromen buiten de doos inbegrepen in een standaardAEM instantie.

* Aangepaste workflows (geen indicator in de console)

   Dit zijn werkstromen die als nieuw, of van uit-van-de-dooswerkschema&#39;s zijn gecreeerd die met aanpassingen zijn bedekt.

* **Verouderd**

   Workflows die zijn gemaakt in een eerdere versie van AEM. Deze kunnen tijdens een upgrade behouden blijven of worden geëxporteerd als een workflowpakket van de vorige versie en vervolgens worden geïmporteerd in de nieuwe versie.

### Tijdelijke workflows {#transient-workflows}

Standaardworkflows slaan runtime (geschiedenis)-informatie op tijdens de uitvoering ervan. U kunt een workflowmodel ook definiëren als **transient** om te voorkomen dat een dergelijke geschiedenis zich blijft voordoen. Dit wordt gebruikt voor prestaties het stemmen aangezien het bespaart/vermijdt de tijd/de middelen die voor het voortbestaan van de informatie worden gebruikt.

U kunt tijdelijke workflows gebruiken voor alle workflows die:

* worden vaak uitgevoerd.
* hebt de workflowgeschiedenis niet nodig.

Er zijn tijdelijke workflows geïntroduceerd voor het laden van een groot aantal elementen, waarbij de elementgegevens belangrijk zijn, maar niet de runtimegeschiedenis van de workflow.

>[!NOTE]
>
>Zie [Een tijdelijk werkschema](/help/sites-developing/workflows-models.md#creating-a-transient-workflow) maken voor meer informatie.

>[!CAUTION]
>
>Wanneer een workflowmodel als tijdelijk is gemarkeerd, zijn er een aantal scenario&#39;s waarin de runtimegegevens nog steeds worden voortgezet:
>
>* Het ladingstype (bijvoorbeeld video) vereist externe stappen voor verwerking; in dergelijke gevallen is de runtimegeschiedenis nodig om de status te bevestigen.
>* De werkstroom voert een **EN-splitsing** in. in dergelijke gevallen is de runtimegeschiedenis nodig om de status te bevestigen.
>* Wanneer de tijdelijke werkstroom een deelnemersstap ingaat, verandert deze modus (bij uitvoering) in een niet-overgangswerkstroom. aangezien de taak aan een persoon wordt doorgegeven , moet de geschiedenis worden voortgezet
>



>[!CAUTION]
>
>Binnen een transiënte workflow mag u geen **Ga naar-stap** gebruiken.
>
>Dit is aangezien de Stap **van de** Ga een slingerbaan creeert om het werkschema op het `goto` punt voort te zetten. Hierdoor wordt het doel van het tijdelijk maken van de workflow overgeslagen en wordt een fout in het logbestand gegenereerd.
>
>Als u beslissingen wilt nemen in een tijdelijke workflow, kunt u de optie **OF splitsen** gebruiken.

>[!NOTE]
>
>Zie [Beste praktijken voor Activa](/help/assets/performance-tuning-guidelines.md#transient-workflows) voor meer informatie over hoe de Transiente Workflows de prestaties van Activa beïnvloeden.

### Ondersteuning voor meerdere bronnen {#multi-resource-support}

Als u **Multi Resource Support** voor uw workflowmodel activeert, wordt één workflowinstantie gestart, zelfs als u meerdere bronnen selecteert. deze zullen als pakket worden bijgevoegd .

Als **MultiResource Support** niet is geactiveerd voor uw workflowmodel en er meerdere bronnen zijn geselecteerd, wordt voor elke bron een afzonderlijke workflowinstantie gestart.

>[!NOTE]
>
>Zie Een workflow [configureren voor ondersteuning](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) van meerdere bronnen voor meer informatie.

### Werkstroomfasen {#workflow-stages}

Workflowfasen helpen u de voortgang van een workflow bij het uitvoeren van taken zichtbaar te maken. Deze kunnen worden gebruikt om een overzicht te geven van de mate waarin de workflow wordt verwerkt, zoals wanneer de workflow wordt uitgevoerd, de gebruiker de voortgang kan bekijken die in het **werkgebied** wordt beschreven (in tegenstelling tot een afzonderlijke stap).

Aangezien de namen van de afzonderlijke stappen specifiek en technisch kunnen zijn, kunnen de werkgebiednamen worden gedefinieerd om een conceptuele weergave van de voortgang van de workflow te bieden.

Bijvoorbeeld voor een workflow met zes stappen en vier stappen:

1. U kunt werkstroomfasen [configureren (die de voortgang van het werkschema weergeven) en vervolgens het juiste werkgebied toewijzen aan elke stap in uw werkstroom](/help/sites-developing/workflows-models.md#configuring-workflow-stages-that-show-workflow-progress):

   * U kunt meerdere werkgebiednamen maken.
   * Vervolgens wordt aan elke stap een afzonderlijke werkgebiednaam toegewezen (een werkgebiednaam kan aan een of meer stappen worden toegewezen).
   | **Naam stap** | **Werkgebied (toegewezen aan de stap)** |
   |---|---|
   | Stap 1 | Maken |
   | Stap 2 | Maken |
   | Stap 3 | Controleren |
   | Stap 4 | Goedkeuren |
   | Stap 5 | Voltooid |
   | Stap 6 | Voltooid |

1. Wanneer de workflow wordt uitgevoerd, kan de gebruiker de voortgang bekijken op basis van de namen van het werkgebied (in plaats van de namen van de stappen). De voortgang van de workflow wordt weergegeven op het tabblad [WORKFLOW INFO van het venster met taakdetails van het werkitem](/help/sites-authoring/workflows-participating.md#opening-a-workflow-item-to-view-details-and-take-actions) dat in het [Postvak](/help/sites-authoring/inbox.md)wordt weergegeven.

### Workflows en formulieren {#workflows-and-forms}

Workflows worden doorgaans gebruikt om formulierverzendingen in AEM te verwerken. Dit kan met de [kerncomponenten van componenten](https://helpx.adobe.com/experience-manager/core-components/using/form-container.html) beschikbaar in een standaardAEM instantie, of met de oplossing [](/help/forms/using/aem-forms-workflow.md)van Vormen AEM zijn.

Bij het maken van een nieuw formulier kan het verzenden van het formulier eenvoudig worden gekoppeld aan een workflowmodel. bijvoorbeeld om de inhoud op een bepaalde locatie van de gegevensopslagruimte op te slaan of om een gebruiker op de hoogte te stellen van de verzending van het formulier en de inhoud ervan.

### Workflows en vertaling {#workflows-and-translation}

Workflows zijn ook een integraal onderdeel van het [vertaalproces](/help/sites-administering/translation.md) .
