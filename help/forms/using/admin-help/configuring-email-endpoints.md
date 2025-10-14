---
title: E-maileindpunten configureren
description: Leer hoe u e-maileindpunten configureert. Met e-maileindpunten kunt u de service oproepen door een of meer documenten naar een opgegeven e-mailaccount te verzenden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 33583a12-4f20-4146-baa4-c9854e454bbf
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '3808'
ht-degree: 0%

---

# E-maileindpunten configureren {#configuring-email-endpoints}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Met e-maileindpunten kunnen gebruikers de service aanroepen door een of meer documenten (als e-mailbijlagen) naar een opgegeven e-mailaccount te verzenden. Het e-mailpostvak fungeert als verzamelpunt voor de bijlagen. De service bewaakt de Postvak IN en verwerkt de bijlagen. De resultaten van de omzetting worden door:sturen aan de gebruiker die in het eindpunt wordt bepaald.

Voor een e-maileindpunt kunnen geautoriseerde gebruikers een proces aanroepen door bestanden naar de juiste account te e-mailen. De resultaten zullen aan de verzendende gebruiker (door gebrek) of aan de gebruiker worden teruggekeerd die in de eindpuntmontages wordt bepaald.

Alvorens u een e-maileindpunt vormt, creeer een POP3 of IMAP e-mailrekening voor gebruik door het eindpunt. Stel een aparte account in voor elk type conversie. Eén account kan bijvoorbeeld worden geconfigureerd om standaard PDF-documenten te genereren op basis van binnenkomende bestandsbijlagen en een andere account kan worden geconfigureerd om beveiligde PDF-documenten te genereren.

>[!NOTE]
>
>Elk e-mailadres moet aan slechts één e-maileindpunt in kaart brengen. U kunt geen meerdere e-maileindpunten configureren naar één e-mailadres, zelfs niet als de extra e-maileindpunten zijn uitgeschakeld.

Alle e-maileindpunten zijn geconfigureerd met een geoorloofde gebruikersnaam en wachtwoord voor de e-mailpostvak, die vereist zijn wanneer de service wordt aangeroepen. Het e-mailaccount is beveiligd door het systeem van de mailserver waarop het is geconfigureerd.

Als uw gebruikers documenten met West-Europese taalkarakters in dossier en omzettingswegnamen verzenden, moeten zij een e-mailtoepassing gebruiken die de vereiste het coderen types (Latin1 [ ISO-8859-1 ], West-Europese [ Vensters ], of UTF-8) steunt. Voor meer informatie, zie *het Installeren van en het Opstellen van AEM vormen* document voor uw toepassingsserver.

