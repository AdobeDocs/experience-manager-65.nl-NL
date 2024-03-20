---
title: Zoeken in facetten om zoekresultaten te filteren
description: Hoe te om onderzoeksfacetten tot stand te brengen, te wijzigen en te gebruiken in [!DNL Adobe Experience Manager].
contentOwner: AG
role: Admin, Developer
feature: Search
exl-id: acaf46e6-ff70-4825-8922-ce8f82905a92
hide: true
solution: Experience Manager, Experience Manager Assets
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '2259'
ht-degree: 11%

---

# Zoeken in facetten {#search-facets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [Klik hier](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/search-facets.html?lang=en) |
| AEM 6,5 | Dit artikel |

Een bedrijfsbrede implementatie van [!DNL Adobe Experience Manager Assets] heeft de capaciteit om vele activa op te slaan. Soms kan het lastig en tijdrovend zijn om het juiste middel te vinden als u alleen de algemene zoekmogelijkheden van [!DNL Experience Manager].

Gebruik zoekfacetten in het deelvenster Filters om de zoekervaring gedetailleerder te maken en de zoekfunctionaliteit efficiënter en veelzijdiger te maken. De facetten van het onderzoek voegen veelvoudige afmetingen (predikaten) toe die u toelaten om complexere onderzoeken uit te voeren. Het deelvenster Filters bevat een aantal standaardfacetten. U kunt ook aangepaste zoekfacetten toevoegen.

Samengevat kunt u met zoekfacetten op verschillende manieren naar elementen zoeken in plaats van in één, vooraf bepaalde, taxonomische volgorde. U kunt gemakkelijk tot het gewenste niveau van detail voor een gerichter onderzoek boor.

Als u bijvoorbeeld een afbeelding zoekt, kunt u kiezen of u een bitmap- of een vectorafbeelding wilt. U kunt het zoekbereik verder verkleinen door het MIME-type voor de afbeelding op te geven. Op dezelfde manier kunt u bij het zoeken naar documenten de indeling opgeven, bijvoorbeeld PDF of MS Word.

## Een voorspelling toevoegen {#adding-a-predicate}

De zoekfacetten die in het deelvenster Filters worden weergegeven, worden in het onderliggende zoekformulier gedefinieerd aan de hand van voorspelden. Als u meer of verschillende facetten wilt weergeven, voegt u voorspelingen toe aan het standaardformulier of gebruikt u een aangepast formulier dat naar keuze facetten bevat.

Voor zoekopdrachten in volledige tekst voegt u de opdracht **[!UICONTROL Fulltext]** voorspellen voor het formulier. Gebruik de voorspelling van de eigenschap om te zoeken naar elementen die overeenkomen met één eigenschap die u opgeeft. Gebruik de voorspelling Opties om te zoeken in elementen die overeenkomen met een of meer waarden voor een bepaalde eigenschap. Voeg de Datumbereik-voorspelling toe aan zoekelementen die binnen een opgegeven datumbereik zijn gemaakt.

1. Klik op de knop [!DNL Experience Manager] logo en ga vervolgens naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Search Forms]**.
1. Van de [!UICONTROL Search Forms] pagina, selecteert u **[!UICONTROL Assets Admin Search Rail]** en klik vervolgens op **[!UICONTROL Edit]** ![bewerkingspictogram](assets/do-not-localize/aemassets_edit.png).

   >[!NOTE]
   >
   >Om de functionaliteit van het omslagonderzoek van vooraf gevormd te gebruiken [!DNL Assets] Voer de volgende stappen uit in een eerdere versie van Admin Search Rail:
   >
   >1. Navigeren naar `/conf/global/settings/dam/search/facets/assets/jcr:content/items` in CRXDE.
   >1. Verwijder de `type` knooppunt.
   >1. Vanaf het pad `/libs/settings/dam/search/facets/assets/jcr:content/items`, kopieert u de knooppunten `asset`, `directory`, `typeor`, `excludepaths`, en `searchtype` op het in stap 1 aangegeven pad.
   >1. Sla de wijzigingen op.

