---
title: Beveiligingsinstellingen configureren
description: Leer hoe u beveiligingsinstellingen configureert. U kunt PDF documenten beschermen door de toegang te beperken. U kunt het document versleutelen, certificeren of met een wachtwoord beveiligen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator,Document Security
exl-id: be076477-2681-4570-953d-6c44d3c30843
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '1421'
ht-degree: 0%

---

# Beveiligingsinstellingen configureren{#configuring-security-settings}

U kunt de toegang tot PDF-documenten beperken door wachtwoorden in te stellen en bepaalde functies, zoals afdrukken en bewerken, te beperken. Wanneer voor een PDF-document beperkingen zijn ingesteld, worden gereedschappen en menu-items die daarmee samenhangen, grijs weergegeven. U kunt ook andere methoden gebruiken om beveiligde documenten te maken, zoals het versleutelen of certificeren van een document. Een beveiligingsinstelling bevat het wachtwoord en de specifieke opties die voor bepaalde PDF-conversies moeten worden gebruikt.

Op de pagina Beveiligingsinstellingen kunt u de volgende taken uitvoeren:

## Een beveiligingsinstelling maken of bewerken {#create-or-edit-a-security-setting}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

A *veiligheid die* plaatst controleert de veiligheid en de toestemmingen voor dossiers die met dat veiligheid het plaatsen worden omgezet.

