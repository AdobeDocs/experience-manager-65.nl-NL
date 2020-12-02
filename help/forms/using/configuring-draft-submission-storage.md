---
title: Opslagservices configureren voor concepten en verzending
seo-title: Opslagservices configureren voor concepten en verzending
description: Leer hoe u opslag voor concepten en verzendingen configureert
seo-description: Leer hoe u opslag voor concepten en verzendingen configureert
uuid: 2f4efc07-312c-4908-8c91-84f4e6c5ad25
topic-tags: publish
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 6ebb6420-68b6-4abc-b298-c252db038416
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f
workflow-type: tm+mt
source-wordcount: '547'
ht-degree: 0%

---


# Opslagservices configureren voor concepten en verzending {#configuring-storage-services-for-drafts-and-submissions}

## Overzicht {#overview}

Met AEM Forms kun je opslaan:

* **Concepten**: Een werkformulier dat eindgebruikers invullen en opslaan voor later en dat achteraf wordt verzonden.

* **Indieningen**: Verzonden formulieren met door de gebruiker opgegeven gegevens.

AEM Forms Portal-services voor gegevens en metagegevens bieden ondersteuning voor concepten en verzendingen. Standaard worden de gegevens opgeslagen in de publicatie-instantie. Deze wordt vervolgens omgekeerd gerepliceerd naar de geconfigureerde auteurinstantie om beschikbaar te zijn voor percolatie naar andere publicatie-instanties.

Het probleem met de bestaande out-of-the-box-aanpak is dat alle gegevens op een publicatieinstantie worden opgeslagen, inclusief de gegevens die kunnen worden beschouwd als Personal Identified Information (PII).

Naast de hierboven vermelde standaardaanpak is er ook een alternatieve implementatie beschikbaar waarmee de formuliergegevens rechtstreeks naar de verwerking worden verplaatst en niet lokaal worden opgeslagen. Klanten die zich zorgen maken over de opslag van mogelijk vertrouwelijke gegevens op een publicatieexemplaar, kunnen kiezen in welke alternatieve implementatie de gegevens naar een verwerkingsserver worden verzonden. Aangezien de verwerking op de auteursinstantie gebeurt, blijft het typisch in een veilige streek.

>[!NOTE]
>
>Wanneer u de verzendactie Forms Portal gebruikt of de optie voor het opslaan van gegevens in het formulierportaal in een adaptieve vorm inschakelt, worden de formuliergegevens opgeslagen in AEM opslagplaats. In een productieomgeving wordt aanbevolen geen concept- of verzonden formuliergegevens in AEM opslagplaats op te slaan. In plaats daarvan moet u de concepten en verzendingscomponent integreren met een beveiligde opslag, zoals een bedrijfsdatabase, om concepten en verzonden formuliergegevens op te slaan.
>
>Zie [Voorbeeld voor het integreren van concepten en verzendingscomponenten met database](/help/forms/using/integrate-draft-submission-database.md) voor meer informatie.

## Concepten en verzendservices van Forms Portal configureren {#configuring-forms-portal-drafts-and-submissions-services}

Klik in AEM Web Console Configuration ( `https://[host]:'port'/system/console/configMgr`) op **Forms Portal Draft and Submission Configuration** in edit mode.

Geef de waarden voor eigenschappen op op basis van uw vereisten, zoals hieronder wordt beschreven:

### Buiten-de-box services om gegevens op te slaan bij publicatie-instantie {#out-of-the-box-services-to-store-data-on-publish-instance}

Gegevens worden omgekeerd gerepliceerd naar de geconfigureerde auteurinstantie.

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Waarde</th>
  </tr>
  <tr>
   <td>Conceptgegevensservice van Forms Portal (id voor conceptgegevensservice (<strong>concept.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Conceptmetagegevensservice van Forms Portal (id voor service met conceptmetagegevens (<strong>concept.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftMetadataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal dient Data Service (id voor verzendgegevensservice (<strong>submit.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitDataServiceImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal verzendt metagegevensservice (id voor verzendmetagegevensservice (<strong>submit.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitMetadataServiceImpl<br /> </td>
  </tr>
 </tbody>
</table>

### Buiten de boxservices om gegevens op te slaan op een externe verwerkingsinstantie {#out-of-the-box-services-to-store-data-on-remote-processing-instance}

Gegevens worden rechtstreeks naar de geconfigureerde externe instantie geduwd

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Waarde</th>
  </tr>
  <tr>
   <td>Conceptgegevensservice van Forms Portal (id voor conceptgegevensservice (<strong>concept.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Conceptmetagegevensservice van Forms Portal (id voor service met conceptmetagegevens (<strong>concept.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.DraftMetadataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal dient Data Service (id voor verzendgegevensservice (<strong>submit.data.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitDataServiceRemoteImpl<br /> </td>
  </tr>
  <tr>
   <td>Forms Portal verzendt metagegevensservice (id voor verzendmetagegevensservice (<strong>submit.metadata.service</strong>))</td>
   <td>com.adobe.fd.fp.service.impl.SubmitMetadataServiceRemoteImpl<br /> </td>
  </tr>
 </tbody>
</table>

Naast de hierboven gespecificeerde configuratie, verstrek informatie over de gevormde verre verwerkingsinstantie.

Klik in AEM webconsoleconfiguratie ( `https://[host]:'port'/system/console/configMgr`) op **AEM DS Settings Service** in bewerkingsmodus. Geef in het dialoogvenster AEM DS Settings Service informatie op over de URL van de verwerkingsserver, de gebruikersnaam van de verwerkingsserver en het wachtwoord.

>[!NOTE]
>
>Er is ook een voorbeeldimplementatie beschikbaar voor het opslaan van gebruikersgegevens in een database. Zie [Voorbeeld voor het integreren van concepten en verzendingscomponenten met database](/help/forms/using/integrate-draft-submission-database.md) voor meer informatie over het configureren van gegevens en metagegevensservices voor het opslaan van gebruikersgegevens in een externe database.

