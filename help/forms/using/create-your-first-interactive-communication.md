---
title: Zelfstudie - Uw eerste interactieve communicatie maken
description: Leer om uw eerste Interactieve Communicatie tot stand te brengen.
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: interactive-communications, introduction
feature: Interactive Communication
exl-id: b20bb719-5686-466e-8dde-279b8471bfe3
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '976'
ht-degree: 0%

---

# Lesbestand: uw eerste interactieve communicatie maken {#tutorial-create-your-first-interactive-communication}

Leer om uw eerste Interactieve Communicatie tot stand te brengen.

![&#x200B; 01-creeer-eerste-adaptief-vorm-held-beeld &#x200B;](assets/01-create-first-adaptive-form-hero-image.png)

De interactieve Mededelingen centraliseert en beheert de verwezenlijking, de assemblage, en de levering van veilige, gepersonaliseerde, en interactieve correspondentie zoals bedrijfscorrespondentie, documenten, verklaringen, marketing post, rekeningen, en welkomstkits. De interactieve Mededelingen kunnen worden geleverd gebruikend twee kanalen: Druk en Web. Het kanaal van de Druk wordt gebruikt om PDF en papiermededelingen tot stand te brengen, terwijl het kanaal van het Web wordt gebruikt om online ervaringen te leveren.

Deze zelfstudie biedt een end-to-end framework voor het maken van interactieve communicatie. De zelfstudie is ingedeeld in een gebruikscase en meerdere hulplijnen. Elke gids helpt u om eigenschappen tot stand te brengen die als bouwstenen worden gebruikt om een Interactieve Communicatie tot stand te brengen.

De volgende afbeelding illustreert de bouwstenen die nodig zijn om een interactieve communicatie te maken.

![&#x200B; werkschema &#x200B;](assets/workflow.gif)

Aan het einde van deze zelfstudie kunt u het volgende doen:

* Bouwstenen maken (formuliergegevensmodel, documentfragmenten en sjablonen)
* Een interactieve communicatie maken
* Een interactieve communicatie testen en publiceren

## Hoofdletters gebruiken {#use-case}

De reis begint met het leren van het gebruiksgeval:

Een telecomoperator stuurt maandelijkse facturen naar de klanten via e-mail. De rekening is een Interactieve Communicatie. Het e-mailbericht bevat:

* Een met een wachtwoord beveiligde PDF, in deze zelfstudie wordt in dit document het kanaal Afdrukken genoemd. Het omvat klantgegevens, factureringsdetails, overzicht van kosten, geschikte wijzen van betaling van de rekening, en gebruiksdetails.
* Een koppeling naar de webversie van de factuur, in deze zelfstudie ook wel webkanaal genoemd. De webversie van de factuur biedt naast de gegevens die in de versie PDF worden vermeld, een grafische weergave van de gebruiksgegevens en persoonlijke aanbiedingen op basis van Adobe Target. De webversie bevat ook een online betalingsformulier. Het helpt om online betalingen te doen zonder het IC te verlaten.
* Een koppeling naar services met toegevoegde waarde, zoals onlineopslag, muziekabonnementen en video-abonnementen op aanvraag.

## Vereisten {#prerequisites}

* Stel een AEM auteur-instantie in.
* Installeer [&#x200B; toe:voegen-aan AEM Forms &#x200B;](/help/forms/using/installing-configuring-aem-forms-osgi.md) op auteursinstantie
* De MYSQL-database instellen
* Vraag het JAR-bestand (JDBC-databasestuurprogramma) aan bij de databaseprovider. De voorbeelden in het leerprogramma zijn gebaseerd op het gegevensbestand MySQL en gebruiken Oracle [&#x200B; MySQL JDBC gegevensbestandbestuurder &#x200B;](https://dev.mysql.com/downloads/connector/j/5.1.html).

## Stap 1: Plan de interactieve communicatie {#step-plan-the-interactive-communication}

![&#x200B; 07-apply-rules-to-adaptive-form_small &#x200B;](assets/07-apply-rules-to-adaptive-form_small.png)

De eerste stap in het plannen van een Interactieve Mededeling is de inhoud van de Interactieve Mededeling te voltooien. Nadat de inhoud wordt voltooid, moet u het analyseren om de diverse activatypes te identificeren die worden vereist om de Interactieve Mededeling tot stand te brengen.

**Doelen:**

Een anatomie maken voor de interactieve communicatie met de volgende gegevensinvoermodi:

* Statische tekst
* Formuliergegevensmodel
* Gebruikersinterface van agent
* Voorwaardelijke gegevens
* Afbeeldingen

[&#128279;](/help/forms/using/planning-interactive-communications.md)

## Stap 2: Een formuliergegevensmodel maken {#step-create-form-data-model}

![&#x200B; 03-create-adaptive-form-main-image_small &#x200B;](assets/03-create-adaptive-form-main-image_small.png)

Met een formuliergegevensmodel kunt u een interactieve communicatie verbinden met verschillende gegevensbronnen. Bijvoorbeeld AEM gebruikersprofiel, RESTful-webservices, SOAP-gebaseerde webservices, OData-services en relationele databases. Een model van vormgegevens is een verenigd schema van de gegevensvertegenwoordiging van bedrijfsentiteiten en de diensten beschikbaar in verbonden gegevensbronnen. U kunt het model van formuliergegevens met een interactieve communicatie gebruiken om gegevens op te halen uit verbonden gegevensbronnen. Voor meer informatie over het model van vormgegevens, zie [&#x200B; de Integratie van Gegevens van AEM Forms &#x200B;](/help/forms/using/data-integration.md).

**Doelen:**

* Database-instantie (MySQL-database) configureren als gegevensbron
* Maak het formuliergegevensmodel met MySQL-database als gegevensbron
* Gegevensmodelobjecten toevoegen aan formuliergegevensmodel
* Lezen- en schrijfservices configureren voor het gegevensmodel van het formulier
* Koppelingen maken tussen gegevensmodelobjecten
* Automatisch gegenereerde voorbeeldgegevens weergeven
* Voorbeeldgegevens bewerken
* Formuliergegevensmodel testen en geconfigureerde services met testgegevens

[&#128279;](/help/forms/using/create-form-data-model0.md)

## Stap 3: documentfragmenten maken {#step-create-document-fragments}

![&#x200B; 05-create-form-data-model-main_small &#x200B;](assets/05-create-form-data-model-main_small.png)

Documentfragmenten zijn herbruikbare componenten van een correspondentie die worden gebruikt om een interactieve communicatie samen te stellen. De documentfragmenten zijn van het type Tekst, Lijst en Voorwaarde.

**Doelen:**

* Documentfragmenten maken
* Variabelen maken
* Regels maken en toepassen

[&#128279;](/help/forms/using/create-document-fragments.md)

## Stap 4: Sjablonen maken {#step-create-templates}

![&#x200B; 07-apply-rules-to-adaptive-form_small &#x200B;](assets/07-apply-rules-to-adaptive-form_small.png)

Om een Interactieve Mededeling tot stand te brengen, moet u malplaatjes beschikbaar op de AEM server voor de Kanalen van de Druk en van het Web hebben.

De sjablonen voor het afdrukkanaal worden gemaakt in Adobe Forms Designer en geüpload naar de AEM server. Deze malplaatjes zijn dan beschikbaar voor gebruik terwijl het creëren van een Interactieve Mededeling.

De malplaatjes voor het kanaal van het Web worden gecreeerd in AEM. Sjabloonauteurs en -beheerders kunnen websjablonen maken, bewerken en inschakelen. Zodra gecreeerd en toegelaten, zijn deze malplaatjes beschikbaar voor gebruik terwijl het creëren van een Interactieve Communicatie.

**Doelen:**

* XDP-sjablonen maken voor het afdrukkanaal met Adobe Forms Designer
* De XDP-sjablonen uploaden naar de AEM Forms-server
* Sjablonen voor het webkanaal maken en inschakelen

[&#128279;](/help/forms/using/create-templates-print-web.md)

## Stap 5: Maak een interactieve communicatie {#step-create-an-interactive-communication}

![&#x200B; 09-stijl-uw-adaptief-vorm-klein &#x200B;](assets/09-style-your-adaptive-form-small.png)

Zodra u alle bouwstenen zoals het model van vormgegevens, documentfragmenten, en malplaatjes voor de Webversie creeert, kunt u beginnen tot een Interactieve Mededeling te leiden.

De interactieve Mededelingen kunnen door twee kanalen worden geleverd: Druk en Web. U kunt ook een interactieve communicatie maken met Afdrukkanaal als stramien. Met de optie Afdrukken als hoofdoptie voor het webkanaal wordt gegarandeerd dat de inhoud, overerving en gegevensbinding van het webkanaal worden afgeleid van het kanaal Afdrukken.

**Doelen:**

* Interactieve communicatie maken voor het afdrukkanaal
* Interactieve communicatie voor het webkanaal maken
* Interactieve communicatie voor afdrukken en web maken met Afdrukken als origineel
* Een dynamische tabel maken in de webversie van Interactieve communicatie
* Creeer een grafiek in de versie van het Web van Interactieve Communicatie
* Hyperlinks maken in de webversie van Interactieve communicatie

[&#128279;](/help/forms/using/create-interactive-communication0.md)

## Stap 6: Publish uw interactieve communicatie {#step-publish-your-interactive-communication}

![&#x200B; 12-publish-your-adaptive-form-_small &#x200B;](assets/12-publish-your-adaptive-form-_small.png)

Nadat u interactieve communicatie hebt gemaakt en getest met de kanalen Afdrukken en Web, kunt u deze elementen publiceren. Het gebruiksscenario dat in deze zelfstudie wordt beschreven, is gericht op het integreren van deze elementen met een e-mailclient. De e-mailclient fungeert als brug voor het verzenden van interactieve communicatie naar meerdere e-mailadressen.

**Doelen:**

* Integreer Interactieve Mededelingen met een e-mailcliënt om een mededeling naar de klanten te kunnen verzenden
* Een PDF-document opnemen als bijlage (interactieve communicatie gemaakt in het afdrukkanaal)
* Neem een koppeling op naar de webversie van de interactieve communicatie
