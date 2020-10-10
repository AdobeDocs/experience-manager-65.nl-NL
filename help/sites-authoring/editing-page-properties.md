---
title: Pagina-eigenschappen bewerken
seo-title: Pagina-eigenschappen bewerken
description: De vereiste eigenschappen voor een pagina definiëren
seo-description: De vereiste eigenschappen voor een pagina definiëren
uuid: d3a2183b-8082-4cfc-aeed-26facbf3f3e6
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: page-authoring
content-type: reference
discoiquuid: 1e9dd0d7-209a-4989-b66b-bca0d04b437a
docset: aem65
translation-type: tm+mt
source-git-commit: ea39bb870fd20f7e30afc2c4f5bceb2fe6427848
workflow-type: tm+mt
source-wordcount: '1781'
ht-degree: 4%

---


# Pagina-eigenschappen bewerken{#editing-page-properties}

U kunt de vereiste eigenschappen voor een pagina definiëren. Deze kunnen afhankelijk van de aard van de pagina variëren. Sommige pagina&#39;s kunnen bijvoorbeeld zijn verbonden met een live kopie, andere niet en de live kopie-informatie is beschikbaar, indien van toepassing.

## Pagina-eigenschappen {#page-properties}

De eigenschappen worden verdeeld over verscheidene lusjes.

### Basis {#basic}

* **Titel**

   De titel van de pagina wordt op verschillende locaties weergegeven. Bijvoorbeeld de lijst op het tabblad **Websites** en de weergave van de **Sites** -kaart/lijst.

   Dit is een verplicht veld.

* **Tags**

   Hier kunt u codes toevoegen aan of verwijderen uit de pagina door de lijst in het selectievak bij te werken:

   * Nadat u een tag hebt geselecteerd, wordt deze weergegeven onder het selectievak. U kunt een tag uit deze lijst verwijderen met de x.
   * U kunt een volledig nieuwe tag invoeren door de naam in een leeg selectievak te typen.

      * De nieuwe tag wordt gemaakt wanneer u op Enter drukt.
      * De nieuwe tag wordt dan weergegeven met een kleine ster aan de rechterkant die aangeeft dat het een nieuwe tag is.
   * Met de vervolgkeuzefunctie kunt u bestaande tags selecteren.
   * Een x wordt weergegeven wanneer u met de muis over een tag-item in het selectievak beweegt. Hiermee kunt u die tag voor deze pagina verwijderen.

   Zie Tags [gebruiken voor meer informatie over tags](/help/sites-authoring/tags.md).

* **Verbergen in navigatie**

   Geeft aan of de pagina wordt weergegeven of verborgen in de paginanavigatie van de resulterende site.

* **Paginatitel**

   Een titel die op de pagina moet worden gebruikt. Wordt meestal gebruikt door titelcomponenten. Als deze leeg is, wordt de **titel** gebruikt.

* **Navigatietitel**

   U kunt een aparte titel opgeven voor gebruik in de navigatie (bijvoorbeeld als u iets beknopter wilt). Als de waarde leeg is, wordt de **titel** gebruikt.

* **Ondertitel**

   Een ondertitel voor gebruik op de pagina.

* **Beschrijving**

   Uw beschrijving van de pagina, het doel of andere details die u wilt toevoegen.

* **Op tijd**

   De datum en het tijdstip waarop de gepubliceerde pagina wordt geactiveerd. Wanneer deze pagina wordt gepubliceerd, blijft deze sluimerend tot de opgegeven tijd.

   Laat deze velden leeg voor pagina&#39;s die u direct wilt publiceren (het normale scenario).

* **Uit-tijd**

   De tijd waarop de gepubliceerde pagina wordt gedeactiveerd.

   Laat deze velden weer leeg voor directe actie.

* **Vanity URL**

   Hiermee kunt u een vanity-URL voor deze pagina invoeren, waarmee u een kortere en/of expressieve URL kunt hebben.

   Als de URL vanity bijvoorbeeld is ingesteld `welcome`op de pagina die wordt aangeduid door het pad `/v1.0/startpage`voor de website, `http://example.com,` zou dit de vanity URL `http://example.com/welcome`zijn van `http://example.com/content/v1.0/startpage`

   >[!CAUTION]
   >
   >Vanity-URL&#39;s:
   >
   >* Dit moet uniek zijn, dus zorg ervoor dat de waarde niet al door een andere pagina wordt gebruikt.
   >* Geen ondersteuning voor regex-patronen.
   >* Deze mag niet op een bestaande pagina worden ingesteld.


   U moet ook Dispatcher configureren om toegang tot vanity URL&#39;s in te schakelen. Zie Toegang [tot URL&#39;s met](https://docs.adobe.com/content/help/en/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html#enabling-access-to-vanity-urls-vanity-urls) Vanity inschakelen voor meer informatie.

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

   Geef het [ontwerp](/help/sites-developing/designer.md) op dat voor deze pagina moet worden gebruikt.

