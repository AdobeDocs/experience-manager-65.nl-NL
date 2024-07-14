---
title: Integreren met Adobe Campaign-componenten
description: Wanneer u integreert met Adobe Campaign, hebt u componenten beschikbaar voor wanneer u met nieuwsbrieven en met formulieren werkt.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: personalization
docset: aem65
exl-id: d1132fcd-e6a0-44a2-8753-d250f68fbd78
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Personalization,Integration
role: User,Admin,Architect,Developer
source-git-commit: 9a3008553b8091b66c72e0b6c317573b235eee24
workflow-type: tm+mt
source-wordcount: '2857'
ht-degree: 0%

---

# Adobe Campaign-componenten{#adobe-campaign-components}

Wanneer u integreert met Adobe Campaign, hebt u componenten beschikbaar voor wanneer u met nieuwsbrieven en met formulieren werkt. Beide worden in dit document beschreven.

>[!CAUTION]
>
>De AEM e-mailcomponenten zijn vervangen. Vanwege de aard van e-mail, waarin inhoud en stijl worden samengevoegd, worden de e-mailcomponenten die door AEM buiten de box worden geleverd van beperkte hergebruik voor klanten omdat aangepaste stijlen moeten worden geïmplementeerd in alle componenten die vereist zijn voor projecten.
>
>E-mailcomponenten kunnen op projectniveau worden geïmplementeerd en de verouderde AEM e-mailcomponenten laten zien hoe dat kan worden bereikt. Gebruik deze vervangen componenten echter niet voor projecten.

## Adobe Campaign Newsletter-componenten {#adobe-campaign-newsletter-components}

