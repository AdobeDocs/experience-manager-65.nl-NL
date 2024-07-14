---
title: Geavanceerde systeemkenmerken configureren
description: Gebruik de Configure Geavanceerde pagina van de Attributen van het Systeem om bepaalde montages in het configuratiedossier te wijzigen zonder de behoefte om, het dossier uit te voeren uit te geven en in te voeren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: 809af2c0-6f5c-4dd4-af48-dbf476c9ea45
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: e821be5233fd5f6688507096790d219d25903892
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---

# Geavanceerde systeemkenmerken configureren {#configure-advanced-system-attributes}

Gebruik de Configure Geavanceerde pagina van de Attributen van het Systeem om bepaalde montages in het configuratiedossier te wijzigen zonder de behoefte om, het dossier uit te voeren uit te geven en in te voeren. (Zie [ het Invoeren en het uitvoeren van het configuratiedossier ](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file).)

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Configuration > Configure Advanced System Attributes]** .
1. (Optioneel) Wijzig een van de volgende sessiekenmerken:

   **de Grens van de Onderbreking van de Zitting (Minuten):** de hoeveelheid tijd, in notulen, alvorens een gebruiker automatisch het programma wordt geopend uit het systeem. AEM formuliercomponenten zoals Workbench time-out na twee uur, ongeacht activiteit of inactiviteit, en de gebruiker moet zich opnieuw aanmelden. Geldige waarden zijn `1` tot `1440` . De standaardwaarde is `120` (2 uur). Met deze instelling wordt de invoersleutel `SAML/Producer/assertionValidityInMinutes` in het configuratiebestand bijgewerkt.

   >[!NOTE]
   >
   >U moet de time-outlimiet voor sessies niet instellen op minder dan 10 minuten, omdat het systeem zich mogelijk niet correct gedraagt. De aanbevolen waarde is 10-120 minuten.

   **Drempel van de Bevestiging (Seconden):** De buffertijd van A om vertragingen wegens systeemtijdverschillen tussen AEM server van de vormtoepassing in een cluster te compenseren. AEM formulieren werken terug op de aanmeldtijd van een gebruiker met de hoeveelheid tijd (in seconden) die in deze eigenschap is opgegeven. Geldige waarden zijn `0` tot `3600` . De standaardwaarde is `60` . Met deze instelling wordt de invoersleutel `SAML/Producer/assertionThresholdInSeconds` in het configuratiebestand bijgewerkt.

   **Maximum Toegestane Verlengingen van een Bevestiging:** het maximumaantal tijden de zitting van een gebruiker kan transparant worden vernieuwd zonder login te vereisen. Geldige waarden zijn `0` tot `9999` . De waarde `0` betekent dat beweringen niet worden vernieuwd. De standaardwaarde is 10. Met deze instelling wordt de invoersleutel `SAML/Producer/maxAssertionRenewalCount` in het configuratiebestand bijgewerkt.

1. (Optioneel) Wijzig een of meer van de volgende kenmerken voor directorysynchronisatie:

   **Logging van de Statistieken van de Synch:** specificeert of het Beheer van de Gebruiker gedetailleerde statistieken tijdens het synchronisatieproces registreert. (Zie [ toelaten of onbruikbaar maken gedetailleerd registreren tijdens synchronisatie ](/help/forms/using/admin-help/synchronizing-directories.md#enable-or-disable-detailed-logging-during-synchronization).)

   **Uitdrukking van de Uitsnede van de Finisher van de Synch:** het interval waarbij het Beheer van de Gebruiker synchronisaties ontbrak. (Zie [ vormen de optie van de foldersynchronisatie opnieuw probeert ](/help/forms/using/admin-help/synchronizing-directories.md#configure-the-directory-synchronization-retry-option).)

   **Onderbreking van het Slot van de Taak van de Cluster in notulen:** Gebruikt in gegroepeerde milieu&#39;s. Als de synchronisatie op één knoop ontbreekt en het clusterslot niet wordt vrijgegeven, specificeert deze waarde het aantal notulen dat een andere knoop wacht alvorens het slot te dwingen. De standaardwaarde is `15` minuten. Geldige waarden zijn `1` tot `1440` minuten.

1. (Optioneel) Wijzig de volgende kenmerken en klik op **[!UICONTROL OK]** :

   **Controle van de Gebeurtenis van de Manager van de Gebruiker:** selecteer deze optie om controle van de gebeurtenissen van de foldersynchronisatie en van authentificatiegebeurtenissen zoals succes, mislukking, en lockout toe te laten. Deze optie is standaard alleen ingeschakeld als u een onderdeel hebt geïnstalleerd waarvoor controle nodig is, zoals een Rights Management. Met deze instelling wordt de invoersleutel `APSAuditService` in het configuratiebestand bijgewerkt.

   **AutoCreatie van Dynamische Groep:** laat de automatische verwezenlijking van dynamische groepen toe die op e-maildomeinen worden gebaseerd. (Zie [ een dynamische groep ](/help/forms/using/admin-help/creating-configuring-groups.md#create-a-dynamic-group) creëren.)

U kunt ook terugkeren naar de oorspronkelijke instellingen voor Gebruikersbeheer door op Opnieuw laden te klikken.