* **Alias**

   Geef een alias op die voor deze pagina moet worden gebruikt.

   >[!NOTE]
   >
   >Alias plaatst het `sling:alias` bezit om een alias naam voor het middel te bepalen (dit beïnvloedt slechts het middel, niet de weg).
   >
   >Bijvoorbeeld: als u een alias van `latin-lang` voor de knoop `/content/we-retail/spanish` bepaalt, dan kan deze pagina via worden betreden `/content/we-retail/latin-language`
   >
   >Zie [Gelokaliseerde paginanamen onder SEO en URL Management Best Practices](/help/managing/seo-and-url-management.md#localized-page-names)voor meer informatie.

* **Overgenomen van &lt;*path*>**

   Geeft aan of de pagina wordt overgeërfd. en waar van.

* **Cloud Configuration**

   Het pad naar de configuratie.

* **Toegestane sjablonen**

   [Definieer de lijst met sjablonen die beschikbaar](/help/sites-authoring/templates.md#allowingatemplate) zijn in deze subvertakking.

* **Inschakelen** (verificatievereiste)

   Schakel het gebruik van verificatie in (of uit) om toegang te krijgen tot de pagina.

   >[!NOTE]
   >
   >Gesloten gebruikersgroepen voor de pagina worden gedefinieerd op het tabblad **[Machtigingen](/help/sites-authoring/editing-page-properties.md#permissions)** .

   >[!CAUTION]
   >
   >Op het tabblad **[Machtigingen](/help/sites-authoring/editing-page-properties.md#main-pars-procedure-949394300)** kunt u CUG-configuraties bewerken op basis van de aanwezigheid van de `granite:AuthenticationRequired` mix. Als de paginamachtigingen gebruikend verouderde configuraties van de GIDS, op de aanwezigheid van `cq:cugEnabled` bezit worden gevormd, zal een waarschuwingsbericht onder de Vereiste **van de** Authentificatie worden getoond en de optie zal niet editable zijn, noch zullen de [Toestemmingen](/help/sites-authoring/editing-page-properties.md#permissions) editable zijn.
   >
   >
   >In een dergelijk geval moeten de toestemmingen van de KUG in [klassieke UI](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md)worden uitgegeven.

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

   Deze optie wordt beschikbaar nadat u een wijziging in de miniatuur hebt aangebracht. Als u de wijziging niet wilt behouden, kunt u die wijziging herstellen voordat u de wijziging opslaat.

### Sociale media {#social-media}

* **Delen via sociale media**

   Definieert de opties voor delen die beschikbaar zijn op de pagina. Hiermee geeft u de opties weer die beschikbaar zijn voor de kerncomponent [](https://helpx.adobe.com/experience-manager/core-components/using/sharing.html)Delen.

   * **Delen door gebruikers voor Facebook inschakelen**
   * **Gebruikersdeling inschakelen voor Pinterest**
   * **Voorkeur voor XF-variatie** Definieer de variatie van het ervaringsfragment die wordt gebruikt voor het genereren van metagegevens voor de pagina

### Cloud Services {#cloud-services}

* **Cloud Services**

   Eigenschappen definiëren voor [cloudservices](/help/sites-developing/extending-cloud-config.md).

### Personalisatie {#personalization}

* **ContextHub-configuraties**

   Selecteer de Configuratie [](/help/sites-developing/ch-configuring.md) ContextHub en de Weg [van](/help/sites-administering/segmentation.md)Segmenten.

* **Doelconfiguratie**

   Selecteer een [merk om een bereik voor het instellen van doelen](/help/sites-authoring/target-adobe-campaign.md)op te geven.

   >[!NOTE]
   >Voor deze optie moet de gebruikersaccount deel uitmaken van de `Target Adminstrators`groep.

### Machtigingen {#permissions}

* **Machtigingen**

   Op dit tabblad kunt u het volgende doen:

   * [Machtigingen toevoegen](/help/sites-administering/user-group-ac-admin.md)
   * [Gesloten gebruikersgroep bewerken](/help/sites-administering/cug.md#applying-your-closed-user-group-to-content-pages)

   * De [effectieve machtigingen weergeven](/help/sites-administering/user-group-ac-admin.md)
   >[!CAUTION]
   >
   >Op het tabblad **Machtigingen** kunt u CUG-configuraties bewerken op basis van de aanwezigheid van de `granite:AuthenticationRequired` mix. Als de paginamachtigingen gebruikend afgekeurde configuraties van de GIDS worden gevormd, die op de aanwezigheid van `cq:cugEnabled` bezit worden gebaseerd, zal een waarschuwingsbericht worden getoond en de toestemmingen van de GG zullen niet editable zijn, noch zal de Vereiste van de Authentificatie op het [Geavanceerde](/help/sites-authoring/editing-page-properties.md#advanced) lusje editable zijn.
   >
   >
   >In een dergelijk geval moeten de toestemmingen van de KUG in [klassieke UI](/help/sites-classic-ui-authoring/classic-page-author-edit-page-properties.md)worden uitgegeven.

   >[!NOTE]
   >
   >Het lusje van Toestemmingen staat niet de verwezenlijking van lege groepen CUG toe, die als eenvoudige manier kunnen nuttig zijn om toegang tot elke gebruiker te ontkennen. Om dit te doen moet de Ontdekkingsreiziger van CRX worden gebruikt. Zie de [Gebruiker van het document, de Groep en het Beleid](/help/sites-administering/user-group-ac-admin.md) van de Rechten van de Toegang voor meer informatie.

### Blauwdruk {#blueprint}

* **Blauwdruk**

   Definieer eigenschappen voor een pagina Vervagen binnen [beheer](/help/sites-administering/msm.md)met meerdere sites. Hiermee bepaalt u de omstandigheden waaronder wijzigingen worden doorgegeven aan Live kopie.

### Live kopie {#live-copy}

* **Livecopy**

   Definieer eigenschappen voor een Live Copy-pagina in [beheer](/help/sites-administering/msm.md)met meerdere sites. Hiermee bepaalt u de omstandigheden waaronder wijzigingen worden doorgegeven via het blauwdruk.

### Sitestructuur {#site-structure}

* Koppelingen maken naar pagina&#39;s die voor de hele site functionaliteit bieden, zoals **Aanmeldingspagina**, **Offline pagina**.

## Pagina-eigenschappen bewerken {#editing-page-properties-1}

U kunt pagina-eigenschappen definiëren:

* Vanuit de **Sites** -console:

   * [Een nieuwe pagina](/help/sites-authoring/managing-pages.md#creating-a-new-page) maken (een subset van de eigenschappen)

   * Klikken of tikken op **eigenschappen**

      * Voor één pagina
      * Voor meerdere pagina&#39;s (alleen een subset van de eigenschappen is beschikbaar voor massabewerking)

* Vanuit de pagina-editor:

   * **Pagina-informatie** gebruiken (en vervolgens **Eigenschappen openen**)

### Vanuit de siteconsole - Eén pagina {#from-the-sites-console-single-page}

Klik of tikken op **Eigenschappen** om de pagina-eigenschappen te definiëren:

1. Navigeer met de **Sites** -console naar de locatie van de pagina waarvan u de eigenschappen wilt weergeven en bewerken.

1. Selecteer de optie **Eigenschappen** voor de vereiste pagina met een van de volgende opties:

   * [Snelle acties](/help/sites-authoring/basic-handling.md#quick-actions)
   * [Selectiemodus](/help/sites-authoring/basic-handling.md#selectionmode)

   De pagina-eigenschappen worden weergegeven met de juiste tabbladen.

1. Bekijk of bewerk de eigenschappen naar wens.

1. Gebruik vervolgens **Opslaan** om uw updates op te slaan, gevolgd door **Sluiten** om terug te keren naar de console.

### Bij het bewerken van een pagina {#when-editing-a-page}

Wanneer u een pagina bewerkt, kunt u met **Pagina-informatie** de pagina-eigenschappen definiëren:

1. Open de pagina waarvan u de eigenschappen wilt bewerken.

1. Selecteer het pictogram **Pagina-informatie** om het selectiemenu te openen:

   ![screen_shot_2018-03-22at095740](assets/screen_shot_2018-03-22at095740.png)

1. Select **Open Properties** and a dailog will open allowing you to edit the properties, sorted by the appropriate tab. De volgende knoppen zijn ook beschikbaar aan de rechterkant van de werkbalk:

   * **Annuleren**
   * **Opslaan en sluiten**

1. Sla de wijzigingen op met de knop **Opslaan en sluiten** .

### Van de Console van Plaatsen - Meerdere Pagina&#39;s {#from-the-sites-console-multiple-pages}

Vanuit de **Sites**-console kunt u meerdere pagina&#39;s selecteren en vervolgens **Eigenschappen weergeven** gebruiken om de pagina-eigenschappen te bekijken en/of te bewerken. Dit wordt het bulkgewijs bewerken van pagina-eigenschappen genoemd.

>[!NOTE]
>
>Bulkbewerking van eigenschappen is ook beschikbaar voor Elementen. Het is erg vergelijkbaar, maar op een paar punten verschilt het. Zie Eigenschappen van meerdere elementen [](/help/assets/metadata.md) bewerken voor meer informatie.
>
>Er is ook de [Bulk-editor](/help/sites-administering/bulk-editor.md), waarmee u met GQL (Google Query Language) naar inhoud op meerdere pagina&#39;s kunt zoeken en de inhoud vervolgens rechtstreeks in de bulkeditor kunt bewerken voordat u de wijzigingen op de pagina&#39;s die beginnen opslaat.

U kunt meerdere pagina&#39;s selecteren voor bulkbewerking op verschillende manieren, zoals:

* Bij het bladeren door de **Sites** -console
* Nadat u **Zoeken** hebt gebruikt om een set pagina&#39;s te zoeken

![epp-01](assets/epp-01.png)

Nadat u de pagina&#39;s hebt geselecteerd en op de optie **Eigenschappen** hebt geklikt of getikt, worden de bulkeigenschappen weergegeven:

![epp-02](assets/epp-02.png)

U kunt alleen pagina&#39;s bulksgewijs bewerken die:

* Hetzelfde brontype delen
* Maakt geen deel uit van een livecopy

   * Als een van de pagina&#39;s zich in een live kopie bevindt, wordt een bericht weergegeven wanneer de eigenschappen worden geopend.

Nadat u de optie Bulk bewerken hebt ingevoerd, kunt u:

* **Weergave**

   Wanneer u pagina-eigenschappen weergeeft voor meerdere pagina&#39;s, kunt u het volgende zien:

   * Een lijst met de betrokken pagina&#39;s

      * U kunt desgewenst selecteren/deselecteren
   * Tabs

      * Net als bij het weergeven van eigenschappen voor één pagina, worden de eigenschappen onder tabbladen geordend.
   * Een subset van eigenschappen

      * Eigenschappen die beschikbaar zijn op alle geselecteerde pagina&#39;s en die expliciet zijn gedefinieerd als beschikbaar voor bulkbewerking, zijn zichtbaar.
      * Als u de paginaselectie tot één pagina reduceert, zijn alle eigenschappen zichtbaar.
   * Algemene eigenschappen met een gemeenschappelijke waarde

      * Alleen eigenschappen met een gemeenschappelijke waarde worden weergegeven in de weergavemodus.
      * Als het veld meerdere waarden heeft (bijvoorbeeld Codes), worden waarden alleen weergegeven als *alle* waarden gemeenschappelijk zijn. Als slechts enkele van deze voorbeelden algemeen zijn, worden deze alleen weergegeven tijdens het bewerken.

   Wanneer er geen eigenschappen met een gemeenschappelijke waarde bestaan, wordt een bericht weergegeven.

* **Bewerken**

   Bij het bewerken van Pagina-eigenschappen voor meerdere pagina&#39;s:

   * U kunt de waarden in de beschikbare velden bijwerken.

      * De nieuwe waarden worden toegepast op alle geselecteerde pagina&#39;s wanneer u **Gereed** selecteert.
      * Wanneer het veld meerdere waarden heeft (bijvoorbeeld Codes), kunt u een nieuwe waarde toevoegen of een gemeenschappelijke waarde verwijderen.
   * Velden die veel voorkomen, maar die verschillende waarden hebben op de verschillende pagina&#39;s, worden aangegeven met een speciale waarde, zoals de tekst `<Mixed Entries>`. Bij het bewerken van dergelijke velden moet de nodige aandacht worden besteed om gegevensverlies te voorkomen.


>[!NOTE]
>
>De paginacomponent kan worden gevormd om de gebieden te specificeren beschikbaar voor bulkbewerking. Zie Uw pagina [configureren voor bulkbewerking van pagina-eigenschappen](/help/sites-developing/bulk-editing.md).
