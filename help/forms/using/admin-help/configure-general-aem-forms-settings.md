---
title: Algemene AEM Forms-instellingen
description: Leer de pagina-instellingen voor Core Configurations in de beheerconsole te configureren die de systeemprestaties kunnen verbeteren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
exl-id: e1519477-b5a8-4947-8597-26b945a3b819
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 1b76b30d8db59e6ad98af1d29f17443442d5378e
workflow-type: tm+mt
source-wordcount: '1768'
ht-degree: 0%

---

# Algemene AEM Forms-instellingen {#general-aem-forms-settings}

De pagina Core Configurations in de beheerconsole biedt instellingen die de systeemprestaties kunnen verbeteren. Start de toepassingsserver opnieuw nadat u deze instellingen hebt geconfigureerd of bijgewerkt.

>[!NOTE]
>
> * Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.
> * U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

Voor informatie over het toelaten van veilige reservewijze, zie [ Toelatend en onbruikbaar makend veilige reservewijze ](/help/forms/using/admin-help/enabling-disabling-safe-backup-mode.md#enabling-and-disabling-safe-backup-mode).


>[!NOTE]
>
>De bestanden in de tijdelijke map en de langlevende documenten in de hoofdmap van de algemene documentopslag (GDS) kunnen vertrouwelijke gebruikersgegevens bevatten, zoals informatie die speciale gegevens vereist wanneer deze worden geopend met behulp van de API&#39;s of gebruikersinterfaces. Daarom is het belangrijk dat deze map correct wordt beveiligd met alle methoden die beschikbaar zijn voor het besturingssysteem. Het wordt aanbevolen dat alleen de account van het besturingssysteem waarmee de toepassingsserver wordt uitgevoerd, lees- en schrijftoegang heeft tot deze map.


1. Selecteer **[!UICONTROL Settings > Core System Settings > Configurations]** in de beheerconsole.
1. Wijzig op de pagina Core Configurations de gewenste opties en selecteer **[!UICONTROL OK]** . Voor details over de opties, zie [ de opties van de Configuraties van de Kern ](configure-general-aem-forms-settings.md#core-configurations-options).


## Opties voor Core Configurations {#core-configurations-options}

**Plaats van tijdelijke folder** de folderweg waar de AEM vormen product tijdelijke dossiers zullen creëren. Als de waarde van deze instelling leeg is, wordt de locatie standaard ingesteld op de Temp-map van het systeem. Zorg ervoor dat de tijdelijke map een beschrijfbare map is.

>[!NOTE]
>
>Zorg ervoor dat de tijdelijke map zich op het lokale bestandssysteem bevindt. AEM formulieren ondersteunen geen tijdelijke map op een externe locatie.

***ndash de Globale folder van de documentopslag van het 0} document de wortelfolder van de documentopslag (GDS) wordt gebruikt voor de volgende doeleinden:**

* Langlevende documenten opslaan. Langlevende documenten hebben geen verlooptijd en blijven bestaan totdat ze worden verwijderd (bijvoorbeeld de PDF-bestanden die in een werkstroomproces worden gebruikt). De langlevende documenten zijn een kritiek deel van de algemene systeemstaat. Als sommige of al deze documenten verloren gaan of beschadigd raken, kan de Forms-server instabiel worden. Daarom is het belangrijk dat deze map wordt opgeslagen op een RAID-apparaat.
* Tijdelijke documenten opslaan die nodig zijn tijdens de verwerking.

>[!NOTE]
>
>U kunt ook de opslag van documenten inschakelen in de AEM-formulierdatabase. Systeemprestaties zijn echter beter wanneer u de GDS gebruikt.

* Documenten overbrengen tussen knooppunten in een cluster. Als u AEM formulieren uitvoert in een geclusterde omgeving, moet deze map toegankelijk zijn vanaf alle knooppunten in de cluster.
* Inkomende parameters ontvangen van externe API-aanroepen.

Als u geen GDS-hoofdmap opgeeft, wordt de map standaard ingesteld op een toepassingsservermap:

* `[JBOSS_HOME]/server/<server>/svcnative/DocumentStorage`
* `[WEBSPHERE_HOME]/installedApps/adobe/'server'/DocumentStorage`
* `[WEBLOGIC_HOME]/user_projects/<domain>/'server'/adobe/AEMformsserver/DocumentStorage`

>[!NOTE]
>
>Het wijzigen van de waarde van de instelling van de GDS-hoofdmap moet met speciale zorg worden uitgevoerd. In de GDS-map worden zowel bestanden met een lange levensduur die in een proces worden gebruikt als essentiële AEM productcomponenten van formulieren opgeslagen. Het wijzigen van de locatie van de GDS-map is een belangrijke systeemwijziging. Als u de locatie van de GDS-directory niet correct configureert, worden AEM formulieren onbruikbaar en moeten AEM formulieren mogelijk volledig opnieuw worden geïnstalleerd. Als u een nieuwe locatie voor de GDS-map opgeeft, moet de toepassingsserver worden afgesloten en moeten de gegevens worden gemigreerd voordat de server opnieuw kan worden gestart. De systeembeheerder moet alle bestanden van de oude locatie naar de nieuwe locatie verplaatsen, maar de interne mapstructuur behouden.

>[!NOTE]
>
>Geef niet dezelfde map op voor de tijdelijke map en de GDS-map.

Voor extra informatie over de GDS folder, zie [ Voorbereidend om AEM vormen (Één enkele Server) te installeren ](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63).

**Plaats van de folder van de Doopvonten van de Server van de Adobe** *ndash; Type de weg aan de folder die de doopvonten van de server van de Adobe bevat. Deze lettertypen worden geïnstalleerd met AEM formulieren. De standaardplaats voor deze doopvonten is de [ aem-vormen wortel ]/de folder van doopvonten. Als deze map niet toegankelijk is, kunt u de lettertypen elders kopiëren en deze instelling gebruiken om de nieuwe locatie op te geven.

**Plaats van de folder van de Doopvonten van de Klant** *ndash; Type de weg aan een folder die extra doopvonten bevat die u wilt gebruiken.

***nota **: De doopvonten worden genomen van het geheime voorgeheugen van de systeemdoopvont van Vensters en een systeemnieuw begin wordt vereist om het geheime voorgeheugen bij te werken. Nadat u de lettertypemap voor de klant hebt opgegeven, dient u het systeem waarop AEM formulieren zijn geïnstalleerd opnieuw te starten.*

**Plaats van de folder van de Doopvonten van het Systeem** *ndash; Type de weg aan de doopvontenfolder die uw werkend systeem verstrekte. Er kunnen meerdere mappen worden toegevoegd, gescheiden door een puntkomma **;** .

**Plaats van het dossier van de Configuratie van de Diensten van Gegevens** *ndash; Specificeert de plaats van het dienst-config.xml- dossier. Dit bestand is standaard ingesloten in het bestand adobe-core-appserver.ear en is niet toegankelijk voor de gebruiker. Een exemplaar van het standaard dienst-config.xml- dossier is in [ aem-vormen wortel ] \sdk\misc\DataServices\Server-Configuration. Als u dit bestand hebt gewijzigd en verplaatst, typt u de nieuwe locatie in dit veld.

Het de configuratiedossier van de Diensten van Gegevens staat aanpassing van de montages van de Diensten van Gegevens, zoals authentificatietype en zuivert output toe.

Deze instelling is standaard leeg.

**Standaard document maximum gealigneerde grootte (bytes)** *ndash; het maximumaantal bytes die in geheugen worden gehouden wanneer het overgaan van documenten tussen diverse AEM vormcomponenten. Gebruik deze instelling voor het afstemmen van de prestaties. Documenten die kleiner zijn dan dit nummer, worden in het geheugen opgeslagen en in de database opgeslagen. Documenten die dit maximum overschrijden, worden opgeslagen op de vaste schijf.

Deze instelling is verplicht. De standaardwaarde is 65536 bytes.

**Standaard document verwijderingstijd (seconden)** *ndash; De maximumhoeveelheid tijd, in seconden, waarin een document dat tussen diverse AEM vormcomponenten wordt overgegaan als actief wordt beschouwd. Nadat deze tijd is verstreken, kunnen bestanden die worden gebruikt om dit document op te slaan, worden verwijderd. Gebruik deze instelling om het gebruik van schijfruimte te regelen.

Deze instelling is verplicht. De standaardwaarde is 600 seconden.

**het kneepinterval van het Document (seconden)** *ndash; De hoeveelheid tijd, in seconden, tussen pogingen om dossiers te schrappen die niet meer nodig zijn en werden gebruikt om documentgegevens tussen de diensten over te gaan.

Deze instelling is verplicht. De standaardwaarde is 30 seconden.

**laat FIPS** *ndash toe; selecteer deze optie om FIPS wijze toe te laten. Federal Information Processing Standard (FIPS) 140-2 is een door de overheid van de VS gedefinieerde cryptologienorm. Wanneer het lopen op FIPS wijze, beperkt AEM vormen gegevensbescherming tot FIPS 140-2 goedgekeurde algoritmen door RSA BSAFE Crypto-C 2.1 encryptiemodule te gebruiken.

De FIPS-modus ondersteunt geen versleutelingsalgoritmen die worden gebruikt in eerdere Adobe Acrobat®-versies dan 7.0. Als de FIPS-modus is ingeschakeld en u de coderingsservice gebruikt om de PDF te coderen met een wachtwoord met een compatibiliteitsniveau ingesteld op Acrobat 5, mislukt de coderingpoging met een fout.

In het algemeen geldt dat wanneer FIPS is ingeschakeld, de Assembler-service geen wachtwoordversleuteling toepast op documenten. Als dit wordt geprobeerd, wordt een FIPSModeException geworpen erop wijzend dat de &quot;encryptie van het Wachtwoord niet op FIPS wijze wordt toegelaten.&quot; Bovendien wordt het element Document Description XML (DDX) PDFsFromBookmarks niet ondersteund in de FIPS-modus wanneer het basisdocument met een wachtwoord is gecodeerd.

>[!NOTE]
>
>AEM formuliersoftware valideert geen code om FIPS-compatibiliteit te garanderen. Het verstrekt een FIPS verrichtingswijze zodat FIPS-Goedgekeurde algoritmen voor cryptografische diensten van de FIPS-Goedgekeurde bibliotheken (RSA) worden gebruikt.

**laat WSDL** *ndash toe; selecteer deze optie om de generatie van de Definitie van de Dienst van het Web van de Taal (WSDL) voor alle diensten toe te laten die deel van AEM vormen uitmaken.

Schakel deze optie in ontwikkelomgevingen in waarin ontwikkelaars de WSDL-generatie gebruiken om hun clienttoepassingen te maken. U kunt verkiezen om de generatie van WSDL in een productiemilieu onbruikbaar te maken vermijden blootstellend de interne details van de dienst.

**laat documentopslag in het gegevensbestand** *ndash toe; selecteer deze optie om documenten van lange duur in het AEM vormengegevensbestand op te slaan. Als u deze optie inschakelt, wordt er geen GDS-map meer nodig. Als u deze optie kiest, worden back-ups AEM formulieren eenvoudiger. Als u alleen de GDS gebruikt, betekent een back-up het plaatsen van de AEM formAEM-formulieren in de back-upmodus en het vervolgens voltooien van de back-ups van de database en de GDS. Als u de databaseoptie selecteert, bestaat de back-up uit het voltooien van de databaseback-up voor een nieuwe installatie of het voltooien van de databaseback-up en de eenmalige back-up van de GDS voor een upgrade. Het is mogelijk dat extra beheer van uw database vereist is om taken en gegevens te wissen in vergelijking met een configuratie die alleen voor GDS is bedoeld. (Zie Back-upopties als database wordt gebruikt voor documentopslag.)

**laat de aanroepingsstatistiek van DSC** *ndash toe; Wanneer deze optie wordt geselecteerd, AEM vormen spoor aanroepingsstatistieken zoals het aantal aanroepen, hoeveelheid tijd wordt genomen om aan te halen, en aantal fouten in aanroepen. Deze informatie wordt opgeslagen in een boon JMX zodat u Java™ JConsole of derdesoftware kunt gebruiken om de statistieken te bekijken. Als u deze statistieken niet wilt zien, schakelt u deze optie uit om de prestaties van AEM formulieren te verbeteren.

**laat RDS** *ndash toe; het selecteren van deze optie laat de Verre server van de Diensten van de Ontwikkeling (RDS) binnen AEM vormen toe. Wanneer deze optie wordt toegelaten, kunnen de cliënt-zijhulpmiddelen met de Diensten van Gegevens in wisselwerking staan om dingen te doen zoals opstellen of modellen ongedaan maken om bestemmingen en eindpunten tot stand te brengen, of te weten te komen welke modellen in eindpunten zijn opgesteld. Deze optie is standaard niet geselecteerd.

**staat niet-beveiligde RDS verzoek** *ndash toe; Wanneer deze optie wordt geselecteerd, te hoeven de verzoeken RDS niet om https te gebruiken. Door gebrek, wordt deze optie niet geselecteerd en alle mededelingen aan de Diensten van Gegevens moeten https verzoeken zijn.

**staat niet-beveiligde documentupload van de toepassingen van Flex** *ndash toe; Het dossier uploadt servlet die wordt gebruikt om documenten van de toepassingen van de Flex® van de Adobe aan AEM vormen te uploaden vereist dat de gebruikers voor authentiek worden verklaard en worden gemachtigd alvorens zij documenten kunnen uploaden. Aan de gebruiker moet de gebruikersrol Document Upload Application of een andere rol worden toegewezen die de machtiging Document uploaden bevat. Zo voorkomt u dat onbevoegde gebruikers documenten uploaden naar de AEM Forms-server. Selecteer deze optie als u deze beveiligingsfunctie wilt uitschakelen in een ontwikkelomgeving of voor achterwaartse compatibiliteit met eerdere versies van AEM formulieren. Deze optie is standaard niet geselecteerd. Zie &quot;AEM formulieren aanroepen met AEM formulieren verwijderen&quot; in Programmeren met AEM formulieren voor meer informatie.

**staat niet-beveiligde documentupload van de toepassingen van SDK van Java** *ndash toe; de uploads van HTTP DocumentManager moeten worden beveiligd. Standaard is voor HTTP-uploads verificatie en verificatie vereist voordat gebruikers documenten kunnen uploaden. De gebruiker moet de rol van de Gebruiker van de Diensten of een andere rol worden toegewezen die de Dienst bevat roept toestemming. Zo voorkomt u dat onbevoegde gebruikers documenten uploaden naar de Forms-server. Selecteer deze optie als u deze beveiligingsfunctie wilt uitschakelen in een ontwikkelomgeving, voor achterwaartse compatibiliteit met eerdere versies van AEM formulieren of op basis van uw firewallinstelling. Deze optie is standaard niet geselecteerd. Zie &quot;AEM formulieren aanroepen met de Java API&quot; in Programmeren met AEM formulieren voor meer informatie.
