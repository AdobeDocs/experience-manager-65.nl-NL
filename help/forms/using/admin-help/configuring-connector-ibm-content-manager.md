---
title: Connector configureren voor IBM&reg; inhoudsbeheer
description: Configureer de Connector voor IBM&reg; Inhoudsbeheer om communicatie tussen AEM formulieren en IBM&reg; Inhoudsbeheer in te schakelen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 50f0c963-8007-4e2a-aa73-d99b97d9a1aa
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
source-git-commit: 9f59606bb58b9e90f07bd22e89f3213afb54a697
workflow-type: tm+mt
source-wordcount: '273'
ht-degree: 0%

---

# Connector configureren voor IBM® Content Manager{#configuring-connector-for-ibm-content-manager}

Connector voor IBM® Content Manager zorgt voor communicatie tussen AEM formulieren en IBM® Content Manager. Zie &quot;Connectors for ECM&quot; in [Servicereferentie](https://www.adobe.com/go/learn_aemforms_services_63).

## De verbinding met IBM® Content Manager configureren {#configure-the-ibm-content-manager-connection}

1. Klik in de beheerconsole op Services > Connector voor IBM® Content Manager.
1. Voer in het vak Naam datastore de naam in van de datastore van IBM® Content Manager waarmee u verbinding wilt maken. Als de database lokaal is, voert u de naam van de database in. Als de database extern is, voert u de naam van de alias in.
1. Voer in het vak Gebruikersnaam de gebruikersnaam in van een gebruiker die verbinding gaat maken met de datastore van IBM® Content Manager.
1. Voer in het vak Wachtwoord het wachtwoord van de gebruiker in.
1. (Optioneel) Voer in het vak Tekenreeks Alias-verbinding aanvullende verbindingsargumenten in. Meestal moet dit vak leeg zijn. Raadpleeg de documentatie bij IBM® voor meer informatie.
1. Klik op Opslaan.

## Validatie van service-instellingen {#validation-of-service-settings}

Als u een onjuiste alias, gebruikersnaam of wachtwoord voor dataStore invoert, krijgt u de volgende resultaten, afhankelijk van het feit of de Content Repository Connector voor IBM® Content Manager service wordt uitgevoerd:

* Als de dienst wordt tegengehouden, wanneer u de informatie van de de dienstconfiguratie opslaat, verschijnt geen fout. Nochtans, wordt de volgende tijd u de dienst begint, een uitzondering geworpen en de dienst begint niet.
* Als de dienst is begonnen, wanneer u de informatie van de de dienstconfiguratie opslaat, probeert de dienst om de referentie informatie onmiddellijk te bevestigen. In dit geval treedt een fout op en worden de configuratiegegevens niet opgeslagen.
