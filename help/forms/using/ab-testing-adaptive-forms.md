---
title: A/B-test voor adaptieve formulieren maken en beheren
seo-title: A/B-test voor adaptieve formulieren maken en beheren
description: AEM Forms is geïntegreerd met Adobe Target waarmee A/B-tests voor adaptieve formulieren kunnen worden uitgevoerd om de gebruikerservaring te verbeteren en de conversiesnelheden te verbeteren.
seo-description: AEM Forms is geïntegreerd met Adobe Target waarmee A/B-tests voor adaptieve formulieren kunnen worden uitgevoerd om de gebruikerservaring te verbeteren en de conversiesnelheden te verbeteren.
uuid: e258805c-4da8-4c5d-ae91-7bea78a6a71b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
discoiquuid: 8f776f30-ff93-4d19-94c6-c4bfe6f1fae2
docset: aem65
translation-type: tm+mt
source-git-commit: 3eaace94bc0499aaebfcd389d4dc97b97c7d9160

---


# A/B-test voor adaptieve formulieren maken en beheren{#create-and-manage-a-b-test-for-adaptive-forms}

## Overzicht {#overview-br}

Uw klanten zullen waarschijnlijk een formulier verlaten als de ervaring die het biedt, niet aantrekkelijk is. Hoewel het voor de klanten frustrerend is, kan het het steunvolume en de kosten voor uw organisatie ook herstellen. Het is kritiek evenals uitdagend om de juiste klantenervaring te identificeren en te verstrekken die de omrekeningskoers verhoogt. Adobe Experience Manager Forms houdt de sleutel voor dit probleem in.

AEM Forms integreert met Adobe Target, een Adobe Marketing Cloud-oplossing, om persoonlijke en boeiende ervaringen van klanten via meerdere digitale kanalen te bieden. Een van de belangrijkste mogelijkheden van Target is A/B-tests waarmee u snel gelijktijdige A/B-tests kunt instellen, relevante inhoud voor de beoogde gebruikers kunt presenteren en de ervaring kunt identificeren die een betere conversiesnelheid mogelijk maakt.

Met AEM Forms kunt u A/B-tests instellen en uitvoeren op adaptieve formulieren in real-time. Het biedt ook offline en aanpasbare rapportagemogelijkheden om de prestaties in real-time van uw formulierervaringen te visualiseren en het systeem te identificeren dat de betrokkenheid en conversie van gebruikers maximaliseert.

## Doel instellen en integreren in AEM-formulieren {#set-up-and-integrate-target-in-aem-forms}

Voordat u A/B-tests gaat maken en analyseren op adaptieve formulieren, moet u de doelserver instellen en integreren in AEM-formulieren.

### Doel instellen {#set-up-target}

Als u AEM wilt integreren met Target, moet u zorgen dat u een geldig Adobe Target-account hebt. Wanneer u zich bij Adobe Target registreert, ontvangt u een clientcode. U hebt de clientcode, de e-mail die aan het Target-account is gekoppeld en het wachtwoord nodig om verbinding te maken met AEM met Target.

