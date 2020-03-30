---
title: We.Gov-referentiesite doorloopt
seo-title: We.Gov-referentiesite doorloopt
description: Gebruik fictieve gebruikers en groepen om AEM Forms-taken uit te voeren met het Web.Gov-demopakket.
seo-description: Gebruik fictieve gebruikers en groepen om AEM Forms-taken uit te voeren met het Web.Gov-demopakket.
uuid: 797e301a-36ed-4bae-9ea8-ee77285c786d
contentOwner: anujkapo
discoiquuid: ddb3778b-be06-4cde-bc6e-0994efa42b18
docset: aem65
translation-type: tm+mt
source-git-commit: f323b490c37effc3cbb36c793b62fa788eca9545

---


# We.Gov-referentiesite doorloopt{#we-gov-reference-site-walkthrough}

## Voorwaarden {#pre-requisites}

Opstelling de verwijzingsplaats zoals die in [Opstelling wordt beschreven en vormt Web.Gov verwijzingsplaats](../../forms/using/forms-install-configure-gov-reference-site.md).

## Gebruikersartikel {#user-story}

* AEM-formulieren

   * Gegevens vastleggen
   * Gegevensintegratie (MS Dynamics)
   * Adobe-handtekening

* Workflow
* Klantcommunicatie

   * Afdrukkanaal
   * Webkanaal

* Adobe Analytics

### Fictitious users and groups {#fictitious-users-and-groups}

Het Wij.Gov-demopakket wordt geleverd met de volgende ingebouwde fictieve gebruikers:

* **Aya Tan**: Burgers die in aanmerking komen voor een dienst van een overheidsinstantie

![Fictieve gebruiker](/help/forms/using/assets/aya_tan_new.png)

* **George Lang**: We.Overheid Business Analyst

![Fictieve gebruiker](/help/forms/using/assets/george_lang.png)

* **Camila Santos**: We.Gov Agency CX Lead

![Fictieve gebruiker](/help/forms/using/assets/camila_santos.png)

De volgende groepen zijn eveneens opgenomen:

* **Gebruikers van GV-formulieren**

   * George Lang (lid)
   * Camila Santos (lid)

* **Wij.Gov-gebruikers**

   * George Lang (lid)
   * Camila Santos (lid)
   * Aya Tan (lid)

### Demo-overzicht: legenda {#demo-overview-terms-legend}

1. **Imiteren**: Gedefinieerde gebruikers en groepen in AEM-demo.
1. **Knop**: Gekleurde rechthoek of omcirkelde pijl voor navigatie.
1. **Klik**: Een handeling uitvoeren in het gebruikersartikel.
1. **Koppelingen**: Deze bevindt zich boven aan het hoofdmenu op de site Web.Gov.
1. **Gebruikersinstructies**: Een reeks numerieke stappen om door het verhaal van de gebruiker te navigeren.
1. **Formulierportal**: *https://&lt;aemserver>:&lt;port>/content/we-gov/formsportal.html*
1. **Mobiele weergave**:Gebruikers van de webserver kunnen een mobiele weergave repliceren met een browser van een andere grootte.
1. **Bureaubladweergave**: We gov-gebruikers bekijken de demo op een laptop of desktop.
1. **Pre-screener-formulier**: Formulier op de startpagina van de website Web.Gov.
1. **Adaptief formulier**: Inschrijvingsaanvraagformulier voor We.gov-demo.

   *https://&lt;aemserver>:&lt;port>/content/forms/af/adobe-gov-forms/enrollment-application-for-health-benefits.html*

1. **Adobe Web.Gov-site**: *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. **Adobe Inbox**: Pictogram [van](assets/bell.svg) Bell van de bovenste menubalk in AEM-achterkant.

   *https://&lt;aemserver>:&lt;port>/aem/start.html*

1. **E-mailclient**: Voorkeur voor het weergeven van e-mails (Gmail, Outlook)
1. **CTA**: Oproep tot actie
1. **Navigeren**: Een specifiek referentiepunt op de browserpagina zoeken.

## Demo van mobiele weergave {#mobile-view-demo}

**Dit deel moet vóór de demonstratie worden uitgevoerd.**

**Gebruikersinstructies:**

