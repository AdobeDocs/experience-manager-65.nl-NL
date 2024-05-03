---
title: XFA-ondersteuning in op XDP gebaseerde adaptieve formulieren
description: Hier worden ondersteunde XFA-gebeurtenissen, -eigenschappen, -scripts en -validatie in adaptieve formulieren weergegeven.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 255be73f-3169-457c-aaa7-a2fb59f1f2cd
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '732'
ht-degree: 0%

---

# XFA-ondersteuning in op XDP gebaseerde adaptieve formulieren{#xfa-support-in-xdp-based-adaptive-forms}

## Inleiding {#introduction}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

Adaptieve formulieren ondersteunen diverse XFA-gebeurtenissen, -eigenschappen, -scripts en -validaties die zijn gedefinieerd in een XDP-bestand, zoals:

* Uitvoering van scripts gedefinieerd voor gebeurtenissen in het XDP-bestand.
* Standaardwaarden en gedragseigenschappen vastleggen voor velden in het XDP-bestand.
* Uitvoering van validatiescripts die zijn gedefinieerd in het XDP-bestand.

Wanneer een adaptief formulier wordt gemaakt op basis van een XDP-bestand, worden de eigenschappen, gebeurtenissen en validaties automatisch ingevuld in de gebruikersinterface van het formulierontwerp. Auteurs van formulieren kunnen sommige van deze elementen echter overschrijven om een andere ervaring te creëren.

Dit artikel bevat een lijst met ondersteunde XFA-gebeurtenissen, -eigenschappen en -validaties die in adaptieve formulieren worden ondersteund, en uitleg hoe u deze in adaptieve formulieren kunt overschrijven.

## Ondersteunde XFA-elementen en hun toewijzing in adaptieve formulieren {#supported-xfa-elements-and-their-mapping-in-adaptive-forms-br}

### Velden {#fields}

Wanneer een adaptief formulier wordt gemaakt met een XDP-bestand, kunt u een XFA-veld naar het adaptieve formulier slepen. In de volgende tabel wordt aangegeven hoe XFA-velden worden toegewezen aan adaptieve formuliervelden.

<table>
 <tbody>
  <tr>
   <td><p><strong>XFA veld of container</strong></p> </td>
   <td><p><strong>Overeenkomende adaptieve formuliercomponent</strong></p> </td>
  </tr>
  <tr>
   <td><p>Knop </p> </td>
   <td><p>Knop</p> </td>
  </tr>
  <tr>
   <td><p>Selectievakje </p> </td>
   <td><p>Selectievakje</p> </td>
  </tr>
  <tr>
   <td><p>Keuzelijst </p> </td>
   <td><p>Vervolgkeuzelijst</p> </td>
  </tr>
  <tr>
   <td><p>Datum-/tijdveld </p> </td>
   <td><p>Datumkiezer</p> </td>
  </tr>
  <tr>
   <td><p>Krabbelen op handtekening</p> </td>
   <td><p>Krabbelhandtekening</p> </td>
  </tr>
  <tr>
   <td><p>Numeriek veld </p> </td>
   <td><p>Numeriek vak</p> </td>
  </tr>
  <tr>
   <td><p>Decimaal veld</p> </td>
   <td><p>Numeriek vak</p> </td>
  </tr>
  <tr>
   <td><p>Tekstveld </p> </td>
   <td><p>Tekstvak</p> </td>
  </tr>
  <tr>
   <td><p>Wachtwoordveld </p> </td>
   <td><p>Wachtwoordvak</p> </td>
  </tr>
  <tr>
   <td><p>Afbeelding</p> </td>
   <td><p>Afbeelding</p> </td>
  </tr>
  <tr>
   <td><p>Tekst</p> </td>
   <td><p>Tekst</p> </td>
  </tr>
  <tr>
   <td><p>Subformulier </p> </td>
   <td><p>Deelvenster</p> </td>
  </tr>
  <tr>
   <td><p>Gebied (groep)</p> </td>
   <td><p>Deelvenster</p> </td>
  </tr>
  <tr>
   <td><p>Subformulierset </p> </td>
   <td><p>Deelvenster</p> </td>
  </tr>
 </tbody>
</table>

### Eigenschappen {#properties}

In de volgende tabel wordt vastgelegd hoe verschillende XFA-scripts die in de XDP-bestanden zijn gedefinieerd, zich gedragen in adaptieve formulieren.