Alle componenten van de Campagne volgen de beste praktijken die in [ worden geschetst Beste praktijken voor E-mailMalplaatjes ](/help/sites-administering/best-practices-for-email-templates.md) en zijn gebaseerd op de de prijsverhogingstaal van de Adobe [ HTML ](https://helpx.adobe.com/experience-manager/htl/using/overview.html).

Wanneer u een nieuwsbrief/e-mail opent die om met Adobe Campaign wordt gevormd te integreren, zou u de volgende componenten in de **Newsletter van Adobe Campaign** sectie moeten zien:

* Kop (campagne)
* Afbeelding (campagne)
* Koppeling (campagne)
* Scene7-afbeeldingssjabloon (campagne)
* Gerichte referentie (campagne)
* Tekst en afbeelding (campagne)
* Tekst en Personalization (campagne)

Een beschrijving van deze componenten vindt u in de volgende sectie.

De componenten zijn als volgt:

![ chlimage_1-43 ](assets/chlimage_1-43.png)

### Kop (campagne) {#heading-campaign}

De kopcomponent kan:

* Toon de naam van de huidige pagina door het **gebied van de Titel** leeg te verlaten.
* Toon een tekst die u op het **gebied van de Titel** specificeert.

U geeft direct de **Kop (Campagne) uit** component. Laat leeg als u de paginatitel wilt gebruiken.

![ chlimage_1-44 ](assets/chlimage_1-44.png)

U kunt het volgende configureren:

* **Titel**
Als u een andere naam dan de paginatitel wilt gebruiken, voert u deze hier in.

* **Kop niveau (1, 2, 3, 4)**
Het niveau van de rubriek op basis van de grootten 1-4 van de rubriek HTML.

In het volgende voorbeeld ziet u een component Kop (Campagne) die wordt weergegeven.

![ chlimage_1-45 ](assets/chlimage_1-45.png)

### Afbeelding (campagne) {#image-campaign}

In de afbeeldings-(campagne)component wordt een afbeelding en de bijbehorende tekst weergegeven volgens de opgegeven parameters.

U kunt een afbeelding uploaden, deze vervolgens bewerken en bewerken (bijvoorbeeld uitsnijden, roteren, koppeling/titel/tekst toevoegen).

U kunt of een beeld van [ Browser van Activa slepen en laten vallen ](/help/sites-authoring/author-environment-tools.md#assetsbrowsertouchoptimizedui) direct op de component of zijn [ vormen dialoog ](/help/sites-authoring/editing-content.md#editconfigurecopycutdeletepastetouchoptimizedui). U kunt een beeld van de Configure dialoog ook uploaden; dit dialoog controleert alle definities en manipulatie van het beeld:

![ chlimage_1-46 ](assets/chlimage_1-46.png)

>[!NOTE]
>
>Ga informatie op het **gebied van de Tekst van Alt** in, of het beeld kan niet worden bewaard.

Nadat het beeld (en niet vóór) wordt geupload kunt u [ gebruiken op plaats het uitgeven ](/help/sites-authoring/editing-content.md#editcontenttouchoptimizedui) om het beeld uit te snijden of te roteren zoals vereist:

![ Plaats het uitgeven toolbar ](do-not-localize/chlimage_1-10.png)

>[!NOTE]
>
>De editor op locatie gebruikt de oorspronkelijke grootte en hoogte-breedteverhouding van de afbeelding tijdens het bewerken. U kunt ook de eigenschappen voor hoogte en breedte opgeven. Beperkingen voor grootte en hoogte-breedteverhouding die in de eigenschappen zijn gedefinieerd, worden toegepast wanneer u de bewerkingswijzigingen opslaat.
>
>Afhankelijk van uw instantie, kunnen de minimum en maximumbeperkingen ook door het [ ontwerp van de pagina ](/help/sites-developing/designer.md) worden opgelegd; deze worden ontwikkeld tijdens projectimplementatie.

Er zijn verschillende aanvullende opties beschikbaar in de modus Volledig scherm, bijvoorbeeld voor toewijzen en zoomen:

![ Volledig scherm het uitgeven wijze ](do-not-localize/chlimage_1-11.png)

Wanneer een beeld wordt geladen, kunt u het volgende vormen:

* **Kaart**
Als u een afbeelding wilt toewijzen, selecteert u Kaart. U kunt opgeven hoe u de afbeelding met hyperlinks wilt maken (rechthoek, veelhoek enzovoort) en waar het gebied naartoe moet wijzen.

* **Uitsnijden**
Selecteer Uitsnijden om een afbeelding uit te snijden. Gebruik de muis om de afbeelding uit te snijden.

* **roteren**
Selecteer Roteren als u een afbeelding wilt roteren. Herhaal deze bewerking totdat de afbeelding op de gewenste manier is geroteerd.

* **Duidelijk**
Verwijder de huidige afbeelding.

* Zoombalk (alleen klassiek)
Als u wilt in- of uitzoomen op de afbeelding, gebruikt u de schuifbalk onder de afbeelding (boven de knoppen OK en Annuleren)
* **Titel**
De titel van de afbeelding.

* **de Tekst van Alt**
Een alternatieve tekst die kan worden gebruikt bij het maken van toegankelijke inhoud.

* **Verbinding aan**
Maak een koppeling naar elementen of andere pagina&#39;s binnen uw website.

* **Beschrijving**
Een beschrijving van de afbeelding.

* **Grootte**
Hiermee stelt u de hoogte en de breedte van de afbeelding in.

>[!NOTE]
>
>Ga informatie op het **Geavanceerd** gebied van de Tekst van Alt {op het **Geavanceerde** lusje in, of het beeld kan niet opslaan en u ziet het volgende foutenbericht:
>
>`Validation failed. Verify the values of the marked fields.`
>

In het volgende voorbeeld ziet u een component Image (Campaign) die wordt weergegeven.

![ chlimage_1-47 ](assets/chlimage_1-47.png)

### Koppeling (campagne) {#link-campaign}

Met de component Koppeling (Campagne) kunt u een koppeling naar uw nieuwsbrief toevoegen.

U kunt het volgende in de **Vertoning** vormen, **Info URL**, of **Geavanceerde** lusjes:

* **Bijschrift van de Verbinding**
Het bijschrift voor de koppeling. Dit is de tekst die gebruikers zien.

* **Link ToolTip**
Hiermee voegt u aanvullende informatie toe over het gebruik van de koppeling.

* **LinkType**
In de drop-down lijst, selecteer tussen a **Douane URL** en een **Aangepast Document**. Dit veld is verplicht. Als u Aangepaste URL selecteert, kunt u de URL van de koppeling opgeven. Als u Aangepast document selecteert, kunt u het documentpad opgeven.

* **Extra Parameter URL**
Voeg aanvullende URL-parameters toe. Klik op Item toevoegen om meerdere items toe te voegen.

>[!NOTE]
>
>Ga informatie op het **gebied van het Type van Verbinding** op het **Info URL** lusje in, of de component kan niet opslaan en u ziet het volgende foutenbericht:
>
>`Validation failed. Verify the values of the marked fields.`
>

In het volgende voorbeeld ziet u een component Link (Campagne) die wordt weergegeven.

![ chlimage_1-48 ](assets/chlimage_1-48.png)

### Dynamic Media Classic (Scene7)-afbeeldingssjabloon (campagne) {#scene-image-template-campaign}

Dynamic Media Classic (Scene7)-afbeeldingssjablonen zijn gelaagde afbeeldingsbestanden, waarbij inhoud en eigenschappen kunnen worden geparametriseerd voor variabiliteit. Met de component **[!UICONTROL Image template]** kunt u Scene7-sjablonen gebruiken in nieuwsbrieven en de waarden van sjabloonparameters wijzigen. Bovendien kunt u de metagegevensvariabelen van Adobe Campaign binnen de parameters gebruiken, zodat elke gebruiker de afbeelding op een persoonlijke manier ervaart.

![ chlimage_1-49 ](assets/chlimage_1-49.png)

Klik **uitgeven** om de component te vormen. U kunt de instellingen configureren die in deze sectie worden beschreven. Dit malplaatje van het Beeld van Scene7 wordt in detail beschreven in [ de component van het Malplaatje van het Beeld van Scene7 ](/help/assets/scene7.md#image-template).

Daarnaast bevat het parametervenster alle sjabloonparameters die zijn gedefinieerd voor de sjabloon in Scene7. Voor elk van deze parameters kunt u de waarde aanpassen, variabelen invoegen of de standaardwaarde ervan herstellen.

![ chlimage_1-50 ](assets/chlimage_1-50.png)

### Gerichte referentie (campagne) {#targeted-reference-campaign}

Met de component Doelverwijzing (Campagne) kunt u een verwijzing naar een doelalinea maken.

In deze component navigeert u naar de doelalinea om deze te selecteren.

Klik op het mappictogram om naar de alinea te navigeren waarnaar u wilt verwijzen. Klik op het vinkje als u klaar bent.

### Tekst en afbeelding (campagne) {#text-image-campaign}

Met de component Tekst en afbeelding (campagne) voegt u een tekstblok en een afbeelding toe.

Wanneer u klikt om de component te vormen, selecteert u Tekst of Beeld.

![ chlimage_1-51 ](assets/chlimage_1-51.png)

Het selecteren van **Tekst** toont een in-lijn redacteur:

![ de toolbar van de Tekst ](do-not-localize/chlimage_1-12.png)

Het selecteren van **Beeld** toont de op zijn plaats redacteur voor beelden:

![ de toolbar van het Beeld ](do-not-localize/chlimage_1-13.png)

Zie [ component van het Beeld (Campagne) ](#image-campaign) voor meer informatie bij het werken met beelden. Zie [ Tekst &amp; de component van Personalization (Campagne) ](#text-personalization-campaign) voor meer informatie bij het werken met tekst.

Net als bij de componenten Text &amp; Personalization (Campaign) en Image (Campaign) kunt u het volgende configureren:

* **Tekst**
Voer tekst in. Met de werkbalk kunt u de opmaak wijzigen, lijsten maken en koppelingen toevoegen.

* **Beeld**
Sleep een afbeelding vanuit de zoekfunctie voor inhoud of klik om naar een afbeelding te bladeren. Uitsnijden of roteren naar wens.

* **Eigenschappen van het Beeld** (**Geavanceerde Eigenschappen van het Beeld**)
Hier kunt u het volgende opgeven:

   * **Titel**
De titel van het blok; deze wordt weergegeven door mouseover.

   * **de Tekst van Alt**
Alternatieve tekst die moet worden weergegeven als de afbeelding niet kan worden weergegeven.

   * **Verbinding aan**
Maak een koppeling naar elementen of andere pagina&#39;s binnen uw website.

   * **Beschrijving**
Een beschrijving van de afbeelding.

   * **Grootte**
Hiermee stelt u de hoogte en breedte van de afbeelding in.

>[!NOTE]
>
>Het **gebied van de Tekst van 0} Alt {op het** Geavanceerde **lusje wordt vereist of de component kan niet opslaan en u ziet het volgende foutenbericht:**
>
>`Validation failed. Verify the values of the marked fields.`
>

In het volgende voorbeeld ziet u een component Text &amp; Image (Campaign) die wordt weergegeven.

![ chlimage_1-52 ](assets/chlimage_1-52.png)

### Tekst en Personalization (campagne) {#text-personalization-campaign}

De component van de Tekst &amp; van Personalization (Campagne) laat u een tekstblok ingaan gebruikend een redacteur WYSIWYG, met functionaliteit die door de [ Rich redacteur van de Tekst ](/help/sites-authoring/rich-text-editor.md) wordt verstrekt. Bovendien laat deze component u contextgebieden en verpersoonlijkingsblokken beschikbaar van Adobe Campaign gebruiken; zie ook [ het Opnemen van Personalization ](/help/sites-authoring/campaign.md#inserting-personalization).

Met de selectie van pictogrammen kunt u de tekst opmaken, inclusief lettertypekenmerken, uitlijning, koppelingen, lijsten en inspringing. De functionaliteit is fundamenteel het zelfde in [ beide UIs ](/help/sites-authoring/editing-content.md), hoewel het blik-en-gevoel verschillend is:

![ chlimage_1-53 ](assets/chlimage_1-53.png)

In de Inplace redacteur kunt u tekst toevoegen, de rechtvaardiging veranderen, verbindingen toevoegen en verwijderen, contextgebieden of verpersoonlijkingsblokken toevoegen, en volledig-schermwijze ingaan. Wanneer u klaar bent met het toevoegen van tekst/personalisatie, selecteert u het vinkje om de wijzigingen op te slaan (of x om te annuleren). Zie [ het Uitgeven van de Plaats ](/help/sites-authoring/editing-content.md#editcontenttouchoptimizedui) voor meer informatie.

>[!NOTE]
>
>* Welke personalisatievelden beschikbaar zijn, is afhankelijk van de Adobe Campaign-sjabloon waaraan uw nieuwsbrief is gekoppeld.
>* Nadat u een persoon van ContextHub selecteert, worden de verpersoonlijkingsgebieden automatisch vervangen door gegevens van het geselecteerde profiel.
>
>Zie [ Invoegend Personalization ](/help/sites-authoring/campaign.md#inserting-personalization).

![ chlimage_1-54 ](assets/chlimage_1-54.png)

>[!NOTE]
>
>Slechts worden de gebieden die in **worden bepaald nms:seedMember** schema of één van zijn uitbreidingen in aanmerking genomen. De attributen van de lijsten verbonden aan **nms:seedMember** zijn niet beschikbaar.

## Adobe Campaign-formuliercomponenten {#adobe-campaign-form-components}

Met Adobe Campaign-componenten kunt u een formulier maken dat gebruikers invullen om zich te abonneren op een nieuwsbrief, zich af te melden bij een nieuwsbrief of hun gebruikersprofielen bij te werken. Zie [ Creërend Adobe Campaign Forms ](/help/sites-authoring/adobe-campaign-forms.md) voor meer informatie.

Elk componentveld kan worden gekoppeld aan een Adobe Campaign-databaseveld. De beschikbare gebieden verschillen volgens het type van gegevens zij bevatten zoals die in de sectie [ Componenten en het Type van Gegevens ](#components-and-data-type) worden beschreven. Als u het schema voor ontvangers in Adobe Campaign uitbreidt, zijn de nieuwe velden beschikbaar in de componenten waarvan de gegevenstypen overeenkomen.

Wanneer u een vorm opent die om met Adobe Campaign wordt gevormd te integreren, ziet u de volgende componenten in de **Adobe Campaign** sectie:

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

![ chlimage_1-55 ](assets/chlimage_1-55.png)

In deze sectie wordt elke component in detail beschreven.

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

![ chlimage_1-56 ](assets/chlimage_1-56.png)

* **Titel**
Als u een andere naam dan de elementnaam wilt gebruiken, voert u deze hier in.

* **Titel van de Huid**
Schakel dit selectievakje in als u de titel niet zichtbaar wilt maken.

* **Beschrijving**
Voeg een beschrijving aan het gebied toe om meer informatie voor gebruikers te verstrekken.

* **toont slechts waarde**
Hiermee wordt alleen de waarde weergegeven als er een is

#### Adobe Campaign {#adobe-campaign}

U kunt het volgende configureren:

* **Toewijzing**
Selecteer desgewenst een personalisatieveld voor Adobe Campaign.

* **Verzoeningssleutel**
Schakel dit selectievakje in als dit veld deel uitmaakt van de afstemmingssleutel.

![ chlimage_1-57 ](assets/chlimage_1-57.png)

#### Restricties {#constraints}

* **Vereiste** selecteer deze controledoos om deze vereiste component te maken; namelijk moeten de gebruikers een waarde ingaan.
* **Vereiste Bericht** naar keuze, voeg een bericht toe verklarend dat het gebied wordt vereist.

![ chlimage_1-58 ](assets/chlimage_1-58.png)

#### Stijlen {#styling}

* **CSS**
Voer de CSS-klassen in die u voor deze component wilt gebruiken.

![ chlimage_1-59 ](assets/chlimage_1-59.png)

### Selectievakje (campagne) {#checkbox-campaign}

Met de component CheckBox (Campagne) kan de gebruiker Adobe Campaign-profielvelden wijzigen die van een Booleaans gegevenstype zijn. U kunt bijvoorbeeld een component CheckBox (Campagne) hebben waarmee de ontvanger kan opgeven dat hij of zij niet via een kanaal mag worden benaderd.

U kunt [ montages gemeenschappelijk voor de meeste componenten van Adobe Campaign ](#settings-common-to-most-components) in de component vormen Checkbox (Campagne).

In het volgende voorbeeld ziet u een component CheckBox (Campagne) die wordt weergegeven.

![ chlimage_1-60 ](assets/chlimage_1-60.png)

### Datumveld (campagne) en Datumveld/HTML 5 (campagne) {#date-field-campaign-and-date-field-html-campaign}

Gebruik het datumveld om ontvangers toe te staan naar een datum te gaan, bijvoorbeeld als u wilt dat de ontvangers hun geboortedatum opgeven. De datumnotatie komt overeen met de notatie die wordt gebruikt in uw Adobe Campaign-exemplaar.

Naast [ montages gemeenschappelijk voor de meeste componenten van Adobe Campaign ](#settings-common-to-most-components), kunt u het volgende vormen:

* **Beperkingen - Beperking** drop-down
U kunt selecteren - **niets** of **Datum -** om de beperking van een datum of geen beperking toe te voegen. Als u datum selecteert, moeten de antwoordgebruikers in het veld een datumnotatie invoeren.

* **Bericht van de Beperking** Bovendien, kunt u een beperkingsbericht toevoegen zodat weten de gebruikers hoe te om hun antwoorden behoorlijk te formatteren.
* **het Stijlen - de Breedte** past de breedte van het gebied aan door **+** en **te klikken of te tikken -** pictogrammen of een aantal in te gaan.

In het volgende voorbeeld wordt een component Date Field (Campaign) weergegeven met de breedte aangepast.

![ chlimage_1-61 ](assets/chlimage_1-61.png)

### Gecodeerde primaire sleutel (campagne) {#encrypted-primary-key-campaign}

Deze component bepaalt de naam van de parameter URL die het herkenningsteken van een profiel van Adobe Campaign (**Belangrijkste Herkenningsteken van het Middel** of **Gecodeerde primaire sleutel** in Adobe Campaign Standard en 6.1, respectievelijk) zal bevatten.

Elke vorm die en het wijzigen van het profielgegevens van Adobe Campaign **toont moet** een Gecodeerde Primaire Zeer belangrijke component omvatten.

U kunt het volgende in de Encrypted Primaire (Campagne) component vormen:

* **Titel en Tekst - de Naam van het Element** Gebreken aan encryptedPK. U hoeft de elementnaam alleen te wijzigen als deze conflicteert met de naam van een ander element op het formulier. Geen twee formuliervelden kunnen dezelfde elementnaam hebben.
* **Adobe Campaign - URL parameter** voegt de parameter URL voor EPK toe. Bijvoorbeeld, kunt u de waarde **epk** gebruiken.

In het volgende voorbeeld ziet u een component Encrypted Primary Key (Campaign) die wordt weergegeven.

![ chlimage_1-62 ](assets/chlimage_1-62.png)

### Foutweergave (campagne) {#error-display-campaign}

Met deze component kunt u back-endfouten weergeven. De foutafhandeling van het formulier moet zijn ingesteld op Volgende om de component correct te laten werken.

In het volgende voorbeeld ziet u een component Error Display (Campaign) die wordt weergegeven.

![ chlimage_1-63 ](assets/chlimage_1-63.png)

### Verborgen afstemmingssleutel (campagne) {#hidden-reconciliation-key-campaign}

Met de component Verborgen afstemmingssleutel (Campagne) kunt u verborgen velden toevoegen als onderdeel van de afstemmingssleutel aan een formulier.

U kunt het volgende configureren in de component Verborgen afstemmingssleutel (Campagne):

* **Titel en Tekst - de Naam van het Element** Gebreken aan reconcilKey. U hoeft de elementnaam alleen te wijzigen als deze conflicteert met de naam van een ander element op het formulier. Geen twee formuliervelden kunnen dezelfde elementnaam hebben.
* **Adobe Campaign - de Afbeelding** Kaart aan een de verpersoonlijkingsgebied van Adobe Campaign.

In het volgende voorbeeld ziet u een component Verborgen afstemmingssleutel (Campagne) die wordt weergegeven.

![ chlimage_1-64 ](assets/chlimage_1-64.png)

### Numeriek veld (campagne) {#numeric-field-campaign}

Gebruik het numerieke veld om ontvangers toe te staan getallen in te voeren, bijvoorbeeld hun leeftijd.

Naast [ montages gemeenschappelijk voor de meeste componenten van Adobe Campaign ](#settings-common-to-most-components), kunt u het volgende vormen:

* **Beperkingen - Beperking** drop-down
U kunt selecteren - **niets** of **Numeriek -** om de beperking van of een aantal of geen beperking toe te voegen. Als u een getal selecteert, moeten de antwoordgebruikers een numeriek getal invoeren in het veld.

* **Bericht van de Beperking** Bovendien, kunt u een beperkingsbericht toevoegen zodat weten de gebruikers hoe te om hun antwoorden behoorlijk te formatteren.
* **het Stijlen - de Breedte** past de breedte van het gebied aan door **+** en **te klikken of te tikken -** pictogrammen of een aantal in te gaan.

In het volgende voorbeeld wordt een component Numeriek veld (Campagne) weergegeven met de geconfigureerde breedte.

![ chlimage_1-65 ](assets/chlimage_1-65.png)

### Optieveld (campagne) {#option-field-campaign}

In deze vervolgkeuzelijst kunt u een optie selecteren, bijvoorbeeld het geslacht of de status van een ontvanger.

U kunt [ montages gemeenschappelijk voor de meeste componenten van Adobe Campaign ](#settings-common-to-most-components) op het Gebied van de Optie (Campagne) component vormen. Als u de vervolgkeuzelijst wilt vullen, selecteert u het desbetreffende veld in de personalisatievelden van Adobe Campaign door op het Adobe Campaign-symbool te klikken of erop te tikken en naar het veld te navigeren.

![ chlimage_1-66 ](assets/chlimage_1-66.png)

In het volgende voorbeeld ziet u een component Option Field (Campaign) die wordt weergegeven.

![ chlimage_1-67 ](assets/chlimage_1-67.png)

### Checklist voor abonnementen (campagne) {#subscriptions-checklist-campaign}

Gebruik de **Checklist van Abonnementen (Campagne)** component om de abonnementen te wijzigen verbonden aan een profiel van Adobe Campaign.

Wanneer deze component aan een formulier wordt toegevoegd, worden alle beschikbare abonnementen als selectievakjes weergegeven en kan de gebruiker de gewenste abonnementen selecteren. Wanneer de gebruikers de vorm voorleggen, abonneert deze component de gebruiker aan of unsubscribes de gebruiker van de geselecteerde diensten afhankelijk van het type van vormactie (**Adobe Campaign: Abonneren aan de Diensten** of **Adobe Campaign: Unsubscribe van de Diensten**).

>[!NOTE]
>
>De component controleert niet welke services de gebruiker al heeft geabonneerd op of zich niet heeft geabonneerd op.

U kunt [ montages gemeenschappelijk voor de meeste componenten van Adobe Campaign ](#settings-common-to-most-components) in de component van Checklist van Abonnementen (Campagne) vormen. (Er zijn geen Adobe Campaign-configuraties beschikbaar voor deze component.)

In het volgende voorbeeld ziet u een component Subscriptions Checklist (Campaign) die wordt weergegeven.

![ chlimage_1-68 ](assets/chlimage_1-68.png)

### Tekstveld (campagne) {#text-field-campaign}

De component van het Gebied van de Tekst (Campagne) die u tekenreekstype gegevens, zoals een voornaam, een familienaam, een adres, een e-mailadres, enz. laat ingaan.

Naast [ montages gemeenschappelijk voor de meeste componenten van Adobe Campaign ](#settings-common-to-most-components), kunt u het volgende vormen:

* **Beperkingen - Beperking** drop-down
U kunt selecteren - **niets,** **E-mail**, of **Naam** (geen umlauts) - om de beperking van of een e-mailadres, naam, of geen beperking toe te voegen. Als u e-mail selecteert, moeten de antwoordgebruikers in het veld een e-mailadres zijn. Als u een naam selecteert, moet deze een naam zijn (umlauts zijn niet toegestaan).

* **Bericht van de Beperking** Bovendien, kunt u een beperkingsbericht toevoegen zodat weten de gebruikers hoe te om hun antwoorden behoorlijk te formatteren.
* **het Stijlen - de Breedte** past de breedte van het gebied aan door **+** en **te klikken of te tikken -** pictogrammen of een aantal in te gaan.

In het volgende voorbeeld ziet u een component Text Field (Campaign) die wordt weergegeven.

![ chlimage_1-69 ](assets/chlimage_1-69.png)
