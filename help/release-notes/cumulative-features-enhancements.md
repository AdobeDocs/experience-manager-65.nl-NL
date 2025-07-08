---
title: Cumulatieve belangrijkste functies en verbeteringen in de Adobe Experience Manager 6.5-release.
description: Een cumulatieve lijst van belangrijkste eigenschappen en verhogingen die in Adobe Experience Manager 6.5 van de vorige acht versies van het de dienstpak worden gemaakt.
content-type: reference
docset: aem65
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 01fe5b53-2244-445f-a4d0-bd58ea38b611
solution: Experience Manager
source-git-commit: 03c070f7bba1d66ce2a5309d2ab79567dbef3264
workflow-type: tm+mt
source-wordcount: '3531'
ht-degree: 0%

---

# Cumulatieve belangrijkste kenmerken en verbeteringen

Een cumulatieve lijst van zeer belangrijke eigenschappen en verhogingen in Adobe Experience Manager 6.5 voor vorige versies van het de dienstpak.

Zie ook [ Adobe Experience Manager 6.5 de Latest Nota&#39;s van de Versie van het Pak van de Dienst ](/help/release-notes/release-notes.md).


## AEM 6.5, Service Pack 23-mei 22, 2025

### Forms {#forms-sp23}

* [ Toegankelijke Hyperlinks met gemengde tekst die in Statische PDFs ](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/using-designer.pdf) stileert: De hyperlinks die gemengde tekststijlen in statische PDFs bevatten worden nu geëtiketteerd als één enkel toegankelijk element. Deze verbetering vereenvoudigt de codestructuur, verbetert de navigatie van de schermlezer, en steunt betere toegankelijkheidsnaleving.

* [ Bijgewerkte Gesteunde Matrijs van het Platform ](/help/forms/using/aem-forms-jee-supported-platforms.md)

  De nieuwste versie introduceert updates van de ondersteunde platformmatrix, zodat deze compatibel zijn met nieuwere technologieën.

   * IBM® Content Manager Client 8.7

   * MongoDB Enterprise 7.0

   * MySQL 8.4

   * Microsoft® SQL Server 2022

   * Microsoft® SQL Server JDBC-stuurprogramma 12.8

   * Red Hat® Enterprise Linux® 9 (Kernel 4.x, 64-bits)

* [ Verhard component van de dossiergehechtheid ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/file-attachment): Als veiligheidsmaatregel, verhindert de component nu voorlegging van dossiers met gewijzigde uitbreidingen die proberen om toegestane dossiertype controles te omzeilen. Dergelijke bestanden worden tijdens de verzending geblokkeerd, zodat alleen geldige bestandstypen worden geaccepteerd.

## AEM 6.5, Service Pack 22-november 21, 2024

### Sites {#sites}

[ de Universele Redacteur ](/help/sites-developing/universal-editor/introduction.md) is nu beschikbaar op AEM 6.5 voor hoofdloze gebruiksgevallen met de toepassing van een eigenschapspak.

### [!DNL Assets]

Het tabblad IPTC ondersteunt nu [!UICONTROL Alt Text] - en [!UICONTROL Extended Description] -tekstvelden. (Assets-34918)

### Forms {#forms-sp22}

#### Nieuwe GA-functies in AEM Forms {#ga-aem-forms-sp22}

* Toegevoegde steun om doopvont toe te laten die in [ Interactieve Communicatie Band APIs ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/interactive-communications/create-interactive-communication#output-format-print-channel) inbedt - Interactieve Mededelingen omvat nu steun voor het inbedden van de doopvonten van Adobe Ming en van Adobe Myungjo in PDFs die door de Band API wordt geproduceerd. Deze verbetering zorgt voor nauwkeurige tekstrendering in gegenereerde documenten, zelfs bij het gebruik van fontsubsets, waardoor meertalige inhoud in PDF-uitvoerbestanden beter wordt ondersteund.

* [ Inhoudslijst API voor de Toegankelijkheid van PDF ](/help/forms/using/aem-document-services-programmatically.md#auto-tag-pdf-documents-auto-tag-api) - AEM Forms op OSGi steunt nu de nieuwe TOC markering API om PDF voor toegankelijkheidsnormen te verbeteren. PDF&#39;s worden toegankelijker gemaakt voor gebruikers met ondersteunende hulpmiddelen.

* [ de resolutie van het Fragment XDP ](/help/forms/using/assembler-service.md#resolve-references-on-crx-repository-resolve-references-on-crx-repository) - AEM Forms op OSGi lost nu Fragment XDPs op die in Primaire XDPs wordt van verwijzingen wordt voorzien en in de Bewaarplaats van AEM CRX wordt opgeslagen.

* [ PDF/A nalevingsverhogingen ](/help/forms/developing/pdf-a-documents.md#converting-documents-to-pdfa-documents-converting-documents-to-pdf-a-documents) - nu kunnen de gebruikers PDFs in formaten PDF/A (1a, 2a, 3a) voor archiveringsdoeleinden omzetten terwijl het verzekeren van toegankelijkheid en het controleren van naleving van deze normen.

* **Steun voor Auto het Grootte van Doopvont voor Statische documenten van PDF** - AEM Forms Designer, OutputService, en FormsService steunt nu auto het rangschikken van doopvonten voor statische PDFs. Als de gebruiker de fontgrootte 0 instelt voor tekst-, numerieke, wachtwoord- of datetime velden, wordt de fontgrootte automatisch aangepast binnen deze velden zonder de algemene grootte van het veld te wijzigen. Als gebruikers de functie willen gebruiken, geven ze een markering door in de aangepaste XCI: `<behaviorOverride>patch-LC-3921991:1</behaviorOverride>` .

#### Nieuwe Beta-functies in AEM Forms {#beta-aem-forms-sp22}

De bètafunctie biedt u een unieke kans om exclusieve toegang te krijgen tot geavanceerde innovaties en om hun ontwikkeling vorm te geven. Wilt u een bètafunctie voor uw omgevingen inschakelen? Verzend een e-mail van uw officiële adres naar aem-forms-ea@adobe.com met de lijst van mogelijkheden die u geinteresseerd bent.

* [ hCaptcha ](/help/forms/using/integrate-adaptive-forms-hcaptcha.md) en [ Cloudflare Turnstile CAPTCHA diensten ](/help/forms/using/integrate-adaptive-forms-turnstile.md): AEM Forms steunt de volgende diensten Captcha:
   * Captcha beschermt formulieren tegen bots, spam en automatisch misbruik door gebruikers uit te dagen met een widget selectievakjes. Het zorgt ervoor dat alleen menselijke gebruikers doorgaan, waardoor de beveiliging voor online transacties wordt verbeterd.
   * Cloudflare Turnstile biedt een beveiligingsmaatregel die tot doel heeft formulieren te beschermen tegen geautomatiseerde bots, kwaadaardige aanvallen, spam en ongewenst geautomatiseerd verkeer. Er wordt een selectievakje weergegeven bij het verzenden van formulieren om te controleren of het formulier menselijk is, voordat het formulier kan worden verzonden.

* Adaptieve formulierversie:
   * [ creeer veelvoudige versies van een AanpassingsVorm ](/help/forms/using/add-versioning-reviews-comments.md) - nu kunnen de gebruikers variaties van bestaande vormen gemakkelijk beheren. Dit proces vereenvoudigt versiecontrole en vergemakkelijkt vergelijking voor vormoptimalisering, allen binnen één enkele, gestroomlijnde werkschema.
   * [ vergelijk Aangepaste Forms ](/help/forms/using/compare-forms-core-components.md): De gebruikers kunnen nu twee vormen gemakkelijk vergelijken om verschillen te identificeren. Het vergemakkelijkt vlotte samenwerking door teamleden toe te laten om revisies te vergelijken en veranderingen efficiënt te bespreken.

## AEM 6.5, Service Pack 21-juni 6, 2024

### [!DNL Assets]

#### Verbeteringen

Het tabblad IPTC ondersteunt nu [!UICONTROL Alt Text] - en [!UICONTROL Extended Description] -tekstvelden. (Assets-34918)

#### Toegankelijkheid

* Als de verwerkingsstatus van een element is mislukt of Metagegevens zijn mislukt, werkt de interface voor bijschriften en audiotracks nu naar behoren. (Assets-37281)
* Wanneer u metagegevens van middelen opslaat en deze probeert te bewerken, wordt de taalnaam nu weergegeven. (Assets-37281)

### [!DNL Forms]

Enkele belangrijke functies en verbeteringen in deze release zijn onder andere:

* **Steun voor Oauth Credentials**: Een nieuw en gemakkelijker om referentie voor server-aan-server authentificatie te gebruiken, die de bestaande referentie van de Rekening van de Dienst (JWT) vervangt. (NPR-41994)
* {de verhogingen van de Redacteur van 0} Regel in AEM Forms [:](/help/forms/using/rule-editor-core-components.md)
   * Ondersteuning voor het implementeren van geneste voorwaarden met `When-then-else` -functionaliteit.
   * Valideer of stel panelen en formulieren, met inbegrip van gebieden opnieuw in.
   * Ondersteuning voor moderne JavaScript-functies zoals let- en pijlfuncties (ES10-ondersteuning) binnen de aangepaste functies.
* [ AutoTag API voor de Toegankelijkheid van PDF ](/help/forms/using/aem-document-services-programmatically.md#doc-utility-services-doc-utility-services): AEM Forms op OSGi steunt nu nieuwe AutoTag API om PDF voor toegankelijkheidsnormen te verbeteren door markeringen toe te voegen: paragrafen, en lijsten. PDF&#39;s worden toegankelijker gemaakt voor gebruikers met ondersteunende hulpmiddelen.
* **16 beetjePNG steun**: De dienst van PDF Generator ImageToPdf steunt nu omzetting van PNGs met 16 beetjekleurdiepte.
* **past artefacten op individuele tekstblokken in XDPs** toe: Forms Designer laat nu gebruikers montages op individuele tekstblokken in XDP dossiers vormen. Hierdoor kunt u elementen beheren die in de PDF&#39;s als artefacten worden behandeld. Deze elementen, zoals kop- en voetteksten, zijn toegankelijk voor ondersteunende hulpmiddelen. Tot de belangrijkste functies behoren het markeren van tekstblokken als artefacten en het insluiten van deze instellingen in de XDP-metagegevens. De Forms Output-service past deze instellingen toe tijdens het genereren van PDF, zodat de juiste PDF/UA-codering wordt gegarandeerd.
* **AEM Forms Designer wordt verklaard met `GB18030:2022` norm**: Met de `GB18030:2022` certificatie, nu steunt Forms Designer de Chinese het karakterreeks van Unicode die u Chinese karakters in alle editable gebieden en dialoogvakjes laat invoeren.
* [ Steun voor route WebToPDF in de Server van JEE ](/help/forms/using/admin-help/configure-service-settings.md#generate-pdf-service-settings-generate-pdf-service-settings) die de dienst van PDF Generator gebruikt steunt nu de route WebToPDF voor het omzetten van de dossiers van HTML in de documenten van PDF op JEE. Deze steun is naast de bestaande (Vensters slechts) routes Webkit en WebCapture. De WebToPDF-route is al beschikbaar op OSGi en uitgebreid naar JEE. Nu, op zowel platforms JEE als OSGi, steunt de dienst van PDF Generator de volgende routes over verschillende werkende systemen:
   * **Vensters**: Webkit, WebCapture, WebToPDF
   * **Linux®**: Webkit, WebToPDF


## AEM 6.5, Service Pack 20-februari 22, 2024

### [!DNL Assets]

* Dynamic Media ondersteunt nu HEIC-afbeeldingsindeling zonder verlies voor Apple iOS/iPadOS. Zie [ fmt ](https://experienceleague.adobe.com/en/docs/dynamic-media-developer-resources/image-serving-api/image-serving-api/http-protocol-reference/command-reference/r-is-http-fmt) in het Dynamische Beeld van Media die en API teruggeven dienen.
* Multisite Manager (MSM) ondersteunt nu de structuren van het Fragment van de Ervaring met inbegrip van omslagen en subfolders, voor efficiënte bulkimplementatie van de Fragmenten van de Ervaring aan Levende Kopieën.

### [!DNL Forms]

* **de Rapportering van de Transactie in AEM Forms op JEE**: Het rapporteringsvermogen van de transactie is geïntroduceerd voor AEM Forms op JEE. Hiermee kunt u uitgebreide documenttransacties, zoals Conversies, Uitvoeringen en Verzending, opnemen. Dit verbetert de efficiëntie en vergemakkelijkt een betere administratie. De functie is standaard uitgeschakeld. U kunt dit inschakelen via de interface voor beheer.
* **Verbeterde Veiligheid met Steun ECDSA**: AEM Forms biedt nu robuuste steun voor het Elliptic Curve Digital Signature Algorithm (ECDSA) over zowel JEE als OSGi stapels aan. Gebruikers kunnen nu PDF-documenten ondertekenen, certificeren en verifiëren met verhoogde beveiliging. Tot de ondersteunde EC-curveralgoritmen behoren:
   * ECDSA elliptische curve P256 met SHA256-digest-algoritme
   * ECDSA elliptische curve P384 met SHA384-digest-algoritme
   * ECDSA elliptische curve P512 met SHA512-digest-algoritme
* **Naadloze Verenigbaarheid met Vensters 11 voor Forms Designer**: AEM Forms Designer steunt nu Vensters 11, die vlotte installatie en verrichting verzekeren. Gebruikers kunnen met vertrouwen een upgrade naar Windows 11 uitvoeren zonder dat ze zich zorgen hoeven te maken over de herinstallatie van Forms Designer of over compatibiliteitsproblemen, waardoor een ononderbroken workflow wordt gegarandeerd.
* **Verbeterde Toegankelijkheid met de Rol van de &quot;Titel&quot;van de Douane in AEM Forms Designer**: AEM Forms Designer omvat nu een geroepen rol van de douanetoegankelijkheid &quot;Bijschrift,&quot;machtigend gebruikers om XDPs met gepersonaliseerde ondertitelingselementen tot stand te brengen. Deze functie verbetert de toegankelijkheid doordat gebruikers aangepaste bijschriften kunnen integreren in hun documentontwerpen, zodat ze de insluiting en gebruikerservaring kunnen verbeteren.

## AEM 6.5, Service Pack 19-december 7, 2023

* Gebruikers van de Sites-pagina-editor/afbeeldingscomponent konden naar elementen van de externe Assets Cloud Service verwijzen. (SITES-13448, SITES-13433)
* AEM ondersteunt nu sorteren op de server voor snellere projectnavigatie in de lijstweergave. Projectknooppunten worden gesorteerd op basis van de door de gebruiker geselecteerde kolom voordat ze in de interface worden weergegeven.

### [!DNL Forms]

* **Nieuwe Aangepaste Componenten van de Kern van de Vorm**: De verticale lusjes, de Voorwaarden &amp;, en Checkbox worden toegevoegd om scalability van vormen te verbeteren.
   * **[CheckBox component ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox)**: De adaptieve Forms die op de Componenten van de Kern wordt gebaseerd kan nu een checkbox component omvatten. Hiermee kunnen gebruikers binaire keuzes maken door een bepaalde optie te selecteren of te deselecteren. De optie wordt meestal weergegeven als een klein vak waarop u kunt klikken of tikken om te schakelen tussen twee statussen: ingeschakeld en uitgeschakeld. Het selectievakje is een veelgebruikt formulierelement voor een ja/nee- of waar/onwaar-keuze.

   * **[de component van de Voorwaarden en van de Voorwaarden ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions)**: De op component-gebaseerde Aangepaste Forms van de kern omvat nu een component van de Voorwaarden en van de Voorwaarden. Auteurs van formulieren voegen deze sectie toe om gebruikers de voorwaarden, juridische overeenkomsten of bepalingen voor de service, het product of het platform te laten zien. Deze component is bedoeld om gebruikers te informeren over de regels, regels en verplichtingen waarmee zij instemmen door het formulier in te dienen.

     ![ Verticale lusjes, Voorwaarden en componenten Checkbox ](/help/forms/using/assets/forms-components.png)

   * **[Verticale de component van lusjes ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs)**: De adaptieve Forms die op de Componenten van de Kern wordt gebaseerd kan vorminhoud in een verticale lijst van lusjes nu organiseren, die een gestructureerde en navigeerbare lay-out verstrekken. De verticale lusjes in een vorm verbeteren de gebruikerservaring door navigatie te vereenvoudigen en inhoud te organiseren. Ze zijn vooral handig wanneer het formulier meerdere secties of complexe informatie bevat.

* **[met 64 bits versie van AEM Forms Designer](/help/forms/using/installing-configuring-designer.md)**: De met 64 bits versie van AEM Forms Designer brengt verbeterde prestaties, scalability, en geheugenbeheer om uw ervaring van de vormverwezenlijking te versterken. Met de 64-bits architectuur kunt u nog grotere en complexere projecten eenvoudig aanpakken, zodat u kunt zorgen voor naadloze ontwerpworkflows en geoptimaliseerde efficiëntie. Verhoog uw mogelijkheden voor formulierontwerp en omarm de toekomst van AEM Forms Designer met deze baanbrekende release.

* **[verbind een Aangepaste Forms met de Lijst van SharePoint Microsoft®](/help/forms/using/configuring-submit-actions.md#submit-to-microsoft&reg;-sharepoint-list)**: AEM Forms verstrekt een out-of-the-box integratie om vormgegevens rechtstreeks naar de Lijst van SharePoint voor te leggen, latend u de mogelijkheden van de Lijsten van SharePoint gebruiken. U kunt de Microsoft® SharePoint-lijst configureren als gegevensbron voor een formuliergegevensmodel en de verzendactie Verzenden met het formuliergegevensmodel gebruiken om een adaptief formulier te verbinden met de SharePoint-lijst.

* **[Steun om Document van de eigenschappen van het Verslag voor de Aangepaste Fragmenten van de Vorm te vormen](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)**: U kunt uw Aangepaste fragmenten van de Vorm en zijn gebieden in de Aangepaste redacteur van de Vorm nu gemakkelijk aanpassen.

* **met 64 bits XMLFM**: De iteratie met 64 bits van XMLFM introduceert verhoogde prestaties, scalability, en verfijnd geheugenbeheer. Het is de eerste inheemse dienst met 64 bits die op server-kant wordt opgesteld. Met XMLFM 64-bits kan een naadloze afhandeling van grotere renderingwerklasten worden bewerkstelligd door gebruik te maken van de inherente mogelijkheid om toegang te krijgen tot grotere geheugenbronnen in vergelijking met de 32-bits tegenhanger. Deze mijlpaal betekent niet alleen een prestatiesprong, maar introduceert ook belangrijke verbeteringen aan het native servicekader binnen de AEM Forms Server. Deze update zorgt ervoor dat AEM Forms Server naadloos alle 64-bits native services ondersteunt.

## AEM 6.5, Service Pack 18-augustus 24, 2023

* Assets, Dynamische Media - [ Veelvoudige titel en audiospoorsteun voor video&#39;s in Dynamische Media ](/help/assets/video.md#about-msma) — U kunt veelvoudige ondertitels en veelvoudige audiosporen aan een primaire video nu gemakkelijk toevoegen. Dit betekent dat uw video&#39;s toegankelijk zijn voor een wereldwijd publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de ondertitels en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.
* Assets - In de zoekresultaten kunt u nu naar de maplocatie met een element navigeren, zodat u verschillende taken voor middelenbeheer kunt uitvoeren.
* De Plukker van Polaris van Plaatsen in de Fragmenten van de Inhoud heeft betere prestaties.
* Gebruikers van de Sites-pagina-editor/afbeeldingscomponent konden naar elementen van de externe Assets Cloud Service verwijzen.
* Adobe ondersteunt nu sorteren op de server om snel een project in de lijstweergave te vinden, waar u mogelijk veel projecten in uw systeem hebt. Projectknooppunten worden op de achtergrond gesorteerd op basis van de kolom die door de gebruiker is geselecteerd voordat ze in de gebruikersinterface worden weergegeven.
* AEM 6.5.18.0 ondersteunt MongoDB 5.0 tot en met 6.0.

### [!DNL Forms]

* **[Verbeterde fout behandeling met de managers van de douanefout in de regelredacteur ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms)** - u kunt een douanefunctie (gebruikend de Bibliotheek van de Cliënt) nu aanhalen als antwoord op een fout die door de externe dienst is teruggekeerd. En u kunt eindgebruikers een op maat gesneden reactie geven. Of u kunt specifieke acties uitvoeren voor fouten die door een service worden geretourneerd. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant meedelen dat de dienst neer is

* **[Verbeterde stap van het Werkschema van het Ondertekenen van Adobe ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/workflows/aem-forms-workflow-step-reference#sign-document-step)** - de het werkschemastap van het Ondertekenen van Adobe in de Werkschema&#39;s van AEM is beschikbaar met de volgende verhogingen.

   * **Verbeterde veiligheid met op identiteitskaart-Gebaseerde authentificatie van de overheid voor het Teken van Adobe** - Op identiteitskaart-Gebaseerde Authentificatie van de Regering van Adobe Acrobat Sign biedt een extra laag van controle aan. Het stelt gebruikers in staat hun identiteit te verifiëren met behulp van door de overheid afgegeven id&#39;s (rijbewijs, nationale identiteitskaart, paspoort). Door vertrouwde identificatiedocumenten te gebruiken, voegt deze verbetering een extra niveau van vertrouwen aan het ondertekeningsproces toe, die het ideaal maakt voor scenario&#39;s die verhoogde veiligheid, naleving, en gebruikersbevestiging vereisen.

   * **Verbeterde transparantie gebruikend het Spoor van de Controle voor de documenten van het Teken van Adobe** - gebruik de eigenschap van het Spoor van de Controle voor gedetailleerde inzichten in de levenscyclus van uw documenten van het Teken van Adobe. Met Audittrail, kunt u een uitvoerig verslag van alle acties en interactie handhaven met betrekking tot uw documenten. Deze handelingen en interacties omvatten wie het document heeft bekeken, bewerkt of ondertekend, samen met tijdstempels voor elke gebeurtenis. Deze verbetering is van cruciaal belang voor het handhaven van de naleving, het oplossen van geschillen en het verzekeren van de integriteit van uw digitale overeenkomsten.


   * **breidde de rollen voor de ontvangers van de Overeenkomst voorbij enkel de Ondertekenaar** uit - Adobe Acrobat Sign laat u de rollen voor de ontvangers van de Overeenkomst voorbij enkel de Ondertekenaar uitbreiden om hun werkschemavereisten beter aan te passen. Wanneer toegelaten, heeft elke ontvanger in een Overeenkomst zijn rol individueel configureerbaar, met Ondertekenaar die het gebrek is.


* **[AEM Forms op volledig installatieprogramma JEE ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/forms/install-aem-forms/jee-installation/aem-forms-jee-supported-platforms)** - het de dienstpak brengt een volledig installatieprogramma voor AEM Forms op JEE die steun voor veelvoudige nieuwe softwarecombinaties, met inbegrip van brengt:
   * Microsoft® Windows Server 2022
   * Microsoft® Active Directory 2022
   * Oracle WebLogic 14C op Windows Server 2022
   * Red Hat® JBoss® 7.4.10
   * MongoDB 6.0 <!-- it was previously MongoDB 4.4 -->
   * MySQL JDBC-connector 8

Als u de nieuwste software voor uw AEM 6.5 Forms in JEE-omgeving installeert of wilt gebruiken, raadt Adobe u aan AEM 6.5.18.0 Forms in te schakelen op het volledige installatieprogramma van JEE. Raadpleeg de documentatie voor AEM Forms op JEE of AEM Forms op OSGi voor meer informatie over de volledige lijst met nieuw toegevoegde en vervangen software.

## AEM 6.5, Service Pack 17—25 mei 2023

* **de ervaringsverhogingen van het Onderzoek** - u kunt de volgende verrichtingen op de activa nu snel uitvoeren die in de onderzoeksresultaten tonen:
   * Een workflow maken
   * Een versie maken
   * Relatieve of niet-gerelateerde elementen

  U hoeft niet naar de middelenlocatie te navigeren en de eigenschappen ervan te bekijken om deze bewerkingen uit te voeren.

* **de Dynamische Momentopname van Media 1} _laat u de bepalingen van het voorproefbeeld en Slimme optimalisaties van het Beeld - zoals output WebP of AVIF, bandbreedte-bewuste compressie, en het schrapen van de Verhouding van het Pixel van het Apparaat - gebruikend testbeelden of Dynamische Media URLs._**Vervolgens kunt u direct vergelijken hoe elke instelling de kwaliteit en de bestandsgrootte beïnvloedt.
Zie [ Dynamische Momentopname van Media ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot).
* **DASH die met Dynamische Media** stroomt - Nieuw protocol (DASH - Dynamische Aanpassings het Streamen over HTTP) voor Aanpassings het Streamen in Dynamische Media video levering (met toegelaten CMAF) wordt gelanceerd. Nu beschikbaar voor alle regio&#39;s.
* **Integratie van Experience Manager Sites en de Fragmenten van de Inhoud met de Dynamische Media van de Volgende-Generatie van Assets** - De gebruikers kunnen hun wolk-ontvangen activa in Experience Manager Sites 6.5 nu gebruiken. Ze kunnen deze middelen op Managed Services- of on-premise instanties ontwerpen en leveren.

### [!DNL Forms]

* **[Aangepaste Forms binnen de Redacteur van de Pagina van AEM](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md)** - u kunt de Redacteur van de Pagina van AEM nu gebruiken om veelvoudige vormen tot stand te brengen en snel toe te voegen aan uw plaatspagina&#39;s. Met deze functie kunnen auteurs van inhoud naadloze ervaringen met gegevensvastlegging op sitepagina&#39;s maken met behulp van de kracht van adaptieve formuliercomponenten, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van registratie- en bedrijfsprocesautomatisering. U kunt:
   * Maak een adaptief formulier door formuliercomponenten te slepen en neer te zetten op de Adaptive Forms Container Component in AEM Sites Editor of Experience Fragments.
   * Met de wizard Adaptive Forms in de AEM Sites-editor kunt u formulieren maken die onafhankelijk zijn van elke sitepagina, zodat u dergelijke formulieren op meerdere pagina&#39;s kunt hergebruiken.
   * Voeg meerdere formulieren toe aan een sitepagina, zodat de gebruikerservaring wordt gestroomlijnd en er meer flexibiliteit wordt geboden.
* **[Steun van reCAPTCHA Onderneming in Experience Manager Forms](/help/forms/using/captcha-adaptive-forms.md)** - toegevoegde steun voor reCAPTCHA Onderneming in Experience Manager Forms. Deze mogelijkheid biedt een betere bescherming tegen frauduleuze activiteiten en spam, naast de bestaande Google reCAPTCHA v2-ondersteuning.
* **[toegevoegde steun voor Adobe Acrobat Sign voor Regering met Experience Manager Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md)** - AEM Forms integreert nu met Adobe Acrobat Sign voor Regering (volgzame FedRAMP). Deze integratie biedt een geavanceerd niveau van naleving en beveiliging voor e-handtekeningen met Adaptief formulier-inzendingen voor met de overheid verband houdende rekeningen (overheidsdiensten en agentschappen). Dankzij de integratie met Adobe Acrobat Sign for Government kunnen Adobe-partners en overheidsklanten in Adaptive Forms elektronische handtekeningen gebruiken voor een aantal van de meest bedrijfskritieke en gevoelige bedrijfsonderdelen. Deze extra laag van veiligheid zorgt ervoor dat alle e-handtekeningen volledig volgzaam met de Matige naleving FedRAMP zijn, die de klanten van de overheid van Adobe van mening voorzien.
* **laat de integratie van Salesforce met Experience Manager Forms voor gegevensuitwisseling** toe - vorm de integratie tussen Experience Manager Forms en de toepassing van Salesforce gebruikend de OAuth 2.0 cliëntgeloofsstroom. Deze mogelijkheid maakt een veilige en directe verificatie en verificatie van de toepassing mogelijk en maakt naadloze communicatie zonder betrokkenheid van de gebruiker mogelijk.
* **Optimalisering en verbeterde functionaliteit van werkschemamotor**: Verhoog de prestaties van de werkschemamotoren door het aantal werkschemainstanties te minimaliseren. Naast `COMPLETED` - en `RUNNING` -statuswaarden ondersteunt de workflow ook drie nieuwe statuswaarden: `ABORTED` , `SUSPENDED` en `FAILED` .

## AEM 6.5, Service Pack 16-23 februari 2023

Het nieuwe protocol DASH (het Dynamische Aanpassings Streamen over HTTP) lanceerde voor het adaptieve bitrate stromen in Dynamische Video van Media levering (met CMAF [ toegelaten het Gemeenschappelijke Formaat van de Toepassing van Media ]).

* Adaptief streamen (DASH/HLS) zorgt voor een betere weergave voor eindgebruikers voor video&#39;s.
* DASH is het internationale standaardprotocol voor adaptieve videostreaming en wordt op grote schaal toegepast in de branche.
* Beschikbaar nu in Azië-Stille Oceaan en Noord-Amerika; binnenkort verkrijgbaar in Europa-Midden-Oost-Afrika.

### [!DNL Forms]

* [ Koploze Aanpassings Forms ](https://experienceleague.adobe.com/en/docs/experience-manager-headless-adaptive-forms/using/overview) laat uw ontwikkelaars toe om, interactieve vormen tot stand te brengen te publiceren en te beheren die met door APIs, eerder dan door een traditioneel grafisch gebruikersinterface kunnen worden betreden en worden in wisselwerking gestaan.

* [ de Adaptieve Componenten van de Kern van Forms ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/adaptive-forms/introduction#features) zijn een reeks 24 open-bron, BEM-volgzame componenten die op de stichting van de Componenten van de Kern van Adobe Experience Manager WCM worden voortgebouwd. Deze componenten zijn open-source en bieden ontwikkelaars de mogelijkheid om deze componenten eenvoudig aan te passen en uit te breiden om aan de specifieke behoeften van hun organisatie te voldoen. Iedereen met bestaande vaardigheden om [ componenten van de Kern WCM ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/get-started/authoring) aan te passen kan deze componenten gemakkelijk aanpassen en opmaken.

* De Reader Extension Service op OSGi biedt nu verschillende opties om invoer- en exportgebruiksrechten op een PDF mogelijk te maken voor het importeren of exporteren van gegevens in Adobe Acrobat Reader.

## AEM 6.5, Service Pack 15-November 24, 2022

### [!DNL Forms]

* AEM Forms Designer is nu beschikbaar in [ Spaanse scène ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).
* U kunt [ OAuth2 nu gebruiken om met Microsoft® Office voor authentiek te verklaren 365 de protocollen van de postserver (SMTP en IMAP) ](/help/forms/using/oauth2-support-for-mail-service.md).
* U kunt [ Revalidate op server ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions#enabling-server-side-validation-br) bezit aan waar plaatsen om de verborgen gebieden voor uitsluiting van een Document van Verslag op de server-kant te identificeren.
* AEM Forms Designer vereist een versie met 32 bits van Visuele C++ 2019 Redistributable (x86).

## AEM 6.5, Service Pack 14-augustus 25, 2022

Alleen opgeloste problemen.

## AEM 6.5, Service Pack 13 - 26 mei 2022

* Gebruik onzichtbare CAPTCHA in een adaptieve vorm: u kunt nu een onzichtbare CAPTCHA gebruiken om de CAPTCHA-uitdaging alleen te tonen als er sprake is van verdachte activiteit. Als geen verdachte activiteit wordt gevonden, wordt de uitdaging CAPTCHA niet getoond. Het helpt menselijke vormvoltooiing zonder controledoosvereisten beoordelen, aanpassingsinspanningen verminderen, en de eindgebruikerservaring verbeteren.

* Extra ondersteuning voor het ophalen van antwoordheaders in de nabewerker van het formuliergegevensmodel voor REST-eindpunten.

* Bij het genereren van een adaptief formuliervertaalbestand is nu dezelfde reeks tekst in het gegenereerde XLIFF-bestand identiek aan de reeks componenten in het corresponderende adaptieve formulier.

* Wanneer u een adaptief formulier lokaliseert en zelfs een kleine wijziging aanbrengt in de tekst van de basistaal, ontbreekt de volledige vertaling voor alle andere talen. Het probleem is opgelost in [!DNL Experience Manager] 6.5.13.0 .

* Verbeterde toegankelijkheid voor Forms:

   * Extra ondersteuning voor schermlezers om de koptekst en hoofdtekst van een tabel te herkennen als continue en verbonden entiteiten. Schermlezers kunnen hierdoor gemakkelijker door de tabellen navigeren. (NPR-37139)
   * Extra ondersteuning voor schermlezers om te stoppen met navigeren in de HTML-werkruimte totdat een dialoogvenster is geopend.

## AEM 6.5, Service Pack 12-24 februari 2022

* Nadat u een verbinding tussen externe DAM- en Sites-implementaties hebt geconfigureerd, worden de middelen op externe DAM beschikbaar gesteld op de implementatie van Sites. U kunt de update uitvoeren, verwijderen, hernoemen en bewerkingen verplaatsen op de externe DAM-middelen of -mappen. De updates zijn, met wat vertraging, automatisch beschikbaar op de plaatsing van Plaatsen.
* Het is nu standaard mogelijk om een actieve-kopieerbron naar meerdere actieve kopieën te verschuiven, zonder dat hiervoor een blauwdrukconfiguratie nodig is.
* De status van asynchrone bewerkingen in uitvoering wordt nu weergegeven in de gebruikersinterface om te voorkomen dat gebruikers per ongeluk meerdere asynchrone bewerkingen op hetzelfde pad activeren.
* Ondersteuning voor op IMS gebaseerde verificatie wordt geboden voor API&#39;s van Analytics 2.0.
* API-ondersteuning voor JSON biedt type Experience Fragment.
* Aanbiedingsaanvraag is nu beschikbaar voor de functie Verwijderen (Experience Fragment API) in IMS.
* De ingebouwde opslagplaats (Apache Jackrabbit Oak) blijft op 1.22.9.
