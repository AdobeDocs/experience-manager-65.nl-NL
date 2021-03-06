---
title: Statistieken weergeven met betrekking tot Werkbeheer
seo-title: Statistieken weergeven met betrekking tot Werkbeheer
description: Het lusje van de Manager van het Werk toont statistieken die op de punten van de Manager van het Werk betrekking hebben. Leer hoe u de werkitems kunt weergeven en filteren.
seo-description: Het lusje van de Manager van het Werk toont statistieken die op de punten van de Manager van het Werk betrekking hebben. Leer hoe u de werkitems kunt weergeven en filteren.
uuid: c3a575c7-773d-477a-bc75-6cbcf8b836b8
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 8e1b2f7c-2609-474b-a1b2-fa820df74ae3
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1241'
ht-degree: 0%

---


# Statistieken weergeven met betrekking tot Werkmanager {#view-statistics-related-to-work-manager}

Het lusje van de Manager van het Werk toont statistieken die op de punten van de Manager van het Werk betrekking hebben. Deze werkitems bevinden zich in verschillende staten, afhankelijk van waar ze zich bevinden. (Zie [Status (alleen voor de categorieën Standaard, Workflow of Gebeurtenissen)](view-statistics-related-manager.md#status-for-default-workflow-or-events-categories-only).) U kunt de informatie filteren om alleen een subset van de items weer te geven met de verschillende beschikbare opties (bijvoorbeeld Status of Categorie). U kunt het resulterende werk of baanpunten (in stijgende of dalende orde) sorteren door één van de kolomkopballen te klikken. Ook, kunt u de het werkpunten beheren door de verrichtingshulpmiddelen te gebruiken die boven de het werkpuntenlijst worden getoond.

## De werkitems filteren {#filter-the-work-items}

1. Klik op het tabblad Werkbeheer.
1. Selecteer de criteria voor een of meer van de hieronder beschreven filters en klik op Ga.

### Categorie {#category}

**Standaard:** alle werkitems waaraan de client geen categorie heeft toegewezen op het moment van verzending. De Manager van het werk beheert deze punten, daarom behoren de statussen tot de Manager van het Werk.

**Taakbeheer:** alle taken die bij Taakbeheer horen. Taakbeheer beheert zijn eigen taken en heeft een eigen taakstatus. Zie de specifieke taakstatussen die hieronder worden beschreven.

**Workflow:** Alle werkitems die bij de uitvoering van de workflow horen. De workflow beheert niet zijn eigen werkitems, maar is afhankelijk van de Werkmanager; daarom behoren de statussen tot de Manager van het Werk.

**Gebeurtenissen:** alle werkitems die bij Gebeurtenisbeheer horen. Gebeurtenisbeheer beheert niet zijn eigen werkitems, maar is afhankelijk van Werkmanager; daarom behoren de statussen tot de Manager van het Werk.

### Status (alleen voor de categorieën Standaard, Workflow of Gebeurtenissen) {#status-for-default-workflow-or-events-categories-only}

**Alles tonen:** geeft alle huidige werkitems weer.

**Gepland:** geeft alle werkitems weer die gereed zijn voor uitvoering door de toepassingsserver, maar nog niet zijn gestart.

**Gepauzeerd:** geeft alle geplande werkitems weer die de clienttoepassing heeft gepauzeerd. Deze items kunnen worden uitgevoerd of verwijderd. (Zie De werkitems of taken beheren.)

**Bezig:** geeft alle werkitems weer die de werkmanager van de toepassingsserver heeft opgepakt en die worden voltooid of gezakt. U kunt geen bewerkingen op deze werkitems gebruiken.

**Voltooien:** Geeft alle werkitems weer die met succes zijn uitgevoerd. De blijvende het werkpunten blijven in deze staat en de niet-blijvende punten worden geschrapt na voltooiing van callbacks aan de callback managers. U kunt deze items verwijderen met de bewerking Items verwijderen. (Zie De werkitems of taken beheren.)

**Mislukt:** Hiermee worden alle werkitems weergegeven die niet zijn voltooid vanwege een fout. Deze werkitems kunnen een paar keer opnieuw worden geprobeerd met de bewerking Items opnieuw proberen. (Zie De werkitems of taken beheren.) Een verbinding van de Mislukking in de kolom van de Status staat u toe om tot details over de mislukking toegang te hebben.

**Onbekend:** Hiermee worden alle werkitems weergegeven waarvan de status onbekend is.

### Status (alleen voor de categorie Taakbeheer) {#status-for-job-manager-category-only}

**Voltooid:** Hiermee geeft u alle taken weer die met succes zijn uitgevoerd. De blijvende het werkpunten blijven in deze staat en de niet-blijvende punten worden geschrapt na voltooiing van callbacks aan de callback managers.

**Voltooid aangevraagd:** Hiermee geeft u taken weer waarvoor een volledige aanvraag is ingediend.

**Mislukt aangevraagd:** geeft taken weer waarvoor een mislukte aanvraag is ingediend.

**Mislukt:** Hiermee geeft u taken weer die niet zijn voltooid vanwege een fout. Een verbinding van de Mislukking in de kolom van de Status staat u toe om tot details over de mislukking toegang te hebben.

**Beëindig Gevraagd:** Toont banen waarvoor een beëindigingsverzoek werd gemaakt.

**Beëindigd:** Hiermee geeft u taken weer die zijn beëindigd zonder te voltooien.

**Opgeschort aangevraagd:** Hiermee geeft u taken weer waarvoor een opschortingsverzoek is ingediend.

**Opgeschort:** Hiermee worden taken weergegeven die zijn opgeschort.

**Hervatten aangevraagd:** Hiermee geeft u taken weer waarvoor een hervattingsverzoek is ingediend.

**In wachtrij:** geeft taken weer die zich in de wachtrij bevinden.

**Wordt uitgevoerd:** geeft taken weer die worden uitgevoerd.

### Servernaam {#server-name}

Alleen voor geclusterde servers selecteert u de naam van het knooppunt om de werkitems of taakitems weer te geven die alleen op die server zijn gemaakt. Als Alles tonen is geselecteerd, worden alle werkitems voor alle knooppunten in een cluster weergegeven.

### Tijd maken {#create-time}

Selecteer een optie in dit filter om alleen die werkitems weer te geven die zijn gemaakt binnen de tijdlijn die u selecteert. Als u bijvoorbeeld 1 dag selecteert, worden alle werkitems weergegeven die zijn gemaakt binnen 24 uur vóór de tijd die is ingesteld in het filter Voor.

### Vóór {#prior-to}

Hiermee stelt u de datum en tijd in die het filter Tijd maken als einddatum gebruikt. Houd de optie Huidige datum en tijd gebruiken geselecteerd om terug te filteren vanaf de huidige datum en tijd, of schrap de optie en ga de aangewezen waarden in. Klik op de kalenderpictogrammen of de klokpictogrammen om waarden te selecteren met deze gereedschappen.

Als u bijvoorbeeld Tijd maken = 1 dag en vóór = Huidige datum en tijd gebruiken selecteert, worden alle werkitems geretourneerd die in de laatste 24 uur zijn gemaakt.

>[!NOTE]
>
>Bij Oracle-databaseimplementaties werken de datumbereikfilters (dat wil zeggen Tijd maken en Voor instellingen) niet correct. Gebruik een ander filter om de werkitems op te halen.

## Informatie over de interface {#about-the-work-manager-tab-interface} op het tabblad Werkbeheer

Wanneer u een vraag van de Manager van het Werk in werking stelt of een verrichting op een het werkpunt of baan uitvoert, verschijnt een bericht boven de lijst. Dit bericht bevat feedback over de actie die u hebt gestart en in sommige gevallen een koppeling Meer informatie voor meer informatie. Als de bewerking die u hebt gestart bijvoorbeeld is mislukt, wordt in het bericht zoveel vermeld en wordt een koppeling weergegeven om details over de fout op te halen.

Wanneer u op Meer informatie klikt, wordt in het dialoogvenster Bewerkingsdetails een lijst weergegeven met de werkitems of taken die tijdens de bewerking zijn geselecteerd. U kunt op elk lijstitem klikken om de foutdetails onder in het dialoogvenster weer te geven.

### De werkitems of taken beheren {#manage-the-work-items-or-jobs}

1. Gebruik de hieronder beschreven bewerkingsgereedschappen om de werkitems of taken in de lijst te beheren.

   >[!NOTE]
   >
   >De verrichtingen zijn beschikbaar afhankelijk van de status van het punt.

   **Items verwijderen:het geselecteerde werkitem of de geselecteerde taak** verwijderen.

   **Pauzeeritems:** Pauzeert het geselecteerde werkitem of de geselecteerde taak.

   **Items hervatten:** Hiermee hervat u het geselecteerde werkitem of de geselecteerde taak vanaf de gepauzeerde status.

   **Opnieuw items proberen:** probeert het geselecteerde werkitem of de geselecteerde taak opnieuw uit te voeren vanaf de huidige status.

   U kunt controleren of een bewerking is gelukt door boven de lijst op Meer informatie te klikken. Er wordt een dialoogvenster weergegeven met de geselecteerde werkitems of -taken en hun status.

## Aanvullende informatie over de status van werkitems {#additional-information-about-work-item-statuses}

Doorgaans bestaat een statusovergang voor een tijdelijk item uit Nieuw > Gepland > Bezig > Voltooid of Mislukt.

De pauzestatus onderbreekt deze normale stroom. De clienttoepassing of de systeembeheerder kan deze onderbreking starten (bijvoorbeeld voor onderhoud of upgrade). U kunt deze actie terugkeren door de verrichting van het Hervatten te gebruiken om het het werkpunt terug naar een Geplande staat te bewegen.

Een het werkpunt in een Geplande staat wordt een rij gevormd voor uitvoering die nog niet is begonnen. Deze items kunnen worden gepauzeerd of verwijderd of worden verplaatst naar de status In uitvoering wanneer de werkmanager ze uit de wachtrij haalt. Werkitems die in uitvoering zijn, kunnen niet worden gewijzigd. Ze zullen ofwel voltooid zijn of mislukken.

De staat Mislukt treedt als resultaat van een foutenvoorwaarde die tijdens de uitvoering van het het werkpunt voorkomt. Als u vermoedt dat fouten indirect zijn (vanwege de context op het moment van uitvoering), kunt u de uitvoering opnieuw proberen en het werkitem weer in de wachtrij plaatsen. Slechts een beperkt aantal pogingen is toegestaan.
