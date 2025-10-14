---
title: De doeltreffendheid en de conversie van formulieren meten en verbeteren
description: AEM Forms is geïntegreerd met Adobe Target- en Adobe Analytics-oplossingen waarmee u de prestaties en conversiesnelheid van uw formulieren kunt meten en verbeteren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
docset: aem65
exl-id: 4f45ad22-611b-4b4f-8e89-cb64a122b70a
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '1274'
ht-degree: 0%

---

# De doeltreffendheid en de conversie van formulieren meten en verbeteren{#measure-and-improve-effectiveness-and-conversion-of-forms}

## De uitdaging {#the-challenge-br}

Organisaties geven hun klanten steeds meer de mogelijkheid om via digitale zelfdiensten op meerdere kanalen te communiceren. Als er echter geen één-op-één terugkoppelingsmechanisme is, wordt het lastig om succes te meten en te experimenteren met digitale formulieren om de gebruikerservaring te verbeteren en conversies te vergroten.

Om ROI te maximaliseren, moeten de organisaties controleren hoe hun klanten met de diensten interactie aangaan, en met hun digitale artefacten (vormen) experimenteren om klantenervaringen te verbeteren. Om succes te meten en een strategie voor verbetering te bepalen, hebben de organisaties antwoorden op vragen zoals nodig:

* Hoeveel klanten hebben geprobeerd toegang te krijgen tot of te communiceren met mijn formulieren?
* Hoeveel van hen hebben de transactie met succes voltooid?
* Hoeveel van hen hebben het formulier verlaten?
* Wat zijn de probleemgebieden waar de klanten met problemen worden geconfronteerd?
* Welke veranderingen breng ik binnen en hoe test ik wat betere omzetting veroorzaakt?

## De oplossing {#the-solution}

