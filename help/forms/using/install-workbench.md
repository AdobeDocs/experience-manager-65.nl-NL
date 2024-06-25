---
title: Workbench installeren
description: Leer hoe u AEM Forms Workbench kunt installeren, verwijderen, configureren, beheren of implementeren.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
role: Admin, User, Developer
exl-id: d530dbb9-f95e-4329-9665-37faf8f7931b
solution: Experience Manager, Experience Manager Forms
feature: Workbench,Adaptive Forms
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '2184'
ht-degree: 0%

---

# Workbench installeren {#install-workbench}

Dit document bevat instructies voor het installeren en configureren van AEM Forms Workbench. Het installatieprogramma installeert ook Forms Designer.

## Wie moet dit document lezen? {#who-should-read-this-doc}

Dit document is bedoeld voor beheerders of ontwikkelaars die verantwoordelijk zijn voor het installeren, configureren, beheren of implementeren van Workbench. Hier vindt u ook informatie over het configureren van uw systeem ter ondersteuning van uw geüpgrade AEM Forms-processen. De verstrekte informatie is gebaseerd op de veronderstelling dat iedereen die dit document leest vertrouwd is met het Microsoft® Windows® besturingssysteem.

## Aanvullende informatie {#additional-information}

De bronnen in deze tabel kunnen u helpen meer te weten te komen over en aan de slag te gaan met AEM Forms.
<table>
 <tbody>
  <tr>
   <td><p><strong>Voor informatie over</strong></p> </td>
   <td><p><strong>Zie</strong></p> </td>
  </tr>
  <tr>
   <td><p>Procedurele informatie voor Workbench</p> </td>
   <td><p><a href="https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/WorkbenchHelp.pdf">Workbench Help</a><br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Algemene informatie over AEM Forms en de wijze waarop het geïntegreerd is met andere Adobe producten</p> </td>
   <td><p><a href="https://experienceleague.adobe.com/docs/experience-manager-65/forms/getting-started/introduction-aem-forms.html?lang=en">AEM Forms - Overzicht</a><br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Alle documentatie die beschikbaar is voor AEM Forms</p> </td>
   <td><p><a href="https://experienceleague.adobe.com/docs/experience-manager-65/forms/getting-started/introduction-aem-forms.html?lang=en">AEM Forms-documentatie</a><br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Reparatie-updates, technische notities en aanvullende informatie over deze productversie</p> </td>
   <td><p>Contact opnemen met Adobe Enterprise Support</a><br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>De Flex Workspace is verouderd voor AEM Forms. Deze is beschikbaar voor de AEM Forms-release.

## Voordat u gaat installeren {#before-you-install}

### Overzicht van Workbench-installatie {#workbench-installation-overview}

Workbench is een geïntegreerde ontwikkelomgeving (IDE) die ontwikkelaars en auteurs van formulieren gebruiken om geautomatiseerde bedrijfsprocessen en formulieren te maken. Het wordt ook gebruikt om de middelen en de diensten te beheren die de processen en de vormen gebruiken.

In de volgende afbeelding ziet u de Workbench-installatie, inclusief:
* Procesontwerp met Workbench
* Formulierontwerp met Designer

>[!NOTE]
>
>Voor de AEM Forms-server is een afzonderlijk installatieprogramma vereist. Raadpleeg de documentatie bij de installatie van AEM Forms on JEE voor meer informatie.

![default-render-vorm](assets/installing-workbench.png)

## Systeemvereisten {#system-prerequisites}

In deze sectie worden de hardware- en softwarevereisten en ondersteunde platforms beschreven.

### Minimale hardware- en softwarevereisten {#minimum-hardware-software-requirements}

**Workbench**
De volgende minimale vereisten worden aanbevolen: schijfruimte voor installatie:
* 680 MB alleen voor Workbench.
* 2,15 GB op één station voor een volledige installatie van Workbench, Designer en de samplingverzameling.
* 400 MB voor tijdelijke installatiemappen - 200 MB in de gebruiker \ temp folder en 200 MB in de tijdelijke folder van Vensters.

>[!NOTE]
>
>Als al deze locaties zich op één station bevinden, moet er tijdens de installatie 1,5 GB aan ruimte beschikbaar zijn. De naar de tijdelijke mappen gekopieerde bestanden worden verwijderd wanneer de installatie is voltooid.

