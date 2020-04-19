---
title: Beveiligingsinstellingen configureren
seo-title: Beveiligingsinstellingen configureren
description: Leer hoe u beveiligingsinstellingen configureert.
seo-description: Leer hoe u beveiligingsinstellingen configureert.
uuid: 9747f268-3551-4064-8dba-e1de4a577843
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: a89ab508-173f-4b1c-88d9-ef944af4d9ae
translation-type: tm+mt
source-git-commit: 2cf9dcf2e9cf71c54e19e2c6ee825c9a8f00a9b7

---


# Beveiligingsinstellingen configureren{#configuring-security-settings}

U kunt de toegang tot PDF-documenten beperken door wachtwoorden in te stellen en bepaalde functies, zoals afdrukken en bewerken, te beperken. Wanneer voor een PDF-document beperkingen zijn ingesteld, worden gereedschappen en menu-items die daarmee samenhangen, grijs weergegeven. U kunt ook andere methoden gebruiken om beveiligde documenten te maken, zoals het versleutelen of certificeren van een document. Een beveiligingsinstelling bevat het wachtwoord en de specifieke opties die voor bepaalde PDF-conversies moeten worden gebruikt.

Op de pagina Beveiligingsinstellingen kunt u de volgende taken uitvoeren:

## Een beveiligingsinstelling maken of bewerken {#create-or-edit-a-security-setting}

Een *beveiligingsinstelling* bepaalt de beveiliging en machtigingen voor bestanden die met die beveiligingsinstelling worden omgezet.

