---
title: Documentservices installeren en configureren
description: Installeer AEM Forms-documentservices voor het maken, samenstellen, distribueren, archiveren van PDF-documenten, het toevoegen van digitale handtekeningen om de toegang tot documenten te beperken en het decoderen van Barcoded Forms.
topic-tags: installing
role: Admin, User, Developer
exl-id: 5d48e987-16c2-434b-8039-c82181d2e028
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication
source-git-commit: f1fc8554b35d7d9c152023a6b9094e31c1b49807
workflow-type: tm+mt
source-wordcount: '5649'
ht-degree: 0%

---

# Documentservices installeren en configureren {#installing-and-configuring-document-services}

AEM Forms biedt een set OSGi-services voor het uitvoeren van verschillende bewerkingen op documentniveau, zoals services voor het maken, samenstellen, distribueren en archiveren van PDF-documenten, het toevoegen van digitale handtekeningen om de toegang tot documenten te beperken en het decoderen van Barcoded Forms. Deze services zijn opgenomen in het invoegpakket voor AEM Forms. Deze services worden gezamenlijk documentservices genoemd. De lijst met beschikbare documentservices en hun belangrijkste mogelijkheden is als volgt:

* **de dienst van de Assembler:** laat u toe om, PDF en documenten te combineren opnieuw te rangschikken en uit te breiden XDP en informatie over de documenten van PDF te verkrijgen. Het programma helpt ook bij het converteren en valideren van PDF-documenten naar PDF/A-standaard, het transformeren van PDF forms, XML-formulieren en PDF forms naar PDF/A-1b, PDF/A-2b en PDFA/A-3b. Voor meer informatie, zie [ Dienst van de Assembler ](/help/forms/using/assembler-service.md).

* **de dienst ConvertPDF:** laat u toe om de documenten van PDF in PostScript of beelddossiers (JPEG, JPEG 2000, PNG, en TIFF) om te zetten. Voor meer informatie, zie [ Dienst ConvertPDF ](/help/forms/using/using-convertpdf-service.md).

* **Barcoded dienst van Forms:** laat u toe om gegevens uit elektronische beelden van streepjescodes te halen. De service accepteert TIFF- en PDF-bestanden die een of meer streepjescodes als invoer bevatten en extraheert de streepjescodegegevens. Voor meer informatie, zie [ Gecodeerde Dienst van Forms ](/help/forms/using/using-barcoded-forms-service.md).

* **de dienst van DocAssurance:** laat u toe om documenten te coderen en te decrypteren, de functionaliteit van de Lezer van Adobe met extra gebruiksrechten uit te breiden, en digitale handtekeningen aan uw documenten toe te voegen. De Doc Assurance-service bevat drie services: handtekening, versleuteling en reader-extensie. Voor meer informatie, zie [ DocAssurance Service ](/help/forms/using/overview-aem-document-services.md).

