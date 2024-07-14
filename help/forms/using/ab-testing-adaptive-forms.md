---
title: A/B-test voor adaptieve formulieren maken en beheren
description: AEM Forms integreert met Adobe Target, waardoor A/B-tests kunnen worden uitgevoerd voor adaptieve formulieren om de ervaring van klanten te verbeteren en de conversiesnelheden te verbeteren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
docset: aem65
exl-id: be2444df-c772-4a8e-83f9-0f565c15a44e
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: Admin, User, Developer
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '1556'
ht-degree: 0%

---

# A/B-test voor adaptieve formulieren maken en beheren{#create-and-manage-a-b-test-for-adaptive-forms}

[!BADGE  beëindigde ]{type=negative tooltip="Deze functie is nu levenseinde"}

<div class="preview"> De functie voor het testen van adaptieve formulieren in A/B is aan het einde van de levensduur verstreken en wordt niet meer ondersteund. </div>

## Overzicht {#overview-br}

Uw klanten zullen waarschijnlijk een formulier verlaten als de ervaring die het biedt, niet aantrekkelijk is. Hoewel het voor de klanten frustrerend is, kan het het steunvolume en de kosten voor uw organisatie ook herstellen. Het is kritiek en uitdagend om de juiste klantenervaring te identificeren en te verstrekken die de omzettingssnelheid verhoogt. Adobe Experience Manager Forms heeft de sleutel tot dit probleem.

AEM Forms integreert met Adobe Target, een Adobe Experience Cloud-oplossing, om persoonlijke en aantrekkelijke klantervaringen op verschillende digitale kanalen te bieden. Een van de belangrijkste mogelijkheden van Target is A/B-tests waarmee u snel gelijktijdige A/B-tests kunt instellen, relevante inhoud voor de beoogde gebruikers kunt presenteren en de ervaring kunt identificeren die een betere conversiesnelheid mogelijk maakt.

Met Adobe Experience Manager (AEM) Forms kunt u A/B-tests instellen en uitvoeren op adaptieve formulieren in real-time. Het biedt ook offline en aanpasbare rapportagemogelijkheden om de prestaties in real-time van uw formulierervaringen te visualiseren en het systeem te identificeren dat de betrokkenheid en conversie van gebruikers maximaliseert.

## Doel instellen en integreren in AEM Forms {#set-up-and-integrate-target-in-aem-forms}

Voordat u A/B-tests gaat maken en analyseren op adaptieve formulieren, moet u eerst de doelserver instellen en deze integreren in AEM Forms.

### Doel instellen {#set-up-target}

Zorg ervoor dat u een geldig Adobe Target-account hebt om AEM met Target te integreren. Wanneer u zich bij Adobe Target registreert, ontvangt u een clientcode. U hebt de cliëntcode, e-mail verbonden aan de rekening van het Doel, en wachtwoord nodig om AEM met Doel te verbinden.

