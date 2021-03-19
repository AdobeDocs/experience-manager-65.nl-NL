---
title: '"Zelfstudie: Het adaptieve formulier testen"'
seo-title: '"Zelfstudie: Het adaptieve formulier testen"'
description: Gebruik automatische tests om meerdere adaptieve formulieren tegelijk te testen.
seo-description: Gebruik automatische tests om meerdere adaptieve formulieren tegelijk te testen.
uuid: 6d182bbc-b47a-4c97-af70-c960b52fdfac
contentOwner: khsingh
discoiquuid: ecddb22e-c148-441f-9088-2e5b35c7021b
docset: aem65
feature: Adaptieve Forms
translation-type: tm+mt
source-git-commit: 48726639e93696f32fa368fad2630e6fca50640e
workflow-type: tm+mt
source-wordcount: '906'
ht-degree: 1%

---


# Zelfstudie: Het adaptieve formulier {#tutorial-testing-your-adaptive-form} testen

![](do-not-localize/10-test-your-adaptive-form.png)

Deze zelfstudie is een stap in de serie [Uw eerste adaptieve vorm maken](https://helpx.adobe.com/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html). U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

Nadat het adaptieve formulier gereed is, is het belangrijk dat u het adaptief test voordat u het naar de eindgebruikers implementeert. U kunt elk veld handmatig testen (functionele tests) of het testen van het adaptieve formulier automatiseren. Wanneer u meerdere adaptieve formulieren hebt, wordt het handmatig testen van elk veld van alle adaptieve formulieren een enorme opgave.

AEM [!DNL Forms] biedt een testframework, Calvin, om het testen van uw adaptieve formulieren te automatiseren. Met behulp van het framework schrijft en voert u tests voor de gebruikersinterface rechtstreeks in een webbrowser uit. Het framework biedt JavaScript API&#39;s voor het maken van tests. Met de geautomatiseerde testprocedure kunt u de vooraf ingevulde ervaring van een adaptief formulier testen, ervaringen met een adaptief formulier, expressieregels, validaties, lazy loading en UI-interacties verzenden. Deze zelfstudie begeleidt u door de stappen voor het maken en uitvoeren van geautomatiseerde tests op een adaptieve vorm. Aan het einde van deze zelfstudie kunt u het volgende doen:

* [Een testsuite maken voor uw adaptieve formulier](../../forms/using/testing-your-adaptive-form.md#step-create-a-test-suite)
* [Tests maken voor uw adaptieve formulier](../../forms/using/testing-your-adaptive-form.md#step-create-a-test-case-to-prefill-values-in-an-adaptive-form)
* [Testsuite en tests voor uw aangepaste formulier uitvoeren](#step-run-all-the-tests-in-a-suite-or-individual-tests-cases)

## Stap 1: Een testsuite {#step-create-a-test-suite} maken

De testreeksen hebben een inzameling van testgevallen. U kunt meerdere testreeksen hebben. Het wordt aanbevolen voor elk formulier een aparte testsuite te gebruiken. Een testsuite maken:

1. Log naar AEM [!DNL Forms] auteurinstantie als beheerder. Open [!UICONTROL CRXDE Lite]. U kunt op AEM Logo > **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL CRXDE Lite]** tikken of de URL [https://localhost:4502/crx/de/index.jsp](https://localhost:4502/crx/de/index.jsp) in een browser openen om CRXDE Lite te openen.

1. Navigeer naar /etc/clientlibs in [!UICONTROL CRXDE Lite]. Klik met de rechtermuisknop op de submap /etc/clientlibs en klik op **[!UICONTROL Create]** > **[!UICONTROL Create Node]**. In het **[!UICONTROL Name]** veldtype **WeRetailFormTestCase**. Selecteer het type als **cq:ClientLibraryFolder** en klik **[!UICONTROL OK]**. Er wordt een knooppunt gemaakt. U kunt elke naam gebruiken in plaats van `WeRetailFormTestCases`.
1. Voeg de volgende eigenschappen toe aan de `WeRetailFormTestCases` knoop en tik **[!UICONTROL Save ALL]**.

   <table>
    <tbody>
     <tr>
      <td><strong>Eigenschap</strong></td>
      <td><strong>Type</strong></td>
      <td><strong>Multi</strong></td>
      <td><strong>Waarde</strong></td>
     </tr>
     <tr>
      <td>categorieën</td>
      <td>Tekenreeks</td>
      <td>Ingeschakeld</td>
      <td>
       <ul>
        <li>granite.testing.hobbes.tests<br /> </li>
        <li>granite.testing.calvin.tests</li>
       </ul> </td>
     </tr>
     <tr>
      <td>afhankelijkheden</td>
      <td>Tekenreeks</td>
      <td>Ingeschakeld</td>
      <td>
       <ul>
        <li>granite.testing.hobbes.testrunner <br /> </li>
        <li>granite.testing.calvin <br /> </li>
        <li>apps.testframework.all</li>
       </ul> </td>
     </tr>
    </tbody>
   </table>

   Zorg ervoor dat elke eigenschap wordt toegevoegd aan een afzonderlijk vak, zoals hieronder wordt weergegeven:

   ![afhankelijkheden](assets/dependencies.png)

1. Klik met de rechtermuisknop op het knooppunt **[!UICONTROL WeRetailFormTestCases]** en klik op **[!UICONTROL Create]** > **[!UICONTROL Create File]**. Typ `js.txt` in het veld **[!UICONTROL Name]** en klik op **[!UICONTROL OK]**.
1. Open het bestand js.txt om het te bewerken, voeg de volgende code toe en sla het bestand op:

   ```text
   #base=.
    init.js
   ```

1. Maak een bestand met de naam init.js in het knooppunt `WeRetailFormTestCases`. Voeg de onderstaande code toe aan het bestand en tik op **[!UICONTROL Save All]**.

   ```javascript
   (function(window, hobs) {
       'use strict';
       window.testsuites = window.testsuites || {};
     // Registering the test form suite to the sytem
     // If there are other forms, all registration should be done here
       window.testsuites.testForm3 = new hobs.TestSuite("We retail - Tests", {
           path: '/etc/clientlibs/WeRetailFormTestCases/init.js',
           register: true
       });
    // window.testsuites.testForm2 = new hobs.TestSuite("testForm2");
   }(window, window.hobs));
   ```

   De bovenstaande code maakt een testsuite met de naam **We Retail - Tests**.

1. Open AEM testinterface (AEM > **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Testing]**). De testsuite - **We Retail - Tests** - wordt weergegeven in de gebruikersinterface.

   ![we-retail-testsuite](assets/we-retail-test-suite.png)

## Stap 2: Een testcase maken om waarden vooraf in te vullen in een adaptieve vorm {#step-create-a-test-case-to-prefill-values-in-an-adaptive-form}

Een testcase is een reeks handelingen om een specifieke functionaliteit te testen. U kunt bijvoorbeeld alle velden van een formulier vooraf invullen en enkele velden valideren om ervoor te zorgen dat de juiste waarden worden ingevoerd.

Een handeling is een specifieke activiteit op een adaptief formulier, zoals het klikken op een knop. U kunt als volgt een testcase en -acties maken om de gebruikersinvoer voor elk adaptief formulierveld te valideren:

1. Navigeer in [!UICONTROL CRXDE lite] naar de map `/content/forms/af/create-first-adaptive-form`. Klik met de rechtermuisknop op het mapknooppunt **[!UICONTROL create-first-adaptive-form]** en klik op **[!UICONTROL Create]** **[!UICONTROL Create File]**. Typ `prefill.xml` in het veld **[!UICONTROL Name]** en klik op **[!UICONTROL OK]**. Voeg de volgende code toe aan het bestand:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?><afData>
     <afUnboundData>
       <data>
         <customer_ID>371767</customer_ID>
         <customer_Name>John Jacobs</customer_Name>
         <customer_Shipping_Address>1657 1657 Riverside Drive Redding</customer_Shipping_Address>
         <customer_State>California</customer_State>
         <customer_ZIPCode>096001</customer_ZIPCode>
        </data>
     </afUnboundData>
     <afBoundData>
       <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/"/>
     </afBoundData>
   </afData>
   ```

1. Ga naar `/etc/clientlibs`. Klik met de rechtermuisknop op de submap `/etc/clientlibs` en klik **[!UICONTROL Create]** **[!UICONTROL Create Node]**.

   Typ `WeRetailFormTests` in het veldtype **[!UICONTROL Name]**. Selecteer de tekst als `cq:ClientLibraryFolder` en klik **[!UICONTROL OK]**.

1. Voeg de volgende eigenschappen aan de **[!UICONTROL WeRetailFormTests]** knoop toe.

   <table>
    <tbody>
     <tr>
      <td><strong>Eigenschap</strong></td>
      <td><strong>Type</strong></td>
      <td><strong>Multi</strong></td>
      <td><strong>Waarde</strong></td>
     </tr>
     <tr>
      <td>categorieën</td>
      <td>Tekenreeks</td>
      <td>Ingeschakeld</td>
      <td>
       <ul>
        <li>granite.testing.hobbes.tests<br /> </li>
        <li>granite.testing.hobbes.tests.testForm</li>
       </ul> </td>
     </tr>
     <tr>
      <td>afhankelijkheden</td>
      <td>Tekenreeks</td>
      <td>Ingeschakeld</td>
      <td>
       <ul>
        <li>granite.testing.calvin.tests</li>
       </ul> </td>
     </tr>
     </tbody>
   </table>

1. Maak een bestand met de naam js.txt in het knooppunt **[!UICONTROL WeRetailFormTests]**. Voeg het volgende toe aan het bestand:

   ```shell
   #base=.
   prefillTest.js
   ```

   Klik op **[!UICONTROL Save All]**.

1. Maak een bestand, `prefillTest.js`, in het knooppunt **[!UICONTROL WeRetailFormTests]**. Voeg de onderstaande code toe aan het bestand. In de code wordt een testcase gemaakt. Het testhoofdlettergebruik vult alle velden van een formulier voor en valideert bepaalde velden om ervoor te zorgen dat correcte waarden worden ingevoerd.

   ```javascript
   (function (window, hobs) {
       'use strict';
   
       var ts = new hobs.TestSuite("Prefill Test", {
           path: '/etc/clientlibs/WeRetailFormTests/prefillTest.js',
           register: false
       })
   
       .addTestCase(new hobs.TestCase("Prefill Test")
           // navigate to the testForm which is to be test
           .navigateTo("/content/forms/af/create-first-adaptive-form/shipping-address-add-update-form.html?wcmmode=disabled&dataRef=crx:///content/forms/af/create-first-adaptive-form/prefill.xml")
           // check if adaptive form is loaded
           .asserts.isTrue(function () {
               return calvin.isFormLoaded()
           })
           .asserts.isTrue(function () {
               return calvin.model("customer_ID").value == 371767;
           })
           .asserts.isTrue(function () {
               return calvin.model("customer_ZIPCode").value == 96001;
           })
       );
   
       // register the test suite with testForm
       window.testsuites.testForm3.add(ts);
   
   }(window, window.hobs));
   ```

   De testcase wordt gemaakt en kan worden uitgevoerd. U kunt testcase maken om verschillende aspecten van een adaptief formulier te valideren, zoals het controleren van de uitvoering van het berekeningsscript, het valideren van patronen en het valideren van de verzendervaring van een adaptief formulier. Zie het automatisch testen van adaptieve formulieren voor informatie over verschillende aspecten van het testen van adaptieve formulieren.

## Stap 3: Alle tests uitvoeren in een suite of in afzonderlijke testgevallen {#step-run-all-the-tests-in-a-suite-or-individual-tests-cases}

Een testsuite kan meerdere testgevallen bevatten. U kunt alle testgevallen in een testsuite tegelijk of afzonderlijk uitvoeren. Wanneer u een test uitvoert, geven de pictogrammen de resultaten aan:

* Een vinkje geeft aan dat een test is geslaagd: ![save_icon](assets/save_icon.svg)
* Een X-pictogram geeft aan dat een test is mislukt: ![close-icon](assets/close-icon.svg)

1. Ga naar AEM pictogram > **[!UICONTROL Tools]** **[!UICONTROL Operations]** **[!UICONTROL Testing]**
1. Alle tests van de testsuite uitvoeren:

   1. Tik in het [!UICONTROL Tests]-deelvenster op **[!UICONTROL We retail - Tests (1)]**. De suite wordt uitgebreid om een testlijst weer te geven.
   1. Tik op de knop **[!UICONTROL Run tests]**. Het lege gebied aan de rechterkant van het scherm wordt tijdens de test vervangen door een adaptieve vorm.

      ![run-all-test](assets/run-all-test.png)

1. Eén test uitvoeren vanuit de testsuite:

   1. Tik in het deelvenster Tests op **[!UICONTROL We retail - Tests (1)]**. De suite wordt uitgebreid om een testlijst weer te geven.
   1. Tik op **[!UICONTROL Prefill Test]** en tik op **[!UICONTROL Run tests]**. Het lege gebied aan de rechterkant van het scherm wordt tijdens de test vervangen door een adaptieve vorm.

1. Tik op de testnaam, de test Vooraf invullen, om de resultaten van de testcase te bekijken. Hiermee wordt het deelvenster [!UICONTROL Result] geopend. Tik op de naam van uw testcase in het deelvenster [!UICONTROL Result] om alle details van de test weer te geven.

   ![revisie](assets/review-results.png)

Het aangepaste formulier kan nu worden gepubliceerd.
