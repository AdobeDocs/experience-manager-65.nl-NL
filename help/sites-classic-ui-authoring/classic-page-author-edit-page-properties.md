---
title: Pagina-eigenschappen bewerken
seo-title: Pagina-eigenschappen bewerken
description: De eigenschappen van een pagina kunnen afhankelijk van de aard van de pagina variëren. Sommige pagina's kunnen bijvoorbeeld zijn verbonden met een live kopie, andere niet en de live kopie-informatie is beschikbaar, indien van toepassing.
seo-description: De eigenschappen van een pagina kunnen afhankelijk van de aard van de pagina variëren. Sommige pagina's kunnen bijvoorbeeld zijn verbonden met een live kopie, andere niet en de live kopie-informatie is beschikbaar, indien van toepassing.
uuid: 63d37d1b-52da-489d-b02b-e8b3d17571d1
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 23768c73-ac64-4727-8313-160c8c131b05
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Pagina-eigenschappen bewerken{#editing-page-properties}

U kunt de vereiste eigenschappen voor een pagina definiëren. Deze kunnen afhankelijk van de aard van de pagina variëren. Sommige pagina&#39;s kunnen bijvoorbeeld zijn verbonden met een live kopie, andere niet en de live kopie-informatie is beschikbaar, indien van toepassing.

## Pagina-eigenschappen {#page-properties}

De eigenschappen zijn verdeeld over verschillende tabbladen:

### Basis {#basic}

* **Titel**

   De titel van de pagina wordt op verschillende locaties weergegeven. Bijvoorbeeld de lijst op het tabblad **Websites** en de weergave van de **Sites** -kaart/lijst.

   Dit is een verplicht veld.

* **Tags**

   Hier kunt u codes toevoegen aan of verwijderen uit de pagina door de lijst in het selectievak bij te werken:

   * Nadat u een tag hebt geselecteerd, wordt deze weergegeven onder het selectievak. U kunt een tag uit deze lijst verwijderen met de x.
   * U kunt een volledig nieuwe tag invoeren door de naam in een leeg selectievak te typen.

      De nieuwe tag wordt gemaakt wanneer u op Enter drukt. De nieuwe tag wordt dan weergegeven in een vak, met rechts een kleine ster die aangeeft dat het een nieuwe tag is.

   * Met de vervolgkeuzefunctie kunt u bestaande tags selecteren.
   * Een x wordt weergegeven wanneer u de muis boven een tagitem in het selectievak houdt. U kunt deze optie gebruiken om die tag voor deze pagina te verwijderen.

* **Verbergen in navigatie**

   Een schakeloptie om aan te geven of de pagina wordt weergegeven of verborgen in de paginanavigatie.

* **Paginatitel**

   Een titel die op de pagina moet worden gebruikt.

* **Navigatietitel**

   U kunt een aparte titel opgeven voor gebruik in de navigatie (bijvoorbeeld als u iets beknopter wilt). Als de waarde leeg is, wordt de **titel** gebruikt.

* **Ondertitel**

   Een ondertitel voor gebruik op de pagina.

* **Beschrijving**

   Uw beschrijving van de pagina, het doel ervan of andere details die u wilt toevoegen.

* **Op tijd**

   De datum en het tijdstip waarop de gepubliceerde pagina wordt geactiveerd. Wanneer deze pagina wordt gepubliceerd, blijft deze slapend tot de opgegeven tijd.

   Laat deze velden leeg voor pagina&#39;s die u direct wilt publiceren (het normale scenario).

* **Uit-tijd**

   De tijd waarop de gepubliceerde pagina wordt gedeactiveerd.

   Laat deze velden weer leeg voor pagina&#39;s die u direct wilt publiceren.

* **Vanity URL**

   Hiermee kunt u een vanity-URL voor deze pagina invoeren. Hierdoor hebt u een kortere en expressievere URL.

   Als bijvoorbeeld de URL van Vanity is ingesteld op w `elcome`op de pagina die wordt aangegeven door het pad/ `v1.0/startpage`voor de website h, `ttp://example.com,` zou dat de ijdeloze URL van h `ttp://example.com/welcome`zijn `ttp://example.com/content/v1.0/startpage`

   >[!CAUTION]
   >
   >Vanity-URL&#39;s:
   >
   >* moet uniek zijn, dus zorg ervoor dat de waarde niet reeds door een andere pagina wordt gebruikt.
   >* bieden geen ondersteuning voor regex-patronen.


* **Redirect Vanity URL**

   Hiermee geeft u aan of u wilt dat de pagina de vanity-URL gebruikt.

### Geavanceerd {#advanced}

* **Taal**

   De paginataal.

* **Omleiden**

   Geef de pagina op waarnaar deze pagina automatisch moet worden omgeleid.

* **Ontwerp**

   Geef het [ontwerp](/help/sites-developing/designer.md) op dat voor deze pagina moet worden gebruikt.

* **Alias**

   Geef een alias op die voor deze pagina moet worden gebruikt.

* **Gesloten gebruikersgroep inschakelen**

   Hiermee wordt het gebruik van [gesloten gebruikersgroepen](/help/sites-administering/cug.md) (CUG&#39;s) ingeschakeld (of uitgeschakeld).

* **Aanmeldingspagina**

   De pagina die voor login moet worden gebruikt.

* **Toegestane groepen**

   Groepen die in aanmerking komen voor aanmelding bij de CUG.

* **Realm**

   Realm name for the CUG.

* **Configuratie exporteren**

   Geef een exportconfiguratie op.

### Miniatuur {#thumbnail}

* **Paginaminiatuur**

   Hiermee geeft u de miniatuurafbeelding van de pagina weer. U kunt:

   * **Voorvertoning genereren**

      Genereer een voorvertoning van de pagina die u als miniatuur wilt gebruiken.

   * **Afbeelding uploaden**

      Upload een afbeelding die u als miniatuur wilt gebruiken.

### Cloud Services {#cloud-services}

* **Cloud Services**

   Eigenschappen definiëren voor [cloudservices](/help/sites-developing/extending-cloud-config.md).

### Personalisatie {#personalization}

* **Personalisatie**

   Selecteer een [merk om een bereik voor het instellen van doelen](/help/sites-classic-ui-authoring/classic-personalization-campaigns.md)op te geven.

### Permissions {#permissions}

* **Machtigingen** (interface met aanraakgeoptimaliseerde interface)

   Bekijk de [effectieve machtigingen en voeg nieuwe machtigingen](/help/sites-administering/user-group-ac-admin.md)toe.

### Blauwdruk {#blueprint}

* **Blauwdruk**

   Definieer eigenschappen voor een pagina Vervagen binnen [beheer](/help/sites-administering/msm.md)met meerdere sites. Hiermee bepaalt u de omstandigheden waaronder wijzigingen worden doorgegeven aan Live kopie.

### Live kopie {#live-copy}

* **Livecopy**

   Definieer eigenschappen voor een Live Copy-pagina in [beheer](/help/sites-administering/msm.md)met meerdere sites. Hiermee bepaalt u de omstandigheden waaronder wijzigingen worden doorgegeven via het blauwdruk.

### Sitestructuur {#site-structure}

* Koppelingen maken naar pagina&#39;s die voor de hele site functionaliteit bieden, zoals **Aanmeldingspagina**, **Offline pagina**.

## Pagina-eigenschappen bewerken {#editing-page-properties-2}

### Pagina-eigenschappen bewerken voor een specifieke pagina {#editing-page-properties-for-a-specific-page}

Pagina-eigenschappen definiëren de verschillende eigenschappen van de pagina, zoals titels, wanneer deze op de website en andere titels worden weergegeven.

1. Open de pagina die u wilt bewerken.

1. Open in het zijpaneel het tabblad **Pagina** en selecteer **Pagina-eigenschappen...**

   Hiermee wordt een dialoogvenster met meerdere tabbladen geopend.

1. Breng de gewenste wijzigingen aan en klik op **OK** om op te slaan.