1. In de [!UICONTROL Edit Search Forms] pagina, sleept u een voorspelling van de **[!UICONTROL Select Predicate]** aan het hoofdvenster. Sleep bijvoorbeeld **[!UICONTROL Property Predicate]**.

   ![Een voorspelling selecteren en verplaatsen om de zoekfilters aan te passen](assets/drag_predicate.png)

   *Afbeelding: selecteer en verplaats een voorspelling om de zoekfilters aan te passen.*

1. In de [!UICONTROL Settings] voert u een veldlabel, plaatsaanduidingstekst en beschrijving voor de voorspelling in. Geef een geldige naam op voor de eigenschap metadata die u aan de voorspelling wilt koppelen. Het koptekstlabel in het dialoogvenster [!UICONTROL Settings] geeft het type van de geselecteerde voorspelling aan.

1. Geef in het veld [!UICONTROL Property Name] een geldige naam op voor de metadata-eigenschap die u aan het predicaat wilt koppelen. Dit is de naam op basis waarvan de zoekopdracht wordt uitgevoerd. Voer bijvoorbeeld `jcr:content/metadata/dc:description` of `./jcr:content/metadata/dc:description` in.

   U kunt ook een bestaand knooppunt selecteren in het dialoogvenster Selecteren.

   ![Een metagegevenseigenschap koppelen aan een voorspelling in het veld Eigenschapnaam](assets/property_settings.png)

   Een metagegevenseigenschap koppelen aan een voorspelling in het veld Eigenschapnaam

1. Klik op de knop **[!UICONTROL Preview]** ![voorvertoning](assets/do-not-localize/preview_icon.png) Hiermee genereert u een voorvertoning van het deelvenster Filters zoals dit wordt weergegeven nadat u de voorspelling hebt toegevoegd.
1. Bekijk de lay-out van de voorspelling in de modus Voorbeeld.

   ![Voorbeeld van het zoekformulier bekijken voordat de wijzigingen worden verzonden](assets/preview-1.png)

   Voorbeeld van het zoekformulier bekijken voordat de wijzigingen worden verzonden

1. Als u de voorvertoning wilt sluiten, klikt u op de knop **[!UICONTROL Close]** ![close](assets/do-not-localize/close.png) in de rechterbovenhoek van de voorvertoning.
1. Klikken **[!UICONTROL Done]** om de instellingen op te slaan.
1. Navigeer naar het deelvenster Zoeken in het dialoogvenster [!DNL Assets] gebruikersinterface. De voorspelling van de eigenschap wordt toegevoegd aan het deelvenster.
1. Voer in het tekstvak een beschrijving in voor het element dat u wilt doorzoeken. Voer bijvoorbeeld `Adobe`. Wanneer u een zoekopdracht uitvoert, worden elementen met overeenkomende beschrijving `Adobe` worden weergegeven in de zoekresultaten.

## Een voorspelling van opties toevoegen {#adding-an-options-predicate}

Met de voorspelling Opties kunt u meerdere zoekopties toevoegen in het deelvenster Filters. U kunt een of meer van deze opties selecteren in het deelvenster Filters om te zoeken naar elementen. Als u bijvoorbeeld naar elementen wilt zoeken op basis van het bestandstype, configureert u opties, zoals Afbeeldingen, Multimedia, Documenten en Archieven, in het zoekformulier. Nadat u deze opties hebt geconfigureerd, wordt de zoekopdracht uitgevoerd op elementen van het type GIF, JPEG, PNG, enzovoort, wanneer u de optie Afbeeldingen in het deelvenster Filters selecteert.

Als u de opties wilt toewijzen aan de desbetreffende eigenschap, maakt u een knooppuntstructuur voor de opties en geeft u het pad van het bovenliggende knooppunt op in de eigenschap Eigenschapnaam van de voorspelling van opties. Het bovenliggende knooppunt moet van het type zijn `sling`: `OrderedFolder`. De opties moeten van het type zijn `nt:unstructured`. De optieknooppunten moeten de eigenschappen hebben `jcr:title` en `value` geconfigureerd.

De `jcr:title` Deze eigenschap is een gebruiksvriendelijke naam voor de optie die wordt weergegeven in het deelvenster Filters. De `value` wordt gebruikt in de query om deze aan te passen aan de opgegeven eigenschap.

Wanneer u een optie selecteert, wordt de zoekopdracht uitgevoerd op basis van de opdracht `value` eigenschap van het optieknooppunt en eventuele onderliggende knooppunten. De volledige structuur onder het optieknooppunt wordt doorlopen en de `value` bezit van elke kindknoop wordt gecombineerd gebruikend OF verrichting om de onderzoeksvraag te vormen.