1. Navigeren naar: *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. Aanmelden met:

   1. **Gebruiker**: aya.tan
   1. **Wachtwoord**: password

1. Wijzig de grootte van het browservenster of gebruik de emulator van de browser om een mobiele apparaatgrootte te repliceren.

### Aya-gebruikersartikel (website Web.Gov) {#aya-user-story-we-gov-website}

![Fictieve gebruiker](/help/forms/using/assets/aya_tan_new-1.png)

**Deze sectie**: Aya is een burger. Ze hoort van een vriend dat ze in aanmerking komt voor een service van een overheidsinstelling. Aya navigeert vanaf haar mobiele telefoon naar de website We.Gov voor meer informatie over services waarvoor ze in aanmerking komt.

### Aya-gebruikersartikel (We.Gov-voorscreener) {#aya-user-story-we-gov-pre-screener}

Aya beantwoordt een paar vragen om haar geschiktheid te bevestigen door een kort adaptief formulier in te vullen op haar mobiele telefoon.

**Gebruikersinstructies:**

1. Maak een selectie in elk vervolgkeuzeveld.

   1. Opmerking: Als de gebruiker meer dan $200.000/jaar verdient, komen ze niet in aanmerking.

1. Klik op &quot;**Ben ik in aanmerking komend?**” button.
1. Klik op de knop &quot;Nu **toepassen**&quot; om door te gaan.

   ![Koppeling Nu toepassen](/help/forms/using/assets/apply_now_link.png)

### Aya-gebruikersartikel (adaptief formulier Wij.Gov) {#aya-user-story-we-gov-adaptive-form}

Aya vindt dat ze in aanmerking komt en vult haar aanvraag in om service aan te vragen op haar mobiele apparaat.

Aya moet sommige documenten thuis herzien alvorens zij de toepassing van het de dienstverzoek kan voltooien. Ze slaat de toepassing op en sluit deze af.

**Gebruikersinstructies:**

1. Vul de velden Basisinformatie in. U moet de volgende velden en downloads invullen:

   1. Basisinformatie

      1. Voornaam
      1. Tweede voornaam
      1. Achternaam
      1. Voorkeursnaam
      1. DOB
      1. Geslacht
   1. Contactgegevens

      1. Adres
      1. Plaats
      1. Telefoonnummer
      1. Postcode
      1. E-mail
      1. Staat
   1. Staat van echtscheiding

      1. Familiestatus



1. Gebruik de volgende **dynamische logica** om de dynamische eigenschap te tonen gebruikend het **drop-down van de Status** van de Familie:

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

**Deze sectie:** Terug thuis heeft Aya de informatie gevonden die ze nodig heeft en de toepassing hervat vanaf haar bureaublad. Navigeert altijd naar de online formulierportal om haar toepassing te hervatten. Met een eenvoudige aanpassing kunnen agentschappen ook automatisch een koppeling genereren en e-mailen om de toepassing te hervatten.

### Aya-gebruikersartikel (vervolg adaptief formulier) {#aya-user-story-continued-adaptive-form}

**Gebruikersinstructies:**

1. Ga naar *https://&lt;aemserver>:&lt;port>/content/we-gov/home.html*
1. Klik in de navigatiebalk op &quot;**Online services**&quot;.
1. Selecteer in het venster &quot;Conceptformulieren&quot; de bestaande &quot;Inschrijvingstoepassing voor gezondheidsvoordelen&quot;.

   ![Inschrijvingsaanvraag voor gezondheidsvoordelen](/help/forms/using/assets/enrollment_application.png)

   De look en feel zijn hetzelfde en ze hoeft geen gegevens opnieuw in te voeren.

   **Gebruikersinstructies:**

1. Klik op Cirkel CTA rechts om naar de volgende sectie te gaan.

   ![Rechthoekcirkel CTA](/help/forms/using/assets/right_circle_cta_new.png)

   Het formulier wordt gevuld tot het punt van de laatste vermelding van Aya. Aya heeft al haar gegevens ingevoerd en is bereid deze te verzenden.

   ![Het adaptieve formulier verzenden](/help/forms/using/assets/submit_adaptive_form.png)

   Na het verzenden van Aya ontvangt ze een e-mail die ze opent en kan ze elektronisch ondertekenen met Adobe Sign.

