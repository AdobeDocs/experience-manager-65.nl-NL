---
title: Problemen oplossen
seo-title: Problemen oplossen
description: In dit artikel worden enkele installatieproblemen besproken die mogelijk optreden bij AEM.
seo-description: In dit artikel worden enkele installatieproblemen besproken die mogelijk optreden bij AEM.
uuid: 2ca898c3-b074-4ccd-a383-b92f226e6c14
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
discoiquuid: 5542de4e-6262-4300-9cf8-0eac79ba4f9a
translation-type: tm+mt
source-git-commit: 80b8571bf745b9e7d22d7d858cff9c62e9f8ed1e
workflow-type: tm+mt
source-wordcount: '1126'
ht-degree: 0%

---


# Problemen oplossen{#troubleshooting}

Deze sectie omvat gedetailleerde informatie over logboeken beschikbaar om u te helpen problemen oplossen en omvat ook informatie over enkele problemen u met AEM zou kunnen ontmoeten.

## De prestaties van auteurs oplossen {#troubleshoot-author-performance}

Het analyseren van langzame prestaties op Authoring instantie kan vrij complex worden. Als eerste stap is het vereist om te achterhalen op welk niveau van de technologiestapel de prestaties verminderen.

De volgende beslisboom verstrekt raad om het knelpunt te versmallen.

![chlimage_1-75](assets/chlimage_1-75.png)

## Basisoptimalisatie {#basic-optimization}

![chlimage_1-76](assets/chlimage_1-76.png)

## Logbestanden en auditlogbestanden configureren {#configuring-log-files-and-audit-logs}

