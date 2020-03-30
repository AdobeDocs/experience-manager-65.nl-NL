---
title: Algemene map voor documentopslag
seo-title: Algemene map voor documentopslag
description: De GDS-map (global document storage) is een map waarin bestanden van lange duur worden opgeslagen die in een proces worden gebruikt.
seo-description: De GDS-map (global document storage) is een map waarin bestanden van lange duur worden opgeslagen die in een proces worden gebruikt.
uuid: 7681672c-a0dc-4445-8004-1b1e2ed3d301
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a33b8834-6e39-47eb-a53b-0982d32e80ad
translation-type: tm+mt
source-git-commit: 317fadfe48724270e59644d2ed9a90fbee95cf9f

---


# Algemene map voor documentopslag{#global-document-storage-directory}

De map *global document storage (GDS)* is een map waarin bestanden van lange duur worden opgeslagen die in een proces worden gebruikt. Deze bestanden bevatten PDF&#39;s, beleidsregels en formuliersjablonen. Bestanden met een lange levensduur vormen een essentieel onderdeel van de algemene status van veel implementaties van AEM-formulieren. Als sommige of alle documenten met een lange levensduur verloren gaan of beschadigd raken, kan de formulierserver instabiel worden. Invoerdocumenten voor asynchrone taakaanroepen worden ook opgeslagen in de GDS-map en moeten beschikbaar zijn voor het verwerken van aanvragen. Het is belangrijk dat u rekening houdt met de betrouwbaarheid van het bestandssysteem dat de GDS-map host. Gebruik een redundante array met onafhankelijke schijven (RAID) of andere technologie die geschikt is voor uw servicekwaliteit en serviceniveau.

Bestanden met een lange levensduur kunnen vertrouwelijke gebruikersgegevens bevatten. Deze informatie kan speciale geloofsbrieven vereisen wanneer betreden door AEM vormen APIs of gebruikersinterfaces te gebruiken. Het is belangrijk dat de GDS-map correct wordt beveiligd via het besturingssysteem. Alleen de beheerdersaccount die wordt gebruikt om de toepassingsserver uit te voeren, moet lees-/schrijftoegang hebben tot de GDS-map.

Naast het selecteren van een veilige, hoogst beschikbare folder voor GDS, kunt u ook verkiezen om documentopslag in het gegevensbestand toe te laten. Zelfs als u de AEM-formulierdatabase gebruikt voor documentopslag, is voor AEM-formulieren de GDS-map nog steeds vereist. (Zie [Back-upopties als database wordt gebruikt voor documentopslag](/help/forms/using/admin-help/files-back-recover.md#backup-options-when-database-is-used-for-document-storage).)

Toepassingsgegevens van AEM-formulieren bevinden zich in de GDS-map en de AEM-formulierdatabase. In de volgende tabel worden de gegevens en de locaties beschreven.

<table>
 <thead>
  <tr>
   <th><p>AEM-formuliergegevens</p></th>
   <th><p>Database</p></th>
   <th><p>GDS</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Toepassingsgegevens (gebruikers, rollen, processen, beleid, eindpunten, gebeurtenissen, enzovoort.)</p></td>
   <td><p>Ja</p></td>
   <td><p>Nee</p></td>
  </tr>
  <tr>
   <td><p>Ingestelde servicecontainers</p></td>
   <td><p>Ja</p></td>
   <td><p>Nee</p></td>
  </tr>
  <tr>
   <td><p>Documentbeheer </p></td>
   <td><p>Nee</p></td>
   <td><p>Ja</p></td>
  </tr>
  <tr>
   <td><p>Formulieropslagplaats</p></td>
   <td><p>Ja</p></td>
   <td><p>Nee</p></td>
  </tr>
  <tr>
   <td><p>Systeemconfiguratie</p></td>
   <td><p>Ja</p></td>
   <td><p>Nee</p></td>
  </tr>
  <tr>
   <td><p>Gecontroleerde mappen</p></td>
   <td><p>Nee</p></td>
   <td><p>Ja</p></td>
  </tr>
 </tbody>
</table>

## De GDS-map configureren {#configuring-the-gds-directory}

De locatie van de GDS-directory kan handmatig worden geconfigureerd tijdens het installatieproces van AEM-formulieren. Als de locatie-instelling tijdens de installatie leeg blijft, wordt standaard als volgt een map onder de installatie van de toepassingsserver gebruikt:

* (JBoss) `[appserver root]/server/[type]/svcnative/DocumentStorage`
* (WebLogic) `[appserverdomain]/'server'/adobe/DocumentServer/DocumentStorage`
* (WebSphere) `[appserver root]/installedApps/adobe/'server'/DocumentStorage`

## De standaard GDS-locatie wijzigen {#change-the-default-gds-location}

U kunt de GDS-locatie in de beheerconsole wijzigen nadat de installatie van AEM-formulieren is voltooid. U moet de gegevens handmatig verplaatsen om het proces te voltooien.

>[!NOTE]
>
>Migreer de gegevens op de volgende manier of er treedt gegevensverlies op.

1. Meld u aan bij de beheerconsole en klik op Instellingen > Core System Settings > Configurations.
1. Voer in het vak Algemene opslagmap voor documenten het volledige pad naar de nieuwe GDS-map in en klik op OK.
1. Sluit de toepassingsserver onmiddellijk af.
1. Verplaats alle bestanden van de oude GDS-map naar de nieuwe locatie, waarbij de interne mapstructuur behouden blijft.
1. Start de toepassingsserver opnieuw.

## Informatie over implementatiebestanden {#about-deployment-files}

AEM-formulieren bestaan uit twee typen implementatiebestanden, de servicecontainers en de Java 2 Platform, Enterprise Edition (J2EE) EAR-bestanden. De EAR-bestanden bestaan uit standaard J2EE-toepassingsbundels die de kernfunctionaliteit van AEM-formulieren bevatten. De server-specifieke EAR-bestanden van de toepassing zijn als volgt:

* adobe-core-*[appserver]*.ear
* adobe-core-*[appserver]*-*[OS]*.ear

Bij het implementeren van AEM-formulieren worden de geassembleerde EAE-bestanden en ondersteunende bestanden geïmplementeerd op de toepassingsserver waar u uw AEM-formulieroplossing wilt uitvoeren. Als u vormde en veelvoudige modules assembleerde, worden de plaatsbare modules verpakt binnen de plaatsbare EAR dossiers. Als u deze bestanden wilt implementeren, kopieert u deze naar de *[appserverstartpagina]*\server\all\deploy directory.

Modules en AEM-formulieren archiveren bestanden worden verpakt in JAR-bestanden. Omdat het geen J2EE-typebestanden zijn, worden deze niet geïmplementeerd op de toepassingsserver. In plaats daarvan worden ze naar de GDS-map gekopieerd en wordt een verwijzing naar de locatie ervan opgeslagen in de AEM-formulierdatabase. Daarom moet de GDS-map worden gedeeld tussen alle knooppunten van de cluster. Alle knopen moeten toegang tot de centrale opslagfolder voor DSCs hebben.

>[!NOTE]
>
>Alvorens u de de dienstcontainers opstelt, zorg ervoor dat u creeerde en de folder GDS vormde. (Zie [De GDS-map](global-document-storage-directory.md#configuring-the-gds-directory)configureren)

