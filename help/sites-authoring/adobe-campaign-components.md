---
title: Adobe Campaign-componenten
seo-title: Adobe Campaign-componenten
description: Wanneer u integreert met Adobe Campaign, hebt u componenten beschikbaar voor wanneer u werkt met nieuwsbrieven en formulieren
seo-description: Wanneer u integreert met Adobe Campaign, hebt u componenten beschikbaar voor wanneer u werkt met nieuwsbrieven en formulieren
uuid: a858d5ca-aa6e-4bde-92db-a6dcd8b48ae6
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
discoiquuid: 9da34dab-7e89-4127-ab26-532687746b2a
docset: aem65
translation-type: tm+mt
source-git-commit: 90c99e527a40bb663d4f32d8746b46cf34a2319f
workflow-type: tm+mt
source-wordcount: '2854'
ht-degree: 0%

---


# Adobe Campaign-componenten{#adobe-campaign-components}

Wanneer u integreert met Adobe Campaign, hebt u componenten beschikbaar voor wanneer u met nieuwsbrieven en met formulieren werkt. Beide worden in dit document beschreven.

>[!CAUTION]
>
>De AEM e-mailcomponenten zijn afgekeurd. Vanwege de aard van e-mail, waarin inhoud en stijl worden samengevoegd, worden de e-mailcomponenten die door AEM buiten de box worden geleverd van beperkte hergebruik voor klanten omdat aangepaste stijlen moeten worden geïmplementeerd in alle componenten die vereist zijn voor projecten.
>
>E-mailcomponenten kunnen op projectniveau worden geïmplementeerd en de verouderde AEM e-mailcomponenten laten zien hoe dat kan worden bereikt. Deze vervangen onderdelen mogen echter niet worden gebruikt voor projecten.

## Adobe Campaign Newsletter-componenten {#adobe-campaign-newsletter-components}

