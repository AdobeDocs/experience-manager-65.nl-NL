---
title: Berichten configureren
description: Leer hoe u in AEM Communities berichten kunt versturen met de functie voor berichten die inlogde sitebezoekers (leden) kunnen gebruiken om berichten naar elkaar te sturen.
contentOwner: Janice Kendall
products: SG_EXPERIENCEMANAGER/6.5/COMMUNITIES
topic-tags: administering
content-type: reference
docset: aem65
role: Admin
exl-id: ee94f093-fd14-49f2-9990-fbe853d924b1
solution: Experience Manager
feature: Communities
source-git-commit: 1f56c99980846400cfde8fa4e9a55e885bc2258d
workflow-type: tm+mt
source-wordcount: '840'
ht-degree: 0%

---

# Berichten configureren {#configure-messaging}

## Overzicht {#overview}

Met de communicatiefunctie voor AEM Communities kunnen bezoekers van de aangemelde site (leden) berichten naar elkaar sturen die toegankelijk zijn wanneer ze zich op de site hebben aangemeld.

Het overseinen wordt toegelaten voor een communautaire plaats door een doos tijdens [ communautaire plaatsverwezenlijking ](/help/communities/sites-console.md) te controleren.

Deze pagina bevat informatie over de standaardconfiguratie en mogelijke aanpassingen.

