---
title: We.Gov en We.Finance
seo-title: We.Gov en We.Finance
description: Gebruik fictieve gebruikers en groepen om AEM Forms-taken uit te voeren met het Demopakket We.Gov en We.Finance.
seo-description: Gebruik fictieve gebruikers en groepen om AEM Forms-taken uit te voeren met het Demopakket We.Gov en We.Finance.
uuid: 797e301a-36ed-4bae-9ea8-ee77285c786d
contentOwner: anujkapo
discoiquuid: ddb3778b-be06-4cde-bc6e-0994efa42b18
docset: aem65
translation-type: tm+mt
source-git-commit: c6b8e184042394d99ceb099c918b81e2cce49497
workflow-type: tm+mt
source-wordcount: '2548'
ht-degree: 0%

---


# We.Gov en We.Finance doorzoeken de referentiesite {#we-gov-reference-site-walkthrough}

## Voorwaarden {#pre-requisites}

Stel de referentiesite in zoals beschreven in [De referentiesite Web.Gov en Web.Finance instellen en configureren](../../forms/using/forms-install-configure-gov-reference-site.md).

## Gebruikersartikel {#user-story}

* AEM Forms

   * automatede form conversion
   * Authoring
   * Formuliergegevensmodellen/gegevensbronnen

* AEM Forms

   * Gegevens vastleggen
   * (Optioneel) Gegevensintegratie (MS Dynamics)
   * (Optioneel) Adobe Sign

* Workflow
* E-mailmeldingen
* (Optioneel) Communicatie door klanten

   * Afdrukkanaal
   * Webkanaal

* Adobe Analytics
* Integratie van gegevensbron

### Fictieve gebruikers en groepen {#fictitious-users-and-groups}

Het Wij.Gov-demopakket wordt geleverd met de volgende ingebouwde fictieve gebruikers:

* **Aya Tan**: Burgers die in aanmerking komen voor een dienst van een overheidsinstantie

![Fictieve gebruiker](/help/forms/using/assets/aya_tan_new.png)

* **George Lang**: We.Overheid Business Analyst

![Fictieve gebruiker](/help/forms/using/assets/george_lang.png)

* **Camila Santos**: We.Gov Agency CX Lead

![Fictieve gebruiker](/help/forms/using/assets/camila_santos.png)

De volgende groepen zijn eveneens opgenomen:

* **We.Gov Forms-gebruikers**

   * George Lang (lid)
   * Camila Santos (lid)

* **Wij.Gov-gebruikers**

   * George Lang (lid)
   * Camila Santos (lid)
   * Aya Tan (lid)

### Demo-overzicht legenda {#demo-overview-terms-legend}

1. **Imiteren**: Gedefinieerde gebruikers en groepen in AEM demo.
1. **Knop**: Gekleurde rechthoek of omcirkelde pijl voor navigatie.
1. **Klik**: Een handeling uitvoeren in het gebruikersartikel.
1. **Koppelingen**: Deze bevindt zich boven aan het hoofdmenu op de site Web.Gov.
1. **Gebruikersinstructies**: Een reeks numerieke stappen om door het verhaal van de gebruiker te navigeren.
1. **Forms Portal**:  *https://&lt;aemserver>:&lt;port>/content/we-gov/formsportal.html*
1. **Mobiele weergave**:Gebruikers van de webserver kunnen een mobiele weergave repliceren met een browser van een andere grootte.
1. **Bureaubladweergave**: We gov-gebruikers bekijken de demo op een laptop of desktop.
1. **Pre-screener-formulier**: Formulier op de startpagina van de website Web.Gov.
1. **Adaptief formulier**: Inschrijvingsaanvraagformulier voor We.gov-demo.

   *https://&lt;aemserver>:&lt;port>/content/forms/af/adobe-gov-forms/enrollment-application-for-health-benefits.html*

1. **Site** Adobe wij.Gov:  *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. **Adobe in vak**: Located top menu bar  [Bell ](assets/bell.svg) iconin AEM background.

   *https://&lt;aemserver>:&lt;port>/aem/start.html*

