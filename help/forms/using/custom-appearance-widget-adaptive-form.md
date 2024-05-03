---
title: Aangepaste weergaven maken voor adaptieve formuliervelden
description: De weergave van out-of-the-box componenten aanpassen in Adaptive Forms.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
docset: aem65
exl-id: 770e257a-9ffd-46a4-9703-ff017ce9caed
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1692'
ht-degree: 0%

---

# Aangepaste weergaven maken voor adaptieve formuliervelden{#create-custom-appearances-for-adaptive-form-fields}

## Inleiding {#introduction}

In adaptieve formulieren worden de [uiterlijk](/help/forms/using/introduction-widgets.md) om u te helpen aangepaste weergaven te maken voor adaptieve formuliervelden en een andere gebruikerservaring te bieden. Vervang bijvoorbeeld keuzerondjes en selectievakjes door schakelknoppen of gebruik aangepaste jQuery-plug-ins om gebruikersinvoer in velden zoals telefoonnummers of e-mailadressen te beperken.

In dit document wordt uitgelegd hoe u met een jQuery-insteekmodule deze alternatieve ervaringen voor adaptieve formuliervelden kunt maken. Daarnaast wordt een voorbeeld weergegeven voor het maken van een aangepaste weergave voor numerieke veldcomponenten die worden weergegeven als een numerieke stapfunctie of schuifregelaar.

Laten we eerst kijken naar de belangrijkste termen en concepten die in dit artikel worden gebruikt.

**Weergave** Verwijst naar de stijl, het uiterlijk en de organisatie van verschillende elementen van een adaptief formulierveld. Het omvat gewoonlijk een etiket, een interactief gebied om input, een hulppictogram, en korte en lange beschrijvingen van het gebied te verstrekken. De aanpassing van de weergave die in dit artikel wordt besproken, is van toepassing op de weergave van het invoergebied van het veld.

**jQuery-insteekmodule** Biedt een standaardmechanisme, gebaseerd op het jQuery-widgetframework, voor het implementeren van een alternatieve weergave.

**ClientLib** Een bibliotheeksysteem aan de clientzijde in AEM verwerking door complexe JavaScript- en CSS-code. Zie Client-Side Libraries gebruiken voor meer informatie.

**Archetype** Een Maven toolkit van de projectmalplaatje die als origineel patroon of model voor Geweven projecten wordt bepaald. Voor meer informatie, zie Inleiding aan Archetypes.

**Gebruikerscontrole** Verwijst naar het hoofdelement in een widget die de waarde van het veld bevat en door het weergaveframework wordt gebruikt om de aangepaste widget-interface te binden aan het aangepaste formuliermodel.

## Stappen om een aangepaste weergave te maken {#steps-to-create-a-custom-appearance}

Op hoog niveau zijn de volgende stappen nodig om een aangepaste weergave te maken:

1. **Een project maken**: Maak een Maven-project dat een inhoudspakket genereert dat op AEM moet worden geïmplementeerd.
1. **Een bestaande widgetklasse uitbreiden**: Breid een bestaande widgetklasse uit en treedt de vereiste klassen met voeten.
1. **Een clientbibliotheek maken**: Maak een `clientLib: af.customwidget` en voeg de vereiste JavaScript- en CSS-bestanden toe.

1. **Het project bouwen en installeren**: Bouw het Maven-project en installeer het gegenereerde inhoudspakket op AEM.
1. **Het aangepaste formulier bijwerken**: Werk de aangepaste eigenschappen van formuliervelden bij om de aangepaste weergave te gebruiken.

### Een project maken {#create-a-project}

Een bepaald archetype is een uitgangspunt voor het creëren van een douaneverschijning. De details van het te gebruiken archetype zijn als volgt:

* **Bewaarplaats**: https://repo1.maven.org/maven2/com/adobe/
* **Artefact-id**: custom-appearance-archetype
* **Groep-id**: com.adobe.aemforms
* **Versie**: 1.0.4

