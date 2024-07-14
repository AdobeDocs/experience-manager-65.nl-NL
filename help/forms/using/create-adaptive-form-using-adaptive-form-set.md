---
title: Een adaptief formulier maken met behulp van een set adaptieve formulieren
description: Met AEM Forms kunt u adaptieve formulieren samenvoegen tot één groot adaptief formulier en de functies ervan begrijpen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: 4254c2cb-66cc-4a46-b447-bc5e32def7a0
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Een adaptief formulier maken met behulp van een set adaptieve formulieren{#create-an-adaptive-form-using-a-set-of-adaptive-forms}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

## Overzicht {#overview}

In een werkstroom, zoals een toepassing voor het openen van een bankrekening, vullen uw gebruikers meerdere formulieren in. In plaats van ze te vragen een set formulieren in te vullen, kunt u de formulieren stapelen en een groot formulier (bovenliggend formulier) samenstellen. Wanneer u een adaptief formulier toevoegt aan het grotere formulier, wordt dit toegevoegd als een deelvenster (onderliggend formulier). U voegt een set onderliggende formulieren toe om een bovenliggend formulier te maken. U kunt deelvensters weergeven of verbergen op basis van de gebruikersinvoer. Met de knoppen van het bovenliggende formulier, zoals Verzenden en opnieuw instellen, overschrijft u de knoppen van het onderliggende formulier. Als u een adaptief formulier wilt toevoegen aan het bovenliggende formulier, kunt u het adaptieve formulier slepen en neerzetten vanuit de elementenbrowser (zoals adaptieve formulierfragmenten).

Beschikbare functies zijn:

* Onafhankelijk ontwerpen
* Aangepaste formulieren weergeven/verbergen
* Lazy loading

Functies zoals onafhankelijk schrijven en laden zorgen voor betere prestaties dan het gebruik van afzonderlijke componenten om het bovenliggende formulier te maken.

>[!NOTE]
>
>U kunt op XFA gebaseerde adaptieve formulieren/fragmenten niet gebruiken als onderliggende of bovenliggende formulieren.

## Achter de schermen {#behind-the-scenes}

U kunt op XSD gebaseerde adaptieve formulieren en fragmenten toevoegen in het bovenliggende formulier. De structuur van de oudervorm is het zelfde als [ om het even welke adaptieve vorm ](../../forms/using/prepopulate-adaptive-form-fields.md). Wanneer u een adaptief formulier toevoegt als een onderliggend formulier, wordt het als een deelvenster toegevoegd in het bovenliggende formulier. Gegevens van een gebonden onderliggend formulier worden opgeslagen onder de `data` -basis van de `afBoundData` -sectie van het XML-schema van het bovenliggende formulier.

Uw klanten vullen bijvoorbeeld een toepassingsformulier in. De eerste twee velden van het formulier zijn naam en identiteit. De XML is:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
        </data>
    </afBoundData>
</afData>
```

U voegt een ander formulier in de toepassing toe waarmee uw klanten hun kantooradres kunnen invullen. De hoofdmap van het schema van het onderliggende formulier is `officeAddress` . Pas `bindref` `/application/officeAddress` of `/officeAddress` toe. Als `bindref` niet wordt verstrekt, wordt de kindvorm toegevoegd als `officeAddress` subtree. Zie de XML van het onderstaande formulier:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <officeAddress>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </officeAddress>
        </data>
    </afBoundData>
</afData>
```

Als u een andere vorm opneemt die uw klanten huisadres laat verstrekken, pas `bindref` `/application/houseAddress or /houseAddress.` toe XML kijkt als:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <officeAddress>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </officeAddress>
            <houseAddress>
                <addressLine>2, Geometrixx City</addressLine>
                <zip>11111</zip>
            </houseAddress>
        </data>
    </afBoundData>
</afData>
```

Als u de zelfde subwortelnaam zoals de schemawortel wilt houden ( `Address` in dit voorbeeld), gebruik geïndexeerde bindrefs.

Pas bijvoorbeeld bindrefs `/application/address[1]` of `/address[1]` en `/application/address[2]` of `/address[2]` toe. De XML van het formulier is:

```xml
<afData>
    <afUnboundData>
        <data />
    </afUnboundData>
    <afBoundData>
        <data xmlns:xfa="https://www.xfa.org/schema/xfa-data/1.0/">
            <applicantName>Sarah Rose</applicantName>
            <applicantId>1234</applicantId>
            <address>
                <addressLine>1, Geometrixx City</addressLine>
                <zip>11111</zip>
            </address>
            <address>
                <addressLine>2, Geometrixx City</addressLine>
                <zip>11111</zip>
            </address>
        </data>
    </afBoundData>
</afData>
```

U kunt de standaardsubstructuur van het adaptieve formulier/fragment wijzigen met de eigenschap `bindRef` . Met de eigenschap `bindRef` kunt u het pad opgeven dat naar een locatie in de boomstructuur van het XML-schema wijst.

Als het onderliggende formulier niet gebonden is, worden de gegevens ervan opgeslagen onder de `data` -basis van de `afUnboundData` -sectie van het XML-schema van het bovenliggende formulier.

U kunt een adaptief formulier meerdere keren als een onderliggend formulier toevoegen. Zorg ervoor dat de eigenschap `bindRef` op de juiste wijze is gewijzigd, zodat elk gebruikt exemplaar van het adaptieve formulier naar een andere subhoofdmap onder de hoofdmap van de gegevens wijst.

>[!NOTE]
>
>Als verschillende formulieren/fragmenten zijn toegewezen aan dezelfde subhoofdmap, worden de gegevens overschreven.

## Een adaptief formulier toevoegen als een onderliggend formulier met de middelenbrowser {#adding-an-adaptive-form-as-a-child-form-using-asset-browser}

Voer de volgende stappen uit om een adaptief formulier toe te voegen als een onderliggend formulier met behulp van de middelenbrowser.

1. Open het bovenliggende formulier in de bewerkingsmodus.
1. In sidebar, klik **Assets** ![ activa-browser ](assets/assets-browser.png). Onder Assets, uitgezochte **Aangepaste Vorm** van drop-down.
   [![ Selecterend adaptieve vorm onder Assets ](assets/asset.png)](assets/asset-1.png)

1. Sleep het adaptieve formulier dat u wilt toevoegen als een onderliggend formulier.
   [![ belemmering-daling de adaptieve vorm in uw plaats ](assets/drag-drop.png)](assets/drag-drop-1.png) de adaptieve vorm u neerzet wordt toegevoegd als kindvorm.
