---
title: '"Zelfstudie: Plan de Interactieve Communicatie"'
seo-title: Uw interactieve communicatie plannen
description: Plan de anatomie voor uw Interactieve Communicatie
seo-description: Plan de anatomie voor uw Interactieve Communicatie
uuid: 1c2b5c5b-c655-4559-8748-3e0b343779c2
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
discoiquuid: 75b2d424-91d3-45b4-a5d7-fb49ab558582
feature: Interactieve communicatie
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---


# Zelfstudie: Plan de Interactieve Communicatie {#tutorial-plan-the-interactive-communication}

Plan de anatomie voor uw Interactieve Communicatie

![02-create-adaptive-form-main-image](assets/02-create-adaptive-form-main-image.png)

Deze zelfstudie is een stap in de serie [Maak uw eerste interactieve communicatiemodellen](/help/forms/using/create-your-first-interactive-communication.md). U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

De eerste stap in het plannen van een Interactieve Mededeling is de inhoud van de Interactieve Mededeling te voltooien. Experts met onderwerpen van afdelingen zoals juridische afdeling, financiën, ondersteuning of marketing kunnen u helpen de inhoud te voltooien. Nadat de inhoud wordt voltooid, moet u het analyseren om de diverse activatypes te identificeren die worden vereist om de Interactieve Mededeling tot stand te brengen.

## Planningsoverwegingen {#planning-considerations}

Een interactieve communicatie omvat de volgende elementen:

* **Statische** tekst omvat vooral de delen van de interactieve mededeling die algemeen van aard zijn en in mededeling aan alle klanten inbegrepen zijn. Bijvoorbeeld kop-, voettekst-, aanhef- of disclaimers.
* **Gegevens die afkomstig zijn van een back-endsysteem (formuliergegevensmodel)** zijn klantspecifiek en worden dynamisch samengevoegd met de interactieve communicatie. Het beleidsnummer of adres kan bijvoorbeeld worden opgehaald aan de hand van het formuliergegevensmodel.
* **Lay-out of** malplaatjes voor de versie van de Druk en van het Web van de Interactieve Mededeling.
* **De volgorde** waarin de verschillende tekstalinea&#39;s worden weergegeven in de interactieve communicatie.
* **Gegevens ingegaan door een frontline werknemer (Agent UI)** die de mededeling alvorens het uit te verzenden aanpast. Bijvoorbeeld de vervaldatum van de betaling.

* **Voorwaardelijke** gegevens die worden gevuld op basis van vooraf gedefinieerde voorwaarden. Bijvoorbeeld de datum waarop de interactieve communicatie wordt gegenereerd.
* **Afbeeldingen die zijn opgeslagen in een opslagplaats**, zoals logo&#39;s en handtekeningafbeeldingen. Afbeeldingen zoals bedrijfslogo&#39;s worden in de meeste of alle interactieve communicatie weergegeven.
* **Grafieken en** tabellen die nodig zijn om de weergave van complexe gegevens in een interactieve communicatie te vereenvoudigen

## Anatomie van de interactieve communicatie {#anatomy-of-the-interactive-communication}

