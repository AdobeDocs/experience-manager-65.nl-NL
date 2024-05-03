---
title: Opslagservices configureren voor concepten en verzending
description: Leer hoe u opslag voor concepten en verzendingen configureert
topic-tags: publish
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 51ca2844-91f0-453a-9b39-b876399ebecb
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '531'
ht-degree: 0%

---

# Opslagservices configureren voor concepten en verzending {#configuring-storage-services-for-drafts-and-submissions}

## Overzicht {#overview}

Met AEM Forms kun je opslaan:

* **Concepten**: Een werklopend formulier dat eindgebruikers invullen en opslaan voor later en dat nadien verzenden.

* **Indieningen**: Verzonden formulieren met door de gebruiker opgegeven gegevens.

AEM Forms Portal-services voor gegevens en metagegevens bieden ondersteuning voor concepten en verzendingen. Standaard worden de gegevens opgeslagen in de publicatie-instantie. Deze wordt vervolgens omgekeerd gerepliceerd naar de geconfigureerde auteurinstantie om beschikbaar te zijn voor percolatie naar andere publicatie-instanties.

Het probleem met de bestaande out-of-the-box-aanpak is dat alle gegevens op een publicatieinstantie worden opgeslagen, inclusief de gegevens die kunnen worden beschouwd als Personal Identified Information (PII).

Naast de hierboven vermelde standaardaanpak is er ook een alternatieve implementatie beschikbaar waarmee de formuliergegevens rechtstreeks naar de verwerking worden verplaatst en niet lokaal worden opgeslagen. Klanten die zich zorgen maken over de opslag van mogelijk vertrouwelijke gegevens op een publicatieexemplaar, kunnen kiezen in welke alternatieve implementatie de gegevens naar een verwerkingsserver worden verzonden. Aangezien de verwerking op de auteursinstantie gebeurt, blijft het typisch in een veilige streek.

>[!NOTE]
>
>Wanneer u de verzendactie Forms Portal gebruikt of de optie voor het opslaan van gegevens in het formulierportaal in een adaptieve vorm inschakelt, worden de formuliergegevens opgeslagen in AEM opslagplaats. In een productieomgeving wordt aanbevolen geen concept- of verzonden formuliergegevens in AEM opslagplaats op te slaan. In plaats daarvan moet u de concepten en verzendingscomponent integreren met een beveiligde opslag, zoals een bedrijfsdatabase, om concepten en verzonden formuliergegevens op te slaan.
>
>Zie voor meer informatie [Voorbeeld voor het integreren van concepten en verzendingen in de database](/help/forms/using/integrate-draft-submission-database.md).

## Concepten en verzendservices van Forms Portal configureren {#configuring-forms-portal-drafts-and-submissions-services}

In de AEM webconsoleconfiguratie ( `https://[host]:'port'/system/console/configMgr`), klikt u om te openen **Concept- en verzendconfiguratie voor Forms Portal** in bewerkingsmodus.

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
   <td>Conceptgegevensservice van Forms Portal(id voor conceptgegevensservice (<strong>concept.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Conceptmetagegevensservice van Forms Portal (id voor concept-metagegevensservice (<strong>concept.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftMetadataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal Submit Data Service (Identifier voor verzenden van gegevensservice) (<strong>submit.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal Submit Metadata Service (Identifier voor verzenden van metagegevensservice (<strong>submit.metadata.service</strong>))</td>
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
   <td>Conceptgegevensservice van Forms Portal(id voor conceptgegevensservice (<strong>concept.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Conceptmetagegevensservice van Forms Portal (id voor concept-metagegevensservice (<strong>concept.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftMetadataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal Submit Data Service (Identifier voor verzenden van gegevensservice) (<strong>submit.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal Submit Metadata Service (Identifier voor verzenden van metagegevensservice (<strong>submit.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitMetadataServiceRemoteImpl<br /> </td>
  </tr>
 </tbody>
</table>

Naast de hierboven gespecificeerde configuratie, verstrek informatie over de gevormde verre verwerkingsinstantie.

In de AEM webconsoleconfiguratie ( `https://[host]:'port'/system/console/configMgr`), klikt u om te openen **AEM DS Settings Service** in bewerkingsmodus. Geef in het dialoogvenster AEM DS Settings Service informatie op over de URL van de verwerkingsserver, de gebruikersnaam van de verwerkingsserver en het wachtwoord.

>[!NOTE]
>
>Er is ook een voorbeeldimplementatie beschikbaar voor het opslaan van gebruikersgegevens in een database. Om te begrijpen hoe te om gegevens en meta-gegevensdiensten te vormen om gebruikersgegevens in een extern gegevensbestand op te slaan, zie [Voorbeeld voor het integreren van concepten en verzendingen in de database](/help/forms/using/integrate-draft-submission-database.md).