Als u bijvoorbeeld &quot;Afbeeldingen&quot; selecteert voor bestandstypen, wordt de zoekquery voor de assets samengesteld door de eigenschap `value` te combineren met een OR-bewerking. De zoekquery voor afbeeldingen wordt bijvoorbeeld samengesteld door de resultaten te combineren die overeenkomen met *afbeelding/jpeg*, *afbeelding/gif*, *afbeelding/png*, *afbeelding/pjpeg* en *afbeelding/tiff* voor de eigenschap `jcr:content/metadata/dc:format` met behulp van een OR-bewerking.

![Het bezit van de waarde van een dossiertype, zoals die in CRXDE wordt gezien wordt gebruikt voor onderzoeksvragen om te werken](assets/filetype-value-property.png)

Het bezit van de waarde van een dossiertype, zoals die in CRXDE wordt gezien wordt gebruikt voor onderzoeksvragen om te werken

In plaats van handmatig een knooppuntstructuur voor de opties in de CRXDE-opslagplaats te maken, kunt u de opties in een JSON-bestand definiëren door corresponderende sleutel-waardeparen op te geven. Geef het pad van het JSON-bestand op in het veld **[!UICONTROL Property Name]**. U kunt bijvoorbeeld de sleutel-waardeparen `image/bmp`, `image/gif`, `image/jpeg` en `image/png` definiëren en hun waarden opgeven zoals getoond in het volgende JSON-voorbeeldbestand. In de **[!UICONTROL Property Name]** kunt u het CRXDE-pad voor dit bestand opgeven.

```json
{
    "options" :
 [
          {"value" : "image/bmp","text" : "BMP"},
          {"value" : "image/gif","text" : "GIF"},
          {"value" : "image/jpeg","text" : "JPEG"},
          {"value" : "image/png","text" : "PNG"}
 ]
}
```

Als u een bestaand knooppunt wilt gebruiken, geeft u dit op in het dialoogvenster Selecteren.

>[!NOTE]
>
>De voorspelling van Opties is een aangepaste omslag die bezitsvoorspelling omvat om het beschreven gedrag aan te tonen. Momenteel, is er geen REST eindpunt beschikbaar om de functionaliteit te steunen native.

1. Klik op de knop [!DNL Experience Manager] logo en ga vervolgens naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Search Forms]**.
1. Van de **[!UICONTROL Search Forms]** pagina, selecteert u **[!UICONTROL Assets Admin Search Rail]** en klik vervolgens op **[!UICONTROL Edit]**.
1. Sleep op de pagina **[!UICONTROL Edit Search Form]** **[!UICONTROL Options Predicate]** van het tabblad **[!UICONTROL Select Predicate]** naar het hoofdvenster.
1. Voer op het tabblad **[!UICONTROL Settings]** een label en een naam voor de eigenschap in. Als u bijvoorbeeld elementen wilt zoeken op basis van hun indeling, geeft u een gebruikersvriendelijke naam voor het label op, bijvoorbeeld **[!UICONTROL File Type]**. Geef bijvoorbeeld de eigenschap op op basis waarvan de zoekopdracht in het eigenschapveld moet worden uitgevoerd. `jcr:content/metadata/dc:format.`
1. Voer een van de volgende handelingen uit:

   * In de **[!UICONTROL Property Name]** vermeld het pad van het JSON-bestand, waarin u de knooppunten voor de opties definieert en corresponderende sleutelwaardeparen opgeeft.
   * Klik op de knop `+` symbool naast het veld Opties om de weergavetekst en de waarde op te geven voor de opties die u in het deelvenster Filters wilt opgeven. Als u nog een optie wilt toevoegen, klikt u op `+` en herhaal de stap.

1. Zorg ervoor dat **[!UICONTROL Single Select]** is uitgeschakeld, zodat de gebruiker meerdere opties voor bestandstypen tegelijk kan selecteren (bijvoorbeeld Afbeeldingen, Documenten, Multimedia en Archieven). Als u **[!UICONTROL Single Select]** selecteert, kan de gebruiker slechts één optie tegelijk selecteren voor bestandstypen.

   ![De beschikbare velden in de voorspelling Opties](assets/options_predicate.png)

   De beschikbare velden in de voorspelling Opties

