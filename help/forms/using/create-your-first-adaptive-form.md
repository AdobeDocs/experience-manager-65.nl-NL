---
title: "Zelfstudie: Uw eerste adaptieve formulier maken"
seo-title: "Tutorial: Create your first adaptive form"
description: Leer zakelijke klassen, interactieve en responsieve formulieren te maken.
seo-description: Learn to create business class, interactive, and responsive forms.
uuid: ee351a3f-ea6a-4b4c-8045-4948ad51b7c1
topic-tags: introduction
discoiquuid: 1142bcd4-e3a7-41ce-a710-132ae6c21dbe
docset: aem65
feature: Adaptive Forms
exl-id: 77a05f83-ac9a-4221-85ac-439e82623a28
source-git-commit: e9f64722ba7df0a7f43aaf1005161483e04142f5
workflow-type: tm+mt
source-wordcount: '966'
ht-degree: 0%

---

# Zelfstudie: Uw eerste adaptieve formulier maken {#tutorial-create-your-first-adaptive-form}

![01-create-first-adaptive-form-hero-image](assets/01-create-first-adaptive-form-hero-image.png)

## Inleiding {#introduction}

Bent u op zoek naar een mobiele-vriendelijke **ervaring met formulieren** die het inschrijven vereenvoudigt, de betrokkenheid verhoogt en de doorlooptijd verkort, **adaptieve formulieren** is perfect voor je. Adaptieve formulieren bieden een mobiele, automatiserings- en analysevriendelijke ervaring voor formulieren. U kunt eenvoudig formulieren maken die responsief en interactief van aard zijn, geautomatiseerde processen gebruiken om beheertaken en repetitieve taken te beperken en gegevensanalyses gebruiken om de ervaring die klanten met uw formulieren hebben, te verbeteren en aan te passen.

Deze zelfstudie biedt een end-to-end framework voor het maken van een adaptief formulier. De zelfstudie is ingedeeld in een gebruikscase en meerdere hulplijnen. Met elke handleiding kunt u nieuwe functies toevoegen aan het aangepaste formulier dat in deze zelfstudie wordt gemaakt. U hebt een werkend adaptief formulier na elke hulplijn. De handleiding voor het maken van een adaptief formulier is beschikbaar. Volgende hulplijnen zijn binnenkort beschikbaar. Aan het einde van deze zelfstudie kunt u het volgende doen:

* Maak een adaptief formulier- en formuliergegevensmodel.
* Stijl uw adaptieve formulier.
* Gebruik de adaptieve redacteur van de vormregel om bedrijfsregels te bouwen.
* Test en publiceer een adaptief formulier.

![create-adaptive-form-workflow](assets/create-daptive-form-workflow.png)

De reis begint met het leren van het gebruiksgeval:

Een website biedt een reeks producten aan voor verschillende klanten. Klanten bladeren door de portal, selecteren en bestellen de producten. Elke klant maakt een account en geeft verzendadres en factuuradres. Een bestaande klant, Sara Rose, probeert haar verzendadres toe te voegen aan de website. De website bevat een onlineformulier voor het toevoegen en bijwerken van verzendadressen.

De website wordt uitgevoerd op Adobe Experience Manager (AEM) en gebruikt AEM [!DNL Forms] voor het vastleggen en verwerken van gegevens. Het formulier voor het toevoegen en bijwerken van adressen is een adaptief formulier. De website slaat klantgegevens in een database op. Zij gebruiken de adrestoevoeging en werken vorm bij om beschikbare adressen terug te winnen en te tonen. Ze gebruiken ook het aangepaste formulier om bijgewerkte en nieuwe adressen te accepteren.

### Vereiste {#prerequisite}

