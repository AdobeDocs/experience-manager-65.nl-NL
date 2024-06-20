---
title: Een aangepaste aangepaste formuliersjabloon maken
description: In dit artikel wordt beschreven hoe u aangepaste formuliersjablonen kunt maken.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
docset: aem65
exl-id: 35b50573-0be8-469d-a1ac-f51b9aaa5fef
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: 872e2de411f51b5f0b26a2ff47cb49f01313d39f
workflow-type: tm+mt
source-wordcount: '1265'
ht-degree: 0%

---

# Een aangepaste aangepaste formuliersjabloon maken{#creating-a-custom-adaptive-form-template}

>[!NOTE]
>
>AEM Forms heeft dynamische sjablonen geïntroduceerd. U kunt de AEM Sites-sjablooneditor gebruiken om [dynamische sjablonen maken of bewerken](../../forms/using/template-editor.md). De sjablonen die in het onderstaande artikel worden vermeld, zijn statische sjablonen. Deze zijn niet beschikbaar bij een standaardinstallatie. [Compatibiliteitspakket installeren](../../forms/using/compatibility-package.md) om deze sjablonen op uw omgeving te plaatsen.

## Vereisten {#prerequisites}

* Inzicht in AEM [Paginasjabloon](/help/sites-authoring/templates.md) en [Adaptief ontwerpen van formulieren](https://helpx.adobe.com/aem-forms/6-1/introduction-forms-authoring.html)

* Inzicht in AEM [Client Side Libraries](/help/sites-developing/clientlibs.md)

## Adaptief formuliersjabloon {#adaptive-form-template}

Een adaptieve formuliersjabloon is gespecialiseerd AEM Paginasjabloon, met bepaalde eigenschappen en inhoudsstructuur die worden gebruikt om een adaptief formulier te maken. De sjabloon heeft vooraf geconfigureerde lay-outs, stijlen en initiële basisinhoudsstructuur.

Als u een formulier hebt gemaakt, worden wijzigingen in de oorspronkelijke structuur van de sjablooninhoud niet meer doorgevoerd in het formulier.

## Standaard adaptieve formuliersjablonen {#default-adaptive-form-templates}

AEM QuickStart bevat de volgende adaptieve formuliersjablonen:

* Beoordelingssjabloon: hiermee kunt u één pagina adaptief formulier maken met de indeling Responsief waarin meerdere kolommen zijn geconfigureerd. De indeling wordt automatisch aangepast op basis van de afmetingen van de verschillende schermen waarop u het formulier wilt weergeven.
* Eenvoudige inschrijfsjabloon: hiermee kunt u in meerdere stappen een adaptief formulier maken met een wizardindeling. In deze lay-out, kunt u een uitdrukking van de stapvoltooiing voor elke stap specificeren, die wordt bevestigd alvorens de tovenaar aan de volgende stap te werk gaat.
* Sjabloon voor inschrijving met tabbladen: hiermee kunt u een adaptief formulier met meerdere tabbladen maken in een lay-out die links wordt weergegeven en waarin u tabbladen in willekeurige volgorde kunt bezoeken.
* Geavanceerd inschrijfsjabloon: hiermee kunt u een formulier maken met meerdere tabbladen en wizard. Er wordt een lay-out met tabs links gebruikt waarmee u tabbladen in willekeurige volgorde kunt bezoeken. Voor ondertekening en verificatie worden Adobe Document Cloud-ontwerpservices gebruikt.
* Lege sjabloon: hiermee kunt u een formulier maken zonder koptekst, voettekst en eerste inhoud. U kunt componenten toevoegen, zoals tekstvakken, knoppen en afbeeldingen. Met de lege sjabloon kunt u een formulier maken dat [insluiten in AEM sitepagina&#39;s](/help/forms/using/embed-adaptive-form-aem-sites.md).

Deze sjablonen bevatten de `sling:resourceType` eigenschap ingesteld op de overeenkomende pagina-component. De paginacomponent geeft de CQ-pagina weer, die een adaptieve formuliercontainer bevat, die op zijn beurt weer een adaptief formulier maakt.

In de volgende tabel wordt de koppeling tussen sjablonen en paginacomponent opgesomd:

<table>
 <tbody>
  <tr>
   <td><p><strong>Sjabloon</strong></p> </td>
   <td><p><strong>Pagina-component</strong></p> </td>
  </tr>
  <tr>
   <td><p>/libs/fd/af/templates/surveyTemplate</p> </td>
   <td><p>/libs/fd/af/components/page/survey</p> </td>
  </tr>
  <tr>
   <td><p>/libs/fd/af/templates/simpleEnrollmentTemplate</p> </td>
   <td><p>/libs/fd/af/components/page/base</p> </td>
  </tr>
  <tr>
   <td><p>/libs/fd/af/templates/tabbedEnrollmentTemplate</p> </td>
   <td><p>/libs/fd/af/components/page/tabbedenrollment</p> </td>
  </tr>
  <tr>
   <td><p>/libs/fd/afaddon/templates/advancedEnrollmentTemplate</p> </td>
   <td><p>/libs/fd/afaddon/components/page/advancedRolment</p> </td>
  </tr>
 </tbody>
</table>

## Een aangepaste formuliersjabloon maken met behulp van een sjablooneditor {#creating-an-adaptive-form-template-using-template-editor}

U kunt de structuur en de initiële inhoud van een adaptief formulier opgeven met de Sjablooneditor. U wilt bijvoorbeeld dat alle formulierauteurs weinig tekstvakken, navigatieknoppen en een verzendknop in een inschrijvingsformulier hebben. U kunt een sjabloon maken die auteurs kunnen gebruiken om een formulier te maken dat consistent is met andere inschrijvingsformulieren. Met AEM Sjablooneditor kunt u:

* Koptekst- en voettekstcomponenten van een formulier toevoegen in de structuurlaag
* Geef de initiële inhoud voor het formulier op.
* Geef een thema op.
* Geef handelingen op, zoals Verzenden, Herstellen en Navigeren.

Zie voor meer informatie [Sjablooneditor](../../forms/using/template-editor.md).

## Een adaptieve formuliersjabloon maken op basis van CRXDE {#creating-an-adaptive-form-template-from-crxde}

In plaats van de beschikbare sjablonen te gebruiken, kunt u een sjabloon maken en deze gebruiken om adaptieve formulieren te maken. Aangepaste sjablonen zijn gebaseerd op verschillende paginacomponenten die verwijzen naar aangepaste formuliercontainers en pagina-elementen, zoals kop- en voettekst.

U kunt deze componenten maken met de basispaginacomponent voor uw website. U kunt ook de paginacomponent van het adaptieve formulier uitbreiden die in de vaksjablonen wordt gebruikt.

Voer de volgende stappen uit om een douanemalplaatje, zoals simpleEnrollmentTemplate tot stand te brengen.

1. Navigeer naar CRXDE Lite op de ontwerpinstantie.

1. Maak onder de map /apps de mapstructuur voor uw toepassing. Als de toepassingsnaam bijvoorbeeld mijn bedrijf is, maakt u een map met deze naam. De toepassingsmap bevat doorgaans componenten, configuratie, sjablonen, bron en installatiemappen. In dit voorbeeld maakt u de mappen voor componenten, configuratie en sjablonen.

1. Navigeer naar de map /libs/fd/af/templates.
1. De `simpleEnrollmentTemplate` knooppunt.
1. Ga naar de map /apps/mijnbedrijf/sjablonen. Klik er met de rechtermuisknop op en selecteer **[!UICONTROL Paste]**.
1. Wijzig zo nodig de naam van het sjabloonknooppunt dat u hebt gekopieerd. Wijzig bijvoorbeeld de naam ervan in een inschrijfsjabloon.

1. Navigeer naar de locatie /apps/mijnbedrijf/sjablonen/inschrijvingssjabloon.

1. Wijzig de `jcr:title` en `jcr:description` eigenschappen voor de `jcr:content` knoop om het malplaatje van het malplaatje te onderscheiden u kopieerde.

1. De `jcr:content` het knooppunt van de gewijzigde sjabloon bevat het `guideContainer` en `guideformtitle` componenten. `guideContainer` is de container die het adaptieve formulier bevat. De `guideformtitle` geeft de toepassingsnaam, beschrijving enzovoort weer.

   In plaats van `guideformtitle`, kunt u een aangepaste component of de `parsys` component. Verwijder bijvoorbeeld `guideformtitle`en voegt u een aangepaste component of de `parsys` componentknooppunt. Zorg ervoor dat de `sling:resourceType` eigenschap van de component verwijst naar de component en hetzelfde wordt gedefinieerd op de pagina `component.jsp` bestand.

1. Navigeer naar de locatie /apps/mijnbedrijf/sjablonen/inschrijving-sjabloon/jcr:content.

1. Open de **[!UICONTROL Properties]** en wijzigt u de waarde van de optie `cq:designPath` eigenschap aan /etc/designs/mijnbedrijf.

1. Maak nu een /etc/designs/mycompany-knooppunt voor de `cq:Page` type.

## Een adaptief onderdeel van een formulierpagina maken {#create-an-adaptive-form-page-component}

De aangepaste sjabloon heeft dezelfde opmaak als de standaardsjabloon, omdat de sjabloon verwijst naar de paginacomponent /libs/fd/af/components/page/base. U kunt de componentenverwijzing als bezit vinden `sling:resourceType` gedefinieerd op het knooppunt /apps/mijnbedrijf/sjablonen/inschrijving-sjabloon/jcr:content. Omdat de basis een kernproductcomponent is, wijzigt u deze component niet.

1. Navigeer naar het knooppunt /apps/mijnbedrijf/sjablonen/inschrijving-sjabloon/jcr:content en wijzig de waarde van de eigenschap `sling:resourceType` naar /apps/mijnbedrijf/componenten/pagina/inschrijfpagina
1. Kopieer het knooppunt /libs/fd/af/components/page/base naar de map /apps/mijnbedrijf/componenten/pagina.

1. De naam van de gekopieerde component wijzigen in `enrollmentpage`.

1. **(Alleen als u al een inhoudspagina hebt)** Voer de volgende stappen (a-d) uit als u een bestaande `contentpage`component voor uw website. Als u geen bestaande `contentpage`kunt u de component voor uw website `resourceSuperType`eigenschap om naar de basispagina buiten het vak te wijzen.

   1. Voor de `enrollmentpage` node, waarde instellen voor eigenschap `sling:resourceSuperType` naar mijnbedrijf/componenten/pagina/inhoudspagina. De `contentpage` is de basispaginacomponent voor uw site. Andere paginacomponenten kunnen het uitbreiden. Scriptbestanden verwijderen onder `enrollmentpage`, behalve `head.jsp`, `content.jsp`, en `library.jsp`. De `sling:resourceSuperType` component, die `contentpage` in dit geval, omvat al dergelijke manuscripten. Kopteksten, waaronder de navigatiebalk en de voettekst, worden overgenomen van de `contentpage` component.

   1. Het bestand openen `head.jsp`.

      Het JSP-bestand bevat de regel `<cq.include script="library.jsp"/>`.

      De `library.jsp` bevat het bestand `guide.theme.simpleEnrollment` clientbibliotheek, die de opmaak voor het adaptieve formulier bevat.

      De component page `enrollmentpage` heeft een exclusieve `head.jsp` bestand dat het `head.jsp` van het `contentpage` component.

   1. Alle scripts opnemen in het dialoogvenster `head.jsp` bestand voor de `contentpage` aan de component `head.jsp` bestand voor de `enrollmentpage` component.
   1. In de `content.jsp` , kunt u extra pagina-inhoud of verwijzingen naar andere componenten toevoegen die worden opgenomen wanneer een pagina wordt weergegeven. Als u bijvoorbeeld de aangepaste component toevoegt `applicationformheader`, zorg ervoor dat u de volgende verwijzing naar de component in het JSP dossier toevoegt:

      `<cq:include path="applicationformheader" resourceType="mycompany/components/applicationformheader"/>`

      En als u een `parsys` neemt ook de aangepaste component op in de sjabloonknooppuntstructuur.

## Een adaptieve formulierclientbibliotheek maken {#creating-an-adaptive-form-client-library}

De `head.jsp` van het `enrollmentpage` component voor de nieuwe sjabloon bevat een clientbibliotheek `guide.theme.simpleEnrollment`. De standaardsjabloon gebruikt deze clientbibliotheek ook. Wijzig de stijl in de nieuwe sjabloon op een van de volgende manieren:

* Een aangepast thema definiëren en het standaardthema vervangen `guide.theme.simpleEnrollment` met het aangepaste thema.
* Definieer een nieuwe clientbibliotheek onder /etc/designs/mijnbedrijf. Neem de clientbibliotheek op na het standaardthemaitem in de jsp-pagina. Neem alle overschreven stijlen en extra JavaScript-bestanden op in deze clientbibliotheek.

>[!NOTE]
>
>Thema verwijst naar een clientbibliotheek die is opgenomen in de paginacomponent die wordt gebruikt om een adaptief formulier te genereren. De clientbibliotheek is voornamelijk van toepassing op het uiterlijk van een adaptief formulier.
