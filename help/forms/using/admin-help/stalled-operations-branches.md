---
title: Werken met stilstaande bewerkingen en vertakkingen
description: De gestalte pagina van Verrichtingen en de Geroepen pagina van Trappen tonen de processen die hebben vastgezet.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: c96faae0-2b0f-4334-b61c-f13b2d1ec179
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '707'
ht-degree: 0%

---

# Werken met stilstaande bewerkingen en vertakkingen {#working-with-stalled-operations-and-branches}

De gestalte pagina van Verrichtingen en de Geroepen pagina van Trappen tonen de processen die hebben vastgezet. Een proces kan stagneren wanneer een fout tijdens of na de uitvoering van een bewerking optreedt of als gevolg van een opzettelijke stallbewerking in het proces:

* Bewerkingen kunnen stagneren als gevolg van een onvoorziene fout. Nochtans, houdt een verrichting van de Tak van de Staal in een proces opzettelijk een proces tegen verder lopend en vereist de beheerder om tussenbeide te komen.
* De takken kunnen tussen verrichtingen tijdens een regelevaluatie stoppen.

Wanneer een proces stagneert, worden geen verdere verrichtingen in werking gesteld tot het probleem wordt bevestigd en de verrichting of de tak opnieuw begonnen.

Voor elk opgebouwd punt, toont de lijst de volgende informatie:

**Naam van de Verrichting of Naam van de Tak:** De naam van de verrichting of tak.

**Status:** altijd GESTALLEERD voor opgezette punten.

**Fout:** Een korte beschrijving van het probleem.

**identiteitskaart van het Proces:** het positieve geheel dat het vormwerkschema toewijst wanneer het proces (namelijk wanneer een gebruiker of een geautomatiseerde stap een proces) wordt geconcretiseerd. U kunt deze id gebruiken om de procesinstantie door de levenscyclus te volgen.

**Naam van het Proces - Versie:** de naam van het proces dat in Workbench wordt toegewezen.

**Geroepen Datum:** de datum en de tijd de verrichting of de tak die worden geïnstalleerd.

U kunt de volgende taken op de Geroepen pagina van Verrichtingen of Geroepen Tanden doen:

* Selecteer een fout om details over het te bekijken. Als u een fout selecteert, wordt de pagina Foutdetails weergegeven.
* Beëindig of herprobeer gestalte verrichtingen of herhaal gestalte takken.

## Opgeslagen bewerkingen of vertakkingen beëindigen of opnieuw proberen {#terminating-or-retrying-stalled-operations-or-branches}

Op de Geroepen pagina van Verrichtingen, kunt u de getoonde procesinstanties eindigen.

Wanneer u een procesinstantie beëindigt, houdt het op lopend en geen verdere verrichtingen plaatsvinden. Doorgaans beëindigt u een proces alleen als het wordt geblokkeerd of onbruikbaar wordt als gevolg van een fout en niet kan worden hersteld en opnieuw kan worden gestart.

Op de Geroepen pagina van Verrichtingen of de Geroepen pagina van Vertakkingen, kunt u de verrichting of de tak opnieuw proberen.

Wanneer u een bewerking opnieuw uitvoert, wordt een verzoek verzonden om de bewerking opnieuw te starten. Als de fout die het proces aan stagnatie veroorzaakte is opgelost en het verzoek om opnieuw te proberen succesvol is, begint het proces opnieuw lopend van het punt het, en zijn statusveranderingen in RUNNING. Als de bewerking niet opnieuw kan worden gestart, blijft deze STALLED en moet u deze wellicht beëindigen.

### Een gestapelde bewerking beëindigen {#terminate-a-stalled-operation}

1. Klik in de beheerconsole op Services > Formulierwerkstroom > Fouten met opgezette bewerkingen.
1. Voor de Geroepen pagina van Verrichtingen, selecteer het punt u wilt eindigen en klik beëindigen.

### Een stilgezette bewerking of vertakking opnieuw uitvoeren {#retry-a-stalled-operation-or-branch}

1. Klik in de beheerconsole op Services > Formulierwerkstroom en klik vervolgens op Fouten met betrekking tot gestagte bewerkingen of Geroepelde vertakkingsfouten.
1. Selecteer op de pagina Geroepen bewerkingen of Geroepen vertakkingen het item dat u opnieuw wilt proberen en klik op Opnieuw.

## Foutgegevens weergeven over stilgezette bewerkingen of vertakkingen {#viewing-error-details-about-stalled-operations-or-branches}

Als u een fout van de lijst van opgezette punten op de Geroepen pagina van Verrichtingen of Geroepen Tanden selecteert, verschijnt de pagina van de Details van de Fout, die details over de fout toont die u kan helpen het probleem problemen oplossen.

Het vak onder aan de pagina bevat de foutgegevens.

U kunt opgezette bewerkingen ook beëindigen of opnieuw proberen en opgezette vertakkingen opnieuw proberen op de pagina Foutdetails.

## Het proces wordt niet vastgezet als de escalatiegebruiker niet bestaat {#process-does-not-stall-when-escalation-user-does-not-exist}

De fouten komen voor wanneer de Assign verrichting van de Taak in de dienst van de Gebruiker van de AEM vormen wordt gevormd om de taak aan een andere gebruiker na een specifieke periode te escaleren, en de escalatiegebruiker wordt geschrapt nadat de Assign verrichting van de Taak uitvoert maar alvorens de escalatie voorkomt.

Wanneer deze situatie voorkomt, verandert de staat van het proces en de taak niet in de gevormde escalatietijd, en de escalatie komt niet voor maar het proces stagneert niet. Het volgende bericht wordt weergegeven in het serverlogbestand:

&quot;Het hoofd dat voor escalatie wordt gespecificeerd is ongeldig, voor taskID: *aantal*, gespecificeerde rij: *aantal*.&quot;

Als de escalatiegebruiker wordt geschrapt alvorens de taak wordt geproduceerd (alvorens de Assign verrichting van de Taak uitvoert), wordt de processtalls of de InvalidPrincipal uitzonderingsgebeurtenis geworpen.

Om dit probleem te verhinderen, wanneer u een gebruiker schrapt, onderzoek naar taken die tot die gebruiker behoren en behandelt hen dienovereenkomstig. (Zie [ Werkend met taken ](/help/forms/using/admin-help/tasks.md#working-with-tasks).)
