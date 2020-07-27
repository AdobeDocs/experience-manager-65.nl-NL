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
source-git-commit: eb5317be52eec39b947ccb3c456d21d567ef2841
workflow-type: tm+mt
source-wordcount: '826'
ht-degree: 0%

---


# Berichten configureren {#configure-messaging}

## Overzicht {#overview}

De overseineneigenschap voor AEM Communities biedt de capaciteit voor ondertekende plaatsbezoekers (leden) om berichten naar elkaar te verzenden die wanneer ondertekend op de plaats toegankelijk zijn.

Het overseinen wordt toegelaten voor een communautaire plaats door een doos tijdens de verwezenlijking [van de](/help/communities/sites-console.md)communautaire plaats te controleren.

Deze pagina bevat informatie over de standaardconfiguratie en mogelijke aanpassingen.

Voor extra informatie voor ontwikkelaars, zie de Hoofdzaak van het [Overseinen](/help/communities/essentials-messaging.md).

## Service voor berichtenverkeer {#messaging-operations-service}

De configuratie [AEM Communities de Dienst](https://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) van de Verrichtingen van het Overseinen identificeert het eindpunt dat overseinen verwante verzoeken behandelt, de omslagen de dienst voor het opslaan van berichten zou moeten gebruiken, en als de berichten dossiergehechtheid kunnen omvatten, welke dossiertypes worden toegestaan.

Voor communautaire plaatsen die gebruikend de `Communities Sites console`, een geval van de dienst worden gecreeerd bestaat reeds, met inbox die aan wordt geplaatst `/mail/inbox`.

### Community Messaging Operations Service {#community-messaging-operations-service}

Zoals hieronder getoond, bestaat een configuratie van de dienst voor plaatsen die met de tovenaar [van de](/help/communities/sites-console.md)plaatsverwezenlijking worden gecreeerd. U kunt de configuratie weergeven of bewerken door het potloodpictogram naast de configuratie te selecteren.

![berichtenverkeer](assets/messaging-operations.png)

### Nieuwe configuratie toevoegen {#add-new-configuration}

Als u een nieuwe configuratie wilt toevoegen, selecteert u het plusteken &#39;**+**&#39; naast de naam van de service:

* **Lijst van gewenste personen Berichtvelden**

   Hiermee geeft u de eigenschappen op van de component Bericht samenstellen die gebruikers kunnen bewerken en behouden. Als nieuwe formulierelementen worden toegevoegd, moet de element-id desgewenst worden toegevoegd om te worden opgeslagen in SRP. Standaard zijn dit twee items: *onderwerp* en *inhoud*.

* **Maximale grootte berichtvenster**

   Het maximum aantal bytes in het berichtvenster van elke gebruiker. De standaardwaarde is *1073741824* (1 GB).

* **Limiet voor aantal berichten**

   Het totale aantal toegestane berichten per gebruiker. De waarde -1 geeft aan dat een onbeperkt aantal berichten is toegestaan, afhankelijk van de groottelimiet van het berichtvenster. De standaardwaarde is *10000* (10 kB).

* **Leveringsfout melden**

   Als deze optie is ingeschakeld, stuurt u een melding naar de afzender als de berichtlevering bij sommige ontvangers mislukt. Standaard is *ingeschakeld*.

* **Leverancier-id mislukt**

   Naam van afzender die in ontbroken bericht verschijnt levering. De standaardwaarde is *failureNotifier*.

* **Sjabloonpad voor mislukte berichten**

   Absolute weg aan de levering ontbrak de wortel van het berichtmalplaatje. De standaardwaarde is */etc/notification/messaging/default*.

* **Aantal pogingen**

   Aantal keren dat het opnieuw verzenden van een bericht moet worden uitgevoerd. De standaardwaarde is *3*.

* **Wacht tussen opnieuw proberen**

   Aantal seconden te wachten tussen pogingen om bericht op gebrek opnieuw te verzenden. De standaardwaarde is *100* (seconden).

* **Grootte van updatepool tellen**

   Aantal gezamenlijke draden die voor tellerupdate worden gebruikt. De standaardwaarde is *10*.

* **Pad in vak**

   (*Vereist*) Het pad, relatief ten opzichte van het knooppunt van de gebruiker (/home/users/*gebruikersnaam*), dat moet worden gebruikt voor de `inbox` map. Het pad mag NIET eindigen met een slash &#39;/&#39; achter het pad. Standaard is dit */e-mail/inbox*.

* **Pad naar verzonden items**

   (*Vereist*) Het pad, relatief ten opzichte van het knooppunt van de gebruiker (/home/users/*gebruikersnaam*), dat moet worden gebruikt voor de `sent items` map. Het pad mag NIET eindigen met een slash &#39;/&#39; achter het pad. Standaard is dit */e-mail/sentimenten* .

* **Ondersteuningsbijlagen**

   Als deze optie is ingeschakeld, kunnen gebruikers bijlagen toevoegen aan hun berichten. Standaard is *ingeschakeld*.

* **Groepsberichten inschakelen**

   Als deze optie is geselecteerd, kunnen geregistreerde gebruikers bulkberichten naar een groep leden verzenden. Standaard is *uitgeschakeld*.

* **Maximum aantal. van de totale begunstigden**

   Als het groepsoverseinen wordt toegelaten, specificeer het maximumaantal ontvangers waarnaar het groepsbericht tegelijkertijd kan worden verzonden. De standaardwaarde is *100*.

* **Batchgrootte**

   Aantal berichten aan partij samen voor verzenden wanneer het verzenden naar een grote groep ontvangers. De standaardwaarde is *100*.

* **Totale grootte van bijlage**

   Als supportAttachments wordt gecontroleerd, specificeert deze waarde de maximum toegestane totale grootte (in bytes) van alle gehechtheid. De standaardwaarde is *104857600* (100 MB).

* **lijst van afgewezen personen bijlagetype**

   Een lijst van afgewezen personen met bestandsextensies, voorafgegaan door &#39;**.**&quot;, dat zal door het systeem worden verworpen. Als de extensie niet is op de lijst met ongewenste personen gestaan, is deze toegestaan. Extensies kunnen worden toegevoegd of verwijderd met de pictogrammen &#39;**+**&#39; en &#39;**-**&#39;.

* **Toegestane typen bijlagen**

   **(*Actie vereist*)** Een lijst van gewenste personen van filename uitbreidingen, het tegenovergestelde van de lijst van afgewezen personen. Als u alle bestandsextensies wilt toestaan, behalve de extensies die zijn op de lijst met ongewenste personen gestaan, gebruikt u het pictogram &#39;**-**&#39; om één leeg item te verwijderen.

* **Servicekiezer**

   (*Vereist*) een absolute weg (eindpunt) waardoor de dienst (een virtueel middel) wordt geroepen. De wortel van de gekozen weg moet één inbegrepen in de configuratie van de Wegen *van de* Uitvoering van OSGi config [ , zoals `Apache Sling Servlet/Script Resolver and Error Handler`](https://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), `/bin/`, en `/apps/``/services/`zijn. Om deze configuratie voor het overseineneigenschap van een plaats te selecteren, wordt dit eindpunt verstrekt als **`Service selector`** waarde voor `Message List and Compose Message components` (zie de Eigenschap [van het](/help/communities/configure-messaging.md)Bericht).

   De standaardwaarde is */bin/messaging* .

* **Lijst van gewenste personen veld**

   De Lijst van gewenste personen **van de Gebieden van het** Bericht van het gebruik.

>[!CAUTION]
>
>Telkens wanneer een `Messaging Operations Service` configuratie voor uitgeven wordt geopend, als `allowedAttachmentTypes.name` was verwijderd, wordt een lege ingang opnieuw toegevoegd om het bezit configureerbaar te maken. Bij één leeg item worden bestandsbijlagen uitgeschakeld.
>
>Als u alle bestandsextensies wilt toestaan, behalve de extensies die zijn op de lijst met ongewenste personen gestaan, gebruikt u het pictogram &#39;**-**&#39; om (opnieuw) de lege invoer te verwijderen voordat u op **Opslaan** klikt.


## Groepsberichten {#group-messaging}

Om geregistreerde gebruikers toe te staan om directe berichten in bulk naar gebruikersgroepen te verzenden, zorg ervoor om groepsoverseinen **in de volgende twee instanties van de configuratie van de Diensten** van de Verrichting van het **Overseinen toe te** laten:

* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-console`
* `com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-messaging`

**Service voor berichtenverkeer: sociale console**

![social-console-op-service](assets/social-console-op-service.png)

**Service voor berichtenverkeer: sociale berichten**

![social-message-op-service](assets/social-message-op-service.png)

## Problemen oplossen {#troubleshooting}

Één manier om problemen op te lossen is het toelaten van [het zuiveren berichten in het logboek.](/help/sites-administering/troubleshooting.md)

Zie ook [Loggers en Schrijvers voor de Individuele Diensten](/help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Het te controleren pakket is `com.adobe.cq.social.messaging`.
