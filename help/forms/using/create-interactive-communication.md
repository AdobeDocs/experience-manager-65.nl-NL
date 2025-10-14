---
title: Een interactieve communicatie maken
description: Creeer een Interactieve Mededeling gebruikend de Interactieve Communicatie redacteur. Gebruik de functie voor slepen en neerzetten om de interactieve communicatie te maken en een voorvertoning van zowel afdruk- als webuitvoer weer te geven voor verschillende apparaattypen.
topic-tags: interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Interactive Communication
exl-id: 1f89c3bf-e67e-4d13-9285-3367be1ac8f8
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '5956'
ht-degree: 0%

---

# Een interactieve communicatie maken{#create-an-interactive-communication}

## Overzicht {#overview}

De interactieve Mededelingen centraliseren en beheert de verwezenlijking, de assemblage, en de levering gepersonaliseerde, en interactieve correspondentie. Met Afdrukken als hoofdkanaal voor het web kunt u dubbel werk minimaliseren bij het maken van de webinvoer van de interactieve communicatie.

### Vereisten {#prerequisites}

Het volgende is de eerste vereisten voor het creëren van een Interactieve Mededeling:

* Opstelling het Model van de Gegevens van de a [&#x200B; Vorm &#x200B;](/help/forms/using/data-integration.md) die testgegevens of met een daadwerkelijke gegevensbron, zoals een geval van de Dynamica Microsoft® bevatten.
* Zorg ervoor dat u de [&#x200B; fragmenten van het Document &#x200B;](/help/forms/using/document-fragments.md) hebt.
* Zorg ervoor dat u [&#x200B; Malplaatjes voor druk en Webkanaal &#x200B;](/help/forms/using/web-channel-print-channel.md) hebt.
* Zorg ervoor dat u het vereiste [&#x200B; thema &#x200B;](/help/forms/using/themes.md) voor het Webkanaal hebt.

## Interactieve communicatie maken {#createic}

1. Meld u aan bij de AEM auteur en navigeer naar **[!UICONTROL Adobe Experience Manager]** > **[!UICONTROL Forms]** > **[!UICONTROL Forms & Documents]** .
1. Selecteer **[!UICONTROL Create]** en selecteer **[!UICONTROL Interactive Communication]** . De pagina Interactieve communicatie maken wordt weergegeven.

   ![&#x200B; creeer-interactief-mededeling &#x200B;](assets/create-interactive-communication.png)

1. Voer de volgende gegevens in. :

   * **[!UICONTROL Title]**: voer de titel van de interactieve communicatie in.
   * **[!UICONTROL Name]**: De naam van de Interactieve Communicatie wordt afgeleid van de titel u ingaat. Bewerk indien nodig de selectie.
   * **[!UICONTROL Description]**: voer een beschrijving in over de interactieve communicatie.
   * **[!UICONTROL Form Data Model]**: blader en selecteer het model van vormgegevens. Voor meer informatie over het Model van de Gegevens van de Vorm, zie [&#x200B; de Integratie van Gegevens van AEM Forms &#x200B;](/help/forms/using/data-integration.md).

   * **[!UICONTROL Prefill Service]**: selecteer de Prefill-service om de gegevens op te halen en de interactieve communicatie vooraf in te vullen.
   * **[!UICONTROL Post Process Type]**: U kunt AEM of Forms-workflow selecteren die moet worden geactiveerd wanneer de interactieve communicatie wordt verzonden. Selecteer het type workflow dat moet worden geactiveerd.

   * **[!UICONTROL Post Process]**: selecteer de naam van de workflow die moet worden geactiveerd. Wanneer u AEM werkstroom selecteert, verstrekt de Weg van de Bijlage, de Weg van de Lay-out, de Weg van de PDF, de Weg van Gegevens van de Druk, en de Weg van Gegevens van het Web.
   * **[!UICONTROL Tags]**: selecteer de tags die u wilt toepassen op interactieve communicatie. U kunt ook een nieuwe/aangepaste tagnaam typen en op Enter drukken om deze te maken.
   * **[!UICONTROL Author]**:De auteursnaam wordt automatisch genomen van de het programma geopende gebruikersnaam.
   * **[!UICONTROL Publish Date:]** Voer de datum in waarop u de interactieve communicatie wilt publiceren.
   * **[!UICONTROL Unpublish Date]**: voer de datum in waarop u de publicatie van de interactieve communicatie ongedaan wilt maken.

1. Selecteer **[!UICONTROL Next]**. Het scherm waarop u afdruk- en webkanaalgegevens wilt opgeven, wordt weergegeven.
1. Voer het volgende in:

   * **[!UICONTROL Print]**: selecteer deze optie om het afdrukkanaal van de interactieve communicatie te genereren.
   * **[!UICONTROL Print Template]**: blader en selecteer XDP als drukmalplaatje.
   * **[!UICONTROL Web]**: selecteer deze optie om het webkanaal of de responsieve uitvoer van Interactieve communicatie te genereren.
   * **[!UICONTROL Interactive Communication Web Template]**: blader en selecteer het Webmalplaatje.
   * **[!UICONTROL Theme]** en **[!UICONTROL Select Theme]**: Blader en selecteer het thema waarmee u het webkanaal van de interactieve communicatie wilt opmaken. Voor meer informatie, zie [&#x200B; Thema&#39;s in AEM Forms &#x200B;](/help/forms/using/themes.md).

   * **[!UICONTROL Use Print As Master for Web Channel]**: selecteer deze optie om het webkanaal synchroon met het afdrukkanaal te maken. Als u het afdrukkanaal als stramien voor het webkanaal gebruikt, zorgt u ervoor dat de inhoud en de gegevensbinding van het webkanaal worden afgeleid van het afdrukkanaal en dat de wijzigingen die u in het afdrukkanaal hebt aangebracht, worden weerspiegeld in het webkanaal wanneer u Synchroniseren selecteert. De auteurs mogen echter desgewenst de overerving voor specifieke componenten in het webkanaal verbreken. Voor meer informatie, zie [&#x200B; Kanaal van het Web met het kanaal van de Druk &#x200B;](../../forms/using/create-interactive-communication.md#synchronize) synchroniseren.
Als u de optie **[!UICONTROL Use Print As Master for Web Channel]** selecteert, kunt u een van de volgende modi selecteren om een webkanaal te genereren:

      * **[!UICONTROL Auto layout]**: selecteer deze modus om automatisch plaatsaanduidingen, inhoud en gegevensbinding voor het webkanaal te genereren via het kanaal Afdrukken.
      * **[!UICONTROL Manually organize]**: selecteer deze modus om handmatig kanaalelementen afdrukken naar het webkanaal te selecteren en toe te voegen met behulp van de basisinhoud die beschikbaar is op het tabblad **[!UICONTROL Data Sources]** . Voor meer informatie, zie [&#x200B; Uitgezochte het kanaalelementen van de Druk om het kanaalinhoud van het Web &#x200B;](#selectprintchannelelements) tot stand te brengen.

   Voor meer informatie over drukkanaal en Webkanaal, zie [&#x200B; het kanaal van de Druk en Webkanaal &#x200B;](/help/forms/using/web-channel-print-channel.md).

1. Selecteer **[!UICONTROL Create]**. De Interactieve Communicatie wordt gecreeerd en een waakzame doos verschijnt. Selecteer **[!UICONTROL Edit]** beginnen de inhoud van de Interactieve Mededeling te bouwen zoals die in [&#x200B; wordt verklaard inhoud gebruikend Interactieve Communicatie auteursgebruikersinterface &#x200B;](#step2) toevoegt. U kunt ook **[!UICONTROL Done]** selecteren en ervoor kiezen om de interactieve communicatie later te bewerken.

## Inhoud toevoegen aan de interactieve communicatie {#step2}

Nadat u een Interactieve Communicatie hebt gecreeerd, kunt u de Interactieve Communicatie auteursinterface gebruiken om zijn inhoud te construeren.

Voor meer informatie over de Interactieve Communicatie auteursinterface, zie [&#x200B; Inleiding aan Interactieve Communicatie authoring &#x200B;](/help/forms/using/introduction-interactive-communication-authoring.md).

1. De Interactieve Communicatie auteursinterface wordt gelanceerd wanneer u uitgezocht geeft zoals vermeld in [&#x200B; Interactieve Communicatie &#x200B;](#createic) tot stand brengen. U kunt ook naar een bestaand interactief communicatiemiddel navigeren op AEM, dit selecteren en **[!UICONTROL Edit]** selecteren om de interactieve communicatieontwerpinterface te starten.

   Standaard wordt het afdrukkanaal van de interactieve communicatie weergegeven, tenzij Interactieve communicatie alleen via het web plaatsvindt. In het afdrukkanaal van de interactieve communicatie worden de doelgebieden weergegeven die beschikbaar zijn in de geselecteerde XDP/afdruksjabloon. In deze doelgebieden en -velden kunt u componenten of elementen toevoegen.

1. Selecteer het kanaal Afdrukken en selecteer de tab **[!UICONTROL Components]** . De volgende componenten zijn beschikbaar in het afdrukkanaal:

   | **Component** | **Functionaliteit** |
   |---|---|
   | Diagram | Hiermee voegt u een grafiek toe die u in Interactieve communicatie kunt gebruiken voor de visuele weergave van tweedimensionale gegevens die zijn opgehaald uit een verzameling formuliergegevensmodellen. Voor meer informatie, zie [&#x200B; Gebruikend grafieken in Interactieve Mededelingen &#x200B;](/help/forms/using/chart-component-interactive-communications.md). |
   | Documentfragment | Hiermee kunt u een herbruikbare component, zoals tekst, lijst of voorwaarde, toevoegen aan een interactieve communicatie. De toegevoegde component kan gebaseerd zijn op een formuliergegevensmodel of zonder een formuliergegevensmodel. |
   | Afbeelding | Hiermee kunt u een afbeelding invoegen. |

   De belemmering-en-daling de componenten in uw Interactieve Communicatie en vormt hen zoals vereist.

   U kunt ook de bewerkingen Ongedaan maken en Opnieuw gebruiken tijdens het ontwerpen van een interactieve communicatie voor zowel de afdruk- als de webkanalen.

   Gebruik de bewerking Ongedaan maken om de laatst uitgevoerde actie te verwijderen en de bewerking Opnieuw om de verwijderde actie opnieuw op te nemen. Als u bijvoorbeeld een afbeelding hebt ingevoegd of een gegevensbinding hebt gemaakt in een interactieve communicatie en deze moet verwijderen, gebruikt u de bewerking Ongedaan maken.

   ![&#x200B; maak ongedaan opnieuw acties &#x200B;](assets/undo_redo_actions_new.png)

   De opties voor Ongedaan maken en Opnieuw worden weergegeven op de werkbalk van de pagina UI-ontwerppagina. De optie Ongedaan maken wordt alleen weergegeven nadat een handeling is uitgevoerd. De optie Opnieuw uitvoeren wordt alleen op de paginabalk weergegeven nadat een bewerking Ongedaan maken is uitgevoerd. Deze handelingen worden opnieuw ingesteld bij het vernieuwen van de pagina.

1. Selecteer het afdrukkanaal en ga naar de tab **[!UICONTROL Assets]** en pas het filter toe om alleen de elementen weer te geven die u wilt zien.

   Met de Assets-browser kunt u ook rechtstreeks elementen naar interactieve communicatiedoelgebieden slepen en neerzetten.

   ![&#x200B; activa-docfragments &#x200B;](assets/assets-docfragments.png)

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

U kunt de binding tussen een doelgebied en een documentfragment ook vervangen door het nieuwe fragment op het doelgebied neer te zetten met de tab **[!UICONTROL Assets]** . De blauwe kleurschaduw van het doelgebied tijdens het slepen van het fragment geeft aan dat het documentfragment naar het doelgebied kan worden neergezet.

Voor meer informatie over documentfragmenten, zie {de Fragmenten van het 0} Document [&#128279;](/help/forms/using/document-fragments.md).

Met de ontwerpinterface kunt u onderscheid maken tussen de niet-gebonden en gebonden velden en variabelen in een interactieve communicatie. De interface markeert de niet-gebonden velden en variabelen met een oranje rand.

![&#x200B; unbound_fields_variables_highlight_dc &#x200B;](assets/unbound_fields_variables_highlights_dc.jpg)

Wanneer u de muisaanwijzer op deze elementen plaatst, wordt bovendien knopinfo weergegeven met het bericht Veld (niet geconsolideerd) of Variabele (niet geconsolideerd).

Een niet-gebonden variabele die in een documentfragment wordt gebruikt, wordt soms niet weergegeven in de ontwerpinterface. Dit kan gebeuren door een inline tekstregel in een documentfragment of als er een voorwaardelement is. In dergelijke gevallen wordt knopinfo, gemarkeerd in blauw, weergegeven als onderdeel van het documentfragment. In de knopinfo wordt het aantal niet-gebonden variabelen weergegeven dat in een documentfragment wordt gebruikt.

![&#x200B; Niet gebonden veranderlijke &#x200B;](assets/df_unbound_variable_new.png)

Selecteer het documentfragment, selecteer ![&#x200B; configure_icon &#x200B;](assets/configure_icon.png) (vorm), en selecteer dan **[!UICONTROL Properties]** van het hulpstuk van de Interactieve Mededeling. In de sectie **[!UICONTROL Variables and Data Model Objects]** worden de variabelen vermeld, inclusief de verborgen variabelen en de gegevensmodelobjecten die in de documentfragmenten worden gebruikt. Gebruik ![&#x200B; uitgeven &#x200B;](assets/edit.svg) (geef uit) pictogram naast elk voorwerp of variabele van het gegevensmodel uit om de eigenschappen uit te geven.

1. Aan opstellingsband van variabelen, selecteer een variabele en selecteer ![&#x200B; configure_icon &#x200B;](assets/configure_icon.png) (vorm) en dan opstelling de bindende eigenschappen in het paneel van Eigenschappen in sidebar.

   * **niets**: De agent zal de waarde voor de variabele invullen.
   * **Fragment van de Tekst**: Als geselecteerd, kunt u doorbladeren en een fragment van het tekstdocument selecteren de waarvan inhoud op het gebied wordt teruggegeven. Alleen tekstdocumentfragmenten kunnen worden gebonden aan variabelen die geen variabelen bevatten.
   * **ModelVoorwerp van Gegevens**: Selecteer een modelbezit van vormgegevens de waarvan waarde op het gebied wordt bevolkt.
   * **Standaardwaarde:** u kunt een standaardwaarde voor de variabele bepalen gebruikend dit gebied. De waarde wordt getoond wanneer u voorproef de Interactieve Communicatie of in de Agent UI.
   * **Patroon van de Vertoning:** u kunt een vertoningsformaat voor een variabele ook bepalen. Selecteer om het even welke vooraf bepaalde opties van het **Type** drop-down lijst om een vertoningsformaat op een variabele toe te passen. Selecteer **Douane** om een vertoningspatroon te bepalen dat niet beschikbaar in de lijst is. Voor meer informatie, zie [&#x200B; de vertoningspatronen van Gegevens &#x200B;](../../forms/using/create-interactive-communication.md#datadisplaypatterns).

   Navigeer aan [&#x200B; Variabelen en de ModelVoorwerpen van Gegevens &#x200B;](../../forms/using/create-interactive-communication.md#hiddenvariables) aan opstellingsband van verborgen variabelen in het documentfragment.

   U kunt ook gegevensbronelementen of tekstdocumentfragmenten slepen en neerzetten om de binding van variabelen in te stellen.  Om een band met om het even welke gegevensbronelementen tot stand te brengen, selecteer het **Bronnen van Gegevens** lusje en belemmering-en-daling het element aan de veranderlijke naam. Het gegevensbronelement en de variabele moeten van het zelfde type zijn aan opstelling met succes bindt. Als u een gegevensbronelement naar een reeds gebonden variabele sleept, vervangt het nieuwe element vorige om een band met de variabele tot stand te brengen. Op dezelfde manier selecteer het **Assets** lusje en belemmering-en-daling het fragment van het tekstdocument aan veranderlijke naam aan opstelling de band tussen hen. Het tekstdocumentfragment mag geen variabelen bevatten.

1. Als u een tabel wilt toevoegen terwijl het afdrukkanaal is geselecteerd, past u op het tabblad **[!UICONTROL Assets]** het filter toe om alleen de layoutfragmenten weer te geven. Sleep het vereiste lay-outfragment naar de interactieve communicatie en zet het neer. Een lay-outfragment is gebaseerd op een XDP en kan worden gebruikt om grafische lay-outs of statische en dynamische lijsten in Interactieve Communicatie tot stand te brengen die met dynamische gegevens worden bevolkt.

   Voorbeeld: een lay-outtabel waarin de brutopremie, de loyaliteitskorting % en de beschikbaarheid van noodhulp langs de weg voor het oude en het nieuwe beleid worden weergegeven.

   Voor meer informatie over lay-outfragmenten, zie {de Fragmenten van het 0} Document [&#128279;](/help/forms/using/document-fragments.md).

1. Selecteer het afdrukkanaal en pas het filter op het tabblad **[!UICONTROL Assets]** toe op de weergave van afbeeldingen. Sleep de vereiste afbeeldingen naar de interactieve communicatie, bijvoorbeeld voor het bedrijfslogo.

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

1. Schakel over naar **[!UICONTROL Web Channel]** . Het webkanaal wordt weergegeven in de interactieve communicatieeditor. Wanneer u voor het eerst van het kanaal van de Druk aan het kanaal van het Web overschakelt, vindt de automatische synchronisatie plaats. Voor meer informatie, zie [&#x200B; Synchroniserend Webkanaal van het drukkanaal &#x200B;](../../forms/using/create-interactive-communication.md#synchronize).

   Aangezien u in dit voorbeeld Afdrukken als stramien voor het web gebruikt, worden de plaatsaanduidingen, inhoud en gegevensbinding van het kanaal Afdrukken gesynchroniseerd met het webkanaal. U kunt de specifieke inhoud in het webkanaal echter wijzigen en aanpassen. [&#x200B; annuleert overerving &#x200B;](#cancelinheritance) voor de doelgebieden en de variabelen die gebruikend het drukkanaal zijn geproduceerd om inhoud aan te passen.

   ![&#x200B; webchannelassets &#x200B;](assets/webchannelassets.png)

   Selecteer het documentfragment, selecteer ![&#x200B; configure_icon &#x200B;](assets/configure_icon.png) (vorm), en selecteer dan **[!UICONTROL Properties]** van het hulpstuk van de Interactieve Mededeling. In de sectie **[!UICONTROL Variables and Data Model Objects]** worden de variabelen vermeld, inclusief de verborgen variabelen en de gegevensmodelobjecten die in de documentfragmenten worden gebruikt. Gebruik ![&#x200B; uitgeven &#x200B;](assets/edit.svg) (geef uit) pictogram naast elk voorwerp of variabele van het gegevensmodel uit om de eigenschappen uit te geven. Bovendien voor documentfragmenten die [&#x200B; auto-geproduceerd &#x200B;](#synchronize) in het kanaal van het Web gebruikend het kanaal van de Druk zijn geweest, gebruik het ![&#x200B; annuleringsovererving &#x200B;](assets/cancelinheritance.png) (Cancel Overerving) pictogram naast elk voorwerp van het gegevensmodel en variabele aan [&#x200B; annuleert overerving &#x200B;](#cancelinheritance) en hen kunnen uitgeven.

1. Selecteer **[!UICONTROL Components]** als u aanvullende componenten in het webkanaal wilt toevoegen terwijl het webkanaal is geselecteerd. De belemmering-en-dalingscomponenten in het Webkanaal van uw Interactieve Communicatie zoals vereist en ga te werk om hen te vormen.

   | Onderdelen | Functionaliteit |
   |---|---|
   | Diagram | Hiermee voegt u een grafiek toe die u in Interactieve communicatie kunt gebruiken voor de visuele weergave van tweedimensionale gegevens die zijn opgehaald uit een verzameling formuliergegevensmodellen. Voor meer informatie, zie [&#x200B; Gebruikend grafiekcomponent &#x200B;](../../forms/using/chart-component-interactive-communications.md). |
   | Documentfragment | Hiermee kunt u een herbruikbare component, tekst, lijst of voorwaarde toevoegen aan een interactieve communicatie. De herbruikbare component die u toevoegt aan een interactieve communicatie kan gebaseerd zijn op een formuliergegevensmodel of geen formuliergegevensmodel. |
   | Afbeelding | Hiermee kunt u een afbeelding invoegen. |
   | Deelvenster | Laat u a [&#x200B; Comité &#x200B;](../../forms/using/create-interactive-communication.md#add-panel-component-to-the-web-channel) aan de Interactieve Mededeling toevoegen. |
   | Tabel | Hiermee voegt u een tabel toe waarin u gegevens in rijen en kolommen kunt ordenen. |
   | Doelgebied | Hiermee voegt u een doelgebied in een webkanaal in om de webkanaalspecifieke componenten te ordenen. Het doelgebied is een normale container waarmee u webkanaalspecifieke componenten kunt groeperen. |
   | Tekst | Voegt rijke tekst aan het Webkanaal van een Interactieve Mededeling toe. Tekst kan ook formuliergegevensmodelobjecten gebruiken om de inhoud dynamisch te maken. |
   | Knop | Laat u a [&#x200B; Knoop &#x200B;](../../forms/using/create-interactive-communication.md#add-button-component-to-the-web-channel) aan de Interactieve Mededeling toevoegen. Met de component Button kunt u naar andere interactieve communicatie, adaptieve formulieren, andere elementen zoals afbeeldingen of documentfragmenten of een externe URL navigeren. |
   | Scheidingsteken | Hiermee kunt u een horizontale lijn in een interactieve communicatie invoegen. Gebruik deze component om onderscheid te maken tussen secties in een correspondentie. U kunt bijvoorbeeld de sectie Scheidingsteken gebruiken om onderscheid te maken tussen Customer Details en Credit Card Details in een creditcardoverzicht. |

1. Voeg desgewenst elementen in uw webkanaal in.

   U kunt [&#x200B; voorproef uw Interactieve Communicatie &#x200B;](#previewic) om te zien wat de druk en Weboutput van de Interactieve Mededeling als kijkt en blijft het aanbrengen van veranderingen, zoals vereist.

## Voorbeeld van interactieve communicatie {#previewic}

U kunt de **optie van de Voorproef** gebruiken om verschijning van de Interactieve Mededeling te evalueren. Het Webkanaal van Interactieve Communicatie verstrekt ook een optie om ervaring van een Interactieve Mededeling voor diverse apparaten te simuleren. Bijvoorbeeld iPhone, iPad en Desktop. U kunt zowel **Voorproef** als **Emulator** gebruiken ![&#x200B; heerser &#x200B;](assets/ruler.png) opties samen met elkaar om de Weboutput voor apparaten van verschillende het schermgrootte voor te vertonen. De voorbeeldgegevens in de voorbeeldweergave worden gevuld vanuit het opgegeven gegevensmodel voor formulieren.

1. Selecteer het kanaal (afdrukken of web) voor een voorvertoning en selecteer een voorvertoning. De interactieve communicatie wordt weergegeven.

   >[!NOTE]
   >
   >Het voorbeeld wordt gevuld met de voorbeeldgegevens van het opgegeven formuliergegevensmodel. Voor meer informatie bij het voorvertonen van de Interactieve Communicatie met wat andere gegevens of het gebruiken van de prefill dienst, zie [&#x200B; het model van vormgegevens van het Gebruik &#x200B;](/help/forms/using/using-form-data-model.md) en [&#x200B; Werk met het model van vormgegevens &#x200B;](/help/forms/using/work-with-form-data-model.md).

1. Voor het Webkanaal, gebruik ![&#x200B; heerser &#x200B;](assets/ruler.png) om te bekijken hoe de Interactieve Communicatie op diverse apparaten kijkt.

   ![&#x200B; webchannelpreview &#x200B;](assets/webchannelpreview.png)

Verder, kunt u [&#x200B; Interactieve Mededeling voorbereiden en verzenden gebruikend de Agent UI &#x200B;](/help/forms/using/prepare-send-interactive-communication.md).

## Eigenschappen configureren in interactieve communicatie  {#configure-properties-in-interactive-communication}

### Bijlagen en bibliotheektoegang {#attachmentslibrary}

In het kanaal van de Druk, kunt u de gehechtheid en bibliotheektoegang vormen om de Agent toe te staan beheer gehechtheid in de Agent UI voor de Interactieve Mededeling:

1. In het kanaal van de Druk, benadruk de Container van het Document en selecteer **Eigenschappen**.

   ![&#x200B; documentcontainereigenschappen &#x200B;](assets/documentcontainerproperties.png)

   Het deelvenster Eigenschappen wordt weergegeven in het zijpaneel.

   ![&#x200B; eigenschappen gehechtheid &#x200B;](assets/propertiesattachments.png)

1. Vouw **Bijlagen** uit en specificeer de volgende eigenschappen:

   * **[!UICONTROL Allow Library Access]**: Selecteer deze optie om bibliotheektoegang voor de agent in te schakelen in de gebruikersinterface van de agent. Indien toegelaten, kan de Agent dossiers van de bibliotheek toevoegen terwijl het voorbereiden van de Interactieve Communicatie.
   * **[!UICONTROL Allow Re-Ordering Of Attachments]**: Selecteer om de Agent toe te laten om de gehechtheid met de Interactieve Mededeling opnieuw in orde te brengen.
   * **[!UICONTROL Max Number Of Attachments Allowed]**: geef het maximumaantal toegestane bijlagen voor interactieve communicatie op.
   * **[!UICONTROL Files To Be Attached]**: selecteer **[!UICONTROL Add]** en blader naar de bestanden die u wilt bijvoegen en geef de volgende instellingen op:

      * **[!UICONTROL Attach This File To Document By Default]**: U kunt deze optie wijzigen als alleen de bijlage niet verplicht is.
      * **[!UICONTROL Mandatory:]** Agent zal niet de gehechtheid in de Agent UI kunnen verwijderen.

   ![&#x200B; gehechfiles &#x200B;](assets/attachfiles.png)

1. Selecteer **[!UICONTROL Done]** .

### Eigenschappen van XDP/Layout-velden {#xdplayoutfieldproperties}

1. Terwijl het uitgeven van het kanaal van de Druk van een Interactieve Mededeling, houd over een gebied, dat in het het kanaalmalplaatje van de Druk wordt gebouwd, en selecteer ![&#x200B; configure_icon &#x200B;](assets/configure_icon.png) (vorm).

   Het dialoogvenster Eigenschappen wordt weergegeven in het zijpaneel.

   ![&#x200B; data_display_patterns_fields &#x200B;](assets/data_display_patterns_fields.jpg)

1. Geef het volgende op:

   * **[!UICONTROL Name]**: JCR-knooppuntnaam.
   * **[!UICONTROL Title]**: Ga een titel in die aan de Agent in de Agent UI en in de boom van de Container van het Document zichtbaar zal zijn.
   * **[!UICONTROL Binding Type]**: Selecteer een van de volgende bindingstypen voor het veld.

      * Geen: de agent vult de waarde voor het bezit in.
      * Tekstfragment: als deze optie is geselecteerd, kunt u door een tekstdocumentfragment bladeren en dit selecteren waarvan de inhoud in het veld wordt gerenderd. U kunt ook het tekstdocumentfragment naar de veldnaam slepen en neerzetten om de binding tussen de tekstfragmenten in te stellen. Het tekstdocumentfragment mag geen variabelen bevatten.
      * Gegevensmodelobject: selecteer een formuliergegevensmodeleigenschap waarvan de waarde in het veld is ingevuld. Alternatief, selecteer de **Bronnen van Gegevens** tabel en belemmering-en-daling het bezit aan het gebied.

   * **[!UICONTROL Default Values]**: de standaardwaarde zorgt ervoor dat het veld niet leeg is wanneer het opgegeven gegevensmodel of tekstfragment geen waarde bevat. Als het type gegevensbinding geen is, wordt de standaardwaarde in het veld vooraf ingevuld.
   * **[!UICONTROL Display Pattern]**: U kunt ook een weergave-indeling voor een veld definiëren. Selecteer om het even welke vooraf bepaalde opties van het **Type** drop-down lijst om een vertoningsformaat op een gebied toe te passen. Selecteer **Douane** om een vertoningspatroon te bepalen dat niet beschikbaar in de lijst is. Voor meer informatie, zie [&#x200B; de vertoningspatronen van Gegevens &#x200B;](../../forms/using/create-interactive-communication.md#datadisplaypatterns)

   * **[!UICONTROL Editable By Agent]**: Uitgezocht om de agent toe te staan om de waarde op het gebied in de Agent UI uit te geven. Deze instelling is niet van toepassing als Type binding tekstfragment is.
   * **[!UICONTROL Label]**: specificeer een tekstkoord dat met het gebied aan de Agent in Agent UI wordt getoond. Deze instelling is niet van toepassing als Type binding tekstfragment is.
   * **[!UICONTROL Tooltip]**: Ga een tekstkoord in dat bij muis over aan de Agent in Agent UI zichtbaar zal zijn. Deze instelling is niet van toepassing als Type binding tekstfragment is.
   * **[!UICONTROL Required]**: selecteer deze optie om het veld verplicht te maken voor de Agent. Deze instelling is niet van toepassing als Type binding tekstfragment is.
   * **[!UICONTROL Allow multiple lines]**: Selecteer dit veld als u meerdere tekstregels als invoer in het veld wilt toestaan. Deze instelling is niet van toepassing als Type binding tekstfragment is.

1. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png).

### Weergavepatronen voor gegevens {#datadisplaypatterns}

Met de ontwerpinterface kunt u gegevenspatronen definiëren voor velden, variabelen en formuliergegevensmodelelementen die beschikbaar zijn tijdens het maken van een interactieve communicatie voor afdruk- en webkanalen.

Om het patroon van de gegevensvertoning te vormen, selecteer het element, selecteer ![&#x200B; configure_icon &#x200B;](assets/configure_icon.png) (vorm) en opstelling het vertoningspatroon in het **[!UICONTROL Properties]** paneel in sidebar. Selecteer een vooraf gedefinieerde optie in de vervolgkeuzelijst **[!UICONTROL Type]** om het patroon weer te geven dat aan het geselecteerde type is gekoppeld. Selecteer **[!UICONTROL Custom]** in de vervolgkeuzelijst **[!UICONTROL Type]** om een patroon te definiëren dat niet beschikbaar is in de lijst. Als u waarden in het veld **[!UICONTROL Pattern]** bewerkt, wordt de tekst automatisch gewijzigd in **[!UICONTROL Custom]** .

Als u het weergavepatroon wilt toepassen, moet het aantal tekens of cijfers dat in het veld Patroon is gedefinieerd, overeenkomen met of groter zijn dan de tekens of cijfers die in de waarde voor velden, variabelen en formuliergegevensmodelelementen zijn gedefinieerd. Voor meer informatie, zie [&#x200B; voorbeeld &#x200B;](../../forms/using/create-interactive-communication.md#greaternumberofdigits).

![&#x200B; data_display_pattern_example &#x200B;](assets/data_display_patterns_ssn_new.png)

Nadat u webinhoud hebt gegenereerd vanuit het afdrukkanaal, kunt u het weergavepatroon voor een veld, variabele of formuliergegevensmodelelement opnieuw definiëren. Dientengevolge, kan een element verschillende vertoningspatronen hebben die voor druk en Webkanalen worden bepaald. Als u geen weergavepatroon definieert voor een element in een afdrukkanaal en webinhoud automatisch genereert met behulp van een afdrukkanaal, definieert de gegevensbinding die voor het element in het afdrukkanaal is gedefinieerd, de weergavepatroon-opties die beschikbaar zijn in de vervolgkeuzelijst **[!UICONTROL Type]** . Als er geen binding is gedefinieerd voor het element, definieert het gegevenstype van het element de beschikbare opties voor weergavepatronen. Als u bijvoorbeeld een gegevensbinding van het type Number maakt voor een element in een afdrukkanaal, zijn de opties voor weergavepatronen in de vervolgkeuzelijst **[!UICONTROL Type]** van het type Number in verschillende indelingen.

Schakelaar aan de **wijze van de Voorproef** of open Agent UI om het vertoningspatroon te bekijken dat op deze elementen wordt toegepast.

In de volgende tabel ziet u een voorbeeld van de waarden die worden weergegeven als gevolg van het instellen van het weergavepatroon voor gegevens van een variabele:

| Type | Standaardwaarde | Weergavepatroon | Weergavewaarde | Beschrijving |
|---|---|---|---|---|
| SocialSecurityNumber | 123456789 | text{999-99-9999} | 123-45-6789 | Het aantal cijfers in het veld Standaardwaarde komt overeen met het aantal cijfers in het veld Patroon. De waarde op basis van het patroon wordt weergegeven. |
| SocialSecurityNumber | 1234567 | text{999-99-9999} | 23-4567 | Het aantal cijfers in het veld Standaardwaarde is kleiner dan het aantal cijfers in het veld Patroon. Het patroon wordt toegepast op de 7 beschikbare cijfers. |
| SocialSecurityNumber | 1234567890 | text{999-99-9999} | 1234567890 | Het aantal cijfers in het veld Standaardwaarde is groter dan het aantal cijfers in het veld Patroon. Het resultaat is dat de weergavewaarde niet wordt gewijzigd. |

Als een vertoningspatroon niet voor een variabele of een modelelement van vormgegevens wordt gespecificeerd, wordt de [&#x200B; globale configuratie van het documentfragment &#x200B;](https://helpx.adobe.com/nl//experience-manager/6-5/forms/using/interactive-communication-configuration-properties.html) gebruikt door gebrek.

Als u geen weergavepatroon toepast op een variabele van het gegevenstype Number, wordt in de afdrukvoorbeeld het patroon weergegeven op basis van de algemene configuratie van het documentfragment. Als u veranderingen op de standaard globale configuratie van het documentfragment toepast, toont de UI van de Agent nog het patroon volgens de standaardseparators die voor de scène worden bepaald.

Als er voor velden geen weergavepatroon is opgegeven, wordt het patroon dat tijdens het maken van de afdruksjabloon (XDP) is gedefinieerd, op dezelfde manier op het veld toegepast. Als er geen patroon is tijdens het maken van de afdruksjabloon, worden de standaardpatronen op basis van XFA-specificaties toegepast op de velden.

Als het opgegeven weergavepatroon onjuist is of niet kan worden toegepast, worden de standaardpatronen op basis van XFA-specificaties toegepast op de velden, variabelen of elementen van het formuliergegevensmodel.

## Pas regels op Interactieve Communicatie componenten toe {#rules}

Om componenten of inhoud in de interactieve mededeling te conditionaliseren, selecteer de component/het stuk van inhoud en selecteer ![&#x200B; createruleicon &#x200B;](assets/createruleicon.png) (creeer Regel) om de Redacteur van de Regel te lanceren.

Zie voor meer informatie:

* [Regeleditor](/help/forms/using/rule-editor.md)
* [Inleiding tot interactieve communicatie authoring](/help/forms/using/introduction-interactive-communication-authoring.md)

## Werken met tabellen {#tables}

### Dynamische tabellen in interactieve communicatie {#dynamic-tables-in-interactive-communication}

U kunt dynamische tabellen toevoegen in Interactieve communicatie met behulp van lay-outfragmenten. De volgende stappen gebruiken een voorbeeld van een creditcardverklaring om het gebruik van een lay-outfragment voor het creëren van een dynamische lijst in een Interactieve Mededeling te illustreren.

1. Zorg ervoor dat het vereiste layoutfragment voor het maken van de tabel in AEM beschikbaar is.
1. Sleep in het afdrukkanaal van uw interactieve communicatie een lay-outfragment (met een tabel met meerdere kolommen) in een doelgebied vanuit de browser Asset.

   ![&#x200B; lf_dragdrop &#x200B;](assets/lf_dragdrop.png)

   Een tabel wordt weergegeven in het lay-outgebied Interactieve communicatie.

   ![&#x200B; lf_dragdrop_table &#x200B;](assets/lf_dragdrop_table.png)

1. Geef de gegevensbinding op voor elk van de cellen in de tabel. Als u een herhaalbare rij wilt maken, voegt u eigenschappen van het formuliergegevensmodel in de rij in die bij een algemene eigenschap voor de verzameling horen.

   1. Selecteer een cel in de lijst en selecteer ![&#x200B; configure_icon &#x200B;](assets/configure_icon.png) (vorm).

      Het dialoogvenster Eigenschappen wordt weergegeven in het zijpaneel.

      ![&#x200B; lf_cell_properties &#x200B;](assets/lf_cell_properties.png)

   1. Configureer de eigenschappen:

      * **[!UICONTROL Name]**: JCR-knooppuntnaam.
      * **[!UICONTROL Title]**: ga een titel in die in de Interactieve Communicatie redacteur zichtbaar zal zijn.
      * **[!UICONTROL Binding Type]**: Selecteer een van de volgende bindingstypen voor het veld.

         * **[!UICONTROL None]**
         * **[!UICONTROL Data model object]**: de waarde van de eigenschap van een formuliergegevensmodel wordt in het veld ingevuld. Alternatief, selecteer de **Bronnen van Gegevens** tabel en belemmering-en-daling het bezit aan het gebied.

      * **[!UICONTROL Data Model Object]**: De eigenschap van het gegevensmodel van het formulier waarvan de waarde in het veld wordt ingevuld.
      * **[!UICONTROL Default Value]**: de standaardwaarde zorgt ervoor dat het veld niet leeg is wanneer het opgegeven gegevensmodelobject geen waarde bevat. De standaardwaarde is vooraf ingevuld in het veld.

      * **[!UICONTROL Editable By Agent]**: Uitgezocht om de agent toe te staan om de waarde op het gebied in de Agent UI uit te geven.

   1. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png).

1. Bekijk een voorvertoning van de interactieve communicatie om te zien welke tabel met de gegevens wordt weergegeven.

   ![&#x200B; lf_preview &#x200B;](assets/lf_preview.png)

### Alleen webkanalen {#webchanneltables}

Selecteer het wortelpaneel in het malplaatje van het Web en selecteer **+** om de component van de a **Lijst** aan de Interactieve Mededeling toe te voegen. In de interactieve communicatie wordt een tabel met twee rijen ingevoegd. De eerste rij van de tabel staat voor de tabelkop.

#### Rijen en kolommen toevoegen aan de tabel {#addrowscolumnstable}

**om kolommen toe te voegen of te schrappen:**

1. Selecteer het standaardtekstvak in de tabelkoprij om de componentwerkbalk weer te geven.
1. Selecteer **toevoegen Kolom** of **Schrap Kolom** om lijstkolommen respectievelijk toe te voegen of te schrappen.

![&#x200B; component_toolbar_table1 &#x200B;](assets/component_toolbar_table1.png)

**om rijen toe te voegen of te schrappen:**

1. Selecteer een tabelrij om de werkbalk van de component weer te geven. U kunt ook tabelrij selecteren met de Inhoudsbrowser in de assistent van de Interactieve communicatie.
1. Selecteer **Rij** toevoegen of **Rij** schrappen om lijstrijen respectievelijk toe te voegen of te schrappen. Gebruik de **Beweging omhoog** en **Beweging neer** opties beschikbaar in de toolbar om rijen in de lijst opnieuw te rangschikken.

![&#x200B; Toolbar van de Component &#x200B;](assets/component_toolbar_table_row_new.png)

**A.** voeg rij **B toe.** Schrap rij **C.** Beweging omhoog **D.** Beweging onderaan

#### Tekst toevoegen of bewerken in tabelcellen {#addedittexttable}

1. Selecteer het standaardtekstvakje in de lijstcel en selecteer ![&#x200B; uitgeven &#x200B;](assets/edit.png) (geef uit).
1. Typ de tekst in de lijstcel en selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png) om het te bewaren.

#### Binding maken tussen tabelcellen en objectelementen van gegevensmodellen {#createbindingtablecells}

1. Selecteer het standaardtekstvakje in de lijstrij en selecteer ![&#x200B; uitgeven &#x200B;](assets/edit.png) (geef uit).
1. Selecteer de vervolgkeuzelijst Gegevensmodelobjecten en selecteer de eigenschap.
1. Selecteer deze optie om een binding tussen de tabelcel en de objecteigenschap van het gegevensmodel op te slaan en te maken.

![&#x200B; creeer gegevensband &#x200B;](assets/create_data_binding_table_new.png)

#### Een hyperlink maken voor tekst in de tabelcel {#createhyperlinktable}

1. Selecteer het standaardtekstvakje in de lijstcel en selecteer ![&#x200B; uitgeven &#x200B;](assets/edit.svg) (geef uit).
1. Selecteer de tekst in de tabelcel en selecteer het pictogram Hyperlink.
1. Specificeer URL op het **gebied van de Weg**.
1. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png) om de hyperlinkeigenschappen te bewaren.

![&#x200B; creeer hyperlink &#x200B;](assets/create_hyperlink_table_new.png)

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

1. Selecteer de lijst en selecteer ![&#x200B; configure_icon &#x200B;](assets/configure_icon.png) (vorm). U kunt de lijst ook selecteren gebruikend **inhoud** browser in het hulpje van de Interactieve Mededeling.
1. Selecteer **het Sorteren toelaten.**
1. Selecteer ![&#x200B; done_icon &#x200B;](assets/done_icon.png) om de lijsteigenschappen te bewaren. De sorteerpictogrammen, pijlen omhoog en omlaag, in kolomkoppen geven aan dat het sorteren is ingeschakeld.

   ![&#x200B; laat het sorteren &#x200B;](assets/enable_sorting_new-1.png) toe

1. Schakelaar aan de **wijze van de Voorproef** om de output te bekijken. De tabel wordt automatisch gesorteerd op basis van de eerste kolom van de tabel.
1. Klik op de kolomkop om de waarden te sorteren op basis van de kolom.

   Een kolomkop met een pijl-omhoog geeft aan dat de instelling:

   * tabel wordt gesorteerd op basis van die kolom.
   * De waarden in de kolom worden in oplopende volgorde weergegeven.

   ![&#x200B; het Sorteren het stijgen &#x200B;](assets/sorting_ascending_new-1.png)

   Op dezelfde manier vertegenwoordigt een kolomkopbal met een benedenpijl dat de waarden in de kolom in dalende orde worden getoond.

## Interactieve communicatie-eigenschappen bewerken {#edit-interactive-communication-properties}

Zodra u een Interactieve Communicatie creeert, kunt u zijn eigenschappen in een recentere fase uitgeven.

Gebruik de **pagina van Eigenschappen** aan:

* Bewerk waarden voor de opgegeven velden tijdens het maken van de interactieve communicatie, zoals Titel en Beschrijving.
* Voeg of schrap het kanaal van het Web voor bestaande Interactieve Mededeling toe.
* Interactieve communicatie voorvertonen, downloaden of verwijderen
* Open de [&#x200B; Agent UI &#x200B;](/help/forms/using/prepare-send-interactive-communication.md).

Om tot de **pagina van Eigenschappen** toegang te hebben:

1. Login aan de AEM auteursinstantie en navigeer aan **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten**.
1. Selecteer de Interactieve Communicatie en selecteer **Eigenschappen**.
1. Selecteer het **Algemene** lusje om de **Titel** uit te geven en **Beschrijving** gebieden.

### Het webkanaal toevoegen of verwijderen {#add-or-delete-the-web-channel}

Voer de volgende stappen uit om het kanaal van het Web voor een bestaande Interactieve Mededeling toe te voegen:

1. Voor de **pagina van Eigenschappen**, selecteer de **Kanalen** tabel.
1. Selecteer **Web** checkbox en selecteer een malplaatje voor het kanaal van het Web.
1. Selecteer **Druk van het Gebruik als Meester voor het Kanaal van het Web** om synchronisatie tussen het kanaal van het Web en het kanaal van de Druk toe te laten.
1. Selecteer **sparen &amp; Sluiten** om de veranderingen te bewaren.

   Op dezelfde manier kunt u **Web** checkbox op het **lusje van Kanalen** selecteren om het kanaal van het Web van de Interactieve Mededeling te schrappen.

## De component Button toevoegen aan het webkanaal {#add-button-component-to-the-web-channel}

U kunt knoop als component aan het Webkanaal van de Interactieve Communicatie toevoegen. Bepaal regels gebruikend de [&#x200B; regelredacteur &#x200B;](../../forms/using/rule-editor.md) om aan andere Interactieve Mededelingen, adaptieve vormen, andere activa zoals beelden of documentfragmenten, of externe URL op de uitgezochte knoop te kunnen navigeren.

Om knoop toe te voegen en regels te bepalen over het:

1. Selecteer het wortelpaneel in het malplaatje van het Web en selecteer **+** om de **component van de Knoop** aan de Interactieve Mededeling toe te voegen.
1. Selecteer de knoopcomponent en selecteer ![&#x200B; geef-regels &#x200B;](assets/edit-rules.png) uit om regels op te bepalen uitgezocht van de knoop.
1. In **wanneer** sectie, uitgezocht **klikte** van de staat van de knoop drop-down lijst.
1. In **toen** sectie:

   1. Selecteer een actie in de vervolgkeuzelijst. Bijvoorbeeld, uitgezochte **navigeer aan** als actietype.

   1. Geef de URL van de interactieve communicatie, het adaptieve formulier, een element of een webpagina op. Geef bijvoorbeeld de URL op in de volgende indeling om naar een andere interactieve communicatie te navigeren: https://&lt;server-name>:&lt;port>/editor.html/content/forms/af/&lt;Interactive Communication name>/kanalen/&lt;channel name - print or web>.html
   1. Geef de optie op om het element op hetzelfde tabblad, op een nieuw tabblad of in een nieuw venster te openen.
   1. Selecteer **Gedaan** en selecteer dan **Sluiten** om de regel te bewaren.

   Op dezelfde manier kunt u andere beschikbare opties selecteren in de vervolgkeuzelijst Type actie, zoals Invoke Service en Formulier verzenden. Voor meer informatie, zie [&#x200B; regelredacteur &#x200B;](../../forms/using/rule-editor.md).

1. Geef een voorvertoning van de interactieve communicatie weer en selecteer de knop om de interactieve communicatie, het adaptieve formulier, een element of een webpagina weer te geven die is opgegeven in stap 4 b).

## Deelvenstercomponent toevoegen aan het webkanaal {#add-panel-component-to-the-web-channel}

De component van het Comité is placeholder voor het groeperen van andere componenten samen en controleert hoe een groep componenten, zoals accordeon en lusjes, in de Interactieve Mededeling worden uiteengezet. Met een deelvenstercomponent kunt u ook een groep componenten herhaalbaar maken voor de eindgebruiker, bijvoorbeeld in meerdere items die nodig zijn om de gegevens van het onderwijs in te vullen.

Voer de volgende stappen uit om een component van het Comité aan het Webkanaal toe te voegen:

1. Tussenvoegsel de **component van het Comité** in het Webkanaal gebruikend om het even welke volgende opties:

   * Selecteer een component, selecteer **+** en selecteer de **3&rbrace; component van het Comité &lbrace;.**

   * Van het **paneel van de Component** browser, belemmering-daling de **3&rbrace; component van het Comité &lbrace;op de Interactieve Mededeling.**

   * Selecteer het **Comité** in het **3&rbrace; browser paneel van de Inhoud &lbrace;en uitgezocht** voeg het Comité van het Kind **toe.** Het selecteren van **voegt het Comité van het Kind** optie toe toont **voeg de dialoogdoos van het Comité van het Kind** toe. Voer de titel en een optionele beschrijving en naam voor de component Panel in.

1. Selecteer het paneel van de **browser van de Inhoud** om extra acties op het Comité uit te voeren zoals vorm, geef regels uit, exemplaar, schrap, en neem component op.

   U kunt ook slepen-en-dalings een paneel binnen **Inhoud** browser om op de verandering in de structuur van de Interactieve Mededeling in de juiste ruit te wijzen.

## Webkanaal synchroniseren met afdrukkanaal {#synchronize}

Wanneer u Afdrukken als stramien voor webkanaal selecteert tijdens het maken van een interactieve communicatie, wordt het webkanaal in synchronisatie met het kanaal Afdrukken gemaakt en worden de inhoud en de gegevensbinding van het webkanaal afgeleid van het afdrukkanaal en kunnen de wijzigingen die in het afdrukkanaal zijn aangebracht, worden doorgevoerd in het webkanaal wanneer u Synchroniseren selecteert.

De auteurs mogen echter desgewenst de overerving voor componenten in het webkanaal verbreken.

![&#x200B; creeer de Meester van de Druk &#x200B;](assets/create_ic_print_master_new-1.png) ![&#x200B; HoofdWeb van de Druk &#x200B;](assets/create_ic_print_master_web_new-1.png)

### Automatisch synchroniseren {#autosync}

Als u de optie **[!UICONTROL Use Print As Master for Web Channel]** selecteert, kunt u een van de volgende modi selecteren om een webkanaal te genereren:

* **[!UICONTROL Auto layout]**: selecteer deze modus om automatisch plaatsaanduidingen, inhoud en gegevensbinding voor het webkanaal te genereren via het kanaal Afdrukken.
* **[!UICONTROL Manually organize]**: selecteer deze modus om handmatig kanaalelementen afdrukken naar het webkanaal te selecteren en toe te voegen met behulp van de basisinhoud die beschikbaar is op het tabblad Gegevensbronnen. Voor meer informatie, zie [&#x200B; Uitgezochte het kanaalelementen van de Druk om het kanaalinhoud van het Web &#x200B;](#selectprintchannelelements) tot stand te brengen.

![&#x200B; creeer IC opties &#x200B;](assets/create_ic_options_updated_new.png)

>[!NOTE]
>
>Als u de kanalen synchroniseert, worden alleen de documentfragmenten, afbeeldingen, voorwaarden, lijsten en layoutfragmenten gesynchroniseerd van het afdrukkanaal naar het webkanaal. De subformulieren of bovenliggende knooppunten die dergelijke elementen bevatten, worden niet gesynchroniseerd.

### Selecteer de kanaalelementen van de Druk om de inhoud van het Webkanaal te creëren {#selectprintchannelelements}

Als u Afdrukken als stramien selecteert tijdens het maken van de interactieve communicatie en de optie voor automatische synchronisatie niet selecteert, kunt u ook de kanaalelementen van de Afdruk naar de ontwerpinterface van het webkanaal slepen en neerzetten.

Navigeer aan **Gegevensbronnen** > **Hoofdinhoud** om de het kanaalelementen van de Druk te bekijken. Sleep de doelgebieden, velden of tabellen naar de ontwerpinterface van het webkanaal en zet deze neer. Een blauw cirkelpictogram naast de elementnaam geeft aan dat het afdrukkanaalelement al in het webkanaal is opgenomen.

![&#x200B; Hoofdinhoud &#x200B;](assets/master_content.png)

### Overerving annuleren {#cancelinheritance}

In het webkanaal worden de componenten ingesloten in de doelgebieden.

Beweeg over het relevante doelgebied of de variabele in het Webkanaal en selecteer ![&#x200B; annuleringsovererving &#x200B;](assets/cancelinheritance.png) (Cancel Overerving) en dan in de Cancel dialoog van de Overerving, uitgezochte **[!UICONTROL Yes]**.

De overerving van de componenten binnen het doelgebied wordt geannuleerd en u kunt ze nu naar wens bewerken.

### Overerving opnieuw inschakelen {#re-enable-inheritance}

In het kanaal van het Web, als u overerving van een component hebt geannuleerd, kunt u het re-toelaten. Om overerving re-toe te laten, houd over de grens van het relevante doelgebied, dat de component omvat, en selecteer ![&#x200B; reenableinheritance &#x200B;](assets/reenableinheritance.png) opnieuw in.

Het dialoogvenster Overerving herstellen wordt weergegeven.

![&#x200B; revertovererving &#x200B;](assets/revertinheritance.png)

Selecteer indien nodig **[!UICONTROL Synchronize The Page After Reverting Inheritance]** . Selecteer deze optie om de volledige interactieve communicatie te synchroniseren. Als u deze optie niet selecteert, wordt alleen het desbetreffende doelgebied gesynchroniseerd bij het opnieuw instellen van de overerving.

Selecteer **[!UICONTROL Yes]** .

### Synchroniseren {#synchronize-1}

Als u Afdrukken als stramien voor webkanaal gebruikt en het kanaal Afdrukken wijzigt, kunt u de inhoud synchroniseren om de zojuist aangebrachte wijzigingen door te voeren in het webkanaal.

1. Als u het webkanaal wilt synchroniseren met het kanaal Afdrukken, schakelt u over naar het kanaal Web en selecteert u het pictogram Meer opties.

   ![&#x200B; Auto synchronisatieopties &#x200B;](assets/auto_sync_options_new.png)

1. Selecteer een van de volgende opties:

   * **[!UICONTROL Sync with Print]**: hiermee wordt alleen de inhoud gesynchroniseerd voor de doelgebieden waarin overerving niet is geannuleerd.
   * **[!UICONTROL Reset]**: synchroniseert de webkanaalinhoud met het kanaal Afdrukken en verwijdert alle wijzigingen die in het webkanaal zijn aangebracht.

### De componententoolbar van het gebruik om acties op geërfte componenten uit te voeren {#componenttoolbar}

Als u automatisch gegenereerde inhoud in het webkanaal hebt met de optie Synchroniseren, kunt u meer acties op componenten uitvoeren zonder dat de overerving wordt geannuleerd.

![&#x200B; Toolbar van de Component &#x200B;](assets/component_toolbar_inherited_web_new.png)

Selecteer de component om de volgende opties weer te geven:

* **Exemplaar:** kopieer een component en kleef het in andere plaatsen in de Interactieve Mededeling.
* **Besnoeiing:** beweeg een component van één plaats aan een andere in de Interactieve Communicatie.
* **Component van het Tussenvoegsel:** neem een component boven de geselecteerde component op.
* **Deeg:** plak de component u knipt of gebruikend de hierboven beschreven opties kopieerde.
* **Groep:** selecteer veelvoudige componenten als u, meer dan één component samen knippen, kopiëren of wilt kleven.
* **Ouder:** selecteer de ouder van een component.
* **Uitdrukking SOM van de Mening:** Bekijk de [&#x200B; uitdrukking SOM &#x200B;](../../forms/using/using-som-expressions-adaptive-forms.md) voor de component.

* **de Voorwerpen van de Groep in Comité:** groepeer de componenten in een paneel om verrichtingen op die componenten gelijktijdig kunnen uitvoeren. Voor details, zie [&#x200B; voorwerpen van de Groep in Comité &#x200B;](#groupobjectspanel).

* **annuleert Overerving:** [&#x200B; annuleert de overerving &#x200B;](#cancelinheritance) van de componenten binnen het doelgebied om hen uit te geven.

### Objecten groeperen in deelvenster {#groupobjectspanel}

Met de ontwerpinterface voor webkanalen kunt u de componenten groeperen in een deelvenster en vervolgens tegelijkertijd bewerkingen op die componenten uitvoeren. Het **lusje van de Inhoud** maakt een lijst van de gegroepeerde componenten als kindelementen van het paneel in de inhoudsboom.

1. Selecteer een component en selecteer de groep ( ![&#x200B; groep &#x200B;](assets/group.jpg)) verrichting.
1. Selecteer veelvoudige componenten en selecteer **voorwerpen van de Groep in Comité**.

   ![&#x200B; de Objecten van de Groep &#x200B;](assets/component_toolbar_group_objects_new.png)

1. In de **Voorwerpen van de Groep in Comité** dialoogdoos, ga een naam voor het Comité in.
1. Voer een optionele titel en beschrijving in voor het deelvenster.
1. Klik ![&#x200B; bullet_checkmark &#x200B;](assets/bullet_checkmark.png).

   De gegroepeerde componenten worden als onderliggende elementen van het deelvenster weergegeven in de inhoudsstructuur.

   ![&#x200B; content_tree_grouping &#x200B;](assets/content_tree_grouping.png)

## Uitvoerindeling voor afdrukkanaal {#output-format-print-channel}

Gebruik PrintChannel API om uitvoerindeling te definiëren voor het afdrukkanaal van een interactieve communicatie. Als u geen uitvoerindeling definieert, genereert AEM Forms de uitvoer in PDF-indeling.

```javascript
//options for rendering print channel of a multi-channel document
PrintChannelRenderOptions renderOptions = new PrintChannelRenderOptions();
PrintDocument printDocument = printChannel.render(renderOptions);
```

Als u de uitvoer in een andere indeling wilt genereren, geeft u het type uitvoerindeling op. Verwijs naar [&#x200B; PrintChannel API &#x200B;](https://helpx.adobe.com/nl/experience-manager/6-5/forms/javadocs/com/adobe/fd/output/api/PrintConfig.html) voor de lijst van gesteunde types van outputformaat.

U kunt bijvoorbeeld het volgende voorbeeld gebruiken om PCL als uitvoerindeling voor een interactieve communicatie te definiëren:

```javascript
//options for rendering print channel of a multi-channel document
PrintChannelRenderOptions renderOptions = new PrintChannelRenderOptions();
renderOptions.setRenderFormat(PrintConfig.HP_PCL_5e);
PrintDocument printDocument = printChannel.render(renderOptions);
```
