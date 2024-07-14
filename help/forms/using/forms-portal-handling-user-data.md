---
title: Forms Portal | Gebruikersgegevens verwerken
description: Meer informatie over het beheer van gebruikersgegevens, zoals toegang, verwijderen en gegevensopslag op AEM Forms Portal.
contentOwner: vishgupt
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin,User
exl-id: 791524a4-a8bb-4632-a68d-e96864e139a9
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
source-git-commit: 539da06db98395ae6eaee8103a3e4b31204abbb8
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---

# Forms Portal | Gebruikersgegevens verwerken {#forms-portal-handling-user-data}

[!DNL AEM Forms] Portal biedt componenten waarmee u adaptieve formulieren, HTML5-formulieren en andere Forms-elementen op de [!DNL AEM Sites] -pagina kunt weergeven. Bovendien kunt u het configureren om concepten en verzonden adaptieve formulieren en HTML5 formulieren voor een aangemelde gebruiker weer te geven. Voor meer informatie over het Portaal van Forms, zie [ Inleiding aan het publiceren van vormen op een portaal ](/help/forms/using/introduction-publishing-forms.md).

Wanneer een aangemelde gebruiker een adaptief formulier opslaat als concept of het verzendt, worden deze weergegeven op de tabbladen Concepten en Verzending op de Forms Portal. De gegevens voor opgestelde of ingediende formulieren worden opgeslagen in de gegevensopslag die voor AEM implementatie is geconfigureerd. De concepten en verzendingen van anonieme gebruikers worden niet weergegeven op de pagina Forms Portal, maar de gegevens worden opgeslagen in de geconfigureerde gegevensopslag. Zie [ het Vormen de opslagdiensten voor concepten en bijdragen ](/help/forms/using/configuring-draft-submission-storage.md).

## Gebruikersgegevens en gegevensopslag {#user-data-and-data-stores}

In Forms Portal worden gegevens voor concepten en verzonden formulieren opgeslagen in de volgende scenario&#39;s:

* Verzenden actie die in de adaptieve vorm wordt gevormd is **het Portaal van Forms verzendt Actie**.
* Voor verzendacties buiten **Forms Portal legt Actie** voor, wordt de **[!UICONTROL Store data in Forms Portal]** optie toegelaten in de **[!UICONTROL Submission]** eigenschappen van de adaptieve vormcontainer.

Voor elk ontwerp en voorgelegd formulier voor aangemelde en anonieme gebruikers slaat het Forms Portal de volgende gegevens op:

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
   <td><p>AEM opslagplaats voor auteur- en Publish-instanties</p> </td>
   <td><p><code>/content/forms/fp/</code></p> </td>
  </tr>
  <tr>
   <td><p>Extern</p> </td>
   <td><p>AEM opslagplaats van Auteur en externe AEM</p> </td>
   <td><p><code>/content/forms/fp/</code></p> </td>
  </tr>
  <tr>
   <td><p>Database</p> </td>
   <td><p>AEM gegevensopslagruimte van instantie Auteur en databasetabellen</p> </td>
   <td>Databasetabellen <code>data</code> , <code>metadata</code> en <code>additionalmetadata</code></td>
  </tr>
 </tbody>
</table>

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

U kunt tot ontwerp en voorgelegde vormengegevens voor het programma geopende en anonieme gebruikers in de gevormde gegevensopslag toegang hebben, en indien nodig, het schrappen.

### AEM {#aem-instances}

Alle concepten en verzonden formuliergegevens in AEM instanties (auteur, publicatie of extern) voor aangemelde en anonieme gebruikers worden opgeslagen in het knooppunt `/content/forms/fp/` van de toepasselijke AEM. Telkens wanneer een aangemelde of anonieme gebruiker een concept opslaat of een formulier verzendt, worden een `draft ID` of `submission ID` , een `user data ID` en een willekeurige `ID` waarde gegenereerd voor elke bijlage (indien van toepassing). Het is gekoppeld aan het desbetreffende ontwerp of de respectieve voorlegging.

#### Gebruikersgegevens openen {#access-user-data}

Wanneer een aangemelde gebruiker een concept opslaat of een formulier verzendt, wordt een onderliggend knooppunt gemaakt met de bijbehorende gebruikers-id. Concepten en verzendgegevens voor Sarah Rose waarvan de gebruikers-id `srose` is, worden bijvoorbeeld opgeslagen in het knooppunt `/content/forms/fp/srose/` in AEM gegevensopslagruimte. Binnen de knoop van identiteitskaart van de gebruiker, worden de gegevens georganiseerd in een hiërarchische structuur.