AEM registreert gedetailleerde logboeken die u zou kunnen willen vormen om installatiekwesties problemen op te lossen. Zie het gedeelte [Werken met auditrecords en logbestanden](/help/sites-deploying/monitoring-and-maintaining.md#working-with-audit-records-and-log-files) voor meer informatie.

## De optie Uitvouwen gebruiken {#using-the-verbose-option}

Wanneer u AEM WCM begint, kunt u - v (verbose) optie aan de bevellijn toevoegen zoals in: java -jar cq-wcm-quickstart-&lt;version>.jar-v.

De verbose optie toont sommige van de het logboekoutput van Quickstart op de console, zodat kan het voor het oplossen van problemen worden gebruikt.

## Algemene installatieproblemen {#common-installation-issues}

In de volgende sectie worden enkele installatieproblemen en de bijbehorende oplossingen beschreven.

### Als u dubbelklikt op de Quickstart-jar, heeft dit geen effect en wordt het jar-bestand geopend met een ander programma (bijvoorbeeld archiefbeheer) {#double-clicking-the-quickstart-jar-does-not-have-any-effect-or-opens-the-jar-file-with-another-program-for-example-archive-manager}

Dit geeft meestal een probleem aan met de manier waarop de bureaubladomgeving van het besturingssysteem is geconfigureerd voor het openen van bestanden met de extensie .jar. Het kan ook aangeven dat u Java niet hebt geïnstalleerd of dat u een niet-ondersteunde versie van Java gebruikt.

Aangezien de jar dossiers het overal formaat van het ZIP gebruiken, kunnen sommige archiveringsprogramma&#39;s automatisch de Desktop vormen om jar dossiers als archiefdossiers te openen.

Ga als volgt te werk om problemen op te lossen:

* Controleer of u ten minste Java versie 1.6 hebt geïnstalleerd.
* Probeer een contextmenu (gewoonlijk klik met de rechtermuisknop) op AEM WCM QuickStart, en selecteer &quot;Open met....&quot;
* Controleer of Java of Sun Java wordt vermeld en probeer er AEM WCM mee uit te voeren. Als u meerdere Java-versies hebt geïnstalleerd, selecteert u de ondersteunde versie.

   Als deze stap is geslaagd en uw besturingssystemen de optie hebben om altijd het geselecteerde programma te gebruiken om de .jar-bestanden uit te voeren, selecteert u deze optie. Dubbelklikken moet vanaf nu werken.

* Soms kunt u de juiste koppeling herstellen door de ondersteunde Java-versie opnieuw te installeren.
* U kunt CRX altijd uitvoeren met behulp van de opdrachtregel of start/stop-scripts zoals eerder in dit document is beschreven.

### Mijn toepassing die op CRX loopt werpt fouten uit het geheugen {#my-application-running-on-crx-throws-out-of-memory-errors}

>[!NOTE]
>
>Zie ook [Geheugenproblemen](https://helpx.adobe.com/experience-manager/kb/AnalyzeMemoryProblems.html)analyseren.


CRX heeft zelf een zeer laag geheugenverbruik. Als de toepassing die binnen CRX wordt uitgevoerd grotere geheugenvereisten heeft of om geheugen-zware verrichtingen (bijvoorbeeld, grote transacties) verzoekt, moet de JVM instantie waar CRX looppas met aangewezen geheugenmontages worden begonnen.

Gebruik de Java-opdrachtopties om geheugeninstellingen van de JVM te definiëren (bijvoorbeeld java -Xmx512m -jar crx&amp;ast;.jar om de heapsize in te stellen op 512MB).

Geef de optie voor het instellen van het geheugen op terwijl u AEM WCM start vanaf de opdrachtregel. De AEM WCM start/stop manuscripten of de douanescripten voor het beheren van AEM opstarten WCM kunnen ook worden gewijzigd om de vereiste geheugenmontages te bepalen.

Als u reeds uw heapsize aan 512MB hebt bepaald, kunt u de geheugenkwestie verder willen analyseren door een heapstortplaats te creëren:

Als u automatisch een heapdump wilt maken wanneer er onvoldoende geheugen beschikbaar is, gebruikt u de volgende opdracht:

java -Xmx256m -XX:+HeapDumpOnOutOfMemoryError -jar&amp;ast;.jar

Hiermee wordt een heap-dump-bestand gegenereerd (**java_..hprof**) wanneer er onvoldoende geheugen beschikbaar is voor het proces. Het proces kan blijven lopen nadat de heapstortplaats werd geproduceerd. Gewoonlijk is één heap-dump-bestand voldoende om het probleem te analyseren.

### Het welkomstscherm AEM wordt niet weergegeven in de browser nadat u hebt dubbelgeklikt op AEM QuickStart {#the-aem-welcome-screen-does-not-display-in-the-browser-after-double-clicking-aem-quickstart}

In bepaalde situaties worden de AEM WCM-welkomstschermen niet automatisch weergegeven, ook al is de gegevensopslagruimte zelf in orde. Dit kan afhangen van de instelling van het besturingssysteem, de configuratie van de browser of vergelijkbare factoren.

Het gebruikelijke symptoom is dat het venster AEM WCM QuickStart &quot;AEM WCM opstarten, wachten op het opstarten van de server....&quot; Als dat bericht relatief lang wordt weergegeven, voert u de AEM WCM-URL handmatig in in het browservenster met de standaard 4502-poort of de poort waarop de instantie wordt uitgevoerd: http://localhost:4502/.

Bovendien kunnen logboeken de reden onthullen waarom de browser niet is gestart.

Soms heeft het AEM WCM QuickStart-venster het bericht &quot;AEM WCM wordt uitgevoerd op http://localhost:port/&quot; en wordt de browser niet automatisch gestart. Klik in dit geval op de URL in het venster AEM WCM QuickStart (het is een hyperlink) of voer de URL handmatig in de browser in.

Als alles anders ontbreekt, controleer de logboeken om te weten te komen wat is gebeurd.

## Installaties met een toepassingsserver oplossen {#troubleshooting-installations-with-an-application-server}

### Pagina niet gevonden bij aanvragen van een geometrixx-buitenpagina {#page-not-found-returned-when-requesting-a-geometrixx-outdoor-page}

**Is van toepassing op WebLogic 10.3.5 en JBoss 5.1**

Wanneer een verzoek aan geometrixx-outdoor/en pagina een 404 (Pagina niet Fouten) terugkeert, kunt u opnieuw controleren dat u het extra het hellen bezit in het sling.properties- dossier nodig voor deze specifieke Servers van de Toepassing hebt geplaatst.

Zie in de stappen *Implementeren AEM webtoepassing* voor meer informatie.

### De grootte van de reactiekop kan groter zijn dan 4Kb {#response-header-size-can-be-greater-than-kb}

502 fouten kunnen erop wijzen dat de Webserver niet de grootte van de AEM HTTP- reactiekop kan behandelen. AEM kunnen HTTP-antwoordheaders genereren die cookies van meer dan 4 kB bevatten. Zorg ervoor dat uw servletcontainer wordt gevormd zodat de maximumgrootte van de reactiekop 4kb kan overschrijden.

Voor Tomcat 7.0, bijvoorbeeld, controleert het maxHttpHeaderSize attribuut van de [Schakelaar](https://tomcat.apache.org/tomcat-7.0-doc/config/http.html) van HTTP beperkingen op kopbalgrootte.

## Adobe Experience Manager verwijderen {#uninstalling-adobe-experience-manager}

Aangezien AEM in één map installeert, is een hulpprogramma voor verwijderen niet nodig. Het verwijderen van de installatiemap kan eenvoudig zijn, maar hoe u de installatiemap verwijdert, hangt AEM af van wat u wilt bereiken en van welke permanente opslag u gebruikt.

Als permanente opslag is ingesloten in de installatiemap, bijvoorbeeld in de standaard-TarPM-installatie, worden bij het verwijderen van mappen ook gegevens verwijderd.

>[!NOTE]
>
>Adobe raadt u ten zeerste aan een back-up van de opslagplaats te maken voordat u AEM verwijdert. Als u de gehele &lt;cq-installation-directory> verwijdert, verwijdert u de opslagplaats. Als u de gegevens in de opslagplaats wilt bewaren voordat u de map &lt;cq-installation-directory>/crx-quickstart/repository verwijdert, verplaatst of kopieert u deze naar een andere locatie voordat u de andere mappen verwijdert.

Als bij de installatie van AEM externe opslag wordt gebruikt, bijvoorbeeld een databaseserver, worden de gegevens niet automatisch verwijderd wanneer u een map verwijdert. De opslagconfiguratie wordt echter wel verwijderd, waardoor het herstellen van de JCR-inhoud moeilijk wordt.

### JSP-bestanden worden niet gecompileerd op JBoss {#jsp-files-are-not-compiled-on-jboss}

Als u JSP dossiers installeert of aan Experience Manager op JBoss bijwerkt en de overeenkomstige servlets niet worden gecompileerd, zorg ervoor de JBoss JSP compiler correct wordt gevormd. Raadpleeg het[JSP Compilation Issues in het JBoss](https://helpx.adobe.com/experience-manager/kb/jsps-dont-compile-jboss.html) -artikel voor meer informatie.
