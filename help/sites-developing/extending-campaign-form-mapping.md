---
title: Aangepaste formuliertoewijzingen maken
description: Wanneer u een aangepaste tabel maakt in Adobe Campaign, kunt u beter een formulier maken in AEM dat is toegewezen aan die aangepaste tabel
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
exl-id: bce6c586-9962-4217-82cb-c837e479abc0
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 66db4b0b5106617c534b6e1bf428a3057f2c2708
workflow-type: tm+mt
source-wordcount: '534'
ht-degree: 0%

---

# Aangepaste formuliertoewijzingen maken{#creating-custom-form-mappings}

Wanneer u een aangepaste tabel maakt in Adobe Campaign, kunt u beter een formulier maken in AEM dat aan die aangepaste tabel wordt toegewezen.

In dit document wordt beschreven hoe u aangepaste formuliertoewijzingen kunt maken. Wanneer u de stappen in dit document voltooit, biedt u uw gebruikers een gebeurtenispagina waarop zij zich kunnen aanmelden voor een aanstaande gebeurtenis. Vervolgens volgt u deze gebruikers via Adobe Campaign.

## Vereisten {#prerequisites}

U moet het volgende installeren:

* Adobe Experience Manager
* Adobe Campaign Classic

Zie [AEM integreren met Adobe Campaign Classic](/help/sites-administering/campaignonpremise.md) voor meer informatie .

## Aangepaste formuliertoewijzingen maken {#creating-custom-form-mappings-2}

Als u aangepaste formuliertoewijzingen wilt maken, moet u de volgende stappen op hoog niveau uitvoeren. Deze worden in de volgende secties uitgebreid beschreven:

1. Een aangepaste tabel maken.
1. Breid uit **zaad** tabel.
1. Een aangepaste toewijzing maken.
1. Maak een levering op basis van de aangepaste toewijzing.
1. Het formulier samenstellen in AEM, waarbij de gemaakte levering wordt gebruikt.
1. Verzend het formulier om het te testen.

### Aangepaste tabel maken in Adobe Campaign {#creating-the-custom-table-in-adobe-campaign}

Begin door een douanetabel in Adobe Campaign te creëren. In dit voorbeeld gebruiken we de volgende definitie om een gebeurtenistabel te maken:

```xml
<element autopk="true" label="Event" labelSingular="Event" name="event">
 <attribute label="Event Date" name="eventdate" type="date"/>
 <attribute label="Event Name" name="eventname" type="string"/>
 <attribute label="Email" name="email" type="string"/>
 <attribute label="Number of Seats" name="seats" type="long"/>
</element>
```

Nadat u de gebeurtenissentabel hebt gemaakt, voert u de **Wizard Databasestructuur bijwerken** om de tabel te maken.

### De zaadtabel uitbreiden {#extending-the-seed-table}

Selecteer in Adobe Campaign **Toevoegen** om een extensie van de **Zaadadressen (nms)** tabel.

![chlimage_1-194](assets/chlimage_1-194.png)

Gebruik nu de velden van de **event** tabel om de **zaad** tabel:

```xml
<element label="Event" name="custom_cus_event">
 <attribute name="eventname" template="cus:event:event/@eventname"/>
 <attribute name="eventdate" template="cus:event:event/@eventdate"/>
 <attribute name="email" template="cus:event:event/@email"/>
 <attribute name="seats" template="cus:event:event/@seats"/>
 </element>
```

Hierna voert u **Databasewizard bijwerken** om de wijzigingen toe te passen.

### Aangepaste doeltoewijzing maken {#creating-custom-target-mapping}

In **Beheer/Campagne** t, ga **Doeltoewijzingen** en voeg een nieuwe T toe **Doeltoewijzing.**

>[!NOTE]
>
>Zorg ervoor dat u een betekenisvolle naam gebruikt voor **Interne naam**.

![chlimage_1-195](assets/chlimage_1-195.png)

### Een aangepaste leveringssjabloon maken {#creating-a-custom-delivery-template}

In deze stap voegt u een leveringsmalplaatje toe dat gecreeerde gebruikt **Doeltoewijzing**.

In **Bronnen/sjablonen**, navigeer naar de leveringssjabloon en dupliceer de bestaande AEM levering. Wanneer u op **Naar**, selecteert u de gebeurtenis create **Doeltoewijzing**.

![chlimage_1-196](assets/chlimage_1-196.png)

### Het formulier samenstellen in AEM {#building-the-form-in-aem}

In AEM, zorg ervoor u een Cloud Service binnen hebt gevormd **Pagina-eigenschappen**.

Dan, in **Adobe Campaign** selecteert u de levering waarin [Een aangepaste leveringssjabloon maken](#creating-a-custom-delivery-template).

![chlimage_1-197](assets/chlimage_1-197.png)

Wanneer u de velden configureert, moet u unieke elementnamen opgeven voor de formuliervelden.

Nadat de gebieden worden gevormd, moet u de afbeelding manueel veranderen.

Ga in CRXDE-lite naar de **jcr:inhoud** (van de pagina) en wijzig de **acMapping** waarde voor de interne naam van de **Doeltoewijzing**.

![chlimage_1-198](assets/chlimage_1-198.png)

Controleer in de configuratie van het formulier of u het selectievakje inschakelt om te maken dat het formulier niet bestaat

![chlimage_1-199](assets/chlimage_1-199.png)

### Het formulier verzenden {#submitting-the-form}

U kunt nu het formulier verzenden en op de Adobe Campaign valideren of de waarden zijn opgeslagen.

![chlimage_1-200](assets/chlimage_1-200.png)

## Problemen oplossen {#troubleshooting}

**&quot;Ongeldig type voor waarde &#39;02/02/2015&#39; van element &#39;@eventdate&#39; (document van type &#39;Event ([adb:event])&#39;)&quot;**

Bij het verzenden van het formulier wordt deze fout in het dialoogvenster **error.log** in AEM.

Dit wordt veroorzaakt door een ongeldige indeling voor het datumveld. De oplossing is om **jjjj-mm-dd** als de waarde.
