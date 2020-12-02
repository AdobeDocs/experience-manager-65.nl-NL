---
title: Een aangepaste aangepaste formuliersjabloon maken
seo-title: Een aangepaste aangepaste formuliersjabloon maken
description: In dit artikel wordt beschreven hoe u aangepaste formuliersjablonen kunt maken.
seo-description: In dit artikel wordt beschreven hoe u aangepaste formuliersjablonen kunt maken.
uuid: 11b5f8cd-c56a-4525-97d5-1938ef5f183d
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
discoiquuid: affba49e-9712-4d29-858b-2f8ec4f2b1f1
docset: aem65
translation-type: tm+mt
source-git-commit: 4ecf5efc568cd21f11801a71d491c3d75ca367fe
workflow-type: tm+mt
source-wordcount: '1284'
ht-degree: 0%

---


# Een aangepaste aangepaste formuliersjabloon maken{#creating-a-custom-adaptive-form-template}

>[!NOTE]
>
>AEM Forms heeft dynamische sjablonen geïntroduceerd. U kunt de malplaatjeredacteur van AEM Sites gebruiken om [dynamische malplaatjes te creëren of uit te geven](../../forms/using/template-editor.md). De sjablonen die in het onderstaande artikel worden vermeld, zijn statische sjablonen. Deze zijn niet beschikbaar bij een standaardinstallatie. [Installeer het compatibiliteitspakket ](../../forms/using/compatibility-package.md) om deze sjablonen in uw omgeving te plaatsen.

## Vereisten {#prerequisites}

