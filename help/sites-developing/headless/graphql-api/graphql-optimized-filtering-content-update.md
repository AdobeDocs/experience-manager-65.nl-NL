---
title: Inhoudsfragmenten bijwerken voor geoptimaliseerde GraphQL-filters
description: Leer hoe u de inhoudsfragmenten voor geoptimaliseerde GraphQL-filters in Adobe Experience Manager kunt bijwerken voor levering van inhoud zonder kop.
exl-id: d78ec052-c091-49ca-9f36-a3d24eb9edd5
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '255'
ht-degree: 0%

---

# Inhoudsfragmenten bijwerken voor geoptimaliseerde GraphQL-filters {#updating-content-fragments-for-optimized-graphql-filtering}

Als u de prestaties van uw GraphQL-filters wilt optimaliseren, voert u een procedure uit om uw Content Fragments bij te werken.

>[!NOTE]
>
>Nadat u de inhoudsfragmenten hebt bijgewerkt, kunt u de aanbevelingen voor [GraphQL-query&#39;s optimaliseren](/help/sites-developing/headless/graphql-api/graphql-optimization.md).

## Vereisten {#prerequisites}

Zorg ervoor dat u minimaal over de 6.5.17.0 release van AEM beschikt.

## Inhoudsfragmenten bijwerken {#updating-content-fragments}

Voer de volgende stappen uit om de procedure uit te voeren:

1. [Vorm de montages OSGi](/help/sites-deploying/configuring-osgi.md) voor de **Taakconfiguratie van migratie van inhoudsfragmenten**:

   ![Configuratie van OSGi-contentfragmentmigratie](assets/cfm-graphql-update-01.png "Configuratie van OSGi-contentfragmentmigratie")

1. Stel deze twee parameters in het dialoogvenster als volgt in:

   * **ContentFragmentMigration:Enabled** : `1`
   * **ContentFragmentMigration:Enforce** : `1`

1. **Opslaan** de specificaties - de updateprocedure begint .

1. Wacht tot de procedure is voltooid. De procedure is voltooid wanneer de eigenschap `cfGlobalVersion` wordt weergegeven op `/content/dam` en is ingesteld op `1`.

1. Keer terug naar de configuratie OSGi om de procedure te deactiveren.

   In het dialoogvenster voor het dialoogvenster **Taakconfiguratie van migratie van inhoudsfragmenten** stel de volgende twee parameters in:

   * **ContentFragmentMigration:Enabled** : `0`
   * **ContentFragmentMigration:Enforce** : `0`

## Beperkingen {#limitations}

Houd rekening met de volgende beperkingen:

* Optimalisatie van de prestaties van GraphQL-filters is alleen mogelijk na een volledige update van al uw Content Fragments (aangegeven door de aanwezigheid van de `cfGlobalVersion` eigenschap voor de JCR-node `/content/dam`)

* Als inhoudsfragmenten worden geïmporteerd uit een inhoudspakket (met `crx/de`) nadat de updateprocedure is uitgevoerd, worden die inhoudsfragmenten niet in de resultaten van de GraphQL-query meegenomen totdat de updateprocedure opnieuw wordt uitgevoerd.
