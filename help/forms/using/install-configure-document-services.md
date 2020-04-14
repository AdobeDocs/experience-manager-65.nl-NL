---
title: Documentservices installeren en configureren
seo-title: Documentservices installeren en configureren
description: Installeer AEM Forms-documentservices om PDF-documenten te maken, samen te stellen, te verspreiden, te archiveren, digitale handtekeningen toe te voegen om de toegang tot documenten te beperken en streepjescodes voor formulieren te decoderen.
seo-description: Installeer AEM Forms-documentservices om PDF-documenten te maken, samen te stellen, te verspreiden, te archiveren, digitale handtekeningen toe te voegen om de toegang tot documenten te beperken en streepjescodes voor formulieren te decoderen.
uuid: 908806a9-b0d4-42d3-9fe4-3eae44cf4326
topic-tags: installing
discoiquuid: b53eae8c-16ba-47e7-9421-7c33e141d268
translation-type: tm+mt
source-git-commit: 726163106ddb80600eaa7cc09b1a2e9b035a223e

---


# Documentservices installeren en configureren {#installing-and-configuring-document-services}

## Inleiding {#introduction}

AEM Forms biedt een set OSGi-services voor het uitvoeren van verschillende bewerkingen op documentniveau, zoals services voor het maken, samenstellen, distribueren en archiveren van PDF-documenten, het toevoegen van digitale handtekeningen om de toegang tot documenten te beperken en het decoderen van streepjescoderingsformulieren. Deze services zijn opgenomen in het invoegpakket voor AEM Forms. Deze services worden gezamenlijk documentservices genoemd. De lijst met beschikbare documentservices en hun belangrijkste mogelijkheden is als volgt:

Hiermee kunt u PDF- en XDP-documenten combineren, opnieuw rangschikken en vergroten en informatie over PDF-documenten verkrijgen. Het helpt ook PDF-documenten te converteren en te valideren naar PDF/A-standaard, PDF-formulieren, XML-formulieren en PDF-formulieren te converteren naar PDF/A-1b, PDF/A-2b en PDFA/A-3b. Voor meer informatie, zie de Dienst van de [Assembler](/help/forms/using/assembler-service.md).

Hiermee kunt u PDF-documenten converteren naar PostScript- of afbeeldingsbestanden (JPEG, JPEG 2000, PNG en TIFF). Zie [ConvertPDF Service](/help/forms/using/using-convertpdf-service.md)voor meer informatie.

Hiermee kunt u gegevens extraheren uit elektronische afbeeldingen van streepjescodes. De service accepteert TIFF- en PDF-bestanden die een of meer streepjescodes bevatten als invoer en extraheert de streepjescodegegevens. Zie [Barcoded Forms Service](/help/forms/using/using-barcoded-forms-service.md)voor meer informatie.

Hiermee kunt u documenten versleutelen en ontsleutelen, de functionaliteit van Adobe Reader uitbreiden met extra gebruiksrechten en digitale handtekeningen toevoegen aan uw documenten. De dienst van de Verzekering van Doc bevat drie diensten: handtekening, versleuteling en reader-extensie. Zie [DocAssurance Service](/help/forms/using/overview-aem-document-services.md)voor meer informatie.

