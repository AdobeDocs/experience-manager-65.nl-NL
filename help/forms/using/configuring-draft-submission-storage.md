---
title: Opslagservices configureren voor concepten en verzending
description: Leer hoe u opslag voor concepten en verzendingen configureert
topic-tags: publish
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 51ca2844-91f0-453a-9b39-b876399ebecb
solution: Experience Manager, Experience Manager Forms
feature: Forms Portal
role: Admin, User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# Opslagservices configureren voor concepten en verzending {#configuring-storage-services-for-drafts-and-submissions}

## Overzicht {#overview}

Met AEM Forms kun je opslaan:

* **Concepten**: Een werk-in-uitvoering vorm die eind - gebruikers vullen en bewaren voor later, en voorleggen daarna.

* **Voorleggen**: Verzonden vormen die gebruiker verstrekte gegevens bevatten.

AEM Forms Portal-services voor gegevens en metagegevens bieden ondersteuning voor concepten en verzendingen. Standaard worden de gegevens opgeslagen in de publicatie-instantie. Deze wordt vervolgens omgekeerd gerepliceerd naar de geconfigureerde auteurinstantie om beschikbaar te zijn voor percolatie naar andere publicatie-instanties.

Het probleem met de bestaande out-of-the-box-aanpak is dat alle gegevens op een publicatieinstantie worden opgeslagen, inclusief de gegevens die kunnen worden beschouwd als Personal Identified Information (PII).

Naast de hierboven vermelde standaardaanpak is er ook een alternatieve implementatie beschikbaar waarmee de formuliergegevens rechtstreeks naar de verwerking worden verplaatst en niet lokaal worden opgeslagen. Klanten die zich zorgen maken over de opslag van mogelijk vertrouwelijke gegevens op een publicatieexemplaar, kunnen kiezen in welke alternatieve implementatie de gegevens naar een verwerkingsserver worden verzonden. Aangezien de verwerking op de auteursinstantie gebeurt, blijft het typisch in een veilige streek.

>[!NOTE]
>
>Wanneer u de verzendactie Forms Portal gebruikt of de optie voor het opslaan van gegevens in het formulierportaal in een adaptieve vorm inschakelt, worden de formuliergegevens opgeslagen in AEM opslagplaats. In een productieomgeving wordt aanbevolen geen concept- of verzonden formuliergegevens in AEM opslagplaats op te slaan. In plaats daarvan moet u de concepten en verzendingscomponent integreren met een beveiligde opslag, zoals een bedrijfsdatabase, om concepten en verzonden formuliergegevens op te slaan.
>
>Voor meer informatie, zie [ Steekproef voor het integreren van concepten &amp; voorleggingscomponent met gegevensbestand ](/help/forms/using/integrate-draft-submission-database.md).

## Concepten en verzendservices van Forms Portal configureren {#configuring-forms-portal-drafts-and-submissions-services}

In de Configuratie van de Console van het AEM ( `https://[host]:'port'/system/console/configMgr`), klik om **het PortaalOntwerp van Forms en de Configuratie van de Verzending** op uit te geven wijze te openen.

Geef de waarden voor eigenschappen op op basis van uw vereisten, zoals hieronder wordt beschreven:

### Buiten-de-box services om gegevens op te slaan op een publicatie-instantie {#out-of-the-box-services-to-store-data-on-publish-instance}

De gegevens worden omgekeerd herhaald aan gevormde auteursinstantie.

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Waarde</th>
  </tr>
  <tr>
   <td>De Dienst van Gegevens van het Ontwerp van het Portaal van Forms (Herkenningsteken voor de dienst van ontwerpgegevens (<strong> concept.data.service </strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>De Dienst van Meta-gegevens van het Ontwerp van Forms Portal (Herkenningsteken voor de dienst van ontwerpMeta-gegevens (<strong> concept.metadata.service </strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftMetadataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal legt de Dienst van Gegevens (Herkenningsteken voor voorlegt datadienst (<strong> submit.data.service </strong>)) voor</td>
   <td>com.adobe.fd.fp.service.impl.SubmitDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>De Portaal van Forms legt de Dienst van Meta-gegevens (Herkenningsteken voor voorlegt meta-gegevensdienst (<strong> submit.metadata.service </strong>)) voor</td>
   <td>com.adobe.fd.fp.service.impl.SubmitMetadataServiceImpl<br /> </td>
  </tr>
 </tbody>
</table>

### Buiten-de-box services om gegevens op te slaan op een externe verwerkingsinstantie {#out-of-the-box-services-to-store-data-on-remote-processing-instance}

Gegevens worden rechtstreeks naar de geconfigureerde externe instantie geduwd

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Waarde</th>
  </tr>
  <tr>
   <td>De Dienst van Gegevens van het Ontwerp van het Portaal van Forms (Herkenningsteken voor de dienst van ontwerpgegevens (<strong> concept.data.service </strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>De Dienst van Meta-gegevens van het Ontwerp van Forms Portal (Herkenningsteken voor de dienst van ontwerpMeta-gegevens (<strong> concept.metadata.service </strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftMetadataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal legt de Dienst van Gegevens (Herkenningsteken voor voorlegt datadienst (<strong> submit.data.service </strong>)) voor</td>
   <td>com.adobe.fd.fp.service.impl.SubmitDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>De Portaal van Forms legt de Dienst van Meta-gegevens (Herkenningsteken voor voorlegt meta-gegevensdienst (<strong> submit.metadata.service </strong>)) voor</td>
   <td>com.adobe.fd.fp.service.impl.SubmitMetadataServiceRemoteImpl<br /> </td>
  </tr>
 </tbody>
</table>

Naast de hierboven gespecificeerde configuratie, verstrek informatie over de gevormde verre verwerkingsinstantie.

In de Configuratie van de Console van het AEM ( `https://[host]:'port'/system/console/configMgr`), klik om **AEM de Dienst van Montages DS** op uit te geven wijze te openen. Geef in het dialoogvenster AEM DS Settings Service informatie op over de URL van de verwerkingsserver, de gebruikersnaam van de verwerkingsserver en het wachtwoord.

>[!NOTE]
>
>Er is ook een voorbeeldimplementatie beschikbaar voor het opslaan van gebruikersgegevens in een database. Om te begrijpen hoe te om gegevens en de meta-gegevensdiensten te vormen om gebruikersgegevens in een extern gegevensbestand op te slaan, zie [ Steekproef voor het integreren van concepten &amp; verzendingscomponent met gegevensbestand ](/help/forms/using/integrate-draft-submission-database.md).
