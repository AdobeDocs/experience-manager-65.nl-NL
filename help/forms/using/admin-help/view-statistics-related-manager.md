---
title: Statistieken weergeven met betrekking tot Werkbeheer
description: Het lusje van de Manager van het Werk toont statistieken die op de punten van de Manager van het Werk betrekking hebben. Leer hoe u de werkitems kunt weergeven en filteren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: ce8f7257-bb9a-428d-b816-27b1d1632ee1
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '1215'
ht-degree: 0%

---

# Statistieken weergeven met betrekking tot Werkbeheer {#view-statistics-related-to-work-manager}

Het lusje van de Manager van het Werk toont statistieken die op de punten van de Manager van het Werk betrekking hebben. Deze werkitems bevinden zich in verschillende staten, afhankelijk van waar ze zich bevinden. (Zie [ Status (voor Standaard, Werkschema, of de categorieën van Gebeurtenissen slechts) ](view-statistics-related-manager.md#status-for-default-workflow-or-events-categories-only).) U kunt de informatie filteren om alleen een subset van de items weer te geven met de verschillende beschikbare opties (bijvoorbeeld Status of Categorie). U kunt het resulterende werk of baanpunten (in stijgende of dalende orde) sorteren door één van de kolomkopballen te klikken. Ook, kunt u de het werkpunten beheren door de verrichtingshulpmiddelen te gebruiken die boven de het werkpuntenlijst worden getoond.

## De werkitems filteren {#filter-the-work-items}

1. Klik op het tabblad Werkbeheer.
1. Selecteer de criteria voor een of meer van de hieronder beschreven filters en klik op Ga.

### Categorie {#category}

**Gebrek:** Alle het werkpunten die de cliënt geen categorie aan toewees toen zij werden voorgelegd. De Manager van het werk beheert deze punten, daarom behoren de statussen tot de Manager van het Werk.

**Manager van de Baan:** Alle banen die tot de Manager van de Baan behoren. Taakbeheer beheert zijn eigen taken en heeft een eigen taakstatus. Zie de specifieke taakstatussen die hieronder worden beschreven.

**Werkschema:** Alle het werkpunten die tot de uitvoering van het Werkschema behoren. De workflow beheert geen eigen werkitems, maar is afhankelijk van de Werkmanager. Daarom behoren de status toe aan de werkmanager.

**Gebeurtenissen:** Alle het werkpunten die tot het Beheer van de Gebeurtenis behoren. Gebeurtenisbeheer beheert geen eigen werkitems, maar is afhankelijk van Werkmanager. Daarom behoren de status toe aan Werkbeheer.

### Status (alleen voor de categorieën Standaard, Workflow of Gebeurtenissen) {#status-for-default-workflow-or-events-categories-only}

**toon allen:** toont alle huidige het werkpunten.

**Gepland:** toont alle het werkpunten klaar voor uitvoering door de toepassingsserver maar nog niet begonnen.

**Gepauzeerd:** toont alle geplande het werkpunten die de cliënttoepassing heeft gepauzeerd. Deze items kunnen worden uitgevoerd of verwijderd. (Zie De werkitems of taken beheren.)

**Bezig:** toont alle het werkpunten die de Manager van het Werk van de toepassingsserver opnam en of volledig of zal ontbreken. U kunt geen bewerkingen op deze werkitems gebruiken.

**Voltooid:** toont alle het werkpunten die met succes uitvoerden. De blijvende het werkpunten blijven in deze staat en de niet-blijvende punten worden geschrapt na voltooiing van callbacks aan de callback managers. U kunt deze items verwijderen met de bewerking Items verwijderen. (Zie De werkitems of taken beheren.)

**Ontbroken:** toont alle het werkpunten die niet met succes wegens een foutenvoorwaarde voltooiden. Deze werkitems kunnen een paar keer opnieuw worden geprobeerd met de bewerking Items opnieuw proberen. (Zie De werkitems of taken beheren.) Met een koppeling Mislukt in de kolom Status hebt u toegang tot details over de fout.

**Onbekend:** toont alle het werkpunten de waarvan status onbekend is.

### Status (alleen voor de categorie Taakbeheer) {#status-for-job-manager-category-only}

**Voltooid:** toont alle banen die met succes hebben uitgevoerd. De blijvende het werkpunten blijven in deze staat en de niet-blijvende punten worden geschrapt na voltooiing van callbacks aan de callback managers.

**Volledig Gevraagd:** de banen van vertoningen waarvoor een volledig verzoek werd gemaakt.

**Gevraagde Mislukt:** de banen van vertoningen waarvoor een mislukkingsverzoek werd gemaakt.

**Ontbroken:** de banen van vertoningen die niet met succes wegens een foutenvoorwaarde voltooiden. Met een koppeling Mislukt in de kolom Status hebt u toegang tot details over de fout.

**beëindigt Gevraagde:** banen van vertoningen waarvoor een beëindigingsverzoek werd gemaakt.

**beëindigde:** banen van vertoningen die zonder de voltooiing beëindigden.

**Gevraagde Opschorting:** banen van vertoningen waarvoor een opschortingsverzoek werd gemaakt.

**opgeschort:** de banen van vertoningen die worden opgeschort.

**Gevraagde Hervatting:** banen van vertoningen waarvoor een hervattingsverzoek werd gemaakt.

**in een rij opgenomen:** de banen van vertoningen die in de rij zijn.

**Lopend:** de banen van vertoningen die lopen.

### Servernaam {#server-name}

Alleen voor geclusterde servers selecteert u de naam van het knooppunt om de werkitems of taakitems weer te geven die alleen op die server zijn gemaakt. Als Alles tonen is geselecteerd, worden alle werkitems voor alle knooppunten in een cluster weergegeven.

### Tijd maken {#create-time}

Selecteer een optie in dit filter om alleen die werkitems weer te geven die zijn gemaakt binnen de tijdlijn die u selecteert. Als u bijvoorbeeld 1 dag selecteert, worden alle werkitems weergegeven die zijn gemaakt binnen 24 uur vóór de tijd die is ingesteld in het filter Voor.

### Voor {#prior-to}

Hiermee stelt u de datum en tijd in die het filter Tijd maken als einddatum gebruikt. Houd de optie Huidige datum en tijd gebruiken geselecteerd om terug te filteren vanaf de huidige datum en tijd, of schrap de optie en ga de aangewezen waarden in. Klik op de kalenderpictogrammen of de klokpictogrammen om waarden te selecteren met deze gereedschappen.

Als u bijvoorbeeld Tijd maken = 1 dag en vóór = Huidige datum en tijd gebruiken selecteert, worden alle werkitems geretourneerd die in de laatste 24 uur zijn gemaakt.

>[!NOTE]
>
>Voor de gegevensbestandplaatsingen van het Oracle, werken de filters van de datumwaaier (namelijk Create Tijd en Voorafgaand aan montages) niet correct. Gebruik een ander filter om de werkitems op te halen.

## De interface op het tabblad Werkbeheer {#about-the-work-manager-tab-interface}

Wanneer u een vraag van de Manager van het Werk in werking stelt of een verrichting op een het werkpunt of baan uitvoert, verschijnt een bericht boven de lijst. Dit bericht bevat feedback over de actie die u hebt gestart en in sommige gevallen een koppeling Meer informatie voor meer informatie. Als de bewerking die u hebt gestart bijvoorbeeld is mislukt, wordt in het bericht zoveel vermeld en wordt een koppeling weergegeven om details over de fout op te halen.

Wanneer u op Meer informatie klikt, wordt in het dialoogvenster Bewerkingsdetails een lijst weergegeven met de werkitems of taken die tijdens de bewerking zijn geselecteerd. U kunt op elk lijstitem klikken om de foutdetails onder in het dialoogvenster weer te geven.

### De werkitems of taken beheren {#manage-the-work-items-or-jobs}

1. Gebruik de hieronder beschreven bewerkingsgereedschappen om de werkitems of taken in de lijst te beheren.

   >[!NOTE]
   >
   >De verrichtingen zijn beschikbaar afhankelijk van de status van het punt.

   **schrapt Punten:** schrapt het geselecteerde het werkpunt of de baan.

   **Pauzeert Punten:** pauzeert het geselecteerde het werkpunt of de baan.

   **Hervat Punten:** hervat het geselecteerde het werkpunt of de baan van zijn gepauzeerde staat.

   **probeer Punten opnieuw:** Probeert het geselecteerde het werkpunt of de baan van zijn huidige staat opnieuw uit te voeren.

   U kunt controleren of een bewerking is gelukt door boven de lijst op Meer informatie te klikken. Er wordt een dialoogvenster weergegeven met de geselecteerde werkitems of -taken en hun status.

## Aanvullende informatie over de status van werkitems {#additional-information-about-work-item-statuses}

Doorgaans bestaat een statusovergang voor een tijdelijk item uit Nieuw > Gepland > Bezig > Voltooid of Mislukt.

De pauzestatus onderbreekt deze normale stroom. De clienttoepassing of de systeembeheerder kan deze onderbreking starten (bijvoorbeeld voor onderhoud of upgrade). U kunt deze actie terugkeren door de verrichting van het Hervatten te gebruiken om het het werkpunt terug naar een Geplande staat te bewegen.

Een het werkpunt in een Geplande staat wordt een rij gevormd voor uitvoering die nog niet is begonnen. Deze items kunnen worden gepauzeerd of verwijderd of worden verplaatst naar de status In uitvoering wanneer de werkmanager ze uit de wachtrij haalt. Werkitems die in uitvoering zijn, kunnen niet worden gewijzigd. Ze zullen ofwel voltooid zijn of mislukken.

De staat Mislukt treedt als resultaat van een foutenvoorwaarde die tijdens de uitvoering van het het werkpunt voorkomt. Als u vermoedt dat fouten indirect zijn (vanwege de context op het moment van uitvoering), kunt u de uitvoering opnieuw proberen en het werkitem weer in de wachtrij plaatsen. Slechts een beperkt aantal pogingen is toegestaan.
