---
title: Uw gebruikersinterface testen
seo-title: Uw gebruikersinterface testen
description: AEM biedt een raamwerk voor het automatiseren van tests voor uw AEM UI
seo-description: AEM biedt een raamwerk voor het automatiseren van tests voor uw AEM UI
uuid: 408a60b5-cba9-4c9f-abd3-5c1fb5be1c50
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: components, testing
discoiquuid: 938100ad-94f9-408a-819d-72657dc115f7
docset: aem65
translation-type: tm+mt
source-git-commit: 46f2ae565fe4a8cfea49572eb87a489cb5d9ebd7
workflow-type: tm+mt
source-wordcount: '751'
ht-degree: 1%

---


# Uw gebruikersinterface testen{#testing-your-ui}

>[!NOTE]
>
>Vanaf AEM 6.5 is het testframework voor de gebruikersinterface van hobbes.js afgekeurd. Adobe is niet van plan haar verder te verbeteren en raadt klanten aan seleniumautomatisering te gebruiken.
>
>Zie [Vervangen en Verwijderde functies](/help/release-notes/deprecated-removed-features.md).

AEM biedt een raamwerk voor het automatiseren van tests voor uw AEM UI. Met behulp van het framework schrijft en voert u tests voor de gebruikersinterface rechtstreeks in een webbrowser uit. Het framework biedt een javascript API voor het maken van tests.

Het AEM testframework gebruikt Hobbes.js, een testbibliotheek die in Javascript is geschreven. Het Hobbes.js-framework is ontwikkeld voor het testen van AEM als onderdeel van het ontwikkelingsproces. Het framework is nu beschikbaar voor gebruik door het publiek om uw AEM toepassingen te testen.

>[!NOTE]
>
>Raadpleeg de Hobbes.js- [documentatie](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/test-api/index.html) voor volledige informatie over de API.

## Structuur van de tests {#structure-of-tests}

Wanneer het gebruiken van geautomatiseerde tests binnen AEM, zijn de volgende termijnen belangrijk om te begrijpen:

| Actie | Een **actie** is een specifieke activiteit op een Web-pagina zoals het klikken van een verbinding of een knoop. |
|---|---|
| Testcase | Een **testcase** is een specifieke situatie die uit één of meerdere **Acties** kan worden samengesteld. |
| Testsuite | Een **testsuite** is een groep verwante **testcase** die samen een specifiek gebruikscase test. |

## Tests uitvoeren {#executing-tests}

### Testuiteinden weergeven {#viewing-test-suites}

Open de testconsole om de geregistreerde testsuites te zien. Het deelvenster Tests bevat een lijst met testreeksen en de bijbehorende testdoosjes.

Navigeer naar de console Tools via **Global Navigation -> Tools > Operations -> Testing**.

![chlimage_1-63](assets/chlimage_1-63.png)

Wanneer het openen van de console, zijn de Suites van de Test vermeld aan de linkerzijde samen met een optie om alle hen opeenvolgend in werking te stellen. De ruimte aan het recht die met een gevlokte achtergrond wordt getoond, is placeholder voor het tonen van paginainhoud aangezien de tests in werking stellen.

![chlimage_1-64](assets/chlimage_1-64.png)

### Eén testsuite uitvoeren {#running-a-single-test-suite}

Testsets kunnen afzonderlijk worden uitgevoerd. Wanneer u een testsuite uitvoert, verandert de pagina terwijl de testcase wordt uitgevoerd en de bijbehorende handelingen worden uitgevoerd. De resultaten verschijnen na afloop van de test. Pictogrammen geven de resultaten aan.

Een vinkje geeft aan dat een test is geslaagd:

![](do-not-localize/chlimage_1-2.png)

Een X-pictogram geeft aan dat een test is mislukt:

![](do-not-localize/chlimage_1-3.png)

Een testsuite uitvoeren:

1. Klik of tik in het deelvenster Tests op de naam van de testcase die u wilt uitvoeren om de details van de handelingen uit te vouwen.

   ![chlimage_1-65](assets/chlimage_1-65.png)

1. Klik of tik op de testknop **Uitvoeren** .

   ![](do-not-localize/chlimage_1-4.png)

1. De tijdelijke aanduiding wordt tijdens de test vervangen door pagina-inhoud.

   ![chlimage_1-66](assets/chlimage_1-66.png)