Alvorens u een e-maileindpunt vormt, vorm de E-maildienst. (Zie [&#x200B; de montages van het standaard e-maileindpunt &#x200B;](configuring-email-endpoints.md#configure-default-email-endpoint-settings) vormen.) De de configuratieparameters van de E-mail dienst hebben twee doeleinden:

* Om attributen te vormen die voor alle e-maileindpunten gemeenschappelijk zijn
* Standaardwaarden opgeven voor alle e-maileindpunten

## SSL configureren voor een e-maileindpunt {#configure-ssl-for-an-email-endpoint}

U kunt POP3, IMAP, of SMTP vormen om de Veilige Laag van Contactdozen (SSL) voor een e-maileindpunt te gebruiken.

1. Schakel op de e-mailserver SSL voor POP3, IMAP of SMTP in volgens de documentatie van de fabrikant.
1. Een clientcertificaat exporteren van de e-mailserver.
1. Gebruik het hulpprogramma Keytool om het clientcertificaatbestand te importeren naar het JVM-certificaatarchief (Java Virtual Machine) van de toepassingsserver. De procedure voor deze stap is afhankelijk van de installatiepaden van JVM en client.

   Als u bijvoorbeeld een standaard WebLogic Server-installatie van het Oracle gebruikt met JDK 1.5.0 op Microsoft Windows Server® 2003, typt u de volgende tekst in een opdrachtprompt:

   `keytool -import -file client_certificate -alias myalias -keystore BEA_HOME\jdk150_04\jre\security\cacerts`

1. Voer desgevraagd het wachtwoord in (voor Java is het standaardwachtwoord `changeit` ). U ontvangt een bericht met de mededeling dat het certificaat is geïmporteerd.
1. De beleidsconsole van het gebruik om het e-maileindpunt aan de dienst toe te voegen.
1. Maak het e-maileindpunt in de beheerconsole. Wanneer het vormen van de eindpuntmontages, uitgezochte POP3/IMAP SSL Toegelaten voor inkomende berichten en SMTP SSL Toegelaten voor uitgaande berichten, en verander dienovereenkomstig de haveneigenschappen.

>[!NOTE]
>
>Tip: als u problemen ondervindt bij het gebruik van SSL, gebruikt u een e-mailclient zoals Microsoft Outlook om te controleren of deze via SSL toegang heeft tot de e-mailserver. Als de e-mailclient geen toegang heeft tot de e-mailserver, is de uitgave gerelateerd aan de configuratie van uw certificaat of uw e-mailserver.

## Standaardinstellingen voor het e-maileindpunt configureren {#configure-default-email-endpoint-settings}

U kunt de pagina van het Beheer van de Dienst gebruiken om attributen te vormen die voor alle e-maileindpunten gemeenschappelijk zijn, en standaardwaarden voor alle e-maileindpunten te verstrekken.

Als u wilt dat de formulierwerkstroom binnenkomende e-mailberichten van gebruikers ontvangt en afhandelt, moet u een e-maileindpunt voor de service Volledige taak maken. Dit e-maileindpunt vereist extra montages, zoals die in [&#x200B; worden beschreven leidt tot een E-mail eindpunt voor de Volledige dienst van de Taak &#x200B;](configuring-email-endpoints.md#create-an-email-endpoint-for-the-complete-task-service).

### De standaardwaarden voor e-maileindpunten wijzigen {#change-the-default-values-for-email-endpoints}

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Klik op de pagina Servicebeheer op E-mail: 1.0 (de component-id is com.adobe.idp.dsc.provider.service.email.Email).
1. Voor het lusje van de Configuratie, specificeer de standaard e-maileindpuntmontages en klik dan sparen.

### Standaardinstellingen voor e-maileindpunt {#default-email-endpoint-settings}

**Uitsnede Uitdrukking:** de uitsnijduitdrukking zoals die door kwarts wordt gebruikt om het opiniepeilen van de inputfolder te plannen.

**Interval van de Herhaal:** het aantal tijden de folderopiniepeiling wordt herhaald. Het standaardherhalingsinterval is in seconden als deze waarde niet in de eindpuntconfiguratie wordt gespecificeerd. De standaardwaarde is 10. Deze waarde mag niet kleiner zijn dan 10.

**Aantal van de Herhaling:** het aantal tijden de inputfolder wordt gepolled. De standaardherhalingstelling om te gebruiken als deze waarde niet in de eindpuntconfiguratie wordt gespecificeerd. De waarde -1 geeft aan dat de map voor onbepaalde tijd wordt gescand. De standaardwaarde is -1.

**Vertraging wanneer de baan begint:** De standaardwaarde, in seconden, voor de vertraging alvorens de baan begint om het eindpunt af te tasten. De standaardwaarde is 0.

**Grootte van de Partij:** Het aantal e-mails de ontvangerprocessen per aftasten voor optimale prestaties. De waarde -1 geeft alle e-mails aan. De standaardwaarde is 2.

**Asynchroon:** identificeert het aanroepingstype als asynchroon of synchroon. De voorbijgaande en synchrone processen kunnen slechts synchroon worden aangehaald. De standaardwaarde is asynchroon.

**Patroon van het Domein:** het patroon van de domeinnaam dat wordt gebruikt om inkomende e-mails te filtreren. Als bijvoorbeeld adobe.com wordt gebruikt, wordt alleen e-mail van adobe.com verwerkt; e-mail van andere domeinen wordt genegeerd.

**Patroon van het Dossier:** de inkomende patronen van de dossiergehechtheid die de leverancier goedkeurt. Dit omvat bestanden met specifieke extensies (&ast;.dat, &ast;.xml), specifieke namen (gegevens) en samengestelde expressies in de naam en de extensie (.[ dD ][aA] &quot;haven&quot;). De standaardwaarde is &ast;.&ast;.

**Begeleidende Ontvangers van de Baan:** Één of meerdere e-mailadressen die worden gebruikt om e-mail te verzenden om op succesvolle banen te wijzen. Standaard wordt altijd een bericht met een geslaagde taak verzonden naar de afzender van de oorspronkelijke taak. Er worden maximaal 100 ontvangers ondersteund. Laat dit veld leeg als u deze instelling wilt uitschakelen.

**ontbroken Ontvangers van de Baan:** Één of meerdere e-mailadressen die worden gebruikt om e-mails te verzenden om ontbroken banen te wijzen. Standaard wordt een mislukte taakbericht altijd verzonden naar de afzender die de eerste taak heeft verzonden. Er worden maximaal 100 ontvangers ondersteund. Laat dit veld leeg als u deze instelling wilt uitschakelen.

**Gastheer Inbox:** De naam van de inbox gastheer of IP adres voor de e-mailleverancier om af te tasten.

**Poort Inbox:** Het aantal van de inbox haven voor de e-mailleverancier om af te tasten. Als de waarde 0 is, wordt de standaardIMAP of POP3 haven gebruikt.

**InboxProtocol:** Het e-mailprotocol voor het e-maileindpunt om te gebruiken om inbox af te tasten. De keuzen zijn IMAP of POP3. De postserver van de inbox gastheer moet deze protocollen steunen.

**Inbox Tijd uit:** specificeert de hoeveelheid tijd het eindpunt alvorens zal wachten te annuleren wanneer het proberen om met inbox te verbinden. Als er geen verbinding wordt gemaakt voordat de time-outwaarde is bereikt, wordt het inbox niet gepolled.

**Inbox Gebruiker:** De gebruikersnaam die aan login aan de e-mailrekening wordt vereist. Afhankelijk van de e-mailserver en configuratie is deze naam mogelijk alleen het onderdeel met de gebruikersnaam van de e-mail of is het mogelijk het volledige e-mailadres.

**Wachtwoord Inbox:** het wachtwoord voor de Gebruiker Inbox.

**POP3/IMAP SSL Toegelaten:** wanneer geselecteerd, laat SSL toe.

**SMTP Gastheer:** de gastheernaam van de postserver die de e-mailleverancier gebruikt om resultaten en foutenmeldingen te verzenden. Bijvoorbeeld mail.example.com.

**Haven SMTP:** de haven die wordt gebruikt om met de postserver te verbinden. De standaardwaarde is 25.

**Gebruiker SMTP:** De gebruikersrekening voor de e-mailleverancier aan gebruik wanneer het e-mail voor resultaten en fouten verzendt.

**Wachtwoord SMTP:** het wachtwoord voor de rekening SMTP. Voor sommige mailservers is geen SMTP-wachtwoord vereist.

**verzendt van:** het e-mailadres (bijvoorbeeld, user@company.com) wordt gebruikt om e-mailberichten van resultaten en fouten te verzenden die. Als u geen waarde opgeeft voor Verzenden vanaf, probeert de e-mailserver het e-mailadres te bepalen door de waarde die is opgegeven in de instelling SMTP-gebruiker te combineren met een standaarddomein dat is geconfigureerd op de e-mailserver. Als uw e-mailserver geen standaarddomein heeft en u geen waarde opgeeft voor Verzenden vanaf, kunnen er fouten optreden. Geef een waarde op voor de instelling Verzenden vanaf om ervoor te zorgen dat de e-mailberichten het juiste adres hebben.

**Toegelaten SMTP SSL:** wanneer geselecteerd, laat SSL over SMTP toe.

**omvat het Originele E-maillichaam als Bijlage:** Door gebrek, wanneer u een e-mail naar de Server van Forms verzendt, is de originele tekst van het bericht inbegrepen in het lichaam van het bericht. Als u de tekst in plaats daarvan als bijlage wilt opnemen, selecteert u deze optie.

**gebruik de Originele Onderwerpregel voor resultaate-mails:** door gebrek, gebruikt de server van Forms de waarden die in de het Onderwerp van het E-mail van het Succes en de montages van het Onderwerp van de Fout E-mail als onderwerpregel worden gespecificeerd wanneer het verzenden van resultaate-mailberichten. Selecteer deze optie als u in plaats daarvan dezelfde onderwerpregel wilt gebruiken als de oorspronkelijke e-mail die naar de server is verzonden.

**E-mailonderwerp van het Succes:** Nadat u een e-mail naar een e-maileindpunt verzendt om een proces te beginnen of voort te zetten, ontvangt u een terugkeer e-mailbericht van de Server van AEM Forms. Als uw e-mail succesvol is, ontvangt u een succesbericht. Als uw e-mail mislukt, ontvangt u een foutbericht waarin u opgeeft waarom dit is mislukt. Met deze instelling kunt u de onderwerpregel van e-mailberichten opgeven die voor dit eindpunt worden verzonden.

**E-mail van het Succes Hoofdtekst:** laat u toe om de lichaamstekst van succes te specificeren e-mailberichten die voor dit eindpunt worden verzonden.

**E-mail van het Onderwerp van de Fout Voorvoegsel:** laat u toe om de tekst te specificeren die aan het begin van de onderwerpregel van mislukkings e-mailberichten wordt gebruikt die voor dit eindpunt worden verzonden.

**E-mail van de Fout Onderwerp:** laat u toe om de onderwerpregel van mislukkings e-mailberichten te specificeren die voor dit eindpunt worden verzonden. Deze tekst wordt weergegeven na het voorvoegsel E-mailonderwerp voor fouten.

**E-mailHoofdtekst van de Fout:** laat u toe om de eerste lijn in de lichaamstekst van mislukkings e-mailberichten te specificeren die voor dit eindpunt worden verzonden.

**E-mail Summiere Info:** Elk succes of mislukkingsbericht omvat een sectie die de originele e-mailtekst bevat die u naar de Server van Forms verzond. Deze instelling geeft de tekst aan die boven die sectie wordt weergegeven.

**bevestigt Inbox alvorens dit Eindpunt te creëren/bij te werken:** wanneer deze optie wordt geselecteerd, controleert de Server van Forms of uw montages SMTP/POP3 correct zijn alvorens het eindpunt te creëren. Wanneer u op Toevoegen klikt, wordt een bericht weergegeven waarin wordt aangegeven of de Postvak IN-account geldig is. Als deze optie niet wordt geselecteerd, leidt de Server van AEM Forms tot het eindpunt zonder inbox te bevestigen.

**Vastgestelde Codering van het Karakter:** het coderen formaat voor het e-mailbericht te gebruiken. Het gebrek is UTF-8, die de meeste gebruikers buiten Japan zullen gebruiken. Gebruikers in een Japanse omgeving kunnen kiezen voor ISO2022-JP.

**Ontbroken E-mail Verzonden Omslag:** specificeert een folder waarin om resultaten op te slaan als de SMTP postserver niet operationeel is.

## Instellingen voor e-maileindpunt {#email-endpoint-settings}

Gebruik de volgende montages om een e-maileindpunt te vormen.

**Naam:** Een verplicht plaatsen die het eindpunt identificeert. Neem geen &lt;-teken op, omdat de naam die in Workspace wordt weergegeven hierdoor wordt afgekapt. Als u een URL als naam van het eindpunt ingaat, zorg ervoor dat het met de syntaxisregels in overeenstemming is die in RFC1738 worden gespecificeerd.

**Beschrijving:** een beschrijving van het eindpunt. Neem geen &lt;-teken op omdat de beschrijving die in Workspace wordt weergegeven daardoor wordt afgekapt.

**Uitsnijduitdrukking:** ga een uitsnijduitdrukking in als e-mail door een uitsnijduitdrukking te gebruiken moet worden gepland.

**Aantal van de Herhaling:** Aantal tijden het e-maileindpunt scant de omslag of de folder. De waarde -1 geeft aan dat een scanbewerking voor onbepaalde tijd wordt uitgevoerd. De standaardwaarde is -1.

**Interval van de Herhaal:** het aftastentarief dat de ontvanger voor het controleren van inkomende post gebruikt.

**Vertraging wanneer het baanbegin:** de tijd te wachten om na het plannerbegin af te tasten.

**Grootte van de Partij:** Het aantal e-mails de ontvangerprocessen per aftasten voor optimale prestaties. De waarde -1 geeft alle e-mails aan. De standaardwaarde is 2.

**Naam van de Gebruiker:** Een verplicht plaatsen, dat de gebruikersnaam is die wanneer het aanhalen van een doeldienst van e-mail wordt gebruikt. De standaardwaarde is SuperAdmin.

**Naam van het Domein:** A mandatory het plaatsen, dat het domein van de gebruiker is. De standaardwaarde is DefaultDom.

**Patroon van het Domein:** specificeert de domeinpatronen van inkomende e-mail die de leverancier goedkeurt. Als bijvoorbeeld adobe.com wordt gebruikt, wordt alleen e-mail van adobe.com verwerkt; e-mail van andere domeinen wordt genegeerd.

**Patroon van het Dossier:** specificeert de inkomende patronen van de dossiergehechtheid die de leverancier goedkeurt. Dit omvat bestanden met specifieke extensies (&ast;.dat, &ast;.xml), specifieke namen (gegevens) of samengestelde expressies in de naam en extensie (&ast;..[ dD ][aA] &quot;haven&quot;).

**Begeleidende Ontvangers van de Baan:** Een e-mailadres waarnaar de berichten worden verzonden om op succesvolle banen te wijzen. Standaard wordt altijd een bericht met een geslaagde taak naar de afzender verzonden. Als u de afzender typt, worden de e-mailresultaten verzonden naar de afzender. Er worden maximaal 100 ontvangers ondersteund. Geef extra ontvangers op met e-mailadressen, gescheiden door komma&#39;s (,).

Laat de instelling leeg als u deze instelling wilt uitschakelen. In sommige gevallen wilt u een proces activeren en geen e-mailmelding van het resultaat.

**ontbroken Ontvangers van de Baan:** Een e-mailadres waarnaar de berichten worden verzonden om ontbroken banen te wijzen. Standaard wordt altijd een mislukte taakbericht naar de afzender verzonden. Als u de afzender typt, worden de e-mailresultaten verzonden naar de afzender. Er worden maximaal 100 ontvangers ondersteund. Geef extra ontvangers op met e-mailadressen, gescheiden door komma&#39;s (,).

Laat de instelling leeg als u deze instelling wilt uitschakelen. In sommige gevallen wilt u een proces activeren en geen e-mailmelding van het resultaat.

**Gastheer Inbox:** De naam van de inbox gastheer of IP adres voor de e-mailleverancier om af te tasten.

**Haven Inbox:** de haven die de e-mailserver gebruikt. De standaardwaarde voor POP3 is 110 en de standaardwaarde voor IMAP is 143. Als SSL wordt toegelaten, is de standaardwaarde voor POP3 995 en de standaardwaarde voor IMAP is 993.

**InboxProtocol:** Het e-mailprotocol voor het e-maileindpunt om te gebruiken om inbox af te tasten. De waarden zijn IMAP of POP3. De postserver van de inbox gastheer moet deze protocollen steunen.

**Uitgaande Tijd Inbox:** de onderbreking, in seconden, voor de e-mailleverancier om op inbox reacties te wachten.

**Inbox Gebruiker:** De gebruikersnaam die aan login aan de e-mailrekening wordt vereist. Afhankelijk van de e-mailserver en configuratie kan deze waarde alleen het onderdeel met de gebruikersnaam van de e-mail zijn of het volledige e-mailadres.

**Wachtwoord Inbox:** het wachtwoord voor de inbox gebruiker.

**POP3/IMAP SSL Toegelaten:** selecteer dit het plaatsen om de e-mailleverancier te dwingen om SSL te gebruiken om inbox af te tasten. Controleer of uw mailserver SSL ondersteunt.

**SMTP Gastheer:** de gastheernaam van de postserver de e-mailleverancier gebruikt om resultaten en foutenmeldingen te verzenden.

**Haven SMTP:** de standaardwaarde voor de haven SMTP is 25.

**Gebruiker SMTP:** De gebruikersrekening voor de e-mailleverancier aan gebruik wanneer het e-mailberichten van resultaten en fouten verzendt.

**Wachtwoord SMTP:** het wachtwoord voor de rekening SMTP. Voor sommige mailservers is geen SMTP-wachtwoord vereist.

**verzendt van:** het e-mailadres (bijvoorbeeld, user@company.com) wordt gebruikt om e-mailberichten van resultaten en fouten te verzenden die. Als u geen waarde opgeeft voor Verzenden vanaf, probeert de e-mailserver het e-mailadres te bepalen door de waarde die is opgegeven in de instelling SMTP-gebruiker te combineren met een standaarddomein dat is geconfigureerd op de e-mailserver. Als uw e-mailserver geen standaarddomein heeft en u geen waarde opgeeft voor Verzenden vanaf, kunnen er fouten optreden. Geef een waarde op voor de instelling Verzenden vanaf om ervoor te zorgen dat de e-mailberichten het juiste adres hebben.

**Toegelaten SMTP SSL:** selecteer dit het plaatsen om de e-mailleverancier te dwingen SSL te gebruiken om inbox af te tasten. Controleer of uw mailserver SSL ondersteunt.

**Ontbroken E-mail Verzonden Omslag:** specificeert een folder waarin om resultaten op te slaan als de SMTP postserver niet operationeel is.

**asynchroon:** Wanneer reeks aan synchroon, worden alle inputdocumenten verwerkt en één enkele reactie is teruggekeerd. Wanneer ingesteld op asynchroon, wordt een reactie verzonden voor elk document dat wordt verwerkt.

Bijvoorbeeld, wordt een e-maileindpunt gecreeerd voor de dienst die één enkel document van Word neemt en dat document als dossier van PDF terugkeert. Een e-mail kan naar inbox van het eindpunt worden verzonden die de veelvoudige (3) documenten van Word bevat. Wanneer alle drie documenten worden verwerkt, als het eindpunt synchroon wordt gevormd, wordt één enkele reactie-e-mail verzonden met alle drie documenten in bijlage. Als het eindpunt asynchroon is, wordt een antwoord-e-mail verzonden nadat elk document van Word in PDF wordt omgezet. Het resultaat is drie e-mails, elk met één PDF bijlage.

De standaardwaarde is asynchroon.

**omvat het originele e-maillichaam als gehechtheid:** Door gebrek, wanneer u een e-mail naar de Server van Forms verzendt, is de originele tekst van het bericht inbegrepen in het lichaam van het bericht. Als u de tekst in plaats daarvan als bijlage wilt opnemen, selecteert u deze optie.

**gebruik de originele onderwerpregel voor resultaate-mail:** Door gebrek, gebruikt de server van Forms de waarden die in de Erfgang e-mail worden gespecificeerd Onderwerp en de montages van het Onderwerp van het E-mail van de Fout als onderwerpregel wanneer het verzenden van resultaate-mailberichten. Selecteer deze optie als u in plaats daarvan dezelfde onderwerpregel wilt gebruiken als de oorspronkelijke e-mail die naar de server is verzonden.

**E-mailonderwerp van het Succes:** Nadat u een e-mail naar een e-maileindpunt verzendt om een proces te beginnen of voort te zetten, ontvangt u een terugkeer e-mailbericht van de Server van AEM Forms. Als uw e-mail succesvol is, ontvangt u een succesbericht. Als uw e-mail mislukt, ontvangt u een foutbericht waarin u opgeeft waarom dit is mislukt. Met deze instelling kunt u de onderwerpregel van e-mailberichten opgeven die voor dit eindpunt worden verzonden.

**E-mail van het Succes Hoofdtekst:** laat u toe om de lichaamstekst van succes te specificeren e-mailberichten die voor dit eindpunt worden verzonden.

**E-mail van het Onderwerp van de Fout Voorvoegsel:** laat u toe om de tekst te specificeren die aan het begin van de onderwerpregel van mislukkings e-mailberichten wordt gebruikt die voor dit eindpunt worden verzonden.

**E-mail van de Fout Onderwerp:** laat u toe om de onderwerpregel van mislukkings e-mailberichten te specificeren die voor dit eindpunt worden verzonden. Deze tekst wordt weergegeven na het voorvoegsel E-mailonderwerp voor fouten.

**E-mailHoofdtekst van de Fout:** laat u toe om de eerste lijn in de lichaamstekst van mislukkings e-mailberichten te specificeren die voor dit eindpunt worden verzonden.

**E-mail Summiere Info:** Elk succes of mislukkingsbericht omvat een sectie die de originele e-mailtekst bevat die u naar de Server van Forms verzond. Deze instelling geeft de tekst aan die boven die sectie wordt weergegeven.

**bevestigt Inbox alvorens dit eindpunt te creëren/bij te werken:** wanneer deze optie wordt geselecteerd, controleert de Server van Forms of uw montages SMTP/POP3 correct zijn alvorens het eindpunt te creëren. Wanneer u op Toevoegen klikt, wordt een bericht weergegeven waarin wordt aangegeven of de Postvak IN-account geldig is. Als deze optie niet wordt geselecteerd, leidt de Server van AEM Forms tot het eindpunt zonder inbox te bevestigen.

**Naam van de Verrichting:** Dit het plaatsen is verplicht. Een lijst van verrichtingen die aan het e-maileindpunt kunnen worden toegewezen. De bewerking die u hier selecteert, bepaalt welke velden worden weergegeven in de secties Toewijzingen invoerparameter en Toewijzingen uitvoerparameter.

**Toewijzingen van de Parameter van de Input:** Gebruikt om de input te vormen die wordt vereist om de dienst en de verrichting te verwerken. De twee typen invoer zijn letterlijk en variabel:

**Letterlijk:** e-mail gebruikt de waarde die op het gebied is ingegaan aangezien het wordt getoond.

**Variabele:** u kunt een koord van het e-mailonderwerp, het lichaam, de kopbal, of het e-mailadres van de afzender in kaart brengen. Gebruik hiervoor een van de volgende trefwoorden: %SUBJECT%, %BODY%, %HEADER% of %SENDER%. Als u bijvoorbeeld %SUBJECT% gebruikt, wordt de inhoud van het e-mailonderwerp gebruikt als invoerparameter. Als u bijlagen wilt ophalen, voert u een bestandspatroon in dat het e-maileindpunt kan gebruiken om de bijgevoegde documenten te selecteren. Als u bijvoorbeeld &ast;.pdf opgeeft, worden alle bijgevoegde documenten met de bestandsnaamextensie .pdf geselecteerd. &amp;amp invoeren;ast; selecteert bijgevoegd document. Als u example.pdf invoert, worden alle gekoppelde documenten met de naam example.pdf geselecteerd.

**Toewijzingen van de Parameter van de Output:** Gebruikt om de output van de dienst en de verrichting te vormen. De volgende tekens in de toewijzingswaarden van de uitvoerparameter worden uitgebreid in de bestandsnaam van de bijlage:

**%F** Vertegenwoordigt de bestandsnaam van het bronbestand (zonder een extensie).

**%E** Vertegenwoordigt de uitbreiding van het bronbestand.

Elke keer dat de backslash (\) voorkomt, wordt vervangen door %%.

***nota &#x200B;**: Als het bericht van het de dienstverzoek veelvoudige dossiergehechtheid omvat, kunt u niet de %F en %E parameters voor het bezit van de Toewijzingen van de Parameter van de Output van het eindpunt gebruiken. Als de servicereactie meerdere bestandsbijlagen retourneert, kunt u niet dezelfde bestandsnaam voor meerdere bijlagen opgeven. Als u deze aanbevelingen niet volgt, leidt de aangehaalde dienst tot de namen voor de teruggekeerde dossiers, en de namen zijn niet voorspelbaar.*

De volgende waarden zijn beschikbaar:

**Enig Voorwerp:** de e-mailleverancier heeft niet de bronomslagbestemming; de resultaten zijn teruggekeerd als gehechtheid. Het patroon is Result/%F.ps en retourneert Result%%sourcefilename.ps als de bestandsbijlage.

**Lijst:** het patroon is Result/%F/ en keert Result%%sourcefilename%%file1 als filename gehechtheid terug.

**Kaart:** het patroon is Result/%F/ en de bronbestemming is Result%%sourcefilename%%file1 en Result%%sourcefilename%%file2. Als de kaart meer dan één voorwerp bevat en het patroon Result/%F.ps is, zijn de gehechtheid van het reactiedossier Result%%sourcefilename1.ps (output 1) en Result%%sourcefilename2.ps (output 2).

## Creeer een E-maileindpunt voor de Volledige dienst van de Taak {#create-an-email-endpoint-for-the-complete-task-service}

Als u wilt dat de formulierwerkstroom binnenkomende e-mailberichten van gebruikers ontvangt en afhandelt, moet u een e-maileindpunt voor de service Volledige taak maken.

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Voor de pagina van het Beheer van de Dienst, klik de Volledige dienst van de Taak.
1. Selecteer op het tabblad Eindpunten de optie E-mail in de vervolgkeuzelijst en klik op Toevoegen.
1. Typ de hostnaam of het IP-adres van de mailserver in het vak Inbox-host.
1. Typ in het vak Inbox-gebruiker de gebruikersnaam die is vereist voor aanmelding bij de e-mailaccount die u hebt gemaakt voor de verwerking van formulierverzendingen. Afhankelijk van de e-mailserver en configuratie kan deze naam alleen het onderdeel met de gebruikersnaam van de e-mail zijn of het volledige e-mailadres.
1. Typ in het vak Wachtwoord Postvak IN het wachtwoord voor de Postvak In-gebruiker.
1. Typ in het vak SMTP-host de hostnaam of het IP-adres van de mailserver waarvan de e-mailprovider de resultaten en foutberichten verzendt.
1. Typ in het vak SMTP-gebruiker de gebruikersaccount voor de e-mailprovider die moet worden gebruikt wanneer deze e-mail verzendt voor resultaten en fouten. Dit gebruikersaccount kan dezelfde waarde zijn als voor Inbox-gebruiker.
1. Typ in het vak SMTP-wachtwoord het wachtwoord voor de SMTP-account.
1. Selecteer Inhalen in de lijst Operation Name.
1. Selecteer in de lijst BijlageMap de optie Variabele en typ `*.*` in het aangrenzende vak. Dit verzendt alle gehechtheid van de binnenkomende postberichten naar een kaartvariabele voor het Volledige proces van de Taak.
1. Selecteer in de lijst mailBody een variabele en typ `%BODY%` in het aangrenzende vak.
1. Selecteer in de lijst MailFrom de optie Variabele en typ `%SENDER%` in het naastgelegen vak. Dit brengt het afzenderadres aan de Volledige het procesgegevens van de Taak in kaart.
1. Typ `results` in het vak Resultaten. Dit veroorzaakt de Volledige Taak of het Proces van het Begin om een resultaatkoord terug te keren.
1. Klik toevoegen.
