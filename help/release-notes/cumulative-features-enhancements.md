---
title: Cumulatieve belangrijkste functies en verbeteringen in de Adobe Experience Manager 6.5-release.
description: Een cumulatieve lijst van belangrijkste eigenschappen en verhogingen die in Adobe Experience Manager 6.5 van de vorige acht versies van het de dienstpak worden gemaakt.
content-type: reference
docset: aem65
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 01fe5b53-2244-445f-a4d0-bd58ea38b611
solution: Experience Manager
source-git-commit: a49af471c5fc2f799687173bff6cdcb21505740a
workflow-type: tm+mt
source-wordcount: '2335'
ht-degree: 0%

---

# Cumulatieve belangrijkste kenmerken en verbeteringen

Een cumulatieve lijst van zeer belangrijke eigenschappen en verhogingen in Adobe Experience Manager 6.5 voor de vorige acht versies van het de dienstpak.

Zie ook [Opmerkingen bij de release van Adobe Experience Manager 6.5 Nieuwste Service Pack](/help/release-notes/release-notes.md).

## AEM 6.5, Service Pack 18-December 7, 2023

* Gebruikers van de Pagina-editor/afbeeldingscomponent van Sites konden naar elementen van de Cloud Service voor externe middelen verwijzen. (SITES-13448, SITES-13433)
* AEM ondersteunt nu sorteren op de server voor snellere projectnavigatie in de lijstweergave. Projectknooppunten worden gesorteerd op basis van de door de gebruiker geselecteerde kolom voordat ze in de interface worden weergegeven.

### [!DNL Forms]

* **Nieuwe adaptieve Core-componenten van het formulier**: De verticale tabbladen, Algemene voorwaarden en Selectievakje worden toegevoegd om de schaalbaarheid van formulieren te verbeteren.
   * **[Component CheckBox](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html)**: Adaptieve Forms op basis van Core Components kan nu een component checkbox bevatten. Hiermee kunnen gebruikers binaire keuzes maken door een bepaalde optie te selecteren of te deselecteren. De optie wordt meestal weergegeven als een klein vak waarop u kunt klikken of tikken om te schakelen tussen twee statussen: ingeschakeld en uitgeschakeld. Het selectievakje is een veelgebruikt formulierelement voor een ja/nee- of waar/onwaar-keuze.

   * **[Component Voorwaarden en bepalingen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html)**: Adaptieve Forms op basis van kerncomponenten kan nu een component Voorwaarden en Voorwaarden bevatten. Hiermee kunnen Forms-auteurs een specifieke sectie in het formulier introduceren waarin gebruikers de voorwaarden, juridische overeenkomsten of het gebruik van een service, product of platform krijgen aangeboden. Deze component is bedoeld om gebruikers te informeren over de regels, regels en verplichtingen waarmee zij instemmen door het formulier in te dienen.

     ![Verticale tabbladen, Algemene voorwaarden en componenten Selectievakje](/help/forms/using/assets/forms-components.png)

   * **[De component Verticale tabbladen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html)**: Adaptieve Forms op basis van Core Components kan nu formulierinhoud ordenen in een verticale lijst met tabbladen, zodat u over een gestructureerde en navigeerbare indeling beschikt. Het gebruik van verticale tabbladen in een formulier kan de algehele gebruikerservaring verbeteren door de navigatie te vereenvoudigen en de organisatie van formulierinhoud te verbeteren, met name in situaties waarin een formulier meerdere secties of complexe informatie bevat.

* **[64-bits versie van AEM Forms Designer](/help/forms/using/installing-configuring-designer.md)**: De 64-bits versie van AEM Forms Designer biedt verbeterde prestaties, schaalbaarheid en geheugenbeheer, zodat u meer mogelijkheden hebt om formulieren te maken. Met de 64-bits architectuur kunt u nog grotere en complexere projecten eenvoudig aanpakken, zodat u kunt zorgen voor naadloze ontwerpworkflows en geoptimaliseerde efficiëntie. Verhoog uw mogelijkheden voor formulierontwerp en omarm de toekomst van AEM Forms Designer met deze geavanceerde release.