In de volgende tabel wordt uitgelegd hoe de gegevens voor alle concepten door `srose` in AEM opslagplaats worden opgeslagen.

>[!NOTE]
>
>Een exacte structuur zoals `drafts` wordt gerepliceerd voor verzonden formulieren voor `srose` onder het knooppunt `/content/forms/fp/srose/submit/` .
>
>Alle concepten en verzendingen door `anonymous` -gebruikers worden opgeslagen onder het knooppunt `/content/forms/fp/anonymous/` , dat concepten en verzendingen voor alle anonieme gebruikers onder de knooppunten `draft` en `submit` organiseert.

| Knooppunt | Beschrijving |
|---|---|
| `/content/forms/fp/srose/drafts` | Containerknoopgegevens voor alle concepten door de gebruiker |
| `/content/forms/fp/srose/drafts/attachments/` | Hiermee organiseert u alle bijlagen voor de gebruiker op basis van concept-id |
| `/content/forms/fp/srose/drafts/attachments/<ID>` | Bevat een bijlage voor geselecteerde identiteitskaart in binair formaat |
| `/content/forms/fp/srose/drafts/metadata/` | Hiermee organiseert u metagegevens van formulieren voor de gebruiker op basis van concept-id |
| `/content/forms/fp/srose/drafts/metadata/<draft ID>` | Bevat formuliermetagegevens voor de geselecteerde concept-id |
| `/content/forms/fp/srose/drafts/data/` | Hiermee ordent u formuliergegevens voor de gebruiker op basis van de gebruikersnaam |
| `/content/forms/fp/srose/drafts/data/<user data ID>` | Bevat formuliergegevens voor de geselecteerde gebruikersnaam in binaire indeling |

#### Gebruikersgegevens verwijderen {#delete-user-data}

Als u gebruikersgegevens wilt verwijderen uit concepten en verzendingen voor een aangemelde gebruiker van AEM systemen, moet u het knooppunt `user ID` voor een specifieke gebruiker uit het auteurknooppunt verwijderen. Verwijder handmatig gegevens uit alle toepasselijke AEM.

Concepten en verzendgegevens voor alle anonieme gebruikers worden opgeslagen in de algemene knooppunten `drafts` en `submit` onder `/content/forms/fp/anonymous` . Er is geen methode om gegevens voor een bepaalde anonieme gebruiker te vinden tenzij sommige identificeerbare informatie gekend is. In dit geval kunt u zoeken naar informatie die de anonieme gebruiker in de AEM bewaarplaats identificeert en manueel de knoop schrappen die het uit alle toepasselijke AEM instanties bevat om gegevens uit het AEM systeem te verwijderen. Als u echter gegevens voor alle anonieme gebruikers wilt verwijderen, kunt u het knooppunt `anonymous` verwijderen om concepten en verzendgegevens voor alle anonieme gebruikers te verwijderen.

### Database {#database}

Wanneer AEM wordt gevormd om gegevens in een gegevensbestand op te slaan, wordt het ontwerp en de voorleggingsgegevens van Forms Portal opgeslagen in de volgende gegevensbestandlijsten voor zowel het programma geopende als anonieme gebruikers:

* data
* metagegevens
* aanvullende metagegevens

#### Gebruikersgegevens openen {#access-user-data-1}

Om tot concepten en voorleggingsgegevens voor een het programma geopende en anonieme gebruiker in de gegevensbestandlijsten toegang te hebben, stel het volgende gegevensbestandbevel in werking. Vervang `logged-in user` in de query door de gebruikersnaam waartoe u toegang wilt hebben of door `anonymous` voor anonieme gebruikers.

```sql
select * from metadata, data, additionalmetadatatable where metadata.owner = 'logged-in user' and metadata.id = additionalmetadatatable.id and metadata.userdataID = data.id
```

#### Gebruikersgegevens verwijderen {#delete-user-data-1}

Als u concepten en verzendingsgegevens voor een aangemelde gebruiker wilt verwijderen uit de databasetabellen, voert u de volgende databaseopdracht uit. Vervang `logged-in user` in de query door de gebruikersnaam waarvan u de gegevens wilt verwijderen of door `anonymous` voor anonieme gebruikers. Om gegevens voor een bepaalde anonieme gebruiker uit het gegevensbestand te schrappen, moet u het vinden gebruikend wat identificeerbare informatie en het schrappen van gegevensbestandlijsten die de informatie bevatten.

```sql
DELETE FROM metadata, data, additionalmetadatatable USING metadata INNER JOIN data ON metadata.userdataID = data.id INNER JOIN additionalmetadatatable ON metadata.id = additionalmetadatatable.id WHERE metadata.owner = 'logged-in user'
```
