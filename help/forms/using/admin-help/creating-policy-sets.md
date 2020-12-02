---
title: Beleidssets maken en beheren
seo-title: Beleidssets maken en beheren
description: De reeksen van het beleid worden gebruikt aan groepsbeleid dat een gemeenschappelijk bedrijfsdoel heeft. U kunt beleid in een beleidsset maken, bewerken en verwijderen.
seo-description: De reeksen van het beleid worden gebruikt aan groepsbeleid dat een gemeenschappelijk bedrijfsdoel heeft. U kunt beleid in een beleidsset maken, bewerken en verwijderen.
uuid: 11faf67c-b9b7-4394-8672-d43cace131ad
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a4fb1a11-8fe3-4092-a036-1c079aea1250
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb
workflow-type: tm+mt
source-wordcount: '1324'
ht-degree: 0%

---


# Beleidssets maken en beheren {#creating-and-managing-policy-sets}

De reeksen van het beleid worden gebruikt aan groepsbeleid dat een gemeenschappelijk bedrijfsdoel heeft. Beleidssets kunnen beschikbaar worden gemaakt voor een subset van gebruikers in het systeem.

Elke beleidsset heeft ten minste één bijbehorende beleidssetcoördinator. De *beleidssetcoördinator* is een beheerder of een gebruiker die extra toestemmingen heeft. De beleidssetcoördinator is typisch een specialist in de organisatie die het beleid in een bepaalde beleidsreeks het best kan ontwerpen.

Beleidssetcoördinatoren kunnen de volgende taken uitvoeren:

* Nieuw beleid maken
* Beleid in de beleidsset bewerken en verwijderen
* Beleidssetinstellingen bewerken
* Coördinatoren voor de beleidsset toevoegen en verwijderen
* Beleid en documentgebeurtenissen weergeven voor beleid of document binnen de beleidsset
* Toegang tot documenten intrekken
* Van beleid wisselen voor het document

Beleidssets worden gemaakt en verwijderd in de interface van de documentbeveiligingsbeheerder door supergebruikers en beleidssetcoördinatoren die hiervoor toestemming hebben.

Wanneer u een beleidsset verwijdert, kunnen beleid dat deel uitmaakte van de set, niet worden toegepast op nieuwe documenten. Nochtans, kunt u de beleidsinformatie in zowel de beleidsconsole als de eindgebruikerWeb-pagina&#39;s voor beleid bekijken die nog in gebruik zijn. U kunt de beleidsinformatie van de documentdetailpagina voor om het even welk document bekijken dat door het beleid wordt beschermd. Het beleid dat nog in gebruik is, kan worden bewerkt.

De supergebruiker of de coördinator van de beleidsreeks voegt domeinen toe die in het Beheer van de Gebruiker aan de zichtbare gebruiker en de groep voor elke beleidsreeks worden gecreeerd. Deze lijst is zichtbaar aan de coördinator van de beleidsreeks en wordt gebruikt om grenzen te zetten op welke domeinen de coördinator van de beleidsreeks kan doorbladeren wanneer het kiezen van gebruikers om aan beleid toe te voegen.

Wanneer u beleidssets maakt, wijst u gebruikers de rol van documentuitgever toe. De *documentuitgever* is de gebruiker die het document met een beleid beschermt. Deze gebruiker is, door gebrek, altijd inbegrepen op een beleid met volledige toegangsrechten, met inbegrip van herroepen en beleid omschakelingsmogelijkheden. Beheerders kunnen echter de toegangsrechten van de uitgever van het document voor gedeeld beleid wijzigen. De beheerder kan bijvoorbeeld het recht van de uitgever van het document uitschakelen om de toegang tot het document in te trekken of om over te schakelen op een ander beleid. Als een beheerder het beleid in bijlage aan het document schakelt, zal de naam van de Uitgever aan de naam van de eigenaar van het beleid worden bijgewerkt dat het laatst op het document wordt toegepast.

Op installatie van documentveiligheid, wordt een standaardbeleidsreeks gecreeerd genoemd *Globale Reeks van het Beleid*. Deze beleidsreeks wordt beheerd door de beheerder die de software of de coördinator van de beleidsreeks installeerde die voor deze beleidsreeks wordt aangewezen.

## Een beleidsset maken {#create-a-policy-set}

De globale Reeks van het Beleid is de enige standaardbeleidsreeks die op installatie wordt gecreeerd. U kunt aanvullende beleidssets maken en beleid, gebruikers, beleidssetcoördinatoren en documentuitgevers toevoegen. Nadat u een beleidsset hebt gemaakt, kunt u beleid maken in de set.

Tijdens het creëren van de beleidsreeks, kunt u de Achterknoop gebruiken om aan het vorige scherm terug te keren en sparen knoop om uw beleidsreeks op elk ogenblik te bewaren.

1. Voor de documentveiligheid, pagina, klik Beleid, klik het lusje van de Reeksen van het Beleid, en klik dan Nieuw.
1. Typ in het vak Naam een naam voor de beleidsset, typ desgewenst een beschrijving en klik op Volgende. De naam mag geen dubbele punt **:** bevatten.

   >[!NOTE]
   >
   >U kunt een naam van een beleidsset maken die uitgebreide tekens bevat. wanneer echter een vergelijking wordt gemaakt tussen twee tekenreeksen, worden tekens met en zonder accent, zoals &quot;e&quot; en &quot;é&quot;, als identiek beschouwd. Wanneer iemand een beleidsset maakt, wordt een vergelijking gemaakt om te controleren of al een beleidsset met dezelfde naam bestaat. De vergelijking kan geen onderscheid maken tussen namen die hetzelfde zijn, behalve voor tekens met accent. Aangenomen wordt dat de beleidsset al aan de database is toegevoegd en de nieuwe niet.

