---
title: Verlopen Reader Extension-servicecertificaten bijwerken
description: 'Uitgebreide documenten Readers werkt niet, certificaten bijwerken '
source-git-commit: a26e4fb53458beae9b259e5ee5dc74a95264f9e1
workflow-type: tm+mt
source-wordcount: '1575'
ht-degree: 0%

---


# Verlopen Reader Extension-servicecertificaten bijwerken {#Updating-expired-Reader-Extension-service-certificates}

Adobe Experience Manager Forms (AEM Forms)-klanten met Adobe Managed Services of On-premise Enterprise Base-licenties hebben het recht om de service Reader Extension te gebruiken. Met deze service kan een organisatie eenvoudig interactieve PDF-documenten delen door de functionaliteit van Adobe Reader uit te breiden met extra gebruiksrechten. De service voegt gebruiksrechten toe aan een PDF-document en activeert functies die gewoonlijk niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Acrobat Reader DC, zoals het toevoegen van opmerkingen aan een document, het invullen van formulieren en het opslaan van het document. Gebruikers van derden hebben geen extra software of plug-ins nodig om met documenten waarvoor rechten zijn ingeschakeld te kunnen werken. PDF-documenten waaraan gebruiksrechten zijn toegevoegd, worden documenten waarvoor rechten zijn ingeschakeld genoemd. Een gebruiker die een voor rechten geschikt PDF-document in Adobe Reader opent, kan de bewerkingen uitvoeren die voor dat document zijn ingeschakeld.

Adobe maakt gebruik van een PKI (Public Key Infrastructure) om digitale certificaten uit te geven voor gebruik in licenties en functionaliteit. Adobe heeft certificaten uitgegeven onder de certificeringsinstantie &quot;Adobe Root CA&quot;, die volgens de planning op 7 januari 2023 afloopt. Dit zal leiden tot het verlopen van alle certificaten die zijn uitgegeven onder deze certificeringsinstantie. Nadat het certificaat is verlopen, werken alle functies die afhankelijk zijn van de certificaten niet meer. Een PDF-document met uitgebreide lezer dat bijvoorbeeld het toevoegen van opmerkingen met Adobe Acrobat Reader toestaat, werkt niet meer na 7 januari 2023 voor klanten. Om de kwestie op te lossen, zou de beheerder van de dienst van de Uitbreiding van de Reader, gebruikend oude certificaten, nieuwe die certificaten verkrijgen en opnieuw toepassen door nieuwe Adobe Root CA G2 aan hun documenten van de PDF (lezer breidt de documenten van de PDF met nieuwe certificaten uit) worden uitgegeven.

