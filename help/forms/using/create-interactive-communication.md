---
title: Een interactieve communicatie maken
description: Creeer een Interactieve Mededeling gebruikend de Interactieve Communicatie redacteur. Gebruik de functie voor slepen en neerzetten om de interactieve communicatie te maken en een voorvertoning van zowel afdruk- als webuitvoer weer te geven voor verschillende apparaattypen.
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: 1f89c3bf-e67e-4d13-9285-3367be1ac8f8
solution: Experience Manager, Experience Manager Forms
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '5956'
ht-degree: 0%

---

# Een interactieve communicatie maken{#create-an-interactive-communication}

## Overzicht {#overview}

De interactieve Mededelingen centraliseren en beheert de verwezenlijking, de assemblage, en de levering gepersonaliseerde, en interactieve correspondentie. Met Afdrukken als hoofdkanaal voor het web kunt u dubbel werk minimaliseren bij het maken van de webinvoer van de interactieve communicatie.

### Vereisten {#prerequisites}

Het volgende is de eerste vereisten voor het creëren van een Interactieve Mededeling:

* Een [Formuliergegevensmodel](/help/forms/using/data-integration.md) met testgegevens of met een werkelijke gegevensbron, zoals een instantie van Microsoft® Dynamics.
* Zorg ervoor dat u de [Documentfragmenten](/help/forms/using/document-fragments.md).
* Zorg ervoor dat u [Sjablonen voor afdrukken en webkanaal](/help/forms/using/web-channel-print-channel.md).
* Zorg ervoor dat u de vereiste [thema](/help/forms/using/themes.md) voor het webkanaal.

## Interactieve communicatie maken {#createic}

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]**.
1. Selecteren **[!UICONTROL Create]** en selecteert u **[!UICONTROL Interactive Communication]**. De pagina Interactieve communicatie maken wordt weergegeven.

   ![create-interactive-communication](assets/create-interactive-communication.png)

1. Voer de volgende gegevens in. :

   * **[!UICONTROL Title]**: Voer de titel van de interactieve communicatie in.
   * **[!UICONTROL Name]**: De naam van de interactieve communicatie wordt afgeleid van de titel die u invoert. Bewerk indien nodig de selectie.
   * **[!UICONTROL Description]**: Voer een beschrijving in over de interactieve communicatie.
   * **[!UICONTROL Form Data Model]**: Blader naar het gegevensmodel van het formulier en selecteer dit. Zie voor meer informatie over het formuliergegevensmodel [AEM Forms-gegevensintegratie](/help/forms/using/data-integration.md).

   * **[!UICONTROL Prefill Service]**: Selecteer de Prefill-service om de gegevens op te halen en de interactieve communicatie vooraf in te vullen.
   * **[!UICONTROL Post Process Type]**: U kunt AEM of Forms-workflow selecteren die moet worden geactiveerd wanneer de interactieve communicatie wordt verzonden. Selecteer het type workflow dat moet worden geactiveerd.

   * **[!UICONTROL Post Process]**: Selecteer de naam van de workflow die moet worden geactiveerd. Wanneer u AEM werkstroom selecteert, verstrekt de Weg van de Bijlage, de Weg van de Lay-out, de Weg van de PDF, de Weg van Gegevens van de Druk, en de Weg van Gegevens van het Web.
   * **[!UICONTROL Tags]**: Selecteer de tags die u wilt toepassen op de interactieve communicatie. U kunt ook een nieuwe/aangepaste tagnaam typen en op Enter drukken om deze te maken.
   * **[!UICONTROL Author]**:De auteursnaam wordt automatisch genomen van de het programma geopende gebruikersnaam.
   * **[!UICONTROL Publish Date:]** Voer de datum in waarop u de interactieve communicatie wilt publiceren.
   * **[!UICONTROL Unpublish Date]**: Voer de datum in waarop u de publicatie van de interactieve communicatie ongedaan wilt maken.

