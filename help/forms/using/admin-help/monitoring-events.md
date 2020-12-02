---
title: Gebeurtenissen controleren
seo-title: Gebeurtenissen controleren
description: Wanneer de controlefunctie is ingeschakeld, kunt u met documentbeveiliging bepaalde typen gebeurtenissen controleren. U kunt de gebeurtenissenlijst eenvoudig zoeken en sorteren met behulp van de documentbeveiliging.
seo-description: Wanneer de controlefunctie is ingeschakeld, kunt u met documentbeveiliging bepaalde typen gebeurtenissen controleren. U kunt de gebeurtenissenlijst eenvoudig zoeken en sorteren met behulp van de documentbeveiliging.
uuid: 22add6ff-536d-4cb9-8eac-b72cad5c3ecf
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 379957bf-0634-4182-b269-1b010da4c90f
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7
workflow-type: tm+mt
source-wordcount: '989'
ht-degree: 0%

---


# Gebeurtenissen {#monitoring-events} controleren

Wanneer de controlefunctie is ingeschakeld, kunt u met documentbeveiliging bepaalde typen gebeurtenissen controleren. De gebeurtenissen die u kunt zien zijn afhankelijk van uw rol:

**Gebruikers:** kunnen gecontroleerde gebeurtenissen weergeven voor documenten die door hun beleid zijn beveiligd en voor beveiligde documenten die zij ontvangen en gebruiken.

**Beleidssetcoördinatoren:** Kan gecontroleerde gebeurtenissen, waaronder document- en beleidsgebeurtenissen, weergeven voor documenten die door beleid worden beschermd tegen hun beleidssets.

**Beheerders:** kan gecontroleerde gebeurtenissen weergeven die betrekking hebben op alle documenten en gebruikers die met een beleid zijn beveiligd. Beheerders kunnen ook andere gebeurtenistypen bijhouden, zoals gebruiker, document, beleid en systeemgebeurtenissen.

>[!NOTE]
>
>Gebeurtenissen die worden uitgevoerd op een kopie van een document dat met een beleid is beveiligd, worden ook als gebeurtenissen bijgehouden in het originele beveiligde document.

(Zie [Opties voor gebeurteniscontrole](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options).)

Een mislukte gebeurtenis wordt geregistreerd als een onbevoegde gebruiker probeert om een document te bekijken of probeert om binnen het gebruiken van een onjuiste gebruikersnaam of een wachtwoord te registreren.

>[!NOTE]
>
>De mislukte anonieme toegangsgebeurtenissen voor documenten kunnen worden geregistreerd als een beleid wordt uitgegeven om anonieme toegang te verwijderen. Wanneer een geautoriseerde ontvanger toegang probeert te krijgen tot een document dat door het bewerkte beleid wordt beveiligd, wordt anonieme toegang nog steeds geprobeerd maar mislukt.

Als een beleid anonieme gebruikerstoegang toestaat maar de beheerder later anonieme toegang voor documentveiligheid uitschakelt, zal de anonieme toegang voor documenten ontbreken die met het beleid worden beschermd en de gebeurtenis zal niet worden geregistreerd.

## Gebeurteniscontrole {#enable-event-auditing} inschakelen

Aan deze instellingsvereisten moet worden voldaan om gebeurteniscontrole uit te voeren:

