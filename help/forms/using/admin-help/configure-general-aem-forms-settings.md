---
title: Algemene AEM Forms-instellingen
seo-title: Algemene AEM Forms-instellingen
description: Leer de pagina-instellingen voor Core Configurations in de beheerconsole te configureren die de systeemprestaties kunnen verbeteren.
seo-description: Leer de pagina-instellingen voor Core Configurations in de beheerconsole te configureren die de systeemprestaties kunnen verbeteren.
uuid: 940680fd-b7ab-4376-aa5b-e139223522ea
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.4/FORMS
discoiquuid: bd648c38-731b-420e-973d-a4728b69868e
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7
workflow-type: tm+mt
source-wordcount: '1728'
ht-degree: 0%

---


# Algemene AEM Forms-instellingen {#general-aem-forms-settings}

De pagina Core Configurations in de beheerconsole biedt instellingen die de systeemprestaties kunnen verbeteren. Nadat u deze instellingen hebt geconfigureerd of bijgewerkt, start u de toepassingsserver opnieuw op.

Zie [Veilige back-upmodus inschakelen en uitschakelen](/help/forms/using/admin-help/enabling-disabling-safe-backup-mode.md#enabling-and-disabling-safe-backup-mode) voor informatie over het inschakelen van de veilige back-upmodus.


>[!NOTE]
>
>De bestanden in de tijdelijke map en de langlevende documenten in de hoofdmap van de algemene documentopslag (GDS) kunnen vertrouwelijke gebruikersgegevens bevatten, zoals informatie die speciale gegevens vereist wanneer deze worden geopend met de API&#39;s of gebruikersinterfaces. Daarom is het belangrijk dat deze map correct wordt beveiligd met alle methoden die beschikbaar zijn voor het besturingssysteem. Het wordt aanbevolen dat alleen de account van het besturingssysteem waarmee de toepassingsserver wordt uitgevoerd, lees- en schrijftoegang heeft tot deze map.


1. Klik in de beheerconsole op **[!UICONTROL Settings > Core System Settings > Configurations]**.
1. Wijzig op de pagina Core Configurations de gewenste opties en klik op **[!UICONTROL OK]**. Zie [Core Configurations options](configure-general-aem-forms-settings.md#core-configurations-options) voor meer informatie over de opties.


## Opties voor kernconfiguraties {#core-configurations-options}

**Locatie van tijdelijke** mapHet directorypad waar AEM formulieren tijdelijke productbestanden maken. Als de waarde van deze instelling leeg is, wordt de locatie standaard ingesteld op de Temp-map van het systeem. Zorg ervoor dat de tijdelijke map een beschrijfbare map is.

>[!NOTE]
>
>Zorg ervoor dat de tijdelijke map zich op het lokale bestandssysteem bevindt. AEM formulieren ondersteunen geen tijdelijke map op een externe locatie.

**Hoofdmap** van algemene documentopslagDe hoofdmap van algemene documentopslag (GDS) wordt gebruikt voor de volgende doeleinden:

* Langlevende documenten opslaan. Langlevende documenten hebben geen verlooptijd en blijven bestaan totdat ze worden verwijderd (bijvoorbeeld de PDF-bestanden die worden gebruikt in een werkstroomproces). De langlevende documenten zijn een kritiek deel van de algemene systeemstaat. Als sommige of al deze documenten verloren gaan of beschadigd raken, wordt de formulierserver mogelijk instabiel. Daarom is het belangrijk dat deze map wordt opgeslagen op een RAID-apparaat.
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
>Het wijzigen van de waarde van de instelling van de GDS-hoofdmap moet met speciale zorg worden uitgevoerd. De GDS-map wordt gebruikt om zowel bestanden met een lange levensduur die in een proces worden gebruikt als essenti??le onderdelen van AEM formulierproduct op te slaan. Het wijzigen van de locatie van de GDS-map is een belangrijke systeemwijziging. Als u de locatie van de GDS-directory niet correct configureert, worden AEM formulieren onbruikbaar en moeten AEM formulieren mogelijk volledig opnieuw worden ge??nstalleerd. Als u een nieuwe locatie voor de GDS-map opgeeft, moet de toepassingsserver worden afgesloten en moeten de gegevens worden gemigreerd voordat de server opnieuw kan worden gestart. De systeembeheerder moet alle bestanden van de oude locatie naar de nieuwe locatie verplaatsen, maar de interne mapstructuur behouden.

>[!NOTE]
>
>Geef niet dezelfde map op voor de tijdelijke map en de GDS-map.

Voor extra informatie over de GDS folder, zie [Voorbereidend om AEM vormen (Enige Server) ](https://www.adobe.com/go/learn_aemforms_prepareInstallsingle_63) te installeren.

**Locatie van de** map Adobe Server FontsTyp het pad naar de map met de Adobe-serverlettertypen. Deze lettertypen worden ge??nstalleerd met AEM formulieren. De standaardlocatie voor deze lettertypen is de map [aem-forms root]/fonts. Als deze map niet toegankelijk is, kunt u de lettertypen elders kopi??ren en deze instelling gebruiken om de nieuwe locatie op te geven.

**Locatie van de** map Customer FontsTyp het pad naar een map met extra lettertypen die u wilt gebruiken.

***opmerking **: De lettertypen worden gekozen uit de cache van het Windows-systeemlettertype en het systeem moet opnieuw worden opgestart om de cache bij te werken. Nadat u de lettertypemap voor de klant hebt opgegeven, dient u het systeem waarop AEM formulieren zijn ge??nstalleerd opnieuw te starten.*

**Locatie van de** map System FontsTyp het pad naar de map fonts die door het besturingssysteem is opgegeven. U kunt meerdere mappen toevoegen, gescheiden door een puntkomma **;**.

**De plaats van het** dossier van de Configuratie van de Diensten van GegevensSpecificeert de plaats van het dienst-config.xml- dossier. Dit bestand is standaard ingesloten in het bestand adobe-core-appserver.ear en is niet toegankelijk voor de gebruiker. Een exemplaar van het standaard dienst-config.xml- dossier wordt gevestigd in [aem-vormen wortel]\sdk\misc\DataServices\Server-Configuration. Als u dit bestand hebt gewijzigd en verplaatst, typt u de nieuwe locatie in dit veld.

Het de configuratiedossier van de Diensten van Gegevens staat aanpassing van de montages van de Diensten van Gegevens, zoals authentificatietype en zuivert output toe.

Deze instelling is standaard leeg.

**Standaard document max. inline-grootte (bytes)** Het maximum aantal bytes dat in het geheugen wordt bewaard wanneer documenten tussen verschillende AEM formuliercomponenten worden doorgegeven. Gebruik deze instelling voor het afstemmen van de prestaties. Documenten die kleiner zijn dan dit nummer, worden in het geheugen opgeslagen en in de database opgeslagen. Documenten die dit maximum overschrijden, worden opgeslagen op de vaste schijf.

Deze instelling is verplicht. De standaardwaarde is 65536 bytes.

**Standaardtime-out voor het verwijderen van documenten (seconden)** De maximale hoeveelheid tijd in seconden waarin een document dat wordt doorgegeven tussen verschillende AEM formuliercomponenten, als actief wordt beschouwd. Nadat deze tijd is verstreken, kunnen bestanden die worden gebruikt om dit document op te slaan, worden verwijderd. Gebruik deze instelling om het gebruik van schijfruimte te regelen.

Deze instelling is verplicht. De standaardwaarde is 600 seconden.

**Het interval van** de veeggebaar van het document (seconden)De hoeveelheid tijd, in seconden, tussen pogingen om dossiers te schrappen die niet meer nodig zijn en werden gebruikt om documentgegevens tussen de diensten over te gaan.

Deze instelling is verplicht. De standaardwaarde is 30 seconden.

**Schakel** FIPSS in en selecteer deze optie om de FIPS-modus in te schakelen. Federal Information Processing Standard (FIPS) 140-2 is een door de overheid van de VS gedefinieerde cryptologienorm. Wanneer het lopen op FIPS wijze, beperkt AEM vormen gegevensbescherming tot FIPS 140-2 goedgekeurde algoritmen door RSA BSAFE Crypto-C 2.1 encryptiemodule te gebruiken.

De FIPS-modus biedt geen ondersteuning voor versleutelingsalgoritmen die worden gebruikt in eerdere Adobe Acrobat??-versies dan versie 7.0. Als de FIPS-modus is ingeschakeld en u de coderingsservice gebruikt om de PDF te coderen met een wachtwoord waarvan het compatibiliteitsniveau op Acrobat 5 is ingesteld, mislukt de coderingpoging.

In het algemeen geldt dat wanneer FIPS is ingeschakeld, de Assembler-service geen wachtwoordversleuteling toepast op documenten. Als dit wordt geprobeerd, wordt een FIPSModeException geworpen erop wijzend dat de &quot;encryptie van het Wachtwoord niet op FIPS wijze wordt toegelaten.&quot; Bovendien wordt het element Document Description XML (DDX) PDFsFromBookmarks niet ondersteund in de FIPS-modus wanneer het basisdocument met een wachtwoord is gecodeerd.

>[!NOTE]
>
>AEM formuliersoftware valideert geen code om FIPS-compatibiliteit te garanderen. Het verstrekt een FIPS verrichtingswijze zodat FIPS-Goedgekeurde algoritmen voor cryptografische diensten van de FIPS-Goedgekeurde bibliotheken (RSA) worden gebruikt.

**Schakel** WSDLS in en selecteer deze optie om WSDL (Web Service Definition Language)-generatie in te schakelen voor alle services die deel uitmaken van AEM formulieren.

Schakel deze optie in ontwikkelomgevingen in waarin ontwikkelaars de WSDL-generatie gebruiken om hun clienttoepassingen te maken. U kunt verkiezen om de generatie van WSDL in een productiemilieu onbruikbaar te maken vermijden blootstellend de interne details van de dienst.

**Documentopslag inschakelen in de** databaseSelecteer deze optie om langlevende documenten op te slaan in de database met AEM formulieren. Als u deze optie inschakelt, wordt er geen GDS-map meer nodig. Als u deze optie kiest, worden back-ups AEM formulieren eenvoudiger. Als u alleen de GDS gebruikt, betekent een back-up het plaatsen van de AEM formAEM-formulieren in de back-upmodus en het vervolgens voltooien van de back-ups van de database en de GDS. Als u de databaseoptie selecteert, bestaat de back-up uit het voltooien van de databaseback-up voor een nieuwe installatie of het voltooien van de databaseback-up en de eenmalige back-up van de GDS voor een upgrade. Het is mogelijk dat extra beheer van uw database vereist is om taken en gegevens te wissen in vergelijking met een configuratie die alleen voor GDS is bedoeld. (Zie Back-upopties als database wordt gebruikt voor documentopslag.)

**DSC-aanroepingsstatistiek inschakelenAls deze optie is geselecteerd, worden AEM aanroepingsstatistieken bijgehouden, zoals het aantal aanroepen, de hoeveelheid tijd die nodig is om aan te roepen en het aantal fouten in aanroepen.** Deze informatie wordt opgeslagen in een boon JMX zodat u Java??? JConsole of derdesoftware kunt gebruiken om de statistieken te bekijken. Als u deze statistieken niet wilt zien, schakelt u deze optie uit om de prestaties van AEM formulieren te verbeteren.

**Schakel** RDSSelecting deze optie in om de RDS-servlet (Remote Development Services) in AEM formulieren in te schakelen. Wanneer deze optie wordt toegelaten, kunnen de cli??nt-zijhulpmiddelen met de Diensten van Gegevens in wisselwerking staan om dingen te doen zoals opstellen of modellen ongedaan maken om bestemmingen en eindpunten tot stand te brengen, of te weten te komen welke modellen in eindpunten zijn opgesteld. Deze optie is standaard niet geselecteerd.

**Niet-beveiligde RDS-** aanvraag toestaanAls deze optie is geselecteerd, hoeven RDS-aanvragen niet https te gebruiken. Door gebrek, wordt deze optie niet geselecteerd en alle mededelingen aan de Diensten van Gegevens moeten https verzoeken zijn.

**Uploaden van niet-beveiligde documenten vanuit Flex-toepassingen toestaan:** voor het uploaden van bestanden die worden gebruikt om documenten vanuit Adobe Flex??-toepassingen te uploaden naar AEM formulieren, moeten gebruikers zijn geverifieerd en geautoriseerd voordat ze documenten kunnen uploaden. Aan de gebruiker moet de gebruikersrol Document Upload Application of een andere rol worden toegewezen die de machtiging Document uploaden bevat. Zo voorkomt u dat onbevoegde gebruikers documenten uploaden naar de AEM formulierserver. Selecteer deze optie als u deze beveiligingsfunctie wilt uitschakelen in een ontwikkelomgeving of voor achterwaartse compatibiliteit met eerdere versies van AEM formulieren. Deze optie is standaard niet geselecteerd. Zie &quot;AEM formulieren aanroepen met AEM formulieren verwijderen&quot; in Programmeren met AEM formulieren voor meer informatie.

**Uploaden van niet-beveiligde documenten vanuit Java SDK-toepassingen toestaan:** HTTP DocumentManager-uploads moeten zijn beveiligd. Standaard is voor HTTP-uploads verificatie en verificatie vereist voordat gebruikers documenten kunnen uploaden. De gebruiker moet de rol van de Gebruiker van de Diensten of een andere rol worden toegewezen die de Dienst bevat roept toestemming. Zo voorkomt u dat onbevoegde gebruikers documenten uploaden naar de formulierserver. Selecteer deze optie als u deze beveiligingsfunctie wilt uitschakelen in een ontwikkelomgeving, voor achterwaartse compatibiliteit met eerdere versies van AEM formulieren of op basis van uw firewallinstelling. Deze optie is standaard niet geselecteerd. Zie &quot;AEM formulieren aanroepen met de Java API&quot; in Programmeren met AEM formulieren voor meer informatie.
