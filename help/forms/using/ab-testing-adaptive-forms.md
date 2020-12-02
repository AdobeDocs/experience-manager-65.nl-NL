---
title: A/B-test voor adaptieve formulieren maken en beheren
seo-title: A/B-test voor adaptieve formulieren maken en beheren
description: AEM Forms integreert met Adobe Target, waardoor A/B-tests kunnen worden uitgevoerd voor adaptieve formulieren om de ervaring van klanten te verbeteren en de conversiesnelheden te verbeteren.
seo-description: AEM Forms integreert met Adobe Target, waardoor A/B-tests kunnen worden uitgevoerd voor adaptieve formulieren om de ervaring van klanten te verbeteren en de conversiesnelheden te verbeteren.
uuid: e258805c-4da8-4c5d-ae91-7bea78a6a71b
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: integrations
discoiquuid: 8f776f30-ff93-4d19-94c6-c4bfe6f1fae2
docset: aem65
translation-type: tm+mt
source-git-commit: 3eaace94bc0499aaebfcd389d4dc97b97c7d9160
workflow-type: tm+mt
source-wordcount: '1581'
ht-degree: 0%

---


# A/B-test voor adaptieve formulieren maken en beheren{#create-and-manage-a-b-test-for-adaptive-forms}

## Overzicht {#overview-br}

Uw klanten zullen waarschijnlijk een formulier verlaten als de ervaring die het biedt, niet aantrekkelijk is. Hoewel het voor de klanten frustrerend is, kan het het steunvolume en de kosten voor uw organisatie ook herstellen. Het is kritiek evenals uitdagend om de juiste klantenervaring te identificeren en te verstrekken die de omrekeningskoers verhoogt. Adobe Experience Manager Forms heeft de sleutel tot dit probleem.

AEM Forms integreert met Adobe Target, een Adobe Marketing Cloud-oplossing, om persoonlijke en aantrekkelijke klantervaringen op verschillende digitale kanalen te bieden. Een van de belangrijkste mogelijkheden van Target is A/B-tests waarmee u snel gelijktijdige A/B-tests kunt instellen, relevante inhoud voor de beoogde gebruikers kunt presenteren en de ervaring kunt identificeren die een betere conversiesnelheid mogelijk maakt.

Met AEM Forms kunt u A/B-tests instellen en uitvoeren op adaptieve formulieren in real-time. Het biedt ook offline en aanpasbare rapportagemogelijkheden om de prestaties in real-time van uw formulierervaringen te visualiseren en het systeem te identificeren dat de betrokkenheid en conversie van gebruikers maximaliseert.

## Doel instellen en integreren in AEM Forms {#set-up-and-integrate-target-in-aem-forms}

Voordat u A/B-tests gaat maken en analyseren op adaptieve formulieren, moet u de doelserver instellen en integreren in AEM Forms.

### Doel instellen {#set-up-target}

Zorg ervoor dat u een geldig Adobe Target-account hebt om AEM met Target te integreren. Wanneer u zich bij Adobe Target registreert, ontvangt u een clientcode. U hebt de clientcode, de e-mail die aan de Target-account is gekoppeld en het wachtwoord nodig om verbinding te maken AEM met Target.