1. Klik in de beheerconsole op Services > PDF Generator > Beveiligingsinstellingen.
1. Klik op Nieuw of klik op de naam van een beveiligingsinstelling.
1. Voer op de pagina Nieuwe beveiligingsinstelling/Beveiligingsinstelling bewerken de vereiste informatie voor de beveiligingsinstelling in. (Zie [ Vormend dossiertype montages ](/help/forms/using/admin-help/configuring-file-type-settings.md#configuring-file-type-settings).)
1. Klik op Opslaan en typ een naam voor de instelling in het dialoogvenster dat wordt weergegeven. Klik vervolgens op OK.

### Beveiligingsinstellingen {#security-settings}

Met deze instellingen configureert u de compatibiliteit en codering. Voor instructies over de toegang tot van de doopvonten montages, zie [ creeer of geef een veiligheid uit die ](configuring-security-settings.md#create-or-edit-a-security-setting) plaatst.

**Verenigbaarheid:** plaatst het type van encryptie voor het openen van een wachtwoord-beschermd document. Bij de optie Acrobat 3.0 en hoger wordt een laag coderingsniveau gebruikt, maar bij de andere opties wordt een hoog coderingsniveau gebruikt:

**Acrobat 3.0 en later:** gebruikt lage encryptie (40 beetje RC4).

**Acrobat 5.0 en later:** gebruikt hoge encryptie (128 beetje RC4).

**Acrobat 6.0 en later:** gebruikt hoge encryptie (128 beetje RC4). Met deze optie kunt u metagegevens inschakelen voor zoeken.

**Acrobat 7.0 en later:** gebruikt hoge encryptie (128 beetje AES). Met deze optie kunt u metagegevens inschakelen om alleen bestandsbijlagen te zoeken en te versleutelen.

**Acrobat 9.0 en later:** gebruikt hoge encryptie (256 beetje AES). Met deze optie kunt u metagegevens inschakelen om alleen bestandsbijlagen te zoeken en te versleutelen.

In een eerdere versie van Acrobat kan geen PDF-document met een hogere compatibiliteitsinstelling worden geopend. Als u bijvoorbeeld de optie Acrobat 7.0 en hoger selecteert, kunt u het document niet openen in Acrobat 6.0 of eerder.

Zorg ervoor dat het compatibiliteitsniveau consistent is met het compatibiliteitsniveau PDF voor dezelfde bron. Als u bijvoorbeeld een controlemap hebt geconfigureerd voor het gebruik van de instelling Standaard PDF, die compatibel is met Acrobat 5.0 of hoger, mag het compatibiliteitsniveau voor de beveiliging niet hoger zijn dan Acrobat 5.0.

**de Beperking van het Document:** de documentbeperkingen die beschikbaar zijn hangen van de optie van de Verenigbaarheid af u selecteerde.

**Geen Encryptie:** codeert geen deel van het document.

**codeer Alle Inhoud van het Document:** codeert het document en de documentmeta-gegevens. Als deze optie is geselecteerd, hebben zoekfuncties geen toegang tot de metagegevens van het document.

**codeer alle inhoud van het Document behalve Meta-gegevens (Acrobat
6 en hoger (compatibel):** Codeert de inhoud van een document maar staat zoekprogramma&#39;s toch toe om de metagegevens van het document te openen. Deze optie is alleen beschikbaar als de optie Compatibiliteit is ingesteld op Acrobat 6.0 of hoger, Acrobat 7.0 of hoger of Acrobat 9.0 of hoger.

**slechts de gehechtheid van het Dossier (Acrobat 7 en later) coderen
(Compatibel):** Gebruikers kunnen het document zonder wachtwoord openen, maar moeten een wachtwoord invoeren om bestandsbijlagen te openen. Deze optie is alleen beschikbaar als de optie Compatibiliteit is ingesteld op Acrobat 7.0 of hoger of op Acrobat 9.0 of hoger.

Met deze instellingen configureert u de wachtwoordbeveiliging:

>[!NOTE]
>
>Als u een wachtwoord bent vergeten, kan dit niet uit het document worden hersteld. Het wordt aanbevolen wachtwoorden op een andere beveiligde locatie op te slaan voor het geval u ze vergeet. Bewaar bovendien een reservekopie van het document dat niet met een wachtwoord is beveiligd.

**vereist een Wachtwoord om het Document te openen:** laat de wachtwoordopties toe.

**Wachtwoord van het Document Open:** verhindert gebruikers het document te openen tenzij zij het wachtwoord typen u specificeert. Wachtwoorden zijn hoofdlettergevoelig. Acrobat gebruikt de RC4 methode van veiligheid van de Veiligheid Inc. van RSA aan wachtwoord-beschermt de documenten van PDF. Als u afdrukken en bewerken beperkt, kunt u het beste een wachtwoord voor het openen van documenten toevoegen om de beveiliging te verbeteren.

**het Wachtwoord van het Document van Retype Open:** zorgt ervoor dat het document open wachtwoord correct is.

**vereist een Wachtwoord om de Bijlagen van het Dossier te openen:** laat de wachtwoordopties toe. Deze optie is alleen beschikbaar als de optie Compatibiliteit is ingesteld op Acrobat 7.0 of hoger of op Acrobat 9.0 of hoger en de optie Documentbeperking is ingesteld op Alleen bestandsbijlagen versleutelen.

**Wachtwoord van het Open van de Bijlage van het Dossier:** zorgt ervoor dat een wachtwoord wordt vereist om een dossiergehechtheid te openen. Gebruikers kunnen het document zonder wachtwoord openen. Deze optie is alleen beschikbaar als de optie Compatibiliteit is ingesteld op Acrobat 7.0 of hoger of op Acrobat 9.0 of hoger en de optie Documentbeperking is ingesteld op Alleen bestandsbijlagen versleutelen.

**de Bijlage van het Dossier van Retype:** zorgt ervoor dat het wachtwoord correct is. Deze optie is alleen beschikbaar als de optie Compatibiliteit is ingesteld op Acrobat 7.0 of hoger of op Acrobat 9.0 of hoger en de optie Documentbeperking is ingesteld op Alleen bestandsbijlagen versleutelen.

Met deze opties configureert u de machtigingen:

**gebruik een wachtwoord om het drukken en het uitgeven van te beperken
Het Document en zijn Montages van de Veiligheid:** laat beperkingen op toestemmingen toe.

**Wachtwoord van Toestemmingen:** beperkt gebruikers van druk en het uitgeven. Gebruikers kunnen deze beveiligingsinstellingen alleen wijzigen als zij het door u opgegeven wachtwoord invoeren. U kunt niet hetzelfde wachtwoord gebruiken als voor het wachtwoord om het document te openen. Wanneer u een wachtwoord voor machtigingen instelt, kunnen alleen die personen die dat wachtwoord invoeren, beveiligingsinstellingen wijzigen. Als het PDF-document beide typen wachtwoorden heeft, wordt het geopend door een van beide wachtwoorden. Een gebruiker kan de beperkte functies echter alleen instellen of wijzigen met het wachtwoord voor machtigingen. Als het PDF-document alleen het wachtwoord voor machtigingen heeft of als een gebruiker het document opent met het wachtwoord om het document te openen, wordt een wachtwoord weergegeven wanneer de gebruiker beveiligingsinstellingen probeert te wijzigen.

**het Wachtwoord van de Toestemmingen van Retype:** zorgt ervoor dat het toestemmingenwachtwoord correct is.

**toegelaten het Afdrukken:** specificeert de kwaliteit van druk voor het document van de PDF:

**niets:** verhindert gebruikers het document te drukken.

**Lage Resolutie (150 dpi):** laat gebruikers het document bij geen hoger dan resolutie 150-dpi drukken. Het afdrukken kan langzamer zijn omdat elke pagina als een bitmapafbeelding wordt afgedrukt. Deze optie is alleen beschikbaar als een hoog versleutelingsniveau is geselecteerd (Acrobat 5.0, 6.0, 7.0 of 9.0).

**Hoge Resolutie:** laat gebruikers bij om het even welke resolutie drukken, richtend vectoroutput van uitstekende kwaliteit aan PostScript en andere printers die geavanceerde high-quality drukeigenschappen steunen.

**Toegelaten Veranderingen:** bepaalt welke het uitgeven acties in het document van de PDF worden toegestaan:

**niets:** verhindert gebruikers het document, met inbegrip van het vullen van handtekening en vormgebieden te veranderen.

**het Invoegen, het Schrappen, en het Roteren Pagina&#39;s:** laat gebruikers invoegen, schrappen, en roteren pagina&#39;s, en tot referenties en duimnagelpagina&#39;s leiden. Deze optie is alleen beschikbaar als een hoog versleutelingsniveau is geselecteerd (Acrobat 5.0, 6.0, 7.0 of 9.0).

**Formuliervelden invullen en bestaande handtekening ondertekenen
Velden:** Hiermee kunnen gebruikers formulieren invullen en digitale handtekeningen toevoegen. Gebruikers kunnen echter geen opmerkingen toevoegen of formuliervelden maken. Deze optie is alleen beschikbaar als een hoog versleutelingsniveau is geselecteerd (Acrobat 5.0, 6.0, 7.0 of 9.0).

**commentaren, het invullen van vormgebieden, en het ondertekenen van bestaand
Handtekeningvelden:** hiermee kunnen gebruikers formulieren invullen en digitale handtekeningen en opmerkingen toevoegen.

**de Lay-out van de pagina, het aanraken, het invullen van vormgebieden en het ondertekenen
Bestaande handtekeningvelden:** hiermee kunnen gebruikers pagina&#39;s invoegen, roteren of verwijderen en bladwijzers of miniatuurafbeeldingen maken, formulieren invullen en digitale handtekeningen toevoegen. Met deze optie kunnen gebruikers geen formuliervelden maken. Deze optie is alleen beschikbaar als een laag coderingsniveau (Acrobat 3.0) is geselecteerd.

**om het even welk behalve het Uitpakken van Pagina&#39;s:** laat gebruikers het document veranderen door om het even welke methode in de Lijst van gewenste personen van Veranderingen te gebruiken, behalve verwijdert pagina&#39;s.

**laat het Kopiëren van Tekst, Beelden, en Andere inhoud toe:** laat gebruikers de inhoud van het document van de PDF selecteren en kopiëren. Ook kunnen hulpprogramma&#39;s die toegang nodig hebben tot de inhoud van een PDF-bestand, zoals Acrobat Catalog, toegang krijgen tot die inhoud. Deze optie is alleen beschikbaar als een hoog versleutelingsniveau is geselecteerd.

**laat teksttoegang van de Apparaten van de Reader van het Scherm voor toe
Visueel beperkt:** laat gebruikers met een visuele handicap het document lezen door schermlezers te gebruiken. Gebruikers kunnen de documentinhoud echter niet kopiëren of uitpakken. Deze optie is alleen beschikbaar als een hoog versleutelingsniveau is geselecteerd.

## Een beveiligingsinstelling verwijderen {#delete-a-security-setting}

U kunt een beveiligingsinstelling verwijderen als deze niet meer vereist is. Voorgeconfigureerde beveiligingsinstellingen kunnen echter niet worden verwijderd.

1. Klik in de beheerconsole op **[!UICONTROL Services > PDF Generator > Security Settings]** .
1. Schakel het selectievakje naast de instelling die u wilt verwijderen in. U kunt meerdere instellingen selecteren.
1. Klik op **[!UICONTROL Delete]** en klik nogmaals op de **[!UICONTROL Delete Confirmation]** pagina **[!UICONTROL Delete]** .