* Hardwarevereisten: Intel® Pentium® 4- of AMD®-equivalent, 1-GHz processor.
* Java™ Runtime Environment (JRE) 7.0 werkt 51 of hoger bij naar 7.0.
* Minimaal 1024 x 768 pixels of meer bij een monitorresolutie van 16 bits of hoger.
* TCP/IPv4- of TCP/IPv6-netwerkverbinding met de AEM Forms Server.
* Installeer Visuele C++ Redistributable runtime Pakketten 2012 met 32 bits.
* Installeer Visuele C++ Redistributable runtime Pakketten 2013 met 32 bits.

>[!NOTE]
>
>U moet over beheerdersrechten beschikken om Workbench te installeren. Als u een niet-beheerdersaccount installeert, vraagt het installatieprogramma u om de referenties voor een geschikte account.

### Ondersteunde platforms {#supported-platforms}

Zie de volledige lijst met ondersteunde platforms voor Workbench op [Door AEM Forms ondersteunde platforms](https://www.adobe.com/go/learn_aemforms_supportedplatforms_65).

## Designer-installatieoverwegingen {#designer-installation-considerations}

Standaard bevat de Workbench-installatie een overeenkomende Engels-enige versie van Designer. Als de Workbench-installatietoepassing een bestaande versie van Designer op uw computer detecteert, wordt de installatie mogelijk beëindigd en moet u de huidige versie van Designer verwijderen voordat u kunt doorgaan.
De onderstaande tabel bevat een volledige lijst met mogelijke Designer-installatiescenario&#39;s die u kunt tegenkomen en alle handelingen die u moet uitvoeren bij de installatie van Workbench.

<table>
 <tbody>
  <tr>
   <td><p><strong>Versie van Designer is momenteel geïnstalleerd</strong></p> </td>
   <td><p><strong>Vereiste acties</strong></p> </td>
  </tr>
  <tr>
   <td><p>Acrobat Pro of Acrobat Pro Extended (omvat Designer)</p> </td>
   <td><p>Geen.<br /> 
Met de Workbench-installatie wordt een exemplaar van Designer op uw computer gedetecteerd dat met Acrobat Pro of Acrobat Pro Extended is geïnstalleerd.<br />
Verschillende versies van Designer kunnen op hetzelfde systeem naast elkaar bestaan, bijvoorbeeld Designer 6.4.x voor Workbench 6.4 en Designer 6.5.0.x voor Workbench 6.5. U hoeft de versie van Designer die met Acrobat 10 Pro of Acrobat 10 Pro Extended of hoger is geïnstalleerd, niet te verwijderen.
<br /></p> </td>
  </tr>
  <tr>
   <td><p>Designer (zelfstandig)</p> </td>
   <td><p>Geen. <br />De versie van Designer die bij Workbench wordt geleverd, is alleen Engelstalig. <br />Het Workbench-installatieprogramma installeert geen nieuwe versie van Designer. In plaats daarvan wordt een bijgewerkte versie, die wordt meegeleverd bij het Workbench-installatieprogramma, patcheerd. Zo kunt u ook uw gelokaliseerde versie van Designer gebruiken in Workbench.<br /> </p> </td>
  </tr>
 </tbody>
</table>

### Designer (zelfstandig) verwijderen op Windows 10 {#uninstall-designer-standalone-windows10}

1. Ga naar **Control Panel > Programs > Programs and Features**
1. Selecteer in de lijst Momenteel geïnstalleerde programma&#39;s de optie **Adobe Designer**.
1. Klikken **Verwijderen** en klik vervolgens op **Ja**.

## Workbench installeren {#installing-workbench}

In dit hoofdstuk wordt beschreven hoe u Workbench kunt installeren.

### Workbench installeren en uitvoeren {#installing-and-running-workbench}

Voordat u Workbench installeert, moet u ervoor zorgen dat uw omgeving de vereiste software en hardware bevat om het uit te voeren (zie sectie: **Voordat u gaat installeren**).

**Workbench installeren en uitvoeren:**

1. Voer een van de volgende taken uit:
   * Navigeer naar de map \workbench op de installatiemedia en dubbelklik op het bestand run_windows_installer.bat.
   * Download de Workbench en pak deze uit naar uw bestandssysteem. Blader nadat u het bestand hebt gedownload naar de map \workbench en dubbelklik op het bestand run_windows_installer.bat.

   >[!IMPORTANT]
   >
   >Het Workbench-installatieprogramma wordt alleen uitgevoerd vanaf een lokaal station. Deze kan niet vanaf een externe site worden uitgevoerd.

   >[!NOTE]
   >
   >Als er een fout optreedt &quot;Kan de Java™ Virtual Machine niet maken&quot;, maakt u een omgevingsvariabele met de naam _JAVA_OPTIONS met de waarde -Xmx512M en voert u het installatieprogramma uit.

1. Klik in het scherm Introductie op Volgende.
1. Lees de licentieovereenkomst voor producten, selecteer Ik accepteer de voorwaarden van de licentieovereenkomst en klik op Volgende.
1. (Optioneel) Selecteer Adobe Designer installeren als u dit gereedschap nodig hebt om formulieren te maken en te wijzigen.

   >[!NOTE]
   >
   >U kunt Designer die met Acrobat 10 is geïnstalleerd, blijven gebruiken door deze optie uit te schakelen.

1. Accepteer de standaardmap zoals deze wordt weergegeven of klik op Kiezen en navigeer naar de map waarin u Workbench wilt installeren. Klik vervolgens op Volgende.

   >[!NOTE]
   >
   >Het pad naar de installatiemap mag geen # (pound)- en $ (dollar)-tekens bevatten.

1. Controleer het overzicht van de voorinstallatie en klik op Installeren. In het installatieprogramma wordt de voortgang van de installatie weergegeven.
1. Controleer het installatieoverzicht. Selecteer AEM Forms Workbench starten als u Workbench wilt starten en klik vervolgens op Volgende.
1. Controleer de opmerkingen bij de release en klik op Gereed.
1. De volgende items zijn nu op uw computer geïnstalleerd:
   * **Workbench**: Als u Workbench wilt uitvoeren vanuit het menu Start, selecteert u Alle programma&#39;s > AEM Forms > Workbench als u de sneltoetsmap daar wilt opslaan. Zie voor meer informatie de <a href="https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/WorkbenchHelp.pdf">Workbench gebruiken</a> documentatie.
   * **Designer**: U kunt Designer openen vanuit Workbench. Zie Aan de slag-onderwerp in <a href="https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/using-designer.pdf">Designer Help</a>.
   * **AEM FORMS SDK**: Zie voor meer informatie over het gebruik van de SDK <a href="https://helpx.adobe.com/pdf/aem-forms/6-3/programming-with-aem-forms.pdf">Programmeren met AEM Forms</a>.

## Processen upgraden {#upgrading-processes}

AEM Forms on JEE-processen kunnen worden geüpgraded naar AEM Forms-toepassingen met de wizard Upgrade. Zie Informatie over verouderde artefacten bijwerken in Workbench Help voor meer informatie.

### Aanmelden bij een server configureren {#configuring-and-logging-server}

Als u Workbench wilt gebruiken, moet u een AEM Forms-exemplaar uitvoeren, meestal op een aparte computer. U moet een gebruikersnaam en wachtwoord hebben om u aan te melden bij AEM Forms, en gegevens over de locatie van de server.

>[!NOTE]
>
>Als u AEM Forms hebt geconfigureerd voor gebruik van de EMC Documentum® of IBM® FileNet Repository Provider en u zich wilt aanmelden bij een andere opslagplaats dan de opslagplaats die in AEM beheerconsole voor formulieren als standaard is geconfigureerd, geeft u de gebruikersnaam op als username@Repository.

### Instellingen voor time-out configureren {#configuring-timeout-settings}

Workbench is na twee uur standaard uitgevallen, ongeacht de activiteit of inactiviteit. Als u de time-outinstelling wilt bewerken, raadpleegt u &quot;Gebruikersbeheer configureren > Geavanceerde systeemkenmerken configureren&quot; in het dialoogvenster <a href="https://experienceleague.adobe.com/docs/experience-manager-65/forms/administrator-help/configure-user-management/configure-advanced-system-attributes.html">Help bij beheerconsole</a>.

### Workbench configureren voor verbinding via HTTPS {#configuring-workbench-to-connect-over-HTTPS}

Als u Workbench via HTTPS wilt verbinden met een AEM Forms-server, moet u ervoor zorgen dat de certificeringsinstantie (CA) die de openbare sleutel heeft uitgegeven, wordt herkend als vertrouwd door Workbench. Als het certificaat niet wordt herkend als afkomstig van een vertrouwde bron, moet u het controlebestand bijwerken in het dialoogvenster [Workbench_HOME]/workbench/jre/lib/security directory.

>[!NOTE]
>
>[Workbench_HOME] vertegenwoordigt de map waarin u Workbench hebt geïnstalleerd. De standaardlocatie is C:\Program Files (x86)\Adobe Experience Manager forms Workbench.

Zorg ervoor dat u verbinding maakt met HTTPS door de naam te gebruiken die in het certificaat is opgegeven. Deze naam is doorgaans de volledig gekwalificeerde hostnaam.

**Het cacert-bestand bijwerken**:
1. Zorg ervoor dat u een kopie van het SSL-certificaat (Secure Sockets Layer) hebt. Neem contact op met de beheerder die de SSL-server heeft geconfigureerd of exporteer het certificaat via een webbrowser.

   >[!NOTE]
   >
   >Als u het certificaat wilt exporteren, opent u een webbrowser en meldt u zich aan bij beheerconsole. Installeer het certificaat in de browser en exporteer het certificaat vanuit de browser naar een tijdelijke opslaglocatie (of rechtstreeks naar de [Workbench_HOME]/workbench/jre/lib/security directory).

1. Het certificaat kopiëren naar de [Workbench_HOME]/workbench/jre/lib/security directory.

1. Een opdrachtpromptvenster openen, naar [Workbench_HOME]/workbench/jre/bin, en typ dan het volgende bevel:
   `keytool -import -storepass changeit -file [Workbench_HOME]\workbench\jre\lib\security\ssl_cert_for_certname.cer -keystore [Workbench_HOME]\workbench\jre\lib\security\cacerts -alias example`
Waarbij:
   * `changeit` is het standaardwachtwoord voor het sleutelarchief van het cacerts.
   * certname is het certificaat dat u hebt geselecteerd in stap 1.
   * Dit is bijvoorbeeld de alias die u kiest voor het certificaat. Deze waarde kan worden gewijzigd.

1. Wanneer u wordt gevraagd het certificaat te vertrouwen, typt u Ja en klikt u op Enter. Het keytool gaat door met het importeren van het cacartbestand in de [Workbench_HOME]/workbench/jre/lib/security directory.

1. Sluit en herstart Workbench om wijzigingen toe te passen.

### Cacheinstellingen configureren voor dynamisch gegenereerde sjablonen {#configuring-cache-settings-for-dynamically-generated-templates}

De volgende aspecten van cachebewerkingen moeten in overweging worden genomen als uw toepassing direct unieke sjablonen genereert door XFA-inhoud automatisch bij te werken. In feite gebruikt elke transactie een nieuwe, unieke sjabloon.

Wanneer de de vormengenerator of output naar, of updates, ingangen in het geheime voorgeheugen voor een specifiek vormmalplaatje zoekt, gebruikt het verscheidene zeer belangrijke waarden om van de specifieke geheim voorgeheugeningang de plaats te bepalen die wordt betreden.

* **Naam sjabloonbestand**: De locatie en bestandsnaam van de sjabloon die wordt gebruikt als de primaire unieke id van het formulier in de cache.
* **Tijdstempel**: Het sjabloonbestand bevat een tijdstempel waarmee de laatste updatetijd van het formulier wordt bepaald.
* **SjabloonUID**: Designer voegt in elke sjabloon een unieke id (UUID) voor het formulier en de versie ervan in. Telkens wanneer het formulier wordt bijgewerkt, wordt de ingesloten UUID bijgewerkt. Een XDP-sjabloon kan bijvoorbeeld de volgende inhoud weergeven:

  `<?xml version="1.0" encoding="UTF-8"?>`
  `<?xfa generator="AdobeAEM formsDesignerES_V8.2" APIVersion="2.6.7185.0"?><xdp:xdp xmlns:xdp=https://ns.adobe.com/xdp/ timeStamp="2008-07-29T21:22:12Z" uuid="823e538f-ff6c-4961-b759-f7626978a223"><template xmlns="https://www.xfa.org/schema/xfa-template/2.6/">`

* **Renderopties**: In de weergegeven formuliercache wordt de inhoud van de cache afzonderlijk opgeslagen voor elke set unieke renderopties.


De Forms-service ontvangt sjablonen op basis van de bestandsnaam of de locatie in de opslagplaats, of op basis van de waarde als een XML-object in het geheugen.

* **Door verwijzing doorgegeven sjablonen**: Hiermee gebruikt u de hoofdmap van de inhoud en de naam van het formulier. Als unieke sjablonen met verschillende bestandsnamen in elke aanvraag worden doorgegeven met deze methode, groeit de schijfcache eindeloos en wordt deze nooit opnieuw gebruikt. Om dit te voorkomen, zouden de unieke malplaatjes met zelfde filename moeten worden overgegaan om ervoor te zorgen dat het zelfde geheime voorgeheugen voor alle verzoeken wordt bijgewerkt.
* **Sjablonen doorgegeven via waarde**: Gebruikt sjabloonbytes die samen met de gegevens worden doorgegeven met de parameter theinDataDoc. Als unieke sjablonen met verschillende UUID met deze methode worden doorgegeven, wordt de schijfcache eindeloos groter en wordt deze nooit opnieuw gebruikt. Om dit te verhinderen, zou het attribuut UUID van alle malplaatjes moeten worden gestript om ervoor te zorgen dat geen geheim voorgeheugen voor het malplaatje wordt gecreeerd. Als u dezelfde UUID doorgeeft die niet gelijk is aan null, kunnen de cacheobjecten worden gemaakt, maar wordt gegarandeerd dat dezelfde cache bij elke aanvraag wordt bijgewerkt.

Als u wilt voorkomen dat de cache eindeloos groeit, moet u rekening houden met de volgende factoren voor het renderen van dynamisch gegenereerde sjablonen met de nieuwe AEM Forms API&#39;s: renderHTMLForm2 en renderPDFForm2.

Wanneer u de nieuwe API&#39;s gebruikt, wordt de sjabloon doorgegeven als een documentobject, dat wordt afgehandeld in de Forms-service op basis van het feit of de sjabloon al dan niet is gepassioneerd.

Houd rekening met de volgende aspecten van gepassiveerde documenten waarin de UUID en de inhoudswortel fungeren als de cachemoets:

* De cache wordt niet gemaakt voor gepassiveerde invoersjablonen zonder UUID.
* Als meer dan één gepassioneerde inputmalplaatje met de zelfde UUID en inhoudswortel worden overgegaan, dan wordt het zelfde geheime voorgeheugen overschreven.

Houd rekening met het volgende voor niet-gepassiveerde documenten waarbij de bestandsnaam en de hoofdmap van de inhoud als cachesleutel fungeren:

* Voor niet-gepassiveerde invoersjablonen is het in cache plaatsen afhankelijk van de hoofdmap en bestandsnaam van de inhoud waaruit het document is gegenereerd.
Hetzelfde cachegeheugen wordt alleen gebruikt voor aanvragen met dezelfde hoofdmap en naam van het sjabloon.
De volgende beste praktijken zorgen ervoor dat het geheime voorgeheugen niet eindeloos groeit wanneer dynamisch geproduceerde malplaatjes worden overgegaan tot de dienst van Forms:
   * Strip UUID of ga zelfde UUID in alle dynamisch geproduceerde malplaatjes over.
   * Genereer het document op basis van sjabloonbytes of op basis van dezelfde bestandsnaam op de schijf.

### Workbench verwijderen {#uninstalling-workbench}

Gebruik de functie Software in het Configuratiescherm om het verwijderprogramma te starten. De Workbench- en Designer-toepassingen hebben aparte verwijderingsprogramma&#39;s.

## AEM Forms XDC Editor configureren {#configuring-aem-forms-xdc-editor}

Met behulp van de XDC Editor kunnen netwerkprinterbeheerders XDC-bestanden (XML Forms Architecture Device Configuration) maken en wijzigen. XDC-bestanden beschrijven de mogelijkheden van printers, zoals de printertaal of de correlatie tussen papierformaat en ladelocatie.

Voordat uw beheerder van de netwerkprinter de XDC Editor gebruikt, verplaatst u de voorbeeld-XDC-bestanden en raadpleegt u Apparaatprofielen maken met de XDC Editor.

**De voorbeeld-XDC-bestanden ophalen**:

1. Zoek op de AEM Forms-server de XDC-map op in [AEM Forms root]\sdk\samples\Output\IVS.
1. Kopieer de inhoud van deze map naar een map die toegankelijk is via het Workbench- of Eclipse-systeem.

**Om de XDC Editor Help te verkrijgen**:

1. Ga naar de AEM Forms documentatiewebsite.
1. Klik op de knop **Ontwikkelen** en navigeer naar Apparaatprofielen maken met XDC Editor. Download het bestand xdc_editor_help_web.zip en installeer de Help-bestanden aan de hand van de instructies in het bestand Readme.
