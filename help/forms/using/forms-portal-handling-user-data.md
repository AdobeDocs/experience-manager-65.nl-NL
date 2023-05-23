---
title: Forms Portal | Gebruikersgegevens verwerken
seo-title: Forms Portal | Handling user data
description: Forms Portal | Gebruikersgegevens verwerken
uuid: 2ac2b2a9-b603-489a-86b8-a78b697f130d
contentOwner: vishgupt
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 48f841b7-0e7f-4216-9ee8-fb6e843acaf0
role: Admin
exl-id: 791524a4-a8bb-4632-a68d-e96864e139a9
source-git-commit: 603518dbe3d842a08900ac40651919c55392b573
workflow-type: tm+mt
source-wordcount: '851'
ht-degree: 0%

---

# Forms Portal | Gebruikersgegevens verwerken {#forms-portal-handling-user-data}

[!DNL AEM Forms] portal biedt componenten waarmee u adaptieve formulieren, HTML5-formulieren en andere Forms-elementen kunt weergeven op [!DNL AEM Sites] pagina. Bovendien kunt u het configureren om concepten en verzonden adaptieve formulieren en HTML5 formulieren voor een aangemelde gebruiker weer te geven. Voor meer informatie over formulierportal raadpleegt u [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md).

Wanneer een aangemelde gebruiker een adaptief formulier opslaat als concept of het verzendt, worden deze weergegeven op de tabbladen Concepten en Verzending op de portal Formulieren. De gegevens voor concepten of verzonden formulieren worden opgeslagen in de gegevensopslag die is geconfigureerd voor AEM implementatie. Concepten en opmerkingen van anonieme gebruikers worden niet weergegeven op de pagina Formulierportal. nochtans, wordt het gegeven opgeslagen in de gevormde gegevensopslag. Zie voor meer informatie [Opslagservices configureren voor concepten en verzending](/help/forms/using/configuring-draft-submission-storage.md).

## Gebruikersgegevens en gegevensopslag {#user-data-and-data-stores}

In Forms Portal worden gegevens voor concepten en verzonden formulieren opgeslagen in de volgende scenario&#39;s:

* De verzendactie die in het adaptieve formulier is geconfigureerd, is **Forms Portal-verzendactie**.
* Voor het verzenden van andere acties dan **Forms Portal-verzendactie** de **[!UICONTROL Store data in forms portal]** optie is ingeschakeld in het dialoogvenster **[!UICONTROL Submission]** eigenschappen van de adaptieve formuliercontainer.

Voor elk ontwerp en voorgelegd formulier voor het programma geopende en anonieme gebruikers, slaat het portaal van formulieren de volgende gegevens op:

* Metagegevens van formulieren zoals de naam, het formulierpad, de concept- of verzendings-id, het pad naar bijlagen en de gebruikersnaam van de gebruikersgegevens
* Formulierbijlage als gegevensbytes
* Formuliergegevens als gegevensbytes

Afhankelijk van de geconfigureerde persistentie van de gegevensopslag worden concepten en verzonden formuliergegevens opgeslagen op de volgende locaties.

<table>
 <tbody>
  <tr>
   <td><p><strong>Type persistentie</strong></p> </td>
   <td><p><strong>Gegevensopslag</strong></p> </td>
   <td><p><strong>Locatie</strong></p> </td>
  </tr>
  <tr>
   <td><p>Standaard</p> </td>
   <td><p>AEM opslagplaats van auteur- en publicatieinstanties</p> </td>
   <td><p><code>/content/forms/fp/</code></p> </td>
  </tr>
  <tr>
   <td><p>Extern</p> </td>
   <td><p>AEM opslagplaats van auteur en externe AEM</p> </td>
   <td><p><code>/content/forms/fp/</code></p> </td>
  </tr>
  <tr>
   <td><p>Database</p> </td>
   <td><p>AEM gegevensopslagruimte van auteurinstantie en databasetabellen</p> </td>
   <td>Databasetabellen <code>data</code>, <code>metadata</code>, en <code>additionalmetadata</code></td>
  </tr>
 </tbody>
</table>

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

U kunt tot ontwerp en voorgelegde vormengegevens voor het programma geopende en anonieme gebruikers in de gevormde gegevensopslag toegang hebben, en indien nodig, het schrappen.

### AEM {#aem-instances}

Alle concepten en verzonden formuliergegevens in AEM instanties (auteur, publicatie of extern) voor aangemelde en anonieme gebruikers worden opgeslagen in het dialoogvenster `/content/forms/fp/` knooppunt van de toepasselijke AEM opslagplaats. Telkens wanneer een aangemelde of anonieme gebruiker een concept opslaat of een formulier, een `draft ID` of `submission ID`, `user data ID`en een willekeurige `ID` voor elke (indien van toepassing) bijlage wordt gegenereerd, die bij het desbetreffende ontwerp of de respectieve indiening hoort.

#### Gebruikersgegevens openen {#access-user-data}

