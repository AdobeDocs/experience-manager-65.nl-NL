---
title: E-maileindpunten configureren
description: Leer hoe u e-maileindpunten configureert. Met e-maileindpunten kunt u de service oproepen door een of meer documenten naar een opgegeven e-mailaccount te verzenden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 33583a12-4f20-4146-baa4-c9854e454bbf
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '3796'
ht-degree: 0%

---

# E-maileindpunten configureren {#configuring-email-endpoints}

Met e-maileindpunten kunnen gebruikers de service aanroepen door een of meer documenten (als e-mailbijlagen) naar een opgegeven e-mailaccount te verzenden. Het e-mailpostvak fungeert als verzamelpunt voor de bijlagen. De service bewaakt de Postvak IN en verwerkt de bijlagen. De resultaten van de omzetting worden door:sturen aan de gebruiker die in het eindpunt wordt bepaald.

Voor een e-maileindpunt kunnen geautoriseerde gebruikers een proces aanroepen door bestanden naar de juiste account te e-mailen. De resultaten zullen aan de verzendende gebruiker (door gebrek) of aan de gebruiker worden teruggekeerd die in de eindpuntmontages wordt bepaald.

Alvorens u een e-maileindpunt vormt, creeer een POP3 of IMAP e-mailrekening voor gebruik door het eindpunt. Stel een aparte account in voor elk type conversie. Eén account kan bijvoorbeeld worden geconfigureerd om standaard PDF-documenten te genereren op basis van binnenkomende bestandsbijlagen en een andere account kan worden geconfigureerd om beveiligde PDF-documenten te genereren.

>[!NOTE]
>
>Elk e-mailadres moet aan slechts één e-maileindpunt in kaart brengen. U kunt geen meerdere e-maileindpunten configureren naar één e-mailadres, zelfs niet als de extra e-maileindpunten zijn uitgeschakeld.

Alle e-maileindpunten zijn geconfigureerd met een geoorloofde gebruikersnaam en wachtwoord voor de e-mailpostvak, die vereist zijn wanneer de service wordt aangeroepen. Het e-mailaccount is beveiligd door het systeem van de mailserver waarop het is geconfigureerd.

Als uw gebruikers documenten met West-Europese taalkarakters in dossier en omzettingswegnamen verzenden, moeten zij een e-mailtoepassing gebruiken die de vereiste coderingstypes (Latin1 steunt [ISO-8859-1], West-Europees [Windows], of UTF-8). Zie de klasse *AEM installeren en implementeren* document voor uw toepassingsserver.