Voor extra informatie voor ontwikkelaars, zie {de Hoofdzaak van het 0} Overseinen ](/help/communities/essentials-messaging.md).[

## Service voor berichtenverkeer {#messaging-operations-service}

De configuratie [ Dienst van de Verrichtingen van het Overseinen van AEM Communities ](https://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) identificeert het eindpunt dat overseinen-verwante verzoeken behandelt, de omslagen de dienst voor het opslaan van berichten zou moeten gebruiken, en als de berichten dossiergehechtheid kunnen omvatten, welke dossiertypes worden toegestaan.

Voor gemeenschapssites die zijn gemaakt met de `Communities Sites console` , bestaat een instantie van de service, met de inbox ingesteld op `/mail/inbox` .

### Community Messaging Operations Service {#community-messaging-operations-service}

Zoals hieronder getoond, bestaat een configuratie van de dienst voor plaatsen die met de [ tovenaar van de plaatsverwezenlijking ](/help/communities/sites-console.md) worden gecreeerd. U kunt de configuratie weergeven of bewerken door het potloodpictogram naast de configuratie te selecteren.

![ overseinen-verrichtingen ](assets/messaging-operations.png)

### Nieuwe configuratie toevoegen {#add-new-configuration}

Om een configuratie toe te voegen, selecteer plus &quot;**+**&quot;pictogram naast de naam van de dienst:

* **Lijst van gewenste personen van de Gebieden van het Bericht**

  Hiermee geeft u de eigenschappen op van de component Bericht samenstellen die gebruikers kunnen bewerken en behouden. Als nieuwe formulierelementen worden toegevoegd, moet de element-id desgewenst worden toegevoegd om te worden opgeslagen in SRP. Het gebrek is twee ingangen: *onderwerp* en *inhoud*.

* **de grens van de het vakje van het Bericht grootte**

  Het maximum aantal bytes in het berichtvenster van elke gebruiker. Het gebrek is *1073741824* (1 GB).

* **de tellingsgrens van het Bericht**

  Het totale aantal toegestane berichten per gebruiker. De waarde -1 geeft aan dat een onbeperkt aantal berichten is toegestaan, afhankelijk van de groottelimiet van het berichtvenster. Het gebrek is *10000* (10k).

* **meldt leveringsmislukking**

  Als deze optie is ingeschakeld, stuurt u een melding naar de afzender als de berichtlevering bij sommige ontvangers mislukt. Het gebrek is *gecontroleerd*.

* **identiteitskaart van de Leveringsafzender van de Mislukking**

  Naam van afzender die in ontbroken bericht verschijnt levering. Het gebrek is *failureNotifier*.

* **de weg van het het berichtmalplaatje van de Mislukking**

  Absoluut pad naar de levering is mislukt. Het gebrek is */etc/notification/messaging/default*.

* **Geen pogingen**

  Aantal keren dat het opnieuw verzenden van een bericht moet worden uitgevoerd. Het gebrek is *3*.

* **wacht tussen opnieuw probeert**

  Aantal seconden te wachten tussen pogingen om bericht op gebrek opnieuw te verzenden. Het gebrek is *100* (seconden).

* **de grootte van de updatepool van de Telling**

  Aantal gezamenlijke draden die voor tellerupdate worden gebruikt. Het gebrek is *10*.

* **Inbox weg**

  (*Vereiste*) de weg, met betrekking tot de knoop van de gebruiker (/huis/gebruikers/*gebruikersbenaming*), om voor de `inbox` omslag te gebruiken. Het pad mag NIET eindigen met een slash &#39;/&#39; achter het pad. Het gebrek is */mail/inbox*.

* **Verzonden puntenweg**

  (*Vereiste*) de weg, met betrekking tot de knoop van de gebruiker (/huis/gebruikers/*gebruikersbenaming*), om voor de `sent items` omslag te gebruiken. Het pad mag NIET eindigen met een slash &#39;/&#39; achter het pad. De standaardwaarde is */email/sentitems* .

* **de gehechtheid van de Steun**

  Als deze optie is ingeschakeld, kunnen gebruikers bijlagen toevoegen aan hun berichten. Het gebrek is *gecontroleerd*.

* **laat groepsoverseinen** toe

  Als deze optie is geselecteerd, kunnen geregistreerde gebruikers bulkberichten naar een groep leden verzenden. Het gebrek is *gedeselecteerd*.

* **Maximum nr. van totale ontvangers**

  Als het groepsoverseinen wordt toegelaten, specificeer het maximumaantal ontvangers waarnaar het groepsbericht tegelijkertijd kan worden verzonden. Het gebrek is *100*.

* **Grootte van de Partij**

  Aantal berichten aan partij samen voor verzenden wanneer het verzenden naar een grote groep ontvangers. Het gebrek is *100*.

* **Totale gehechtheidsgrootte**

  Als supportAttachments wordt gecontroleerd, specificeert deze waarde de maximum toegestane totale grootte (in bytes) van alle gehechtheid. Het gebrek is *104857600* (100 MB).

* **lijst van gewezen personen van het type van Bijlage**

  Een lijst van gewezen personen van filename uitbreidingen, die met &quot;**vooraf wordt bepaald.**&#39;, dat wordt verworpen door het systeem. Als de extensie niet wordt gevoegd op lijst van gewenste personen, is deze toegestaan. De uitbreidingen kunnen worden toegevoegd of worden verwijderd gebruikend &quot;**+**&quot;en &quot;**-**&quot;pictogrammen.

* **Toegestane gehechtheidstypes**

  **(*Vereiste Actie*)** een lijst van gewenste personen van filename uitbreidingen, het tegenovergestelde van de lijst van gewezen personen. Om alle filename uitbreidingen toe te staan, behalve die gevoegd op lijst van gewenste personen, gebruik het &quot;**-**&quot;pictogram om de enige lege ingang te verwijderen.

* **de selecteur van de Dienst**

  (*Vereiste*) een absolute weg (eindpunt) waardoor de dienst (een virtueel middel) wordt geroepen. De wortel van de gekozen weg moet één inbegrepen zijn in de *configuratie die van de Wegen van de Uitvoering {van 0} van OSGi config [`Apache Sling Servlet/Script Resolver and Error Handler` ](https://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), zoals `/bin/`, `/apps/`, en `/services/` plaatst.* Om deze configuratie voor het overseineneigenschap van een plaats te selecteren, wordt dit eindpunt verstrekt als **`Service selector`** waarde voor `Message List and Compose Message components` (zie [ Eigenschap van het Bericht ](/help/communities/configure-messaging.md)).

  De standaardwaarde is */bin/messaging* .

* **Lijst van gewenste personen van het Gebied**

  De Lijst van gewenste personen van de Gebieden van het Bericht van het gebruik ****.

>[!CAUTION]
>
>Telkens wanneer een `Messaging Operations Service` -configuratie wordt geopend voor bewerking, als `allowedAttachmentTypes.name` was verwijderd, wordt een leeg item opnieuw gelezen om de eigenschap configureerbaar te maken. Bij één leeg item worden bestandsbijlagen uitgeschakeld.
>
>Om alle filename uitbreidingen toe te staan, behalve die gevoegde op lijst van gewenste personen, gebruik het pictogram &#39;**-**&#39; (opnieuw) om de enige lege ingang te verwijderen alvorens **te klikken sparen**.

## Groepsberichten {#group-messaging}

Om geregistreerde gebruikers toe te staan om directe berichten in bulk naar gebruikersgroepen te verzenden, zorg ervoor **groepsoverseinen** in de volgende twee instanties van **de configuratie van de Diensten van de Verrichting van het Overseinen** toelaat:

* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-console`
* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-messaging`

**Dienst van de Verrichtingen van het Overseinen: sociale console**

![ sociaal-console-op-dienst ](assets/social-console-op-service.png)

**Dienst van de Verrichtingen van het Overseinen: sociaal overseinen**

![ sociaal-bericht-op-dienst ](assets/social-message-op-service.png)

## Problemen oplossen {#troubleshooting}

Één manier om problemen op te lossen is [ het zuiveren berichten in het logboek toe te laten.](/help/sites-administering/troubleshooting.md)

Zie ook [ Loggers en Schrijvers voor de Individuele Diensten ](/help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Het te controleren pakket is `com.adobe.cq.social.messaging`.