1. Bekijk de resultaten van de testcase door op de beschrijving te tikken of te klikken om het deelvenster **Resultaat** te openen. Als u in het deelvenster **Resultaat** op de naam van uw testcase tikt of erop klikt, worden alle details weergegeven.

   ![chlimage_1-67](assets/chlimage_1-67.png)

### Meerdere tests uitvoeren {#running-multiple-tests}

Testsets worden opeenvolgend uitgevoerd in de volgorde waarin ze in de console worden weergegeven. U kunt naar beneden in een test boren om de gedetailleerde resultaten te zien.

![chlimage_1-68](assets/chlimage_1-68.png)

1. Tik in het deelvenster Tests op de knop Alle tests **** uitvoeren of klik op de knop Tests **** uitvoeren onder de titel van de testsuite die u wilt uitvoeren.

   ![](do-not-localize/chlimage_1-5.png)

1. Tik of klik op de titel van de testcase om de resultaten van elke testcase weer te geven. Als u in het deelvenster **Resultaat** op de naam van de test tikt of erop klikt, worden alle details weergegeven.

   ![chlimage_1-69](assets/chlimage_1-69.png)

## Een eenvoudige testsuite maken en gebruiken {#creating-and-using-a-simple-test-suite}

De volgende procedure begeleidt u door het creëren en uitvoeren van een Reeks van de Test gebruikend [Wij.Detailhandel inhoud](/help/sites-developing/we-retail.md), maar u kunt de test gemakkelijk wijzigen om een verschillende Web-pagina te gebruiken.

Zie de documentatie [van de](https://helpx.adobe.com/experience-manager/6-5/sites/developing/using/reference-materials/test-api/index.html)Hobbes.js-API voor meer informatie over het maken van uw eigen testsuites.

1. Open CRXDE Lite. ([https://localhost:4502/crx/de](https://localhost:4502/crx/de))
1. Klik met de rechtermuisknop op de `/etc/clientlibs` map en klik op **Maken > Map** maken. Typ `myTests` de naam en klik op **OK**.
1. Klik met de rechtermuisknop op de `/etc/clientlibs/myTests` map en klik op **Maken > Knooppunt** maken. Gebruik de volgende eigenschapswaarden en klik op **OK**:

   * Naam: `myFirstTest`
   * Type: `cq:ClientLibraryFolder`

1. Voeg de volgende eigenschappen toe aan het myFirstTest-knooppunt:

   | Naam | Type | Waarde |
   |---|---|---|
   | `categories` | Tekenreeks[] | `granite.testing.hobbes.tests` |
   | `dependencies` | Tekenreeks[] | `granite.testing.hobbes.testrunner` |

   >[!NOTE]
   >
   >**Alleen AEM Forms**
   >
   >
   >Als u adaptieve formulieren wilt testen, voegt u de volgende waarden toe aan de categorieën en afhankelijkheden. Bijvoorbeeld:
   >
   >
   >**categorieën**: `granite.testing.hobbes.tests, granite.testing.hobbes.af.commons`
   >
   >
   >**afhankelijkheden**: `granite.testing.hobbes.testrunner, granite.testing.hobbes.af`

1. Klik op Alles **opslaan**.
1. Klik met de rechtermuisknop op het `myFirstTest` knooppunt en klik op **Maken > Bestand** maken. Name the file `js.txt` and click **OK**.
1. Voer de volgende tekst in het `js.txt` bestand in:

   ```
   #base=.
   myTestSuite.js
   ```

1. Klik op Alles **** opslaan en sluit het `js.txt` bestand.
1. Klik met de rechtermuisknop op het `myFirstTest` knooppunt en klik op **Maken > Bestand** maken. Name the file `myTestSuite.js` and click **OK**.
1. Kopieer de volgende code naar het `myTestSuite.js` bestand en sla het bestand op:

   ```
   new hobs.TestSuite("Experience Content Test Suite", {path:"/etc/clientlibs/myTests/myFirstTest/myTestSuite.js"})
      .addTestCase(new hobs.TestCase("Navigate to Experience Content")
         .navigateTo("/content/we-retail/us/en/experience/arctic-surfing-in-lofoten.html")
      )
      .addTestCase(new hobs.TestCase("Hover Over Topnav")
         .mouseover("li.visible-xs")
      )
      .addTestCase(new hobs.TestCase("Click Topnav Link")
         .click("li.active a")
   );
   ```

1. Navigeer naar de **testconsole** om uw testsuite uit te proberen.
