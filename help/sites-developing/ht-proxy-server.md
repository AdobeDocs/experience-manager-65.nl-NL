---
title: Het gereedschap Proxyserver gebruiken
description: De proxyserver fungeert als een tussenliggende server die verzoeken tussen een client en een server afspeelt
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 7222a0c3-cdb9-4c73-9d53-26f00792e439
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '943'
ht-degree: 0%

---

# Het gereedschap Proxyserver gebruiken{#how-to-use-the-proxy-server-tool}

De proxyserver fungeert als een tussenliggende server die verzoeken tussen een client en een server afspeelt. De volmachtsserver volgt alle cliënt-server interactie en output een logboek van de volledige mededeling van TCP. Dit laat u precies controleren wat aan de hand is, zonder het moeten tot de belangrijkste server toegang hebben.

U kunt hier de proxyserver in uw AEM-installatie vinden:

`crx-quickstart/opt/helpers/proxy-2.1.jar`

U kunt de volmachtsserver gebruiken om alle cliënt-server interactie, ongeacht het onderliggende communicatie protocol te controleren. U kunt bijvoorbeeld de volgende protocollen controleren:

* HTTP voor Web-pagina&#39;s
* HTTPS voor beveiligde webpagina&#39;s
* SMTP voor e-mailberichten
* LDAP voor gebruikersbeheer

U kunt bijvoorbeeld de proxyserver tussen twee toepassingen plaatsen die via een TCP/IP-netwerk communiceren, bijvoorbeeld een webbrowser en AEM. Hiermee kunt u precies controleren wat er gebeurt wanneer u een CQ-pagina aanvraagt.

## Het gereedschap Proxyserver starten {#starting-the-proxy-server-tool}

Start de server op de opdrachtregel:

`java -jar proxy-2.1.jar <host> <remoteport> <localport> [options]`

**Parameters**

`<host>`

Dit is het hostadres van de CRX-instantie waarmee u verbinding wilt maken. Als de instantie zich op uw lokale computer bevindt, is dit `localhost`.

`<remoteport>`

Dit is de gastheerhaven van de doelCRX instantie. De standaardinstelling van een nieuw geïnstalleerde AEM is bijvoorbeeld **`4502`** en de standaardinstelling voor een nieuw geïnstalleerd AEM auteur-exemplaar is `4502`.

`<localport>`

Dit is de poort op uw lokale computer die u wilt gebruiken om verbinding te maken met de CRX-instantie via de proxy.

**Opties**

`-q` (stille modus)

Schrijft niet de output aan het consolevenster. Gebruik deze optie als u de verbinding niet wilt vertragen of als u de uitvoer naar een bestand wilt vastleggen (zie de optie -logfile).

`-b`(binaire modus)

Als u specifieke bytecombinaties in het verkeer zoekt, laat binaire wijze toe. De uitvoer bevat vervolgens de hexadecimale uitvoer en de tekenuitvoer.

`-t` (logbestandvermeldingen voor tijdstempel)

Hiermee voegt u een tijdstempel toe aan elk logbestand. Het tijdstempel is in seconden, zodat het mogelijk niet geschikt is voor het controleren van afzonderlijke aanvragen. Gebruik het om van gebeurtenissen de plaats te bepalen die in een specifiek ogenblik voorkwamen als u de volmachtsserver over een langere tijdspanne gebruikt.

`-logfile <filename>`(schrijven naar logbestand)

Schrijft het cliënt-server gesprek aan een logboekdossier. Deze parameter werkt ook in de stille modus.

**`-i <numIndentions>`**(inspringing toevoegen)

Elke actieve verbinding springt in voor betere leesbaarheid. De standaardwaarde is 16 niveaus. Deze functie is geïntroduceerd met `proxy.jar version 1.16`.

### Logbestandsindeling {#log-format}

De logboekingangen die door volmacht-2.1.jar worden geproduceerd hebben allen het volgende formaat:

`[timestamp (optional)] [Client|Server]-[ConnectionNumber]-[BytePosition] ->[Character Stream]`

Een verzoek om een webpagina kan er bijvoorbeeld als volgt uitzien:

`C-0-#000000 -> [GET /author/prox.html?CFC_cK=1102938422341 HTTP/1.1 ]`

* C betekent dat deze ingang uit de cliënt (het is een verzoek om een Web-pagina) komt
* 0 is het verbindingsnummer (de verbindenteller begint bij 0)
* #00000 de verschuiving in de bytestream. Dit is de eerste vermelding, dus de verschuiving is 0.
* `[GET <?>]` Dit is de inhoud van de aanvraag, in het voorbeeld een van de HTTP-headers (url).

Wanneer een verbinding sluit, wordt de volgende informatie geregistreerd:

```
C-6-Finished: 758 bytes (1.0 kb/s)
S-6-Finished: 665 bytes (1.0 kb/s)
```

Dit toont het aantal bytes dat tussen cliënt ( `C`) en de server ( `S`) op de zesde aansluiting en op de gemiddelde snelheid.

**Een voorbeeld van een logbestandsuitvoer**

Neem bijvoorbeeld een pagina die op verzoek de volgende code produceert:

### Voorbeeld {#example}

Neem bijvoorbeeld een eenvoudig HTML-document in de repository op

`/content/test.html`

Naast een afbeeldingsbestand op

`/content/test.jpg`

De inhoud van `test.html` is:

```xml
<html>
<head>
    <title>Test</title>
</head>
<body>
    Test<br>
    <img src="test.jpg">
</body>
</html>
```

Ervan uitgaande dat de AEM-instantie ingeschakeld is `localhost:4502`, wordt de proxy als volgt gestart:

`java -jar proxy.jar localhost 4502 4444 -logfile test.log`

