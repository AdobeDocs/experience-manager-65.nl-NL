---
title: AEM uitvoeren in productielocatie
description: Leer hoe u AEM kunt uitvoeren in de productielocatie.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
exl-id: 3c342014-f8ec-4404-afe5-514bdb651aae
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# AEM uitvoeren in productielocatie{#running-aem-in-production-ready-mode}

Met AEM 6.1 introduceert de Adobe de nieuwe `"nosamplecontent"` de uitvoeringsmodus, die tot doel heeft de stappen te automatiseren die nodig zijn om een AEM voor te bereiden voor de implementatie in een productieomgeving.

De nieuwe looppaswijze zal niet alleen automatisch de instantie vormen om aan de veiligheid beste praktijken te houden die in veiligheidscontrolelijst worden beschreven, maar zal ook alle toepassingen en configuraties van de steekproef Geometrixx in het proces verwijderen.

>[!NOTE]
>
>Omdat de AEM productielocatie gereed is om praktische redenen alleen de meeste taken bestrijkt die nodig zijn om een instantie te beveiligen, wordt u ten zeerste aangeraden de [Beveiligingscontrolelijst](/help/sites-administering/security-checklist.md) voordat u met uw productieomgeving gaat leven.
>
>Ook, merk op dat het runnen van AEM in Productie Klaar Wijze effectief toegang tot CRXDE Lite zal onbruikbaar maken. Als u het voor het zuiveren doeleinden nodig hebt, zie [CRXDE Lite inschakelen in AEM](/help/sites-administering/enabling-crxde-lite.md).

![chlimage_1-83](assets/chlimage_1-83a.png)

Als u AEM wilt uitvoeren in de productielocmodus, hoeft u alleen maar de knop `nosamplecontent` via de `-r` looppas wijzeschakelaar aan uw bestaande startargumenten:

```shell
java -jar aem-quickstart.jar -r nosamplecontent
```

U kunt bijvoorbeeld de productie gebruiken die klaar is om een auteurinstantie te starten met MongoDB-persistentie zoals deze:

```shell
java -jar aem-quickstart.jar -r author,crx3,crx3mongo,nosamplecontent -Doak.mongo.uri=mongodb://remoteserver:27017 -Doak.mongo.db=aem-author
```

## Verandert een deel van de Productie Klaar Wijze {#changes-part-of-the-production-ready-mode}

Meer specifiek, worden de volgende configuratieveranderingen uitgevoerd wanneer AEM op productie klaar wijze in werking wordt gesteld:

1. De **CRXDE-ondersteuningsbundel** ( `com.adobe.granite.crxde-support`) is standaard uitgeschakeld in de modus voor productie-klaar. Het kan op elk ogenblik van de Adobe openbare Maven bewaarplaats worden geïnstalleerd. Versie 3.0.0 is vereist voor AEM 6.1.

1. De **Apache Sling Simple WebDAV Access to repositories** ( `org.apache.sling.jcr.webdav`) is alleen beschikbaar op **auteur** instanties.

1. Nieuwe gebruikers moeten het wachtwoord wijzigen bij de eerste aanmelding. Dit is niet van toepassing op de beheerder.
1. **Foutopsporingsinfo genereren** is uitgeschakeld voor de **Apache Sling JavaScript-handler**.

1. **Toegewezen inhoud** en **Foutopsporingsinfo genereren** zijn uitgeschakeld voor de **Apache Sling JSP Script Handler**.

1. De **Day CQ WCM-filter** is ingesteld op `edit` op **auteur** en `disabled` op **publish** instanties.

1. De **Adobe Granite HTML Library Manager** is geconfigureerd met de volgende instellingen:

   1. **Miniatuur:** `enabled`
   1. **Foutopsporing:** `disabled`
   1. **Gzip:** `enabled`
   1. **Timing:** `disabled`

1. De **Apache Sling GET Servlet** is standaard ingesteld op ondersteuning van veilige configuraties, zoals hieronder wordt getoond:

| **Configuratie** | **Auteur** | **Publiceren** |
|---|---|---|
| TXT-uitvoering | uitgeschakeld | uitgeschakeld |
| HTML-uitvoering | uitgeschakeld | uitgeschakeld |
| JSON-uitvoering | enabled | enabled |
| XML-uitvoering | uitgeschakeld | uitgeschakeld |
| json.maximumresults | 1000 | 100 |
| Automatische index | uitgeschakeld | uitgeschakeld |
