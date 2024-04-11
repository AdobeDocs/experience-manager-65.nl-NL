---
title: Eigenschappen van inhoudspagina bewerken
description: Definieer de vereiste eigenschappen voor een pagina in Adobe Experience Manager.
exl-id: 3cd9374f-6f16-40fb-97cf-5f9a750b8dd2
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '1855'
ht-degree: 1%

---

# Pagina-eigenschappen bewerken{#editing-page-properties}

U kunt de vereiste eigenschappen voor een pagina definiëren. Deze kunnen afhankelijk van de aard van de pagina variëren. Sommige pagina&#39;s kunnen bijvoorbeeld zijn verbonden met een live kopie, andere niet en de live kopieergegevens worden beschikbaar, indien van toepassing.

## Pagina-eigenschappen {#page-properties}

De eigenschappen worden verdeeld over verscheidene lusjes.

### Basis {#basic}

* **Titel**

  De titel van de pagina wordt op verschillende locaties weergegeven. Bijvoorbeeld de **Websites** en de **Sites** kaart-/lijstweergaven.

  Dit is een verplicht veld.

* **Tags**

  Hier kunt u codes toevoegen aan of verwijderen uit de pagina door de lijst in het selectievak bij te werken:

   * Nadat u een tag hebt geselecteerd, wordt deze weergegeven onder het selectievak. U kunt een tag uit deze lijst verwijderen met de x.
   * U kunt een nieuwe tag invoeren door de naam in een leeg selectievak te typen.

      * De nieuwe tag wordt gemaakt wanneer u op Enter drukt.
      * De nieuwe tag wordt weergegeven met een kleine ster aan de rechterkant die aangeeft dat het een nieuwe tag is.

   * Met de vervolgkeuzefunctie kunt u bestaande tags selecteren.
   * Een x wordt weergegeven wanneer u met de muis over een tag-item in het selectievak beweegt. Hiermee kunt u die tag voor deze pagina verwijderen.

  Zie voor meer informatie over tags [Tags gebruiken](/help/sites-authoring/tags.md).

* **Verbergen in navigatie**

  Geeft aan of de pagina wordt weergegeven of verborgen in de paginanavigatie van de resulterende site.

* **Branding**

  Pas een consistente merkidentiteit toe op de verschillende pagina&#39;s door een merkmarkering aan elke paginatitel toe te voegen. Voor deze functionaliteit is het gebruik van de component Pagina vanaf versie 2.14.0 of hoger van het dialoogvenster [Core Components.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html)

   * **Negeren** - Schakel dit selectievakje in om de merkwitruimte op deze pagina te definiëren.
      * De waarde wordt overgeërfd door onderliggende pagina&#39;s, tenzij deze ook hun **Negeren** ingestelde waarden.
   * **Waarde overschrijven** - De tekst van de merkmarkering die aan de paginatitel moet worden toegevoegd.
      * De waarde wordt toegevoegd aan de paginatitel na een pipe-teken, zoals &quot;Cycling Tuscany&quot; | Altijd klaar voor de WKND&quot;
* **Paginatitel**

  Een titel die op de pagina moet worden gebruikt. Wordt meestal gebruikt door titelcomponenten. Indien leeg, **Titel** wordt gebruikt.

* **Navigatietitel**

  U kunt een aparte titel opgeven voor gebruik in de navigatie (bijvoorbeeld als u iets beknopter wilt). Indien leeg, **Titel** wordt gebruikt.

* **Ondertitel**

  Een ondertitel voor gebruik op de pagina.

* **Beschrijving**

  Uw beschrijving van de pagina, het doel of andere details die u wilt toevoegen.

* **Op tijd**

  De datum en tijd waarop de gepubliceerde pagina wordt geactiveerd. Wanneer deze pagina wordt gepubliceerd, blijft deze sluimerend tot de opgegeven tijd.

  Laat deze velden leeg voor pagina&#39;s die u direct wilt publiceren (het normale scenario).

* **Uit-tijd**

  De tijd waarop de gepubliceerde pagina wordt gedeactiveerd.

  Laat deze velden weer leeg voor directe actie.

* **Vanity URL**

  Voer een vanity-URL voor deze pagina in, zodat u een kortere en/of meer expressieve URL kunt gebruiken.

  Als bijvoorbeeld de URL voor Vanity is ingesteld op `welcome`naar de pagina die wordt aangeduid door het pad `/v1.0/startpage`voor de website `http://example.com,` dan `http://example.com/welcome`zou de vanzelf-URL zijn van `http://example.com/content/v1.0/startpage`

  >[!CAUTION]
  >
  >Vanity-URL&#39;s:
  >
  >* Moet uniek zijn. Zorg ervoor dat de waarde nog niet door een andere pagina wordt gebruikt.
  >* Geen ondersteuning voor regex-patronen.
  >* Deze mag niet op een bestaande pagina worden ingesteld.
  >

  Configureer Dispatcher om toegang tot vanity URL&#39;s in te schakelen. Zie [Toegang tot URL&#39;s met Vanity inschakelen](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#enabling-access-to-vanity-urls-vanity-urls) voor meer informatie .

