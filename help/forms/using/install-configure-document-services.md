---
title: Documentservices installeren en configureren
description: Installeer AEM Forms-documentservices voor het maken, samenstellen, distribueren, archiveren van PDF-documenten, toevoegen van digitale handtekeningen om de toegang tot documenten te beperken en decoderen van Barcoded Forms.
topic-tags: installing
role: Admin, User, Developer
solution: Experience Manager, Experience Manager Forms
exl-id: 5d48e987-16c2-434b-8039-c82181d2e028
source-git-commit: 0a1a0d8e3a2794bda247e7b07a2ef9d9fcac7c13
workflow-type: tm+mt
source-wordcount: '5503'
ht-degree: 0%

---

# Documentservices installeren en configureren {#installing-and-configuring-document-services}

AEM Forms biedt een set OSGi-services voor het uitvoeren van verschillende bewerkingen op documentniveau, zoals services voor het maken, samenstellen, distribueren en archiveren van PDF-documenten, het toevoegen van digitale handtekeningen om de toegang tot documenten te beperken en het decoderen van Barcoded Forms. Deze services zijn opgenomen in het invoegpakket voor AEM Forms. Deze services worden gezamenlijk documentservices genoemd. De lijst met beschikbare documentservices en hun belangrijkste mogelijkheden is als volgt:

* **Assembler-service:** Hiermee kunt u PDF- en XDP-documenten combineren, opnieuw rangschikken en vergroten en informatie over PDF-documenten opvragen. Het helpt ook PDF documenten in PDF/A norm omzetten en bevestigen, PDF forms, de vormen van XML, en PDF forms omzetten in PDF/A-1b, PDF/A-2b, en PDFA/A-3b. Zie voor meer informatie [Assembler-service](/help/forms/using/assembler-service.md).

* **ConvertPDF-service:** Hiermee kunt u PDF-documenten omzetten in PostScript- of afbeeldingsbestanden (JPEG, JPEG 2000, PNG en TIFF). Zie voor meer informatie [ConvertPDF-service](/help/forms/using/using-convertpdf-service.md).

* **Barcoded Forms-service:** Hiermee kunt u gegevens extraheren uit elektronische afbeeldingen van streepjescodes. De service accepteert TIFF- en PDF-bestanden die een of meer streepjescodes als invoer bevatten en extraheert de streepjescodegegevens. Zie voor meer informatie [Barcoded Forms Service](/help/forms/using/using-barcoded-forms-service.md).

* **DocAssurance-service:** Hiermee kunt u documenten versleutelen en ontsleutelen, de functionaliteit van Adobe Reader uitbreiden met extra gebruiksrechten en digitale handtekeningen toevoegen aan uw documenten. De Doc Assurance-service bevat drie services: handtekening, versleuteling en reader-extensie. Zie voor meer informatie [DocAssurance Service](/help/forms/using/overview-aem-document-services.md).

