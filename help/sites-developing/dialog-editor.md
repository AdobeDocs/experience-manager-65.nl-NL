---
title: Dialoogvenster-editor
seo-title: Dialoogvenster-editor
description: De dialoogvenster-editor biedt een grafische interface voor het eenvoudig maken en bewerken van dialoogvensters en subformulieren
seo-description: De dialoogvenster-editor biedt een grafische interface voor het eenvoudig maken en bewerken van dialoogvensters en subformulieren
uuid: 64d3fb12-8638-441b-8595-c590d48f3072
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
discoiquuid: b7ac457d-3689-4f5d-9ceb-ff6a9944e7eb
translation-type: tm+mt
source-git-commit: 58fa0f05bae7ab5ba51491be3171b5c6ffbe870d

---


# Dialoogvenster-editor{#dialog-editor}

De dialoogeditor biedt een grafische interface voor het eenvoudig maken en bewerken van dialoogvensters en subformulieren.

Als u wilt zien hoe het werkt, gaat u naar CRXDE Lite en opent u de verkenner-structuur `/libs/foundation/components/chart` en dubbelklikt u op het knooppunt `dialog`:

![chlimage_1-247](assets/chlimage_1-247.png)

Het dialoogvenster wordt geopend in de **dialoogeditor**:

![screen_shot_2012-02-01at25033pm](assets/screen_shot_2012-02-01at25033pm.png)

## Overzicht van gebruikersinterface {#user-interface-overview}

De interface van de dialoogeditor bestaat uit vier deelvensters:

* Het **palet** in de linkerbovenhoek. In dit deelvenster staan de widgets die beschikbaar zijn voor het samenstellen van een dialoogvenster, zoals tabdeelvensters, tekstvelden, selectielijsten en knoppen. U kunt de verschillende categorieën in het palet uitbreiden door op de gewenste scheidingsbalk te klikken.
* Het deelvenster **Structuur** , linksonder. In dit deelvenster ziet u de hiërarchische structuur van knooppunten die de dialoogdefinitie vormen. U kunt dezelfde structuur zien door het dialoogvenster uit te vouwen in CRXDE Lite of CRX Content Explorer.
* Het **rendervenster** in het midden van het venster. In dit deelvenster ziet u hoe de in het structuurvenster gedefinieerde dialoogdefinitie wordt weergegeven als een echt dialoogvenster.
* Het deelvenster **Eigenschappen** . In dit deelvenster worden de eigenschappen weergegeven van het knooppunt dat momenteel is gemarkeerd in het structuurvenster.

### De Dialoogeditor gebruiken {#using-the-dialog-editor}

Om een dialoogvenster te maken, sleept de gebruiker elementen van het palet naar het structuurvenster en zet deze neer op de positie in de hiërarchie van de dialoogdefinitie.

Zodra de gewenste structuur is voltooid, klikt de gebruiker op **Opslaan** boven aan het rendervenster.

>[!CAUTION]
>
>De dialoogeditor is bedoeld voor het maken van relatief eenvoudige dialoogvensters en kan wellicht geen complexere dialoogdefinities bewerken. In gevallen waarin de dialoogeditor het bewerken van een dialoogstructuur niet toestaat, moet de dialoogdefinitie handmatig worden gemaakt en/of bewerkt door de knooppuntstructuur rechtstreeks te bewerken met bijvoorbeeld CRXDE Lite of CRX Content Explorer.

### Een nieuw dialoogvenster maken {#creating-a-new-dialog}

**** Klik op **Maken om een nieuw dialoogvenster te maken dat u nodig hebt om de vereiste component te selecteren... en vervolgens Dialoogvenster** maken... .

Voer de vereiste gegevens in en klik op Alles **** opslaan. U kunt nu dubbelklikken in het dialoogvenster om het dialoogvenster te openen met de editor.

### De Dialoogeditor voor subklassen gebruiken {#using-the-dialog-editor-for-scaffolds}

Een substraat is een speciale pagina met een formulier dat in één stap kan worden ingevuld en verzonden. Zo kunt u snel een pagina maken met de ingevoerde inhoud.

Het formulier waaruit een subformulier bestaat, wordt net als een normaal dialoogvenster gedefinieerd door een definitie in het dialoogvenster, hoewel het op de basispagina in een ander formulier wordt weergegeven. Omdat dialoogdefinities worden gebruikt om basisbeginselen te definiëren, kunnen basisbeginselen worden ontworpen met de dialoogeditor. Let op: wanneer u de dialoogeditor op deze manier gebruikt, wordt de definitie van het dialoogvenster in het rendervenster nog steeds weergegeven in de vorm van een dialoogvenster en niet als een subvenster.

Zie [Basisstructuur](/help/sites-authoring/scaffolding.md) voor meer informatie over het gebruik van de dialoogeditor om subformulieren te maken.
