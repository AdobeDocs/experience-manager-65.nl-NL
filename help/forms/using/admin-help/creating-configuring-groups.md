---
title: Groepen maken en configureren
seo-title: Groepen maken en configureren
description: Leer hoe u groepen handmatig of dynamisch maakt, een groep bewerkt, details over een groep weergeeft of een groep verwijdert.
seo-description: Leer hoe u groepen handmatig of dynamisch maakt, een groep bewerkt, details over een groep weergeeft of een groep verwijdert.
uuid: 8532d72b-270a-4fcf-b7a5-56fca979a5fe
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 2058b501-65ce-4ad3-8e1b-b2eab896f70f
translation-type: tm+mt
source-git-commit: d3719a9ce2fbb066f99445475af8e1f1e7476f4e
workflow-type: tm+mt
source-wordcount: '1593'
ht-degree: 0%

---


# Groepen maken en configureren{#creating-and-configuring-groups}

Door groepen gebruikers te maken, kunt u rollen toewijzen aan de groep in plaats van aan individuele gebruikers.

Er zijn twee verschillende typen groepen beschikbaar. U kunt handmatig een groep maken en er gebruikers en andere groepen aan toevoegen. U kunt ook dynamische groepen maken die automatisch alle gebruikers bevatten die aan een opgegeven set regels voldoen.

