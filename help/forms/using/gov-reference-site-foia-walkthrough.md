---
title: We.Gov-referentiesite FOIA-doortocht
seo-title: We.Gov-referentiesite FOIA-doortocht
description: Zie de website van de website We.Gov om te begrijpen hoe AEM Forms regeringen helpt om informatie te ontvangen en te verstrekken die door individuen wordt gevraagd op grond van de Freedom of Information Act.
seo-description: Zie de website van de website We.Gov om te begrijpen hoe AEM Forms regeringen helpt om informatie te ontvangen en te verstrekken die door individuen wordt gevraagd op grond van de Freedom of Information Act.
uuid: 65d4233c-8dad-4e5e-8e39-22eb4f145adc
topic-tags: introduction
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: cef8f597-7935-4d98-aacf-9981470ab620
translation-type: tm+mt
source-git-commit: af326f2d2b278fe36df05afc8c172f74c99a064c
workflow-type: tm+mt
source-wordcount: '865'
ht-degree: 0%

---


# We.Gov-referentiesite FOIA-doortocht {#we-gov-reference-site-foia-walkthrough}

## Referentiescenario voor de Freedom of Information Act {#reference-site-freedom-of-information-act-scenario}

We.Gov is een overheidsorganisatie die adoptieve ouders de mogelijkheid biedt om in te schrijven voor kinderopvang als ze een kind adopteren. We.Gov staat ouders ook toe om informatie te vragen van de volgende regeringsdepartementen in het kader van de wet op de vrijheid van informatie:

* Defense Logistics Agency
* Department of Defense Office of Inspector General
* Department of Justice - Office of Information Policy
* Departement marine
* Agentschap voor milieubescherming

