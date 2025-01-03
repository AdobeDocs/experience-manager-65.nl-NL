---
title: Mappen synchroniseren
description: Leer hoe u de gebruikersbeheerdatabase synchroniseert met wijzigingen in de brondirectoryservers via handmatige of geplande synchronisatie.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: cb642289-4137-4ba7-8bde-0e458c8c94fe
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 0835dca60d8011ce8660f1e7fdefb2b14ccd6129
workflow-type: tm+mt
source-wordcount: '1015'
ht-degree: 0%

---


# Mappen synchroniseren {#synchronizing-directories}

Als u domeinen wilt synchroniseren, kunt u een handmatige of geplande synchronisatie uitvoeren. A *handsynchronisatie* synchroniseert om het even welke geselecteerde domeinen. A *geplande synchronisatie* synchroniseert alle domeinen.

De synchronisatie van de folder wordt gebruikt om details van de folderservers te trekken die u in uw foldermontages in het gegevensbestand van het Beheer van de Gebruiker specificeerde. Later kunt u ook handmatig synchroniseren als er wijzigingen of updates optreden op de directoryservers. U kunt bijvoorbeeld een handmatige synchronisatie uitvoeren als gebruikers en groepen worden toegevoegd of als er wijzigingen worden aangebracht in de account van een gebruiker.

U kunt ook een dagelijkse synchronisatieplanning instellen om de gebruikersbeheerdatabase automatisch te synchroniseren met wijzigingen of updates van de brondirectoryservers. Dit proces gebruikt echter netwerk- en serverbronnen. Kies periodes met weinig gebruikstijd en vermijd het plannen van onnodige synchronisaties die systeem en netwerkmiddelen opbinden. Als u overbodige synchronisaties wilt minimaliseren, gebruikt u in plaats daarvan de optie Direct synchroniseren.

U kunt ook specificeren of om gebruiker en groepsinformatie in de (afgekeurde) Diensten 9 van de Inhoud van het LiveCycle van de Adobe te duwen wanneer het synchroniseren van domeinen.

>[!NOTE]
>
>Maak geen meerdere lokale gebruikers en groepen terwijl er een LDAP-directorysynchronisatie wordt uitgevoerd. Als u dit proces probeert uit te voeren, kunnen fouten optreden.

>[!NOTE]
>
>Als het proces van de domeinsynchronisatie wordt onderbroken (bijvoorbeeld, is de toepassingsserver gesloten tijdens het proces), wacht terwijl alvorens u probeert om het domein te synchroniseren. Kijk naar de status om de status van synchronisatie te evalueren. Als Gebruikersbeheer een vergrendeling heeft verkregen voordat de toepassing wordt afgesloten, wacht u 10 minuten tot de vergrendeling is opgeheven nadat de server opnieuw is opgestart. Als de synchronisatiestatus &quot;Bezig&quot; is, maar de synchronisatie wordt onderbroken of geblokkeerd, probeert het Gebruikersbeheer de synchronisatie na 3 minuten opnieuw. Na drie mislukte pogingen, verklaart het Beheer van de Gebruiker de synchronisatie een mislukking en geeft het slot vrij.

