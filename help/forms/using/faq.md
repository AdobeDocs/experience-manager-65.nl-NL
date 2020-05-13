---
title: Veelgestelde vragen (FAQ) voor HTML5-formulieren
seo-title: Veelgestelde vragen (FAQ) voor HTML5-formulieren
description: Veelgestelde vragen (FAQ) over indeling, ondersteuning van scripts en het bereik van HTML5-formulieren.
seo-description: Veelgestelde vragen (FAQ) over indeling, ondersteuning van scripts en het bereik van HTML5-formulieren.
uuid: 398e31de-3e46-4288-b3cd-39d51fa17abc
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 4b676e7e-191f-4a19-8b8f-fc3e30244b59
docset: aem65
translation-type: tm+mt
source-git-commit: 407b4d0b86c6bcbff11a085ea10bd3bf90115257
workflow-type: tm+mt
source-wordcount: '1970'
ht-degree: 0%

---


# Veelgestelde vragen (FAQ) voor HTML5-formulieren{#frequently-asked-questions-faq-for-html-forms}

Er zijn een aantal veelgestelde vragen (FAQ) over indeling, ondersteuning van scripts en het bereik van HTML5-formulieren.

## Indeling {#layout}

1. Waarom worden streepjescodes en handtekeningvelden niet in mijn formulier weergegeven?

   Antwoord: Streepjescodes en handtekeningvelden zijn niet relevant in HTML- of mobiele scenario&#39;s. Deze velden worden weergegeven als een niet-interactief gebied. AEM Forms Designer biedt echter een nieuw veld voor het schrijven van handtekeningen dat u kunt gebruiken in plaats van een handtekeningveld. U kunt ook een [aangepaste widget](../../forms/using/custom-widgets.md) voor streepjescodes toevoegen en integreren.

1. Wordt RTF-tekst ondersteund voor het XFA-tekstveld?

   Antwoord: Het XFA-veld, dat rijke inhoud in AEM Forms Designer toestaat, wordt niet ondersteund en wordt weergegeven als normale tekst zonder ondersteuning voor het opmaken van tekst vanuit de gebruikersinterface. Daarnaast worden XFA-velden met de eigenschap combinatie weergegeven als een normaal veld, hoewel er nog steeds beperkingen zijn voor het aantal toegestane tekens op basis van de waarde van combinatie-cijfers.

1. Zijn er beperkingen met betrekking tot het gebruik van herhaalbare subformulieren?

   Antwoord: Herhalbare subformulieren moeten een beginaantal van 1 of meer hebben. Herhalbare subformulieren met een beginaantal van nul worden niet ondersteund. U kunt er ook voor kiezen een herhaalbaar subformulier te gebruiken en het niet weer te geven wanneer het formulier wordt geladen. Om het gebruiksgeval te bereiken:

   1. Stel het aanvankelijke aantal van het herhaalbare subformulier in op 1.

      ![eerste telling](assets/intial-count.png)

   1. Gebruik de initialisatiegebeurtenis van het formulier om het primaire exemplaar van het subformulier te verbergen. De onderstaande code verbergt bijvoorbeeld het primaire exemplaar van Subform bij initialisatie van het formulier. Het verifieert ook het app type om ervoor te zorgen dat het manuscript slechts op de cliëntkant wordt uitgevoerd:

      ```
      if ((xfa.host.appType == "HTML 5" || xfa.host.appType == "Exchange-Pro" || xfa.host.appType == "Reader")&&(_RepeatSubform.count == 1)&&(form1.Page1.Subform1.RepeatSubform.Key.rawValue == null)) {
      RepeatSubform.presence = "hidden";
      }
      ```

   1. Open het script om een exemplaar van het subformulier toe te voegen voor bewerking. Voeg de code zoals hieronder toe om een exemplaar van het Subform manuscript toe te voegen.

      De onderstaande code controleert het verborgen exemplaar van het subformulier. Als het verborgen exemplaar van het subformulier wordt gevonden, verwijdert u het verborgen exemplaar van het subformulier en voegt u een nieuw exemplaar van het subformulier in. Als het verborgen exemplaar van het subformulier niet wordt gevonden, voegt u gewoon een nieuw exemplaar van het subformulier in.

      ```
      if (RepeatSubform.presence == "hidden")
      {
      RepeatSubform.instanceManager.insertInstance(0);
      RepeatSubform.instanceManager.removeInstance(1);
      }
      else
      {
      RepeatSubform.instanceManager.addInstance(1);
      }
      ```

   1. Open het script om een exemplaar van het subformulier te verwijderen en te bewerken. Voeg de volgende code toe om een exemplaar van het Subform-script te verwijderen.

      De code controleert het aantal subformulieren. Als het aantal subformulieren 1 is, wordt het subformulier door de code verborgen in plaats van het subformulier te verwijderen.

      ```
      if (RepeatSubform.instanceManager.count == 1) {
      RepeatSubform.presence = "hidden";
      } else {
      RepeatSubform.instanceManager.removeInstance(RepeatSubform.instanceManager.count - 1);
      }
      ```

   1. Open de gebeurtenis presubmit van het formulier voor bewerking. Voeg het volgende script toe aan de gebeurtenis om het verborgen exemplaar van het script te verwijderen voordat u het bewerkt. Hiermee voorkomt u dat gegevens van het verborgen subformulier bij verzending worden verzonden.

      ```
      if(RepeatSubform.instanceManager.count == 1 && RepeatSubform.presence == "hidden") {
      RepeatSubform.instanceManager.removeInstance(0);
      }
      ```