Zie [www.foia.gov](https://www.foia.gov)voor meer informatie over de Freedom of Information Act.

Het scenario omvat de volgende personen:

* Sarah Rose, de persoon die om informatie verzoekt krachtens
* John Jacobs, de persoon die het verzoek behandelt, stuurt het door naar de bevoegde dienst
* Gloria Rios, de overheidsfunctionaris die de informatie verstrekt overeenkomstig het verzoek

## Sarah initieert verzoek om informatie onder FOIA {#sarah-initiates-request-for-information-under-foia}

In het kader van de Freedom of Information Act vraagt Sarah om een kopie van de &quot;Administration for Children and Families case logs&quot; (FY) voor de jaren 2013 tot en met 2016. Sarah legt dit verzoek voor aan het Ministerie van Justitie - Office of Information Policy en geeft ook aan dat ze bereid is tot 100 dollar te betalen voor de druk- en postkosten.

### Hoe werkt het {#how-it-works}

### Zie het zelf {#see-it-yourself}

Open deze in uw browser `https://<hostname>:<PublishPort>/wegov`. Tik op de website Web.Gov op Toepassingen > Alle toepassingen. Tik op de pagina Alle toepassingen op Toepassen onder Toepassing voor FOIA-verzoek.

## Sarah start haar verzoek om informatie onder FOIA {#sarah-starts-her-application-for-information-under-foia}

Sarah klikt op **Toepassen** en in de pagina &quot;Freedom of Information Act Request Form&quot; voert Sarah informatie in, waaronder:

* **Bureau:** Sarah geeft aan tot welk agentschap het verzoek is gericht als Department of Justice - Office of Information Policy.

* **Betalen tot**: Sarah geeft aan dat ze bereid is tot 100 dollar te betalen voor druk- en verzendkosten.
* **Beschrijf de aanvraag in detail**: Sarah specificeert &quot;het verzoeken om exemplaar van het Beleid voor Kinderen en Gezinnen dossierlogboeken voor begrotingsjaren 2013 door 2016.&quot;

![Verzoek om een kopie van het dossier &quot;Administration for Children and Families&quot; voor de begrotingsjaren 2013 tot en met 2016](assets/sarahfiosform.png)

Verzoek om een kopie van het dossier &quot;Administration for Children and Families&quot; voor de begrotingsjaren 2013 tot en met 2016

Sarah kan op elk gewenst moment op Opslaan tikken om het concept van het formulier op te slaan en later terugkeren om het formulier in te vullen en te verzenden. Sarah legt het formulier voor.

>[!NOTE]
>
>De workflow voor het hervatten van e-mailberichten werkt alleen met aangemelde gebruikers. In het scenario van de verwijzingsplaats, zorg ervoor dat de gebruiker Sarah Rose wordt toegevoegd. Sarah&#39;s aanmeldgegevens zijn `srose/password`.

## John Jacobs ontvangt de aanvraag en keurt deze goed {#john-jacobs-receives-and-approves-the-application}

John Jacobs ontvangt de verzoeken en leidt ze naar de juiste persoon. AEM Inbox laat haar alle ingediende aanvragen op één plaats zien.

### Hoe werkt het {#how-it-works-1}

Wanneer Sarah de FOIA-toepassing invult en verzendt, wordt een record van de toepassing verzonden naar de inbox van John Jacobs. John Jacobs kan de ingediende aanvraag bekijken en deze accepteren of afwijzen.

### Zie het zelf {#see-it-yourself-1}

U kunt tot AEM inbox op https://&lt;***hostname***>:&lt;***PublishPort***>/content/we-finance/global/en/login.html toegang hebben?resource=/aem/inbox.html. Meld u aan bij de AEM inbox met jjacobs/password als gebruikersnaam/wachtwoord voor John Jacobs en zie de FOIA-toepassing. Zie Forms-toepassingen en -taken [beheren in AEM Postvak IN](/help/forms/using/manage-applications-inbox.md)voor informatie over het gebruik van AEM Postvak IN voor op formulieren gerichte workflowtaken.

![johnjacobs](assets/johnjacobs.png)

John Jacobs kan de toepassing van het toepassingsdashboard zien, goedkeuren of afwijzen. John Jacobs selecteert en opent de verzoekdetails en na het herzien van het verzoek, keurt het goed.

![johnjacobstaskdetail-1](assets/johnjacobstaskdetail-1.png)

### <strong>Sarah ontvangt een bevestigingsbericht</strong> {#strong-sarah-receives-an-acknowledgement-email-strong}

Nadat John Jacobs de aanvraag goedkeurt, ontvangt Sarah een bevestigingsmail van de website We.Gov. Sarah wordt op de hoogte gebracht van de kosten en de tijd die nodig zijn voor de behandeling van haar aanvraag. Het e-mailbericht bevat ook e-mail- en telefoongegevens die sarah kan raadplegen voor updates van haar toepassing.

![sarahroseemail](assets/sarahroseemail.png)

## Gloria ontvangt het FOIA-verzoek om goedkeuring op het tweede niveau {#gloria-receives-the-foia-request-for-second-level-approval}

Nadat John Jacobs de vereiste informatie heeft ingevuld en het verzoek van Sarah heeft goedgekeurd, gaan de verzoeken naar Gloria Rios voor de definitieve goedkeuring. Gloria herziet het bijgevoegde stuk met stukken en keurt het verzoek goed.

![gloriariosinbox](assets/gloriariosinbox.png)

### Hoe werkt het {#how-it-works-2}

Wanneer John Jacobs het FOIA-verzoek goedkeurt, wordt een PDF- of Document of Record-bestand van de toepassing gemaakt en naar Gloria Rios&#39; inbox verzonden. Gloria kan het ingediende verzoek bekijken en het goedkeuren of afwijzen.

### Zie voor uzelf {#see-for-yourself}

U kunt tot AEM inbox op https://&lt;***hostname***>:&lt;***PublishPort***>/content/we-finance/global/en/login.html toegang hebben?resource=/aem/inbox.html. Meld u aan bij de AEM-inbox met behulp van grios/wachtwoord als gebruikersnaam/wachtwoord voor Gloria Rios, en raadpleeg de FOIS-aanvraag.

Gloria opent het verzoek en onderzoekt de bijzonderheden van het FOIA-verzoek. Na bestudering van de bijzonderheden van het verzoek en na te gaan of het haalbaar is de vereiste documenten over te leggen, keurt Gloria het verzoek goed.

![gloriarioskeurt goed](assets/gloriariosapproves.png)

## Sarah ontvangt een melding dat haar verzoek is goedgekeurd {#sarah-receives-notification-that-her-request-is-approved}

Nadat Gloria het FOIA-verzoek heeft goedgekeurd, ontvangt Sarah een e-mail met de kennisgeving dat haar verzoek is goedgekeurd. De e-mail bevat ook de informatie over de voorlopige tijdlijn voor het verzenden van het document en contactgegevens voor de follow-up van het verzoek.

![sarahroseemaily](assets/sarahroseemailapproval.png)