* Een [AEM](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html#author-and-publish-installs)
* Installeren [AEM Forms-invoegtoepassing](../../forms/using/installing-configuring-aem-forms-osgi.md) op auteurinstantie.
* Vraag het JAR-bestand (JDBC-databasestuurprogramma) aan bij de databaseprovider. Voorbeelden in de zelfstudie zijn gebaseerd op [!DNL MySQL] database en gebruik [!DNL Oracle's] [MySQL JDBC-databasestuurprogramma](https://dev.mysql.com/downloads/connector/j/5.1.html).

* Stel een database in die klantgegevens bevat met de onderstaande velden. Een database is niet essentieel om een adaptief formulier te maken. Deze zelfstudie gebruikt een database om het formuliergegevensmodel en de persistentiemogelijkheden van AEM weer te geven [!DNL Forms].

![adaptiveformdata](assets/adaptiveformdata.png)

## Stap 1: Een adaptief formulier maken {#step-create-an-adaptive-form}

![03-create-adaptive-form-main-image_small](assets/03-create-adaptive-form-main-image_small.png)

Adaptieve formulieren zijn nieuwe generatie, boeiend, responsief, dynamisch en adaptief van aard. Met behulp van adaptieve formulieren kunt u persoonlijke en doelgerichte ervaringen bieden. AEM [!DNL Forms] voorzien een belemmering-en-dalings redacteur WYSIWYG om adaptieve vormen tot stand te brengen. Zie voor meer informatie over adaptieve formulieren [Inleiding tot het ontwerpen van adaptieve formulieren](../../forms/using/introduction-forms-authoring.md).

Doelstellingen:

* Een adaptief formulier maken waarmee een klant een verzendadres kan toevoegen
* Indelingsvelden van een adaptief formulier voor het weergeven en accepteren van informatie van een klant
* Verzendactie maken om een e-mail met formulierinhoud te verzenden
* Een adaptief formulier voorvertonen en verzenden

[![Zie de Guide](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](create-adaptive-form.md)

## Stap 2: Formuliergegevensmodel maken {#step-create-form-data-model}

![05-create-form-data-model-main_small](assets/05-create-form-data-model-main_small.png)

Met een formuliergegevensmodel kunt u een adaptief formulier aansluiten op verschillende gegevensbronnen. Bijvoorbeeld AEM gebruikersprofiel, RESTful Webdiensten, op SOAP-Gebaseerde Webdiensten, OData diensten, en relationele gegevensbestanden. Een gegevensmodel van de Vorm is een verenigd schema van de gegevensvertegenwoordiging van bedrijfsentiteiten en de diensten beschikbaar in verbonden gegevensbronnen. U kunt het formuliergegevensmodel met een adaptief formulier gebruiken om gegevens op te halen, bij te werken, te verwijderen en aan verbonden gegevensbronnen toe te voegen.

Doelstellingen:

* De database-instantie van de website configureren ([!DNL MySQL] database) als gegevensbronnen
* Het formuliergegevensmodel maken met [!DNL MySQL] database als gegevensbron
* Gegevensmodelobjecten toevoegen aan formuliergegevensmodel
* Lezen- en schrijfservices configureren voor het gegevensmodel van het formulier
* Formuliergegevensmodel testen en geconfigureerde services met testgegevens

[![Zie de Guide](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](create-form-data-model.md)

## Stap 3: Regels toepassen op aangepaste formuliervelden {#step-apply-rules-to-adaptive-form-fields}

![07-apply-rules-to-adaptive-form_small](assets/07-apply-rules-to-adaptive-form_small.png)

Met adaptieve formulieren kunt u in een editor regels schrijven voor adaptieve formulierobjecten. Met deze regels worden acties gedefinieerd die op formulierobjecten worden geactiveerd op basis van vooraf ingestelde voorwaarden, gebruikersinvoer en gebruikersacties op het formulier. Hierdoor wordt de nauwkeurigheid en snelheid van het invullen van formulieren gegarandeerd.

Doelstellingen:

* Regels maken en toepassen op adaptieve formuliervelden
* Regels gebruiken om services voor formuliergegevensmodellen te activeren voor het bijwerken van gegevens naar een database

[![Zie de Guide](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](apply-rules-to-adaptive-form-fields.md)

## Stap 4: Stijl uw adaptieve formulier {#step-style-your-adaptive-form}

![adaptieve vormgeving](/help/forms/using/assets/09-style-your-adaptive-form-small.png)

Adaptieve formulieren bieden thema&#39;s en een [editor](../../forms/using/themes.md) om thema&#39;s voor de adaptieve formulieren te maken. Een thema bevat opmaakgegevens voor componenten en deelvensters en u kunt een thema in verschillende formulieren opnieuw gebruiken. Stijlen omvatten eigenschappen zoals achtergrondkleuren, statuskleuren, transparantie, uitlijning en grootte. Wanneer u het thema toepast op het formulier, weerspiegelt de opgegeven stijl de overeenkomstige componenten van het formulier. Adaptieve formulieren ondersteunen ook inline opmaak voor stijlen die specifiek zijn voor een formulier.

Doelstellingen:

* Een thema uit het vak toepassen op een adaptief formulier
* Een thema maken voor een adaptief formulier met de themaeditor
* Weblettertypen gebruiken in een aangepast thema

[![Zie de Guide](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](style-your-adaptive-form.md)

## Stap 5: Het aangepaste formulier publiceren {#step-publish-your-adaptive-form}

![12-publish-your-adaptive-form-_small](assets/12-publish-your-adaptive-form-_small.png)

U kunt adaptieve formulieren publiceren als een zelfstandig formulier (toepassing van één pagina), inclusief in AEM [Sites-pagina](/help/forms/using/embed-adaptive-form-aem-sites.md)of op een AEM [!DNL Site] gebruiken [Forms Portal](../../forms/using/introduction-publishing-forms.md).

Doelstellingen:

* Het adaptieve formulier publiceren als een AEM
* Het adaptieve formulier insluiten in een AEM [!DNL Sites] Pagina
* Het adaptieve formulier insluiten in een externe webpagina (een niet-AEM webpagina die buiten AEM wordt gehost)

[![Zie de Guide](https://helpx.adobe.com/content/dam/help/en/marketing-cloud/how-to/digital-foundation/_jcr_content/main-pars/image_1250343773/see-the-guide-sm.png)](publish-your-adaptive-form.md)
