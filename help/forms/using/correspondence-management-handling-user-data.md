---
title: Correspondentenbeheer | Gebruikersgegevens verwerken
seo-title: Correspondentenbeheer | Gebruikersgegevens verwerken
description: Correspondentenbeheer | Gebruikersgegevens verwerken
uuid: d5bb190b-d668-4da3-95da-b7705ad302d9
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 764d8e0d-604d-4c7b-89cd-7686ce5f03ff
translation-type: tm+mt
source-git-commit: a873cf3e7efd3bc9cd4744bf09078d9040efcdda
workflow-type: tm+mt
source-wordcount: '545'
ht-degree: 0%

---


# Correspondentenbeheer | Gebruikersgegevens verwerken {#correspondence-management-handling-user-data}

Met AEM Forms Correspondence Management kunt u veilige en gepersonaliseerde klantcorrespondentie maken, beheren en stroomlijnen. Het verstrekt een intuïtieve gebruikersinterface voor bedrijfsgebruikers om correspondentie tot stand te brengen gebruikend vooraf goedgekeurde inhoudsblokken en media elementen. Zie [Correspondentie](/help/forms/using/create-correspondence.md)maken voor meer informatie over het maken van correspondentie.

Wanneer een zakelijke gebruiker of een agent een correspondentie opslaat als concept of deze verzendt, wordt een letterinstantie opgeslagen in de AEM-opslagplaats. De brieveninstantie omvat brievengegevens en meta-gegevens.

>[!NOTE]
>
>In AEM 6.5 Forms is het correspondentiebeheer niet beschikbaar in het tekstvak. Als u een upgrade uitvoert vanaf een eerdere AEM Forms-versie, installeert u het compatibiliteitspakket en migreert u de middelen voor correspondentiebeheer om deze te blijven gebruiken in AEM 6.5 Forms. Zie [Compatibiliteitspakket](/help/forms/using/compatibility-package.md)voor meer informatie.

## Gebruikersgegevens en gegevensopslag {#data}

In het Correspondentiebeheer worden gegevens voor concept en verzonden brieven alleen in AEM opslagplaats opgeslagen als de publicatie-instantie is geconfigureerd voor het beheren van brievenexemplaren. Voor meer informatie over de configuratie, zie de configuratieeigenschappen [van het Beheer van de](/help/forms/using/cm-configuration-properties.md)Correspondentie.

Afhankelijk van de persistentie van de gegevensopslag die voor uw AEM plaatsing wordt gevormd, worden de concepten en de voorgelegde brievengegevens opgeslagen bij de volgende plaatsen.

<table>
 <tbody>
  <tr>
   <td><p><strong>Type persistentie</strong></p> </td>
   <td><p><strong>Gegevensopslag</strong></p> </td>
   <td><p><strong>Locatie</strong></p> </td>
  </tr>
  <tr>
   <td><p>Standaard</p> </td>
   <td><p>AEM opslagplaats van publicatie-instantie en auteurinstanties die zijn opgegeven in omgekeerde replicatieconfiguratie</p> </td>
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code> </p> </td>
  </tr>
  <tr>
   <td><p>Extern</p> </td>
   <td><p>AEM opslagplaats van de externe verwerkingsauteurinstantie</p> </td>
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code></p> </td>
  </tr>
 </tbody>
</table>

Op de hierboven vermelde locatie van AEM opslagplaats:

* `[yyyy]/[mm]/[dd]` is de nodestructuur die op de datum wordt gebaseerd waarop de brieveninstantie wordt gecreeerd
* `[node-id]` is de id die is toegewezen aan de map met de letter
* `[letter-instance-name]` is de naam die is opgegeven bij het opslaan of verzenden van een letter

Onder het [letter-instance-name] knooppunt wordt de volgende knooppuntstructuur gemaakt en worden de gegevens voor elke letterinstantie opgeslagen in de AEM-opslagplaats:

| Knooppunt | Beschrijving |
|---|---|
| `extendedProperties` | Hiermee worden eigenschappen van metagegevens van de letterinstantie opgeslagen. |
| `dataXML` | Hiermee wordt een downloadbaar dataXML-bestand opgeslagen dat de correspondentiegegevens in binaire indeling bevat. |
| `processedXDP` | Omvat de details van het malplaatje XDP dat wordt gebruikt om de voorgelegde brief tot stand te brengen. Dit knooppunt wordt alleen gemaakt voor verzonden correspondentie. |
| `submittedLetter` | Slaat de voorgelegde brievengegevens in downloadbaar binair formaat op. Dit knooppunt wordt alleen gemaakt voor verzonden correspondentie. |

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

U kunt tot ontwerp en voorgelegde brievengegevens in de gevormde gegevensopslag toegang hebben, en indien nodig, het schrappen.

### Gebruikersgegevens openen {#access-user-data}

Correspondentiebeheer biedt API&#39;s die u kunt gebruiken om concepten en verzonden brieven te zoeken en te openen. Met behulp van de API&#39;s kunt u lettervarianten zoeken en openen met de id van het lettertype of de gebruiker die de correspondentie heeft opgeslagen of verzonden. Zie [API&#39;s voor toegang tot letterinstanties](/help/forms/using/cm-apis-to-access-letter-instances.md)voor meer informatie.

U kunt ook met behulp van CRX DELite naar de letter-instantie in AEM opslagplaats navigeren. Zie [Gebruikersgegevens en gegevensopslagruimten](/help/forms/using/correspondence-management-handling-user-data.md#data) voor informatie over opgeslagen gegevens en opslaglocatie.

### Gebruikersgegevens verwijderen {#delete-user-data}

Als u een letterinstantie wilt zoeken die de gegevens van een bepaalde gebruiker bevat, kunt u:

* Gebruik correspondentiebeheer-API&#39;s als de naam van een letter of de gebruiker die het concept heeft opgeslagen of de correspondentie heeft verzonden, bekend is
* Gebruik AEM zoekopdracht in de repository met behulp van persoonlijk identificeerbare informatie zoals de e-mail-id of naam om het knooppunt te vinden waar de informatie is opgeslagen

Als u gebruikersgegevens uit concept en verzonden correspondentie volledig wilt verwijderen uit AEM systemen, moet u het knooppunt voor de letter handmatig verwijderen uit alle toepasselijke AEM.