**Gebruikersinstructies:**

1. Na verzending wordt de pagina Bedankt weergegeven.
1. Navigeer naar uw e-mailclient en zoek de Adobe-e-mail voor ondertekening.
1. Klik op de koppeling naar Adobe-ondertekening.

   ![Adobe-koppeling voor ondertekenen](/help/forms/using/assets/adobe_sign_link.png)

**Gebruikersinstructies:**

1. Schakel het selectievakje **Ik ga akkoord** in.
1. Klik op &quot;**Accepteren**&quot;.
1. Blader naar de onderkant van het gereviseerde document.
1. Klik op de gemarkeerde gele tab om het document te ondertekenen.

   ![Het document](/help/forms/using/assets/sign_document_new.png) ondertekenen en het testdocument ![ondertekenen](/help/forms/using/assets/sign_test_document.png)

## Regeringsagent (George) {#government-agent-george}

![Government Agent George](/help/forms/using/assets/george_lang-1.png)

**Deze sectie:** George is een zakenanalist bij het overheidsagentschap Aya vraagt om een dienst van. George heeft één dashboard waar hij alle toepassingen van het de dienstverzoek kan zien die aan hem voor overzicht zijn toegewezen.

### George User Story (AEM-Postvak) {#george-user-story-aem-inbox}

**Gebruikersinstructies:**

1. Ga naar *https://&lt;aemserver>:&lt;port>/aem/start.html*
1. Klik op het gebruikerspictogram (rechterbovenhoek) en gebruik de optie **Afmelden** of de menuoptie &quot;**Imiteren als**&quot; als u momenteel bent aangemeld bij een beheerder.

   1. Aanmelden met:

      1. **Gebruiker:** george.lang
      1. **Wachtwoord:** password
   1. Of imiteren:

      1. Typ &quot;**George**&quot; in het veld &quot;**Impersonate as**&quot;.

      1. Klik op OK om u voor te doen.


1. Klik in de rechterbovenhoek op het pictogram Melding (bel).
1. Klik op Alles **** weergeven om naar het Postvak IN te navigeren.
1. Open vanuit het Postvak In de nieuwste taak &quot;**Health Benefits Application Review**&quot;.

   ![Evaluatie van de gezondheidsuitkeringen](/help/forms/using/assets/health_benefits.png)

### George User Story (AEM-inbox en MS Dynamics) {#george-user-story-aem-inbox-and-ms-dynamics}

Dankzij gegevensintegratie en geautomatiseerde workflows wordt de toepassing van Aya weergegeven, samen met een CRM-record dat automatisch is gegenereerd op het moment dat de gegevens werden verzonden.

**Gebruikersinstructies:**

1. Open en inspecteer het alleen-lezen adaptieve formulier.
1. Klik op de knop &quot;MS Dynamics **** openen&quot; om de record voor MS Dynamics in een nieuw venster te openen.
1. In CRM kunt u alle informatie zien kan worden bijgewerkt

   1. Voeg desgewenst enkele revisienotities rechtstreeks toe in Dynamiek.

1. Sluit en ga terug naar AEM Inbox.

   ![MS Dynamics-record](/help/forms/using/assets/ms_dynamics.png)

### George User Story (terug naar AEM-Postvak) {#george-user-story-back-to-aem-inbox}

George keurt de aanvraag van Aya goed en dankzij een bestaande geautomatiseerde workflow wordt ook een bevestigingsbericht naar Aya gestuurd.

**Gebruikersinstructies:**

1. Navigeer naar de linkerbovenhoek en klik op **Goedkeuren** om de toepassing goed te keuren.
1. In de modale modus kunt u een bericht voor de CX-lead achterlaten.
1. Klik op Gereed.
1. (Burgerrol) Open uw e-mailclient om de e-mail te bekijken die naar Aya is verzonden.

   ![De naar Aya verzonden e-mail weergeven](/help/forms/using/assets/email_client.png)

## CX-lood (Camila) {#cx-lead-camila}

![Camila (CX lead)](/help/forms/using/assets/camila_santos-1.png)