* **de dienst van de Encryptie:** laat u toe om documenten te coderen en te decrypteren. Wanneer een document wordt versleuteld, wordt de inhoud ervan onleesbaar. Een geautoriseerde gebruiker kan het document decoderen om toegang tot de inhoud te krijgen. Voor meer informatie, zie [ Dienst van de Encryptie ](/help/forms/using/overview-aem-document-services.md#encryption-service).

* **de dienst van Forms:** laat u interactieve gegevens tot stand brengen vangen cliënttoepassingen die bevestigen, verwerken, transformeren, en leveren vormen die typisch in Forms Designer worden gecreeerd. De Forms-service geeft elk formulierontwerp dat u ontwikkelt, weer in PDF-documenten. Voor meer informatie, zie [ Dienst van Forms ](/help/forms/using/forms-service.md).

* **de dienst van de Output:** laat u toe om documenten in verschillende formaten, met inbegrip van PDF, de formaten van de laserprinter, en de formaten van de etiketprinter tot stand te brengen. Laserprinterindelingen zijn PostScript en Printer Control Language (PCL). Voor meer informatie, zie [ Dienst van de Output ](/help/forms/using/output-service.md).

* **de dienst van PDF Generator:** de dienst van PDF Generator verstrekt APIs om inheemse dossierformaten in PDF om te zetten. PDF wordt ook geconverteerd naar andere bestandsindelingen en de grootte van PDF-documenten wordt geoptimaliseerd. Voor meer informatie, zie [ Dienst van PDF Generator ](aem-document-services-programmatically.md#pdfgeneratorservice).

* **de dienst van de Uitbreiding van Reader:** laat uw organisatie toe om interactieve documenten van PDF gemakkelijk te delen door de functionaliteit van de Lezer van Adobe met extra gebruiksrechten uit te breiden. De service activeert functies die niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Reader, zoals het toevoegen van opmerkingen aan een document, het invullen van formulieren en het opslaan van het document. Voor meer informatie, zie [ de Dienst van de Uitbreiding van Reader ](/help/forms/using/overview-aem-document-services.md#reader-extension-service).

* **de dienst van de Handtekening:** laat u met digitale handtekeningen en documenten op de server van AEM werken. De service Handtekening wordt bijvoorbeeld doorgaans in de volgende situaties gebruikt:

   * De AEM-server certificeert een formulier voordat het naar een gebruiker wordt verzonden om te worden geopend met Acrobat of Adobe Reader.
   * De AEM-server valideert een handtekening die aan een formulier is toegevoegd met Acrobat of Adobe Reader.
   * De AEM-server ondertekent een formulier namens een openbare notaris.

  De handtekeningsdienst heeft toegang tot certificaten en geloofsbrieven die in de vertrouwde opslag worden opgeslagen. Voor meer informatie, zie [ Dienst van de Handtekening ](/help/forms/using/aem-document-services-programmatically.md).

AEM Forms is een krachtig platform op bedrijfsniveau en de documentservices zijn slechts een van de mogelijkheden van AEM Forms. Voor de volledige lijst van mogelijkheden, zie [ Inleiding aan AEM Forms ](/help/forms/using/introduction-aem-forms.md).

## Implementatietopologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Over het algemeen hebt u slechts één AEM-exemplaar (auteur of publicatie) nodig om AEM Forms-documentservices uit te voeren. De volgende topologie wordt geadviseerd om de documentdiensten van AEM Forms in werking te stellen. Voor gedetailleerde informatie over topologieën, zie [ Architectuur en plaatsingstopologieën voor AEM Forms ](/help/forms/using/aem-forms-architecture-deployment.md).

![ Architectuur en plaatsingstopologieën voor AEM Forms ](do-not-localize/document-services.png)

>[!NOTE]
>
>Hoewel u met AEM Forms alle functies van één server kunt instellen en uitvoeren, moet u capaciteitsplanning uitvoeren, taakverdeling toepassen en specifieke servers instellen voor specifieke mogelijkheden in een productieomgeving. Voor een omgeving die bijvoorbeeld gebruikmaakt van de PDF Generator-service voor het converteren van duizenden pagina&#39;s per dag en van meerdere adaptieve formulieren voor het vastleggen van gegevens, stelt u afzonderlijke AEM Forms-servers in voor de PDF Generator-service en de mogelijkheden voor adaptieve formulieren. Het helpt optimale prestaties te bieden en de servers onafhankelijk van elkaar te schalen.

## Systeemvereisten {#system-requirements}

Voordat u de documentservices van AEM Forms gaat installeren en configureren, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Voor een gedetailleerde lijst van gesteunde hardware en software, zie [ technische vereisten ](/help/sites-deploying/technical-requirements.md).

* Het installatiepad van de AEM-instantie bevat geen spaties.
* Een AEM-instantie wordt uitgevoerd. In AEM-terminologie is een &quot;instantie&quot; een kopie van AEM die wordt uitgevoerd op een server in de auteur- of publicatiemodus. Over het algemeen hebt u slechts één AEM-exemplaar (auteur of publicatie) nodig om AEM Forms-documentservices uit te voeren:

   * **Auteur**: Een instantie van AEM die wordt gebruikt om, inhoud tot stand te brengen te uploaden en uit te geven en de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **publiceer**: Een instantie van AEM die de gepubliceerde inhoud aan het publiek over Internet of een intern netwerk dient.

* Er wordt voldaan aan de geheugenvereisten. AEM Forms-add-on-pakket vereist:

   * 15 GB tijdelijke ruimte voor Microsoft® Windows-installaties.
   * 6 GB tijdelijke ruimte voor UNIX-installaties.

* Clientsoftware die vereist is voor conversie door PDF-producenten op Microsoft® Windows en Linux®, is geïnstalleerd:

   * **Microsoft® Vensters**: Installeer [ Microsoft® Bureau ](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p) of [ Apache OpenOffice ](/help/forms/using/aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator)
   * **Linux®**: Installeer [ Apache OpenOffice ](/help/forms/using/aem-forms-jee-supported-platforms.md#p-software-support-for-pdf-generator-p)

>[!NOTE]
>
>* In Microsoft® Windows biedt PDF Generator ondersteuning voor WebKit, Acrobat WebCapture en WebToPDF-conversieroutes voor het converteren van HTML-bestanden naar PDF-documenten.
>* Op UNIX-besturingssystemen ondersteunt PDF Generator WebKit- en WebToPDF-conversieroutes voor het converteren van HTML-bestanden naar PDF-documenten.
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

* **(Alleen PDF Generator** ) Installeer de 32-bits versie van bibliotheken met libcurl, libcrypto en libssl en maak de onderstaande koppelingen. De symlinks verwijzen naar de meest recente versie van de respectievelijke bibliotheken:

   * /usr/lib/libcurl.so
   * /usr/lib/libcrypto.so
   * /usr/lib/libssl.so

* **(Alleen PDF Generator)** PDF Generator-service ondersteunt WebKit- en WebToPDF-routes voor het converteren van HTML-bestanden naar PDF-documenten. Als u conversie voor WebToPDF-route wilt inschakelen, installeert u de onderstaande 64-bits bibliotheken. Over het algemeen zijn deze bibliotheken al geïnstalleerd. Als er een bibliotheek ontbreekt, installeert u deze handmatig:

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
* (Alleen PDF Generator) Om WebKit-route in te schakelen bij RHEL 8- of RHEL 9-instellingen, is de 32-bits `nspr` bibliotheek mogelijk niet standaard beschikbaar. Installeer deze bibliotheek als deze niet aanwezig is.

* (Alleen PDF Generator) Als de WebToPDF-conversie mislukt op de Unix®-server met de volgende fout:

  ```Auto configuration failed 4143511872:error:0E079065:configuration file routines:DEF_LOAD_BIO:missing equal sign:conf_def.c:362:line 57```
Stel vervolgens de volgende omgevingsvariabele in en start de server opnieuw:
  `OPENSSL_CONF=/etc/ssl`

>[!NOTE]
>
> WebToPDF wordt ook gebruikt door de eigenschap van de Grafiek in Interactieve Mededelingen. Daarom zijn alle configuratiestappen die hierboven voor WebToPDF worden vermeld van toepassing om de eigenschapfuncties van de Grafiek te verzekeren correct.

## Vooraf geïnstalleerde configuraties {#preinstallationconfigurations}

Configuraties die worden vermeld in de sectie voor configuraties vóór de installatie zijn alleen van toepassing op de PDF Generator-service. Als u de PDF Generator-service niet configureert, kunt u het gedeelte voor configuratie vóór de installatie overslaan.

### Adobe Acrobat en toepassingen van derden installeren {#install-adobe-acrobat-and-third-party-applications}

Als u de PDF Generator-service gaat gebruiken om eigen bestandsindelingen zoals Microsoft® Word, Microsoft® Excel, Microsoft® PowerPoint, OpenOffice, WordPerfect X7 en Adobe Acrobat naar PDF-documenten om te zetten, moet u ervoor zorgen dat deze toepassingen op de AEM Forms-server zijn geïnstalleerd.

>[!NOTE]
>
>* Als uw Server van AEM Forms in een off-line of veilig milieu is en Internet niet beschikbaar is om Adobe Acrobat te activeren, zie [ Offlineactivering ](https://exception.licenses.adobe.com/aoes/aoes/v1/t1?locale=en) voor instructies om dergelijke instanties van Adobe Acrobat te activeren.
>* Adobe Acrobat, Microsoft® Word, Excel en PowerPoint zijn alleen beschikbaar voor Microsoft® Windows. Als u het op UNIX-Gebaseerde werkende systeem gebruikt, installeer OpenOffice om rijke tekstdossiers en gesteunde dossiers van Microsoft® Office in de documenten van PDF om te zetten.
>* Sluit alle dialoogvensters die worden weergegeven na de installatie van Adobe Acrobat en software van derden voor alle gebruikers die zijn geconfigureerd voor het gebruik van de PDF Generator-service.
>* Start minstens één keer alle geïnstalleerde software. Alle dialoogvensters sluiten voor alle gebruikers die zijn geconfigureerd om de PDF Generator-service te gebruiken.
>* [ de vervaldatum van de Controle van uw serienummers van Adobe Acrobat ](https://helpx.adobe.com/nl/enterprise/kb/volume-license-expiration-check.html) en reeks een datum om vergunning bij te werken of [ migreer uw serienummer ](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/licensing.html#migrating-your-serial-number) dat op de vervaldatum wordt gebaseerd.

Open Microsoft® Word nadat u Acrobat hebt geïnstalleerd. Op het **Acrobat** lusje, klik **creeer PDF** en zet een .doc of .docx dossier beschikbaar op uw machine in een Document van PDF om. Als de conversie succesvol is, is AEM Forms klaar om Acrobat te gebruiken met de PDF Generator-service.

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
   <td><p>C:\Program Files (x86)\OpenOffice 4</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>* Alle omgevingsvariabelen en de respectieve paden zijn hoofdlettergevoelig.
>* JAVA_HOME en Acrobat_PATH (alleen Windows) zijn verplichte omgevingsvariabelen.
>* De omgevingsvariabele OpenOffice_PATH wordt ingesteld op de installatiemap in plaats van op het pad naar het uitvoerbare bestand.
>* Stel geen omgevingsvariabelen in voor Microsoft® Office-toepassingen zoals Word, PowerPoint, Excel en Project, of voor AutoCAD. Als deze toepassingen op de server zijn geïnstalleerd, worden deze toepassingen automatisch gestart door de service PDF genereren.
>* Voor op UNIX-Gebaseerde platforms, installeer OpenOffice als /root. Als OpenOffice niet als root is geïnstalleerd, converteert de PDF Generator-service OpenOffice-documenten niet naar PDF-documenten. Als u OpenOffice als niet-wortelgebruiker moet installeren en in werking stellen, dan verstrek sudo rechten aan de niet-wortelgebruiker.
>* Als u OpenOffice op een UNIX-Gebaseerd platform gebruikt, stel het volgende bevel in werking om de wegvariabele te plaatsen:\
> `export OpenOffice_PATH=/opt/openoffice.org4`
>* Voer op platforms die zijn gebaseerd op SUSE® Linux® (SLES 15 SP6 of hoger) de volgende stappen uit om OpenOffice in te stellen:
>     * Installeer de nieuwste 32-bits variant van `OpenOffice 4.1.x` in een map, zoals `/opt/openoffice4` .
>     * Stel de omgevingsvariabele `OpenOffice_PATH` zo in dat deze naar deze locatie wijst. Bijvoorbeeld: `OpenOffice_PATH=/opt/openoffice4` .
>     * Zorg ervoor dat de `OpenOffice_PATH` -variabele algemeen is ingesteld (bijvoorbeeld met `/etc/profile` of het systeemspecifieke equivalent), zodat deze beschikbaar is voor alle gebruikers bij het aanmelden.

### (Alleen voor IBM® WebSphere®) Configureer IBM® SSL-socketprovider {#only-for-ibm-websphere-configure-ibm-ssl-socket-provider}

Voer de volgende stappen uit om IBM® SSL-socketprovider te configureren:

1. Maak een kopie van het bestand java.security. De standaardlocatie van het bestand is `[WebSphere_installation_directory]\Appserver\java_[version]\jre\lib\security` .
1. Open het gekopieerde bestand java.security voor bewerking.
1. Wijzig de standaard SSL-socketfabrieken om de JSSE2-fabrieken te gebruiken in plaats van de standaard IBM® WebSphere®-fabrieken:

   **Standaard inhoud:**

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

Wijzig de instellingen van het Microsoft® Office-vertrouwenscentrum om de PDF Generator-service in staat te stellen bestanden die zijn gemaakt met oudere versies van Microsoft® Office, om te zetten.

1. Open een Microsoft® Office-toepassing. Bijvoorbeeld Microsoft® Word. Navigeer naar **[!UICONTROL File]** > **[!UICONTROL Options]** . Het dialoogvenster Opties wordt geopend.

1. Klik op **[!UICONTROL Trust Center]** en klik op **[!UICONTROL Trust Center Settings]** .
1. Klik in de **[!UICONTROL Trust Center settings]** op **[!UICONTROL File Block Settings]** .
1. Schakel in de lijst **[!UICONTROL File Type]** de optie **[!UICONTROL Open]** uit voor het bestandstype dat de PDF Generator-service moet kunnen converteren naar PDF-documenten.

### (Alleen Windows) Vervang het token voor een procesniveau {#grant-the-replace-a-process-level-token-privilege}

De gebruikersrekening die wordt gebruikt om de toepassingsserver te beginnen vereist **vervang het symbolische** voorrecht van het procesniveau. De lokale systeemrekening heeft **vervangen een symbolische** voorrecht van het procesniveau door gebrek. Voor de servers die met een gebruiker van de Lokale groep van Beheerders lopen, moet het voorrecht uitdrukkelijk worden verleend. Voer de volgende stappen uit om het voorrecht toe te kennen:

1. Open de Redacteur van het Beleid van de Groep voor Microsoft® Vensters. Om de Redacteur van het Beleid van de Groep te openen, klik **[!UICONTROL Start]**, type **gpedit.msc** in het vakje van het Onderzoek van het Begin, en klik **[!UICONTROL Group Policy Editor]**.
1. Navigeer naar **[!UICONTROL Local Computer Policy]** > **[!UICONTROL Computer Configuration]** > **[!UICONTROL Windows Settings]** > **[!UICONTROL Security Settings]** > **[!UICONTROL Local Policies]** > **[!UICONTROL User Rights Assignment]** en bewerk het **[!UICONTROL Replace a process level token]** -beleid en neem de groep Beheerders op.
1. Voeg de gebruiker toe aan de Replace een Symbolische ingang van het Niveau van het Proces.

>[!NOTE]
>
> Zoals hierboven geïmpliceerd, als de server van AEM als dienst onder de rekening LocalSystem (LSA) loopt, uitdrukkelijk is het toewijzen van dit voorrecht aan een gebruiker niet noodzakelijk.

### (Alleen Windows) De PDF Generator-service inschakelen voor niet-beheerders {#enable-the-pdf-generator-service-for-non-administrators}

U kunt een gebruiker zonder beheerder inschakelen om de PDF Generator-service te gebruiken. Normaal gesproken kunnen alleen gebruikers met beheerdersrechten de service gebruiken:

1. Maak een omgevingsvariabele, PDFG_NON_ADMIN_ENABLED.
1. Stel de waarde van de omgevingsvariabele in op TRUE.
1. Start de AEM Forms-instantie opnieuw.

>[!NOTE]
>
> U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.

### (Alleen Windows) Gebruikersaccountbeheer uitschakelen (UAC) {#disable-user-account-control-uac}

1. Ga naar **[!UICONTROL Start > Run]** en voer **[!UICONTROL MSCONFIG]** in om het hulpprogramma Systeemconfiguratie te openen.
1. Klik op de tab **[!UICONTROL Tools]** , blader omlaag en selecteer **[!UICONTROL Change UAC Settings]** . Klik op **[!UICONTROL Launch]** om de opdracht in een nieuw venster uit te voeren.
1. Pas de schuifregelaar aan op het niveau Nooit aangeven. Wanneer gebeëindigd, sluit het bevelvenster en sluit het venster van de Configuratie van het Systeem.
1. Verifieer dat register het plaatsen voor UAC aan 0 (nul) wordt geplaatst. Voer de volgende stappen uit om te verifiëren:

   1. Microsoft® raadt u aan een back-up van het register te maken voordat u het wijzigt. Voor gedetailleerde stappen, zie [ hoe te file en herstel de registratie in Vensters ](https://support.microsoft.com/en-us/help/322756).
   1. Open Microsoft® Windows Registry Editor. Als u de registereditor wilt openen, gaat u naar Start > Uitvoeren, typt u regedit en klikt u op OK.
   1. Navigeer naar `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\policies\system\` . Zorg ervoor dat de waarde van EnableLUA is ingesteld op 0 (nul).
   1. Verzeker waarde van **EnableLUA** wordt geplaatst aan 0 (nul). Als de waarde niet 0 is, wijzigt u de waarde in 0. Sluit de registereditor.

1. Start de computer opnieuw op.

### (Alleen Windows) Fout bij rapporteren van service uitschakelen {#disable-error-reporting-service}

Terwijl het omzetten van een document in PDF gebruikend de dienst van PDF Generator op de Server van Vensters, soms, meldt de Server van Vensters dat uitvoerbaar een probleem heeft ontmoet en moet sluiten. Het heeft echter geen invloed op de PDF-conversie zoals deze op de achtergrond wordt voortgezet.

Als u wilt voorkomen dat de fout wordt ontvangen, kunt u de rapportage van fouten in Windows uitschakelen. Voor meer informatie bij het onbruikbaar maken van fout meldend, zie [ https://technet.microsoft.com/en-us/library/cc754364.aspx ](https://technet.microsoft.com/en-us/library/cc754364.aspx).

### (Alleen Windows) Conversie HTML naar PDF configureren {#configure-html-to-pdf-conversion}

De PDF Generator-service biedt WebKit, WebCapture en WebToPDF-routes of methoden voor het converteren van HTML-bestanden naar PDF-documenten. Als u in Windows conversie wilt inschakelen voor WebKit- en Acrobat WebCapture-routes, kopieert u het Unicode-font naar de map %windir%\fonts.

>[!NOTE]
>
>Wanneer u nieuwe lettertypen in de map Fonts installeert, start u het AEM Forms-exemplaar opnieuw.

### (Alleen op UNIX gebaseerde platforms) Extra configuraties voor conversie van HTML naar PDF  {#extra-configurations-for-html-to-pdf-conversion}

Op UNIX-gebaseerde platforms, steunt de dienst van PDF Generator WebKit en WebToPDF routes om de dossiers van HTML in de documenten van PDF om te zetten. Voer de volgende configuraties uit die van toepassing zijn op de door u gewenste omzettingsroute om de conversie van HTML naar PDF mogelijk te maken:

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
>* Wanneer u de PDF Generator-service uitvoert als een gebruiker die geen hoofdmap heeft, geeft u de gebruiker lees- en schrijftoegang tot alle fontmappen.
>* Wanneer u nieuwe lettertypen in de map Fonts installeert, start u het AEM Forms-exemplaar opnieuw.
>

## AEM Forms-invoegtoepassing installeren {#install-aem-forms-add-on-package}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Het pakket bevat AEM Forms Document Services en andere AEM Forms-mogelijkheden. Voer de volgende stappen uit om het pakket te installeren:

1. Open [ Distributie van de Software ](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]** :
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
1. Open [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65/administering/contentmanagement/package-manager.html?lang=nl-NL) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]** .

   U kunt het pakket via de directe verbinding ook downloaden die in het [ wordt vermeld versies van AEM Forms ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=nl-NL) artikel.

1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om het AEM-exemplaar opnieuw te starten. **stop niet onmiddellijk de server.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer in het bestand `[AEM-Installation-Directory]/crx-quickstart/logs/error` .log worden weergegeven en het logbestand stabiel is.

## Configuratie na installatie {#post-installation-configurations}

### Opstartdelegatie configureren voor bibliotheken met RSA/BouncyCastle  {#configure-boot-delegation-for-rsa-bouncycastle-libraries}

1. Stop de AEM-instantie. Navigeer aan de [ de installatiemap van AEM ] \crx-quickstart\conf\. Open het bestand sling.properties voor bewerking.

   Als u `[AEM installation directory]\crx-quickstart\bin\start.bat` gebruikt om een AEM-instantie te starten, bewerkt u de eigenschappen sling.property op `[AEM_root]\crx-quickstart\` .

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

1. Login aan [ de Manager van de Configuratie van AEM ](http://localhost:4502/system/console/configMgr) als beheerder.
1. Zoek en open de service **[!UICONTROL CQ-DAM-Handler-Gibson Font Managers]** . Geef het pad op van de systeemlettertypen, Adobe Server-lettertypen en de directory&#39;s met klantlettertypen. Klik op **[!UICONTROL Save]**.

   >[!NOTE]
   >
   >Uw recht om lettertypen te gebruiken die door andere partijen dan Adobe worden geboden, wordt beheerst door de licentieovereenkomsten die deze partijen u met deze lettertypen bieden, en wordt niet gedekt door uw licentie om Adobe-software te gebruiken. Adobe raadt u aan na te gaan of u voldoet aan alle toepasselijke niet-Adobe-licentieovereenkomsten voordat u niet-Adobe-lettertypen gebruikt met Adobe-software, met name voor het gebruik van lettertypen in een serveromgeving.
   >Wanneer u nieuwe lettertypen in de map Fonts installeert, start u het AEM Forms-exemplaar opnieuw.
   >

### Een lokale gebruikersaccount configureren om de PDF Generator-service uit te voeren  {#configure-a-local-user-account-to-run-the-pdf-generator-service}

Een lokale gebruikersaccount is vereist om de PDF Generator-service uit te voeren. Voor stappen om een lokale gebruiker tot stand te brengen, zie [ een gebruikersrekening in Vensters ](https://support.microsoft.com/en-us/help/13951/windows-create-user-account) creëren of een gebruikersrekening in op UNIX-Gebaseerde platforms creëren.

1. Open de [ pagina van de Configuratie van AEM Forms PDF Generator ](http://localhost:4502/libs/fd/pdfg/config/ui.html).

1. Geef op het tabblad **[!UICONTROL User Accounts]** de gegevens van een lokale gebruikersaccount op en klik op **[!UICONTROL Submit]** . Als Microsoft® Windows daarom vraagt, geeft u de gebruiker toegang. Wanneer de geconfigureerde gebruiker met succes is toegevoegd, wordt deze weergegeven onder de sectie **[!UICONTROL Your user accounts]** op het tabblad **[!UICONTROL User Accounts]** .

### De time-outinstellingen configureren {#configure-the-time-out-settings}

1. In [ AEM configuratiemanager ](http://localhost:4502/system/console/configMgr), bepaal de plaats en open de **[!UICONTROL Jacorb ORB Provider]** dienst.

   Voeg het volgende toe aan het veld **[!UICONTROL Custom Properties.name]** en klik op **[!UICONTROL Save]** . De wachtende antwoordtime-out (ook wel CORBA-clienttime-out genoemd) wordt ingesteld op 600 seconden.

   `jacorb.connection.client.pending_reply_timeout=600000`

1. Meld u aan bij de AEM-auteurinstantie en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Tools]** > **[!UICONTROL Forms]** > **[!UICONTROL Configure PDF Generator]** . De standaard-URL is <http://localhost:4502/libs/fd/pdfg/config/ui.html> .

   Open het tabblad **[!UICONTROL General Configuration]** en wijzig de waarde van de volgende velden voor uw omgeving:

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
   <td>270 seconden <br /> </td>
  </tr>
  <tr>
   <td>Seconden van PDFG-opschoning</td>
   <td>Het aantal seconden dat wordt vereist om post-omzettingsverrichtingen uit te voeren.<br /> </td>
   <td>3600 seconden</td>
  </tr>
  <tr>
   <td>Seconden van taakvervaldatum</td>
   <td>Duur waarvoor de dienst van PDF Generator een omzetting mag in werking stellen. Zorg ervoor dat de waarde van de Seconden van de Vervaltijd van de Baan groter is dan de waarde van de Seconden van de Schoonmaakactie PDFG.</td>
   <td>7200 seconden</td>
  </tr>
 </tbody>
</table>

### (Alleen Windows) Acrobat configureren voor de PDF Generator-service {#configure-acrobat-for-the-pdf-generator-service}

In Microsoft® Windows gebruikt de PDF Generator-service Adobe Acrobat om ondersteunde bestandsindelingen te converteren naar een PDF-document. Voer de volgende stappen uit om Adobe Acrobat voor de PDF Generator-service te configureren:

1. Open Acrobat en selecteer **[!UICONTROL Edit]** > **[!UICONTROL Preferences]** > **[!UICONTROL Updater]** . Schakel in Controleren op updates de optie **[!UICONTROL Automatically install updates]** uit en klik op **[!UICONTROL OK]** . Sluit Acrobat.
1. Dubbelklik op een PDF-document op uw systeem. Wanneer Acrobat voor de eerste keer wordt gestart, worden de dialoogvensters Aanmelden, Welkomstscherm en EULA weergegeven. Deze dialoogvensters sluiten voor alle gebruikers die zijn geconfigureerd om PDF Generator te gebruiken.
1. Voer het PDF Generator-hulpprogrammabatchbestand uit om Acrobat voor de PDF Generator-service te configureren:

   1. Open [ de Manager van het Pakket van AEM ](http://localhost:4502/crx/packmgr/index.jsp) en download het `adobe-aemfd-pdfg-common-pkg-[version].zip` dossier van de Manager van het Pakket.
   1. Pak het gedownloade .zip-bestand uit. Open de opdrachtprompt met beheerdersrechten.
   1. Ga naar de `[extracted-zip-file]\jcr_root\etc\packages\day\cq60\fd\adobe-aemds-common-pkg-[version]\jcr_root\etc\packages\day\cq60\fd\`
   1. Pak de `adobe-aemfd-pdfg-common-pkg-[version]` uit.
   1. Navigeer naar de map `[downloaded-adobe-aemfd-pdfg-common-pkg]\jcr_root\libs\fd\pdfg\tools\adobe-aemfd-pdfg-utilities-[version]` . Voer het volgende batchbestand uit:

      `Acrobat_for_PDFG_Configuration.bat`

      Acrobat is geconfigureerd om te worden uitgevoerd met de PDF Generator-service.

1. Looppas [ Hulpmiddel van de Gereedheid van het Systeem (SRT) ](#SRT) om de installatie van Acrobat te bevestigen.

### (Alleen Windows) Primaire route configureren voor conversie van HTML naar PDF {#configure-primary-route-for-html-to-pdf-conversion-windows-only}

De PDF Generator-service biedt meerdere manieren om HTML-bestanden te converteren naar PDF-documenten: Webkit, Acrobat WebCapture (alleen Windows) en WebToPDF. Adobe raadt u aan de WebToPDF-route te gebruiken, omdat deze de mogelijkheid biedt om dynamische inhoud af te handelen en omdat deze geen afhankelijkheden heeft met 32-bits bibliotheken of geen extra lettertypen vereist. Bovendien vereist WebToPDF-route geen sudo- of hoofdtoegang om de conversie uit te voeren.

De standaard primaire route voor conversie van HTML naar PDF is Webkit. De omzettingsroute wijzigen:

1. Navigeer in de AEM-auteurinstantie naar **[!UICONTROL Tools]**> **[!UICONTROL Forms]**> **[!UICONTROL Configure PDF Generator]** .

1. Selecteer op het tabblad **[!UICONTROL General Configuration]** de voorkeursomzettingsroute in de vervolgkeuzelijst **[!UICONTROL Primary Route for HTML to PDF conversions]** .

### Global Trust Store initialiseren {#intialize-global-trust-store}

Met het Betrouwbaarheidsopslagbeheer kunt u certificaten die u op de server vertrouwt, importeren, bewerken en verwijderen voor validatie van digitale handtekeningen en certificaatverificatie. U kunt om het even welk aantal certificaten invoeren en uitvoeren. Nadat een certificaat is geïmporteerd, kunt u de vertrouwensinstellingen bewerken en het type vertrouwde opslag vertrouwen. Voer de volgende stappen uit om een vertrouwde opslag te initialiseren:

1. Meld u als beheerder aan bij een AEM Forms-instantie.
1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Trust Store]** .
1. Klik op **[!UICONTROL Create TrustStore]** . Stel het wachtwoord in en selecteer **[!UICONTROL Save]** .

### Certificaten instellen voor de extensie- en coderingsservice van Reader {#set-up-certificates-for-reader-extension-and-encryption-service}

De DocAssurance-service kan gebruiksrechten toepassen op PDF-documenten. Als u gebruiksrechten wilt toepassen op PDF-documenten, configureert u de certificaten.

Voordat u de certificaten instelt, moet u controleren of u beschikt over:

* Certificaatbestand (.pfx).

* Wachtwoord voor persoonlijke sleutel dat bij het certificaat wordt geleverd.

* Alias persoonlijke sleutel. U kunt de Java-opdracht Keytool uitvoeren om de alias Persoonlijke sleutel weer te geven:
  `keytool -list -v -keystore [keystore-file] -storetype pkcs12`

* Wachtwoord sleutelarchiefbestand. Als u het Adobe Reader Extensions-certificaat gebruikt, is het wachtwoord voor het sleutelarchiefbestand altijd hetzelfde als het wachtwoord voor de persoonlijke sleutel.

Voer de volgende stappen uit om de certificaten te configureren:

1. Meld u als beheerder aan bij de AEM Author-instantie. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Users]** .
1. Klik op het veld **[!UICONTROL name]** van de gebruikersaccount. De pagina **[!UICONTROL Edit User Settings]** wordt geopend. Op de AEM Author-instantie bevinden certificaten zich in een KeyStore. Als u nog geen KeyStore hebt gemaakt, klikt u op **[!UICONTROL Create KeyStore]** en stelt u een nieuw wachtwoord in voor de KeyStore. Als de server al een KeyStore bevat, slaat u deze stap over.  Als u het Adobe Reader Extensions-certificaat gebruikt, is het wachtwoord voor het sleutelarchiefbestand altijd hetzelfde als het wachtwoord voor de persoonlijke sleutel.
1. Selecteer op de pagina **[!UICONTROL Edit User Settings]** de tab **[!UICONTROL KeyStore]** . Vouw de optie **[!UICONTROL Add Private Key from Key Store file]** uit en geef een alias op. De alias wordt gebruikt om de bewerking Reader Extensions uit te voeren.
1. Als u het certificaatbestand wilt uploaden, klikt u op **[!UICONTROL Select Key Store File]** en uploadt u een bestand &lt;filename>.pfx.

   Voeg de **[!UICONTROL Key Store Password]** , **[!UICONTROL Private Key Password]** en **[!UICONTROL Private Key Alias]** die aan het certificaat zijn gekoppeld, toe aan de respectievelijke velden. Klik op **[!UICONTROL Submit]**.

   >[!NOTE]
   >
   >In het productiemilieu, vervang uw evaluatiegeloofsbrieven met productiereferenties. Zorg ervoor dat u uw oude Reader Extensions-referenties verwijdert voordat u een verlopen extensie of evaluatiereferentie bijwerkt.

1. Klik op **[!UICONTROL Save & Close]** op de pagina **[!UICONTROL Edit User Settings]**.

### AES-256 inschakelen {#enable-aes}

Als u AES 256-versleuteling wilt gebruiken voor PDF-bestanden, moet u de JCE-bestanden (Unlimited Strength Jurdiction Policy) (Java Cryptography Extension) ophalen en installeren. Vervang de bestanden local_policy.jar en US_export_policy.jar in de map jre/lib/security. Als u bijvoorbeeld Sun JDK gebruikt, kopieert u de gedownloade bestanden naar de map `[JAVA_HOME]/jre/lib/security` .

De Assembler-service is afhankelijk van de service Reader Extensions, de Signature-service, de Forms-service en de Output-service. Voer de volgende stappen uit om te verifiëren dat de vereiste diensten in gebruik zijn:

1. Meld u aan bij de URL `https://'[server]:[port]'/system/console/bundles` als beheerder.
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

### (Alleen Windows) Registervermelding configureren voor Microsoft® Project {#configure-registry-entry-for-microsoft-project}

Nadat u de invoegtoepassing AEM Forms en het Microsoft®-project op uw computer hebt geïnstalleerd, registreert u een vermelding voor het Microsoft®-project op de 64-bits locatie. Het vergemakkelijkt de uitvoering van project aan PDFG omzettingstests. Hieronder volgen de stappen waarin het registratieproces wordt beschreven:

1. Open de Register-editor van Microsoft® Windows (regedit), ga naar Start > Uitvoeren om de registereditor te openen, typ regedit en klik op OK.
1. Navigeer aan `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Adobe\Acrobat PDFMaker\<version>\Office\SupportedApp`, en creeer een nieuw **Binaire registratie van de Waarde** en noem het aan **Project** anders.
1. Wijzig de gegevenswaarde van gecreeerd Binair register in 01 en klik O.K.
1. Sluit de registervermelding.


## Bekende problemen en problemen oplossen {#known-issues-and-troubleshooting}

* De conversie van HTML naar PDF mislukt als een gecomprimeerd invoerbestand HTML-bestanden bevat met double-bytetekens in bestandsnamen. U voorkomt dit door geen double-bytetekens te gebruiken bij de naamgeving van HTML-bestanden.

* Op UNIX-besturingssystemen vindt u de volgende handelingen om ontbrekende bibliotheken te zoeken:

1. Navigeer naar `[crx-repository]/bedrock/svcnative/HtmlToPdfSvc/bin/` .

1. Voer de volgende opdracht uit om alle bibliotheken weer te geven die WebToPDF nodig heeft voor conversie van HTML naar PDF.

   `ldd phantomjs`

   Voer de volgende opdracht uit om ontbrekende bibliotheken weer te geven.

   `ldd phantomjs | grep not`

1. De ontbrekende bibliotheken handmatig installeren.

## Systeemgereedheid (SRT) {#SRT}

Het [ hulpmiddel van de Gereedheid van het Systeem ](#srt-configuration) controleert als de machine behoorlijk wordt gevormd om de omzettingen van PDF Generator in werking te stellen. Het hulpmiddel produceert rapport bij de gespecificeerde weg. Het gereedschap uitvoeren:

1. Opdrachtprompt openen. Navigeer naar de map `[extracted-adobe-aemfd-pdfg-common-pkg]\jcr_root\libs\fd\pdfg\tools` .

1. Voer het volgende bevel van de bevelherinnering in werking:

   `java -jar forms-srt-[version].jar [Path_of_reports_folder] en`

   Het bevel produceert rapport en leidt ook tot het srt_config.yaml- dossier. U kunt het gebruiken om opties voor het hulpmiddel te vormen SRT. Het is facultatief om opties voor het hulpmiddel te vormen SRT.

   >[!NOTE]
   >
   >* Als het Hulpprogramma voor systeemgereedheid meldt dat het bestand pdfgen.api niet beschikbaar is in de map met Acrobat-plug-ins, kopieert u het bestand pdfgen.api van de map `[extracted-adobe-aemfd-pdfg-common-pkg]\jcr_root\libs\fd\pdfg\tools\adobe-aemfd-pdfg-utilities-[version]\plugins\x86_win32` naar de map `[Acrobat_root]\Acrobat\plug_ins` .

1. Navigeer naar `[Path_of_reports_folder]` . Open het bestand SystemReadyTool.html. Verifieer het rapport en los de bovengenoemde kwesties op.

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

* **Landinstelling:** Het is een verplichte parameter. De klasse biedt ondersteuning voor Engels(en), Duits (de), Frans (fr) en Japans(ja). De standaardwaarde is en. Het heeft geen gevolgen voor PDF Generator-diensten die op AEM Forms draaien op OSGi.
* **aemTempDir:** Het is een facultatieve parameter. Hiermee wordt de tijdelijke opslaglocatie van Adobe Experience Manager opgegeven.
* **gebruikers:** Het is een facultatieve parameter. U kunt een gebruiker opgeven om te controleren of de gebruiker machtigingen heeft vereist en om toegang te krijgen tot mappen die vereist zijn om PDF Generator uit te voeren. Als geen gebruiker wordt gespecificeerd, worden de gebruiker-specifieke controles overgeslagen en getoond zoals ontbroken in het rapport.
* **outputDir:** specificeer de plaats om het SRT rapport te bewaren. De standaardplaats is de huidige het werk folder van het hulpmiddel SRT.

## Problemen oplossen

Als u problemen zelfs na het bevestigen van alle die problemen door het hulpmiddel van SRT wordt gemeld, voer de volgende controles uit:

Alvorens de volgende controles uit te voeren, zorg ervoor dat [ Hulpmiddel van de Gereedheid van het Systeem ](#SRT) geen fout meldt.

+++ Adobe Acrobat

* Verzeker slechts [ gesteunde versie ](aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) van Microsoft® Office (met 32 bits) en Adobe Acrobat wordt geïnstalleerd en het openen van dialogen wordt geannuleerd.
* Controleer of Adobe Acrobat Update Service is uitgeschakeld.
* Zorg ervoor dat het {[&#128279;](#configure-acrobat-for-the-pdf-generator-service) partijdossier 0} Acrobat_for_PDFG_Configuration.bat met beheerdervoorrechten in werking werd gesteld.
* Controleer of een PDF Generator-gebruiker is toegevoegd aan de configuratieinterface van PDF.
* Zorg ervoor dat [ vervang een teken van het procesniveau ](#grant-the-replace-a-process-level-token-privilege) toestemming voor de gebruiker van PDF Generator wordt toegevoegd.
* Zorg ervoor dat de COM-invoegtoepassing Acrobat PDFMaker Office is ingeschakeld voor Microsoft Office-toepassingen.

+++

+++OpenOffice

**Microsoft® Vensters**

* Zorg ervoor dat 32 beetje [ gesteunde versie ](aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) van Microsoft Office geïnstalleerd is en het openen van dialogen voor alle toepassingen wordt geannuleerd.
* Controleer of een PDF Generator-gebruiker is toegevoegd aan de configuratieinterface van PDF.
* Verzeker de gebruiker van PDF Generator een lid van beheerdersgroep is en [ vervangt het symbolische ](#grant-the-replace-a-process-level-token-privilege) voorrecht van het procesniveau voor de gebruiker wordt geplaatst.
* Zorg ervoor dat de gebruiker is geconfigureerd in de gebruikersinterface van PDF Generator en voer de volgende handelingen uit:
   1. Meld u aan bij de Microsoft® Windows met PDF Generator-gebruiker.
   1. Open Microsoft® Office of OpenOffice toepassingen en annuleer alle dialoogvensters.
   1. Stel Adobe PDF in als standaardprinter.
   1. Acrobat instellen als standaardprogramma voor PDF-bestanden.
   1. Handmatige omzetting uitvoeren met de opties Bestand > Afdrukken en Acrobat in Microsoft Office-toepassingen en alle dialoogvensters annuleren.
   1. Beëindig alle processen met betrekking tot omzetting zoals winword.exe, powerpoint.exe, en excel.exe.
   1. Start de AEM Forms-server opnieuw.

**Linux®**

* Installeer de [ gesteunde versie ](aem-forms-jee-supported-platforms.md#software-support-for-pdf-generator) van OpenOffice. AEM Forms ondersteunt zowel 32-bits als 64-bits versies. Na het installeren, open alle toepassingen OpenOffice, annuleer alle dialoogvensters, en sluit de toepassingen. Open de toepassingen opnieuw en controleer of er geen dialoogvenster wordt weergegeven wanneer u een OpenOffice-toepassing opent.

* Creeer een omgevingsvariabele `OpenOffice_PATH` en plaats het om het aan installatie te richten OpenOffice wordt geplaatst in de [ console ](https://linuxize.com/post/how-to-set-and-list-environment-variables-in-linux/) of het dt (de Boom van het Apparaat) profiel.
* Als er kwesties in het installeren van OpenOffice zijn, zorg ervoor dat [ bibliotheken met 32 bits ](#extrarequirements) die voor installatie OpenOffice worden vereist beschikbaar zijn.

+++

+++ HTML naar PDF conversieproblemen

* Zorg ervoor dat de mappen met fonts worden toegevoegd in de PDF Generator config-gebruikersinterface.

**Linux en Solaris (WebToPDF omzettingsroute)**

* Zorg ervoor dat er een 32-bits bibliotheek beschikbaar is (libicudata.so.42) voor HTMLToPDF-conversie op basis van Webkit en 64-bits (libicudata.so.42 libs zijn beschikbaar voor HTMLToPDF-conversie op basis van WebToPDF.

* Voer de volgende opdracht uit om ontbrekende bibliotheken voor WebToPDF weer te geven:

  ```
  ldd phantomjs | grep not
  ```

**Linux® en Solaris™ (WebKit omzettingsroute)**

* Controleer of de mappen `/usr/lib/X11/fonts` en `/usr/share/fonts` bestaan. Als de mappen niet bestaan, maakt u een symbolische koppeling van `/usr/share/X11/fonts` naar `/usr/lib/X11/fonts` en een andere symbolische koppeling van `/usr/share/fonts` naar `/usr/share/X11/fonts` .

  ```
  ln -s /usr/share/fonts /usr/share/X11/fonts
  
  ln -s /usr/share/X11/fonts /usr/lib/X11/fonts
  ```

* Zorg ervoor dat IBM-lettertypen worden gekopieerd onder usr/share/fonts.
* Zorg ervoor dat glibc voor GGGL-kwetsbaarheidsprobleem met spook beschikbaar is op de computer. Gebruik uw standaardpakketbeheer om bij te werken naar de nieuwste versie van glibc. Dit omvat het verhelpen van spookkwetsbaarheden.
* Zorg ervoor dat de nieuwste versies van 32-bits bibliotheken met lib-curl, libcrypto en libssl op het systeem zijn geïnstalleerd. Maak ook symlinks `/usr/lib/libcurl.so` (of libcurl.a voor AIX®), `/usr/lib/libcrypto.so` (of libcrypto.a voor AIX®) en `/usr/lib/libssl.so` (of libssl.a voor AIX®) naar de nieuwste versies (32 bits) van de respectievelijke bibliotheken.

* Voer de volgende stappen uit voor IBM® SSL Socket provider:
   1. Kopieer het bestand java.security van `<WAS_Installed_JAVA>\jre\lib\security` naar een willekeurige locatie op uw AEM Forms-server. De standaardlocatie is Standaardlocatie = `<WAS_Installed>\Appserver\java_[version]\jre\lib\security` .

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

+++ Kan geen PDF Generator-gebruiker (PDFG) toevoegen

* Zorg ervoor dat Microsoft® Visual C++ 2012 x86 en Microsoft® Visual C++ 2013 x86 (32-bits) opnieuw distribueerbaar zijn geïnstalleerd in Windows.

+++

+++Fouten in de automatiseringstest

* Voer voor Microsoft® Office en OpenOffice ten minste één omzetting handmatig uit (als elke gebruiker) om ervoor te zorgen dat er geen dialoogvenster verschijnt tijdens de conversie. Als er een dialoogvenster verschijnt, wordt dit gesloten. Een dergelijk dialoogvenster wordt niet weergegeven tijdens automatische conversie.

* Voordat u automatisering uitvoert op een AEM Forms in een OSGi-omgeving, moet u controleren of het testpakket is geïnstalleerd en actief is.

+++

+++Meerdere omzettingsfouten voor gebruikers

* Verifieer de serverlogboeken om te controleren of de omzetting voor een bepaalde gebruiker ontbreekt.(De Ontdekkingsreiziger van het Proces kan u helpen het lopende proces voor verschillende gebruikers controleren)

* Zorg ervoor dat de gebruiker die voor PDF Generator is geconfigureerd, lokale beheerdersrechten heeft.

* Zorg ervoor dat PDF Generator-gebruikers lees-, schrijf- en uitvoermachtigingen hebben voor gebruikers met LC-temp en PDFG-sjablonen.

* Voer voor Microsoft® Office en OpenOffice ten minste één omzetting handmatig uit (als elke gebruiker) om ervoor te zorgen dat er geen dialoogvenster verschijnt tijdens de conversie. Als er een dialoogvenster verschijnt, wordt dit gesloten. Een dergelijk dialoogvenster wordt niet weergegeven tijdens automatische conversie.

* Voer een steekproefomzetting uit.

+++

+++Licentie van Adobe Acrobat geïnstalleerd op AEM Forms Server verloopt.

* Als u een bestaande vergunning van Adobe Acrobat hebt en het is verlopen, [ Download de recentste versie van Adobe Application Manager ](https://helpx.adobe.com/in/creative-suite/kb/aam-troubleshoot-download-install.html), en migrerend uw serienummer. Alvorens [ migrerend uw serienummer ](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/licensing.html#migrating-your-serial-number).

   * Gebruik de volgende bevelen om prov.xml te produceren en bestaande te reserialize gebruikend het prov.xml- dossier in plaats van bevelen die in [ worden verstrekt migrerend uw serienummer ](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/licensing.html#migrating-your-serial-number) aantalartikel.

         &quot;
         
          adobe_prtk —tool=VolumeSerialize —generate —serial=&lt;serialnum> [-leid=&lt;LEID>] [-regsuppress=ss] [-eulasuppress] [-locales=limited lijst van scènes in xx_XX formaat of ALL>] [-provfile=&lt;Absolute weg aan prov.xml>] 
         
         &quot;
     
   * Het volume rangschikt het pakket (re-serialize de bestaande installatie gebruikend het prov.xml- dossier en nieuwe serie): stel het volgende bevel van de PRTK installatiemap als beheerder in werking om de opgestelde pakketten op cliëntmachines in series te vervaardigen en te activeren:

         &quot;
          adobe_prtk —tool=VolumeSerialize —provfile=C:\prov.xml -stream 
         
         &quot;
     
* Voor grootschalige installaties, gebruik [ Acrobat Customization Wizard ](https://www.adobe.com/devnet-docs/acrobatetk/tools/Wizard/index.html) om vorige versies van Reader en Acrobat te verwijderen. Pas het installatieprogramma aan en implementeer het op alle computers van uw organisatie.

+++

+++ AEM Forms Server bevindt zich in een offline- of beveiligde omgeving en het internet is niet beschikbaar om Acrobat te activeren.

* U kunt binnen 7 dagen na de eerste introductie van uw Adobe-product online gaan om een online activering en registratie te voltooien of een apparaat met internetverbinding en het serienummer van uw product gebruiken om dit proces te voltooien. Voor gedetailleerde instructies, zie [ Offlineactivering ](https://exception.licenses.adobe.com/aoes/aoes/v1/t1?locale=en).

+++

+++ Kan Word- of Excel-bestand niet converteren naar PDF op Windows Server

Wanneer de gebruiker Word- of Excel-bestanden naar PDF probeert om te zetten op Microsoft Windows Server, wordt de volgende fout aangetroffen:

*het bericht van de Fout van primaire converter:
ALC-PDG-015-003-Het systeem kan het invoerbestand niet openen. Verzend opnieuw uw dossier of contacteer uw systeembeheerder.*

Om de kwestie op te lossen, zie [ Onbekwaam om Word of dossier van Excel in PDF op de Server van Vensters om te zetten ](/help/forms/using/disable-uac-for-pdfgconfiguration.md).

+++

+++ Kan Excel-bestanden niet converteren naar PDF op Windows Server 2019

Wanneer u Microsoft Excel 2019 op de Server 2019 van Microsoft Windows omzet in PDF, moet u het volgende verzekeren:

* Tijdens het gebruik van de PDF Generator-service mag de Windows-computer geen actieve externe verbinding met de AEM-server hebben (Windows RDP-sessie).
* De standaardprinter moet op Adobe PDF worden ingesteld.

  >[!NOTE]
  >* Voor Apple macOS en Ubuntu OS hoeft u de bovenstaande instellingen niet te configureren.

+++

+++ Kan XPS-bestanden niet converteren naar PDF

Om de kwestie op te lossen, [ creeer een eigenschap-specifieke registratiesleutel op Vensters ](https://helpx.adobe.com/in/acrobat/kb/unable-convert-xps-to-pdfs.html).

+++


## Volgende stappen {#next-steps}

U hebt een werkende AEM Forms-omgeving voor documentservices. U kunt documentservices gebruiken via:

* [Centrische workflows van formulieren op OSGi](/help/forms/using/aem-forms-workflow.md)
* [Gecontroleerde mappen](/help/forms/using/watched-folder-in-aem-forms.md)
* [API&#39;s voor documentservices](/help/forms/using/aem-document-services-programmatically.md)