Zodra u de inhoud en de elementen hebt voltooid die worden gebruikt om uw Interactieve Mededeling tot stand te brengen, kunt u een anatomie van de Interactieve Communicatie tot stand brengen. De anatomie moet de details hebben die in [de sectie van de Overwegingen van de Planning ](/help/forms/using/planning-interactive-communications.md#planning-considerations) worden vermeld. Gebaseerd op ons gebruiksgeval, is het volgende een voorbeeld van een anatomie van de maandelijkse rekening die een telecomexploitant aan zijn klanten verzendt.

De anatomie bevat gegevens met de volgende invoermodi:

* Statische tekst
* Formuliergegevensmodel
* Gebruikersinterface van agent
* Voorwaardelijke gegevens
* Afbeeldingen

In elke sectie staat de vetgedrukte tekst voor statische tekst. Het gegevensbestand omvat klant, rekeningen, en vraaglijsten. Een formuliergegevensmodel kan gegevens uit al deze tabellen ontvangen. Zie [Formuliergegevensmodel maken](/help/forms/using/create-form-data-model0.md) voor meer informatie.

De volgende tabel illustreert de gegevensbron voor elk veld in de anatomie van interactieve communicatie:

<table>
 <tbody>
  <tr>
   <td>Sectie</td>
   <td>Statische tekst</td>
   <td>FDM </td>
   <td>Gebruikersinterface van agent</td>
   <td>Afbeeldingen</td>
  </tr>
  <tr>
   <td>Bill Details</td>
   <td><p>Factuurnummer</p> <p>Bill Date</p> <p>Bill Period</p> <p>Uw abonnement</p> </td>
   <td><p>Waarde voor <strong>Uw abonnement </strong>veld</p> <p>Tabel - klant</p> </td>
   <td><p>Waarden voor de volgende velden:</p>
    <ul>
     <li>Factuurnummer</li>
     <li>Bill Date</li>
     <li>Bill Period</li>
    </ul> <p> </p> </td>
   <td>—</td>
  </tr>
  <tr>
   <td>Klantgegevens</td>
   <td><p>Plaats van levering</p> <p>Statuscode</p> <p>Mobiel nummer</p> <p>Alternatief contactnummer</p> <p>Relatie-nummer</p> <p>Aantal verbindingen</p> </td>
   <td><p>Waarden voor de volgende velden:</p>
    <ul>
     <li>Naam</li>
     <li>Adres</li>
     <li>Mobiel nummer</li>
     <li>Alternatief contactnummer</li>
     <li>Relatie-nummer</li>
    </ul> <p>Tabel - klant</p> </td>
   <td><p>Waarden voor de volgende velden:</p>
    <ul>
     <li>Plaats van levering</li>
     <li>Statuscode</li>
     <li>Aantal verbindingen</li>
    </ul> </td>
   <td>—</td>
  </tr>
  <tr>
   <td>Bill Summary</td>
   <td><p>Vorig saldo</p> <p>Betalingen</p> <p>Aanpassingen</p> <p>Lopende factuurperiode</p> <p>Te betalen bedrag</p> <p>Vervaldatum</p> </td>
   <td><p>Waarde voor het veld <strong>Lopende factuurperiode </strong></p> <p>Tabel - rekeningen</p> </td>
   <td><p>Waarden voor de volgende velden:</p>
    <ul>
     <li>Vorig saldo</li>
     <li>Betalingen</li>
     <li>Aanpassingen</li>
     <li>Te betalen bedrag</li>
     <li>Vervaldatum</li>
    </ul> </td>
   <td>—</td>
  </tr>
  <tr>
   <td>Overzicht van kosten</td>
   <td><p>Oproepkosten</p> <p>Kosten voor conferentiegesprek</p> <p>SMS-kosten </p> <p>Mobiele internetkosten</p> <p>Nationale roamingkosten</p> <p>Internationale roamingkosten</p> <p>Kosten voor toegevoegde services</p> <p>Totale kosten</p> <p>TOTAAL BETAALBAAR</p> <p>Voorwaarde voor het veld Kosten toegevoegde services</p> </td>
   <td><p>Waarden voor de volgende velden:</p>
    <ul>
     <li>Oproepkosten</li>
     <li>Kosten voor conferentiegesprek</li>
     <li>SMS-kosten </li>
     <li>Mobiele internetkosten</li>
     <li>Nationale roamingkosten</li>
     <li>Internationale roamingkosten</li>
     <li>Kosten voor toegevoegde services</li>
     <li>Totale kosten (veld voor berekende gebruiksrechten)</li>
     <li>TOTAAL BETAALBAAR (veld gebruiksrechten berekend)</li>
    </ul> <p>Tabel - rekeningen</p> </td>
   <td>Geen velden</td>
   <td>—</td>
  </tr>
  <tr>
   <td>Gespecialiseerde vraag - Uitgaand</td>
   <td><p>Kolomnamen:</p>
    <ul>
     <li>Date</li>
     <li>Time</li>
     <li>Getal</li>
     <li>Duur</li>
     <li>Heffingen</li>
    </ul> </td>
   <td><p>Alle waarden</p> <p>Tabel - aanroepen</p> </td>
   <td>Geen velden</td>
   <td>—</td>
  </tr>
  <tr>
   <td>Nu betalen</td>
   <td>—</td>
   <td>—</td>
   <td>—</td>
   <td>Nu betalen</td>
  </tr>
  <tr>
   <td>Services voor toegevoegde waarde</td>
   <td>—</td>
   <td>—</td>
   <td>—</td>
   <td>ValueAddedServices</td>
  </tr>
 </tbody>
</table>

