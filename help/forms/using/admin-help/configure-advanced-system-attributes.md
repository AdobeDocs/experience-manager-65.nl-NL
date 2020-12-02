---
title: Geavanceerde systeemkenmerken configureren
seo-title: Geavanceerde systeemkenmerken configureren
description: Gebruik de Configure Geavanceerde pagina van de Attributen van het Systeem om bepaalde montages in het configuratiedossier te wijzigen zonder de behoefte om, het dossier uit te voeren uit te geven en in te voeren.
seo-description: Gebruik de Configure Geavanceerde pagina van de Attributen van het Systeem om bepaalde montages in het configuratiedossier te wijzigen zonder de behoefte om, het dossier uit te voeren uit te geven en in te voeren.
uuid: 6bcfbaa9-f492-46aa-97d2-00fc3e67d0d7
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 533ad3f7-3905-420d-8bb9-8ae8f14fb28e
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '495'
ht-degree: 1%

---


# Geavanceerde systeemkenmerken configureren {#configure-advanced-system-attributes}

Gebruik de Configure Geavanceerde pagina van de Attributen van het Systeem om bepaalde montages in het configuratiedossier te wijzigen zonder de behoefte om, het dossier uit te voeren uit te geven en in te voeren. (Zie [Het configuratiebestand importeren en exporteren](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file).)

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Configuration > Configure Advanced System Attributes]**.
1. (Optioneel) Wijzig een van de volgende sessiekenmerken:

   **Tijdslimiet voor sessie (minuten):** de hoeveelheid tijd, in minuten, voordat een gebruiker automatisch wordt afgemeld bij het systeem. AEM formuliercomponenten zoals Workbench time-out na twee uur, ongeacht activiteit of inactiviteit, en de gebruiker moet zich opnieuw aanmelden. Geldige waarden zijn `1` tot `1440`. De standaardwaarde is `120` (2 uur). Met deze instelling wordt de `SAML/Producer/assertionValidityInMinutes`-invoersleutel in het configuratiebestand bijgewerkt.

   >[!NOTE]
   >
   >U moet de time-outlimiet voor sessies niet instellen op minder dan 10 minuten omdat het systeem zich mogelijk niet correct gedraagt. De aanbevolen waarde is 10-120 (minuten).

   **Assertion Threshold (Seconden):** Een buffertijd om vertragingen als gevolg van systeemtijdverschillen tussen AEM formuliertoepassingsserver in een cluster te compenseren. AEM formulieren werken terug op de aanmeldtijd van een gebruiker met de hoeveelheid tijd (in seconden) die in deze eigenschap is opgegeven. Geldige waarden zijn `0` tot `3600`. De standaardwaarde is `60`. Met deze instelling wordt de `SAML/Producer/assertionThresholdInSeconds`-invoersleutel in het configuratiebestand bijgewerkt.

   **Maximaal toegestane verlenging van een bevestiging:** het maximale aantal keren dat een gebruikerssessie transparant kan worden vernieuwd zonder dat een aanmelding vereist is. Geldige waarden zijn `0` tot `9999`. De waarde `0` betekent dat beweringen niet worden vernieuwd. De standaardwaarde is 10. Met deze instelling wordt de `SAML/Producer/maxAssertionRenewalCount`-invoersleutel in het configuratiebestand bijgewerkt.

1. (Optioneel) Wijzig een of meer van de volgende kenmerken voor directorysynchronisatie:

   **Logboekregistratie van synchronisatiestatistieken:** Geeft aan of gebruikersbeheer gedetailleerde statistieken registreert tijdens het synchronisatieproces. (Zie [Gedetailleerde logboekregistratie tijdens synchronisatie inschakelen of uitschakelen](/help/forms/using/admin-help/synchronizing-directories.md#enable-or-disable-detailed-logging-during-synchronization).)

   **Uitsnijduitdrukking synchroniseren Finisher:** het interval waarmee gebruikersbeheer opnieuw mislukte synchronisaties probeert uit te voeren. (Zie [De optie voor het opnieuw proberen van de directorysynchronisatie configureren](/help/forms/using/admin-help/synchronizing-directories.md#configure-the-directory-synchronization-retry-option).)

   **Time-out clustertaakvergrendeling in minuten:** gebruikt in geclusterde omgevingen. Als de synchronisatie op één knoop ontbreekt en het clusterslot niet wordt vrijgegeven, specificeert deze waarde het aantal notulen dat een andere knoop wacht alvorens het slot te dwingen. De standaardwaarde is `15` minuten. Geldige waarden zijn `1` tot `1440` minuten.

1. (Optioneel) Wijzig de volgende kenmerken en klik op **[!UICONTROL OK]**:

   **Gebeurteniscontrole door gebruikersbeheerder:** selecteer deze optie om de controle van gebeurtenissen van de foldersynchronisatie en van authentificatiegebeurtenissen zoals succes, mislukking, en lockout toe te laten. Deze optie is standaard alleen ingeschakeld als u een onderdeel hebt geïnstalleerd waarvoor controle nodig is, zoals een Rights Management. Met deze instelling wordt de `APSAuditService`-invoersleutel in het configuratiebestand bijgewerkt.

   **Automatisch maken van dynamische groep:** maakt het automatisch maken van dynamische groepen op basis van e-maildomeinen mogelijk. (Zie [Een dynamische groep maken](/help/forms/using/admin-help/creating-configuring-groups.md#create-a-dynamic-group).)

U kunt ook terugkeren naar de oorspronkelijke instellingen voor Gebruikersbeheer door op Opnieuw laden te klikken.
