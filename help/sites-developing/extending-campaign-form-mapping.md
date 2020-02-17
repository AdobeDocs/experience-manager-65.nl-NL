---
title: Aangepaste formuliertoewijzingen maken
seo-title: Aangepaste formuliertoewijzingen maken
description: Wanneer u een aangepaste tabel maakt in Adobe Campaign, kunt u in AEM een formulier maken dat is toegewezen aan die aangepaste tabel
seo-description: Wanneer u een aangepaste tabel maakt in Adobe Campaign, kunt u in AEM een formulier maken dat is toegewezen aan die aangepaste tabel
uuid: f3bde513-6edb-4eb6-9048-40045ee08c4a
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
discoiquuid: d5dac1db-2dde-4b75-a31b-e057b447f6e2
translation-type: tm+mt
source-git-commit: a3c303d4e3a85e1b2e794bec2006c335056309fb

---


# Aangepaste formuliertoewijzingen maken{#creating-custom-form-mappings}

Wanneer u een aangepaste tabel maakt in Adobe Campaign, kunt u in AEM een formulier maken dat aan die aangepaste tabel wordt toegewezen.

In dit document wordt beschreven hoe u aangepaste formuliertoewijzingen kunt maken. Wanneer u de stappen in dit document voltooit, biedt u uw gebruikers een gebeurtenispagina waarop zij zich kunnen aanmelden voor een aanstaande gebeurtenis. Daarna volgt u deze gebruikers via Adobe Campaign.

## Vereisten {#prerequisites}

U moet het volgende installeren:

* Adobe Experience Manager
* Adobe Campaign Classic

Zie AEM [integreren met Adobe Campaign Classic](/help/sites-administering/campaignonpremise.md) voor meer informatie.

## Aangepaste formuliertoewijzingen maken {#creating-custom-form-mappings-2}

Als u aangepaste formuliertoewijzingen wilt maken, moet u de volgende stappen op hoog niveau uitvoeren. Deze worden in de volgende secties uitgebreid beschreven:

1. Een aangepaste tabel maken.
1. Breid de **zaadlijst** uit.
1. Een aangepaste toewijzing maken.
1. Maak een levering op basis van de aangepaste toewijzing.
1. Het formulier samenstellen in AEM, waarvoor de gemaakte levering wordt gebruikt.
1. Verzend het formulier om het te testen.

### Aangepaste tabel maken in Adobe-campagne {#creating-the-custom-table-in-adobe-campaign}

Begin door een douanetabel in de Campagne van Adobe te creëren. In dit voorbeeld gebruiken we de volgende definitie om een gebeurtenistabel te maken:

```xml
<element autopk="true" label="Event" labelSingular="Event" name="event">
 <attribute label="Event Date" name="eventdate" type="date"/>
 <attribute label="Event Name" name="eventname" type="string"/>
 <attribute label="Email" name="email" type="string"/>
 <attribute label="Number of Seats" name="seats" type="long"/>
</element>
```

Nadat u de gebeurtenistabel hebt gemaakt, voert u de wizard **Databasestructuur** bijwerken uit om de tabel te maken.

### De zaadtabel uitbreiden {#extending-the-seed-table}

Tik/klik in Adobe Campagne op **Toevoegen** om een nieuwe extensie van de tabel met **zaadadressen (nms)** te maken.

![chlimage_1-194](assets/chlimage_1-194.png)

Gebruik nu de velden uit de **gebeurtenistabel** om de **zaadtabel** uit te breiden:

```xml
<element label="Event" name="custom_cus_event">
 <attribute name="eventname" template="cus:event:event/@eventname"/>
 <attribute name="eventdate" template="cus:event:event/@eventdate"/>
 <attribute name="email" template="cus:event:event/@email"/>
 <attribute name="seats" template="cus:event:event/@seats"/>
 </element>
```

Voer daarna de databasetovenaar **** Update uit om de wijzigingen toe te passen.

### Aangepaste doeltoewijzing maken {#creating-custom-target-mapping}

In **Beleid/het** Beheer van de Campagne, ga naar **Toewijzingen** van het Doel en voeg een nieuwe **Afbeelding van het Doel toe.**

>[!NOTE]
>
>Gebruik een betekenisvolle naam voor de **interne naam**.

![chlimage_1-195](assets/chlimage_1-195.png)

### Een aangepaste leveringssjabloon maken {#creating-a-custom-delivery-template}

In deze stap, voegt u een leveringsmalplaatje toe dat de gecreeerde afbeelding **van het** Doel gebruikt.

In **Middelen/Malplaatjes**, navigeer aan het Malplaatje van de Levering en dupliceer de bestaande levering AEM. Wanneer u klikt **aan**, selecteer creeer gebeurtenis **richt afbeelding**.

![chlimage_1-196](assets/chlimage_1-196.png)

### Het formulier samenstellen in AEM {#building-the-form-in-aem}

In AEM, zorg ervoor u een Dienst van de Wolk in **Pagina Eigenschappen** hebt gevormd.

Selecteer vervolgens op het tabblad **Adobe-campagne** de levering die is gemaakt in [Een aangepaste leveringssjabloon](#creating-a-custom-delivery-template)maken.

![chlimage_1-197](assets/chlimage_1-197.png)

Wanneer u de velden configureert, moet u unieke elementnamen opgeven voor de formuliervelden.

Nadat de gebieden worden gevormd, moet u de afbeelding manueel veranderen.

Ga in CRXDE-lite naar het knooppunt **jcr:content** (van de pagina) en wijzig de **acMapping** -waarde in de interne naam van de **doeltoewijzing**.

![chlimage_1-198](assets/chlimage_1-198.png)

Controleer in de configuratie van het formulier of u het selectievakje inschakelt om te maken dat het formulier niet bestaat

![chlimage_1-199](assets/chlimage_1-199.png)

### Het formulier verzenden {#submitting-the-form}

U kunt het formulier nu verzenden en valideren aan de zijde van Adobe Campagne, ongeacht of de waarden zijn opgeslagen.

![chlimage_1-200](assets/chlimage_1-200.png)

## Problemen oplossen {#troubleshooting}

**&quot;Ongeldig type voor waarde &#39;02/02/2015&#39; van element &#39;@eventdate&#39; (document van type &#39;Event ([adb:event])&#39;)&quot;**

Bij het verzenden van het formulier wordt deze fout aangemeld bij **error.log** in AEM.

Dit wordt veroorzaakt door een ongeldige indeling voor het datumveld. U kunt dit omzeilen door dd- **mm-jjjj** als waarde op te geven.