Wanneer een aangemelde gebruiker een concept opslaat of een formulier verzendt, wordt een onderliggend knooppunt gemaakt met haar gebruikersnaam. Concepten en verzendgegevens voor Sarah Rose waarvan de gebruikersnaam `srose` worden opgeslagen in `/content/forms/fp/srose/` knooppunt in AEM repository. Binnen de knoop van identiteitskaart van de gebruiker, worden de gegevens georganiseerd in een hiërarchische structuur.

In de volgende tabel wordt uitgelegd hoe de gegevens voor alle concepten `srose` wordt opgeslagen in AEM opslagplaats.

>[!NOTE]
>
>Een exacte structuur zoals `drafts` wordt gerepliceerd voor verzonden formulieren voor `srose` onder de `/content/forms/fp/srose/submit/` knooppunt.
>
>Alle ontwerpen en opmerkingen van `anonymous` gebruikers worden opgeslagen onder de `/content/forms/fp/anonymous/` knooppunt, dat concepten en verzendingen voor alle anonieme gebruikers onder de `draft` en `submit` knooppunten.

| Knooppunt | Beschrijving |
|---|---|
| `/content/forms/fp/srose/drafts` | Containerknoopgegevens voor alle concepten door de gebruiker |
| `/content/forms/fp/srose/drafts/attachments/` | Hiermee organiseert u alle bijlagen voor de gebruiker op basis van concept-id |
| `/content/forms/fp/srose/drafts/attachments/<ID>` | Bevat bijlage voor geselecteerde identiteitskaart in binaire formaat |
| `/content/forms/fp/srose/drafts/metadata/` | Hiermee organiseert u metagegevens van formulieren voor de gebruiker op basis van concept-id |
| `/content/forms/fp/srose/drafts/metadata/<draft ID>` | Bevat formuliermetagegevens voor de geselecteerde concept-id |
| `/content/forms/fp/srose/drafts/data/` | Hiermee ordent u formuliergegevens voor de gebruiker op basis van de gebruikersnaam |
| `/content/forms/fp/srose/drafts/data/<user data ID>` | Bevat formuliergegevens voor de geselecteerde gebruikersnaam in binaire indeling |

#### Gebruikersgegevens verwijderen {#delete-user-data}

Als u gebruikersgegevens uit concepten en verzendingen voor een aangemelde gebruiker volledig van AEM systemen wilt verwijderen, moet u de `user ID` knooppunt voor een specifieke gebruiker van het auteurknooppunt. U moet gegevens handmatig verwijderen uit alle toepasselijke AEM.

Concepten en verzendgegevens voor alle anonieme gebruikers worden opgeslagen in de algemene `drafts` en `submit` knooppunten onder `/content/forms/fp/anonymous`. Er is geen methode om gegevens voor een bepaalde anonieme gebruiker te vinden tenzij sommige identificeerbare informatie gekend is. In dit geval kunt u zoeken naar de informatie die de anonieme gebruiker in AEM opslagplaats identificeert en handmatig het knooppunt met het knooppunt uit alle toepasselijke AEM verwijderen om gegevens uit het AEM systeem te verwijderen. Als u echter gegevens voor alle anonieme gebruikers wilt verwijderen, kunt u de opdracht `anonymous` knooppunt om concepten en verzendgegevens voor alle anonieme gebruikers te verwijderen.

### Database {#database}

Wanneer AEM wordt gevormd om gegevens in een gegevensbestand op te slaan, vormen portalconcept en voorleggingsgegevens in de volgende gegevensbestandlijsten voor zowel het programma geopende als anonieme gebruikers worden opgeslagen:

* data
* metagegevens
* aanvullende metagegevens

#### Gebruikersgegevens openen {#access-user-data-1}

Om tot concepten en voorleggingsgegevens voor het programma geopende en anonieme gebruikers in de gegevensbestandlijsten toegang te hebben, stel het volgende gegevensbestandbevel in werking. In de query vervangt u `logged-in user` met de gebruikersnaam waarvan u de gegevens wilt openen of gebruiken `anonymous` voor anonieme gebruikers.

```sql
select * from metadata, data, additionalmetadatatable where metadata.owner = 'logged-in user' and metadata.id = additionalmetadatatable.id and metadata.userdataID = data.id
```

#### Gebruikersgegevens verwijderen {#delete-user-data-1}

Als u concepten en verzendingsgegevens voor een aangemelde gebruiker wilt verwijderen uit de databasetabellen, voert u de volgende databaseopdracht uit. In de query vervangt u `logged-in user` met de gebruikersnaam waarvan u de gegevens wilt verwijderen of met `anonymous` voor anonieme gebruikers. Merk op dat om gegevens voor een bepaalde anonieme gebruiker van het gegevensbestand te schrappen, u het moet vinden gebruikend wat identificeerbare informatie en het schrappen van gegevensbestandlijsten die de informatie bevatten.

```sql
DELETE FROM metadata, data, additionalmetadatatable USING metadata INNER JOIN data ON metadata.userdataID = data.id INNER JOIN additionalmetadatatable ON metadata.id = additionalmetadatatable.id WHERE metadata.owner = 'logged-in user'
```