**Deze sectie:** Camila de CX Lead organiseert een welkome telefoongesprek met Aya om uit te leggen hoe gebruik kan worden gemaakt van de overheidsdiensten waarvoor ze is goedgekeurd.

### Camila User Story (AEM-inbox &amp; MS Dynamics) {#camila-user-story-aem-inbox-ms-dynamics}

**Gebruikersinstructies:**

1. Ga naar *https://&lt;aemserver>:&lt;port>/aem/start.html*
1. Klik op het gebruikerspictogram (rechterbovenhoek) en gebruik de optie **Afmelden** of de menuoptie &quot;**Imiteren als**&quot; als u momenteel bent aangemeld bij een beheerder.

   1. Aanmelden met:

      1. **Gebruiker**: camila.santos
      1. **Wachtwoord**: password
   1. Of imiteren:

      1. Typ &quot;**Camila**&quot; in het veld &quot;**Impersonate as**&quot;.

      1. Klik op OK om u voor te doen.


1. Klik in de rechterbovenhoek op het pictogram Melding (bel).
1. Klik op Alles **** weergeven om naar het Postvak IN te navigeren.
1. Open vanuit het Postvak In de laatste taak **Nieuwe contactgoedkeuring**.

   ![Nieuwe contactgoedkeuring](/help/forms/using/assets/new_contact_approval.png)

   **Gebruikersinstructies:**

1. Open en inspecteer het alleen-lezen adaptieve formulier.
1. Klik op de knop &quot;MS Dynamics **** openen&quot; om de record voor MS Dynamics in een nieuw venster te openen.
1. In CRM kunt u alle informatie zien kan worden bijgewerkt

   1. Naar keuze, voeg direct een nieuwe vraagactiviteit in Dynamiek toe.
   1. Open de sectie &quot;**Activiteiten**&quot;.
   1. Klik op de optie &quot;**Nieuwe Vraag** van de Telefoon&quot;.
   1. Voeg telefoongesprekdetails toe.
   1. Sla het venster op en sluit het.

1. Navigeer weer in AEM naar de linkerbovenhoek en klik op &quot;**Verzenden**&quot; om de toepassing te verzenden.
1. In de modale modus kunt u een bericht achterlaten.
1. Klik op Gereed.

   ![Het tabblad](/help/forms/using/assets/activities_tab.png) Activiteiten ![Nieuwe contactpersoon bevestigen](/help/forms/using/assets/confirm_new_contact.png)

## Welkom Kit-burger (Aya) {#welcome-kit-citizen-aya}

**Deze sectie:** Aya ontvangt een e-mailbericht met een koppeling naar een interactieve communicatie waarin de voordelen van het bericht worden samengevat en waarin ook formuliervelden worden opgenomen die moeten worden ingevuld. Met PDF-uitkeringsinstructie bijgevoegd en koppeling naar interactieve communicatieletter in de e-mail (met hetzelfde thema/branding als de interactieve communicatie).

### Aya-gebruikersartikel (e-mailclient) {#aya-user-story-email-client}

**Gebruikersinstructies:**

1. Zoek en open de welkomstkit-e-mail.
1. Blader naar de PDF-bijlage onder aan de pagina.
1. Klik om de PDF-bijlage te openen.
1. Schuif een back-up in uw e-mailclient en klik op &quot;**Welkomstkit online** weergeven&quot;.

   1. Hiermee wordt de webkanaalversie van hetzelfde document geopend.

1. Een snelle verwijzing naar PDF rechtstreeks vindt u:

   *https://&lt;aemserver>:&lt;port>/aem/formdetails.html/content/dam/formsanddocuments/adobe-gov-forms/welcome-handbook/we-gov-welcome-handbook*

1. Voor een snelle verwijzing naar IC direct:

   *https://&lt;aemserver>:&lt;port>/content/dam/formsanddocuments/adobe-gov-forms/welcome-handbook/we-gov-welcome-handbook/jcr:content?channel=web&amp;mode=preview&amp;wcmmode=disabled*

   ![Welkomstvoordelen Handboek](/help/forms/using/assets/welcome_benefits_handbook.png) ![Interactieve Communicatie Verbinding](/help/forms/using/assets/interactive_communication.png)

## Herinnering burger (Aya) {#renewal-reminder-citizen-aya}