1. **E-mailclient**: Voorkeur voor het weergeven van e-mails (Gmail, Outlook)
1. **CTA**: Oproep tot actie
1. **Navigeren**: Een specifiek referentiepunt op de browserpagina zoeken.
1. **AFC**: automatede form conversion

## automatede form conversion (Camila) {#automated-forms-conversion}

**Deze sectie**: Camila de CX Lead heeft een bestaand PDF-formulier dat is gebruikt als onderdeel van een papierproces. Als onderdeel van een moderniseringsinspanning wil ze dit PDF-formulier gebruiken om automatisch een nieuwe, moderne Adaptieve Forms te maken.

### automatede form conversion - Wij.Gov (Camila) {#automated-forms-conversion-wegov}

1. Navigeer naar *https://&lt;aemserver>:&lt;port>/aem/start.html*

1. Aanmelden met:
   * **Gebruiker**: camila.santos
   * **Wachtwoord**: password
1. Selecteer op de hoofdpagina Forms > Forms &amp; Documents > AEM Forms Web.gov Forms > AFC.
1. Camila uploadt de PDF naar AEM Forms.

   ![Formulier uploaden](assets/aftia-upload-form.jpg)

1. Camilla selecteert vervolgens het PDF-formulier en klikt op **Geautomatiseerde conversie starten** om het conversieproces te starten. U moet mogelijk **Conversie overschrijven** klikken als u het formulier hebt geconverteerd.

   >[!NOTE]
   >
   >De instellingen in AFC zijn vooraf geconfigureerd voor de eindgebruiker, wat betekent dat deze instellingen niet mogen worden gewijzigd.

   * **Optioneel**: Als u het Accessible Ultramarine-thema wilt gebruiken, klikt u gewoon op het pictogram Een adaptief formulierthema opgeven en selecteert u het Accessible-Ultramarine-thema dat wordt weergegeven in de lijst met opties.

   ![Conversie starten](assets/aftia-start-conversion.jpg)

   ![Ultramarijnthema](assets/aftia-upload-conversion-settings.jpg)

   Het percentage voltooide status wordt weergegeven tijdens de conversie. Als de status **Converted** heeft weergegeven, klikt u op de map **output**, selecteert u het aangepaste formulier en klikt u op **Edit** om het geconverteerde formulier te openen.

1. Camilla controleert vervolgens het formulier en controleert of alle velden aanwezig zijn

   ![Omzetting controleren](assets/aftia-review-conversion.jpg)

1. Camilla begint vervolgens met het bewerken van het formulier. Ze selecteert Hoofdvenster > Bewerken (de moersleutel) > Tabs bovenaan in het vervolgkeuzemenu Indeling deelvenster > Selecteert het selectievakje.

   ![Eigenschappen van revisie](assets/aftia-review-properties.jpg)

1. Camilla voegt vervolgens alle noodzakelijke CSS- en veldwijzigingen toe om het eindproduct te produceren.

   ![CSS toevoegen](assets/aftia-add-css.jpg)

### Formuliergegevensmodel en gegevensbronnen (Camila) {#data-sources}

**Deze sectie**: Nadat het document is geconverteerd en een adaptieve vorm heeft geproduceerd, moet Camila het adaptieve formulier vervolgens verbinden met een gegevensbron.