* **[Een adaptieve Forms verbinden met de Microsoft® SharePoint List](/help/forms/using/configuring-submit-actions.md#submit-to-microsoft&reg;-sharepoint-list)**: AEM Forms biedt een out-of-the-box integratie om formuliergegevens rechtstreeks naar de SharePoint List te verzenden, zodat u de mogelijkheden van SharePoint List kunt gebruiken. U kunt de Microsoft® SharePoint-lijst configureren als gegevensbron voor een formuliergegevensmodel en de verzendactie Verzenden met het formuliergegevensmodel gebruiken om een adaptief formulier te verbinden met de SharePoint-lijst.

* **[Ondersteuning voor het configureren van Document of Record-eigenschappen voor adaptieve formulierfragmenten](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)**: U kunt de fragmenten van het adaptieve formulier en de bijbehorende velden nu gemakkelijk aanpassen in de Adaptieve formuliereditor.

* **64-bits XMLFM**: De 64-bits iteratie van XMLFM introduceert verhoogde prestaties, schaalbaarheid en verfijnd geheugenbeheer. Het is de eerste inheemse dienst met 64 bits die op server-kant wordt opgesteld. Met XMLFM 64-bits kan een naadloze afhandeling van grotere renderingwerklasten worden bewerkstelligd door gebruik te maken van de inherente mogelijkheid om toegang te krijgen tot grotere geheugenbronnen in vergelijking met de 32-bits tegenhanger. Deze mijlpaal betekent niet alleen een prestatiesprong, maar introduceert ook belangrijke verbeteringen aan het native servicekader binnen de AEM Forms Server. Deze update zorgt ervoor dat AEM Forms Server naadloos elke 64-bits native service ondersteunt.

## AEM 6.5, Service Pack 18-augustus 24, 2023

* Middelen, Dynamic Media - [Ondersteuning voor meerdere bijschriften en audiotracks voor video&#39;s in Dynamic Media](/help/assets/video.md#about-msma)—U kunt nu eenvoudig meerdere ondertitels en meerdere audiotracks toevoegen aan een primaire video. Dit betekent dat uw video&#39;s toegankelijk zijn voor een breed publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de ondertitels en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.
* Middelen - Vanuit de zoekresultaten kunt u nu naar de maplocatie navigeren die een element bevat waarmee u verschillende taken voor middelenbeheer kunt uitvoeren.
* De Plukker van Polaris van Plaatsen in de Fragmenten van de Inhoud heeft betere prestaties.
* Gebruikers van de Pagina-editor/afbeeldingscomponent van Sites konden naar elementen van de Cloud Service voor externe middelen verwijzen.
* Om snel een project in de mening van de Lijst te vinden, waar u vele projecten in uw systeem kunt hebben, steunt de Adobe nu server-zijhet sorteren. Projectknooppunten worden op de achtergrond gesorteerd op basis van de kolom die door de gebruiker is geselecteerd voordat ze in de gebruikersinterface worden weergegeven.
* AEM 6.5.18.0 ondersteunt MongoDB 5.0 tot 6.0.

### [!DNL Forms]

* **[Verbeterde fout behandeling met de managers van de douanefout in de regelredacteur](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms.html)** - U kunt nu een aangepaste functie aanroepen (met behulp van de clientbibliotheek) als reactie op een fout die door een externe service is geretourneerd. En u kunt eindgebruikers een op maat gesneden reactie geven. Of u kunt specifieke acties uitvoeren voor fouten die door een service worden geretourneerd. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant meedelen dat de dienst neer is

* **[Verbeterde Adobe Sign Workflow-stap](https://experienceleague.adobe.com/docs/experience-manager-65/forms/workflows/aem-forms-workflow-step-reference.html#sign-document-step)** - Adobe Sign-workflowstap in AEM Workflows is beschikbaar met de volgende verbeteringen.

   * **Uitgebreide beveiliging met verificatie op basis van overheidsidentiteitskaart voor Adobe Sign** - Verificatie op basis van Adobe Acrobat Sign-gebruikersnaam biedt een extra verificatielaag. Het stelt gebruikers in staat hun identiteit te verifiëren met behulp van door de overheid afgegeven id&#39;s (rijbewijs, nationale identiteitskaart, paspoort). Door vertrouwde identificatiedocumenten te gebruiken, voegt deze verbetering een extra niveau van vertrouwen aan het ondertekeningsproces toe, die het ideaal maakt voor scenario&#39;s die verhoogde veiligheid, naleving, en gebruikersbevestiging vereisen.

   * **Verbeterde transparantie met audittrail voor Adobe Sign-documenten** - Gebruik de functie Audittrail voor meer informatie over de levenscyclus van uw Adobe Sign-documenten. Met het audittrail, kunt u een uitvoerig verslag van alle acties en interactie handhaven met betrekking tot uw documenten. Dit omvat gegevens zoals wie het document heeft bekeken, bewerkt of ondertekend, samen met tijdstempels voor elke gebeurtenis. Deze verbetering is van cruciaal belang voor het handhaven van de naleving, het oplossen van geschillen en het verzekeren van de integriteit van uw digitale overeenkomsten.


   * **De rollen voor overeenkomstontvangers uitbreiden tot buiten alleen de ondertekenaar** - Met Adobe Acrobat Sign kunt u de rollen voor overeenkomstontvangers uitbreiden naar een andere plaats dan alleen de ondertekenaar, zodat ze beter aansluiten op hun workflowvereisten. Wanneer toegelaten, heeft elke ontvanger in een Overeenkomst zijn rol individueel configureerbaar, met Ondertekenaar die het gebrek is.


* **[AEM Forms op JEE volledig installatieprogramma](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/jee-installation/aem-forms-jee-supported-platforms.html)** - Het servicepakket biedt een volledig installatieprogramma voor AEM Forms op JEE dat ondersteuning biedt voor meerdere nieuwe softwarecombinaties, waaronder:
   * Microsoft® Windows Server 2022
   * Microsoft® Active Directory 2022
   * Oracle WebLogic 14C op Windows Server 2022
   * Red Hat® JBoss® 7.4.10
   * MongoDB 6.0 <!-- it was previously MongoDB 4.4 -->
   * MySQL JDBC-connector 8

Als u de nieuwste software voor uw AEM 6.5 Forms in JEE-omgeving installeert of wilt gebruiken, raadt Adobe u aan AEM 6.5.18.0 Forms in te voeren in het volledige installatieprogramma van JEE. Raadpleeg de documentatie voor AEM Forms op JEE of AEM Forms op OSGi voor meer informatie over de volledige lijst met nieuw toegevoegde en vervangen software.

## AEM 6.5, Service Pack 17-mei 25, 2023

* **Verbeterde zoekervaring** - U kunt nu snel de volgende bewerkingen uitvoeren op de elementen die in de zoekresultaten worden weergegeven:
   * Een workflow maken
   * Een versie maken
   * Relatieve of niet-gerelateerde elementen

  U hoeft niet naar de middelenlocatie te navigeren en de eigenschappen ervan te bekijken om deze bewerkingen uit te voeren.
* **Dynamic Media _Opname_**- Experimenteer met testafbeeldingen of Dynamic Media-URL&#39;s om de uitvoer van verschillende afbeeldingsmodifiers en Smart Imaging-optimalisaties voor de bestandsgrootte (met WebP- en AVIF-levering), de netwerkbandbreedte en de pixelverhouding van het apparaat te bekijken. Zie [Dynamic Media-momentopname](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html).
* **DASH-streaming met Dynamic Media** - Ondersteuning voor het nieuwe protocol (DASH - Dynamic Adaptive Streaming via HTTP) dat wordt gestart voor Adaptive streaming in Dynamic Media-video (met CMAF ingeschakeld). Nu beschikbaar voor alle regio&#39;s, [ingeschakeld via een ondersteuningsticket](/help/assets/video.md#enable-dash-on-your-account-enable-dash).
* **Integratie van Experience Manager Sites en Content Fragments met Assets Next-Generation Dynamic Media** - Gebruikers van Experience Manager Assets as a Cloud Service Next-Generation Dynamic Media kunnen deze door de cloud gehoste middelen nu gebruiken voor het ontwerpen en leveren van on-premise of Managed Services-exemplaren van Experience Manager Sites 6.5.

### [!DNL Forms]

* **[Adaptieve Forms in AEM paginaeditor](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md)**: U kunt nu AEM Pagina-editor gebruiken om snel meerdere formulieren te maken en aan uw sitepagina&#39;s toe te voegen. Met deze functie kunnen auteurs van inhoud naadloze ervaringen met gegevensvastlegging op sitepagina&#39;s maken met behulp van de kracht van adaptieve formuliercomponenten, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van registratie- en bedrijfsprocesautomatisering. U kunt:
   * Maak een adaptief formulier door formuliercomponenten te slepen en neer te zetten op Adaptive Forms Container Component in AEM Sites Editor of Experience Fragments.
   * Met de wizard Adaptive Forms in de AEM Sites-editor kunt u onafhankelijk van elke sitepagina formulieren maken die u de vrijheid geven dergelijke formulieren op meerdere pagina&#39;s opnieuw te gebruiken.
   * Voeg meerdere formulieren toe aan een sitepagina, zodat de gebruikerservaring wordt gestroomlijnd en er meer flexibiliteit wordt geboden.
* **[Ondersteuning voor reCAPTCHA Enterprise in Experience Manager Forms](/help/forms/using/captcha-adaptive-forms.md)**: Toegevoegde ondersteuning voor reCAPTCHA Enterprise in Experience Manager Forms, die naast de bestaande Google reCAPTCHA v2-ondersteuning een betere bescherming biedt tegen frauduleuze activiteiten en spam.
* **[Steun aan Adobe Acrobat Sign voor de regering met Experience Manager Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md)**: AEM Forms is nu geïntegreerd met Adobe Acrobat Sign for Government (FedRAMP-compatibel). Deze integratie biedt een geavanceerd niveau van naleving en beveiliging voor e-handtekeningen met Adaptief formulier-inzendingen voor met de overheid verband houdende rekeningen (overheidsdiensten en agentschappen). Dankzij de integratie met Adobe Acrobat Sign for Government kunnen partners en klanten van de Adobe in Adaptive Forms elektronische handtekeningen gebruiken voor een aantal van de meest bedrijfskritieke en gevoelige bedrijfsonderdelen. Deze extra laag van veiligheid zorgt ervoor dat alle e-handtekeningen volledig volgzaam met de Matige naleving FedRAMP zijn, die de klanten van de overheid van de Adobe van mening voorziet.
* **Integratie van Salesforce met Experience Manager Forms inschakelen voor gegevensuitwisseling**: Configureer de integratie tussen Experience Manager Forms en de Salesforce-toepassing met behulp van de OAuth 2.0-clientaanmeldingsgegevens. Deze mogelijkheid maakt een veilige en directe verificatie en verificatie van de toepassing mogelijk en maakt naadloze communicatie zonder betrokkenheid van de gebruiker mogelijk.
* **Optimalisatie en verbeterde functionaliteit van de workflow-engine**: Verhoog de prestaties van de workflowengines door het aantal workflowinstanties te minimaliseren. Naast `COMPLETED` en `RUNNING` statuswaarden, de workflow ondersteunt ook drie nieuwe statuswaarden: `ABORTED`, `SUSPENDED`, en `FAILED`.

## AEM 6.5, Service Pack 16-februari 23, 2023

Het nieuwe protocol DASH (Dynamic Adaptive Streaming via HTTP) ondersteunt de introductie van adaptieve streaming van bitsnelheden in Dynamic Media-video (met CMAF) [Common Media Application Format] ingeschakeld).

* Adaptief streamen (DASH/HLS) zorgt voor een betere weergave voor eindgebruikers voor video&#39;s.
* DASH is het internationale standaardprotocol voor adaptieve videostreaming en wordt op grote schaal toegepast in de branche.
* Beschikbaar in Azië-Stille Oceaan en Noord-Amerika (in te schakelen via een steunticket); binnenkort verkrijgbaar in Europa-Midden-Oost-Afrika.

Zie [DASH inschakelen voor uw account](/help/assets/video.md#enable-dash).

### [!DNL Forms]

* [Forms zonder hoofdadapter](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) stelt u uw ontwikkelaars in staat om interactieve formulieren te maken, te publiceren en te beheren die via API&#39;s kunnen worden benaderd en waarmee interactie mogelijk is, in plaats van via een traditionele grafische gebruikersinterface.

* [Adaptieve Forms Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html#features) zijn 24 open-source, BEM-compatibele componenten die op de basis van de Adobe Experience Manager WCM Core Components zijn gebouwd. Deze componenten zijn open-source en bieden ontwikkelaars de mogelijkheid om deze componenten eenvoudig aan te passen en uit te breiden, zodat ze voldoen aan de specifieke behoeften van hun organisatie. Iedereen met bestaande vaardigheden om zich aan te passen [WCM Core-componenten](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/authoring.html) U kunt deze componenten eenvoudig aanpassen en opmaken.

* De dienst van de Uitbreiding van de Reader op OSGi verstrekt nu afzonderlijke opties om de invoer en de uitvoergebruiksrechten op een PDF toe te laten om gegevens in Adobe Acrobat Reader in te voeren of uit te voeren.

## AEM 6.5, Service Pack 15-November 24, 2022

### [!DNL Forms]

* AEM Forms Designer is nu beschikbaar in [Landinstelling Spaans](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).
* U kunt nu [OAuth2 voor verificatie met Microsoft® Office 365-mailserverprotocollen (SMTP en IMAP)](/help/forms/using/oauth2-support-for-mail-service.md).
* U kunt instellen [Revalidate op server](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html#enabling-server-side-validation-br) eigenschap in op true om de verborgen velden te identificeren voor uitsluiting van een document of record op de server.
* AEM Forms Designer vereist een 32-bits versie van Visual C++ 2019 Redistributable (x86).

## AEM 6.5, Service Pack 14-augustus 25, 2022

Alleen opgeloste problemen.

## AEM 6.5, Service Pack 13-mei 26, 2022

* Gebruik onzichtbare CAPTCHA in een adaptieve vorm: u kunt nu een onzichtbare CAPTCHA gebruiken om de CAPTCHA-uitdaging alleen te tonen als er verdachte activiteit is. Als geen verdachte activiteit wordt gevonden, wordt de uitdaging CAPTCHA niet getoond. Het helpt menselijke vormvoltooiing zonder controledoosvereisten beoordelen, aanpassingsinspanningen verminderen, en de eindgebruikerservaring verbeteren.

* Extra ondersteuning voor het ophalen van antwoordheaders in de nabewerker van het formuliergegevensmodel voor REST-eindpunten.

* Bij het genereren van een adaptief formuliervertaalbestand is nu dezelfde reeks teksten als het gegenereerde XLIFF-bestand identiek aan de reeks componenten in het corresponderende adaptieve formulier.

* Wanneer u een adaptief formulier lokaliseert en zelfs een kleine wijziging aanbrengt in de tekst van de basistaal, ontbreekt de volledige vertaling voor alle andere talen. Het probleem is opgelost in [!DNL Experience Manager] 6.5.13.0.

* Verbeterde toegankelijkheid voor Forms:

   * Extra ondersteuning voor schermlezers om de koptekst en hoofdtekst van een tabel te herkennen als continue en verbonden entiteiten. Schermlezers kunnen hierdoor gemakkelijker door de tabellen navigeren. (NPR-37139)
   * Extra ondersteuning voor schermlezers om te stoppen met navigeren door de HTML-werkruimte totdat een dialoogvenster is geopend.

## AEM 6.5, Service Pack 12-februari 24, 2022

* Nadat u een verbinding tussen externe DAM- en Sites-implementaties hebt geconfigureerd, worden de middelen op externe DAM beschikbaar gesteld op de implementatie van Sites. U kunt de update uitvoeren, verwijderen, hernoemen en bewerkingen verplaatsen op de externe DAM-middelen of -mappen. De updates zijn, met wat vertraging, automatisch beschikbaar op de plaatsing van Plaatsen.
* Push-rollouts van een live-kopiebron naar meerdere live kopieën is nu standaard mogelijk, zonder dat een blauwdrukconfiguratie nodig is.
* De status van asynchrone bewerkingen in uitvoering wordt nu weergegeven in de gebruikersinterface om te voorkomen dat gebruikers per ongeluk meerdere asynchrone bewerkingen op hetzelfde pad activeren.
* Ondersteuning voor op IMS gebaseerde verificatie wordt geboden voor API&#39;s van Analytics 2.0.
* API-ondersteuning voor JSON biedt een fragment voor typeervaring.
* Aanbiedingsaanvraag is nu beschikbaar voor de functie Verwijderen (Experience Fragment API) in IMS.
* De ingebouwde opslagplaats (Apache Jackrabbit Oak) staat nog steeds op 1.22.9.