**Deze sectie:** Camila plant ook een herinnering voor communicatie, een jaar later. (Workflowstap die automatiseert/uitvoert en e-mail verzendt).

### Aya-gebruikersartikel (e-mailclient) {#aya-user-story-email-client-1}

**Gebruikersinstructies:**

1. Navigeer naar uw e-mailclient.
1. Zoek en open het e-mailbericht Herinnering voor vernieuwen.
1. Klik op de knop &quot;**Een nieuwe toepassing** verzenden&quot; om het aangepaste formulier te openen.

   1. Deze sectie wordt opzettelijk leeg gelaten ter ondersteuning van gegevens die vooraf in fase 2 worden ingevuld.
   ![Herinnering voor e-mail vernieuwen](/help/forms/using/assets/renewal_reminder_email.png)

## Analytics CX Lead (Camila) {#analytics-cx-lead-camila}

**Deze sectie:** Camila navigeert naar een dashboard waar ze in de hele organisatie KPI&#39;s kan zien, zoals % van de burgers die beginnen met het invullen van een formulier voor een serviceaanvraag en afzien, de gemiddelde tijdsduur van indiening van een aanvraag tot een antwoord op een vraag over goedkeuring/weigering, en betrokkenheidsstatistieken voor de bonushandboeken die ze naar de burgers heeft gestuurd.

### Camila beoordeelt Sites-rapportage (We.Gov Adobe Analytics) {#camila-reviews-sites-reporting-we-gov-adobe-analytics}

1. Ga naar *https://&lt;aemserver>:&lt;port>/sites.html/content*
1. Selecteer de site ****&quot;AEM Forms We.Gov&quot; om de sitepagina&#39;s weer te geven.
1. Selecteer een van de sitepagina (bijvoorbeeld Home) en kies &quot;**Analytics &amp; Recommendations**&quot;.

   ![Analyse en aanbeveling](/help/forms/using/assets/analytics_recommendation.jpg)

1. Op deze pagina wordt opgehaalde informatie van Adobe Analytics weergegeven, die betrekking heeft op de pagina AEM Sites (OPMERKING: Deze informatie wordt door het ontwerp periodiek vernieuwd vanuit Adobe Analytics en wordt niet in real-time weergegeven).

   ![Belangrijke meetgegevens van Adobe Analytics](/help/forms/using/assets/analytics_key_metrics.jpg)

1. Terug op de pagina van de paginamening (betreden in stap 3.), kunt u de informatie van de paginamening ook bekijken door de vertoning te veranderen die punten in de &quot;Mening **van de** Lijst&quot;plaatst te bekijken.
1. Zoek het vervolgkeuzemenu **Weergave** en selecteer **Lijstweergave**.

   ![Lijstweergave in het vervolgkeuzemenu Weergave](/help/forms/using/assets/list_view_view_dropdown.jpg)

1. Selecteer &#39;**Weergave-instelling**&#39; in hetzelfde menu en selecteer de kolommen die u wilt weergeven in de sectie &#39;**Analytics**&#39;.

   ![De weergave van kolommen configureren](/help/forms/using/assets/view_setting_analytics.jpg)

1. Klik op &quot;**Bijwerken**&quot; om de nieuwe kolommen beschikbaar te maken.

   ![Nieuwe kolommen beschikbaar maken](/help/forms/using/assets/new_columns_available.jpg)

### Camila controleert Forms Reporting (We.Gov Adobe Analytics) {#camila-reviews-forms-reporting-we-gov-adobe-analytics}

1. Ga naar

   *https://&lt;aemserver>:&lt;port>/aem/forms.html/content/dam/formsanddocuments/adobe-gov-forms*

1. Selecteer het adaptieve formulier &quot;**Inschrijvingstoepassing voor gezondheidsvoordelen**&quot; en selecteer de optie &quot;**Analyserapport**&quot;.

   ![Inschrijvingsaanvraag voor gezondheidsvoordelen](/help/forms/using/assets/analytics_report_benefits.jpg)

1. Wacht tot de pagina is geladen en bekijk de analysegegevens.

   ![Analyserapportgegevens](/help/forms/using/assets/analytics_report_data_updated.jpg)