1. Zijn er beperkingen met betrekking tot het gebruik van verborgen subformulieren?

   Antwoord: Een verborgen subformulier met een complexe hiërarchie die over pagina&#39;s wordt gesplitst, veroorzaakt problemen met de indeling. Als tussenoplossing kunt u het subformulier in eerste instantie zichtbaar markeren en het vervolgens verbergen in een initialisatiescript op basis van logica of gegevens.

1. Waarom sommige tekst wordt afgekapt of onjuist wordt weergegeven in HTML5?

   Antwoord: Wanneer een tekstelement Tekenen of Bijschrift niet voldoende ruimte heeft om inhoud weer te geven, wordt de tekst afgebroken weergegeven in mobiele formulieruitvoering. Deze afkapping is ook zichtbaar in de ontwerpweergave van AEM Forms Designer. Hoewel deze afkapping kan worden verwerkt in de PDF&#39;s, kan deze niet worden verwerkt in de HTML5-formulieren. U voorkomt dit probleem door voldoende ruimte te bieden om tekst te tekenen of te ondertitelen zodat de tekst niet wordt afgekapt in de ontwerpmodus van de AEM Forms Designer.

1. Ik observeer layoutproblemen met betrekking tot ontbrekende inhoud of overlappende inhoud. Wat is de reden?

   Antwoord: Als er naast een ander overlappend element op dezelfde positie een element Tekst tekenen of Afbeelding tekenen is (bijvoorbeeld een rechthoek), is de inhoud Tekst tekenen niet zichtbaar als deze later in de documentvolgorde komt (in de Hiërarchieweergave van AEM Forms Designer). PDF ondersteunt transparante lagen, maar HTML/browsers bieden geen ondersteuning voor transparante lagen.

1. Waarom worden sommige lettertypen in het HTML-formulier anders weergegeven dan de lettertypen die bij het ontwerpen van het formulier worden gebruikt?

   Antwoord: In HTML5-formulieren worden geen fonts ingesloten (in tegenstelling tot PDF-formulieren waarin fonts in het formulier zijn ingesloten). Zorg ervoor dat de in de XDP opgegeven fonts beschikbaar zijn op de server en op de clientcomputer, zodat de HTML-versie van het formulier naar behoren wordt weergegeven. Als de vereiste lettertypen niet beschikbaar zijn op de server, worden er vervangende lettertypen gebruikt. Bovendien worden standaardlettertypen van de browser gebruikt om de tekst weer te geven als u lettertypen in formuliersjablonen gebruikt die niet beschikbaar zijn op het clientapparaat.

1. Worden vAlign- en hAlign-kenmerken ondersteund in HTML-formulieren?

   Ja, de kenmerken vAlign en hAlign worden ondersteund. Het kenmerk vAlign wordt niet ondersteund in Internet Explorer en in velden met meerdere regels.

1. Ondersteunt HTML5-formulieren Hebreeuwse tekens?

   HTML5-formulieren ondersteunen Hebreeuwse tekens in alle browsers behalve Microsoft Internet Explorer.

1. Hebben HTML5-formulieren enige beperkingen op numeriek veld?

   Antwoord: Ja, HTML5-formulieren hebben een aantal beperkingen. Als het aantal cijfers groter is dan het aantal dat is opgegeven in de afbeeldingsvoorwaarde, worden de getallen niet gelokaliseerd en weergegeven in de Engelse landinstelling.

