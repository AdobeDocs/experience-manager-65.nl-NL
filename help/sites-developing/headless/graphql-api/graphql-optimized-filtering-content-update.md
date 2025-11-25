---
title: Inhoudsfragmenten bijwerken voor geoptimaliseerde GraphQL-filters
description: Leer hoe u de inhoudsfragmenten voor geoptimaliseerde GraphQL-filters in Adobe Experience Manager kunt bijwerken voor levering van inhoud zonder kop.
exl-id: d78ec052-c091-49ca-9f36-a3d24eb9edd5
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Developer
source-git-commit: 07289e891399a78568dcac957bc089cc08c7898c
workflow-type: tm+mt
source-wordcount: '250'
ht-degree: 0%

---

# Inhoudsfragmenten bijwerken voor geoptimaliseerde GraphQL-filters {#updating-content-fragments-for-optimized-graphql-filtering}

Als u de prestaties van uw GraphQL-filters wilt optimaliseren, voert u een procedure uit om uw Content Fragments bij te werken.

>[!NOTE]
>
>Na het bijwerken van uw Fragmenten van de Inhoud, kunt u de aanbevelingen voor [&#x200B; volgen het Optimaliseren van de Vragen van GraphQL &#x200B;](/help/sites-developing/headless/graphql-api/graphql-optimization.md).

## Vereisten {#prerequisites}

Zorg ervoor dat u minimaal over de release van 6.5.17.0 AEM beschikt.

## Inhoudsfragmenten bijwerken {#updating-content-fragments}

Voer de volgende stappen uit om de procedure uit te voeren:

1. [&#x200B; vorm de montages OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) voor de **Configuratie van de Baan van de Migratie van het Fragment van de Inhoud**:

   ![&#x200B; OSGi de Configuratie van de Baan van de Migratie van het Fragment van de Inhoud 1&rbrace; OSGi de Configuratie van de Baan van de Migratie van het Fragment van de Inhoud &#x200B;](assets/cfm-graphql-update-01.png "")

1. Stel deze twee parameters in het dialoogvenster als volgt in:

   * **ContentFragmentMigration:Enabled** : `1`
   * **ContentFragmentMigration:Enforce** : `1`

1. **sparen** de specificaties - de updateprocedure begint.

1. Wacht tot de procedure is voltooid. De procedure is voltooid wanneer de eigenschap `cfGlobalVersion` wordt weergegeven op `/content/dam` en is ingesteld op `1` .

1. Keer terug naar de configuratie OSGi om de procedure te deactiveren.

   In de dialoog voor de **Configuratie van de Baan van de Migratie van het Fragment van de Inhoud** plaatst deze twee parameters als volgt:

   * **ContentFragmentMigration:Enabled** : `0`
   * **ContentFragmentMigration:Enforce** : `0`

## Beperkingen {#limitations}

Houd rekening met de volgende beperkingen:

* Optimalisatie van de prestaties van GraphQL-filters is alleen mogelijk na een volledige update van al uw Content Fragments (aangegeven door de eigenschap `cfGlobalVersion` voor het JCR-knooppunt `/content/dam` )

* Als Inhoudsfragmenten uit een inhoudspakket worden geïmporteerd (met `crx/de` ) nadat de updateprocedure is uitgevoerd, worden die Inhoudsfragmenten pas in de resultaten van de GraphQL-query meegenomen als de updateprocedure opnieuw wordt uitgevoerd.
