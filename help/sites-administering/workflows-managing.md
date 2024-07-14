---
title: Toegang tot werkstromen beheren
description: Leer hoe te om de Lijsten van het Toegangsbeheer volgens gebruikersrekeningen te vormen om het beginnen van, en het deelnemen aan, werkschema's toe te staan (of onbruikbaar te maken).
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
exl-id: cc54d637-d66c-49d2-99ee-00d96f1a74e0
solution: Experience Manager, Experience Manager Sites
feature: Operations
role: Admin
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Toegang tot werkstromen beheren{#managing-access-to-workflows}

Vorm ACLs volgens gebruikersrekeningen om het beginnen van, en het deelnemen aan, werkschema&#39;s toe te staan (of onbruikbaar te maken).

## Vereiste gebruikersmachtigingen voor workflows {#required-user-permissions-for-workflows}

Acties betreffende workflows kunnen worden uitgevoerd als:

* u werkt met het `admin` -account
* de account is toegewezen aan de standaardgroep `workflow-users` :

   * deze groep beschikt over alle rechten die uw gebruikers nodig hebben om workflowhandelingen uit te voeren.
   * als de account in deze groep staat, heeft deze alleen toegang tot werkstromen die het heeft gestart.

* de account is toegewezen aan de standaardgroep `workflow-administrators` :

   * deze groep heeft alle rechten die nodig zijn voor uw geprivilegieerde gebruikers om workflows te controleren en beheren.
   * als de account zich in deze groep bevindt, heeft deze toegang tot alle workflows.

>[!NOTE]
>
>Dit zijn de minimumvereisten. Uw account moet ook de toegewezen deelnemer of een lid van de toegewezen groep zijn om specifieke stappen te kunnen uitvoeren.

## Toegang tot werkstromen configureren {#configuring-access-to-workflows}

De modellen van het werkschema erven een standaard toegangsbeheerlijst (ACL) voor het controleren hoe de gebruikers met werkschema&#39;s kunnen in wisselwerking staan. Om gebruikerstoegang voor een werkschema aan te passen, wijzig de Lijst van het Toegangsbeheer (ACL) in de bewaarplaats voor de omslag die de knoop van het werkschemamodel bevat:

* [Pas ACL voor het specifieke werkschemamodel op /var/workflow/modellen toe](/help/sites-administering/workflows-managing.md#apply-an-acl-for-the-specific-workflow-model-to-var-workflow-models)
* [Creeer een subfolder in /var/workflow/modellen en pas ACL op dat toe](/help/sites-administering/workflows-managing.md#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that)

>[!NOTE]
>
>Voor informatie over het gebruiken van CRXDE Lite om ACLs te vormen, zie [ het Juiste Beheer van de Toegang ](/help/sites-administering/user-group-ac-admin.md#access-right-management).

### Pas ACL voor het specifieke werkschemamodel op /var/workflow/modellen toe {#apply-an-acl-for-the-specific-workflow-model-to-var-workflow-models}

Als het werkschemamodel binnen `/var/workflow/models` wordt opgeslagen, dan kunt u specifieke ACL, relevant voor slechts dat werkschema, op de omslag toewijzen:

1. Open CRXDE Lite in uw Webbrowser (bijvoorbeeld, [ http://localhost:4502/crx/de ](http://localhost:4502/crx/de)).
1. Selecteer in de nodestructuur het knooppunt voor de map workflowmodellen:

   `/var/workflow/models`

1. Klik het **Controle van de Toegang** tabel.
1. In de **Lokale Lijst van het Toegangsbeheer** (**Lijst van het Toegangsbeheer**), klik het plus pictogram aan **voeg Ingang** toe.
1. In **voeg Nieuwe Ingang** dialoogdoos toe, voeg ACE met de volgende eigenschappen toe:

   * **Belangrijk**: `content-authors`
   * **Type**: `Deny`
   * **Bevoegdheden**: `jcr:read`
   * **rep:glob**: verwijzing naar het specifieke werkschema

   ![ wf-108 ](assets/wf-108.png)

   De **lijst van het Toegangsbeheer** omvat nu de beperking voor `content-authors` op het `prototype-wfm-01` werkschemamodel.

   ![ wf-109 ](assets/wf-109.png)

1. Klik **sparen allen**.

   De `prototype-wfm-01` -workflow is niet meer beschikbaar voor leden van de `content-authors` -groep.

### Creeer een subfolder in /var/workflow/modellen en pas ACL op dat toe {#create-a-subfolder-in-var-workflow-models-and-apply-the-acl-to-that}

Uw [ ontwikkelingsteam kan tot de werkschema&#39;s in subfolder ](/help/sites-developing/workflows-models.md#creating-a-new-workflow) van leiden

`/var/workflow/models`

Vergelijkbaar met de DAM-workflows die zijn opgeslagen onder

`/var/workflow/models/dam/`

U kunt ACL aan de omslag zelf dan toevoegen.

1. Open CRXDE Lite in uw Webbrowser (bijvoorbeeld, [ http://localhost:4502/crx/de ](http://localhost:4502/crx/de)).
1. Selecteer in de knooppuntenstructuur het knooppunt voor de afzonderlijke map in de map met workflowmodellen, bijvoorbeeld:

   `/var/workflow/models/prototypes`

1. Klik het **Controle van de Toegang** tabel.
1. In de **Toepasselijke lijst van het Beleid van het Toegangsbeheer**, klik het plus pictogram aan **voeg** een ingang toe.
1. In de **Lokale Lijst van het Toegangsbeheer** (**Lijst van het Toegangsbeheer**), klik het plus pictogram aan **voeg Ingang** toe.
1. In **voeg Nieuwe Ingang** dialoogdoos toe, voeg ACE met de volgende eigenschappen toe:

   * **Belangrijk**: `content-authors`
   * **Type**: `Deny`
   * **Bevoegdheden**: `jcr:read`

   >[!NOTE]
   >
   >Zoals met [ ACL voor het specifieke werkschemamodel op /var/workflow/models ](/help/sites-administering/workflows-managing.md#apply-an-acl-for-the-specific-workflow-model-to-var-workflow-models) toepassen kunt u rep omvatten:glob om toegang tot een specifiek werkschema te beperken.

   ![ wf-110 ](assets/wf-110.png)

   De **lijst van het Toegangsbeheer** omvat nu de beperking voor `content-authors` op de `prototypes` omslag.

   ![ wf-111 ](assets/wf-111.png)

1. Klik **sparen allen**.

   De modellen in de map `prototypes` zijn niet meer beschikbaar voor leden van de groep `content-authors` .