De clientcode identificeert de Adobe Target-klantenaccount en wordt gebruikt als een subdomein in de URL wanneer de Adobe Target-server wordt aangeroepen. Voordat u verdergaat, moet u ervoor zorgen dat u zich bij [https://testandtarget.omniture.com/](https://testandtarget.omniture.com/) kunt aanmelden.

### Doel integreren in AEM Forms {#integrate-target-in-aem-forms}

Voer de volgende stappen uit om een actieve doelserver te integreren met AEM Forms:

1. Ga op AEM server naar https://&lt;*hostnaam*>:&lt;*port*>/libs/cq/core/content/tools/cloudservices.html.

1. Klik in de sectie **Adobe Target** op **Configuraties tonen** en vervolgens op het pictogram **+** om een nieuwe configuratie toe te voegen.
Als u doel voor het eerst vormt, klik **nu vormen.**

1. In de Create configuratiedialoog, specificeer **Titel** en naar keuze een **Naam** voor de configuratie.

1. Klik **Maken**. Het dialoogvenster Component bewerken wordt geopend.
1. Geef de gegevens van uw doelaccount op, zoals clientcode, e-mail en wachtwoord.
1. Selecteer **Rest** van de drop-down lijst van het Type API.

1. Klik **Verbinding maken met Adobe Target** om de verbinding met Doel te initialiseren. Als de verbinding succesvol is, wordt het bericht Verbinding succesvol getoond. Klik **OK** op het bericht en dan **OK** op het dialoogvenster. De doelaccount is geconfigureerd.

1. Maak een doelframework zoals beschreven in [Een framework toevoegen](/help/sites-administering/target.md).

1. Ga naar https://&lt;*hostnaam*>:&lt;*poort*/system/console/configMgr.

1. Klik **AEM Forms Target Configuration**.
1. Selecteer een **Doelframework**.
1. Geef in het veld **Doel-URL&#39;s** alle URL&#39;s op waarop A/B-tests worden uitgevoerd. Bijvoorbeeld https://&lt;*hostnaam*:&lt;*port*>/ voor AEM Forms-server op OSGi of https://&lt;*hostnaam*>:&lt;*port*/lc/ voor AEM Forms-server op JEE.
Bedenk dat u een Doel URL voor een publicatieinstantie wilt vormen en uw klanten tot het kunnen toegang hebben gebruikend hostname of het IP adres, zult u zowel als Doel URLs moeten vormen - gebruikend hostname evenals het IP adres. Als u slechts één van URLs vormt, zal uw test A/B niet lopen voor klanten die van andere URL komen. Klik **+** om veelvoudige URLs te specificeren.

1. Klik **Opslaan**.

Uw doelserver is geïntegreerd met AEM Forms. U kunt nu A/B-tests inschakelen als u een volledige licentie hebt om Adobe Target te gebruiken.

Als u een volledige licentie hebt om Adobe Target te gebruiken, start u de server met de volgende parameters nadat u Target hebt geïntegreerd met AEM Forms:

`parameter -Dabtesting.enabled=true java -Xmx2048m -XX:MaxPermSize=512M -jar -Dabtesting.enabled=true`

Als de AEM instantie op JBoss loopt, begonnen als dienst van turnkey, in `jboss\bin\standalone.conf.bat` dossier, add-Dabtesting.enabled=true parameter in de volgende ingang:

`set "JAVA_OPTS=%JAVA_OPTS% -Dadobeidp.serverName=server1 -Dfile.encoding=utf8 -Djava.net.preferIPv4Stack=true -Dabtesting.enabled=true"`

Naast de jreliëfserver kunt u ook het jvm-argument Dabtesting.enabled=true toevoegen in het opstartscript van de server voor elke toepassingsserver. U kunt nu A/B-tests maken en uitvoeren voor adaptieve formulieren.

>[!NOTE]
>
>Als u gevormde Doel URLs later bijwerkt, zorg ervoor dat u om het even welke lopende tests A/B bijwerkt zodat zij aan huidige URLs richten. Zie [A/B-test bijwerken](/help/forms/using/ab-testing-adaptive-forms.md#p-update-a-b-test-p) voor informatie over het bijwerken van A/B-tests.


## Soorten publiek maken binnen AEM {#create-audiences-within-aem}

Met AEM kunt u een publiek maken en dit gebruiken voor een A/B-test. Het publiek dat u binnen AEM maakt, is beschikbaar in AEM Forms. Voer de volgende stappen uit om een publiek te maken binnen AEM:

1. Tik in ontwerpinstantie op **Adobe Experience Manager** > **Personalisatie** > **Soorten publiek**.

1. Tik op de pagina Soorten publiek op **Soorten publiek maken > Doelpubliek maken**.
1. Selecteer een doelconfiguratie in het dialoogvenster Adobe Target-configuratie en klik op **OK**.
1. Maak regels op de pagina Nieuw publiek maken. Met regels kunt u het publiek indelen. U wilt bijvoorbeeld soorten publiek categoriseren op basis van het besturingssysteem. Uw publiek A komt van Vensters, en publiek B komt van Linux.

   1. Om publiek te categoriseren dat op Vensters, in Regel 1 wordt gebaseerd, selecteer **OS** kenmerktype. Van wanneer drop-down, uitgezochte **Vensters.**

   1. Als u een publiek wilt categoriseren op basis van Linux, selecteert u in Regel 2 het kenmerktype **OS**. Selecteer **Linux** in de vervolgkeuzelijst **When** en klik op **Next**.

1. Geef een naam voor het gemaakte publiek op en klik op **Opslaan**.

U kunt de doelgroep selecteren wanneer u A/B-tests voor een formulier configureert, zoals hieronder wordt weergegeven.

## A/B-test maken {#create-a-b-test}

Voer de volgende stappen uit om een A/B-test voor een adaptief formulier te maken.

1. Ga naar **Forms &amp; Documents** op https://&lt;*hostnaam*:&lt;*port*>/aem/forms.html/content/dam/formsanddocuments.

1. Navigeer naar de map met het adaptieve formulier.
1. Klik op het gereedschap **Selecteer** op de werkbalk en selecteer het aangepaste formulier.
1. Klik **Meer** in toolbar en selecteer **A/B het Testen** vormen. De Configure A/B testende pagina opent.

[ ![A/B testconfiguratiepagina voor adaptieve formulieren](assets/ab-test-configure.png)](assets/ab-test-configure-1.png)

1. Geef een **Naam activiteit** op voor de A/B-test.

1. Selecteer in de vervolgkeuzelijst Publiek een publiek voor wie u verschillende ervaringen met het formulier wilt gebruiken. Bijvoorbeeld **Bezoekers die Chrome** gebruiken. De publiekslijst wordt bevolkt van de gevormde server van het Doel.

1. Geef in de velden **Experience Distribution** voor ervaringen A en B de spreiding in procenten op om de verdeling van ervaringen onder het totale publiek te bepalen. Als u bijvoorbeeld 40, 60 opgeeft voor respectievelijk de ervaringen A en B, zal de ervaring A worden benut voor 40% van het publiek en zal de resterende 60% de ervaring B zien.
1. Klik **Configure**. Er verschijnt een dialoogvenster waarin de aanmaak van de A/B-test wordt bevestigd.
1. Klik op **Ervaring B** bewerken om het adaptieve formulier te openen in de bewerkingsmodus. Wijzig het formulier om een andere ervaring op te doen dan de standaardeigenschap A. De mogelijke variaties die in ervaring B zijn toegestaan, zijn veranderingen in:

   * CSS of opmaak
   * Volgorde van velden in verschillende deelvensters of in hetzelfde deelvenster
   * Deelvensterlay-out
   * Deelvenstertitels
   * Beschrijving, label en Help-tekst voor een veld
   * Scripts die geen invloed hebben op of een einde maken aan de verzendstroom
   * Validaties (zowel client als server)
   * Thema voor ervaring B. (U kunt een ander thema selecteren voor ervaring B)

1. Ga naar de gebruikersinterface van Forms en Documenten, selecteer het adaptieve formulier, klik op **Meer** en selecteer **A/B Testing starten**.

De A/B-test wordt nu uitgevoerd en het opgegeven publiek wordt op willekeurige wijze aangeboden op basis van de opgegeven distributie.

## A/B-test bijwerken {#update-a-b-test}

U kunt het publiek bijwerken en verspreidingen van een lopende test A/B ervaren. Daartoe:

1. Navigeer in de gebruikersinterface van Forms en documenten naar de map met het adaptieve formulier waarop de A/B-test wordt uitgevoerd.
1. Selecteer het adaptieve formulier.
1. Klik **Meer** en selecteer **A/B-tests bewerken**. De testpagina A/B bijwerken wordt geopend.

1. Werk het publiek en ervaringsprestaties bij, indien nodig.
1. Klik **Update**.

## A/B-testrapport {#view-and-analyze-a-b-test-report} weergeven en analyseren

Zodra u de A/B test hebt toegestaan om voor de gewenste periode te lopen, kunt u een rapport produceren en controleren welke ervaring in betere omzetting heeft geresulteerd. U kunt de beter presterende ervaring declareren als winnaar of een andere A/B-test uitvoeren. Voer hiertoe de volgende stappen uit:

1. Selecteer het adaptieve formulier, klik op **Meer** en klik vervolgens op **A/B-testrapport**. Het rapport wordt weergegeven.

[ ![A/B Testrapport](assets/ab-test-report-2.png)](assets/ab-test-report-3.png)

1. Analyseer het rapport en controleer of u genoeg gegevenspunten hebt om één van de beter presterende ervaringen als winnaar te verklaren. U kunt ervoor kiezen om dezelfde A/B-test langer te blijven uitvoeren of een winnaar te declareren en de A/B-test te beëindigen.
1. Als u een winnaar wilt declareren en de A/B-test wilt beëindigen, klikt u op de knop **A/B-test beëindigen** op het rapportagedashboard. In een dialoogvenster wordt u gevraagd een van de twee ervaringen als winnaar op te geven. Kies een winnaar en bevestig om de A/B-test te beëindigen.
U kunt ook eerst een winnaar declareren door op de knop **Winner declareren** voor de desbetreffende ervaring te klikken. Je wordt gevraagd de winnaar te bevestigen. Klik **Ja** om de A/B-test te beëindigen.

Als u A als winnaar hebt gekozen, wordt de A/B-test stopgezet en gaat u verder, dan wordt alleen Experience A aan alle doelgroepen aangeboden.
