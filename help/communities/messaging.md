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
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Berichten configureren{#configure-messaging}

## Overzicht {#overview}

De berichtenfunctie voor AEM Communities biedt de mogelijkheid voor ingetekende sitebezoekers (leden) om berichten naar elkaar te verzenden die toegankelijk zijn wanneer ze zich op de site hebben aangemeld.

Het overseinen wordt toegelaten voor een communautaire plaats door een doos tijdens de verwezenlijking [van de](/help/communities/sites-console.md)communautaire plaats te controleren.

Deze pagina bevat informatie over de standaardconfiguratie en mogelijke aanpassingen.

Voor extra informatie voor ontwikkelaars, zie de Hoofdzaak van het [Overseinen](/help/communities/essentials-messaging.md).

## Service voor berichtenverkeer {#messaging-operations-service}

De configuratie [AEM de Dienst](https://localhost:4502/system/console/configMgr/com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl) van de Verrichtingen van het Overseinen van Gemeenschappen identificeert het eindpunt dat overseinen verwante verzoeken behandelt, de omslagen de dienst voor het opslaan van berichten zou moeten gebruiken, en als de berichten dossiergehechtheid kunnen omvatten, welke dossiertypes worden toegestaan.

Voor communautaire plaatsen die gebruikend de `Communities Sites console`, een geval van de dienst worden gecreeerd bestaat reeds, met inbox die aan `/mail/inbox`. wordt geplaatst.

### Community Messaging Operations Service {#community-messaging-operations-service}

Zoals hieronder getoond, bestaat een configuratie van de dienst voor plaatsen die met de tovenaar [van de](/help/communities/sites-console.md)plaatsverwezenlijking worden gecreeerd. U kunt de configuratie weergeven of bewerken door het potloodpictogram naast de configuratie te selecteren.

![berichtenverkeer](assets/messaging-operations.png)

### Nieuwe configuratie toevoegen {#add-new-configuration}

Als u een nieuwe configuratie wilt toevoegen, selecteert u het plusteken &#39;**+**&#39; naast de naam van de service:

* **Whitelist van de Gebieden van het bericht** specificeert de eigenschappen van de samenstellen de componentengebruikers van het Bericht kunnen uitgeven en voortzetten. Als nieuwe formulierelementen worden toegevoegd, moet de element-id desgewenst worden toegevoegd om te worden opgeslagen in SRP. Standaard zijn dit twee items: *onderwerp* en *inhoud*.

* **Grootte van berichtvenster is beperkt** Het maximum aantal bytes in het berichtvenster van elke gebruiker. De standaardwaarde is *1073741824 *(1 GB).

* **Limiet** voor aantal berichten Het totale aantal berichten dat per gebruiker is toegestaan. De waarde -1 geeft aan dat een onbeperkt aantal berichten is toegestaan, afhankelijk van de groottelimiet van het berichtvenster. De standaardwaarde is *10000* (10 kB).

* **De leveringsmislukking** van het berichtIndien gecontroleerd, bericht afzender als de berichtlevering aan sommige ontvangers ontbreekt. Standaard is *ingeschakeld*.

* **Identiteitskaart** Naam van afzender van mislukte levering die in levering ontbroken bericht verschijnt. De standaardwaarde is *failureNotifier*.

* **Het weg van het berichtmalplaatje** van de mislukking Absolute weg aan de levering ontbrak de wortel van het berichtmalplaatje. De standaardwaarde is */etc/notification/messaging/default*.

* **Geen pogingen opnieuw** Aantal keren om opnieuw te proberen bericht dat niet kan worden geleverd. De standaardwaarde is *3*.

* **Wacht tussen opnieuw probeert** Aantal seconden om tussen pogingen te wachten om bericht op mislukking opnieuw te verzenden. De standaardwaarde is *100 *(seconden).

* **De grootte** van de de updatepool van de telling Aantal gezamenlijke draden die voor tellerupdate worden gebruikt. De standaardwaarde is *10*.

* **Inbox path**(*Required*) The path, relative to the user&#39;s node (/home/users/*username*), to use for the **`inbox`** folder. Het pad mag NIET eindigen met een slash &#39;/&#39; achter het pad. Standaard is dit */e-mail/inbox.*

* **Pad** naar verzonden items (*vereist*) Het pad ten opzichte van het knooppunt van de gebruiker (/home/users/*gebruikersnaam*) dat moet worden gebruikt voor de **`send items`** map. Het pad mag NIET eindigen met een slash &#39;/&#39; achter het pad. Standaard is dit */e-mail/sentimenten* .

* **Ondersteuningsbijlagen** Als deze optie is ingeschakeld, kunnen gebruikers bijlagen toevoegen aan hun berichten. Standaard is *ingeschakeld*.

* **Schakel het groepsbericht** in als deze optie is geselecteerd, kunnen geregistreerde gebruikers bulkberichten naar een groep leden verzenden. Standaard is *uitgeschakeld*.

* **Maximum aantal. van totale ontvangers** Als het groepsoverseinen wordt toegelaten, specificeer het maximumaantal ontvangers waarnaar het groepsbericht in een tijd kan worden verzonden. De standaardwaarde is *100*.

* **De grootte** van de partijAantal berichten om samen voor te slaan verzendt wanneer het verzenden naar een grote groep ontvangers. De standaardwaarde is *100*.

* **Totale grootte** van bijlage als supportAttachments wordt gecontroleerd, specificeert deze waarde de maximum toegestane totale grootte (in bytes) van alle gehechtheid. De standaardwaarde is *104857600* (100 MB).

* **zwarte lijst** Een zwarte lijst met bestandsextensies, vooraf ingesteld op &#39;**.**&quot;, dat zal door het systeem worden verworpen. Als de extensie niet op de zwarte lijst staat, is deze toegestaan. Extensies kunnen worden toegevoegd of verwijderd met de pictogrammen &#39;**+**&#39; en &#39;**-**&#39;.

* **Toegestane typen bijlagen**
   **(*Actie vereist*)** Een whitelist van bestandsextensies, het tegenovergestelde van de zwarte lijst. Als u alle bestandsextensies wilt toestaan, behalve extensies die op de zwarte lijst staan, gebruikt u het pictogram &#39;**-**&#39; om één leeg item te verwijderen.

* **De selecteur** van de dienst (*Vereist*) een absolute weg (eindpunt) waardoor de dienst (een virtueel middel) wordt geroepen. De wortel van de gekozen weg moet één inbegrepen in de configuratie van de Wegen *van de* Uitvoering van OSGi config [ , zoals `Apache Sling Servlet/Script Resolver and Error Handler`](https://localhost:4502/system/console/configMgr/org.apache.sling.servlets.resolver.SlingServletResolver), `/bin/`, en `/apps/``/services/`zijn. Om deze configuratie voor het overseineneigenschap van een plaats te selecteren, wordt dit eindpunt verstrekt als **`Service selector`** waarde voor `Message List and Compose Message components` (zie de Eigenschap [van het](/help/communities/configure-messaging.md)Bericht).
De standaardwaarde is */bin/messaging* .

* **whitelist van veld** Gebruik whitelist van **berichtvelden**.

>[!CAUTION]
>
>Telkens wanneer een `Messaging Operations Service` configuratie voor uitgeven wordt geopend, als `allowedAttachmentTypes.name` was verwijderd, wordt een lege ingang opnieuw toegevoegd om het bezit configureerbaar te maken. Bij één leeg item worden bestandsbijlagen uitgeschakeld.
>
>Als u alle bestandsextensies wilt toestaan, met uitzondering van extensies die op de zwarte lijst staan, gebruikt u het pictogram &#39;**-**&#39; om (opnieuw) één leeg item te verwijderen voordat u op **Opslaan** klikt.

## Groepsberichten {#group-messaging}

Om geregistreerde gebruikers toe te staan om directe berichten in bulk naar gebruikersgroepen te verzenden, zorg ervoor om **groepsoverseinen **in de volgende twee instanties van de configuratie van de Diensten **van de Verrichting van het** Overseinen toe te laten:

* com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-console
* com.adobe.cq.social.messaging.client.endpoints.impl.MessagingOperationsServiceImpl~social-messaging

**Service voor berichtenverkeer: sociale console**

![social-console-op-service](assets/social-console-op-service.png)

**Service voor berichtenverkeer: sociale berichten**

![social-message-op-service](assets/social-message-op-service.png)

## Problemen oplossen {#troubleshooting}

Één manier om problemen op te lossen is het toelaten van [het zuiveren berichten in het logboek.](/help/sites-administering/troubleshooting.md)

Zie ook [Loggers en Schrijvers voor de Individuele Diensten](/help/sites-deploying/configure-logging.md#loggers-and-writers-for-individual-services).

Het te controleren pakket is `com.adobe.cq.social.messaging`.