AEM Forms integreert met [&#x200B; Adobe Marketing Cloud &#x200B;](https://www.adobe.com/marketing-cloud.html) oplossingen - [&#x200B; Adobe Analytics &#x200B;](https://www.adobe.com/marketing-cloud/web-analytics.html) en [&#x200B; Adobe Target &#x200B;](https://www.adobe.com/marketing-cloud/testing-targeting.html) - die u kunnen helpen controleren en analyseren hoe uw vormen presteren en u toelaten om de ervaring te experimenteren en te identificeren die tot betere omzettingspercentage leidt.

## De workflow {#the-workflow}

We gaan verder met de details over hoe u de prestaties kunt meten en de conversietarieven voor formulieren kunt verbeteren.

### Doelgroep {#target-audience}

* Zakelijke gebruikers en analisten die verantwoordelijk zijn voor marketingstrategieën en succes
* IT-personeel dat zorg draagt voor de installatie en het onderhoud van infrastructuur en oplossingen

### Betrokken AEM Forms-componenten en -functies {#aem-forms-components-and-features-involved}

* Aangepaste formulieren
* Integratie met Adobe Analytics voor het verzamelen, organiseren en rapporteren van klantinteracties met uw aangepaste formulieren
* Integratie met Adobe Target om A/B-tests uit te voeren voor adaptieve formulieren

### Veronderstellingen {#assumptions}

* U hebt al een Adobe Marketing Cloud-account en bent geregistreerd voor Analytics en Target-oplossingen.
* U hebt een gepubliceerd adaptief formulier waartoe klanten toegang hebben.

### Workflowstappen {#workflow-steps}

#### Stap 1: Analyse en doel configureren in AEM Forms  {#step-configure-analytics-and-target-in-aem-forms-br}

**vorm Analytics**

Om diepgaande inzichten in uw klanteninteractie met uw vormen te verkrijgen, moet u Analytics eerst in AEM Forms vormen. Voer de volgende stappen uit:

1. Een rapportsuite maken in Adobe Analytics
1. Cloudserviceconfiguratie maken in AEM
1. Cloudserviceframework maken in AEM
1. Configuratieservice voor AEM Forms Analytics configureren in AEM
1. Analyses inschakelen op het formulier in AEM

Voor gedetailleerde stappen, zie [&#x200B; het Vormen analyses en rapporten voor adaptieve vormen &#x200B;](../../forms/using/configure-analytics-forms-documents.md).

**vorm Doel**

Om A/B tests voor uw adaptieve vormen tot stand te brengen en in werking te stellen, vorm Doel in AEM Forms zoals die in [&#x200B; wordt beschreven Opstelling en integreer Doel in AEM Forms &#x200B;](../../forms/using/ab-testing-adaptive-forms.md#p-set-up-and-integrate-target-in-aem-forms-p).

#### Stap 2: analyserapport weergeven {#step-view-analytics-report-br}

Aangezien uw klanten tot en met vormen toegang hebben waarop u Analytics hebt toegelaten, worden hun interactie gevangen in hoogst beveiligde gegevensbestanden van Analytics. De databases worden gesegmenteerd door clients en zijn toegankelijk via beveiligde verbindingen.

U kunt een rapport vanuit AEM weergeven voor formulieren die analyses ondersteunen en gegevens analyseren. U kunt als volgt het rapport weergeven:

1. Op AEM server, navigeer aan **Forms > Forms &amp; Documenten**.
1. Selecteer het formulier waarvoor u het analyserapport wilt gebruiken.
1. Klik op het pictogram Analytische rapporten. Het rapport wordt weergegeven.

Laten we eens kijken naar de gegevenspunten die Analytics verzamelt en rapporteert voor formulieren.

**Forms analyserapport**

In het analyserapport voor adaptieve formulieren worden de volgende prestatiekernindicatoren (KPI&#39;s) op formulierniveau vastgelegd:

* **Gemiddelde vultijd**: Gemiddelde die tijd in het vullen van de vorm wordt doorgebracht
* **Impressies**: Aantal tijden de vorm in de onderzoeksresultaten verscheen

* **Vertoningen**: Aantal tijden de vorm is teruggegeven of geopend
* **Concepten**: Aantal tijden de vorm is bewaard als ontwerp

* **Voorleggen**: Aantal tijden de vorm is voorgelegd
* **verlaat**: Aantal tijden gebruikers verlaten zonder de vorm te voltooien
* **bezoeken/Voorleggen**: Verhouding van bezoeken per voorlegging

Bovendien krijgt u de volgende details over elk paneel in de vorm:

* **Tijd**: Gemiddelde die tijd (seconden) op het paneel en zijn gebieden wordt doorgebracht

* **Fout**: Aantal fouten die op het paneel en zijn gebieden per 1000 vormvertoningen worden ontmoet

* **Hulp**: Aantal tijden hebben de gebruikers tot de in-context hulp voor het paneel en zijn gebieden per 1000 vormvertoningen toegang gehad

![&#x200B; het rapport van de steekproefanalyse van A voor een adaptieve vorm &#x200B;](assets/summary-report.png)

Voor meer details over de rapporten van de vormenanalyse, zie [&#x200B; het Bekijken van en het begrip van de analyserapporten van AEM Forms &#x200B;](../../forms/using/view-understand-aem-forms-analytics-reports.md).

>[!NOTE]
>
>U kunt gedetailleerde rapporten weergeven en meer inzicht krijgen in uw klanten en hun interactie met uw formulieren via uw Analytics-account op Adobe Marketing Cloud.

#### Stap 3: Gegevenspunten analyseren {#step-analyze-data-points}

In deze stap analyseert u de gegevenspunten in het analyserapport en geeft u aan hoe het formulier functioneert. Als het niet aan uw succes KPIs voldoet, zult u hypotheses construeren, die op gegevens worden gebaseerd, en mogelijke oplossingen vinden om de kwesties te bevestigen. Bijvoorbeeld:

* Als de gemiddelde vultijd voor het formulier hoger is dan u verwacht, is het mogelijk dat uw formulier complex is voor klanten om te begrijpen, het formulier geen standaardterminologie gebruikt, het formulier te lang is, enzovoort. In dit geval kunt u de formulierstructuur en velden vereenvoudigen, het formulierontwerp opnieuw bewerken, de lengte van het formulier verkorten of Help-beschrijvingen en voorbeelden toevoegen voor niet-standaardformuliervelden.
* Als uit de gegevens blijkt dat de meeste klanten de Help voor een formuliervenster openen, is het duidelijk dat klanten zich afvragen welke informatie moet worden ingevuld. U kunt alternatieve terminologie gebruiken of wat voorbeeldinput en hulpbeschrijving voor dat paneel toevoegen.
* Als het afbreken of verlaten van de plaats voor een vorm hoger is dan verwacht, zou het wegens het formulier kunnen zijn die lange tijd te geven duurt, landen de klanten onbedoeld op het formulier, of het is te ingewikkeld. In dit geval kunt u de formulierbeschrijving die wordt weergegeven in de zoekresultaten optimaliseren, het formulier vereenvoudigen, het formulier optimaliseren zodat het sneller kan worden geladen, enzovoort.

Als u deze gegevenspunten hebt geanalyseerd en tot een hypothese bent gekomen, brengt u de vereiste wijzigingen aan in het formulier.

#### Stap 4: uw analyse en correcties valideren {#step-validate-your-analysis-and-fixes}

In deze stap valideert u de wijzigingen die u in het formulier hebt aangebracht en controleert u of deze van invloed zijn op de conversiesnelheid.

**stel een test A/B in werking**

Dankzij de integratie van AEM Forms met Target kunnen A/B-tests voor adaptieve formulieren worden gemaakt. In tests A/B, presenteert u willekeurig verschillende ervaringen van een vorm aan uw klanten in echt - tijd om te weten welke ervaring werkt beter of veroorzaakt meer omzettingen. Zodra u significante gegevens hebt die op één ervaring wijzen die betere omzetting levert dan andere, kunt u dat ervaringen als winnaar verklaren, en de toekomst, het wordt de standaardervaring zichtbaar aan alle klanten.

Voor meer informatie over het creëren van een test A/B voor een adaptieve vorm, zie [&#x200B; het testen A/B van adaptieve vormen &#x200B;](../../forms/using/ab-testing-adaptive-forms.md).

![&#x200B; een steekproefsamenvattingsrapport van A/B test voor een adaptieve vorm &#x200B;](assets/ab-test-report-4.png)

## Aanbevolen procedures {#best-practices}

De echte beste praktijken zijn degenen die u zich tijdens het uitvoeren van deze werkschema identificeert. Ze zijn uniek voor uw omgeving en vereisten. Leg uw lessen vast in de workflow en documenteer ze als aanbevolen procedures.

Sommige aanbevelingen voor het ontwerpen van formulieren en het uitvoeren van A/B-tests zijn als volgt:

**het ontwerp van Forms**

* Houd het formulier eenvoudig, kort en eenvoudig om te navigeren. Gebruik richtingsaanwijzingen voor navigatie.
* Standaardterminologie of algemene terminologie gebruiken voor formuliervelden.
* Beschrijf het veld en de vereiste invoer met voorbeelden of Help, waarbij gebruikers door elkaar kunnen raken.
* Valideer gebruikersinvoer tijdens het typen, waar mogelijk, om fouten bij het verzenden van formulieren te voorkomen.
* Lay-outs voor bureaublad en mobiele apparaten optimaliseren.
* Gegevens automatisch invullen voor bekende gebruikers.

**tests A/B**

* Construeer een hypothese en identificeer succeswaarden voordat u de A/B-test uitvoert.
* Voer minimale variaties (idealiter één voor één) uit in uw alternatieve ervaring om te weten wat de conversiesnelheid beïnvloedt.
* Test regelmatig om inefficiënties te voorkomen.
