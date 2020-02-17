---
title: Zelfstudie - Uw eerste interactieve communicatie maken
seo-title: Maak uw eerste interactieve communicatie
description: Leer om uw eerste Interactieve Communicatie tot stand te brengen.
seo-description: Leer om uw eerste Interactieve Communicatie tot stand te brengen.
uuid: ed5003c6-ba3a-4fcb-8645-c7b607b22fb5
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: interactive-communications
discoiquuid: 954da8da-a30b-477d-bde7-3edd86a5be11
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Zelfstudie: Maak uw eerste interactieve communicatie {#tutorial-create-your-first-interactive-communication}

Leer om uw eerste Interactieve Communicatie tot stand te brengen.

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

De interactieve Mededelingen centraliseert en beheert de verwezenlijking, de assemblage, en de levering van veilige, gepersonaliseerde, en interactieve correspondentie zoals bedrijfscorrespondentie, documenten, verklaringen, marketing post, rekeningen, en welkomstkits. Interactieve communicatie kan via twee kanalen worden aangeboden: Afdrukken en web. Het kanaal van de Druk wordt gebruikt om PDFs en papiermededelingen tot stand te brengen, terwijl het kanaal van het Web wordt gebruikt om online ervaringen te leveren.

Deze zelfstudie biedt een end-to-end framework voor het maken van interactieve communicatie. De zelfstudie is ingedeeld in een gebruikscase en meerdere hulplijnen. Elke gids helpt u om eigenschappen tot stand te brengen die als bouwstenen worden gebruikt om een Interactieve Communicatie tot stand te brengen.

De volgende afbeelding illustreert de bouwstenen die nodig zijn om een interactieve communicatie te maken.

![werkstroom](assets/workflow.gif)

Aan het einde van deze zelfstudie kunt u het volgende doen:

* Bouwstenen maken (formuliergegevensmodel, documentfragmenten en sjablonen)
* Een interactieve communicatie maken
* Een interactieve communicatie testen en publiceren

## Hoofdletters gebruiken {#use-case}

De reis begint met het leren van het gebruiksgeval:

Een telecomoperator stuurt maandelijkse facturen naar de klanten via e-mail. De rekening is een Interactieve Communicatie. Het e-mailbericht bevat:

* Een PDF die met een wachtwoord is beveiligd. Dit wordt in deze zelfstudie het afdrukkanaal genoemd. Het omvat klantgegevens, factureringsdetails, overzicht van kosten, geschikte wijzen van betaling van de rekening, en gebruiksdetails.
* Een koppeling naar de webversie van de factuur, in deze zelfstudie ook wel webkanaal genoemd. De webversie van de factuur biedt naast de gegevens die in de PDF-versie worden vermeld, een grafische weergave van de gebruiksgegevens en de persoonlijke aanbiedingen op basis van Adobe Target. De webversie bevat ook een online betalingsformulier. Het helpt om online betalingen te doen zonder het IC te verlaten.
* Een koppeling naar services met toegevoegde waarde, zoals onlineopslag, muziekabonnementen en video-abonnementen op aanvraag.

## Vereisten {#prerequisites}

* Stel een instantie van AEM-auteurs in.
* Invoegtoepassing [AEM Forms installeren](/help/forms/using/installing-configuring-aem-forms-osgi.md) op auteurinstantie
* De MYSQL-database instellen
* Vraag het JAR-bestand (JDBC-databasestuurprogramma) aan bij de databaseprovider. De voorbeelden in de zelfstudie zijn gebaseerd op MySQL-database en gebruiken het [MySQL JDBC-databasestuurprogramma](https://dev.mysql.com/downloads/connector/j/5.1.html)van Oracle.

## Stap 1: De interactieve communicatie plannen {#step-plan-the-interactive-communication}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

De eerste stap in het plannen van een Interactieve Mededeling is de inhoud van de Interactieve Mededeling te voltooien. Nadat de inhoud wordt voltooid, moet u het analyseren om de diverse activatypes te identificeren die worden vereist om de Interactieve Mededeling tot stand te brengen.

**Doelstellingen:**

Om een anatomie voor Interactieve Communicatie met de volgende wijzen van gegevensinput tot stand te brengen:

* Statische tekst
* Formuliergegevensmodel
* Gebruikersinterface van agent
* Voorwaardelijke gegevens
* Afbeeldingen

   [ ![zie-de-gids-sm](assets/see-the-guide-sm.png)](/help/forms/using/planning-interactive-communications.md)

## Stap 2:Formuliergegevensmodel maken {#step-create-form-data-model}

![03-create-adaptive-form-main-image_small](assets/03-create-adaptive-form-main-image_small.png)

Met een formuliergegevensmodel kunt u een interactieve communicatie met verschillende gegevensbronnen verbinden. Bijvoorbeeld: AEM-gebruikersprofiel, RESTful-webservices, SOAP-webservices, OData-services en relationele databases. Een model van vormgegevens is een verenigd schema van de gegevensvertegenwoordiging van bedrijfsentiteiten en de diensten beschikbaar in verbonden gegevensbronnen. U kunt het model van formuliergegevens met een interactieve communicatie gebruiken om gegevens op te halen uit verbonden gegevensbronnen. Voor meer informatie over het model van vormgegevens, zie de Integratie [van Gegevens van](/help/forms/using/data-integration.md)Vormen AEM.

**Doelstellingen:**

* Database-instantie (MySQL-database) configureren als gegevensbron
* Maak het formuliergegevensmodel met MySQL-database als gegevensbron
* Gegevensmodelobjecten toevoegen aan formuliergegevensmodel
* Lezen- en schrijfservices configureren voor het gegevensmodel van het formulier
* Koppelingen maken tussen gegevensmodelobjecten
* Automatisch gegenereerde voorbeeldgegevens weergeven
* Voorbeeldgegevens bewerken
* Formuliergegevensmodel testen en geconfigureerde services met testgegevens

   [ ![zie-de-gids-sm](assets/see-the-guide-sm.png)](/help/forms/using/create-form-data-model0.md)

## Stap 3: Documentfragmenten maken {#step-create-document-fragments}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Documentfragmenten zijn herbruikbare componenten van een correspondentie die worden gebruikt om een interactieve communicatie samen te stellen. De documentfragmenten zijn van het type: Tekst, Lijst en Voorwaarde.

**Doelstellingen:**

*  Documentfragmenten maken
* Variabelen maken
* Regels maken en toepassen

   [ ![zie-de-gids-sm](assets/see-the-guide-sm.png)](/help/forms/using/create-document-fragments.md)

## Stap 4: Sjablonen maken {#step-create-templates}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Als u een interactieve communicatie wilt maken, moet u sjablonen op de AEM-server beschikbaar hebben voor Afdrukken en Webkanalen.

De sjablonen voor het kanaal Afdrukken worden gemaakt in Adobe Forms Designer en geüpload naar de AEM-server. Deze malplaatjes zijn dan beschikbaar voor gebruik terwijl het creëren van een Interactieve Mededeling.

De sjablonen voor het webkanaal worden gemaakt in AEM. Sjabloonauteurs en -beheerders kunnen websjablonen maken, bewerken en inschakelen. Zodra gecreeerd en toegelaten, zijn deze malplaatjes beschikbaar voor gebruik terwijl het creëren van een Interactieve Communicatie.

**Doelstellingen:**

* XDP-sjablonen maken voor het afdrukkanaal met Adobe Forms Designer
* De XDP-sjablonen uploaden naar de AEM Forms Server
* Sjablonen voor het webkanaal maken en inschakelen

   [ ![zie-de-gids-sm](assets/see-the-guide-sm.png)](/help/forms/using/create-templates-print-web.md)

## Stap 5: Een interactieve communicatie maken {#step-create-an-interactive-communication}

![09-stijl-uw-adaptief-vorm-klein](assets/09-style-your-adaptive-form-small.png)

Zodra u alle bouwstenen zoals het model van vormgegevens, documentfragmenten, en malplaatjes voor de Webversie creeert, kunt u beginnen tot een Interactieve Mededeling te leiden.

De interactieve Mededelingen kunnen door twee kanalen worden geleverd: Afdrukken en web. U kunt ook een interactieve communicatie maken met Afdrukkanaal als stramien. Met de optie Afdrukken als hoofdoptie voor het webkanaal wordt gegarandeerd dat de inhoud, overerving en gegevensbinding van het webkanaal worden afgeleid van het kanaal Afdrukken.

**Doelstellingen:**

* Interactieve communicatie maken voor het afdrukkanaal
* Interactieve communicatie voor het webkanaal maken
* Interactieve communicatie voor afdrukken en web maken met Afdrukken als origineel
* Een dynamische tabel maken in de webversie van Interactieve communicatie
* Creeer een grafiek in de versie van het Web van Interactieve Communicatie
* Hyperlinks maken in de webversie van Interactieve communicatie

   [ ![zie-de-gids-sm](assets/see-the-guide-sm.png)](/help/forms/using/create-interactive-communication0.md)

## Stap 6: Interactieve communicatie testen {#step-test-your-interactive-communication}

![11-test-uw-adaptieve vorm](assets/11-test-your-adaptive-form.png)

Zodra u een Interactieve Communicatie hebt gecreeerd, is het belangrijk dat u elke verandering test die u in hen aanbrengt. Het testen van elk gebied van een Interactieve Mededeling is vervelend. AEM Forms verstrekt SDK (Calvin SDK) om het testen van Interactieve Mededelingen in Webbrowser te automatiseren.

**Doelstellingen:**

* Testsuite maken
* Testcase maken
* Voer de testcase uit

## Stap 7: Uw interactieve communicatie publiceren {#step-publish-your-interactive-communication}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

Nadat u interactieve communicatie hebt gemaakt en getest met de kanalen Afdrukken en Web, kunt u deze elementen publiceren. Het gebruiksscenario dat in deze zelfstudie wordt beschreven, is gericht op het integreren van deze elementen met een e-mailclient. De e-mailclient fungeert als brug voor het verzenden van interactieve communicatie naar meerdere e-mailadressen.

**Doelstellingen:**

* Integreer Interactieve Mededelingen met een e-mailcliënt om een mededeling naar de klanten te kunnen verzenden
* Een PDF-document opnemen als een bijlage (interactieve communicatie gemaakt in het afdrukkanaal)
* Neem een koppeling op naar de webversie van de interactieve communicatie

