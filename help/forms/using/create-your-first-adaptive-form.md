---
title: 'Lesbestand: uw eerste adaptieve formulier maken'
description: Leer zakelijke klassen, interactieve en responsieve formulieren te maken.
topic-tags: introduction
docset: aem65
feature: Adaptive Forms
exl-id: 77a05f83-ac9a-4221-85ac-439e82623a28
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f941782f9a4201e7bff898853d3fc18954418500
workflow-type: tm+mt
source-wordcount: '908'
ht-degree: 0%

---

# Lesbestand: uw eerste adaptieve formulier maken {#tutorial-create-your-first-adaptive-form}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/creating-adaptive-form.html) |
| AEM 6,5 | Dit artikel |


![ 01-creeer-eerste-adaptief-vorm-held-beeld ](assets/01-create-first-adaptive-form-hero-image.png)

## Inleiding {#introduction}

Bent u op zoek naar een mobiel-vriendschappelijke **vormervaring** die inschrijving vereenvoudigt, overeenkomst verhoogt, en turnaround tijd vermindert, **adaptieve vormen** is perfect geschikt voor u. Adaptieve formulieren bieden een mobiele, automatiserings- en analysevriendelijke ervaring voor formulieren. U kunt eenvoudig formulieren maken die responsief en interactief van aard zijn, geautomatiseerde processen gebruiken om beheertaken en repetitieve taken te beperken en gegevensanalyses gebruiken om de ervaring die klanten met uw formulieren hebben, te verbeteren en aan te passen.

Deze zelfstudie biedt een end-to-end framework voor het maken van een adaptief formulier. De zelfstudie is ingedeeld in een gebruikscase en meerdere hulplijnen. Met elke handleiding kunt u nieuwe functies toevoegen aan het aangepaste formulier dat in deze zelfstudie wordt gemaakt. U hebt een werkend adaptief formulier na elke hulplijn. De handleiding voor het maken van een adaptief formulier is beschikbaar. Volgende hulplijnen komen binnenkort. Aan het einde van deze zelfstudie moet u het volgende kunnen doen:

* Maak een adaptief formulier- en formuliergegevensmodel.
* Stijl uw adaptieve formulier.
* Gebruik de adaptieve redacteur van de vormregel om bedrijfsregels te bouwen.
* Test en publiceer een adaptief formulier.

![ creeer-adaptief-vorm-werkschema ](assets/create-daptive-form-workflow.png)

De reis begint met het leren van het gebruiksgeval:

Een website biedt een reeks producten aan voor verschillende klanten. Klanten bladeren door de portal, selecteren en bestellen de producten. Elke klant maakt een account en geeft verzendadres en factuuradres. Een bestaande klant, Sara Rose, probeert haar verzendadres toe te voegen aan de website. De website bevat een onlineformulier voor het toevoegen en bijwerken van verzendadressen.

De website wordt uitgevoerd op Adobe Experience Manager (AEM) en gebruikt AEM [!DNL Forms] voor het vastleggen en verwerken van gegevens. Het formulier voor het toevoegen en bijwerken van adressen is een adaptief formulier. De website slaat klantgegevens in een database op. Zij gebruiken de adrestoevoeging en werken vorm bij om beschikbare adressen terug te winnen en te tonen. Ze gebruiken ook het aangepaste formulier om bijgewerkte en nieuwe adressen te accepteren.

### Vereiste {#prerequisite}