1. In de **[!UICONTROL Description]** veld, voer een optionele beschrijving in en klik vervolgens op **[!UICONTROL Done]**.
1. Navigeer naar het deelvenster Zoeken. De voorspelling Opties wordt toegevoegd aan de **Zoeken** deelvenster. De opties voor **[!UICONTROL File Type]** worden weergegeven als selectievakjes.

## Eigenschappenvoorspelling voor meerdere waarden toevoegen {#adding-a-multi-value-property-predicate}

Met de voorspelling Multi-Value-eigenschap kunt u elementen zoeken naar meerdere waarden. Overweeg een scenario waar u beelden van veelvoudige producten in hebt [!DNL Assets] en de metagegevens voor elke afbeelding bevatten een SKU-nummer dat aan het product is gekoppeld. Met deze voorspelling kunt u op basis van meerdere SKU-nummers zoeken naar productafbeeldingen.

1. Klik op de knop [!DNL Experience Manager] logo en ga vervolgens naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Search Forms]**.
1. Selecteer op de pagina Search Forms de optie **[!UICONTROL Assets Admin Search Rail]**, klikt u op **[!UICONTROL Edit]** ![bewerkingspictogram](assets/do-not-localize/aemassets_edit.png).
1. Sleep op de pagina Zoekformulier bewerken een **[!UICONTROL Multi Value Property Predicate]** van het tabblad **[!UICONTROL Select Predicate]** naar het hoofdvenster.
1. In de **[!UICONTROL Settings]** voert u een label en plaatsaanduidingstekst in voor de voorspelling. Geef bijvoorbeeld de eigenschapnaam op op basis waarvan de zoekopdracht in het eigenschapveld moet worden uitgevoerd. `jcr:content/metadata/dc:value`. U kunt ook een knooppunt selecteren in het dialoogvenster Selecteren.
1. Zorg ervoor dat **[!UICONTROL Delimiter Support]** is geselecteerd. Geef in het veld **[!UICONTROL Input Delimiters]** scheidingstekens op om afzonderlijke waarden van elkaar te scheiden. Standaard wordt een komma opgegeven als scheidingsteken. U kunt een ander scheidingsteken opgeven.
1. In de **Beschrijving** veld, voer een optionele beschrijving in en klik vervolgens op **[!UICONTROL Done]**.
1. Navigeer naar het deelvenster Filters in het dialoogvenster [!DNL Assets] gebruikersinterface. Het predicaat **[!UICONTROL Multi Value Property]** wordt toegevoegd aan het deelvenster.
1. Geef meerdere waarden op in het veld Meerdere waarden, gescheiden door de scheidingstekens, en voer de zoekopdracht uit. Met de functie voor voorspellen wordt een exacte tekstovereenkomst opgehaald voor de waarden die u opgeeft.

## Een voorspelling van tags toevoegen {#adding-a-tags-predicate}

Met de tagvoorspelling kunt u op tags gebaseerde zoekopdrachten naar elementen uitvoeren. Standaard, [!DNL Assets] zoekt elementen naar een of meer labels die overeenkomen met de tags die u opgeeft. Met andere woorden, de zoekquery voert een OR-bewerking uit met de opgegeven tags. U kunt echter de optie Alle tags afstemmen gebruiken om te zoeken naar elementen die alle tags bevatten die u opgeeft.

1. Klik op de knop [!DNL Experience Manager] logo en ga vervolgens naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Search Forms]**.
1. Selecteer op de pagina Zoeken in Forms de optie **[!UICONTROL Assets Admin Search Rail]** en klik vervolgens op **[!UICONTROL Edit]** ![bewerkingspictogram](assets/do-not-localize/aemassets_edit.png).
1. Sleep in de pagina Zoekformulier bewerken het gereedschap **[!UICONTROL Tags Predicate]** van het Uitgezochte lusje Predicate aan de belangrijkste ruit.
1. Voer op het tabblad Instellingen een plaatsaanduidingstekst in voor de voorspelling. Geef bijvoorbeeld de eigenschapnaam op op basis waarvan de zoekopdracht in het eigenschapveld moet worden uitgevoerd. *jcr:content/metadata/cq:tags*. U kunt ook een knooppunt in CRXDE selecteren in het dialoogvenster Selecteren.
1. Configureer de padeigenschap Root-tags van deze voorspelling om verschillende tags in de lijst Tags te vullen.
1. Selecteer **[!UICONTROL Show match all tags option]** om te zoeken naar assets die alle tags bevatten die u opgeeft.

