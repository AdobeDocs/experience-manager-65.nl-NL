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

Gebruik de Configure Geavanceerde pagina van de Attributen van het Systeem om bepaalde montages in het configuratiedossier te wijzigen zonder de behoefte om, het dossier uit te voeren uit te geven en in te voeren. (Zie [Het configuratiebestand importeren en exporteren](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file).)

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Configuration > Configure Advanced System Attributes]**.
1. (Optioneel) Wijzig een van de volgende sessiekenmerken:

   **Tijdslimiet voor sessie (minuten):** De hoeveelheid tijd, in minuten, voordat een gebruiker automatisch uit het systeem wordt afgemeld. AEM formuliercomponenten zoals Workbench time-out na twee uur, ongeacht activiteit of inactiviteit, en de gebruiker moet zich opnieuw aanmelden. Geldige waarden zijn `1` tot `1440`. De standaardwaarde is `120` (2 uur). Deze instelling werkt de `SAML/Producer/assertionValidityInMinutes` ingangstoets in het configuratiebestand.

   >[!NOTE]
   >
   >U moet de time-outlimiet voor sessies niet instellen op minder dan 10 minuten, omdat het systeem zich mogelijk niet correct gedraagt. De aanbevolen waarde is 10-120 minuten.

   **Drempel bevestiging (seconden):** Een buffertijd om vertragingen als gevolg van systeemtijdverschillen tussen AEM formuliertoepassingsserver in een cluster te compenseren. AEM formulieren werken terug op de aanmeldtijd van een gebruiker met de hoeveelheid tijd (in seconden) die in deze eigenschap is opgegeven. Geldige waarden zijn `0` tot `3600`. De standaardwaarde is `60`. Deze instelling werkt de `SAML/Producer/assertionThresholdInSeconds` ingangstoets in het configuratiebestand.

   **Maximaal toegestane verlenging van een bevestiging:** Het maximale aantal keren dat een gebruikerssessie transparant kan worden vernieuwd zonder aanmelding te vereisen. Geldige waarden zijn `0` tot `9999`. Een waarde van `0` betekent dat de beweringen niet worden verlengd. De standaardwaarde is 10. Deze instelling werkt de `SAML/Producer/maxAssertionRenewalCount` ingangstoets in het configuratiebestand.

1. (Optioneel) Wijzig een of meer van de volgende kenmerken voor directorysynchronisatie:

   **Logboekregistratie synchronisatiestatistieken:** Specificeert of het Beheer van de Gebruiker gedetailleerde statistieken tijdens het synchronisatieproces registreert. (Zie [Gedetailleerde logboekregistratie tijdens synchronisatie inschakelen of uitschakelen](/help/forms/using/admin-help/synchronizing-directories.md#enable-or-disable-detailed-logging-during-synchronization).)

   **Synch Finisher Cron Expression:** Het interval waarbij het Beheer van de Gebruiker mislukte synchronisaties opnieuw probeert. (Zie [De optie voor het opnieuw proberen van de directorysynchronisatie configureren](/help/forms/using/admin-help/synchronizing-directories.md#configure-the-directory-synchronization-retry-option).)

   **Time-out clustertaakvergrendeling in minuten:** Wordt gebruikt in geclusterde omgevingen. Als de synchronisatie op één knoop ontbreekt en het clusterslot niet wordt vrijgegeven, specificeert deze waarde het aantal notulen dat een andere knoop wacht alvorens het slot te dwingen. De standaardwaarde is `15` minuten. Geldige waarden zijn `1` tot `1440` minuten.

1. (Optioneel) Wijzig de volgende kenmerken en klik op **[!UICONTROL OK]**:

   **Gebeurteniscontrole van gebruikersbeheer:** Selecteer deze optie om controle van de gebeurtenissen van de foldersynchronisatie en van authentificatiegebeurtenissen zoals succes, mislukking, en lockout toe te laten. Deze optie is standaard alleen ingeschakeld als u een onderdeel hebt geïnstalleerd waarvoor controle nodig is, zoals een Rights Management. Deze instelling werkt de `APSAuditService` ingangstoets in het configuratiebestand.

   **Automatisch maken van dynamische groep:** Hiermee kunt u automatisch dynamische groepen maken op basis van e-maildomeinen. (Zie [Een dynamische groep maken](/help/forms/using/admin-help/creating-configuring-groups.md#create-a-dynamic-group).)

U kunt ook terugkeren naar de oorspronkelijke instellingen voor Gebruikersbeheer door op Opnieuw laden te klikken.
