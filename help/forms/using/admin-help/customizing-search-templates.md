---
title: Zoeksjablonen aanpassen
description: U kunt zoeksjablonen maken die in Workspace worden gebruikt om te zoeken naar varianten van processen op de pagina's Aan en Volgen. U kunt ook bestaande zoeksjablonen bewerken of verwijderen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_workspace
products: SG_EXPERIENCEMANAGER/6.5/FORMS
exl-id: bf69de86-2ca6-4d21-936c-07c1debacfa0
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 6a9806d8f40f711a610c130c63d9ab9b2460d075
workflow-type: tm+mt
source-wordcount: '867'
ht-degree: 0%

---

# Zoeksjablonen aanpassen {#customizing-search-templates}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

U kunt zoeksjablonen maken die in Workspace worden gebruikt om te zoeken naar varianten van processen op de pagina&#39;s Aan en Volgen. U kunt ook bestaande zoeksjablonen bewerken of verwijderen.

Wanneer u een zoeksjabloon maakt of bewerkt, kunt u de indeling en sorteervolgorde van de zoekresultaten opgeven. Gebruikers kunnen deze instellingen echter wijzigen in Workspace nadat de zoekresultaten zijn weergegeven.

U kunt zo veel zoeksjablonen maken als u wilt.

>[!NOTE]
>
>Wanneer u een zoeksjabloon opslaat, moet u deze een unieke naam geven. Anders kan een bestaande sjabloon zonder waarschuwingsbericht worden overschreven.

## Een eenvoudige zoeksjabloon maken {#create-a-simple-search-template}

1. Klik in de beheerconsole op Services > Workspace > Sjablonen zoeken.
1. Geef op het tabblad Identificatie in het vak Beschrijving van zoeksjabloon het doel van de sjabloon op.
1. (Optioneel) Klik op het tabblad Criteria en geef de zoekcriteria voor de sjabloon op.
1. Klik op het tabblad Opslaan, voer een unieke naam voor de sjabloon in en klik op Opslaan.

## Een zoeksjabloon maken of bewerken {#create-or-edit-a-search-template}

1. Klik in de beheerconsole op Services > Workspace > Sjablonen zoeken.
1. (Optioneel) Als u een bestaande sjabloon bewerkt of een bestaande sjabloon gebruikt als basis voor een nieuwe sjabloon, selecteert u de sjabloon in de lijst Sjabloonnaam zoeken.
1. Geef in het vak Beschrijving van zoeksjabloon het doel van de sjabloon op.
1. (Optioneel) Geef in het vak Gebruikersinstructies instructies op die u kunnen helpen bij het gebruik van de sjabloon. Deze instructies worden weergegeven in Workspace wanneer een gebruiker de zoeksjabloon selecteert.
1. Klik op het tabblad Criteria. Hier definieert u een of meer zoekcriteria. Een zoekcriterium toevoegen:

   * Selecteer boven aan het tabblad Criteria een proceselement of taakelement.

     **Uiteinde**: *als u eerder het element van de Naam van het Proces selecteerde en een proces specificeerde, zijn om het even welke Variabelen van het Proces die in dat proces worden bepaald ook beschikbaar voor selectie.*

     **Uiteinde**: *als u het Zichtbare element van de Taak selecteert, zullen de gebruikers voltooide taken uit de onderzoeksresultaten kunnen verwijderen.*

     De velden met zoekcriteria voor het geselecteerde element staan onder aan het tabblad Criteria.

   * Vul voor elk proceselement, elk taakelement en elke procesvariabele die u selecteert de bijbehorende zoekvelden onder aan het tabblad Criteria in:

      * Selecteer een relationele operator (bijvoorbeeld &quot;gelijk aan&quot;) in de opgegeven lijst en geef de waarde van de operand op in het vak ernaast.
      * (Optioneel) Als u wilt dat gebruikers de operandwaarde in Workspace kunnen wijzigen, selecteert u Toestaan dat de gebruiker de operand wijzigt.
      * (Optioneel) Als u gebruikers wilt toestaan de relationele operator te wijzigen, selecteert u Toestaan dat de gebruiker een andere relationele operator selecteert. Selecteer in de lijst die wordt weergegeven de operatoren die beschikbaar zijn voor de gebruiker.

     **Uiteinde**: *als u de Naam van het Proces als element selecteerde, kunt u het pictogram naast het operandgebied klikken om een lijst te tonen waar u een proces kunt selecteren dat op de Server van Forms loopt. Na het selecteren van een proces, zijn om het even welke procesvariabelen die in dat proces worden bepaald beschikbaar voor selectie onder de Variabelen van het Proces in de hoogste sectie van het lusje van Criteria.*

     **Uiteinde**: *u kunt een element van het onderzoeksmalplaatje schrappen door het pictogram van de Schrapping naast de het onderzoekscriteria van het element te klikken.*

1. (Optioneel) Klik op het tabblad Lay-out voor elke kolomkop die in de zoekresultaten moet worden weergegeven en voer de volgende stappen uit:

   * Selecteer een proces- of taakelement en klik op de pijl-rechts om dit naar de lijst Kolommen te rapporteren te verplaatsen.
   * Selecteer in de lijst Kolommen die u wilt rapporteren het proces- of taakelement en klik op de pijl-omhoog of pijl-omlaag om dit naar de gewenste plaats in de kolomvolgorde te verplaatsen. De kolomkoppen in de zoekresultaten worden weergegeven in de volgorde waarin ze hier worden vermeld.
   * (Optioneel) Als u de naam van het element voor de kolomkop wilt wijzigen, selecteert u het element in de lijst Te rapporteren kolommen en geeft u de nieuwe naam op.

   >[!NOTE]
   >
   >De indeling die in de zoeksjabloon is opgegeven, heeft voorrang op de gebruikersvoorkeuren die in Workspace voor kolomkoppen zijn opgegeven.

1. (Optioneel) Klik op het tabblad Sorteren voor elke kolom die u in de zoekresultaten wilt sorteren en voer de volgende stappen uit:

   * Selecteer een proces- of taakelement en klik op de pijl-rechts om dit naar de lijst Sorteervolgorde te verplaatsen.
   * Selecteer het proces- of taakelement in de lijst Sorteervolgorde en klik op Pijl-omhoog of Pijl-omlaag om het element in de sorteervolgorde te verplaatsen. De kolommen in de zoekresultaten worden gesorteerd op basis van de volgorde waarin ze hier worden weergegeven.
   * (Optioneel) Als u een kolom in aflopende volgorde wilt sorteren, schakelt u het selectievakje naast de elementnaam in. Als het selectievakje niet is ingeschakeld, wordt de kolom in oplopende volgorde gesorteerd.

1. Klik op het tabblad Opslaan.
1. (Optioneel) Geef een zoeksjabloon een unieke naam. Als u geen unieke naam opgeeft, kunt u een bestaande sjabloon overschrijven.
1. Klik op Opslaan.

## Een zoeksjabloon verwijderen {#delete-a-search-template}

1. Selecteer op het tabblad Identificatie een naam in de lijst Naam zoeksjabloon.
1. Klik op Deze sjabloon verwijderen en klik op OK.
