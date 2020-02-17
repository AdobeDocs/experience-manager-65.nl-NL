---
title: Openingspagina's
seo-title: Openingspagina's
description: Met de functie voor het plaatsen van pagina's kunt u snel en eenvoudig een ontwerp en inhoud rechtstreeks in een AEM-pagina importeren. Een webontwikkelaar kan de HTML en aanvullende elementen voorbereiden die als een volledige pagina of als een deel van een pagina kunnen worden geïmporteerd.
seo-description: Met de functie voor het plaatsen van pagina's kunt u snel en eenvoudig een ontwerp en inhoud rechtstreeks in een AEM-pagina importeren. Een webontwikkelaar kan de HTML en aanvullende elementen voorbereiden die als een volledige pagina of als een deel van een pagina kunnen worden geïmporteerd.
uuid: b294c43f-63ae-4b5b-bef0-04566e350b63
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
discoiquuid: 061dee36-a3bb-4166-a9c1-3ab7e4de1d1d
docset: aem65
translation-type: tm+mt
source-git-commit: 016c705230dffec052c200b058a36cdbe0520fc4

---


# Openingspagina&#39;s{#landing-pages}

Met de functie voor het plaatsen van pagina&#39;s kunt u snel en eenvoudig een ontwerp en inhoud rechtstreeks in een AEM-pagina importeren. Een webontwikkelaar kan de HTML en aanvullende elementen voorbereiden die als een volledige pagina of als een deel van een pagina kunnen worden geïmporteerd. De functionaliteit is nuttig om bestemmingspagina&#39;s tot stand te brengen die slechts voor een beperkte tijd actief zijn en snel moeten worden gecreeerd.

Deze pagina beschrijft het volgende:

* welke landingspagina&#39;s er in AEM uitzien, inclusief de beschikbare componenten
* hoe u een openingspagina maakt en hoe u een ontwerppakket importeert
* werken met bestemmingspagina&#39;s in AEM
* mobiele bestemmingspagina&#39;s instellen

