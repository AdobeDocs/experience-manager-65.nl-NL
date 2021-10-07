---
source-git-commit: 99d38dddbcd06fecb82c744d446b9cef981e0781
workflow-type: tm+mt
source-wordcount: '753'
ht-degree: 4%

---
# Richtlijnen voor het bijdragen aan de documentatie van Adobe Experience Manager

## Documentatiefilosofie

We weten dat Adobe Experience Manager-gebruikers werken in zeer concurrerende omgevingen en streven naar het creëren van digitale ervaringen die hen onderscheiden van hun concurrenten. Daarom is het van essentieel belang dat wanneer Adobe geavanceerde nieuwe hulpmiddelen in AEM levert, deze hulpmiddelen met nauwkeurige en duidelijke documentatie worden aangevuld om de klant toe te staan om hun AEM investering onmiddellijk te hefboomwerking en het rendement te maximaliseren.

Het doel van de AEM is zo snel mogelijk documentatie in de handen van AEM gebruikers te plaatsen. Daarom geven wij prioriteit aan nauwkeurige, bruikbare documentatie en streven wij ernaar deze voortdurend bij te werken en te verbeteren.

## Documentatiebijdragen

Met het oog op de voortdurende verbetering van AEM documentatie is de hele gemeenschap van AEM gebruikers welkom om bij te dragen aan de documentatie. Of het door trekkingsverzoeken of kwesties, de verbeteringen van de documentatie kunnen correcties, verduidelijkingen, uitbreidingen, en extra voorbeelden zijn.

## Documentatienormen

Hoewel wij blij zijn met de bijdragen aan onze documentatie, moet elke bijdrage aan de AEM documentatie, in de vorm van een pull-verzoek of een kwestie, in overeenstemming zijn met onze bijdrage- en documentatienormen.

Bijdragen die niet aan deze normen voldoen, kunnen worden afgewezen.

### We documenteren standaardgebruiksgevallen.

AEM documentatie behandelt standaardgebruikscenario&#39;s. Gebruiksgevallen die buiten het bereik van de standaardinstallatie en het standaardgebruik van het product vallen, maken geen deel uit van AEM documentatie.

### In het algemeen documenteren we geen bugs of hun aanraakpunten.

AEM documentatie behandelt standaardgebruikscenario&#39;s. Daarom worden bugs, effecten die door bugs worden veroorzaakt en tijdelijke oorzaken voor bugs over het algemeen niet gedocumenteerd.

De uitzonderingen op deze regel zijn op de versienota&#39;s van toepassing waar de bekende kwesties met mogelijke oplossingen kunnen worden vermeld die door AEM Beheer van het Product zijn goedgekeurd.

### De bijdragen van de documentatie zijn niet voor het beantwoorden van technische vragen.

Alle ideeën die u eventueel nodig hebt om AEM documentatie te verbeteren, zijn welkom als bijdragen. Opmerkingen, problemen en pull-aanvragen zijn echter alleen bedoeld voor *bijdragen*. Ze zijn niet bedoeld om u te helpen uw vragen te beantwoorden over het gebruik van AEM, het implementeren van uw AEM-project of het oplossen van technische problemen.

Vragen over het gebruik van AEM of technische fouten die u mogelijk hebt gemaakt, moeten via het normale supportproces worden gerapporteerd via het [portal voor ondersteuning van Experience Managers](https://experienceleague.adobe.com/?support-solution=Experience+Manager#support) of worden besproken in de [community voor Experience Managers](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community).

***AEM documentatiebijdragen zijn geen vervanging voor*** Klantenondersteuning en dergelijke bijdragen die antwoorden op supportgerelateerde vragen zoeken, zullen worden afgewezen.

### Bijdragen moeten duidelijk verwijzen naar betrokken documentatiepagina&#39;s.

Als u een probleem maakt om verbeteringen in de documentatie voor te stellen, moet u koppelingen naar de betrokken pagina&#39;s opnemen. Als u een probleemmelding maakt met de koppeling **Deze pagina bewerken** op een documentatiepagina, wordt de probleemmelding automatisch gemaakt met een koppeling naar de pagina.

Dit is niet van toepassing op trekkingsverzoeken aangezien trekkingsverzoeken door hun aard verwijzen naar de betrokken pagina(&#39;s).

## Documentatierichtlijnen

Wij vragen dat bij alle bijdragen aan onze documentatie bepaalde stijlrichtlijnen worden gevolgd.

Door deze richtlijnen te volgen wordt de revisie van uw bijdrage gemakkelijker en daarom is integratie in onze documentatie sneller.

### Taal en stijl

#### Taal

* AEM documentatie is geschreven en onderhouden in het Engels van de VS.
* Zin zo eenvoudig mogelijk houden.
* Houd de taal duidelijk en beknopt.

Alle lezers van AEM documentatie zijn wereldwijd en kunnen niet verwachten dat ze native of vloeiende Engelstalige luidsprekers zijn. Vermijd colloquialisme en houd de taal zo duidelijk en eenvoudig mogelijk.

#### Handleiding Microsoft volgen

[De Microsoft Manual of ](https://docs.microsoft.com/en-us/style-guide/welcome/) Style is een vrij beschikbare documentatiestijlgids die zich concentreert op softwaredocumentatie en AEM documentatie volgt deze gids waar mogelijk.

### Opmaak

| Item | Stijl |
|---|---|
| UI-element of -optie | **vet** |
| Bestandsnaam, pad, gebruikersinvoer, parameterwaarden | `monospaced` |
| Code, opdrachtregel | ```Code Block``` |

### Schermpresentaties

Schermopnamen moeten met de nodige voorzichtigheid worden gebruikt en alleen wanneer een tekstbeschrijving niet volstaat.

Markeertekens of andere annotaties in schermafbeeldingen (zoals rode kaders, pijlen of tekst) mogen niet worden gebruikt. Op deze manier zijn de schermafbeeldingen gemakkelijker te hergebruiken of te repliceren in gelokaliseerde versies van de documentatie.

### Versiespecifieke verwijzingen

Probeer zo veel mogelijk directe verwijzingen naar een specifieke versie in de documentatie te voorkomen. Dit maakt de documentatie flexibeler en verlengbaar voor toekomstige versies.

### Gebruik van Dag, AEM, CQ, CRX

Voor het eerst in een artikel moet altijd naar het product worden verwezen met de volledige naam **Adobe Experience Manager** en kan daarna worden verwezen naar **AEM**.

De software van de dag, de Dag, CQ, en CRX zouden niet moeten worden gebruikt behalve waar onvermijdbaar zoals in klassennamen of verwijzend naar de geschiedenis van AEM.