De clientcode identificeert de Adobe Target-klantaccount en wordt gebruikt als een subdomein in de URL wanneer de Adobe Target-server wordt aangeroepen. Voordat u verdergaat, moet u ervoor zorgen dat u zich op [https://testandtarget.omniture.com/](https://testandtarget.omniture.com/)kunt aanmelden.

### Doel integreren in AEM-formulieren {#integrate-target-in-aem-forms}

Voer de volgende stappen uit om een actieve doelserver te integreren met AEM-formulieren:

1. Ga op de AEM-server naar https://&lt;*hostname*>:&lt;*port*>/libs/cq/core/content/tools/cloudservices.html.

1. Klik in de sectie **Adobe Target** op Configuraties **** tonen en vervolgens op het pictogram **+** om een nieuwe configuratie toe te voegen.
Als u doel voor het eerst vormt, klik nu **vormen.**

1. In de Create configuratiedialoog, specificeer een **Titel** en naar keuze een **Naam** voor de configuratie.

1. Klik op **Maken**. Het dialoogvenster Component bewerken wordt geopend.
1. Geef de gegevens van uw doelaccount op, zoals clientcode, e-mail en wachtwoord.
1. Selecteer **Rest** in de vervolgkeuzelijst Type API.

1. Klik op **Verbinding maken met Adobe Target** om de verbinding met Target te initialiseren. Als de verbinding succesvol is, wordt het bericht Verbinding succesvol getoond. Klik op **OK** in het bericht en vervolgens op **OK** in het dialoogvenster. De doelaccount is geconfigureerd.

1. Maak een doelframework zoals beschreven in [Een framework](/help/sites-administering/target.md)toevoegen.

1. Ga naar https://&lt;*hostname*>:&lt;*port*>/system/console/configMgr.

1. Klik op **AEM Forms Target Configuration**.
1. Selecteer een **doelframework**.
1. Geef in het veld **Doel-URL&#39;s** alle URL&#39;s op waar A/B-tests worden uitgevoerd. Bijvoorbeeld https://&lt;*hostnaam*>:&lt;*poort*>/ voor AEM Forms-server op OSGi of https://&lt;*hostnaam*>:&lt;*poort*>/lc/ voor AEM Forms-server op JEE.
Bedenk dat u een Doel URL voor publiceer instantie wilt vormen en uw klanten tot het kunnen toegang hebben gebruikend hostname of het IP adres, zult u zowel als Doel URLs moeten vormen - gebruikend hostname evenals het IP adres. Als u slechts één van URLs vormt, zal uw test A/B niet lopen voor klanten die van andere URL komen. Klik **+** om meerdere URL&#39;s op te geven.

1. Click **Save**.

Uw doelserver is geïntegreerd met AEM-formulieren. U kunt het testen A/B nu inschakelen als u een volledige licentie hebt om Adobe Target te gebruiken.

Als u een volledige licentie hebt om Adobe Target te gebruiken, start u de server met de volgende parameters nadat u Target met AEM Forms hebt geïntegreerd:

`parameter -Dabtesting.enabled=true java -Xmx2048m -XX:MaxPermSize=512M -jar -Dabtesting.enabled=true`

Als de instantie AEM op JBoss loopt, begonnen als dienst van turnkey, in `jboss\bin\standalone.conf.bat` dossier, add-Dabtesting.enabled=true parameter in de volgende ingang:

`set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

Naast de jreliëfserver kunt u ook het jvm-argument Dabtesting.enabled=true toevoegen in het opstartscript van de server voor elke toepassingsserver. U kunt nu A/B-tests maken en uitvoeren voor adaptieve formulieren.

>[!NOTE]
>
>Als u gevormde Doel URLs later bijwerkt, zorg ervoor dat u om het even welke lopende tests A/B bijwerkt zodat zij aan huidige URLs richten. Voor informatie over het bijwerken van A/B tests, zie [Update A/B test](/help/forms/using/ab-testing-adaptive-forms.md#p-update-a-b-test-p).


## Soorten publiek maken in AEM {#create-audiences-within-aem}

Met AEM kunt u een publiek maken en dit gebruiken voor een A/B-test. Het publiek dat u in AEM maakt, is beschikbaar in AEM Forms. Voer de volgende stappen uit om een publiek te maken in AEM:

1. Tik in de ontwerpversie op **Adobe Experience Manager** > **Persoonlijke** waarden > **Soorten publiek**.

1. Tik op de pagina Soorten publiek op **Publiek maken > Doelpubliek** maken.
1. Selecteer een doelconfiguratie in het dialoogvenster Adobe Target Configuration en klik op **OK**.
1. Maak regels op de pagina Nieuw publiek maken. Met regels kunt u het publiek indelen. U wilt bijvoorbeeld soorten publiek indelen op basis van het besturingssysteem. Uw publiek A komt van Vensters, en publiek B komt van Linux.

   1. Als u een publiek wilt categoriseren op basis van Windows, selecteert u in Regel 1 het **kenmerk type van het besturingssysteem** . Selecteer **Windows in het keuzemenu Bij.**

   1. Als u een publiek wilt categoriseren op basis van Linux, selecteert u in Regel 2 het **kenmerktype van het besturingssysteem** . Selecteer **Linux** in de vervolgkeuzelijst **Wanneer** en klik op **Volgende**.

1. Geef een naam op voor het publiek dat u hebt gemaakt en klik op **Opslaan**.

U kunt de doelgroep selecteren wanneer u A/B-tests voor een formulier configureert, zoals hieronder wordt weergegeven.

## A/B-test maken {#create-a-b-test}

Voer de volgende stappen uit om een A/B-test voor een adaptief formulier te maken.

1. Ga naar **Forms &amp; Documents** op https://&lt;*hostname*>:&lt;*port*>/aem/forms.html/content/dam/formsanddocuments.

1. Navigeer naar de map met het adaptieve formulier.
1. Klik op het gereedschap **Selectie** op de werkbalk en selecteer het aangepaste formulier.
1. Klik op **Meer** op de werkbalk en selecteer **A/B-tests** configureren. De Configure A/B testende pagina opent.

[ Pagina met testconfiguratie ![A/B voor adaptieve formulieren](assets/ab-test-configure.png)](assets/ab-test-configure-1.png)

1. Geef een naam **voor de** activiteit op voor de A/B-test.

1. Selecteer in de vervolgkeuzelijst Publiek een publiek voor wie u verschillende ervaringen met het formulier wilt gebruiken. Bijvoorbeeld **Bezoekers die Chrome** gebruiken. De publiekslijst wordt bevolkt van de gevormde server van het Doel.

1. In de gebieden van de Distributie **van de** Ervaring voor ervaringen A en B, specificeer de distributie, in termen van percentage, om de distributie van ervaringen onder het totale publiek te bepalen. Als u bijvoorbeeld 40, 60 opgeeft voor respectievelijk de ervaringen A en B, zal de ervaring A worden benut voor 40% van het publiek en zal de resterende 60% de ervaring B zien.
1. Klik op **Configureren**. Er verschijnt een dialoogvenster waarin de aanmaak van de A/B-test wordt bevestigd.
1. Klik op **Ervaring B** bewerken om het adaptieve formulier te openen in de bewerkingsmodus. Wijzig het formulier om een andere ervaring op te doen dan de standaardeigenschap A. De mogelijke variaties die in ervaring B zijn toegestaan, zijn veranderingen in:

   * CSS of opmaak
   * Volgorde van velden in verschillende deelvensters of in hetzelfde deelvenster
   * Deelvensterlay-out
   * Deelvenstertitels
   * Beschrijving, label en Help-tekst voor een veld
   * Scripts die geen invloed hebben op of een einde maken aan de verzendstroom
   * Validaties (zowel client als server)
   * Thema voor ervaring B. (U kunt een ander thema selecteren voor ervaring B)

1. Ga naar de interface Formulieren en documenten, selecteer het aangepaste formulier, klik op **Meer** en selecteer **A/B-tests** starten.

De A/B-test wordt nu uitgevoerd en het opgegeven publiek wordt op willekeurige wijze aangeboden op basis van de opgegeven distributie.

## A/B-test bijwerken {#update-a-b-test}

U kunt het publiek bijwerken en verspreidingen van een lopende test A/B ervaren. Daartoe:

1. Navigeer in de gebruikersinterface Formulieren en documenten naar de map met het adaptieve formulier waarop de A/B-test wordt uitgevoerd.
1. Selecteer het adaptieve formulier.
1. Klik op **Meer** en selecteer vervolgens **A/B-tests** bewerken. De testpagina A/B bijwerken wordt geopend.

1. Werk het publiek en ervaringsprestaties bij, indien nodig.
1. Klik op **Bijwerken**.

## A/B-testrapport weergeven en analyseren {#view-and-analyze-a-b-test-report}

Zodra u de A/B test hebt toegestaan om voor de gewenste periode te lopen, kunt u een rapport produceren en controleren welke ervaring in betere omzetting heeft geresulteerd. U kunt de beter presterende ervaring declareren als winnaar of een andere A/B-test uitvoeren. Voer hiertoe de volgende stappen uit:

1. Selecteer het aangepaste formulier, klik op **Meer** en klik vervolgens op **Testrapport** A/B. Het rapport wordt weergegeven.

[ Testrapport ![A/B](assets/ab-test-report-2.png)](assets/ab-test-report-3.png)

1. Analyseer het rapport en controleer of u genoeg gegevenspunten hebt om één van de beter presterende ervaringen als winnaar te verklaren. U kunt ervoor kiezen om dezelfde A/B-test langer te blijven uitvoeren of een winnaar te declareren en de A/B-test te beëindigen.
1. Als u een winnaar wilt declareren en de A/B-test wilt beëindigen, klikt u op de knop **Einde A/B-test** op het rapportagedashboard. In een dialoogvenster wordt u gevraagd een van de twee ervaringen als winnaar op te geven. Kies een winnaar en bevestig om de A/B-test te beëindigen.
U kunt ook eerst een winnaar declareren door op de knop Winner **** declareren te klikken voor de desbetreffende ervaring. Je wordt gevraagd de winnaar te bevestigen. Klik op **Ja** om de A/B-test te beëindigen.

Als u A als winnaar hebt gekozen, wordt de A/B-test stopgezet en gaat u verder, dan wordt alleen Experience A aan alle doelgroepen aangeboden.