<table>
 <tbody>
  <tr>
   <td><p><strong>Eigenschappen van XFA-componenten</strong></p> </td>
   <td><p><strong>Corresponsief gedrag in adaptieve formulieren</strong></p> </td>
  </tr>
  <tr>
   <td><p>somExpression </p> </td>
   <td><p>Toegewezen aan de eigenschap Bind reference (bindRef) in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>aanwezigheid </p> </td>
   <td><p>Toegewezen aan de eigenschap visible in adaptieve vorm. U kunt deze negeren met behulp van de zichtbaarheidsexpressie.</p> </td>
  </tr>
  <tr>
   <td><p>toegang </p> </td>
   <td><p>Toegewezen aan de eigenschap enabled in adaptieve vorm. U kunt het met de uitdrukking van de Toegang met voeten treden.</p> </td>
  </tr>
  <tr>
   <td><p>Toegankelijkheid: rol </p> </td>
   <td><p>Toegewezen aan de rolineigenschap in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>Toegankelijkheid: speakPriority </p> </td>
   <td><p>Toegewezen aan de eigenschap speakPriority in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>Toegankelijkheid: speakText</p> </td>
   <td><p>Toegewezen aan de aangepaste toegankelijkheidstekst in aangepaste vorm.</p> </td>
  </tr>
  <tr>
   <td><p>Toegankelijkheid: knopinfo </p> </td>
   <td><p>Toegewezen aan de korte beschrijvingseigenschap in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>bijschrift<em> (alle veldtypen)</em></p> </td>
   <td><p>Toegewezen aan de eigenschap Title in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>displayFormat<em> (alle veldtypen)</em></p> </td>
   <td><p>Wordt in adaptieve vorm toegewezen aan het weergavepatroon.</p> </td>
  </tr>
  <tr>
   <td><p>rawValue<em> (alle veldtypen)</em></p> </td>
   <td><p>Toegewezen aan waarde-eigenschap in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>items<em> (Keuzelijst, Selectievakje)</em></p> </td>
   <td><p>Eigenschap toegewezen aan opties in adaptieve vorm. U kunt deze negeren met de expressie Opties.</p> </td>
  </tr>
  <tr>
   <td><p>maxChar<em> (Tekstveld)</em></p> </td>
   <td><p>Toegewezen aan de eigenschap Maximum aantal tekens toegestaan in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>multiline<em> (Tekstveld)</em></p> </td>
   <td><p>Toegewezen aan de eigenschap Meerdere regels toestaan in aangepaste vorm.</p> </td>
  </tr>
  <tr>
   <td><p>fracDigit<em> (Numeriek veld, decimaal veld)</em></p> </td>
   <td><p>Toegewezen aan de eigenschap Frac digits in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>leadDigit<em> (Numeriek veld, decimaal veld)</em></p> </td>
   <td><p>Wordt in adaptieve vorm toegewezen aan de eigenschap Cijfers lead.</p> </td>
  </tr>
  <tr>
   <td><p>multiSelect<em> (Keuzelijst)</em></p> </td>
   <td><p>Toegewezen aan de eigenschap Meerdere selecties in aangepaste vorm toestaan.</p> </td>
  </tr>
 </tbody>
</table>

### Scripts {#scripts}

In de volgende tabel wordt vastgelegd hoe verschillende XFA-scripts die in het XDP-bestand zijn gedefinieerd, zich gedragen in adaptieve formulieren.

<table>
 <tbody>
  <tr>
   <td><p><strong>XFA-scriptgebeurtenissen</strong></p> </td>
   <td><p><strong>Corresponsief gedrag in adaptieve formulieren</strong></p> </td>
  </tr>
  <tr>
   <td><p>initialiseren </p> </td>
   <td><p>Dit script wordt uitgevoerd bij uitvoering en kan niet worden overschreven in de adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>berekenen</p> </td>
   <td><p>Toegewezen aan de expressie Berekenen in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>validate </p> </td>
   <td><p>Toegewezen aan de validatie-expressie in adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>validationState </p> </td>
   <td><p>Dit script wordt uitgevoerd bij uitvoering en kan niet worden overschreven in de adaptieve vorm.<br /> </p> </td>
  </tr>
  <tr>
   <td><p>exit </p> </td>
   <td><p>Dit script wordt uitgevoerd bij uitvoering en kan niet worden overschreven in de adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>klikken (knopvelden)</p> </td>
   <td><p>Toegewezen aan de klikuitdrukking van de knoop.</p> </td>
  </tr>
  <tr>
   <td><p>Ondersteuning voor serverscripts</p> </td>
   <td><p>Dit script wordt uitgevoerd bij uitvoering en kan niet worden overschreven in de adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>Ondersteuning voor webservices</p> </td>
   <td><p>Dit script wordt uitgevoerd bij uitvoering en kan niet worden overschreven in de adaptieve vorm.</p> </td>
  </tr>
  <tr>
   <td><p>Wijzigen (krabbelveld, keuzerondje, selectievakje)</p> </td>
   <td><p>Dit script wordt uitgevoerd bij uitvoering en kan niet worden overschreven in de adaptieve vorm.</p> </td>
  </tr>
 </tbody>
</table>

### Validaties {#validations}

In de volgende tabel wordt vastgelegd hoe XFA-validaties worden toegewezen aan validaties in adaptieve formulieren.

<table>
 <tbody>
  <tr>
   <td><p><strong>XFA-validatie</strong></p> </td>
   <td><p><strong>Overeenkomstige validatie in adaptieve vorm</strong></p> </td>
  </tr>
  <tr>
   <td><p>Validatiepatroon (formatTest)</p> </td>
   <td><p>validatePictureClause</p> </td>
  </tr>
  <tr>
   <td><p>Bericht van validatiepatroon (formatTestMessage)</p> </td>
   <td><p>validatePictureMessage</p> </td>
  </tr>
  <tr>
   <td><p>Vereist (nullTest)</p> </td>
   <td><p>verplicht </p> </td>
  </tr>
  <tr>
   <td><p>Leeg bericht (nullTestMessage) </p> </td>
   <td><p>mandatoryMessage</p> </td>
  </tr>
  <tr>
   <td><p>Script valideren (scriptTest)</p> </td>
   <td><p>validateExp</p> </td>
  </tr>
  <tr>
   <td><p>Bericht van validatiescript (scriptTestMessage)</p> </td>
   <td><p>validateMessage</p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>U kunt de verplichte eigenschap voor het adaptieve formulier keuzerondje en de groep selectievakjes die zijn gebonden aan XFA-knoppen, niet overschrijven.
