---
title: Starten promoten
description: U moet opstartiepagina's promoten om de inhoud vóór publicatie weer naar de bron (productie) te verplaatsen. Wanneer een startpagina wordt bevorderd, wordt de bijbehorende pagina van de bronpagina's vervangen door de inhoud van de gepromoveerde pagina.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
exl-id: 3013adc3-bec6-4ecc-aefd-f8df2b86dfef
solution: Experience Manager, Experience Manager Sites
source-git-commit: 76fffb11c56dbf7ebee9f6805ae0799cd32985fe
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Starten promoten{#promoting-launches}

U moet opstartiepagina&#39;s promoten om de inhoud vóór publicatie weer naar de bron (productie) te verplaatsen. Wanneer een startpagina wordt bevorderd, wordt de bijbehorende pagina van de bronpagina&#39;s vervangen door de inhoud van de gepromoveerde pagina. De volgende opties zijn beschikbaar bij het promoten van een startpagina:

* Of alleen de huidige pagina of de volledige lancering wordt bevorderd.
* Of de onderliggende pagina&#39;s van de huidige pagina worden bevorderd.
* Of de volledige lancering of slechts pagina&#39;s wordt bevorderd die zijn veranderd.

## Startpagina&#39;s promoten {#promoting-launch-pages}

Als u pagina&#39;s wilt promoten, voert u de volgende stappen uit tijdens het bewerken van de startpagina die u wilt promoten:

1. Op de **Pagina** tabblad in Sidekick, klikt u op **Starten bevorderen**.
1. Geef de pagina&#39;s op die u wilt promoten:

   * (Standaard) Als u alleen de huidige pagina wilt promoten, selecteert u **Paginawijzigingen doorvoeren naar productieversie**.
   * Als u ook de onderliggende pagina&#39;s van de huidige pagina wilt bevorderen, selecteert u **Inclusief subpagina&#39;s**.
   * Selecteer **Volledige introductie naar productieversie bevorderen**.

1. Als u de productiepagina&#39;s aan een workflowpakket wilt toevoegen, selecteert u **Toevoegen aan workflowpakket** en selecteer vervolgens het workflowpakket.
1. Klikken **Bevorderen**.

## Promotiepagina&#39;s verwerken met AEM workflow {#processing-promoted-pages-using-aem-workflow}

Gebruik workflowmodellen voor bulkverwerking van geconverteerde startpagina&#39;s:

1. Maak een workflowpakket.
1. Wanneer auteurs startpagina&#39;s promoten, slaan ze deze op in het workflowpakket.
1. Start een workflowmodel met het pakket als de payload.

Als u automatisch een workflow wilt starten wanneer pagina&#39;s worden geconverteerd, [configureren van workflow-starter](/help/sites-administering/workflows-starting.md#workflows-launchers) voor het pakketknooppunt.

U kunt bijvoorbeeld automatisch aanvragen voor paginanactivering genereren wanneer auteurs pagina&#39;s voor Starten promoten. Configureer een werkstroomstartprogramma om de workflow voor activering van aanvragen te starten wanneer het pakketknooppunt wordt gewijzigd.

![chlimage_1-136](assets/chlimage_1-136.png)
