---
title: Zoeken naar procesinstanties
description: Gebruik de pagina van het Onderzoek van het Proces om onderzoekscriteria in te gaan om een procesgeval te vinden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 35f9acbf-7a82-43b1-9e17-9be4de666212
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Zoeken naar procesinstanties{#searching-for-process-instances}

Gebruik de pagina van het Onderzoek van het Proces om onderzoekscriteria in te gaan om een procesgeval te vinden. U kunt de pagina van het Onderzoek van het Proces van de pagina van het vormwerkschema toegang hebben of door Onderzoek op de pagina van de Instantie van het Proces te klikken.

U kunt basiscriteria invoeren om een algemene zoekopdracht uit te voeren, specifieke kenmerken om een gedetailleerde zoekopdracht uit te voeren of een combinatie van basiscriteria en specifieke kenmerken om een gecombineerde zoekopdracht uit te voeren.

## Een algemene zoekopdracht uitvoeren {#perform-a-general-search}

Een algemene zoekopdracht naar een proces is het meest geschikt als u de proces-id van de procesinstantie kent, als u naar een groep verwante procesinstanties zoekt of als slechts een paar procesinstanties actief zijn.

Voer de basiscriteria in om een algemene zoekopdracht uit te voeren. Als u meerdere criteria invoert, wordt de zoekopdracht uitgevoerd met een impliciete AND-voorwaarde.

1. Klik in de beheerconsole op Services > Forms-workflow > Zoeken in processen.
1. Geef op de pagina Zoeken in proces onder Algemeen zoeken de volgende criteria op:

   * **Proces-id:** Het positieve geheel dat elke unieke procesinstantie identificeert.
   * **Processtatus:** Selecteer een status in de lijst.
   * **Toepassing:** Selecteer een toepassing in de lijst. Slechts worden de opgestelde toepassingen getoond.
   * **Procesnaam - Versie:** Selecteer een procesnaam in het menu. Slechts worden de opgestelde processen getoond.

1. Klik op Zoeken. De pagina Procesinstantie wordt weergegeven met een overzicht van de gevonden varianten.

## Gedetailleerde zoekopdrachten uitvoeren naar een proces {#perform-a-detailed-search-for-a-process}

U kunt specifieke kenmerken invoeren om een gedetailleerde zoekopdracht uit te voeren. Een gedetailleerde zoekopdracht is het meest geschikt als u veel procesinstanties uitvoert en u de mogelijke zoekopdrachten aan de hand van bepaalde criteria moet beperken.

1. Klik in de beheerconsole op Services > Forms-workflow > Zoeken in processen.
1. Geef op de pagina Zoeken in proces onder Gedetailleerd zoeken de eerste criteria op die u hebt ingesteld:

   * Selecteer een kenmerk in de lijst Kenmerk.
   * Selecteer een operator in de lijst Filter.
   * Typ in het vak Waarde een waarde die geschikt is voor het geselecteerde kenmerk.

1. Als u nog een rij wilt toevoegen, selecteert u Meer filters. Er wordt een andere set met kenmerken-, filter- en waardenlijsten weergegeven en een lijst met voorwaarden.
1. Selecteer AND of OR onder Voorwaarde. Herhaal desgewenst de stappen 1 tot en met 3 om uw zoekopdracht verder te beperken.
1. Als u rijen wilt toevoegen of verwijderen, klikt u op Meer filters of Minder filters. U kunt een tot vier rijen hebben.
1. Klik op Zoeken. De pagina Procesinstantie wordt weergegeven met een overzicht van de gevonden varianten.

[Over procesinstantiestatussen](/help/forms/using/admin-help/processes.md#about-process-instance-statuses)

## Een gecombineerde zoekopdracht naar een proces uitvoeren {#perform-a-combined-search-for-a-process}

Als u een zoekopdracht wilt maken op basis van zowel een algemene zoekopdracht als een gedetailleerde zoekopdracht, met een impliciete AND tussen de gebieden, voert u uw zoekcriteria in in de gebieden Algemeen zoeken en Gedetailleerd zoeken op de pagina Zoeken in proces.

Als de zoekopdracht te smal is, worden er geen exemplaren gevonden.
