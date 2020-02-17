---
title: Klassieke UI-tagconsole
seo-title: Klassieke UI-tagconsole
description: Meer informatie over de Classic UI Tagging Console.
seo-description: Meer informatie over de Classic UI Tagging Console.
uuid: 51e29422-f967-424b-a7fd-4ca2ddc6b8a3
contentOwner: Chiradeep Majumdar
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: content
content-type: reference
discoiquuid: b279c033-bc93-4e62-81ad-123c40b9fdd2
docset: aem65
translation-type: tm+mt
source-git-commit: 684d2d5f73d571a15c8155e7870134c28dc892b7

---


# Klassieke UI-tagconsole{#classic-ui-tagging-console}

Deze sectie is voor de Classic UI Tagging Console.

De voor aanraking geoptimaliseerde UI Tagingconsole is [hier](/help/sites-administering/tags.md#tagging-console).

U kunt als volgt de klassieke UI-tagingconsole openen:

* op auteur
* aanmelden met beheerdersrechten
* blader aan de console bijvoorbeeld, [https://localhost:4502/tagging](https://localhost:4502/tagging)

![](assets/managing_tags_usingthetagasministrationconsole.png)

## Tags en naamruimten maken {#creating-tags-and-namespaces}

1. Afhankelijk van het niveau dat u begint, kunt u een tag of een naamruimte maken met **Nieuw**:

   Als u **Tags** selecteert, kunt u een naamruimte maken:

   ![](assets/creating_tags_andnamespaces.png)

   Als u een naamruimte selecteert (bijvoorbeeld **Demo**), kunt u binnen die naamruimte een tag maken:

   ![](assets/creating_tags_andnamespacesinnewnamespace.png)

1. In beide gevallen voert u

   * **Titel**(*vereist*) De weergavetotel voor de tag. U kunt elk teken invoeren, maar u kunt het beste deze speciale tekens niet gebruiken:

      * `colon (:)` - naamruimtescheidingsteken
      * `forward slash (/)` - scheidingsteken voor subtags
      Deze tekens worden niet weergegeven als ze worden ingevoerd.

   * **Naam**(*Vereist*) De knooppuntnaam voor de markering.

   * **Beschrijving**(*Optioneel*) Een beschrijving van de tag.

   * Selecteer **Maken**


## Tags bewerken {#editing-tags}

1. Selecteer in het rechterdeelvenster de tag die u wilt bewerken.
1. Click **Edit**.
1. U kunt de **titel** en de **beschrijving** wijzigen.
1. Klik op **Opslaan** om het dialoogvenster te sluiten.

## Tags verwijderen {#deleting-tags}

1. Selecteer in het rechterdeelvenster het label dat u wilt verwijderen.
1. Click **Delete**.
1. Klik op **Ja** om het dialoogvenster te sluiten.

   De tag mag niet meer worden vermeld.

## Labels activeren en deactiveren {#activating-and-deactivating-tags}

1. Selecteer in het rechterdeelvenster de naamruimte of tag die u wilt activeren (publiceren) of deactiveren (publiceren ongedaan maken).
1. Klik naar wens op **Activeren** of **Deactiveren** .

## Lijst - tonen waar naar tags wordt verwezen {#list-showing-where-tags-are-referenced}

**Met List** wordt een nieuw venster geopend met de paden van alle pagina&#39;s die de gemarkeerde code gebruiken:

![](assets/list_showing_wheretagsarereferenced.png)

## Labels verplaatsen {#moving-tags}

Als u wilt helpen dat tagbeheerders en ontwikkelaars de taxonomie opschonen of de naam van een tag-id wijzigen, kunt u een tag naar een nieuwe locatie verplaatsen:

1. Open de **Tagingconsole** .
1. **Selecteer de tag en klik op** Verplaatsen... in de bovenste werkbalk (of in het contextmenu).
1. Definieer in het dialoogvenster **Tag** verplaatsen:

   * **naar**, de bestemmingsknoop.
   * **Naam wijzigen in**, de naam van het nieuwe knooppunt.

1. Klik op **Verplaatsen**.

Het dialoogvenster **Tag** verplaatsen ziet er als volgt uit:

![](assets/move_tag.png)

>[!NOTE]
>
>Auteurs mogen geen tags verplaatsen of de naam van een tag-id wijzigen. Auteurs mogen indien nodig alleen de [titels](#editing-tags)van de tags wijzigen.

## Tags samenvoegen {#merging-tags}

U kunt tags samenvoegen wanneer een taxonomie duplicaten bevat. Wanneer label A wordt samengevoegd met label B, worden alle pagina&#39;s met label A getagd met label B en is label A niet meer beschikbaar voor auteurs.

Een tag samenvoegen in een andere tag:

1. Open de **Tagingconsole** .
1. **Selecteer de tag en klik op** Samenvoegen... in de bovenste werkbalk (of in het contextmenu).
1. Definieer in het dialoogvenster **Samenvoegcode** :

   * **in**, de bestemmingsknoop.

1. Klik op **Samenvoegen**.

Het dialoogvenster **Samenvoegcode** ziet er als volgt uit:

![](assets/mergetag.png)

## Gebruik van tags tellen {#counting-usage-of-tags}

Zo ziet u hoe vaak een tag wordt gebruikt:

1. Open de **Tagingconsole** .
1. Klik op **Tellen in de bovenste werkbalk** : In de kolom Aantal wordt het resultaat weergegeven.

## Tags beheren in verschillende talen {#managing-tags-in-different-languages}

De optionele `title`eigenschap van een tag kan in meerdere talen worden vertaald. De tag `titles` kan vervolgens worden weergegeven volgens de taal van de gebruiker of de paginataal.

### Tagtitels definiëren in meerdere talen {#defining-tag-titles-in-multiple-languages}

De volgende procedure laat zien hoe u het label `title`van **Dieren** vertaalt in het Engels, Duits en Frans:

1. Ga naar de **Tagingconsole** .
1. Bewerk de tag **Dieren** onder **tags** > **Stock Photography**.
1. Voeg de vertalingen in de volgende talen toe:

   * **Engels**: Dieren
   * **Duits**: Tiere
   * **Frans**: Animaux

1. Sla de wijzigingen op.

Het dialoogvenster ziet er als volgt uit:

![](assets/edit_tag.png)

In de tagconsole wordt de taalinstelling van de gebruiker gebruikt. Voor de tag Animal wordt &#39;Animaux&#39; weergegeven voor een gebruiker die de taal in gebruikerseigenschappen instelt op Frans.

Als u een nieuwe taal wilt toevoegen aan het dialoogvenster, raadpleegt u de sectie Een nieuwe taal [toevoegen aan het dialoogvenster](/help/sites-developing/building.md#adding-a-new-language-to-the-edit-tag-dialog) Tag bewerken in de sectie **Tags toevoegen voor ontwikkelaars** .

### Tagtitels weergeven in Pagina-eigenschappen in een opgegeven taal {#displaying-tag-titles-in-page-properties-in-a-specified-language}

Standaard wordt de tag `titles`in de pagina-eigenschappen weergegeven in de paginataal. Het tagdialoogvenster in de pagina-eigenschappen heeft een taalveld waarmee de tag `titles`in een andere taal kan worden weergegeven. In de volgende procedure wordt beschreven hoe u de tag `titles`in het Frans kunt weergeven:

1. Raadpleeg de vorige sectie om de Franse vertaling toe te voegen aan de **dieren** onder **Tags** > **Stock Photography**.
1. Open de pagina-eigenschappen van de pagina **Producten** in de Engelse vertakking van de site **Geometrixx** .
1. Open het dialoogvenster **Tags/Trefwoorden** (door het keuzemenu rechts van het weergavegebied Tags/Trefwoorden te selecteren) en selecteer de **Franse** taal in het keuzemenu in de rechterbenedenhoek.
1. Schuif met de pijlen naar links en rechts totdat u het tabblad **Stock Photography** kunt selecteren

   Selecteer de tag **Dieren** (**Animaux**) en selecteer buiten het dialoogvenster om deze te sluiten en voeg de tag toe aan de pagina-eigenschappen.

   ![](assets/french_tag.png)

Standaard wordt in het dialoogvenster Pagina-eigenschappen de code weergegeven `titles`volgens de paginataal.

In het algemeen wordt de taal van de tag opgehaald uit de paginataal als de paginataal beschikbaar is. Wanneer de [ widget `tag`](/help/sites-developing/building.md#tagging-on-the-client-side) in andere gevallen wordt gebruikt (bijvoorbeeld in formulieren of in dialoogvensters), is de taal van de tag afhankelijk van de context.

>[!NOTE]
>
>De tagcloud en de metatrefwoorden in de standaardpaginacomponent gebruiken de gelokaliseerde tag `titles`op basis van de paginataal, indien beschikbaar.