* **Coderingsservice:** Hiermee kunt u documenten versleutelen en ontsleutelen. Wanneer een document wordt versleuteld, wordt de inhoud ervan onleesbaar. Een geautoriseerde gebruiker kan het document decoderen om toegang tot de inhoud te krijgen. Zie voor meer informatie [Coderingsservice](/help/forms/using/overview-aem-document-services.md#encryption-service).

* **Forms-service:** Hiermee kunt u interactieve toepassingen voor het vastleggen van gegevens maken die formulieren valideren, verwerken, transformeren en leveren die gewoonlijk in Forms Designer worden gemaakt. De Forms-service geeft elk formulierontwerp dat u ontwikkelt, weer in PDF-documenten. Zie voor meer informatie [Forms Service](/help/forms/using/forms-service.md).

* **Uitvoerservice:** Hiermee kunt u documenten in verschillende indelingen maken, zoals PDF, laserprinterindelingen en labelprinterindelingen. Indelingen voor laserprinters zijn PostScript en Printer Control Language (PCL). Zie voor meer informatie [Uitvoerservice](/help/forms/using/output-service.md).

* **PDF Generator:** De service PDF Generator biedt API&#39;s waarmee native bestandsindelingen kunnen worden omgezet in PDF. Het zet ook PDF in andere dossierformaten om en optimaliseert de grootte van PDF documenten. Zie voor meer informatie [PDF Generator-service](aem-document-services-programmatically.md#pdfgeneratorservice).

* **Reader Extension Service:** Laat uw organisatie toe om interactieve documenten van de PDF gemakkelijk te delen door de functionaliteit van Adobe Reader met extra gebruiksrechten uit te breiden. De service activeert functies die niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Reader, zoals het toevoegen van opmerkingen aan een document, het invullen van formulieren en het opslaan van het document. Zie voor meer informatie [Reader Extension Service](/help/forms/using/overview-aem-document-services.md#reader-extension-service).

* **Handtekeningenservice:** Hiermee kunt u werken met digitale handtekeningen en documenten op de AEM server. De service Handtekening wordt bijvoorbeeld doorgaans in de volgende situaties gebruikt:

   * De AEM server certificeert een formulier voordat het naar een gebruiker wordt verzonden om te worden geopend met Acrobat of Adobe Reader.
   * De AEM server valideert een handtekening die aan een formulier is toegevoegd met Acrobat of Adobe Reader.
   * De AEM server ondertekent een formulier namens een openbare notaris.

  De handtekeningsdienst heeft toegang tot certificaten en geloofsbrieven die in de vertrouwde opslag worden opgeslagen. Zie voor meer informatie [Handtekeningenservice](/help/forms/using/aem-document-services-programmatically.md).

AEM Forms is een krachtig platform op bedrijfsniveau en de documentservices zijn slechts een van de mogelijkheden van AEM Forms. Voor de volledige lijst met mogelijkheden raadpleegt u [Inleiding tot AEM Forms](/help/forms/using/introduction-aem-forms.md).

## Implementatietopologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Over het algemeen hebt u slechts één AEM (auteur of publicatie) nodig om AEM Forms-documentservices uit te voeren. De volgende topologie wordt geadviseerd om de documentdiensten van AEM Forms in werking te stellen. Voor gedetailleerde informatie over topologieën, zie [Architectuur en plaatsingstopologieën voor AEM Forms](/help/forms/using/aem-forms-architecture-deployment.md).

![Architectuur en plaatsingstopologieën voor AEM Forms](do-not-localize/document-services.png)

>[!NOTE]
>
>Hoewel u met AEM Forms alle functies van één server kunt instellen en uitvoeren, moet u capaciteitsplanning uitvoeren, taakverdeling toepassen en specifieke servers instellen voor specifieke mogelijkheden in een productieomgeving. Voor een omgeving die bijvoorbeeld gebruikmaakt van de service PDF Generator om duizenden pagina&#39;s per dag om te zetten en meerdere adaptieve formulieren om gegevens vast te leggen, stelt u afzonderlijke AEM Forms-servers in voor de service PDF Generator en de mogelijkheden voor adaptieve formulieren. Het helpt optimale prestaties te bieden en de servers onafhankelijk van elkaar te schalen.

## Systeemvereisten {#system-requirements}

Voordat u de documentservices van AEM Forms gaat installeren en configureren, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Voor een gedetailleerde lijst met ondersteunde hardware en software raadpleegt u [technische voorschriften](/help/sites-deploying/technical-requirements.md).

* Het installatiepad van de AEM-instantie bevat geen witruimten.
* Er wordt een AEM-instantie uitgevoerd. In AEM terminologie is een &quot;instantie&quot; een kopie van AEM die op een server in de auteur- of publicatiemodus wordt uitgevoerd. Over het algemeen hebt u slechts één AEM (auteur of publicatie) nodig om AEM Forms-documentservices uit te voeren:

   * **Auteur**: Een AEM die wordt gebruikt om inhoud te maken, te uploaden en te bewerken en om de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Publiceren**: Een AEM instantie die de gepubliceerde inhoud via internet of een intern netwerk aan het publiek levert.

* Er wordt voldaan aan de geheugenvereisten. AEM Forms-add-on-pakket vereist:

   * 15 GB tijdelijke ruimte voor Microsoft® Windows-installaties.
   * 6 GB tijdelijke ruimte voor UNIX-installaties.

* Clientsoftware die vereist is voor PDF Generator om conversie uit te voeren op Microsoft® Windows en Linux®, is geïnstalleerd:

   * **Microsoft® Windows**: installeren [Microsoft® Office](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p) of [Apache OpenOffice](/help/forms/using/aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator)
   * **Linux®**: installeren [Apache OpenOffice](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p)

>[!NOTE]
>
>* In Microsoft® Windows ondersteunt PDF Generator WebKit, Acrobat WebCapture en PhantomJS conversieroutes om HTML-bestanden om te zetten in PDF-documenten.
>* Op op UNIX-Gebaseerde werkende systemen, steunt de PDF Generator WebKit en PhantomJS omzettingsroutes om HTML dossiers in de documenten van PDF om te zetten.
>

### Extra eisen voor het op UNIX gebaseerde besturingssysteem {#extrarequirements}

Als u een op UNIX gebaseerd besturingssysteem gebruikt, installeert u de volgende 32-bits pakketten via de installatiemedia van het desbetreffende besturingssysteem:
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

* **(alleen PDF Generator**) Installeer de 32-bits versie van bibliotheken met libcurl, libcrypto en libssl en maak de onderstaande koppelingen. De symlinks verwijzen naar de meest recente versie van de respectievelijke bibliotheken:

   * /usr/lib/libcurl.so
   * /usr/lib/libcrypto.so
   * /usr/lib/libssl.so

* **(alleen PDF Generator)** De dienst van de PDF Generator steunt WebKit en routes PhantomJS om de dossiers van HTML in de documenten van PDF om te zetten. Om omzetting voor route PhantomJS toe te laten, installeer hieronder vermelde bibliotheken met 64 bits. Over het algemeen zijn deze bibliotheken al geïnstalleerd. Als er een bibliotheek ontbreekt, installeert u deze handmatig:

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

## Vooraf geïnstalleerde configuraties {#preinstallationconfigurations}

Configuraties die worden vermeld in de sectie voor configuraties vóór de installatie zijn alleen van toepassing op de service PDF Generator. Als u de dienst van de PDF Generator niet vormt, kunt u de sectie van de pre-installatieconfiguratie overslaan.

### Adobe Acrobat en toepassingen van derden installeren {#install-adobe-acrobat-and-third-party-applications}

Als u de dienst van de PDF Generator gaat gebruiken om inheemse dossierformaten zoals Microsoft® Word, Microsoft® Excel, Microsoft® PowerPoint, OpenOffice, WordPerfect X7, en Adobe Acrobat aan de Documenten van PDF om te zetten, zorg ervoor dat deze toepassingen op de Server van AEM Forms worden geïnstalleerd.

>[!NOTE]
>
>* Als uw AEM Forms Server zich in een offline- of beveiligde omgeving bevindt en het internet niet beschikbaar is om Adobe Acrobat te activeren, raadpleegt u [Offlineactivering](https://exception.licenses.adobe.com/aoes/aoes/v1/t1?locale=en) voor instructies om dergelijke instanties van Adobe Acrobat te activeren.
>* Adobe Acrobat, Microsoft® Word, Excel en PowerPoint zijn alleen beschikbaar voor Microsoft® Windows. Als u het op UNIX-Gebaseerde werkende systeem gebruikt, installeer OpenOffice om rijke tekstdossiers en gesteunde dossiers van Microsoft® Office in de documenten van PDF om te zetten.
>* Sluit alle dialoogvensters die na het installeren van Adobe Acrobat en software van derden worden weergegeven voor alle gebruikers die zijn geconfigureerd om de service PDF Generator te gebruiken.
>* Start minstens één keer alle geïnstalleerde software. Alle dialoogvensters sluiten voor alle gebruikers die zijn geconfigureerd om de service PDF Generator te gebruiken.
>* [Vervaldatum van je Adobe Acrobat serienummers controleren](https://helpx.adobe.com/enterprise/kb/volume-license-expiration-check.html) en een datum voor het bijwerken van de licentie of [serienummer migreren](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/licensing.html#migrating-your-serial-number) op basis van de vervaldatum.

Open Microsoft® Word nadat u Acrobat hebt geïnstalleerd. Op de **Acrobat** tabblad, klikt u op **PDF maken** en converteert u een .doc- of .docx-bestand dat op uw computer beschikbaar is naar een PDF-document. Als de conversie succesvol is, is AEM Forms klaar om Acrobat te gebruiken met de service PDF Generator.

### Omgevingsvariabelen instellen {#setup-environment-variables}

Stel omgevingsvariabelen in voor de 64-bits Java Development Kit, toepassingen van derden en Adobe Acrobat. De omgevingsvariabelen moeten het absolute pad bevatten van het uitvoerbare bestand dat wordt gebruikt om de bijbehorende toepassing te starten. In de onderstaande tabel worden bijvoorbeeld de omgevingsvariabelen voor een paar toepassingen weergegeven:

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
>* JAVA_HOME en Acrobat_PATH (alleen Windows) zijn verplichte omgevingsvariabelen.
>* De omgevingsvariabele OpenOffice_PATH wordt ingesteld op de installatiemap in plaats van op het pad naar het uitvoerbare bestand.
>* Stel geen omgevingsvariabelen in voor Microsoft® Office-toepassingen zoals Word, PowerPoint, Excel en Project, of voor AutoCAD. Als deze toepassingen op de server worden geïnstalleerd, genereert de dienst van de PDF automatisch begint deze toepassingen.
>* Voor op UNIX-Gebaseerde platforms, installeer OpenOffice als /root. Als OpenOffice niet als wortel wordt geïnstalleerd, kan de dienst van de PDF Generator geen documenten OpenOffice in de documenten van PDF omzetten. Als u OpenOffice als niet-wortelgebruiker moet installeren en in werking stellen, dan verstrek sudo rechten aan de niet-wortelgebruiker.
>* Als u OpenOffice op een UNIX-Gebaseerd platform gebruikt, stel het volgende bevel in werking om de wegvariabele te plaatsen:
>
>  `export OpenOffice_PATH=/opt/openoffice.org4`

### (Alleen voor IBM® WebSphere®) Configureer IBM® SSL-socketprovider {#only-for-ibm-websphere-configure-ibm-ssl-socket-provider}

Voer de volgende stappen uit om IBM® SSL-socketprovider te configureren:

1. Maak een kopie van het bestand java.security. De standaardlocatie van het bestand is `[WebSphere_installation_directory]\Appserver\java_[version]\jre\lib\security`.
1. Open het gekopieerde bestand java.security voor bewerking.
1. Wijzig de standaard SSL-socketfabrieken om de JSSE2-fabrieken te gebruiken in plaats van de standaard IBM® WebSphere®-fabrieken:

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

### (Alleen Windows) Configureer de instellingen voor bestandsblokken voor Microsoft® Office {#configure-the-file-block-settings-for-microsoft-office}

Wijzig de instellingen van het Microsoft® Office-vertrouwenscentrum om de PDF Generator in staat te stellen bestanden die zijn gemaakt met oudere versies van Microsoft® Office, om te zetten.

1. Open een Microsoft® Office-toepassing. Bijvoorbeeld Microsoft® Word. Navigeren naar **[!UICONTROL File]**> **[!UICONTROL Options]**. Het dialoogvenster Opties wordt geopend.

1. Klikken **[!UICONTROL Trust Center]** en klik op **[!UICONTROL Trust Center Settings]**.
1. In de **[!UICONTROL Trust Center settings]**, klikt u op **[!UICONTROL File Block Settings]**.
1. In de **[!UICONTROL File Type]** lijst, deselecteren **[!UICONTROL Open]** voor het bestandstype dat de service PDF Generator moet kunnen converteren naar PDF-documenten.

### (Alleen Windows) Vervang het token voor een procesniveau {#grant-the-replace-a-process-level-token-privilege}

Voor de gebruikersaccount die wordt gebruikt om de toepassingsserver te starten, is het **Een token op procesniveau vervangen** voorrecht. De lokale systeemaccount heeft de **Een token op procesniveau vervangen** bevoegdheden standaard. Voor de servers die met een gebruiker van de Lokale groep van Beheerders lopen, moet het voorrecht uitdrukkelijk worden verleend. Voer de volgende stappen uit om het voorrecht toe te kennen:

1. Open de Redacteur van het Beleid van de Groep voor Microsoft® Vensters. Om de Redacteur van het Beleid van de Groep te openen, klik **[!UICONTROL Start]**, type **gpedit.msc** in het vak Zoekopdracht starten en klik op **[!UICONTROL Group Policy Editor]**.
1. Navigeren naar **[!UICONTROL Local Computer Policy]** > **[!UICONTROL Computer Configuration]** > **[!UICONTROL Windows Settings]** > **[!UICONTROL Security Settings]** > **[!UICONTROL Local Policies]** > **[!UICONTROL User Rights Assignment]** en bewerkt u de **[!UICONTROL Replace a process level token]** beleid en omvat de groep van Beheerders.
1. Voeg de gebruiker toe aan de Replace een Symbolische ingang van het Niveau van het Proces.

>[!NOTE]
>
> Zoals hierboven geïmpliceerd, als de AEM server als dienst onder de rekening LocalSystem (LSA) loopt, uitdrukkelijk is het toewijzen van dit voorrecht aan een gebruiker niet noodzakelijk.

### (Alleen Windows) De service PDF Generator inschakelen voor niet-beheerders {#enable-the-pdf-generator-service-for-non-administrators}

U kunt een niet beheerdergebruiker toelaten om de dienst van de PDF Generator te gebruiken. Normaal gesproken kunnen alleen gebruikers met beheerdersrechten de service gebruiken:

1. Maak een omgevingsvariabele, PDFG_NON_ADMIN_ENABLED.
1. Stel de waarde van de omgevingsvariabele in op TRUE.
1. Start de AEM Forms-instantie opnieuw.

>[!NOTE]
>
> Het wordt aanbevolen de SDK opnieuw te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

### (Alleen Windows) Gebruikersaccountbeheer uitschakelen (UAC) {#disable-user-account-control-uac}

1. Ga voor toegang tot het hulpprogramma Systeemconfiguratie naar **[!UICONTROL Start > Run]** en vervolgens voert u **[!UICONTROL MSCONFIG]**.
1. Klik op de knop **[!UICONTROL Tools]** en omlaag schuiven en selecteren **[!UICONTROL Change UAC Settings]**. Klikken **[!UICONTROL Launch]** om de opdracht in een nieuw venster uit te voeren.
1. Pas de schuifregelaar aan op het niveau Nooit aangeven. Wanneer gebeëindigd, sluit het bevelvenster en sluit het venster van de Configuratie van het Systeem.
1. Verifieer dat register het plaatsen voor UAC aan 0 (nul) wordt geplaatst. Voer de volgende stappen uit om te verifiëren:

   1. Microsoft® raadt u aan een back-up van het register te maken voordat u het wijzigt. Zie voor meer informatie [Hoe te file en herstel de registratie in Vensters](https://support.microsoft.com/en-us/help/322756).
   1. Open Microsoft® Windows Registry Editor. Als u de registereditor wilt openen, gaat u naar Start > Uitvoeren, typt u regedit en klikt u op OK.
   1. Navigeren naar `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system\`. Zorg ervoor dat de waarde van EnableLUA is ingesteld op 0 (nul).
   1. Waarde van garanderen **EnableLUA** is ingesteld op 0 (nul). Als de waarde niet 0 is, wijzigt u de waarde in 0. Sluit de registereditor.

1. Start de computer opnieuw op.

### (Alleen Windows) Fout bij rapporteren van service uitschakelen {#disable-error-reporting-service}

Terwijl het omzetten van een document in PDF gebruikend de dienst van de PDF Generator op de Server van Vensters, soms, meldt de Server van Vensters dat uitvoerbaar een probleem heeft ontmoet en moet sluiten. Het heeft echter geen invloed op de PDF-conversie zoals deze op de achtergrond wordt voortgezet.

Als u wilt voorkomen dat de fout wordt ontvangen, kunt u de rapportage van fouten in Windows uitschakelen. Voor meer informatie over het uitschakelen van foutmeldingen raadpleegt u [https://technet.microsoft.com/en-us/library/cc754364.aspx](https://technet.microsoft.com/en-us/library/cc754364.aspx).

### (Alleen Windows) Conversie van HTML naar PDF configureren {#configure-html-to-pdf-conversion}

De dienst van de PDF Generator verstrekt WebKit, WebCapture, en routes PhantomJS of methodes om de dossiers van HTML in de documenten van PDF om te zetten. Als u in Windows conversie wilt inschakelen voor WebKit- en Acrobat WebCapture-routes, kopieert u het Unicode-font naar de map %windir%\fonts.

>[!NOTE]
>
>Wanneer u nieuwe lettertypen in de map Fonts installeert, start u het AEM Forms-exemplaar opnieuw.

### (Alleen op UNIX gebaseerde platforms) Extra configuraties voor conversie van HTML naar PDF  {#extra-configurations-for-html-to-pdf-conversion}

Op op UNIX-Gebaseerde platforms, steunt de dienst van de PDF Generator WebKit en routes PhantomJS om de dossiers van HTML in de documenten van PDF om te zetten. Om HTML aan PDF omzetting toe te laten, voer de volgende configuraties uit, toepasselijk op uw aangewezen omzettingsroute:

### (Alleen op UNIX gebaseerde platforms) Ondersteuning voor Unicode-lettertypen inschakelen (alleen WebKit) {#enable-support-for-unicode-fonts-webkit-only}

Kopieer het Unicode-lettertype naar een van de volgende mappen, afhankelijk van uw systeem:

* /usr/lib/X11/fonts/TrueType
* /usr/share/fonts/default/TrueType
* /usr/X11R6/lib/X11/fonts/ttf
* /usr/X11R6/lib/X11/fonts/truetype
* /usr/X11R6/lib/X11/fonts/TrueType
* /usr/X11R6/lib/X11/fonts/TTF
* /usr/openwin/lib/X11/fonts/TrueType (Solaris™)

>[!NOTE]
>
>* Op Red Hat® Enterprise Linux® 6.x en hoger zijn de koerierlettertypen niet beschikbaar. Download het zip-archief font-ibm-type1-1.0.3.zip om de koerierlettertypen te installeren. Extraheer het archief op /usr/share/fonts. Maak een symbolische koppeling van /usr/share/X11/fonts naar /usr/share/fonts.
>* Verwijder alle .lst-cachebestanden voor lettertypen uit de mappen HTML2PdfSvc/bin en /usr/share/fonts.
>* Zorg ervoor dat de mappen /usr/lib/X11/fonts en /usr/share/fonts bestaan. Als de mappen niet bestaan, gebruikt u de ln-opdracht om een symbolische koppeling te maken van /usr/share/X11/fonts naar /usr/lib/X11/fonts en een andere symbolische koppeling van /usr/share/fonts naar /usr/share/X11/fonts. Zorg er ook voor dat de koerierlettertypen beschikbaar zijn op /usr/lib/X11/fonts.
>* Zorg ervoor dat alle lettertypen (Unicode en niet-Unicode) beschikbaar zijn in de map /usr/share/fonts of /usr/share/X11/fonts.
>* Wanneer u de dienst van de PDF Generator als niet wortelgebruiker in werking stelt, verstrek de niet wortelgebruiker lees en schrijf toegang tot alle doopvontfolders.
>* Wanneer u nieuwe lettertypen in de map Fonts installeert, start u het AEM Forms-exemplaar opnieuw.
>

## AEM Forms-invoegtoepassing installeren {#install-aem-forms-add-on-package}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Het pakket bevat AEM Forms Document Services en andere AEM Forms-mogelijkheden. Voer de volgende stappen uit om het pakket te installeren:

1. Openen [Softwaredistributie](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteren **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de **[!UICONTROL Filters]** sectie:
   1. Selecteren **[!UICONTROL Forms]** van de **[!UICONTROL Solution]** vervolgkeuzelijst.
   2. Selecteer de versie en typ voor het pakket. U kunt ook de opdracht **[!UICONTROL Search Downloads]** om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem. Selecteer **[!UICONTROL Accept EULA Terms]** en selecteert u **[!UICONTROL Download]**.
1. Openen [Pakketbeheer](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html)  en klik op **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

   U kunt het pakket ook downloaden via de directe koppeling in het dialoogvenster [AEM Forms-releases](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html) artikel.

1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om de AEM opnieuw te starten. **Stop niet onmiddellijk de server.** Voordat u de AEM Forms-server stopt, wacht u tot de niet-geregistreerde ServiceEvent-berichten en de niet-geregistreerde ServiceEvent-berichten niet meer worden weergegeven in de `[AEM-Installation-Directory]/crx-quickstart/logs/error`Het .log-bestand en het logbestand zijn stabiel.

## Configuratie na installatie {#post-installation-configurations}

### Opstartdelegatie configureren voor bibliotheken met RSA/BouncyCastle  {#configure-boot-delegation-for-rsa-bouncycastle-libraries}

1. Stop de AEM instantie. Ga naar de [AEM installatiemap]\crx-quickstart\conf\. Open het bestand sling.properties voor bewerking.

   Als u `[AEM installation directory]\crx-quickstart\bin\start.bat` om een AEM instantie te starten, bewerkt u de eigenschappen sling.property op `[AEM_root]\crx-quickstart\`.

1. Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```shell
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*
   ```

1. (Alleen AIX®) Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```shell
   sling.bootdelegation.xerces=org.apache.xerces.*
   ```

1. Sla het bestand op en sluit het.

### De service voor lettertypebeheer configureren  {#configuring-the-font-manager-service}

1. Aanmelden bij [AEM Configuration Manager](http://localhost:4502/system/console/configMgr) als beheerder.
1. Zoek en open de **[!UICONTROL CQ-DAM-Handler-Gibson Font Managers]** service. Geef het pad op van de systeemlettertypen, de Adobe-serverlettertypen en de directory&#39;s met klantlettertypen. Klik op **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Uw recht om lettertypen te gebruiken die door andere partijen dan Adobe worden verstrekt, wordt geregeld door de licentieovereenkomsten die deze partijen u met die lettertypen verstrekken, en wordt niet gedekt door uw licentie om Adobe software te gebruiken. Adobe raadt u aan na te gaan of u voldoet aan alle toepasselijke licentieovereenkomsten voor niet-Adoben voordat u lettertypen gebruikt die niet van Adobe zijn met Adobe-software, met name voor het gebruik van lettertypen in een serveromgeving.
   >Wanneer u nieuwe lettertypen in de map Fonts installeert, start u het AEM Forms-exemplaar opnieuw.
   >

### Een lokale gebruikersaccount configureren om de service PDF Generator uit te voeren  {#configure-a-local-user-account-to-run-the-pdf-generator-service}

Een lokale gebruikersrekening wordt vereist om de dienst van de PDF Generator in werking te stellen. Ga voor stappen om een lokale gebruiker te maken naar [Een gebruikersaccount maken in Windows](https://support.microsoft.com/en-us/help/13951/windows-create-user-account) of maak een gebruikersaccount op UNIX-gebaseerde platforms.

1. Open de [Configuratie AEM Forms PDF Generator](http://localhost:4502/libs/fd/pdfg/config/ui.html) pagina.

1. In de **[!UICONTROL User Accounts]** , geeft u de gegevens van een lokale gebruikersaccount op en klikt u op **[!UICONTROL Submit]**. Als Microsoft® Windows daarom vraagt, geeft u de gebruiker toegang. Wanneer met succes toegevoegd, wordt de gevormde gebruiker getoond onder **[!UICONTROL Your user accounts]** in de **[!UICONTROL User Accounts]** tab.

### De time-outinstellingen configureren {#configure-the-time-out-settings}

1. In [AEM](http://localhost:4502/system/console/configMgr), zoekt en opent u de **[!UICONTROL Jacorb ORB Provider]** service.

   Voeg het volgende toe aan de **[!UICONTROL Custom Properties.name]** veld en klik op **[!UICONTROL Save]**. De wachtende antwoordtime-out (ook wel CORBA-clienttime-out genoemd) wordt ingesteld op 600 seconden.

   `jacorb.connection.client.pending_reply_timeout=600000`

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Configure PDF Generator]**. De standaard-URL is <http://localhost:4502/libs/fd/pdfg/config/ui.html>.

   Open de **[!UICONTROL General Configuration]** en wijzigt u de waarde van de volgende velden voor uw omgeving:

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
   <td>Duur waarvoor de dienst van de PDF Generator wordt toegestaan om een omzetting in werking te stellen. Zorg ervoor dat de waarde van de Seconden van de Vervaltijd van de Baan groter is dan de waarde van de Seconden van de Schoonmaakactie PDFG.</td>
   <td>7200 seconden</td>
  </tr>
 </tbody>
</table>

### (Alleen Windows) Acrobat configureren voor de service PDF Generator {#configure-acrobat-for-the-pdf-generator-service}

In Microsoft® Windows gebruikt de service PDF Generator Adobe Acrobat om ondersteunde bestandsindelingen te converteren naar een PDF-document. Voer de volgende stappen uit om Adobe Acrobat voor de dienst van de PDF Generator te vormen:

1. Open Acrobat en selecteer **[!UICONTROL Edit]**> **[!UICONTROL Preferences]**> **[!UICONTROL Updater]**. Schakel in Controleren op updates de optie **[!UICONTROL Automatically install updates]** en klik op **[!UICONTROL OK]**. Sluit Acrobat.
1. Dubbelklik op een PDF-document op uw systeem. Wanneer Acrobat voor de eerste keer wordt gestart, worden de dialoogvensters Aanmelden, Welkomstscherm en EULA weergegeven. Deze dialoogvensters sluiten voor alle gebruikers die zijn geconfigureerd om PDF Generator te gebruiken.
1. Voer het batchbestand van het hulpprogramma PDF Generator uit om Acrobat voor de service PDF Generator te configureren:

   1. Openen [AEM Package Manager](http://localhost:4502/crx/packmgr/index.jsp) en download de `adobe-aemfd-pdfg-common-pkg-[version].zip` in Package Manager.
   1. Pak het gedownloade .zip-bestand uit. Open de opdrachtprompt met beheerdersrechten.
   1. Ga naar de `[extracted-zip-file]\jcr_root\etc\packages\day\cq60\fd\adobe-aemds-common-pkg-[version]\jcr_root\etc\packages\day\cq60\fd\`
   1. Pak de `adobe-aemfd-pdfg-common-pkg-[version]`.
   1. Ga naar de `[downloaded-adobe-aemfd-pdfg-common-pkg]\jcr_root\libs\fd\pdfg\tools\adobe-aemfd-pdfg-utilities-[version]` directory. Voer het volgende batchbestand uit:

      `Acrobat_for_PDFG_Configuration.bat`

      Acrobat is geconfigureerd om te worden uitgevoerd met de service PDF Generator.

1. Uitvoeren [Systeemgereedheid (SRT)](#SRT) om de installatie van Acrobat te valideren.

### (Alleen Windows) Vorm primaire route voor conversie van HTML naar PDF {#configure-primary-route-for-html-to-pdf-conversion-windows-only}

De dienst van de PDF Generator verstrekt veelvoudige routes om de dossiers van HTML in de documenten van PDF om te zetten: Webkit, Acrobat WebCapture (Vensters slechts), en PhantomJS. Adobe raadt u aan de PhantomJS-route te gebruiken, omdat deze de mogelijkheid heeft om dynamische inhoud af te handelen en geen afhankelijkheden heeft met 32-bits bibliotheken of geen extra lettertypen nodig heeft. Ook, vereist de route PhantomJS sudo of worteltoegang niet om de omzetting in werking te stellen.

De standaard primaire route voor HTML aan PDF omzetting is Webkit. De omzettingsroute wijzigen:

1. Navigeer in AEM auteurinstantie naar **[!UICONTROL Tools]**> **[!UICONTROL Forms]**> **[!UICONTROL Configure PDF Generator]**.

1. In de **[!UICONTROL General Configuration]** tabblad selecteert u de voorkeursconversieroute in het dialoogvenster **[!UICONTROL Primary Route for HTML to PDF conversions]** vervolgkeuzelijst.

### Global Trust Store initialiseren {#intialize-global-trust-store}

Met het Betrouwbaarheidsopslagbeheer kunt u certificaten die u op de server vertrouwt, importeren, bewerken en verwijderen voor validatie van digitale handtekeningen en certificaatverificatie. U kunt om het even welk aantal certificaten invoeren en uitvoeren. Nadat een certificaat is geïmporteerd, kunt u de vertrouwensinstellingen bewerken en het type vertrouwde opslag vertrouwen. Voer de volgende stappen uit om een vertrouwde opslag te initialiseren:

1. Meld u als beheerder aan bij een AEM Forms-instantie.
1. Ga naar  **[!UICONTROL Tools]** >  **[!UICONTROL Security]** >  **[!UICONTROL Trust Store]**.
1. Klikken  **[!UICONTROL Create TrustStore]**. Wachtwoord instellen en selecteren **[!UICONTROL Save]**.

### Certificaten instellen voor de extensie en coderingsservice van Readers {#set-up-certificates-for-reader-extension-and-encryption-service}

De dienst DocAssurance kan gebruiksrechten toepassen op PDF documenten. Als u gebruiksrechten wilt toepassen op PDF-documenten, configureert u de certificaten.

Voordat u de certificaten instelt, moet u controleren of u beschikt over:

* Certificaatbestand (.pfx).

* Wachtwoord voor persoonlijke sleutel dat bij het certificaat wordt geleverd.

* Alias persoonlijke sleutel. U kunt de Java-opdracht Keytool uitvoeren om de alias Persoonlijke sleutel weer te geven:
  `keytool -list -v -keystore [keystore-file] -storetype pkcs12`

* Wachtwoord sleutelarchiefbestand. Als u het certificaat van de Uitbreidingen van de Reader van de Adobe gebruikt, is het keystore dossierwachtwoord altijd het zelfde als Persoonlijke Zeer belangrijke wachtwoord.

Voer de volgende stappen uit om de certificaten te configureren:

1. Meld u als beheerder aan bij AEM instantie Auteur. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]**.
1. Klik op de knop **[!UICONTROL name]** van de gebruikersaccount. De **[!UICONTROL Edit User Settings]** pagina wordt geopend. Voor de AEM instantie van de Auteur, verblijven de certificaten in een KeyStore. Als u nog geen KeyStore hebt gemaakt, klikt u op **[!UICONTROL Create KeyStore]** en stel een nieuw wachtwoord in voor de KeyStore. Als de server al een KeyStore bevat, slaat u deze stap over.  Als u het certificaat van de Uitbreidingen van de Reader van de Adobe gebruikt, is het keystore dossierwachtwoord altijd het zelfde als Persoonlijke Zeer belangrijke wachtwoord.
1. Op de **[!UICONTROL Edit User Settings]** pagina, selecteert u de **[!UICONTROL KeyStore]** tab. Breid uit **[!UICONTROL Add Private Key from Key Store file]** en geef een alias op. De alias wordt gebruikt om de bewerking Reader Extensions uit te voeren.
1. Klik op **[!UICONTROL Select Key Store File]** en uploaden een &lt;filename>.pfx-bestand.

   Voeg de **[!UICONTROL Key Store Password]**, **[!UICONTROL Private Key Password]**, en **[!UICONTROL Private Key Alias]** die is gekoppeld aan het certificaat aan de desbetreffende velden. Klik op **[!UICONTROL Submit]**.

   >[!NOTE]
   >
   >In het productiemilieu, vervang uw evaluatiegeloofsbrieven met productiereferenties. Zorg ervoor dat u uw oude geloofsbrieven van de Uitbreidingen van de Reader schrapt, alvorens een verlopen of evaluatiereferentie bij te werken.

1. Klik op **[!UICONTROL Save & Close]** op de pagina **[!UICONTROL Edit User Settings]**.

### AES-256 inschakelen {#enable-aes}

Als u AES 256-versleuteling wilt gebruiken voor PDF-bestanden, moet u de JCE-bestanden (Unlimited Strength Rechtdiction Policy) (Java Cryptography Extension) ophalen en installeren. Vervang de bestanden local_policy.jar en US_export_policy.jar in de map jre/lib/security. Als u bijvoorbeeld Sun JDK gebruikt, kopieert u de gedownloade bestanden naar de `[JAVA_HOME]/jre/lib/security` map.

De dienst van de Assembler hangt van de dienst van de Uitbreidingen van de Reader, de dienst van de Handtekening, de dienst van Forms, en de dienst van de Output af. Voer de volgende stappen uit om te verifiëren dat de vereiste diensten in gebruik zijn:

1. Aanmelden bij URL `https://'[server]:[port]'/system/console/bundles` als beheerder.
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
   <td>Reader Extensions-service</td>
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

### (Alleen Windows) Registervermelding configureren voor Microsoft® Project {#configure-registry-entry-for-microsoft-project}

Nadat u de invoegtoepassing AEM Forms en het Microsoft®-project op uw computer hebt geïnstalleerd, registreert u een vermelding voor het Microsoft®-project op de 64-bits locatie. Het vergemakkelijkt de uitvoering van project aan PDFG omzettingstests. Hieronder volgen de stappen waarin het registratieproces wordt beschreven:

1. Open de Register-editor van Microsoft® Windows (regedit), ga naar Start > Uitvoeren om de registereditor te openen, typ regedit en klik op OK.
1. Navigeren naar `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Adobe\Acrobat PDFMaker\<version>\Office\SupportedApp`en een nieuwe **Binaire waarde** registreren en naam ervan wijzigen in **Project**.
1. Wijzig de gegevenswaarde van gecreeerd Binair register in 01 en klik O.K.
1. Sluit de registervermelding.


## Bekende problemen en problemen oplossen {#known-issues-and-troubleshooting}

* De conversie van HTML naar PDF mislukt als een gecomprimeerd invoerbestand HTML-bestanden bevat met double-bytetekens in bestandsnamen. U voorkomt dit door geen double-bytetekens te gebruiken bij de naamgeving van HTML-bestanden.

* Op UNIX-besturingssystemen vindt u de volgende handelingen om ontbrekende bibliotheken te zoeken:

1. Navigeren naar `[crx-repository]/bedrock/svcnative/HtmlToPdfSvc/bin/`.

1. Voer de volgende opdracht uit om alle bibliotheken weer te geven die PhantomJS nodig heeft voor conversie van HTML naar PDF.

   `ldd phantomjs`

   Voer de volgende opdracht uit om ontbrekende bibliotheken weer te geven.

   `ldd phantomjs | grep not`

1. De ontbrekende bibliotheken handmatig installeren.

## Systeemgereedheid (SRT) {#SRT}

De [Gereedschap Systeem](#srt-configuration) controleert of de machine behoorlijk wordt gevormd om de omzettingen van de PDF Generator in werking te stellen. Het hulpmiddel produceert rapport bij de gespecificeerde weg. Het gereedschap uitvoeren:

1. Opdrachtprompt openen. Ga naar de `[extracted-adobe-aemfd-pdfg-common-pkg]\jcr_root\libs\fd\pdfg\tools` map.

1. Voer het volgende bevel van de bevelherinnering in werking:

   `java -jar forms-srt-[version].jar [Path_of_reports_folder] en`

   Het bevel produceert rapport en leidt ook tot het srt_config.yaml- dossier. U kunt het gebruiken om opties voor het hulpmiddel te vormen SRT. Het is facultatief om opties voor het hulpmiddel te vormen SRT.

   >[!NOTE]
   >
   >* Als het Hulpmiddel van de Gereedheid van het Systeem meldt dat het pdfgen.api- dossier niet beschikbaar in de Acrobat stop-ins omslag is, dan kopieer het pdfgen.api- dossier van het `[extracted-adobe-aemfd-pdfg-common-pkg]\jcr_root\libs\fd\pdfg\tools\adobe-aemfd-pdfg-utilities-[version]\plugins\x86_win32` aan de `[Acrobat_root]\Acrobat\plug_ins` directory.

1. Navigeren naar `[Path_of_reports_folder]`. Open het bestand SystemReadyTool.html. Verifieer het rapport en los de bovengenoemde kwesties op.

### Opties configureren voor het SRT-gereedschap {#srt-configuration}

U kunt het srt_config.yaml- dossier gebruiken om diverse montages voor het hulpmiddel te vormen SRT. De bestandsindeling is:

```shell
   # =================================================================
   # SRT Configuration
   # =================================================================
   #Note - follow correct format to avoid parsing failures
   #for example, <param name>:<space><param value> 
   #locale: (mandatory field)Locale to be used for SRT. Supported locales [en/fr/de/ja].
   locale: en
   
   #aemTempDir: AEM Temp direcotry
   aemTempDir:
   
   #users: provide PDFG converting users list
   #users:
   # - user1
   # - user2
   users:
   
   #profile: select profile to run specific checks. Choose from [LCM], more will be added soon 
   profile:
   
   #outputDir: directory where output files will be saved
   outputDir:
```

* **Landinstelling:** Het is een verplichte parameter. De klasse biedt ondersteuning voor Engels(en), Duits (de), Frans (fr) en Japans(ja). De standaardwaarde is en. Het heeft geen gevolgen voor de diensten van de PDF Generator die op AEM Forms lopen op OSGi.
* **aemTempDir:** Het is een optionele parameter. Hiermee wordt de tijdelijke opslaglocatie van Adobe Experience Manager opgegeven.
* **gebruikers:** Het is een optionele parameter. U kunt een gebruiker specificeren om te controleren of de gebruiker toestemmingen en lees/schrijf toegang op folders heeft die worden vereist om PDF Generator in werking te stellen. Als geen gebruiker wordt gespecificeerd, worden de gebruiker-specifieke controles overgeslagen en getoond zoals ontbroken in het rapport.
* **outputDir:** Specificeer de plaats om het SRT- rapport te bewaren. De standaardplaats is de huidige het werk folder van het hulpmiddel SRT.

## Problemen oplossen

Als u problemen zelfs na het bevestigen van alle die problemen door het hulpmiddel van SRT wordt gemeld, voer de volgende controles uit:

Controleer voordat u de volgende controles uitvoert of [Gereedschap Systeem](#SRT) geen fout rapporteert.

+++ Adobe Acrobat

* Alleen controleren [ondersteunde versie](aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) van Microsoft® Office (32-bits) en Adobe Acrobat is geïnstalleerd en het openen van dialoogvensters wordt geannuleerd.
* Controleer of Adobe Acrobat Update Service is uitgeschakeld.
* Zorg ervoor dat de [Acrobat_for_PDFG_Configuration.bat](#configure-acrobat-for-the-pdf-generator-service) batchbestand is uitgevoerd met beheerdersrechten.
* Zorg ervoor dat een gebruiker van de PDF Generator wordt toegevoegd in de configuratie-UI van de PDF.
* Zorg ervoor dat de [Een token op procesniveau vervangen](#grant-the-replace-a-process-level-token-privilege) Deze machtiging wordt toegevoegd voor de gebruiker van de PDF Generator.
* Zorg ervoor dat de COM-invoegtoepassing Acrobat PDFMaker Office is ingeschakeld voor Microsoft Office-toepassingen.

+++

+++OpenOffice

**Microsoft® Windows**

* Zorg ervoor dat 32 bits [ondersteunde versie](aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) van Microsoft Office is geïnstalleerd en het openen van dialoogvensters wordt voor alle toepassingen geannuleerd.
* Zorg ervoor dat een gebruiker van de PDF Generator wordt toegevoegd in de configuratie-UI van de PDF.
* Zorg ervoor dat de gebruiker van de PDF Generator lid is van de beheerdersgroep en de [Een token op procesniveau vervangen](#grant-the-replace-a-process-level-token-privilege) bevoegdheden wordt ingesteld voor de gebruiker.
* Zorg ervoor dat de gebruiker in PDF Generator UI wordt gevormd en voert de volgende acties uit:
   1. Meld u aan bij de Microsoft® Windows met PDF Generator gebruiker.
   1. Open Microsoft® Office of OpenOffice toepassingen en annuleer alle dialoogvensters.
   1. Stel Adobe PDF in als standaardprinter.
   1. Acrobat instellen als standaardprogramma voor PDF-bestanden.
   1. Handmatige omzetting uitvoeren met de opties Bestand > Afdrukken en Acrobat in Microsoft Office-toepassingen en alle dialoogvensters annuleren.
   1. Beëindig alle processen met betrekking tot omzetting zoals winword.exe, powerpoint.exe, en excel.exe.
   1. Start de AEM Forms-server opnieuw.

**Linux®**

* Installeer de [ondersteunde versie](aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) van OpenOffice. AEM Forms ondersteunt zowel 32-bits als 64-bits versies. Na het installeren, open alle toepassingen OpenOffice, annuleer alle dialoogvensters, en sluit de toepassingen. Open de toepassingen opnieuw en controleer of er geen dialoogvenster wordt weergegeven wanneer u een OpenOffice-toepassing opent.

* Een omgevingsvariabele maken `OpenOffice_PATH` en deze zo instellen dat deze naar de OpenOffice-installatie wijst, is ingesteld in het dialoogvenster [console](https://linuxize.com/post/how-to-set-and-list-environment-variables-in-linux/) of het dt-profiel (apparaatstructuur).
* Als er problemen zijn met de installatie van OpenOffice, controleert u of [32-bits bibliotheken](#extrarequirements) is vereist voor OpenOffice-installatie.

+++

+++HTML naar aanleiding van problemen met PDF-conversie

* Zorg ervoor dat de folders van doopvonten in PDF Generator config UI worden toegevoegd.

**Linux en Solaris (PhantomJS conversieroute)**

* Zorg ervoor dat er een 32-bits bibliotheek beschikbaar is (libicudata.so.42) voor HTMLToPDF-conversie op basis van Webkit en 64-bits (libicudata.so.42 libs zijn beschikbaar voor HTMLToPDF-conversie op basis van PhantomJS.

* Voer de volgende opdracht uit om ontbrekende bibliotheken voor fantoomjs weer te geven:

  ```
  ldd phantomjs | grep not
  ```

**Linux® en Solaris™ (WebKit conversieroute)**

* Ervoor zorgen dat de mappen `/usr/lib/X11/fonts` en `/usr/share/fonts` bestaan. Als de mappen niet bestaan, maakt u een symbolische koppeling op basis van `/usr/share/X11/fonts` tot `/usr/lib/X11/fonts` en een andere symbolische koppeling van `/usr/share/fonts` tot `/usr/share/X11/fonts`.

  ```
  ln -s /usr/share/fonts /usr/share/X11/fonts
  
  ln -s /usr/share/X11/fonts /usr/lib/X11/fonts
  ```

* Zorg ervoor dat IBM-lettertypen worden gekopieerd onder usr/share/fonts.
* Zorg ervoor dat glibc voor GGGL-kwetsbaarheidsprobleem met spook beschikbaar is op de computer. Gebruik uw standaardpakketbeheer om bij te werken naar de nieuwste versie van glibc. Dit omvat het verhelpen van spookkwetsbaarheden.
* Zorg ervoor dat de nieuwste versies van 32-bits bibliotheken met lib-curl, libcrypto en libssl op het systeem zijn geïnstalleerd. Ook symlinks maken `/usr/lib/libcurl.so` (of libcurl.a voor AIX®), `/usr/lib/libcrypto.so` (of libcrypto.a voor AIX®) en `/usr/lib/libssl.so` (of libssl.a voor AIX®) wijzend naar de recentste versies (32 bits) van respectieve bibliotheken.

* Voer de volgende stappen uit voor IBM® SSL Socket provider:
   1. Kopieer het bestand java.security van `<WAS_Installed_JAVA>\jre\lib\security` naar een willekeurige locatie op uw AEM Forms-server. De standaardlocatie is = `<WAS_Installed>\Appserver\java_[version]\jre\lib\security`.

   1. Bewerk het bestand java.security op de gekopieerde locatie en wijzig de standaard SSL Socket-fabrieken met JSSE2-fabrieken (gebruik JSSE2-fabrieken in plaats van WebSphere®).

      Wijzig de volgende standaard JSSE-socketfabrieken:

      ```
      #ssl.SocketFactory.provider=com.ibm.jsse2.SSLSocketFactoryImpl
      #ssl.ServerSocketFactory.provider=com.ibm.jsse2.SSLServerSocketFactoryImpl
      WebSphere socket factories (in cryptosf.jar)
      ssl.SocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLSocketFactory
      ssl.ServerSocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLServerSocketFactory
      ```

      with

      ```
      ssl.SocketFactory.provider=com.ibm.jsse2.SSLSocketFactoryImpl
      ssl.ServerSocketFactory.provider=com.ibm.jsse2.SSLServerSocketFactoryImpl
      WebSphere socket factories (in cryptosf.jar)
      #ssl.SocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLSocketFactory
      #ssl.ServerSocketFactory.provider=com.ibm.websphere.ssl.protocol.SSLServerSocketFactory
      ```

+++

+++ Kan geen PDF Generator (PDFG)-gebruiker toevoegen

* Zorg ervoor dat Microsoft® Visual C++ 2012 x86 en Microsoft® Visual C++ 2013 x86 (32-bits) opnieuw distribueerbaar zijn geïnstalleerd in Windows.

+++

+++Fouten in de automatiseringstest

* Voer voor Microsoft® Office en OpenOffice ten minste één omzetting handmatig uit (als elke gebruiker) om ervoor te zorgen dat er geen dialoogvenster verschijnt tijdens de conversie. Als er een dialoogvenster verschijnt, wordt dit gesloten. Een dergelijk dialoogvenster wordt niet weergegeven tijdens automatische conversie.

* Voordat u automatisering uitvoert op een AEM Forms in een OSGi-omgeving, moet u controleren of het testpakket is geïnstalleerd en actief is.

+++

+++Meerdere omzettingsfouten voor gebruikers

* Verifieer de serverlogboeken om te controleren of de omzetting voor een bepaalde gebruiker ontbreekt.(De Ontdekkingsreiziger van het Proces kan u helpen het lopende proces voor verschillende gebruikers controleren)

* Zorg ervoor dat de gebruiker die voor PDF Generator is geconfigureerd lokale beheerdersrechten heeft.

* Zorg ervoor dat de gebruiker van de PDF Generator lees-, schrijf- en uitvoermachtigingen heeft voor gebruikers van de temp van LC en PDFG.

* Voer voor Microsoft® Office en OpenOffice ten minste één omzetting handmatig uit (als elke gebruiker) om ervoor te zorgen dat er geen dialoogvenster verschijnt tijdens de conversie. Als er een dialoogvenster verschijnt, wordt dit gesloten. Een dergelijk dialoogvenster wordt niet weergegeven tijdens automatische conversie.

* Voer een steekproefomzetting uit.

+++

+++Licentie van Adobe Acrobat geïnstalleerd op AEM Forms Server verloopt.

* Als u een bestaande licentie van Adobe Acrobat hebt en deze is verlopen, [Download de nieuwste versie van Adobe Application Manager](https://helpx.adobe.com/in/creative-suite/kb/aam-troubleshoot-download-install.html)en het migreren van uw serienummer. Voor [serienummer migreren](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/licensing.html#migrating-your-serial-number).

   * Gebruik de volgende opdrachten om prov.xml te genereren en de bestaande installatie opnieuw te erialiseren met behulp van het bestand prov.xml in plaats van de opdrachten in [serienummer migreren](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/licensing.html#migrating-your-serial-number) nummerartikel.

         &quot;
         
         adobe_prtk —tool=VolumeSerialize —generate —serial=&lt;serialnum> [—leid=&lt;leid>] [—regsuppress=ss] [—eulasuppress] [—locales=limited list van landinstellingen in xx_XX formaat of ALL>] [—provfile=&lt;absolute path=&quot;&quot; to=&quot;&quot; prov.xml=&quot;&quot;>]
         
         &quot;
     
   * Het volume rangschikt het pakket (re-serialize de bestaande installatie gebruikend het prov.xml- dossier en nieuwe serie): stel het volgende bevel van de PRTK installatiemap als beheerder in werking om de opgestelde pakketten op cliëntmachines in series te vervaardigen en te activeren:

         &quot;
         adobe_prtk —tool=VolumeSerialize —provfile=C:\prov.xml -stream
         
         &quot;
     
* Voor grootschalige installaties gebruikt u de opdracht [Acrobat Customization Wizard](https://www.adobe.com/devnet-docs/acrobatetk/tools/Wizard/index.html) eerdere versies van Reader en Acrobat verwijderen. Pas het installatieprogramma aan en implementeer het op alle computers van uw organisatie.

+++

+++ AEM Forms Server bevindt zich in een offline- of beveiligde omgeving en het internet is niet beschikbaar om Acrobat te activeren.

* U kunt binnen 7 dagen na de eerste keer dat u uw product voor de Adobe hebt gestart online gaan om een online activering en registratie te voltooien of een apparaat met internetverbinding en het serienummer van uw product gebruiken om dit proces te voltooien. Zie voor gedetailleerde instructies [Offlineactivering](https://exception.licenses.adobe.com/aoes/aoes/v1/t1?locale=en).

+++

+++ Kan Word- of Excel-bestand niet converteren naar PDF op Windows Server

Wanneer de gebruiker Word- of Excel-bestanden naar PDF probeert om te zetten op Microsoft Windows Server, wordt de volgende fout aangetroffen:

*Foutbericht van de primaire converter: ALC-PDG-015-003-Het systeem kan het invoerbestand niet openen. Verzend het bestand opnieuw of neem contact op met de systeembeheerder.*

Ga voor een oplossing van het probleem naar [Kan Word- of Excel-bestand niet converteren naar PDF op Windows Server](/help/forms/using/disable-uac-for-pdfgconfiguration.md).

+++

+++ Kan Excel-bestanden niet converteren naar PDF op Windows Server 2019

Wanneer u Microsoft Excel 2019 omzet in PDF op de Server 2019 van Microsoft Windows, moet u het volgende verzekeren:

* Tijdens het gebruiken van de dienst van de PDF Generator, zou uw machine van Vensters geen actieve verre verbinding met de AEM server (de zitting van RDP van Vensters) moeten hebben.
* De standaardprinter moet op Adobe PDF worden ingesteld.

  >[!NOTE]
  >* Voor Apple macOS en Ubuntu OS hoeft u de bovenstaande instellingen niet te configureren.

+++

+++ Kan XPS-bestanden niet omzetten in PDF

Om het probleem op te lossen, [creeer een eigenschap-specifieke registratiesleutel op Vensters](https://helpx.adobe.com/in/acrobat/kb/unable-convert-xps-to-pdfs.html).

+++


## Volgende stappen {#next-steps}

U hebt een werkende AEM Forms-omgeving voor documentservices. U kunt documentservices gebruiken via:

* [Centrische workflows van formulieren op OSGi](/help/forms/using/aem-forms-workflow.md)
* [Gecontroleerde mappen](/help/forms/using/watched-folder-in-aem-forms.md)
* [API&#39;s voor documentservices](/help/forms/using/aem-document-services-programmatically.md)