* Opstelling een [ AEM auteursinstantie ](https://experienceleague.adobe.com/docs/experience-manager-65/content/implementing/deploying/deploying/deploy.html#author-and-publish-installs)
* Installeer [ toe:voegen-on van AEM Forms ](../../forms/using/installing-configuring-aem-forms-osgi.md) op auteursinstantie.
* Vraag het JAR-bestand (JDBC-databasestuurprogramma) aan bij de databaseprovider. De voorbeelden in het leerprogramma zijn gebaseerd op [!DNL MySQL] gegevensbestand en gebruiken [!DNL Oracle's] [ MySQL JDBC gegevensbestandbestuurder ](https://dev.mysql.com/downloads/connector/j/5.1.html).

* Stel een database in die klantgegevens bevat met de onderstaande velden. Een database is niet essentieel om een adaptief formulier te maken. Deze zelfstudie gebruikt een database om het gegevensmodel van het formulier en de persistentiemogelijkheden van AEM [!DNL Forms] weer te geven.

![ adaptiveformdata ](assets/adaptiveformdata.png)

## Stap 1: Een adaptief formulier maken {#step-create-an-adaptive-form}

![ 03-create-adaptive-form-main-image_small ](assets/03-create-adaptive-form-main-image_small.png)

Adaptieve formulieren zijn nieuwe generatie, boeiend, responsief, dynamisch en adaptief van aard. Met behulp van adaptieve formulieren kunt u persoonlijke en doelgerichte ervaringen bieden. AEM [!DNL Forms] beschikt over een WYSIWYG-editor voor slepen en neerzetten waarmee u adaptieve formulieren kunt maken. Voor meer informatie over adaptieve vormen, zie [ Inleiding aan auteursadaptieve vormen ](../../forms/using/introduction-forms-authoring.md).

Doelstellingen:

* Maak een adaptief formulier waarmee een klant een verzendadres kan toevoegen.
* Indelingsvelden van een adaptief formulier voor het weergeven en accepteren van informatie van een klant.
* Verzendactie maken om een e-mail met formulierinhoud te verzenden.
* Een voorbeeld bekijken en een adaptief formulier verzenden.

[![ zie de Gids ](assets/see-the-guide-sm.png)](create-adaptive-form.md)

## Stap 2: Formuliergegevensmodel maken {#step-create-form-data-model}

![ 05-create-form-data-model-main_small ](assets/05-create-form-data-model-main_small.png)

Met een formuliergegevensmodel kunt u een adaptief formulier aansluiten op verschillende gegevensbronnen. Bijvoorbeeld AEM gebruikersprofiel, RESTful-webservices, SOAP-gebaseerde webservices, OData-services en relationele databases. Een gegevensmodel van de Vorm is een verenigd schema van de gegevensvertegenwoordiging van bedrijfsentiteiten en de diensten beschikbaar in verbonden gegevensbronnen. U kunt het formuliergegevensmodel met een adaptief formulier gebruiken om gegevens op te halen, bij te werken, te verwijderen en aan verbonden gegevensbronnen toe te voegen.

Doelstellingen:

* Configureer de database-instantie van de website ([!DNL MySQL] database) als gegevensbron.
* Maak het formuliergegevensmodel met behulp van [!DNL MySQL] -database als gegevensbron.
* Voeg gegevensmodelvoorwerpen toe zodat kunt u het gegevensmodel vormen.
* Configureer lees- en schrijfservices voor het model met formuliergegevens.
* Het model van vormgegevens en de gevormde diensten van de test met testgegevens.

[![ zie de Gids ](assets/see-the-guide-sm.png)](create-form-data-model.md)

## Stap 3: Regels toepassen op adaptieve formuliervelden {#step-apply-rules-to-adaptive-form-fields}

![ 07-apply-rules-to-adaptive-form_small ](assets/07-apply-rules-to-adaptive-form_small.png)

Met adaptieve formulieren kunt u in een editor regels schrijven voor adaptieve formulierobjecten. Met deze regels worden acties gedefinieerd die op formulierobjecten worden geactiveerd op basis van vooraf ingestelde voorwaarden, gebruikersinvoer en gebruikersacties op het formulier. Hierdoor wordt de nauwkeurigheid en snelheid van het invullen van formulieren gegarandeerd.

Doelstellingen:

* Maak regels en pas deze toe op adaptieve formuliervelden.
* Gebruik regels om services van het formuliergegevensmodel te activeren om de gegevens bij te werken naar de database.

[![ zie de Gids ](assets/see-the-guide-sm.png)](apply-rules-to-adaptive-form-fields.md)

## Stap 4: Stijl uw adaptieve formulier {#step-style-your-adaptive-form}

![ adapative-form-styling ](/help/forms/using/assets/09-style-your-adaptive-form-small.png)

De adaptieve vormen verstrekken thema&#39;s en een [ redacteur ](../../forms/using/themes.md) om thema&#39;s voor de adaptieve vormen tot stand te brengen. Een thema bevat opmaakgegevens voor componenten en deelvensters en u kunt een thema in verschillende formulieren opnieuw gebruiken. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u het thema toepast op het formulier, weerspiegelt de opgegeven stijl de overeenkomstige componenten van het formulier. Adaptieve formulieren ondersteunen ook inline opmaak voor stijlen die specifiek zijn voor een formulier.

Doelstellingen:

* Pas een uitwendig thema toe op een adaptief formulier.
* Maak een thema voor een adaptief formulier met de themaeditor.
* Gebruik Webben Fonts in een aangepast thema.

[![ zie de Gids ](assets/see-the-guide-sm.png)](style-your-adaptive-form.md)

## Stap 5: Publish uw adaptieve formulier {#step-publish-your-adaptive-form}

![ 12-publish-your-adaptive-form-_small ](assets/12-publish-your-adaptive-form-_small.png)

U kunt adaptieve vormen als stand-alone vorm (enige paginatoepassing) publiceren, in AEM [ pagina van Plaatsen ](/help/forms/using/embed-adaptive-form-aem-sites.md) omvatten, of lijst op een AEM [!DNL Site] gebruikend [ Portaal van Forms ](../../forms/using/introduction-publishing-forms.md).

Doelstellingen:

* Publish het adaptieve formulier als een AEM pagina.
* Sluit het adaptieve formulier in een AEM [!DNL Sites] pagina in.
* Sluit het adaptieve formulier in een externe webpagina in (een niet-AEM webpagina die buiten AEM wordt gehost).

[![ zie de Gids ](assets/see-the-guide-sm.png)](publish-your-adaptive-form.md)