De gebruikers kunnen een langzamere reactietijd ervaren als zij tot vele groepen (bijvoorbeeld, 500 of meer) behoren of als de groepen diep worden genesteld (bijvoorbeeld, 30 niveaus). Als dit probleem optreedt, kunt u AEM formulieren zo configureren dat informatie uit bepaalde domeinen vooraf wordt opgehaald. (Zie [AEM formulieren configureren om domeininformatie vooraf in te stellen](/help/forms/using/admin-help/configure-aem-forms-prefetch-domain.md#configure-aem-forms-to-prefetch-domain-information).)

## Handmatig een groep maken {#create-a-group-manually}

Wanneer u handmatig een groep maakt, kunt u gebruikers en andere groepen eraan toevoegen en rollen aan de groep toewijzen. U kunt de groep ook koppelen aan een bovenliggende groep.

Als u de (Vervangen) Diensten van de Inhoud gebruikt, kunt u Uitgezochte Deze Optie voor het Push Gebruikers en Groepen in Geregistreerde Externe Leveranciers van de Opslag op de pagina van het Beheer van het Domein selecteren om de informatie voor om het even welke nieuwe gebruikers of groepen te duwen die u in de Diensten van de Inhoud (Vervangen) creeert.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Gebruikers en groepen en klik vervolgens op Nieuwe groep.
1. Vul de sectie Algemene instellingen in en klik op Volgende. Canonical Name en Group Name zijn verplichte kenmerken.

   De Canonical Name is een unieke id voor de groep. Elke groep en gebruiker in een domein moet een unieke canonieke naam hebben. Schakel het selectievakje Door systeem gegenereerd in als u wilt dat gebruikersbeheer een unieke waarde toewijst of schakel het selectievakje uit en geef een aangepaste waarde op voor Canonical Name.

   Gebruik geen onderstrepingstekens (_) in canonieke namen, bijvoorbeeld `sample_group`. Wanneer u naar groepen zoekt op basis van hun canonieke naam, worden de groepen met onderstrepingstekens niet geretourneerd.

1. Als u gebruikers en groepen aan deze nieuwe groep wilt toevoegen, klikt u op Gebruikers/groepen zoeken en voert u de volgende taken uit:

   * Typ uw zoekcriteria in het vak Zoeken.
   * Selecteer Gebruikers, groepen of gebruikers en groepen in de lijst In.
   * Selecteer Naam, E-mail of Gebruikersnaam in de lijst Gebruiken.
   * Selecteer het domein, selecteer het aantal items dat u wilt weergeven en klik op Zoeken.
   * Selecteer in de zoekresultaten de selectievakjes voor de gebruikers en groepen die u aan deze nieuwe groep wilt toevoegen en klik op OK.

1. Klik op Next.
1. Als u deze nieuwe groep wilt toevoegen aan andere bestaande groepen, klikt u op Groepen zoeken en voert u de volgende taken uit:

   * Typ uw zoekcriteria in het vak Zoeken.
   * Selecteer het domein, selecteer het aantal items dat u wilt weergeven en klik op Zoeken.
   * Selecteer in de zoekresultaten de selectievakjes voor de groepen waartoe de nieuwe groep behoort en klik op OK.

1. Klik op Next.
1. Als u rollen wilt toewijzen aan de groep, klikt u op Rollen zoeken, schakelt u de selectievakjes in voor elke rol die u wilt toewijzen aan de groep en klikt u op OK. De gebruikers in de groep erven rollen die op het groepsniveau worden toegewezen.
1. Klik op Voltooien.

## Een dynamische groep maken {#create-a-dynamic-group}

In een dynamische groep selecteert u niet afzonderlijk de gebruikers die tot de groep behoren. In plaats daarvan geeft u een set regels op en worden alle gebruikers die aan deze regels voldoen, automatisch toegevoegd aan de dynamische groep.

U kunt op een van de volgende twee manieren dynamische groepen maken:

* Schakel het automatisch maken van dynamische groepen in op basis van e-maildomeinen, zoals @adobe.com. Wanneer u deze functie inschakelt, maakt Gebruikersbeheer een dynamische groep voor elk uniek e-maildomein in de database met AEM formulieren. Gebruik een uitsnijdexpressie om op te geven hoe vaak gebruikersbeheer de database met AEM formulieren doorzoekt naar nieuwe e-maildomeinen. Deze dynamische groepen worden toegevoegd aan het lokale domein DefaultDom en worden genoemd &quot;Alle gebruikers met een *`[email domain]`* postidentiteitskaart&quot;
* Maak een dynamische groep op basis van opgegeven criteria, zoals het e-maildomein, de beschrijving, de canonieke naam en de domeinnaam van de gebruiker. Een gebruiker moet aan alle opgegeven criteria voldoen om tot de dynamische groep te kunnen behoren. Als u een voorwaarde &quot;of&quot; wilt instellen, maakt u twee aparte dynamische groepen en voegt u deze twee groepen toe aan een lokale groep. U kunt deze methode bijvoorbeeld gebruiken om een groep gebruikers te maken die tot het e-maildomein @adobe.com behoren of waarvan de canonieke naam ou=adobe.com bevat. De gebruikers hoeven echter niet noodzakelijkerwijs aan beide voorwaarden te voldoen.

Een dynamische groep bevat alleen gebruikers. Het kan geen andere groepen bevatten. Een dynamische groep kan echter tot een bovenliggende groep behoren.

### Automatisch dynamische groepen maken op basis van e-maildomeinen {#automatically-create-dynamic-groups-based-on-email-domains}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Geavanceerde systeemkenmerken configureren.
1. Schakel het selectievakje Automatisch maken van dynamische groep in.
1. Geef op wanneer Gebruikersbeheer controleert op nieuwe e-maildomeinen. Deze tijd zou na de tijd van de domeinsynchronisatie moeten zijn omdat de verwezenlijking van dynamische groepen logisch slechts is als de domeinsynchronisatie wordt voltooid.

   * Om automatische synchronisatie op een dagelijkse basis toe te laten, typ de tijd in het formaat van 24 uur in Occurs Daily bij doos. Wanneer u uw instellingen opslaat, wordt deze waarde omgezet in een uitsnijdexpressie, die in het onderstaande vak wordt weergegeven.
   * Als u synchronisatie wilt plannen op een bepaalde dag van de week of maand, of in een bepaalde maand, selecteert u de gewenste uitsnijdexpressie in het vak. De standaardwaarde is `0 00 4 ? * *` (wat controle bij 4 A.M. betekent) elke dag).

      Het gebruik van de expressie voor uitsnijden is gebaseerd op het open-source taakplanningssysteem van Kwartz, versie 1.4.0.

1. Klik op Opslaan.

### Een dynamische groep maken op basis van opgegeven criteria {#create-a-dynamic-group-based-on-specified-criteria}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Gebruikers en groepen.
1. Klik op Nieuwe dynamische groep.
1. Vul de sectie Algemene instellingen in. Groepsnaam is een verplicht kenmerk. U kunt de groep aan om het even welk gevormd domein toewijzen.
1. Geef onder Dynamische groepscriteria een of meer kenmerken op die worden gebruikt om de dynamische groep te vullen.

   >[!NOTE]
   >
   >De kenmerken E-mail, Beschrijving en Canonical Name zijn hoofdlettergevoelig wanneer u de operator Equals gebruikt. Ze zijn niet hoofdlettergevoelig bij Begint met, Eindigt met of Bevat operatoren.

   **E-mail:Het e-maildomein van de** gebruiker, zoals  `@adobe.com`.

   **Beschrijving:Beschrijving van** gebruiker, zoals &quot;Computerwetenschapper&quot;

   **Canonical Name:** User&#39;s canonical name, zoals  `ou=adobe.com`

   **Domeinnaam:** de naam van het domein waartoe de gebruiker behoort, zoals  `DefaultDom`. Het attribuut van de Naam van het Domein is case-sensitive wanneer het gebruiken van Bevat exploitant. Het is niet hoofdlettergevoelig met de operatoren Begint met, Eindigt met of Gelijk aan.

1. Klik op Testen. Op een testpagina worden de eerste 200 gebruikers weergegeven die aan de gedefinieerde criteria voldoen. Klik op Sluiten.
1. Als de test de verwachte resultaten heeft geretourneerd, klikt u op Volgende. Bewerk anders de dynamische groepscriteria en test het opnieuw.
1. Als u de dynamische groep aan een bovenliggende groep wilt toevoegen, klikt u op Groepen zoeken en voert u de volgende taken uit:

   * Typ uw zoekcriteria in het vak Zoeken.
   * Selecteer het domein, selecteer het aantal items dat u wilt weergeven en klik op Zoeken.
   * Selecteer in de zoekresultaten de selectievakjes voor groepen waartoe de dynamische groep behoort en klik op OK.

1. Klik op Next.
1. Als u rollen wilt toewijzen aan de dynamische groep, klikt u op Rollen zoeken, schakelt u de selectievakjes in voor elke rol die u wilt toewijzen aan de groep en klikt u op OK. De gebruikers in de groep erven rollen die op het groepsniveau worden toegewezen.
1. Klik op Voltooien.

## Details weergeven over een groep {#view-details-about-a-group}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Gebruikers en groepen.
1. Selecteer Groep in de lijst In en klik vervolgens op Zoeken. De resultaten van de zoekopdracht worden onder aan de pagina weergegeven. U kunt de lijst sorteren door op een van de kolomkoppen te klikken.
1. Klik op de naam van de groep om details weer te geven over de groep. De pagina Groepdetails wordt weergegeven.
1. Klik op Onderliggende principes om de directe leden van de groep weer te geven.

## Een groep {#edit-a-group} bewerken

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Gebruikers en groepen.
1. Ga als volgt te werk om de groep te zoeken die u wilt bewerken:

   * Typ uw zoekcriteria in het vak Zoeken.
   * Selecteer Naam of E-mail in de lijst Gebruiken.
   * Selecteer Groepen in de lijst In.
   * Selecteer het domein, selecteer het aantal items dat u wilt weergeven en klik op Zoeken.
   * Klik in de zoekresultaten op de naam van de groep die u wilt bewerken.

1. Bewerk op het tabblad Details de algemene instellingen en klik op Opslaan.
1. Als u de gekoppelde groepen wilt bewerken, klikt u op het tabblad Bovenliggende groepen en voert u de volgende taken uit:

   * Als u groepen wilt zoeken die u aan de koppeling wilt toevoegen, klikt u op Groepen zoeken en vult u de zoekgegevens in.
   * Als u groepen wilt toevoegen, schakelt u het selectievakje in voor de groepen die u wilt toevoegen, klikt u op OK en vervolgens op Opslaan.
   * Als u een gekoppelde groep wilt verwijderen, schakelt u het selectievakje in dat de groep moet verwijderen, klikt u op Verwijderen, klikt u op OK en vervolgens op Opslaan.

1. Als u de gebruikers en groepen in de groep wilt bewerken, klikt u op het tabblad Onderliggende principal en voert u de volgende taken uit:

   * Als u wilt zoeken naar gebruikers en groepen die u wilt toevoegen, klikt u op Gebruikers/groepen zoeken en vult u de zoekgegevens in.
   * Als u een gebruiker of groep wilt toevoegen, schakelt u het selectievakje voor de gebruiker of groep in, klikt u op OK en vervolgens op Opslaan.
   * Als u een gebruiker of groep wilt verwijderen, schakelt u het selectievakje voor de gebruiker of groep in, klikt u op Verwijderen, klikt u op OK en vervolgens op Opslaan.

1. Als u roltoewijzingen wilt bewerken, klikt u op het tabblad Roltoewijzingen en voert u de volgende taken uit:

   * Klik op Rollen zoeken om rollen te zoeken die u aan de groep wilt toewijzen.
   * Als u een rol wilt toevoegen, schakelt u het selectievakje voor de rol in, klikt u op OK en vervolgens op Opslaan.
   * Als u de toewijzing van een rol ongedaan wilt maken, schakelt u het selectievakje voor de rol in, klikt u op Toewijzen ongedaan maken en klikt u vervolgens op Opslaan.

## Een groep {#delete-a-group} verwijderen

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Gebruikers en groepen.
1. Selecteer Groepen in de lijst Zoeken en klik op Zoeken.
1. Schakel het selectievakje voor de groep die u wilt verwijderen in, klik op Verwijderen en klik op OK.