1. Waarom zijn HTML-formulieren groter dan PDF-formulieren?

   Er zijn veel tussenliggende gegevensstructuren en -objecten vereist, zoals formulierdom, gegevensdom en indelingsdom, om een XDP naar een HTML-formulier te renderen.

   Voor PDF-formulieren beschikt Adobe Acrobat over een ingebouwde XTG-engine voor het maken van tussenliggende gegevensstructuren en objecten. Acrobat is ook belast met layout en scripts.

   Voor HTML5-formulieren beschikken browsers niet over een ingebouwde XTG-engine om tussenliggende gegevensstructuren te maken, en hebben ze geen objecten van onbewerkte XDP-bytes. Voor HTML5-formulieren worden dus tussenstructuren gegenereerd op de server en naar de client verzonden. Op client gebruikt de op JavaScript gebaseerde script- en indelingsengine deze tussenliggende structuren.

   De grootte van de tussenliggende structuur is afhankelijk van de grootte van de oorspronkelijke XDP en de gegevens die met de XDP zijn samengevoegd.

1. Zijn er om het even welke beperkingen betreffende het gebruiken van lijsten in mijn xdp?

   Antwoord: Complexe tabellen veroorzaken problemen bij het renderen.

   * Sectie (SubformSet) binnen een tabel wordt niet ondersteund.
   * In sommige tabellen worden kop- of voettekstrijen gemarkeerd voor herhaling. Bij sommige problemen kan het splitsen van dergelijke tabellen over meerdere pagina&#39;s een rol spelen.

1. Hebben toegankelijke tabellen beperkingen?

   Antwoord: Ja, toegankelijke tabellen hebben de volgende beperkingen:

   * Geneste tabellen en subformulieren in een tabel worden niet ondersteund.
   * Kopteksten worden alleen ondersteund voor de bovenste of linkerkolom van de tabel. Kopteksten worden niet ondersteund voor elementen in de middelste tabel. U kunt kopteksten op veelvoudige rij en kolomkopballen toepassen worden gesteund op voorwaarde dat al dergelijke rijen en kolommen samen met de hoogste rij of uiterst linkse kolom van de lijst zijn.
   * `Rowspan`en `colspan`vanuit een willekeurige locatie in de tabel wordt niet ondersteund.

   * U kunt geen instantie van rijen dynamisch toevoegen of verwijderen die elementen met rowspan waarde groter dan 1 bevatten.

1. Wat is de leesvolgorde van knopinfo en bijschrift voor schermlezers?

   * Als zowel het bijschrift als de knopinfo aanwezig zijn, wordt het enige bijschrift gelezen. Als het bijschrift niet beschikbaar is, wordt de knopinfo gelezen. U kunt ook de prioriteit voor het lezen in een XDP opgeven met behulp van formulierontwerper
   * Wanneer u de muisaanwijzer op een element plaatst, wordt knopinfo weergegeven. Als knopinfo niet beschikbaar is, wordt spraaktekst weergegeven. Als de spraaktekst niet beschikbaar is, wordt de veldnaam weergegeven.

1. Wanneer u de cursor op een veld plaatst, wordt knopinfo weergegeven. Hoe kan ik het uitschakelen?

   Als u knopinfo wilt uitschakelen wanneer u de muisaanwijzer aanwijst, selecteert u Geen in het deelvenster Toegankelijkheid van Designer.

1. In Designer kan een gebruiker aangepaste weergave-eigenschappen van keuzerondjes en selectievakjes configureren. Nemen HTML5-formulieren tijdens het weergeven van de formulieren deze aangepaste weergave-eigenschappen in aanmerking?

   Antwoord: In HTML5-formulieren worden de aangepaste weergave-eigenschappen van keuzerondjes en selectievakjes genegeerd. De keuzerondjes en selectievakjes worden weergegeven volgens de specificaties van de onderliggende browser.

1. Wanneer een HTML5-formulier wordt geopend in een ondersteunde browser, wordt de rand van de aangrenzende velden niet goed uitgelijnd of worden subformulieren overlappend weergegeven. Als in Forms Designer een voorbeeld wordt weergegeven van hetzelfde HTML5-formulier, worden de velden en de indeling niet verkeerd uitgelijnd weergegeven en worden de subformulieren op de juiste positie weergegeven. Hoe los je het probleem op?

   Wanneer een subformulier is ingesteld op Stroominhoud en het subformulier heeft een verborgen randelement, wordt de rand van de velden die ernaast worden geplaatst, niet correct uitgelijnd of worden subformulieren overlapt. U kunt het probleem verhelpen door de verborgen &lt;border>-elementen uit de bijbehorende XDP te verwijderen of er opmerkingen aan toe te voegen. Het volgende &lt;border>-element is bijvoorbeeld gemarkeerd als een opmerking:

   ```xml
               <!--<border>
                  <edge presence="hidden"/>
                  <corner thickness="0.175mm" presence="hidden"/>
               </border> -->
   ```