* Het systeem of de beheerder moet het controlevermogen voor de server toelaten.

   (Zie [Gebeurteniscontrole en privacy-instellingen configureren](/help/forms/using/admin-help/configuring-client-server-options.md#configuring-event-auditing-and-privacy-settings).)

* Voor het beleid dat u gebruikt om het document te beveiligen, moet controle zijn ingeschakeld. (Zie [Beleid maken en bewerken](/help/forms/using/admin-help/creating-policies.md#creating-and-editing-policies).)

## Zoeken naar een gebeurtenis {#search-for-an-event}

U kunt de gebeurtenissenlijst doorzoeken en meer gedetailleerde beschrijvingen van gebeurtenissen weergeven. De gedetailleerde beschrijvingen bevatten informatie zoals de gebeurtenis-id, beschrijving, IP-adres, organisatie, beïnvloede gebruiker, datum en tijd waarop de gebeurtenis heeft plaatsgevonden, ontkende activiteiten en offlinegebeurtenissen (wanneer gebruikers proberen een document te gebruiken wanneer ze geen verbinding hebben met documentbeveiliging).

U kunt naar gebeurtenissen op de pagina Gebeurtenissen zoeken met een combinatie van zoekcriteria voor gebeurtenissen en de datums waarop de gebeurtenissen hebben plaatsgevonden. Welke gebeurtenissen u kunt zoeken, is afhankelijk van uw rol:

**Gebruikers:** kunnen gecontroleerde gebeurtenissen weergeven voor documenten die door hun beleid zijn beveiligd en voor beveiligde documenten die zij ontvangen en gebruiken. Deze zoekopties zijn beschikbaar:

**Gebeurtenissen met betrekking tot mij:** gebruikers kunnen gebeurtenissen vinden voor elk document dat met een beleid is beveiligd en dat ze hebben gemaakt of ontvangen. Als een gebruiker bijvoorbeeld een document opent, weergeeft of afdrukt dat door een andere persoon is beveiligd, ziet de gebruiker alleen deze gebeurtenissen voor dat document.

**Gebeurtenissen met betrekking tot mijn documenten:** gebruikers kunnen alle gebeurtenissen vinden die betrekking hebben op hun eigen documenten die met een beleid zijn beveiligd. De gebruikers zien de gebeurtenissen die door elke persoon worden geproduceerd die hun documenten behandelde.

**Beleidssetcoördinatoren:** Kan gecontroleerde gebeurtenissen, waaronder document- en beleidsgebeurtenissen, weergeven voor documenten die door beleid worden beschermd tegen hun beleidssets. De volgende opties zijn beschikbaar:

**Documentgebeurtenissen waarbij ik coördinator ben van een beleidsset:** Beleidssetcoördinatoren die de machtiging voor weergavegebeurtenissen hebben, kunnen gebeurtenissen vinden die betrekking hebben op documenten die door het beleid van hun beleidssets worden beveiligd.

**Beleidsgebeurtenissen waarbij ik een beleidssetcoördinator ben:** Beleidssetcoördinatoren die de machtiging voor weergavegebeurtenissen hebben, kunnen gebeurtenissen vinden die gerelateerd zijn aan beleid vanuit hun beleidssets.

**Beheerders:** kan gecontroleerde gebeurtenissen weergeven die betrekking hebben op alle documenten en gebruikers die met een beleid zijn beveiligd. Beheerders kunnen ook andere typen bijhouden. Ook kunnen beheerders zoekopdrachten naar gebeurtenissen verder onderverdelen op basis van het type gebruiker:

**Bekende gebruikers:** Gebruikers bevinden zich in de brondirectory&#39;s of zijn geregistreerd als externe gebruikers.

**Anonieme gebruikers:** Onbekende gebruikers die toegang hebben tot een document dat is beveiligd met een beleid dat anonieme toegang toestaat.

**Systeemgebruikers:** Server-gestarte gebeurtenissen, zoals een foldersynchronisatie.

1. Klik op Gebeurtenissen op de pagina Documentbeveiliging.
1. Selecteer in de lijst Zoeken de zoekcriteria die u wilt gebruiken. Afhankelijk van de selectie in de lijst Zoeken wordt een tweede lijst weergegeven met aanvullende zoekcriteria. Typ, indien van toepassing, in het tekstvak de zoekcriteria.

   Zie [Opties voor gebeurteniscontrole](/help/forms/using/admin-help/configuring-client-server-options.md#event-auditing-options) voor meer informatie over de specifieke gebeurtenistypen.

1. Selecteer in de lijst Gebruiker het gebruikerstype dat de gebeurtenis heeft uitgevoerd:

   * Als u Bekende Gebruiker selecteert, wordt een tweede onderzoeksvakje getoond, waar u de gebruikersnaam of e-mailadres van de gebruiker moet typen.
   * Als u deze waarden niet kent, klikt u op het zoekpictogram in het adresboek om naar de gebruiker te zoeken op basis van de gebruikersnaam of het e-mailadres.

1. Selecteer in de lijst Datum een optie voor het datumbereik. Als u Aangepaste datums selecteert, worden vakken weergegeven waarin u de datum typt in de notatie jjjj/mm/dd of u kunt de Datumkiezer gebruiken om het datumbereik op te geven:

   * Klik op de kalender om de Datumkiezer te openen.
   * Gebruik de pijlen om een jaar en een maand te vinden.
   * Klik op een dag van de maand in de kalender.
   * Klik op OK om de Datumkiezer te sluiten.

1. Selecteer in de lijst Weergave het aantal zoekresultaten dat per pagina moet worden weergegeven.
1. Klik op Zoeken.

   Eventuele mislukte gebeurtenissen worden in de lijst gemarkeerd met een afgewezen pictogram.

1. Klik op de beschrijving van de gebeurtenis in de lijst om de details van een gebeurtenis weer te geven.

## De gebeurtenislijst {#sort-the-event-list} sorteren

U kunt de gebeurtenissenlijst sorteren op kolomkop om gebeurtenissen gemakkelijker te vinden. De driehoekspictogrammen naast de kolomkop geven aan welke kolom momenteel wordt gebruikt om te sorteren. Een naar boven wijzend driehoekje geeft de oplopende volgorde aan, terwijl een naar beneden wijzend driehoekje de aflopende volgorde aangeeft.

1. Klik op de gewenste kolomkop.
1. Klik nogmaals op de kolomkop om de sorteervolgorde te wijzigen.