Voer het volgende bevel uit om een lokaal project tot stand te brengen dat op archetype wordt gebaseerd:

`mvn archetype:generate -DarchetypeRepository=https://repo1.maven.org/maven2/com/adobe/ -DarchetypeGroupId=com.adobe.aemforms -DarchetypeArtifactId=custom-appearance-archetype -DarchetypeVersion=1.0.4`

De opdracht downloadt de Maven-plug-ins en archetype-informatie van de opslagplaats en genereert een project op basis van de volgende informatie:

* **groupId**: Groep-id gebruikt door het gegenereerde Maven-project
* **artefactId**: Artefact-id gebruikt door het gegenereerde Maven-project.
* **versie**: Versie voor het gegenereerde Maven-project.
* **package**: Pakket gebruikt voor de bestandsstructuur.
* **artifactName**: Artefactnaam van het gegenereerde AEM.
* **packageGroup**: Pakketgroep van het gegenereerde AEM.
* **widgetName**: Naam van vormgeving die ter referentie wordt gebruikt.

Het gegenereerde project heeft de volgende structuur:

```java
─<artifactId>

 └───src

     └───main

         └───content

             └───jcr_root

                 └───etc

                     └───clientlibs

                         └───custom

                             └───<widgetName>

                                 ├───common [client library - af.customwidgets which encapsulates below clientLibs]

                                 ├───integration [client library - af.customwidgets.<widgetName>_widget which contains template files for integrating a third-party plugin with Adaptive Forms]

                                 │   ├───css

                                 │   └───javascript

                                 └───jqueryplugin [client library - af.customwidgets.<widgetName>_plugin which holds the third-party plugins and related dependencies]

                                     ├───css

                                     └───javascript
```

### Een bestaande widgetklasse uitbreiden {#extend-an-existing-widget-class}

Zodra het projectmalplaatje wordt gecreeerd, doe de volgende veranderingen, zoals vereist:

1. Neem de afhankelijkheid van de externe plug-in van het project op.

   1. Plaats de externe of aangepaste jQuery-plug-ins in het dialoogvenster `jqueryplugin/javascript` map en verwante CSS-bestanden in de `jqueryplugin/css` map. Zie de JS- en CSS-bestanden onder de `jqueryplugin/javascript and jqueryplugin/css` map.

   1. Wijzig de `js.txt` en `css.txt` bestanden die extra JavaScript- en CSS-bestanden van de jQuery-insteekmodule bevatten.

1. Integreer de externe insteekmodule met het framework om interactie mogelijk te maken tussen het aangepaste weergaveframework en de jQuery-insteekmodule. De nieuwe widget werkt alleen nadat u de volgende functies hebt uitgebreid of genegeerd.

