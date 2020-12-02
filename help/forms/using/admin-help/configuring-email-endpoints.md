---
title: E-maileindpunten configureren
seo-title: E-maileindpunten configureren
description: Leer hoe u e-maileindpunten configureert.
seo-description: Leer hoe u e-maileindpunten configureert.
uuid: d47bb45b-0e0e-43ca-9e25-e347d0e60206
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_endpoints
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: dcf15c42-9ec6-4d1c-ad41-083aa0b8c7ae
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f
workflow-type: tm+mt
source-wordcount: '3766'
ht-degree: 0%

---


# E-maileindpunten {#configuring-email-endpoints} configureren

Met e-maileindpunten kunnen gebruikers de service aanroepen door een of meer documenten (als e-mailbijlagen) naar een opgegeven e-mailaccount te verzenden. Het e-mailpostvak fungeert als verzamelpunt voor de bijlagen. De service bewaakt de Postvak IN en verwerkt de bijlagen. De resultaten van de omzetting worden door:sturen aan de gebruiker die in het eindpunt wordt bepaald.

Voor een e-maileindpunt kunnen geautoriseerde gebruikers een proces aanroepen door bestanden naar de juiste account te e-mailen. De resultaten zullen aan de verzendende gebruiker (door gebrek) of aan de gebruiker worden teruggekeerd die in de eindpuntmontages wordt bepaald.

Alvorens u een e-maileindpunt vormt, creeer een POP3 of IMAP e-mailrekening voor gebruik door het eindpunt. Stel een aparte account in voor elk type conversie. U kunt bijvoorbeeld één account configureren om standaard PDF-documenten te genereren op basis van binnenkomende bestandsbijlagen en een andere account configureren om beveiligde PDF-documenten te genereren.

>[!NOTE]
>
>Elk e-mailadres moet aan slechts één e-maileindpunt in kaart brengen. U kunt geen meerdere e-maileindpunten configureren naar één e-mailadres, zelfs niet als de extra e-maileindpunten zijn uitgeschakeld.

Alle e-maileindpunten zijn geconfigureerd met een geoorloofde gebruikersnaam en wachtwoord voor de e-mailpostvak, die vereist zijn wanneer de service wordt aangeroepen. Het e-mailaccount is beveiligd door het systeem van de mailserver waarop het is geconfigureerd.

Als uw gebruikers documenten met West-Europese taalkarakters in dossier en omzettingswegnamen verzenden, moeten zij een e-mailtoepassing gebruiken die de vereiste coderingstypes (Latin1 [ISO-8859-1], West-Europees [Vensters], of UTF-8) steunt. Zie *AEM formulieren installeren en implementeren* voor meer informatie.

