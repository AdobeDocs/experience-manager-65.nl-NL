---
title: Gecontroleerde eindpunten van mappen configureren
seo-title: Gecontroleerde eindpunten van mappen configureren
description: Leer hoe te om gecontroleerde omslageindpunten te vormen.
seo-description: Leer hoe te om gecontroleerde omslageindpunten te vormen.
uuid: 01fb5ff8-2071-44bd-9241-7d5d41a5b26e
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: 761e7909-43ba-4642-bcfc-8d76f139b9a3
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Gecontroleerde eindpunten van mappen configureren {#configuring-watched-folder-endpoints}

Een beheerder kan een netwerkmap, ook wel een *gecontroleerde map* genoemd, zo configureren dat wanneer een gebruiker een bestand (zoals een PDF-bestand) in de gecontroleerde map plaatst, een geconfigureerde servicebewerking wordt aangeroepen en het bestand wordt gemanipuleerd. Nadat de service de opgegeven bewerking heeft uitgevoerd, wordt het gewijzigde bestand opgeslagen in een opgegeven uitvoermap.

## De service Gecontroleerde map configureren {#configuring-the-watched-folder-service}

Alvorens u een gecontroleerd omslageindpunt vormt, vorm de Gecontroleerde dienst van de Omslag. De configuratieparameters van de service Gecontroleerde map hebben twee doelen:

* Om attributen te vormen die gemeenschappelijk voor alle gelete op omslageindpunten zijn
* Standaardwaarden opgeven voor alle eindpunten van de gecontroleerde map

Nadat u de service Gecontroleerde map hebt geconfigureerd, voegt u een eindpunt voor gecontroleerde mappen voor de doelservice toe. Wanneer het toevoegen van het eindpunt, plaatst u waarden, zoals de de dienstnaam en verrichtingsnaam om te roepen wanneer de dossiers of de omslagen in de inputomslag van de gevormde Gecontroleerde dienst van de Omslag worden geplaatst. Zie [Gecontroleerde instellingen voor](/help/forms/using/admin-help/configure-service-settings.md#watched-folder-service-settings)mapservice voor meer informatie over het configureren van de service Gecontroleerde map.

## Een controlemap maken {#creating-a-watched-folder}

U kunt op de volgende twee manieren een controlemap maken:

* Wanneer het vormen van de montages voor een gecontroleerd omslageindpunt, typ de volledige weg aan de ouderfolder in de doos van de Weg en voeg de naam van de gecontroleerde omslag toe die moet worden gecreeerd, zoals aangetoond in dit voorbeeld:
   `  C:\MyPDFs\MyWatchedFolder`Aangezien de map MyWatchedFolder nog niet bestaat, proberen AEM-formulieren deze op die locatie te maken.

* Creeer een omslag op het dossiersysteem alvorens een gecontroleerd omslageindpunt te vormen, en typ dan de volledige weg in de doos van de Weg.

In een gegroepeerde omgeving, moet de omslag die als gecontroleerde omslag zal worden gebruikt toegankelijk zijn, schrijfbaar, en op het dossiersysteem of netwerk worden gedeeld. In dit scenario moet elke instantie van de toepassingsserver van de cluster toegang hebben tot dezelfde gedeelde map.

Als de toepassingsserver in Windows als service wordt uitgevoerd, moet deze zijn gestart met de juiste toegang tot de gedeelde map op een van de volgende manieren:

* Configureer de **parameter** Log On As van de toepassingsserverservice om te beginnen als een specifieke gebruiker met de juiste toegang tot de gedeelde controlemap.
* Vorm het de dienstbegin van de toepassingsserver als Lokale optie van het Systeem om de Dienst toe te staan om met de Desktop in wisselwerking te staan. Deze optie vereist dat de gedeelde gecontroleerde map toegankelijk en schrijfbaar is voor iedereen.

## Gecontroleerde mappen aan elkaar koppelen {#chaining-together-watched-folders}

Gecontroleerde mappen kunnen aan elkaar worden gekoppeld, zodat het resulterende document van een gecontroleerde map het invoerdocument van de volgende controlemap is. Elke gecontroleerde map kan een andere service oproepen. Door gecontroleerde omslagen op deze manier te vormen, kunnen de veelvoudige diensten worden aangehaald. Eén gecontroleerde map kan bijvoorbeeld PDF-bestanden converteren naar Adobe PostScript® en een tweede gecontroleerde map kan de PostScript-bestanden converteren naar PDF/A-indeling. Om dit te doen, plaats eenvoudig de *resultaatomslag* van de gelete op omslag die door uw eerste eindpunt wordt bepaald aan de *inputomslag* van de gelete op omslag te richten door uw tweede eindpunt wordt bepaald.

De uitvoer van de eerste conversie gaat naar \path\result. De invoer voor de tweede conversie zou \path\result zijn en de uitvoer van de tweede conversie zou naar \path\result\result (of de map die u in het vak Resultaatmap voor de tweede conversie definieert) gaan.

## Hoe gebruikers omgaan met gecontroleerde mappen {#how-users-interact-with-watched-folders}

Voor een gecontroleerd mapeindpunt kunnen gebruikers een activering uitvoeren door invoerbestanden of mappen van hun bureaublad naar een gecontroleerde map te kopiëren of te slepen. De bestanden worden verwerkt in de volgorde waarin ze aankomen.

Voor gecontroleerde omslageindpunten, als de baan slechts één inputdossier vereist, kan de gebruiker dat dossier aan de wortel van de gecontroleerde omslag kopiëren.

Als de taak meer dan één invoerbestand bevat, moet de gebruiker een map buiten de controlemahiërarchie maken die alle vereiste bestanden bevat. Deze nieuwe map moet de invoerbestanden bevatten (en desgewenst een DDX-bestand als dit vereist is voor het proces). Nadat de taakmap is samengesteld, kopieert de gebruiker deze naar de invoermap van de gecontroleerde map.

>[!NOTE]
>
>Controleer of de toepassingsserver de toegang tot de bestanden in de gecontroleerde map heeft verwijderd. Als AEM-formulieren de bestanden niet kunnen verwijderen uit de invoermap nadat ze zijn gescand, wordt het bijbehorende proces voor onbepaalde tijd aangeroepen.

## Uitvoer van gecontroleerde map {#watched-folder-output}

Wanneer de invoer een map is en de uitvoer uit meerdere bestanden bestaat, wordt in AEM-formulieren een uitvoermap gemaakt met dezelfde naam als de invoermap en worden de uitvoerbestanden naar die map gekopieerd. Wanneer de uitvoer bestaat uit een documentkaart die een sleutelwaardepaar bevat, zoals de uitvoer van een uitvoerproces, wordt de sleutel gebruikt als de naam van het uitvoerbestand.

De namen van uitvoerbestanden die het resultaat zijn van een eindpuntproces, mogen geen andere tekens bevatten dan letters, cijfers en een punt (.) vóór de bestandsextensie. AEM-formulieren zetten andere tekens om in hexadecimale waarden.

Clienttoepassingen nemen de resultaatdocumenten op in de map met gecontroleerde resultaten. Procesfouten worden aangemeld in de map met gecontroleerde mapfouten.

## Hoe gecontroleerde map werkt {#how-watched-folder-works}

De module Gecontroleerde map bevat de volgende services:

* Service voor gecontroleerde mappen
* provider.file_scan_service
* provider.file_write_results_service

Naast de hierboven vermelde services, is Controlemap ook afhankelijk van andere services, waaronder de plannerservice voor het plannen van de taken en de taakbeheerservice voor het ondersteunen van asynchrone aanroepen van doelservices.

### Hoe gecontroleerde map een aanroepingsverzoek verwerkt {#how-watched-folder-processes-an-invocation-request}

De service Gecontroleerde map handelt het maken, bijwerken en verwijderen van de eindpunten af. Nadat de beheerder de eindpunten creeert, zijn zij gepland om door de dienst van de Planner te worden teweeggebracht die op het gespecificeerde herhalingsinterval of gewassenuitdrukking wordt gebaseerd.

In dit diagram ziet u hoe een aanroepingsverzoek in een gecontroleerde map wordt verwerkt.

![en_watchedfolder](assets/en_watchedfolder.png)

Het aanroepen van een service met gecontroleerde mappen verloopt als volgt:

1. Een clienttoepassing plaatst bestanden of mappen in de invoermap van de gecontroleerde map.
1. Wanneer het taakaftasteninterval voorkomt, roept de dienst van de Planner de provider.file_scan_service aan om de dossiers of de omslagen in de inputomslag te verwerken.
1. De provider.file_scan_service voert de volgende taken uit:


   * Hiermee wordt de invoermap gescand op bestanden of mappen die overeenkomen met het include-bestandspatroon en worden bestanden of mappen voor het opgegeven bestandspatroon uitgesloten. De oudste bestanden of mappen worden als eerste opgepakt. Bestanden en mappen die ouder zijn dan de wachttijd worden ook opgehaald. In één scan is het aantal bestanden of mappen dat wordt verwerkt, afhankelijk van de grootte van de batch. Zie [Bestandspatronen](configuring-watched-folder-endpoints.md#about-file-patterns)voor informatie over bestandspatronen. Zie [Gecontroleerde mapservice-instellingen](/help/forms/using/admin-help/configure-service-settings.md#watched-folder-service-settings)voor informatie over het instellen van de batchgrootte.
   * Hiermee worden de bestanden of mappen opgehaald voor verwerking. Als de bestanden of mappen niet volledig zijn gedownload, worden ze opgehaald in de volgende scan. Om ervoor te zorgen dat mappen volledig worden gedownload, moeten beheerders een map met een naam maken met het bestandspatroon voor uitsluiten. Nadat de map alle bestanden bevat, moet de naam ervan worden gewijzigd in het patroon dat is opgegeven in het bestandspatroon voor opnemen. Deze stap zorgt ervoor dat de omslag alle noodzakelijke dossiers nodig heeft om de dienst aan te halen. Zie [Tips en trucs voor gecontroleerde mappen](configuring-watched-folder-endpoints.md#tips-and-tricks-for-watched-folders)voor meer informatie over hoe u ervoor kunt zorgen dat mappen volledig worden gedownload.
   * Hiermee verplaatst u de bestanden of mappen naar de werkgebiedmap nadat u ze hebt geselecteerd voor verwerking.
   * Hiermee worden de bestanden of mappen in de werkgebiedmap omgezet in de juiste invoer op basis van de parametertoewijzingen voor eindpuntinvoer. Zie [Tips en trucs voor gecontroleerde mappen](configuring-watched-folder-endpoints.md#tips-and-tricks-for-watched-folders)voor voorbeelden van invoerparametertoewijzingen.


1. De doeldienst die voor het eindpunt wordt gevormd wordt of synchroon of asynchroon aangehaald. De doeldienst wordt aangehaald gebruikend de gebruikersnaam en het wachtwoord dat voor het eindpunt wordt gevormd.

   * De synchrone aanroeping roept de doeldienst direct en behandelt onmiddellijk de reactie.
   * Voor asynchrone aanroeping, wordt de doeldienst geroepen door de dienst van de Manager van de Baan, die het verzoek in een rij plaatst. De dienst van de Manager van de Baan, beurtelings, roept provider.file_write_results_service om de resultaten te behandelen.

1. De provider.file_write_results_service handelt de reactie of de mislukking van de aanroeping van de doeldienst af. Wanneer succesvol, wordt de output bewaard aan de resultaatomslag die op de eindpuntconfiguratie wordt gebaseerd. De provider.file_write_results_service bewaart ook de bron als het eindpunt wordt gevormd om de resultaten op succesvolle voltooiing te bewaren.

   Wanneer de aanroeping van de doeldienst in een mislukking resulteert, registreert provider.file_write_results_service de oorzaak van de mislukking in een mislukking.log dossier en plaatst dat dossier in de mislukkingsomslag. De mislukkingsomslag wordt gecreeerd gebaseerd op de configuratieparameters die voor het eindpunt worden gespecificeerd. Wanneer de beheerder de optie Bij mislukken behouden voor de eindpuntconfiguratie instelt, kopieert provider.file_write_results_service ook de bronbestanden naar de mislukkingsmap. Voor informatie over het terugkrijgen van dossiers van de mislukkingsomslag, zie [Mislukkingspunten en terugwinning](configuring-watched-folder-endpoints.md#failure-points-and-recovery).


## Instellingen voor het eindpunt van gecontroleerde mappen {#watched-folder-endpoint-settings}

Gebruik de volgende montages om een gecontroleerd omslageindpunt te vormen.

**Naam:** (Verplicht) Identificeert het eindpunt. Neem geen &lt;-teken op omdat de naam die in Workspace wordt weergegeven hierdoor wordt afgekapt. Als u een URL als naam van het eindpunt ingaat, zorg ervoor dat het met de syntaxisregels in overeenstemming is die in RFC1738 worden gespecificeerd.

**Omschrijving:** Een beschrijving van het eindpunt. Neem geen &lt;-teken op omdat de beschrijving die in Workspace wordt weergegeven hierdoor wordt afgekapt.

**Pad:** (Verplicht) Geeft de locatie van de gecontroleerde map aan. In een gegroepeerd milieu, moet dit plaatsen aan een gedeelde netwerkomslag richten die van elke computer in de cluster toegankelijk is.

**Asynchroon:** Identificeert het aanroepingstype als asynchroon of synchroon. De standaardwaarde is asynchroon. Asynchroon wordt aanbevolen voor langlevende processen, terwijl synchroon wordt aanbevolen voor voorbijgaande of kortstondige processen.

**Uitsnijduitdrukking:** Voer een uitsnijdexpressie in als de gecontroleerde map moet worden gepland met een uitsnijdexpressie. Wanneer deze instelling is geconfigureerd, wordt Interval herhalen genegeerd.

**Interval herhalen:** Het interval in seconden voor het scannen van de controlemap op invoer. Als de instelling voor Throttle niet is ingeschakeld, moet het interval voor herhalen langer zijn dan de tijd voor het verwerken van een gemiddelde taak. anders kan het systeem overbelast raken . De standaardwaarde is 5. Zie de beschrijving bij Batchgrootte voor meer informatie.

**Aantal herhalingen:** Het aantal keren dat de gecontroleerde map de map of map scant. De waarde -1 geeft aan dat een scanbewerking voor onbepaalde tijd wordt uitgevoerd. De standaardwaarde is -1.

**Throttle:** Als deze optie is geselecteerd, wordt het aantal controletaken dat door AEM-formulieren op een bepaald moment wordt verwerkt, beperkt. Het maximumaantal taken wordt bepaald door de waarde voor Batchgrootte. (Zie Informatie over vertragen.)

**Gebruikersnaam:** (Verplicht) De gebruikersnaam die wordt gebruikt wanneer een doelservice wordt aangeroepen vanuit de gecontroleerde map. De standaardwaarde is SuperAdmin.

**Domeinnaam:** (Verplicht) Het domein van de gebruiker. De standaardwaarde is DefaultDom.

**Batchgrootte:** Het aantal bestanden of mappen dat per scan moet worden opgehaald. gebruiken om overbelasting van het systeem te voorkomen; te veel bestanden tegelijk scannen kan ertoe leiden dat de toepassing vastloopt. De standaardwaarde is 2.

Met de instellingen voor Interval herhalen en Batchgrootte bepaalt u hoeveel bestanden in Gecontroleerde map worden opgehaald bij elke scan. De gecontroleerde Omslag gebruikt een de draadpool van het Kwartz om de inputomslag af te tasten. De draadpool wordt gedeeld met andere diensten. Als het aftasteninterval klein is, zullen de draden de inputomslag vaak aftasten. Als bestanden vaak in de controlemap worden neergezet, moet u het scaninterval klein houden. Als de dossiers niet vaak worden gelaten vallen, gebruik een groter aftasteninterval zodat de andere diensten de draden kunnen gebruiken.

Als er een groot volume bestanden verloren gaat, maakt u de batch groot. Als de service die wordt aangeroepen door het gecontroleerde mapeindpunt bijvoorbeeld 700 bestanden per minuut kan verwerken en gebruikers bestanden naar dezelfde snelheid in de invoermap kunnen neerzetten, helpt het instellen van Batchgrootte op 350 en Herhalingsinterval op 30 seconden de prestaties van gecontroleerde mappen te controleren zonder de kosten voor het te vaak doorzoeken van de gecontroleerde map op te lopen.

Wanneer bestanden in de controlemap worden neergezet, worden de bestanden in de invoer weergegeven. Hierdoor kunnen de prestaties afnemen wanneer elke seconde wordt gescand. Het verhogen van het aftasteninterval kan prestaties verbeteren. Als het volume van de dossiers dat klein is wordt gelaten vallen, pas de Grootte van de Partij en Interval dienovereenkomstig aan. Als er bijvoorbeeld elke seconde 10 bestanden worden verwijderd, stelt u het interval voor herhalen in op 1 seconde en de waarde voor Batchgrootte op 10.

**Wacht tijd:** De tijd, in milliseconden, om te wachten alvorens u een omslag of een dossier scant nadat het wordt gecreeerd. Als de wachttijd bijvoorbeeld 3.600.000 milliseconden (een uur) is en het bestand een minuut geleden is gemaakt, wordt dit bestand opgepikt nadat 59 minuten zijn verstreken. De standaardwaarde is 0.

Deze instelling is handig om ervoor te zorgen dat een bestand of map volledig naar de invoermap wordt gekopieerd. Als u bijvoorbeeld een groot bestand hebt dat moet worden verwerkt en het downloaden van het bestand duurt tien minuten, stelt u de wachttijd in op 10&amp;ast;60 &amp;ast;1000 milliseconden. Zo voorkomt u dat de gecontroleerde map het bestand scant als het nog geen tien minuten oud is.

**Bestandspatroon uitsluiten:** een puntkomma **;** gescheiden lijst met patronen die een gecontroleerde map gebruikt om te bepalen welke bestanden en mappen worden gescand en opgepakt. Bestanden of mappen met dit patroon worden niet gescand voor verwerking.

Deze instelling is handig wanneer de invoer een map met meerdere bestanden is. De inhoud van de map kan worden gekopieerd naar een map met een naam die wordt opgepakt door de gecontroleerde map. Hierdoor wordt voorkomen dat de gecontroleerde map een map opneemt die moet worden verwerkt voordat de map volledig naar de invoermap is gekopieerd.

U kunt bestandspatronen gebruiken om uit te sluiten:

* Bestanden met specifieke bestandsnaamextensies; bijvoorbeeld &amp;ast;.dat, &amp;ast;.xml, &amp;ast;.pdf.
* Bestanden met specifieke namen; bijvoorbeeld gegevens.&amp;ast; bestanden en mappen met de naam *data1*, *data2* enzovoort uitsluiten.
* Bestanden met samengestelde expressies in de naam en de extensie, zoals in de volgende voorbeelden:

   * Gegevens[0-9][0-9][0-9].[dD][aA]&#39;port&#39;
   * &amp;ast;.[dD][Aa]&#39;port&#39;
   * &amp;ast;.[x][MM][Ll]

Zie [Bestandspatronen](configuring-watched-folder-endpoints.md#about-file-patterns)voor meer informatie over bestandspatronen.

**Inclusief bestandspatroon:** (Verplicht) Een puntkomma **;** gescheiden lijst met patronen die in de gecontroleerde map worden gebruikt om te bepalen welke mappen en bestanden worden gescand en opgepakt. Als bijvoorbeeld het Include Patroon van het Dossier input&amp;amp is;ast;, alle dossiers en omslagen die input&amp;amp aanpassen;ast; worden opgepakt. Dit omvat bestanden en mappen met de naam input1, input2, enzovoort.

De standaardwaarde is &amp;ast; en geeft alle bestanden en mappen aan.

U kunt bestandspatronen gebruiken om het volgende op te nemen:

* Bestanden met specifieke bestandsnaamextensies; bijvoorbeeld &amp;ast;.dat, &amp;ast;.xml, &amp;ast;.pdf.
* Bestanden met specifieke namen; bijvoorbeeld gegevens.&amp;ast; omvat bestanden en mappen met de naam *data1*, *data2* enzovoort.
* Bestanden met samengestelde expressies in de naam en de extensie, zoals in de volgende voorbeelden:

   * Gegevens[0-9][0-9][0-9].[dD][aA]&#39;port&#39;
   * &amp;ast;.[dD][Aa]&#39;port&#39;
   * &amp;ast;.[x][MM][Ll]

Zie [Bestandspatronen](configuring-watched-folder-endpoints.md#about-file-patterns)voor meer informatie over bestandspatronen.


**Map met resultaten:** De map waarin de opgeslagen resultaten worden opgeslagen. Als de resultaten niet in deze map worden weergegeven, controleert u de map met foutmeldingen. Alleen-lezen bestanden worden niet verwerkt en worden opgeslagen in de map met foutmeldingen. Deze waarde kan een absoluut of relatief pad zijn met de volgende bestandspatronen:

* %F = voorvoegsel bestandsnaam
* %E = bestandsnaamextensie
* %Y = jaar (volledig)
* %y = jaar (laatste twee cijfers)
* %M = maand
* %D = dag van de maand
* %d = dag van het jaar
* %H = uur (24-uurs klok)
* %h = uur (12-uurs klok)
* %m = minuut
* %s = seconde
* %l = millisecond
* %R = willekeurig getal (tussen 0 en 9)
* %P = proces- of taak-id

Als de waarde op 17 juli 2009 bijvoorbeeld 8 uur is en u opgeeft `C:/Test/WF0/failure/%Y/%M/%D/%H/`, is de resultatenmap `C:/Test/WF0/failure/2009/07/17/20`.

Als het pad niet absoluut maar relatief is, wordt de map in de controlemap gemaakt. De standaardwaarde is result/%Y/%M/%D/. Dit is de resultatenmap in de gecontroleerde map. Zie [Bestandspatronen](configuring-watched-folder-endpoints.md#about-file-patterns)voor meer informatie over bestandspatronen.

>[!NOTE]
>
>Hoe kleiner de resulterende mappen, hoe beter Gecontroleerde mappen. Als het geschatte laden voor de gecontroleerde map bijvoorbeeld 1000 bestanden per uur is, probeert u een patroon als `result/%Y%M%D%H` zodat er elk uur een nieuwe submap wordt gemaakt. Als het laden kleiner is (bijvoorbeeld 1000 bestanden per dag), kunt u een patroon gebruiken zoals `result/%Y%M%D`.

**Map behouden:** De locatie waar bestanden worden opgeslagen nadat bestanden zijn gescand en opgehaald. Het pad kan een absoluut, relatief of null-mappad zijn. U kunt bestandspatronen gebruiken, zoals beschreven in Resultaatmap. De standaardwaarde is preserve/%Y/%M/%D/.

**Map mislukt:** De map waarin bestanden met fouten worden opgeslagen. Deze locatie is altijd relatief ten opzichte van de gecontroleerde map. U kunt bestandspatronen gebruiken, zoals beschreven in Resultaatmap.

Alleen-lezen bestanden worden niet verwerkt en worden opgeslagen in de map met foutmeldingen.

De standaardwaarde is error/%Y/%M/%D/.

**Behouden bij fout:** Invoerbestanden behouden als de bewerking niet op een service wordt uitgevoerd. De standaardwaarde is true.

**Dubbele bestandsnamen overschrijven:** Als u de waarde True instelt, worden de bestanden in de map results en preserve overschreven. Wanneer ingesteld op Onwaar, worden bestanden en mappen met het numerieke indexachtervoegsel gebruikt voor de naam. De standaardwaarde is False.

**Duur wissen:** (Verplicht) Bestanden en mappen in de resultaatmap worden gewist wanneer ze ouder zijn dan deze waarde. Deze waarde wordt gemeten in dagen. Deze instelling is handig om ervoor te zorgen dat de resultaatmap niet vol wordt.

De waarde -1 dagen geeft aan dat u de resultatenmap nooit wilt verwijderen. De standaardwaarde is -1.

**Bedrijfsnaam:** (Verplicht) Een lijst van verrichtingen die aan het gelete op omslageindpunt kunnen worden toegewezen.

**Toewijzingen invoerparameter:** Gebruikt om de input te vormen die wordt vereist om de dienst en de verrichting te verwerken. Welke instellingen beschikbaar zijn, is afhankelijk van de service die het gecontroleerde mapeindpunt gebruikt. Hier volgen de twee typen invoer:

**Letterlijk:** De controlemap gebruikt de waarde die in het veld wordt ingevoerd terwijl deze wordt weergegeven. Alle basistypen van Java worden ondersteund. Als een API bijvoorbeeld invoer gebruikt zoals String, long, int en Boolean, wordt de tekenreeks omgezet in het juiste type en wordt de service aangeroepen.

**Variabele:** De ingevoerde waarde is een bestandspatroon waarmee de gecontroleerde map de invoer kan selecteren. Bijvoorbeeld, in het geval van de encrypt wachtwoorddienst, waar het inputdocument een Pdf- dossier moet zijn, kan de gebruiker &amp;ast;.pdf als dossierpatroon gebruiken. De gecontroleerde map pakt alle bestanden in de gecontroleerde map op die overeenkomen met dit patroon en roept de service voor elk bestand aan. Wanneer een variabele wordt gebruikt, worden alle invoerbestanden geconverteerd naar documenten. Alleen API&#39;s die Document als invoertype gebruiken, worden ondersteund.

**Toewijzingen uitvoerparameter:** Gebruikt om de output van de dienst en de verrichting te vormen. Welke instellingen beschikbaar zijn, is afhankelijk van de service die het gecontroleerde mapeindpunt gebruikt.

De gecontroleerde output van de Omslag kan één enkel document, een lijst van documenten, of een kaart van documenten zijn. Deze uitvoerdocumenten worden vervolgens opgeslagen in de resultaatmap met het patroon dat is opgegeven in de toewijzing Uitvoerparameter.

>[!NOTE]
>
>Het opgeven van namen die resulteren in unieke uitvoerbestandsnamen verbetert de prestaties. Neem bijvoorbeeld het geval waarin de service één uitvoerdocument retourneert en de functie Toewijzing uitvoerparameter aan `%F.%E` (de bestandsnaam en extensie van het invoerbestand) toewijst. Als gebruikers in dit geval elke minuut bestanden met dezelfde naam neerzetten en de resultaatmap is geconfigureerd `result/%Y/%M/%D`en de instelling Dubbele bestandsnaam overschrijven is uitgeschakeld, probeert de gecontroleerde map de dubbele bestandsnamen op te lossen. Het proces voor het oplossen van dubbele bestandsnamen kan van invloed zijn op de prestaties. In deze situatie, die de Toewijzing van de Parameter van de Output veranderen om uren, notulen, seconden, en milliseconden aan de naam toe `%F_%h_%m_%s_%l` te voegen, of ervoor zorgen dat de gelaten vallen dossiers unieke namen hebben kan prestaties verbeteren.

## Bestandspatronen {#about-file-patterns}

Beheerders kunnen het type bestand opgeven dat een service kan aanroepen. Voor elke gecontroleerde map kunnen meerdere bestandspatronen worden ingesteld. Een bestandspatroon kan een van de volgende bestandseigenschappen zijn:

* Bestanden met specifieke bestandsextensies; &amp;ast;.dat, &amp;ast;.xml, &amp;ast;.pdf,;
* Bestanden met specifieke namen; bijvoorbeeld gegevens.&amp;ast;
* Bestanden met samengestelde expressies in de naam en de extensie, zoals in de volgende voorbeelden:

   * Gegevens[0-9][0-9][0-9].[dD][aA]&#39;port&#39;
   * &amp;ast;.[dD][Aa]&#39;port&#39;
   * &amp;ast;.[x][MM][Ll]

De beheerder kan het bestandspatroon van de uitvoermap definiëren waarin de resultaten worden opgeslagen. Voor de uitvoermappen (resultaat, behoud en fout) kan de beheerder een van de volgende bestandspatronen opgeven:

* %Y = jaar (volledig)
* %y = jaar (laatste twee cijfers)
* %M = maand,
* %D = dag van de maand,
* %d = dag van het jaar,
* %h = uur,
* %m = minuut,
* %s = seconde,
* %R = willekeurig getal tussen 0 en 9
* %J = Taaknaam

Het pad naar de resultaatmap kan bijvoorbeeld `C:\Adobe\Adobe_Experience_Manager_forms\BarcodedForms\%y\%m\%d`zijn.

Toewijzingen voor uitvoerparameters kunnen ook aanvullende patronen opgeven, zoals:

* %F = bronbestandsnaam
* %E = extensie bronbestandsnaam

Als het toewijzingspatroon van de uitvoerparameter eindigt met &quot;File.separator&quot; (dit is het padscheidingsteken), wordt een map gemaakt en wordt de inhoud naar die map gekopieerd. Als het patroon niet eindigt met &quot;File.separator&quot;, wordt de inhoud (resultaatbestand of -map) met die naam gemaakt. Zie [Tips en trucs voor gecontroleerde mappen](configuring-watched-folder-endpoints.md#tips-and-tricks-for-watched-folders)voor meer informatie over uitvoerparametertoewijzingen.

## Over vertragen {#about-throttling}

Wanneer throttling voor een eindpunt van de controlemap wordt toegelaten, beperkt het het aantal gelete op omslagbanen die op om het even welk bepaald ogenblik kunnen worden verwerkt. Het maximumaantal banen wordt bepaald door de waarde van de Grootte van de Partij, ook configureerbaar in het Gecontroleerde eindpunt van de Omslag. Binnenkomende documenten in de invoermap van de controlemap worden niet gepolled wanneer de limiet voor het vertragen is bereikt. De documenten blijven ook in de invoermap totdat andere controlemaptaken zijn voltooid en een andere opiniepeilingpoging is uitgevoerd. In het geval van synchrone verwerking, zullen alle banen die in één enkele opiniepeiling worden verwerkt op de vertragingsgrens tellen, alhoewel de banen achtereenvolgens in één enkele draad worden verwerkt.

>[!NOTE]
>
>De rotatie wordt niet met een cluster geschaald. Wanneer de throttling wordt toegelaten, zal de cluster als geheel niet meer dan het aantal banen verwerken die in de Grootte van de Partij op een bepaald ogenblik worden gespecificeerd. Deze limiet geldt voor de hele cluster en is niet specifiek voor elk knooppunt in de cluster. Met een Batch-grootte van 2, bijvoorbeeld, kan de vertragingslimiet worden bereikt met één knooppunt dat twee taken verwerkt, en geen enkele andere knooppunten zullen de invoermap opvragen totdat een van de taken is voltooid.

### Hoe vertragen werkt {#how-throttling-works}

Gecontroleerde map scant de invoermap bij elk herhalingsinterval, haalt het aantal bestanden op dat is opgegeven in Batchgrootte en roept de doelservice voor elk van deze bestanden aan. Als de Batchgrootte bijvoorbeeld vier is, worden bij elke scan vier bestanden door Gecontroleerde map opgehaald, vier aanroepingsverzoeken gemaakt en de doelservice aangeroepen. Voordat deze aanvragen worden voltooid, worden er, als Controlemap wordt aangeroepen, opnieuw vier taken gestart, ongeacht of de vorige vier taken zijn voltooid.

Door deze functie voorkomt u dat Gecontroleerde map nieuwe taken aanroept wanneer de vorige taken niet zijn voltooid. Gecontroleerde map detecteert taken die worden uitgevoerd en verwerkt nieuwe taken op basis van de batchgrootte min de taken die worden uitgevoerd. Als het aantal voltooide taken in de tweede aanroep bijvoorbeeld slechts drie is en er nog één taak actief is, worden er door de gecontroleerde map slechts drie extra taken aangeroepen.

* Controlemap is afhankelijk van het aantal bestanden in de werkgebiedmap om te bepalen hoeveel taken worden uitgevoerd. Als bestanden niet worden verwerkt in de werkgebiedmap, worden er geen taken meer aangeroepen in de gecontroleerde map. Als de batchgrootte bijvoorbeeld vier en drie taken is, wordt bij volgende aanroepen slechts één taak aangeroepen als de controlemap vier en drie taken is geïnstalleerd. Er zijn meerdere scenario&#39;s die ertoe kunnen leiden dat bestanden niet worden verwerkt in de werkgebiedmap. Wanneer taken zijn vastgezet, kan de beheerder het proces op de pagina met beheer van de formulierwerkstroom beëindigen, zodat de bestanden uit de werkgebiedmap worden verplaatst.
* Als de formulierserver uitvalt voordat de taken kunnen worden aangeroepen door de gecontroleerde map, kan de beheerder de bestanden uit de werkgebiedmap verplaatsen. Zie [Foutpunten en herstel](configuring-watched-folder-endpoints.md#failure-points-and-recovery)voor meer informatie.
* Als de formulierserver actief is maar de gecontroleerde map niet wordt uitgevoerd wanneer de taakbeheerservice weer wordt aangeroepen, wat gebeurt wanneer services niet in de geordende volgorde worden gestart, kan de beheerder de bestanden uit de werkgebiedmap verplaatsen. Zie [Foutpunten en herstel](configuring-watched-folder-endpoints.md#failure-points-and-recovery)voor meer informatie.


## Prestaties en schaalbaarheid {#performance-and-scalability}

Gecontroleerde map kan in totaal 100 mappen aanleveren op één knooppunt. De prestaties van de gecontroleerde map zijn afhankelijk van de prestaties van de formulierserver. Voor asynchrone aanroep zijn de prestaties meer afhankelijk van de systeembelasting en de taken in de taakbeheerwachtrij.

De prestaties van gecontroleerde mappen kunnen worden verbeterd door knooppunten toe te voegen aan de cluster. De gecontroleerde banen van de Omslag worden verdeeld over de clusterknopen door de planner van het Kwartz en, in het geval van asynchrone verzoeken, door de dienst van de Manager van de Baan. Alle taken blijven behouden in de database.

De gecontroleerde Omslag hangt van de dienst van de Planner voor het plannen, het uit plannen, en het opnieuw plannen van de banen af. Andere diensten, zoals de dienst van het Beheer van de Gebeurtenis, de dienst van de Manager van de Gebruiker, en de dienst van de E-mailLeverancier, zijn beschikbaar die de de draadpool van de de dienstdraad van de Planner delen. Dit kan van invloed zijn op de prestaties van gecontroleerde mappen. De de dienstdraadpool van de Planner het stemmen zal nodig zijn wanneer alle diensten beginnen het te gebruiken.

## Gecontroleerde mappen in een cluster {#watched-folders-in-a-cluster}

In een cluster is de gecontroleerde map afhankelijk van de planner van het Kwartet en de taakbeheerservice voor taakverdeling en overname bij storing. Zie [Kwartz-documentatie](https://www.quartz-scheduler.org/documentation)voor meer informatie over het clustergedrag van Kwartz.

De gecontroleerde Omslag voert deze drie belangrijkste taken bij elke opiniepeiling uit:

* De map doorzoeken
* De doelservice aanroepen
* De resultaten afhandelen

Het gedrag voor taakverdeling en failover verandert afhankelijk van het feit of de gecontroleerde map is geconfigureerd voor synchrone of asynchrone aanroep.

### Synchrone gecontroleerde map in een cluster {#synchronous-watched-folder-in-a-cluster}

Voor synchrone aanroepen bepaalt het taakverdelingsmechanisme van het Kwartz welk knooppunt de polling-gebeurtenis krijgt. De knoop die de opiniepeilingsgebeurtenis krijgt zal alle taken uitvoeren: scan de map, activeer de doelservice en behandel de resultaten.

![en_synchwatchedfoldercluster](assets/en_synchwatchedfoldercluster.png)

Voor synchrone aanroepen, wanneer één knoop ontbreekt, verzendt de planner van het Kwartz nieuwe opiniepeilingsgebeurtenissen naar andere knopen. Aanroepen die op de mislukte knoop begonnen zijn zullen verloren gaan. Voor meer informatie over hoe te om de dossiers terug te krijgen verbonden aan de ontbroken baan, zie [Mislukkingspunten en terugwinning](configuring-watched-folder-endpoints.md#failure-points-and-recovery).


### Asynchrone gecontroleerde map in een cluster {#asynchronous-watched-folder-in-a-cluster}

Voor asynchrone aanroepen bepaalt het taakverdelingsmechanisme van het Kwartz welk knooppunt de polling-gebeurtenis krijgt. De knoop die de opiniepeilingsgebeurtenis krijgt zal de inputomslag aftasten en de doeldienst aanhalen door het verzoek in de de dienstrij van de Manager van de Baan te plaatsen. Het taakbeheertaaktaaktaaktaakverdelingsmechanisme bepaalt op zijn beurt welk knooppunt het aanroepingsverzoek zal verwerken. Het is mogelijk dat zelfs alhoewel de knoop A tot het aanroepingsverzoek leidde, de knoop B omhoog verwerkend het verzoek beëindigt. Of het knooppunt dat de aanroepingsaanvraag heeft gestart, kan de aanvraag ook verwerken.

![nl_asynchwatchedfoldercluster](assets/en_asynchwatchedfoldercluster.png)

Voor asynchrone aanroepen, wanneer één knoop ontbreekt, verzendt de planner van het Kwartz nieuwe opiniepeilingsgebeurtenissen naar andere knopen. Aanroepingsverzoeken die op het mislukte knooppunt zijn gemaakt, worden in de servicewachtrij van Taakbeheer geplaatst en worden voor verwerking naar andere knooppunten verzonden. Bestanden waarvoor geen aanroepingsverzoeken zijn gemaakt, blijven in de werkgebiedmap. Voor meer informatie over hoe te om de dossiers terug te krijgen verbonden aan de ontbroken baan, zie [Mislukkingspunten en terugwinning](configuring-watched-folder-endpoints.md#failure-points-and-recovery).


## Foutpunten en herstel {#failure-points-and-recovery}

Bij elke opiniepeilingsgebeurtenis worden de invoermap vergrendeld door de gecontroleerde map, worden de bestanden die overeenkomen met het include-bestandspatroon verplaatst naar de werkgebiedmap en wordt de invoermap ontgrendeld. Het sluiten is nodig zodat twee draden niet de zelfde reeks dossiers oppakken en hen tweemaal verwerken. De kans dat dit gebeurt neemt toe met een kleine herhalingsinterval en een grote batch. Nadat de bestanden naar de werkgebiedmap zijn verplaatst, wordt de invoermap ontgrendeld, zodat andere threads de map kunnen scannen. Deze stap helpt hoge productie te verstrekken omdat andere draden kunnen aftasten terwijl één draad de dossiers verwerkt.

Nadat de bestanden naar de werkgebiedmap zijn verplaatst, worden voor elk bestand aanroepingsverzoeken gemaakt en wordt de doelservice aangeroepen. Er kunnen zich gevallen voordoen waarin de bestanden in de werkgebiedmap niet kunnen worden hersteld met de gecontroleerde map:

* Als de server uitvalt voordat de aanroepingsaanvraag kan worden gemaakt met de gecontroleerde map, blijven de bestanden in de werkgebiedmap in de werkgebiedmap en worden deze niet hersteld.
* Als de Gecontroleerde Omslag met succes de oproepingsverzoek voor elk van de dossiers in de omslag van het Stadium en de serverneerstortingen heeft gecreeerd, zijn er twee gedrag dat op het oproepingstype wordt gebaseerd:

**Synchroon:** Als Controlemap is geconfigureerd om de service synchroon aan te roepen, blijven alle bestanden in de werkgebiedmap onverwerkt in de werkgebiedmap.

**Asynchroon:** In dit geval is de gecontroleerde map afhankelijk van de service Taakbeheer. Als de service Taakbeheer de gecontroleerde map terugroept, worden de bestanden in de werkgebiedmap verplaatst naar de map preserve of failure op basis van de resultaten van de aanroep. Als de service Taakbeheer de gecontroleerde map niet terugroept, blijven de bestanden onverwerkt in de werkgebiedmap. Deze situatie treedt op wanneer de gecontroleerde map niet wordt uitgevoerd wanneer de taakmanager terugbelt.

### Niet-verwerkte bronbestanden herstellen in de werkgebiedmap {#recovering-unprocessed-source-files-in-the-stage-folder}

Wanneer de bronbestanden in de werkgebiedmap niet kunnen worden verwerkt in de gecontroleerde map, kunt u de onverwerkte bestanden herstellen.

1. Start de toepassingsserver of het knooppunt opnieuw.
1. (Optioneel) Stop Gecontroleerde map met het verwerken van nieuwe invoerbestanden. Als u deze stap overslaat, is het veel moeilijker om te bepalen welke bestanden niet worden verwerkt in de werkgebiedmap. Voer een van de volgende taken uit om te voorkomen dat gecontroleerde mappen nieuwe invoerbestanden verwerken:

   * In Toepassingen en de Diensten, verander de Include parameter van het Patroon van het Dossier voor het gecontroleerde omslageindpunt in iets dat geen van de nieuwe inputdossiers (bijvoorbeeld, ga binnen `NOMATCH`) zal aanpassen.
   * Onderbreek het proces dat nieuwe invoerbestanden maakt.
   Wacht tot alle bestanden zijn hersteld en verwerkt in AEM-formulieren. De meeste bestanden moeten worden hersteld en nieuwe invoerbestanden moeten correct worden verwerkt. De tijdsduur dat u wacht tot de gecontroleerde map de bestanden heeft hersteld en verwerkt, is afhankelijk van de lengte van de bewerking die moet worden aangeroepen en het aantal bestanden dat moet worden hersteld.

1. Bepaal welke bestanden niet kunnen worden verwerkt. Ga naar de volgende stap als u op een geschikte hoeveelheid tijd hebt gewacht en de vorige stap hebt voltooid en er nog steeds onverwerkte bestanden in de map met werkgebieden staan.

   >[!NOTE]
   >
   >U kunt de datum- en tijdstempel van de bestanden in de werkgebiedmap bekijken. Afhankelijk van het aantal bestanden en de normale verwerkingstijd kunt u bepalen welke bestanden oud genoeg zijn om als geplakt te worden beschouwd.

1. Kopieer de onverwerkte bestanden van de werkgebiedmap naar de invoermap.
1. Als u hebt verhinderd dat gecontroleerde map nieuwe invoerbestanden kon verwerken in stap 2, wijzigt u het Include-bestandspatroon in de vorige waarde of schakelt u het proces dat u hebt uitgeschakeld opnieuw in.

## Beveiligingsoverwegingen voor gecontroleerde mappen {#security-considerations-for-watched-folders}

Elke gecontroleerde map is geconfigureerd met een gebruikersnaam en wachtwoord. Deze geloofsbrieven worden gebruikt wanneer het aanhalen van de diensten. Gecontroleerde map is afhankelijk van het feit dat de gedeelde map is beveiligd met het onderliggende beveiligingsbestandssysteem, zodat alleen de eigenaar van de gecontroleerde map toegang heeft tot de gedeelde map.

## Tips en trucs voor gecontroleerde mappen {#tips-and-tricks-for-watched-folders}

Hier zijn sommige uiteinden en trucs wanneer het vormen van het Gecontroleerde eindpunt van de Omslag:

* Als u een gecontroleerde omslag op Vensters hebt die beelddossiers verwerkt, specificeer waarden voor de Include optie van het Patroon van het Dossier of van de Uitsluiting van het Patroon van het Dossier om de Vensters auto-geproduceerde Thumbs.db- dossier te verhinderen door de gecontroleerde omslag worden gepolled.
* Wanneer een uitsnijdexpressie wordt opgegeven, wordt het herhalingsinterval genegeerd. Het gebruik van de expressie voor uitsnijden is gebaseerd op het open-source taakplanningssysteem van Kwartz, versie 1.4.0.
* De batch-grootte is het aantal bestanden of mappen dat wordt opgehaald in elke scan van de gecontroleerde map. Als de batchgrootte is ingesteld op twee en tien bestanden of mappen die in de controlemap worden neergezet, worden er slechts twee opgehaald in elke scan. In de volgende scan, die zal plaatsvinden na de tijd die is opgegeven in het herhalingsinterval, worden de volgende twee bestanden opgehaald.
* Voor bestandspatronen kunnen beheerders reguliere expressies opgeven met extra ondersteuning voor jokertekenpatronen om bestandspatronen op te geven. Gecontroleerde map wijzigt de reguliere expressie ter ondersteuning van jokertekenpatronen zoals &amp;ast;.&amp;ast; of &amp;ast;.pdf. Deze jokertekenpatronen worden niet ondersteund door de reguliere expressies.
* Gecontroleerde map scant de invoermap op de invoer en weet niet of het bronbestand of de bronmap volledig naar de invoermap is gekopieerd voordat het bestand of de map wordt verwerkt. Ga als volgt te werk om ervoor te zorgen dat het bronbestand of de bronmap volledig naar de invoermap van de gecontroleerde map wordt gekopieerd voordat het bestand of de map wordt opgepakt:

   * De Wacht van het gebruik, die de tijd in milliseconden is die de Gecontroleerde Omslag van de laatste gewijzigde tijd wacht. Gebruik deze functie als u grote bestanden wilt verwerken. Als het downloaden van een bestand bijvoorbeeld 10 minuten duurt, geeft u de wachttijd op als 10&amp;ast;60 &amp;ast;1000 milliseconden. Hierdoor wordt voorkomen dat gecontroleerde map het bestand ophaalt als het niet zo oud is als 10 minuten.
   * Gebruik bestandspatroon uitsluiten en bestandspatroon opnemen. Als het bestandspatroon voor uitsluiten bijvoorbeeld is `ex*` en het bestandspatroon voor opnemen `in*`is, worden met Gecontroleerde map de bestanden opgehaald die beginnen met &#39;in&#39; en worden de bestanden die beginnen met &#39;ex&#39; niet opgepakt. Als u grote bestanden of mappen wilt kopiëren, wijzigt u eerst de naam van het bestand of de map, zodat de naam begint met &quot;ex&quot;. Nadat het bestand of de map met de naam &quot;ex&quot; volledig naar de gecontroleerde map is gekopieerd, wijzigt u de naam in &quot;in&amp;ast;&quot;.

* Gebruik de purgeduur om de resultatenmap schoon te houden. Met Gecontroleerde map worden alle bestanden gewist die ouder zijn dan de duur die in de purgeduur is vermeld. De duur is in dagen.
* Wanneer u een eindpunt van een gecontroleerde map toevoegt, wordt na het selecteren van de naam van de bewerking de invoerparametertoewijzing gevuld. Voor elke invoer van de bewerking wordt één toewijzingsveld voor de invoerparameter gegenereerd. Hier volgen voorbeelden van invoerparametertoewijzingen:

   * Voor `com.adobe.idp.Document` invoer: Als de de dienstverrichting een input van type heeft `Document`, kan de beheerder het toewijzingstype specificeren als `Variable`. Gecontroleerde map haalt de invoer op van de invoermap van de gecontroleerde map op basis van het bestandspatroon dat voor de invoerparameter is opgegeven. Als de beheerder `*.pdf` als parameter specificeert, zal elk dossier dat een uitbreiding van .pdf heeft worden opgenomen, worden omgezet in, `com.adobe.idp.Document`en de aangeroepen dienst.
   * Voor `java.util.Map` invoer: Als de de dienstverrichting een input van type heeft `Map`, kan de beheerder het toewijzingstype specificeren als `Variable` en een toewijzingswaarde met een patroon als `*.pdf`. Een service heeft bijvoorbeeld een kaart nodig van twee `com.adobe.idp.Document` objecten die twee bestanden in de invoermap vertegenwoordigen, zoals 1.pdf en 2.pdf. Controlemap maakt een kaart met de sleutel als bestandsnaam en de waarde als `com.adobe.idp.Document`.
   * Voor `java.util.List` invoer: Als de de dienstverrichting een input van het typeLijst heeft, kan de beheerder het toewijzingstype als specificeren `Variable` en een toewijzingswaarde met een patroon als `*.pdf`. ingaan. Wanneer PDF-bestanden in de invoermap worden neergezet, wordt met Gecontroleerde map een lijst gemaakt met de `com.adobe.idp.Document` objecten die deze bestanden vertegenwoordigen en wordt de doelservice geactiveerd.
   * Voor `java.lang.String`: De beheerder heeft twee opties. Ten eerste kan de beheerder het toewijzingstype opgeven als `Literal` en een toewijzingswaarde invoeren als een tekenreeks, zoals `hello.` Gecontroleerde map die de service aanroept met de tekenreeks `hello`. Ten tweede kan de beheerder het toewijzingstype als een `Variable` en een toewijzingswaarde met een patroon als `*.txt`opgeven. In het laatste geval worden bestanden met de extensie .txt gelezen als een document dat als een tekenreeks wordt gecomprimeerd om de service aan te roepen.
   * Primitief Java-type: De beheerder kan het toewijzingstype als `Literal` en de waarde specificeren. Gecontroleerde map activeert de service met de opgegeven waarde.

* Controlemap is bedoeld voor gebruik met documenten. De ondersteunde uitvoerbestanden zijn `com.adobe.idp.Document`, `org.w3c.Document`, `org.w3c.Node`en een lijst en kaart van deze typen. Elk ander type resulteert in een foutuitvoer in de map failure.
* Als de resultaten niet in de resultaatomslag zijn, verifieer de mislukkingsomslag om te zien of is een mislukking voorgekomen.
* Controlemap werkt het beste als deze wordt gebruikt in de asynchrone modus. In deze modus wordt de aanroepingsaanvraag door de gecontroleerde map in de wachtrij geplaatst en wordt een nieuwe aanroep uitgevoerd. De wachtrij wordt vervolgens asynchroon verwerkt. Wanneer de Asynchrone optie niet wordt geplaatst, roept de Gecontroleerde Omslag de doeldienst synchroon aan en de Motor van het Proces wacht tot de dienst met het verzoek wordt gedaan en de resultaten worden veroorzaakt. Als het verwerken van de aanvraag lang duurt voor de doelservice, kunnen time-outfouten optreden in de gecontroleerde map.
* Het maken van gecontroleerde mappen voor import- en exportbewerkingen staat het onttrekken van bestandsextensies niet toe. Wanneer de service Formuliergegevensintegratie wordt aangeroepen met gecontroleerde mappen, komt het extensietype voor het uitvoerbestand mogelijk niet overeen met de gewenste uitvoerindeling voor het documentobjecttype. Als het invoerbestand naar een controlemap die de exportbewerking activeert bijvoorbeeld een XFA-formulier is dat gegevens bevat, moet de uitvoer een XDP-gegevensbestand zijn. Als u een uitvoerbestand met de juiste bestandsnaamextensie wilt verkrijgen, kunt u dit opgeven in de toewijzing van de uitvoerparameter. In dit voorbeeld kunt u %F.xdp gebruiken voor de toewijzing van de uitvoerparameter.
* De gecontroleerde Omslag kan inputdossiers verwerken alvorens zij volledig aan de omslag worden gekopieerd. Het vergrendelen van bestanden is niet verplicht in UNIX, zoals in Windows. Als een bestand naar een gecontroleerde map wordt gekopieerd, kan het daarom zijn dat het bestand met de gecontroleerde map naar het werkgebied wordt verplaatst zonder te wachten tot de bestandskopie is voltooid. Hierdoor wordt slechts een gedeelte van het invoerbestand verwerkt. Er zijn momenteel twee tijdelijke oorzaken:

   * Workaround 1

      1. Geef een patroon op voor Bestandspatroon uitsluiten, zoals tijdelijk&amp;ast;.ps.
      1. Kopieer bestanden die beginnen met temp (bijvoorbeeld temp1.ps) naar de gecontroleerde map.
      1. Nadat het bestand volledig naar de gecontroleerde map is gekopieerd, wijzigt u de naam van het bestand in overeenstemming met het patroon dat is opgegeven voor Inclusief bestandspatroon. Controlemap verplaatst het voltooide bestand vervolgens naar het werkgebied.
   * Workaround 2

      Als u weet hoeveel tijd het maximaal duurt om uw bestanden naar een gecontroleerde map te kopiëren, geeft u de tijd op in seconden voor de wachttijd. Controlemap wacht dan de opgegeven tijdsduur voordat het bestand naar het werkgebied wordt verplaatst.

      Dit is geen kwestie voor dossiers op Vensters omdat de Vensters een dossier vergrendelt wanneer één draad schrijft. Dit is echter een probleem voor mappen in Windows. Voor mappen moet u de stappen in Workaround 1 volgen.


* Als het het eindpuntattribuut van de Naam van de Omslag van het Behouden voor Gecontroleerde Omslag aan een ongeldig folderweg wordt geplaatst, wordt de het opvoeren folder niet schoongemaakt aangezien het zou moeten zijn. De map bevat nog steeds het verwerkte bestand en de tijdelijke map.

## Servicespecifieke aanbevelingen voor gecontroleerde mappen {#service-specific-recommendations-for-watched-folders}

Voor alle services moet u de batchgrootte en het herhalingsinterval van de gecontroleerde map aanpassen, zodat de snelheid waarmee gecontroleerde map nieuwe bestanden en mappen oppakt voor verwerking niet hoger is dan de snelheid van de taken die door de AEM-formulierserver kunnen worden verwerkt. Welke parameters werkelijk moeten worden gebruikt, is afhankelijk van het aantal gecontroleerde mappen dat wordt geconfigureerd, welke services gecontroleerde mappen gebruiken en hoe intensief de taken zijn voor de processor.

### Aanbevelingen voor PDF-service genereren {#generate-pdf-service-recommendations}

* Met de service PDF genereren kunt u slechts één bestand tegelijk converteren voor de volgende bestandstypen: Microsoft Word, Microsoft Excel, Microsoft PowerPoint, Microsoft Project, AutoCAD, Adobe Photoshop®, Adobe FrameMaker® en Adobe PageMaker®. Het gaat om langdurige banen; Zorg er daarom voor dat de batchgrootte laag blijft. Verhoog ook het herhalingsinterval als er meer knooppunten in de cluster zijn.
* Voor de bestandstypen PostScript (PS), Encapsulated PostScript (EPS) en Afbeeldingen kan de service PDF genereren verschillende bestanden parallel verwerken. U zou de grootte van de groep van de zittingsboon zorgvuldig moeten stemmen (die het aantal omzettingen bepaalt die parallel zullen worden gedaan) afhankelijk van de capaciteit van uw server en het aantal knopen in de cluster. Vergroot de batch vervolgens tot een getal dat gelijk is aan de grootte van de groep met sessies voor de bestandstypen die u wilt converteren. De stemfrequentie moet worden bepaald door het aantal knooppunten in de cluster; Maar omdat de service PDF genereren dit soort taken heel snel verwerkt, kunt u het herhalingsinterval op een lage waarde instellen, bijvoorbeeld 5 of 10.
* Hoewel met de service PDF genereren slechts één OpenOffice-bestand tegelijk kan worden geconverteerd, verloopt de conversie vrij snel. De bovenstaande logica voor PS-, EPS- en afbeeldingsconversies is ook van toepassing op OpenOffice-conversies.
* Om eenvormige ladingsdistributie in de cluster toe te laten, houd de partijgrootte laag en verhoog het herhalingsinterval.

### aanbevelingen van de streepjescodeneservice {#barcoded-forms-service-recommendations}

* Voor de beste prestaties bij het verwerken van formulieren met streepjescodes (kleine bestanden) voert u `10` bij Batchgrootte en `2` bij Herhalingsinterval in.
* Wanneer veel bestanden in de invoermap worden geplaatst, kunnen er fouten optreden met verborgen bestanden die *thumbs.db* worden genoemd. Daarom wordt u aangeraden het Include-bestandspatroon voor de include-bestanden in te stellen op dezelfde waarde die voor de invoervariabele is opgegeven (bijvoorbeeld `*.tiff`). Hiermee voorkomt u dat de gecontroleerde map de DB-bestanden verwerkt.
* Een waarde voor Batchgrootte van `5` en Herhalingsinterval van `2` is doorgaans voldoende omdat de service Barcoded Forms meestal ongeveer 0,5 seconden nodig heeft om één streepjescode te verwerken.
* Gecontroleerde map wacht niet tot de procesengine de taak heeft voltooid voordat nieuwe bestanden of mappen worden opgehaald. De controlemap wordt voortdurend gescand en de doelservice wordt aangeroepen. Dit gedrag kan de motor overbelasten, veroorzakend hulpproblemen en onderbreking. Controleer of u het interval met herhalingen en de grootte van de batch gebruikt om de invoer van de gecontroleerde map te vertragen. U kunt het herhalingsinterval verhogen en de partijgrootte verminderen als meer gecontroleerde omslagen bestaan of throttling op het eindpunt toelaten. Zie [Informatie over vertragen](configuring-watched-folder-endpoints.md#about-throttling)voor informatie over vertragen.
* Gecontroleerde map vormt een weerspiegeling van de gebruiker die is opgegeven in de gebruikersnaam en de domeinnaam. Gecontroleerde map roept de service aan als deze gebruiker wanneer deze rechtstreeks wordt aangeroepen of wanneer het proces van korte duur is. Voor een langdurig proces, wordt het proces aangehaald met de context van het Systeem. Beheerders kunnen beleidsregels voor het besturingssysteem voor gecontroleerde mappen instellen om te bepalen welke gebruiker toegang toestaat of weigert.
* Gebruik bestandspatronen om resultaten, fouten en mappen te ordenen. (Zie [Bestandspatronen](configuring-watched-folder-endpoints.md#about-file-patterns).)

* De gecontroleerde omslag baseert zich op de planner van het Kwartz voor het aftasten van de gecontroleerde omslagen. De planner van het Kwartz heeft een draadpool om hen af te tasten. Als het herhalingsinterval voor de gecontroleerde map erg laag is (&lt; 5 seconden) en de batch groot is (> 2), kan er een race plaatsvinden. Wanneer deze voorwaarde zich voordoet, wordt één bestand opgehaald door twee kwartthreads:

   * Één van de draden vindt met succes het dossier en haalt de doeldienst met het dossier aan.
   * De tweede thread ziet het bestand, maar mislukt wanneer wordt geprobeerd uit te zoeken of het bestand geldig is (lees- of schrijfbestand). Dit veroorzaakt fout-fouten die aangeven dat het bestand niet kan worden verwerkt omdat het alleen-lezen is. Dit gebeurt alleen met een lage herhalingsinterval en een hoge batchgrootte.