De CQ/CRX-instantie is nu toegankelijk via de proxy op `localhost:4444` en alle communicatie via deze poort is aangemeld bij `test.log`.

Als u nu de uitvoer van de proxy bekijkt, ziet u de interactie tussen de browser en de AEM.

Bij het opstarten voert de proxy het volgende uit:

```xml
starting proxy for localhost:4502 on port 4444
using logfile: <some-dir>/crx-quickstart/opt/helpers/test.log
```

Open nu een browser en open de testpagina:

`http://localhost:4444/content/test.html`

Je ziet dat de browser een `GET` verzoek om de pagina:

```shell
C-0-#000000 -> [GET /content/test.html HTTP/1.1 ]
C-0-#000033 -> [Host: localhost:4444 ]
C-0-#000055 -> [Connection: keep-alive ]
C-0-#000079 -> [User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_7_4) AppleWebKit/536.11 (KHTML, like Gecko) Chrome/20.0.1132.57 Safari/536.11 ]
C-0-#000212 -> [Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8 ]
C-0-#000285 -> [Accept-Encoding: gzip,deflate,sdch ]
C-0-#000321 -> [Accept-Language: en-US,en;q=0.8 ]
C-0-#000354 -> [Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.3 ]
C-0-#000402 -> [Cookie: login-token=179ba6bd-e0a7-4909-a965-e11c7f2bc2fc%3a618bd8a8-fbaf-43c5-827d-c84c62248c5e_22ee860cc9036fee%3acrx.default%3b21148fb0-eb6c]
C-0-#000543 -> [-43c9-a2b9-c8d40618d8ae%3ad87a3d1a-5e9a-4d5a-bab1-0ee60ad6d8df_d0e4ddce0fcd84b6%3acrx.default%3b5cb95227-ea51-47bf-850b-68ad1dfd7297%3af3bbb6]
C-0-#000684 -> [59-7913-4285-8857-832c087bafd5_c484727d3b3665ad%3acrx.default; ys-cq-siteadmin-tree=o%3Awidth%3Dn%253A240%5EselectedPath%3Ds%253A/content ]
C-0-#000824 -> [ ]
```

De AEM instantie reageert met de inhoud van het bestand `test.html`:

```shell
S-0-#000000 -> [HTTP/1.1 200 OK ]
S-0-#000017 -> [Connection: Keep-Alive ]
S-0-#000041 -> [Server: Day-Servlet-Engine/4.1.24  ]
S-0-#000077 -> [Content-Type: text/html;charset=utf-8 ]
S-0-#000116 -> [Content-Length: 104 ]
S-0-#000137 -> [Date: Mon, 16 Jul 2012 11:23:38 GMT ]
S-0-#000174 -> [Last-Modified: Mon, 16 Jul 2012 11:19:27 GMT ]
S-0-#000220 -> [ ]
S-0-#000222 -> [<html>]
S-0-#000229 -> [<head>]
S-0-#000236 -> [    <title>Test</title>]
S-0-#000260 -> [</head> ]
S-0-#000269 -> [<body>]
S-0-#000276 -> [ Test<br>]
S-0-#000286 -> [    <img src="test.jpg">]
S-0-#000311 -> [</body>]
S-0-#000319 -> [</html>]
```

### Gebruikt proxyserver {#uses-of-the-proxy-server}

De volgende scenario&#39;s illustreren een paar van de doeleinden waarvoor de Server van de Volmacht kan worden gebruikt:

**Controleren op cookies en de bijbehorende waarden**

In het volgende voorbeeld van een logbestandvermelding worden alle cookies en hun waarden weergegeven die door de client worden verzonden via de zesde verbinding die is geopend sinds de proxy is gestart:

`C-6-#000635 -> [Cookie: cq3session=7e39bc51-ac72-3f48-88a9-ed80dbac0693; Show=ShowMode; JSESSIONID=68d78874-cabf-9444-84a4-538d43f5064d ]`

**Controleren op kopteksten en hun waarden**

In het volgende voorbeeld van een logbestandvermelding wordt getoond dat de server in staat is een verbinding te maken waarbij de inhoud in leven blijft en dat de header van de lengte van de inhoud juist is ingesteld:

```
S-7-#000017 -> [Connection: Keep-Alive ]
 ...
 S-7-#000107 -> [Content-Length: 124 ]
```

**Controleren of Keep-Alive werkt**

Levend is een eigenschap van HTTP die een cliënt toestaat om de verbinding van TCP aan de server opnieuw te gebruiken om veelvoudige verzoeken (voor de paginacode, beelden, stijlbladen, etc.) te maken. Zonder houden-levend, moet de cliënt een nieuwe verbinding voor elk verzoek vestigen.

Controleren of in leven houden werkt:

* Start de proxyserver.
* Vraag een pagina aan.
* Als houden-levend werkt, zou de verbindenteller nooit boven 5 tot 10 verbindingen moeten gaan.
* Als houden-levend niet werkt, stijgt de verbindenteller snel.

**Verzoeken om verlies zoeken**

Als u verzoeken verliest in een complexe serverinstelling, bijvoorbeeld met een firewall en een Dispatcher, kunt u de proxyserver gebruiken om te achterhalen waar de aanvraag is verloren. Als er een firewall is:

* Een proxy starten voor een firewall
* Een andere proxy starten na een firewall
* Gebruik deze om te zien hoe ver de verzoeken krijgen.

**Verzoeken wijzigen**

Als u van tijd tot tijd hangende verzoeken ervaart:

* Start de proxy.
* Wacht of schrijf het toegangslogboek in een dossier met elke ingang die een timestamp heeft.
* Wanneer het verzoek begint te hangen, kunt u zien hoeveel verbindingen open waren en welk verzoek problemen veroorzaakt.
