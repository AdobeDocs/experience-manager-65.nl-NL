---
title: Adaptieve Forms synchroniseren met XFA-formuliersjablonen
description: Leer hoe u formulieren synchroniseert met XFA/XDP-bestanden. Hiermee worden formuliervelden opnieuw gebruikt die zijn gesynchroniseerd met wijzigingen die zijn aangebracht in de overeenkomende velden in de XFA/XDP-bestanden.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
docset: aem65
feature: Adaptive Forms,Foundation Components
exl-id: fed67c23-a9b7-403e-9199-dfd527d5f209
solution: Experience Manager, Experience Manager Forms
role: User, Developer
source-git-commit: d7b9e947503df58435b3fee85a92d51fae8c1d2d
workflow-type: tm+mt
source-wordcount: '1226'
ht-degree: 0%

---

# Adaptieve Forms synchroniseren met XFA-formuliersjablonen{#synchronizing-adaptive-forms-with-xfa-form-templates}

<span class="preview"> de Adobe adviseert gebruikend de moderne en verlengbare gegevens vangen [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [&#x200B; het creëren van nieuwe Aangepaste Forms &#x200B;](/help/forms/using/create-an-adaptive-form-core-components.md) of [&#x200B; het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites &#x200B;](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

## Inleiding {#introduction}

U kunt een adaptief formulier maken op basis van een XFA-formuliersjabloon ( `*.XDP` -bestand). Met dit hergebruik kunt u uw investering in bestaande XFA-formulieren behouden. Voor informatie over hoe te om een XFA vormmalplaatje te gebruiken voor het creëren van een adaptieve vorm, [&#x200B; creeer een AanpassingsVorm die op een malplaatje &#x200B;](../../forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-an-xfa-form-template-p) wordt gebaseerd.

U kunt velden uit het XDP-bestand opnieuw gebruiken in het aangepaste formulier. Deze velden worden gebonden velden genoemd. De eigenschappen van de gebonden velden (zoals scripts, labels en weergave-indeling) worden uit het XDP-bestand gekopieerd. U kunt er ook voor kiezen de waarde van sommige van deze eigenschappen te overschrijven.

AEM Forms biedt een manier om u te helpen de velden van de adaptieve formulieren synchroon te houden met alle wijzigingen die later worden aangebracht in de corresponderende velden in het XDP-bestand. In dit artikel wordt uitgelegd hoe u deze synchronisatie kunt inschakelen.

![&#x200B; u kunt gebieden van een vorm XFA aan een adaptieve vorm slepen &#x200B;](assets/drag-drop-xfa.gif.gif)

In de AEM Forms-ontwerpomgeving kunt u velden van een XFA-formulier (links) naar een adaptief formulier slepen (rechts)

## Vereisten {#prerequisites}

Om de informatie in dit artikel te gebruiken, wordt een vertrouwdheid met de volgende gebieden geadviseerd:

* [Een adaptief formulier maken](../../forms/using/creating-adaptive-form.md)

* XFA (XML Forms Architecture)

Om de activa te gebruiken verstrekt voor het voorbeeld in het artikel, download het steekproefpakket zoals die in de volgende sectie wordt verklaard, [&#x200B; pakket van de Steekproef &#x200B;](../../forms/using/synchronizing-adaptive-forms-xfa.md#p-sample-package-p).

## Voorbeeldpakket {#sample-package}

In het artikel wordt een voorbeeld gebruikt om te tonen hoe u het aangepaste formulier synchroniseert met een bijgewerkte XFA-formuliersjabloon. De activa die in het voorbeeld worden gebruikt zijn beschikbaar in een pakket, dat van de [&#x200B; sectie van Downloads &#x200B;](../../forms/using/synchronizing-adaptive-forms-xfa.md#p-downloads-p) in dit artikel kan worden gedownload.

Nadat u het pakket hebt geüpload, kunt u deze elementen weergeven in de gebruikersinterface van AEM Forms.

Installeer het pakket met gebruik van Package Manager: `https://<server>:<port>/crx/packmgr/index.jsp`

Het pakket bevat de volgende elementen:

1. `sample-form.xdp`: De XFA-formuliersjabloon die als voorbeeld wordt gebruikt

1. `sample-xfa-af`: Het adaptieve formulier op basis van het bestand sample-form.xdp. Dit adaptieve formulier bevat echter geen velden. In de volgende stap voegt u inhoud toe aan dit aangepaste formulier.

### Inhoud toevoegen aan het aangepaste formulier {#add-content-to-adaptive-form-br}

1. Ga naar https://&lt;server>:&lt;port>/aem/forms.html. Voer uw referenties in als hierom wordt gevraagd.
1. Open de sample-af-xfa voor bewerking in de auteursmodus.
1. Kies Gegevensmodelobjecten op het tabblad Inhoud in de inhoudbrowser op de zijbalk. Sleep NumeriekVeld1 en TextField1 naar het adaptieve formulier.
1. Verander de Titel van NumericField1 van **Numeriek Gebied** aan **AF Numeriek Gebied.**

>[!NOTE]
>
>In de voorgaande stappen overschrijft u een eigenschap van een veld in het XDP-bestand. Deze eigenschap wordt daarom niet gesynchroniseerd als de overeenkomende eigenschap in het XDP-bestand later wordt bewerkt.

## Wijzigingen detecteren in XDP-bestand {#detecting-changes-in-xdp-file}

Telkens wanneer er een wijziging optreedt in een XDP-bestand of een fragment, geeft de gebruikersinterface van AEM Forms alle adaptieve formulieren weer die zijn gebaseerd op het XDP-bestand of het fragment.

Nadat u een XDP-bestand hebt bijgewerkt, moet u het opnieuw uploaden in de AEM Forms-gebruikersinterface om de wijzigingen te kunnen markeren.

Laten we het `sample-form.xdp` -bestand bijvoorbeeld als volgt bijwerken:

1. Navigeer naar `https://<server>:<port>/projects.html.` Voer uw gegevens in als u hierom wordt gevraagd.
1. Klik op het tabblad Forms aan de linkerkant.
1. Download het `sample-form.xdp` -bestand op uw lokale computer. Het XDP-bestand wordt gedownload als een `.zip` -bestand, dat kan worden uitgepakt met een willekeurig bestandsdecompressiehulpprogramma.

1. Open het `sample-form.xdp` dossier en verander de titel van het gebied TextField1 van **Gebied van de Tekst** aan **Mijn Gebied van de Tekst**.

1. Upload het `sample-form.xdp` -bestand weer naar de gebruikersinterface van AEM Forms.

Als een XDP-bestand wordt bijgewerkt, wordt in de editor een pictogram weergegeven wanneer u de adaptieve formulieren bewerkt op basis van het XDP-bestand. Dit pictogram geeft aan dat het adaptieve formulier niet meer synchroon is met het XDP-bestand. Zie het pictogram naast in het zijpaneel in de volgende afbeelding.

![&#x200B; Pictogram om te tonen dat de adaptieve vorm uit synchronisatie met het XDP dossier &#x200B;](assets/sync-af-xfa.png) is

## Aangepaste formulieren synchroniseren met het nieuwste XDP-bestand {#synchronizing-adaptive-forms-with-the-latest-xdp-file}

Wanneer een adaptief formulier dat niet meer synchroon is met het XDP-bestand de volgende keer wordt geopend voor ontwerpen, wordt het volgende bericht weergegeven: **Schema/formuliersjabloon voor het Adaptieve formulier is bijgewerkt. `Click Here` om deze opnieuw te baseren met de nieuwe versie.**

Wanneer u op het bericht klikt, worden de velden in het adaptieve formulier gesynchroniseerd met de bijbehorende velden in het XDP-bestand.

Open `sample-xfa-af` in de ontwerpmodus voor het voorbeeld dat in dit artikel wordt gebruikt. Het bericht wordt onder aan het adaptieve formulier weergegeven.

![&#x200B; Bericht die u ertoe aanzet om de adaptieve vorm met het XDP dossier te synchroniseren &#x200B;](assets/sync-af-xfa-1.png)

### De eigenschappen bijwerken {#updating-the-properties}

Alle eigenschappen die van het XDP-bestand naar het adaptieve formulier zijn gekopieerd, worden bijgewerkt, behalve de eigenschappen die door de auteur expliciet in het adaptieve formulier (uit het dialoogvenster Component) zijn genegeerd. De lijst met eigenschappen die zijn bijgewerkt, is beschikbaar in de serverlogboeken.

Als u de eigenschappen in het adaptieve voorbeeldformulier wilt bijwerken, klikt u op de koppeling (met het label `"Click Here"` ) in het bericht. De titel van TextField1 verandert van **Gebied van de Tekst** in **Mijn Gebied van de Tekst**.

![&#x200B; update-bezit &#x200B;](assets/update-property.png)

>[!NOTE]
>
>Het etiketAF Numeriek Gebied werd niet veranderd omdat u dit bezit van de dialoog van componenteneigenschappen met voeten had getreden, zoals die in [&#x200B; wordt beschreven voegt inhoud aan adaptieve vormen &#x200B;](../../forms/using/synchronizing-adaptive-forms-xfa.md#p-add-content-to-adaptive-form-br-p) toe.

### Nieuwe velden van XDP-bestand toevoegen aan adaptief formulier   {#adding-new-fields-from-xdp-file-to-adaptive-form-nbsp}

Alle velden die later aan het oorspronkelijke XDP-bestand worden toegevoegd, worden weergegeven op het tabblad Formulierhiërarchie en u kunt deze nieuwe velden naar het aangepaste formulier slepen.

U hoeft niet op de koppeling in het foutbericht te klikken om de velden op het tabblad Formulierhiërarchie bij te werken.

### Verwijderde velden in XDP-bestand {#deleted-fields-in-xdp-file}

Als een veld dat eerder naar een adaptief formulier is gekopieerd, uit een XDP-bestand wordt verwijderd, wordt in de ontwerpmodus een foutbericht weergegeven met de mededeling dat het veld niet bestaat in het XDP-bestand. Verwijder in dergelijke gevallen handmatig het veld uit het aangepaste formulier of wis de eigenschap `bindRef` in het dialoogvenster met componenten.

De volgende stappen illustreren deze gebruiksstroom voor de elementen in het voorbeeld dat in dit artikel wordt gebruikt:

1. Werk het `sample-form.xdp` -bestand bij en verwijder NumericField1.
1. Upload het `sample-form.xdp` -bestand in de gebruikersinterface van AEM Forms
1. Open het `sample-xfa-af` adaptieve formulier voor ontwerpen. Het volgende foutbericht wordt weergegeven: Het schema/formuliersjabloon voor het adaptieve formulier is bijgewerkt. `Click Here` gebruiken om de toepassing opnieuw te baseren op de nieuwe versie.

1. Klik op de koppeling (met het label &quot; `Click Here`&quot;) in het bericht. Er wordt een foutbericht weergegeven met de mededeling dat het veld niet meer bestaat in het XDP-bestand.

![&#x200B; Fout u ziet wanneer u een element in het XDP dossier &#x200B;](assets/no-element-xdp.png) schrapt

Het veld dat is verwijderd, wordt ook gemarkeerd met een pictogram om een fout in het veld aan te geven.

![&#x200B; pictogram van de Fout op het gebied &#x200B;](assets/error-field.png)

>[!NOTE]
>
>De velden in het adaptieve formulier met een onjuiste binding (een ongeldige `bindRef` -waarde in het dialoogvenster Bewerken) worden ook beschouwd als verwijderde velden. Als de auteur deze fouten niet corrigeert en het adaptieve formulier niet publiceert, wordt het veld beschouwd als een normaal, niet-gebonden adaptief formulierveld en wordt het veld opgenomen in de niet-gebonden sectie van het XML-uitvoerbestand.

## Downloads {#downloads}

Inhoudspakket voor het voorbeeld in dit artikel

[Bestand ophalen](assets/sample-xfa-af-sync-1.0.zip)
