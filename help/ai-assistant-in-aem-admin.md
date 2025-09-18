---
title: AI-assistent configureren in AEM
description: Leer hoe u AI Assistant instelt en configureert met de Admin Console in Adobe Experience Manager.
solution: Experience Manager
feature: Authoring, AI Assistant, AI Tools
role: Admin, Architect, Developer, User
exl-id: 06824b3d-f912-4922-8fb6-ee2ca04c6326
source-git-commit: 646816ab50c432c86772c228878f8114854c320f
workflow-type: tm+mt
source-wordcount: '1148'
ht-degree: 0%

---

# AI-assistent configureren in AEM {#aem-ai-asst-admin-setup}

<!-- An Administrator must configure access, permissions, and settings before users in their organization can use the features in AI Assistant in AEM. -->

<!-- badge: label="Beta" type="Positive" -->

Als u AI Assistant in AEM (Adobe Experience Manager) wilt gebruiken, is toestemming voor toegang tot productkennis via de AI Assistant verplicht. Deze machtiging is standaard ingeschakeld.

Als u wilt controleren wie tot de Kennis van het Product toegang heeft, verzend een e-mail naar [ aemaiassistant@adobe.com ](mailto:aemaiassistant@adobe.com) van uw e-mailadres verbonden aan uw Adobe ID. Adobe kan toegangsbeheer op gebruikersniveau inschakelen. Wanneer deze optie is ingeschakeld, kan uw beheerder gebruikerstoegang verlenen door de hieronder beschreven stappen te volgen.

Als u toegangsbeheer op gebruikersniveau hebt aangevraagd, moet uw organisatie zich aanmelden via de Adobe Admin Console. Een productbeheerder maakt (of kiest) een gebruikersgroep en verleent deze de nieuwe machtiging &quot;AI Assistant&quot;. Iedereen die aan die groep is toegevoegd, krijgt direct toegang tot AI Assistant in AEM. Als het doel bedrijfsbrede beschikbaarheid is, wijst admin eenvoudig alle gebruikers aan die groep toe.

Vanuit het perspectief van een werknemer, is het proces ongecompliceerd: identificeer de productbeheerder voor Adobe Experience Manager in uw organisatie en verzoek om aan de AI-Toegelaten gebruikersgroep te worden toegevoegd. Zodra u in die groep verschijnt, verschijnt het Hulppictogram automatisch de volgende tijd u binnen ondertekent.

Beheerders moeten het normale bestuur van Cloud Manager in gedachten houden. Houd de rechten van productbeheerders in de Admin Console in om profielen te maken, gebruikersgroepen te beheren of machtigingen te bewerken. Als de gebruikers ook de ingebouwde **eigenschap van het Ticket van de Steun** van de Hulp nodig hebben, voeg de standaard **rol Admin van de Steun** (standaardrol van Admin Console) aan de zelfde individuen of de groep toe.

Het configuratieproces van AI Assistant in AEM bestaat uit de volgende stappen:

1. [ creeer een nieuw productprofiel in Adobe Admin Console ](#create-profile).
1. [ laat de toestemmingen van de Kennis van het AI Hulpproduct ](#enable-permission) toe.
1. [ creeer een nieuwe gebruikersgroep (of gebruik een bestaande gebruikersgroep) ](#create-user-group).
1. [ voegt gebruikers aan de gebruikersgroep ](#add-users) toe.
1. [ wijs het productprofiel aan de gebruikersgroep ](#assign-product-profile) toe.

**Eerste vereisten**

Voordat u begint, moet u controleren of aan de volgende voorwaarden is voldaan:

* U moet minstens over de rechten van de productbeheerder in Adobe Admin Console beschikken.
* U hebt inzicht in de gebruikersbeheerstructuur van uw organisatie.

**overwegingen van de Configuratie**

* Verwerkingstijd: het kan maximaal 2 minuten duren voordat de in Cloud Manager gemaakte bronnen in de Admin Console worden weergegeven voor machtigingsconfiguratie.
* Meerdere profielen: gebruikers kunnen deel uitmaken van meerdere profielen en machtigingen worden gecombineerd van alle toegewezen profielen.
* Organisatiebereik: sommige machtigingen kunnen op organisatieniveau van toepassing zijn op alle programma&#39;s.
* Vooraf gedefinieerde profielen: Verwijder vooraf gedefinieerde machtigingsprofielen niet uit de Admin Console.


## 1 - Een nieuw productprofiel maken in de Adobe Admin Console{#create-profile}

1. Volg de gedetailleerde instructies in [ creeer een nieuw productprofiel in Adobe Admin Console ](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/ui/create-profile) dat in de documentatie van Experience Platform wordt gevonden.

1. Bij het maken van het nieuwe productprofiel kunt u de volgende voorgestelde waarden voor AI Assistant gebruiken.

   | Tekstveld | Voorgestelde waarde |
   | --- | --- |
   | Naam van productprofiel | `AI Assistant in AEM` (of uw voorkeursbeschrijvende naam) |
   | Weergavenaam (optioneel) | `AI Assistant` |
   | Beschrijving (optioneel) | `Product profile for managing AI Assistant in AEM access` |
   | Melding | Configureren op basis van de voorkeuren van uw organisatie |


## 2 - Bevoegdheden voor AI Assistant-productkennis inschakelen{#enable-permission}

Het proces voor het toewijzen van aangepaste machtigingen aan productprofielen volgt de standaard Adobe Cloud Manager-workflow voor aangepaste machtigingen.

Het artikel van de verwijzing: [ wijst douanetoestemmingen aan het nieuwe productprofiel ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-manager/content/requirements/custom-permissions#assign-permissions) toe

1. Klik in de Admin Console op de naam van het zojuist gemaakte productprofiel (`AI Assistant in AEM`)

   ![ Screenshot ](/help/assets/assets-ai/ai-assistant-console.png)

1. Om de lijst van editable toestemmingen te bekijken, klik de **Toestemmingen** tabel.

1. Zoek in de lijst met tabellen de machtiging `AI Assistant Product Knowledge` .

   ![ AI Hulp het lusje van Toestemmingen in Admin Console ](/help/assets/assets-ai/ai-assistant-permission.png)

1. Rechts van de toestemmingsnaam, klik ![ pictogram van het Potlood of geef pictogram ](https://spectrum.adobe.com/static/icons/workflow_18/Smock_Edit_18_N.svg) uit.

1. Op **geef Toestemmingen voor AI Medewerker** pagina uit, zet de **AI Hulpschakelaar van de Kennis van het Product** van het Product van een knevel.

   ![ geef de pagina van Toestemmingen voor AI de Hulpoptie van de knevel van de Kennis van het Product uit ](/help/assets/assets-ai/ai-assistant-prod-knowledge.png)

1. In de laag-juiste hoek van de pagina, klik **sparen**.

   Voor uw productprofiel is nu de machtiging AI Assistant-productkennis ingeschakeld.


## 3 - Een nieuwe gebruikersgroep maken (of een bestaande gebruikersgroep gebruiken){#create-user-group}

1. Voer een van de volgende handelingen uit:

>[!BEGINTABS]

>[!TAB  creeer een nieuwe gebruikersgroep ]

1. In Admin Console, klik **Gebruikers** > **Gebruikersgroepen**.

   ![ Gebruikersgroepen ](/help/assets/assets-ai/ai-assistant-user-groups.png)

1. Op de **pagina van de Groepen van de Gebruiker 0&rbrace; &lbrace;, klik** Nieuwe gebruikersgroep **.**

   ![ Nieuwe knoop van de gebruikersgroep op de pagina van de Gebruikersgroepen ](/help/assets/assets-ai/ai-assistant-new-user-group.png)

1. Op **creeer een nieuwe gebruikersgroep** pagina, verstrek de volgende informatie:

   | Optie | Voorgestelde waarde |
   | --- | --- |
   | Naam gebruikersgroep | `AI Assistant in AEM` (of uw voorkeursnaam) |
   | Beschrijving (optioneel) | `User group for managing AI Assistant in AEM access` |

   ![ creeer een nieuwe pagina van de gebruikersgroep ](/help/assets/assets-ai/ai-assistant-create-new-user-group.png)

1. In de lagere juiste hoek van de pagina, klik **sparen**.

>[!TAB  Gebruik een bestaande gebruikersgroep ]

U kunt een bestaande AEM-gebruikersgroep gebruiken als deze voldoet aan de vereisten voor toegang tot AI Assistant in plaats van een nieuwe groep te maken.

>[!ENDTABS]

## 4 - Gebruikers toevoegen aan de gebruikersgroep{#add-users}

1. Voer een van de volgende handelingen uit:

>[!BEGINTABS]

>[!TAB voeg individuele gebruikers  toe]

1. Op de **pagina van de Gebruikersgroepen**, in de **naam van de Groep** lijst, klik de naam van de gebruikersgroep die u, of een bestaande naam van de gebruikersgroep onlangs creeerde.

   ![ pagina die van de Gebruikersgroepen AI Medewerker in de naam van de AEM gebruikersgroep in de lijst tonen ](/help/assets/assets-ai/ai-assistant-user-group-name-in-table.png)

1. In de **pagina van de groepen van de Gebruiker** voor de **AI Medewerker in AEM**, klik het **Gebruikers** lusje, dan klik **voegt gebruikers** toe.

   ![ AI Medewerker in de pagina van de gebruikersgroepen van AEM, die het lusje van Gebruikers en Add gebruikersknoop toont ](/help/assets/assets-ai/ai-assistant-add-users.png)

1. Zoek en selecteer op de pagina **`Add users to this user group`** gebruikers die toegang tot de AI-assistent in AEM nodig hebben.

   ![ voegt gebruikers aan deze pagina van de gebruikersgroep ](/help/assets/assets-ai/ai-assistant-add-users-to-this-group.png) toe

1. In de laag-juiste hoek van de pagina, klik **sparen**.
1. Nu, [ wijs het productprofiel aan de gebruikersgroep ](#assign-product-profile) toe.

>[!TAB  voegt gebruikers in bulk toe ]

U kunt de bulkupload-functie in de Admin Console gebruiken.

1. Een CSV-bestand met gebruikersgegevens voorbereiden.
1. Gebruik de optie **`Add users by CSV`** voor efficiënte bulktoevoeging.
1. Nu, [ wijs het productprofiel aan de gebruikersgroep ](#assign-product-profile) toe.

>[!ENDTABS]


## 5 - Het productprofiel toewijzen aan de gebruikersgroep{#assign-product-profile}

Deze stap volgt de standaard Adobe Admin Console-workflow voor het toewijzen van productprofielen aan gebruikersgroepen.

Het artikel van de verwijzing: [ beheert productprofielen voor ondernemingsgebruikers ](https://helpx.adobe.com/enterprise/using/manage-product-profiles.html)

1. Terwijl nog in uw Medewerker AI in AEM gebruikersgroep van [ 4 - voeg gebruikers aan de gebruikersgroep ](#add-users) toe, klik de **Toegewezen productprofielen** tabel.
1. Klik **toewijzen profiel**.

   ![ AI Medewerker in de pagina van de gebruikersgroep van AEM met Toegewezen geselecteerde productprofielen ](/help/assets/assets-ai/ai-assistant-assign-profile.png)

1. Op **wijs producten en profielen** pagina toe, in het **Uitgezochte de dialoogvakje van productprofielen**, onderzoek naar en selecteer uw **AI Medewerker** productprofiel.

   ![ de &quot;Assign producten en profielen&quot;pagina, die de &quot;Uitgezochte productprofielen&quot;dialoogdoos toont, en het &quot;AI Medewerker&quot;geselecteerde productprofiel ](/help/assets/assets-ai/ai-assistant-select-product-profile.png)

1. Vlak de laag-juiste hoek van de dialoogdoos, past de klik **&#x200B;**&#x200B;toe.
1. Vlak de laag-juiste hoek van **wijs producten en profielen** pagina toe, klik **sparen**.

   {het profiel van het 0} AI Hulpproduct dat aan AI Medewerker in de gebruikersgroep van AEM wordt toegewezen ![](/help/assets/assets-ai/ai-assistant-profile-assigned-to-user-group.png)


## De configuratie controleren

* Controleer of het profiel van uw product het juiste aantal toegewezen gebruikersgroepen bevat.
* Controleer of in de gebruikersgroep het juiste aantal gebruikers wordt weergegeven.
* Bevestig dat de toestemming van de Kennis van het Product van AI Medewerker wordt toegelaten en behoorlijk gevormd.


## De configuratie testen

Een gebruiker van de toegewezen groep hebben doe het volgende:

1. Log in bij AEM.
2. Controleer of de AI Assistant-functies toegankelijk zijn.
3. Test de functionaliteit van AI Assistant om te zorgen dat deze correct wordt geactiveerd.

## Zie ook

* [AI Assistant in AEM](/help/ai-assistant-in-aem.md)
* [ de Toegangscontrole van Adobe Experience Platform ](https://experienceleague.adobe.com/en/docs/experience-platform/access-control/ui/overview)
<!-- * [Cloud Manager Custom Permissions](/help/implementing/cloud-manager/custom-permissions.md) -->
