---
title: A/B-test voor adaptieve formulieren maken en beheren
description: AEM Forms integreert met Adobe Target, waardoor A/B-tests kunnen worden uitgevoerd voor adaptieve formulieren om de ervaring van klanten te verbeteren en de conversiesnelheden te verbeteren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
docset: aem65
exl-id: be2444df-c772-4a8e-83f9-0f565c15a44e
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '1556'
ht-degree: 0%

---

# A/B-test voor adaptieve formulieren maken en beheren{#create-and-manage-a-b-test-for-adaptive-forms}

[!BADGE Stopzetten]{type=negative tooltip="Deze functie is nu levenseinde"}

<div class="preview"> De functie voor het testen van adaptieve formulieren in A/B is aan het einde van de levensduur verstreken en wordt niet meer ondersteund. </div>

## Overzicht {#overview-br}

Uw klanten zullen waarschijnlijk een formulier verlaten als de ervaring die het biedt, niet aantrekkelijk is. Hoewel het voor de klanten frustrerend is, kan het het steunvolume en de kosten voor uw organisatie ook herstellen. Het is kritiek en uitdagend om de juiste klantenervaring te identificeren en te verstrekken die de omzettingssnelheid verhoogt. Adobe Experience Manager Forms heeft de sleutel tot dit probleem.

AEM Forms integreert met Adobe Target, een Adobe Experience Cloud-oplossing, om persoonlijke en aantrekkelijke klantervaringen op verschillende digitale kanalen te bieden. Een van de belangrijkste mogelijkheden van Target is A/B-tests waarmee u snel gelijktijdige A/B-tests kunt instellen, relevante inhoud voor de beoogde gebruikers kunt presenteren en de ervaring kunt identificeren die een betere conversiesnelheid mogelijk maakt.

Met Adobe Experience Manager (AEM) Forms kunt u A/B-tests instellen en uitvoeren op adaptieve formulieren in real-time. Het biedt ook offline en aanpasbare rapportagemogelijkheden om de prestaties in real-time van uw formulierervaringen te visualiseren en het systeem te identificeren dat de betrokkenheid en conversie van gebruikers maximaliseert.

## Doel instellen en integreren in AEM Forms {#set-up-and-integrate-target-in-aem-forms}

Voordat u A/B-tests gaat maken en analyseren op adaptieve formulieren, moet u eerst de doelserver instellen en deze integreren in AEM Forms.

### Doel instellen {#set-up-target}

Zorg ervoor dat u een geldig Adobe Target-account hebt om AEM met Target te integreren. Wanneer u zich bij Adobe Target registreert, ontvangt u een clientcode. U hebt de cliëntcode, e-mail verbonden aan de rekening van het Doel, en wachtwoord nodig om AEM met Doel te verbinden.