1. (Optioneel) Als u de domeinen wilt instellen die zichtbaar zijn voor documentuitgevers wanneer zij gebruikers aan een beleid toevoegen, klikt u op Domeinen toevoegen, selecteert u de domeinen die u wilt doorzoeken, klikt u op Toevoegen en klikt u vervolgens op OK.
1. Klik op de pagina Zichtbare gebruikers en groepen toevoegen op Volgende.
1. (Optioneel) Als u een beleidssetcoördinator wilt toevoegen, klikt u op Gebruikers en groepen toevoegen op de pagina Beleidssetcoördinator(s) toevoegen (stap 3 van 4) en voert u de volgende taken uit:

   * Typ de naam of het e-mailadres in het vak Zoeken.
   * Selecteer de gewenste optie in de lijst Gebruiken.
   * Selecteer in de lijst Type de optie Gebruiker en selecteer in de lijst In het domein dat u wilt zoeken.
   * Selecteer in de lijst Weergave het aantal resultaten dat per pagina moet worden weergegeven en klik op Zoeken.
   * Schakel het selectievakje in voor de gebruiker of groep die u wilt toevoegen en klik op Volgende.
   * Selecteer de bevoegdheden van de beleidssetcoördinator en klik op Toevoegen. De volgende machtigingen kunnen worden ingesteld:

      * Gebeurtenissen weergeven
      * Documenten beheren (toegang tot documenten intrekken en opnieuw instellen en het beleid voor documenten wijzigen)
      * Beleid beheren (beleid maken, bewerken en verwijderen)
      * Documentuitgevers beheren (documentuitgevers toevoegen en verwijderen)
      * Delegeren (beleidssetcoördinatoren toevoegen en verwijderen)

1. Herhaal stap 5 om meer beleidssetcoördinatoren toe te voegen.
1. Controleer de instellingen van de beleidssetcoördinator en klik op Volgende.
1. Klik op Gebruikers en groepen toevoegen om documentuitgevers toe te voegen die het beleid in de beleidsset kunnen gebruiken om documenten te beschermen.
1. Voer de volgende taken uit op de pagina Documentuitgevers toevoegen:

   * Typ de naam of het e-mailadres in het vak Zoeken.
   * Selecteer de gewenste optie in de lijst Gebruiken.
   * Selecteer in de lijst Type de optie Gebruiker en selecteer in de lijst In het domein dat u wilt zoeken.
   * Selecteer in de lijst Weergave het aantal resultaten dat per pagina moet worden weergegeven en klik op Zoeken.
   * Selecteer de selectievakjes voor de gebruikers en groepen die u wilt toevoegen, klik op Toevoegen en klik vervolgens op OK.

1. Klik op Opslaan.

U kunt nu beleid toevoegen aan uw beleidsset. (Zie [Beleid maken en bewerken](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).)

## Een beleidsset {#edit-a-policy-set} bewerken

1. Voor de documentveiligheid, pagina, klik Beleid, klik het lusje van de Reeksen van het Beleid, en klik de beleidreeks om uit te geven.
1. Klik op het desbetreffende tabblad en bewerk indien nodig:

   * **Details:de naam en beschrijving van de beleidsset** bewerken.
   * **Beleid:beleid** maken, inschakelen, bewerken en verwijderen binnen de beleidsset.
   * **Zichtbare gebruikers en groepen:zichtbare gebruikers en groepen** toevoegen en verwijderen die in een beleid kunnen worden opgenomen.
   * **Beleidssetcoördinatoren:machtigingen voor coördinatoren** toevoegen, verwijderen en wijzigen.
   * **Documentuitgevers:gebruikers** toevoegen en verwijderen die documenten kunnen publiceren met het beleid in de set.

1. Als u een zichtbare gebruiker of groep, beleidssetcoördinator of documentuitgever wilt verwijderen, klikt u op het desbetreffende tabblad, schakelt u het selectievakje voor de invoer in, klikt u op Verwijderen en klikt u vervolgens op OK.
1. Als u zichtbare gebruikers of groepen, een beleidssetcoördinator of documentuitgevers wilt toevoegen, klikt u op het desbetreffende tabblad, klikt u op Gebruikers of groepen toevoegen, zoekt u naar de gebruiker of groep die u wilt toevoegen, selecteert u het item, klikt u op Toevoegen en klikt u vervolgens op OK.
1. Zoek op het tabblad Beleid naar beleid dat u wilt toevoegen aan de beleidsset en maak nieuwe beleidsregels:

   * Als u naar een beleid wilt zoeken, selecteert u Beleids-id of Beleidsnaam, typt u de bijbehorende waarde, selecteert u het aantal items dat u wilt weergeven en klikt u op Zoeken.
   * Zie [Beleid maken en bewerken](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies) voor meer informatie over het maken van een nieuw beleid.

## Een beleidsset {#delete-a-policy-set} verwijderen

Wanneer u een beleidsset verwijdert, kunnen beleid dat deel uitmaakte van de set, niet worden toegepast op nieuwe documenten. Nochtans, kunt u de beleidsinformatie in zowel de beleidsconsole als de eindgebruikerWeb-pagina&#39;s voor beleid bekijken dat nog in gebruik is. U kunt de beleidsinformatie van de documentdetailpagina voor om het even welk document bekijken dat door het beleid wordt beschermd. Het beleid dat nog in gebruik is, kan worden bewerkt.

1. Klik op Beleid en klik op het tabblad Beleidssets.
1. Schakel het selectievakje in voor de beleidsset die u wilt verwijderen.
1. Klik op Verwijderen en vervolgens op OK.

