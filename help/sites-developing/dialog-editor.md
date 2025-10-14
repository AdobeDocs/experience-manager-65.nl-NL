---
title: Dialoogeditor
description: De dialoogeditor biedt een grafische interface voor het eenvoudig maken en bewerken van dialoogvensters en subformulieren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
exl-id: 57303608-c3e1-4201-8054-1a1798613e2c
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 305227eff3c0d6414a5ae74bcf3a74309dccdd13
workflow-type: tm+mt
source-wordcount: '474'
ht-degree: 0%

---

# Dialoogeditor{#dialog-editor}

De dialoogeditor biedt een grafische interface voor het eenvoudig maken en bewerken van dialoogvensters en subformulieren.

Ga naar CRXDE Lite om te zien hoe het werkt door de verkenner-boomstructuur `/libs/foundation/components/chart` te openen en te dubbelklikken op het knooppunt `dialog` :

![&#x200B; chlimage_1-247 &#x200B;](assets/chlimage_1-247.png)

De dialoogknoop opent in de **dialoogredacteur**:

![&#x200B; screen_shot_2012-02-01at25033pm &#x200B;](assets/screen_shot_2012-02-01at25033pm.png)

## Overzicht van gebruikersinterface {#user-interface-overview}

De interface van de dialoogredacteur bestaat uit vier ruiten:

* Het **palet**, in de upper-left hoek. In dit deelvenster staan de widgets die beschikbaar zijn voor het samenstellen van een dialoogvenster, zoals tabdeelvensters, tekstvelden, selectielijsten en knoppen. U kunt de verschillende categorieën in het palet uitbreiden door op de gewenste scheidingsbalk te klikken.
* De **structuur** ruit, in de laag-linkerhoek. In dit deelvenster ziet u de hiërarchische structuur van knooppunten die de dialoogdefinitie vormen. U kunt dezelfde structuur zien door het dialoogvenster uit te vouwen in CRXDE Lite of CRX Content Explorer.
* **geef** ruit terug, in het centrum van het venster. In dit deelvenster ziet u hoe de dialoogdefinitie die in het structuurvenster is gedefinieerd, wordt weergegeven als een echt dialoogvenster.
* De **eigenschappen** ruit. In dit deelvenster ziet u de eigenschappen van het knooppunt dat in het structuurvenster is gemarkeerd.

### De Dialoogeditor gebruiken {#using-the-dialog-editor}

Om een dialoogvenster te maken, sleept de gebruiker elementen van het palet naar het structuurvenster en zet deze neer op de positie in de hiërarchie van de dialoogdefinitie.

Zodra de gewenste structuur wordt voltooid, klikt de gebruiker **sparen**, bij de bovenkant van teruggeeft ruit.

>[!CAUTION]
>
>De dialoogredacteur is voor het creëren van eenvoudige dialogen. Het is mogelijk dat het niet mogelijk is complexere dialoogdefinities te bewerken. Wanneer de dialoogeditor het bewerken van een dialoogstructuur niet toestaat, moet de dialoogdefinitie handmatig worden gemaakt of bewerkt, of beide. U doet dit door de knoopstructuur rechtstreeks te bewerken met bijvoorbeeld CRXDE Lite of CRX Content Explorer.

### Een nieuw dialoogvenster maken {#creating-a-new-dialog}

Om een dialoogdoos tot stand te brengen, selecteer de vereiste component, klik **creëren..** en dan **creëren Dialoog...**.

Ga de vereiste details in dan klik **sparen allen** - nu kunt u de dialoog tweemaal klikken zodat opent het met de redacteur.

### De Dialoogeditor voor subklassen gebruiken {#using-the-dialog-editor-for-scaffolds}

Een substraat is een speciale pagina met een formulier dat in één stap kan worden ingevuld en verzonden. Zo kunt u snel een pagina maken met de ingevoerde inhoud.

Het formulier waaruit een subformulier bestaat, wordt net als een normaal dialoogvenster gedefinieerd door een definitie in het dialoogvenster, hoewel het op de basispagina in een ander formulier wordt weergegeven. Omdat dialoogdefinities worden gebruikt om basisbeginselen te definiëren, kunnen basisbeginselen worden ontworpen met behulp van de dialoogeditor. Als u de dialoogvenster-editor op deze manier gebruikt, wordt in het rendervenster de definitie van het dialoogvenster nog steeds weergegeven in de vorm van een dialoogvenster en niet als een subvenster.

Zie [&#x200B; Basisstructuur &#x200B;](/help/sites-authoring/scaffolding.md) voor meer informatie bij het gebruiken van de dialoogredacteur om scaffilles tot stand te brengen.