Alvorens u een e-maileindpunt vormt, vorm de E-maildienst. (Zie [Standaardinstellingen voor het e-maileindpunt configureren](configuring-email-endpoints.md#configure-default-email-endpoint-settings).) De configuratieparameters van de e-mailservice hebben twee doelen:

* Om attributen te vormen die voor alle e-maileindpunten gemeenschappelijk zijn
* Standaardwaarden opgeven voor alle e-maileindpunten

## SSL configureren voor een e-maileindpunt {#configure-ssl-for-an-email-endpoint}

U kunt POP3, IMAP, of SMTP vormen om de Veilige Laag van Contactdozen (SSL) voor een e-maileindpunt te gebruiken.

1. Schakel op de e-mailserver SSL voor POP3, IMAP of SMTP in volgens de documentatie van de fabrikant.
1. Een clientcertificaat exporteren van de e-mailserver.
1. Gebruik het hulpprogramma Keytool om het clientcertificaatbestand te importeren naar het JVM-certificaatarchief (Java Virtual Machine) van de toepassingsserver. De procedure voor deze stap is afhankelijk van de installatiepaden van JVM en client.

   Als u bijvoorbeeld een standaard WebLogic Server-installatie van het Oracle gebruikt met JDK 1.5.0 op Microsoft Windows Server® 2003, typt u de volgende tekst in een opdrachtprompt:

   `keytool -import -file client_certificate -alias myalias -keystore BEA_HOME\jdk150_04\jre\security\cacerts`

1. Voer desgevraagd het wachtwoord in (voor Java is het standaardwachtwoord `changeit`). U ontvangt een bericht met de mededeling dat het certificaat is geïmporteerd.
1. De beleidsconsole van het gebruik om het e-maileindpunt aan de dienst toe te voegen.
1. Maak het e-maileindpunt in de beheerconsole. Wanneer het vormen van de eindpuntmontages, uitgezochte POP3/IMAP SSL Toegelaten voor inkomende berichten en SMTP SSL Toegelaten voor uitgaande berichten, en verander dienovereenkomstig de haveneigenschappen.

>[!NOTE]
>
>Tip: als u problemen ondervindt bij het gebruik van SSL, gebruikt u een e-mailclient zoals Microsoft Outlook om te controleren of deze via SSL toegang heeft tot de e-mailserver. Als de e-mailclient geen toegang heeft tot de e-mailserver, is de uitgave gerelateerd aan de configuratie van uw certificaat of uw e-mailserver.

## Standaardinstellingen voor het e-maileindpunt configureren {#configure-default-email-endpoint-settings}

U kunt de pagina van het Beheer van de Dienst gebruiken om attributen te vormen die voor alle e-maileindpunten gemeenschappelijk zijn, en standaardwaarden voor alle e-maileindpunten te verstrekken.

Als u wilt dat de formulierwerkstroom binnenkomende e-mailberichten van gebruikers ontvangt en afhandelt, moet u een e-maileindpunt voor de service Volledige taak maken. Dit e-maileindpunt vereist extra montages, zoals die in worden beschreven [Creeer een E-maileindpunt voor de Volledige dienst van de Taak](configuring-email-endpoints.md#create-an-email-endpoint-for-the-complete-task-service).

### De standaardwaarden voor e-maileindpunten wijzigen {#change-the-default-values-for-email-endpoints}

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Klik op de pagina Servicebeheer op E-mail: 1.0 (de component-id is com.adobe.idp.dsc.provider.service.email.Email).
1. Voor het lusje van de Configuratie, specificeer de standaard e-maileindpuntmontages en klik dan sparen.

### Standaardinstellingen voor e-maileindpunt {#default-email-endpoint-settings}

**Uitsnijduitdrukking:** De expressie voor uitsnijden, zoals gebruikt door kwarts om de opiniepeiling van de invoermap te plannen.

**Interval herhalen:** Het aantal keren dat de mapopiniepeiling wordt herhaald. Het standaardherhalingsinterval is in seconden als deze waarde niet in de eindpuntconfiguratie wordt gespecificeerd. De standaardwaarde is 10. Deze waarde mag niet kleiner zijn dan 10.

**Aantal herhalingen:** Het aantal keren dat de invoermap wordt gepolled. De standaardherhalingstelling om te gebruiken als deze waarde niet in de eindpuntconfiguratie wordt gespecificeerd. De waarde -1 geeft aan dat de map voor onbepaalde tijd wordt gescand. De standaardwaarde is -1.

**Vertraging bij het starten van de taak:** De standaardwaarde, in seconden, voor de vertraging alvorens de baan begint om het eindpunt af te tasten. De standaardwaarde is 0.

**Batchgrootte:** Het aantal e-mailberichten dat de ontvangerprocessen per scan uitvoeren voor optimale prestaties. De waarde -1 geeft alle e-mails aan. De standaardwaarde is 2.

**Asynchroon:** Identificeert het aanroepingstype als asynchroon of synchroon. De voorbijgaande en synchrone processen kunnen slechts synchroon worden aangehaald. De standaardwaarde is asynchroon.

**Domeinpatroon:** Het domeinnaampatroon waarmee inkomende e-mailberichten worden gefilterd. Als bijvoorbeeld adobe.com wordt gebruikt, wordt alleen e-mail van adobe.com verwerkt; e-mail van andere domeinen wordt genegeerd.

**Bestandspatroon** De inkomende patronen van de dossiergehechtheid die de leverancier goedkeurt. Dit omvat bestanden met specifieke extensies (&amp;ast;.dat, &amp;ast;.xml), specifieke namen (gegevens) en samengestelde expressies in de naam en de extensie (.[dD][aA]&#39;port&#39;). De standaardwaarde is &amp;last;.&amp;ast;..

**Ontvangers van geslaagde taak:** Een of meer e-mailadressen die worden gebruikt om e-mailberichten te verzenden om aan te geven dat taken zijn geslaagd. Standaard wordt altijd een bericht met een geslaagde taak verzonden naar de afzender van de oorspronkelijke taak. Er worden maximaal 100 ontvangers ondersteund. Laat dit veld leeg als u deze instelling wilt uitschakelen.

**Ontvangers van mislukte taak:** Een of meer e-mailadressen die worden gebruikt om e-mailberichten te verzenden om aan te geven dat taken zijn mislukt. Standaard wordt een mislukte taakbericht altijd verzonden naar de afzender die de eerste taak heeft verzonden. Er worden maximaal 100 ontvangers ondersteund. Laat dit veld leeg als u deze instelling wilt uitschakelen.

**Host Postvak IN:** De hostnaam of het IP-adres in het Postvak IN van de e-mailprovider die moet worden gescand.

**Poort Postvak IN:** Het inbox-poortnummer dat de e-mailprovider moet scannen. Als de waarde 0 is, wordt de standaardIMAP of POP3 haven gebruikt.

**Inbox-protocol:** Het e-mailprotocol voor het e-maileindpunt dat moet worden gebruikt om inbox te scannen. De keuzen zijn IMAP of POP3. De postserver van de inbox gastheer moet deze protocollen steunen.

**Uittijd Postvak IN:** Specificeert de hoeveelheid tijd het eindpunt zal wachten alvorens te annuleren wanneer het proberen om met inbox te verbinden. Als er geen verbinding wordt gemaakt voordat de time-outwaarde is bereikt, wordt het inbox niet gepolled.

**Gebruiker Postvak IN:** De gebruikersnaam die is vereist om u aan te melden bij de e-mailaccount. Afhankelijk van de e-mailserver en configuratie is deze naam mogelijk alleen het onderdeel met de gebruikersnaam van de e-mail of is het mogelijk het volledige e-mailadres.

**Wachtwoord Postvak IN:** Het wachtwoord voor de Inbox-gebruiker.

**POP3/IMAP SSL ingeschakeld:** Als deze optie is geselecteerd, wordt SSL ingeschakeld.

**SMTP-host:** De hostnaam van de mailserver die de e-mailprovider gebruikt om resultaten en foutberichten te verzenden. Bijvoorbeeld mail.example.com.

**SMTP-poort:** De poort die wordt gebruikt om verbinding te maken met de mailserver. De standaardwaarde is 25.

**SMTP-gebruiker:** De gebruikersaccount voor de e-mailprovider die moet worden gebruikt wanneer deze e-mail verzendt voor resultaten en fouten.

**SMTP-wachtwoord:** Het wachtwoord voor de SMTP-account. Voor sommige mailservers is geen SMTP-wachtwoord vereist.

**Verzenden vanaf:** Het e-mailadres (bijvoorbeeld user@company.com) dat wordt gebruikt voor het verzenden van e-mailmeldingen over resultaten en fouten. Als u geen waarde opgeeft voor Verzenden vanaf, probeert de e-mailserver het e-mailadres te bepalen door de waarde die is opgegeven in de instelling SMTP-gebruiker te combineren met een standaarddomein dat is geconfigureerd op de e-mailserver. Als uw e-mailserver geen standaarddomein heeft en u geen waarde opgeeft voor Verzenden vanaf, kunnen er fouten optreden. Geef een waarde op voor de instelling Verzenden vanaf om ervoor te zorgen dat de e-mailberichten het juiste adres hebben.

**SMTP SSL ingeschakeld:** Als deze optie is geselecteerd, wordt SSL ingeschakeld via SMTP.

**De originele e-mailtekst opnemen als bijlage:** Wanneer u een e-mail naar de Forms Server verzendt, wordt standaard de oorspronkelijke tekst van het bericht opgenomen in de hoofdtekst van het bericht. Als u de tekst in plaats daarvan als bijlage wilt opnemen, selecteert u deze optie.

**Gebruik de originele onderwerpregel voor resultaate-mails:** Standaard gebruikt de Forms-server de waarden die zijn opgegeven in de instellingen voor E-mailonderwerp met succes en E-mailonderwerp met fouten als onderwerpregel bij het verzenden van e-mailberichten met resultaatmeldingen. Selecteer deze optie als u in plaats daarvan dezelfde onderwerpregel wilt gebruiken als de oorspronkelijke e-mail die naar de server is verzonden.

**E-mailonderwerp geslaagd:** Nadat u een e-mail naar een e-maileindpunt verzendt om een proces te beginnen of voort te zetten, ontvangt u een terugkeer e-mailbericht van de Server van AEM Forms. Als uw e-mail succesvol is, ontvangt u een succesbericht. Als uw e-mail mislukt, ontvangt u een foutbericht waarin u opgeeft waarom dit is mislukt. Met deze instelling kunt u de onderwerpregel van e-mailberichten opgeven die voor dit eindpunt worden verzonden.

**Tekst voor e-mail met succes:** Laat u toe om de lichaamstekst van succes te specificeren e-mailberichten die voor dit eindpunt worden verzonden.

**Fout bij voorvoegsel e-mailonderwerp:** Laat u toe om de tekst te specificeren die aan het begin van de onderwerpregel van mislukkings e-mailberichten wordt gebruikt die voor dit eindpunt worden verzonden.

**Fout in e-mailonderwerp:** Laat u toe om de onderwerpregel van mislukkings e-mailberichten te specificeren die voor dit eindpunt worden verzonden. Deze tekst wordt weergegeven na het voorvoegsel E-mailonderwerp voor fouten.

**Fout in e-mailhoofdtekst:** Laat u toe om de eerste lijn in de lichaamstekst van mislukkings e-mailberichten te specificeren die voor dit eindpunt worden verzonden.

**E-mailoverzichtsgegevens:** Elk succes- of foutbericht bevat een sectie met de originele e-mailtekst die u naar de Forms Server hebt verzonden. Deze instelling geeft de tekst aan die boven die sectie wordt weergegeven.

**Valideer Inbox alvorens dit eindpunt tot stand te brengen/bij te werken:** Wanneer deze optie wordt geselecteerd, controleert de Server van Forms of uw montages SMTP/POP3 correct zijn alvorens het eindpunt te creëren. Wanneer u op Toevoegen klikt, wordt een bericht weergegeven waarin wordt aangegeven of de Postvak IN-account geldig is. Als deze optie niet wordt geselecteerd, leidt de Server van AEM Forms tot het eindpunt zonder inbox te bevestigen.

**Codering tekenset:** De coderingsindeling die voor het e-mailbericht moet worden gebruikt. Het gebrek is UTF-8, die de meeste gebruikers buiten Japan zullen gebruiken. Gebruikers in een Japanse omgeving kunnen kiezen voor ISO2022-JP.

**Verzonden map via e-mail is mislukt:** Specificeert een folder waarin om resultaten op te slaan als de SMTP postserver niet operationeel is.

## Instellingen voor e-maileindpunt {#email-endpoint-settings}

Gebruik de volgende montages om een e-maileindpunt te vormen.

**Naam:** Een verplichte instelling die het eindpunt identificeert. Neem geen &lt;-teken op omdat de naam die in Workspace wordt weergegeven hierdoor wordt afgekapt. Als u een URL als naam van het eindpunt ingaat, zorg ervoor dat het met de syntaxisregels in overeenstemming is die in RFC1738 worden gespecificeerd.

**Omschrijving:** Een beschrijving van het eindpunt. Neem geen &lt;-teken op omdat dit de beschrijving in Workspace afkapt.

**Uitsnijduitdrukking:** Voer een expressie voor uitsnijden in als de e-mail moet worden gepland met een expressie voor uitsnijden.

**Aantal herhalingen:** Aantal tijden het e-maileindpunt scant de omslag of de folder. De waarde -1 geeft aan dat een scanbewerking voor onbepaalde tijd wordt uitgevoerd. De standaardwaarde is -1.

**Interval herhalen:** De scansnelheid die de ontvanger gebruikt om inkomende e-mail te controleren.

**Vertraging bij het starten van de taak:** De tijd om te wachten om na de planner begint te aftasten.

**Batchgrootte:** Het aantal e-mailberichten dat de ontvangerprocessen per scan uitvoeren voor optimale prestaties. De waarde -1 geeft alle e-mails aan. De standaardwaarde is 2.

**Gebruikersnaam:** A mandatory setting, which is the user name that is used when invoking a target service from email. De standaardwaarde is SuperAdmin.

**Domeinnaam:** Een verplichte instelling; dit is het domein van de gebruiker. De standaardwaarde is DefaultDom.

**Domeinpatroon:** Geeft de domeinpatronen aan van binnenkomende e-mailberichten die de provider accepteert. Als bijvoorbeeld adobe.com wordt gebruikt, wordt alleen e-mail van adobe.com verwerkt; e-mail van andere domeinen wordt genegeerd.

**Bestandspatroon** Hiermee worden de inkomende patronen voor bestandsbijlagen opgegeven die de provider accepteert. Dit omvat bestanden met specifieke extensies (&amp;ast;.dat, &amp;ast;.xml), specifieke namen (gegevens) of samengestelde expressies in de naam en extensie (&amp;ast;..[dD][aA]&#39;port&#39;).

**Ontvangers van geslaagde taak:** Een e-mailadres waarnaar berichten worden verzonden om aan te geven dat taken zijn gelukt. Standaard wordt altijd een bericht met een geslaagde taak naar de afzender verzonden. Als u de afzender typt, worden de e-mailresultaten verzonden naar de afzender. Er worden maximaal 100 ontvangers ondersteund. Geef extra ontvangers op met e-mailadressen, gescheiden door komma&#39;s (,).

Laat de instelling leeg als u deze instelling wilt uitschakelen. In sommige gevallen wilt u een proces activeren en geen e-mailmelding van het resultaat.

**Ontvangers van mislukte taak:** Een e-mailadres waarnaar berichten worden verzonden om mislukte taken aan te geven. Standaard wordt altijd een mislukte taakbericht naar de afzender verzonden. Als u de afzender typt, worden de e-mailresultaten verzonden naar de afzender. Er worden maximaal 100 ontvangers ondersteund. Geef extra ontvangers op met e-mailadressen, gescheiden door komma&#39;s (,).

Laat de instelling leeg als u deze instelling wilt uitschakelen. In sommige gevallen wilt u een proces activeren en geen e-mailmelding van het resultaat.

**Host Postvak IN:** De hostnaam of het IP-adres in het Postvak IN van de e-mailprovider die moet worden gescand.

**Poort Postvak IN:** De poort die de e-mailserver gebruikt. De standaardwaarde voor POP3 is 110 en de standaardwaarde voor IMAP is 143. Als SSL wordt toegelaten, is de standaardwaarde voor POP3 995 en de standaardwaarde voor IMAP is 993.

**Inbox-protocol:** Het e-mailprotocol voor het e-maileindpunt dat moet worden gebruikt om inbox te scannen. De waarden zijn IMAP of POP3. De postserver van de inbox gastheer moet deze protocollen steunen.

**Uittijd Postvak IN:** De time-out, in seconden, waarmee de e-mailprovider wacht op inbox-reacties.

**Gebruiker Postvak IN:** De gebruikersnaam die is vereist om u aan te melden bij het e-mailaccount. Afhankelijk van de e-mailserver en configuratie kan deze waarde alleen het onderdeel met de gebruikersnaam van de e-mail zijn of het volledige e-mailadres.

**Wachtwoord Postvak IN:** Het wachtwoord voor de inbox-gebruiker.

**POP3/IMAP SSL ingeschakeld:** Selecteer deze instelling om de e-mailprovider te dwingen SSL te gebruiken om de inbox te scannen. Controleer of uw mailserver SSL ondersteunt.

**SMTP-host:** De hostnaam van de mailserver die de e-mailprovider gebruikt om resultaten en foutberichten te verzenden.

**SMTP-poort:** De standaardwaarde voor de haven SMTP is 25.

**SMTP-gebruiker:** De gebruikersaccount voor de e-mailprovider die moet worden gebruikt wanneer deze e-mailmeldingen over resultaten en fouten verzendt.

**SMTP-wachtwoord:** Het wachtwoord voor de SMTP-account. Voor sommige mailservers is geen SMTP-wachtwoord vereist.

**Verzenden vanaf:** Het e-mailadres (bijvoorbeeld user@company.com) dat wordt gebruikt voor het verzenden van e-mailmeldingen over resultaten en fouten. Als u geen waarde opgeeft voor Verzenden vanaf, probeert de e-mailserver het e-mailadres te bepalen door de waarde die is opgegeven in de instelling SMTP-gebruiker te combineren met een standaarddomein dat is geconfigureerd op de e-mailserver. Als uw e-mailserver geen standaarddomein heeft en u geen waarde opgeeft voor Verzenden vanaf, kunnen er fouten optreden. Geef een waarde op voor de instelling Verzenden vanaf om ervoor te zorgen dat de e-mailberichten het juiste adres hebben.

**SMTP SSL ingeschakeld:** Selecteer deze instelling om de e-mailprovider te dwingen SSL te gebruiken om de inbox te scannen. Controleer of uw mailserver SSL ondersteunt.

**Verzonden map via e-mail is mislukt:** Specificeert een folder waarin om resultaten op te slaan als de SMTP postserver niet operationeel is.

**asynchroon:** Wanneer deze optie is ingesteld op synchroon, worden alle invoerdocumenten verwerkt en wordt één reactie geretourneerd. Wanneer ingesteld op asynchroon, wordt een reactie verzonden voor elk document dat wordt verwerkt.

Bijvoorbeeld, wordt een e-maileindpunt gecreeerd voor de dienst die één enkel document van Word neemt en dat document als dossier van PDF terugkeert. Een e-mail kan naar inbox van het eindpunt worden verzonden die de veelvoudige (3) documenten van Word bevat. Wanneer alle drie documenten worden verwerkt, als het eindpunt synchroon wordt gevormd, wordt één enkele reactie-e-mail verzonden met alle drie documenten in bijlage. Als het eindpunt asynchroon is, wordt een antwoord-e-mail verzonden nadat elk document van Word in PDF wordt omgezet. Het resultaat is drie e-mails, elk met één PDF bijlage.

De standaardwaarde is asynchroon.

**De originele e-mailtekst opnemen als bijlage:** Wanneer u een e-mail naar de Forms Server verzendt, wordt standaard de oorspronkelijke tekst van het bericht opgenomen in de hoofdtekst van het bericht. Als u de tekst in plaats daarvan als bijlage wilt opnemen, selecteert u deze optie.

**Gebruik de originele onderwerpregel voor resultaate-mails:** Standaard gebruikt de Forms-server de waarden die zijn opgegeven in de instellingen voor E-mailonderwerp met succes en E-mailonderwerp met fouten als onderwerpregel bij het verzenden van e-mailberichten met resultaatmeldingen. Selecteer deze optie als u in plaats daarvan dezelfde onderwerpregel wilt gebruiken als de oorspronkelijke e-mail die naar de server is verzonden.

**E-mailonderwerp geslaagd:** Nadat u een e-mail naar een e-maileindpunt verzendt om een proces te beginnen of voort te zetten, ontvangt u een terugkeer e-mailbericht van de Server van AEM Forms. Als uw e-mail succesvol is, ontvangt u een succesbericht. Als uw e-mail mislukt, ontvangt u een foutbericht waarin u opgeeft waarom dit is mislukt. Met deze instelling kunt u de onderwerpregel van e-mailberichten opgeven die voor dit eindpunt worden verzonden.

**Tekst voor e-mail met succes:** Laat u toe om de lichaamstekst van succes te specificeren e-mailberichten die voor dit eindpunt worden verzonden.

**Fout bij voorvoegsel e-mailonderwerp:** Laat u toe om de tekst te specificeren die aan het begin van de onderwerpregel van mislukkings e-mailberichten wordt gebruikt die voor dit eindpunt worden verzonden.

**Fout in e-mailonderwerp:** Laat u toe om de onderwerpregel van mislukkings e-mailberichten te specificeren die voor dit eindpunt worden verzonden. Deze tekst wordt weergegeven na het voorvoegsel E-mailonderwerp voor fouten.

**Fout in e-mailhoofdtekst:** Laat u toe om de eerste lijn in de lichaamstekst van mislukkings e-mailberichten te specificeren die voor dit eindpunt worden verzonden.

**E-mailoverzichtsgegevens:** Elk succes- of foutbericht bevat een sectie met de originele e-mailtekst die u naar de Forms Server hebt verzonden. Deze instelling geeft de tekst aan die boven die sectie wordt weergegeven.

**Valideer Inbox alvorens dit eindpunt tot stand te brengen/bij te werken:** Wanneer deze optie wordt geselecteerd, controleert de Server van Forms of uw montages SMTP/POP3 correct zijn alvorens het eindpunt te creëren. Wanneer u op Toevoegen klikt, wordt een bericht weergegeven waarin wordt aangegeven of de Postvak IN-account geldig is. Als deze optie niet wordt geselecteerd, leidt de Server van AEM Forms tot het eindpunt zonder inbox te bevestigen.

**Bedrijfsnaam:** Deze instelling is verplicht. Een lijst van verrichtingen die aan het e-maileindpunt kunnen worden toegewezen. De bewerking die u hier selecteert, bepaalt welke velden worden weergegeven in de secties Toewijzingen invoerparameter en Toewijzingen uitvoerparameter.

**Toewijzingen invoerparameter:** Gebruikt om de input te vormen die wordt vereist om de dienst en de verrichting te verwerken. De twee typen invoer zijn letterlijk en variabel:

**Letterlijk:** Het e-mailbericht gebruikt de waarde die in het veld wordt ingevoerd terwijl het wordt weergegeven.

**Variabele:** U kunt een tekenreeks toewijzen aan het e-mailadres van het onderwerp, de tekst, de koptekst of de afzender. Gebruik hiervoor een van de volgende trefwoorden: %SUBJECT%, %BODY%, %HEADER% of %SENDER%. Als u bijvoorbeeld %SUBJECT% gebruikt, wordt de inhoud van het e-mailonderwerp gebruikt als invoerparameter. Als u bijlagen wilt ophalen, voert u een bestandspatroon in dat het e-maileindpunt kan gebruiken om de bijgevoegde documenten te selecteren. Als u bijvoorbeeld &amp;last;.pdf opgeeft, worden alle bijgevoegde documenten met de bestandsnaamextensie .pdf geselecteerd. &amp;Bezig met invoeren van snelheid; selecteert bijgevoegd document. Als u example.pdf invoert, worden alle gekoppelde documenten met de naam example.pdf geselecteerd.

**Toewijzingen uitvoerparameter:** Gebruikt om de output van de dienst en de verrichting te vormen. De volgende tekens in de toewijzingswaarden van de uitvoerparameter worden uitgebreid in de bestandsnaam van de bijlage:

**%F** Vertegenwoordigt de bestandsnaam van het bronbestand (zonder extensie).

**%E** Vertegenwoordigt de extensie van het bronbestand.

Elke keer dat de backslash (\) voorkomt, wordt vervangen door %%.

***notitie **: Als het serviceaanvraagbericht meerdere bestandsbijlagen bevat, kunt u de parameters %F en %E niet gebruiken voor de eigenschap Uitvoerparametertoewijzingen van het eindpunt. Als de servicereactie meerdere bestandsbijlagen retourneert, kunt u niet dezelfde bestandsnaam voor meerdere bijlagen opgeven. Als u deze aanbevelingen niet volgt, leidt de aangehaalde dienst tot de namen voor de teruggekeerde dossiers, en de namen zijn niet voorspelbaar.*

De volgende waarden zijn beschikbaar:

**Enkel object:** De e-mailprovider heeft niet de bestemming van de bronmap; de resultaten worden geretourneerd als bijlagen. Het patroon is Result/%F.ps en retourneert Result%%sourcefilename.ps als de bestandsbijlage.

**Lijst:** Het patroon is Resultaat/%F/ en retourneert Result%%sourcefilename%%file1 als de bestandsbijlage.

**Toewijzing:** Het patroon is Result/%F/ en de bronbestemming is Result%%sourcefilename%%file1 en Result%%sourcefilename%%file2. Als de kaart meer dan één voorwerp bevat en het patroon Result/%F.ps is, zijn de gehechtheid van het reactiedossier Result%%sourcefilename1.ps (output 1) en Result%%sourcefilename2.ps (output 2).

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
1. Selecteer Variabele en typ in de lijst Bijlage `*.*` in het aangrenzende vak. Dit verzendt alle gehechtheid van de binnenkomende postberichten naar een kaartvariabele voor het Volledige proces van de Taak.
1. Selecteer in de lijst MailBody de variabele en typ `%BODY%` in het aangrenzende vak.
1. Selecteer Variabele in de lijst MailFrom en typ `%SENDER%` in het aangrenzende vak. Dit brengt het afzenderadres aan de Volledige het procesgegevens van de Taak in kaart.
1. Typ in het vak Resultaten `results`. Dit veroorzaakt de Volledige Taak of het Proces van het Begin om een resultaatkoord terug te keren.
1. Klik toevoegen.
