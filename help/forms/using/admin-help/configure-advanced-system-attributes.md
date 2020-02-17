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

---


# Geavanceerde systeemkenmerken configureren {#configure-advanced-system-attributes}

Gebruik de Configure Geavanceerde pagina van de Attributen van het Systeem om bepaalde montages in het configuratiedossier te wijzigen zonder de behoefte om, het dossier uit te voeren uit te geven en in te voeren. (Zie Het configuratiebestand [](/help/forms/using/admin-help/importing-exporting-configuration-file.md#importing-and-exporting-the-configuration-file)importeren en exporteren.)

1. Klik in de beheerconsole op **[!UICONTROL Instellingen > Gebruikersbeheer > Configuratie > Geavanceerde systeemkenmerken]** configureren.
1. (Optioneel) Wijzig een van de volgende sessiekenmerken:

   **** Tijdslimiet voor sessie (minuten): De hoeveelheid tijd, in minuten, voordat een gebruiker automatisch uit het systeem wordt afgemeld. Standaard vormt AEM componenten, zoals Workbench time out na twee uur, ongeacht activiteit of inactiviteit, en de gebruiker moet zich opnieuw aanmelden. Geldige waarden zijn `1` aan `1440`. De standaardwaarde is `120` (2 uur). Met deze instelling wordt de `SAML/Producer/assertionValidityInMinutes` ingangstoets in het configuratiebestand bijgewerkt.

   >[!NOTE]
   >
   >U moet de time-outlimiet voor sessies niet instellen op minder dan 10 minuten, omdat het systeem zich mogelijk niet correct gedraagt. De aanbevolen waarde is 10-120 (minuten).

   **** Drempel bevestiging (seconden): Een buffertijd om vertragingen als gevolg van verschillen in systeemtijd tussen AEM-formuliertoepassingsservers in een cluster te compenseren. Met AEM-formulieren wordt de aanmeldtijd van een gebruiker teruggezet op basis van de tijd (in seconden) die in deze eigenschap is opgegeven. Geldige waarden zijn `0` aan `3600`. De standaardwaarde is `60`. Met deze instelling wordt de `SAML/Producer/assertionThresholdInSeconds` ingangstoets in het configuratiebestand bijgewerkt.

   **** Maximaal toegestane verlenging van een bevestiging: Het maximale aantal keren dat een gebruikerssessie transparant kan worden vernieuwd zonder aanmelding te vereisen. Geldige waarden zijn `0` aan `9999`. Een waarde van `0` betekent dat beweringen niet worden vernieuwd. De standaardwaarde is 10. Met deze instelling wordt de `SAML/Producer/maxAssertionRenewalCount` ingangstoets in het configuratiebestand bijgewerkt.

1. (Optioneel) Wijzig een of meer van de volgende kenmerken voor directorysynchronisatie:

   **** Logboekregistratie synchronisatiestatistieken: Specificeert of het Beheer van de Gebruiker gedetailleerde statistieken tijdens het synchronisatieproces registreert. (Zie Gedetailleerde logboekregistratie tijdens synchronisatie [in- of uitschakelen](/help/forms/using/admin-help/synchronizing-directories.md#enable-or-disable-detailed-logging-during-synchronization).)

   **** Synch Finisher Cron Expression: Het interval waarbij het Beheer van de Gebruiker mislukte synchronisaties opnieuw probeert. (Zie De optie [voor het opnieuw proberen van de directorysynchronisatie](/help/forms/using/admin-help/synchronizing-directories.md#configure-the-directory-synchronization-retry-option)configureren.)

   **** Time-out clustertaakvergrendeling in minuten: Wordt gebruikt in geclusterde omgevingen. Als de synchronisatie op één knoop ontbreekt en het clusterslot niet wordt vrijgegeven, specificeert deze waarde het aantal notulen dat een andere knoop wacht alvorens het slot te dwingen. The default value is `15` minutes. Geldige waarden zijn `1` `1440` minuten.

1. (Optioneel) Wijzig de volgende kenmerken en klik op **[!UICONTROL OK]**:

   **** Gebeurteniscontrole van gebruikersbeheer: Selecteer deze optie om controle van de gebeurtenissen van de foldersynchronisatie en van authentificatiegebeurtenissen zoals succes, mislukking, en lockout toe te laten. Deze optie is standaard alleen geselecteerd als u een component hebt geïnstalleerd waarvoor controle vereist is, zoals Rights Management. Met deze instelling wordt de `APSAuditService` ingangstoets in het configuratiebestand bijgewerkt.

   **** Automatisch maken van dynamische groep: Hiermee kunt u automatisch dynamische groepen maken op basis van e-maildomeinen. (Zie [Een dynamische groep](/help/forms/using/admin-help/creating-configuring-groups.md#create-a-dynamic-group)maken.)

U kunt ook terugkeren naar de oorspronkelijke instellingen voor Gebruikersbeheer door op Opnieuw laden te klikken.