1. In de **[!UICONTROL Description]** veld, voer een optionele beschrijving in en klik vervolgens op **[!UICONTROL Done]**.
1. Navigeer naar het deelvenster Zoeken. De **[!UICONTROL Tags]** predicate wordt toegevoegd aan het deelvenster Zoeken.
1. Geef tags op op basis waarvan u de elementen wilt zoeken of een selectie wilt maken in de lijst met suggesties.

1. Selecteren **[!UICONTROL Match all]** om te zoeken naar overeenkomsten die alle tags bevatten die u opgeeft.

## Andere voorspelling toevoegen {#adding-other-predicates}

Net als bij de manier waarop u een voorspelling van eigenschappen of een voorspelling van opties toevoegt, kunt u de volgende aanvullende voorspelling toevoegen aan het deelvenster Zoeken:

| Naam voorspelling | Beschrijving | Eigenschappen |
|---|---|---|
| [!UICONTROL Fulltext] | Zoekvoorspelling om volledige tekstzoekopdrachten uit te voeren op een volledig elementknooppunt. Deze wordt toegewezen met de operator jcr:contains. U kunt een relatief pad opgeven als u een volledige tekstzoekopdracht wilt uitvoeren op een bepaald gedeelte van het knooppunt met elementen. | <ul><li>Label</li><li>Plaatsaanduiding</li><li>Eigenschapnaam</li><li>Beschrijving</li></ul> |
| [!UICONTROL Path Browser] | Zoekvoorspelling voor het zoeken naar elementen in mappen en submappen op een vooraf geconfigureerd hoofdpad | <ul><li>Plaatsaanduiding</li><li>Basispad</li><li>Beschrijving</li></ul> |
| [!UICONTROL Path] | Gebruik deze optie om resultaten op de locatie te filteren. U kunt verschillende paden opgeven als opties. | <ul><li>Label</li><li>Pad</li><li>Beschrijving</li></ul> |
| [!UICONTROL Publish Status] | Zoeken voorspellen om te zoeken op middelen op basis van hun publicatiestatus | <ul><li>Label</li><li>Eigenschapnaam</li><li>Beschrijving</li></ul> |
| [!UICONTROL Relative Date] | Zoeken voorspelt dat er wordt gezocht naar elementen op basis van de relatieve datum waarop deze zijn gemaakt. U kunt bijvoorbeeld opties configureren, zoals 2 maanden geleden, 3 weken geleden enzovoort. | <ul><li>Label</li><li>Eigenschapnaam</li><li>Relatieve datum</li></ul> |
| [!UICONTROL Range] | Zoeken voorspelt dat er wordt gezocht in elementen die binnen een opgegeven bereik vallen. In het paneel van het Onderzoek, kunt u minimum en maximumwaarden voor de waaier specificeren. | <ul><li>Label</li><li>Eigenschapnaam</li><li>Beschrijving</li></ul> |
| [!UICONTROL Date Range] | Zoeken voorspelt hoe u elementen die binnen een opgegeven bereik zijn gemaakt, kunt zoeken naar een datumeigenschap. In het deelvenster Zoeken kunt u begin- en einddatums opgeven met behulp van datumkiezers. | <ul><li>Label</li><li>Plaatsaanduiding</li><li>Eigenschapnaam</li><li>Tekst bereik (van)</li><li>Tekst bereik (naar)</li><li>Beschrijving</li></ul> |
| [!UICONTROL Date] | Zoeken voorspelt hoe elementen op basis van een schuifregelaar worden doorzocht op basis van een eigenschap date. | <ul><li>Label</li><li>Eigenschapnaam</li><li>Beschrijving</li></ul> |
| [!UICONTROL File Size] | Zoeken voorspelt hoe u elementen kunt zoeken op basis van hun grootte. Het is een op meer details gebaseerde voorspelling waarbij u de schuifopties van een configureerbaar knooppunt selecteert. De standaardopties worden gedefinieerd bij /libs/dam/options/predicates/filesize in de CRXDE-opslagplaats. De bestandsgrootte wordt opgegeven in bytes. | <ul><li>Label</li><li>Eigenschapnaam</li><li>Pad</li><li>Beschrijving</li></ul> |
| [!UICONTROL Asset Last Modified] | Zoekvoorspelling voor zoeken in onlangs gewijzigde elementen | <ul><li>Eigenschapnaam</li><li>Waarde van eigenschap</li><li>Beschrijving</li></ul> |
| [!UICONTROL Publish Status] | Zoeken voorspellen om naar elementen te zoeken op basis van hun publicatiestatus | <ul><li>Label</li><li>Eigenschapnaam</li><li>Beschrijving</li></ul> |
| [!UICONTROL Rating] | Zoeken voorspelt dat er wordt gezocht naar elementen op basis van hun gemiddelde waardering | <ul><li>Label</li><li>Eigenschapnaam</li><li>Optiepad</li><li>Beschrijving</li></ul> |
| [!UICONTROL Expiry Status] | Zoeken voorspelt dat naar elementen wordt gezocht op basis van hun vervalstatus | <ul><li>Label</li><li>Eigenschapnaam</li><li>Beschrijving</li></ul> |
| [!UICONTROL Hidden] | Zoekvoorspelling die een verborgen veldeigenschap definieert voor het zoeken naar elementen | <ul><li>Eigenschapnaam</li><li>Waarde van eigenschap</li><li>Beschrijving</li></ul> |

