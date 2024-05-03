---
title: Verbeter de prestaties van grote formulieren met het laden van de formulieren
description: Lazy loading verbetert de prestaties van grote en complexe adaptieve formulieren aanzienlijk door de initialisatie en het laden van formulierfragmenten uit te stellen totdat deze zichtbaar zijn.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms, Foundation Components
exl-id: f7e3e2cd-0cbe-4b26-9e55-7afc6dc3af63
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: f6771bd1338a4e27a48c3efd39efe18e57cb98f9
workflow-type: tm+mt
source-wordcount: '1060'
ht-degree: 0%

---

# Verbeter de prestaties van grote formulieren met het laden van de formulieren{#improve-performance-of-large-forms-with-lazy-loading}

<span class="preview"> Adobe beveelt aan moderne en uitbreidbare gegevensvastlegging te gebruiken [Kernonderdelen](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) for [nieuwe Adaptieve Forms maken](/help/forms/using/create-an-adaptive-form-core-components.md) of [Aangepaste Forms toevoegen aan AEM Sites-pagina&#39;s](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/create-an-adaptive-form-on-forms-cs/lazy-loading-adaptive-forms.html) |
| AEM 6,5 | Dit artikel |

## Inleiding tot wazig laden {#introduction-to-lazy-loading}

Wanneer het formulier groot en complex wordt met honderden en duizenden velden, ervaren eindgebruikers een lange responstijd bij het weergeven van formulieren tijdens runtime. Om de reactietijd te minimaliseren, laat de adaptieve vormen u vormen in logische fragmenten breken en vormen om initialisering of lading van fragmenten uit te stellen tot het fragment zichtbaar moet zijn. Het wordt genoemd lazy ladend. Bovendien worden de fragmenten die zijn geconfigureerd voor wazig laden verwijderd wanneer de gebruiker naar andere secties in het formulier navigeert en de fragmenten niet meer zichtbaar zijn.

Laten we eerst de vereisten en voorbereidende stappen begrijpen voordat u lazy laden configureert.

## Voorbereiden op het configureren van wazig laden {#preparing-to-configure-lazy-loading}

Voordat u het laden van fragmenten in het aangepaste formulier kunt configureren, is het belangrijk dat u strategieën definieert voor het maken van fragmenten, waarden identificeert die in scripts worden gebruikt of die in andere fragmenten worden doorverwezen, en regels definieert voor het beheren van de zichtbaarheid van velden in laaggeladen fragmenten.

* **Fragmenten identificeren en maken**
U kunt alleen adaptieve formulierfragmenten configureren voor wazig laden. Een fragment is een zelfstandig segment dat zich buiten een adaptief formulier bevindt en dat in verschillende formulieren opnieuw kan worden gebruikt. De eerste stap bij het implementeren van lui laden is het identificeren van logische secties in een formulier en het omzetten ervan in fragmenten. U kunt een geheel nieuw fragment maken of een bestaand formulierdeelvenster opslaan als fragment.

  Zie voor meer informatie over het maken van fragmenten [Adaptieve formulierfragmenten](../../forms/using/adaptive-form-fragments.md).

* **Algemene waarden identificeren en markeren**
Bij op Forms gebaseerde transacties worden dynamische elementen gebruikt om relevante gegevens van gebruikers vast te leggen en te verwerken om het invullen van formulieren te vereenvoudigen. Het formulier heeft bijvoorbeeld veld A in fragment X, waarvan de waarde de geldigheid van veld B in een ander fragment bepaalt. In dit geval moet, als fragment X is gemarkeerd voor lui laden, de waarde van veld A beschikbaar zijn om veld B te valideren, zelfs als fragment X niet is geladen. Hiertoe kunt u veld A markeren als globaal, zodat de waarde ervan beschikbaar is voor het valideren van veld B wanneer fragment X niet is geladen.

  Voor informatie over hoe u een veldwaarde globaal kunt maken, raadpleegt u [Lazy laden configureren](../../forms/using/lazy-loading-adaptive-forms.md#p-configuring-lazy-loading-p).

* **Regels schrijven om de zichtbaarheid van velden te bepalen**
Forms bevat enkele velden en secties die niet van toepassing zijn op alle gebruikers en onder alle omstandigheden. Forms-auteurs en -ontwikkelaars gebruiken zichtbaarheids- of show-hide-regels om hun zichtbaarheid te bepalen op basis van gebruikersinvoer. Bijvoorbeeld, wordt het gebied van het Adres van het Bureau niet getoond aan de gebruikers die op het gebied van de Status van de Werkgelegenheid in een vorm werkloos kiezen. Voor meer informatie over het schrijven van regels, zie [Regeleditor gebruiken](../../forms/using/rule-editor.md).

  U kunt zichtbaarheidsregels gebruiken in de laaggeladen fragmenten, zodat voorwaardelijke velden alleen worden weergegeven wanneer ze vereist zijn. Markeer ook het voorwaardelijke veld globaal om ernaar te verwijzen in de zichtbaarheidsexpressie van het langzaam geladen fragment.

## Lazy laden configureren {#configuring-lazy-loading}

Voer de volgende stappen uit om het laden van een adaptief formulierfragment in te schakelen:

1. Open het adaptieve formulier in de ontwerpmodus dat het fragment bevat dat u wilt inschakelen voor wazig laden.
1. Selecteer het adaptieve formulierfragment en selecteer ![cmppr](assets/cmppr.png).
1. Schakel in de zijbalk de optie **[!UICONTROL Load fragment lazily]** en selecteert u **Gereed**.

   ![Lazy loading inschakelen voor het adaptieve formulierfragment](assets/lazy-loading-fragment.png)

   Het fragment is nu ingeschakeld voor wazig laden.

U kunt de waarden van objecten in het laaggeladen fragment als globaal markeren, zodat deze beschikbaar zijn voor gebruik in scripts wanneer het bevattende fragment niet is geladen. Ga als volgt te werk:

1. Open het adaptieve formulierfragment in de ontwerpmodus.
1. Selecteer het veld waarvan u de waarde als globaal wilt markeren en selecteer vervolgens ![cmppr](assets/cmppr.png).
1. Schakel in de zijbalk de optie **Waarde gebruiken tijdens laden van item**.

   ![Lazy loading field in sidebar](assets/enable-lazy-loading.png)

   De waarde wordt nu gemarkeerd als globaal en is beschikbaar voor gebruik in scripts, zelfs wanneer het omvattende fragment wordt verwijderd.

## Overwegingen en aanbevolen procedures voor het configureren van lazy laden {#considerations-and-best-practices-for-configuring-lazy-loading}

Enkele beperkingen, aanbevelingen en belangrijke punten waarmee u rekening moet houden bij het werken met lazy laden zijn:

* Gebruik op XSD-schema gebaseerde adaptieve formulieren via op XFA gebaseerde adaptieve formulieren voor het configureren van lazy loading op grote formulieren. De prestatiewinst als gevolg van de lazy loading-implementatie in op XFA gebaseerde adaptieve formulieren is relatief minder dan de toename in op XSD gebaseerde adaptieve formulieren.
* Het laden van fragmenten in een adaptieve vorm die gebruikmaken van **[!UICONTROL Responsive -everything on one page without navigation]** layout voor het hoofddeelvenster. Als gevolg van de responsieve layoutconfiguratie worden alle fragmenten tegelijkertijd in een adaptieve vorm geladen. Het kan ook leiden tot verminderde prestaties.
* Het wordt aanbevolen om het laden van het eerste fragment niet in een adaptieve vorm te configureren.
* Het wordt aanbevolen het laden van fragmenten in het eerste deelvenster dat wordt weergegeven bij het laden van het adaptieve formulier, niet te configureren.
* Lazy loading wordt ondersteund tot twee niveaus in de fragmenthiërarchie.
* Zorg ervoor dat velden die zijn gemarkeerd als globaal, uniek zijn in een adaptief formulier.
* U kunt zichtbaarheidsregels schrijven voor fragmenten die op basis van een voorwaarde moeten worden weergegeven of verborgen. U kunt bijvoorbeeld het fragment Gegevens echtgenoot weergeven of verbergen op basis van de staat van het huwelijk die een gebruiker heeft opgegeven.
* Componenten voor bestandsbijlagen en Algemene voorwaarden worden niet ondersteund in laaggeladen fragmenten.

### Aanbevolen procedures voor het schrijven van scripts voor het configureren van lazy loading {#scripting-best-practices-for-configuring-lazy-loading}

Belangrijke aandachtspunten bij het ontwikkelen van scripts voor luie laadvensters zijn:

* Zorg ervoor dat de initialisatie en de berekening van manuscripten die op de gebieden van een lui geladen fragment worden gebruikt in de aard van de epidemie zijn. Onbetrouwbare scripts zijn scripts die hetzelfde effect hebben, zelfs na meerdere uitvoeringen.
* Met de algemeen beschikbare eigenschap van velden kunt u de waarde van velden in een wazig venster voor het laden beschikbaar maken voor alle andere deelvensters van een formulier.
* Verwijs geen verwijzingswaarde van een gebied binnen een lui paneel ongeacht gebied door zich globaal over fragmenten wordt duidelijk of niet.
* Met de functie voor het opnieuw instellen van deelvensters kunt u alle zichtbare elementen in het deelvenster opnieuw instellen met de volgende klikexpressie.\
  guideBridge.resolveNode(guideBridge.getFocus({&quot;focusOption&quot;: &quot;navigablePanel&quot;})).resetData()