Hiermee kunt u documenten versleutelen en ontsleutelen. Wanneer een document wordt versleuteld, wordt de inhoud ervan onleesbaar. Een geautoriseerde gebruiker kan het document decoderen om toegang tot de inhoud te krijgen. Zie [Coderingsservice](/help/forms/using/overview-aem-document-services.md#p-encryption-service-p)voor meer informatie.

Hiermee kunt u interactieve toepassingen voor het vastleggen van gegevens maken die formulieren valideren, verwerken, transformeren en leveren die normaal gesproken in Forms Designer worden gemaakt. Met de service Forms kunt u elk formulierontwerp dat u ontwikkelt naar PDF-documenten renderen. Zie [Formulierservice](/help/forms/using/forms-service.md)voor meer informatie.

Hiermee kunt u documenten in verschillende indelingen maken, zoals PDF, laserprinterindelingen en labelprinterindelingen. Indelingen voor laserprinters zijn PostScript en Printer Control Language (PCL). Zie [Uitvoerservice](/help/forms/using/output-service.md)voor meer informatie.

De service PDF Generator biedt API&#39;s waarmee native bestandsindelingen naar PDF kunnen worden geconverteerd. Ook wordt PDF geconverteerd naar andere bestandsindelingen en wordt de grootte van PDF-documenten geoptimaliseerd. Zie [PDF Generator Service](aem-document-services-programmatically.md#pdfgeneratorservice)voor meer informatie.

Hiermee kan uw organisatie interactieve PDF-documenten eenvoudig delen door de functionaliteit van Adobe Reader uit te breiden met extra gebruiksrechten. De service activeert functies die niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Reader, zoals het toevoegen van opmerkingen aan een document, het invullen van formulieren en het opslaan van het document. Zie [Reader Extension Service](/help/forms/using/overview-aem-document-services.md#p-reader-extension-service-p)voor meer informatie.

Hiermee kunt u werken met digitale handtekeningen en documenten op de AEM-server. De service Handtekening wordt bijvoorbeeld doorgaans in de volgende situaties gebruikt:

* De AEM-server certificeert een formulier voordat het naar een gebruiker wordt verzonden om te worden geopend met Acrobat of Adobe Reader.
* De AEM-server valideert een handtekening die aan een formulier is toegevoegd met Acrobat of Adobe Reader.
* De AEM-server ondertekent een formulier namens een openbare notaris.

De handtekeningsdienst heeft toegang tot certificaten en geloofsbrieven die in de vertrouwde opslag worden opgeslagen. Zie [Handtekeningenservice](/help/forms/using/aem-document-services-programmatically.md)voor meer informatie.

AEM Forms is een krachtig platform op bedrijfsniveau en de documentservices zijn slechts een van de mogelijkheden van AEM Forms. Voor de volledige lijst van mogelijkheden, zie [Inleiding aan Vormen](/help/forms/using/introduction-aem-forms.md)AEM.

## Implementatietopologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Over het algemeen hebt u slechts één AEM-instantie (auteur of publicatie) nodig om AEM Forms-documentservices uit te voeren. De volgende topologie wordt geadviseerd om de het documentdiensten van Vormen AEM in werking te stellen. Voor gedetailleerde informatie over topologieën, zie [Architectuur en plaatsingstopologieën voor Vormen](/help/forms/using/aem-forms-architecture-deployment.md)AEM.

![](do-not-localize/document-services.png)

>[!NOTE]
>
>Hoewel u met AEM Forms alle functies van één server kunt instellen en uitvoeren, moet u capaciteitsplanning uitvoeren, taakverdeling toepassen en specifieke servers instellen voor specifieke mogelijkheden in een productieomgeving. Als u bijvoorbeeld in een omgeving met de service PDF Generator duizenden pagina&#39;s per dag converteert en meerdere adaptieve formulieren gebruikt om gegevens vast te leggen, stelt u afzonderlijke AEM Forms-servers in voor de service PDF Generator en de mogelijkheden voor adaptieve formulieren. Het helpt optimale prestaties te bieden en de servers onafhankelijk van elkaar te schalen.

## Systeemvereisten {#system-requirements}

Voordat u begint met het installeren en configureren van AEM Forms-documentservices, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Raadpleeg de [technische vereisten](/help/sites-deploying/technical-requirements.md)voor een gedetailleerde lijst met ondersteunde hardware en software.

* Het installatiepad van de AEM-instantie bevat geen spaties.
* Er wordt een AEM-instantie uitgevoerd. In AEM-terminologie is een &quot;instantie&quot; een kopie van AEM die wordt uitgevoerd op een server in de auteur- of publicatiemodus. Over het algemeen hebt u slechts één AEM-instantie (auteur of publicatie) nodig om AEM Forms-documentservices uit te voeren:

   * **Auteur**: Een AEM-instantie die wordt gebruikt om inhoud te maken, te uploaden en te bewerken en om de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Publiceren**: Een AEM-instantie die de gepubliceerde inhoud via internet of een intern netwerk aan het publiek levert.

* Er wordt voldaan aan de geheugenvereisten. AEM Forms add-on package vereist:

   * 15 GB tijdelijke ruimte voor op Microsoft Windows gebaseerde installaties.
   * 6 GB tijdelijke ruimte voor UNIX-installaties.

* Clientsoftware die vereist is voor conversie door PDF-generator op Microsoft Windows en Linux wordt geïnstalleerd:

   * **Microsoft Windows**: Microsoft [Office](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p)of [Apache OpenOffice installeren](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p)
   * **Linux**: Apache [OpenOffice installeren](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p)

>[!NOTE]
>
>* In Microsoft Windows ondersteunt de PDF Generator WebKit, Acrobat WebCapture en FhantomJS conversieroutes voor het converteren van HTML-bestanden naar PDF-documenten.
>* Op UNIX-besturingssystemen ondersteunt de PDF Generator WebKit- en PhantomJS-conversieroutes voor het converteren van HTML-bestanden naar PDF-documenten.
>



Als u het op UNIX gebaseerde besturingssysteem gebruikt, installeert u de volgende pakketten via de installatiemedia van het desbetreffende besturingssysteem:

<table> 
 <tbody> 
  <tr> 
   <td> 
    <ul> 
     <li>uitzetten</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libxcb</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>freetype</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libXau</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li>libSM</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>zlib</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libICE</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libuuid</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li>glibc</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libXext</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>nss-softokn-freebl</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>fontconfig</li> 
    </ul> </td> 
  </tr> 
  <tr> 
   <td> 
    <ul> 
     <li>libX11</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libXrender</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libXrandr</li> 
    </ul> </td> 
   <td> 
    <ul> 
     <li>libXinerama</li> 
    </ul> </td> 
  </tr> 
 </tbody> 
</table>

* **(Alleen** PDF-generator) Installeer de 32-bits versie van bibliotheken met libcurl, libcrypto en libssl en maak de onderstaande koppelingen. De symlinks verwijzen naar de meest recente versie van de respectievelijke bibliotheken:

   * /usr/lib/libcurl.so
   * /usr/lib/libcrypto.so
   * /usr/lib/libssl.so

* **(Alleen PDF-generator)** De service PDF Generator ondersteunt WebKit en PhantomJS-routes voor het converteren van HTML-bestanden naar PDF-documenten. Om omzetting voor route PhantomJS toe te laten, installeer hieronder vermelde bibliotheken met 64 bits. Over het algemeen zijn deze bibliotheken al geïnstalleerd. Als er een bibliotheek ontbreekt, installeert u deze handmatig:

   * linux-gate.so.1
   * libz.so.1
   * libfontconfig.so.1
   * libfreetype.so.6
   * libdl.so.2
   * librt.so.1
   * libpthread.so.0
   * libstdc++.so.6
   * libm.so.6
   * libgcc_s.so.1
   * libc.so.6
   * ld-linux.so.2
   * libexpat.so.1

### Adobe Acrobat en toepassingen van derden installeren {#install-adobe-acrobat-and-third-party-applications}

Als u de PDF Generator-service gaat gebruiken om eigen bestandsindelingen zoals Microsoft Word, Microsoft Excel, Microsoft PowerPoint, OpenOffice, WordPerfect X7 en Adobe Acrobat te converteren naar PDF-documenten, moet u ervoor zorgen dat deze toepassingen zijn geïnstalleerd op de AEM Forms-server.

>[!NOTE]
>
>* Adobe Acrobat, Microsoft Word, Excel en PowerPoint zijn alleen beschikbaar voor Microsoft Windows. Als u het op UNIX-Gebaseerde werkende systeem gebruikt, installeer OpenOffice om rijke tekstdossiers en gesteunde dossiers van Microsoft Office in Pdf- documenten om te zetten.
>* Sluit alle dialoogvensters die na de installatie van Adobe Acrobat en software van derden worden weergegeven voor alle gebruikers die zijn geconfigureerd voor gebruik van de service PDF Generator.
>* Start minstens één keer alle geïnstalleerde software. Alle dialoogvensters sluiten voor alle gebruikers die zijn geconfigureerd voor gebruik van de service PDF Generator.
>



Open Microsoft Word nadat u Acrobat hebt geïnstalleerd. Klik **op het** tabblad **Acrobat op PDF** maken en converteer een .doc- of .docx-bestand dat op uw computer beschikbaar is naar een PDF-document. Als de conversie is gelukt, is AEM Forms gereed voor gebruik van Acrobat met de service PDF Generator.

### Omgevingsvariabelen instellen {#setup-environment-variables}

Omgevingsvariabelen instellen voor 32-bits en 64-bits Java Development Kit, toepassingen van derden en Adobe Acrobat. De omgevingsvariabelen moeten het absolute pad bevatten van het uitvoerbare bestand dat wordt gebruikt om de bijbehorende toepassing te starten. In de onderstaande tabel worden bijvoorbeeld de omgevingsvariabelen voor een paar toepassingen weergegeven:

<table> 
 <tbody> 
  <tr> 
   <td><p><strong>Toepassing</strong></p> </td> 
   <td><p><strong>Omgevingsvariabele</strong></p> </td> 
   <td><p><strong>Voorbeeld</strong></p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>JDK (64 bits)</strong></p> </td> 
   <td><p>JAVA_HOME</p> </td> 
   <td><p>C:\Program Files\Java\jdk1.8.0_74</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>JDK (32 bits)</strong></p> </td> 
   <td><p>JAVA_HOME_32</p> </td> 
   <td><p>C:\Program Files (x86)\Java\jdk1.8.0_74</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>Adobe Acrobat</strong></p> </td> 
   <td><p>Acrobat_PATH</p> </td> 
   <td><p>C:\Program Files (x86)\Adobe\Acrobat 2015\Acrobat\Acrobat.exe</p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>Kladblok</strong></p> </td> 
   <td><p>Kladblok_PATH</p> </td> 
   <td><p>C:\WINDOWS\notepad.exe<br /> <strong></strong></p> </td> 
  </tr> 
  <tr> 
   <td><p><strong>OpenOffice</strong></p> </td> 
   <td><p>OpenOffice_PATH</p> </td> 
   <td><p>C:\Program Files (x86)\OpenOffice.org4</p> </td> 
  </tr> 
 </tbody> 
</table>

>[!NOTE]
>
>* Alle omgevingsvariabelen en de respectieve paden zijn hoofdlettergevoelig.
>* JAVA_HOME, JAVA_HOME_32 en Acrobat_PATH (alleen Windows) zijn verplichte omgevingsvariabelen.
>* De omgevingsvariabele OpenOffice_PATH wordt ingesteld op de installatiemap in plaats van op het pad naar het uitvoerbare bestand.
>* Stel geen omgevingsvariabelen in voor Microsoft Office-toepassingen zoals Word, PowerPoint, Excel en Project, of voor AutoCAD. Als deze toepassingen op de server zijn geïnstalleerd, worden deze toepassingen automatisch gestart door de service PDF genereren.
>* Voor op UNIX-Gebaseerde platforms, installeer OpenOffice als /root. Als OpenOffice niet als hoofdmap is geïnstalleerd, converteert de service PDF Generator OpenOffice-documenten niet naar PDF-documenten. Als u OpenOffice als niet-wortelgebruiker moet installeren en in werking stellen, dan verstrek sudo rechten aan de niet-wortelgebruiker.
>* Als u OpenOffice op een UNIX-Gebaseerd platform gebruikt, stel het volgende bevel in werking om de wegvariabele te plaatsen:\
   >  `export OpenOffice_PATH=/opt/openoffice.org4`
>



### (Alleen voor IBM WebSphere) IBM SSL-socketprovider configureren {#only-for-ibm-websphere-configure-ibm-ssl-socket-provider}

* Voer de volgende stappen uit om IBM SSL-socketprovider te configureren:

1. Maak een kopie van het bestand java.security. De standaardlocatie van het bestand is `[WebSphere_installation_directory]\Appserver\java_[version]\jre\lib\security`.
1. Open het gekopieerde bestand java.security voor bewerking.
1. Wijzig de standaard SSL-socketfabrieken om de JSSE2-fabrieken te gebruiken in plaats van de standaard IBM WebSphere-fabrieken:

   **Standaardinhoud:**

   ```shell
   #ssl.SocketFactory.provider=com.ibm.jsse2.SSLSocketFactoryImpl
   #ssl.ServerSocketFactory.provider=com.ibm.jsse2.SSLServerSocketFactoryImpl
   #WebSphere socket factories (in cryptosf.jar)
   ssl.SocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLSocketFactory
   ssl.ServerSocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLServerSocketFactory
   ```

   **Gewijzigde inhoud:**

   ```shell
   ssl.SocketFactory.provider=com.ibm.jsse2.SSLSocketFactoryImpl
   ssl.ServerSocketFactory.provider=com.ibm.jsse2.SSLServerSocketFactoryImpl
   
   #WebSphere socket factories (in cryptosf.jar)
   #ssl.SocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLSocketFactory
   #ssl.ServerSocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLServerSocketFactory
   ```

1. Als u wilt dat AEM Forms Server het bijgewerkte bestand java.security kan gebruiken terwijl de AEM Forms-server wordt gestart, voegt u het volgende Java-argument toe:

   `-Djava.security.properties= [path of newly created Java.security file].`

### De service Inkt en handschrift installeren configureren {#configure-install-ink-and-handwriting-service}

Als u de Server van Microsoft Windows in werking stelt, vorm de Inkt en de dienst Handwriting. De service is vereist voor het openen van Microsoft PowerPoint-bestanden die inktmogelijkheden van Microsoft Office gebruiken:

1. Open Serverbeheer. Klik op het pictogram **[!UICONTROL Serverbeheer]** in het snelstartvak.
1. Klik op Functies **** toevoegen in het menu **[!UICONTROL Functies]** . Selecteer de de controledoos van de Diensten **[!UICONTROL van de]** Inkt en van de Handtekening.
1. **[!UICONTROL Selecteer de dialoogdoos van Eigenschappen]** met de **[!UICONTROL Inkt en de Diensten]** van het Handschrift geselecteerd. Klik op **[!UICONTROL Installeren]** en de service is geïnstalleerd.

### De instellingen voor bestandsblokken configureren voor Microsoft Office {#configure-the-file-block-settings-for-microsoft-office}

Wijzig de instellingen van het Microsoft Office-vertrouwenscentrum om de service PDF Generator in te schakelen voor het converteren van bestanden die zijn gemaakt met oudere versies van Microsoft Office.

1. Open een Microsoft Office-toepassing. Bijvoorbeeld Microsoft Word. Ga naar **[!UICONTROL Bestand]**> **[!UICONTROL Opties]**. Het dialoogvenster Opties wordt geopend.

1. Klik op **[!UICONTROL Vertrouwenscentrum]** en klik op Instellingen **[!UICONTROL van]** Vertrouwenscentrum.
1. Klik in de instellingen **** Vertrouwenscentrum op Instellingen **[!UICONTROL voor]** bestandsblokkering.
1. Schakel in de lijst **[!UICONTROL Bestandstype]** de optie **[!UICONTROL Openen]** uit voor het bestandstype dat de service PDF Generator moet kunnen converteren naar PDF-documenten.

### Toeslagrechten verlenen voor het vervangen van een procesniveautoken {#grant-the-replace-a-process-level-token-privilege}

Voor de gebruikersaccount die wordt gebruikt om de toepassingsserver te starten, is het token **-voorrecht op procesniveau** vervangen vereist. De lokale systeemaccount heeft standaard de token **-bevoegdheid** Vervangen op procesniveau. Voor de servers die met een gebruiker van de Lokale groep van Beheerders lopen, moet het voorrecht uitdrukkelijk worden verleend. Voer de volgende stappen uit om het voorrecht toe te kennen:

1. Open de Redacteur van het Beleid van de Groep voor Microsoft Windows. Om de Redacteur van het Beleid van de Groep te openen, klik **[!UICONTROL Begin]**, typ **gpedit.msc** in het vakje van het Onderzoek van het Begin, en klik de Redacteur **[!UICONTROL van het Beleid van de]** Groep.
1. Navigeer naar **[!UICONTROL Lokaal computerbeleid]** > **[!UICONTROL Computerconfiguratie]** > **[!UICONTROL Windows-instellingen]** > **[!UICONTROL Beveiligingsinstellingen]** > **[!UICONTROL Lokaal beleid]** **** **** > Toewijzing van gebruikersrechtenen bewerk het token op procesniveau vervangen en neem de groep Beheerders op.
1. Voeg de gebruiker toe aan de Replace een Symbolische ingang van het Niveau van het Proces.

#### De service PDF Generator inschakelen voor niet-beheerders {#enable-the-pdf-generator-service-for-non-administrators}

U kunt een gebruiker zonder beheerder inschakelen om de service PDF Generator te gebruiken. Normaal gesproken kunnen alleen gebruikers met beheerdersrechten de service gebruiken:

1. Maak een omgevingsvariabele, PDFG_NON_ADMIN_ENABLED.
1. Stel de waarde van de omgevingsvariabele in op TRUE.
1. Start de instantie AEM Forms opnieuw.

### Gebruikersaccountbeheer uitschakelen (UAC) {#disable-user-account-control-uac}

1. Ga naar **[!UICONTROL Start > Uitvoeren]** en voer **[!UICONTROL MSCONFIG]** in om het hulpprogramma Systeemconfiguratie te openen.
1. Klik op het tabblad **[!UICONTROL Gereedschappen]** en schuif omlaag en selecteer **[!UICONTROL UAC-instellingen]** wijzigen. Klik op **[!UICONTROL Starten]** om de opdracht in een nieuw venster uit te voeren.
1. Pas de schuifregelaar aan op het niveau Nooit aangeven. Als u klaar bent, sluit u het opdrachtvenster en sluit u het venster Systeemconfiguratie.
1. Verifieer dat register het plaatsen voor UAC aan 0 (nul) wordt geplaatst. Voer de volgende stappen uit om te verifiëren:

   1. Microsoft raadt u aan een back-up van het register te maken voordat u het register wijzigt. Voor gedetailleerde stappen, zie [hoe te file en herstel de registratie in Vensters](https://support.microsoft.com/en-us/help/322756).
   1. Open de Register-editor voor Microsoft Windows. Als u de registereditor wilt openen, gaat u naar Start > Uitvoeren, typt u regedit en klikt u op OK.
   1. Ga naar `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system\`. Zorg ervoor dat de waarde van EnableLUA is ingesteld op 0 (nul).
   1. Zorg ervoor dat de waarde van **EnableLUA** is ingesteld op 0 (nul). Als de waarde niet 0 is, wijzigt u de waarde in 0. Sluit de registereditor.

1. Start de computer opnieuw op.

### Foutrapportservice uitschakelen {#disable-error-reporting-service}

Bij het converteren van een document naar PDF met de service PDF Generator op Windows Server meldt Windows Server af en toe dat het uitvoerbare bestand een probleem heeft aangetroffen en moet worden gesloten. Het heeft echter geen invloed op de PDF-conversie zoals deze op de achtergrond wordt voortgezet.

Als u wilt voorkomen dat de fout wordt ontvangen, kunt u de rapportage van fouten in Windows uitschakelen. Raadpleeg [https://technet.microsoft.com/en-us/library/cc754364.aspx voor meer informatie over het uitschakelen van foutmeldingen](https://technet.microsoft.com/en-us/library/cc754364.aspx).

### HTML naar PDF converteren {#configure-html-to-pdf-conversion}

De service PDF genereren biedt WebKit, WebCapture en FhantomJS-routes of methoden voor het converteren van HTML-bestanden naar PDF-documenten. Als u in Windows conversie wilt inschakelen voor WebKit- en Acrobat WebCapture-routes, kopieert u het Unicode-font naar de map %windir%\fonts.

>[!NOTE]
>
> Wanneer u nieuwe lettertypen in de map Fonts installeert, start u de instantie AEM Forms opnieuw.


### Extra configuraties voor conversie van HTML naar PDF {#extra-configurations-for-html-to-pdf-conversion}

Op UNIX-platforms ondersteunt de service van de PDF Generator WebKit en PhantomJS-routes voor het converteren van HTML-bestanden naar PDF-documenten. Voer de volgende configuraties uit die van toepassing zijn op de door u gewenste conversieroute om HTML naar PDF-conversie in te schakelen:

#### Ondersteuning voor Unicode-lettertypen inschakelen (alleen WebKit) {#enable-support-for-unicode-fonts-webkit-only}

Kopieer het Unicode-lettertype naar een van de volgende mappen, afhankelijk van uw systeem:

* /usr/lib/X11/fonts/TrueType
* /usr/share/fonts/default/TrueType
* /usr/X11R6/lib/X11/fonts/ttf
* /usr/X11R6/lib/X11/fonts/truetype
* /usr/X11R6/lib/X11/fonts/TrueType
* /usr/X11R6/lib/X11/fonts/TTF
* /usr/openwin/lib/X11/fonts/TrueType (Solaris)

>[!NOTE]
>
>* In RedHat Enterprise Linux 6.x en hoger zijn de koerierlettertypen niet beschikbaar. Download het zip-archief font-ibm-type1-1.0.3.zip om de koerierlettertypen te installeren. Extraheer het archief op /usr/share/fonts. Maak een symbolische koppeling van /usr/share/X11/fonts naar /usr/share/fonts.
>* Verwijder alle .lst-cachebestanden voor lettertypen uit de mappen Html2PdfSvc/bin en /usr/share/fonts.
>* Zorg ervoor dat de mappen /usr/lib/X11/fonts en /usr/share/fonts bestaan. Als de mappen niet bestaan, gebruikt u de ln-opdracht om een symbolische koppeling te maken van /usr/share/X11/fonts naar /usr/lib/X11/fonts en een andere symbolische koppeling van /usr/share/fonts naar /usr/share/X11/fonts. Zorg er ook voor dat de koerierlettertypen beschikbaar zijn op /usr/lib/X11/fonts.
>* Zorg ervoor dat alle lettertypen (Unicode en niet-Unicode) beschikbaar zijn in de map /usr/share/fonts of /usr/share/X11/fonts.
>* Wanneer u de PDF Generator-service uitvoert als een gebruiker die geen hoofdmap heeft, geeft u de gebruiker die geen hoofdmap heeft, lees- en schrijftoegang tot alle fontmappen.
>* Wanneer u nieuwe lettertypen in de map Fonts installeert, start u de instantie AEM Forms opnieuw.
>



## AEM Forms add-on-pakket installeren {#install-aem-forms-add-on-package}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Het pakket bevat AEM Forms Document Services en andere mogelijkheden voor AEM Forms. Voer de volgende stappen uit om het pakket te installeren:

1. Meld u als beheerder aan bij de [AEM-server](http://localhost:4502) en open [pakketshare](http://localhost:4502/crx/packageshare). U hebt een Adobe-id nodig om u aan te melden bij het delen van het pakket.

1. Zoek in [AEM-pakketdeling](http://localhost:4502/crx/packageshare/login.html)in **[!UICONTROL AEM 6.4-formulierinvoegpakketten]** naar het pakket dat op uw besturingssysteem van toepassing is en klik op **[!UICONTROL Downloaden]**. Lees en accepteer de licentieovereenkomst en klik op **[!UICONTROL OK]**. Het downloaden begint. Nadat u het bestand hebt gedownload, staat het woord **[!UICONTROL Gedownload]** naast het pakket.

   U kunt het versienummer ook gebruiken om een add-on pakket te zoeken. Raadpleeg het [artikel over de release](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) van AEM Forms voor het versienummer van het meest recente pakket.

1. Klik op **[!UICONTROL Gedownload]** nadat het downloaden is voltooid. U wordt omgeleid naar pakketbeheer. Zoek in pakketbeheer naar het gedownloade pakket en klik op **[!UICONTROL Installeren]**.

   Als u het pakket handmatig downloadt via de directe koppeling in het [artikel met de release](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) van AEM Forms, meldt u zich aan bij pakketbeheer, klikt u op Pakket **** uploaden, selecteert u het gedownloade pakket en klikt u op Uploaden. Nadat het pakket is geüpload, klikt u op de pakketnaam en klikt u op **[!UICONTROL Installeren]**.

1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM-instantie opnieuw te starten. **Stop niet onmiddellijk de server.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer voorkomen in het bestand `[AEM-Installation-Directory]/crx-quickstart/logs/error`.log en het logbestand stabiel is.

## Configuratie na installatie {#post-installation-configurations}

### Opstartdelegatie configureren voor bibliotheken met RSA/BouncyCastle {#configure-boot-delegation-for-rsa-bouncycastle-libraries}

1. Stop de AEM-instantie. Navigeer naar de [AEM-installatiemap]\crx-quickstart\conf\ folder. Open het bestand sling.properties voor bewerking.

   Als u een AEM-instantie start `[AEM installation directory]\crx-quickstart\bin\start.bat` , bewerkt u de eigenschappen sling.properties op `[AEM_root]\crx-quickstart\`.

1. Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   sling.bootdelegation.class.org.bouncycastle.jce.provider.BouncyCastleProvider=org.bouncycastle.*
   ```

1. (Alleen AIX) Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Sla het bestand op en sluit het.

### De service voor lettertypebeheer configureren {#configuring-the-font-manager-service}

1. Meld u als beheerder aan bij [AEM Configuration Manager](http://localhost:4502/system/console/configMgr) .
1. Zoek en open de service **[!UICONTROL CQ-DAM-Handler-Gibson Font Managers]** . Geef het pad op van de systeemlettertypen, Adobe Server-lettertypen en de directory&#39;s met klantlettertypen. Click **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Uw recht om lettertypen te gebruiken die door andere partijen dan Adobe worden geleverd, wordt beheerst door de licentieovereenkomsten die deze partijen u met deze lettertypen bieden, en wordt niet gedekt door uw licentie voor het gebruik van Adobe-software. Adobe raadt u aan na te gaan of u voldoet aan alle toepasselijke niet-Adobe-licentieovereenkomsten voordat u niet-Adobe-lettertypen gebruikt met Adobe-software, met name wat het gebruik van lettertypen in een serveromgeving betreft.
   > Wanneer u nieuwe lettertypen in de map Fonts installeert, start u de instantie AEM Forms opnieuw.

### Een lokale gebruikersaccount configureren om de service PDF Generator uit te voeren {#configure-a-local-user-account-to-run-the-pdf-generator-service}

Er is een lokale gebruikersaccount vereist om de service PDF Generator uit te voeren. Zie Een gebruikersaccount [maken in Windows](https://support.microsoft.com/en-us/help/13951/windows-create-user-account) of [een gebruikersaccount maken op UNIX-platforms](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/4/html/Step_by_Step_Guide/s1-starting-create-account.html)voor stappen om een lokale gebruiker te maken.

1. Open de configuratiepagina van de [AEM Forms PDF Generator](http://localhost:4502/libs/fd/pdfg/config/ui.html) .

1. Geef op het tabblad **[!UICONTROL Gebruikersaccounts]** de gegevens van een lokale gebruikersaccount op en klik op **[!UICONTROL Verzenden]**. Als Microsoft Windows daarom vraagt, geeft u de gebruiker toegang. Als de geconfigureerde gebruiker met succes is toegevoegd, wordt deze weergegeven onder de sectie **[!UICONTROL Uw gebruikersaccounts]** op het tabblad **[!UICONTROL Gebruikersaccounts]** .

### De time-outinstellingen configureren {#configure-the-time-out-settings}

1. Zoek in [AEM-configuratiemanager](http://localhost:4502/system/console/configMgr)de **[!UICONTROL Jacorb ORB Provider]** -service op en open deze.

   Voeg het volgende toe aan het veld **[!UICONTROL Custom Properties.name]** en klik op **[!UICONTROL Save]**. De wachtende antwoordtime-out (ook wel CORBA-clienttime-out genoemd) wordt ingesteld op 600 seconden.

   `jacorb.connection.client.pending_reply_timeout=600000`

1. Meld u aan bij de AEM-auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Gereedschappen]** > **[!UICONTROL Formulieren]** > PDF-generator **** configureren. De standaard-URL is http://localhost:4502/libs/fd/pdfg/config/ui.html.

   Open het tabblad **[!UICONTROL Algemene configuratie]** en wijzig de waarde van de volgende velden voor uw omgeving:

<table> 
 <tbody> 
  <tr> 
   <td>Veld</td> 
   <td>Beschrijving</td> 
   <td>Standaardwaarde</td> 
  </tr> 
  <tr> 
   <td>Time-out serverconversie</td> 
   <td>Een PDFG-conversie blijft actief gedurende het aantal seconden dat is gedefinieerd in de time-out voor serverconversie</td> 
   <td>270 seconden<br /> </td> 
  </tr> 
  <tr> 
   <td>Seconden van PDFG-opschoning</td> 
   <td>Het aantal seconden dat is vereist om bewerkingen na de conversie uit te voeren.<br /> </td> 
   <td>3600 seconden</td> 
  </tr> 
  <tr> 
   <td>Seconden van taakvervaldatum</td> 
   <td>Duur waarvoor de service van de PDF Generator een conversie mag uitvoeren. Zorg ervoor dat de waarde van de Seconden van de Vervaltijd van de Baan groter is dan de waarde van de Seconden van de Schoonmaakactie PDFG.</td> 
   <td>7200 seconden</td> 
  </tr> 
 </tbody> 
</table>

### Acrobat configureren voor de service PDF Generator {#configure-acrobat-for-the-pdf-generator-service}

In Microsoft Windows gebruikt de service PDF Generator Adobe Acrobat om ondersteunde bestandsindelingen te converteren naar een PDF-document. Voer de volgende stappen uit om Adobe Acrobat voor de service PDF Generator te configureren:

1. Open Acrobat en selecteer **[!UICONTROL Bewerken]**> **[!UICONTROL Voorkeuren]**> **[!UICONTROL Updater]**. Schakel in Controleren op updates de optie **[!UICONTROL Automatisch updates]** installeren uit en klik op **[!UICONTROL OK]**. Sluit Acrobat.
1. Dubbelklik op een PDF-document op uw systeem. Wanneer Acrobat voor het eerst wordt gestart, worden de dialoogvensters Aanmelden, Welkomstscherm en EULA weergegeven. Deze dialoogvensters sluiten voor alle gebruikers die zijn geconfigureerd voor het gebruik van PDF Generator.
1. Voer de PDF Generator-hulpprogrammabatchbestand uit om Acrobat voor de PDF Generator-service te configureren:

   1. Open [AEM Package Manager](http://localhost:4502/crx/packmgr/index.jsp) en download het `adobe-aemfd-pdfg-common-pkg-[version].zip` bestand van pakketbeheer.
   1. Pak het gedownloade .zip-bestand uit. Open de opdrachtprompt met beheerdersrechten.
   1. Navigate to the `[extracted-zip-file]\jcr_root\etc\fd\pdfg\tools\adobe-aemfd-pdfg-utilities-[version]-win.zip\scripts` directory. Voer het volgende batchbestand uit:

      `Acrobat_for_PDFG_Configuration.bat`

      Acrobat is geconfigureerd om te worden uitgevoerd met de service PDF Generator.

1. Start System Readiness Tool (SRT) om de installatie van Acrobat te valideren. Het gereedschap controleert of de computer op de juiste wijze is geconfigureerd voor het uitvoeren van conversies van PDF Generator en genereert een rapport bij het opgegeven pad:

   1. Opdrachtprompt openen. Navigate to the `[extracted-adobe-aemfd-pdfg-common-pkg]\jcr_root\etc\fd\ pdfg\tools\adobe-aemfd-pdfg-utilities-[version]-win.zip\srt` folder. Voer het volgende bevel van de bevelherinnering in werking:

      `cscript SystemReadinessTool.vbs [Path_of_reports_folder] en`

      >[!NOTE]
      >
      >Als het Hulpprogramma voor systeemgereedheid meldt dat het bestand pdfgen.api niet beschikbaar is in de map acrobat plug-ins, kopieert u het bestand pdfgen.api van de `[extracted-adobe-aemfd-pdfg-common-pkg]\plugins\x86_win32` map naar de `[Acrobat_root]\Acrobat\plug_ins` map.

   1. Ga naar `[Path_of_reports_folder]`. Open het bestand SystemReadinessTool.html. Verifieer het rapport en los de bovengenoemde kwesties op.

### Primaire route voor conversie van HTML naar PDF configureren (alleen Windows) {#configure-primary-route-for-html-to-pdf-conversion-windows-only}

De service PDF Generator biedt meerdere manieren om HTML-bestanden naar PDF-documenten te converteren: Webkit, Acrobat WebCapture (alleen Windows) en PhantomJS. Adobe raadt u aan de PhantomJS-route te gebruiken, omdat deze de mogelijkheid biedt om dynamische inhoud af te handelen en omdat deze route geen afhankelijkheden heeft met 32-bits bibliotheken, 32-bits JDK of geen extra lettertypen vereist. Ook, vereist de route PhantomJS sudo of worteltoegang niet om de omzetting in werking te stellen.

De primaire standaardroute voor conversie van HTML naar PDF is Webkit. U wijzigt de omzettingsroute als volgt:

1. Navigeer in de auteur van AEM naar **[!UICONTROL Gereedschappen]**> **[!UICONTROL Formulieren]**> PDF-generator **** configureren.

1. Op het **[!UICONTROL Algemene lusje van de Configuratie]** , selecteer de aangewezen omzettingsroute van de **[!UICONTROL Primaire Route voor de omzettingen]** van HTML aan PDF drop-down.

### Global Trust Store initialiseren{#intialize-global-trust-store}

Met het Betrouwbaarheidsopslagbeheer kunt u certificaten die u op de server vertrouwt, importeren, bewerken en verwijderen voor validatie van digitale handtekeningen en certificaatverificatie. U kunt om het even welk aantal certificaten invoeren en uitvoeren. Nadat een certificaat is geïmporteerd, kunt u de vertrouwensinstellingen bewerken en het type vertrouwde opslag vertrouwen. Voer de volgende stappen uit om een vertrouwde opslag te initialiseren:

1. Meld u als beheerder aan bij de AEM Forms-instantie.
1. Ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Beveiliging]** > **[!UICONTROL Betrouwbaarheidswinkel]**.
1. Klik op **[!UICONTROL TrustStore]** maken. Stel het wachtwoord in en tik op **[!UICONTROL Opslaan]**.

### Certificaten instellen voor Reader-extensie en -coderingsservice {#set-up-certificates-for-reader-extension-and-encryption-service}

De DocAssurance-service kan gebruiksrechten toepassen op PDF-documenten. Als u gebruiksrechten wilt toepassen op PDF-documenten, configureert u de certificaten.

Voordat u de certificaten instelt, moet u controleren of u beschikt over:

* Certificaatbestand (.pfx).

* Wachtwoord voor persoonlijke sleutel dat bij het certificaat wordt geleverd.

* Alias persoonlijke sleutel. U kunt de Java-opdracht Keytool uitvoeren om de alias Persoonlijke sleutel weer te geven:
   `keytool -list -v -keystore [keystore-file] -storetype pkcs12`

* Wachtwoord sleutelarchiefbestand. Als u het Adobe Reader Extensions-certificaat gebruikt, is het wachtwoord voor het sleutelarchiefbestand altijd hetzelfde als het wachtwoord voor de persoonlijke sleutel.

Voer de volgende stappen uit om de certificaten te configureren:

1. Meld u als beheerder aan bij de AEM-auteur-instantie. Ga naar **[!UICONTROL Gereedschappen]** > **[!UICONTROL Beveiliging]** > **[!UICONTROL Gebruikers]**.
1. Klik op het veld **[!UICONTROL Naam]** van de gebruikersaccount. De pagina Gebruikersinstellingen **** bewerken wordt geopend. Voor de instantie van de Auteur AEM, verblijven de certificaten in een KeyStore. Als u nog niet eerder een KeyStore hebt gemaakt, klikt u op **[!UICONTROL Create KeyStore]** en stelt u een nieuw wachtwoord in voor de KeyStore. Als de server al een KeyStore bevat, slaat u deze stap over.  Als u het Adobe Reader Extensions-certificaat gebruikt, is het wachtwoord voor het sleutelarchiefbestand altijd hetzelfde als het wachtwoord voor de persoonlijke sleutel.
1. Selecteer op de pagina Gebruikersinstellingen **** bewerken het tabblad **[!UICONTROL KeyStore]** . Vouw de optie Persoonlijke sleutel **[!UICONTROL toevoegen uit sleutelarchiefbestand]** uit en geef een alias op. De alias wordt gebruikt om de bewerking Reader Extensions uit te voeren.
1. Als u het certificaatbestand wilt uploaden, klikt u op Bestand **[!UICONTROL sleutelarchief]** selecteren en uploadt u een bestand &lt;filename>.pfx.

   Voeg het **[!UICONTROL Sleutelwachtwoord]** van de Opslag, het Wachtwoord **[!UICONTROL van de]** Persoonlijke Sleutel, en de Alias **[!UICONTROL van de]** Persoonlijke Sleutel toe die met het certificaat aan de respectieve gebieden wordt geassocieerd. Klik op **[!UICONTROL Verzenden]**.

   >[!NOTE]
   >
   >* In het productiemilieu, vervang uw evaluatiegeloofsbrieven met productiereferenties. Zorg ervoor dat u de oude gegevens voor Reader-extensies verwijdert voordat u een verlopen extensie of evaluatiereferentie bijwerkt.


1. Klik op **[!UICONTROL Opslaan en sluiten]** op de pagina Gebruikersinstellingen **** bewerken.

### AES-256 inschakelen {#enable-aes}

Als u AES 256-versleuteling wilt gebruiken voor PDF-bestanden, moet u de JCE-bestanden (Unlimited Strength Jurdiction Policy) (Java Cryptography Extension) ophalen en installeren. Vervang de bestanden local_policy.jar en US_export_policy.jar in de map jre/lib/security. Als u bijvoorbeeld Sun JDK gebruikt, kopieert u de gedownloade bestanden naar de `[JAVA_HOME]/jre/lib/security` map.

De service Assembler is afhankelijk van de service Reader Extensions, de service Handtekening, de service Forms en de service Output. Voer de volgende stappen uit om te verifiëren dat de vereiste diensten in gebruik zijn:

1. Meld u `https://'[server]:[port]'/system/console/bundles` als beheerder aan bij de URL.
1. Zoek de volgende dienst en zorg ervoor dat de diensten in gebruik zijn:

<table> 
 <tbody> 
  <tr> 
   <th>Servicenaam</th> 
   <th>Bundnaam</th> 
  </tr> 
  <tr> 
   <td>Handtekeningenservice</td> 
   <td>adobe-aemfd-signatures</td> 
  </tr> 
  <tr> 
   <td>Reader Extensions Service</td> 
   <td>com.adobe.aemfd.adobe-aemfd-readerextensions<br /> </td> 
  </tr> 
  <tr> 
   <td>Forms Service</td> 
   <td>com.adobe.livecycle.adobe-lc-forms-bedrock-connector<br /> </td> 
  </tr> 
  <tr> 
   <td>Uitvoerservice</td> 
   <td>com.adobe.livecycle.adobe-lc-forms-bedrock-connector</td> 
  </tr> 
 </tbody> 
</table>

## Bekende problemen en problemen oplossen {#known-issues-and-troubleshooting}

* De conversie van HTML naar PDF mislukt als een gecomprimeerd invoerbestand HTML-bestanden bevat met double-bytetekens in bestandsnamen. U voorkomt dit door geen double-bytetekens te gebruiken bij de naamgeving van HTML-bestanden.

* Op UNIX-besturingssystemen vindt u de volgende handelingen om ontbrekende bibliotheken te zoeken:

1. Ga naar `[crx-repository]/bedrock/svcnative/HtmlToPdfSvc/bin/`.

1. Voer de volgende opdracht uit om alle bibliotheken weer te geven die PhantomJS nodig heeft voor conversie van HTML naar PDF.

   `ldd phantomjs`

   Voer de volgende opdracht uit om ontbrekende bibliotheken weer te geven.

   `ldd phantomjs | grep not`

1. De ontbrekende bibliotheken handmatig installeren.

## Volgende stappen {#next-steps}

U hebt een werkende omgeving voor AEM Forms-documentservices. U kunt documentservices gebruiken via:

* [Centrische workflows van formulieren op OSGi](/help/forms/using/aem-forms-workflow.md)
* [Gecontroleerde mappen](/help/forms/using/watched-folder-in-aem-forms.md)
* [API&#39;s voor documentservices](/help/forms/using/aem-document-services-programmatically.md)

