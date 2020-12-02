---
title: Berichten configureren
seo-title: Berichten configureren
description: Communityberichten
seo-description: Communityberichten
uuid: 159dcf9d-7948-4a3d-9f51-a5b4d03e172b
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
discoiquuid: 232a0ec1-8dfc-41ec-84cc-69f9db494ea0
docset: aem65
translation-type: tm+mt
source-git-commit: f375b40c084ee363757b78c602091f38524b8b03
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 0%

---


# Berichten {#configure-messaging} configureren

## Overzicht {#overview}

Met de communicatiefunctie voor AEM Communities kunnen bezoekers van de aangemelde site (leden) berichten naar elkaar sturen die toegankelijk zijn wanneer ze zich op de site hebben aangemeld.

Het overseinen wordt toegelaten voor een communautaire plaats door een doos tijdens [de verwezenlijking van de communautaire plaats](/help/communities/sites-console.md) te controleren.

Deze pagina bevat informatie over de standaardconfiguratie en mogelijke aanpassingen.

Voor extra informatie voor ontwikkelaars, zie [Hoofdzaak van het Overseinen](/help/communities/essentials-messaging.md).

## Service voor berichtenverkeer {#messaging-operations-service}

De configuratie [De Dienst van de Verrichtingen van het Overseinen van AEM Communities ](https://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identificeert het eindpunt dat overseinen verwante verzoeken behandelt, de omslagen de dienst voor het opslaan van berichten zou moeten gebruiken, en als de berichten dossiergehechtheid kunnen omvatten, welke dossiertypes worden toegestaan.

Voor gemeenschapssites die zijn gemaakt met de `Communities Sites console`, bestaat al een instantie van de service, met de inbox ingesteld op `/mail/inbox`.

### Community Messaging Operations Service {#community-messaging-operations-service}

Zoals hieronder wordt weergegeven, bestaat er een configuratie van de service voor sites die zijn gemaakt met de wizard [Site maken](/help/communities/sites-console.md). U kunt de configuratie weergeven of bewerken door het potloodpictogram naast de configuratie te selecteren.

![berichtenverkeer](assets/messaging-operations.png)

### Nieuwe configuratie {#add-new-configuration} toevoegen

Als u een nieuwe configuratie wilt toevoegen, selecteert u de plusknop &#39;**+**&#39; naast de naam van de service:

* **Lijst van gewenste personen Berichtvelden**

   Hiermee geeft u de eigenschappen op van de component Bericht samenstellen die gebruikers kunnen bewerken en behouden. Als nieuwe formulierelementen worden toegevoegd, moet de element-id desgewenst worden toegevoegd om te worden opgeslagen in SRP. Standaard zijn dit twee items: *subject* en *content*.

* **Maximale grootte berichtvenster**

   Het maximum aantal bytes in het berichtvenster van elke gebruiker. De standaardwaarde is *1073741824* (1 GB).

* **Limiet voor aantal berichten**

   Het totale aantal toegestane berichten per gebruiker. De waarde -1 geeft aan dat een onbeperkt aantal berichten is toegestaan, afhankelijk van de groottelimiet van het berichtvenster. De standaardwaarde is *10000* (10k).

* **Leveringsfout melden**

   Als deze optie is ingeschakeld, stuurt u een melding naar de afzender als de berichtlevering bij sommige ontvangers mislukt. Standaard is *checked*.

* **Leverancier-id mislukt**

   Naam van afzender die in ontbroken bericht verschijnt levering. Standaard is *failureNotifier*.

* **Sjabloonpad voor mislukte berichten**

   Absolute weg aan de levering ontbrak de wortel van het berichtmalplaatje. Standaard is */etc/notification/messaging/default*.

* **Aantal pogingen**

   Aantal keren dat het opnieuw verzenden van een bericht moet worden uitgevoerd. De standaardwaarde is *3*.

* **Wacht tussen opnieuw proberen**

   Aantal seconden te wachten tussen pogingen om bericht op gebrek opnieuw te verzenden. De standaardwaarde is *100* (seconden).

* **Grootte van updatepool tellen**

   Aantal gezamenlijke draden die voor tellerupdate worden gebruikt. De standaardwaarde is *10*.

* **Pad in vak**

   (*Required*) De weg, met betrekking tot de knoop van de gebruiker (/home/users/*username*), aan gebruik voor de `inbox` omslag. Het pad mag NIET eindigen met een slash &#39;/&#39; achter het pad. Standaard is */mail/inbox*.

* **Pad naar verzonden items**

   (*Required*) De weg, met betrekking tot de knoop van de gebruiker (/home/users/*username*), aan gebruik voor de `sent items` omslag. Het pad mag NIET eindigen met een slash &#39;/&#39; achter het pad. De standaardwaarde is */mail/sentitems*.

* **Ondersteuningsbijlagen**

   Als deze optie is ingeschakeld, kunnen gebruikers bijlagen toevoegen aan hun berichten. Standaard is *checked*.

* **Groepsberichten inschakelen**

   Als deze optie is geselecteerd, kunnen geregistreerde gebruikers bulkberichten naar een groep leden verzenden. Standaard is *niet geselecteerd*.

* **Maximum aantal. van totale ontvangers**

   Als het groepsoverseinen wordt toegelaten, specificeer het maximumaantal ontvangers waarnaar het groepsbericht tegelijkertijd kan worden verzonden. De standaardwaarde is *100*.

* **Batchgrootte**

   Aantal berichten aan partij samen voor verzenden wanneer het verzenden naar een grote groep ontvangers. De standaardwaarde is *100*.

* **Totale grootte van bijlage**

   Als supportAttachments wordt gecontroleerd, specificeert deze waarde de maximum toegestane totale grootte (in bytes) van alle gehechtheid. De standaardwaarde is *104857600* (100 MB).

* **Lijst van afgewezen personen bijlagetype**

   Een lijst van afgewezen personen met bestandsextensies, vooraf ingesteld op &#39;**.**&quot;, dat zal door het systeem worden verworpen. Als de extensie niet wordt toegevoegd op lijst van gewenste personen, is deze toegestaan. Extensies kunnen worden toegevoegd of verwijderd met de pictogrammen &#39;**+**&#39; en &#39;**-**&#39;.

* **Toegestane typen bijlagen**

   **(*Actie vereist*)** Een lijst van gewenste personen van filename uitbreidingen, het tegenovergestelde van de lijst van afgewezen personen. Als u alle bestandsextensies wilt toestaan, behalve de extensies die zijn toegevoegd op lijst van gewenste personen, gebruikt u het pictogram &#39;**-**&#39; om één leeg item te verwijderen.

* **Servicekiezer**

   (*Required*) Een absolute weg (eindpunt) waardoor de dienst (een virtuele middel) wordt geroepen. De wortel van de gekozen weg moet één inbegrepen in *de configuratieplaatsen van Wegen van de Uitvoering* van OSGi config [ `Apache Sling Servlet/Script Resolver and Error Handler`](https://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), zoals `/bin/`, `/apps/`, en `/services/` zijn. Om deze configuratie voor de het overseineneigenschap van een plaats te selecteren, wordt dit eindpunt verstrekt als **`Service selector`** waarde voor `Message List and Compose Message components` (zie [Berichteigenschap](/help/communities/configure-messaging.md)).

   De standaardwaarde is */bin/messaging*.

* **Lijst van gewenste personen veld**

   Gebruik **Lijst van gewenste personen van de Gebieden van het bericht**.

>[!CAUTION]
>
>Elke keer dat een `Messaging Operations Service` configuratie voor uitgeven wordt geopend, als `allowedAttachmentTypes.name` was verwijderd, wordt een lege ingang opnieuw toegevoegd om het bezit configureerbaar te maken. Bij één leeg item worden bestandsbijlagen uitgeschakeld.
>
>Als u alle bestandsextensies wilt toestaan, behalve de extensies die zijn toegevoegd op lijst van gewenste personen, gebruikt u het pictogram &#39;**-**&#39; om (opnieuw) één leeg item te verwijderen voordat u op **Opslaan** klikt.

## Groepsberichten {#group-messaging}

Om geregistreerde gebruikers toe te staan om directe berichten in bulk naar gebruikersgroepen te verzenden, zorg ervoor om **groepsoverseinen** in de volgende twee instanties van **de Configuratie van de Bewerking van het Overseinen Services** toe te laten:

* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-console`
* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-messaging`

**Service voor berichtenverkeer: sociale console**

![social-console-op-service](assets/social-console-op-service.png)

**Service voor berichtenverkeer: sociale berichten**

![social-message-op-service](assets/social-message-op-service.png)

## Problemen oplossen {#troubleshooting}

Één manier om problemen op te lossen is [het zuiveren berichten in het logboek toe te laten.](/help/sites-administering/troubleshooting.md)

Zie ook [Loggers and Writers for Individual Services](/help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Het te controleren pakket is `com.adobe.cq.social.messaging`.