1. Selecteer **[!UICONTROL Next]**. Het scherm waarop u afdruk- en webkanaalgegevens wilt opgeven, wordt weergegeven.
1. Voer het volgende in:

   * **[!UICONTROL Print]**: Selecteer deze optie om het afdrukkanaal van de interactieve communicatie te genereren.
   * **[!UICONTROL Print Template]**: Blader naar een XDP en selecteer deze als de afdruksjabloon.
   * **[!UICONTROL Web]**: Selecteer deze optie om het webkanaal of de responsieve uitvoer van interactieve communicatie te genereren.
   * **[!UICONTROL Interactive Communication Web Template]**: Blader naar de websjabloon en selecteer deze.
   * **[!UICONTROL Theme]** en **[!UICONTROL Select Theme]**: Blader en selecteer het thema om het webkanaal van de interactieve communicatie op te maken. Zie voor meer informatie [Thema&#39;s in AEM Forms](/help/forms/using/themes.md).

   * **[!UICONTROL Use Print As Master for Web Channel]**: Selecteer deze optie als u het webkanaal wilt maken dat synchroon is met het afdrukkanaal. Als u het afdrukkanaal als stramien voor het webkanaal gebruikt, zorgt u ervoor dat de inhoud en de gegevensbinding van het webkanaal worden afgeleid van het afdrukkanaal en dat de wijzigingen die u in het afdrukkanaal hebt aangebracht, worden weerspiegeld in het webkanaal wanneer u Synchroniseren selecteert. De auteurs mogen echter desgewenst de overerving voor specifieke componenten in het webkanaal verbreken. Zie voor meer informatie [Webkanaal synchroniseren met afdrukkanaal](../../forms/using/create-interactive-communication.md#synchronize).
Als u **[!UICONTROL Use Print As Master for Web Channel]** kunt u een van de volgende modi selecteren om een webkanaal te genereren:

      * **[!UICONTROL Auto layout]**: Selecteer deze modus om automatisch plaatsaanduidingen, inhoud en gegevensbinding voor het webkanaal te genereren via het kanaal Afdrukken.
      * **[!UICONTROL Manually organize]**: Selecteer deze modus om de kanaalelementen van Afdrukken handmatig te selecteren en aan het webkanaal toe te voegen met behulp van de basisinhoud in het dialoogvenster **[!UICONTROL Data Sources]** tab. Zie voor meer informatie [Selecteer de kanaalelementen van de Druk om de inhoud van het Webkanaal te creëren](#selectprintchannelelements).

   Ga voor meer informatie over het afdrukkanaal en het webkanaal naar [Kanaal en webkanaal afdrukken](/help/forms/using/web-channel-print-channel.md).

1. Selecteer **[!UICONTROL Create]**. De Interactieve Communicatie wordt gecreeerd en een waakzame doos verschijnt. Selecteren **[!UICONTROL Edit]** beginnen met het opbouwen van de inhoud van de interactieve communicatie, zoals uiteengezet in [Inhoud toevoegen met de gebruikersinterface voor interactieve communicatie](#step2). U kunt ook **[!UICONTROL Done]** en kiest u om de interactieve communicatie later te bewerken.

## Inhoud toevoegen aan de interactieve communicatie {#step2}

Nadat u een Interactieve Communicatie hebt gecreeerd, kunt u de Interactieve Communicatie auteursinterface gebruiken om zijn inhoud te construeren.

Voor meer informatie over de Interactieve Communicatie auteursinterface, zie [Inleiding tot interactieve communicatie authoring](/help/forms/using/introduction-interactive-communication-authoring.md).

1. De interactieve Communicatie auteursinterface wordt gelanceerd wanneer u uitgezocht geeft zoals vermeld in [Interactieve communicatie maken](#createic). Alternatief, kunt u aan een bestaand Interactief Communicatie middel op AEM navigeren, het selecteren, en selecteren **[!UICONTROL Edit]** om de Interactieve Communicatie auteursinterface te lanceren.

   Standaard wordt het afdrukkanaal van de interactieve communicatie weergegeven, tenzij Interactieve communicatie alleen via het web plaatsvindt. In het afdrukkanaal van de interactieve communicatie worden de doelgebieden weergegeven die beschikbaar zijn in de geselecteerde XDP/afdruksjabloon. In deze doelgebieden en -velden kunt u componenten of elementen toevoegen.

1. Selecteer het kanaal Afdrukken en selecteer de optie **[!UICONTROL Components]** tab. De volgende componenten zijn beschikbaar in het afdrukkanaal:

   | **Component** | **Functionaliteit** |
   |---|---|
   | Diagram | Hiermee voegt u een grafiek toe die u in Interactieve communicatie kunt gebruiken voor de visuele weergave van tweedimensionale gegevens die zijn opgehaald uit een verzameling formuliergegevensmodellen. Zie voor meer informatie [Het gebruiken van grafieken in Interactieve Communicatie](/help/forms/using/chart-component-interactive-communications.md). |
   | Documentfragment | Hiermee kunt u een herbruikbare component, zoals tekst, lijst of voorwaarde, toevoegen aan een interactieve communicatie. De toegevoegde component kan gebaseerd zijn op een formuliergegevensmodel of zonder een formuliergegevensmodel. |
   | Afbeelding | Hiermee kunt u een afbeelding invoegen. |

   De belemmering-en-daling de componenten in uw Interactieve Communicatie en vormt hen zoals vereist.

   U kunt ook de bewerkingen Ongedaan maken en Opnieuw gebruiken tijdens het ontwerpen van een interactieve communicatie voor zowel de afdruk- als de webkanalen.

   Gebruik de bewerking Ongedaan maken om de laatst uitgevoerde actie te verwijderen en de bewerking Opnieuw om de verwijderde actie opnieuw op te nemen. Als u bijvoorbeeld een afbeelding hebt ingevoegd of een gegevensbinding hebt gemaakt in een interactieve communicatie en deze moet verwijderen, gebruikt u de bewerking Ongedaan maken.

   ![Opnieuw Handelingen ongedaan maken](assets/undo_redo_actions_new.png)

   De opties voor Ongedaan maken en Opnieuw worden weergegeven op de werkbalk van de pagina UI-ontwerppagina. De optie Ongedaan maken wordt alleen weergegeven nadat een handeling is uitgevoerd. De optie Opnieuw uitvoeren wordt alleen op de paginabalk weergegeven nadat een bewerking Ongedaan maken is uitgevoerd. Deze handelingen worden opnieuw ingesteld bij het vernieuwen van de pagina.

1. Selecteer het afdrukkanaal en ga naar het **[!UICONTROL Assets]** en pas het filter toe om alleen de elementen weer te geven die u wilt zien.

   Met behulp van de middelenbrowser kunt u ook rechtstreeks elementen slepen en neerzetten in interactieve communicatiedoelgebieden.

   ![assets-docfragmenten](assets/assets-docfragments.png)

1. Sleep de documentfragmenten naar de interactieve communicatie. Hier volgen de typen documentfragmenten die u kunt gebruiken in het afdrukkanaal van de interactieve communicatie.

<table>
 <tbody>
  <tr>
   <td><strong>Type documentfragment</strong></td>
   <td><strong>Voorbeeld</strong></td>
  </tr>
  <tr>
   <td><a href="/help/forms/using/texts-interactive-communications.md" target="_blank">Tekst</a></td>
   <td>Tekst voor het toevoegen van het adres, de e-mail van de ontvanger en de platte tekst van de brief </td>
  </tr>
  <tr>
   <td><a href="/help/forms/using/conditions-interactive-communications.md" target="_blank">Voorwaarde</a></td>
   <td>Voorwaarde om de juiste koptekstafbeelding aan de communicatie toe te voegen op basis van het type beleid: Standaard of Premium. <br /> </td>
  </tr>
  <tr>
   <td>Lijst</td>
   <td>Groep documentfragmenten, zoals tekst, voorwaarden, andere lijsten en afbeeldingen. <br /> </td>
  </tr>
 </tbody>
</table>

U kunt de binding tussen een doelgebied en een documentfragment ook vervangen door het nieuwe fragment in het doelgebied neer te zetten met de opdracht **[!UICONTROL Assets]** tab. De blauwe kleurschaduw van het doelgebied tijdens het slepen van het fragment geeft aan dat het documentfragment naar het doelgebied kan worden neergezet.

Zie voor meer informatie over documentfragmenten [Documentfragmenten](/help/forms/using/document-fragments.md).

Met de ontwerpinterface kunt u onderscheid maken tussen de niet-gebonden en gebonden velden en variabelen in een interactieve communicatie. De interface markeert de niet-gebonden velden en variabelen met een oranje rand.

![unbound_fields_variables_highlight_dc](assets/unbound_fields_variables_highlights_dc.jpg)

Wanneer u de muisaanwijzer op deze elementen plaatst, wordt bovendien knopinfo weergegeven met het bericht Veld (niet geconsolideerd) of Variabele (niet geconsolideerd).

Een niet-gebonden variabele die in een documentfragment wordt gebruikt, wordt soms niet weergegeven in de ontwerpinterface. Dit kan gebeuren door een inline tekstregel in een documentfragment of als er een voorwaardelement is. In dergelijke gevallen wordt knopinfo, gemarkeerd in blauw, weergegeven als onderdeel van het documentfragment. In de knopinfo wordt het aantal niet-gebonden variabelen weergegeven dat in een documentfragment wordt gebruikt.

![Niet-gebonden variabele](assets/df_unbound_variable_new.png)

Selecteer het documentfragment ![configure_icon](assets/configure_icon.png) (Configureren) en selecteer vervolgens **[!UICONTROL Properties]** van de assistent van de interactieve communicatie. De **[!UICONTROL Variables and Data Model Objects]** bevat een lijst met de variabelen, inclusief de verborgen variabelen en de gegevensmodelobjecten die in de documentfragmenten worden gebruikt. Gebruik de ![bewerken](assets/edit.svg) (Bewerken) naast elk gegevensmodelobject of elke variabele om de eigenschappen te bewerken.

1. Selecteer een variabele en selecteer ![configure_icon](assets/configure_icon.png) (Configureer) en stel vervolgens de bindingseigenschappen in het deelvenster Eigenschappen in het zijpaneel in.

   * **Geen**: Agent vult de waarde voor de variabele in.
   * **Tekstfragment**: Als deze optie is geselecteerd, kunt u door een tekstdocumentfragment bladeren en dit selecteren waarvan de inhoud in het veld wordt gerenderd. Alleen tekstdocumentfragmenten kunnen worden gebonden aan variabelen die geen variabelen bevatten.
   * **Gegevensmodelobject**: Selecteer een eigenschap van het formuliergegevensmodel waarvan de waarde in het veld is ingevuld.
   * **Standaardwaarde:** U kunt een standaardwaarde voor de variabele bepalen gebruikend dit gebied. De waarde wordt getoond wanneer u voorproef de Interactieve Communicatie of in de Agent UI.
   * **Weergavepatroon:** U kunt ook een weergave-indeling voor een variabele definiëren. Selecteer een van de vooraf gedefinieerde opties in het menu **Type** vervolgkeuzelijst om een weergaveformaat toe te passen op een variabele. Selecteren **Aangepast** om een weergavepatroon te definiëren dat niet beschikbaar is in de lijst. Zie voor meer informatie [Weergavepatronen voor gegevens](../../forms/using/create-interactive-communication.md#datadisplaypatterns).

   Navigeren naar [Variabelen en gegevensmodelobjecten](../../forms/using/create-interactive-communication.md#hiddenvariables) Hiermee stelt u de binding in van verborgen variabelen in het documentfragment.

   U kunt ook gegevensbronelementen of tekstdocumentfragmenten slepen en neerzetten om de binding van variabelen in te stellen.  Als u een binding wilt maken met gegevensbronelementen, selecteert u de optie **Gegevensbronnen** en sleep het element naar de naam van de variabele. Het gegevensbronelement en de variabele moeten van het zelfde type zijn aan opstelling met succes bindt. Als u een gegevensbronelement naar een reeds gebonden variabele sleept, vervangt het nieuwe element vorige om een band met de variabele tot stand te brengen. Selecteer op dezelfde manier de **Activa** en sleep het tekstdocumentfragment naar de naam van een variabele om de binding tussen de fragmenten in te stellen. Het tekstdocumentfragment mag geen variabelen bevatten.

1. Als u een tabel wilt toevoegen met het afdrukkanaal geselecteerd in het dialoogvenster **[!UICONTROL Assets]** past u het filter toe om alleen de layoutfragmenten weer te geven. Sleep het vereiste lay-outfragment naar de interactieve communicatie en zet het neer. Een lay-outfragment is gebaseerd op een XDP en kan worden gebruikt om grafische lay-outs of statische en dynamische lijsten in Interactieve Communicatie tot stand te brengen die met dynamische gegevens worden bevolkt.

   Voorbeeld: een lay-outtabel waarin de brutopremie, de loyaliteitskorting % en de beschikbaarheid van noodhulp langs de weg voor het oude en het nieuwe beleid worden weergegeven.

   Zie voor meer informatie over layoutfragmenten [Documentfragmenten](/help/forms/using/document-fragments.md).

1. Selecteer het afdrukkanaal in het dialoogvenster **[!UICONTROL Assets]** past u het filter toe op de weergave van afbeeldingen. Sleep de vereiste afbeeldingen naar de interactieve communicatie, bijvoorbeeld voor het bedrijfslogo.

   Bovendien, beheer het volgende in de Interactieve Mededeling:

   * [Grafieken toevoegen en configureren](/help/forms/using/chart-component-interactive-communications.md)
   * [Webkanaal synchroniseren met afdrukkanaal](../../forms/using/create-interactive-communication.md#synchronize)

      * Automatisch synchroniseren
      * Overerving annuleren
      * Overerving opnieuw inschakelen
      * Synchroniseren

   * [Bijlagen en bibliotheektoegang](../../forms/using/create-interactive-communication.md#attachmentslibrary)
   * [Eigenschappen van XDP/Layout-velden](../../forms/using/create-interactive-communication.md#xdplayoutfieldproperties)
   * [Regels toevoegen aan componenten](../../forms/using/create-interactive-communication.md#rules)

1. Overschakelen op **[!UICONTROL Web Channel]**. Het webkanaal wordt weergegeven in de interactieve communicatieeditor. Wanneer u voor het eerst van het kanaal van de Druk aan het kanaal van het Web overschakelt, vindt de automatische synchronisatie plaats. Zie voor meer informatie [Webkanaal synchroniseren via het afdrukkanaal](../../forms/using/create-interactive-communication.md#synchronize).

   Aangezien u in dit voorbeeld Afdrukken als stramien voor het web gebruikt, worden de plaatsaanduidingen, inhoud en gegevensbinding van het kanaal Afdrukken gesynchroniseerd met het webkanaal. U kunt de specifieke inhoud in het webkanaal echter wijzigen en aanpassen. [Overerving annuleren](#cancelinheritance) voor de doelgebieden en variabelen die met het afdrukkanaal zijn gegenereerd, zodat u de inhoud kunt aanpassen.

   ![webchannelmiddelen](assets/webchannelassets.png)

   Selecteer het documentfragment ![configure_icon](assets/configure_icon.png) (Configureren) en selecteer vervolgens **[!UICONTROL Properties]** van de assistent van de interactieve communicatie. De **[!UICONTROL Variables and Data Model Objects]** bevat een lijst met de variabelen, inclusief de verborgen variabelen en de gegevensmodelobjecten die in de documentfragmenten worden gebruikt. Gebruik de ![bewerken](assets/edit.svg) (Bewerken) naast elk gegevensmodelobject of elke variabele om de eigenschappen te bewerken. Daarnaast voor documentfragmenten die [automatisch gegenereerd](#synchronize) in het kanaal van het Web dat het kanaal van de Druk gebruikt, gebruik ![cancelovererving](assets/cancelinheritance.png) (Overerving annuleren), pictogram naast elk gegevensmodelobject en variabele naar [overerving annuleren](#cancelinheritance) en om ze te kunnen bewerken.

1. Om extra componenten in het kanaal van het Web toe te voegen, met het geselecteerde kanaal van het Web, selecteer **[!UICONTROL Components]**. De belemmering-en-dalingscomponenten in het Webkanaal van uw Interactieve Communicatie zoals vereist en ga te werk om hen te vormen.

   | Onderdelen | Functionaliteit |
   |---|---|
   | Diagram | Hiermee voegt u een grafiek toe die u in Interactieve communicatie kunt gebruiken voor de visuele weergave van tweedimensionale gegevens die zijn opgehaald uit een verzameling formuliergegevensmodellen. Zie voor meer informatie [Grafiekcomponent gebruiken](../../forms/using/chart-component-interactive-communications.md). |
   | Documentfragment | Hiermee kunt u een herbruikbare component, tekst, lijst of voorwaarde toevoegen aan een interactieve communicatie. De herbruikbare component die u toevoegt aan een interactieve communicatie kan gebaseerd zijn op een formuliergegevensmodel of geen formuliergegevensmodel. |
   | Afbeelding | Hiermee kunt u een afbeelding invoegen. |
   | Deelvenster | Hiermee kunt u een [Deelvenster](../../forms/using/create-interactive-communication.md#add-panel-component-to-the-web-channel) naar de interactieve communicatie. |
   | Tabel | Hiermee voegt u een tabel toe waarin u gegevens in rijen en kolommen kunt ordenen. |
   | Doelgebied | Hiermee voegt u een doelgebied in een webkanaal in om de webkanaalspecifieke componenten te ordenen. Het doelgebied is een normale container waarmee u webkanaalspecifieke componenten kunt groeperen. |
   | Tekst | Voegt rijke tekst aan het Webkanaal van een Interactieve Mededeling toe. Tekst kan ook formuliergegevensmodelobjecten gebruiken om de inhoud dynamisch te maken. |
   | Knop | Hiermee kunt u een [Knop](../../forms/using/create-interactive-communication.md#add-button-component-to-the-web-channel) naar de interactieve communicatie. Met de component Button kunt u naar andere interactieve communicatie, adaptieve formulieren, andere elementen zoals afbeeldingen of documentfragmenten of een externe URL navigeren. |
   | Scheidingsteken | Hiermee kunt u een horizontale lijn in een interactieve communicatie invoegen. Gebruik deze component om onderscheid te maken tussen secties in een correspondentie. U kunt bijvoorbeeld de sectie Scheidingsteken gebruiken om onderscheid te maken tussen Customer Details en Credit Card Details in een creditcardoverzicht. |

1. Voeg desgewenst elementen in uw webkanaal in.

   U kunt [voorproef uw Interactieve Communicatie](#previewic) om te zien hoe de afdruk- en webuitvoer van de interactieve communicatie eruitziet en door te gaan met het aanbrengen van wijzigingen, indien nodig.

## Voorbeeld van interactieve communicatie {#previewic}

U kunt de **Voorvertoning, optie** de weergave van de interactieve communicatie evalueren. Het Webkanaal van Interactieve Communicatie verstrekt ook een optie om ervaring van een Interactieve Mededeling voor diverse apparaten te simuleren. Bijvoorbeeld iPhone, iPad en Desktop. U kunt beide gebruiken **Voorvertoning** en **Emulator** ![liniaal](assets/ruler.png) in combinatie met elkaar de uitvoerbestanden van het web voor apparaten van verschillende schermgrootten voor te vertonen. De voorbeeldgegevens in de voorbeeldweergave worden gevuld vanuit het opgegeven gegevensmodel voor formulieren.

1. Selecteer het kanaal (afdrukken of web) voor een voorvertoning en selecteer een voorvertoning. De interactieve communicatie wordt weergegeven.

   >[!NOTE]
   >
   >Het voorbeeld wordt gevuld met de voorbeeldgegevens van het opgegeven formuliergegevensmodel. Voor meer informatie bij het voorvertonen van de Interactieve Communicatie met wat andere gegevens of het gebruiken van de Prefill dienst, zie [Formuliergegevensmodel gebruiken](/help/forms/using/using-form-data-model.md) en [Werken met formuliergegevensmodel](/help/forms/using/work-with-form-data-model.md).

1. Gebruik voor het webkanaal ![liniaal](assets/ruler.png) om te bekijken hoe de Interactieve Communicatie op diverse apparaten kijkt.

   ![webchannelvoorvertoning](assets/webchannelpreview.png)

Verder kunt u [Bereid en verzend Interactieve Communicatie gebruikend de Agent UI voor](/help/forms/using/prepare-send-interactive-communication.md).

## Eigenschappen configureren in interactieve communicatie  {#configure-properties-in-interactive-communication}

### Bijlagen en bibliotheektoegang {#attachmentslibrary}

In het kanaal van de Druk, kunt u de gehechtheid en bibliotheektoegang vormen om de Agent toe te staan beheer gehechtheid in de Agent UI voor de Interactieve Mededeling:

1. Markeer in het kanaal Afdrukken de documentcontainer en selecteer **Eigenschappen**.

   ![documentcontainereigenschappen](assets/documentcontainerproperties.png)

   Het deelvenster Eigenschappen wordt weergegeven in het zijpaneel.

   ![eigenschappen, bijlagen](assets/propertiesattachments.png)

1. Uitbreiden **Bijlagen** en geeft u de volgende eigenschappen op:

   * **[!UICONTROL Allow Library Access]**: Selecteer om bibliotheektoegang voor de agent in de Agent UI toe te laten. Indien toegelaten, kan de Agent dossiers van de bibliotheek toevoegen terwijl het voorbereiden van de Interactieve Communicatie.
   * **[!UICONTROL Allow Re-Ordering Of Attachments]**: Selecteer om de Agent toe te laten om de gehechtheid met de Interactieve Mededeling opnieuw in orde te brengen.
   * **[!UICONTROL Max Number Of Attachments Allowed]**: Geef het maximumaantal toegestane bijlagen voor de interactieve communicatie op.
   * **[!UICONTROL Files To Be Attached]**: Select **[!UICONTROL Add]** en blader naar de geselecteerde bestanden die u wilt bijvoegen en geef de volgende instellingen op:

      * **[!UICONTROL Attach This File To Document By Default]**: U kunt deze optie wijzigen als alleen de bijlage niet verplicht is.
      * **[!UICONTROL Mandatory:]** De agent zal niet de gehechtheid in de Agent UI kunnen verwijderen.

   ![bijlagen](assets/attachfiles.png)

1. Selecteren **[!UICONTROL Done]**.

### Eigenschappen van XDP/Layout-velden {#xdplayoutfieldproperties}

1. Houd de muisaanwijzer tijdens het bewerken van het kanaal Afdrukken van een interactieve communicatie boven een veld dat is ingebouwd in de sjabloon Afdrukkanaal en selecteer ![configure_icon](assets/configure_icon.png) (Configureren).

   Het dialoogvenster Eigenschappen wordt weergegeven in het zijpaneel.

   ![data_display_patterns_fields](assets/data_display_patterns_fields.jpg)

1. Geef het volgende op:

   * **[!UICONTROL Name]**: JCR-knooppuntnaam.
   * **[!UICONTROL Title]**: Ga een titel in die aan de Agent in de Agent UI en in de boom van de Container van het Document zichtbaar zal zijn.
   * **[!UICONTROL Binding Type]**: Selecteer een van de volgende bindingstypen voor het veld.

      * Geen: de agent vult de waarde voor het bezit in.
      * Tekstfragment: als deze optie is geselecteerd, kunt u door een tekstdocumentfragment bladeren en dit selecteren waarvan de inhoud in het veld wordt gerenderd. U kunt ook het tekstdocumentfragment naar de veldnaam slepen en neerzetten om de binding tussen de tekstfragmenten in te stellen. Het tekstdocumentfragment mag geen variabelen bevatten.
      * Gegevensmodelobject: selecteer een formuliergegevensmodeleigenschap waarvan de waarde in het veld is ingevuld. U kunt ook de **Gegevensbronnen** en sleep de eigenschap naar het veld.

   * **[!UICONTROL Default Values]**: De standaardwaarde zorgt ervoor dat het veld niet leeg is wanneer het opgegeven gegevensmodelobject of tekstfragment geen waarde bevat. Als het type gegevensbinding geen is, wordt de standaardwaarde in het veld vooraf ingevuld.
   * **[!UICONTROL Display Pattern]**: U kunt ook een weergave-indeling voor een veld definiëren. Selecteer een van de vooraf gedefinieerde opties in het menu **Type** vervolgkeuzelijst om een weergaveformaat toe te passen op een veld. Selecteren **Aangepast** om een weergavepatroon te definiëren dat niet beschikbaar is in de lijst. Zie voor meer informatie [Weergavepatronen voor gegevens](../../forms/using/create-interactive-communication.md#datadisplaypatterns)

   * **[!UICONTROL Editable By Agent]**: Selecteer om de agent toe te staan om de waarde op het gebied in de Agent UI uit te geven. Deze instelling is niet van toepassing als Type binding tekstfragment is.
   * **[!UICONTROL Label]**: Specificeer een tekstkoord dat met het gebied aan de Agent in Agent UI wordt getoond. Deze instelling is niet van toepassing als Type binding tekstfragment is.
   * **[!UICONTROL Tooltip]**: Ga een tekstkoord in dat op muis over aan de Agent in Agent UI zichtbaar zal zijn. Deze instelling is niet van toepassing als Type binding tekstfragment is.
   * **[!UICONTROL Required]**: Selecteer deze optie om het veld verplicht te maken voor de Agent. Deze instelling is niet van toepassing als Type binding tekstfragment is.
   * **[!UICONTROL Allow multiple lines]**: Selecteer dit veld als u meerdere tekstregels als invoer in het veld wilt toestaan. Deze instelling is niet van toepassing als Type binding tekstfragment is.

1. Selecteren ![done_icon](assets/done_icon.png).

### Weergavepatronen voor gegevens {#datadisplaypatterns}

Met de ontwerpinterface kunt u gegevenspatronen definiëren voor velden, variabelen en formuliergegevensmodelelementen die beschikbaar zijn tijdens het maken van een interactieve communicatie voor afdruk- en webkanalen.

Selecteer het element om het weergavepatroon van de gegevens te configureren ![configure_icon](assets/configure_icon.png) (Configureren) en stel het weergavepatroon in het dialoogvenster **[!UICONTROL Properties]** in de zijbalk. Selecteer een vooraf gedefinieerde optie in het menu **[!UICONTROL Type]** vervolgkeuzelijst om het patroon weer te geven dat aan de geselecteerde tekst is gekoppeld. Selecteren **[!UICONTROL Custom]** van de **[!UICONTROL Type]** een patroon definiëren dat niet beschikbaar is in de lijst. Waarden bewerken in het dialoogvenster **[!UICONTROL Pattern]** veld wijzigt de tekst automatisch in **[!UICONTROL Custom]**.

Als u het weergavepatroon wilt toepassen, moet het aantal tekens of cijfers dat in het veld Patroon is gedefinieerd, overeenkomen met of groter zijn dan de tekens of cijfers die in de waarde voor velden, variabelen en formuliergegevensmodelelementen zijn gedefinieerd. Zie voor meer informatie [voorbeeld](../../forms/using/create-interactive-communication.md#greaternumberofdigits).

![data_display_pattern_example](assets/data_display_patterns_ssn_new.png)

Nadat u webinhoud hebt gegenereerd vanuit het afdrukkanaal, kunt u het weergavepatroon voor een veld, variabele of formuliergegevensmodelelement opnieuw definiëren. Dientengevolge, kan een element verschillende vertoningspatronen hebben die voor druk en Webkanalen worden bepaald. Als u geen weergavepatroon definieert voor een element in een afdrukkanaal en webinhoud automatisch genereert met behulp van een afdrukkanaal, worden met de gegevensbinding die voor het element in het afdrukkanaal is gedefinieerd, de weergavepatroon-opties gedefinieerd die beschikbaar zijn in het dialoogvenster **[!UICONTROL Type]** vervolgkeuzelijst. Als er geen binding is gedefinieerd voor het element, definieert het gegevenstype van het element de beschikbare opties voor weergavepatronen. Als u bijvoorbeeld een gegevensbinding van het type Number maakt voor een element in een afdrukkanaal, zijn de opties voor weergavepatronen beschikbaar in het dialoogvenster **[!UICONTROL Type]** de vervolgkeuzelijst is van het type Number in verschillende indelingen.

Schakel over naar de **Voorvertoning** modus of open Agent-interface om het weergavepatroon weer te geven dat op deze elementen is toegepast.

In de volgende tabel ziet u een voorbeeld van de waarden die worden weergegeven als gevolg van het instellen van het weergavepatroon voor gegevens van een variabele:

| Type | Standaardwaarde | Weergavepatroon | Weergavewaarde | Beschrijving |
|---|---|---|---|---|
| SocialSecurityNumber | 123456789 | text{999-99-9999} | 123-45-6789 | Het aantal cijfers in het veld Standaardwaarde komt overeen met het aantal cijfers in het veld Patroon. De waarde op basis van het patroon wordt weergegeven. |
| SocialSecurityNumber | 1234567 | text{999-99-9999} | 23-4567 | Het aantal cijfers in het veld Standaardwaarde is kleiner dan het aantal cijfers in het veld Patroon. Het patroon wordt toegepast op de 7 beschikbare cijfers. |
| SocialSecurityNumber | 1234567890 | text{999-99-9999} | 1234567890 | Het aantal cijfers in het veld Standaardwaarde is groter dan het aantal cijfers in het veld Patroon. Het resultaat is dat de weergavewaarde niet wordt gewijzigd. |

Als er geen weergavepatroon is opgegeven voor een variabele of een formuliergegevensmodelelement, [algemene fragmentconfiguratie van document](https://helpx.adobe.com//experience-manager/6-5/forms/using/interactive-communication-configuration-properties.html) wordt standaard gebruikt.

Als u geen weergavepatroon toepast op een variabele van het gegevenstype Number, wordt in de afdrukvoorbeeld het patroon weergegeven op basis van de algemene configuratie van het documentfragment. Als u veranderingen op de standaard globale configuratie van het documentfragment toepast, toont de UI van de Agent nog het patroon volgens de standaardseparators die voor de scène worden bepaald.

Als er voor velden geen weergavepatroon is opgegeven, wordt het patroon dat tijdens het maken van de afdruksjabloon (XDP) is gedefinieerd, op dezelfde manier op het veld toegepast. Als er geen patroon is tijdens het maken van de afdruksjabloon, worden de standaardpatronen op basis van XFA-specificaties toegepast op de velden.

Als het opgegeven weergavepatroon onjuist is of niet kan worden toegepast, worden de standaardpatronen op basis van XFA-specificaties toegepast op de velden, variabelen of elementen van het formuliergegevensmodel.

## Pas regels op Interactieve Communicatie componenten toe {#rules}

Om componenten of inhoud in de interactieve mededeling te conditionaliseren, selecteer de component/het stuk van inhoud en selecteer ![createruleus](assets/createruleicon.png) (Regel maken) om de Regel-editor te starten.

Zie voor meer informatie:

* [Regeleditor](/help/forms/using/rule-editor.md)
* [Inleiding tot interactieve communicatie authoring](/help/forms/using/introduction-interactive-communication-authoring.md)

## Werken met tabellen {#tables}

### Dynamische tabellen in interactieve communicatie {#dynamic-tables-in-interactive-communication}

U kunt dynamische tabellen toevoegen in Interactieve communicatie met behulp van lay-outfragmenten. De volgende stappen gebruiken een voorbeeld van een creditcardverklaring om het gebruik van een lay-outfragment voor het creëren van een dynamische lijst in een Interactieve Mededeling te illustreren.

1. Zorg ervoor dat het vereiste layoutfragment voor het maken van de tabel in AEM beschikbaar is.
1. Sleep in het afdrukkanaal van uw interactieve communicatie een lay-outfragment (met een tabel met meerdere kolommen) in een doelgebied vanuit de browser Asset.

   ![lf_dragdrop](assets/lf_dragdrop.png)

   Een tabel wordt weergegeven in het lay-outgebied Interactieve communicatie.

   ![lf_dragdrop_table](assets/lf_dragdrop_table.png)

1. Geef de gegevensbinding op voor elk van de cellen in de tabel. Als u een herhaalbare rij wilt maken, voegt u eigenschappen van het formuliergegevensmodel in de rij in die bij een algemene eigenschap voor de verzameling horen.

   1. Selecteer een cel in de tabel en selecteer ![configure_icon](assets/configure_icon.png) (Configureren).

      Het dialoogvenster Eigenschappen wordt weergegeven in het zijpaneel.

      ![lf_cell_properties](assets/lf_cell_properties.png)

   1. Configureer de eigenschappen:

      * **[!UICONTROL Name]**: JCR-knooppuntnaam.
      * **[!UICONTROL Title]**: Ga een titel in die in de Interactieve Communicatie redacteur zichtbaar zal zijn.
      * **[!UICONTROL Binding Type]**: Selecteer een van de volgende bindingstypen voor het veld.

         * **[!UICONTROL None]**
         * **[!UICONTROL Data model object]**: De waarde van een eigenschap van een formuliergegevensmodel wordt in het veld ingevuld. U kunt ook de **Gegevensbronnen** en sleep de eigenschap naar het veld.

      * **[!UICONTROL Data Model Object]**: De eigenschap van het gegevensmodel van het formulier waarvan de waarde in het veld wordt ingevuld.
      * **[!UICONTROL Default Value]**: De standaardwaarde zorgt ervoor dat het veld niet leeg is wanneer het opgegeven gegevensmodelobject geen waarde bevat. De standaardwaarde is vooraf ingevuld in het veld.

      * **[!UICONTROL Editable By Agent]**: Selecteer om de agent toe te staan om de waarde op het gebied in de Agent UI uit te geven.

   1. Selecteren ![done_icon](assets/done_icon.png).

1. Bekijk een voorvertoning van de interactieve communicatie om te zien welke tabel met de gegevens wordt weergegeven.

   ![lf_preview](assets/lf_preview.png)

### Alleen webkanalen {#webchanneltables}

Selecteer het wortelpaneel in het malplaatje van het Web en selecteer **+** om een **Tabel** aan de Interactieve Communicatie. In de interactieve communicatie wordt een tabel met twee rijen ingevoegd. De eerste rij van de tabel staat voor de tabelkop.

#### Rijen en kolommen toevoegen aan de tabel {#addrowscolumnstable}

**Kolommen toevoegen of verwijderen:**

1. Selecteer het standaardtekstvak in de tabelkoprij om de componentwerkbalk weer te geven.
1. Selecteren **Kolom toevoegen** of **Kolom verwijderen** om respectievelijk tabelkolommen toe te voegen of te verwijderen.

![component_toolbar_table1](assets/component_toolbar_table1.png)

**Rijen toevoegen of verwijderen:**

1. Selecteer een tabelrij om de werkbalk van de component weer te geven. U kunt ook tabelrij selecteren met de Inhoudsbrowser in de assistent van de Interactieve communicatie.
1. Selecteren **Rij toevoegen** of **Rij verwijderen** om respectievelijk tabelrijen toe te voegen of te verwijderen. Gebruik de **Omhoog** en **Omlaag** in de werkbalk kunt u de rijen in de tabel opnieuw rangschikken.

![Werkbalk Component](assets/component_toolbar_table_row_new.png)

**A.** Rij toevoegen **B.** Rij verwijderen **C.** Omhoog verplaatsen **D.** Omlaag verplaatsen

#### Tekst toevoegen of bewerken in tabelcellen {#addedittexttable}

1. Selecteer het standaardtekstvak in de tabelcel en selecteer ![bewerken](assets/edit.png) (Bewerken).
1. Typ de tekst in de tabelcel en selecteer ![done_icon](assets/done_icon.png) opslaan.

#### Binding maken tussen tabelcellen en objectelementen van gegevensmodellen {#createbindingtablecells}

1. Selecteer het standaardtekstvak in de tabelrij en selecteer ![bewerken](assets/edit.png) (Bewerken).
1. Selecteer de vervolgkeuzelijst Gegevensmodelobjecten en selecteer de eigenschap.
1. Selecteer deze optie om een binding tussen de tabelcel en de objecteigenschap van het gegevensmodel op te slaan en te maken.

![Gegevensbinding maken](assets/create_data_binding_table_new.png)

#### Een hyperlink maken voor tekst in de tabelcel {#createhyperlinktable}

1. Selecteer het standaardtekstvak in de tabelcel en selecteer ![bewerken](assets/edit.svg) (Bewerken).
1. Selecteer de tekst in de tabelcel en selecteer het pictogram Hyperlink.
1. Geef de URL op in het dialoogvenster **Pad** veld.
1. Selecteren ![done_icon](assets/done_icon.png) om de eigenschappen van de hyperlink op te slaan.

![Hyperlink maken](assets/create_hyperlink_table_new.png)

#### Dynamische tabellen maken {#createdynamictables}

U kunt een Web-kanaal slechts dynamische lijst in een Interactieve Mededeling tot stand brengen gebruikend een bezit van het gegevensmodel van typeinzameling. Een dergelijke tabel is een weergave van de onderliggende eigenschappen van een eigenschap van een verzameling. U kunt alleen de opmaakeigenschappen van de verschillende cellen in de tabel bewerken.

1. Ga naar het webkanaal en kies vervolgens om de browser Gegevensbronnen weer te geven.
1. Sleep een verzamelingseigenschap naar een subformulier. Er wordt een tabel gemaakt in het subformulier.
1. Geef een voorvertoning van de tabel weer in de webvoorvertoning van de interactieve communicatie.

#### Kolommen in een tabel sorteren {#sortcolumns}

U kunt gegevens sorteren die op om het even welke kolom in een lijst in de Interactieve Mededeling worden gebaseerd. De waarden in de kolom kunnen in oplopende of aflopende volgorde worden gesorteerd.

Sorteren kan worden toegepast op tabelkolommen met:

* Statische tekst
* Objecteigenschappen gegevensmodel
* Combinatie van statische tekst en eigenschappen van gegevensmodelobjecten

Sorteren inschakelen:

1. Selecteer de tabel en selecteer ![configure_icon](assets/configure_icon.png) (Configureren). U kunt de tabel ook selecteren met de **Inhoud** browser in het hulpje van de Interactieve Communicatie.
1. Selecteren **Sorteren inschakelen.**
1. Selecteren ![done_icon](assets/done_icon.png) om de tabeleigenschappen op te slaan. De sorteerpictogrammen, pijlen omhoog en omlaag, in kolomkoppen geven aan dat het sorteren is ingeschakeld.

   ![Sorteren inschakelen](assets/enable_sorting_new-1.png)

1. Schakel over naar de **Voorvertoning** om de uitvoer weer te geven. De tabel wordt automatisch gesorteerd op basis van de eerste kolom van de tabel.
1. Klik op de kolomkop om de waarden te sorteren op basis van de kolom.

   Een kolomkop met een pijl-omhoog geeft aan dat de instelling:

   * tabel wordt gesorteerd op basis van die kolom.
   * De waarden in de kolom worden in oplopende volgorde weergegeven.

   ![Oplopend sorteren](assets/sorting_ascending_new-1.png)

   Op dezelfde manier vertegenwoordigt een kolomkopbal met een benedenpijl dat de waarden in de kolom in dalende orde worden getoond.

## Interactieve communicatie-eigenschappen bewerken {#edit-interactive-communication-properties}

Zodra u een Interactieve Communicatie creeert, kunt u zijn eigenschappen in een recentere fase uitgeven.

Gebruik de **Eigenschappen** pagina naar:

* Bewerk waarden voor de opgegeven velden tijdens het maken van de interactieve communicatie, zoals Titel en Beschrijving.
* Voeg of schrap het kanaal van het Web voor bestaande Interactieve Mededeling toe.
* Interactieve communicatie voorvertonen, downloaden of verwijderen
* Open de [Gebruikersinterface van agent](/help/forms/using/prepare-send-interactive-communication.md).

Als u toegang wilt krijgen tot **Eigenschappen** pagina:

1. Meld u aan bij de AEM auteur en navigeer naar **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.
1. Selecteer de Interactieve Communicatie en selecteer **Eigenschappen**.
1. Selecteer de **Algemeen** tabblad om de **Titel** en **Beschrijving** velden.

### Het webkanaal toevoegen of verwijderen {#add-or-delete-the-web-channel}

Voer de volgende stappen uit om het kanaal van het Web voor een bestaande Interactieve Mededeling toe te voegen:

1. Op de **Eigenschappen** pagina, selecteert u de **Kanalen** tab.
1. Selecteer de **Web** en selecteer een malplaatje voor het kanaal van het Web.
1. Selecteren **Afdrukken als origineel voor webkanaal gebruiken** om synchronisatie tussen het kanaal van het Web en het kanaal van de Druk toe te laten.
1. Selecteren **Opslaan en sluiten** om de wijzigingen op te slaan

   Op dezelfde manier kunt u de opdracht **Web** Selectievakje op de **Kanalen** om het kanaal van het Web van de Interactieve Mededeling te schrappen.

## De component Button toevoegen aan het webkanaal {#add-button-component-to-the-web-channel}

U kunt knoop als component aan het Webkanaal van de Interactieve Communicatie toevoegen. Definieer regels met de [regeleditor](../../forms/using/rule-editor.md) om te kunnen navigeren naar andere interactieve communicatie, adaptieve formulieren, andere elementen zoals afbeeldingen of documentfragmenten, of een externe URL wanneer u de knop selecteert.

Om knoop toe te voegen en regels te bepalen over het:

1. Selecteer het wortelpaneel in het malplaatje van het Web en selecteer **+** om de **Knop** aan de Interactieve Communicatie.
1. Selecteer de component Button en selecteer ![bewerkingsregels](assets/edit-rules.png) om regels te definiëren voor het selecteren van de knop.
1. In de **Wanneer** sectie, selecteert u **geklikt** uit de status van de vervolgkeuzelijst met knoppen.
1. In de **Vervolgens** sectie:

   1. Selecteer een actie in de vervolgkeuzelijst. Selecteer bijvoorbeeld **Navigeren naar** als het handelingstype.

   1. Geef de URL van de interactieve communicatie, het adaptieve formulier, een element of een webpagina op. Geef bijvoorbeeld de URL op in de volgende notatie om naar een andere interactieve communicatie te navigeren: https://&lt;server-name>:&lt;port>/editor.html/content/forms/af/&lt;interactive communication=&quot;&quot; name=&quot;&quot;>/kanalen/&lt;channel name=&quot;&quot; print=&quot;&quot; or=&quot;&quot; web=&quot;&quot;>.html
   1. Geef de optie op om het element op hetzelfde tabblad, op een nieuw tabblad of in een nieuw venster te openen.
   1. Selecteren **Gereed** en selecteer vervolgens **Sluiten** om de regel op te slaan.

   Op dezelfde manier kunt u andere beschikbare opties selecteren in de vervolgkeuzelijst Type actie, zoals Invoke Service en Formulier verzenden. Zie voor meer informatie [regeleditor](../../forms/using/rule-editor.md).

1. Geef een voorvertoning van de interactieve communicatie weer en selecteer de knop om de interactieve communicatie, het adaptieve formulier, een element of een webpagina weer te geven die is opgegeven in stap 4 b).

## Deelvenstercomponent toevoegen aan het webkanaal {#add-panel-component-to-the-web-channel}

De component van het Comité is placeholder voor het groeperen van andere componenten samen en controleert hoe een groep componenten, zoals accordeon en lusjes, in de Interactieve Mededeling worden uiteengezet. Met een deelvenstercomponent kunt u ook een groep componenten herhaalbaar maken voor de eindgebruiker, bijvoorbeeld in meerdere items die nodig zijn om de gegevens van het onderwijs in te vullen.

Voer de volgende stappen uit om een component van het Comité aan het Webkanaal toe te voegen:

1. Voeg de **Deelvenster** in het webkanaal met een van de volgende opties:

   * Selecteer een component, selecteer **+** en selecteert u de **Deelvenster** component.

   * Van de **Component** browservenster, slepen en neerzetten **Deelvenster** component op de Interactieve Communicatie.

   * Selecteer de **Deelvenster** in de **Inhoud** browservenster en selecteer **Deelvenster Onderliggend element toevoegen**. De **Deelvenster Onderliggend element toevoegen** geeft de optie **Deelvenster Onderliggend element toevoegen** in. Voer de titel en een optionele beschrijving en naam voor de component Panel in.

1. Selecteer het deelvenster in het menu **Inhoud** browser om extra acties op het Comité uit te voeren zoals vorm, geef regels uit, kopieer, schrap, en neem component op.

   U kunt een deelvenster ook slepen en neerzetten in het dialoogvenster **Inhoud** browser om op de verandering in de structuur van de Interactieve Communicatie in de juiste ruit te wijzen.

## Webkanaal synchroniseren met afdrukkanaal {#synchronize}

Wanneer u Afdrukken als stramien voor webkanaal selecteert tijdens het maken van een interactieve communicatie, wordt het webkanaal in synchronisatie met het kanaal Afdrukken gemaakt en worden de inhoud en de gegevensbinding van het webkanaal afgeleid van het afdrukkanaal en kunnen de wijzigingen die in het afdrukkanaal zijn aangebracht, worden doorgevoerd in het webkanaal wanneer u Synchroniseren selecteert.

De auteurs mogen echter desgewenst de overerving voor componenten in het webkanaal verbreken.

![Stramien afdrukken maken](assets/create_ic_print_master_new-1.png) ![Stramienweb afdrukken](assets/create_ic_print_master_web_new-1.png)

### Automatisch synchroniseren {#autosync}

Als u **[!UICONTROL Use Print As Master for Web Channel]** kunt u een van de volgende modi selecteren om een webkanaal te genereren:

* **[!UICONTROL Auto layout]**: Selecteer deze modus om automatisch plaatsaanduidingen, inhoud en gegevensbinding voor het webkanaal te genereren via het kanaal Afdrukken.
* **[!UICONTROL Manually organize]**: Selecteer deze modus om de kanaalelementen van Afdrukken handmatig te selecteren en toe te voegen aan het webkanaal met behulp van de basisinhoud die beschikbaar is op het tabblad Gegevensbronnen. Zie voor meer informatie [Selecteer de kanaalelementen van de Druk om de inhoud van het Webkanaal te creëren](#selectprintchannelelements).

![IC-opties maken](assets/create_ic_options_updated_new.png)

>[!NOTE]
>
>Als u de kanalen synchroniseert, worden alleen de documentfragmenten, afbeeldingen, voorwaarden, lijsten en layoutfragmenten gesynchroniseerd van het afdrukkanaal naar het webkanaal. De subformulieren of bovenliggende knooppunten die dergelijke elementen bevatten, worden niet gesynchroniseerd.

### Selecteer de kanaalelementen van de Druk om de inhoud van het Webkanaal te creëren {#selectprintchannelelements}

Als u Afdrukken als stramien selecteert tijdens het maken van de interactieve communicatie en de optie voor automatische synchronisatie niet selecteert, kunt u ook de kanaalelementen van de Afdruk naar de ontwerpinterface van het webkanaal slepen en neerzetten.

Navigeren naar **Gegevensbronnen** > **Basisinhoud** om de de kanaalelementen van de Druk te bekijken. Sleep de doelgebieden, velden of tabellen naar de ontwerpinterface van het webkanaal en zet deze neer. Een blauw cirkelpictogram naast de elementnaam geeft aan dat het afdrukkanaalelement al in het webkanaal is opgenomen.

![Basisinhoud](assets/master_content.png)

### Overerving annuleren {#cancelinheritance}

In het webkanaal worden de componenten ingesloten in de doelgebieden.

Houd de muisaanwijzer boven het desbetreffende doelgebied of de desbetreffende variabele in het webkanaal en selecteer ![cancelovererving](assets/cancelinheritance.png) (Overerving annuleren) en selecteer vervolgens in het dialoogvenster Overerving annuleren **[!UICONTROL Yes]**.

De overerving van de componenten binnen het doelgebied wordt geannuleerd en u kunt ze nu naar wens bewerken.

### Overerving opnieuw inschakelen {#re-enable-inheritance}

In het kanaal van het Web, als u overerving van een component hebt geannuleerd, kunt u het re-toelaten. Als u overerving weer wilt inschakelen, plaatst u de cursor boven de grens van het desbetreffende doelgebied, dat de component omvat, en selecteert u ![reenableerbaarheid](assets/reenableinheritance.png).

Het dialoogvenster Overerving herstellen wordt weergegeven.

![revertovererving](assets/revertinheritance.png)

Selecteer indien nodig **[!UICONTROL Synchronize The Page After Reverting Inheritance]**. Selecteer deze optie om de volledige interactieve communicatie te synchroniseren. Als u deze optie niet selecteert, wordt alleen het desbetreffende doelgebied gesynchroniseerd bij het opnieuw instellen van de overerving.

Selecteren **[!UICONTROL Yes]**.

### Synchroniseren {#synchronize-1}

Als u Afdrukken als stramien voor webkanaal gebruikt en het kanaal Afdrukken wijzigt, kunt u de inhoud synchroniseren om de zojuist aangebrachte wijzigingen door te voeren in het webkanaal.

1. Als u het webkanaal wilt synchroniseren met het kanaal Afdrukken, schakelt u over naar het kanaal Web en selecteert u het pictogram Meer opties.

   ![Opties voor automatisch synchroniseren](assets/auto_sync_options_new.png)

1. Selecteer een van de volgende opties:

   * **[!UICONTROL Sync with Print]**: Hiermee wordt de inhoud alleen gesynchroniseerd voor de doelgebieden waarin overname niet is geannuleerd.
   * **[!UICONTROL Reset]**: Hiermee synchroniseert u de webkanaalinhoud met het kanaal Afdrukken en verwijdert u alle wijzigingen die in het webkanaal zijn aangebracht.

### De componententoolbar van het gebruik om acties op geërfte componenten uit te voeren {#componenttoolbar}

Als u automatisch gegenereerde inhoud in het webkanaal hebt met de optie Synchroniseren, kunt u meer acties op componenten uitvoeren zonder dat de overerving wordt geannuleerd.

![Werkbalk Component](assets/component_toolbar_inherited_web_new.png)

Selecteer de component om de volgende opties weer te geven:

* **Kopiëren:** Kopieer een component en plak deze op andere plaatsen in de interactieve communicatie.
* **Knippen:** Verplaats een component van één plaats naar een andere in de Interactieve Communicatie.
* **Component invoegen:** Voeg een component in boven de geselecteerde component.
* **Plakken:** Plak de component die u hebt geknipt of gekopieerd met de hierboven beschreven opties.
* **Groep:** Selecteer meerdere componenten als u meerdere componenten tegelijk wilt knippen, kopiëren of plakken.
* **Bovenliggend element:** Selecteer het bovenliggende element van een component.
* **SOM-expressie weergeven:** De weergave [SOM-expressie](../../forms/using/using-som-expressions-adaptive-forms.md) voor de component.

* **Objecten groeperen in deelvenster:** Groepeer de componenten in een paneel om verrichtingen op die componenten gelijktijdig kunnen uitvoeren. Zie voor meer informatie [Objecten groeperen in deelvenster](#groupobjectspanel).

* **Overerving annuleren:** [De overerving annuleren](#cancelinheritance) van de componenten binnen het doelgebied om hen uit te geven.

### Objecten groeperen in deelvenster {#groupobjectspanel}

Met de ontwerpinterface voor webkanalen kunt u de componenten groeperen in een deelvenster en vervolgens tegelijkertijd bewerkingen op die componenten uitvoeren. De **Inhoud** worden de gegroepeerde componenten als onderliggende elementen van het deelvenster in de inhoudsstructuur weergegeven.

1. Selecteer een component en selecteer de groep ( ![groep](assets/group.jpg)).
1. Selecteer meerdere componenten en selecteer **Objecten groeperen in deelvenster**.

   ![Objecten groeperen](assets/component_toolbar_group_objects_new.png)

1. In de **Objecten groeperen in deelvenster** voert u een naam in voor het deelvenster.
1. Voer een optionele titel en beschrijving in voor het deelvenster.
1. Klikken ![bullet_checkmark](assets/bullet_checkmark.png).

   De gegroepeerde componenten worden als onderliggende elementen van het deelvenster weergegeven in de inhoudsstructuur.

   ![content_tree_grouping](assets/content_tree_grouping.png)

## Uitvoerindeling voor afdrukkanaal {#output-format-print-channel}

Gebruik PrintChannel API om uitvoerindeling te definiëren voor het afdrukkanaal van een interactieve communicatie. Als u geen uitvoerindeling definieert, genereert AEM Forms de uitvoer in PDF-indeling.

```javascript
//options for rendering print channel of a multi-channel document
PrintChannelRenderOptions renderOptions = new PrintChannelRenderOptions();
PrintDocument printDocument = printChannel.render(renderOptions);
```

Als u de uitvoer in een andere indeling wilt genereren, geeft u het type uitvoerindeling op. Zie [PrintChannel-API](https://helpx.adobe.com/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/PrintConfig.html) voor de lijst met ondersteunde uitvoerindelingstypen.

U kunt bijvoorbeeld het volgende voorbeeld gebruiken om PCL als uitvoerindeling voor een interactieve communicatie te definiëren:

```javascript
//options for rendering print channel of a multi-channel document
PrintChannelRenderOptions renderOptions = new PrintChannelRenderOptions();
renderOptions.setRenderFormat(PrintConfig.HP_PCL_5e);
PrintDocument printDocument = printChannel.render(renderOptions);
```
