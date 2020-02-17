---
title: AEM wordt uitgevoerd in productiekaartmodus
seo-title: AEM wordt uitgevoerd in productiekaartmodus
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

---


# AEM wordt uitgevoerd in productiekaartmodus{#running-aem-in-production-ready-mode}

Met AEM 6.1 introduceert Adobe de nieuwe `"nosamplecontent"` runmode die de stappen moet automatiseren die nodig zijn om een AEM-instantie voor te bereiden voor implementatie in een productieomgeving.

De nieuwe runmode zal niet alleen automatisch de instantie vormen om aan de veiligheid beste praktijken te houden die in veiligheidscontrolelijst worden beschreven, maar zal ook alle toepassingen en configuraties van de steekproefgeometrixx in het proces verwijderen.

>[!NOTE]
>
>Aangezien de AEM Production Ready Mode om praktische redenen slechts een groot deel van de taken omvat die nodig zijn om een instantie te beveiligen, wordt u ten zeerste aangeraden de [Beveiligingschecklist](/help/sites-administering/security-checklist.md) te raadplegen voordat u met uw productieomgeving gaat werken.
>
>Houd er ook rekening mee dat het uitvoeren van AEM in productieklaar de toegang tot CRXDE Lite effectief zal uitschakelen. Als u het voor het zuiveren doeleinden nodig hebt, zie [Toelatend CRXDE Lite in AEM](/help/sites-administering/enabling-crxde-lite.md).

![chlimage_1-83](assets/chlimage_1-83a.png)

Om AEM op productie klaar wijze in werking te stellen moet u allen doen toevoegen `nosamplecontent` via de `-r` runmode schakelaar aan uw bestaande startargumenten:

```shell
java -jar aem-quickstart.jar -r nosamplecontent
```

U kunt bijvoorbeeld de productie gebruiken die klaar is om een auteurinstantie te starten met MongoDB-persistentie zoals deze:

```shell
java -jar aem-quickstart.jar -r author,crx3,crx3mongo,nosamplecontent -Doak.mongo.uri=mongodb://remoteserver:27017 -Doak.mongo.db=aem-author
```

## Verandert een deel van de Productie Klaar Wijze {#changes-part-of-the-production-ready-mode}

Meer specifiek, zullen de volgende configuratieveranderingen worden uitgevoerd wanneer AEM op productie klaar wijze in werking wordt gesteld:

1. De **CRXDE-ondersteuningspakket** ( `com.adobe.granite.crxde-support`) is standaard uitgeschakeld in de productieloestandmodus. Het kan op elk moment worden geïnstalleerd vanuit de openbare Maven-opslagplaats van Adobe. Versie 3.0.0 is vereist voor AEM 6.1.

1. De bundel **Apache Sling Simple WebDAV Access to repositories** ( `org.apache.sling.jcr.webdav`) is alleen beschikbaar op **auteur** -exemplaren.

1. Nieuwe gebruikers moeten het wachtwoord wijzigen bij de eerste aanmelding. Dit is niet van toepassing op de beheerder.
1. **Het genereren van foutopsporingsinformatie** is uitgeschakeld voor de **Apache Java Script-handler**.

1. **Toegewezen inhoud** en **Genereer foutopsporingsgegevens** zijn uitgeschakeld voor de JSP Script-handler **** Apache Sling.

1. Het **dagfilter** WCM is ingesteld op `edit` auteur **en** publicatie `disabled` **** -instanties.

1. **Adobe Granite HTML Library Manager** is geconfigureerd met de volgende instellingen:

   1. **** Miniatuur: `enabled`
   1. **** Foutopsporing: `disabled`
   1. **** Gzip: `enabled`
   1. **** Timing: `disabled`

1. De **Apache Sling GET Servlet** is als volgt ingesteld om veilige configuraties standaard te ondersteunen:

| **Configuratie** | **Author** | **Publiceren** |
|---|---|---|
| TXT-uitvoering | disabled | disabled |
| HTML-uitvoering | disabled | disabled |
| JSON-uitvoering | enabled | enabled |
| XML-uitvoering | disabled | disabled |
| json.maximum results | 1000 | 100 |
| Automatische index | disabled | disabled |

