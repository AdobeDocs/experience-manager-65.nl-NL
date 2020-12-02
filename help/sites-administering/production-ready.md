---
title: AEM uitvoeren in productielocatie
seo-title: AEM uitvoeren in productielocatie
description: Leer hoe u AEM kunt uitvoeren in de productielodus.
seo-description: Leer hoe u AEM kunt uitvoeren in de productielodus.
uuid: f48c8bae-c72f-4772-967e-f1526f096399
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
discoiquuid: 32da99f0-f058-40ae-95a8-2522622438ce
translation-type: tm+mt
source-git-commit: 1c1ade947f2cbd26b35920cfd10b1666b132bcbd
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 3%

---


# AEM uitvoeren in productieklaar{#running-aem-in-production-ready-mode}

Met AEM 6.1 introduceert Adobe de nieuwe `"nosamplecontent"`-runmode die de stappen moet automatiseren die nodig zijn om een AEM-instantie voor te bereiden voor implementatie in een productieomgeving.

De nieuwe runmode zal niet alleen automatisch de instantie vormen om aan de veiligheid beste praktijken te houden die in veiligheidscontrolelijst worden beschreven, maar zal ook alle toepassingen en configuraties van de steekproefgeometrixx in het proces verwijderen.

>[!NOTE]
>
>Aangezien de AEM productieklaar-klaar modus om praktische redenen slechts een groot deel van de taken omvat die nodig zijn om een instantie te beveiligen, wordt u ten zeerste aangeraden de [Beveiligingschecklist](/help/sites-administering/security-checklist.md) te raadplegen voordat u met uw productieomgeving gaat werken.
>
>Ook, merk op dat het runnen van AEM in Productie Klaar Wijze effectief toegang tot CRXDE Lite zal onbruikbaar maken. Als u het voor het zuiveren doeleinden nodig hebt, zie [Het toelaten van CRXDE Lite in AEM](/help/sites-administering/enabling-crxde-lite.md).

![chlimage_1-83](assets/chlimage_1-83a.png)

Als u AEM wilt uitvoeren in de modus gereed voor productie, hoeft u alleen `nosamplecontent` via de runmode-switch `-r` toe te voegen aan uw bestaande opstartargumenten:

```shell
java -jar aem-quickstart.jar -r nosamplecontent
```

U kunt bijvoorbeeld de productie gebruiken die klaar is om een auteurinstantie te starten met MongoDB-persistentie zoals deze:

```shell
java -jar aem-quickstart.jar -r author,crx3,crx3mongo,nosamplecontent -Doak.mongo.uri=mongodb://remoteserver:27017 -Doak.mongo.db=aem-author
```

## Verandert een deel van de Klaar Wijze {#changes-part-of-the-production-ready-mode} van de Productie

Meer specifiek, zullen de volgende configuratieveranderingen worden uitgevoerd wanneer AEM op productie klaar wijze in werking wordt gesteld:

1. De **CRXDE-ondersteuningspakket** ( `com.adobe.granite.crxde-support`) is standaard uitgeschakeld in de productielocmodus. Het kan op elk ogenblik van de Adobe openbare Maven bewaarplaats worden geïnstalleerd. Versie 3.0.0 is vereist voor AEM 6.1.

1. De **Apache Sling Simple WebDAV Access to repositories** ( `org.apache.sling.jcr.webdav`)-bundel is alleen beschikbaar in **auteur**-instanties.

1. Nieuwe gebruikers moeten het wachtwoord wijzigen bij de eerste aanmelding. Dit is niet van toepassing op de beheerder.
1. **Genereren van foutopsporingsinformatie is uitgeschakeld** voor de  **Apache Java Script-handler**.

1. **Toegewezen** inhoud en  **genereren foutopsporingsinformatie uitgeschakeld voor de JSP Script-handler**   **** Apache Sling.

1. Het **Day CQ WCM-filter** wordt ingesteld op `edit` op **auteur** en `disabled` op **publish**-instanties.

1. **De Adobe Granite HTML Library** Manageris geconfigureerd met de volgende instellingen:

   1. **Miniatuur:** `enabled`
   1. **Foutopsporing:** `disabled`
   1. **Gzip:** `enabled`
   1. **Timing:** `disabled`

1. De **Apache Sling GET Servlet** is standaard ingesteld op ondersteuning van veilige configuraties, zoals hieronder wordt getoond:

| **Configuratie** | **Auteur** | **Publicatie** |
|---|---|---|
| TXT-uitvoering | disabled | uitgeschakeld |
| HTML-uitvoering | uitgeschakeld | uitgeschakeld |
| JSON-uitvoering | enabled | enabled |
| XML-uitvoering | uitgeschakeld | uitgeschakeld |
| json.maximumresults | 1000 | 100 |
| Automatische index | uitgeschakeld | uitgeschakeld |