De clientcode identificeert de Adobe Target-klantenaccount en wordt gebruikt als een subdomein in de URL wanneer de Adobe Target-server wordt aangeroepen. Alvorens te werk te gaan, login aan [ https://experience.adobe.com/ ](https://experience.adobe.com/) en, als u toegang hebt, bekijk de [!DNL Adobe Target] optie in de [!UICONTROL Quick Access] sectie.

### Een actieve doelserver integreren met AEM Forms {#integrate-target-in-aem-forms}

1. Op AEM server, ga naar https://&lt; *hostname*>:&lt; *haven*>/libs/cq/core/content/tools/cloudservices.html.

1. In de **Adobe Target** sectie, klik **Configuraties** tonen en dan **+** pictogram om een configuratie toe te voegen.
Als u een doel voor het eerst vormt, klik **nu vormen.**

1. In de Create configuratiedialoog, specificeer a **Titel** en naar keuze a **Naam** voor de configuratie.

1. Klik **creëren**. Het dialoogvenster Component bewerken wordt geopend.
1. Geef de gegevens van uw doelaccount op, zoals clientcode, e-mail en wachtwoord.
1. Selecteer **Rest** van de drop-down lijst van het Type API.

1. Klik **verbinden met Adobe Target** zodat kunt u de verbinding met Doel initialiseren. Als de verbinding succesvol is, wordt het bericht Verbinding succesvol getoond. Klik **O.K.** op het bericht en dan **O.K.** op de dialoog. De doelaccount is geconfigureerd.

1. Creeer een kader van het Doel zoals die in [ wordt beschreven voeg een kader ](/help/sites-administering/target.md) toe.

1. Ga naar https://&lt;*hostname*>:&lt; *haven*>/system/console/configMgr.

1. Klik **het DoelConfiguratie van AEM Forms**.
1. Selecteer a **Kader van het Doel**.
1. Op het **gebied van het Doel URLs**, specificeer al URLs waar A/B tests lopen. Bijvoorbeeld, https://&lt;*hostname*>:&lt; *haven*>/ voor de Server van AEM Forms op OSGi of https://&lt;*hostname*>:&lt;*haven*>/lc/ voor de Server van AEM Forms op JEE.
Bedenk dat u een doel-URL voor een Publish-instantie wilt configureren en uw klanten er toegang toe hebben met de hostnaam of het IP-adres. In dat geval, moet u zowel als Doel URLs vormen - gebruikend hostname en het IP adres. Als u slechts één van URLs vormt, loopt uw test A/B niet voor klanten die van andere URL komen. Klik **+** om veelvoudige URLs te specificeren.

1. Klik **sparen**.

Uw doelserver is geïntegreerd met AEM Forms. U kunt nu A/B-tests inschakelen als u een volledige licentie hebt om Adobe Target te gebruiken.

Als u over een volledige licentie voor het gebruik van Adobe Target beschikt, start u de server met de volgende parameters nadat u Target met AEM Forms hebt geïntegreerd:

`parameter -Dabtesting.enabled=true java -Xmx2048m -XX:MaxPermSize=512M -jar -Dabtesting.enabled=true`

Als de AEM-instantie wordt uitgevoerd op JBoss®, gestart als een service van key, voegt u in `jboss\bin\standalone.conf.bat` file de parameter add-Dabtesting.enabled=true toe in de volgende vermelding:

`set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

Naast JBoss® server, kunt u - Dabtesting.enabled=true jvm argument in het serverstartmanuscript voor om het even welke toepassingsserver toevoegen. Nu kunt u A/B-tests maken en uitvoeren voor adaptieve formulieren.

>[!NOTE]
>
>Als u gevormde Doel URLs later bijwerkt, zorg ervoor dat u om het even welke lopende tests A/B bijwerkt zodat zij aan huidige URLs richten. Voor informatie over het bijwerken van tests A/B, zie [ de test van A/B van de Update ](/help/forms/using/ab-testing-adaptive-forms.md#p-update-a-b-test-p).
>

## Soorten publiek maken binnen AEM {#create-audiences-within-aem}

Met AEM kunt u een publiek maken en dit gebruiken voor een A/B-test. Het publiek dat u binnen AEM maakt, is beschikbaar in AEM Forms. Ga als volgt te werk om een publiek binnen AEM te maken:

1. In auteursinstantie, uitgezochte **Adobe Experience Manager** > **Personalization** > **Soorten van publiek**.

1. In de pagina van het publiek, creeer de uitgezochte **Publiek > tot het Publiek van het Doel** leidt.
1. In de dialoog van de Configuratie van Adobe Target, selecteer een configuratie van het Doel en klik **O.K.**.
1. Maak regels op de pagina Nieuw publiek maken. Met regels kunt u het publiek indelen. U wilt bijvoorbeeld soorten publiek categoriseren op basis van het besturingssysteem. Uw publiek A komt van Vensters, en publiek B komt van Linux®.

   1. Om een publiek te categoriseren dat op Vensters, in Regel #1 wordt gebaseerd, selecteer het **OS** kenmerktype dat. Van wanneer drop-down, uitgezochte **Vensters.**

   1. Om publiek te categoriseren dat op Linux®, in Regel #2 wordt gebaseerd, selecteer het **OS** attribuuttype dat. Van **wanneer** drop-down, uitgezochte **Linux®**, en klik **daarna**.

1. Specificeer een naam voor het gecreeerde publiek, en klik **sparen**.

U kunt de doelgroep selecteren wanneer u A/B-tests voor een formulier configureert, zoals hieronder wordt weergegeven.

## A/B-test maken voor een adaptief formulier {#create-a-b-test}

1. Ga naar **Forms &amp; Documenten** in https://&lt; *hostname*>:&lt; *haven*>/aem/forms.html/content/dam/formsanddocuments.

1. Navigeer naar de map met het adaptieve formulier.
1. Klik het **Uitgezochte** hulpmiddel in de toolbar en selecteer de adaptieve vorm.
1. Klik **Meer** in de toolbar en selecteer **A/B het Testen** vormen. De Configure A/B testende pagina opent.

[](assets/ab-test-configure-1.png)

1. Specificeer een **Naam van de Activiteit** voor de test A/B.

1. Selecteer in de vervolgkeuzelijst Publiek een publiek voor wie u verschillende ervaringen met het formulier wilt gebruiken. Bijvoorbeeld, **Bezoekers die Chrome** gebruiken. De publiekslijst wordt bevolkt van de gevormde server van het Doel.

1. In de **gebieden van de Distributie van de Ervaring** voor ervaringen A en B, specificeer de distributie, in termen van percentage, om de distributie van ervaringen onder het totale publiek te bepalen. Als u bijvoorbeeld 40, 60 opgeeft voor respectievelijk de ervaringen A en B, wordt de ervaring A opgedaan voor 40% van het publiek en de resterende 60% voor de ervaring B.
1. Klik **vormen**. Er verschijnt een dialoogvenster waarin de aanmaak van de A/B-test wordt bevestigd.
1. Klik **geef Ervaring B** uit zodat kunt u de adaptieve vorm op uitgeven wijze openen. Wijzig het formulier door een andere ervaring te maken dan de standaardeigenschap A. De mogelijke variaties die in ervaring B zijn toegestaan, zijn veranderingen in:

   * CSS of opmaak
   * Volgorde van velden in verschillende deelvensters of in hetzelfde deelvenster
   * Deelvensterlay-out
   * Deelvenstertitels
   * Beschrijving, label en Help-tekst voor een veld
   * Scripts die geen invloed hebben op of een einde maken aan de verzendstroom
   * Validaties (zowel client als server)
   * Thema voor ervaring B. (U kunt een ander thema voor ervaring B selecteren)

1. Ga naar Forms en Documenten UI, selecteer de adaptieve vorm, klik **Meer**, en selecteer **Testen A/B van het Begin**.

Uw A/B-test wordt nu uitgevoerd en het opgegeven publiek wordt op willekeurige wijze gediend met de ervaringen op basis van de opgegeven distributie.

## De A/B-test bijwerken {#update-a-b-test}

U kunt het publiek bijwerken en verspreidingen van een lopende test A/B ervaren.

De A/B-test bijwerken:

1. Navigeer in de gebruikersinterface van Forms en documenten naar de map met het adaptieve formulier waarop de A/B-test wordt uitgevoerd.
1. Selecteer het adaptieve formulier.
1. Klik **Meer** en selecteer dan **A/B het testen** uitgeven. De testpagina A/B bijwerken wordt geopend.

1. Werk het publiek en ervaringsprestaties bij, indien nodig.
1. Klik **Update**.

## A/B-testrapport weergeven en analyseren {#view-and-analyze-a-b-test-report}

Zodra u de A/B test hebt toegestaan om voor de gewenste periode te lopen, kunt u een rapport produceren en controleren welke ervaring in betere omzetting heeft geresulteerd. U kunt de beter presterende ervaring declareren als winnaar of een andere A/B-test uitvoeren.

Het testrapport A/B weergeven en analyseren:

1. Selecteer de adaptieve vorm, klik **Meer**, en klik dan **het Testen van A/B Rapport**. Het rapport wordt weergegeven.

[](assets/ab-test-report-3.png)

1. Analyseer het rapport en controleer of u genoeg gegevenspunten hebt om één van de beter presterende ervaringen als winnaar te verklaren. U kunt ervoor kiezen om dezelfde A/B-test langer te blijven uitvoeren of een winnaar te declareren en de A/B-test te beëindigen.
1. Om een winnaar te verklaren en de test te beëindigen A/B, klik het **Eind A/B test** knoop op het rapporteringsdashboard. In een dialoogvenster wordt u gevraagd een van de twee ervaringen als winnaar op te geven. Kies een winnaar en bevestig om de A/B-test te beëindigen.
Alternatief, kunt u een winnaar eerst verklaren door de **knoop van de Beller van de Declaratie** voor de respectieve ervaring te klikken. Je wordt gevraagd de winnaar te bevestigen. Klik **ja** om de test te beëindigen A/B.

Als u A als winnaar hebt gekozen, wordt de A/B-test beëindigd en, in de toekomst, wordt alleen Experience A aan het publiek aangeboden.