<table>
 <tbody>
  <tr>
   <td><strong>Functie</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td><code>render</code></td>
   <td>De renderfunctie retourneert het jQuery-object voor het standaard HTML-element van de widget. Het standaardelement van HTML zou van brandpuntsafhankelijk type moeten zijn. Bijvoorbeeld: <code>&lt;a&gt;</code>, <code>&lt;input&gt;</code>, en <code>&lt;li&gt;</code>. Het geretourneerde element wordt gebruikt zoals <code>$userControl</code>. Als de <code>$userControl</code> geeft de bovenstaande beperking, de functies van de <code>AbstractWidget</code> -klasse werkt zoals verwacht, anders moeten sommige gemeenschappelijke API's (focus, klikken) worden gewijzigd. </td>
  </tr>
  <tr>
   <td><code>getEventMap</code></td>
   <td>Retourneert een kaart om HTML-gebeurtenissen om te zetten in XFA-gebeurtenissen. <br /> <code class="code">{
      blur: XFA_EXIT_EVENT,
      }</code><br /> In dit voorbeeld wordt getoond dat <code>blur</code> is een HTML-gebeurtenis en <code>XFA_EXIT_EVENT</code> is de overeenkomstige XFA-gebeurtenis. </td>
  </tr>
  <tr>
   <td><code>getOptionsMap</code></td>
   <td>Retourneert een kaart met details over de handeling die moet worden uitgevoerd bij de wijziging van een optie. De sleutels zijn de opties die aan widget worden verstrekt en de waarden zijn functies die worden geroepen wanneer een verandering in de optie wordt ontdekt. De widget biedt handlers voor alle algemene opties (behalve <code>value</code> en <code>displayValue</code>).</td>
  </tr>
  <tr>
   <td><code>getCommitValue</code></td>
   <td>Het jQuery-widgetframework laadt de functie wanneer de waarde van de jQuery-widget in het XFA-model wordt opgeslagen (bijvoorbeeld bij afsluitgebeurtenis van een tekstveld). De implementatie moet de waarde retourneren die is opgeslagen in de widget. De handler krijgt de nieuwe waarde voor de optie.</td>
  </tr>
  <tr>
   <td><code>showValue</code></td>
   <td>Standaard wordt in XFA bij Enter de gebeurtenis <code>rawValue</code> wordt weergegeven. Deze functie wordt aangeroepen om de functie <code>rawValue</code> aan de gebruiker. </td>
  </tr>
  <tr>
   <td><code>showDisplayValue</code></td>
   <td>Standaard wordt in XFA bij afsluitgebeurtenis de optie <code>formattedValue</code> wordt weergegeven. Deze functie wordt aangeroepen om de functie <code>formattedValue</code> aan de gebruiker. </td>
  </tr>
 </tbody>
</table>