>[!NOTE]
>
>Adobe® LiveCycle® Content Services ES (Afgekeurd) is een contentbeheersysteem dat met LiveCycle is geïnstalleerd. Hiermee kunnen gebruikers processen ontwerpen, beheren, bewaken en optimaliseren die op mensen zijn gericht. De ondersteuning voor Content Services (Afgekeurd) eindigt op 31-12-2014. Zie {het document van de de levenscyclus van het 0} product van de Adobe ](https://www.adobe.com/support/products/enterprise/eol/eol_matrix.html).[

## Synchronisatie van delta-directory inschakelen {#enable-delta-directory-synchronization}

Synchronisatie van Delta-directory&#39;s verbetert de efficiëntie van directorysynchronisatie. Wanneer de synchronisatie van de deltadirectory is ingeschakeld, synchroniseert het Gebruikersbeheer alleen gebruikers en groepen die sinds de laatste synchronisatie zijn toegevoegd of bijgewerkt.

Gebruikersbeheer voert de volgende stappen uit wanneer de synchronisatie van de deltadirectory is ingeschakeld:

* Haal alle gebruikers op van de directoryservers, maar werk de gebruikersbeheerdatabase alleen bij met de gebruikers waarvan de tijdstempel is gewijzigd.
* U kunt alle groepen ophalen, maar de gebruikersbeheerdatabase alleen bijwerken met de groepen waarvan de tijdstempel is gewijzigd.
* Groepsleden alleen ophalen voor de groepen waarvan de tijdstempels zijn gewijzigd en de gebruikersbeheerdatabase met die informatie bijwerken.

>[!NOTE]
>
> * Gebruikers en groepen die uit de map zijn verwijderd, worden pas verwijderd uit de gebruikersbeheerdatabase als u een volledige directorysynchronisatie uitvoert.
> * Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.


1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
2. Schakel het selectievakje Delta Synch in en klik op Opslaan.
3. Bewerk de directoryinstellingen voor elk van de ondernemingsdomeinen die de functie voor synchronisatie van de delta-directory gebruiken. Zoek op de pagina Gebruikersinstellingen en Groepinstellingen de instelling Tijdstempel wijzigen en voer `modify TimeStamp` in als waarde. Voor details over het uitgeven van ondernemingsdomeinen, zie [ het Uitgeven en het omzetten van bestaande domeinen ](/help/forms/using/admin-help/editing-converting-existing-domains.md#editing-and-converting-existing-domains).

## Gedetailleerde logboekregistratie tijdens synchronisatie inschakelen of uitschakelen {#enable-or-disable-detailed-logging-during-synchronization}

Door gebrek, registreert het Beheer van de Gebruiker gedetailleerde statistieken tijdens het synchronisatieproces.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Geavanceerde systeemkenmerken configureren.
1. Schakel onder Synch Statistics Logging het selectievakje uit om de gedetailleerde logboekregistratie uit te schakelen of selecteer deze optie om logboekregistratie in te schakelen en klik op Opslaan.

## De optie voor het opnieuw proberen van de directorysynchronisatie configureren {#configure-the-directory-synchronization-retry-option}

U kunt Gebruikersbeheer configureren om periodiek te controleren op mislukte pogingen tot directorysynchronisatie. Het Beheer van de gebruiker probeert dan om de ontbroken synchronisaties te voltooien.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Geavanceerde systeemkenmerken configureren.
1. Onder de Uitdrukking van de Uitsnede van de Finisher van de Synch, ga een kroonuitdrukking in die het interval vertegenwoordigt waarmee het Beheer van de Gebruiker mislukte synchronisaties opnieuw probeert. Het gebruik van de expressie voor uitsnijden is gebaseerd op het open-source taakplanningssysteem van Kwartz, versie 1.4.0.

   De standaardwaarde is 0 0/13 &amp;ast; ? &amp;ast; , wat betekent dat de controle elke 13 minuten plaatsvindt.

## Mappen handmatig synchroniseren {#manually-synchronize-directories}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. (Optioneel) Als u gebruikers- en groepsgegevens wilt overbrengen naar Content Services (Afgekeurd), selecteert u de optie Deze optie selecteren voor gebruikers en groepen overslaan naar geregistreerde externe belangrijkste opslagproviders. Deze optie is ook van toepassing wanneer u nieuwe gebruikers en groepen toevoegt via de pagina Gebruikers en groepen.
1. Schakel het selectievakje in voor elk ondernemingsdomein dat u wilt synchroniseren en klik op Nu synchroniseren.

   Als u meerdere domeinen selecteert, kan de domeinsynchronisatie voor alle domeinen tegelijkertijd worden uitgevoerd. Als u echter de domeinen afzonderlijk selecteert, kan slechts één domeinsynchronisatie tegelijk worden uitgevoerd.

## Mapsynchronisatie plannen {#schedule-directory-synchronization}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Synchronisatie plannen:

   * Om automatische synchronisatie op een dagelijkse basis, onder Planner toe te laten, komt de uitgezochte Voorkomen voor. Selecteer Dagelijks in de lijst en typ de tijd in het formaat van 24 uur in het overeenkomstige vakje. Wanneer u uw instellingen opslaat, wordt deze waarde omgezet in een uitsnijduitdrukking, die wordt weergegeven in het vak Uitsnijduitdrukking.
   * Als u synchronisatie wilt plannen op een bepaalde dag van de week of maand, of in een bepaalde maand, selecteert u Uitsnijduitdrukking en typt u de gewenste expressie in het vak. Synchroniseer bijvoorbeeld om 1:30 uur op de laatste vrijdag van de maand.

Het gebruik van de expressie voor uitsnijden is gebaseerd op het open-source taakplanningssysteem van Kwartz, versie 1.4.0.

* Als u automatische synchronisatie wilt uitschakelen, selecteert u Voorkomen en kiest u Nooit in de lijst.
* (Optioneel) Als u gebruikers- en groepsgegevens wilt overbrengen naar Content Services (Afgekeurd), selecteert u de optie Deze optie selecteren voor gebruikers en groepen overslaan naar geregistreerde externe belangrijkste opslagproviders. Deze optie is ook van toepassing wanneer u nieuwe gebruikers en groepen toevoegt via de pagina Gebruikers en groepen.
* Klik op Opslaan.

## Alle synchronisatie van directory&#39;s die momenteel worden uitgevoerd stoppen {#stop-all-directory-synchronizations-currently-in-progress}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer.
1. Klik op Afbreken. Deze knop wordt alleen weergegeven als er een mappensynchronisatie wordt uitgevoerd.