* Begrijpen van AEM [Paginasjabloon](/help/sites-authoring/templates.md) en [Adaptieve formulierontwerpomgeving](https://helpx.adobe.com/aem-forms/6-1/introduction-forms-authoring.html)

* Inzicht in AEM [Client Side Libraries](/help/sites-developing/clientlibs.md)

## Adaptief formuliersjabloon {#adaptive-form-template}

Een adaptieve formuliersjabloon is gespecialiseerd AEM Paginasjabloon, met bepaalde eigenschappen en inhoudsstructuur die worden gebruikt om een adaptief formulier te maken. De sjabloon heeft vooraf geconfigureerde lay-outs, stijlen en initiële basisinhoudsstructuur.

Als u een formulier hebt gemaakt, worden wijzigingen in de oorspronkelijke structuur van de sjablooninhoud niet meer doorgevoerd in het formulier.

## Standaard adaptieve formuliersjablonen {#default-adaptive-form-templates}

AEM QuickStart bevat de volgende adaptieve formuliersjablonen:

* Beoordelingssjabloon: Hiermee kunt u een adaptief formulier van één pagina maken met de indeling Responsief waarin meerdere kolommen zijn geconfigureerd. De indeling wordt automatisch aangepast op basis van de afmetingen van de verschillende schermen waarop u het formulier wilt weergeven.
* Eenvoudige inschrijfsjabloon: Hiermee kunt u een adaptief formulier met meerdere stappen maken met een wizardindeling. In deze lay-out, kunt u een uitdrukking van de stapvoltooiing voor elke stap specificeren, die wordt bevestigd alvorens de tovenaar aan de volgende stap te werk gaat.
* Sjabloon voor inschrijving met tabbladen: Hiermee kunt u een adaptief formulier met meerdere tabbladen maken met een lay-out voor tabbladen links, waar u tabbladen in willekeurige volgorde kunt bekijken.
* Geavanceerd inschrijfsjabloon: Hiermee kunt u een formulier maken met meerdere tabbladen en wizard. Er wordt een lay-out met tabs links gebruikt waarmee u tabbladen in willekeurige volgorde kunt bezoeken. Voor ondertekening en verificatie worden Adobe Document Cloud-ontwerpservices gebruikt.
* Lege sjabloon: Hiermee kunt u een formulier maken zonder koptekst, voettekst en eerste inhoud. U kunt componenten toevoegen, zoals tekstvakken, knoppen en afbeeldingen. Met de lege sjabloon kunt u een formulier maken dat u [kunt insluiten in AEM sitepagina&#39;s](/help/forms/using/embed-adaptive-form-aem-sites.md).

Voor deze sjablonen is de eigenschap `sling:resourceType` ingesteld op de corresponderende paginacomponent. De paginacomponent geeft de CQ-pagina weer, die een adaptieve formuliercontainer bevat, die op zijn beurt weer een adaptief formulier maakt.

In de volgende tabel wordt de koppeling tussen sjablonen en paginacomponent opgesomd:

<table>
 <tbody>
  <tr>
   <td><p><strong>Sjabloonmodel</strong></p> </td>
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

## Een aangepaste formuliersjabloon maken met behulp van sjablooneditor {#creating-an-adaptive-form-template-using-template-editor}

U kunt de structuur en de initiële inhoud van een adaptief formulier opgeven met de Sjablooneditor. U wilt bijvoorbeeld dat alle formulierauteurs weinig tekstvakken, navigatieknoppen en een verzendknop in een inschrijvingsformulier hebben. U kunt een sjabloon maken die auteurs kunnen gebruiken om een formulier te maken dat consistent is met andere inschrijvingsformulieren. Met AEM Sjablooneditor kunt u:

* Koptekst- en voettekstcomponenten van een formulier toevoegen in de structuurlaag
* Geef de initiële inhoud voor het formulier op.
* Geef een thema op.
* Geef handelingen op, zoals Verzenden, Herstellen en Navigeren.

Zie [Sjablooneditor](../../forms/using/template-editor.md) voor meer informatie.

## Een adaptieve formuliersjabloon maken op basis van CRXDE {#creating-an-adaptive-form-template-from-crxde}

In plaats van de beschikbare sjablonen te gebruiken, kunt u een sjabloon maken en deze gebruiken om adaptieve formulieren te maken. Aangepaste sjablonen zijn gebaseerd op verschillende paginacomponenten die verwijzen naar aangepaste formuliercontainers en pagina-elementen, zoals kop- en voettekst.

U kunt deze componenten maken met de basispaginacomponent voor uw website. U kunt ook de paginacomponent van het adaptieve formulier uitbreiden die in de vaksjablonen wordt gebruikt.

Voer de volgende stappen uit om een douanemalplaatje, zoals simpleEnrollmentTemplate tot stand te brengen.

1. Navigeer naar CRXDE Lite op de ontwerpinstantie.

1. Maak onder de map /apps de mapstructuur voor uw toepassing. Als de toepassingsnaam bijvoorbeeld mijn bedrijf is, maakt u een map met deze naam. De toepassingsmap bevat doorgaans componenten, configuratie, sjablonen, bron en installatiemappen. In dit voorbeeld maakt u de mappen voor componenten, configuratie en sjablonen.

1. Navigeer naar de map /libs/fd/af/templates.
1. Kopieer de `simpleEnrollmentTemplate` knoop.
1. Navigeer naar de map /apps/mijnbedrijf/sjablonen. Klik er met de rechtermuisknop op en selecteer **[!UICONTROL Paste]**.
1. Wijzig zo nodig de naam van het sjabloonknooppunt dat u hebt gekopieerd. Wijzig bijvoorbeeld de naam ervan in een inschrijfsjabloon.

1. Navigeer naar de locatie /apps/mijnbedrijf/sjablonen/inschrijvingssjabloon.

1. Wijzig `jcr:title` en `jcr:description` eigenschappen voor `jcr:content` knoop om het malplaatje van het malplaatje te onderscheiden u kopieerde.

1. Het knooppunt `jcr:content` van de gewijzigde sjabloon bevat de componenten `guideContainer` en `guideformtitle`. `guideContainer` is de container die het adaptieve formulier bevat. De `guideformtitle` component toont de toepassingsnaam, beschrijving, etc.

   In plaats van `guideformtitle` kunt u een aangepaste component of de `parsys` component opnemen. Verwijder bijvoorbeeld `guideformtitle` en voeg een aangepaste component of het componentknooppunt `parsys` toe. Zorg ervoor dat de eigenschap `sling:resourceType` van de component verwijst naar de component en dat dit is gedefinieerd in het bestand `component.jsp` op de pagina.

1. Navigeer naar de locatie /apps/mijnbedrijf/sjablonen/inschrijving-sjabloon/jcr:content.

1. Open het tabblad **[!UICONTROL Properties]** en wijzig de waarde van de eigenschap `cq:designPath` in /etc/designs/mijnbedrijf.

1. Creëer nu een /etc/designs/mycompany knoop voor het `cq:Page` type.

## Een adaptieve formulierpaginacomponent {#create-an-adaptive-form-page-component} maken

De aangepaste sjabloon heeft dezelfde opmaak als de standaardsjabloon, omdat de sjabloon verwijst naar de paginacomponent /libs/fd/af/components/page/base. U kunt de componentenverwijzing vinden als bezit `sling:resourceType` die bij de knoop /apps/mijnbedrijf/malplaatjes/inschrijfment-malplaatje/jcr wordt bepaald:content. Omdat de basis een kernproductcomponent is, wijzigt u deze component niet.

1. Ga naar het knooppunt /apps/mijnbedrijf/sjablonen/inschrijving-sjabloon/jcr:content en wijzig de waarde van de eigenschap `sling:resourceType` in /apps/mijnbedrijf/componenten/pagina/inschrijfpagina
1. Kopieer het knooppunt /libs/fd/af/components/page/base naar de map /apps/mijnbedrijf/componenten/pagina.

1. Wijzig de naam van de gekopieerde component in `enrollmentpage`.

1. **(Alleen als u al een inhoudspagina hebt)** Voer de volgende stappen (a-d) uit als u een bestaande  `contentpage`component voor uw website hebt. Als u geen bestaande `contentpage`component voor uw website hebt, kunt u de `resourceSuperType`eigenschap laten verwijzen naar de OOTB-basispagina.

   1. Stel voor het knooppunt `enrollmentpage` de waarde van de eigenschap `sling:resourceSuperType` in op mijnbedrijf/componenten/pagina/contentPage. De component `contentpage` is de basispaginacomponent voor uw site. Andere paginacomponenten kunnen het uitbreiden. Verwijder manuscriptdossiers onder `enrollmentpage`, behalve `head.jsp`, `content.jsp`, en `library.jsp`. De `sling:resourceSuperType` component, die `contentpage` in dit geval is, omvat al dergelijke manuscripten. Kopteksten, inclusief navigatiebalk en voettekst, worden overgenomen van de component `contentpage`.

   1. Open het bestand `head.jsp`.

      Het JSP-bestand bevat de regel `<cq.include script="library.jsp"/>`.

      Het `library.jsp`-bestand bevat de `guide.theme.simpleEnrollment`-clientbibliotheek, die de opmaak voor het adaptieve formulier bevat.

      De paginacomponent `enrollmentpage` heeft een exclusief `head.jsp` dossier dat het `head.jsp` dossier van `contentpage` component met voeten treedt.

   1. Neem alle scripts in het `head.jsp`-bestand op voor de `contentpage`-component naar het `head.jsp`-bestand voor de `enrollmentpage`-component.
   1. In het `content.jsp`-script kunt u extra pagina-inhoud of verwijzingen toevoegen naar andere componenten die worden opgenomen wanneer een pagina wordt gerenderd. Als u bijvoorbeeld de aangepaste component `applicationformheader` toevoegt, moet u de volgende verwijzing naar de component in het JSP-bestand toevoegen:

      `<cq:include path="applicationformheader" resourceType="mycompany/components/applicationformheader"/>`

      Op dezelfde manier als u een `parsys` component in de structuur van de malplaatjeknoop toevoegt, omvat ook de douanecomponent.

## Een aangepaste formulierclientbibliotheek maken {#creating-an-adaptive-form-client-library}

Het `head.jsp`-bestand van de `enrollmentpage`-component voor de nieuwe sjabloon bevat een clientbibliotheek `guide.theme.simpleEnrollment`. De standaardsjabloon gebruikt deze clientbibliotheek ook. Wijzig de stijl in de nieuwe sjabloon op een van de volgende manieren:

* Definieer een aangepast thema en vervang het standaardthema `guide.theme.simpleEnrollment` door het aangepaste thema.
* Definieer een nieuwe clientbibliotheek onder /etc/designs/mijnbedrijf. Neem de clientbibliotheek op na het standaardthemaitem in de jsp-pagina. Neem alle overschreven stijlen en extra JavaScript-bestanden op in deze clientbibliotheek.

>[!NOTE]
>
>Thema verwijst naar een clientbibliotheek die is opgenomen in de paginacomponent die wordt gebruikt om een adaptief formulier te genereren. De clientbibliotheek is voornamelijk van toepassing op het uiterlijk van een adaptief formulier.