De clientcode identificeert de Adobe Target-klantenaccount en wordt gebruikt als een subdomein in de URL wanneer de Adobe Target-server wordt aangeroepen. Meld u aan bij [https://experience.adobe.com/](https://experience.adobe.com/) en, als u toegang hebt, bekijk [!DNL Adobe Target] in de [!UICONTROL Quick Access] sectie.

### Een actieve doelserver integreren met AEM Forms {#integrate-target-in-aem-forms}

1. Ga op AEM server naar https://&lt;*hostnaam*>:&lt;*poort*>/libs/cq/core/content/tools/cloudservices.html.

1. In de **Adobe Target** sectie, klikken **Configuraties tonen** en vervolgens de **+** pictogram om een configuratie toe te voegen.
Als u een doel voor het eerst configureert, klikt u op **Nu configureren.**

1. Geef in het dialoogvenster Configuratie maken een **Titel** en eventueel een **Naam** voor de configuratie.

1. Klikken **Maken**. Het dialoogvenster Component bewerken wordt geopend.
1. Geef de gegevens van uw doelaccount op, zoals clientcode, e-mail en wachtwoord.
1. Selecteren **Rust** in de vervolgkeuzelijst Type API.

1. Klikken **Verbinding maken met Adobe Target** zodat u de verbinding met Doel kunt initialiseren. Als de verbinding succesvol is, wordt het bericht Verbinding succesvol getoond. Klikken **OK** op het bericht en vervolgens **OK** in het dialoogvenster. De doelaccount is geconfigureerd.

1. Een doelframework maken zoals beschreven in [Een framework toevoegen](/help/sites-administering/target.md).

1. Ga naar https://&lt;*hostnaam*>:&lt;*poort*>/system/console/configMgr.

1. Klikken **AEM Forms Target Configuration**.
1. Selecteer een **Doelframework**.
1. In de **Doel-URL&#39;s** geeft u alle URL&#39;s op waar A/B-tests worden uitgevoerd. Bijvoorbeeld https://&lt;*hostnaam*>:&lt;*poort*>/ voor AEM Forms Server op OSGi of https://&lt;*hostnaam*>:&lt;*poort*>/lc/ voor AEM Forms Server op JEE.
Bedenk dat u een Doel URL voor een Publish instantie wilt vormen en uw klanten tot het kunnen toegang hebben gebruikend hostname of het IP adres. In dat geval, moet u zowel als Doel URLs vormen - gebruikend hostname en het IP adres. Als u slechts één van URLs vormt, loopt uw test A/B niet voor klanten die van andere URL komen. Klikken **+** meerdere URL&#39;s opgeven.

1. Klikken **Opslaan**.

Uw doelserver is geïntegreerd met AEM Forms. U kunt nu A/B-tests inschakelen als u een volledige licentie hebt om Adobe Target te gebruiken.

Als u over een volledige licentie voor het gebruik van Adobe Target beschikt, start u de server met de volgende parameters nadat u Target met AEM Forms hebt geïntegreerd:

`parameter -Dabtesting.enabled=true java -Xmx2048m -XX:MaxPermSize=512M -jar -Dabtesting.enabled=true`

Als de AEM-instantie op JBoss® wordt uitgevoerd, is deze als een service vanuit Turkije gestart, `jboss\bin\standalone.conf.bat` file, add-Dabtesting.enabled=true parameter in de volgende vermelding:

`set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

Naast JBoss® server, kunt u - Dabtesting.enabled=true jvm argument in het serverstartmanuscript voor om het even welke toepassingsserver toevoegen. Nu kunt u A/B-tests maken en uitvoeren voor adaptieve formulieren.

>[!NOTE]
>
>Als u gevormde Doel URLs later bijwerkt, zorg ervoor dat u om het even welke lopende tests A/B bijwerkt zodat zij aan huidige URLs richten. Zie voor informatie over het bijwerken van A/B-tests [A/B-test bijwerken](/help/forms/using/ab-testing-adaptive-forms.md#p-update-a-b-test-p).
>

## Soorten publiek maken binnen AEM {#create-audiences-within-aem}

Met AEM kunt u een publiek maken en dit gebruiken voor een A/B-test. Het publiek dat u binnen AEM maakt, is beschikbaar in AEM Forms. Ga als volgt te werk om een publiek binnen AEM te maken:

1. Selecteer in ontwerpinstantie **Adobe Experience Manager** > **Personalisatie** > **Soorten publiek**.

1. Selecteer op de pagina Soorten publiek de optie **Publiek maken > Doelpubliek maken**.
1. Selecteer een doelconfiguratie in het dialoogvenster Adobe Target-configuratie en klik op **OK**.
1. Maak regels op de pagina Nieuw publiek maken. Met regels kunt u het publiek indelen. U wilt bijvoorbeeld soorten publiek categoriseren op basis van het besturingssysteem. Uw publiek A komt van Vensters, en publiek B komt van Linux®.

   1. Als u een publiek wilt indelen op basis van Windows, selecteert u in Regel 1 de optie **OS** kenmerktype. Selecteer in het vervolgkeuzemenu Wanneer de optie **Windows.**

   1. Als u een publiek wilt indelen op basis van Linux®, selecteert u in Regel 2 de optie **OS** kenmerktype. Van de **Wanneer** vervolgkeuzelijst, selecteert u **Linux®** en klik op **Volgende**.

1. Geef een naam op voor het nieuwe publiek en klik op **Opslaan**.

U kunt de doelgroep selecteren wanneer u A/B-tests voor een formulier configureert, zoals hieronder wordt weergegeven.

## A/B-test maken voor een adaptief formulier {#create-a-b-test}

1. Ga naar **Forms &amp; Documenten** op https://&lt;*hostnaam*>:&lt;*poort*>/aem/forms.html/content/dam/formsanddocuments.

1. Navigeer naar de map met het adaptieve formulier.
1. Klik op de knop **Selecteren** in de werkbalk en selecteert u het aangepaste formulier.
1. Klikken **Meer** in de werkbalk en selecteert u **A/B-tests configureren**. De Configure A/B testende pagina opent.

[](assets/ab-test-configure-1.png)

1. Geef een **Naam activiteit** voor de A/B-test.

1. Selecteer in de vervolgkeuzelijst Publiek een publiek voor wie u verschillende ervaringen met het formulier wilt gebruiken. Bijvoorbeeld: **Bezoekers met Chrome**. De publiekslijst wordt bevolkt van de gevormde server van het Doel.

1. In de **Ervaringsverdeling** in de velden voor de ervaringen A en B de spreiding, uitgedrukt in percentage, van de ervaringen over het totale publiek. Als u bijvoorbeeld 40, 60 opgeeft voor respectievelijk de ervaringen A en B, wordt de ervaring A opgedaan voor 40% van het publiek en de resterende 60% voor de ervaring B.
1. Klikken **Configureren**. Er verschijnt een dialoogvenster waarin de aanmaak van de A/B-test wordt bevestigd.
1. Klikken **Ervaring B bewerken** zodat u het adaptieve formulier kunt openen in de bewerkingsmodus. Wijzig het formulier door een andere ervaring te maken dan de standaardeigenschap A. De mogelijke variaties die in ervaring B zijn toegestaan, zijn veranderingen in:

   * CSS of opmaak
   * Volgorde van velden in verschillende deelvensters of in hetzelfde deelvenster
   * Deelvensterlay-out
   * Deelvenstertitels
   * Beschrijving, label en Help-tekst voor een veld
   * Scripts die geen invloed hebben op of een einde maken aan de verzendstroom
   * Validaties (zowel client als server)
   * Thema voor ervaring B. (U kunt een ander thema voor ervaring B selecteren)

1. Ga naar de gebruikersinterface van Forms en Documenten, selecteer het aangepaste formulier en klik op **Meer** en selecteert u **A/B-tests starten**.

Uw A/B-test wordt nu uitgevoerd en het opgegeven publiek wordt op willekeurige wijze gediend met de ervaringen op basis van de opgegeven distributie.

## De A/B-test bijwerken {#update-a-b-test}

U kunt het publiek bijwerken en verspreidingen van een lopende test A/B ervaren.

De A/B-test bijwerken:

1. Navigeer in de gebruikersinterface van Forms en documenten naar de map met het adaptieve formulier waarop de A/B-test wordt uitgevoerd.
1. Selecteer het adaptieve formulier.
1. Klikken **Meer** en selecteer vervolgens **A/B-tests bewerken**. De testpagina A/B bijwerken wordt geopend.

1. Werk het publiek en ervaringsprestaties bij, indien nodig.
1. Klikken **Bijwerken**.

## A/B-testrapport weergeven en analyseren {#view-and-analyze-a-b-test-report}

Zodra u de A/B test hebt toegestaan om voor de gewenste periode te lopen, kunt u een rapport produceren en controleren welke ervaring in betere omzetting heeft geresulteerd. U kunt de beter presterende ervaring declareren als winnaar of een andere A/B-test uitvoeren.

Het testrapport A/B weergeven en analyseren:

1. Selecteer het aangepaste formulier en klik op **Meer** en klik vervolgens op **Testrapport A/B**. Het rapport wordt weergegeven.

[](assets/ab-test-report-3.png)

1. Analyseer het rapport en controleer of u genoeg gegevenspunten hebt om één van de beter presterende ervaringen als winnaar te verklaren. U kunt ervoor kiezen om dezelfde A/B-test langer te blijven uitvoeren of een winnaar te declareren en de A/B-test te beëindigen.
1. Als u een winnaar wilt declareren en de toets A/B wilt beëindigen, klikt u op de knop **Einde A/B-test** op het rapportdashboard. In een dialoogvenster wordt u gevraagd een van de twee ervaringen als winnaar op te geven. Kies een winnaar en bevestig om de A/B-test te beëindigen.
U kunt ook eerst een winnaar declareren door op de knop **Winner declareren** voor de desbetreffende ervaring. Je wordt gevraagd de winnaar te bevestigen. Klikken **Ja** om de A/B-test te beëindigen.

Als u A als winnaar hebt gekozen, wordt de A/B-test beëindigd en, in de toekomst, wordt alleen Experience A aan het publiek aangeboden.