De vervaldatum van certificaten is van invloed op zowel AEM Forms op JEE als AEM Forms op OSGi-stapels. Beide stapels hebben een andere set instructies. Na vergadering [vooraanvragen](#Pre-requisites) en [nieuwe certificaten verkrijgen](#obtain-the-certificates)Kies, afhankelijk van de stapel, een van de volgende paden:

* [Certificaten bijwerken voor een AEM Forms in JEE-omgeving](#Updating-and-Applying-certificates-for-an-AEM-Forms-on-JEE-environment)
* [Certificaten bijwerken voor een AEM Forms in een OSGi-omgeving](#Updating-and-applying-certificates-for-an-AEM-Forms-on-OSGi-environment)

>[!NOTE]
>
>Het document gebruikt onderling verwisselbare term certificaten en referenties.

## Voorwaarden {#Pre-requisites}

Voor het bijwerken van de certificaten moeten handelingen worden gebruikt die beschikbaar zijn op de AEM Forms-beheerconsole en de Reader Extension API&#39;s van AEM Forms. Het document is bedoeld voor gebruikers en beheerders die bekend zijn met het gebruik van Adobe Experience Manager Forms API&#39;s. Voordat u begint, moet u ervoor zorgen dat:

* de gebruiker beheerdersrechten heeft op de onderliggende AEM Forms-omgeving.
* de gebruiker heeft ingesteld dat [ontwikkelomgeving](https://experienceleague.adobe.com/docs/experience-manager-65/developing/devtools/howto-projects-eclipse.html) en heeft er toegang tot.
* de certificaten verkrijgen.

### Certificaten ophalen {#obtain-the-certificates}

De rechtenreferentie wordt geleverd als een digitaal certificaat dat de openbare sleutel, de persoonlijke sleutel en het wachtwoord bevat dat wordt gebruikt om toegang te krijgen tot de referentie.

Als uw organisatie een productieversie van de Uitbreidingen van de Reader koopt, wordt de productierechtenreferentie geleverd door de Website van de Vergunning van de Adobe (LWS). Een productierechten-referentie is uniek voor uw organisatie en kan de specifieke gebruiksrechten inschakelen die u nodig hebt.

Als u de Uitbreidingen van de Reader door een partner of softwareleverancier hebt verkregen die de Uitbreidingen van de Reader in hun software integreerde, wordt de referentie van Rechten verstrekt aan u door die partner die, beurtelings, deze referentie van Adobe ontvangt.

>[!NOTE]
>
>De rechtenreferentie kan niet worden gebruikt voor het ondertekenen of bevestigen van de identiteit van typische documenten. Voor deze toepassingen kunt u een zelfondertekend certificaat gebruiken of een identiteitscertificaat verkrijgen van een certificeringsinstantie (CA).

De volgende soorten geloofsbrieven van Rechten zijn beschikbaar:

**Klantenbeoordeling**: Een referentie met een korte geldigheidsperiode die wordt verstrekt aan klanten die de Uitbreidingen van de Reader willen evalueren. Gebruiksrechten die worden toegepast op documenten die deze referentie gebruiken, verlopen wanneer de referentie verloopt. Dit type referentie is slechts twee tot drie maanden geldig.

**Productie**: Een referentie met een lange geldigheidsperiode die wordt verstrekt aan klanten die het volledige product hebben gekocht. De geloofsbrieven van de productie zijn uniek aan elke klant maar kunnen op veelvoudige systemen worden geïnstalleerd.

Als u al certificaten hebt gebruikt voor het uitbreiden van PDF-bestanden met Reader, kunt u een productiecertificaat downloaden van [Adobe Licensing Website (LWS)](https://licensing.adobe.com/).

## Certificaten bijwerken en toepassen voor een AEM Forms on JEE-omgeving {#Updating-and-Applying-certificates-for-an-AEM-Forms-on-JEE-environment}

Voor het bijwerken en toepassen van nieuwe certificaten op AEM Forms in de JEE-stapel moeten nieuwe gegevens worden geïmporteerd, moeten gebruiksrechten uit bestaande PDF-documenten worden verwijderd en moeten gebruiksrechten worden toegepast. U kunt beheerconsole gebruiken om referenties te importeren en AEM Forms Reader Extension API&#39;s om gebruiksrechten te verwijderen en toe te passen.

### Referenties importeren en configureren

Met de pagina&#39;s Betrouwbaarheidswinkelbeheer kunt u een nieuwe of vervangende referentie importeren. De Trust Store kan meer dan één referentie voor extensies voor Readers bevatten. U moet één van die geloofsbrieven als referentie van de Uitbreidingen van de standaardReader aanwijzen. De standaardreferentie wordt gebruikt wanneer een Workbench-gebruiker niet kan bepalen welke referentie moet worden gebruikt tijdens het maken van processen. Deze regels zijn van toepassing op standaardreferenties:

* Als u een referentie voor extensies voor Readers importeert en de Trust Store geen andere referenties voor extensies voor Readers bevat, wordt deze ingesteld als de standaardinstelling.
* Als u een referentie voor extensies voor Readers importeert terwijl de optie Standaard is ingeschakeld, wordt het standaardtype verwijderd uit een bestaande standaardreferentie. De geïmporteerde referentie wordt de standaardinstelling.
* U kunt geen referentie voor standaardextensies voor Readers verwijderen. Als u de standaardreferentie wilt verwijderen, stelt u eerst een andere referentie in als de standaardreferentie. Een uitzondering op deze regel is dat als er slechts één referentie is, u het kunt schrappen alhoewel het het gebrek is.
* U kunt een standaardreferentie voor extensies voor Readers niet bijwerken.

De referenties importeren:

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op Importeren en selecteer Acrobat Reader DC Extension Credential onder Type vertrouwde winkel.
1. (Optioneel) Selecteer Standaard om aan te geven dat deze referentie de standaardreferentie is voor gebruik met Acrobat Reader DC-extensies.
1. Typ in het vak Alias een id voor de referentie. Deze id wordt gebruikt als de weergavenaam voor de referentie in Acrobat Reader DC-extensies. Deze alias wordt ook gebruikt om de referentie via programmacode te benaderen met de SDK voor AEM formulieren.
1. Klik op Bestand kiezen om de referentie te zoeken, typ het wachtwoord van de referentie en klik op OK.

Als het foutbericht &quot;Kan referentie niet importeren vanwege een onjuiste bestandsindeling of een onjuist wachtwoord&quot; wordt weergegeven, controleert u of het wachtwoord geldig is.

U kunt geloofsbrieven ook invoeren en schrappen programmatically. (Zie [Programmeren met AEM formulieren](../../developing/credentials.md).)

### Gebruiksrechten verwijderen uit bestaande PDF-documenten waarvoor rechten zijn ingeschakeld

Verwijder gebruiksrechten uit bestaande PDF-documenten waarvoor gebruiksrechten zijn ingeschakeld voordat u gebruiksrechten toepast met de meest recente gegevens. AEM Forms on JEE biedt API&#39;s om gebruiksrechten te verwijderen. Zie voor gedetailleerde instructies [Gebruiksrechten verwijderen uit PDF-documenten](../../developing/assigning-usage-rights.md#removing-usage-rights-from-pdf-documents).

Als u gebruiksrechten voor AEM Forms wilt verwijderen voor JEE-processen die zijn ontwikkeld in Workbench, raadpleegt u [Workbench Help](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/WorkbenchHelp.pdf).

### Gebruikersrechten toepassen op PDF-documenten

Nadat nieuwe geloofsbrieven en het verwijderen van gebruiksrechten uit bestaande rechten-toegelaten PDF documenten invoeren, pas gebruiksrechten op PDF documenten toe gebruikend de nieuwe geloofsbrieven. U kunt gebruiksrechten toepassen op PDF-documenten met de Acrobat Reader DC Extension Java Client API en webservice.  Zie voor meer informatie [Gebruiksrechten toepassen op PDF-documenten](../../developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents).


## Certificaten bijwerken en toepassen voor een AEM Forms in een OSGi-omgeving {#Updating-and-applying-certificates-for-an-AEM-Forms-on-OSGi-environment}

Voor het bijwerken en toepassen van nieuwe certificaten op AEM Forms in de OSGi-stapel moeten nieuwe gegevens worden geïmporteerd, moeten gebruiksrechten uit bestaande PDF-documenten worden verwijderd en gebruiksrechten worden toegepast. U kunt beheerconsole gebruiken om referenties te importeren en AEM Forms Reader Extension API&#39;s om gebruiksrechten te verwijderen en toe te passen.

### Referenties importeren {#Import-credentials}

In een AEM Forms op milieu OSGi, wordt een referentie van de Uitbreiding van de Reader geassocieerd met fd-dienst gebruiker. Voordat u referenties toevoegt voor het sleutelarchief van de gebruiker, voert u de volgende stappen uit om een sleutelarchief te maken:

1. Meld u als beheerder aan bij de AEM-auteur.
1. Ga naar **[!UICONTROL Tools]**> **[!UICONTROL Security]**>**[!UICONTROL Users]**.
1. Blader omlaag in de lijst met gebruikers totdat u een gebruikersaccount voor fd-service vindt.
1. Klikken **[!UICONTROL fd-service]** gebruiker.
1. Klik op het tabblad sleutelarchief.
1. Klik op **[!UICONTROL Create KeyStore]**.
1. Stel het wachtwoord voor toegang tot KeyStore in en sla uw instellingen op om het wachtwoord voor KeyStore te maken.

Nadat u de sleutelarchief hebt gemaakt, voegt u referenties toe aan de gebruiker van de fd-service. In de volgende video worden de stappen beschreven:

>[!VIDEO](https://images-tv.adobe.com/mpcv3/5577/8db8e554-f04b-4fae-8108-b9b5e0eb03ad_1627925794.854x480at800_h264.mp4)

De volgende opdracht geeft een overzicht van de details van het pfx-bestand. Navigeer voordat u de opdracht uitvoert naar de map met het .pfx-bestand.

`keytool -v -list -storetype pkcs12 -keystore <name of your .pfx file>`

Bijvoorbeeld keytool -v -list -storetype pkcs12 -keystore 1005566.pfx waarbij 1005566.pfx de naam van mijn pfx-bestand is

### Gebruiksrechten verwijderen uit bestaande PDF-documenten waarvoor rechten zijn ingeschakeld

Verwijder gebruiksrechten uit bestaande PDF-documenten waarvoor gebruiksrechten zijn ingeschakeld voordat u gebruiksrechten toepast met de meest recente gegevens. U kunt de gebruiksrechten voor een document verwijderen door de removeUsageRights-API aan te roepen vanuit de docAssuranceServiceAPI. Zie voor meer informatie [Gebruiksrechten verwijderen](/help/forms/using/aem-document-services-programmatically.md#removing-usage-rights) document.

### Gebruikersrechten toepassen op PDF-documenten

Om gebruiksrechten in een AEM Forms op milieu OSGi toe te passen, creeer de dienst van douane OSGi aan gebruiksrechten op de documenten. U kunt ook een servlet met een methode van de POST tot stand brengen om de lezer uitgebreide PDF aan de gebruiker terug te keren. Zie voor gedetailleerde instructies [Reader-extensies toepassen](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/document-services/apply-reader-extension-rights-to-pdf.html).

## Veelgestelde vragen

**Met wie moet ik contact opnemen als ik nog meer vragen heb?**

U kunt contact opnemen met [Adobe-ondersteuning](https://experienceleague.adobe.com/?support-solution=Experience+Manager#support) of een ondersteuningsticket opsteken.

**Wat gebeurt er als ik mijn certificaat niet bijwerk voor 7 januari 2023?**

Als gebruikers proberen een PDF-document te openen dat is Reader Extended met oude-certificaten, krijgen ze een foutbericht en hebben ze geen toegang meer tot de functies die zijn uitgebreid met de lezer. Een voorbeeldfout is.

`The document has been changed since it was created and use of extended features in no longer available. Please contact the author for the orignal version of this document.`

**Is er een wijziging in de naam van de nieuwe beschrijving?**

In nieuwe Reader Extension-certificaten wordt G3-P24 in de beschrijving als programmenaam vermeld. In de oudere certificaten werd de naam P24 vermeld in de beschrijving.