1. Camila opent de eigenschappen op de vorm die in [Automatede form conversion - wij.Gov](#automated-forms-conversion-wegov) werd omgezet.

1. In Camila selecteert u vervolgens Formuliermodel > Formuliergegevensmodel selecteren in het vervolgkeuzemenu Selecteert de FDM voor inschrijving via Web.gov in de lijst met opties.

1. Klik op de knop Opslaan en sluiten.

   ![FDM-selectie](assets/aftia-select-fdm.jpg)

1. Camila klikt op de map **output**, selecteert het aangepaste formulier en klikt op **Edit** om het voltooide Web.Gov-formulier te openen.
1. Camila selecteert een adaptief formulierveld en klikt op ![Pictogram configureren](assets/configure-icon.svg). Ze maakt binding met de formuliergegevensmodelentiteiten met het veld **Bind Reference**. Ze herhaalt deze stap voor alle velden in het adaptieve formulier.

### Toegankelijkheidstest van formulier (Camila) {#form-accessibility-testing}

Camila controleert ook of de gemaakte inhoud correct en volledig toegankelijk is volgens de bedrijfsnormen.

1. Camila klikt op de map **output**, selecteert het aangepaste formulier en klikt op **Preview** om het voltooide Web.Gov-formulier te openen.

1. Hiermee opent u het tabblad Audit in het Chrome Developer Tool.

1. Voert een toegankelijkheidscontrole uit om het adaptieve formulier te valideren.

   ![Toegankelijkheidscontrole](assets/aftia-accessibility.jpg)

## Aangepast formulier voor mobiele weergave demo (Aya) {#mobile-view-demo}

**Dit deel moet vóór de demonstratie worden uitgevoerd.**

**Gebruikersinstructies:**

1. Navigeren naar: *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. Aanmelden met:

   1. **Gebruiker**: aya.tan
   1. **Wachtwoord**: password

1. Wijzig de grootte van het browservenster of gebruik de emulator van de browser om een mobiele apparaatgrootte te repliceren.

### Web.Gov Website (Aya) {#aya-user-story-we-gov-website}

![Fictieve gebruiker](/help/forms/using/assets/aya_tan_new-1.png)

**Deze sectie**: Aya is een burger. Ze hoort van een vriend dat ze in aanmerking komt voor een service van een overheidsinstelling. Aya navigeert vanaf haar mobiele telefoon naar de website We.Gov voor meer informatie over services waarvoor ze in aanmerking komt.

### We.Gov Pre-Screener (Aya) {#aya-user-story-we-gov-pre-screener}

Aya beantwoordt een paar vragen om haar geschiktheid te bevestigen door een kort adaptief formulier in te vullen op haar mobiele telefoon.

**Gebruikersinstructies:**

1. Maak een selectie in elk vervolgkeuzeveld.

   >[!NOTE]
   >
   >Als de gebruiker meer dan $200.000/jaar verdient, komen ze niet in aanmerking.

1. Klik op &quot;**Komt ik in aanmerking?**” button.
1. Klik op de knop &quot;**Nu toepassen**&quot; om door te gaan.

   ![Koppeling Nu toepassen](/help/forms/using/assets/apply_now_link.png)

### We.Gov Adaptief formulier (Aya) {#aya-user-story-we-gov-adaptive-form}

Aya vindt dat ze in aanmerking komt en vult haar aanvraag in om service aan te vragen op haar mobiele apparaat.

Aya moet sommige documenten thuis herzien alvorens zij de toepassing van het de dienstverzoek kan voltooien. Ze slaat de toepassing op en sluit deze af van haar mobiele apparaat.

**Gebruikersinstructies:**

1. Vul de velden Basisinformatie in. U moet de volgende velden en downloads invullen:

   1. Basisinformatie

      1. Voornaam
      1. Achternaam
      1. DOB
      1. E-mail

1. Gebruik de volgende **dynamische logica** om dynamische eigenschap te demonstreren gebruikend **Familiestatus** dropdown:

   1. **Enkel**: Volgende paneel van skin tonen
   1. **Gehuwd**: Deelvenster echtelijk afhankelijk weergeven
   1. **Geforceerd**: Volgende paneel van skin tonen
   1. **Getabeld**: Volgende paneel van skin tonen
   1. **Heb je kinderen?**: (Ja/Nee), keuzerondje om het onderliggende afhankelijke deelvenster weer te geven.

      1. (Toevoegen/verwijderen) om meerdere onderliggende afhankelijke deelvensters toe te voegen of te verwijderen.

1. Klik op de pijl-rechts in de grijze menubalk.
1. Klik onderaan op de knop Opslaan.

   ![Details adaptieve vorm](/help/forms/using/assets/adaptive_form.png)

## Bureaubladdemo {#desktop-demo}

**Deze sectie:** Terug thuis, heeft Aya de informatie gevonden die zij nodig had en hervat de toepassing van haar Desktop. Navigeert altijd naar de online formulierportal om haar toepassing te hervatten. Met een eenvoudige aanpassing kunnen agentschappen ook automatisch een koppeling genereren en e-mailen om de toepassing te hervatten.

### Vervolg adaptief formulier (Aya) {#aya-user-story-continued-adaptive-form}

**Gebruikersinstructies:**

1. Navigeer naar *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. Klik in de navigatiebalk op &quot;**Online services**&quot;.
1. Selecteer in het deelvenster &quot;Concept Forms&quot; de bestaande &quot;Inschrijvingstoepassing voor gezondheidsvoordelen&quot;.

   ![Inschrijvingsaanvraag voor gezondheidsvoordelen](/help/forms/using/assets/enrollment_application.png)

   De look en feel zijn hetzelfde en ze hoeft geen gegevens opnieuw in te voeren.

   **Gebruikersinstructies:**

1. Klik op Cirkel CTA rechts om naar de volgende sectie te gaan.

   ![Rechthoekcirkel CTA](/help/forms/using/assets/right_circle_cta_new.png)

   Het formulier wordt gevuld tot het punt van de laatste vermelding van Aya. Aya heeft al haar gegevens ingevoerd en is bereid deze te verzenden.

   ![Het adaptieve formulier verzenden](/help/forms/using/assets/submit_adaptive_form.png)

   >[!NOTE]
   >
   >Wanneer Aya het veld Telefoonnummer invult, moet ze het invullen als een doorlopend getal van 11 cijfers zonder streepjes, spaties of afbreekstreepjes.

   Na het verzenden van Aya ontvangt je pagina Bedankt. Desgewenst ontvangt zij ook een e-mail die zij kan openen om het document van registratie elektronisch met Adobe Sign te ondertekenen.

### Optioneel: Adobe Sign (Aya) {#adobe-sign}

**Gebruikersinstructies:**

1. Navigeer naar uw e-mailclient en zoek de Adobe Sign-e-mail.
1. Klik op de koppeling naar Adobe Sign.

   ![Koppeling met Adobe ondertekenen](/help/forms/using/assets/adobe_sign_link.png)

**Gebruikersinstructies:**

1. Schakel het selectievakje &quot;**Ik ga akkoord**&quot; in.
1. Klik op &quot;**Accepteren**&quot;.
1. Blader naar de onderkant van het gereviseerde document.
1. Klik op de gemarkeerde gele tab om het document te ondertekenen.

   ![Onderteken het ](/help/forms/using/assets/sign_document_new.png) ![documentOnderteken het testdocument](/help/forms/using/assets/sign_test_document.png)

## Regeringsagent (George) {#government-agent-george}

![Government Agent George](/help/forms/using/assets/george_lang-1.png)

**Dit deel:** George is een zakenanalist bij het overheidsagentschap Aya vraagt om een dienst van. George heeft één dashboard waar hij alle toepassingen van het de dienstverzoek kan zien die aan hem voor overzicht zijn toegewezen.

### AEM Inbox (George) {#george-user-story-aem-inbox}

**Gebruikersinstructies:**

1. Navigeer naar *https://&lt;aemserver>:&lt;port>/aem/start.html*
1. Klik op het gebruikerspictogram (rechterbovenhoek) en gebruik &quot;**Sign Out**&quot;, of &quot;**Impersonate as**&quot;menuoptie als u momenteel met een administratieve gebruiker wordt het programma geopend.

   1. Aanmelden met:

      1. **Gebruiker:** george.lang
      1. **Wachtwoord:** wachtwoord
   1. Of imiteren:

      1. Typ &quot;**George**&quot; in het veld &quot;**Imiteren als**&quot;.

      1. Klik op OK om u voor te doen.


1. Klik in de rechterbovenhoek op het pictogram Melding (bel).
1. Klik &quot;**Bekijk allen**&quot;om aan Inbox te navigeren.
1. Open vanuit het Postvak In de laatste taak &quot;**Health Benefits Application Review**&quot;.

   ![Evaluatie van de gezondheidsuitkeringen](/help/forms/using/assets/health_benefits.png)

### Optioneel: AEM Inbox &amp; MS Dynamics (George) {#george-user-story-aem-inbox-and-ms-dynamics}

Dankzij gegevensintegratie en geautomatiseerde workflows wordt de toepassing van Aya weergegeven, samen met een CRM-record dat automatisch is gegenereerd op het moment dat de gegevens werden verzonden.

**Gebruikersinstructies:**

1. Open en inspecteer het alleen-lezen adaptieve formulier.
1. Klik op de knop &quot;**MS Dynamics**&quot; openen om de MS Dynamics-record in een nieuw venster te openen.
1. In CRM kunt u alle informatie zien kan worden bijgewerkt

   1. Voeg desgewenst enkele revisienotities rechtstreeks toe in Dynamiek.

1. Sluiten en terug naar AEM Postvak IN.

   ![MS Dynamics-record](/help/forms/using/assets/ms_dynamics.png)

### Terug naar AEM Postvak IN (George) {#george-user-story-back-to-aem-inbox}

George keurt de aanvraag van Aya goed en dankzij een bestaande geautomatiseerde workflow wordt ook een bevestigingsbericht naar Aya gestuurd.

**Gebruikersinstructies:**

1. Navigeer naar de linkerbovenhoek en klik op &quot;**Goedkeuren**&quot; om de toepassing goed te keuren.
1. In de modale modus kunt u een bericht voor de CX-lead achterlaten.
1. Klik op Gereed.
1. (Burgerrol) Open uw e-mailclient om de e-mail te bekijken die naar Aya is verzonden.

   ![De naar Aya verzonden e-mail weergeven](/help/forms/using/assets/email_client.png)

## CX lood (Camila) {#cx-lead-camila}

![Camila (CX lead)](/help/forms/using/assets/camila_santos-1.png)

**In deze sectie:** Camila, de CX-leider, heeft een welkome telefoongesprek met Aya opgezet om uit te leggen hoe gebruik kan worden gemaakt van de overheidsdiensten waarvoor zij is goedgekeurd.

### (Optioneel) AEM Inbox &amp; MS Dynamics {#camila-user-story-aem-inbox-ms-dynamics}

**Gebruikersinstructies:**

1. Navigeer naar *https://&lt;aemserver>:&lt;port>/aem/start.html*
1. Klik op het gebruikerspictogram (rechterbovenhoek) en gebruik &quot;**Sign Out**&quot;, of &quot;**Impersonate as**&quot;menuoptie als u momenteel met een administratieve gebruiker wordt het programma geopend.

   1. Aanmelden met:

      1. **Gebruiker**: camila.santos
      1. **Wachtwoord**: password
   1. Of imiteren:

      1. Typ &quot;**Camila**&quot; in het veld &quot;**Imiteren als**&quot;.

      1. Klik op OK om u voor te doen.


1. Klik in de rechterbovenhoek op het pictogram Melding (bel).
1. Klik &quot;**Bekijk allen**&quot;om aan Inbox te navigeren.
1. Open vanuit het vak Inbox de laatste taak &quot;**Nieuwe contactpersoon voor goedkeuring**&quot;.

![Nieuwe contactgoedkeuring](/help/forms/using/assets/new_contact_approval.png)

**(Optioneel) Gebruikersinstructies:**

1. Open en inspecteer het alleen-lezen adaptieve formulier.
1. Klik op de knop &quot;**MS Dynamics**&quot; openen om de MS Dynamics-record in een nieuw venster te openen.
1. In CRM kunt u alle informatie zien kan worden bijgewerkt

   1. Naar keuze, voeg direct een nieuwe vraagactiviteit in Dynamiek toe.
   1. Open de sectie &quot;**Activiteiten**&quot;.
   1. Klik op &quot;**Nieuwe Vraag van de Telefoon**&quot;optie.
   1. Voeg telefoongesprekdetails toe.
   1. Sla het venster op en sluit het.

1. Navigeer weer in AEM naar de linkerbovenhoek en klik op &quot;**Verzenden**&quot; om de toepassing te verzenden.
1. In de modale modus kunt u een bericht achterlaten.
1. Klik op Gereed.

   ![Activiteiten ](/help/forms/using/assets/activities_tab.png) ![tabbladNieuwe contactpersoon bevestigen](/help/forms/using/assets/confirm_new_contact.png)

## (Optioneel) Welkom Kit Citizen (Aya) {#welcome-kit-citizen-aya}

**In deze sectie:** Aya ontvangt een e-mail met een koppeling naar een interactieve communicatie waarin de voordelen worden samengevat en waarin ook formuliervelden worden opgenomen die moeten worden ingevuld. Met PDF-uitkeringsinstructie bijgevoegd en koppeling naar interactieve communicatieletter in de e-mail (met hetzelfde thema/branding als de interactieve communicatie).

### Melding e-mailclient (Aya) {#aya-user-story-email-client}

**Gebruikersinstructies:**

1. Zoek en open de welkomstkit-e-mail.
1. Blader naar de PDF-bijlage onder aan de pagina.
1. Klik om de PDF-bijlage te openen.
1. Schuif een back-up in uw e-mailclient en klik op &quot;**De welkomstkit online weergeven**&quot;.

   1. Hiermee wordt de webkanaalversie van hetzelfde document geopend.

1. Een snelle verwijzing naar PDF rechtstreeks vindt u:

   *https://&lt;aemserver>:&lt;port>/aem/formdetails.html/content/dam/formsanddocuments/adobe-gov-forms/welcome-handbook/we-gov-welcome-handbook*

1. Voor een snelle verwijzing naar IC direct:

   *https://&lt;aemserver>:&lt;port>/content/dam/formsanddocuments/adobe-gov-forms/welcome-handbook/we-gov-welcome-handbook/jcr:content?channel=web&amp;mode=preview&amp;wcmmode=disabled*

   ![Welkomstvoordelen ](/help/forms/using/assets/welcome_benefits_handbook.png) ![HandbookInteractive Communication Link](/help/forms/using/assets/interactive_communication.png)

## Herinnering burger (Aya) {#renewal-reminder-citizen-aya}

**In deze sectie:** Camila plant ook een herinnering voor communicatie, een jaar later. (Workflowstap die automatiseert/uitvoert en e-mail verzendt).

### Melding e-mailclient (Aya) {#aya-user-story-email-client-updated}

**Gebruikersinstructies:**

1. Navigeer naar uw e-mailclient.
1. Zoek en open het e-mailbericht Herinnering voor vernieuwen.
1. Klik op de knop &quot;**Een nieuwe toepassing verzenden**&quot; om het aangepaste formulier te openen.

   1. Deze sectie wordt opzettelijk leeg gelaten ter ondersteuning van gegevens die vooraf in fase 2 worden ingevuld.

   ![Herinnering voor e-mail vernieuwen](/help/forms/using/assets/renewal_reminder_email.png)

## (Optioneel) Formuliergegevensmodel (Camila) {#form-data-model}

**Deze sectie**: Camila navigeert naar AEM Forms Data Integrations waar ze een snelle test kan uitvoeren om te zien dat de informatie die via de integratie van het formuliergegevensmodel naar de externe gegevensbron wordt verzonden, aanwezig is.

### Formuliergegevensmodel (Camila) {#form-data-model-camila}

**Deze sectie**: Camila navigeert aan de pagina van Gegevensbronnen om de gegevens te bevestigen die de server binnen het gegevensbestand van Derby heeft herhaald.

1. Als de gebruikerservaring is voltooid en de gebruiker klaar is met verzenden, navigeert Camila naar het tabblad Gegevensbronnen in AEM Forms (**Forms** > **Gegevensintegratie**)

1. Camila selecteert vervolgens AEM Forms **We.gov FDM** en bewerkt vervolgens de **We.gov-inschrijving FDM**.

1. Camila selecteert vervolgens **Contact** > **Service lezen** om te testen.

   ![Contact opnemen met leesservice](assets/aftia-contact-read-service.jpg)

1. Camila verstrekt dan de testdienst van contactidentiteitskaart en klikt dan op de knoop van de Test. 1 of 2, bijvoorbeeld als u het formulier hebt verzonden. Als u het formulier niet hebt verzonden, worden er geen gegevens geretourneerd.

   ![Contact opnemen met leesservice](assets/aftia-test-service.jpg)

1. Camila kan dan bevestigen dat de gegevens met succes in de gegevensbron zijn opgenomen.

   * De gegevens in de DS van Derby lijken op de volgende indeling:

   ```xml
      [
         {
         "ADDRESS_COUNTRY": "USA",
         "LAST_NAME": "Tan",
         "ADDRESS_CITY": "New York",
         "FIRST_NAME": "Aya",
         "ADDRESS_STATE": "AL",
         "ADDRESS_LINE1": "123 Street crescent",
         "GENDER_CODE": "2",
         "ADDRESS_LINE2": "123 Street crescent",
         "ADDRESS_POSTAL_CODE": "90210",
         "BIRTH_DATE": "1991-12-12",
         "CONTACT_ID": 1,
         "MIDDLE_NAME": "M",
         "HAS_CHILDREN_CODE": "0"
         }
   ]
   ```

## (Optioneel) Analytics (Camila) {#analytics-cx-lead-camila}

**Dit gedeelte:** Camila navigeert naar een dashboard waar ze in de hele organisatie KPI&#39;s kan zien, zoals % van de burgers die beginnen met het invullen van een formulier voor een serviceaanvraag en het opgeven van hun aanvraag, de gemiddelde tijdsduur vanaf de indiening van een aanvraag tot de reactie op goedkeuring/weigering, en betrokkenheidsstatistieken voor de bonushandboeken die ze naar de burgers heeft gestuurd.

### Adobe Analytics Sites Reporting (Camila) {#camila-reviews-sites-reporting-we-gov-adobe-analytics}

1. Navigeer naar *https://&lt;aemserver>:&lt;port>/sites.html/content*
1. Selecteer &quot;**AEM Forms We.Gov Site**&quot; om de sitepagina&#39;s weer te geven.
1. Selecteer een van de sitepagina (bijvoorbeeld Home) en kies &quot;**Analytics &amp; Recommendations**&quot;.

   ![Analyse en aanbeveling](/help/forms/using/assets/analytics_recommendation.jpg)

1. Op deze pagina wordt opgehaalde informatie van Adobe Analytics weergegeven die betrekking heeft op de AEM Sites-pagina (OPMERKING: Deze informatie wordt door het ontwerp periodiek vernieuwd vanuit Adobe Analytics en wordt niet in real-time weergegeven).

   ![Metrische Adobe Analytics-sleutel](/help/forms/using/assets/analytics_key_metrics.jpg)

1. Terug op de pagina van de paginamening (betreden in stap 3.), kunt u de informatie van de paginamening ook bekijken door de vertoning te veranderen die aan meningspunten in &quot;**de Mening van de Lijst**&quot;plaatst te bekijken.
1. Zoek het vervolgkeuzemenu &quot;**Weergave**&quot; en selecteer &quot;**Lijstweergave**&quot;.

   ![Lijstweergave in het vervolgkeuzemenu Weergave](/help/forms/using/assets/list_view_view_dropdown.jpg)

1. Selecteer in hetzelfde menu de optie &quot;**Weergave-instelling**&quot; en selecteer de kolommen die u wilt weergeven in de sectie &quot;**Analytics**&quot;.

   ![De weergave van kolommen configureren](/help/forms/using/assets/view_setting_analytics.jpg)

1. Klik &quot;**Update**&quot;om de nieuwe kolommen ter beschikking te stellen.

   ![Nieuwe kolommen beschikbaar maken](/help/forms/using/assets/new_columns_available.jpg)

### Adobe Analytics Forms Reporting (Camila) {#camila-reviews-forms-reporting-we-gov-adobe-analytics}

1. Ga naar

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

1. Selecteer het adaptieve formulier &quot;**Inschrijvingstoepassing voor gezondheidsvoordelen**&quot; en selecteer de optie &quot;**Analyserapport**&quot;.

   ![Inschrijvingsaanvraag voor gezondheidsvoordelen](/help/forms/using/assets/analytics_report_benefits.jpg)

1. Wacht tot de pagina is geladen en bekijk de analysegegevens.

   ![Analyserapportgegevens](/help/forms/using/assets/analytics_report_data_updated.jpg)

