---
title: Adaptieve Forms synchroniseren met XFA-formuliersjablonen
seo-title: Adaptieve Forms synchroniseren met XFA-formuliersjablonen
description: Aangepaste formulieren synchroniseren met XFA/XDP-bestanden.
seo-description: Aangepaste formulieren synchroniseren met XFA/XDP-bestanden.
uuid: 92818132-1ae0-4576-84f2-ece485a34457
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: dac4539b-804d-4420-9170-68000ebb2638
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65
workflow-type: tm+mt
source-wordcount: '1169'
ht-degree: 0%

---


# Adaptieve Forms synchroniseren met XFA-formuliersjablonen{#synchronizing-adaptive-forms-with-xfa-form-templates}

## Inleiding {#introduction}

U kunt een adaptief formulier maken op basis van een XFA-formuliersjabloon ( `*.XDP` bestand). Dankzij dit hergebruik kunt u uw investering in bestaande XFA-formulieren behouden. [Een adaptief formulier maken op basis van een sjabloon](../../forms/using/creating-adaptive-form.md#p-create-an-adaptive-form-based-on-an-xfa-form-template-p) voor informatie over het gebruik van een XFA-formuliersjabloon voor het maken van een adaptief formulier.

U kunt velden uit het XDP-bestand opnieuw gebruiken in het aangepaste formulier. Deze velden worden gebonden velden genoemd. De eigenschappen van de gebonden velden (zoals scripts, labels en weergave-indeling) worden uit het XDP-bestand gekopieerd. U kunt er ook voor kiezen de waarde van sommige van deze eigenschappen te overschrijven.

AEM Forms biedt een manier om u te helpen de velden van de adaptieve formulieren synchroon te houden met alle wijzigingen die later worden aangebracht in de corresponderende velden in het XDP-bestand. In dit artikel wordt uitgelegd hoe u deze synchronisatie kunt inschakelen.

![U kunt velden van een XFA-formulier naar een adaptief formulier slepen](assets/drag-drop-xfa.gif.gif)

In de AEM Forms-ontwerpomgeving kunt u velden van een XFA-formulier (links) naar een adaptief formulier slepen (rechts)

## Vereisten {#prerequisites}

Om de informatie in dit artikel te gebruiken, wordt een vertrouwdheid met de volgende gebieden aanbevolen:

* [Een adaptief formulier maken](../../forms/using/creating-adaptive-form.md)

* XFA (XML Forms Architecture)

Als u de elementen in het voorbeeld in het artikel wilt gebruiken, downloadt u het voorbeeldpakket zoals wordt beschreven in de volgende sectie, [Voorbeeldpakket](../../forms/using/synchronizing-adaptive-forms-xfa.md#p-sample-package-p).

## Voorbeeldpakket {#sample-package}

In het artikel wordt een voorbeeld gebruikt om te tonen hoe u het aangepaste formulier synchroniseert met een bijgewerkte XFA-formuliersjabloon. De elementen die in het voorbeeld worden gebruikt, zijn beschikbaar in een pakket. U kunt deze downloaden in de sectie [Downloads](../../forms/using/synchronizing-adaptive-forms-xfa.md#p-downloads-p) in dit artikel.

Nadat u het pakket hebt geüpload, kunt u deze elementen weergeven in de gebruikersinterface van AEM Forms.

Installeer het pakket met behulp van pakketbeheer: `https://<server>:<port>/crx/packmgr/index.jsp`

Het pakket bevat de volgende elementen:

1. `sample-form.xdp`: De XFA-formuliersjabloon die als voorbeeld wordt gebruikt

1. `sample-xfa-af`: Het adaptieve formulier op basis van het bestand sample-form.xdp. Dit adaptieve formulier bevat echter geen velden. In de volgende stap voegen we inhoud toe aan dit aangepaste formulier.

### Inhoud toevoegen aan adaptief formulier {#add-content-to-adaptive-form-br}

1. Ga naar https://&lt;server>:&lt;port>/aem/forms.html. Voer uw referenties in als hierom wordt gevraagd.
1. Open de sample-af-xfa voor bewerking in de auteursmodus.
1. Kies Gegevensmodelobjecten op het tabblad Inhoud in de inhoudbrowser op de zijbalk. Sleep NumeriekVeld1 en TextField1 naar het adaptieve formulier.
1. Wijzig de titel van NumericField1 van **Numeriek veld** in **AF Numeriek veld.**

>[!NOTE]
>
>In de voorgaande stappen is een eigenschap van een veld in het XDP-bestand overschreven. Deze eigenschap wordt daarom niet gesynchroniseerd als de overeenkomende eigenschap in het XDP-bestand later wordt gewijzigd.

## Wijzigingen in XDP-bestand {#detecting-changes-in-xdp-file} detecteren

Telkens wanneer er een wijziging optreedt in een XDP-bestand of een fragment, geeft de gebruikersinterface van AEM Forms alle adaptieve formulieren weer die zijn gebaseerd op het XDP-bestand of het fragment.

Nadat u een XDP-bestand hebt bijgewerkt, moet u het opnieuw uploaden in de AEM Forms-gebruikersinterface om de wijzigingen te kunnen markeren.

Als voorbeeld, laten wij het `sample-form.xdp` dossier bijwerken gebruikend de volgende stappen:

1. Navigeer naar `https://<server>:<port>/projects.html.` Voer desgevraagd uw referenties in.
1. Klik op het tabblad Forms aan de linkerkant.
1. Download het `sample-form.xdp`-bestand op uw lokale computer. Het XDP-bestand wordt gedownload als een `.zip`-bestand, dat kan worden geëxtraheerd met een willekeurig bestandsdecompressiehulpprogramma.

1. Open het `sample-form.xdp` dossier en verander de titel van het gebied TextField1 van **Tekstgebied** in **Mijn Gebied van de Tekst**.

1. Upload het `sample-form.xdp` bestand terug naar de gebruikersinterface van AEM Forms.

Als een XDP-bestand wordt bijgewerkt, wordt in de editor een pictogram weergegeven wanneer u de adaptieve formulieren bewerkt op basis van het XDP-bestand. Dit pictogram geeft aan dat het adaptieve formulier niet meer synchroon is met het XDP-bestand. Zie het pictogram naast in het zijpaneel in de volgende afbeelding.

![Pictogram om weer te geven dat het adaptieve formulier niet meer synchroon is met het XDP-bestand](assets/sync-af-xfa.png)

## Aangepaste formulieren synchroniseren met het nieuwste XDP-bestand {#synchronizing-adaptive-forms-with-the-latest-xdp-file}

Wanneer een adaptief formulier dat niet meer synchroon is met het XDP-bestand de volgende keer wordt geopend voor ontwerpen, wordt het volgende bericht weergegeven: **Schema-/formuliersjabloon voor het adaptieve formulier is bijgewerkt. `Click Here` om het met de nieuwe versie opnieuw te baseren.**

Wanneer u op het bericht klikt, worden de velden in het adaptieve formulier gesynchroniseerd met de bijbehorende velden in het XDP-bestand.

Open `sample-xfa-af` in de ontwerpmodus voor het voorbeeld dat in dit artikel wordt gebruikt. Het bericht wordt onder aan het adaptieve formulier weergegeven.

![Bericht waarin u wordt gevraagd het adaptieve formulier te synchroniseren met het XDP-bestand](assets/sync-af-xfa-1.png)

### De eigenschappen {#updating-the-properties} bijwerken

Alle eigenschappen die van het XDP-bestand naar het adaptieve formulier zijn gekopieerd, worden bijgewerkt, behalve de eigenschappen die door de auteur expliciet in het adaptieve formulier (uit het dialoogvenster Component) zijn genegeerd. De lijst met eigenschappen die zijn bijgewerkt, is beschikbaar in de serverlogboeken.

Als u de eigenschappen in het adaptieve voorbeeldformulier wilt bijwerken, klikt u op de koppeling (met het label `"Click Here"`) in het bericht. De titel van TextField1 verandert van **Tekstveld** in **Mijn tekstveld**.

![update-property](assets/update-property.png)

>[!NOTE]
>
>Het label AF Numeriek veld is niet gewijzigd omdat u deze eigenschap uit het dialoogvenster Eigenschappen van component hebt overschreven, zoals beschreven in [Inhoud toevoegen aan adaptieve formulieren](../../forms/using/synchronizing-adaptive-forms-xfa.md#p-add-content-to-adaptive-form-br-p).

### Nieuwe velden van XDP-bestand toevoegen aan adaptief formulier   {#adding-new-fields-from-xdp-file-to-adaptive-form-nbsp}

Alle velden die later aan het oorspronkelijke XDP-bestand worden toegevoegd, worden weergegeven op het tabblad Formulierhiërarchie en u kunt deze nieuwe velden naar het aangepaste formulier slepen.

U hoeft niet op de koppeling in het foutbericht te klikken om de velden op het tabblad Formulierhiërarchie bij te werken.

### Verwijderde velden in XDP-bestand {#deleted-fields-in-xdp-file}

Als een veld dat eerder naar een adaptief formulier is gekopieerd, uit een XDP-bestand wordt verwijderd, wordt in de ontwerpmodus een foutbericht weergegeven met de mededeling dat het veld niet bestaat in het XDP-bestand. Verwijder in dergelijke gevallen handmatig het veld uit het adaptieve formulier of wis de eigenschap `bindRef` in het dialoogvenster met componenten.

De volgende stappen illustreren deze gebruiksstroom voor de elementen in het voorbeeld dat in dit artikel wordt gebruikt:

1. Werk het `sample-form.xdp` dossier bij en schrap NumericField1.
1. Het `sample-form.xdp`-bestand uploaden in de gebruikersinterface van AEM Forms
1. Open het aangepaste formulier `sample-xfa-af` voor ontwerpen. Het volgende foutbericht wordt weergegeven: Schema/formuliersjabloon voor het adaptieve formulier is bijgewerkt. `Click Here` om het met de nieuwe versie opnieuw te baseren.

1. Klik op de koppeling ( &quot; `Click Here`&quot;) in het bericht. Er wordt een foutbericht weergegeven met de mededeling dat het veld niet meer bestaat in het XDP-bestand.

![Fout die u ziet wanneer u een element in het XDP dossier schrapt](assets/no-element-xdp.png)

Het veld dat is verwijderd, wordt ook gemarkeerd met een pictogram om een fout in het veld aan te geven.

![Foutpictogram in het veld](assets/error-field.png)

>[!NOTE]
>
>De velden in het adaptieve formulier met een onjuiste binding (een ongeldige `bindRef`-waarde in het dialoogvenster Bewerken) worden ook beschouwd als verwijderde velden. Als de auteur deze fouten niet corrigeert en het adaptieve formulier niet publiceert, wordt het veld behandeld als een normaal, niet-gebonden adaptief formulierveld en wordt het veld opgenomen in de niet-gebonden sectie van het XML-uitvoerbestand.

## Downloads {#downloads}

Inhoudspakket voor het voorbeeld in dit artikel

[Bestand ophalen](assets/sample-xfa-af-sync-1.0.zip)