1. Het JavaScript-bestand in het dialoogvenster `integration/javascript` map, naar wens.

   * De tekst vervangen `__widgetName__` met de eigenlijke widgetnaam.
   * Breid de widget uit van een geschikte buitenste widgetklasse. In de meeste gevallen is dit de klasse widget die overeenkomt met de bestaande widget die wordt vervangen. De naam van de bovenliggende klasse wordt op meerdere locaties gebruikt. Het wordt daarom aanbevolen naar alle instanties van de tekenreeks te zoeken `xfaWidget.textField` in het bestand en deze vervangen door de werkelijk gebruikte bovenliggende klasse.
   * Breid uit `render` methode om een alternatieve UI te verstrekken. Dit is de locatie vanwaar de jQuery-insteekmodule wordt aangeroepen om de gebruikersinterface of het interactiegedrag bij te werken. De `render` de methode zou een user-control element moeten terugkeren.

   * Breid uit `getOptionsMap` methode om opties te overschrijven die worden beïnvloed door een wijziging in de widget. De functie retourneert een toewijzing die details bevat voor de actie die moet worden uitgevoerd bij wijziging van een optie. De sleutels zijn de opties die aan widget worden verstrekt en de waarden zijn de functies die worden geroepen wanneer een verandering in de optie wordt ontdekt.
   * De `getEventMap` De methode wijst gebeurtenissen toe die door widget worden teweeggebracht, met de gebeurtenissen die door het adaptieve vormmodel worden vereist. De standaardwaarde wijst standaard HTML-gebeurtenissen voor de standaardwidget toe en moet worden bijgewerkt als een alternatieve gebeurtenis wordt geactiveerd.
   * De `showDisplayValue` en `showValue` pas de weergave- en bewerkingsafbeeldingsvoorwaarde toe en kan worden overschreven voor een ander gedrag.

   * De `getCommitValue` methode wordt aangeroepen door het raamwerk voor adaptieve formulieren wanneer de `commit`-gebeurtenis plaatsvindt. Over het algemeen is dit de afsluitgebeurtenis, behalve voor de vervolgkeuzelijst, het keuzerondje en de selectievakjes (waar deze voorkomt bij wijziging). Zie voor meer informatie [Adaptieve Forms-expressies](../../forms/using/adaptive-form-expressions.md#p-value-commit-script-p).

   * Het sjabloonbestand biedt voorbeeldimplementatie voor verschillende methoden. Verwijder methoden die niet moeten worden uitgebreid.

### Een clientbibliotheek maken {#create-a-client-library}

Het steekproefproject dat door Maven wordt geproduceerd archetype leidt automatisch vereiste cliëntbibliotheken, en verpakt hen in een cliëntbibliotheek met een categorie `af.customwidgets`. De JavaScript- en CSS-bestanden die beschikbaar zijn in de `af.customwidgets` worden automatisch bij uitvoering opgenomen.

### Samenstellen en installeren {#build-and-install}

Om het project te bouwen, voer het volgende bevel op shell uit om een pakket te produceren CRX dat op de AEM server moet worden geïnstalleerd.

`mvn clean install`

>[!NOTE]
>
>Het beheerde project verwijst naar een externe opslagplaats binnen het POM-bestand. Dit is alleen ter referentie en volgens Maven-standaarden wordt de informatie in de repository vastgelegd in de `settings.xml` bestand.

### Het aangepaste formulier bijwerken {#update-the-adaptive-form}

De aangepaste weergave toepassen op een adaptief formulierveld:

1. Open het adaptieve formulier in de bewerkingsmodus.
1. Open de **Eigenschap** voor het veld waarop u de aangepaste weergave wilt toepassen.
1. In de **Stijlen** tabblad, werkt u de `CSS class` eigenschap om de weergavenaam toe te voegen in het dialoogvenster `widget_<widgetName>` gebruiken. Bijvoorbeeld: **widget_numericstepper**

## Voorbeeld: een aangepaste weergave maken   {#sample-create-a-custom-appearance-nbsp}

Bekijk nu een voorbeeld om een douaneverschijning voor een numeriek gebied tot stand te brengen om als numerieke stapper of schuif te verschijnen. Voer de volgende stappen uit:

1. Voer het volgende bevel uit om een lokaal project tot stand te brengen dat op Maven archetype wordt gebaseerd:

   `mvn archetype:generate -DarchetypeRepository=https://repo1.maven.org/maven2/com/adobe/ -DarchetypeGroupId=com.adobe.aemforms -DarchetypeArtifactId=custom-appearance-archetype -DarchetypeVersion=1.0.4`

   U wordt gevraagd waarden op te geven voor de volgende parameters.
   *De in dit voorbeeld gebruikte waarden worden vet gemarkeerd*.

   `Define value for property 'groupId': com.adobe.afwidgets`

   `Define value for property 'artifactId': customWidgets`

   `Define value for property 'version': 1.0.1-SNAPSHOT`

   `Define value for property 'package': com.adobe.afwidgets`

   `Define value for property 'artifactName': customWidgets`

   `Define value for property 'packageGroup': adobe/customWidgets`

   `Define value for property 'widgetName': numericStepper`

1. Ga naar de `customWidgets` (opgegeven waarde voor de `artifactID` eigenschap) en voer de volgende opdracht uit om een Eclipse-project te genereren:

   `mvn eclipse:eclipse`

1. Open het gereedschap Eclipse en voer de volgende handelingen uit om het Eclipse-project te importeren:

   1. Selecteren **[!UICONTROL File > Import > Existing Projects into Workspace]**.

   1. Blader naar de map waarin u het dialoogvenster `archetype:generate` gebruiken.

   1. Klik op **[!UICONTROL Finish]**.

      ![eclipse-screenshot](assets/eclipse-screenshot.png)

1. Selecteer de widget die voor de aangepaste weergave moet worden gebruikt. In dit voorbeeld wordt de volgende numerieke stepper-widget gebruikt:

   [https://www.jqueryscript.net/form/User-Friendly-Number-Input-Spinner-with-jQuery-Bootstrap.html](https://www.jqueryscript.net/form/User-Friendly-Number-Input-Spinner-with-jQuery-Bootstrap.html)

   Controleer in het Eclipse-project de insteekmodulecode in de `plugin.js` om ervoor te zorgen dat deze voldoet aan de vereisten voor de weergave. In dit voorbeeld voldoet de weergave aan de volgende vereisten:

   * De numerieke stapfunctie moet worden uitgebreid van `- $.xfaWidget.numericInput`.
   * De `set value` De methode van widget plaatst de waarde nadat de nadruk op het gebied is. Dit is een verplichte vereiste voor een adaptieve formulierwidget.
   * De `render` moet worden overschreven om de `bootstrapNumber` methode.

   * Er is geen andere afhankelijkheid van de plug-in dan de hoofdbroncode van de plug-in.
   * In het voorbeeld wordt geen stijl toegepast op de stapfunctie. Er is dus geen extra CSS vereist.
   * De `$userControl` -object beschikbaar moet zijn voor `render` methode. Het is een gebied van `text` type dat is gekloond met de plug-incode.

   * De **+** en **-** De knoppen moeten worden uitgeschakeld wanneer het veld wordt uitgeschakeld.

1. De inhoud van de `bootstrap-number-input.js` (jQuery-insteekmodule) met de inhoud van de `numericStepper-plugin.js` bestand.
1. In de `numericStepper-widget.js` Voeg de volgende code toe om de rendermethode te overschrijven om de insteekmodule aan te roepen en de `$userControl` object:

   ```javascript
   render : function() {
        var control = $.xfaWidget.numericInput.prototype.render.apply(this, arguments);
        var $control = $(control);
        var controlObject;
        try{
            if($control){
            $control.bootstrapNumber();
            var id = $control.attr("id");
            controlObject = $("#"+id);
            }
        }catch (exc){
             console.log(exc);
        }
        return controlObject;
   }
   ```

1. In de `numericStepper-widget.js` bestand, overschrijf de `getOptionsMap` eigenschap om de toegangsoptie te overschrijven en de knoppen + en - in de uitgeschakelde modus te verbergen.

   ```javascript
   getOptionsMap: function(){
       var parentOptionsMap = $.xfaWidget.numericInput.prototype.getOptionsMap.apply(this,arguments),
   
       newMap = $.extend({},parentOptionsMap,
   
        {
   
              "access": function(val) {
              switch(val) {
                 case "open" :
                   this.$userControl.removeAttr("readOnly");
                   this.$userControl.removeAttr("aria-readonly");
                   this.$userControl.removeAttr("disabled");
                   this.$userControl.removeAttr("aria-disabled");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',false);
                   break;
                 case "nonInteractive" :
                 case "protected" :
                   this.$userControl.attr("disabled", "disabled");
                   this.$userControl.attr("aria-disabled", "true");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',true);
                   break;
                case "readOnly" :
                   this.$userControl.attr("readOnly", "readOnly");
                   this.$userControl.attr("aria-readonly", "true");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',true);
                   break;
               default :
                   this.$userControl.removeAttr("disabled");
                   this.$userControl.removeAttr("aria-disabled");
                   this.$userControl.parent().find(".input-group-btn button").prop('disabled',false);
                   break;
             }
          },
      });
      return newMap;
    }
   ```

1. Sla de wijzigingen op en navigeer naar de map met de `pom.xml` en voer het volgende Maven bevel uit om het project te bouwen:

   `mvn clean install`

1. Installeer het pakket met AEM Package Manager.

1. Open het adaptieve formulier in de bewerkingsmodus waarop u de aangepaste weergave wilt toepassen en voer de volgende handelingen uit:

   1. Klik met de rechtermuisknop op het veld waarop u de weergave wilt toepassen en klik op **[!UICONTROL Edit]** om het dialoogvenster Component bewerken te openen.

   1. Werk op het tabblad Stijl de **[!UICONTROL CSS class]** toe te voegen eigenschap `widget_numericStepper`.

De nieuwe weergave die u hebt gemaakt, is nu beschikbaar voor gebruik.