## Standaardzoekfacetten herstellen {#restoring-default-search-facets}

Standaard een slotpictogram ![gesloten pictogram vergrendelen](assets/do-not-localize/lock_closed_icon.svg) verschijnt vóór **[!UICONTROL Assets Admin Search Rail]** in de **[!UICONTROL Search Forms]** pagina. Het vergrendelingspictogram tegen een optie op de pagina Zoeken in Forms geeft aan dat de standaardinstellingen intact zijn en niet worden aangepast. Het pictogram ![gesloten pictogram vergrendelen](assets/do-not-localize/lock_closed_icon.svg) verdwijnt als u zoekfacetten aan het formulier toevoegt die aangeven dat het standaardformulier is gewijzigd.

![Vergrendelingspictogram](assets/locked_admin_rail.png)

Voer de volgende stappen uit om de standaardzoekfacet te herstellen:

1. Selecteren **[!UICONTROL Assets Admin Search Rail]** in de **[!UICONTROL Search Forms]** pagina.
1. Klikken **[!UICONTROL Delete]** ![deleteoutline](assets/do-not-localize/deleteoutline.png) in de werkbalk.
1. Klik in het bevestigingsdialoogvenster op **[!UICONTROL Delete]** om de aangepaste wijzigingen te verwijderen.

   Nadat u de aangepaste wijzigingen in zoekfacetten hebt verwijderd, wordt het vergrendelingspictogram weergegeven ![gesloten pictogram vergrendelen](assets/do-not-localize/lock_closed_icon.svg) opnieuw verschijnt voor **[!UICONTROL Assets Admin Search Rail]** in de **[!UICONTROL Search Forms]** pagina.

## Gebruikersmachtigingen {#user-permissions}

Als er geen beheerdersrol aan u is toegewezen, volgt hier een lijst met machtigingen die u nodig hebt voor het uitvoeren van bewerkingen, verwijderen en voorvertoningen van handelingen met zoekfacetten.

| Handeling | Machtigingen |
| ------------------- | ---------------------------------------------------------------- |
| [!UICONTROL Edit] | Lezen en schrijven toestemmingen op `/apps` knooppunt in CRXDE |
| [!UICONTROL Delete] | De machtiging Lezen, Schrijven en Verwijderen geldt voor de `/apps` knooppunt in CRXDE |
| [!UICONTROL Preview] | De machtiging Lezen, Schrijven en Verwijderen geldt voor de `/var/dam/content` knooppunt in CRXDE. Ook, lees en schrijf toestemmingen op `/apps` knooppunt. |

>[!MORELIKETHIS]
>
>* [Zoekmogelijkheden voor middelen uitbreiden](searchx.md)
>* [Assets doorzoeken](search-assets.md)