Alle componenten van de Campagne volgen de beste praktijken die in [Beste praktijken voor E-mailMalplaatjes](/help/sites-administering/best-practices-for-email-templates.md) worden geschetst en zijn gebaseerd op de de prijsverhogingstaal van de Adobe [HTML](https://helpx.adobe.com/experience-manager/htl/using/overview.html).

Wanneer u een nieuwsbrief/e-mail opent die wordt gevormd om met Adobe Campaign te integreren, zou u de volgende componenten in de **Adobe Campaign Newsletter** sectie moeten zien:

* Kop (campagne)
* Afbeelding (campagne)
* Koppeling (campagne)
* Scene7-afbeeldingssjabloon (campagne)
* Gerichte referentie (campagne)
* Tekst en afbeelding (campagne)
* Tekst en persoonlijke voorkeur (campagne)

Een beschrijving van deze componenten vindt u in de volgende sectie.

De componenten zijn als volgt:

![chlimage_1-43](assets/chlimage_1-43.png)

### Kop (campagne) {#heading-campaign}

De kopcomponent kan:

* Geef de naam van de huidige pagina weer door het veld **Titel** leeg te laten.
* Geef een tekst weer die u opgeeft in het veld **Titel** .

U bewerkt de component **Kop (Campagne)** rechtstreeks. Laat leeg als u de paginatitel wilt gebruiken.

![chlimage_1-44](assets/chlimage_1-44.png)

U kunt het volgende configureren:

* **Titel** Als u een andere naam dan de paginatitel wilt gebruiken, voert u deze hier in.

* **Kopniveau (1, 2, 3, 4)** Het kopniveau op basis van de HTML-kopgrootten 1-4.

In het volgende voorbeeld ziet u een component Kop (Campagne) die wordt weergegeven.

![chlimage_1-45](assets/chlimage_1-45.png)

### Afbeelding (campagne) {#image-campaign}

In de afbeeldings-(campagne)component wordt een afbeelding en de bijbehorende tekst weergegeven volgens de opgegeven parameters.

U kunt een afbeelding uploaden, deze vervolgens bewerken en bewerken (bijvoorbeeld uitsnijden, roteren, koppeling/titel/tekst toevoegen).

U kunt een afbeelding van de [Asset Browser](/help/sites-authoring/author-environment-tools.md#assetsbrowsertouchoptimizedui) rechtstreeks naar de component slepen of het dialoogvenster [Configureren](/help/sites-authoring/editing-content.md#editconfigurecopycutdeletepastetouchoptimizedui)ervan. U kunt een beeld van de Configure dialoog ook uploaden; dit dialoogvenster bevat ook alle definities en bewerkingen van de afbeelding :

![chlimage_1-46](assets/chlimage_1-46.png)

>[!NOTE]
>
>U moet informatie invoeren in het veld **Alt-tekst** , anders kan de afbeelding niet worden opgeslagen.

Nadat de afbeelding is geüpload (en niet eerder) kunt u desgewenst [op plaats bewerken](/help/sites-authoring/editing-content.md#editcontenttouchoptimizedui) om de afbeelding uit te snijden of te roteren:

![](do-not-localize/chlimage_1-10.png)

>[!NOTE]
>
>De editor op locatie gebruikt de oorspronkelijke grootte en hoogte-breedteverhouding van de afbeelding tijdens het bewerken. U kunt ook de eigenschappen voor hoogte en breedte opgeven. Beperkingen voor grootte en hoogte-breedteverhouding die in de eigenschappen zijn gedefinieerd, worden toegepast wanneer u de bewerkingswijzigingen opslaat.
>
>Afhankelijk van uw exemplaar, kunnen de minimum en maximumbeperkingen ook door het [ontwerp van de pagina](/help/sites-developing/designer.md)worden opgelegd; deze worden ontwikkeld tijdens de uitvoering van het project .

In de modus Volledig scherm zijn verschillende aanvullende opties beschikbaar. bijvoorbeeld toewijzen en zoomen:

![](do-not-localize/chlimage_1-11.png)

Wanneer een beeld wordt geladen, kunt u het volgende vormen:

* **Selecteer Toewijzen** aan afbeelding toewijzen. U kunt opgeven hoe u de afbeelding met hyperlinks wilt maken (rechthoek, veelhoek enzovoort) en waar het gebied naartoe moet wijzen.

* **Uitsnijden** Selecteer Uitsnijden om een afbeelding uit te snijden. Gebruik de muis om de afbeelding uit te snijden.

* **Selecteer Roteren** om een afbeelding te roteren. Herhaal deze bewerking totdat de afbeelding op de gewenste manier is geroteerd.

* **Wis** verwijder de huidige afbeelding.

* Zoombalk (alleen klassiek) Als u wilt in- of uitzoomen op de afbeelding, gebruikt u de schuifbalk onder de afbeelding (boven de knoppen OK en Annuleren)
* **Titel** De titel van de afbeelding.

* **Alt Text** An Alternative text for use when creating accessible content.

* **Koppeling naar** Een koppeling maken naar elementen of andere pagina&#39;s op uw website.

* **Beschrijving** Een beschrijving van de afbeelding.

* **Met Grootte** stelt u de hoogte en de breedte van de afbeelding in.

>[!NOTE]
>
>U moet informatie invoeren in het veld **Alt-tekst** op het tabblad **Geavanceerd** , anders kan de afbeelding niet worden opgeslagen en wordt het volgende foutbericht weergegeven:
>
>`Validation failed. Verify the values of the marked fields.`


In het volgende voorbeeld ziet u een component Image (Campaign) die wordt weergegeven.

![chlimage_1-47](assets/chlimage_1-47.png)

### Koppeling (campagne) {#link-campaign}

Met de component Koppeling (Campagne) kunt u een koppeling naar uw nieuwsbrief toevoegen.

U kunt het volgende configureren op de tabbladen **Weergave**, **URL-info** of **Geavanceerd** :

* **Bijschrift** koppelen Het bijschrift voor de koppeling. Dit is de tekst die gebruikers zien.

* **Link ToolTip** voegt aanvullende informatie toe over het gebruik van de koppeling.

* **LinkType** selecteert u in de vervolgkeuzelijst tussen een 
**Aangepaste URL** en een **adaptief document**. Dit veld is verplicht. Als u Aangepaste URL selecteert, kunt u de URL van de koppeling opgeven. Als u Aangepast document selecteert, kunt u het documentpad opgeven.

* **Aanvullende URL-parameter** Voeg aanvullende URL-parameters toe. Klik op Item toevoegen om meerdere items toe te voegen.

>[!NOTE]
>
>U moet informatie invoeren in het veld **Koppelingstype** op het tabblad **URL-informatie** , anders kan de component niet opslaan en wordt het volgende foutbericht weergegeven:
>
>`Validation failed. Verify the values of the marked fields.`


In het volgende voorbeeld ziet u een component Link (Campagne) die wordt weergegeven.

![chlimage_1-48](assets/chlimage_1-48.png)

### Scene7-afbeeldingssjabloon (campagne) {#scene-image-template-campaign}

[Scene7-afbeeldingssjablonen](https://help.adobe.com/en_US/scene7/using/WS60B68844-9054-4099-BF69-3DC998A04D3C.html) zijn gelaagde afbeeldingsbestanden, waarbij inhoud en eigenschappen kunnen worden geparametriseerd voor variabiliteit. Met de sjablooncomponent **Afbeelding** kunt u Scene7-sjablonen in nieuwsbrieven gebruiken en de waarden van sjabloonparameters wijzigen. Daarnaast kunt u metagegevensvariabelen van Adobe Campaign binnen de parameters gebruiken, zodat elke gebruiker de afbeelding op een persoonlijke manier ervaart.

![chlimage_1-49](assets/chlimage_1-49.png)

Klik op **Bewerken** om de component te configureren. U kunt de instellingen configureren die in deze sectie worden beschreven. Deze Scene7-afbeeldingssjabloon wordt in detail beschreven in de [Scene7 Image Template-component](/help/assets/scene7.md#image-template).

Daarnaast bevat het parametervenster alle sjabloonparameters die zijn gedefinieerd voor de sjabloon in Scene7. Voor elk van deze parameters kunt u de waarde aanpassen, variabelen invoegen of de standaardwaarde ervan herstellen.

![chlimage_1-50](assets/chlimage_1-50.png)

### Gerichte referentie (campagne) {#targeted-reference-campaign}

Met de component Doelverwijzing (Campagne) kunt u een verwijzing naar een doelalinea maken.

In deze component navigeert u naar de doelalinea om deze te selecteren.

Klik op het mappictogram om naar de alinea te navigeren waarnaar u wilt verwijzen. Klik op het vinkje als u klaar bent.

### Tekst en afbeelding (campagne) {#text-image-campaign}

Met de component Tekst en afbeelding (campagne) voegt u een tekstblok en een afbeelding toe.

Wanneer u klikt om de component te vormen, selecteert u Tekst of Beeld.

![chlimage_1-51](assets/chlimage_1-51.png)

Als u **Tekst** selecteert, wordt een inline-editor weergegeven:

![](do-not-localize/chlimage_1-12.png)

Als u **Afbeelding** selecteert, wordt de interne editor voor afbeeldingen weergegeven:

![](do-not-localize/chlimage_1-13.png)

Zie de component [](#image-campaign) Afbeelding (Campagne) voor meer informatie over het werken met afbeeldingen. Zie de component [](#text-personalization-campaign) Tekst en personalisatie (Campagne) voor meer informatie over het werken met tekst.

Net als bij de componenten Text &amp; Personalization (Campaign) en Image (Campaign) kunt u het volgende configureren:

* **Tekst** Voer tekst in. Met de werkbalk kunt u de opmaak wijzigen, lijsten maken en koppelingen toevoegen.

* **Afbeelding** slepen Een afbeelding vanuit de zoekfunctie voor inhoud of klik om naar een afbeelding te bladeren. Uitsnijden of roteren naar wens.

* **Eigenschappen** van afbeelding (**Geavanceerde afbeeldingseigenschappen**) Hiermee kunt u het volgende opgeven:

   * **Titel** De titel van het blok; wordt weergegeven door mouseover.

   * **Alternatieve tekst voor alt-tekst** die moet worden weergegeven als de afbeelding niet kan worden weergegeven.

   * **Koppeling maken naar** Koppelingen naar elementen of andere pagina&#39;s op uw website.

   * **Beschrijving** Een beschrijving van de afbeelding.

   * **Met Grootte** stelt u de hoogte en breedte van de afbeelding in.

>[!NOTE]
>
>Het veld **Alt-tekst** op het tabblad **Geavanceerd** is vereist of de component kan niet worden opgeslagen. Het volgende foutbericht wordt weergegeven:
>
>`Validation failed. Verify the values of the marked fields.`


In het volgende voorbeeld ziet u een component Text &amp; Image (Campaign) die wordt weergegeven.

![chlimage_1-52](assets/chlimage_1-52.png)

### Tekst en persoonlijke voorkeur (campagne) {#text-personalization-campaign}

Met de component Tekst en personalisatie (Campagne) kunt u een tekstblok invoeren met een WYSIWYG-editor, met functionaliteit die wordt geboden door de [Rich Text Editor](/help/sites-authoring/rich-text-editor.md). Daarnaast kunt u met deze component contextvelden en personaliseringsblokken gebruiken die beschikbaar zijn in Adobe Campaign. Zie ook [Personalisatie](/help/sites-authoring/campaign.md#inserting-personalization)invoegen.

Met de selectie van pictogrammen kunt u tekst opmaken, inclusief lettertypekenmerken, uitlijning, koppelingen, lijsten en inspringing. De functionaliteit is in wezen het zelfde in [beide UIs](/help/sites-authoring/editing-content.md), hoewel het blik-en-gevoel verschillend is:

![chlimage_1-53](assets/chlimage_1-53.png)

In de Inplace redacteur kunt u tekst toevoegen, de rechtvaardiging veranderen, verbindingen toevoegen en verwijderen, contextgebieden of verpersoonlijkingsblokken toevoegen, en volledig-schermwijze ingaan. Wanneer u klaar bent met het toevoegen van tekst/personalisatie, selecteert u het vinkje om de wijzigingen op te slaan (of x om te annuleren). Zie Bewerken [](/help/sites-authoring/editing-content.md#editcontenttouchoptimizedui) plaatsen voor meer informatie.

>[!NOTE]
>
>* Welke personalisatievelden beschikbaar zijn, is afhankelijk van de Adobe Campaign-sjabloon waaraan uw nieuwsbrief is gekoppeld.
>* Nadat u een persoon van ContextHub selecteert, worden de verpersoonlijkingsgebieden automatisch vervangen door gegevens van het geselecteerde profiel.

>
>
Zie [Persoonlijke instellingen](/help/sites-authoring/campaign.md#inserting-personalization)invoegen.

![chlimage_1-54](assets/chlimage_1-54.png)

>[!NOTE]
>
>Alleen de velden die zijn gedefinieerd in het schema **nms:seedMember** of een van de extensies worden in aanmerking genomen. De kenmerken van de tabellen die gekoppeld zijn aan **nms:seedMember** zijn niet beschikbaar.

## Adobe Campaign-formuliercomponenten {#adobe-campaign-form-components}

Met Adobe Campaign-componenten kunt u een formulier maken dat gebruikers invullen om zich te abonneren op een nieuwsbrief, zich af te melden bij een nieuwsbrief of hun gebruikersprofielen bij te werken. Zie Adobe Campaign Forms [](/help/sites-authoring/adobe-campaign-forms.md) maken voor meer informatie.

Elk componentveld kan worden gekoppeld aan een Adobe Campaign-databaseveld. De beschikbare velden verschillen afhankelijk van het type gegevens dat ze bevatten, zoals wordt beschreven in de sectie [Componenten en Gegevenstype](#components-and-data-type). Als u het schema voor ontvangers in Adobe Campaign uitbreidt, zijn de nieuwe velden beschikbaar in de componenten waarvan de gegevenstypen overeenkomen.

Wanneer u een formulier opent dat is geconfigureerd voor integratie met Adobe Campaign, ziet u de volgende componenten in de sectie **Adobe Campaign** :

* Selectievakje (campagne)
* Datumveld (campagne) en Datumveld/HTML5 (campagne)
* Gecodeerde primaire sleutel (campagne)
* Foutweergave (campagne)
* Verborgen afstemmingssleutel (campagne)
* Numeriek veld (campagne)
* Optieveld (campagne)
* Checklist voor abonnementen (campagne)
* Tekstveld (campagne)

De componenten zijn als volgt:

![chlimage_1-55](assets/chlimage_1-55.png)

In deze sectie wordt elke component gedetailleerd beschreven.

### Componenten en gegevenstype {#components-and-data-type}

In de volgende tabel worden de componenten beschreven die beschikbaar zijn om Adobe Campaign-profielgegevens weer te geven en te wijzigen. Elke component kan worden toegewezen aan een Adobe Campaign-profielveld om de waarde weer te geven en het veld bij te werken wanneer het formulier wordt verzonden. De verschillende componenten kunnen slechts aan gebieden van een aangewezen gegevenstype worden aangepast.

<table>
 <tbody>
  <tr>
   <td><p><strong>Component</strong></p> </td>
   <td><p><strong>Gegevenstype van Adobe Campaign-veld</strong></p> </td>
   <td><p><strong>Voorbeeldveld</strong></p> </td>
  </tr>
  <tr>
   <td><p>Selectievakje (campagne)</p> </td>
   <td><p>boolean</p> </td>
   <td><p>Geen contact meer (via een kanaal)</p> </td>
  </tr>
  <tr>
   <td><p>Datumveld (campagne)</p> <p>Datumveld/HTML 5 (campagne)</p> </td>
   <td><p>date</p> </td>
   <td><p>Geboortedatum</p> </td>
  </tr>
  <tr>
   <td><p>Numeriek veld (campagne)</p> </td>
   <td><p>numeriek (byte, short, long, double)</p> </td>
   <td><p>Leeftijd</p> </td>
  </tr>
  <tr>
   <td><p>Optieveld (campagne)</p> </td>
   <td><p>byte met gekoppelde waarden</p> </td>
   <td><p>Geslacht</p> </td>
  </tr>
  <tr>
   <td><p>Tekstveld (campagne)</p> </td>
   <td><p>string</p> </td>
   <td><p>E-mail</p> </td>
  </tr>
 </tbody>
</table>

### Instellingen die door de meeste componenten worden gebruikt {#settings-common-to-most-components}

De Adobe Campaign-componenten hebben dezelfde instellingen voor alle componenten (behalve de componenten Gecodeerde primaire sleutel en Verborgen reconstruatietoets).

In de meeste componenten, kunt u het volgende vormen:

#### Titel en tekst {#title-and-text}

![chlimage_1-56](assets/chlimage_1-56.png)

* **Titel** Als u een andere naam dan de elementnaam wilt gebruiken, voert u deze hier in.

* **Titel** verbergen Schakel dit selectievakje in als u de titel niet zichtbaar wilt maken.

* **Beschrijving** Voeg een beschrijving aan het veld toe voor meer informatie voor gebruikers.

* **Alleen waarde** tonen geeft alleen de waarde weer, als er een is

#### Adobe Campaign {#adobe-campaign}

U kunt het volgende configureren:

* **Toewijzing** Selecteer, indien van toepassing, een personalisatieveld voor Adobe Campaign.

* **Afstemmingssleutel** Schakel dit selectievakje in als dit veld deel uitmaakt van de afstemmingssleutel.

![chlimage_1-57](assets/chlimage_1-57.png)

#### Restricties {#constraints}

* **Vereist** Schakel dit selectievakje in om dit onderdeel verplicht te maken. gebruikers moeten dus een waarde invoeren.
* **Vereist Bericht** optioneel. Voeg een bericht toe met de mededeling dat het veld verplicht is.

![chlimage_1-58](assets/chlimage_1-58.png)

#### Stijlen {#styling}

* **CSS** Voer de CSS-klassen in die u voor deze component wilt gebruiken.

![chlimage_1-59](assets/chlimage_1-59.png)

### Selectievakje (campagne) {#checkbox-campaign}

Met de component CheckBox (Campagne) kan de gebruiker Adobe Campaign-profielvelden wijzigen die van een Booleaans gegevenstype zijn. U kunt bijvoorbeeld een component CheckBox (Campagne) hebben waarmee de ontvanger kan opgeven dat hij of zij niet via een kanaal mag worden benaderd.

U kunt instellingen [configureren die gelden voor de meeste Adobe Campaign-componenten](#settings-common-to-most-components) in de component Checkbox (Campagne).

In het volgende voorbeeld wordt een component CheckBox (Campagne) weergegeven.

![chlimage_1-60](assets/chlimage_1-60.png)

### Datumveld (campagne) en Datumveld/HTML 5 (campagne) {#date-field-campaign-and-date-field-html-campaign}

Gebruik het datumveld om ontvangers toe te staan een datum te zoeken. bijvoorbeeld wilt u dat de ontvangers hun geboortedatum opgeven. De datumnotatie komt overeen met de notatie die wordt gebruikt in uw Adobe Campaign-exemplaar.

Naast de [instellingen die de meeste Adobe Campaign-componenten](#settings-common-to-most-components)gemeen hebben, kunt u het volgende configureren:

* **Restricties - beperking** vervolgkeuzelijstU kunt kiezen - **Geen** of **Datum -** om de beperking van een datum of geen beperking toe te voegen. Als u datum selecteert, moeten de antwoordgebruikers in het veld een datumnotatie invoeren.

* **Restrictiebericht** Daarnaast kunt u een beperkingsbericht toevoegen, zodat gebruikers weten hoe ze hun antwoorden op de juiste wijze moeten opmaken.
* **Stijl - Breedte** Pas de breedte van het veld aan door op de pictogrammen **+** en **-** te klikken of door een getal in te voeren.

In het volgende voorbeeld wordt een component Date Field (Campaign) weergegeven met de breedte aangepast.

![chlimage_1-61](assets/chlimage_1-61.png)

### Gecodeerde primaire sleutel (campagne) {#encrypted-primary-key-campaign}

Deze component definieert de naam van de URL-parameter die de id van een Adobe Campaign-profiel (**hoofd-id** of **gecodeerde primaire sleutel** in respectievelijk Adobe Campaign Standard en 6.1) zal bevatten.

Elk formulier dat Adobe Campaign-profielgegevens weergeeft en wijzigt, **moet** een gecodeerde primaire-sleutelcomponent bevatten.

U kunt het volgende in de Encrypted Primaire (Campagne) component vormen:

* **Titel en tekst - Standaardnaam** element is ingesteld op encryptedPK. U hoeft de elementnaam alleen te wijzigen als deze conflicteert met de naam van een ander element op het formulier. Geen twee formuliervelden kunnen dezelfde elementnaam hebben.
* **Adobe Campaign - URL-parameter** Voeg de URL-parameter voor de EPK toe. U kunt bijvoorbeeld de waarde **epk** gebruiken.

In het volgende voorbeeld ziet u een component Encrypted Primary Key (Campaign) die wordt weergegeven.

![chlimage_1-62](assets/chlimage_1-62.png)

### Foutweergave (campagne) {#error-display-campaign}

Met deze component kunt u back-endfouten weergeven. De foutafhandeling van het formulier moet zijn ingesteld op Volgende om de component correct te laten werken.

In het volgende voorbeeld ziet u een component Error Display (Campaign) die wordt weergegeven.

![chlimage_1-63](assets/chlimage_1-63.png)

### Verborgen afstemmingssleutel (campagne) {#hidden-reconciliation-key-campaign}

Met de component Verborgen afstemmingssleutel (Campagne) kunt u verborgen velden toevoegen als onderdeel van de afstemmingssleutel aan een formulier.

U kunt het volgende configureren in de component Verborgen afstemmingssleutel (Campagne):

* **Titel en tekst - Standaardnaam** element retourneert reconcilKey. U hoeft de elementnaam alleen te wijzigen als deze conflicteert met de naam van een ander element op het formulier. Geen twee formuliervelden kunnen dezelfde elementnaam hebben.
* **Adobe Campaign - Toewijzing** aan een Adobe Campaign-personalisatieveld.

In het volgende voorbeeld ziet u een component Verborgen afstemmingssleutel (Campagne) die wordt weergegeven.

![chlimage_1-64](assets/chlimage_1-64.png)

### Numeriek veld (campagne) {#numeric-field-campaign}

Gebruik het numerieke veld om ontvangers toe te staan getallen in te voeren, bijvoorbeeld hun leeftijd.

Naast de [instellingen die de meeste Adobe Campaign-componenten](#settings-common-to-most-components)gemeen hebben, kunt u het volgende configureren:

* **Restricties - Restrictie** vervolgkeuzelijstU kunt kiezen - **Geen** of **Numeriek -** om de beperking van een getal of geen beperking toe te voegen. Als u een getal selecteert, moeten de antwoordgebruikers een numeriek getal invoeren in het veld.

* **Restrictiebericht** Daarnaast kunt u een beperkingsbericht toevoegen, zodat gebruikers weten hoe ze hun antwoorden op de juiste wijze moeten opmaken.
* **Stijl - Breedte** Pas de breedte van het veld aan door op de pictogrammen **+** en **-** te klikken of door een getal in te voeren.

In het volgende voorbeeld wordt een component Numeriek veld (Campagne) weergegeven met de geconfigureerde breedte.

![chlimage_1-65](assets/chlimage_1-65.png)

### Optieveld (campagne) {#option-field-campaign}

In deze vervolgkeuzelijst kunt u een optie selecteren. bijvoorbeeld het geslacht of de status van een ontvanger.

U kunt instellingen [configureren die gelden voor de meeste Adobe Campaign-componenten](#settings-common-to-most-components) in de component Optieveld (Campagne). Als u de vervolgkeuzelijst wilt vullen, selecteert u het desbetreffende veld in de personalisatievelden van Adobe Campaign door op het Adobe Campaign-symbool te klikken of erop te tikken en naar het veld te navigeren.

![chlimage_1-66](assets/chlimage_1-66.png)

In het volgende voorbeeld ziet u een component Option Field (Campaign) die wordt weergegeven.

![chlimage_1-67](assets/chlimage_1-67.png)

### Checklist voor abonnementen (campagne) {#subscriptions-checklist-campaign}

Met de component **Controlelijst voor abonnementen (Campagne)** kunt u de abonnementen wijzigen die aan een Adobe Campaign-profiel zijn gekoppeld.

Wanneer deze component aan een formulier wordt toegevoegd, worden alle beschikbare abonnementen als selectievakjes weergegeven en kan de gebruiker de gewenste abonnementen selecteren. Wanneer gebruikers het formulier verzenden, abonneert deze component de gebruiker op de geselecteerde services of meldt deze de gebruiker af, afhankelijk van het type formulieractie (**Adobe Campaign: Abonneren op Services** of **Adobe Campaign: Abonnement op Services** opzeggen).

>[!NOTE]
>
>De component controleert niet welke services de gebruiker al heeft geabonneerd op of zich niet heeft geabonneerd op.

U kunt instellingen [configureren die gelden voor de meeste Adobe Campaign-componenten](#settings-common-to-most-components) in de component Checklist (Campagne) voor abonnementen. (Er zijn geen Adobe Campaign-configuraties beschikbaar voor deze component.)

In het volgende voorbeeld ziet u een component Subscriptions Checklist (Campaign) die wordt weergegeven.

![chlimage_1-68](assets/chlimage_1-68.png)

### Tekstveld (campagne) {#text-field-campaign}

De component van het Gebied van de Tekst (Campagne) die u tekenreekstype gegevens, zoals een voornaam, een familienaam, een adres, een e-mailadres, enz. laat ingaan.

Naast de [instellingen die de meeste Adobe Campaign-componenten](#settings-common-to-most-components)gemeen hebben, kunt u het volgende configureren:

* **Restricties - Restrictie** vervolgkeuzelijstU kunt - **Geen,** **E-mail** of **Naam** (geen umlauts) - selecteren om de beperking van een e-mailadres, naam of geen beperking toe te voegen. Als u e-mail selecteert, moeten de antwoordgebruikers in het veld een e-mailadres zijn. Als u een naam selecteert, moet deze een naam zijn (umlauts zijn niet toegestaan).

* **Restrictiebericht** Daarnaast kunt u een beperkingsbericht toevoegen, zodat gebruikers weten hoe ze hun antwoorden op de juiste wijze moeten opmaken.
* **Stijl - Breedte** Pas de breedte van het veld aan door op de pictogrammen **+** en **-** te klikken of door een getal in te voeren.

In het volgende voorbeeld wordt een component Text Field (Campaign) weergegeven.

![chlimage_1-69](assets/chlimage_1-69.png)

