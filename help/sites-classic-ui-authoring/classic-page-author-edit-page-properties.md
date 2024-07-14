---
title: Pagina-eigenschappen bewerken
description: De eigenschappen van een pagina kunnen afhankelijk van de aard van de pagina variëren. Sommige pagina's kunnen bijvoorbeeld zijn verbonden met een live kopie, andere niet en de live kopie-informatie is op de juiste wijze beschikbaar.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
exl-id: 1a77e4cd-bbf8-4d05-bb35-fd43c02eaf30
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '760'
ht-degree: 0%

---

# Pagina-eigenschappen bewerken{#editing-page-properties}

U kunt de vereiste eigenschappen voor een pagina definiëren. Deze kunnen afhankelijk van de aard van de pagina variëren. Sommige pagina&#39;s kunnen bijvoorbeeld zijn verbonden met een live kopie, andere niet en de live kopie-informatie is op de juiste wijze beschikbaar.

## Pagina-eigenschappen {#page-properties}

De eigenschappen zijn verdeeld over verschillende tabbladen:

### Basis {#basic}

* **Titel**

  De titel van de pagina wordt op verschillende locaties weergegeven. Bijvoorbeeld, de **het tablijst van Websites** en de **3} kaart/lijstmeningen van Plaatsen {.**

  Dit is een verplicht veld.

* **Markeringen**

  Hier kunt u codes toevoegen aan of verwijderen uit de pagina door de lijst in het selectievak bij te werken:

   * Nadat u een tag hebt geselecteerd, wordt deze weergegeven onder het selectievak. U kunt een tag uit deze lijst verwijderen met de x.
   * U kunt een volledig nieuwe tag invoeren door de naam in een leeg selectievak te typen.

     De nieuwe tag wordt gemaakt wanneer u op Enter drukt. De nieuwe tag wordt dan weergegeven in een vak, met rechts een kleine ster die aangeeft dat het een nieuwe tag is.

   * Met de vervolgkeuzefunctie kunt u bestaande tags selecteren.
   * Er verschijnt een x wanneer u de muis boven een tag-item in het selectievak houdt. U kunt dit gebruiken om die tag voor deze pagina te verwijderen.

* **Verbergen in Navigatie**

  Een schakeloptie om aan te geven of de pagina wordt weergegeven of verborgen in de paginanavigatie.

* **Titel van de Pagina**

  Een titel die op de pagina moet worden gebruikt.

* **Titel van de Navigatie**

  U kunt een aparte titel opgeven voor gebruik in de navigatie (bijvoorbeeld als u iets beknopter wilt). Als leeg, wordt de **Titel** gebruikt.

* **Ondertitel**

  Een ondertitel voor gebruik op de pagina.

* **Beschrijving**

  Uw beschrijving van de pagina, het doel ervan of andere details die u wilt toevoegen.

* **op Tijd**

  De datum en het tijdstip waarop de gepubliceerde pagina wordt geactiveerd. Wanneer deze pagina wordt gepubliceerd, blijft deze sluimerend tot de opgegeven tijd.

  Laat deze velden leeg voor pagina&#39;s die u direct wilt publiceren (het normale scenario).

* **Van Tijd**

  De tijd waarop de gepubliceerde pagina wordt gedeactiveerd.

  Laat deze velden weer leeg voor pagina&#39;s die u direct wilt publiceren.

* **Vanity URL**

  Hiermee kunt u een vanity-URL voor deze pagina invoeren. Hierdoor hebt u een kortere en expressievere URL.

  Als bijvoorbeeld de URL van Vanity is ingesteld op w `elcome` op de pagina die wordt aangegeven door het pad / `v1.0/startpage` voor de website h `ttp://example.com,` , zou h `ttp://example.com/welcome` de vanity URL van h zijn `ttp://example.com/content/v1.0/startpage`

  >[!CAUTION]
  >
  >Vanity-URL&#39;s:
  >
  >* moet uniek zijn, dus zorg ervoor dat de waarde niet reeds door een andere pagina wordt gebruikt.
  >* regex-patronen niet ondersteunen.

* **Redirect Vanity URL**

  Hiermee geeft u aan of u wilt dat de pagina de vanity-URL gebruikt.

### Geavanceerd {#advanced}

* **Taal**

  De paginataal.

* **opnieuw richten**

  Geef de pagina op waarnaar deze pagina automatisch moet worden omgeleid.

* **Ontwerp**

  Wijs op het [ ontwerp ](/help/sites-developing/designer.md) dat voor deze pagina moet worden gebruikt.

* **Alias**

  Geef een alias op die voor deze pagina moet worden gebruikt.

* **laat Gesloten Groep van de Gebruiker toe**

  Laat (of maakt) gebruik van [ gesloten gebruikersgroepen ](/help/sites-administering/cug.md) (CUGs) toe onbruikbaar.

* **Login Pagina**

  De pagina die voor login moet worden gebruikt.

* **Toegestane Groepen**

  Groepen die in aanmerking komen voor aanmelding bij de CUG.

* **Realm**

  Realm name for the CUG.

* **de Configuratie van de Uitvoer**

  Geef een exportconfiguratie op.

### Miniatuur {#thumbnail}

* **de Duimnagel van de Pagina**

  Hiermee geeft u de miniatuurafbeelding van de pagina weer. U kunt:

   * **produceer Voorproef**

     Genereer een voorvertoning van de pagina die u als miniatuur wilt gebruiken.

   * **upload Beeld**

     Upload een afbeelding die u als miniatuur wilt gebruiken.

### Cloud Servicen {#cloud-services}

* **Cloud Servicen**

  Bepaal eigenschappen voor [ wolkendiensten ](/help/sites-developing/extending-cloud-config.md).

### Personalization {#personalization}

* **Personalization**

  Selecteer a [ Merk om een werkingsgebied voor het richten ](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md) te specificeren.

### Machtigingen {#permissions}

* **Toestemmingen** (aanraking-geoptimaliseerde UI)

  Bekijk de [ efficiënte toestemmingen en voeg nieuwe toestemmingen ](/help/sites-administering/user-group-ac-admin.md) toe.

### Blauwdruk {#blueprint}

* **Vervaging**

  Bepaal eigenschappen voor een pagina van de Vervaging binnen [ multi-site beheer ](/help/sites-administering/msm.md). Hiermee bepaalt u de omstandigheden waaronder wijzigingen worden doorgegeven aan Live kopie.

### Live kopie {#live-copy}

* **Livecopy**

  Bepaal eigenschappen voor een Levende pagina van het Exemplaar binnen [ multi-site beheer ](/help/sites-administering/msm.md). Hiermee bepaalt u de omstandigheden waaronder wijzigingen worden doorgegeven via het blauwdruk.

### Sitestructuur {#site-structure}

* Verstrek verbindingen aan pagina&#39;s die plaats-brede functionaliteit, zoals **pagina van de Aantekening**, **Off-line Pagina**, onder anderen verstrekken.

## Pagina-eigenschappen bewerken {#editing-page-properties-2}

### Pagina-eigenschappen bewerken voor een specifieke pagina {#editing-page-properties-for-a-specific-page}

Pagina-eigenschappen definiëren de verschillende eigenschappen van de pagina, zoals titels, wanneer deze op de website en andere titels worden weergegeven.

1. Open de pagina die u wilt bewerken.

1. In sidekick open het **lusje van de Pagina** dan selecteren **Eigenschappen van de Pagina...**

   Hiermee wordt een dialoogvenster met meerdere tabbladen geopend.

1. Breng de veranderingen aan u vereist, dan klik O.K. **om te bewaren.**
