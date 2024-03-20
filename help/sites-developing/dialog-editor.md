---
title: Dialoogeditor
description: De dialoogeditor biedt een grafische interface voor het eenvoudig maken en bewerken van dialoogvensters en subformulieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 57303608-c3e1-4201-8054-1a1798613e2c
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# Dialoogeditor{#dialog-editor}

De dialoogeditor biedt een grafische interface voor het eenvoudig maken en bewerken van dialoogvensters en subformulieren.

Ga naar CRXDE Lite en open de verkenner-boomstructuur om te zien hoe het werkt `/libs/foundation/components/chart` en dubbelklikken op het knooppunt `dialog`:

![chlimage_1-247](assets/chlimage_1-247.png)

Het dialoogvenster wordt geopend in het dialoogvenster **dialoogeditor**:

![screen_shot_2012-02-01at25033pm](assets/screen_shot_2012-02-01at25033pm.png)

## Overzicht van gebruikersinterface {#user-interface-overview}

De interface van de dialoogredacteur bestaat uit vier ruiten:

* De **palet** in de linkerbovenhoek. In dit deelvenster staan de widgets die beschikbaar zijn voor het samenstellen van een dialoogvenster, zoals tabdeelvensters, tekstvelden, selectielijsten en knoppen. U kunt de verschillende categorieën in het palet uitbreiden door op de gewenste scheidingsbalk te klikken.
* De **structuur** in de linkerbenedenhoek. In dit deelvenster ziet u de hiërarchische structuur van knooppunten die de dialoogdefinitie vormen. U kunt dezelfde structuur zien door het dialoogvenster uit te vouwen in CRXDE Lite of CRX Content Explorer.
* De **renderen** in het midden van het venster. In dit deelvenster ziet u hoe de dialoogdefinitie die in het structuurvenster is gedefinieerd, wordt weergegeven als een echt dialoogvenster.
* De **eigenschappen** venster. In dit deelvenster ziet u de eigenschappen van het knooppunt dat in het structuurvenster is gemarkeerd.

### De Dialoogeditor gebruiken {#using-the-dialog-editor}

Om een dialoogvenster te maken, sleept de gebruiker elementen van het palet naar het structuurvenster en zet deze neer op de positie in de hiërarchie van de dialoogdefinitie.

Nadat de gewenste structuur is voltooid, klikt de gebruiker op **Opslaan**, boven aan het rendervenster.

>[!CAUTION]
>
>De dialoogredacteur is voor het creëren van eenvoudige dialogen. Het is mogelijk dat het niet mogelijk is complexere dialoogdefinities te bewerken. Wanneer de dialoogeditor het bewerken van een dialoogstructuur niet toestaat, moet de dialoogdefinitie handmatig worden gemaakt of bewerkt, of beide. U doet dit door de nodestructuur direct uit te geven gebruikend de Ontdekkingsreiziger van de Inhoud van CRXDE Lite of CRX, bijvoorbeeld.

### Een nieuw dialoogvenster maken {#creating-a-new-dialog}

Als u een dialoogvenster wilt maken, selecteert u de gewenste component en klikt u op **Maken...** en vervolgens **Dialoogvenster maken...**.

Voer de vereiste gegevens in en klik op **Alles opslaan** - nu kunt u dubbelklikken op het dialoogvenster, zodat het wordt geopend met de editor.

### De Dialoogeditor voor subklassen gebruiken {#using-the-dialog-editor-for-scaffolds}

Een substraat is een speciale pagina met een formulier dat in één stap kan worden ingevuld en verzonden. Zo kunt u snel een pagina maken met de ingevoerde inhoud.

Het formulier waaruit een subformulier bestaat, wordt net als een normaal dialoogvenster gedefinieerd door een definitie in het dialoogvenster, hoewel het op de basispagina in een ander formulier wordt weergegeven. Omdat dialoogdefinities worden gebruikt om basisbeginselen te definiëren, kunnen basisbeginselen worden ontworpen met behulp van de dialoogeditor. Als u de dialoogvenster-editor op deze manier gebruikt, wordt in het rendervenster de definitie van het dialoogvenster nog steeds weergegeven in de vorm van een dialoogvenster en niet als een subvenster.

Zie [Basisstructuur](/help/sites-authoring/scaffolding.md) voor meer informatie over het gebruik van de dialoogeditor om subformulieren te maken.
