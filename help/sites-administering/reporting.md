---
title: Rapportage
seo-title: Rapportage
description: Leer hoe u met Rapporten in AEM werkt.
seo-description: Leer hoe u met Rapporten in AEM werkt.
uuid: eee4befd-5fa9-4ebc-8eea-56e1534a6b9b
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
discoiquuid: 7e2b30a3-75ff-4735-8038-5c5391ac36f3
docset: aem65
translation-type: tm+mt
source-git-commit: 4e5e6ef022dc9f083859e13ab9c86b622fc3d46e
workflow-type: tm+mt
source-wordcount: '2793'
ht-degree: 0%

---


# {#reporting} rapporteren

Om u te helpen de staat van uw instantie controleren en analyseren, verstrekt AEM een selectie van standaardrapporten, die voor uw individuele vereisten kunnen worden gevormd:

* [Componentrapport](#component-report)
* [Schijfgebruik](#disk-usage)
* [Health Check](#health-check)
* [Rapport Paginaactiviteit](#page-activity-report)
* [Rapport Door gebruiker gegenereerde inhoud](#user-generated-content-report)
* [Gebruikersrapport](#user-report)
* [Rapport voor werkstroominstantie](#workflow-instance-report)
* [Workflowrapport](#workflow-report)

Alle rapporten kunnen van **Tools** console worden betreden. Selecteer **Rapporten** in de linkerruit, dan klik het vereiste rapport in de juiste ruit tweemaal om het voor het bekijken en/of configuratie te openen.

De nieuwe instanties van een rapport kunnen ook van **Tools** console worden gecreeerd. Selecteer **Rapporten** in het linkerpaneel, dan **Nieuw..** op de werkbalk. Definieer een **Titel** en **Naam**, selecteer het gewenste rapporttype en klik vervolgens op **Maken**. Uw nieuwe rapportexemplaar zal in de lijst verschijnen. Dubbelklik op deze knop om deze te openen en sleep een component van de assistent om de eerste kolom te maken en de rapportdefinitie te starten.

>[!NOTE]
>
>Naast de standaard AEM rapporten die uit de doos beschikbaar zijn, kunt u [uw eigen (volledig nieuwe) rapporten ontwikkelen](/help/sites-developing/dev-reports.md).

## De grondbeginselen van de Aanpassing van het Rapport {#the-basics-of-report-customization}

Er zijn verschillende indelingen voor rapporten beschikbaar. De volgende rapporten allen gebruiken kolommen die zoals gedetailleerd in de volgende secties kunnen worden aangepast:

* [Componentrapport](#component-report)
* [Rapport Paginaactiviteit](#page-activity-report)
* [Rapport Door gebruiker gegenereerde inhoud](#user-generated-content-report)
* [Gebruikersrapport](#user-report)
* [Rapport voor werkstroominstantie](#workflow-instance-report)

>[!NOTE]
>
>De volgende rapporten hebben elk hun eigen formaat en aanpassing:
>
>
>* [Met Health ](#health-check) Checkuses worden selectievelden gebruikt om de gegevens op te geven waarover u wilt rapporteren.
>* [Schijfgebruik ](#disk-usage) maakt gebruik van koppelingen om naar beneden door de structuur van de opslagplaats te gaan.
>* [Workflowrapporten ](/help/sites-administering/reporting.md#workflow-report) geven een overzicht van de workflows die op uw exemplaar worden uitgevoerd.

>
>
De volgende procedures voor de kolomconfiguratie zijn dus niet geschikt. Zie de beschrijvingen van de afzonderlijke rapporten voor hun details.

### De gegevenskolommen selecteren en plaatsen {#selecting-and-positioning-the-data-columns}

Kolommen kunnen worden toegevoegd aan, verplaatst naar of verwijderd uit een van de rapporten, standaard of aangepast.

Het **lusje van Componenten** van sidekick (beschikbaar op de rapportpagina) maakt een lijst van alle categorieën gegevens die als kolommen kunnen worden geselecteerd.

De gegevensselectie wijzigen:

* als u een nieuwe kolom wilt toevoegen, sleept u de vereiste component van de zijkant naar de gewenste positie

   * een groene markering geeft aan wanneer de positie geldig is en een paar pijlen geven precies aan waar de positie wordt geplaatst
   * een rood niet-go symbool geeft aan wanneer de positie ongeldig is

* om een kolom te verplaatsen, klikt u op de koptekst, houdt u de muisknop ingedrukt en sleept u naar de nieuwe positie
* om een kolom te verwijderen, klik op de kolomtitel, houd en sleep omhoog in het gebied van de rapportkopbal (rood minus symbool zal erop wijzen dat de positie ongeldig is); Laat de muisknop los en in het dialoogvenster Component(s) verwijderen wordt bevestigd dat u de kolom echt wilt verwijderen.

### Vervolgkeuzemenu Kolom {#column-drop-down-menu}

Elke kolom in het rapport heeft een drop-down menu. Dit wordt zichtbaar wanneer de muiscursor over de cel van de kolomtitel beweegt.

Een pijlkop wordt helemaal rechts van de titelcel weergegeven (niet te verwarren met de pijlkop direct rechts van de titeltekst die het [huidige sorteermechanisme](#sorting-the-data) aangeeft).

![reportcolumnsort](assets/reportcolumnsort.png)

Welke opties beschikbaar zijn in het menu, is afhankelijk van de configuratie van de kolom (zoals die tijdens de projectontwikkeling is gemaakt). Eventuele ongeldige opties worden grijs weergegeven.

### De gegevens {#sorting-the-data} sorteren

De gegevens kunnen volgens een specifieke kolom worden gesorteerd door:

* klikken op de juiste kolomkop; bij het sorteren wordt geschakeld tussen oplopend en aflopend, hetgeen wordt aangegeven door een pijlkop direct naast de titeltekst
* gebruik het [vervolgkeuzemenu van de kolom](#column-drop-down-menu) om of **Sorteren Ascending** of **Sorteren Descending** specifiek te selecteren; nogmaals, dit wordt aangegeven met een pijlkop direct naast de titeltekst

### Groepen en het Huidige gegevensdiagram {#groups-and-the-current-data-chart}

Op aangewezen kolommen kunt u **Groeperen door deze kolom** van [de drop-down menu van de kolom ](#column-drop-down-menu) selecteren. Hiermee worden de gegevens gegroepeerd op basis van elke afzonderlijke waarde in die kolom. U kunt meerdere kolommen selecteren die u wilt groeperen. De optie wordt grijs weergegeven wanneer de gegevens in de kolom niet geschikt zijn. Dit betekent dat elke vermelding afzonderlijk en uniek is, zodat er geen groepen kunnen worden gevormd, bijvoorbeeld de kolom Gebruikersnaam van het gebruikersrapport.

Nadat ten minste één kolom is gegroepeerd, wordt een cirkeldiagram van **Huidige gegevens** gegenereerd op basis van deze groepering. Als er meerdere kolommen zijn gegroepeerd, wordt dit ook aangegeven in het diagram.

![verslaggever](assets/reportuser.png)

Als u de cursor op het cirkeldiagram plaatst, wordt de samengevoegde waarde voor het desbetreffende segment weergegeven. Hierbij wordt het aggregaat gebruikt dat momenteel voor de kolom is gedefinieerd; bijvoorbeeld aantal , minimum , gemiddelde , enz .

### Filters en aggregaten {#filters-and-aggregates}

Op aangewezen kolommen kunt u **de Montages van de Filter** en/of **Aggregates** van [drop-down menu ](#column-drop-down-menu) ook vormen.

#### Filters {#filters}

Met filterinstellingen kunt u de criteria opgeven voor items die moeten worden weergegeven. De beschikbare operatoren zijn:

* `contains`
* `equals`

![rapportfilter](assets/reportfilter.png)

Een filter instellen:

1. Selecteer de gewenste operator in de vervolgkeuzelijst.
1. Voer de tekst in waarop u wilt filteren.
1. Klik **Toepassen**.

Het filter deactiveren:

1. Verwijder de filtertekst.
1. Klik **Toepassen**.

#### Samengevoegde {#aggregates}

U kunt ook een aggregatiemethode selecteren (deze kan afhankelijk van de geselecteerde kolom variëren):

![verslaglegging](assets/reportaggregate.png)

### Kolomeigenschappen {#column-properties}

Deze optie is alleen beschikbaar wanneer de [Algemene kolom](#generic-column) is gebruikt in het [Gebruikersrapport](#user-report).

### Historische gegevens {#historic-data}

Een grafiek van de verandering in uw gegevens in tijd kan onder **Historische gegevens** worden gezien. Dit is afgeleid van momentopnamen die met regelmatige intervallen worden genomen.

Gegevens zijn:

* Verzameld door, indien beschikbaar, de eerste gesorteerde kolom, anders de eerste (niet-gegroepeerde) kolom
* Gegroepeerd door de desbetreffende kolom

Het rapport kan worden gegenereerd:

1. Stel **Groepering** in op de vereiste kolom.
1. **** Bewerk de configuratie om te bepalen hoe vaak de momentopnamen moeten worden gemaakt; uur of dag.
1. **Voltooien...** de definitie waarmee de verzameling van momentopnamen wordt gestart.

   De rode/groene schuifknop linksboven geeft aan wanneer momentopnamen worden verzameld.

Het resulterende diagram wordt rechtsonder weergegeven:

![verslaggeving](assets/reporttrends.png)

Nadat de gegevensverzameling is gestart, kunt u selecteren:

* **Periode**

   U kunt van en tot data voor de rapportgegevens selecteren om te tonen.

* **Interval**

   Maand, Week, Dag, Uur kan worden geselecteerd voor de schaal en de samenvoeging van het rapport.

   Als bijvoorbeeld dagelijkse momentopnamen beschikbaar zijn voor februari 2011:

   * Als het interval aan `Day` wordt geplaatst, wordt elke momentopname getoond als één enkele waarde in de grafiek.
   * Als het interval aan `Month` wordt geplaatst, worden alle momentopnamen voor Februari samengevoegd tot één enkele waarde (die als één enkele &quot;punt&quot;in de grafiek wordt getoond).

Selecteer uw vereisten, dan klik **Go** om hen op het rapport toe te passen. Als u de weergave wilt bijwerken nadat er meer momentopnamen zijn gemaakt, klikt u nogmaals op **Go**.

![chlimage_1-43](assets/chlimage_1-43.png)

Wanneer momentopnamen worden verzameld, kunt u:

* **Voltooien gebruiken..** opnieuw om de inzameling opnieuw te initialiseren.

   **Voltooi**  &quot;bevriest&quot;de structuur van het rapport (d.w.z. de kolommen toegewezen aan het rapport en die worden gegroepeerd, gesorteerd, gefiltreerd, enz.) en maakt momentopnamen.

* Open het dialoogvenster **Bewerken** om **Geen gegevensmomentopnamen** te selecteren om de verzameling te beëindigen totdat dit nodig is.

   **Met** Editonly schakelt u het maken van momentopnamen in of uit. Als het nemen van momentopnamen opnieuw wordt aangezet, gebruikt het de staat van het rapport toen het voor het laatst voor het nemen van verdere momentopnamen werd gebeëindigd.

>[!NOTE]
>
>Momentopnamen worden opgeslagen onder `/var/reports/...` waar de rest van de weg de weg van het respectieve rapport en identiteitskaart weerspiegelt die werd gecreeerd toen het rapport werd gebeëindigd.
>
>
>U kunt oude momentopnamen handmatig leegmaken als u er zeker van bent dat u deze instanties niet meer nodig hebt.

>[!NOTE]
>
>De vooraf geconfigureerde rapporten zijn niet prestatieintensief, maar het wordt nog steeds aanbevolen dagelijkse momentopnamen te gebruiken in een productieomgeving. Voer indien mogelijk deze dagelijkse momentopnamen uit op een tijdstip waarop er niet veel activiteit op uw website staat. dit kan worden bepaald met de `Daily snapshots (repconf.hourofday)` parameter voor **Day CQ Reporting Configuration**; zie [Configuratie OSGI](/help/sites-deploying/configuring-osgi.md) voor meer details over hoe te om dit te vormen.

#### Limieten {#display-limits} weergeven

Het historische gegevensrapport kan ook enigszins van uiterlijk veranderen als gevolg van limieten die kunnen worden ingesteld, afhankelijk van het aantal resultaten voor de geselecteerde periode.

Elke horizontale lijn is gekend als reeks (en beantwoordt aan een ingang in de grafieklegende), vertegenwoordigt elke verticale kolom van punten de bijeengevoegde momentopnamen.

![chlimage_1-44](assets/chlimage_1-44.png)

Om de kaart langer schoon te houden, kunnen er grenzen worden gesteld. Voor de standaardrapporten zijn deze:

* horizontale reeks - zowel standaard als systeemmaximum is `9`

* verticale samengevoegde momentopnamen - standaard is `35` (per horizontale reeks)

Wanneer de (passende) grenswaarden worden overschreden:

* de punten worden niet weergegeven
* de legenda voor de historische gegevenstabel zou een verschillend aantal ingangen aan dat van de huidige gegevensgrafiek kunnen tonen

![chlimage_1-45](assets/chlimage_1-45.png)

De aangepaste rapporten kunnen **Total** waarde voor alle reeksen ook tonen. Dit wordt getoond als reeks (horizontale lijn en ingang in de legenda).

>[!NOTE]
>
>Voor aangepaste rapporten kunnen de limieten anders worden ingesteld.

### Bewerken (rapport) {#edit-report}

Met de knop **Bewerken** opent u het dialoogvenster **Rapport bewerken**.

Dit is één plaats waar de periode voor het verzamelen van momentopnamen voor [Historische gegevens](#historic-data) wordt bepaald, maar diverse andere montages kunnen ook worden bepaald:

![gerapporteerd](assets/reportedit.png)

* **Titel**

   U kunt uw eigen titel definiëren.

* **Beschrijving**

   U kunt uw eigen beschrijving definiëren.

* **Hoofdpad**  (*alleen actief voor bepaalde rapporten*)

   Gebruik dit om het rapport te beperken tot een (sub-) sectie van de repository.

* **Rapportverwerking**

   * **gegevens automatisch vernieuwen**

      De rapportgegevens zullen worden vernieuwd telkens als u de rapportdefinitie bijwerkt.

   * **gegevens handmatig vernieuwen**

      Deze optie kan worden gebruikt om vertragingen te verhinderen die door automatisch worden veroorzaakt verfrist verrichtingen wanneer er een groot volume van gegevens is.

      Het selecteren van dit wijst erop dat de rapportgegevens manueel moeten worden verfrist wanneer om het even welk aspect van de rapportconfiguratie is veranderd. Het betekent ook dat zodra u om het even welk aspect van de configuratie verandert de rapportlijst zal worden gewist.

      Als deze optie is geselecteerd, wordt de knop **[Gegevens laden](#load-data)** weergegeven (naast **Bewerken** in het rapport). **De** gegevens van de lading zullen de gegevens laden en zullen de getoonde rapportgegevens verfrissen.

* ****
MomentopnamenU kunt bepalen hoe vaak momentopnamen moeten worden gemaakt; dagelijks, al dan niet per uur.

### Gegevens {#load-data} laden

De **knop Gegevens laden** is alleen zichtbaar wanneer **gegevens handmatig vernieuwen** is geselecteerd uit **[Bewerken](#edit-report)**.

![chlimage_1-46](assets/chlimage_1-46.png)

Als u op **Gegevens laden** klikt, worden de gegevens opnieuw geladen en wordt het weergegeven rapport bijgewerkt.

Als u selecteert om gegevens handmatig te vernieuwen, betekent dit dat:

1. Zodra u de rapportconfiguratie verandert, zal de lijst van rapportgegevens worden leeggemaakt.

   Als u bijvoorbeeld het sorteermechanisme voor een kolom wijzigt, worden de gegevens niet weergegeven.

1. Als u wilt dat de rapportgegevens opnieuw worden getoond zult u op **Gegevens van de Lading** moeten klikken om de gegevens opnieuw te laden.

### Voltooien (rapport) {#finish-report}

Wanneer u **Eindigt** het rapport:

* De rapportdefinitie *vanaf dat punt in tijd* zal voor het nemen van momentopnamen worden gebruikt (achteraf kunt u aan een rapportdefinitie blijven werken aangezien het dan van de momentopnamen gescheiden is).
* Eventuele bestaande momentopnamen worden verwijderd.
* Nieuwe momentopnamen worden verzameld voor de [Historische gegevens](#historic-data).

In dit dialoogvenster kunt u uw eigen titel en beschrijving voor het resulterende rapport definiëren of bijwerken.

![reportage](assets/reportfinish.png)

## Rapporttypen {#report-types}

### Componentrapport {#component-report}

Het componentenrapport bevat informatie over hoe uw website de componenten gebruikt.

[Kolommen met ](#selecting-and-positioning-the-data-columns) informatie over:

* Auteur
* Componentpad
* Componenttype
* Laatst gewijzigd
* Pagina

Het gemiddelde dat u kunt zien, bijvoorbeeld:

* Welke componenten worden gebruikt waar.

   Nuttig, bijvoorbeeld bij het testen.

* Hoe de instanties van een specifieke component worden verdeeld.

   Dit kan interessant zijn als specifieke pagina&#39;s (d.w.z. &quot;zware pagina&#39;s&quot;) ondervindt prestatieproblemen.

* Delen van de site identificeren met frequente/minder frequente wijzigingen.
* Zie hoe pagina-inhoud zich ontwikkelt in de loop van de tijd.

Alle componenten zijn inbegrepen, product-norm en project-specifiek. Met het dialoogvenster **Bewerken** kan de gebruiker ook een **basispad** instellen dat het startpunt van het rapport definieert. Alle componenten onder die hoofdmap worden beschouwd als voor het rapport.

![](assets/reportcomponent.png) ![reportComponentCompleteAll](assets/reportcompentall.png)

### Schijfgebruik {#disk-usage}

Het rapport van het schijfgebruik bevat informatie over de gegevens die in uw opslagplaats zijn opgeslagen.

Het rapport begint in de basis ( / ) van de gegevensopslagruimte; door op een bepaalde vertakking te klikken kunt u naar beneden boren in de repository (het huidige pad wordt weerspiegeld in de rapporttitel).

![verslaglegging](assets/reportdiskusage.png)

### Health Check {#health-check}

Dit rapport analyseert het huidige aanvraaglogboek:

`<cq-installation-dir>/crx-quickstart/logs/request.log`
om u te helpen de duurste aanvraag(en) binnen een bepaalde periode identificeren.

Om het rapport te produceren kunt u specificeren:

* **Periode (uren)**

   Het aantal uren (in het verleden) dat moet worden geanalyseerd.

   Standaard: `24`

* **max. Resultaten**

   Maximumaantal uitvoerlijnen.

   Standaard: `50`

* **max. Aanvragen**

   Maximumaantal te analyseren verzoeken.

   Standaard: `-1` (alle)

* **E-mailadres**

   Resultaten naar een e-mailadres verzenden.

   Optioneel; Standaard: blank

* **Dagelijks uitvoeren om (uu:mm)**

   Specificeer een tijd voor het rapport automatisch op een dagelijkse basis moet worden in werking gesteld.

   Optioneel; Standaard: blank

![verslaggeving](assets/reporthealth.png)

### Rapport voor paginaactiviteit {#page-activity-report}

Het pagina-activiteitenrapport bevat een overzicht van de pagina&#39;s en de acties die erop zijn uitgevoerd.

[Kolommen met ](#selecting-and-positioning-the-data-columns) informatie over:

* Pagina
* Time
* Type
* Gebruiker

Het gemiddelde dat u kunt controleren:

* De meest recente wijzigingen.
* Auteurs die aan specifieke pagina&#39;s werken.
* Pagina&#39;s die onlangs niet zijn gewijzigd, waardoor mogelijk actie nodig is.
* Pagina&#39;s die het meest of het minst vaak worden gewijzigd.
* Meest actieve of minst actieve gebruikers.

Het pagina activiteitenrapport neemt al zijn informatie van het controlelogboek. Door gebrek wordt de wortelweg gevormd aan het controlelogboek bij `/var/audit/com.day.cq.wcm.core.page`.

![rapportageActivity](assets/reportpageactivity.png)

### Door gebruiker gegenereerd inhoudsrapport {#user-generated-content-report}

Dit rapport bevat informatie over door gebruikers gegenereerde inhoud. Dit zijn opmerkingen, beoordelingen of forums.

[Kolommen met ](#selecting-and-positioning-the-data-columns) informatie over:

* Date
* IP-adres
* Pagina
* Referenter
* Type
* Gebruiker-id

Toestaan dat:

* Zie welke pagina&#39;s de meeste opmerkingen ontvangen.
* Bekijk een overzicht van alle opmerkingen die specifieke bezoekers van de site achterlaten. Mogelijk zijn de problemen gerelateerd.
* Realiseer of de nieuwe inhoud commentaren door te controleren veroorzaakt wanneer de commentaren op een pagina worden gemaakt.

![meltuserinhoud](assets/reportusercontent.png)

### Gebruikersrapport {#user-report}

Dit rapport bevat informatie over alle gebruikers die een account en/of profiel hebben geregistreerd. dit kan zowel auteurs binnen uw organisatie als externe bezoekers omvatten.

[Kolommen met informatie](#selecting-and-positioning-the-data-columns)  (indien beschikbaar) over:

* Leeftijd
* Land
* Domein
* E-mail
* Familienaam
* Geslacht
* [Algemeen](#generic-column)
* Voornaam
* Info
* Rente
* Taal
* NTLM-hashcode
* Gebruikersnaam

Toestaan dat:

* Bekijk de demografische spreiding van je gebruikers.
* Rapport over aangepaste velden die u aan de profielen hebt toegevoegd.

![verslaggeefster](assets/reportusercanned.png)

#### Algemene kolom {#generic-column}

De **Algemene** kolom is beschikbaar in het Rapport van de Gebruiker zodat u tot aangepaste informatie, gewoonlijk van [gebruikersprofielen](/help/sites-administering/identity-management.md#profiles-and-user-accounts) kunt toegang hebben; bijvoorbeeld [Favoriete kleur, zoals wordt beschreven onder Velden toevoegen aan de profieldefinitie](/help/sites-administering/identity-management.md#adding-fields-to-the-profile-definition).

Het dialoogvenster Algemene kolom wordt geopend wanneer u:

* Sleep de Algemene component van sidekick aan het rapport.
* Selecteer de Eigenschappen van de Kolom voor een bestaande Algemene kolom.

![meltusrgenericcolm](assets/reportusrgenericcolm.png)

Op het tabblad **Definities** kunt u definiëren:

* **Titel**

   Uw eigen titel voor de algemene kolom.

* **Eigenschap**

   De eigenschapsnaam zoals deze in de opslagplaats is opgeslagen, meestal binnen het profiel van de gebruiker.

* **Pad**

   Gewoonlijk wordt de eigenschap opgehaald uit de `profile`.

* **Type**

   Selecteer het veldtype uit `String`, `Number`, `Integer`, `Date`.

* **Standaard aggregaat**

   Dit bepaalt het aggregaat dat door gebrek wordt gebruikt als de kolom in een rapport met minstens één gegroepeerde kolom wordt ungrouped. Selecteer het vereiste aggregaat van `Count`, `Minimum`, `Average`, `Maximum`, `Sum`.

   *Count* betekent bijvoorbeeld voor een `String` veld dat het aantal afzonderlijke `String` waarden wordt weergegeven voor de kolom in de geaggregeerde status.

Op het tabblad **Uitgebreid** kunt u ook de beschikbare aggregaten en filters definiëren:

![meltusrgenericcolmextent](assets/reportusrgenericcolmextented.png)

### Rapport van workflowinstantie {#workflow-instance-report}

Dit geeft u een beknopt overzicht, verstrekkend informatie over de individuele instanties van werkschema&#39;s, zowel lopend als voltooid.

[Kolommen met ](#selecting-and-positioning-the-data-columns) informatie over:

* Voltooid
* Duur
* Initiator
* Model
* Payload
* Gestart
* Status

Meet u kunt:

* De gemiddelde duur van de workflows bewaken; als dit regelmatig gebeurt , kan het problemen met de workflow aan het licht brengen .

![rapportworkflowintentie](assets/reportworkflowintance.png)

### Workflow Report {#workflow-report}

Dit verstrekt zeer belangrijke statistieken over de werkschema&#39;s die op uw instantie lopen.

![rapportwerkstroom](assets/reportworkflow.png)

## Rapporten gebruiken in een publicatieomgeving {#using-reports-in-a-publish-environment}

Zodra u de rapporten aan uw specifieke vereisten hebt gevormd kunt u het activeren om de configuratie naar het publicatiemilieu over te brengen.

>[!CAUTION]
>
>Als u **Historische gegevens** voor het publicatiemilieu wilt, dan **beëindigt** het rapport over het auteursmilieu alvorens de pagina te activeren.

Het desbetreffende verslag is dan toegankelijk via

`/etc/reports`

Het door de gebruiker gegenereerde inhoudsrapport is bijvoorbeeld te vinden onder:

`http://localhost:4503/etc/reports/ugcreport.html`

Hiermee wordt nu verslag uitgebracht over gegevens die zijn verzameld uit de publicatieomgeving.

Aangezien geen rapportconfiguratie in het publicatiemilieu wordt toegestaan, zijn **Edit** en **Finish** knopen niet beschikbaar. Nochtans, kunt u **Period** en **Interval** voor **Historische gegevens** rapporten selecteren als de momentopnamen worden verzameld.

![verslaggeving](assets/reportsucgpublish.png)

>[!CAUTION]
>
>De toegang tot deze verslagen kan een veiligheidskwestie zijn; daarom raden we u aan de Dispatcher zo te configureren dat `/etc/reports` niet beschikbaar is voor externe bezoekers. Zie [Beveiligingschecklist](security-checklist.md) voor meer informatie.

## Machtigingen vereist voor het uitvoeren van rapporten {#permissions-needed-for-running-reports}

De benodigde machtigingen zijn afhankelijk van de handeling:

* De gegevens van het rapport worden hoofdzakelijk verzameld gebruikend de voorrechten van de huidige gebruiker.
* De historische gegevens worden verzameld gebruikend de voorrechten van de gebruiker die het rapport beëindigde.

In een standaard AEM installatie zijn de volgende toestemmingen vooraf ingesteld voor de rapporten:

* **Gebruikersrapport**

   `user administrators` - lezen en schrijven

* **Rapport Paginaactiviteit**

   `contributors` - lezen en schrijven

* **Componentrapport**

   `contributors` - lezen en schrijven

* **Rapport Door gebruiker gegenereerde inhoud**

   `contributors` - lezen en schrijven

* **Rapport voor werkstroominstantie**

   `workflow-users` - lezen en schrijven

Alle leden van de groep `administrators` hebben de noodzakelijke rechten om nieuwe rapporten tot stand te brengen.