* **Redirect Vanity URL**

  Hiermee geeft u aan of u wilt dat de pagina de vanity-URL gebruikt.

### Geavanceerd {#advanced}

* **Taal**

  De paginataal.

* **Taalbasis**

  Moet worden gecontroleerd als de pagina de wortel van een taalexemplaar is.

* **Omleiden**

  Geef de pagina op waarnaar deze pagina automatisch moet worden omgeleid.

* **Ontwerp**

  Geef de [ontwerp](/help/sites-developing/designer.md) voor deze pagina te gebruiken.

* **Alias**

  Geef een alias op die voor deze pagina moet worden gebruikt.

   * Als u bijvoorbeeld een alias definieert van `private` voor de pagina `/content/wknd/us/en/magazine/members-only`, kan deze pagina ook worden geopend via `/content/wknd/us/en/magazine/private`
   * Het creëren van een aliasreeksen `sling:alias` eigenschap op het paginaknooppunt, die alleen invloed heeft op de bron, niet op het pad naar de opslagplaats.
   * Pagina&#39;s die door aliassen in de editor worden benaderd, kunnen niet worden gepubliceerd. [Publicatieopties](/help/sites-authoring/publishing-pages.md) in de editor zijn alleen beschikbaar voor pagina&#39;s die via hun werkelijke paden worden benaderd.
   * Zie voor meer informatie [Gelokaliseerde paginanamen onder SEO- en URL-beheertips](/help/managing/seo-and-url-management.md#localized-page-names).

* **Overgenomen van &lt;*pad*>**

  Geeft aan of de pagina wordt overgeërfd. en waar van.

* **Cloud Configuration**

  Het pad naar de configuratie.

* **Toegestane sjablonen**

  [De lijst met beschikbare sjablonen definiëren](/help/sites-authoring/templates.md#allowingatemplate) binnen dit subbijkantoor.

* **Inschakelen** (Verificatievereiste)

  Schakel het gebruik van verificatie in (of uit), zodat u toegang kunt krijgen tot de pagina.

  >[!NOTE]
  >
  >Gesloten gebruikersgroepen voor de pagina worden gedefinieerd op de **[Machtigingen](/help/sites-authoring/editing-page-properties.md#permissions)** tab.

  >[!CAUTION]
  >
  >De **[Machtigingen](/help/sites-authoring/editing-page-properties.md#main-pars-procedure-949394300)** kunt u op basis van de aanwezigheid van de `granite:AuthenticationRequired` mixin. Als de paginamachtigingen gebruikend verouderde configuraties van de KUG worden gevormd, gebaseerd op de aanwezigheid van `cq:cugEnabled` eigenschap, wordt een waarschuwing weergegeven onder **Verificatievereiste** en de optie kan niet worden bewerkt, en de optie [Machtigingen](/help/sites-authoring/editing-page-properties.md#permissions) bewerkbaar.
  >
  >
  >In dat geval moeten de CUG-machtigingen worden bewerkt in het dialoogvenster [klassieke gebruikersinterface](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md).

* **Aanmeldingspagina**

  De pagina die voor login moet worden gebruikt.

* **Configuratie exporteren**

  Geef een exportconfiguratie op.

### Miniatuur {#thumbnail}

Hiermee geeft u de miniatuurafbeelding van de pagina weer. U kunt:

* **Voorvertoning genereren**

  Genereer een voorvertoning van de pagina die u als miniatuur wilt gebruiken.

* **Afbeelding uploaden**

  Upload een afbeelding die u als miniatuur wilt gebruiken.

* **Afbeelding selecteren**

  Selecteer een bestaand element dat u als miniatuur wilt gebruiken.

* **Vorige versie**

  Deze optie wordt beschikbaar nadat u de miniatuur hebt gewijzigd. Als u de wijziging niet wilt behouden, kunt u die wijziging herstellen voordat u de wijziging opslaat.

### Sociale media {#social-media}

* **Delen via sociale media**

  Definieert de opties voor delen die beschikbaar zijn op de pagina. Hiermee worden de opties beschikbaar voor de [De kerncomponent delen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/sharing.html).

   * **Delen door gebruikers voor Facebook inschakelen**
   * **Delen door gebruikers voor Pinterest inschakelen**
   * **Voorkeurswijziging XF**
Variatie van ervaringsfragment definiëren die wordt gebruikt voor het genereren van metagegevens voor een pagina

### Cloud Servicen {#cloud-services}

* **Cloud Servicen**

  Eigenschappen definiëren voor [cloudservices](/help/sites-developing/extending-cloud-config.md).

### Personalisatie {#personalization}

* **ContextHub-configuraties**

  Selecteer de [ContextHub-configuratie](/help/sites-developing/ch-configuring.md) en [Segmentpad](/help/sites-administering/segmentation.md).

* **Doelconfiguratie**

  Selecteer een [Merk om een werkingsgebied voor het richten te specificeren](/help/sites-authoring/target-adobe-campaign.md).

  >[!NOTE]
  >Deze optie vereist dat de gebruikersaccount zich in de `Target Adminstrators`groep.

### Machtigingen {#permissions}

* **Machtigingen**

  Op dit tabblad kunt u het volgende doen:

   * [Machtigingen toevoegen](/help/sites-administering/user-group-ac-admin.md)
   * [Gesloten gebruikersgroep bewerken](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)

   * De weergave [Effectieve machtigingen](/help/sites-administering/user-group-ac-admin.md)

  >[!CAUTION]
  >
  >De **Machtigingen** kunt u op basis van de aanwezigheid van de `granite:AuthenticationRequired` mixin. Als de paginamachtigingen gebruikend verouderde configuraties van de KUG worden gevormd, gebaseerd op de aanwezigheid van `cq:cugEnabled` eigenschap, wordt een waarschuwingsbericht weergegeven en de CUG-machtigingen kunnen niet worden bewerkt, en de verificatievereiste geldt ook voor het [Geavanceerd](/help/sites-authoring/editing-page-properties.md#advanced) bewerkbaar tabblad.
  >
  >
  >In dat geval moeten de CUG-machtigingen worden bewerkt in het dialoogvenster [klassieke gebruikersinterface](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md).

  >[!NOTE]
  >
  >Het lusje van Toestemmingen staat niet de verwezenlijking van lege groepen CUG toe, die als eenvoudige manier kunnen nuttig zijn om toegang tot elke gebruiker te ontkennen. Hiervoor moet CRX Explorer worden gebruikt. Zie het document [Gebruiker, Groep en het Beleid van de Rechten van de Toegang](/help/sites-administering/user-group-ac-admin.md) voor meer informatie .

### Blauwdruk {#blueprint}

* **Blauwdruk**

  Eigenschappen definiëren voor een pagina Vervagen in [beheer op meerdere locaties](/help/sites-administering/msm.md). Hiermee bepaalt u de omstandigheden waaronder wijzigingen worden doorgegeven aan Live kopie.

### Live kopie {#live-copy}

* **Livecopy**

  Eigenschappen definiëren voor een pagina van Live kopie binnen [beheer op meerdere locaties](/help/sites-administering/msm.md). Hiermee bepaalt u de omstandigheden waaronder wijzigingen worden doorgegeven vanuit het deelvenster Vervagen.

### Sitestructuur {#site-structure}

* Koppelingen maken naar pagina&#39;s die functionaliteit voor de hele site bieden, zoals **Aanmeldingspagina**, **Offline pagina**, onder andere.

## Pagina-eigenschappen bewerken {#editing-page-properties-1}

U kunt pagina-eigenschappen definiëren:

* Van de **Sites** console:

   * [Een pagina maken](/help/sites-authoring/managing-pages.md#creating-a-new-page) (een subset van de eigenschappen)

   * Klikken of tikken **Eigenschappen**

      * Voor één pagina
      * Voor meerdere pagina&#39;s (alleen een subset van de eigenschappen is beschikbaar voor massabewerking)

* Vanuit de pagina-editor:

   * **Pagina-informatie** gebruiken (en vervolgens **Eigenschappen openen**)

### Vanuit de siteconsole - Eén pagina {#from-the-sites-console-single-page}

Klikken of tikken **Eigenschappen** om de pagina-eigenschappen te definiëren:

1. Met de **Sites** navigeer naar de locatie van de pagina waarvan u de eigenschappen wilt weergeven en bewerken.

1. Selecteer de **Eigenschappen** optie voor de vereiste pagina met behulp van:

   * [Snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-authoring/basic-handling.md#selectionmode)

   De pagina-eigenschappen worden weergegeven met de juiste tabbladen.

1. Bekijk of bewerk de eigenschappen naar wens.

1. Gebruik vervolgens **Opslaan** om uw updates op te slaan, gevolgd door **Sluiten** zodat kunt u aan de console terugkeren.

### Bij het bewerken van een pagina {#when-editing-a-page}

Wanneer u een pagina bewerkt, kunt u **Pagina-informatie** om de pagina-eigenschappen te definiëren:

1. Open de pagina waarvan u de eigenschappen wilt bewerken.

1. Selecteer de **Pagina-informatie** pictogram om het selectiemenu te openen:

   ![screen_shot_2018-03-22at095740](assets/screen_shot_2018-03-22at095740.png)

1. Selecteren **Eigenschappen openen** en er wordt een dialoogvenster geopend waarin u de eigenschappen kunt bewerken, gesorteerd op het juiste tabblad. De volgende knoppen zijn ook beschikbaar aan de rechterkant van de werkbalk:

   * **Annuleren**
   * **Opslaan en sluiten**

1. Gebruik de **Opslaan en sluiten** om de wijzigingen op te slaan.

### Van de Console van Plaatsen - Meerdere Pagina&#39;s {#from-the-sites-console-multiple-pages}

Van de **Sites** console, kunt u verscheidene pagina&#39;s selecteren dan gebruiken **Eigenschappen weergeven** om de pagina-eigenschappen weer te geven en/of te bewerken. Dit wordt het bulkgewijs bewerken van pagina-eigenschappen genoemd.

>[!NOTE]
>
>Bulkbewerking van eigenschappen is ook beschikbaar voor Elementen. Het is vergelijkbaar, maar op een paar punten verschilt het. Zie [Eigenschappen van meerdere elementen bewerken](/help/assets/metadata.md) voor meer informatie.
>
>Er is ook [Bulkeditor](/help/sites-administering/bulk-editor.md). Met deze editor kunt u zoeken naar inhoud van meerdere pagina&#39;s met behulp van GQL (Google Query Language) en de inhoud vervolgens rechtstreeks bewerken met de Bulk-editor voordat u de wijzigingen opslaat in de oorspronkelijke pagina&#39;s.

U kunt meerdere pagina&#39;s selecteren voor bulkbewerking op verschillende manieren, zoals:

* Wanneer u door de **Sites** console
* Na gebruik van **Zoeken** om een set pagina&#39;s te zoeken

![epp-01](assets/epp-01.png)

Nadat u de pagina&#39;s hebt geselecteerd en vervolgens op de knop **Eigenschappen, optie**, worden de eigenschappen voor bulkgoederen weergegeven:

![epp-02](assets/epp-02.png)

U kunt alleen pagina&#39;s bulksgewijs bewerken die:

* Hetzelfde brontype delen
* Maakt geen deel uit van een livecopy

   * Als een van de pagina&#39;s zich in een live kopie bevindt, wordt een bericht weergegeven wanneer de eigenschappen worden geopend.

Nadat u de optie Bulk bewerken hebt ingevoerd, kunt u het volgende doen:

* **Weergave**

  Wanneer u Pagina-eigenschappen voor meerdere pagina&#39;s bekijkt, ziet u het volgende:

   * Een lijst met de betrokken pagina&#39;s

      * U kunt desgewenst selecteren of deselecteren

   * Tabs

      * Net als bij het weergeven van eigenschappen voor één pagina, worden de eigenschappen onder tabbladen geordend.

   * Een subset van eigenschappen

      * Eigenschappen die beschikbaar zijn op alle geselecteerde pagina&#39;s en die expliciet zijn gedefinieerd als beschikbaar voor bulkbewerking, zijn zichtbaar.
      * Als u de paginaselectie tot één pagina reduceert, zijn alle eigenschappen zichtbaar.

   * Algemene eigenschappen met een gemeenschappelijke waarde

      * Alleen eigenschappen met een gemeenschappelijke waarde worden weergegeven in de weergavemodus.
      * Wanneer het veld meerdere waarden heeft (bijvoorbeeld tags), worden waarden alleen weergegeven wanneer *alles* vaak voorkomen. Als slechts enkele van de algemene voorbeelden voorkomen, worden deze alleen weergegeven tijdens het bewerken.

  Wanneer er geen eigenschappen met een gemeenschappelijke waarde bestaan, wordt een bericht weergegeven.

* **Bewerken**

  Bij het bewerken van Pagina-eigenschappen voor meerdere pagina&#39;s:

   * U kunt de waarden in de beschikbare velden bijwerken.

      * De nieuwe waarden worden toegepast op alle geselecteerde pagina&#39;s wanneer u **Gereed**.
      * Als het veld meerdere waarden heeft (bijvoorbeeld Codes), kunt u een nieuwe waarde toevoegen of een gemeenschappelijke waarde verwijderen.

   * Velden die veel voorkomen, maar verschillende waarden op de verschillende pagina&#39;s hebben, worden aangegeven met een speciale waarde, zoals de tekst `<Mixed Entries>`.

>[!NOTE]
>
>De paginacomponent kan worden gevormd om de gebieden te specificeren beschikbaar voor bulkbewerking. Zie [De pagina configureren voor het bulksgewijs bewerken van pagina-eigenschappen](/help/sites-developing/bulk-editing.md).
