---
title: Dialoogvenster-editor
seo-title: Dialog Editor
description: De dialoogvenster-editor biedt een grafische interface voor het eenvoudig maken en bewerken van dialoogvensters en subformulieren
seo-description: The dialog editor provides a graphical interface for easily creating and editing dialog boxes and scaffolds
uuid: 64d3fb12-8638-441b-8595-c590d48f3072
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: b7ac457d-3689-4f5d-9ceb-ff6a9944e7eb
exl-id: 57303608-c3e1-4201-8054-1a1798613e2c
source-git-commit: b220adf6fa3e9faf94389b9a9416b7fca2f89d9d
workflow-type: tm+mt
source-wordcount: '491'
ht-degree: 0%

---

# Dialoogvenster-editor{#dialog-editor}

De dialoogeditor biedt een grafische interface voor het eenvoudig maken en bewerken van dialoogvensters en subformulieren.

Ga naar CRXDE Lite en open de verkenner-boomstructuur om te zien hoe het werkt `/libs/foundation/components/chart` en dubbelklik op het knooppunt `dialog`:

![chlimage_1-247](assets/chlimage_1-247.png)

Het dialoogvenster wordt geopend in het dialoogvenster **dialoogeditor**:

![screen_shot_2012-02-01at25033pm](assets/screen_shot_2012-02-01at25033pm.png)

## Overzicht van gebruikersinterface {#user-interface-overview}

De interface van de dialoogeditor bestaat uit vier deelvensters:

* De **palet** in de linkerbovenhoek. In dit deelvenster staan de widgets die beschikbaar zijn voor het samenstellen van een dialoogvenster, zoals tabdeelvensters, tekstvelden, selectielijsten en knoppen. U kunt de verschillende categorieën in het palet uitbreiden door op de gewenste scheidingsbalk te klikken.
* De **structuur** in de linkerbenedenhoek. In dit deelvenster ziet u de hiërarchische structuur van knooppunten die de dialoogdefinitie vormen. U kunt dezelfde structuur zien door het dialoogvenster uit te vouwen in CRXDE Lite of CRX Content Explorer.
* De **renderen** in het midden van het venster. In dit deelvenster ziet u hoe de in het structuurvenster gedefinieerde dialoogdefinitie wordt weergegeven als een echt dialoogvenster.
* De **eigenschappen** venster. In dit deelvenster worden de eigenschappen weergegeven van het knooppunt dat momenteel is gemarkeerd in het structuurvenster.

### De Dialoogeditor gebruiken {#using-the-dialog-editor}

Om een dialoogvenster te maken, sleept de gebruiker elementen van het palet naar het structuurvenster en zet deze neer op de positie in de hiërarchie van de dialoogdefinitie.

Nadat de gewenste structuur is voltooid, klikt de gebruiker op **Opslaan**, boven aan het rendervenster.

>[!CAUTION]
>
>De dialoogeditor is bedoeld voor het maken van relatief eenvoudige dialoogvensters en kan wellicht geen complexere dialoogdefinities bewerken. Wanneer de dialoogeditor het bewerken van een dialoogstructuur niet toestaat, moet de dialoogdefinitie handmatig worden gemaakt en/of bewerkt door de knooppuntstructuur rechtstreeks te bewerken met bijvoorbeeld CRXDE Lite of CRX Content Explorer.

### Een nieuw dialoogvenster maken {#creating-a-new-dialog}

Als u een nieuw dialoogvenster wilt maken, selecteert u de gewenste component en klikt u op **Maken...** en vervolgens **Dialoogvenster maken...**.

Voer de vereiste gegevens in en klik op **Alles opslaan** - nu kunt u dubbelklikken op het dialoogvenster om het te openen met de editor.

### De Dialoogeditor voor subklassen gebruiken {#using-the-dialog-editor-for-scaffolds}

Een substraat is een speciale pagina met een formulier dat in één stap kan worden ingevuld en verzonden. Zo kunt u snel een pagina maken met de ingevoerde inhoud.

Het formulier waaruit een subformulier bestaat, wordt net als een normaal dialoogvenster gedefinieerd door een definitie in het dialoogvenster, hoewel het op de basispagina in een ander formulier wordt weergegeven. Omdat dialoogdefinities worden gebruikt om basisbeginselen te definiëren, kunnen basisbeginselen worden ontworpen met de dialoogeditor. Let op: wanneer u de dialoogeditor op deze manier gebruikt, wordt de definitie van het dialoogvenster in het rendervenster nog steeds weergegeven in de vorm van een dialoogvenster en niet als een subvenster.

Zie [Basisstructuur](/help/sites-authoring/scaffolding.md) voor meer informatie over het gebruik van de dialoogeditor om subformulieren te maken.
