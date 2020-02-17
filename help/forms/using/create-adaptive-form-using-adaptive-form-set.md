---
title: Een adaptief formulier maken met behulp van een set adaptieve formulieren
seo-title: Een adaptief formulier maken met behulp van een set adaptieve formulieren
description: 'Met AEM Forms combineert u adaptieve formulieren tot één groot adaptief formulier en begrijpt u de functies ervan. '
seo-description: 'Met AEM Forms combineert u adaptieve formulieren tot één groot adaptief formulier en begrijpt u de functies ervan. '
uuid: e52e4f90-8821-49ec-89ff-fbf07db69bd2
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 264aa8c0-ba64-4768-b3d1-1b9baa6b4d72
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65

---


# Een adaptief formulier maken met behulp van een set adaptieve formulieren{#create-an-adaptive-form-using-a-set-of-adaptive-forms}

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

U kunt op XSD gebaseerde adaptieve formulieren en fragmenten toevoegen in het bovenliggende formulier. De structuur van het bovenliggende formulier is gelijk aan die van [elk adaptief formulier](../../forms/using/prepopulate-adaptive-form-fields.md). Wanneer u een adaptief formulier toevoegt als een onderliggend formulier, wordt het als een deelvenster toegevoegd in het bovenliggende formulier. De gegevens van een gebonden onderliggend formulier worden opgeslagen onder de `data`basis van de `afBoundData` sectie van het XML-schema van het bovenliggende formulier.

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

U voegt een ander formulier in de toepassing toe waarmee uw klanten hun kantooradres kunnen invullen. De hoofdmap van het schema van het onderliggende formulier is `officeAddress`. Toepassen `bindref` of `/application/officeAddress` `/officeAddress`. Als dit niet `bindref`het geval is, wordt het onderliggende formulier toegevoegd als de `officeAddress` substructuur. Zie de XML van het onderstaande formulier:

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

Als u een ander formulier invoegt waarmee uw klanten huisadres kunnen opgeven, past u `bindref` `/application/houseAddress or /houseAddress.`de XML-code als volgt toe:

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

Als u de zelfde subwortelnaam zoals de schemaroot ( `Address`in dit voorbeeld) wilt houden, gebruik geïndexeerde bindrefs.

U kunt bijvoorbeeld bindrefs toepassen `/application/address[1]` of `/address[1]` en `/application/address[2]` of `/address[2]`. De XML van het formulier is:

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

U kunt de standaardsubstructuur van het adaptieve formulier/fragment wijzigen met de `bindRef` eigenschap. Met de `bindRef` eigenschap kunt u het pad opgeven dat naar een locatie in de boomstructuur van het XML-schema wijst.

Als het onderliggende formulier niet gebonden is, worden de gegevens ervan opgeslagen onder de `data`basis van het `afUnboundData` gedeelte van het XML-schema van het bovenliggende formulier.

U kunt een adaptief formulier meerdere keren als een onderliggend formulier toevoegen. Zorg ervoor dat het formulier op de juiste wijze `bindRef` wordt gewijzigd, zodat elk gebruikt exemplaar van het adaptieve formulier naar een andere subhoofdmap onder de hoofdmap van het bestand wijst.

>[!NOTE]
>
>Als verschillende formulieren/fragmenten zijn toegewezen aan dezelfde subhoofdmap, worden de gegevens overschreven.

## Een adaptief formulier toevoegen als een onderliggend formulier met de middelenbrowser {#adding-an-adaptive-form-as-a-child-form-using-asset-browser}

Voer de volgende stappen uit om een adaptief formulier toe te voegen als een onderliggend formulier met behulp van de middelenbrowser.

1. Open het bovenliggende formulier in de bewerkingsmodus.
1. Klik in de zijbalk op **Middelen** - ![middelen-browser](assets/assets-browser.png). Selecteer onder Elementen de optie **Adaptief formulier** in de vervolgkeuzelijst.
   [ Aanpassingsformulier ![selecteren onder Activa](assets/asset.png)](assets/asset-1.png)

1. Sleep het adaptieve formulier dat u wilt toevoegen als een onderliggend formulier.
   [ Sleep het adaptieve formulier ![naar uw](assets/drag-drop.png)](assets/drag-drop-1.png)site en zet het neer. Het adaptieve formulier dat u neerzet, wordt toegevoegd als een onderliggend formulier.

