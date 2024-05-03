---
title: Een adaptief formulier maken met behulp van een set adaptieve formulieren
description: Met AEM Forms kunt u adaptieve formulieren samenvoegen tot één groot adaptief formulier en de functies ervan begrijpen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: 4254c2cb-66cc-4a46-b447-bc5e32def7a0
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '620'
ht-degree: 0%

---

# Een adaptief formulier maken met behulp van een set adaptieve formulieren{#create-an-adaptive-form-using-a-set-of-adaptive-forms}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

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

U kunt op XSD gebaseerde adaptieve formulieren en fragmenten toevoegen in het bovenliggende formulier. De structuur van het bovenliggende formulier is gelijk aan [elk adaptief formulier](../../forms/using/prepopulate-adaptive-form-fields.md). Wanneer u een adaptief formulier toevoegt als een onderliggend formulier, wordt het als een deelvenster toegevoegd in het bovenliggende formulier. De gegevens van een gebonden onderliggend formulier worden opgeslagen onder de `data`basis van de `afBoundData` van het XML-schema van het bovenliggende formulier.

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

U voegt een ander formulier in de toepassing toe waarmee uw klanten hun kantooradres kunnen invullen. De hoofdmap van het schema van het onderliggende formulier is `officeAddress`. Toepassen `bindref` `/application/officeAddress` of `/officeAddress`. Indien `bindref`niet wordt opgegeven, wordt het onderliggende formulier toegevoegd als de `officeAddress` substructuur. Zie de XML van het onderstaande formulier:

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

Als u een ander formulier invoegt waarmee uw klanten huisadres kunnen opgeven, kunt u het volgende doen: `bindref` `/application/houseAddress or /houseAddress.`De XML ziet er als volgt uit:

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

Als u dezelfde subhoofdnaam wilt behouden als de hoofdmap van het schema ( `Address`in dit voorbeeld), gebruik geïndexeerde bindrefs.

Bijvoorbeeld bindrefs toepassen `/application/address[1]` of `/address[1]` en `/application/address[2]` of `/address[2]`. De XML van het formulier is:

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

U kunt de standaardsubstructuur van het adaptieve formulier/fragment wijzigen met de opdracht `bindRef` eigenschap. De `bindRef` Met deze eigenschap kunt u het pad opgeven dat naar een locatie in de boomstructuur van het XML-schema wijst.

Als het onderliggende formulier niet gebonden is, worden de gegevens ervan opgeslagen onder de `data`basis van de `afUnboundData` van het XML-schema van het bovenliggende formulier.

U kunt een adaptief formulier meerdere keren als een onderliggend formulier toevoegen. Zorg ervoor dat de `bindRef` wordt correct gewijzigd, zodat elk gebruikt exemplaar van het adaptieve formulier naar een verschillende subhoofdmap onder de gegevensbasis wijst.

>[!NOTE]
>
>Als verschillende formulieren/fragmenten zijn toegewezen aan dezelfde subhoofdmap, worden de gegevens overschreven.

## Een adaptief formulier toevoegen als een onderliggend formulier met de middelenbrowser {#adding-an-adaptive-form-as-a-child-form-using-asset-browser}

Voer de volgende stappen uit om een adaptief formulier toe te voegen als een onderliggend formulier met behulp van de middelenbrowser.

1. Open het bovenliggende formulier in de bewerkingsmodus.
1. Klik in de zijbalk op **Activa** ![assets-browser](assets/assets-browser.png). Selecteer onder Elementen de optie **Adaptief formulier** in de vervolgkeuzelijst.
   [![Aangepast formulier selecteren onder Activa](assets/asset.png)](assets/asset-1.png)

1. Sleep het adaptieve formulier dat u wilt toevoegen als een onderliggend formulier.
   [![Sleep het adaptieve formulier naar uw site](assets/drag-drop.png)](assets/drag-drop-1.png)Het aangepaste formulier dat u neerzet, wordt toegevoegd als een onderliggend formulier.