1. Klik in de beheerconsole op Services > PDF Generator > Beveiligingsinstellingen.
1. Klik op Nieuw of klik op de naam van een beveiligingsinstelling.
1. Voer op de pagina Nieuwe beveiligingsinstelling/Beveiligingsinstelling bewerken de vereiste informatie voor de beveiligingsinstelling in. (Zie Instellingen voor [bestandstypen](/help/forms/using/admin-help/configuring-file-type-settings.md#configuring-file-type-settings)configureren.)
1. Klik op Opslaan en typ een naam voor de instelling in het dialoogvenster dat wordt weergegeven. Klik vervolgens op OK.

### Beveiligingsinstellingen {#security-settings}

Met deze instellingen configureert u de compatibiliteit en codering. Zie Een beveiligingsinstelling [maken of bewerken voor instructies over het openen van de lettertype-instellingen](configuring-security-settings.md#create-or-edit-a-security-setting).

**Compatibiliteit:** Hiermee stelt u het type versleuteling in voor het openen van een document dat met een wachtwoord is beveiligd. Bij de optie Acrobat 3.0 en hoger wordt een laag coderingsniveau gebruikt, maar bij de andere opties wordt een hoog coderingsniveau gebruikt:

**Acrobat 3.0 en hoger:** Gebruikt lage encryptie (40 beetje RC4).

**Acrobat 5.0 en hoger:** Gebruikt hoge encryptie (128 bits RC4).

**Acrobat 6.0 en hoger:** Gebruikt hoge encryptie (128 bits RC4). Met deze optie kunt u metagegevens inschakelen voor zoeken.

**Acrobat 7.0 en hoger:** Gebruikt hoge codering (128-bits AES). Met deze optie kunt u metagegevens inschakelen om alleen bestandsbijlagen te zoeken en te versleutelen.

**Acrobat 9.0 en hoger:** Gebruikt hoge codering (256-bits AES). Met deze optie kunt u metagegevens inschakelen om alleen bestandsbijlagen te zoeken en te versleutelen.

Een eerdere versie van Acrobat kan geen PDF-document openen met een hogere compatibiliteitsinstelling. Als u bijvoorbeeld de optie Acrobat 7.0 en hoger selecteert, kunt u het document niet openen in Acrobat 6.0 of lager.

Zorg ervoor dat het compatibiliteitsniveau consistent is met het PDF-compatibiliteitsniveau voor dezelfde bron. Als u bijvoorbeeld een controlemap hebt geconfigureerd voor het gebruik van de instelling Standaard-PDF, die compatibel is met Acrobat 5.0 of hoger, mag het niveau van de beveiligingscompatibiliteit niet hoger zijn dan Acrobat 5.0.

**Documentbeperking:** Welke documentbeperkingen beschikbaar zijn, is afhankelijk van de optie Compatibiliteit die u hebt geselecteerd.

**Geen versleuteling:** Hiermee wordt geen enkel deel van het document versleuteld.

**Alle inhoud van het document versleutelen:** Hiermee worden het document en de metagegevens van het document gecodeerd. Als deze optie is geselecteerd, hebben zoekprogramma&#39;s geen toegang tot de metagegevens van het document.

**Alle inhoud van het document versleutelen, behalve metagegevens (compatibel met Acrobat6 en hoger):** Hiermee wordt de inhoud van een document gecodeerd, maar zijn de metagegevens van het document nog wel toegankelijk voor zoekfuncties. Deze optie is alleen beschikbaar als de optie Compatibiliteit is ingesteld op Acrobat 6.0 of hoger, Acrobat 7.0 of hoger of Acrobat 9.0 of hoger.

**Alleen bestandsbijlagen versleutelen (compatibel met Acrobat 7 en hoger):** Gebruikers kunnen het document zonder wachtwoord openen, maar moeten een wachtwoord invoeren om bestandsbijlagen te openen. Deze optie is alleen beschikbaar als de optie Compatibiliteit is ingesteld op Acrobat 7.0 of hoger of op Acrobat 9.0 of hoger.

Met deze instellingen configureert u de wachtwoordbeveiliging:

>[!NOTE]
>
>Als u een wachtwoord bent vergeten, kan dit niet uit het document worden hersteld. Het wordt aanbevolen wachtwoorden op een andere beveiligde locatie op te slaan voor het geval u ze vergeet. Bewaar bovendien een reservekopie van het document dat niet met een wachtwoord is beveiligd.

**Wachtwoord vereist om document te openen:** Hiermee schakelt u de wachtwoordopties in.

**Wachtwoord voor document openen:** Hiermee voorkomt u dat gebruikers het document kunnen openen, tenzij ze het door u opgegeven wachtwoord invoeren. Wachtwoorden zijn hoofdlettergevoelig. Acrobat gebruikt de RC4-beveiligingsmethode van RSA Security Inc. om PDF-documenten met een wachtwoord te beveiligen. Als u afdrukken en bewerken beperkt, kunt u het beste een wachtwoord voor het openen van documenten toevoegen om de beveiliging te verbeteren.

**Typ het wachtwoord voor het openen van het document opnieuw:** Hiermee zorgt u ervoor dat het wachtwoord voor het openen van het document correct is.

**Wachtwoord vereisen voor het openen van bestandsbijlagen:** Hiermee schakelt u de wachtwoordopties in. Deze optie is alleen beschikbaar als de optie Compatibiliteit is ingesteld op Acrobat 7.0 of hoger of op Acrobat 9.0 of hoger en de optie Documentbeperking is ingesteld op Alleen bestandsbijlagen versleutelen.

**Wachtwoord voor het openen van bestandsbijlagen:** Hiermee zorgt u ervoor dat een wachtwoord is vereist om een bestandsbijlage te openen. Gebruikers kunnen het document zonder wachtwoord openen. Deze optie is alleen beschikbaar als de optie Compatibiliteit is ingesteld op Acrobat 7.0 of hoger of op Acrobat 9.0 of hoger en de optie Documentbeperking is ingesteld op Alleen bestandsbijlagen versleutelen.

**Bestandsbijlage opnieuw typen:** Hiermee zorgt u ervoor dat het wachtwoord juist is. Deze optie is alleen beschikbaar als de optie Compatibiliteit is ingesteld op Acrobat 7.0 of hoger of op Acrobat 9.0 of hoger en de optie Documentbeperking is ingesteld op Alleen bestandsbijlagen versleutelen.

Met deze opties configureert u de machtigingen:

**Gebruik een wachtwoord om het afdrukken en bewerken van het document en de beveiligingsinstellingen te beperken:** Hiermee worden beperkingen op machtigingen ingeschakeld.

**Wachtwoord voor machtigingen:** Hiermee beperkt u gebruikers tot afdrukken en bewerken. Gebruikers kunnen deze beveiligingsinstellingen alleen wijzigen als zij het door u opgegeven wachtwoord invoeren. U kunt niet hetzelfde wachtwoord gebruiken als voor het wachtwoord om het document te openen. Wanneer u een wachtwoord voor machtigingen instelt, kunnen alleen die personen die dat wachtwoord invoeren, beveiligingsinstellingen wijzigen. Als het PDF-document beide typen wachtwoorden heeft, wordt het geopend met een van beide wachtwoorden. Een gebruiker kan de beperkte functies echter alleen instellen of wijzigen met het wachtwoord voor machtigingen. Als het PDF-document alleen het wachtwoord voor machtigingen heeft of als een gebruiker het document opent met het wachtwoord om het document te openen, wordt een wachtwoord weergegeven wanneer de gebruiker beveiligingsinstellingen probeert te wijzigen.

**Wachtwoord voor machtigingen opnieuw invoeren:** Hiermee zorgt u ervoor dat het wachtwoord voor machtigingen correct is.

**Afdrukken toegestaan:** Hiermee geeft u de afdrukkwaliteit voor het PDF-document op:

**Geen:** Voorkomt dat gebruikers het document afdrukken.

**Lage resolutie (150 dpi):** Gebruikers kunnen het document afdrukken met een resolutie die niet hoger is dan 150 dpi. Het afdrukken kan langzamer zijn omdat elke pagina als een bitmapafbeelding wordt afgedrukt. Deze optie is alleen beschikbaar als u een hoog versleutelingsniveau hebt geselecteerd (Acrobat 5.0, 6.0, 7.0 of 9.0).

**Hoge resolutie:** Gebruikers kunnen met elke resolutie afdrukken, waarbij vectoruitvoer van hoge kwaliteit wordt afgedrukt op PostScript-printers en andere printers die geavanceerde functies voor hoge afdrukkwaliteit ondersteunen.

**Wijzigingen toegestaan:** Hiermee definieert u welke bewerkhandelingen zijn toegestaan in het PDF-document:

**Geen:** Hiermee voorkomt u dat gebruikers het document wijzigen, inclusief het invullen van handtekeningen en formuliervelden.

**Pagina&#39;s invoegen, verwijderen en roteren:** Gebruikers kunnen pagina&#39;s invoegen, verwijderen en roteren en bladwijzers en miniatuurpagina&#39;s maken. Deze optie is alleen beschikbaar als u een hoog versleutelingsniveau hebt geselecteerd (Acrobat 5.0, 6.0, 7.0 of 9.0).

**Formuliervelden invullen en bestaande SignatureFields ondertekenen:** Gebruikers kunnen formulieren invullen en digitale handtekeningen toevoegen. Gebruikers kunnen echter geen opmerkingen toevoegen of formuliervelden maken. Deze optie is alleen beschikbaar als u een hoog versleutelingsniveau hebt geselecteerd (Acrobat 5.0, 6.0, 7.0 of 9.0).

**Opmerkingen plaatsen, formuliervelden invullen en bestaande handtekeningvelden ondertekenen:** Gebruikers kunnen formulieren invullen en digitale handtekeningen en opmerkingen toevoegen.

**Pagina-indeling, retoucheren, formuliervelden invullen en bestaande handtekeningvelden ondertekenen:** Gebruikers kunnen pagina&#39;s invoegen, roteren of verwijderen en bladwijzers of miniatuurafbeeldingen maken, formulieren invullen en digitale handtekeningen toevoegen. Met deze optie kunnen gebruikers geen formuliervelden maken. Deze optie is alleen beschikbaar als u een laag coderingsniveau (Acrobat 3.0) hebt geselecteerd.

**Alles behalve pagina&#39;s uitnemen:** Hiermee kunnen gebruikers het document wijzigen met een methode in de lijst Wijzigingen toegestaan, behalve door pagina&#39;s te verwijderen.

**Kopiëren van tekst, afbeeldingen en andere inhoud inschakelen:** Gebruikers kunnen de inhoud van het PDF-document selecteren en kopiëren. Ook kunnen hulpprogramma&#39;s die toegang nodig hebben tot de inhoud van een PDF-bestand, zoals Acrobat Catalog, toegang krijgen tot deze inhoud. Deze optie is alleen beschikbaar als een hoog versleutelingsniveau is geselecteerd.

**Tekstweergave van slechtzienden op schermlezers inschakelen:** Hiermee kunnen gebruikers met een visuele handicap het document lezen met schermlezers. Gebruikers kunnen de documentinhoud echter niet kopiëren of uitpakken. Deze optie is alleen beschikbaar als een hoog versleutelingsniveau is geselecteerd.

## Een beveiligingsinstelling verwijderen {#delete-a-security-setting}

U kunt een beveiligingsinstelling verwijderen als deze niet meer vereist is. Voorgeconfigureerde beveiligingsinstellingen kunnen echter niet worden verwijderd.

1. Klik in de beheerconsole op **[!UICONTROL Services > PDF Generator > Beveiligingsinstellingen]**.
1. Schakel het selectievakje naast de instelling die u wilt verwijderen in. U kunt meerdere instellingen selecteren.
1. Klik op **[!UICONTROL Verwijderen]** en klik nogmaals op de pagina **[!UICONTROL Bevestiging]** verwijderen **** .

