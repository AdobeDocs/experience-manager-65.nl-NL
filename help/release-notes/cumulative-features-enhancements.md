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

Zie ook [ Adobe Experience Manager 6.5 de Latest Nota&#39;s van de Versie van het Pak van de Dienst ](/help/release-notes/release-notes.md).

## AEM 6.5, Service Pack 18-December 7, 2023

* Gebruikers van de Pagina-editor/afbeeldingscomponent van sites konden naar elementen van de externe Assets-Cloud Service verwijzen. (SITES-13448, SITES-13433)
* AEM ondersteunt nu sorteren op de server voor snellere projectnavigatie in de lijstweergave. Projectknooppunten worden gesorteerd op basis van de door de gebruiker geselecteerde kolom voordat ze in de interface worden weergegeven.

### [!DNL Forms]

* **Nieuwe Aangepaste Componenten van de Kern van de Vorm**: De verticale lusjes, de Voorwaarden &amp;, en Checkbox worden toegevoegd om scalability van vormen te verbeteren.
   * **[CheckBox component ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html)**: De adaptieve Forms die op de Componenten van de Kern wordt gebaseerd kan nu een checkbox component omvatten. Hiermee kunnen gebruikers binaire keuzes maken door een bepaalde optie te selecteren of te deselecteren. De optie wordt meestal weergegeven als een klein vak waarop u kunt klikken of tikken om te schakelen tussen twee statussen: ingeschakeld en uitgeschakeld. Het selectievakje is een veelgebruikt formulierelement voor een ja/nee- of waar/onwaar-keuze.

   * **[de component van de Bepalingen en van de Voorwaarden ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html)**: De adaptieve Forms die op de Componenten van de Kern wordt gebaseerd kan nu een component van de Voorwaarden en van de Voorwaarden omvatten. Hiermee kunnen Forms-auteurs een specifieke sectie in het formulier introduceren waarin gebruikers de voorwaarden, juridische overeenkomsten of het gebruik van een service, product of platform krijgen aangeboden. Deze component is bedoeld om gebruikers te informeren over de regels, regels en verplichtingen waarmee zij instemmen door het formulier in te dienen.

     ![ Verticale lusjes, Voorwaarden en componenten Checkbox ](/help/forms/using/assets/forms-components.png)

   * **[Verticale de component van lusjes ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html)**: De adaptieve Forms die op de Componenten van de Kern wordt gebaseerd kan vorminhoud in een verticale lijst van lusjes nu organiseren, die een gestructureerde en navigeerbare lay-out verstrekken. Het gebruik van verticale tabbladen in een formulier kan de algehele gebruikerservaring verbeteren door de navigatie te vereenvoudigen en de organisatie van formulierinhoud te verbeteren, met name in situaties waarin een formulier meerdere secties of complexe informatie bevat.

* **[met 64 bits versie van AEM Forms Designer](/help/forms/using/installing-configuring-designer.md)**: De met 64 bits versie van AEM Forms Designer brengt verbeterde prestaties, scalability, en geheugenbeheer om uw ervaring van de vormverwezenlijking te versterken. Met de 64-bits architectuur kunt u nog grotere en complexere projecten eenvoudig aanpakken, zodat u kunt zorgen voor naadloze ontwerpworkflows en geoptimaliseerde efficiëntie. Verhoog uw mogelijkheden voor formulierontwerp en omarm de toekomst van AEM Forms Designer met deze baanbrekende release.

* **[verbind een Aangepaste Forms met de Lijst van SharePoint Microsoft®](/help/forms/using/configuring-submit-actions.md#submit-to-microsoft&reg;-sharepoint-list)**: AEM Forms verstrekt een out-of-the-box integratie om vormgegevens rechtstreeks naar de Lijst van SharePoint voor te leggen, latend u de mogelijkheden van de Lijsten van SharePoint gebruiken. U kunt de Microsoft® SharePoint-lijst configureren als gegevensbron voor een formuliergegevensmodel en de verzendactie Verzenden met het formuliergegevensmodel gebruiken om een adaptief formulier te verbinden met de SharePoint-lijst.

* **[Steun om Document van de eigenschappen van het Verslag voor de Aangepaste Fragmenten van de Vorm te vormen](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)**: U kunt uw Aangepaste fragmenten van de Vorm en zijn gebieden in de Aangepaste redacteur van de Vorm nu gemakkelijk aanpassen.

* **met 64 bits XMLFM**: De iteratie met 64 bits van XMLFM introduceert verhoogde prestaties, scalability, en verfijnd geheugenbeheer. Het is de eerste inheemse dienst met 64 bits die op server-kant wordt opgesteld. Met XMLFM 64-bits kan een naadloze afhandeling van grotere renderingwerklasten worden bewerkstelligd door gebruik te maken van de inherente mogelijkheid om toegang te krijgen tot grotere geheugenbronnen in vergelijking met de 32-bits tegenhanger. Deze mijlpaal betekent niet alleen een prestatiesprong, maar introduceert ook belangrijke verbeteringen aan het native servicekader binnen de AEM Forms Server. Deze update zorgt ervoor dat AEM Forms Server naadloos elke 64-bits native service ondersteunt.

## AEM 6.5, Service Pack 18-augustus 24, 2023

* Assets, Dynamic Media - [ Veelvoudige titel en audiospoorsteun voor video&#39;s in Dynamic Media ](/help/assets/video.md#about-msma) - u kunt veelvoudige ondertitels en veelvoudige audiosporen aan een primaire video nu gemakkelijk toevoegen. Dit betekent dat uw video&#39;s toegankelijk zijn voor een breed publiek. U kunt één gepubliceerde primaire video aanpassen aan een wereldwijd publiek in meerdere talen en de richtlijnen voor toegankelijkheid voor verschillende geografische regio&#39;s naleven. Auteurs kunnen de ondertitels en audiotracks ook beheren vanaf één tabblad in de gebruikersinterface.
* Assets - In de zoekresultaten kunt u nu naar de maplocatie met een element navigeren, zodat u verschillende taken voor middelenbeheer kunt uitvoeren.
* De Plukker van Polaris van Plaatsen in de Fragmenten van de Inhoud heeft betere prestaties.
* Gebruikers van de Pagina-editor/afbeeldingscomponent van sites konden naar elementen van de externe Assets-Cloud Service verwijzen.
* Om snel een project in de mening van de Lijst te vinden, waar u vele projecten in uw systeem kunt hebben, steunt de Adobe nu server-zijhet sorteren. Projectknooppunten worden op de achtergrond gesorteerd op basis van de kolom die door de gebruiker is geselecteerd voordat ze in de gebruikersinterface worden weergegeven.
* AEM 6.5.18.0 ondersteunt MongoDB 5.0 tot 6.0.

### [!DNL Forms]

* **[Verbeterde fout behandeling met de managers van de douanefout in de regelredacteur ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/adaptive-forms-advanced-authoring/standard-validation-error-messages-adaptive-forms.html)** - u kunt een douanefunctie (gebruikend de Bibliotheek van de Cliënt) nu aanhalen als antwoord op een fout die door de externe dienst is teruggekeerd. En u kunt eindgebruikers een op maat gesneden reactie geven. Of u kunt specifieke acties uitvoeren voor fouten die door een service worden geretourneerd. Bijvoorbeeld, kunt u een douanewerkschema in de achtergrond voor specifieke foutencodes aanhalen of de klant meedelen dat de dienst neer is

* **[Verbeterde stap van het Werkschema van Adobe Sign ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/workflows/aem-forms-workflow-step-reference.html#sign-document-step)** - de werkschemastap van Adobe Sign in AEM Workflows is beschikbaar met de volgende verhogingen.

   * **Verbeterde Veiligheid met op identiteitskaart-Gebaseerde Authentificatie van de Regering voor Adobe Sign** - Adobe Acrobat Sign op identiteitskaart-Gebaseerde Authentificatie van de Regering biedt een extra laag van controle aan. Het stelt gebruikers in staat hun identiteit te verifiëren met behulp van door de overheid afgegeven id&#39;s (rijbewijs, nationale identiteitskaart, paspoort). Door vertrouwde identificatiedocumenten te gebruiken, voegt deze verbetering een extra niveau van vertrouwen aan het ondertekeningsproces toe, die het ideaal maakt voor scenario&#39;s die verhoogde veiligheid, naleving, en gebruikersbevestiging vereisen.

   * **Verbeterde Transparantie met het Spoor van de Controle voor de Documenten van Adobe Sign** - gebruik de eigenschap van het Spoor van de Controle voor gedetailleerde inzichten in de levenscyclus van uw documenten van Adobe Sign. Met het audittrail, kunt u een uitvoerig verslag van alle acties en interactie handhaven met betrekking tot uw documenten. Dit omvat gegevens zoals wie het document heeft bekeken, bewerkt of ondertekend, samen met tijdstempels voor elke gebeurtenis. Deze verbetering is van cruciaal belang voor het handhaven van de naleving, het oplossen van geschillen en het verzekeren van de integriteit van uw digitale overeenkomsten.


   * **breidde de rollen voor de ontvangers van de Overeenkomst voorbij enkel de Ondertekenaar** uit - Adobe Acrobat Sign laat u de rollen voor de ontvangers van de Overeenkomst voorbij enkel de Ondertekenaar uitbreiden om hun werkschemavereisten beter aan te passen. Wanneer toegelaten, heeft elke ontvanger in een Overeenkomst zijn rol individueel configureerbaar, met Ondertekenaar die het gebrek is.


* **[AEM Forms op volledig installatieprogramma JEE ](https://experienceleague.adobe.com/docs/experience-manager-65/forms/install-aem-forms/jee-installation/aem-forms-jee-supported-platforms.html)** - het de dienstpak brengt een volledig installatieprogramma voor AEM Forms op JEE die steun voor veelvoudige nieuwe softwarecombinaties, met inbegrip van brengt:
   * Microsoft® Windows Server 2022
   * Microsoft® Active Directory 2022
   * Oracle WebLogic 14C op Windows Server 2022
   * Red Hat® JBoss® 7.4.10
   * MongoDB 6.0 <!-- it was previously MongoDB 4.4 -->
   * MySQL JDBC-connector 8

Als u de nieuwste software voor uw AEM 6.5 Forms in JEE-omgeving installeert of wilt gebruiken, raadt Adobe u aan AEM 6.5.18.0 Forms in te voeren in het volledige installatieprogramma van JEE. Raadpleeg de documentatie voor AEM Forms op JEE of AEM Forms op OSGi voor meer informatie over de volledige lijst met nieuw toegevoegde en vervangen software.

## AEM 6.5, Service Pack 17-mei 25, 2023

* **de ervaringsverhogingen van het Onderzoek** - u kunt de volgende verrichtingen op de activa nu snel uitvoeren die in de onderzoeksresultaten tonen:
   * Een workflow maken
   * Een versie maken
   * Relatieve of niet-gerelateerde elementen

  U hoeft niet naar de middelenlocatie te navigeren en de eigenschappen ervan te bekijken om deze bewerkingen uit te voeren.
* _de Momentopname van Dynamic Media _**- Experimenteer met testbeelden of Dynamic Media URLs, om de output van verschillende beeldbepalingen, en Slimme optimalisaties van het Beeld voor dossiergrootte (met levering WebP en AVIF), netwerkbandbreedte, en de Verhouding van het Pixel van het Apparaat te zien.**Zie [ Momentopname van Dynamic Media ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/dynamic-media/images/dynamic-media-snapshot.html).
* **DASH die met Dynamic Media** stroomt - Nieuw protocol (DASH - Dynamische Aanpassings het Streamen over HTTP) steun voor Aangepast het stromen in Dynamic Media videeverstrekking (met toegelaten CMAF) wordt gelanceerd die. Beschikbaar nu voor alle gebieden, [ die als steunkaartje ](/help/assets/video.md#enable-dash-on-your-account-enable-dash) wordt toegelaten.
* **Integratie van Experience Manager Sites en de Fragmenten van de Inhoud met Assets volgende-Generatie Dynamic Media** - De gebruikers van Experience Manager Assets as a Cloud Service volgende-Generatie Dynamic Media kunnen die wolk-ontvangen activa voor creatie en levering met op-gebouw of Managed Services instanties van Experience Manager Sites 6.5 nu gebruiken.

### [!DNL Forms]

* **[Aangepaste Forms binnen AEM Redacteur van de Pagina](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md)**: U kunt nu AEM Redacteur van de Pagina gebruiken om veelvoudige vormen aan uw plaatspagina&#39;s snel tot stand te brengen en toe te voegen. Met deze functie kunnen auteurs van inhoud naadloze ervaringen met gegevensvastlegging op sitepagina&#39;s maken met behulp van de kracht van adaptieve formuliercomponenten, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van registratie- en bedrijfsprocesautomatisering. U kunt:
   * Maak een adaptief formulier door formuliercomponenten te slepen en neer te zetten op Adaptive Forms Container Component in AEM Sites Editor of Experience Fragments.
   * Met de wizard Adaptive Forms in de AEM Sites-editor kunt u onafhankelijk van elke sitepagina formulieren maken die u de vrijheid geven dergelijke formulieren op meerdere pagina&#39;s opnieuw te gebruiken.
   * Voeg meerdere formulieren toe aan een sitepagina, zodat de gebruikerservaring wordt gestroomlijnd en er meer flexibiliteit wordt geboden.
* **[Steun van reCAPTCHA Onderneming in Experience Manager Forms](/help/forms/using/captcha-adaptive-forms.md)**: Toegevoegde steun voor reCAPTCHA Onderneming in Experience Manager Forms, die verbeterde bescherming tegen frauduleuze activiteit en spam, naast bestaande Google reCAPTCHA v2 steun verleent.
* **[Steun voor Adobe Acrobat Sign voor Regering met Experience Manager Forms](/help/forms/using/adobe-sign-integration-adaptive-forms.md)**: AEM Forms integreert nu met Adobe Acrobat Sign voor Regering (volgzame FedRAMP). Deze integratie biedt een geavanceerd niveau van naleving en beveiliging voor e-handtekeningen met Adaptief formulier-inzendingen voor met de overheid verband houdende rekeningen (overheidsdiensten en agentschappen). Dankzij de integratie met Adobe Acrobat Sign for Government kunnen partners en klanten van de Adobe in Adaptive Forms elektronische handtekeningen gebruiken voor een aantal van de meest bedrijfskritieke en gevoelige bedrijfsonderdelen. Deze extra laag van veiligheid zorgt ervoor dat alle e-handtekeningen volledig volgzaam met de Matige naleving FedRAMP zijn, die de klanten van de overheid van de Adobe van mening voorziet.
* **laat integratie Salesforce met Experience Manager Forms voor gegevensuitwisseling** toe: Vorm de integratie tussen Experience Manager Forms en de toepassing Salesforce gebruikend de OAuth 2.0 cliëntgeloofsstroom. Deze mogelijkheid maakt een veilige en directe verificatie en verificatie van de toepassing mogelijk en maakt naadloze communicatie zonder betrokkenheid van de gebruiker mogelijk.
* **Optimalisering en verbeterde functionaliteit van werkschemamotor**: Verhoog de prestaties van de werkschemamotoren door het aantal werkschemainstanties te minimaliseren. Naast `COMPLETED` - en `RUNNING` -statuswaarden ondersteunt de workflow ook drie nieuwe statuswaarden: `ABORTED` , `SUSPENDED` en `FAILED` .

## AEM 6.5, Service Pack 16-februari 23, 2023

Het nieuwe protocol DASH (het Dynamische Aanpassings Streamen over HTTP) steunt gelanceerd voor het adaptieve bitrate stromen in de videoverlevering van Dynamic Media (met CMAF [ toegelaten het Gemeenschappelijke Formaat van de Toepassing van Media ]).

* Adaptief streamen (DASH/HLS) zorgt voor een betere weergave voor eindgebruikers voor video&#39;s.
* DASH is het internationale standaardprotocol voor adaptieve videostreaming en wordt op grote schaal toegepast in de branche.
* Beschikbaar in Azië-Stille Oceaan en Noord-Amerika (in te schakelen via een steunticket); binnenkort verkrijgbaar in Europa-Midden-Oost-Afrika.

Zie [ DASH op uw rekening ](/help/assets/video.md#enable-dash) toelaten.

### [!DNL Forms]

* [ Koploze Aanpassings Forms ](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/overview.html) laat uw ontwikkelaars toe om, interactieve vormen tot stand te brengen te publiceren en te beheren die met door APIs, eerder dan door een traditioneel grafisch gebruikersinterface kunnen worden betreden en worden in wisselwerking gestaan.

* [ de Adaptieve Componenten van de Kern van Forms ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html#features) zijn een reeks 24 open-bron, BEM-volgzame componenten die op de stichting van de Componenten van de Kern van Adobe Experience Manager WCM worden voortgebouwd. Deze componenten zijn open-source en bieden ontwikkelaars de mogelijkheid om deze componenten eenvoudig aan te passen en uit te breiden, zodat ze voldoen aan de specifieke behoeften van hun organisatie. Iedereen met bestaande vaardigheden om [ componenten van de Kern WCM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/get-started/authoring.html) aan te passen kan deze componenten gemakkelijk aanpassen en opmaken.

* De dienst van de Uitbreiding van de Reader op OSGi verstrekt nu afzonderlijke opties om de invoer en de uitvoergebruiksrechten op een PDF toe te laten om gegevens in Adobe Acrobat Reader in te voeren of uit te voeren.

## AEM 6.5, Service Pack 15-November 24, 2022

### [!DNL Forms]

* AEM Forms Designer is nu beschikbaar in [ Spaanse scène ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html).
* U kunt [ OAuth2 nu gebruiken om met Microsoft® Office voor authentiek te verklaren 365 de protocollen van de postserver (SMTP en IMAP) ](/help/forms/using/oauth2-support-for-mail-service.md).
* U kunt [ Revalidate op server ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-submit-actions-and-metadata-submission/configuring-submit-actions.html#enabling-server-side-validation-br) bezit aan waar plaatsen om de verborgen gebieden voor uitsluiting van een Document van Verslag op server-kant te identificeren.
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
