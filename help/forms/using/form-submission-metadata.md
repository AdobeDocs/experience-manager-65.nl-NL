---
title: Informatie uit gebruikersgegevens toevoegen aan metagegevens voor het verzenden van formulieren
seo-title: Informatie uit gebruikersgegevens toevoegen aan metagegevens voor het verzenden van formulieren
description: 'Leer hoe u met door de gebruiker verstrekte gegevens informatie aan metagegevens van een verzonden formulier kunt toevoegen. '
seo-description: 'Leer hoe u met door de gebruiker verstrekte gegevens informatie aan metagegevens van een verzonden formulier kunt toevoegen. '
uuid: c3eea3c0-31f8-4bf8-b5cf-34f907bdbdba
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
discoiquuid: 2c971da0-5bd5-40d1-820d-4efc2a44b49d
docset: aem65
translation-type: tm+mt
source-git-commit: 27a054cc5d502d95c664c3b414d0066c6c120b65
workflow-type: tm+mt
source-wordcount: '709'
ht-degree: 0%

---


# Informatie uit gebruikersgegevens toevoegen aan metagegevens voor formulierverzending{#adding-information-from-user-data-to-form-submission-metadata}

U kunt waarden die zijn ingevoerd in een element van het formulier gebruiken om metagegevensvelden van een concept of een formulier te berekenen. Met metagegevens kunt u inhoud filteren op basis van gebruikersgegevens. Een gebruiker voert bijvoorbeeld Jan Smit in het naamveld van het formulier. U kunt deze informatie gebruiken om metagegevens te berekenen die deze verzending kunnen categoriseren onder de JD voor initialen.

Als u metagegevensvelden wilt berekenen met door de gebruiker ingevoerde waarden, voegt u elementen van het formulier toe aan de metagegevens. Wanneer een gebruiker een waarde in dat element invoert, gebruikt een script de waarde om informatie te berekenen. Deze informatie wordt toegevoegd aan de metagegevens. Wanneer u een element als meta-gegevensgebied toevoegt, verstrekt u een sleutel voor het. De sleutel wordt toegevoegd als gebied in de meta-gegevens, en de gegevens verwerkte informatie wordt geregistreerd tegen het.

Een ziekteverzekeringsbedrijf publiceert bijvoorbeeld een formulier. In dit formulier legt een veld de pagina van de eindgebruikers vast. De klant wil alle verzendingen in een bepaald leeftijdsbereik controleren nadat een aantal gebruikers het formulier heeft verzonden. In plaats van alle gegevens te doorlopen die gecompliceerd worden door een toenemend aantal formulieren, helpen extra metagegevens de klant. De auteur van het formulier kan configureren welke eigenschappen/gegevens door de eindgebruiker worden ingevuld op het hoogste niveau, zodat de zoekopdracht gemakkelijker kan worden uitgevoerd. De extra meta-gegevens zijn door de gebruiker ingevulde informatie die op het hoogste niveau van de meta-gegevensknoop wordt opgeslagen, aangezien de auteur het vormde.

Een ander voorbeeld van een formulier waarin e-mailadres en telefoonnummer worden vastgelegd. Wanneer een gebruiker dit formulier anoniem bezoekt en het formulier verlaat, kan de auteur het formulier zodanig configureren dat de e-mailadres en het telefoonnummer automatisch worden opgeslagen. Dit formulier wordt automatisch opgeslagen en het telefoonnummer en de e-mailadres worden opgeslagen in het metagegevensknooppunt van het concept. Een gebruik-geval van deze configuratie is het lood management dashboard.

## Formulierelementen toevoegen aan metagegevens {#adding-form-elements-to-metadata}

Voer de volgende stappen uit om een element toe te voegen aan de metagegevens:

1. Open het aangepaste formulier in de bewerkingsmodus.\
   Als u het formulier wilt openen in de bewerkingsmodus, selecteert u het formulier in het formulierbeheer en tikt u op **Open**.
1. Selecteer in de bewerkingsmodus een component, tik ![veldniveau](assets/field-level.png) > **Aangepaste formuliercontainer** en tik vervolgens op ![cmp](assets/cmppr.png).
1. Klik in het zijpaneel op **Metagegevens**.
1. Klik in de sectie Metagegevens op **Toevoegen**.
1. Voeg scripts toe in het veld Waarde van het tabblad Metagegevens. Met de scripts die u toevoegt, worden gegevens verzameld uit elementen op het formulier en worden waarden berekend die worden doorgegeven aan de metagegevens.

   **true** wordt bijvoorbeeld aangemeld als de ingevoerde leeftijd groter is dan 21 en **false** wordt geregistreerd als deze lager is dan 21. U voert het volgende script in op het tabblad Metagegevens:

   `(agebox.value >= 21) ? true : false`

   ![Metagegevensscript](assets/add-element-metadata.png)

   Script dat is ingevoerd op het tabblad Metagegevens

1. Klik **OK**.

Nadat een gebruiker gegevens in het element invoert dat als meta-gegevensgebied wordt geselecteerd, wordt de gegevens gegevens gegevens geregistreerd in de meta-gegevens. U ziet de metagegevens in de opslagplaats waarin u metagegevens hebt opgeslagen.

## Metagegevens voor bijgewerkte formulierverzending bekijken: {#seeing-updated-form-nbsp-submission-metadata}

In het bovenstaande voorbeeld worden de metagegevens opgeslagen in de CRX-opslagplaats. De metagegevens zien er als volgt uit:

![Metagegevens](assets/metadata_entry_new.png)

Als u een element van het controlevakje in de meta-gegevens toevoegt, worden de geselecteerde waarden opgeslagen als een komma gescheiden koord. U voegt bijvoorbeeld een component CheckBox in het formulier toe en geeft de naam op als `checkbox1`. In de eigenschappen van de component van het controlevakje, voegt u de punten Rijvergunning, het Aantal van de Sociale Veiligheid, en Paspoort voor waarden 0, 1, en 2 toe.

![Meerdere waarden opslaan vanuit een selectievakje](assets/checkbox-metadata.png)

U selecteert een adaptieve formuliercontainer en in de formuliereigenschappen voegt u een metagegevenssleutel `cb1` toe waarmee `checkbox1.value` wordt opgeslagen, en publiceert u het formulier. Wanneer een klant het formulier invult, selecteert de klant de opties Paspoort en burgerservicenummer in het veld Selectievakje. De waarden 1 en 2 worden opgeslagen als 1, 2 in het cb1-veld van de metagegevens voor verzending.

![Metagegevensitem voor meerdere waarden die zijn geselecteerd in een veld van het selectievakje](assets/metadata-entry.png)

>[!NOTE]
>
>Het bovenstaande voorbeeld is alleen bedoeld voor leerdoeleinden. Zorg ervoor dat u naar metagegevens zoekt op de juiste locatie zoals deze is geconfigureerd in uw AEM Forms-implementatie.