Alvorens u een e-maileindpunt vormt, vorm de E-maildienst. (Zie [Standaardinstellingen voor e-maileindpunt configureren](configuring-email-endpoints.md#configure-default-email-endpoint-settings).) De configuratieparameters van de e-mailservice hebben twee doelen:

* Om attributen te vormen die voor alle e-maileindpunten gemeenschappelijk zijn
* Standaardwaarden opgeven voor alle e-maileindpunten

## SSL configureren voor een e-maileindpunt {#configure-ssl-for-an-email-endpoint}

U kunt POP3, IMAP, of SMTP vormen om de Veilige Laag van Contactdozen (SSL) voor een e-maileindpunt te gebruiken.

1. Schakel op de e-mailserver SSL voor POP3, IMAP of SMTP in volgens de documentatie van de fabrikant.
1. Een clientcertificaat exporteren van de e-mailserver.
1. Gebruik het hulpprogramma Keytool om het clientcertificaatbestand te importeren naar het JVM-certificaatarchief (Java Virtual Machine) van de toepassingsserver. De procedure voor deze stap is afhankelijk van de installatiepaden van JVM en client.

   Als u bijvoorbeeld een standaard Oracle WebLogic Server-installatie gebruikt met JDK 1.5.0 op Microsoft Windows Server® 2003, typt u de volgende tekst in een opdrachtprompt:

   `keytool -import -file client_certificate -alias myalias -keystore BEA_HOME\jdk150_04\jre\security\cacerts`

1. Voer desgevraagd het wachtwoord in (voor Java is het standaardwachtwoord `changeit`). U ontvangt een bericht met de mededeling dat het certificaat is geïmporteerd.
1. De beleidsconsole van het gebruik om het e-maileindpunt aan de dienst toe te voegen.
1. Maak het e-maileindpunt in de beheerconsole. Wanneer het vormen van de eindpuntmontages, uitgezochte POP3/IMAP SSL Toegelaten voor inkomende berichten en SMTP SSL Toegelaten voor uitgaande berichten, en verander dienovereenkomstig de haveneigenschappen.

>[!NOTE]
>
>Tip: Als u problemen ondervindt bij het gebruik van SSL, gebruikt u een e-mailclient zoals Microsoft Outlook om te controleren of deze via SSL toegang heeft tot de e-mailserver. Als de e-mailclient geen toegang heeft tot de e-mailserver, is de uitgave gerelateerd aan de configuratie van uw certificaat of uw e-mailserver.

## Standaardinstellingen voor het e-maileindpunt configureren {#configure-default-email-endpoint-settings}

U kunt de pagina van het Beheer van de Dienst gebruiken om attributen te vormen die voor alle e-maileindpunten gemeenschappelijk zijn, en standaardwaarden voor alle e-maileindpunten te verstrekken.

Als u wilt dat de formulierwerkstroom binnenkomende e-mailberichten van gebruikers ontvangt en afhandelt, moet u een e-maileindpunt voor de service Volledige taak maken. Dit e-maileindpunt vereist extra montages, zoals die in [worden beschreven een E-maileindpunt voor de Volledige dienst van de Taak ](configuring-email-endpoints.md#create-an-email-endpoint-for-the-complete-task-service) creëren.

### De standaardwaarden wijzigen voor e-maileindpunten {#change-the-default-values-for-email-endpoints}

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Klik op E-mail op de pagina Servicebeheer: 1.0 (de component-id is com.adobe.idp.dsc.provider.service.email.Email).
1. Voor het lusje van de Configuratie, specificeer de standaard e-maileindpuntmontages en klik dan sparen.

### Standaardinstellingen {#default-email-endpoint-settings} voor e-maileindpunt

**Uitsnijdexpressie:** de uitsnijdexpressie die door het kwartpunt wordt gebruikt om de opiniepeiling van de invoermap te plannen.

**Interval herhalen:** Het aantal keren dat de mappenopiniepeiling wordt herhaald. Het standaardherhalingsinterval is in seconden als deze waarde niet in de eindpuntconfiguratie wordt gespecificeerd. De standaardwaarde is 10. Deze waarde mag niet kleiner zijn dan 10.

**Aantal herhalingen:** het aantal keren dat de invoermap wordt gepolled. De standaardherhalingstelling om te gebruiken als deze waarde niet in de eindpuntconfiguratie wordt gespecificeerd. De waarde -1 geeft aan dat de map voor onbepaalde tijd wordt gescand. De standaardwaarde is -1.

**Vertraging wanneer de baan begint:** De standaardwaarde, in seconden, voor de vertraging alvorens de baan begint het eindpunt af te tasten. De standaardwaarde is 0.

**Batchgrootte:** het aantal e-mails dat de ontvangers verwerken per scan voor optimale prestaties. De waarde -1 geeft alle e-mails aan. De standaardwaarde is 2.

**Asynchroon:** Identificeert het aanroepingstype als asynchroon of synchroon. De voorbijgaande en synchrone processen kunnen slechts synchroon worden aangehaald. De standaardwaarde is asynchroon.

**Domeinpatroon:** het domeinnaampatroon dat wordt gebruikt om binnenkomende e-mails te filteren. Als bijvoorbeeld adobe.com wordt gebruikt, wordt alleen e-mail van adobe.com verwerkt. E-mail van andere domeinen wordt genegeerd.

**Bestandspatroon:** de inkomende patronen voor bestandsbijlagen die de provider accepteert. Dit omvat bestanden met specifieke extensies (&amp;ast;.dat, &amp;ast;.xml), specifieke namen (gegevens) en samengestelde expressies in de naam en de extensie (.[dD][aA]&#39;port&#39;). De standaardwaarde is &amp;ast;.&amp;ast;.

**Ontvangers van taak met succes:** een of meer e-mailadressen die worden gebruikt om e-mails te verzenden om aan te geven dat taken zijn geslaagd. Standaard wordt altijd een bericht met een geslaagde taak verzonden naar de afzender van de oorspronkelijke taak. Er worden maximaal 100 ontvangers ondersteund. Laat dit veld leeg als u deze instelling wilt uitschakelen.

**Ontvangers van mislukte taak:** Een of meer e-mailadressen die worden gebruikt om e-mails te verzenden om aan te geven dat taken zijn mislukt. Standaard wordt een mislukte taakbericht altijd verzonden naar de afzender die de eerste taak heeft verzonden. Er worden maximaal 100 ontvangers ondersteund. Laat dit veld leeg als u deze instelling wilt uitschakelen.

**Inbox Host:** de hostnaam van de inbox of het IP-adres van de e-mailprovider die moet worden gescand.

**Poort in vak:** het inbox-poortnummer dat de e-mailprovider moet scannen. Als de waarde 0 is, wordt de standaard IMAP- of POP3-poort gebruikt.

**Inbox Protocol:** het e-mailprotocol voor het e-maileindpunt dat moet worden gebruikt om inbox af te tasten. De keuzen zijn IMAP of POP3. De postserver van de inbox gastheer moet deze protocollen steunen.

**Inbox Tijd uit:** Specificeert de hoeveelheid tijd het eindpunt alvorens zal wachten te annuleren wanneer het proberen om met inbox te verbinden. Als er geen verbinding wordt gemaakt voordat de time-outwaarde is bereikt, wordt het inbox niet gepolled.

**Inbox Gebruiker:** De gebruikersnaam die is vereist om u aan te melden bij de e-mailaccount. Afhankelijk van de e-mailserver en configuratie is deze naam mogelijk alleen het onderdeel met de gebruikersnaam van de e-mail of is het mogelijk het volledige e-mailadres.

**Postvak IN:Wachtwoord:** het wachtwoord voor de gebruiker Inbox.

**POP3/IMAP SSL ingeschakeld:** Wanneer deze optie is geselecteerd, wordt SSL ingeschakeld.

**SMTP-host:** de hostnaam van de mailserver die de e-mailprovider gebruikt om resultaten en foutberichten te verzenden. Bijvoorbeeld mail.corp.example.com.

**SMTP-poort:** de poort die wordt gebruikt om verbinding te maken met de mailserver. De standaardwaarde is 25.

**SMTP-gebruiker:** De gebruikersaccount voor de e-mailprovider die moet worden gebruikt wanneer deze e-mail verzendt voor resultaten en fouten.

**SMTP-wachtwoord:** het wachtwoord voor de SMTP-account. Voor sommige mailservers is geen SMTP-wachtwoord vereist.

**Verzenden vanaf:** Het e-mailadres (bijvoorbeeld user@company.com) dat wordt gebruikt voor het verzenden van e-mailmeldingen over resultaten en fouten. Als u geen waarde opgeeft voor Verzenden vanaf, probeert de e-mailserver het e-mailadres te bepalen door de waarde die is opgegeven in de instelling SMTP-gebruiker te combineren met een standaarddomein dat is geconfigureerd op de e-mailserver. Als uw e-mailserver geen standaarddomein heeft en u geen waarde opgeeft voor Verzenden vanaf, kunnen er fouten optreden. Geef een waarde op voor de instelling Verzenden vanaf om ervoor te zorgen dat de e-mailberichten het juiste adres hebben.

**SMTP SSL ingeschakeld:** Wanneer deze optie is geselecteerd, wordt SSL ingeschakeld via SMTP.

**De originele e-mailtekst opnemen als bijlage:** standaard wordt de oorspronkelijke tekst van het bericht opgenomen in de hoofdtekst van het bericht wanneer u een e-mail verzendt naar de formulierserver. Als u de tekst in plaats daarvan als bijlage wilt opnemen, selecteert u deze optie.

**Gebruik de originele onderwerpregel voor resultaate-mails:** Standaard gebruikt de Forms-server de waarden die zijn opgegeven in de instellingen voor E-mailonderwerp met succes en E-mailonderwerp met fout als onderwerpregel bij het verzenden van resultaatberichten. Selecteer deze optie als u in plaats daarvan dezelfde onderwerpregel wilt gebruiken als de oorspronkelijke e-mail die naar de server is verzonden.

**E-mailonderwerp met succes:** Nadat u een e-mailbericht naar een e-maileindpunt hebt verzonden om een proces te starten of voort te zetten, ontvangt u een e-mailbericht van de server voor AEM formulieren. Als uw e-mail succesvol is, ontvangt u een succesbericht. Als uw e-mail mislukt, ontvangt u een foutbericht waarin u opgeeft waarom dit is mislukt. Met deze instelling kunt u de onderwerpregel van e-mailberichten opgeven die voor dit eindpunt worden verzonden.

**Tekst voor e-mail met succes:** Laat u toe om de lichaamstekst van succes te specificeren e-mailberichten die voor dit eindpunt worden verzonden.

**Voorvoegsel E-mailonderwerp van de fout:** Laat u toe om de tekst te specificeren die aan het begin van de onderwerpregel van mislukkings e-mailberichten wordt gebruikt die voor dit eindpunt worden verzonden.

**Fout-e-mailonderwerp:** Laat u toe om de onderwerpregel van mislukkings-e-mailberichten te specificeren die voor dit eindpunt worden verzonden. Deze tekst wordt weergegeven na het voorvoegsel E-mailonderwerp voor fouten.

**Hoofdtekst van fout-e-mail:** Laat u toe om de eerste lijn in de lichaamstekst van mislukkings e-mailberichten te specificeren die voor dit eindpunt worden verzonden.

**E-mailoverzicht Info:** Elk succes- of foutbericht bevat een sectie met de originele e-mailtekst die u naar de formulierserver hebt verzonden. Deze instelling geeft de tekst aan die boven die sectie wordt weergegeven.

**Valideer Inbox alvorens dit Eindpunt te creëren/bij te werken:** Wanneer deze optie wordt geselecteerd, controleert de vormenserver of uw montages SMTP/POP3 correct zijn alvorens het eindpunt tot stand te brengen. Wanneer u op Toevoegen klikt, wordt een bericht weergegeven waarin wordt aangegeven of de Postvak IN-account geldig is. Als deze optie niet is geselecteerd, maakt de AEM-formulierserver het eindpunt zonder het postvak in te vullen.

**Codering tekenset:** de coderingsindeling die voor het e-mailbericht moet worden gebruikt. Het gebrek is UTF-8, die de meeste gebruikers buiten Japan zullen gebruiken. Gebruikers in een Japanse omgeving kunnen kiezen voor ISO2022-JP.

**Verzonden map via e-mail is mislukt:** geeft een map op waarin de resultaten moeten worden opgeslagen als de SMTP-mailserver niet operationeel is.

## Instellingen voor e-maileindpunt {#email-endpoint-settings}

Gebruik de volgende montages om een e-maileindpunt te vormen.

**Naam:** Een verplichte instelling die het eindpunt aangeeft. Neem geen &lt;-teken op omdat de naam die in Workspace wordt weergegeven hierdoor wordt afgekapt. Als u een URL als naam van het eindpunt ingaat, zorg ervoor dat het met de syntaxisregels in overeenstemming is die in RFC1738 worden gespecificeerd.

**Beschrijving:** Een beschrijving van het eindpunt. Neem geen &lt;-teken op omdat dit de beschrijving in Workspace afkapt.

**Uitsnijduitdrukking:** Voer een uitsnijduitdrukking in als de e-mail moet worden gepland met een uitsnijduitdrukking.

**Aantal herhalingen:** Aantal keren dat het e-maileindpunt de map of map scant. De waarde -1 geeft aan dat een scanbewerking voor onbepaalde tijd wordt uitgevoerd. De standaardwaarde is -1.

**Interval herhalen:** de scansnelheid die de ontvanger gebruikt om inkomende e-mail te controleren.

**Vertraging wanneer de baan begint:** de tijd om te wachten om te scannen nadat de planner begint.

**Batchgrootte:** het aantal e-mails dat de ontvangers verwerken per scan voor optimale prestaties. De waarde -1 geeft alle e-mails aan. De standaardwaarde is 2.

**Gebruikersnaam:** Een verplichte instelling. Dit is de gebruikersnaam die wordt gebruikt bij het aanroepen van een doelservice via e-mail. De standaardwaarde is SuperAdmin.

**Domeinnaam:** Een verplichte instelling, het domein van de gebruiker. De standaardwaarde is DefaultDom.

**Domeinpatroon:** geeft de domeinpatronen op van binnenkomende e-mail die de provider accepteert. Als bijvoorbeeld adobe.com wordt gebruikt, wordt alleen e-mail van adobe.com verwerkt. E-mail van andere domeinen wordt genegeerd.

**Bestandspatroon:** geeft de inkomende patronen voor bestandsbijlagen op die de provider accepteert. Dit omvat bestanden met specifieke extensies (&amp;ast;.dat, &amp;ast;.xml), specifieke namen (gegevens) of samengestelde expressies in de naam en extensie (&amp;ast;..[dD][aA]&#39;port&#39;).

**Ontvangers van taak met succes:** Een e-mailadres waarnaar berichten worden verzonden om aan te geven dat taken zijn geslaagd. Standaard wordt altijd een bericht met een geslaagde taak naar de afzender verzonden. Als u de afzender typt, worden de e-mailresultaten verzonden naar de afzender. Er worden maximaal 100 ontvangers ondersteund. Geef extra ontvangers op met e-mailadressen, gescheiden door komma&#39;s (,).

Laat de instelling leeg als u deze instelling wilt uitschakelen. In sommige gevallen wilt u een proces activeren en geen e-mailmelding van het resultaat.

**Ontvangers van mislukte taak:** Een e-mailadres waarnaar berichten worden verzonden om mislukte taken aan te geven. Standaard wordt altijd een mislukte taakbericht naar de afzender verzonden. Als u de afzender typt, worden de e-mailresultaten verzonden naar de afzender. Er worden maximaal 100 ontvangers ondersteund. Geef extra ontvangers op met e-mailadressen, gescheiden door komma&#39;s (,).

Laat de instelling leeg als u deze instelling wilt uitschakelen. In sommige gevallen wilt u een proces activeren en geen e-mailmelding van het resultaat.

**Inbox Host:** de hostnaam van de inbox of het IP-adres van de e-mailprovider die moet worden gescand.

**Poort in vak:** de poort die de e-mailserver gebruikt. De standaardwaarde voor POP3 is 110 en de standaardwaarde voor IMAP is 143. Als SSL wordt toegelaten, is de standaardwaarde voor POP3 995 en de standaardwaarde voor IMAP is 993.

**Inbox Protocol:** het e-mailprotocol voor het e-maileindpunt dat moet worden gebruikt om inbox af te tasten. De waarden zijn IMAP of POP3. De postserver van de inbox gastheer moet deze protocollen steunen.

**Inbox Time Out:** De time-out, in seconden, voor de e-mailprovider die wacht op reacties in het Postvak IN.

**Inbox Gebruiker:** De gebruikersnaam die is vereist om u aan te melden bij de e-mailaccount. Afhankelijk van de e-mailserver en configuratie kan deze waarde alleen het onderdeel met de gebruikersnaam van de e-mail zijn of het volledige e-mailadres.

**Wachtwoord in vak:** het wachtwoord voor de gebruiker in het Postvak IN.

**POP3/IMAP SSL ingeschakeld:** selecteer deze instelling om de e-mailprovider te dwingen SSL te gebruiken om de Postvak IN te scannen. Controleer of uw mailserver SSL ondersteunt.

**SMTP-host:** de hostnaam van de mailserver die de e-mailprovider gebruikt om resultaten en foutberichten te verzenden.

**SMTP-poort:** de standaardwaarde voor de SMTP-poort is 25.

**SMTP-gebruiker:** De gebruikersaccount voor de e-mailprovider die moet worden gebruikt wanneer deze e-mailmeldingen over resultaten en fouten verzendt.

**SMTP-wachtwoord:** het wachtwoord voor de SMTP-account. Voor sommige mailservers is geen SMTP-wachtwoord vereist.

**Verzenden vanaf:** Het e-mailadres (bijvoorbeeld user@company.com) dat wordt gebruikt voor het verzenden van e-mailmeldingen over resultaten en fouten. Als u geen waarde opgeeft voor Verzenden vanaf, probeert de e-mailserver het e-mailadres te bepalen door de waarde die is opgegeven in de instelling SMTP-gebruiker te combineren met een standaarddomein dat is geconfigureerd op de e-mailserver. Als uw e-mailserver geen standaarddomein heeft en u geen waarde opgeeft voor Verzenden vanaf, kunnen er fouten optreden. Geef een waarde op voor de instelling Verzenden vanaf om ervoor te zorgen dat de e-mailberichten het juiste adres hebben.

**SMTP SSL ingeschakeld:** selecteer deze instelling om de e-mailprovider te dwingen SSL te gebruiken om de Postvak IN te scannen. Controleer of uw mailserver SSL ondersteunt.

**Verzonden map via e-mail is mislukt:** geeft een map op waarin de resultaten moeten worden opgeslagen als de SMTP-mailserver niet operationeel is.

**asynchroon:** Wanneer ingesteld op synchroon, worden alle invoerdocumenten verwerkt en wordt één reactie geretourneerd. Wanneer ingesteld op asynchroon, wordt een reactie verzonden voor elk document dat wordt verwerkt.

Er wordt bijvoorbeeld een e-maileindpunt gemaakt voor een service die gebruikmaakt van één Word-document en dat document retourneert als een PDF-bestand. Een e-mail kan naar inbox van het eindpunt worden verzonden die de veelvoudige (3) documenten van Word bevat. Wanneer alle drie documenten worden verwerkt, als het eindpunt synchroon wordt gevormd, wordt één enkele reactie-e-mail verzonden met alle drie documenten in bijlage. Als het eindpunt asynchroon is, wordt een antwoord-e-mail verzonden nadat elk Word-document is geconverteerd naar PDF. Het resultaat is drie e-mailberichten, elk met één PDF-bijlage.

De standaardwaarde is asynchroon.

**De originele e-mailtekst opnemen als bijlage:** Standaard wordt de oorspronkelijke tekst van het bericht opgenomen in de hoofdtekst van het bericht wanneer u een e-mail verzendt naar de formulierserver. Als u de tekst in plaats daarvan als bijlage wilt opnemen, selecteert u deze optie.

**Gebruik de oorspronkelijke onderwerpregel voor resultaate-mails:** Standaard gebruikt de Forms-server de waarden die zijn opgegeven in de instellingen E-mailonderwerp met succes en E-mailonderwerp met fout als onderwerpregel bij het verzenden van resultaatberichten. Selecteer deze optie als u in plaats daarvan dezelfde onderwerpregel wilt gebruiken als de oorspronkelijke e-mail die naar de server is verzonden.

**E-mailonderwerp met succes:** Nadat u een e-mailbericht naar een e-maileindpunt hebt verzonden om een proces te starten of voort te zetten, ontvangt u een e-mailbericht van de server voor AEM formulieren. Als uw e-mail succesvol is, ontvangt u een succesbericht. Als uw e-mail mislukt, ontvangt u een foutbericht waarin u opgeeft waarom dit is mislukt. Met deze instelling kunt u de onderwerpregel van e-mailberichten opgeven die voor dit eindpunt worden verzonden.

**Tekst voor e-mail met succes:** Laat u toe om de lichaamstekst van succes te specificeren e-mailberichten die voor dit eindpunt worden verzonden.

**Voorvoegsel E-mailonderwerp van de fout:** Laat u toe om de tekst te specificeren die aan het begin van de onderwerpregel van mislukkings e-mailberichten wordt gebruikt die voor dit eindpunt worden verzonden.

**Fout-e-mailonderwerp:** Laat u toe om de onderwerpregel van mislukkings-e-mailberichten te specificeren die voor dit eindpunt worden verzonden. Deze tekst wordt weergegeven na het voorvoegsel E-mailonderwerp voor fouten.

**Hoofdtekst van fout-e-mail:** Laat u toe om de eerste lijn in de lichaamstekst van mislukkings e-mailberichten te specificeren die voor dit eindpunt worden verzonden.

**E-mailoverzicht Info:** Elk succes- of foutbericht bevat een sectie met de originele e-mailtekst die u naar de formulierserver hebt verzonden. Deze instelling geeft de tekst aan die boven die sectie wordt weergegeven.

**Valideer Inbox alvorens dit eindpunt tot stand te brengen/bij te werken:** Wanneer deze optie wordt geselecteerd, controleert de vormenserver of uw montages SMTP/POP3 correct zijn alvorens het eindpunt tot stand te brengen. Wanneer u op Toevoegen klikt, wordt een bericht weergegeven waarin wordt aangegeven of de Postvak IN-account geldig is. Als deze optie niet is geselecteerd, maakt de AEM-formulierserver het eindpunt zonder het postvak in te vullen.

**Naam van bewerking:** deze instelling is verplicht. Een lijst van verrichtingen die aan het e-maileindpunt kunnen worden toegewezen. De bewerking die u hier selecteert, bepaalt welke velden worden weergegeven in de secties Toewijzingen invoerparameter en Toewijzingen uitvoerparameter.

**Invoer Parameter Mappings:** Gebruikt om de input te vormen die wordt vereist om de dienst en de verrichting te verwerken. De twee typen invoer zijn letterlijk en variabel:

**Letterlijk:** Het e-mailbericht gebruikt de waarde die in het veld wordt ingevoerd terwijl het wordt weergegeven.

**Variabele:** u kunt een tekenreeks toewijzen aan het e-mailadres van het onderwerp, de tekst, de koptekst of de afzender. Hiervoor gebruikt u een van de volgende trefwoorden: %SUBJECT%, %BODY%, %HEADER% of %SENDER%. Als u bijvoorbeeld %SUBJECT% gebruikt, wordt de inhoud van het e-mailonderwerp gebruikt als invoerparameter. Als u bijlagen wilt ophalen, voert u een bestandspatroon in dat het e-maileindpunt kan gebruiken om de bijgevoegde documenten te selecteren. Als u bijvoorbeeld &amp;ast;.pdf opgeeft, worden alle bijgevoegde documenten met de bestandsnaamextensie .pdf geselecteerd. &amp;amp invoeren;ast; selecteert een bijgevoegd document. Als u example.pdf invoert, worden alle gekoppelde documenten met de naam example.pdf geselecteerd.

**Toewijzingen uitvoerparameter:** gebruikt om de uitvoer van de service en bewerking te configureren. De volgende tekens in de toewijzingswaarden van de uitvoerparameter worden uitgebreid in de bestandsnaam van de bijlage:

**%** FRVertegenwoordigt de bestandsnaam van het bronbestand (zonder extensie).

**%** ERVertegenwoordigt de extensie van het bronbestand.

Elke keer dat de backslash (\) voorkomt, wordt vervangen door %%.

***opmerking **: Als het serviceaanvraagbericht meerdere bestandsbijlagen bevat, kunt u de parameters %F en %E niet gebruiken voor de eigenschap Uitvoerparametertoewijzingen van het eindpunt. Als de servicereactie meerdere bestandsbijlagen retourneert, kunt u niet dezelfde bestandsnaam voor meerdere bijlagen opgeven. Als u deze aanbevelingen niet volgt, leidt de aangehaalde dienst tot de namen voor de teruggekeerde dossiers, en de namen zijn niet voorspelbaar.*

De volgende waarden zijn beschikbaar:

**Eén object:** de e-mailprovider heeft niet de bestemming van de bronmap; resultaten worden geretourneerd als bijlagen. Het patroon is Result/%F.ps en retourneert Result%%sourcefilename.ps als de bestandsbijlage.

**Lijst:** Het patroon is Resultaat/%F/ en retourneert Result%%sourcefilename%%file1 als de bestandsbijlage.

**Toewijzing:** Het patroon is Result/%F/ en de bronbestemming is Result%%sourcefilename%%file1 en Result%%sourcefilename%%file2. Als de kaart meer dan één voorwerp bevat en het patroon Result/%F.ps is, zijn de gehechtheid van het reactiedossier Result%%sourcefilename1.ps (output 1) en Result%%sourcefilename2.ps (output 2).

## Creeer een E-maileindpunt voor de Volledige dienst van de Taak {#create-an-email-endpoint-for-the-complete-task-service}

Als u wilt dat de formulierwerkstroom binnenkomende e-mailberichten van gebruikers ontvangt en afhandelt, moet u een e-maileindpunt voor de service Volledige taak maken.

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Voor de pagina van het Beheer van de Dienst, klik de Volledige dienst van de Taak.
1. Selecteer op het tabblad Eindpunten de optie E-mail in de vervolgkeuzelijst en klik op Toevoegen.
1. Typ de hostnaam of het IP-adres van de mailserver in het vak Inbox-host.
1. Typ in het vak Inbox-gebruiker de gebruikersnaam die is vereist voor aanmelding bij de e-mailaccount die u hebt gemaakt voor de verwerking van formulierverzendingen. Afhankelijk van de e-mailserver en configuratie kan deze naam alleen het onderdeel met de gebruikersnaam van de e-mail zijn of het volledige e-mailadres.
1. Typ het wachtwoord voor de Postvak In in het vak Wachtwoord Postvak IN.
1. Typ in het vak SMTP-host de hostnaam of het IP-adres van de mailserver waarvan de e-mailprovider de resultaten en foutberichten verzendt.
1. Typ in het vak SMTP-gebruiker de gebruikersaccount voor de e-mailprovider die moet worden gebruikt wanneer deze e-mail verzendt voor resultaten en fouten. Dit gebruikersaccount kan dezelfde waarde zijn als voor Inbox-gebruiker.
1. Typ in het vak SMTP-wachtwoord het wachtwoord voor de SMTP-account.
1. Selecteer Inhalen in de lijst Operation Name.
1. Selecteer in de lijst BijlageMap de optie Variabele en typ `*.*` in het aangrenzende vak. Dit verzendt alle gehechtheid van de binnenkomende postberichten naar een kaartvariabele voor het Volledige proces van de Taak.
1. Selecteer in de lijst mailBody een variabele en typ `%BODY%` in het aangrenzende vak.
1. Selecteer in de lijst MailFrom de optie Variabele en typ `%SENDER%` in het aangrenzende vak. Dit brengt het afzenderadres aan de Volledige het procesgegevens van de Taak in kaart.
1. Typ `results` in het vak Resultaten. Dit veroorzaakt de Volledige Taak of Proces van het Begin om een resultaatkoord terug te keren.
1. Klik op Toevoegen.