1. Waarom schermlezers niet correct werken met het datum-/tijdveldobject?

   Schermlezers ondersteunen geen datum-/tijdvelden. U kunt echter handmatig datum/tijd invoeren in het veld om de schermlezer de datum/tijd te laten lezen. Gebruik knopinfo of schermlezertekst om de gebruiker op te dragen handmatig datum/tijd voor het veld te selecteren.

1. Biedt HTML5-formulieren ondersteuning voor weergavepatronen voor zwevende velden?

   Antwoord: HTML5-formulieren ondersteunen geen weergavepatronen voor zwevende velden.

### Scripts {#scripting}

1. Zijn er beperkingen in de JavaScript-implementatie voor HTML-formulieren?

   Antwoord:

   * Er is beperkte ondersteuning voor het script xfa.connectionSet. Voor connectionSet wordt alleen aanroep van de webservice op de server ondersteund. Zie [Scriptondersteuning](/help/forms/using/scripting-support.md)voor meer informatie.
   * Er is geen ondersteuning voor $record en $data in clientscripts. Als de scripts echter zijn geschreven in een formReady, layoutReady-blok, werken de scripts nog steeds omdat deze gebeurtenissen aan de serverzijde worden uitgevoerd.
   * Elementspecifieke scripts voor XFA Draw, zoals het wijzigen van de tekst Tekenen (of de bijschrifttekst in het geval van velden), worden niet ondersteund.

1. Zijn er beperkingen in het gebruik van formCalc?

   Antwoord: Er is momenteel alleen een subset van de FormCalc-scripts geïmplementeerd. Zie [Scriptondersteuning](/help/forms/using/scripting-support.md)voor meer informatie.

1. Is er een aanbevolen naamgevingsconventie en zijn er gereserveerde trefwoorden die moeten worden vermeden?

   * In AEM Forms Designer wordt aangeraden de naam van een object (zoals een subformulier of een tekstveld) niet met een onderstrepingsteken (_) te laten beginnen. Als u het onderstrepingsteken aan het begin van de naam wilt gebruiken, voegt u een voorvoegsel toe na het onderstrepingsteken, _&lt;prefix>&lt;objectname>.
   * Alle API&#39;s voor HTML5-formulieren zijn gereserveerde trefwoorden. Gebruik voor aangepaste API&#39;s/functies een naam die niet gelijk is aan API&#39;s voor [HTML5-formulieren](/help/forms/using/scripting-support.md).

1. Biedt HTML5-formulieren ondersteuning voor zwevende velden?

   Ja, HTML5 Forms ondersteunt zwevende velden. Als u zwevende velden wilt inschakelen, voegt u de volgende eigenschap toe aan het renderprofiel:

   >[!NOTE]
   >
   >De velden zijn standaard niet ingeschakeld voor zweven. Met Forms Designer kunt u de zwevende eigenschap van de velden instellen.

   1. Open de CRXde-lijst en navigeer naar het `/content/xfaforms/profiles/default` knooppunt.
   1. Voeg een eigenschap `mfDataDependentFloatingField`van het type String toe en stel de waarde van de eigenschap in op `true`.
   1. Klik op Alles **opslaan**. De zwevende velden worden nu ingeschakeld voor de HTML-formulieren met behulp van het bijgewerkte renderprofiel.

      >[!NOTE]
      >
      >Als u zwevende velden wilt inschakelen voor een specifiek formulier zonder het renderingprofiel bij te werken, geeft u de eigenschap mfDataDependentFloatingField=true door als een URL-parameter.

1. Voeren HTML5-formulieren het initialisatiescript en de gebeurtenis form ready meerdere keren uit?

   Ja, de initialisatiescripts en form ready-gebeurtenissen worden meerdere keren uitgevoerd, ten minste één keer op de server en één keer op de client. Er wordt voorgesteld om scripts als initialize of form:ready-gebeurtenissen te schrijven op basis van bepaalde bedrijfslogica (formulier- of veldgegevens), zodat de actie wordt uitgevoerd op basis van de status van de gegevens en de epidemische waarde (als de gegevens identiek zijn).

### XDP ontwerpen {#designing-xdp}

1. Zijn er gereserveerde trefwoorden in HTML5-formulieren?

   Antwoord: Alle API&#39;s voor HTML5-formulieren zijn gereserveerde trefwoorden. Gebruik voor aangepaste API&#39;s/functies een naam die niet gelijk is aan API&#39;s voor [HTML5-formulieren](/help/forms/using/scripting-support.md). Als u objectnamen gebruikt die met een onderstrepingsteken (_) beginnen, wordt het aangeraden naast gereserveerde trefwoorden ook een uniek voorvoegsel na het onderstrepingsteken toe te voegen. Door een voorvoegsel toe te voegen voorkomt u mogelijke conflicten met interne API&#39;s voor HTML5-formulieren. Bijvoorbeeld, `_fpField1`