Het voorbereiden van het ontwerppakket voor het invoeren wordt behandeld in het [Uitbreiden en het Vormen van de Importeur](/help/sites-administering/extending-the-design-importer-for-landingpages.md)van het Ontwerp. Integratie met Adobe Analytics is inbegrepen bij het [integreren van bestemmingspagina&#39;s met Adobe Analytics.](/help/sites-administering/integrating-landing-pages-with-adobe-analytics.md)

>[!CAUTION]
>
>De importmodule voor ontwerpen, die wordt gebruikt voor het importeren van bestemmingspagina&#39;s, [is vervangen door AEM 6.5](/help/release-notes/deprecated-removed-features.md#deprecated-features).

>[!CAUTION]
>
>Omdat de Design Importer toegang tot vereist `/apps`, zal het niet werken in containerized wolkmilieu&#39;s waar onveranderlijk `/apps` is.

## Wat zijn bestemmingspagina&#39;s? {#what-are-landing-pages}

Landingspagina&#39;s zijn sites met één of meerdere pagina&#39;s die het &#39;eindpunt&#39; zijn van een marketingstrategie, bijvoorbeeld met e-mail, adwords/banners, sociale media. Een landingspagina kan verschillende doelen dienen, maar heeft allemaal één ding gemeen: de bezoeker moet een taak uitvoeren en dat bepaalt het succes van een landingspagina.

Met de functie Landing Pages in AEM kunnen marketers samenwerken met webontwerpers bij agentschappen of interne creatieve teams om paginaontwerpen te maken die gemakkelijk kunnen worden geïmporteerd in AEM en die nog steeds bewerkbaar zijn voor de marketers en worden gepubliceerd onder hetzelfde bestuur als de rest van de AEM-sites.

In AEM, creeert u landende pagina&#39;s door de volgende stappen uit te voeren:

1. Maak in AEM een pagina die het canvas van de bestemmingspagina&#39;s bevat. AEM wordt geleverd met een voorbeeld met de naam **Importer Page**.

1. [Bereid de HTML en de activa voor.](/help/sites-administering/extending-the-design-importer-for-landingpages.md)
1. Verpak de middelen in een dossier van het PIT dat hier als het Pakket van het Ontwerp wordt bedoeld.
1. Importeer het ontwerppakket op de pagina Importeren.
1. Wijzig en publiceer de pagina.

### Openingspagina&#39;s bureaublad {#desktop-landing-pages}

Een voorbeeldlandingspagina in AEM ziet er als volgt uit:

![chlimage_1-2](assets/chlimage_1-2.jpeg)

### Mobiele bestemmingspagina&#39;s {#mobile-landing-pages}

Een openingspagina kan ook een mobiele versie van de pagina hebben. Voor een aparte mobiele versie van de bestemmingspagina moet het importontwerp twee HTML-bestanden hebben: *index.htm(l)* en *mobile.index.htm(l)*.

De invoerprocedure voor de landingspagina is dezelfde als die van een normale openingspagina. Het ontwerp van de bestemmingspagina heeft een extra HTML-bestand dat overeenkomt met de bestemmingspagina. Dit HTML-bestand moet ook een canvas hebben `div` met `id=cqcanvas` net als de bestemmingspagina van het bureaublad html en het ondersteunt alle bewerkbare componenten die worden beschreven voor de openingspagina van het bureaublad.

De mobiele openingspagina wordt gemaakt als een onderliggende pagina van de openingspagina van het bureaublad. Navigeer naar de openingspagina in Websites en open de onderliggende pagina om deze te openen.

![chlimage_1-22](assets/chlimage_1-22.png)

>[!NOTE]
>
>De landingspagina voor mobiele apparaten wordt samen met de bestemmingspagina verwijderd of gedeactiveerd als de bestemmingspagina van het bureaublad wordt verwijderd of gedeactiveerd.

## Onderdelen van bestemmingspagina {#landing-page-components}

Als u onderdelen van de HTML die worden geïmporteerd, bewerkbaar wilt maken in AEM, kunt u inhoud binnen de HTML-landingspagina&#39;s rechtstreeks toewijzen aan AEM-componenten. De ontwerpimporteur begrijpt standaard de volgende componenten:

* Tekst, voor alle tekst
* Titel, voor inhoud in H1-6-tags
* Afbeelding, voor afbeeldingen die uitwisselbaar moeten worden gemaakt
* Oproep aan acties:

   * Koppeling doorklikken
   * Grafische koppeling

* CTA leiden-Vorm, om gebruikersinformatie te vangen
* Het Systeem van de paragraaf (Parsys), om het even welke component toe te staan om worden toegevoegd, of de bovengenoemde component om te zetten

Bovendien is het mogelijk om dit uit te breiden en douanecomponenten te steunen. In deze sectie worden de componenten gedetailleerd beschreven.

### Tekst {#text}

Met de component Text kunt u een tekstblok invoeren met een WYSIWYG-editor. Zie [Tekstcomponent](/help/sites-authoring/default-components.md#text) voor meer informatie.

![chlimage_1-23](assets/chlimage_1-23.png)

Hieronder ziet u een voorbeeld van een tekstcomponent op een bestemmingspagina:

![chlimage_1-24](assets/chlimage_1-24.png)

#### Titel {#title}

Met de titelcomponent kunt u een titel weergeven en de grootte configureren (h1-6). Zie [Titelcomponent](/help/sites-authoring/default-components.md#title) voor meer informatie.

![chlimage_1-25](assets/chlimage_1-25.png)

Hieronder ziet u een voorbeeld van een titelcomponent op een landingspagina:

![chlimage_1-26](assets/chlimage_1-26.png)

#### Image {#image}

De afbeeldingscomponent toont een afbeelding die u kunt slepen en neerzetten vanuit de Inhoudszoeker of waarop u kunt klikken om te uploaden. Zie de [afbeeldingscomponent](/help/sites-authoring/default-components.md) voor meer informatie.

![chlimage_1-27](assets/chlimage_1-27.png)

Hieronder ziet u een voorbeeld van een afbeeldingscomponent op een landingspagina:

![chlimage_1-28](assets/chlimage_1-28.png)

#### Oproep tot actie (CTA) {#call-to-action-cta}

Een landingspagina-ontwerp kan verscheidene verbindingen hebben - sommige kunnen als &quot;Vraag aan actie&quot;worden bedoeld.

De oproep tot actie (CTA) wordt gebruikt om de bezoeker te krijgen onmiddellijk actie op de landende pagina zoals &quot;Abonneren nu,&quot;Bekijk deze video,&quot;Beperkte Tijd slechts&quot;etc.

* Klik via koppeling - Hiermee kunt u een tekstkoppeling toevoegen waarmee de bezoeker naar een doel-URL gaat wanneer erop wordt geklikt.
* Grafische koppeling - Hiermee kunt u een afbeelding toevoegen die de bezoeker naar een doel-URL stuurt wanneer erop wordt geklikt.

Beide componenten CTA hebben gelijkaardige opties. De optie Doorklikken via koppeling heeft extra tekstopties. De componenten worden in de volgende alinea&#39;s uitgebreid beschreven.

#### Klikken door koppeling {#click-through-link}

Deze component CTA kan worden gebruikt om een tekstverbinding op de het landen pagina toe te voegen. Op die koppeling kan worden geklikt om de gebruiker naar de doel-URL te brengen die in de componenteigenschappen is opgegeven. Het maakt deel uit van de &quot;Vraag aan Actie&quot;groep.

![chlimage_1-29](assets/chlimage_1-29.png)

**Label** De tekst die gebruikers zien. U kunt opmaak wijzigen met de RTF-editor.

**Doel-URL** Voer de URI in die gebruikers moeten bezoeken als ze op de tekst klikken.

**Renderopties** beschrijft renderopties. U kunt een van de volgende opties selecteren:

* Pagina laden in een nieuw browservenster
* Pagina in huidig venster laden
* Pagina in het bovenliggende frame laden
* Alle frames annuleren en pagina in volledig browservenster laden

**In CSS** op het tabblad Stijl voert u een pad naar de CSS-stijlpagina in.

**ID** op het tabblad Stijl voert u een id in waarmee de component deze op unieke wijze kan identificeren.

Hieronder ziet u een voorbeeld van een klik door een koppeling:

![chlimage_1-30](assets/chlimage_1-30.png)

#### Grafische koppeling {#graphical-link}

Deze component CTA kan worden gebruikt om het even welk grafisch beeld met verbinding op de het landen pagina toe te voegen. De afbeelding kan een eenvoudige knop zijn of een grafische afbeelding als achtergrond. Wanneer op de afbeelding wordt geklikt, gaat de gebruiker naar de doel-URL die in de componenteigenschappen is opgegeven. Het maakt deel uit van de groep **Call to Action** .

![chlimage_1-31](assets/chlimage_1-31.png)

**Label** De tekst die gebruikers in de afbeelding zien. U kunt opmaak wijzigen met de RTF-editor.

**Doel-URL** Voer de URI in die gebruikers moeten bezoeken als ze op de afbeelding klikken.

**Renderopties** beschrijft renderopties. U kunt een van de volgende opties selecteren:

* Pagina laden in een nieuw browservenster
* Pagina in huidig venster laden
* Pagina in het bovenliggende frame laden
* Alle frames annuleren en pagina in volledig browservenster laden

**In CSS** op het tabblad Stijl voert u een pad naar de CSS-stijlpagina in.

**ID** op het tabblad Stijl voert u een id in waarmee de component deze op unieke wijze kan identificeren.

Hier volgt een voorbeeld van een grafische koppeling:

![chlimage_1-32](assets/chlimage_1-32.png)

### Oproep tot actie (CTA) Lead Form {#call-to-action-cta-lead-form}

Een formulier voor leads is een formulier dat wordt gebruikt om de profielgegevens van een bezoeker/lead te verzamelen. Deze informatie kan later worden opgeslagen en gebruikt om een efficiënte marketing te doen die op de informatie wordt gebaseerd. Deze informatie omvat gewoonlijk titel, naam, e-mail, geboortedatum, adres, rente, enzovoort. Het is een onderdeel van de **CTA Lead-formuliergroep** .

Een voorbeeld van een CTA-loodformulier ziet er als volgt uit:

![chlimage_1-33](assets/chlimage_1-33.png)

CTA-loodformulieren worden samengesteld uit verschillende onderdelen:

* **Loodformulier** De voorbeeldformuliercomponent definieert het begin en einde van een nieuw formulier voor leads op een pagina. Andere componenten kunnen vervolgens tussen deze elementen worden geplaatst, zoals E-mailadres, Voornaam, enzovoort.

* **Formuliervelden en -elementen** Formuliervelden en -elementen kunnen tekstvakken, keuzerondjes, afbeeldingen enzovoort bevatten. De gebruiker voert vaak een handeling uit in een formulierveld, zoals het typen van tekst. Zie de afzonderlijke formulierelementen voor meer informatie.

* **Profielcomponenten** Profielen hebben betrekking op bezoekersprofielen die worden gebruikt voor sociale samenwerking en andere gebieden waar personalisatie van bezoekers is vereist.

In het voorgaande voorbeeld wordt een voorbeeldformulier weergegeven; het bestaat uit de component **Loodformulier** (begin en einde), met de velden **Voornaam** en **E-mailadres** die worden gebruikt voor invoer en een veld **Verzenden** .

Van sidekick, zijn de volgende componenten beschikbaar voor de CTA Lood Vorm:

![chlimage_1-34](assets/chlimage_1-34.png)

#### Algemene instellingen voor veel onderdelen van formulieren voor lead {#settings-common-to-many-lead-form-components}

Hoewel elk van de componenten van het hoofdformulier een ander doel heeft, bestaan veel van deze componenten uit vergelijkbare opties en parameters.

Wanneer u een van de formuliercomponenten configureert, zijn de volgende tabbladen beschikbaar in het dialoogvenster:

* **Titel en tekst** Hier moet u de basisinformatie opgeven, zoals de titel van de component en eventuele bijbehorende tekst. In voorkomend geval kunt u ook andere belangrijke informatie definiëren, zoals of het veld meerdere selecties kan bevatten en of items kunnen worden geselecteerd.

* **Met Beginwaarden** kunt u een standaardwaarde opgeven.

* **Restricties** Hier kunt u opgeven of een veld vereist is en er beperkingen voor plaatsen gelden in dat veld (moet bijvoorbeeld numeriek zijn, enzovoort).

* **Stijl** geeft de grootte en opmaak van de velden aan.

>[!NOTE]
>
>Welke velden u ziet, is afhankelijk van de afzonderlijke component.
>
>Niet alle opties zijn beschikbaar voor alle onderdelen van het loodformulier. Zie Formulieren voor meer informatie over deze [algemene instellingen](/help/sites-authoring/default-components.md#formsgroup).

#### Voorloopformuliercomponenten {#lead-form-components}

De volgende sectie beschrijft de componenten beschikbaar aan vraag-aan-actie leiden vormen.

**Over** Hiermee kunnen gebruikers informatie toevoegen.

![chlimage_1-35](assets/chlimage_1-35.png)

**Adresveld** Hiermee kunnen gebruikers adresgegevens invoeren. Wanneer u deze component configureert, moet u de elementnaam in het dialoogvenster invoeren. De elementnaam is de naam van het formulierelement. Dit geeft aan waar in de gegevensopslagruimte de gegevens worden opgeslagen.

![chlimage_1-36](assets/chlimage_1-36.png)

**Geboortedatum** Gebruikers kunnen geboortedatum invoeren.

![chlimage_1-37](assets/chlimage_1-37.png)

**E-mailadres** Hiermee kunnen gebruikers een e-mailadres (identificatie) invoeren.

![chlimage_1-38](assets/chlimage_1-38.png)

**Voornaam** verstrekt een gebied voor gebruikers om hun voornaam in te gaan.

![chlimage_1-39](assets/chlimage_1-39.png)

**Gendergebruikers** kunnen hun geslacht selecteren in een vervolgkeuzelijst.

![chlimage_1-40](assets/chlimage_1-40.png)

**Gebruikers met achternaam** kunnen informatie over achternaam invoeren.

![chlimage_1-41](assets/chlimage_1-41.png)

**Loodformulier** Voeg deze component toe om een loodformulier aan de bestemmingspagina toe te voegen. Een lead-formulier bevat automatisch het veld Start of Lead Form en End of Lead Form. Hierna voegt u de in deze sectie beschreven componenten Formulier lead toe.

![chlimage_1-42](assets/chlimage_1-42.png)

De component Formulier lead definieert zowel het begin als het einde van een formulier met behulp van de elementen **Formulierbegin** en **Formuliereinde** . Deze worden altijd gekoppeld om ervoor te zorgen dat het formulier correct is gedefinieerd.

Nadat u het hoofdformulier hebt toegevoegd, kunt u het begin of einde van het formulier configureren door op **Bewerken** op de bijbehorende balk te klikken.

**Begin van Lead-formulier**

Er zijn twee tabbladen beschikbaar voor de configuratie van **Formulier** en **Geavanceerd**:

![chlimage_1-43](assets/chlimage_1-43.png)

**Hartelijk dank. De pagina** waarnaar wordt verwezen, is bedoeld om bezoekers te bedanken voor hun invoer. Als het formulier leeg blijft, wordt het na verzending opnieuw weergegeven.

**De Werkstroom** van het begin bepaalt welke werkschema wordt teweeggebracht zodra een loodformulier wordt voorgelegd.

![chlimage_1-44](assets/chlimage_1-44.png)

**Opties voor** advertentie De volgende opties zijn beschikbaar:

* Lead maken
* E-mailservice: Abonnee maken en toevoegen aan lijst - Gebruik deze optie als u een e-mailserviceprovider gebruikt, zoals ExactTarget.
* E-mailservice: E-mail met automatische reactie verzenden - Gebruik deze functie als u een e-mailserviceprovider gebruikt, zoals ExactTarget.
* E-mailservice: Abonnement voor gebruiker opzeggen uit lijst - Gebruik deze optie als u een e-mailserviceprovider gebruikt, zoals ExactTarget.
* Abonnement op gebruiker opzeggen

**Formulierid** De formulier-id vormt een unieke identificatie van het hoofdformulier. Gebruik de formulier-id als u meerdere formulieren op één pagina hebt; zorg ervoor zij verschillende herkenningstekens hebben.

**Laadpad** is het pad naar knoopeigenschappen dat wordt gebruikt om vooraf gedefinieerde waarden in de hoofdformuliervelden te laden.

Dit is een optioneel veld dat het pad naar een knooppunt in de repository aangeeft. Als dit knooppunt eigenschappen heeft die overeenkomen met de veldnamen, worden de desbetreffende velden op het formulier vooraf geladen met de waarde van die eigenschappen. Als er geen overeenkomst bestaat, bevat het veld de standaardwaarde.

**Clientvalidatie** geeft aan of clientvalidatie is vereist voor dit formulier (servervalidatie vindt altijd plaats). Dit kan in combinatie met de component Forms Captcha worden bereikt.

**Het type** met validatieresources definieert het type resource voor formuliervalidatie als u het volledige hoofdformulier wilt valideren (in plaats van afzonderlijke velden).

Als u het volledige formulier valideert, voert u ook een van de volgende handelingen uit:

* Een script voor clientvalidatie:
   ` /apps/<myApp>/form/<myValidation>/formclientvalidation.jsp`

* Een script voor validatie aan de serverzijde:
   ` /apps/<myApp>/form/<myValidation>/formservervalidation.jsp`

**Configuratie** van handeling Afhankelijk van de selectie in Post Options, verandert de Configuratie van handeling. Als u bijvoorbeeld Lead maken selecteert, kunt u instellen aan welke lijst de lead wordt toegevoegd.

![chlimage_1-45](assets/chlimage_1-45.png)

* **Knop** Verzenden tonen geeft aan of een knop Verzenden moet worden weergegeven of niet.

* **Naam** verzenden Een id als u meerdere verzendknoppen in een formulier gebruikt.

* **Titel** verzenden De naam die op de knop wordt weergegeven, zoals Verzenden of Verzenden.

* **De knop** Herstellen tonen Selectievakje selecteren om de knop Herstellen zichtbaar te maken.

* **Titel** opnieuw instellen De naam die wordt weergegeven op de knop Herstellen.

* **Beschrijving**-informatie die onder de knop wordt weergegeven.

## Een bestemmingspagina maken {#creating-a-landing-page}

Wanneer u een landingspagina maakt, moet u drie stappen uitvoeren:

1. Maak een importerpagina.
1. [Maak de HTML gereed voor importeren.](/help/sites-administering/extending-the-design-importer-for-landingpages.md)
1. Importeer het ontwerppakket.

### Gebruik van de ontwerpimportmodule {#use-of-the-design-importer}

Omdat bij het importeren van pagina&#39;s HTML, verificatie en tests van de pagina&#39;s moeten worden voorbereid, is het importeren van bestemmingspagina&#39;s een beheertaak. Als beheerder hebben de gebruikers die de importbewerking uitvoeren, lees-, schrijf-, maak- en verwijdermachtigingen nodig op `/apps`. Als de gebruiker niet over deze machtigingen beschikt, mislukt het importeren.

>[!NOTE]
>
>Omdat de ontwerpimportmodule is bedoeld als een beheerprogramma waarvoor lees-, schrijf-, maak- en verwijdermachtigingen zijn vereist, raadt Adobe het gebruik van de ontwerpimportmodule in productie niet aan. `/apps`

Adobe raadt u aan de importer voor ontwerpen op een testexemplaar te gebruiken. Op een testinstantie kan de import worden getest en gevalideerd door een ontwikkelaar die vervolgens verantwoordelijk is voor het implementeren van de code in de productieinstantie.

### Een importpagina maken {#creating-an-importer-page}

Voordat u het ontwerp van de bestemmingspagina kunt importeren, moet u een importerpagina maken, bijvoorbeeld in het kader van een campagne. Met de sjabloon Pagina importeren kunt u de volledige HTML-openingspagina importeren. De pagina bevat een neerzetvak waarin het ontwerppakket van de bestemmingspagina kan worden geïmporteerd door slepen en neerzetten te gebruiken.

>[!NOTE]
>
>Standaard kan een pagina Importer alleen worden gemaakt onder campagnes, maar u kunt deze sjabloon ook bedekken om een bestemmingspagina onder te maken `/content/mysite`.

Een nieuwe openingspagina maken:

1. Ga naar de **websiteconsole** .
1. Selecteer de campagne in het linkerdeelvenster.
1. Klik op **Nieuw** om het venster **Pagina** maken te openen.
1. Selecteer de sjabloon **Pagina** importeren en voeg desgewenst een titel en een naam toe en klik op **Maken**.

   ![chlimage_1-1-1](assets/chlimage_1-1-1.png)

   De nieuwe importpagina wordt weergegeven.

### De HTML voorbereiden voor importeren {#preparing-the-html-for-import}

Voordat u het ontwerppakket kunt importeren, moet de HTML worden voorbereid. Zie [Uitbreiden en het Vormen de Invoer](/help/sites-administering/extending-the-design-importer-for-landingpages.md) van het Ontwerp voor meer informatie.

### Het ontwerppakket importeren {#importing-the-design-package}

Nadat een importerpagina is gemaakt, kunt u een ontwerppakket op deze pagina importeren. Details over het maken van het ontwerppakket en de aanbevolen structuur worden uitgelegd in het [Uitbreiden en configureren van de ontwerpimport](/help/sites-administering/extending-the-design-importer-for-landingpages.md).

Ervan uitgaande dat u het ontwerppakket klaar hebt, wordt in de volgende stappen beschreven hoe u het ontwerppakket op een importerpagina kunt importeren.

1. Open de importerpagina die u eerder [hebt](#creatingablankcanvaspage)gemaakt.

   ![chlimage_1-46](assets/chlimage_1-46.png)

1. Sleep het ontwerppakket naar de dropbox. De pijl verandert van richting wanneer een pakket eroverheen wordt gesleept.
1. Als gevolg van slepen en neerzetten wordt de openingspagina weergegeven in plaats van de pagina Importer. De HTML-openingspagina is geïmporteerd.

   ![chlimage_1-2-1](assets/chlimage_1-2-1.png)

>[!NOTE]
>
>Tijdens het importeren wordt de markering om veiligheidsredenen ontsmet en om het importeren en publiceren van ongeldige opmaak te voorkomen. Hierbij wordt ervan uitgegaan dat alleen HTML is opgemaakt en dat alle andere vormen van elementen, zoals inline SVG of Web Components, worden uitgefilterd.

>[!NOTE]
>
>Als u problemen hebt met het importeren van het ontwerppakket, raadpleegt u [Problemen oplossen](/help/sites-administering/extending-the-design-importer-for-landingpages.md#troubleshooting).

## Werken met bestemmingspagina&#39;s {#working-with-landing-pages}

Het ontwerp en de elementen voor een openingspagina worden meestal gemaakt door een ontwerper, mogelijk in een bureau, met gereedschappen die deze kan gebruiken, zoals Adobe Photoshop of Adobe Dreamweaver. Wanneer het ontwerp is voltooid, stuurt de ontwerper een zip-bestand met alle elementen naar marketing. De contactpersoon bij marketing is dan verantwoordelijk voor het neerzetten van het ZIP-bestand in AEM en het publiceren van de inhoud.

Bovendien kan de ontwerper wijzigingen in de het landen pagina moeten aanbrengen nadat het door inhoud uit te geven of te schrappen en de vraag-aan-actie componenten te vormen wordt ingevoerd. Ten slotte wil de marketeer de bestemmingspagina voorvertonen en vervolgens de campagne activeren om ervoor te zorgen dat de bestemmingspagina wordt gepubliceerd.

In deze sectie wordt beschreven hoe u het volgende kunt doen:

* Een openingspagina verwijderen
* Download het ontwerppakket
* Informatie over importeren weergeven
* Een openingspagina opnieuw instellen
* [Vorm de componenten CTA en voeg inhoud aan de pagina toe](#call-to-action-cta)
* Voorvertoning van de openingspagina weergeven
* Een openingspagina activeren/publiceren

Wanneer u het ontwerppakket importeert, kunt u de opties Ontwerpen **** wissen en Geïmporteerd ZIP **** downloaden vinden in het menu Instellingen van de pagina:

![chlimage_1-3-1](assets/chlimage_1-3-1.png)

### Het geïmporteerde ontwerppakket downloaden {#downloading-the-imported-design-package}

Door het ZIP-bestand te downloaden, kunt u opnemen welk ZIP-bestand met een bepaalde bestemmingspagina is geïmporteerd. Wijzigingen die op een pagina zijn aangebracht, worden niet toegevoegd aan het postvak.

Als u het geïmporteerde ontwerppakket wilt downloaden, klikt u op Postcode **downloaden** op de werkbalk Openingspagina.

### Informatie over importeren weergeven {#viewing-import-information}

U kunt op elk gewenst moment informatie over de laatste importbewerking weergeven door op het blauwe uitroepteken boven aan de bestemmingspagina in de klassieke gebruikersinterface te klikken.

![chlimage_1-47](assets/chlimage_1-47.png)

Als het geïmporteerde ontwerppakket enkele problemen heeft, bijvoorbeeld als het verwijst naar afbeeldingen/scripts die niet in het pakket voorkomen, enzovoort, geeft de ontwerpimportmodule deze problemen weer in de vorm van een lijst. Als u de lijst met problemen wilt weergeven, klikt u in de klassieke gebruikersinterface op de koppeling voor problemen op de werkbalk Openingspagina. Klik in de volgende afbeelding op de koppeling **Problemen** oplossen om het venster Problemen importeren te openen.

![chlimage_1-3](assets/chlimage_1-3.jpeg)

### Een openingspagina opnieuw instellen {#resetting-a-landing-page}

Als u het ontwerppakket van de bestemmingspagina opnieuw wilt importeren nadat u er enkele wijzigingen in hebt aangebracht, kunt u de openingspagina &quot;wissen&quot; door boven aan de bestemmingspagina in de klassieke gebruikersinterface op **Wissen** te klikken of op Wissen in het instellingenmenu in de gebruikersinterface met geoptimaliseerde aanrakingen te klikken. Hiermee verwijdert u de geïmporteerde bestemmingspagina en maakt u een lege importpagina.

Tijdens het wissen van de openingspagina kunt u de wijzigingen in de inhoud verwijderen. Als u op **Nee** klikt, blijven de wijzigingen in de inhoud behouden. De onderliggende structuur `jcr:content/importer`blijft dus behouden en worden alleen de paginacomponent van de importer en de bronnen in `etc/design` het bestand verwijderd. Als u op **Ja** klikt, `jcr:content/importer` wordt ook de knop verwijderd.

>[!NOTE]
>
>Als u besluit om de inhoudswijzigingen te verwijderen, gaan alle wijzigingen die u hebt aangebracht op de geïmporteerde bestemmingspagina en alle pagina-eigenschappen verloren wanneer u op **Wissen** klikt.

### Componenten wijzigen en toevoegen op een bestemmingspagina {#modifying-and-adding-components-on-a-landing-page}

Als u componenten op de openingspagina wilt wijzigen, dubbelklikt u erop om ze te openen en te bewerken zoals u dat met andere componenten doet.

Als u componenten aan de bestemmingspagina wilt toevoegen, sleept u componenten naar de bestemmingspagina (van het hulpapparaat in de klassieke gebruikersinterface of vanuit het deelvenster Componenten in de gebruikersinterface met geoptimaliseerde aanrakingen) en bewerkt u de onderdelen naar wens.

>[!NOTE]
>
>Als een component op de openingspagina niet kan worden bewerkt, moet u het ZIP-bestand opnieuw importeren nadat u het HTML-bestand hebt [gewijzigd.](/help/sites-administering/extending-the-design-importer-for-landingpages.md) Dit betekent dat de niet-bewerkbare onderdelen tijdens het importeren niet zijn omgezet in AEM-componenten.

### Een openingspagina verwijderen {#deleting-a-landing-page}

Het verwijderen van een landingspagina is vergelijkbaar met het verwijderen van een normale AEM-pagina.

De enige uitzondering is dat wanneer u een bestemmingspagina verwijdert, deze ook de bijbehorende bestemmingspagina voor mobiele apparaten verwijdert (indien aanwezig), maar niet andersom.

### Een openingspagina publiceren {#publishing-a-landing-page}

U kunt de openingspagina en alle bijbehorende afhankelijkheden publiceren op dezelfde manier als een normale pagina publiceren.

>[!NOTE]
>
>Wanneer u de bestemmingspagina publiceert, wordt ook de bijbehorende mobiele versie (indien van toepassing) gepubliceerd. Bij het publiceren van een bestemmingspagina voor mobiele apparaten wordt de bureaubladversie echter niet gepubliceerd.
