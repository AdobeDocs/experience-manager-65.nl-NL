---
title: Workflows ontwikkelen en uitbreiden
description: AEM biedt verschillende gereedschappen en bronnen voor het maken van workflowmodellen, het ontwikkelen van workflowstappen en voor programmatisch communiceren met workflows.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: 041b1767-8b6c-4887-a70d-abc96a116976
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '1460'
ht-degree: 0%

---


# Workflows ontwikkelen en uitbreiden{#developing-and-extending-workflows}

AEM biedt verschillende gereedschappen en bronnen voor het maken van workflowmodellen, het ontwikkelen van workflowstappen en voor programmatisch communiceren met workflows.

Met workflows kunt u processen automatiseren voor het beheer van bronnen en het publiceren van inhoud in uw AEM. Workflows bestaan uit een reeks stappen waarbij elke stap een afzonderlijke taak uitvoert. U kunt logica en runtime gegevens gebruiken om te bepalen wanneer een proces kan worden voortgezet en de volgende stap te selecteren uit een van de meerdere mogelijke stappen.

Zo bevatten bedrijfsprocessen voor het maken en publiceren van webpagina&#39;s goedkeurings- en aftekeningstaken van verschillende deelnemers. Deze processen kunnen worden gemodelleerd gebruikend AEM werkschema&#39;s en op specifieke inhoud worden toegepast.

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
>* Deelnemend aan werkschema&#39;s, zie [ Gebruikend Werkschema&#39;s ](/help/sites-authoring/workflows.md).
>* Het beheren van werkschema&#39;s en werkschemainstanties, zie [ het Beheer Werkschema&#39;s ](/help/sites-administering/workflows.md).
>* Voor een Communautair Artikel van begin tot eind, zie [ Wijzigend Digitale Assets gebruikend de Workflows van Adobe Experience Manager.](https://experienceleague.adobe.com/docs/experience-manager-65/assets/using/assets-workflow.html)
>* Zie [ vragen de AEM Deskundigen Webinar op Werkschema&#39;s ](https://communities.adobeconnect.com/p5s33iburd54/).
>* De veranderingen in de plaatsen van informatie zien &lbrace;de Herstructurering van de Bewaarplaats in AEM 6.5 [&#128279;](/help/sites-deploying/repository-restructuring.md) en [ Beste praktijken van het Werkschema - Punten ](/help/sites-developing/workflows-best-practices.md#locations).
>

## Model {#model}

Een `WorkflowModel` vertegenwoordigt een definitie (model) van een workflow. Het bestaat uit `WorkflowNodes` en `WorkflowTransitions` . De overgangen verbinden de knopen en bepalen de *stroom*. Het model heeft altijd een beginknooppunt en een eindknooppunt.

### Runtimemodel {#runtime-model}

Workflowmodellen hebben een versienummer. Wanneer u een werkstroominstantie uitvoert, wordt het runtimemodel van de werkstroom gebruikt en bewaard, zoals beschikbaar op het moment dat de werkstroom werd gestart.

Een runtime model wordt [ geproduceerd wanneer **Synchronisatie** in de redacteur van het werkschemamodel ](/help/sites-developing/workflows-models.md#sync-your-workflow-generate-a-runtime-model) wordt teweeggebracht.

Bewerk aan het werkschemamodel dat voorkomt, of runtime modellen die, of allebei worden geproduceerd, *nadat* de specifieke instantie was begonnen niet op die instantie wordt toegepast.

>[!CAUTION]
>
>De uitgevoerde stappen worden bepaald door het [ runtime model ](/help/sites-developing/workflows-models.md#sync-your-workflow-generate-a-runtime-model), dat tegelijkertijd wordt geproduceerd de **actie van de Synchronisatie** in de werkschemamodeleditor wordt teweeggebracht.
>
>Als het werkschemamodel na dit punt in tijd (zonder **Synchronisatie** wordt veranderd die) wordt teweeggebracht, dan wijst de runtime instantie niet op die veranderingen. Alleen runtimemodellen die na de update worden gegenereerd, weerspiegelen de wijzigingen. De uitzonderingen zijn de onderliggende ECMA-scripts, die slechts eenmaal worden bijgehouden zodat deze wijzigingen worden doorgevoerd.

### Stap {#step}

Elke stap voert een afzonderlijke taak uit. Er zijn verschillende typen workflowstappen:

* Deelnemer (Gebruiker/Groep): Met deze stappen wordt een tijdelijk item gegenereerd en toegewezen aan een gebruiker of groep. Een gebruiker moet het het werkpunt voltooien om de werkschema vooruit te gaan.
* Proces (script, Java™ methode call): deze stappen worden automatisch uitgevoerd door het systeem. Een ECMA- of Java™-klasse implementeert de stap. De diensten kunnen worden ontwikkeld om aan speciale werkschemagebeurtenissen te luisteren en taken volgens de bedrijfslogica uit te voeren.
* Container (subworkflow): dit type stap start een ander workflowmodel.
* OF Splitsen/samenvoegen: gebruik logica om te beslissen welke stap u vervolgens in de workflow wilt uitvoeren.
* EN Splitsen/samenvoegen: hiermee kunnen meerdere stappen tegelijkertijd worden uitgevoerd.

Alle stappen delen de volgende algemene eigenschappen: `Autoadvance` en `Timeout` waarschuwingen (scriptbaar).

### Overgang {#transition}

Een `WorkflowTransition` vertegenwoordigt een overgang tussen twee `WorkflowNodes` van een `WorkflowModel` .

* De koppeling tussen twee opeenvolgende stappen wordt gedefinieerd.
* Het is mogelijk regels toe te passen.

### WorkItem {#workitem}

Een `WorkItem` is de eenheid die wordt doorgegeven via een `Workflow` -instantie van een `WorkflowModel` . Deze bevat de `WorkflowData` die de instantie gebruikt en een verwijzing naar `WorkflowNode` die de onderliggende werkstroomstap beschrijft.

* Het wordt gebruikt om de taak te identificeren en in respectieve inbox gezet.
* Een workflowinstantie kan een of meer `WorkItems` tegelijk hebben (afhankelijk van het workflowmodel).
* De `WorkItem` verwijst naar de werkstroominstantie.
* In de repository wordt `WorkItem` opgeslagen onder de werkstroominstantie.

### Payload {#payload}

Verwijst naar de bron die door een werkstroom moet worden geavanceerd.

De implementatie van de payload verwijst naar een bron in de opslagplaats (via pad, UUID of URL) of naar een geserialiseerd Java™-object. Verwijzen naar een bron in de opslagplaats is flexibel en productief. Het knooppunt waarnaar wordt verwezen, kan bijvoorbeeld worden weergegeven als een formulier.

### Levenscyclus {#lifecycle}

Wordt gemaakt bij het starten van een nieuwe workflow (door het desbetreffende workflowmodel te kiezen en de lading te definiëren) en eindigt wanneer het eindknooppunt wordt verwerkt.

De volgende acties zijn mogelijk op een werkstroominstantie:

* Beëindigen
* Onderbreken
* Hervatten
* Opnieuw starten

Voltooide en beëindigde exemplaren worden gearchiveerd.

### Inbox {#inbox}

Elke gebruikersaccount heeft zijn eigen workflow-inbox waarin de toegewezen `WorkItems` toegankelijk zijn.

`WorkItems` wordt toegewezen aan of de gebruikersrekening direct of aan de groep waartot zij behoren.

### Workflowtypen {#workflow-types}

Er zijn verschillende typen werkstromen die worden aangegeven in de console Workflowmodellen:

![ wf-upgrade-03 ](assets/wf-upgraded-03.png)

* **Gebrek**

  Dit zijn de werkstromen buiten de doos inbegrepen in een standaard AEM instantie.

* Aangepaste workflows (geen indicator in de console)

  Deze workflows zijn gemaakt als nieuwe workflows of als out-of-the-box workflows die zijn bedekt met aanpassingen.

* **Verouderd**

  Workflows die zijn gemaakt in een eerdere versie van AEM. Deze workflows kunnen tijdens een upgrade behouden blijven of worden geëxporteerd als een workflowpakket van de vorige versie en vervolgens worden geïmporteerd in de nieuwe versie.

### Tijdelijke workflows {#transient-workflows}

Standaardworkflows slaan runtime (geschiedenis)-informatie op tijdens het uitvoeren. U kunt een werkschemamodel ook bepalen als **Overgangs** om dergelijke geschiedenis te vermijden die wordt gepresteerd. Deze workflow wordt gebruikt voor het afstemmen van prestaties, omdat hierdoor tijd en bronnen worden bespaard die worden gebruikt voor het blijvend maken van de informatie.

U kunt tijdelijke workflows gebruiken voor workflows die:

* worden vaak uitgevoerd.
* hebt de workflowgeschiedenis niet nodig.

Er zijn tijdelijke workflows geïntroduceerd voor het laden van vele elementen, waarbij de elementgegevens belangrijk zijn, maar niet de runtimegeschiedenis van de workflow.

>[!NOTE]
>
>Zie [ Creërend een Voorbijgaande Werkschema ](/help/sites-developing/workflows-models.md#creating-a-transient-workflow) voor verdere details.

>[!CAUTION]
>
>Wanneer een workflowmodel als tijdelijk wordt gemarkeerd, zijn er een paar scenario&#39;s wanneer de runtime-informatie moet worden voortgezet:
>
>* Het ladingstype (bijvoorbeeld video) vereist externe stappen voor verwerking; in dergelijke gevallen is de runtime geschiedenis nodig voor statusbevestiging.
>* Het werkschema gaat een **EN Gesplitst** in. In dergelijke gevallen is de runtimegeschiedenis nodig voor statusbevestiging.
>* Wanneer de tijdelijke workflow een stap voor deelnemers activeert, verandert deze modus bij uitvoering in een stap zonder overgang. Aangezien de taak aan een persoon wordt overgegaan, moet de geschiedenis worden voortgeduurd.
>

>[!CAUTION]
>
>Binnen een transient werkschema, zou u a **niet moeten gebruiken gaan**.
>
>De reden is omdat de **Goto Stap** tot een slingerbaan leidt om het werkschema op het `goto` punt voort te zetten. Het verslaat het doel om het werkschema transient te maken, en produceert een fout in het logboekdossier.
>
>Het gebruik **OF Splitst** om keuzen binnen een transient werkschema te maken.

>[!NOTE]
>
>Zie [ Beste praktijken voor Assets ](/help/assets/performance-tuning-guidelines.md#transient-workflows) voor verdere informatie over hoe de Transiente Workflows de prestaties van Activa beïnvloeden.

### Ondersteuning voor meerdere bronnen {#multi-resource-support}

Het activeren van **MultiSteun van het Middel** voor uw werkschemamodel betekent dat één enkele werkschemainstantie is begonnen zelfs wanneer u veelvoudige middelen selecteert. Elk object wordt als een pakket toegevoegd.

Als **de MultiSteun van het Middel** niet voor uw werkschemamodel wordt geactiveerd en de veelvoudige middelen worden geselecteerd, dan is een individuele werkschemainstantie begonnen voor elk middel.

>[!NOTE]
>
>Zie [ Vormend een Werkschema voor de Steun van het Meerdere Middel ](/help/sites-developing/workflows-models.md#configuring-a-workflow-for-multi-resource-support) voor verdere details.

### Werkstroomfasen {#workflow-stages}

Workflowfasen helpen u de voortgang van een workflow bij het uitvoeren van taken zichtbaar te maken. Ze kunnen worden gebruikt om een overzicht te geven van de mate waarin de workflow wordt verwerkt. Wanneer de werkschemalooppas, de gebruiker de vooruitgang kan bekijken die door **wordt beschreven Stadium** (in tegenstelling tot individuele stap).

Aangezien de namen van de afzonderlijke stappen specifiek en technisch kunnen zijn, kunnen de werkgebiednamen worden gedefinieerd om een conceptuele weergave van de voortgang van de workflow te bieden.

Bijvoorbeeld voor een workflow met zes stappen en vier stappen:

1. U kunt [ de Staven van het Werkschema (die de Voortgang van het Werkschema tonen) vormen en dan het aangewezen stadium aan elke stap in uw werkschema toewijzen ](/help/sites-developing/workflows-models.md#configuring-workflow-stages-that-show-workflow-progress):

   * U kunt meerdere werkgebiednamen maken.
   * Vervolgens wordt aan elke stap een afzonderlijke werkgebiednaam toegewezen (een werkgebiednaam kan aan een of meer stappen worden toegewezen).

   | **Naam van de Stap** | **Stadium (die aan de stap wordt toegewezen)** |
   |---|---|
   | Stap 1 | Maken |
   | Stap 2 | Maken |
   | Stap 3 | Controleren |
   | Stap 4 | Goedkeuren |
   | Stap 5 | Voltooid |
   | Stap 6 | Voltooid |

1. Wanneer de workflow wordt uitgevoerd, kan de gebruiker de voortgang bekijken op basis van de namen van het werkgebied (in plaats van de namen van de stappen). De werkschemavooruitgang wordt getoond in het [ lusje van de INFO van de WORKFLOW van het venster van taakdetails van het werkschemapunt ](/help/sites-authoring/workflows-participating.md#opening-a-workflow-item-to-view-details-and-take-actions) dat in [ wordt vermeld Inbox ](/help/sites-authoring/inbox.md).

### Workflows en Forms {#workflows-and-forms}

Workflows worden doorgaans gebruikt om formulierverzendingen in AEM te verwerken. Het kan met de [ kerncomponenten zijn componenten ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/forms/form-container.html) beschikbaar in een standaard AEM instantie, of met de [ oplossing van AEM Forms ](/help/forms/using/aem-forms-workflow.md).

Bij het maken van een formulier kan het verzenden van het formulier eenvoudig worden gekoppeld aan een workflowmodel. Bijvoorbeeld om de inhoud op een bepaalde locatie van de gegevensopslagruimte op te slaan of om een gebruiker op de hoogte te stellen van het verzenden van het formulier en de inhoud ervan.

### Workflows en vertaling {#workflows-and-translation}

De werkschema&#39;s zijn ook een deel van het [ Vertaal ](/help/sites-administering/translation.md) proces.
